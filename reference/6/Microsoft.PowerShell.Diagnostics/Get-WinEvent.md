---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 11/20/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/get-winevent?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-WinEvent
ms.openlocfilehash: 72455745d4523a33cac4ccca5af9c8be29ac9e37
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267380"
---
# Get-WinEvent

## SAMMANFATTNING
Hämtar händelser från händelse loggar och händelse spårnings loggar på lokala datorer och fjärrdatorer.

## SYNTAX

### GetLogSet (standard)

```
Get-WinEvent [[-LogName] <String[]>] [-MaxEvents <Int64>] [-ComputerName <String>]
 [-Credential <PSCredential>] [-FilterXPath <String>] [-Force] [-Oldest] [<CommonParameters>]
```

### ListLogSet

```
Get-WinEvent [-ListLog] <String[]> [-ComputerName <String>] [-Credential <PSCredential>] [-Force]
 [<CommonParameters>]
```

### ListProviderSet

```
Get-WinEvent [-ListProvider] <String[]> [-ComputerName <String>] [-Credential <PSCredential>]
 [<CommonParameters>]
```

### GetProviderSet

```
Get-WinEvent [-ProviderName] <String[]> [-MaxEvents <Int64>] [-ComputerName <String>]
 [-Credential <PSCredential>] [-FilterXPath <String>] [-Force] [-Oldest] [<CommonParameters>]
```

### FileSet

```
Get-WinEvent [-Path] <String[]> [-MaxEvents <Int64>] [-Credential <PSCredential>]
 [-FilterXPath <String>] [-Oldest] [<CommonParameters>]
```

### HashQuerySet

```
Get-WinEvent [-MaxEvents <Int64>] [-ComputerName <String>] [-Credential <PSCredential>]
 [-FilterHashtable] <Hashtable[]> [-Force] [-Oldest] [<CommonParameters>]
```

### XmlQuerySet

```
Get-WinEvent [-MaxEvents <Int64>] [-ComputerName <String>] [-Credential <PSCredential>]
 [-FilterXml] <XmlDocument> [-Oldest] [<CommonParameters>]
```

## BESKRIVNING

`Get-WinEvent`Cmdleten hämtar händelser från händelse loggar, inklusive klassiska loggar som **system** -och **program** loggar. Cmdleten hämtar data från händelse loggar som genereras av Windows-händelseloggen som introducerades i Windows Vista. Och händelser i loggfiler som genereras av **ETW (Event tracing for Windows) (ETW)**. Som standard `Get-WinEvent` returnerar händelse information i ordningen nyaste till äldsta.

`Get-WinEvent` visar händelse loggar och providers för händelse loggar. Tryck på <kbd>CTRL</kbd>C om du vill avbryta kommandot + <kbd>C</kbd>. Du kan hämta händelser från valda loggar eller från loggar som skapats av valda händelse leverantörer. Du kan också kombinera händelser från flera källor i ett enda kommando.
`Get-WinEvent` gör att du kan filtrera händelser med hjälp av XPath-frågor, strukturerade XML-frågor och frågor om hash-tabeller.

Om du inte kör PowerShell som administratör kan du se fel meddelanden om att du inte kan hämta information om en logg.

## EXEMPEL

### Exempel 1: Hämta alla loggar från en lokal dator

Det här kommandot hämtar alla händelse loggar på den lokala datorn. Loggarna visas i den ordning som de `Get-WinEvent` hämtas. Klassiska loggar hämtas först, följt av de nya händelse loggarna i Windows.
Det är möjligt att en loggs **RecordCount** måste vara null, vilket är tomt eller noll.

```powershell
Get-WinEvent -ListLog *
```

```Output
LogMode   MaximumSizeInBytes RecordCount LogName
-------   ------------------ ----------- -------
Circular            15532032       14500 Application
Circular             1052672         117 Azure Information Protection
Circular             1052672        3015 CxAudioSvcLog
Circular            20971520             ForwardedEvents
Circular            20971520           0 HardwareEvents
```

`Get-WinEvent`Cmdleten hämtar logg information från datorn. Parametern **ListLog** använder jokertecknet asterisk ( `*` ) för att visa information om varje logg.

### Exempel 2: hämta den klassiska installations loggen

Det här kommandot hämtar ett **EventLogConfiguration** -objekt som representerar den klassiska **installations** loggen. Objektet innehåller information om loggen, till exempel fil storlek, Provider, fil Sök väg och om loggen är aktive rad.

```powershell
Get-WinEvent -ListLog Setup | Format-List -Property *
```

