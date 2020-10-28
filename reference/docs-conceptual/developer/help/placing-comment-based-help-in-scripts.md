---
ms.date: 09/12/2016
ms.topic: reference
title: Lägga till kommentarsbaserat hjälp i skript
description: Lägga till kommentarsbaserat hjälp i skript
ms.openlocfilehash: b0d32b7ab063269085899a643b0c3a17da2073fc
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645433"
---
# <a name="placing-comment-based-help-in-scripts"></a><span data-ttu-id="fd572-103">Lägga till kommentarsbaserat hjälp i skript</span><span class="sxs-lookup"><span data-stu-id="fd572-103">Placing Comment-Based Help in Scripts</span></span>

<span data-ttu-id="fd572-104">I det här avsnittet beskrivs var du kan placera den kommenterade hjälpen för ett skript så att `Get-Help` cmdleten associerar det kommenterade hjälp avsnittet med skript och inte med funktioner som kan finnas i skriptet.</span><span class="sxs-lookup"><span data-stu-id="fd572-104">This topic explains where to place comment-based help for a script so that the `Get-Help` cmdlet associates the comment-based help topic with scripts and not with any functions that might be in the script.</span></span>

## <a name="where-to-place-comment-based-help-for-a-script"></a><span data-ttu-id="fd572-105">Plats Comment-Based hjälp för ett skript</span><span class="sxs-lookup"><span data-stu-id="fd572-105">Where to Place Comment-Based Help for a Script</span></span>

- <span data-ttu-id="fd572-106">I början av skript filen.</span><span class="sxs-lookup"><span data-stu-id="fd572-106">At the beginning of the script file.</span></span>

  <span data-ttu-id="fd572-107">Skript hjälpen kan bara föregås av kommentarer och tomma rader.</span><span class="sxs-lookup"><span data-stu-id="fd572-107">Script Help can be preceded in the script only by comments and blank lines.</span></span>

- <span data-ttu-id="fd572-108">I slutet av skript filen.</span><span class="sxs-lookup"><span data-stu-id="fd572-108">At the end of the script file.</span></span>

  <span data-ttu-id="fd572-109">Om det första objektet i skript texten (efter hjälpen) är en funktions deklaration måste det finnas minst två tomma rader mellan slutet av skript hjälpen och funktions deklarationen.</span><span class="sxs-lookup"><span data-stu-id="fd572-109">If the first item in the script body (after the Help) is a function declaration, there must be at least two blank lines between the end of the script Help and the function declaration.</span></span> <span data-ttu-id="fd572-110">Annars tolkas hjälpen som hjälp för funktionen, inte för att hjälpa till med skriptet.</span><span class="sxs-lookup"><span data-stu-id="fd572-110">Otherwise, the Help is interpreted as being Help for the function, not Help for the script.</span></span>

## <a name="examples-of-help-placement-in-a-script"></a><span data-ttu-id="fd572-111">Exempel på hur hjälp placeras i ett skript</span><span class="sxs-lookup"><span data-stu-id="fd572-111">Examples of Help Placement in a Script</span></span>

<span data-ttu-id="fd572-112">I följande exempel visas var och en av placerings alternativen för den kommenterade hjälpen för ett skript.</span><span class="sxs-lookup"><span data-stu-id="fd572-112">The following examples show each of the placement options for comment-based help for a script.</span></span>

### <a name="help-at-the-beginning-of-a-script"></a><span data-ttu-id="fd572-113">Hjälp i början av ett skript</span><span class="sxs-lookup"><span data-stu-id="fd572-113">Help at the Beginning of a Script</span></span>

<span data-ttu-id="fd572-114">I följande exempel visas en kommentar baserad i början av ett skript.</span><span class="sxs-lookup"><span data-stu-id="fd572-114">The following example shows comment-based at the beginning of a script.</span></span>

```powershell
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a><span data-ttu-id="fd572-115">Hjälp i slutet av ett skript</span><span class="sxs-lookup"><span data-stu-id="fd572-115">Help at the End of a Script</span></span>

 <span data-ttu-id="fd572-116">I följande exempel visas en kommentar baserad i slutet av ett skript.</span><span class="sxs-lookup"><span data-stu-id="fd572-116">The following example shows comment-based at the end of a script.</span></span>

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>
```
