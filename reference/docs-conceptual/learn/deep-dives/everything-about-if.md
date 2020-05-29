---
title: Allt du ville veta om instruktionen IF
description: Precis som många andra språk har PowerShell instruktioner för att villkorligt köra kod i dina skript.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 6ffb70af694e80430d31991045b9fadc1a2cc3f0
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149868"
---
# <a name="everything-you-wanted-to-know-about-the-if-statement"></a>Allt du ville veta om instruktionen IF

Precis som många andra språk har PowerShell instruktioner för att villkorligt köra kod i dina skript. En av dessa uttryck är [IF][] -instruktionen. Idag tar vi en djupare inblick i ett av de mest grundläggande kommandona i PowerShell.

> [!NOTE]
> Den [ursprungliga versionen][] av den här artikeln visas på bloggen som skrivits av [@KevinMarquette][] . PowerShell-teamet tackar för att dela det här innehållet med oss. Ta en titt på hans blogg på [PowerShellExplained.com][].

## <a name="conditional-execution"></a>Villkorlig körning

Dina skript behöver ofta fatta beslut och utföra en annan logik utifrån dessa beslut.
Detta är vad jag menar vid villkorlig körning. Du har ett uttryck eller ett värde att utvärdera och kör sedan ett annat avsnitt av kod baserat på den utvärderingen. Detta är exakt vad `if` instruktionen gör.

## <a name="the-if-statement"></a>Instruktionen IF

Här är ett grundläggande exempel på `if` instruktionen:

```powershell
$condition = $true
if ( $condition )
{
    Write-Output "The condition was true"
}
```

Det första `if` instruktionen är att utvärdera uttrycket inom parentes. Om den utvärderas till `$true` kör den `scriptblock` på klammerparenteserna. Om värdet var `$false` hoppar det över det script block.

I föregående exempel `if` utvärderar uttrycket bara `$condition` variabeln. Det var `$true` och skulle ha kört `Write-Output` kommandot inuti script block.

På vissa språk kan du placera en enda kodrad efter `if` instruktionen och den körs. Det är inte fallet i PowerShell. Du måste ange en fullständig `scriptblock` klammerparentes för att den ska fungera korrekt.

## <a name="comparison-operators"></a>Jämförelseoperatorer

Den vanligaste användningen av `if` instruktionen för är att jämföra två objekt med varandra. PowerShell har särskilda operatorer för olika jämförelse scenarier. När du använder en jämförelse operator jämförs värdet till vänster sida med värdet på den högra sidan.

### <a name="-eq-for-equality"></a>-EQ för likhet

`-eq`Gör en likhets kontroll mellan två värden för att se till att de är lika med varandra.

```powershell
$value = Get-MysteryValue
if ( 5 -eq $value )
{
    # do something
}
```

I det här exemplet tar jag ett känt värde `5` och jämför det med mitt `$value` för att se om de matchar.

Ett möjligt användnings fall är att kontrol lera status för ett värde innan du vidtar en åtgärd på den. Du kan få en tjänst och kontrol lera att statusen kördes innan du anropade `Restart-Service` den.

Det är vanligt på andra språk `==` , t. ex. C#, som används för likheter (t. ex.: `5 == $value` ) men som inte fungerar med PowerShell. Ett annat vanligt misstag är att använda likhets tecknet (t. ex. `5 = $value` ) som är reserverat för att tilldela värden till variabler. Genom att placera ditt kända värde till vänster gör det att förskrivet mer olämpligt att göra.

Den här operatorn (och andra) har några varianter.

- `-eq`Skift läges okänsligt likhet
- `-ieq`Skift läges okänsligt likhet
- `-ceq`Skift läges känslig likhet

### <a name="-ne-not-equal"></a>-Ne inte lika med

Många operatorer har en relaterad operator som söker efter motsatt resultat. `-ne`kontrollerar att värdena inte motsvarar varandra.

```powershell
if ( 5 -ne $value )
{
    # do something
}
```

