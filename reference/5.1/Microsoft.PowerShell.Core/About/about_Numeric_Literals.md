---
description: Både heltal och reella numeriska litteraler kan ha Type-och multiplikator-suffix.
Locale: en-US
ms.date: 04/09/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_numeric_literals?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Om numeriska litteraler
ms.openlocfilehash: 99fa8c1a751551d028fe6df0b0cec94e07f19c59
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/21/2020
ms.locfileid: "93273243"
---
# <a name="about-numeric-literals"></a>Om numeriska litteraler

Det finns två typer av numeriska litteraler: heltal och verklig. Båda kan ha Type-och multiplikator-suffix.

## <a name="integer-literals"></a>Heltals strängar

Heltals-litteraler kan skrivas i decimal-eller hexadecimal notation. Hexadecimala litteraler föregås av `0x` för att skilja dem från decimal tal.

Heltals-litteraler kan ha ett Type-suffix och ett multiplikator-suffix.

| Huvudnamnssuffix |       Innebörd       |
| ------ | ------------------- |
| l      | lång datatyp      |
| kunskap     | KB-multiplikator |
| MB     | MB multiplikator |
| minst     | GB multiplikator |
| TB     | terabyte-multiplikator |
| PT     | petabyte-multiplikator |

Typen av heltals sträng bestäms av dess värde, typens suffix och det numeriska multiplikator suffixet.

För en heltals sträng utan typ suffix:

- Om värdet kan representeras av typ `[int]` , vilket är dess typ.
- Annars, om värdet kan representeras av typ `[long]` , vilket är dess typ.
- Annars, om värdet kan representeras av typ `[decimal]` , vilket är dess typ.
- Annars representeras det av typen `[double]` .

För en heltals sträng med ett Type-suffix:

- Om Type-suffixet är `u` och värdet kan representeras av typ, `[int]` är dess typ `[int]` .
- Om Type-suffixet är `u` och värdet kan representeras av typ, `[long]` är dess typ `[long]` .
- Om dess värde kan representeras av en typ som anges, är det dess typ.
- Annars är den litteralen felaktig.

## <a name="real-literals"></a>Riktiga litteraler

Det går bara att skriva reella litteraler i decimal format. Den här notationen kan innehålla bråk värden efter ett decimal tecken och matematisk notation med en exponentiell del.

Exponentiell delen innehåller ett "e" följt av ett valfritt tecken (+/-) och ett tal som representerar exponenten. Till exempel är Literal-värdet `1e2` lika med det numeriska värdet 100.

Reella litteraler kan ha ett Type-suffix och ett multiplikator-suffix.

| Huvudnamnssuffix |       Innebörd       |
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

Utkombinations-suffixen kan användas i kombination med `u` , `ul` och `l` skriver suffix.

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
| `[UInt16]`  |                      | 16-bitars heltal (osignerat)        |
| `[Int32]`   |                      | 32-bitars heltal                   |
| `[int]`     | alias för `[int32]`  | 32-bitars heltal                   |
| `[UInt32]`  |                      | 32-bitars heltal (osignerat)        |
| `[Int64]`   |                      | 64-bitars heltal                   |
| `[long]`    | alias för `[int64]`  | 64-bitars heltal                   |
| `[UInt64]`  |                      | 64-bitars heltal (osignerat)        |
| `[bigint]`  |                      | Se [BigInteger struct][bigint]  |
| `[single]`  |                      | Flyttal med enkel precision  |
| `[float]`   | alias för `[single]` | Flyttal med enkel precision  |
| `[double]`  |                      | Dubbel precision, flytande punkt  |
| `[decimal]` |                      | 128-bitars svävande punkt           |

### <a name="working-with-other-numeric-types"></a>Arbeta med andra numeriska typer

Om du vill arbeta med andra numeriska typer måste du använda typ acceleratorer, som inte utan några problem. Till exempel tolkas alltid höga heltals värden som dubbelt innan de skickas till någon annan typ.

```
PS> [bigint]111111111111111111111111111111111111111111111111111111
111111111111111100905595216014112456735339620444667904
```

Värdet parsas som en dubbel första och förlorar precisionen i de högre intervallen.
Undvik det här problemet genom att ange värden som strängar och sedan konvertera dem:

```
PS> [bigint]'111111111111111111111111111111111111111111111111111111'
111111111111111111111111111111111111111111111111111111
```

## <a name="examples"></a>Exempel

Följande tabell innehåller flera exempel på numeriska litteraler och visar deras typ och värde:

|  Antal  |  Typ   |    Värde     |
| -------: | ------- | -----------: |
|      100 | Int32   |          100 |
|     100D | Decimal |          100 |
|     100l | Int64   |          100 |
|      1e2 | Double  |          100 |
|     1. E2 | Double  |          100 |
|    0x1e2 | Int32   |          482 |
|   0x1e2L | Int64   |          482 |
|   0x1e2D | Int32   |         7725 |
|     482D | Decimal |          482 |
|    482gb | Int64   | 517543559168 |
| 0x1e2lgb | Int64   | 517543559168 |

### <a name="commands-that-look-like-numeric-literals"></a>Kommandon som ser ut som numeriska litteraler

Alla kommandon som ser ut som en numerisk litteral måste köras med hjälp av anrops operatorn ( `&` ), annars tolkas det som ett tal av den associerade typen.

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
PS> 2L.GetType().Name
Int64
PS> 1.234.GetType().Name
Double
PS> (2).GetType().Name
Int32
```

De två första exemplen fungerar utan att omsluta literala värden, eftersom PowerShell-parsern kan avgöra var den numeriska literalen slutar och **gettype** -metoden börjar.

<!-- reference links -->
[bigint]: /dotnet/api/system.numerics.biginteger
