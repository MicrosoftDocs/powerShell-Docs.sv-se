---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: a0b1573611c5d4232082c19ca19b4cca79d0699e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685258"
---
# <a name="powershell-module-discovery-install-and-inventory-with-powershellget"></a>PowerShell-Modulidentifiering, installera och inventering med PowerShellGet

PowerShellGet ingår i den här versionen av WMF:
-   Find-Module kan filtrera på modulen metadata med parametern - tagg
-   Find-Module kan filtrera på lagringsplatsen sökningar språk med parametern - Filter
-   Find-Module kan filter baserat på modulen innehåll med - kommando, - DscResource, och - innehåller parametrar
-   Sök-DscResource tillåter identifiering av enskilda DSC-resurser i databaser
-   Stöd för att installera från och publicering till filresurser med NuGet

## <a name="example-commands"></a>Exempel på kommandon
```powershell
\# Find all modules with tags Azure or DSC
Find-Module -Tag Azure, DSC

\# Find modules with a specific DscResource
Find-Module -DscResource xFirewall

\#Find modules with specific commands
Find-Module -Command Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer

\# Find all modules with Dsc resources
Find-Module -Includes DscResource

\# Find all modules with cmdlets
Find-Module -Includes Cmdlet

\# Find all modules with functions
Find-Module -Includes Function

\# Find all DSC resources
Find-DscResource

\# Find all DSC resources contained within a specific module
Find-DscResource -ModuleName xNetworking

\# Find all DSC resources in modules with DSCResourceKit or DesiredStateConfiguration
Find-DscResource -Tag DesiredStateConfiguration, DSCResourceKit

\# Find modules using -Filter parameter
\# Specified filter value is searched in Name and Description properties
Find-Module -Filter Cookbook -Repository PSGallery
Find-Module -Filter RBAC -Repository PSGallery
```

## <a name="new-features-in-powershellget"></a>Nya funktioner i PowerShellGet
-   Stöd för sida-vid-sida-version på Windows PowerShell 5.0 eller senare
-   Stöd för policymodul beroende installation
-   Tre nya cmdletar
    -   Get-InstalledModule
    -   Uninstall-Module
    -   Save-Module
