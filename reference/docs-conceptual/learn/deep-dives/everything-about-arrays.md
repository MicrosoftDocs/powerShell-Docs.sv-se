---
title: Allt du ville veta om matriser
description: Matriser är en grundläggande språk funktion för de flesta programmeringsspråk.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 5cab354a99b122401f8f8119de24e075cf9d21f8
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149924"
---
# <a name="everything-you-wanted-to-know-about-arrays"></a>Allt du ville veta om matriser

[Matriser][] är en grundläggande språk funktion för de flesta programmeringsspråk. De är en samling med värden eller objekt som är svåra att undvika. Låt oss ta en närmare titt på matriser och allt de behöver för att erbjuda.

> [!NOTE]
> Den [ursprungliga versionen][] av den här artikeln visas på bloggen som skrivits av [@KevinMarquette][] . PowerShell-teamet tackar för att dela det här innehållet med oss. Ta en titt på hans blogg på [PowerShellExplained.com][].

## <a name="what-is-an-array"></a>Vad är en matris?

Jag ska börja med en grundläggande teknisk beskrivning av vilka matriser som är och hur de används av de flesta programmeringsspråk innan jag växlar till andra sätt som PowerShell använder dem.

En matris är en data struktur som fungerar som en samling av flera objekt. Du kan iterera över matrisen eller komma åt enskilda objekt med ett index. Matrisen skapas som ett sekventiellt segment av minne där varje värde lagras direkt bredvid det andra.

Jag tittar på var och en av de här detaljerna.

## <a name="basic-usage"></a>Grundläggande användning

Eftersom matriser är en sådan grundläggande funktion i PowerShell finns det en enkel syntax för att arbeta med dem i PowerShell.

### <a name="create-an-array"></a>Skapa en matris

En tom matris kan skapas med hjälp av`@()`

```powershell
PS> $data = @()
PS> $data.count
0
```

Vi kan skapa en matris och dirigera den med värden genom att placera dem inom `@()` parentesen.

```powershell
PS> $data = @('Zero','One','Two','Three')
PS> $data.count
4

PS> $data
Zero
One
Two
Three
```

Den här matrisen innehåller 4 objekt. När vi kallar `$data` variabeln visas en lista över våra objekt. Om det är en sträng mat ris, får vi en rad per sträng.

Vi kan deklarera en matris på flera rader. Kommatecken är valfri i det här fallet och skrivs vanligt vis ut.

```powershell
$data = @(
    'Zero'
    'One'
    'Two'
    'Three'
)
```

Jag vill deklarera mina matriser på flera rader som. Det blir inte bara lättare att läsa när du har flera objekt, men det gör det också enklare att jämföra med tidigare versioner när du använder käll kontroll.

#### <a name="other-syntax"></a>Annan syntax

Det är vanligt att du `@()` använder syntaxen för att skapa en matris, men i kommaavgränsade listor fungerar det mesta av tiden.

```powershell
$data = 'Zero','One','Two','Three'
```

#### <a name="write-output-to-create-arrays"></a>Skriva utdata för att skapa matriser

Ett häftigt svårt att nämna är att du kan använda `Write-Output` för att snabbt skapa strängar i-konsolen.

```powershell
$data = Write-Output Zero One Two Three
```

Detta är praktiskt eftersom du inte behöver ange citat tecken runt strängarna när parametern accepterar strängar. Jag skulle aldrig göra detta i ett skript, men det är ett rättvist spel i-konsolen.

### <a name="accessing-items"></a>Åtkomst till objekt

Nu när du har en matris med objekt i den, kanske du vill komma åt och uppdatera dessa objekt.

#### <a name="offset"></a>Offset

För att få åtkomst till enskilda objekt använder vi hakparenteserna `[]` med ett förskjutnings värde som börjar vid 0. Så här får vi det första objektet i vår matris:

```powershell
PS> $data = 'Zero','One','Two','Three'
PS> $data[0]
Zero
```

Anledningen till varför vi använder noll här är att det första objektet är i början av listan, så vi använder en förskjutning på 0 objekt för att komma till den. För att komma till det andra objektet måste vi använda en förskjutning på 1 för att hoppa över det första objektet.

```powershell
PS> $data[1]
One
```

Detta innebär att det sista objektet finns vid förskjutning 3.

```powershell
PS> $data[3]
Three
```

#### <a name="index"></a>Index

Nu kan du se varför jag har valt de värden som jag gjorde för det här exemplet. Jag introducerade detta som en förskjutning eftersom det är det som är det som egentligen är, men den här förskjutningen kallas ofta för ett index. Ett index som startar vid `0` . För resten av den här artikeln anropar du förskjutningen av ett index.

