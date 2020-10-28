---
ms.date: 09/13/2016
ms.topic: reference
title: Begära bekräftelser
description: Begära bekräftelser
ms.openlocfilehash: 3e29803407bd9fbf13e6db0d0a02239c34e9c4fa
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667002"
---
# <a name="how-to-request-confirmations"></a><span data-ttu-id="51222-103">Begära bekräftelser</span><span class="sxs-lookup"><span data-stu-id="51222-103">How to Request Confirmations</span></span>

<span data-ttu-id="51222-104">Det här exemplet visar hur du anropar metoderna [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) för att begära bekräftelser från användaren innan en åtgärd vidtas.</span><span class="sxs-lookup"><span data-stu-id="51222-104">This example shows how to call the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods to request confirmations from the user before an action is taken.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="51222-105">Mer information om hur Windows PowerShell hanterar dessa förfrågningar finns i [begära bekräftelse](./requesting-confirmation-from-cmdlets.md).</span><span class="sxs-lookup"><span data-stu-id="51222-105">For more information about how Windows PowerShell handles these requests, see [Requesting Confirmation](./requesting-confirmation-from-cmdlets.md).</span></span>

## <a name="to-request-confirmation"></a><span data-ttu-id="51222-106">Att begära bekräftelse</span><span class="sxs-lookup"><span data-stu-id="51222-106">To request confirmation</span></span>

1. <span data-ttu-id="51222-107">Se till att `SupportsShouldProcess` parametern för cmdlet-attributet är inställt på `true` .</span><span class="sxs-lookup"><span data-stu-id="51222-107">Ensure that the `SupportsShouldProcess` parameter of the Cmdlet attribute is set to `true`.</span></span> <span data-ttu-id="51222-108">(För functions är det en parameter för attributet CmdletBinding.)</span><span class="sxs-lookup"><span data-stu-id="51222-108">(For functions this is a parameter of the CmdletBinding attribute.)</span></span>

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. <span data-ttu-id="51222-109">Lägg till en `Force` parameter till din cmdlet så att användaren kan åsidosätta en bekräftelse förfrågan.</span><span class="sxs-lookup"><span data-stu-id="51222-109">Add a `Force` parameter to your cmdlet so that the user can override a confirmation request.</span></span>

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. <span data-ttu-id="51222-110">Lägg till en `if` instruktion som använder returvärdet för metoden [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) för att avgöra om metoden [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) anropas.</span><span class="sxs-lookup"><span data-stu-id="51222-110">Add an `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method to determine if the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method is called.</span></span>

4. <span data-ttu-id="51222-111">Lägg till en andra `if` instruktion som använder returvärdet för metoden [system. Management. Automation. cmdlet. ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) och värdet för `Force` parametern för att avgöra om åtgärden ska utföras.</span><span class="sxs-lookup"><span data-stu-id="51222-111">Add a second `if` statement that uses the return value of the [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) method and the value of the `Force` parameter to determine whether the operation should be performed.</span></span>

## <a name="example"></a><span data-ttu-id="51222-112">Exempel</span><span class="sxs-lookup"><span data-stu-id="51222-112">Example</span></span>

<span data-ttu-id="51222-113">I följande kod exempel anropas metoderna [system. Management. Automation. cmdlet. ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) och [system. Management](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) . Automation. cmdlet. ShouldContinue från åsidosättningen av metoden [system. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) .</span><span class="sxs-lookup"><span data-stu-id="51222-113">In the following code example, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) and [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) methods are called from within the override of the [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) method.</span></span> <span data-ttu-id="51222-114">Men du kan också anropa dessa metoder från andra metoder för bearbetning av indata.</span><span class="sxs-lookup"><span data-stu-id="51222-114">However, you can also call these methods from the other input processing methods.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="51222-115">Se även</span><span class="sxs-lookup"><span data-stu-id="51222-115">See Also</span></span>

[<span data-ttu-id="51222-116">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="51222-116">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
