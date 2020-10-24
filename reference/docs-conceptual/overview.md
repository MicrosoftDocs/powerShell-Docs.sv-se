---
ms.date: 05/22/2020
keywords: powershell,cmdlet
title: Vad är PowerShell?
description: Den här artikeln är en introduktion till PowerShell-skript miljön och dess funktioner.
ms.openlocfilehash: 91fc580af9a3adf43a24c40b4aaf3f1843882705
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500784"
---
# <a name="what-is-powershell"></a><span data-ttu-id="f00ee-104">Vad är PowerShell?</span><span class="sxs-lookup"><span data-stu-id="f00ee-104">What is PowerShell?</span></span>

<span data-ttu-id="f00ee-105">PowerShell är en plattforms oberoende uppgift för automatisering och konfigurations hanterings ramverk, som består av ett kommando rads gränssnitt och skript språk.</span><span class="sxs-lookup"><span data-stu-id="f00ee-105">PowerShell is a cross-platform task automation and configuration management framework, consisting of a command-line shell and scripting language.</span></span> <span data-ttu-id="f00ee-106">Till skillnad från de flesta Shell, som godkänner och returnerar text, bygger PowerShell på CLR (Common Language Runtime) för .NET och godkänner och returnerar .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="f00ee-106">Unlike most shells, which accept and return text, PowerShell is built on top of the .NET Common Language Runtime (CLR), and accepts and returns .NET objects.</span></span> <span data-ttu-id="f00ee-107">Den här grundläggande ändringen ger helt nya verktyg och metoder för automatisering.</span><span class="sxs-lookup"><span data-stu-id="f00ee-107">This fundamental change brings entirely new tools and methods for automation.</span></span>

