---
ms.date: 07/17/2020
ms.topic: reference
title: SendConfigurationApplyAsync-metoden
description: SendConfigurationApplyAsync-metoden
ms.openlocfilehash: 92c9d03a7653e72b1ff04084caea4a8b5aadb0e5
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644796"
---
# <a name="sendconfigurationapplyasync-method"></a>SendConfigurationApplyAsync-metoden

Skickar konfigurations dokumentet asynkront till den hanterade noden och använder konfigurations agenten för att tillämpa konfigurationen.

## <a name="syntax"></a>Syntax

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a>Parametrar

**ConfigurationData** \[ i \] miljö data för konfigurationen.

**tvinga** \[ i \] **True** för att tvinga konfigurationen att stoppas.

**jobId** \[ i \] ID: t för det jobb som du vill skicka konfigurationen för.

## <a name="return-value"></a>Returvärde

Returnerar noll vid lyckad; annars returneras en felkod.

## <a name="remarks"></a>Kommentarer

Detta är en statisk metod.

## <a name="requirements"></a>Krav

**MOF:** DscCore. MOF

**Namnrymd** : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se även

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
