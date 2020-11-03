---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/sort-object?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Sort-Object
ms.openlocfilehash: 1d27641f94d82b85bab694b392c0f09bb3265517
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/10/2020
ms.locfileid: "93268964"
---
# Sort-Object

## SAMMANFATTNING
Sorterar objekt efter egenskaps värden.

## SYNTAX

### Standard (standard)

```
Sort-Object [[-Property] <Object[]>] [-Descending] [-Unique] [-InputObject <psobject>]
 [-Culture <string>] [-CaseSensitive] [<CommonParameters>]
```

## BESKRIVNING

`Sort-Object`Cmdlet sorterar objekt i stigande eller fallande ordning baserat på objekt egenskaps värden. Om sorterings egenskaper inte ingår i ett kommando använder PowerShell standard sorterings egenskaper för det första objektet. Om typen av inobjektet inte har några standard sorterings egenskaper försöker PowerShell att jämföra själva objekten. Mer information finns i avsnittet om [anteckningar](#notes) .

Du kan sortera objekt efter en enskild egenskap eller flera egenskaper. Flera egenskaper använder hash-tabeller för att sortera i stigande ordning, fallande ordning eller en kombination av sorterings ordning. Egenskaperna sorteras som Skift läges känsliga eller Skift läges känsliga. Använd den **unika** parametern för att eliminera dubbletter från utdata.

## EXEMPEL

### Exempel 1: sortera den aktuella katalogen efter namn

Det här kommandot sorterar filer och under kataloger i en katalog.

```
PS> Get-ChildItem -Path C:\Test | Sort-Object

    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     08:55             26 anotherfile.txt
-a----        2/13/2019     13:26             20 Bfile.txt
-a----        2/12/2019     15:40         118014 Command.txt
-a----         2/1/2019     08:43            183 CreateTestFile.ps1
d-----        2/25/2019     18:25                Files
d-----        2/25/2019     18:24                Logs
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
-a----        2/12/2019     16:24             23 Zsystemlog.log
```

Cmdlet: en `Get-ChildItem` hämtar filer och under kataloger från katalogen som anges av **Sök vägs** parametern, **C:\test**. Objekten skickas ned pipelinen till `Sort-Object` cmdleten.
`Sort-Object` anger ingen egenskap så utdata sorteras efter standard sorterings egenskap, **namn**.

### Exempel 2: sortera den aktuella katalogen efter fil längd

Det här kommandot visar filerna i den aktuella katalogen efter längd i stigande ordning.

```
PS> Get-ChildItem -Path C:\Test -File | Sort-Object -Property Length

    Directory: C:\Test

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        2/13/2019     13:26             20 Bfile.txt
-a----        2/12/2019     16:24             23 Zsystemlog.log
-a----        2/13/2019     08:55             26 anotherfile.txt
-ar---        2/12/2019     14:31             27 ReadOnlyFile.txt
-a----         2/1/2019     08:43            183 CreateTestFile.ps1
-a----        2/12/2019     15:40         118014 Command.txt
```

`Get-ChildItem`Cmdlet: en hämtar filerna från katalogen som anges i parametern **Path** .
Parametern **File** anger att `Get-ChildItem` endast fil objekt ska hämtas. Objekten skickas ned pipelinen till `Sort-Object` cmdleten. `Sort-Object` använder parametern **length** för att sortera filerna efter längd i stigande ordning.

### Exempel 3: sortera processer efter minnes användning

I det här exemplet visas processer med högsta minnes användning baserat på storleken på deras arbets minne (WS).

```
PS> Get-Process | Sort-Object -Property WS | Select-Object -Last 5

 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
    136   193.92     217.11     889.16   87492   8 OUTLOOK
    112   347.73     297.02      95.19  106908   8 Teams
    206   266.54     323.71      37.17   60620   8 MicrosoftEdgeCP
     35   552.19     549.94     131.66    6552   8 Code
      0     1.43     595.12       0.00    2780   0 Memory Compression
```

`Get-Process`Cmdleten hämtar listan över processer som körs på datorn. Process objekt skickas ned pipelinen till `Sort-Object` cmdleten. `Sort-Object` använder **egenskaps** parametern för att sortera objekten efter **WS**. Objekten skickas ned pipelinen till `Select-Object` cmdleten.
`Select-Object` använder den **sista** parametern för att ange de sista fem objekten, som är de objekt som har högst **WS** -användning.

### Exempel 4: sortera HistoryInfo-objekt efter ID

Det här kommandot sorterar PowerShell-sessionens **HistoryInfo** -objekt med egenskapen **ID** . Varje PowerShell-session har en egen kommando historik.

```
PS> Get-History | Sort-Object -Property Id -Descending

  Id CommandLine
  -- -----------
  10 Get-Command Sort-Object -Syntax
   9 $PSVersionTable
   8 Get-Command Sort-Object -Syntax
   7 Get-Command Sort-Object -ShowCommandInfo
   6 Get-ChildItem -Path C:\Test | Sort-Object -Property Length
   5 Get-Help Clear-History -online
   4 Get-Help Clear-History -full
   3 Get-ChildItem | Get-Member
   2 Get-Command Sort-Object -Syntax
   1 Set-Location C:\Test\
```

`Get-History`Cmdlet: en hämtar historik objekt från den aktuella PowerShell-sessionen. Objekten skickas ned pipelinen till `Sort-Object` cmdleten. `Sort-Object` använder **egenskaps** parametern för att sortera objekten efter **ID**. Den **fallande** parametern sorterar kommando historiken från nyaste till äldsta.

### Exempel 5: Använd en hash-tabell för att sortera egenskaper i stigande och fallande ordning

Det här kommandot använder två egenskaper för att sortera objekt, **status** och **DisplayName**. **Status** sorteras i fallande ordning och **DisplayName** sorteras i stigande ordning.

En hash-tabell används för att ange **egenskaps** parameterns värde. Hash-tabellen använder ett uttryck för att ange egenskaps namn och sorterings ordning. Mer information om hash-tabeller finns i [about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md).

**Status** egenskapen som används i hash-tabellen är en uppräknad egenskap.
Mer information finns i [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).

```
PS C:\> Get-Service | Sort-Object -Property @{Expression = "Status"; Descending = $True}, @{Expression = "DisplayName"; Descending = $False}

Status   Name               DisplayName
------   ----               -----------
Running  Appinfo            Application Information
Running  BthAvctpSvc        AVCTP service
Running  BrokerInfrastru... Background Tasks Infrastructure Ser...
Running  BDESVC             BitLocker Drive Encryption Service
Running  CoreMessagingRe... CoreMessaging
Running  VaultSvc           Credential Manager
Running  DsSvc              Data Sharing Service
Running  Dhcp               DHCP Client
...
Stopped  ALG                Application Layer Gateway Service
Stopped  AppMgmt            Application Management
Stopped  BITS               Background Intelligent Transfer Ser...
Stopped  wbengine           Block Level Backup Engine Service
Stopped  BluetoothUserSe... Bluetooth User Support Service_14fb...
Stopped  COMSysApp          COM+ System Application
Stopped  smstsmgr           ConfigMgr Task Sequence Agent
Stopped  DeviceInstall      Device Install Service
Stopped  MSDTC              Distributed Transaction Coordinator
```

`Get-Service`Cmdlet: en hämtar listan över tjänster på datorn. Tjänst objekt skickas ned pipelinen till `Sort-Object` cmdleten. `Sort-Object` använder **egenskaps** parametern med en hash-tabell för att ange egenskaps namn och sorterings ordning. **Egenskaps** parametern sorteras efter två egenskaper, **status** i fallande ordning och **DisplayName** i stigande ordning.

**Status** är en uppräknad egenskap. **Stoppad** har värdet **1** och **körs** har värdet **4**. Den **fallande** parametern anges till `$True` så att processer som **körs** visas innan **stoppade** processer. **DisplayName** anger **fallande** parameter för `$False` att sortera visnings namnen i alfabetisk ordning.

### Exempel 6: sortera textfiler efter tids period

Det här kommandot sorterar textfiler i fallande ordning efter tidsintervallet mellan **CreationTime** och **LastWriteTime**.

```
PS> Get-ChildItem -Path C:\Test\*.txt | Sort-Object -Property @{Expression = {$_.CreationTime - $_.LastWriteTime}; Descending = $False} | Format-Table CreationTime, LastWriteTime, FullName

CreationTime          LastWriteTime        FullName
------------          -------------        --------
11/21/2018 12:39:01   2/26/2019 08:59:36   C:\Test\test2.txt
12/4/2018 08:29:41    2/26/2019 08:57:05   C:\Test\powershell_list.txt
2/20/2019 08:15:59    2/26/2019 12:09:43   C:\Test\CreateTestFile.txt
2/20/2019 08:15:59    2/26/2019 12:07:41   C:\Test\Command.txt
2/20/2019 08:15:59    2/26/2019 08:57:52   C:\Test\ReadOnlyFile.txt
11/29/2018 15:16:50   12/4/2018 16:16:24   C:\Test\LogData.txt
2/25/2019 18:25:11    2/26/2019 12:08:47   C:\Test\Zsystemlog.txt
2/25/2019 18:25:11    2/26/2019 08:55:33   C:\Test\Bfile.txt
2/26/2019 08:46:59    2/26/2019 12:12:19   C:\Test\LogFile3.txt

```

`Get-ChildItem`Cmdleten använder parametern **Path** för att ange katalogen **C:\test** och alla `*.txt` filer. Objekten skickas ned pipelinen till `Sort-Object` cmdleten.
`Sort-Object` använder **egenskaps** parametern med en hash-tabell för att avgöra varje fil intervall mellan **CreationTime** och **LastWriteTime**. Parametern **fallande** är inställd på `$False` att sortera i ordningen längst till kortast tids period.

### Exempel 7: Sortera namn i en textfil

Det här exemplet visar hur du sorterar en lista från en textfil. Den ursprungliga filen visas som en osorterad lista. `Sort-Object` sorterar innehållet och sorterar innehållet med den **unika** parameter som tar bort dubbletter.

```
PS> Get-Content -Path C:\Test\ServerNames.txt
localhost
server01
server25
LOCALHOST
Server19
server3
localhost

PS> Get-Content -Path C:\Test\ServerNames.txt | Sort-Object
localhost
LOCALHOST
localhost
server01
Server19
server25
server3

PS> Get-Content -Path C:\Test\ServerNames.txt | Sort-Object -Unique
localhost
server01
Server19
server25
server3
```

`Get-Content`Cmdleten använder parametern **Path** för att ange katalog och fil namn. Filen **ServerNames.txt** innehåller en osorterad lista med dator namn.

`Get-Content`Cmdleten använder parametern **Path** för att ange katalog och fil namn. Filen **ServerNames.txt** innehåller en osorterad lista med dator namn. Objekten skickas ned pipelinen till `Sort-Object` cmdleten. `Sort-Object` sorterar listan i standard ordningen, stigande.

`Get-Content`Cmdleten använder parametern **Path** för att ange katalog och fil namn. Filen **ServerNames.txt** innehåller en osorterad lista med dator namn. Objekten skickas ned pipelinen till `Sort-Object` cmdleten. `Sort-Object` använder den **unika** parametern för att ta bort dubbla dator namn. Listan sorteras i standard ordningen, stigande.

### Exempel 8: sortera en sträng som ett heltal

Det här exemplet visar hur du sorterar en textfil som innehåller sträng objekt som heltal. Du kan skicka varje kommando nedåt i pipeline till `Get-Member` och kontrol lera att objekten är strängar i stället för heltal. I de här exemplen `ProductId.txt` innehåller filen en osorterad lista med produkt nummer.

I det första exemplet `Get-Content` hämtar innehållet i filen och pipe-raderna till- `Sort-Object` cmdleten. `Sort-Object` sorterar sträng objekt i stigande ordning.

```
PS> Get-Content -Path C:\Test\ProductId.txt | Sort-Object
0
1
12345
1500
2
2800
3500
4100
500
6200
77
88
99999

PS> Get-Content -Path C:\Test\ProductId.txt | Sort-Object {[int]$_}
0
1
2
77
88
500
1500
2800
3500
4100
6200
12345
99999
```

I det andra exemplet `Get-Content` hämtar innehållet i filen och pipe-raderna till- `Sort-Object` cmdleten. `Sort-Object` använder ett-skript block för att konvertera strängarna till heltal. I exempel koden `[int]` konverterar strängen till ett heltal och `$_` representerar varje sträng som den kommer nedåt i pipelinen. Heltals objekt skickas ned pipelinen till `Sort-Object` cmdleten.
`Sort-Object` sorterar heltals objekt i numerisk ordning.

`Get-Content`Cmdleten använder parametern **Path** för att ange katalog och fil namn. Filen **ProductId.txt** innehåller en osorterad lista med produkt nummer. String-objekten skickas ned pipelinen till `ForEach-Object` cmdleten. `ForEach-Object` använder ett-skript block för att konvertera strängarna till heltal. I exempel koden `[int]` konverterar strängen till ett heltal och `$_` representerar varje sträng som den kommer nedåt i pipelinen. Heltals objekt skickas ned pipelinen till `Sort-Object` cmdleten. `Sort-Object` sorterar heltals objekt i numerisk ordning.
## PARAMETRAR

### -CaseSensitive

Anger att sorteringen är Skift läges känslig. Som standard är sorteringar inte Skift läges känsliga.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Case-insensitive
Accept pipeline input: False
Accept wildcard characters: False
```

### – Kultur

Anger den kulturella konfiguration som ska användas för sortering. Används `Get-Culture` för att Visa systemets kultur konfiguration.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Fallande

Anger att `Sort-Object` objekten sorteras i fallande ordning. Standardvärdet är stigande ordning.

Om du vill sortera flera egenskaper med olika sorterings ordning använder du en hash-tabell. Med en hash-tabell kan du till exempel sortera en egenskap i stigande ordning och en annan egenskap i fallande ordning.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Ascending
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject

Om du vill sortera objekt kan du skicka dem nedåt i pipeline till `Sort-Object` . Om du använder parametern **InputObject** för att skicka en samling objekt, `Sort-Object` tar emot ett objekt som representerar samlingen. Eftersom ett objekt inte kan sorteras, `Sort-Object` returnerar hela samlingen oförändrad.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### – Egenskap

Anger de egenskaps namn som `Sort-Object` används för att sortera objekten. Jokertecken är tillåtna.
Objekten sorteras baserat på egenskaps värden. Om du inte anger någon egenskap, `Sort-Object` sorteras baserat på standard egenskaper för objekt typen eller själva objekten.

Flera egenskaper kan sorteras i stigande ordning, fallande ordning eller en kombination av sorterings ordningar. När du anger flera egenskaper sorteras objekten efter den första egenskapen. Om flera objekt har samma värde för den första egenskapen, sorteras dessa objekt efter den andra egenskapen. Den här processen fortsätter tills det inte finns några fler angivna egenskaper eller inga grupper av objekt.

**Egenskaps** parameterns värde kan vara en beräknad egenskap. Använd en hash-tabell om du vill skapa en beräknad egenskap.

Giltiga nycklar för en hash-tabell är följande:

- `expression` - `<string>` eller `<script block>`
- `ascending` eller `descending` - `<boolean>`

Mer information finns i [about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md).

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: Default properties
Accept pipeline input: False
Accept wildcard characters: True
```

### – Unik

Anger att `Sort-Object` tar bort dubbletter och returnerar bara de unika medlemmarna i samlingen. Den första instansen av ett unikt värde ingår i de sorterade utdata.

**Unique** är Skift läges okänsligt. Strängar som endast skiljer sig från versaler anses vara identiska.
Till exempel, Character och CHARACTER.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: All
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Management. Automation. PSObject

Du kan skicka vidare de objekt som ska sorteras till `Sort-Object` .

## UTDATA

### System. Management. Automation. PSObject

`Sort-Object` Returnerar de sorterade objekten.

## ANTECKNINGAR

`Sort-Object`Cmdlet sorterar objekt baserat på egenskaper som anges i kommandot eller standard sorterings egenskaperna för objekt typen. Standard sorterings egenskaper definieras med hjälp av `PropertySet` namnet `DefaultKeyPropertySet` i en `types.ps1xml` fil. Mer information finns i [about_Types.ps1XML](/powershell/module/Microsoft.PowerShell.Core/About/about_Types.ps1xml).

Om ett objekt inte har någon av de angivna egenskaperna tolkas egenskap svärdet för objektet med `Sort-Object` **Null** och placeras i slutet av sorterings ordningen.

När inga sorterings egenskaper är tillgängliga försöker PowerShell att jämföra själva objekten.
`Sort-Object` använder metoden **compare** för varje egenskap. Om en egenskap inte implementerar **IComparable** , konverterar cmdleten egenskap svärdet till en sträng och använder metoden **compare** för **system. String**. Mer information finns i [metoden PSObject. CompareTo (Object)](/dotnet/api/system.management.automation.psobject.compareto).

Om du sorterar efter en uppräknad egenskap, till exempel **status** , `Sort-Object` sorteras efter uppräknings värden. För Windows-tjänster har **stoppat** värdet **1** och **körs** har värdet **4**.
**Stoppad** sorteras före **körning** på grund av uppräknade värden. Mer information finns i [ServiceControllerStatus](/dotnet/api/system.serviceprocess.servicecontrollerstatus).

## RELATERADE LÄNKAR

[about_Calculated_Properties](../Microsoft.PowerShell.Core/About/about_Calculated_Properties.md)

[about_Hash_Tables](../Microsoft.PowerShell.Core/About/about_Hash_Tables.md)

[about_Types.ps1XML](../Microsoft.PowerShell.Core/About/about_Types.ps1xml.md)

[Jämför objekt](Compare-Object.md)

[-Objekt](../Microsoft.PowerShell.Core/ForEach-Object.md)

[Gruppera objekt](Group-Object.md)

[Mått – objekt](Measure-Object.md)

[Nytt – objekt](New-Object.md)

[Select-Object](Select-Object.md)

[Tee – objekt](Tee-Object.md)
