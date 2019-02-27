---
title: Runspace01 exemplet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42c1c59c-6da5-4cda-9562-e8059177fee1
caps.latest.revision: 11
ms.openlocfilehash: c33044fde4456513b5b07b998cc8db389b318e8e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846615"
---
# <a name="runspace01-sample"></a><span data-ttu-id="bfa05-102">Runspace01 – exempel</span><span class="sxs-lookup"><span data-stu-id="bfa05-102">Runspace01 Sample</span></span>

<span data-ttu-id="bfa05-103">Det här exemplet visar hur du använder den [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) klassen för att köra den [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synkront.</span><span class="sxs-lookup"><span data-stu-id="bfa05-103">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchronously.</span></span> <span data-ttu-id="bfa05-104">Den [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returnerar [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objekt för varje process som körs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="bfa05-104">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects for each process running on the local computer.</span></span> <span data-ttu-id="bfa05-105">Värdena för den [System.Diagnostics.Process.Processname\*](/dotnet/api/System.Diagnostics.Process.ProcessName) och [System.Diagnostics.Process.Handlecount\*](/dotnet/api/System.Diagnostics.Process.Handlecount) egenskaper sedan extraheras från objekt som returneras och visas i en konsol fönstret.</span><span class="sxs-lookup"><span data-stu-id="bfa05-105">The values of the [System.Diagnostics.Process.Processname\*](/dotnet/api/System.Diagnostics.Process.ProcessName) and [System.Diagnostics.Process.Handlecount\*](/dotnet/api/System.Diagnostics.Process.Handlecount) properties are then extracted from the returned objects and displayed in a console window.</span></span>

## <a name="requirements"></a><span data-ttu-id="bfa05-106">Krav</span><span class="sxs-lookup"><span data-stu-id="bfa05-106">Requirements</span></span>

 <span data-ttu-id="bfa05-107">Det här exemplet kräver Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="bfa05-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="bfa05-108">Visar</span><span class="sxs-lookup"><span data-stu-id="bfa05-108">Demonstrates</span></span>

- <span data-ttu-id="bfa05-109">Skapa en [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objekt att köra ett kommando.</span><span class="sxs-lookup"><span data-stu-id="bfa05-109">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to run a command.</span></span>

- <span data-ttu-id="bfa05-110">Att lägga till ett kommando i pipelinen av den [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objekt.</span><span class="sxs-lookup"><span data-stu-id="bfa05-110">Adding a command to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="bfa05-111">Kommandot körs synkront.</span><span class="sxs-lookup"><span data-stu-id="bfa05-111">Running the command synchronously.</span></span>

- <span data-ttu-id="bfa05-112">Med hjälp av [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objekt att extrahera egenskaper från objekten som returneras av kommandot.</span><span class="sxs-lookup"><span data-stu-id="bfa05-112">Using [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objects to extract properties from the objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="bfa05-113">Exempel</span><span class="sxs-lookup"><span data-stu-id="bfa05-113">Example</span></span>

 <span data-ttu-id="bfa05-114">Det här exemplet körs den [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synkront i standard-körningsutrymmet som tillhandahålls av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bfa05-114">This sample runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchronously in the default runspace provided by Windows PowerShell.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="bfa05-115">Se även</span><span class="sxs-lookup"><span data-stu-id="bfa05-115">See Also</span></span>
