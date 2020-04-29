---
title: Redigera referens artiklar
description: Den här artikeln beskriver de specifika kraven för att redigera cmdlet-referenser och om ämnen i PowerShell-dokumentationen.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: e135f6cc81ba7537a535a08421e1ca9b2b2af573
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81624779"
---
# <a name="editing-reference-articles"></a><span data-ttu-id="05c07-103">Redigera referens artiklar</span><span class="sxs-lookup"><span data-stu-id="05c07-103">Editing reference articles</span></span>

<span data-ttu-id="05c07-104">Artiklar med cmdlet-referenser har en speciell struktur.</span><span class="sxs-lookup"><span data-stu-id="05c07-104">Cmdlet reference articles have a specific structure.</span></span> <span data-ttu-id="05c07-105">Strukturen definieras av [PlatyPS][].</span><span class="sxs-lookup"><span data-stu-id="05c07-105">This structure is defined by [PlatyPS][].</span></span>
<span data-ttu-id="05c07-106">PlatyPS genererar cmdlet-hjälpen för PowerShell-moduler i markdown.</span><span class="sxs-lookup"><span data-stu-id="05c07-106">PlatyPS generates the cmdlet help for PowerShell modules in Markdown.</span></span> <span data-ttu-id="05c07-107">När du har redigerat Markdown-filerna används PlatyPS för att skapa MAML-hjälpfiler som används av cmdleten `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="05c07-107">After editing the Markdown files, PlatyPS is used create the MAML help files used by the `Get-Help` cmdlet.</span></span>

<span data-ttu-id="05c07-108">PlatyPS har ett hårdkodat schema för cmdlet-referenser som skrivs in i koden.</span><span class="sxs-lookup"><span data-stu-id="05c07-108">PlatyPS has a hard-coded schema for cmdlet reference that is written into the code.</span></span> <span data-ttu-id="05c07-109">Dokumentet [platyPS.schema.md][] är ett försök att beskriva strukturen.</span><span class="sxs-lookup"><span data-stu-id="05c07-109">The [platyPS.schema.md][] document attempts to describe this structure.</span></span> <span data-ttu-id="05c07-110">Schemaöverträdelser orsakar build-fel som måste åtgärdas innan vi kan acceptera ditt bidrag.</span><span class="sxs-lookup"><span data-stu-id="05c07-110">Schema violations cause build errors that must be fixed before we can accept your contribution.</span></span>

## <a name="general-guidelines"></a><span data-ttu-id="05c07-111">Allmänna riktlinjer</span><span class="sxs-lookup"><span data-stu-id="05c07-111">General guidelines</span></span>

- <span data-ttu-id="05c07-112">Ta inte bort någon av rubrikstrukturerna.</span><span class="sxs-lookup"><span data-stu-id="05c07-112">Do not remove any of the header structures.</span></span> <span data-ttu-id="05c07-113">PlatyPS förväntar sig en specifik uppsättning rubriker.</span><span class="sxs-lookup"><span data-stu-id="05c07-113">PlatyPS expects a specific set of headers.</span></span>
- <span data-ttu-id="05c07-114">Rubrikerna **Indatatyp** och **Utdatatyp** måste ha en typ.</span><span class="sxs-lookup"><span data-stu-id="05c07-114">The **Input type** and **Output type** headers must have a type.</span></span> <span data-ttu-id="05c07-115">Om cmdleten inte kräver inmatade värden eller returnerar ett värde använder du `None`värdet.</span><span class="sxs-lookup"><span data-stu-id="05c07-115">If the cmdlet does not take input or return a value then use the value `None`.</span></span>
- <span data-ttu-id="05c07-116">Inhägnade kodblock är bara tillåtna i avsnittet [Exempel](#structuring-examples).</span><span class="sxs-lookup"><span data-stu-id="05c07-116">Fenced code blocks are only allowed in the [Examples](#structuring-examples) section.</span></span>
- <span data-ttu-id="05c07-117">Infogade kodomfång kan användas i alla stycken.</span><span class="sxs-lookup"><span data-stu-id="05c07-117">Inline code spans can be used in any paragraph.</span></span>

## <a name="formatting-about_-files"></a><span data-ttu-id="05c07-118">Formatera About_-filer</span><span class="sxs-lookup"><span data-stu-id="05c07-118">Formatting About_ files</span></span>

<span data-ttu-id="05c07-119">`About_*`filerna skrivs i markdown men levereras som oformaterade textfiler.</span><span class="sxs-lookup"><span data-stu-id="05c07-119">`About_*` files are written in Markdown but are shipped as plain text files.</span></span> <span data-ttu-id="05c07-120">Vi använder [pandoc][] för att konvertera markdown till oformaterad text.</span><span class="sxs-lookup"><span data-stu-id="05c07-120">We use [Pandoc][] to convert the Markdown to plain text.</span></span> <span data-ttu-id="05c07-121">`About_*`filerna är formaterade för bästa kompatibilitet i alla versioner av PowerShell och med publicerings verktygen.</span><span class="sxs-lookup"><span data-stu-id="05c07-121">`About_*` files are formatted for the best compatibility across all versions of PowerShell and with the publishing tools.</span></span>

<span data-ttu-id="05c07-122">Riktlinjer för grundläggande formatering:</span><span class="sxs-lookup"><span data-stu-id="05c07-122">Basic formatting guidelines:</span></span>

- <span data-ttu-id="05c07-123">Begränsa rader till 80 tecken.</span><span class="sxs-lookup"><span data-stu-id="05c07-123">Limit lines to 80 characters.</span></span> <span data-ttu-id="05c07-124">Pandoc drar in vissa markdown-block så att dessa block måste justeras.</span><span class="sxs-lookup"><span data-stu-id="05c07-124">Pandoc indents some Markdown blocks so those block must be adjusted.</span></span>
  - <span data-ttu-id="05c07-125">Kodblock är begränsade till 76 tecken</span><span class="sxs-lookup"><span data-stu-id="05c07-125">Code blocks are limited to 76 characters</span></span>
  - <span data-ttu-id="05c07-126">Tabeller är begränsade 76 tecken</span><span class="sxs-lookup"><span data-stu-id="05c07-126">Tables are limited 76 characters</span></span>
  - <span data-ttu-id="05c07-127">Blockquotes (och aviseringar) är begränsade 78 tecken</span><span class="sxs-lookup"><span data-stu-id="05c07-127">Blockquotes (and Alerts) are limited 78 characters</span></span>

- <span data-ttu-id="05c07-128">Använda pandoc särskilda meta-tecken `\`, och`$``<`</span><span class="sxs-lookup"><span data-stu-id="05c07-128">Using Pandoc's special meta-characters `\`,`$`, and `<`</span></span>
  - <span data-ttu-id="05c07-129">Inom ett sidhuvud – dessa tecken måste föregås av ett inledande `\` tecken eller omges av kod intervall med hjälp av baktick ()`` ` ``</span><span class="sxs-lookup"><span data-stu-id="05c07-129">Within a header - these characters must be escaped using a leading `\` character or enclosed in code spans using backticks (`` ` ``)</span></span>
  - <span data-ttu-id="05c07-130">I ett stycke ska de här tecknen placeras i kod intervall.</span><span class="sxs-lookup"><span data-stu-id="05c07-130">Within a paragraph, these characters should be put into code spans.</span></span> <span data-ttu-id="05c07-131">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="05c07-131">For example:</span></span>

    ~~~markdown
    ### The purpose of the \$foo variable

    The `$foo` variable is used to store ...
    ~~~