Använd den här för att se till att åtgärden endast körs om värdet inte är det `5` . En lämplig användning – fall där du bör kontrol lera om en tjänst var i körnings tillstånd innan du försöker starta den.

**Olika**

- `-ne`Skift läges okänsligt är inte lika med
- `-ine`Skift läges okänsligt är inte lika med
- `-cne`Skift läges känsligt är inte lika med

Detta är inverterade variationer av `-eq` . Jag grupperar de här typerna tillsammans när jag listar varianter för andra operatorer.

### <a name="-gt--ge--lt--le-for-greater-than-or-less-than"></a>-gt-ge-lt-Le för större än eller mindre än

Dessa operatorer används vid kontroll för att se om ett värde är större eller mindre än ett annat värde.
`-gt -ge -lt -le`Stativ för GreaterThan, GreaterThanOrEqual, LessThan och LessThanOrEqual.

```powershell
if ( $value -gt 5 )
{
    # do something
}
```

**Olika**

- `-gt`större än
- `-igt`större än, SKIFT läges okänsligt
- `-cgt`större än, SKIFT läges känsligt
- `-ge`större än eller lika med
- `-ige`större än eller lika med Skift läges okänslig
- `-cge`större än eller lika med Skift läges känslig
- `-lt`mindre än
- `-ilt`mindre än, SKIFT läges okänsligt
- `-clt`mindre än, SKIFT läges känsligt
- `-le`mindre än eller lika med
- `-ile`mindre än eller lika med Skift läges okänslig
- `-cle`mindre än eller lika med Skift läges känslig

Jag vet inte varför du skulle använda Skift läges känsliga och inkänsliga alternativ för dessa operatörer.

### <a name="-like-wildcard-matches"></a>– som jokertecken matchar

PowerShell har en egen syntax för jokertecken, och du kan använda den med `-like` operatorn. Dessa mönster för jokertecken är ganska enkla.

- `?`matchar alla enskilda bokstäver
- `*`matchar valfritt antal tecken

```powershell
$value = 'S-ATX-SQL01'
if ( $value -like 'S-*-SQL??')
{
    # do something
}
```

Det är viktigt att peka på att mönstret matchar hela strängen. Om du behöver matcha något i mitten av strängen måste du placera i `*` båda ändarna av strängen.

```powershell
$value = 'S-ATX-SQL02'
if ( $value -like '*SQL*')
{
    # do something
}
```

**Olika**

- `-like`Skift läges okänsligt jokertecken
- `-ilike`Skift läges okänsligt jokertecken
- `-clike`Skift läges känsligt jokertecken
- `-notlike`Skift läges okänsligt jokertecken matchar inte
- `-inotlike`Skift läges okänsligt jokertecken matchar inte
- `-cnotlike`Skift läges känsligt jokertecken matchar inte

### <a name="-match-regular-expression"></a>– matcha reguljärt uttryck

Med `-match` operatorn kan du kontrol lera en sträng för en reguljär-uttrycks matchning. Använd det här när mönster mönster inte är tillräckligt flexibla.

```powershell
$value = 'S-ATX-SQL01'
if ( $value -match 'S-\w\w\w-SQL\d\d')
{
    # do something
}
```

Ett regex-mönster matchar var som helst i strängen. Så du kan ange en under sträng som du vill matcha så här:

```powershell
$value = 'S-ATX-SQL01'
if ( $value -match 'SQL')
{
    # do something
}
```

Regex är ett komplext språk som är eget och som är värt att titta på. Jag pratar mer om `-match` och [många sätt att använda regex][] i en annan artikel.

**Olika**

- `-match`Skift läges okänsligt regex
- `-imatch`Skift läges okänsligt regex
- `-cmatch`Skift läges känsligt regex
- `-notmatch`Skift läges okänsligt regex matchade inte
- `-inotmatch`Skift läges okänsligt regex matchade inte
- `-cnotmatch`Skift läges känsligt regex matchas inte

### <a name="-is-of-type"></a>-är av typen

Du kan kontrol lera ett värdes typ med `-is` operatorn.

```powershell
if ( $value -is [string] )
{
    # do something
}
```

