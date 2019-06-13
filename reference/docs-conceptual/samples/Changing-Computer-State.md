---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Ändra datorstatus
ms.openlocfilehash: 80692ad7c56aa13e55d4997cfec289ffb3605458
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030276"
---
# <a name="changing-computer-state"></a><span data-ttu-id="2d2fe-103">Ändra datorstatus</span><span class="sxs-lookup"><span data-stu-id="2d2fe-103">Changing Computer State</span></span>

<span data-ttu-id="2d2fe-104">Om du vill återställa en dator i Windows PowerShell använder du ett kommandoradsverktyg som standard eller en WMI-klass.</span><span class="sxs-lookup"><span data-stu-id="2d2fe-104">To reset a computer in Windows PowerShell, use either a standard command-line tool or a WMI class.</span></span> <span data-ttu-id="2d2fe-105">Även om du använder Windows PowerShell endast för att köra verktyget, visar lära dig hur du ändrar energinivån för en dator i Windows PowerShell några av viktig information om hur du arbetar med externa verktyg i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2d2fe-105">Although you are using Windows PowerShell only to run the tool, learning how to change a computer's power state in Windows PowerShell illustrates some of the important details about working with external tools in Windows PowerShell.</span></span>

## <a name="locking-a-computer"></a><span data-ttu-id="2d2fe-106">Låsa en dator</span><span class="sxs-lookup"><span data-stu-id="2d2fe-106">Locking a Computer</span></span>

<span data-ttu-id="2d2fe-107">Det enda sättet att låsa en dator direkt med standardverktyg för tillgänglig är att anropa den **LockWorkstation()** fungera i **user32.dll**:</span><span class="sxs-lookup"><span data-stu-id="2d2fe-107">The only way to lock a computer directly with the standard available tools is to call the **LockWorkstation()** function in **user32.dll**:</span></span>

```
rundll32.exe user32.dll,LockWorkStation
```

<span data-ttu-id="2d2fe-108">Det här kommandot låses omedelbart arbetsstationen.</span><span class="sxs-lookup"><span data-stu-id="2d2fe-108">This command immediately locks the workstation.</span></span> <span data-ttu-id="2d2fe-109">Den använder *rundll32.exe*, som kör Windows-dll: er (och sparar sina bibliotek för upprepad användning) att köra user32.dll, ett bibliotek med Windows-hanteringsfunktioner.</span><span class="sxs-lookup"><span data-stu-id="2d2fe-109">It uses *rundll32.exe*, which runs Windows DLLs (and saves their libraries for repeated use) to run user32.dll, a library of Windows management functions.</span></span>

<span data-ttu-id="2d2fe-110">När du låsa en arbetsstation medan snabbt användarbyte är aktiverat, t.ex. på Windows XP datorn visar inloggningsskärmen för användaren i stället för att starta den aktuella användaren skärmsläckaren.</span><span class="sxs-lookup"><span data-stu-id="2d2fe-110">When you lock a workstation while Fast User Switching is enabled, such as on Windows XP, the computer displays the user logon screen rather than starting the current user's screensaver.</span></span>

<span data-ttu-id="2d2fe-111">Om du vill stänga av specifika sessioner på en Terminal Server använder den **tsshutdn.exe** kommandoradsverktyget.</span><span class="sxs-lookup"><span data-stu-id="2d2fe-111">To shut down particular sessions on a Terminal Server, use the **tsshutdn.exe** command-line tool.</span></span>

## <a name="logging-off-the-current-session"></a><span data-ttu-id="2d2fe-112">Logga ut den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="2d2fe-112">Logging Off the Current Session</span></span>

<span data-ttu-id="2d2fe-113">Du kan använda flera olika tekniker för att logga ut från en session på det lokala systemet.</span><span class="sxs-lookup"><span data-stu-id="2d2fe-113">You can use several different techniques to log off of a session on the local system.</span></span> <span data-ttu-id="2d2fe-114">Det enklaste sättet är att använda kommandoradsverktyget Remote Desktop/Terminal Services **logoff.exe** (Mer information finns i Windows PowerShell-Kommandotolken skriver du **utloggning /?** ).</span><span class="sxs-lookup"><span data-stu-id="2d2fe-114">The simplest way is to use the Remote Desktop/Terminal Services command-line tool, **logoff.exe** (For details, at the Windows PowerShell prompt, type **logoff /?**).</span></span> <span data-ttu-id="2d2fe-115">Om du vill logga ut den aktuella aktiva sessionen, skriver **utloggning** utan argument.</span><span class="sxs-lookup"><span data-stu-id="2d2fe-115">To log off the current active session, type **logoff** with no arguments.</span></span>

