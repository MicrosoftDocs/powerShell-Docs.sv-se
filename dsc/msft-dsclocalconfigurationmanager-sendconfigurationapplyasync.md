---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: SendConfigurationApplyAsync-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: 7ff821a277a548869862741551ee9897e417ea45
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a>SendConfigurationApplyAsync-metoden för MSFT_DSCLocalConfigurationManager-klassen

Skickar konfiguration dokumentet asynkront till noden hanterade används Configuration Agent för att tillämpa konfigurationen.

<a name="syntax"></a>Syntax
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a>Parametrar
----------

*ConfigurationData* \[i\] miljödata för konfigurationen.

*Tvinga* \[i\] **SANT** att tvinga konfigurationen som ska sluta.

*jobId* \[i\] ID för jobbet för att skicka konfigurationen.

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