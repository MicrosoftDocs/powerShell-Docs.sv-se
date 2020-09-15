---
ms.date: 07/17/2020
keywords: DSC, PowerShell, konfiguration, installation
title: RemoveConfiguration-metoden
ms.openlocfilehash: ef15c873d8dfaf28e5cdeb611b72a70921c099be
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464357"
---
# <a name="removeconfiguration-method"></a>RemoveConfiguration-metoden

Tar bort konfigurationsfilerna.

## <a name="syntax"></a>Syntax

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
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

**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se även

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
