---
ms.date: 09/13/2016
ms.topic: reference
title: RemoteRunspacePool01 – exempel
description: RemoteRunspacePool01 – exempel
ms.openlocfilehash: 6594faca17b472140b6b0843bf8ede8e803675e3
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92657961"
---
# <a name="remoterunspacepool01-sample"></a><span data-ttu-id="3d68e-103">RemoteRunspacePool01 – exempel</span><span class="sxs-lookup"><span data-stu-id="3d68e-103">RemoteRunspacePool01 Sample</span></span>

<span data-ttu-id="3d68e-104">Det här exemplet visar hur du skapar en körnings utrymme-pool och hur du kör flera kommandon samtidigt med hjälp av den här poolen.</span><span class="sxs-lookup"><span data-stu-id="3d68e-104">This sample shows how to construct a remote runspace pool and how to run multiple commands concurrently by using this pool.</span></span>

## <a name="requirements"></a><span data-ttu-id="3d68e-105">Krav</span><span class="sxs-lookup"><span data-stu-id="3d68e-105">Requirements</span></span>

 <span data-ttu-id="3d68e-106">Det här exemplet kräver Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="3d68e-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="3d68e-107">Demonstrationer</span><span class="sxs-lookup"><span data-stu-id="3d68e-107">Demonstrates</span></span>

- <span data-ttu-id="3d68e-108">Skapar ett [system. Management. Automation. körnings utrymmen. Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) -objekt.</span><span class="sxs-lookup"><span data-stu-id="3d68e-108">Creating a [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) object.</span></span>

- <span data-ttu-id="3d68e-109">Ange [system. Management. Automation. körnings utrymmen. Runspaceconnectioninfo. OperationTimeout \*](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConnectionInfo.OperationTimeout) och [system. Management. Automation. körnings utrymmen. Runspaceconnectioninfo. opentimey \*](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConnectionInfo.OpenTimeout) Properties för objektet [system. Management. Automation. körnings utrymmen. Wsmanconnectioninfo.](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)</span><span class="sxs-lookup"><span data-stu-id="3d68e-109">Setting the [System.Management.Automation.Runspaces.Runspaceconnectioninfo.Operationtimeout\*](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConnectionInfo.OperationTimeout) and [System.Management.Automation.Runspaces.Runspaceconnectioninfo.Opentimeout\*](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConnectionInfo.OpenTimeout) properties of the [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) object.</span></span>

- <span data-ttu-id="3d68e-110">Skapa en fjärran sluten körnings utrymme som använder objektet [system. Management. Automation. körnings utrymmen. Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) för att upprätta en fjärr anslutning.</span><span class="sxs-lookup"><span data-stu-id="3d68e-110">Creating a remote runspace that uses the [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) object to establish the remote connection.</span></span>

- <span data-ttu-id="3d68e-111">Köra cmdletarna [Get-process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) och [Get-service](/powershell/module/microsoft.powershell.management/get-service) samtidigt med hjälp av körnings utrymme-poolen.</span><span class="sxs-lookup"><span data-stu-id="3d68e-111">Running the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Get-Service](/powershell/module/microsoft.powershell.management/get-service) cmdlets concurrently by using the remote runspace pool.</span></span>

- <span data-ttu-id="3d68e-112">Stänger den fjärranslutna körnings utrymme-poolen för att frigöra fjärr anslutningen.</span><span class="sxs-lookup"><span data-stu-id="3d68e-112">Closing the remote runspace pool to release the remote connection.</span></span>

## <a name="example"></a><span data-ttu-id="3d68e-113">Exempel</span><span class="sxs-lookup"><span data-stu-id="3d68e-113">Example</span></span>

 <span data-ttu-id="3d68e-114">Det här exemplet visar hur du skapar en körnings utrymme-pool och hur du kör flera kommandon samtidigt med hjälp av den här poolen.</span><span class="sxs-lookup"><span data-stu-id="3d68e-114">This sample shows how to construct a remote runspace pool and how to run multiple commands concurrently by using this pool.</span></span>

