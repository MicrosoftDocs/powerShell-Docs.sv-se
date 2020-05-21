---
title: Runspace06-exempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 471c85f3-9287-45c2-b4bc-833caa1b7634
caps.latest.revision: 8
ms.openlocfilehash: 49a938a5acd7817476b299deea465771b6a94985
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83563670"
---
# <a name="runspace06-sample"></a><span data-ttu-id="91c7a-102">Runspace06 – exempel</span><span class="sxs-lookup"><span data-stu-id="91c7a-102">Runspace06 Sample</span></span>

<span data-ttu-id="91c7a-103">Det här exemplet visar hur du lägger till en modul i ett [system. Management. Automation. körnings utrymmen. Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -objekt så att modulen läses in när körnings utrymme öppnas.</span><span class="sxs-lookup"><span data-stu-id="91c7a-103">This sample shows how to add a module to an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object so that the module is loaded when the runspace is opened.</span></span> <span data-ttu-id="91c7a-104">Modulen innehåller en get-proc-cmdlet (definieras av [GetProcessSample02-exemplet](../cmdlet/getprocesssample02-sample.md)) som körs synkront med hjälp av ett [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -objekt.</span><span class="sxs-lookup"><span data-stu-id="91c7a-104">The module provides a Get-Proc cmdlet (defined by the [GetProcessSample02 Sample](../cmdlet/getprocesssample02-sample.md)) that is run synchronously by using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

## <a name="requirements"></a><span data-ttu-id="91c7a-105">Krav</span><span class="sxs-lookup"><span data-stu-id="91c7a-105">Requirements</span></span>

<span data-ttu-id="91c7a-106">Det här exemplet kräver Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="91c7a-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="91c7a-107">Demonstrationer</span><span class="sxs-lookup"><span data-stu-id="91c7a-107">Demonstrates</span></span>

<span data-ttu-id="91c7a-108">Det här exemplet demonstrerar följande.</span><span class="sxs-lookup"><span data-stu-id="91c7a-108">This sample demonstrates the following.</span></span>

- <span data-ttu-id="91c7a-109">Skapar ett [system. Management. Automation. körnings utrymmen. Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -objekt.</span><span class="sxs-lookup"><span data-stu-id="91c7a-109">Creating an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="91c7a-110">Lägga till modulen i objektet [system. Management. Automation. körnings utrymmen. Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .</span><span class="sxs-lookup"><span data-stu-id="91c7a-110">Adding the module to the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="91c7a-111">Skapar ett [system. Management. Automation. körnings utrymmen. körnings utrymme](/dotnet/api/System.Management.Automation.Runspaces.Runspace) -objekt som använder objektet [system. Management. Automation. körnings utrymmen. Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) .</span><span class="sxs-lookup"><span data-stu-id="91c7a-111">Creating a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object that uses the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="91c7a-112">Skapar ett [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -objekt som använder körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="91c7a-112">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the runspace.</span></span>

- <span data-ttu-id="91c7a-113">Lägger till modulens get-proc-cmdlet i pipelinen för objektet [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="91c7a-113">Adding the module's get-proc cmdlet to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="91c7a-114">Köra kommandot synkront.</span><span class="sxs-lookup"><span data-stu-id="91c7a-114">Running the command synchronously.</span></span>

- <span data-ttu-id="91c7a-115">Extraherar egenskaper från objekten [system. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) som returnerades av kommandot.</span><span class="sxs-lookup"><span data-stu-id="91c7a-115">Extracting properties from the [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="91c7a-116">Exempel</span><span class="sxs-lookup"><span data-stu-id="91c7a-116">Example</span></span>

<span data-ttu-id="91c7a-117">Det här exemplet skapar en körnings utrymme som använder ett [system. Management. Automation. körnings utrymmen. Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -objekt för att definiera de element som är tillgängliga när körnings utrymme öppnas.</span><span class="sxs-lookup"><span data-stu-id="91c7a-117">This sample creates a runspace that uses an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to define the elements that are available when the runspace is opened.</span></span> <span data-ttu-id="91c7a-118">I det här exemplet läggs en modul som definierar en get-proc-cmdlet till i det första sessionstillståndet.</span><span class="sxs-lookup"><span data-stu-id="91c7a-118">In this sample, a module that defines a Get-Proc cmdlet is added to the initial session state.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="91c7a-119">Se även</span><span class="sxs-lookup"><span data-stu-id="91c7a-119">See Also</span></span>

[<span data-ttu-id="91c7a-120">Skriva ett Windows PowerShell-värdprogram</span><span class="sxs-lookup"><span data-stu-id="91c7a-120">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