```Output
FileSize                       : 69632
IsLogFull                      : False
LastAccessTime                 : 3/13/2019 09:41:46
LastWriteTime                  : 3/13/2019 09:41:46
OldestRecordNumber             : 1
RecordCount                    : 23
LogName                        : Setup
LogType                        : Operational
LogIsolation                   : Application
IsEnabled                      : True
IsClassicLog                   : False
SecurityDescriptor             : O:BAG:SYD: ...
LogFilePath                    : %SystemRoot%\System32\Winevt\Logs\Setup.evtx
MaximumSizeInBytes             : 1052672
LogMode                        : Circular
OwningProviderName             : Microsoft-Windows-Eventlog
ProviderNames                  : {Microsoft-Windows-WUSA, Microsoft-Windows-ActionQueue...
ProviderLevel                  :
ProviderKeywords               :
ProviderBufferSize             : 64
ProviderMinimumNumberOfBuffers : 0
ProviderMaximumNumberOfBuffers : 64
ProviderLatency                : 1000
ProviderControlGuid            :
```

`Get-WinEvent`Cmdleten använder parametern **ListLog** för att ange **installations** loggen. Objektet skickas ned pipelinen till `Format-List` cmdleten. `Format-List` använder **egenskaps** parametern med jokertecknet asterisk ( `*` ) för att visa varje egenskap.

### Exempel 3: Hämta händelse loggar från en server

Det här kommandot hämtar endast händelse loggar på den lokala datorn som innehåller händelser. Det är möjligt att en loggs **RecordCount** är null eller noll. I exemplet används `$_` variabeln. Mer information finns i [about_Automatic_Variables](../Microsoft.PowerShell.Core/about/about_automatic_variables.md).

```powershell
Get-WinEvent -ListLog * -ComputerName localhost | Where-Object { $_.RecordCount }
```

```Output
LogMode   MaximumSizeInBytes RecordCount LogName
-------   ------------------ ----------- -------
Circular            15532032       14546 Application
Circular             1052672         117 Azure Information Protection
Circular             1052672        2990 CxAudioSvcLog
Circular             1052672           9 MSFTVPN Setup
Circular             1052672         282 OAlerts
```

`Get-WinEvent`Cmdleten hämtar logg information från datorn. Parametern **ListLog** använder jokertecknet asterisk ( `*` ) för att visa information om varje logg. Parametern **computername** anger att ska hämta loggarna från den lokala datorn, **localhost**. Objekten skickas ned pipelinen till `Where-Object` cmdleten. `Where-Object` använder `$_.RecordCount` för att returnera enbart loggar som innehåller data. `$_` är en variabel som representerar det aktuella objektet i pipelinen. **RecordCount** är en egenskap hos objektet med ett värde som inte är null.

### Exempel 4: Hämta händelse loggar från flera servrar

Det här exemplet hämtar objekt som representerar **program** händelse loggarna på tre datorer: Server01, Server02 och Server03. **Nyckelordet för** förhands skydd används eftersom parametern **computername** bara accepterar ett värde. Mer information finns i [about_Foreach](../Microsoft.PowerShell.Core/about/about_Foreach.md).

```powershell
$S = 'Server01', 'Server02', 'Server03'
ForEach ($Server in $S) {
  Get-WinEvent -ListLog Application -ComputerName $Server |
    Select-Object LogMode, MaximumSizeInBytes, RecordCount, LogName,
      @{name='ComputerName'; expression={$Server}} |
    Format-Table -AutoSize
}
```

```Output
 LogMode MaximumSizeInBytes RecordCount LogName     ComputerName
 ------- ------------------ ----------- -------     ------------
Circular           15532032       14577 Application Server01
Circular           15532032        9689 Application Server02
Circular           15532032        5309 Application Server03
```

Variabeln `$S` lagrar namnen tre servrar: **Server01** , **Server02** och **Server03**. I den **förgrunds** deklarationen används en loop för att bearbeta varje server `($Server in $S)` . Skript blocket inom klammerparenteser ( `{ }` ) kör `Get-WinEvent` kommandot. Parametern **ListLog** anger **program** loggen. Parametern **computername** använder variabeln `$Server` för att hämta logg information från varje server.

Objekten skickas ned pipelinen till `Select-Object` cmdleten. `Select-Object` hämtar egenskaperna **LogMode** , **MaximumSizeInBytes** , **RecordCount** , **LogName** och använder ett beräknat uttryck för att visa det **computername** som använder `$Server` variabeln. Objekten skickas ned pipelinen till `Format-Table` cmdleten för att visa utdata i PowerShell-konsolen. Parametern **AutoSize** formaterar utdata så att den passar skärmen.

