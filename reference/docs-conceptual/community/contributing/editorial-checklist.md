---
title: Redaktionell check lista
description: Det här är en sammanfattande lista med regler för redigering av PowerShell-dokumentation.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 511e0c323e1a3256039e819d06f32f6e1ac42767
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/10/2020
ms.locfileid: "79078579"
---
# <a name="editors-checklist"></a><span data-ttu-id="5c97b-103">Redaktörens check lista</span><span class="sxs-lookup"><span data-stu-id="5c97b-103">Editor's checklist</span></span>

<span data-ttu-id="5c97b-104">Det här är en sammanfattning av regler som ska gälla när du skriver nya eller uppdaterar befintliga artiklar.</span><span class="sxs-lookup"><span data-stu-id="5c97b-104">This is a summary of rules to apply when writing new or updating existing articles.</span></span> <span data-ttu-id="5c97b-105">Se andra artiklar i bidrags hand boken för detaljerade förklaringar och exempel på dessa regler.</span><span class="sxs-lookup"><span data-stu-id="5c97b-105">See other articles in the Contributor's Guide for detailed explanations and examples of these rules.</span></span>

## <a name="metadata"></a><span data-ttu-id="5c97b-106">Metadata</span><span class="sxs-lookup"><span data-stu-id="5c97b-106">Metadata</span></span>

- <span data-ttu-id="5c97b-107">`ms.date`: måste vara i formatet **mm/dd/åååå**</span><span class="sxs-lookup"><span data-stu-id="5c97b-107">`ms.date`: must be in the format **MM/DD/YYYY**</span></span>
  - <span data-ttu-id="5c97b-108">Ändra datumet då det finns en betydande eller saklig uppdatering</span><span class="sxs-lookup"><span data-stu-id="5c97b-108">Change the date when there is a significant or factual update</span></span>
    - <span data-ttu-id="5c97b-109">Organisera om artikeln</span><span class="sxs-lookup"><span data-stu-id="5c97b-109">Reorganizing the article</span></span>
    - <span data-ttu-id="5c97b-110">Åtgärda faktiska fel</span><span class="sxs-lookup"><span data-stu-id="5c97b-110">Fixing factual errors</span></span>
    - <span data-ttu-id="5c97b-111">Lägger till ny information</span><span class="sxs-lookup"><span data-stu-id="5c97b-111">Adding new information</span></span>
  - <span data-ttu-id="5c97b-112">Ändra inte datumet om uppdateringen är obetydlig</span><span class="sxs-lookup"><span data-stu-id="5c97b-112">Do not change the date if the update is insignificant</span></span>
    - <span data-ttu-id="5c97b-113">Korrigera skrivfel och formatering</span><span class="sxs-lookup"><span data-stu-id="5c97b-113">Fixing typos and formatting</span></span>
- <span data-ttu-id="5c97b-114">`title`: unik sträng med 43-59 tecken inklusive blank steg</span><span class="sxs-lookup"><span data-stu-id="5c97b-114">`title`: unique string of 43-59 chars including spaces</span></span>
  - <span data-ttu-id="5c97b-115">Ta inte med plats identifierare (den genereras automatiskt)</span><span class="sxs-lookup"><span data-stu-id="5c97b-115">Do not include site identifier (it is auto-generated)</span></span>
  - <span data-ttu-id="5c97b-116">Använd menings fall – Inled bara det första ordet och alla korrekta Substantiv</span><span class="sxs-lookup"><span data-stu-id="5c97b-116">Use sentence case - capitalize only the first word and any proper nouns</span></span>
- <span data-ttu-id="5c97b-117">`description`: 115-145 tecken inklusive blank steg – denna abstrakt visas i Sök resultatet</span><span class="sxs-lookup"><span data-stu-id="5c97b-117">`description`: 115-145 characters including spaces - this abstract displays in the search result</span></span>

## <a name="formatting"></a><span data-ttu-id="5c97b-118">Formatering</span><span class="sxs-lookup"><span data-stu-id="5c97b-118">Formatting</span></span>

