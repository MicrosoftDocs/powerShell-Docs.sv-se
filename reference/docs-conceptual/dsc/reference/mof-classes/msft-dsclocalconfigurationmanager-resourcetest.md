---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: ResourceTest-metoden
ms.openlocfilehash: ff06fd645a94055e79aa0f8d20f2f06e16483720
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942645"
---
# <a name="resourcetest-method"></a>ResourceTest-metoden

Anropar direkt **test** metoden för en DSC-resurs.

## <a name="syntax"></a>Syntax

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a>Parametrar

*ResourceType* \[in @ no__t-2 namnet på resursen som ska anropas.

*Modulnamn* \[in @ no__t-2 namnet på den modul som innehåller resursen som ska anropas.

*resourceProperty* \[in @ no__t-2 anger resursens egenskaps namn och dess värde i en hash-tabell som nyckel respektive värde. Använd cmdleten [Get-dscresource Keyword Supports](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) för att identifiera resurs egenskaper och deras typer.

*InDesiredState* \[out @ no__t-2 vid retur anges den här egenskapen till **Sant** om målnoden är i önskat tillstånd.

## <a name="return-value"></a>Returvärde

Returnerar noll vid lyckad; annars returneras en felkod.

## <a name="remarks"></a>Anmärkningar

Detta är en statisk metod.

## <a name="requirements"></a>Krav

**-** DscCore. MOF

**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se även

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
