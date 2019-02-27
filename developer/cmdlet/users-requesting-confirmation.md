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
ms.openlocfilehash: e4abbb14b31406b845d9b6af6b6372338fb0d926
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846979"
---
# <a name="users-requesting-confirmation"></a><span data-ttu-id="656f1-102">Användare som begär bekräftelse</span><span class="sxs-lookup"><span data-stu-id="656f1-102">Users Requesting Confirmation</span></span>

<span data-ttu-id="656f1-103">När du anger ett värde av `true` för den `SupportsShouldProcess` parametern för cmdleten attributet deklarationen som användarna kan ange den `Confirm` parameter i Kommandotolken.</span><span class="sxs-lookup"><span data-stu-id="656f1-103">When you specify a value of `true` for the `SupportsShouldProcess` parameter of the Cmdlet attribute declaration, users can specify the `Confirm` parameter at the command prompt.</span></span>

<span data-ttu-id="656f1-104">Användare kan ange i standardmiljön, den `Confirm` parametern eller `"-Confirm:$true` så att bekräftelse begärs när den [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metoden anropas.</span><span class="sxs-lookup"><span data-stu-id="656f1-104">In the default environment, users can specify the `Confirm` parameter or `"-Confirm:$true` so that confirmation is requested when the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method is called.</span></span> <span data-ttu-id="656f1-105">Detta kringgår [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) bekräftelse begäranden, även för hög inverkan åtgärder.</span><span class="sxs-lookup"><span data-stu-id="656f1-105">This bypasses [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) confirmation requests, even for high-impact operations.</span></span>

<span data-ttu-id="656f1-106">Om `Confirm` inte anges i [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) anrop begär bekräftelse om den `$ConfirmPreference` inställningsvariabeln är lika med eller större än den `ConfirmImpact` inställningen för den cmdlet eller providern.</span><span class="sxs-lookup"><span data-stu-id="656f1-106">If `Confirm` is not specified, the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation if the `$ConfirmPreference` preference variable is equal to or greater than the `ConfirmImpact` setting of the cmdlet or provider.</span></span> <span data-ttu-id="656f1-107">Standardinställningen för `$ConfirmPreference` är hög.</span><span class="sxs-lookup"><span data-stu-id="656f1-107">The default setting of `$ConfirmPreference` is High.</span></span> <span data-ttu-id="656f1-108">Därför i standardmiljön begär endast-cmdlets och providers som anger en hög inverkan åtgärd bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="656f1-108">Therefore, in the default environment, only cmdlets and providers that specify a high-impact action request confirmation.</span></span>

<span data-ttu-id="656f1-109">Om `Confirm` är false eller om `"-Confirm:$false` anges den [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) anrop begär bekräftelse från användaren, och `$ConfirmPreference` gränssnittsvariabeln ignoreras.</span><span class="sxs-lookup"><span data-stu-id="656f1-109">If `Confirm` is false or if `"-Confirm:$false` is specified, the [System.Management.Automation.Cmdlet.Shouldprocess\*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation from the user, and the `$ConfirmPreference` shell variable is ignored.</span></span>

## <a name="remarks"></a><span data-ttu-id="656f1-110">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="656f1-110">Remarks</span></span>

- <span data-ttu-id="656f1-111">För cmdlets och providers som anger `SupportsShouldProcess`, men inte `ConfirmImpact`dessa åtgärder hanteras som ”medelstor inverkan”-åtgärder och de uppmanas inte som standard.</span><span class="sxs-lookup"><span data-stu-id="656f1-111">For cmdlets and providers that specify `SupportsShouldProcess`, but not `ConfirmImpact`, those actions are handled as "medium impact" actions, and they will not prompt by default.</span></span> <span data-ttu-id="656f1-112">Deras inverkan är lägre än standardinställningen för den `$ConfirmPreference` inställningsvariabeln.</span><span class="sxs-lookup"><span data-stu-id="656f1-112">Their impact level is less than the default setting of the `$ConfirmPreference` preference variable.</span></span>

- <span data-ttu-id="656f1-113">Om användaren anger den `Verbose` parameter, de kommer att meddelas om åtgärden även om de inte uppmanas att bekräfta.</span><span class="sxs-lookup"><span data-stu-id="656f1-113">If the user specifies the `Verbose` parameter, they will be notified of the operation even if they are not prompted for confirmation.</span></span>

## <a name="see-also"></a><span data-ttu-id="656f1-114">Se även</span><span class="sxs-lookup"><span data-stu-id="656f1-114">See Also</span></span>

[<span data-ttu-id="656f1-115">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="656f1-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
