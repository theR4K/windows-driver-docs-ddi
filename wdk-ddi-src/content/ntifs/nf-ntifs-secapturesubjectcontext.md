---
UID: NF:ntifs.SeCaptureSubjectContext
title: SeCaptureSubjectContext function (ntifs.h)
description: The SeCaptureSubjectContext routine in ntifs.h captures the security context of the calling thread for access validation and auditing.
old-location: ifsk\secapturesubjectcontext.htm
tech.root: ifsk
ms.date: 04/16/2018
keywords: ["SeCaptureSubjectContext function"]
ms.keywords: SeCaptureSubjectContext, SeCaptureSubjectContext routine [Installable File System Drivers], ifsk.secapturesubjectcontext, ntifs/SeCaptureSubjectContext, seref_192d13d7-4841-4c3e-831f-c12fe3cde04f.xml
req.header: ntifs.h
req.include-header: Ntifs.h, Wdm.h
req.target-type: Universal
req.target-min-winverclnt: 
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
req.irql: PASSIVE_LEVEL
targetos: Windows
req.typenames: 
f1_keywords:
 - SeCaptureSubjectContext
 - ntifs/SeCaptureSubjectContext
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - DllExport
api_location:
 - NtosKrnl.exe
api_name:
 - SeCaptureSubjectContext
---

# SeCaptureSubjectContext function (ntifs.h)


## -description

The <b>SeCaptureSubjectContext</b> routine captures the security context of the calling thread for access validation and auditing.

## -parameters

### -param SubjectContext [out]


Pointer to a caller-allocated <a href="/windows-hardware/drivers/kernel/eprocess">SECURITY_SUBJECT_CONTEXT</a> structure.

## -remarks

The <b>SeCaptureSubjectContext</b> routine returns a pointer to a <a href="/windows-hardware/drivers/kernel/eprocess">SECURITY_SUBJECT_CONTEXT</a> structure, which contains references to access tokens. The contents of that structure can change. The <a href="/windows-hardware/drivers/ddi/ntifs/nf-ntifs-selocksubjectcontext">SeLockSubjectContext</a> routine locks the primary access token and any impersonation tokens associated with the structure.



When using routines that query token information, such as <a href="/windows-hardware/drivers/ddi/ntifs/nf-ntifs-sequeryauthenticationidtoken">SeQueryAuthenticationIdToken</a>, <a href="/windows-hardware/drivers/ddi/ntifs/nf-ntifs-sequerysubjectcontexttoken">SeQuerySubjectContextToken</a>, <a href="/windows-hardware/drivers/ddi/ntifs/nf-ntifs-sequeryinformationtoken">SeQueryInformationToken</a>, and <a href="/windows-hardware/drivers/ddi/ntifs/nf-ntifs-seprivilegecheck">SePrivilegeCheck</a>, more than once in the same security context, lock the subject context with <a href="/windows-hardware/drivers/ddi/ntifs/nf-ntifs-selocksubjectcontext">SeLockSubjectContext</a> to obtain consistent results.

File systems must call <b>SeCaptureSubjectContext</b> before performing access validation or generating audit messages. This is necessary to provide a consistent security context to routines such as <a href="/windows-hardware/drivers/ddi/ntifs/nf-ntifs-sequeryauthenticationidtoken">SeQueryAuthenticationIdToken</a>, <a href="/windows-hardware/drivers/ddi/ntifs/nf-ntifs-sequerysubjectcontexttoken">SeQuerySubjectContextToken</a>, and <a href="/windows-hardware/drivers/ddi/ntifs/nf-ntifs-seprivilegecheck">SePrivilegeCheck</a>. After these operations have been performed, the captured context should be released as soon as possible by calling <a href="/windows-hardware/drivers/ddi/ntifs/nf-ntifs-sereleasesubjectcontext">SeReleaseSubjectContext</a>.

For more information about security and access control, see the documentation on these topics in the Microsoft Windows SDK.

## -see-also

<a href="/windows-hardware/drivers/kernel/eprocess">SECURITY_SUBJECT_CONTEXT</a>



<a href="/windows-hardware/drivers/ddi/ntifs/nf-ntifs-selocksubjectcontext">SeLockSubjectContext</a>



<a href="/windows-hardware/drivers/ddi/ntifs/nf-ntifs-seprivilegecheck">SePrivilegeCheck</a>



<a href="/windows-hardware/drivers/ddi/ntifs/nf-ntifs-sequeryauthenticationidtoken">SeQueryAuthenticationIdToken</a>



<a href="/windows-hardware/drivers/ddi/ntifs/nf-ntifs-sequerysubjectcontexttoken">SeQuerySubjectContextToken</a>



<a href="/windows-hardware/drivers/ddi/ntifs/nf-ntifs-sereleasesubjectcontext">SeReleaseSubjectContext</a>



<a href="/windows-hardware/drivers/ddi/ntifs/nf-ntifs-seunlocksubjectcontext">SeUnlockSubjectContext</a>
