---
description: Beskriver hur du skapar, använder och sorterar hash-tabeller i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/28/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_hash_tables?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Hash_Tables
ms.openlocfilehash: 2d7b886a8d36a72f789395650d1f2dd17123258c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271227"
---
# <a name="about-hash-tables"></a>Om hash-tabeller

## <a name="short-description"></a>KORT BESKRIVNING
Beskriver hur du skapar, använder och sorterar hash-tabeller i PowerShell.

## <a name="long-description"></a>LÅNG BESKRIVNING

En hash-tabell, som även kallas för ett lexikon eller en associativ matris, är en komprimerad data struktur som lagrar ett eller flera nyckel/värde-par. En hash-tabell kan till exempel innehålla en serie med IP-adresser och dator namn, där IP-adresserna är nycklarna och dator namnen är värdena eller vice versa.

I PowerShell är varje hash-tabell ett hash-objekt (system. Collections. hash). Du kan använda egenskaper och metoder för hash-objekt i PowerShell.

Från och med PowerShell 3,0 kan du använda attributet [ordnat] för att skapa en ordnad ord lista (system. Collections. specialiserad. OrderedDictionary) i PowerShell.

Ordnade ord listor skiljer sig från hash-tabeller i att nycklarna alltid visas i den ordning som du visar dem. Ordningen på nycklarna i en hash-tabell har inte fastställts.

Nycklarna och värdet i hash-tabeller är också .NET-objekt. De är oftast strängar eller heltal, men de kan ha valfri objekt typ. Du kan också skapa kapslade hash-tabeller där värdet för en nyckel är en annan hash-tabell.

Hash-tabeller används ofta eftersom de är mycket effektiva för att hitta och hämta data. Du kan använda hash-tabeller för att lagra listor och skapa beräknade egenskaper i PowerShell. Och PowerShell har en cmdlet, ConvertFrom-StringData, som konverterar strängar till en hash-tabell.

### <a name="syntax"></a>Syntax

Syntaxen för en hash-tabell är följande:

```powershell
@{ <name> = <value>; [<name> = <value> ] ...}
```

Syntaxen för en ordnad ord lista är följande:

```powershell
[ordered]@{ <name> = <value>; [<name> = <value> ] ...}
```

Attributet [ordnat] introducerades i PowerShell 3,0.

### <a name="creating-hash-tables"></a>Skapa hash-tabeller

Följ dessa rikt linjer om du vill skapa en hash-tabell:

- Starta hash-tabellen med ett at-tecken (@).
- Omge hash-tabellen med klammerparenteser ( {} ).
- Ange ett eller flera nyckel/värde-par för innehållet i hash-tabellen.
- Använd ett likhets tecken (=) för att avgränsa varje nyckel från värdet.
- Använd ett semikolon (;) eller en rad brytning för att avgränsa nyckel/värde-par.
- Nycklar som innehåller blank steg måste stå inom citat tecken. Värdena måste vara giltiga PowerShell-uttryck. Strängar måste omges av citat tecken, även om de inte innehåller blank steg.
- Om du vill hantera hash-tabellen sparar du den i en variabel.
- När du tilldelar en ordnad hash-tabell till en variabel placerar du attributet [ordnat] före symbolen "@". Kommandot Miss lyckas om du placerar det före variabelns namn.

Om du vill skapa en tom hash-tabell i värdet för $hash, skriver du:

```powershell
$hash = @{}
```

Du kan också lägga till nycklar och värden i en hash-tabell när du skapar den. Till exempel skapar följande instruktion en hash-tabell med tre nycklar.

```powershell
$hash = @{ Number = 1; Shape = "Square"; Color = "Blue"}
```

### <a name="creating-ordered-dictionaries"></a>Skapa beställda ord listor

Du kan skapa en ordnad ord lista genom att lägga till ett objekt av typen OrderedDictionary, men det enklaste sättet att skapa en ordnad ord lista använder attributet [ordnat].

Attributet [ordnat] introduceras i PowerShell 3,0.

