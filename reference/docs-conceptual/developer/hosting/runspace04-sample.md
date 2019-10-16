---
title: Runspace04-exempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a6a04f15-b5d8-475b-ac9c-e75c58ec8933
caps.latest.revision: 8
ms.openlocfilehash: 3cb370cd1bfe9ce7198980cc1c26fafb126d00a3
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353048"
---
# <a name="runspace04-sample"></a><span data-ttu-id="d489e-102">Runspace04 – exempel</span><span class="sxs-lookup"><span data-stu-id="d489e-102">Runspace04 Sample</span></span>

<span data-ttu-id="d489e-103">Det här exemplet visar hur du använder klassen [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) för att köra kommandon och hur du fångar upp avslutande fel som uppstår när du kör kommandona.</span><span class="sxs-lookup"><span data-stu-id="d489e-103">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run commands, and how to catch terminating errors that are thrown when running the commands.</span></span> <span data-ttu-id="d489e-104">Två kommandon körs och det sista kommandot skickas till ett parameter argument som inte är giltigt.</span><span class="sxs-lookup"><span data-stu-id="d489e-104">Two commands are run, and the last command is passed a parameter argument that is not valid.</span></span> <span data-ttu-id="d489e-105">Därför returneras inga objekt och ett avslutande fel genereras.</span><span class="sxs-lookup"><span data-stu-id="d489e-105">As a result, no objects are returned and a terminating error is thrown.</span></span>

## <a name="requirements"></a><span data-ttu-id="d489e-106">Krav</span><span class="sxs-lookup"><span data-stu-id="d489e-106">Requirements</span></span>

<span data-ttu-id="d489e-107">Det här exemplet kräver Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="d489e-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="d489e-108">Visat</span><span class="sxs-lookup"><span data-stu-id="d489e-108">Demonstrates</span></span>

<span data-ttu-id="d489e-109">Det här exemplet demonstrerar följande.</span><span class="sxs-lookup"><span data-stu-id="d489e-109">This sample demonstrates the following.</span></span>

- <span data-ttu-id="d489e-110">Skapar ett [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -objekt.</span><span class="sxs-lookup"><span data-stu-id="d489e-110">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="d489e-111">Lägger till kommandon i pipelinen för objektet [system. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) .</span><span class="sxs-lookup"><span data-stu-id="d489e-111">Adding commands to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="d489e-112">Lägger till parameter argument i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="d489e-112">Adding parameter arguments to the pipeline.</span></span>

- <span data-ttu-id="d489e-113">Anropar kommandona synkront.</span><span class="sxs-lookup"><span data-stu-id="d489e-113">Invoking the commands synchronously.</span></span>

- <span data-ttu-id="d489e-114">Med hjälp av [system. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) -objekt kan du extrahera och Visa egenskaper från de objekt som returneras av kommandona.</span><span class="sxs-lookup"><span data-stu-id="d489e-114">Using [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects to extract and display properties from the objects returned by the commands.</span></span>

- <span data-ttu-id="d489e-115">Hämta och Visa fel poster som genererades under körningen av kommandona.</span><span class="sxs-lookup"><span data-stu-id="d489e-115">Retrieving and displaying error records that were generated during the running of the commands.</span></span>

- <span data-ttu-id="d489e-116">Fånga och Visa avslutande undantag som har utlösts av kommandona.</span><span class="sxs-lookup"><span data-stu-id="d489e-116">Catching and displaying terminating exceptions thrown by the commands.</span></span>

## <a name="example"></a><span data-ttu-id="d489e-117">Exempel</span><span class="sxs-lookup"><span data-stu-id="d489e-117">Example</span></span>

<span data-ttu-id="d489e-118">Det här exemplet kör kommandon synkront i standard-körnings utrymme som tillhandahålls av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d489e-118">This sample runs commands synchronously in the default runspace provided by Windows PowerShell.</span></span> <span data-ttu-id="d489e-119">Det sista kommandot genererar ett avslutande fel eftersom ett parameter argument som inte är giltigt skickas till kommandot.</span><span class="sxs-lookup"><span data-stu-id="d489e-119">The last command throws a terminating error because a parameter argument that is not valid is passed to the command.</span></span> <span data-ttu-id="d489e-120">Det avslutande felet fångas och visas.</span><span class="sxs-lookup"><span data-stu-id="d489e-120">The terminating error is trapped and displayed.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace04
  {
    /// <summary>
    /// This sample shows how to use a PowerShell object to run commands.
    /// The commands generate a terminating exception that the caller
    /// should catch and process.
    /// </summary>
    /// <param name="args">The parameter is not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object to run commands.
    /// 2. Adding commands to the pipeline of  the PowerShell object.
    /// 3. Passing input objects to the commands from the calling program.
    /// 4. Using PSObject objects to extract and display properties from the
    ///    objects returned by the commands.
    /// 5. Retrieving and displaying error records that were generated
    ///    while running the commands.
    /// 6. Catching and displaying terminating exceptions generated
    ///    while running the commands.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Create a PowerShell object.
      using (PowerShell powershell = PowerShell.Create())
      {
        // Add the commands to the PowerShell object.
        powershell.AddCommand("Get-ChildItem").AddCommand("Select-String").AddArgument("*");

        // Run the commands synchronously. Because of the bad regular expression,
        // no objects will be returned. Instead, an exception will be thrown.
        try
        {
          foreach (PSObject result in powershell.Invoke())
          {
            Console.WriteLine("'{0}'", result.ToString());
          }

          // Process any error records that were generated while running the commands.
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
        catch (RuntimeException runtimeException)
        {
          // Trap any exception generated by the commands. These exceptions
          // will all be derived from the RuntimeException exception.
          System.Console.WriteLine(
                        "Runtime exception: {0}: {1}\n{2}",
                        runtimeException.ErrorRecord.InvocationInfo.InvocationName,
                        runtimeException.Message,
                        runtimeException.ErrorRecord.InvocationInfo.PositionMessage);
        }
      }

      System.Console.WriteLine("\nHit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="d489e-121">Se även</span><span class="sxs-lookup"><span data-stu-id="d489e-121">See Also</span></span>

[<span data-ttu-id="d489e-122">Skriva ett Windows PowerShell-värdprogram</span><span class="sxs-lookup"><span data-stu-id="d489e-122">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)