<span data-ttu-id="2d2fe-116">Du kan också använda den **shutdown.exe** verktyget med utloggningsalternativet dess:</span><span class="sxs-lookup"><span data-stu-id="2d2fe-116">You can also use the **shutdown.exe** tool with its logoff option:</span></span>

```
shutdown.exe -l
```

<span data-ttu-id="2d2fe-117">Ett tredje alternativ är att använda WMI.</span><span class="sxs-lookup"><span data-stu-id="2d2fe-117">A third option is to use WMI.</span></span> <span data-ttu-id="2d2fe-118">Win32_OperatingSystem-klassen har en Win32Shutdown-metod.</span><span class="sxs-lookup"><span data-stu-id="2d2fe-118">The Win32_OperatingSystem class has a Win32Shutdown method.</span></span> <span data-ttu-id="2d2fe-119">Anropa metoden med flaggan 0 initierar utloggning:</span><span class="sxs-lookup"><span data-stu-id="2d2fe-119">Invoking the method with the 0 flag initiates logoff:</span></span>

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

<span data-ttu-id="2d2fe-120">Mer information och hitta andra funktioner i metoden Win32Shutdown finns ”Win32Shutdown metoden av the Win32_OperatingSystem-klassen” i MSDN.</span><span class="sxs-lookup"><span data-stu-id="2d2fe-120">For more information, and to find other features of the Win32Shutdown method, see "Win32Shutdown Method of the Win32_OperatingSystem Class" in MSDN.</span></span>

## <a name="shutting-down-or-restarting-a-computer"></a><span data-ttu-id="2d2fe-121">Stänga av eller starta om en dator</span><span class="sxs-lookup"><span data-stu-id="2d2fe-121">Shutting Down or Restarting a Computer</span></span>

<span data-ttu-id="2d2fe-122">Stänga av och starta om datorer är vanligtvis samma typ av uppgift.</span><span class="sxs-lookup"><span data-stu-id="2d2fe-122">Shutting down and restarting computers are generally the same types of task.</span></span> <span data-ttu-id="2d2fe-123">Verktyg som stänga av datorn Allmänt startar om den också, och vice versa.</span><span class="sxs-lookup"><span data-stu-id="2d2fe-123">Tools that shut down a computer will generally restart it as well—and vice versa.</span></span> <span data-ttu-id="2d2fe-124">Det finns två enkla alternativ för att starta om en dator från Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2d2fe-124">There are two straightforward options for restarting a computer from Windows PowerShell.</span></span> <span data-ttu-id="2d2fe-125">Använd Tsshutdn.exe eller Shutdown.exe med rätt argument.</span><span class="sxs-lookup"><span data-stu-id="2d2fe-125">Use either Tsshutdn.exe or Shutdown.exe with appropriate arguments.</span></span> <span data-ttu-id="2d2fe-126">Du kan få detaljerad användningsinformation från **tsshutdn.exe /?**</span><span class="sxs-lookup"><span data-stu-id="2d2fe-126">You can get detailed usage information from **tsshutdn.exe /?**</span></span> <span data-ttu-id="2d2fe-127">eller **shutdown.exe /?** .</span><span class="sxs-lookup"><span data-stu-id="2d2fe-127">or **shutdown.exe /?**.</span></span>

<span data-ttu-id="2d2fe-128">Du kan också utföra avstängning och starta om åtgärder direkt från Windows PowerShell samt.</span><span class="sxs-lookup"><span data-stu-id="2d2fe-128">You can also perform shutdown and restart operations directly from Windows PowerShell as well.</span></span>

<span data-ttu-id="2d2fe-129">Om du vill stänga av datorn, använder du kommandot Stop-Computer</span><span class="sxs-lookup"><span data-stu-id="2d2fe-129">To shut down the computer, use the Stop-Computer command</span></span>

```powershell
Stop-Computer
```

<span data-ttu-id="2d2fe-130">Om du vill starta om operativsystemet, använder du kommandot Restart-Computer</span><span class="sxs-lookup"><span data-stu-id="2d2fe-130">To restart the operating system, use the Restart-Computer command</span></span>

```powershell
Restart-Computer
```

<span data-ttu-id="2d2fe-131">Om du vill framtvinga en omedelbar omstart av datorn, Använd parametern - Force.</span><span class="sxs-lookup"><span data-stu-id="2d2fe-131">To force an immediate restart of the computer, use the -Force parameter.</span></span>

```powershell
Restart-Computer -Force
```