Du kan använda det här om du arbetar med klasser eller accepterar olika objekt i pipelinen. Du kan antingen ha en tjänst eller ett tjänst namn som inmatade. Kontrol lera sedan för att se om du har en tjänst och hämtar tjänsten om du bara har namnet.

```powershell
if ( $Service -isnot [System.ServiceProcess.ServiceController] )
{
    $Service = Get-Service -Name $Service
}
```

**Olika**

- `-is`av typen
- `-isnot`inte av typen

## <a name="collection-operators"></a>Samlings operatörer

När du använder föregående operatorer med ett enda värde är resultatet `$true` eller `$false` . Detta hanteras något annorlunda när du arbetar med en samling. Varje objekt i samlingen utvärderas och operatorn returnerar varje värde som utvärderas till `$true` .

```powershell
PS> 1,2,3,4 -eq 3
3
```

Detta fungerar fortfarande korrekt i en `if` instruktion. Ett värde returneras av operatören och sedan är hela instruktionen `$true` .

```powershell
$array = 1..6
if ( $array -gt 3 )
{
    # do something
}
```

Det finns en liten svällning som döljs i den information som jag behöver för att peka. När du använder `-ne` operatorn på det här sättet, är det lätt att titta närmare på logiken baklänges. `-ne` `$true` Om ett objekt i samlingen inte matchar ditt värde med hjälp av med en samling returneras det.

```powershell
PS> 1,2,3 -ne 4
1
2
3
```

Detta kan se ut som ett smarta-stick, men vi har operatörer `-contains` och kan `-in` hantera detta mer effektivt. Och `-notcontains` vad du förväntar dig.

### <a name="-contains"></a>– innehåller

`-contains`Operatorn kontrollerar insamlingen för ditt värde. Så fort en matchning hittas returneras `$true` .

```powershell
$array = 1..6
if ( $array -contains 3 )
{
    # do something
}
```

Detta är det bästa sättet att se om en samling innehåller ditt värde. `Where-Object`Om du använder (eller `-eq` ) guidas hela listan varje gång och är betydligt långsammare.

**Olika**

- `-contains`Skift läges okänslig matchning
- `-icontains`Skift läges okänslig matchning
- `-ccontains`Skift läges känslig matchning
- `-notcontains`Skift läges känsligt matchar inte
- `-inotcontains`Skift läges känsligt matchar inte
- `-cnotcontains`Skift läges känsligt matchade inte

### <a name="-in"></a>– in

`-in`Operatorn är precis som `-contains` operatorn, förutom att samlingen är på den högra sidan.

```powershell
$array = 1..6
if ( 3 -in $array )
{
    # do something
}
```

**Olika**

- `-in`Skift läges okänslig matchning
- `-iin`Skift läges okänslig matchning
- `-cin`Skift läges känslig matchning
- `-notin`Skift läges känsligt matchar inte
- `-inotin`Skift läges känsligt matchar inte
- `-cnotin`Skift läges känsligt matchade inte

## <a name="logical-operators"></a>Logiska operatorer

Logiska operatorer används för att invertera eller kombinera andra uttryck.

### <a name="-not"></a>– inte

`-not`Operatorn vänder ett uttryck från `$false` till `$true` eller från `$true` till `$false` . Här är ett exempel där vi vill utföra en åtgärd när `Test-Path` är `$false` .

```powershell
if ( -not ( Test-Path -Path $path ) )
```

De flesta operatörer har vi talat med en variation där du inte behöver använda `-not` operatorn. Men det finns fortfarande tillfällen då det är användbart.

### <a name="-operator"></a>! operator

Du kan använda `!` som alias för `-not` .

```powershell
if ( -not $value ){}
if ( !$value ){}
```

Du kan se `!` använda mer av personer som kommer från ett annat språk, till exempel C#. Jag vill skriva ut den eftersom jag tycker att det är svårt att se när jag tittar på mina skript.

### <a name="-and"></a>-och

Du kan kombinera uttryck med `-and` operatorn. När du gör det måste båda sidorna vara för att `$true` hela uttrycket ska vara `$true` .

