---
description: Beskriver matriser, som är data strukturer som är utformade för att lagra samlings objekt.
Locale: en-US
ms.date: 08/26/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_arrays?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Arrays
ms.openlocfilehash: 2e7cf9c8f7d4e6f1d5bc66310f56d3de9461e592
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710693"
---
# <a name="about-arrays"></a>Om matriser

## <a name="short-description"></a>Kort beskrivning
Beskriver matriser, som är data strukturer som är utformade för att lagra samlings objekt.

## <a name="long-description"></a>Lång beskrivning

En matris är en data struktur som är utformad för att lagra en samling objekt.
Objekten kan vara av samma typ eller olika typer.

Från och med Windows PowerShell 3,0 har en samling med noll eller ett objekt vissa egenskaper för matriser.

## <a name="creating-and-initializing-an-array"></a>Skapa och initiera en matris

Om du vill skapa och initiera en matris tilldelar du flera värden till en variabel. Värdena som lagras i matrisen avgränsas med kommatecken och skiljs från variabelns namn av tilldelnings operatorn ( `=` ).

Om du till exempel vill skapa en matris med namnet `$A` som innehåller de sju numeriska (int) värdena 22, 5, 10, 8, 12, 9 och 80 skriver du:

```powershell
$A = 22,5,10,8,12,9,80
```

Kommatecken kan också användas för att initiera ett enskilt objekts mat ris genom att placera kommatecknet före det enskilda objektet.

Om du till exempel vill skapa en matris med ett enda objekt `$B` som innehåller det enskilda värdet 7 skriver du:

```powershell
$B = ,7
```

Du kan också skapa och initiera en matris med hjälp av intervall operatorn ( `..` ).
I följande exempel skapas en matris som innehåller värdena 5 till 8.

```powershell
$C = 5..8
```

Därför `$C` innehåller fyra värden: 5, 6, 7 och 8.

När ingen datatyp anges skapar PowerShell varje matris som en objekt mat ris (**system. Object []**). Om du vill fastställa data typen för en matris använder du **gettype ()** -metoden. Om du till exempel vill fastställa data typen för `$A` matrisen skriver du:

```powershell
$A.GetType()
```

För att skapa en starkt angiven matris, det vill säga en matris som bara kan innehålla värden av en viss typ, omvandla variabeln som en mat ris typ, till exempel **string []**, **lång []** eller **Int32 []**. Om du vill omvandla en matris måste du före variabel namnet med en mat ris typ inom hakparenteser. Om du till exempel vill skapa en 32-bitars heltals mat ris med namnet `$ia` som innehåller fyra heltal (1500, 2230, 3350 och 4000) skriver du:

```powershell
[int32[]]$ia = 1500,2230,3350,4000
```

Därför `$ia` kan matrisen bara innehålla heltal.

Du kan skapa matriser som har omvandlats till en typ som stöds i Microsoft .NET Framework. Till exempel är de objekt som `Get-Process` hämtar för att representera processer av typen **system. Diagnostics. process** . Ange följande kommando för att skapa en strikt skriven matris med process objekt:

```powershell
[Diagnostics.Process[]]$zz = Get-Process
```

## <a name="the-array-sub-expression-operator"></a>Operatorn för under uttryck för matris

Operatorn array-underuttryck skapar en matris från instruktionerna inuti den. Oavsett vilken instruktion som ingår i operatorn kommer operatorn att placera den i en matris. Även om det finns noll eller ett objekt.

Mat ris operatorns syntax är följande:

```syntax
@( ... )
```

Du kan använda array-operatorn för att skapa en matris med noll eller ett objekt. Exempel:

```powershell
$a = @("Hello World")
$a.Count
```

```Output
1
```

```powershell
$b = @()
$b.Count
```

```Output
0
```

Mat ris operatorn är användbar i skript när du hämtar objekt, men vet inte hur många objekt du får. Exempel:

```powershell
$p = @(Get-Process Notepad)
```

