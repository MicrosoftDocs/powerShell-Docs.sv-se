---
title: Allt du ville veta om variabel ersättning i strängar
description: Det finns många sätt att använda variabler i strängar för att skapa formaterad text.
ms.date: 05/23/2020
ms.custom: contributor-KevinMarquette
ms.openlocfilehash: 1e65e90ffa09b34f62bc49ad64b062d429483c33
ms.sourcegitcommit: ed4a895d672334c7b02fb7ef6e950dbc2ba4a197
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/28/2020
ms.locfileid: "84149826"
---
# <a name="everything-you-wanted-to-know-about-variable-substitution-in-strings"></a>Allt du ville veta om variabel ersättning i strängar

Det finns många sätt att använda variabler i strängar. Jag anropar den här variabeln ersättningen men jag refererar till den tid som du vill formatera en sträng för att ta med värden från variabler. Det här är något som jag ofta upptäcker för nya skript.

> [!NOTE]
> Den [ursprungliga versionen][] av den här artikeln visas på bloggen som skrivits av [@KevinMarquette][] . PowerShell-teamet tackar för att dela det här innehållet med oss. Ta en titt på hans blogg på [PowerShellExplained.com][].

## <a name="concatenation"></a>Sammanlänkning

Den första klass metoden kan kallas för sammanfogning. Det är i princip att ta flera strängar och koppla ihop dem. Det finns en lång historik för att använda sammanfogning för att bygga formaterade strängar.

```powershell
$name = 'Kevin Marquette'
$message = 'Hello, ' + $name
```

Sammanfogningen fungerar OK när det bara finns några värden att lägga till. Men det kan enkelt bli krångligt.

```powershell
$first = 'Kevin'
$last = 'Marquette'
```

```powershell
$message = 'Hello, ' + $first + ' ' + $last + '.'
```

Det här enkla exemplet kan redan bli svårare att läsa.

## <a name="variable-substitution"></a>Variabel ersättning

PowerShell har ett annat alternativ som är enklare. Du kan ange variablerna direkt i strängarna.

```powershell
$message = "Hello, $first $last."
```

Den typ av offerter som du använder runt strängen är en skillnad. En dubbel citat tecken sträng tillåter ersättning men en sträng med citat tecken. Det finns flera gånger då du vill ha ett alternativ.

## <a name="command-substitution"></a>Kommando ersättning

Det får ingen aning när du börjar försöka hämta värdena för egenskaperna i en sträng. Det är här som många nya personer får utlöst. Börja med att visa dig vad de tror bör fungera (och värdet för ansikts värde nästan ser ut ungefär som det borde).

```powershell
$directory = Get-Item 'c:\windows'
$message = "Time: $directory.CreationTime"
```

Du förväntar dig att få `CreationTime` bort `$directory` , men i stället får du detta `Time: c:\windows.CreationTime` som värde. Orsaken är att den här typen av ersättning endast ser bas variabeln. Den tar perioden som en del av strängen, så att den slutar att lösa värdet djupare.

Det innebär bara att det här objektet ger en sträng som standardvärde när den placeras i en sträng.
Vissa objekt ger dig typ namnet i stället `System.Collections.Hashtable` . Bara något att titta efter.

Med PowerShell kan du utföra kommando körning inuti strängen med en speciell syntax. Detta gör att vi kan hämta egenskaperna för dessa objekt och köra andra kommandon för att få ett värde.

```powershell
$message = "Time: $($directory.CreationTime)"
```

Detta fungerar bra för vissa situationer, men det kan komma precis som galna som sammanfogning om du bara har några få variabler.

### <a name="command-execution"></a>Kommando körning

Du kan köra kommandon inuti en sträng. Trots att jag har det här alternativet, jag vill inte. Den får en snabb och svår fel sökning. Antingen kör du kommandot och sparar till en variabel eller använder en format sträng.

```powershell
$message = "Date: $(Get-Date)"
```

## <a name="format-string"></a>Format sträng

.NET har ett sätt att formatera strängar som jag tycker är ganska enkla att arbeta med. Låt oss först visa dig den statiska metoden för den innan jag visar PowerShell-genvägen för att göra samma sak.

```powershell
# .NET string format string
[string]::Format('Hello, {0} {1}.',$first,$last)

# PowerShell format string
'Hello, {0} {1}.' -f $first, $last
```