### Exempel 5: Hämta händelse logg leverantörer och logg namn

Det här kommandot hämtar tjänsterna för händelse loggar och de loggar som de skriver till.

```powershell
Get-WinEvent -ListProvider *
```

```Output
Name     : .NET Runtime
LogLinks : {Application}
Opcodes  : {}
Tasks    : {}

Name     : .NET Runtime Optimization Service
LogLinks : {Application}
Opcodes  : {}
Tasks    : {}
```

`Get-WinEvent`Cmdleten hämtar logg information från datorn. Parametern **ListProvider** använder jokertecknet asterisk ( `*` ) för att visa information om varje provider. I utdata är **namnet** providern och **LogLinks** den logg som providern skriver till.

### Exempel 6: Hämta alla händelse logg leverantörer som skriver till en speciell logg

Det här kommandot hämtar alla providers som skriver till **program** loggen.

```powershell
(Get-WinEvent -ListLog Application).ProviderNames
```

```Output
.NET Runtime
.NET Runtime Optimization Service
Application
Application Error
Application Hang
Application Management
```

`Get-WinEvent`Cmdleten hämtar logg information från datorn. Parametern **ListLog** använder **programmet** för att hämta objekt för den loggen. **ProviderNames** är en egenskap hos objektet och visar de leverantörer som skriver till **program** loggen.

### Exempel 7: Hämta namn på händelse logg leverantörer som innehåller en angiven sträng

Detta kommando hämtar händelse logg leverantörer med namn som innehåller en speciell sträng i Providerns namn.

```powershell
Get-WinEvent -ListProvider *Policy*
```

```Output
Name     : Group Policy Applications
LogLinks : {Application}
Opcodes  : {}
Tasks    : {}

Name     : Group Policy Client
LogLinks : {Application}
Opcodes  : {}
Tasks    : {}

Name     : Group Policy Data Sources
LogLinks : {Application}
Opcodes  : {}
Tasks    : {}
```

`Get-WinEvent`Cmdleten hämtar logg information från datorn. Parametern **ListProvider** använder jokertecknet asterisk ( `*` ) för att hitta **principen** var som helst inom Providerns namn.

### Exempel 8: Hämta händelse-ID som Event Provider genererar

Det här kommandot visar de händelse-ID: n som **Microsoft-Windows-GroupPolicy-** Händelseprovidern genererar tillsammans med händelse beskrivningen.

```powershell
(Get-WinEvent -ListProvider Microsoft-Windows-GroupPolicy).Events | Format-Table Id, Description
```

```Output
  Id  Description
  --  -----------
1500  The Group Policy settings for the computer were processed successfully...
1501  The Group Policy settings for the user were processed successfully...
4115  Group Policy Service started.
4116  Started the Group Policy service initialization phase.
4117  Group Policy Session started.
```

`Get-WinEvent`Cmdleten hämtar logg information från datorn. Parametern **ListProvider** anger providern, **Microsoft-Windows-GroupPolicy**. Uttrycket omges av parenteser och använder egenskapen **Events** för att hämta objekt. Objekten skickas ned pipelinen till `Format-Table` cmdleten. `Format-Table` visar **ID** och **Beskrivning** för händelse objekt.

### Exempel 9: Hämta logg information från händelse objekts egenskaper

Det här exemplet visar hur du hämtar information om en loggs innehåll med hjälp av händelse objekt egenskaper.
Händelse objekt lagras i en variabel och grupperas och räknas sedan av **händelse-ID** och **nivå**.

```powershell
$Event = Get-WinEvent -LogName 'Windows PowerShell'
$Event.Count
$Event | Group-Object -Property Id -NoElement | Sort-Object -Property Count -Descending
$Event | Group-Object -Property LevelDisplayName -NoElement
```

```Output
195

Count  Name
-----  ----
  147  600
   22  400
   21  601
    3  403
    2  103

Count  Name
-----  ----
    2  Warning
  193  Information
```

`Get-WinEvent`Cmdleten använder parametern **LogName** för att ange händelse loggen för **Windows PowerShell** . Händelse objekt lagras i `$Event` variabeln. Egenskapen **Count** för `$Event` visar det totala antalet loggade händelser.

`$Event`Variabeln skickas ned pipelinen till `Group-Object` cmdleten. `Group-Object` använder **egenskaps** parametern för att ange **ID-** egenskapen och räknar objekten med händelse-ID-värdet. Parametern **noelement** tar bort andra egenskaper från objektets utdata. De grupperade objekten skickas ned pipelinen till `Sort-Object` cmdleten. `Sort-Object` använder **egenskaps** parametern för att sortera objekten efter **antal**. I **fallande** parameter visas utdata efter antal, från högsta till lägsta. I resultatet innehåller kolumnen **Count** det totala antalet för varje händelse. Kolumnen **namn** innehåller grupperade händelse-ID-nummer.

