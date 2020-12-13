---
ms.date: 09/13/2016
ms.topic: reference
title: GetProcessSample04 – exempel
description: GetProcessSample04 – exempel
ms.openlocfilehash: 4b2b7f7ed5fd87711d0d7872caaf75d453de4832
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652726"
---
# <a name="getprocesssample04-sample"></a><span data-ttu-id="a141f-103">GetProcessSample04 – exempel</span><span class="sxs-lookup"><span data-stu-id="a141f-103">GetProcessSample04 Sample</span></span>

<span data-ttu-id="a141f-104">Det här exemplet visar hur du implementerar en cmdlet som hämtar processerna på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="a141f-104">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="a141f-105">Den genererar ett fel som inte avslutas om ett fel inträffar när en process hämtas.</span><span class="sxs-lookup"><span data-stu-id="a141f-105">It generates a nonterminating error if an error occurs while retrieving a process.</span></span> <span data-ttu-id="a141f-106">Denna cmdlet är en förenklad version av `Get-Process` cmdleten som tillhandahålls av Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="a141f-106">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="a141f-107">Så här skapar du exemplet med Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a141f-107">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="a141f-108">Med Windows PowerShell 2,0 SDK installerat navigerar du till mappen GetProcessSample04</span><span class="sxs-lookup"><span data-stu-id="a141f-108">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample04 folder.</span></span> <span data-ttu-id="a141f-109">Standard platsen är C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04.</span><span class="sxs-lookup"><span data-stu-id="a141f-109">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04.</span></span>

2. <span data-ttu-id="a141f-110">Dubbelklicka på ikonen för lösnings filen (. SLN).</span><span class="sxs-lookup"><span data-stu-id="a141f-110">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="a141f-111">Exempel projektet öppnas i Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a141f-111">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="a141f-112">I menyn **build** väljer du **build-lösning**.</span><span class="sxs-lookup"><span data-stu-id="a141f-112">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="a141f-113">Biblioteket för exemplet skapas i standardmappen \Bin eller \Bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="a141f-113">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="a141f-114">Köra exemplet</span><span class="sxs-lookup"><span data-stu-id="a141f-114">How to run the sample</span></span>

1. <span data-ttu-id="a141f-115">Skapa följande modul-mapp:</span><span class="sxs-lookup"><span data-stu-id="a141f-115">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample04`

2. <span data-ttu-id="a141f-116">Kopiera exempel sammansättningen till module-mappen.</span><span class="sxs-lookup"><span data-stu-id="a141f-116">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="a141f-117">Starta Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a141f-117">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="a141f-118">Kör följande kommando för att läsa in sammansättningen i Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="a141f-118">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `Import-module getprossessample04`

5. <span data-ttu-id="a141f-119">Kör följande kommando för att köra cmdleten:</span><span class="sxs-lookup"><span data-stu-id="a141f-119">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="a141f-120">Krav</span><span class="sxs-lookup"><span data-stu-id="a141f-120">Requirements</span></span>

<span data-ttu-id="a141f-121">Det här exemplet kräver Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="a141f-121">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="a141f-122">Demonstrationer</span><span class="sxs-lookup"><span data-stu-id="a141f-122">Demonstrates</span></span>

<span data-ttu-id="a141f-123">Det här exemplet demonstrerar följande.</span><span class="sxs-lookup"><span data-stu-id="a141f-123">This sample demonstrates the following.</span></span>

- <span data-ttu-id="a141f-124">Deklarera en cmdlet-klass med cmdlet-attributet.</span><span class="sxs-lookup"><span data-stu-id="a141f-124">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="a141f-125">Deklarera en cmdlet-parameter med attributet parameter.</span><span class="sxs-lookup"><span data-stu-id="a141f-125">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="a141f-126">Anger positionen för parametern.</span><span class="sxs-lookup"><span data-stu-id="a141f-126">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="a141f-127">Ange att parametern ska ta emot indata från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="a141f-127">Specifying that the parameter takes input from the pipeline.</span></span> <span data-ttu-id="a141f-128">Indatamängden kan hämtas från ett objekt eller ett värde från en egenskap för ett objekt vars egenskaps namn är detsamma som parameter namnet.</span><span class="sxs-lookup"><span data-stu-id="a141f-128">The input can be taken from an object or a value from a property of an object whose property name is the same as the parameter name.</span></span>

- <span data-ttu-id="a141f-129">Deklarera ett verifierings attribut för parameter indatatypen.</span><span class="sxs-lookup"><span data-stu-id="a141f-129">Declaring a validation attribute for the parameter input.</span></span>

- <span data-ttu-id="a141f-130">Sväller ett fel som inte avslutas och skriver ett fel meddelande till fel strömmen.</span><span class="sxs-lookup"><span data-stu-id="a141f-130">Trapping a nonterminating error and writing an error message to the error stream.</span></span>

## <a name="example"></a><span data-ttu-id="a141f-131">Exempel</span><span class="sxs-lookup"><span data-stu-id="a141f-131">Example</span></span>

<span data-ttu-id="a141f-132">Det här exemplet visar hur du skapar en-cmdlet som hanterar fel som inte avslutas och skriver fel meddelanden till fel strömmen.</span><span class="sxs-lookup"><span data-stu-id="a141f-132">This sample shows how to create a cmdlet that handles nonterminating errors and writes error messages to the error stream.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
    using System;
    using System.Diagnostics;
    using System.Management.Automation;      // Windows PowerShell namespace.
   #region GetProcCommand

   /// <summary>
   /// This class implements the get-proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc")]
   public class GetProcCommand : Cmdlet
   {
      #region Parameters

       /// <summary>
       /// The names of the processes to act on.
       /// </summary>
       private string[] processNames;

      /// <summary>
      /// Gets or sets the list of process names on
      /// which the Get-Proc cmdlet will work.
      /// </summary>
      [Parameter(
         Position = 0,
         ValueFromPipeline = true,
         ValueFromPipelineByPropertyName = true)]
      [ValidateNotNullOrEmpty]
      public string[] Name
      {
         get { return this.processNames; }
         set { this.processNames = value; }
      }

      #endregion Parameters

      #region Cmdlet Overrides

      /// <summary>
      /// The ProcessRecord method calls the Process.GetProcesses
      /// method to retrieve the processes specified by the Name
      /// parameter. Then, the WriteObject method writes the
      /// associated processes to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
          // If no process names are passed to cmdlet, get all
          // processes.
          if (this.processNames == null)
          {
              WriteObject(Process.GetProcesses(), true);
          }
          else
          {
              // If process names are passed to the cmdlet, get and write
              // the associated processes.
              // If a nonterminating error occurs while retrieving processes,
              // call the WriteError method to send an error record to the
              // error stream.
              foreach (string name in this.processNames)
              {
                  Process[] processes;

                  try
                  {
                      processes = Process.GetProcessesByName(name);
                  }
                  catch (InvalidOperationException ex)
                  {
                      WriteError(new ErrorRecord(
                         ex,
                         "UnableToAccessProcessByName",
                         ErrorCategory.InvalidOperation,
                         name));
                      continue;
                  }

                  WriteObject(processes, true);
              } // foreach (string name...
          } // else
      } // ProcessRecord

      #endregion Overrides
    } // End GetProcCommand class.

   #endregion GetProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="a141f-133">Se även</span><span class="sxs-lookup"><span data-stu-id="a141f-133">See Also</span></span>

[<span data-ttu-id="a141f-134">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="a141f-134">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
