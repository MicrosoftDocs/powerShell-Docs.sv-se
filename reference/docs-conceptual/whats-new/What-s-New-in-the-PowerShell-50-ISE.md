---
ms.date: 09/06/2019
keywords: PowerShell, cmdlet
title: Nyheter i PowerShell 5,0 ISE
ms.openlocfilehash: f687c409a1a4b0e6b872863e9f132f7cf5baff20
ms.sourcegitcommit: a6e54a305fdeb6482321c77da8066d2f991c93e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/15/2019
ms.locfileid: "74117515"
---
# <a name="whats-new-in-the-windows-powershell-50-ise"></a><span data-ttu-id="963d9-103">Vad är nytt i Windows PowerShell 5,0 ISE</span><span class="sxs-lookup"><span data-stu-id="963d9-103">What's New in the Windows PowerShell 5.0 ISE</span></span>

<span data-ttu-id="963d9-104">I det här avsnittet beskrivs nya och uppdaterade funktioner som har introducerats i versioner av Windows PowerShell ISE (Integrated Scripting Environment).</span><span class="sxs-lookup"><span data-stu-id="963d9-104">This topic explains the new and updated features that have been introduced in versions of Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="feature-description"></a><span data-ttu-id="963d9-105">Funktionsbeskrivning</span><span class="sxs-lookup"><span data-stu-id="963d9-105">Feature description</span></span>

<span data-ttu-id="963d9-106">Windows PowerShell ISE är ett värd program som gör det möjligt att skriva, köra och testa skript och moduler i en grafisk och intuitiv miljö.</span><span class="sxs-lookup"><span data-stu-id="963d9-106">The Windows PowerShell ISE is a host application that enables you to write, run, and test scripts and modules in a graphical and intuitive environment.</span></span> <span data-ttu-id="963d9-107">Viktiga funktioner som syntax-färgning, TABB-slutförande, visuell fel sökning, Unicode-kompatibilitet och Sammanhangs beroende hjälp ger en omfattande skript upplevelse.</span><span class="sxs-lookup"><span data-stu-id="963d9-107">Key features such as syntax-coloring, tab completion, visual debugging, Unicode compliance, and context-sensitive Help provide a rich scripting experience.</span></span>

<span data-ttu-id="963d9-108">Mer information finns i [Introduktion till Windows PowerShell ISE](../components/ise/Introducing-the-Windows-PowerShell-ISE.md).</span><span class="sxs-lookup"><span data-stu-id="963d9-108">For more information, see [Introducing the Windows PowerShell ISE](../components/ise/Introducing-the-Windows-PowerShell-ISE.md).</span></span>

<span data-ttu-id="963d9-109">I följande tabell visas de nya och ändrade funktionerna i den här versionen av Windows PowerShell ISE i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="963d9-109">The following table lists the new and changed features for this release of Windows PowerShell ISE in Windows PowerShell.</span></span>

## <a name="intellisense"></a><span data-ttu-id="963d9-110">Tillhandahåller</span><span class="sxs-lookup"><span data-stu-id="963d9-110">IntelliSense</span></span>

> <span data-ttu-id="963d9-111">Tillagt i ISE 3,0</span><span class="sxs-lookup"><span data-stu-id="963d9-111">Added in ISE 3.0</span></span>

<span data-ttu-id="963d9-112">IntelliSense är en hjälp funktion för automatisk komplettering som är en del av Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="963d9-112">IntelliSense is an automatic-completion assistance feature that is part of Windows PowerShell ISE.</span></span>
<span data-ttu-id="963d9-113">IntelliSense visar klicknings bara menyer med potentiellt matchande cmdlets, parametrar, parameter värden, filer eller mappar medan du skriver.</span><span class="sxs-lookup"><span data-stu-id="963d9-113">IntelliSense displays clickable menus of potentially matching cmdlets, parameters, parameter values, files, or folders as you type.</span></span>

<span data-ttu-id="963d9-114">**Vilket värde lägger den här ändringen till?**</span><span class="sxs-lookup"><span data-stu-id="963d9-114">**What value does this change add?**</span></span>

<span data-ttu-id="963d9-115">Med tillägget av IntelliSense är det lättare att identifiera cmdlets och syntax när du använder Windows PowerShell ISE för att skapa skript.</span><span class="sxs-lookup"><span data-stu-id="963d9-115">With the addition of IntelliSense, it's easier to discover cmdlets and syntax when you use Windows PowerShell ISE to create scripts.</span></span> <span data-ttu-id="963d9-116">Du kan också använda Windows PowerShell ISE för att lära dig Windows PowerShell medan du skapar nya skript.</span><span class="sxs-lookup"><span data-stu-id="963d9-116">You can also use Windows PowerShell ISE to learn Windows PowerShell while you create new scripts.</span></span>

<span data-ttu-id="963d9-117">**Vad fungerar annorlunda?**</span><span class="sxs-lookup"><span data-stu-id="963d9-117">**What works differently?**</span></span>

