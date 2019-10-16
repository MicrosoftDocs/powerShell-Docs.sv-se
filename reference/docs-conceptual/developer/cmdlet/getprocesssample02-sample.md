---
title: GetProcessSample02-exempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 481f557d-3344-4d33-b2da-4736a0165181
caps.latest.revision: 7
ms.openlocfilehash: fa4cd8a724793e71b615c84a5c5a833aa92c93fc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355624"
---
# <a name="getprocesssample02-sample"></a><span data-ttu-id="4662f-102">GetProcessSample02 – exempel</span><span class="sxs-lookup"><span data-stu-id="4662f-102">GetProcessSample02 Sample</span></span>

<span data-ttu-id="4662f-103">Det här exemplet visar hur du skriver en cmdlet som hämtar processerna på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="4662f-103">This sample shows how to write a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="4662f-104">Det ger en `Name`-parameter som kan användas för att ange vilka processer som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="4662f-104">It provides a `Name` parameter that can be used to specify the processes to be retrieved.</span></span> <span data-ttu-id="4662f-105">Denna cmdlet är en förenklad version av cmdleten `Get-Process` som tillhandahålls av Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="4662f-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="4662f-106">Så här skapar du exemplet med Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4662f-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="4662f-107">Med Windows PowerShell 2,0 SDK installerat navigerar du till mappen GetProcessSample02</span><span class="sxs-lookup"><span data-stu-id="4662f-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample02 folder.</span></span> <span data-ttu-id="4662f-108">Standard platsen är C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.</span><span class="sxs-lookup"><span data-stu-id="4662f-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.</span></span>

2. <span data-ttu-id="4662f-109">Dubbelklicka på ikonen för lösnings filen (. SLN).</span><span class="sxs-lookup"><span data-stu-id="4662f-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="4662f-110">Exempel projektet öppnas i Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4662f-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="4662f-111">I menyn **build** väljer du **build-lösning**.</span><span class="sxs-lookup"><span data-stu-id="4662f-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="4662f-112">Biblioteket för exemplet skapas i standardmappen \Bin eller \Bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="4662f-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="4662f-113">Så här kör du exemplet</span><span class="sxs-lookup"><span data-stu-id="4662f-113">How to run the sample</span></span>

1. <span data-ttu-id="4662f-114">Skapa följande modul-mapp:</span><span class="sxs-lookup"><span data-stu-id="4662f-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample02`

2. <span data-ttu-id="4662f-115">Kopiera exempel sammansättningen till module-mappen.</span><span class="sxs-lookup"><span data-stu-id="4662f-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="4662f-116">Starta Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4662f-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="4662f-117">Kör följande kommando för att läsa in sammansättningen i Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="4662f-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `import-module getprossessample02`

5. <span data-ttu-id="4662f-118">Kör följande kommando för att köra cmdleten:</span><span class="sxs-lookup"><span data-stu-id="4662f-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="4662f-119">Krav</span><span class="sxs-lookup"><span data-stu-id="4662f-119">Requirements</span></span>

<span data-ttu-id="4662f-120">Det här exemplet kräver Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="4662f-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="4662f-121">Visat</span><span class="sxs-lookup"><span data-stu-id="4662f-121">Demonstrates</span></span>

<span data-ttu-id="4662f-122">Det här exemplet demonstrerar följande.</span><span class="sxs-lookup"><span data-stu-id="4662f-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="4662f-123">Deklarera en cmdlet-klass med cmdlet-attributet.</span><span class="sxs-lookup"><span data-stu-id="4662f-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="4662f-124">Deklarera en cmdlet-parameter med attributet parameter.</span><span class="sxs-lookup"><span data-stu-id="4662f-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="4662f-125">Anger positionen för parametern.</span><span class="sxs-lookup"><span data-stu-id="4662f-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="4662f-126">Deklarera ett verifierings attribut för parameter indatatypen.</span><span class="sxs-lookup"><span data-stu-id="4662f-126">Declaring a validation attribute for the parameter input.</span></span>

## <a name="example"></a><span data-ttu-id="4662f-127">Exempel</span><span class="sxs-lookup"><span data-stu-id="4662f-127">Example</span></span>

<span data-ttu-id="4662f-128">Det här exemplet visar en implementering av cmdleten Get-proc som innehåller en `Name`-parameter.</span><span class="sxs-lookup"><span data-stu-id="4662f-128">This sample shows an implementation of the Get-Proc cmdlet that includes a `Name` parameter.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
  using System;
  using System.Diagnostics;
  using System.Management.Automation;     // Windows PowerShell namespace

  #region GetProcCommand

  /// <summary>
  /// This class implements the get-proc cmdlet.
  /// </summary>
  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
  {
    #region Parameters

    /// <summary>
    /// The names of the processes retrieved by the cmdlet.
    /// </summary>
    private string[] processNames;

    /// <summary>
    /// Gets or sets the list of process names on which
    /// the Get-Proc cmdlet will work.
    /// </summary>
    [Parameter(Position = 0)]
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
    /// associated process objects to the pipeline.
    /// </summary>
    protected override void ProcessRecord()
    {
      // If no process names are passed to the cmdlet, get all
      // processes.
      if (this.processNames == null)
      {
        WriteObject(Process.GetProcesses(), true);
      }
      else
      {
        // If process names are passed to cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // End if (processNames...).
    } // End ProcessRecord.
    #endregion Cmdlet Overrides
  } // End GetProcCommand class.
  #endregion GetProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="4662f-129">Se även</span><span class="sxs-lookup"><span data-stu-id="4662f-129">See Also</span></span>

[<span data-ttu-id="4662f-130">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="4662f-130">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
