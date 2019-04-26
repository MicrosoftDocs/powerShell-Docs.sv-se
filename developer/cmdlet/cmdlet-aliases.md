---
title: Alias för cmdleten | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0d70864-33fb-49ce-8054-c41ba19fd554
caps.latest.revision: 11
ms.openlocfilehash: 32f45702cc0d28e6652ef61ebdbe085291013408
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068733"
---
# <a name="cmdlet-aliases"></a><span data-ttu-id="8345a-102">Cmdlet-alias</span><span class="sxs-lookup"><span data-stu-id="8345a-102">Cmdlet Aliases</span></span>

<span data-ttu-id="8345a-103">Du kan använda cmdleten alias för att förbättra användarupplevelsen cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8345a-103">You can use cmdlet aliases to improve the cmdlet user experience.</span></span> <span data-ttu-id="8345a-104">Du kan lägga till alias ofta använda cmdlets för att minska att skriva och gör det enklare att utföra uppgifter snabbt.</span><span class="sxs-lookup"><span data-stu-id="8345a-104">You can add aliases to frequently used cmdlets to reduce typing and to make it easier to complete tasks quickly.</span></span> <span data-ttu-id="8345a-105">Du kan inkludera inbyggda alias i dina cmdlets eller användare kan definiera egna anpassade alias.</span><span class="sxs-lookup"><span data-stu-id="8345a-105">You can include built-in aliases in your cmdlets, or users can define their own custom aliases.</span></span>

<span data-ttu-id="8345a-106">Till exempel den [Get-Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet har en inbyggd `gcm` alias.</span><span class="sxs-lookup"><span data-stu-id="8345a-106">For example, the [Get-Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet has a built-in `gcm` alias.</span></span> <span data-ttu-id="8345a-107">Du kan också använda alias för att lägga till kommandonamn från andra språk så att användarna inte behöver lära dig nya kommandon.</span><span class="sxs-lookup"><span data-stu-id="8345a-107">You can also use aliases to add command names from other languages so that users do not have to learn new commands.</span></span>

## <a name="alias-guidelines"></a><span data-ttu-id="8345a-108">Riktlinjer för alias</span><span class="sxs-lookup"><span data-stu-id="8345a-108">Alias Guidelines</span></span>

<span data-ttu-id="8345a-109">Följ dessa riktlinjer när du skapar inbyggda alias för dina cmdlets:</span><span class="sxs-lookup"><span data-stu-id="8345a-109">Follow these guidelines when you create built-in aliases for your cmdlets:</span></span>

- <span data-ttu-id="8345a-110">Innan du tilldelar alias, starta Windows PowerShell och kör sedan den [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet för att se de alias som redan används.</span><span class="sxs-lookup"><span data-stu-id="8345a-110">Before you assign aliases, start Windows PowerShell, and then run the [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet to see the aliases that are already used.</span></span>

- <span data-ttu-id="8345a-111">Inkludera ett alias-prefix som refererar till verbet i cmdlet-namn och en alias-suffix som refererar till substantiv av cmdlet-namn.</span><span class="sxs-lookup"><span data-stu-id="8345a-111">Include an alias prefix that references the verb of the cmdlet name and an alias suffix that references the noun of the cmdlet name.</span></span> <span data-ttu-id="8345a-112">Till exempel alias för den `Import-Module` cmdlet är ”ipmo”.</span><span class="sxs-lookup"><span data-stu-id="8345a-112">For example, the alias for the `Import-Module` cmdlet is "ipmo".</span></span> <span data-ttu-id="8345a-113">En lista över alla verb och deras alias, se [Cmdlet verb](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="8345a-113">For a list of all the verbs and their aliases, see [Cmdlet Verbs](./approved-verbs-for-windows-powershell-commands.md).</span></span>

- <span data-ttu-id="8345a-114">För cmdletar som har samma verb prefixet samma alias.</span><span class="sxs-lookup"><span data-stu-id="8345a-114">For cmdlets that have the same verb, include the same alias prefix.</span></span> <span data-ttu-id="8345a-115">Till exempel använda alias för alla Windows PowerShell-cmdlets som har ”Get”-verbet i sina namn prefixet ”g”.</span><span class="sxs-lookup"><span data-stu-id="8345a-115">For example, the aliases for all the Windows PowerShell cmdlets that have the "Get" verb in their name use the "g" prefix.</span></span>

- <span data-ttu-id="8345a-116">För cmdletar som har samma substantiv innehåller samma alias-suffix.</span><span class="sxs-lookup"><span data-stu-id="8345a-116">For cmdlets that have the same noun, include the same alias suffix.</span></span> <span data-ttu-id="8345a-117">Till exempel använda alias för alla Windows PowerShell-cmdlets som har ”Session” substantiv i sina namn med suffixet ”sn”.</span><span class="sxs-lookup"><span data-stu-id="8345a-117">For example, the aliases for all the Windows PowerShell cmdlets that have the "Session" noun in their name use the "sn" suffix.</span></span>

- <span data-ttu-id="8345a-118">Använd namnet på kommandot för cmdletar som motsvarar kommandon på andra språk.</span><span class="sxs-lookup"><span data-stu-id="8345a-118">For cmdlets that are equivalent to commands in other languages, use the name of the command.</span></span>

- <span data-ttu-id="8345a-119">I allmänhet kan göra alias så korta som möjligt.</span><span class="sxs-lookup"><span data-stu-id="8345a-119">In general, make aliases as short as possible.</span></span> <span data-ttu-id="8345a-120">Kontrollera att aliaset som har minst ett tecken för verbet och ett distinkt tecken för substantivet.</span><span class="sxs-lookup"><span data-stu-id="8345a-120">Make sure the alias has at least one distinct character for the verb and one distinct character for the noun.</span></span> <span data-ttu-id="8345a-121">Lägga till fler tecken som behövs för att göra det alias som är unika.</span><span class="sxs-lookup"><span data-stu-id="8345a-121">Add more characters as needed to make the alias unique.</span></span>

## <a name="see-also"></a><span data-ttu-id="8345a-122">Se även</span><span class="sxs-lookup"><span data-stu-id="8345a-122">See Also</span></span>

[<span data-ttu-id="8345a-123">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8345a-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