#### <a name="special-index-tricks"></a>Särskilda index trick

På de flesta språk kan du bara ange ett enda tal som index och få ett enda objekt tillbaka.
PowerShell är mycket mer flexibelt. Du kan använda flera index samtidigt. Genom att tillhandahålla en lista över index kan vi välja flera objekt.

```powershell
PS> $data[0,2,3]
Zero
Two
Three
```

Objekten returneras baserat på ordningen på de index som tillhandahålls. Om du duplicerar ett index får du objektet båda gånger.

```powershell
PS> $data[3,0,3]
Three
Zero
Three
```

Vi kan ange en sekvens med siffror med den inbyggda `..` operatorn.

```powershell
PS> $data[1..3]
One
Two
Three
```

Detta fungerar även i omvänd ordning.

```powershell
PS> $data[3..1]
Three
Two
One
```

Du kan använda negativa index värden för att räkna från slutet. Så om du behöver det sista objektet i listan kan du använda `-1` .

```powershell
PS> $data[-1]
Three
```

Ett ord med varnings meddelande här med `..` operatorn. Sekvensen `0..-1` och `-1..0` utvärdera till värdena `0,-1` och `-1,0` . Det är enkelt att se `$data[0..-1]` och fundera på att räkna upp alla objekt om du glömmer den här informationen. `$data[0..-1]`ger dig samma värde som när `$data[0,-1]` du ger det första och sista objektet i matrisen (och inget av de andra värdena).

#### <a name="out-of-bounds"></a>Utanför intervallet

Om du försöker komma åt ett index för ett objekt som är i slutet av matrisen på de flesta språk får du någon typ av fel eller ett undantag. PowerShell returnerar ingenting i tysthet.

```powershell
PS> $null -eq $data[9000]
True
```

#### <a name="cannot-index-into-a-null-array"></a>Det går inte att indexera till en null-matris

Om din variabel är `$null` och du försöker indexera den som en matris får du ett `System.Management.Automation.RuntimeException` undantag med meddelandet `Cannot index into a null array` .

```powershell
PS> $empty = $null
SP> $empty[0]
Error: Cannot index into a null array.
```

Se därför till att matriserna inte är `$null` innan du försöker komma åt element i dem.

#### <a name="count"></a>Antal

Matriser och andra samlingar har en Count-egenskap som visar hur många objekt som finns i matrisen.

```powershell
PS> $data.count
4
```

PowerShell 3,0 har lagt till en Count-egenskap på de flesta objekt. Du kan ha ett enda objekt och det bör ge dig ett antal `1` .

```powershell
PS> $date = Get-Date
PS> $date.count
1
```

`$null`Det finns även en Count-egenskap förutom den returnerar `0` .

```powershell
PS> $null.count
0
```

Det finns vissa traps som jag ska gå tillbaka när jag söker efter `$null` eller tomma matriser senare i den här artikeln.

#### <a name="off-by-one-errors"></a>Av-ett fel

Ett vanligt programmerings fel har skapats eftersom matriser börjar vid index 0. Andra fel kan införas på två sätt.

Det första är att tänka på att du vill ha det andra objektet och använda ett index för `2` och verkligen hämtar det tredje objektet. Eller genom att fundera på att du har fyra objekt och du vill ha det sista objektet så använder du antalet för att komma åt det sista objektet.

```powershell
$data[ $data.count ]
```

PowerShell är perfekt glad att låta dig göra det och ge dig exakt det objekt som finns vid index 4: `$null` . Du bör använda `$data.count - 1` eller det `-1` som vi har lärt dig ovan.

```powershell
PS> $data[ $data.count - 1 ]
Three
```

Det är här du kan använda `-1` indexet för att hämta det sista elementet.

```powershell
PS> $data[ -1 ]
Three
```

Pettersson Dailey pekar också ut till mig som vi kan använda `$data.GetUpperBound(0)` för att hämta det högsta index numret.

```powershell
PS> $data.GetUpperBound(0)
Three
```

Det andra vanligaste sättet är när du går igenom listan och inte stoppar vid rätt tidpunkt. Jag går igenom detta när vi pratar om att använda `for` slingan.

### <a name="updating-items"></a>Uppdaterar objekt

Vi kan använda samma index för att uppdatera befintliga objekt i matrisen. Detta ger oss direkt åtkomst till uppdatering av enskilda objekt.

```powershell
$data[2] = 'dos'
$data[3] = 'tres'
```

Om vi försöker uppdatera ett objekt som har passerat det sista elementet får vi ett `Index was outside the bounds of the array.` fel meddelande.

