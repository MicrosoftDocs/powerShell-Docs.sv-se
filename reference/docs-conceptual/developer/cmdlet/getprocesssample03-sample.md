---
ms.date: 09/13/2016
ms.topic: reference
title: GetProcessSample03 – exempel
description: GetProcessSample03 – exempel
ms.openlocfilehash: 7827247238f3dad2018b55e396b73d1fa434eb97
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660727"
---
# <a name="getprocesssample03-sample"></a>GetProcessSample03 – exempel

Det här exemplet visar hur du implementerar en cmdlet som hämtar processerna på den lokala datorn. Den innehåller en `Name` parameter som kan acceptera ett objekt från pipelinen eller ett värde från en egenskap hos ett objekt vars egenskaps namn är detsamma som parameter namnet. Denna cmdlet är en förenklad version av `Get-Process` cmdleten som tillhandahålls av Windows PowerShell 2,0.

## <a name="how-to-build-the-sample-using-visual-studio"></a>Så här skapar du exemplet med Visual Studio.

1. Med Windows PowerShell 2,0 SDK installerat navigerar du till mappen GetProcessSample03 Standard platsen är C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample03.

2. Dubbelklicka på ikonen för lösnings filen (. SLN). Exempel projektet öppnas i Visual Studio.

3. I menyn **build** väljer du **build-lösning**.

    Biblioteket för exemplet skapas i standardmappen \Bin eller \Bin\Debug.

### <a name="how-to-run-the-sample"></a>Köra exemplet

1. Skapa följande modul-mapp:

    `[user]/documents/windowspowershell/modules/GetProcessSample03`

2. Kopiera exempel sammansättningen till module-mappen.

3. Starta Windows PowerShell

4. Kör följande kommando för att läsa in sammansättningen i Windows PowerShell:

    `Import-module getprossessample03`

5. Kör följande kommando för att köra cmdleten:

    `get-proc`

## <a name="requirements"></a>Krav

Det här exemplet kräver Windows PowerShell 2,0.

## <a name="demonstrates"></a>Demonstrationer

Det här exemplet demonstrerar följande.

- Deklarera en cmdlet-klass med cmdlet-attributet.

- Deklarera en cmdlet-parameter med attributet parameter.

- Anger positionen för parametern.

- Ange att parametern ska ta emot indata från pipelinen. Indatamängden kan hämtas från ett objekt eller ett värde från en egenskap för ett objekt vars egenskaps namn är detsamma som parameter namnet.

- Deklarera ett verifierings attribut för parameter indatatypen.

## <a name="example"></a>Exempel

Det här exemplet visar en implementering av Get-Proc-cmdleten som innehåller en `Name` parameter som accepterar inmatade från pipelinen.

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

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
