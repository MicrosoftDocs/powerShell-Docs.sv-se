---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-EventLog
ms.openlocfilehash: af1c808b22a812700857e756136fd570fa0acc35
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685908"
---
# Clear-EventLog

## SAMMANFATTNING
Tar bort alla poster från angivna händelse loggar på lokala eller fjärranslutna datorer.

## SYNTAX

```
Clear-EventLog [-LogName] <String[]> [[-ComputerName] <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Clear-EventLog`Cmdleten tar bort alla poster från de angivna händelse loggarna på den lokala datorn eller på fjärrdatorer. För att kunna använda `Clear-EventLog` måste du vara medlem i gruppen Administratörer på den berörda datorn.

De cmdletar som innehåller **EventLog** -händelsen Substantiv (EventLog-cmdletar) fungerar bara på klassiska händelse loggar. Om du vill hämta händelser från loggar som använder Windows händelse logg teknik i Windows Vista och senare versioner av Windows, använder du Get-WinEvent-cmdleten.

## EXEMPEL

### Exempel 1: rensa vissa händelse logg typer från den lokala datorn

```powershell
Clear-EventLog "Windows PowerShell"
```

Det här kommandot rensar posterna från Windows PowerShell-händelseloggen på den lokala datorn.

### Exempel 2: ta bort vissa olika logg typer från lokala datorer och fjärrdatorer

```powershell
Clear-EventLog -LogName ODiag, OSession -ComputerName localhost, Server02
```

Med det här kommandot rensas alla poster i ODiag-(Microsoft Office Diagnostics) och Microsoft Office-sessioner (OSession) på den lokala datorn och på Server02-fjärrdatorn.

### Exempel 3: Rensa alla loggar på de angivna datorerna och Visa sedan händelse logg listan

```powershell
Clear-EventLog -LogName application, system -confirm
```

Med det här kommandot uppmanas du att bekräfta innan du tar bort posterna i de angivna händelse loggarna.

### Exempel 4: Rensa alla loggar på de angivna datorerna och Visa sedan händelse logg listan

```powershell
function clear-all-event-logs ($computerName="localhost")
{
   $logs = Get-EventLog -ComputerName $computername -List | ForEach-Object {$_.Log}
   $logs | ForEach-Object {Clear-EventLog -ComputerName $computername -LogName $_ }
   Get-EventLog -ComputerName $computername -list
}

clear-all-event-logs -ComputerName Server01
```

```Output
Max(K) Retain OverflowAction        Entries Log
------ ------ --------------        ------- ---
15,168      0 OverwriteAsNeeded           0 Application
15,168      0 OverwriteAsNeeded           0 DFS Replication
512         7 OverwriteOlder              0 DxStudio
20,480      0 OverwriteAsNeeded           0 Hardware Events
512         7 OverwriteOlder              0 Internet Explorer
20,480      0 OverwriteAsNeeded           0 Key Management Service
16,384      0 OverwriteAsNeeded           0 Microsoft Office Diagnostics
16,384      0 OverwriteAsNeeded           0 Microsoft Office Sessions
30,016      0 OverwriteAsNeeded           1 Security
15,168      0 OverwriteAsNeeded           2 System
15,360      0 OverwriteAsNeeded           0 Windows PowerShell
```

Den här funktionen rensar alla händelse loggar på de angivna datorerna och visar sedan den resulterande händelse logg listan.

Observera att några poster har lagts till i systemet och säkerhets loggar när loggarna rensades, men innan de visades.

## PARAMETRAR

### -ComputerName

Anger en fjärrdator. Standard är den lokala datorn.

Ange NetBIOS-namnet, en Internet Protocol IP-adress eller ett fullständigt kvalificerat domän namn för en fjärrdator. Om du vill ange den lokala datorn skriver du datorns namn, en punkt (.) eller "localhost".

Den här parametern är inte beroende av Windows PowerShell-fjärrkommunikation. Du kan använda parametern **computername** för `Get-EventLog` även om datorn inte är konfigurerad för att köra fjärrkommandon.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: 1
Default value: Local computer
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -LogName

Anger händelse loggarna. Ange logg namnet (värdet för **logg** egenskapen inte **LogDisplayName**) för en eller flera händelse loggar, avgränsade med kommatecken. Jokertecken tillåts inte. Den här parametern är obligatorisk.

> [!IMPORTANT]
> Den här parametern ska acceptera värden från pipelinen efter egenskaps namn. Det finns dock ett fel som förhindrar att detta fungerar. Du måste skicka ett värde med hjälp av parametern direkt.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
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

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### Inget

Det går inte att skicka pipe-objekt till `Clear-EventLog` .

## UTDATA

### Inget

Denna cmdlet genererar inga utdata.

## ANTECKNINGAR

- Om du vill använda `Clear-EventLog` i Windows Vista och senare versioner av Windows startar du Windows PowerShell med alternativet "kör som administratör".

## RELATERADE LÄNKAR

[Get-EventLog](Get-EventLog.md)

[Begränsning-EventLog](Limit-EventLog.md)

[Ny-EventLog](New-EventLog.md)

[Ta bort-EventLog](Remove-EventLog.md)

[Visa-EventLog](Show-EventLog.md)

[Skriv-EventLog](Write-EventLog.md)
