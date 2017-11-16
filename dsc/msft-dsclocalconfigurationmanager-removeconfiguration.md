---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: RemoveConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: faa113c442b80eea3ac474220b098b7d80ec50a8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>RemoveConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager

Tar bort konfigurationsfilerna.

<a name="syntax"></a>Syntax
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a>Parametrar
----------

*Steget* \[i\]  
Anger vilken konfiguration dokumentet ska tas bort. Följande värden är giltiga:

|Värde |Beskrivning |
|:--- |:---|
|**1** | Den **aktuella** configuration dokumentet (current.mof). |
|**2** | Den **väntande** configuration dokumentet (pending.mof).  |
|**4** | Den **föregående** configuration dokumentet (previous.mof). |

*Framtvinga* \[i\]  
**SANT** att Framtvinga borttagning av konfigurationen.

## <a name="return-value"></a>Returvärde
------------

Returnerar noll på lyckade; Annars returnerar en felkod.

## <a name="remarks"></a>Anmärkningar

Det här är en statisk metod.

## <a name="requirements"></a>Krav
------------
>**MOF:** DscCore.mof

>**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration


## <a name="see-also"></a>Se även


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)


 

 



