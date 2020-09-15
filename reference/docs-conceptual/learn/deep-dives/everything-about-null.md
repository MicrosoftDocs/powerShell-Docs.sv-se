---
title: Allt du ville veta mer om $null
description: PowerShell-$null verkar ofta vara enkelt men det har många olika delarna. Låt oss ta en närmare titt på $null så att du vet vad som händer när du plötsligt kör ett null-värde.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: e0553a5e17450d8044f548792649369e99903850
ms.sourcegitcommit: d0461273abb6db099c5e784ef00f57fd551be4a6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/01/2020
ms.locfileid: "84149833"
---
# <a name="everything-you-wanted-to-know-about-null"></a>Allt du ville veta mer om $null

PowerShell `$null` verkar ofta vara enkelt men det har många olika delarna. Låt oss ta en närmare titt på `$null` så att du vet vad som händer när du har råkat ut för ett `$null` värde.

> [!NOTE]
> Den [ursprungliga versionen][] av den här artikeln visas på bloggen som skrivits av [@KevinMarquette][] . PowerShell-teamet tackar för att dela det här innehållet med oss. Ta en titt på hans blogg på [PowerShellExplained.com][].

## <a name="what-is-null"></a>Vad är NULL?

Du kan tänka på NULL som ett okänt eller tomt värde. En variabel är NULL tills du tilldelar ett värde eller ett objekt till det. Detta kan vara viktigt eftersom det finns vissa kommandon som kräver ett värde och genererar fel om värdet är NULL.

### <a name="powershell-null"></a>PowerShell-$null

`$null` är en automatisk variabel i PowerShell som används för att representera NULL. Du kan tilldela den till variabler, använda den i jämförelser och använda den som plats hållare för NULL i en samling.

PowerShell behandlar `$null` som ett objekt med värdet null. Detta skiljer sig från vad du kan förväntar dig om du kommer från ett annat språk.

## <a name="examples-of-null"></a>Exempel på $null

När du försöker använda en variabel som du inte har initierat är värdet `$null` . Detta är ett av de vanligaste sätten att `$null` använda värden i koden.

```powershell
PS> $null -eq $undefinedVariable
True
```

Om du råkar skriva ett variabel namn, ser PowerShell det som en annan variabel och värdet är `$null` .

Det andra sättet att hitta `$null` värden är när de kommer från andra kommandon som inte ger dig några resultat.

```powershell
PS> function Get-Nothing {}
PS> $value = Get-Nothing
PS> $null -eq $value
True
```

## <a name="impact-of-null"></a>Effekt av $null

`$null` värdena påverkar koden på olika sätt beroende på var de visas.

### <a name="in-strings"></a>I strängar

Om du använder `$null` i en sträng är det ett tomt värde (eller en tom sträng).

```powershell
PS> $value = $null
PS> Write-Output "The value is $value"
The value is
```

Detta är en av orsakerna till att jag vill placera hakparenteser runt variabler när de använder dem i logg meddelanden. Det är ännu mer viktigt att identifiera kanterna på dina variabel värden när värdet är i slutet av strängen.

```powershell
PS> $value = $null
PS> Write-Output "The value is [$value]"
The value is []
```

Detta gör tomma strängar och `$null` värden enkla att upptäcka.

### <a name="in-numeric-equation"></a>I numerisk ekvation

När ett `$null` värde används i en numerisk ekvation är resultatet ogiltigt om det inte ger ett fel. Ibland `$null` utvärderas `0` resultatet och andra gånger det blir hela resultatet `$null` .
Här är ett exempel med multiplikation som ger 0 eller `$null` beroende på ordningen för värdena.

```powershell
PS> $null * 5
PS> $null -eq ( $null * 5 )
True

PS> 5 * $null
0
PS> $null -eq ( 5 * $null )
False
```

### <a name="in-place-of-a-collection"></a>I stället för en samling

Med en samling kan du använda ett index för att få åtkomst till värden. Om du försöker indexera i en samling som faktiskt används `null` får du följande fel meddelande: `Cannot index into a null array` .

```powershell
PS> $value = $null
PS> $value[10]
Cannot index into a null array.
At line:1 char:1
+ $value[10]
+ ~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [], RuntimeException
    + FullyQualifiedErrorId : NullArray
```

Om du har en samling men försöker komma åt ett element som inte finns i samlingen får du ett `$null` resultat.

```powershell
$array = @( 'one','two','three' )
$null -eq $array[100]
True
```

