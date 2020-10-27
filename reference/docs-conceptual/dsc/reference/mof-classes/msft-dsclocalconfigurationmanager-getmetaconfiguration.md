---
ms.date: 07/17/2020
ms.topic: reference
title: GetMetaConfiguration-metoden
description: GetMetaConfiguration-metoden
ms.openlocfilehash: deca6b8ec342a34543bbe0e1fabbc2a740a88feb
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644720"
---
# <a name="getmetaconfiguration-method"></a>GetMetaConfiguration-metoden

Hämtar de lokala Configuration Manager inställningar som används för att kontrol lera konfigurations agenten.

## <a name="syntax"></a>Syntax

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a>Parametrar

**MetaConfiguration** \[ ut \] vid retur innehåller en inbäddad instans av klassen **MSFT_DSCMetaConfiguration** som definierar inställningarna.

## <a name="return-value"></a>Returvärde

Returnerar noll vid lyckad; annars returneras en felkod.

## <a name="remarks"></a>Kommentarer

Detta är en statisk metod.

## <a name="requirements"></a>Krav

**MOF:** DscCore. MOF

**Namnrymd** : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se även

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
