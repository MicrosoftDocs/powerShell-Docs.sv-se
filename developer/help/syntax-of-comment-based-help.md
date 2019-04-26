---
title: Syntaxen för Kommentarbaserad hjälp | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8adc997-1a71-48e9-9383-513ef13da7cf
caps.latest.revision: 4
ms.openlocfilehash: 584e5923008e8369a83c699478844f0e0c295adc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083220"
---
# <a name="syntax-of-comment-based-help"></a><span data-ttu-id="07f75-102">Syntax för kommentarsbaserad hjälp</span><span class="sxs-lookup"><span data-stu-id="07f75-102">Syntax of Comment-Based Help</span></span>

<span data-ttu-id="07f75-103">Det här avsnittet beskrivs syntaxen för kommentarbaserad hjälp.</span><span class="sxs-lookup"><span data-stu-id="07f75-103">This section describes the syntax of comment-based help.</span></span>

## <a name="syntax-diagram"></a><span data-ttu-id="07f75-104">Syntaxdiagrammet</span><span class="sxs-lookup"><span data-stu-id="07f75-104">Syntax Diagram</span></span>

 <span data-ttu-id="07f75-105">Syntaxen för kommentarbaserad hjälp är följande:</span><span class="sxs-lookup"><span data-stu-id="07f75-105">The syntax for comment-based Help is as follows:</span></span>

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a><span data-ttu-id="07f75-106">Syntax beskrivning</span><span class="sxs-lookup"><span data-stu-id="07f75-106">Syntax Description</span></span>

 <span data-ttu-id="07f75-107">Kommentarbaserad hjälp skrivs som en serie med kommentarer.</span><span class="sxs-lookup"><span data-stu-id="07f75-107">Comment-based Help is written as a series of comments.</span></span> <span data-ttu-id="07f75-108">Du kan skriva en kommentarsymbolen (#) före varje rad med kommentarer eller du kan använda den ”\<#” och ”#>” symboler för att skapa en kommentarblocket.</span><span class="sxs-lookup"><span data-stu-id="07f75-108">You can type a comment symbol (#) before each line of comments, or you can use the "\<#" and "#>" symbols to create a comment block.</span></span> <span data-ttu-id="07f75-109">Alla rader inom kommentarblocket tolkas som kommentarer.</span><span class="sxs-lookup"><span data-stu-id="07f75-109">All the lines within the comment block are interpreted as comments.</span></span>

 <span data-ttu-id="07f75-110">Varje avsnitt på kommentarbaserad hjälp definieras av ett nyckelord och varje nyckelord föregås av en punkt (.).</span><span class="sxs-lookup"><span data-stu-id="07f75-110">Each section of comment-based Help is defined by a keyword and each keyword is preceded by a dot (.).</span></span> <span data-ttu-id="07f75-111">Nyckelord kan visas i valfri ordning.</span><span class="sxs-lookup"><span data-stu-id="07f75-111">The keywords can appear in any order.</span></span> <span data-ttu-id="07f75-112">Nyckelordet namnen är inte skiftlägeskänsliga.</span><span class="sxs-lookup"><span data-stu-id="07f75-112">The keyword names are not case-sensitive.</span></span>

 <span data-ttu-id="07f75-113">En kommentarblocket måste innehålla minst ett nyckelord för hjälp.</span><span class="sxs-lookup"><span data-stu-id="07f75-113">A comment block must contain at least one help keyword.</span></span> <span data-ttu-id="07f75-114">Några av nyckelord som exempel, kan visas flera gånger i samma kommentarblocket.</span><span class="sxs-lookup"><span data-stu-id="07f75-114">Some of the keywords, such as EXAMPLE, can appear many times in the same comment block.</span></span> <span data-ttu-id="07f75-115">Hjälpinnehåll för varje nyckelord börjar på raden efter nyckelordet och kan sträcka sig över flera rader.</span><span class="sxs-lookup"><span data-stu-id="07f75-115">The Help content for each keyword begins on the line after the keyword and can span multiple lines.</span></span>

 <span data-ttu-id="07f75-116">Alla rader i ett kommentarbaserad hjälpavsnitt måste vara sammanhängande.</span><span class="sxs-lookup"><span data-stu-id="07f75-116">All of the lines in a comment-based Help topic must be contiguous.</span></span> <span data-ttu-id="07f75-117">Om ett kommentarbaserad hjälpavsnitt följer en kommentar som inte ingår i hjälpavsnittet, måste det finnas minst en tom rad mellan den sista kommentarraden i icke-Help och början av kommentarbaserad hjälp.</span><span class="sxs-lookup"><span data-stu-id="07f75-117">If a comment-based Help topic follows a comment that is not part of the Help topic, there must be at least one blank line between the last non-Help comment line and the beginning of the comment-based Help.</span></span>

 <span data-ttu-id="07f75-118">I följande kommentarbaserad hjälpavsnittet innehåller exempelvis den. Beskrivning av nyckelord och dess värde, som är en beskrivning av en funktion eller ett skript.</span><span class="sxs-lookup"><span data-stu-id="07f75-118">For example, the following comment-based help topic contains the .Description keyword and its value, which is a description of a function or script.</span></span>

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```