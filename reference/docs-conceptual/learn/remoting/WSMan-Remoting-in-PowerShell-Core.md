---
title: WS-Management-fjärrkommunikation (WSMan) i PowerShell Core
description: Fjärr kommunikation i PowerShell Core med WSMan
ms.date: 08/06/2018
ms.openlocfilehash: fdc4159279db28b8ee60bc0853e19512a1f9ec14
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501311"
---
# <a name="ws-management-wsman-remoting-in-powershell-core"></a><span data-ttu-id="5decd-103">WS-Management-fjärrkommunikation (WSMan) i PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="5decd-103">WS-Management (WSMan) Remoting in PowerShell Core</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="5decd-104">Instruktioner för att skapa en fjärran sluten slut punkt</span><span class="sxs-lookup"><span data-stu-id="5decd-104">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="5decd-105">PowerShell Core-paketet för Windows innehåller ett WinRM-plugin-program ( `pwrshplugin.dll` ) och ett installations skript ( `Install-PowerShellRemoting.ps1` ) i `$PSHome` .</span><span class="sxs-lookup"><span data-stu-id="5decd-105">The PowerShell Core package for Windows includes a WinRM plug-in (`pwrshplugin.dll`) and an installation script (`Install-PowerShellRemoting.ps1`) in `$PSHome`.</span></span> <span data-ttu-id="5decd-106">De här filerna gör att PowerShell kan acceptera inkommande PowerShell fjärr anslutningar när dess slut punkt anges.</span><span class="sxs-lookup"><span data-stu-id="5decd-106">These files enable PowerShell to accept incoming PowerShell remote connections when its endpoint is specified.</span></span>

### <a name="motivation"></a><span data-ttu-id="5decd-107">Motivation</span><span class="sxs-lookup"><span data-stu-id="5decd-107">Motivation</span></span>

<span data-ttu-id="5decd-108">En installation av PowerShell kan upprätta PowerShell-sessioner till fjärrdatorer med hjälp av `New-PSSession` och `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="5decd-108">An installation of PowerShell can establish PowerShell sessions to remote computers using `New-PSSession` and `Enter-PSSession`.</span></span> <span data-ttu-id="5decd-109">För att det ska kunna ta emot inkommande PowerShell-fjärranslutningar måste användaren skapa en WinRM Remoting-slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="5decd-109">To enable it to accept incoming PowerShell remote connections, the user must create a WinRM remoting endpoint.</span></span> <span data-ttu-id="5decd-110">Det här är ett explicit scenario där användaren kör Install-PowerShellRemoting.ps1 för att skapa WinRM-slutpunkten.</span><span class="sxs-lookup"><span data-stu-id="5decd-110">This is an explicit opt-in scenario where the user runs Install-PowerShellRemoting.ps1 to create the WinRM endpoint.</span></span> <span data-ttu-id="5decd-111">Installations skriptet är en kortsiktig lösning tills vi lägger till ytterligare funktioner till `Enable-PSRemoting` för att utföra samma åtgärd.</span><span class="sxs-lookup"><span data-stu-id="5decd-111">The installation script is a short-term solution until we add additional functionality to `Enable-PSRemoting` to perform the same action.</span></span> <span data-ttu-id="5decd-112">Mer information hittar du i problem [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span><span class="sxs-lookup"><span data-stu-id="5decd-112">For more details, please see issue [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span></span>

### <a name="script-actions"></a><span data-ttu-id="5decd-113">Skript åtgärder</span><span class="sxs-lookup"><span data-stu-id="5decd-113">Script Actions</span></span>

<span data-ttu-id="5decd-114">Skriptet</span><span class="sxs-lookup"><span data-stu-id="5decd-114">The script</span></span>

1. <span data-ttu-id="5decd-115">Skapar en katalog för plugin-programmet i `$env:windir\System32\PowerShell`</span><span class="sxs-lookup"><span data-stu-id="5decd-115">Creates a directory for the plug-in within `$env:windir\System32\PowerShell`</span></span>
1. <span data-ttu-id="5decd-116">Kopierar pwrshplugin.dll till den platsen</span><span class="sxs-lookup"><span data-stu-id="5decd-116">Copies pwrshplugin.dll to that location</span></span>
1. <span data-ttu-id="5decd-117">Genererar en konfigurations fil</span><span class="sxs-lookup"><span data-stu-id="5decd-117">Generates a configuration file</span></span>
1. <span data-ttu-id="5decd-118">Registrerar plugin-programmet med WinRM</span><span class="sxs-lookup"><span data-stu-id="5decd-118">Registers that plug-in with WinRM</span></span>

### <a name="registration"></a><span data-ttu-id="5decd-119">Registrering</span><span class="sxs-lookup"><span data-stu-id="5decd-119">Registration</span></span>

<span data-ttu-id="5decd-120">Skriptet måste köras i en PowerShell-session på administratörs nivå och köras i två lägen.</span><span class="sxs-lookup"><span data-stu-id="5decd-120">The script must be executed within an Administrator-level PowerShell session and runs in two modes.</span></span>

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a><span data-ttu-id="5decd-121">Körs av den instans av PowerShell som den ska registreras</span><span class="sxs-lookup"><span data-stu-id="5decd-121">Executed by the instance of PowerShell that it will register</span></span>

```powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a><span data-ttu-id="5decd-122">Utföras av en annan instans av PowerShell på uppdrag av den instans som den ska registreras</span><span class="sxs-lookup"><span data-stu-id="5decd-122">Executed by another instance of PowerShell on behalf of the instance that it will register</span></span>

```powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

<span data-ttu-id="5decd-123">Exempel:</span><span class="sxs-lookup"><span data-stu-id="5decd-123">For Example:</span></span>

```powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

> [!NOTE]
> <span data-ttu-id="5decd-124">Registrerings skriptet för fjärr kommunikation startar om WinRM.</span><span class="sxs-lookup"><span data-stu-id="5decd-124">The remoting registration script restarts WinRM.</span></span> <span data-ttu-id="5decd-125">Alla befintliga PSRP-sessioner avslutas omedelbart efter att skriptet har körts.</span><span class="sxs-lookup"><span data-stu-id="5decd-125">All existing PSRP sessions are terminate immediately after the script is run.</span></span> <span data-ttu-id="5decd-126">Om kör under en fjärrsession avslutar skriptet anslutningen.</span><span class="sxs-lookup"><span data-stu-id="5decd-126">If run during a remote session, the script terminates the connection.</span></span>

## <a name="how-to-connect-to-the-new-endpoint"></a><span data-ttu-id="5decd-127">Så här ansluter du till den nya slut punkten</span><span class="sxs-lookup"><span data-stu-id="5decd-127">How to Connect to the New Endpoint</span></span>

<span data-ttu-id="5decd-128">Skapa en PowerShell-session för den nya PowerShell-slutpunkten genom att ange `-ConfigurationName "some endpoint name"` .</span><span class="sxs-lookup"><span data-stu-id="5decd-128">Create a PowerShell session to the new PowerShell endpoint by specifying `-ConfigurationName "some endpoint name"`.</span></span> <span data-ttu-id="5decd-129">Om du vill ansluta till PowerShell-instansen från exemplet ovan använder du antingen:</span><span class="sxs-lookup"><span data-stu-id="5decd-129">To connect to the PowerShell instance from the example above, use either:</span></span>

```powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

<span data-ttu-id="5decd-130">Observera att `New-PSSession` och `Enter-PSSession` anrop som inte anges `-ConfigurationName` kommer att riktas mot standard-PowerShell-slutpunkten `microsoft.powershell` .</span><span class="sxs-lookup"><span data-stu-id="5decd-130">Note that `New-PSSession` and `Enter-PSSession` invocations that do not specify `-ConfigurationName` will target the default PowerShell endpoint, `microsoft.powershell`.</span></span>
