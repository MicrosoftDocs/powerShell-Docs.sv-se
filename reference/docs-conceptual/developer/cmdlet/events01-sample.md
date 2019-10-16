---
title: Events01-exempel | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 27d0ee5e-2589-4530-92ef-c09996b80994
caps.latest.revision: 10
ms.openlocfilehash: 8f745cc0e5ef6db7a6bbdf39d826103f3b8a98ce
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359359"
---
# <a name="events01-sample"></a>Events01 – exempel

Det här exemplet visar hur du skapar en-cmdlet som gör att användaren kan registrera sig för händelser som aktive ras av [system. io. FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).
Med den här cmdleten kan användarna registrera en åtgärd som ska utföras när en fil skapas under en angiven katalog.
Det här exemplet härleds från Bask Lassen [Microsoft. PowerShell. commands. ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) .

## <a name="how-to-build-the-sample-by-using-visual-studio"></a>Så här skapar du exemplet med hjälp av Visual Studio.

1. Med Windows PowerShell 2,0 SDK installerat navigerar du till mappen Events01
   Standard platsen är `C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01`.

2. Dubbelklicka på ikonen för lösnings filen (. SLN).
   Detta öppnar exempelprojektet i Microsoft Visual Studio.

3. I menyn **build** väljer du **build-lösning**.
   Biblioteket för exemplet skapas i standard `\bin`-eller `\bin\debug`-mappar.

### <a name="how-to-run-the-sample"></a>Så här kör du exemplet

1. Skapa följande modul-mapp:

    `[user]/documents/windowspowershell/modules/events01`

2. Kopiera biblioteks filen för exemplet till module-mappen.

3. Starta Windows PowerShell

4. Kör följande kommando för att läsa in cmdleten i Windows PowerShell:

    ```powershell
    import-module events01
    ```

5. Använd cmdleten register-FileSystemEvent för att registrera en åtgärd som ska skriva ett meddelande när en fil skapas i TEMP-katalogen.

    ```powershell
    Register-FileSystemEvent $env:temp Created -filter "*.txt" -action { Write-Host "A file was created in the TEMP directory" }
    ```

6. Skapa en fil under TEMP-katalogen och Observera att åtgärden körs (meddelandet visas).

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

Det här exemplet kräver Windows PowerShell 2,0.

## <a name="demonstrates"></a>Visat

Det här exemplet demonstrerar följande.

### <a name="how-to-write-a-cmdlet-for-event-registration"></a>Så här skriver du en cmdlet för händelse registrering

Cmdleten härleds från klassen [Microsoft. PowerShell. commands. ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) , som ger stöd för parametrar som är gemensamma för cmdletarna `Register-*Event`.
Cmdletar som är härledda från [Microsoft. PowerShell. commands. ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) behöver bara definiera sina specifika parametrar och åsidosätta de abstrakta metoderna `GetSourceObject` och @no__t 2.

## <a name="example"></a>Exempel

Det här exemplet visar hur du registrerar för händelser som aktive ras av [system. io. FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).

```csharp
namespace Sample
{
    using System;
    using System.IO;
    using System.Management.Automation;
    using System.Management.Automation.Runspaces;
    using Microsoft.PowerShell.Commands;

    [Cmdlet(VerbsLifecycle.Register, "FileSystemEvent")]
    public class RegisterObjectEventCommand : ObjectEventRegistrationBase
    {
        /// <summary>The FileSystemWatcher that exposes the events.</summary>
        private FileSystemWatcher fileSystemWatcher = new FileSystemWatcher();

        /// <summary>Name of the event to which the cmdlet registers.</summary>
        private string eventName = null;

        /// <summary>
        /// Gets or sets the path that will be monitored by the FileSystemWatcher.
        /// </summary>
        [Parameter(Mandatory = true, Position = 0)]
        public string Path
        {
            get
            {
                return this.fileSystemWatcher.Path;
            }

            set
            {
                this.fileSystemWatcher.Path = value;
            }
        }

        /// <summary>
        /// Gets or sets the name of the event to which the cmdlet registers.
        /// <para>
        /// Currently System.IO.FileSystemWatcher exposes 6 events: Changed, Created,
        /// Deleted, Disposed, Error, and Renamed. Check the MSDN documentation of
        /// FileSystemWatcher for details on each event.
        /// </para>
        /// </summary>
        [Parameter(Mandatory = true, Position = 1)]
        public string EventName
        {
            get
            {
                return this.eventName;
            }

            set
            {
                this.eventName = value;
            }
        }

        /// <summary>
        /// Gets or sets the filter that will be user by the FileSystemWatcher.
        /// </summary>
        [Parameter(Mandatory = false)]
        public string Filter
        {
            get
            {
                return this.fileSystemWatcher.Filter;
            }

            set
            {
                this.fileSystemWatcher.Filter = value;
            }
        }

        /// <summary>
        /// Derived classes must implement this method to return the object that generates
        /// the events to be monitored.
        /// </summary>
        /// <returns> This sample returns an instance of System.IO.FileSystemWatcher</returns>
        protected override object GetSourceObject()
        {
            return this.fileSystemWatcher;
        }

        /// <summary>
        /// Derived classes must implement this method to return the name of the event to
        /// be monitored. This event must be exposed by the input object.
        /// </summary>
        /// <returns> This sample returns the event specified by the user with the -EventName parameter.</returns>
        protected override string GetSourceObjectEventName()
        {
            return this.eventName;
        }
    }
}
```

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-cmdlet](writing-a-windows-powershell-cmdlet.md)