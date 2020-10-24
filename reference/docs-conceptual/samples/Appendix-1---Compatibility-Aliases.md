---
ms.date: 08/03/2020
keywords: powershell,cmdlet
title: Bilaga 1 Kompatibilitetsalias
description: PowerShell har flera alias som låter UNIX-och cmd.exe användare använda välbekanta kommandon.
ms.openlocfilehash: 8cbbd5a358de9018fcb5c840e711cd76f7a9a353
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500750"
---
# <a name="appendix-1---compatibility-aliases"></a><span data-ttu-id="87893-104">Bilaga 1 – kompatibilitets-alias</span><span class="sxs-lookup"><span data-stu-id="87893-104">Appendix 1 - Compatibility Aliases</span></span>

<span data-ttu-id="87893-105">PowerShell har flera alias som låter **UNIX** -och **cmd.exe** användare använda välbekanta kommandon.</span><span class="sxs-lookup"><span data-stu-id="87893-105">PowerShell has several aliases that allow **UNIX** and **cmd.exe** users to use familiar commands.</span></span>
<span data-ttu-id="87893-106">Kommandona och deras relaterade PowerShell-cmdlet och PowerShell-alias visas i följande tabell:</span><span class="sxs-lookup"><span data-stu-id="87893-106">The commands and their related PowerShell cmdlet and PowerShell alias are shown in the following table:</span></span>

|            <span data-ttu-id="87893-107">cmd.exe kommando</span><span class="sxs-lookup"><span data-stu-id="87893-107">cmd.exe command</span></span>            | <span data-ttu-id="87893-108">UNIX-kommando</span><span class="sxs-lookup"><span data-stu-id="87893-108">UNIX command</span></span> | <span data-ttu-id="87893-109">PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="87893-109">PowerShell cmdlet</span></span> | <span data-ttu-id="87893-110">PowerShell-alias</span><span class="sxs-lookup"><span data-stu-id="87893-110">PowerShell alias</span></span> |
| ------------------------------------- | ------------ | ----------------- | ---------------- |
| <span data-ttu-id="87893-111">**CD**, **chdir**</span><span class="sxs-lookup"><span data-stu-id="87893-111">**cd**, **chdir**</span></span>                     | <span data-ttu-id="87893-112">**installations**</span><span class="sxs-lookup"><span data-stu-id="87893-112">**cd**</span></span>       | `Set-Location`    | `sl`             |
| <span data-ttu-id="87893-113">**CLS**</span><span class="sxs-lookup"><span data-stu-id="87893-113">**cls**</span></span>                               | <span data-ttu-id="87893-114">**Rensa**</span><span class="sxs-lookup"><span data-stu-id="87893-114">**clear**</span></span>    | `Clear-Host`      | `cls`            |
| <span data-ttu-id="87893-115">**kopiering**</span><span class="sxs-lookup"><span data-stu-id="87893-115">**copy**</span></span>                              | <span data-ttu-id="87893-116">**CP**</span><span class="sxs-lookup"><span data-stu-id="87893-116">**cp**</span></span>       | `Copy-Item`       | `cpi`            |
| <span data-ttu-id="87893-117">**del**, **Radera**, **RD**, **rmdir**</span><span class="sxs-lookup"><span data-stu-id="87893-117">**del**, **erase**, **rd**, **rmdir**</span></span> | <span data-ttu-id="87893-118">**RM**</span><span class="sxs-lookup"><span data-stu-id="87893-118">**rm**</span></span>       | `Remove-Item`     | `ri`             |
| <span data-ttu-id="87893-119">**tillämpning**</span><span class="sxs-lookup"><span data-stu-id="87893-119">**dir**</span></span>                               | <span data-ttu-id="87893-120">**LS**</span><span class="sxs-lookup"><span data-stu-id="87893-120">**ls**</span></span>       | `Get-ChildItem`   | `gci`            |
| <span data-ttu-id="87893-121">**eko**</span><span class="sxs-lookup"><span data-stu-id="87893-121">**echo**</span></span>                              | <span data-ttu-id="87893-122">**eko**</span><span class="sxs-lookup"><span data-stu-id="87893-122">**echo**</span></span>     | `Write-Output`    | `write`          |
| <span data-ttu-id="87893-123">**MD**</span><span class="sxs-lookup"><span data-stu-id="87893-123">**md**</span></span>                                | <span data-ttu-id="87893-124">**mkdir**</span><span class="sxs-lookup"><span data-stu-id="87893-124">**mkdir**</span></span>    | `New-Item`        | `ni`             |
| <span data-ttu-id="87893-125">**fart**</span><span class="sxs-lookup"><span data-stu-id="87893-125">**move**</span></span>                              | <span data-ttu-id="87893-126">**MV**</span><span class="sxs-lookup"><span data-stu-id="87893-126">**mv**</span></span>       | `Move-Item`       | `mi`             |
| <span data-ttu-id="87893-127">**POPD**</span><span class="sxs-lookup"><span data-stu-id="87893-127">**popd**</span></span>                              | <span data-ttu-id="87893-128">**POPD**</span><span class="sxs-lookup"><span data-stu-id="87893-128">**popd**</span></span>     | `Pop-Location`    | `popd`           |
| <span data-ttu-id="87893-129">**PUSHD**</span><span class="sxs-lookup"><span data-stu-id="87893-129">**pushd**</span></span>                             | <span data-ttu-id="87893-130">**PUSHD**</span><span class="sxs-lookup"><span data-stu-id="87893-130">**pushd**</span></span>    | `Push-Location`   | `pushd`          |
| <span data-ttu-id="87893-131">**Outlook**</span><span class="sxs-lookup"><span data-stu-id="87893-131">**ren**</span></span>                               | <span data-ttu-id="87893-132">**MV**</span><span class="sxs-lookup"><span data-stu-id="87893-132">**mv**</span></span>       | `Rename-Item`     | `rni`            |
| <span data-ttu-id="87893-133">**bastyp**</span><span class="sxs-lookup"><span data-stu-id="87893-133">**type**</span></span>                              | <span data-ttu-id="87893-134">**lat**</span><span class="sxs-lookup"><span data-stu-id="87893-134">**cat**</span></span>      | `Get-Content`     | `gc`             |

<span data-ttu-id="87893-135">Använd cmdleten [Get-alias](xref:Microsoft.PowerShell.Utility.Get-Alias) för att hitta PowerShell-alias.</span><span class="sxs-lookup"><span data-stu-id="87893-135">To find the PowerShell aliases, use the [Get-Alias](xref:Microsoft.PowerShell.Utility.Get-Alias) cmdlet.</span></span> <span data-ttu-id="87893-136">Om du vill visa en cmdlets alias använder du **definitions** parametern och anger namnet på cmdleten.</span><span class="sxs-lookup"><span data-stu-id="87893-136">To display a cmdlet's aliases, use the **Definition** parameter and specify the cmdlet name.</span></span>
<span data-ttu-id="87893-137">Eller, om du vill hitta ett Aliass cmdlet-namn, använder du parametern **Name** och anger aliaset.</span><span class="sxs-lookup"><span data-stu-id="87893-137">Or, to find an alias's cmdlet name, use the **Name** parameter and specify the alias.</span></span>

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
