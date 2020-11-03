---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 01/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/new-eventlog?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-EventLog
ms.openlocfilehash: 61fafc0670a24fd6ca057e4cf0c7179d90446b07
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265532"
---
# New-EventLog

## SAMMANFATTNING
Skapar en ny händelse logg och en ny händelse källa på en lokal eller fjärran sluten dator.

## SYNTAX

```
New-EventLog [-LogName] <string> [-Source] <string[]> [[-ComputerName] <string[]>]
  [-CategoryResourceFile <string>] [-MessageResourceFile <string>] [-ParameterResourceFile <string>]
  [<CommonParameters>]
```

## BESKRIVNING

Denna cmdlet skapar en ny klassisk händelse logg på en lokal eller fjärran sluten dator. Det kan också registrera en händelse källa som skriver till den nya loggen eller till en befintlig logg.

De cmdletar som innehåller EventLog-händelsen Substantiv (händelse logg-cmdletar) fungerar bara på klassiska händelse loggar.
Använd för att hämta händelser från loggar som använder Windows händelse logg teknik i Windows Vista och senare versioner av Windows `Get-WinEvent` .

## EXEMPEL

### Exempel 1 – Skapa en ny händelse logg

Med det här kommandot skapas händelse loggen TestLog på den lokala datorn och en ny källa registreras.

```powershell
New-EventLog -source TestApp -LogName TestLog -MessageResourceFile C:\Test\TestApp.dll
```

### Exempel 2 – lägga till en ny händelse källa i en befintlig logg

Detta kommando lägger till en ny händelse källa, NewTestApp, i program loggen på Server01-fjärrdatorn.

```powershell
$file = "C:\Program Files\TestApps\NewTestApp.dll"
New-EventLog -ComputerName Server01 -Source NewTestApp -LogName Application -MessageResourceFile $file -CategoryResourceFile $file
```

Kommandot kräver att NewTestApp.dll-filen finns på den Server01 datorn.

## PARAMETRAR

### -CategoryResourceFile

Anger sökvägen till filen som innehåller kategori strängar för käll händelser. Den här filen kallas även för kategori meddelande filen.

Filen måste finnas på den dator där händelse loggen skapas. Den här parametern skapar eller flyttar inte filer.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: CRF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ComputerName

Skapar de nya händelse loggarna på de angivna datorerna. Standard är den lokala datorn.

NetBIOS-namn, IP-adress eller fullständigt kvalificerat domän namn för en fjärrdator.
Om du vill ange den lokala datorn skriver du datorns namn, en punkt (.) eller "localhost".

Den här parametern är inte beroende av PowerShell-fjärrkommunikation. Du kan använda parametern **computername** för `Get-EventLog` även om datorn inte är konfigurerad för att köra fjärrkommandon.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: CN

Required: False
Position: 3
Default value: Local computer
Accept pipeline input: False
Accept wildcard characters: False
```

### -LogName

Anger namnet på händelse loggen.

Om loggen inte finns `New-EventLog` skapar loggen och använder det här värdet för **logg** -och **LogDisplayName** -egenskaperna för den nya händelse loggen. Om det finns en logg `New-EventLog` registreras en ny källa för händelse loggen.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: LN

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -MessageResourceFile

Anger sökvägen till filen som innehåller strängar för meddelande formatering för käll händelser.
Den här filen kallas även för händelse meddelande filen.

Filen måste finnas på den dator där händelse loggen skapas.
Den här parametern skapar eller flyttar inte filer.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: MRF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ParameterResourceFile

Anger sökvägen till filen som innehåller strängar som används för parameter ersättningar i händelse beskrivningar. Den här filen kallas även för parameter meddelande filen.

Filen måste finnas på den dator där händelse loggen skapas.
Den här parametern skapar eller flyttar inte filer.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PRF

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Source

Anger namnen på händelse logg källorna, till exempel program program som skriver till händelse loggen. Den här parametern är obligatorisk.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: SRC

Required: True
Position: 2
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

## ANTECKNINGAR

Om du vill använda `New-EventLog` i Windows Vista och senare versioner av Windows öppnar du PowerShell med alternativet "kör som administratör".

Om du vill skapa en händelse källa i Windows Vista, Windows XP Professional eller Windows Server 2003 måste du vara medlem i gruppen Administratörer på datorn.

När du skapar en ny händelse logg och en ny händelse källa registrerar systemet den nya källan för den nya loggen, men loggen skapas inte förrän den första posten skrivs till den.

Operativ systemet lagrar händelse loggar som filer.

När du skapar en ny händelse logg lagras den tillhör ande filen i `$env:SystemRoot\System32\Config` katalogen på den angivna datorn.

Fil namnet är de första åtta tecknen i **logg** egenskapen med fil namns tillägget. evt.

## RELATERADE LÄNKAR

[Rensa-EventLog](Clear-EventLog.md)

[Get-EventLog](Get-EventLog.md)

[Get-WinEvent](../Microsoft.PowerShell.Diagnostics/Get-WinEvent.md)

[Begränsning-EventLog](Limit-EventLog.md)

[Ny-EventLog](New-EventLog.md)

[Ta bort-EventLog](Remove-EventLog.md)

[Visa-EventLog](Show-EventLog.md)

[Skriv-EventLog](Write-EventLog.md)
