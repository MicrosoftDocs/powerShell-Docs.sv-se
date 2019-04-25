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
ms.openlocfilehash: eec9c616fc6d5240db185f764a3ea2c8f9575d03
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082795"
---
# <a name="runspace01-sample"></a>Runspace01 – exempel

Det här exemplet visar hur du använder den [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) klassen för att köra den [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synkront. Den [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returnerar [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objekt för varje process som körs på den lokala datorn. Värdena för den [System.Diagnostics.Process.Processname*](/dotnet/api/System.Diagnostics.Process.ProcessName) och [System.Diagnostics.Process.Handlecount*](/dotnet/api/System.Diagnostics.Process.Handlecount) egenskaper sedan extraheras från objekt som returneras och visas i en konsol fönstret.

## <a name="requirements"></a>Krav

 Det här exemplet kräver Windows PowerShell 2.0.

## <a name="demonstrates"></a>Visar

- Skapa en [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objekt att köra ett kommando.

- Att lägga till ett kommando i pipelinen av den [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) objekt.

- Kommandot körs synkront.

- Med hjälp av [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objekt att extrahera egenskaper från objekten som returneras av kommandot.

## <a name="example"></a>Exempel

 Det här exemplet körs den [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synkront i standard-körningsutrymmet som tillhandahålls av Windows PowerShell.

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

## <a name="see-also"></a>Se även
