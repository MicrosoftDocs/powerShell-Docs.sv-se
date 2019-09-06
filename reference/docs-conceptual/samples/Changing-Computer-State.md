---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Ändra datorstatus
ms.openlocfilehash: de3e31e358548943a015b7bba275c4461202b20f
ms.sourcegitcommit: d1ba596f9e0d4df9565601a70687a126d535c917
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/05/2019
ms.locfileid: "70386290"
---
# <a name="changing-computer-state"></a><span data-ttu-id="4c489-103">Ändra datorstatus</span><span class="sxs-lookup"><span data-stu-id="4c489-103">Changing Computer State</span></span>

<span data-ttu-id="4c489-104">Om du vill återställa en dator i Windows PowerShell använder du antingen ett standard kommando rads verktyg, WMI eller CIM-klass.</span><span class="sxs-lookup"><span data-stu-id="4c489-104">To reset a computer in Windows PowerShell, use either a standard command-line tool, WMI or CIM class.</span></span> <span data-ttu-id="4c489-105">Även om du bara använder Windows PowerShell för att köra verktyget, kan du lära dig hur du ändrar datorns energi tillstånd i Windows PowerShell. här visas några viktiga detaljer om hur du arbetar med externa verktyg i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4c489-105">Although you are using Windows PowerShell only to run the tool, learning how to change a computer's power state in Windows PowerShell illustrates some of the important details about working with external tools in Windows PowerShell.</span></span>

## <a name="locking-a-computer"></a><span data-ttu-id="4c489-106">Låsa en dator</span><span class="sxs-lookup"><span data-stu-id="4c489-106">Locking a Computer</span></span>

<span data-ttu-id="4c489-107">Det enda sättet att låsa en dator direkt med de standard verktyg som är tillgängliga är att anropa funktionen **LockWorkstation ()** i **user32. dll**:</span><span class="sxs-lookup"><span data-stu-id="4c489-107">The only way to lock a computer directly with the standard available tools is to call the **LockWorkstation()** function in **user32.dll**:</span></span>

```
rundll32.exe user32.dll,LockWorkStation
```

<span data-ttu-id="4c489-108">Det här kommandot låser arbets stationen omedelbart.</span><span class="sxs-lookup"><span data-stu-id="4c489-108">This command immediately locks the workstation.</span></span> <span data-ttu-id="4c489-109">Den använder *rundll32. exe*, som kör Windows-DLL: er (och sparar deras bibliotek för upprepad användning) för att köra user32. dll, ett bibliotek med Windows Management-funktioner.</span><span class="sxs-lookup"><span data-stu-id="4c489-109">It uses *rundll32.exe*, which runs Windows DLLs (and saves their libraries for repeated use) to run user32.dll, a library of Windows management functions.</span></span>

<span data-ttu-id="4c489-110">När du låser en arbets Station medan snabbt användar byte är aktiverat, till exempel på Windows XP, visar datorn inloggnings skärmen för användare i stället för att starta den aktuella användarens skärmsläckare.</span><span class="sxs-lookup"><span data-stu-id="4c489-110">When you lock a workstation while Fast User Switching is enabled, such as on Windows XP, the computer displays the user logon screen rather than starting the current user's screensaver.</span></span>

<span data-ttu-id="4c489-111">Om du vill stänga av vissa sessioner på en Terminal Server använder du kommando rads verktyget **tsshutdn. exe** .</span><span class="sxs-lookup"><span data-stu-id="4c489-111">To shut down particular sessions on a Terminal Server, use the **tsshutdn.exe** command-line tool.</span></span>

## <a name="logging-off-the-current-session"></a><span data-ttu-id="4c489-112">Logga ut den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="4c489-112">Logging Off the Current Session</span></span>

<span data-ttu-id="4c489-113">Du kan använda flera olika tekniker för att logga ut från en session på det lokala systemet.</span><span class="sxs-lookup"><span data-stu-id="4c489-113">You can use several different techniques to log off of a session on the local system.</span></span> <span data-ttu-id="4c489-114">Det enklaste sättet är att använda kommando rads verktyget fjärr skrivbord/Terminal Services, **LOGOFF. exe** (mer information finns i Windows PowerShell-prompten genom att skriva **LOGOFF/?** ).</span><span class="sxs-lookup"><span data-stu-id="4c489-114">The simplest way is to use the Remote Desktop/Terminal Services command-line tool, **logoff.exe** (For details, at the Windows PowerShell prompt, type **logoff /?**).</span></span> <span data-ttu-id="4c489-115">Logga ut den aktuella aktiva sessionen genom att skriva **LOGOFF** utan argument.</span><span class="sxs-lookup"><span data-stu-id="4c489-115">To log off the current active session, type **logoff** with no arguments.</span></span>

