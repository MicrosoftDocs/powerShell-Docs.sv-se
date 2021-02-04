---
title: Komma igång med PowerShell
description: Var du hittar och hur du startar PowerShell för nya användare.
ms.date: 06/02/2020
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: 8b9fee222347970df4e35f9ba0841232952a292d
ms.sourcegitcommit: df5e6f032ee2d4b556d50406832732d2f7dc2502
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98216181"
---
# <a name="chapter-1---getting-started-with-powershell"></a><span data-ttu-id="776e6-103">Kapitel 1 – Komma igång med PowerShell</span><span class="sxs-lookup"><span data-stu-id="776e6-103">Chapter 1 - Getting Started with PowerShell</span></span>

<span data-ttu-id="776e6-104">Jag upptäcker ofta att presentatörer på konferenser och användar grupps möten redan har PowerShell igång när de startar ingångs nivå presentationer.</span><span class="sxs-lookup"><span data-stu-id="776e6-104">I often find that presenters at conferences and user group meetings already have PowerShell running when they start entry-level presentations.</span></span> <span data-ttu-id="776e6-105">Den här boken börjar genom att besvara frågorna som jag har hört deltagare som inte tidigare har använt PowerShell fråga i dessa sessioner.</span><span class="sxs-lookup"><span data-stu-id="776e6-105">This book begins by answering the questions I've heard attendees who haven't previously used PowerShell ask in those sessions.</span></span>

<span data-ttu-id="776e6-106">I detta kapitel fokuserar vi på att söka efter och starta PowerShell och lösa några av de inledande problemen som nya användare upplever med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="776e6-106">Specifically, this chapter focuses on finding and launching PowerShell, and solving some of the initial pain points that new users experience with PowerShell.</span></span> <span data-ttu-id="776e6-107">Se till att följa med och gå igenom exemplen som visas i det här kapitlet på Windows 10 labb miljö datorn.</span><span class="sxs-lookup"><span data-stu-id="776e6-107">Be sure to follow along and walk through the examples shown in this chapter on your Windows 10 lab environment computer.</span></span>

## <a name="what-do-i-need-to-get-started-with-powershell"></a><span data-ttu-id="776e6-108">Vad behöver jag för att komma igång med PowerShell?</span><span class="sxs-lookup"><span data-stu-id="776e6-108">What do I need to get started with PowerShell?</span></span>

<span data-ttu-id="776e6-109">Alla moderna versioner av Windows-operativsystem levereras med PowerShell installerat.</span><span class="sxs-lookup"><span data-stu-id="776e6-109">All modern versions of Windows operating systems ship with PowerShell installed.</span></span> <span data-ttu-id="776e6-110">Om du kör en version som är äldre än 5,1 bör du installera den senaste versionen.</span><span class="sxs-lookup"><span data-stu-id="776e6-110">If you're running a version older than 5.1, you should install the latest version.</span></span>

- <span data-ttu-id="776e6-111">Information om hur du uppgraderar till Windows PowerShell 5,1 finns i [uppgradera befintliga Windows PowerShell][]</span><span class="sxs-lookup"><span data-stu-id="776e6-111">To upgrade to Windows PowerShell 5.1, see [Upgrading existing Windows PowerShell][]</span></span>
- <span data-ttu-id="776e6-112">Information om hur du installerar den senaste versionen av PowerShell finns i [Installera PowerShell][]</span><span class="sxs-lookup"><span data-stu-id="776e6-112">To install the latest version of PowerShell, see [Installing PowerShell][]</span></span>

## <a name="where-do-i-find-powershell"></a><span data-ttu-id="776e6-113">Var hittar jag PowerShell?</span><span class="sxs-lookup"><span data-stu-id="776e6-113">Where do I find PowerShell?</span></span>

<span data-ttu-id="776e6-114">Det enklaste sättet att hitta PowerShell i Windows 10 är att skriva **PowerShell** i Sök fältet som visas i bild 1-1.</span><span class="sxs-lookup"><span data-stu-id="776e6-114">The easiest way to find PowerShell on Windows 10 is to type **PowerShell** into the search bar as shown in Figure 1-1.</span></span>

