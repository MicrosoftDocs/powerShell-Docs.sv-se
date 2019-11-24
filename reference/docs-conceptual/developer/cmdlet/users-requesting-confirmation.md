---
title: Användare som begär bekräftelse | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f337498-c534-40ed-968a-09d4d9ca3849
caps.latest.revision: 8
ms.openlocfilehash: ed9ff9fc1668a89e1ac0ceac8f0800a15b349226
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359155"
---
# <a name="users-requesting-confirmation"></a><span data-ttu-id="d6791-102">Användare som begär bekräftelse</span><span class="sxs-lookup"><span data-stu-id="d6791-102">Users Requesting Confirmation</span></span>

<span data-ttu-id="d6791-103">När du anger ett värde för `true` för `SupportsShouldProcess`-parametern för cmdlet-attributets deklaration, kan användarna ange `Confirm`-parametern i kommando tolken.</span><span class="sxs-lookup"><span data-stu-id="d6791-103">When you specify a value of `true` for the `SupportsShouldProcess` parameter of the Cmdlet attribute declaration, users can specify the `Confirm` parameter at the command prompt.</span></span>

<span data-ttu-id="d6791-104">I Standard miljön kan användare ange `Confirm` parameter eller `"-Confirm:$true` så att en bekräftelse begärs när metoden [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) anropas.</span><span class="sxs-lookup"><span data-stu-id="d6791-104">In the default environment, users can specify the `Confirm` parameter or `"-Confirm:$true` so that confirmation is requested when the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method is called.</span></span> <span data-ttu-id="d6791-105">Detta kringgår [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) bekräftelse förfrågningar, även för åtgärder med hög påverkan.</span><span class="sxs-lookup"><span data-stu-id="d6791-105">This bypasses [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) confirmation requests, even for high-impact operations.</span></span>

<span data-ttu-id="d6791-106">Om `Confirm` inte anges bekräftar [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) anrops begär Anden om inställningen `$ConfirmPreference` är lika med eller större än `ConfirmImpact` inställningen för cmdleten eller providern.</span><span class="sxs-lookup"><span data-stu-id="d6791-106">If `Confirm` is not specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation if the `$ConfirmPreference` preference variable is equal to or greater than the `ConfirmImpact` setting of the cmdlet or provider.</span></span> <span data-ttu-id="d6791-107">Standardinställningen för `$ConfirmPreference` är hög.</span><span class="sxs-lookup"><span data-stu-id="d6791-107">The default setting of `$ConfirmPreference` is High.</span></span> <span data-ttu-id="d6791-108">I Standard miljön är det därför bara-cmdletar och-providers som anger en bekräftelse av åtgärden som kräver hög påverkan.</span><span class="sxs-lookup"><span data-stu-id="d6791-108">Therefore, in the default environment, only cmdlets and providers that specify a high-impact action request confirmation.</span></span>

<span data-ttu-id="d6791-109">Om `Confirm` är falskt eller om `"-Confirm:$false` anges, begär [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) förfrågningar från användaren och `$ConfirmPreference` Shell-variabeln ignoreras.</span><span class="sxs-lookup"><span data-stu-id="d6791-109">If `Confirm` is false or if `"-Confirm:$false` is specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation from the user, and the `$ConfirmPreference` shell variable is ignored.</span></span>

## <a name="remarks"></a><span data-ttu-id="d6791-110">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="d6791-110">Remarks</span></span>

- <span data-ttu-id="d6791-111">För cmdlets och providers som anger `SupportsShouldProcess`, men inte `ConfirmImpact`, hanteras dessa åtgärder som "medelhög påverkan"-åtgärder och de kommer inte att fråga som standard.</span><span class="sxs-lookup"><span data-stu-id="d6791-111">For cmdlets and providers that specify `SupportsShouldProcess`, but not `ConfirmImpact`, those actions are handled as "medium impact" actions, and they will not prompt by default.</span></span> <span data-ttu-id="d6791-112">Deras effekt nivå är mindre än standardinställningen för variabeln `$ConfirmPreference`.</span><span class="sxs-lookup"><span data-stu-id="d6791-112">Their impact level is less than the default setting of the `$ConfirmPreference` preference variable.</span></span>

- <span data-ttu-id="d6791-113">Om användaren anger parametern `Verbose` kommer de att meddelas om åtgärden även om de inte uppmanas att bekräfta.</span><span class="sxs-lookup"><span data-stu-id="d6791-113">If the user specifies the `Verbose` parameter, they will be notified of the operation even if they are not prompted for confirmation.</span></span>

## <a name="see-also"></a><span data-ttu-id="d6791-114">Se även</span><span class="sxs-lookup"><span data-stu-id="d6791-114">See Also</span></span>

[<span data-ttu-id="d6791-115">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="d6791-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
