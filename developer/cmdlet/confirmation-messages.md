---
title: Bekräftelsemeddelanden | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a886a26d-7730-4586-aeac-fd3f0bc60b88
caps.latest.revision: 8
ms.openlocfilehash: 229725b5b9f1f0082592dcebe11564fd2f630ce1
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059481"
---
# <a name="confirmation-messages"></a><span data-ttu-id="f8c5e-102">Bekräftelsemeddelanden</span><span class="sxs-lookup"><span data-stu-id="f8c5e-102">Confirmation Messages</span></span>

<span data-ttu-id="f8c5e-103">Här följer olika bekräftelsemeddelanden som kan visas beroende på varianter av den [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [System.Management.Automation.Cmdlet.ShouldContinue ](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metoder som anropas.</span><span class="sxs-lookup"><span data-stu-id="f8c5e-103">Here are different confirmation messages that can be displayed depending on the variants of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods that are called.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f8c5e-104">Exempelkod som visar hur du begär bekräftelser, se [så begäran bekräftelser](./how-to-request-confirmations.md).</span><span class="sxs-lookup"><span data-stu-id="f8c5e-104">For sample code that shows how to request confirmations, see [How to Request Confirmations](./how-to-request-confirmations.md).</span></span>

## <a name="specifying-the-resource"></a><span data-ttu-id="f8c5e-105">Att ange resursen</span><span class="sxs-lookup"><span data-stu-id="f8c5e-105">Specifying the Resource</span></span>

<span data-ttu-id="f8c5e-106">Du kan ange den resurs som håller på att ändras genom att anropa den [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) metod.</span><span class="sxs-lookup"><span data-stu-id="f8c5e-106">You can specify the resource that is about to be changed by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="f8c5e-107">I så fall kan du ange resursen med hjälp av den `target` -parametern för metoden och åtgärden läggs till av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f8c5e-107">In this case, you supply the resource by using the `target` parameter of the method, and the operation is added by Windows PowerShell.</span></span> <span data-ttu-id="f8c5e-108">I ett meddelande om texten ”MyResource” är den resurs som kördes på och åtgärden är namnet på det kommando som gör anropet.</span><span class="sxs-lookup"><span data-stu-id="f8c5e-108">In the following message, the text "MyResource" is the resource acted on and the operation is the name of the command that makes the call.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="f8c5e-109">Om användaren väljer **Ja** eller **Ja till alla** bekräftelsen be (som visas i följande exempel), ett anrop till den [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue)metoden görs, vilket leder till ett andra bekräftelsemeddelande som ska visas.</span><span class="sxs-lookup"><span data-stu-id="f8c5e-109">If the user selects **Yes** or **Yes to All** to the confirmation request (as shown in the following example), a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a><span data-ttu-id="f8c5e-110">Anger åtgärden och resurs</span><span class="sxs-lookup"><span data-stu-id="f8c5e-110">Specifying the Operation and Resource</span></span>

<span data-ttu-id="f8c5e-111">Du kan ange den resurs som håller på att ändras och åtgärden som kommandot håller på att utföra genom att anropa den [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) metod.</span><span class="sxs-lookup"><span data-stu-id="f8c5e-111">You can specify the resource that is about to be changed and the operation that the command is about to perform by calling the [System.Management.Automation.Cmdlet.Shouldprocess%2A?Displayproperty=Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) method.</span></span> <span data-ttu-id="f8c5e-112">I så fall kan du ange resursen med hjälp av den `target` parametern och åtgärden med hjälp av den `target` parametern.</span><span class="sxs-lookup"><span data-stu-id="f8c5e-112">In this case, you supply the resource by using the `target` parameter and the operation by using the `target` parameter.</span></span> <span data-ttu-id="f8c5e-113">I ett meddelande om texten ”MyResource” är den resurs som kördes på och ”MyAction” är en åtgärd som ska utföras.</span><span class="sxs-lookup"><span data-stu-id="f8c5e-113">In the following message, the text "MyResource" is the resource acted on and "MyAction" is the operation to be performed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="f8c5e-114">Om användaren väljer **Ja** eller **Ja till alla** till föregående meddelande, ett anrop till den [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metoden görs, som orsakar en andra bekräftelsemeddelande som ska visas.</span><span class="sxs-lookup"><span data-stu-id="f8c5e-114">If the user selects **Yes** or **Yes to All** to the previous message, a call to the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is made, which causes a second confirmation message to be displayed.</span></span>

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a><span data-ttu-id="f8c5e-115">Se även</span><span class="sxs-lookup"><span data-stu-id="f8c5e-115">See Also</span></span>

[<span data-ttu-id="f8c5e-116">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f8c5e-116">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
