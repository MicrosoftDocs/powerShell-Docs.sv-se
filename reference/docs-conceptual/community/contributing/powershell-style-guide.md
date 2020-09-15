---
title: Stilguide för PowerShell-Docs
description: Den här artikeln innehåller regler för format för att skriva PowerShell-dokumentation.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 32df641f7cafa2a5bfcf1bcbf94be594aa77c7d0
ms.sourcegitcommit: 105c69ecedfe5180d8c12e8015d667c5f1a71579
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85837451"
---
# <a name="powershell-docs-style-guide"></a><span data-ttu-id="b49bd-103">Stilguide för PowerShell-Docs</span><span class="sxs-lookup"><span data-stu-id="b49bd-103">PowerShell-Docs style guide</span></span>

<span data-ttu-id="b49bd-104">Den här artikeln innehåller rikt linjer som är speciella för innehållet i PowerShell-dok.</span><span class="sxs-lookup"><span data-stu-id="b49bd-104">This article provides style guidance specific to the PowerShell-Docs content.</span></span> <span data-ttu-id="b49bd-105">Detta bygger på den information som beskrivs i [översikten](overview.md#get-started-writing-docs).</span><span class="sxs-lookup"><span data-stu-id="b49bd-105">This builds on the information outlined in the [Overview](overview.md#get-started-writing-docs).</span></span>

## <a name="product-terminology"></a><span data-ttu-id="b49bd-106">Produktterminologi</span><span class="sxs-lookup"><span data-stu-id="b49bd-106">Product Terminology</span></span>

<span data-ttu-id="b49bd-107">Det finns flera varianter av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b49bd-107">There are several variants of PowerShell.</span></span>

- <span data-ttu-id="b49bd-108">**PowerShell** – Det här är standardinställningen.</span><span class="sxs-lookup"><span data-stu-id="b49bd-108">**PowerShell** - This is the default.</span></span> <span data-ttu-id="b49bd-109">Vi rekommenderar att du använder PowerShell 7 och senare för att bli den som är den sanna PowerShell som går framåt.</span><span class="sxs-lookup"><span data-stu-id="b49bd-109">We consider PowerShell 7 and beyond to be the one, true PowerShell going forward.</span></span>
- <span data-ttu-id="b49bd-110">**PowerShell Core** – PowerShell som bygger på .net Core.</span><span class="sxs-lookup"><span data-stu-id="b49bd-110">**PowerShell Core** - PowerShell built on .NET Core.</span></span> <span data-ttu-id="b49bd-111">Användning av termen **Core** bör begränsas till fall där det är nödvändigt att skilja den från Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b49bd-111">Usage of the term **Core** should be limited to cases where it is necessary to differentiate it from Windows PowerShell.</span></span>
- <span data-ttu-id="b49bd-112">**Windows PowerShell** – PowerShell som bygger på .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b49bd-112">**Windows PowerShell** - PowerShell built on .NET Framework.</span></span> <span data-ttu-id="b49bd-113">Windows PowerShell-fartyg endast på Windows och kräver hela ramverket.</span><span class="sxs-lookup"><span data-stu-id="b49bd-113">Windows PowerShell ships only on Windows and requires the complete Framework.</span></span>

  <span data-ttu-id="b49bd-114">Generellt sett kan referenser till "Windows PowerShell" i dokumentationen ändras till "PowerShell".</span><span class="sxs-lookup"><span data-stu-id="b49bd-114">In general, references to "Windows PowerShell" in documentation can be changed to "PowerShell".</span></span>
  <span data-ttu-id="b49bd-115">"Windows PowerShell" ska användas när Windows PowerShell-det aktuella beteendet diskuteras.</span><span class="sxs-lookup"><span data-stu-id="b49bd-115">"Windows PowerShell" should be used when "Windows PowerShell"-specific behavior is being discussed.</span></span>

<span data-ttu-id="b49bd-116">Relaterade produkter</span><span class="sxs-lookup"><span data-stu-id="b49bd-116">Related products</span></span>

- <span data-ttu-id="b49bd-117">**Visual Studio Code (vs Code)** – det här är Microsofts kostnads fria redigerare med öppen källkod.</span><span class="sxs-lookup"><span data-stu-id="b49bd-117">**Visual Studio Code (VS Code)** - This is Microsoft's free, open source editor.</span></span> <span data-ttu-id="b49bd-118">I första omnämnandet ska det fullständiga namnet användas.</span><span class="sxs-lookup"><span data-stu-id="b49bd-118">At first mention, the full name should be used.</span></span> <span data-ttu-id="b49bd-119">Efter det kan du använda **vs Code**.</span><span class="sxs-lookup"><span data-stu-id="b49bd-119">After that you may use **VS Code**.</span></span> <span data-ttu-id="b49bd-120">Använd inte "VSCode".</span><span class="sxs-lookup"><span data-stu-id="b49bd-120">Do not use "VSCode".</span></span>
- <span data-ttu-id="b49bd-121">**PowerShell-tillägg för Visual Studio Code** – tillägget FÖRVANDLAr vs-kod till önskad IDE för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b49bd-121">**PowerShell Extension for Visual Studio Code** - The extension turns VS Code into the preferred IDE for PowerShell.</span></span> <span data-ttu-id="b49bd-122">I första omnämnandet ska det fullständiga namnet användas.</span><span class="sxs-lookup"><span data-stu-id="b49bd-122">At first mention, the full name should be used.</span></span> <span data-ttu-id="b49bd-123">Efter det kan du använda **PowerShell-tillägget**.</span><span class="sxs-lookup"><span data-stu-id="b49bd-123">After that you may use **PowerShell extension**.</span></span>
- <span data-ttu-id="b49bd-124">**Azure PowerShell** – det här är en samling PowerShell-moduler som används för att hantera Azure-tjänster.</span><span class="sxs-lookup"><span data-stu-id="b49bd-124">**Azure PowerShell** - This is the collection of PowerShell modules used to manage Azure services.</span></span>
- <span data-ttu-id="b49bd-125">**Azure Stack PowerShell** – det här är samlingen av PowerShell-moduler som används för att hantera Microsofts hybrid moln lösning.</span><span class="sxs-lookup"><span data-stu-id="b49bd-125">**Azure Stack PowerShell** - This is the collection of PowerShell modules used to manage Microsoft's hybrid cloud solution.</span></span>

## <a name="markdown-specifics"></a><span data-ttu-id="b49bd-126">Markdown-information</span><span class="sxs-lookup"><span data-stu-id="b49bd-126">Markdown specifics</span></span>

<span data-ttu-id="b49bd-127">Microsoft Open Publishing system (OPS) som bygger vår dokumentation använder [markdig][] för att bearbeta markdown-dokumenten.</span><span class="sxs-lookup"><span data-stu-id="b49bd-127">The Microsoft Open Publishing System (OPS) that builds our documentation uses [markdig][] to process the Markdown documents.</span></span> <span data-ttu-id="b49bd-128">Markdig analyserar dokumenten baserat på reglerna för den senaste [CommonMark][] -specifikationen.</span><span class="sxs-lookup"><span data-stu-id="b49bd-128">Markdig parses the documents based on the rules of the latest [CommonMark][] specification.</span></span>

<span data-ttu-id="b49bd-129">Den nya CommonMark-specifikationen är mycket strängare om konstruktion av vissa markdown-element.</span><span class="sxs-lookup"><span data-stu-id="b49bd-129">The new CommonMark spec is much stricter about the construction of some Markdown elements.</span></span> <span data-ttu-id="b49bd-130">Var uppmärksam på de uppgifter som anges i det här dokumentet.</span><span class="sxs-lookup"><span data-stu-id="b49bd-130">Pay close attention to the details provided in this document.</span></span>

### <a name="blank-lines-spaces-and-tabs"></a><span data-ttu-id="b49bd-131">Tomma rader, blanksteg och tabbar</span><span class="sxs-lookup"><span data-stu-id="b49bd-131">Blank lines, spaces, and tabs</span></span>

<span data-ttu-id="b49bd-132">Tomma rader indikerar också slutet av ett block i Markdown.</span><span class="sxs-lookup"><span data-stu-id="b49bd-132">Blank lines also signal the end of a block in Markdown.</span></span> <span data-ttu-id="b49bd-133">Det måste finnas ett tomt värde mellan Markdown-block av olika typer (till exempel mellan ett stycke och en lista eller rubrik).</span><span class="sxs-lookup"><span data-stu-id="b49bd-133">There should be a single blank between Markdown blocks of different types (for example, between a paragraph and a list or header).</span></span>

<span data-ttu-id="b49bd-134">Ta bort dubbletter av tomma rader.</span><span class="sxs-lookup"><span data-stu-id="b49bd-134">Remove duplicate blank lines.</span></span> <span data-ttu-id="b49bd-135">Flera tomma rader återges som en enda tom rad i HTML så det finns inget ändamål för flera tomma rader.</span><span class="sxs-lookup"><span data-stu-id="b49bd-135">Multiple blank lines render as a single blank line in HTML so there is no purpose for multiple blank lines.</span></span> <span data-ttu-id="b49bd-136">Flera tomma rader i ett kodblock bryter kod blocket.</span><span class="sxs-lookup"><span data-stu-id="b49bd-136">Multiple blank lines within a code block break the code block.</span></span>

<span data-ttu-id="b49bd-137">Ta bort extra blanksteg i slutet av rader.</span><span class="sxs-lookup"><span data-stu-id="b49bd-137">Remove extra spaces at the end of lines.</span></span>

> [!NOTE]
> <span data-ttu-id="b49bd-138">Avståndet har betydelse i Markdown.</span><span class="sxs-lookup"><span data-stu-id="b49bd-138">Spacing is significant in Markdown.</span></span> <span data-ttu-id="b49bd-139">Använd alltid blanksteg i stället för hårda tabbar.</span><span class="sxs-lookup"><span data-stu-id="b49bd-139">Always uses spaces instead of hard tabs.</span></span> <span data-ttu-id="b49bd-140">Avslutande blank steg kan ändra hur markdown återges.</span><span class="sxs-lookup"><span data-stu-id="b49bd-140">Trailing spaces can change how Markdown renders.</span></span>

### <a name="titles-and-headings"></a><span data-ttu-id="b49bd-141">Rubriker</span><span class="sxs-lookup"><span data-stu-id="b49bd-141">Titles and headings</span></span>

<span data-ttu-id="b49bd-142">Använd bara [ATX-rubriker][atx] (# style, i stället för `=` eller `-` stilrubriker).</span><span class="sxs-lookup"><span data-stu-id="b49bd-142">Only use [ATX headings][atx] (# style, as opposed to `=` or `-` style headers).</span></span>

- <span data-ttu-id="b49bd-143">Använd bara inledande versal i meningar, och den första bokstaven i en rubrik skrivas med versal</span><span class="sxs-lookup"><span data-stu-id="b49bd-143">Use sentence case - only proper nouns and the first letter of a title or header should be capitalized</span></span>
- <span data-ttu-id="b49bd-144">Det måste finnas ett blanksteg mellan `#` och den första bokstaven i rubriken</span><span class="sxs-lookup"><span data-stu-id="b49bd-144">There must be a single space between the `#` and the first letter of the heading</span></span>
- <span data-ttu-id="b49bd-145">Rubriker ska omges av en enda tom rad</span><span class="sxs-lookup"><span data-stu-id="b49bd-145">Headings should be surrounded by a single blank line</span></span>
- <span data-ttu-id="b49bd-146">Endast en H1 per dokument</span><span class="sxs-lookup"><span data-stu-id="b49bd-146">Only one H1 per document</span></span>
- <span data-ttu-id="b49bd-147">Rubrik nivåerna bör ökas med ett.</span><span class="sxs-lookup"><span data-stu-id="b49bd-147">Header levels should increment by one.</span></span> <span data-ttu-id="b49bd-148">Hoppa över nivåer</span><span class="sxs-lookup"><span data-stu-id="b49bd-148">Do not skip levels</span></span>
- <span data-ttu-id="b49bd-149">Använd inte fetstil eller andra markeringar i sidhuvuden</span><span class="sxs-lookup"><span data-stu-id="b49bd-149">Do not use bold or other markup in headers</span></span>

### <a name="limit-line-length-to-100-characters"></a><span data-ttu-id="b49bd-150">Begränsa radlängden till 100 tecken</span><span class="sxs-lookup"><span data-stu-id="b49bd-150">Limit line length to 100 characters</span></span>

<span data-ttu-id="b49bd-151">Detta gäller för konceptuella artiklar och cmdlet-referens.</span><span class="sxs-lookup"><span data-stu-id="b49bd-151">This applies to conceptual articles and cmdlet reference.</span></span> <span data-ttu-id="b49bd-152">Att begränsa rad längden ger bättre läsbarhet i git-differenser och historik.</span><span class="sxs-lookup"><span data-stu-id="b49bd-152">Limiting the line length improves the readability of git diffs and history.</span></span> <span data-ttu-id="b49bd-153">Det gör det också enklare för andra skrivare att göra bidrag.</span><span class="sxs-lookup"><span data-stu-id="b49bd-153">It also makes it easier for other writers to make contributions.</span></span>

<span data-ttu-id="b49bd-154">Använd tillägget [Flow markdown][reflow] i Visual Studio Code för att enkelt ommontera stycken för att passa den angivna rad längden.</span><span class="sxs-lookup"><span data-stu-id="b49bd-154">Use the [Reflow Markdown][reflow] extension in Visual Studio Code to easily reflow paragraphs to fit the prescribed line length.</span></span>

<span data-ttu-id="b49bd-155">About_topics är begränsade till 80 tecken.</span><span class="sxs-lookup"><span data-stu-id="b49bd-155">About_topics are limited to 80 characters.</span></span> <span data-ttu-id="b49bd-156">Mer detaljerad information finns i [Redigera referens artiklar](./editing-cmdlet-ref.md#formatting-about_-files).</span><span class="sxs-lookup"><span data-stu-id="b49bd-156">For more specific information, see [Editing reference articles](./editing-cmdlet-ref.md#formatting-about_-files).</span></span>

### <a name="lists"></a><span data-ttu-id="b49bd-157">Listor</span><span class="sxs-lookup"><span data-stu-id="b49bd-157">Lists</span></span>

<span data-ttu-id="b49bd-158">Om din lista innehåller flera meningar eller stycken kan du överväga att använda en underordnad rubrik i stället för en lista.</span><span class="sxs-lookup"><span data-stu-id="b49bd-158">If your list contains multiple sentences or paragraphs, consider using a sub-level header rather than a list.</span></span>

<span data-ttu-id="b49bd-159">Listan ska omges av en enda tom rad.</span><span class="sxs-lookup"><span data-stu-id="b49bd-159">List should be surrounded by a single blank line.</span></span>

#### <a name="unordered-lists"></a><span data-ttu-id="b49bd-160">Osorterade listor</span><span class="sxs-lookup"><span data-stu-id="b49bd-160">Unordered lists</span></span>

<span data-ttu-id="b49bd-161">Avsluta aldrig listobjekt med punkt om de inte innehåller flera meningar.</span><span class="sxs-lookup"><span data-stu-id="b49bd-161">Do not end list items with a period unless they contain multiple sentences.</span></span> <span data-ttu-id="b49bd-162">Använd bindestreck (`-`) som punkter för listobjekt.</span><span class="sxs-lookup"><span data-stu-id="b49bd-162">Use the hyphen character (`-`) for list item bullets.</span></span> <span data-ttu-id="b49bd-163">På så sätt undviker du sammanblandning med markeringen för fetstil eller kursiv stil, som använder asterisk [`*`].</span><span class="sxs-lookup"><span data-stu-id="b49bd-163">This avoids confusion with bold or italic markup that uses the asterisk [`*`].</span></span> <span data-ttu-id="b49bd-164">Om du vill lägga till ett stycke eller andra element under ett objekt i en punktlista infogar du en radbrytning och justerar indraget efter det första tecknet efter punkten.</span><span class="sxs-lookup"><span data-stu-id="b49bd-164">To include a paragraph or other elements under a bullet item, insert a line break and align indentation with the first character after the bullet.</span></span>

<span data-ttu-id="b49bd-165">Exempel:</span><span class="sxs-lookup"><span data-stu-id="b49bd-165">For example:</span></span>

```markdown
This is a list that contain sub-elements under a bullet item.

- First bullet item

  Sentence explaining the first bullet.

  - Sub-bullet item

    Sentence explaining the sub-bullet.

- Second bullet item
- Third bullet item
```

<span data-ttu-id="b49bd-166">Det här är en lista som innehåller underordnade element under ett objekt i en punktlista.</span><span class="sxs-lookup"><span data-stu-id="b49bd-166">This is a list that contains sub-elements under a bullet item.</span></span>

- <span data-ttu-id="b49bd-167">Första objektet i punktlistan</span><span class="sxs-lookup"><span data-stu-id="b49bd-167">First bullet item</span></span>

  <span data-ttu-id="b49bd-168">Mening som beskriver den första punkten.</span><span class="sxs-lookup"><span data-stu-id="b49bd-168">Sentence explaining the first bullet.</span></span>

  - <span data-ttu-id="b49bd-169">Underordnat objekt i punktlista</span><span class="sxs-lookup"><span data-stu-id="b49bd-169">Sub-bullet item</span></span>

    <span data-ttu-id="b49bd-170">Mening som beskriver den första underordnade punkten.</span><span class="sxs-lookup"><span data-stu-id="b49bd-170">Sentence explaining the sub-bullet.</span></span>

- <span data-ttu-id="b49bd-171">Andra objektet i punktlistan</span><span class="sxs-lookup"><span data-stu-id="b49bd-171">Second bullet item</span></span>
- <span data-ttu-id="b49bd-172">Tredje objektet i punktlistan</span><span class="sxs-lookup"><span data-stu-id="b49bd-172">Third bullet item</span></span>

#### <a name="ordered-lists"></a><span data-ttu-id="b49bd-173">Sorterade listor</span><span class="sxs-lookup"><span data-stu-id="b49bd-173">Ordered lists</span></span>

<span data-ttu-id="b49bd-174">Om du vill lägga till ett stycke eller andra element under ett numrerat objekt, justerar du indraget efter det första tecknet som följer efter objektets nummer.</span><span class="sxs-lookup"><span data-stu-id="b49bd-174">To include a paragraph or other elements under a numbered item, align indentation with the first character after the item number.</span></span> <span data-ttu-id="b49bd-175">Alla objekt i en numrerad lista ska använda talet i `1.` stället för att öka varje objekt.</span><span class="sxs-lookup"><span data-stu-id="b49bd-175">All items in a numbered listed should use the number `1.` rather than incrementing each item.</span></span> <span data-ttu-id="b49bd-176">Med Markdown-rendering ökar värdet automatiskt.</span><span class="sxs-lookup"><span data-stu-id="b49bd-176">Markdown rendering increments the value automatically.</span></span> <span data-ttu-id="b49bd-177">Det här gör det enklare att ändra ordning på objekt och standardiserar indrag för underordnat innehåll.</span><span class="sxs-lookup"><span data-stu-id="b49bd-177">This makes reordering items easier and standardizes the indentation of subordinate content.</span></span>

<span data-ttu-id="b49bd-178">Exempel:</span><span class="sxs-lookup"><span data-stu-id="b49bd-178">For example:</span></span>

```markdown
1. For the first element, insert a single space after the 1. Long sentences should be
   wrapped to the next line and must line up with the first character after the numbered
   list marker.

   To include a second element (like this one), insert a line break after the first
   and align indentations. The indentation of the second element must line up with
   the first character after the numbered list marker. For single digit items, like
   this one, you indent to column 4. For double digits items, for example item number
   10, you indent to column 5.

1. The next numbered item starts here.
```

<span data-ttu-id="b49bd-179">Den resulterande markdown återges på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="b49bd-179">The resulting Markdown is rendered as follows:</span></span>

1. <span data-ttu-id="b49bd-180">För det första elementet infogar du ett blanksteg efter siffran 1.</span><span class="sxs-lookup"><span data-stu-id="b49bd-180">For the first element, insert a single space after the 1.</span></span> <span data-ttu-id="b49bd-181">Långa meningar ska omslutas till nästa rad, och måste anpassas efter det första tecknet efter markören för den numrerade listan.</span><span class="sxs-lookup"><span data-stu-id="b49bd-181">Long sentences should be wrapped to the next line and must line up with the first character after the numbered list marker.</span></span>

   <span data-ttu-id="b49bd-182">Vill du lägga till ett andra element (som det här) infogar du en radbrytning efter det första och justerar indragen.</span><span class="sxs-lookup"><span data-stu-id="b49bd-182">To include a second element (like this one), insert a line break after the first and align indentations.</span></span> <span data-ttu-id="b49bd-183">Indraget för det andra elementet måste anpassas efter det första tecknet efter markören för den numrerade listan.</span><span class="sxs-lookup"><span data-stu-id="b49bd-183">The indentation of the second element must line up with the first character after the numbered list marker.</span></span> <span data-ttu-id="b49bd-184">För ensiffriga objekt, som det här, gör du indrag till kolumn 4.</span><span class="sxs-lookup"><span data-stu-id="b49bd-184">For single digit items, like this one, you indent to column 4.</span></span> <span data-ttu-id="b49bd-185">För tvåsiffriga objekt, till exempel objekt nummer 10, gör du indrag till kolumn 5.</span><span class="sxs-lookup"><span data-stu-id="b49bd-185">For double digits items, for example item number 10, you indent to column 5.</span></span>

1. <span data-ttu-id="b49bd-186">Nästa numrerade objekt börjar här.</span><span class="sxs-lookup"><span data-stu-id="b49bd-186">The next numbered item starts here.</span></span>

### <a name="images"></a><span data-ttu-id="b49bd-187">Avbildningar</span><span class="sxs-lookup"><span data-stu-id="b49bd-187">Images</span></span>

<span data-ttu-id="b49bd-188">Syntax för att infoga en bild:</span><span class="sxs-lookup"><span data-stu-id="b49bd-188">The syntax to include an image is:</span></span>

```markdown
![[alt text]](<folderPath>)

Example:
![Introduction](./media/overview/Introduction.png)
```

<span data-ttu-id="b49bd-189">`alt text` är en kort beskrivning av bilden och `<folder path>` är en relativ sökväg till bilden.</span><span class="sxs-lookup"><span data-stu-id="b49bd-189">Where `alt text` is a brief description of the image and `<folder path>` is a relative path to the image.</span></span> <span data-ttu-id="b49bd-190">Alternativ text krävs för skärmläsare för personer med nedsatt syn.</span><span class="sxs-lookup"><span data-stu-id="b49bd-190">Alternate text is required for screen readers for the visually impaired.</span></span> <span data-ttu-id="b49bd-191">Det är också användbart om det har uppstått ett fel på webbplatsen och bilden inte kan återges.</span><span class="sxs-lookup"><span data-stu-id="b49bd-191">It is also useful in case there is a site bug where the image cannot be rendered.</span></span>

<span data-ttu-id="b49bd-192">Avbildningar ska lagras i en `media/<article-name>` mapp i den mapp som innehåller artikeln.</span><span class="sxs-lookup"><span data-stu-id="b49bd-192">Images should be stored in a `media/<article-name>` folder within the folder containing the article.</span></span>
<span data-ttu-id="b49bd-193">Bilder ska inte delas mellan artiklar.</span><span class="sxs-lookup"><span data-stu-id="b49bd-193">Images should not be shared between articles.</span></span> <span data-ttu-id="b49bd-194">Skapa en mapp som matchar filnamnet för din artikel under mappen `media`.</span><span class="sxs-lookup"><span data-stu-id="b49bd-194">Create a folder that matches the filename of your article under the `media` folder.</span></span> <span data-ttu-id="b49bd-195">Kopiera bilderna till artikeln till den nya mappen.</span><span class="sxs-lookup"><span data-stu-id="b49bd-195">Copy the images for that article to that new folder.</span></span> <span data-ttu-id="b49bd-196">Om en bild används av flera artiklar måste varje bildmapp innehålla en kopia av bildfilen.</span><span class="sxs-lookup"><span data-stu-id="b49bd-196">If an image is used by multiple articles, each image folder must have a copy of that image file.</span></span> <span data-ttu-id="b49bd-197">Den här metoden förhindrar att en ändring av en bild i en artikel påverkar en annan artikel.</span><span class="sxs-lookup"><span data-stu-id="b49bd-197">This practice prevents a change to an image in one article affecting another article.</span></span>

<span data-ttu-id="b49bd-198">Följande bild fil typer stöds:,, `*.png` , `*.gif` `*.jpeg` `*.jpg` , `*.svg`</span><span class="sxs-lookup"><span data-stu-id="b49bd-198">The following image file types are supported: `*.png`, `*.gif`, `*.jpeg`, `*.jpg`, `*.svg`</span></span>

### <a name="markdown-extensions-supported-by-open-publishing"></a><span data-ttu-id="b49bd-199">Markdown-tillägg stöds av Open Publishing</span><span class="sxs-lookup"><span data-stu-id="b49bd-199">Markdown extensions supported by Open Publishing</span></span>

<span data-ttu-id="b49bd-200">[Microsoft docs redigerings paketet](/contribute/how-to-write-docs-auth-pack) innehåller verktyg som stöder funktioner som är unika för vårt publicerings system.</span><span class="sxs-lookup"><span data-stu-id="b49bd-200">The [Microsoft Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack) contains tools that support features unique to our publishing system.</span></span> <span data-ttu-id="b49bd-201">Aviseringar är ett markdown-tillägg för att skapa blockquotes som återger på docs.microsoft.com med färger och ikoner som markerar innehållets omfattning.</span><span class="sxs-lookup"><span data-stu-id="b49bd-201">Alerts are a Markdown extension to create blockquotes that render on docs.microsoft.com with colors and icons that highlight the significance of the content.</span></span> <span data-ttu-id="b49bd-202">Följande aviseringstyper stöds:</span><span class="sxs-lookup"><span data-stu-id="b49bd-202">The following alert types are supported:</span></span>

```markdown
> [!NOTE]
> Information the user should notice even if skimming.

> [!TIP]
> Optional information to help a user be more successful.

> [!IMPORTANT]
> Essential information required for user success.

> [!CAUTION]
> Negative potential consequences of an action.

> [!WARNING]
> Dangerous certain consequences of an action.
```

<span data-ttu-id="b49bd-203">Dessa aviseringar ser ut så här på docs.microsoft.com:</span><span class="sxs-lookup"><span data-stu-id="b49bd-203">These alerts look like this on docs.microsoft.com:</span></span>

<span data-ttu-id="b49bd-204">Antecknings block</span><span class="sxs-lookup"><span data-stu-id="b49bd-204">Note block</span></span>

> [!NOTE]
> <span data-ttu-id="b49bd-205">Information som användaren ska kunna se även vid snabbläsning.</span><span class="sxs-lookup"><span data-stu-id="b49bd-205">Information the user should notice even if skimming.</span></span>

<span data-ttu-id="b49bd-206">Tip-block</span><span class="sxs-lookup"><span data-stu-id="b49bd-206">Tip block</span></span>

> [!TIP]
> <span data-ttu-id="b49bd-207">Valfri information som hjälper användaren.</span><span class="sxs-lookup"><span data-stu-id="b49bd-207">Optional information to help a user be more successful.</span></span>

<span data-ttu-id="b49bd-208">Viktigt block</span><span class="sxs-lookup"><span data-stu-id="b49bd-208">Important block</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b49bd-209">Viktig information som användaren behöver.</span><span class="sxs-lookup"><span data-stu-id="b49bd-209">Essential information required for user success.</span></span>

<span data-ttu-id="b49bd-210">Varnings block</span><span class="sxs-lookup"><span data-stu-id="b49bd-210">Caution block</span></span>

> [!CAUTION]
> <span data-ttu-id="b49bd-211">Potentiella negativa konsekvenser av en åtgärd.</span><span class="sxs-lookup"><span data-stu-id="b49bd-211">Negative potential consequences of an action.</span></span>

<span data-ttu-id="b49bd-212">Varnings block</span><span class="sxs-lookup"><span data-stu-id="b49bd-212">Warning block</span></span>

> [!WARNING]
> <span data-ttu-id="b49bd-213">Farliga konsekvenser av en åtgärd.</span><span class="sxs-lookup"><span data-stu-id="b49bd-213">Dangerous certain consequences of an action.</span></span>

### <a name="hyperlinks"></a><span data-ttu-id="b49bd-214">Hyperlänkar</span><span class="sxs-lookup"><span data-stu-id="b49bd-214">Hyperlinks</span></span>

- <span data-ttu-id="b49bd-215">Hyperlänkar måste använda markdown-syntax `[friendlyname](url-or-path)`</span><span class="sxs-lookup"><span data-stu-id="b49bd-215">Hyperlinks must use Markdown syntax `[friendlyname](url-or-path)`</span></span>
- <span data-ttu-id="b49bd-216">Länkar bör vara HTTPS när det är möjligt.</span><span class="sxs-lookup"><span data-stu-id="b49bd-216">Links should be HTTPS when possible.</span></span>
- <span data-ttu-id="b49bd-217">Länkar måste ha ett användarvänligt namn, vanligtvis rubriken för det länkade ämnet</span><span class="sxs-lookup"><span data-stu-id="b49bd-217">Links must have a friendly name, usually the title of the linked topic</span></span>
- <span data-ttu-id="b49bd-218">Alla objekt i avsnittet "relaterade länkar" längst ned ska vara hyperlänkade</span><span class="sxs-lookup"><span data-stu-id="b49bd-218">All items in the "related links" section at the bottom should be hyperlinked</span></span>
- <span data-ttu-id="b49bd-219">Använd inte grava accenter, fetstil eller andra markeringar inuti hakparenteserna för en hyperlänk.</span><span class="sxs-lookup"><span data-stu-id="b49bd-219">Do not use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>
- <span data-ttu-id="b49bd-220">Bare-URL: er kan användas när du pratar om en angiven URI.</span><span class="sxs-lookup"><span data-stu-id="b49bd-220">Bare URLs may be used when you are talking about a specific URI.</span></span> <span data-ttu-id="b49bd-221">URI måste omges av baktick.</span><span class="sxs-lookup"><span data-stu-id="b49bd-221">The URI must be enclosed in backticks.</span></span> <span data-ttu-id="b49bd-222">Exempel:</span><span class="sxs-lookup"><span data-stu-id="b49bd-222">For example:</span></span>

  ```markdown
  By default, if you do not specify this parameter, the DMTF standard resource URI
  `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.
  ```

#### <a name="linking-to-other-content"></a><span data-ttu-id="b49bd-223">Länka till annat innehåll</span><span class="sxs-lookup"><span data-stu-id="b49bd-223">Linking to other content</span></span>

<span data-ttu-id="b49bd-224">Det finns två typer av hyperlänkar som stöds av publicerings systemet:</span><span class="sxs-lookup"><span data-stu-id="b49bd-224">There are two types of hyperlinks supported by the publishing system:</span></span>

<span data-ttu-id="b49bd-225">En **URL-länk** kan vara en URL-sökväg som är relativ till roten i docs.Microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="b49bd-225">A **URL link** can be a URL path that is relative to the root of docs.microsoft.com.</span></span> <span data-ttu-id="b49bd-226">Eller en absolut URL som innehåller fullständig URL-syntax.</span><span class="sxs-lookup"><span data-stu-id="b49bd-226">Or an absolute URL that include the full URL syntax.</span></span> <span data-ttu-id="b49bd-227">Exempelvis: `https:/github.com/MicrosoftDocs/PowerShell-Docs`</span><span class="sxs-lookup"><span data-stu-id="b49bd-227">For example: `https:/github.com/MicrosoftDocs/PowerShell-Docs`</span></span>

- <span data-ttu-id="b49bd-228">Använd URL-länkar när du länkar till innehåll utanför PowerShell-dokument eller mellan cmdlet-referenser och konceptuella artiklar i PowerShell-dokument. Det enklaste sättet att skapa en relativ länk är att kopiera URL: en från webbläsaren och sedan ta bort `https://docs.microsoft.com/en-us` den från det värde som du klistrar in i markdown.</span><span class="sxs-lookup"><span data-stu-id="b49bd-228">Use URL links when linking to content outside of PowerShell-Docs or between cmdlet reference and conceptual articles within PowerShell-docs. The simplest way to create a relative link is to copy the URL from your browser then remove `https://docs.microsoft.com/en-us` from the value you paste into markdown.</span></span>
- <span data-ttu-id="b49bd-229">Ta inte med språk i URL: er för Microsoft-egenskaper (t. ex.</span><span class="sxs-lookup"><span data-stu-id="b49bd-229">Do not include locales in URLs on Microsoft properties (eg.</span></span> <span data-ttu-id="b49bd-230">ta bort `/en-us` från URL).</span><span class="sxs-lookup"><span data-stu-id="b49bd-230">remove `/en-us` from URL).</span></span>
- <span data-ttu-id="b49bd-231">Ta bort alla onödiga frågeparametrar från URL-adressen om du inte behöver länka till en viss version av en artikel.</span><span class="sxs-lookup"><span data-stu-id="b49bd-231">Remove any unnecessary query parameters from the URL unless you need to link to a specific version of an article.</span></span> <span data-ttu-id="b49bd-232">Exempel:</span><span class="sxs-lookup"><span data-stu-id="b49bd-232">Examples:</span></span>
  - <span data-ttu-id="b49bd-233">`?view=powershell-5.1` – Detta används för att länka till en angiven version av PowerShell</span><span class="sxs-lookup"><span data-stu-id="b49bd-233">`?view=powershell-5.1` - this is used to link to a specific version of PowerShell</span></span>
  - <span data-ttu-id="b49bd-234">`?redirectedfrom=MSDN` – Detta läggs till i URL: en när du omdirigeras från en gammal artikel till en ny plats</span><span class="sxs-lookup"><span data-stu-id="b49bd-234">`?redirectedfrom=MSDN` - this is added to the URL when you get redirected from an old article to its new location</span></span>
- <span data-ttu-id="b49bd-235">Alla URL: er till externa webbplatser bör använda HTTPS om det inte är giltigt för mål platsen.</span><span class="sxs-lookup"><span data-stu-id="b49bd-235">All URLs to external websites should use HTTPS unless that is not valid for the target site.</span></span>

<span data-ttu-id="b49bd-236">En **fil länk** används för att länka från en referens artikel till en annan, eller från en konceptuell artikel till en annan.</span><span class="sxs-lookup"><span data-stu-id="b49bd-236">A **file link** is used to link from one reference article to another, or from one conceptual article to another.</span></span> <span data-ttu-id="b49bd-237">Om du behöver länka till en referens artikel för en viss version av PowerShell måste du använda en URL-länk.</span><span class="sxs-lookup"><span data-stu-id="b49bd-237">If you need to link to a reference article for a specific version of PowerShell, then you must use a URL link.</span></span>

- <span data-ttu-id="b49bd-238">Fil länkar innehåller en relativ fil Sök väg (till exempel: `../folder/file.md` )</span><span class="sxs-lookup"><span data-stu-id="b49bd-238">File links contain a relative file path (for example: `../folder/file.md`)</span></span>
- <span data-ttu-id="b49bd-239">Alla fil Sök vägar använder snedstreck ( `/` )-tecken</span><span class="sxs-lookup"><span data-stu-id="b49bd-239">All file paths use forward-slash (`/`) characters</span></span>

<span data-ttu-id="b49bd-240">Djup länkning tillåts för både URL-adresser och fil länkar.</span><span class="sxs-lookup"><span data-stu-id="b49bd-240">Deep linking is allowed on both URL and file links.</span></span> <span data-ttu-id="b49bd-241">Lägg till fäst punkten i slutet av mål Sök vägen.</span><span class="sxs-lookup"><span data-stu-id="b49bd-241">Add the anchor to the end of the target path.</span></span>
<span data-ttu-id="b49bd-242">Exempel:</span><span class="sxs-lookup"><span data-stu-id="b49bd-242">For example:</span></span>

- `[about_Splatting](about_Splatting.md#splatting-with-arrays)`
- `[custom key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings)`

<span data-ttu-id="b49bd-243">Mer information finns i [använda länkar i dokumentation](/contribute/how-to-write-links).</span><span class="sxs-lookup"><span data-stu-id="b49bd-243">For more information, see [Use links in documentation](/contribute/how-to-write-links).</span></span>

## <a name="formatting-command-syntax-elements"></a><span data-ttu-id="b49bd-244">Formatera element i kommandosyntax</span><span class="sxs-lookup"><span data-stu-id="b49bd-244">Formatting command syntax elements</span></span>

- <span data-ttu-id="b49bd-245">Använd alltid det fullständiga namnet för cmdletar och parametrar.</span><span class="sxs-lookup"><span data-stu-id="b49bd-245">Always use the full name for cmdlets and parameters.</span></span> <span data-ttu-id="b49bd-246">Undvik att använda alias om du inte specifikt demonstrerar aliaset.</span><span class="sxs-lookup"><span data-stu-id="b49bd-246">Avoid using aliases unless you are specifically demonstrating the alias.</span></span>

- <span data-ttu-id="b49bd-247">Egenskap, parameter, objekt, typ namn, klass namn, klass metoder ska vara **fetstil**.</span><span class="sxs-lookup"><span data-stu-id="b49bd-247">Property, parameter, object, type names, class names, class methods should be **bold**.</span></span>
  - <span data-ttu-id="b49bd-248">Egenskaps-och parameter värden ska omslutas i baktick ( `` ` `` ).</span><span class="sxs-lookup"><span data-stu-id="b49bd-248">Property and parameter values should be wrapped in backticks (`` ` ``).</span></span>
  - <span data-ttu-id="b49bd-249">När du refererar till typer med hjälp av den hakparentesa stilen använder du baktick.</span><span class="sxs-lookup"><span data-stu-id="b49bd-249">When referring to types using the bracketed style, use backticks.</span></span> <span data-ttu-id="b49bd-250">Exempelvis: `[System.Io.FileInfo]`</span><span class="sxs-lookup"><span data-stu-id="b49bd-250">For example: `[System.Io.FileInfo]`</span></span>

- <span data-ttu-id="b49bd-251">Språk nyckelord, cmdlet-namn, funktioner, variabler, interna EXEs, fil Sök vägar och infogade syntaxer ska omslutas av tecken i text Ticket ( `` ` `` ).</span><span class="sxs-lookup"><span data-stu-id="b49bd-251">Language keywords, cmdlet names, functions, variables, native EXEs, file paths, and inline syntax examples should be wrapped in backtick (`` ` ``) characters.</span></span>

  <span data-ttu-id="b49bd-252">Exempel:</span><span class="sxs-lookup"><span data-stu-id="b49bd-252">For example:</span></span>

  ~~~markdown
  The following code uses `Get-ChildItem` to list the contents of `C:\Windows` and assigns
  the output to the `$files` variable.

  ```powershell
  $files = Get-ChildItem C:\Windows
  ```
  ~~~

  - <span data-ttu-id="b49bd-253">När du refererar till en parameter med namnet ska det skrivas med **fetstil**.</span><span class="sxs-lookup"><span data-stu-id="b49bd-253">When referring to a parameter by name, the name should be **bold**.</span></span> <span data-ttu-id="b49bd-254">När du illustrerar användningen av en parameter med avstavningsprefixet ska parametern omslutas av grava accenter.</span><span class="sxs-lookup"><span data-stu-id="b49bd-254">When illustrating the use of a parameter with the hyphen prefix, the parameter should be wrapped in backticks.</span></span> <span data-ttu-id="b49bd-255">Exempel:</span><span class="sxs-lookup"><span data-stu-id="b49bd-255">For example:</span></span>

    ```markdown
    The parameter's name is **Name**, but it is typed as `-Name` when used on the command
    line as a parameter.
    ```

  - <span data-ttu-id="b49bd-256">När du visar exempel på användning av ett externt kommando ska exemplet omslutas av grava accenter.</span><span class="sxs-lookup"><span data-stu-id="b49bd-256">When showing example usage of an external command, the example should be wrapped in backticks.</span></span>
    <span data-ttu-id="b49bd-257">Ta alltid med fil tillägget i det inbyggda kommandot.</span><span class="sxs-lookup"><span data-stu-id="b49bd-257">Always include the file extension in the native command.</span></span> <span data-ttu-id="b49bd-258">Exempel:</span><span class="sxs-lookup"><span data-stu-id="b49bd-258">For example:</span></span>

    ```markdown
    To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.
    ```

    <span data-ttu-id="b49bd-259">Inklusive fil tillägget säkerställer att rätt kommando körs enligt PowerShell: s kommando prioritet.</span><span class="sxs-lookup"><span data-stu-id="b49bd-259">Including the file extension ensures that the correct command is executed according PowerShell's command precedence.</span></span>

- <span data-ttu-id="b49bd-260">När du skriver en konceptuell artikel (till skillnad från referensinnehåll) ska den första förekomsten av ett cmdlet-namn hyperlänkas till cmdlet-dokumentationen.</span><span class="sxs-lookup"><span data-stu-id="b49bd-260">When writing a conceptual article (as opposed to reference content), the first instance of a cmdlet name should be hyperlinked to the cmdlet documentation.</span></span> <span data-ttu-id="b49bd-261">Använd inte grava accenter, fetstil eller andra markeringar inuti hakparenteserna för en hyperlänk.</span><span class="sxs-lookup"><span data-stu-id="b49bd-261">Do not use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>

  <span data-ttu-id="b49bd-262">Exempel:</span><span class="sxs-lookup"><span data-stu-id="b49bd-262">For example:</span></span>

  ```markdown
  This [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet
  uses the **Object** parameter to ...
  ```

  <span data-ttu-id="b49bd-263">Mer information finns i avsnittet [hyperlinks](#hyperlinks) i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="b49bd-263">For more information, see [Hyperlinks](#hyperlinks) section of this article.</span></span>

## <a name="markdown-for-code-samples"></a><span data-ttu-id="b49bd-264">Markdown för kod exempel</span><span class="sxs-lookup"><span data-stu-id="b49bd-264">Markdown for code samples</span></span>

<span data-ttu-id="b49bd-265">Markdown stöder två olika kodformat:</span><span class="sxs-lookup"><span data-stu-id="b49bd-265">Markdown supports two different code styles:</span></span>

- <span data-ttu-id="b49bd-266">**Kod sträcker sig över (infogade)** – markerade med ett enda baktick ( `` ` `` )-tecken.</span><span class="sxs-lookup"><span data-stu-id="b49bd-266">**Code spans (inline)** - marked by a single backtick (`` ` ``) character.</span></span> <span data-ttu-id="b49bd-267">Används inom ett stycke i stället för som ett fristående block.</span><span class="sxs-lookup"><span data-stu-id="b49bd-267">Used within a paragraph rather than as a standalone block.</span></span>
- <span data-ttu-id="b49bd-268">**Kodblock** – ett block med flera rader som omges av tredubbel-bakticket ( `` ``` `` )-strängar.</span><span class="sxs-lookup"><span data-stu-id="b49bd-268">**Code blocks** - a multi-line block surrounded by triple-backtick (`` ``` ``) strings.</span></span> <span data-ttu-id="b49bd-269">Kod block kan också ha en språk etikett efter bakstrecken.</span><span class="sxs-lookup"><span data-stu-id="b49bd-269">Code blocks may also have a language label following the backticks.</span></span> <span data-ttu-id="b49bd-270">Språk etiketten aktiverar syntax för innehållet i kod blocket.</span><span class="sxs-lookup"><span data-stu-id="b49bd-270">The language label enables syntax highlighting for the contents of the code block.</span></span>

<span data-ttu-id="b49bd-271">Alla kodblock ska finnas i en kodavgränsning.</span><span class="sxs-lookup"><span data-stu-id="b49bd-271">All code blocks should be contained in a code fence.</span></span> <span data-ttu-id="b49bd-272">Använd aldrig indrag för kodblock.</span><span class="sxs-lookup"><span data-stu-id="b49bd-272">Never use indentation for code blocks.</span></span> <span data-ttu-id="b49bd-273">Markdown tillåter det här mönstret, men det kan vara problematiskt och bör undvikas.</span><span class="sxs-lookup"><span data-stu-id="b49bd-273">Markdown allows this pattern but it can be problematic and should be avoided.</span></span>

<span data-ttu-id="b49bd-274">Ett kodblock är en eller flera kodrader som omges av en kod gräns för tredubbelt skal streck ( `` ``` `` ).</span><span class="sxs-lookup"><span data-stu-id="b49bd-274">A code block is one or more lines of code surrounded by a triple-backtick (`` ``` ``) code fence.</span></span>
<span data-ttu-id="b49bd-275">Kodavgränsningsmarkörerna måste finnas på en egen rad före och efter kodexemplet.</span><span class="sxs-lookup"><span data-stu-id="b49bd-275">The code fence markers must be on their own line before and after the code sample.</span></span> <span data-ttu-id="b49bd-276">Markören i början av kodblocket kan ha en valfri språketikett.</span><span class="sxs-lookup"><span data-stu-id="b49bd-276">The marker at the start of the code block may have an optional language label.</span></span> <span data-ttu-id="b49bd-277">Microsofts Open Publishing System (OPS) använder språketiketten för att stödja markeringsfunktionen för syntax.</span><span class="sxs-lookup"><span data-stu-id="b49bd-277">Microsoft's Open Publishing System (OPS) uses the language label to support the syntax highlighting feature.</span></span>

<span data-ttu-id="b49bd-278">En fullständig lista över språk koder som stöds finns i [avgränsade kodblock](/contribute/code-in-docs#fenced-code-blocks) i den centraliserade deltagar guiden.</span><span class="sxs-lookup"><span data-stu-id="b49bd-278">For a full list of supported language tags, see [Fenced code blocks](/contribute/code-in-docs#fenced-code-blocks) in the centralized contributor guide.</span></span>

<span data-ttu-id="b49bd-279">OPS lägger också till knappen **Kopiera**, som kopierar innehållet i kodblocket till Urklipp.</span><span class="sxs-lookup"><span data-stu-id="b49bd-279">OPS also adds a **Copy** button that copies the contents of the code block to the clipboard.</span></span> <span data-ttu-id="b49bd-280">På så sätt kan du snabbt klistra in koden i ett skript för att testa kod exemplet.</span><span class="sxs-lookup"><span data-stu-id="b49bd-280">This allows you to quickly paste the code into a script to test the code sample.</span></span> <span data-ttu-id="b49bd-281">Men inte alla exempel i vår dokumentation är avsedda att köras i befintligt skick.</span><span class="sxs-lookup"><span data-stu-id="b49bd-281">However, not all examples in our documentation are intended to be run as-is.</span></span> <span data-ttu-id="b49bd-282">Vissa kod block är enkla illustrationer av ett PowerShell-begrepp.</span><span class="sxs-lookup"><span data-stu-id="b49bd-282">Some code blocks are simple illustrations of a PowerShell concept.</span></span>

<span data-ttu-id="b49bd-283">Det finns tre typer av kod block som används i vår dokumentation:</span><span class="sxs-lookup"><span data-stu-id="b49bd-283">There are three types code blocks used in our documentation:</span></span>

1. <span data-ttu-id="b49bd-284">Kommandosyntax</span><span class="sxs-lookup"><span data-stu-id="b49bd-284">Syntax blocks</span></span>
1. <span data-ttu-id="b49bd-285">Illustrerande exempel</span><span class="sxs-lookup"><span data-stu-id="b49bd-285">Illustrative examples</span></span>
1. <span data-ttu-id="b49bd-286">Körbara exempel</span><span class="sxs-lookup"><span data-stu-id="b49bd-286">Executable examples</span></span>

### <a name="syntax-code-blocks"></a><span data-ttu-id="b49bd-287">Kod block för syntax</span><span class="sxs-lookup"><span data-stu-id="b49bd-287">Syntax code blocks</span></span>

<span data-ttu-id="b49bd-288">Syntax Code block används för att beskriva en kommandos syntaktiska struktur.</span><span class="sxs-lookup"><span data-stu-id="b49bd-288">Syntax code blocks are used to describe the syntactic structure of a command.</span></span> <span data-ttu-id="b49bd-289">Använd inte en språktagg på kod avgränsningen.</span><span class="sxs-lookup"><span data-stu-id="b49bd-289">Do not use a language tag on the code fence.</span></span> <span data-ttu-id="b49bd-290">Det här exemplet illustrerar alla möjliga parametrar för cmdleten `Get-Command`.</span><span class="sxs-lookup"><span data-stu-id="b49bd-290">This example illustrates all the possible parameters of the `Get-Command` cmdlet.</span></span>

~~~markdown
```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
  [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax]
  [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
  [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```
~~~

<span data-ttu-id="b49bd-291">I det här exemplet beskrivs satsen `for` i generaliserade villkor:</span><span class="sxs-lookup"><span data-stu-id="b49bd-291">This example describes the `for` statement in generalized terms:</span></span>

~~~markdown
```
for (<init>; <condition>; <repeat>)
{<statement list>}
```
~~~

### <a name="illustrative-examples"></a><span data-ttu-id="b49bd-292">Illustrerande exempel</span><span class="sxs-lookup"><span data-stu-id="b49bd-292">Illustrative examples</span></span>

<span data-ttu-id="b49bd-293">Illustrerande exempel används för att förklara ett PowerShell-begrepp.</span><span class="sxs-lookup"><span data-stu-id="b49bd-293">Illustrative examples are used to explain a PowerShell concept.</span></span> <span data-ttu-id="b49bd-294">De är inte avsedda att kopieras till Urklipp för körning.</span><span class="sxs-lookup"><span data-stu-id="b49bd-294">They are not meant to be copied to the clipboard for execution.</span></span> <span data-ttu-id="b49bd-295">Dessa används vanligt vis för enkla exempel som är lätta att skriva och som är lätta att förstå.</span><span class="sxs-lookup"><span data-stu-id="b49bd-295">These are most commonly used for simple examples that are easy to type and easy to understand.</span></span> <span data-ttu-id="b49bd-296">Kod blocket kan innehålla PowerShell-prompten och exempel på utdata.</span><span class="sxs-lookup"><span data-stu-id="b49bd-296">The code block can include the PowerShell prompt and example output.</span></span>

<span data-ttu-id="b49bd-297">Här är ett enkelt exempel som illustrerar PowerShell-jämförelse operatorer.</span><span class="sxs-lookup"><span data-stu-id="b49bd-297">Here is a simple example illustrating the PowerShell comparison operators.</span></span> <span data-ttu-id="b49bd-298">I det här fallet förväntar vi oss inte att läsaren ska kopiera och köra exemplet.</span><span class="sxs-lookup"><span data-stu-id="b49bd-298">In this case, we don't intend the reader to copy and run this example.</span></span>

~~~markdown
```powershell
PS> 2 -eq 2
True

PS> 2 -eq 3
False

PS>  1,2,3 -eq 2
2

PS> "abc" -eq "abc"
True

PS> "abc" -eq "abc", "def"
False

PS> "abc", "def" -eq "abc"
abc
```
~~~

### <a name="executable-examples"></a><span data-ttu-id="b49bd-299">Körbara exempel</span><span class="sxs-lookup"><span data-stu-id="b49bd-299">Executable examples</span></span>

<span data-ttu-id="b49bd-300">Avancerade exempel eller exempel som är avsedda att kopieras och köras ska använda följande block-Style-markering:</span><span class="sxs-lookup"><span data-stu-id="b49bd-300">Complex examples, or examples that are intended to be copied and executed, should use the following block-style markup:</span></span>

~~~markdown
```powershell
<Your PowerShell code goes here>
```
~~~

<span data-ttu-id="b49bd-301">De utdata som visas av PowerShell-kommandon måste anges i ett kodblock för **utdata** för att förhindra markering av syntax.</span><span class="sxs-lookup"><span data-stu-id="b49bd-301">The output displayed by PowerShell commands should be enclosed in an **Output** code block to prevent syntax highlighting.</span></span> <span data-ttu-id="b49bd-302">Exempel:</span><span class="sxs-lookup"><span data-stu-id="b49bd-302">For example:</span></span>

~~~markdown
```powershell
Get-Command -Module Microsoft.PowerShell.Security
```

```Output
CommandType  Name                        Version    Source
-----------  ----                        -------    ------
Cmdlet       ConvertFrom-SecureString    3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       ConvertTo-SecureString      3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-Acl                     3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-AuthenticodeSignature   3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-CmsMessage              3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-Credential              3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-ExecutionPolicy         3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Get-PfxCertificate          3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       New-FileCatalog             3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Protect-CmsMessage          3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-Acl                     3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-AuthenticodeSignature   3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Set-ExecutionPolicy         3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Test-FileCatalog            3.0.0.0    Microsoft.PowerShell.Security
Cmdlet       Unprotect-CmsMessage        3.0.0.0    Microsoft.PowerShell.Security
```
~~~

<span data-ttu-id="b49bd-303">Kodetiketten **Utdata** är inte ett officiellt ”språk” som stöds av syntaxens markeringssystem.</span><span class="sxs-lookup"><span data-stu-id="b49bd-303">The **Output** code label is not an official "language" supported by the syntax highlighting system.</span></span>
<span data-ttu-id="b49bd-304">Den här etiketten är dock användbar eftersom OPS lägger till etiketten "utdata" i rutan med kod rutan på webb sidan.</span><span class="sxs-lookup"><span data-stu-id="b49bd-304">However, this label is useful because OPS adds the "Output" label to the code box frame on the web page.</span></span> <span data-ttu-id="b49bd-305">Kod rutan "utdata" har ingen markering av syntax.</span><span class="sxs-lookup"><span data-stu-id="b49bd-305">The "Output" code box has no syntax highlighting.</span></span>

## <a name="coding-style-rules"></a><span data-ttu-id="b49bd-306">Regler för kodningsformat</span><span class="sxs-lookup"><span data-stu-id="b49bd-306">Coding style rules</span></span>

### <a name="avoid-line-continuation-in-code-samples"></a><span data-ttu-id="b49bd-307">Undvik radfortsättning i kodexempel</span><span class="sxs-lookup"><span data-stu-id="b49bd-307">Avoid line continuation in code samples</span></span>

<span data-ttu-id="b49bd-308">Undvik att använda radfortsättningstecken (`` ` ``) i PowerShell-kodexempel.</span><span class="sxs-lookup"><span data-stu-id="b49bd-308">Avoid using line continuation characters (`` ` ``) in PowerShell code examples.</span></span> <span data-ttu-id="b49bd-309">De är svåra att se och kan orsaka problem om det finns extra blanksteg i slutet av raden.</span><span class="sxs-lookup"><span data-stu-id="b49bd-309">These are hard to see and can cause problems if there are extra spaces at the end of the line.</span></span>

- <span data-ttu-id="b49bd-310">Använd PowerShell-ihopbuntning för att minska radlängden för cmdletar som har många parametrar.</span><span class="sxs-lookup"><span data-stu-id="b49bd-310">Use PowerShell splatting to reduce line length for cmdlets that have a lot of parameters.</span></span>
- <span data-ttu-id="b49bd-311">Dra nytta av PowerShells naturliga radbrytningsmöjligheter, t.ex. efter pipe-tecken (`|`), inledande klammerparentes, parenteser och hakparenteser.</span><span class="sxs-lookup"><span data-stu-id="b49bd-311">Take advantage of PowerShell's natural line break opportunities, like after pipe (`|`) characters, opening braces, parentheses, and brackets.</span></span>

### <a name="avoid-using-powershell-prompts-in-examples"></a><span data-ttu-id="b49bd-312">Undvik att använda PowerShell-prompter i exempel</span><span class="sxs-lookup"><span data-stu-id="b49bd-312">Avoid using PowerShell prompts in examples</span></span>

<span data-ttu-id="b49bd-313">Användning av frågesträngen rekommenderas inte och bör begränsas till scenarier som är avsedda att illustrera användning av kommandoraden.</span><span class="sxs-lookup"><span data-stu-id="b49bd-313">Use of the prompt string is discouraged and should be limited to scenarios that are meant to illustrate command line usage.</span></span> <span data-ttu-id="b49bd-314">I de flesta av dessa exempel bör LED text strängen vara `PS>` .</span><span class="sxs-lookup"><span data-stu-id="b49bd-314">For most of these examples, the prompt string should be `PS>`.</span></span> <span data-ttu-id="b49bd-315">Den här frågan är oberoende av OS-/regionsspecifika indikatorer.</span><span class="sxs-lookup"><span data-stu-id="b49bd-315">This prompt is independent of OS-specific indicators.</span></span>

<span data-ttu-id="b49bd-316">Frågor krävs för exempel som illustrerar kommandon som förändrar frågan, eller när sökvägen som visas är viktig för scenariot som illustreras.</span><span class="sxs-lookup"><span data-stu-id="b49bd-316">Prompts are required for examples that illustrate commands that alter the prompt or when the path displayed is significant to the scenario being illustrated.</span></span> <span data-ttu-id="b49bd-317">I följande exempel visas hur frågan ändras när du använder registerprovidern.</span><span class="sxs-lookup"><span data-stu-id="b49bd-317">The following example illustrates how the prompt changes when using the Registry provider.</span></span>

```powershell
PS C:\> cd HKCU:\System\
PS HKCU:\System\> dir

    Hive: HKEY_CURRENT_USER\System

Name                   Property
----                   --------
CurrentControlSet
GameConfigStore        GameDVR_Enabled                       : 1
                       GameDVR_FSEBehaviorMode               : 2
                       Win32_AutoGameModeDefaultProfile      : {2, 0, 1, 0...}
                       Win32_GameModeRelatedProcesses        : {1, 0, 1, 0...}
                       GameDVR_HonorUserFSEBehaviorMode      : 0
                       GameDVR_DXGIHonorFSEWindowsCompatible : 0
```

### <a name="do-not-use-aliases-in-examples"></a><span data-ttu-id="b49bd-318">Använd inte alias i exempel</span><span class="sxs-lookup"><span data-stu-id="b49bd-318">Do not use aliases in examples</span></span>

<span data-ttu-id="b49bd-319">Du bör alltid använda det fullständiga namnet på alla cmdletar och parametrar om du inte diskuterar aliaset specifikt.</span><span class="sxs-lookup"><span data-stu-id="b49bd-319">You should always use the full name of all cmdlets and parameters unless you are specifically talking about the alias.</span></span> <span data-ttu-id="b49bd-320">Cmdlet-och parameter namn måste ha rätt Pascal-bokstäver namn.</span><span class="sxs-lookup"><span data-stu-id="b49bd-320">Cmdlet and parameter names must use the proper Pascal-cased names.</span></span>

### <a name="using-parameters-in-examples"></a><span data-ttu-id="b49bd-321">Använda parametrar i exempel</span><span class="sxs-lookup"><span data-stu-id="b49bd-321">Using parameters in examples</span></span>

<span data-ttu-id="b49bd-322">Undvik att använda positionsparametrar.</span><span class="sxs-lookup"><span data-stu-id="b49bd-322">Avoid using positional parameters.</span></span> <span data-ttu-id="b49bd-323">I allmänhet bör du alltid inkludera parameter namnet i ett exempel, även om parametern är i position.</span><span class="sxs-lookup"><span data-stu-id="b49bd-323">In general, you should always include the parameter name in an example, even if the parameter is positional.</span></span> <span data-ttu-id="b49bd-324">På så sätt minskar du risken för förvirring i exemplen.</span><span class="sxs-lookup"><span data-stu-id="b49bd-324">This reduces the chance of confusion in your examples.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b49bd-325">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="b49bd-325">Next steps</span></span>

[<span data-ttu-id="b49bd-326">Redigera cmdlet-referens</span><span class="sxs-lookup"><span data-stu-id="b49bd-326">Editing cmdlet reference</span></span>](editing-cmdlet-ref.md)

<!-- External URLs -->
[platyPS]: https://github.com/PowerShell/platyPS
[markdig]: https://github.com/lunet-io/markdig
[CommonMark]: https://spec.commonmark.org/
[atx]: https://github.github.com/gfm/#atx-headings
[pascal-case]: https://en.wikipedia.org/wiki/PascalCase
[reflow]: https://marketplace.visualstudio.com/items?itemName=marvhen.reflow-markdown
