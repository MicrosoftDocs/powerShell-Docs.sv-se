---
title: Events01-exempel | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c7b0f759ca6f3c078649a462eac1713e8214a237
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87774465"
---
# <a name="events01-sample"></a><span data-ttu-id="b3328-102">Events01 – exempel</span><span class="sxs-lookup"><span data-stu-id="b3328-102">Events01 Sample</span></span>

<span data-ttu-id="b3328-103">Det här exemplet visar hur du skapar en-cmdlet som gör att användaren kan registrera sig för händelser som aktive ras av [system. io. FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span><span class="sxs-lookup"><span data-stu-id="b3328-103">This sample shows how to create a cmdlet that allows the user to register for events that are raised by [System.IO.FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span>
<span data-ttu-id="b3328-104">Med den här cmdleten kan användarna registrera en åtgärd som ska utföras när en fil skapas under en angiven katalog.</span><span class="sxs-lookup"><span data-stu-id="b3328-104">With this cmdlet, users can register an action to execute when a file is created under a specific directory.</span></span>
<span data-ttu-id="b3328-105">Det här exemplet härleds från Bask Lassen [Microsoft. PowerShell. commands. ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) .</span><span class="sxs-lookup"><span data-stu-id="b3328-105">This sample derives from the [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) base class.</span></span>

## <a name="how-to-build-the-sample-by-using-visual-studio"></a><span data-ttu-id="b3328-106">Så här skapar du exemplet med hjälp av Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b3328-106">How to build the sample by using Visual Studio.</span></span>

1. <span data-ttu-id="b3328-107">Med Windows PowerShell 2,0 SDK installerat navigerar du till mappen Events01</span><span class="sxs-lookup"><span data-stu-id="b3328-107">With the Windows PowerShell 2.0 SDK installed, navigate to the Events01 folder.</span></span>
   <span data-ttu-id="b3328-108">Standardplatsen är `C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01`.</span><span class="sxs-lookup"><span data-stu-id="b3328-108">The default location is `C:\Program Files (x86)\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\csharp\Events01`.</span></span>

2. <span data-ttu-id="b3328-109">Dubbelklicka på ikonen för lösnings filen (. SLN).</span><span class="sxs-lookup"><span data-stu-id="b3328-109">Double-click the icon for the solution (.sln) file.</span></span>
   <span data-ttu-id="b3328-110">Detta öppnar exempelprojektet i Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b3328-110">This opens the sample project in Microsoft Visual Studio.</span></span>

3. <span data-ttu-id="b3328-111">I menyn **build** väljer du **build-lösning**.</span><span class="sxs-lookup"><span data-stu-id="b3328-111">In the **Build** menu, select **Build Solution**.</span></span>
   <span data-ttu-id="b3328-112">Biblioteket för exemplet skapas i standard- `\bin` eller- `\bin\debug` mapparna.</span><span class="sxs-lookup"><span data-stu-id="b3328-112">The library for the sample will be built in the default `\bin` or `\bin\debug` folders.</span></span>

### <a name="how-to-run-the-sample"></a><span data-ttu-id="b3328-113">Köra exemplet</span><span class="sxs-lookup"><span data-stu-id="b3328-113">How to run the sample</span></span>

1. <span data-ttu-id="b3328-114">Skapa följande modul-mapp:</span><span class="sxs-lookup"><span data-stu-id="b3328-114">Create the following module folder:</span></span>

    `[user]/documents/windowspowershell/modules/events01`

2. <span data-ttu-id="b3328-115">Kopiera biblioteks filen för exemplet till module-mappen.</span><span class="sxs-lookup"><span data-stu-id="b3328-115">Copy the library file for the sample to the module folder.</span></span>

3. <span data-ttu-id="b3328-116">Starta Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b3328-116">Start Windows PowerShell.</span></span>

4. <span data-ttu-id="b3328-117">Kör följande kommando för att läsa in cmdleten i Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="b3328-117">Run the following command to load the cmdlet into Windows PowerShell:</span></span>

    ```powershell
    import-module events01
    ```

5. <span data-ttu-id="b3328-118">Använd cmdleten register-FileSystemEvent för att registrera en åtgärd som ska skriva ett meddelande när en fil skapas i TEMP-katalogen.</span><span class="sxs-lookup"><span data-stu-id="b3328-118">Use the Register-FileSystemEvent cmdlet to register an action that will write a message when a file is created under the TEMP directory.</span></span>

    ```powershell
    Register-FileSystemEvent $env:temp Created -filter "*.txt" -action { Write-Host "A file was created in the TEMP directory" }
    ```

6. <span data-ttu-id="b3328-119">Skapa en fil under TEMP-katalogen och Observera att åtgärden körs (meddelandet visas).</span><span class="sxs-lookup"><span data-stu-id="b3328-119">Create a file under the TEMP directory and note that the action is executed (the message is displayed).</span></span>

<span data-ttu-id="b3328-120">Detta är ett exempel på utdata som resulterar i följande steg.</span><span class="sxs-lookup"><span data-stu-id="b3328-120">This is a sample output that results by following these steps.</span></span>

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

## <a name="requirements"></a><span data-ttu-id="b3328-121">Krav</span><span class="sxs-lookup"><span data-stu-id="b3328-121">Requirements</span></span>

<span data-ttu-id="b3328-122">Det här exemplet kräver Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="b3328-122">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="b3328-123">Demonstrationer</span><span class="sxs-lookup"><span data-stu-id="b3328-123">Demonstrates</span></span>

<span data-ttu-id="b3328-124">Det här exemplet demonstrerar följande.</span><span class="sxs-lookup"><span data-stu-id="b3328-124">This sample demonstrates the following.</span></span>

### <a name="how-to-write-a-cmdlet-for-event-registration"></a><span data-ttu-id="b3328-125">Så här skriver du en cmdlet för händelse registrering</span><span class="sxs-lookup"><span data-stu-id="b3328-125">How to write a cmdlet for event registration</span></span>

<span data-ttu-id="b3328-126">Cmdleten härleds från klassen [Microsoft. PowerShell. commands. ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) , som ger stöd för parametrar som är gemensamma för `Register-*Event` cmdletarna.</span><span class="sxs-lookup"><span data-stu-id="b3328-126">The cmdlet derives from the [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) class, which provides support for parameters common to the `Register-*Event` cmdlets.</span></span>
<span data-ttu-id="b3328-127">Cmdletar som är härledda från [Microsoft. PowerShell. commands. ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) behöver bara definiera sina specifika parametrar och åsidosätta `GetSourceObject` `GetSourceObjectEventName` metoderna och.</span><span class="sxs-lookup"><span data-stu-id="b3328-127">Cmdlets that are derived from [Microsoft.PowerShell.Commands.ObjectEventRegistrationBase](/dotnet/api/Microsoft.PowerShell.Commands.ObjectEventRegistrationBase) need only to define their particular parameters and override the `GetSourceObject` and `GetSourceObjectEventName` abstract methods.</span></span>

## <a name="example"></a><span data-ttu-id="b3328-128">Exempel</span><span class="sxs-lookup"><span data-stu-id="b3328-128">Example</span></span>

<span data-ttu-id="b3328-129">Det här exemplet visar hur du registrerar för händelser som aktive ras av [system. io. FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span><span class="sxs-lookup"><span data-stu-id="b3328-129">This sample shows how to register for events raised by [System.IO.FileSystemWatcher](/dotnet/api/System.IO.FileSystemWatcher).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b3328-130">Se även</span><span class="sxs-lookup"><span data-stu-id="b3328-130">See Also</span></span>

[<span data-ttu-id="b3328-131">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="b3328-131">Writing a Windows PowerShell Cmdlet</span></span>](writing-a-windows-powershell-cmdlet.md)