`$Event`Variabeln skickas ned pipelinen till `Group-Object` cmdleten. `Group-Object` använder **egenskaps** parametern för att ange egenskapen **LevelDisplayName** och räknar objekten med **LevelDisplayName**. Objekten grupperas efter de nivåer som **Varning** och **information**.
Parametern **noelement** tar bort andra egenskaper från utdata. I resultatet innehåller kolumnen **Count** det totala antalet för varje händelse. Kolumnen **Name** innehåller den grupperade **LevelDisplayName**.

### Exempel 10: Hämta fel händelser som har en angiven sträng i sitt namn

I det här exemplet används en kommaavgränsad sträng med logg namn. Utdata grupperas efter nivå som fel eller varning och logg namnet.

```powershell
Get-WinEvent -LogName *PowerShell*, Microsoft-Windows-Kernel-WHEA* |
  Group-Object -Property LevelDisplayName, LogName -NoElement |
    Format-Table -AutoSize
```

```Output
Count  Name
-----  ----
    1  Error, PowerShellCore/Operational
   26  Information, Microsoft-Windows-Kernel-WHEA/Operational
  488  Information, Microsoft-Windows-PowerShell/Operational
   77  Information, PowerShellCore/Operational
 9835  Information, Windows PowerShell
   19  Verbose, PowerShellCore/Operational
  444  Warning, Microsoft-Windows-PowerShell/Operational
  512  Warning, PowerShellCore/Operational
```

`Get-WinEvent`Cmdleten hämtar logg information från datorn. Parametern **LogName** använder en kommaavgränsad sträng med jokertecknet asterisk ( `*` ) för att ange logg namnen. Objekten skickas ned pipelinen till `Group-Object` cmdleten. `Group-Object` använder **egenskaps** parametern för att gruppera objekten efter **LevelDisplayName** och **LogName**. Parametern **noelement** tar bort andra egenskaper från utdata. De grupperade objekten skickas ned pipelinen till `Format-Table` cmdleten. `Format-Table` använder parametern **AutoSize** för att formatera kolumnerna. Kolumnen **Count** innehåller det totala antalet varje händelse. Kolumnen **Name** innehåller grupperade **LevelDisplayName** och **LogName**.

### Exempel 11: Hämta händelser från en arkiverad händelse logg

`Get-WinEvent` kan hämta händelse information från sparade loggfiler. I det här exemplet används en arkiverad PowerShell-logg som är lagrad på den lokala datorn.

```powershell
Get-WinEvent -Path 'C:\Test\Windows PowerShell.evtx'
```

```Output
   ProviderName: PowerShell

TimeCreated              Id LevelDisplayName  Message
-----------              -- ----------------  -------
3/15/2019 13:54:13      403 Information       Engine state is changed from Available to Stopped...
3/15/2019 13:54:13      400 Information       Engine state is changed from None to Available...
3/15/2019 13:54:13      600 Information       Provider "Variable" is Started...
3/15/2019 13:54:13      600 Information       Provider "Function" is Started...
3/15/2019 13:54:13      600 Information       Provider "FileSystem" is Started...
```

`Get-WinEvent`Cmdleten hämtar logg information från datorn. Parametern **Path** anger katalog-och fil namn.

### Exempel 12: Hämta ett angivet antal händelser från en arkiverad händelse logg

De här kommandona hämtar ett angivet antal händelser från en arkiverad händelse logg. `Get-WinEvent` har parametrar som kan få maximalt antal händelser eller äldsta händelser. I det här exemplet används en arkiverad PowerShell-logg som lagras i **C:\Test\PowerShellCore-Operational. evtx**.

```powershell
Get-WinEvent -Path 'C:\Test\PowerShellCore Operational.evtx' -MaxEvents 100
```

```Output
   ProviderName: PowerShellCore

TimeCreated                 Id   LevelDisplayName  Message
-----------                 --   ----------------  -------
3/15/2019 09:54:54        4104   Warning           Creating Scriptblock text (1 of 1):...
3/15/2019 09:37:13       40962   Information       PowerShell console is ready for user input
3/15/2019 07:56:24        4104   Warning           Creating Scriptblock text (1 of 1):...
...
3/7/2019 10:53:22        40961   Information       PowerShell console is starting up
3/7/2019 10:53:22         8197   Verbose           Runspace state changed to Opening
3/7/2019 10:53:22         8195   Verbose           Opening RunspacePool
```

