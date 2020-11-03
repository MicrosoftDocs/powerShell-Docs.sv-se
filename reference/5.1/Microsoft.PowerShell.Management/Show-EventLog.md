---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/show-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-EventLog
ms.openlocfilehash: e8dbcf1aa4280c0481714a8a9fb24f2e5ef79ffe
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265371"
---
# Show-EventLog

## SAMMANFATTNING
Visar händelse loggarna för den lokala datorn eller en fjärrdator i Loggboken.

## SYNTAX

```
Show-EventLog [[-ComputerName] <String>] [<CommonParameters>]
```

## BESKRIVNING
Cmdleten **show-EventLog** öppnar Loggboken på den lokala datorn och visar den alla klassiska händelse loggar på den lokala datorn eller en fjärrdator.

För att öppna Loggboken i Windows Vista och senare versioner av operativ systemet Windows måste den aktuella användaren vara medlem i gruppen Administratörer på den lokala datorn.

De cmdletar som innehåller **EventLog** -händelsen Substantiv ( **EventLog** -cmdletar) fungerar bara på klassiska händelse loggar.
Om du vill hämta händelser från loggar som använder Windows händelse logg teknik i Windows Vista och senare versioner av Windows-operativsystemet, använder du Get-WinEvent-cmdleten.

## EXEMPEL

### Exempel 1: Visa händelse loggar för den lokala datorn

```
PS C:\> Show-EventLog
```

Det här kommandot öppnar Loggboken och visar de klassiska händelse loggarna på den lokala datorn.

### Exempel 2: Visa händelse loggar för en fjärran sluten dator

```
PS C:\> Show-EventLog -ComputerName "Server01"
```

Det här kommandot öppnar Loggboken och visar den klassiska händelse loggarna på den Server01 datorn.

## PARAMETRAR

### -ComputerName
Anger en fjärrdator.
**Visa-EventLog** visar händelse loggarna från den angivna datorn i Loggboken på den lokala datorn.
Standard är den lokala datorn.

Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn för en fjärrdator.

Den här parametern är inte beroende av Windows PowerShell-fjärrkommunikation.
Du kan använda parametern *computername* även om datorn inte är konfigurerad för att köra fjärrkommandon.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CN

Required: False
Position: 0
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

### Inget
Denna cmdlet genererar inga utdata.

## ANTECKNINGAR

* Kommando tolken för Windows PowerShell returneras så snart Loggboken öppnas. Du kan arbeta i den aktuella sessionen medan Loggboken är öppen.

  Eftersom denna cmdlet kräver ett användar gränssnitt fungerar den inte på Server Core-installationer av Windows Server.

*

## RELATERADE LÄNKAR

[Rensa-EventLog](Clear-EventLog.md)

[Get-EventLog](Get-EventLog.md)

[Begränsning-EventLog](Limit-EventLog.md)

[Ny-EventLog](New-EventLog.md)

[Ta bort-EventLog](Remove-EventLog.md)

[Skriv-EventLog](Write-EventLog.md)