Mer information om operatorn array under uttryck finns [about_Operators](about_Operators.md).

## <a name="accessing-and-using-array-elements"></a>Komma åt och använda mat ris element

### <a name="reading-an-array"></a>Läser en matris

Du kan referera till en matris med hjälp av dess variabel namn. Om du vill visa alla element i matrisen skriver du mat ris namnet. Anta till exempel `$a` att en matris innehåller heltal som är 0, 1, 2 till och med 9; skriva:

```powershell
$a
```

```Output
0
1
2
3
4
5
6
7
8
9
```

Du kan referera till elementen i en matris med hjälp av ett index, med början vid position 0. Omge indexet med hakparenteser. Om du till exempel vill visa det första elementet i `$a` matrisen skriver du:

```powershell
$a[0]
```

```Output
0
```

Om du vill visa det tredje elementet i `$a` matrisen skriver du:

```powershell
$a[2]
```

```Output
2
```

Du kan hämta en del av matrisen med en intervall operator för indexet. Om du till exempel vill hämta det andra till femte element i matrisen skriver du:

```powershell
$a[1..4]
```

```Output
1
2
3
4
```

Antalet negativa tal från slutet av matrisen. Till exempel refererar "-1" till det sista elementet i matrisen. Om du vill visa de sista tre elementen i matrisen skriver du följande i index, stigande ordning:

```powershell
$a = 0 .. 9
$a[-3..-1]
```

```Output
7
8
9
```

Om du skriver negativa index i fallande ordning ändras utdata.

```powershell
$a = 0 .. 9
$a[-1..-3]
```

```Output
9
8
7
```

Men var försiktig när du använder den här notationen. Notationen går från slut kanten till början av matrisen.

```powershell
$a = 0 .. 9
$a[2..-2]
```

```Output
2
1
0
9
8
```

Ett vanligt misstag är att anta `$a[0..-2]` att avser alla element i matrisen, förutom den sista. Den refererar till de första, sista och andra-till-sista elementen i matrisen.

Du kan använda plus operatorn ( `+` ) för att kombinera ett intervall med en lista med element i en matris. Om du till exempel vill visa elementen vid index positionerna 0, 2 och 4 till 6, skriver du:

```powershell
$a = 0 .. 9
$a[0,2+4..6]
```

```Output
0
2
4
5
6
```

För att visa flera områden och enskilda element kan du också använda plus-operatorn. Om du till exempel vill lista elementen noll till två, fyra till sex och elementet med åttonde positions typ:

```powershell
$a = 0..9
$a[+0..2+4..6+8]
```

```Output
0
1
2
4
5
6
8
```

### <a name="iterations-over-array-elements"></a>Iterationer över mat ris element

Du kan också använda loop-konstruktioner, t. ex., och while-slingor för att referera till elementen i en matris. Om du till exempel vill använda en förgrunds slinga för att Visa elementen i `$a` matrisen skriver du:

```powershell
$a = 0..9
foreach ($element in $a) {
  $element
}
```

```Output
0
1
2
3
4
5
6
7
8
9
```

Förgrunds-loopen upprepas genom matrisen och returnerar varje värde i matrisen tills den når slutet av matrisen.

For-slingan är användbar när du ökar räknare och undersöker elementen i en matris. Om du till exempel vill använda en for-slinga för att returnera varannan värde i en matris, skriver du:

```powershell
$a = 0..9
for ($i = 0; $i -le ($a.length - 1); $i += 2) {
  $a[$i]
}
```

```Output
0
2
4
6
8
```

Du kan använda en while-slinga för att visa element i en matris tills ett definierat villkor inte längre är sant. Om du till exempel vill visa elementen i `$a` matrisen medan mat ris indexet är mindre än 4 skriver du:

```powershell
$a = 0..9
$i=0
while($i -lt 4) {
  $a[$i];
  $i++
}
```

```Output
0
1
2
3
```

## <a name="properties-of-arrays"></a>Egenskaper för matriser

