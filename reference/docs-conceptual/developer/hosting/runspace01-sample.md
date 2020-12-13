---
ms.date: 09/13/2016
ms.topic: reference
title: Runspace01 – exempel
description: Runspace01 – exempel
ms.openlocfilehash: f47f79dd507db258119016353dc5a72d110d9252
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657916"
---
# <a name="runspace01-sample"></a><span data-ttu-id="d90eb-103">Runspace01 – exempel</span><span class="sxs-lookup"><span data-stu-id="d90eb-103">Runspace01 Sample</span></span>

<span data-ttu-id="d90eb-104">Det här exemplet visar hur du använder klassen [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) för att köra cmdleten [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) synkront.</span><span class="sxs-lookup"><span data-stu-id="d90eb-104">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchronously.</span></span> <span data-ttu-id="d90eb-105">Cmdleten [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) returnerar [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -objekt för varje process som körs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="d90eb-105">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects for each process running on the local computer.</span></span> <span data-ttu-id="d90eb-106">Värdena för egenskaperna [system. Diagnostics. process. processname \*](/dotnet/api/System.Diagnostics.Process.ProcessName) och [system. Diagnostics. process. HandleCount \*](/dotnet/api/System.Diagnostics.Process.Handlecount) extraheras sedan från de returnerade objekten och visas i konsol fönstret.</span><span class="sxs-lookup"><span data-stu-id="d90eb-106">The values of the [System.Diagnostics.Process.Processname\*](/dotnet/api/System.Diagnostics.Process.ProcessName) and [System.Diagnostics.Process.Handlecount\*](/dotnet/api/System.Diagnostics.Process.Handlecount) properties are then extracted from the returned objects and displayed in a console window.</span></span>

## <a name="requirements"></a><span data-ttu-id="d90eb-107">Krav</span><span class="sxs-lookup"><span data-stu-id="d90eb-107">Requirements</span></span>

 <span data-ttu-id="d90eb-108">Det här exemplet kräver Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="d90eb-108">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="d90eb-109">Demonstrationer</span><span class="sxs-lookup"><span data-stu-id="d90eb-109">Demonstrates</span></span>

- <span data-ttu-id="d90eb-110">Skapar ett-kommando med ett [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -objekt för att köra ett kommando.</span><span class="sxs-lookup"><span data-stu-id="d90eb-110">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to run a command.</span></span>

- <span data-ttu-id="d90eb-111">Lägga till ett kommando i pipelinen för objektet [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="d90eb-111">Adding a command to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="d90eb-112">Köra kommandot synkront.</span><span class="sxs-lookup"><span data-stu-id="d90eb-112">Running the command synchronously.</span></span>

- <span data-ttu-id="d90eb-113">Med hjälp av [system. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) -objekt kan du extrahera egenskaper från de objekt som returneras av kommandot.</span><span class="sxs-lookup"><span data-stu-id="d90eb-113">Using [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects to extract properties from the objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="d90eb-114">Exempel</span><span class="sxs-lookup"><span data-stu-id="d90eb-114">Example</span></span>

 <span data-ttu-id="d90eb-115">Det här exemplet kör cmdleten [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) synkront i standard-körnings utrymme som tillhandahålls av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d90eb-115">This sample runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchronously in the default runspace provided by Windows PowerShell.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Management.Automation;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace01
  {
    /// <summary>
    /// This sample uses the PowerShell class to execute
    /// the get-process cmdlet synchronously. The name and
    /// handlecount are then extracted from the PSObjects
    /// returned and displayed.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object to run a command.
    /// 2. Adding a command to the pipeline of the PowerShell object.
    /// 3. Running the command synchronously.
    /// 4. Using PSObject objects to extract properties from the objects
    ///    returned by the command.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Create a PowerShell object. Creating this object takes care of
      // building all of the other data structures needed to run the command.
      using (PowerShell powershell = PowerShell.Create().AddCommand("get-process"))
      {
        Console.WriteLine("Process              HandleCount");
        Console.WriteLine("--------------------------------");

        // Invoke the command synchronously and display the
        // ProcessName and HandleCount properties of the
        // objects that are returned.
        foreach (PSObject result in powershell.Invoke())
        {
          Console.WriteLine(
                      "{0,-20} {1}",
                      result.Members["ProcessName"].Value,
                      result.Members["HandleCount"].Value);
        }
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="d90eb-116">Se även</span><span class="sxs-lookup"><span data-stu-id="d90eb-116">See Also</span></span>
