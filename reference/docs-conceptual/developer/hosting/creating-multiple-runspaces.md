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
# <a name="creating-multiple-runspaces"></a><span data-ttu-id="b2fe4-103">Skapa flera körningsutrymmen</span><span class="sxs-lookup"><span data-stu-id="b2fe4-103">Creating multiple runspaces</span></span>

<span data-ttu-id="b2fe4-104">Om du skapar ett stort antal körnings utrymmen kan du överväga att skapa en körnings utrymme-pool.</span><span class="sxs-lookup"><span data-stu-id="b2fe4-104">If you create a large number of runspaces, you might consider creating a runspace pool.</span></span> <span data-ttu-id="b2fe4-105">Att använda ett [system. Management. Automation. körnings utrymmen. RunspacePool](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool) -objekt i stället för att skapa ett stort antal enskilda körnings utrymmen med samma egenskaper, kan förbättra prestandan.</span><span class="sxs-lookup"><span data-stu-id="b2fe4-105">Using a [System.Management.Automation.Runspaces.Runspacepool](/dotnet/api/System.Management.Automation.Runspaces.RunspacePool) object, rather than creating a large number of individual runspaces with the same characteristics, can improve performance.</span></span>

## <a name="creating-and-using-a-runspace-pool"></a><span data-ttu-id="b2fe4-106">Skapa och använda en körnings utrymme-pool.</span><span class="sxs-lookup"><span data-stu-id="b2fe4-106">Creating and using a runspace pool.</span></span>

 <span data-ttu-id="b2fe4-107">I följande exempel visas hur du skapar en körnings utrymme-pool och hur du kör ett kommando asynkront i en körnings utrymme i poolen.</span><span class="sxs-lookup"><span data-stu-id="b2fe4-107">The following example shows how to create a runspace pool and how to run a command asynchronously in a runspace of the pool.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b2fe4-108">Se även</span><span class="sxs-lookup"><span data-stu-id="b2fe4-108">See Also</span></span>

 [<span data-ttu-id="b2fe4-109">Skapa en InitialSessionState</span><span class="sxs-lookup"><span data-stu-id="b2fe4-109">Creating an InitialSessionState</span></span>](./creating-an-initialsessionstate.md)
