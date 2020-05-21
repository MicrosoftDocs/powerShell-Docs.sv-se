---
title: Placera kommenterings-baserad hjälp i functions | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ec7159e-e4e9-4b21-95df-94244432f679
caps.latest.revision: 5
ms.openlocfilehash: 898225a582c7ed25f746dec7f84012db1ae60b98
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557080"
---
# <a name="placing-comment-based-help-in-functions"></a><span data-ttu-id="db697-102">Lägga till kommentarsbaserad hjälp i funktioner</span><span class="sxs-lookup"><span data-stu-id="db697-102">Placing Comment-Based Help in Functions</span></span>

<span data-ttu-id="db697-103">I det här avsnittet beskrivs var du kan placera den kommenterade hjälpen för en funktion så att `Get-Help` cmdleten associerar det kommenterade hjälp avsnittet med rätt funktion.</span><span class="sxs-lookup"><span data-stu-id="db697-103">This topic explains where to place comment-based help for a function so that the `Get-Help` cmdlet associates the comment-based help topic with the correct function.</span></span>

## <a name="where-to-place-comment-based-help-for-a-function"></a><span data-ttu-id="db697-104">Var du vill placera kommenterings hjälpen för en funktion</span><span class="sxs-lookup"><span data-stu-id="db697-104">Where to Place Comment-Based Help for a Function</span></span>

- <span data-ttu-id="db697-105">I början av funktions texten.</span><span class="sxs-lookup"><span data-stu-id="db697-105">At the beginning of the function body.</span></span>

- <span data-ttu-id="db697-106">I slutet av funktions texten.</span><span class="sxs-lookup"><span data-stu-id="db697-106">At the end of the function body.</span></span>

- <span data-ttu-id="db697-107">Före `Function` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="db697-107">Before the `Function` keyword.</span></span> <span data-ttu-id="db697-108">När funktionen finns i en skript-eller skriptbaserad modul får det inte finnas mer än en tom rad mellan den sista raden i den kommenterade hjälpen och `Function` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="db697-108">When the function is in a script or script module, there cannot be more than one blank line between the last line of the comment-based help and the `Function` keyword.</span></span> <span data-ttu-id="db697-109">Annars `Get-Help` associeras hjälpen med skriptet, inte med funktionen.</span><span class="sxs-lookup"><span data-stu-id="db697-109">Otherwise, `Get-Help` associates the help with the script, not with the function.</span></span>

## <a name="examples-of-help-placement-in-a-function"></a><span data-ttu-id="db697-110">Exempel på hur hjälp placeras i en funktion</span><span class="sxs-lookup"><span data-stu-id="db697-110">Examples of Help Placement in a Function</span></span>

 <span data-ttu-id="db697-111">I följande exempel visas var och en av de tre placerings alternativen för en kommenterings-baserad hjälp för en funktion.</span><span class="sxs-lookup"><span data-stu-id="db697-111">The following examples show each of the three placement options for comment-based help for a function.</span></span>

### <a name="help-at-the-beginning-of-a-function-body"></a><span data-ttu-id="db697-112">Hjälp i början av en funktions text</span><span class="sxs-lookup"><span data-stu-id="db697-112">Help at the Beginning of a Function Body</span></span>

 <span data-ttu-id="db697-113">I följande exempel visas en kommentar baserad i början av en funktions text.</span><span class="sxs-lookup"><span data-stu-id="db697-113">The following example shows comment-based at the beginning of a function body.</span></span>

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

### <a name="help-at-the-end-of-a-function-body"></a><span data-ttu-id="db697-114">Hjälp i slutet av en funktions text</span><span class="sxs-lookup"><span data-stu-id="db697-114">Help at the End of a Function Body</span></span>

 <span data-ttu-id="db697-115">I följande exempel visas en kommentar baserad i slutet av en funktions text.</span><span class="sxs-lookup"><span data-stu-id="db697-115">The following example shows comment-based at the end of a function body.</span></span>

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

### <a name="help-before-the-function-keyword"></a><span data-ttu-id="db697-116">Hjälp innan nyckelordet Function</span><span class="sxs-lookup"><span data-stu-id="db697-116">Help Before the Function Keyword</span></span>

 <span data-ttu-id="db697-117">I följande exempel visas en kommentar baserad på raden före nyckelordet function.</span><span class="sxs-lookup"><span data-stu-id="db697-117">The following examples shows comment-based on the line before the function keyword.</span></span>

```powershell

<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}

```
