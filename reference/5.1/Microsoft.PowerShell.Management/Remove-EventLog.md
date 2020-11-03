---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-EventLog
ms.openlocfilehash: 4cf29146727c9a54715459a2d56e47a27c5bacc0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265484"
---
# Remove-EventLog

## SAMMANFATTNING
Tar bort en händelse logg eller avregistrerar en händelse källa.

## SYNTAX

### Standard (standard)

```
Remove-EventLog [[-ComputerName] <String[]>] [-LogName] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Källa

```
Remove-EventLog [[-ComputerName] <String[]>] [-Source <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING
Cmdleten **Remove-EventLog** tar bort en händelse logg fil från en lokal dator eller fjärrdator och avregistrerar alla händelse källor för loggen.
Du kan också använda denna cmdlet för att avregistrera händelse källor utan att ta bort några händelse loggar.

Cmdlet: arna som innehåller **EventLog** substantiv, **EventLog** -cmdletar fungerar bara på klassiska händelse loggar.
Använd Get-WinEvent för att hämta händelser från loggar som använder Windows händelse logg teknik i Windows Vista och senare versioner av operativ systemet Windows.

Varning! den här cmdleten kan ta bort händelse loggar för operativ systemet, vilket kan orsaka program fel och oväntade system beteenden.

## EXEMPEL

### Exempel 1: ta bort en händelse logg från den lokala datorn

```
PS C:\> Remove-EventLog -LogName "MyLog"
```

Det här kommandot tar bort händelse loggen MyLog från den lokala datorn och avregistrerar dess händelse källor.

### Exempel 2: ta bort en händelse logg från flera datorer

```
PS C:\> Remove-EventLog -LogName "MyLog", "TestLog" -ComputerName "Server01", "Server02", "localhost"
```

Det här kommandot tar bort händelse loggarna MyLog och TestLog från den lokala datorn och Server01-och Server02-fjärrdatorerna.
Kommandot avregistrerar också händelse källorna för dessa loggar.

### Exempel 3: ta bort en händelse källa

```
PS C:\> Remove-EventLog -Source "MyApp"
```

Det här kommandot tar bort händelse källan för MyApp från loggarna på den lokala datorn.
När kommandot har slutförts kan inte programmet Mittprog skriva till några händelse loggar.

### Exempel 4: ta bort en händelse logg och bekräfta åtgärden

```
The first command lists the event logs on the local computer.
PS C:\> Get-EventLog -List
Max(K) Retain OverflowAction        Entries Log
------ ------ --------------        ------- ---
15,168      0 OverwriteAsNeeded      22,923 Application
15,168      0 OverwriteAsNeeded          53 DFS Replication
15,168      7 OverwriteOlder              0 Hardware Events
512      7 OverwriteOlder              0 Internet Explorer
20,480      0 OverwriteAsNeeded           0 Key Management Service
30,016      0 OverwriteAsNeeded      50,060 Security
15,168      0 OverwriteAsNeeded      27,592 System
15,360      0 OverwriteAsNeeded      18,355 Windows PowerShell
15,168      7 OverwriteAsNeeded          12 ZapLog

The second command deletes the ZapLog event log.
PS C:\> Remove-EventLog -LogName "ZapLog"

The third command lists the event logs again. The ZapLog event log no longer appears in the list.
PS C:\> Get-EventLog -List
Max(K) Retain OverflowAction        Entries Log
------ ------ --------------        ------- ---
15,168      0 OverwriteAsNeeded      22,923 Application
15,168      0 OverwriteAsNeeded          53 DFS Replication
15,168      7 OverwriteOlder              0 Hardware Events
512      7 OverwriteOlder              0 Internet Explorer
20,480      0 OverwriteAsNeeded           0 Key Management Service
30,016      0 OverwriteAsNeeded      50,060 Security
15,168      0 OverwriteAsNeeded      27,592 System
15,360      0 OverwriteAsNeeded      18,355 Windows PowerShell
```

De här kommandona visar hur du listar händelse loggarna på en dator och kontrollerar att kommandot **Remove-EventLog** har slutförts.

### Exempel 5: ta bort en händelse källa och bekräfta åtgärden

```
PS C:\> Get-WmiObject win32_nteventlogfile -Filter "logfilename='TestLog'" | foreach {$_.sources}
MyApp
TestApp
PS C:\> Remove-Eventlog -Source "MyApp"
PS C:\> Get-WmiObject win32_nteventlogfile -Filter "logfilename='TestLog'"} | foreach {$_.sources}
TestApp
```

Dessa kommandon använder Get-WmiObject-cmdleten för att visa händelse källorna på den lokala datorn.
Du kan kontrol lera att ett kommando är klart eller ta bort en händelse källa.

Det första kommandot hämtar händelse källorna för händelse loggen TestLog på den lokala datorn.
MyApp är en av källorna.

Det andra kommandot använder *käll* parametern för **Remove-EventLog** för att ta bort händelse källan för MyApp.

Det tredje kommandot är identiskt med det första.
Det visar att händelse källan för MyApp har tagits bort.

## PARAMETRAR

### -ComputerName
Anger en fjärrdator.
Standard är den lokala datorn.

Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn för en fjärrdator.
Om du vill ange den lokala datorn skriver du datorns namn, en punkt (.) eller localhost.

Den här parametern är inte beroende av Windows PowerShell-fjärrkommunikation.
Du kan använda parametern *computername* för **Remove-EventLog** även om datorn inte har kon figurer ATS för att köra fjärrkommandon.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LogName
Anger händelse loggarna.
Ange logg namnet för en eller flera händelse loggar, avgränsade med kommatecken.
Logg namnet är värdet för egenskapen **log** , inte *LogDisplayName* , jokertecken tillåts inte.
Den här parametern är obligatorisk.

```yaml
Type: System.String[]
Parameter Sets: Default
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source
Anger händelse källorna som denna cmdlet avregistrerar.
Ange käll namnen, inte namnet på den körbara filen, avgränsade med kommatecken.

```yaml
Type: System.String[]
Parameter Sets: Source
Aliases: SRC

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Confirm
Uppmanar dig att bekräfta innan du kör cmdleten.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf
Visar vad som skulle hända om cmdleten kördes.
Cmdleten körs inte.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters
Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget
Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### Inget
Denna cmdlet returnerar inga utdata.

## ANTECKNINGAR

* Om du vill använda **Remove-EventLog** på Windows Vista och senare versioner av operativ systemet Windows startar du Windows PowerShell med alternativet Kör som administratör.

  Om du tar bort en händelse logg och sedan skapar loggen igen kommer du inte att kunna registrera samma händelse källor.
Program som använde händelse källorna för att skriva poster till den ursprungliga loggen kommer inte att kunna skriva till den nya loggen.

* När du avregistrerar en händelse källa för en viss logg kan händelse källan förhindras från att skriva poster i andra händelse loggar.

## RELATERADE LÄNKAR

[Rensa-EventLog](Clear-EventLog.md)

[Get-EventLog](Get-EventLog.md)

[Begränsning-EventLog](Limit-EventLog.md)

[Ny-EventLog](New-EventLog.md)

[Ta bort-EventLog](Remove-EventLog.md)

[Visa-EventLog](Show-EventLog.md)

[Skriv-EventLog](Write-EventLog.md)
