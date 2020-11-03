---
description: Beskriver de operatorer som utför aritmetiska i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_arithmetic_operators?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Arithmetic_Operators
ms.openlocfilehash: 3ece7464198ff52fe6c22ccc54ceede84288bd7b
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270237"
---
# <a name="about-arithmetic-operators"></a>Om aritmetiska operatorer

## <a name="short-description"></a>KORT BESKRIVNING
Beskriver de operatorer som utför aritmetiska i PowerShell.

## <a name="long-description"></a>LÅNG BESKRIVNING

Aritmetiska operatorer beräknar numeriska värden. Du kan använda en eller flera aritmetiska operatorer för att lägga till, subtrahera, multiplicera och dividera värden och för att beräkna resten (Modulus) av en divisions åtgärd.

Dessutom körs operatorn addition ( `+` ) och multiplikation ( `*` ) även på strängar, matriser och hash-tabeller. Operatorn addition sammanfogar indatamängden. Operatorn multiplikation returnerar flera kopior av indatamängden. Du kan till och med blanda objekt typer i en aritmetisk instruktion. Metoden som används för att utvärdera uttrycket bestäms av typen för objektet längst till vänster i uttrycket.

Från och med PowerShell 2,0 fungerar alla aritmetiska operatorer på 64-bitars nummer.

Från och med PowerShell 3,0 `-shr` läggs (Shift-höger) och `-shl` (Shift-Left) till som stöd för bitvisa aritmetiska i PowerShell.

PowerShell stöder följande aritmetiska operatorer:

|Operator|Beskrivning                       |Exempel                      |
|--------|----------------------------------|-----------------------------|
| +      |Lägger till heltal; sammanfogar       |`6 + 2`                      |
|        |strängar, matriser och hash-tabeller. |`"file" + "name"`            |
|        |                                  |`@(1, "one") + @(2.0, "two")`|
|        |                                  |`@{"one" = 1} + @{"two" = 2}`|
| -      |Subtraherar ett värde från ett annat  |`6 - 2`                      |
|        |värde                             |                             |
| -      |Gör ett tal till ett negativt tal  |`-6`                         |
|        |                                  |`(Get-Date).AddDays(-1)`     |
| *      |Multiplicera tal eller kopiera strängar  |`6 * 2`                      |
|        |och matriser det angivna talet   |`@("!") * 4`                 |
|        |av gånger.                         |`"!" * 3`                    |
| /      |Dividerar två värden.               |`6 / 2`                      |
| %      |Modulus-returnerar resten av|`7 % 2`                      |
|        |en divisions åtgärd.             |                             |
|-band   |Bitvis och                       |`5 -band 3`                  |
|-bnot   |Bitvis NOT                       |`-bnot 5`                    |
|– bor    |Bitvis eller                        |`5 -bor 0x03`                |
|-bxor   |Bitvis XOR                       |`5 -bxor 3`                  |
|-shl    |Flyttar bitar till vänster           |`102 -shl 2`                 |
|-shr    |Flyttar bitar till höger          |`102 -shr 2`                 |

De bitvisa operatorerna fungerar bara på heltals typer.

## <a name="operator-precedence"></a>PRIORITET FÖR OPERATOR

PowerShell bearbetar aritmetiska operatorer i följande ordning:

|Prioritet|Operator          |Beskrivning                            |
|----------|------------------|---------------------------------------|
|1         | `()`             |Parentes                            |
|2         | `-`              |För en negativ siffra eller enställig operator|
|3         | `*`, `/`, `%`    |För multiplikation och division        |
|4         | `+`, `-`         |För addition och subtraktion           |
|5         | `-band`, `-bnot` |För bitvisa åtgärder                 |
|5         | `-bor`, `-bxor`  |För bitvisa åtgärder                 |
|5         | `-shr`, `-shl`   |För bitvisa åtgärder                 |

PowerShell bearbetar uttrycken från vänster till höger enligt prioritets reglerna. I följande exempel visas resultatet av prioritets reglerna:

|Uttryck |Resultat|
|-----------|------|
|`3+6/3*4`  |`11`  |
|`3+6/(3*4)`|`3.5` |
|`(3+6)/3*4`|`12`  |

