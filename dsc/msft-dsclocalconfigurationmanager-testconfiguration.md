---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: TestConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: 7815d458a9a67639a31c917510097212d104eb8a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>TestConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen

Skickar konfiguration dokumentet till hanterade noder och verifierar den aktuella konfigurationen mot dokumentet.

<a name="syntax"></a>Syntax
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

<a name="parameters"></a>Parametrar
----------

*configurationData* \[i\] miljödata för confuguration.

*InDesiredState* \[ut\] på RETUR, anger om hanterad nod är i tillståndet anges i configuration-dokumentet.

*ResourcesInDesiredState* \[ut\] på RETUR, innehåller en inbäddad instans av den **MSFT_ResourceInDesiredState** klass som anger resurser som ingår i tillståndet.

*ResourcesNotInDesiredState* \[ut\] på RETUR, innehåller en inbäddad instans av den **MSFT_ResourceNotInDesiredState** klass som anger resurser som inte är i tillståndet önskade.

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