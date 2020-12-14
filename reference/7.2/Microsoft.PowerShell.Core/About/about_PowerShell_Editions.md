---
description: Olika versioner av PowerShell körs på olika underliggande körningar.
Locale: en-US
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_powershell_editions?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_PowerShell_Editions
ms.openlocfilehash: 3b1b938874b36919a1a0627f3b492cbc961e4a2f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710561"
---
# <a name="about-powershell-editions"></a>Om PowerShell-versioner

## <a name="short-description"></a>Kort beskrivning
Olika versioner av PowerShell körs på olika underliggande körningar.

## <a name="long-description"></a>Lång beskrivning

Från PowerShell 5,1 finns det flera *utgåvor* av PowerShell som körs på en annan .net-körning. Från och med PowerShell 6,2 finns två versioner av PowerShell:

- **Desktop**, som körs på .NET Framework. PowerShell 4 och lägre, samt PowerShell 5,1 på Windows-versioner med full funktionalitet som Windows Desktop, Windows Server, Windows Server Core och de flesta andra Windows-operativsystem är Desktop Edition.
  Det här är den ursprungliga PowerShell-versionen.
- **Core**, som körs på .net Core. PowerShell 6,0 och senare, samt PowerShell 5,1 på vissa Windows-versioner med lägre storlek, till exempel Windows Nano Server och Windows IoT där .NET Framework inte är tillgängligt.

Eftersom versionen av PowerShell motsvarar .NET-körningen är det den primära indikatorn för kompatibilitet med .NET API och PowerShell-modul. vissa .NET-API: er, typer eller metoder är inte tillgängliga i både .NET-körningar och detta påverkar PowerShell-skript och moduler som är beroende av dem.

## <a name="the-psedition-automatic-variable"></a>Den `$PSEdition` automatiska variabeln

I PowerShell 5,1 och senare kan du ta reda på vilken version som körs med den `$PSEdition` automatiska variabeln:

```powershell
$PSEdition
```

```Output
Core
```

Den här variabeln finns inte i PowerShell 4 och lägre. `$PSEdition` null ska behandlas som det samma som värdet `Desktop` .

### <a name="edition-in-psversiontable"></a>Utgåva i `$PSVersionTable`

Den `$PSVersionTable` automatiska variabeln har även versions information i PowerShell 5,1 och senare:

```powershell
$PSVersionTable
```

```Output
Name                           Value
----                           -----
PSVersion                      6.2.0-rc.1
PSEdition                      Core           # <-- Edition information
GitCommitId                    6.2.0-rc.1
OS                             Microsoft Windows 10.0.18865
Platform                       Win32NT
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
WSManStackVersion              3.0
```

`PSEdition`Fältet får samma värde som den `$PSEdition` automatiska variabeln.

## <a name="the-compatiblepseditions-module-manifest-field"></a>`CompatiblePSEditions`Modulens manifest fält

PowerShell-moduler kan deklarera vilka utgåvor av PowerShell de är kompatibla med med hjälp av `CompatiblePSEditions` fältet i modul manifestet.

Till exempel är ett modul manifest som deklarerar kompatibilitet med både `Desktop` och `Core` utgåvor av PowerShell:

```powershell
@{
    ModuleVersion = '1.0'
    FunctionsToExport = @('Test-MyModule')
    CompatiblePSEditions = @('Desktop', 'Core')
}
```

Ett exempel på en modul manifest med endast `Desktop` kompatibilitet:

```powershell
@{
    ModuleVersion = '1.0'
    FunctionsToExport = @('Test-MyModule')
    CompatiblePSEditions = @('Desktop')
}
```

Om du utelämnar `CompatiblePSEditions` fältet från ett modul-manifest får du samma resultat som att ställa in det på `Desktop` , eftersom moduler som skapats innan det här fältet introducerades implicit för den här utgåvan.

För moduler som inte levereras som en del av Windows (d.v.s. moduler som du skriver eller installerar från galleriet), är det här fältet endast information. PowerShell ändrar inte beteendet baserat på `CompatiblePSEditions` fältet, men visar det på `PSModuleInfo` objektet (returneras av `Get-Module` ) för din egen logik:

```powershell
New-ModuleManifest -Path .\TestModuleWithEdition.psd1 -CompatiblePSEditions Desktop,Core -PowerShellVersion '5.1'
$ModuleInfo = Test-ModuleManifest -Path .\TestModuleWithEdition.psd1
$ModuleInfo.CompatiblePSEditions
```

```Output
Desktop
Core
```

> [!NOTE]
> Fältet `CompatiblePSEditions` modul är bara kompatibelt med PowerShell 5,1 och senare.
> Om du inkluderar det här fältet kommer en modul vara inkompatibel med PowerShell 4 och lägre.
> Eftersom fältet är rent information kan det vara säkert utelämnat i senare PowerShell-versioner.

I PowerShell 6,1 `Get-Module -ListAvailable` har formateringen uppdaterats för att Visa utgåva-kompatibiliteten för varje modul:

```PowerShell
Get-Module -ListAvailable
```

```Output

    Directory: C:\Users\me\Documents\PowerShell\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Script     1.4.0      Az                                  Core,Desk
Script     1.3.1      Az.Accounts                         Core,Desk {Disable-AzDataCollection, Disable-AzContextAutosave, E...
Script     1.0.1      Az.Aks                              Core,Desk {Get-AzAks, New-AzAks, Remove-AzAks, Import-AzAksCreden...

...

Script     4.4.0      Pester                              Desk      {Describe, Context, It, Should...}
Script     1.18.0     PSScriptAnalyzer                    Desk      {Get-ScriptAnalyzerRule, Invoke-ScriptAnalyzer, Invoke-...
Script     1.0.0      WindowsCompatibility                Core      {Initialize-WinSession, Add-WinFunction, Invoke-WinComm...

```

