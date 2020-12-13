---
ms.date: 09/13/2016
ms.topic: reference
title: GetProcessSample01 – exempel
description: GetProcessSample01 – exempel
ms.openlocfilehash: 159c277d17a8551d2b5c52377a230babacafc9ab
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652762"
---
# <a name="getprocesssample01-sample"></a>GetProcessSample01 – exempel

Det här exemplet visar hur du implementerar en cmdlet som hämtar processerna på den lokala datorn. Denna cmdlet är en förenklad version av `Get-Process` cmdleten som tillhandahålls av Windows PowerShell 2,0.

## <a name="how-to-build-the-sample-by-using-visual-studio"></a>Så här skapar du exemplet med hjälp av Visual Studio.

1. Med Windows PowerShell 2,0 SDK installerat navigerar du till mappen GetProcessSample01 Standard platsen är C:\Program Files (x86) \Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\GetProcessSample01.

2. Dubbelklicka på ikonen för lösnings filen (. SLN). Detta öppnar exempelprojektet i Microsoft Visual Studio.

3. I menyn **build** väljer du **build-lösning**.

  Biblioteket för exemplet skapas i standardmappen \Bin eller \Bin\Debug.

### <a name="how-to-run-the-sample"></a>Köra exemplet

1. Öppna ett kommandotolksfönster.

2. Navigera till den katalog som innehåller Sample. dll-filen.

3. Kör InstallUtil "GetProcessSample01.dll".

4. Starta Windows PowerShell

5. Kör följande kommando för att lägga till snapin-modulen i gränssnittet.

   `Add-PSSnapin GetProcPSSnapIn01`

6. Ange följande kommando för att köra cmdleten. `get-proc`

   `get-proc`

   Detta är ett exempel på utdata som resulterar i följande steg.

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

Det här exemplet kräver Windows PowerShell 1,0 eller senare.

## <a name="demonstrates"></a>Demonstrationer

Det här exemplet demonstrerar följande.

- Skapar en grundläggande exempel-cmdlet.

- Definiera en cmdlet-klass med hjälp av cmdlet-attributet.

- Skapa en snapin-modul som fungerar med både Windows PowerShell 1,0 och Windows PowerShell 2,0. Efterföljande exempel använder moduler i stället för snapin-moduler så att de kräver Windows PowerShell 2,0.

## <a name="example"></a>Exempel

Det här exemplet visar hur du skapar en enkel cmdlet och dess snapin-modul.

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

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
