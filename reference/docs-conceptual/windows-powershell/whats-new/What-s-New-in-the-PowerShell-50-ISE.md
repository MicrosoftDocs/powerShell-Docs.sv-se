---
ms.date: 09/06/2019
keywords: powershell,cmdlet
title: Nyheter i PowerShell 5,0 ISE
ms.openlocfilehash: 1f5d32d583165ff8ead0a95b1c882386cf654326
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83810528"
---
# <a name="whats-new-in-the-windows-powershell-50-ise"></a><span data-ttu-id="5869e-103">Vad är nytt i Windows PowerShell 5,0 ISE</span><span class="sxs-lookup"><span data-stu-id="5869e-103">What's New in the Windows PowerShell 5.0 ISE</span></span>

<span data-ttu-id="5869e-104">I det här avsnittet beskrivs nya och uppdaterade funktioner som har introducerats i version 5,0 av Windows PowerShell ISE (Integrated Scripting Environment).</span><span class="sxs-lookup"><span data-stu-id="5869e-104">This topic explains the new and updated features that have been introduced in version 5.0 of the Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

> [!NOTE]
> <span data-ttu-id="5869e-105">PowerShell ISE är inte längre vid utveckling av aktiva funktioner.</span><span class="sxs-lookup"><span data-stu-id="5869e-105">The PowerShell ISE is no longer in active feature development.</span></span> <span data-ttu-id="5869e-106">Som en leverans komponent i Windows fortsätter den att vara officiellt tillgänglig för säkerhets-och högprioriterade service-korrigeringar.</span><span class="sxs-lookup"><span data-stu-id="5869e-106">As a shipping component of Windows, it continues to be officially supported for security and high-priority servicing fixes.</span></span>
> <span data-ttu-id="5869e-107">Vi har för närvarande inga planer på att ta bort ISE från Windows.</span><span class="sxs-lookup"><span data-stu-id="5869e-107">We currently have no plans to remove the ISE from Windows.</span></span>
>
> <span data-ttu-id="5869e-108">Det finns inget stöd för ISE i PowerShell V6 och senare.</span><span class="sxs-lookup"><span data-stu-id="5869e-108">There is no support for the ISE in PowerShell v6 and beyond.</span></span> <span data-ttu-id="5869e-109">Användare som söker efter ersättning för ISE bör använda [Visual Studio Code](https://code.visualstudio.com/) med [PowerShell-tillägget](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell).</span><span class="sxs-lookup"><span data-stu-id="5869e-109">Users looking for replacement for the ISE should use [Visual Studio Code](https://code.visualstudio.com/) with the [PowerShell Extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell).</span></span>

## <a name="feature-description"></a><span data-ttu-id="5869e-110">Funktionsbeskrivning</span><span class="sxs-lookup"><span data-stu-id="5869e-110">Feature description</span></span>

<span data-ttu-id="5869e-111">Windows PowerShell ISE är ett värd program som gör det möjligt att skriva, köra och testa skript och moduler i en grafisk och intuitiv miljö.</span><span class="sxs-lookup"><span data-stu-id="5869e-111">The Windows PowerShell ISE is a host application that enables you to write, run, and test scripts and modules in a graphical and intuitive environment.</span></span> <span data-ttu-id="5869e-112">Viktiga funktioner som syntax-färgning, TABB-slutförande, visuell fel sökning, Unicode-kompatibilitet och Sammanhangs beroende hjälp ger en omfattande skript upplevelse.</span><span class="sxs-lookup"><span data-stu-id="5869e-112">Key features such as syntax-coloring, tab completion, visual debugging, Unicode compliance, and context-sensitive Help provide a rich scripting experience.</span></span>

<span data-ttu-id="5869e-113">Mer information finns i [Introduktion till Windows PowerShell ISE](../ise/Introducing-the-Windows-PowerShell-ISE.md).</span><span class="sxs-lookup"><span data-stu-id="5869e-113">For more information, see [Introducing the Windows PowerShell ISE](../ise/Introducing-the-Windows-PowerShell-ISE.md).</span></span>

<span data-ttu-id="5869e-114">I följande tabell visas de nya och ändrade funktionerna i den här versionen av Windows PowerShell ISE i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5869e-114">The following table lists the new and changed features for this release of Windows PowerShell ISE in Windows PowerShell.</span></span>

## <a name="intellisense"></a><span data-ttu-id="5869e-115">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="5869e-115">IntelliSense</span></span>

> <span data-ttu-id="5869e-116">Tillagt i ISE 3,0</span><span class="sxs-lookup"><span data-stu-id="5869e-116">Added in ISE 3.0</span></span>

<span data-ttu-id="5869e-117">IntelliSense är en hjälp funktion för automatisk komplettering som är en del av Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="5869e-117">IntelliSense is an automatic-completion assistance feature that is part of Windows PowerShell ISE.</span></span>
<span data-ttu-id="5869e-118">IntelliSense visar klicknings bara menyer med potentiellt matchande cmdlets, parametrar, parameter värden, filer eller mappar medan du skriver.</span><span class="sxs-lookup"><span data-stu-id="5869e-118">IntelliSense displays clickable menus of potentially matching cmdlets, parameters, parameter values, files, or folders as you type.</span></span>

<span data-ttu-id="5869e-119">**Vilket värde medför den här ändringen?**</span><span class="sxs-lookup"><span data-stu-id="5869e-119">**What value does this change add?**</span></span>

<span data-ttu-id="5869e-120">Med tillägget av IntelliSense är det lättare att identifiera cmdlets och syntax när du använder Windows PowerShell ISE för att skapa skript.</span><span class="sxs-lookup"><span data-stu-id="5869e-120">With the addition of IntelliSense, it's easier to discover cmdlets and syntax when you use Windows PowerShell ISE to create scripts.</span></span> <span data-ttu-id="5869e-121">Du kan också använda Windows PowerShell ISE för att lära dig Windows PowerShell medan du skapar nya skript.</span><span class="sxs-lookup"><span data-stu-id="5869e-121">You can also use Windows PowerShell ISE to learn Windows PowerShell while you create new scripts.</span></span>

<span data-ttu-id="5869e-122">**Vad fungerar inte på samma sätt?**</span><span class="sxs-lookup"><span data-stu-id="5869e-122">**What works differently?**</span></span>

<span data-ttu-id="5869e-123">När du skriver cmdlets i Windows PowerShell ISE visas en rullnings bar och klickande meny, så att du kan bläddra och välja lämpliga kommandon.</span><span class="sxs-lookup"><span data-stu-id="5869e-123">When you type cmdlets in the Windows PowerShell ISE, a scrollable and clickable menu displays, allowing you to browse and select the appropriate commands.</span></span>

## <a name="snippets"></a><span data-ttu-id="5869e-124">Kodfragment</span><span class="sxs-lookup"><span data-stu-id="5869e-124">Snippets</span></span>

> <span data-ttu-id="5869e-125">Tillagt i ISE 3,0</span><span class="sxs-lookup"><span data-stu-id="5869e-125">Added in ISE 3.0</span></span>

<span data-ttu-id="5869e-126">*Kodfragment* är korta avsnitt med Windows PowerShell-kod som du kan infoga i de skript som du skapar i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="5869e-126">*Snippets* are short sections of Windows PowerShell code that you can insert into the scripts you create in Windows PowerShell ISE.</span></span> <span data-ttu-id="5869e-127">Windows PowerShell ISE levereras med en standard uppsättning kod avsnitt.</span><span class="sxs-lookup"><span data-stu-id="5869e-127">Windows PowerShell ISE comes with a default set of snippets.</span></span> <span data-ttu-id="5869e-128">Du kan lägga till kodfragment med hjälp av `New-Snippet` cmdleten när du arbetar i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="5869e-128">You can add snippets by using the `New-Snippet` cmdlet while working in Windows PowerShell ISE.</span></span>

<span data-ttu-id="5869e-129">**Vilket värde medför den här ändringen?**</span><span class="sxs-lookup"><span data-stu-id="5869e-129">**What value does this change add?**</span></span>

<span data-ttu-id="5869e-130">Genom att använda kodfragment kan du snabbt sätta samman och skapa skript för att automatisera din miljö.</span><span class="sxs-lookup"><span data-stu-id="5869e-130">By using snippets, you can quickly assemble and create scripts to automate your environment.</span></span>

<span data-ttu-id="5869e-131">**Vad fungerar inte på samma sätt?**</span><span class="sxs-lookup"><span data-stu-id="5869e-131">**What works differently?**</span></span>

<span data-ttu-id="5869e-132">Om du vill använda kodfragment i Windows PowerShell 3,0 eller senare klickar du på **Starta kodfragment**på **Redigera** -menyn eller trycker på <kbd>CTRL</kbd> + <kbd>J</kbd>.</span><span class="sxs-lookup"><span data-stu-id="5869e-132">To use snippets in Windows PowerShell 3.0 or later, on the **Edit** menu, click **Start Snippets**, or press <kbd>Ctrl</kbd>+<kbd>J</kbd>.</span></span>

## <a name="add-on-tools"></a><span data-ttu-id="5869e-133">Tilläggs verktyg</span><span class="sxs-lookup"><span data-stu-id="5869e-133">Add-on tools</span></span>

> <span data-ttu-id="5869e-134">Tillagt i PowerShell 3,0</span><span class="sxs-lookup"><span data-stu-id="5869e-134">Added in PowerShell 3.0</span></span>

<span data-ttu-id="5869e-135">Windows PowerShell ISE stöder nu tilläggs verktyg med hjälp av objekt modellen.</span><span class="sxs-lookup"><span data-stu-id="5869e-135">Windows PowerShell ISE now supports add-on tools using the object model.</span></span> <span data-ttu-id="5869e-136">Dessa tillägg är Windows Presentation Foundation-kontroller (WPF) som visas som ett lodrätt eller vågrätt fönster i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="5869e-136">These add-ons are Windows Presentation Foundation (WPF) controls that are displayed as a vertical or horizontal pane in the console.</span></span> <span data-ttu-id="5869e-137">Flera tilläggs verktyg i ett fönster visas som en tabbad kontroll.</span><span class="sxs-lookup"><span data-stu-id="5869e-137">Multiple add-on tools in a pane are displayed as a tabbed control.</span></span> <span data-ttu-id="5869e-138">Du kan också lägga till eller ta bort tilläggs verktyg som produceras av icke-Microsoft-parter.</span><span class="sxs-lookup"><span data-stu-id="5869e-138">You can also add or remove add-on tools that are produced by non-Microsoft parties.</span></span> <span data-ttu-id="5869e-139">Mer information finns i [syftet med Windows PowerShell ISE skript objekt modell](../ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md).</span><span class="sxs-lookup"><span data-stu-id="5869e-139">For more information, see [The Purpose of the Windows PowerShell ISE Scripting Object Model](../ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md).</span></span>

<span data-ttu-id="5869e-140">**Vilket värde medför den här ändringen?**</span><span class="sxs-lookup"><span data-stu-id="5869e-140">**What value does this change add?**</span></span>

<span data-ttu-id="5869e-141">Med tillägg kan du utöka och anpassa Windows PowerShell ISE med verktyg som lägger till funktioner och förbättrar skript upplevelsen.</span><span class="sxs-lookup"><span data-stu-id="5869e-141">Add-ons allow you to extend and customize Windows PowerShell ISE with tools that add functionality and enhance your scripting experience.</span></span>

<span data-ttu-id="5869e-142">**Vad fungerar inte på samma sätt?**</span><span class="sxs-lookup"><span data-stu-id="5869e-142">**What works differently?**</span></span>

<span data-ttu-id="5869e-143">Windows PowerShell ISE 3,0 och senare levereras med **kommando** tillägg.</span><span class="sxs-lookup"><span data-stu-id="5869e-143">Windows PowerShell ISE 3.0 and later come with the **Commands** add-on.</span></span> <span data-ttu-id="5869e-144">Med **kommandona kommando** tillägg kan du bläddra bland cmdletar och få åtkomst till hjälp om cmdlets sida vid sida med **skript** -och **konsol** Fönstren.</span><span class="sxs-lookup"><span data-stu-id="5869e-144">The **Commands** add-on allows you to browse cmdlets, and access help about the cmdlets side-by-side with the **Script** and **Console** Panes.</span></span>

<span data-ttu-id="5869e-145">Du hittar ytterligare tillägg med hjälp av kommandot **Öppna tilläggs verktyg webbplats** på menyn **tillägg** .</span><span class="sxs-lookup"><span data-stu-id="5869e-145">Additional add-ons can be found by using the **Open Add-on Tools Website** command on the **Add-ons** menu.</span></span>

## <a name="restart-manager-and-auto-save"></a><span data-ttu-id="5869e-146">Starta om hanteraren och Spara automatiskt</span><span class="sxs-lookup"><span data-stu-id="5869e-146">Restart manager and auto-save</span></span>

> <span data-ttu-id="5869e-147">Tillagt i PowerShell 3,0</span><span class="sxs-lookup"><span data-stu-id="5869e-147">Added in PowerShell 3.0</span></span>

<span data-ttu-id="5869e-148">Windows PowerShell ISE sparar nu automatiskt de öppna skripten var två: e minut, på en annan plats.</span><span class="sxs-lookup"><span data-stu-id="5869e-148">Windows PowerShell ISE now automatically saves your open scripts every two minutes, in a separate location.</span></span> <span data-ttu-id="5869e-149">När Windows PowerShell ISE startar om efter en oväntad krasch eller omstart återställer den skript som var öppna i den senaste sessionen, även om skripten inte sparades.</span><span class="sxs-lookup"><span data-stu-id="5869e-149">When Windows PowerShell ISE restarts after an unexpected crash or reboot, it recovers scripts that were open in the last session, even if the scripts weren't saved.</span></span>

<span data-ttu-id="5869e-150">Om du vill ändra intervallet för automatisk sparande kör du följande kommando i konsol fönstret: `$psise.Options.AutoSaveMinuteInterval` .</span><span class="sxs-lookup"><span data-stu-id="5869e-150">To change the automatic saving interval, run the following command in the Console pane: `$psise.Options.AutoSaveMinuteInterval`.</span></span>

<span data-ttu-id="5869e-151">**Vilket värde medför den här ändringen?**</span><span class="sxs-lookup"><span data-stu-id="5869e-151">**What value does this change add?**</span></span>

<span data-ttu-id="5869e-152">Nu kan du arbeta inom Windows PowerShell ISE vet att dina öppna skript sparas automatiskt.</span><span class="sxs-lookup"><span data-stu-id="5869e-152">You can now work within Windows PowerShell ISE knowing that your open scripts are automatically saved.</span></span>

<span data-ttu-id="5869e-153">**Vad fungerar inte på samma sätt?**</span><span class="sxs-lookup"><span data-stu-id="5869e-153">**What works differently?**</span></span>

<span data-ttu-id="5869e-154">Windows PowerShell ISE 2,0 sparar inte skripten automatiskt.</span><span class="sxs-lookup"><span data-stu-id="5869e-154">Windows PowerShell ISE 2.0 doesn't save the scripts automatically.</span></span>

## <a name="most-recently-used-list"></a><span data-ttu-id="5869e-155">Lista över senast använda</span><span class="sxs-lookup"><span data-stu-id="5869e-155">Most-recently used list</span></span>

> <span data-ttu-id="5869e-156">Tillagt i PowerShell 3,0</span><span class="sxs-lookup"><span data-stu-id="5869e-156">Added in PowerShell 3.0</span></span>

<span data-ttu-id="5869e-157">Windows PowerShell ISE har nu en lista med senast använda filer för filer.</span><span class="sxs-lookup"><span data-stu-id="5869e-157">Windows PowerShell ISE now has a most-recently used list for files.</span></span> <span data-ttu-id="5869e-158">När du öppnar en fil i Windows PowerShell ISE läggs filen till i listan över senast använda på **Arkiv** -menyn.</span><span class="sxs-lookup"><span data-stu-id="5869e-158">When you open a file in Windows PowerShell ISE, the file is added to the most-recently used list on the **File** menu.</span></span>

<span data-ttu-id="5869e-159">Om du vill ändra standardvärdet för antal filer i listan senast använda, kör du följande kommando i konsol fönstret: `$psise.Options.MruCount` .</span><span class="sxs-lookup"><span data-stu-id="5869e-159">To change the default number of files in the most-recently used list, run the following command in the Console Pane: `$psise.Options.MruCount`.</span></span>

<span data-ttu-id="5869e-160">**Vilket värde medför den här ändringen?**</span><span class="sxs-lookup"><span data-stu-id="5869e-160">**What value does this change add?**</span></span>

<span data-ttu-id="5869e-161">Nu kan du använda listan med senast använda listan för att enkelt komma åt dina ofta använda filer.</span><span class="sxs-lookup"><span data-stu-id="5869e-161">You can now use the most-recently used list to easily access your frequently used files.</span></span>

<span data-ttu-id="5869e-162">**Vad fungerar inte på samma sätt?**</span><span class="sxs-lookup"><span data-stu-id="5869e-162">**What works differently?**</span></span>

<span data-ttu-id="5869e-163">Windows PowerShell ISE 2,0 har inte någon lista som du nyligen har använt.</span><span class="sxs-lookup"><span data-stu-id="5869e-163">Windows PowerShell ISE 2.0 doesn't have a most-recently used list.</span></span>

## <a name="console-pane"></a><span data-ttu-id="5869e-164">Konsol fönster</span><span class="sxs-lookup"><span data-stu-id="5869e-164">Console Pane</span></span>

> <span data-ttu-id="5869e-165">Tillagt i PowerShell 3,0</span><span class="sxs-lookup"><span data-stu-id="5869e-165">Added in PowerShell 3.0</span></span>

<span data-ttu-id="5869e-166">De separata kommando-och utdatafönstret som var tillgängliga i den första versionen av Windows PowerShell ISE har kombinerats till ett enda konsol fönster.</span><span class="sxs-lookup"><span data-stu-id="5869e-166">The separate Command and Output Panes that were available in the first release of Windows PowerShell ISE have been combined into a single Console Pane.</span></span> <span data-ttu-id="5869e-167">Konsol fönstret liknar en typisk Windows PowerShell-konsol, men den innehåller följande förbättringar:</span><span class="sxs-lookup"><span data-stu-id="5869e-167">The Console Pane is similar in function and appearance to a typical Windows PowerShell console, but it includes the following enhancements:</span></span>

- <span data-ttu-id="5869e-168">Syntax för inmatnings text (inte text), inklusive XML-syntax</span><span class="sxs-lookup"><span data-stu-id="5869e-168">Syntax coloring for input text (not output text), including XML syntax</span></span>
- <span data-ttu-id="5869e-169">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="5869e-169">IntelliSense</span></span>
- <span data-ttu-id="5869e-170">Matchning av klammerparentes</span><span class="sxs-lookup"><span data-stu-id="5869e-170">Brace matching</span></span>
- <span data-ttu-id="5869e-171">Fel indikation</span><span class="sxs-lookup"><span data-stu-id="5869e-171">Error indication</span></span>
- <span data-ttu-id="5869e-172">Fullständigt Unicode-stöd</span><span class="sxs-lookup"><span data-stu-id="5869e-172">Full Unicode support</span></span>
- <span data-ttu-id="5869e-173"><kbd>F1</kbd> Sammanhangs beroende hjälp</span><span class="sxs-lookup"><span data-stu-id="5869e-173"><kbd>F1</kbd> context-sensitive help</span></span>
- <span data-ttu-id="5869e-174"><kbd>CTRL</kbd> + <kbd>F1</kbd> kontext känsligt show-kommando</span><span class="sxs-lookup"><span data-stu-id="5869e-174"><kbd>Ctrl</kbd>+<kbd>F1</kbd> context-sensitive Show-Command</span></span>
- <span data-ttu-id="5869e-175">Komplext skript och stöd från höger till vänster</span><span class="sxs-lookup"><span data-stu-id="5869e-175">Complex script and right-to-left support</span></span>
- <span data-ttu-id="5869e-176">Stöd för teckensnitt</span><span class="sxs-lookup"><span data-stu-id="5869e-176">Font support</span></span>
- <span data-ttu-id="5869e-177">Zoom</span><span class="sxs-lookup"><span data-stu-id="5869e-177">Zoom</span></span>
- <span data-ttu-id="5869e-178">Linje – Välj och blockera – Välj lägen</span><span class="sxs-lookup"><span data-stu-id="5869e-178">Line-select and block-select modes</span></span>
- <span data-ttu-id="5869e-179">Bevarande av typ av innehåll på kommando raden när du trycker på <kbd>nedåtpilen</kbd> för att visa historiken i-konsolen</span><span class="sxs-lookup"><span data-stu-id="5869e-179">Preservation of typed content at the command line when you press the <kbd>UpArrow</kbd> to view history in the console</span></span>

<span data-ttu-id="5869e-180">**Vilket värde medför den här ändringen?**</span><span class="sxs-lookup"><span data-stu-id="5869e-180">**What value does this change add?**</span></span>

<span data-ttu-id="5869e-181">Att lägga till dessa ändringar i konsol fönstret är en skript upplevelse som är mer konsekvent med konsol gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="5869e-181">The addition of these Console Pane changes provides a scripting experience that is more consistent with the console interface.</span></span>

<span data-ttu-id="5869e-182">**Vad fungerar inte på samma sätt?**</span><span class="sxs-lookup"><span data-stu-id="5869e-182">**What works differently?**</span></span>

<span data-ttu-id="5869e-183">Windows PowerShell ISE 2,0 har separata kommando-och utmatnings fönster.</span><span class="sxs-lookup"><span data-stu-id="5869e-183">Windows PowerShell ISE 2.0 has separate Command and Output Panes.</span></span>

## <a name="command-line-switches"></a><span data-ttu-id="5869e-184">Kommando rads växlar</span><span class="sxs-lookup"><span data-stu-id="5869e-184">Command-line switches</span></span>

> <span data-ttu-id="5869e-185">Tillagt i PowerShell 3,0</span><span class="sxs-lookup"><span data-stu-id="5869e-185">Added in PowerShell 3.0</span></span>

<span data-ttu-id="5869e-186">Om du startar Windows PowerShell ISE från kommando raden (genom att skriva **powershell_ise. exe**) kan du lägga till följande nya kommando rads växlar.</span><span class="sxs-lookup"><span data-stu-id="5869e-186">If you start Windows PowerShell ISE from the command line (by typing **powershell_ise.exe**), you can add the following new command-line switches.</span></span>

- <span data-ttu-id="5869e-187">`-NoProfile`: Startar Windows PowerShell ISE utan att köra`$profile`</span><span class="sxs-lookup"><span data-stu-id="5869e-187">`-NoProfile`: Starts Windows PowerShell ISE without running `$profile`</span></span>
- <span data-ttu-id="5869e-188">`-Help`: Visar ett hjälp fönster</span><span class="sxs-lookup"><span data-stu-id="5869e-188">`-Help`: Displays a Help window</span></span>
- <span data-ttu-id="5869e-189">`-mta`: Startar Windows PowerShell ISE i flertrådade Apartment-läge.</span><span class="sxs-lookup"><span data-stu-id="5869e-189">`-mta`: Starts Windows PowerShell ISE in multithreaded apartment mode.</span></span> <span data-ttu-id="5869e-190">Standard åtgärds läget för Windows PowerShell ISE är ett entrådat Apartment-läge, eller `-sta` .</span><span class="sxs-lookup"><span data-stu-id="5869e-190">The default operation mode for Windows PowerShell ISE is single-threaded apartment mode, or `-sta`.</span></span>

<span data-ttu-id="5869e-191">**Vilket värde medför den här ändringen?**</span><span class="sxs-lookup"><span data-stu-id="5869e-191">**What value does this change add?**</span></span>

<span data-ttu-id="5869e-192">Genom att lägga till dessa kommando rads växlar kan du kontrol lera miljön där Windows PowerShell ISE körs.</span><span class="sxs-lookup"><span data-stu-id="5869e-192">The addition of these command-line switches allows you to control the environment in which the Windows PowerShell ISE runs.</span></span>

<span data-ttu-id="5869e-193">**Vad fungerar inte på samma sätt?**</span><span class="sxs-lookup"><span data-stu-id="5869e-193">**What works differently?**</span></span>

<span data-ttu-id="5869e-194">Windows PowerShell ISE 2,0 känner inte igen kommando rads växlarna.</span><span class="sxs-lookup"><span data-stu-id="5869e-194">Windows PowerShell ISE 2.0 doesn't recognize these command-line switches.</span></span>

## <a name="new-editor-features"></a><span data-ttu-id="5869e-195">Nya redigerings funktioner</span><span class="sxs-lookup"><span data-stu-id="5869e-195">New editor features</span></span>

> <span data-ttu-id="5869e-196">Tillagt i PowerShell 3,0</span><span class="sxs-lookup"><span data-stu-id="5869e-196">Added in PowerShell 3.0</span></span>

<span data-ttu-id="5869e-197">Andra Windows PowerShell ISE redigerings funktioner är:</span><span class="sxs-lookup"><span data-stu-id="5869e-197">Other Windows PowerShell ISE editing features include:</span></span>

- <span data-ttu-id="5869e-198">Syntax för **XML-syntax** – Windows PowerShell ISE nu XML-syntax för färger på samma sätt som i Windows PowerShell-syntaxen.</span><span class="sxs-lookup"><span data-stu-id="5869e-198">**XML syntax coloring** - Windows PowerShell ISE now colors XML syntax in the same way as it colors Windows PowerShell syntax.</span></span>
- <span data-ttu-id="5869e-199">**Matchning av klamrar** – Windows PowerShell ISE innehåller matchning och markering av klamrar och kan användas på följande sätt: (Använd kommandot **gå till matchning** eller <kbd>CTRL</kbd> + <kbd>)</kbd> för att hitta den avslutande klammerparentesen, om du har valt en inledande klammerparentes).</span><span class="sxs-lookup"><span data-stu-id="5869e-199">**Brace matching** - Windows PowerShell ISE includes brace matching and highlighting, and can be used in the following ways: (for example, using the **Go to Match** command or <kbd>Ctrl</kbd>+<kbd>]</kbd> locates the closing brace, if you have an opening brace selected).</span></span>
- <span data-ttu-id="5869e-200">**Dispositionsvy** Skript fönstret stöder disposition, vilket gör det möjligt att dölja eller expandera avsnitt i kod genom att klicka på plus eller minus tecken i vänstermarginalen.</span><span class="sxs-lookup"><span data-stu-id="5869e-200">**Outline view** The Script Pane supports outlining, which allows collapsing or expanding sections of code by clicking plus or minus signs in the left margin.</span></span> <span data-ttu-id="5869e-201">Du kan använda klammerparenteser eller `#region` `#endregion` taggarna och för att markera början eller slutet av ett komprimerbart avsnitt.</span><span class="sxs-lookup"><span data-stu-id="5869e-201">You can use braces or the `#region` and `#endregion` tags to mark the beginning or end of a collapsible section.</span></span> <span data-ttu-id="5869e-202">Tryck på <kbd>CTRL</kbd>M om du vill visa eller dölja alla regioner + <kbd>M</kbd>.</span><span class="sxs-lookup"><span data-stu-id="5869e-202">To expand or collapse all regions, press <kbd>Ctrl</kbd>+<kbd>M</kbd>.</span></span>
- <span data-ttu-id="5869e-203">**Dra och släpp text redigering** – Windows PowerShell ISE stöder nu text redigering med dra och släpp.</span><span class="sxs-lookup"><span data-stu-id="5869e-203">**Drag and drop text editing** - Windows PowerShell ISE now supports drag and drop text editing.</span></span> <span data-ttu-id="5869e-204">Du kan välja ett valfritt textblock och dra texten till en annan plats i redigeraren eller till-konsolen för att flytta texten.</span><span class="sxs-lookup"><span data-stu-id="5869e-204">You can select any block of text and drag that text to another location in the editor or the console to move the text.</span></span> <span data-ttu-id="5869e-205">Om du håller ned <kbd>CTRL</kbd> -tangenten medan du drar den markerade texten, kopieras texten till den nya platsen när du släpper mus knappen.</span><span class="sxs-lookup"><span data-stu-id="5869e-205">If you hold down the <kbd>Ctrl</kbd> key while you drag the selected text, when you release the mouse button the text is copied to the new location.</span></span> <span data-ttu-id="5869e-206">I den här versionen av Windows PowerShell ISE när du drar och släpper filer till Windows PowerShell ISE Windows PowerShell ISE öppnar filen.</span><span class="sxs-lookup"><span data-stu-id="5869e-206">In this version of Windows PowerShell ISE, when you drag and drop files onto Windows PowerShell ISE, Windows PowerShell ISE opens the file.</span></span>
- <span data-ttu-id="5869e-207">**Fel vid visning av parsningsfel** – parsa fel visas med röda understrykningar.</span><span class="sxs-lookup"><span data-stu-id="5869e-207">**Parse error display** - Parse errors are indicated with red underlines.</span></span> <span data-ttu-id="5869e-208">När du hovrar över ett indikerat fel visas det problem som påträffades i koden i knapp beskrivnings texten.</span><span class="sxs-lookup"><span data-stu-id="5869e-208">When you hover over an indicated error, tooltip text displays the problem that was found in the code.</span></span>
- <span data-ttu-id="5869e-209">**Zooma** – zoomnings procenten för konsolens innehåll kan ställas in med hjälp av skjutreglaget Zooma (i det nedre högra hörnet i Windows PowerShell ISE-fönstret) eller genom att ange kommandot `$psise.options.Zoom` i konsol fönstret.</span><span class="sxs-lookup"><span data-stu-id="5869e-209">**Zoom** - The zoom percentage of the console's content can be set by using the zoom slider (in the lower right corner of Windows PowerShell ISE window), or by entering the command `$psise.options.Zoom` in the Console Pane.</span></span>
- <span data-ttu-id="5869e-210">**RTF-kopiering och Inklistrings** kopiering till urklipp i Windows PowerShell ISE bevarar teckensnitt, storlek och färg information för den ursprungliga markeringen.</span><span class="sxs-lookup"><span data-stu-id="5869e-210">**Rich text copy and paste** - Copying to the clipboard in Windows PowerShell ISE preserves the font, size, and color information of the original selection.</span></span>
- <span data-ttu-id="5869e-211">**Block markering** – du kan välja ett textblock genom att hålla ned <kbd>Alt</kbd> -tangenten medan du väljer text i skript fönstret med musen, eller genom att trycka på <kbd>Alt</kbd> + <kbd>Shift</kbd>- + <kbd>pilen</kbd>.</span><span class="sxs-lookup"><span data-stu-id="5869e-211">**Block selection** - You can select a block of text by holding down the <kbd>ALT</kbd> key while selecting text in the Script Pane with your mouse, or by pressing <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>Arrow</kbd>.</span></span>