### <a name="count-or-length-or-longlength"></a>Antal eller längd eller LongLength

Om du vill ta reda på hur många objekt som finns i en matris använder du `Length` egenskapen eller dess `Count` alias. `Longlength` är användbart om matrisen innehåller fler än 2 147 483 647 element.

```powershell
$a = 0..9
$a.Count
$a.Length
```

```Output
10
10
```

### <a name="rank"></a>Rangordning

Returnerar antalet dimensioner i matrisen. De flesta matriser i PowerShell har en dimension. Även om du tror att du bygger en flerdimensionell matris. som i följande exempel:

```powershell
$a = @(
  @(0,1),
  @("b", "c"),
  @(Get-Process)
)

[int]$r = $a.Rank
"`$a rank: $r"
```

```Output
$a rank: 1
```

I följande exempel visas hur du skapar en faktiskt flerdimensionell matris med .NET Framework.

```powershell
[int[,]]$rank2 = [int[,]]::new(5,5)
$rank2.rank
```

```Output
2
```

## <a name="methods-of-arrays"></a>Metoder för matriser

### <a name="clear"></a>Rensa

Anger alla element värden till _standardvärdet_ för matrisens element typ.
Metoden clear () återställer inte storleken på matrisen.

I följande exempel `$a` är en matris med objekt.

```powershell
$a = 1, 2, 3
$a.Clear()
$a | % { $null -eq $_ }
```

```Output
True
True
True
```

I det här exemplet har `$intA` explicit angetts som innehåller heltal.

```powershell
[int[]] $intA = 1, 2, 3
$intA.Clear()
$intA
```

```Output
0
0
0
```

### <a name="foreach"></a>ForEach

Gör det möjligt att iterera över alla element i matrisen och utföra en specifik åtgärd för varje element i matrisen.

Den förgrunds metoden har flera överlagringar som utför olika åtgärder.

```
ForEach(scriptblock expression)
ForEach(scriptblock expression, object[] arguments)
ForEach(type convertToType)
ForEach(string propertyName)
ForEach(string propertyName, object[] newValue)
ForEach(string methodName)
ForEach(string methodName, object[] arguments)
```

#### <a name="foreachscriptblock-expression"></a>Solredovisning (script block-uttryck)

#### <a name="foreachscriptblock-expression-object-arguments"></a>(Script block-uttryck, objekt [] argument)

Den här metoden har lagts till i PowerShell v4.

> [!NOTE]
> Syntaxen kräver att ett skript block används. Parenteser är valfria om script block är den enda parametern. Det får inte finnas något blank steg mellan metoden och den inledande parentesen eller klammerparentesen.

I följande exempel visas hur du använder den förgrunds metoden. I det här fallet är avsikten att generera det fyrkantiga värdet för elementen i matrisen.

```powershell
$a = @(0 .. 3)
$a.ForEach({ $_ * $_})
```

```Output
0
1
4
9
```

Precis som `-ArgumentList` parametern för `ForEach-Object` , `arguments` tillåter parametern att en matris med argument skickas till ett skript block som kon figurer ATS för att godkänna dem.

Mer information om beteendet för **argument List** finns [about_Splatting](about_Splatting.md#splatting-with-arrays).

#### <a name="foreachtype-converttotype"></a>(Typ convertToType)

`ForEach`Metoden kan användas för att snabbt omvandla elementen till en annan typ. i följande exempel visas hur du konverterar en lista med sträng datum som ska `[DateTime]` skrivas.

```powershell
@("1/1/2017", "2/1/2017", "3/1/2017").ForEach([datetime])
```

```Output