<span data-ttu-id="963d9-118">När du skriver cmdlets i Windows PowerShell ISE visas en rullnings bar och klickande meny, så att du kan bläddra och välja lämpliga kommandon.</span><span class="sxs-lookup"><span data-stu-id="963d9-118">When you type cmdlets in the Windows PowerShell ISE, a scrollable and clickable menu displays, allowing you to browse and select the appropriate commands.</span></span>

## <a name="snippets"></a><span data-ttu-id="963d9-119">kodfragment</span><span class="sxs-lookup"><span data-stu-id="963d9-119">Snippets</span></span>

> <span data-ttu-id="963d9-120">Tillagt i ISE 3,0</span><span class="sxs-lookup"><span data-stu-id="963d9-120">Added in ISE 3.0</span></span>

<span data-ttu-id="963d9-121">*Kodfragment* är korta avsnitt med Windows PowerShell-kod som du kan infoga i de skript som du skapar i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="963d9-121">*Snippets* are short sections of Windows PowerShell code that you can insert into the scripts you create in Windows PowerShell ISE.</span></span> <span data-ttu-id="963d9-122">Windows PowerShell ISE levereras med en standard uppsättning kod avsnitt.</span><span class="sxs-lookup"><span data-stu-id="963d9-122">Windows PowerShell ISE comes with a default set of snippets.</span></span> <span data-ttu-id="963d9-123">Du kan lägga till kodfragment med hjälp av `New-Snippet` cmdlet när du arbetar i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="963d9-123">You can add snippets by using the `New-Snippet` cmdlet while working in Windows PowerShell ISE.</span></span>

<span data-ttu-id="963d9-124">**Vilket värde lägger den här ändringen till?**</span><span class="sxs-lookup"><span data-stu-id="963d9-124">**What value does this change add?**</span></span>

<span data-ttu-id="963d9-125">Genom att använda kodfragment kan du snabbt sätta samman och skapa skript för att automatisera din miljö.</span><span class="sxs-lookup"><span data-stu-id="963d9-125">By using snippets, you can quickly assemble and create scripts to automate your environment.</span></span>

<span data-ttu-id="963d9-126">**Vad fungerar annorlunda?**</span><span class="sxs-lookup"><span data-stu-id="963d9-126">**What works differently?**</span></span>

<span data-ttu-id="963d9-127">Om du vill använda kodfragment i Windows PowerShell 3,0 eller senare klickar du på **Starta kodfragment**på **Redigera** -menyn eller trycker på <kbd>CTRL</kbd>+<kbd>J</kbd>.</span><span class="sxs-lookup"><span data-stu-id="963d9-127">To use snippets in Windows PowerShell 3.0 or later, on the **Edit** menu, click **Start Snippets**, or press <kbd>Ctrl</kbd>+<kbd>J</kbd>.</span></span>

## <a name="add-on-tools"></a><span data-ttu-id="963d9-128">Tilläggs verktyg</span><span class="sxs-lookup"><span data-stu-id="963d9-128">Add-on tools</span></span>

> <span data-ttu-id="963d9-129">Tillagt i PowerShell 3,0</span><span class="sxs-lookup"><span data-stu-id="963d9-129">Added in PowerShell 3.0</span></span>

<span data-ttu-id="963d9-130">Windows PowerShell ISE stöder nu tilläggs verktyg med hjälp av objekt modellen.</span><span class="sxs-lookup"><span data-stu-id="963d9-130">Windows PowerShell ISE now supports add-on tools using the object model.</span></span> <span data-ttu-id="963d9-131">Dessa tillägg är Windows Presentation Foundation-kontroller (WPF) som visas som ett lodrätt eller vågrätt fönster i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="963d9-131">These add-ons are Windows Presentation Foundation (WPF) controls that are displayed as a vertical or horizontal pane in the console.</span></span> <span data-ttu-id="963d9-132">Flera tilläggs verktyg i ett fönster visas som en tabbad kontroll.</span><span class="sxs-lookup"><span data-stu-id="963d9-132">Multiple add-on tools in a pane are displayed as a tabbed control.</span></span> <span data-ttu-id="963d9-133">Du kan också lägga till eller ta bort tilläggs verktyg som produceras av icke-Microsoft-parter.</span><span class="sxs-lookup"><span data-stu-id="963d9-133">You can also add or remove add-on tools that are produced by non-Microsoft parties.</span></span> <span data-ttu-id="963d9-134">Mer information finns i [syftet med Windows PowerShell ISE skript objekt modell](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md).</span><span class="sxs-lookup"><span data-stu-id="963d9-134">For more information, see [The Purpose of the Windows PowerShell ISE Scripting Object Model](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md).</span></span>

<span data-ttu-id="963d9-135">**Vilket värde lägger den här ändringen till?**</span><span class="sxs-lookup"><span data-stu-id="963d9-135">**What value does this change add?**</span></span>

