---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 0a481fb9d4f2aab89bc448c71b01f1d541cf24bc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085090"
---
# <a name="side-by-side-version-support-on-powershell-50-or-newer"></a><span data-ttu-id="c4dda-102">Versionsstöd sida vid sida i PowerShell 5.0 eller senare</span><span class="sxs-lookup"><span data-stu-id="c4dda-102">Side-by-Side Version Support on PowerShell 5.0 or newer</span></span>

<span data-ttu-id="c4dda-103">Det finns nu sida-vid-sida (SxS)-modul Versionsstöd i Install-Module, Update-modulen och Publish-Module-cmdletar som körs i Windows PowerShell 5.0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="c4dda-103">There is now side-by-side (SxS) module version support in Install-Module, Update-Module, and Publish-Module cmdlets that run in Windows PowerShell 5.0 or newer.</span></span>
<span data-ttu-id="c4dda-104">Dessutom har vi lagt till en - RequiredVersion-parameter till Publish-Module-cmdlet för att ange vilken version som ska publiceras.</span><span class="sxs-lookup"><span data-stu-id="c4dda-104">Also, we have added a -RequiredVersion parameter to the Publish-Module cmdlet to specify the version to be published.</span></span> <span data-ttu-id="c4dda-105">Parametern Path har nu stöd för modulen rotsökväg med version-mapp.</span><span class="sxs-lookup"><span data-stu-id="c4dda-105">The Path parameter now supports the module base path with the version folder.</span></span>

<span data-ttu-id="c4dda-106">**Install-Module-exempel:**</span><span class="sxs-lookup"><span data-stu-id="c4dda-106">**Install-Module examples:**</span></span>
```powershell
Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.0 -Repository PSGallery
Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name : PSScriptAnalyzer
Version : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

Install-Module -Name PSScriptAnalyzer -RequiredVersion 1.1.1 -Repository PSGallery
Get-Module -ListAvailable -Name PSScriptAnalyzer | Format-List Name,Version,ModuleBase

Name       : PSScriptAnalyzer
Version    : 1.1.1
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.1
Name       : PSScriptAnalyzer
Version    : 1.1.0
ModuleBase : C:\Program Files\WindowsPowerShell\Modules\PSScriptAnalyzer\1.1.0

Get-InstalledModule -Name PSScriptAnalyzer -AllVersions

Version    Name                                Type       Repository           Description
-------    ----                                ----       ----------           -----------
1.1.0      PSScriptAnalyzer                    Module     PSGallery            PSScriptAnalyzer provides script analysis...
1.1.1      PSScriptAnalyzer                    Module     PSGallery            PSScriptAnalyzer provides script analysis...
```
