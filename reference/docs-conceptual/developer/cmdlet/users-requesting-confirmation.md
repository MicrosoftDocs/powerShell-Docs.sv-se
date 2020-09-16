---
title: Användare som begär bekräftelse | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6f0effb35a110f33248a582fab874e3ab95c7df4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786347"
---
# <a name="users-requesting-confirmation"></a><span data-ttu-id="fca89-102">Användare som begär bekräftelse</span><span class="sxs-lookup"><span data-stu-id="fca89-102">Users Requesting Confirmation</span></span>

<span data-ttu-id="fca89-103">När du anger ett värde för `true` `SupportsShouldProcess` parametern för cmdlet-attributets deklaration, kan användarna ange `Confirm` parametern i kommando tolken.</span><span class="sxs-lookup"><span data-stu-id="fca89-103">When you specify a value of `true` for the `SupportsShouldProcess` parameter of the Cmdlet attribute declaration, users can specify the `Confirm` parameter at the command prompt.</span></span>

<span data-ttu-id="fca89-104">I Standard miljön kan användarna ange `Confirm` parametern eller `"-Confirm:$true` så att bekräftelse begärs när metoden [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) anropas.</span><span class="sxs-lookup"><span data-stu-id="fca89-104">In the default environment, users can specify the `Confirm` parameter or `"-Confirm:$true` so that confirmation is requested when the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method is called.</span></span> <span data-ttu-id="fca89-105">Detta kringgår [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) bekräftelse förfrågningar, även för åtgärder med hög påverkan.</span><span class="sxs-lookup"><span data-stu-id="fca89-105">This bypasses [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) confirmation requests, even for high-impact operations.</span></span>

<span data-ttu-id="fca89-106">Om `Confirm` inte anges bekräftelser anropen [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) om `$ConfirmPreference` Preference-variabeln är lika med eller större än `ConfirmImpact` inställningen för cmdleten eller providern.</span><span class="sxs-lookup"><span data-stu-id="fca89-106">If `Confirm` is not specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation if the `$ConfirmPreference` preference variable is equal to or greater than the `ConfirmImpact` setting of the cmdlet or provider.</span></span> <span data-ttu-id="fca89-107">Standardinställningen `$ConfirmPreference` är hög.</span><span class="sxs-lookup"><span data-stu-id="fca89-107">The default setting of `$ConfirmPreference` is High.</span></span> <span data-ttu-id="fca89-108">I Standard miljön är det därför bara-cmdletar och-providers som anger en bekräftelse av åtgärden som kräver hög påverkan.</span><span class="sxs-lookup"><span data-stu-id="fca89-108">Therefore, in the default environment, only cmdlets and providers that specify a high-impact action request confirmation.</span></span>

<span data-ttu-id="fca89-109">Om `Confirm` har värdet False eller om `"-Confirm:$false` har angetts, begär anropet [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) från användaren och Shell- `$ConfirmPreference` variabeln ignoreras.</span><span class="sxs-lookup"><span data-stu-id="fca89-109">If `Confirm` is false or if `"-Confirm:$false` is specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation from the user, and the `$ConfirmPreference` shell variable is ignored.</span></span>

## <a name="remarks"></a><span data-ttu-id="fca89-110">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="fca89-110">Remarks</span></span>

- <span data-ttu-id="fca89-111">För-cmdletar och-providers som anger `SupportsShouldProcess` , men inte `ConfirmImpact` , hanteras dessa åtgärder som "medelhög påverkan"-åtgärder och de kommer inte att fråga som standard.</span><span class="sxs-lookup"><span data-stu-id="fca89-111">For cmdlets and providers that specify `SupportsShouldProcess`, but not `ConfirmImpact`, those actions are handled as "medium impact" actions, and they will not prompt by default.</span></span> <span data-ttu-id="fca89-112">Deras effekt nivå är mindre än standardinställningen för `$ConfirmPreference` variabeln Preference.</span><span class="sxs-lookup"><span data-stu-id="fca89-112">Their impact level is less than the default setting of the `$ConfirmPreference` preference variable.</span></span>

- <span data-ttu-id="fca89-113">Om användaren anger `Verbose` parametern kommer de att meddelas om åtgärden även om de inte behöver bekräftas.</span><span class="sxs-lookup"><span data-stu-id="fca89-113">If the user specifies the `Verbose` parameter, they will be notified of the operation even if they are not prompted for confirmation.</span></span>

## <a name="see-also"></a><span data-ttu-id="fca89-114">Se även</span><span class="sxs-lookup"><span data-stu-id="fca89-114">See Also</span></span>

[<span data-ttu-id="fca89-115">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="fca89-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