Den ordning i vilken PowerShell utvärderar uttryck kan skilja sig från andra programmerings-och skript språk som du har använt. I följande exempel visas en komplicerad tilldelnings instruktion.

```powershell
$a = 0
$b = @(1,2)
$c = @(-1,-2)

$b[$a] = $c[$a++]
```

I det här exemplet `$a++` utvärderas uttrycket före `$b[$a]` .
Utvärdering av `$a++` ändringar av värdet `$a` efter det används i instruktionen, `$c[$a++]` men innan det används i `$b[$a]` . Variabeln `$a` i `$b[$a]` är lika med `1` , `0` så tilldelar instruktionen ett värde till `$b[1]` , inte `$b[0]` .

Ovanstående kod motsvarar:

```powershell
$a = 0
$b = @(1,2)
$c = @(-1,-2)

$tmp = $c[$a]
$a = $a + 1
$b[$a] = $tmp
```

## <a name="division-and-rounding"></a>DIVISION OCH AVRUNDNING

När kvoten för en divisions åtgärd är ett heltal, avrundar PowerShell värdet till närmaste heltal. När värdet är `.5` , avrundas det till närmaste jämna heltal.

I följande exempel visas effekterna av avrundning till närmaste jämna heltal.

|Uttryck      |Resultat|
|----------------|------|
|`[int]( 5 / 2 )`|`2`   |
|`[int]( 7 / 2 )`|`4`   |

Observera hur **_5/2_ = 2,5** rundas av till **2**. Men **_7/2_ = 3,5** rundas av till **4**.

Du kan använda- `[Math]` klassen för att få olika avrundnings sätt.

|                          Uttryck                          | Resultat |
| ------------------------------------------------------------ | ------ |
| `[int][Math]::Round(5 / 2,[MidpointRounding]::AwayFromZero)` | `3`    |
| `[int][Math]::Ceiling(5 / 2)`                                | `3`    |
| `[int][Math]::Floor(5 / 2)`                                  | `2`    |

Mer information finns i metoden [Math. Round](/dotnet/api/system.math.round) .

## <a name="adding-and-multiplying-non-numeric-types"></a>LÄGGA TILL OCH MULTIPLICERA ICKE-NUMERISKA TYPER

Du kan lägga till siffror, strängar, matriser och hash-tabeller. Du kan också multiplicera siffror, strängar och matriser. Du kan dock inte multiplicera hash-tabeller.

När du lägger till strängar, matriser eller hash-tabeller sammanfogas elementen. När du sammanfogar samlingar, till exempel matriser eller hash-tabeller, skapas ett nytt objekt som innehåller objekten från båda samlingarna. Om du försöker sammanfoga hash-tabeller som har samma nyckel, Miss lyckas åtgärden.

Följande kommandon skapar till exempel två matriser och lägger till dem:

```powershell
$a = 1,2,3
$b = "A","B","C"
$a + $b
```

```output
1
2
3
A
B
C
```

Du kan också utföra aritmetiska åtgärder på objekt av olika typer.
Den åtgärd som PowerShell utför bestäms av Microsoft .NET Framework-typen för objektet längst till vänster i åtgärden. PowerShell försöker konvertera alla objekt i åtgärden till den .NET Framework typen för det första objektet. Om det lyckas med att konvertera objekten utför den åtgärden som är lämplig för den .NET Framework typen för det första objektet. Åtgärden Miss lyckas om det inte går att konvertera något av objekten.

I följande exempel demonstreras användningen av operatorerna addition och multiplikation. i åtgärder som innehåller olika objekt typer. Antag `$array = 1,2,3` :

|Uttryck       |Resultat                 |
|-----------------|-----------------------|
|`"file" + 16`    |`file16`               |
|`$array + 16`    |`1`,`2`,`3`,`16`       |
|`$array + "file"`|`1`,`2`,`3`,`file`     |
|`$array * 2`     |`1`,`2`,`3`,`1`,`2`,`3`|
|`"file" * 3`     |`filefilefile`         |

