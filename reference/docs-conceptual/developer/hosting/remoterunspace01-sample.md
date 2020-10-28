---
ms.date: 09/13/2016
ms.topic: reference
title: RemoteRunspace01 – exempel
description: RemoteRunspace01 – exempel
ms.openlocfilehash: 13c6213089700e779eb185fe48a67c1616fad437
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658025"
---
# <a name="remoterunspace01-sample"></a><span data-ttu-id="0d815-103">RemoteRunspace01 – exempel</span><span class="sxs-lookup"><span data-stu-id="0d815-103">RemoteRunspace01 Sample</span></span>

<span data-ttu-id="0d815-104">Det här exemplet visar hur du skapar en fjärran sluten körnings utrymme som används för att upprätta en fjärr anslutning.</span><span class="sxs-lookup"><span data-stu-id="0d815-104">This sample shows how to create a remote runspace that is used to establish a remote connection.</span></span>

## <a name="requirements"></a><span data-ttu-id="0d815-105">Krav</span><span class="sxs-lookup"><span data-stu-id="0d815-105">Requirements</span></span>

 <span data-ttu-id="0d815-106">Det här exemplet kräver Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="0d815-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="0d815-107">Demonstrationer</span><span class="sxs-lookup"><span data-stu-id="0d815-107">Demonstrates</span></span>

- <span data-ttu-id="0d815-108">Skapar ett [system. Management. Automation. körnings utrymmen. Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) -objekt.</span><span class="sxs-lookup"><span data-stu-id="0d815-108">Creating a [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) object.</span></span>

- <span data-ttu-id="0d815-109">Ange [system. Management. Automation. körnings utrymmen. Runspaceconnectioninfo. OperationTimeout \*](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConnectionInfo.OperationTimeout) och [system. Management. Automation. körnings utrymmen. Runspaceconnectioninfo. opentimey \*](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConnectionInfo.OpenTimeout) Properties för objektet [system. Management. Automation. körnings utrymmen. Wsmanconnectioninfo.](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)</span><span class="sxs-lookup"><span data-stu-id="0d815-109">Setting the [System.Management.Automation.Runspaces.Runspaceconnectioninfo.Operationtimeout\*](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConnectionInfo.OperationTimeout) and [System.Management.Automation.Runspaces.Runspaceconnectioninfo.Opentimeout\*](/dotnet/api/System.Management.Automation.Runspaces.RunspaceConnectionInfo.OpenTimeout) properties of the [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) object.</span></span>

- <span data-ttu-id="0d815-110">Skapa en fjärran sluten körnings utrymme som använder objektet [system. Management. Automation. körnings utrymmen. Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) för att upprätta en fjärr anslutning.</span><span class="sxs-lookup"><span data-stu-id="0d815-110">Creating a remote runspace that uses the [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) object to establish the remote connection.</span></span>

- <span data-ttu-id="0d815-111">Stänger fjärr-körnings utrymme för att frigöra fjärr anslutningen.</span><span class="sxs-lookup"><span data-stu-id="0d815-111">Closing the remote runspace to release the remote connection.</span></span>

## <a name="example"></a><span data-ttu-id="0d815-112">Exempel</span><span class="sxs-lookup"><span data-stu-id="0d815-112">Example</span></span>

<span data-ttu-id="0d815-113">Det här exemplet definierar en fjärr anslutning och använder sedan denna anslutnings information för att upprätta en fjärr anslutning.</span><span class="sxs-lookup"><span data-stu-id="0d815-113">This sample defines a remote connection and then uses that connection information to establish a remote connection.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Management.Automation;             // Windows PowerShell namespace.
  using System.Management.Automation.Runspaces;   // Windows PowerShell namespace.

  /// <summary>
  /// This class contains the Main entry point for the application.
  /// </summary>
  internal class RemoteRunspace01
  {
    /// <summary>
    /// This sample shows how to use a WSManConnectionInfo object to set
    /// various timeouts and how to establish a remote connection.
    /// </summary>
    /// <param name="args">This parameter is not used.</param>
    public static void Main(string[] args)
    {
      // Create a WSManConnectionInfo object using the default constructor
      // to connect to the "localHost". The WSManConnectionInfo object can
      // also specify connections to remote computers.
      WSManConnectionInfo connectionInfo = new WSManConnectionInfo();

      // Set the OperationTimeout property. The OperationTimeout is used to tell
      // Windows PowerShell how long to wait (in milliseconds) before timing out
      // for any operation. This includes sending input data to the remote computer,
      // receiving output data from the remote computer, and more. The user can
      // change this timeout depending on whether the connection is to a computer
      // in the data center or across a slow WAN.
      connectionInfo.OperationTimeout = 4 * 60 * 1000; // 4 minutes.

      // Set the OpenTimeout property. OpenTimeout is used to tell Windows PowerShell
      // how long to wait (in milliseconds) before timing out while establishing a
      // remote connection. The user can change this timeout depending on whether the
      // connection is to a computer in the data center or across a slow WAN.
      connectionInfo.OpenTimeout = 1 * 60 * 1000; // 1 minute.

      // Create a remote runspace using the connection information.
      using (Runspace remoteRunspace = RunspaceFactory.CreateRunspace(connectionInfo))
      {
        // Establish the connection by calling the Open() method to open the runspace.
        // The OpenTimeout value set previously will be applied while establishing
        // the connection. Establishing a remote connection involves sending and
        // receiving some data, so the OperationTimeout will also play a role in this process.
        remoteRunspace.Open();

        // Add the code to run commands in the remote runspace here. The
        // OperationTimeout value set previously will play a role here because
        // running commands involves sending and receiving data.

        // Close the connection. Call the Close() method to close the remote
        // runspace. The Dispose() method (called by using primitive) will call
        // the Close() method if it is not already called.
        remoteRunspace.Close();
      }
    }
  }
}
```
