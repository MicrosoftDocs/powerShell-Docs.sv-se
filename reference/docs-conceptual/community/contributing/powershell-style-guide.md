---
title: Stilguide för PowerShell-Docs
description: Den här artikeln innehåller regler för format för att skriva PowerShell-dokumentation.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: b4bc547c3560538ba246a6ed582fd4f9ce796dd2
ms.sourcegitcommit: bda70d2163eef5a158441cb1c38ac422d704535d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/10/2020
ms.locfileid: "81005592"
---
# <a name="powershell-docs-style-guide"></a><span data-ttu-id="0198c-103">Stilguide för PowerShell-Docs</span><span class="sxs-lookup"><span data-stu-id="0198c-103">PowerShell-Docs style guide</span></span>

<span data-ttu-id="0198c-104">Den här artikeln innehåller rikt linjer som är speciella för innehållet i PowerShell-dok.</span><span class="sxs-lookup"><span data-stu-id="0198c-104">This article provides style guidance specific to the PowerShell-Docs content.</span></span> <span data-ttu-id="0198c-105">Detta bygger på den information som beskrivs i [översikten](overview.md#get-started-writing-docs).</span><span class="sxs-lookup"><span data-stu-id="0198c-105">This builds on the information outlined in the [Overview](overview.md#get-started-writing-docs).</span></span>

## <a name="product-terminology"></a><span data-ttu-id="0198c-106">Produkt terminologi</span><span class="sxs-lookup"><span data-stu-id="0198c-106">Product Terminology</span></span>

<span data-ttu-id="0198c-107">Det finns flera varianter av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0198c-107">There are several variants of PowerShell.</span></span>
<span data-ttu-id="0198c-108">I den här tabellen definieras några av de olika termer som används för att diskutera PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0198c-108">This table defines some of the different terms used to discuss PowerShell.</span></span>

- <span data-ttu-id="0198c-109">**PowerShell** – det här är standardinställningen.</span><span class="sxs-lookup"><span data-stu-id="0198c-109">**PowerShell** - This is the default.</span></span> <span data-ttu-id="0198c-110">Vi rekommenderar att du använder PowerShell 7 och senare för att bli den som är den sanna PowerShell som går framåt.</span><span class="sxs-lookup"><span data-stu-id="0198c-110">We consider PowerShell 7 and beyond to be the one, true PowerShell going forward.</span></span>

- <span data-ttu-id="0198c-111">**PowerShell Core** – PowerShell som bygger på .net Core.</span><span class="sxs-lookup"><span data-stu-id="0198c-111">**PowerShell Core** - PowerShell built on .NET Core.</span></span> <span data-ttu-id="0198c-112">Användning av termen **Core** bör begränsas till fall där det är nödvändigt att skilja den från Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0198c-112">Usage of the term **Core** should be limited to cases where it is necessary to differentiate it from Windows PowerShell.</span></span>

- <span data-ttu-id="0198c-113">**Windows PowerShell** – PowerShell som bygger på .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0198c-113">**Windows PowerShell** - PowerShell built on .NET Framework.</span></span> <span data-ttu-id="0198c-114">Windows PowerShell-fartyg endast på Windows och kräver hela ramverket.</span><span class="sxs-lookup"><span data-stu-id="0198c-114">Windows PowerShell ships only on Windows and requires the complete Framework.</span></span>

<span data-ttu-id="0198c-115">I allmänhet kan referenser till "Windows PowerShell" i dokumentationen ändras till "PowerShell".</span><span class="sxs-lookup"><span data-stu-id="0198c-115">In general, references to "Windows PowerShell" in documentation can be changed to "PowerShell".</span></span>
<span data-ttu-id="0198c-116">"Windows PowerShell" bör **inte** ändras när en Windows-speciell teknik diskuteras.</span><span class="sxs-lookup"><span data-stu-id="0198c-116">"Windows PowerShell" should **not** be changed when Windows-specific technology is being discussed.</span></span>

## <a name="markdown-specifics"></a><span data-ttu-id="0198c-117">Markdown-information</span><span class="sxs-lookup"><span data-stu-id="0198c-117">Markdown specifics</span></span>

<span data-ttu-id="0198c-118">Microsoft Open Publishing system (OPS) som bygger vår dokumentation använder [markdig][] för att bearbeta markdown-dokumenten.</span><span class="sxs-lookup"><span data-stu-id="0198c-118">The Microsoft Open Publishing System (OPS) that builds our documentation uses [markdig][] to process the Markdown documents.</span></span> <span data-ttu-id="0198c-119">Markdig analyserar dokumenten baserat på reglerna för den senaste [CommonMark][] -specifikationen.</span><span class="sxs-lookup"><span data-stu-id="0198c-119">Markdig parses the documents based on the rules of the latest [CommonMark][] specification.</span></span>

<span data-ttu-id="0198c-120">Den nya CommonMark-specifikationen är mycket strängare om konstruktion av vissa markdown-element.</span><span class="sxs-lookup"><span data-stu-id="0198c-120">The new CommonMark spec is much stricter about the construction of some Markdown elements.</span></span> <span data-ttu-id="0198c-121">Var uppmärksam på de uppgifter som anges i det här dokumentet.</span><span class="sxs-lookup"><span data-stu-id="0198c-121">Pay close attention to the details provided in this document.</span></span>

### <a name="blank-lines-spaces-and-tabs"></a><span data-ttu-id="0198c-122">Tomma rader, blank steg och tabbar</span><span class="sxs-lookup"><span data-stu-id="0198c-122">Blank lines, spaces, and tabs</span></span>

<span data-ttu-id="0198c-123">Ta bort dubbletter av tomma rader.</span><span class="sxs-lookup"><span data-stu-id="0198c-123">Remove duplicate blank lines.</span></span> <span data-ttu-id="0198c-124">Flera tomma rader återges som en enda tom rad i HTML så att det inte är något ändamål för flera tomma rader.</span><span class="sxs-lookup"><span data-stu-id="0198c-124">Multiple blank lines render as a single blank line in HTML so there is not purpose for multiple blank lines.</span></span>

<span data-ttu-id="0198c-125">Tomma rader signalerar också slutet av ett block i markdown.</span><span class="sxs-lookup"><span data-stu-id="0198c-125">Blank lines also signal the end of a block in Markdown.</span></span> <span data-ttu-id="0198c-126">Det måste finnas ett enda tomt värde mellan markdown-block av olika typer (till exempel mellan ett stycke och en lista eller rubrik).</span><span class="sxs-lookup"><span data-stu-id="0198c-126">There should be a single blank between Markdown blocks of different types (for example, between a paragraph and a list or header).</span></span>

> [!NOTE]
> <span data-ttu-id="0198c-127">Avståndet är signifikant i markdown.</span><span class="sxs-lookup"><span data-stu-id="0198c-127">Spacing is significant in Markdown.</span></span> <span data-ttu-id="0198c-128">Använder alltid blank steg i stället för hårda tabbar.</span><span class="sxs-lookup"><span data-stu-id="0198c-128">Always uses spaces instead of hard tabs.</span></span> <span data-ttu-id="0198c-129">Ta bort extra blank steg i slutet av rader.</span><span class="sxs-lookup"><span data-stu-id="0198c-129">Remove extra spaces at the end of lines.</span></span>

### <a name="titles-and-headings"></a><span data-ttu-id="0198c-130">Titlar och rubriker</span><span class="sxs-lookup"><span data-stu-id="0198c-130">Titles and headings</span></span>

<span data-ttu-id="0198c-131">Använd endast [ATX-rubriker][atx] (# Style, i stället för `=` eller `-` format rubriker).</span><span class="sxs-lookup"><span data-stu-id="0198c-131">Only use [ATX headings][atx] (# style, as opposed to `=` or `-` style headers).</span></span>

- <span data-ttu-id="0198c-132">Använd endast inledande versal i meningar och den första bokstaven i en rubrik eller rubrik ska kapitaliseras</span><span class="sxs-lookup"><span data-stu-id="0198c-132">Use sentence case - only proper nouns and the first letter of a title or header should be capitalized</span></span>
- <span data-ttu-id="0198c-133">Det måste finnas ett enda blank steg mellan `#` och den första bokstaven i rubriken</span><span class="sxs-lookup"><span data-stu-id="0198c-133">There must be a single space between the `#` and the first letter of the heading</span></span>
- <span data-ttu-id="0198c-134">Rubriker ska omges av en enda tom linje</span><span class="sxs-lookup"><span data-stu-id="0198c-134">Headings should be surrounded by a single blank line</span></span>
- <span data-ttu-id="0198c-135">Endast ett H1 per dokument</span><span class="sxs-lookup"><span data-stu-id="0198c-135">Only one H1 per document</span></span>
- <span data-ttu-id="0198c-136">Rubrik nivåerna bör ökas med ett.</span><span class="sxs-lookup"><span data-stu-id="0198c-136">Header levels should increment by one.</span></span> <span data-ttu-id="0198c-137">Hoppa över nivåer</span><span class="sxs-lookup"><span data-stu-id="0198c-137">Do not skip levels</span></span>
- <span data-ttu-id="0198c-138">Använd inte fetstil eller andra markeringar i sidhuvuden</span><span class="sxs-lookup"><span data-stu-id="0198c-138">Do not use bold or other markup in headers</span></span>

### <a name="limit-line-length-to-100-characters"></a><span data-ttu-id="0198c-139">Begränsa rad längden till 100 tecken</span><span class="sxs-lookup"><span data-stu-id="0198c-139">Limit line length to 100 characters</span></span>

<span data-ttu-id="0198c-140">Detta gäller för konceptuella artiklar och cmdlet-referens.</span><span class="sxs-lookup"><span data-stu-id="0198c-140">This applies to conceptual articles and cmdlet reference.</span></span> <span data-ttu-id="0198c-141">About_topics är begränsade till 80 tecken.</span><span class="sxs-lookup"><span data-stu-id="0198c-141">About_topics are limited to 80 characters.</span></span>
<span data-ttu-id="0198c-142">Att begränsa rad längden ger bättre läsbarhet i git-differenser och historik.</span><span class="sxs-lookup"><span data-stu-id="0198c-142">Limiting the line length improves the readability of git diffs and history.</span></span> <span data-ttu-id="0198c-143">Det gör det också enklare för andra skrivare att göra bidrag.</span><span class="sxs-lookup"><span data-stu-id="0198c-143">It also makes it easier for other writers to make contributions.</span></span>

<span data-ttu-id="0198c-144">Använd tillägget [Flow markdown][reflow] i Visual Studio Code för att enkelt ommontera stycken för att passa den angivna rad längden.</span><span class="sxs-lookup"><span data-stu-id="0198c-144">Use the [Reflow Markdown][reflow] extension in Visual Studio Code to easily reflow paragraphs to fit the prescribed line length.</span></span>

### <a name="lists"></a><span data-ttu-id="0198c-145">Visar en lista över</span><span class="sxs-lookup"><span data-stu-id="0198c-145">Lists</span></span>

<span data-ttu-id="0198c-146">Om din lista innehåller flera meningar eller stycken bör du överväga att använda en rubrik på underordnade nivåer i stället för en lista.</span><span class="sxs-lookup"><span data-stu-id="0198c-146">If your list contains multiple sentences or paragraphs, consider using a sub-level header rather than a list.</span></span>

<span data-ttu-id="0198c-147">Listan ska omges av en enda tom rad.</span><span class="sxs-lookup"><span data-stu-id="0198c-147">List should be surrounded by a single blank line.</span></span>

#### <a name="unordered-lists"></a><span data-ttu-id="0198c-148">Osorterade listor</span><span class="sxs-lookup"><span data-stu-id="0198c-148">Unordered lists</span></span>

<span data-ttu-id="0198c-149">Avsluta inte List objekt med en punkt om de inte innehåller flera meningar.</span><span class="sxs-lookup"><span data-stu-id="0198c-149">Do not end list items with a period unless they contain multiple sentences.</span></span> <span data-ttu-id="0198c-150">Använd bindestrecks tecken (`-`) för List objekts punkter.</span><span class="sxs-lookup"><span data-stu-id="0198c-150">Use the hyphen character (`-`) for list item bullets.</span></span> <span data-ttu-id="0198c-151">Detta förhindrar förvirring med fet eller kursiv markering som använder asterisken [`*`].</span><span class="sxs-lookup"><span data-stu-id="0198c-151">This avoids confusion with bold or italic markup that uses the asterisk [`*`].</span></span> <span data-ttu-id="0198c-152">Om du vill inkludera ett stycke eller andra element under ett punkt objekt infogar du en rad brytning och justerar indraget med det första tecknet efter punkten.</span><span class="sxs-lookup"><span data-stu-id="0198c-152">To include a paragraph or other elements under a bullet item, insert a line break and align indentation with the first character after the bullet.</span></span>

<span data-ttu-id="0198c-153">Exempel:</span><span class="sxs-lookup"><span data-stu-id="0198c-153">For example:</span></span>

```markdown
This is a list that contain sub-elements under a bullet item.

- First bullet item

  Sentence explaining the first bullet.

  - Sub-bullet item

    Sentence explaining the sub-bullet.

- Second bullet item
- Third bullet item
```

<span data-ttu-id="0198c-154">Det här är en lista som innehåller underordnade element under ett punkt objekt.</span><span class="sxs-lookup"><span data-stu-id="0198c-154">This is a list that contains sub-elements under a bullet item.</span></span>

- <span data-ttu-id="0198c-155">Första punkt objekt</span><span class="sxs-lookup"><span data-stu-id="0198c-155">First bullet item</span></span>

  <span data-ttu-id="0198c-156">Mening som förklarar den första punkten.</span><span class="sxs-lookup"><span data-stu-id="0198c-156">Sentence explaining the first bullet.</span></span>

  - <span data-ttu-id="0198c-157">Objekt under punkt</span><span class="sxs-lookup"><span data-stu-id="0198c-157">Sub-bullet item</span></span>

    <span data-ttu-id="0198c-158">Mening som förklarar under punkten.</span><span class="sxs-lookup"><span data-stu-id="0198c-158">Sentence explaining the sub-bullet.</span></span>

- <span data-ttu-id="0198c-159">Andra punkt objekt</span><span class="sxs-lookup"><span data-stu-id="0198c-159">Second bullet item</span></span>
- <span data-ttu-id="0198c-160">Tredje punkt objekt</span><span class="sxs-lookup"><span data-stu-id="0198c-160">Third bullet item</span></span>

#### <a name="ordered-lists"></a><span data-ttu-id="0198c-161">Ordnade listor</span><span class="sxs-lookup"><span data-stu-id="0198c-161">Ordered lists</span></span>

<span data-ttu-id="0198c-162">Om du vill inkludera ett stycke eller andra element under ett numrerat objekt, justera indrag med det första bokstaven efter objekt numret.</span><span class="sxs-lookup"><span data-stu-id="0198c-162">To include a paragraph or other elements under a numbered item, align indentation with the first character after the item number.</span></span> <span data-ttu-id="0198c-163">Alla objekt i en numrerad lista ska använda antalet `1.` snarare än att öka varje objekt.</span><span class="sxs-lookup"><span data-stu-id="0198c-163">All items in a numbered listed should use the number `1.` rather than incrementing each item.</span></span> <span data-ttu-id="0198c-164">Markdown renderar ökar värdet automatiskt.</span><span class="sxs-lookup"><span data-stu-id="0198c-164">Markdown rendering increments the value automatically.</span></span> <span data-ttu-id="0198c-165">Detta gör det enklare att ordna om objekten och standardisera indraget för underordnat innehåll.</span><span class="sxs-lookup"><span data-stu-id="0198c-165">This makes reordering items easier and standardizes the indentation of subordinate content.</span></span>

<span data-ttu-id="0198c-166">Exempel:</span><span class="sxs-lookup"><span data-stu-id="0198c-166">For example:</span></span>

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

<span data-ttu-id="0198c-167">Den resulterande markdown återges på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="0198c-167">The resulting Markdown is rendered as follows:</span></span>

1. <span data-ttu-id="0198c-168">För det första elementet infogar du ett enskilt blank steg efter 1.</span><span class="sxs-lookup"><span data-stu-id="0198c-168">For the first element, insert a single space after the 1.</span></span> <span data-ttu-id="0198c-169">Långa meningar ska omslutas till nästa rad och måste radas med det första tecknet efter den numrerade List markören.</span><span class="sxs-lookup"><span data-stu-id="0198c-169">Long sentences should be wrapped to the next line and must line up with the first character after the numbered list marker.</span></span>

   <span data-ttu-id="0198c-170">Om du vill inkludera ett andra element (t. ex. det här) infogar du en rad brytning efter det första och har justerat indrag.</span><span class="sxs-lookup"><span data-stu-id="0198c-170">To include a second element (like this one), insert a line break after the first and align indentations.</span></span> <span data-ttu-id="0198c-171">Indraget för det andra elementet måste justeras med det första tecknet efter den numrerade List markören.</span><span class="sxs-lookup"><span data-stu-id="0198c-171">The indentation of the second element must line up with the first character after the numbered list marker.</span></span> <span data-ttu-id="0198c-172">För ensiffriga objekt, t. ex. det här, kan du dra in dem till kolumn 4.</span><span class="sxs-lookup"><span data-stu-id="0198c-172">For single digit items, like this one, you indent to column 4.</span></span> <span data-ttu-id="0198c-173">För objekt med dubbla siffror, till exempel objekt nummer 10, indrag till kolumn 5.</span><span class="sxs-lookup"><span data-stu-id="0198c-173">For double digits items, for example item number 10, you indent to column 5.</span></span>

1. <span data-ttu-id="0198c-174">Nästa numrerade objekt börjar här.</span><span class="sxs-lookup"><span data-stu-id="0198c-174">The next numbered item starts here.</span></span>

### <a name="formatting-command-syntax-elements"></a><span data-ttu-id="0198c-175">Formaterar kommando element för syntax</span><span class="sxs-lookup"><span data-stu-id="0198c-175">Formatting command syntax elements</span></span>

- <span data-ttu-id="0198c-176">Använd alltid det fullständiga namnet för cmdletar och parametrar.</span><span class="sxs-lookup"><span data-stu-id="0198c-176">Always use the full name for cmdlets and parameters.</span></span> <span data-ttu-id="0198c-177">Undvik att använda alias om du inte specifikt demonstrerar aliaset.</span><span class="sxs-lookup"><span data-stu-id="0198c-177">Avoid using aliases unless you are specifically demonstrating the alias.</span></span>

- <span data-ttu-id="0198c-178">I ett stycke ska språknyckelord, cmdlet-namn, variabler och fil Sök vägar omslutas i`` ` ``-tecken (text).</span><span class="sxs-lookup"><span data-stu-id="0198c-178">Within a paragraph, language keywords, cmdlet names, variables, and file paths should be wrapped in backtick (`` ` ``) characters.</span></span> <span data-ttu-id="0198c-179">Egenskaps-, parameter-och klass namn ska vara **fetstil**.</span><span class="sxs-lookup"><span data-stu-id="0198c-179">Property, parameter, and class names should be **bold**.</span></span>

  <span data-ttu-id="0198c-180">Exempel:</span><span class="sxs-lookup"><span data-stu-id="0198c-180">For example:</span></span>

  ~~~markdown
  The following code uses `Get-ChildItem` to list the contents of `C:\Windows` and assigns
  the output to the `$files` variable.

  ```powershell
  $files = Get-ChildItem C:\Windows
  ```
  ~~~

- <span data-ttu-id="0198c-181">När du refererar till en parameter efter namn ska namnet vara **fetstilt**.</span><span class="sxs-lookup"><span data-stu-id="0198c-181">When referring to a parameter by name, the name should be **bold**.</span></span> <span data-ttu-id="0198c-182">När du illustrerar användningen av en parameter med avstavnings prefixet ska parametern omslutas med baktick.</span><span class="sxs-lookup"><span data-stu-id="0198c-182">When illustrating the use of a parameter with the hyphen prefix, the parameter should be wrapped in backticks.</span></span> <span data-ttu-id="0198c-183">Exempel:</span><span class="sxs-lookup"><span data-stu-id="0198c-183">For example:</span></span>

  ```markdown
  The parameter's name is **Name**, but it is typed as `-Name` when used on the command
  line as a parameter.
  ```

- <span data-ttu-id="0198c-184">När du refererar till externa kommandon (EXEs, skript osv.) ska kommando namnet vara fetstilt, alla gemener (eller versaler i början av en mening) och inkludera lämpligt fil namns tillägg.</span><span class="sxs-lookup"><span data-stu-id="0198c-184">When referring to external commands (EXEs, scripts, etc.), the command name should be bold, all lowercase (or capitalized if at the beginning of a sentence), and include the appropriate file extension.</span></span> <span data-ttu-id="0198c-185">Exempel:</span><span class="sxs-lookup"><span data-stu-id="0198c-185">For example:</span></span>

  ```markdown
  For example, on Windows systems, you can use the `net start` and `net stop` commands
  to start and stop a service. **Sc.exe** is another service control tool for Windows.
  That name does not fit into the naming pattern for the **net.exe** service commands.
  ```

- <span data-ttu-id="0198c-186">När du visar exempel användningen av ett externt kommando ska exemplet omslutas med baktick.</span><span class="sxs-lookup"><span data-stu-id="0198c-186">When showing example usage of an external command, the example should be wrapped in backticks.</span></span>
  <span data-ttu-id="0198c-187">Om det finns en namn konflikt med ett alias måste du inkludera fil tillägget i kommando exemplet.</span><span class="sxs-lookup"><span data-stu-id="0198c-187">When there is a name collisions with an alias you must include the file extension in the command example.</span></span> <span data-ttu-id="0198c-188">Exempel:</span><span class="sxs-lookup"><span data-stu-id="0198c-188">For example:</span></span>

  ```markdown
  To start the spooler service on a remote computer named DC01, you type `sc.exe \\DC01 start spooler`.
  ```

- <span data-ttu-id="0198c-189">När du skriver en konceptuell artikel (till skillnad från referens innehållet) ska den första instansen av ett cmdlet-namn hyperlänkas till cmdlet-dokumentationen.</span><span class="sxs-lookup"><span data-stu-id="0198c-189">When writing a conceptual article (as opposed to reference content), the first instance of a cmdlet name should be hyperlinked to the cmdlet documentation.</span></span> <span data-ttu-id="0198c-190">Använd inte autoskalning, fetstil eller andra markeringar inuti hakparenteserna för en hyperlänk.</span><span class="sxs-lookup"><span data-stu-id="0198c-190">Do not use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>

  <span data-ttu-id="0198c-191">Exempel:</span><span class="sxs-lookup"><span data-stu-id="0198c-191">For example:</span></span>

  ```markdown
  This [Write-Host](/powershell/module/Microsoft.PowerShell.Utility/Write-Host) cmdlet
  uses the **Object** parameter to ...
  ```

  <span data-ttu-id="0198c-192">Mer information finns i avsnittet [hyperlinks](#hyperlinks) i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="0198c-192">For more information, see [Hyperlinks](#hyperlinks) section of this article.</span></span>

### <a name="images"></a><span data-ttu-id="0198c-193">Avbildningar</span><span class="sxs-lookup"><span data-stu-id="0198c-193">Images</span></span>

<span data-ttu-id="0198c-194">Syntaxen för att inkludera en avbildning är:</span><span class="sxs-lookup"><span data-stu-id="0198c-194">The syntax to include an image is:</span></span>

```markdown
![[alt text]](<folderPath>)

Example:
![Introduction](./media/overview/Introduction.png)
```

<span data-ttu-id="0198c-195">Där `alt text` är en kort beskrivning av avbildningen och `<folder path>` är en relativ sökväg till avbildningen.</span><span class="sxs-lookup"><span data-stu-id="0198c-195">Where `alt text` is a brief description of the image and `<folder path>` is a relative path to the image.</span></span> <span data-ttu-id="0198c-196">Alternativ text krävs för skärm läsare för synskadade.</span><span class="sxs-lookup"><span data-stu-id="0198c-196">Alternate text is required for screen readers for the visually impaired.</span></span> <span data-ttu-id="0198c-197">Det är också användbart om ett plats fel uppstår där avbildningen inte kan återges.</span><span class="sxs-lookup"><span data-stu-id="0198c-197">It is also useful in case there is a site bug where the image cannot be rendered.</span></span>

<span data-ttu-id="0198c-198">Avbildningar ska lagras i en `media/<article-name>`-mapp i den mapp som innehåller artikeln.</span><span class="sxs-lookup"><span data-stu-id="0198c-198">Images should be stored in a `media/<article-name>` folder within the folder containing the article.</span></span>
<span data-ttu-id="0198c-199">Bilder ska inte delas mellan artiklar.</span><span class="sxs-lookup"><span data-stu-id="0198c-199">Images should not be shared between articles.</span></span> <span data-ttu-id="0198c-200">Skapa en mapp som matchar fil namnet för din artikel under mappen `media`.</span><span class="sxs-lookup"><span data-stu-id="0198c-200">Create a folder that matches the filename of your article under the `media` folder.</span></span> <span data-ttu-id="0198c-201">Kopiera avbildningarna för artikeln till den nya mappen.</span><span class="sxs-lookup"><span data-stu-id="0198c-201">Copy the images for that article to that new folder.</span></span> <span data-ttu-id="0198c-202">Om en bild används av flera artiklar måste varje mapp i bilden ha en kopia av avbildnings filen.</span><span class="sxs-lookup"><span data-stu-id="0198c-202">If an image is used by multiple articles, each image folder must have a copy of that image file.</span></span> <span data-ttu-id="0198c-203">Den här metoden förhindrar en ändring av en bild i en artikel som påverkar en annan artikel.</span><span class="sxs-lookup"><span data-stu-id="0198c-203">This practice prevents a change to an image in one article affecting another article.</span></span>

<span data-ttu-id="0198c-204">Följande bild fil typer stöds: `*.png`, `*.gif`, `*.jpeg`, `*.jpg`, `*.svg`</span><span class="sxs-lookup"><span data-stu-id="0198c-204">The following image file types are supported: `*.png`, `*.gif`, `*.jpeg`, `*.jpg`, `*.svg`</span></span>

### <a name="markdown-extensions-supported-by-open-publishing"></a><span data-ttu-id="0198c-205">Markdown-tillägg stöds av Open Publishing</span><span class="sxs-lookup"><span data-stu-id="0198c-205">Markdown extensions supported by Open Publishing</span></span>

<span data-ttu-id="0198c-206">[Microsoft docs redigerings paketet](/contribute/how-to-write-docs-auth-pack) innehåller verktyg som stöder funktioner som är unika för vårt publicerings system.</span><span class="sxs-lookup"><span data-stu-id="0198c-206">The [Microsoft Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack) contains tools that support features unique to our publishing system.</span></span> <span data-ttu-id="0198c-207">Aviseringar är ett markdown-tillägg för att skapa block offerter som återger docs.microsoft.com med färger och ikoner som visar innebörden av innehållet.</span><span class="sxs-lookup"><span data-stu-id="0198c-207">Alerts are a Markdown extension to create block quotes that render on docs.microsoft.com with colors and icons that indicate the significance of the content.</span></span> <span data-ttu-id="0198c-208">Följande aviserings typer stöds:</span><span class="sxs-lookup"><span data-stu-id="0198c-208">The following alert types are supported:</span></span>

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

<span data-ttu-id="0198c-209">Dessa aviseringar ser ut så här på docs.microsoft.com:</span><span class="sxs-lookup"><span data-stu-id="0198c-209">These alerts look like this on docs.microsoft.com:</span></span>

> [!NOTE]
> <span data-ttu-id="0198c-210">Information som användaren bör märka även om skumering.</span><span class="sxs-lookup"><span data-stu-id="0198c-210">Information the user should notice even if skimming.</span></span>

> [!TIP]
> <span data-ttu-id="0198c-211">Valfri information som hjälper en användare att bli mer framgångs rik.</span><span class="sxs-lookup"><span data-stu-id="0198c-211">Optional information to help a user be more successful.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0198c-212">Nödvändig information krävs för att användaren ska lyckas.</span><span class="sxs-lookup"><span data-stu-id="0198c-212">Essential information required for user success.</span></span>

> [!CAUTION]
> <span data-ttu-id="0198c-213">Negativa potentiella följder av en åtgärd.</span><span class="sxs-lookup"><span data-stu-id="0198c-213">Negative potential consequences of an action.</span></span>

> [!WARNING]
> <span data-ttu-id="0198c-214">Farliga vissa följder av en åtgärd.</span><span class="sxs-lookup"><span data-stu-id="0198c-214">Dangerous certain consequences of an action.</span></span>

## <a name="hyperlinks"></a><span data-ttu-id="0198c-215">Hyperlänkar</span><span class="sxs-lookup"><span data-stu-id="0198c-215">Hyperlinks</span></span>

- <span data-ttu-id="0198c-216">Undvik att använda Bare-URL: er.</span><span class="sxs-lookup"><span data-stu-id="0198c-216">Avoid using bare URLs.</span></span> <span data-ttu-id="0198c-217">Länkar bör använda markdown syntax `[friendlyname](url-or-path)`</span><span class="sxs-lookup"><span data-stu-id="0198c-217">Links should use Markdown syntax `[friendlyname](url-or-path)`</span></span>
- <span data-ttu-id="0198c-218">Bare-URL: er kan användas vid behov, men ska stå inom bakstreck.</span><span class="sxs-lookup"><span data-stu-id="0198c-218">Bare URLs may be used when necessary, but should be enclosed in backticks.</span></span> <span data-ttu-id="0198c-219">Exempel:</span><span class="sxs-lookup"><span data-stu-id="0198c-219">For example:</span></span>

  ```markdown
  By default, if you do not specify this parameter, the DMTF standard resource URI
  `http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/` is used and the class name is appended to it.
  ```

- <span data-ttu-id="0198c-220">URL-länkar bör vara HTTPS när det är möjligt.</span><span class="sxs-lookup"><span data-stu-id="0198c-220">URL links should be HTTPS when possible.</span></span>
- <span data-ttu-id="0198c-221">Länkar måste ha ett eget namn, vanligt vis rubriken för det länkade ämnet</span><span class="sxs-lookup"><span data-stu-id="0198c-221">Links must have a friendly name, usually the title of the linked topic</span></span>
- <span data-ttu-id="0198c-222">Alla objekt i avsnittet "relaterade länkar" längst ned ska vara hyperlänkade.</span><span class="sxs-lookup"><span data-stu-id="0198c-222">All items in the "related links" section at the bottom should be hyperlinked.</span></span>
- <span data-ttu-id="0198c-223">Använd inte autoskalning, fetstil eller andra markeringar inuti hakparenteserna för en hyperlänk.</span><span class="sxs-lookup"><span data-stu-id="0198c-223">Do not use backticks, bold, or other markup inside the brackets of a hyperlink.</span></span>

### <a name="linking-to-other-content"></a><span data-ttu-id="0198c-224">Länka till annat innehåll</span><span class="sxs-lookup"><span data-stu-id="0198c-224">Linking to other content</span></span>

<span data-ttu-id="0198c-225">Det finns två typer av hyperlänkar som stöds av publicerings systemet: URL: er och fil länkar.</span><span class="sxs-lookup"><span data-stu-id="0198c-225">There are two types of hyperlinks supported by the publishing system: URLs and file links.</span></span>

<span data-ttu-id="0198c-226">En URL-länk kan vara en URL-sökväg som är relativ till roten i docs.microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="0198c-226">A URL link can be a URL path that is relative to the root of docs.microsoft.com.</span></span> <span data-ttu-id="0198c-227">Eller en absolut URL som innehåller fullständig URL-syntax.</span><span class="sxs-lookup"><span data-stu-id="0198c-227">Or an absolute URL that include the full URL syntax.</span></span> <span data-ttu-id="0198c-228">(Till exempel: `https:/github.com/MicrosoftDocs/PowerShell-Docs`)</span><span class="sxs-lookup"><span data-stu-id="0198c-228">(For example: `https:/github.com/MicrosoftDocs/PowerShell-Docs`)</span></span>

- <span data-ttu-id="0198c-229">Använd URL-länkar när du länkar till innehåll utanför PowerShell-dokument eller mellan cmdlet-referenser och konceptuella artiklar i PowerShell-dokument.</span><span class="sxs-lookup"><span data-stu-id="0198c-229">Use URL links when linking to content outside of PowerShell-Docs or between cmdlet reference and conceptual articles within PowerShell-docs.</span></span>
- <span data-ttu-id="0198c-230">Det enklaste sättet att skapa en relativ länk är att kopiera URL: en från webbläsaren och sedan ta bort `https://docs.microsoft.com/en-us` från det värde som du klistrar in i markdown.</span><span class="sxs-lookup"><span data-stu-id="0198c-230">The simplest way to create a relative link is to copy the URL from your browser then remove `https://docs.microsoft.com/en-us` from the value you paste into markdown.</span></span>
   - <span data-ttu-id="0198c-231">Ta inte med språk i URL: er för Microsoft-egenskaper (t. ex.</span><span class="sxs-lookup"><span data-stu-id="0198c-231">Do not include locales in URLs on Microsoft properties (eg.</span></span> <span data-ttu-id="0198c-232">ta bort "/en-US" från URL: en.</span><span class="sxs-lookup"><span data-stu-id="0198c-232">remove "/en-us" from URL).</span></span>
- <span data-ttu-id="0198c-233">Alla URL: er till externa webbplatser bör använda HTTPS om det inte är giltigt för mål platsen.</span><span class="sxs-lookup"><span data-stu-id="0198c-233">All URLs to external websites should use HTTPS unless that is not valid for the target site.</span></span>

<span data-ttu-id="0198c-234">En fil länk används för att länka från en referens artikel till en annan, eller från en konceptuell artikel till en annan.</span><span class="sxs-lookup"><span data-stu-id="0198c-234">A file link is used to link from one reference article to another, or from one conceptual article to another.</span></span> <span data-ttu-id="0198c-235">Om du behöver länka till en referens artikel för en viss version av PowerShell måste du använda en URL-länk.</span><span class="sxs-lookup"><span data-stu-id="0198c-235">If you need to link to a reference article for a specific version of PowerShell, then you need to use a URL link.</span></span>

- <span data-ttu-id="0198c-236">Fil länkar innehåller en relativ fil Sök väg (till exempel: `../folder/file.md`)</span><span class="sxs-lookup"><span data-stu-id="0198c-236">File links contain a relative file path (for example: `../folder/file.md`)</span></span>
- <span data-ttu-id="0198c-237">Alla fil Sök vägar använder snedstreck (`/`) tecken</span><span class="sxs-lookup"><span data-stu-id="0198c-237">All file paths use forward-slash (`/`) characters</span></span>

## <a name="formatting-code-samples"></a><span data-ttu-id="0198c-238">Formatera kod exempel</span><span class="sxs-lookup"><span data-stu-id="0198c-238">Formatting code samples</span></span>

<span data-ttu-id="0198c-239">Markdown stöder två olika kod format:</span><span class="sxs-lookup"><span data-stu-id="0198c-239">Markdown supports two different code styles:</span></span>

- <span data-ttu-id="0198c-240">Kod sträcker sig över (infogade) – markerade med ett enda`` ` ``-tecken.</span><span class="sxs-lookup"><span data-stu-id="0198c-240">Code spans (inline) - marked by a single backtick (`` ` ``) character.</span></span> <span data-ttu-id="0198c-241">Används inom ett stycke i stället för som ett fristående block.</span><span class="sxs-lookup"><span data-stu-id="0198c-241">Used within a paragraph rather than as a standalone block.</span></span>
- <span data-ttu-id="0198c-242">Kodblock – ett block med flera rader som omges av tredubbla`` ``` ``-strängar (Triple-Ticket).</span><span class="sxs-lookup"><span data-stu-id="0198c-242">Code blocks - a multi-line block surrounded by triple-backtick (`` ``` ``) strings.</span></span> <span data-ttu-id="0198c-243">Kod block kan också ha en språk etikett efter bakstrecken.</span><span class="sxs-lookup"><span data-stu-id="0198c-243">Code blocks may also have a language label following the backticks.</span></span> <span data-ttu-id="0198c-244">Språk etiketten aktiverar syntax för innehållet i kod blocket.</span><span class="sxs-lookup"><span data-stu-id="0198c-244">The language label enables syntax highlighting for the contents of the code block.</span></span>

### <a name="using-code-blocks"></a><span data-ttu-id="0198c-245">Använda kodblock</span><span class="sxs-lookup"><span data-stu-id="0198c-245">Using code blocks</span></span>

<span data-ttu-id="0198c-246">Markdown gör att indrag kan använda ett kodblock, men det här mönstret kan vara problematiskt och bör undvikas.</span><span class="sxs-lookup"><span data-stu-id="0198c-246">Markdown allows for indentation to signify a code block, but this pattern can be problematic and should be avoided.</span></span> <span data-ttu-id="0198c-247">Alla kodblock ska finnas i en kod avgränsning.</span><span class="sxs-lookup"><span data-stu-id="0198c-247">All code blocks should be contained in a code fence.</span></span> <span data-ttu-id="0198c-248">En kod avgränsning är ett kodblock som omges av tredubbel-`` ``` ``-strängar (Triple-Ticket).</span><span class="sxs-lookup"><span data-stu-id="0198c-248">A code fence is a block of code surrounded by triple-backtick (`` ``` ``) strings.</span></span> <span data-ttu-id="0198c-249">Kod avgränsnings markörerna måste finnas på en egen rad före och efter kod exemplet.</span><span class="sxs-lookup"><span data-stu-id="0198c-249">The code fence markers must be on their own line before and after the code sample.</span></span> <span data-ttu-id="0198c-250">Markören i början av kod blocket kan ha en valfri språk etikett.</span><span class="sxs-lookup"><span data-stu-id="0198c-250">The marker at the start of the code block may have an optional language label.</span></span> <span data-ttu-id="0198c-251">Microsoft Open Publishing system (OPS) använder språk etiketten för att stödja funktionen för att markera funktioner.</span><span class="sxs-lookup"><span data-stu-id="0198c-251">Microsoft's Open Publishing System (OPS) uses the language label to support the syntax highlighting feature.</span></span>

