---
UID: NS:d3dkmddi._DXGKARGCB_SIGNALEVENT
title: DXGKARGCB_SIGNALEVENT (d3dkmddi.h)
description: Arguments used in the call to DXGKCB_SIGNALEVENT.
ms.date: 10/13/2021
keywords: ["DXGKARGCB_SIGNALEVENT structure"]
ms.keywords: _DXGKARGCB_SIGNALEVENT, DXGKARGCB_SIGNALEVENT,
req.header: d3dkmddi.h
req.include-header: 
req.target-type: 
req.target-min-winverclnt: Windows 10, version 1809 (WDDM 2.5)
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.lib: 
req.dll: 
req.ddi-compliance: 
req.unicode-ansi: 
req.max-support: 
req.typenames: DXGKARGCB_SIGNALEVENT
targetos: Windows
tech.root: display
ms.custom: RS5
f1_keywords:
 - _DXGKARGCB_SIGNALEVENT
 - d3dkmddi/_DXGKARGCB_SIGNALEVENT
 - DXGKARGCB_SIGNALEVENT
 - d3dkmddi/DXGKARGCB_SIGNALEVENT
topic_type:
 - apiref
api_type:
 - HeaderDef
api_location:
 - d3dkmddi.h
api_name:
 - _DXGKARGCB_SIGNALEVENT
 - DXGKARGCB_SIGNALEVENT
dev_langs:
 - c++
---

# DXGKARGCB_SIGNALEVENT structure

## -description

**DXGKARGCB_SIGNALEVENT** contains the arguments used by the [**DXGKCB_SIGNALEVENT**](nc-d3dkmddi-dxgkcb_signalevent.md) callback function, to signal an event.

## -struct-fields

### -field hDxgkProcess [in]

Handle to the DXGK process object that is passed to [**DxgkDdiCreateProcess**](nc-d3dkmddi-dxgkddi_createprocess.md). The process must be created for a virtual machine, where DXGK_CREATEPROCESSFLAGS::VirtualMachineProcess is set in **DxgkDdiCreateProcess**.

The driver must synchronize the callback with [**DxgkDdiDestroyProcess**](nc-d3dkmddi-dxgkddi_destroyprocess.md) to ensure that the process is not destroyed during the callback.

### -field hEvent [in]

The user-mode event handle that needs to be signaled. The handle is valid in the context of the DXGK process, identified by **hDxgkProcess**. The user-mode driver on the guest can send the user-mode event handle to the kernel-mode driver via [**DXGKDDI_ESCAPE**](nc-d3dkmddi-dxgkddi_escape.md) or other APIs that allow private driver data.

### -field CpuEventObject [in]

When set, indicates the event is a CPU event object. Supported starting in Windows 11 (WDDM 3.0).

### -field Reserved [in]

Reserved; set to zero.

### -field Flags [in]

A single value containing the flags set in the structure.

## -remarks

## -see-also

[**DXGKCB_SIGNALEVENT**](nc-d3dkmddi-dxgkcb_signalevent.md)

[**DXGKDDI_ESCAPE**](nc-d3dkmddi-dxgkddi_escape.md)

[**DxgkDdiCreateProcess**](nc-d3dkmddi-dxgkddi_createprocess.md)

[**DxgkDdiDestroyProcess**](nc-d3dkmddi-dxgkddi_destroyprocess.md)
