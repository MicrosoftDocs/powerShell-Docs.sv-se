---
description: Beskriver WMI Query Language (WQL) som kan användas för att hämta WMI-objekt i Windows PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_wql?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_WQL
ms.openlocfilehash: c6fd523864d419fb400b7041e92ec8f0733724b7
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271916"
---
# <a name="about-wql"></a>Om WQL

## <a name="short-description"></a>KORT BESKRIVNING

Beskriver WMI Query Language (WQL) som kan användas för att hämta WMI-objekt i Windows PowerShell.

## <a name="long-description"></a>LÅNG BESKRIVNING

WQL är frågespråket för Windows Management Instrumentation (WMI), vilket är det språk som används för att hämta information från WMI.

Du behöver inte använda WQL för att utföra en WMI-fråga i Windows PowerShell.
I stället kan du använda parametrarna i Get-WmiObject-eller Get-CimInstance-cmdletar. WQL-frågor är något snabbare än vanliga Get-WmiObject kommandon och den förbättrade prestandan är tydlig när kommandona körs på hundratals system. Men se till att den tid du ägnat att skriva en lyckad WQL-fråga inte uppväger prestanda förbättringen.

De grundläggande WQL-uttrycken som du behöver för att använda WQL är Select, WHERE och from.

## <a name="when-to-use-wql"></a>NÄR DU SKA ANVÄNDA WQL

När du arbetar med WMI och särskilt med WQL, ska du inte glömma att du även använder Windows PowerShell. Ofta, om en WQL-fråga inte fungerar som förväntat, är det enklare att använda ett Windows PowerShell-kommando än att felsöka WQL-frågan.

Om du inte returnerar enorma data mängder från över bandbredds begränsade fjärrsystem är det sällan produktivt att ägna timmar åt att försöka med en komplicerad och komplexa WQL-fråga när det finns en perfekt acceptabel Windows-cmdlet som gör samma sak, om det blir långsammare.

## <a name="using-the-select-statement"></a>ANVÄNDA SELECT-INSTRUKTIONEN

En typisk WMI-fråga börjar med en SELECT-instruktion som hämtar alla egenskaper eller vissa egenskaper för en WMI-klass. Om du vill välja alla egenskaper för en WMI-klass använder du en asterisk ( \* ). From-nyckelordet anger WMI-klassen.

En SELECT-instruktion har följande format:

```
Select <property> from <WMI-class>
```

Följande SELECT-instruktion väljer till exempel alla egenskaper (*) från instanserna av Win32_Bios WMI-klassen.

```
Select * from Win32_Bios
```

Om du vill välja en viss egenskap för en WMI-klass, placerar du egenskaps namnet mellan nyckelorden Select och from.

Följande fråga väljer bara namnet på BIOS från Win32_Bios WMI-klassen. Kommandot sparar frågan i variabeln $queryName.

```
Select Name from Win32_Bios
```

Om du vill markera fler än en egenskap använder du kommatecken för att avgränsa egenskaps namnen.
Följande WMI-fråga väljer namn och version för Win32_Bios WMI-klassen. Kommandot sparar frågan i variabeln $queryNameVersion.

```
Select name, version from Win32_Bios
```

## <a name="using-the-wql-query"></a>ANVÄNDA WQL-FRÅGAN

Det finns tre sätt att använda WQL-frågor i Windows PowerShell-kommandot.

- Använd Get-WmiObject-cmdleten
- Använd Get-CimInstance-cmdleten
- Använd [wmisearcher]-typ Accelerator.

## <a name="using-the-get-wmiobject-cmdlet"></a>ANVÄNDA CMDLETEN GET-WMIOBJECT

Det mest grundläggande sättet att använda WQL-frågan är att omge det med citat tecken (som en sträng) och sedan använda frågesträngen som värde för Frågeparametern för Get-WmiObject-cmdlet, som visas i följande exempel.

