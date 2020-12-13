---
ms.date: 09/13/2016
ms.topic: reference
title: Anropa en cmdlet inifrån en cmdlet
description: Anropa en cmdlet inifrån en cmdlet
ms.openlocfilehash: d137ac895f66000329de76a2c16a74b02c0e82ca
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667053"
---
# <a name="how-to-invoke-a-cmdlet-from-within-a-cmdlet"></a><span data-ttu-id="908d6-103">Anropa en cmdlet inifrån en cmdlet</span><span class="sxs-lookup"><span data-stu-id="908d6-103">How to Invoke a Cmdlet from Within a Cmdlet</span></span>

<span data-ttu-id="908d6-104">Det här exemplet visar hur du anropar en cmdlet från en annan cmdlet, vilket gör att du kan lägga till funktionerna i den anropade cmdleten till den cmdlet som du utvecklar.</span><span class="sxs-lookup"><span data-stu-id="908d6-104">This example shows how to invoke a cmdlet from within another cmdlet, which allows you to add the functionality of the invoked cmdlet to the cmdlet you are developing.</span></span> <span data-ttu-id="908d6-105">I det här exemplet `Get-Process` anropas cmdleten för att hämta de processer som körs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="908d6-105">In this example, the `Get-Process` cmdlet is invoked to get the processes that are running on the local computer.</span></span> <span data-ttu-id="908d6-106">Anropet till `Get-Process` cmdleten motsvarar följande kommando.</span><span class="sxs-lookup"><span data-stu-id="908d6-106">The call to the `Get-Process` cmdlet is equivalent to the following command.</span></span> <span data-ttu-id="908d6-107">Det här kommandot hämtar alla processer vars namn börjar med tecknen "a" till "t".</span><span class="sxs-lookup"><span data-stu-id="908d6-107">This command retrieves all the processes whose names start with the characters "a" through "t".</span></span>

```powershell
Get-Process -name [a-t]
```

> [!IMPORTANT]
> <span data-ttu-id="908d6-108">Du kan bara anropa de cmdlet: ar som härleds direkt från klassen [system. Management. Automation. cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) .</span><span class="sxs-lookup"><span data-stu-id="908d6-108">You can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="908d6-109">Det går inte att anropa en cmdlet som härleds från klassen [system. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) .</span><span class="sxs-lookup"><span data-stu-id="908d6-109">You cannot invoke a cmdlet that derives from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

## <a name="to-invoke-a-cmdlet-from-within-a-cmdlet"></a><span data-ttu-id="908d6-110">Anropa en cmdlet inifrån en cmdlet</span><span class="sxs-lookup"><span data-stu-id="908d6-110">To invoke a cmdlet from within a cmdlet</span></span>

1. <span data-ttu-id="908d6-111">Kontrol lera att sammansättningen som definierar den cmdlet som ska anropas refereras och att lämplig `using` instruktion läggs till.</span><span class="sxs-lookup"><span data-stu-id="908d6-111">Ensure that the assembly that defines the cmdlet to be invoked is referenced and that the appropriate `using` statement is added.</span></span> <span data-ttu-id="908d6-112">I det här exemplet läggs följande namn områden till.</span><span class="sxs-lookup"><span data-stu-id="908d6-112">In this example, the following namespaces are added.</span></span>

    ```csharp
    using System.Diagnostics;
    using System.Management.Automation;   // Windows PowerShell assembly.
    using Microsoft.PowerShell.Commands;  // Windows PowerShell assembly.
    ```

2. <span data-ttu-id="908d6-113">Skapa en ny instans av cmdleten som ska anropas i den ingångs bearbetnings metoden för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="908d6-113">In the input processing method of the cmdlet, create a new instance of the cmdlet to be invoked.</span></span> <span data-ttu-id="908d6-114">I det här exemplet skapas ett objekt av typen [Microsoft. PowerShell. commands. Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) tillsammans med strängen som innehåller de argument som används när cmdleten anropas.</span><span class="sxs-lookup"><span data-stu-id="908d6-114">In this example, an object of type [Microsoft.PowerShell.Commands.Getprocesscommand](/dotnet/api/Microsoft.PowerShell.Commands.GetProcessCommand) is created along with the string that contains the arguments that are used when the cmdlet is invoked.</span></span>

    ```csharp
    GetProcessCommand gp = new GetProcessCommand();
    gp.Name = new string[] { "[a-t]*" };
    ```

3. <span data-ttu-id="908d6-115">Anropa metoden [system. Management. Automation. cmdlet. Invoke \*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) för att anropa `Get-Process` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="908d6-115">Call the [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method to invoke the `Get-Process` cmdlet.</span></span>

    ```csharp
      foreach (Process p in gp.Invoke<Process>())
      {
        Console.WriteLine(p.ToString());
      }
    }
    ```

## <a name="example"></a><span data-ttu-id="908d6-116">Exempel</span><span class="sxs-lookup"><span data-stu-id="908d6-116">Example</span></span>

<span data-ttu-id="908d6-117">I det här exemplet `Get-Process` anropas cmdleten i metoden [system. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="908d6-117">In this example, the `Get-Process` cmdlet is invoked from within the [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) method of a cmdlet.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="908d6-118">Se även</span><span class="sxs-lookup"><span data-stu-id="908d6-118">See Also</span></span>

[<span data-ttu-id="908d6-119">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="908d6-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
