---
title: Redigera referens artiklar
description: Den här artikeln beskriver de specifika kraven för att redigera cmdlet-referenser och om ämnen i PowerShell-dokumentationen.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 3aed1c14429310c57681397d4877a3a6f48400fd
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500980"
---
# <a name="editing-reference-articles"></a><span data-ttu-id="0ba52-103">Redigera referens artiklar</span><span class="sxs-lookup"><span data-stu-id="0ba52-103">Editing reference articles</span></span>

<span data-ttu-id="0ba52-104">Artiklar om cmdlet-referenser har en speciell struktur.</span><span class="sxs-lookup"><span data-stu-id="0ba52-104">Cmdlet reference articles have a specific structure.</span></span> <span data-ttu-id="0ba52-105">Den här strukturen definieras av [PlatyPS][].</span><span class="sxs-lookup"><span data-stu-id="0ba52-105">This structure is defined by [PlatyPS][].</span></span>
<span data-ttu-id="0ba52-106">PlatyPS genererar cmdlet-hjälpen för PowerShell-moduler i markdown.</span><span class="sxs-lookup"><span data-stu-id="0ba52-106">PlatyPS generates the cmdlet help for PowerShell modules in Markdown.</span></span> <span data-ttu-id="0ba52-107">När du har redigerat markdown-filerna används PlatyPS för att skapa MAML-hjälpfiler som används av `Get-Help`-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="0ba52-107">After editing the Markdown files, PlatyPS is used create the MAML help files used by the `Get-Help` cmdlet.</span></span>

<span data-ttu-id="0ba52-108">PlatyPS har ett hårdkodat schema för cmdlet-referenser som skrivs till koden.</span><span class="sxs-lookup"><span data-stu-id="0ba52-108">PlatyPS has a hard-coded schema for cmdlet reference that is written into the code.</span></span> <span data-ttu-id="0ba52-109">[PlatyPS.schema.MD][] -dokumentet försöker beskriva den här strukturen.</span><span class="sxs-lookup"><span data-stu-id="0ba52-109">The [platyPS.schema.md][] document attempts to describe this structure.</span></span> <span data-ttu-id="0ba52-110">Schema överträdelser orsakar build-fel som måste åtgärdas innan vi kan acceptera ditt bidrag.</span><span class="sxs-lookup"><span data-stu-id="0ba52-110">Schema violations cause build errors that must be fixed before we can accept your contribution.</span></span>

## <a name="general-guidelines"></a><span data-ttu-id="0ba52-111">Allmänna riktlinjer</span><span class="sxs-lookup"><span data-stu-id="0ba52-111">General guidelines</span></span>

- <span data-ttu-id="0ba52-112">Ta inte bort någon av huvud strukturerna.</span><span class="sxs-lookup"><span data-stu-id="0ba52-112">Do not remove any of the header structures.</span></span> <span data-ttu-id="0ba52-113">PlatyPS förväntar sig en speciell uppsättning huvuden.</span><span class="sxs-lookup"><span data-stu-id="0ba52-113">PlatyPS expects a specific set of headers.</span></span>
- <span data-ttu-id="0ba52-114">**Indatatypen och utmatnings** **typ** rubrikerna måste ha en typ.</span><span class="sxs-lookup"><span data-stu-id="0ba52-114">The **Input type** and **Output type** headers must have a type.</span></span> <span data-ttu-id="0ba52-115">Om cmdleten inte kräver inmatade värden eller returnerar ett värde använder du värdet `None`.</span><span class="sxs-lookup"><span data-stu-id="0ba52-115">If the cmdlet does not take input or return a value then use the value `None`.</span></span>
- <span data-ttu-id="0ba52-116">Block med inhägnade kod är endast tillåtna i avsnittet [exempel](#structuring-examples) .</span><span class="sxs-lookup"><span data-stu-id="0ba52-116">Fenced code blocks are only allowed in the [Examples](#structuring-examples) section.</span></span>
- <span data-ttu-id="0ba52-117">Infogad kod sträcker kan användas i alla stycken.</span><span class="sxs-lookup"><span data-stu-id="0ba52-117">Inline code spans can be used in any paragraph.</span></span>

## <a name="formatting-about_-files"></a><span data-ttu-id="0ba52-118">Formatera About_ filer</span><span class="sxs-lookup"><span data-stu-id="0ba52-118">Formatting About_ files</span></span>

<span data-ttu-id="0ba52-119">`About_*` filer bearbetas nu av [pandoc][], i stället för PlatyPS.</span><span class="sxs-lookup"><span data-stu-id="0ba52-119">`About_*` files are now processed by [Pandoc][], instead of PlatyPS.</span></span> <span data-ttu-id="0ba52-120">`About_*` filer formateras för bästa kompatibilitet i alla versioner av PowerShell och med publicerings verktygen.</span><span class="sxs-lookup"><span data-stu-id="0ba52-120">`About_*` files are formatted for the best compatibility across all versions of PowerShell and with the publishing tools.</span></span>

<span data-ttu-id="0ba52-121">Grundläggande rikt linjer för formatering:</span><span class="sxs-lookup"><span data-stu-id="0ba52-121">Basic formatting guidelines:</span></span>

- <span data-ttu-id="0ba52-122">Begränsa rader till 80 tecken</span><span class="sxs-lookup"><span data-stu-id="0ba52-122">Limit lines to 80 characters</span></span>
- <span data-ttu-id="0ba52-123">Kodblock och tabeller är begränsade till 76 tecken, eftersom pandoc indrag av fyra blank steg under konverteringen till oformaterad text</span><span class="sxs-lookup"><span data-stu-id="0ba52-123">Code blocks and tables are limited to 76 characters because Pandoc indents these by four spaces during conversion to plain text</span></span>
- <span data-ttu-id="0ba52-124">Tabeller måste rymmas inom 76 tecken</span><span class="sxs-lookup"><span data-stu-id="0ba52-124">Tables need to fit within 76 characters</span></span>
  - <span data-ttu-id="0ba52-125">Radbryt innehållet i celler manuellt över flera rader</span><span class="sxs-lookup"><span data-stu-id="0ba52-125">Manually wrap contents of cells across multiple lines</span></span>
  - <span data-ttu-id="0ba52-126">Använda inledande och avslutande `|` tecken på varje rad</span><span class="sxs-lookup"><span data-stu-id="0ba52-126">Use opening and closing `|` characters on each line</span></span>
  - <span data-ttu-id="0ba52-127">Se ett arbets exempel i [about_Comparison_Operators][about-example]</span><span class="sxs-lookup"><span data-stu-id="0ba52-127">See a working example in [about_Comparison_Operators][about-example]</span></span>
- <span data-ttu-id="0ba52-128">Använda pandoc specialtecken `\`,`$`och `<`</span><span class="sxs-lookup"><span data-stu-id="0ba52-128">Using Pandoc special characters `\`,`$`, and `<`</span></span>
  - <span data-ttu-id="0ba52-129">Inom ett sidhuvud – dessa tecken måste föregås av ett inledande `\` tecken eller omges av bakstreck (`` ` ``)</span><span class="sxs-lookup"><span data-stu-id="0ba52-129">Within a header - these characters must be escaped using a leading `\` character or enclosed in backticks (`` ` ``)</span></span>
  - <span data-ttu-id="0ba52-130">I ett stycke ska de här tecknen placeras i kod intervall.</span><span class="sxs-lookup"><span data-stu-id="0ba52-130">Within a paragraph, these characters should be put into code spans.</span></span> <span data-ttu-id="0ba52-131">Exempel:</span><span class="sxs-lookup"><span data-stu-id="0ba52-131">For example:</span></span>

    ~~~markdown
    ### The purpose of the \$foo variable

    The `$foo` variable is used to store ...
    ~~~

