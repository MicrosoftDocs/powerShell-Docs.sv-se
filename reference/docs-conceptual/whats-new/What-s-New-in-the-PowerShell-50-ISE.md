---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Nyheter i PowerShell 50 ISE
ms.assetid: 38648d47-7c27-4b37-a40e-ad29948519c2
ms.openlocfilehash: 2d953bc4553de7720c590304d29750b84a1ef3b2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058190"
---
# <a name="what39s-new-in-the-windows-powershell-ise"></a><span data-ttu-id="cc7a5-103">Vad&#39;nytt i Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="cc7a5-103">What&#39;s New in the Windows PowerShell ISE</span></span>
<span data-ttu-id="cc7a5-104">Det här avsnittet beskrivs nya och uppdaterade funktioner som har införts i versioner av Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="cc7a5-104">This topic explains the new and updated features that have been introduced in versions of Windows PowerShell  Integrated Scripting Environment (ISE).</span></span>

## <a name="feature-description"></a><span data-ttu-id="cc7a5-105">Funktionsbeskrivning</span><span class="sxs-lookup"><span data-stu-id="cc7a5-105">Feature description</span></span>
<span data-ttu-id="cc7a5-106">Windows PowerShell ISE är ett program som hjälper dig att skriva, köra och testa skript och moduler i en grafisk och intuitiv miljö.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-106">The Windows PowerShell ISE is a host application that enables you to write, run, and test scripts and modules in a graphical and intuitive environment.</span></span> <span data-ttu-id="cc7a5-107">Viktiga funktioner, till exempel syntaxfärgning, fliken slutförande, visual-felsökning, Unicode-efterlevnad och sammanhangsberoende hjälp ger en rik upplevelse för skript.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-107">Key features such as syntax-coloring, tab completion, visual debugging, Unicode compliance, and context-sensitive Help provide a rich scripting experience.</span></span>

