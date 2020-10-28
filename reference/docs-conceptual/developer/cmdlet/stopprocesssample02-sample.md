---
ms.date: 09/13/2016
ms.topic: reference
title: StopProcessSample02 – exempel
description: StopProcessSample02 – exempel
ms.openlocfilehash: 96171413f9f04d12460d48ba91c2c927e1856fd1
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666900"
---
# <a name="stopprocesssample02-sample"></a><span data-ttu-id="75a4e-103">StopProcessSample02 – exempel</span><span class="sxs-lookup"><span data-stu-id="75a4e-103">StopProcessSample02 Sample</span></span>

<span data-ttu-id="75a4e-104">Det här exemplet visar hur du skriver en cmdlet som skriver fel sökning (WriteDebug), utförliga (WriteVerbose) och varnings meddelanden (WriteWarning) medan processer stoppas på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="75a4e-104">This sample shows how to write a cmdlet that writes debug (WriteDebug), verbose (WriteVerbose), and warning (WriteWarning) messages while stopping processes on the local computer.</span></span> <span data-ttu-id="75a4e-105">Denna cmdlet liknar den `Stop-Process` cmdlet som tillhandahålls av Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="75a4e-105">This cmdlet is similar to the `Stop-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

### <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="75a4e-106">Så här skapar du exemplet med hjälp av Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="75a4e-106">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="75a4e-107">Öppna Windows Internet Explorer och gå till katalogen StopProcessSample02 i katalogen samples.</span><span class="sxs-lookup"><span data-stu-id="75a4e-107">Open Windows Internet Explorer and navigate to the StopProcessSample02 directory under the Samples directory.</span></span>

    <span data-ttu-id="75a4e-108">Med Windows PowerShell 2,0 SDK installerat navigerar du till mappen StopProcessSample02</span><span class="sxs-lookup"><span data-stu-id="75a4e-108">With the Windows PowerShell 2.0 SDK installed, navigate to the StopProcessSample02 folder.</span></span> <span data-ttu-id="75a4e-109">Standard platsen är C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\StopProcessSample02.</span><span class="sxs-lookup"><span data-stu-id="75a4e-109">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\StopProcessSample02.</span></span>

2. <span data-ttu-id="75a4e-110">Dubbelklicka på ikonen för lösnings filen (. SLN).</span><span class="sxs-lookup"><span data-stu-id="75a4e-110">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="75a4e-111">Detta öppnar exempelprojektet i Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="75a4e-111">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="75a4e-112">I menyn **build** väljer du **build-lösning** .</span><span class="sxs-lookup"><span data-stu-id="75a4e-112">In the **Build** menu, select **Build Solution** .</span></span>

    <span data-ttu-id="75a4e-113">Biblioteket för exemplet skapas i standardmappen \Bin eller \Bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="75a4e-113">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="75a4e-114">Köra exemplet</span><span class="sxs-lookup"><span data-stu-id="75a4e-114">How to run the sample</span></span>

1. <span data-ttu-id="75a4e-115">Skapa följande modul-mapp:</span><span class="sxs-lookup"><span data-stu-id="75a4e-115">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/StopProcessSample02`

2. <span data-ttu-id="75a4e-116">Kopiera exempel sammansättningen till module-mappen.</span><span class="sxs-lookup"><span data-stu-id="75a4e-116">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="75a4e-117">Starta Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="75a4e-117">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="75a4e-118">Kör följande kommando för att läsa in sammansättningen i Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="75a4e-118">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `import-module stopprossessample02`

5. <span data-ttu-id="75a4e-119">Kör följande kommando för att köra cmdleten:</span><span class="sxs-lookup"><span data-stu-id="75a4e-119">Run the following command to run the cmdlet:</span></span>

    `stop-proc`

## <a name="requirements"></a><span data-ttu-id="75a4e-120">Krav</span><span class="sxs-lookup"><span data-stu-id="75a4e-120">Requirements</span></span>

<span data-ttu-id="75a4e-121">Det här exemplet kräver Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="75a4e-121">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="75a4e-122">Demonstrationer</span><span class="sxs-lookup"><span data-stu-id="75a4e-122">Demonstrates</span></span>

<span data-ttu-id="75a4e-123">Det här exemplet demonstrerar följande.</span><span class="sxs-lookup"><span data-stu-id="75a4e-123">This sample demonstrates the following.</span></span>

- <span data-ttu-id="75a4e-124">Deklarera en cmdlet-klass med hjälp av cmdlet-attributet.</span><span class="sxs-lookup"><span data-stu-id="75a4e-124">Declaring a cmdlet class by using the Cmdlet attribute.</span></span>

