---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 3/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-EventLog
ms.openlocfilehash: ab1a97dc3c78bbfdcc239fd573ef3b1f839e2b21
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266162"
---
# Get-EventLog

## SAMMANFATTNING
Hämtar händelserna i en händelse logg eller en lista över händelse loggar på den lokala datorn eller fjärrdatorn.

## SYNTAX

### LogName (standard)

```
Get-EventLog [-LogName] <String> [-ComputerName <String[]>] [-Newest <Int32>] [-After <DateTime>]
 [-Before <DateTime>] [-UserName <String[]>] [[-InstanceId] <Int64[]>] [-Index <Int32[]>]
 [-EntryType <String[]>] [-Source <String[]>] [-Message <String>] [-AsBaseObject]
 [<CommonParameters>]
```

### Lista

```
Get-EventLog [-ComputerName <String[]>] [-List] [-AsString] [<CommonParameters>]
```

## BESKRIVNING

`Get-EventLog`Cmdleten hämtar händelser och händelse loggar från lokala datorer och fjärrdatorer. Som standard `Get-EventLog` hämtar loggar från den lokala datorn. Använd parametern **computername** för att hämta loggar från fjärrdatorer.

Du kan använda `Get-EventLog` parameter-och egenskaps värden för att söka efter händelser. Cmdleten hämtar händelser som matchar angivna egenskaps värden.

PowerShell-cmdletar som innehåller `EventLog` Substantiv fungerar endast på Windows klassiska händelse loggar som program, system eller säkerhet. Använd för att hämta loggar som använder Windows händelse logg teknik i Windows Vista och senare versioner av Windows `Get-WinEvent` .

> [!NOTE]
> `Get-EventLog` använder ett Win32-API som är föråldrat. Resultatet kanske inte stämmer. Använd `Get-WinEvent` cmdleten i stället.

## EXEMPEL

### Exempel 1: Hämta händelse loggar på den lokala datorn

I det här exemplet visas en lista över händelse loggar som är tillgängliga på den lokala datorn. Namnen i kolumnen logg används med parametern **LogName** för att ange vilken logg som söks efter händelser.

```powershell
Get-EventLog -List
```

```Output
Max(K)   Retain   OverflowAction      Entries  Log
------   ------   --------------      -------  ---
15,168        0   OverwriteAsNeeded   20,792   Application
15,168        0   OverwriteAsNeeded   12,559   System
15,360        0   OverwriteAsNeeded   11,173   Windows PowerShell
```

`Get-EventLog`Cmdleten använder **list** parametern för att visa tillgängliga loggar.

### Exempel 2: Hämta nya poster från en händelse logg på den lokala datorn

I det här exemplet hämtas de senaste posterna från system händelse loggen.

```powershell
Get-EventLog -LogName System -Newest 5
```

```Output
Index   Time          EntryType    Source              InstanceID   Message
-----   ----          ---------    ------              ----------   -------
13820   Jan 17 19:16  Error        DCOM                     10016   The description for Event...
13819   Jan 17 19:08  Error        DCOM                     10016   The description for Event...
13818   Jan 17 19:06  Information  Service Control...  1073748864   The start type of the Back...
13817   Jan 17 19:05  Error        DCOM                     10016   The description for Event...
13815   Jan 17 19:03  Information  Microsoft-Windows...        35   The time service is now sync...
```

`Get-EventLog`Cmdleten använder parametern **LogName** för att ange system händelse loggen. Den **nyaste** parametern returnerar de fem senaste händelserna.

### Exempel 3: Sök efter alla källor för ett angivet antal poster i en händelse logg

Det här exemplet visar hur du hittar alla källor som ingår i de 1000 senaste posterna i system händelse loggen.

```powershell
$Events = Get-EventLog -LogName System -Newest 1000
$Events | Group-Object -Property Source -NoElement | Sort-Object -Property Count -Descending
```

```Output
Count   Name
-----   ----
  110   DCOM
   65   Service Control Manager
   51   Microsoft-Windows-Kern...
   14   EventLog
   14   BTHUSB
   13   Win32k
```

`Get-EventLog`Cmdleten använder parametern **LogName** för att ange system loggen. Den **nyaste** parametern väljer de 1000 senaste händelserna. Händelse objekt lagras i `$Events` variabeln. `$Events`Objekten skickas ned pipelinen till `Group-Object` cmdleten.
`Group-Object` använder **egenskaps** parametern för att gruppera objekten efter källa och räknar antalet objekt för varje källa. Parametern **noelement** tar bort grupp medlemmar från utdata.
`Sort-Object`Cmdleten använder **egenskaps** parametern för att sortera efter antalet käll namn.
Parametern **fallande** sorterar listan i ordning efter antal från högst till lägsta.

