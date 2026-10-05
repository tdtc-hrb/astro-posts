---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Nasm64"
description: "64-bit assembler"
date: 2026-01-16
author: xiaobin
tags: ["assembly", "tui"]
---
```
git clone https://github.com/ShiftMediaProject/VSNASM.git
```
- x64 Native Tools Command Prompt for VS 2022
> Run command prompt as administrator
```cmd
cd \
cd VSNASM
install_script.bat
```

## project
- set compile    
Project -> Build Customizations    
checked:
```
nasm(.targets, .props)
```

- set entry point    
Linker -> Advanced
```
Entry Point: main
```

### compile
- manual:
```
nasm -f win64 hello_floats.asm
```
- auto:    
In the Solution Explorer, select the asm file, then right-click and select Compile.

### Generate exe
run "x64 Native Tools Command Prompt for VS 2022"
```
link hello_floats.obj /subsystem:console /out:hello6.exe kernel32.lib msvcrt.lib ucrt.lib legacy_stdio_definitions.lib
```

### hello_floats.asm
```
; Copyright 2019 Siew Yi Liang.
; 
default rel
bits 64

segment .data
    a dd 3.25
    b dd 10.53

    fmt db 'result is: %f', 0xa, 0

segment .text
global main
extern _CRT_INIT
extern ExitProcess
extern printf

main:
    call _CRT_INIT                 ; Needed since our entry point is not _DllMainCRTStartup. See https://msdn.microsoft.com/en-us/library/708by912.aspx

    push    rbp
    mov    rbp, rsp
    sub    rsp, 32

    movss    xmm0, [a]             ; Load a
    movss    xmm1, [b]             ; Load b
    vaddss    xmm2, xmm0, xmm1      ; xmm2 = xmm1 + xmm2
    lea    rcx, [fmt]
    movss    xmm1, xmm2

    ; Remember, %f actually expects a double, so we need to convert the float to double
    cvtss2sd    xmm1, xmm1

    ; Also remember: floats are passed in xmm registers, but printf wants a
    ; double! This is an aggregate so it's passed in RDX instead.
    movq    rdx, xmm1
    call    printf

    xor eax, eax                ; return 0
    call ExitProcess

```


## Ref
- [Understanding Windows x64 Assembly](https://sonictk.github.io/asm_tutorial/)
