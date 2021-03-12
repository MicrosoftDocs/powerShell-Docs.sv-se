---
description: Beskriver hur du använder operatörer för att tilldela värden till variabler.
Locale: en-US
ms.date: 04/26/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_assignment_operators?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Assignment_Operators
ms.openlocfilehash: 469c482ea8dbf2af315ed64129b8e790b66840e4
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194557"
---
# <a name="about-assignment-operators"></a>Om tilldelnings operatörer

## <a name="short-description"></a>Kort beskrivning
Beskriver hur du använder operatörer för att tilldela värden till variabler.

## <a name="long-description"></a>Lång beskrivning

Tilldelnings operatörer tilldelar en eller flera värden till en variabel. De kan utföra numeriska åtgärder på värdena innan tilldelningen.

PowerShell har stöd för följande tilldelnings operatorer.

|Operator|Beskrivning                                                  |
|--------|-------------------------------------------------------------|
|=       |Ställer in värdet för en variabel till det angivna värdet.         |
|+=      |Ökar värdet för en variabel med det angivna värdet, eller |
|        |lägger till det angivna värdet i det befintliga värdet.           |
|-=      |Minskar värdet för en variabel med det angivna värdet.    |
|*=      |Multiplicerar värdet för en variabel med det angivna värdet, eller|
|        |lägger till det angivna värdet i det befintliga värdet.           |
|/=      |Dividerar värdet för en variabel med det angivna värdet.      |
|%=      |Dividerar värdet för en variabel med det angivna värdet och   |
|        |tilldelar sedan resten (Modulus) till variabeln.        |
|++      |Ökar värdet för en variabel, tilldelnings bara egenskap eller   |
|        |mat ris element med 1.                                          |
|--      |Minskar värdet för en variabel, tilldelnings bara egenskap eller   |
|        |mat ris element med 1.                                          |

## <a name="syntax"></a>Syntax

Syntaxen för tilldelnings operatörerna är följande:

`<assignable-expression>` `<assignment-operator>` `<value>`

Tilldelnings bara uttryck innehåller variabler och egenskaper. Värdet kan vara ett enskilt värde, en matris med värden eller ett kommando, ett uttryck eller en instruktion.

Operatorerna öka och minska är unära operatorer. Varje har prefix-och postfix-versioner.

`<assignable-expression><operator>`
`<operator><assignable-expression>`

Det tilldelnings bara uttrycket måste vara ett tal eller konvertera det till ett tal.

## <a name="assigning-values"></a>Tilldela värden

Variabler är namngivna minnes utrymmen som lagrar värden. Du lagrar värdena i variablerna med hjälp av tilldelnings operatorn `=` . Det nya värdet kan ersätta det befintliga värdet för variabeln, eller så kan du lägga till ett nytt värde till det befintliga värdet.

Den grundläggande tilldelnings operatorn är likhets tecknet `=` `(ASCII 61)` . Följande-sats tilldelar exempelvis värdet PowerShell till `$MyShell` variabeln:

```powershell
$MyShell = "PowerShell"
```

När du tilldelar ett värde till en variabel i PowerShell skapas variabeln om den inte redan finns. Till exempel skapar den första av följande två tilldelnings uttryck `$a` variabeln och tilldelar värdet 6 till `$a` . Den andra tilldelnings instruktionen tilldelar värdet 12 till `$a` . Den första instruktionen skapar en ny variabel. Den andra instruktionen ändrar bara dess värde:

```powershell
$a = 6
$a = 12
```

Variabler i PowerShell har inte någon speciell datatyp om du inte skickar dem.
När en variabel bara innehåller ett objekt, använder variabeln data typen för objektet. När en variabel innehåller en samling av objekt, har variabeln system. Object-datatyp. Därför kan du tilldela valfri typ av objekt till samlingen. I följande exempel visas att du kan lägga till process objekt, service objekt, strängar och heltal till en variabel utan att generera ett fel:

```powershell
$a = Get-Process
$a += Get-Service
$a += "string"
$a += 12
```

