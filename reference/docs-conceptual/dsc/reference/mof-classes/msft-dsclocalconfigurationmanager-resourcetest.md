---
ms.date: 07/17/2020
ms.topic: reference
title: ResourceTest-metoden
description: ResourceTest-metoden
ms.openlocfilehash: cbac53ea96a59ec92fa840f75cd264a3125b965a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650672"
---
# <a name="resourcetest-method"></a>ResourceTest-metoden

Anropar direkt **test** metoden för en DSC-resurs.

## <a name="syntax"></a>Syntax

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a>Parametrar

**Resourcetype** \[ i \] namnet på resursen som ska anropas.

**Modulnamn** \[ i \] namnet på den modul som innehåller resursen som ska anropas.

**_resourceProperty_* \[ i \] anger resurs egenskapens namn och dess värde i en hash-tabell som nyckel och värde respektive. Använd cmdleten [Get-dscresource Keyword Supports](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) för att identifiera resurs egenskaper och deras typer.

*InDesiredState* *  InDesiredState \[ ut \] vid retur anges den här egenskapen till **Sant** om målnoden är i önskat tillstånd.

## <a name="return-value"></a>Returvärde

Returnerar noll vid lyckad; annars returneras en felkod.

## <a name="remarks"></a>Kommentarer

Detta är en statisk metod.

## <a name="requirements"></a>Krav

**MOF:** DscCore. MOF

**Namnrymd** : Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se även

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