- <span data-ttu-id="5c97b-119">Element för bakticks-syntax som visas, infogade, i ett stycke</span><span class="sxs-lookup"><span data-stu-id="5c97b-119">Backtick syntax elements that appear, inline, within a paragraph</span></span>
  - <span data-ttu-id="5c97b-120">Cmdlet-namn `Verb-Noun`</span><span class="sxs-lookup"><span data-stu-id="5c97b-120">Cmdlet names `Verb-Noun`</span></span>
  - <span data-ttu-id="5c97b-121">Variabel `$counter`</span><span class="sxs-lookup"><span data-stu-id="5c97b-121">Variable `$counter`</span></span>
  - <span data-ttu-id="5c97b-122">Exempel på syntaktiska `Verb-Noun -Parameter`</span><span class="sxs-lookup"><span data-stu-id="5c97b-122">Syntactic examples `Verb-Noun -Parameter`</span></span>
  - <span data-ttu-id="5c97b-123">Fil Sök vägar `C:\Program Files\PowerShell``/usr/bin/pwsh`</span><span class="sxs-lookup"><span data-stu-id="5c97b-123">File paths `C:\Program Files\PowerShell`, `/usr/bin/pwsh`</span></span>
  - <span data-ttu-id="5c97b-124">URL: er som inte är avsedda att vara klickade i dokumentet</span><span class="sxs-lookup"><span data-stu-id="5c97b-124">URLs that are not meant to be clickable in the document</span></span>
- <span data-ttu-id="5c97b-125">Använd fetstil för egenskaps namn, parameter värden, parameter namn, klass namn, Modulnamn, entitetsnamn, namn på objekt eller typnamn</span><span class="sxs-lookup"><span data-stu-id="5c97b-125">Use bold for property names, parameter values, parameter names, class names, module names, entity names, object or type names</span></span>
  - <span data-ttu-id="5c97b-126">Fetstil används för semantisk markering, inte betoning</span><span class="sxs-lookup"><span data-stu-id="5c97b-126">Bold is used for semantic markup, not emphasis</span></span>
  - <span data-ttu-id="5c97b-127">Fet – Använd asterisker `**`</span><span class="sxs-lookup"><span data-stu-id="5c97b-127">Bold - use asterisks `**`</span></span>
- <span data-ttu-id="5c97b-128">Kursiv – Använd under streck `_`</span><span class="sxs-lookup"><span data-stu-id="5c97b-128">Italic - use underscore `_`</span></span>
  - <span data-ttu-id="5c97b-129">Används endast för betoning, inte för semantisk markering</span><span class="sxs-lookup"><span data-stu-id="5c97b-129">Only used for emphasis, not for semantic markup</span></span>
- <span data-ttu-id="5c97b-130">Rad brytningar vid 100 kolumner (eller vid 80 för **about_Topics**)</span><span class="sxs-lookup"><span data-stu-id="5c97b-130">Line breaks at 100 columns (or at 80 for **about_Topics**)</span></span>
- <span data-ttu-id="5c97b-131">Inga hårda flikar – Använd bara blank steg</span><span class="sxs-lookup"><span data-stu-id="5c97b-131">No hard tabs - use spaces only</span></span>
- <span data-ttu-id="5c97b-132">Inga avslutande blank steg på rader</span><span class="sxs-lookup"><span data-stu-id="5c97b-132">No trailing spaces on lines</span></span>

### <a name="headers"></a><span data-ttu-id="5c97b-133">Rubriker</span><span class="sxs-lookup"><span data-stu-id="5c97b-133">Headers</span></span>

