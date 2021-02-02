---
description: Kör en instruktions lista en eller flera gånger, beroende på ett while eller ett villkor.
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_do?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Do
ms.openlocfilehash: 412a13669e86df5804dd74d75fcb5b4389192c79
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710633"
---
# <a name="about-do"></a><span data-ttu-id="cc3fa-103">Om gör</span><span class="sxs-lookup"><span data-stu-id="cc3fa-103">About Do</span></span>

## <a name="short-description"></a><span data-ttu-id="cc3fa-104">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="cc3fa-104">SHORT DESCRIPTION</span></span>
<span data-ttu-id="cc3fa-105">Kör en instruktions lista en eller flera gånger, beroende på ett while eller ett villkor.</span><span class="sxs-lookup"><span data-stu-id="cc3fa-105">Runs a statement list one or more times, subject to a While or Until condition.</span></span>

## <a name="long-description"></a><span data-ttu-id="cc3fa-106">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="cc3fa-106">LONG DESCRIPTION</span></span>

<span data-ttu-id="cc3fa-107">Nyckelordet Keyword fungerar med nyckelordet while eller till nyckelordet until för att köra instruktionerna i ett-skript block, beroende på ett villkor.</span><span class="sxs-lookup"><span data-stu-id="cc3fa-107">The Do keyword works with the While keyword or the Until keyword to run the statements in a script block, subject to a condition.</span></span> <span data-ttu-id="cc3fa-108">Till skillnad från den relaterade while-loopen körs skript blocket i en loop-slinga alltid minst en gång.</span><span class="sxs-lookup"><span data-stu-id="cc3fa-108">Unlike the related While loop, the script block in a Do loop always runs at least once.</span></span>

<span data-ttu-id="cc3fa-109">En while-loop är en mängd av while **-** slingan.</span><span class="sxs-lookup"><span data-stu-id="cc3fa-109">A **Do-While** loop is a variety of the While loop.</span></span> <span data-ttu-id="cc3fa-110">I en **while-** loop utvärderas villkoret när skript blocket har körts.</span><span class="sxs-lookup"><span data-stu-id="cc3fa-110">In a **Do-While** loop, the condition is evaluated after the script block has run.</span></span> <span data-ttu-id="cc3fa-111">Som i en while-slinga upprepas skript blocket så länge villkoret utvärderas till sant.</span><span class="sxs-lookup"><span data-stu-id="cc3fa-111">As in a While loop, the script block is repeated as long as the condition evaluates to true.</span></span>

<span data-ttu-id="cc3fa-112">Som en **while-** slinga körs en upprepa **-tills-** loop alltid minst en gång innan villkoret utvärderas.</span><span class="sxs-lookup"><span data-stu-id="cc3fa-112">Like a **Do-While** loop, a **Do-Until** loop always runs at least once before the condition is evaluated.</span></span> <span data-ttu-id="cc3fa-113">Skript blocket körs dock bara när villkoret är falskt.</span><span class="sxs-lookup"><span data-stu-id="cc3fa-113">However, the script block runs only while the condition is false.</span></span>

<span data-ttu-id="cc3fa-114">Nyckelorden *Continue* och *Break* Flow kan användas i en **while-** loop eller i en sling **-until-** slinga.</span><span class="sxs-lookup"><span data-stu-id="cc3fa-114">The *Continue* and *Break* flow control keywords can be used in a **Do-While** loop or in a **Do-Until** loop.</span></span>

### <a name="syntax"></a><span data-ttu-id="cc3fa-115">Syntax</span><span class="sxs-lookup"><span data-stu-id="cc3fa-115">Syntax</span></span>

<span data-ttu-id="cc3fa-116">Nedan visas syntaxen för instruktionen **while** .</span><span class="sxs-lookup"><span data-stu-id="cc3fa-116">The following shows the syntax of the **Do-While** statement:</span></span>

```powershell
do {<statement list>} while (<condition>)
```

