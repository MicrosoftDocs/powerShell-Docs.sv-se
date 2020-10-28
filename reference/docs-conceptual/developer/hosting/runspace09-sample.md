---
ms.date: 09/13/2016
ms.topic: reference
title: Runspace09 – exempel
description: Runspace09 – exempel
ms.openlocfilehash: 8dedc3e2ee7c1d41f7b7ad367d8cebeb5f58b8e9
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92657609"
---
# <a name="runspace09-sample"></a><span data-ttu-id="11724-103">Runspace09 – exempel</span><span class="sxs-lookup"><span data-stu-id="11724-103">Runspace09 Sample</span></span>

<span data-ttu-id="11724-104">Det här exemplet visar hur du lägger till ett skript i pipelinen för ett [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -objekt och hur du kör skriptet asynkront.</span><span class="sxs-lookup"><span data-stu-id="11724-104">This sample shows how to add a script to the pipeline of a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object and how to run the script asynchronously.</span></span> <span data-ttu-id="11724-105">Händelser används för att hantera utdata från skriptet.</span><span class="sxs-lookup"><span data-stu-id="11724-105">Events are used to handle the output of the script.</span></span>

## <a name="requirements"></a><span data-ttu-id="11724-106">Krav</span><span class="sxs-lookup"><span data-stu-id="11724-106">Requirements</span></span>

<span data-ttu-id="11724-107">Det här exemplet kräver Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="11724-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="11724-108">Demonstrationer</span><span class="sxs-lookup"><span data-stu-id="11724-108">Demonstrates</span></span>

<span data-ttu-id="11724-109">Det här exemplet demonstrerar följande.</span><span class="sxs-lookup"><span data-stu-id="11724-109">This sample demonstrates the following.</span></span>

- <span data-ttu-id="11724-110">Skapar ett [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -objekt som använder körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="11724-110">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the runspace.</span></span>

- <span data-ttu-id="11724-111">Lägga till ett skript i pipeline för objektet [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="11724-111">Adding a script the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="11724-112">Använda metoden [system. Management. Automation. PowerShell. BeginInvoke \*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) för att köra pipelinen asynkront.</span><span class="sxs-lookup"><span data-stu-id="11724-112">Using the [System.Management.Automation.Powershell.Begininvoke\*](/dotnet/api/System.Management.Automation.PowerShell.BeginInvoke) method to run the pipeline asynchronously.</span></span>

- <span data-ttu-id="11724-113">Med hjälp av händelserna i objektet [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) kan du bearbeta utdata från skriptet.</span><span class="sxs-lookup"><span data-stu-id="11724-113">Using the events of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to process the output of the script.</span></span>

- <span data-ttu-id="11724-114">Använd metoden [system. Management. Automation. PowerShell. stop \*](/dotnet/api/System.Management.Automation.PowerShell.Stop) för att avbryta anropet av pipelinen.</span><span class="sxs-lookup"><span data-stu-id="11724-114">Using the [System.Management.Automation.Powershell.Stop\*](/dotnet/api/System.Management.Automation.PowerShell.Stop) method to interrupt the invocation of the pipeline.</span></span>

## <a name="example"></a><span data-ttu-id="11724-115">Exempel</span><span class="sxs-lookup"><span data-stu-id="11724-115">Example</span></span>

<span data-ttu-id="11724-116">Det här exemplet körs för att köra ett skript som genererar talen från 1 till 10 med fördröjningar mellan varje tal.</span><span class="sxs-lookup"><span data-stu-id="11724-116">This sample runs to run a script that generates the numbers from 1 to 10 with delays between each number.</span></span> <span data-ttu-id="11724-117">Skriptet körs asynkront och händelser används för att hantera utdata.</span><span class="sxs-lookup"><span data-stu-id="11724-117">The script is run asynchronously and events are used to handle the output.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.Generic;
  using System.Collections.ObjectModel;
  using System.Diagnostics;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace09
  {
    /// <summary>
    /// This sample shows how to use a PowerShell object to run a
    /// script that generates the numbers from 1 to 10 with delays
    /// between each number. The pipeline of the PowerShell object
    /// is run asynchronously and events are used to handle the output.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object.
    /// 2. Adding a script to the pipeline of the PowerShell object.
    /// 3. Using the BeginInvoke method to run the pipeline asynchronously.
    /// 4. Using the events of the PowerShell object to process the
    ///    output of the script.
    /// 5. Using the PowerShell.Stop() method to interrupt the invocation of
    ///    the pipeline.
    /// </remarks>
    private static void Main(string[] args)
    {
      Console.WriteLine("Print the numbers from 1 to 10. Hit any key to halt processing\n");

      using (PowerShell powershell = PowerShell.Create())
      {
        // Add a script to the PowerShell object. The script generates the
        // numbers from 1 to 10 in half second intervals.
        powershell.AddScript("1..10 | foreach {$_ ; start-sleep -milli 500}");

        // Add the event handlers.  If we did not care about hooking the DataAdded
        // event, we would let BeginInvoke create the output stream for us.
        PSDataCollection<PSObject> output = new PSDataCollection<PSObject>();
        output.DataAdded += new EventHandler<DataAddedEventArgs>(Output_DataAdded);
        powershell.InvocationStateChanged += new EventHandler<PSInvocationStateChangedEventArgs>(Powershell_InvocationStateChanged);

        // Invoke the pipeline asynchronously.
        IAsyncResult asyncResult = powershell.BeginInvoke<PSObject, PSObject>(null, output);

        // Wait for things to happen. If the user hits a key before the
        // script has completed, then call the PowerShell Stop() method
        // to halt processing.
        Console.ReadKey();
        if (powershell.InvocationStateInfo.State != PSInvocationState.Completed)
        {
          // Stop the invocation of the pipeline.
          Console.WriteLine("\nStopping the pipeline!\n");
          powershell.Stop();

          // Wait for the Windows PowerShell state change messages to be displayed.
          System.Threading.Thread.Sleep(500);
          Console.WriteLine("\nPress a key to exit");
          Console.ReadKey();
        }
      }
    }

    /// <summary>
    /// The output data added event handler. This event is called when
    /// data is added to the output pipe. It reads the data that is
    /// available and displays it on the console.
    /// </summary>
    /// <param name="sender">The output pipe this event is associated with.</param>
    /// <param name="e">Parameter is not used.</param>
    private static void Output_DataAdded(object sender, DataAddedEventArgs e)
    {
      PSDataCollection<PSObject> myp = (PSDataCollection<PSObject>)sender;

      Collection<PSObject> results = myp.ReadAll();
      foreach (PSObject result in results)
      {
        Console.WriteLine(result.ToString());
      }
    }

    /// <summary>
    /// This event handler is called when the pipeline state is changed.
    /// If the state change is to Completed, the handler issues a message
    /// asking the user to exit the program.
    /// </summary>
    /// <param name="sender">This parameter is not used.</param>
    /// <param name="e">The PowerShell state information.</param>
    private static void Powershell_InvocationStateChanged(object sender, PSInvocationStateChangedEventArgs e)
    {
      Console.WriteLine("PowerShell object state changed: state: {0}\n", e.InvocationStateInfo.State);
      if (e.InvocationStateInfo.State == PSInvocationState.Completed)
      {
        Console.WriteLine("Processing completed, press a key to exit!");
      }
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="11724-118">Se även</span><span class="sxs-lookup"><span data-stu-id="11724-118">See Also</span></span>

[<span data-ttu-id="11724-119">Skriva ett Windows PowerShell-värdprogram</span><span class="sxs-lookup"><span data-stu-id="11724-119">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
