---
title: GetProcessSample03 exemplet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc9d80ee-6ebd-48cd-a7ea-53cb2b442a22
caps.latest.revision: 6
ms.openlocfilehash: ec5a8c284dd3fa772261099281aba1fb68c49118
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068053"
---
# <a name="getprocesssample03-sample"></a><span data-ttu-id="ec924-102">GetProcessSample03 – exempel</span><span class="sxs-lookup"><span data-stu-id="ec924-102">GetProcessSample03 Sample</span></span>

<span data-ttu-id="ec924-103">Detta exempel visar hur du implementerar en cmdlet som hämtar processer på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="ec924-103">This sample shows how to implement a cmdlet that retrieves the processes on the local computer.</span></span> <span data-ttu-id="ec924-104">Det ger en `Name` parameter som kan godkänna ett objekt från pipelinen eller ett värde från en egenskap för ett objekt vars egenskapsnamnet är samma som parameternamnet.</span><span class="sxs-lookup"><span data-stu-id="ec924-104">It provides a `Name` parameter that can accept an object from the pipeline or a value from a property of an object whose property name is the same as the parameter name.</span></span> <span data-ttu-id="ec924-105">Denna cmdlet är en förenklad version av den `Get-Process` cmdlet som tillhandahålls av Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="ec924-105">This cmdlet is a simplified version of the `Get-Process` cmdlet provided by Windows PowerShell 2.0.</span></span>

## <a name="how-to-build-the-sample-using-visual-studio"></a><span data-ttu-id="ec924-106">Hur du skapar exemplet med Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ec924-106">How to build the sample using Visual Studio.</span></span>

1. <span data-ttu-id="ec924-107">Navigera till mappen GetProcessSample03 med Windows PowerShell 2.0 SDK för installerade.</span><span class="sxs-lookup"><span data-stu-id="ec924-107">With the Windows PowerShell 2.0 SDK installed, navigate to the GetProcessSample03 folder.</span></span> <span data-ttu-id="ec924-108">Standardplatsen är C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03.</span><span class="sxs-lookup"><span data-stu-id="ec924-108">The default location is C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03.</span></span>

2. <span data-ttu-id="ec924-109">Dubbelklicka på ikonen för lösningsfilen (.sln).</span><span class="sxs-lookup"><span data-stu-id="ec924-109">Double-click the icon for the solution (.sln) file.</span></span> <span data-ttu-id="ec924-110">Exempelprojektet öppnas i Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ec924-110">This opens the sample project in Visual Studio.</span></span>

3. <span data-ttu-id="ec924-111">I den **skapa** menyn och välj **skapa lösning**.</span><span class="sxs-lookup"><span data-stu-id="ec924-111">In the **Build** menu, select **Build Solution**.</span></span>

    <span data-ttu-id="ec924-112">Biblioteket för exemplet skapas i standardmappar \bin eller \bin\debug.</span><span class="sxs-lookup"><span data-stu-id="ec924-112">The library for the sample will be built in the default \bin or \bin\debug folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="ec924-113">Hur du kör exemplet</span><span class="sxs-lookup"><span data-stu-id="ec924-113">How to run the sample</span></span>

1. <span data-ttu-id="ec924-114">Skapa följande modulmappen:</span><span class="sxs-lookup"><span data-stu-id="ec924-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/GetProcessSample03`

2. <span data-ttu-id="ec924-115">Kopiera exemplet sammansättningen till modulmappen.</span><span class="sxs-lookup"><span data-stu-id="ec924-115">Copy the sample assembly to the module folder.</span></span>

3. <span data-ttu-id="ec924-116">Starta Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ec924-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="ec924-117">Kör följande kommando för att läsa in sammansättningen i Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="ec924-117">Run the following command to load the assembly into Windows PowerShell:</span></span>

    `Import-module getprossessample03`

5. <span data-ttu-id="ec924-118">Kör följande kommando för att köra cmdleten:</span><span class="sxs-lookup"><span data-stu-id="ec924-118">Run the following command to run the cmdlet:</span></span>

    `get-proc`

## <a name="requirements"></a><span data-ttu-id="ec924-119">Krav</span><span class="sxs-lookup"><span data-stu-id="ec924-119">Requirements</span></span>

<span data-ttu-id="ec924-120">Det här exemplet kräver Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="ec924-120">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="ec924-121">Visar</span><span class="sxs-lookup"><span data-stu-id="ec924-121">Demonstrates</span></span>

<span data-ttu-id="ec924-122">Detta exempel visar följande.</span><span class="sxs-lookup"><span data-stu-id="ec924-122">This sample demonstrates the following.</span></span>

- <span data-ttu-id="ec924-123">Deklarera en cmdlet-klass med hjälp av Cmdlet-attributet.</span><span class="sxs-lookup"><span data-stu-id="ec924-123">Declaring a cmdlet class using the Cmdlet attribute.</span></span>

- <span data-ttu-id="ec924-124">Deklarera en cmdlet-parameter med hjälp av parametern-attributet.</span><span class="sxs-lookup"><span data-stu-id="ec924-124">Declaring a cmdlet parameter using the Parameter attribute.</span></span>

- <span data-ttu-id="ec924-125">Anger positionen för parametern.</span><span class="sxs-lookup"><span data-stu-id="ec924-125">Specifying the position of the parameter.</span></span>

- <span data-ttu-id="ec924-126">Anger att parametern hämtar indata från pipeline.</span><span class="sxs-lookup"><span data-stu-id="ec924-126">Specifying that the parameter takes input from the pipeline.</span></span> <span data-ttu-id="ec924-127">Indata kan hämtas från ett objekt eller ett värde från en egenskap för ett objekt vars egenskapsnamnet är samma som parameternamnet.</span><span class="sxs-lookup"><span data-stu-id="ec924-127">The input can be taken from an object or a value from a property of an object whose property name is the same as the parameter name.</span></span>

- <span data-ttu-id="ec924-128">Deklarera en verifieringsattribut för parametern indata.</span><span class="sxs-lookup"><span data-stu-id="ec924-128">Declaring a validation attribute for the parameter input.</span></span>

## <a name="example"></a><span data-ttu-id="ec924-129">Exempel</span><span class="sxs-lookup"><span data-stu-id="ec924-129">Example</span></span>

<span data-ttu-id="ec924-130">Det här exemplet visar en implementering av cmdleten Get-processen som innehåller en `Name` parameter som godkänner indata från pipeline.</span><span class="sxs-lookup"><span data-stu-id="ec924-130">This sample shows an implementation of the Get-Proc cmdlet that includes a `Name` parameter that accepts input from the pipeline.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ec924-131">Se även</span><span class="sxs-lookup"><span data-stu-id="ec924-131">See Also</span></span>

[<span data-ttu-id="ec924-132">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="ec924-132">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
