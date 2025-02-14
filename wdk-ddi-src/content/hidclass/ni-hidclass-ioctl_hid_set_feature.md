---
UID: NI:hidclass.IOCTL_HID_SET_FEATURE
title: IOCTL_HID_SET_FEATURE (hidclass.h)
description: The IOCTL_HID_SET_FEATURE request sends a feature report to a top-level collection.
old-location: hid\ioctl_hid_set_feature2.htm
tech.root: hid
ms.date: 04/28/2022
keywords: ["IOCTL_HID_SET_FEATURE IOCTL"]
ms.keywords: IOCTL_HID_SET_FEATURE, IOCTL_HID_SET_FEATURE control, IOCTL_HID_SET_FEATURE control code [Human Input Devices], hid.ioctl_hid_set_feature2, hidclass/IOCTL_HID_SET_FEATURE, hidioreq_def58360-8e73-49dd-ab90-33cf3b6a92de.xml
req.header: hidclass.h
req.include-header: Hidclass.h
req.target-type: Windows
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
req.lib: 
req.dll: 
req.irql: 
targetos: Windows
req.typenames: 
f1_keywords:
 - IOCTL_HID_SET_FEATURE
 - hidclass/IOCTL_HID_SET_FEATURE
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - HeaderDef
api_location:
 - hidclass.h
api_name:
 - IOCTL_HID_SET_FEATURE
---

# IOCTL_HID_SET_FEATURE IOCTL

## -description

The IOCTL_HID_SET_FEATURE request sends a feature report to a [top-level collection](/windows-hardware/drivers/hid/top-level-collections).

For general information about HIDClass devices, see [HID Collections](/windows-hardware/drivers/hid/hid-collections).

## -ioctlparameters

### -input-buffer

The `Parameters.DeviceIoControl.InputBufferLength` member is set to the size, in bytes, of a requester-allocated input buffer that contains a HID class feature report.

The size of the input buffer in bytes. The buffer must be large enough to hold the feature report plus one additional byte that specifies a nonzero report ID. If report ID is not used, the ID value is zero.

The `Irp->AssociatedIrp.SystemBuffer` member points to the input buffer that contains a feature report. If the collection includes report IDs, the requester must set the first byte of the buffer to a nonzero report ID; otherwise the requester must set the first byte to zero. The feature report is located at `((PUCHAR)ReportBuffer + 1)`.

**Minidriver handling**

`Irp->UserBuffer` points to a [HID_XFER_PACKET](./ns-hidclass-_hid_xfer_packet.md) structure that the HID class driver uses to input the following members:

### -input-buffer-length

The size of the input buffer in bytes. The buffer must be large enough to hold the output report plus one additional byte that specifies a nonzero report ID. If report ID is not used, the ID value is zero.

**Minidriver handling**

The size of a [HID_XFER_PACKET](./ns-hidclass-_hid_xfer_packet.md) structure.

### -output-buffer

None.

### -output-buffer-length

None.

### -in-out-buffer

### -inout-buffer-length

### -status-block

The HID class driver sets the following fields of `Irp->IoStatus`:

- *Information* is set to zero.
- *Status* is set to STATUS_SUCCESS if the transfer completed without error. Otherwise, it is set to an appropriate NTSTATUS error code

**Minidriver handling**

HID minidrivers that carry out the I/O to the device set the following fields of `Irp->IoStatus`:

- *Information* is set to the number of bytes transferred to the device.
- *Status* is set to STATUS_SUCCESS if the transfer completed without error. Otherwise, it is set to an appropriate NTSTATUS error code.

HID minidrivers that call other drivers with this IOCTL to carry out the I/O, should ensure that the *Information* field of the status block is correct and not change the contents of the *Status* field.

## -ReportID

Specifies the report ID for a top-level collection.

## -reportBuffer

Pointer to a requester-allocated input buffer that contains a feature report.

## -reportBufferLen

Specifies the size, in bytes, of the input buffer.

## -see-also

- [HidD_GetFeature](../hidsdi/nf-hidsdi-hidd_getfeature.md)
- [HidD_GetInputReport](../hidsdi/nf-hidsdi-hidd_getinputreport.md)
- [HidD_SetFeature](../hidsdi/nf-hidsdi-hidd_setfeature.md)
- [HidD_SetOutputReport](../hidsdi/nf-hidsdi-hidd_setoutputreport.md)
- [IOCTL_HID_GET_INPUT_REPORT](./ni-hidclass-ioctl_hid_get_input_report.md)
- [IOCTL_HID_SET_OUTPUT_REPORT](./ni-hidclass-ioctl_hid_set_output_report.md)
