---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: galleriet, powershell, cmdlet, psget
title: Skriptet med kompatibla versioner av PowerShell
ms.openlocfilehash: 3cb82fe56e17d0bc41d75f6db69fa7b3b0fdf3f6
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.contentlocale: sv-SE
ms.lasthandoff: 05/10/2018
---
# <a name="script-with-compatible-powershell-editions"></a><span data-ttu-id="e95fb-103">Skriptet med kompatibla versioner av PowerShell</span><span class="sxs-lookup"><span data-stu-id="e95fb-103">Script with compatible PowerShell editions</span></span>

<span data-ttu-id="e95fb-104">Från och med version 5.1 finns PowerShell i olika utgåvor som anger olika funktionsuppsättningar och plattformskompatibilitet.</span><span class="sxs-lookup"><span data-stu-id="e95fb-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="e95fb-105">**Desktop Edition:** bygger på .NET Framework och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på fullständiga utgåvor av Windows, till exempel Server Core och Windows Desktop.</span><span class="sxs-lookup"><span data-stu-id="e95fb-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="e95fb-106">**Core Edition:** bygger på .NET Core och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på begränsade utgåvor av Windows som Nano Server och Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="e95fb-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="e95fb-107">Vilken utgåva av PowerShell som körs visas i PSEdition-egenskapen i $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="e95fb-107">The running edition of PowerShell is shown in the PSEdition property of $PSVersionTable.</span></span>

```powershell
$PSVersionTable

Name                           Value
----                           -----
PSVersion                      5.1.14300.1000
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
CLRVersion                     4.0.30319.42000
BuildVersion                   10.0.14300.1000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

<span data-ttu-id="e95fb-108">Skriptskribenter kan förhindra att ett skript körs om det inte körs på en kompatibel version av PowerShell med hjälp av parametern PSEdition på ett #requires-uttryck.</span><span class="sxs-lookup"><span data-stu-id="e95fb-108">Script authors can prevent a script from executing unless it is run on a compatible edition of PowerShell using the PSEdition parameter on a #requires statement.</span></span>

```powershell
Set-Content C:\script.ps1 -Value "#requires -PSEdition Core
Get-Process -Name PowerShell"
Get-Content C:\script.ps1
#requires -PSEdition Core
Get-Process -Name PowerShell

C:\script.ps1
C:\script.ps1 : The script 'script.ps1' cannot be run because it contained a "#requires" statement for PowerShell Core edition. The edition of PowerShell that is required by the script does not match the currently running PowerShell Desktop edition.
At line:1 char:1
+ C:\script.ps1
+ ~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (script.ps1:String) [], RuntimeException
    + FullyQualifiedErrorId : ScriptRequiresUnmatchedPSEdition
```

<span data-ttu-id="e95fb-109">PowerShell-galleriet användare kan hitta listan stöds på en viss version av PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="e95fb-109">PowerShell Gallery users can find the list of scripts supported on a specific PowerShell Edition.</span></span>
<span data-ttu-id="e95fb-110">Skript utan PSEdition_Desktop och PSEditon_Core anses fungerar på PowerShell Desktop-versioner.</span><span class="sxs-lookup"><span data-stu-id="e95fb-110">Scripts without PSEdition_Desktop and PSEditon_Core are considered to work fine on PowerShell Desktop editions.</span></span>

```powershell

# Find scripts supported on PowerShell Desktop edition
Find-Script -Tag PSEditon_Desktop

# Find scripts supported on PowerShell Core editions
Find-Script -Tag PSEditon_Core

```

## <a name="more-details"></a><span data-ttu-id="e95fb-111">Mer information</span><span class="sxs-lookup"><span data-stu-id="e95fb-111">More details</span></span>

- [<span data-ttu-id="e95fb-112">Moduler med PSEditions</span><span class="sxs-lookup"><span data-stu-id="e95fb-112">Modules with PSEditions</span></span>](module-psedition-support.md)
- [<span data-ttu-id="e95fb-113">Stöd för PSEditions på PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="e95fb-113">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-items/searching-by-psedition.md)