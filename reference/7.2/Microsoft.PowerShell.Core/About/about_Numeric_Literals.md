---
description: Både heltal och reella numeriska litteraler kan ha Type-och multiplikator-suffix.
Locale: en-US
ms.date: 04/12/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_numeric_literals?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Om numeriska litteraler
ms.openlocfilehash: 0e4081c7601928ce9b74010ea3c86762902ca97a
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708874"
---
# <a name="about-numeric-literals"></a>Om numeriska litteraler

Det finns två typer av numeriska litteraler: heltal och verklig. Båda kan ha Type-och multiplikator-suffix.

## <a name="integer-literals"></a>Heltals strängar

Heltals-litteraler kan skrivas i decimal-, hexadecimal-eller binär notation.
Hexadecimala litteraler föregås av `0x` och binära litteraler föregås av `0b` för att skilja dem från decimal tal.

Heltals-litteraler kan ha ett Type-suffix och ett multiplikator-suffix.

| Huvudnamnssuffix |            Betydelse             |          Anteckning           |
| ------ | ------------------------------ | ----------------------- |
| y      | datatyp för signerad byte          | Tillagt i PowerShell 6,2 |
| uy     | datatyp för osignerad byte        | Tillagt i PowerShell 6,2 |
| s      | kort datatyp                | Tillagt i PowerShell 6,2 |
| USA     | osignerad kort data typ       | Tillagt i PowerShell 6,2 |
| l      | lång datatyp                 |                         |
| ä      | osignerad int-eller Long-datatyp | Tillagt i PowerShell 6,2 |
| UL     | osignerad Long-datatyp        | Tillagt i PowerShell 6,2 |
| n      | Data typen BigInteger           | Tillagt i PowerShell 7,0 |
| kunskap     | KB-multiplikator            |                         |
| MB     | MB multiplikator            |                         |
| minst     | GB multiplikator            |                         |
| TB     | terabyte-multiplikator            |                         |
| PT     | petabyte-multiplikator            |                         |

Typen av heltals sträng bestäms av dess värde, typens suffix och det numeriska multiplikator suffixet.

För en heltals sträng utan typ suffix:

- Om värdet kan representeras av typ `[int]` , vilket är dess typ.
- Annars, om värdet kan representeras av typ `[long]` , vilket är dess typ.
- Annars, om värdet kan representeras av typ `[decimal]` , vilket är dess typ.
- Annars representeras det av typen `[double]` .

För en heltals sträng med ett Type-suffix:

- Om Type-suffixet är `u` och värdet kan representeras av typ, `[uint]` är dess typ `[uint]` .
- Om Type-suffixet är `u` och värdet kan representeras av typ, `[ulong]` är dess typ `[ulong]` .
- Om dess värde kan representeras av en typ som anges, är det dess typ.
- Annars är den litteralen felaktig.

## <a name="real-literals"></a>Riktiga litteraler

Det går bara att skriva reella litteraler i decimal format. Den här notationen kan innehålla bråk värden efter ett decimal tecken och matematisk notation med en exponentiell del.

Exponentiell delen innehåller ett "e" följt av ett valfritt tecken (+/-) och ett tal som representerar exponenten. Till exempel är Literal-värdet `1e2` lika med det numeriska värdet 100.

Reella litteraler kan ha ett Type-suffix och ett multiplikator-suffix.

| Huvudnamnssuffix |       Betydelse       |
| ------ | ------------------- |
| d      | decimal data typ   |
| kunskap     | KB-multiplikator |
| MB     | MB multiplikator |
| minst     | GB multiplikator |
| TB     | terabyte-multiplikator |
| PT     | petabyte-multiplikator |

Det finns två typer av verklig literal: dubbel och decimal. Dessa anges av frånvaron eller närvaron av typen decimal-typ. PowerShell har inte stöd för en litteral representation av ett `[float]` värde. En dubbel verklig literal har en typ `[double]` . En riktig decimal literal har en typ `[decimal]` .
Efterföljande nollor i bråk delen av en decimal verklig literal är signifikanta.