### Exempel 4: Hämta fel händelser från en speciell händelse logg

Det här exemplet hämtar fel händelser från system händelse loggen.

```powershell
Get-EventLog -LogName System -EntryType Error
```

```Output
Index Time          EntryType   Source  InstanceID Message
----- ----          ---------   ------  ---------- -------
13296 Jan 16 13:53  Error       DCOM    10016 The description for Event ID '10016' in Source...
13291 Jan 16 13:51  Error       DCOM    10016 The description for Event ID '10016' in Source...
13245 Jan 16 11:45  Error       DCOM    10016 The description for Event ID '10016' in Source...
13230 Jan 16 11:07  Error       DCOM    10016 The description for Event ID '10016' in Source...
```

`Get-EventLog`Cmdleten använder parametern **LogName** för att ange system loggen. Parametern **EntryType** filtrerar händelser så att endast fel händelser visas.

### Exempel 5: Hämta händelser från en händelse logg med ett InstanceId-och käll värde

I det här exemplet hämtas händelser från system loggen för ett särskilt InstanceId och en källa.

```powershell
Get-EventLog -LogName System -InstanceId 10016 -Source DCOM
```

```Output
Index Time          EntryType  Source  InstanceID  Message
----- ----          ---------  ------  ----------  -------
13245 Jan 16 11:45  Error      DCOM         10016  The description for Event ID '10016' in Source...
13230 Jan 16 11:07  Error      DCOM         10016  The description for Event ID '10016' in Source...
13219 Jan 16 10:00  Error      DCOM         10016  The description for Event ID '10016' in Source...
```

`Get-EventLog`Cmdleten använder parametern **LogName** för att ange system loggen. Parametern **InstanceID** väljer händelser med angivet instans-ID. Parametern **Source** anger händelse egenskapen.

### Exempel 6: Hämta händelser från flera datorer

Det här kommandot hämtar händelserna från system händelse loggen på tre datorer: Server01, Server02 och Server03.

```powershell
Get-EventLog -LogName System -ComputerName Server01, Server02, Server03
```

`Get-EventLog`Cmdleten använder parametern **LogName** för att ange system loggen. Parametern **computername** använder en kommaavgränsad sträng för att visa en lista över de datorer som du vill hämta händelse loggarna från.

### Exempel 7: Hämta alla händelser som innehåller ett särskilt ord i meddelandet

Det här kommandot hämtar alla händelser i system händelse loggen som innehåller ett särskilt ord i händelsens meddelande. Det är möjligt att den angivna **meddelande** parameterns värde ingår i meddelandets innehåll men inte visas i PowerShell-konsolen.

```powershell
Get-EventLog -LogName System -Message *description*
```

```Output
Index Time          EntryType   Source       InstanceID   Message
----- ----          ---------   ------       ----------   -------
13821 Jan 17 19:17  Error       DCOM              10016   The description for Event ID '10016'...
13820 Jan 17 19:16  Error       DCOM              10016   The description for Event ID '10016'...
13819 Jan 17 19:08  Error       DCOM              10016   The description for Event ID '10016'...
```

`Get-EventLog`Cmdleten använder parametern **LogName** för att ange system händelse loggen. Parametern **Message** anger ett ord att söka efter i meddelande fältet för varje händelse.

### Exempel 8: Visa egenskaps värden för en händelse

Det här exemplet visar hur du visar alla egenskaper och värden för en händelse.

```powershell
$A = Get-EventLog -LogName System -Newest 1
$A | Select-Object -Property *
```

```Output
EventID            : 10016
MachineName        : localhost
Data               : {}
Index              : 13821
Category           : (0)
CategoryNumber     : 0
EntryType          : Error
Message            : The description for Event ID '10016' in Source 'DCOM'...
Source             : DCOM
ReplacementStrings : {Local,...}
InstanceId         : 10016
TimeGenerated      : 1/17/2019 19:17:23
TimeWritten        : 1/17/2019 19:17:23
UserName           : username
Site               :
Container          :
```

`Get-EventLog`Cmdleten använder parametern **LogName** för att ange system händelse loggen. Den **nyaste** parametern väljer det senaste händelse objekt. Objektet lagras i `$A` variabeln. Objektet i `$A` variabeln skickas ned pipelinen till `Select-Object` cmdleten.
`Select-Object` använder **egenskaps** parametern med en asterisk ( `*` ) för att markera alla objekt egenskaper.

