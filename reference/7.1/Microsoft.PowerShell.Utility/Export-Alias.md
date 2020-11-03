---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-alias?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Alias
ms.openlocfilehash: 1ea81eb6875fa01d12899dffb4f99cbf910c14c9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266438"
---
# Export-Alias

## SAMMANFATTNING
Exporterar information om aktuella definierade alias till en fil.

## SYNTAX

### ByPath (standard)

```
Export-Alias [-Path] <String> [[-Name] <String[]>] [-PassThru] [-As <ExportAliasFormat>] [-Append] [-Force]
 [-NoClobber] [-Description <String>] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Export-Alias -LiteralPath <String> [[-Name] <String[]>] [-PassThru] [-As <ExportAliasFormat>] [-Append]
 [-Force] [-NoClobber] [-Description <String>] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Export-Alias`Cmdleten exporterar aliasen i den aktuella sessionen till en fil.
Om utdatafilen inte finns skapas den av cmdleten.

`Export-Alias` kan exportera alias i ett visst omfång eller med alla omfattningar, det kan generera data i CSV-format eller som en serie med Set-Alias-kommandon som du kan lägga till i en session eller till en PowerShell-profil.

## EXEMPEL

### Exempel 1: exportera ett alias

```powershell
Export-Alias -Path "alias.csv"
```

Det här kommandot exporterar aktuell aliasresurspost till en fil med namnet Alias.csv i den aktuella katalogen.

### Exempel 2: exportera ett alias om inte export filen redan finns

```powershell
Export-Alias -Path "alias.csv" -NoClobber
```

Detta kommando exporterar alias i den aktuella sessionen till en Alias.csv-fil.

Eftersom parametern **NoClobber** anges kommer kommandot att Miss förväntas om det redan finns en Alias.csv fil i den aktuella katalogen.

### Exempel 3: Lägg till alias i en fil

```powershell
Export-Alias -Path "alias.csv" -Append -Description "Appended Aliases" -Force
```

Detta kommando lägger till alias i den aktuella sessionen till Alias.csv-filen.

Kommandot använder parametern **Description** för att lägga till en beskrivning till kommentarerna överst i filen.

Kommandot använder också parametern **Force** för att skriva över eventuella befintliga Alias.csv-filer, även om de har attributet skrivskyddad.

### Exempel 4: exportera alias som ett skript

```powershell
Export-Alias -Path "alias.ps1" -As Script
Add-Content -Path $Profile -Value (Get-Content alias.ps1)
$S = New-PSSession -ComputerName Server01
Invoke-Command -Session $S -FilePath .\alias.ps1
```

Det här exemplet visar hur du använder skript fil formatet som `Export-Alias` genereras.

Det första kommandot exporterar aliasen i sessionen till Alias.ps1-filen.
Den använder parametern **as** med ett värde för skript för att skapa en fil som innehåller ett Set-Alias-kommando för varje alias.

Det andra kommandot lägger till alias i Alias.ps1-filen till CurrentUser-CurrentHost profilen.
Sökvägen till profilen sparas i `$Profile` variabeln.
Kommandot använder `Get-Content` cmdleten för att hämta alias från Alias.ps1-filen och `Add-Content` cmdlet: en för att lägga till dem i profilen.
Mer information finns i about_Profiles.

De tredje och fjärde kommandona lägger till alias i Alias.ps1-filen till en fjärrsession på Server01-datorn.
Det tredje kommandot använder `New-PSSession` cmdleten för att skapa sessionen.
Det fjärde kommandot använder parametern **sökväg** för `Invoke-Command` cmdleten för att köra Alias.ps1-filen i den nya sessionen.

## PARAMETRAR

### -Lägg till

Anger att denna cmdlet lägger till utdata i den angivna filen i stället för att skriva över det befintliga innehållet i filen.

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

### – Som

Anger utdataformatet.
CSV är standardvärdet.
De acceptabla värdena för den här parametern är:

- SKV.
Format med kommaavgränsade värden (CSV).
- Över.
Skapar ett `Set-Alias` kommando för varje exporterat alias.
Om du namnger utdatafilen med fil namns tillägget. ps1 kan du köra det som ett skript för att lägga till alias till en session.

```yaml
Type: Microsoft.PowerShell.Commands.ExportAliasFormat
Parameter Sets: (All)
Aliases:
Accepted values: Csv, Script

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Beskrivning

Anger beskrivningen av den exporterade filen.
Beskrivningen visas som en kommentar överst i filen, efter rubrik informationen.

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

### -Force

Tvingar kommandot att köras utan att fråga användaren om bekräftelse.

Skriver över utdatafilen, även om det skrivskyddade attributet är inställt på filen.

Som standard `Export-Alias` skriver överskrivna filer utan varning, om inte attributet skrivskyddad eller dold har angetts eller parametern **NoClobber** används i kommandot.
**NoClobber** -parametern har företräde framför parametern **Force** när båda används i ett kommando.

**Force** -parametern kan inte tvinga `Export-Alias` att skriva över filer med det dolda attributet.

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

### -LiteralPath

Anger sökvägen till utdatafilen.
Till skillnad från **sökväg** används värdet för parametern **LiteralPath** exakt som det har angetts.
Inga tecken tolkas som jokertecken.
Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.
Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Anger namnen som en matris med de alias som ska exporteras.
Jokertecken är tillåtna.

Som standard `Export-Alias` exporteras alla alias i sessionen eller omfattningen.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -NoClobber

Anger att denna cmdlet förhindrar att `Export-Alias` filer skrivs över, även om **Force** -parametern används i kommandot.

Om parametern **NoClobber** utelämnas skrivs `Export-Alias` en befintlig fil över utan varning, om inte attributet skrivskyddad anges för filen.
*NoClobber* prioriteras över **Force** -parametern som tillåter `Export-Alias` att en fil skrivs över med attributet skrivskyddad.

*NoClobber* förhindrar inte att parametern **Lägg** till innehåll läggs till i en befintlig fil.

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

### – PassThru

Returnerar ett objekt som representerar det objekt som du arbetar med.
Som standard genererar denna cmdlet inga utdata.

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

### -Path

Anger sökvägen till utdatafilen.
Jokertecken tillåts, men värdet för den resulterande sökvägen måste matcha ett enda fil namn.

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### – Omfattning

Anger omfånget som aliasen ska exporteras från.
De acceptabla värdena för den här parametern är:

- Global
- Lokal
- Skript
- Ett tal i förhållande till det aktuella omfånget (0 till antalet omfattningar där 0 är det aktuella omfånget och 1 är överordnat)

Standardvärdet är Local.
Mer information finns i about_Scopes.

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

### Inga.

Det går inte att skicka pipe-objekt till denna cmdlet.

## UTDATA

### Ingen eller system. Management. Automation. AliasInfo

När du använder parametern **Passthru** `Export-Alias` returneras ett objekt av **system. Management. Automation. AliasInfo** som representerar aliaset.
Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

* Du kan bara Export-Aliases till en fil.

## RELATERADE LÄNKAR

[Get-alias](Get-Alias.md)

[Importera-alias](Import-Alias.md)

[Nytt-alias](New-Alias.md)

[Set-alias](Set-Alias.md)

