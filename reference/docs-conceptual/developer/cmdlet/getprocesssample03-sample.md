---
title: GetProcessSample03-exempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc9d80ee-6ebd-48cd-a7ea-53cb2b442a22
caps.latest.revision: 6
ms.openlocfilehash: ec5a8c284dd3fa772261099281aba1fb68c49118
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359308"
---
# <a name="getprocesssample03-sample"></a><span data-ttu-id="2728d-102">GetProcessSample03 – exempel</span><span class="sxs-lookup"><span data-stu-id="2728d-102">GetProcessSample03 Sample</span></span>

<span data-ttu-id="2728d-103">Det här exemplet visar hur du implementerar en cmdlet som hämtar processerna på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="2728d-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="2728d-104">Det ger en `Name` parameter som kan acceptera ett objekt från pipelinen eller ett värde från en egenskap hos ett objekt vars egenskaps namn är detsamma som parameter namnet.</span><span class="sxs-lookup"><span data-stu-id="2728d-104">It provides a `Name` parameter that can accept an object from the pipeline or a value from a property of an object whose property name is the same as the parameter name.</span></span> <span data-ttu-id="2728d-105">Denna cmdlet är en förenklad version av `Get-Process`-cmdleten som tillhandahålls av Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="2728d-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="2728d-106">Så här skapar du exemplet med Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2728d-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="2728d-107">Med Windows PowerShell 2,0 SDK installerat navigerar du till mappen GetProcessSample03</span><span class="sxs-lookup"><span data-stu-id="2728d-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample03 folder.</span></span> <span data-ttu-id="2728d-108">Standard platsen är C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03.</span><span class="sxs-lookup"><span data-stu-id="2728d-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03.</span></span>

2. <span data-ttu-id="2728d-109">Dubbelklicka på ikonen för lösnings filen (. SLN).</span><span class="sxs-lookup"><span data-stu-id="2728d-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="2728d-110">Exempel projektet öppnas i Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2728d-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="2728d-111">I menyn **build** väljer du **build-lösning**.</span><span class="sxs-lookup"><span data-stu-id="2728d-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="2728d-112">Biblioteket för exemplet skapas i standardmappen \Bin eller \Bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="2728d-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="2728d-113">Köra exemplet</span><span class="sxs-lookup"><span data-stu-id="2728d-113">How to run the sample</span></span>

1. <span data-ttu-id="2728d-114">Skapa följande modul-mapp:</span><span class="sxs-lookup"><span data-stu-id="2728d-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample03`

2. <span data-ttu-id="2728d-115">Kopiera exempel sammansättningen till module-mappen.</span><span class="sxs-lookup"><span data-stu-id="2728d-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="2728d-116">Starta Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2728d-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="2728d-117">Kör följande kommando för att läsa in sammansättningen i Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="2728d-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `Import-module getprossessample03`

5. <span data-ttu-id="2728d-118">Kör följande kommando för att köra cmdleten:</span><span class="sxs-lookup"><span data-stu-id="2728d-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="2728d-119">Krav</span><span class="sxs-lookup"><span data-stu-id="2728d-119">Requirements</span></span>

<span data-ttu-id="2728d-120">Det här exemplet kräver Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="2728d-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="2728d-121">Demonstrationer</span><span class="sxs-lookup"><span data-stu-id="2728d-121">Demonstrates</span></span>

<span data-ttu-id="2728d-122">Det här exemplet demonstrerar följande.</span><span class="sxs-lookup"><span data-stu-id="2728d-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="2728d-123">Deklarera en cmdlet-klass med cmdlet-attributet.</span><span class="sxs-lookup"><span data-stu-id="2728d-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="2728d-124">Deklarera en cmdlet-parameter med attributet parameter.</span><span class="sxs-lookup"><span data-stu-id="2728d-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="2728d-125">Anger positionen för parametern.</span><span class="sxs-lookup"><span data-stu-id="2728d-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="2728d-126">Ange att parametern ska ta emot indata från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="2728d-126">Specifying that the parameter takes input from the pipeline.</span></span> <span data-ttu-id="2728d-127">Indatamängden kan hämtas från ett objekt eller ett värde från en egenskap för ett objekt vars egenskaps namn är detsamma som parameter namnet.</span><span class="sxs-lookup"><span data-stu-id="2728d-127">The input can be taken from an object or a value from a property of an object whose property name is the same as the parameter name.</span></span>

- <span data-ttu-id="2728d-128">Deklarera ett verifierings attribut för parameter indatatypen.</span><span class="sxs-lookup"><span data-stu-id="2728d-128">Declaring a validation attribute for the parameter input.</span></span>

## <a name="example"></a><span data-ttu-id="2728d-129">Exempel</span><span class="sxs-lookup"><span data-stu-id="2728d-129">Example</span></span>

<span data-ttu-id="2728d-130">Det här exemplet visar en implementering av cmdleten Get-proc som innehåller en `Name` parameter som accepterar ininformation från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="2728d-130">This sample shows an implementation of the Get-Proc cmdlet that includes a `Name` parameter that accepts input from the pipeline.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Commands
{
  using System;
  using System.Diagnostics;
  using System.Management.Automation;           // Windows PowerShell namespace
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
    /// Gets or sets the names of the
    /// process that the cmdlet will retrieve.
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
      // If no process names are passed to the cmdlet, get all
      // processes.
      if (this.processNames == null)
      {
        WriteObject(Process.GetProcesses(), true);
      }
      else
      {
        // If process names are passed to the cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // End if (processNames ...)
    } // End ProcessRecord.

    #endregion Overrides
  } // End GetProcCommand.
  #endregion GetProcCommand
}
```

## <a name="see-also"></a><span data-ttu-id="2728d-131">Se även</span><span class="sxs-lookup"><span data-stu-id="2728d-131">See Also</span></span>

[<span data-ttu-id="2728d-132">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="2728d-132">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
