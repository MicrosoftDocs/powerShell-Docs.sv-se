---
title: GetProcessSample02 exemplet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 481f557d-3344-4d33-b2da-4736a0165181
caps.latest.revision: 7
ms.openlocfilehash: fa4cd8a724793e71b615c84a5c5a833aa92c93fc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849513"
---
# <a name="getprocesssample02-sample"></a>GetProcessSample02 – exempel

Detta exempel visar hur du skriver en cmdlet som hämtar processer på den lokala datorn. Det ger en `Name` parameter som kan användas för att ange processerna som ska hämtas. Denna cmdlet är en förenklad version av den `Get-Process` cmdlet som tillhandahålls av Windows PowerShell 2.0.

## <a name="how-to-build-the-sample-using-visual-studio"></a>Hur du skapar exemplet med Visual Studio.

1. Navigera till mappen GetProcessSample02 med Windows PowerShell 2.0 SDK för installerade. Standardplatsen är C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample02.

2. Dubbelklicka på ikonen för lösningsfilen (.sln). Exempelprojektet öppnas i Visual Studio.

3. I den **skapa** menyn och välj **skapa lösning**.

    Biblioteket för exemplet skapas i standardmappar \bin eller \bin\debug.

### <a name="how-to-run-the-sample"></a>Hur du kör exemplet

1. Skapa följande modulmappen:

    `[user]/documents/windowspowershell/modules/GetProcessSample02`

2. Kopiera exemplet sammansättningen till modulmappen.

3. Starta Windows PowerShell

4. Kör följande kommando för att läsa in sammansättningen i Windows PowerShell:

    `import-module getprossessample02`

5. Kör följande kommando för att köra cmdleten:

    `get-proc`

## <a name="requirements"></a>Krav

Det här exemplet kräver Windows PowerShell 2.0.

## <a name="demonstrates"></a>Visar

Detta exempel visar följande.

- Deklarera en cmdlet-klass med hjälp av Cmdlet-attributet.

- Deklarera en cmdlet-parameter med hjälp av parametern-attributet.

- Anger positionen för parametern.

- Deklarera en verifieringsattribut för parametern indata.

## <a name="example"></a>Exempel

Det här exemplet visar en implementering av cmdleten Get-processen som innehåller en `Name` parametern.

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

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
