---
ms.date: 12/23/2019
keywords: PowerShell, cmdlet
title: Ändra datorstatus
ms.openlocfilehash: 9278df55ba027134a61c8ed4e89b5b839d460b29
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/08/2020
ms.locfileid: "75736921"
---
# <a name="changing-computer-state"></a><span data-ttu-id="0455e-103">Ändra datorstatus</span><span class="sxs-lookup"><span data-stu-id="0455e-103">Changing Computer State</span></span>

<span data-ttu-id="0455e-104">Om du vill återställa en dator i PowerShell använder du antingen ett standard kommando rads verktyg, WMI eller CIM-klass.</span><span class="sxs-lookup"><span data-stu-id="0455e-104">To reset a computer in PowerShell, use either a standard command-line tool, WMI or CIM class.</span></span>
<span data-ttu-id="0455e-105">Även om du bara använder PowerShell för att köra verktyget, kan du lära dig hur du ändrar datorns energi tillstånd i PowerShell. här visas några viktiga detaljer om hur du arbetar med externa verktyg i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0455e-105">Although you are using PowerShell only to run the tool, learning how to change a computer's power state in PowerShell illustrates some of the important details about working with external tools in PowerShell.</span></span>

## <a name="locking-a-computer"></a><span data-ttu-id="0455e-106">Låsa en dator</span><span class="sxs-lookup"><span data-stu-id="0455e-106">Locking a Computer</span></span>

<span data-ttu-id="0455e-107">Det enda sättet att låsa en dator direkt med de standard verktyg som är tillgängliga är att anropa funktionen **LockWorkstation ()** i **user32. dll**:</span><span class="sxs-lookup"><span data-stu-id="0455e-107">The only way to lock a computer directly with the standard available tools is to call the **LockWorkstation()** function in **user32.dll**:</span></span>

```powershell
rundll32.exe user32.dll,LockWorkStation
```

<span data-ttu-id="0455e-108">Det här kommandot låser arbets stationen omedelbart.</span><span class="sxs-lookup"><span data-stu-id="0455e-108">This command immediately locks the workstation.</span></span> <span data-ttu-id="0455e-109">Den använder **rundll32. exe**, som kör Windows-DLL-filer (och sparar bibliotek för upprepad användning) för att köra `user32.dll`, ett bibliotek med Windows Management-funktioner.</span><span class="sxs-lookup"><span data-stu-id="0455e-109">It uses **rundll32.exe**, which runs Windows DLLs (and saves their libraries for repeated use) to run `user32.dll`, a library of Windows management functions.</span></span>

<span data-ttu-id="0455e-110">När du låser en arbets Station medan snabbt användar byte är aktiverat, till exempel på Windows XP, visar datorn inloggnings skärmen för användare i stället för att starta den aktuella användarens skärmsläckare.</span><span class="sxs-lookup"><span data-stu-id="0455e-110">When you lock a workstation while Fast User Switching is enabled, such as on Windows XP, the computer displays the user logon screen rather than starting the current user's screensaver.</span></span>

<span data-ttu-id="0455e-111">Om du vill stänga av vissa sessioner på en Terminal Server använder du kommando rads verktyget **tsshutdn. exe** .</span><span class="sxs-lookup"><span data-stu-id="0455e-111">To shut down particular sessions on a Terminal Server, use the **tsshutdn.exe** command-line tool.</span></span>

## <a name="logging-off-the-current-session"></a><span data-ttu-id="0455e-112">Logga ut den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="0455e-112">Logging Off the Current Session</span></span>

<span data-ttu-id="0455e-113">Du kan använda flera olika tekniker för att logga ut från en session på det lokala systemet.</span><span class="sxs-lookup"><span data-stu-id="0455e-113">You can use several different techniques to log off of a session on the local system.</span></span> <span data-ttu-id="0455e-114">Det enklaste sättet är att använda kommando rads verktyget fjärr skrivbord/Terminal Services, **LOGOFF. exe** (mer information finns i PowerShell-prompten genom att skriva `logoff /?`).</span><span class="sxs-lookup"><span data-stu-id="0455e-114">The simplest way is to use the Remote Desktop/Terminal Services command-line tool, **logoff.exe** (For details, at the PowerShell prompt, type `logoff /?`).</span></span> <span data-ttu-id="0455e-115">Om du vill logga ut från den aktuella aktiva sessionen skriver du `logoff` utan argument.</span><span class="sxs-lookup"><span data-stu-id="0455e-115">To log off the current active session, type `logoff` with no arguments.</span></span>

