---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Ändra datorstatus
ms.assetid: 8093268b-27f8-4a49-8871-142c5cc33f01
ms.openlocfilehash: c659ad54325b0f7305f882e1cb9607062abad6a4
ms.sourcegitcommit: 2ffb9fa92129c2001379ca2c17646466721f7165
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/09/2018
ms.locfileid: "35251525"
---
# <a name="changing-computer-state"></a><span data-ttu-id="24f4f-103">Ändra datorstatus</span><span class="sxs-lookup"><span data-stu-id="24f4f-103">Changing Computer State</span></span>

<span data-ttu-id="24f4f-104">Om du vill återställa en dator i Windows PowerShell använder du antingen ett kommandoradsverktyg som standard eller en WMI-klassen.</span><span class="sxs-lookup"><span data-stu-id="24f4f-104">To reset a computer in Windows PowerShell, use either a standard command-line tool or a WMI class.</span></span> <span data-ttu-id="24f4f-105">Även om du använder Windows PowerShell endast för att köra verktyget visar Lär dig att ändra en dators energisparläge i Windows PowerShell några av viktig information om hur du arbetar med externa verktyg i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24f4f-105">Although you are using Windows PowerShell only to run the tool, learning how to change a computer's power state in Windows PowerShell illustrates some of the important details about working with external tools in Windows PowerShell.</span></span>

### <a name="locking-a-computer"></a><span data-ttu-id="24f4f-106">Låsa en dator</span><span class="sxs-lookup"><span data-stu-id="24f4f-106">Locking a Computer</span></span>

<span data-ttu-id="24f4f-107">Det enda sättet att låsa en dator direkt med standard tillgängliga verktyg är att anropa den **LockWorkstation()** fungera i **user32.dll**:</span><span class="sxs-lookup"><span data-stu-id="24f4f-107">The only way to lock a computer directly with the standard available tools is to call the **LockWorkstation()** function in **user32.dll**:</span></span>

```
rundll32.exe user32.dll,LockWorkStation
```

<span data-ttu-id="24f4f-108">Det här kommandot låser omedelbart arbetsstationen.</span><span class="sxs-lookup"><span data-stu-id="24f4f-108">This command immediately locks the workstation.</span></span> <span data-ttu-id="24f4f-109">Den använder *rundll32.exe*som kör Windows-dll: er (och sparar sina bibliotek för fortlöpande användning) att köra user32.dll, ett bibliotek med funktioner för Windows.</span><span class="sxs-lookup"><span data-stu-id="24f4f-109">It uses *rundll32.exe*, which runs Windows DLLs (and saves their libraries for repeated use) to run user32.dll, a library of Windows management functions.</span></span>

<span data-ttu-id="24f4f-110">När du låsa en arbetsstation medan snabbt användarbyte är aktiverad, t.ex. på Windows XP datorn visar inloggningsskärmen användaren i stället för att starta den aktuella användaren skärmsläckaren.</span><span class="sxs-lookup"><span data-stu-id="24f4f-110">When you lock a workstation while Fast User Switching is enabled, such as on Windows XP, the computer displays the user logon screen rather than starting the current user's screensaver.</span></span>

<span data-ttu-id="24f4f-111">Om du vill stänga av viss sessioner på Terminal Server måste du använda den **tsshutdn.exe** kommandoradsverktyget.</span><span class="sxs-lookup"><span data-stu-id="24f4f-111">To shut down particular sessions on a Terminal Server, use the **tsshutdn.exe** command-line tool.</span></span>

### <a name="logging-off-the-current-session"></a><span data-ttu-id="24f4f-112">Logga ut den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="24f4f-112">Logging Off the Current Session</span></span>

<span data-ttu-id="24f4f-113">Du kan använda flera olika metoder för att logga ut från en session på det lokala systemet.</span><span class="sxs-lookup"><span data-stu-id="24f4f-113">You can use several different techniques to log off of a session on the local system.</span></span> <span data-ttu-id="24f4f-114">Det enklaste sättet är att använda kommandoradsverktyget Remote Desktop/Terminal Services **logoff.exe** (Mer information i Windows PowerShell-Kommandotolken skriver **utloggning /?**).</span><span class="sxs-lookup"><span data-stu-id="24f4f-114">The simplest way is to use the Remote Desktop/Terminal Services command-line tool, **logoff.exe** (For details, at the Windows PowerShell prompt, type **logoff /?**).</span></span> <span data-ttu-id="24f4f-115">Om du vill logga ut den aktuella aktiva sessionen, skriver **utloggning** utan argument.</span><span class="sxs-lookup"><span data-stu-id="24f4f-115">To log off the current active session, type **logoff** with no arguments.</span></span>