- <span data-ttu-id="05c07-132">Tabeller måste rymmas inom 76 tecken</span><span class="sxs-lookup"><span data-stu-id="05c07-132">Tables need to fit within 76 characters</span></span>
  - <span data-ttu-id="05c07-133">Radbryt innehållet i celler manuellt över flera rader</span><span class="sxs-lookup"><span data-stu-id="05c07-133">Manually wrap contents of cells across multiple lines</span></span>
  - <span data-ttu-id="05c07-134">Använd inledande och avslutande `|`-tecken på varje rad</span><span class="sxs-lookup"><span data-stu-id="05c07-134">Use opening and closing `|` characters on each line</span></span>
  - <span data-ttu-id="05c07-135">I följande exempel visas hur du skapar en tabell som innehåller information som radbryts på flera rader i en cell.</span><span class="sxs-lookup"><span data-stu-id="05c07-135">The following example illustrates how to properly construct a table that contains information that wraps on multiple lines within a cell.</span></span>

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
    > <span data-ttu-id="05c07-136">Begränsningen 76-kolumn gäller endast för `About_*` ämnen.</span><span class="sxs-lookup"><span data-stu-id="05c07-136">The 76-column limitation applies only to `About_*` topics.</span></span> <span data-ttu-id="05c07-137">Du kan använda breda kolumner i konceptuella eller cmdlet Reference-artiklar.</span><span class="sxs-lookup"><span data-stu-id="05c07-137">You can use wide columns in conceptual or cmdlet reference articles.</span></span>