```powershell
PS> $data[4] = 'four'
Index was outside the bounds of the array.
At line:1 char:1
+ $data[4] = 'four'
+ ~~~~~~~~~~~~~
+ CategoryInfo          : OperationStopped: (:) [], IndexOutOfRangeException
+ FullyQualifiedErrorId : System.IndexOutOfRangeException
```

Jag går tillbaka senare när jag pratar om hur man gör en matris större.

### <a name="iteration"></a>Iteration

Ibland kan du behöva gå igenom hela listan och utföra en åtgärd för varje objekt i matrisen.

#### <a name="pipeline"></a>Pipeline

Matriser och PowerShell-pipeline är avsedda för varandra. Detta är ett av de enklaste sätten att bearbeta dessa värden. När du skickar en matris till en pipeline bearbetas varje objekt i matrisen separat.

```powershell
PS> $data = 'Zero','One','Two','Three'
PS> $data | ForEach-Object {"Item: [$PSItem]"}
Item: [Zero]
Item: [One]
Item: [Two]
Item: [Three]
```

Om du inte har sett `$PSItem` tidigare vet du att det är samma sak som `$_` . Du kan använda antingen en, eftersom de båda representerar det aktuella objektet i pipelinen.

#### <a name="foreach-loop"></a>Förgrunds slinga

`ForEach`Slingan fungerar bra med samlingar. Använda syntaxen:`foreach ( <variable> in <collection> )`

```powershell
foreach ( $node in $data )
{
    "Item: [$node]"
}
```

#### <a name="foreach-method"></a>Förgrunds metod

Jag vill glömma bort det här, men det fungerar bra för enkla åtgärder. Med PowerShell kan du anropa `.ForEach()` en samling.

```powershell
PS> $data.foreach({"Item [$PSItem]"})
Item [Zero]
Item [One]
Item [Two]
Item [Three]
```

`.foreach()`Tar en parameter som är ett skript block. Du kan ta bort parenteserna och bara ange skript blocket.

```powershell
$data.foreach{"Item [$PSItem]"}
```

Detta är en mindre känd syntax, men den fungerar precis på samma sätt. Den här `foreach` metoden har lagts till i PowerShell 4,0.

#### <a name="for-loop"></a>For-slinga

`for`Slingan används kraftigt på de flesta andra språk, men du ser det inte mycket i PowerShell. När du gör det är det ofta i sammanhanget att gå en matris.

```powershell
for ( $index = 0; $index -lt $data.count; $index++)
{
    "Item: [{0}]" -f $data[$index]
}
```

Det första vi gör är att initiera en `$index` till `0` . Sedan lägger vi till villkoret som `$index` måste vara mindre än `$data.count` . Slutligen anger vi att det ska gå att öka indexet genom att varje gång vi loopar `1` . I det här fallet `$index++` är det kort för `$index = $index + 1` .

När du använder en `for` slinga bör du ägna särskild uppmärksamhet åt villkoret. Jag använde `$index -lt $data.count` detta. Det är enkelt att få tillståndet något fel för att få ett fel i din logik. `$index -le $data.count` `$index -lt ($data.count - 1)` Det kan vara något fel att använda eller. Detta skulle leda till att du bearbetar för många eller för få objekt. Detta är det klassiska fel meddelandet.

#### <a name="switch-loop"></a>Växel slinga

Det här är en som är lätt att förbise. Om du anger en matris till en [switch-instruktion][], kontrollerar den varje objekt i matrisen.

```powershell
$data = 'Zero','One','Two','Three'
switch( $data )
{
    'One'
    {
        'Tock'
    }
    'Three'
    {
        'Tock'
    }
    Default
    {
        'Tick'
    }
}
```

```Output
Tick
Tock
Tick
Tock
```

Det finns många häftiga saker som vi kan göra med Switch-instruktionen. Jag har en annan artikel som är engagerad i detta.

- [Allt du ville veta om switch-instruktionen][switch] -sats

#### <a name="updating-values"></a>Uppdaterar värden

Om matrisen är en samling strängar eller heltal (värde typer) kan ibland det hända att du vill uppdatera värdena i matrisen när du loopar. De flesta av slingarna ovan använder en variabel i slingan som innehåller en kopia av värdet. Om du uppdaterar variabeln, uppdateras inte det ursprungliga värdet i matrisen.

Undantaget till den instruktionen är `for` slingan. Om du vill visa en matris och uppdatera värden inuti den, `for` är loopen det du söker.

```powershell
for ( $index = 0; $index -lt $data.count; $index++ )
{
    $data[$index] = "Item: [{0}]" -f $data[$index]
}
```

Det här exemplet tar ett värde av indexet, gör några ändringar och använder sedan samma index för att tilldela det igen.

## <a name="arrays-of-objects"></a>Matriser med objekt

