---
ms.date: 09/13/2016
ms.topic: reference
title: Runspace06 – exempel
description: Runspace06 – exempel
ms.openlocfilehash: 39841478f115eda089e4d4b1f822954b6ba7d09b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92657672"
---
# <a name="runspace06-sample"></a><span data-ttu-id="81928-103">Runspace06 – exempel</span><span class="sxs-lookup"><span data-stu-id="81928-103">Runspace06 Sample</span></span>

<span data-ttu-id="81928-104">Det här exemplet visar hur du lägger till en modul i ett [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -objekt så att modulen läses in när körnings utrymme öppnas.</span><span class="sxs-lookup"><span data-stu-id="81928-104">This sample shows how to add a module to an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object so that the module is loaded when the runspace is opened.</span></span> <span data-ttu-id="81928-105">Modulen innehåller en Get-Proc-cmdlet (definieras av [GetProcessSample02-exemplet](../cmdlet/getprocesssample02-sample.md)) som körs synkront med hjälp av ett [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -objekt.</span><span class="sxs-lookup"><span data-stu-id="81928-105">The module provides a Get-Proc cmdlet (defined by the [GetProcessSample02 Sample](../cmdlet/getprocesssample02-sample.md)) that is run synchronously by using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

## <a name="requirements"></a><span data-ttu-id="81928-106">Krav</span><span class="sxs-lookup"><span data-stu-id="81928-106">Requirements</span></span>

<span data-ttu-id="81928-107">Det här exemplet kräver Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="81928-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="81928-108">Demonstrationer</span><span class="sxs-lookup"><span data-stu-id="81928-108">Demonstrates</span></span>

<span data-ttu-id="81928-109">Det här exemplet demonstrerar följande.</span><span class="sxs-lookup"><span data-stu-id="81928-109">This sample demonstrates the following.</span></span>

- <span data-ttu-id="81928-110">Skapar ett [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -objekt.</span><span class="sxs-lookup"><span data-stu-id="81928-110">Creating an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="81928-111">Lägger till modulen i [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -objektet.</span><span class="sxs-lookup"><span data-stu-id="81928-111">Adding the module to the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="81928-112">Skapar ett [system. Management. Automation. körnings utrymmen. körnings utrymme](/dotnet/api/System.Management.Automation.Runspaces.Runspace) -objekt som använder [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -objektet.</span><span class="sxs-lookup"><span data-stu-id="81928-112">Creating a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object that uses the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="81928-113">Skapar ett [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -objekt som använder körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="81928-113">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the runspace.</span></span>

- <span data-ttu-id="81928-114">Lägger till modulens get-proc-cmdlet i pipelinen för objektet [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="81928-114">Adding the module's get-proc cmdlet to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="81928-115">Köra kommandot synkront.</span><span class="sxs-lookup"><span data-stu-id="81928-115">Running the command synchronously.</span></span>

- <span data-ttu-id="81928-116">Extraherar egenskaper från objekten [system. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) som returnerades av kommandot.</span><span class="sxs-lookup"><span data-stu-id="81928-116">Extracting properties from the [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="81928-117">Exempel</span><span class="sxs-lookup"><span data-stu-id="81928-117">Example</span></span>

<span data-ttu-id="81928-118">Det här exemplet skapar en körnings utrymme som använder ett [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -objekt för att definiera de element som är tillgängliga när körnings utrymme öppnas.</span><span class="sxs-lookup"><span data-stu-id="81928-118">This sample creates a runspace that uses an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to define the elements that are available when the runspace is opened.</span></span> <span data-ttu-id="81928-119">I det här exemplet läggs en modul som definierar en Get-Proc-cmdlet till i det första sessionstillståndet.</span><span class="sxs-lookup"><span data-stu-id="81928-119">In this sample, a module that defines a Get-Proc cmdlet is added to the initial session state.</span></span>

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
  internal class Runspace06
  {
    /// <summary>
    /// This sample shows how to define an initial session state that is
    /// used when creating a runspace. The sample invokes a command from
    /// a binary module that is loaded by the initial session state.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    /// <remarks>
    /// This sample assumes that user has coppied the GetProcessSample02.dll
    /// that is produced by the GetProcessSample02 sample to the current
    /// directory.
    /// This sample demonstrates the following:
    /// 1. Creating a default initial session state.
    /// 2. Adding a module to the initial session state.
    /// 3. Creating a runspace that uses the initial session state.
    /// 4. Creating a PowerShell object that uses the runspace.
    /// 5. Adding the module's get-proc cmdlet to the PowerShell object.
    /// 6. Running the command synchronously.
    /// 7. Using PSObject objects to extract and display properties from
    ///    the objects returned by the cmdlet.
    /// </remarks>
    private static void Main(string[] args)
    {
        // Create the default initial session state and add the module.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      iss.ImportPSModule(new string[] { @".\GetProcessSample02.dll" });

      // Create a runspace. Notice that no PSHost object is supplied to the
      // CreateRunspace method so the default host is used. See the Host
      // samples for more information on creating your own custom host.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();

        // Create a PowerShell object.
        using (PowerShell powershell = PowerShell.Create())
        {
          // Add the cmdlet and specify the runspace.
          powershell.AddCommand(@"GetProcessSample02\get-proc");
          powershell.Runspace = myRunSpace;

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

## <a name="see-also"></a><span data-ttu-id="81928-120">Se även</span><span class="sxs-lookup"><span data-stu-id="81928-120">See Also</span></span>

[<span data-ttu-id="81928-121">Skriva ett Windows PowerShell-värdprogram</span><span class="sxs-lookup"><span data-stu-id="81928-121">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
