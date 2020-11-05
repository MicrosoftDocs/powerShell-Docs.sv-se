---
title: Allt du ville veta om switch-instruktionen
description: Switch-instruktionen i PowerShell erbjuder funktioner som inte finns på andra språk.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: c2e77aa5fb36d04fec1bc86f751291205120c729
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/05/2020
ms.locfileid: "93355127"
---
# <a name="everything-you-ever-wanted-to-know-about-the-switch-statement"></a>Allt du ville veta om switch-instruktionen

Precis som många andra språk har PowerShell kommandon för att kontrol lera körnings flödet i dina skript. En av dessa uttryck är [switch][] -instruktionen och i PowerShell finns funktioner som inte finns på andra språk. Idag tar vi en djupare erfarenhet av att arbeta med PowerShell `switch` .

> [!NOTE]
> Den [ursprungliga versionen][] av den här artikeln visas på bloggen som skrivits av [@KevinMarquette][] . PowerShell-teamet tackar för att dela det här innehållet med oss. Ta en titt på hans blogg på [PowerShellExplained.com][].

## <a name="the-if-statement"></a>`if`Instruktionen

En av de första satserna som du lär dig är- `if` instruktionen. Du kan köra ett skript block om en instruktion är `$true` .

``` powershell
if ( Test-Path $Path )
{
    Remove-Item $Path
}
```

Du kan ha mycket mer komplicerad logik genom att använda `elseif` och- `else` instruktioner. Här är ett exempel där jag har ett numeriskt värde för veckodag och jag vill hämta namnet som en sträng.

``` powershell
$day = 3

if ( $day -eq 0 ) { $result = 'Sunday'        }
elseif ( $day -eq 1 ) { $result = 'Monday'    }
elseif ( $day -eq 2 ) { $result = 'Tuesday'   }
elseif ( $day -eq 3 ) { $result = 'Wednesday' }
elseif ( $day -eq 4 ) { $result = 'Thursday'  }
elseif ( $day -eq 5 ) { $result = 'Friday'    }
elseif ( $day -eq 6 ) { $result = 'Saturday'  }

$result
```

```Output
Wednesday
```

Det gör att det här är ett vanligt mönster och det finns många sätt att hantera detta på. En av dem är med en `switch` .

## <a name="switch-statement"></a>Switch-instruktion

Med `switch` instruktionen kan du ange en variabel och en lista över möjliga värden. Om värdet matchar variabeln körs dess script block.

``` powershell
$day = 3

switch ( $day )
{
    0 { $result = 'Sunday'    }
    1 { $result = 'Monday'    }
    2 { $result = 'Tuesday'   }
    3 { $result = 'Wednesday' }
    4 { $result = 'Thursday'  }
    5 { $result = 'Friday'    }
    6 { $result = 'Saturday'  }
}

$result
```

```Output
'Wednesday'
```

I det här exemplet är värdet för att `$day` matcha ett av de numeriska värdena, och sedan tilldelas rätt namn `$result` . Vi utför bara en variabel tilldelning i det här exemplet, men alla PowerShell kan köras i dessa skript block.

### <a name="assign-to-a-variable"></a>Tilldela till en variabel

Vi kan skriva det senaste exemplet på ett annat sätt.

``` powershell
$result = switch ( $day )
{
    0 { 'Sunday'    }
    1 { 'Monday'    }
    2 { 'Tuesday'   }
    3 { 'Wednesday' }
    4 { 'Thursday'  }
    5 { 'Friday'    }
    6 { 'Saturday'  }
}
```

Vi placerar värdet på PowerShell-pipeline och tilldelar det till `$result` . Du kan göra samma sak med- `if` och- `foreach` satserna.

### <a name="default"></a>Standardvärde

Vi kan använda `default` nyckelordet för att identifiera vad som ska hända om det inte finns någon matchning.

``` powershell
$result = switch ( $day )
{
    0 { 'Sunday' }
    # ...
    6 { 'Saturday' }
    default { 'Unknown' }
}
```

Här returnerar vi värdet `Unknown` i standard fallet.

