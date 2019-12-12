---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: TestConfiguration-metoden
ms.openlocfilehash: 384134212e3b29b63dc045aee4b708c87c970302
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
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

*configurationData* \[i\] miljö data för confuguration.

*InDesiredState* \[ut\] vid retur anger om den hanterade noden är i det tillstånd som anges av konfigurations dokumentet.

*ResourcesInDesiredState* \[ut\] vid retur innehåller en inbäddad instans av **MSFT_ResourceInDesiredState** -klassen som anger resurser som är i önskat tillstånd.

*ResourcesNotInDesiredState* \[ut\] vid retur innehåller en inbäddad instans av **MSFT_ResourceNotInDesiredState** -klassen som anger resurser som inte är i önskat tillstånd.

## <a name="return-value"></a>Returvärde

Returnerar noll vid lyckad; annars returneras en felkod.

## <a name="remarks"></a>Anmärkningar

Detta är en statisk metod.

## <a name="requirements"></a>Krav

**MOF:** DscCore. MOF

**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se även

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
