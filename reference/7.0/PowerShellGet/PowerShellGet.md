---
Download Help Link: https://go.microsoft.com/fwlink/?linkid=2113539
Help Version: 7.0.1.0
keywords: powershell,cmdlet
Locale: en-US
Module Guid: 1d73a601-4a6c-43c5-ba3f-619b18bbb404
Module Name: PowerShellGet
ms.date: 06/09/2017
schema: 2.0.0
title: PowerShellGet
ms.openlocfilehash: b4988bdfa027c439436073d683e1cc1013294fc8
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94890465"
---
# PowerShellGet-modul

## Beskrivning

PowerShellGet är en modul med kommandon för att upptäcka, installera, uppdatera och publicera PowerShell-artefakter som moduler, DSC-resurser, roll funktioner och skript.

> [!IMPORTANT]
> Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1. Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet. Använd följande kommando för att se till att du använder TLS 1,2:
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.

## PowerShellGet-cmdletar

### [Sök-kommando](Find-Command.md)
Söker efter PowerShell-kommandon i moduler.

### [Find-Dscresource Keyword Supports](Find-DscResource.md)
Söker efter Desired State Configuration (DSC)-resurser.

### [Sök-modul](Find-Module.md)
Söker efter moduler i en lagrings plats som matchar de angivna kriterierna.

### [Find-RoleCapability](Find-RoleCapability.md)
Hittar roll funktioner i moduler.

### [Sök – skript](Find-Script.md)
Söker efter ett skript.

### [Get-InstalledModule](Get-InstalledModule.md)
Hämtar en lista över moduler på den dator som har installerats av PowerShellGet.

### [Get-InstalledScript](Get-InstalledScript.md)
Hämtar ett installerat skript.

### [Get-PSRepository](Get-PSRepository.md)
Hämtar PowerShell-databaser.

### [Installera-modul](Install-Module.md)
Laddar ned en eller flera moduler från en lagrings plats och installerar dem på den lokala datorn.

### [Installera – skript](Install-Script.md)
Installerar ett skript.

### [New-ScriptFileInfo](New-ScriptFileInfo.md)
Skapar en skript fil med metadata.

### [Publicera-modul](Publish-Module.md)
Publicerar en angiven modul från den lokala datorn till ett onlinegalleri.

### [Publicera – skript](Publish-Script.md)
Publicerar ett skript.

### [Registrera – PSRepository](Register-PSRepository.md)
Registrerar en PowerShell-lagringsplats.

### [Spara-modul](Save-Module.md)
Sparar en modul och dess beroenden på den lokala datorn, men installerar inte modulen.

### [Spara – skript](Save-Script.md)
Sparar ett skript.

### [Set-PSRepository](Set-PSRepository.md)
Anger värden för en registrerad lagrings plats.

### [Test-ScriptFileInfo](Test-ScriptFileInfo.md)
Verifierar ett kommentar block för ett skript.

### [Avinstallera-modul](Uninstall-Module.md)
Avinstallerar en modul.

### [Avinstallera – skript](Uninstall-Script.md)
Avinstallerar ett skript.

### [Avregistrera-PSRepository](Unregister-PSRepository.md)
Avregistrerar en lagrings plats.

### [Update-modul](Update-Module.md)
Hämtar och installerar den senaste versionen av angivna moduler från ett onlinegalleri till den lokala datorn.

### [Uppdatera – ModuleManifest](Update-ModuleManifest.md)
Uppdaterar en modul manifest fil.

### [Uppdatera skript](Update-Script.md)
Uppdaterar ett skript.

### [Update-ScriptFileInfo](Update-ScriptFileInfo.md)
Uppdaterings information för ett skript.

