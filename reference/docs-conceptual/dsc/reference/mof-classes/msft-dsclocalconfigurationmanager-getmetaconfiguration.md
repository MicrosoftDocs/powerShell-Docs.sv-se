---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: GetMetaConfiguration-metoden
ms.openlocfilehash: bd280cb8ebd7b0522e4e01cbd24bd9bdcfddf4c2
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941567"
---
# <a name="getmetaconfiguration-method"></a>GetMetaConfiguration-metoden

Hämtar de lokala Configuration Manager inställningar som används för att kontrol lera konfigurations agenten.

## <a name="syntax"></a>Syntax

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a>Parametrar

*MetaConfiguration* \[out @ no__t-2 vid retur innehåller en inbäddad instans av **MSFT_DSCMetaConfiguration** -klassen som definierar inställningarna.

## <a name="return-value"></a>Returvärde

Returnerar noll vid lyckad; annars returneras en felkod.

## <a name="remarks"></a>Anmärkningar

Detta är en statisk metod.

## <a name="requirements"></a>Krav

**-** DscCore. MOF

**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se även

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
