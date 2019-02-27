---
title: 'Cmdlet: en anger | Microsoft Docs'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bcf0739e-920e-4dd8-afca-2c6d6927bc2a
caps.latest.revision: 10
ms.openlocfilehash: e9c59474b7e2bbc07166df8a8b4fa8099edd360f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849051"
---
# <a name="cmdlet-sets"></a><span data-ttu-id="94d87-102">Cmdlet-uppsättningar</span><span class="sxs-lookup"><span data-stu-id="94d87-102">Cmdlet Sets</span></span>

<span data-ttu-id="94d87-103">När du utformar dina cmdlets kan som uppstå fall där du behöver utföra flera åtgärder på samma typ av data.</span><span class="sxs-lookup"><span data-stu-id="94d87-103">When you design your cmdlets, you might encounter cases in which you need to perform several actions on the same piece of data.</span></span> <span data-ttu-id="94d87-104">Du kan behöva hämta och ange data eller starta och stoppa en process.</span><span class="sxs-lookup"><span data-stu-id="94d87-104">For example, you might need to get and set data or start and stop a process.</span></span> <span data-ttu-id="94d87-105">Även om du behöver skapa separata cmdletar för att utföra varje åtgärd, ska utformningen av cmdlet: en inkludera en basklass från vilka klasser för enskilda cmdletar hämtas.</span><span class="sxs-lookup"><span data-stu-id="94d87-105">Although you will need to create separate cmdlets to perform each action, your cmdlet design should include a base class from which the classes for the individual cmdlets are derived.</span></span>

<span data-ttu-id="94d87-106">Håll följande i åtanke när du implementerar en basklass.</span><span class="sxs-lookup"><span data-stu-id="94d87-106">Keep the following things in mind when implementing a base class.</span></span>

- <span data-ttu-id="94d87-107">Deklarera alla gemensamma parametrar som används av alla härledda cmdletar i basklassen.</span><span class="sxs-lookup"><span data-stu-id="94d87-107">Declare any common parameters used by all the derived cmdlets in the base class.</span></span>

- <span data-ttu-id="94d87-108">Lägg till cmdlet-specifika parametrar till lämpliga cmdlet-klassen.</span><span class="sxs-lookup"><span data-stu-id="94d87-108">Add cmdlet-specific parameters to the appropriate cmdlet class.</span></span>

- <span data-ttu-id="94d87-109">Åsidosätta lämpliga indata metoden i basklassen bearbetades.</span><span class="sxs-lookup"><span data-stu-id="94d87-109">Override the appropriate input processing method in the base class.</span></span>

- <span data-ttu-id="94d87-110">Deklarera de [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attributet på alla cmdlet klasser, men inte deklarera den på basklassen.</span><span class="sxs-lookup"><span data-stu-id="94d87-110">Declare the [System.Management.Automation.Cmdletattribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute on all cmdlet classes, but do not declare it on the base class.</span></span>

- <span data-ttu-id="94d87-111">Implementera en [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) eller [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) klassen vars namn och beskrivning återspeglar uppsättning cmdlets.</span><span class="sxs-lookup"><span data-stu-id="94d87-111">Implement a [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) or [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) class whose name and description reflects the set of cmdlets.</span></span>

## <a name="example"></a><span data-ttu-id="94d87-112">Exempel</span><span class="sxs-lookup"><span data-stu-id="94d87-112">Example</span></span>

<span data-ttu-id="94d87-113">I följande exempel visas implementeringen av en basklass som används av Get-processen och stoppa Proc cmdlet som härleds från samma basklassen.</span><span class="sxs-lookup"><span data-stu-id="94d87-113">The following example shows the implementation of a base class that is used by Get-Proc and Stop-Proc cmdlet that derive from the same base class.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;             //Windows PowerShell namespace.

namespace Microsoft.Samples.PowerShell.Commands
{

  #region ProccessCommands

  /// <summary>
  /// This class implements a Stop-Proc cmdlet. The parameters
  /// for this cmdlet are defined by the BaseProcCommand class.
  /// </summary>
  [Cmdlet(VerbsLifecycle.Stop, "Proc", SupportsShouldProcess = true)]
  public class StopProcCommand : BaseProcCommand
  {
    public override void ProcessObject(Process process)
    {
      if (ShouldProcess(process.ProcessName, "Stop-Proc"))
      {
        process.Kill();
      }
    }
  }

  /// <summary>
  /// This class implements a Get-Proc cmdlet. The parameters
  /// for this cmdlet are defined by the BaseProcCommand class.
  /// </summary>

  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : BaseProcCommand
  {
    public override void ProcessObject(Process process)
    {
      WriteObject(process);
    }
  }

  /// <summary>
  /// This class is the base class that defines the common
  /// functionality used by the Get-Proc and Stop-Proc
  /// cmdlets.
  /// </summary>
  public class BaseProcCommand : Cmdlet
  {
    #region Parameters

    // Defines the Name parameter that is used to
    // specify a process by its name.
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

    // Defines the Exclude parameter that is used to
    // specify which processes should be excluded when
    // the cmdlet performs its action.
    [Parameter()]
    public string[] Exclude
    {
      get { return excludeNames; }
      set { excludeNames = value; }
    }
    private string[] excludeNames = new string[0];
    #endregion Parameters

    public virtual void ProcessObject(Process process)
    {
      throw new NotImplementedException("This method should be overridden.");
    }

    #region Cmdlet Overrides
    // <summary>
    // For each of the requested process names, retrieve and write
    // the associated processes.
    // </summary>
    protected override void ProcessRecord()
    {
      // Set up the wildcard chracters used in resolving
      // the process names.
      WildcardOptions options = WildcardOptions.IgnoreCase |
                                WildcardOptions.Compiled;

      WildcardPattern[] include = new WildcardPattern[Name.Length];
      for (int i = 0; i < Name.Length; i++)
      {
        include[i] = new WildcardPattern(Name[i], options);
      }

      WildcardPattern[] exclude = new WildcardPattern[Exclude.Length];
      for (int i = 0; i < Exclude.Length; i++)
      {
        exclude[i] = new WildcardPattern(Exclude[i], options);
      }

      foreach (Process p in Process.GetProcesses())
      {
        foreach (WildcardPattern wIn in include)
        {
          if (wIn.IsMatch(p.ProcessName))
          {
            bool processThisOne = true;
            foreach (WildcardPattern wOut in exclude)
            {
              if (wOut.IsMatch(p.ProcessName))
              {
                processThisOne = false;
                break;
              }
            }
            if (processThisOne)
            {
              ProcessObject(p);
            }
            break;
          }
        }
      }
    }
    #endregion Cmdlet Overrides
  }
    #endregion ProcessCommands
}
```

## <a name="see-also"></a><span data-ttu-id="94d87-114">Se även</span><span class="sxs-lookup"><span data-stu-id="94d87-114">See Also</span></span>

[<span data-ttu-id="94d87-115">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="94d87-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