### <a name="strings"></a>Strängar

Jag matchade talen i de senaste exemplen, men du kan också matcha strängar.

``` powershell
$item = 'Role'

switch ( $item )
{
    Component
    {
        'is a component'
    }
    Role
    {
        'is a role'
    }
    Location
    {
        'is a location'
    }
}
```

```Output
is a role
```

Jag beslutade att inte omsluta `Component` , `Role` och `Location` matchar citat tecken här för att markera att de är valfria. `switch`I de flesta fall behandlas de som en sträng.

## <a name="arrays"></a>Matriser

En av de häftiga funktionerna i PowerShell `switch` är hur den hanterar matriser. Om du anger en `switch` matris bearbetar den varje element i samlingen.

``` powershell
$roles = @('WEB','Database')

switch ( $roles ) {
    'Database'   { 'Configure SQL' }
    'WEB'        { 'Configure IIS' }
    'FileServer' { 'Configure Share' }
}
```

```Output
Configure IIS
Configure SQL
```

Om du har upprepade objekt i matrisen matchas de flera gånger av lämpligt avsnitt.

### <a name="psitem"></a>PSItem

Du kan använda `$PSItem` eller `$_` för att referera till det aktuella objektet som bearbetades. När vi gör en enkel matchning `$PSItem` är det värde som vi matchar. Jag utför några avancerade matchningar i nästa avsnitt där denna variabel används.

## <a name="parameters"></a>Parametrar

En unik funktion i PowerShell `switch` är att den har ett antal [växel parametrar][] som ändrar hur det fungerar.

### <a name="-casesensitive"></a>-CaseSensitive

Matchningarna är inte Skift läges känsliga som standard. Om du behöver vara Skift läges känslig kan du använda `-CaseSensitive` . Detta kan användas tillsammans med andra växel parametrar.

### <a name="-wildcard"></a>– Jokertecken

Vi kan aktivera stöd för jokertecken med `-wildcard` växeln. Detta använder samma logik för jokertecken som `-like` operatorn för att göra varje matchning.

``` powershell
$Message = 'Warning, out of disk space'

switch -Wildcard ( $message )
{
    'Error*'
    {
        Write-Error -Message $Message
    }
    'Warning*'
    {
        Write-Warning -Message $Message
    }
    default
    {
        Write-Information $message
    }
}
```

```Output
WARNING: Warning, out of disk space
```

Här bearbetar vi ett meddelande och placerar det på olika strömmar baserat på innehållet.

### <a name="-regex"></a>– Regex

Switch-instruktionen stöder regex matchar precis som jokertecken.

``` powershell
switch -Regex ( $message )
{
    '^Error'
    {
        Write-Error -Message $Message
    }
    '^Warning'
    {
        Write-Warning -Message $Message
    }
    default
    {
        Write-Information $message
    }
}
```

Jag har fler exempel på att använda regex i en annan artikel som jag skrev: [på många sätt att använda regex][].

### <a name="-file"></a>– Fil

En liten känd funktion i Switch-instruktionen är att den kan bearbeta en fil med `-File` parametern. Du använder `-file` med en sökväg till en fil i stället för att ge den ett variabel uttryck.

``` powershell
switch -Wildcard -File $path
{
    'Error*'
    {
        Write-Error -Message $PSItem
    }
    'Warning*'
    {
        Write-Warning -Message $PSItem
    }
    default
    {
        Write-Output $PSItem
    }
}
```

Det fungerar precis som att bearbeta en matris. I det här exemplet kombinerar jag det med matchning av jokertecken och använder `$PSItem` . Detta bearbetar en loggfil och konverterar den till varnings-och fel meddelanden beroende på regex-matchningarna.

## <a name="advanced-details"></a>Avancerad information

Nu när du är medveten om alla dessa dokumenterade funktioner kan vi använda dem i samband med mer avancerad bearbetning.

### <a name="expressions"></a>Uttryck

`switch`Kan finnas i ett uttryck i stället för en variabel.

``` powershell
switch ( ( Get-Service | Where status -eq 'running' ).name ) {...}
```

