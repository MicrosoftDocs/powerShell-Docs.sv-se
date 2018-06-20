---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 9efc640dfda7e08e59d2c56746facd9658b1f9de
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222181"
---
# <a name="powershell-module-discovery-install-and-inventory-with-powershellget"></a>Identifiering av PowerShell-modulen, installera och inventera med PowerShellGet

PowerShellGet ingår i den här versionen av WMF:
-   Hitta modulen kan filtrera efter modulens med parametern - tagg
-   Hitta modulen kan filtrera på databas-specifika sökspråk med parametern - Filter
-   Hitta modulen kan filter baserat på modulen innehåll med kommandot-, - DscResource, och - innehåller parametrar
-   Hitta DscResource tillåter identifiering av enskilda DSC-resurser i databaser
-   Stöd för installation från och publicering till filresurser med NuGet

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
-   Stöd för modulen beroende installation
-   Tre nya cmdlet: ar
    -   Get-InstalledModule
    -   Avinstallera modul
    -   Spara-modul
