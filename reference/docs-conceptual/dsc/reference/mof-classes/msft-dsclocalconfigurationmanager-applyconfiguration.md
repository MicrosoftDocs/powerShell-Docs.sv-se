---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: ApplyConfiguration-metoden
ms.openlocfilehash: 0425b9a7db37e421830ba37da8f5c0a4877a1b72
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941602"
---
# <a name="applyconfiguration-method"></a>ApplyConfiguration-metoden

Använder konfigurations agenten för att tillämpa den konfiguration som väntar.

Om det inte finns någon väntande konfiguration, tillämpar den här metoden den aktuella konfigurationen igen.

## <a name="syntax"></a>Syntax

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>Parametrar

*tvinga* \[in @ no__t-2 om detta är **Sant**tillämpas den aktuella konfigurationen igen, även om det finns en väntande konfiguration.

## <a name="return-value"></a>Returvärde

Returnerar noll vid lyckad; annars returneras en felkod.

## <a name="remarks"></a>Anmärkningar

Detta är en statisk metod.

## <a name="requirements"></a>Krav

**-** DscCore. MOF

**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se även

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
