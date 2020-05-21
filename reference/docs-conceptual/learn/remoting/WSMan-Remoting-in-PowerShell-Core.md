---
title: WS-Management-fjärrkommunikation (WSMan) i PowerShell Core
description: Fjärr kommunikation i PowerShell Core med WSMan
ms.date: 08/06/2018
ms.openlocfilehash: 7b090e1463808ab10758bbd417d52fcc16c31366
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564521"
---
# <a name="ws-management-wsman-remoting-in-powershell-core"></a><span data-ttu-id="436e2-103">WS-Management-fjärrkommunikation (WSMan) i PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="436e2-103">WS-Management (WSMan) Remoting in PowerShell Core</span></span>

## <a name="instructions-to-create-a-remoting-endpoint"></a><span data-ttu-id="436e2-104">Instruktioner för att skapa en fjärran sluten slut punkt</span><span class="sxs-lookup"><span data-stu-id="436e2-104">Instructions to Create a Remoting Endpoint</span></span>

<span data-ttu-id="436e2-105">PowerShell Core-paketet för Windows innehåller ett WinRM-plugin-program ( `pwrshplugin.dll` ) och ett installations skript ( `Install-PowerShellRemoting.ps1` ) i `$PSHome` .</span><span class="sxs-lookup"><span data-stu-id="436e2-105">The PowerShell Core package for Windows includes a WinRM plug-in (`pwrshplugin.dll`) and an installation script (`Install-PowerShellRemoting.ps1`) in `$PSHome`.</span></span>
<span data-ttu-id="436e2-106">De här filerna gör att PowerShell kan acceptera inkommande PowerShell fjärr anslutningar när dess slut punkt anges.</span><span class="sxs-lookup"><span data-stu-id="436e2-106">These files enable PowerShell to accept incoming PowerShell remote connections when its endpoint is specified.</span></span>

### <a name="motivation"></a><span data-ttu-id="436e2-107">Motivation</span><span class="sxs-lookup"><span data-stu-id="436e2-107">Motivation</span></span>

