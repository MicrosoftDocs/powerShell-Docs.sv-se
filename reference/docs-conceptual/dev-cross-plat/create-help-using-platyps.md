---
title: Skapa XML-baserad hjälp med PlatyPS
description: Att använda PlatyPS är ett snabbt och effektivt sätt att skapa en XML-baserad hjälp.
ms.date: 07/21/2020
ms.openlocfilehash: 79cf8c077a07bf1e7aa8ea1ea799be5f8d4af12c
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "86972623"
---
# <a name="create-xml-based-help-using-platyps"></a><span data-ttu-id="c762f-103">Skapa XML-baserad hjälp med PlatyPS</span><span class="sxs-lookup"><span data-stu-id="c762f-103">Create XML-based help using PlatyPS</span></span>

<span data-ttu-id="c762f-104">När du skapar en PowerShell-modul rekommenderar vi alltid att du inkluderar detaljerad hjälp för de cmdlets som du skapar.</span><span class="sxs-lookup"><span data-stu-id="c762f-104">When creating a PowerShell module, it is always recommended that you include detailed help for the cmdlets you create.</span></span> <span data-ttu-id="c762f-105">Om dina cmdletar implementeras i kompilerad kod måste du använda den XML-baserade hjälpen.</span><span class="sxs-lookup"><span data-stu-id="c762f-105">If your cmdlets are implemented in compiled code, you must use the XML-based help.</span></span> <span data-ttu-id="c762f-106">Detta XML-format kallas MAML (Microsoft Assistance Markup Language).</span><span class="sxs-lookup"><span data-stu-id="c762f-106">This XML format is known as the Microsoft Assistance Markup Language (MAML).</span></span>

<span data-ttu-id="c762f-107">Den äldre PowerShell SDK-dokumentationen innehåller information om hur du skapar hjälp för PowerShell-cmdlets paketerade i moduler.</span><span class="sxs-lookup"><span data-stu-id="c762f-107">The legacy PowerShell SDK documentation covers the details of creating help for PowerShell cmdlets packaged into modules.</span></span> <span data-ttu-id="c762f-108">PowerShell tillhandahåller dock inga verktyg för att skapa den XML-baserade hjälpen.</span><span class="sxs-lookup"><span data-stu-id="c762f-108">However, PowerShell does not provide any tools for creating the XML-based help.</span></span> <span data-ttu-id="c762f-109">SDK-dokumentationen förklarar strukturen i MAML-hjälpen, men låter dig skapa det komplexa och djupt kapslade, MAML innehållet manuellt.</span><span class="sxs-lookup"><span data-stu-id="c762f-109">The SDK documentation explains the structure of MAML help, but leaves you the task of creating the complex, and deeply nested, MAML content by hand.</span></span>

<span data-ttu-id="c762f-110">Det är här som [PlatyPS][] -modulen kan hjälpa dig.</span><span class="sxs-lookup"><span data-stu-id="c762f-110">This is where the [PlatyPS][] module can help.</span></span>

## <a name="what-is-platyps"></a><span data-ttu-id="c762f-111">Vad är PlatyPS?</span><span class="sxs-lookup"><span data-stu-id="c762f-111">What is PlatyPS?</span></span>

<span data-ttu-id="c762f-112">PlatyPS är ett verktyg med [öppen källkod][platyps-repo] som startas som ett _Hackathon_ -projekt för att skapa och underhålla MAML enklare.</span><span class="sxs-lookup"><span data-stu-id="c762f-112">PlatyPS is an [open-source][platyps-repo] tool that started as a _hackathon_ project to make the creation and maintenance of MAML easier.</span></span> <span data-ttu-id="c762f-113">PlatyPS dokumenterar syntaxen för parameter uppsättningar och de enskilda parametrarna för varje cmdlet i modulen.</span><span class="sxs-lookup"><span data-stu-id="c762f-113">PlatyPS documents the syntax of parameter sets and the individual parameters for each cmdlet in your module.</span></span> <span data-ttu-id="c762f-114">PlatyPS skapar strukturerade [markdown][] -filer som innehåller information om syntaxen.</span><span class="sxs-lookup"><span data-stu-id="c762f-114">PlatyPS creates structured [Markdown][] files that contain the syntax information.</span></span> <span data-ttu-id="c762f-115">Det går inte att skapa beskrivningar eller ange exempel.</span><span class="sxs-lookup"><span data-stu-id="c762f-115">It can't create descriptions or provide examples.</span></span>

<span data-ttu-id="c762f-116">PlatyPS skapar plats hållare där du kan fylla i beskrivningar och exempel.</span><span class="sxs-lookup"><span data-stu-id="c762f-116">PlatyPS creates placeholders for you to fill in descriptions and examples.</span></span> <span data-ttu-id="c762f-117">När du har lagt till nödvändig information kompilerar PlatyPS markdown-filerna till MAML-filer.</span><span class="sxs-lookup"><span data-stu-id="c762f-117">After adding the required information, PlatyPS compiles the Markdown files into MAML files.</span></span> <span data-ttu-id="c762f-118">PowerShell: s hjälp system tillåter även vanliga hjälp filer för konceptuell text (om ämnen).</span><span class="sxs-lookup"><span data-stu-id="c762f-118">PowerShell's help system also allows for plain-text conceptual help files (about topics).</span></span> <span data-ttu-id="c762f-119">PlatyPS har en cmdlet för att skapa en strukturerad markdown-mall för en ny _om_ -fil, men dessa filer måste bevaras `about_*.help.txt` manuellt.</span><span class="sxs-lookup"><span data-stu-id="c762f-119">PlatyPS has a cmdlet to create a structured Markdown template for a new _about_ file, but these `about_*.help.txt` files must be maintained manually.</span></span>

