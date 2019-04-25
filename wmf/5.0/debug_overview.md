---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 22a027ebc97e15075980bc77ce272d8ecdae0b5f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058673"
---
# <a name="improvements-in-powershell-script-debugging"></a><span data-ttu-id="8b0db-102">Förbättringar i felsökning av PowerShell-skript</span><span class="sxs-lookup"><span data-stu-id="8b0db-102">Improvements in PowerShell Script Debugging</span></span>

<span data-ttu-id="8b0db-103">Ett antal förbättringar har gjorts i PowerShell 5.0 att förbättra felsökningen:</span><span class="sxs-lookup"><span data-stu-id="8b0db-103">A number of improvements were made in PowerShell 5.0 to enhance the debugging experience:</span></span>

## <a name="break-all"></a><span data-ttu-id="8b0db-104">Bryt alla</span><span class="sxs-lookup"><span data-stu-id="8b0db-104">Break All</span></span>

<span data-ttu-id="8b0db-105">PowerShell-konsolen och Windows PowerShell ISE nu kan du bryta in i felsökaren för att köra skript.</span><span class="sxs-lookup"><span data-stu-id="8b0db-105">The PowerShell console and Windows PowerShell ISE now allow you to break into the debugger for running scripts.</span></span> <span data-ttu-id="8b0db-106">Detta fungerar i både lokala och fjärrskrivbord-sessioner.</span><span class="sxs-lookup"><span data-stu-id="8b0db-106">This works in both local and remote sessions.</span></span>

<span data-ttu-id="8b0db-107">I konsolen, trycker du på **Ctrl + Break**.</span><span class="sxs-lookup"><span data-stu-id="8b0db-107">In the console, press **Ctrl+Break**.</span></span>

<span data-ttu-id="8b0db-108">I ISE, trycker du på **Ctrl + B**, eller Använd den **felsökning -> bryta alla** menykommandot.</span><span class="sxs-lookup"><span data-stu-id="8b0db-108">In ISE, press **Ctrl+B**, or use the **Debug -> Break All** menu command.</span></span>

## <a name="remote-debugging-and-remote-file-editing-in-windows-powershell-ise"></a><span data-ttu-id="8b0db-109">Fjärrfelsökning och fjärrfil redigering i Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="8b0db-109">Remote debugging and remote file editing in Windows PowerShell ISE</span></span>

<span data-ttu-id="8b0db-110">Windows PowerShell ISE nu kan du öppna och redigera filer i en fjärrsession genom att köra kommandot PSEdit.</span><span class="sxs-lookup"><span data-stu-id="8b0db-110">Windows PowerShell ISE now lets you open and edit files in a remote session by running the PSEdit command.</span></span>
<span data-ttu-id="8b0db-111">Du kan till exempel öppna en fil för redigering från kommandoraden i en fjärrsession på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="8b0db-111">For example, you can open a file for editing from the command line in a remote session as follows:</span></span>

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

<span data-ttu-id="8b0db-112">Dessutom kan du nu redigera och spara ändringar i en fjärrfil som öppnas automatiskt i Windows PowerShell ISE när du når en brytpunkt.</span><span class="sxs-lookup"><span data-stu-id="8b0db-112">In addition, you can now edit and save changes in a remote file that is automatically opened in Windows PowerShell ISE when you hit a breakpoint.</span></span>
<span data-ttu-id="8b0db-113">Nu kan du felsöka en skriptfil som körs på en fjärrdator, redigera filen för att åtgärda ett fel och kör sedan det ändrade skriptet.</span><span class="sxs-lookup"><span data-stu-id="8b0db-113">Now, you can debug a script file that is running on a remote computer, edit the file to fix an error, and then rerun the modified script.</span></span>

## <a name="advanced-script-debugging"></a><span data-ttu-id="8b0db-114">Felsökning av avancerade skript</span><span class="sxs-lookup"><span data-stu-id="8b0db-114">Advanced Script Debugging</span></span>

<span data-ttu-id="8b0db-115">Det finns nya, avancerad felsökning funktioner som låter dig ansluta till en lokal dator-process som har lästs in Windows PowerShell och felsöka godtyckliga körningsutrymmen i den här processen.</span><span class="sxs-lookup"><span data-stu-id="8b0db-115">There are new, advanced debugging features that let you attach to any local computer process that has loaded Windows PowerShell, and debug arbitrary runspaces in that process.</span></span>

### <a name="runspace-debugging"></a><span data-ttu-id="8b0db-116">Körningsutrymme felsökning</span><span class="sxs-lookup"><span data-stu-id="8b0db-116">Runspace Debugging</span></span>

<span data-ttu-id="8b0db-117">Nya cmdletar har lagts till som gör att du listan aktuella körningsutrymmen i en process och koppla i Windows PowerShell-konsolen eller ISE debugger till den körningsutrymme för felsökning av skript:</span><span class="sxs-lookup"><span data-stu-id="8b0db-117">New cmdlets have been added that let you list current runspaces in a process, and attach the Windows PowerShell console or ISE debugger to that runspace for script debugging:</span></span>

-   <span data-ttu-id="8b0db-118">Get-Körningsutrymme</span><span class="sxs-lookup"><span data-stu-id="8b0db-118">Get-Runspace</span></span>
-   <span data-ttu-id="8b0db-119">Debug-Runspace</span><span class="sxs-lookup"><span data-stu-id="8b0db-119">Debug-Runspace</span></span>
-   <span data-ttu-id="8b0db-120">Enable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="8b0db-120">Enable-RunspaceDebug</span></span>
-   <span data-ttu-id="8b0db-121">Disable-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="8b0db-121">Disable-RunspaceDebug</span></span>
-   <span data-ttu-id="8b0db-122">Get-RunspaceDebug</span><span class="sxs-lookup"><span data-stu-id="8b0db-122">Get-RunspaceDebug</span></span>

### <a name="attach-to-process-hosting-powershell"></a><span data-ttu-id="8b0db-123">Koppla till Process som är värd för PowerShell</span><span class="sxs-lookup"><span data-stu-id="8b0db-123">Attach to Process hosting PowerShell</span></span>

<span data-ttu-id="8b0db-124">Nu kan du koppla till alla processer för datorn med Windows PowerShell som lästs in.</span><span class="sxs-lookup"><span data-stu-id="8b0db-124">You can now attach to any computer process that has Windows PowerShell loaded.</span></span> <span data-ttu-id="8b0db-125">Du kan göra detta genom att ange i en interaktiv session med processen, på samma sätt som hur du anger i en interaktiv fjärrsession genom att köra cmdleten Enter-PSSession:</span><span class="sxs-lookup"><span data-stu-id="8b0db-125">You do this by entering into an interactive session with the process, similarly to how you enter into an interactive remote session by running the Enter-PSSession cmdlet:</span></span>

-   <span data-ttu-id="8b0db-126">Ange PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="8b0db-126">Enter-PSHostProcess</span></span>
-   <span data-ttu-id="8b0db-127">Avsluta PSHostProcess</span><span class="sxs-lookup"><span data-stu-id="8b0db-127">Exit-PSHostProcess</span></span>
