---
title: GetProcessSample04 exemplet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aa2aa4c4-3457-4601-806a-801afe3dcc80
caps.latest.revision: 6
ms.openlocfilehash: 095bebf868efd00f8eeaec979a5606f140714cb1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068036"
---
# <a name="getprocesssample04-sample"></a>GetProcessSample04 – exempel

Detta exempel visar hur du implementerar en cmdlet som hämtar processer på den lokala datorn. Den genererar en oändliga fel om ett fel inträffar vid hämtning av en process. Denna cmdlet är en förenklad version av den `Get-Process` cmdlet som tillhandahålls av Windows PowerShell 2.0.

## <a name="how-to-build-the-sample-using-visual-studio"></a>Hur du skapar exemplet med Visual Studio.

1. Navigera till mappen GetProcessSample04 med Windows PowerShell 2.0 SDK för installerade. Standardplatsen är C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample04.

2. Dubbelklicka på ikonen för lösningsfilen (.sln). Exempelprojektet öppnas i Visual Studio.

3. I den **skapa** menyn och välj **skapa lösning**.

    Biblioteket för exemplet skapas i standardmappar \bin eller \bin\debug.

### <a name="how-to-run-the-sample"></a>Hur du kör exemplet

1. Skapa följande modulmappen:

    `[user]/documents/windowspowershell/modules/GetProcessSample04`

2. Kopiera exemplet sammansättningen till modulmappen.

3. Starta Windows PowerShell

4. Kör följande kommando för att läsa in sammansättningen i Windows PowerShell:

    `Import-module getprossessample04`

5. Kör följande kommando för att köra cmdleten:

    `get-proc`

## <a name="requirements"></a>Krav

Det här exemplet kräver Windows PowerShell 2.0.

## <a name="demonstrates"></a>Visar

Detta exempel visar följande.

- Deklarera en cmdlet-klass med hjälp av Cmdlet-attributet.

- Deklarera en cmdlet-parameter med hjälp av parametern-attributet.

- Anger positionen för parametern.

- Anger att parametern hämtar indata från pipeline. Indata kan hämtas från ett objekt eller ett värde från en egenskap för ett objekt vars egenskapsnamnet är samma som parameternamnet.

- Deklarera en verifieringsattribut för parametern indata.

- Hantering av ett oändliga fel och skriver ett felmeddelande till felströmmen.

## <a name="example"></a>Exempel

Det här exemplet visar hur du skapar en cmdlet som hanterar oändliga fel, skriver felmeddelanden till felströmmen.

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

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
