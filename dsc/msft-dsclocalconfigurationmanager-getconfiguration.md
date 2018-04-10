---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: GetConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: 07d7db9dcc4288e6b72d5df37d82e44eb6f72ad2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>GetConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen

Skickar konfiguration dokumentet till hanterade noder och använder den **hämta** metod för att tillämpa konfigurationen Configuration Agent.

<a name="syntax"></a>Syntax
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a>Parametrar
----------

*configurationData* \[i\] anger konfigurationsdata för att skicka.

*konfigurationer* \[ut\] på RETUR, innehåller en inbäddad instans av konfigurationer.

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