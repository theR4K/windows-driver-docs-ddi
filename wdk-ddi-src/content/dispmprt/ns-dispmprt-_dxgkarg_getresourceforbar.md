---
UID: NS:dispmprt._DXGKARG_GETRESOURCEFORBAR
title: _DXGKARG_GETRESOURCEFORBAR
description: Arguments used to get the host partition base address of a single Virtual Function base address register (BAR).
tech.root: display
ms.date: 04/04/2019
keywords: ["DXGKARG_GETRESOURCEFORBAR structure"]
ms.keywords: _DXGKARG_GETRESOURCEFORBAR, DXGKARG_GETRESOURCEFORBAR, *PDXGKARG_GETRESOURCEFORBAR,
req.header: dispmprt.h
req.include-header: 
req.target-type: 
req.target-min-winverclnt: 
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.lib: 
req.dll: 
req.ddi-compliance: 
req.unicode-ansi: 
req.max-support: 
req.typenames: DXGKARG_GETRESOURCEFORBAR, *PDXGKARG_GETRESOURCEFORBAR
targetos: Windows
ms.custom: 19H1
f1_keywords:
 - _DXGKARG_GETRESOURCEFORBAR
 - dispmprt/_DXGKARG_GETRESOURCEFORBAR
 - PDXGKARG_GETRESOURCEFORBAR
 - dispmprt/PDXGKARG_GETRESOURCEFORBAR
 - DXGKARG_GETRESOURCEFORBAR
 - dispmprt/DXGKARG_GETRESOURCEFORBAR
topic_type:
 - apiref
api_type:
 - HeaderDef
api_location:
 - dispmprt.h
api_name:
 - _DXGKARG_GETRESOURCEFORBAR
 - PDXGKARG_GETRESOURCEFORBAR
 - DXGKARG_GETRESOURCEFORBAR
product:
 - Windows
dev_langs:
 - c++
---

# _DXGKARG_GETRESOURCEFORBAR structure


## -description

Arguments used to get the host partition base address of a single Virtual Function base address register (BAR).

## -struct-fields

### -field VirtualFunctionIndex

Zero-based offset of the Virtual Function from the first VF exposed by this Physical Function.

### -field BarIndex

Index to the bar to retrieve the resource for.

### -field pResource

Out variable that will be filled in with the resource information, specifically the base address.  This is a CM_PARTIAL_RESOURCE_DESCRIPTOR. Valid types are CmResourceTypeMemory and CmResourceTypeMemoryLarge.

## -remarks

## -see-also