<span data-ttu-id="436e2-108">En installation av PowerShell kan upprätta PowerShell-sessioner till fjärrdatorer med hjälp av `New-PSSession` och `Enter-PSSession` .</span><span class="sxs-lookup"><span data-stu-id="436e2-108">An installation of PowerShell can establish PowerShell sessions to remote computers using `New-PSSession` and `Enter-PSSession`.</span></span>
<span data-ttu-id="436e2-109">För att det ska kunna ta emot inkommande PowerShell-fjärranslutningar måste användaren skapa en WinRM Remoting-slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="436e2-109">To enable it to accept incoming PowerShell remote connections, the user must create a WinRM remoting endpoint.</span></span>
<span data-ttu-id="436e2-110">Det här är ett explicit scenario där användaren kör Install-PowerShellRemoting. ps1 för att skapa WinRM-slutpunkten.</span><span class="sxs-lookup"><span data-stu-id="436e2-110">This is an explicit opt-in scenario where the user runs Install-PowerShellRemoting.ps1 to create the WinRM endpoint.</span></span>
<span data-ttu-id="436e2-111">Installations skriptet är en kortsiktig lösning tills vi lägger till ytterligare funktioner till `Enable-PSRemoting` för att utföra samma åtgärd.</span><span class="sxs-lookup"><span data-stu-id="436e2-111">The installation script is a short-term solution until we add additional functionality to `Enable-PSRemoting` to perform the same action.</span></span>
<span data-ttu-id="436e2-112">Mer information hittar du i problem [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span><span class="sxs-lookup"><span data-stu-id="436e2-112">For more details, please see issue [#1193](https://github.com/PowerShell/PowerShell/issues/1193).</span></span>

### <a name="script-actions"></a><span data-ttu-id="436e2-113">Skript åtgärder</span><span class="sxs-lookup"><span data-stu-id="436e2-113">Script Actions</span></span>

<span data-ttu-id="436e2-114">Skriptet</span><span class="sxs-lookup"><span data-stu-id="436e2-114">The script</span></span>

1. <span data-ttu-id="436e2-115">Skapar en katalog för plugin-programmet i`$env:windir\System32\PowerShell`</span><span class="sxs-lookup"><span data-stu-id="436e2-115">Creates a directory for the plug-in within `$env:windir\System32\PowerShell`</span></span>
1. <span data-ttu-id="436e2-116">Kopierar pwrshplugin. dll till den platsen</span><span class="sxs-lookup"><span data-stu-id="436e2-116">Copies pwrshplugin.dll to that location</span></span>
1. <span data-ttu-id="436e2-117">Genererar en konfigurations fil</span><span class="sxs-lookup"><span data-stu-id="436e2-117">Generates a configuration file</span></span>
1. <span data-ttu-id="436e2-118">Registrerar plugin-programmet med WinRM</span><span class="sxs-lookup"><span data-stu-id="436e2-118">Registers that plug-in with WinRM</span></span>

### <a name="registration"></a><span data-ttu-id="436e2-119">Registrering</span><span class="sxs-lookup"><span data-stu-id="436e2-119">Registration</span></span>

<span data-ttu-id="436e2-120">Skriptet måste köras i en PowerShell-session på administratörs nivå och köras i två lägen.</span><span class="sxs-lookup"><span data-stu-id="436e2-120">The script must be executed within an Administrator-level PowerShell session and runs in two modes.</span></span>

#### <a name="executed-by-the-instance-of-powershell-that-it-will-register"></a><span data-ttu-id="436e2-121">Körs av den instans av PowerShell som den ska registreras</span><span class="sxs-lookup"><span data-stu-id="436e2-121">Executed by the instance of PowerShell that it will register</span></span>

```powershell
Install-PowerShellRemoting.ps1
```

#### <a name="executed-by-another-instance-of-powershell-on-behalf-of-the-instance-that-it-will-register"></a><span data-ttu-id="436e2-122">Utföras av en annan instans av PowerShell på uppdrag av den instans som den ska registreras</span><span class="sxs-lookup"><span data-stu-id="436e2-122">Executed by another instance of PowerShell on behalf of the instance that it will register</span></span>

```powershell
<path to powershell>\Install-PowerShellRemoting.ps1 -PowerShellHome "<absolute path to the instance's $PSHOME>"
```

<span data-ttu-id="436e2-123">Exempel:</span><span class="sxs-lookup"><span data-stu-id="436e2-123">For Example:</span></span>

```powershell
Set-Location -Path 'C:\Program Files\PowerShell\6.0.0\'
.\Install-PowerShellRemoting.ps1 -PowerShellHome "C:\Program Files\PowerShell\6.0.0\"
```

<span data-ttu-id="436e2-124">**Obs:** Registrerings skriptet för fjärr kommunikation startar om WinRM, så att alla befintliga PSRP-sessioner avslutas omedelbart efter att skriptet har körts.</span><span class="sxs-lookup"><span data-stu-id="436e2-124">**NOTE:** The remoting registration script will restart WinRM, so all existing PSRP sessions will terminate immediately after the script is run.</span></span> <span data-ttu-id="436e2-125">Om kör under en fjärrsession kommer detta att avsluta anslutningen.</span><span class="sxs-lookup"><span data-stu-id="436e2-125">If run during a remote session, this will terminate the connection.</span></span>

## <a name="how-to-connect-to-the-new-endpoint"></a><span data-ttu-id="436e2-126">Så här ansluter du till den nya slut punkten</span><span class="sxs-lookup"><span data-stu-id="436e2-126">How to Connect to the New Endpoint</span></span>

<span data-ttu-id="436e2-127">Skapa en PowerShell-session för den nya PowerShell-slutpunkten genom att ange `-ConfigurationName "some endpoint name"` .</span><span class="sxs-lookup"><span data-stu-id="436e2-127">Create a PowerShell session to the new PowerShell endpoint by specifying `-ConfigurationName "some endpoint name"`.</span></span> <span data-ttu-id="436e2-128">Om du vill ansluta till PowerShell-instansen från exemplet ovan använder du antingen:</span><span class="sxs-lookup"><span data-stu-id="436e2-128">To connect to the PowerShell instance from the example above, use either:</span></span>

```powershell
New-PSSession ... -ConfigurationName "powershell.6.0.0"
Enter-PSSession ... -ConfigurationName "powershell.6.0.0"
```

<span data-ttu-id="436e2-129">Observera att `New-PSSession` och `Enter-PSSession` anrop som inte anges `-ConfigurationName` kommer att riktas mot standard-PowerShell-slutpunkten `microsoft.powershell` .</span><span class="sxs-lookup"><span data-stu-id="436e2-129">Note that `New-PSSession` and `Enter-PSSession` invocations that do not specify `-ConfigurationName` will target the default PowerShell endpoint, `microsoft.powershell`.</span></span>