## <a name="edition-compatibility-for-modules-that-ship-as-part-of-windows"></a>Edition-kompatibilitet för moduler som levereras som en del av Windows

För moduler som ingår som en del av Windows (eller som installeras som en del av en roll eller funktion) behandlar PowerShell 6,1 och ovan `CompatiblePSEditions` fältet på olika sätt. Sådana moduler finns i Windows PowerShell-katalogen system modules ( `%windir%\System\WindowsPowerShell\v1.0\Modules` ).

För moduler som läses in från eller hittas i den här katalogen använder PowerShell 6,1 och senare `CompatiblePSEditions` fältet för att avgöra om modulen kommer att vara kompatibel med den aktuella sessionen och beter sig enligt detta.

När används `Import-Module` , importeras inte en modul utan `Core` i `CompatiblePSEditions` och ett fel meddelande visas:

```powershell
Import-Module BitsTransfer
```

```Output
Import-Module : Module 'C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\BitsTransfer\BitsTransfer.psd1' does not support current PowerShell edition 'Core'. Its supported editions are 'Desktop'. Use 'Import-Module -SkipEditionCheck' to ignore the compatibility of this module.
At line:1 char:1
+ Import-Module BitsTransfer
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~
+ CategoryInfo          : ResourceUnavailable: (C:\WINDOWS\system32\u2026r\BitsTransfer.psd1:String) [Import-Module], InvalidOperationException
+ FullyQualifiedErrorId : Modules_PSEditionNotSupported,Microsoft.PowerShell.Commands.ImportModuleCommand
```

När används visas `Get-Module -ListAvailable` inte moduler utan `Core` i `CompatiblePSEditions` :

```powershell
Get-Module -ListAvailable BitsTransfer
```

```Output
# No output
```

I båda fallen `-SkipEditionCheck` kan switch-parametern användas för att åsidosätta detta beteende:

```powershell
Get-Module -ListAvailable -SkipEditionCheck BitsTransfer
```

```Output

    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.0.0    BitsTransfer                        Desk      {Add-BitsFile, Complete-BitsTransfer, Get-BitsTransfer,...

```

> [!WARNING]
> `Import-Module -SkipEditionCheck` kan verka som om en modul har körts, men med den modulen körs risken att en inkompatibilitet påträffas senare. När modulen lästes in initialt slutförs, kan ett kommando senare anropa ett inkompatibelt API och Miss lyckas spontant.

## <a name="authoring-powershell-modules-for-edition-cross-compatibility"></a>Redigera PowerShell-moduler för kompatibilitet mellan versioner

När du skriver en PowerShell-modul för att nå både `Desktop` och `Core` utgåvor av PowerShell finns det saker du kan göra för att säkerställa kompatibilitet mellan utgåvor.

Det enda sanna sättet att bekräfta och validera kompatibilitet är dock att skriva tester för ditt skript eller din modul och köra dem på alla versioner och utgåvor av PowerShell som du behöver kompatibla med. Ett rekommenderat test ramverk för detta är [pester][].

### <a name="powershell-script"></a>PowerShell-skript

Som språk fungerar PowerShell likadant mellan versioner. Det är de cmdlets, moduler och .NET-API: er som du använder som påverkas av versionens kompatibilitet.

Vanligt vis fungerar skript som fungerar i PowerShell 6,1 och senare med Windows PowerShell 5,1, men det finns vissa undantag.

Version 1.18.0 [PSScriptAnalyzer][] -modulen har regler som [`PSUseCompatibleCommands`][] och [`PSUseCompatibleTypes`][] som kan identifiera eventuellt inkompatibel användning av kommandon och .NET-API: er i PowerShell-skript.

### <a name="net-assemblies"></a>.NET-sammansättningar

Om du skriver en binär modul eller en modul som införlivar .NET-sammansättningar (dll) som genereras från käll koden, bör du kompilera mot [.net standard][] och [PowerShell standard][] för autentisering vid kompilering av .net-och PowerShell API-kompatibilitet.

Även om dessa bibliotek kan kontrol lera kompatibilitet vid kompilering, kan de inte fånga upp möjliga beteende skillnader mellan olika versioner. För detta måste du fortfarande skriva tester.

## <a name="see-also"></a>Se även

- [about_Automatic_Variables](about_Automatic_Variables.md)
- [Importera-modul](xref:Microsoft.PowerShell.Core.Import-Module)
- [Hämta modul](xref:Microsoft.PowerShell.Core.Get-Module)
- [Moduler med kompatibla PowerShell-versioner](/powershell/scripting/gallery/concepts/module-psedition-support)

[Pester]: https://github.com/pester/Pester/wiki/Pester
[PSScriptAnalyzer]: https://github.com/PowerShell/PSScriptAnalyzer
['PSUseCompatibleCommands']: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/RuleDocumentation/UseCompatibleCommands.md
['PSUseCompatibleTypes']: https://github.com/PowerShell/PSScriptAnalyzer/blob/master/RuleDocumentation/UseCompatibleTypes.md
[.NET Standard]: /dotnet/standard/net-standard
[PowerShell-standard]: https://devblogs.microsoft.com/powershell/powershell-standard-library-build-single-module-that-works-across-windows-powershell-and-powershell-core/