Eftersom tilldelnings operatorn `=` har lägre prioritet än pipeline-operatorn `|` , behöver parenteser inte tilldela resultatet av en kommando pipeline till en variabel. Följande kommando sorterar till exempel tjänsterna på datorn och tilldelar sedan de sorterade tjänsterna till `$a` variabeln:

```powershell
$a = Get-Service | Sort-Object -Property name
```

Du kan också tilldela värdet som skapats av en instruktion till en variabel, som i följande exempel:

```powershell
$a = if ($b -lt 0) { 0 } else { $b }
```

I det här exemplet tilldelas `$a` variabeln noll till variabeln om värdet för `$b` är mindre än noll. Det tilldelar värdet `$b` till `$a` om värdet `$b` inte är mindre än noll.

### <a name="the-assignment-operator"></a>Tilldelnings operatorn

Tilldelnings operatorn `=` tilldelar värden till variabler. Om variabeln redan har ett värde ersätter tilldelnings operatorn `=` värdet utan varning.

Följande instruktion tilldelar heltal svärdet 6 till `$a` variabeln:

```powershell
$a = 6
```

Om du vill tilldela ett sträng värde till en variabel, omger du strängvärdet med citat tecken enligt följande:

```powershell
$a = "baseball"
```

Om du vill tilldela en matris (flera värden) till en variabel separerar du värdena med kommatecken enligt följande:

```powershell
$a = "apple", "orange", "lemon", "grape"
```

Om du vill tilldela en hash-tabell till en variabel använder du standard-hash-format i PowerShell. Skriv ett at-tecken `@` följt av nyckel/värde-par som skiljs åt av semikolon `;` och omges av klammerparenteser `{ }` . Om du till exempel vill tilldela en hash-tabell till `$a` variabeln skriver du:

```powershell
$a = @{one=1; two=2; three=3}
```

Om du vill tilldela hexadecimala värden till en variabel, skriver du in före värdet med `0x` .
PowerShell konverterar det hexadecimala värdet (0x10) till ett Decimal värde (i det här fallet 16) och tilldelar värdet till `$a` variabeln. Om du till exempel vill tilldela värdet 0x10 till `$a` variabeln skriver du:

```powershell
$a = 0x10
```

Om du vill tilldela en variabel ett exponentiellt värde anger du rot numret, bokstaven `e` och ett tal som representerar en multipel av 10. Om du till exempel vill tilldela värdet 3,1415 till kraften hos 1 000 till `$a` variabeln skriver du:

```powershell
$a = 3.1415e3
```

PowerShell kan också konvertera kilobyte `KB` , megabyte `MB` och gigabyte `GB` i byte. Om du till exempel vill tilldela värdet 10 kilobyte till `$a` variabeln, skriver du:

```powershell
$a = 10kb
```

### <a name="the-assignment-by-addition-operator"></a>Operatorn tilldelning efter tillägg

Operatorn för tilldelning efter addition `+=` ökar antingen värdet för en variabel eller lägger till det angivna värdet i det befintliga värdet. Åtgärden beror på om variabeln har en numerisk typ eller sträng typ och om variabeln innehåller ett enda värde (en skalär) eller flera värden (en samling).

`+=`Operatorn kombinerar två åtgärder. Först läggs den till och tilldelas sedan.
Därför är följande uttryck likvärdiga:

```powershell
$a += 2
$a = ($a + 2)
```

När variabeln innehåller ett enkelt numeriskt värde `+=` ökar operatorn det befintliga värdet med summan till höger om operatorn. Sedan tilldelar operatorn resultatvärdet värdet till variabeln. I följande exempel visas hur du använder `+=` operatorn för att öka värdet för en variabel:

```powershell
$a = 4
$a += 2
$a
```

```
6
```

När värdet för variabeln är en sträng, läggs värdet på höger sida av operatorn till i strängen enligt följande:

```powershell
$a = "Windows"
$a += " PowerShell"
$a
```

