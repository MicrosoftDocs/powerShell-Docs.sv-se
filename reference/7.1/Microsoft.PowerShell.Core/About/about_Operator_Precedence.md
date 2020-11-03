---
description: Visar PowerShell-operatörer i prioritetsordning.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_operator_precedence?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Operator_Precedence
ms.openlocfilehash: d8b0b3f339739186825b5cb041adba5e06e5d702
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271730"
---
# <a name="about-operator-precedence"></a>Om operator prioritet

## <a name="short-description"></a>KORT BESKRIVNING
Visar PowerShell-operatörer i prioritetsordning.

## <a name="long-description"></a>LÅNG BESKRIVNING

Med PowerShell-operatörer kan du skapa enkla, men kraftfulla uttryck. I det här avsnittet visas operatorerna i prioritetsordning. Prioritetsordning är i vilken ordning som PowerShell utvärderar operatorer när flera operatorer visas i samma uttryck.

När operatorer har samma prioritet utvärderar PowerShell dem från vänster till höger som de visas i uttrycket. Undantagen är tilldelnings operatorer, omvandlings operatorer och negation operatorer ( `!` , `-not` , `-bnot` ) som utvärderas från höger till vänster.

Du kan använda-höljen, till exempel parenteser, för att åsidosätta standard prioritets ordningen och tvinga PowerShell att utvärdera den inneslutna delen av ett uttryck före en icke omsluten del.

I följande lista visas operatörerna i den ordning som de utvärderas. Operatorer på samma rad eller i samma grupp har samma prioritet.

Operator-kolumnen visar operatorerna. Referens kolumnen visar PowerShell-hjälp avsnittet där operatorn beskrivs. Om du vill visa avsnittet skriver du `get-help <topic-name>` .

|         OPERATOR         |           FÖRHÅLLANDE            |
| ------------------------ | ------------------------------ |
| `$() @() ()`             | [about_Operators][]            |
| `. ?.` (medlems åtkomst)   | [about_Operators][]            |
| `::` oföränderlig            | [about_Operators][]            |
| `[0] ?[0]` (index operator) | [about_Operators][]         |
| `[int]` (Cast-operatorer) | [about_Operators][]            |
| `-split` Operator         | [about_Split][]                |
| `-join` Operator          | [about_Join][]                 |
| `,` (komma operator)     | [about_Operators][]            |
| `++ --`                  | [about_Assignment_Operators][] |
| `! -not`                 | [about_Logical_Operators][]    |
| `..` (intervall operator)    | [about_Operators][]            |
| `-f` (format operator)   | [about_Operators][]            |
| `-` (enställig/negativ)     | [about_Arithmetic_Operators][] |
| `* / %`                  | [about_Arithmetic_Operators][] |
| `+ -`                    | [about_Arithmetic_Operators][] |

Följande grupp med operatorer har samma prioritet. De Skift läges känsliga och Skift läges känsliga varianterna har samma prioritet.

|         OPERATOR          |           FÖRHÅLLANDE            |
| ------------------------- | ------------------------------ |
| `-split` binär         | [about_Split][]                |
| `-join` binär          | [about_Join][]                 |
| `-is -isnot -as`          | [about_Type_Operators][]       |
| `-eq -ne -gt -gt -lt -le` | [about_Comparison_Operators][] |
| `-like -notlike`          | [about_Comparison_Operators][] |
| `-match -notmatch`        | [about_Comparison_Operators][] |
| `-in -notIn`              | [about_Comparison_Operators][] |
| `-contains -notContains`  | [about_Comparison_Operators][] |
| `-replace`                | [about_Comparison_Operators][] |

Listan återupptas här med följande operatorer i prioritetsordning:

|                OPERATOR                 |           FÖRHÅLLANDE            |
| --------------------------------------- | ------------------------------ |
| `-band -bnot -bor -bxor -shr -shl`      | [about_Arithmetic_Operators][] |
| `-and -or -xor`                         | [about_Logical_Operators][]    |

Följande objekt är inte sanna operatorer. De är en del av PowerShell-kommandosyntaxen, inte uttrycks syntax. Tilldelning är alltid den senaste åtgärd som inträffar.