<span data-ttu-id="963d9-136">Med tillägg kan du utöka och anpassa Windows PowerShell ISE med verktyg som lägger till funktioner och förbättrar skript upplevelsen.</span><span class="sxs-lookup"><span data-stu-id="963d9-136">Add-ons allow you to extend and customize Windows PowerShell ISE with tools that add functionality and enhance your scripting experience.</span></span>

<span data-ttu-id="963d9-137">**Vad fungerar annorlunda?**</span><span class="sxs-lookup"><span data-stu-id="963d9-137">**What works differently?**</span></span>

<span data-ttu-id="963d9-138">Windows PowerShell ISE 3,0 och senare levereras med **kommando** tillägg.</span><span class="sxs-lookup"><span data-stu-id="963d9-138">Windows PowerShell ISE 3.0 and later come with the **Commands** add-on.</span></span> <span data-ttu-id="963d9-139">Med **kommandona kommando** tillägg kan du bläddra bland cmdletar och få åtkomst till hjälp om cmdlets sida vid sida med **skript** -och **konsol** Fönstren.</span><span class="sxs-lookup"><span data-stu-id="963d9-139">The **Commands** add-on allows you to browse cmdlets, and access help about the cmdlets side-by-side with the **Script** and **Console** Panes.</span></span>

<span data-ttu-id="963d9-140">Du hittar ytterligare tillägg med hjälp av kommandot **Öppna tilläggs verktyg webbplats** på menyn **tillägg** .</span><span class="sxs-lookup"><span data-stu-id="963d9-140">Additional add-ons can be found by using the **Open Add-on Tools Website** command on the **Add-ons** menu.</span></span>

## <a name="restart-manager-and-auto-save"></a><span data-ttu-id="963d9-141">Starta om hanteraren och Spara automatiskt</span><span class="sxs-lookup"><span data-stu-id="963d9-141">Restart manager and auto-save</span></span>

> <span data-ttu-id="963d9-142">Tillagt i PowerShell 3,0</span><span class="sxs-lookup"><span data-stu-id="963d9-142">Added in PowerShell 3.0</span></span>

<span data-ttu-id="963d9-143">Windows PowerShell ISE sparar nu automatiskt de öppna skripten var två: e minut, på en annan plats.</span><span class="sxs-lookup"><span data-stu-id="963d9-143">Windows PowerShell ISE now automatically saves your open scripts every two minutes, in a separate location.</span></span> <span data-ttu-id="963d9-144">När Windows PowerShell ISE startar om efter en oväntad krasch eller omstart återställer den skript som var öppna i den senaste sessionen, även om skripten inte sparades.</span><span class="sxs-lookup"><span data-stu-id="963d9-144">When Windows PowerShell ISE restarts after an unexpected crash or reboot, it recovers scripts that were open in the last session, even if the scripts weren't saved.</span></span>

<span data-ttu-id="963d9-145">Om du vill ändra intervallet för automatisk sparande kör du följande kommando i konsol fönstret: `$psise.Options.AutoSaveMinuteInterval`.</span><span class="sxs-lookup"><span data-stu-id="963d9-145">To change the automatic saving interval, run the following command in the Console pane: `$psise.Options.AutoSaveMinuteInterval`.</span></span>

<span data-ttu-id="963d9-146">**Vilket värde lägger den här ändringen till?**</span><span class="sxs-lookup"><span data-stu-id="963d9-146">**What value does this change add?**</span></span>

<span data-ttu-id="963d9-147">Nu kan du arbeta inom Windows PowerShell ISE vet att dina öppna skript sparas automatiskt.</span><span class="sxs-lookup"><span data-stu-id="963d9-147">You can now work within Windows PowerShell ISE knowing that your open scripts are automatically saved.</span></span>

<span data-ttu-id="963d9-148">**Vad fungerar annorlunda?**</span><span class="sxs-lookup"><span data-stu-id="963d9-148">**What works differently?**</span></span>

<span data-ttu-id="963d9-149">Windows PowerShell ISE 2,0 sparar inte skripten automatiskt.</span><span class="sxs-lookup"><span data-stu-id="963d9-149">Windows PowerShell ISE 2.0 doesn't save the scripts automatically.</span></span>

## <a name="most-recently-used-list"></a><span data-ttu-id="963d9-150">Lista över senast använda</span><span class="sxs-lookup"><span data-stu-id="963d9-150">Most-recently used list</span></span>

> <span data-ttu-id="963d9-151">Tillagt i PowerShell 3,0</span><span class="sxs-lookup"><span data-stu-id="963d9-151">Added in PowerShell 3.0</span></span>

<span data-ttu-id="963d9-152">Windows PowerShell ISE har nu en lista med senast använda filer för filer.</span><span class="sxs-lookup"><span data-stu-id="963d9-152">Windows PowerShell ISE now has a most-recently used list for files.</span></span> <span data-ttu-id="963d9-153">När du öppnar en fil i Windows PowerShell ISE läggs filen till i listan över senast använda på **Arkiv** -menyn.</span><span class="sxs-lookup"><span data-stu-id="963d9-153">When you open a file in Windows PowerShell ISE, the file is added to the most-recently used list on the **File** menu.</span></span>