```
Windows PowerShell
```

När värdet för variabeln är en matris, `+=` lägger operatorn till värdena på höger sida av operatorn i matrisen. Om inte matrisen anges explicit genom databyte, kan du lägga till valfri typ av värde i matrisen enligt följande:

```powershell
$a = 1,2,3
$a += 2
$a
```

```
1
2
3
2
```

och

```powershell
$a += "String"
$a
```

```
1
2
3
2
String
```

När värdet för en variabel är en hash-tabell, `+=` lägger operatorn till värdet på höger sida av operatorn i hash-tabellen. Men eftersom den enda typ som du kan lägga till i en hash-tabell är en annan hash-tabell, så går det inte att utföra andra tilldelningar.

Följande kommando tilldelar till exempel en hash-tabell till `$a` variabeln.
Sedan använder den `+=` operatorn för att lägga till en annan hash-tabell i den befintliga hash-tabellen, vilket effektivt lägger till ett nytt nyckel/värde-par i den befintliga hash-tabellen.
Det här kommandot slutförs, som visas i utdata:

```powershell
$a = @{a = 1; b = 2; c = 3}
$a += @{mode = "write"}
$a
```

```
Name                           Value
----                           -----
a                              1
b                              2
mode                           write
c                              3
```

Följande kommando försöker lägga till ett heltal "1" till hash-tabellen i `$a` variabeln. Detta kommando Miss lyckas:

```powershell
$a = @{a = 1; b = 2; c = 3}
$a += 1
```

```
You can add another hash table only to a hash table.
At line:1 char:6
+ $a += <<<<  1
```

### <a name="the-assignment-by-subtraction-operator"></a>Tilldelningen efter subtraktion-operator

Tilldelningen av subtraktion-operatorn `-=` utvärderar värdet för en variabel med det värde som anges på höger sida av operatorn. Det går inte att använda den här operatorn med String-variabler och den kan inte användas för att ta bort ett element från en samling.

`-=`Operatorn kombinerar två åtgärder. Först subtraheras den och tilldelas sedan. Därför är följande uttryck likvärdiga:

```powershell
$a -= 2
$a = ($a - 2)
```

I följande exempel visas hur du använder `-=` operatorn för att minska värdet för en variabel:

```powershell
$a = 8
$a -= 2
$a
```

```
6
```

Du kan också använda `-=` operatorn tilldelning för att minska värdet för en medlem i en numerisk matris. Det gör du genom att ange indexet för det mat ris element som du vill ändra. I följande exempel minskas värdet för det tredje elementet i en matris (element 2) med 1:

```powershell
$a = 1,2,3
$a[2] -= 1
$a
```

```
1
2
2
```

Du kan inte använda `-=` operatorn för att ta bort värdena för en variabel. Om du vill ta bort alla värden som har tilldelats en variabel använder du cmdletarna [Clear-item](xref:Microsoft.PowerShell.Management.Clear-Item) eller [Clear-Variable](xref:Microsoft.PowerShell.Utility.Clear-Variable) för att tilldela värdet `$null` eller `""` variabeln.

```powershell
$a = $null
```

Om du vill ta bort ett visst värde från en matris använder du Array-notation för att tilldela ett värde `$null` till ett visst objekt. Följande uttryck tar till exempel bort det andra värdet (index position 1) från en matris:

```powershell
$a = 1,2,3
$a
```

```
1
2
3
```

```powershell
$a[1] = $null
$a
```

```
1
3
```

Om du vill ta bort en variabel använder du cmdleten [Remove-Variable](xref:Microsoft.PowerShell.Utility.Remove-Variable) . Den här metoden är användbar när variabeln uttryckligen omvandlas till en viss datatyp och du vill ha en variabel som inte har angetts. Följande kommando tar bort `$a` variabeln:

```powershell
Remove-Variable -Name a
```

### <a name="the-assignment-by-multiplication-operator"></a>Operatorn tilldelning efter multiplikation

