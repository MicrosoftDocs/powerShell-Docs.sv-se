---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: GetConfigurationStatus-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: dde4ac003b346018561481e05ca7374475f9ff1d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a>GetConfigurationStatus-metoden för MSFT_DSCLocalConfigurationManager-klassen

Hämta statushistorik konfiguration.

<a name="syntax"></a>Syntax
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a>Parametrar
----------

*Alla* \[i\] **SANT** om den här metoden ska returnera information om alla konfigurationen som körs på datorn, inklusive program för konfiguration och konsekvenskontrollen.

*configurationStatus* \[ut\] på RETUR, innehåller en inbäddad instans av den **MSFT_DSCConfigurationStatus** klass som definierar inställningar.

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