<span data-ttu-id="963d9-154">Om du vill ändra standardvärdet för antal filer i listan senast använda, kör du följande kommando i konsol fönstret: `$psise.Options.MruCount`.</span><span class="sxs-lookup"><span data-stu-id="963d9-154">To change the default number of files in the most-recently used list, run the following command in the Console Pane: `$psise.Options.MruCount`.</span></span>

<span data-ttu-id="963d9-155">**Vilket värde lägger den här ändringen till?**</span><span class="sxs-lookup"><span data-stu-id="963d9-155">**What value does this change add?**</span></span>

<span data-ttu-id="963d9-156">Nu kan du använda listan med senast använda listan för att enkelt komma åt dina ofta använda filer.</span><span class="sxs-lookup"><span data-stu-id="963d9-156">You can now use the most-recently used list to easily access your frequently used files.</span></span>

<span data-ttu-id="963d9-157">**Vad fungerar annorlunda?**</span><span class="sxs-lookup"><span data-stu-id="963d9-157">**What works differently?**</span></span>

<span data-ttu-id="963d9-158">Windows PowerShell ISE 2,0 har inte någon lista som du nyligen har använt.</span><span class="sxs-lookup"><span data-stu-id="963d9-158">Windows PowerShell ISE 2.0 doesn't have a most-recently used list.</span></span>

## <a name="console-pane"></a><span data-ttu-id="963d9-159">Konsol fönster</span><span class="sxs-lookup"><span data-stu-id="963d9-159">Console Pane</span></span>

> <span data-ttu-id="963d9-160">Tillagt i PowerShell 3,0</span><span class="sxs-lookup"><span data-stu-id="963d9-160">Added in PowerShell 3.0</span></span>

<span data-ttu-id="963d9-161">De separata kommando-och utdatafönstret som var tillgängliga i den första versionen av Windows PowerShell ISE har kombinerats till ett enda konsol fönster.</span><span class="sxs-lookup"><span data-stu-id="963d9-161">The separate Command and Output Panes that were available in the first release of Windows PowerShell ISE have been combined into a single Console Pane.</span></span> <span data-ttu-id="963d9-162">Konsol fönstret liknar en typisk Windows PowerShell-konsol, men den innehåller följande förbättringar:</span><span class="sxs-lookup"><span data-stu-id="963d9-162">The Console Pane is similar in function and appearance to a typical Windows PowerShell console, but it includes the following enhancements:</span></span>

- <span data-ttu-id="963d9-163">Syntax för inmatnings text (inte text), inklusive XML-syntax</span><span class="sxs-lookup"><span data-stu-id="963d9-163">Syntax coloring for input text (not output text), including XML syntax</span></span>
- <span data-ttu-id="963d9-164">Tillhandahåller</span><span class="sxs-lookup"><span data-stu-id="963d9-164">IntelliSense</span></span>
- <span data-ttu-id="963d9-165">Matchning av klammerparentes</span><span class="sxs-lookup"><span data-stu-id="963d9-165">Brace matching</span></span>
- <span data-ttu-id="963d9-166">Fel indikation</span><span class="sxs-lookup"><span data-stu-id="963d9-166">Error indication</span></span>
- <span data-ttu-id="963d9-167">Fullständigt Unicode-stöd</span><span class="sxs-lookup"><span data-stu-id="963d9-167">Full Unicode support</span></span>
- <span data-ttu-id="963d9-168"><kbd>F1</kbd> Sammanhangs beroende hjälp</span><span class="sxs-lookup"><span data-stu-id="963d9-168"><kbd>F1</kbd> context-sensitive help</span></span>
- <span data-ttu-id="963d9-169"><kbd>Ctrl</kbd>+<kbd>F1</kbd> kontext känsligt show-Command</span><span class="sxs-lookup"><span data-stu-id="963d9-169"><kbd>Ctrl</kbd>+<kbd>F1</kbd> context-sensitive Show-Command</span></span>
- <span data-ttu-id="963d9-170">Komplext skript och stöd från höger till vänster</span><span class="sxs-lookup"><span data-stu-id="963d9-170">Complex script and right-to-left support</span></span>
- <span data-ttu-id="963d9-171">Stöd för teckensnitt</span><span class="sxs-lookup"><span data-stu-id="963d9-171">Font support</span></span>
- <span data-ttu-id="963d9-172">Förhindra</span><span class="sxs-lookup"><span data-stu-id="963d9-172">Zoom</span></span>
- <span data-ttu-id="963d9-173">Linje – Välj och blockera – Välj lägen</span><span class="sxs-lookup"><span data-stu-id="963d9-173">Line-select and block-select modes</span></span>
- <span data-ttu-id="963d9-174">Bevarande av typ av innehåll på kommando raden när du trycker på <kbd>nedåtpilen</kbd> för att visa historiken i-konsolen</span><span class="sxs-lookup"><span data-stu-id="963d9-174">Preservation of typed content at the command line when you press the <kbd>UpArrow</kbd> to view history in the console</span></span>