Operatorn tilldelning av multiplikation `*=` multiplicerar ett numeriskt värde eller lägger till det angivna antalet kopior av strängvärdet för en variabel.

När en variabel innehåller ett enkelt numeriskt värde multipliceras värdet med värdet till höger om operatorn. I följande exempel visas exempelvis hur du använder `*=` operatorn för att multiplicera värdet för en variabel:

```powershell
$a = 3
$a *= 4
$a
```

```
12
```

I det här fallet `*=` kombinerar operatorn två åtgärder. Först, den multipliceras och tilldelas sedan. Därför är följande uttryck likvärdiga:

```powershell
$a *= 2
$a = ($a * 2)
```

När en variabel innehåller ett sträng värde lägger PowerShell till det angivna antalet strängar till värdet enligt följande:

```powershell
$a = "file"
$a *= 4
$a
```

```
filefilefilefile
```

Om du vill multiplicera ett element i en matris använder du ett index för att identifiera det element som du vill multiplicera. Följande kommando multiplicerar exempelvis det första elementet i matrisen (index position 0) med 2:

```powershell
$a[0] *= 2
```

### <a name="the-assignment-by-division-operator"></a>Operatorn tilldelning efter avdelning

Operatorn tilldelning efter Division `/=` delar ett numeriskt värde med det värde som anges på höger sida av operatorn. Det går inte att använda operatorn med String-variabler.

`/=`Operatorn kombinerar två åtgärder. Först delas den upp och tilldelas sedan. Därför är följande två uttryck likvärdiga:

```powershell
$a /= 2
$a = ($a / 2)
```

Följande kommando använder exempelvis `/=` operatorn för att dividera värdet för en variabel:

```powershell
$a = 8
$a /=2
$a
```

```
4
```

Om du vill dela upp ett element i en matris använder du ett index för att identifiera det element som du vill ändra. Följande kommando delar till exempel det andra elementet i matrisen (index position 1) med 2:

```powershell
$a[1] /= 2
```

### <a name="the-assignment-by-modulus-operator"></a>Operatorn tilldelning efter modul

Operatorn tilldelning efter modul `%=` delar värdet för en variabel med värdet till höger om operatorn. Sedan `%=` tilldelar operatorn resten (kallas Modulus) till variabeln. Du kan bara använda den här operatorn när en variabel innehåller ett enkelt numeriskt värde. Du kan inte använda den här operatorn när en variabel innehåller en sträng variabel eller en matris.

`%=`Operatorn kombinerar två åtgärder. Först delar den upp och avgör resten och tilldelar sedan resten till variabeln. Därför är följande uttryck likvärdiga:

```powershell
$a %= 2
$a = ($a % 2)
```

I följande exempel visas hur du använder `%=` operatorn för att spara Modulus av en kvot:

```powershell
$a = 7
$a %= 4
$a
```

```
3
```

## <a name="the-increment-and-decrement-operators"></a>Operatorerna öka och minska

Operatorn Increment `++` ökar värdet för en variabel med 1. När du använder operatorn Increment i en enkel instruktion returneras inget värde. Visa resultatet genom att visa värdet för variabeln enligt följande:

```powershell
$a = 7
++$a
$a
```

```
8
```

Om du vill tvinga fram ett värde som ska returneras omger du variabeln och operatorn inom parentes enligt följande:

```powershell
$a = 7
(++$a)
```

```
8
```

Operatorn Increment kan placeras före (prefix) eller efter (postfix) en variabel. Prefixlängden för operatorn ökar en variabel innan dess värde används i instruktionen enligt följande:

```powershell
$a = 7
$c = ++$a
$a
```

```
8
```

```powershell
$c
```

```
8
```

Postfix-versionen av operatorn ökar en variabel när dess värde används i instruktionen. I följande exempel `$c` `$a` har variablerna och samma värden, eftersom värdet tilldelas `$c` innan `$a` ändringar:

```powershell
$a = 7
$c = $a++
$a
```

```
8
```

```powershell
$c
```

```
7
```

