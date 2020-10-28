---
ms.date: 09/13/2016
ms.topic: reference
title: Runspace10 – exempel
description: Runspace10 – exempel
ms.openlocfilehash: fd58cea553e6b830a56df7edfa7901d39f46a06c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92657572"
---
# <a name="runspace10-sample"></a><span data-ttu-id="62741-103">Runspace10 – exempel</span><span class="sxs-lookup"><span data-stu-id="62741-103">Runspace10 Sample</span></span>

<span data-ttu-id="62741-104">Det här exemplet visar hur du skapar ett standard tillstånd för inledande session, hur du lägger till en cmdlet i [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState), hur du skapar en körnings utrymme som använder det inledande sessionstillståndet och hur du kör kommandot med hjälp av ett [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -objekt.</span><span class="sxs-lookup"><span data-stu-id="62741-104">This sample shows how to create a default initial session state, how to add a cmdlet to the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState), how to create a runspace that uses the initial session state, and how to run the command by using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

## <a name="requirements"></a><span data-ttu-id="62741-105">Krav</span><span class="sxs-lookup"><span data-stu-id="62741-105">Requirements</span></span>

<span data-ttu-id="62741-106">Det här exemplet kräver Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="62741-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="62741-107">Demonstrationer</span><span class="sxs-lookup"><span data-stu-id="62741-107">Demonstrates</span></span>

<span data-ttu-id="62741-108">Det här exemplet demonstrerar följande.</span><span class="sxs-lookup"><span data-stu-id="62741-108">This sample demonstrates the following.</span></span>

- <span data-ttu-id="62741-109">Skapar ett [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -objekt.</span><span class="sxs-lookup"><span data-stu-id="62741-109">Creating an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="62741-110">Lägga till en cmdlet (som definieras av värd programmet) i [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -objektet.</span><span class="sxs-lookup"><span data-stu-id="62741-110">Adding a cmdlet (defined by the Host application) to the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="62741-111">Skapar ett [system. Management. Automation. körnings utrymmen. körnings utrymme](/dotnet/api/System.Management.Automation.Runspaces.Runspace) -objekt som använder objektet.</span><span class="sxs-lookup"><span data-stu-id="62741-111">Creating a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object that uses the object.</span></span>

- <span data-ttu-id="62741-112">Skapar ett [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -objekt som använder objektet [system. Management. Automation. körnings utrymmen. körnings utrymme](/dotnet/api/System.Management.Automation.Runspaces.Runspace) .</span><span class="sxs-lookup"><span data-stu-id="62741-112">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object.</span></span>

- <span data-ttu-id="62741-113">Kommandot läggs till i pipelinen för objektet [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="62741-113">Adding the command to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="62741-114">Extraherar egenskaper från objekten [system. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) som returnerades av kommandot.</span><span class="sxs-lookup"><span data-stu-id="62741-114">Extracting properties from the [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="62741-115">Exempel</span><span class="sxs-lookup"><span data-stu-id="62741-115">Example</span></span>

<span data-ttu-id="62741-116">Det här exemplet skapar en körnings utrymme som använder ett [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -objekt för att definiera de element som är tillgängliga när körnings utrymme öppnas.</span><span class="sxs-lookup"><span data-stu-id="62741-116">This sample creates a runspace that uses an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to define the elements that are available when the runspace is opened.</span></span> <span data-ttu-id="62741-117">I det här exemplet läggs Get-Proc-cmdleten (som definieras av värd programmet) till i det första sessionstillståndet och cmdleten körs synkront med hjälp av ett [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -objekt.</span><span class="sxs-lookup"><span data-stu-id="62741-117">In this sample, the Get-Proc cmdlet (defined by the Host application) is added to the initial session state, and the cmdlet is run synchronously by using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

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

  #region GetProcCommand

  /// <summary>
  /// Class that implements the GetProcCommand.
  /// </summary>
  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
  {
    #region Cmdlet Overrides

    /// <summary>
    /// For each of the requested process names, retrieve and write
    /// the associated processes.
    /// </summary>
    protected override void ProcessRecord()
    {
      // Get the current processes.
      Process[] processes = Process.GetProcesses();

      // Write the processes to the pipeline making them available
      // to the next cmdlet. The second argument (true) tells the
      // system to enumerate the array, and send one process object
      // at a time to the pipeline.
      WriteObject(processes, true);
    }

    #endregion Overrides
  } // End GetProcCommand class.

  #endregion GetProcCommand

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace10
  {
    /// <summary>
    /// This sample shows how to create a default initial session state, how to add
    /// add a cmdlet to the InitialSessionState object, and then how to create
    /// a Runspace object.
    /// </summary>
    /// <param name="args">Parameter is not used.</param>
    /// This sample demonstrates:
    /// 1. Creating an InitialSessionState object.
    /// 2. Adding a cmdlet to the InitialSessionState object.
    /// 3. Creating a runspace that uses the InitialSessionState object.
    /// 4. Creating a PowerShell object that uses the Runspace object.
    /// 5. Running the added command synchronously.
    /// 6. Working with PSObject objects to extract properties
    ///    from the objects returned by the pipeline.
    private static void Main(string[] args)
    {
      // Create a default InitialSessionState object. The default
      // InitialSessionState object contains all the elements provided
      // by Windows PowerShell.
      InitialSessionState iss = InitialSessionState.CreateDefault();

      // Add the get-proc cmdlet to the InitialSessionState object.
      SessionStateCmdletEntry ssce = new SessionStateCmdletEntry("get-proc", typeof(GetProcCommand), null);
      iss.Commands.Add(ssce);

      // Create a Runspace object that uses the InitialSessionState object.
      // Notice that no PSHost object is specified, so the default host is used.
      // See the Hosting samples for information on creating your own custom host.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();

        using (PowerShell powershell = PowerShell.Create())
        {
          powershell.Runspace = myRunSpace;

          // Add the get-proc cmdlet to the pipeline of the PowerShell object.
          powershell.AddCommand("get-proc");

          Collection<PSObject> results = powershell.Invoke();

          Console.WriteLine("Process              HandleCount");
          Console.WriteLine("--------------------------------");

          // Display the output of the pipeline.
          foreach (PSObject result in results)
          {
             Console.WriteLine(
                               "{0,-20} {1}",
                               result.Members["ProcessName"].Value,
                               result.Members["HandleCount"].Value);
          }
        }

        // Close the runspace to release resources.
        myRunSpace.Close();
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="62741-118">Se även</span><span class="sxs-lookup"><span data-stu-id="62741-118">See Also</span></span>

[<span data-ttu-id="62741-119">Skriva ett Windows PowerShell-värdprogram</span><span class="sxs-lookup"><span data-stu-id="62741-119">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
