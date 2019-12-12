---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: ResourceGet-metoden
ms.openlocfilehash: dbe610dfcef5ef6c79783801ecb6fdb7408bdfa5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71942680"
---
# <a name="resourceget-method"></a>ResourceGet-metoden

Anropar direkt **Get** -metoden för en DSC-resurs.

## <a name="syntax"></a>Syntax

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

## <a name="parameters"></a>Parametrar

*Resurs-\[i*\] namnet på resursen som ska anropas.

*Modulnamn* \[i\] namnet på den modul som innehåller resursen som ska anropas.

*resourceProperty* \[i\] anger resursens egenskaps namn och dess värde i en hash-tabell som nyckel respektive värde. Använd cmdleten [Get-dscresource Keyword Supports](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) för att identifiera resurs egenskaper och deras typer.

*konfigurationer* \[ut\] vid retur innehåller en inbäddad instans av konfigurationerna.

## <a name="return-value"></a>Returvärde

Returnerar noll vid lyckad; annars returneras en felkod.

## <a name="remarks"></a>Anmärkningar

Detta är en statisk metod.

## <a name="requirements"></a>Krav

**MOF:** DscCore. MOF

**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se även

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