![Bild 1-1 – Sök efter PowerShell på Start menyn](media/figure1-1.png)

<span data-ttu-id="776e6-116">Observera att fyra olika kortkommandon för PowerShell visas i bild 1-1.</span><span class="sxs-lookup"><span data-stu-id="776e6-116">Notice that four different shortcuts for PowerShell are shown in Figure 1-1.</span></span> <span data-ttu-id="776e6-117">Datorn som används i demonstrations syfte i den här boken kör 64-bitars versionen av Windows 10, så det finns en 64-bitars version av PowerShell-konsolen och PowerShell ISE (Integrated Scripting Environment) och en 32-bitars version av var och en som anges av (x86)-suffixet i gen vägarna.</span><span class="sxs-lookup"><span data-stu-id="776e6-117">The computer used for demonstration purposes in this book is running the 64-bit version of Windows 10 so there's a 64-bit version of the PowerShell console and the PowerShell ISE (Integrated Scripting Environment), and a 32-bit version of each one as denoted by the (x86) suffix on the shortcuts.</span></span> <span data-ttu-id="776e6-118">Om du råkar köra en 32-bitars version av Windows 10 har du bara två genvägar.</span><span class="sxs-lookup"><span data-stu-id="776e6-118">If you happen to be running a 32-bit version of Windows 10, you'll only have two shortcuts.</span></span> <span data-ttu-id="776e6-119">Dessa objekt har inte (x86) suffix, men är 32-bitars versioner.</span><span class="sxs-lookup"><span data-stu-id="776e6-119">Those items don't have the (x86) suffix, but are 32-bit versions.</span></span> <span data-ttu-id="776e6-120">Om du har ett 64-bitars operativ system är min rekommendation att köra 64-bitars versionen av PowerShell, om du inte har en unik orsak för att köra 32-bitars versionen.</span><span class="sxs-lookup"><span data-stu-id="776e6-120">If you have a 64-bit operating system, my recommendation is to run the 64-bit version of PowerShell unless you have a specific reason for running the 32-bit version.</span></span>

<span data-ttu-id="776e6-121">Information om hur du startar PowerShell i andra versioner av Windows finns i [Starta Windows PowerShell][].</span><span class="sxs-lookup"><span data-stu-id="776e6-121">For information about starting PowerShell on other versions of Windows, see [Starting Windows PowerShell][].</span></span>

## <a name="how-do-i-launch-powershell"></a><span data-ttu-id="776e6-122">Hur gör jag för att starta PowerShell?</span><span class="sxs-lookup"><span data-stu-id="776e6-122">How do I launch PowerShell?</span></span>

<span data-ttu-id="776e6-123">I produktions företags miljöer som jag stöder använder jag tre olika Active Directory-användarkonton.</span><span class="sxs-lookup"><span data-stu-id="776e6-123">In the production enterprise environments that I support, I use three different Active Directory user accounts.</span></span> <span data-ttu-id="776e6-124">Jag har speglat dessa konton i labb miljön som används i den här boken.</span><span class="sxs-lookup"><span data-stu-id="776e6-124">I've mirrored those accounts in the lab environment used in this book.</span></span> <span data-ttu-id="776e6-125">Jag loggar in på Windows 10-datorn som en domän användare som inte är en domän eller lokal administratör.</span><span class="sxs-lookup"><span data-stu-id="776e6-125">I log into the Windows 10 computer as a domain user who is not a domain or local administrator.</span></span>

<span data-ttu-id="776e6-126">Jag har lanserat PowerShell-konsolen genom att klicka på genvägen "Windows PowerShell" som visas i bild 1-1.</span><span class="sxs-lookup"><span data-stu-id="776e6-126">I've launched the PowerShell console by clicking on the "Windows PowerShell" shortcut as shown in Figure 1-1.</span></span>

