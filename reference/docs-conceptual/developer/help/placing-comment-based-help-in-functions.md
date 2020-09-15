---
title: Lägga till kommentarsbaserad hjälp i funktioner
ms.date: 09/12/2016
ms.openlocfilehash: c7a8f8db6c71fa2ef12aaa4df0f78815626ec8d6
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893211"
---
# <a name="placing-comment-based-help-in-functions"></a><span data-ttu-id="84166-102">Lägga till kommentarsbaserad hjälp i funktioner</span><span class="sxs-lookup"><span data-stu-id="84166-102">Placing Comment-Based Help in Functions</span></span>

<span data-ttu-id="84166-103">I det här avsnittet beskrivs var du kan placera den kommenterade hjälpen för en funktion så att `Get-Help` cmdleten associerar det kommenterade hjälp avsnittet med rätt funktion.</span><span class="sxs-lookup"><span data-stu-id="84166-103">This topic explains where to place comment-based help for a function so that the `Get-Help` cmdlet associates the comment-based help topic with the correct function.</span></span>

## <a name="where-to-place-comment-based-help-for-a-function"></a><span data-ttu-id="84166-104">Var du vill placera kommenterings hjälpen för en funktion</span><span class="sxs-lookup"><span data-stu-id="84166-104">Where to Place Comment-Based Help for a Function</span></span>

- <span data-ttu-id="84166-105">I början av funktions texten.</span><span class="sxs-lookup"><span data-stu-id="84166-105">At the beginning of the function body.</span></span>

- <span data-ttu-id="84166-106">I slutet av funktions texten.</span><span class="sxs-lookup"><span data-stu-id="84166-106">At the end of the function body.</span></span>

- <span data-ttu-id="84166-107">Före `Function` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="84166-107">Before the `Function` keyword.</span></span> <span data-ttu-id="84166-108">När funktionen finns i en skript-eller skriptbaserad modul får det inte finnas mer än en tom rad mellan den sista raden i den kommenterade hjälpen och `Function` nyckelordet.</span><span class="sxs-lookup"><span data-stu-id="84166-108">When the function is in a script or script module, there cannot be more than one blank line between the last line of the comment-based help and the `Function` keyword.</span></span> <span data-ttu-id="84166-109">Annars `Get-Help` associeras hjälpen med skriptet, inte med funktionen.</span><span class="sxs-lookup"><span data-stu-id="84166-109">Otherwise, `Get-Help` associates the help with the script, not with the function.</span></span>

## <a name="examples-of-help-placement-in-a-function"></a><span data-ttu-id="84166-110">Exempel på hur hjälp placeras i en funktion</span><span class="sxs-lookup"><span data-stu-id="84166-110">Examples of Help Placement in a Function</span></span>

<span data-ttu-id="84166-111">I följande exempel visas var och en av de tre placerings alternativen för en kommenterings-baserad hjälp för en funktion.</span><span class="sxs-lookup"><span data-stu-id="84166-111">The following examples show each of the three placement options for comment-based help for a function.</span></span>

### <a name="help-at-the-beginning-of-a-function-body"></a><span data-ttu-id="84166-112">Hjälp i början av en funktions text</span><span class="sxs-lookup"><span data-stu-id="84166-112">Help at the Beginning of a Function Body</span></span>

<span data-ttu-id="84166-113">I följande exempel visas en kommentar baserad i början av en funktions text.</span><span class="sxs-lookup"><span data-stu-id="84166-113">The following example shows comment-based at the beginning of a function body.</span></span>

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

### <a name="help-at-the-end-of-a-function-body"></a><span data-ttu-id="84166-114">Hjälp i slutet av en funktions text</span><span class="sxs-lookup"><span data-stu-id="84166-114">Help at the End of a Function Body</span></span>

 <span data-ttu-id="84166-115">I följande exempel visas en kommentar baserad i slutet av en funktions text.</span><span class="sxs-lookup"><span data-stu-id="84166-115">The following example shows comment-based at the end of a function body.</span></span>

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

### <a name="help-before-the-function-keyword"></a><span data-ttu-id="84166-116">Hjälp innan nyckelordet Function</span><span class="sxs-lookup"><span data-stu-id="84166-116">Help Before the Function Keyword</span></span>

 <span data-ttu-id="84166-117">I följande exempel visas en kommentar baserad på raden före nyckelordet function.</span><span class="sxs-lookup"><span data-stu-id="84166-117">The following examples shows comment-based on the line before the function keyword.</span></span>

```powershell
<#
    .Description
    The MyProcess function gets the Windows PowerShell process.
#>
function MyFunction { Get-Process powershell}
```