- <span data-ttu-id="75a4e-125">Deklarera en cmdlet-parameter genom att använda attributet parameter.</span><span class="sxs-lookup"><span data-stu-id="75a4e-125">Declaring a cmdlet parameters by using the Parameter attribute.</span></span>

- <span data-ttu-id="75a4e-126">Skriver utförliga meddelanden.</span><span class="sxs-lookup"><span data-stu-id="75a4e-126">Writing verbose messages.</span></span> <span data-ttu-id="75a4e-127">Mer information om den metod som används för att skriva utförliga meddelanden finns i [system. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span><span class="sxs-lookup"><span data-stu-id="75a4e-127">For more information about the method used to write verbose messages, see [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose).</span></span>

- <span data-ttu-id="75a4e-128">Skriver fel meddelanden.</span><span class="sxs-lookup"><span data-stu-id="75a4e-128">Writing error messages.</span></span> <span data-ttu-id="75a4e-129">Mer information om den metod som används för att skriva fel meddelanden finns i [system. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError).</span><span class="sxs-lookup"><span data-stu-id="75a4e-129">For more information about the method used to write error messages, see [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError).</span></span>

- <span data-ttu-id="75a4e-130">Skriver varnings meddelanden.</span><span class="sxs-lookup"><span data-stu-id="75a4e-130">Writing warning messages.</span></span> <span data-ttu-id="75a4e-131">Mer information om vilken metod som används för att skriva varnings meddelanden finns i [system. Management. Automation. cmdlet. WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning).</span><span class="sxs-lookup"><span data-stu-id="75a4e-131">For more information about the method used to write warning messages, see [System.Management.Automation.Cmdlet.WriteWarning](/dotnet/api/System.Management.Automation.Cmdlet.WriteWarning).</span></span>

## <a name="example"></a><span data-ttu-id="75a4e-132">Exempel</span><span class="sxs-lookup"><span data-stu-id="75a4e-132">Example</span></span>

<span data-ttu-id="75a4e-133">Det här exemplet visar hur du skriver fel söknings-, utförliga och varnings meddelanden med hjälp av `WriteDebug` `WriteVerbose` metoderna, och `WriteWarning` .</span><span class="sxs-lookup"><span data-stu-id="75a4e-133">This sample shows how to write debug, verbose, and warning messages by using the `WriteDebug`, `WriteVerbose`, and `WriteWarning` methods.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Collections;
using Win32Exception = System.ComponentModel.Win32Exception;
using System.Management.Automation;             //Windows PowerShell namespace
using System.Globalization;

namespace Microsoft.Samples.PowerShell.Commands
{
   #region StopProcCommand

    /// <summary>
   /// This class implements the stop-proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsLifecycle.Stop, "Proc",
       SupportsShouldProcess = true)]
   public class StopProcCommand : Cmdlet
   {
       #region Parameters

      /// <summary>
      /// This parameter provides the list of process names on
      /// which the Stop-Proc cmdlet will work.
      /// </summary>
       [Parameter(
          Position = 0,
          Mandatory = true,
          ValueFromPipeline = true,
          ValueFromPipelineByPropertyName = true
       )]
       public string[] Name
       {
          get { return processNames; }
          set { processNames = value; }
       }
       private string[] processNames;

       /// <summary>
       /// This parameter overrides the ShouldContinue call to force
       /// the cmdlet to stop its operation. This parameter should always
       /// be used with caution.
       /// </summary>
       [Parameter]
       public SwitchParameter Force
       {
           get { return force; }
           set { force = value; }
       }
       private bool force;

       /// <summary>
       /// This parameter indicates that the cmdlet should return
       /// an object to the pipeline after the processing has been
       /// completed.
       /// </summary>
       [Parameter]
       public SwitchParameter PassThru
       {
           get { return passThru; }
           set { passThru = value; }
       }
       private bool passThru;

       #endregion Parameters

       #region Cmdlet Overrides

       /// <summary>
       /// The ProcessRecord method does the following for each of the
       /// requested process names:
       /// 1) Check that the process is not a critical process.
       /// 2) Attempt to stop that process.
       /// If no process is requested then nothing occurs.
       /// </summary>
       protected override void ProcessRecord()
       {
           foreach (string name in processNames)
           {
               string message = null;

               // For every process name passed to the cmdlet, get the associated
               // processes.
               // Write a nonterminating error for failure to retrieve
               // a process.

               // Write a user-friendly verbose message to the pipeline. These
               // messages are intended to give the user detailed information
               // on the operations performed by the cmdlet. These messages will
               // appear with the -Verbose option.
               message = String.Format(CultureInfo.CurrentCulture,
                              "Attempting to stop process \"{0}\".", name);
               WriteVerbose(message);

               Process[] processes;

               try
               {
                   processes = Process.GetProcessesByName(name);
               }
               catch (InvalidOperationException ioe)
               {
                   WriteError(new ErrorRecord(ioe,
                                     "UnableToAccessProcessByName",
                                         ErrorCategory.InvalidOperation,
                                             name));
                   continue;
               }

               // Try to stop the processes that have been retrieved.
               foreach (Process process in processes)
               {
                   string processName;

                   try
                   {
                       processName = process.ProcessName;
                   }
                   catch (Win32Exception e)
                   {
                       WriteError(new ErrorRecord(e, "ProcessNameNotFound",
                                         ErrorCategory.ObjectNotFound, process));
                       continue;
                   }

                   // Write a debug message to the host that can be used when
                   // troubleshooting a problem. All debug messages will appear
                   // with the -Debug option.
                   message = String.Format(CultureInfo.CurrentCulture,
                                 "Acquired name for pid {0} : \"{1}\"",
                                        process.Id, processName);
                   WriteDebug(message);

                   // Confirm the operation first.
                   // This is always false if the WhatIf parameter is specified.
                   if (!ShouldProcess(string.Format(CultureInfo.CurrentCulture,
                                        "{0} ({1})",
                                            processName, process.Id)))
                   {
                       continue;
                   }

                   // Make sure that the user really wants to stop a critical
                   // process that can possibly stop the computer.
                   bool criticalProcess = criticalProcessNames.Contains(processName.ToLower(CultureInfo.CurrentCulture));

                   if (criticalProcess && !force)
                   {
                       message = String.Format(CultureInfo.CurrentCulture,
                                    "The process \"{0}\" is a critical process and should not be stopped. Are you sure you wish to stop the process?",
                                        processName);

                       // It is possible that the ProcessRecord method is called
                       // multiple times when objects are received as inputs from
                       // the pipeline. So to retain YesToAll and NoToAll input that
                       // the user may enter across multiple calls to this function,
                       // they are stored as private members of the cmdlet.
                       if (!ShouldContinue(message, "Warning!",
                                    ref yesToAll, ref noToAll))
                       {
                           continue;
                       }
                   } // if (criticalProcess...

                   // Display a warning message if the cmdlet is stopping a
                   // critical process.
                   if (criticalProcess)
                   {
                       message = String.Format(CultureInfo.CurrentCulture,
                                     "Stopping the critical process \"{0}\".",
                                          processName);
                       WriteWarning(message);
                   } // if (criticalProcess...

                   // Stop the named process.
                   try
                   {
                       process.Kill();
                   }
                   catch (Exception e)
                   {
                       if ((e is Win32Exception) || (e is SystemException) ||
                           (e is InvalidOperationException))
                       {
                           // This process could not be stopped so write
                           // a nonterminating error.
                           WriteError(new ErrorRecord(
                                            e,
                                            "CouldNotStopProcess",
                                            ErrorCategory.CloseError,
                                            process)
                                      );
                           continue;
                       } // if ((e is...
                           else throw;
                   } // catch

                   message = String.Format(CultureInfo.CurrentCulture,
                                  "Stopped process \"{0}\", pid {1}.",
                                        processName, process.Id);

                   WriteVerbose(message);

                   // If the PassThru parameter is specified,
                   // return the terminated process object to the pipeline.
                   if (passThru)
                   {
                       message = String.Format(CultureInfo.CurrentCulture,
                                     "Writing process \"{0}\" to pipeline",
                                          processName);
                       WriteDebug(message);
                       WriteObject(process);
                   } // if (passThru...
               } // foreach (Process...
            } // foreach (string...
        } // ProcessRecord

       #endregion Cmdlet Overrides

       #region Private Data

       private bool yesToAll, noToAll;

       /// <summary>
       /// Partial list of critical processes that should not be
       /// stopped.  Lower case is used for case insensitive matching.
       /// </summary>
       private ArrayList criticalProcessNames = new ArrayList(
          new string[] { "system", "winlogon", "spoolsv" }
       );

       #endregion Private Data

   } // StopProcCommand

   #endregion StopProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="75a4e-134">Se även</span><span class="sxs-lookup"><span data-stu-id="75a4e-134">See Also</span></span>

[<span data-ttu-id="75a4e-135">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="75a4e-135">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