`Get-WinEvent`Cmdleten hämtar logg information från datorn. Parametern **Path** anger katalog och fil namn. Parametern **MaxEvents** anger att 100 poster visas, från nyaste till äldsta.

### Exempel 13: ETW (Event Tracing for Windows)

ETW (Event Tracing for Windows) (ETW) skriver händelser till loggen när händelser inträffar. Händelserna lagras i ordningen äldst till nyaste. En arkiverad ETW-fil sparas som `.etl` **tracelog. etl**.
Händelserna visas i den ordning som de skrivs till loggen, så den *äldsta* parametern krävs.

```powershell
Get-WinEvent -Path 'C:\Tracing\TraceLog.etl' -Oldest |
  Sort-Object -Property TimeCreated -Descending |
    Select-Object -First 100
```

`Get-WinEvent`Cmdleten hämtar logg information från den arkiverade filen. Parametern **Path** anger katalog-och fil namn. Den **äldsta** parametern används för att mata ut händelser i den ordning som de skrivs, äldst till nyaste. Objekten skickas ned pipelinen till `Sort-Object` cmdleten `Sort-Object` sorterar objekten i fallande ordning efter värdet för egenskapen **TimeCreated** . Objekten skickas ned pipelinen till den `Select-Object` cmdlet som visar 100 nyaste händelser.

### Exempel 14: Hämta händelser från en händelse spårnings logg

I det här exemplet visas hur du hämtar händelser från en händelse spårnings logg fil ( `.etl` ) och en arkiverad Windows PowerShell-loggfil ( `.evtx` ). Du kan kombinera flera filtyper i ett enda kommando.
Eftersom filerna innehåller samma typ av **.NET Framework** objekt, **EventLogRecord** , kan du filtrera dem med samma egenskaper. Kommandot kräver den **äldsta** parametern eftersom den läser från en `.etl` fil, men den **äldsta** parametern gäller för varje fil.

```powershell
Get-WinEvent -Path 'C:\Tracing\TraceLog.etl', 'C:\Test\Windows PowerShell.evtx' -Oldest |
  Where-Object { $_.Id -eq '403' }
```

`Get-WinEvent`Cmdleten hämtar logg information från de arkiverade filerna. Parametern **Path** använder en kommaavgränsad lista för att ange varje fil katalog och fil namn. Den **äldsta** parametern används för att mata ut händelser i den ordning som de skrivs, äldst till nyaste. Objekten skickas ned pipelinen till `Where-Object` cmdleten. `Where-Object` använder ett-skript block för att hitta händelser med och **Id** **403**. `$_`Variabeln representerar det aktuella objektet i pipelinen och **ID:** t är händelse-ID-egenskapen.

### Exempel 15: filtrera händelse loggs resultat

I det här exemplet visas flera olika metoder för att filtrera och välja händelser från en händelse logg. Alla de här kommandona hämtar händelser som inträffat under de senaste 24 timmarna från händelse loggen i **Windows PowerShell** .
Filter metoderna är mer effektiva än att använda- `Where-Object` cmdleten. Filter används när objekten hämtas. `Where-Object` hämtar alla objekt och använder sedan filter på alla objekt.

```powershell
# Using the Where-Object cmdlet:
$Yesterday = (Get-Date) - (New-TimeSpan -Day 1)
Get-WinEvent -LogName 'Windows PowerShell' | Where-Object { $_.TimeCreated -ge $Yesterday }

# Using the FilterHashtable parameter:
$Yesterday = (Get-Date) - (New-TimeSpan -Day 1)
Get-WinEvent -FilterHashtable @{ LogName='Windows PowerShell'; Level=3; StartTime=$Yesterday }

# Using the FilterXML parameter:
$xmlQuery = @'
<QueryList>
  <Query Id="0" Path="Windows PowerShell">
    <Select Path="System">*[System[(Level=3) and
        TimeCreated[timediff(@SystemTime) &lt;= 86400000]]]</Select>
  </Query>
</QueryList>
'@
Get-WinEvent -FilterXML $xmlQuery

# Using the FilterXPath parameter:
$XPath = '*[System[Level=3 and TimeCreated[timediff(@SystemTime) &lt;= 86400000]]]'
Get-WinEvent -LogName 'Windows PowerShell' -FilterXPath $XPath
```

### Exempel 16: använda FilterHashtable för att hämta händelser från program loggen

