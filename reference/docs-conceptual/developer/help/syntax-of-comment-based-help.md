---
title: Syntax för kommenterings-baserad hjälp | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8adc997-1a71-48e9-9383-513ef13da7cf
caps.latest.revision: 4
ms.openlocfilehash: 584e5923008e8369a83c699478844f0e0c295adc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72357836"
---
# <a name="syntax-of-comment-based-help"></a><span data-ttu-id="4da7c-102">Syntax för kommentarsbaserad hjälp</span><span class="sxs-lookup"><span data-stu-id="4da7c-102">Syntax of Comment-Based Help</span></span>

<span data-ttu-id="4da7c-103">I det här avsnittet beskrivs syntaxen för en kommenterings-baserad hjälp.</span><span class="sxs-lookup"><span data-stu-id="4da7c-103">This section describes the syntax of comment-based help.</span></span>

## <a name="syntax-diagram"></a><span data-ttu-id="4da7c-104">Syntax-diagram</span><span class="sxs-lookup"><span data-stu-id="4da7c-104">Syntax Diagram</span></span>

 <span data-ttu-id="4da7c-105">Syntaxen för kommenterings-baserad hjälp är följande:</span><span class="sxs-lookup"><span data-stu-id="4da7c-105">The syntax for comment-based Help is as follows:</span></span>

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a><span data-ttu-id="4da7c-106">Beskrivning av syntax</span><span class="sxs-lookup"><span data-stu-id="4da7c-106">Syntax Description</span></span>

 <span data-ttu-id="4da7c-107">Kommenterad hjälp skrivs som en rad kommentarer.</span><span class="sxs-lookup"><span data-stu-id="4da7c-107">Comment-based Help is written as a series of comments.</span></span> <span data-ttu-id="4da7c-108">Du kan skriva en kommentars symbol (#) före varje rad med kommentarer, eller så kan du använda symbolerna "\<#" och "# >" för att skapa ett kommentar block.</span><span class="sxs-lookup"><span data-stu-id="4da7c-108">You can type a comment symbol (#) before each line of comments, or you can use the "\<#" and "#>" symbols to create a comment block.</span></span> <span data-ttu-id="4da7c-109">Alla rader i kommentars blocket tolkas som kommentarer.</span><span class="sxs-lookup"><span data-stu-id="4da7c-109">All the lines within the comment block are interpreted as comments.</span></span>

 <span data-ttu-id="4da7c-110">Varje del av den kommenterade hjälpen definieras av ett nyckelord och varje nyckelord föregås av en punkt (.).</span><span class="sxs-lookup"><span data-stu-id="4da7c-110">Each section of comment-based Help is defined by a keyword and each keyword is preceded by a dot (.).</span></span> <span data-ttu-id="4da7c-111">Nyckelorden kan visas i vilken ordning som helst.</span><span class="sxs-lookup"><span data-stu-id="4da7c-111">The keywords can appear in any order.</span></span> <span data-ttu-id="4da7c-112">Nyckelords namnen är inte Skift läges känsliga.</span><span class="sxs-lookup"><span data-stu-id="4da7c-112">The keyword names are not case-sensitive.</span></span>

 <span data-ttu-id="4da7c-113">Ett kommentar block måste innehålla minst ett hjälp nyckelord.</span><span class="sxs-lookup"><span data-stu-id="4da7c-113">A comment block must contain at least one help keyword.</span></span> <span data-ttu-id="4da7c-114">Några av nyckelorden, till exempel, kan visas många gånger i samma kommentars block.</span><span class="sxs-lookup"><span data-stu-id="4da7c-114">Some of the keywords, such as EXAMPLE, can appear many times in the same comment block.</span></span> <span data-ttu-id="4da7c-115">Hjälp innehållet för varje nyckelord börjar på raden efter nyckelordet och kan omfatta flera rader.</span><span class="sxs-lookup"><span data-stu-id="4da7c-115">The Help content for each keyword begins on the line after the keyword and can span multiple lines.</span></span>

 <span data-ttu-id="4da7c-116">Alla rader i ett kommenterat hjälp avsnitt måste vara sammanhängande.</span><span class="sxs-lookup"><span data-stu-id="4da7c-116">All of the lines in a comment-based Help topic must be contiguous.</span></span> <span data-ttu-id="4da7c-117">Om ett kommenterat hjälp avsnitt följer en kommentar som inte är en del av hjälp avsnittet, måste det finnas minst en tom rad mellan den sista raden för icke-hjälp-kommentarer och början av den kommenterade hjälpen.</span><span class="sxs-lookup"><span data-stu-id="4da7c-117">If a comment-based Help topic follows a comment that is not part of the Help topic, there must be at least one blank line between the last non-Help comment line and the beginning of the comment-based Help.</span></span>

 <span data-ttu-id="4da7c-118">Till exempel innehåller följande kommenterings-baserade hjälp avsnitt. Nyckelordet Description och dess värde, som är en beskrivning av en funktion eller ett skript.</span><span class="sxs-lookup"><span data-stu-id="4da7c-118">For example, the following comment-based help topic contains the .Description keyword and its value, which is a description of a function or script.</span></span>

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```