## <a name="structuring-examples"></a><span data-ttu-id="05c07-138">Strukturerings exempel</span><span class="sxs-lookup"><span data-stu-id="05c07-138">Structuring examples</span></span>

<span data-ttu-id="05c07-139">I PlatyPS-schemat är rubriken **EXEMPEL** en H2-rubrik, och varje exempel är en H3-rubrik.</span><span class="sxs-lookup"><span data-stu-id="05c07-139">In the PlatyPS schema, the **EXAMPLES** header is an H2 header and each example is an H3 header.</span></span>

<span data-ttu-id="05c07-140">I ett exempel tillåter inte schemat att kodblock avgränsas med stycken.</span><span class="sxs-lookup"><span data-stu-id="05c07-140">Within an example, the schema does not allow code blocks to be separated by paragraphs.</span></span> <span data-ttu-id="05c07-141">Det schema som stöds är:</span><span class="sxs-lookup"><span data-stu-id="05c07-141">The supported schema is:</span></span>

```
### Example #X title

0 or more paragraphs
1 or more code blocks
0 or more paragraphs.
```

<span data-ttu-id="05c07-142">Numrera varje exempel och lägg till en kort rubrik.</span><span class="sxs-lookup"><span data-stu-id="05c07-142">Number each example and add a brief title.</span></span>

<span data-ttu-id="05c07-143">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="05c07-143">For example:</span></span>

### <a name="example-1-get-cmdlets-functions-and-aliases"></a><span data-ttu-id="05c07-144">Exempel 1: Hämta cmdlets, Functions och alias</span><span class="sxs-lookup"><span data-stu-id="05c07-144">Example 1: Get cmdlets, functions, and aliases</span></span>

<span data-ttu-id="05c07-145">Det här kommandot hämtar PowerShell-cmdletar, funktioner och alias som är installerade på datorn.</span><span class="sxs-lookup"><span data-stu-id="05c07-145">This command gets the PowerShell cmdlets, functions, and aliases that are installed on the computer.</span></span>

```powershell
Get-Command
```

### <a name="example-2-get-commands-in-the-current-session"></a><span data-ttu-id="05c07-146">Exempel 2: Hämta kommandon i den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="05c07-146">Example 2: Get commands in the current session</span></span>

```powershell
Get-Command -ListImported
```

## <a name="next-steps"></a><span data-ttu-id="05c07-147">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="05c07-147">Next steps</span></span>

[<span data-ttu-id="05c07-148">Checklista för redigering</span><span class="sxs-lookup"><span data-stu-id="05c07-148">Editorial checklist</span></span>](editorial-checklist.md)

<!-- link references -->
[PlatyPS]: https://github.com/powershell/platyps
[platyPS.schema.md]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[issue1806]: https://github.com/MicrosoftDocs/PowerShell-Docs/issues/1806
[about-example]: /PowerShell/module/Microsoft.PowerShell.Core/About/about_Comparison_Operators
[Pandoc]: https://pandoc.org