<span data-ttu-id="4c489-116">Du kan också använda **Shutdown. exe** -verktyget med dess utloggnings alternativ:</span><span class="sxs-lookup"><span data-stu-id="4c489-116">You can also use the **shutdown.exe** tool with its logoff option:</span></span>

```
shutdown.exe -l
```

<span data-ttu-id="4c489-117">Ett annat alternativ är att använda WMI.</span><span class="sxs-lookup"><span data-stu-id="4c489-117">Another option is to use WMI.</span></span> <span data-ttu-id="4c489-118">Win32_OperatingSystem-klassen har en Win32Shutdown-metod.</span><span class="sxs-lookup"><span data-stu-id="4c489-118">The Win32_OperatingSystem class has a Win32Shutdown method.</span></span> <span data-ttu-id="4c489-119">När du anropar metoden med flaggan 0 påbörjas utloggning:</span><span class="sxs-lookup"><span data-stu-id="4c489-119">Invoking the method with the 0 flag initiates logoff:</span></span>

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

<span data-ttu-id="4c489-120">Mer information och hitta andra funktioner i Win32Shutdown-metoden finns i "Win32Shutdown-metoden för klassen Win32_OperatingSystem" i MSDN.</span><span class="sxs-lookup"><span data-stu-id="4c489-120">For more information, and to find other features of the Win32Shutdown method, see "Win32Shutdown Method of the Win32_OperatingSystem Class" in MSDN.</span></span>

<span data-ttu-id="4c489-121">Slutligen kan du använda CIM med samma Win32_OperatingSystem-klass enligt beskrivningen ovan i WMI-metoden.</span><span class="sxs-lookup"><span data-stu-id="4c489-121">Finally you can use CIM with the same Win32_OperatingSystem class as described above in the WMI method.</span></span>

```powershell
Get-CIMInstance -Classname Win32_OperatingSystem | Invoke-CimMethod -MethodName Shutdown
```

## <a name="shutting-down-or-restarting-a-computer"></a><span data-ttu-id="4c489-122">Stänga av eller starta om en dator</span><span class="sxs-lookup"><span data-stu-id="4c489-122">Shutting Down or Restarting a Computer</span></span>

<span data-ttu-id="4c489-123">Att stänga av och starta om datorer är vanligt vis samma typer av uppgift.</span><span class="sxs-lookup"><span data-stu-id="4c489-123">Shutting down and restarting computers are generally the same types of task.</span></span> <span data-ttu-id="4c489-124">Verktyg som stänger av en dator startar normalt även om det, och vice versa.</span><span class="sxs-lookup"><span data-stu-id="4c489-124">Tools that shut down a computer will generally restart it as well—and vice versa.</span></span> <span data-ttu-id="4c489-125">Det finns två enkla alternativ för att starta om en dator från Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4c489-125">There are two straightforward options for restarting a computer from Windows PowerShell.</span></span> <span data-ttu-id="4c489-126">Använd antingen tsshutdn. exe eller Shutdown. exe med lämpliga argument.</span><span class="sxs-lookup"><span data-stu-id="4c489-126">Use either Tsshutdn.exe or Shutdown.exe with appropriate arguments.</span></span> <span data-ttu-id="4c489-127">Du kan få detaljerad användnings information från **tsshutdn. exe/?**</span><span class="sxs-lookup"><span data-stu-id="4c489-127">You can get detailed usage information from **tsshutdn.exe /?**</span></span> <span data-ttu-id="4c489-128">eller **Shutdown. exe/?** .</span><span class="sxs-lookup"><span data-stu-id="4c489-128">or **shutdown.exe /?**.</span></span>

<span data-ttu-id="4c489-129">Du kan också utföra åtgärder för avstängning och omstart direkt från Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4c489-129">You can also perform shutdown and restart operations directly from Windows PowerShell as well.</span></span>

<span data-ttu-id="4c489-130">Om du vill stänga av datorn använder du kommandot Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="4c489-130">To shut down the computer, use the Stop-Computer command</span></span>

```powershell
Stop-Computer
```

<span data-ttu-id="4c489-131">Starta om operativ systemet genom att använda kommandot Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="4c489-131">To restart the operating system, use the Restart-Computer command</span></span>

```powershell
Restart-Computer
```

<span data-ttu-id="4c489-132">Använd parametern-Force om du vill framtvinga en omedelbar omstart av datorn.</span><span class="sxs-lookup"><span data-stu-id="4c489-132">To force an immediate restart of the computer, use the -Force parameter.</span></span>

```powershell
Restart-Computer -Force
```
