---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: RemoveConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: e0ae8a50212b70841d210d7b2d666a2855218d1a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>RemoveConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen

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

*Steget* \[i\] anger vilken konfiguration dokumentet ska tas bort. Följande värden är giltiga:

|Värde |Beskrivning |
|:--- |:---|
|**1** | Den **aktuella** configuration dokumentet (current.mof). |
|**2** | Den **väntande** configuration dokumentet (pending.mof).  |
|**4** | Den **föregående** configuration dokumentet (previous.mof). |

*Tvinga* \[i\] **SANT** att Framtvinga borttagning av konfigurationen.

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