<span data-ttu-id="0198c-252">OPS lägger också till en **kopierings** knapp som kopierar innehållet i kod blocket till Urklipp.</span><span class="sxs-lookup"><span data-stu-id="0198c-252">OPS also adds a **Copy** button that copies the contents of the code block to the clipboard.</span></span> <span data-ttu-id="0198c-253">På så sätt kan du snabbt klistra in koden i ett skript för att testa kod exemplet.</span><span class="sxs-lookup"><span data-stu-id="0198c-253">This allows you to quickly paste the code into a script for testing the code example.</span></span> <span data-ttu-id="0198c-254">Alla exempel i vår dokumentation är dock inte avsedda att köras.</span><span class="sxs-lookup"><span data-stu-id="0198c-254">However, not all examples in our documentation are intended to be run.</span></span> <span data-ttu-id="0198c-255">Vissa kod block är enkla illustrationer av ett PowerShell-begrepp.</span><span class="sxs-lookup"><span data-stu-id="0198c-255">Some code blocks are simple illustrations of a PowerShell concept.</span></span>

<span data-ttu-id="0198c-256">Det finns två typer av kod block som används i vår dokumentation:</span><span class="sxs-lookup"><span data-stu-id="0198c-256">There are two types code blocks used in our documentation:</span></span>