## <a name="structuring-examples"></a><span data-ttu-id="0ba52-132">Strukturerings exempel</span><span class="sxs-lookup"><span data-stu-id="0ba52-132">Structuring examples</span></span>

<span data-ttu-id="0ba52-133">I PlatyPS-schemat är **exempel** rubriken en H2-rubrik och varje exempel är ett H3-huvud.</span><span class="sxs-lookup"><span data-stu-id="0ba52-133">In the PlatyPS schema, the **EXAMPLES** header is an H2 header and each example is an H3 header.</span></span>

<span data-ttu-id="0ba52-134">I ett exempel tillåter schemat inte att kodblock separeras med stycken.</span><span class="sxs-lookup"><span data-stu-id="0ba52-134">Within an example, the schema does not allow code blocks to be separated by paragraphs.</span></span> <span data-ttu-id="0ba52-135">Det schema som stöds är:</span><span class="sxs-lookup"><span data-stu-id="0ba52-135">The supported schema is:</span></span>

```
### Example #X title

0 or more paragraphs
1 or more code blocks
0 or more paragraphs.
```

<span data-ttu-id="0ba52-136">Numrera varje exempel och Lägg till en kort rubrik.</span><span class="sxs-lookup"><span data-stu-id="0ba52-136">Number each example and add a brief title.</span></span>

<span data-ttu-id="0ba52-137">Exempel:</span><span class="sxs-lookup"><span data-stu-id="0ba52-137">For example:</span></span>

### <a name="example-1-get-cmdlets-functions-and-aliases"></a><span data-ttu-id="0ba52-138">Exempel 1: Hämta cmdlets, Functions och alias</span><span class="sxs-lookup"><span data-stu-id="0ba52-138">Example 1: Get cmdlets, functions, and aliases</span></span>

<span data-ttu-id="0ba52-139">Det här kommandot hämtar PowerShell-cmdletar, funktioner och alias som är installerade på datorn.</span><span class="sxs-lookup"><span data-stu-id="0ba52-139">This command gets the PowerShell cmdlets, functions, and aliases that are installed on the computer.</span></span>

```powershell
Get-Command
```

### <a name="example-2-get-commands-in-the-current-session"></a><span data-ttu-id="0ba52-140">Exempel 2: Hämta kommandon i den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="0ba52-140">Example 2: Get commands in the current session</span></span>

```powershell
Get-Command -ListImported
```

## <a name="next-steps"></a><span data-ttu-id="0ba52-141">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="0ba52-141">Next steps</span></span>

[<span data-ttu-id="0ba52-142">Redaktionell check lista</span><span class="sxs-lookup"><span data-stu-id="0ba52-142">Editorial checklist</span></span>](editorial-checklist.md)

<!-- link references -->
[PlatyPS]: https://github.com/powershell/platyps
[platyPS.schema.md]: https://github.com/PowerShell/platyPS/blob/master/platyPS.schema.md
[issue1806]: https://github.com/MicrosoftDocs/PowerShell-Docs/issues/1806
[about-example]: /PowerShell/module/Microsoft.PowerShell.Core/About/about_Comparison_Operators
[Pandoc]: https://pandoc.org
