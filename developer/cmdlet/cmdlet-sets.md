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
ms.openlocfilehash: ef3b5bab5dcafc578397bcb4f071776bbdeaced1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068393"
---
# <a name="cmdlet-sets"></a>Cmdlet-uppsättningar

När du utformar dina cmdlets kan som uppstå fall där du behöver utföra flera åtgärder på samma typ av data. Du kan behöva hämta och ange data eller starta och stoppa en process. Även om du behöver skapa separata cmdletar för att utföra varje åtgärd, ska utformningen av cmdlet: en inkludera en basklass från vilka klasser för enskilda cmdletar hämtas.

Håll följande i åtanke när du implementerar en basklass.

- Deklarera alla gemensamma parametrar som används av alla härledda cmdletar i basklassen.

- Lägg till cmdlet-specifika parametrar till lämpliga cmdlet-klassen.

- Åsidosätta lämpliga indata metoden i basklassen bearbetades.

- Deklarera de [System.Management.Automation.CmdletAttribute](/dotnet/api/System.Management.Automation.CmdletAttribute) attributet på alla cmdlet klasser, men inte deklarera den på basklassen.

- Implementera en [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) eller [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) klassen vars namn och beskrivning återspeglar uppsättning cmdlets.

## <a name="example"></a>Exempel

I följande exempel visas implementeringen av en basklass som används av Get-processen och stoppa Proc cmdlet som härleds från samma basklassen.

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

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
