---
description: Beskriver reguljära uttryck i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 03/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_regular_expressions?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Regular_Expressions
ms.openlocfilehash: 6112c63b6d0c1018b56df85ec6ae919a0285ffc3
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270506"
---
# <a name="about-regular-expressions"></a>Om reguljära uttryck

## <a name="short-description"></a>Kort beskrivning
Beskriver reguljära uttryck i PowerShell.

## <a name="long-description"></a>Lång beskrivning

> [!NOTE]
> Den här artikeln visar syntax och metoder för att använda reguljära uttryck i PowerShell, men all syntax diskuteras inte. En mer fullständig referens finns i [snabb referens för reguljära uttryck](/dotnet/standard/base-types/regular-expression-language-quick-reference).

Ett reguljärt uttryck är ett mönster som används för att matcha text. Det kan bestå av litterala tecken, operatorer och andra konstruktioner.

Den här artikeln visar syntaxen för reguljära uttryck i PowerShell. PowerShell har flera operatorer och cmdlets som använder reguljära uttryck. Du kan läsa mer om deras syntax och användning på länkarna nedan.

- [Select-String](xref:Microsoft.PowerShell.Utility.Select-String)
- [– matcha och-ersätt operatörer](about_Comparison_Operators.md)
- [– Dela](about_Split.md)
- [Switch-instruktion med alternativet-regex](about_Switch.md)

Reguljära uttryck i PowerShell är Skift läges känsliga som standard. Varje metod som visas ovan har ett annat sätt att framtvinga Skift läges känslighet.

|       Metod       |                      Skift läges känslighet                      |
| ------------------ | ---------------------------------------------------------- |
| `Select-String`    | Använd `-CaseSensitive` switch                                |
| `switch` Sekretesspolicy | Använd `-casesensitive` alternativet                            |
| operatorer          | prefix med **"c"** ( `-cmatch` , `-csplit` eller `-creplace` ) |

### <a name="character-literals"></a>Tecken strängar

Ett reguljärt uttryck kan vara ett tecken eller en sträng. Uttrycket gör att motorn matchar texten som anges exakt.

```powershell
# This statement returns true because book contains the string "oo"
'book' -match 'oo'
```

### <a name="character-classes"></a>Character-klasser

Tecken strängar fungerar om du känner till det exakta mönstret, men med tecken klasser kan du vara mindre specifika.

#### <a name="character-groups"></a>Character-grupper

`[character group]` gör att du kan matcha valfritt antal tecken en enda stund och `[^character group]` bara matcha tecken som inte finns i gruppen.

```powershell
# This expression returns true if the pattern matches big, bog, or bug.
'big' -match 'b[iou]g'
```

Om listan över tecken som ska matchas innehåller bindestreck ( `-` ) måste den finnas i början eller slutet av listan för att skilja den från ett tecken intervall uttryck.

#### <a name="character-ranges"></a>Character-intervall

Ett mönster kan också vara ett tecken intervall. Tecknen kan vara alfabetiska `[A-Z]` , numeriska `[0-9]` eller jämna ASCII-baserade `[ -~]` (alla tecken som kan skrivas ut).

```powershell
# This expression returns true if the pattern matches any 2 digit number.
42 -match '[0-9][0-9]'
```

#### <a name="numbers"></a>Tal

`\d`Tecken klassen matchar alla decimal siffror. Omvänt `\D` kommer att matcha alla siffror som inte är decimaler.

```powershell
# This expression returns true if it matches a server name.
# (Server-01 - Server-99).
'Server-01' -match 'Server-\d\d'
```

#### <a name="word-characters"></a>Ord tecken

`\w`Klassen Character matchar valfritt ord `[a-zA-Z_0-9]` . Använd om du vill matcha ord som inte är ord `\W` .

```powershell
# This expression returns true.
# The pattern matches the first word character 'B'.
'Book' -match '\w'
```

#### <a name="wildcards"></a>Jokertecken

Punkten ( `.` ) är ett jokertecken i reguljära uttryck. Det matchar alla bokstäver utom en ny rad ( `\n` ).

```powershell
# This expression returns true.
# The pattern matches any 4 characters except the newline.
'a1\ ' -match '....'
```

#### <a name="whitespace"></a>Blanksteg

Blank steg matchas med `\s` klassen Character. Tecken som inte är blank steg matchas med `\S` . Tecken för tecken avstånd `' '` kan också användas.

```powershell
# This expression returns true.
# The pattern uses both methods to match the space.
' - ' -match '\s- '
```

### <a name="quantifiers"></a>Kvantifierare

Kvantifierare styr hur många instanser av varje element som ska finnas i Indatasträngen.

Följande är några av de kvantifierare som är tillgängliga i PowerShell:

| Kvantifieraren |                Beskrivning                |
| ---------- | ----------------------------------------- |
| `*`        | Noll eller flera gånger.                       |
| `+`        | En eller flera gånger.                        |
| `?`        | Noll eller en tid.                         |
| `{n,m}`    | Minst `n` , men inte mer än `m` gånger. |

