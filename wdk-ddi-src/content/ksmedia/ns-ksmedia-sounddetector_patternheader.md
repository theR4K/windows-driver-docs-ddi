---
UID: NS:ksmedia.__unnamed_struct_40
title: SOUNDDETECTOR_PATTERNHEADER (ksmedia.h)
description: The SOUNDDETECTOR_PATTERNHEADER structure (ksmedia.h) specifies the pattern header for the sound detector.
old-location: audio\sounddetector_patternheader.htm
tech.root: audio
ms.date: 04/30/2019
keywords: ["SOUNDDETECTOR_PATTERNHEADER structure"]
ms.keywords: SOUNDDETECTOR_PATTERNHEADER, SOUNDDETECTOR_PATTERNHEADER structure [Audio Devices], audio.sounddetector_patternheader, ksmedia/SOUNDDETECTOR_PATTERNHEADER
req.header: ksmedia.h
req.include-header: Keyworddetectoroemadapter.h
req.target-type: Windows
req.target-min-winverclnt: Windows 10
req.target-min-winversvr: Windows Server 2016
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
req.typenames: SOUNDDETECTOR_PATTERNHEADER
f1_keywords:
 - SOUNDDETECTOR_PATTERNHEADER
 - ksmedia/SOUNDDETECTOR_PATTERNHEADER
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - HeaderDef
api_location:
 - ksmedia.h
api_name:
 - SOUNDDETECTOR_PATTERNHEADER
---

# SOUNDDETECTOR_PATTERNHEADER structure (ksmedia.h) (ksmedia.h)


## -description

The **SOUNDDETECTOR_PATTERNHEADER** structure specifies the pattern header for the sound detector in the [KSPROPERTY_SOUNDDETECTOR_PATTERNS](/windows-hardware/drivers/audio/ksproperty-sounddetector-patterns) property.

## -struct-fields

### -field Size

The size of the audio data.

### -field PatternType

The keyword pattern format, expressed as a GUID.

## -see-also

[KSPROPERTY_SOUNDDETECTOR_PATTERNS](/windows-hardware/drivers/audio/ksproperty-sounddetector-patterns)