Oavsett vilket uttryck som utvärderas till är det värde som används för matchningen.

### <a name="multiple-matches"></a>Flera matchningar

Du kanske redan har valt detta, men en `switch` kan matcha flera villkor. Detta gäller särskilt när du använder `-wildcard` eller `-regex` matchar. Du kan lägga till samma villkor flera gånger och alla utlöses.

``` powershell
switch ( 'Word' )
{
    'word' { 'lower case word match' }
    'Word' { 'mixed case word match' }
    'WORD' { 'upper case word match' }
}
```

```Output
lower case word match
mixed case word match
upper case word match
```

Alla tre dessa uttryck utlöses. Detta visar att varje villkor är markerat (i ordning). Detta gäller för bearbetning av matriser där varje objekt kontrollerar varje villkor.

### <a name="continue"></a>Fortsätt

Normalt är det här där jag skulle introducera `break` instruktionen, men det är bättre att vi lär oss att använda den `continue` först. Precis som med en `foreach` loop `continue` fortsätter du till nästa objekt i samlingen eller avslutar `switch` om det inte finns några fler objekt. Vi kan skriva om det senaste exemplet med Continue-instruktioner så att endast en sats körs.

``` powershell
switch ( 'Word' )
{
    'word'
    {
        'lower case word match'
        continue
    }
    'Word'
    {
        'mixed case word match'
        continue
    }
    'WORD'
    {
        'upper case word match'
        continue
    }
}
```

```Output
lower case word match
```

I stället för att matcha alla tre objekten matchas det första, och växeln fortsätter till nästa värde. Eftersom det inte finns några värden kvar för att bearbeta, avslutas växeln. I nästa exempel visas hur ett jokertecken kan matcha flera objekt.

``` powershell
switch -Wildcard -File $path
{
    '*Error*'
    {
        Write-Error -Message $PSItem
        continue
    }
    '*Warning*'
    {
        Write-Warning -Message $PSItem
        continue
    }
    default
    {
        Write-Output $PSItem
    }
}
```

Eftersom en rad i indatafilen kan innehålla både ordet `Error` och `Warning` , vill vi bara att den första är att köra och sedan fortsätta att bearbeta filen.

### <a name="break"></a>Bryt ned

En `break` instruktion avslutar växeln. Detta är samma beteende som `continue` visar för enskilda värden. Skillnaden visas när du bearbetar en matris. `break` stoppar all bearbetning i växeln och `continue` flyttas till nästa objekt.

``` powershell
$Messages = @(
    'Downloading update'
    'Ran into errors downloading file'
    'Error: out of disk space'
    'Sending email'
    '...'
)

switch -Wildcard ($Messages)
{
    'Error*'
    {
        Write-Error -Message $PSItem
        break
    }
    '*Error*'
    {
        Write-Warning -Message $PSItem
        continue
    }
    '*Warning*'
    {
        Write-Warning -Message $PSItem
        continue
    }
    default
    {
        Write-Output $PSItem
    }
}
```

```Output
Downloading update
WARNING: Ran into errors downloading file
write-error -message $PSItem : Error: out of disk space
+ CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
+ FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException
```

I det här fallet visas ett fel meddelande om vi träffar de rader som börjar med `Error` och växeln stoppas.
Detta är vad den här `break` instruktionen gör för oss. Om vi hittar `Error` i strängen och inte bara i början skriver vi den som en varning. Vi gör samma sak för `Warning` . Det är möjligt att en rad kan ha både ordet `Error` och `Warning` , men vi behöver bara en att bearbeta. Detta är vad `continue` instruktionen gör för oss.

### <a name="break-labels"></a>Bryt etiketter

`switch`Instruktionen stöder `break/continue` Etiketter precis som `foreach` .

``` powershell
:filelist foreach($path in $logs)
{
    :logFile switch -Wildcard -File $path
    {
        'Error*'
        {
            Write-Error -Message $PSItem
            break filelist
        }
        'Warning*'
        {
            Write-Error -Message $PSItem
            break logFile
        }
        default
        {
            Write-Output $PSItem
        }
    }
}
```

