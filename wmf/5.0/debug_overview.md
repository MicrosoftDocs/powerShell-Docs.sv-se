---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
ms.openlocfilehash: dee5e8206c61d79faadf8573a82c74d4ac0fb8e0
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="improvements-in-powershell-script-debugging"></a><span data-ttu-id="af55c-102">Förbättringar i felsökning av PowerShell-skript</span><span class="sxs-lookup"><span data-stu-id="af55c-102">Improvements in PowerShell Script Debugging</span></span>

<span data-ttu-id="af55c-103">Ett antal förbättringar har gjorts i PowerShell 5.0 att förbättra Felsökning:</span><span class="sxs-lookup"><span data-stu-id="af55c-103">A number of improvements were made in PowerShell 5.0 to enhance the debugging experience:</span></span>

## <a name="break-all"></a><span data-ttu-id="af55c-104">Bryt alla</span><span class="sxs-lookup"><span data-stu-id="af55c-104">Break All</span></span>

<span data-ttu-id="af55c-105">PowerShell-konsolen och Windows PowerShell ISE nu kan du bryta in i felsökaren för att köra skript.</span><span class="sxs-lookup"><span data-stu-id="af55c-105">The PowerShell console and Windows PowerShell ISE now allow you to break into the debugger for running scripts.</span></span> <span data-ttu-id="af55c-106">Det här fungerar i både lokala och fjärranslutna sessioner.</span><span class="sxs-lookup"><span data-stu-id="af55c-106">This works in both local and remote sessions.</span></span>

<span data-ttu-id="af55c-107">I konsolen, trycker du på **Ctrl + Break**.</span><span class="sxs-lookup"><span data-stu-id="af55c-107">In the console, press **Ctrl+Break**.</span></span>

<span data-ttu-id="af55c-108">I ISE, trycker du på **Ctrl + B**, eller använda den **Debug -> Bryt alla** kommando.</span><span class="sxs-lookup"><span data-stu-id="af55c-108">In ISE, press **Ctrl+B**, or use the **Debug -> Break All** menu command.</span></span>

## <a name="remote-debugging-and-remote-file-editing-in-windows-powershell-ise"></a><span data-ttu-id="af55c-109">Fjärrfelsökning och Fjärrlagring redigering i Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="af55c-109">Remote debugging and remote file editing in Windows PowerShell ISE</span></span>

<span data-ttu-id="af55c-110">Windows PowerShell ISE nu kan du öppna och redigera filer i en fjärrsession genom att köra kommandot PSEdit.</span><span class="sxs-lookup"><span data-stu-id="af55c-110">Windows PowerShell ISE now lets you open and edit files in a remote session by running the PSEdit command.</span></span>
<span data-ttu-id="af55c-111">Du kan till exempel öppna en fil för redigering från kommandoraden i en fjärrsession på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="af55c-111">For example, you can open a file for editing from the command line in a remote session as follows:</span></span>

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

<span data-ttu-id="af55c-112">Dessutom kan du nu redigera och spara ändringarna i en fjärrfil som öppnas automatiskt i Windows PowerShell ISE när du klickar på en brytpunkt.</span><span class="sxs-lookup"><span data-stu-id="af55c-112">In addition, you can now edit and save changes in a remote file that is automatically opened in Windows PowerShell ISE when you hit a breakpoint.</span></span>
<span data-ttu-id="af55c-113">Nu kan du felsöka en skriptfil som körs på en fjärrdator, redigera filen för att åtgärda ett fel och kör sedan skriptet ändrade.</span><span class="sxs-lookup"><span data-stu-id="af55c-113">Now, you can debug a script file that is running on a remote computer, edit the file to fix an error, and then rerun the modified script.</span></span>

## <a name="advanced-script-debugging"></a><span data-ttu-id="af55c-114">Felsökning av avancerade skript</span><span class="sxs-lookup"><span data-stu-id="af55c-114">Advanced Script Debugging</span></span>

<span data-ttu-id="af55c-115">Det finns nya, avancerad felsökning funktioner som gör att du kan ansluta till en lokal dator process som har lästs in Windows PowerShell och felsöka godtycklig körningsutrymmen i den här processen.</span><span class="sxs-lookup"><span data-stu-id="af55c-115">There are new, advanced debugging features that let you attach to any local computer process that has loaded Windows PowerShell, and debug arbitrary runspaces in that process.</span></span>

### <a name="runspace-debugging"></a><span data-ttu-id="af55c-116">Runspace felsökning</span><span class="sxs-lookup"><span data-stu-id="af55c-116">Runspace Debugging</span></span>

<span data-ttu-id="af55c-117">Nya cmdletar har lagts till som du kan visa en lista över aktuella körningsutrymmen i en process och bifoga Windows PowerShell-konsolen eller ISE felsökare som runspace för felsökning av skript:</span><span class="sxs-lookup"><span data-stu-id="af55c-117">New cmdlets have been added that let you list current runspaces in a process, and attach the Windows PowerShell console or ISE debugger to that runspace for script debugging:</span></span>

-   <span data-ttu-id="af55c-118">Get-Runspace</span><span class="sxs-lookup"><span data-stu-id="af55c-118">Get-Runspace</span></span>
-   <span data-ttu-id="af55c-119">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="af55c-119">Debug-Runspace</span></span>
-   <span data-ttu-id="af55c-120">Aktivera RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="af55c-120">Enable-RunspaceDebug</span></span>
-   <span data-ttu-id="af55c-121">Inaktivera RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="af55c-121">Disable-RunspaceDebug</span></span>
-   <span data-ttu-id="af55c-122">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="af55c-122">Get-RunspaceDebug</span></span>

### <a name="attach-to-process-hosting-powershell"></a><span data-ttu-id="af55c-123">Koppla till Process som är värd för PowerShell</span><span class="sxs-lookup"><span data-stu-id="af55c-123">Attach to Process hosting PowerShell</span></span>

<span data-ttu-id="af55c-124">Nu kan du koppla till alla processer för datorn med Windows PowerShell som lästs in.</span><span class="sxs-lookup"><span data-stu-id="af55c-124">You can now attach to any computer process that has Windows PowerShell loaded.</span></span> <span data-ttu-id="af55c-125">Du kan göra detta genom att ange i en interaktiv session med processen, på samma sätt som hur du kan ange i en interaktiv fjärrsession genom att köra cmdleten Enter-PSSession:</span><span class="sxs-lookup"><span data-stu-id="af55c-125">You do this by entering into an interactive session with the process, similarly to how you enter into an interactive remote session by running the Enter-PSSession cmdlet:</span></span>

-   <span data-ttu-id="af55c-126">Enter-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="af55c-126">Enter-PSHostProcess</span></span>
-   <span data-ttu-id="af55c-127">Exit-PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="af55c-127">Exit-PSHostProcess</span></span>