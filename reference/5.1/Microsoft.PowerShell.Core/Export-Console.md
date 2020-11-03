---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/export-console?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Console
ms.openlocfilehash: 7b643b5f9b6868a5da988b19b65dead24f986f67
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263636"
---
# Export-Console

## SAMMANFATTNING
Exporterar namn på snapin-moduler i den aktuella sessionen till en konsol fil.

## SYNTAX

```
Export-Console [[-Path] <String>] [-Force] [-NoClobber] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING
Cmdleten **export-Console** exporterar namnen på Windows PowerShell-snapin-modulerna i den aktuella sessionen till en Windows PowerShell-konsol fil (. psc1).
Du kan använda denna cmdlet för att spara snapin-modulerna som ska användas i framtida sessioner.

Om du vill lägga till snapin-modulerna i. psc1-konsol filen i en session startar du Windows PowerShell (Powershell.exe) på kommando raden genom att använda Cmd.exe eller en annan Windows PowerShell-session och använder sedan *PSConsoleFile* -parametern för Powershell.exe för att ange konsol filen.

Mer information om snapin-moduler för Windows PowerShell finns i about_PSSnapins.

## EXEMPEL

### Exempel 1: exportera namnen på snapin-modulerna i den aktuella sessionen

```
PS C:\> Export-Console -Path $pshome\Consoles\ConsoleS1.psc1
```

Detta kommando exporterar namnen på Windows PowerShell-snapin-modulerna i den aktuella sessionen till filen ConsoleS1. psc1 i mappen konsoler i installationsmappen för Windows PowerShell $pshome.

### Exempel 2: exportera namn på snapin-moduler till den senaste konsol filen

```
PS C:\> Export-Console
```

Detta kommando exporterar namnen på Windows PowerShell-snapin-moduler från den aktuella sessionen till Windows PowerShell-konsolen som senast användes i den aktuella sessionen.
Det skriver över det tidigare fil innehållet.

Om du inte har exporterat en konsol fil under den aktuella sessionen uppmanas du att ange behörighet för att fortsätta och sedan ange ett fil namn.

### Exempel 3: Lägg till en snapin-modul och exportera namnen på snapin-modulerna

```
PS C:\> Add-PSSnapin NewPSSnapin
PS C:\> Export-Console -path NewPSSnapinConsole.psc1
PS C:\> powershell.exe -PsConsoleFile NewPsSnapinConsole.psc1
```

Dessa kommandon lägger till Windows PowerShell-snapin-modulen NewPSSnapin i den aktuella sessionen, exporterar namnen på Windows PowerShell-snapin-modulerna i den aktuella sessionen till en konsol fil och startar sedan en Windows PowerShell-session med konsol filen.

Det första kommandot använder cmdleten **Add-PSSnapin** för att lägga till snapin-modulen NewPSSnapin i den aktuella sessionen.
Du kan bara lägga till Windows PowerShell-snapin-moduler som är registrerade i systemet.

Det andra kommandot exporterar Windows PowerShell-snapin-modulernas namn till filen NewPSSnapinConsole. psc1.

Det tredje kommandot startar Windows PowerShell med filen NewPSSnapinConsole. psc1.
Eftersom konsol filen innehåller namnet på Windows PowerShell-snapin-modulen är cmdletarna och providers i snapin-modulen tillgängliga i den aktuella sessionen.

### Exempel 4: exportera namn på snapin-moduler till en angiven plats

```
PS C:\> export-console -path Console01
PS C:\> notepad console01.psc1
<?xml version="1.0" encoding="utf-8"?>
<PSConsoleFile ConsoleSchemaVersion="1.0">
  <PSVersion>2.0</PSVersion>
  <PSSnapIns>
     <PSSnapIn Name="NewPSSnapin" />
  </PSSnapIns>
