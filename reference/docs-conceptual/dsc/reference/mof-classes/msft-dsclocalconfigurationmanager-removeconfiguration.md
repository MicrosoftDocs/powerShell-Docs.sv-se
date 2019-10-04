---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: RemoveConfiguration-metoden
ms.openlocfilehash: aacbed96beb960d7e0d449423a4de9a27f0a287e
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941560"
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

*Stage* \[in @ no__t-2 anger vilket konfigurations dokument som ska tas bort. Följande värden är giltiga:

|Value |Beskrivning |
|:--- |:---|
|**1** | **Aktuellt** konfigurations dokument (aktuell. MOF). |
|**2** | **Väntande** konfigurations dokument (väntar. MOF).  |
|**4** | **Föregående** konfigurations dokument (föregående. MOF). |

*Framtvinga* \[in @ no__t-2 **True** för att framtvinga borttagning av konfigurationen.

## <a name="return-value"></a>Returvärde

Returnerar noll vid lyckad; annars returneras en felkod.

## <a name="remarks"></a>Anmärkningar

Detta är en statisk metod.

## <a name="requirements"></a>Krav

**-** DscCore. MOF

**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se även

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
