---
description: Visar en lista med reserverade ord som inte kan användas som identifierare eftersom de har en särskild betydelse i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 07/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_reserved_words?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Reserved_Words
ms.openlocfilehash: edf37ce528c8fd98ce3ca7741a1a6c9e0443173a
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272474"
---
# <a name="about-reserved-words"></a><span data-ttu-id="33a42-104">Om reserverade ord</span><span class="sxs-lookup"><span data-stu-id="33a42-104">About Reserved Words</span></span>

## <a name="short-description"></a><span data-ttu-id="33a42-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="33a42-105">SHORT DESCRIPTION</span></span>
<span data-ttu-id="33a42-106">Visar en lista med reserverade ord som inte kan användas som identifierare eftersom de har en särskild betydelse i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="33a42-106">Lists the reserved words that cannot be used as identifiers because they have a special meaning in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="33a42-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="33a42-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="33a42-108">Det finns vissa ord som har en särskild betydelse i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="33a42-108">There are certain words that have special meaning in PowerShell.</span></span> <span data-ttu-id="33a42-109">När dessa ord visas utan citat tecken försöker PowerShell tillämpa sin särskilda innebörd i stället för att behandla dem som tecken strängar.</span><span class="sxs-lookup"><span data-stu-id="33a42-109">When these words appear without quotation marks, PowerShell attempts to apply their special meaning rather than treating them as character strings.</span></span> <span data-ttu-id="33a42-110">Om du vill använda dessa ord som parameter argument i ett kommando eller skript utan att anropa deras särskilda innebörd, omger du reserverade ord inom citat tecken.</span><span class="sxs-lookup"><span data-stu-id="33a42-110">To use these words as parameter arguments in a command or script without invoking their special meaning, enclose the reserved words in quotation marks.</span></span>

<span data-ttu-id="33a42-111">Följande är reserverade ord i PowerShell:</span><span class="sxs-lookup"><span data-stu-id="33a42-111">The following are the reserved words in PowerShell:</span></span>

```
assembly         exit            process
base             filter          public
begin            finally         return
break            for             sequence
catch            foreach         static
class            from (*)        switch
command          function        throw
configuration    hidden          trap
continue         if              try
data             in              type
define (*)       inlinescript    until
do               interface       using
dynamicparam     module          var (*)
else             namespace       while
elseif           parallel        workflow
end              param
enum             private

(*) These keywords are reserved for future use.
```

<span data-ttu-id="33a42-112">Flera språk nyckelord, inklusive `Foreach` , `If` , `For` och `While` , har sina egna hjälp artiklar.</span><span class="sxs-lookup"><span data-stu-id="33a42-112">Several language keywords, including `Foreach`, `If`, `For`, and `While`, have their own help articles.</span></span> <span data-ttu-id="33a42-113">Om du vill visa dem skriver du `Get-Help about_` och lägger till nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="33a42-113">To view them, type `Get-Help about_` and add the keyword.</span></span> <span data-ttu-id="33a42-114">Om du till exempel vill hämta information om `Foreach` instruktionen skriver du:</span><span class="sxs-lookup"><span data-stu-id="33a42-114">For example, to get information about the `Foreach` statement, type:</span></span>

```powershell
Get-Help about_ForEach
```

<span data-ttu-id="33a42-115">Om du vill ha mer information om `Filter` instruktionen eller `Return` syntaxen för uttrycket skriver du:</span><span class="sxs-lookup"><span data-stu-id="33a42-115">For information about the `Filter` statement or the `Return` statement syntax, type:</span></span>

```powershell
Get-Help about_Functions
```

<span data-ttu-id="33a42-116">Om du vill ha information om andra reserverade ord skriver du:</span><span class="sxs-lookup"><span data-stu-id="33a42-116">For information about other reserved words, type:</span></span>

```powershell
Get-Help <Reserved_Word>
```

> [!NOTE]
> <span data-ttu-id="33a42-117">Alla reserverade ord har inte en egen hjälp artikel.</span><span class="sxs-lookup"><span data-stu-id="33a42-117">Not every reserved word has its own help article.</span></span> <span data-ttu-id="33a42-118">Om inte `Get-Help` returnerar en artikel kan du söka efter artiklar som talar om det reserverade ordet med hjälp av följande kommando:</span><span class="sxs-lookup"><span data-stu-id="33a42-118">If `Get-Help` does not return an article, you can search for articles that talk about the reserved word using the following command:</span></span>
>
> ```powershell
> Get-Help <Reserved_Word> -Category:HelpFile
> ```

## <a name="see-also"></a><span data-ttu-id="33a42-119">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="33a42-119">SEE ALSO</span></span>

- [<span data-ttu-id="33a42-120">about_Command_Syntax</span><span class="sxs-lookup"><span data-stu-id="33a42-120">about_Command_Syntax</span></span>](about_Command_Syntax.md)
- [<span data-ttu-id="33a42-121">about_Language_Keywords</span><span class="sxs-lookup"><span data-stu-id="33a42-121">about_Language_Keywords</span></span>](about_Language_Keywords.md)
- [<span data-ttu-id="33a42-122">about_Parsing</span><span class="sxs-lookup"><span data-stu-id="33a42-122">about_Parsing</span></span>](about_Parsing.md)
- [<span data-ttu-id="33a42-123">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="33a42-123">about_Quoting_Rules</span></span>](about_Quoting_Rules.md)
- [<span data-ttu-id="33a42-124">about_Script_Blocks</span><span class="sxs-lookup"><span data-stu-id="33a42-124">about_Script_Blocks</span></span>](about_Script_Blocks.md)
- [<span data-ttu-id="33a42-125">about_Special_Characters</span><span class="sxs-lookup"><span data-stu-id="33a42-125">about_Special_Characters</span></span>](about_Special_Characters.md)
