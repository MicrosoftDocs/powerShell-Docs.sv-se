---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Förbättringar i felsökning av PowerShell-skript
description: WMF 5,0 lägger till nya fel söknings funktioner i Windows-PoowerShell.
ms.openlocfilehash: 5703343e1b85024931638e8b04a09f7208ea123c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92646738"
---
# <a name="improvements-in-powershell-script-debugging"></a><span data-ttu-id="f8a62-104">Förbättringar i felsökning av PowerShell-skript</span><span class="sxs-lookup"><span data-stu-id="f8a62-104">Improvements in PowerShell Script Debugging</span></span>

<span data-ttu-id="f8a62-105">PowerShell 5,0 innehåller flera förbättringar som förbättrar fel söknings upplevelsen.</span><span class="sxs-lookup"><span data-stu-id="f8a62-105">PowerShell 5.0 includes several improvements that enhance the debugging experience.</span></span>

## <a name="break-all"></a><span data-ttu-id="f8a62-106">Bryt alla</span><span class="sxs-lookup"><span data-stu-id="f8a62-106">Break All</span></span>

<span data-ttu-id="f8a62-107">Med PowerShell-konsolen och PowerShell ISE kan du nu dela upp det i fel söknings programmet för skript körning.</span><span class="sxs-lookup"><span data-stu-id="f8a62-107">The PowerShell console and PowerShell ISE now allow you to break into the debugger for running scripts.</span></span> <span data-ttu-id="f8a62-108">Detta fungerar både i lokala och fjärranslutna sessioner.</span><span class="sxs-lookup"><span data-stu-id="f8a62-108">This works in both local and remote sessions.</span></span>

<span data-ttu-id="f8a62-109">Tryck på <kbd>CTRL</kbd> + <kbd>Break</kbd>i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="f8a62-109">In the console, press <kbd>Ctrl</kbd>+<kbd>Break</kbd>.</span></span>

<span data-ttu-id="f8a62-110">Tryck på <kbd>CTRL</kbd> + <kbd>B</kbd>i ISE eller Använd kommandot **Debug-> Bryt alla** Meny kommandon.</span><span class="sxs-lookup"><span data-stu-id="f8a62-110">In ISE, press <kbd>Ctrl</kbd>+<kbd>B</kbd>, or use the **Debug -> Break All** menu command.</span></span>

## <a name="remote-debugging-and-remote-file-editing-in-powershell-ise"></a><span data-ttu-id="f8a62-111">Fjärrfelsökning och fjärrstyrd fil redigering i PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="f8a62-111">Remote debugging and remote file editing in PowerShell ISE</span></span>

<span data-ttu-id="f8a62-112">Nu kan du öppna och redigera filer i en fjärrsession med PowerShell ISE genom att köra kommandot PSEdit.</span><span class="sxs-lookup"><span data-stu-id="f8a62-112">PowerShell ISE now lets you open and edit files in a remote session by running the PSEdit command.</span></span>
<span data-ttu-id="f8a62-113">Du kan till exempel öppna en fil för redigering från kommando raden i en fjärrsession enligt följande:</span><span class="sxs-lookup"><span data-stu-id="f8a62-113">For example, you can open a file for editing from the command line in a remote session as follows:</span></span>

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

<span data-ttu-id="f8a62-114">Dessutom kan du nu redigera och spara ändringar i en fjärrfil som öppnas automatiskt i PowerShell ISE när du trycker på en Bryt punkt.</span><span class="sxs-lookup"><span data-stu-id="f8a62-114">In addition, you can now edit and save changes in a remote file that is automatically opened in PowerShell ISE when you hit a breakpoint.</span></span> <span data-ttu-id="f8a62-115">Nu kan du Felsöka en skript fil som körs på en fjärrdator, redigera filen för att åtgärda ett fel och sedan köra det ändrade skriptet igen.</span><span class="sxs-lookup"><span data-stu-id="f8a62-115">Now, you can debug a script file that is running on a remote computer, edit the file to fix an error, and then rerun the modified script.</span></span>

## <a name="advanced-script-debugging"></a><span data-ttu-id="f8a62-116">Avancerad skript fel sökning</span><span class="sxs-lookup"><span data-stu-id="f8a62-116">Advanced Script Debugging</span></span>

<span data-ttu-id="f8a62-117">Det finns nya, avancerade fel söknings funktioner som gör att du kan ansluta till en lokal dator process som har läst in PowerShell och felsöka godtyckliga körnings utrymmen i den processen.</span><span class="sxs-lookup"><span data-stu-id="f8a62-117">There are new, advanced debugging features that let you attach to any local computer process that has loaded PowerShell, and debug arbitrary runspaces in that process.</span></span>

### <a name="runspace-debugging"></a><span data-ttu-id="f8a62-118">Körnings utrymme-felsökning</span><span class="sxs-lookup"><span data-stu-id="f8a62-118">Runspace Debugging</span></span>

<span data-ttu-id="f8a62-119">Nya cmdletar har lagts till som gör att du kan lista aktuella körnings utrymmen i en process och koppla PowerShell-konsolen eller PowerShell ISE-felsökaren till den körnings utrymme för skript fel sökning:</span><span class="sxs-lookup"><span data-stu-id="f8a62-119">New cmdlets have been added that let you list current runspaces in a process, and attach the PowerShell console or PowerShell ISE debugger to that runspace for script debugging:</span></span>

- <span data-ttu-id="f8a62-120">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="f8a62-120">Get-Runspace</span></span>
- <span data-ttu-id="f8a62-121">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="f8a62-121">Debug-Runspace</span></span>
- <span data-ttu-id="f8a62-122">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="f8a62-122">Enable-RunspaceDebug</span></span>
- <span data-ttu-id="f8a62-123">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="f8a62-123">Disable-RunspaceDebug</span></span>
- <span data-ttu-id="f8a62-124">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="f8a62-124">Get-RunspaceDebug</span></span>

### <a name="attach-to-process-hosting-powershell"></a><span data-ttu-id="f8a62-125">Ansluta till process hosting PowerShell</span><span class="sxs-lookup"><span data-stu-id="f8a62-125">Attach to Process hosting PowerShell</span></span>

<span data-ttu-id="f8a62-126">Nu kan du ansluta till en dator process som har PowerShell inläst.</span><span class="sxs-lookup"><span data-stu-id="f8a62-126">You can now attach to any computer process that has PowerShell loaded.</span></span> <span data-ttu-id="f8a62-127">Du gör detta genom att ange en interaktiv session med värd processen.</span><span class="sxs-lookup"><span data-stu-id="f8a62-127">You do this by entering into an interactive session with the host process.</span></span> <span data-ttu-id="f8a62-128">Mer information finns i:</span><span class="sxs-lookup"><span data-stu-id="f8a62-128">For more information, see:</span></span>

- [<span data-ttu-id="f8a62-129">Retur-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="f8a62-129">Enter-PSHostProcess</span></span>](/powershell/module/Microsoft.PowerShell.Core/Enter-PSHostProcess)
- [<span data-ttu-id="f8a62-130">Avsluta-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="f8a62-130">Exit-PSHostProcess</span></span>](/powershell/module/Microsoft.PowerShell.Core/Exit-PSHostProcess)
