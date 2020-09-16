---
title: Skapa en binär standard biblioteks-modul
description: Med PowerShell-standardbiblioteket kan vi skapa moduler för flera plattformar som fungerar både i PowerShell Core och med Windows PowerShell 5,1.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: ff6a49f70a3fb77f5a30cc909d53bb77b3cd7d43
ms.sourcegitcommit: 8c01e56f0c10ff2637955dc892ea78432d563a7b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/21/2020
ms.locfileid: "88702753"
---
# <a name="how-to-create-a-standard-library-binary-module"></a>Såhär skapar du en binär modul för standardbibliotek

Jag hade nyligen en idé för modulen som jag ville implementera som en binär modul. Jag har ännu inte skapat en med hjälp av [PowerShell-standardbiblioteket][] , så det här är en bra möjlighet. Jag använde guiden [skapa en plattforms oberoende binär modul][] för att skapa den här modulen utan någon hindren.
Vi ska gå vidare till samma process och lägga till en lite extra kommentarer på vägen.

> [!NOTE]
> Den [ursprungliga versionen][] av den här artikeln visas på bloggen som skrivits av [@KevinMarquette][] . PowerShell-teamet tackar för att dela det här innehållet med oss. Ta en titt på hans blogg på [PowerShellExplained.com][].

## <a name="what-is-the-powershell-standard-library"></a>Vad är PowerShell standard library?

Med PowerShell-standardbiblioteket kan vi skapa moduler för flera plattformar som fungerar både i PowerShell Core och med Windows PowerShell 5,1 (eller 3,0).

## <a name="planning-our-module"></a>Planera vår modul

Planen för den här modulen är att skapa en `src` mapp för C#-koden och strukturera resten på samma sätt som för en-skript-modul. Detta omfattar att använda ett build-skript för att kompilera allt i en `output` mapp. Mappstrukturen ser ut så här:

```
MyModule
├───src
├───Output
│   └───MyModule
├───MyModule
│   ├───Data
│   ├───Private
│   └───Public
└───Tests
```

## <a name="getting-started"></a>Komma igång

Jag använder normalt en gips-mall, men min aktuella mall har inte stöd för binär modul än. Inte ett stort avtal. Jag skapar den här gången för tillfället.

Först måste jag skapa mappen och skapa git-lagrings platsen. Jag använder `$module` som plats hållare för modulnamnet. Detta gör det enklare för dig att återanvända dessa exempel vid behov.

```powershell
$module = 'MyModule'
New-Item -Path $module -Type Directory
Set-Location $module
git init
```

Skapa sedan rot nivåns mappar.

```powershell
New-Item -Path 'src' -Type Directory
New-Item -Path 'Output' -Type Directory
New-Item -Path 'Tests' -Type Directory
New-Item -Path $module -Type Directory
```

### <a name="binary-module-setup"></a>Installation av binär modul

Artikeln OS fokuserar på den binära modulen så att vi startar. Det här avsnittet hämtar exempel från guiden [skapa en binär plattforms oberoende modul][] . Läs den här guiden om du behöver mer information eller om du har problem.

Det första du vill göra är att kontrol lera vilken version av [dotNet Core SDK][] som vi har installerat. Jag använder 2.1.4, men du bör ha 2.0.0 eller senare innan du fortsätter.

```powershell
PS> dotnet --version
2.1.4
```

Jag arbetar i `src` mappen för det här avsnittet.

```powershell
Set-Location 'src'
```

Skapa ett nytt klass bibliotek med kommandot dotNet.

```powershell
dotnet new classlib --name $module
```

Detta skapade biblioteks projektet i en undermapp men jag vill inte ha den extra kapslings nivån. Jag ska flytta filerna uppåt en nivå.

```powershell
Move-Item -Path .\$module\* -Destination .\
Remove-Item $module -Recurse
```

Ange .NET Core SDK-versionen för projektet. Jag har 2,1 SDK så jag ska ange 2.1.0.
Använd 2.0.0 om du använder 2,0 SDK: n.

```powershell
dotnet new globaljson --sdk-version 2.1.0
```

Lägg till PowerShell- [NuGet-paketet][] för standard bibliotek i projektet. Se till att du använder den senaste versionen som är tillgänglig för den kompatibilitetsnivå du behöver. Jag skulle använda den senaste versionen som standard, men jag tycker inte att den här modulen använder några funktioner som är nyare än PowerShell 3,0.

```powershell
dotnet add package PowerShellStandard.Library --version 7.0.0-preview.1
```

Vi bör ha en src-mapp som ser ut så här:

```powershell
PS> Get-ChildItem
    Directory: \MyModule\src

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        7/14/2018   9:51 PM                obj
-a----        7/14/2018   9:51 PM             86 Class1.cs
-a----        7/14/2018  10:03 PM            259 MyModule.csproj
-a----        7/14/2018  10:05 PM             45 global.json
```

Nu är vi redo att lägga till vår egen kod i projektet.

### <a name="building-a-binary-cmdlet"></a>Skapa en binär cmdlet

Vi måste uppdatera `src\Class1.cs` för att innehålla denna start-cmdlet:

```csharp
using System;
using System.Management.Automation;

namespace MyModule
{
    [Cmdlet( VerbsDiagnostic.Resolve , "MyCmdlet")]
    public class ResolveMyCmdletCommand : PSCmdlet
    {
        [Parameter(Position=0)]
        public Object InputObject { get; set; }

        protected override void EndProcessing()
        {
            this.WriteObject(this.InputObject);
            base.EndProcessing();
        }
    }
}
```

Byt namn på filen så att den matchar klass namnet.

```powershell
Rename-Item .\Class1.cs .\ResolveMyCmdletCommand.cs
```

Sedan kan vi bygga vår modul.

```powershell
PS> dotnet build

Microsoft (R) Build Engine version 15.5.180.51428 for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

Restore completed in 18.19 ms for C:\workspace\MyModule\src\MyModule.csproj.
MyModule -> C:\workspace\MyModule\src\bin\Debug\netstandard2.0\MyModule.dll

Build succeeded.
    0 Warning(s)
    0 Error(s)

Time Elapsed 00:00:02.19
```

Vi kan anropa `Import-Module` den nya DLL-filen för att läsa in vår nya CMDlet.

```powershell
PS> Import-Module .\bin\Debug\netstandard2.0\$module.dll
PS> Get-Command -Module $module

CommandType Name                    Version Source
----------- ----                    ------- ------
Cmdlet      Resolve-MyCmdlet        1.0.0.0 MyModule
```

Om importen Miss lyckas på systemet kan du prova att uppdatera .NET till 4.7.1 eller senare. Guiden [skapa en binär plattforms oberoende modul][] innehåller mer information om .net-support och kompatibilitet för äldre versioner av .net.

### <a name="module-manifest"></a>Modul manifest

Det är bra att vi kan importera DLL-filen och ha en fungerande modul. Jag vill fortsätta med den och skapa ett modul manifest. Vi behöver manifestet om vi vill publicera till PSGallery senare.

Från roten av vårt projekt kan vi köra det här kommandot för att skapa modulens manifest som vi behöver.

```powershell
$manifestSplat = @{
    Path              = ".\$module\$module.psd1"
    Author            = 'Kevin Marquette'
    NestedModules     = @('bin\MyModule.dll')
    RootModule        = "$module.psm1"
    FunctionsToExport = @('Resolve-MyCmdlet')
}
New-ModuleManifest @manifestSplat
```

Jag ska också skapa en tom modul för framtida PowerShell-funktioner.

```powershell
Set-Content -Value '' -Path ".\$module\$module.psm1"
```

Detta gör att jag kan blanda både normala PowerShell-funktioner och binära cmdlets i samma projekt.

### <a name="building-the-full-module"></a>Skapa hela modulen

Jag kompilerar allt tillsammans i en mapp för utdata. Vi behöver skapa ett build-skript för att göra det. Jag lägger normalt till detta i ett `Invoke-Build` skript, men vi kan hålla det enkelt för det här exemplet. Lägg till detta i en `build.ps1` rot i projektet.

```powershell
$module = 'MyModule'
Push-Location $PSScriptRoot

dotnet build $PSScriptRoot\src -o $PSScriptRoot\output\$module\bin
Copy-Item "$PSScriptRoot\$module\*" "$PSScriptRoot\output\$module" -Recurse -Force

Import-Module "$PSScriptRoot\Output\$module\$module.psd1"
Invoke-Pester "$PSScriptRoot\Tests"
```

Dessa kommandon skapar vår DLL och placerar den i vår `output\$module\bin` mapp. Den kopierar sedan de andra modulens filer till plats.

```
Output
└───MyModule
    │   MyModule.psd1
    │   MyModule.psm1
    │
    └───bin
            MyModule.deps.json
            MyModule.dll
            MyModule.pdb
```

Vi kan nu importera vår modul med psd1-filen.

```powershell
Import-Module ".\Output\$module\$module.psd1"
```

Härifrån kan vi släppa `.\Output\$module` mappen i vår `$env:PSModulePath` katalog så laddar den automatiskt in vårt kommando när vi behöver det.

### <a name="update-dotnet-new-psmodule"></a>Uppdatera: dotNet New PSModule

Jag har lärt dig att `dotnet` verktyget har en `PSModule` mall.

Alla steg som beskrivs ovan är fortfarande giltiga, men den här mallen delar ut många av dem. Det är fortfarande en ganska ny mall som fortfarande kommer att få lite polska att placeras på den. Det kan vara bättre att komma igång.

Så här använder du installera och använder PSModule-mallen.

```powershell
dotnet new -i Microsoft.PowerShell.Standard.Module.Template
dotnet new psmodule
dotnet build
Import-Module "bin\Debug\netstandard2.0\$module.dll"
Get-Module $module
```

Den här minimala mallen tar hand om att lägga till .NET SDK, PowerShell standard-biblioteket och skapar en exempel klass i projektet. Du kan skapa den och köra den direkt.

## <a name="important-details"></a>Viktig information

Innan vi slutför den här artikeln är här några andra detaljer som är värda att nämna.

