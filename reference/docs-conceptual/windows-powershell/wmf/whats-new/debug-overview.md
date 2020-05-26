---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Förbättringar i felsökning av PowerShell-skript
ms.openlocfilehash: f1771a451ba671da2371fcfc95374e6131573ddc
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810395"
---
# <a name="improvements-in-powershell-script-debugging"></a><span data-ttu-id="0983e-103">Förbättringar i felsökning av PowerShell-skript</span><span class="sxs-lookup"><span data-stu-id="0983e-103">Improvements in PowerShell Script Debugging</span></span>

<span data-ttu-id="0983e-104">PowerShell 5,0 innehåller flera förbättringar som förbättrar fel söknings upplevelsen.</span><span class="sxs-lookup"><span data-stu-id="0983e-104">PowerShell 5.0 includes several improvements that enhance the debugging experience.</span></span>

## <a name="break-all"></a><span data-ttu-id="0983e-105">Bryt alla</span><span class="sxs-lookup"><span data-stu-id="0983e-105">Break All</span></span>

<span data-ttu-id="0983e-106">Med PowerShell-konsolen och PowerShell ISE kan du nu dela upp det i fel söknings programmet för skript körning.</span><span class="sxs-lookup"><span data-stu-id="0983e-106">The PowerShell console and PowerShell ISE now allow you to break into the debugger for running scripts.</span></span> <span data-ttu-id="0983e-107">Detta fungerar både i lokala och fjärranslutna sessioner.</span><span class="sxs-lookup"><span data-stu-id="0983e-107">This works in both local and remote sessions.</span></span>

<span data-ttu-id="0983e-108">Tryck på <kbd>CTRL</kbd> + <kbd>Break</kbd>i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="0983e-108">In the console, press <kbd>Ctrl</kbd>+<kbd>Break</kbd>.</span></span>

<span data-ttu-id="0983e-109">Tryck på <kbd>CTRL</kbd> + <kbd>B</kbd>i ISE eller Använd kommandot **Debug-> Bryt alla** Meny kommandon.</span><span class="sxs-lookup"><span data-stu-id="0983e-109">In ISE, press <kbd>Ctrl</kbd>+<kbd>B</kbd>, or use the **Debug -> Break All** menu command.</span></span>

## <a name="remote-debugging-and-remote-file-editing-in-powershell-ise"></a><span data-ttu-id="0983e-110">Fjärrfelsökning och fjärrstyrd fil redigering i PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="0983e-110">Remote debugging and remote file editing in PowerShell ISE</span></span>

<span data-ttu-id="0983e-111">Nu kan du öppna och redigera filer i en fjärrsession med PowerShell ISE genom att köra kommandot PSEdit.</span><span class="sxs-lookup"><span data-stu-id="0983e-111">PowerShell ISE now lets you open and edit files in a remote session by running the PSEdit command.</span></span>
<span data-ttu-id="0983e-112">Du kan till exempel öppna en fil för redigering från kommando raden i en fjärrsession enligt följande:</span><span class="sxs-lookup"><span data-stu-id="0983e-112">For example, you can open a file for editing from the command line in a remote session as follows:</span></span>

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

<span data-ttu-id="0983e-113">Dessutom kan du nu redigera och spara ändringar i en fjärrfil som öppnas automatiskt i PowerShell ISE när du trycker på en Bryt punkt.</span><span class="sxs-lookup"><span data-stu-id="0983e-113">In addition, you can now edit and save changes in a remote file that is automatically opened in PowerShell ISE when you hit a breakpoint.</span></span> <span data-ttu-id="0983e-114">Nu kan du Felsöka en skript fil som körs på en fjärrdator, redigera filen för att åtgärda ett fel och sedan köra det ändrade skriptet igen.</span><span class="sxs-lookup"><span data-stu-id="0983e-114">Now, you can debug a script file that is running on a remote computer, edit the file to fix an error, and then rerun the modified script.</span></span>

## <a name="advanced-script-debugging"></a><span data-ttu-id="0983e-115">Avancerad skript fel sökning</span><span class="sxs-lookup"><span data-stu-id="0983e-115">Advanced Script Debugging</span></span>

<span data-ttu-id="0983e-116">Det finns nya, avancerade fel söknings funktioner som gör att du kan ansluta till en lokal dator process som har läst in PowerShell och felsöka godtyckliga körnings utrymmen i den processen.</span><span class="sxs-lookup"><span data-stu-id="0983e-116">There are new, advanced debugging features that let you attach to any local computer process that has loaded PowerShell, and debug arbitrary runspaces in that process.</span></span>

### <a name="runspace-debugging"></a><span data-ttu-id="0983e-117">Körnings utrymme-felsökning</span><span class="sxs-lookup"><span data-stu-id="0983e-117">Runspace Debugging</span></span>

<span data-ttu-id="0983e-118">Nya cmdletar har lagts till som gör att du kan lista aktuella körnings utrymmen i en process och koppla PowerShell-konsolen eller PowerShell ISE-felsökaren till den körnings utrymme för skript fel sökning:</span><span class="sxs-lookup"><span data-stu-id="0983e-118">New cmdlets have been added that let you list current runspaces in a process, and attach the PowerShell console or PowerShell ISE debugger to that runspace for script debugging:</span></span>

- <span data-ttu-id="0983e-119">Get-körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="0983e-119">Get-Runspace</span></span>
- <span data-ttu-id="0983e-120">Felsök – körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="0983e-120">Debug-Runspace</span></span>
- <span data-ttu-id="0983e-121">Aktivera – RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="0983e-121">Enable-RunspaceDebug</span></span>
- <span data-ttu-id="0983e-122">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="0983e-122">Disable-RunspaceDebug</span></span>
- <span data-ttu-id="0983e-123">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="0983e-123">Get-RunspaceDebug</span></span>

### <a name="attach-to-process-hosting-powershell"></a><span data-ttu-id="0983e-124">Ansluta till process hosting PowerShell</span><span class="sxs-lookup"><span data-stu-id="0983e-124">Attach to Process hosting PowerShell</span></span>

<span data-ttu-id="0983e-125">Nu kan du ansluta till en dator process som har PowerShell inläst.</span><span class="sxs-lookup"><span data-stu-id="0983e-125">You can now attach to any computer process that has PowerShell loaded.</span></span> <span data-ttu-id="0983e-126">Du gör detta genom att ange en interaktiv session med värd processen.</span><span class="sxs-lookup"><span data-stu-id="0983e-126">You do this by entering into an interactive session with the host process.</span></span> <span data-ttu-id="0983e-127">Mer information finns i:</span><span class="sxs-lookup"><span data-stu-id="0983e-127">For more information, see:</span></span>

- [<span data-ttu-id="0983e-128">Retur-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="0983e-128">Enter-PSHostProcess</span></span>](/powershell/module/Microsoft.PowerShell.Core/Enter-PSHostProcess)
- [<span data-ttu-id="0983e-129">Avsluta-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="0983e-129">Exit-PSHostProcess</span></span>](/powershell/module/Microsoft.PowerShell.Core/Exit-PSHostProcess)
