---
ms.date: 07/17/2020
ms.topic: reference
title: RemoveConfiguration-metoden
description: RemoveConfiguration-metoden
ms.openlocfilehash: d5988ac014c457407c56a097c9a376427376eb3f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650733"
---
# <a name="removeconfiguration-method"></a>RemoveConfiguration-metoden

Tar bort konfigurationsfilerna.

## <a name="syntax"></a>Syntax

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a>Parametrar

**Steg** \[ i \] anger vilket konfigurations dokument som ska tas bort. Följande värden är giltiga:

|Värde |Beskrivning |
|:--- |:---|
|**1** | **Aktuellt** konfigurations dokument (aktuell. MOF). |
|**2** | **Väntande** konfigurations dokument (väntar. MOF).  |
|**4** | **Föregående** konfigurations dokument (föregående. MOF). |

*Tvinga* \[ i \] **True** för att framtvinga borttagning av konfigurationen.

## <a name="return-value"></a>Returvärde

Returnerar noll vid lyckad; annars returneras en felkod.

## <a name="remarks"></a>Kommentarer

Detta är en statisk metod.

## <a name="requirements"></a>Krav

**MOF:** DscCore. MOF

**Namnrymd** : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se även

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