<span data-ttu-id="c762f-120">Du kan inkludera MAML-och text-hjälpfiler med modulen.</span><span class="sxs-lookup"><span data-stu-id="c762f-120">You can include the MAML and Text help files with your module.</span></span> <span data-ttu-id="c762f-121">Du kan också använda PlatyPS för att kompilera hjälpfilerna till ett CAB-paket som kan vara värd för uppdaterings bara hjälp.</span><span class="sxs-lookup"><span data-stu-id="c762f-121">You can also use PlatyPS to compile the help files into a CAB package that can be hosted for updateable help.</span></span>

## <a name="get-started-using-platyps"></a><span data-ttu-id="c762f-122">Kom igång med PlatyPS</span><span class="sxs-lookup"><span data-stu-id="c762f-122">Get started using PlatyPS</span></span>

<span data-ttu-id="c762f-123">Först måste du installera PlatyPS från PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="c762f-123">First you must install PlatyPS from the PowerShell Gallery.</span></span>

```powershell
Install-Module platyps -Force
Import-Module platyps
```

<span data-ttu-id="c762f-124">Följande flödes schema beskriver processen för att skapa eller uppdatera PowerShell-referensens innehåll.</span><span class="sxs-lookup"><span data-stu-id="c762f-124">The following flowchart outlines the process for creating or updating PowerShell reference content.</span></span>

:::image type="content" source="./media/create-help-using-platyps/cmdlet-ref-flow-v2.png" alt-text="Arbets flödet för att skapa XML-baserad hjälp med PlatyPS":::

##  <a name="create-markdown-content-for-a-powershell-module"></a><span data-ttu-id="c762f-126">Skapa markdown-innehåll för en PowerShell-modul</span><span class="sxs-lookup"><span data-stu-id="c762f-126">Create Markdown content for a PowerShell module</span></span>

1. <span data-ttu-id="c762f-127">Importera din nya modul till sessionen.</span><span class="sxs-lookup"><span data-stu-id="c762f-127">Import your new module into the session.</span></span> <span data-ttu-id="c762f-128">Upprepa det här steget för varje modul du behöver för att dokumentera.</span><span class="sxs-lookup"><span data-stu-id="c762f-128">Repeat this step for each module you need to document.</span></span>

   <span data-ttu-id="c762f-129">Kör följande kommando för att importera dina moduler:</span><span class="sxs-lookup"><span data-stu-id="c762f-129">Run the following command to import your modules:</span></span>

   ```powershell
   Import-Module <your module name>
   ```

