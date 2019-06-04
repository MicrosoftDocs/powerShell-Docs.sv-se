---
ms.date: 12/14/2018
keywords: PowerShell cmdlet
title: Skriva bärbar moduler
ms.openlocfilehash: 237f6aaea0ed019c54d04a8477d7a456edf00910
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470990"
---
# <a name="portable-modules"></a>Bärbar moduler

Windows PowerShell är avsedd för [.NET Framework][] medan PowerShell Core är avsedd för [.NET Core][]. Bärbar moduler är moduler som fungerar i både Windows PowerShell och PowerShell Core. .NET Framework och .NET Core är mycket kompatibel, finns men det skillnader i de tillgängliga API: er mellan två. Det finns också skillnader i API: er i Windows PowerShell och PowerShell Core. Moduler som är avsedd att användas i båda miljöerna behöver känna till dessa skillnader.

## <a name="porting-an-existing-module"></a>Porta en modul

### <a name="porting-a-pssnapin"></a>Porta en PSSnapIn

PowerShell [snapin-modulen](/powershell/developer/cmdlet/modules-and-snap-ins) stöds inte i PowerShell Core. Dock är det enkelt att konvertera en PSSnapIn till en PowerShell-modul. Registreringskod PSSnapIn är vanligtvis i en enda källa-fil av en klass som härleds från [PSSnapIn][].
Ta bort den här källfilen från build; Det är inte längre behövs.

Använd [New-ModuleManifest][] att skapa en ny modulmanifestet som ersätter behovet av PSSnapIn Registreringskod. Vissa värden från den **PSSnapIn** (till exempel **beskrivning**) kan återanvändas i modulmanifestet.

Den **RootModule** egenskapen i modulmanifestet ska anges till namnet på sammansättningen (dll) som implementerar cmdletarna.

### <a name="the-net-portability-analyzer-aka-apiport"></a>.NET portabilitet Analyzer (även kallat APIPort)

Till port moduler som skrivits för Windows PowerShell för att arbeta med PowerShell Core, börja med den [.NET portabilitet Analyzer][]. Kör det här verktyget mot din kompilerad sammansättning att avgöra om .NET API: er används i modulen är kompatibla med .NET Framework, .NET Core och andra .NET-körningar. Verktyget föreslår alternativa API: er om de finns. Annars kan du behöva lägga till [Runtime-kontroller][] och begränsa funktioner som inte ingår i specifika körningar.

## <a name="creating-a-new-module"></a>Skapa en ny modul

Om du skapar en ny modul rekommendationen är att använda den [.NET CLI][].

### <a name="installing-the-powershell-standard-module-template"></a>Installera PowerShell Standard modulen mallen

När .NET CLI har installerats kan du installera en mallbibliotek för att generera en enkel PowerShell-modul.
Modulen är kompatibel med Windows PowerShell PowerShell Core, Windows, Linux och macOS.

I följande exempel visas hur du installerar mallen:

```powershell
dotnet new -i Microsoft.PowerShell.Standard.Module.Template
```

```output
  Restoring packages for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj...
  Installing Microsoft.PowerShell.Standard.Module.Template 0.1.3.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\obj\restore.csproj.nuget.g.targets.
  Restore completed in 1.66 sec for C:\Users\Steve\.templateengine\dotnetcli\v2.1.302\scratch\restore.csproj.

Usage: new [options]

Options:
  -h, --help          Displays help for this command.
  -l, --list          Lists templates containing the specified name. If no name is specified, lists all templates.
  -n, --name          The name for the output being created. If no name is specified, the name of the current directory is used.
  -o, --output        Location to place the generated output.
  -i, --install       Installs a source or a template pack.
  -u, --uninstall     Uninstalls a source or a template pack.
  --nuget-source      Specifies a NuGet source to use during install.
  --type              Filters templates based on available types. Predefined values are "project", "item" or "other".
  --force             Forces content to be generated even if it would change existing files.
  -lang, --language   Filters templates based on language and specifies the language of the template to create.


Templates                                         Short Name         Language          Tags
----------------------------------------------------------------------------------------------------------------------------
Console Application                               console            [C#], F#, VB      Common/Console
Class library                                     classlib           [C#], F#, VB      Common/Library
PowerShell Standard Module                        psmodule           [C#]              Library/PowerShell/Module
...
```

### <a name="creating-a-new-module-project"></a>Skapa ett nytt projekt i modulen

