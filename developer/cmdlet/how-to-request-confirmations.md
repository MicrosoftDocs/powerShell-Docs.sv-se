---
title: Hur du begär bekräftelser | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f24f77d5-e224-4b62-b128-535e045d333e
caps.latest.revision: 9
ms.openlocfilehash: 19e96b612a8778d82cdbafb528a7ffeb01f15f99
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067849"
---
# <a name="how-to-request-confirmations"></a><span data-ttu-id="ef300-102">Begära bekräftelser</span><span class="sxs-lookup"><span data-stu-id="ef300-102">How to Request Confirmations</span></span>

<span data-ttu-id="ef300-103">Det här exemplet visar hur du anropar den [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metoder för att begära bekräftelser från den användaren innan en åtgärd utförs.</span><span class="sxs-lookup"><span data-stu-id="ef300-103">This example shows how to call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to request confirmations from the user before an action is taken.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ef300-104">Läs mer om hur Windows PowerShell hanterar dessa begäranden [begär bekräftelse](./requesting-confirmation-from-cmdlets.md).</span><span class="sxs-lookup"><span data-stu-id="ef300-104">For more information about how Windows PowerShell handles these requests, see [Requesting Confirmation](./requesting-confirmation-from-cmdlets.md).</span></span>

## <a name="to-request-confirmation"></a><span data-ttu-id="ef300-105">Begär bekräftelse</span><span class="sxs-lookup"><span data-stu-id="ef300-105">To request confirmation</span></span>

1. <span data-ttu-id="ef300-106">Se till att den `SupportsShouldProcess` parametern för Cmdlet-attributet är inställd på `true`.</span><span class="sxs-lookup"><span data-stu-id="ef300-106">Ensure that the `SupportsShouldProcess` parameter of the Cmdlet attribute is set to `true`.</span></span> <span data-ttu-id="ef300-107">(För det här är en parameter av CmdletBinding-attribut.)</span><span class="sxs-lookup"><span data-stu-id="ef300-107">(For functions this is a parameter of the CmdletBinding attribute.)</span></span>

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. <span data-ttu-id="ef300-108">Lägg till en `Force` parameter i cmdlet: så att användaren kan åsidosätta en begäran om händelsebekräftelse.</span><span class="sxs-lookup"><span data-stu-id="ef300-108">Add a `Force` parameter to your cmdlet so that the user can override a confirmation request.</span></span>

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. <span data-ttu-id="ef300-109">Lägg till en `if` instruktion som använder returvärdet för den [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) metod för att avgöra om den [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metoden anropas.</span><span class="sxs-lookup"><span data-stu-id="ef300-109">Add an `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to determine if the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is called.</span></span>

4. <span data-ttu-id="ef300-110">Lägg till en andra `if` instruktion som använder returvärdet för den [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metoden och värdet för den `Force` parametern för att avgöra om åtgärden bör vara utföra.</span><span class="sxs-lookup"><span data-stu-id="ef300-110">Add a second `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method and the value of the `Force` parameter to determine whether the operation should be performed.</span></span>

## <a name="example"></a><span data-ttu-id="ef300-111">Exempel</span><span class="sxs-lookup"><span data-stu-id="ef300-111">Example</span></span>

<span data-ttu-id="ef300-112">I följande kodexempel i [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) metoder som anropas från inom åsidosättningen av den [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) metod.</span><span class="sxs-lookup"><span data-stu-id="ef300-112">In the following code example, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods are called from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="ef300-113">Du kan också anropa metoderna från andra indata metoderna.</span><span class="sxs-lookup"><span data-stu-id="ef300-113">However, you can also call these methods from the other input processing methods.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ef300-114">Se även</span><span class="sxs-lookup"><span data-stu-id="ef300-114">See Also</span></span>

[<span data-ttu-id="ef300-115">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ef300-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