![Bild 1-4 – namn listen i PowerShell-fönstret](media/figure1-4.png)

<span data-ttu-id="776e6-128">Observera att PowerShell-konsolens namn List säger "Windows PowerShell" som visas i bild 1-4.</span><span class="sxs-lookup"><span data-stu-id="776e6-128">Notice that the title bar of the PowerShell console says "Windows PowerShell" as shown in Figure 1-4.</span></span> <span data-ttu-id="776e6-129">Vissa kommandon fungerar bra, men PowerShell kan inte delta i användar Access Control (UAC).</span><span class="sxs-lookup"><span data-stu-id="776e6-129">Some commands run fine, but PowerShell can't participate in User Access Control (UAC).</span></span> <span data-ttu-id="776e6-130">Det innebär att det inte går att fråga efter utökad behörighet för uppgifter som kräver godkännande av en administratör.</span><span class="sxs-lookup"><span data-stu-id="776e6-130">That means it's unable to prompt for elevation for tasks that require the approval of an administrator.</span></span>
<span data-ttu-id="776e6-131">Följande fel meddelande genereras:</span><span class="sxs-lookup"><span data-stu-id="776e6-131">The following error message is generated:</span></span>

```powershell
Get-Service -Name W32Time | Stop-Service
```

```Output
Stop-Service : Service 'Windows Time (W32Time)' cannot be stopped due to the following
error: Cannot open W32Time service on computer '.'.
At line:1 char:29
+ Get-Service -Name W32Time | Stop-Service
+
    + CategoryInfo          : CloseError: (System.ServiceProcess.ServiceController:ServiceController)
     [Stop-Service], ServiceCommandException
    + FullyQualifiedErrorId : CouldNotStopService,Microsoft.PowerShell.Commands.StopServiceCommand
```

<span data-ttu-id="776e6-132">Lösningen på det här problemet är att köra PowerShell som en domän användare som är en lokal administratör.</span><span class="sxs-lookup"><span data-stu-id="776e6-132">The solution to this problem is to run PowerShell as a domain user who is a local administrator.</span></span>
<span data-ttu-id="776e6-133">Så här konfigureras mitt andra domän användar konto.</span><span class="sxs-lookup"><span data-stu-id="776e6-133">This is how my second domain user account is configured.</span></span> <span data-ttu-id="776e6-134">Det här kontot bör inte vara en domän administratör eller ha utökade privilegier i domänen.</span><span class="sxs-lookup"><span data-stu-id="776e6-134">Using the principal of least privilege, this account should NOT be a domain administrator, or have any elevated privileges in the domain.</span></span>

<span data-ttu-id="776e6-135">Stäng PowerShell.</span><span class="sxs-lookup"><span data-stu-id="776e6-135">Close PowerShell.</span></span> <span data-ttu-id="776e6-136">Starta om PowerShell-konsolen, förutom den här gången, högerklicka på genvägen **Windows PowerShell** och välj **Kör som administratör** enligt bilden 1-5.</span><span class="sxs-lookup"><span data-stu-id="776e6-136">Relaunch the PowerShell console, except this time right-click on the **Windows PowerShell** shortcut and select **Run as administrator** as shown in Figure 1-5.</span></span>

![Bild 1-5 – snabb meny – kör som administratör](media/figure1-5.png)

<span data-ttu-id="776e6-138">Om du är inloggad på Windows som en vanlig användare uppmanas du att ange autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="776e6-138">If you're logged into Windows as a normal user, you'll be prompted for credentials.</span></span> <span data-ttu-id="776e6-139">Jag anger autentiseringsuppgifterna för mitt användar konto som är domän användare och lokal administratör enligt bild 1-6.</span><span class="sxs-lookup"><span data-stu-id="776e6-139">I'll enter the credentials for my user account who is a domain user and local admin as shown in Figure 1-6.</span></span>

![Figur 1-6](media/figure1-6.png)