Operatorn minska `--` minskar värdet för en variabel med 1. Precis som med operatorn Increment returneras inget värde när du använder operatorn i en enkel instruktion. Använd parenteser för att returnera ett värde enligt följande:

```powershell
$a = 7
--$a
$a
```

```
6
```

```powershell
(--$a)
```

```
5
```

Prefixlängden för operatorn minskar en variabel innan dess värde används i instruktionen enligt följande:

```powershell
$a = 7
$c = --$a
$a
```

```
6
```

```powershell
$c
```

```
6
```

Postfix-versionen av operatorn minskar en variabel när dess värde används i instruktionen. I följande exempel `$d` `$a` har variablerna och samma värden, eftersom värdet tilldelas `$d` innan `$a` ändringar:

```powershell
$a = 7
$d = $a--
$a
```

```
6
```

```powershell
$d
```

```
7
```

## <a name="microsoft-net-framework-types"></a>Microsoft .NET Ramverks typer

Som standard när en variabel bara har ett värde, bestämmer värdet som tilldelas variabeln data typen för variabeln. Följande kommando skapar till exempel en variabel som har typen "Integer" (system. Int32):

```powershell
$a = 6
```

Om du vill hitta .NET Framework typen för en variabel använder du **gettype** -metoden och dess **FullName** -egenskap enligt följande. Se till att ta med parenteserna efter namnet på **gettype** -metoden, även om metod anropet inte har några argument:

```powershell
$a = 6
$a.GetType().FullName
```

```
System.Int32
```

Om du vill skapa en variabel som innehåller en sträng tilldelar du ett sträng värde till variabeln. Om du vill ange att värdet är en sträng omger du det med citat tecken enligt följande:

```powershell
$a = "6"
$a.GetType().FullName
```

```
System.String
```

Om det första värdet som är kopplat till variabeln är en sträng behandlar PowerShell alla åtgärder som sträng åtgärder och skickar nya värden till strängar.
Detta inträffar i följande exempel:

```powershell
$a = "file"
$a += 3
$a
```

```
file3
```

Om det första värdet är ett heltal behandlar PowerShell alla åtgärder som heltals åtgärder och skickar nya värden till heltal. Detta inträffar i följande exempel:

```powershell
$a = 6
$a += "3"
$a
```

```
9
```

Du kan omvandla en ny skalär variabel som vilken .NET Framework typ som helst genom att placera namnet inom hak paren tes före antingen variabel namnet eller det första tilldelning svärdet. När du kastar en variabel kan du bestämma vilka typer av data som kan lagras i variabeln. Du kan också bestämma hur variabeln beter sig när du ändrar den.

Följande kommando skickar exempelvis variabeln som en sträng typ:

```powershell
[string]$a = 27
$a += 3
$a
```

```
273
```

I följande exempel skickas det första värdet i stället för att omvandla variabeln:

```powershell
$a = [string]27
```

När du skickar en variabel till en speciell typ är den gemensamma konventionen att omvandla variabeln, inte värdet. Du kan dock inte omkonvertera data typen för en befintlig variabel om dess värde inte kan konverteras till den nya data typen. Om du vill ändra data typen måste du ersätta dess värde enligt följande:

```powershell
$a = "string"
[int]$a
```

```
Cannot convert value "string" to type "System.Int32". Error: "Input string was
not in a correct format." At line:1 char:8 + [int]$a <<<<
```

```powershell
[int]$a = 3
```

När du föregår ett variabel namn med en datatyp är typen av variabeln låst, såvida du inte uttryckligen åsidosätter typen genom att ange en annan datatyp. Om du försöker tilldela ett värde som är inkompatibelt med den befintliga typen, och du inte uttryckligen åsidosätter typen, visar PowerShell ett fel som visas i följande exempel:

```powershell
$a = 3
$a = "string"
[int]$a = 3
$a = "string"
```

```
Cannot convert value "string" to type "System.Int32". Error: "Input
string was not in a correct format."
At line:1 char:3
+ $a <<<<  = "string"
```