```csharp
namespace Samples
{
  using System;
  using System.Management.Automation;            // Windows PowerShell namespace.
  using System.Management.Automation.Runspaces;  // Windows PowerShell namespace.

  /// <summary>
  /// This class contains the Main entry point for the application.
  /// </summary>
  internal class RemoteRunspacePool01
  {
    /// <summary>
    /// This sample shows how to construct a remote RunspacePool and how to
    /// concurrently run the get-process and get-service commands using the
    /// runspaces of the pool.
    /// </summary>
    /// <param name="args">Parameter is not used.</param>
    public static void Main(string[] args)
    {
      // Create a WSManConnectionInfo object using the default constructor to
      // connect to the "localhost". The WSManConnectionInfo object can also
      // specify connections to remote computers.
      WSManConnectionInfo connectionInfo = new WSManConnectionInfo();

      // Create a remote runspace pool that uses the WSManConnectionInfo object.
      // The minimum runspaces value of 1 specifies that Windows PowerShell will
      // keep at least 1 runspace open. The maximum runspaces value of 2 specifies
      // that Windows PowerShell will allows 2 runspaces to be opened at the
      // same time so that two commands can be run concurrently.
      using (RunspacePool remoteRunspacePool =
             RunspaceFactory.CreateRunspacePool(1, 2, connectionInfo))
      {
        // Call the Open() method to open the runspace pool and establish
        // the connection.
        remoteRunspacePool.Open();

        // Call the Create() method to create a pipeline, call the AddCommand(string)
        // method to add the "get-process" command, and then call the BeginInvoke()
        // method to run the command asynchronously using a runspace of the pool.
        PowerShell gpsCommand = PowerShell.Create().AddCommand("get-process");
        gpsCommand.RunspacePool = remoteRunspacePool;
        IAsyncResult gpsCommandAsyncResult = gpsCommand.BeginInvoke();

        // The previous call does not block the current thread because it is
        // running asynchronously. Because the remote runspace pool can open two
        // runspaces, the second command can be run.
        PowerShell getServiceCommand = PowerShell.Create().AddCommand("get-service");
        getServiceCommand.RunspacePool = remoteRunspacePool;
        IAsyncResult getServiceCommandAsyncResult = getServiceCommand.BeginInvoke();

        // When you are ready to handle the output, wait for the command to complete
        // before extracting results. A call to the EndInvoke() method will block and return
        // the output.
        PSDataCollection<PSObject> gpsCommandOutput = gpsCommand.EndInvoke(gpsCommandAsyncResult);

        // Process the output from the first command.
        if ((gpsCommandOutput != null) && (gpsCommandOutput.Count > 0))
        {
          Console.WriteLine("The first output from running get-process command: ");
          Console.WriteLine(
                            "Process Name: {0} Process Id: {1}",
                            gpsCommandOutput[0].Properties["ProcessName"].Value,
                            gpsCommandOutput[0].Properties["Id"].Value);
          Console.WriteLine();
        }

        // Now process the output from the second command. As discussed previously, wait
        // for the command to complete before extracting the results.
        PSDataCollection<PSObject> getServiceCommandOutput = getServiceCommand.EndInvoke(
                                   getServiceCommandAsyncResult);

        // Process the output of the second command as needed.
        if ((getServiceCommandOutput != null) && (getServiceCommandOutput.Count > 0))
        {
          Console.WriteLine("The first output from running get-service command: ");
          Console.WriteLine(
                            "Service Name: {0} Description: {1} State: {2}",
                            getServiceCommandOutput[0].Properties["ServiceName"].Value,
                            getServiceCommandOutput[0].Properties["DisplayName"].Value,
                            getServiceCommandOutput[0].Properties["Status"].Value);
        }

        // Once done with running all the commands, close the remote runspace pool.
        // The Dispose() method (called by using primitive) will call Close(), if it
        // is not already called.
        remoteRunspacePool.Close();
      } // End Using.
    } // End Main.
  } // End RemoteRunspacePool01 class
}
```

## <a name="see-also"></a><span data-ttu-id="3d68e-115">Se även</span><span class="sxs-lookup"><span data-stu-id="3d68e-115">See Also</span></span>
