---
description: Beskriver variabler som lagrar Tillståndsinformation för PowerShell. Dessa variabler skapas och underhålls av PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 08/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_automatic_variables?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Automatic_Variables
ms.openlocfilehash: d56e844bd10dfffabb1d2cfd75bcfe113724a334
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271640"
---
# <a name="about-automatic-variables"></a>Om automatiska variabler

## <a name="short-description"></a>Kort beskrivning

Beskriver variabler som lagrar Tillståndsinformation för PowerShell. Dessa variabler skapas och underhålls av PowerShell.

## <a name="long-description"></a>Lång beskrivning

Dessa variabler anses konceptuellt vara skrivskyddade. Även om de **kan** skrivas till **bör de inte** skrivas för bakåtkompatibilitet.

Här är en lista över de automatiska variablerna i PowerShell:

### <a name=""></a>$$

Innehåller den sista token i den sista raden som togs emot av sessionen.

### <a name=""></a>$?

Innehåller körnings status för det sista kommandot. Det innehåller **Sant** om det sista kommandot lyckades och **falskt** om det misslyckades.

För cmdlets och avancerade funktioner som körs i flera steg i en pipeline, t. ex. i både `process` och `end` block, som anropar `this.WriteError()` eller `$PSCmdlet.WriteError()` på någon punkt, anges `$?` till **falskt** , som `this.ThrowTerminatingError()` och `$PSCmdlet.ThrowTerminatingError()` .

`Write-Error`Cmdleten anges alltid `$?` till **false** omedelbart efter att den körts, men är inte inställd `$?` på **false** för en funktion som anropar den:

```powershell
function Test-WriteError
{
    Write-Error "Bad"
    $? # $false
}

Test-WriteError
$? # $true
```

För det senare ändamålet `$PSCmdlet.WriteError()` ska du i stället använda.

För inbyggda kommandon (körbara filer) `$?` anges till **Sant** när `$LASTEXITCODE` är 0 och anges till **falskt** om `$LASTEXITCODE` är ett annat värde.

> [!NOTE]
> Fram till PowerShell 7, som innehåller en instruktion inom parentes `(...)` , återställs inte syntaxen för under uttryck `$(...)` eller mat ris uttryck `@(...)` `$?` till **True** , så att `(Write-Error)` visas `$?` som **Sant**.
> Detta har ändrats i PowerShell 7, så det `$?` visar alltid det faktiska resultatet för det sista kommandot som körs i dessa uttryck.

### <a name=""></a>$^

Innehåller den första token i den sista raden som togs emot av sessionen.

### <a name="_"></a>$_

Samma som `$PSItem` . Innehåller det aktuella objektet i pipeline-objektet. Du kan använda den här variabeln i kommandon som utför en åtgärd på varje objekt eller på valda objekt i en pipeline.

### <a name="args"></a>$args

Innehåller en matris med värden för parametrar som inte har deklarerats som skickas till en funktion, ett skript eller ett skript block. När du skapar en funktion kan du deklarera parametrarna med hjälp av `param` nyckelordet eller genom att lägga till en kommaavgränsad lista med parametrar inom parentes efter funktions namnet.

I en händelse åtgärd `$Args` innehåller variabeln objekt som representerar händelse argumenten för den händelse som bearbetas. Den här variabeln fylls bara i `Action` blocket för ett händelse registrerings kommando.
Värdet för den här variabeln finns också i egenskapen **SourceArgs** för **PSEventArgs** -objektet som `Get-Event` returnerar.

### <a name="consolefilename"></a>$ConsoleFileName

Innehåller sökvägen till konsol filen ( `.psc1` ) som senast användes i sessionen. Den här variabeln fylls när du startar PowerShell med parametern **PSConsoleFile** eller när du använder `Export-Console` cmdleten för att exportera snapin-namn till en konsol fil.

När du använder `Export-Console` cmdleten utan parametrar uppdaterar den automatiskt konsol filen som användes senast i sessionen. Du kan använda den här automatiska variabeln för att avgöra vilken fil som ska uppdateras.

