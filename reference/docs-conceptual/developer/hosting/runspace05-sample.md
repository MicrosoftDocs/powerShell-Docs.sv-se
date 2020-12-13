---
ms.date: 09/13/2016
ms.topic: reference
title: Runspace05 – exempel
description: Runspace05 – exempel
ms.openlocfilehash: 67a372eecba30452587471328412e8a2bdd9ec5a
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657736"
---
# <a name="runspace05-sample"></a><span data-ttu-id="e7ca7-103">Runspace05 – exempel</span><span class="sxs-lookup"><span data-stu-id="e7ca7-103">Runspace05 Sample</span></span>

<span data-ttu-id="e7ca7-104">Det här exemplet visar hur du lägger till en snapin-modul till ett [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -objekt så att cmdleten för snapin-modulen är tillgänglig när körnings utrymme öppnas.</span><span class="sxs-lookup"><span data-stu-id="e7ca7-104">This sample shows how to add a snap-in to an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object so that the cmdlet of the snap-in is available when the runspace is opened.</span></span> <span data-ttu-id="e7ca7-105">Snapin-modulen innehåller en Get-Proc-cmdlet (definieras av [GetProcessSample01-exemplet](../cmdlet/getprocesssample01-sample.md)) som körs synkront med hjälp av ett [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -objekt.</span><span class="sxs-lookup"><span data-stu-id="e7ca7-105">The snap-in provides a Get-Proc cmdlet (defined by the [GetProcessSample01 Sample](../cmdlet/getprocesssample01-sample.md)) that is run synchronously by using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

## <a name="requirements"></a><span data-ttu-id="e7ca7-106">Krav</span><span class="sxs-lookup"><span data-stu-id="e7ca7-106">Requirements</span></span>

<span data-ttu-id="e7ca7-107">Det här exemplet kräver Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="e7ca7-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="e7ca7-108">Demonstrationer</span><span class="sxs-lookup"><span data-stu-id="e7ca7-108">Demonstrates</span></span>

<span data-ttu-id="e7ca7-109">Det här exemplet demonstrerar följande.</span><span class="sxs-lookup"><span data-stu-id="e7ca7-109">This sample demonstrates the following.</span></span>

- <span data-ttu-id="e7ca7-110">Skapar ett [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -objekt.</span><span class="sxs-lookup"><span data-stu-id="e7ca7-110">Creating an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="e7ca7-111">Lägga till snapin-modulen till [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -objektet.</span><span class="sxs-lookup"><span data-stu-id="e7ca7-111">Adding the snap-in to the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="e7ca7-112">Skapar ett [system. Management. Automation. körnings utrymmen. körnings utrymme](/dotnet/api/System.Management.Automation.Runspaces.Runspace) -objekt som använder [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -objektet.</span><span class="sxs-lookup"><span data-stu-id="e7ca7-112">Creating a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object that uses the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="e7ca7-113">Skapar ett [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -objekt som använder körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="e7ca7-113">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the runspace.</span></span>

- <span data-ttu-id="e7ca7-114">Lägga till snapin-modulen get-proc-cmdlet: en i pipelinen för objektet [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="e7ca7-114">Adding the snap-in's get-proc cmdlet to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="e7ca7-115">Köra kommandot synkront.</span><span class="sxs-lookup"><span data-stu-id="e7ca7-115">Running the command synchronously.</span></span>

- <span data-ttu-id="e7ca7-116">Extraherar egenskaper från objekten [system. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) som returnerades av kommandot.</span><span class="sxs-lookup"><span data-stu-id="e7ca7-116">Extracting properties from the [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="e7ca7-117">Exempel</span><span class="sxs-lookup"><span data-stu-id="e7ca7-117">Example</span></span>

<span data-ttu-id="e7ca7-118">Det här exemplet skapar en körnings utrymme som använder ett [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -objekt för att definiera de element som är tillgängliga när körnings utrymme öppnas.</span><span class="sxs-lookup"><span data-stu-id="e7ca7-118">This sample creates a runspace that uses an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to define the elements that are available when the runspace is opened.</span></span> <span data-ttu-id="e7ca7-119">I det här exemplet läggs en snapin-modul som definierar en Get-Proc-cmdlet till i det första sessionstillståndet.</span><span class="sxs-lookup"><span data-stu-id="e7ca7-119">In this sample, a snap-in that defines a Get-Proc cmdlet is added to the initial session state.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace05
  {
    /// <summary>
    /// This sample shows how to define an initial session state that is
    /// used when creating a runspace. The sample invokes a command from
    /// a Windows PowerShell snap-in that is present in the console file.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample assumes that user has coppied the GetProcessSample01.dll
    /// that is produced by the GetProcessSample01 sample to the current
    /// directory.
    /// This sample demonstrates the following:
    /// 1. Creating a default initial session state.
    /// 2. Adding a snap-in to the initial session state.
    /// 3. Creating a runspace that uses the initial session state.
    /// 4. Creating a PowerShell object that uses the runspace.
    /// 5. Adding the snap-in's get-proc cmdlet to the PowerShell object.
    /// 6. Using PSObject objects to extract and display properties from
    ///    the objects returned by the cmdlet.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Create the default initial session state. The default initial
      // session state contains all the elements provided by Windows
      // PowerShell.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      PSSnapInException warning;
      iss.ImportPSSnapIn("GetProcPSSnapIn01", out warning);

      // Create a runspace. Notice that no PSHost object is supplied to the
      // CreateRunspace method so the default host is used. See the Host
      // samples for more information on creating your own custom host.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();

        // Create a PowerShell object.
        using (PowerShell powershell = PowerShell.Create())
        {
          // Add the snap-in cmdlet and specify the runspace.
          powershell.AddCommand("GetProcPSSnapIn01\\get-proc");
          powershell.Runspace = myRunSpace;

          // Run the cmdlet synchronously.
          Collection<PSObject> results = powershell.Invoke();

          Console.WriteLine("Process              HandleCount");
          Console.WriteLine("--------------------------------");

          // Display the results.
          foreach (PSObject result in results)
          {
            Console.WriteLine(
                              "{0,-20} {1}",
                              result.Members["ProcessName"].Value,
                              result.Members["HandleCount"].Value);
          }
        }

        // Close the runspace to release any resources.
        myRunSpace.Close();
      }
      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="e7ca7-120">Se även</span><span class="sxs-lookup"><span data-stu-id="e7ca7-120">See Also</span></span>

[<span data-ttu-id="e7ca7-121">Skriva ett Windows PowerShell-värdprogram</span><span class="sxs-lookup"><span data-stu-id="e7ca7-121">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