1. <span data-ttu-id="0198c-257">Exempel på exempel</span><span class="sxs-lookup"><span data-stu-id="0198c-257">Illustrative examples</span></span>
2. <span data-ttu-id="0198c-258">Körbara exempel</span><span class="sxs-lookup"><span data-stu-id="0198c-258">Executable examples</span></span>

### <a name="syntax-code-blocks"></a><span data-ttu-id="0198c-259">Kod block för syntax</span><span class="sxs-lookup"><span data-stu-id="0198c-259">Syntax code blocks</span></span>

<span data-ttu-id="0198c-260">Det här exemplet illustrerar alla möjliga parametrar i `Get-Command`-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="0198c-260">This example illustrates all the possible parameters of the `Get-Command` cmdlet.</span></span>

~~~markdown
```
Get-Command [-Verb <String[]>] [-Noun <String[]>] [-Module <String[]>]
  [-FullyQualifiedModule <ModuleSpecification[]>] [-TotalCount <Int32>] [-Syntax] [-ShowCommandInfo]
  [[-ArgumentList] <Object[]>] [-All] [-ListImported] [-ParameterName <String[]>]
  [-ParameterType <PSTypeName[]>] [<CommonParameters>]
```
~~~

<span data-ttu-id="0198c-261">I det här exemplet beskrivs `for`-instruktionen i generaliserade villkor:</span><span class="sxs-lookup"><span data-stu-id="0198c-261">This example describes the `for` statement in generalized terms:</span></span>

