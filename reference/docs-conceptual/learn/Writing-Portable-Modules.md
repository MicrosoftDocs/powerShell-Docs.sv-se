---
ms.date: 01/10/2020
keywords: PowerShell, cmdlet
title: Skriva portabla moduler
ms.openlocfilehash: 124e6efadfd07b8c5214a5c0446b1589f7142388
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "76022238"
---
# <a name="portable-modules"></a>Bärbara moduler

Windows PowerShell är skrivet för [.NET Framework][] medan PowerShell-kärnan skrivs för [.net Core][]. Bärbara moduler är moduler som fungerar både i Windows PowerShell och PowerShell Core. Även om .NET Framework och .NET Core är mycket kompatibla finns det skillnader i de tillgängliga API: erna mellan de två. Det finns också skillnader i de API: er som är tillgängliga i Windows PowerShell och PowerShell Core. Moduler som är avsedda att användas i båda miljöerna måste vara medvetna om dessa skillnader.

## <a name="porting-an-existing-module"></a>Portning av en befintlig modul

### <a name="porting-a-pssnapin"></a>Porting a PSSnapIn

PowerShell- [modulerna](/powershell/scripting/developer/cmdlet/modules-and-snap-ins) stöds inte i PowerShell Core. Det är dock enkelt att konvertera en PSSnapIn till en PowerShell-modul. Normalt är registrerings koden PSSnapIn i en enda källfil för en klass som härleds från [PSSnapIn][].
Ta bort den här käll filen från versionen. det behövs inte längre.

Använd [New-ModuleManifest][] för att skapa ett nytt modul-manifest som ersätter behovet av registrerings koden för PSSnapIn. Några av värdena från **PSSnapIn** (till exempel **Beskrivning**) kan återanvändas i manifestet för modulen.

Egenskapen **RootModule** i modulen manifest ska anges till namnet på sammansättningen (dll) som implementerar cmdletarna.

### <a name="the-net-portability-analyzer-aka-apiport"></a>.NET-portbaserad analys för aka (APIPort)

Om du vill att moduler som är skrivna för Windows PowerShell ska fungera med PowerShell-kärnan börjar du med [.net-ports Analyzer][]. Kör det här verktyget mot den kompilerade sammansättningen för att avgöra om de .NET-API: er som används i modulen är kompatibla med .NET Framework, .NET Core och andra .NET-körningar. Verktyget föreslår alternativa API: er om de finns. Annars kan du behöva lägga till [körnings kontroller][] och begränsa funktioner som inte är tillgängliga i vissa körningar.

## <a name="creating-a-new-module"></a>Skapa en ny modul

Om du skapar en ny modul är rekommendationen att använda [.net CLI][].

### <a name="installing-the-powershell-standard-module-template"></a>Installera PowerShell-modulen för standard mal len

När .NET CLI har installerats installerar du ett mall bibliotek för att generera en enkel PowerShell-modul.
Modulen är kompatibel med Windows PowerShell, PowerShell Core, Windows, Linux och macOS.

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

### <a name="creating-a-new-module-project"></a>Skapa ett nytt modul-projekt

När mallen har installerats kan du skapa ett nytt PowerShell-Modulnamn med den mallen. I det här exemplet kallas exempel modulen "module".

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

### <a name="building-the-module"></a>Modulen skapas

Använd standard .NET CLI-kommandon för att bygga projektet.

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

När du har skapat modulen kan du importera den och köra exempel-cmdleten.

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

I följande avsnitt beskrivs några av de tekniker som används av den här mallen.

## <a name="net-standard-library"></a>.NET standard-bibliotek

[.Net standard][] är en formell specifikation av .NET-API: er som är tillgängliga i alla .net-implementeringar. Hanterad kod för .NET standard fungerar med de .NET Framework-och .NET Core-versioner som är kompatibla med den versionen av .NET standard.

> [!NOTE]
> Även om ett API kan finnas i .NET standard kan API-implementeringen i .NET Core medföra `PlatformNotSupportedException` en vid körning, så för att kontrol lera kompatibilitet med Windows PowerShell och PowerShell Core är det bästa sättet att köra tester för modulen i båda miljöerna.
> Kör även tester på Linux och macOS om modulen är avsedd att vara plattforms oberoende.

Genom att använda .NET standard kan du se till att inkompatibla API: er inte har introducerats av misstag i modulen, eftersom modulen utvecklas. Inkompatibiliteter upptäcks vid kompilering i stället för körning.

Men det är inte nödvändigt att använda .NET standard för att en modul ska fungera med både Windows PowerShell och PowerShell Core, så länge du använder kompatibla API: er. Det mellanliggande språket (IL) är kompatibelt mellan de två körningarna. Du kan rikta .NET Framework 4.6.1, som är kompatibel med .NET standard 2,0. Om du inte använder API: er utanför .NET standard 2,0, fungerar modulen med PowerShell Core 6 utan att kompilera om.

## <a name="powershell-standard-library"></a>PowerShell-standardbibliotek

