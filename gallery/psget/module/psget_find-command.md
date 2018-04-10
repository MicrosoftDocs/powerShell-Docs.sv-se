---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: galleriet, powershell, cmdlet, psget
title: Kommandot Sök
ms.openlocfilehash: 26ddf4824816db245131a0fc95b7d2a88bef8f4c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="find-command"></a>Kommandot Sök

Söker efter PowerShell-kommandon i moduler.

## <a name="description"></a>Beskrivning
Kommandot Sök cmdleten hittar PowerShell-kommandon, till exempel-cmdlet: ar, alias, funktioner och arbetsflöden. Kommandot Sök söker moduler i registrerade databaser.
För varje kommando som den här cmdleten söker efter, returneras ett PSGetCommandInfo-objekt. Du kan överföra ett PSGetCommandInfo-objekt till cmdleten Install-Module så här installerar du den modul som innehåller kommandot.

- Sök-kommandot kan du filtrera med parametrarna: MinimumVersion, RequiredVersion, allaversioner.
  - Dessa parametrar kan inte anges samtidigt.
  - De här parametrarna tillåts endast med enda modulnamnet utan några jokertecken.
  - Om parametern RequiredVersion inte anges returnerar kommandot Sök den senaste versionen av den modul som är lika med eller större än den angivna lägsta versionen eller den senaste versionen av modulen om ingen minsta version anges.
  - Om parametern RequiredVersion har angetts returnerar kommandot Sök endast versionen av den modul som exakt matchar den angivna versionen.
- Sök-kommandot kan du filtrera på modulen metadata med parametern - tagg
- Sök-kommandot kan du filtrera på databas-specifika sökspråk med parametern - Filter.
- Sök-kommandot kan du filtrera på moduler från alla eller fåtal registrerade databaser.

## <a name="cmdlet-syntax"></a>Cmdlet-syntax
```powershell
Get-Command -Name Find-Command -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Cmdlet-referens för onlinehjälp

[Kommandot Sök](http://go.microsoft.com/fwlink/?LinkId=733636)

## <a name="example-commands"></a>Exempel på kommandon
```powershell

# Find a specific command
Find-Command -Name Get-ScriptAnalyzerRule

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Get-ScriptAnalyzerRule              1.5.0      PSScriptAnalyzer                    PSGallery

# Find multiple commands
Find-Command -Name Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

# Find all available commands from all registered repositories
Find-Command

# Find available commands from few registered repositories
Find-Command -Repository PSGallery,PrivatePSGallery

# Find all commands in a specified repository
Find-Command -Repository PSGallery

# Find a command defined in a specific module
Find-Command -Name Get-ScriptAnalyzerRule -Module PSScriptAnalyzer

# Find commands from all versions of a module
Find-Command -ModuleName PSReadline -AllVersions

# Find commands with module name and MinimumVersion.
Find-Command -ModuleName PSReadline -MinimumVersion 1.1

# Find commands with module name and exact version
Find-Command -ModuleName AzureRM -RequiredVersion 1.4.0

# Find commands defined modules with -Filter based search. -Filter searches in description and module names
Find-Command -Filter Cookbook
Find-Command -Filter RBAC

# Find all commands with tags Azure or DSC in module metadata
Find-Command -Tag Azure, DSC

```