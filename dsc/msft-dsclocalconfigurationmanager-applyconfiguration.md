---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: ApplyConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klass
ms.openlocfilehash: 2844e354e0d054b13b92267ce314536d88a1c33e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>ApplyConfiguration-metoden för MSFT_DSCLocalConfigurationManager-klass

Använder Configuration Agent för att använda den konfiguration som är i vänteläge.

Om det finns ingen konfiguration väntande, återställer den här metoden den aktuella konfigurationen.


## <a name="syntax"></a>Syntax
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>Parametrar
----------

*Tvinga* \[i\] om det här är **SANT**, den aktuella konfigurationen används igen, även om det finns en konfiguration väntande.

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