```powershell
if ( ($age -gt 13) -and ($age -lt 55) )
```

I det exemplet `$age` måste vara 13 eller äldre för vänster sida och mindre än 55 för den högra sidan. Jag har lagt till extra parenteser för att göra det tydligare i det exemplet, men de är valfria så länge uttrycket är enkelt. Här är samma exempel utan dem.

```powershell
if ( $age -gt 13 -and $age -lt 55 )
```

Utvärderingen sker från vänster till höger. Om det första objektet utvärderas till `$false` avslutas det tidigt och det utför inte rätt jämförelse. Detta är praktiskt när du behöver kontrol lera att det finns ett värde innan du använder det. Genererar till exempel `Test-Path` ett fel om du ger den en `$null` sökväg.

```powershell
if ( $null -ne $path -and (Test-Path -Path $path) )
```

### <a name="-or"></a>-eller

Med `-or` kan du ange två uttryck och returnerar `$true` om något av dem är `$true` .

```powershell
if ( $age -le 13 -or $age -ge 55 )
```

Precis som med `-and` operatorn sker utvärderingen från vänster till höger. Förutom att om den första delen är `$true` , är hela instruktionen `$true` och bearbetar inte resten av uttrycket.

Notera också hur syntaxen fungerar för de här operatorerna. Du behöver två separata uttryck. Jag har sett att användare försöker göra något som liknar detta `$value -eq 5 -or 6` utan att realisera sitt misstag.

### <a name="-xor-exclusive-or"></a>– XOR exklusivt eller

Det här är lite ovanligt. `-xor`tillåter endast ett uttryck att utvärdera till `$true` . Så om båda elementen är `$false` eller båda elementen `$true` är hela uttrycket `$false` . Ett annat sätt att titta på det här är att uttrycket bara är `$true` om resultatet av uttrycket är olika.

Det är ovanligt att vem som helst skulle använda den logiska operatorn och jag kan inte se ett användbart exempel på varför jag skulle använda den.

## <a name="bitwise-operators"></a>Bitvisa operatorer

Bitvisa operatorer utför beräkningar på bitarna i värdena och genererar ett nytt värde som resultat. Andra undervisnings [operatorer][] ligger utanför den här artikelns omfång, men här är listan över dem.

- `-band`binär och
- `-bor`binär eller
- `-bxor`binärt exklusivt eller
- `-bnot`binär NOT
- `-shl`Skift vänster
- `-shr`Shift, höger

## <a name="powershell-expressions"></a>PowerShell-uttryck

Vi kan använda normal PowerShell i villkors instruktionen.

```powershell
if ( Test-Path -Path $Path )
```

`Test-Path`Returnerar `$true` eller `$false` när den körs. Detta gäller även för kommandon som returnerar andra värden.

```powershell
if ( Get-Process Notepad* )
```

Den utvärderas till `$true` om det finns en returnerad process och `$false` om there'sn'thing. Den är perfekt giltig att använda pipeline-uttryck eller andra PowerShell-uttryck som detta:

```powershell
if ( Get-Process | Where Name -eq Notepad )
```

Dessa uttryck kan kombineras med `-and` `-or` -och-operatorer, men du kan behöva använda parenteser för att dela upp dem i under uttryck.

```powershell
if ( (Get-Process) -and (Get-Service) )
```

### <a name="checking-for-null"></a>Söker efter $null

Inget resultat eller ett `$null` värde utvärderas `$false` i `if` instruktionen. När du kontrollerar specifikt för är `$null` det bäst att placera `$null` på den vänstra sidan.

```powershell
if ( $null -eq $value )
```

Det finns ganska några olika delarna när du hanterar `$null` värden i PowerShell. Om du är intresse rad av simhopp djupare har jag en artikel om [allt du ville veta mer om $null][].

### <a name="variable-assignment"></a>Variabeltilldelning

Jag har nästan glömt att lägga till det här felet förrän [Prasoon Karunan V][] har beminnas mig.

```powershell
if ($process=Get-Process notepad -ErrorAction ignore) {$process} else {$false}
```

