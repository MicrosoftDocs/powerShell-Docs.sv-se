---
title: Cmdlet-uppsättningar | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bcf0739e-920e-4dd8-afca-2c6d6927bc2a
caps.latest.revision: 10
ms.openlocfilehash: ef3b5bab5dcafc578397bcb4f071776bbdeaced1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356464"
---
# <a name="cmdlet-sets"></a><span data-ttu-id="d26a5-102">Cmdlet-uppsättningar</span><span class="sxs-lookup"><span data-stu-id="d26a5-102">Cmdlet Sets</span></span>

<span data-ttu-id="d26a5-103">När du utformar dina cmdletar kan du stöta på fall där du behöver utföra flera åtgärder på samma data.</span><span class="sxs-lookup"><span data-stu-id="d26a5-103">When you design your cmdlets, you might encounter cases in which you need to perform several actions on the same piece of data.</span></span> <span data-ttu-id="d26a5-104">Du kan till exempel behöva hämta och ange data eller starta och stoppa en process.</span><span class="sxs-lookup"><span data-stu-id="d26a5-104">For example, you might need to get and set data or start and stop a process.</span></span> <span data-ttu-id="d26a5-105">Även om du behöver skapa separata cmdlets för att utföra varje åtgärd, bör din cmdlet-design innehålla en basklass som klasserna för de enskilda cmdletarna härleds från.</span><span class="sxs-lookup"><span data-stu-id="d26a5-105">Although you will need to create separate cmdlets to perform each action, your cmdlet design should include a base class from which the classes for the individual cmdlets are derived.</span></span>

<span data-ttu-id="d26a5-106">Tänk på följande när du implementerar en basklass.</span><span class="sxs-lookup"><span data-stu-id="d26a5-106">Keep the following things in mind when implementing a base class.</span></span>

- <span data-ttu-id="d26a5-107">Deklarera eventuella gemensamma parametrar som används av alla härledda cmdlets i Bask Lassen.</span><span class="sxs-lookup"><span data-stu-id="d26a5-107">Declare any common parameters used by all the derived cmdlets in the base class.</span></span>

- <span data-ttu-id="d26a5-108">Lägg till cmdlet-/regionsspecifika parametrar till lämplig cmdlet-klass.</span><span class="sxs-lookup"><span data-stu-id="d26a5-108">Add cmdlet-specific parameters to the appropriate cmdlet class.</span></span>

- <span data-ttu-id="d26a5-109">Åsidosätt lämplig metod för bearbetning av indata i Bask Lassen.</span><span class="sxs-lookup"><span data-stu-id="d26a5-109">Override the appropriate input processing method in the base class.</span></span>

- <span data-ttu-id="d26a5-110">Deklarera attributet [system. Management. Automation. CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) på alla cmdlet-klasser, men deklarera det inte i Bask Lassen.</span><span class="sxs-lookup"><span data-stu-id="d26a5-110">Declare the [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attribute on all cmdlet classes, but do not declare it on the base class.</span></span>

- <span data-ttu-id="d26a5-111">Implementera en [system. Management. Automation. PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) -eller [system. Management. Automation. Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) -klass vars namn och beskrivning visar uppsättningen cmdlets.</span><span class="sxs-lookup"><span data-stu-id="d26a5-111">Implement a [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) or [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) class whose name and description reflects the set of cmdlets.</span></span>

## <a name="example"></a><span data-ttu-id="d26a5-112">Exempel</span><span class="sxs-lookup"><span data-stu-id="d26a5-112">Example</span></span>

<span data-ttu-id="d26a5-113">I följande exempel visas implementeringen av en basklass som används av Get-proc-och Stop-proc-cmdlet: en som härleds från samma basklass.</span><span class="sxs-lookup"><span data-stu-id="d26a5-113">The following example shows the implementation of a base class that is used by Get-Proc and Stop-Proc cmdlet that derive from the same base class.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;             //Windows PowerShell namespace.

namespace Microsoft.Samples.PowerShell.Commands
{

  #region ProcessCommands

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
      // Set up the wildcard characters used in resolving
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

## <a name="see-also"></a><span data-ttu-id="d26a5-114">Se även</span><span class="sxs-lookup"><span data-stu-id="d26a5-114">See Also</span></span>

[<span data-ttu-id="d26a5-115">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="d26a5-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
