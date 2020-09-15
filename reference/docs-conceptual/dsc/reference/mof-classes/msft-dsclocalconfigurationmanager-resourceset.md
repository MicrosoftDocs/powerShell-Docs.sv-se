---
ms.date: 07/17/2020
keywords: DSC, PowerShell, konfiguration, installation
title: ResourceSet-metoden
ms.openlocfilehash: c015960b2a5ffca0d28b714d571aa616400555bd
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/18/2020
ms.locfileid: "86464067"
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

**Resourcetype** \[ i \] namnet på resursen som ska anropas.

**Modulnamn** \[ i \] namnet på den modul som innehåller resursen som ska anropas.

**resourceProperty** \[ i \] anger resurs egenskapens namn och dess värde i en hash-tabell som nyckel och värde respektive. Använd cmdleten [Get-dscresource Keyword Supports](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) för att identifiera resurs egenskaper och deras typer.

**RebootRequired** \[ ut \] vid retur anges den här egenskapen till **Sant** om målnoden måste startas om.

## <a name="return-value"></a>Returvärde

Returnerar noll vid lyckad; annars returneras en felkod.

## <a name="remarks"></a>Kommentarer

Detta är en statisk metod.

## <a name="requirements"></a>Krav

**MOF:** DscCore. MOF

**Namnrymd**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se även

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