- <span data-ttu-id="5c97b-134">H1 är endast första ett H1 per artikel</span><span class="sxs-lookup"><span data-stu-id="5c97b-134">H1 is first - only one H1 per article</span></span>
- <span data-ttu-id="5c97b-135">Använd endast [ATX-rubriker](https://github.github.com/gfm/#atx-headings)</span><span class="sxs-lookup"><span data-stu-id="5c97b-135">Use [ATX Headers](https://github.github.com/gfm/#atx-headings) only</span></span>
- <span data-ttu-id="5c97b-136">Använd menings fall för alla sidhuvuden</span><span class="sxs-lookup"><span data-stu-id="5c97b-136">Use sentence case for all headers</span></span>
- <span data-ttu-id="5c97b-137">Hoppa inte över nivåer – inget H3 utan H2</span><span class="sxs-lookup"><span data-stu-id="5c97b-137">Do not skip levels - no H3 without an H2</span></span>
- <span data-ttu-id="5c97b-138">Max djup på H3 eller H4</span><span class="sxs-lookup"><span data-stu-id="5c97b-138">Max depth of H3 or H4</span></span>
- <span data-ttu-id="5c97b-139">Tom rad före och efter</span><span class="sxs-lookup"><span data-stu-id="5c97b-139">Blank line before and after</span></span>
- <span data-ttu-id="5c97b-140">PlatyPS tillämpar vissa huvuden i schemat – Lägg inte till eller ta bort huvuden</span><span class="sxs-lookup"><span data-stu-id="5c97b-140">PlatyPS enforces specific headers in its schema - do not add or remove headers</span></span>

### <a name="code-blocks"></a><span data-ttu-id="5c97b-141">Kodblock</span><span class="sxs-lookup"><span data-stu-id="5c97b-141">Code blocks</span></span>

- <span data-ttu-id="5c97b-142">Tom rad före och efter</span><span class="sxs-lookup"><span data-stu-id="5c97b-142">Blank line before and after</span></span>
- <span data-ttu-id="5c97b-143">Använd taggade kod avgränsningar – **PowerShell**, **utdata**eller annat lämpligt språk-ID</span><span class="sxs-lookup"><span data-stu-id="5c97b-143">Use tagged code fences - **powershell**, **Output**, or other appropriate language ID</span></span>
- <span data-ttu-id="5c97b-144">Otaggade block för staket eller andra gränssnitt</span><span class="sxs-lookup"><span data-stu-id="5c97b-144">Untagged fence - syntax blocks or other shells</span></span>
- <span data-ttu-id="5c97b-145">Lägg till **utdata** i ett separat kodblock förutom enkla exempel där du inte har för avsikt att läsa in läsaren för att använda **kopierings** knappen</span><span class="sxs-lookup"><span data-stu-id="5c97b-145">Put **Output** in separate code block except for simple examples where you don't intend the for the reader to use the **Copy** button</span></span>
- <span data-ttu-id="5c97b-146">Se listan över [språk som stöds](/contribute/code-in-docs#supported-languages)</span><span class="sxs-lookup"><span data-stu-id="5c97b-146">See list of [supported languages](/contribute/code-in-docs#supported-languages)</span></span>

### <a name="lists"></a><span data-ttu-id="5c97b-147">Listor</span><span class="sxs-lookup"><span data-stu-id="5c97b-147">Lists</span></span>

- <span data-ttu-id="5c97b-148">Indraget korrekt</span><span class="sxs-lookup"><span data-stu-id="5c97b-148">Indented properly</span></span>
- <span data-ttu-id="5c97b-149">Tom rad före första objektet och efter sista posten</span><span class="sxs-lookup"><span data-stu-id="5c97b-149">Blank line before first item and after last item</span></span>
- <span data-ttu-id="5c97b-150">Punkt-Använd bindestreck (`-`) inte asterisk (`*`) – för lätt att förväxla med betoning</span><span class="sxs-lookup"><span data-stu-id="5c97b-150">Bullet - use hyphen (`-`) not asterisk (`*`) - too easy to confuse with emphasis</span></span>
- <span data-ttu-id="5c97b-151">För numrerade listor är alla siffror "1".</span><span class="sxs-lookup"><span data-stu-id="5c97b-151">For numbered lists, all numbers are "1."</span></span>

## <a name="terminology"></a><span data-ttu-id="5c97b-152">Terminologi</span><span class="sxs-lookup"><span data-stu-id="5c97b-152">Terminology</span></span>

- <span data-ttu-id="5c97b-153">PowerShell jämfört med Windows PowerShell vs. PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="5c97b-153">PowerShell vs. Windows PowerShell vs. PowerShell Core</span></span>
- <span data-ttu-id="5c97b-154">Se [produkt terminologi](powershell-style-guide.md#product-terminology)</span><span class="sxs-lookup"><span data-stu-id="5c97b-154">See [Product Terminology](powershell-style-guide.md#product-terminology)</span></span>

## <a name="cmdlet-reference-examples"></a><span data-ttu-id="5c97b-155">Exempel på cmdlet-referenser</span><span class="sxs-lookup"><span data-stu-id="5c97b-155">Cmdlet reference examples</span></span>

- <span data-ttu-id="5c97b-156">Måste ha minst ett exempel i cmdlet-referensen</span><span class="sxs-lookup"><span data-stu-id="5c97b-156">Must have at least one example in cmdlet reference</span></span>
- <span data-ttu-id="5c97b-157">Exempel bör vara tillräckligt många kod för att demonstrera användningen</span><span class="sxs-lookup"><span data-stu-id="5c97b-157">Examples should be just enough code to demonstrate the usage</span></span>
- <span data-ttu-id="5c97b-158">PowerShell-syntax</span><span class="sxs-lookup"><span data-stu-id="5c97b-158">PowerShell syntax</span></span>
  - <span data-ttu-id="5c97b-159">Använd fullständiga namn på cmdletar och parametrar-inga alias</span><span class="sxs-lookup"><span data-stu-id="5c97b-159">Use full names of cmdlets and parameters - no aliases</span></span>
  - <span data-ttu-id="5c97b-160">Använda ihopbuntning för parametrar när kommando raden blir för lång</span><span class="sxs-lookup"><span data-stu-id="5c97b-160">Use splatting for parameters when the command line gets too long</span></span>
  - <span data-ttu-id="5c97b-161">Undvik att använda rad fortsättnings omskalning – Använd bara vid behov</span><span class="sxs-lookup"><span data-stu-id="5c97b-161">Avoid using line continuation backticks - only use when necessary</span></span>
- <span data-ttu-id="5c97b-162">Ta bort eller förenkla PowerShell-prompten (`PS>`), förutom om det krävs för exemplet</span><span class="sxs-lookup"><span data-stu-id="5c97b-162">Remove or simplify the PowerShell prompt (`PS>`) except where required for the example</span></span>
- <span data-ttu-id="5c97b-163">Exempel på cmdlet-referens måste följa följande PlatyPS-schema</span><span class="sxs-lookup"><span data-stu-id="5c97b-163">Cmdlet reference example must follow the following PlatyPS schema</span></span>

  ~~~Markdown
  ### Example 1 - Descriptive title

  Zero or more short descriptive paragraphs explaining the context of the example followed by one or
  more code blocks. Recommend at least one and no more than two.

  ```powershell
  ... one or more PowerShell code statements ...
  ```

  ```Output
  Example output of the code above.
  ```

  Zero or more optional follow up paragraphs that explain the details of the code and output.
  ~~~

- <span data-ttu-id="5c97b-164">Lägg inte till några stycken mellan kod blocken.</span><span class="sxs-lookup"><span data-stu-id="5c97b-164">Do not put paragraphs between the code blocks.</span></span> <span data-ttu-id="5c97b-165">Allt beskrivande innehåll måste komma före eller efter kod blocken.</span><span class="sxs-lookup"><span data-stu-id="5c97b-165">All descriptive content must come before or after the code blocks.</span></span>

## <a name="linking-to-other-documents"></a><span data-ttu-id="5c97b-166">Länka till andra dokument</span><span class="sxs-lookup"><span data-stu-id="5c97b-166">Linking to other documents</span></span>

- <span data-ttu-id="5c97b-167">Länka utanför dokument uppsättning eller mellan cmdlet-referens och konceptuell</span><span class="sxs-lookup"><span data-stu-id="5c97b-167">Linking outside the docset or between cmdlet reference and conceptual</span></span>
  - <span data-ttu-id="5c97b-168">Använd relativa URL: er vid länkning till docs.microsoft.com (ta bort `https://docs.microsoft.com/en-us`)</span><span class="sxs-lookup"><span data-stu-id="5c97b-168">Use relative URLs when linking to docs.microsoft.com (remove `https://docs.microsoft.com/en-us`)</span></span>
  - <span data-ttu-id="5c97b-169">Ta inte med språk i URL: er för Microsoft-egenskaper (t. ex.</span><span class="sxs-lookup"><span data-stu-id="5c97b-169">Do not include locales in URLs on Microsoft properties (eg.</span></span> <span data-ttu-id="5c97b-170">ta bort `/en-us` från URL)</span><span class="sxs-lookup"><span data-stu-id="5c97b-170">remove `/en-us` from URL)</span></span>
  - <span data-ttu-id="5c97b-171">Alla URL: er till externa webbplatser bör använda HTTPS om det inte är giltigt för mål platsen</span><span class="sxs-lookup"><span data-stu-id="5c97b-171">All URLs to external websites should use HTTPS unless that is not valid for the target site</span></span>
- <span data-ttu-id="5c97b-172">Inom dokument uppsättning</span><span class="sxs-lookup"><span data-stu-id="5c97b-172">Within docset</span></span>
  - <span data-ttu-id="5c97b-173">Länk till fil Sök väg (t. ex. `../folder/file.md`)</span><span class="sxs-lookup"><span data-stu-id="5c97b-173">Link to file path (e.g. `../folder/file.md`)</span></span>
  - <span data-ttu-id="5c97b-174">Alla fil Sök vägar använder snedstreck (`/`) tecken</span><span class="sxs-lookup"><span data-stu-id="5c97b-174">All file paths use forward-slash (`/`) characters</span></span>
- <span data-ttu-id="5c97b-175">Bild länkar måste ha en unik alternativ text</span><span class="sxs-lookup"><span data-stu-id="5c97b-175">Image links should have unique alt text</span></span>
