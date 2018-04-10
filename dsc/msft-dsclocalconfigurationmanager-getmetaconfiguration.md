---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: GetMetaConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: ddc016402239bcdea060a717fbac9ab7ea42698c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>GetMetaConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klassen

Hämtar den lokala Configuration Manager-inställningar som används för att styra Configuration Agent.

<a name="syntax"></a>Syntax
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a>Parametrar
----------

*Metakonfigurationen* \[ut\] på RETUR, innehåller en inbäddad instans av den **MSFT_DSCMetaConfiguration** klass som definierar inställningar.

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