Hittills har vi placerat i en matris som värde typ, men matriser kan också innehålla objekt.

```powershell
$data = @(
    [pscustomobject]@{FirstName='Kevin';LastName='Marquette'}
    [pscustomobject]@{FirstName='John'; LastName='Doe'}
)
```

Många cmdlets returnerar samlingar av objekt som matriser när du tilldelar dem till en variabel.

```powershell
$processList = Get-Process
```

Alla grundläggande funktioner som vi redan har talat om fortfarande gäller för matriser med objekt med lite information som pekar på.

### <a name="accessing-properties"></a>Åtkomst till egenskaper

Vi kan använda ett index för att komma åt ett enskilt objekt i en samling, precis som med värde typerna.

```powershell
PS> $data[0]

FirstName LastName
-----     ----
Kevin     Marquette
```

Vi kan komma åt och uppdatera egenskaper direkt.

```powershell
PS> $data[0].FirstName

Kevin

PS> $data[0].FirstName = 'Jay'
PS> $data[0]

FirstName LastName
-----     ----
Jay       Marquette
```

#### <a name="array-properties"></a>Mat ris egenskaper

Normalt skulle du behöva räkna upp hela listan som detta för att få åtkomst till alla egenskaper:

```powershell
PS> $data | ForEach-Object {$_.LastName}

Marquette
Doe
```

Eller med hjälp av `Select-Object -ExpandProperty` cmdleten.

```powershell
PS> $data | Select-Object -ExpandProperty LastName

Marquette
Doe
```

Men PowerShell ger oss möjlighet att begära `LastName` direkt. PowerShell räknar upp dem för oss och returnerar en rensad lista.

```powershell
PS> $data.LastName

Marquette
Doe
```

Uppräkningen utförs fortfarande men vi ser inte komplexiteten bakom den.

### <a name="where-object-filtering"></a>Where-objekt filtrering

`Where-Object`I så fall kan vi filtrera och välja vad du vill ha i matrisen baserat på egenskaperna för objektet.

```powershell
PS> $data | Where-Object {$_.FirstName -eq 'Kevin'}

FirstName LastName
-----     ----
Kevin     Marquette
```

Vi kan skriva samma fråga för att få din `FirstName` sökning.

```powershell
$data | Where FirstName -eq Kevin
```

#### <a name="where"></a>Where ()

Matriser har en `Where()` metod för dem som gör att du kan ange en `scriptblock` för filtret.

```powershell
$data.Where({$_.FirstName -eq 'Kevin'})
```

Den här funktionen lades till i PowerShell 4,0.

### <a name="updating-objects-in-loops"></a>Uppdatera objekt i slingor

Med värde typer är det enda sättet att uppdatera matrisen att använda en for-loop eftersom vi måste känna till indexet för att ersätta värdet. Vi har fler alternativ med objekt eftersom de är referens typer. Här är ett snabbt exempel:

```powershell
foreach($person in $data)
{
    $person.FirstName = 'Kevin'
}
```

Den här slingen går igenom varje objekt i `$data` matrisen. Eftersom objekt är referens typer `$person` refererar variabeln exakt samma objekt som finns i matrisen. Så uppdateringar av dess egenskaper uppdaterar du originalet.

Du kan fortfarande inte ersätta hela objektet på det här sättet. Om du försöker tilldela ett nytt objekt till `$person` variabeln uppdaterar du variabel referensen till något annat som inte längre pekar på det ursprungliga objektet i matrisen. Detta fungerar som du förväntar dig:

```powershell
foreach($person in $data)
{
    $person = [pscustomobject]@{
        FirstName='Kevin'
        LastName='Marquette'
    }
}
```

## <a name="operators"></a>Operatorer

Operatorerna i PowerShell fungerar också på matriser. Några av dem fungerar något annorlunda.

### <a name="-join"></a>– Anslut

`-join`Operatören är den mest uppenbara, så låt oss titta på den först. Jag gillar `-join` operatorn och använder den ofta. Den kopplar ihop alla element i matrisen med det tecken eller den sträng som du anger.

```powershell
PS> $data = @(1,2,3,4)
PS> $data -join '-'
1-2-3-4
PS> $data -join ','
1,2,3,4
```

En av de funktioner som jag gillar om `-join` operatorn är att den hanterar enskilda objekt.

```powershell
PS> 1 -join '-'
1
```

Jag använder det här i loggnings-och utförliga meddelanden.

```powershell
PS> $data = @(1,2,3,4)
PS> "Data is $($data -join ',')."
Data is 1,2,3,4.
```

#### <a name="-join-array"></a>– Anslut $array