<span data-ttu-id="963d9-175">**Vilket värde lägger den här ändringen till?**</span><span class="sxs-lookup"><span data-stu-id="963d9-175">**What value does this change add?**</span></span>

<span data-ttu-id="963d9-176">Att lägga till dessa ändringar i konsol fönstret är en skript upplevelse som är mer konsekvent med konsol gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="963d9-176">The addition of these Console Pane changes provides a scripting experience that is more consistent with the console interface.</span></span>

<span data-ttu-id="963d9-177">**Vad fungerar annorlunda?**</span><span class="sxs-lookup"><span data-stu-id="963d9-177">**What works differently?**</span></span>

<span data-ttu-id="963d9-178">Windows PowerShell ISE 2,0 har separata kommando-och utmatnings fönster.</span><span class="sxs-lookup"><span data-stu-id="963d9-178">Windows PowerShell ISE 2.0 has separate Command and Output Panes.</span></span>

## <a name="command-line-switches"></a><span data-ttu-id="963d9-179">Kommando rads växlar</span><span class="sxs-lookup"><span data-stu-id="963d9-179">Command-line switches</span></span>

> <span data-ttu-id="963d9-180">Tillagt i PowerShell 3,0</span><span class="sxs-lookup"><span data-stu-id="963d9-180">Added in PowerShell 3.0</span></span>

<span data-ttu-id="963d9-181">Om du startar Windows PowerShell ISE från kommando raden (genom att skriva **powershell_ise. exe**) kan du lägga till följande nya kommando rads växlar.</span><span class="sxs-lookup"><span data-stu-id="963d9-181">If you start Windows PowerShell ISE from the command line (by typing **powershell_ise.exe**), you can add the following new command-line switches.</span></span>

- <span data-ttu-id="963d9-182">`-NoProfile`: startar Windows PowerShell ISE utan att köra `$profile`</span><span class="sxs-lookup"><span data-stu-id="963d9-182">`-NoProfile`: Starts Windows PowerShell ISE without running `$profile`</span></span>
- <span data-ttu-id="963d9-183">`-Help`: visar ett hjälp fönster</span><span class="sxs-lookup"><span data-stu-id="963d9-183">`-Help`: Displays a Help window</span></span>
- <span data-ttu-id="963d9-184">`-mta`: börjar Windows PowerShell ISE i flertrådadt Apartment-läge.</span><span class="sxs-lookup"><span data-stu-id="963d9-184">`-mta`: Starts Windows PowerShell ISE in multithreaded apartment mode.</span></span> <span data-ttu-id="963d9-185">Standard åtgärds läget för Windows PowerShell ISE är ett entrådat Apartment-läge, eller `-sta`.</span><span class="sxs-lookup"><span data-stu-id="963d9-185">The default operation mode for Windows PowerShell ISE is single-threaded apartment mode, or `-sta`.</span></span>

<span data-ttu-id="963d9-186">**Vilket värde lägger den här ändringen till?**</span><span class="sxs-lookup"><span data-stu-id="963d9-186">**What value does this change add?**</span></span>

<span data-ttu-id="963d9-187">Genom att lägga till dessa kommando rads växlar kan du kontrol lera miljön där Windows PowerShell ISE körs.</span><span class="sxs-lookup"><span data-stu-id="963d9-187">The addition of these command-line switches allows you to control the environment in which the Windows PowerShell ISE runs.</span></span>

<span data-ttu-id="963d9-188">**Vad fungerar annorlunda?**</span><span class="sxs-lookup"><span data-stu-id="963d9-188">**What works differently?**</span></span>

<span data-ttu-id="963d9-189">Windows PowerShell ISE 2,0 känner inte igen kommando rads växlarna.</span><span class="sxs-lookup"><span data-stu-id="963d9-189">Windows PowerShell ISE 2.0 doesn't recognize these command-line switches.</span></span>

## <a name="new-editor-features"></a><span data-ttu-id="963d9-190">Nya redigerings funktioner</span><span class="sxs-lookup"><span data-stu-id="963d9-190">New editor features</span></span>

> <span data-ttu-id="963d9-191">Tillagt i PowerShell 3,0</span><span class="sxs-lookup"><span data-stu-id="963d9-191">Added in PowerShell 3.0</span></span>

<span data-ttu-id="963d9-192">Andra Windows PowerShell ISE redigerings funktioner är:</span><span class="sxs-lookup"><span data-stu-id="963d9-192">Other Windows PowerShell ISE editing features include:</span></span>

