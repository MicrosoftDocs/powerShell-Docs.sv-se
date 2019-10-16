---
title: Så här anropar du en cmdlet inifrån en cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: efa4dc9c-ddee-46a3-978a-9dbb61e9bb6f
caps.latest.revision: 12
ms.openlocfilehash: 57543a88d04eb66c9d109249a99ddd272b02ef9d
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356310"
---
# <a name="how-to-invoke-a-cmdlet-from-within-a-cmdlet"></a><span data-ttu-id="d2776-102">Anropa en cmdlet inifrån en cmdlet</span><span class="sxs-lookup"><span data-stu-id="d2776-102">How to Invoke a Cmdlet from Within a Cmdlet</span></span>

<span data-ttu-id="d2776-103">Det här exemplet visar hur du anropar en cmdlet från en annan cmdlet, vilket gör att du kan lägga till funktionerna i den anropade cmdleten till den cmdlet som du utvecklar.</span><span class="sxs-lookup"><span data-stu-id="d2776-103">This example shows how to invoke a cmdlet from within another cmdlet, which allows you to add the functionality of the invoked cmdlet to the cmdlet you are developing.</span></span> <span data-ttu-id="d2776-104">I det här exemplet anropas cmdleten `Get-Process` för att hämta de processer som körs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="d2776-104">In this example, the `Get-Process` cmdlet is invoked to get the processes that are running on the local computer.</span></span> <span data-ttu-id="d2776-105">Anropet till `Get-Process`-cmdleten motsvarar följande kommando.</span><span class="sxs-lookup"><span data-stu-id="d2776-105">The call to the `Get-Process` cmdlet is equivalent to the following command.</span></span> <span data-ttu-id="d2776-106">Det här kommandot hämtar alla processer vars namn börjar med tecknen "a" till "t".</span><span class="sxs-lookup"><span data-stu-id="d2776-106">This command retrieves all the processes whose names start with the characters "a" through "t".</span></span>

```powershell
Get-Process -name [a-t]
```

> [!IMPORTANT]
> <span data-ttu-id="d2776-107">Du kan bara anropa de cmdlet: ar som härleds direkt från klassen [system. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) .</span><span class="sxs-lookup"><span data-stu-id="d2776-107">You can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="d2776-108">Det går inte att anropa en cmdlet som härleds från klassen [system. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .</span><span class="sxs-lookup"><span data-stu-id="d2776-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

## <a name="to-invoke-a-cmdlet-from-within-a-cmdlet"></a><span data-ttu-id="d2776-109">Anropa en cmdlet inifrån en cmdlet</span><span class="sxs-lookup"><span data-stu-id="d2776-109">To invoke a cmdlet from within a cmdlet</span></span>

1. <span data-ttu-id="d2776-110">Kontrol lera att sammansättningen som definierar den cmdlet som ska anropas refereras och att rätt `using`-instruktion läggs till.</span><span class="sxs-lookup"><span data-stu-id="d2776-110">Ensure that the assembly that defines the cmdlet to be invoked is referenced and that the appropriate `using` statement is added.</span></span> <span data-ttu-id="d2776-111">I det här exemplet läggs följande namn områden till.</span><span class="sxs-lookup"><span data-stu-id="d2776-111">In this example, the following namespaces are added.</span></span>

    ```csharp
    using System.Diagnostics;
    using System.Management.Automation;   // Windows PowerShell assembly.
    using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.
    ```

2. <span data-ttu-id="d2776-112">Skapa en ny instans av cmdleten som ska anropas i den ingångs bearbetnings metoden för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="d2776-112">In the input processing method of the cmdlet, create a new instance of the cmdlet to be invoked.</span></span> <span data-ttu-id="d2776-113">I det här exemplet skapas ett objekt av typen [Microsoft. PowerShell. commands. Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) tillsammans med strängen som innehåller de argument som används när cmdleten anropas.</span><span class="sxs-lookup"><span data-stu-id="d2776-113">In this example, an object of type [Microsoft.PowerShell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) is created along with the string that contains the arguments that are used when the cmdlet is invoked.</span></span>

    ```csharp
    GetProcessCommand gp = new GetProcessCommand();
    gp.Name = new string[] { "[a-t]*" };
    ```

3. <span data-ttu-id="d2776-114">Anropa metoden [system. Management. Automation. cmdlet. Invoke \*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) för att anropa `Get-Process`-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="d2776-114">Call the [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method to invoke the `Get-Process` cmdlet.</span></span>

    ```csharp
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }
    ```

## <a name="example"></a><span data-ttu-id="d2776-115">Exempel</span><span class="sxs-lookup"><span data-stu-id="d2776-115">Example</span></span>

<span data-ttu-id="d2776-116">I det här exemplet anropas cmdleten `Get-Process` inifrån metoden [system. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d2776-116">In this example, the `Get-Process` cmdlet is invoked from within the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method of a cmdlet.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;   // Windows PowerShell assembly.
using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.

namespace SendGreeting
{
  // Declare the class as a cmdlet and specify an
  // appropriate verb and noun for the cmdlet name.
  [Cmdlet(VerbsCommunications.Send, "GreetingInvoke")]
  public class SendGreetingInvokeCommand : Cmdlet
  {
    // Declare the parameters for the cmdlet.
    [Parameter(Mandatory = true)]
    public string Name
    {
      get { return name; }
      set { name = value; }
    }
    private string name;

    // Override the BeginProcessing method to invoke
    // the Get-Process cmdlet.
    protected override void BeginProcessing()
    {
      GetProcessCommand gp = new GetProcessCommand();
      gp.Name = new string[] { "[a-t]*" };
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }

    // Override the ProcessRecord method to process
    // the supplied user name and write out a
    // greeting to the user by calling the WriteObject
    // method.
    protected override void ProcessRecord()
    {
      WriteObject("Hello " + name + "!");
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="d2776-117">Se även</span><span class="sxs-lookup"><span data-stu-id="d2776-117">See Also</span></span>

[<span data-ttu-id="d2776-118">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="d2776-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
