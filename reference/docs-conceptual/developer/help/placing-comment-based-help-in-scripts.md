---
title: Placera kommenterad hjälp i skript | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49f8267c-d887-4d7d-b9b7-80dc624b1261
caps.latest.revision: 4
ms.openlocfilehash: d199c53a748ac57bb2a5f998b5056e39d3e80c0d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353251"
---
# <a name="placing-comment-based-help-in-scripts"></a><span data-ttu-id="0910c-102">Lägga till kommentarsbaserat hjälp i skript</span><span class="sxs-lookup"><span data-stu-id="0910c-102">Placing Comment-Based Help in Scripts</span></span>

<span data-ttu-id="0910c-103">I det här avsnittet beskrivs var du kan placera den kommenterade hjälpen för ett skript så att `Get-Help`-cmdleten associerar det kommenterande hjälp avsnittet med skript och inte med funktioner som kan finnas i skriptet.</span><span class="sxs-lookup"><span data-stu-id="0910c-103">This topic explains where to place comment-based help for a script so that the `Get-Help` cmdlet associates the comment-based help topic with scripts and not with any functions that might be in the script.</span></span>

## <a name="where-to-place-comment-based-help-for-a-script"></a><span data-ttu-id="0910c-104">Var du vill placera kommenterad hjälp för ett skript</span><span class="sxs-lookup"><span data-stu-id="0910c-104">Where to Place Comment-Based Help for a Script</span></span>

- <span data-ttu-id="0910c-105">I början av skript filen.</span><span class="sxs-lookup"><span data-stu-id="0910c-105">At the beginning of the script file.</span></span> <span data-ttu-id="0910c-106">Skript hjälpen kan bara föregås av kommentarer och tomma rader.</span><span class="sxs-lookup"><span data-stu-id="0910c-106">Script Help can be preceded in the script only by comments and blank lines.</span></span>

- <span data-ttu-id="0910c-107">I slutet av skript filen.</span><span class="sxs-lookup"><span data-stu-id="0910c-107">At the end of the script file.</span></span>

  <span data-ttu-id="0910c-108">Om det första objektet i skript texten (efter hjälpen) är en funktions deklaration måste det finnas minst två tomma rader mellan slutet av skript hjälpen och funktions deklarationen.</span><span class="sxs-lookup"><span data-stu-id="0910c-108">If the first item in the script body (after the Help) is a function declaration, there must be at least two blank lines between the end of the script Help and the function declaration.</span></span> <span data-ttu-id="0910c-109">Annars tolkas hjälpen som hjälp för funktionen, inte för att hjälpa till med skriptet.</span><span class="sxs-lookup"><span data-stu-id="0910c-109">Otherwise, the Help is interpreted as being Help for the function, not Help for the script.</span></span>

## <a name="examples-of-help-placement-in-a-script"></a><span data-ttu-id="0910c-110">Exempel på hur hjälp placeras i ett skript</span><span class="sxs-lookup"><span data-stu-id="0910c-110">Examples of Help Placement in a Script</span></span>

 <span data-ttu-id="0910c-111">I följande exempel visas var och en av placerings alternativen för den kommenterade hjälpen för ett skript.</span><span class="sxs-lookup"><span data-stu-id="0910c-111">The following examples show each of the placement options for comment-based help for a script.</span></span>

### <a name="help-at-the-beginning-of-a-script"></a><span data-ttu-id="0910c-112">Hjälp i början av ett skript</span><span class="sxs-lookup"><span data-stu-id="0910c-112">Help at the Beginning of a Script</span></span>

 <span data-ttu-id="0910c-113">I följande exempel visas en kommentar baserad i början av ett skript.</span><span class="sxs-lookup"><span data-stu-id="0910c-113">The following example shows comment-based at the beginning of a script.</span></span>

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a><span data-ttu-id="0910c-114">Hjälp i slutet av ett skript</span><span class="sxs-lookup"><span data-stu-id="0910c-114">Help at the End of a Script</span></span>

 <span data-ttu-id="0910c-115">I följande exempel visas en kommentar baserad i slutet av ett skript.</span><span class="sxs-lookup"><span data-stu-id="0910c-115">The following example shows comment-based at the end of a script.</span></span>

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```