Om värdet för exponentens siffror i en `[double]` riktig literal är mindre än det lägsta stödda värdet är värdet för den `[double]` verkliga literalen 0. Om värdet för exponentens siffror i en `[decimal]` riktig literal är mindre än det lägsta stödda värdet är den litteralen felaktig. Om värdet för exponentens siffror i en `[double]` eller `[decimal]` reella litteraler är större än det högsta tillåtna värdet, är den litteralen felaktig.

> [!NOTE]
> Syntaxen tillåter en dubbel verklig literal att ha ett suffix med lång typ.
> PowerShell behandlar det här fallet som en heltals sträng vars värde representeras av Type `[long]` . Den här funktionen har behållits för bakåtkompatibilitet med tidigare versioner av PowerShell. Programmerare rekommenderas dock inte att använda heltals strängar i det här formuläret eftersom de lätt kan dölja litteralens faktiska värde. Har t. ex. `1.2L` värdet 1, `1.2345e1L` värdet 12 och `1.2345e-5L` värdet 0, ingen av som är direkt uppenbara.

## <a name="numeric-multipliers"></a>Numeriska multiplikatorer

För enkelhetens skull kan heltal och reella litteraler innehålla en numerisk multiplikator som visar en uppsättning vanliga befogenheter på 2. Den numeriska multiplikatorn kan skrivas i valfri kombination av versaler eller gemener.

Multiplikatorns suffix kan användas i kombination med alla typer av suffix, men måste finnas efter typ-suffixet. Literalen är till exempel `100gbL` felaktig, men litteralen `100Lgb` är giltig.

Om en multiplikator skapar ett värde som överskrider de möjliga värdena för den numeriska typ som suffixet anger, är literalen felaktig. Litteralen är till exempel `1usgb` felaktig eftersom värdet `1gb` är större än vad som tillåts för den `[ushort]` typ som anges av `us` suffixet.

### <a name="multiplier-examples"></a>Multiplikator exempel

```
PS> 1kb
1024

PS> 1.30Dmb
1363148.80

PS> 0x10Gb
17179869184

PS> 1.4e23tb
1.5393162788864E+35

PS> 0x12Lpb
20266198323167232
```

## <a name="numeric-type-accelerators"></a>Numeriska typ acceleratorer

PowerShell stöder följande typ acceleratorer:

| Gas |         Anteckning         |           Beskrivning            |
| ----------- | -------------------- | -------------------------------- |
| `[byte]`    |                      | Byte (ej signerat)                  |
| `[sbyte]`   |                      | Byte (signerat)                    |
| `[Int16]`   |                      | 16-bitars heltal                   |
| `[short]`   | alias för `[int16]`  | 16-bitars heltal                   |
| `[UInt16]`  |                      | 16-bitars heltal (osignerat)        |
| `[ushort]`  | alias för `[uint16]` | 16-bitars heltal (osignerat)        |
| `[Int32]`   |                      | 32-bitars heltal                   |
| `[int]`     | alias för `[int32]`  | 32-bitars heltal                   |
| `[UInt32]`  |                      | 32-bitars heltal (osignerat)        |
| `[uint]`    | alias för `[uint32]` | 32-bitars heltal (osignerat)        |
| `[Int64]`   |                      | 64-bitars heltal                   |
| `[long]`    | alias för `[int64]`  | 64-bitars heltal                   |
| `[UInt64]`  |                      | 64-bitars heltal (osignerat)        |
| `[ulong]`   | alias för `[uint64]` | 64-bitars heltal (osignerat)        |
| `[bigint]`  |                      | Se [BigInteger struct][bigint]  |
| `[single]`  |                      | Flyttal med enkel precision  |
| `[float]`   | alias för `[single]` | Flyttal med enkel precision  |
| `[double]`  |                      | Dubbel precision, flytande punkt  |
| `[decimal]` |                      | 128-bitars svävande punkt           |

> [!NOTE]
> Följande typ acceleratorer har lagts till i PowerShell 6,2: `[short]` , `[ushort]` , `[uint]` , `[ulong]` .

## <a name="examples"></a>Exempel

Följande tabell innehåller flera exempel på numeriska litteraler och visar deras typ och värde:

