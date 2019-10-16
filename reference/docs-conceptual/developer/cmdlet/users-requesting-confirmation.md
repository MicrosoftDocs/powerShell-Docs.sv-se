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
# <a name="users-requesting-confirmation"></a><span data-ttu-id="7cee0-102">Användare som begär bekräftelse</span><span class="sxs-lookup"><span data-stu-id="7cee0-102">Users Requesting Confirmation</span></span>

<span data-ttu-id="7cee0-103">När du anger ett värde för `true` för parametern `SupportsShouldProcess` i deklarationen för cmdlet-attribut kan användarna ange `Confirm`-parametern i kommando tolken.</span><span class="sxs-lookup"><span data-stu-id="7cee0-103">When you specify a value of `true` for the `SupportsShouldProcess` parameter of the Cmdlet attribute declaration, users can specify the `Confirm` parameter at the command prompt.</span></span>

<span data-ttu-id="7cee0-104">I Standard miljön kan användarna ange parametern `Confirm` eller `"-Confirm:$true` så att bekräftelse begärs när metoden [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) anropas.</span><span class="sxs-lookup"><span data-stu-id="7cee0-104">In the default environment, users can specify the `Confirm` parameter or `"-Confirm:$true` so that confirmation is requested when the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method is called.</span></span> <span data-ttu-id="7cee0-105">Detta kringgår [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) bekräftelse förfrågningar, även för åtgärder med hög påverkan.</span><span class="sxs-lookup"><span data-stu-id="7cee0-105">This bypasses [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) confirmation requests, even for high-impact operations.</span></span>

<span data-ttu-id="7cee0-106">Om `Confirm` inte anges, bekräftar [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) anrops begär Anden om inställnings variabeln @no__t 2 är lika med eller större än den `ConfirmImpact` inställningen för cmdleten eller providern.</span><span class="sxs-lookup"><span data-stu-id="7cee0-106">If `Confirm` is not specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation if the `$ConfirmPreference` preference variable is equal to or greater than the `ConfirmImpact` setting of the cmdlet or provider.</span></span> <span data-ttu-id="7cee0-107">Standardvärdet för `$ConfirmPreference` är högt.</span><span class="sxs-lookup"><span data-stu-id="7cee0-107">The default setting of `$ConfirmPreference` is High.</span></span> <span data-ttu-id="7cee0-108">I Standard miljön är det därför bara-cmdletar och-providers som anger en bekräftelse av åtgärden som kräver hög påverkan.</span><span class="sxs-lookup"><span data-stu-id="7cee0-108">Therefore, in the default environment, only cmdlets and providers that specify a high-impact action request confirmation.</span></span>

<span data-ttu-id="7cee0-109">Om `Confirm` är falskt eller om `"-Confirm:$false` har angetts, begär anropet [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) från användaren, och skal variabeln `$ConfirmPreference` ignoreras.</span><span class="sxs-lookup"><span data-stu-id="7cee0-109">If `Confirm` is false or if `"-Confirm:$false` is specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation from the user, and the `$ConfirmPreference` shell variable is ignored.</span></span>

## <a name="remarks"></a><span data-ttu-id="7cee0-110">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="7cee0-110">Remarks</span></span>

- <span data-ttu-id="7cee0-111">För-cmdlets och providers som anger `SupportsShouldProcess`, men inte `ConfirmImpact`, hanteras dessa åtgärder som "medelhög påverkan"-åtgärder, och de kommer inte att fråga som standard.</span><span class="sxs-lookup"><span data-stu-id="7cee0-111">For cmdlets and providers that specify `SupportsShouldProcess`, but not `ConfirmImpact`, those actions are handled as "medium impact" actions, and they will not prompt by default.</span></span> <span data-ttu-id="7cee0-112">Deras effekt nivå är mindre än standardinställningen för variabeln `$ConfirmPreference`.</span><span class="sxs-lookup"><span data-stu-id="7cee0-112">Their impact level is less than the default setting of the `$ConfirmPreference` preference variable.</span></span>

- <span data-ttu-id="7cee0-113">Om användaren anger parametern `Verbose` kommer de att meddelas om åtgärden även om de inte uppmanas att bekräfta.</span><span class="sxs-lookup"><span data-stu-id="7cee0-113">If the user specifies the `Verbose` parameter, they will be notified of the operation even if they are not prompted for confirmation.</span></span>

## <a name="see-also"></a><span data-ttu-id="7cee0-114">Se även</span><span class="sxs-lookup"><span data-stu-id="7cee0-114">See Also</span></span>

[<span data-ttu-id="7cee0-115">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="7cee0-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
