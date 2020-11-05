---
ms.date: 09/13/2016
ms.topic: reference
title: Bekräftelsemeddelanden
description: Bekräftelsemeddelanden
ms.openlocfilehash: 76302b2f8d8ca6dcdfe1b3c36f71aad23a53f7cf
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/05/2020
ms.locfileid: "93355195"
---
# <a name="confirmation-messages"></a><span data-ttu-id="2de39-103">Bekräftelsemeddelanden</span><span class="sxs-lookup"><span data-stu-id="2de39-103">Confirmation Messages</span></span>

<span data-ttu-id="2de39-104">Här är olika bekräftelse meddelanden som kan visas beroende på varianterna för [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) -metoder som anropas.</span><span class="sxs-lookup"><span data-stu-id="2de39-104">Here are different confirmation messages that can be displayed depending on the variants of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods that are called.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2de39-105">Exempel kod som visar hur du begär bekräftelser finns i [så här begär du bekräftelser](./how-to-request-confirmations.md).</span><span class="sxs-lookup"><span data-stu-id="2de39-105">For sample code that shows how to request confirmations, see [How to Request Confirmations](./how-to-request-confirmations.md).</span></span>

## <a name="specifying-the-resource"></a><span data-ttu-id="2de39-106">Ange resursen</span><span class="sxs-lookup"><span data-stu-id="2de39-106">Specifying the Resource</span></span>

<span data-ttu-id="2de39-107">Du kan ange den resurs som ska ändras genom att anropa [system. Management. Automation. cmdlet. ShouldProcess% 2a? Displayproperty = FullName](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -metoden.</span><span class="sxs-lookup"><span data-stu-id="2de39-107">You can specify the resource that is about to be changed by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method.</span></span> <span data-ttu-id="2de39-108">I det här fallet kan du ange resursen med hjälp av `target` -parametern för-metoden och åtgärden läggs till av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2de39-108">In this case, you supply the resource by using the `target` parameter of the method, and the operation is added by Windows PowerShell.</span></span> <span data-ttu-id="2de39-109">I följande meddelande är texten "min resurs" den resurs som är aktive ras och åtgärden är namnet på kommandot som gör anropet.</span><span class="sxs-lookup"><span data-stu-id="2de39-109">In the following message, the text "MyResource" is the resource acted on and the operation is the name of the command that makes the call.</span></span>

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="2de39-110">Om användaren väljer **Ja** eller **Ja till alla** i bekräftelse förfrågningen (som visas i följande exempel), görs ett anrop till metoden [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) , vilket gör att ett andra bekräftelse meddelande visas.</span><span class="sxs-lookup"><span data-stu-id="2de39-110">If the user selects **Yes** or **Yes to All** to the confirmation request (as shown in the following example), a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a><span data-ttu-id="2de39-111">Ange åtgärden och resursen</span><span class="sxs-lookup"><span data-stu-id="2de39-111">Specifying the Operation and Resource</span></span>

<span data-ttu-id="2de39-112">Du kan ange den resurs som ska ändras och åtgärden som kommandot ska utföra genom att anropa [system. Management. Automation. cmdlet. ShouldProcess% 2a? Displayproperty = FullName](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -metoden.</span><span class="sxs-lookup"><span data-stu-id="2de39-112">You can specify the resource that is about to be changed and the operation that the command is about to perform by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method.</span></span> <span data-ttu-id="2de39-113">I det här fallet kan du ange resursen med hjälp av- `target` parametern och åtgärden med hjälp av- `target` parametern.</span><span class="sxs-lookup"><span data-stu-id="2de39-113">In this case, you supply the resource by using the `target` parameter and the operation by using the `target` parameter.</span></span> <span data-ttu-id="2de39-114">I följande meddelande är texten "min resurs" den resurs som har åtgärd ATS och "mina åtgärder" är den åtgärd som ska utföras.</span><span class="sxs-lookup"><span data-stu-id="2de39-114">In the following message, the text "MyResource" is the resource acted on and "MyAction" is the operation to be performed.</span></span>

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="2de39-115">Om användaren väljer **Ja** eller **Ja till alla** i föregående meddelande, görs ett anrop till metoden [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) , vilket gör att ett andra bekräftelse meddelande visas.</span><span class="sxs-lookup"><span data-stu-id="2de39-115">If the user selects **Yes** or **Yes to All** to the previous message, a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```Output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a><span data-ttu-id="2de39-116">Se även</span><span class="sxs-lookup"><span data-stu-id="2de39-116">See Also</span></span>

[<span data-ttu-id="2de39-117">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="2de39-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