Här är ett smarta-stick som Pettersson Dailey påpekade till mig. I stället för att göra detta, om du vill koppla allt utan en avgränsare:

```powershell
PS> $data = @(1,2,3,4)
PS> $data -join $null
1234
```

Du kan använda `-join` med matrisen som parameter utan prefix. Ta en titt på det här exemplet för att se att jag pratar om.

```powershell
PS> $data = @(1,2,3,4)
PS> -join $data
1234
```

### <a name="-replace-and--split"></a>-Ersätt och-dela

De andra operatorerna som `-replace` och `-split` körs på varje objekt i matrisen. Jag kan inte säga att jag någonsin har använt dem på det här sättet, men här är ett exempel.

```powershell
PS> $data = @('ATX-SQL-01','ATX-SQL-02','ATX-SQL-03')
PS> $data -replace 'ATX','LAX'
LAX-SQL-01
LAX-SQL-02
LAX-SQL-03
```

### <a name="-contains"></a>– innehåller

Med `-contains` operatorn kan du kontrol lera en matris med värden för att se om den innehåller ett angivet värde.

```powershell
PS> $data = @('red','green','blue')
PS> $data -contains 'green'
True
```

### <a name="-in"></a>– in

Om du har ett enda värde som du vill verifiera matchar ett av flera värden kan du använda `-in` operatorn. Värdet är till vänster och matrisen på höger sida av åtgärden.

```powershell
PS> $data = @('red','green','blue')
PS> 'green' -in $data
True
```

Detta kan bli dyrt om listan är stor. Jag använder ofta ett regex-mönster om jag söker efter fler än några värden.

```powershell
PS> $data = @('red','green','blue')
PS> $pattern = "^({0})$" -f ($data -join '|')
PS> $pattern
^(red|green|blue)$

PS> 'green' -match $pattern
True
```

### <a name="-eq-and--ne"></a>-EQ och-Ne

Likheter och matriser kan bli komplicerade. När matrisen är på vänster sida jämförs varje objekt. I stället för att returnera returneras `True` det objekt som matchar.

```powershell
PS> $data = @('red','green','blue')
PS> $data -eq 'green'
green
```

När du använder `-ne` operatorn får vi alla värden som inte är lika med vårt värde.

```powershell
PS> $data = @('red','green','blue')
PS> $data -ne 'green'
red
blue
```

När du använder det här i en `if()` instruktion är ett värde som returneras ett `True` värde. Om inget värde returneras är det ett `False` värde. Båda dessa Next-instruktioner utvärderas till `True` .

```powershell
$data = @('red','green','blue')
if ( $data -eq 'green' )
{
    'Green was found'
}
if ( $data -ne 'green' )
{
    'And green was not found'
}
```

Jag går tillbaka så snart vi pratar om testningen av `$null` .

### <a name="-match"></a>-matcha

`-match`Operatorn försöker matcha varje objekt i samlingen.

```powershell
PS> $servers = @(
    'LAX-SQL-01'
    'LAX-API-01'
    'ATX-SQL-01'
    'ATX-API-01'
)
PS> $servers -match 'SQL'
LAX-SQL-01
ATX-SQL-01
```

När du använder `-match` med ett enda värde fylls en speciell variabel `$Matches` med matchnings information. Detta är inte fallet när en matris behandlas på det här sättet.

Vi kan utföra samma tillvägagångs sätt med `Select-String` .

```powershell
$servers | Select-String SQL
```

Jag tar en närmare titt på `Select-String` , `-match` och `$matches` variabeln i ett annat inlägg som kallas [för många sätt att använda regex][].

### <a name="null-or-empty"></a>$null eller tomt

`$null`Det kan vara svårt att testa för eller tomma matriser. Här är vanliga traps med matriser.

Den här instruktionen ser ut ungefär som den ska fungera.

```powershell
if ( $array -eq $null)
{
    'Array is $null'
}
```

Men jag gick bara igenom hur `-eq` kontrollerar varje objekt i matrisen. Vi kan därför ha en matris med flera objekt med ett enda $null värde och det skulle utvärderas till`$true`

```powershell
$array = @('one',$null,'three')
if ( $array -eq $null)
{
    'I think Array is $null, but I would be wrong'
}
```

Det är därför det bästa sättet att placera `$null` på den vänstra sidan av operatören. Detta gör att det här scenariot inte är ett problem.

```powershell
if ( $null -eq $array )
{
    'Array actually is $null'
}
```

En `$null` matris är inte samma sak som en tom matris. Om du vet att du har en matris kontrollerar du antalet objekt i den. Om matrisen är är `$null` antalet `0` .

```powershell
if ( $array.count -gt 0 )
{
    'Array isn't empty'
}
```

