---
description: Beskriver de operatorer som jämför värden i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comparison_operators?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Comparison_Operators
ms.openlocfilehash: 28e7d1c49f64fae09679948a729319d9525248a0
ms.sourcegitcommit: c9e56ec489522c706b8d6b8733f3f015d6d7e893
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2020
ms.locfileid: "93272925"
---
# <a name="about-comparison-operators"></a>Om jämförelse operatorer

## <a name="short-description"></a>Kort beskrivning
Beskriver de operatorer som jämför värden i PowerShell.

## <a name="long-description"></a>Lång beskrivning

Med jämförelse operatorer kan du ange villkor för jämförelse av värden och hitta värden som matchar angivna mönster. Om du vill använda en jämförelse operator anger du de värden som du vill jämföra tillsammans med en operator som särskiljer dessa värden.

PowerShell innehåller följande jämförelse operatorer:

| Typ        | Operatorer    | Beskrivning                                 |
| ----------- | ------------ | --------------------------------------------|
| Likhet    | -EQ          | är lika med                                      |
|             | -Ne          | inte lika med                                  |
|             | -gt          | större än                                |
|             | -ge          | större än eller lika med                       |
|             | -lt          | mindre än                                   |
|             | -Le          | mindre än eller lika med                          |
|             |              |                                             |
| Matching    | – som        | Returnerar true när strängen matchar jokertecken   |
|             |              | ofta                                     |
|             | -notlike     | Returnerar sant när strängen inte matchar     |
|             |              | mönster för jokertecken                            |
|             | -matcha       | Returnerar sant när strängen matchar regex      |
|             |              | ofta $matches innehåller matchande strängar |
|             | -notmatch    | Returnerar sant när strängen inte matchar     |
|             |              | regex-mönster; $matches innehåller matchande   |
|             |              | strängar                                     |
|             |              |                                             |
| Behållare | – innehåller    | Returnerar sant när referensvärdet finns |
|             |              | i en samling                             |
|             | -notcontains | Returnerar värdet true när referensvärdet inte       |
|             |              | ingår i en samling                   |
|             | – in          | Returnerar sant när test värde i en |
|             |              | samling                                  |
|             | -notin       | Returnerar sant när test värde inte ingår  |
|             |              | i en samling                             |
|             |              |                                             |
| Ny funktion | -Ersätt     | Ersätter ett sträng mönster                   |
|             |              |                                             |
| Typ        | -är          | Returnerar true om båda objekten är identiska    |
|             |              | typ                                        |
|             | – IsNot       | Returnerar sant om objekten inte är samma|
|             |              | typ                                        |

Som standard är alla jämförelse operatorer Skift läges känsliga. Om du vill göra en jämförelse operator Skift läges känslig, måste du före operator namnet med en `c` . Till exempel är den Skift läges känsliga versionen av `-eq` är `-ceq` . Om du vill göra Skift läges känsligheten explicit måste du föregå operatorn med en `i` . Till exempel är den explicita Skift läges känsliga versionen `-eq` av `-ieq` .

När indatamängden till en operator är ett skalärt värde returnerar jämförelse operatorer ett booleskt värde. När indatatypen är en samling med värden returnerar jämförelse operatorer alla matchande värden. Om det inte finns några matchningar i en samling returnerar jämförelse operatorer en tom matris.

```powershell
PS> (1, 2 -eq 3).GetType().FullName
System.Object[]
```

Undantagen är operatorerna för inne slutning, operatorerna och typ operatorerna, som alltid returnerar ett **booleskt** värde.

> [!NOTE]
> Om du behöver jämföra ett värde med till `$null` `$null` vänster i jämförelsen. När du jämför `$null` med ett **objekt []** är resultatet **falskt** eftersom jämförelse objektet är en matris. När du jämför en matris med `$null` filtrerar jämförelser alla `$null` värden som lagras i matrisen. Ett exempel:
>
> ```powershell
> PS> $null -ne $null, "hello"
> True
> PS> $null, "hello" -ne $null
> hello
> ```

### <a name="equality-operators"></a>Likhets operatorer

Likhets operatorerna ( `-eq` , `-ne` ) returnerar värdet true eller matchar när ett eller flera indatavärden är identiska med det angivna mönstret. Hela mönstret måste matcha ett helt värde.

Exempel:

#### <a name="-eq"></a>-EQ

Beskrivning: lika med. Innehåller ett identiskt värde.

Exempel:

```powershell
PS> 2 -eq 2
True

PS> 2 -eq 3
False

PS> 1,2,3 -eq 2
2
PS> "abc" -eq "abc"
True

PS> "abc" -eq "abc", "def"
False

PS> "abc", "def" -eq "abc"
abc
```