<span data-ttu-id="776e6-141">När PowerShell startas om som administratör ska namn listen stå "administratör: Windows PowerShell" som visas i bild 1-7.</span><span class="sxs-lookup"><span data-stu-id="776e6-141">Once PowerShell is relaunched as an administrator, the title bar should say "Administrator: Windows PowerShell" as shown in Figure 1-7.</span></span>

![Figur 1-7](media/figure1-7.png)

<span data-ttu-id="776e6-143">Nu när PowerShell körs upphöjt till en lokal administratör kommer UAC inte längre att vara ett problem när ett kommando körs på den lokala datorn som normalt skulle kräva en uppmaning om utökade privilegier.</span><span class="sxs-lookup"><span data-stu-id="776e6-143">Now that PowerShell is being run elevated as a local administrator, UAC will no longer be a problem when a command is run on the local computer that would normally require a prompt for elevation.</span></span> <span data-ttu-id="776e6-144">Tänk på att alla kommandon som körs från den här upphöjda instansen av PowerShell-konsolen också körs med förhöjd behörighet.</span><span class="sxs-lookup"><span data-stu-id="776e6-144">Keep in mind though that any command run from this elevated instance of the PowerShell console, also runs elevated.</span></span>

<span data-ttu-id="776e6-145">För att förenkla sökning av PowerShell och starta den som administratör rekommenderar vi att du fäster den i aktivitets fältet och ställer in den så att den startar automatiskt som en administratör varje gången den körs.</span><span class="sxs-lookup"><span data-stu-id="776e6-145">To simplify finding PowerShell and launching it as an administrator, I recommend pinning it to the taskbar and setting it to automatically launch as an admin each time it's run.</span></span>

<span data-ttu-id="776e6-146">Sök efter PowerShell igen, förutom den här gången högerklickar du på den och väljer Fäst på aktivitets fältet som visas i bild 1-8.</span><span class="sxs-lookup"><span data-stu-id="776e6-146">Search for PowerShell again, except this time right-click on it and select "Pin to taskbar" as shown in Figure 1-8.</span></span>

![Figur 1-8](media/figure1-8.png)

<span data-ttu-id="776e6-148">Högerklicka på PowerShell-genvägen som nu har fästs i aktivitets fältet och välj egenskaper som visas i bild 1-9.</span><span class="sxs-lookup"><span data-stu-id="776e6-148">Right-click on the PowerShell shortcut that's now pinned to the taskbar and select properties as shown in Figure 1-9.</span></span>

![Figur 1-9-kontroll av användar konto – ange autentiseringsuppgifter](media/figure1-9.png)

<span data-ttu-id="776e6-150">Klicka på "Avancerat" som antecknas genom att #1 i bild 1-10, markera kryss rutan Kör som administratör som betecknas genom att #2 i bild 1-10 och klicka sedan på OK två gånger för att acceptera ändringarna och avsluta från båda dialog rutorna.</span><span class="sxs-lookup"><span data-stu-id="776e6-150">Click on "Advanced" as denoted by #1 in Figure 1-10, then check the "Run as administrator" checkbox as denoted by #2 in Figure 1-10, and then click OK twice to accept the changes and exit out of both dialog boxes.</span></span>

![Figur 1-10 – namn listen visar "administratör"](media/figure1-10.png)

<span data-ttu-id="776e6-152">Du behöver aldrig bekymra dig om att hitta PowerShell eller om den körs som administratör igen.</span><span class="sxs-lookup"><span data-stu-id="776e6-152">You'll never have to worry about finding PowerShell or whether or not it's running as an administrator again.</span></span>

<span data-ttu-id="776e6-153">Att köra PowerShell som administratör för att förhindra problem med UAC påverkar bara kommandon som körs mot den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="776e6-153">Running PowerShell elevated as an administrator to prevent having problems with UAC only impacts commands that are run against the local computer.</span></span> <span data-ttu-id="776e6-154">Den har ingen påverkan på kommandon som är riktade till fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="776e6-154">It has no effect on commands that target remote computers.</span></span>

