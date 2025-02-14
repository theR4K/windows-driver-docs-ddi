---
UID: NF:ntifs.FsRtlRemovePerStreamContext
title: FsRtlRemovePerStreamContext function (ntifs.h)
description: FsRtlRemovePerStreamContext removes a per-stream context structure from the list of per-stream contexts associated with a file stream.
old-location: ifsk\fsrtlremoveperstreamcontext.htm
tech.root: ifsk
ms.date: 04/16/2018
keywords: ["FsRtlRemovePerStreamContext function"]
ms.keywords: FsRtlRemovePerStreamContext, FsRtlRemovePerStreamContext function [Installable File System Drivers], fsrtlref_904bd4dd-c254-4762-8af6-dcc49aaa5c92.xml, ifsk.fsrtlremoveperstreamcontext, ntifs/FsRtlRemovePerStreamContext
req.header: ntifs.h
req.include-header: Ntifs.h
req.target-type: Universal
req.target-min-winverclnt: This routine is available on Update Rollup for Windows 2000 Service Pack 4 (SP4) and on Microsoft Windows XP and later.
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
 - FsRtlRemovePerStreamContext
 - ntifs/FsRtlRemovePerStreamContext
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - DllExport
api_location:
 - NtosKrnl.exe
api_name:
 - FsRtlRemovePerStreamContext
---

# FsRtlRemovePerStreamContext function


## -description

<b>FsRtlRemovePerStreamContext</b> removes a per-stream context structure from the list of per-stream contexts associated with a file stream.

## -parameters

### -param StreamContext [in]


Pointer to the FSRTL_ADVANCED_FCB_HEADER structure for the file stream. To get this pointer from a file object, use the <a href="/windows-hardware/drivers/ddi/ntifs/nf-ntifs-fsrtlgetperstreamcontextpointer">FsRtlGetPerStreamContextPointer</a> macro.

### -param OwnerId [in, optional]


Used to identify context information as belonging to a particular filter driver.

### -param InstanceId [in, optional]


Used to search for a particular instance of a per-stream context. If not provided, any of the contexts owned by the filter driver is removed and returned. 

If neither the <i>OwnerId</i> nor the <i>InstanceId</i> is provided, any associated per-stream context will be removed and returned.

## -returns

<b>FsRtlRemovePerStreamContext</b> returns a pointer to the per-stream context that is removed. If no match is found, or if the file system does not support filter contexts, <b>FsRtlRemovePerStreamContext</b> returns <b>NULL</b>.

## -remarks

A file system filter driver calls <b>FsRtlRemovePerStreamContext</b> to remove its own per-stream context structure from the list of per-stream contexts associated with a file stream. 

<div class="alert"><b>Note</b>  <b>FsRtlRemovePerStreamContext</b> removes only the first matching per-stream context structure that is found. If there are additional matching per-stream contexts, the filter driver must call <b>FsRtlRemovePerStreamContext</b> as many times as required to remove them all.</div>
<div> </div>
This routine should only be used when a filter driver needs to discard the context information it has associated with a file stream while the stream is still open. For example, a filter driver might call <b>FsRtlRemovePerStreamContext</b> in the following cases: 

<ul>
<li>
When it receives a request from a user-mode application to stop logging I/O requests on a particular volume. 

</li>
<li>
When it detects that a file or directory has been renamed. 

</li>
</ul>
When a file stream is closed, the file system is responsible for ensuring that all per-stream contexts associated with that stream are removed and freed. To do this, the file system must call <a href="/windows-hardware/drivers/ddi/ntifs/nf-ntifs-fsrtlteardownperstreamcontexts">FsRtlTeardownPerStreamContexts</a> on the file control block (FCB) or other stream context object for the file stream. <b>FsRtlTeardownPerStreamContexts</b> walks the FilterContexts list, removing each entry and calling its <i>FreeCallback</i> routine. 

Thus, a file system filter driver should not call <b>FsRtlRemovePerStreamContext</b> from within an IRP_MJ_CLOSE or IRP_MJ_PNP dispatch routine. Not only would such a call be unnecessary, but it might also interfere with the file system's call to <a href="/windows-hardware/drivers/ddi/ntifs/nf-ntifs-fsrtlteardownperstreamcontexts">FsRtlTeardownPerStreamContexts</a>. 

<div class="alert"><b>Note</b>    A file system filter driver should not call <b>FsRtlRemovePerStreamContext</b> from within a per-stream context structure's <i>FreeCallback</i> routine. This is because the underlying file system calls the <i>FreeCallback</i> routine after it has already removed the context structure from the FilterContexts list.</div>
<div> </div>
To initialize a per-stream context structure, use the <a href="/windows-hardware/drivers/ddi/ntifs/nf-ntifs-fsrtlinitperstreamcontext">FsRtlInitPerStreamContext</a> macro. 

To associate an initialized per-stream context structure with a file stream, call <a href="/windows-hardware/drivers/ddi/ntifs/nf-ntifs-fsrtlinsertperstreamcontext">FsRtlInsertPerStreamContext</a>. 

To retrieve a per-stream context structure that is associated with a file stream, call <a href="/windows-hardware/drivers/ddi/ntifs/nf-ntifs-fsrtllookupperstreamcontext">FsRtlLookupPerStreamContext</a>. 

<b>FsRtlRemovePerStreamContext</b> can only be used on file systems that support filter contexts. 

For more information, see <a href="/windows-hardware/drivers/ifs/tracking-per-stream-context-in-a-legacy-file-system-filter-driver">Tracking Per-Stream Context in a Legacy File System Filter Driver</a>.

## -see-also

<a href="/windows-hardware/drivers/ddi/ntifs/ns-ntifs-_fsrtl_advanced_fcb_header">FSRTL_ADVANCED_FCB_HEADER</a>



<a href="/previous-versions/ff547357(v=vs.85)">FSRTL_PER_STREAM_CONTEXT</a>



<a href="/windows-hardware/drivers/ddi/ntifs/nf-ntifs-fsrtlgetperstreamcontextpointer">FsRtlGetPerStreamContextPointer</a>



<a href="/windows-hardware/drivers/ddi/ntifs/nf-ntifs-fsrtlinitperstreamcontext">FsRtlInitPerStreamContext</a>



<a href="/windows-hardware/drivers/ddi/ntifs/nf-ntifs-fsrtlinsertperstreamcontext">FsRtlInsertPerStreamContext</a>



<a href="/windows-hardware/drivers/ddi/ntifs/nf-ntifs-fsrtllookupperstreamcontext">FsRtlLookupPerStreamContext</a>



<a href="/previous-versions/ff547257(v=vs.85)">FsRtlSetupAdvancedHeader</a>



<a href="/previous-versions/ff547285(v=vs.85)">FsRtlSupportsPerStreamContexts</a>



<a href="/windows-hardware/drivers/ddi/ntifs/nf-ntifs-fsrtlteardownperstreamcontexts">FsRtlTeardownPerStreamContexts</a>



<a href="/windows-hardware/drivers/kernel/irp-mj-close">IRP_MJ_CLOSE</a>



<a href="/windows-hardware/drivers/ifs/irp-mj-pnp">IRP_MJ_PNP</a>
