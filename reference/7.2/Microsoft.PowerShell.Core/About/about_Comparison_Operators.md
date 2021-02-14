---
description: Beskriver de operatorer som jämför värden i PowerShell.
Locale: en-US
ms.date: 01/20/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_comparison_operators?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Comparison_Operators
ms.openlocfilehash: 2ccd631083ddc06d25f2c3b4733223cca2e89d44
ms.sourcegitcommit: 77f6225ab0c8ea9faa1fe46b2ea15c178ec170e3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/14/2021
ms.locfileid: "100500254"
---
# <a name="about-comparison-operators"></a>Om jämförelse operatorer

## <a name="short-description"></a>Kort beskrivning

Jämförelse operatorerna i PowerShell kan antingen jämföra två värden eller filtrera element i en samling mot ett indatavärde.

## <a name="long-description"></a>Lång beskrivning

Med jämförelse operatorer kan du jämföra värden eller hitta värden som matchar angivna mönster. PowerShell innehåller följande jämförelse operatorer:

|    Typ     |   Operator   |              Jämförelse test              |
| ----------- | ------------ | ----------------------------------------- |
| Likhet    | -EQ          | lika med                                    |
|             | -Ne          | inte lika med                                |
|             | -gt          | större än                              |
|             | -ge          | större än eller lika med                     |
|             | -lt          | mindre än                                 |
|             | -Le          | mindre än eller lika med                        |
| Matching    | – som        | sträng matchar mönster för jokertecken           |
|             | -notlike     | strängen matchar inte mönstret jokertecken    |
|             | -matcha       | sträng matchar regex-mönster              |
|             | -notmatch    | strängen matchar inte regex-mönstret       |
| Ny funktion | -Ersätt     | ersätter strängar som matchar ett regex-mönster |
| Behållare | – innehåller    | samlingen innehåller ett värde               |
|             | -notcontains | samlingen innehåller inget värde       |
|             | – in          | värdet finns i en samling                  |
|             | -notin       | värdet finns inte i en samling              |
| Typ        | -är          | båda objekten är av samma typ            |
|             | – IsNot       | objekten är inte av samma typ         |

## <a name="common-features"></a>Vanliga funktioner

Som standard är alla jämförelse operatorer Skift läges känsliga. Om du vill göra en jämförelse operator Skift läges känslig, lägger du till en `c` efter `-` . Till exempel `-ceq` är den Skift läges känsliga versionen av `-eq` . Om du vill göra Skift läges känsligheten lägger du till ett `i` före `-` . Till exempel `-ieq` är den uttryckligen Skift läges känsliga versionen av `-eq` .

När indatamängden för en operator är ett skalärt värde returnerar operatorn ett **booleskt** värde. När indatatypen är en samling returnerar operatorn elementen i den samling som matchar det högra värdet för uttrycket.
Om det inte finns några matchningar i samlingen returnerar jämförelse operatorer en tom matris. Exempel:

```powershell
$a = (1, 2 -eq 3)
$a.GetType().Name
$a.Count
```

```output
Object[]
0
```

Det finns några undantag:

- Operatorerna inne och Type returnerar alltid ett **booleskt** värde
- `-replace`Operatorn returnerar ersättnings resultatet
- `-match` `-notmatch` Operatorerna och fyller även i den `$Matches` automatiska variabeln

## <a name="equality-operators"></a>Likhetsoperatorer

### <a name="-eq-and--ne"></a>-EQ och-Ne

När den vänstra sidan är skalär `-eq` returnerar **True** om den högra sidan är en exakt matchning, annars `-eq` returnerar **false**. `-ne` är motsatt; den returnerar **falskt** när båda sidorna matchar; annars `-ne` returnerar true.

Exempel:

```powershell
2 -eq 2                 # Output: True
2 -eq 3                 # Output: False
"abc" -eq "abc"         # Output: True
"abc" -eq "abc", "def"  # Output: False
"abc" -ne "def"         # Output: True
"abc" -ne "abc"         # Output: False
"abc" -ne "abc", "def"  # Output: True
```

När den vänstra sidan är en samling `-eq` returnerar de medlemmar som matchar den högra sidan, medan `-ne` filtrerar dem.

Exempel:

```powershell
1,2,3 -eq 2             # Output: 2
"abc", "def" -eq "abc"  # Output: abc
"abc", "def" -ne "abc"  # Output: def
```

Dessa operatorer bearbetar alla element i samlingen. Exempel:

```powershell
"zzz", "def", "zzz" -eq "zzz"
```

```output
zzz
zzz
```

