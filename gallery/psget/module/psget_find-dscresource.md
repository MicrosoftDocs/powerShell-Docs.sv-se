---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: galleriet, powershell, cmdlet, psget
title: Find-DscResource
ms.openlocfilehash: 6c5713f122d48e9c9d5e0aa45dc14047afc56102
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/15/2018
---
# <a name="find-dscresource"></a>Find-DscResource

Söker efter DSC-resurser i moduler.

## <a name="description"></a>Beskrivning

Hitta DscResource cmdleten hittar [önskade tillstånd Configuration (DSC)](https://msdn.microsoft.com/PowerShell/dsc/overview) resurser som ingår i moduler som matchar de angivna villkoren från registrerade databaser.
För varje modul som söker efter denna cmdlet returnerar hitta DscResource ett PSGetDscResourceInfo-objekt som du kan skicka vidare till Install-modulen för att installera modulerna som innehåller de resurser som denna cmdlet returnerar.

DSC är en ny plattform i Windows PowerShell som gör att distribuera och hantera konfigurationsdata för programtjänster och hantera miljön där tjänsterna körs.

Önskade tillstånd Configuration (DSC) resurser innehåller byggblock för DSC-konfigurationen. En resurs Exponerar egenskaper som kan vara konfigurerade (schema) och innehåller funktioner för PowerShell-skript som den lokala Configuration Manager (MGM) anrop till ”gör den det”.

En resurs kan modellen något som generiska som en fil eller så specifik som en inställning för IIS-servern. Grupper av som resurser kombineras till en DSC-modul som ordnar alla filer som krävs i en struktur som har en bärbar och som innehåller metadata för att identifiera hur resurserna som är avsedd att användas i.

- Hitta DscResource kan filtrera med parametrarna: MinimumVersion, RequiredVersion, allaversioner.
  - Dessa parametrar kan inte anges samtidigt.
  - De här parametrarna tillåts endast med enda modulnamnet utan några jokertecken.
  - Om parametern RequiredVersion inte anges returnerar hitta DscResource den senaste versionen av den modul som är lika med eller större än den angivna lägsta versionen eller den senaste versionen av modulen om ingen minsta version anges.
  - Om parametern RequiredVersion har angetts returnerar hitta DscResource endast versionen av den modul som exakt matchar den angivna versionen.
- Hitta DscResource kan filtrera efter modulens med parametern - tagg
- Hitta DscResource kan filtrera på databas-specifika sökspråk med parametern - Filter.
- Hitta DscResource kan filtrera efter moduler från alla eller fåtal registrerade databaser.

## <a name="cmdlet-syntax"></a>Cmdlet-syntax
```powershell
Get-Command -Name Find-DscResource -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Cmdlet-referens för onlinehjälp

[Hitta DscResource](http://go.microsoft.com/fwlink/?LinkId=517196)

## <a name="example-commands"></a>Exempel på kommandon
```powershell

# Find a specific DSC Resource
Find-DscResource -Name xIisFeatureDelegation

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
xIisFeatureDelegation               1.10.0.0   xWebAdministration                  PSGallery

# Find all available DSC Resources from all registered repositories
Find-DscResource

# Find a DSC resource by name
Find-DscResource -Name xWebsite

# Find multiple DSC Resources
Find-DscResource -Name xIisHandler, xFirewall

# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking
Find-DscResource -ModuleName xWebAdministration

# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

# Find available DSC Resources from few registered repositories
Find-DscResource -Repository PSGallery,PrivatePSGallery

# Find all DSC Resources in a specified repository
Find-DscResource -Repository PSGallery

# Find DSC Resources from all versions of a module
Find-DscResource -ModuleName xNetworking -AllVersions

# Find DSC Resources with module name and MinimumVersion.
Find-DscResource -ModuleName xNetworking -MinimumVersion 1.1

# Find DSC Resources with module name and exact version
Find-DscResource -ModuleName xNetworking -RequiredVersion 2.1.1

# Find DSC Resources defined modules with -Filter based search. -Filter searches in description and module names
Find-DscResource -Filter Domain

# Find all DSC Resources with tags Azure or DSC in module metadata
Find-DscResource -Tag Azure, DSC

```

