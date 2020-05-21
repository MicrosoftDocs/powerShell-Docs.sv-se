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
ms.openlocfilehash: 1bebfbd822963830363012060067c656d7709543
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83565534"
---
# <a name="placing-comment-based-help-in-scripts"></a><span data-ttu-id="e120d-102">Lägga till kommentarsbaserat hjälp i skript</span><span class="sxs-lookup"><span data-stu-id="e120d-102">Placing Comment-Based Help in Scripts</span></span>

<span data-ttu-id="e120d-103">I det här avsnittet beskrivs var du kan placera den kommenterade hjälpen för ett skript så att `Get-Help` cmdleten associerar det kommenterade hjälp avsnittet med skript och inte med funktioner som kan finnas i skriptet.</span><span class="sxs-lookup"><span data-stu-id="e120d-103">This topic explains where to place comment-based help for a script so that the `Get-Help` cmdlet associates the comment-based help topic with scripts and not with any functions that might be in the script.</span></span>

## <a name="where-to-place-comment-based-help-for-a-script"></a><span data-ttu-id="e120d-104">Var du vill placera kommenterad hjälp för ett skript</span><span class="sxs-lookup"><span data-stu-id="e120d-104">Where to Place Comment-Based Help for a Script</span></span>

- <span data-ttu-id="e120d-105">I början av skript filen.</span><span class="sxs-lookup"><span data-stu-id="e120d-105">At the beginning of the script file.</span></span> <span data-ttu-id="e120d-106">Skript hjälpen kan bara föregås av kommentarer och tomma rader.</span><span class="sxs-lookup"><span data-stu-id="e120d-106">Script Help can be preceded in the script only by comments and blank lines.</span></span>

- <span data-ttu-id="e120d-107">I slutet av skript filen.</span><span class="sxs-lookup"><span data-stu-id="e120d-107">At the end of the script file.</span></span>

  <span data-ttu-id="e120d-108">Om det första objektet i skript texten (efter hjälpen) är en funktions deklaration måste det finnas minst två tomma rader mellan slutet av skript hjälpen och funktions deklarationen.</span><span class="sxs-lookup"><span data-stu-id="e120d-108">If the first item in the script body (after the Help) is a function declaration, there must be at least two blank lines between the end of the script Help and the function declaration.</span></span> <span data-ttu-id="e120d-109">Annars tolkas hjälpen som hjälp för funktionen, inte för att hjälpa till med skriptet.</span><span class="sxs-lookup"><span data-stu-id="e120d-109">Otherwise, the Help is interpreted as being Help for the function, not Help for the script.</span></span>

## <a name="examples-of-help-placement-in-a-script"></a><span data-ttu-id="e120d-110">Exempel på hur hjälp placeras i ett skript</span><span class="sxs-lookup"><span data-stu-id="e120d-110">Examples of Help Placement in a Script</span></span>

 <span data-ttu-id="e120d-111">I följande exempel visas var och en av placerings alternativen för den kommenterade hjälpen för ett skript.</span><span class="sxs-lookup"><span data-stu-id="e120d-111">The following examples show each of the placement options for comment-based help for a script.</span></span>

### <a name="help-at-the-beginning-of-a-script"></a><span data-ttu-id="e120d-112">Hjälp i början av ett skript</span><span class="sxs-lookup"><span data-stu-id="e120d-112">Help at the Beginning of a Script</span></span>

 <span data-ttu-id="e120d-113">I följande exempel visas en kommentar baserad i början av ett skript.</span><span class="sxs-lookup"><span data-stu-id="e120d-113">The following example shows comment-based at the beginning of a script.</span></span>

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a><span data-ttu-id="e120d-114">Hjälp i slutet av ett skript</span><span class="sxs-lookup"><span data-stu-id="e120d-114">Help at the End of a Script</span></span>

 <span data-ttu-id="e120d-115">I följande exempel visas en kommentar baserad i slutet av ett skript.</span><span class="sxs-lookup"><span data-stu-id="e120d-115">The following example shows comment-based at the end of a script.</span></span>

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```
