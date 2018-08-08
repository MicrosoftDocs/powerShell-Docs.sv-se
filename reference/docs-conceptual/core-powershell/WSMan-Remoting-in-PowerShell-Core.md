---
title: WS-Management-fjärrkommunikation (WSMan) i PowerShell Core
description: Fjärrkommunikation i PowerShell Core med WSMan
ms.date: 08/06/2018
ms.openlocfilehash: ce58ed88f59f32b0f83951e55de36e829f7fa3f4
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587354"
---
# <a name="ws-management-wsman-remoting-in-powershell-core"></a><span data-ttu-id="8750c-103">WS-Management-fjärrkommunikation (WSMan) i PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="8750c-103">WS-Management (WSMan) Remoting in PowerShell Core</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="8750c-104">Instruktioner för att skapa en slutpunkt för fjärrkommunikation</span><span class="sxs-lookup"><span data-stu-id="8750c-104">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="8750c-105">PowerShell Core-paket för Windows innehåller ett plugin-programmet WinRM (`pwrshplugin.dll`) och ett installationsskript (`Install-PowerShellRemoting.ps1`) i `$PSHome`.</span><span class="sxs-lookup"><span data-stu-id="8750c-105">The PowerShell Core package for Windows includes a WinRM plug-in (`pwrshplugin.dll`) and an installation script (`Install-PowerShellRemoting.ps1`) in `$PSHome`.</span></span>
<span data-ttu-id="8750c-106">De här filerna aktivera PowerShell för att acceptera inkommande fjärranslutningar i PowerShell när dess slutpunkt har angetts.</span><span class="sxs-lookup"><span data-stu-id="8750c-106">These files enable PowerShell to accept incoming PowerShell remote connections when its endpoint is specified.</span></span>

### <a name="motivation"></a><span data-ttu-id="8750c-107">Motivation</span><span class="sxs-lookup"><span data-stu-id="8750c-107">Motivation</span></span>

<span data-ttu-id="8750c-108">En installation av PowerShell kan upprätta PowerShell-sessioner till fjärrdatorer med hjälp av `New-PSSession` och `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="8750c-108">An installation of PowerShell can establish PowerShell sessions to remote computers using `New-PSSession` and `Enter-PSSession`.</span></span>
<span data-ttu-id="8750c-109">Användaren måste skapa en slutpunkt för WinRM-fjärrkommunikation för att aktivera den för att acceptera inkommande fjärranslutningar med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8750c-109">To enable it to accept incoming PowerShell remote connections, the user must create a WinRM remoting endpoint.</span></span>
<span data-ttu-id="8750c-110">Detta är en explicit opt i scenariot där användaren kör Install-PowerShellRemoting.ps1 skapa WinRM-slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="8750c-110">This is an explicit opt-in scenario where the user runs Install-PowerShellRemoting.ps1 to create the WinRM endpoint.</span></span>
<span data-ttu-id="8750c-111">Installationsskriptet är en kortsiktig lösning tills vi lägger till ytterligare funktioner `Enable-PSRemoting` att utföra samma åtgärd.</span><span class="sxs-lookup"><span data-stu-id="8750c-111">The installation script is a short-term solution until we add additional functionality to `Enable-PSRemoting` to perform the same action.</span></span>
<span data-ttu-id="8750c-112">Mer information finns på problemet [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span><span class="sxs-lookup"><span data-stu-id="8750c-112">For more details, please see issue [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span></span>

### <a name="script-actions"></a><span data-ttu-id="8750c-113">Skriptåtgärder</span><span class="sxs-lookup"><span data-stu-id="8750c-113">Script Actions</span></span>

<span data-ttu-id="8750c-114">Skriptet</span><span class="sxs-lookup"><span data-stu-id="8750c-114">The script</span></span>

1. <span data-ttu-id="8750c-115">Skapar en katalog för plugin-programmet i %windir%\System32\PowerShell</span><span class="sxs-lookup"><span data-stu-id="8750c-115">Creates a directory for the plug-in within %windir%\System32\PowerShell</span></span>
1. <span data-ttu-id="8750c-116">Kopierar pwrshplugin.dll dit</span><span class="sxs-lookup"><span data-stu-id="8750c-116">Copies pwrshplugin.dll to that location</span></span>
1. <span data-ttu-id="8750c-117">Genererar en konfigurationsfil</span><span class="sxs-lookup"><span data-stu-id="8750c-117">Generates a configuration file</span></span>
1. <span data-ttu-id="8750c-118">Registrerar som plugin-programmet med WinRM</span><span class="sxs-lookup"><span data-stu-id="8750c-118">Registers that plug-in with WinRM</span></span>

### <a name="registration"></a><span data-ttu-id="8750c-119">Registrering</span><span class="sxs-lookup"><span data-stu-id="8750c-119">Registration</span></span>

<span data-ttu-id="8750c-120">Skriptet måste köras i en behörighet på PowerShell-session och körs i två lägen.</span><span class="sxs-lookup"><span data-stu-id="8750c-120">The script must be executed within an Administrator-level PowerShell session and runs in two modes.</span></span>

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a><span data-ttu-id="8750c-121">Körs av instansen av PowerShell som den registreras</span><span class="sxs-lookup"><span data-stu-id="8750c-121">Executed by the instance of PowerShell that it will register</span></span>

```powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a><span data-ttu-id="8750c-122">Körs av en annan instans av PowerShell för den instans som den registreras</span><span class="sxs-lookup"><span data-stu-id="8750c-122">Executed by another instance of PowerShell on behalf of the instance that it will register</span></span>

```powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

<span data-ttu-id="8750c-123">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="8750c-123">For Example:</span></span>

```powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

<span data-ttu-id="8750c-124">**Obs:** fjärrkommunikation registrering skriptet startar om WinRM, så att alla befintliga PSRP sessioner avslutas omedelbart när skriptet har körts.</span><span class="sxs-lookup"><span data-stu-id="8750c-124">**NOTE:** The remoting registration script will restart WinRM, so all existing PSRP sessions will terminate immediately after the script is run.</span></span> <span data-ttu-id="8750c-125">Om under en fjärrsession, kommer detta avslutar anslutningen.</span><span class="sxs-lookup"><span data-stu-id="8750c-125">If run during a remote session, this will terminate the connection.</span></span>

## <a name="how-to-connect-to-the-new-endpoint"></a><span data-ttu-id="8750c-126">Hur du ansluter till den nya slutpunkten</span><span class="sxs-lookup"><span data-stu-id="8750c-126">How to Connect to the New Endpoint</span></span>

<span data-ttu-id="8750c-127">Skapa en PowerShell-session till den nya PowerShell-slutpunkten genom att ange `-ConfigurationName "some endpoint name"`.</span><span class="sxs-lookup"><span data-stu-id="8750c-127">Create a PowerShell session to the new PowerShell endpoint by specifying `-ConfigurationName "some endpoint name"`.</span></span> <span data-ttu-id="8750c-128">Använd antingen när du ansluter till PowerShell-instansen i exemplet ovan:</span><span class="sxs-lookup"><span data-stu-id="8750c-128">To connect to the PowerShell instance from the example above, use either:</span></span>

```powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

<span data-ttu-id="8750c-129">Observera att `New-PSSession` och `Enter-PSSession` anrop som inte anger `-ConfigurationName` rikta in dig på PowerShell standardslutpunkten `microsoft.powershell`.</span><span class="sxs-lookup"><span data-stu-id="8750c-129">Note that `New-PSSession` and `Enter-PSSession` invocations that do not specify `-ConfigurationName` will target the default PowerShell endpoint, `microsoft.powershell`.</span></span>