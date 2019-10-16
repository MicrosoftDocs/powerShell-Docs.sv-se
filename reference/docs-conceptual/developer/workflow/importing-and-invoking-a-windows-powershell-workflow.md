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
ms.openlocfilehash: 1113c0d1cd68bb97d2f96b529f755b62137d1f40
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356653"
---
# <a name="importing-and-invoking-a-windows-powershell-workflow"></a>Importera och anropa ett Windows PowerShell-arbetsflöde

Med Windows PowerShell 3 kan du importera och anropa ett arbets flöde som är paketerat som en Windows PowerShell-modul. Information om Windows PowerShell-moduler finns i [skriva en Windows PowerShell-modul](../module/writing-a-windows-powershell-module.md).

Klassen [system. Management. Automation. Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)används som en klients IDE-proxy för arbets flödes objekt på servern. Följande procedur beskriver hur du använder ett [system. Management. Automation. Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)-objekt för att anropa ett arbets flöde.

### <a name="creating-a-psjobproxy-object-to-execute-workflow-commands-on-a-remote-server"></a>Skapa ett PSJobProxy-objekt för att köra arbets flödes kommandon på en fjärrserver.

1. Skapa en anslutning till en fjärran körnings utrymme genom att skapa ett [system. Management. Automation. körnings utrymmen. Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)-objekt.

2. Ange en Windows PowerShell-slutpunkt genom att ange egenskapen [system. Management. Automation. körnings utrymmen. Wsmanconnectioninfo. Shelluri *](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ShellUri) för objektet [system. Management. Automation. körnings utrymmen. Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)till `Microsoft.PowerShell.Workflow` för att ange en Windows PowerShell-slutpunkt.

3. Skapa en körnings utrymme som använder den anslutning som skapats genom att slutföra föregående steg.

4. Skapa ett [system. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell)-objekt och ange dess [system. Management. Automation. PowerShell. körnings utrymme *](/dotnet/api/System.Management.Automation.PowerShell.Runspace) -egenskap till den körnings utrymme som skapades i föregående steg.

5. Importera arbets flödes modulen och dess kommandon till [system. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell).

6. Skapa ett [system. Management. Automation. Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy) -objekt och Använd det för att köra arbets flödes kommandon på fjärrservern.

## <a name="example"></a>Exempel

Följande kod exempel visar hur du anropar ett arbets flöde med hjälp av Windows PowerShell.

Det här exemplet kräver Windows PowerShell 3.

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