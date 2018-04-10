---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: galleriet, powershell, cmdlet, psget
title: Find-Script
ms.openlocfilehash: 1f5076d94015c0b1041591144f1f0fe36819204b
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="find-script"></a>Find-Script

Söker efter PowerShell-skriptfilerna från en online-galleriet som uppfyller angivna villkor.

## <a name="description"></a>Beskrivning

Hitta skriptet identifierar skriptfiler från registrerade databaser som matchar de angivna kriterierna.
För varje skript hitta returnerar hitta skript ett PSRepositoryItemInfo-objekt som eventuellt kan skickas till installationsskriptet för att installera skripten.
Hitta skript-cmdleten låter dig för att identifiera skriptfiler med andra sökvillkor som namn, tagg, filter, namn, version omfång, exakt vilken version, alla versioner, inklusive dess beroenden och från vissa eller alla registrerade databaser.

- Sök-skript kan filter baserat på skriptet innehåll med kommandot - och - innehåller parametrar.
- Sök-skript kan filtrera med parametrarna: MinimumVersion, MaximumVersion, RequiredVersion, allaversioner.
  - Dessa parametrar är ömsesidigt uteslutande, utom MinmimumVersion och MaximumVersion.
  - De här parametrarna tillåts endast med enda Skriptnamn utan någon jokertecken.
  - Om parametern RequiredVersion anges returnerar Sök-skriptet den senaste versionen av det skript som är lika med eller större än den angivna lägsta versionen eller den senaste versionen av skriptet om ingen minsta version anges.
  - Om parametern RequiredVersion har angetts returnerar hitta skript endast version av skript som exakt matchar den angivna versionen.
- Sök-skript kan filtrera på skriptmetadata med parametern - taggen.
- Sök-skript kan filtrera på databas-specifika sökspråk med parametern - Filter.
- Sök-skript kan filtrera efter skript från alla eller fåtal registrerade databaser.

**Obs:** registrerade PSRepository måste ha en giltig ScriptSourceLocation. Du kan använda Set-PSRepository för att ange ScriptSourceLocation värde.

## <a name="cmdlet-syntax"></a>Cmdlet-syntax

```powershell
Get-Command -Name Find-Script -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Cmdlet-referens för onlinehjälp

[Sök-skript](http://go.microsoft.com/fwlink/?LinkId=619785)

## <a name="example-commands"></a>Exempel på kommandon

```powershell
# Find a script from the registered repository with ScriptSourceLocation
Find-Script Connect-AzureVM

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0        Connect-AzureVM                     PSGallery            This runbook sets up a connection to an Azure vi...

# Find multiple scripts
Find-Script -Name Connect-AzureVM, Show-Tree, Connect-O365

# Find scripts with wildcards in -Name
Find-Script -Name *Azure*

# Find all versions of a script
Find-Script -Name Connect-O365 -AllVersions

# Find a script with -MinimumVersion.
# With MinimumVersion we can find a script whose version is greate than or equal to the specified MinimumVersion value.
Find-Script Connect-O365 -MinimumVersion 1.4

# Find a script with MaximumVersion
Find-Script -Name Connect-O365 -MaximumVersion 1.6.2

# Find a script with both MinimumVersion and MaximumVersion range.
Find-Script -Name Connect-O365 -MinimumVersion 1.1 -MaximumVersion 1.6.2

# Find a script with exact version
Find-Script -Name Connect-O365 -RequiredVersion 1.5.7

# Find a script with a specific pre-release version
Find-Script -Name Connect-O365 -RequiredVersion 1.3.2-alpha -AllowPrerelease

# Find a script from the specified repository
Find-Script -Name Fabrikam-ServerScript -Repository MyLocalRepo

# Find available scripts from all registered repositories
Find-Script

# Find available scripts from few registered repositories
Find-Script -Repository PSGallery, PrivatePSGallery

# Find a script along with its dependent modules and scripts
Find-Script -Name Connect-AzureVM -IncludeDependencies

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0        Connect-AzureVM                     PSGallery            This runbook sets up a connection to an Azure vi...
1.4.0      Azure                               PSGallery            Microsoft Azure PowerShell - Service Management
1.1.2      Azure.Storage                       PSGallery            Microsoft Azure PowerShell - Storage service cmd...
1.0.8      AzureRM.profile                     PSGallery            Microsoft Azure PowerShell - Profile credential ...

# Find all scripts with workflows
Find-Script -Includes Workflow

# Find all scripts with functions
Find-Script -Includes Function

# Find scripts with specific commands
Find-Script -Command Log-Message
Find-Script -Command Log-Message, Show-Tree -Includes Function
Find-Script -Command Connect-AzureVM -Includes Workflow

# Find scripts with -Filter based search. -Filter searches in description and names
Find-Script -Filter Windows
Find-Script -Filter Azure

# Find all scripts with tags O365 or Nano
Find-Script -Tag O365, Nano

# Properties of Find-Script returned object
Find-Script Show-Tree | Format-List * -Force
Name                       : Show-Tree
Version                    : 1.0.0
Type                       : Script
Description                : Script to show the layout of PowerShell namespaces (Trees) using ASCII
Author                     : Jeffrey Snover
CompanyName                : jsnover
Copyright                  : (C) Microsoft Corporation. All rights reserved.
PublishedDate              : 2/15/2016 10:15:35 PM
InstalledDate              :
UpdatedDate                :
LicenseUri                 :
ProjectUri                 :
IconUri                    :
Tags                       : {Nano, PSScript}
Includes                   : {Function, RoleCapability, Command, DscResource...}
PowerShellGetFormatVersion :
ReleaseNotes               :
Dependencies               : {}
RepositorySourceLocation   : https://www.powershellgallery.com/api/v2/
Repository                 : PSGallery
PackageManagementProvider  : NuGet
AdditionalMetadata         : {versionDownloadCount, ItemType, copyright, PackageManagementProvider...}


# Includes property on PSRepositoryItemInfo object
$t = Find-Script -Includes Workflow -Repository INT -Name Fabrikam-ClientScript
$t.Includes

Name                           Value
----                           -----
Function                       {Test-FunctionFromScript_Fabrikam-ClientScript}
RoleCapability                 {}
Command                        {Test-FunctionFromScript_Fabrikam-ClientScript, Test-WorkflowFromScript_Fabrikam-Clie...
DscResource                    {}
Workflow                       {Test-WorkflowFromScript_Fabrikam-ClientScript}
Cmdlet                         {}


```