Placera attributet omedelbart före symbolen "@".

```powershell
$hash = [ordered]@{ Number = 1; Shape = "Square"; Color = "Blue"}
```

Du kan använda beställda ord listor på samma sätt som du använder hash-tabeller.
Antingen kan typen användas som värde för parametrar som tar en hash-tabell eller-ord lista (iDictionary).

Du kan inte använda attributet [ordnat] för att konvertera eller omvandla en hash-tabell. Om du placerar det beställda attributet före variabelns namn, Miss lyckas kommandot med följande fel meddelande.

```powershell
PS C:\> [ordered]$hash = @{}
At line:1 char:1
+ [ordered]$hash = @{}
+ [!INCLUDE[]()]
The ordered attribute can be specified only on a hash literal node.
+ CategoryInfo          : ParserError: (:) [], ParentContainsErrorRecordExc
eption
+ FullyQualifiedErrorId : OrderedAttributeOnlyOnHashLiteralNode
```

Om du vill korrigera uttrycket flyttar du attributet [ordnat].

```powershell
PS C:\> $hash = [ordered]@{}
```

Du kan omvandla en ordnad ord lista till en hash-tabell, men du kan inte återställa det beställda attributet, även om du rensar variabeln och anger nya värden. För att återupprätta ordningen måste du ta bort och återskapa variabeln.

```
PS C:\> [hashtable]$hash = [ordered]@{
>> Number = 1; Shape = "Square"; Color = "Blue"}
PS C:\> $hash

Name                           Value
----                           -----
Color                          Blue
Shape                          Square
Number                         1
```

### <a name="displaying-hash-tables"></a>Visa hash-tabeller

Om du vill visa en hash-tabell som har sparats i en variabel skriver du variabelns namn.
Som standard visas hash-tabeller som en tabell med en kolumn för nycklar och en för-värden.

```powershell
C:\PS> $hash

Name                           Value
----                           -----
Shape                          Square
Color                          Blue
Number                         1
```

Hash-tabeller har nycklar och värden egenskaper. Använd punkt notation för att visa alla nycklar eller alla värden.

```powershell
C:\PS> $hash.keys
Number
Shape
Color

C:\PS> $hash.values
1
Square
Blue
```

Varje nyckel namn är också en egenskap för hash-tabellen och dess värde är värdet för nyckel namns egenskapen. Använd följande format för att Visa egenskaps värden.

```powershell
$hashtable.<key>
<value>
```

Ett exempel:

```powershell
C:\PS> $hash.Number
1

C:\PS> $hash.Color
Blue
```

Om nyckel namnet kolliderar med ett av egenskaps namnen för typ av hash-typ, kan du använda `PSBase` för att få åtkomst till dessa egenskaper. Om nyckel namnet till exempel är `keys` och du vill returnera en samling nycklar använder du följande syntax:

```powershell
$hashtable.PSBase.Keys
```

Hash-tabeller har en Count-egenskap som anger antalet nyckel/värde-par i hash-tabellen.

```powershell
C:\PS> $hash.count
3
```

Hash-tabellens tabeller är inte matriser, så du kan inte använda ett heltal som ett index i hash-tabellen, men du kan använda ett nyckel namn för att indexera till hash-tabellen.
Om nyckeln är ett sträng värde omger du nyckel namnet med citat tecken.

Ett exempel:

```powershell
C:\PS> $hash["Number"]
1
```

### <a name="adding-and-removing-keys-and-values"></a>Lägga till och ta bort nycklar och värden

Använd följande kommando format om du vill lägga till nycklar och värden i en hash-tabell.

```powershell
$hash["<key>"] = "<value>"
```

Om du till exempel vill lägga till en "Time"-nyckel med värdet "Now" i hash-tabellen använder du följande uttryck.

```powershell
$hash["Time"] = "Now"
```

Du kan också lägga till nycklar och värden i en hash-tabell med hjälp av metoden Add i objektet system. Collections. hash. Metoden Add har följande syntax:

```powershell
Add(Key, Value)
```

Om du till exempel vill lägga till en "Time"-nyckel med värdet "Now" i hash-tabellen använder du följande uttryck.

```powershell
$hash.Add("Time", "Now")
```

Du kan också lägga till nycklar och värden i en hash-tabell med hjälp av additionsoperatorn (+) för att lägga till en hash-tabell i en befintlig hash-tabell. Följande uttryck lägger till exempel till en "Time"-nyckel med värdet "Now" i hash-tabellen i $hash variabeln.

```powershell
$hash = $hash + @{Time="Now"}
```

Du kan också lägga till värden som lagras i variabler.

```powershell
$t = "Today"
$now = (Get-Date)

$hash.Add($t, $now)
```

Du kan inte använda en subtraktion-operator för att ta bort ett nyckel/värde-par från en hash-tabell, men du kan använda metoden Remove för objektet hash-objekt. Metoden Remove tar nyckeln som värde.

Metoden Remove har följande syntax:

```
Remove(Key)
```

Om du till exempel vill ta bort tid = nu nyckel/värde-paret från hash-tabellen i värdet för variabeln $hash, skriver du:

```powershell
$hash.Remove("Time")
```

Du kan använda alla egenskaper och metoder för hash-objekt i PowerShell, inklusive innehåller, rensa, klona och CopyTo. Mer information om hash-objekt finns i "system. Collections. hash" på MSDN.

### <a name="object-types-in-hashtables"></a>Objekt typer i hash

Nycklar och värden i en hash-tabell kan ha vilken .NET-objekt typ som helst, och en enda hash-tabell kan ha nycklar och värden av flera typer.

Följande instruktion skapar en hash-tabell med process namns strängar och bearbetar objekt värden och sparar dem i \$ variabeln p.

```powershell
$p = @{"PowerShell" = (Get-Process PowerShell);
"Notepad" = (Get-Process notepad)}
```

Du kan visa hash-tabellen i \$ p och använda egenskaperna för nyckel namn för att visa värdena.

```powershell
C:\PS> $p

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)

C:\PS> $p.PowerShell

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    441      24    54196      54012   571     5.10   1788 PowerShell

C:\PS> $p.keys | foreach {$p.$_.handles}
441
251
```

Nycklarna i en hash-tabell kan också vara vilken .NET-typ som helst. Följande instruktion lägger till ett nyckel/värde-par till hash-tabellen i \$ p-variabeln. Nyckeln är ett tjänst objekt som representerar WinRM-tjänsten och värdet är tjänstens aktuella status.

```powershell
C:\PS> $p = $p + @{(Get-Service WinRM) = ((Get-Service WinRM).Status)}
```

Du kan visa och komma åt det nya nyckel/värde-paret genom att använda samma metoder som du använder för andra par i hash-tabellen.

```powershell
C:\PS> $p

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)
System.ServiceProcess.Servi... Running

C:\PS> $p.keys
PowerShell
Notepad

Status   Name               DisplayName
------   ----               -----------
Running  winrm              Windows Remote Management (WS-Manag...

C:\PS> $p.keys | foreach {$_.name}
winrm
```

Nycklar och värden i en hash-tabell kan också vara hash-objekt. Följande uttryck lägger till nyckel/värde-par till hash-tabellen i den \$ p-variabel där nyckeln är en sträng, Hash2 och värdet är en hash-tabell med tre nyckel/värde-par.

```powershell
C:\PS> $p = $p + @{"Hash2"= @{a=1; b=2; c=3}}
```

Du kan visa och komma åt de nya värdena med samma metoder.

```powershell
C:\PS> $p

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)
System.ServiceProcess.Servi... Running
Hash2                          {a, b, c}

C:\PS> $p.Hash2

Name                           Value
----                           -----
a                              1
b                              2
c                              3

C:\PS> $p.Hash2.b
2
```

### <a name="sorting-keys-and-values"></a>Sortera nycklar och värden