När mallen har installerats kan skapa du ett nytt PowerShell-modulen projekt med hjälp av mallen. I det här exemplet kallas exempelmodulen 'myModule'.

```
PS> mkdir myModule

    Directory: C:\Users\Steve

Mode LastWriteTime Length Name
---- ------------- ------ ----
d----- 8/3/2018 2:41 PM myModule

PS> cd myModule
PS C:\Users\Steve\myModule> dotnet new psmodule

The template "PowerShell Standard Module" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on C:\Users\Steve\myModule\myModule.csproj...
  Restoring packages for C:\Users\Steve\myModule\myModule.csproj...
  Installing PowerShellStandard.Library 5.1.0.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.props.
  Generating MSBuild file C:\Users\Steve\myModule\obj\myModule.csproj.nuget.g.targets.
  Restore completed in 1.76 sec for C:\Users\Steve\myModule\myModule.csproj.

Restore succeeded.
```

### <a name="building-the-module"></a>Att skapa modulen

Använd standard .NET CLI-kommandon för att skapa projektet.

```powershell
dotnet build
```

```output
PS C:\Users\Steve\myModule> dotnet build
Microsoft (R) Build Engine version 15.7.179.6572 for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 76.85 ms for C:\Users\Steve\myModule\myModule.csproj.
  myModule -> C:\Users\Steve\myModule\bin\Debug\netstandard2.0\myModule.dll

Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:05.40
```

### <a name="testing-the-module"></a>Testa modulen

När du har skapat modulen kan du importera den och kör exempel-cmdlet.

```powershell
ipmo .\bin\Debug\netstandard2.0\myModule.dll
Test-SampleCmdlet -?
Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat
```

```output
PS C:\Users\Steve\myModule> ipmo .\bin\Debug\netstandard2.0\myModule.dll
PS C:\Users\Steve\myModule> Test-SampleCmdlet -?

NAME
    Test-SampleCmdlet

SYNTAX
    Test-SampleCmdlet [-FavoriteNumber] <int> [[-FavoritePet] {Cat | Dog | Horse}] [<CommonParameters>]


ALIASES
    None


REMARKS
    None


PS C:\Users\Steve\myModule> Test-SampleCmdlet -FavoriteNumber 7 -FavoritePet Cat

FavoriteNumber FavoritePet
-------------- -----------
             7 Cat
```

I följande avsnitt beskrivs i detalj några av de tekniker som används av den här mallen.

## <a name="net-standard-library"></a>.NET-standardbibliotek

[.NET-standard][] är en formella specifikation av .NET API: er som är tillgängliga i alla .NET-implementeringar. Hanterad kod som riktar in sig på .NET Standard fungerar med .NET Framework och .NET Core-versioner som är kompatibla med den versionen av .NET-Standard.

> [!NOTE]
> Även om ett API kan finnas i .NET Standard API-implementering i .NET Core kan vara en `PlatformNotSupportedException` vid körning, så för att verifiera kompatibilitet med Windows PowerShell och PowerShell Core bästa praxis är att köra tester för i båda miljöerna.
> Köra testerna på Linux och macOS om din modul är avsedd att vara plattformsoberoende.

Inriktning på .NET Standard hjälper till att säkerställa att som modulen utvecklas inkompatibla API: er inte av misstag bli presenterade i modulen. Inkompatibiliteter identifieras vid kompilering i stället för körning.

Det inte krävs till målet för .NET Standard för en modul med både Windows PowerShell och PowerShell Core, så länge du använder kompatibla API: er. Mellanliggande språk (IL) är kompatibelt mellan två körningar. Du kan använda .NET Framework 4.6.1, som är kompatibel med .NET Standard 2.0. Om du inte använder API: er utanför .NET Standard 2.0 fungerar modulens med PowerShell Core 6 utan att kompileras om.

## <a name="powershell-standard-library"></a>PowerShell-Standard-biblioteket

Den [PowerShell Standard][] biblioteket är en formella specifikation av PowerShell APIs tillgänglig i alla PowerShell-versioner är större än eller lika med versionen av som standard.

Till exempel [PowerShell Standard 5.1][] är kompatibelt med Windows PowerShell 5.1- och PowerShell Core 6.0 eller senare.

Vi rekommenderar att du kompilera modulens med hjälp av PowerShell-standardbibliotek. Biblioteket säkerställer API: er är tillgängliga och implementerade både i Windows PowerShell och PowerShell Core 6.
PowerShell är tänkt att alltid vara vidarebefordran-kompatibel. En modul som skapats med hjälp av PowerShell Standard biblioteket 5.1 kommer alltid att vara kompatibel med framtida versioner av PowerShell.

