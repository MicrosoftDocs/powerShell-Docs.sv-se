---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: GetMetaConfiguration-metoden
ms.openlocfilehash: bd280cb8ebd7b0522e4e01cbd24bd9bdcfddf4c2
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
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

*MetaConfiguration* \[ut\] vid retur, innehåller en inbäddad instans av klassen **MSFT_DSCMetaConfiguration** som definierar inställningarna.

## <a name="return-value"></a>Returvärde

Returnerar noll vid lyckad; annars returneras en felkod.

## <a name="remarks"></a>Anmärkningar

Detta är en statisk metod.

## <a name="requirements"></a>Krav

**MOF:** DscCore. MOF

**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se även

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