|   Antal    |    Typ    |    Värde     |
| ----------: | ---------- | -----------: |
|         100 | Int32      |          100 |
|        100u | UInt32     |          100 |
|        100D | Decimal    |          100 |
|        100l | Int64      |          100 |
|       100uL | UInt64     |          100 |
|       100us | UInt16     |          100 |
|       100uy | Byte       |          100 |
|        100y | SByte      |          100 |
|         1e2 | Double     |          100 |
|        1. E2 | Double     |          100 |
|       0x1e2 | Int32      |          482 |
|      0x1e2L | Int64      |          482 |
|      0x1e2D | Int32      |         7725 |
|        482D | Decimal    |          482 |
|       482gb | Int64      | 517543559168 |
|      482ngb | BigInteger | 517543559168 |
|    0x1e2lgb | Int64      | 517543559168 |
|   0b1011011 | Int32      |           91 |
|     0xFFFFs | Int16      |           -1 |
|  0xFFFFFFFF | Int32      |           -1 |
| -0xFFFFFFFF | Int32      |            1 |
| 0xFFFFFFFFu | UInt32     |   4294967295 |

### <a name="working-with-binary-or-hexadecimal-numbers"></a>Arbeta med binära eller hexadecimala tal

Alltför stora binära eller hexadecimala litteraler kan returneras som `[bigint]` i stället för att parsa, om och endast om `n` suffixet har angetts. Signerade bitar respekteras fortfarande över jämna `[decimal]` intervall, men:

- Om en binär sträng är en multipel av 8 bitar, behandlas den högsta biten som Sign-biten.
- Om en hex-sträng, som har en längd som är delbar med 8, har den första siffran med 8 eller högre, behandlas siffror som negativt.

Om du anger ett osignerat suffix för binär-och hex-litteraler ignoreras tecken bitar. Returnerar till exempel `0xFFFFFFFF` `-1` , men `0xFFFFFFFFu` returnerar `[uint]::MaxValue` 4294967295.

I PowerShell 7,1 returnerar nu ett signerat värde av den typen genom att använda ett Type-suffix på en hexadecimal litteral. I PowerShell 7,0 returnerar uttrycket till exempel `0xFFFFs` ett fel eftersom det positiva värdet är för stort för en `[int16]` typ.
PowerShell 7,1 tolkar detta som `-1` en `[int16]` typ.

Genom att prefixet med en sträng `0` kringgås detta och behandlas som osignerat.
Till exempel: `0b011111111`. Detta kan vara nödvändigt när du arbetar med litteraler i `[bigint]` intervallet, eftersom `u` `n` suffixen inte kan kombineras.

Du kan också negera binär och hex-litteraler med `-` prefixet. Detta kan resultera i ett positivt tal eftersom inloggnings bitar är tillåtna.

Signerade bitar accepteras för BigInteger-suffix:

- BigInteger-suffixet hex behandlar den höga biten av en literal med en längd på flera av 8 tecken som tecken sträng. Längden inkluderar inte `0x` prefixet eller några suffix.
- Binär BigInteger accepterar tecken med tecken på 96 och 128 tecken, och var 8 tecken efter.

### <a name="commands-that-look-like-numeric-literals"></a>Kommandon som ser ut som numeriska litteraler

Alla kommandon som ser ut som en giltig numerisk literal måste köras med hjälp av anrops operatorn ( `&` ), annars tolkas det som ett tal. Felaktiga litteraler med giltig syntax som `1usgb` leder till följande fel:

```
PS> 1usgb
At line:1 char:6
+ 1usgb
+      ~
The numeric constant 1usgb is not valid.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : BadNumericConstant
```

Felaktiga litteraler med ogiltig syntax som `1gbus` kommer att tolkas som en vanlig standard sträng och kan tolkas som ett giltigt kommando namn i kontexter där kommandon kan anropas.

### <a name="access-properties-and-methods-of-numeric-objects"></a>Åtkomst egenskaper och metoder för numeriska objekt

Om du vill ha åtkomst till en medlem med en numerisk literal, finns det fall när du behöver omsluta literalen inom parentes.

