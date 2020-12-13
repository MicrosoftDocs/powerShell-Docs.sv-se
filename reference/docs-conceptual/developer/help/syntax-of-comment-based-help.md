---
ms.date: 09/12/2016
ms.topic: reference
title: Syntax för kommentarsbaserad hjälp
description: Syntax för kommentarsbaserad hjälp
ms.openlocfilehash: 3866f25b40fc970e8d219af6f423b7a25f5b875c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659509"
---
# <a name="syntax-of-comment-based-help"></a><span data-ttu-id="a990c-103">Syntax för kommentarsbaserad hjälp</span><span class="sxs-lookup"><span data-stu-id="a990c-103">Syntax of Comment-Based Help</span></span>

<span data-ttu-id="a990c-104">I det här avsnittet beskrivs syntaxen för en kommenterings-baserad hjälp.</span><span class="sxs-lookup"><span data-stu-id="a990c-104">This section describes the syntax of comment-based help.</span></span>

## <a name="syntax-diagram"></a><span data-ttu-id="a990c-105">Syntax-diagram</span><span class="sxs-lookup"><span data-stu-id="a990c-105">Syntax Diagram</span></span>

 <span data-ttu-id="a990c-106">Syntaxen för kommenterings-baserad hjälp är följande:</span><span class="sxs-lookup"><span data-stu-id="a990c-106">The syntax for comment-based Help is as follows:</span></span>

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a><span data-ttu-id="a990c-107">Beskrivning av syntax</span><span class="sxs-lookup"><span data-stu-id="a990c-107">Syntax Description</span></span>

 <span data-ttu-id="a990c-108">Kommenterad hjälp skrivs som en rad kommentarer.</span><span class="sxs-lookup"><span data-stu-id="a990c-108">Comment-based Help is written as a series of comments.</span></span> <span data-ttu-id="a990c-109">Du kan skriva en kommentars symbol ( `#` ) före varje rad med kommentarer, eller så kan du använda- `<#` och- `#>` symbolerna för att skapa ett kommentar block.</span><span class="sxs-lookup"><span data-stu-id="a990c-109">You can type a comment symbol (`#`) before each line of comments, or you can use the `<#` and `#>` symbols to create a comment block.</span></span> <span data-ttu-id="a990c-110">Alla rader i kommentars blocket tolkas som kommentarer.</span><span class="sxs-lookup"><span data-stu-id="a990c-110">All the lines within the comment block are interpreted as comments.</span></span>

 <span data-ttu-id="a990c-111">Varje del av den kommenterade hjälpen definieras av ett nyckelord och varje nyckelord föregås av en punkt ( `.` ).</span><span class="sxs-lookup"><span data-stu-id="a990c-111">Each section of comment-based Help is defined by a keyword and each keyword is preceded by a dot (`.`).</span></span> <span data-ttu-id="a990c-112">Nyckelorden kan visas i vilken ordning som helst.</span><span class="sxs-lookup"><span data-stu-id="a990c-112">The keywords can appear in any order.</span></span> <span data-ttu-id="a990c-113">Nyckelords namnen är inte Skift läges känsliga.</span><span class="sxs-lookup"><span data-stu-id="a990c-113">The keyword names are not case-sensitive.</span></span>

 <span data-ttu-id="a990c-114">Ett kommentar block måste innehålla minst ett hjälp nyckelord.</span><span class="sxs-lookup"><span data-stu-id="a990c-114">A comment block must contain at least one help keyword.</span></span> <span data-ttu-id="a990c-115">Några av nyckelorden, till **exempel**, kan visas många gånger i samma kommentars block.</span><span class="sxs-lookup"><span data-stu-id="a990c-115">Some of the keywords, such as **EXAMPLE**, can appear many times in the same comment block.</span></span> <span data-ttu-id="a990c-116">Hjälp innehållet för varje nyckelord börjar på raden efter nyckelordet och kan omfatta flera rader.</span><span class="sxs-lookup"><span data-stu-id="a990c-116">The Help content for each keyword begins on the line after the keyword and can span multiple lines.</span></span>

 <span data-ttu-id="a990c-117">Alla rader i ett kommenterat hjälp avsnitt måste vara sammanhängande.</span><span class="sxs-lookup"><span data-stu-id="a990c-117">All of the lines in a comment-based Help topic must be contiguous.</span></span> <span data-ttu-id="a990c-118">Om ett kommenterat hjälp avsnitt följer en kommentar som inte är en del av hjälp avsnittet, måste det finnas minst en tom rad mellan den sista raden för icke-hjälp-kommentarer och början av den kommenterade hjälpen.</span><span class="sxs-lookup"><span data-stu-id="a990c-118">If a comment-based Help topic follows a comment that is not part of the Help topic, there must be at least one blank line between the last non-Help comment line and the beginning of the comment-based Help.</span></span>

 <span data-ttu-id="a990c-119">Till exempel innehåller följande kommenterings-baserade hjälp avsnitt. Nyckelordet Description och dess värde, som är en beskrivning av en funktion eller ett skript.</span><span class="sxs-lookup"><span data-stu-id="a990c-119">For example, the following comment-based help topic contains the .Description keyword and its value, which is a description of a function or script.</span></span>

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```