Normalt när du tilldelar ett värde till en variabel, skickas värdet inte till pipelinen eller konsolen. När du gör en variabel tilldelning i ett under uttryck skickas den vidare till pipelinen.

```powershell
PS> $first = 1
PS> ($second = 2)
2
```

Se hur `$first` tilldelningen inte har några utdata och `$second` tilldelningen gör? När en tilldelning görs i en `if` instruktion körs den precis som `$second` tilldelningen ovan. Här är ett rent exempel på hur du kan använda det:

```powershell
if ( $process = Get-Process Notepad* )
{
    $process | Stop-Process
}
```

Om `$process` tilldelas ett värde `$true` stoppas instruktionen och `$process` stoppas.

Se till att du inte förväxla detta med `-eq` eftersom det inte är en likhets kontroll. Detta är en mer skymd funktion som de flesta inte inser fungerar på det här sättet.

## <a name="alternate-execution-path"></a>Sökväg för alternativ körning

Med `if` instruktionen kan du ange en åtgärd för inte bara när instruktionen är `$true` , utan även för när den är `$false` . Det är här som `else` instruktionen kommer att spelas upp.

### <a name="else"></a>else

`else`Instruktionen är alltid den sista delen av `if` instruktionen när den används.

```powershell
if ( Test-Path -Path $Path -PathType Leaf )
{
    Move-Item -Path $Path -Destination $archivePath
}
else
{
    Write-Warning "$path doesn't exist or isn't a file."
}
```

I det här exemplet kontrollerar vi `$path` för att se till att det är en fil. Om vi hittar filen flyttar vi den. Annars skriver vi en varning. Den här typen av branchningslogik är mycket vanlig.

### <a name="nested-if"></a>Kapslad om

`if` `else` Instruktionen och tar ett skript block, så vi kan placera alla PowerShell-kommandon i dem, inklusive en annan `if` instruktion. Detta gör att du kan använda mycket mer komplicerad logik.

```powershell
if ( Test-Path -Path $Path -PathType Leaf )
{
    Move-Item -Path $Path -Destination $archivePath
}
else
{
    if ( Test-Path -Path $Path )
    {
        Write-Warning "A file was required but a directory was found instead."
    }
    else
    {
        Write-Warning "$path could not be found."
    }
}
```

I det här exemplet testar vi den glad sökvägen först och gör sedan en åtgärd på den. Om detta Miss lyckas gör vi en annan kontroll och ger mer detaljerad information till användaren.

### <a name="elseif"></a>ElseIf

Vi är inte begränsade till bara en enda villkorlig kontroll. Vi kan kedja `if` och `else` uttryck tillsammans i stället för att kapsla dem med hjälp av `elseif` instruktionen.

```powershell
if ( Test-Path -Path $Path -PathType Leaf )
{
    Move-Item -Path $Path -Destination $archivePath
}
elseif ( Test-Path -Path $Path )
{
    Write-Warning "A file was required but a directory was found instead."
}
else
{
    Write-Warning "$path could not be found."
}
```

Körningen sker uppifrån och ned. Den översta `if` instruktionen utvärderas först. Om det är `$false` det flyttas det nedåt till nästa `elseif` eller `else` i listan. Det sista `else` är den standard åtgärd som ska vidtas om ingen av de andra returneras `$true` .

### <a name="switch"></a>växla

Nu måste jag nämna `switch` instruktionen. Den innehåller en alternativ syntax för att utföra flera jämförelser med ett värde. Med `switch` kan du ange ett uttryck och resultatet jämförs med flera olika värden. Om något av dessa värden matchar, körs det matchande kod blocket. Ta en titt på det här exemplet:

```powershell
$itemType = 'Role'
switch ( $itemType )
{
    'Component'
    {
        'is a component'
    }
    'Role'
    {
        'is a role'
    }
    'Location'
    {
        'is a location'
    }
}
```

Det finns tre möjliga värden som kan matcha `$itemType` . I det här fallet matchar den med `Role` . Jag använde ett enkelt exempel bara för att ge dig viss exponering för `switch` operatorn. Jag pratar mer om [allt du ville veta om switch-satsen][] i en annan artikel.