<span data-ttu-id="5869e-212">**Vilket värde medför den här ändringen?**</span><span class="sxs-lookup"><span data-stu-id="5869e-212">**What value does this change add?**</span></span>

<span data-ttu-id="5869e-213">De ytterligare redigerings funktionerna ger en mer enhetlig och kraftfull redigerings miljö.</span><span class="sxs-lookup"><span data-stu-id="5869e-213">The additional editing features provide a more consistent and powerful editing environment.</span></span>

<span data-ttu-id="5869e-214">**Vad fungerar inte på samma sätt?**</span><span class="sxs-lookup"><span data-stu-id="5869e-214">**What works differently?**</span></span>

<span data-ttu-id="5869e-215">Dessa redigerings förbättringar fanns inte i Windows PowerShell ISE 2,0.</span><span class="sxs-lookup"><span data-stu-id="5869e-215">These editing enhancements weren't present in Windows PowerShell ISE 2.0.</span></span>

## <a name="new-help-viewer-window"></a><span data-ttu-id="5869e-216">Nytt hjälp visnings fönster</span><span class="sxs-lookup"><span data-stu-id="5869e-216">New Help viewer window</span></span>

> <span data-ttu-id="5869e-217">Tillagt i PowerShell 3,0</span><span class="sxs-lookup"><span data-stu-id="5869e-217">Added in PowerShell 3.0</span></span>