1. <span data-ttu-id="c762f-130">Använd PlatyPS för att generera markdown-filer för din modul-sida och alla associerade cmdlets i modulen.</span><span class="sxs-lookup"><span data-stu-id="c762f-130">Use PlatyPS to generate Markdown files for your module page and all associated cmdlets within the module.</span></span> <span data-ttu-id="c762f-131">Upprepa det här steget för varje modul du behöver för att dokumentera.</span><span class="sxs-lookup"><span data-stu-id="c762f-131">Repeat this step for each module you need to document.</span></span>

   ```powershell
   $OutputFolder = <output path>
   $parameters = @{
       Module = <ModuleName>
       OutputFolder = $OutputFolder
       AlphabeticParamsOrder = $true
       WithModulePage = $true
       ExcludeDontShow = $true
       Encoding = 'UTF8BOM'
   }
   New-MarkdownHelp @parameters

   New-MarkdownAboutHelp -OutputFolder $OutputFolder -AboutName "topic_name"
   ```

   <span data-ttu-id="c762f-132">Om mappen utdata inte finns `New-MarkdownHelp` skapar den.</span><span class="sxs-lookup"><span data-stu-id="c762f-132">If the output folder does not exist, `New-MarkdownHelp` creates it.</span></span> <span data-ttu-id="c762f-133">I det här exemplet `New-MarkdownHelp` skapar en MARKDOWN-fil för varje cmdlet i modulen.</span><span class="sxs-lookup"><span data-stu-id="c762f-133">In this example, `New-MarkdownHelp` creates a Markdown file for each cmdlet in the module.</span></span> <span data-ttu-id="c762f-134">Dessutom skapas _sidan modul_ i en fil med namnet `<ModuleName>.md` .</span><span class="sxs-lookup"><span data-stu-id="c762f-134">It also creates the _module page_ in a file named `<ModuleName>.md`.</span></span> <span data-ttu-id="c762f-135">Den här modulen innehåller en lista över de cmdletar som finns i modulen och plats hållarna för **sammanfattnings** beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="c762f-135">This module page contains a list of the cmdlets contained in the module and placeholders for the **Synopsis** description.</span></span> <span data-ttu-id="c762f-136">Metadata på sidan modul kommer från modulen manifest och används av PlatyPS för att skapa HelpInfo XML-filen (som beskrivs [nedan](#creating-an-updateable-help-package)).</span><span class="sxs-lookup"><span data-stu-id="c762f-136">The metadata in the module page comes from the module manifest and is used by PlatyPS to create the HelpInfo XML file (as explained [below](#creating-an-updateable-help-package)).</span></span>

   <span data-ttu-id="c762f-137">`New-MarkdownAboutHelp` skapar en ny _om_ -fil med namnet `about_topic_name.md` .</span><span class="sxs-lookup"><span data-stu-id="c762f-137">`New-MarkdownAboutHelp` creates a new _about_ file named `about_topic_name.md`.</span></span>

   <span data-ttu-id="c762f-138">Mer information finns i [New-MarkdownHelp][] och [New-MarkdownAboutHelp][].</span><span class="sxs-lookup"><span data-stu-id="c762f-138">For more information, see [New-MarkdownHelp][] and [New-MarkdownAboutHelp][].</span></span>

### <a name="update-existing-markdown-content-when-the-module-changes"></a><span data-ttu-id="c762f-139">Uppdatera befintligt markdown-innehåll när modulen ändras</span><span class="sxs-lookup"><span data-stu-id="c762f-139">Update existing Markdown content when the module changes</span></span>

<span data-ttu-id="c762f-140">PlatyPS kan också uppdatera befintliga markdown-filer för en modul.</span><span class="sxs-lookup"><span data-stu-id="c762f-140">PlatyPS can also update existing Markdown files for a module.</span></span> <span data-ttu-id="c762f-141">Använd det här steget för att uppdatera befintliga moduler som har nya cmdlets, nya parametrar eller parametrar som har ändrats.</span><span class="sxs-lookup"><span data-stu-id="c762f-141">Use this step to update existing modules that have new cmdlets, new parameters, or parameters that have changed.</span></span>

1. <span data-ttu-id="c762f-142">Importera din nya modul till sessionen.</span><span class="sxs-lookup"><span data-stu-id="c762f-142">Import your new module into the session.</span></span> <span data-ttu-id="c762f-143">Upprepa det här steget för varje modul du behöver för att dokumentera.</span><span class="sxs-lookup"><span data-stu-id="c762f-143">Repeat this step for each module you need to document.</span></span>

   <span data-ttu-id="c762f-144">Kör följande kommando för att importera dina moduler:</span><span class="sxs-lookup"><span data-stu-id="c762f-144">Run the following command to import your modules:</span></span>

   ```powershell
   Import-Module <your module name>
   ```

1. <span data-ttu-id="c762f-145">Använd PlatyPS för att uppdatera markdown-filer för modulens landnings sida och alla associerade cmdlets i modulen.</span><span class="sxs-lookup"><span data-stu-id="c762f-145">Use PlatyPS to update Markdown files for your module landing page and all associated cmdlets within the module.</span></span> <span data-ttu-id="c762f-146">Upprepa det här steget för varje modul du behöver för att dokumentera.</span><span class="sxs-lookup"><span data-stu-id="c762f-146">Repeat this step for each module you need to document.</span></span>

   ```powershell
   $parameters = @{
       Path = <folder with Markdown>
       RefreshModulePage = $true
       AlphabeticParamsOrder = $true
       UpdateInputOutput = $true
       ExcludeDontShow = $true
       LogPath = <path to store log file>
       Encoding = 'UTF8BOM'
   }
   Update-MarkdownHelpModule @parameters
   ```

   <span data-ttu-id="c762f-147">`Update-MarkdownHelpModule` uppdaterar cmdlet-och modulens markdown-filer i den angivna mappen.</span><span class="sxs-lookup"><span data-stu-id="c762f-147">`Update-MarkdownHelpModule` updates the cmdlet and module Markdown files in the specified folder.</span></span>
   <span data-ttu-id="c762f-148">Filerna uppdateras inte `about_*.md` .</span><span class="sxs-lookup"><span data-stu-id="c762f-148">It does not update the `about_*.md` files.</span></span> <span data-ttu-id="c762f-149">Modul filen ( `ModuleName.md` ) tar emot alla nya **sammanfattnings** texter som har lagts till i cmdlet-filerna.</span><span class="sxs-lookup"><span data-stu-id="c762f-149">The module file (`ModuleName.md`) receives any new **Synopsis** text that has been added to the cmdlet files.</span></span> <span data-ttu-id="c762f-150">Uppdateringar av cmdlet-filer innehåller följande ändring:</span><span class="sxs-lookup"><span data-stu-id="c762f-150">Updates to cmdlet files include the following change:</span></span>

   - <span data-ttu-id="c762f-151">Nya parameter uppsättningar</span><span class="sxs-lookup"><span data-stu-id="c762f-151">New parameter sets</span></span>
   - <span data-ttu-id="c762f-152">Nya parametrar</span><span class="sxs-lookup"><span data-stu-id="c762f-152">New parameters</span></span>
   - <span data-ttu-id="c762f-153">Uppdaterade metadata för parameter</span><span class="sxs-lookup"><span data-stu-id="c762f-153">Updated parameter metadata</span></span>
   - <span data-ttu-id="c762f-154">Uppdaterad information om indata och Utdatatyp</span><span class="sxs-lookup"><span data-stu-id="c762f-154">Updated input and output type information</span></span>

   <span data-ttu-id="c762f-155">Mer information finns i [Update-MarkdownHelpModule][].</span><span class="sxs-lookup"><span data-stu-id="c762f-155">For more information, see [Update-MarkdownHelpModule][].</span></span>

## <a name="edit-the-new-or-updated-markdown-files"></a><span data-ttu-id="c762f-156">Redigera nya eller uppdaterade markdown-filer</span><span class="sxs-lookup"><span data-stu-id="c762f-156">Edit the new or updated Markdown files</span></span>

<span data-ttu-id="c762f-157">PlatyPS dokumenterar syntaxen för parameter uppsättningarna och de enskilda parametrarna.</span><span class="sxs-lookup"><span data-stu-id="c762f-157">PlatyPS documents the syntax of the parameter sets and the individual parameters.</span></span> <span data-ttu-id="c762f-158">Det går inte att skapa beskrivningar eller ange exempel.</span><span class="sxs-lookup"><span data-stu-id="c762f-158">It can't create descriptions or provide examples.</span></span> <span data-ttu-id="c762f-159">De olika områdena där innehåll behövs finns i klammerparenteser.</span><span class="sxs-lookup"><span data-stu-id="c762f-159">The specific areas where content is needed are contained in curly braces.</span></span> <span data-ttu-id="c762f-160">Exempelvis: `{{ Fill in the Description }}`</span><span class="sxs-lookup"><span data-stu-id="c762f-160">For example: `{{ Fill in the Description }}`</span></span>

:::image type="content" source="./media/create-help-using-platyps/placeholders-example.png" alt-text="Markdown-mall som visar plats hållarna i VS Code":::

<span data-ttu-id="c762f-162">Du måste lägga till en sammanfattning, en beskrivning av cmdleten, beskrivningar för varje parameter och minst ett exempel.</span><span class="sxs-lookup"><span data-stu-id="c762f-162">You need to add a synopsis, a description of the cmdlet, descriptions for each parameter, and at least one example.</span></span>

<span data-ttu-id="c762f-163">Detaljerad information om hur du skriver PowerShell-innehåll finns i följande artiklar:</span><span class="sxs-lookup"><span data-stu-id="c762f-163">For detailed information about writing PowerShell content, see the following articles:</span></span>

- [<span data-ttu-id="c762f-164">PowerShell-format guide</span><span class="sxs-lookup"><span data-stu-id="c762f-164">PowerShell style guide</span></span>](/powershell/scripting/community/contributing/powershell-style-guide)
- [<span data-ttu-id="c762f-165">Redigera referens artiklar</span><span class="sxs-lookup"><span data-stu-id="c762f-165">Editing reference articles</span></span>](/powershell/scripting/community/contributing/editing-cmdlet-ref)

> [!NOTE]
> <span data-ttu-id="c762f-166">PlatyPS har ett särskilt schema som används för cmdlet-referensen.</span><span class="sxs-lookup"><span data-stu-id="c762f-166">PlatyPS has a specific schema that is uses for cmdlet reference.</span></span> <span data-ttu-id="c762f-167">Schemat tillåter endast vissa markdown-block i specifika delar av dokumentet.</span><span class="sxs-lookup"><span data-stu-id="c762f-167">That schema only allows certain Markdown blocks in specific sections of the document.</span></span> <span data-ttu-id="c762f-168">Om du har placerat innehåll på fel plats Miss lyckas PlatyPS build-steget.</span><span class="sxs-lookup"><span data-stu-id="c762f-168">If you put content in the wrong location, the PlatyPS build step fails.</span></span> <span data-ttu-id="c762f-169">Mer information finns i [schema][] dokumentationen i PlatyPS-lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="c762f-169">For more information, see the [schema][] documentation in the PlatyPS repository.</span></span> <span data-ttu-id="c762f-170">Ett fullständigt exempel på välformulerad cmdlet-referens finns i [Get-item][].</span><span class="sxs-lookup"><span data-stu-id="c762f-170">For a complete example of well-formed cmdlet reference, see [Get-Item][].</span></span>

<span data-ttu-id="c762f-171">När du har angett nödvändigt innehåll för var och en av dina cmdletar måste du se till att uppdatera modulens landnings sida.</span><span class="sxs-lookup"><span data-stu-id="c762f-171">After providing the required content for each of your cmdlets, you need to make sure that you update the module landing page.</span></span> <span data-ttu-id="c762f-172">Kontrol lera att modulen har rätt `Module Guid` `Download Help Link` värden och värden i yaml metadata för `<module-name>.md` filen.</span><span class="sxs-lookup"><span data-stu-id="c762f-172">Verify your module has the correct `Module Guid` and `Download Help Link` values in the YAML metadata of the `<module-name>.md` file.</span></span> <span data-ttu-id="c762f-173">Lägg till metadata som saknas.</span><span class="sxs-lookup"><span data-stu-id="c762f-173">Add any missing metadata.</span></span>

<span data-ttu-id="c762f-174">Du kan också märka att vissa cmdlets kan sakna en **Sammanfattning** (_kort beskrivning_).</span><span class="sxs-lookup"><span data-stu-id="c762f-174">Also, you may notice that some cmdlets may be missing a **Synopsis** (_short description_).</span></span> <span data-ttu-id="c762f-175">Följande kommando uppdaterar modulens landnings sida med din **sammanfattnings** beskrivnings text.</span><span class="sxs-lookup"><span data-stu-id="c762f-175">The following command updates the module landing page with your **Synopsis** description text.</span></span> <span data-ttu-id="c762f-176">Öppna modulens landnings sida för att kontrol lera beskrivningarna.</span><span class="sxs-lookup"><span data-stu-id="c762f-176">Open the module landing page to verify the descriptions.</span></span>

```powershell
Update-MarkdownHelpModule –Path <full path output folder> -RefreshModulePage
```

<span data-ttu-id="c762f-177">Nu när du har angett allt innehåll kan du skapa MAML-hjälpfiler som visas `Get-Help` i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="c762f-177">Now that you have entered all the content, you can create the MAML help files that are displayed by `Get-Help` in the PowerShell console.</span></span>

## <a name="create-the-external-help-files"></a><span data-ttu-id="c762f-178">Skapa de externa hjälpfilerna</span><span class="sxs-lookup"><span data-stu-id="c762f-178">Create the external help files</span></span>

<span data-ttu-id="c762f-179">Det här steget skapar MAML-hjälpfilerna som visas `Get-Help` i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="c762f-179">This step creates the MAML help files that are displayed by `Get-Help` in the PowerShell console.</span></span>

<span data-ttu-id="c762f-180">Kör följande kommando för att skapa MAML-filerna:</span><span class="sxs-lookup"><span data-stu-id="c762f-180">To build the MAML files, run the following command:</span></span>

```powershell
New-ExternalHelp –Path <folder with MDs> -OutputPath <output help folder>
```

<span data-ttu-id="c762f-181">`New-ExternalHelp` konverterar alla cmdlet markdown-filer till en (eller flera) MAML-filer.</span><span class="sxs-lookup"><span data-stu-id="c762f-181">`New-ExternalHelp` converts all of the cmdlet Markdown files into one (or more) MAML files.</span></span> <span data-ttu-id="c762f-182">Om filer konverteras till oformaterade filer med följande namn format: `about_topic_name.help.txt` .</span><span class="sxs-lookup"><span data-stu-id="c762f-182">About files are converted to plain-text files with the following name format: `about_topic_name.help.txt`.</span></span>
<span data-ttu-id="c762f-183">Markdown-innehållet måste uppfylla kraven för PlatyPS-schemat.</span><span class="sxs-lookup"><span data-stu-id="c762f-183">The Markdown content must meet the requirement of the PlatyPS schema.</span></span> <span data-ttu-id="c762f-184">`New-ExternalHelp` kommer att avslutas med fel när innehållet inte följer schemat.</span><span class="sxs-lookup"><span data-stu-id="c762f-184">`New-ExternalHelp` will exits with errors when the content does not follow the schema.</span></span> <span data-ttu-id="c762f-185">Du måste redigera filerna för att åtgärda schema felen.</span><span class="sxs-lookup"><span data-stu-id="c762f-185">You must edit the files to fix the schema violations.</span></span>

> [!CAUTION]
> <span data-ttu-id="c762f-186">PlatyPS gör `about_*.md` att filerna konverteras till oformaterad text med ett dåligt jobb.</span><span class="sxs-lookup"><span data-stu-id="c762f-186">PlatyPS does a poor job converting the `about_*.md` files to plain text.</span></span> <span data-ttu-id="c762f-187">Du måste använda mycket enkla markdown för att få godtagbara resultat.</span><span class="sxs-lookup"><span data-stu-id="c762f-187">You must use very simple Markdown to get acceptable results.</span></span> <span data-ttu-id="c762f-188">Du kanske vill underhålla filerna i oformaterat text `about_topic_name.help.txt` format, i stället för att tillåta PlatyPS att konvertera dem.</span><span class="sxs-lookup"><span data-stu-id="c762f-188">You may want to maintain the files in plain-text `about_topic_name.help.txt` format, rather than allowing PlatyPS to convert them.</span></span>

<span data-ttu-id="c762f-189">När det här steget har slutförts visas `*-help.xml` och `about_*.help.txt` filer i målmappen.</span><span class="sxs-lookup"><span data-stu-id="c762f-189">Once this step is complete, you will see `*-help.xml` and `about_*.help.txt` files in the target output folder.</span></span>

<span data-ttu-id="c762f-190">Mer information finns i [New-ExternalHelp][]</span><span class="sxs-lookup"><span data-stu-id="c762f-190">For more information, see [New-ExternalHelp][]</span></span>

### <a name="test-the-compiled-help-files"></a><span data-ttu-id="c762f-191">Testa de kompilerade hjälpfilerna</span><span class="sxs-lookup"><span data-stu-id="c762f-191">Test the compiled help files</span></span>

<span data-ttu-id="c762f-192">Du kan verifiera innehållet med cmdleten [Get-HelpPreview][] :</span><span class="sxs-lookup"><span data-stu-id="c762f-192">You can verify the content with the [Get-HelpPreview][] cmdlet:</span></span>

```powershell
Get-HelpPreview -Path "<ModuleName>-Help.xml"
```

<span data-ttu-id="c762f-193">Cmdlet: en läser den kompilerade MAML-filen och matar ut innehållet i samma format som du skulle ta emot från `Get-Help` .</span><span class="sxs-lookup"><span data-stu-id="c762f-193">The cmdlet reads the compiled MAML file and outputs the content in the same format you would receive from `Get-Help`.</span></span> <span data-ttu-id="c762f-194">På så sätt kan du granska resultaten för att kontrol lera att markdown-filerna kompileras korrekt och ger önskade resultat.</span><span class="sxs-lookup"><span data-stu-id="c762f-194">This allows you to inspect the results to verify that the Markdown files compiled correctly and produce the desired results.</span></span> <span data-ttu-id="c762f-195">Om du hittar ett fel redigerar du markdown-filerna igen och kompilerar om MAML.</span><span class="sxs-lookup"><span data-stu-id="c762f-195">If you find an error, re-edit the Markdown files and recompile the MAML.</span></span>

<span data-ttu-id="c762f-196">Nu är du redo att publicera dina hjälpfiler.</span><span class="sxs-lookup"><span data-stu-id="c762f-196">Now you are ready to publish your help files.</span></span>

## <a name="publishing-your-help"></a><span data-ttu-id="c762f-197">Publicera din hjälp</span><span class="sxs-lookup"><span data-stu-id="c762f-197">Publishing your help</span></span>

<span data-ttu-id="c762f-198">Nu när du har kompilerat markdown-filerna till PowerShell-hjälpfilerna är du redo att göra filerna tillgängliga för användarna.</span><span class="sxs-lookup"><span data-stu-id="c762f-198">Now that you have compiled the Markdown files into PowerShell help files, you are ready to make the files available to users.</span></span> <span data-ttu-id="c762f-199">Det finns två alternativ för att tillhandahålla hjälp i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="c762f-199">There are two options for providing help in the PowerShell console.</span></span>

- <span data-ttu-id="c762f-200">Paketera hjälpfilerna med modulen</span><span class="sxs-lookup"><span data-stu-id="c762f-200">Package the help files with the module</span></span>
- <span data-ttu-id="c762f-201">Skapa ett uppdaterings bara hjälp paket som användare installerar med `Update-Help` cmdleten</span><span class="sxs-lookup"><span data-stu-id="c762f-201">Create an updateable help package that users install with the `Update-Help` cmdlet</span></span>

### <a name="packaging-help-with-the-module"></a><span data-ttu-id="c762f-202">Paketera hjälp med modulen</span><span class="sxs-lookup"><span data-stu-id="c762f-202">Packaging help with the module</span></span>

<span data-ttu-id="c762f-203">Hjälpfilerna kan paketeras med modulen.</span><span class="sxs-lookup"><span data-stu-id="c762f-203">The help files can be packaged with your module.</span></span> <span data-ttu-id="c762f-204">Mer information om mappstrukturen finns i [skriva hjälp för moduler][] .</span><span class="sxs-lookup"><span data-stu-id="c762f-204">See [Writing Help for Modules][] for details of the folder structure.</span></span> <span data-ttu-id="c762f-205">Du bör inkludera listan över hjälpfiler i värdet för nyckeln **filelist** i modulen manifest.</span><span class="sxs-lookup"><span data-stu-id="c762f-205">You should include the list of Help files in the value of the **FileList** key in the module manifest.</span></span>

### <a name="creating-an-updateable-help-package"></a><span data-ttu-id="c762f-206">Skapa ett uppdaterings bara hjälp paket</span><span class="sxs-lookup"><span data-stu-id="c762f-206">Creating an updateable help package</span></span>

<span data-ttu-id="c762f-207">Stegen för att skapa uppdaterings bara hjälp finns på en hög nivå:</span><span class="sxs-lookup"><span data-stu-id="c762f-207">At a high level, the steps to create updateable help include:</span></span>

1. <span data-ttu-id="c762f-208">Hitta en Internet plats som värd för dina hjälpfiler</span><span class="sxs-lookup"><span data-stu-id="c762f-208">Find an internet site to host your help files</span></span>
1. <span data-ttu-id="c762f-209">Lägg till en **HelpInfoURI** -nyckel till modulen manifest</span><span class="sxs-lookup"><span data-stu-id="c762f-209">Add a **HelpInfoURI** key to your module manifest</span></span>
1. <span data-ttu-id="c762f-210">Skapa en HelpInfo XML-fil</span><span class="sxs-lookup"><span data-stu-id="c762f-210">Create a HelpInfo XML file</span></span>
1. <span data-ttu-id="c762f-211">Skapa CAB-filer</span><span class="sxs-lookup"><span data-stu-id="c762f-211">Create CAB files</span></span>
1. <span data-ttu-id="c762f-212">Ladda upp filer</span><span class="sxs-lookup"><span data-stu-id="c762f-212">Upload your files</span></span>

<span data-ttu-id="c762f-213">Mer information finns i [stöd för att uppdatera hjälp: steg-för-steg][step-by-step].</span><span class="sxs-lookup"><span data-stu-id="c762f-213">For more information, see [Supporting Updateable Help: Step-by-step][step-by-step].</span></span>

<span data-ttu-id="c762f-214">PlatyPS hjälper dig med några av de här stegen.</span><span class="sxs-lookup"><span data-stu-id="c762f-214">PlatyPS assists you with  some of these steps.</span></span>

<span data-ttu-id="c762f-215">**HelpInfoURI** är en URL som pekar på platsen där dina hjälpfiler finns på Internet.</span><span class="sxs-lookup"><span data-stu-id="c762f-215">The **HelpInfoURI** is a URL that points to location where your help files are hosted on the internet.</span></span> <span data-ttu-id="c762f-216">Det här värdet konfigureras i manifestet för modulen.</span><span class="sxs-lookup"><span data-stu-id="c762f-216">This value is configured in the module manifest.</span></span> <span data-ttu-id="c762f-217">`Update-Help` läser modulens manifest för att hämta den här URL: en och hämta det uppdaterings bara hjälp innehållet.</span><span class="sxs-lookup"><span data-stu-id="c762f-217">`Update-Help` reads the module manifest to get this URL and download the updateable help content.</span></span> <span data-ttu-id="c762f-218">URL: en ska bara peka på mappens plats och inte till enskilda filer.</span><span class="sxs-lookup"><span data-stu-id="c762f-218">This URL should only point to the folder location and not to individual files.</span></span> <span data-ttu-id="c762f-219">`Update-Help` skapar de fil namn som ska laddas ned baserat på annan information från modulens manifest och XML-filen HelpInfo.</span><span class="sxs-lookup"><span data-stu-id="c762f-219">`Update-Help` constructs the filenames to download based on other information from the module manifest and the HelpInfo XML file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c762f-220">**HelpInfoURI** måste avslutas med ett snedstreck ( `/` ).</span><span class="sxs-lookup"><span data-stu-id="c762f-220">The **HelpInfoURI** must end with a forward-slash character (`/`).</span></span> <span data-ttu-id="c762f-221">Utan det tecknen kan `Update-Help` inte skapa rätt sökvägar för att ladda ned innehållet.</span><span class="sxs-lookup"><span data-stu-id="c762f-221">Without that character, `Update-Help` cannot construct the correct file paths to download the content.</span></span> <span data-ttu-id="c762f-222">De flesta HTTP-baserade fil tjänster är också Skift läges känsliga.</span><span class="sxs-lookup"><span data-stu-id="c762f-222">Also, most HTTP-based file services are case-sensitive.</span></span> <span data-ttu-id="c762f-223">Det är viktigt att modulens metadata i XML-filen HelpInfo innehåller rätt bokstavs fall.</span><span class="sxs-lookup"><span data-stu-id="c762f-223">It is important that the module metadata in the HelpInfo XML file contains the proper letter case.</span></span>

<span data-ttu-id="c762f-224">`New-ExternalHelp`Cmdleten skapar XML-filen HelpInfo i mappen utdata.</span><span class="sxs-lookup"><span data-stu-id="c762f-224">The `New-ExternalHelp` cmdlet creates the HelpInfo XML file in the output folder.</span></span> <span data-ttu-id="c762f-225">XML-filen HelpInfo skapas med YAML-metadata som finns i modulen markdown Files ( `ModuleName.md` ).</span><span class="sxs-lookup"><span data-stu-id="c762f-225">The HelpInfo XML file is built using YAML metadata contained in the module Markdown files (`ModuleName.md`).</span></span>

<span data-ttu-id="c762f-226">`New-ExternalHelpCab`Cmdleten skapar zip-och CAB-filer som innehåller de MAML och `about_*.help.txt` filer som du har kompilerat.</span><span class="sxs-lookup"><span data-stu-id="c762f-226">The `New-ExternalHelpCab` cmdlet creates ZIP and CAB files containing the MAML and `about_*.help.txt` files you compiled.</span></span> <span data-ttu-id="c762f-227">CAB-filer är kompatibla med alla versioner av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c762f-227">CAB files are compatible with all versions of PowerShell.</span></span>
<span data-ttu-id="c762f-228">PowerShell 6 och senare kan använda ZIP-filer.</span><span class="sxs-lookup"><span data-stu-id="c762f-228">PowerShell 6 and higher can use ZIP files.</span></span>

```powershell
$helpCabParameters = @{
    CabFilesFolder = $MamlOutputFolder
    LandingPagePath = $LandingPage
    OutputFolder = $CabOutputFolder
}
New-ExternalHelpCab @helpCabParameters
```

<span data-ttu-id="c762f-229">När du har skapat ZIP-och CAB-filerna laddar du upp ZIP-, CAB-och HelpInfo-XML-filerna till HTTP-filservern.</span><span class="sxs-lookup"><span data-stu-id="c762f-229">After creating the ZIP and CAB files, upload the ZIP, CAB, and HelpInfo XML files to your HTTP file server.</span></span> <span data-ttu-id="c762f-230">Lägg filerna på den plats som anges i **HelpInfoURI**.</span><span class="sxs-lookup"><span data-stu-id="c762f-230">Put the files in the location indicated by the **HelpInfoURI**.</span></span>

<span data-ttu-id="c762f-231">Mer information finns i [New-ExternalHelpCab][].</span><span class="sxs-lookup"><span data-stu-id="c762f-231">For more information, see [New-ExternalHelpCab][].</span></span>

### <a name="other-publishing-options"></a><span data-ttu-id="c762f-232">Andra publicerings alternativ</span><span class="sxs-lookup"><span data-stu-id="c762f-232">Other publishing options</span></span>

<span data-ttu-id="c762f-233">Markdown är ett mångsidigt format som är enkelt att transformera till andra format för publicering.</span><span class="sxs-lookup"><span data-stu-id="c762f-233">Markdown is a versatile format that is easy to transform to other formats for publishing.</span></span> <span data-ttu-id="c762f-234">Genom att använda ett verktyg som [pandoc][]kan du konvertera dina markdown-hjälpfiler till många olika dokument format, inklusive formaten oformaterad text, HTML, PDF och Office-dokument.</span><span class="sxs-lookup"><span data-stu-id="c762f-234">Using a tool like [Pandoc][], you can convert your Markdown help files to many different document formats, including plain text, HTML, PDF, and Office document formats.</span></span>

<span data-ttu-id="c762f-235">Dessutom kan cmdletarna [ConvertFrom-markdown][] och [show-markdown][] i PowerShell 6 och senare användas för att konvertera markdown till HTML eller skapa en färgad skärm i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="c762f-235">Also, the cmdlets [ConvertFrom-Markdown][] and [Show-Markdown][] in PowerShell 6 and higher can be used to convert Markdown to HTML or create a colorful display in the PowerShell console.</span></span>

## <a name="known-issues"></a><span data-ttu-id="c762f-236">Kända problem</span><span class="sxs-lookup"><span data-stu-id="c762f-236">Known issues</span></span>

<span data-ttu-id="c762f-237">PlatyPS är mycket känslig för [schemat][] för strukturen för de markdown-filer som skapas och kompileras.</span><span class="sxs-lookup"><span data-stu-id="c762f-237">PlatyPS is very sensitive to the [schema][] for the structure of the Markdown files it creates and compiles.</span></span> <span data-ttu-id="c762f-238">Det är mycket enkelt att skriva giltiga markdown som strider mot schemat.</span><span class="sxs-lookup"><span data-stu-id="c762f-238">It is very easy write valid Markdown that violates this schema.</span></span> <span data-ttu-id="c762f-239">Mer information finns i PowerShell- [stils guiden][] och [Redigera referens artiklar][].</span><span class="sxs-lookup"><span data-stu-id="c762f-239">For more information, consult the [PowerShell style guide][] and [Editing reference articles][].</span></span>

<!-- link references -->
[platyps-repo]: https://github.com/PowerShell/platyps
[PlatyPS]: https://www.powershellgallery.com/packages/platyPS/
[Markdown]: https://commonmark.org
[markdig]: https://github.com/lunet-io/markdig
[schema]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[Hämta objekt]: https://github.com/MicrosoftDocs/PowerShell-Docs/blob/staging/reference/7.0/Microsoft.PowerShell.Management/Get-Item.md
[Get-Item]: https://github.com/MicrosoftDocs/PowerShell-Docs/blob/staging/reference/7.0/Microsoft.PowerShell.Management/Get-Item.md
[New-MarkdownHelp]: https://github.com/PowerShell/platyPS/blob/master/docs/New-MarkdownHelp.md
[Uppdatera – MarkdownHelpModule]: https://github.com/PowerShell/platyPS/blob/master/docs/Update-MarkdownHelpModule.md
[Update-MarkdownHelpModule]: https://github.com/PowerShell/platyPS/blob/master/docs/Update-MarkdownHelpModule.md
[New-MarkdownAboutHelp]: https://github.com/PowerShell/platyPS/blob/master/docs/New-MarkdownAboutHelp.md
[New-ExternalHelp]: https://github.com/PowerShell/platyPS/blob/master/docs/New-ExternalHelp.md
[Get-HelpPreview]: https://github.com/PowerShell/platyPS/blob/master/docs/Get-HelpPreview.md
[New-ExternalHelpCab]: https://github.com/PowerShell/platyPS/blob/master/docs/New-ExternalHelpCab.md
[PowerShell-format guide]: /powershell/scripting/community/contributing/powershell-style-guide
[PowerShell style guide]: /powershell/scripting/community/contributing/powershell-style-guide
[Redigera referens artiklar]: /powershell/scripting/community/contributing/editing-cmdlet-ref
[Editing reference articles]: /powershell/scripting/community/contributing/editing-cmdlet-ref
[Skriver hjälp för moduler]: /powershell/scripting/developer/help/writing-help-for-windows-powershell-modules
[Writing Help for Modules]: /powershell/scripting/developer/help/writing-help-for-windows-powershell-modules
[step-by-step]: /powershell/scripting/developer/help/updatable-help-authoring-step-by-step
[Pandoc]: https://pandoc.org
[ConvertFrom – markdown]: /powershell/module/microsoft.powershell.utility/convertfrom-markdown
[ConvertFrom-Markdown]: /powershell/module/microsoft.powershell.utility/convertfrom-markdown
[Visa markdown]: /powershell/module/microsoft.powershell.utility/show-markdown
[Show-Markdown]: /powershell/module/microsoft.powershell.utility/show-markdown