Likhets operatorerna accepterar två objekt, inte bara en skalär eller samling.
Men jämförelse resultatet är inte garanterat meningsfullt för slutanvändaren.
I följande exempel demonstreras problemet.

```powershell
class MyFileInfoSet {
    [String]$File
    [Int64]$Size
}
$a = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$b = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$a -eq $b
```

```Output
False
```

I det här exemplet har vi skapat två objekt med identiska egenskaper. Men resultatet av likhets testet är **falskt** eftersom det är olika objekt. Om du vill skapa jämförbara klasser måste du implementera [system. IEquatable \<T> ][2] i din-klass. I följande exempel demonstreras den partiella implementeringen av en **MyFileInfoSet** -klass som implementerar [system. \<T> IEquatable][2] och har två egenskaper, **fil** och **storlek**. `Equals()`Metoden returnerar true om fil-och storleks egenskaperna för två **MyFileInfoSet** -objekt är desamma.

```powershell
class MyFileInfoSet : System.IEquatable[Object] {
    [String]$File
    [Int64]$Size

    [bool] Equals([Object] $obj) {
        return ($this.File -eq $obj.File) -and ($this.Size -eq $obj.Size)
    }
}
$a = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$b = [MyFileInfoSet]@{File = "C:\Windows\explorer.exe"; Size = 4651032}
$a -eq $b
```

```Output
True
```

Ett framträdande exempel på att jämföra valfria objekt är att ta reda på om de är null. Men om du behöver avgöra om en variabel är måste `$null` du ange till `$null` vänster i likhets operatorn. Det är inte det du förväntar dig att placera det på den högra sidan.

Låt oss till exempel `$a` vara en matris som innehåller null-element:

```powershell
$a = 1, 2, $null, 4, $null, 6
```

Följande test som `$a` inte är null.

```powershell
$null -ne $a
```

```output
False
```

Följande är en fil som delar ut alla null-element från `$a` :

```powershell
$a -ne $null # Output: 1, 2, 4, 6
```

```output
1
2
4
6
```

### <a name="-gt--ge--lt-and--le"></a>-gt,-ge,-lt och-Le

`-gt`, `-ge` , `-lt` , och `-le` beter sig på samma sätt. När båda sidorna är skalära returneras **True** eller **false** beroende på hur två sidor jämför:

| Operator | Returnerar sant när...                   |
| -------- | -------------------------------------- |
| -gt      | Den vänstra sidan är större          |
| -ge      | Den vänstra sidan är större än eller lika med |
| -lt      | Den vänstra sidan är mindre          |
| -Le      | Den vänstra sidan är mindre än eller lika med |

I följande exempel returnerar alla satser True.

```powershell
8 -gt 6  # Output: True
8 -ge 8  # Output: True
6 -lt 8  # Output: True
8 -le 8  # Output: True
```

> [!NOTE]
> I de flesta programmeringsspråk är större än-operatorn större än `>` . I PowerShell används det här specialtecknet för omdirigering. Mer information finns i [about_Redirection][3].

När den vänstra sidan är en samling, jämför dessa operatörer varje medlem i samlingen med den högra sidan. Beroende på deras logik, behåller de antingen eller ignorerar medlemmen.

Exempel:

```powershell
$a=5, 6, 7, 8, 9

Write-Output "Test collection:"
$a

Write-Output "`nMembers greater than 7"
$a -gt 7

Write-Output "`nMembers greater than or equal to 7"
$a -ge 7

Write-Output "`nMembers smaller than 7"
$a -lt 7

Write-Output "`nMembers smaller than or equal to 7"
$a -le 7
```

```output
Test collection:
5
6
7
8
9

Members greater than 7
8
9

Members greater than or equal to 7
7
8
9

Members smaller than 7
5
6

Members smaller than or equal to 7
5
6
7
```

Dessa operatörer fungerar med alla klasser som implementerar [system. IComparable][1].

Exempel:

```powershell
# Date comparison
[DateTime]'2001-11-12' -lt [DateTime]'2020-08-01' # True