### Exempel 9: Hämta händelser från en händelse logg med ett käll-och händelse-ID

I det här exemplet hämtas händelser för ett angivet käll-och händelse-ID.

```powershell
Get-EventLog -LogName Application -Source Outlook | Where-Object {$_.EventID -eq 63} |
              Select-Object -Property Source, EventID, InstanceId, Message
```

```Output
Source   EventID   InstanceId   Message
------   -------   ----------   -------
Outlook       63   1073741887   The Exchange web service request succeeded.
Outlook       63   1073741887   Outlook detected a change notification.
Outlook       63   1073741887   The Exchange web service request succeeded.
```

`Get-EventLog`Cmdleten använder parametern **LogName** för att ange program händelse loggen. Parametern **Source** anger program namnet, Outlook. Objekten skickas ned pipelinen till `Where-Object` cmdleten. För varje objekt i pipelinen `Where-Object` använder cmdleten variabeln `$_.EventID` för att jämföra händelse-ID-egenskapen med det angivna värdet. Objekten skickas ned pipelinen till `Select-Object` cmdleten. `Select-Object` använder **egenskaps** parametern för att välja de egenskaper som ska visas i PowerShell-konsolen.

### Exempel 10: Hämta händelser och grupper efter en egenskap

```powershell
Get-EventLog -LogName System -UserName NT* | Group-Object -Property UserName -NoElement |
              Select-Object -Property Count, Name
```

```Output
Count  Name
-----  ----
6031   NT AUTHORITY\SYSTEM
  42   NT AUTHORITY\LOCAL SERVICE
   4   NT AUTHORITY\NETWORK SERVICE
```

`Get-EventLog`Cmdleten använder parametern **LogName** för att ange system loggen. Parametern **username** innehåller jokertecknet asterisk ( `*` ) för att ange en del av användar namnet. Händelse objekten skickas ned pipelinen till `Group-Object` cmdleten. `Group-Object` använder **egenskaps** parametern för att ange att egenskapen **username** används för att gruppera objekten och räknar antalet objekt för varje användar namn. Parametern **noelement** tar bort grupp medlemmar från utdata. Objekten skickas ned pipelinen till `Select-Object` cmdleten.
`Select-Object` använder **egenskaps** parametern för att välja de egenskaper som ska visas i PowerShell-konsolen.

### Exempel 11: Hämta händelser som inträffat under ett visst datum-och tidsintervall

Det här exemplet hämtar fel händelser från system händelse loggen för ett angivet datum-och tidsintervall. Parametrarna **före** och **efter** anger datum-och tidsintervallet, men exkluderas från utdata.

```powershell
$Begin = Get-Date -Date '1/17/2019 08:00:00'
$End = Get-Date -Date '1/17/2019 17:00:00'
Get-EventLog -LogName System -EntryType Error -After $Begin -Before $End
```

```Output
Index Time          EntryType   Source   InstanceID  Message
----- ----          ---------   ------   ----------  -------
13821 Jan 17 13:40  Error       DCOM          10016  The description for Event ID...
13820 Jan 17 13:11  Error       DCOM          10016  The description for Event ID...
...
12372 Jan 17 10:08  Error       DCOM          10016  The description for Event ID...
12371 Jan 17 09:04  Error       DCOM          10016  The description for Event ID...
```

`Get-Date`Cmdleten använder parametern **date** för att ange ett datum och en tid. **Datetime** -objekten lagras i `$Begin` `$End` variablerna och. `Get-EventLog`Cmdleten använder parametern **LogName** för att ange system loggen. Parametern **EntryType** anger fel händelse typ. Datum-och tidsintervallet anges av **efter** -parametern och `$Begin` variabeln och **före** -parametern och `$End` variabeln.

## PARAMETRAR

### – Efter

Hämtar händelser som inträffat efter ett angivet datum och tid. Datum och tid för parametern **efter** tas inte med i utdata. Ange ett **datetime** -objekt, till exempel det värde som returneras av `Get-Date` cmdleten.

