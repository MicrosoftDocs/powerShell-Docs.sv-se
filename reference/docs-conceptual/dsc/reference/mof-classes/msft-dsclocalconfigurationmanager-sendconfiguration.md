---
ms.date: 07/17/2020
ms.topic: reference
title: SendConfiguration-metoden
description: SendConfiguration-metoden
ms.openlocfilehash: 3939a76ab6672b49559847b0ef1408f1c7be6d0c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650551"
---
# <a name="sendconfiguration-method"></a>SendConfiguration-metoden

Skickar konfigurations dokumentet till den hanterade noden och sparar det som en väntande ändring.

## <a name="syntax"></a>Syntax

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a>Parametrar

**ConfigurationData** \[ i \] miljö data för konfigurationen.

**tvinga** \[ i \] **True** för att tvinga konfigurationen att stoppas.

## <a name="return-value"></a>Returvärde

Returnerar noll vid lyckad; annars returneras en felkod.

## <a name="remarks"></a>Kommentarer

Detta är en statisk metod.

## <a name="requirements"></a>Krav

**MOF:** DscCore. MOF

**Namnrymd** : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se även

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
