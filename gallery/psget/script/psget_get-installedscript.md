---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: galleriet, powershell, cmdlet, psget
title: Get-InstalledScript
ms.openlocfilehash: f35e57cdadd1448bd9032ab007d692003c4cf4a2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="get-installedscript"></a>Get-InstalledScript

Hämtar installerade skript på en dator.

## <a name="description"></a>Beskrivning

Get-InstalledScript cmdlet hämtar installerade PowerShell-skript på en dator.

För varje installerade skript returnerar Get-InstalledScript ett PSRepositoryItemInfo-objekt som eventuellt kan skickas till avinstallera-skript för att avinstallera de installerade skript.

- Get-InstalledScript kan filtrera installerade skript baserat på namn, versionsparametrar.
- Get-InstalledScript kan filtrera med parametrarna: MinimumVersion, MaximumVersion, RequiredVersion, allaversioner.
  - Dessa parametrar är ömsesidigt uteslutande, utom MinmimumVersion och MaximumVersion.
  - De här parametrarna tillåts endast med enda Skriptnamn utan någon jokertecken.
  - Om parametern RequiredVersion inte anges returnerar Get-InstalledScript den senaste versionen av den installerade skript som är lika med eller större än den angivna lägsta versionen eller den senaste versionen av skriptet om ingen minsta version anges. 
  - Om parametern RequiredVersion har angetts returnerar Get-InstalledScript endast versionen av installerade skript som exakt matchar den angivna versionen.

## <a name="cmdlet-syntax"></a>Cmdlet-syntax

```powershell
Get-Command -Name Get-InstalledScript -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Cmdlet-referens för onlinehjälp

[Get-InstalledScript](http://go.microsoft.com/fwlink/?LinkId=619790)

## <a name="example-commands"></a>Exempel på kommandon

```powershell

# Get all scripts installed using PowerShellGet cmdlets
Get-InstalledScript

# Get a specific installed script
Get-InstalledScript Show-Tree

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
1.0.0      Show-Tree                           PSGallery            Script to show the layout of PowerShell namespaces (Tr...

# Get installed script with wildcards
Get-InstalledScript -Name *Azure*

# Get all versions of an installed script
Get-InstalledScript -Name Connect-O365 -AllVersions

# Get installed script with MinimumVersion
Get-InstalledScript -Name Connect-O365 -MinimumVersion 1.1

# Get installed script with MaximumVersion
Get-InstalledScript -Name Connect-O365 -MaximumVersion 1.6.3

# Get installed script with version range
Get-InstalledScript -Name Connect-O365 -MinimumVersion 1.1 -MaximumVersion 1.6.3

# Get installed script with RequiredVersion
Get-InstalledScript -Name Connect-O365 -RequiredVersion 1.4

# Properties of Get-InstalledScript returned object
Get-InstalledScript Show-Tree | Format-List * -Force

Name                       : Show-Tree
Version                    : 1.0.0
Type                       : Script
Description                : Script to show the layout of PowerShell namespaces (Trees) using ASCII
Author                     : Jeffrey Snover
CompanyName                : jsnover
Copyright                  : (C) Microsoft Corporation. All rights reserved.
PublishedDate              : 2/15/2016 10:15:35 PM
InstalledDate              : 5/4/2016 11:44:13 PM
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
AdditionalMetadata         : {description, installeddate, tags, PackageManagementProvider...}
InstalledLocation          : C:\Program Files\WindowsPowerShell\Scripts


```

