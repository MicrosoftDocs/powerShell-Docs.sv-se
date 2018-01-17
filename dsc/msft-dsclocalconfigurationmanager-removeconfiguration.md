---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: RemoveConfiguration-metoden i klassen MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: fed45836293adedbce18f01cfe53cdfa1a474975
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
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


 

 



