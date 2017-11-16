---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: galleriet, powershell, cmdlet, psget
title: Hitta RoleCapability
ms.openlocfilehash: 77c5b492d9681fa05315401fba410c508af1d13b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="find-rolecapability"></a>Hitta RoleCapability

Söker efter roll funktioner i moduler.

## <a name="description"></a>Beskrivning
Hitta RoleCapability cmdleten hittar PowerShell rollen funktioner i moduler. Hitta RoleCapability söker moduler i registrerade databaser. För varje roll-funktion som söker efter denna cmdlet returnerar den ett PSGetRoleCapabilityInfo-objekt. Du kan överföra ett PSGetRoleCapabilityInfo-objekt till cmdleten Install-Module så här installerar du den modul som innehåller den roll kapaciteten.
PowerShell rollen funktioner definierar vilka kommandon, program och så vidare är tillgängliga för en användare i en precis tillräckligt Administration JEA ()-slutpunkten. Rollen funktioner definieras av filer med filnamnstillägget .psrc.

- Hitta RoleCapability kan filtrera med parametrarna: MinimumVersion, RequiredVersion, allaversioner.
  - Dessa parametrar kan inte anges samtidigt.
  - De här parametrarna tillåts endast med enda modulnamnet utan några jokertecken.
  - Om parametern RequiredVersion inte anges returnerar hitta RoleCapability den senaste versionen av den modul som är lika med eller större än den angivna lägsta versionen eller den senaste versionen av modulen om ingen minsta version anges.
  - Om parametern RequiredVersion har angetts returnerar hitta RoleCapability endast versionen av den modul som exakt matchar den angivna versionen.
- Hitta RoleCapability kan filtrera efter modulens med parametern - tagg
- Hitta RoleCapability kan filtrera på databas-specifika sökspråk med parametern - Filter.
- Hitta RoleCapability kan filtrera efter moduler från alla eller fåtal registrerade databaser.

## <a name="cmdlet-syntax"></a>Cmdlet-syntax
```powershell
Get-Command -Name Find-RoleCapability -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a>Cmdlet-referens för onlinehjälp

[Hitta RoleCapability](http://go.microsoft.com/fwlink/?LinkId=718029)

## <a name="example-commands"></a>Exempel på kommandon
```powershell

# Find a specific role capability
Find-RoleCapability -Name Maintenance

Name                                Version    ModuleName                          Repository
----                                -------    ----------                          ----------
Maintenance                         1.5.0      RoleCapModule                       PrivatePSGallery

# Find multiple role capabilities
Find-RoleCapability -Name MyJeaRole, Maintenance

# Find all available role capabilities from all registered repositories
Find-RoleCapability

# Find available role capabilities from few registered repositories
Find-RoleCapability -Repository PSGallery,PrivatePSGallery

# Find all role capabilities in a specified repository
Find-RoleCapability -Repository PSGallery

# Find a role capability defined in a specific module
Find-RoleCapability -Name Maintenance -ModuleName RoleCapModule

# Find role capabilities from all versions of a module
Find-RoleCapability -ModuleName RoleCapModule -AllVersions

# Find role capabilities with module name and MinimumVersion.
Find-RoleCapability -ModuleName RoleCapModule -MinimumVersion 1.1

# Find role capabilities with module name and exact version
Find-RoleCapability -ModuleName RoleCapModule -RequiredVersion 1.4.0

# Find role capabilities defined modules with -Filter based search. -Filter searches in description and module names
Find-RoleCapability -Filter Cookbook
Find-RoleCapability -Filter RBAC

# Find all role capabilities with tags Azure or DSC in module metadata
Find-RoleCapability -Tag Azure, DSC

```