~~~markdown
```
for (<init>; <condition>; <repeat>)
{<statement list>}
```
~~~

### <a name="illustrative-examples"></a><span data-ttu-id="0198c-262">Exempel på exempel</span><span class="sxs-lookup"><span data-stu-id="0198c-262">Illustrative examples</span></span>

<span data-ttu-id="0198c-263">Exempel på exempel används för att förklara ett PowerShell-begrepp.</span><span class="sxs-lookup"><span data-stu-id="0198c-263">Illustrative examples are used to explain a PowerShell concept.</span></span> <span data-ttu-id="0198c-264">De är inte avsedda att kopieras till Urklipp för körning.</span><span class="sxs-lookup"><span data-stu-id="0198c-264">They are not meant to be copied to the clipboard for execution.</span></span> <span data-ttu-id="0198c-265">Dessa används vanligt vis för enkla exempel som är enkla att skriva.</span><span class="sxs-lookup"><span data-stu-id="0198c-265">These are most commonly used for simple examples that are easy to type.</span></span>
<span data-ttu-id="0198c-266">De används också för syntax-exempel där du illustrerar syntaxen för ett kommando.</span><span class="sxs-lookup"><span data-stu-id="0198c-266">They are also used for syntax examples where you are illustrating the syntax of a command.</span></span> <span data-ttu-id="0198c-267">Kod blocket kan innehålla exempel på utdata från kommandot som illustreras.</span><span class="sxs-lookup"><span data-stu-id="0198c-267">The code block may contain example output from the command being illustrated.</span></span>

