---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Instruction-set: jae and jge"
description: "edits.asm - tv2.0"
date: 2026-01-16
author: xiaobin
tags: ["assembly", "tui"]
---

JAE, Jump if Above or Equal, should be used when comparing unsigned numbers. 

JGE, Jump if Greater or Equal, should be used when comparing signed numbers.

### JAE
Jump If Above or Equal

JAE short-label    
Logic:
```
    Jump if CF = 0
```
Used after a CMP or SUB instruction, JAE transfers control to short-label 
if the first operand (which should be unsigned) was greater than or equal to the second operand (also unsigned). 
The target of the jump must be within -128 to +127 bytes of the next instruction.

|Operands |Clocks |Transfers |Bytes |Example|
|-|-|-|-|-|
|short-label |16 or 4 |-|2 |JAE ABOVE_EQUAL|

Note: JNB (Jump Not Below) is the same instruction as JAE.

### JGE
Jump If Greater or Equal

JGE short-label
Logic:

    Jump if SF = OF

Used after a CMP or SUB instruction, JGE transfers control to short- label 
if the first operand is greater than or equal to the second. (Both operands are treated as signed numbers.)
The target of the jump must be within -128 to +127 bytes of the next instruction. 

|Operands |Clocks |Transfers |Bytes |Example|
|-|-|-|-|-|
|short-label |16 or 4 |- |2 |JGE GREATER_EQUAL|

Note: JNL, Jump if Not Less, is the same instruction as JGE.

## Ref
- ["J" Instructions](https://www.dei.isep.ipp.pt/~nsilva/ensino/ArqC/ArqC1998-1999/nguide/ng-j.htm)
- [Borland Original Turbo Vision 2.0.3 code](http://www.sigala.it/sergio/tvision/source/tv2orig.zip)
- [turbo vision](https://crates.io/crates/turbo-vision)