## <a name="what-version-of-powershell-am-i-running"></a><span data-ttu-id="776e6-155">Vilken version av PowerShell körs?</span><span class="sxs-lookup"><span data-stu-id="776e6-155">What version of PowerShell am I running?</span></span>

<span data-ttu-id="776e6-156">Det finns ett antal automatiska variabler i PowerShell som lagrar statusinformation.</span><span class="sxs-lookup"><span data-stu-id="776e6-156">There are a number of automatic variables in PowerShell that store state information.</span></span> <span data-ttu-id="776e6-157">En av dessa variabler är `$PSVersionTable` , som innehåller en hash-modul som kan användas för att visa relevant information om PowerShell-version:</span><span class="sxs-lookup"><span data-stu-id="776e6-157">One of these variables is `$PSVersionTable`, which contains a hashtable that can be used to display the relevant PowerShell version information:</span></span>

```powershell
$PSVersionTable
```

```Output
Name                           Value
----                           -----
PSVersion                      5.1.19041.1
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
BuildVersion                   10.0.19041.1
CLRVersion                     4.0.30319.42000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

<span data-ttu-id="776e6-158">Nyare versioner av Windows PowerShell distribueras som en del av Windows Management Framework (WMF).</span><span class="sxs-lookup"><span data-stu-id="776e6-158">Newer versions of Windows PowerShell are distributed as part of the Windows Management Framework (WMF).</span></span> <span data-ttu-id="776e6-159">En angiven version av .NET Framework krävs beroende på WMF-versionen.</span><span class="sxs-lookup"><span data-stu-id="776e6-159">A specific version of the .NET Framework is required depending on the WMF version.</span></span> <span data-ttu-id="776e6-160">Information om hur du uppgraderar till Windows PowerShell 5,1 finns i [uppgradera befintliga Windows PowerShell][].</span><span class="sxs-lookup"><span data-stu-id="776e6-160">To upgrade to Windows PowerShell 5.1, see [Upgrading existing Windows PowerShell][].</span></span>

## <a name="execution-policy"></a><span data-ttu-id="776e6-161">Körnings princip</span><span class="sxs-lookup"><span data-stu-id="776e6-161">Execution Policy</span></span>

<span data-ttu-id="776e6-162">Till skillnad från populär tro är körnings principen i PowerShell inte en säkerhets gränser.</span><span class="sxs-lookup"><span data-stu-id="776e6-162">Contrary to popular belief, the execution policy in PowerShell is not a security boundary.</span></span> <span data-ttu-id="776e6-163">Den är utformad för att hindra en användare från att känna sig osäker på att köra ett skript.</span><span class="sxs-lookup"><span data-stu-id="776e6-163">It's designed to prevent a user from unknowingly running a script.</span></span> <span data-ttu-id="776e6-164">En bestämd användare kan enkelt kringgå körnings principen i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="776e6-164">A determined user can easily bypass the execution policy in PowerShell.</span></span> <span data-ttu-id="776e6-165">Tabell 1-2 visar standard körnings principen för aktuella Windows-operativsystem.</span><span class="sxs-lookup"><span data-stu-id="776e6-165">Table 1-2 shows the default execution policy for current Windows operating systems.</span></span>

| <span data-ttu-id="776e6-166">Operativ system version för Windows</span><span class="sxs-lookup"><span data-stu-id="776e6-166">Windows Operating System Version</span></span> | <span data-ttu-id="776e6-167">Standard körnings princip</span><span class="sxs-lookup"><span data-stu-id="776e6-167">Default Execution Policy</span></span> |
| -------------------------------- | ------------------------ |
| <span data-ttu-id="776e6-168">Server 2019</span><span class="sxs-lookup"><span data-stu-id="776e6-168">Server 2019</span></span>                      | <span data-ttu-id="776e6-169">Fjärran sluten signerad</span><span class="sxs-lookup"><span data-stu-id="776e6-169">Remote Signed</span></span>            |
| <span data-ttu-id="776e6-170">Server 2016</span><span class="sxs-lookup"><span data-stu-id="776e6-170">Server 2016</span></span>                      | <span data-ttu-id="776e6-171">Fjärran sluten signerad</span><span class="sxs-lookup"><span data-stu-id="776e6-171">Remote Signed</span></span>            |
| <span data-ttu-id="776e6-172">Windows 10</span><span class="sxs-lookup"><span data-stu-id="776e6-172">Windows 10</span></span>                       | <span data-ttu-id="776e6-173">Begränsade</span><span class="sxs-lookup"><span data-stu-id="776e6-173">Restricted</span></span>               |

<span data-ttu-id="776e6-174">Oavsett inställningen för körnings principen kan alla PowerShell-kommandon köras interaktivt.</span><span class="sxs-lookup"><span data-stu-id="776e6-174">Regardless of the execution policy setting, any PowerShell command can be run interactively.</span></span> <span data-ttu-id="776e6-175">Körnings principen påverkar bara kommandon som körs i ett skript.</span><span class="sxs-lookup"><span data-stu-id="776e6-175">The execution policy only affects commands running in a script.</span></span> <span data-ttu-id="776e6-176">`Get-ExecutionPolicy`Cmdleten används för att avgöra vad den aktuella körnings princip inställningen är och att `Set-ExecutionPolicy` cmdleten används för att ändra körnings principen.</span><span class="sxs-lookup"><span data-stu-id="776e6-176">The `Get-ExecutionPolicy` cmdlet is used to determine what the current execution policy setting is and the `Set-ExecutionPolicy` cmdlet is used to change the execution policy.</span></span> <span data-ttu-id="776e6-177">Min rekommendation är att använda **RemoteSigned** -principen, som kräver att hämtade skript signeras av en betrodd utgivare för att kunna köras.</span><span class="sxs-lookup"><span data-stu-id="776e6-177">My recommendation is to use the **RemoteSigned** policy, which requires downloaded scripts to be signed by a trusted publisher in order to be run.</span></span>

<span data-ttu-id="776e6-178">Kontrol lera den aktuella körnings principen:</span><span class="sxs-lookup"><span data-stu-id="776e6-178">Check the current execution policy:</span></span>

```powershell
Get-ExecutionPolicy
```

```Output
Restricted
```

<span data-ttu-id="776e6-179">PowerShell-skript kan inte köras alls när körnings principen är inställd på **begränsad**.</span><span class="sxs-lookup"><span data-stu-id="776e6-179">PowerShell scripts can't be run at all when the execution policy is set to **Restricted**.</span></span> <span data-ttu-id="776e6-180">Detta är standardinställningen på alla Windows-klientens operativ system.</span><span class="sxs-lookup"><span data-stu-id="776e6-180">This is the default setting on all Windows client operating systems.</span></span> <span data-ttu-id="776e6-181">För att demonstrera problemet sparar du följande kod som en `.ps1` fil med namnet `Stop-TimeService.ps1` .</span><span class="sxs-lookup"><span data-stu-id="776e6-181">To demonstrate the problem, save the following code as a `.ps1` file named `Stop-TimeService.ps1`.</span></span>

```powershell
Get-Service -Name W32Time | Stop-Service -PassThru
```

<span data-ttu-id="776e6-182">Kommandot körs interaktivt utan fel så länge PowerShell körs upphöjt till en administratör.</span><span class="sxs-lookup"><span data-stu-id="776e6-182">That command runs interactively without error as long as PowerShell is run elevated as an administrator.</span></span> <span data-ttu-id="776e6-183">Men så snart det sparas som en skript fil och du försöker köra skriptet, genererar det ett fel:</span><span class="sxs-lookup"><span data-stu-id="776e6-183">But as soon as it's saved as a script file and you try to execute the script, it generates an error:</span></span>

```powershell
.\Stop-TimeService.ps1
```

```Output
.\Stop-TimeService.ps1 : File C:\demo\Stop-TimeService.ps1 cannot be loaded because
running scripts is disabled on this system. For more information, see
about_Execution_Policies at http://go.microsoft.com/fwlink/?LinkID=135170.
At line:1 char:1
+ .\Stop-TimeService.ps1
+
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
```

<span data-ttu-id="776e6-184">Observera att det fel som visas i den föregående uppsättningen resultat visar exakt vad problemet är (körning av skript är inaktiverat i systemet).</span><span class="sxs-lookup"><span data-stu-id="776e6-184">Notice that the error shown in the previous set of results tells you exactly what the problem is (running scripts is disabled on this system).</span></span> <span data-ttu-id="776e6-185">När du kör ett kommando i PowerShell som genererar ett fel meddelande, bör du läsa fel meddelandet i stället för att bara köra kommandot och lura som körs.</span><span class="sxs-lookup"><span data-stu-id="776e6-185">When you run a command in PowerShell that generates an error message, be sure to read the error message instead of just rerunning the command and hoping that it runs successfully.</span></span>

<span data-ttu-id="776e6-186">Ändra PowerShell-körnings principen till fjärran sluten signerad.</span><span class="sxs-lookup"><span data-stu-id="776e6-186">Change the PowerShell execution policy to remote signed.</span></span>

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned
```