```yaml
Type: System.DateTime
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -AsBaseObject

Anger att denna cmdlet returnerar ett standard **system. Diagnostics. EventLogEntry** -objekt för varje händelse. Utan den här parametern `Get-EventLog` returnerar ett utökat **PSObject** -objekt med ytterligare egenskaper för **EventLogName** , **Source** och **InstanceID** .

Om du vill se resultatet av den här parametern kan du skicka vidare händelserna till cmdlet: en `Get-Member` och granska värdet **TypeName** i resultatet.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Uppsträng

Anger att denna cmdlet returnerar utdata som strängar, i stället för objekt.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: List
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Före

Hämtar händelser som inträffat före ett angivet datum och tid. **Innan** parameterns datum och tid undantas från utdata. Ange ett **datetime** -objekt, till exempel det värde som returneras av `Get-Date` cmdleten.

```yaml
Type: System.DateTime
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Den här parametern anger en fjärrdators NetBIOS-namn, Internet Protocol IP-adress eller ett fullständigt kvalificerat domän namn (FQDN).

Om parametern **computername** inte anges används `Get-EventLog` standardvärdet för den lokala datorn. Parametern accepterar också en punkt ( `.` ) för att ange den lokala datorn.

Parametern **computername** är inte beroende av Windows PowerShell-fjärrkommunikation. Du kan använda `Get-EventLog` med parametern **computername** även om datorn inte är konfigurerad för att köra fjärrkommandon.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – EntryType

Anger, som en sträng mat ris, post typen för de händelser som denna cmdlet hämtar.

De acceptabla värdena för den här parametern är:

- Fel
- Information
- FailureAudit
- SuccessAudit
- Varning

```yaml
Type: System.String[]
Parameter Sets: LogName
Aliases: ET
Accepted values: Error, Information, FailureAudit, SuccessAudit, Warning

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Index

Anger de index värden som ska hämtas från händelse loggen. Parametern accepterar en kommaavgränsad sträng med värden.

```yaml
Type: System.Int32[]
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -InstanceId

Anger de instans-ID: n som ska hämtas från händelse loggen. Parametern accepterar en kommaavgränsad sträng med värden.

```yaml
Type: System.Int64[]
Parameter Sets: LogName
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Lista

Visar en lista över händelse loggar på datorn.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: List
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LogName

Anger namnet på en händelse logg. För att hitta de logg namn som ska användas `Get-EventLog -List` . Jokertecken är tillåtna. Den här parametern är obligatorisk.

```yaml
Type: System.String
Parameter Sets: LogName
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### – Meddelande

Anger en sträng i händelse meddelandet. Du kan använda den här parametern för att söka efter meddelanden som innehåller vissa ord eller fraser. Jokertecken är tillåtna.

```yaml
Type: System.String
Parameter Sets: LogName
Aliases: MSG

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### – Nyaste

Börjar med de senaste händelserna och hämtar det angivna antalet händelser. Antalet händelser krävs, till exempel `-Newest 100` . Anger det maximala antalet händelser som returneras.

```yaml
Type: System.Int32
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source

Anger, som en sträng mat ris, källor som skrevs till loggen som denna cmdlet hämtar. Jokertecken är tillåtna.

```yaml
Type: System.String[]
Parameter Sets: LogName
Aliases: ABO

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -UserName

Anger, som en sträng mat ris, användar namn som är associerade med händelser. Ange namn eller namn mönster, till exempel `User01` , `User*` eller `Domain01\User*` . Jokertecken är tillåtna.

```yaml
Type: System.String[]
Parameter Sets: LogName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Du kan inte skicka pipe-ininformation till `Get-EventLog` .

## UTDATA

### System. Diagnostics. EventLogEntry. System. Diagnostics. EventLog. System. String

Om parametern **LogName** anges är utdata en samling **system. Diagnostics. EventLogEntry** -objekt.

Om endast **list** parametern anges är utdata en samling **system. Diagnostics. EventLog** -objekt.

Om både **listan** och dess **sträng** parametrar anges, är utdata en samling **system. String** -objekt.

## ANTECKNINGAR

Cmdlets `Get-EventLog` och `Get-WinEvent` stöds inte i Windows Preinstallation Environment (Windows PE).

## RELATERADE LÄNKAR

[Rensa-EventLog](Clear-EventLog.md)

[Get-WinEvent](../Microsoft.PowerShell.Diagnostics/Get-WinEvent.md)

[Gruppera objekt](../Microsoft.PowerShell.Utility/Group-Object.md)

[Begränsning-EventLog](Limit-EventLog.md)

[Ny-EventLog](New-EventLog.md)

[Ta bort-EventLog](Remove-EventLog.md)

[Select-Object](../Microsoft.PowerShell.Utility/Select-Object.md)

[Visa-EventLog](Show-EventLog.md)

[Skriv-EventLog](Write-EventLog.md)
