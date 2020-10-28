---
ms.date: 07/14/2020
ms.topic: reference
title: ApplyConfiguration-metoden
description: ApplyConfiguration-metoden
ms.openlocfilehash: aa99221b33d39c3ecc70156a11eaee10b540e2dc
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664272"
---
# <a name="applyconfiguration-method"></a>ApplyConfiguration-metoden

Använder konfigurations agenten för att tillämpa den konfiguration som väntar.

Om det inte finns någon väntande konfiguration, tillämpar den här metoden den aktuella konfigurationen igen.

## <a name="syntax"></a>Syntax

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>Parametrar

### <a name="force"></a>inför

Om detta är **Sant** tillämpas den aktuella konfigurationen igen, även om det finns en väntande konfiguration.

## <a name="return-value"></a>Returvärde

Returnerar noll vid lyckad; annars returneras en felkod.

## <a name="remarks"></a>Kommentarer

Detta är en statisk metod.

## <a name="requirements"></a>Krav

**MOF:** DscCore. MOF

**Namnrymd** : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se även

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