### <a name="in-place-of-an-object"></a>I stället för ett objekt

Om du försöker komma åt en egenskap eller under egenskap för ett objekt som inte har den angivna egenskapen får du ett `$null` värde som du skulle göra för en odefinierad variabel. Det spelar ingen roll om variabeln är `$null` eller ett faktiskt objekt i det här fallet.

```powershell
PS> $null -eq $undefined.some.fake.property
True

PS> $date = Get-Date
PS> $null -eq $date.some.fake.property
True
```

### <a name="method-on-a-null-valued-expression"></a>Metod i ett null-värde-uttryck

Anropa en metod på ett `$null` objekt genererar en `RuntimeException` .

```powershell
PS> $value = $null
PS> $value.toString()
You cannot call a method on a null-valued expression.
At line:1 char:1
+ $value.tostring()
+ ~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [], RuntimeException
    + FullyQualifiedErrorId : InvokeMethodOnNull
```

När jag ser frasen `You cannot call a method on a null-valued expression` är det första du letar efter platser där jag anropar en metod i en variabel utan att först kontrol lera den `$null` .

## <a name="checking-for-null"></a>Söker efter $null

Du kanske har märkt att jag alltid placerar den till `$null` vänster när jag söker efter `$null` i mina exempel. Detta är avsiktligt och accepterat som en PowerShell-metod. Det finns vissa scenarier där det inte ger det förväntade resultatet.

Titta på följande exempel och försök att förutsäga resultaten:

```powershell
if ( $value -eq $null )
{
    'The array is $null'
}
if ( $value -ne $null )
{
    'The array is not $null'
}
```

Om jag inte definierar `$value` , kommer den första uppgiften att utvärderas till `$true` och vårt meddelande är `The array is $null` . Trap här är att det är möjligt att skapa en `$value` som låter båda `$false`

```powershell
$value = @( $null )
```

I det här fallet `$value` är en matris som innehåller en `$null` . `-eq`Kontrollerar varje värde i matrisen och returnerar det `$null` som matchar. Detta utvärderas till `$false` . `-ne`Returnerar allt som inte matchar `$null` och i det här fallet finns det inga resultat (detta utvärderas även till `$false` ). Varken en är `$true` trots att den ser ut som en av dem.

Det går inte bara att skapa ett värde som gör att båda utvärderas till `$false` . det är möjligt att skapa ett värde där de båda utvärderas `$true` . Mathias Jessen ( @IISResetMe ) har ett [lämpligt inlägg][] som dykningar i det scenariot.

### <a name="psscriptanalyzer-and-vscode"></a>PSScriptAnalyzer och VSCode

[PSScriptAnalyzer][] -modulen har en regel som söker efter det här problemet som kallas `PSPossibleIncorrectComparisonWithNull` .

```powershell
PS> Invoke-ScriptAnalyzer ./myscript.ps1

RuleName                              Message
--------                              -------
PSPossibleIncorrectComparisonWithNull $null should be on the left side of equality comparisons.
```

Eftersom VS Code använder PSScriptAnalyser-reglerna också, markerar den eller identifierar det som ett problem i skriptet.

### <a name="simple-if-check"></a>Enkel om-kontroll

Ett vanligt sätt att söka efter ett värde som inte är $null är att använda en enkel `if()` instruktion utan jämförelse.

```powershell
if ( $value )
{
    Do-Something
}
```

Om värdet är `$null` , utvärderas detta till `$false` . Detta är enkelt att läsa, men var noga med att leta efter exakt det du förväntar dig att söka efter. Jag läser den raden med kod som:

> Om `$value` har ett värde.

Men det är inte hela berättelsen. Den raden säger egentligen:

> Om `$value` inte är `$null` eller `0` eller `$false``empty string`

Här är ett mer komplett exempel på den här instruktionen.

```powershell
if ( $null -ne $value -and
        $value -ne 0 -and
        $value -ne '' -and
        $value -ne $false )
{
    Do-Something
}
```

Det är perfekt att använda en grundläggande `if` kontroll så länge du minns att de andra värdena räknas som `$false` och inte bara att en variabel har ett värde.

Jag har stött på det här problemet vid omstrukturering av några få dagar sedan. Den hade en grundläggande egenskaps kontroll som detta.

```powershell
if ( $object.property )
{
    $object.property = $value
}
```

