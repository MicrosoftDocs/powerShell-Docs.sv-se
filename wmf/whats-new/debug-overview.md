---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Förbättringar i felsökning av PowerShell-skript
ms.openlocfilehash: f1771a451ba671da2371fcfc95374e6131573ddc
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856177"
---
# <a name="improvements-in-powershell-script-debugging"></a><span data-ttu-id="449f7-103">Förbättringar i felsökning av PowerShell-skript</span><span class="sxs-lookup"><span data-stu-id="449f7-103">Improvements in PowerShell Script Debugging</span></span>

<span data-ttu-id="449f7-104">PowerShell 5.0 innehåller flera förbättringar som förbättrar upplevelsen för felsökning.</span><span class="sxs-lookup"><span data-stu-id="449f7-104">PowerShell 5.0 includes several improvements that enhance the debugging experience.</span></span>

## <a name="break-all"></a><span data-ttu-id="449f7-105">Bryt alla</span><span class="sxs-lookup"><span data-stu-id="449f7-105">Break All</span></span>

<span data-ttu-id="449f7-106">PowerShell-konsolen och PowerShell ISE nu kan du bryta in i felsökaren för att köra skript.</span><span class="sxs-lookup"><span data-stu-id="449f7-106">The PowerShell console and PowerShell ISE now allow you to break into the debugger for running scripts.</span></span> <span data-ttu-id="449f7-107">Detta fungerar i både lokala och fjärrskrivbord-sessioner.</span><span class="sxs-lookup"><span data-stu-id="449f7-107">This works in both local and remote sessions.</span></span>

<span data-ttu-id="449f7-108">I konsolen, trycker du på <kbd>Ctrl</kbd>+<kbd>bryta</kbd>.</span><span class="sxs-lookup"><span data-stu-id="449f7-108">In the console, press <kbd>Ctrl</kbd>+<kbd>Break</kbd>.</span></span>

<span data-ttu-id="449f7-109">I ISE, trycker du på <kbd>Ctrl</kbd>+<kbd>B</kbd>, eller Använd den **felsökning -> bryta alla** menykommandot.</span><span class="sxs-lookup"><span data-stu-id="449f7-109">In ISE, press <kbd>Ctrl</kbd>+<kbd>B</kbd>, or use the **Debug -> Break All** menu command.</span></span>

## <a name="remote-debugging-and-remote-file-editing-in-powershell-ise"></a><span data-ttu-id="449f7-110">Fjärrfelsökning och fjärrfil redigering i PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="449f7-110">Remote debugging and remote file editing in PowerShell ISE</span></span>

<span data-ttu-id="449f7-111">PowerShell ISE nu kan du öppna och redigera filer i en fjärrsession genom att köra kommandot PSEdit.</span><span class="sxs-lookup"><span data-stu-id="449f7-111">PowerShell ISE now lets you open and edit files in a remote session by running the PSEdit command.</span></span>
<span data-ttu-id="449f7-112">Du kan till exempel öppna en fil för redigering från kommandoraden i en fjärrsession på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="449f7-112">For example, you can open a file for editing from the command line in a remote session as follows:</span></span>

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

<span data-ttu-id="449f7-113">Dessutom kan du nu redigera och spara ändringar i en fjärrfil som öppnas automatiskt i PowerShell ISE när du når en brytpunkt.</span><span class="sxs-lookup"><span data-stu-id="449f7-113">In addition, you can now edit and save changes in a remote file that is automatically opened in PowerShell ISE when you hit a breakpoint.</span></span> <span data-ttu-id="449f7-114">Nu kan du felsöka en skriptfil som körs på en fjärrdator, redigera filen för att åtgärda ett fel och kör sedan det ändrade skriptet.</span><span class="sxs-lookup"><span data-stu-id="449f7-114">Now, you can debug a script file that is running on a remote computer, edit the file to fix an error, and then rerun the modified script.</span></span>

## <a name="advanced-script-debugging"></a><span data-ttu-id="449f7-115">Felsökning av avancerade skript</span><span class="sxs-lookup"><span data-stu-id="449f7-115">Advanced Script Debugging</span></span>

<span data-ttu-id="449f7-116">Det finns nya, avancerad felsökning funktioner som låter dig ansluta till en lokal dator-process som har lästs in PowerShell och felsöka godtyckliga körningsutrymmen i den här processen.</span><span class="sxs-lookup"><span data-stu-id="449f7-116">There are new, advanced debugging features that let you attach to any local computer process that has loaded PowerShell, and debug arbitrary runspaces in that process.</span></span>

### <a name="runspace-debugging"></a><span data-ttu-id="449f7-117">Körningsutrymme felsökning</span><span class="sxs-lookup"><span data-stu-id="449f7-117">Runspace Debugging</span></span>

<span data-ttu-id="449f7-118">Nya cmdletar har lagts till som gör att du listan aktuella körningsutrymmen i en process och koppla PowerShell-konsolen eller PowerShell ISE debugger till den körningsutrymme för felsökning av skript:</span><span class="sxs-lookup"><span data-stu-id="449f7-118">New cmdlets have been added that let you list current runspaces in a process, and attach the PowerShell console or PowerShell ISE debugger to that runspace for script debugging:</span></span>

- <span data-ttu-id="449f7-119">Get-Körningsutrymme</span><span class="sxs-lookup"><span data-stu-id="449f7-119">Get-Runspace</span></span>
- <span data-ttu-id="449f7-120">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="449f7-120">Debug-Runspace</span></span>
- <span data-ttu-id="449f7-121">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="449f7-121">Enable-RunspaceDebug</span></span>
- <span data-ttu-id="449f7-122">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="449f7-122">Disable-RunspaceDebug</span></span>
- <span data-ttu-id="449f7-123">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="449f7-123">Get-RunspaceDebug</span></span>

### <a name="attach-to-process-hosting-powershell"></a><span data-ttu-id="449f7-124">Koppla till Process som är värd för PowerShell</span><span class="sxs-lookup"><span data-stu-id="449f7-124">Attach to Process hosting PowerShell</span></span>

<span data-ttu-id="449f7-125">Nu kan du koppla till en dator-process som har lästs in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="449f7-125">You can now attach to any computer process that has PowerShell loaded.</span></span> <span data-ttu-id="449f7-126">Du kan göra detta genom att ange i en interaktiv session med värdprocessen.</span><span class="sxs-lookup"><span data-stu-id="449f7-126">You do this by entering into an interactive session with the host process.</span></span> <span data-ttu-id="449f7-127">Mer information finns i följande avsnitt:</span><span class="sxs-lookup"><span data-stu-id="449f7-127">For more information, see:</span></span>

- [<span data-ttu-id="449f7-128">Ange PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="449f7-128">Enter-PSHostProcess</span></span>](/powershell/module/Microsoft.PowerShell.Core/Enter-PSHostProcess)
- [<span data-ttu-id="449f7-129">Avsluta PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="449f7-129">Exit-PSHostProcess</span></span>](/powershell/module/Microsoft.PowerShell.Core/Exit-PSHostProcess)
