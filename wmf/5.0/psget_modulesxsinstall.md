---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
ms.openlocfilehash: f9a121c320ffb780503dbe0c278f698a6fa40289
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="side-by-side-version-support-on-powershell-50-or-newer"></a><span data-ttu-id="426f0-102">Stöd för sida-vid-sida-Version på PowerShell 5.0 eller senare</span><span class="sxs-lookup"><span data-stu-id="426f0-102">Side-by-Side Version Support on PowerShell 5.0 or newer</span></span>

<span data-ttu-id="426f0-103">Stöds nu sida-vid-sida (SxS) modulen version i installera modulen Update-modulen och publicera modul-cmdlet: ar som körs i Windows PowerShell 5.0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="426f0-103">There is now side-by-side (SxS) module version support in Install-Module, Update-Module, and Publish-Module cmdlets that run in Windows PowerShell 5.0 or newer.</span></span>
<span data-ttu-id="426f0-104">Vi har även lagt till parameter - RequiredVersion cmdlet Publish-Module anger versionen publiceras.</span><span class="sxs-lookup"><span data-stu-id="426f0-104">Also, we have added a -RequiredVersion parameter to the Publish-Module cmdlet to specify the version to be published.</span></span> <span data-ttu-id="426f0-105">Parametern Path stöder nu modulen bassökväg med version-mapp.</span><span class="sxs-lookup"><span data-stu-id="426f0-105">The Path parameter now supports the module base path with the version folder.</span></span>

<span data-ttu-id="426f0-106">**Installera modulen exempel:**</span><span class="sxs-lookup"><span data-stu-id="426f0-106">**Install-Module examples:**</span></span>
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