</PSConsoleFile>
```

Detta kommando exporterar namnen på Windows PowerShell-snapin-modulerna i den aktuella sessionen till filen Console01. psc1 i den aktuella katalogen.

Det andra kommandot visar innehållet i filen Console01. psc1 i anteckningar.

### Exempel 5: Bestäm konsol filen som ska uppdateras

```
PS C:\> powershell.exe -PSConsoleFile Console01.psc1
PS C:\> Add-PSSnapin MySnapin
PS C:\> Export-Console NewConsole.psc1
PS C:\> $ConsoleFileName
PS C:\> Add-PSSnapin SnapIn03
PS C:\> Export-Console
```

I det här exemplet visas hur du använder den automatiska variabeln $ConsoleFileName för att fastställa konsol filen som ska uppdateras om du använder **export-konsolen** utan parametern *Path* -värde.

Det första kommandot använder *PSConsoleFile* -parametern för PowerShell.exe för att öppna Windows PowerShell med filen Console01. psc1.

Det andra kommandot använder cmdleten **Add-PSSnapin** för att lägga till snapin-modulen för snap-in-Windows PowerShell i den aktuella sessionen.

Det tredje kommandot använder cmdleten **export-Console** för att exportera namnen på alla Windows PowerShell-snapin-moduler i sessionen till filen NewConsole. psc1.

Det fjärde kommandot visar $ConsoleFileName variabeln.
Den innehåller den senast använda konsol filen.
Exemplet på utdata visar att NewConsole.ps1 är den senast använda filen.

Det femte kommandot lägger till SnapIn03 i den aktuella konsolen.

Det sjätte kommandot använder cmdleten **export-Console** utan en *Sök vägs* parameter.
Detta kommando exporterar namnen på alla Windows PowerShell-snapin-moduler i den aktuella sessionen till den senast använda filen, NewConsole. psc1.

## PARAMETRAR

### -Force
Anger att denna cmdlet skriver över data i en konsol fil utan varning, även om filen har attributet skrivskyddad.
Det skrivskyddade attributet har ändrats och återställs inte när kommandot har slutförts.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoClobber
Anger att denna cmdlet inte skriver över en befintlig konsol fil.
Som standard skriver **export konsolen** över filen utan varning om en fil förekommer i den angivna sökvägen.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path
Anger en sökväg och ett fil namn för konsol filen (*. psc1).
Ange en valfri sökväg och ett namn.
Jokertecken tillåts inte.

Om du bara anger ett fil namn skapar **export konsolen** en fil med det namnet och fil namns tillägget. psc1 i den aktuella katalogen.

Den här parametern krävs om du inte har öppnat Windows PowerShell med parametern *PSConsoleFile* eller exporterat en konsol fil under den aktuella sessionen.
Det krävs också när du använder parametern *NoClobber* för att förhindra att den aktuella konsol filen skrivs över.

Om du utelämnar den här parametern skriver **export konsolen** över konsol filen som användes senast under den här sessionen.
Sökvägen till den senast använda konsol filen lagras i värdet för den $ConsoleFileName automatiska variabeln.
Mer information finns i about_Automatic_Variables.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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

### System. String
Du kan skicka en Sök vägs sträng till denna cmdlet.

## UTDATA

### System. IO. FileInfo
Denna cmdlet skapar en fil som innehåller de exporterade aliasen.

## ANTECKNINGAR

* När en konsol fil (. psc1) används för att starta sessionen lagras namnet på konsol filen automatiskt i $ConsoleFileName automatiska variabeln. Värdet för $ConsoleFileName uppdateras när du använder parametern *Path* i **export-konsolen** för att ange en ny konsol fil. Om ingen konsol fil används har $ConsoleFileName inget värde ($Null).

  Använd följande syntax för att starta Windows PowerShell för att använda en Windows PowerShell-konsolfil i en ny session:

  `powershell.exe -PsConsoleFile \<ConsoleFile\>.psc1`

  Du kan också spara Windows PowerShell-snapin-moduler för framtida sessioner genom att lägga till ett Add-PSSnapin-kommando i Windows PowerShell-profilen.
Mer information finns i about_Profiles.


## RELATERADE LÄNKAR

[Add-PSSnapin](Add-PSSnapin.md)

[Get-PSSnapin](Get-PSSnapin.md)

[Remove-PSSnapin](Remove-PSSnapin.md)