Asterisken ( `*` ) matchar föregående element noll eller flera gånger. Resultatet är att även en indatasträng utan element skulle vara en matchning.

```powershell
# This returns true for all account name strings even if the name is absent.
'ACCOUNT NAME:    Administrator' -match 'ACCOUNT NAME:\s*\w*'
```

Plus tecknet ( `+` ) matchar det föregående elementet en eller flera gånger.

```powershell
# This returns true if it matches any server name.
'DC-01' -match '[A-Z]+-\d\d'
```

Frågetecknet `?` matchar föregående element noll eller en tid. Precis som asterisk `*` , matchar den även strängar där elementet saknas.

```powershell
# This returns true for any server name, even server names without dashes.
'SERVER01' -match '[A-Z]+-?\d\d'
```

`{n, m}`Kvantifieraren kan användas på flera olika sätt för att tillåta detaljerad kontroll över Kvantifieraren. Det andra elementet `m` och kommatecken `,` är valfria.

| Kvantifieraren |                Beskrivning                 |
| ---------- | ------------------------------------------ |
| `{n}`      | Matcha exakt `n` antal gånger.         |
| `{n,}`     | Matcha minst `n` antal gånger.        |
| `{n,m}`    | Matcha mellan `n` och `m` antal gånger. |

```powershell
# This returns true if it matches any phone number.
'111-222-3333' -match '\d{3}-\d{3}-\d{4}'
```

### <a name="anchors"></a>Ankare

Med ankare kan du göra så att en matchning lyckas eller Miss lyckas baserat på matchnings positionen i Indatasträngen.

De två ofta använda ankarena är `^` och `$` . Cirkumflexet `^` matchar början av en sträng och `$` , som matchar slutet på en sträng. Med ankarena kan du matcha din text vid en speciell position medan du också tar bort oönskade tecken.

```powershell
# The pattern expects the string 'fish' to be the only thing on the line.
# This returns FALSE.
'fishing' -match '^fish$'
```

> [!NOTE]
> När du definierar ett regex som innehåller ett `$` ankare måste du omsluta regex med enkla citat tecken ( `'` ) i stället för dubbla citat tecken ( `"` ) eller PowerShell för att expandera uttrycket som en variabel.

När du använder ankare i PowerShell bör du förstå skillnaden mellan **Singleline** och alternativ för reguljära uttryck i **flera rader** .

- Flera **rader** : Multiline-läge tvingar fram `^` och `$` matchar början av varje rad i stället för början och slutet av Indatasträngen.
- **Singleline** : Singleline mode behandlar Indatasträngen som en **Singleline**.
  Det tvingar `.` tecknet att matcha varje Character (inklusive newlines), i stället för att matcha alla bokstäver förutom rad matningen `\n` .

Om du vill läsa mer om de här alternativen och hur du använder dem går du till [snabb referens för det reguljära uttrycks språket](/dotnet/standard/base-types/regular-expression-language-quick-reference).

### <a name="escaping-characters"></a>Undantagna tecken