Sunday, January 1, 2017 12:00:00 AM
Wednesday, February 1, 2017 12:00:00 AM
Wednesday, March 1, 2017 12:00:00 AM
```

#### <a name="foreachstring-propertyname"></a>(String propertyName)

#### <a name="foreachstring-propertyname-object-newvalue"></a>(String propertyName, objekt [] newValue)

`ForEach`Metoden kan också användas för att snabbt hämta eller ange egenskaps värden för varje objekt i samlingen.

```powershell
# Set all LastAccessTime properties of files to the current date.
(dir 'C:\Temp').ForEach('LastAccessTime', (Get-Date))
# View the newly set LastAccessTime of all items, and find Unique entries.
(dir 'C:\Temp').ForEach('LastAccessTime') | Get-Unique
```

```Output
Wednesday, June 20, 2018 9:21:57 AM
```

#### <a name="foreachstring-methodname"></a>(Sträng methodName)

#### <a name="foreachstring-methodname-object-arguments"></a>Sol(sträng methodName, objekt [] argument)

Slutligen `ForEach` kan metoder användas för att köra en metod på alla objekt i samlingen.

```powershell
("one", "two", "three").ForEach("ToUpper")
```

```Output
ONE
TWO
THREE
```

Precis som `-ArgumentList` parametern för `ForEach-Object` , `arguments` tillåter parametern att en matris med argument skickas till ett skript block som kon figurer ATS för att godkänna dem.

> [!NOTE]
> Från och med Windows PowerShell 3,0 att hämta egenskaper och köra metoder för varje objekt i en samling kan också utföras med hjälp av "metoder för skalära objekt och samlingar" du kan läsa mer om det här [about_Methods](about_methods.md).

### <a name="where"></a>Var

Tillåter att filtrera eller välja element i matrisen. Skriptet måste utvärderas till något annat än: noll (0), tom sträng `$false` eller `$null` element som ska visas efter `Where`

Det finns en definition för `Where` metoden.

```
Where(scriptblock expression[, WhereOperatorSelectionMode mode
                            [, int numberToReturn]])
