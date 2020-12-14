---
description: Visar en lista över de cmdletar som har utformats för användning med PowerShell-leverantörer.
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_core_commands?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Core_Commands
ms.openlocfilehash: 1f023c5a66265f561ef6644afdc45cd0149f35b7
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710663"
---
# <a name="about-core-commands"></a>Om Core-kommandon

## <a name="short-description"></a>KORT BESKRIVNING
Visar en lista över de cmdletar som har utformats för användning med PowerShell-leverantörer.

## <a name="long-description"></a>LÅNG BESKRIVNING

PowerShell innehåller en uppsättning cmdletar som är särskilt utformade för att hantera objekt i data lager som exponeras av PowerShell-leverantörer.
Du kan använda dessa cmdlets på samma sätt för att hantera alla olika typer av data som providern gör tillgängliga för dig. Om du vill ha mer information om leverantörer skriver du "Get-Help about_providers".

Du kan till exempel använda cmdleten Get-ChildItem för att lista filerna i en fil system katalog, nycklar under en register nyckel eller de objekt som exponeras av en provider som du skriver eller hämtar.

Följande är en lista över PowerShell-cmdletar som har utformats för användning med providers:

ChildItem-cmdletar

- Get-ChildItem

Innehålls-cmdletar

- Add-Content
- Clear-Content
- Get-Content
- Set-Content

Objekt-cmdletar

- Clear-Item
- Copy-Item
- Get-Item
- Invoke-Item
- Move-Item
- New-Item
- Remove-Item
- Rename-Item
- Set-Item

ItemProperty-cmdletar

- Clear-ItemProperty
- Copy-ItemProperty
- Get-ItemProperty
- Move-ItemProperty
- New-ItemProperty
- Remove-ItemProperty
- Rename-ItemProperty
- Set-ItemProperty

Plats-cmdletar

- Get-Location
- Pop-Location
- Push-Location
- Set-Location

Sök vägs-cmdletar

- Join-Path
- Convert-Path
- Split-Path
- Resolve-Path
- Test-Path

PSDrive-cmdletar

- Get-PSDrive
- New-PSDrive
- Remove-PSDrive

PSProvider-cmdletar

- Get-PSProvider

Om du vill ha mer information om en cmdlet skriver du `get-help <cmdlet-name>` .

## <a name="see-also"></a>SE ÄVEN

[about_Providers](about_Providers.md)