- <span data-ttu-id="963d9-193">Syntax för **XML-syntax** – Windows PowerShell ISE nu XML-syntax för färger på samma sätt som i Windows PowerShell-syntaxen.</span><span class="sxs-lookup"><span data-stu-id="963d9-193">**XML syntax coloring** - Windows PowerShell ISE now colors XML syntax in the same way as it colors Windows PowerShell syntax.</span></span>
- <span data-ttu-id="963d9-194">**Matchning av klamrar** – Windows PowerShell ISE innehåller matchning och markering av klamrar och kan användas på följande sätt: (om du till exempel använder kommandot **gå till matchning** eller <kbd>CTRL</kbd>+<kbd>]</kbd> hittar du en avslutande klammerparentes, om du har valt en inledande klammerparentes).</span><span class="sxs-lookup"><span data-stu-id="963d9-194">**Brace matching** - Windows PowerShell ISE includes brace matching and highlighting, and can be used in the following ways: (for example, using the **Go to Match** command or <kbd>Ctrl</kbd>+<kbd>]</kbd> locates the closing brace, if you have an opening brace selected).</span></span>
- <span data-ttu-id="963d9-195">**Dispositionsvy** Skript fönstret stöder disposition, vilket gör det möjligt att dölja eller expandera avsnitt i kod genom att klicka på plus eller minus tecken i vänstermarginalen.</span><span class="sxs-lookup"><span data-stu-id="963d9-195">**Outline view** The Script Pane supports outlining, which allows collapsing or expanding sections of code by clicking plus or minus signs in the left margin.</span></span> <span data-ttu-id="963d9-196">Du kan använda klammerparenteser eller taggarna `#region` och `#endregion` för att markera början eller slutet av ett komprimerbart avsnitt.</span><span class="sxs-lookup"><span data-stu-id="963d9-196">You can use braces or the `#region` and `#endregion` tags to mark the beginning or end of a collapsible section.</span></span> <span data-ttu-id="963d9-197">Om du vill visa eller dölja alla regioner trycker du på <kbd>Ctrl</kbd>+<kbd>M</kbd>.</span><span class="sxs-lookup"><span data-stu-id="963d9-197">To expand or collapse all regions, press <kbd>Ctrl</kbd>+<kbd>M</kbd>.</span></span>
- <span data-ttu-id="963d9-198">**Dra och släpp text redigering** – Windows PowerShell ISE stöder nu text redigering med dra och släpp.</span><span class="sxs-lookup"><span data-stu-id="963d9-198">**Drag and drop text editing** - Windows PowerShell ISE now supports drag and drop text editing.</span></span> <span data-ttu-id="963d9-199">Du kan välja ett valfritt textblock och dra texten till en annan plats i redigeraren eller till-konsolen för att flytta texten.</span><span class="sxs-lookup"><span data-stu-id="963d9-199">You can select any block of text and drag that text to another location in the editor or the console to move the text.</span></span> <span data-ttu-id="963d9-200">Om du håller ned <kbd>CTRL</kbd> -tangenten medan du drar den markerade texten, kopieras texten till den nya platsen när du släpper mus knappen.</span><span class="sxs-lookup"><span data-stu-id="963d9-200">If you hold down the <kbd>Ctrl</kbd> key while you drag the selected text, when you release the mouse button the text is copied to the new location.</span></span> <span data-ttu-id="963d9-201">I den här versionen av Windows PowerShell ISE när du drar och släpper filer till Windows PowerShell ISE Windows PowerShell ISE öppnar filen.</span><span class="sxs-lookup"><span data-stu-id="963d9-201">In this version of Windows PowerShell ISE, when you drag and drop files onto Windows PowerShell ISE, Windows PowerShell ISE opens the file.</span></span>
- <span data-ttu-id="963d9-202">**Fel vid visning av parsningsfel** – parsa fel visas med röda understrykningar.</span><span class="sxs-lookup"><span data-stu-id="963d9-202">**Parse error display** - Parse errors are indicated with red underlines.</span></span> <span data-ttu-id="963d9-203">När du hovrar över ett indikerat fel visas det problem som påträffades i koden i knapp beskrivnings texten.</span><span class="sxs-lookup"><span data-stu-id="963d9-203">When you hover over an indicated error, tooltip text displays the problem that was found in the code.</span></span>
- <span data-ttu-id="963d9-204">**Zooma** – zoomnings procenten för konsolens innehåll kan ställas in med hjälp av skjutreglaget Zooma (i det nedre högra hörnet i Windows PowerShell ISE-fönstret) eller genom att ange kommandot `$psise.options.Zoom` i konsol fönstret.</span><span class="sxs-lookup"><span data-stu-id="963d9-204">**Zoom** - The zoom percentage of the console's content can be set by using the zoom slider (in the lower right corner of Windows PowerShell ISE window), or by entering the command `$psise.options.Zoom` in the Console Pane.</span></span>
- <span data-ttu-id="963d9-205">**RTF-kopiering och Inklistrings** kopiering till urklipp i Windows PowerShell ISE bevarar teckensnitt, storlek och färg information för den ursprungliga markeringen.</span><span class="sxs-lookup"><span data-stu-id="963d9-205">**Rich text copy and paste** - Copying to the clipboard in Windows PowerShell ISE preserves the font, size, and color information of the original selection.</span></span>
- <span data-ttu-id="963d9-206">**Block markering** – du kan välja ett textblock genom att hålla ned <kbd>Alt</kbd> -tangenten medan du väljer text i skript fönstret med musen, eller genom att trycka på <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>pilen</kbd>.</span><span class="sxs-lookup"><span data-stu-id="963d9-206">**Block selection** - You can select a block of text by holding down the <kbd>ALT</kbd> key while selecting text in the Script Pane with your mouse, or by pressing <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>Arrow</kbd>.</span></span>