Eftersom metoden som används för att utvärdera instruktioner bestäms av objektet längst till vänster, är addition och multiplikation i PowerShell inte strikt commutative. Till exempel är `(a + b)` inte alltid lika med `(b + a)` , och `(ab)` är inte alltid lika med `(ba)` .

Följande exempel visar den här principen:

|Uttryck   |Resultat                                               |
|-------------|-----------------------------------------------------|
|`"file" + 16`|`file16`                                             |
|`16 + "file"`|`Cannot convert value "file" to type "System.Int32".`|
|             |`Error: "Input string was not in a correct format."` |
|             |`At line:1 char:1`                                   |
|             |+ 16 + "fil" "                                       |

Hash-tabeller skiljer sig något från versaler. Du kan lägga till hash-tabeller i en annan hash-tabell, så länge som de tillagda hash-tabellerna inte har dubbla nycklar.

I följande exempel visas hur du lägger till hash-tabeller till varandra.

```powershell
$hash1 = @{a=1; b=2; c=3}
$hash2 = @{c1="Server01"; c2="Server02"}
$hash1 + $hash2
```

```output
Name                           Value
----                           -----
c2                             Server02
a                              1
b                              2
c1                             Server01
c                              3
```

I följande exempel utlöses ett fel eftersom en av nycklarna dupliceras i båda hash-tabellerna.

```powershell
$hash1 = @{a=1; b=2; c=3}
$hash2 = @{c1="Server01"; c="Server02"}
$hash1 + $hash2
```

```output
Item has already been added. Key in dictionary: 'c'  Key being added: 'c'
At line:3 char:1
+ $hash1 + $hash2
+ ~~~~~~~~~~~~~~~
    + CategoryInfo          : OperationStopped: (:) [], ArgumentException
    + FullyQualifiedErrorId : System.ArgumentException
```

Du kan också lägga till en hash-tabell i en matris. Dessutom blir hela hash-tabellen ett objekt i matrisen.

```powershell
$array1 = @(0, "Hello World", [datetime]::Now)
$hash1 = @{a=1; b=2}
$array2 = $array1 + $hash1
$array2
```

```output
0
Hello World

Monday, June 12, 2017 3:05:46 PM

Key   : a
Value : 1
Name  : a

Key   : b
Value : 2
Name  : b
```

Du kan dock inte lägga till någon annan typ i en hash-tabell.

```powershell
$hash1 + 2
```

```output
A hash table can only be added to another hash table.
At line:3 char:1
+ $hash1 + 2
```

Även om addition-operatörerna är mycket användbara använder du tilldelnings operatörerna för att lägga till element i hash-tabeller och matriser. Mer information finns i [about_assignment_operators](about_Assignment_Operators.md). I följande exempel används `+=` tilldelnings operatorn för att lägga till objekt i en matris:

```powershell
$array = @()
(0..9).foreach{ $array += $_ }
$array
```

```output
0
1
2
```

## <a name="type-conversion-to-accommodate-result"></a>SKRIV KONVERTERING FÖR ATT HANTERA RESULTATET

PowerShell väljer automatiskt den .NET Framework numeriska typ som bäst uttrycker resultatet utan att förlora precisionen. Ett exempel:

```powershell
2 + 3.1

(2). GetType().FullName
(2 + 3.1).GetType().FullName
```

```output
5.1
System.Int32
System.Double
```

Om resultatet av en åtgärd är för stort för typen, utvidgas typen av resultat för att hantera resultatet, som i följande exempel:

```powershell
(512MB).GetType().FullName
(512MB * 512MB).GetType().FullName
```

```output
System.Int32
System.Double
```

Resultat typen behöver inte nödvändigt vis vara samma som en av operanderna. I följande exempel kan det negativa värdet inte omvandlas till ett osignerat heltal, och det osignerade heltalet är för stort för att kunna omvandlas till `Int32` :

```powershell
([int32]::minvalue + [uint32]::maxvalue).gettype().fullname
```

```output
System.Int64
```

I det här exemplet `Int64` kan hantera båda typerna.