I det här exemplet används parametern **FilterHashtable** för att hämta händelser från **program** loggen. Hash-tabellen använder **nyckel/värde-** par. Mer information om parametern **FilterHashtable** finns i [skapa Get-WinEvent frågor med FilterHashtable](/powershell/scripting/samples/Creating-Get-WinEvent-queries-with-FilterHashtable).
Mer information om hash-tabeller finns i [about_Hash_Tables](../Microsoft.PowerShell.Core/about/about_hash_tables.md).

```powershell
$Date = (Get-Date).AddDays(-2)
Get-WinEvent -FilterHashtable @{ LogName='Application'; StartTime=$Date; Id='1003' }
```

`Get-Date`Cmdleten använder metoden **AddDays** för att hämta ett datum som infaller två dagar före det aktuella datumet. Date-objektet lagras i `$Date` variabeln.

`Get-WinEvent`Cmdleten hämtar logg information. Parametern **FilterHashtable** används för att filtrera utdata. Nyckeln **LogName** anger värdet som **program** logg. Nyckeln **StartTime** använder det värde som lagras i `$Date` variabeln. **ID-** nyckeln använder ett händelse-ID-värde, **1003**.

### Exempel 17: använda FilterHashtable för att hämta program fel

I det här exemplet används parametern **FilterHashtable** för att hitta program fel i Internet Explorer som inträffat under den senaste veckan.

```powershell
$StartTime = (Get-Date).AddDays(-7)
Get-WinEvent -FilterHashtable @{
  Logname='Application'
  ProviderName='Application Error'
  Data='iexplore.exe'
  StartTime=$StartTime
}
```

`Get-Date`Cmdleten använder metoden **AddDays** för att hämta ett datum som är sju dagar före det aktuella datumet. Date-objektet lagras i `$StartTime` variabeln.

`Get-WinEvent`Cmdleten hämtar logg information. Parametern **FilterHashtable** används för att filtrera utdata. Nyckeln **LogName** anger värdet som **program** logg. **ProviderName** -nyckeln använder värdet, **program felet** , som är händelsens **källa**. **Data** nyckeln använder värdet **iexplore.exe** nyckeln **StartTime** använder värdet som lagras i `$StartTime` variabeln.

### Exempel 18: använda SuppressHashFilter för att filtrera program fel

Till exempel 16 ovan använder det här exemplet **FilterHashtable** -parametern för att hämta händelser från **program** loggen. Vi lägger dock till **SuppressHashFilter** -nyckeln för att filtrera bort händelser på **informations** nivå.

```powershell
$Date = (Get-Date).AddDays(-2)
$filter = @{
  LogName='Application'
  StartTime=$Date
  SuppressHashFilter=@{Level=4}
}
Get-WinEvent -FilterHashtable $filter
```

I det här exemplet `Get-WinEvent` hämtar alla händelser från **program** loggen under de senaste två dagarna förutom de som har **nivån** 4 (information).

## PARAMETRAR

### -ComputerName

Anger namnet på den dator som denna cmdlet hämtar händelser från händelse loggarna. Ange NetBIOS-namn, en IP-adress eller det fullständigt kvalificerade domän namnet (FQDN) för datorn. Standardvärdet är den lokala datorn, **localhost**. Den här parametern accepterar bara ett dator namn i taget.

Om du vill hämta händelse loggar från fjärrdatorer konfigurerar du brand Väggs porten för händelse logg tjänsten att tillåta fjärråtkomst.

Denna cmdlet är inte beroende av PowerShell-fjärrkommunikation. Du kan använda parametern **computername** även om datorn inte är konfigurerad för att köra fjärrkommandon.

