---
layout: ../../layouts/MarkdownPostLayout.astro
title: "MASM32"
description: "32-bit assembler"
date: 2026-01-16
author: xiaobin
tags: ["assembly", "tui"]
---
After downloading [v11r](http://www.masm32.com/download/masm32v11r.zip), install it using administrator.

Create an empty console application (VC++) and set it up.

## project Set
- set masm    
Project -> Build Customizations    
checked:
```
masm(.targets, .props)
```

- set entry point    
Linker -> Advanced
```
Entry Point: main
```

- set path    
Linker -> General -> Additional Library Directories
```
C:\masm32\lib;
```


## program
new file "test1.asm" right click "properties" choice "Microsoft Macro Assembler"
```
Project -> Add New Item
```
![Add New Item](https://github.com/tdtc-hrb/cnblogs/raw/main/images/Add-New-Item_vc141.png)

Microsoft Macro Assembler -> General -> Include Paths
```
C:\masm32\include;
```

### code
> test1.asm

- v14.x
```
.686
.MODEL  flat, c

includelib ucrt.lib                            ; VS2015+ Usage
includelib legacy_stdio_definitions.lib        ; VS2015+ Usage
;includelib  \masm32\lib\msvcrt.lib            ; VS2013- Usage

;Function prototypes 
printf  proto arg1:ptr byte, printlist:vararg

.data
msg1fmt byte "%s%d",0Ah,0
msg1    byte "y: ",0
x       sdword ?
y       sdword ?

.code
        align 4
        
main    PROC
        mov eax, 3h
        mov x, eax
        ;;y = 2 + 3
        ;add eax, 2h
        ;;y = 3 - 2
        sub eax, 2h
        mov y, eax

        invoke printf, ADDR msg1fmt, ADDR msg1, y
        ret
main    ENDP

end ;program end
```

## Ref
- [Setting Up Visual Studio 10 for MASM32 Programming](https://scriptbucket.wordpress.com/2011/10/19/setting-up-visual-studio-10-for-masm32-programming/)
- [printf working not correct in masm - Vortex](http://masm32.com/board/index.php?topic=6347.0)