`System.Decimal`Typen är ett undantag. Om någon av operanderna har decimal typen, blir resultatet av decimal typen. Om resultatet är för stort för decimal typen, kommer det inte att omvandlas till Double. I stället ett fel resultat.

|Uttryck               |Resultat                                         |
|-------------------------|-----------------------------------------------|
|`[Decimal]::maxvalue`    |`79228162514264337593543950335`                |
|`[Decimal]::maxvalue + 1`|`Value was either too large or too small for a`|
|                         |`Decimal.`                                     |

## <a name="arithmetic-operators-and-variables"></a>ARITMETISKA OPERATORER OCH VARIABLER

Du kan också använda aritmetiska operatorer med variabler. Operatorerna fungerar på Variablernas värden. I följande exempel demonstreras användningen av aritmetiska operatorer med variabler:

| Uttryck                                    |Resultat      |
|-----------------------------------------------|------------|
|`$intA = 6`<br/>`$intB = 4`<br/>`$intA + $intB`|`10`        |
|`$a = "Power"`<br/>`$b = "Shell"`<br/>`$a + $b`|`PowerShell`|

## <a name="arithmetic-operators-and-commands"></a>ARITMETISKA OPERATORER OCH KOMMANDON

Normalt använder du aritmetiska operatorer i uttryck med siffror, strängar och matriser. Du kan dock också använda aritmetiska operatorer med de objekt som kommandona returnerar och med egenskaperna för dessa objekt.

I följande exempel visas hur du använder de aritmetiska operatorerna i uttryck med PowerShell-kommandon:

```powershell
(get-date) + (new-timespan -day 1)
```

Parentes operatorn tvingar fram utvärderingen av `get-date` cmdleten och utvärderingen av `new-timespan -day 1` cmdlet-uttrycket i den ordningen. Båda resultaten läggs sedan till med `+` operatorn.

```powershell
Get-Process | Where-Object { ($_.ws * 2) -gt 50mb }
```

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1896      39    50968      30620   264 1,572.55   1104 explorer
  12802      78   188468      81032   753 3,676.39   5676 OUTLOOK
    660       9    36168      26956   143    12.20    988 PowerShell
    561      14     6592      28144   110 1,010.09    496 services
   3476      80    34664      26092   234 ...45.69    876 svchost
    967      30    58804      59496   416   930.97   2508 WINWORD