```powershell
Get-WmiObject -Query "Select * from Win32_Bios"
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

Du kan också spara WQL-instruktionen i en variabel och sedan använda variabeln som värde för Frågeparametern, som du ser i följande kommando.

```powershell
$query = "Select * from Win32_Bios"
Get-WmiObject -Query $query
```

Du kan använda något av formaten med valfri WQL-instruktion. Följande kommando använder frågan i variabeln $queryName för att bara hämta namn och versions egenskaper för systemets BIOS.

```powershell
$queryNameVersion = "Select Name, Version from Win32_Bios"
Get-WmiObject -Query $queryNameVersion
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
Version          : LENOVO - 1360
```

Kom ihåg att du kan använda parametrarna för Get-WmiObject cmdlet för att få samma resultat. Följande kommando hämtar till exempel även värdena för namn-och versions egenskaperna för instanser av Win32_Bios WMI-klassen.

```powershell
Get-WmiObject -Class Win32_Bios -Property Name, Version
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
Version          : LENOVO - 1360
```

## <a name="using-the-get-ciminstance-cmdlet"></a>ANVÄNDA CMDLETEN GET-CIMINSTANCE

Från och med Windows PowerShell 3,0 kan du använda cmdleten Get-CimInstance för att köra WQL-frågor.

Get-CimInstance hämtar instanser av CIM-kompatibla klasser, inklusive WMI-klasser. CIM-cmdletarna introducerade Windows PowerShell 3,0 och utför samma uppgifter som WMI-cmdlets. CIM-cmdlets följer WS-Management (WSMan)-standarder och med Common Information Model (CIM) standard, vilket gör att cmdletarna kan använda samma metoder för att hantera Windows-datorer och datorer som kör andra operativ system.

Följande kommando använder cmdleten Get-CimInstance för att köra en WQL-fråga.

Alla WQL-frågor som kan användas med Get-WmiObject kan också användas med Get-CimInstance.

```powershell
Get-CimInstance -Query "Select * from Win32_Bios"
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

Get-CimInstance returnerar ett CimInstance-objekt, i stället för de ManagementObject som Get-WmiObject returnerar, men objekten är ganska likartade.

```
(Get-CimInstance -Query "Select * from Win32_Bios").GetType().FullName
Microsoft.Management.Infrastructure.CimInstance
(Get-WmiObject -Query "Select * from Win32_Bios").GetType().FullName
System.Management.ManagementObject
```

## <a name="using-the-wmisearcher-type-accelerator"></a>ANVÄNDA [wmisearcher]-typ ACCELERATOR

Typ acceleratorn [wmisearcher] skapar ett ManagementObjectSearcher-objekt från en WQL-instruktions sträng. ManagementObjectSearcher-objektet har många egenskaper och metoder, men den mest grundläggande metoden är Get-metoden, som anropar den angivna WMI-frågan och returnerar resulterande objekt.

Genom att använda [wmisearcher] får du enkel åtkomst till ManagementObjectSearcher .NET Framework-klassen. På så sätt kan du fråga WMI och konfigurera hur frågan utförs.

Använda typ Accelerator [wmisearcher]:

1. Omvandla WQL-strängen till ett ManagementObjectSearcher-objekt.
2. Anropa Get-metoden för ManagementObjectSearcher-objektet.

Följande kommando skickar till exempel frågan "Select all", sparar resultatet i variabeln $bios och anropar sedan Get-metoden för ManagementObjectSearcher-objektet i $bios-variabeln.

```powershell
$bios = [wmisearcher]"Select * from Win32_Bios"
$bios.Get()
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

Obs: endast valda objekt egenskaper visas som standard. Dessa egenskaper definieras i Types.ps1XML-filen.

Du kan använda [wmisearcher]-typ Accelerator för att omvandla frågan eller variabeln. I följande exempel används [wmisearcher] Type Accelerator för att omvandla variabeln. Resultatet är detsamma.

```powershell
[wmisearcher]$bios = "Select * from Win32_Bios"
$bios.Get()
```

```output
SMBIOSBIOSVersion : 8BET56WW (1.36 )
Manufacturer      : LENOVO
Name              : Default System BIOS
SerialNumber      : R9FPY3P
Version           : LENOVO - 1360
```

När du använder typen [wmisearcher] kan du ändra frågesträngen till ett ManagementObjectSearcher-objekt, som du ser i följande kommandon.

```
$a = "Select * from Win32_Bios"
$a.GetType().FullName
System.String