<span data-ttu-id="0198c-268">Här är ett enkelt exempel som illustrerar en PowerShell-jämförelse operatorer:</span><span class="sxs-lookup"><span data-stu-id="0198c-268">Here is a simple example illustrating a PowerShell comparison operators:</span></span>

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

<span data-ttu-id="0198c-269">Observera att det här exemplet har den förenklade PowerShell-prompten och visar resultatet.</span><span class="sxs-lookup"><span data-stu-id="0198c-269">Note that this example has the simplified PowerShell prompt and shows the resulting output.</span></span> <span data-ttu-id="0198c-270">I det här fallet har vi inte förvarat läsaren för att kopiera och köra det här exemplet.</span><span class="sxs-lookup"><span data-stu-id="0198c-270">In this case, we don't intend the reader to copy and run this example.</span></span>

### <a name="executable-examples"></a><span data-ttu-id="0198c-271">Körbara exempel</span><span class="sxs-lookup"><span data-stu-id="0198c-271">Executable examples</span></span>

<span data-ttu-id="0198c-272">Mer komplexa exempel eller exempel som är avsedda att vara användbara för att kopiera och köra ska använda följande block/stil-markering:</span><span class="sxs-lookup"><span data-stu-id="0198c-272">More complex examples or examples that are intended to be useful to copy and execute should use the following block-style markup:</span></span>