## <a name="module-manifest"></a>Modulmanifestet

### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a>Som visar kompatibilitet med Windows PowerShell och PowerShell Core

När du har validerat att modulens fungerar både med Windows PowerShell och PowerShell Core modulmanifestet uttryckligen ska indikera kompatibilitet med hjälp av den [CompatiblePSEditions][] egenskapen. Värdet `Desktop` innebär att modulen är kompatibel med Windows PowerShell, vid värdet `Core` innebär att modulen är kompatibel med PowerShell Core. Både `Desktop` och `Core` innebär att modulen är kompatibelt med Windows PowerShell- och PowerShell Core.

> [!NOTE]
> `Core` automatiskt innebär inte att modulen är kompatibel med Windows, Linux och macOS.
> Den **CompatiblePSEditions** egenskapen introducerades i PowerShell v5. Modulen manifest som använder den **CompatiblePSEditions** egenskapen inte att läsa in i tidigare versioner än PowerShell v5.

### <a name="indicating-os-compatibility"></a>Om OS-kompatibilitet

Verifiera först att modulens fungerar på Linux och macOS. Därefter visa kompatibilitet med dessa operativsystem i modulmanifestet. Detta gör det enklare för användarna att hitta din modul för deras operativsystem när publiceras till den [PowerShell-galleriet][].

I modulmanifestet, den `PrivateData` egenskapen har en `PSData` underordnade egenskapen. Den valfria `Tags` egenskapen för `PSData` tar en matris med värden som visas i PowerShell-galleriet. PowerShell-galleriet har stöd för följande kompatibilitet värden:

| Tagg               | Beskrivning                                |
|-------------------|--------------------------------------------|
| PSEdition_Core    | Kompatibel med PowerShell Core 6          |
| PSEdition_Desktop | Kompatibel med Windows PowerShell         |
| Windows           | Kompatibel med Windows                    |
| Linux             | Kompatibel med Linux (ingen specifik distribution) |
| macOS             | Kompatibla med macOS                      |

Exempel:

```powershell
@{
    GUID = "4ae9fd46-338a-459c-8186-07f910774cb8"
    Author = "Microsoft Corporation"
    CompanyName = "Microsoft Corporation"
    Copyright = "(C) Microsoft Corporation. All rights reserved."
    HelpInfoUri = "https://go.microsoft.com/fwlink/?linkid=855962"
    ModuleVersion = "1.2.4"
    PowerShellVersion = "3.0"
    ClrVersion = "4.0"
    RootModule = "PackageManagement.psm1"
    Description = 'PackageManagement (a.k.a. OneGet) is a new way to discover and install software packages from around the web.
 It is a manager or multiplexer of existing package managers (also called package providers) that unifies Windows package management with a single Windows PowerShell interface. With PackageManagement, you can do the following.
  - Manage a list of software repositories in which packages can be searched, acquired and installed
  - Discover software packages
  - Seamlessly install, uninstall, and inventory packages from one or more software repositories'

    CmdletsToExport = @(
        'Find-Package',
        'Get-Package',
        'Get-PackageProvider',
        'Get-PackageSource',
        'Install-Package',
        'Import-PackageProvider'
        'Find-PackageProvider'
        'Install-PackageProvider'
        'Register-PackageSource',
        'Set-PackageSource',
        'Unregister-PackageSource',
        'Uninstall-Package'
        'Save-Package'
    )

    FormatsToProcess  = @('PackageManagement.format.ps1xml')

    PrivateData = @{
        PSData = @{
            Tags = @('PackageManagement', 'PSEdition_Core', 'PSEdition_Desktop', 'Windows', 'Linux', 'macOS')
            ProjectUri = 'https://oneget.org'
        }
    }
}
```

<!-- reference links -->
[.NET Framework]: /dotnet/framework/
[.NET Core]: /dotnet/core/
[PSSnapIn]: /dotnet/api/system.management.automation.pssnapin
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[Runtime-kontroller]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[.NET CLI]: /dotnet/core/tools/?tabs=netcore2x
[.NET-standard]: /dotnet/standard/net-standard
[PowerShell Standard]: https://github.com/PowerShell/PowerShellStandard
[PowerShell Standard 5.1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell-galleriet]: https://www.powershellgallery.com
[.NET portabilitet Analyzer]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/gallery/concepts/module-psedition-support