# Sorting order comparison
'a' -lt 'z'           # True; 'a' comes before 'z'
'macOS' -ilt 'MacOS'  # False
'MacOS' -ilt 'macOS'  # False
'macOS' -clt 'MacOS'  # True; 'm' comes before 'M'
```

Följande exempel visar att det inte finns någon symbol på ett amerikanskt QWERTY-tangentbord som sorteras efter "a". Den matas en uppsättning som innehåller alla sådana symboler till `-gt` operatorn för att jämföra dem mot "a". Utdata är en tom matris.

```powershell
$a=' ','`','~','!','@','#','$','%','^','&','*','(',')','_','+','-','=',
   '{','}','[',']',':',';','"','''','\','|','/','?','.','>',',','<'
$a -gt 'a'
# Output: Nothing
```

Om de två sidorna av operatörerna inte är rimligen jämförbara, genererar dessa operatörer ett icke-avslutande fel.

## <a name="matching-operators"></a>Matchande operatorer

Matchande operatorer ( `-like` , `-notlike` , `-match` och `-notmatch` ) hittar element som matchar eller inte matchar ett angivet mönster. Mönstret för `-like` och `-notlike` är ett jokertecken (som innehåller `*` , `?` , och `[ ]` ), `-match` och `-notmatch` accepterar ett reguljärt uttryck (regex).

Syntax:

```
<string[]> -like    <wildcard-expression>
<string[]> -notlike <wildcard-expression>
<string[]> -match    <regular-expression>
<string[]> -notmatch <regular-expression>
```

När inmatade operatorer är ett skalärt värde returnerar de ett **booleskt** värde. När indatatypen är en samling med värden returnerar operatörerna alla matchande medlemmar. Om det inte finns några matchningar i en samling returnerar operatörerna en tom matris.

### <a name="-like-and--notlike"></a>-like och-notlike

`-like` och `-notlike` beter sig på samma sätt som `-eq` och `-ne` , men den högra sidan kan vara en sträng som innehåller [jokertecken](about_Wildcards.md).

Exempel:

```powershell
"PowerShell" -like    "*shell"           # Output: True
"PowerShell" -notlike "*shell"           # Output: False
"PowerShell" -like    "Power?hell"       # Output: True
"PowerShell" -notlike "Power?hell"       # Output: False
"PowerShell" -like    "Power[p-w]hell"   # Output: True
"PowerShell" -notlike "Power[p-w]hell"   # Output: False

"PowerShell", "Server" -like "*shell"    # Output: PowerShell
"PowerShell", "Server" -notlike "*shell" # Output: Server
```

### <a name="-match-and--notmatch"></a>-match och-notmatch

`-match` och `-notmatch` Använd reguljära uttryck för att söka efter mönster i värdena för den vänstra sidan. Reguljära uttryck kan matcha komplexa mönster som e-postadresser, UNC-sökvägar eller formaterade telefonnummer. Den högra strängen måste följa reglerna för [reguljära uttryck](about_Regular_Expressions.md) .

Skalära exempel:

```powershell
# Partial match test, showing how differently -match and -like behave
"PowerShell" -match 'shell'        # Output: True
"PowerShell" -like  'shell'        # Output: False

# Regex syntax test
"PowerShell" -match    '^Power\w+' # Output: True
'bag'        -notmatch 'b[iou]g'   # Output: True
```

Om indatamängden är en samling returnerar operatorerna de matchande medlemmarna i samlingen.

Samlings exempel:

```powershell
"PowerShell", "Super PowerShell", "Power's hell" -match '^Power\w+'
# Output: PowerShell

"Rhell", "Chell", "Mel", "Smell", "Shell" -match "hell"
# Output: Rhell, Chell, Shell

"Bag", "Beg", "Big", "Bog", "Bug"  -match 'b[iou]g'
#Output: Big, Bog, Bug

"Bag", "Beg", "Big", "Bog", "Bug"  -notmatch 'b[iou]g'
#Output: Bag, Beg
```

`-match` och `-notmatch` stöder regex-infångnings grupper. Varje gången de körs skrivs den `$Matches` automatiska variabeln över. När `<input>` är en samling `$Matches` är variabeln `$null` . `$Matches` är en **hash** som alltid har en nyckel med namnet "0" som lagrar hela matchningen. Om det reguljära uttrycket innehåller infångnings grupper `$Matches` innehåller ytterligare nycklar för varje grupp.

Exempel:

```powershell
$string = 'The last logged on user was CONTOSO\jsmith'
$string -match 'was (?<domain>.+)\\(?<user>.+)'

$Matches

Write-Output "`nDomain name:"
$Matches.domain

Write-Output "`nUser name:"
$Matches.user
```

```output
True

Name                           Value
----                           -----
domain                         CONTOSO
user                           jsmith
0                              was CONTOSO\jsmith

Domain name:
CONTOSO

User name:
jsmith
```

Mer information finns i [about_Regular_Expressions](about_Regular_Expressions.md).

## <a name="replacement-operator"></a>Ersättnings operatör

### <a name="replacement-with-regular-expressions"></a>Ersätta med reguljära uttryck

`-match`På samma sätt `-replace` använder operatorn reguljära uttryck för att hitta det angivna mönstret. Men till skillnad från `-match` ersätter den matchningen med ett annat angivet värde.

Syntax:

```
<input> -replace <regular-expression>, <substitute>
```

Operatorn ersätter hela eller delar av ett värde med det angivna värdet med hjälp av reguljära uttryck. Du kan använda operatorn för många administrativa uppgifter, till exempel att byta namn på filer. Följande kommando ändrar till exempel fil namns tilläggen för alla `.txt` filer till `.log` :

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.name -replace '\.txt$','.log' }
```

Som standard `-replace` är operatorn Skift läges okänslig. Använd för att göra det Skift läges känsligt `-creplace` . Använd om du vill göra det uttryckligen Skift läges okänsligt `-ireplace` .

Exempel:

```powershell
"book" -ireplace "B", "C" # Case insensitive
"book" -creplace "B", "C" # Case-sensitive; hence, nothing to replace
```

```Output
Cook
book
```

### <a name="regular-expressions-substitutions"></a>Reguljära uttryck ersättningar

Det går också att använda reguljära uttryck för att dynamiskt ersätta text med hjälp av insamlings grupper och ersättningar. Det går att referera till infångnings grupper i `<substitute>` strängen med dollar tecknet ( `$` ) före grupp-ID: n.

I följande exempel `-replace` accepterar operatorn ett användar namn i formatet `DomainName\Username` och konverteras till `Username@DomainName` formatet:

```powershell
$SearchExp = '^(?<DomainName>[\w-.]+)\\(?<Username>[\w-.]+)$'
$ReplaceExp = '${Username}@${DomainName}'

'Contoso.local\John.Doe' -replace $SearchExp,$ReplaceExp
```

```output
John.Doe@Contoso.local
```

> [!WARNING]
> `$`Specialtecknet har syntatic-roller i både PowerShell-och reguljära uttryck:
>
> - I PowerShell, mellan dubbla citat tecken, anger den variabler och fungerar som en under Express operator.
> - I regex Sök strängar betecknar det slutet av raden
> - I regex-substitutions strängar anger den fångade grupper. Se till att antingen placera dina reguljära uttryck mellan enkla citat tecken eller infoga ett baktick ( `` ` `` )-tecken före.

Exempel:

```powershell
$1 = 'Goodbye'

'Hello World' -replace '(\w+) \w+', "$1 Universe"
# Output: Goodbye Universe

'Hello World' -replace '(\w+) \w+', '$1 Universe'
# Output: Hello Universe
```

`$$` i regex anger en literal `$` . Detta `$$` i ersättnings strängen som innehåller en litteral `$` i den resulterande ersättningen. Exempel:

```powershell
'5.72' -replace '(.+)', '$ $1' # Output: $ 5.72
'5.72' -replace '(.+)', '$$$1' # Output: $5.72
'5.72' -replace '(.+)', '$$1'  # Output: $1
```

Mer information finns i [about_Regular_Expressions](about_Regular_Expressions.md) och [ersättningar i reguljära uttryck][4].

### <a name="substituting-in-a-collection"></a>Ersätta i en samling

När `<input>` `-replace` operatorn till är en samling, tillämpar PowerShell ersättningen på alla värden i samlingen. Exempel:

```powershell
"B1","B2","B3","B4","B5" -replace "B", 'a'
a1
a2
a3
a4
a5
```

### <a name="replacement-with-a-script-block"></a>Ersätta med ett skript block

I PowerShell 6 och senare, `-replace` accepterar operatorn också ett skript block som utför ersättningen. Skript blocket körs en gång för varje matchning.

Syntax:

```powershell
<String> -replace <regular-expression>, {<Script-block>}
```

I-skript blocket använder du den `$_` automatiska variabeln för att få åtkomst till den inmatade text som ersätts och annan användbar information. Den här variabelns klass typ är [system. text. RegularExpressions. match][2].

I följande exempel ersätts varje sekvens med tre siffror med motsvarande tecken. Skript blocket körs för varje uppsättning av tre siffror som måste ersättas.

```powershell
"072101108108111" -replace "\d{3}", {return [char][int]$_.Value}
```

```output
Hello
```

## <a name="containment-operators"></a>Inne slutnings operatorer

Inne slutnings operatorerna ( `-contains` , `-notcontains` , `-in` och `-notin` ) liknar likhets operatorerna, förutom att de alltid returnerar ett **booleskt** värde, även när indatatypen är en samling. Dessa operatorer slutar att jämföra så fort de identifierar den första matchningen, medan likhets operatorerna utvärderar alla ingående medlemmar. I en mycket stor samling returnerar de här operatorerna snabbare än likhets operatorerna.

Syntax:

```
<Collection> -contains <Test-object>
<Collection> -notcontains <Test-object>
<Test-object> -in <Collection>
<Test-object> -notin <Collection>
```

### <a name="-contains-and--notcontains"></a>-innehåller och-notcontains

Dessa operatorer anger om en mängd innehåller ett visst element. `-contains` returnerar true när den högra sidan (test objekt) matchar ett av elementen i mängden. `-notcontains` returnerar falskt i stället. När test-objektet är en samling använder dessa operatorer referens likhet, d.v.s. de kontrollerar om en av uppsättningens element är samma instans av test-objektet.

Exempel:

```powershell
"abc", "def" -contains "def"                  # Output: True
"abc", "def" -notcontains "def"               # Output: False
"Windows", "PowerShell" -contains "Shell"     # Output: False
"Windows", "PowerShell" -notcontains "Shell"  # Output: True
"abc", "def", "ghi" -contains "abc", "def"    # Output: False
"abc", "def", "ghi" -notcontains "abc", "def" # Output: True
```

Mer komplexa exempel:

```powershell
$DomainServers = "ContosoDC1","ContosoDC2","ContosoFileServer","ContosoDNS",
                 "ContosoDHCP","ContosoWSUS"
$thisComputer  = "ContosoDC2"

$DomainServers -contains $thisComputer
# Output: True

$a = "abc", "def"
"abc", "def", "ghi" -contains $a # Output: False
$a, "ghi" -contains $a           # Output: True
```

### <a name="-in-and--notin"></a>-in-och-notin

`-in` `notin` Operatorerna och har introducerats i PowerShell 3 som omvänt i `contains` och med `-notcontain` operatorerna och. `-in` Returnerar **True** när den vänstra sidan `<test-object>` matchar ett av elementen i uppsättningen. `-notin` Returnerar **falskt** i stället. När test-objektet är en uppsättning använder dessa operatorer referens likhet för att kontrol lera om en av uppsättningens element är samma instans av test-objektet.

Följande exempel gör samma sak som exemplen för `-contain` och `-notcontain` gör, men de skrivs med `-in` och `-notin` i stället.

```powershell
"def" -in "abc", "def"                  # Output: True
"def" -notin "abc", "def"               # Output: False
"Shell" -in "Windows", "PowerShell"     # Output: False
"Shell" -notin "Windows", "PowerShell"  # Output: True
"abc", "def" -in "abc", "def", "ghi"    # Output: False
"abc", "def" -notin "abc", "def", "ghi" # Output: True
```

Mer komplexa exempel:

```powershell
$DomainServers = "ContosoDC1","ContosoDC2","ContosoFileServer","ContosoDNS",
                 "ContosoDHCP","ContosoWSUS"
$thisComputer  = "ContosoDC2"

$thisComputer -in $DomainServers
# Output: True

$a = "abc", "def"
$a -in "abc", "def", "ghi" # Output: False
$a -in $a, "ghi"           # Output: True
```

## <a name="type-comparison"></a>Typ jämförelse

Typ jämförelse operatorer ( `-is` och `-isnot` ) används för att avgöra om ett objekt är en speciell typ.

Syntax:

```powershell
<object> -is <type-reference>
<object> -isnot <type-reference>
```

Exempel:

```powershell
$a = 1
$b = "1"
$a -is [int]           # Output: True
$a -is $b.GetType()    # Output: False
$b -isnot [int]        # Output: True
$a -isnot $b.GetType() # Output: True
```

## <a name="see-also"></a>SE ÄVEN

- [about_Operators](about_Operators.md)
- [about_Regular_Expressions](about_Regular_Expressions.md)
- [about_Wildcards](about_Wildcards.md)
- [Jämför objekt](xref:Microsoft.PowerShell.Utility.Compare-Object)
- [-Objekt](xref:Microsoft.PowerShell.Core.ForEach-Object)
- [Where-objekt](xref:Microsoft.PowerShell.Core.Where-Object)

[1]: /dotnet/api/system.icomparable
[2]: /dotnet/api/system.iequatable-1
[3]: /dotnet/api/system.text.regularexpressions.match
[4]: about_Redirection.md#potential-confusion-with-comparison-operators
[5]: /dotnet/standard/base-types/substitutions-in-regular-expressions
