---
title: Placera Kommentarbaserad hjälp i Functions | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: a663bd69be7825b1685f64ff8d3068bdd8ca3265
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848176"
---
# <a name="placing-comment-based-help-in-functions"></a><span data-ttu-id="d8601-102">Lägga till kommentarsbaserad hjälp i funktioner</span><span class="sxs-lookup"><span data-stu-id="d8601-102">Placing Comment-Based Help in Functions</span></span>

<span data-ttu-id="d8601-103">Det här avsnittet förklarar var du ska placera kommentarbaserad hjälp för en funktion så att den `Get-Help` cmdlet associerar hjälpavsnitt kommentarbaserad med rätt funktion.</span><span class="sxs-lookup"><span data-stu-id="d8601-103">This topic explains where to place comment-based help for a function so that the `Get-Help` cmdlet associates the comment-based help topic with the correct function.</span></span>

## <a name="where-to-place-comment-based-help-for-a-function"></a><span data-ttu-id="d8601-104">Var man ska placera Kommentarbaserad hjälp för en funktion</span><span class="sxs-lookup"><span data-stu-id="d8601-104">Where to Place Comment-Based Help for a Function</span></span>

- <span data-ttu-id="d8601-105">I början av funktionen brödtext.</span><span class="sxs-lookup"><span data-stu-id="d8601-105">At the beginning of the function body.</span></span>

- <span data-ttu-id="d8601-106">I slutet av funktionen brödtext.</span><span class="sxs-lookup"><span data-stu-id="d8601-106">At the end of the function body.</span></span>

- <span data-ttu-id="d8601-107">Innan den `Function` nyckelord.</span><span class="sxs-lookup"><span data-stu-id="d8601-107">Before the `Function` keyword.</span></span> <span data-ttu-id="d8601-108">När funktionen är i ett skript eller en skriptmodul, det får inte finnas mer än en tom rad mellan den sista raden i kommentarbaserad hjälp och `Function` nyckelord.</span><span class="sxs-lookup"><span data-stu-id="d8601-108">When the function is in a script or script module, there cannot be more than one blank line between the last line of the comment-based help and the `Function` keyword.</span></span> <span data-ttu-id="d8601-109">I annat fall `Get-Help` associerar hjälp med skriptet, inte funktionen.</span><span class="sxs-lookup"><span data-stu-id="d8601-109">Otherwise, `Get-Help` associates the help with the script, not with the function.</span></span>

## <a name="examples-of-help-placement-in-a-function"></a><span data-ttu-id="d8601-110">Exempel på Hjälp placering i en funktion</span><span class="sxs-lookup"><span data-stu-id="d8601-110">Examples of Help Placement in a Function</span></span>

 <span data-ttu-id="d8601-111">I följande exempel visas var och en av de tre placeringsalternativ för kommentarbaserad hjälp för en funktion.</span><span class="sxs-lookup"><span data-stu-id="d8601-111">The following examples show each of the three placement options for comment-based help for a function.</span></span>

### <a name="help-at-the-beginning-of-a-function-body"></a><span data-ttu-id="d8601-112">Hjälp i början av brödtexten för en funktion</span><span class="sxs-lookup"><span data-stu-id="d8601-112">Help at the Beginning of a Function Body</span></span>

 <span data-ttu-id="d8601-113">I följande exempel visas kommentarbaserad i början av brödtexten för en funktion.</span><span class="sxs-lookup"><span data-stu-id="d8601-113">The following example shows comment-based at the beginning of a function body.</span></span>

```powershell

function MyProcess
{
    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>

    Get-Process powershell
}

```

### <a name="help-at-the-end-of-a-function-body"></a><span data-ttu-id="d8601-114">Hjälp i slutet av brödtexten för en funktion</span><span class="sxs-lookup"><span data-stu-id="d8601-114">Help at the End of a Function Body</span></span>

 <span data-ttu-id="d8601-115">I följande exempel visas kommentarbaserad i slutet av brödtexten för en funktion.</span><span class="sxs-lookup"><span data-stu-id="d8601-115">The following example shows comment-based at the end of a function body.</span></span>

```powershell

function MyFunction
{
    Get-Process powershell

    <#
       .Description
       The MyProcess function gets the Windows PowerShell process.
    #>
}

```

### <a name="help-before-the-function-keyword"></a><span data-ttu-id="d8601-116">Hjälpa innan nyckelordet Function</span><span class="sxs-lookup"><span data-stu-id="d8601-116">Help Before the Function Keyword</span></span>

 <span data-ttu-id="d8601-117">I följande exempel visar kommentarbaserad på rad innan nyckelordet function.</span><span class="sxs-lookup"><span data-stu-id="d8601-117">The following examples shows comment-based on the line before the function keyword.</span></span>

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```