~~~markdown
```powershell
<PowerShell code goes here>
```
~~~

<span data-ttu-id="0198c-273">De utdata som visas av PowerShell-kommandon måste omges av ett **utmatnings** kods block för att förhindra markering av syntax.</span><span class="sxs-lookup"><span data-stu-id="0198c-273">The output displayed by PowerShell commands should be enclosed in an **Output** code block to prevent syntax highlighting.</span></span> <span data-ttu-id="0198c-274">Exempel:</span><span class="sxs-lookup"><span data-stu-id="0198c-274">For example:</span></span>

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

<span data-ttu-id="0198c-275">Etiketten för den **resulterande** koden är inte ett officiellt språk som stöds av syntaxens markerings system.</span><span class="sxs-lookup"><span data-stu-id="0198c-275">The **Output** code label is not an official "language" supported by the syntax highlighting system.</span></span>
<span data-ttu-id="0198c-276">Den här etiketten är dock användbar eftersom OPS lägger till etiketten "utdata" i rutan med kod rutan på webb sidan.</span><span class="sxs-lookup"><span data-stu-id="0198c-276">However, this label is useful because OPS adds the "Output" label to the code box frame on the web page.</span></span> <span data-ttu-id="0198c-277">Kod rutan "utdata" har ingen markering av syntax.</span><span class="sxs-lookup"><span data-stu-id="0198c-277">The "Output" code box has no syntax highlighting.</span></span>