Jag ville bara tilldela ett värde till egenskapen objekt om det fanns. I de flesta fall hade det ursprungliga objektet ett värde som skulle utvärderas `$true` i `if` instruktionen. Men jag stötte på ett problem där värdet ibland inte skulle hämtas. Jag har felsökt koden och upptäckt att objektet hade egenskapen men det var ett tomt sträng värde. Detta förhindrade att det någonsin uppdaterades med föregående logik. Jag har nu lagt till en korrekt `$null` kontroll och allt arbete.

```powershell
if ( $null -ne $object.property )
{
    $object.property = $value
}
```

Det är en liten del buggar som är svår att upptäcka och gör så att du kan kontrol lera värdena på ett aggressivt sätt `$null` .

## <a name="nullcount"></a>$null. Reparationer

Om du försöker få åtkomst till en egenskap för ett `$null` värde är egenskapen också `$null` . `count`Egenskapen är undantags felet för den här regeln.

```powershell
PS> $value = $null
PS> $value.count
0
```

När du har ett `$null` värde `count` är det `0` . Den här särskilda egenskapen läggs till av PowerShell.

### <a name="pscustomobject-count"></a>PSCustomObject Reparationer

Nästan alla objekt i PowerShell har denna egenskap Count. Ett viktigt undantag är `[PSCustomObject]` i Windows PowerShell 5,1 (detta åtgärdas i PowerShell 6,0). Det finns ingen Count-egenskap så du får ett `$null` värde om du försöker använda det. Jag kallar det här så att du inte försöker använda `.Count` i stället för en `$null` kontroll.

Genom att köra det här exemplet på Windows PowerShell 5,1 och PowerShell 6,0 får du olika resultat.

```powershell
$value = [PSCustomObject]@{Name='MyObject'}
if ( $value.count -eq 1 )
{
    "We have a value"
}
```

## <a name="empty-null"></a>Tomt null

Det finns en speciell typ av `$null` som fungerar annorlunda än de andra. Jag kommer att anropa det tomt, `$null` men det är verkligen en [system. Management. Automation. Internal. AutomationNull][]. Detta tomt `$null` är det som du får som ett resultat av en funktion eller ett skript block som returnerar inget (ett void-resultat).

```powershell
PS> function Get-Nothing {}
PS> $nothing = Get-Nothing
PS> $null -eq $nothing
True
```

Om du jämför den med får `$null` du ett `$null` värde. När det används i en utvärdering där ett värde krävs är värdet alltid `$null` . Men om du placerar det inuti en matris behandlas det på samma sätt som en tom matris.

```powershell
PS> $containempty = @( @() )
PS> $containnothing = @($nothing)
PS> $containnull = @($null)

PS> $containempty.count
0
PS> $containnothing.count
0
PS> $containnull.count
1
```

Du kan ha en matris som innehåller ett `$null` värde och dess `count` är `1` . Men om du placerar ett tomt resultat i en matris räknas det inte som ett objekt. Antalet är `0` .

Om du behandlar det tomma `$null` objektet som en samling är det tomt.

### <a name="pipeline"></a>Pipeline

Den primära plats som du ser är skillnaden när du använder pipelinen. Du kan skicka ett `$null` värde, men inte ett tomt `$null` värde.

```powershell
PS> $null | ForEach-Object{ Write-Output 'NULL Value' }
'NULL Value'
PS> $nothing | ForEach-Object{ Write-Output 'No Value' }
```

Beroende på din kod bör du ha ett konto för `$null` i din logik.

Sök antingen efter `$null` första

- Filtrera bort null i pipelinen ( `... | Where {$null -ne $_} | ...` )
- Hantera den i pipeline-funktionen

## <a name="foreach"></a>foreach

En av mina favorit funktioner i `foreach` är att den inte räknar upp över en `$null` samling.

```powershell
foreach ( $node in $null )
{
    #skipped
}
```

Detta sparar mig från att behöva `$null` kontrol lera samlingen innan jag räknar upp den. Om du har en samling med `$null` värden kan det `$node` fortfarande vara `$null` .

Den här metoden började arbeta på det här sättet med PowerShell 3,0. Om du råkar vara på en äldre version är detta inte fallet. Detta är en av de viktiga ändringarna som du bör känna till när du säkerhetskopierar kod för 2,0-kompatibilitet.

## <a name="value-types"></a>Värde typer

Tekniskt sett kan endast referens typer användas `$null` . Men PowerShell är mycket generöst och gör det möjligt för variabler att vara vilken typ som helst. Om du bestämmer dig för att ange en värdetyp som är absolut, kan det inte vara `$null` .
PowerShell konverterar `$null` till ett standardvärde för många typer.

