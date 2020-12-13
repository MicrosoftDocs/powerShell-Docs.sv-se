---
ms.date: 09/12/2016
ms.topic: reference
title: Lägga till kommentarsbaserad hjälp i funktioner
description: Lägga till kommentarsbaserad hjälp i funktioner
ms.openlocfilehash: 3bd72f0c71d8f6ad54c43c99f044423c072fdeeb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92658213"
---
# <a name="placing-comment-based-help-in-functions"></a><span data-ttu-id="30b92-103">Lägga till kommentarsbaserad hjälp i funktioner</span><span class="sxs-lookup"><span data-stu-id="30b92-103">Placing Comment-Based Help in Functions</span></span>

<span data-ttu-id="30b92-104">I det här avsnittet beskrivs var du kan placera den kommenterade hjälpen för en funktion så att `Get-Help` cmdleten associerar det kommenterade hjälp avsnittet med rätt funktion.</span><span class="sxs-lookup"><span data-stu-id="30b92-104">This topic explains where to place comment-based help for a function so that the `Get-Help` cmdlet associates the comment-based help topic with the correct function.</span></span>

## <a name="where-to-place-comment-based-help-for-a-function"></a><span data-ttu-id="30b92-105">Var du ska placera Comment-Based hjälp för en funktion</span><span class="sxs-lookup"><span data-stu-id="30b92-105">Where to Place Comment-Based Help for a Function</span></span>

- <span data-ttu-id="30b92-106">I början av funktions texten.</span><span class="sxs-lookup"><span data-stu-id="30b92-106">At the beginning of the function body.</span></span>

- <span data-ttu-id="30b92-107">I slutet av funktions texten.</span><span class="sxs-lookup"><span data-stu-id="30b92-107">At the end of the function body.</span></span>

- <span data-ttu-id="30b92-108">Före `Function` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="30b92-108">Before the `Function` keyword.</span></span> <span data-ttu-id="30b92-109">När funktionen finns i en skript-eller skriptbaserad modul får det inte finnas mer än en tom rad mellan den sista raden i den kommenterade hjälpen och `Function` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="30b92-109">When the function is in a script or script module, there cannot be more than one blank line between the last line of the comment-based help and the `Function` keyword.</span></span> <span data-ttu-id="30b92-110">Annars `Get-Help` associeras hjälpen med skriptet, inte med funktionen.</span><span class="sxs-lookup"><span data-stu-id="30b92-110">Otherwise, `Get-Help` associates the help with the script, not with the function.</span></span>

## <a name="examples-of-help-placement-in-a-function"></a><span data-ttu-id="30b92-111">Exempel på hur hjälp placeras i en funktion</span><span class="sxs-lookup"><span data-stu-id="30b92-111">Examples of Help Placement in a Function</span></span>

<span data-ttu-id="30b92-112">I följande exempel visas var och en av de tre placerings alternativen för en kommenterings-baserad hjälp för en funktion.</span><span class="sxs-lookup"><span data-stu-id="30b92-112">The following examples show each of the three placement options for comment-based help for a function.</span></span>

### <a name="help-at-the-beginning-of-a-function-body"></a><span data-ttu-id="30b92-113">Hjälp i början av en funktions text</span><span class="sxs-lookup"><span data-stu-id="30b92-113">Help at the Beginning of a Function Body</span></span>

<span data-ttu-id="30b92-114">I följande exempel visas en kommentar baserad i början av en funktions text.</span><span class="sxs-lookup"><span data-stu-id="30b92-114">The following example shows comment-based at the beginning of a function body.</span></span>

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

### <a name="help-at-the-end-of-a-function-body"></a><span data-ttu-id="30b92-115">Hjälp i slutet av en funktions text</span><span class="sxs-lookup"><span data-stu-id="30b92-115">Help at the End of a Function Body</span></span>

 <span data-ttu-id="30b92-116">I följande exempel visas en kommentar baserad i slutet av en funktions text.</span><span class="sxs-lookup"><span data-stu-id="30b92-116">The following example shows comment-based at the end of a function body.</span></span>

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

### <a name="help-before-the-function-keyword"></a><span data-ttu-id="30b92-117">Hjälp innan nyckelordet Function</span><span class="sxs-lookup"><span data-stu-id="30b92-117">Help Before the Function Keyword</span></span>

 <span data-ttu-id="30b92-118">I följande exempel visas en kommentar baserad på raden före nyckelordet function.</span><span class="sxs-lookup"><span data-stu-id="30b92-118">The following examples shows comment-based on the line before the function keyword.</span></span>

```powershell
<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}
```
