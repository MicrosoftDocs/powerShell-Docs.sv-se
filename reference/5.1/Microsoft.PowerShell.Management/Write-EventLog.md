---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/write-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-EventLog
ms.openlocfilehash: 051f02b00144805569d5130686a51a0f42b64b00
ms.sourcegitcommit: f5986121386c81acddcf324eb0526d7d092bcc8f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/20/2021
ms.locfileid: "98584638"
---
# Write-EventLog

## SAMMANFATTNING
Skriver en händelse i en händelse logg.

## SYNTAX

```
Write-EventLog [-LogName] <String> [-Source] <String> [[-EntryType] <EventLogEntryType>] [-Category <Int16>]
 [-EventId] <Int32> [-Message] <String> [-RawData <Byte[]>] [-ComputerName <String>] [<CommonParameters>]
```

## BESKRIVNING

`Write-EventLog`Cmdleten skriver en händelse till en händelse logg.

Om du vill skriva en händelse i en händelse logg måste händelse loggen finnas på datorn och källan måste vara registrerad för händelse loggen.

De cmdletar som innehåller **EventLog** -händelsen Substantiv ( **EventLog** -cmdletar) fungerar bara på klassiska händelse loggar. Använd cmdleten för att hämta händelser från loggar som använder Windows händelse logg teknik i Windows Vista och senare versioner av Windows-operativsystemet `Get-WinEvent` .

## EXEMPEL

### Exempel 1: skriva en händelse i program händelse loggen

```
PS C:\> Write-EventLog -LogName "Application" -Source "MyApp" -EventID 3001 -EntryType Information -Message "MyApp added a user-requested feature to the display." -Category 1 -RawData 10,20
```

Det här kommandot skriver en händelse från Mittprog-källan till program händelse loggen.

### Exempel 2: skriva en händelse i program händelse loggen på en fjärrdator

```
PS C:\> Write-EventLog -ComputerName "Server01" -LogName Application -Source "MyApp" -EventID 3001 -Message "MyApp added a user-requested feature to the display."
```

Det här kommandot skriver en händelse från en Mittprog-källa till program händelse loggen på Server01-fjärrdatorn.

## PARAMETRAR

### – Kategori

Anger en aktivitets kategori för händelsen. Ange ett heltal som är associerat med strängarna i kategori meddelande filen för händelse loggen.

```yaml
Type: System.Int16
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Anger en fjärrdator. Standard är den lokala datorn.

Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn för en fjärrdator.

Den här parametern är inte beroende av Windows PowerShell-fjärrkommunikation. Du kan använda parametern **computername** för `Get-EventLog` cmdleten även om datorn inte är konfigurerad för att köra fjärrkommandon.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CN

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – EntryType

Anger händelsens post typ. De acceptabla värdena för den här parametern är: error, Warning, information, SuccessAudit och FailureAudit. Standardvärdet är information.

En beskrivning av värdena finns i EventLogEntryType- [uppräkning](/dotnet/api/system.diagnostics.eventlogentrytype).

```yaml
Type: System.Diagnostics.EventLogEntryType
Parameter Sets: (All)
Aliases: ET
Accepted values: Error, Information, FailureAudit, SuccessAudit, Warning

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – EventId

Anger händelse-ID. Den här parametern är obligatorisk. Det maximala värdet för parametern **EventId** är 65535.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: ID, EID

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LogName

Anger namnet på den logg som händelsen skrivs till. Ange namnet på loggen. Logg namnet är värdet för **logg** egenskapen, inte **LogDisplayName**. Jokertecken tillåts inte.
Den här parametern är obligatorisk.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Meddelande

Anger händelse meddelandet. Den här parametern är obligatorisk.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: MSG

Required: True
Position: 4
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RawData

Anger de binära data som är associerade med händelsen, i byte.

```yaml
Type: System.Byte[]
Parameter Sets: (All)
Aliases: RD

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source

Anger händelse källan, som vanligt vis är namnet på det program som skriver händelsen till loggen.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: SRC

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### System. Diagnostics. EventLogEntry

Denna cmdlet returnerar objekt som representerar händelserna i loggarna.

## ANTECKNINGAR

För vissa Windows-händelseloggar kräver Skriv händelser administratörs behörighet. Du måste starta PowerShell med alternativet **Kör som administratör** .

## RELATERADE LÄNKAR

[Rensa-EventLog](Clear-EventLog.md)

[Get-EventLog](Get-EventLog.md)

[Begränsning-EventLog](Limit-EventLog.md)

[Ny-EventLog](New-EventLog.md)

[Ta bort-EventLog](Remove-EventLog.md)

[Visa-EventLog](Show-EventLog.md)

[Skriv-EventLog](Write-EventLog.md)