$a = [wmisearcher]"Select * from Win32_Bios"
$a.GetType().FullName
System.Management.ManagementObjectSearcher
```

Det här kommando formatet fungerar för alla frågor. Följande kommando hämtar värdet för egenskapen Name i Win32_Bios WMI-klassen.

```powershell
$biosname = [wmisearcher]"Select Name from Win32_Bios"
$biosname.Get()
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
```

Du kan utföra den här åtgärden i ett enda kommando, men kommandot är lite svårare att tolka.

I det här formatet använder du text acceleratorn [wmisearcher] för att omvandla WQL-frågesträngen till en ManagementObjectSearcher och anropa sedan metoden get i objektet--all i ett enda kommando. Parenteserna () som omger den Casted strängen Direct Windows PowerShell för att omvandla strängen innan metoden anropas.

```powershell
([wmisearcher]"Select name from Win32_Bios").Get()
```

```output
__GENUS          : 2
__CLASS          : Win32_BIOS
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
Name             : Default System BIOS
```

## <a name="using-the-basic-wql-where-statement"></a>ANVÄNDA BASIC WQL WHERE-INSTRUKTION

En WHERE-instruktion upprättar villkor för de data som en SELECT-instruktion returnerar.

WHERE-instruktionen har följande format:

```
where <property> <operator> <value>
```

Ett exempel:

```
where Name = 'Notepad.exe'
```

WHERE-instruktionen används med SELECT-instruktionen, som visas i följande exempel.

```
Select * from Win32_Process where Name = 'Notepad.exe'
```

När du använder instruktionen WHERE måste egenskaps namnet och värdet vara korrekt.

Följande kommando hämtar till exempel anteckningar-processerna på den lokala datorn.

```powershell
Get-WmiObject -Query "Select * from Win32_Process where name='Notepad.exe'"
```

Följande kommando Miss lyckas dock, eftersom process namnet innehåller fil namns tillägget ". exe".

```powershell
Get-WmiObject -Query "Select * from Win32_Process where name='Notepad'"
```

## <a name="where-statement-comparison-operators"></a>WHERE-SATSEN JÄMFÖRELSE OPERATORER

Följande operatorer är giltiga i en WQL WHERE-instruktion.

```
Operator    Description
-----------------------
=           Equal
!=          Not equal
<>          Not equal
<           Less than
>           Greater than
<=          Less than or equal
>=          Greater than or equal
LIKE        Wildcard match
IS          Evaluates null
ISNOT       Evaluates not null
ISA         Evaluates a member of a WMI class
```

Det finns andra operatorer, men de är de som används för att jämföra dem.

Följande fråga väljer till exempel namn och prioritets egenskaper från processer i Win32_Process-klassen där process prioriteten är större än eller lika med 11. Get-WmiObject cmdleten kör frågan.

```powershell
$highPriority = "Select Name, Priority from Win32_Process " +
  "where Priority >= 11"
Get-WmiObject -Query $highPriority
```

## <a name="using-the-wql-operators-in-the-filter-parameter"></a>ANVÄNDA WQL-OPERATÖRER I FILTER PARAMETERN

WQL-operatörer kan också användas i värdet för filter parametern för Get-WmiObject-eller Get-CimInstance-cmdletar, samt i värdet för frågeparametrar för dessa cmdletar.

Följande kommando hämtar till exempel namn-och ProcessID-egenskaperna för de senaste fem processerna som har ProcessID-värden som är större än 1004. Kommandot använder filter parametern för att ange ProcessID-villkoret.

```powershell
Get-WmiObject -Class Win32_Process `
-Property Name, ProcessID -Filter "ProcessID >= 1004" |
Sort ProcessID | Select Name, ProcessID -Last 5
```