<span data-ttu-id="963d9-207">**Vilket värde lägger den här ändringen till?**</span><span class="sxs-lookup"><span data-stu-id="963d9-207">**What value does this change add?**</span></span>

<span data-ttu-id="963d9-208">De ytterligare redigerings funktionerna ger en mer enhetlig och kraftfull redigerings miljö.</span><span class="sxs-lookup"><span data-stu-id="963d9-208">The additional editing features provide a more consistent and powerful editing environment.</span></span>

<span data-ttu-id="963d9-209">**Vad fungerar annorlunda?**</span><span class="sxs-lookup"><span data-stu-id="963d9-209">**What works differently?**</span></span>

<span data-ttu-id="963d9-210">Dessa redigerings förbättringar fanns inte i Windows PowerShell ISE 2,0.</span><span class="sxs-lookup"><span data-stu-id="963d9-210">These editing enhancements weren't present in Windows PowerShell ISE 2.0.</span></span>

## <a name="new-help-viewer-window"></a><span data-ttu-id="963d9-211">Nytt hjälp visnings fönster</span><span class="sxs-lookup"><span data-stu-id="963d9-211">New Help viewer window</span></span>

> <span data-ttu-id="963d9-212">Tillagt i PowerShell 3,0</span><span class="sxs-lookup"><span data-stu-id="963d9-212">Added in PowerShell 3.0</span></span>

<span data-ttu-id="963d9-213">Om du trycker på <kbd>F1</kbd> när markören finns i en cmdlet, eller om du har en del av en-cmdlet markerad, öppnas den nya hjälp visningen av Sammanhangs beroende hjälp om den markerade cmdleten.</span><span class="sxs-lookup"><span data-stu-id="963d9-213">If you press <kbd>F1</kbd> when your cursor is in a cmdlet, or you have part of a cmdlet highlighted, the new Help viewer opens context-sensitive Help about the highlighted cmdlet.</span></span> <span data-ttu-id="963d9-214">**Om** du vill visa hjälp för Windows PowerShell skriver du `operators` i konsol fönstret och trycker sedan på <kbd>F1</kbd>.</span><span class="sxs-lookup"><span data-stu-id="963d9-214">To display Windows PowerShell **About** help, type `operators` in the console pane, and then press <kbd>F1</kbd>.</span></span>

<span data-ttu-id="963d9-215">Innan du använder den här funktionen kan du hämta den senaste versionen av hjälp avsnitten för Windows PowerShell från Microsofts webbplats.</span><span class="sxs-lookup"><span data-stu-id="963d9-215">Before you use this feature, download the most current version of Windows PowerShell Help topics from the Microsoft website.</span></span> <span data-ttu-id="963d9-216">Den enklaste metoden för att hämta hjälp avsnitten är att köra cmdleten `Update-Help` i konsol fönstret när du kör Windows PowerShell ISE som administratör.</span><span class="sxs-lookup"><span data-stu-id="963d9-216">The simplest method for downloading the Help topics is to run the `Update-Help` cmdlet in the Console Pane when running Windows PowerShell ISE as administrator.</span></span>

<span data-ttu-id="963d9-217">Du kan ändra var <kbd>F1</kbd> -nyckeln söker efter hjälp.</span><span class="sxs-lookup"><span data-stu-id="963d9-217">You can alter where the <kbd>F1</kbd> key looks for Help.</span></span> <span data-ttu-id="963d9-218">På menyn **verktyg**/**alternativ** på fliken **allmänna inställningar** under **andra inställningar**, kan du ange eller avmarkera kryss rutan **Använd lokalt hjälp innehåll i stället för online-innehåll**.</span><span class="sxs-lookup"><span data-stu-id="963d9-218">In the **Tools**/**Options** menu, on the **General Settings** tab, under **Other Settings**, you can set or clear the checkbox **Use local help content instead of online content**.</span></span> <span data-ttu-id="963d9-219">När det här alternativet är markerat söker klienten efter cmdlet-hjälpen i den nedladdade hjälpen i mappen moduler.</span><span class="sxs-lookup"><span data-stu-id="963d9-219">When checked, the client looks for the cmdlet Help in the downloaded Help found in the modules folder.</span></span> <span data-ttu-id="963d9-220">Om kryss rutan är avmarkerad söker klienten efter hjälp online.</span><span class="sxs-lookup"><span data-stu-id="963d9-220">If the checkbox is cleared, the client looks for help online.</span></span>