```

> [!NOTE]
> Syntaxen kräver att ett skript block används. Parenteser är valfria om script block är den enda parametern. Det får inte finnas något blank steg mellan metoden och den inledande parentesen eller klammerparentesen.

`Expression`Är script block som krävs för filtrering, det `mode` valfria argumentet tillåter ytterligare markerings funktioner och det `numberToReturn` valfria argumentet ger möjlighet att begränsa hur många objekt som returneras från filtret.

Godkända värden för `mode` är:

- Standard (0) – returnera alla objekt
- Första (1) – returnera det första objektet
- Senaste (2) – returnera det sista objektet
- SkipUntil (3) – hoppa över objekt tills villkoret är sant, returnera återstående objekt
- Till (4) – returnera alla objekt tills villkoret är sant
- Split (5) – returnera en matris med två element
  - Det första elementet innehåller matchande objekt
  - Det andra elementet innehåller återstående objekt

I följande exempel visas hur du markerar alla udda tal från matrisen.

```powershell
(0..9).Where{ $_ % 2 }
```

```Output
1
3
5
7
9
```

Det här exemplet visar hur du väljer de strängar som inte är tomma.

```powershell
('hi', '', 'there').Where({$_.Length})
```

```Output
hi
there
```

#### <a name="default"></a>Standardvärde

`Default`Läget filtrerar objekt med hjälp av `Expression` script block.

Om en anges anges det `numberToReturn` maximala antalet objekt som ska returneras.

```powershell
# Get the zip files in the current users profile, sorted by LastAccessTime.
$Zips = dir $env:userprofile -Recurse '*.zip' | Sort-Object LastAccessTime
# Get the least accessed file over 100MB
$Zips.Where({$_.Length -gt 100MB}, 'Default', 1)
```

> [!NOTE]
> Både `Default` läge och `First` läge returnerar de första ( `numberToReturn` ) objekten och kan användas utbytbart.

#### <a name="last"></a>Sista

```powershell
$h = (Get-Date).AddHours(-1)
$logs = dir 'C:\' -Recurse '*.log' | Sort-Object CreationTime
# Find the last 5 log files created in the past hour.
$logs.Where({$_.CreationTime -gt $h}, 'Last', 5)
```

#### <a name="skipuntil"></a>SkipUntil

`SkipUntil`Läget hoppar över alla objekt i en samling tills ett objekt klarar filtret för skript block uttryck. Den returnerar sedan **alla** återstående samlings objekt utan att testa dem. _Endast ett överförings objekt testas_.

Det innebär att den returnerade samlingen innehåller både _överförda_ och _icke-godkända_ objekt som inte har testats.

Antalet returnerade objekt kan begränsas genom att ett värde skickas till `numberToReturn` argumentet.

```powershell
$computers = "Server01", "Server02", "Server03", "localhost", "Server04"
# Find the first available online server.
$computers.Where({ Test-Connection $_ }, 'SkipUntil', 1)
```

```Output
localhost
```

#### <a name="until"></a>Tills

`Until`Läget inverterar `SkipUntil` läget.  Den returnerar **alla** objekt i en samling tills ett objekt skickar skript Blocks uttrycket. När ett objekt _passerar_ script block-uttrycket `Where` slutar metoden att bearbeta objekt.

Det innebär att du får den första uppsättningen _icke-överförda_ objekt från- `Where` metoden. _När_ ett objekt har passerat testas inte resten eller returneras.

Antalet returnerade objekt kan begränsas genom att ett värde skickas till `numberToReturn` argumentet.

```powershell
# Retrieve the first set of numbers less than or equal to 10.
(1..50).Where({$_ -gt 10}, 'Until')
# This would perform the same operation.
(1..50).Where({$_ -le 10})
```

```Output
1
2
3
4
5
6
7
8
9
10
```

> [!NOTE]
> Både `Until` och används `SkipUntil` under den plats där ingen grupp objekt testas.
>
> `Until` Returnerar objekten **före** det första _passet_.
>
> `SkipUntil` returnerar alla objekt **efter** det första steget, inklusive det första _passet_.

#### <a name="split"></a>Dela

`Split`Läget delas eller grupperar samlings objekt i två separata samlingar. De som skickar script block-uttrycket och de som inte gör det.

Om en `numberToReturn` har angetts innehåller den första samlingen de _överförda_ objekten, inte större än det angivna värdet.

Återstående objekt, även de som **skickar** uttrycks filtret, returneras i den andra samlingen.

```powershell
$running, $stopped = (Get-Service).Where({$_.Status -eq 'Running'}, 'Split')
$running
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  Appinfo            Application Information
Running  AudioEndpointBu... Windows Audio Endpoint Builder
Running  Audiosrv           Windows Audio
...
```

```powershell
$stopped
```

```Output
Status   Name               DisplayName
------   ----               -----------
Stopped  AJRouter           AllJoyn Router Service
Stopped  ALG                Application Layer Gateway Service
Stopped  AppIDSvc           Application Identity
...
```

## <a name="get-the-members-of-an-array"></a>Hämta medlemmarna i en matris

Om du vill hämta egenskaper och metoder för en matris, till exempel egenskapen längd och metoden **SetValue** , använder du parametern **InputObject** för `Get-Member` cmdleten.

När du skickar en matris till `Get-Member` skickar PowerShell objekten en i taget och `Get-Member` returnerar typen för varje objekt i matrisen (ignorerar dubbletter).

När du använder parametern **InputObject** `Get-Member` returneras medlemmarna i matrisen.

Följande kommando hämtar till exempel medlemmarna i `$a` mat ris variabeln.

```powershell
Get-Member -InputObject $a
```

Du kan också hämta medlemmarna i en matris genom att skriva ett kommatecken (,) före det värde som är skickas till `Get-Member` cmdleten. Kommatecknet gör matrisen till det andra objektet i en matris med matriser. PowerShell flyttar matriserna en i taget och `Get-Member` returnerar medlemmarna i matrisen. Precis som i de följande två exemplen.

```powershell
,$a | Get-Member