```output
Name                                 ProcessID
----                                 ---------
SROSVC.exe                                4220
WINWORD.EXE                               4664
TscHelp.exe                               4744
SnagIt32.exe                              4748
WmiPrvSE.exe                              5056
```

## <a name="using-the-like-operator"></a>ANVÄNDA OPERATORN LIKE

Operatorn Like gör att du kan använda jokertecken för att filtrera resultatet av en WQL-fråga.

```
Like Operator  Description
--------------------------------------------------
[]             Character in a range [a-f] or a set
               of characters [abcdef]. The items in
               a set do not need to be consecutive or
               listed in alphabetical order.

^              Character not in a range [^a-f] or
               not in a set [^abcdef]. The items in
               a set do not need to be consecutive or
               listed in alphabetical order.

%              A string of zero or more characters

_              One character.
(underscore)   NOTE: To use a literal underscore
               in a query string, enclose it in
               square brackets [_].
```

När operatorn Like används utan jokertecken eller intervall operatorer beter sig den som likhets operatorn (=) och returnerar bara objekt när de är en exakt matchning för mönstret.

Du kan kombinera åtgärds området med jokertecknet i procent för att skapa enkla, men ändå kraftfulla filter.

### <a name="like-operator-examples"></a>EXEMPEL PÅ LIKE-OPERATOR

#### <a name="example-1-range"></a>EXEMPEL 1: [ \<range> ]

Följande kommandon startar anteckningar och söker sedan efter en instans av klassen Win32_Process som har ett namn som börjar med en bokstav mellan "H" och "N" (Skift läges okänsligt).

Frågan ska returnera vilken process som helst från Hotpad.exe via Notepad.exe.

```powershell
Notepad   # Starts Notepad
$query = "Select * from win32_Process where Name LIKE '[H-N]otepad.exe'"
Get-WmiObject -Query $query | Select Name, ProcessID
```

```output
Name                                ProcessID
----                                ---------
notepad.exe                              1740
```

#### <a name="example-2-range-and-"></a>EXEMPEL 2: [ \<range> ] och%

Följande kommandon väljer alla processer som har ett namn som börjar med en bokstav mellan A och P (Skift läges okänsligt) följt av noll eller flera bokstäver i valfri kombination.

Get-WmiObject cmdleten kör frågan, Select-Object-cmdleten hämtar egenskaperna för namn och ProcessID och Sort-Object-cmdlet sorterar resultaten i bokstavs ordning efter namn.

```powershell
$query = "Select * from win32_Process where name LIKE '[A-P]%'"
Get-WmiObject -Query $query |
Select-Object -Property Name, ProcessID |
Sort-Object -Property Name
```

#### <a name="example-3-not-in-range-"></a>EXEMPEL 3: inte inom intervallet (^)

Följande kommando hämtar processer vars namn inte börjar med någon av följande bokstäver: A, S, W, P, R, C, U, N

och följde noll eller flera bokstäver.

```powershell
$query = "Select * from win32_Process where name LIKE '[^ASWPRCUN]%'"
Get-WmiObject -Query $query |
Select-Object -Property Name, ProcessID |
Sort-Object -Property Name
```

#### <a name="example-4-any-characters----or-none-"></a>EXEMPEL 4: alla tecken, eller inget (%)

Följande kommandon hämtar processer som har namn som börjar med "Calc".
Symbolen% i WQL motsvarar asterisken ( \* ) i reguljära uttryck.

```powershell
$query = "Select * from win32_Process where Name LIKE 'calc%'"
Get-WmiObject -Query $query | Select-Object -Property Name, ProcessID
```

```output
Name                               ProcessID
----                               ---------
calc.exe                                4424
```

#### <a name="example-5-one-character-_"></a>EXEMPEL 5: ett Character (_)