Omvänt snedstreck ( `\` ) används för att undanta tecken så att de inte tolkas av motorn för reguljära uttryck.

Följande tecken är reserverade: `[]().\^$|?*+{}` .

Du måste undanta dessa tecken i mönstren för att matcha dem i dina indatatyper.

```powershell
# This returns true and matches numbers with at least 2 digits of precision.
# The decimal point is escaped using the backslash.
'3.141' -match '3\.\d{2,}'
```

Det finns en statisk metod för regex-klassen som kan kringgå text åt dig.

```powershell
[regex]::escape('3.\d{2,}')
```

```Output
3\.\\d\{2,}
```

> [!NOTE]
> Detta utrymningr alla reserverade tecken i reguljära uttryck, inklusive befintliga omvända snedstreck som används i tecken klasser. Se till att du bara använder den i den del av ditt mönster som du behöver undanta.

#### <a name="other-character-escapes"></a>Andra tecken Escape

Det finns också reserverade escape-tecken som du kan använda för att matcha särskilda tecken typer.

Här följer några vanliga escape-tecken:

|Tecken Escape  |Beskrivning  |
|---------|---------|
|`\t`|Matchar en flik|
|`\n`|Matchar en ny rad|
|`\r`|Matchar en vagn retur|

### <a name="groups-captures-and-substitutions"></a>Grupper, avbildningar och ersättningar

Gruppering av konstruktion separerar en indatasträng i del strängar som kan fångas eller ignoreras. Grupperade del strängar kallas under uttryck. Som standard registreras under uttryck i numrerade grupper, men du kan även tilldela dem namn.

En grupperings-konstruktion är ett reguljärt uttryck som omges av parenteser. All text som matchas av det omslutna reguljära uttrycket fångas. I följande exempel bryts inmatad text i två hämtade grupper.

```powershell
'The last logged on user was CONTOSO\jsmith' -match '(.+was )(.+)'
```

```Output
True
```

Använd den `$Matches` automatiska variabeln **hash** för att hämta insamlad text.
Texten som representerar hela matchningen lagras i nyckeln `0` .

```powershell
$Matches.0
```

```Output
The last logged on user was CONTOSO\jsmith
```

Avbildningar lagras i numeriska **heltals** nycklar som ökar från vänster till höger. Capture `1` innehåller all text tills användar namnet, avbildningen `2` innehåller bara användar namnet.

```powershell
$Matches
```

```Output
Name                           Value
----                           -----
2                              CONTOSO\jsmith
1                              The last logged on user was
0                              The last logged on user was CONTOSO\jsmith
```

> [!IMPORTANT]
> `0`Nyckeln är ett **heltal**. Du kan använda valfri **hash** -Metod för att komma åt värdet som lagras.
>
> ```
> PS> 'Good Dog' -match 'Dog'
> True
>
> PS> $Matches[0]
> Dog
>
> PS> $Matches.Item(0)
> Dog
>
> PS> $Matches.0
> Dog
> ```

#### <a name="named-captures"></a>Namngivna insamlingar

Som standard lagras avbildningar i stigande numerisk ordning, från vänster till höger.
Du kan också tilldela ett **namn** till en samlad grupp. Det här **namnet** blir en nyckel på den `$Matches` automatiska variabeln **hash** .

I en insamlings grupp använder `?<keyname>` du för att lagra insamlade data under en namngiven nyckel.

```
PS> $string = 'The last logged on user was CONTOSO\jsmith'
PS> $string -match 'was (?<domain>.+)\\(?<user>.+)'
True

PS> $Matches

Name                           Value
----                           -----
domain                         CONTOSO
user                           jsmith
0                              was CONTOSO\jsmith

PS> $Matches.domain
CONTOSO

PS> $Matches.user
jsmith
```

I följande exempel lagras den senaste logg posten i säkerhets loggen i Windows.
Det angivna reguljära uttrycket extraherar användar namnet och domänen från meddelandet och lagrar dem under nycklarna: **N** för namn och **D** för domän.

```powershell
$log = (Get-WinEvent -LogName Security -MaxEvents 1).message
$r = '(?s).*Account Name:\s*(?<N>.*).*Account Domain:\s*(?<D>[A-Z,0-9]*)'
$log -match $r
```

```Output
True
```

```powershell
$Matches
```

```Output
Name                           Value
----                           -----
D                              CONTOSO
N                              jsmith
0                              A process has exited....
```

Mer information finns i [gruppera konstruktioner i reguljära uttryck](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions).

#### <a name="substitutions-in-regular-expressions"></a>Ersättningar i reguljära uttryck

Med hjälp av de reguljära uttrycken med `-replace` operatorn kan du ersätta text dynamiskt med hjälp av insamlad text.

`<input> -replace <original>, <substitute>`

- `<input>`: Strängen som ska genomsökas
- `<original>`: Ett reguljärt uttryck som används för att söka i Indatasträngen
- `<substitute>`: Ett uttryck för vanlig uttrycks ersättning som ersätter matchningar som finns i Indatasträngen.

> [!NOTE]
> `<original>` `<substitute>` Operanderna och omfattas av regler för den reguljära uttrycks motorn, till exempel tecken undantag.

Det går att referera till hämtade grupper i `<substitute>` strängen. Ersättningen görs med hjälp av ett `$` tecken före grupp-ID: n.

Det finns två sätt att referera till infångade grupper med hjälp av **nummer** och efter **namn**.

- Per **nummer** – fångar grupper numreras från vänster till höger.

  ```powershell
  'John D. Smith' -replace '(\w+) (\w+)\. (\w+)', '$1.$2.$3@contoso.com'
  ```

  ```Output
  John.D.Smith@contoso.com
  ```

- Efter **namn** -hämtade grupper kan också refereras till med hjälp av namn.

  ```powershell
  'CONTOSO\Administrator' -replace '\w+\\(?<user>\w+)', 'FABRIKAM\${user}'
  ```

  ```Output
  FABRIKAM\Administrator
  ```

`$&`Uttrycket representerar all matchad text.

```powershell
'Gobble' -replace 'Gobble', '$& $&'
```

```Output
Gobble Gobble
```

> [!WARNING]
> Eftersom det `$` används i sträng expansion måste du använda litterala strängar med ersättning eller Escape- `$` tecken när du använder dubbla citat tecken.
>
> ```powershell
> 'Hello World' -replace '(\w+) \w+', '$1 Universe'
> "Hello World" -replace "(\w+) \w+", "`$1 Universe"
> ```
>
> ```Output
> Hello Universe
> Hello Universe
> ```
>
> Om du vill `$` använda som ett litteralt tecken ska du använda `$$` i stället för vanliga escape-tecken. När du använder dubbla citat tecken kan du fortfarande kringgå alla instanser av `$` för att undvika felaktig ersättning.
>
> ```powershell
> '5.72' -replace '(.+)', '$$$1'
> "5.72" -replace "(.+)", "`$`$`$1"
> ```
>
> ```Output
> $5.72
> $5.72
> ```

Mer information finns i [ersättningar i reguljära uttryck](/dotnet/standard/base-types/substitutions-in-regular-expressions).

## <a name="see-also"></a>Se även

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Operators](about_Operators.md)
