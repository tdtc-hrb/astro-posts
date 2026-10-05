---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Instruction-set: movzx"
description: "Fix crash when editing text - tui"
date: 2026-01-16
author: xiaobin
tags: ["assembly", "tui"]
---
![Figure 2: Example of a single 64-bit GPR extended from the 8080 ISA.](https://github.com/tdtc-hrb/csdn/raw/master/images/figure2_asm.png)
from [General-purpose registers](https://sonictk.github.io/asm_tutorial/)

### Fix crash when editing text - [edits.asm](https://github.com/magiblot/tvision/commit/af1e40f1f1cdfabf4ad3c9a69412be411f8c5515)
Amazing. The assembly function lineEnd, which searches for a carriage return in the current line, 
uses the REPNE instruction which relies on the (E)CX register to stop iterating. 
When they wrote this function in 32-bit assembly, though, they forgot about the upper half of ECX. 
Therefore, if the upper half of ECX was different from zero, REPNE would keep iterating even if CX was zero, which is how it worked in 16-bit.

For some reason (either due to a huge amount of luck, 
or because they knew too well what the program was doing) this still worked if the assembly version of TVWRITE was in use; 
the assumption that ECX<31..16> equals zero is no longer true when using the new CPP version. 
This made me initially believe this was a bug in the code I wrote, but it is not.

- ln252 - old
```
ELSE        ;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;32-bit;;;;;;;;;;;;;;;;;;;;;;;;;;
        USES    ESI, EDI, EBX

        MOV     ESI, DWORD PTR [thisPtr]
        MOV     EBX, [ESI+TEditorBuffer]
        MOVZX   EDI, WORD PTR [P]
        MOV     AL, 0DH
        CLD
        MOV     CX, [ESI+TEditorCurPtr]
        SUB     CX, DI
        JBE   @@1
        ADD     EDI, EBX
        REPNE   SCASB
        JE    @@2
        MOVZX   EDI, WORD PTR [ESI+TEditorCurPtr]
@@1:    MOV     CX, [ESI+TEditorBufLen]
        SUB     CX, DI
        JCXZ  @@4
        MOVZX   EDX, WORD PTR [ESI+TEditorGapLen]
        ADD     EBX, EDX
        ADD     EDI, EBX
        REPNE   SCASB
        JNE   @@3
@@2:    DEC     EDI
@@3:    SUB     EDI, EBX
@@4:    MOV     EAX, EDI
        RET

ENDIF
```

changed 1(ln260):
```
        MOVZX   ECX, WORD PTR [ESI+TEditorCurPtr]
        SUB     ECX, EDI
```
changed 2(ln267):
```
@@1:    MOVZX   ECX, WORD PTR [ESI+TEditorBufLen]
        SUB     ECX, EDI
```

### movzx
If you have same-sized operands, you're expected to use <i>mov</i>.

<i>movzx</i> and <i>movsx</i> are only intended to be used when the destination is wider than the source so there's some actual Zero eXtension or Sign eXtension to do.

```
movzx specifically wants the destination to be larger than the source.
```

## Ref
- [Text-based user interface](https://en.wikipedia.org/wiki/Text-based_user_interface)
- [Why doesn't MOVZX work when operands have the same size?](https://stackoverflow.com/questions/67933514/why-doesnt-movzx-work-when-operands-have-the-same-size)
