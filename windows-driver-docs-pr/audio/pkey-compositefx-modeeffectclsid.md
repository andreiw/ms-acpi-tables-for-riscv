---
title: PKEY\_CompositeFX\_ModeEffectClsid
description: In Windows 10 Version 1803 later, the PKEY\_Compositefx\_ModeEffectClsid property key identifies the mode effect (MFX) supported by the driver. The driver developer should specify the list of supported processing modes that their driver supports.
ms.date: 03/06/2023
ms.topic: reference
---

# PKEY\_CompositeFX\_ModeEffectClsid

In Windows 10 Version 1803 and later, the **PKEY\_CompositeFX\_ModeEffectClsid** property key identifies the mode effect (MFX) supported by the driver. The driver developer should specify the list of supported processing modes that their driver supports.

This property key is identical to the [PKEY\_FX\_ModeEffectClsid](pkey-fx-modeeffectclsid.md) property key, but it is a composite that is expressed as a reg multistring in the registry to allow multiple effects in a single position.

The INF file property key instructs the audio endpoint builder to set the CLSIDs for endpoint APOs into the effects property store. This information is used to build the audio graph that will be used to inform upper level apps what effects are in place.

## <span id="INF_File_Sample"></span><span id="inf_file_sample"></span><span id="INF_FILE_SAMPLE"></span>INF File Sample

An INF file specifies settings for an audio mode effect in the add-registry section for that device. The following INF example shows the strings and add-registry section that loads the APO for a mode effect into the registry.

```inf
[Strings]
PKEY_CompositeFX_ModeEffectClsid     = "{D04E05A6-594B-4fb6-A80D-01AF5EED7D1D},14"
...
; Driver developers should replace this CLSIDs with that of their own APO
SWAP_FX_MODE_CLSID      = "{00000000-0000-0000-0000-000000000000}"
DELAY_FX_STREAM_CLSID   = "{00000000-0000-0000-0000-000000000000}"
...
 
[SWAPAPO.I.Association0.AddReg]
HKR,FX\0,%PKEY_CompositeFX_ModeEffectClsid%,0x00010000,%SWAP_FX_MODE_CLSID%,%DELAY_FX_MODE_CLSID%

```

## <span id="related_topics"></span>Related topics


[Media-Class INF Extensions](media-class-inf-extensions.md)

 

 