,(1,2,3) | Get-Member
```

## <a name="manipulating-an-array"></a>Ändra en matris

Du kan ändra elementen i en matris, lägga till ett element i en matris och kombinera värdena från två matriser till en tredje matris.

Om du vill ändra värdet för ett visst element i en matris anger du mat ris namnet och indexet för det element som du vill ändra och använder sedan tilldelnings operatorn ( `=` ) för att ange ett nytt värde för elementet. Om du till exempel vill ändra värdet för det andra objektet i `$a` matrisen (index position 1) till 10, skriver du:

```powershell
$a[1] = 10
```

Du kan också använda metoden **SetValue** i en matris för att ändra ett värde. I följande exempel ändras det andra värdet (index position 1) för `$a` matrisen till 500:

```powershell
$a.SetValue(500,1)
```

Du kan använda `+=` operatorn för att lägga till ett element i en matris. I följande exempel visas hur du lägger till ett-element i `$a` matrisen.

```powershell
$a = @(0..4)
$a += 5
```

> [!NOTE]
> När du använder `+=` operatorn skapar PowerShell faktiskt en ny matris med värdena för den ursprungliga matrisen och det tillagda värdet. Detta kan orsaka prestanda problem om åtgärden upprepas flera gånger eller om storleken på matrisen är för stor.

Det är inte enkelt att ta bort element från en matris, men du kan skapa en ny matris som bara innehåller valda element i en befintlig matris. Om du till exempel vill skapa `$t` matrisen med alla element i `$a` matrisen, förutom värdet vid index position 2, skriver du:

```powershell
$t = $a[0,1 + 3..($a.length - 1)]
```

Om du vill kombinera två matriser i en enda matris använder du plus operatorn ( `+` ). I följande exempel skapas två matriser, kombinerar dem och sedan visas den resulterande kombinerade matrisen.

```powershell
$x = 1,3
$y = 5,9
$z = $x + $y
```

Därför `$z` innehåller matrisen 1, 3, 5 och 9.

Om du vill ta bort en matris tilldelar `$null` du värdet till matrisen. Följande kommando tar bort matrisen i `$a` variabeln.

`$a = $null`

Du kan också använda `Remove-Item` cmdleten, men tilldelning av värdet `$null` är snabbare, särskilt för stora matriser.

## <a name="arrays-of-zero-or-one"></a>Matriser med noll eller ett

Från och med Windows PowerShell 3,0 har en samling med noll eller ett objekt värdet count och length. Du kan också indexera i en matris med ett objekt. Den här funktionen hjälper dig att undvika skript fel som uppstår när ett kommando som förväntar en samling får färre än två objekt.

I följande exempel demonstreras den här funktionen.

### <a name="zero-objects"></a>Noll objekt

```powershell
$a = $null
$a.Count
$a.Length
```

```Output
0
0
```

### <a name="one-object"></a>Ett objekt

```powershell
$a = 4
$a.Count
$a.Length
$a[0]
$a[-1]
```

```Output
1
1
4
4
```

## <a name="indexing-support-for-systemtuple-objects"></a>Indexerings stöd för system. tuple-objekt

PowerShell 6,1 har lagt till stöd för indexerad åtkomst till **tuple** -objekt, ungefär som matriser.
Exempel:

```powershell
PS> $tuple = [Tuple]::Create(1, 'test')
PS> $tuple[0]
1
PS> $tuple[1]
test
PS> $tuple[0..1]
1
test
PS> $tuple[-1]
test
```

Till skillnad från matriser och andra samlings objekt behandlas **tuple** -objekt som ett enda objekt när de skickas genom pipelinen eller med parametrar som stöder matriser med objekt.

Mer information finns i [system. tuple](/dotnet/api/system.tuple).

## <a name="see-also"></a>Se även

- [about_Assignment_Operators](about_Assignment_Operators.md)
- [about_Hash_Tables](about_Hash_Tables.md)
- [about_Operators](about_Operators.md)
- [about_For](about_For.md)
- [about_Foreach](about_Foreach.md)
- [about_While](about_While.md)

