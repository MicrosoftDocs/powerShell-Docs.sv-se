---
title: Importera och anropa ett Windows PowerShell-arbetsflöde | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50e6f9b1-2678-4f53-9250-7c48843a9549
caps.latest.revision: 5
ms.openlocfilehash: a9497d72a586d0cc64c1d4e090819230285767e8
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564974"
---
# <a name="importing-and-invoking-a-windows-powershell-workflow"></a><span data-ttu-id="41081-102">Importera och anropa ett Windows PowerShell-arbetsflöde</span><span class="sxs-lookup"><span data-stu-id="41081-102">Importing and Invoking a Windows PowerShell Workflow</span></span>

<span data-ttu-id="41081-103">Med Windows PowerShell 3 kan du importera och anropa ett arbets flöde som är paketerat som en Windows PowerShell-modul.</span><span class="sxs-lookup"><span data-stu-id="41081-103">Windows PowerShell 3, allows you to import and invoke a workflow that is packaged as a Windows PowerShell module.</span></span> <span data-ttu-id="41081-104">Information om Windows PowerShell-moduler finns i [skriva en Windows PowerShell-modul](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="41081-104">For information about Windows PowerShell modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

<span data-ttu-id="41081-105">Klassen [system. Management. Automation. Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)används som en klients IDE-proxy för arbets flödes objekt på servern.</span><span class="sxs-lookup"><span data-stu-id="41081-105">The [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)class is used as a client side proxy for workflow objects on the server.</span></span> <span data-ttu-id="41081-106">Följande procedur beskriver hur du använder ett [system. Management. Automation. Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)-objekt för att anropa ett arbets flöde.</span><span class="sxs-lookup"><span data-stu-id="41081-106">The following procedure explains how to use a [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)object to invoke a workflow.</span></span>

### <a name="creating-a-psjobproxy-object-to-execute-workflow-commands-on-a-remote-server"></a><span data-ttu-id="41081-107">Skapa ett PSJobProxy-objekt för att köra arbets flödes kommandon på en fjärrserver.</span><span class="sxs-lookup"><span data-stu-id="41081-107">Creating a PSJobProxy object to execute workflow commands on a remote server.</span></span>

1. <span data-ttu-id="41081-108">Skapa en anslutning till en fjärran körnings utrymme genom att skapa ett [system. Management. Automation. körnings utrymmen. Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)-objekt.</span><span class="sxs-lookup"><span data-stu-id="41081-108">Create an [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)object to create a connection to a remote runspace.</span></span>

2. <span data-ttu-id="41081-109">Ange en Windows PowerShell-slutpunkt genom att ange egenskapen [system. Management. Automation. körnings utrymmen. Wsmanconnectioninfo. Shelluri \*](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ShellUri) för objektet [system. Management. Automation. körnings utrymmen. Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) `Microsoft.PowerShell.Workflow` .</span><span class="sxs-lookup"><span data-stu-id="41081-109">Set the [System.Management.Automation.Runspaces.Wsmanconnectioninfo.Shelluri\*](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ShellUri) property of the [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)object to `Microsoft.PowerShell.Workflow` to specify a Windows PowerShell endpoint.</span></span>

3. <span data-ttu-id="41081-110">Skapa en körnings utrymme som använder den anslutning som skapats genom att slutföra föregående steg.</span><span class="sxs-lookup"><span data-stu-id="41081-110">Create a runspace that uses the connection created by completing the previous steps.</span></span>

4. <span data-ttu-id="41081-111">Skapa ett [system. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell)-objekt och ange dess [system. Management. Automation. PowerShell. körnings utrymme \*](/dotnet/api/System.Management.Automation.PowerShell.Runspace) -egenskap till den körnings utrymme som skapades i föregående steg.</span><span class="sxs-lookup"><span data-stu-id="41081-111">Create a [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell)object and set its [System.Management.Automation.Powershell.Runspace\*](/dotnet/api/System.Management.Automation.PowerShell.Runspace) property to the runspace created in the previous step.</span></span>

5. <span data-ttu-id="41081-112">Importera arbets flödes modulen och dess kommandon till [system. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell).</span><span class="sxs-lookup"><span data-stu-id="41081-112">Import the workflow module and its commands into the [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell).</span></span>

6. <span data-ttu-id="41081-113">Skapa ett [system. Management. Automation. Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy) -objekt och Använd det för att köra arbets flödes kommandon på fjärrservern.</span><span class="sxs-lookup"><span data-stu-id="41081-113">Create a [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy) object and use it to execute workflow commands on the remote server.</span></span>

## <a name="example"></a><span data-ttu-id="41081-114">Exempel</span><span class="sxs-lookup"><span data-stu-id="41081-114">Example</span></span>

<span data-ttu-id="41081-115">Följande kod exempel visar hur du anropar ett arbets flöde med hjälp av Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="41081-115">The following code example demonstrates how to invoke a workflow by using Windows PowerShell.</span></span>

<span data-ttu-id="41081-116">Det här exemplet kräver Windows PowerShell 3.</span><span class="sxs-lookup"><span data-stu-id="41081-116">This example requires Windows PowerShell 3.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;
using System.Management.Automation.Runspaces;

namespace WorkflowHostTest
{

class Program
    {
        static void Main(string[] args)
        {
            if (args.Length == 0)
            {
                Console.WriteLine("Specify path to Workflow module");
                return;
            }

            string moduleFile = args[0];

            Console.Write("Creating Remote runspace connection...");
            WSManConnectionInfo connectionInfo = new WSManConnectionInfo();

            //Set the shellURI to workflow endpoint Microsoft.PowerShell.Workflow
            connectionInfo.ShellUri = "Microsoft.PowerShell.Workflow";

            //Create and open a runspace.
            Runspace runspace = RunspaceFactory.CreateRunspace(connectionInfo);
            runspace.Open();
            Console.WriteLine("done");

            PowerShell powershell = PowerShell.Create();
            powershell.Runspace = runspace;
            Console.Write("Setting $VerbosePreference=\"Continue\"...");
            powershell.AddScript("$VerbosePreference=\"Continue\"");
            powershell.Invoke();
            Console.WriteLine("done");

            Console.Write("Importing Workflow module...");
            powershell.Commands.Clear();

            //Import the module in to the PowerShell runspace. A XAML file could also be imported directly by using Import-Module.
            powershell.AddCommand("Import-Module").AddArgument(moduleFile);
            powershell.Invoke();
            Console.WriteLine("done");

            Console.Write("Creating job proxy...");
            powershell.Commands.Clear();
            powershell.AddCommand("Get-Proc").AddArgument("*");
            PSJobProxy job = powershell.AsJobProxy();
            Console.WriteLine("done");

                Console.WriteLine();
                Console.WriteLine("Using job proxy and performing operations...");
                Console.WriteLine("State of Job :" + job.JobStateInfo.State.ToString());
                Console.WriteLine("Starting job...");
                job.StartJob();
                Console.WriteLine("State of Job :" + job.JobStateInfo.State.ToString());

                // use blocking enumerator to wait for objects until job finishes
                job.Output.BlockingEnumerator = true;
                foreach (PSObject o in job.Output)
                {
                    Console.WriteLine(o.Properties["ProcessName"].Value.ToString());
                }

                // wait for a random time before attempting to stop job
                Random random = new Random();
                int time = random.Next(1, 10);
                Console.Write("Sleeping for {0} seconds when job is running on another thread...", time);
                System.Threading.Thread.Sleep(time * 1000);
                Console.WriteLine("done");
                Console.WriteLine("Stopping job...");
                job.StopJob();
                Console.WriteLine("State of Job :" + job.JobStateInfo.State.ToString());
                Console.WriteLine();
                job.Finished.WaitOne();
                Console.WriteLine("Output from job");
                Console.WriteLine("---------------");

                foreach (PSObject o in job.Output)
                {
                    Console.WriteLine(o.Properties["ProcessName"].Value.ToString());
                }

                Console.WriteLine();
                Console.WriteLine("Verbose messages from job");
                Console.WriteLine("-------------------------");
                foreach (VerboseRecord v in job.Verbose)
                {
                    Console.WriteLine(v.Message);
                }

            runspace.Close();
        }
    }
}

```
