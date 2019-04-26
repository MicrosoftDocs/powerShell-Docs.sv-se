---
title: Placera Kommentarbaserad hjälp i skript | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49f8267c-d887-4d7d-b9b7-80dc624b1261
caps.latest.revision: 4
ms.openlocfilehash: d199c53a748ac57bb2a5f998b5056e39d3e80c0d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083237"
---
# <a name="placing-comment-based-help-in-scripts"></a><span data-ttu-id="bb720-102">Lägga till kommentarsbaserat hjälp i skript</span><span class="sxs-lookup"><span data-stu-id="bb720-102">Placing Comment-Based Help in Scripts</span></span>

<span data-ttu-id="bb720-103">Det här avsnittet förklarar var du ska placera kommentarbaserad hjälp för ett skript så att den `Get-Help` cmdlet associerar hjälpavsnitt kommentarbaserad med skript och inte med alla funktioner som kan vara i skriptet.</span><span class="sxs-lookup"><span data-stu-id="bb720-103">This topic explains where to place comment-based help for a script so that the `Get-Help` cmdlet associates the comment-based help topic with scripts and not with any functions that might be in the script.</span></span>

## <a name="where-to-place-comment-based-help-for-a-script"></a><span data-ttu-id="bb720-104">Var man ska placera Kommentarbaserad hjälp för ett skript</span><span class="sxs-lookup"><span data-stu-id="bb720-104">Where to Place Comment-Based Help for a Script</span></span>

- <span data-ttu-id="bb720-105">I början av skriptfilen.</span><span class="sxs-lookup"><span data-stu-id="bb720-105">At the beginning of the script file.</span></span> <span data-ttu-id="bb720-106">Hjälp för skript kan föregås i skriptet bara av kommentarer och tomma rader.</span><span class="sxs-lookup"><span data-stu-id="bb720-106">Script Help can be preceded in the script only by comments and blank lines.</span></span>

- <span data-ttu-id="bb720-107">I slutet av skriptfilen.</span><span class="sxs-lookup"><span data-stu-id="bb720-107">At the end of the script file.</span></span>

  <span data-ttu-id="bb720-108">Om det första objektet i skripttext (efter hjälp) är en funktionsdeklarationen, måste det finnas minst två tomma rader mellan slutet av skriptet hjälp och funktionsdeklarationen.</span><span class="sxs-lookup"><span data-stu-id="bb720-108">If the first item in the script body (after the Help) is a function declaration, there must be at least two blank lines between the end of the script Help and the function declaration.</span></span> <span data-ttu-id="bb720-109">I annat fall tolkas hjälp som hjälp för funktionen inte hjälp för skriptet.</span><span class="sxs-lookup"><span data-stu-id="bb720-109">Otherwise, the Help is interpreted as being Help for the function, not Help for the script.</span></span>

## <a name="examples-of-help-placement-in-a-script"></a><span data-ttu-id="bb720-110">Exempel på Hjälp placering i ett skript</span><span class="sxs-lookup"><span data-stu-id="bb720-110">Examples of Help Placement in a Script</span></span>

 <span data-ttu-id="bb720-111">I följande exempel visas var och en av placeringsalternativ för kommentarbaserad hjälp för ett skript.</span><span class="sxs-lookup"><span data-stu-id="bb720-111">The following examples show each of the placement options for comment-based help for a script.</span></span>

### <a name="help-at-the-beginning-of-a-script"></a><span data-ttu-id="bb720-112">Hjälp i början av ett skript</span><span class="sxs-lookup"><span data-stu-id="bb720-112">Help at the Beginning of a Script</span></span>

 <span data-ttu-id="bb720-113">I följande exempel visas kommentarbaserad i början av ett skript.</span><span class="sxs-lookup"><span data-stu-id="bb720-113">The following example shows comment-based at the beginning of a script.</span></span>

```
<#
.Description
This script performs a series of network connection tests.
#>

param [string]$ComputerName
...
```

### <a name="help-at-the-end-of-a-script"></a><span data-ttu-id="bb720-114">Hjälp i slutet av ett skript</span><span class="sxs-lookup"><span data-stu-id="bb720-114">Help at the End of a Script</span></span>

 <span data-ttu-id="bb720-115">I följande exempel visas kommentarbaserad i slutet av ett skript.</span><span class="sxs-lookup"><span data-stu-id="bb720-115">The following example shows comment-based at the end of a script.</span></span>

```powershell
...
function Ping { Test-Connection -ComputerName $ComputerName }

<#
.Description
This script performs a series of network connection tests.
#>

```