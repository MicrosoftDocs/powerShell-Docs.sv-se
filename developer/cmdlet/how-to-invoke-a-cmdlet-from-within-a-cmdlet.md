---
title: Hur du anropar en Cmdlet från inom en Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: efa4dc9c-ddee-46a3-978a-9dbb61e9bb6f
caps.latest.revision: 12
ms.openlocfilehash: 57543a88d04eb66c9d109249a99ddd272b02ef9d
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055911"
---
# <a name="how-to-invoke-a-cmdlet-from-within-a-cmdlet"></a><span data-ttu-id="915e1-102">Anropa en cmdlet inifrån en cmdlet</span><span class="sxs-lookup"><span data-stu-id="915e1-102">How to Invoke a Cmdlet from Within a Cmdlet</span></span>

<span data-ttu-id="915e1-103">Det här exemplet visar hur du anropar en cmdlet från inom en annan cmdlet, där du kan lägga till funktioner för anropade cmdlet: en till den cmdlet som du utvecklar.</span><span class="sxs-lookup"><span data-stu-id="915e1-103">This example shows how to invoke a cmdlet from within another cmdlet, which allows you to add the functionality of the invoked cmdlet to the cmdlet you are developing.</span></span> <span data-ttu-id="915e1-104">I det här exemplet på `Get-Process` cmdlet anropas för att få de processer som körs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="915e1-104">In this example, the `Get-Process` cmdlet is invoked to get the processes that are running on the local computer.</span></span> <span data-ttu-id="915e1-105">Anropet till den `Get-Process` cmdlet är likvärdiga med följande kommando.</span><span class="sxs-lookup"><span data-stu-id="915e1-105">The call to the `Get-Process` cmdlet is equivalent to the following command.</span></span> <span data-ttu-id="915e1-106">Detta kommando hämtar alla processer med namn som börjar med tecknen ”a” till ”t”.</span><span class="sxs-lookup"><span data-stu-id="915e1-106">This command retrieves all the processes whose names start with the characters "a" through "t".</span></span>

```powershell
Get-Process -name [a-t]
```

> [!IMPORTANT]
> <span data-ttu-id="915e1-107">Du kan anropa dessa cmdlets som härleds direkt från den [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) klass.</span><span class="sxs-lookup"><span data-stu-id="915e1-107">You can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="915e1-108">Du kan inte anropa en cmdlet som härleds från den [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) klass.</span><span class="sxs-lookup"><span data-stu-id="915e1-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

## <a name="to-invoke-a-cmdlet-from-within-a-cmdlet"></a><span data-ttu-id="915e1-109">Anropa en cmdlet från inom en cmdlet</span><span class="sxs-lookup"><span data-stu-id="915e1-109">To invoke a cmdlet from within a cmdlet</span></span>

1. <span data-ttu-id="915e1-110">Se till att sammansättningen som definierar cmdlet anropas refereras och att rätt `using` instruktionen har lagts till.</span><span class="sxs-lookup"><span data-stu-id="915e1-110">Ensure that the assembly that defines the cmdlet to be invoked is referenced and that the appropriate `using` statement is added.</span></span> <span data-ttu-id="915e1-111">I det här exemplet läggs följande namnrymder.</span><span class="sxs-lookup"><span data-stu-id="915e1-111">In this example, the following namespaces are added.</span></span>

    ```csharp
    using System.Diagnostics;
    using System.Management.Automation;   // Windows PowerShell assembly.
    using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.
    ```

2. <span data-ttu-id="915e1-112">Skapa en ny instans av cmdlet anropas i den inkommande metoden-cmdlet: ens bearbetades.</span><span class="sxs-lookup"><span data-stu-id="915e1-112">In the input processing method of the cmdlet, create a new instance of the cmdlet to be invoked.</span></span> <span data-ttu-id="915e1-113">I det här exemplet, ett objekt av typen [Microsoft.PowerShell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) skapas tillsammans med den sträng som innehåller de argument som används när cmdleten har anropats.</span><span class="sxs-lookup"><span data-stu-id="915e1-113">In this example, an object of type [Microsoft.PowerShell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) is created along with the string that contains the arguments that are used when the cmdlet is invoked.</span></span>

    ```csharp
    GetProcessCommand gp = new GetProcessCommand();
    gp.Name = new string[] { "[a-t]*" };
    ```

3. <span data-ttu-id="915e1-114">Anropa den [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) metoden för att anropa den `Get-Process` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="915e1-114">Call the [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method to invoke the `Get-Process` cmdlet.</span></span>

    ```csharp
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }
    ```

## <a name="example"></a><span data-ttu-id="915e1-115">Exempel</span><span class="sxs-lookup"><span data-stu-id="915e1-115">Example</span></span>

<span data-ttu-id="915e1-116">I det här exemplet på `Get-Process` cmdlet anropas inifrån den [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) -metoden för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="915e1-116">In this example, the `Get-Process` cmdlet is invoked from within the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method of a cmdlet.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="915e1-117">Se även</span><span class="sxs-lookup"><span data-stu-id="915e1-117">See Also</span></span>

[<span data-ttu-id="915e1-118">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="915e1-118">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
