---
ms.date: 09/13/2016
ms.topic: reference
title: Runspace03 – exempel
description: Runspace03 – exempel
ms.openlocfilehash: fff699bf0545bb1419aa45b8c46bbd9c2cf0a99e
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92657851"
---
# <a name="runspace03-sample"></a><span data-ttu-id="2ad2c-103">Runspace03 – exempel</span><span class="sxs-lookup"><span data-stu-id="2ad2c-103">Runspace03 Sample</span></span>

<span data-ttu-id="2ad2c-104">Det här exemplet visar hur du använder klassen [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) för att köra ett skript synkront och hur du hanterar icke-avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="2ad2c-104">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run a script synchronously, and how to handle non-terminating errors.</span></span> <span data-ttu-id="2ad2c-105">Skriptet tar emot en lista över process namn och hämtar sedan dessa processer.</span><span class="sxs-lookup"><span data-stu-id="2ad2c-105">The script receives a list of process names and then retrieves those processes.</span></span> <span data-ttu-id="2ad2c-106">Resultatet av skriptet, inklusive eventuella icke-avslutande fel som genererades när skriptet kördes, visas i konsol fönstret.</span><span class="sxs-lookup"><span data-stu-id="2ad2c-106">The results of the script, including any non-terminating errors that were generated when running the script, are displayed in a console window.</span></span>

## <a name="requirements"></a><span data-ttu-id="2ad2c-107">Krav</span><span class="sxs-lookup"><span data-stu-id="2ad2c-107">Requirements</span></span>

<span data-ttu-id="2ad2c-108">Det här exemplet kräver Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="2ad2c-108">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="2ad2c-109">Demonstrationer</span><span class="sxs-lookup"><span data-stu-id="2ad2c-109">Demonstrates</span></span>

<span data-ttu-id="2ad2c-110">Det här exemplet demonstrerar följande.</span><span class="sxs-lookup"><span data-stu-id="2ad2c-110">This sample demonstrates the following.</span></span>

- <span data-ttu-id="2ad2c-111">Ett [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -objekt skapas för att köra ett skript.</span><span class="sxs-lookup"><span data-stu-id="2ad2c-111">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to run a script.</span></span>

- <span data-ttu-id="2ad2c-112">Lägga till ett skript i pipelinen för objektet [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="2ad2c-112">Adding a script to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="2ad2c-113">Skicka in inobjekt till skriptet från det anropande programmet.</span><span class="sxs-lookup"><span data-stu-id="2ad2c-113">Passing input objects to the script from the calling program.</span></span>

- <span data-ttu-id="2ad2c-114">Köra skriptet synkront.</span><span class="sxs-lookup"><span data-stu-id="2ad2c-114">Running the script synchronously.</span></span>

- <span data-ttu-id="2ad2c-115">Med hjälp av [system. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) -objekt kan du extrahera och Visa egenskaper från de objekt som returneras av skriptet.</span><span class="sxs-lookup"><span data-stu-id="2ad2c-115">Using [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects to extract and display properties from the objects returned by the script.</span></span>

- <span data-ttu-id="2ad2c-116">Hämta och Visa fel poster som genererades när skriptet kördes.</span><span class="sxs-lookup"><span data-stu-id="2ad2c-116">Retrieving and displaying error records that were generated when the script was run.</span></span>

## <a name="example"></a><span data-ttu-id="2ad2c-117">Exempel</span><span class="sxs-lookup"><span data-stu-id="2ad2c-117">Example</span></span>

<span data-ttu-id="2ad2c-118">Det här exemplet kör ett skript synkront i standard-körnings utrymme som tillhandahålls av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2ad2c-118">This sample runs a script synchronously in the default runspace provided by Windows PowerShell.</span></span> <span data-ttu-id="2ad2c-119">Utdata från skriptet och eventuella icke-avslutande fel som genereras visas i konsol fönstret.</span><span class="sxs-lookup"><span data-stu-id="2ad2c-119">The output of the script and any non-terminating errors that were generated are displayed in a console window.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace03
  {
    /// <summary>
    /// This sample shows how to use the PowerShell class to run a
    /// script that retrieves process information for the list of
    /// process names passed to the script. It shows how to pass input
    /// objects to a script and how to retrieve error objects as well
    /// as the output objects.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerSHell object to run a script.
    /// 2. Adding a script to the pipeline of the PowerShell object.
    /// 3. Passing input objects to the script from the calling program.
    /// 4. Running the script synchronously.
    /// 5. Using PSObject objects to extract and display properties from
    ///    the objects returned by the script.
    /// 6. Retrieving and displaying error records that were generated
    ///    when the script was run.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Define a list of processes to look for.
      string[] processNames = new string[]
      {
        "lsass", "nosuchprocess", "services", "nosuchprocess2"
      };

      // The script to run to get these processes. Input passed
      // to the script will be available in the $input variable.
      string script = "$input | get-process -name {$_}";

      // Create a PowerShell object. Creating this object takes care of
      // building all of the other data structures needed to run the script.
      using (PowerShell powershell = PowerShell.Create())
      {
        powershell.AddScript(script);

        Console.WriteLine("Process              HandleCount");
        Console.WriteLine("--------------------------------");

        // Invoke the script synchronously and display the
        // ProcessName and HandleCount properties of the
        // objects that are returned.
        foreach (PSObject result in powershell.Invoke(processNames))
        {
          Console.WriteLine(
                            "{0,-20} {1}",
                            result.Members["ProcessName"].Value,
                            result.Members["HandleCount"].Value);
        }

        // Process any error records that were generated while running
        //  the script.
        Console.WriteLine("\nThe following non-terminating errors occurred:\n");
        PSDataCollection<ErrorRecord> errors = powershell.Streams.Error;
        if (errors != null && errors.Count > 0)
        {
          foreach (ErrorRecord err in errors)
          {
            System.Console.WriteLine("    error: {0}", err.ToString());
          }
        }
      }

      System.Console.WriteLine("\nHit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="2ad2c-120">Se även</span><span class="sxs-lookup"><span data-stu-id="2ad2c-120">See Also</span></span>

[<span data-ttu-id="2ad2c-121">Skriva ett Windows PowerShell-värdprogram</span><span class="sxs-lookup"><span data-stu-id="2ad2c-121">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