[PowerShell][] -standardbiblioteket är en formell specifikation av PowerShell-API: er som är tillgängliga i alla PowerShell-versioner som är större än eller lika med den standard versionen.

Till exempel är [PowerShell Standard 5,1][] kompatibelt med både Windows PowerShell 5,1 och PowerShell Core 6,0 eller senare.

Vi rekommenderar att du kompilerar modulen med PowerShell-standardbiblioteket. Biblioteket säkerställer att API: erna är tillgängliga och implementerade i både Windows PowerShell och PowerShell Core 6.
PowerShell-standarden är avsedd att alltid vidarebefordras-kompatibel. En modul som skapats med PowerShell standard library 5,1 är alltid kompatibel med framtida versioner av PowerShell.

## <a name="module-manifest"></a>Modul manifest

### <a name="indicating-compatibility-with-windows-powershell-and-powershell-core"></a>Indikerar kompatibilitet med Windows PowerShell och PowerShell Core

När du har verifierat att modulen fungerar med både Windows PowerShell och PowerShell Core bör modulens manifest uttryckligen indikera kompatibilitet med hjälp av egenskapen [CompatiblePSEditions][] . Värdet `Desktop` innebär att modulen är kompatibel med Windows PowerShell, medan värdet `Core` innebär att modulen är kompatibel med PowerShell Core. Inklusive både `Desktop` och `Core` innebär att modulen är kompatibel med både Windows PowerShell och PowerShell Core.

> [!NOTE]
> `Core`innebär inte automatiskt att modulen är kompatibel med Windows, Linux och macOS.
> Egenskapen **CompatiblePSEditions** introducerades i PowerShell v5. Modul manifest som använder egenskapen **CompatiblePSEditions** kan inte läsas in i tidigare versioner än PowerShell v5.

### <a name="indicating-os-compatibility"></a>Indikerar OS-kompatibilitet

Kontrol lera först att modulen fungerar på Linux och macOS. Sedan anger du kompatibiliteten med dessa operativ system i manifestet för modulen. Detta gör det enklare för användarna att hitta modulen för sitt operativ system när de publiceras till [PowerShell-galleriet][].

I modulen manifest har `PrivateData` egenskapen en `PSData` underordnad egenskap. Den valfria `Tags` egenskapen för `PSData` tar en matris med värden som visas i PowerShell-galleriet. PowerShell-galleriet har stöd för följande kompatibilitetsinställningar:

| Tagga               | Beskrivning                                |
|-------------------|--------------------------------------------|
| PSEdition_Core    | Kompatibel med PowerShell Core 6          |
| PSEdition_Desktop | Kompatibel med Windows PowerShell         |
| Windows           | Kompatibel med Windows                    |
| Linux             | Kompatibel med Linux (inga speciella distribution) |
| macOS             | Kompatibel med macOS                      |

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

## <a name="dependency-on-native-libraries"></a>Beroende av interna bibliotek

Moduler som ska användas i olika operativ system eller processor arkitekturer kan vara beroende av ett hanterat bibliotek som är beroende av vissa interna bibliotek.

Före PowerShell 7 måste det finnas en anpassad kod för att läsa in rätt inbyggda DLL-fil så att det hanterade biblioteket kan hitta det korrekt.

Med PowerShell 7 genomsöks interna binärfiler i undermappar i det hanterade bibliotekets plats enligt en delmängd av [.net RID-katalogens][] notation.

```
managed.dll folder
                |
                |--- 'win-x64' folder
                |       |--- native.dll
                |
                |--- 'win-x86' folder
                |       |--- native.dll
                |
                |--- 'win-arm' folder
                |       |--- native.dll
                |
                |--- 'win-arm64' folder
                |       |--- native.dll
                |
                |--- 'linux-x64' folder
                |       |--- native.so
                |
                |--- 'linux-x86' folder
                |       |--- native.so
                |
                |--- 'linux-arm' folder
                |       |--- native.so
                |
                |--- 'linux-arm64' folder
                |       |--- native.so
                |
                |--- 'osx-x64' folder
                |       |--- native.dylib
```

<!-- reference links -->
[.NET Framework]: /dotnet/framework/
[.NET Core]: /dotnet/core/
[PSSnapIn]: /dotnet/api/system.management.automation.pssnapin
[New-ModuleManifest]: /powershell/module/microsoft.powershell.core/new-modulemanifest
[körnings kontroller]: /dotnet/api/system.runtime.interopservices.runtimeinformation.frameworkdescription#System_Runtime_InteropServices_RuntimeInformation_FrameworkDescription
[.NET CLI]: /dotnet/core/tools/?tabs=netcore2x
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell-standard]: https://github.com/PowerShell/PowerShellStandard
[PowerShell standard 5,1]: https://www.nuget.org/packages/PowerShellStandard.Library/5.1.0
[PowerShell-galleriet]: https://www.powershellgallery.com
[.NET-portbaserad analys]: https://github.com/Microsoft/dotnet-apiport
[CompatiblePSEditions]: /powershell/scripting/gallery/concepts/module-psedition-support
[.NET RID-katalog]: https://docs.microsoft.com/dotnet/core/rid-catalog