### <a name="unloading-dlls"></a>Laddar bort dll: er

När en binär modul har lästs in kan du verkligen ta bort den. DLL-filen är låst tills du tar bort den. Detta kan vara irriterande när du utvecklar eftersom varje gång du gör en ändring och vill skapa den, är filen ofta låst. Det enda pålitliga sättet att lösa detta är att stänga PowerShell-sessionen som laddade DLL-filen.

### <a name="vs-code-reload-window-action"></a>VS Code Omladdnings fönster åtgärd

Jag gör det mesta av min PowerShell-dev i [vs Code][]. När jag arbetar med en binär modul (eller en modul med klasser) har jag fått till gång till att läsa in VS Code varje gång jag skapar.
<kbd>CTRL</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd> pop-kommando fönstret och `Reload Window` är alltid överst i listan.

### <a name="nested-powershell-sessions"></a>Kapslade PowerShell-sessioner

Ett annat alternativ är att ha en lämplig pester test täckning. Sedan kan du justera build.ps1-skriptet för att starta en ny PowerShell-session, utföra bygget, köra testerna och stänga sessionen.

### <a name="updating-installed-modules"></a>Uppdaterar installerade moduler

Den här låsningen kan vara irriterande vid försök att uppdatera den lokalt installerade modulen. Om en session har lästs in måste du leta efter den och stänga den. Detta är mindre av ett problem när du installerar från en PSGallery eftersom en modul version placerar den nya i en annan mapp.

Du kan konfigurera en lokal PSGallery och publicera den som en del av din version. Gör sedan din lokala installation från den PSGallery. Detta låter till exempel mycket arbete, men det kan vara lika enkelt som att starta en Docker-behållare. Jag får ett sätt att göra det i mitt inlägg på att [använda en NuGet-Server för en PSRepository][].

## <a name="why-binary-modules"></a>Varför binära moduler?

Jag har direkt till gång till hur man skapar en binär modul och inte ville säga varför du vill skapa en. I verkligheten skriver du C# och ger enkel åtkomst till PowerShell-cmdlets och functions. Det är den viktigaste anledningen till varför jag inte har växlat till de binära modulerna tidigare.

Men om du skapar en modul som inte är beroende av många andra PowerShell-kommandon kan prestanda förmånen vara betydande. Genom att släppa i C# får du till gång till den extra kostnad som har lagts till av PowerShell. PowerShell optimerades för administratören, inte på datorn, och det lägger till en lite extra kostnad.

På arbetet har vi en kritisk process som gör mycket arbete med JSON och hash. Vi optimerade PowerShell så mycket som vi kunde, men den här processen kördes fortfarande i 12 minuter. Modulen innehåller redan en mängd C#-format PowerShell. Detta gjorde konverteringen till en binär modul ren och lätt att göra. Vår konvertering klipper ut från över 12 minuter till under fyra minuter.

### <a name="hybrid-modules"></a>Hybrid moduler

Du kan blanda binära cmdletar med avancerade PowerShell-funktioner. Det är precis vad jag gör i den här guiden. Du kan ta allt du känner till om skript moduler och allt används på samma sätt.
Den tomma `psm1` filen som jag skapade idag finns bara så att du kan släppa andra PowerShell-funktioner senare.

Nästan alla kompilerade cmdlets som vi skapade startade som en PowerShell-funktion först. Alla våra binära moduler är i själva verket hybrid moduler.

### <a name="build-scripts"></a>Bygg skript

Jag har bevarat Bygg skriptet enkelt här. Jag använder vanligt vis ett stort `Invoke-Build` skript som en del av min CI/CD-pipeline. Det är mer Magic som att köra pester-tester, köra PSScriptAnalyzer, hantera versions hantering och publicera till PSGallery. När jag har börjat använda ett build-skript för mina moduler kan jag hitta massor av saker att lägga till i det.

## <a name="final-thoughts"></a>Slutliga tankar

Det är enkelt att skapa binära moduler. Jag har inte använt C#-syntaxen för att skapa en cmdlet, men det finns massor av dokumentation på den i [Windows POWERSHELL SDK][]. Det är definitivt något som är värt att experimentera med som en stege-sten i mer allvarliga C#.

<!-- link references -->
[ursprunglig version]: https://powershellexplained.com/2018-08-04-Powershell-Standard-Library-Binary-Module/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[PowerShell-standardbibliotek]: https://github.com/PowerShell/PowerShellStandard
[Skapa en binär plattforms oberoende modul]: https://github.com/PowerShell/PowerShell/blob/master/docs/cmdlet-example/command-line-simple-example.md
[dotNet Core SDK]: https://www.microsoft.com/net/download/core
[Använda en NuGet-Server för en PSRepository]: https://powershellexplained.com/2018-03-03-Powershell-Using-a-NuGet-server-for-a-PSRepository/
[Windows PowerShell SDK]: /powershell/scripting/developer/windows-powershell-reference
[VS-kod]: https://code.visualstudio.com
[NuGet-paket]: https://www.nuget.org/packages/PowerShellStandard.Library/