Det finns ytterligare en svällning att titta närmare på. Du kan använda `count` även om du har ett enda objekt, om inte objektet är ett `PSCustomObject` . Detta är ett fel som korrigeras i PowerShell 6,1.
Det är goda nyheter, men många människor är kvar på 5,1 och behöver titta på det.

```powershell
PS> $object = [PSCustomObject]@{Name='TestObject'}
PS> $object.count
$null
```

Om du fortfarande använder PowerShell 5,1 kan du figursätta objektet i en matris innan du kontrollerar antalet för att få ett korrekt antal.

```powershell
if ( @($array).count -gt 0 )
{
    'Array isn't empty'
}
```

Kontrol lera och kontrol lera antalet för att kunna spela upp det säkert `$null` .

```powershell
if ( $null -ne $array -and @($array).count -gt 0 )
{
    'Array isn't empty'
}
```

### <a name="all--eq"></a>Alla-EQ

Jag såg nyligen någon fråga om att [kontrol lera att varje värde i en matris matchar ett angivet värde][].
Reddit User **/u/BIS** hade denna smarta- [lösning][] som söker efter felaktiga värden och vänder sedan resultatet.

```powershell
$results = Test-Something
if ( -not ( $results -ne 'Passed') )
{
    'All results a Passed'
}
```

## <a name="adding-to-arrays"></a>Lägga till i matriser

Nu börjar du med att undrar hur du lägger till objekt i en matris. Det snabba svaret är att du inte kan. En matris är en fast storlek i minnet. Om du behöver utöka den eller lägga till ett enda objekt i det måste du skapa en ny matris och kopiera alla värden från den gamla matrisen. Det här låter dyra och som mycket arbete, men PowerShell döljer komplexiteten för att skapa den nya matrisen.

### <a name="array-addition"></a>Mat ris tillägg

Vi kan använda operatorn addition med arrayer för att skapa en ny matris. Vi har fått dessa två matriser:

```powershell
$first = @(
    'Zero'
    'One'
)
$second = @(
    'Two'
    'Three'
)
```

Vi kan lägga till dem tillsammans för att få en ny matris.

```powershell
PS> $first + $second

Zero
One
Two
Three
```

### <a name="plus-equals-"></a>Plus lika med + =

Vi kan skapa en ny matris på plats och lägga till ett objekt i den så här:

```powershell
$data = @(
    'Zero'
    'One'
    'Two'
    'Three'
)
$data += 'four'
```

Kom bara ihåg att varje gång du använder `+=` som du duplicerar och skapar en ny matris. Detta är inte ett problem för små data uppsättningar, men det skalas extremt dåligt.

### <a name="pipeline-assignment"></a>Pipeline-tilldelning

Du kan tilldela resultatet av en pipeline till en variabel. Det är en matris om den innehåller flera objekt.

```powershell
$array = 1..5 | ForEach-Object {
    "ATX-SQL-$PSItem"
}
```

Normalt när vi tänker på att använda pipelinen kommer vi att tänka på en typisk PowerShell-liners. Vi kan utnyttja pipelinen med `foreach()` instruktioner och andra slingor. I stället för att lägga till objekt i en matris i en slinga kan vi släppa objekt i pipelinen.

```powershell
$array = foreach ( $node in (1..5))
{
    "ATX-SQL-$node"
}
```

Genom att tilldela resultatet av `foreach` en variabel fångar vi alla objekt och skapar en enda matris.

## <a name="array-types"></a>Mat ris typer

Som standard skapas en matris i PowerShell som en `[PSObject[]]` typ. Detta gör att den kan innehålla alla typer av objekt eller värden. Detta fungerar eftersom allt ärvs från `PSObject` typen.

### <a name="strongly-typed-arrays"></a>Starkt skrivna matriser

Du kan skapa en matris av vilken typ som helst med hjälp av samma syntax. När du skapar en starkt angiven matris får den bara innehålla värden eller objekt av den angivna typen.

```powershell
PS> [int[]] $numbers = 1,2,3
PS> [int[]] $numbers2 = 'one','two','three'
ERROR: Cannot convert value "one" to type "System.Int32". Input string was not in a correct format."

PS> [string[]] $strings = 'one','two','three'
```

### <a name="arraylist"></a>ArrayList

Att lägga till objekt i en matris är en av dess största begränsningar, men det finns några andra samlingar som vi kan göra för att lösa problemet.

`ArrayList`Är vanligt vis ett av de första saker som vi tänker på när vi behöver en matris som är snabbare att arbeta med. Den fungerar som en objekt mat ris varje plats som vi behöver det, men det hanterar snabbt tillägg av objekt.

Så här skapar vi en `ArrayList` och lägger till objekt i den.

