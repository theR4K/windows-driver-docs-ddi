---
UID: NF:printerextension.IPrintSchemaOptionCollection.GetAt
title: IPrintSchemaOptionCollection::GetAt (printerextension.h)
description: Gets a pointer to an IPrintSchemaOption object.
old-location: print\iprintschemaoptioncollection_getat.htm
tech.root: print
ms.date: 04/20/2018
keywords: ["IPrintSchemaOptionCollection::GetAt"]
ms.keywords: GetAt, GetAt method [Print Devices], GetAt method [Print Devices],IPrintSchemaOptionCollection interface, IPrintSchemaOptionCollection interface [Print Devices],GetAt method, IPrintSchemaOptionCollection.GetAt, IPrintSchemaOptionCollection::GetAt, print.iprintschemaoptioncollection_getat, printerextension/IPrintSchemaOptionCollection::GetAt
req.header: printerextension.h
req.include-header: 
req.target-type: Desktop
req.target-min-winverclnt: Windows 8
req.target-min-winversvr: Windows Server 2012
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: 
targetos: Windows
req.typenames: 
f1_keywords:
 - IPrintSchemaOptionCollection::GetAt
 - printerextension/IPrintSchemaOptionCollection::GetAt
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - COM
api_location:
 - Printerextension.h
api_name:
 - IPrintSchemaOptionCollection::GetAt
---

# IPrintSchemaOptionCollection::GetAt


## -description

Gets a pointer to an <a href="/windows-hardware/drivers/ddi/printerextension/nn-printerextension-iprintschemaoption">IPrintSchemaOption</a> object.

## -parameters

### -param ulIndex [in]


Index of the <b>IPrintSchemaOption</b> object within the collection.

### -param ppOption [out, retval, optional]


Pointer to an <a href="/windows-hardware/drivers/ddi/printerextension/nn-printerextension-iprintschemaoption">IPrintSchemaOption</a> object.

## -returns

Returns an <b>HRESULT</b> value. If the method call was not successful,  it returns the appropriate <b>HRESULT</b> error code.

## -see-also

<a href="/windows-hardware/drivers/ddi/printerextension/nn-printerextension-iprintschemaoption">IPrintSchemaOption</a>



<a href="/windows-hardware/drivers/ddi/printerextension/nn-printerextension-iprintschemaoptioncollection">IPrintSchemaOptionCollection</a>