```Output
Execution Policy Change
The execution policy helps protect you from scripts that you do not trust. Changing the execution
policy might expose you to the security risks described in the about_Execution_Policies help topic
at http://go.microsoft.com/fwlink/?LinkID=135170. Do you want to change the execution policy?
[Y] Yes [A] Yes to All [N] No [L] No to All [S] Suspend [?] Help (default is "N"):y
```

<span data-ttu-id="776e6-187">Se till att läsa varningen som visas när du ändrar körnings principen.</span><span class="sxs-lookup"><span data-stu-id="776e6-187">Be sure to read the warning that's displayed when changing the execution policy.</span></span> <span data-ttu-id="776e6-188">Jag rekommenderar också att ta en titt på [about_Execution_Policies][] hjälp avsnittet och se till att du förstår säkerhets konsekvenserna av att ändra körnings principen.</span><span class="sxs-lookup"><span data-stu-id="776e6-188">I also recommend taking a look at the [about_Execution_Policies][] help topic to make sure you understand the security implications of changing the execution policy.</span></span>

<span data-ttu-id="776e6-189">Nu när körnings principen har ställts in på **RemoteSigned** `Stop-TimeService.ps1` Kör skriptet fel kostnads fritt.</span><span class="sxs-lookup"><span data-stu-id="776e6-189">Now that the execution policy has been set to **RemoteSigned**, the `Stop-TimeService.ps1` script runs error free.</span></span>