```yaml
Type: System.String
Parameter Sets: GetLogSet, ListLogSet, ListProviderSet, GetProviderSet, HashQuerySet, XmlQuerySet
Aliases: Cn

Required: False
Position: Named
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Anger ett användar konto som har behörighet att utföra den här åtgärden. Standardvärdet är den aktuella användaren.

Ange ett användar namn, till exempel **user01** eller **Domain01\User01**. Eller ange ett **PSCredential** -objekt, till exempel ett som genereras av `Get-Credential` cmdleten. Om du anger ett användar namn uppmanas du att ange ett lösen ord. Om du bara anger parameter namnet uppmanas du att ange både ett användar namn och ett lösen ord.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilterHashtable

Anger en fråga i hash-format för att välja händelser från en eller flera händelse loggar. Frågan innehåller en hash-tabell med ett eller flera **nyckel/värde-** par.

Hash-tabellfrågor har följande regler:

- Nycklar och värden är inte Skift läges känsliga.
- Jokertecken är bara giltiga i de värden som är associerade med **LogName** -och **ProviderName** -nycklarna.
- Varje nyckel kan bara listas en gång i varje hash-tabell.
- Värdet **Path** tar sökvägar till `.etl` -, `.evt` -och- `.evtx` loggfiler.
- Nycklarna **LogName** , **Path** och **ProviderName** kan användas i samma fråga.
- **UserID** -nyckeln kan ta ett giltigt säkerhets-ID (sid) eller ett domän konto namn som kan användas för att skapa ett giltigt **system. Security. objekt. NTAccount-objekt**.
- **Datavärdet** tar händelse data i ett namnlöst fält. Till exempel händelser i klassiska händelse loggar.
- `<named-data>` nyckel representerar ett namngivet händelse data fält.

När `Get-WinEvent` det inte går att tolka ett **nyckel/värde** -par tolkar den nyckeln som ett skift läges känsligt namn för händelse data i händelsen.

Giltiga `Get-WinEvent` **nyckel/värde-** par är följande:

- **LogName**=`<String[]>`
- **ProviderName**=`<String[]>`
- **Sökväg**=`<String[]>`
- **Reserverade**=`<Long[]>`
- **IDENTITET**=`<Int32[]>`
- **Nivå**=`<Int32[]>`
- **/St**=`<DateTime>`
- **Slut**=`<DateTime>`
- **UserID**=`<SID>`
- **Data**=`<String[]>`
- `<named-data>`=`<String[]>`
- **SuppressHashFilter**=`<Hashtable>`

```yaml
Type: System.Collections.Hashtable[]
Parameter Sets: HashQuerySet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilterXml

Anger en strukturerad XML-fråga som denna cmdlet väljer händelser från en eller flera händelse loggar.

Om du vill generera en giltig XML-fråga använder du funktionen **Skapa anpassad vy** och **filtrera aktuella loggar** i Windows Loggboken. Använd objekten i dialog rutan för att skapa en fråga och klicka sedan på XML-fliken för att visa frågan i XML-format. Du kan kopiera XML-filen från XML-fliken till värdet för parametern **FilterXml** . Mer information om Loggboken funktionerna finns i Loggboken hjälp.

Använd en XML-fråga för att skapa en komplex fråga som innehåller flera XPath-uttryck. XML-formatet låter dig också använda ett **dolt XML-** element som undantar händelser från frågan. Mer information om XML-schemat för händelse logg frågor finns i [query schema](/windows/win32/wes/queryschema-schema) och avsnittet XML-händelseloggen i [händelse urvalet](/previous-versions/aa385231(v=vs.85)).

Du kan också skapa ett **undertrycks** element med parametern **FilterHashtable** .

```yaml
Type: System.Xml.XmlDocument
Parameter Sets: XmlQuerySet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -FilterXPath

Anger en XPath-fråga som denna cmdlet väljer händelser från en eller flera loggar.

Mer information om XPath-språket finns i [XPath-referens](/previous-versions/dotnet/netframework-4.0/ms256115(v=vs.100)) och urvals filter avsnittet i [händelse urvalet](/previous-versions/aa385231(v=vs.85)).

```yaml
Type: System.String
Parameter Sets: GetLogSet, GetProviderSet, FileSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Hämtar fel söknings-och analys loggar, förutom andra händelse loggar. Parametern **Force** krävs för att hämta en fel söknings-eller analys logg när värdet för name-parametern innehåller jokertecken.

Som standard `Get-WinEvent` utesluter cmdleten dessa loggar om du inte anger det fullständiga namnet på en fel sökning eller analytisk logg.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GetLogSet, ListLogSet, GetProviderSet, HashQuerySet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ListLog

Anger händelse loggarna. Ange namn på händelse loggar i en kommaavgränsad lista. Jokertecken är tillåtna. Använd jokertecknet asterisk () om du vill hämta alla loggar `*` .

```yaml
Type: System.String[]
Parameter Sets: ListLogSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -ListProvider

Anger de händelse logg leverantörer som denna cmdlet hämtar. En händelse logg leverantör är ett program eller en tjänst som skriver händelser till händelse loggen.

Ange leverantörs namnen i en kommaavgränsad lista. Jokertecken är tillåtna. Använd jokertecknet asterisk () om du vill hämta providers för alla händelse loggar på datorn `*` .

```yaml
Type: System.String[]
Parameter Sets: ListProviderSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -LogName

Anger händelse loggar som denna cmdlet hämtar händelser från. Ange namn på händelse loggar i en kommaavgränsad lista. Jokertecken är tillåtna. Du kan också skicka logg namn till- `Get-WinEvent` cmdlet: en.