<span data-ttu-id="963d9-221">**Vilket värde lägger den här ändringen till?**</span><span class="sxs-lookup"><span data-stu-id="963d9-221">**What value does this change add?**</span></span>

<span data-ttu-id="963d9-222">Sammanhangs beroende hjälp utan att lämna din aktuella cmdlet eller ditt skript är en integrerad inlärnings upplevelse.</span><span class="sxs-lookup"><span data-stu-id="963d9-222">Context-sensitive Help without leaving your current cmdlet or script provides an integrated learning experience.</span></span>

<span data-ttu-id="963d9-223">**Vad fungerar annorlunda?**</span><span class="sxs-lookup"><span data-stu-id="963d9-223">**What works differently?**</span></span>

<span data-ttu-id="963d9-224">Om <kbd>du</kbd> trycker på F1 i tidigare versioner av Windows PowerShell ISE öppnat hjälp filen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="963d9-224">Pressing <kbd>F1</kbd> in previous versions of Windows PowerShell ISE opened the help file on the local computer.</span></span> <span data-ttu-id="963d9-225">I Windows PowerShell ISE 3,0 och senare öppnas ett fönster som innehåller hjälpen för cmdleten som går att söka efter och som kan konfigureras.</span><span class="sxs-lookup"><span data-stu-id="963d9-225">In Windows PowerShell ISE 3.0 and later, a window opens that contains the help for the cmdlet that is searchable and configurable.</span></span> <span data-ttu-id="963d9-226">Den här hjälp versionen är ny för Windows PowerShell ISE 3,0 och uppdaterings bar hjälp är ny för Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="963d9-226">This Help experience is new for Windows PowerShell ISE 3.0, and Updatable Help is new for Windows PowerShell 3.0.</span></span>

## <a name="show-command-cmdlet"></a><span data-ttu-id="963d9-227">Visa-kommando-cmdlet</span><span class="sxs-lookup"><span data-stu-id="963d9-227">Show-Command cmdlet</span></span>

> <span data-ttu-id="963d9-228">Tillagt i PowerShell 3,0</span><span class="sxs-lookup"><span data-stu-id="963d9-228">Added in PowerShell 3.0</span></span>

<span data-ttu-id="963d9-229">Med `Show-Command` cmdlet kan du skapa eller köra en cmdlet eller funktion genom att fylla i ett grafiskt formulär.</span><span class="sxs-lookup"><span data-stu-id="963d9-229">The `Show-Command` cmdlet enables you to compose or run a cmdlet or function by filling in a graphical form.</span></span> <span data-ttu-id="963d9-230">I formuläret kan användarna arbeta med Windows PowerShell i en grafisk miljö.</span><span class="sxs-lookup"><span data-stu-id="963d9-230">The form lets users work with Windows PowerShell in a graphical environment.</span></span>
<span data-ttu-id="963d9-231">`Show-Command` aktiverar även avancerade skript för att skapa ett snabb Windows PowerShell-baserat GUI.</span><span class="sxs-lookup"><span data-stu-id="963d9-231">`Show-Command` also enables advanced scripters to create a quick Windows PowerShell-based GUI.</span></span>

<span data-ttu-id="963d9-232">**Vilket värde lägger den här ändringen till?**</span><span class="sxs-lookup"><span data-stu-id="963d9-232">**What value does this change add?**</span></span>

<span data-ttu-id="963d9-233">Genom att använda `Show-Command` i dina Windows PowerShell-skript kan du ge användarna en grafisk miljö som de är bekanta med.</span><span class="sxs-lookup"><span data-stu-id="963d9-233">By using `Show-Command` in your Windows PowerShell scripts, you can provide your users with the graphical environment with which they're familiar.</span></span> <span data-ttu-id="963d9-234">`Show-Command` kan också hjälpa inledande användare att lära sig Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="963d9-234">`Show-Command` can also help introductory users learn Windows PowerShell.</span></span>

<span data-ttu-id="963d9-235">**Vad fungerar annorlunda?**</span><span class="sxs-lookup"><span data-stu-id="963d9-235">**What works differently?**</span></span>

<span data-ttu-id="963d9-236">`Show-Command` är nytt Windows PowerShell ISE 3,0.</span><span class="sxs-lookup"><span data-stu-id="963d9-236">`Show-Command` is new Windows PowerShell ISE 3.0.</span></span>

## <a name="see-also"></a><span data-ttu-id="963d9-237">Se även</span><span class="sxs-lookup"><span data-stu-id="963d9-237">See also</span></span>

<span data-ttu-id="963d9-238">Mer information om hur du använder Windows PowerShell ISE finns i [utforska Windows PowerShell Integrated Scripting Environment](../components/ise/exploring-the-windows-powershell-ise.md).</span><span class="sxs-lookup"><span data-stu-id="963d9-238">For more information about using Windows PowerShell ISE, see [Exploring the Windows PowerShell Integrated Scripting Environment](../components/ise/exploring-the-windows-powershell-ise.md).</span></span>