|                SYNTAX                   |           FÖRHÅLLANDE            |
| --------------------------------------- | ------------------------------ |
| `.` (punkt-källa)                        | [about_Operators][]            |
| `&` kontakt                              | [about_Operators][]            |
| `? <if-true> : <if-false>` (Ternär operatör) | [about_Operators][]      |
| `??` (null-operatorer)            | [about_Operators][]            |
| <code>&#124;</code> (pipeline-operator) | [about_Operators][]            |
| `> >> 2> 2>> 2>&1`                      | [about_Redirection][]          |
| <code>&& &#124;&#124;</code> (pipelines kedje operatorer) | [about_Operators][] |
| `= += -= *= /= %= ??=`                  | [about_Assignment_Operators][] |

## <a name="examples"></a>EXEMPEL

Följande två kommandon visar de aritmetiska operatorerna och effekterna av att använda parenteser för att tvinga PowerShell att utvärdera den omslutna delen av uttrycket först.

```powershell
PS> 2 + 3 * 4
14

PS> (2 + 3) * 4
20
```

I följande exempel hämtas de skrivskyddade textfilerna från den lokala katalogen och sparas i `$read_only` variabeln.

```powershell
$read_only = Get-ChildItem *.txt | Where-Object {$_.isReadOnly}
```

Det motsvarar följande exempel.

```powershell
$read_only = ( Get-ChildItem *.txt | Where-Object {$_.isReadOnly} )
```

Eftersom pipeline-operatorn ( `|` ) har högre prioritet än tilldelnings operatorn ( `=` ) skickas filerna som `Get-ChildItem` cmdleten hämtar till `Where-Object` cmdleten för filtrering innan de tilldelas till `$read_only` variabeln.

Följande exempel visar att index operatorn har företräde framför omvandlings operatorn.

Det här uttrycket skapar en matris med tre strängar. Sedan använder den index operatorn med värdet 0 för att välja det första objektet i matrisen, som är den första strängen. Slutligen skickar den det valda objektet som en sträng. I det här fallet har Casten ingen påverkan.

```powershell
PS> [string]@('Windows','PowerShell','2.0')[0]
Windows
```

Det här uttrycket använder parenteser för att tvinga Cast-åtgärden att ske före index valet. Därför omvandlas hela matrisen som en (enkel) sträng. Sedan väljer index operatorn det första objektet i sträng mat ris, vilket är det första tecken.

```powershell
PS> ([string]@('Windows','PowerShell','2.0'))[0]
W
```

I följande exempel, eftersom `-gt` operatorn (större än) har en högre prioritet än `-and` operatorn (logisk och), är resultatet av uttrycket falskt.

```powershell
PS> 2 -gt 4 -and 1
False
```

Det motsvarar följande uttryck.

```powershell
PS> (2 -gt 4) -and 1
False
```

Om-och-operatorn har högre prioritet skulle svaret vara sant.

```powershell
PS> 2 -gt (4 -and 1)
True
```

Det här exemplet visar dock en viktig princip för att hantera operatörs prioritet. När ett uttryck är svårt för användare att tolka, använder du parenteser för att tvinga fram utvärderings ordningen, även om den tvingar standard operatorn prioritet. Parenteserna gör dina avsikter tydliga för personer som läser och underhåller dina skript.

## <a name="see-also"></a>SE ÄVEN

[about_Operators][]

[about_Assignment_Operators][]

[about_Comparison_Operators][]

[about_Arithmetic_Operators][]

[about_Join][]

[about_Redirection][]

[about_Scopes][]

[about_Split][]

[about_Type_Operators][]

<!-- reference links -->
[about_Arithmetic_Operators]: about_Arithmetic_Operators.md
[about_Assignment_Operators]: about_Assignment_Operators.md
[about_Comparison_Operators]: about_Comparison_Operators.md
[about_Join]: about_Join.md
[about_Logical_Operators]: about_logical_operators.md
[about_Operators]: about_Operators.md
[about_Redirection]: about_Redirection.md
[about_Scopes]: about_Scopes.md
[about_Split]: about_Split.md
[about_Type_Operators]: about_Type_Operators.md