#### <a name="-ne"></a>-Ne

Beskrivning: inte lika med. Innehåller ett annat värde.

Exempel:

```powershell
PS> "abc" -ne "def"
True

PS> "abc" -ne "abc"
False

PS> "abc" -ne "abc", "def"
True

PS> "abc", "def" -ne "abc"
def
```

#### <a name="-gt"></a>-gt

Beskrivning: större än.

Exempel:

```powershell
PS> 8 -gt 6
True

PS> 7, 8, 9 -gt 8
9
```

> [!NOTE]
> Detta bör inte förväxlas med `>` operatorn större än i många andra programmeringsspråk. I PowerShell `>` används för omdirigering. Mer information finns i [About_redirection](about_Redirection.md#potential-confusion-with-comparison-operators).

#### <a name="-ge"></a>-ge

Beskrivning: större än eller lika med.

Exempel:

```powershell
PS> 8 -ge 8
True

PS> 7, 8, 9 -ge 8
8
9
```

#### <a name="-lt"></a>-lt

Beskrivning: mindre än.

Exempel:

```powershell

PS> 8 -lt 6
False

PS> 7, 8, 9 -lt 8
7
```

#### <a name="-le"></a>-Le

Beskrivning: mindre än eller lika med.

Exempel:

```powershell
PS> 6 -le 8
True

PS> 7, 8, 9 -le 8
7
8
```

### <a name="matching-operators"></a>Matchande operatorer

Operatorerna like ( `-like` och `-notlike` ) hittar element som matchar eller inte matchar ett angivet mönster med jokertecken.

Syntax:

```powershell
<string[]> -like <wildcard-expression>
<string[]> -notlike <wildcard-expression>
```

Matchnings operatorerna ( `-match` och `-notmatch` ) söker efter element som matchar eller inte matchar ett angivet mönster med hjälp av reguljära uttryck.

Match operatorerna fyller den `$Matches` automatiska variabeln när indatamängden (det vänstra argumentet) till operatorn är ett enda skalärt objekt. När invärdet är skalärt `-match` , `-notmatch` returnerar operatorn och det booleska värdet och anger värdet för den `$Matches` automatiska variabeln till de matchade komponenterna i argumentet.

Syntax:

```powershell
<string[]> -match <regular-expression>
<string[]> -notmatch <regular-expression>
```

#### <a name="-like"></a>– som

Beskrivning: matcha med jokertecknet ( \* ).

Exempel:

```powershell
PS> "PowerShell" -like "*shell"
True

PS> "PowerShell", "Server" -like "*shell"
PowerShell
```

#### <a name="-notlike"></a>-notlike

Beskrivning: överensstämmer inte med jokertecknet ( \* ).

Exempel:

```powershell
PS> "PowerShell" -notlike "*shell"
False

PS> "PowerShell", "Server" -notlike "*shell"
Server
```

### <a name="-match"></a>-matcha

Beskrivning: matchar en sträng med hjälp av reguljära uttryck. När indatatypen är skalär, fylls den `$Matches` automatiska variabeln i.

Om indatamängden är en samling, `-match` `-notmatch` returnerar operatorn och de matchande medlemmarna i samlingen, men operatorn fyller inte `$Matches` variabeln.

Följande kommando skickar till exempel en samling med strängar till `-match` operatorn. `-match`Operatorn returnerar objekten i den samling som matchar. Den automatiska variabeln fylls inte i `$Matches` .

```powershell
PS> "Sunday", "Monday", "Tuesday" -match "sun"
Sunday

PS> $Matches
PS>
```

Följande kommando skickar däremot en enskild sträng till `-match` operatorn. `-match`Operatorn returnerar ett booleskt värde och fyller den `$Matches` automatiska variabeln. Den `$Matches` automatiska variabeln är en **hash** -variabel. Om ingen gruppering eller hämtning används, fylls bara en nyckel i.
`0`Nyckeln representerar all text som matchades. Mer information om gruppering och insamling av reguljära uttryck finns [about_Regular_Expressions](about_Regular_Expressions.md).

```powershell
PS> "Sunday" -match "sun"
True

PS> $Matches

Name                           Value
----                           -----
0                              Sun
```

Det är viktigt att notera att hash-tabellen `$Matches` bara innehåller den första förekomsten av eventuella matchande mönster.

```powershell
PS> "Banana" -match "na"
True

PS> $Matches

Name                           Value
----                           -----
0                              na
```

> [!IMPORTANT]
> `0`Nyckeln är ett **heltal**. Du kan använda valfri **hash** -Metod för att komma åt värdet som lagras.
>
> ```powershell
> PS> "Good Dog" -match "Dog"
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

`-notmatch`Operatorn fyller den `$Matches` automatiska variabeln när indatatypen är skalär och resultatet är falskt, det vill säga när en matchning upptäcks.

```powershell
PS> "Sunday" -notmatch "rain"
True

PS> $matches
PS>

PS> "Sunday" -notmatch "day"
False

PS> $matches

Name                           Value
----                           -----
0                              day
```

#### <a name="-notmatch"></a>-notmatch

Beskrivning: matchar inte en sträng. Använder reguljära uttryck. När indatatypen är skalär, fylls den `$Matches` automatiska variabeln i.

Exempel:

```powershell
PS> "Sunday" -notmatch "sun"
False

PS> $matches
Name Value
---- -----
0    sun

PS> "Sunday", "Monday" -notmatch "sun"
Monday
```

### <a name="containment-operators"></a>Inne slutnings operatorer

Inne slutnings operatorerna ( `-contains` och `-notcontains` ) liknar likhets operatorerna. Däremot returnerar inne slutnings operatorer alltid ett booleskt värde, även om indatatypen är en samling.

Till skillnad från likhets operatorerna returnerar inne slutnings operatorerna ett värde så fort de identifierar den första matchningen. Likhets operatorerna utvärderar alla indatatyper och returnerar sedan alla träffar i samlingen.

#### <a name="-contains"></a>– innehåller

Beskrivning: inne slutnings operator. Anger om en samling med referens värden innehåller ett enda testvärde. Returnerar alltid ett booleskt värde. Returnerar sant endast om testvärdet exakt matchar minst ett av referensvärdena.

När testvärdet är en samling använder operatorn referens likhet. Den returnerar endast TRUE när ett av referensvärdena är samma instans av objektet test värde.

I en mycket stor samling `-contains` returnerar operatorn snabbare resultat än operatorn lika med.

Syntax:

`<Reference-values> -contains <Test-value>`

Exempel:

```powershell
PS> "abc", "def" -contains "def"
True

PS> "Windows", "PowerShell" -contains "Shell"
False  #Not an exact match

# Does the list of computers in $DomainServers include $ThisComputer?
PS> $DomainServers -contains $thisComputer
True

PS> "abc", "def", "ghi" -contains "abc", "def"
False

PS> $a = "abc", "def"
PS> "abc", "def", "ghi" -contains $a
False
PS> $a, "ghi" -contains $a
True
```

#### <a name="-notcontains"></a>-notcontains

Beskrivning: inne slutnings operator. Anger om en samling med referens värden innehåller ett enda testvärde. Returnerar alltid ett booleskt värde. Returnerar sant när testvärdet inte är en exakt matchning för minst ett av referens värden.

När testvärdet är en samling använder NotContains-operatorn referens likhet.

Syntax:

`<Reference-values> -notcontains <Test-value>`

Exempel:

```powershell
PS> "Windows", "PowerShell" -notcontains "Shell"
True  #Not an exact match

# Get cmdlet parameters, but exclude common parameters
function get-parms ($cmdlet)
{
    $Common = "Verbose", "Debug", "WarningAction", "WarningVariable",
      "ErrorAction", "ErrorVariable", "OutVariable", "OutBuffer"

    $allparms = (Get-Command $Cmdlet).parametersets |
      foreach {$_.Parameters} |
        foreach {$_.Name} | Sort-Object | Get-Unique

    $allparms | where {$Common -notcontains $_ }
}

# Find unapproved verbs in the functions in my module
PS> $ApprovedVerbs = Get-Verb | foreach {$_.verb}
PS> $myVerbs = Get-Command -Module MyModule | foreach {$_.verb}
PS> $myVerbs | where {$ApprovedVerbs -notcontains $_}
ForEach
Sort
Tee
Where
```

#### <a name="-in"></a>– in

Beskrivning: i-Operator. Anger om ett testvärde visas i en samling med referens värden. Returnera alltid som booleskt värde. Returnerar sant endast om testvärdet exakt matchar minst ett av referensvärdena.

När testvärdet är en samling använder operatorn i referens likhet.
Den returnerar endast TRUE när ett av referensvärdena är samma instans av objektet test värde.

`-in`Operatorn introducerades i PowerShell 3,0.

Syntax:

`<Test-value> -in <Reference-values>`

Exempel:

```powershell
PS> "def" -in "abc", "def"
True

PS> "Shell" -in "Windows", "PowerShell"
False  #Not an exact match

PS> "Windows" -in "Windows", "PowerShell"
True  #An exact match

PS> "Windows", "PowerShell" -in "Windows", "PowerShell", "ServerManager"
False  #Using reference equality

PS> $a = "Windows", "PowerShell"
PS> $a -in $a, "ServerManager"
True  #Using reference equality

# Does the list of computers in $DomainServers include $ThisComputer?
PS> $thisComputer -in  $domainServers
True
```

#### <a name="-notin"></a>-notin

Beskrivning: anger om ett testvärde visas i en samling med referens värden. Returnerar alltid ett booleskt värde. Returnerar sant när testvärdet inte är en exakt matchning för minst ett av referens värden.

När testvärdet är en samling använder operatorn i referens likhet.
Den returnerar endast TRUE när ett av referensvärdena är samma instans av objektet test värde.

`-notin`Operatorn introducerades i PowerShell 3,0.

Syntax:

`<Test-value> -notin <Reference-values>`

Exempel:

```powershell
PS> "def" -notin "abc", "def"
False

PS> "ghi" -notin "abc", "def"
True

PS> "Shell" -notin "Windows", "PowerShell"
True  #Not an exact match

PS> "Windows" -notin "Windows", "PowerShell"
False  #An exact match

# Find unapproved verbs in the functions in my module
PS> $ApprovedVerbs = Get-Verb | foreach {$_.verb}
PS> $MyVerbs = Get-Command -Module MyModule | foreach {$_.verb}

PS> $MyVerbs | where {$_ -notin $ApprovedVerbs}
ForEach
Sort
Tee
Where
```

### <a name="replacement-operator"></a>Ersättnings operatör

`-replace`Operatorn ersätter hela eller delar av ett värde med det angivna värdet med hjälp av reguljära uttryck. Du kan använda `-replace` operatorn för många administrativa uppgifter, till exempel att byta namn på filer. Följande kommando ändrar till exempel fil namns tilläggen för alla txt-filer till. log:

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.name -replace '\.txt$','.log' }
```

`-replace`Operatorns syntax är följande, där `<original>` plats hållaren representerar de tecken som ska ersättas och `<substitute>` plats hållaren representerar de tecken som ersätter dem:

`<input> <operator> <original>, <substitute>`

Som standard `-replace` är operatorn Skift läges okänslig. Använd för att göra det Skift läges känsligt `-creplace` . Använd om du vill göra det uttryckligen Skift läges okänsligt `-ireplace` .

Överväg följande exempel:

```powershell
PS> "book" -replace "B", "C"
```

```Output
Cook
```

```powershell
"book" -ireplace "B", "C"
```

```Output
Cook
```

```powershell
"book" -creplace "B", "C"
```

```Output
book
```

Det går också att använda reguljära uttryck för att dynamiskt ersätta text med hjälp av insamlings grupper och ersättningar. Mer information finns i [about_Regular_Expressions](about_Regular_Expressions.md).

### <a name="scriptblock-substitutions"></a>Script block ersättningar

Från och med PowerShell 6 kan du använda ett **script block** -argument för *ersättnings* texten. **Script block** körs för varje matchning som hittades i *Indatasträngen* .

I **script block** använder du den `$_` automatiska variabeln för att referera till det aktuella **systemet. text. RegularExpressions. match** -objektet. **Match** -objektet ger dig åtkomst till den aktuella inmatade texten som ersätts samt annan användbar information.

Det här exemplet ersätter varje sekvens med tre decimaler med motsvarande tecken. **Script block** körs för varje uppsättning av tre decimaler som måste ersättas.

```powershell
PS> "072101108108111" -replace "\d{3}", {[char][int]$_.Value}
Hello
```

### <a name="type-comparison"></a>Typ jämförelse

Typ jämförelse operatorer ( `-is` och `-isnot` ) används för att avgöra om ett objekt är en speciell typ.

#### <a name="-is"></a>-är

Syntax:

`<object> -is <type reference>`

Exempel:

```powershell
PS> $a = 1
PS> $b = "1"
PS> $a -is [int]
True
PS> $a -is $b.GetType()
False
```

#### <a name="-isnot"></a>– IsNot

Syntax:

`<object> -isnot <type reference>`

Exempel:

```powershell
PS> $a = 1
PS> $b = "1"
PS> $a -isnot $b.GetType()
True
PS> $b -isnot [int]
True
```

## <a name="see-also"></a>SE ÄVEN

- [about_Operators](about_Operators.md)
- [about_Regular_Expressions](about_Regular_Expressions.md)
- [about_Wildcards](about_Wildcards.md)
- [Jämför objekt](xref:Microsoft.PowerShell.Utility.Compare-Object)
- [-Objekt](xref:Microsoft.PowerShell.Core.ForEach-Object)
- [Where-objekt](xref:Microsoft.PowerShell.Core.Where-Object)
