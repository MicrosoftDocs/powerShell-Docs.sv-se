---
title: GetProcessSample01 exemplet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b48bf80-cbf0-4cb1-8d5b-3b8d06196598
caps.latest.revision: 10
ms.openlocfilehash: 00190c7350cb0f1cfc5c389b56e48e9397480446
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068070"
---
# <a name="getprocesssample01-sample"></a>GetProcessSample01 – exempel

Detta exempel visar hur du implementerar en cmdlet som hämtar processer på den lokala datorn. Denna cmdlet är en förenklad version av den `Get-Process` cmdlet som tillhandahålls av Windows PowerShell 2.0.

## <a name="how-to-build-the-sample-by-using-visual-studio"></a>Hur du skapar exemplet med hjälp av Visual Studio.

1. Navigera till mappen GetProcessSample01 med Windows PowerShell 2.0 SDK för installerade. Standardplatsen är C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01.

2. Dubbelklicka på ikonen för lösningsfilen (.sln). Exempelprojektet öppnas i Microsoft Visual Studio.

3. I den **skapa** menyn och välj **skapa lösning**.

  Biblioteket för exemplet skapas i standardmappar \bin eller \bin\debug.

### <a name="how-to-run-the-sample"></a>Hur du kör exemplet

1. Öppna Kommandotolken.

2. Navigera till den katalog som innehåller till exempel DLL-fil.

3. Kör installutil ”GetProcessSample01.dll”.

4. Starta Windows PowerShell

5. Kör följande kommando för att lägga till snapin-modulen i gränssnittet.

   `Add-PSSnapin GetProcPSSnapIn01`

6. Ange följande kommando för att köra cmdleten. `get-proc`

   `get-proc`

   Det här är ett exempel på utdata resulterar i följande steg.

   ```output
   Id              Name            State      HasMoreData     Location             Command
   --              ----            -----      -----------     --------             -------
   1               26932870-d3b... NotStarted False                                 Write-Host "A f...

   ```

   ```powershell
   Set-Content $env:temp\test.txt "This is a test file"
   ```

   ```output
   A file was created in the TEMP directory
   ```

## <a name="requirements"></a>Krav

Det här exemplet kräver Windows PowerShell 1.0 eller senare.

## <a name="demonstrates"></a>Visar

Detta exempel visar följande.

- Skapa en grundläggande exempel-cmdlet.

- Definiera en cmdlet-klass med hjälp av Cmdlet-attributet.

- Skapa en snapin-modul som fungerar både med Windows PowerShell 1.0 och Windows PowerShell 2.0. Efterföljande prover använder moduler i stället för snapin-moduler så att de kräver Windows PowerShell 2.0.

## <a name="example"></a>Exempel

Detta exempel visar hur du skapar en enkel cmdlet och dess snapin-modulen.

```csharp
using System;
using System.Diagnostics;
using System.Management.Automation;             //Windows PowerShell namespace
using System.ComponentModel;

namespace Microsoft.Samples.PowerShell.Commands
{

   #region GetProcCommand

   /// <summary>
   /// This class implements the Get-Proc cmdlet.
   /// </summary>
   [Cmdlet(VerbsCommon.Get, "Proc")]
   public class GetProcCommand : Cmdlet
   {
      #region Cmdlet Overrides

      /// <summary>
      /// The ProcessRecord method calls the Process.GetProcesses
      /// method to retrieve the processes of the local computer.
      /// Then, the WriteObject method writes the associated processes
      /// to the pipeline.
      /// </summary>
      protected override void ProcessRecord()
      {
         // Retrieve the current processes.
         Process[] processes = Process.GetProcesses();

         // Write the processes to the pipeline to make them available
         // to the next cmdlet. The second argument (true) tells Windows
         // PowerShell to enumerate the array and to send one process
         // object at a time to the pipeline.
         WriteObject(processes, true);
      }

      #endregion Overrides

   } //GetProcCommand

   #endregion GetProcCommand

   #region PowerShell snap-in

   /// <summary>
   /// Create this sample as an PowerShell snap-in
   /// </summary>
   [RunInstaller(true)]
   public class GetProcPSSnapIn01 : PSSnapIn
   {
       /// <summary>
       /// Create an instance of the GetProcPSSnapIn01
       /// </summary>
       public GetProcPSSnapIn01()
           : base()
       {
       }

       /// <summary>
       /// Get a name for this PowerShell snap-in. This name will be used in registering
       /// this PowerShell snap-in.
       /// </summary>
       public override string Name
       {
           get
           {
               return "GetProcPSSnapIn01";
           }
       }

       /// <summary>
       /// Vendor information for this PowerShell snap-in.
       /// </summary>
       public override string Vendor
       {
           get
           {
               return "Microsoft";
           }
       }

       /// <summary>
       /// Gets resource information for vendor. This is a string of format:
       /// resourceBaseName,resourceName.
       /// </summary>
       public override string VendorResource
       {
           get
           {
               return "GetProcPSSnapIn01,Microsoft";
           }
       }

       /// <summary>
       /// Description of this PowerShell snap-in.
       /// </summary>
       public override string Description
       {
           get
           {
               return "This is a PowerShell snap-in that includes the get-proc cmdlet.";
           }
       }
   }

   #endregion PowerShell snap-in
}
```

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)