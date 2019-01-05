---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: ResourceSet-metoden för MSFT_DSCLocalConfigurationManager-klassen
ms.openlocfilehash: 2712b7ff0a19e643c1f343d436c084f8970c9dd4
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048694"
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a>ResourceSet-metoden för MSFT_DSCLocalConfigurationManager-klassen

Direkt anropar den **ange** -metoden för en DSC-resurs.

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

*ResourceType* \[i\] namnet på resursen att anropa.

*ModuleName* \[i\] namnet på den modul som innehåller resursen som ska anropa.

*resourceProperty* \[i\] anger egenskapen resursnamnet och dess värde i en hash-tabell som nyckel och värde, respektive. Använd den [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet för att identifiera resursegenskaper och deras typer.

*RebootRequired* \[ut\] på RETUR, den här egenskapen anges **SANT** om målnoden måste startas.

## <a name="return-value"></a>Returvärde

Returnerar noll om åtgärden lyckades; Annars returnerar en felkod.

## <a name="remarks"></a>Anmärkningar

Det här är en statisk metod.

## <a name="requirements"></a>Krav

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Se även

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)