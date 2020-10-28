---
ms.date: 09/13/2016
ms.topic: reference
title: Cmdlet-alias
description: Cmdlet-alias
ms.openlocfilehash: 734553a9911aef256df563afa6abcdb23d7a62e6
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92660786"
---
# <a name="cmdlet-aliases"></a><span data-ttu-id="b7de7-103">Cmdlet-alias</span><span class="sxs-lookup"><span data-stu-id="b7de7-103">Cmdlet Aliases</span></span>

<span data-ttu-id="b7de7-104">Du kan använda cmdlet-alias för att förbättra användar upplevelsen för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b7de7-104">You can use cmdlet aliases to improve the cmdlet user experience.</span></span> <span data-ttu-id="b7de7-105">Du kan lägga till alias till ofta använda cmdletar för att minska inmatningen och göra det enklare att snabbt utföra uppgifter.</span><span class="sxs-lookup"><span data-stu-id="b7de7-105">You can add aliases to frequently used cmdlets to reduce typing and to make it easier to complete tasks quickly.</span></span> <span data-ttu-id="b7de7-106">Du kan inkludera inbyggda alias i dina cmdletar, eller så kan användarna definiera egna anpassade alias.</span><span class="sxs-lookup"><span data-stu-id="b7de7-106">You can include built-in aliases in your cmdlets, or users can define their own custom aliases.</span></span>

<span data-ttu-id="b7de7-107">Till exempel har cmdleten [Get-Command](/powershell/module/microsoft.powershell.core/get-command) ett inbyggt `gcm` alias.</span><span class="sxs-lookup"><span data-stu-id="b7de7-107">For example, the [Get-Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet has a built-in `gcm` alias.</span></span> <span data-ttu-id="b7de7-108">Du kan också använda alias för att lägga till kommando namn från andra språk så att användarna inte behöver lära sig nya kommandon.</span><span class="sxs-lookup"><span data-stu-id="b7de7-108">You can also use aliases to add command names from other languages so that users do not have to learn new commands.</span></span>

## <a name="alias-guidelines"></a><span data-ttu-id="b7de7-109">Rikt linjer för alias</span><span class="sxs-lookup"><span data-stu-id="b7de7-109">Alias Guidelines</span></span>

<span data-ttu-id="b7de7-110">Följ dessa rikt linjer när du skapar inbyggda alias för dina cmdlet: ar:</span><span class="sxs-lookup"><span data-stu-id="b7de7-110">Follow these guidelines when you create built-in aliases for your cmdlets:</span></span>

- <span data-ttu-id="b7de7-111">Innan du tilldelar alias startar du Windows PowerShell och kör cmdleten [Get-alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) för att se de alias som redan används.</span><span class="sxs-lookup"><span data-stu-id="b7de7-111">Before you assign aliases, start Windows PowerShell, and then run the [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet to see the aliases that are already used.</span></span>

- <span data-ttu-id="b7de7-112">Inkludera ett alias som refererar till verbet för cmdlet-namnet och ett alias som refererar till substantivet för cmdlet-namnet.</span><span class="sxs-lookup"><span data-stu-id="b7de7-112">Include an alias prefix that references the verb of the cmdlet name and an alias suffix that references the noun of the cmdlet name.</span></span> <span data-ttu-id="b7de7-113">Aliaset för `Import-Module` cmdleten är till exempel "ipmo".</span><span class="sxs-lookup"><span data-stu-id="b7de7-113">For example, the alias for the `Import-Module` cmdlet is "ipmo".</span></span> <span data-ttu-id="b7de7-114">En lista över alla verb och deras alias finns i [cmdlet-verb](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="b7de7-114">For a list of all the verbs and their aliases, see [Cmdlet Verbs](./approved-verbs-for-windows-powershell-commands.md).</span></span>

- <span data-ttu-id="b7de7-115">För cmdletar som har samma verb inkluderar du samma alias.</span><span class="sxs-lookup"><span data-stu-id="b7de7-115">For cmdlets that have the same verb, include the same alias prefix.</span></span> <span data-ttu-id="b7de7-116">Alias för alla Windows PowerShell-cmdletar som har verbet "Get" i namnet använder till exempel prefixet "g".</span><span class="sxs-lookup"><span data-stu-id="b7de7-116">For example, the aliases for all the Windows PowerShell cmdlets that have the "Get" verb in their name use the "g" prefix.</span></span>

- <span data-ttu-id="b7de7-117">För cmdletar som har samma Substantiv inkluderar du samma alias.</span><span class="sxs-lookup"><span data-stu-id="b7de7-117">For cmdlets that have the same noun, include the same alias suffix.</span></span> <span data-ttu-id="b7de7-118">Alias för alla Windows PowerShell-cmdletar som har "session" Substantiv i sitt namn använder till exempel suffixet "sn".</span><span class="sxs-lookup"><span data-stu-id="b7de7-118">For example, the aliases for all the Windows PowerShell cmdlets that have the "Session" noun in their name use the "sn" suffix.</span></span>

- <span data-ttu-id="b7de7-119">För cmdletar som motsvarar kommandon på andra språk använder du namnet på kommandot.</span><span class="sxs-lookup"><span data-stu-id="b7de7-119">For cmdlets that are equivalent to commands in other languages, use the name of the command.</span></span>

- <span data-ttu-id="b7de7-120">I allmänhet ska alias vara så kort som möjligt.</span><span class="sxs-lookup"><span data-stu-id="b7de7-120">In general, make aliases as short as possible.</span></span> <span data-ttu-id="b7de7-121">Kontrol lera att aliaset har minst ett distinktt Character för verbet och ett distinkt Character för substantivet.</span><span class="sxs-lookup"><span data-stu-id="b7de7-121">Make sure the alias has at least one distinct character for the verb and one distinct character for the noun.</span></span> <span data-ttu-id="b7de7-122">Lägg till fler tecken vid behov för att göra aliaset unikt.</span><span class="sxs-lookup"><span data-stu-id="b7de7-122">Add more characters as needed to make the alias unique.</span></span>

## <a name="see-also"></a><span data-ttu-id="b7de7-123">Se även</span><span class="sxs-lookup"><span data-stu-id="b7de7-123">See Also</span></span>

[<span data-ttu-id="b7de7-124">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="b7de7-124">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