<span data-ttu-id="cc7a5-108">En översikt över Windows PowerShell ISE, se [översikt över Windows PowerShell Integrated Scripting Environment](https://technet.microsoft.com/library/3c1892c2-bf84-4cb6-af26-1f453be9e671).</span><span class="sxs-lookup"><span data-stu-id="cc7a5-108">For an overview of Windows PowerShell ISE, see [Windows PowerShell Integrated Scripting Environment overview](https://technet.microsoft.com/library/3c1892c2-bf84-4cb6-af26-1f453be9e671).</span></span>

## <a name="new-and-changed-functionality-in-windows-powershell-ise"></a><span data-ttu-id="cc7a5-109">Nya och ändrade funktioner i Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="cc7a5-109">New and changed functionality in Windows PowerShell ISE</span></span>
<span data-ttu-id="cc7a5-110">I följande tabell visas de nya och ändrade funktionerna för den här versionen av Windows PowerShell ISE i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-110">The following table lists the new and changed features for this release of Windows PowerShell ISE in Windows PowerShell.</span></span>

|<span data-ttu-id="cc7a5-111">Funktion/funktionalitet</span><span class="sxs-lookup"><span data-stu-id="cc7a5-111">Feature/functionality</span></span>|<span data-ttu-id="cc7a5-112">Windows PowerShell ISE 4.0</span><span class="sxs-lookup"><span data-stu-id="cc7a5-112">Windows PowerShell ISE 4.0</span></span>|<span data-ttu-id="cc7a5-113">Windows PowerShell ISE 3.0</span><span class="sxs-lookup"><span data-stu-id="cc7a5-113">Windows PowerShell ISE 3.0</span></span>|<span data-ttu-id="cc7a5-114">Windows PowerShell ISE 2.0</span><span class="sxs-lookup"><span data-stu-id="cc7a5-114">Windows PowerShell ISE 2.0</span></span>|
|--------------------------|-----------------------------------------------|-----------------------------------------------|-----------------------------------------------|
|<span data-ttu-id="cc7a5-115">**[IntelliSense](#intellisense)**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-115">**[IntelliSense](#intellisense)**</span></span>|<span data-ttu-id="cc7a5-116">X</span><span class="sxs-lookup"><span data-stu-id="cc7a5-116">X</span></span>|<span data-ttu-id="cc7a5-117">X</span><span class="sxs-lookup"><span data-stu-id="cc7a5-117">X</span></span>||
|<span data-ttu-id="cc7a5-118">**[Kodfragment](#snippets)**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-118">**[Snippets](#snippets)**</span></span>|<span data-ttu-id="cc7a5-119">X</span><span class="sxs-lookup"><span data-stu-id="cc7a5-119">X</span></span>|<span data-ttu-id="cc7a5-120">X</span><span class="sxs-lookup"><span data-stu-id="cc7a5-120">X</span></span>||
|<span data-ttu-id="cc7a5-121">**[Tilläggsverktyg](#add-on-tools)**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-121">**[Add-on Tools](#add-on-tools)**</span></span>|<span data-ttu-id="cc7a5-122">X</span><span class="sxs-lookup"><span data-stu-id="cc7a5-122">X</span></span>|<span data-ttu-id="cc7a5-123">X</span><span class="sxs-lookup"><span data-stu-id="cc7a5-123">X</span></span>||
|<span data-ttu-id="cc7a5-124">**[Starta om Manager och spara automatiskt](#restart-manager-and-auto-save)**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-124">**[Restart Manager and Auto-save](#restart-manager-and-auto-save)**</span></span>|<span data-ttu-id="cc7a5-125">X</span><span class="sxs-lookup"><span data-stu-id="cc7a5-125">X</span></span>|<span data-ttu-id="cc7a5-126">X</span><span class="sxs-lookup"><span data-stu-id="cc7a5-126">X</span></span>||
|<span data-ttu-id="cc7a5-127">**[Lista över senast använda](#most-recently-used-list)**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-127">**[Most-recently used list](#most-recently-used-list)**</span></span>|<span data-ttu-id="cc7a5-128">X</span><span class="sxs-lookup"><span data-stu-id="cc7a5-128">X</span></span>|<span data-ttu-id="cc7a5-129">X</span><span class="sxs-lookup"><span data-stu-id="cc7a5-129">X</span></span>||
|<span data-ttu-id="cc7a5-130">**[Konsolfönstret](#console-pane)**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-130">**[Console Pane](#console-pane)**</span></span>|<span data-ttu-id="cc7a5-131">X</span><span class="sxs-lookup"><span data-stu-id="cc7a5-131">X</span></span>|<span data-ttu-id="cc7a5-132">X</span><span class="sxs-lookup"><span data-stu-id="cc7a5-132">X</span></span>||
|<span data-ttu-id="cc7a5-133">**[Kommandoradsväxlar](#command-line-switches)**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-133">**[Command-line switches](#command-line-switches)**</span></span>|<span data-ttu-id="cc7a5-134">X</span><span class="sxs-lookup"><span data-stu-id="cc7a5-134">X</span></span>|<span data-ttu-id="cc7a5-135">X</span><span class="sxs-lookup"><span data-stu-id="cc7a5-135">X</span></span>||
|<span data-ttu-id="cc7a5-136">**[Nya funktioner i Redigeraren](#new-editor-features)**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-136">**[New editor features](#new-editor-features)**</span></span>|<span data-ttu-id="cc7a5-137">X</span><span class="sxs-lookup"><span data-stu-id="cc7a5-137">X</span></span>|<span data-ttu-id="cc7a5-138">X</span><span class="sxs-lookup"><span data-stu-id="cc7a5-138">X</span></span>||
|<span data-ttu-id="cc7a5-139">**[Nya visningsprogrammet hjälpfönstret](#new-help-viewer-window)**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-139">**[New Help viewer window](#new-help-viewer-window)**</span></span>|<span data-ttu-id="cc7a5-140">X</span><span class="sxs-lookup"><span data-stu-id="cc7a5-140">X</span></span>|<span data-ttu-id="cc7a5-141">X</span><span class="sxs-lookup"><span data-stu-id="cc7a5-141">X</span></span>||
|<span data-ttu-id="cc7a5-142">**[Visa-Command-cmdlet](#show-command-cmdlet)**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-142">**[Show-Command cmdlet](#show-command-cmdlet)**</span></span>|<span data-ttu-id="cc7a5-143">X</span><span class="sxs-lookup"><span data-stu-id="cc7a5-143">X</span></span>|<span data-ttu-id="cc7a5-144">X</span><span class="sxs-lookup"><span data-stu-id="cc7a5-144">X</span></span>||

### <a name="intellisense"></a><span data-ttu-id="cc7a5-145">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="cc7a5-145">IntelliSense</span></span>
<span data-ttu-id="cc7a5-146">**Har lagts till i ISE 3.0**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-146">**Added in ISE 3.0**</span></span>

<span data-ttu-id="cc7a5-147">IntelliSense är en funktion för automatisk komplettering hjälp som ingår i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-147">IntelliSense is an automatic-completion assistance feature that is part of Windows PowerShell ISE.</span></span> <span data-ttu-id="cc7a5-148">IntelliSense visar klickbara menyer av potentiellt matchande cmdletar, parametrar, parametervärden, filer eller mappar som du skriver.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-148">IntelliSense displays clickable menus of potentially matching cmdlets, parameters, parameter values, files, or folders as you type.</span></span>

<span data-ttu-id="cc7a5-149">**Vilket värde medför den här ändringen?**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-149">**What value does this change add?**</span></span>

<span data-ttu-id="cc7a5-150">Med IntelliSense dessutom är det lättare att upptäcka cmdlet: ar och syntax när du använder Windows PowerShell ISE för att skapa skript.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-150">With the addition of IntelliSense, it is easier to discover cmdlets and syntax when you use Windows PowerShell ISE to create scripts.</span></span> <span data-ttu-id="cc7a5-151">Du kan också använda Windows PowerShell ISE för att lära dig Windows PowerShell när du skapar nya skript.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-151">You can also use Windows PowerShell ISE to learn Windows PowerShell while you create new scripts.</span></span>

<span data-ttu-id="cc7a5-152">**Vad fungerar annorlunda?**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-152">**What works differently?**</span></span>

<span data-ttu-id="cc7a5-153">När du skriver cmdlets i Windows PowerShell ISE 3.0 eller senare, visas en meny för bläddringsbara och klickbara så att du kan bläddra och väljer sedan lämpliga kommandon.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-153">When you type cmdlets in the Windows PowerShell ISE 3.0 or later, a scrollable and clickable menu displays, allowing you to browse and select the appropriate commands.</span></span>

### <a name="snippets"></a><span data-ttu-id="cc7a5-154">Kodfragment</span><span class="sxs-lookup"><span data-stu-id="cc7a5-154">Snippets</span></span>
<span data-ttu-id="cc7a5-155">**Har lagts till i ISE 3.0**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-155">**Added in ISE 3.0**</span></span>

<span data-ttu-id="cc7a5-156">*Kodfragment* är korta avsnitt av Windows PowerShell-kod som du kan lägga till i de skript som du skapar i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-156">*Snippets* are short sections of Windows PowerShell code that you can insert into the scripts you create in Windows PowerShell ISE.</span></span> <span data-ttu-id="cc7a5-157">Windows PowerShell ISE levereras med en standarduppsättning med kodfragment.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-157">Windows PowerShell ISE comes with a default set of snippets.</span></span> <span data-ttu-id="cc7a5-158">Du kan lägga till kodfragment med hjälp av den **New-kodfragment** cmdlet när du arbetar i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-158">You can add snippets by using the **New-Snippet** cmdlet while working in Windows PowerShell ISE.</span></span>

<span data-ttu-id="cc7a5-159">**Vilket värde medför den här ändringen?**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-159">**What value does this change add?**</span></span>

<span data-ttu-id="cc7a5-160">Du kan snabbt Assemblera och skapa skript för att automatisera din miljö genom att använda kodfragment.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-160">By using snippets, you can quickly assemble and create scripts to automate your environment.</span></span>

<span data-ttu-id="cc7a5-161">**Vad fungerar annorlunda?**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-161">**What works differently?**</span></span>

<span data-ttu-id="cc7a5-162">Att använda kodfragment i Windows PowerShell 3.0 eller senare måste den **redigera** -menyn klickar du på **starta kodfragment**, eller tryck på **Ctrl-J**.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-162">To use snippets in Windows PowerShell 3.0 or later, on the **Edit** menu, click **Start Snippets**, or press **Ctrl-J**.</span></span>

### <a name="add-on-tools"></a><span data-ttu-id="cc7a5-163">Tilläggsverktyg</span><span class="sxs-lookup"><span data-stu-id="cc7a5-163">Add-on tools</span></span>
<span data-ttu-id="cc7a5-164">**Har lagts till i PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-164">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="cc7a5-165">Windows PowerShell ISE har nu stöd för tilläggsverktyg som är Windows Presentation Foundation (WPF)-kontroller som har lagts till med hjälp av objektmodellen.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-165">Windows PowerShell ISE now supports add-on tools, which are Windows Presentation Foundation (WPF) controls that are added by using the object model.</span></span> <span data-ttu-id="cc7a5-166">Tilläggsverktyg kan visas som en lodrät eller vågrät rutan i konsolen.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-166">Add-on tools can be displayed as a vertical or horizontal pane in the console.</span></span> <span data-ttu-id="cc7a5-167">Flera tilläggsverktyg i ett fönster visas som en flikar kontroll.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-167">Multiple add-on tools in a pane are displayed as a tabbed control.</span></span> <span data-ttu-id="cc7a5-168">Du kan också lägga till eller ta bort tilläggsverktyg som genereras av Microsoft-anknutna parter.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-168">You can also add or remove add-on tools that are produced by non-Microsoft parties.</span></span> <span data-ttu-id="cc7a5-169">Läs mer om hur du importerar eller ta bort tilläggsverktyg [Windows PowerShell ISE-åtgärder](https://technet.microsoft.com/library/cc732148.aspx).</span><span class="sxs-lookup"><span data-stu-id="cc7a5-169">For more information about how to import or remove add-on tools, see [Windows PowerShell ISE Operations](https://technet.microsoft.com/library/cc732148.aspx).</span></span>

<span data-ttu-id="cc7a5-170">**Vilket värde medför den här ändringen?**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-170">**What value does this change add?**</span></span>

<span data-ttu-id="cc7a5-171">Tillägg kan du utöka och anpassa Windows PowerShell ISE med verktyg som kan förbättra din upplevelse med skript eller lägga till funktioner i Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-171">Add-ons allow you to extend and customize Windows PowerShell ISE with tools that can enhance your scripting experience or add functionality to Windows PowerShell ISE.</span></span>

<span data-ttu-id="cc7a5-172">**Vad fungerar annorlunda?**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-172">**What works differently?**</span></span>

<span data-ttu-id="cc7a5-173">Windows PowerShell ISE 3.0 och senare levereras med den **kommandon** tillägg.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-173">Windows PowerShell ISE 3.0 and later come with the **Commands** add-on.</span></span> <span data-ttu-id="cc7a5-174">Den **kommandon** tillägg kan du bläddra cmdletar och få åtkomst till hjälp om de cmdlets sida vid sidan med de **skriptet** och **konsolen** fönster.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-174">The **Commands** add-on allows you to browse cmdlets, and access help about the cmdlets side-by-side with the **Script** and **Console** Panes.</span></span>

<span data-ttu-id="cc7a5-175">Ytterligare tillägg kan hittas genom att använda den **öppen tillägg verktyg webbplats** på den **tillägg** menyn.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-175">Additional add-ons can be found by using the **Open Add-on Tools Website** command on the **Add-ons** menu.</span></span>

### <a name="restart-manager-and-auto-save"></a><span data-ttu-id="cc7a5-176">Starta om manager och spara automatiskt</span><span class="sxs-lookup"><span data-stu-id="cc7a5-176">Restart manager and auto-save</span></span>
<span data-ttu-id="cc7a5-177">**Har lagts till i PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-177">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="cc7a5-178">Windows PowerShell ISE nu sparas automatiskt skripten öppna varannan minut, på en annan plats.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-178">Windows PowerShell ISE now automatically saves your open scripts every two minutes, in a separate location.</span></span>  <span data-ttu-id="cc7a5-179">Om Windows PowerShell ISE slutar fungera eller om operativsystemet startas när Windows PowerShell ISE har startats om, återställs det öppna skript som har på den senaste sessionen även om skripten inte sparades.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-179">If Windows PowerShell ISE stops working, or if the operating system is restarted, after Windows PowerShell ISE restarts, it recovers scripts that were open in the last session, even if the scripts were not saved.</span></span>

<span data-ttu-id="cc7a5-180">Om du vill ändra intervall för automatisk sparar, kör du följande kommando i konsolfönstret: **$psise. Options.AutoSaveMinuteInterval**.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-180">To change the automatic saving interval, run the following command in the Console pane: **$psise.Options.AutoSaveMinuteInterval**.</span></span>

<span data-ttu-id="cc7a5-181">**Vilket värde medför den här ändringen?**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-181">**What value does this change add?**</span></span>

<span data-ttu-id="cc7a5-182">Nu kan du arbeta i Windows PowerShell ISE att känna till att öppna skripten sparas automatiskt i händelse av en oväntad omstart.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-182">You can now work within Windows PowerShell ISE knowing that your open scripts are automatically saved in the event of an unexpected restart.</span></span>

<span data-ttu-id="cc7a5-183">**Vad fungerar annorlunda?**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-183">**What works differently?**</span></span>

<span data-ttu-id="cc7a5-184">Windows PowerShell ISE 2.0 sparas inte skripten automatiskt i händelse av en omstart.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-184">Windows PowerShell ISE 2.0 does not save the scripts automatically in the event of a restart.</span></span>

### <a name="most-recently-used-list"></a><span data-ttu-id="cc7a5-185">Lista över senast använda</span><span class="sxs-lookup"><span data-stu-id="cc7a5-185">Most-recently used list</span></span>
<span data-ttu-id="cc7a5-186">**Har lagts till i PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-186">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="cc7a5-187">Windows PowerShell ISE har nu en senast använda lista för filer.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-187">Windows PowerShell ISE now has a most-recently used list for files.</span></span> <span data-ttu-id="cc7a5-188">När du öppnar en fil i Windows PowerShell ISE filen läggs till listan över senast använda på den **filen** menyn.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-188">When you open a file in Windows PowerShell ISE, the file is added to the most-recently used list on the **File** menu.</span></span>

<span data-ttu-id="cc7a5-189">Om du vill ändra standardvärdet för antal filer i listan över senast använda, kör du följande kommando i konsolfönstret: **$psise. Options.MruCount**.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-189">To change the default number of files in the most-recently used list, run the following command in the Console Pane: **$psise.Options.MruCount**.</span></span>

<span data-ttu-id="cc7a5-190">**Vilket värde medför den här ändringen?**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-190">**What value does this change add?**</span></span>

<span data-ttu-id="cc7a5-191">Du kan nu använda listan över senast använda för att enkelt komma åt dina vanliga filer.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-191">You can now use the most-recently used list to easily access your frequently-used files.</span></span>

<span data-ttu-id="cc7a5-192">**Vad fungerar annorlunda?**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-192">**What works differently?**</span></span>

<span data-ttu-id="cc7a5-193">Windows PowerShell ISE 2.0 har inte en senast använda lista.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-193">Windows PowerShell ISE 2.0 does not have a most-recently used list.</span></span>

### <a name="console-pane"></a><span data-ttu-id="cc7a5-194">Konsolfönstret</span><span class="sxs-lookup"><span data-stu-id="cc7a5-194">Console Pane</span></span>
<span data-ttu-id="cc7a5-195">**Har lagts till i PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-195">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="cc7a5-196">Separata kommandot och utdata-fönster som var tillgängliga i den första versionen av Windows PowerShell ISE har nu kombinerats till en enda konsolfönstret.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-196">The separate Command and Output Panes that were available in the first release of Windows PowerShell ISE have been combined into a single Console Pane.</span></span> <span data-ttu-id="cc7a5-197">Konsolfönstret är liknande funktion och utseende i en typisk Windows PowerShell-konsol, men den innehåller följande förbättringar (de flesta är beskrivs i det här avsnittet).</span><span class="sxs-lookup"><span data-stu-id="cc7a5-197">The Console Pane is similar in function and appearance to a typical Windows PowerShell console, but it includes the following enhancements (most are described in this topic).</span></span>

- <span data-ttu-id="cc7a5-198">Syntaxfärgning för indata-text (inte returnerar text), inklusive XML-syntax</span><span class="sxs-lookup"><span data-stu-id="cc7a5-198">Syntax coloring for input text (not output text), including XML syntax</span></span>

- <span data-ttu-id="cc7a5-199">IntelliSense</span><span class="sxs-lookup"><span data-stu-id="cc7a5-199">IntelliSense</span></span>

- <span data-ttu-id="cc7a5-200">Klammerparentes matchar</span><span class="sxs-lookup"><span data-stu-id="cc7a5-200">Brace matching</span></span>

- <span data-ttu-id="cc7a5-201">Fel-uppgift</span><span class="sxs-lookup"><span data-stu-id="cc7a5-201">Error indication</span></span>

- <span data-ttu-id="cc7a5-202">Fullständigt stöd för Unicode</span><span class="sxs-lookup"><span data-stu-id="cc7a5-202">Full Unicode support</span></span>

- <span data-ttu-id="cc7a5-203">**F1** sammanhangsberoende hjälp</span><span class="sxs-lookup"><span data-stu-id="cc7a5-203">**F1** context-sensitive help</span></span>

- <span data-ttu-id="cc7a5-204">**CTRL + F1** sammanhangsberoende visningskommandot</span><span class="sxs-lookup"><span data-stu-id="cc7a5-204">**Ctrl+F1** context-sensitive Show-Command</span></span>

- <span data-ttu-id="cc7a5-205">Komplicerade skriftspråk och stöd för höger-till-vänster</span><span class="sxs-lookup"><span data-stu-id="cc7a5-205">Complex script and right-to-left support</span></span>

- <span data-ttu-id="cc7a5-206">Stöd för teckensnitt</span><span class="sxs-lookup"><span data-stu-id="cc7a5-206">Font support</span></span>

- <span data-ttu-id="cc7a5-207">Zooma</span><span class="sxs-lookup"><span data-stu-id="cc7a5-207">Zoom</span></span>

- <span data-ttu-id="cc7a5-208">Rad-Välj och blockera väljer lägen</span><span class="sxs-lookup"><span data-stu-id="cc7a5-208">Line-select and block-select modes</span></span>

- <span data-ttu-id="cc7a5-209">Bevara skrivet innehåll på kommandoraden när du trycker på den **upp** pilen för att visa historik i konsolen</span><span class="sxs-lookup"><span data-stu-id="cc7a5-209">Preservation of typed content at the command line when you press the **Up** arrow to view history in the console</span></span>

<span data-ttu-id="cc7a5-210">**Vilket värde medför den här ändringen?**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-210">**What value does this change add?**</span></span>

<span data-ttu-id="cc7a5-211">Tillägg av ändringarna konsolfönstret är det skript som är mer konsekvent med gränssnittet konsolen.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-211">The addition of these Console Pane changes provides a scripting experience that is more consistent with the console interface.</span></span>

<span data-ttu-id="cc7a5-212">**Vad fungerar annorlunda?**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-212">**What works differently?**</span></span>

<span data-ttu-id="cc7a5-213">Windows PowerShell ISE 2.0 har separata kommandot och utdata-fönster.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-213">Windows PowerShell ISE 2.0 has separate Command and Output Panes.</span></span>

### <a name="command-line-switches"></a><span data-ttu-id="cc7a5-214">Kommandoradsväxlar</span><span class="sxs-lookup"><span data-stu-id="cc7a5-214">Command-line switches</span></span>
<span data-ttu-id="cc7a5-215">**Har lagts till i PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-215">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="cc7a5-216">Om du startar Windows PowerShell ISE från kommandoraden (genom att skriva **powershell_ise.exe**), kan du lägga till följande nya kommandoradsväxlar.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-216">If you start Windows PowerShell ISE from the command line (by typing **powershell_ise.exe**), you can add the following new command-line switches.</span></span>

- <span data-ttu-id="cc7a5-217">*-NoProfile*: Startar Windows PowerShell ISE utan att köra **$profile**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-217">*-NoProfile*: Starts Windows PowerShell ISE without running **$profile**</span></span>

- <span data-ttu-id="cc7a5-218">*-Hjälpa*: Visar en Hjälp-fönstret</span><span class="sxs-lookup"><span data-stu-id="cc7a5-218">*-Help*: Displays a Help window</span></span>

- <span data-ttu-id="cc7a5-219">*-mta*: Startar Windows PowerShell ISE i flertrådat lägenhetsnummer läge.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-219">*-mta*: Starts Windows PowerShell ISE in multithreaded apartment mode.</span></span> <span data-ttu-id="cc7a5-220">Standardläget för åtgärden för Windows PowerShell ISE är flertrådade läge eller *- sta*.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-220">The default operation mode for Windows PowerShell ISE is single-threaded apartment mode, or *-sta*.</span></span>

<span data-ttu-id="cc7a5-221">**Vilket värde medför den här ändringen?**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-221">**What value does this change add?**</span></span>

<span data-ttu-id="cc7a5-222">Tillägget av dessa kan du kontrollera miljön där Windows PowerShell ISE körs.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-222">The addition of these command-line switches allows you to control the environment in which the Windows PowerShell ISE runs.</span></span>

<span data-ttu-id="cc7a5-223">**Vad fungerar annorlunda?**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-223">**What works differently?**</span></span>

<span data-ttu-id="cc7a5-224">Windows PowerShell ISE 2.0 känner inte dessa kommandoradsväxlar.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-224">Windows PowerShell ISE 2.0 does not recognize these command-line switches.</span></span>

### <a name="new-editor-features"></a><span data-ttu-id="cc7a5-225">Nya funktioner i Redigeraren</span><span class="sxs-lookup"><span data-stu-id="cc7a5-225">New editor features</span></span>
<span data-ttu-id="cc7a5-226">**Har lagts till i PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-226">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="cc7a5-227">Andra funktioner för redigering av Windows PowerShell ISE är:</span><span class="sxs-lookup"><span data-stu-id="cc7a5-227">Other Windows PowerShell ISE editing features include:</span></span>

- <span data-ttu-id="cc7a5-228">**XML-syntaxfärgning**Windows PowerShell ISE färger nu XML-syntaxen på samma sätt som den färger Windows PowerShell-syntax.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-228">**XML syntax coloring**Windows PowerShell ISE now colors XML syntax in the same way as it colors Windows PowerShell syntax.</span></span>

- <span data-ttu-id="cc7a5-229">**Klammerparentes matchar** Windows PowerShell ISE innehåller klammerparentes matchar och markering och kan användas på följande sätt: (till exempel med hjälp av den **går att matcha** kommando eller **Ctrl +]** hittar den klammerparentes, om du har en inledande klammerparentesen valt).</span><span class="sxs-lookup"><span data-stu-id="cc7a5-229">**Brace matching** Windows PowerShell ISE includes brace matching and highlighting, and can be used in the following ways: (for example, using the **Go to Match** command or **Ctrl + ]** locates the closing brace, if you have an opening brace selected).</span></span>

- <span data-ttu-id="cc7a5-230">**Beskriver visa** i skriptfönstret stöder disposition, vilket gör att dölja eller expandera avsnitt med kod genom att klicka på plus eller minus loggar i vänster marginal.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-230">**Outline view** The Script Pane supports outlining, which allows collapsing or expanding sections of code by clicking plus or minus signs in the left margin.</span></span> <span data-ttu-id="cc7a5-231">Du kan använda klammerparenteser eller **#region** och **#endregion** taggar om du vill markera början eller slutet av ett komprimerbart avsnitt.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-231">You can use braces or the **#region** and **#endregion** tags to mark the beginning or end of a collapsible section.</span></span> <span data-ttu-id="cc7a5-232">Om du vill visa eller dölja alla regioner, trycker du på **Ctrl + M**.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-232">To expand or collapse all regions, press **Ctrl + M**.</span></span>

- <span data-ttu-id="cc7a5-233">**Dra och släpp textredigering**Windows PowerShell ISE nu har stöd för dra och släpp textredigering.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-233">**Drag and drop text editing**Windows PowerShell ISE now supports drag and drop text editing.</span></span> <span data-ttu-id="cc7a5-234">Du kan markera alla textblock och dra texten till en annan plats i redigeraren eller konsolen för att flytta texten.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-234">You can select any block of text and drag that text to another location in the editor or the console to move the text.</span></span> <span data-ttu-id="cc7a5-235">Om du håller ned Ctrl-tangenten medan du drar den markerade texten när du släpper musknappen har texten kopierats till den nya platsen.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-235">If you hold down the Ctrl key while you drag the selected text, when you release the mouse button the text is copied to the new location.</span></span> <span data-ttu-id="cc7a5-236">I den här versionen av Windows PowerShell ISE, samt den tidigare versionen av Windows PowerShell ISE öppnar Windows PowerShell ISE filen när du drar och släpper filer till Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-236">In this version of Windows PowerShell ISE, as well as the previous version of Windows PowerShell ISE, when you drag and drop files onto Windows PowerShell ISE, Windows PowerShell ISE opens the file.</span></span>

- <span data-ttu-id="cc7a5-237">**Parsa fel visas** parsningsfel anges med röd understrykning.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-237">**Parse error display** Parse errors are indicated with red underlines.</span></span> <span data-ttu-id="cc7a5-238">När du hovrar över ett angivet fel visar Knappbeskrivningstext problemet som hittades i koden.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-238">When you hover over an indicated error, tooltip text displays the problem that was found in the code.</span></span>

- <span data-ttu-id="cc7a5-239">**Zooma** zoomning procentandelen konsolens innehåll kan anges med hjälp av skjutreglaget (i det nedre högra hörnet av Windows PowerShell ISE-fönster) eller genom att ange kommandot **$psise.options.Zoom** i konsolfönstret.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-239">**Zoom** The zoom percentage of the console's content can be set by using the zoom slider (in the lower right corner of Windows PowerShell ISE window), or by entering the command **$psise.options.Zoom** in the Console Pane.</span></span>

- <span data-ttu-id="cc7a5-240">**Rich text kopiera och klistra in** kopiera till Urklipp i Windows PowerShell ISE bevarar teckensnitt, storlek och färginformation för den ursprungliga markeringen.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-240">**Rich text copy and paste** Copying to the clipboard in Windows PowerShell ISE preserves the font, size, and color information of the original selection.</span></span>

- <span data-ttu-id="cc7a5-241">**Blockera val av** du kan välja ett textblock genom att hålla ned ALT-tangenten medan du markerar text i skriptfönstret med musen eller genom att trycka på **Alt + Skift + pil**.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-241">**Block selection** You can select a block of text by holding down the ALT key while selecting text in the Script Pane with your mouse, or by pressing **Alt+Shift+Arrow**.</span></span>

<span data-ttu-id="cc7a5-242">**Vilket värde medför den här ändringen?**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-242">**What value does this change add?**</span></span>

<span data-ttu-id="cc7a5-243">Ytterligare funktioner för redigering ger en mer enhetlig och kraftfulla Kodredigering.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-243">The additional editing features provide a more consistent and powerful editing environment.</span></span>

<span data-ttu-id="cc7a5-244">**Vad fungerar annorlunda?**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-244">**What works differently?**</span></span>

<span data-ttu-id="cc7a5-245">Dessa förbättringar av redigering fanns inte i Windows PowerShell ISE 2.0.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-245">These editing enhancements were not present in Windows PowerShell ISE 2.0.</span></span>

### <a name="new-help-viewer-window"></a><span data-ttu-id="cc7a5-246">Nya visningsprogrammet hjälpfönstret</span><span class="sxs-lookup"><span data-stu-id="cc7a5-246">New Help viewer window</span></span>
<span data-ttu-id="cc7a5-247">**Har lagts till i PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-247">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="cc7a5-248">Om du trycker på **F1** när markören är i en cmdlet, eller du har en del av en cmdlet markerat, nya hjälpprogrammet öppnas sammanhangsberoende hjälp om cmdleten markerade.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-248">If you press **F1** when your cursor is in a cmdlet, or you have part of a cmdlet highlighted, the new Help viewer opens context-sensitive Help about the highlighted cmdlet.</span></span> <span data-ttu-id="cc7a5-249">Visa Windows PowerShell om hjälp, skriva **operatörer** i konsolfönstret och tryck sedan på **F1**.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-249">To display Windows PowerShell About help, type  **operators** in the console pane, and then press **F1**.</span></span>

<span data-ttu-id="cc7a5-250">Innan du använder den här funktionen kan du ladda ned den senaste versionen av Windows PowerShell-hjälpen från Microsofts webbplats.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-250">Before you use this feature, download the most current version of Windows PowerShell Help topics from the Microsoft website.</span></span> <span data-ttu-id="cc7a5-251">Den enklaste metoden för att ladda ned hjälpavsnitten är att köra den **Update-Help** cmdlet i konsolfönstret när du kör Windows PowerShell ISE som administratör.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-251">The simplest method for downloading the Help topics is to run the **Update-Help** cmdlet in the Console Pane when running Windows PowerShell ISE as administrator.</span></span>

<span data-ttu-id="cc7a5-252">Du kan ändra var den **F1** nyckeln ser ut för att få hjälp.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-252">You can alter where the **F1** key looks for Help.</span></span> <span data-ttu-id="cc7a5-253">I den **verktyg**/**alternativ** menyn på den **allmänna inställningar** fliken, under **andra inställningar**, du kan ange eller ta bort den kryssrutan **använda lokala hjälpinnehållet i stället för onlineinnehåll**.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-253">In the **Tools**/**Options** menu, on the **General Settings** tab, under **Other Settings**, you can set or clear the checkbox **Use local help content instead of online content**.</span></span> <span data-ttu-id="cc7a5-254">Om du söker klienten efter cmdleten hjälp i hämtade hjälpen finns i modulmappen.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-254">If checked, then the client looks for the cmdlet Help in the downloaded Help found in the modules folder.</span></span>  <span data-ttu-id="cc7a5-255">Om kryssrutan är avmarkerad försvinner söker klienten på TechNet-biblioteket för cmdlet-hjälpen.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-255">If the checkbox is cleared, then the client looks on the TechNet library for the cmdlet help.</span></span>

<span data-ttu-id="cc7a5-256">**Vilket värde medför den här ändringen?**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-256">**What value does this change add?**</span></span>

<span data-ttu-id="cc7a5-257">Sammanhangsberoende hjälp utan att lämna din aktuella cmdlet eller ett skript ger en sömlös inlärningsupplevelse.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-257">Context-sensitive Help without leaving your current cmdlet or script provides a seamless learning experience.</span></span>

<span data-ttu-id="cc7a5-258">**Vad fungerar annorlunda?**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-258">**What works differently?**</span></span>

<span data-ttu-id="cc7a5-259">Om du trycker på F1 i tidigare versioner av Windows PowerShell ISE öppnas hjälpfilen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-259">Pressing F1 in previous versions of Windows PowerShell ISE opened the help file on the local computer.</span></span> <span data-ttu-id="cc7a5-260">I Windows PowerShell ISE 3.0 och senare, öppnas ett fönster som innehåller hjälpen för cmdlet: en som är sökbart och kan konfigureras.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-260">In Windows PowerShell ISE 3.0 and later, a window opens that contains the help for the cmdlet that is searchable and configurable.</span></span> <span data-ttu-id="cc7a5-261">Den här hjälpfunktionen är nytt för Windows PowerShell ISE 3.0 och uppdateringsbar hjälp är nytt för Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-261">This Help experience is new for Windows PowerShell ISE 3.0, and Updatable Help is new for Windows PowerShell 3.0.</span></span>

### <a name="show-command-cmdlet"></a><span data-ttu-id="cc7a5-262">Visa-Command-cmdlet</span><span class="sxs-lookup"><span data-stu-id="cc7a5-262">Show-Command cmdlet</span></span>
<span data-ttu-id="cc7a5-263">**Har lagts till i PowerShell 3.0**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-263">**Added in PowerShell 3.0**</span></span>

<span data-ttu-id="cc7a5-264">Den **visningskommandot** kan du skapa eller kör en cmdlet eller funktion genom att fylla i en grafisk form.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-264">The **Show-Command** cmdlet enables you to compose or run a cmdlet or function by filling in a graphical form.</span></span> <span data-ttu-id="cc7a5-265">Formuläret kan användarna arbeta med Windows PowerShell i en grafisk miljö.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-265">The form lets users work with Windows PowerShell in a graphical environment.</span></span> <span data-ttu-id="cc7a5-266">**Visa kommando** också möjliggör avancerade utvecklare att skapa en snabb GUI för Windows PowerShell-baserade av skript.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-266">**Show-Command** also enables advanced scripters to create a quick Windows PowerShell-based GUI.</span></span>

<span data-ttu-id="cc7a5-267">**Vilket värde medför den här ändringen?**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-267">**What value does this change add?**</span></span>

<span data-ttu-id="cc7a5-268">Med hjälp av **visningskommandot** i din Windows PowerShell-skript, du kan ge användarna grafisk miljö som de är vana.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-268">By using **Show-Command** in your Windows PowerShell scripts, you can provide your users with the graphical environment with which they are familiar.</span></span> <span data-ttu-id="cc7a5-269">**Visa kommando** kan också inledande användare Läs Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-269">**Show-Command** can also help introductory users learn Windows PowerShell.</span></span>

<span data-ttu-id="cc7a5-270">**Vad fungerar annorlunda?**</span><span class="sxs-lookup"><span data-stu-id="cc7a5-270">**What works differently?**</span></span>

<span data-ttu-id="cc7a5-271">Visa-kommandot är nya Windows PowerShell ISE 3.0.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-271">Show-Command is new Windows PowerShell ISE 3.0.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc7a5-272">Se även</span><span class="sxs-lookup"><span data-stu-id="cc7a5-272">See also</span></span>
<span data-ttu-id="cc7a5-273">Mer information om hur du använder Windows PowerShell ISE i Windows PowerShell finns i följande länkar.</span><span class="sxs-lookup"><span data-stu-id="cc7a5-273">For more information about using Windows PowerShell ISE in Windows PowerShell, see the following links.</span></span>

- [<span data-ttu-id="cc7a5-274">Utforska Windows PowerShell Integrated Scripting Environment</span><span class="sxs-lookup"><span data-stu-id="cc7a5-274">Exploring the Windows PowerShell Integrated Scripting Environment</span></span>](../getting-started/fundamental/exploring-the-windows-powershell-ise.md)
- [<span data-ttu-id="cc7a5-275">ISE på TechNet Wiki</span><span class="sxs-lookup"><span data-stu-id="cc7a5-275">ISE on the TechNet Wiki</span></span>](https://social.technet.microsoft.com/wiki/search/searchresults.aspx?q=ISE)
- [<span data-ttu-id="cc7a5-276">Skriptcenter</span><span class="sxs-lookup"><span data-stu-id="cc7a5-276">Script Center</span></span>](https://technet.microsoft.com/scriptcenter/default)