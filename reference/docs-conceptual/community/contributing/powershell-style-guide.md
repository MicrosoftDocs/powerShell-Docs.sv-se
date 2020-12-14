---
title: Stilguide för PowerShell-Docs
description: Den här artikeln innehåller regler för format för att skriva PowerShell-dokumentation.
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: 6f23f63cffc9fed9cbbcf84539875bfaf4247732
ms.sourcegitcommit: 61765d08321623743dc5db5367160f6982fe7857
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97352679"
---
# <a name="powershell-docs-style-guide"></a><span data-ttu-id="2ea1f-103">Stilguide för PowerShell-Docs</span><span class="sxs-lookup"><span data-stu-id="2ea1f-103">PowerShell-Docs style guide</span></span>

<span data-ttu-id="2ea1f-104">Den här artikeln innehåller rikt linjer som är speciella för PowerShell-Docs innehållet.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-104">This article provides style guidance specific to the PowerShell-Docs content.</span></span> <span data-ttu-id="2ea1f-105">Den bygger på den information som beskrivs i [översikten](overview.md#get-started-writing-docs).</span><span class="sxs-lookup"><span data-stu-id="2ea1f-105">It builds on the information outlined in the [Overview](overview.md#get-started-writing-docs).</span></span>

## <a name="product-terminology"></a><span data-ttu-id="2ea1f-106">Produktterminologi</span><span class="sxs-lookup"><span data-stu-id="2ea1f-106">Product Terminology</span></span>

<span data-ttu-id="2ea1f-107">Det finns flera varianter av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-107">There are several variants of PowerShell.</span></span>

- <span data-ttu-id="2ea1f-108">**PowerShell** – Det här är standardinställningen.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-108">**PowerShell** - This is the default.</span></span> <span data-ttu-id="2ea1f-109">Vi betraktar PowerShell 7 och bortom det som är den sanna PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-109">We consider PowerShell 7 and beyond to be the one, true PowerShell.</span></span>
- <span data-ttu-id="2ea1f-110">**PowerShell Core** – PowerShell som bygger på .net Core.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-110">**PowerShell Core** - PowerShell built on .NET Core.</span></span> <span data-ttu-id="2ea1f-111">Användning av termen **Core** bör begränsas till fall där det är nödvändigt att skilja den från Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-111">Usage of the term **Core** should be limited to cases where it's necessary to differentiate it from Windows PowerShell.</span></span>
- <span data-ttu-id="2ea1f-112">**Windows PowerShell** – PowerShell som bygger på .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-112">**Windows PowerShell** - PowerShell built on .NET Framework.</span></span> <span data-ttu-id="2ea1f-113">Windows PowerShell-fartyg endast på Windows och kräver hela ramverket.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-113">Windows PowerShell ships only on Windows and requires the complete Framework.</span></span>

  <span data-ttu-id="2ea1f-114">I allmänhet kan referenser till "Windows PowerShell" i dokumentationen ändras till _PowerShell_.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-114">In general, references to "Windows PowerShell" in documentation can be changed to _PowerShell_.</span></span>
  <span data-ttu-id="2ea1f-115">"Windows PowerShell" ska användas när _Windows PowerShell_-ett enskilt beteende diskuteras.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-115">"Windows PowerShell" should be used when _Windows PowerShell_-specific behavior is being discussed.</span></span>

<span data-ttu-id="2ea1f-116">Relaterade produkter</span><span class="sxs-lookup"><span data-stu-id="2ea1f-116">Related products</span></span>

- <span data-ttu-id="2ea1f-117">**Visual Studio Code (vs Code)** – det här är Microsofts kostnads fria redigerare med öppen källkod.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-117">**Visual Studio Code (VS Code)** - This is Microsoft's free, open-source editor.</span></span> <span data-ttu-id="2ea1f-118">I första omnämnandet ska det fullständiga namnet användas.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-118">At first mention, the full name should be used.</span></span> <span data-ttu-id="2ea1f-119">Efter det kan du använda **vs Code**.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-119">After that you may use **VS Code**.</span></span> <span data-ttu-id="2ea1f-120">Använd inte "VSCode".</span><span class="sxs-lookup"><span data-stu-id="2ea1f-120">Don't use "VSCode".</span></span>
- <span data-ttu-id="2ea1f-121">**PowerShell-tillägg för Visual Studio Code** – tillägget FÖRVANDLAr vs-kod till önskad IDE för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-121">**PowerShell Extension for Visual Studio Code** - The extension turns VS Code into the preferred IDE for PowerShell.</span></span> <span data-ttu-id="2ea1f-122">I första omnämnandet ska det fullständiga namnet användas.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-122">At first mention, the full name should be used.</span></span> <span data-ttu-id="2ea1f-123">Efter det kan du använda **PowerShell-tillägget**.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-123">After that you may use **PowerShell extension**.</span></span>
- <span data-ttu-id="2ea1f-124">**Azure PowerShell** – det här är en samling PowerShell-moduler som används för att hantera Azure-tjänster.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-124">**Azure PowerShell** - This is the collection of PowerShell modules used to manage Azure services.</span></span>
- <span data-ttu-id="2ea1f-125">**Azure Stack PowerShell** – det här är samlingen av PowerShell-moduler som används för att hantera Microsofts hybrid moln lösning.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-125">**Azure Stack PowerShell** - This is the collection of PowerShell modules used to manage Microsoft's hybrid cloud solution.</span></span>

## <a name="markdown-specifics"></a><span data-ttu-id="2ea1f-126">Markdown-information</span><span class="sxs-lookup"><span data-stu-id="2ea1f-126">Markdown specifics</span></span>

<span data-ttu-id="2ea1f-127">Microsoft Open Publishing system (OPS) som bygger vår dokumentation använder [markdig][] för att bearbeta markdown-dokumenten.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-127">The Microsoft Open Publishing System (OPS) that builds our documentation uses [markdig][] to process the Markdown documents.</span></span> <span data-ttu-id="2ea1f-128">Markdig analyserar dokumenten baserat på reglerna för den senaste [CommonMark][] -specifikationen.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-128">Markdig parses the documents based on the rules of the latest [CommonMark][] specification.</span></span>

<span data-ttu-id="2ea1f-129">Den nya CommonMark-specifikationen är mycket strängare om konstruktion av vissa markdown-element.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-129">The new CommonMark spec is much stricter about the construction of some Markdown elements.</span></span> <span data-ttu-id="2ea1f-130">Var uppmärksam på de uppgifter som anges i det här dokumentet.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-130">Pay close attention to the details provided in this document.</span></span>

### <a name="blank-lines-spaces-and-tabs"></a><span data-ttu-id="2ea1f-131">Tomma rader, blanksteg och tabbar</span><span class="sxs-lookup"><span data-stu-id="2ea1f-131">Blank lines, spaces, and tabs</span></span>

<span data-ttu-id="2ea1f-132">Tomma rader indikerar också slutet av ett block i Markdown.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-132">Blank lines also signal the end of a block in Markdown.</span></span> <span data-ttu-id="2ea1f-133">Det måste finnas ett tomt värde mellan Markdown-block av olika typer (till exempel mellan ett stycke och en lista eller rubrik).</span><span class="sxs-lookup"><span data-stu-id="2ea1f-133">There should be a single blank between Markdown blocks of different types (for example, between a paragraph and a list or header).</span></span>

<span data-ttu-id="2ea1f-134">Flera tomma rader i följd återges som en enda tom rad i HTML.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-134">Multiple consecutive blank lines render as a single blank line in HTML.</span></span> <span data-ttu-id="2ea1f-135">De tjänar inget syfte.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-135">They serve no purpose.</span></span>
<span data-ttu-id="2ea1f-136">I ett kodblock bryts kod blocket i löpande tomma rader.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-136">Within a code block, consecutive blank lines break the code block.</span></span>