<span data-ttu-id="24f4f-116">Du kan också använda den **shutdown.exe** verktyget med utloggningsalternativet dess:</span><span class="sxs-lookup"><span data-stu-id="24f4f-116">You can also use the **shutdown.exe** tool with its logoff option:</span></span>

```
shutdown.exe -l
```

<span data-ttu-id="24f4f-117">Ett tredje alternativ är att använda WMI.</span><span class="sxs-lookup"><span data-stu-id="24f4f-117">A third option is to use WMI.</span></span> <span data-ttu-id="24f4f-118">Win32_OperatingSystem-klassen har en Win32Shutdown-metod.</span><span class="sxs-lookup"><span data-stu-id="24f4f-118">The Win32_OperatingSystem class has a Win32Shutdown method.</span></span> <span data-ttu-id="24f4f-119">Startar metod med flaggan 0 initierar utloggning:</span><span class="sxs-lookup"><span data-stu-id="24f4f-119">Invoking the method with the 0 flag initiates logoff:</span></span>

```powershell
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

<span data-ttu-id="24f4f-120">Mer information och andra funktioner för metoden Win32Shutdown finns ”Win32Shutdown metod för den Win32_OperatingSystem-klassen” i MSDN.</span><span class="sxs-lookup"><span data-stu-id="24f4f-120">For more information, and to find other features of the Win32Shutdown method, see "Win32Shutdown Method of the Win32_OperatingSystem Class" in MSDN.</span></span>

### <a name="shutting-down-or-restarting-a-computer"></a><span data-ttu-id="24f4f-121">Stänga av eller starta om en dator</span><span class="sxs-lookup"><span data-stu-id="24f4f-121">Shutting Down or Restarting a Computer</span></span>

<span data-ttu-id="24f4f-122">Stänga av och starta om datorer är vanligtvis samma typ av aktivitet.</span><span class="sxs-lookup"><span data-stu-id="24f4f-122">Shutting down and restarting computers are generally the same types of task.</span></span> <span data-ttu-id="24f4f-123">Verktyg som stänga av datorn normalt startar om den också, och vice versa.</span><span class="sxs-lookup"><span data-stu-id="24f4f-123">Tools that shut down a computer will generally restart it as well—and vice versa.</span></span> <span data-ttu-id="24f4f-124">Det finns två enkla alternativ för att starta om en dator från Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24f4f-124">There are two straightforward options for restarting a computer from Windows PowerShell.</span></span> <span data-ttu-id="24f4f-125">Använda Tsshutdn.exe eller Shutdown.exe med lämpliga argument.</span><span class="sxs-lookup"><span data-stu-id="24f4f-125">Use either Tsshutdn.exe or Shutdown.exe with appropriate arguments.</span></span> <span data-ttu-id="24f4f-126">Du kan få detaljerad användningsinformation från **tsshutdn.exe /?**</span><span class="sxs-lookup"><span data-stu-id="24f4f-126">You can get detailed usage information from **tsshutdn.exe /?**</span></span> <span data-ttu-id="24f4f-127">eller **shutdown.exe /?**.</span><span class="sxs-lookup"><span data-stu-id="24f4f-127">or **shutdown.exe /?**.</span></span>

<span data-ttu-id="24f4f-128">Du kan också utföra avstängning och starta om operations direkt från Windows PowerShell samt.</span><span class="sxs-lookup"><span data-stu-id="24f4f-128">You can also perform shutdown and restart operations directly from Windows PowerShell as well.</span></span>

<span data-ttu-id="24f4f-129">Använd kommandot starta om datorn för att stänga av datorn</span><span class="sxs-lookup"><span data-stu-id="24f4f-129">To shut down the computer, use the restart-computer command</span></span>

```powershell
stop-computer
```

<span data-ttu-id="24f4f-130">Om du vill starta om operativsystemet, använder du kommandot starta om datorn</span><span class="sxs-lookup"><span data-stu-id="24f4f-130">To restart the operating system, use the restart-computer command</span></span>

```powershell
restart-computer
```