```

I uttrycket ovan multipliceras varje process arbets utrymme ( `$_.ws` ) av `2` och resultatet jämförs med `50mb` för att se om det är större än.

## <a name="bitwise-operators"></a>Bitvisa operatorer

PowerShell stöder bitvisa standardoperatorer, inklusive bitvis-AND ( `-bAnd` ), inkluderings-och Exclusive-eller operatorerna ( `-bOr` och `-bXor` ) och bitvis-not ( `-bNot` ).

Från och med PowerShell 2,0 fungerar alla bitvisa operatorer med 64-bitars heltal.

Från och med PowerShell 3,0 `-shr` introduceras (Shift-höger) och `-shl` (Shift-Left) för att stödja bitvisa beräkningar i PowerShell.

PowerShell stöder följande bitvisa operatorer.

| Operator | Beskrivning            | Uttryck   | Resultat |
| -------- | ---------------------- | ------------ | ------ |
| `-band`  | Bitvis och            | `10 -band 3` | 2      |
| `-bor`   | Bitvis eller (inklusiv) | `10 -bor 3`  | 11     |
| `-bxor`  | Bitvis eller (exklusiv) | `10 -bxor 3` | 9      |
| `-bnot`  | Bitvis NOT            | `-bNot 10`   | -11    |
| `-shl`   | Shift-vänster             | `102 -shl 2` | 408    |
| `-shr`   | Shift-höger            | `102 -shr 1` | 51     |

Bitvisa operatorer fungerar som ett värde i binärformat. Bit strukturen för nummer 10 är till exempel 00001010 (baserat på 1 byte) och bit strukturen för talet 3 är 00000011. När du använder en bitvis operator för att jämföra 10 och 3 jämförs de enskilda bitarna i varje byte.

I en bitvis och-åtgärd anges den resulterande biten till 1 endast när båda indataportarna är 1.

```
1010      (10)
0011      ( 3)
--------------  bAND
0010      ( 2)
```

I en bitvis eller (inklusiv) åtgärd anges den resulterande biten till 1 när antingen eller båda indataportarna är 1. Den resulterande biten anges till 0 endast när båda indataportarna anges till 0.

```
1010      (10)
0011      ( 3)
--------------  bOR (inclusive)
1011      (11)
```

I en bitvis eller (exklusiv) åtgärd anges den resulterande biten till 1 endast när en indataport är 1.

```
1010      (10)
0011      ( 3)
--------------  bXOR (exclusive)
1001      ( 9)
```

Den bitvis NOT-operatorn är en unär operator som producerar det binära komplettering svärdet. Bit-bit 1 är inställd på 0 och biten 0 har värdet 1.

Till exempel binära komplementet 0 är-1, det maximala osignerade heltalet (0xFFFFFFFF) och det binära komplementet på-1 är 0.

```powershell
-bNot 10
```

```Output
-11
```

```
0000 0000 0000 1010  (10)
------------------------- bNOT
1111 1111 1111 0101  (-11, xfffffff5)
```

I en bitvis Shift-Left-åtgärd flyttas alla bitar "n" dit till vänster, där "n" är värdet för den högra operanden. En nolla infogas på den plats där de finns.

När den vänstra operanden är ett heltals värde (32-bitars) avgör de nedre 5 bitarna i den högra operanden hur många bitar av den vänstra operanden som flyttas.

När den vänstra operanden är ett Long (64-bitars) värde, bestämmer de nedre 6 bitarna i den högra operanden hur många bitar av den vänstra operanden som flyttas.

|Uttryck |Resultat|Binära resultat|
|-----------|------|-------------|
|`21 -shl 0`|21    |0001 0101    |
|`21 -shl 1`|42    |0010 1010    |
|`21 -shl 2`|84    |0101 0100    |

I en bitvis Shift-höger-åtgärd flyttas alla bitar "n" åt höger, där "n" anges av den högra operanden. Shift-höger-operatorn (-SHR) infogar en nolla på platsen längst till vänster när ett positivt eller osignerat värde flyttas till höger.

När den vänstra operanden är ett heltals värde (32-bitars) avgör de nedre 5 bitarna i den högra operanden hur många bitar av den vänstra operanden som flyttas.

När den vänstra operanden är ett Long (64-bitars) värde, bestämmer de nedre 6 bitarna i den högra operanden hur många bitar av den vänstra operanden som flyttas.

|Uttryck              |Resultat      |Binär     |Hexadecimal         |
|------------------------|------------|-----------|------------|
|`21 -shr 0`             | 21         | 0001 0101 | 0x15       |
|`21 -shr 1`             | 10         | 0000 1010 | 0x0A       |
|`21 -shr 2`             | 5          | 0000 0101 | 0x05       |
|`21 -shr 31`            | 0          | 0000 0000 | 0x00       |
|`21 -shr 32`            | 21         | 0001 0101 | 0x15       |
|`21 -shr 64`            | 21         | 0001 0101 | 0x15       |
|`21 -shr 65`            | 10         | 0000 1010 | 0x0A       |
|`21 -shr 66`            | 5          | 0000 0101 | 0x05       |
|`[int]::MaxValue -shr 1`| 1073741823 |           | 0x3FFFFFFF |
|`[int]::MinValue -shr 1`| – 1073741824|           | 0xC0000000 |
|`-1 -shr 1`             | -1         |           | 0xFFFFFFFF |

## <a name="see-also"></a>SE ÄVEN

- [about_arrays](about_Arrays.md)
- [about_assignment_operators](about_Assignment_Operators.md)
- [about_comparison_operators](about_Comparison_Operators.md)
- [about_hash_tables](about_Hash_Tables.md)
- [about_operators](about_Operators.md)
- [about_variables](about_Variables.md)
- [Hämta datum](xref:Microsoft.PowerShell.Utility.Get-Date)
- [New-TimeSpan](xref:Microsoft.PowerShell.Utility.New-TimeSpan)
