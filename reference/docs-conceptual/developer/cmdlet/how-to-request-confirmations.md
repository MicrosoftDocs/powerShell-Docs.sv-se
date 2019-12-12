---
title: Så här begär du bekräftelser | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f24f77d5-e224-4b62-b128-535e045d333e
caps.latest.revision: 9
ms.openlocfilehash: 19e96b612a8778d82cdbafb528a7ffeb01f15f99
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359336"
---
# <a name="how-to-request-confirmations"></a><span data-ttu-id="24e5a-102">Begära bekräftelser</span><span class="sxs-lookup"><span data-stu-id="24e5a-102">How to Request Confirmations</span></span>

<span data-ttu-id="24e5a-103">Det här exemplet visar hur du anropar metoderna [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) för att begära bekräftelser från användaren innan en åtgärd vidtas.</span><span class="sxs-lookup"><span data-stu-id="24e5a-103">This example shows how to call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to request confirmations from the user before an action is taken.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="24e5a-104">Mer information om hur Windows PowerShell hanterar dessa förfrågningar finns i [begära bekräftelse](./requesting-confirmation-from-cmdlets.md).</span><span class="sxs-lookup"><span data-stu-id="24e5a-104">For more information about how Windows PowerShell handles these requests, see [Requesting Confirmation](./requesting-confirmation-from-cmdlets.md).</span></span>

## <a name="to-request-confirmation"></a><span data-ttu-id="24e5a-105">Att begära bekräftelse</span><span class="sxs-lookup"><span data-stu-id="24e5a-105">To request confirmation</span></span>

1. <span data-ttu-id="24e5a-106">Se till att parametern `SupportsShouldProcess` för cmdlet-attributet är inställd på `true`.</span><span class="sxs-lookup"><span data-stu-id="24e5a-106">Ensure that the `SupportsShouldProcess` parameter of the Cmdlet attribute is set to `true`.</span></span> <span data-ttu-id="24e5a-107">(För functions är det en parameter för attributet CmdletBinding.)</span><span class="sxs-lookup"><span data-stu-id="24e5a-107">(For functions this is a parameter of the CmdletBinding attribute.)</span></span>

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. <span data-ttu-id="24e5a-108">Lägg till en `Force`-parameter till din cmdlet så att användaren kan åsidosätta en bekräftelse förfrågan.</span><span class="sxs-lookup"><span data-stu-id="24e5a-108">Add a `Force` parameter to your cmdlet so that the user can override a confirmation request.</span></span>

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. <span data-ttu-id="24e5a-109">Lägg till en `if`-instruktion som använder returvärdet för metoden [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) för att avgöra om metoden [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) anropas.</span><span class="sxs-lookup"><span data-stu-id="24e5a-109">Add an `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to determine if the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is called.</span></span>

4. <span data-ttu-id="24e5a-110">Lägg till en andra `if`-instruktion som använder returvärdet för metoden [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) och värdet för parametern `Force` för att avgöra om åtgärden ska utföras.</span><span class="sxs-lookup"><span data-stu-id="24e5a-110">Add a second `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method and the value of the `Force` parameter to determine whether the operation should be performed.</span></span>

## <a name="example"></a><span data-ttu-id="24e5a-111">Exempel</span><span class="sxs-lookup"><span data-stu-id="24e5a-111">Example</span></span>

<span data-ttu-id="24e5a-112">I följande kod exempel anropas metoderna [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [system. Management](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) . Automation. cmdlet. ShouldContinue från åsidosättningen av metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="24e5a-112">In the following code example, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods are called from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="24e5a-113">Men du kan också anropa dessa metoder från andra metoder för bearbetning av indata.</span><span class="sxs-lookup"><span data-stu-id="24e5a-113">However, you can also call these methods from the other input processing methods.</span></span>

```csharp
protected override void ProcessRecord()
{
  if (ShouldProcess("ShouldProcess target"))
  {
    if (Force || ShouldContinue("", ""))
    {
      // Add code that performs the operation.
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="24e5a-114">Se även</span><span class="sxs-lookup"><span data-stu-id="24e5a-114">See Also</span></span>

[<span data-ttu-id="24e5a-115">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="24e5a-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