```powershell
PS> [int]$number = $null
PS> $number
0

PS> [bool]$boolean = $null
PS> $boolean
False

PS> [string]$string = $null
PS> $string -eq ''
True
```

Det finns vissa typer som inte har någon giltig konvertering från `$null` . De här typerna genererar ett `Cannot convert null to type` fel.

```powershell
PS> [datetime]$date = $null
Cannot convert null to type "System.DateTime".
At line:1 char:1
+ [datetime]$date = $null
+ ~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : MetadataError: (:) [], ArgumentTransformationMetadataException
    + FullyQualifiedErrorId : RuntimeException
```

### <a name="function-parameters"></a>Funktions parametrar

Att använda ett starkt angivet värde i funktions parametrar är mycket vanligt. Vi lär dig vanligt vis att definiera typerna av parametrar även om vi inte brukar definiera typerna av andra variabler i våra skript. Du kanske redan har några starkt skrivna variabler i dina funktioner och inte ens inser det.

```powershell
function Do-Something
{
    param(
        [String] $Value
    )
}
```

När du anger typen för parametern som en `string` , kan värdet aldrig vara `$null` . Det är vanligt att kontrol lera om ett värde är `$null` att se om användaren har angett ett värde eller inte.

```powershell
if ( $null -ne $Value ){...}
```

`$Value` är en tom sträng `''` när inget värde har angetts. Använd den automatiska variabeln `$PSBoundParameters.Value` i stället.

```powershell
if ( $null -ne $PSBoundParameters.Value ){...}
```

`$PSBoundParameters` innehåller bara de parametrar som angavs när funktionen anropades.
Du kan också använda- `ContainsKey` metoden för att kontrol lera egenskapen.

```powershell
if ( $PSBoundParameters.ContainsKey('Value') ){...}
```

### <a name="isnotnullorempty"></a>IsNotNullOrEmpty

Om värdet är en sträng kan du använda en statisk sträng funktion för att kontrol lera om värdet är `$null` eller en tom sträng på samma tidpunkt.

```powershell
if ( -not [string]::IsNullOrEmpty( $value ) ){...}
```

Jag hittar mig själv med hjälp av det här ofta när jag vet att värde typen ska vara en sträng.

## <a name="when-i-null-check"></a>När jag $null check

Jag är en försvars skript. När jag anropar en funktion och tilldelar den till en variabel, kontrollerar jag den för `$null` .

```powershell
$userList = Get-ADUser kevmar
if ($null -ne $userList){...}
```

Jag föredrar att använda `if` eller `foreach` via användning `try/catch` . Jag vill inte ha fel, jag använder fortfarande `try/catch` mycket. Men om jag kan testa ett fel tillstånd eller en tom uppsättning resultat, kan jag tillåta min undantags hantering för sanna undantag.

Jag tenderar också att söka efter `$null` innan jag indexerar till ett värde eller anropar metoder för ett objekt. De här två åtgärderna kan inte utföras för ett `$null` objekt så jag tycker att det är viktigt att validera dem först. Jag har redan täckt de scenarierna tidigare i det här inlägget.

### <a name="no-results-scenario"></a>Inget resultat scenario

Det är viktigt att veta att olika funktioner och kommandon hanterar scenariot för inga resultat annorlunda. Många PowerShell-kommandon Returnerar tom `$null` och ett fel i fel strömmen. Men andra genererar undantag eller ger dig ett status objekt. Det är fortfarande upp till dig att veta hur de kommandon som du använder hanterar med inga resultat och fel scenarier.

## <a name="initializing-to-null"></a>Initierar till $null

En jag har valt att initiera alla mina variabler innan jag använder dem. Du måste göra detta på andra språk. Överst i min funktion eller när jag anger en förgrunds slinga definierar jag alla värden som jag använder.

Här är ett scenario som jag vill ta en nära titt på. Det är ett exempel på ett fel som jag hade kunnat spåra innan.

```powershell
function Do-Something
{
    foreach ( $node in 1..6 )
    {
        try
        {
            $result = Get-Something -ID $node
        }
        catch
        {
            Write-Verbose "[$result] not valid"
        }

        if ( $null -ne $result )
        {
            Update-Something $result
        }
    }
}
```

Förväntat här är att `Get-Something` returnerar antingen ett resultat eller en tom `$null` . Om det uppstår ett fel loggar vi det. Sedan kontrollerar vi att vi fick ett giltigt resultat innan du bearbetar det.