### <a name="error"></a>$Error

Innehåller en matris med fel objekt som representerar de senaste felen.
Det senaste felet är det första fel objektet i matrisen `$Error[0]` .

Om du vill förhindra att ett fel läggs till i `$Error` matrisen använder du parametern **ErrorAction** common med värdet **Ignore**. Mer information finns i [about_CommonParameters](about_CommonParameters.md).

### <a name="event"></a>$Event

Innehåller ett **PSEventArgs** -objekt som representerar den händelse som bearbetas. Den här variabeln fylls bara i `Action` blocket för ett händelse registrerings kommando, till exempel `Register-ObjectEvent` . Värdet för den här variabeln är samma objekt som `Get-Event` cmdleten returnerar. Därför kan du använda egenskaperna för `Event` variabeln, till exempel `$Event.TimeGenerated` i ett- `Action` skript block.

### <a name="eventargs"></a>$EventArgs

Innehåller ett objekt som representerar det första händelse argumentet som härleds från **EventArgs** för den händelse som bearbetas. Den här variabeln fylls bara i `Action` blocket för ett händelse registrerings kommando.
Värdet för den här variabeln finns också i egenskapen **SourceEventArgs** för **PSEventArgs** -objektet som `Get-Event` returnerar.

### <a name="eventsubscriber"></a>$EventSubscriber

Innehåller ett **PSEventSubscriber** -objekt som representerar händelse prenumeranten för den händelse som bearbetas. Den här variabeln fylls bara i `Action` blocket för ett händelse registrerings kommando. Värdet för den här variabeln är samma objekt som `Get-EventSubscriber` cmdleten returnerar.

### <a name="executioncontext"></a>$ExecutionContext

Innehåller ett **EngineIntrinsics** -objekt som representerar körnings kontexten för PowerShell-värden. Du kan använda den här variabeln för att hitta de körnings objekt som är tillgängliga för-cmdletar.

### <a name="false"></a>$false

Innehåller **falskt**. Du kan använda den här variabeln för att representera **falskt** i kommandon och skript i stället för att använda strängen "false". Strängen kan tolkas som **Sant** om den konverteras till en sträng som inte är tom eller till ett heltal som inte är noll.

### <a name="foreach"></a>$foreach

Innehåller uppräkna ren (inte de resulterande värdena) för en [förgrunds](about_ForEach.md) slinga. `$ForEach`Variabeln finns bara medan `ForEach` loopen körs. den tas bort när loopen har slutförts.

