---
ms.date: 12/14/2020
title: Använda experimentella funktioner i PowerShell
description: Visar en lista över tillgängliga experimentella funktioner och hur du använder dem.
ms.openlocfilehash: f97cea1dff4030da22be1efbe3cd5cbb7a9f3527
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685280"
---
# <a name="using-experimental-features-in-powershell"></a>Använda experimentella funktioner i PowerShell

Stöd för experimentella funktioner i PowerShell är en mekanism för experimentella funktioner som kan användas tillsammans med befintliga stabila funktioner i PowerShell-eller PowerShell-moduler.

En experimentell funktion är en där designen inte har slutförts. Funktionen är tillgänglig för användare att testa och ge feedback. När en experimentell funktion har slutförts blir design ändringarna ändringar.

> [!CAUTION]
> Experimentella funktioner är inte avsedda att användas i produktion eftersom ändringarna kan avbrytas. Experimentella funktioner stöds inte officiellt. Vi uppskattar dock alla synpunkter och fel rapporter. Du kan fil problem i [GitHub-käll databasen](https://github.com/PowerShell/PowerShell/issues/new/choose).

Mer information om hur du aktiverar eller inaktiverar dessa funktioner finns [about_Experimental_Features](/powershell/module/microsoft.powershell.core/about/about_experimental_features).

## <a name="available-features"></a>Tillgängliga funktioner

Den här artikeln beskriver de experimentella funktioner som är tillgängliga och hur du använder funktionen.

|                            Namn                            |   6,2   |   7.0   |   7.1   |   7.2   |
| ---------------------------------------------------------- | :-----: | :-----: | :-----: | :-----: |
| PSTempDrive (vanlig i PS 7.0 +)                        | &check; |         |         |         |
| PSUseAbbreviationExpansion (vanlig i PS 7.0 +)         | &check; |         |         |         |
| PSNullConditionalOperators (vanlig i PS 7.1 +)         |         | &check; |         |         |
| PSUnixFileStat (endast Windows-konventionellt i PS 7.1 +)  |         | &check; |         |         |
| PSCommandNotFoundSuggestion                                | &check; | &check; | &check; | &check; |
| PSImplicitRemotingBatching                                 | &check; | &check; | &check; | &check; |
| Microsoft. PowerShell. Utility. PSManageBreakpointsInRunspace |         | &check; | &check; | &check; |
| PSDesiredStateConfiguration.InvokeDscResource              |         | &check; | &check; | &check; |
| PSNativePSPathResolution                                   |         |         | &check; | &check; |
| PSCultureInvariantReplaceOperator                          |         |         | &check; | &check; |
| PSNotApplyErrorActionToStderr                              |         |         | &check; | &check; |
| PSSubsystemPluginModel                                     |         |         | &check; | &check; |
| PSAnsiProgress                                             |         |         |         | &check; |
| PSAnsiRendering                                            |         |         |         | &check; |

## <a name="microsoftpowershellutilitypsmanagebreakpointsinrunspace"></a>Microsoft. PowerShell. Utility. PSManageBreakpointsInRunspace

I PowerShell 7,0 aktiverar experimentet **BreakAll** -parametern i `Debug-Runspace` `Debug-Job` cmdletarna och gör att användarna kan välja om de vill att PowerShell ska brytas direkt på den aktuella platsen när de bifogar en fel sökare.

I PowerShell 7,1 lägger detta experiment till att även lägga till parametern **körnings utrymme** i `*-PSBreakpoint` cmdletarna.

- `Disable-PSBreakpoint`
- `Enable-PSBreakpoint`
- `Get-PSBreakpoint`
- `Remove-PSBreakpoint`
- `Set-PSBreakpoint`

Parametern **körnings utrymme** anger ett **körnings utrymme** -objekt som interagerar med Bryt punkter i den angivna körnings utrymme.

```powershell
Start-Job -ScriptBlock {
    Set-PSBreakpoint -Command Start-Sleep
    Start-Sleep -Seconds 10
}

$runspace = Get-Runspace -Id 1

$breakpoint = Get-PSBreakPoint -Runspace $runspace
```

I det här exemplet startas ett jobb och en Bryt punkt anges som Bryt när körs `Set-PSBreakPoint` . Körnings utrymme lagras i en variabel och skickas till `Get-PSBreakPoint` kommandot med parametern **körnings utrymme** . Sedan kan du kontrol lera Bryt punkten i `$breakpoint` variabeln.

## <a name="psansirendering"></a>PSAnsiRendering

Det här experimentet lades till i PowerShell 7,2. Funktionen gör det möjligt att ändra hur PowerShell-motorn matar ut text och lägger till den `$PSStyle` automatiska variabeln för att styra ANSI-åter givning av sträng utdata.

```powershell
PS> $PSStyle | Get-Member

   TypeName: System.Management.Automation.PSStyle

Name             MemberType Definition
----             ---------- ----------
Equals           Method     bool Equals(System.Object obj)
FormatHyperlink  Method     string FormatHyperlink(string text, uri link)
GetHashCode      Method     int GetHashCode()
GetType          Method     type GetType()
ToString         Method     string ToString()
Background       Property   System.Management.Automation.PSStyle+BackgroundColor Background {get;}
Blink            Property   string Blink {get;}
BlinkOff         Property   string BlinkOff {get;}
Bold             Property   string Bold {get;}
BoldOff          Property   string BoldOff {get;}
Foreground       Property   System.Management.Automation.PSStyle+ForegroundColor Foreground {get;}
Formatting       Property   System.Management.Automation.PSStyle+FormattingData Formatting {get;}
Hidden           Property   string Hidden {get;}
HiddenOff        Property   string HiddenOff {get;}
Italic           Property   string Italic {get;}
ItalicOff        Property   string ItalicOff {get;}
OutputRendering  Property   System.Management.Automation.OutputRendering OutputRendering {get;set;}
Progress         Property   System.Management.Automation.PSStyle+ProgressConfiguration Progress {get;}
Reset            Property   string Reset {get;}
Reverse          Property   string Reverse {get;}
ReverseOff       Property   string ReverseOff {get;}
Strikethrough    Property   string Strikethrough {get;}
StrikethroughOff Property   string StrikethroughOff {get;}
Underline        Property   string Underline {get;}
UnderlineOff     Property   string UnderlineOff {get;}
```

Bas medlemmarna returnerar strängar av ANSI escape-sekvenser som är mappade till deras namn. Värdena kan anges för att tillåta anpassning.

Mer information finns i [about_Automatic_Variables](/reference/7.2/Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

> [!NOTE]
> För C#-utvecklare kan du komma åt `PSStyle` som en singleton. Användningen kommer att se ut så här:
>
> ```csharp
> string output = $"{PSStyle.Instance.Foreground.Red}{PSStyle.Instance.Bold}Hello{PSStyle.Instance.Reset}";
> ```
>
> `PSStyle` finns i namn området system. Management. Automation.

Tillsammans med åtkomst till `$PSStyle` , introducerar detta ändringar i PowerShell-motorn. PowerShell-formatsystemet uppdateras för att respektera `$PSStyle.OutputRendering` .

- `StringDecorated` typen läggs till för att hantera ANSI-undantagna strängar.
- `string IsDecorated` boolesk egenskap läggs till för att returnera om strängen innehåller ANSI escape-sekvenser baserat på om strängen innehåller ESC eller C1 CSI.
- `Length`Egenskapen returnerar _bara_ längden för texten utan ANSI escape-sekvenser.
- `StringDecorated Substring(int contentLength)` Metoden returnerar en under sträng som börjar vid indexet 0 upp till innehålls längden som inte är en del av ANSI escape-sekvenser. Detta krävs för tabellformatering för att trunkera strängar och bevara ANSI escape-sekvenser som inte tar upp ett utskrivbart tecken utrymme.
- `string ToString()` metoden förblir densamma och returnerar strängens klartext-version.
- `string ToString(bool Ansi)` Metoden returnerar rå ANSI Embedded-sträng om `Ansi` parametern är true. Annars returneras en klar text version med ANSI escape-sekvenser.

`FormatHyperlink(string text, uri link)`Returnerar en sträng som innehåller ANSI escape-sekvens som används för att dekorera hyperlänkar. Vissa Terminal-värdar, t. ex. [Windows Terminal](https://www.microsoft.com/p/windows-terminal/9n0dx20hk701), stöder den här markeringen, vilket gör att den återgivna texten går att klicka på i terminalen.

## <a name="psansiprogress"></a>PSAnsiProgress

Det här experimentet lades till i PowerShell 7,2. Funktionen lägger till `$PSStyle.Progress` medlemmen och gör att du kan kontrol lera visningen av förlopps visaren.

- `$PSStyle.Progress.Style` – En ANSI-sträng anger åter givnings formatet.
- `$PSStyle.Progress.MaxWidth` -Anger Max bredden för vyn. Ange som `0` konsol bredd.
  Standardvärdet `120`
- `$PSStyle.Progress.View` – En Enum med värden `Minimal` och `Classic` . `Classic` är den befintliga renderingen utan ändringar. `Minimal` är en enskild linje som är minimal åter givning. `Minimal` används som standard.

I följande exempel uppdateras åter givnings formatet till en minimal förlopps indikator.

```powershell
$PSStyle.Progress.View.Minimal
```

> [!NOTE]
> Du måste ha **PSAnsiRendering** experimentell funktion aktive rad för att använda den här funktionen.

## <a name="pscommandnotfoundsuggestion"></a>PSCommandNotFoundSuggestion

Rekommenderar möjliga kommandon baserade på fuzzy-matchande sökning efter en **CommandNotFoundException**.

```powershell
PS> get
```

```Output
get: The term 'get' is not recognized as the name of a cmdlet, function, script file, or operable
program. Check the spelling of the name, or if a path was included, verify that the path is correct
and try again.

Suggestion [4,General]: The most similar commands are: set, del, ft, gal, gbp, gc, gci, gcm, gdr,
gcs.
```

## <a name="pscultureinvariantreplaceoperator"></a>PSCultureInvariantReplaceOperator

När den vänstra operanden i en `-replace` operator-instruktion inte är en sträng, konverteras den operanden till en sträng.

När den här funktionen är inaktive rad `-replace` gör operatorn en kultur känslig sträng konvertering.
Om kulturen till exempel är inställt på franska (FR) `1.2` konverteras värdet till strängen `1,2` .

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
12
PS> [cultureinfo]::CurrentCulture = 'en'
PS> 1.2 -replace ','
1.2
```

Med funktionen aktive rad:

```powershell
PS> [cultureinfo]::CurrentCulture = 'fr'
PS> 1.2 -replace ','
1.2
```

## <a name="psdesiredstateconfigurationinvokedscresource"></a>PSDesiredStateConfiguration.InvokeDscResource

Möjliggör kompilering till MOF på icke-Windows-system och möjliggör användning av `Invoke-DSCResource` utan LCM.

## <a name="psimplicitremotingbatching"></a>PSImplicitRemotingBatching

Den här funktionen undersöker kommandot som anges i gränssnittet och om alla kommandon är implicita proxy-kommandon för fjärr kommunikation som utgör en enkel pipeline, grupperas kommandona tillsammans och anropas som en enda fjärrpipeline.

Exempel:

```powershell
# Create remote session and import TestIMod module
$s = nsn -host remoteMachine
icm $s { ipmo 'C:\Users\user\Documents\WindowsPowerShell\Modules\TestIMod\TestIMod.psd1' }
Import-PSSession $s -mod testimod

$maxProcs = 1000
$filter = 'pwsh','powershell*','wmi*'

# Without batching, this pipeline takes approximately 12 seconds to run
Measure-Command { Get-AllProcesses -MaxCount $maxProcs | Select-Custom $filter | Group-Stuff $filter }
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 12
Milliseconds      : 463

# But with the batching experimental feature enabled, it takes approximately 0.20 seconds
Measure-Command { Get-AllProcesses -MaxCount $maxProcs | Select-Custom $filter | Group-Stuff $filter }
Days              : 0
Hours             : 0
Minutes           : 0
Seconds           : 0
Milliseconds      : 209
```

Som det sågs ovan, med funktionen för batchbearbetning, är alla tre implicita proxy-kommandon för fjärr kommunikation,,,, `Get-AllProcesses` `Select-Custom` `Group-Stuff` som körs i fjärrsessionen och resultatet från pipelinen de enda data som returneras till klienten. Detta minskar mängden data som skickas fram och tillbaka mellan klienten och fjärrsessionen och minskar också mängden objekt serialisering och avserialisering.

## <a name="psnativepspathresolution"></a>PSNativePSPathResolution

Om en PSDrive-sökväg som använder fil Systems leverantören skickas till ett ursprungligt kommando skickas den matchade fil Sök vägen till det ursprungliga kommandot. Det innebär att ett kommando som `code temp:/test.txt` nu fungerar som förväntat.

I Windows, om sökvägen börjar med `~` , är det också som matchas med den fullständiga sökvägen och skickas till det inbyggda kommandot. I båda fallen normaliseras sökvägen till katalog avgränsarna för det aktuella operativ systemet.

- Om sökvägen inte är en PSDrive eller `~` (i Windows) sker inte Sök vägs normalisering
- Om sökvägen är i enkla citat tecken matchas den inte och behandlas som literal

## <a name="psnotapplyerroractiontostderr"></a>PSNotApplyErrorActionToStderr

När den här experimentella funktionen är aktive rad skrivs fel poster som omdirigeras från interna kommandon, t. ex. När du använder omdirigerings operatorer ( `2>&1` ), inte till `$Error` variabeln och Preference-variabeln `$ErrorActionPreference` påverkar inte de omdirigerade utdata.

Många interna kommandon skriver till `stderr` som en alternativ ström för ytterligare information. Det här beteendet kan orsaka förvirring när du tittar på fel eller ytterligare utdata kan gå förlorade till användaren om `$ErrorActionPreference` har angetts till ett tillstånd som inaktive ras av utdata.

Om ett ursprungligt kommando har en slutkod som inte är noll `$?` är inställt på `$false` . Om slut koden är noll `$?` anges till `$true` .

## <a name="psnullconditionaloperators"></a>PSNullConditionalOperators

Introducerar nya operatörer för null-ansvariga för villkorlig medlem- `?.` och `?[]` . Null-ansvariga för medlems åtkomst kan användas för skalära typer och mat ris typer. Returnera värdet för den använda medlemmen om variabeln inte är null. Om värdet för variabeln är null returnerar du null.

```powershell
$x = $null
${x}?.propname
${x?}?.propname

${x}?[0]
${x?}?[0]

${x}?.MyMethod()
```

Egenskapen `propname` används och värdet returneras endast om `$x` inte är null. På samma sätt används indexeraren endast om `$x` inte är null. Om `$x` är null returneras null.

`?.` `?[]` Operatorerna och är medlemmar i operatorn och ger inte ett blank steg mellan variabel namnet och operatorn.

Eftersom PowerShell tillåter `?` som en del av variabel namnet, krävs avtvetydighet när operatorerna används utan blank steg mellan variabelns namn och operatorn. För att disambiguate ska variablerna använda `{}` runt variabel namnet som: `${x?}?.propertyName` eller `${y}?[0]` .

> [!NOTE]
> Den här funktionen har flyttat från experiment fasen och är en vanlig funktion i PowerShell 7,1 och högre.

## <a name="pstempdrive"></a>PSTempDrive

Skapar den `TEMP:` PSDrive som är mappad till användarens tillfälliga katalog Sök väg.

> [!NOTE]
> Den här funktionen har flyttat från experiment fasen och är en vanlig funktion i PowerShell 7 och högre.

## <a name="psunixfilestat"></a>PSUnixFileStat

Den här funktionen ger nya beteenden för att inkludera data från UNIX **stat** -API i utdatan från fil system leverantören för att under lätta en mer UNIX-liknande fil lista. Den lägger till en ny antecknings egenskap i fil namns leverantören med namnet **UnixStat** som innehåller ett gemensamt uttryck för `stat(2)` API: et från det underliggande UNIX-typ systemet.

Utdata från `Get-ChildItem` bör se ut ungefär så här:

```powershell
dir | select -first 4 -skip 5


    Directory: /Users/jimtru/src/github/forks/JamesWTruher/PowerShell-1

UnixMode   User      Group           LastWriteTime        Size Name
--------   ----      -----           -------------        ---- ----
drwxr-xr-x jimtru    staff        10/23/2019 13:16         416 test
drwxr-xr-x jimtru    staff         11/8/2019 10:37         896 tools
-rw-r--r-- jimtru    staff         11/8/2019 10:37      112858 build.psm1
-rw-r--r-- jimtru    staff         11/8/2019 10:37      201297 CHANGELOG.md
```

> [!NOTE]
> Den här funktionen har flyttat från experiment fasen och är en vanlig funktion i PowerShell 7,1 och högre.

## <a name="psuseabbreviationexpansion"></a>PSUseAbbreviationExpansion

Den här funktionen gör det möjligt att slutföra nedtvingade cmdlets och funktioner:

Exempel:

- `i-psdf<tab>` Returnerar `Import-PowerShellDataFile` .
- `u-akvmssdr<tab>` avkastning `Undo-AzKeyVaultManagedStorageSasDefinitionRemoval`

Detta fungerar bara för slut för ande av flikar (interaktiv användning), så det `i-psdf` är inte ett giltigt cmdlet-namn i ett skript.

> [!NOTE]
> Den här funktionen har flyttat från experiment fasen och är en vanlig funktion i PowerShell 7 och högre.

## <a name="pssubsystempluginmodel"></a>PSSubsystemPluginModel

Den här funktionen aktiverar under Systems-plugin-modellen i PowerShell. Funktionen gör det möjligt att separera komponenter i `System.Management.Automation.dll` enskilda under system som finns i en egen sammansättning. Den här separationen minskar den grundläggande PowerShell-motorns disk utrymme och gör att dessa komponenter blir valfria funktioner för en minimal PowerShell-installation.

För närvarande stöds endast under systemet **CommandPredictor** . Det här del systemet används tillsammans med PSReadLine-modulen för att tillhandahålla anpassade förutsägelse-plugin-program. I framtiden kan **jobb**, **CommandCompleter**, **fjärr kommunikation** och andra komponenter delas upp i del system sammansättningar utanför `System.Management.Automation.dll` .

Experiment funktionen innehåller en ny cmdlet, [Get-PSSubsystem](xref:Microsoft.PowerShell.Core.Get-PSSubsystem). Den här cmdleten är endast tillgänglig om funktionen är aktive rad. Denna cmdlet returnerar information om de del system som är tillgängliga i systemet.