Fel som döljer i den här koden är när `Get-Something` ett undantag utlöses och inget värde tilldelas `$result` . Det Miss lyckas före tilldelningen så att vi inte ens tilldelar `$null` `$result` variabeln. `$result` innehåller fortfarande föregående giltig `$result` från andra iterationer.
`Update-Something` för att köra flera gånger på samma objekt i det här exemplet.

Jag har ställt in `$result` till `$null` höger i förgrunds-slingan innan jag använder den för att undvika det här problemet.

```powershell
foreach ( $node in 1..6 )
{
    $result = $null
    try
    {
        ...
```

### <a name="scope-issues"></a>Omfattnings problem

Detta hjälper också till att minska omfattnings problem. I det exemplet tilldelar vi värden till `$result` över och över i en slinga. Men eftersom PowerShell tillåter variabel värden utanför funktionen att utlösas i omfånget för den aktuella funktionen, minimerar de fel som kan introduceras på det sättet genom att initiera dem i funktionen.

En oinitierad variabel i funktionen är inte `$null` om den har angetts till ett värde i en överordnad omfattning.
Det överordnade omfånget kan vara en annan funktion som anropar din funktion och använder samma variabel namn.

Om jag `Do-something` använder samma exempel och tar bort slingan så skulle jag få något som ser ut som i det här exemplet:

```powershell
function Invoke-Something
{
    $result = 'ParentScope'
    Do-Something
}

function Do-Something
{
    try
    {
        $result = Get-Something -ID $node
    }
    catch
    {
        Write-Verbose "[$result] not valid"
    }

    if ( $null -ne $result )
    {
        Update-Something $result
    }
}
```

Om anropet `Get-Something` returnerar ett undantag `$null` hittar min kontroll `$result` från `Invoke-Something` . Att initiera värdet i funktionen minskar det här problemet.

Namngivning av variabler är svårt och det är vanligt att en författare använder samma variabel namn i flera funktioner. Jag vet att jag använder `$node` , `$result` och `$data` hela tiden. Det skulle då vara mycket enkelt för värden från olika omfattningar att visas på platser där de inte ska vara det.

## <a name="redirect-output-to-null"></a>Omdirigera utdata till $null

Jag har pratat om `$null` värden för hela artikeln men avsnittet är inte klart om jag inte omdirigeringen av utdata till `$null` . Det finns tillfällen när du har kommandon som utvärderar information eller objekt som du vill ignorera. Omdirigerar utdata till `$null` gör det.

### <a name="out-null"></a>Ut-null

Kommandot out-null är det inbyggda sättet att omdirigera pipeline-data till `$null` .

```powershell
New-Item -Type Directory -Path $path | Out-Null
```

### <a name="assign-to-null"></a>Tilldela till $null

Du kan tilldela resultatet av ett kommando för att `$null` få samma resultat som med `Out-Null` .

```powershell
$null = New-Item -Type Directory -Path $path
```

Eftersom `$null` är ett konstant värde kan du aldrig skriva över det. Jag vill inte att det ska se ut i koden, men det går ofta snabbare än `Out-Null` .

### <a name="redirect-to-null"></a>Omdirigera till $null

Du kan också använda operatorn för omdirigering för att skicka utdata till `$null` .

```powershell
New-Item -Type Directory -Path $path > $null
```

Om du hanterar körbara kommando rads program som utdata på olika strömmar. Du kan omdirigera alla utdata strömmar till så `$null` här:

```powershell
git status *> $null
```

## <a name="summary"></a>Sammanfattning

Jag har täckt en stor del av den här artikeln och jag vet att den här artikeln är mer fragmenterad än de flesta av mina djupgående dykningar. Det beror på att `$null` värden kan visas på många olika platser i PowerShell och alla olika delarna är bara de där du hittar det. Jag hoppas att du får en bättre förståelse för `$null` och en medvetenhet om de mer dolda scenarier som du kan köra i.

<!-- link references -->
[ursprunglig version]: https://powershellexplained.com/2018-12-23-Powershell-null-everything-you-wanted-to-know/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[lämpligt inlägg]: https://blog.iisreset.me/schrodingers-argumentlist
[PSScriptAnalyzer]: https://www.powershellgallery.com/packages/PSScriptAnalyzer
[System. Management. Automation. Internal. AutomationNull]: /dotnet/api/system.management.automation.internal.automationnull
