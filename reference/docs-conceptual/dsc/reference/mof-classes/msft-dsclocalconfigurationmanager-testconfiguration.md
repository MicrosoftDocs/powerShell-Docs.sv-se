---
ms.date: 07/17/2020
ms.topic: reference
title: TestConfiguration-metoden
description: TestConfiguration-metoden
ms.openlocfilehash: ed26fcad2286ca753fb4b1845b8c6ad0741d491b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648920"
---
# <a name="testconfiguration-method"></a>TestConfiguration-metoden

Skickar konfigurations dokumentet till den hanterade noden och verifierar den aktuella konfigurationen mot dokumentet.

## <a name="syntax"></a>Syntax

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a>Parametrar

**configurationData** \[ i \] miljö data för konfigurationen.

**InDesiredState** \[ ut \] vid retur anger om den hanterade noden är i det tillstånd som anges av konfigurations dokumentet.

**ResourcesInDesiredState** \[ ut \] vid retur innehåller en inbäddad instans av klassen **MSFT_ResourceInDesiredState** som anger vilka resurser som är i önskat tillstånd.

**ResourcesNotInDesiredState** \[ ut \] vid retur innehåller en inbäddad instans av klassen **MSFT_ResourceNotInDesiredState** som anger resurser som inte är i önskat tillstånd.

## <a name="return-value"></a>Returvärde

Returnerar noll vid lyckad; annars returneras en felkod.

## <a name="remarks"></a>Kommentarer

Detta är en statisk metod.

## <a name="requirements"></a>Krav

**MOF:** DscCore. MOF

**Namnrymd** : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se även

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