## <a name="pipeline"></a>Pipeline

Pipelinen är en unik och viktig funktion i PowerShell. Ett värde som inte är undertryckt eller som har tilldelats en variabel placeras i pipelinen. På ett sätt kan `if` vi dra nytta av pipelinen på ett sätt som inte alltid är uppenbart.

```powershell
$discount = if ( $age -ge 55 )
{
    Get-SeniorDiscount
}
elseif ( $age -le 13 )
{
    Get-ChildDiscount
}
else
{
    0.00
}
```

Varje skript block placerar resultatet av kommandona eller värdet i pipelinen. Sedan tilldelar vi resultatet av IF-instruktionen till `$discount` variabeln. Det här exemplet kan ha lika enkelt tilldelat dessa värden till `$discount` variabeln direkt i varje script block. Jag kan inte säga att jag använder detta med `if` instruktionen ofta, men jag har ett exempel där jag använde detta nyligen.

### <a name="array-inline"></a>Infoga matris

Jag har en funktion som kallas [Invoke-SnowSql][] som startar en körbar fil med flera kommando rads argument. Här är ett klipp från funktionen där jag skapar en argument mat ris.

```powershell
$snowSqlParam = @(
    '--accountname', $Endpoint
    '--username', $Credential.UserName
    '--option', 'exit_on_error=true'
    '--option', 'output_format=csv'
    '--option', 'friendly=false'
    '--option', 'timing=false'
    if ($Debug)
    {
        '--option', 'log_level=DEBUG'
    }
    if ($Path)
    {
        '--filename', $Path
    }
    else
    {
        '--query', $singleLineQuery
    }
)
```

`$Debug` `$Path` Variablerna och är parametrar för den funktion som slutanvändaren tillhandahåller.
Jag utvärderar dem inuti initieringen av min matris. Om `$Debug` är sant hamnar dessa värden på `$snowSqlParam` rätt plats. Samma gäller för `$Path` variabeln.

## <a name="simplify-complex-operations"></a>Förenkla komplexa åtgärder

Det är ofrånkomligt att du stöter på en situation som har för många jämförelser för att kontrol lera och instruktionen IF rullar ut på skärmens högra sida.

```powershell
$user = Get-ADUser -Identity $UserName
if ( $null -ne $user -and $user.Department -eq 'Finance' -and $user.Title -match 'Senior' -and $user.HomeDrive -notlike '\\server\*' )
{
    # Do Something
}
```

De kan vara svåra att läsa och det gör det svårare att göra misstag. Det finns några saker som vi kan göra med det.

### <a name="line-continuation"></a>Rad fortsättning

Det finns några operatörer i PowerShell som låter dig figursätta kommandot till nästa rad. De logiska operatörerna `-and` och `-or` är bra operatörer att använda om du vill dela upp uttrycket i flera rader.

```powershell
if ($null -ne $user -and
    $user.Department -eq 'Finance' -and
    $user.Title -match 'Senior' -and
    $user.HomeDrive -notlike '\\server\*'
)
{
    # Do Something
}
```

Det finns fortfarande mycket som finns där, men att placera varje del på en egen linje gör stor skillnad.
Jag använder vanligt vis det här när jag får fler än två jämförelser eller om jag måste bläddra till höger för att läsa någon av logiken.

### <a name="pre-calculating-results"></a>För beräknings resultat

Vi kan ta den instruktionen från IF-instruktionen och bara kontrol lera resultatet.

```powershell
$needsSecureHomeDrive = $null -ne $user -and
    $user.Department -eq 'Finance' -and
    $user.Title -match 'Senior' -and
    $user.HomeDrive -notlike '\\server\*'

if ( $needsSecureHomeDrive )
{
    # Do Something
}
```

Det här är bara att ha mycket renare än det föregående exemplet. Du får också möjlighet att använda ett variabel namn som förklarar vad det är som du verkligen kontrollerar. Detta är även ett exempel på självdokumenterande kod som sparar onödiga kommentarer.

