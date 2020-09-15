---
ms.date: 08/03/2020
keywords: powershell,cmdlet
title: Bilaga 1 Kompatibilitetsalias
ms.openlocfilehash: e5bd170fea6b6109d2ef4fd58863d6cc8a0e3ae1
ms.sourcegitcommit: d3f78120bdc9096c72aa0dfdbdd91efaf254c738
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87758507"
---
# <a name="appendix-1---compatibility-aliases"></a><span data-ttu-id="5899b-103">Bilaga 1 – kompatibilitets-alias</span><span class="sxs-lookup"><span data-stu-id="5899b-103">Appendix 1 - Compatibility Aliases</span></span>

<span data-ttu-id="5899b-104">PowerShell har flera alias som låter **UNIX** -och **cmd.exe** användare använda välbekanta kommandon.</span><span class="sxs-lookup"><span data-stu-id="5899b-104">PowerShell has several aliases that allow **UNIX** and **cmd.exe** users to use familiar commands.</span></span>
<span data-ttu-id="5899b-105">Kommandona och deras relaterade PowerShell-cmdlet och PowerShell-alias visas i följande tabell:</span><span class="sxs-lookup"><span data-stu-id="5899b-105">The commands and their related PowerShell cmdlet and PowerShell alias are shown in the following table:</span></span>

|            <span data-ttu-id="5899b-106">cmd.exe kommando</span><span class="sxs-lookup"><span data-stu-id="5899b-106">cmd.exe command</span></span>            | <span data-ttu-id="5899b-107">UNIX-kommando</span><span class="sxs-lookup"><span data-stu-id="5899b-107">UNIX command</span></span> | <span data-ttu-id="5899b-108">PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="5899b-108">PowerShell cmdlet</span></span> | <span data-ttu-id="5899b-109">PowerShell-alias</span><span class="sxs-lookup"><span data-stu-id="5899b-109">PowerShell alias</span></span> |
| ------------------------------------- | ------------ | ----------------- | ---------------- |
| <span data-ttu-id="5899b-110">**CD**, **chdir**</span><span class="sxs-lookup"><span data-stu-id="5899b-110">**cd**, **chdir**</span></span>                     | <span data-ttu-id="5899b-111">**installations**</span><span class="sxs-lookup"><span data-stu-id="5899b-111">**cd**</span></span>       | `Set-Location`    | `sl`             |
| <span data-ttu-id="5899b-112">**CLS**</span><span class="sxs-lookup"><span data-stu-id="5899b-112">**cls**</span></span>                               | <span data-ttu-id="5899b-113">**Rensa**</span><span class="sxs-lookup"><span data-stu-id="5899b-113">**clear**</span></span>    | `Clear-Host`      | `cls`            |
| <span data-ttu-id="5899b-114">**exemplar**</span><span class="sxs-lookup"><span data-stu-id="5899b-114">**copy**</span></span>                              | <span data-ttu-id="5899b-115">**CP**</span><span class="sxs-lookup"><span data-stu-id="5899b-115">**cp**</span></span>       | `Copy-Item`       | `cpi`            |
| <span data-ttu-id="5899b-116">**del**, **Radera**, **RD**, **rmdir**</span><span class="sxs-lookup"><span data-stu-id="5899b-116">**del**, **erase**, **rd**, **rmdir**</span></span> | <span data-ttu-id="5899b-117">**RM**</span><span class="sxs-lookup"><span data-stu-id="5899b-117">**rm**</span></span>       | `Remove-Item`     | `ri`             |
| <span data-ttu-id="5899b-118">**tillämpning**</span><span class="sxs-lookup"><span data-stu-id="5899b-118">**dir**</span></span>                               | <span data-ttu-id="5899b-119">**LS**</span><span class="sxs-lookup"><span data-stu-id="5899b-119">**ls**</span></span>       | `Get-ChildItem`   | `gci`            |
| <span data-ttu-id="5899b-120">**eko**</span><span class="sxs-lookup"><span data-stu-id="5899b-120">**echo**</span></span>                              | <span data-ttu-id="5899b-121">**eko**</span><span class="sxs-lookup"><span data-stu-id="5899b-121">**echo**</span></span>     | `Write-Output`    | `write`          |
| <span data-ttu-id="5899b-122">**MD**</span><span class="sxs-lookup"><span data-stu-id="5899b-122">**md**</span></span>                                | <span data-ttu-id="5899b-123">**mkdir**</span><span class="sxs-lookup"><span data-stu-id="5899b-123">**mkdir**</span></span>    | `New-Item`        | `ni`             |
| <span data-ttu-id="5899b-124">**fart**</span><span class="sxs-lookup"><span data-stu-id="5899b-124">**move**</span></span>                              | <span data-ttu-id="5899b-125">**MV**</span><span class="sxs-lookup"><span data-stu-id="5899b-125">**mv**</span></span>       | `Move-Item`       | `mi`             |
| <span data-ttu-id="5899b-126">**POPD**</span><span class="sxs-lookup"><span data-stu-id="5899b-126">**popd**</span></span>                              | <span data-ttu-id="5899b-127">**POPD**</span><span class="sxs-lookup"><span data-stu-id="5899b-127">**popd**</span></span>     | `Pop-Location`    | `popd`           |
| <span data-ttu-id="5899b-128">**PUSHD**</span><span class="sxs-lookup"><span data-stu-id="5899b-128">**pushd**</span></span>                             | <span data-ttu-id="5899b-129">**PUSHD**</span><span class="sxs-lookup"><span data-stu-id="5899b-129">**pushd**</span></span>    | `Push-Location`   | `pushd`          |
| <span data-ttu-id="5899b-130">**Outlook**</span><span class="sxs-lookup"><span data-stu-id="5899b-130">**ren**</span></span>                               | <span data-ttu-id="5899b-131">**MV**</span><span class="sxs-lookup"><span data-stu-id="5899b-131">**mv**</span></span>       | `Rename-Item`     | `rni`            |
| <span data-ttu-id="5899b-132">**bastyp**</span><span class="sxs-lookup"><span data-stu-id="5899b-132">**type**</span></span>                              | <span data-ttu-id="5899b-133">**lat**</span><span class="sxs-lookup"><span data-stu-id="5899b-133">**cat**</span></span>      | `Get-Content`     | `gc`             |

<span data-ttu-id="5899b-134">Använd cmdleten [Get-alias](xref:Microsoft.PowerShell.Utility.Get-Alias) för att hitta PowerShell-alias.</span><span class="sxs-lookup"><span data-stu-id="5899b-134">To find the PowerShell aliases, use the [Get-Alias](xref:Microsoft.PowerShell.Utility.Get-Alias) cmdlet.</span></span> <span data-ttu-id="5899b-135">Om du vill visa en cmdlets alias använder du **definitions** parametern och anger namnet på cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5899b-135">To display a cmdlet's aliases, use the **Definition** parameter and specify the cmdlet name.</span></span>
<span data-ttu-id="5899b-136">Eller, om du vill hitta ett Aliass cmdlet-namn, använder du parametern **Name** och anger aliaset.</span><span class="sxs-lookup"><span data-stu-id="5899b-136">Or, to find an alias's cmdlet name, use the **Name** parameter and specify the alias.</span></span>

```powershell
Get-Alias -Definition Get-ChildItem
```

```Output
CommandType     Name
-----------     ----
Alias           dir -> Get-ChildItem
Alias           gci -> Get-ChildItem
Alias           ls -> Get-ChildItem
```

```powershell
Get-Alias -Name gci
```

```Output
CommandType     Name
-----------     ----
Alias           gci -> Get-ChildItem
```