```powershell
.\Stop-TimeService.ps1
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  W32Time            Windows Time
```

<span data-ttu-id="776e6-190">Se till att starta tids tjänsten för Windows innan du fortsätter annars kan du stöta på oförutsedda problem.</span><span class="sxs-lookup"><span data-stu-id="776e6-190">Be sure to start your Windows Time service before continuing otherwise you may run into unforeseen problems.</span></span>

```powershell
Start-Service -Name w32time
```

## <a name="summary"></a><span data-ttu-id="776e6-191">Sammanfattning</span><span class="sxs-lookup"><span data-stu-id="776e6-191">Summary</span></span>

<span data-ttu-id="776e6-192">I det här kapitlet har du lärt dig hur du hittar och startar PowerShell och hur du skapar en genväg som startar PowerShell som administratör.</span><span class="sxs-lookup"><span data-stu-id="776e6-192">In this chapter, you've learned how to find and launch PowerShell, and how to create a shortcut that launches PowerShell as an administrator.</span></span> <span data-ttu-id="776e6-193">Du har också lärt dig om standard körnings principen och hur du ändrar den.</span><span class="sxs-lookup"><span data-stu-id="776e6-193">You've also learned about the default execution policy and how to change it.</span></span>

## <a name="review"></a><span data-ttu-id="776e6-194">Genomgång</span><span class="sxs-lookup"><span data-stu-id="776e6-194">Review</span></span>