Uppräknare innehåller egenskaper och metoder som du kan använda för att hämta loop-värden och ändra den aktuella loop-iterationen. Mer information finns i [använda uppräknare](#using-enumerators).

### <a name="home"></a>$HOME

Innehåller den fullständiga sökvägen till användarens Hem Katalog. Den här variabeln motsvarar `"$env:homedrive$env:homepath"` Windows-miljövariablerna, vanligt vis `C:\Users\<UserName>` .

### <a name="host"></a>$Host

Innehåller ett objekt som representerar det aktuella värd programmet för PowerShell. Du kan använda den här variabeln för att representera den aktuella värden i kommandon eller för att visa eller ändra egenskaperna för värden, till exempel `$Host.version` eller `$Host.CurrentCulture` , eller `$host.ui.rawui.setbackgroundcolor("Red")` .

### <a name="input"></a>$input

Innehåller en uppräknare som räknar upp alla indatatyper som skickas till en funktion. `$input`Variabeln är endast tillgänglig för funktioner och skript block (som är ej namede funktioner).

- I en funktion utan ett `Begin` , `Process` eller- `End` block, `$input` räknar variabeln upp indatamängden för funktionen.

- I `Begin` blocket `$input` innehåller variabeln inga data.

- I `Process` blocket `$input` innehåller variabeln det objekt som för närvarande finns i pipelinen.

- I `End` blocket `$input` räknar variabeln upp indatamängden för funktionen.

  > [!NOTE]
  > Du kan inte använda `$input` variabeln i både process blocket och slut blocket i samma funktion eller i ett skript block.

Eftersom `$input` är en uppräknare kan åtkomst till någon av dess egenskaper `$input` inte längre vara tillgänglig. Du kan lagra `$input` i en annan variabel om du vill återanvända `$input` egenskaperna.

Uppräknare innehåller egenskaper och metoder som du kan använda för att hämta loop-värden och ändra den aktuella loop-iterationen. Mer information finns i [använda uppräknare](#using-enumerators).


### <a name="lastexitcode"></a>$LastExitCode

Innehåller avslutnings koden för det senaste Windows-baserade program som kördes.

### <a name="matches"></a>$Matches

`Matches`Variabeln fungerar med `-match` `-notmatch` operatorerna och.
När du skickar skalära indatatyper till `-match` `-notmatch` operatorn eller, och antingen identifierar en matchning, returnerar de ett booleskt värde och fyller den `$Matches` automatiska variabeln med en hash-tabell för alla sträng värden som matchades. `$Matches`Hash-tabellen kan också fyllas i med insamlingar när du använder reguljära uttryck med `-match` operatorn.

Mer information om `-match` operatorn finns i [about_Comparison_Operators](about_comparison_operators.md). Mer information om reguljära uttryck finns [about_Regular_Expressions](about_Regular_Expressions.md).

### <a name="myinvocation"></a>$MyInvocation

Innehåller information om det aktuella kommandot, till exempel namn, parametrar, parameter värden och information om hur kommandot startades, anropades eller anropades, till exempel namnet på det skript som anropade det aktuella kommandot.

`$MyInvocation` är endast ifyllt för skript, funktions-och skript block. Du kan använda informationen i objektet **system. Management. Automation. InvocationInfo** som `$MyInvocation` returneras i det aktuella skriptet, t. ex. sökvägen och fil namnet för skriptet ( `$MyInvocation.MyCommand.Path` ) eller namnet på en funktion ( `$MyInvocation.MyCommand.Name` ) för att identifiera det aktuella kommandot. Detta är särskilt användbart för att hitta namnet på det aktuella skriptet.

Från och med PowerShell 3,0, `MyInvocation` har följande nya egenskaper.

| Egenskap      | Beskrivning                                         |
| ------------- | --------------------------------------------------- |
| **PSScriptRoot**  | Innehåller den fullständiga sökvägen till skriptet som anropades   |
|               | det aktuella kommandot. Värdet för den här egenskapen är  |
|               | fylls bara i när anroparen är ett skript.         |
| **PSCommandPath** | Innehåller den fullständiga sökvägen till och fil namnet på skriptet  |
|               | som anropade det aktuella kommandot. Värdet för det här |
|               | Egenskapen fylls bara när anroparen är en     |
|               | över.                                             |

Till skillnad från `$PSScriptRoot` de `$PSCommandPath` automatiska variablerna innehåller egenskaperna **PSScriptRoot** och **PSCommandPath** för den `$MyInvocation` automatiska variabeln information om anroparen eller anropet till skriptet, inte det aktuella skriptet.

### <a name="nestedpromptlevel"></a>$NestedPromptLevel

Innehåller den aktuella LED text nivån. Värdet 0 anger den ursprungliga LED text nivån. Värdet ökar när du anger en kapslad nivå och när du avslutar det.

PowerShell visar till exempel en kapslad kommando tolk när du använder- `$Host.EnterNestedPrompt` metoden. PowerShell visar också en kapslad kommando tolk när du når en Bryt punkt i PowerShell-felsökaren.

När du anger en kapslad prompt pausar PowerShell det aktuella kommandot, sparar körnings kontexten och ökar värdet för `$NestedPromptLevel` variabeln. Om du vill skapa ytterligare kapslade kommando prompter (upp till 128 nivåer) eller återgå till den ursprungliga kommando tolken, slutför du kommandot eller Skriv `exit` .

`$NestedPromptLevel`Variabeln hjälper dig att spåra LED text nivån. Du kan skapa en alternativ kommando tolk för PowerShell som innehåller det här värdet så att det alltid är synligt.

### <a name="null"></a>$null

`$null` är en automatisk variabel som innehåller ett **Null** -värde eller ett tomt värde. Du kan använda den här variabeln för att representera ett frånvarande eller odefinierat värde i kommandon och skript.

PowerShell behandlar `$null` som ett objekt med ett värde, det vill säga som en explicit plats hållare, så att du kan använda `$null` för att representera ett tomt värde i en serie med värden.

När `$null` ingår i en samling räknas den till exempel som ett av objekten.

```powershell
$a = "one", $null, "three"
$a.count
```

```Output
3
```

Om du rör `$null` variabeln till `ForEach-Object` cmdleten genererar den ett värde för `$null` , precis som för de andra objekten

```powershell
"one", $null, "three" | ForEach-Object { "Hello " + $_}
```

```Output
Hello one
Hello
Hello three
```

Det innebär att du inte kan använda `$null` till att betyda ett **parameter värde**. Ett parameter värde för `$null` åsidosätter standard parameter värde.

Men eftersom PowerShell behandlar `$null` variabeln som en plats hållare kan du använda den i skript som följande, som inte fungerar om `$null` ignorerades.

```powershell
$calendar = @($null, $null, "Meeting", $null, $null, "Team Lunch", $null)
$days = "Sunday","Monday","Tuesday","Wednesday","Thursday",
        "Friday","Saturday"
$currentDay = 0
foreach($day in $calendar)
{
    if($day -ne $null)
    {
        "Appointment on $($days[$currentDay]): $day"
    }

    $currentDay++
}
```

```Output
Appointment on Tuesday: Meeting
Appointment on Friday: Team lunch
```

### <a name="pid"></a>$PID

Innehåller process identifieraren (PID) för processen som är värd för den aktuella PowerShell-sessionen.

### <a name="profile"></a>$PROFILE

Innehåller den fullständiga sökvägen till PowerShell-profilen för den aktuella användaren och det aktuella värd programmet. Du kan använda den här variabeln för att representera profilen i kommandon. Du kan till exempel använda den i ett kommando för att avgöra om en profil har skapats:

```powershell
Test-Path $PROFILE
```

Eller så kan du använda den i ett kommando för att skapa en profil:

```powershell
New-Item -ItemType file -Path $PROFILE -Force
```

Du kan använda den i ett kommando för att öppna profilen i **notepad.exe** :

```powershell
notepad.exe $PROFILE
```

### <a name="psboundparameters"></a>$PSBoundParameters

Innehåller en lista över parametrar som skickas till ett skript eller en funktion och deras aktuella värden. Den här variabeln har ett värde endast i ett omfång där parametrar deklareras, till exempel ett skript eller en funktion. Du kan använda den för att visa eller ändra aktuella värden för parametrar eller skicka parameter värden till ett annat skript eller en annan funktion.

I det här exemplet skickar funktionen **TEST2** `$PSBoundParameters` till **test1** -funktionen. `$PSBoundParameters`Visas i formatet för **nyckel** och **värde**.

```powershell
function Test1 {
   param($a, $b)

   # Display the parameters in dictionary format.
   $PSBoundParameters
}

function Test2 {
   param($a, $b)

   # Run the Test1 function with $a and $b.
   Test1 @PSBoundParameters
}
```

```powershell
Test2 -a Power -b Shell
```

```Output
Key   Value
---   -----
a     Power
b     Shell
```

### <a name="pscmdlet"></a>$PSCmdlet

Innehåller ett objekt som representerar den cmdlet eller avancerad funktion som körs.

Du kan använda egenskaperna och metoderna för objektet i din cmdlet eller funktions kod för att svara på användnings villkoren. Till exempel innehåller egenskapen **ParameterSetName** namnet på den parameter uppsättning som används och **ShouldProcess** -metoden lägger till **whatIf** -och **Confirm** -parametrarna i cmdleten dynamiskt.

Mer information om den `$PSCmdlet` automatiska variabeln finns i [about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md) och [about_Functions_Advanced](about_Functions_Advanced.md).

### <a name="pscommandpath"></a>$PSCommandPath

Innehåller den fullständiga sökvägen och fil namnet för det skript som körs. Den här variabeln är giltig i alla skript.

### <a name="psculture"></a>$PSCulture

Innehåller namnet på kulturen som används i operativ systemet. Kulturen bestämmer visnings formatet för objekt som tal, valuta och datum och lagras i ett **system. globalisering. CultureInfo** -objekt. Används `Get-Culture` för att Visa datorns kultur. `$PSCulture` innehåller värde för egenskapen **Name** .

### <a name="psdebugcontext"></a>$PSDebugContext

Vid fel sökning innehåller den här variabeln information om fel söknings miljön. Annars innehåller den ett **Null** -värde. Därför kan du använda den för att ange om fel söknings programmet har kontroll. När den har fyllts i innehåller den ett **PsDebugContext** -objekt som har **Bryt punkter** och **InvocationInfo** egenskaper. Egenskapen **InvocationInfo** har flera användbara egenskaper, inklusive egenskapen **location** . Egenskapen **location** anger sökvägen till skriptet som felsöks.

### <a name="pshome"></a>$PSHOME

Innehåller den fullständiga sökvägen till installations katalogen för PowerShell, vanligt vis `$env:windir\System32\PowerShell\v1.0` i Windows-system. Du kan använda den här variabeln i sökvägar för PowerShell-filer. Till exempel söker följande kommando efter ordet **variabel** i de konceptuella hjälp avsnitten:

```powershell
Select-String -Pattern Variable -Path $pshome\*.txt
```

### <a name="psitem"></a>$PSItem

Samma som `$_` . Innehåller det aktuella objektet i pipeline-objektet. Du kan använda den här variabeln i kommandon som utför en åtgärd på varje objekt eller på valda objekt i en pipeline.

### <a name="psscriptroot"></a>$PSScriptRoot

Innehåller den katalog som ett skript körs från.

I PowerShell 2,0 är den här variabeln endast giltig i script modules ( `.psm1` ).
Från och med PowerShell 3,0 är det giltigt i alla skript.

### <a name="pssenderinfo"></a>$PSSenderInfo

Innehåller information om den användare som startade PSSession, inklusive användar identitet och tidszon på den ursprungliga datorn. Den här variabeln är endast tillgänglig i PSSessions.

`$PSSenderInfo`Variabeln innehåller en egenskap som kan konfigureras av användaren, **ApplicationArguments** , som standard bara innehåller `$PSVersionTable` från den ursprungliga sessionen. Om du vill lägga till data i egenskapen **ApplicationArguments** använder du parametern **ApplicationArguments** för `New-PSSessionOption` cmdleten.

### <a name="psuiculture"></a>$PSUICulture

Innehåller namnet på användar gränssnitts kulturen (UI) som används i operativ systemet. ANVÄNDAR gränssnittets kultur avgör vilka text strängar som används för gränssnitts element, till exempel menyer och meddelanden. Detta är värdet för systemets **system.Globalization.CultureInfo.CurrentUICulture.name** -egenskap. Använd cmdleten för att hämta objektet **system. globalisering. CultureInfo** för systemet `Get-UICulture` .

### <a name="psversiontable"></a>$PSVersionTable

Innehåller en skrivskyddad hash-tabell som visar information om den version av PowerShell som körs i den aktuella sessionen. Tabellen innehåller följande objekt:

| Egenskap                  | Beskrivning                                   |
| ------------------------- | --------------------------------------------- |
| **BuildVersion**          | Versions numret för den aktuella versionen       |
| **CLRVersion**            | Versionen av Common Language Runtime    |
|                           | CLR                                         |
| **PSCompatibleVersions**  | Versioner av PowerShell som är kompatibla    |
|                           | med den aktuella versionen                      |
| **PSEdition**             | Den här egenskapen har värdet "Desktop", för |
|                           | Windows Server-och Windows-klient versioner.   |
|                           | Den här egenskapen har värdet "Core" för     |
|                           | PowerShell som körs under Nano Server eller       |
|                           | Windows IOT.                                  |
| **PSRemotingProtocolVersion** | Versionen av PowerShell-fjärrservern      |
|                           | hanterings protokoll.                          |
| **PSVersion**             | PowerShell-versions numret                 |
| **SerializationVersion**  | Versionen av serialiserings metoden       |
| **WSManStackVersion**     | WS-Management stackens versions nummer |

### <a name="pwd"></a>$PWD

Innehåller ett Sök vägs objekt som representerar den fullständiga sökvägen till den aktuella katalogen.

### <a name="sender"></a>$Sender

Innehåller objektet som skapade den här händelsen. Den här variabeln fylls bara i åtgärds blocket för ett händelse registrerings kommando. Värdet för den här variabeln finns också i egenskapen Sender för **PSEventArgs** -objektet som `Get-Event` returnerar.

### <a name="shellid"></a>$ShellId

Innehåller identifieraren för det aktuella gränssnittet.

### <a name="stacktrace"></a>$StackTrace

Innehåller en stack spårning för det senaste felet.

### <a name="switch"></a>$switch

Innehåller uppräkna ren inte resulterande värden för en `Switch` instruktion. `$switch`Variabeln finns bara medan `Switch` instruktionen körs. den tas bort när `switch` instruktionen Slutför körningen. Mer information finns i [about_Switch](about_Switch.md).

Uppräknare innehåller egenskaper och metoder som du kan använda för att hämta loop-värden och ändra den aktuella loop-iterationen. Mer information finns i [använda uppräknare](#using-enumerators).

### <a name="this"></a>$this

I ett skript block som definierar en skript egenskap eller skript metod `$this` refererar variabeln till det objekt som ska utökas.

I en anpassad klass `$this` refererar variabeln till själva klassobjektet som ger åtkomst till egenskaper och metoder som definierats i klassen.

### <a name="true"></a>$true

Innehåller **Sant**. Du kan använda den här variabeln för att representera **Sant** i kommandon och skript.

## <a name="using-enumerators"></a>Använda uppräknare

`$input` `$foreach` Variablerna, och `$switch` är alla uppräknare som används för att iterera genom de värden som bearbetas av deras inneslutna kodblock.

En uppräknare innehåller egenskaper och metoder som du kan använda för att fortsätta eller återställa iteration eller hämta upprepnings värden. Att direkt manipulera uppräknare anses inte vara bästa praxis.

- I slingor, flödes kontrollens nyckelord [bryts](about_Break.md) och [Fortsätt](about_Continue.md) bör föredras.
- I funktioner som accepterar pipeline-inflöde är det bäst att använda parametrar med **ValueFromPipeline** -eller **ValueFromPipelineByPropertyName** -attributen.

  Mer information finns i [about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md).

### <a name="movenext"></a>Anropa

Metoden [MoveNext](/dotnet/api/system.collections.ienumerator.movenext) flyttar uppräkna ren till nästa element i mängden. **MoveNext** returnerar **True** om uppräkna ren lyckades, **falskt** om uppräkna ren har passerat slutet av samlingen.

> [!NOTE]
> Det **booleska** värdet som returnerade min **MoveNext** skickas till utdataströmmen.
> Du kan ignorera utdata genom att Typecasting den `[void]` eller skicka den till [out-null](xref:Microsoft.PowerShell.Core.Out-Null).
>
> ```powershell
> $input.MoveNext() | Out-Null
> ```
>
> ```powershell
> [void]$input.MoveNext()
> ```

### <a name="reset"></a>Återställ

Metoden [Reset](/dotnet/api/system.collections.ienumerator.reset) anger uppräkna ren till den ursprungliga positionen, som är **före** det första elementet i samlingen.

### <a name="current"></a>Aktuellt

Den [aktuella](/dotnet/api/system.collections.ienumerator.current) egenskapen hämtar elementet i samlingen eller pipelinen vid den aktuella positionen för uppräkna ren.

Den **aktuella** egenskapen fortsätter att returnera samma egenskap tills **MoveNext** anropas.

## <a name="examples"></a>Exempel

### <a name="example-1-using-the-input-variable"></a>Exempel 1: använda variabeln $input

I följande exempel `$input` rensar Access variabeln variabeln tills nästa gång process blocket körs. Om du använder **Reset** -metoden återställs `$input` variabeln till det aktuella pipeline-värdet.

```powershell
function Test
{
    begin
    {
        $i = 0
    }

    process
    {
        "Iteration: $i"
        $i++
        "`tInput: $input"
        "`tAccess Again: $input"
        $input.Reset()
        "`tAfter Reset: $input"
    }
}

"one","two" | Test
```

```Output
Iteration: 0
    Input: one
    Access Again:
    After Reset: one
Iteration: 1
    Input: two
    Access Again:
    After Reset: two
```

Process blocket flyttar automatiskt `$input` variabeln även om du inte har åtkomst till den.

```powershell
$skip = $true
function Skip
{
    begin
    {
        $i = 0
    }

    process
    {
        "Iteration: $i"
        $i++
        if ($skip)
        {
            "`tSkipping"
            $skip = $false
        }
        else
        {
            "`tInput: $input"
        }
    }
}

"one","two" | Skip
```

```Output
Iteration: 0
    Skipping
Iteration: 1
    Input: two
```

### <a name="example-2-using-input-outside-the-process-block"></a>Exempel 2: använda $input utanför process blocket

Utanför process blocket `$input` representerar variabeln alla värden som skickas i funktionen.

- Vid åtkomst till `$input` variabeln rensas alla värden.
- **Reset** -metoden återställer hela samlingen.
- Den **aktuella** egenskapen fylls aldrig i.
- Metoden **MoveNext** returnerar false eftersom samlingen inte kan vara avancerad.
  - Anrop av **MoveNext** rensar bort `$input` variabeln.

```powershell
Function All
{
    "All Values: $input"
    "Access Again: $input"
    $input.Reset()
    "After Reset: $input"
    $input.MoveNext() | Out-Null
    "After MoveNext: $input"
}

"one","two","three" | All
```

```Output
All Values: one two three
Access Again:
After Reset: one two three
After MoveNext:
```

### <a name="example-3-using-the-inputcurrent-property"></a>Exempel 3: använda $input. Aktuell egenskap

Genom att använda den **aktuella** egenskapen kan det aktuella pipeline-värdet nås flera gånger utan att använda metoden **Reset** . Process blocket anropar inte metoden **MoveNext** automatiskt.

Den **aktuella** egenskapen kommer aldrig att fyllas i om du inte uttryckligen anropar **MoveNext**. Den **aktuella** egenskapen kan nås flera gånger i process blocket utan att värdet rensas.

```powershell
function Current
{
    begin
    {
        $i = 0
    }

    process
    {
        "Iteration: $i"
        $i++
        "`tBefore MoveNext: $($input.Current)"
        $input.MoveNext() | Out-Null
        "`tAfter MoveNext: $($input.Current)"
        "`tAccess Again: $($input.Current)"
    }
}

"one","two" | Current
```

```Output
Iteration: 0
    Before MoveNext:
    After MoveNext: one
    Access Again: one
Iteration: 1
    Before MoveNext:
    After MoveNext: two
    Access Again: two
```

### <a name="example-4-using-the-foreach-variable"></a>Exempel 4: använda variabeln $foreach

Till skillnad från `$input` variabeln `$foreach` representerar variabeln alltid alla objekt i samlingen när de nås direkt. Använd den **aktuella** egenskapen för att komma åt det aktuella samlings elementet och metoderna **Reset** och **MoveNext** för att ändra dess värde.

> [!NOTE]
> Varje iteration av `foreach` slingen anropar automatiskt **MoveNext** -metoden.

Följande slinga körs bara två gånger. I den andra iterationen flyttas samlingen till det tredje elementet innan iterationen är klar. Efter den andra iterationen finns det nu inga fler värden att iterera, och loopen avslutas.

Egenskapen **MoveNext** påverkar inte den variabel som valts för att iterera igenom samlingen ( `$Num` ).

```powershell
$i = 0
foreach ($num in ("one","two","three"))
{
    "Iteration: $i"
    $i++
    "`tNum: $num"
    "`tCurrent: $($foreach.Current)"

    if ($foreach.Current -eq "two")
    {
        "Before MoveNext (Current): $($foreach.Current)"
        $foreach.MoveNext() | Out-Null
        "After MoveNext (Current): $($foreach.Current)"
        "Num has not changed: $num"
    }
}
```

```Output
Iteration: 0
        Num: one
        Current: one
Iteration: 1
        Num: two
        Current: two
Before MoveNext (Current): two
After MoveNext (Current): three
Num has not changed: two
```

Om du använder **Reset** -metoden återställs det aktuella elementet i samlingen. I följande exempel upprepas de två första elementen **två gånger** eftersom **återställnings** metoden anropas. Efter de två första slingorna `if` Miss lyckas instruktionen och loopen upprepas genom alla tre elementen normalt.

> [!IMPORTANT]
> Detta kan resultera i en oändlig loop.

```powershell
$stopLoop = 0
foreach ($num in ("one","two", "three"))
{
    ("`t" * $stopLoop) + "Current: $($foreach.Current)"

    if ($num -eq "two" -and $stopLoop -lt 2)
    {
        $foreach.Reset() | Out-Null
        ("`t" * $stopLoop) + "Reset Loop: $stopLoop"
        $stopLoop++
    }
}
```

```Output
Current: one
Current: two
Reset Loop: 0
        Current: one
        Current: two
        Reset Loop: 1
                Current: one
                Current: two
                Current: three
```

### <a name="example-5-using-the-switch-variable"></a>Exempel 5: använda variabeln $switch

`$switch`Variabeln har exakt samma regler som `$foreach` variabeln.
Följande exempel visar alla koncept för uppräknare.

> [!NOTE]
> Observera att **NotEvaluated** -fallet aldrig körs, även om det inte finns någon `break` instruktion efter **MoveNext** -metoden.

```powershell
$values = "Start", "MoveNext", "NotEvaluated", "Reset", "End"
$stopInfinite = $false
switch ($values)
{
    "MoveNext" {
        "`tMoveNext"
        $switch.MoveNext() | Out-Null
        "`tAfter MoveNext: $($switch.Current)"
    }
    # This case is never evaluated.
    "NotEvaluated" {
        "`tAfterMoveNext: $($switch.Current)"
    }

    "Reset" {
        if (!$stopInfinite)
        {
            "`tReset"
            $switch.Reset()
            $stopInfinite = $true
        }
    }

    default {
        "Default (Current): $($switch.Current)"
    }
}
```

```Output
Default (Current): Start
    MoveNext
    After MoveNext: NotEvaluated
    Reset
Default (Current): Start
    MoveNext
    After MoveNext: NotEvaluated
Default (Current): End
```

## <a name="see-also"></a>Se även

[about_Functions](about_Functions.md)

[about_Functions_Advanced](about_Functions_Advanced.md)

[about_Functions_Advanced_Methods](about_Functions_Advanced_Methods.md)

[about_Functions_Advanced_Parameters](about_Functions_Advanced_Parameters.md)

[about_Functions_OutputTypeAttribute](about_Functions_OutputTypeAttribute.md)

[about_Functions_CmdletBindingAttribute](about_Functions_CmdletBindingAttribute.md)

[about_Hash_Tables](about_Hash_Tables.md)

[about_Preference_Variables](about_Preference_Variables.md)

[about_Splatting](about_Splatting.md)

[about_Variables](about_Variables.md)
