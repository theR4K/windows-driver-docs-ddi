---
UID: NF:ntifs.CcCopyWrite
title: CcCopyWrite function (ntifs.h)
description: The CcCopyWrite routine copies data from a user buffer to a cached file.
old-location: ifsk\cccopywrite.htm
tech.root: ifsk
ms.date: 04/16/2018
keywords: ["CcCopyWrite function"]
ms.keywords: CcCopyWrite, CcCopyWrite routine [Installable File System Drivers], ccref_97ca67a6-e212-42bb-8998-be458c792f7b.xml, ifsk.cccopywrite, ntifs/CcCopyWrite
req.header: ntifs.h
req.include-header: Ntifs.h, FltKernel.h
req.target-type: Universal
req.target-min-winverclnt: Available on Microsoft Windows 2000 and later Windows operating systems.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: NtosKrnl.lib
req.dll: NtosKrnl.exe
req.irql: <= APC_LEVEL
targetos: Windows
req.typenames: 
f1_keywords:
 - CcCopyWrite
 - ntifs/CcCopyWrite
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - DllExport
api_location:
 - NtosKrnl.exe
api_name:
 - CcCopyWrite
---

# CcCopyWrite function


## -description

The <b>CcCopyWrite</b> routine copies data from a user buffer to a cached file.

## -parameters

### -param FileObject [in]


A pointer to a file object for the cached file to which the data is to be written.

### -param FileOffset [in]


A pointer to a variable that specifies the starting byte offset within the cached file.

### -param Length [in]


The length in bytes of the data to be written.

### -param Wait [in]


Set to <b>TRUE</b> if the caller can be put into a wait state until all the data has been copied, <b>FALSE</b> otherwise.

### -param Buffer [in]


A pointer to the buffer from which the data is to be copied.

## -returns

The <b>CcCopyWrite</b> routine returns <b>TRUE</b> if the data was copied successfully, <b>FALSE</b> otherwise.

## -remarks

If <i>Wait</i> is <b>TRUE</b>, <b>CcCopyWrite</b> is guaranteed to complete the copy request and return <b>TRUE</b>. If the required pages of the cached file are already resident in memory, the data will be copied immediately and no blocking will occur. If any needed pages are not resident, the caller will be put in a wait state until all required pages have been made resident and the data can be copied.

If <i>Wait</i> is <b>FALSE</b>, <b>CcCopyWrite</b> will refuse to block, and will return <b>FALSE</b>, if the required pages of the cached file are not already resident in memory or if the FO_WRITE_THROUGH flag is set on the file object.

If any failure occurs, <b>CcCopyWrite</b> raises a status exception for that particular failure. For example, if a pool allocation failure occurs, <b>CcCopyWrite</b> raises a STATUS_INSUFFICIENT_RESOURCES exception; if an I/O error occurs, <b>CcCopyWrite</b> raises the status exception of the I/O error. Therefore, to gain control if a failure occurs, the driver should wrap the call to <b>CcCopyWrite</b> in a <b>try-except</b> or <b>try-finally</b> statement.

To cache a file, use <a href="/windows-hardware/drivers/ddi/ntifs/nf-ntifs-ccinitializecachemap">CcInitializeCacheMap</a>.

## -see-also

<a href="/windows-hardware/drivers/ddi/ntifs/nf-ntifs-ccinitializecachemap">CcInitializeCacheMap</a>