<span data-ttu-id="2ea1f-137">Ta bort extra blanksteg i slutet av rader.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-137">Remove extra spaces at the end of lines.</span></span>

> [!NOTE]
> <span data-ttu-id="2ea1f-138">Avståndet har betydelse i Markdown.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-138">Spacing is significant in Markdown.</span></span> <span data-ttu-id="2ea1f-139">Använd alltid blanksteg i stället för hårda tabbar.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-139">Always uses spaces instead of hard tabs.</span></span> <span data-ttu-id="2ea1f-140">Avslutande blank steg kan ändra hur markdown återges.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-140">Trailing spaces can change how Markdown renders.</span></span>

### <a name="titles-and-headings"></a><span data-ttu-id="2ea1f-141">Rubriker</span><span class="sxs-lookup"><span data-stu-id="2ea1f-141">Titles and headings</span></span>

<span data-ttu-id="2ea1f-142">Använd bara [ATX-rubriker][atx] (# style, i stället för `=` eller `-` stilrubriker).</span><span class="sxs-lookup"><span data-stu-id="2ea1f-142">Only use [ATX headings][atx] (# style, as opposed to `=` or `-` style headers).</span></span>

- <span data-ttu-id="2ea1f-143">Använd bara inledande versal i meningar, och den första bokstaven i en rubrik skrivas med versal</span><span class="sxs-lookup"><span data-stu-id="2ea1f-143">Use sentence case - only proper nouns and the first letter of a title or header should be capitalized</span></span>
- <span data-ttu-id="2ea1f-144">Det måste finnas ett blanksteg mellan `#` och den första bokstaven i rubriken</span><span class="sxs-lookup"><span data-stu-id="2ea1f-144">There must be a single space between the `#` and the first letter of the heading</span></span>
- <span data-ttu-id="2ea1f-145">Rubriker ska omges av en enda tom rad</span><span class="sxs-lookup"><span data-stu-id="2ea1f-145">Headings should be surrounded by a single blank line</span></span>
- <span data-ttu-id="2ea1f-146">Endast en H1 per dokument</span><span class="sxs-lookup"><span data-stu-id="2ea1f-146">Only one H1 per document</span></span>
- <span data-ttu-id="2ea1f-147">Rubrik nivåerna bör ökas med ett.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-147">Header levels should increment by one.</span></span> <span data-ttu-id="2ea1f-148">Hoppa inte över nivåer</span><span class="sxs-lookup"><span data-stu-id="2ea1f-148">Don't skip levels</span></span>
- <span data-ttu-id="2ea1f-149">Använd inte fetstil eller andra markeringar i sidhuvuden</span><span class="sxs-lookup"><span data-stu-id="2ea1f-149">Don't use bold or other markup in headers</span></span>

### <a name="limit-line-length-to-100-characters"></a><span data-ttu-id="2ea1f-150">Begränsa radlängden till 100 tecken</span><span class="sxs-lookup"><span data-stu-id="2ea1f-150">Limit line length to 100 characters</span></span>

<span data-ttu-id="2ea1f-151">Detta gäller för konceptuella artiklar och cmdlet-referens.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-151">This applies to conceptual articles and cmdlet reference.</span></span> <span data-ttu-id="2ea1f-152">Att begränsa rad längden ger bättre läsbarhet i git-differenser och historik.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-152">Limiting the line length improves the readability of git diffs and history.</span></span> <span data-ttu-id="2ea1f-153">Det gör det också enklare för andra skrivare att göra bidrag.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-153">It also makes it easier for other writers to make contributions.</span></span>

<span data-ttu-id="2ea1f-154">Använd tillägget [Flow markdown][reflow] i Visual Studio Code för att enkelt ommontera stycken för att passa den angivna rad längden.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-154">Use the [Reflow Markdown][reflow] extension in Visual Studio Code to easily reflow paragraphs to fit the prescribed line length.</span></span>

<span data-ttu-id="2ea1f-155">About_topics är begränsade till 80 tecken.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-155">About_topics are limited to 80 characters.</span></span> <span data-ttu-id="2ea1f-156">Mer detaljerad information finns i [formatera About_ filer](#formatting-about_-files).</span><span class="sxs-lookup"><span data-stu-id="2ea1f-156">For more specific information, see [Formatting About_ files](#formatting-about_-files).</span></span>

### <a name="lists"></a><span data-ttu-id="2ea1f-157">Listor</span><span class="sxs-lookup"><span data-stu-id="2ea1f-157">Lists</span></span>

<span data-ttu-id="2ea1f-158">Om listan innehåller flera meningar eller stycken bör du överväga att använda ett under rubrik i stället för en lista.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-158">If your list contains multiple sentences or paragraphs, consider using a sublevel header rather than a list.</span></span>

<span data-ttu-id="2ea1f-159">Listan ska omges av en enda tom rad.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-159">List should be surrounded by a single blank line.</span></span>

#### <a name="unordered-lists"></a><span data-ttu-id="2ea1f-160">Osorterade listor</span><span class="sxs-lookup"><span data-stu-id="2ea1f-160">Unordered lists</span></span>

<span data-ttu-id="2ea1f-161">Avsluta inte List objekt med en punkt om de inte innehåller flera meningar.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-161">Don't end list items with a period unless they contain multiple sentences.</span></span> <span data-ttu-id="2ea1f-162">Använd bindestreck (`-`) som punkter för listobjekt.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-162">Use the hyphen character (`-`) for list item bullets.</span></span> <span data-ttu-id="2ea1f-163">På så sätt undviker du sammanblandning med markeringen för fetstil eller kursiv stil, som använder asterisk [`*`].</span><span class="sxs-lookup"><span data-stu-id="2ea1f-163">This avoids confusion with bold or italic markup that uses the asterisk [`*`].</span></span> <span data-ttu-id="2ea1f-164">Om du vill lägga till ett stycke eller andra element under ett objekt i en punktlista infogar du en radbrytning och justerar indraget efter det första tecknet efter punkten.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-164">To include a paragraph or other elements under a bullet item, insert a line break and align indentation with the first character after the bullet.</span></span>

<span data-ttu-id="2ea1f-165">Exempel:</span><span class="sxs-lookup"><span data-stu-id="2ea1f-165">For example:</span></span>

```markdown
This is a list that contain child elements under a bullet item.

- First bullet item

  Sentence explaining the first bullet.

  - Child bullet item

    Sentence explaining the child bullet.

- Second bullet item
- Third bullet item
```

<span data-ttu-id="2ea1f-166">Det här är en lista som innehåller underordnade element under ett punkt objekt.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-166">This is a list that contains child elements under a bullet item.</span></span>

- <span data-ttu-id="2ea1f-167">Första objektet i punktlistan</span><span class="sxs-lookup"><span data-stu-id="2ea1f-167">First bullet item</span></span>

  <span data-ttu-id="2ea1f-168">Mening som beskriver den första punkten.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-168">Sentence explaining the first bullet.</span></span>

  - <span data-ttu-id="2ea1f-169">Underordnat punkt objekt</span><span class="sxs-lookup"><span data-stu-id="2ea1f-169">Child bullet item</span></span>

    <span data-ttu-id="2ea1f-170">Mening som förklarar den underordnade punkten.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-170">Sentence explaining the child bullet.</span></span>

- <span data-ttu-id="2ea1f-171">Andra objektet i punktlistan</span><span class="sxs-lookup"><span data-stu-id="2ea1f-171">Second bullet item</span></span>
- <span data-ttu-id="2ea1f-172">Tredje objektet i punktlistan</span><span class="sxs-lookup"><span data-stu-id="2ea1f-172">Third bullet item</span></span>

#### <a name="ordered-lists"></a><span data-ttu-id="2ea1f-173">Sorterade listor</span><span class="sxs-lookup"><span data-stu-id="2ea1f-173">Ordered lists</span></span>

<span data-ttu-id="2ea1f-174">Om du vill lägga till ett stycke eller andra element under ett numrerat objekt, justerar du indraget efter det första tecknet som följer efter objektets nummer.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-174">To include a paragraph or other elements under a numbered item, align indentation with the first character after the item number.</span></span> <span data-ttu-id="2ea1f-175">Alla objekt i en numrerad lista ska använda talet i `1.` stället för att öka varje objekt.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-175">All items in a numbered listed should use the number `1.` rather than incrementing each item.</span></span> <span data-ttu-id="2ea1f-176">Med Markdown-rendering ökar värdet automatiskt.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-176">Markdown rendering increments the value automatically.</span></span> <span data-ttu-id="2ea1f-177">Det här gör det enklare att ändra ordning på objekt och standardiserar indrag för underordnat innehåll.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-177">This makes reordering items easier and standardizes the indentation of subordinate content.</span></span>

<span data-ttu-id="2ea1f-178">Exempel:</span><span class="sxs-lookup"><span data-stu-id="2ea1f-178">For example:</span></span>

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

<span data-ttu-id="2ea1f-179">Den resulterande markdown återges på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="2ea1f-179">The resulting Markdown is rendered as follows:</span></span>

1. <span data-ttu-id="2ea1f-180">För det första elementet infogar du ett blanksteg efter siffran 1.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-180">For the first element, insert a single space after the 1.</span></span> <span data-ttu-id="2ea1f-181">Långa meningar ska omslutas till nästa rad, och måste anpassas efter det första tecknet efter markören för den numrerade listan.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-181">Long sentences should be wrapped to the next line and must line up with the first character after the numbered list marker.</span></span>

   <span data-ttu-id="2ea1f-182">Vill du lägga till ett andra element (som det här) infogar du en radbrytning efter det första och justerar indragen.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-182">To include a second element (like this one), insert a line break after the first and align indentations.</span></span> <span data-ttu-id="2ea1f-183">Indraget för det andra elementet måste anpassas efter det första tecknet efter markören för den numrerade listan.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-183">The indentation of the second element must line up with the first character after the numbered list marker.</span></span> <span data-ttu-id="2ea1f-184">För ensiffriga objekt, som det här, gör du indrag till kolumn 4.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-184">For single digit items, like this one, you indent to column 4.</span></span> <span data-ttu-id="2ea1f-185">För tvåsiffriga objekt, till exempel objekt nummer 10, gör du indrag till kolumn 5.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-185">For double digits items, for example item number 10, you indent to column 5.</span></span>

1. <span data-ttu-id="2ea1f-186">Nästa numrerade objekt börjar här.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-186">The next numbered item starts here.</span></span>

### <a name="images"></a><span data-ttu-id="2ea1f-187">Avbildningar</span><span class="sxs-lookup"><span data-stu-id="2ea1f-187">Images</span></span>

<span data-ttu-id="2ea1f-188">Syntax för att infoga en bild:</span><span class="sxs-lookup"><span data-stu-id="2ea1f-188">The syntax to include an image is:</span></span>

```markdown
![[alt text]](<folderPath>)

Example:
![Introduction](./media/overview/Introduction.png)
```

<span data-ttu-id="2ea1f-189">`alt text` är en kort beskrivning av bilden och `<folder path>` är en relativ sökväg till bilden.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-189">Where `alt text` is a brief description of the image and `<folder path>` is a relative path to the image.</span></span> <span data-ttu-id="2ea1f-190">Alternativ text krävs för skärmläsare för personer med nedsatt syn.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-190">Alternate text is required for screen readers for the visually impaired.</span></span>

<span data-ttu-id="2ea1f-191">Avbildningar ska lagras i en `media/<article-name>` mapp i den mapp som innehåller artikeln.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-191">Images should be stored in a `media/<article-name>` folder within the folder containing the article.</span></span>
<span data-ttu-id="2ea1f-192">Dela inte bilder mellan artiklar.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-192">Don't share images between articles.</span></span> <span data-ttu-id="2ea1f-193">Skapa en mapp som matchar filnamnet för din artikel under mappen `media`.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-193">Create a folder that matches the filename of your article under the `media` folder.</span></span> <span data-ttu-id="2ea1f-194">Kopiera bilderna till artikeln till den nya mappen.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-194">Copy the images for that article to that new folder.</span></span> <span data-ttu-id="2ea1f-195">Om en bild används av flera artiklar måste varje bildmapp innehålla en kopia av bildfilen.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-195">If an image is used by multiple articles, each image folder must have a copy of that image file.</span></span> <span data-ttu-id="2ea1f-196">Den här metoden förhindrar att en ändring av en bild i en artikel påverkar en annan artikel.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-196">This practice prevents a change to an image in one article affecting another article.</span></span>

<span data-ttu-id="2ea1f-197">Följande bild fil typer stöds:,, `*.png` , `*.gif` `*.jpeg` `*.jpg` , `*.svg`</span><span class="sxs-lookup"><span data-stu-id="2ea1f-197">The following image file types are supported: `*.png`, `*.gif`, `*.jpeg`, `*.jpg`, `*.svg`</span></span>

### <a name="markdown-extensions-supported-by-open-publishing"></a><span data-ttu-id="2ea1f-198">Markdown-tillägg stöds av Open Publishing</span><span class="sxs-lookup"><span data-stu-id="2ea1f-198">Markdown extensions supported by Open Publishing</span></span>

<span data-ttu-id="2ea1f-199">[Microsoft docs redigerings paketet](/contribute/how-to-write-docs-auth-pack) innehåller verktyg som stöder funktioner som är unika för vårt publicerings system.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-199">The [Microsoft Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack) contains tools that support features unique to our publishing system.</span></span> <span data-ttu-id="2ea1f-200">Aviseringar är ett markdown-tillägg för att skapa blockquotes som återger på docs.microsoft.com med färger och ikoner som markerar innehållets omfattning.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-200">Alerts are a Markdown extension to create blockquotes that render on docs.microsoft.com with colors and icons that highlight the significance of the content.</span></span> <span data-ttu-id="2ea1f-201">Följande aviseringstyper stöds:</span><span class="sxs-lookup"><span data-stu-id="2ea1f-201">The following alert types are supported:</span></span>

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

<span data-ttu-id="2ea1f-202">Dessa aviseringar ser ut så här på docs.microsoft.com:</span><span class="sxs-lookup"><span data-stu-id="2ea1f-202">These alerts look like this on docs.microsoft.com:</span></span>

<span data-ttu-id="2ea1f-203">Antecknings block</span><span class="sxs-lookup"><span data-stu-id="2ea1f-203">Note block</span></span>

> [!NOTE]
> <span data-ttu-id="2ea1f-204">Information som användaren ska kunna se även vid snabbläsning.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-204">Information the user should notice even if skimming.</span></span>

<span data-ttu-id="2ea1f-205">Tip-block</span><span class="sxs-lookup"><span data-stu-id="2ea1f-205">Tip block</span></span>

> [!TIP]
> <span data-ttu-id="2ea1f-206">Valfri information som hjälper användaren.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-206">Optional information to help a user be more successful.</span></span>

<span data-ttu-id="2ea1f-207">Viktigt block</span><span class="sxs-lookup"><span data-stu-id="2ea1f-207">Important block</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2ea1f-208">Viktig information som användaren behöver.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-208">Essential information required for user success.</span></span>

<span data-ttu-id="2ea1f-209">Varnings block</span><span class="sxs-lookup"><span data-stu-id="2ea1f-209">Caution block</span></span>

> [!CAUTION]
> <span data-ttu-id="2ea1f-210">Potentiella negativa konsekvenser av en åtgärd.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-210">Negative potential consequences of an action.</span></span>

<span data-ttu-id="2ea1f-211">Varnings block</span><span class="sxs-lookup"><span data-stu-id="2ea1f-211">Warning block</span></span>

> [!WARNING]
> <span data-ttu-id="2ea1f-212">Farliga konsekvenser av en åtgärd.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-212">Dangerous certain consequences of an action.</span></span>

### <a name="hyperlinks"></a><span data-ttu-id="2ea1f-213">Hyperlänkar</span><span class="sxs-lookup"><span data-stu-id="2ea1f-213">Hyperlinks</span></span>

- <span data-ttu-id="2ea1f-214">Hyperlänkar måste använda markdown-syntax `[friendlyname](url-or-path)` .</span><span class="sxs-lookup"><span data-stu-id="2ea1f-214">Hyperlinks must use Markdown syntax `[friendlyname](url-or-path)`.</span></span> <span data-ttu-id="2ea1f-215">[Länk referenser][linkref] stöds.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-215">[Link references][linkref] are supported.</span></span>
- <span data-ttu-id="2ea1f-216">Publicerings systemet har stöd för tre typer av länkar:</span><span class="sxs-lookup"><span data-stu-id="2ea1f-216">The publishing system supports three types of links:</span></span>
  - <span data-ttu-id="2ea1f-217">URL-länkar</span><span class="sxs-lookup"><span data-stu-id="2ea1f-217">URL links</span></span>
  - <span data-ttu-id="2ea1f-218">Fil länkar</span><span class="sxs-lookup"><span data-stu-id="2ea1f-218">File links</span></span>
  - <span data-ttu-id="2ea1f-219">Kors referens länkar</span><span class="sxs-lookup"><span data-stu-id="2ea1f-219">Cross-reference links</span></span>
- <span data-ttu-id="2ea1f-220">Länkar till andra artiklar på docs.microsoft.com måste vara plats relativa sökvägar</span><span class="sxs-lookup"><span data-stu-id="2ea1f-220">Links to other articles on docs.microsoft.com must be site-relative paths</span></span>
- <span data-ttu-id="2ea1f-221">Alla URL: er till externa webbplatser bör använda HTTPS om det inte är giltigt för mål platsen.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-221">All URLs to external websites should use HTTPS unless that isn't valid for the target site.</span></span>
- <span data-ttu-id="2ea1f-222">Länkar måste ha ett eget namn, vanligt vis rubriken för den länkade artikeln</span><span class="sxs-lookup"><span data-stu-id="2ea1f-222">Links must have a friendly name, usually the title of the linked article</span></span>
- <span data-ttu-id="2ea1f-223">Alla objekt i avsnittet _relaterade länkar_ längst ned ska vara hyperlänkade</span><span class="sxs-lookup"><span data-stu-id="2ea1f-223">All items in the _Related links_ section at the bottom should be hyperlinked</span></span>
- <span data-ttu-id="2ea1f-224">Använd inte autoskalning, fetstil eller andra markeringar inuti hakparenteserna för en hyperlänk.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-224">Don't use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>
- <span data-ttu-id="2ea1f-225">Bare-URL: er kan användas när du har dokumenterat en angiven URI.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-225">Bare URLs may be used when you're documenting a specific URI.</span></span> <span data-ttu-id="2ea1f-226">URI måste omges av baktick.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-226">The URI must be enclosed in backticks.</span></span> <span data-ttu-id="2ea1f-227">Exempel:</span><span class="sxs-lookup"><span data-stu-id="2ea1f-227">For example:</span></span>

  ```markdown
  By default, if you don't specify this parameter, the DMTF standard resource URI
  `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.
  ```

#### <a name="linking-to-other-content-on-docsmicrosoftcom"></a><span data-ttu-id="2ea1f-228">Länka till annat innehåll på docs.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="2ea1f-228">Linking to other content on docs.microsoft.com</span></span>

- <span data-ttu-id="2ea1f-229">**URL-länkar** till andra artiklar på docs.Microsoft.com måste vara plats relativa sökvägar.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-229">**URL links** to other articles on docs.microsoft.com must be site-relative paths.</span></span> <span data-ttu-id="2ea1f-230">Det enklaste sättet att skapa en relativ länk är att kopiera URL: en från webbläsaren och sedan ta bort `https://docs.microsoft.com/en-us` den från det värde som du klistrar in i markdown.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-230">The simplest way to create a relative link is to copy the URL from your browser then remove `https://docs.microsoft.com/en-us` from the value you paste into markdown.</span></span> <span data-ttu-id="2ea1f-231">Ta inte med språk i URL: er för Microsoft-egenskaper (ta bort `/en-us` från URL).</span><span class="sxs-lookup"><span data-stu-id="2ea1f-231">Don't include locales in URLs on Microsoft properties (remove `/en-us` from URL).</span></span> <span data-ttu-id="2ea1f-232">Ta bort alla onödiga frågeparametrar från URL: en.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-232">Remove any unnecessary query parameters from the URL.</span></span> <span data-ttu-id="2ea1f-233">Exempel som ska tas bort:</span><span class="sxs-lookup"><span data-stu-id="2ea1f-233">Examples that should be removed:</span></span>

  - <span data-ttu-id="2ea1f-234">`?view=powershell-5.1` – används för att länka till en angiven version av PowerShell</span><span class="sxs-lookup"><span data-stu-id="2ea1f-234">`?view=powershell-5.1` - used to link to a specific version of PowerShell</span></span>
  - <span data-ttu-id="2ea1f-235">`?redirectedfrom=MSDN` – läggs till i URL: en när du omdirigeras från en gammal artikel till en ny plats</span><span class="sxs-lookup"><span data-stu-id="2ea1f-235">`?redirectedfrom=MSDN` - added to the URL when you get redirected from an old article to its new location</span></span>

  <span data-ttu-id="2ea1f-236">Om du behöver länka till en speciell version av ett dokument måste du lägga till `&preserve_view=true` parametern i frågesträngen.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-236">If you need to link to a specific version of a document, then you need to add the `&preserve_view=true` parameter to the query string.</span></span> <span data-ttu-id="2ea1f-237">Exempel: `?view=powershell-5.1&preserve_view=true`</span><span class="sxs-lookup"><span data-stu-id="2ea1f-237">For example: `?view=powershell-5.1&preserve_view=true`</span></span>

- <span data-ttu-id="2ea1f-238">En **fil länk** används för att länka från en referens artikel till en annan, eller från en konceptuell artikel till en annan.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-238">A **file link** is used to link from one reference article to another, or from one conceptual article to another.</span></span> <span data-ttu-id="2ea1f-239">Om du behöver länka till en referens artikel för en viss version av PowerShell måste du använda en URL-länk.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-239">If you need to link to a reference article for a specific version of PowerShell, then you must use a URL link.</span></span>

  - <span data-ttu-id="2ea1f-240">Fil länkar innehåller en relativ fil Sök väg (till exempel: `../folder/file.md` )</span><span class="sxs-lookup"><span data-stu-id="2ea1f-240">File links contain a relative file path (for example: `../folder/file.md`)</span></span>
  - <span data-ttu-id="2ea1f-241">Alla fil Sök vägar använder snedstreck ( `/` )-tecken</span><span class="sxs-lookup"><span data-stu-id="2ea1f-241">All file paths use forward-slash (`/`) characters</span></span>

- <span data-ttu-id="2ea1f-242">**Länkar mellan referenser** är en särskild funktion som stöds av publicerings systemet.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-242">**Cross-reference links** are a special feature supported by the publishing system.</span></span> <span data-ttu-id="2ea1f-243">Du kan använda kors referens länkar i konceptuella artiklar för att länka till .NET API eller cmdlet-referens.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-243">You can use cross-reference links in conceptual articles to link to .NET API or cmdlet reference.</span></span>

  <span data-ttu-id="2ea1f-244">Länkar till .NET API-referens finns i [använda länkar i dokumentation](/contribute/how-to-write-links#xref-cross-reference-links) i Central Contributor-guiden.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-244">For links to .NET API reference, see [Use links in documentation](/contribute/how-to-write-links#xref-cross-reference-links) in the central Contributor Guide.</span></span>

  <span data-ttu-id="2ea1f-245">Länkar till cmdlet-referensen har följande format: `xref:<module-name>.<cmdlet-name>` .</span><span class="sxs-lookup"><span data-stu-id="2ea1f-245">Links to cmdlet reference have the following format: `xref:<module-name>.<cmdlet-name>`.</span></span> <span data-ttu-id="2ea1f-246">Till exempel för att länka till- `Get-Content` cmdlet: en i modulen **Microsoft. PowerShell. Management** .</span><span class="sxs-lookup"><span data-stu-id="2ea1f-246">For example, to link to the `Get-Content` cmdlet in the **Microsoft.PowerShell.Management** module.</span></span>

  `[Get-Content](xref:Microsoft.PowerShell.Management.Get-Content)`

<span data-ttu-id="2ea1f-247">Djup länkning tillåts för både URL-adresser och fil länkar.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-247">Deep linking is allowed on both URL and file links.</span></span> <span data-ttu-id="2ea1f-248">Lägg till fäst punkten i slutet av mål Sök vägen.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-248">Add the anchor to the end of the target path.</span></span>
<span data-ttu-id="2ea1f-249">Exempel:</span><span class="sxs-lookup"><span data-stu-id="2ea1f-249">For example:</span></span>

- `[about_Splatting](about_Splatting.md#splatting-with-arrays)`
- `[custom key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings)`

<span data-ttu-id="2ea1f-250">Mer information finns i [använda länkar i dokumentation](/contribute/how-to-write-links).</span><span class="sxs-lookup"><span data-stu-id="2ea1f-250">For more information, see [Use links in documentation](/contribute/how-to-write-links).</span></span>

## <a name="formatting-command-syntax-elements"></a><span data-ttu-id="2ea1f-251">Formatera element i kommandosyntax</span><span class="sxs-lookup"><span data-stu-id="2ea1f-251">Formatting command syntax elements</span></span>

- <span data-ttu-id="2ea1f-252">Använd alltid det fullständiga namnet för cmdletar och parametrar.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-252">Always use the full name for cmdlets and parameters.</span></span> <span data-ttu-id="2ea1f-253">Undvik att använda alias om du inte specifikt demonstrerar aliaset.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-253">Avoid using aliases unless you're specifically demonstrating the alias.</span></span>

- <span data-ttu-id="2ea1f-254">Egenskap, parameter, objekt, typ namn, klass namn, klass metoder ska vara **fetstil**.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-254">Property, parameter, object, type names, class names, class methods should be **bold**.</span></span>
  - <span data-ttu-id="2ea1f-255">Egenskaps-och parameter värden ska omslutas i baktick ( `` ` `` ).</span><span class="sxs-lookup"><span data-stu-id="2ea1f-255">Property and parameter values should be wrapped in backticks (`` ` ``).</span></span>
  - <span data-ttu-id="2ea1f-256">När du refererar till typer med hjälp av den hakparentesa stilen använder du baktick.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-256">When referring to types using the bracketed style, use backticks.</span></span> <span data-ttu-id="2ea1f-257">Exempel: `[System.Io.FileInfo]`</span><span class="sxs-lookup"><span data-stu-id="2ea1f-257">For example: `[System.Io.FileInfo]`</span></span>

- <span data-ttu-id="2ea1f-258">Språk nyckelord, cmdlet-namn, funktioner, variabler, interna EXEs, fil Sök vägar och infogade syntaxer ska omslutas av tecken i text Ticket ( `` ` `` ).</span><span class="sxs-lookup"><span data-stu-id="2ea1f-258">Language keywords, cmdlet names, functions, variables, native EXEs, file paths, and inline syntax examples should be wrapped in backtick (`` ` ``) characters.</span></span>

  <span data-ttu-id="2ea1f-259">Exempel:</span><span class="sxs-lookup"><span data-stu-id="2ea1f-259">For example:</span></span>

  ~~~markdown
  The following code uses `Get-ChildItem` to list the contents of `C:\Windows` and assigns
  the output to the `$files` variable.

  ```powershell
  $files = Get-ChildItem C:\Windows
  ```
  ~~~

  - <span data-ttu-id="2ea1f-260">När du refererar till en parameter med namnet ska det skrivas med **fetstil**.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-260">When referring to a parameter by name, the name should be **bold**.</span></span> <span data-ttu-id="2ea1f-261">När du illustrerar användningen av en parameter med avstavningsprefixet ska parametern omslutas av grava accenter.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-261">When illustrating the use of a parameter with the hyphen prefix, the parameter should be wrapped in backticks.</span></span> <span data-ttu-id="2ea1f-262">Exempel:</span><span class="sxs-lookup"><span data-stu-id="2ea1f-262">For example:</span></span>

    ```markdown
    The parameter's name is **Name**, but it's typed as `-Name` when used on the command
    line as a parameter.
    ```

  - <span data-ttu-id="2ea1f-263">När du visar exempel på användning av ett externt kommando ska exemplet omslutas av grava accenter.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-263">When showing example usage of an external command, the example should be wrapped in backticks.</span></span>
    <span data-ttu-id="2ea1f-264">Ta alltid med fil tillägget i det inbyggda kommandot.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-264">Always include the file extension in the native command.</span></span> <span data-ttu-id="2ea1f-265">Exempel:</span><span class="sxs-lookup"><span data-stu-id="2ea1f-265">For example:</span></span>

    ```markdown
    To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.
    ```

    <span data-ttu-id="2ea1f-266">Inklusive fil tillägget säkerställer att rätt kommando körs enligt PowerShell: s kommando prioritet.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-266">Including the file extension ensures that the correct command is executed according to PowerShell's command precedence.</span></span>

- <span data-ttu-id="2ea1f-267">När du skriver en konceptuell artikel (till skillnad från referensinnehåll) ska den första förekomsten av ett cmdlet-namn hyperlänkas till cmdlet-dokumentationen.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-267">When writing a conceptual article (as opposed to reference content), the first instance of a cmdlet name should be hyperlinked to the cmdlet documentation.</span></span> <span data-ttu-id="2ea1f-268">Använd inte autoskalning, fetstil eller andra markeringar inuti hakparenteserna för en hyperlänk.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-268">Don't use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>

  <span data-ttu-id="2ea1f-269">Exempel:</span><span class="sxs-lookup"><span data-stu-id="2ea1f-269">For example:</span></span>

  ```markdown
  This [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet
  uses the **Object** parameter to ...
  ```

  <span data-ttu-id="2ea1f-270">Mer information finns i avsnittet [hyperlinks](#hyperlinks) i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-270">For more information, see [Hyperlinks](#hyperlinks) section of this article.</span></span>

## <a name="markdown-for-code-samples"></a><span data-ttu-id="2ea1f-271">Markdown för kod exempel</span><span class="sxs-lookup"><span data-stu-id="2ea1f-271">Markdown for code samples</span></span>

<span data-ttu-id="2ea1f-272">Markdown stöder två olika kodformat:</span><span class="sxs-lookup"><span data-stu-id="2ea1f-272">Markdown supports two different code styles:</span></span>

- <span data-ttu-id="2ea1f-273">**Kod sträcker sig över (infogade)** – markerade med ett enda baktick ( `` ` `` )-tecken.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-273">**Code spans (inline)** - marked by a single backtick (`` ` ``) character.</span></span> <span data-ttu-id="2ea1f-274">Används inom ett stycke i stället för som ett fristående block.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-274">Used within a paragraph rather than as a standalone block.</span></span>
- <span data-ttu-id="2ea1f-275">**Kodblock** – ett block med flera rader som omges av tredubbel-bakticket ( `` ``` `` )-strängar.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-275">**Code blocks** - a multi-line block surrounded by triple-backtick (`` ``` ``) strings.</span></span> <span data-ttu-id="2ea1f-276">Kod block kan också ha en språk etikett efter bakstrecken.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-276">Code blocks may also have a language label following the backticks.</span></span> <span data-ttu-id="2ea1f-277">Språk etiketten aktiverar syntax för innehållet i kod blocket.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-277">The language label enables syntax highlighting for the contents of the code block.</span></span>

<span data-ttu-id="2ea1f-278">Alla kodblock ska finnas i en kodavgränsning.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-278">All code blocks should be contained in a code fence.</span></span> <span data-ttu-id="2ea1f-279">Använd aldrig indrag för kodblock.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-279">Never use indentation for code blocks.</span></span> <span data-ttu-id="2ea1f-280">Markdown tillåter det här mönstret, men det kan vara problematiskt och bör undvikas.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-280">Markdown allows this pattern but it can be problematic and should be avoided.</span></span>

<span data-ttu-id="2ea1f-281">Ett kodblock är en eller flera kodrader som omges av en kod gräns för tredubbelt skal streck ( `` ``` `` ).</span><span class="sxs-lookup"><span data-stu-id="2ea1f-281">A code block is one or more lines of code surrounded by a triple-backtick (`` ``` ``) code fence.</span></span>
<span data-ttu-id="2ea1f-282">Kodavgränsningsmarkörerna måste finnas på en egen rad före och efter kodexemplet.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-282">The code fence markers must be on their own line before and after the code sample.</span></span> <span data-ttu-id="2ea1f-283">Markören i början av kodblocket kan ha en valfri språketikett.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-283">The marker at the start of the code block may have an optional language label.</span></span> <span data-ttu-id="2ea1f-284">Microsofts Open Publishing System (OPS) använder språketiketten för att stödja markeringsfunktionen för syntax.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-284">Microsoft's Open Publishing System (OPS) uses the language label to support the syntax highlighting feature.</span></span>

<span data-ttu-id="2ea1f-285">En fullständig lista över språk koder som stöds finns i [avgränsade kodblock](/contribute/code-in-docs#fenced-code-blocks) i den centraliserade deltagar guiden.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-285">For a full list of supported language tags, see [Fenced code blocks](/contribute/code-in-docs#fenced-code-blocks) in the centralized contributor guide.</span></span>

<span data-ttu-id="2ea1f-286">OPS lägger också till knappen **Kopiera**, som kopierar innehållet i kodblocket till Urklipp.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-286">OPS also adds a **Copy** button that copies the contents of the code block to the clipboard.</span></span> <span data-ttu-id="2ea1f-287">På så sätt kan du snabbt klistra in koden i ett skript för att testa kod exemplet.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-287">This allows you to quickly paste the code into a script to test the code sample.</span></span> <span data-ttu-id="2ea1f-288">Men inte alla exempel i vår dokumentation är avsedda att köras i befintligt skick.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-288">However, not all examples in our documentation are intended to be run as-is.</span></span> <span data-ttu-id="2ea1f-289">Vissa kod block är enkla illustrationer av ett PowerShell-begrepp.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-289">Some code blocks are simple illustrations of a PowerShell concept.</span></span>

<span data-ttu-id="2ea1f-290">Det finns tre typer av kod block som används i vår dokumentation:</span><span class="sxs-lookup"><span data-stu-id="2ea1f-290">There are three types code blocks used in our documentation:</span></span>

1. <span data-ttu-id="2ea1f-291">Kommandosyntax</span><span class="sxs-lookup"><span data-stu-id="2ea1f-291">Syntax blocks</span></span>
1. <span data-ttu-id="2ea1f-292">Illustrerande exempel</span><span class="sxs-lookup"><span data-stu-id="2ea1f-292">Illustrative examples</span></span>
1. <span data-ttu-id="2ea1f-293">Körbara exempel</span><span class="sxs-lookup"><span data-stu-id="2ea1f-293">Executable examples</span></span>

### <a name="syntax-code-blocks"></a><span data-ttu-id="2ea1f-294">Kod block för syntax</span><span class="sxs-lookup"><span data-stu-id="2ea1f-294">Syntax code blocks</span></span>

<span data-ttu-id="2ea1f-295">Syntax Code block används för att beskriva en kommandos syntaktiska struktur.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-295">Syntax code blocks are used to describe the syntactic structure of a command.</span></span> <span data-ttu-id="2ea1f-296">Använd inte en språk tagg på kod avgränsningen.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-296">Don't use a language tag on the code fence.</span></span> <span data-ttu-id="2ea1f-297">Det här exemplet illustrerar alla möjliga parametrar för cmdleten `Get-Command`.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-297">This example illustrates all the possible parameters of the `Get-Command` cmdlet.</span></span>

~~~markdown
```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
  [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax]
  [-ShowCommandInfo] [[-ArgumentList] <Object[]>] [-All] [-ListImported]
  [-ParameterName <String[]>] [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```
~~~

<span data-ttu-id="2ea1f-298">I det här exemplet beskrivs satsen `for` i generaliserade villkor:</span><span class="sxs-lookup"><span data-stu-id="2ea1f-298">This example describes the `for` statement in generalized terms:</span></span>

~~~markdown
```
for (<init>; <condition>; <repeat>)
{<statement list>}
```
~~~

### <a name="illustrative-examples"></a><span data-ttu-id="2ea1f-299">Illustrerande exempel</span><span class="sxs-lookup"><span data-stu-id="2ea1f-299">Illustrative examples</span></span>

<span data-ttu-id="2ea1f-300">Illustrerande exempel används för att förklara ett PowerShell-begrepp.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-300">Illustrative examples are used to explain a PowerShell concept.</span></span> <span data-ttu-id="2ea1f-301">De är inte avsedda att kopieras till Urklipp för körning.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-301">They aren't meant to be copied to the clipboard for execution.</span></span> <span data-ttu-id="2ea1f-302">Dessa används vanligt vis för enkla exempel som är lätta att skriva och som är lätta att förstå.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-302">These are most commonly used for simple examples that are easy to type and easy to understand.</span></span> <span data-ttu-id="2ea1f-303">Kod blocket kan innehålla PowerShell-prompten och exempel på utdata.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-303">The code block can include the PowerShell prompt and example output.</span></span>

<span data-ttu-id="2ea1f-304">Här är ett enkelt exempel som illustrerar PowerShell-jämförelse operatorer.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-304">Here's a simple example illustrating the PowerShell comparison operators.</span></span> <span data-ttu-id="2ea1f-305">I det här fallet förväntar vi oss inte att läsaren ska kopiera och köra exemplet.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-305">In this case, we don't intend the reader to copy and run this example.</span></span>

~~~markdown
```powershell
PS> 2 -eq 2
True

PS> 2 -eq 3
False

PS> 1,2,3 -eq 2
2

PS> "abc" -eq "abc"
True

PS> "abc" -eq "abc", "def"
False

PS> "abc", "def" -eq "abc"
abc
```
~~~

### <a name="executable-examples"></a><span data-ttu-id="2ea1f-306">Körbara exempel</span><span class="sxs-lookup"><span data-stu-id="2ea1f-306">Executable examples</span></span>

<span data-ttu-id="2ea1f-307">Avancerade exempel eller exempel som är avsedda att kopieras och köras ska använda följande block-Style-markering:</span><span class="sxs-lookup"><span data-stu-id="2ea1f-307">Complex examples, or examples that are intended to be copied and executed, should use the following block-style markup:</span></span>

~~~markdown
```powershell
<Your PowerShell code goes here>
```
~~~

<span data-ttu-id="2ea1f-308">De utdata som visas av PowerShell-kommandon måste anges i ett kodblock för **utdata** för att förhindra markering av syntax.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-308">The output displayed by PowerShell commands should be enclosed in an **Output** code block to prevent syntax highlighting.</span></span> <span data-ttu-id="2ea1f-309">Exempel:</span><span class="sxs-lookup"><span data-stu-id="2ea1f-309">For example:</span></span>

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

<span data-ttu-id="2ea1f-310">Den **resulterande** kod etiketten är inte ett officiellt språk som stöds av syntaxens markerings system.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-310">The **Output** code label isn't an official "language" supported by the syntax highlighting system.</span></span>
<span data-ttu-id="2ea1f-311">Den här etiketten är dock användbar eftersom OPS lägger till etiketten "utdata" i rutan med kod rutan på webb sidan.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-311">However, this label is useful because OPS adds the "Output" label to the code box frame on the web page.</span></span> <span data-ttu-id="2ea1f-312">Kod rutan "utdata" har ingen markering av syntax.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-312">The "Output" code box has no syntax highlighting.</span></span>

## <a name="coding-style-rules"></a><span data-ttu-id="2ea1f-313">Regler för kodningsformat</span><span class="sxs-lookup"><span data-stu-id="2ea1f-313">Coding style rules</span></span>

### <a name="avoid-line-continuation-in-code-samples"></a><span data-ttu-id="2ea1f-314">Undvik radfortsättning i kodexempel</span><span class="sxs-lookup"><span data-stu-id="2ea1f-314">Avoid line continuation in code samples</span></span>

<span data-ttu-id="2ea1f-315">Undvik att använda radfortsättningstecken (`` ` ``) i PowerShell-kodexempel.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-315">Avoid using line continuation characters (`` ` ``) in PowerShell code examples.</span></span> <span data-ttu-id="2ea1f-316">De är svåra att se och kan orsaka problem om det finns extra blanksteg i slutet av raden.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-316">These are hard to see and can cause problems if there are extra spaces at the end of the line.</span></span>

- <span data-ttu-id="2ea1f-317">Använd PowerShell-ihopbuntning för att minska rad längden för cmdletar som har flera parametrar.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-317">Use PowerShell splatting to reduce line length for cmdlets that have several parameters.</span></span>
- <span data-ttu-id="2ea1f-318">Dra nytta av PowerShell: s naturliga rad brytnings möjligheter, till exempel efter pipe ( `|` )-tecken, öppna klammerparenteser ( `{` ), parenteser ( `(` ) och hakparenteser ( `[` ).</span><span class="sxs-lookup"><span data-stu-id="2ea1f-318">Take advantage of PowerShell's natural line break opportunities, like after pipe (`|`) characters, opening braces (`{`), parentheses (`(`), and brackets (`[`).</span></span>

### <a name="avoid-using-powershell-prompts-in-examples"></a><span data-ttu-id="2ea1f-319">Undvik att använda PowerShell-prompter i exempel</span><span class="sxs-lookup"><span data-stu-id="2ea1f-319">Avoid using PowerShell prompts in examples</span></span>

<span data-ttu-id="2ea1f-320">Användning av LED text strängen rekommenderas inte och bör begränsas till scenarier som är avsedda att illustrera användningen av kommando raden.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-320">Use of the prompt string is discouraged and should be limited to scenarios that are meant to illustrate command-line usage.</span></span> <span data-ttu-id="2ea1f-321">I de flesta av dessa exempel bör LED text strängen vara `PS>` .</span><span class="sxs-lookup"><span data-stu-id="2ea1f-321">For most of these examples, the prompt string should be `PS>`.</span></span> <span data-ttu-id="2ea1f-322">Den här frågan är oberoende av OS-/regionsspecifika indikatorer.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-322">This prompt is independent of OS-specific indicators.</span></span>

<span data-ttu-id="2ea1f-323">Det krävs i exempel för att illustrera kommandon som ändrar prompten eller när den angivna sökvägen är viktig för scenariot.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-323">Prompts are required in examples to illustrate commands that alter the prompt or when the path displayed is significant to the scenario.</span></span> <span data-ttu-id="2ea1f-324">I följande exempel visas hur frågan ändras när du använder registerprovidern.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-324">The following example illustrates how the prompt changes when using the Registry provider.</span></span>

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

### <a name="dont-use-aliases-in-examples"></a><span data-ttu-id="2ea1f-325">Använd inte alias i exempel</span><span class="sxs-lookup"><span data-stu-id="2ea1f-325">Don't use aliases in examples</span></span>

<span data-ttu-id="2ea1f-326">Använd det fullständiga namnet på alla cmdletar och parametrar om du inte uttryckligen har dokumenterat aliaset.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-326">Use the full name of all cmdlets and parameters unless you're specifically documenting the alias.</span></span>
<span data-ttu-id="2ea1f-327">Cmdlet-och parameter namn måste ha rätt [Pascal-bokstäver][] namn.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-327">Cmdlet and parameter names must use the proper [Pascal-cased][] names.</span></span>

### <a name="using-parameters-in-examples"></a><span data-ttu-id="2ea1f-328">Använda parametrar i exempel</span><span class="sxs-lookup"><span data-stu-id="2ea1f-328">Using parameters in examples</span></span>

<span data-ttu-id="2ea1f-329">Undvik att använda positionsparametrar.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-329">Avoid using positional parameters.</span></span> <span data-ttu-id="2ea1f-330">I allmänhet bör du alltid inkludera parameter namnet i ett exempel, även om parametern är i position.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-330">In general, you should always include the parameter name in an example, even if the parameter is positional.</span></span> <span data-ttu-id="2ea1f-331">På så sätt minskar du risken för förvirring i exemplen.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-331">This reduces the chance of confusion in your examples.</span></span>

## <a name="formatting-cmdlet-reference-articles"></a><span data-ttu-id="2ea1f-332">Formatera cmdlet Reference-artiklar</span><span class="sxs-lookup"><span data-stu-id="2ea1f-332">Formatting cmdlet reference articles</span></span>

<span data-ttu-id="2ea1f-333">Artiklar med cmdlet-referenser har en speciell struktur.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-333">Cmdlet reference articles have a specific structure.</span></span> <span data-ttu-id="2ea1f-334">Strukturen definieras av [PlatyPS][].</span><span class="sxs-lookup"><span data-stu-id="2ea1f-334">This structure is defined by [PlatyPS][].</span></span>
<span data-ttu-id="2ea1f-335">PlatyPS genererar cmdlet-hjälpen för PowerShell-moduler i markdown.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-335">PlatyPS generates the cmdlet help for PowerShell modules in Markdown.</span></span> <span data-ttu-id="2ea1f-336">När du har redigerat Markdown-filerna används PlatyPS för att skapa MAML-hjälpfiler som används av cmdleten `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-336">After editing the Markdown files, PlatyPS is used create the MAML help files used by the `Get-Help` cmdlet.</span></span>

<span data-ttu-id="2ea1f-337">PlatyPS har ett hårdkodat schema för cmdlet-referenser som skrivs in i koden.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-337">PlatyPS has a hard-coded schema for cmdlet reference that is written into the code.</span></span> <span data-ttu-id="2ea1f-338">Dokumentet [platyPS.schema.md][] är ett försök att beskriva strukturen.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-338">The [platyPS.schema.md][] document attempts to describe this structure.</span></span> <span data-ttu-id="2ea1f-339">Schemaöverträdelser orsakar build-fel som måste åtgärdas innan vi kan acceptera ditt bidrag.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-339">Schema violations cause build errors that must be fixed before we can accept your contribution.</span></span>

- <span data-ttu-id="2ea1f-340">Ta inte bort någon av ATX-huvud strukturerna.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-340">Don't remove any of the ATX header structures.</span></span> <span data-ttu-id="2ea1f-341">PlatyPS förväntar sig en specifik uppsättning rubriker.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-341">PlatyPS expects a specific set of headers.</span></span>
- <span data-ttu-id="2ea1f-342">Rubrikerna **Indatatyp** och **Utdatatyp** måste ha en typ.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-342">The **Input type** and **Output type** headers must have a type.</span></span> <span data-ttu-id="2ea1f-343">Om cmdleten inte tar emot eller returnerar ett värde använder du värdet `None` .</span><span class="sxs-lookup"><span data-stu-id="2ea1f-343">If the cmdlet doesn't take input or return a value, then use the value `None`.</span></span>
- <span data-ttu-id="2ea1f-344">Infogade kodomfång kan användas i alla stycken.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-344">Inline code spans can be used in any paragraph.</span></span>
- <span data-ttu-id="2ea1f-345">Block med inhägnade kod är endast tillåtna i avsnittet **exempel** .</span><span class="sxs-lookup"><span data-stu-id="2ea1f-345">Fenced code blocks are only allowed in the **EXAMPLES** section.</span></span>

<span data-ttu-id="2ea1f-346">I PlatyPS-schemat är **exempel** en H2-rubrik.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-346">In the PlatyPS schema, **EXAMPLES** is an H2 header.</span></span> <span data-ttu-id="2ea1f-347">Varje exempel är ett H3-huvud.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-347">Each example is an H3 header.</span></span> <span data-ttu-id="2ea1f-348">I ett exempel tillåter schemat inte att kodblock separeras av stycken.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-348">Within an example, the schema doesn't allow code blocks to be separated by paragraphs.</span></span> <span data-ttu-id="2ea1f-349">Schemat tillåter följande struktur:</span><span class="sxs-lookup"><span data-stu-id="2ea1f-349">The schema allows the following structure:</span></span>

```
### Example X - Title sentence

0 or more paragraphs
1 or more code blocks
0 or more paragraphs.
```

<span data-ttu-id="2ea1f-350">Numrera varje exempel och lägg till en kort rubrik.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-350">Number each example and add a brief title.</span></span>

<span data-ttu-id="2ea1f-351">Exempel:</span><span class="sxs-lookup"><span data-stu-id="2ea1f-351">For example:</span></span>

~~~markdown
### Example 1: Get cmdlets, functions, and aliases

This command gets the PowerShell cmdlets, functions, and aliases that are installed on the
computer.

```powershell
Get-Command
```

### Example 2: Get commands in the current session

```powershell
Get-Command -ListImported
```
~~~

## <a name="formatting-about_-files"></a><span data-ttu-id="2ea1f-352">Formatera About_-filer</span><span class="sxs-lookup"><span data-stu-id="2ea1f-352">Formatting About_ files</span></span>

<span data-ttu-id="2ea1f-353">`About_*` filerna skrivs i markdown men levereras som oformaterade textfiler.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-353">`About_*` files are written in Markdown but are shipped as plain text files.</span></span> <span data-ttu-id="2ea1f-354">Vi använder [pandoc][] för att konvertera markdown till oformaterad text.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-354">We use [Pandoc][] to convert the Markdown to plain text.</span></span> <span data-ttu-id="2ea1f-355">`About_*` filerna är formaterade för bästa kompatibilitet i alla versioner av PowerShell och med publicerings verktygen.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-355">`About_*` files are formatted for the best compatibility across all versions of PowerShell and with the publishing tools.</span></span>

<span data-ttu-id="2ea1f-356">Riktlinjer för grundläggande formatering:</span><span class="sxs-lookup"><span data-stu-id="2ea1f-356">Basic formatting guidelines:</span></span>

- <span data-ttu-id="2ea1f-357">Begränsa normala rader till 80 tecken</span><span class="sxs-lookup"><span data-stu-id="2ea1f-357">Limit normal lines to 80 characters</span></span>
- <span data-ttu-id="2ea1f-358">Kodblock är begränsade till 76 tecken</span><span class="sxs-lookup"><span data-stu-id="2ea1f-358">Code blocks are limited to 76 characters</span></span>
- <span data-ttu-id="2ea1f-359">Blockquotes (och aviseringar) är begränsade 78 tecken</span><span class="sxs-lookup"><span data-stu-id="2ea1f-359">Blockquotes (and Alerts) are limited 78 characters</span></span>
- <span data-ttu-id="2ea1f-360">När du använder dessa särskilda meta-tecken `\` , `$` , och `<` :</span><span class="sxs-lookup"><span data-stu-id="2ea1f-360">When using these special meta-characters `\`,`$`, and `<`:</span></span>
  - <span data-ttu-id="2ea1f-361">I en rubrik måste dessa tecken föregås av ett inledande `\` tecken eller omges av kod intervall med hjälp av baktick ( `` ` `` )</span><span class="sxs-lookup"><span data-stu-id="2ea1f-361">Within a header, these characters must be escaped using a leading `\` character or enclosed in code spans using backticks (`` ` ``)</span></span>
  - <span data-ttu-id="2ea1f-362">I ett stycke ska de här tecknen placeras i kod intervall.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-362">Within a paragraph, these characters should be put into code spans.</span></span> <span data-ttu-id="2ea1f-363">Exempel:</span><span class="sxs-lookup"><span data-stu-id="2ea1f-363">For example:</span></span>

    ~~~markdown
    ### The purpose of the \$foo variable

    The `$foo` variable is used to store ...
    ~~~

- <span data-ttu-id="2ea1f-364">Tabeller måste rymmas inom 76 tecken</span><span class="sxs-lookup"><span data-stu-id="2ea1f-364">Tables need to fit within 76 characters</span></span>
  - <span data-ttu-id="2ea1f-365">Radbryt innehållet i celler manuellt över flera rader</span><span class="sxs-lookup"><span data-stu-id="2ea1f-365">Manually wrap contents of cells across multiple lines</span></span>
  - <span data-ttu-id="2ea1f-366">Använd inledande och avslutande `|`-tecken på varje rad</span><span class="sxs-lookup"><span data-stu-id="2ea1f-366">Use opening and closing `|` characters on each line</span></span>
  - <span data-ttu-id="2ea1f-367">I följande exempel visas hur du skapar en tabell som innehåller information som radbryts på flera rader i en cell.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-367">The following example illustrates how to properly construct a table that contains information that wraps on multiple lines within a cell.</span></span>

    ~~~markdown
    ```
    |Operator|Description                |Example                          |
    |--------|---------------------------|---------------------------------|
    |`-is`   |Returns TRUE when the input|`(get-date) -is [DateTime]`      |
    |        |is an instance of the      |`True`                           |
    |        |specified .NET type.       |                                 |
    |`-isNot`|Returns TRUE when the input|`(get-date) -isNot [DateTime]`   |
    |        |not an instance of the     |`False`                          |
    |        |specified.NET type.        |                                 |
    |`-as`   |Converts the input to the  |`"5/7/07" -as [DateTime]`        |
    |        |specified .NET type.       |`Monday, May 7, 2007 12:00:00 AM`|
    ```
    ~~~

    > [!NOTE]
    > <span data-ttu-id="2ea1f-368">Begränsningen 76-kolumn gäller endast för `About_*` ämnen.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-368">The 76-column limitation applies only to `About_*` topics.</span></span> <span data-ttu-id="2ea1f-369">Du kan använda breda kolumner i konceptuella eller cmdlet Reference-artiklar.</span><span class="sxs-lookup"><span data-stu-id="2ea1f-369">You can use wide columns in conceptual or cmdlet reference articles.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2ea1f-370">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="2ea1f-370">Next steps</span></span>

[<span data-ttu-id="2ea1f-371">Checklista för redigering</span><span class="sxs-lookup"><span data-stu-id="2ea1f-371">Editorial checklist</span></span>](editorial-checklist.md)

<!-- link references -->
[atx]: https://github.github.com/gfm/#atx-headings
[CommonMark]: https://spec.commonmark.org/
[markdig]: https://github.com/lunet-io/markdig
[Pandoc]: https://pandoc.org
[Pascal-bokstäver]: https://en.wikipedia.org/wiki/PascalCase
[Pascal-cased]: https://en.wikipedia.org/wiki/PascalCase
[platyPS.schema.md]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[PlatyPS]: https://github.com/powershell/platyps
[reflow]: https://marketplace.visualstudio.com/items?itemName=marvhen.reflow-markdown
[linkref]: https://spec.commonmark.org/0.29/#link-reference-definitions