```powershell
$myarray = [System.Collections.ArrayList]::new()
[void]$myArray.Add('Value')
```

Vi ringer till .NET för att få den här typen. I det här fallet använder vi Standardkonstruktorn för att skapa den. Sedan anropar vi `Add` metoden för att lägga till ett objekt i det.

Anledningen till att jag använder `[void]` i början av raden är att utelämna retur koden. Vissa .NET-anrop gör detta och kan skapa oväntade utdata.

Om de enda data som du har i matrisen är strängar, tar du också en titt på att använda [StringBuilder][]. Det är nästan samma sak men har några metoder som bara är för att hantera strängar. `StringBuilder`Är särskilt utformad för prestanda.

Det är vanligt att du ser att personer flyttas till `ArrayList` från matriser. Men det kommer från en tid där C# inte hade generisk support. `ArrayList`Är avskriven i stöd för den generiska`List[]`

### <a name="generic-list"></a>Allmän lista

En generisk typ är en särskild typ i C# som definierar en generaliserad klass och användaren anger de data typer som används när den skapas. Så om du vill ha en lista med tal eller strängar definierar du att du vill ha en lista över `int` eller `string` typer.

Så här skapar du en lista med strängar.

```powershell
$mylist = [System.Collections.Generic.List[string]]::new()
```

Eller en lista med tal.

```powershell
$mylist = [System.Collections.Generic.List[int]]::new()
```

Vi kan omvandla en befintlig matris till en lista som detta utan att först skapa objektet:

```powershell
$mylist = [System.Collections.Generic.List[int]]@(1,2,3)
```

Vi kan förkorta syntaxen med `using namespace` instruktionen i PowerShell 5 och senare. `using`Instruktionen måste vara den första raden i skriptet. Genom att deklarera ett namn område kan du använda PowerShell för att lämna det av data typerna när du refererar till dem.

```powershell
using namespace System.Collections.Generic
$myList = [List[int]]@(1,2,3)
```

Detta gör det `List` mycket mer användbart.

Du har en liknande `Add` metod som är tillgänglig för dig. Till skillnad från ArrayList finns det inget retur värde för metoden, `Add` så vi behöver inte göra `void` det.

```powershell
$myList.Add(10)
```

Och vi har fortfarande åtkomst till elementen som andra matriser.

```powershell
PS> $myList[-1]
10
```

#### <a name="listpsobject"></a>Lista [PSObject]

Du kan ha en lista över vilken typ som helst, men när du inte vet vilken typ av objekt du kan använda `[List[PSObject]]` för att ta med dem.

```powershell
$list = [List[PSObject]]::new()
```

#### <a name="remove"></a>Remove()

`ArrayList`Och generiskt `List[]` stöder borttagning av objekt från samlingen.

```powershell
using namespace System.Collections.Generic
$myList = [List[string]]@('Zero','One','Two','Three')
[void]$myList.Remove("Two")
Zero
One
Three
```

När du arbetar med värde typer tar den bort det första från listan. Du kan anropa det igen om du vill fortsätta att ta bort värdet. Om du har referens typer måste du ange det objekt som du vill ta bort.

```powershell
[list[System.Management.Automation.PSDriveInfo]]$drives = Get-PSDrive
$drives.remove($drives[2])
```

```powershell
$delete = $drives[2]
$drives.remove($delete)
```

Metoden Remove returnerar `true` om den kunde hitta och ta bort objektet från samlingen.

### <a name="more-collections"></a>Fler samlingar