<span data-ttu-id="5869e-218">Om du trycker på <kbd>F1</kbd> när markören finns i en cmdlet, eller om du har en del av en-cmdlet markerad, öppnas den nya hjälp visningen av Sammanhangs beroende hjälp om den markerade cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5869e-218">If you press <kbd>F1</kbd> when your cursor is in a cmdlet, or you have part of a cmdlet highlighted, the new Help viewer opens context-sensitive Help about the highlighted cmdlet.</span></span> <span data-ttu-id="5869e-219">**Om** du vill visa hjälp för Windows PowerShell skriver `operators` du i konsol fönstret och trycker sedan på <kbd>F1</kbd>.</span><span class="sxs-lookup"><span data-stu-id="5869e-219">To display Windows PowerShell **About** help, type `operators` in the console pane, and then press <kbd>F1</kbd>.</span></span>

<span data-ttu-id="5869e-220">Innan du använder den här funktionen kan du hämta den senaste versionen av hjälp avsnitten för Windows PowerShell från Microsofts webbplats.</span><span class="sxs-lookup"><span data-stu-id="5869e-220">Before you use this feature, download the most current version of Windows PowerShell Help topics from the Microsoft website.</span></span> <span data-ttu-id="5869e-221">Den enklaste metoden för att hämta hjälp avsnitten är att köra `Update-Help` cmdleten i konsol fönstret när du kör Windows PowerShell ISE som administratör.</span><span class="sxs-lookup"><span data-stu-id="5869e-221">The simplest method for downloading the Help topics is to run the `Update-Help` cmdlet in the Console Pane when running Windows PowerShell ISE as administrator.</span></span>