<span data-ttu-id="cc3fa-117">Nedan visas syntaxen för instruktionen **-until** :</span><span class="sxs-lookup"><span data-stu-id="cc3fa-117">The following shows the syntax of the **Do-Until** statement:</span></span>

```powershell
do {<statement list>} until (<condition>)
```

<span data-ttu-id="cc3fa-118">Instruktions listan innehåller en eller flera instruktioner som körs varje gången loopen anges eller upprepas.</span><span class="sxs-lookup"><span data-stu-id="cc3fa-118">The statement list contains one or more statements that run each time the loop is entered or repeated.</span></span>

<span data-ttu-id="cc3fa-119">Villkors delen i instruktionen matchar värdet sant eller falskt.</span><span class="sxs-lookup"><span data-stu-id="cc3fa-119">The condition portion of the statement resolves to true or false.</span></span>

### <a name="example"></a><span data-ttu-id="cc3fa-120">Exempel</span><span class="sxs-lookup"><span data-stu-id="cc3fa-120">Example</span></span>

<span data-ttu-id="cc3fa-121">Följande exempel på en Statement-instruktion räknar objekten i en matris tills den når ett objekt med värdet 0.</span><span class="sxs-lookup"><span data-stu-id="cc3fa-121">The following example of a Do statement counts the items in an array until it reaches an item with a value of 0.</span></span>

```powershell
C:\PS> $x = 1,2,78,0
C:\PS> do { $count++; $a++; } while ($x[$a] -ne 0)
C:\PS> $count
3
```

<span data-ttu-id="cc3fa-122">I följande exempel används nyckelordet until.</span><span class="sxs-lookup"><span data-stu-id="cc3fa-122">The following example uses the Until keyword.</span></span> <span data-ttu-id="cc3fa-123">Observera att operatorn som inte är lika med ( `-ne` ) ersätts av operatorn lika med ( `-eq` ).</span><span class="sxs-lookup"><span data-stu-id="cc3fa-123">Notice that the not equal to operator (`-ne`) is replaced by the equal to operator (`-eq`).</span></span>

```powershell
C:\PS> $x = 1,2,78,0
C:\PS> do { $count++; $a++; } until ($x[$a] -eq 0)
C:\PS> $count
3
```

<span data-ttu-id="cc3fa-124">I följande exempel skrivs alla värden i en matris, vilket hoppar över värden som är mindre än noll.</span><span class="sxs-lookup"><span data-stu-id="cc3fa-124">The following example writes all the values of an array, skipping any value that is less than zero.</span></span>

```powershell
do {
  if ($x[$a] -lt 0) { continue }
  Write-Host $x[$a]
}
while (++$a -lt 10)
```

## <a name="see-also"></a><span data-ttu-id="cc3fa-125">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="cc3fa-125">SEE ALSO</span></span>

[<span data-ttu-id="cc3fa-126">about_While</span><span class="sxs-lookup"><span data-stu-id="cc3fa-126">about_While</span></span>](about_While.md)

[<span data-ttu-id="cc3fa-127">about_Operators</span><span class="sxs-lookup"><span data-stu-id="cc3fa-127">about_Operators</span></span>](about_Operators.md)

[<span data-ttu-id="cc3fa-128">about_Assignment_Operators</span><span class="sxs-lookup"><span data-stu-id="cc3fa-128">about_Assignment_Operators</span></span>](about_Assignment_Operators.md)

[<span data-ttu-id="cc3fa-129">about_Comparison_Operators</span><span class="sxs-lookup"><span data-stu-id="cc3fa-129">about_Comparison_Operators</span></span>](about_Comparison_Operators.md)

[<span data-ttu-id="cc3fa-130">about_Break</span><span class="sxs-lookup"><span data-stu-id="cc3fa-130">about_Break</span></span>](about_Break.md)

[<span data-ttu-id="cc3fa-131">about_Continue</span><span class="sxs-lookup"><span data-stu-id="cc3fa-131">about_Continue</span></span>](about_Continue.md)