```powershell
[string]$a = "string"
```

I PowerShell hanteras data typerna för variabler som innehåller flera objekt i en matris på olika sätt från data typerna för variabler som innehåller ett enda objekt. Om inte en datatyp specifikt tilldelas en mat ris variabel är data typen alltid `System.Object []` . Den här data typen är speciell för matriser.

Ibland kan du åsidosätta standard typen genom att ange en annan typ. Följande kommando skickar exempelvis variabeln som en `string []` mat ris typ:

```powershell
[string []] $a = "one", "two", "three"
```

PowerShell-variabler kan vara valfria .NET Framework-datatyp. Dessutom kan du tilldela en fullständigt kvalificerad .NET Framework-datatyp som är tillgänglig i den aktuella processen. Följande kommando anger till exempel en `System.DateTime` datatyp:

```powershell
[System.DateTime]$a = "5/31/2005"
```

Variabeln tilldelas ett värde som överensstämmer med `System.DateTime` data typen. Värdet för `$a` variabeln skulle vara följande:

```
Tuesday, May 31, 2005 12:00:00 AM
```

## <a name="assigning-multiple-variables"></a>Tilldela flera variabler

I PowerShell kan du tilldela värden till flera variabler genom att använda ett enda kommando. Det första elementet i tilldelning svärdet tilldelas den första variabeln, det andra elementet tilldelas till den andra variabeln, det tredje elementet till den tredje variabeln och så vidare. Följande kommando tilldelar till exempel värdet 1 till `$a` variabeln, värdet 2 till `$b` variabeln och värdet 3 till `$c` variabeln:

```powershell
$a, $b, $c = 1, 2, 3
```

Om tilldelning svärdet innehåller fler element än variabler, tilldelas alla återstående värden den sista variabeln. Följande kommando innehåller till exempel tre variabler och fem värden:

```powershell
$a, $b, $c = 1, 2, 3, 4, 5
```

Därför tilldelar PowerShell värdet 1 till `$a` variabeln och värdet 2 till `$b` variabeln. De tilldelar värdena 3, 4 och 5 till `$c` variabeln.
Om du vill tilldela värden i `$c` variabeln till tre andra variabler använder du följande format:

```powershell
$d, $e, $f = $c
```

Det här kommandot tilldelar värdet 3 till `$d` variabeln, värdet 4 till `$e` variabeln och värdet 5 till `$f` variabeln.

Om tilldelning svärdet innehåller färre element än variabler, tilldelas inte alla återstående variabler i slutet några värden. Följande kommando innehåller till exempel tre variabler och två värden:

```powershell
$a, $b, $c = 1, 2
```

Därför tilldelar PowerShell värdet 1 till `$a` variabeln och värdet 2 till `$b` variabeln. Det tilldelar inget värde till `$c` variabeln.

Du kan också tilldela ett enskilt värde till flera variabler genom att länka variablerna. Följande kommando tilldelar till exempel värdet "tre" till alla fyra variabler:

```powershell
$a = $b = $c = $d = "three"
```

## <a name="variable-related-cmdlets"></a>Variabla-relaterade cmdletar

Förutom att använda en tilldelnings åtgärd för att ange ett variabel värde kan du också använda cmdleten [set-Variable](xref:Microsoft.PowerShell.Utility.Set-Variable) . Följande kommando använder `Set-Variable` till exempel för att tilldela en matris med 1, 2, 3 till `$a` variabeln.

```powershell
Set-Variable -Name a -Value 1, 2, 3
```

## <a name="see-also"></a>Se även

[about_Arrays](about_Arrays.md)

[about_Hash_Tables](about_Hash_Tables.md)

[about_Variables](about_Variables.md)

[Clear-Variable](xref:Microsoft.PowerShell.Utility.Clear-Variable)

[Ta bort variabel](xref:Microsoft.PowerShell.Utility.Remove-Variable)

[Set-Variable](xref:Microsoft.PowerShell.Utility.Set-Variable)
