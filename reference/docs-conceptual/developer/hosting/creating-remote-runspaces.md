---
ms.date: 09/12/2016
ms.topic: reference
title: Skapa fjärranslutna körningsutrymmen
description: Skapa fjärranslutna körningsutrymmen
ms.openlocfilehash: 4a2af4094ff2503fc12ee460d49565f035f0e4fe
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649366"
---
# <a name="creating-remote-runspaces"></a><span data-ttu-id="c4db2-103">Skapa fjärranslutna körningsutrymmen</span><span class="sxs-lookup"><span data-stu-id="c4db2-103">Creating remote runspaces</span></span>

<span data-ttu-id="c4db2-104">PowerShell-kommandon som tar en **computername** -parameter kan köras på alla datorer som kör PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c4db2-104">PowerShell commands that take a **ComputerName** parameter can be run on any computer that runs PowerShell.</span></span> <span data-ttu-id="c4db2-105">Om du vill köra kommandon som inte tar en **computername** -parameter kan du använda WS-Management för att konfigurera en körnings utrymme som ansluter till en angiven dator och kör kommandon på den datorn.</span><span class="sxs-lookup"><span data-stu-id="c4db2-105">To run commands that don't take a **ComputerName** parameter, you can use WS-Management to configure a runspace that connects to a specified computer, and run commands on that computer.</span></span>

## <a name="using-a-wsmanconnection-to-create-a-remote-runspace"></a><span data-ttu-id="c4db2-106">Använda en WSManConnection för att skapa en fjärran sluten körnings utrymme</span><span class="sxs-lookup"><span data-stu-id="c4db2-106">Using a WSManConnection to create a remote runspace</span></span>

 <span data-ttu-id="c4db2-107">Om du vill skapa en körnings utrymme som ansluter till en fjärrdator skapar du ett [system. Management. Automation. körnings utrymmen. WSManConnectionInfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) -objekt.</span><span class="sxs-lookup"><span data-stu-id="c4db2-107">To create a runspace that connects to a remote computer, you create a [System.Management.Automation.Runspaces.WSManConnectionInfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) object.</span></span> <span data-ttu-id="c4db2-108">Du anger mål slut punkten för anslutningen genom att ange egenskapen [system. Management. Automation. körnings utrymmen. WSManConnectionInfo. ConnectionUri](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ConnectionUri) för objektet.</span><span class="sxs-lookup"><span data-stu-id="c4db2-108">You specify the target endpoint for the connection by setting the [System.Management.Automation.Runspaces.WSManConnectionInfo.ConnectionUri](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ConnectionUri) property of the object.</span></span> <span data-ttu-id="c4db2-109">Sedan skapar du en körnings utrymme genom att anropa metoden [system. Management. Automation. körnings utrymmen. RunspaceFactory. CreateRunspace](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory.CreateRunspace) , ange [system. Management. Automation. körnings utrymmen. WSManConnectionInfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) -objektet som `connectionInfo` parameter.</span><span class="sxs-lookup"><span data-stu-id="c4db2-109">You then create a runspace by calling the [System.Management.Automation.Runspaces.RunspaceFactory.CreateRunspace](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory.CreateRunspace) method, specifying the [System.Management.Automation.Runspaces.WSManConnectionInfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) object as the `connectionInfo` parameter.</span></span>

 <span data-ttu-id="c4db2-110">I följande exempel visas hur du skapar en körnings utrymme som ansluter till en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="c4db2-110">The following example shows how to create a runspace that connects to a remote computer.</span></span> <span data-ttu-id="c4db2-111">I exemplet `RemoteComputerUri` används som plats hållare för den faktiska URI: n för en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="c4db2-111">In the example, `RemoteComputerUri` is used as a placeholder for the actual URI of a remote computer.</span></span>

```csharp
namespace Samples
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;            // PowerShell namespace.
  using System.Management.Automation.Runspaces;  // PowerShell namespace.

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class RemoteRunspace02
  {
    /// <summary>
    /// This sample shows how to create a remote runspace that
    /// runs commands on the local computer.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    private static void Main(string[] args)
    {
      // Create a WSManConnectionInfo object using the default constructor
      // to connect to the "localHost". The WSManConnectionInfo object can
      // also be used to specify connections to remote computers.
      Uri RemoteComputerUri = new Uri("http://Server01:5985/WSMAN");
      WSManConnectionInfo connectionInfo = new WSManConnectionInfo(RemoteComputerUri);

      // Set the OperationTimeout property and OpenTimeout properties.
      // The OperationTimeout property is used to tell PowerShell
      // how long to wait (in milliseconds) before timing out for an
      // operation. The OpenTimeout property is used to tell Windows
      // PowerShell how long to wait (in milliseconds) before timing out
      // while establishing a remote connection.
      connectionInfo.OperationTimeout = 4 * 60 * 1000; // 4 minutes.
      connectionInfo.OpenTimeout = 1 * 60 * 1000; // 1 minute.

      // Create a remote runspace using the connection information.
      //using (Runspace remoteRunspace = RunspaceFactory.CreateRunspace())
      using (Runspace remoteRunspace = RunspaceFactory.CreateRunspace(connectionInfo))
      {
        // Establish the connection by calling the Open() method to open the runspace.
        // The OpenTimeout value set previously will be applied while establishing
        // the connection. Establishing a remote connection involves sending and
        // receiving some data, so the OperationTimeout will also play a role in this process.
          remoteRunspace.Open();

        // Create a PowerShell object to run commands in the remote runspace.
        using (PowerShell powershell = PowerShell.Create())
        {
          powershell.Runspace = remoteRunspace;
          powershell.AddCommand("get-process");
          powershell.Invoke();

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

        // Close the connection. Call the Close() method to close the remote
        // runspace. The Dispose() method (called by using primitive) will call
        // the Close() method if it is not already called.
        remoteRunspace.Close();
      }
    }
  }
}
```