## <a name="coding-style-rules"></a><span data-ttu-id="0198c-278">Regler för kodnings format</span><span class="sxs-lookup"><span data-stu-id="0198c-278">Coding style rules</span></span>

### <a name="avoid-line-continuation-in-code-samples"></a><span data-ttu-id="0198c-279">Undvik rad fortsättning i kod exempel</span><span class="sxs-lookup"><span data-stu-id="0198c-279">Avoid line continuation in code samples</span></span>

<span data-ttu-id="0198c-280">Undvik att använda linje fortsättnings tecken (`` ` ``) i PowerShell-kod exempel.</span><span class="sxs-lookup"><span data-stu-id="0198c-280">Avoid using line continuation characters (`` ` ``) in PowerShell code examples.</span></span> <span data-ttu-id="0198c-281">Detta är svårt att se och kan orsaka problem om det finns extra blank steg i slutet av raden.</span><span class="sxs-lookup"><span data-stu-id="0198c-281">These are hard to see and can cause problems if there are extra spaces at the end of the line.</span></span>

- <span data-ttu-id="0198c-282">Använd PowerShell-ihopbuntning för att minska rad längden för cmdletar som har många parametrar.</span><span class="sxs-lookup"><span data-stu-id="0198c-282">Use PowerShell splatting to reduce line length for cmdlets that have a lot of parameters.</span></span>
- <span data-ttu-id="0198c-283">Dra nytta av PowerShell: s naturliga rad brytnings möjligheter, t. ex. efter pipe-tecken (`|`), inledande klammerparentes, parenteser och hakparenteser.</span><span class="sxs-lookup"><span data-stu-id="0198c-283">Take advantage of PowerShell's natural line break opportunities, like after pipe (`|`) characters, opening braces, parentheses, and brackets.</span></span>