### <a name="multiple-if-statements"></a>Multiple IF-instruktioner

Vi kan dela upp det i flera instruktioner och kontrol lera dem en i taget. I det här fallet använder vi en flagga eller en spårnings variabel för att kombinera resultaten.

```powershell

$skipUser = $false

if( $null -eq $user )
{
    $skipUser = $true
}

if( $user.Department -ne 'Finance' )
{
    Write-Verbose "isn't in Finance department"
    $skipUser = $true
}

if( $user.Title -match 'Senior' )
{
    Write-Verbose "Doesn't have Senior title"
    $skipUser = $true
}

if( $user.HomeDrive -like '\\server\*' )
{
    Write-Verbose "Home drive already configured"
    $skipUser = $true
}

if ( -not $skipUser )
{
    # do something
}
```

Jag måste invertera logiken för att flagga logiken ska fungera korrekt. Varje utvärdering är en enskild `if` instruktion. Fördelen med detta är att när du felsöker kan du se exakt vad logiken gör. Jag har kunnat lägga till mycket bättre utförlighet på samma tid.

Den uppenbara nack delen är att det är så mycket mer kod att skriva. Koden är mer komplex att titta på när den tar en enda rad logik och expanderar den till 25 eller fler rader.

### <a name="using-functions"></a>Använda funktioner

Vi kan också flytta alla validerings logiken till en funktion. Titta på hur det här ser ut snabbt.

```powershell
if ( Test-SecureDriveConfiguration -ADUser $user )
{
    # do something
}
```

Du måste fortfarande skapa funktionen för att utföra verifieringen, men den gör den här koden mycket enklare att arbeta med. Det gör det enklare att testa den här koden. I dina tester kan du modellera samtalet `Test-ADDriveConfiguration` och du behöver bara två test för den här funktionen. En där den returnerar `$true` och en där den returnerar `$false` . Testning av den andra funktionen är enklare eftersom det är så litet.

Bröd texten i den funktionen kan fortfarande vara att en-liner som vi startade med eller den nedbrutena logiken som vi använde i det sista avsnittet. Detta fungerar bra för båda scenarierna och gör att du enkelt kan ändra implementeringen senare.

## <a name="error-handling"></a>Felhantering

En viktig användning av `if` instruktionen är att söka efter fel villkor innan du stöter på fel. Ett exempel är att kontrol lera om det redan finns en mapp innan du försöker skapa den.

```powershell
if ( -not (Test-Path -Path $folder) )
{
    New-Item -Type Directory -Path $folder
}
```

Jag vill säga att om du förväntar dig att ett undantag inträffar är det egentligen inget undantag. Kontrol lera värdena och kontrol lera dina villkor där du kan.

Om du vill få lite mer om faktisk undantags hantering har jag en artikel om [allt du någonsin ville veta om undantag][].

## <a name="final-words"></a>Sista ord

`if`Instruktionen är en enkel instruktion men är en grundläggande del av PowerShell. Du kommer att se hur du använder det här flera gånger i nästan alla skript som du skriver. Jag hoppas att du har en bättre förståelse än du hade tidigare.

<!-- link references -->
[ursprunglig version]: https://powershellexplained.com/2019-08-11-PowerShell-if-then-else-equals-operator/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[eventuella]: /powershell/module/microsoft.powershell.core/about/about_if
[bitvisa operatorer]: https://powershellexplained.com/powershell/module/microsoft.powershell.core/about/about_arithmetic_operators#bitwise-operators
[många sätt att använda regex]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression/
[allt du ville veta mer om undantag]: everything-about-exceptions.md
[allt du ville veta mer om $null]: everything-about-null.md
[Prasoon Karunan V]: https://twitter.com/prasoonkarunan
[allt du ville veta om switch-instruktionen]: everything-about-switch.md
[Invoke-SnowSql]: https://github.com/loanDepot/SnowSQL/blob/a3731b52e4ab4ecb503fb81e2d8cb131e8f90410/SnowSQL/public/Invoke-SnowSql.ps1#L90