Det finns många andra samlingar som kan användas, men de är bra generiska matriser.
Om du är intresse rad av att lära dig mer av de här alternativen kan du ta en titt på det här [registret](https://gist.github.com/kevinblumenfeld/4a698dbc90272a336ed9367b11d91f1c) som [markerar Kraus](https://get-powershellblog.blogspot.com/2016/11/about-mark-kraus.html) .

## <a name="other-nuances"></a>Andra olika delarna

Nu när jag har täckt alla större funktioner finns här några saker som jag ville nämna innan jag omsluter detta.

### <a name="pre-sized-arrays"></a>I storleks mat ris

Jag nämnde att du inte kan ändra storleken på en matris när den har skapats. Vi kan skapa en matris med en fördefinierad storlek genom att anropa den med `new($size)` konstruktorn.

```powershell
$data = [Object[]]::new(4)
$data.count
4
```

### <a name="multiplying-arrays"></a>Multiplicerar matriser

Ett intressant litet stick är att du kan multiplicera en matris med ett heltal.

```powershell
PS> $data = @('red','green','blue')
PS> $data * 3
red
green
blue
red
green
blue
red
green
blue
```

### <a name="initialize-with-0"></a>Initiera med 0

Ett vanligt scenario är att du vill skapa en matris med enbart nollor. Om du bara kommer att använda heltal, är en stark inskriven matris med heltal som standard alla nollor.

```powershell
PS> [int[]]::new(4)
0
0
0
0
```

Vi kan även använda det multipliceringa sticket för att göra detta.

```powershell
PS> $data = @(0) * 4
PS> $data
0
0
0
0
```

Det som är trevligt om att multiplicera sticket är att du kan använda vilket värde som helst. Så om du hellre vill ha det `255` som standardvärde, är det ett bra sätt att göra det.

```powershell
PS> $data = @(255) * 4
PS> $data
255
255
255
255
```

### <a name="nested-arrays"></a>Kapslade matriser

En matris i en matris kallas för en kapslad matris. Jag använder inte dessa mycket i PowerShell men jag har använt dem på andra språk. Överväg att använda en matris med matriser när dina data passar i ett rutnät som mönster.

Här följer två sätt att skapa en tvådimensionell matris.

```powershell
$data = @(@(1,2,3),@(4,5,6),@(7,8,9))

$data2 = @(
    @(1,2,3),
    @(4,5,6),
    @(7,8,9)
)
```

Kommatecknet är mycket viktigt i de här exemplen. Jag fick ett tidigare exempel på en normal matris på flera rader där kommatecknet var valfritt. Det är inte fallet med en flerdimensionell matris.

Hur vi använder index notation ändras en aning nu när vi har en kapslad matris. Vi använder `$data` ovanstående för att få åtkomst till värdet 3.

```powershell
PS> $outside = 0
PS> $inside = 2
PS> $data[$outside][$inside]
3
```

Lägg till en uppsättning hakparenteser för varje nivå av mat ris kapsling. Den första uppsättningen hakparenteser är för den yttre mest matrisen och sedan arbetar du på ditt sätt i därifrån.

### <a name="write-output--noenumerate"></a>Write-output-noenumeration

PowerShell gillar att packa upp eller räkna upp matriser. Detta är en grund aspekt av hur PowerShell använder pipelinen, men det finns tillfällen då du inte vill att det ska hända.

Jag rör ofta objekt till `Get-Member` för att lära sig mer om dem. När jag rör en matris till den, kommer den att bli figursatt och Get-Member ser medlemmarna i matrisen och inte själva matrisen.

```powershell
PS> $data = @('red','green','blue')
PS> $data | Get-Member
TypeName: System.String
...
```

Du kan använda för att förhindra att matrisen bryts av `Write-Object -NoEnumerate` .

```powershell
PS> Write-Output -NoEnumerate $data | Get-Member
TypeName: System.Object[]
...
```

Jag har ett andra sätt som är mer av ett Hack (och jag försöker undvika hackningar som detta). Du kan placera ett kommatecken framför matrisen innan du rör det.

```powershell
PS> ,$data | Get-Member
TypeName: System.Object[]
...
```

### <a name="return-an-array"></a>Returnera en matris

Den här omplaceringen av matriser sker också när du matar ut eller returnerar värden från en funktion. Du kan fortfarande hämta en matris om du tilldelar utdata till en variabel, så det är inte ofta ett problem.

Fångsten är att du har en ny matris. Om det skulle uppstå ett problem kan du använda `Write-Output -NoEnumerate $array` eller `return ,$array` för att undvika det.

## <a name="anything-else"></a>Något mer?

Jag vet att det är allt du behöver göra i. Min idé är att du lär dig något från den här artikeln varje gång du läser det och att det blir en lämplig referens till dig under lång tid att komma. Om du har hittat detta för att vara till hjälp kan du dela den med andra som du tror kan få ett värde av det.

Härifrån rekommenderar vi att du tar en titt på ett liknande inlägg som jag skrev om [hash][].

<!-- link references -->
[ursprunglig version]: https://powershellexplained.com/2018-10-15-Powershell-arrays-Everything-you-wanted-to-know/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Matriser]: /powershell/module/microsoft.powershell.core/about/about_arrays
[Switch-instruktion]: everything-about-switch.md
[hash]: everything-about-hashtable.md
[Många sätt att använda regex]: https://powershellexplained.com/2017-07-31-Powershell-regex-regular-expression/
[så här kontrollerar du att varje värde i en matris matchar ett angivet värde]: https://www.reddit.com/r/PowerShell/comments/9mzo09/if_statement_multiple_variables_but_1_condition
[lösa]: https://www.reddit.com/r/PowerShell/comments/9mzo09/if_statement_multiple_variables_but_1_condition/e7iizca
[StringBuilder]: https://powershellexplained.com/2017-11-20-Powershell-StringBuilder/