<span data-ttu-id="0455e-116">Du kan också använda **Shutdown. exe** -verktyget med dess utloggnings alternativ:</span><span class="sxs-lookup"><span data-stu-id="0455e-116">You can also use the **shutdown.exe** tool with its logoff option:</span></span>

```powershell
shutdown.exe -l
```

<span data-ttu-id="0455e-117">Ett annat alternativ är att använda WMI.</span><span class="sxs-lookup"><span data-stu-id="0455e-117">Another option is to use WMI.</span></span> <span data-ttu-id="0455e-118">**Win32_OperatingSystem** -klassen har en **avslutnings** metod.</span><span class="sxs-lookup"><span data-stu-id="0455e-118">The **Win32_OperatingSystem** class has a **Shutdown** method.</span></span>
<span data-ttu-id="0455e-119">När du anropar metoden med flaggan 0 påbörjas utloggning:</span><span class="sxs-lookup"><span data-stu-id="0455e-119">Invoking the method with the 0 flag initiates logoff:</span></span>

<span data-ttu-id="0455e-120">Mer information om metoden för **avstängning** finns i [metoden shutdown i Win32_OperatingSystem-klassen](/windows/win32/cimwin32prov/shutdown-method-in-class-win32-operatingsystem)</span><span class="sxs-lookup"><span data-stu-id="0455e-120">For more information about the **Shutdown** method, see [Shutdown method of the Win32_OperatingSystem class](/windows/win32/cimwin32prov/shutdown-method-in-class-win32-operatingsystem)</span></span>

```powershell
Get-CimInstance -Classname Win32_OperatingSystem | Invoke-CimMethod -MethodName Shutdown
```

## <a name="shutting-down-or-restarting-a-computer"></a><span data-ttu-id="0455e-121">Stänga av eller starta om en dator</span><span class="sxs-lookup"><span data-stu-id="0455e-121">Shutting Down or Restarting a Computer</span></span>

<span data-ttu-id="0455e-122">Att stänga av och starta om datorer är vanligt vis samma typer av uppgift.</span><span class="sxs-lookup"><span data-stu-id="0455e-122">Shutting down and restarting computers are generally the same types of task.</span></span> <span data-ttu-id="0455e-123">Verktyg som stänger av en dator startar normalt även om det, och vice versa.</span><span class="sxs-lookup"><span data-stu-id="0455e-123">Tools that shut down a computer will generally restart it as well—and vice versa.</span></span> <span data-ttu-id="0455e-124">Det finns två enkla alternativ för att starta om en dator från PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0455e-124">There are two straightforward options for restarting a computer from PowerShell.</span></span> <span data-ttu-id="0455e-125">Använd antingen **tsshutdn. exe** eller **Shutdown. exe** med lämpliga argument.</span><span class="sxs-lookup"><span data-stu-id="0455e-125">Use either **tsshutdn.exe** or **shutdown.exe** with appropriate arguments.</span></span> <span data-ttu-id="0455e-126">Du kan få detaljerad användnings information från `tsshutdn.exe /?` eller `shutdown.exe /?`.</span><span class="sxs-lookup"><span data-stu-id="0455e-126">You can get detailed usage information from `tsshutdn.exe /?` or `shutdown.exe /?`.</span></span>

<span data-ttu-id="0455e-127">Du kan också utföra åtgärder för avstängning och omstart direkt från PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0455e-127">You can also perform shutdown and restart operations directly from PowerShell as well.</span></span>

<span data-ttu-id="0455e-128">Om du vill stänga av datorn använder du kommandot Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="0455e-128">To shut down the computer, use the Stop-Computer command</span></span>

```powershell
Stop-Computer
```

<span data-ttu-id="0455e-129">Starta om operativ systemet genom att använda kommandot Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="0455e-129">To restart the operating system, use the Restart-Computer command</span></span>

```powershell
Restart-Computer
```

<span data-ttu-id="0455e-130">Använd parametern-Force om du vill framtvinga en omedelbar omstart av datorn.</span><span class="sxs-lookup"><span data-stu-id="0455e-130">To force an immediate restart of the computer, use the -Force parameter.</span></span>

```powershell
Restart-Computer -Force
```
