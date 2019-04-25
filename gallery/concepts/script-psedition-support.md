---
ms.date: 06/12/2017
contributor: manikb
keywords: galleriet, powershell, cmdlet, psget
title: Skriptet med kompatibla PowerShell-utgåvor
ms.openlocfilehash: e364879f611429a8583e550fb7704431e456fbb1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084699"
---
# <a name="script-with-compatible-powershell-editions"></a><span data-ttu-id="856cc-103">Skriptet med kompatibla PowerShell-utgåvor</span><span class="sxs-lookup"><span data-stu-id="856cc-103">Script with compatible PowerShell editions</span></span>

<span data-ttu-id="856cc-104">Från och med version 5.1 finns PowerShell i olika utgåvor som anger olika funktionsuppsättningar och plattformskompatibilitet.</span><span class="sxs-lookup"><span data-stu-id="856cc-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="856cc-105">**Desktop Edition:** Bygger på .NET Framework och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på fullständiga utgåvor av Windows, till exempel Server Core och Windows-skrivbordet.</span><span class="sxs-lookup"><span data-stu-id="856cc-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>

- <span data-ttu-id="856cc-106">**Core Edition:** Bygger på .NET Core och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på begränsade utgåvor av Windows som Nano Server och Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="856cc-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

<span data-ttu-id="856cc-107">Vilken utgåva av PowerShell som körs visas i PSEdition-egenskapen i $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="856cc-107">The running edition of PowerShell is shown in the PSEdition property of $PSVersionTable.</span></span>

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

<span data-ttu-id="856cc-108">Skriptskribenter kan förhindra att ett skript körs om den körs på en kompatibel version av PowerShell med hjälp av parametern PSEdition på ett `#requires` instruktionen.</span><span class="sxs-lookup"><span data-stu-id="856cc-108">Script authors can prevent a script from executing unless it is run on a compatible edition of PowerShell using the PSEdition parameter on a `#requires` statement.</span></span>

```powershell
Set-Content C:\script.ps1 -Value "#requires -PSEdition Core
Get-Process -Name PowerShell"
Get-Content C:\script.ps1
#requires -PSEdition Core
Get-Process -Name PowerShell

C:\script.ps1
C:\script.ps1 : The script 'script.ps1' cannot be run because it contained a "#requires" statement for PowerShell editions 'Core'. The edition of PowerShell that is required by the script does not match the currently running PowerShell Desktop edition.
At line:1 char:1
+ C:\script.ps1
+ ~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (script.ps1:String) [], RuntimeException
    + FullyQualifiedErrorId : ScriptRequiresUnmatchedPSEdition
```

<span data-ttu-id="856cc-109">PowerShell-galleriet användare kan hitta listan stöds på en viss version av PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="856cc-109">PowerShell Gallery users can find the list of scripts supported on a specific PowerShell Edition.</span></span>
<span data-ttu-id="856cc-110">Skript utan PSEdition_Desktop och PSEdition_Core taggar anses fungera på PowerShell Desktop edition.</span><span class="sxs-lookup"><span data-stu-id="856cc-110">Scripts without PSEdition_Desktop and PSEdition_Core tags are considered to work fine on PowerShell Desktop edition.</span></span>

```powershell
# Find scripts supported on PowerShell Desktop edition
Find-Script -Tag PSEdition_Desktop

# Find scripts supported on PowerShell Core edition
Find-Script -Tag PSEdition_Core
```

## <a name="more-details"></a><span data-ttu-id="856cc-111">Mer information</span><span class="sxs-lookup"><span data-stu-id="856cc-111">More details</span></span>

- [<span data-ttu-id="856cc-112">Moduler med PSEditions</span><span class="sxs-lookup"><span data-stu-id="856cc-112">Modules with PSEditions</span></span>](module-psedition-support.md)
- [<span data-ttu-id="856cc-113">Stöd för PSEditions på PowerShellGallery</span><span class="sxs-lookup"><span data-stu-id="856cc-113">PSEditions support on PowerShellGallery</span></span>](../how-to/finding-packages/searching-by-compatibility.md)
