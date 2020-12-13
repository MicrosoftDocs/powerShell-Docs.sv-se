---
ms.date: 09/13/2016
ms.topic: reference
title: Skapa flera körningsutrymmen
description: Skapa flera körningsutrymmen
ms.openlocfilehash: 2dc9cc0397178d679a4d418b7b19fb0895a4e1b7
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649399"
---
# <a name="creating-multiple-runspaces"></a>Skapa flera körningsutrymmen

Om du skapar ett stort antal körnings utrymmen kan du överväga att skapa en körnings utrymme-pool. Att använda ett [system. Management. Automation. körnings utrymmen. RunspacePool](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool) -objekt i stället för att skapa ett stort antal enskilda körnings utrymmen med samma egenskaper, kan förbättra prestandan.

## <a name="creating-and-using-a-runspace-pool"></a>Skapa och använda en körnings utrymme-pool.

 I följande exempel visas hur du skapar en körnings utrymme-pool och hur du kör ett kommando asynkront i en körnings utrymme i poolen.

```csharp
namespace HostRunspacePool
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;

  /// <summary>
  /// This class provides the Main entry point for the Host application.
  /// </summary>
  internal class HostRunspacePool
  {
    /// <summary>
    /// This sample demonstrates the following.
    /// 1. Creating and opening a runspace pool.
    /// 2. Creating a PowerShell object.
    /// 3. Adding commands and arguments to the PowerShell object.
    /// 4. Running the commands asynchronously using the runspace
    ///    of the runspace pool.
    /// </summary>
    /// <param name="args">Parameter is not used.</param>
    private static void Main(string[] args)
    {
      // Create a pool of runspaces.
      using (RunspacePool rsp = RunspaceFactory.CreateRunspacePool())
      {
        rsp.Open();

        // Create a PowerShell object to run the following command.
        //  get-process wmi*
        PowerShell gpc = PowerShell.Create();
        // Specify the runspace to use and add commands.
        gpc.RunspacePool = rsp;
        gpc.AddCommand("Get-Process").AddArgument("wmi*");

        // Invoke the command asynchronously.
        IAsyncResult gpcAsyncResult = gpc.BeginInvoke();
        // Get the results of running the command.
        PSDataCollection<PSObject> gpcOutput = gpc.EndInvoke(gpcAsyncResult);

        // Process the output.
        Console.WriteLine("The output from running the command: get-process wmi*");
        for (int i= 0; i < gpcOutput.Count; i++)
        {
         Console.WriteLine(
                           "Process Name: {0} Process Id: {1}",
                           gpcOutput[i].Properties["ProcessName"].Value,
                           gpcOutput[i].Properties["Id"].Value);
        }
      } // End using.
    } // End Main entry point.
  } // End HostPs5 class.
}
```

## <a name="see-also"></a>Se även

 [Skapa en InitialSessionState](./creating-an-initialsessionstate.md)