Vad som händer här är att strängen tolkas för token `{0}` och `{1}` sedan används den siffran för att välja från de angivna värdena. Om du vill upprepa ett visst värde på en viss plats i strängen kan du återanvända det värde numret.

Desto mer komplicerade strängen får, desto mer värde får du av den här metoden.

### <a name="format-values-as-arrays"></a>Formatera värden som matriser

Om din format rad är för lång kan du placera värdena i en matris först.

```powershell
$values = @(
    "Kevin"
    "Marquette"
)
'Hello, {0} {1}.' -f $values
```

Detta är inte ihopbuntning eftersom jag skickar hela matrisen i, men idén är liknande.

## <a name="advanced-formatting"></a>Avancerad formatering

Jag har avsiktligt anropat dessa från .NET eftersom det finns många formateringsalternativ som redan är väl [dokumenterade][] på det. Det finns inbyggda sätt att formatera olika data typer.

```powershell
"{0:yyyyMMdd}" -f (Get-Date)
"Population {0:N0}" -f  8175133
```

Jag kommer inte att gå till dem, men jag ville bara meddela att det här är en mycket kraftfull format motor om du behöver den.

## <a name="joining-strings"></a>Ansluta till strängar

Ibland vill du verkligen sammanfoga en lista med värden. Det finns en `-join` operatör som kan göra det åt dig. Det innebär även att du kan ange ett tangent att koppla mellan strängarna.

```powershell
$servers = @(
    'server1'
    'server2'
    'server3'
)

$servers  -join ','
```

Om du vill använda en `-join` del strängar utan avgränsare måste du ange en tom sträng `''` .
Men om det är allt du behöver finns det ett snabbare alternativ.

```powershell
[string]::Concat('server1','server2','server3')
[string]::Concat($servers)
```

Det är också värt att peka på att du även kan `-split` strängar.

## <a name="join-path"></a>Anslut till sökväg

Detta är ofta överblickat men en bra cmdlet för att skapa en fil Sök väg.

```powershell
$folder = 'Temp'
Join-Path -Path 'c:\windows' -ChildPath $folder
```

Det här är ett bra tips om att det fungerar som det ska när du placerar värdena tillsammans. Detta är särskilt viktigt om du tar värden från användare eller konfigurationsfiler.

Detta går också bra med `Split-Path` och `Test-Path` . Jag lägger också till dessa i mitt inlägg om [att läsa och spara filer][].

## <a name="strings-are-arrays"></a>Strängar är matriser

Jag behöver nämna att lägga till strängar här innan jag går vidare. Kom ihåg att en sträng bara är en matris med tecken. När du lägger till flera strängar tillsammans skapas en ny matris varje gång.

Titta på det här exemplet:

```powershell
$message = "Numbers: "
foreach($number in 1..10000)
{
    $message += " $number"
}
```

Det verkar mycket grundläggande men det som du inte ser är att varje gången en sträng läggs till i `$message` en ny sträng skapas. Minnet allokeras, data kopieras och det gamla det ignoreras.
Inte ett stort avtal när det bara är ett par gånger, men en slinga som detta skulle innebära problemet.

### <a name="stringbuilder"></a>StringBuilder

StringBuilder är också mycket populär för att skapa stora strängar från massor av mindre strängar. Orsaken till detta är att den bara samlar in alla strängar som du lägger till i den och bara sammanfogar alla dem i slutet när du hämtar värdet.

```powershell
$stringBuilder = New-Object -TypeName "System.Text.StringBuilder"

[void]$stringBuilder.Append("Numbers: ")
foreach($number in 1..10000)
{
    [void]$stringBuilder.Append(" $number")
}
$message = $stringBuilder.ToString()
```

Återigen är det något som jag når till .NET för. Jag använder det inte ofta längre, men det är bra att känna till det.

## <a name="delineation-with-braces"></a>Delinjärt med klammerparenteser

Detta används för kombination av suffix i strängen. Ibland har din variabel inte en ren ord-gränser.

```powershell
$test = "Bet"
$tester = "Better"
Write-Host "$test $tester ${test}ter"
```

Tack [/u/-real_parbold][] för det.

Här är ett alternativ till den här metoden:

```powershell
Write-Host "$test $tester $($test)ter"
Write-Host "{0} {1} {0}ter" -f $test, $tester
```

Jag använder en format sträng för det här, men det är en bättre idé att se om den finns i jokertecken.

## <a name="find-and-replace-tokens"></a>Sök och ersätt tokens

De flesta av de här funktionerna begränsar ditt behov av att återställa din egen lösning, men det finns tillfällen där du kan ha stora mallfiler där du vill ersätta strängar inuti.

Låt oss anta att du har hämtat en mall från en fil som har mycket text.

```powershell
$letter = Get-Content -Path TemplateLetter.txt -RAW
$letter = $letter -replace '#FULL_NAME#', 'Kevin Marquette'
```

Du kan ha många token som ska ersättas. Ditt Stick är att använda en mycket skild token som är lätt att hitta och ersätta. Jag brukar använda ett specialtecken i båda ändar för att hjälpa till att skilja det.

Jag har nyligen hittat ett nytt sätt att närma sig detta. Jag beslutade att lämna det här avsnittet här eftersom det är ett mönster som används ofta.

### <a name="replace-multiple-tokens"></a>Ersätt flera tokens

När jag har en lista över tokens som jag behöver ersätta, tar jag en mer allmän metod. Jag skulle placera dem i en hash-hash och iterera över dem för att ersätta dem.

```powershell
$tokenList = @{
    Full_Name = 'Kevin Marquette'
    Location = 'Orange County'
    State = 'CA'
}

$letter = Get-Content -Path TemplateLetter.txt -RAW
foreach( $token in $tokenList.GetEnumerator() )
{
    $pattern = '#{0}#' -f $token.key
    $letter = $letter -replace $pattern, $token.Value
}
```

Dessa token kan läsas in från JSON eller CSV om det behövs.

### <a name="executioncontext-expandstring"></a>ExecutionContext ExpandString

Det finns ett smarta sätt att definiera en ersättnings sträng med enkla citat tecken och expandera variablerna senare. Titta på det här exemplet:

```powershell
$message = 'Hello, $Name!'
$name = 'Kevin Marquette'
$string = $ExecutionContext.InvokeCommand.ExpandString($message)
```

Anropet till `.InvokeCommand.ExpandString` i den aktuella körnings kontexten använder variablerna i det aktuella omfånget för ersättning. Nyckeln här är att `$message` kan definieras tidigt innan variablerna blir kvar.

Om vi expanderar på bara en liten bit kan vi utföra denna ersättning över och över wih olika värden.

```powershell
$message = 'Hello, $Name!'
$nameList = 'Mark Kraus','Kevin Marquette','Lee Dailey'
foreach($name in $nameList){
    $ExecutionContext.InvokeCommand.ExpandString($message)
}
```

För att fortsätta med den här idén. Du kan importera en stor e-postmall från en textfil för att göra detta. Jag måste tacka [mark Kraus][] för det här [förslaget][].

## <a name="whatever-works-the-best-for-you"></a>Vad som fungerar bäst för dig

Jag är en fläkt i format Strängs metoden. Det gör du definitivt med de mer komplicerade strängarna eller om det finns flera variabler. På något som är mycket kort kan jag använda något av dessa.

## <a name="anything-else"></a>Något mer?

Jag har täckt mycket av grunden på det här. Mitt hoppas att du kan gå vidare med att lära dig något nytt.

<!-- link references -->
[ursprunglig version]: https://powershellexplained.com/2017-01-13-powershell-variable-substitution-in-strings/
[powershellexplained.com]: https://powershellexplained.com/
[@KevinMarquette]: https://twitter.com/KevinMarquette
[Markera Kraus]: https://get-powershellblog.blogspot.com/
[lämna]: https://www.reddit.com/r/PowerShell/comments/5npf8h/kevmar_everything_you_wanted_to_know_about/dcdfia5/
[/u/real_parbold]: https://www.reddit.com/r/PowerShell/comments/5npf8h/kevmar_everything_you_wanted_to_know_about/dcdfm6p/
[läsa och spara till filer]: https://powershellexplained.com/2017-03-18-Powershell-reading-and-saving-data-to-files/
[dokumenteras]: /dotnet/api/system.string.format#overloads