Följande kommandon hämtar processer som har namn som har följande mönster: "c_lc.exe" där under strecks tecknet representerar ett tecken. Det här mönstret matchar alla namn från calc.exe via czlc.exe eller c9lc.exe, men matchar inte namnen där "c" och "l" är avgränsade med mer än ett.

```powershell
$query = "Select * from Win32_Process where Name LIKE 'c_lc.exe'"
Get-WmiObject -Query $query | Select-Object -Property Name, ProcessID
```

```output
Name                                 ProcessID
----                                 ---------
calc.exe                                  4424
```

#### <a name="example-6-exact-match"></a>EXEMPEL 6: exakt matchning

Följande kommandon hämtar processer med namnet WLIDSVC.exe. Även om frågan använder nyckelordet like krävs en exakt matchning, eftersom värdet inte innehåller jokertecken.

```powershell
$query = "Select * from win32_Process where name LIKE 'WLIDSVC.exe'"
Get-WmiObject -Query $query | Select-Object -Property Name, ProcessID
```powershell

```output
Name                                 ProcessID
----                                 ---------
WLIDSVC.exe                                84
```

## <a name="using-the-or-operator"></a>ANVÄNDA OPERATORN OR

Om du vill ange flera oberoende villkor använder du nyckelordet eller. Nyckelordet eller visas i WHERE-satsen. Den utför en eller flera åtgärder på två (eller fler) villkor och returnerar objekt som uppfyller något av villkoren.

Operatorn OR har följande format:

```
Where <property> <operator> <value> or <property> <operator> <value> ...
```

Följande kommandon hämtar till exempel alla instanser av klassen Win32_Process WMI men returnerar dem endast om process namnet är winword.exe eller excel.exe.

```powershell
$q = "Select * from Win32_Process where Name='winword.exe'" +
  " or Name='excel.exe'"
Get-WmiObject -Query $q
```

Instruktionen or kan användas med fler än två villkor. I följande fråga hämtar or-instruktionen Winword.exe, Excel.exe eller Powershell.exe.

```powershell
$q = "Select * from Win32_Process where Name='winword.exe'" +
  " or Name='excel.exe' or Name='powershell.exe'"
```

## <a name="using-the-and-operator"></a>ANVÄNDA OPERATORN OCH

Om du vill ange flera relaterade villkor använder du nyckelordet och. Nyckelordet och visas i WHERE-satsen. Den returnerar objekt som uppfyller alla villkor.

Operatorn och har följande format:

```
Where <property> <operator> <value> and <property> <operator> <value> ...
```

Följande kommandon får till exempel processer som har namnet "Winword.exe" och process-ID: t 6512.

Observera att kommandona använder Get-CimInstance-cmdleten.

```powershell
$q = "Select * from Win32_Process where Name = 'winword.exe' " +
  "and ProcessID =6512"
Get-CimInstance -Query $q
```

```output
ProcessId   Name             HandleCount      WorkingSetSize   VirtualSize
---------   ----             -----------      --------------   -----------
# 6512      WINWORD.EXE      768              117170176        633028608
```

Alla operatorer, inklusive like-operatorer, är giltiga med operatorerna or och och. Och du kan kombinera operatorerna or och och och i en enskild fråga med parenteser som anger för Windows PowerShell vilka satser som ska bearbetas först.

