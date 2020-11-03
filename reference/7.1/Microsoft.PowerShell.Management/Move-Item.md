---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/move-item?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Move-Item
ms.openlocfilehash: 1898d0b80e715c817612b54d795d0c2f57b6c6b7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263312"
---
# Move-Item

## SAMMANFATTNING
Flyttar ett objekt från en plats till en annan.

## SYNTAX

### Sökväg (standard)

```
Move-Item [-Path] <String[]> [[-Destination] <String>] [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-PassThru] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPath

```
Move-Item -LiteralPath <String[]> [[-Destination] <String>] [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-PassThru] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Move-Item`Cmdleten flyttar ett objekt, inklusive dess egenskaper, innehåll och underordnade objekt, från en plats till en annan plats. Platserna måste stödjas av samma provider.
Till exempel kan den flytta en fil eller under katalog från en katalog till en annan eller flytta en register under nyckel från en nyckel till en annan.
När du flyttar ett objekt läggs det till på den nya platsen och tas bort från den ursprungliga platsen.

## EXEMPEL

### Exempel 1: flytta en fil till en annan katalog och Byt namn på den

Det här kommandot flyttar `Test.txt` filen från `C:` enheten till `E:\Temp` katalogen och byter namn till den från `test.txt` till `tst.txt` .

```powershell
Move-Item -Path C:\test.txt -Destination E:\Temp\tst.txt
```

### Exempel 2: flytta en katalog och dess innehåll till en annan katalog

Detta kommando flyttar `C:\Temp` katalogen och dess innehåll till `C:\Logs` katalogen.
Katalogen "temp" och alla dess under kataloger och filer visas i katalogen "loggar".

```powershell
Move-Item -Path C:\Temp -Destination C:\Logs
```

### Exempel 3: flytta alla filer för ett angivet tillägg från den aktuella katalogen till en annan katalog

Detta kommando flyttar alla textfiler ( `*.txt` ) i den aktuella katalogen (som representeras av en punkt ( `.` )) till `C:\Logs` katalogen.

```powershell
Move-Item -Path .\*.txt -Destination C:\Logs
```

### Exempel 4: flytta alla filer i ett angivet tillägg rekursivt från den aktuella katalogen till en annan katalog

Det här kommandot flyttar alla textfiler från den aktuella katalogen och alla under kataloger, rekursivt, till katalogen "C:\TextFiles".

```powershell
Get-ChildItem -Path ".\*.txt" -Recurse | Move-Item -Destination "C:\TextFiles"
```

Kommandot använder `Get-ChildItem` cmdleten för att hämta alla underordnade objekt i den aktuella katalogen (representeras av punkten \[ . \] ) och dess under kataloger som har *fil namns tillägget ". txt". Parametern **rekursivt** används för att göra hämtningen rekursiv och include-parametern för att begränsa hämtningen till "*. txt"-filer.

Pipeline-operatorn ( `|` ) skickar resultatet från det här kommandot till `Move-Item` , som flyttar textfilerna till katalogen "TextFiles".

Om filer som ska flyttas till "C:\Textfiles" har samma namn, `Move-Item` visar ett fel och fortsätter, men flyttar bara en fil med varje namn till "C:\Textfiles".
De andra filerna finns kvar i sina ursprungliga kataloger.

Om katalogen "textfiles" (eller något annat element i mål Sök vägen) inte finns, Miss lyckas kommandot.
Den saknade katalogen skapas inte åt dig, även om du använder **Force** -parametern.
`Move-Item` flyttar det första objektet till en fil med namnet "textfiles" och visar sedan ett fel som förklarar att filen redan finns.

`Get-ChildItem`Inte heller flyttar dolda filer som standard.
Om du vill flytta dolda filer använder du parametern **Force** med `Get-ChildItem` .

> [!NOTE]
> I Windows PowerShell 2,0 **Recurse** `Get-ChildItem` måste värdet för **Sök vägs** parametern vara en behållare när du använder rekursivt-parametern för cmdleten.
> Använd parametern **include** för att ange fil namns filtret. txt ( `Get-ChildItem -Path .\* -Include *.txt -Recurse | Move-Item -Destination C:\TextFiles` ).

### Exempel 5: flytta register nycklar och värden till en annan nyckel

Det här kommandot flyttar register nycklar och värden i register nyckeln "mina företag" i `HKLM\Software` till nyckeln "MyNewCompany".
Jokertecknet ( `*` ) anger att innehållet i nyckeln "företaget" ska flyttas, inte själva nyckeln.
I det här kommandot utelämnas de valfria **Sök vägs** -och **mål** parameter namnen.

```powershell
Move-Item "HKLM:\software\mycompany\*" "HKLM:\software\mynewcompany"
```

### Exempel 6: flytta en katalog och dess innehåll till en under katalog till den angivna katalogen

Detta kommando flyttar katalogen "loggar \[ september \` 06 \] " (och dess innehåll) till katalogen "logs \[ 2006 \] ".

```powershell
Move-Item -LiteralPath 'Logs[Sept`06]' -Destination 'Logs[2006]'
```

Parametern **LiteralPath** används i stället för **Path** , eftersom det ursprungliga katalog namnet innehåller vänster hak paren tes tecken (" \[ " och " \] ").
Sökvägen omges också av enkla citat tecken (""), så att bakstrecks symbolen ( \` ) inte tolkas.

**Mål** parametern kräver ingen literal sökväg, eftersom mål variabeln också måste omges av enkla citat tecken, eftersom den innehåller hakparenteser som kan vara feltolkade.

## PARAMETRAR

### -Credential

> [!NOTE]
> Den här parametern stöds inte av några providrar som installeras med PowerShell.
> Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Mål

Anger sökvägen till den plats där objekten flyttas.
Standardvärdet är den aktuella katalogen.
Jokertecken tillåts, men resultatet måste ange en enda plats.

Om du vill byta namn på objektet som flyttas anger du ett nytt namn i värdet för **mål** parametern.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current directory
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Undanta

Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar i åtgärden. Värdet för den här parametern kvalificerar parametern **Path** . Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` . Jokertecken är tillåtna. Parametern **exclude** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Filter