### <a name="avoid-using-powershell-prompts-in-examples"></a><span data-ttu-id="0198c-284">Undvik att använda PowerShell-prompter i exempel</span><span class="sxs-lookup"><span data-stu-id="0198c-284">Avoid using PowerShell prompts in examples</span></span>

<span data-ttu-id="0198c-285">Användning av LED text strängen rekommenderas inte och bör begränsas till scenarier som är avsedda att illustrera kommando linje användningen.</span><span class="sxs-lookup"><span data-stu-id="0198c-285">Use of the prompt string is discouraged and should be limited to scenarios that are meant to illustrate command line usage.</span></span> <span data-ttu-id="0198c-286">I de flesta av de här exemplen ska LED texten vara `PS>`.</span><span class="sxs-lookup"><span data-stu-id="0198c-286">For most of these examples, the prompt string should be `PS>`.</span></span> <span data-ttu-id="0198c-287">Den här frågan är oberoende av OS-/regionsspecifika indikatorer.</span><span class="sxs-lookup"><span data-stu-id="0198c-287">This prompt is independent of OS-specific indicators.</span></span>

<span data-ttu-id="0198c-288">Prompter krävs för exempel som illustrerar kommandon som ändrar prompten eller när den angivna sökvägen är viktig för scenariot som illustreras.</span><span class="sxs-lookup"><span data-stu-id="0198c-288">Prompts are required for examples that illustrate commands that alter the prompt or when the path displayed is significant to the scenario being illustrated.</span></span> <span data-ttu-id="0198c-289">I följande exempel visas hur prompten ändras när du använder Registry-providern.</span><span class="sxs-lookup"><span data-stu-id="0198c-289">The following example illustrates how the prompt changes when using the Registry provider.</span></span>

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

### <a name="do-not-use-aliases-in-examples"></a><span data-ttu-id="0198c-290">Använd inte alias i exempel</span><span class="sxs-lookup"><span data-stu-id="0198c-290">Do not use aliases in examples</span></span>

<span data-ttu-id="0198c-291">Du bör alltid använda det fullständiga namnet på alla cmdletar och parametrar om du inte specifikt pratar om aliaset.</span><span class="sxs-lookup"><span data-stu-id="0198c-291">You should always use the full name of all cmdlets and parameters unless you are specifically talking about the alias.</span></span> <span data-ttu-id="0198c-292">Cmdlet-och parameter namn måste använda rätt stavning som definierats i koden.</span><span class="sxs-lookup"><span data-stu-id="0198c-292">Cmdlet and parameter names must use the proper spelling defined in the code.</span></span>

### <a name="using-parameters-in-examples"></a><span data-ttu-id="0198c-293">Använda parametrar i exempel</span><span class="sxs-lookup"><span data-stu-id="0198c-293">Using parameters in examples</span></span>

<span data-ttu-id="0198c-294">Undvik att använda positions parametrar.</span><span class="sxs-lookup"><span data-stu-id="0198c-294">Avoid using positional parameters.</span></span> <span data-ttu-id="0198c-295">I allmänhet bör du alltid inkludera parameter namnet i ett exempel, även om parametern är i position.</span><span class="sxs-lookup"><span data-stu-id="0198c-295">In general, you should always include the parameter name in an example, even if the parameter is positional.</span></span> <span data-ttu-id="0198c-296">Detta minskar risken för förvirring i exemplen.</span><span class="sxs-lookup"><span data-stu-id="0198c-296">This reduces the chance of confusion in your examples.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0198c-297">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="0198c-297">Next steps</span></span>

[<span data-ttu-id="0198c-298">Redigera cmdlet-referens</span><span class="sxs-lookup"><span data-stu-id="0198c-298">Editing cmdlet reference</span></span>](editing-cmdlet-ref.md)

<!-- External URLs -->
[platyPS]: https://github.com/PowerShell/platyPS
[markdig]: https://github.com/lunet-io/markdig
[CommonMark]: https://spec.commonmark.org/
[atx]: https://github.github.com/gfm/#atx-headings
[pascal-case]: https://en.wikipedia.org/wiki/PascalCase
[reflow]: https://marketplace.visualstudio.com/items?itemName=marvhen.reflow-markdown