Objekten i en hash-tabell är osorterade i ordningsföljd. Nyckel-/värdeparen kan visas i en annan ordning varje gången du visar dem.

Även om du inte kan sortera en hash-tabell kan du använda GetEnumerator-metoden för hash-tabeller för att räkna upp nycklar och värden, och sedan använda cmdleten Sort-Object för att sortera uppräknade värden för visning.

Följande kommandon räknar exempelvis upp nycklar och värden i hash-tabellen i \$ variabeln p och sorterar sedan nycklarna i alfabetisk ordning.

```powershell
C:\PS> $p.GetEnumerator() | Sort-Object -Property key

Name                           Value
----                           -----
Notepad                        System.Diagnostics.Process (notepad)
PowerShell                     System.Diagnostics.Process (PowerShell)
System.ServiceProcess.Servi... Running
```

Följande kommando använder samma procedur för att sortera hash-värden i fallande ordning.

```powershell
C:\PS> $p.getenumerator() | Sort-Object -Property Value -Descending

Name                           Value
----                           -----
PowerShell                     System.Diagnostics.Process (PowerShell)
Notepad                        System.Diagnostics.Process (notepad)
System.ServiceProcess.Servi... Running
```

### <a name="creating-objects-from-hash-tables"></a>Skapa objekt från hash-tabeller

Från och med PowerShell 3,0 kan du skapa ett objekt från en hash-tabell med egenskaper och egenskaps värden.

Syntaxen ser ut så här:

```powershell
[<class-name>]@{
  <property-name>=<property-value>
  <property-name>=<property-value>
}
```

Den här metoden fungerar bara för klasser som har en konstruktor som är null, det vill säga en konstruktor som inte har några parametrar. Objekt egenskaperna måste vara offentliga och kan anges.

Mer information finns i [about_Object_Creation](about_Object_Creation.md).

### <a name="convertfrom-stringdata"></a>ConvertFrom-StringData

`ConvertFrom-StringData`Cmdleten konverterar en sträng eller en här-sträng med nyckel/värde-par till en hash-tabell. Du kan använda `ConvertFrom-StringData` cmdleten på ett säkert sätt i avsnittet data i ett skript, och du kan använda den med- `Import-LocalizedData` cmdleten för att Visa användar meddelanden i användar gränssnitts kulturen (UI) för den aktuella användaren.

Här – strängarna är särskilt användbara när värdena i hash-tabellen innehåller citat tecken. Mer information om här – strängar finns [about_Quoting_Rules](about_Quoting_Rules.md).

I följande exempel visas hur du skapar en här-sträng av användar meddelandena i föregående exempel och hur du använder `ConvertFrom-StringData` för att konvertera dem från en sträng till en hash-tabell.

Följande kommando skapar en här-sträng för nyckel/värde-par och sparar det i \$ variabeln String.

```powershell
C:\PS> $string = @"
Msg1 = Type "Windows".
Msg2 = She said, "Hello, World."
Msg3 = Enter an alias (or "nickname").
"@
```

Det här kommandot använder cmdleten ConvertFrom-StringData för att konvertera denna-sträng till en hash-tabell.

```powershell
C:\PS> ConvertFrom-StringData $string

Name                           Value
----                           -----
Msg3                           Enter an alias (or "nickname").
Msg2                           She said, "Hello, World."
Msg1                           Type "Windows".
```

Mer information om här – strängar finns [about_Quoting_Rules](about_Quoting_Rules.md).

## <a name="see-also"></a>SE ÄVEN

[about_Arrays](about_Arrays.md)

[about_Object_Creation](about_Object_Creation.md)

[about_Quoting_Rules](about_Quoting_Rules.md)

[about_Script_Internationalization](about_Script_Internationalization.md)

[ConvertFrom-StringData](xref:Microsoft.PowerShell.Utility.ConvertFrom-StringData)

[Importera – LocalizedData](xref:Microsoft.PowerShell.Utility.Import-LocalizedData)

[System. Collections. hash](/dotnet/api/system.collections.hashtable)