Anger ett filter för att kvalificera **Sök vägs** parametern. [Fil Systems](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) leverantören är den enda installerade PowerShell-providern som stöder användningen av filter. Du kan hitta syntaxen för filter språket för **fil systemet** i [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).
Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -Force

Tvingar kommandot att köras utan att fråga användaren om bekräftelse.
Implementeringen varierar från providern till providern.
Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Inkludera

Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden. Värdet för den här parametern kvalificerar parametern **Path** . Ange ett Sök vägs element eller ett mönster, till exempel `"*.txt"` . Jokertecken är tillåtna. Parametern **include** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### -LiteralPath

Anger en sökväg till en eller flera platser. Värdet för **LiteralPath** används exakt som det har angetts. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken. Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
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
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Anger sökvägen till objektets aktuella plats.
Standardvärdet är den aktuella katalogen.
Jokertecken är tillåtna.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: Current directory
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
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

Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` . Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### System. String

Du kan skicka vidare en sträng som innehåller en sökväg till denna cmdlet.

## UTDATA

### Ingen eller ett objekt som representerar det flyttade objektet

När du använder parametern *Passthru* genererar denna cmdlet ett objekt som representerar det flyttade objektet.
Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

- Den här cmdleten flyttar filer mellan enheter som stöds av samma provider, men kommer bara att flytta kataloger inom samma enhet.
- Eftersom ett `Move-Item` kommando flyttar egenskaper, innehåll och underordnade objekt i ett objekt, är alla flyttningar rekursiva som standard.
- Denna cmdlet är utformad för att fungera med data som exponeras av vilken provider som helst.
  Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .
  Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## RELATERADE LÄNKAR

[Rensa objekt](Clear-Item.md)

[Kopiera objekt](Copy-Item.md)

[Hämta objekt](Get-Item.md)

[Anropa-objekt](Invoke-Item.md)

[Nytt objekt](New-Item.md)

[Ta bort objekt](Remove-Item.md)

[Byt namn – objekt](Rename-Item.md)

[Ange objekt](Set-Item.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)

