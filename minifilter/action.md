---
layout: ../../layouts/MarkdownPostLayout.astro
title: "Preoperation and postoperation callback routines"
description:  "In its DriverEntry routine, 
a minifilter driver can register up to one preoperation callback routine and up to 
one postoperation callback routine for each type of I/O operation that it needs to filter."
date: 2026-06-01
author: "tdtc"
---
In its DriverEntry routine, a minifilter driver can register up to one preoperation callback routine 
and up to one postoperation callback routine for each type of I/O operation that it needs to filter.

### [preoperation callback routine](https://learn.microsoft.com/en-us/windows-hardware/drivers/ddi/fltkernel/nc-fltkernel-pflt_pre_operation_callback)
```
PFLT_PRE_OPERATION_CALLBACK PfltPreOperationCallback;

FLT_PREOP_CALLBACK_STATUS PfltPreOperationCallback(
  [in, out] PFLT_CALLBACK_DATA Data,
  [in]      PCFLT_RELATED_OBJECTS FltObjects,
  [out]     PVOID *CompletionContext
)
```

- For example: Declarations in FsMinifilter
```
EXTERN_C_START
    FLT_PREOP_CALLBACK_STATUS FLTAPI PreOperationCreate(
        _Inout_ PFLT_CALLBACK_DATA Data,
        _In_ PCFLT_RELATED_OBJECTS FltObjects,
        _Flt_CompletionContext_Outptr_ PVOID* CompletionContext
    );
EXTERN_C_END
```

### [postoperation callback routine](https://learn.microsoft.com/en-us/windows-hardware/drivers/ddi/fltkernel/nc-fltkernel-pflt_post_operation_callback)
```
PFLT_POST_OPERATION_CALLBACK PfltPostOperationCallback;

FLT_POSTOP_CALLBACK_STATUS PfltPostOperationCallback(
  [in, out]      PFLT_CALLBACK_DATA Data,
  [in]           PCFLT_RELATED_OBJECTS FltObjects,
  [in, optional] PVOID CompletionContext,
  [in]           FLT_POST_OPERATION_FLAGS Flags
)
```

- For example: Declarations in filter/avscan.c
```
FLT_POSTOP_CALLBACK_STATUS
AvPostCreate (
    _Inout_ PFLT_CALLBACK_DATA Data,
    _In_ PCFLT_RELATED_OBJECTS FltObjects,
    _In_opt_ PVOID CompletionContext,
    _In_ FLT_POST_OPERATION_FLAGS Flags
    );
```

## Ref
- [Writing Preoperation and Postoperation Callback Routines](https://learn.microsoft.com/en-us/windows-hardware/drivers/ifs/writing-preoperation-and-postoperation-callback-routines)
