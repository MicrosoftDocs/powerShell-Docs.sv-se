---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: ResourceSet-metoden
ms.openlocfilehash: 18364027b249e502e1f0b8802d9f3e031c7b07ce
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942652"
---
# <a name="resourceset-method"></a>ResourceSet-metoden

Anropar **set** -metoden för en DSC-resurs direkt.

## <a name="syntax"></a>Syntax

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

## <a name="parameters"></a>Parametrar

*Resurs-\[i*\] namnet på resursen som ska anropas.

*Modulnamn* \[i\] namnet på den modul som innehåller resursen som ska anropas.

*resourceProperty* \[i\] anger resursens egenskaps namn och dess värde i en hash-tabell som nyckel respektive värde. Använd cmdleten [Get-dscresource Keyword Supports](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) för att identifiera resurs egenskaper och deras typer.

*RebootRequired* \[ut\] vid retur anges den här egenskapen till **Sant** om målnoden måste startas om.

## <a name="return-value"></a>Returvärde

Returnerar noll vid lyckad; annars returneras en felkod.

## <a name="remarks"></a>Kommentarer

Detta är en statisk metod.

## <a name="requirements"></a>Krav

**MOF:** DscCore. MOF

**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se också

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