Jag vill inte använda brytnings etiketter, men jag ville peka ut dem eftersom de är förvirrande om du aldrig har sett dem förut. Om du har flera `switch` eller `foreach` -satser som är kapslade kanske du vill dela upp fler än det inre objektet. Du kan placera en etikett på en `switch` som kan vara målet för din `break` .

### <a name="enum"></a>Enum

PowerShell 5,0 gav oss Fasttext och vi kan använda dem i en växel.

``` powershell
enum Context {
    Component
    Role
    Location
}

$item = [Context]::Role

switch ( $item )
{
    Component
    {
        'is a component'
    }
    Role
    {
        'is a role'
    }
    Location
    {
        'is a location'
    }
}
```

```Output
is a role
```

Om du vill behålla allting som starkt skrivna uppräkningar kan du placera dem inom parentes.

``` powershell
switch ($item )
{
    ([Context]::Component)
    {
        'is a component'
    }
    ([Context]::Role)
    {
        'is a role'
    }
    ([Context]::Location)
    {
        'is a location'
    }
}
```

Parenteserna behövs här så att växeln inte behandlar värdet `[Context]::Location` som en literal sträng.

### <a name="scriptblock"></a>Script block

Vi kan använda en script block för att utföra utvärderingen för en matchning om det behövs.

``` powershell
$age = 37

switch ( $age )
{
    {$PSItem -le 18}
    {
        'child'
    }
    {$PSItem -gt 18}
    {
        'adult'
    }
}
```

```Output
'adult'
```

Detta ökar komplexiteten och kan göra det `switch` svårt att läsa. I de flesta fall där du använder något som liknar det, skulle det vara bättre att använda `if` och `elseif` uttryck. Jag skulle vilja använda detta om jag redan har en stor växel på plats och jag behövde två objekt för att få samma utvärderings block.

Ett bra sätt är att placera script block i parenteser.

``` powershell
switch ( $age )
{
    ({$PSItem -le 18})
    {
        'child'
    }
    ({$PSItem -gt 18})
    {
        'adult'
    }
}
```

Den körs fortfarande på samma sätt och ger ett bättre visuellt avbrott när du snabbt tittar på det.

### <a name="regex-matches"></a>Regex $matches

Vi behöver gå tillbaka till regex för att vidröra något som inte är uppenbart tydligt. Användningen av regex fyller på `$matches` variabeln. Jag går igenom användningen av `$matches` mer när jag pratar om [många sätt att använda regex][]. Här är ett snabbt exempel som visar hur det fungerar med namngivna matchningar.

``` powershell
$message = 'my ssn is 123-23-3456 and credit card: 1234-5678-1234-5678'

switch -regex ($message)
{
    '(?<SSN>\d\d\d-\d\d-\d\d\d\d)'
    {
        Write-Warning "message contains a SSN: $($matches.SSN)"
    }
    '(?<CC>\d\d\d\d-\d\d\d\d-\d\d\d\d-\d\d\d\d)'
    {
        Write-Warning "message contains a credit card number: $($matches.CC)"
    }
    '(?<Phone>\d\d\d-\d\d\d-\d\d\d\d)'
    {
        Write-Warning "message contains a phone number: $($matches.Phone)"
    }
}
```

```Output
WARNING: message may contain a SSN: 123-23-3456
WARNING: message may contain a credit card number: 1234-5678-1234-5678
```

### <a name="null"></a>$null

Du kan matcha ett `$null` värde som inte måste vara standardvärdet.

``` powershell
$value = $null

switch ( $value )
{
    $null
    {
        'Value is null'
    }
    default
    {
        'value is not null'
    }
}

```Output
Value is null
```

Samma för en tom sträng.

``` powershell
switch ( '' )
{
    ''
    {
        'Value is empty'
    }
    default
    {
        'value is a empty string'
    }
}

```Output
Value is empty
```

### <a name="constant-expression"></a>Kon stan Tut tryck

