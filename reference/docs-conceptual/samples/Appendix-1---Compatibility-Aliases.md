---
ms.date: 09/09/2019
keywords: PowerShell, cmdlet
title: Bilaga 1 Kompatibilitetsalias
ms.openlocfilehash: 2351fdf23711fe1417f7e3fc3cca5b642d5a59fc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "70848173"
---
# <a name="appendix-1---compatibility-aliases"></a><span data-ttu-id="e9fa1-103">Bilaga 1 – kompatibilitets-alias</span><span class="sxs-lookup"><span data-stu-id="e9fa1-103">Appendix 1 - Compatibility Aliases</span></span>

<span data-ttu-id="e9fa1-104">PowerShell har flera alias som gör att **UNIX** -och **cmd. exe** -användare kan använda välbekanta kommandon.</span><span class="sxs-lookup"><span data-stu-id="e9fa1-104">PowerShell has several aliases that allow **UNIX** and **cmd.exe** users to use familiar commands.</span></span>
<span data-ttu-id="e9fa1-105">Kommandona och deras relaterade PowerShell-cmdlet och PowerShell-alias visas i följande tabell:</span><span class="sxs-lookup"><span data-stu-id="e9fa1-105">The commands and their related PowerShell cmdlet and PowerShell alias are shown in the following table:</span></span>

|<span data-ttu-id="e9fa1-106">cmd. exe-kommando</span><span class="sxs-lookup"><span data-stu-id="e9fa1-106">cmd.exe command</span></span>|<span data-ttu-id="e9fa1-107">UNIX-kommando</span><span class="sxs-lookup"><span data-stu-id="e9fa1-107">UNIX command</span></span>|<span data-ttu-id="e9fa1-108">PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="e9fa1-108">PowerShell cmdlet</span></span>|<span data-ttu-id="e9fa1-109">PowerShell-alias</span><span class="sxs-lookup"><span data-stu-id="e9fa1-109">PowerShell alias</span></span>|
|---------------|----------------|--------------|------------|
|<span data-ttu-id="e9fa1-110">**CLS**</span><span class="sxs-lookup"><span data-stu-id="e9fa1-110">**cls**</span></span>|<span data-ttu-id="e9fa1-111">**Rensa**</span><span class="sxs-lookup"><span data-stu-id="e9fa1-111">**clear**</span></span>|<span data-ttu-id="e9fa1-112">`Clear-Host` (funktion)</span><span class="sxs-lookup"><span data-stu-id="e9fa1-112">`Clear-Host` (function)</span></span>|`cls`|
|<span data-ttu-id="e9fa1-113">**exemplar**</span><span class="sxs-lookup"><span data-stu-id="e9fa1-113">**copy**</span></span>|<span data-ttu-id="e9fa1-114">**CP**</span><span class="sxs-lookup"><span data-stu-id="e9fa1-114">**cp**</span></span>|`Copy-Item`|`cpi`|
|<span data-ttu-id="e9fa1-115">**tillämpning**</span><span class="sxs-lookup"><span data-stu-id="e9fa1-115">**dir**</span></span>|<span data-ttu-id="e9fa1-116">**LS**</span><span class="sxs-lookup"><span data-stu-id="e9fa1-116">**ls**</span></span>|`Get-ChildItem`|`gci`|
|<span data-ttu-id="e9fa1-117">**type**</span><span class="sxs-lookup"><span data-stu-id="e9fa1-117">**type**</span></span>|<span data-ttu-id="e9fa1-118">**lat**</span><span class="sxs-lookup"><span data-stu-id="e9fa1-118">**cat**</span></span>|`Get-Content`|`gc`|
|<span data-ttu-id="e9fa1-119">**fart**</span><span class="sxs-lookup"><span data-stu-id="e9fa1-119">**move**</span></span>|<span data-ttu-id="e9fa1-120">**MV**</span><span class="sxs-lookup"><span data-stu-id="e9fa1-120">**mv**</span></span>|`Move-Item`|`mi`|
|<span data-ttu-id="e9fa1-121">**MD**</span><span class="sxs-lookup"><span data-stu-id="e9fa1-121">**md**</span></span>|<span data-ttu-id="e9fa1-122">**mkdir**</span><span class="sxs-lookup"><span data-stu-id="e9fa1-122">**mkdir**</span></span>|`New-Item`|`ni`|
|<span data-ttu-id="e9fa1-123">**PUSHD**</span><span class="sxs-lookup"><span data-stu-id="e9fa1-123">**pushd**</span></span>|<span data-ttu-id="e9fa1-124">**PUSHD**</span><span class="sxs-lookup"><span data-stu-id="e9fa1-124">**pushd**</span></span>|`Push-Location`|`pushd`|
|<span data-ttu-id="e9fa1-125">**POPD**</span><span class="sxs-lookup"><span data-stu-id="e9fa1-125">**popd**</span></span>|<span data-ttu-id="e9fa1-126">**POPD**</span><span class="sxs-lookup"><span data-stu-id="e9fa1-126">**popd**</span></span>|`Pop-Location`|`popd`|
|<span data-ttu-id="e9fa1-127">**del**, **Radera**, **RD**, **rmdir**</span><span class="sxs-lookup"><span data-stu-id="e9fa1-127">**del**, **erase**, **rd**, **rmdir**</span></span>|<span data-ttu-id="e9fa1-128">**RM**</span><span class="sxs-lookup"><span data-stu-id="e9fa1-128">**rm**</span></span>|`Remove-Item`|`ri`|
|<span data-ttu-id="e9fa1-129">**Outlook**</span><span class="sxs-lookup"><span data-stu-id="e9fa1-129">**ren**</span></span>|<span data-ttu-id="e9fa1-130">**MV**</span><span class="sxs-lookup"><span data-stu-id="e9fa1-130">**mv**</span></span>|`Rename-Item`|`rni`|
|<span data-ttu-id="e9fa1-131">**CD**, **chdir**</span><span class="sxs-lookup"><span data-stu-id="e9fa1-131">**cd**, **chdir**</span></span>|<span data-ttu-id="e9fa1-132">**installations**</span><span class="sxs-lookup"><span data-stu-id="e9fa1-132">**cd**</span></span>|`Set-Location`|`sl`|

<span data-ttu-id="e9fa1-133">Använd cmdleten [Get-alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) för att hitta PowerShell-alias.</span><span class="sxs-lookup"><span data-stu-id="e9fa1-133">To find the PowerShell aliases, use the [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet.</span></span> <span data-ttu-id="e9fa1-134">Om du vill visa en cmdlets alias använder du **definitions** parametern och anger namnet på cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e9fa1-134">To display a cmdlet's aliases, use the **Definition** parameter and specify the cmdlet name.</span></span>
<span data-ttu-id="e9fa1-135">Eller, om du vill hitta ett Aliass cmdlet-namn, använder du parametern **Name** och anger aliaset.</span><span class="sxs-lookup"><span data-stu-id="e9fa1-135">Or, to find an alias's cmdlet name, use the **Name** parameter and specify the alias.</span></span>

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