> [!NOTE]
> PowerShell begränsar inte mängden loggar som du kan begära. `Get-WinEvent`Cmdlet: en frågar dock Windows API, som har en gräns på 256. Detta kan göra det svårt att filtrera igenom alla dina loggar på en och samma tidpunkt. Du kan undvika detta genom att använda en `foreach` loop för att iterera igenom varje logg så här: `Get-WinEvent -ListLog * | ForEach-Object{ Get-WinEvent -LogName $_.Logname }`

```yaml
Type: System.String[]
Parameter Sets: GetLogSet
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### – MaxEvents

Anger det maximala antalet händelser som returneras. Ange ett heltal som 100. Standardvärdet är att returnera alla händelser i loggarna eller filerna.

```yaml
Type: System.Int64
Parameter Sets: GetLogSet, GetProviderSet, FileSet, HashQuerySet, XmlQuerySet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Äldst

Ange att denna cmdlet hämtar händelserna i den äldsta-första ordningen. Som standard returneras händelser i den nyaste-första ordningen.

Den här parametern krävs för att hämta händelser från `.etl` och `.evt` filer och från fel söknings-och analys loggar. I de här filerna registreras händelser i den äldsta-första ordningen och händelserna kan bara returneras i den äldsta första ordningen.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: GetLogSet, GetProviderSet, FileSet, HashQuerySet, XmlQuerySet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Anger sökvägen till de händelse loggs filer som denna cmdlet hämtar händelser från. Ange Sök vägarna till loggfilerna i en kommaavgränsad lista eller Använd jokertecken för att skapa mönster för fil Sök vägar.

`Get-WinEvent` stöder filer med `.evt` `.evtx` `.etl` fil namns tilläggen, och. Du kan inkludera händelser från olika filer och filtyper i samma kommando.

```yaml
Type: System.String[]
Parameter Sets: FileSet
Aliases: PSPath

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -ProviderName

Anger, som en sträng mat ris, de händelse logg leverantörer från vilka denna cmdlet hämtar händelser. Ange leverantörs namnen i en kommaavgränsad lista eller Använd jokertecken för att skapa namn mönster för providern.

En händelse logg leverantör är ett program eller en tjänst som skriver händelser till händelse loggen. Det är inte en PowerShell-Provider.

```yaml
Type: System.String[]
Parameter Sets: GetProviderSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String, System.Xml.Xml-dokument, system. Collections. hash

Du kan pipelina en **LogName** (sträng), en **FilterXML** -fråga eller en **FilterHashtable** -fråga till `Get-WinEvent` .

## UTDATA

### System. Diagnostics. Eventing. Reader. EventLogConfiguration, system. Diagnostics. Eventing. Reader. EventLogRecord, system. Diagnostics. Eventing. Reader. ProviderMetadata

Med parametern **ListLog** `Get-WinEvent` returneras **system. Diagnostics. Eventing. Reader. EventLogConfiguration** -objekt.

Med parametern **ListProvider** `Get-WinEvent` returneras **system. Diagnostics. Eventing. Reader. ProviderMetadata** -objekt.

Med alla andra parametrar `Get-WinEvent` returneras **system. Diagnostics. Eventing. Reader. EventLogRecord** -objekt.

## ANTECKNINGAR

`Get-WinEvent` är utformad för att ersätta `Get-EventLog` cmdleten på datorer som kör Windows Vista och senare versioner av Windows. `Get-EventLog` hämtar endast händelser i klassiska händelse loggar. `Get-EventLog` kvarhålls för bakåtkompatibilitet.

`Get-WinEvent` `Get-EventLog` Cmdletarna och stöds inte i Windows PE (Windows pre-installation Environment).

## RELATERADE LÄNKAR

[about_Automatic_Variables](../Microsoft.PowerShell.Core/about/about_automatic_variables.md)

[about_Foreach](../Microsoft.PowerShell.Core/about/about_Foreach.md)

[about_Hash_Tables](../Microsoft.PowerShell.Core/about/about_hash_tables.md)

[Skapar Get-WinEvent-frågor med FilterHashtable](/powershell/scripting/samples/Creating-Get-WinEvent-queries-with-FilterHashtable)

[Format-Table](../Microsoft.PowerShell.Utility/Format-Table.md)

[Gruppera objekt](../Microsoft.PowerShell.Utility/Group-Object.md)

[Sortera objekt](../Microsoft.PowerShell.Utility/Sort-Object.md)

[Where-objekt](../Microsoft.PowerShell.Core/Where-Object.md)
