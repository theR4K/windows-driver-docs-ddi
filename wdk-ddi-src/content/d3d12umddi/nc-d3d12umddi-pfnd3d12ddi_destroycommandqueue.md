---
UID: NC:d3d12umddi.PFND3D12DDI_DESTROYCOMMANDQUEUE
title: PFND3D12DDI_DESTROYCOMMANDQUEUE
author: windows-driver-content
description: 
ms.assetid: 751d9b9d-9f0e-4ded-a15a-cae5efeea015
ms.author: windowsdriverdev
ms.date: 
ms.topic: callback
ms.prod: windows-hardware
ms.technology: windows-devices
req.header: d3d12umddi.h
req.include-header:
req.target-type:
req.target-min-winverclnt:
req.target-min-winversvr:
req.kmdf-ver:
req.umdf-ver:
req.lib:
req.dll:
req.irql: 
req.ddi-compliance:
req.unicode-ansi:
req.idl:
req.max-support:
req.namespace:
req.assembly:
req.type-library: 
topic_type: 
-	apiref
api_type: 
-	UserDefined
api_location: 
-	d3d12umddi.h
api_name: 
-	PFND3D12DDI_DESTROYCOMMANDQUEUE
product: 
- Windows
targetos: Windows
tech.root: display
---

# PFND3D12DDI_DESTROYCOMMANDQUEUE callback function

## -description

Implemented by the client driver to ... 

## -prototype

```
//Declaration

PFND3D12DDI_DESTROYCOMMANDQUEUE Pfnd3d12ddiDestroycommandqueue; 

// Definition

VOID Pfnd3d12ddiDestroycommandqueue 
(
	 D3D12DDI_HDEVICE
	 D3D12DDI_HCOMMANDQUEUE
)
{...}

PFND3D12DDI_DESTROYCOMMANDQUEUE 


```

## -parameters

### -param D3D12DDI_HDEVICE: 
### -param D3D12DDI_HCOMMANDQUEUE: 



## -returns

Returns VOID that ...

## -remarks

Register your implementation of this callback function by setting the appropriate member of <!-- REPLACE ME --> and then calling <!-- REPLACE ME -->.


## -see-also