Det här kommandot använder fortsättnings tecknen i Windows PowerShell (') för att dela upp kommandot i två rader.

```powershell
$q = "Select * from Win32_Process `
where (Name = 'winword.exe' or Name = 'excel.exe') and HandleCount > 700"
Get-CimInstance -Query $q
```

```output
ProcessId    Name             HandleCount      WorkingSetSize   VirtualSize
---------    ----             -----------      --------------   -----------
     6512    WINWORD.EXE      797              117268480        634425344
     9610    EXCEL.EXE        727               38858752        323227648
```

## <a name="searching-for-null-values"></a>SÖKER EFTER NULL-VÄRDEN

Det är svårt att söka efter null-värden i WMI, eftersom det kan leda till oförutsägbara resultat. Null är inte noll och är inte detsamma som eller en tom sträng. Vissa egenskaper för WMI-klass initieras och andra är inte, så en sökning efter null kanske inte fungerar för alla egenskaper.

Om du vill söka efter null-värden använder du operatorn är med värdet null.

Följande kommandon får till exempel processer som har ett null-värde för egenskapen IntallDate. Kommandona returnerar många processer.

```powershell
$q = "Select * from Win32_Process where InstallDate is null"
Get-WmiObject -Query $q
```

Följande kommando hämtar däremot användar konton som har ett null-värde för egenskapen Description. Det här kommandot returnerar inga användar konton, även om de flesta användar konton inte har något värde för egenskapen Description.

```powershell
$q = "Select * from Win32_UserAccount where Description is null"
Get-WmiObject -Query $q
```

Om du vill hitta användar konton som saknar värde för egenskapen Description använder du likhets operatorn för att hämta en tom sträng. Om du vill visa den tomma strängen använder du två enkla citat tecken i följd.

```powershell
$q = "Select * from Win32_UserAccount where Description = '' "
```

## <a name="using-true-or-false"></a>ANVÄNDA TRUE ELLER FALSE

Om du vill hämta booleska värden i egenskaperna för WMI-objekt, använder du True och false.
De är inte skiftlägeskänsliga.

Följande WQL-fråga returnerar endast lokala användar konton från en domänansluten dator.

```powershell
$q = "Select * from Win32_UserAccount where LocalAccount = True"
Get-CimInstance -Query $q
```

Om du vill hitta domän konton använder du värdet FALSKT, som du ser i följande exempel.

```powershell
$q = "Select * from Win32_UserAccount where LocalAccount = False"
Get-CimInstance -Query $q
```

## <a name="using-the-escape-character"></a>ANVÄNDA ESCAPE-TECKEN

WQL använder omvänt snedstreck ( \) som escape-tecken). Detta skiljer sig från Windows PowerShell, som använder Baknings tecknen (').

Citat tecken och tecknen som används för citat tecken måste ofta vara undantagna så att de inte tolkas.

Om du vill hitta en användare vars namn innehåller ett enkelt citat tecken, använder du ett omvänt snedstreck för att undvika det enkla citat tecknet, som du ser i följande kommando.

```powershell
$q = "Select * from Win32_UserAccount where Name = 'Tim O\'Brian'"
Get-CimInstance -Query $q
```

```output
Name             Caption          AccountType      SID              Domain
----             -------          -----------      ---              ------
Tim O'Brian      FABRIKAM\TimO    512              S-1-5-21-1457... FABRIKAM
```

I vissa fall måste omvänt snedstreck också vara ett undantag. Följande kommandon genererar till exempel ett ogiltigt frågefel på grund av omvänt snedstreck i värdet Caption.

```powershell
$q = "Select * from Win32_UserAccount where Caption = 'Fabrikam\TimO'"
Get-CimInstance -Query $q
```

```output
Get-CimInstance : Invalid query
At line:1 char:1
+ Get-CimInstance -Query $q
+ ~~~~~~~~~~~
  + CategoryInfo          : InvalidArgument: (:) [Get-CimInstance], CimExcep
  + FullyQualifiedErrorId : HRESULT 0x80041017,Microsoft.Management.Infrastr
```

Om du vill undanta omvänt snedstreck använder du ett andra omvänt snedstreck, som du ser i följande kommando.

```powershell
$q = "Select * from Win32_UserAccount where Caption = 'Fabrikam\\TimO'"
Get-CimInstance -Query $q
```

## <a name="see-also"></a>SE ÄVEN

[about_Special_Characters](about_Special_Characters.md)

[about_Quoting_Rules](about_Quoting_Rules.md)

[about_WMI](about_WMI.md)

[about_WMI_Cmdlets](about_WMI_Cmdlets.md)