<!-- removing images until we can get replacements
:::row:::
   :::column span="":::
      Windows
      [![PowerShell on Windows](media/overview/windows-desktop-660.gif)](media/overview/windows-desktop.gif#lightbox)
      [Install on Windows](install/installing-powershell-core-on-windows.md)
   :::column-end:::
   :::column span="":::
      Linux
      [![PowerShell on Linux](media/overview/linux-desktop-660.gif)](media/overview/linux-desktop.gif#lightbox)
      [Install on Linux](install/installing-powershell-core-on-linux.md)
   :::column-end:::
   :::column span="":::
      macOS
      [![PowerShell on macOS](media/overview/macos-desktop-660.gif)](media/overview/macos-desktop.gif#lightbox)
      [Install on macOS](install/installing-powershell-core-on-macos.md)
   :::column-end:::
:::row-end:::
-->

## <a name="output-is-object-based"></a><span data-ttu-id="f00ee-108">Utdata är Object-baserad</span><span class="sxs-lookup"><span data-stu-id="f00ee-108">Output is object-based</span></span>

<span data-ttu-id="f00ee-109">Till skillnad från traditionella kommando rads gränssnitt är PowerShell-cmdletar utformade för att hantera objekt.</span><span class="sxs-lookup"><span data-stu-id="f00ee-109">Unlike traditional command-line interfaces, PowerShell cmdlets are designed to deal with objects.</span></span>
<span data-ttu-id="f00ee-110">Ett objekt är strukturerad information som är mer än bara den sträng med tecken som visas på skärmen.</span><span class="sxs-lookup"><span data-stu-id="f00ee-110">An object is structured information that is more than just the string of characters appearing on the screen.</span></span> <span data-ttu-id="f00ee-111">Kommandoutdata innehåller alltid ytterligare information som du kan använda om du behöver den.</span><span class="sxs-lookup"><span data-stu-id="f00ee-111">Command output always carries extra information that you can use if you need it.</span></span>

<span data-ttu-id="f00ee-112">Om du har använt text bearbetnings verktyg för att bearbeta data tidigare kommer du att se att de fungerar annorlunda när de används i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f00ee-112">If you've used text-processing tools to process data in the past, you'll find that they behave differently when used in PowerShell.</span></span> <span data-ttu-id="f00ee-113">I de flesta fall behöver du inte text bearbetnings verktyg för att extrahera speciell information.</span><span class="sxs-lookup"><span data-stu-id="f00ee-113">In most cases, you don't need text-processing tools to extract specific information.</span></span> <span data-ttu-id="f00ee-114">Du får direkt åtkomst till delar av data med hjälp av standardsyntaxen för PowerShell-objekt.</span><span class="sxs-lookup"><span data-stu-id="f00ee-114">You directly access portions of the data using standard PowerShell object syntax.</span></span>

## <a name="the-command-family-is-extensible"></a><span data-ttu-id="f00ee-115">Kommando serien är utöknings bar</span><span class="sxs-lookup"><span data-stu-id="f00ee-115">The command family is extensible</span></span>

<span data-ttu-id="f00ee-116">Gränssnitt som `cmd.exe` inte ger dig möjlighet att direkt utöka den inbyggda kommando uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="f00ee-116">Interfaces such as `cmd.exe` don't provide a way for you to directly extend the built-in command set.</span></span> <span data-ttu-id="f00ee-117">Du kan skapa externa kommando rads verktyg som körs i `cmd.exe` .</span><span class="sxs-lookup"><span data-stu-id="f00ee-117">You can create external command-line tools that run in `cmd.exe`.</span></span> <span data-ttu-id="f00ee-118">Men dessa externa verktyg saknar tjänster, till exempel hjälp integrering.</span><span class="sxs-lookup"><span data-stu-id="f00ee-118">But these external tools don't have services, such as Help integration.</span></span> <span data-ttu-id="f00ee-119">`cmd.exe` känner inte automatiskt till att dessa externa verktyg är giltiga kommandon.</span><span class="sxs-lookup"><span data-stu-id="f00ee-119">`cmd.exe` doesn't automatically know that these external tools are valid commands.</span></span>

<span data-ttu-id="f00ee-120">Kommandona i PowerShell kallas _cmdlets_.</span><span class="sxs-lookup"><span data-stu-id="f00ee-120">The commands in PowerShell are known as _cmdlets_.</span></span> <span data-ttu-id="f00ee-121">Du kan använda varje cmdlet separat, men deras effekt realiseras när du kombinerar dem för att utföra komplexa uppgifter.</span><span class="sxs-lookup"><span data-stu-id="f00ee-121">You can use each cmdlet separately, but their power is realized when you combine them to perform complex tasks.</span></span> <span data-ttu-id="f00ee-122">Precis som många gränssnitt ger PowerShell åtkomst till fil systemet på datorn.</span><span class="sxs-lookup"><span data-stu-id="f00ee-122">Like many shells, PowerShell gives you access to the file system on the computer.</span></span> <span data-ttu-id="f00ee-123">Med PowerShell- _providers_ kan du komma åt andra data lager, till exempel registret och certifikat Arkiv, så enkelt som du har åtkomst till fil systemet.</span><span class="sxs-lookup"><span data-stu-id="f00ee-123">PowerShell _providers_ enable you to access other data stores, such as the registry and the certificate stores, as easily as you access the file system.</span></span>

<span data-ttu-id="f00ee-124">Du kan skapa egna cmdlet-och Function-moduler med hjälp av kompilerade kod eller skript.</span><span class="sxs-lookup"><span data-stu-id="f00ee-124">You can create your own cmdlet and function modules using compiled code or scripts.</span></span> <span data-ttu-id="f00ee-125">Moduler kan lägga till cmdlets och providers i gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="f00ee-125">Modules can add cmdlets and providers to the shell.</span></span> <span data-ttu-id="f00ee-126">PowerShell stöder även skript som är likvärdiga med UNIX-Shell-skript och `cmd.exe` kommandofiler.</span><span class="sxs-lookup"><span data-stu-id="f00ee-126">PowerShell also supports scripts that are analogous to UNIX shell scripts and `cmd.exe` batch files.</span></span>

## <a name="support-for-command-aliases"></a><span data-ttu-id="f00ee-127">Stöd för kommando-alias</span><span class="sxs-lookup"><span data-stu-id="f00ee-127">Support for command aliases</span></span>

<span data-ttu-id="f00ee-128">PowerShell stöder alias för att referera till kommandon med alternativa namn.</span><span class="sxs-lookup"><span data-stu-id="f00ee-128">PowerShell supports aliases to refer to commands by alternate names.</span></span> <span data-ttu-id="f00ee-129">Med aliasering kan användare i andra gränssnitt använda vanliga kommando namn som de redan känner till för liknande åtgärder i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f00ee-129">Aliasing allows users with experience in other shells to use common command names that they already know for similar operations in PowerShell.</span></span>

<span data-ttu-id="f00ee-130">Alias associerar ett nytt namn med ett annat kommando.</span><span class="sxs-lookup"><span data-stu-id="f00ee-130">Aliasing associates a new name with another command.</span></span> <span data-ttu-id="f00ee-131">PowerShell har till exempel en intern funktion med namnet `Clear-Host` som rensar utdatafönstret.</span><span class="sxs-lookup"><span data-stu-id="f00ee-131">For example, PowerShell has an internal function named `Clear-Host` that clears the output window.</span></span> <span data-ttu-id="f00ee-132">Du kan ange antingen `cls` eller `clear` aliaset i en kommando tolk.</span><span class="sxs-lookup"><span data-stu-id="f00ee-132">You can type either the `cls` or `clear` alias at a command prompt.</span></span> <span data-ttu-id="f00ee-133">PowerShell tolkar dessa alias och kör `Clear-Host` funktionen.</span><span class="sxs-lookup"><span data-stu-id="f00ee-133">PowerShell interprets these aliases and runs the `Clear-Host` function.</span></span>

<span data-ttu-id="f00ee-134">Den här funktionen hjälper användare att lära sig PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f00ee-134">This feature helps users to learn PowerShell.</span></span> <span data-ttu-id="f00ee-135">De flesta- `cmd.exe` och UNIX-användare har ett stort repertoaren kommandon som användare redan känner till med namn.</span><span class="sxs-lookup"><span data-stu-id="f00ee-135">First, most `cmd.exe` and Unix users have a large repertoire of commands that users already know by name.</span></span> <span data-ttu-id="f00ee-136">PowerShell-motsvarigheterna kanske inte genererar identiska resultat.</span><span class="sxs-lookup"><span data-stu-id="f00ee-136">The PowerShell equivalents may not produce identical results.</span></span> <span data-ttu-id="f00ee-137">Resultaten är dock tillräckligt nära att användarna kan arbeta utan att känna till PowerShell-kommando namnet.</span><span class="sxs-lookup"><span data-stu-id="f00ee-137">However, the results are close enough that users can do work without knowing the PowerShell command name.</span></span> <span data-ttu-id="f00ee-138">"Muskel minne" är en annan stor källa för att lära sig ett nytt kommando gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="f00ee-138">"Muscle memory" is another major source of frustration when learning a new command shell.</span></span> <span data-ttu-id="f00ee-139">Om du har använt `cmd.exe` i år kan du ange `cls` kommandot för att rensa skärmen.</span><span class="sxs-lookup"><span data-stu-id="f00ee-139">If you have used `cmd.exe` for years, you might reflexively type the `cls` command to clear the screen.</span></span> <span data-ttu-id="f00ee-140">Utan alias för `Clear-Host` får du ett fel meddelande och vet inte vad du ska göra för att rensa utdata.</span><span class="sxs-lookup"><span data-stu-id="f00ee-140">Without the alias for `Clear-Host`, you receive an error message and won't know what to do to clear the output.</span></span>

## <a name="powershell-handles-console-input-and-display"></a><span data-ttu-id="f00ee-141">PowerShell hanterar inmatade konsoler och visar</span><span class="sxs-lookup"><span data-stu-id="f00ee-141">PowerShell handles console input and display</span></span>

<span data-ttu-id="f00ee-142">När du skriver ett kommando bearbetar PowerShell alltid kommando rads indatamängden direkt.</span><span class="sxs-lookup"><span data-stu-id="f00ee-142">When you type a command, PowerShell always processes the command-line input directly.</span></span> <span data-ttu-id="f00ee-143">PowerShell formaterar också utdata som visas på skärmen.</span><span class="sxs-lookup"><span data-stu-id="f00ee-143">PowerShell also formats the output that you see on the screen.</span></span> <span data-ttu-id="f00ee-144">Den här skillnaden är viktig eftersom den minskar det arbete som krävs för varje cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f00ee-144">This difference is significant because it reduces the work required of each cmdlet.</span></span> <span data-ttu-id="f00ee-145">Det garanterar att du alltid kan göra saker på samma sätt med alla cmdletar.</span><span class="sxs-lookup"><span data-stu-id="f00ee-145">It ensures that you can always do things the same way with any cmdlet.</span></span> <span data-ttu-id="f00ee-146">Cmdlet-utvecklare behöver inte skriva kod för att parsa kommando rads argumenten eller formatera utdata.</span><span class="sxs-lookup"><span data-stu-id="f00ee-146">Cmdlet developers don't need to write code to parse the command-line arguments or format the output.</span></span>

<span data-ttu-id="f00ee-147">Traditionella kommando rads verktyg har egna scheman för att begära och Visa hjälp.</span><span class="sxs-lookup"><span data-stu-id="f00ee-147">Traditional command-line tools have their own schemes for requesting and displaying Help.</span></span> <span data-ttu-id="f00ee-148">Vissa kommando rads verktyg används `/?` för att utlösa hjälp visningen, andra använder `-?` , `/H` eller till och med `//` .</span><span class="sxs-lookup"><span data-stu-id="f00ee-148">Some command-line tools use `/?` to trigger the Help display; others use `-?`, `/H`, or even `//`.</span></span> <span data-ttu-id="f00ee-149">Vissa visar hjälpen i ett GUI-fönster, i stället för i konsolens visning.</span><span class="sxs-lookup"><span data-stu-id="f00ee-149">Some will display Help in a GUI window, rather than in the console display.</span></span> <span data-ttu-id="f00ee-150">Om du använder fel parameter kan verktyget ignorera det du skrev och börja köra en uppgift automatiskt.</span><span class="sxs-lookup"><span data-stu-id="f00ee-150">If you use the wrong parameter, the tool might ignore what you typed and begin executing a task automatically.</span></span>
<span data-ttu-id="f00ee-151">Eftersom PowerShell automatiskt tolkar och bearbetar kommando raden `-?` betyder parametern alltid att visa mig hjälp för det här kommandot.</span><span class="sxs-lookup"><span data-stu-id="f00ee-151">Since PowerShell automatically parses and processes the command line, the `-?` parameter always means "show me Help for this command".</span></span>

> [!NOTE]
> <span data-ttu-id="f00ee-152">Om du kör ett grafiskt program i PowerShell öppnas fönstret för programmet.</span><span class="sxs-lookup"><span data-stu-id="f00ee-152">If you run a graphic application in PowerShell, the window for the application opens.</span></span>
> <span data-ttu-id="f00ee-153">PowerShell inverkar bara vid bearbetning av kommando rads indata som du anger eller programutdata som returneras till konsol fönstret.</span><span class="sxs-lookup"><span data-stu-id="f00ee-153">PowerShell intervenes only when processing the command-line input you supply or the application output returned to the console window.</span></span> <span data-ttu-id="f00ee-154">Det påverkar inte hur programmet fungerar internt.</span><span class="sxs-lookup"><span data-stu-id="f00ee-154">It does not affect how the application works internally.</span></span>

## <a name="powershell-has-a-pipeline"></a><span data-ttu-id="f00ee-155">PowerShell har en pipeline</span><span class="sxs-lookup"><span data-stu-id="f00ee-155">PowerShell has a pipeline</span></span>

<span data-ttu-id="f00ee-156">Pipelines är utan tvekan det mest värdefulla konceptet som används i kommando rads gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="f00ee-156">Pipelines are arguably the most valuable concept used in command-line interfaces.</span></span> <span data-ttu-id="f00ee-157">När den används korrekt minskar pipelinen arbetet med att använda komplexa kommandon och gör det lättare att se arbets flödet.</span><span class="sxs-lookup"><span data-stu-id="f00ee-157">When used properly, pipelines reduce the effort of using complex commands and make it easier to see the flow of work.</span></span> <span data-ttu-id="f00ee-158">Varje kommando i en pipeline skickar utdata, objekt efter objekt, till nästa kommando.</span><span class="sxs-lookup"><span data-stu-id="f00ee-158">Each command in a pipeline passes its output, item by item, to the next command.</span></span> <span data-ttu-id="f00ee-159">Kommandon behöver inte hantera mer än ett objekt i taget.</span><span class="sxs-lookup"><span data-stu-id="f00ee-159">Commands don't have to handle more than one item at a time.</span></span> <span data-ttu-id="f00ee-160">Resultatet är minskad resursförbrukning och möjligheten att få utdata direkt.</span><span class="sxs-lookup"><span data-stu-id="f00ee-160">The result is reduced resource consumption and the ability to get output immediately.</span></span>

<span data-ttu-id="f00ee-161">Den notation som används för pipelines liknar den notation som används i andra gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="f00ee-161">The notation used for pipelines is similar to the notation used in other shells.</span></span> <span data-ttu-id="f00ee-162">I första hand kan det vara inte uppenbart hur pipelines skiljer sig i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f00ee-162">At first glance, it may not be apparent how pipelines are different in PowerShell.</span></span> <span data-ttu-id="f00ee-163">Även om du ser text på skärmen, PowerShell pipe-objekt, inte text, mellan kommandon.</span><span class="sxs-lookup"><span data-stu-id="f00ee-163">Although you see text on the screen, PowerShell pipes objects, not text, between commands.</span></span>

<span data-ttu-id="f00ee-164">Om du till exempel använder `Out-Host` cmdleten för att tvinga fram visning av utdata från ett annat kommando, ser utdata ut precis som den normala texten som visas på skärmen, och delas upp i sidor:</span><span class="sxs-lookup"><span data-stu-id="f00ee-164">For example, if you use the `Out-Host` cmdlet to force a page-by-page display of output from another command, the output looks just like the normal text displayed on the screen, broken up into pages:</span></span>

```powershell
Get-ChildItem | Out-Host -Paging
```

```Output
    Directory: /mnt/c/Git/PS-Docs/PowerShell-Docs/reference/7.0/Microsoft.PowerShell.Core

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d----          05/22/2020    08:30                About
-----          05/20/2020    14:36           9044 Add-History.md
-----          05/20/2020    14:36          12227 Clear-History.md
-----          05/20/2020    14:36           3566 Clear-Host.md
-----          05/20/2020    14:36          29087 Connect-PSSession.md
-----          05/20/2020    14:36           5705 Debug-Job.md
-----          05/20/2020    14:36           3515 Disable-ExperimentalFeature.md
-----          05/20/2020    14:36          25531 Disable-PSRemoting.md
-----          05/20/2020    14:36           7852 Disable-PSSessionConfiguration.md
-----          05/20/2020    14:36          25355 Disconnect-PSSession.md
-----          05/20/2020    14:36           3491 Enable-ExperimentalFeature.md
-----          05/20/2020    14:36          13310 Enable-PSRemoting.md
-----          05/20/2020    14:36           8401 Enable-PSSessionConfiguration.md
-----          05/20/2020    14:36           9531 Enter-PSHostProcess.md
...
<SPACE> next page; <CR> next line; Q quit
```

<span data-ttu-id="f00ee-165">Växlingen minskar också processor användningen eftersom bearbetningen överförs till `Out-Host` cmdleten när en hel sida är klar att visas.</span><span class="sxs-lookup"><span data-stu-id="f00ee-165">Paging also reduces CPU utilization because processing transfers to the `Out-Host` cmdlet when it has a complete page ready to display.</span></span> <span data-ttu-id="f00ee-166">Cmdletarna som föregår den i pipelinen pausar körningen tills nästa sida med utdata är tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="f00ee-166">The cmdlets that precede it in the pipeline pause execution until the next page of output is available.</span></span>

### <a name="objects-in-the-pipeline"></a><span data-ttu-id="f00ee-167">Objekt i pipelinen</span><span class="sxs-lookup"><span data-stu-id="f00ee-167">Objects in the pipeline</span></span>

<span data-ttu-id="f00ee-168">När du kör en cmdlet i PowerShell visas text utdata eftersom det är nödvändigt att representera objekt som text i ett konsol fönster.</span><span class="sxs-lookup"><span data-stu-id="f00ee-168">When you run a cmdlet in PowerShell, you see text output because it is necessary to represent objects as text in a console window.</span></span> <span data-ttu-id="f00ee-169">Text utmatningen kanske inte visar alla egenskaper för objektet som ska skrivas ut.</span><span class="sxs-lookup"><span data-stu-id="f00ee-169">The text output may not display all of the properties of the object being output.</span></span>

<span data-ttu-id="f00ee-170">Överväg till exempel `Get-Location` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f00ee-170">For example, consider the `Get-Location` cmdlet.</span></span> <span data-ttu-id="f00ee-171">Text utmatningen är en sammanfattning av informationen, inte en fullständig representation av det objekt som returnerades av `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="f00ee-171">The text output is a summary of information, not a complete representation of the object returned by `Get-Location`.</span></span> <span data-ttu-id="f00ee-172">Rubriken i utdata läggs till av processen som formaterar data för skärm visning.</span><span class="sxs-lookup"><span data-stu-id="f00ee-172">The heading in the output is added by the process that formats the data for onscreen display.</span></span>

```powershell
Get-Location
```

```Output
Path
----
C:\
```

<span data-ttu-id="f00ee-173">Genom att skicka utdata till `Get-Member` cmdleten visas information om objektet som returnerades av `Get-Location` .</span><span class="sxs-lookup"><span data-stu-id="f00ee-173">Piping the output to the `Get-Member` cmdlet displays information about the object returned by `Get-Location`.</span></span>

```powershell
Get-Location | Get-Member
```

```Output
   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Equals       Method     bool Equals(System.Object obj)
GetHashCode  Method     int GetHashCode()
GetType      Method     type GetType()
ToString     Method     string ToString()
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   string Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {get;}
ProviderPath Property   string ProviderPath {get;}
```

<span data-ttu-id="f00ee-174">`Get-Location` Returnerar ett **PathInfo** -objekt som innehåller den aktuella sökvägen och annan information.</span><span class="sxs-lookup"><span data-stu-id="f00ee-174">`Get-Location` returns a **PathInfo** object that contains the current path and other information.</span></span>

## <a name="built-in-help-system"></a><span data-ttu-id="f00ee-175">Inbyggt hjälpsystem</span><span class="sxs-lookup"><span data-stu-id="f00ee-175">Built-in help system</span></span>

<span data-ttu-id="f00ee-176">På samma sätt som UNIX `man` -sidor innehåller PowerShell detaljerade hjälp artiklar som förklarar PowerShell-begrepp och kommandosyntax.</span><span class="sxs-lookup"><span data-stu-id="f00ee-176">Similar to Unix `man` pages, PowerShell includes detailed help articles that explain PowerShell concepts and command syntax.</span></span> <span data-ttu-id="f00ee-177">Använd cmdleten [Get-Help][] för att visa dessa artiklar i kommando tolken eller Visa de senaste uppdaterade versionerna av de här artiklarna i PowerShell-dokumentationen online.</span><span class="sxs-lookup"><span data-stu-id="f00ee-177">Use the [Get-Help][] cmdlet to display these articles at the command prompt or view the most recently updated versions of these articles in the PowerShell documentation online.</span></span>

## <a name="next-steps"></a><span data-ttu-id="f00ee-178">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="f00ee-178">Next steps</span></span>

<span data-ttu-id="f00ee-179">Mer information om PowerShell finns i avsnittet **Learning PowerShell** på den här webbplatsen.</span><span class="sxs-lookup"><span data-stu-id="f00ee-179">To learn more about PowerShell, see the **Learning PowerShell** section of this site.</span></span>

<!-- link references -->

[Get – hjälp]: /powershell/module/microsoft.powershell.core/Get-Help
[Get-Help]: /powershell/module/microsoft.powershell.core/Get-Help
