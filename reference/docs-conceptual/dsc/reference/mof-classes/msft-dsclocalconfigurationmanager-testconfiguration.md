---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: TestConfiguration-metoden
ms.openlocfilehash: 384134212e3b29b63dc045aee4b708c87c970302
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942589"
---
# <a name="testconfiguration-method"></a>TestConfiguration-metoden

Skickar konfigurations dokumentet till den hanterade noden och verifierar den aktuella konfigurationen mot dokumentet.

## <a name="syntax"></a>Syntax

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a>Parametrar

*configurationData* \[in @ no__t-2-miljö data för confuguration.

*InDesiredState* \[out @ no__t-2 vid retur anger om den hanterade noden är i det tillstånd som anges av konfigurations dokumentet.

*ResourcesInDesiredState* \[out @ no__t-2 vid retur innehåller en inbäddad instans av **MSFT_ResourceInDesiredState** -klassen som anger resurser som är i önskat tillstånd.

*ResourcesNotInDesiredState* \[out @ no__t-2 vid retur innehåller en inbäddad instans av **MSFT_ResourceNotInDesiredState** -klassen som anger resurser som inte är i önskat tillstånd.

## <a name="return-value"></a>Returvärde

Returnerar noll vid lyckad; annars returneras en felkod.

## <a name="remarks"></a>Anmärkningar

Detta är en statisk metod.

## <a name="requirements"></a>Krav

**-** DscCore. MOF

**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se även

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