<span data-ttu-id="5869e-222">Du kan ändra var <kbd>F1</kbd> -nyckeln söker efter hjälp.</span><span class="sxs-lookup"><span data-stu-id="5869e-222">You can alter where the <kbd>F1</kbd> key looks for Help.</span></span> <span data-ttu-id="5869e-223">På menyn **verktyg** / **alternativ** på fliken **allmänna inställningar** under **andra inställningar**, kan du ange eller avmarkera kryss rutan **Använd lokalt hjälp innehåll i stället för online-innehåll**.</span><span class="sxs-lookup"><span data-stu-id="5869e-223">In the **Tools**/**Options** menu, on the **General Settings** tab, under **Other Settings**, you can set or clear the checkbox **Use local help content instead of online content**.</span></span> <span data-ttu-id="5869e-224">När det här alternativet är markerat söker klienten efter cmdlet-hjälpen i den nedladdade hjälpen i mappen moduler.</span><span class="sxs-lookup"><span data-stu-id="5869e-224">When checked, the client looks for the cmdlet Help in the downloaded Help found in the modules folder.</span></span> <span data-ttu-id="5869e-225">Om kryss rutan är avmarkerad söker klienten efter hjälp online.</span><span class="sxs-lookup"><span data-stu-id="5869e-225">If the checkbox is cleared, the client looks for help online.</span></span>

<span data-ttu-id="5869e-226">**Vilket värde medför den här ändringen?**</span><span class="sxs-lookup"><span data-stu-id="5869e-226">**What value does this change add?**</span></span>

<span data-ttu-id="5869e-227">Sammanhangs beroende hjälp utan att lämna din aktuella cmdlet eller ditt skript är en integrerad inlärnings upplevelse.</span><span class="sxs-lookup"><span data-stu-id="5869e-227">Context-sensitive Help without leaving your current cmdlet or script provides an integrated learning experience.</span></span>

<span data-ttu-id="5869e-228">**Vad fungerar inte på samma sätt?**</span><span class="sxs-lookup"><span data-stu-id="5869e-228">**What works differently?**</span></span>

<span data-ttu-id="5869e-229">Om <kbd>du</kbd> trycker på F1 i tidigare versioner av Windows PowerShell ISE öppnat hjälp filen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="5869e-229">Pressing <kbd>F1</kbd> in previous versions of Windows PowerShell ISE opened the help file on the local computer.</span></span> <span data-ttu-id="5869e-230">I Windows PowerShell ISE 3,0 och senare öppnas ett fönster som innehåller hjälpen för cmdleten som går att söka efter och som kan konfigureras.</span><span class="sxs-lookup"><span data-stu-id="5869e-230">In Windows PowerShell ISE 3.0 and later, a window opens that contains the help for the cmdlet that is searchable and configurable.</span></span> <span data-ttu-id="5869e-231">Den här hjälp versionen är ny för Windows PowerShell ISE 3,0 och uppdaterings bar hjälp är ny för Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="5869e-231">This Help experience is new for Windows PowerShell ISE 3.0, and Updatable Help is new for Windows PowerShell 3.0.</span></span>

## <a name="show-command-cmdlet"></a><span data-ttu-id="5869e-232">Visa-kommando-cmdlet</span><span class="sxs-lookup"><span data-stu-id="5869e-232">Show-Command cmdlet</span></span>

> <span data-ttu-id="5869e-233">Tillagt i PowerShell 3,0</span><span class="sxs-lookup"><span data-stu-id="5869e-233">Added in PowerShell 3.0</span></span>

<span data-ttu-id="5869e-234">Med `Show-Command` cmdleten kan du skapa eller köra en cmdlet eller funktion genom att fylla i ett grafiskt formulär.</span><span class="sxs-lookup"><span data-stu-id="5869e-234">The `Show-Command` cmdlet enables you to compose or run a cmdlet or function by filling in a graphical form.</span></span> <span data-ttu-id="5869e-235">I formuläret kan användarna arbeta med Windows PowerShell i en grafisk miljö.</span><span class="sxs-lookup"><span data-stu-id="5869e-235">The form lets users work with Windows PowerShell in a graphical environment.</span></span>
<span data-ttu-id="5869e-236">`Show-Command`aktiverar även avancerade skript för att skapa ett snabb Windows PowerShell-baserat GUI.</span><span class="sxs-lookup"><span data-stu-id="5869e-236">`Show-Command` also enables advanced scripters to create a quick Windows PowerShell-based GUI.</span></span>

<span data-ttu-id="5869e-237">**Vilket värde medför den här ändringen?**</span><span class="sxs-lookup"><span data-stu-id="5869e-237">**What value does this change add?**</span></span>

<span data-ttu-id="5869e-238">Genom att använda `Show-Command` i dina Windows PowerShell-skript kan du ge användarna en grafisk miljö som de är bekanta med.</span><span class="sxs-lookup"><span data-stu-id="5869e-238">By using `Show-Command` in your Windows PowerShell scripts, you can provide your users with the graphical environment with which they're familiar.</span></span> <span data-ttu-id="5869e-239">`Show-Command`kan även hjälpa introduktions användare att lära sig Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5869e-239">`Show-Command` can also help introductory users learn Windows PowerShell.</span></span>

<span data-ttu-id="5869e-240">**Vad fungerar inte på samma sätt?**</span><span class="sxs-lookup"><span data-stu-id="5869e-240">**What works differently?**</span></span>

<span data-ttu-id="5869e-241">`Show-Command`är New Windows PowerShell ISE 3,0.</span><span class="sxs-lookup"><span data-stu-id="5869e-241">`Show-Command` is new Windows PowerShell ISE 3.0.</span></span>

## <a name="see-also"></a><span data-ttu-id="5869e-242">Se även</span><span class="sxs-lookup"><span data-stu-id="5869e-242">See also</span></span>

<span data-ttu-id="5869e-243">Mer information om hur du använder Windows PowerShell ISE finns i [utforska Windows PowerShell Integrated Scripting Environment](../ise/exploring-the-windows-powershell-ise.md).</span><span class="sxs-lookup"><span data-stu-id="5869e-243">For more information about using Windows PowerShell ISE, see [Exploring the Windows PowerShell Integrated Scripting Environment](../ise/exploring-the-windows-powershell-ise.md).</span></span>