- Literalen har inget decimal tecken
- Literalen saknar siffror efter decimal tecknet
- Literalen har inget suffix

Till exempel Miss lyckas följande exempel:

```
PS> 2.GetType().Name
At line:1 char:11
+ 2.GetType().Name
+           ~
An expression was expected after '('.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordException
+ FullyQualifiedErrorId : ExpectedExpression
```

Följande exempel fungerar:

```
PS> 2uL.GetType().Name
UInt64
PS> 1.234.GetType().Name
Double
PS> (2).GetType().Name
Int32
```

De två första exemplen fungerar utan att omsluta literala värden, eftersom PowerShell-parsern kan avgöra var den numeriska literalen slutar och **gettype** -metoden börjar.

## <a name="how-powershell-parses-numeric-literals"></a>Hur PowerShell tolkar numeriska litteraler

PowerShell v 7.0 har ändrat hur numeriska litteraler tolkas för att aktivera de nya funktionerna.

### <a name="parsing-real-numeric-literals"></a>Parsa reella numeriska litteraler

Om literalen innehåller ett decimal tecken eller e-postnotationen tolkas strängen som ett reellt tal.

- Om decimal-suffixet är tillgängligt direkt i `[decimal]` .
- Annars kan du parsa `[Double]` och tillämpa multiplikatorn till värdet. Kontrol lera sedan Skriv suffixen och försök att omvandla till lämplig typ.
- Om strängen inte har något typ-suffix tolkar du som `[Double]` .

### <a name="paring-integer-numeric-literals"></a>Paring heltal för numeriska litteraler

Heltals typ strängar parsas med hjälp av följande steg:

1. Fastställa bas-formatet
   - För binära format, parsa till `[BigInteger]` .
   - För hexadecimala format kan du analysera i `[BigInteger]` att använda särskilda Casies för att behålla ursprungliga beteenden när värdet är i `[int]` `[long]` intervallet eller.
   - Om varken binärt eller hex tolkas normalt som en `[BigInteger]` .
2. Använd multiplikator värdet innan du försöker utföra några sändningar för att säkerställa att typ gränser kan kontrol leras på lämpligt sätt utan att flöda över.
3. Kontrol lera Skriv suffix.
   - Kontrol lera typ gränser och försök att parsa till den typen.
   - Om inget suffix används, begränsas värdet – kontrol leras i följande ordning, vilket resulterar i det första lyckade testet som avgör typen av nummer.
     - `[int]`
     - `[long]`
     - `[decimal]` (endast bas-10-litteraler)
     - `[double]` (endast bas-10-litteraler)
   - Om värdet ligger utanför `[long]` intervallet för hex och Binary Number, Miss lyckas parsningen.
   - Om värdet ligger utanför `[double]` intervallet för bas 10-nummer, Miss lyckas parsningen.
   - Högre värden måste uttryckligen skrivas med hjälp av `n` suffixet för att parsa literalen som en `BigInteger` .

### <a name="parsing-large-value-literals"></a>Parsa stora värdes strängar

Tidigare parsades högre heltals värden som Double innan de omvandlades till någon annan typ. Detta resulterar i en förlust av precision i de högre intervallen. Exempel:

```
PS> [bigint]111111111111111111111111111111111111111111111111111111
111111111111111100905595216014112456735339620444667904
```

Undvik det här problemet genom att skriva värden som strängar och sedan konvertera dem:

```
PS> [bigint]'111111111111111111111111111111111111111111111111111111'
111111111111111111111111111111111111111111111111111111
```

I PowerShell 7,0 måste du använda `N` suffixet.

```
PS> 111111111111111111111111111111111111111111111111111111n
111111111111111111111111111111111111111111111111111111
```

Värden mellan `[ulong]::MaxValue` och `[decimal]::MaxValue` bör också anges med decimal-suffixet `D` för att bibehålla noggrannhet. Utan suffixet tolkas dessa värden som att `[Double]` använda det verkliga tolknings läget.

<!-- reference links -->
[bigint]: /dotnet/api/system.numerics.biginteger