1. <span data-ttu-id="776e6-195">Hur tar du reda på vilken PowerShell-version en dator kör?</span><span class="sxs-lookup"><span data-stu-id="776e6-195">How do you determine what PowerShell version a computer is running?</span></span>
1. <span data-ttu-id="776e6-196">Varför är det viktigt att starta PowerShell som administratör?</span><span class="sxs-lookup"><span data-stu-id="776e6-196">Why is it important to launch PowerShell elevated as an administrator?</span></span>
1. <span data-ttu-id="776e6-197">Hur avgör du den aktuella PowerShell-körnings principen?</span><span class="sxs-lookup"><span data-stu-id="776e6-197">How do you determine the current PowerShell execution policy?</span></span>
1. <span data-ttu-id="776e6-198">Vad hindrar standard körnings principen för PowerShell på Windows-klientdatorer från att ske?</span><span class="sxs-lookup"><span data-stu-id="776e6-198">What does the default PowerShell execution policy on Windows client computers prevent from occurring?</span></span>
1. <span data-ttu-id="776e6-199">Hur ändrar du körnings principen för PowerShell?</span><span class="sxs-lookup"><span data-stu-id="776e6-199">How do you change the PowerShell execution policy?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="776e6-200">Rekommenderad läsning</span><span class="sxs-lookup"><span data-stu-id="776e6-200">Recommended Reading</span></span>

<span data-ttu-id="776e6-201">För dem som vill veta mer om de ämnen som beskrivs i det här kapitlet rekommenderar vi att du läser följande PowerShell-hjälp avsnitt.</span><span class="sxs-lookup"><span data-stu-id="776e6-201">For those who want to know more information about the topics covered in this chapter, I recommend reading the following PowerShell help topics.</span></span>

- <span data-ttu-id="776e6-202">[about_Automatic_Variables][]</span><span class="sxs-lookup"><span data-stu-id="776e6-202">[about_Automatic_Variables][]</span></span>
- <span data-ttu-id="776e6-203">[about_Hash_Tables][]</span><span class="sxs-lookup"><span data-stu-id="776e6-203">[about_Hash_Tables][]</span></span>
- <span data-ttu-id="776e6-204">[about_Execution_Policies][]</span><span class="sxs-lookup"><span data-stu-id="776e6-204">[about_Execution_Policies][]</span></span>

<span data-ttu-id="776e6-205">I nästa kapitel får du lära dig mer om hur du kan hitta kommandon i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="776e6-205">In the next chapter, you'll learn about the discoverability of commands in PowerShell.</span></span> <span data-ttu-id="776e6-206">Ett av de saker som kommer att omfattas är hur du uppdaterar PowerShell så att hjälp avsnitten kan visas direkt från PowerShell i stället för att behöva visa dem på Internet.</span><span class="sxs-lookup"><span data-stu-id="776e6-206">One of the things that will be covered is how to update PowerShell so those help topics can be viewed right from within PowerShell instead of having to view them on the internet.</span></span>

<!-- link references -->
[about_Automatic_Variables]: /powershell/module/microsoft.powershell.core/about/about_automatic_variables
[about_Hash_Tables]: /powershell/module/microsoft.powershell.core/about/about_hash_tables
[about_Execution_Policies]: /powershell/module/microsoft.powershell.core/about/about_execution_policies
[Uppgradera befintliga Windows PowerShell]: /powershell/scripting/windows-powershell/install/installing-windows-powershell#upgrading-existing-windows-powershell
[Upgrading existing Windows PowerShell]: /powershell/scripting/windows-powershell/install/installing-windows-powershell#upgrading-existing-windows-powershell
[Installera PowerShell]: /powershell/scripting/install/installing-powershell
[Installing PowerShell]: /powershell/scripting/install/installing-powershell
[Starta Windows Powershell]: /powershell/scripting/windows-powershell/starting-windows-powershell
[Starting Windows PowerShell]: /powershell/scripting/windows-powershell/starting-windows-powershell