Pettersson Dailey påpekade att vi kan använda ett kon stan Tut `$true` Tryck för att utvärdera `[bool]` objekt.
Tänk dig att vi har flera booleska kontroller som måste utföras.

``` powershell
$isVisible = $false
$isEnabled = $true
$isSecure = $true

switch ( $true )
{
    $isEnabled
    {
        'Do-Action'
    }
    $isVisible
    {
        'Show-Animation'
    }
    $isSecure
    {
        'Enable-AdminMenu'
    }
}
```

```Output
Do-Action
Enabled-AdminMenu
```

Detta är ett rent sätt att utvärdera och vidta åtgärder för status för flera booleska fält. Det häftiga med detta är att du kan ha en match som vänder statusen för ett värde som ännu inte har utvärderats.

``` powershell
$isVisible = $false
$isEnabled = $true
$isAdmin = $false

switch ( $true )
{
    $isEnabled
    {
        'Do-Action'
        $isVisible = $true
    }
    $isVisible
    {
        'Show-Animation'
    }
    $isAdmin
    {
        'Enable-AdminMenu'
    }
}
```

```Output
Do-Action
Show-Animation
```

Inställningen `$isEnabled` till `$true` i det här exemplet ser till att `$isVisible` också är inställd på `$true` . När `$isVisible` utvärderas, anropas dess script block. Detta är en bit som är intuitiv men som är en smarta användning av Mechanics.

### <a name="switch-automatic-variable"></a>$switch automatisk variabel

När `switch` bearbetar dess värden skapar den en uppräknare och anropar den `$switch` . Det här är en automatisk variabel som skapats av PowerShell och du kan ändra den direkt.

```powershell
$a = 1, 2, 3, 4

switch($a) {
    1 { [void]$switch.MoveNext(); $switch.Current }
    3 { [void]$switch.MoveNext(); $switch.Current }
}
```

Detta ger dig resultatet av:

```Output
2
4
```

Genom att flytta uppräkna ren framåt bearbetas inte nästa objekt av, `switch` men du kan komma åt det värdet direkt. Jag kallar IT-Madness.

## <a name="other-patterns"></a>Andra mönster

### <a name="hashtables"></a>Hash

Ett av mina populäraste inlägg är det jag gjorde på [hash][]. En av användnings fallen för en `hashtable` är en uppslags tabell. Det är en alternativ metod för ett vanligt mönster som en `switch` instruktion ofta riktar sig på.

``` powershell
$day = 3

$lookup = @{
    0 = 'Sunday'
    1 = 'Monday'
    2 = 'Tuesday'
    3 = 'Wednesday'
    4 = 'Thursday'
    5 = 'Friday'
    6 = 'Saturday'
}

$lookup[$day]
```

```Output
Wednesday
```

Om jag bara använder en `switch` som sökning, använder jag ofta en `hashtable` i stället.

### <a name="enum"></a>Enum

PowerShell 5,0 introducerade `Enum` och det är också ett alternativ i det här fallet.

``` powershell
$day = 3

enum DayOfTheWeek {
    Sunday
    Monday
    Tuesday
    Wednesday
    Thursday
    Friday
    Saturday
}

[DayOfTheWeek]$day
```

```Output
Wednesday
```

Vi kan gå hela dagen och titta på olika sätt för att lösa problemet. Jag ville bara se till att du visste att du hade några alternativ.

## <a name="final-words"></a>Sista ord

Switch-instruktionen är enkel på ytan, men den erbjuder vissa avancerade funktioner som de flesta inte inser är tillgängliga. Genom att stränga dessa funktioner är det en kraftfull funktion. Jag hoppas att du har lärt dig något som du inte hade realiserat tidigare.

<!-- link references -->
[ursprunglig version]: https://powershellexplained.com/2018-01-12-Powershell-switch-statement/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[byta]: /powershell/module/microsoft.powershell.core/about/about_switch
[Växla parametrar]: https://www.powershellmagazine.com/2013/12/20/using-powershell-switch-vs-boolean-parameters-in-sma-runbooks/
[Många sätt att använda regex]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression
[hash]: everything-about-hashtable.md
