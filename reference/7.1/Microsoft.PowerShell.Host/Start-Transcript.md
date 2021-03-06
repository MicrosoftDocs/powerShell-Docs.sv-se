---
external help file: Microsoft.PowerShell.ConsoleHost.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Host
ms.date: 01/26/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.host/start-transcript?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Transcript
ms.openlocfilehash: 32d8893190489be0a102b2db4dee3482133a4243
ms.sourcegitcommit: 11880ca974fe2df308191c9f6dcdfe0b89c2dc67
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/27/2021
ms.locfileid: "98860849"
---
# Start-Transcript

## Sammanfattning
Skapar en post med hela eller delar av en PowerShell-session till en textfil.

## Syntax

### ByPath (standard)

```
Start-Transcript [[-Path] <String>] [-Append] [-Force] [-NoClobber] [-IncludeInvocationHeader]
 [-UseMinimalHeader] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

### ByLiteralPath

```
Start-Transcript [[-LiteralPath] <String>] [-Append] [-Force] [-NoClobber]
 [-IncludeInvocationHeader] [-UseMinimalHeader] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

### ByOutputDirectory

```
Start-Transcript [[-OutputDirectory] <String>] [-Append] [-Force] [-NoClobber]
 [-IncludeInvocationHeader] [-UseMinimalHeader] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

## Description

`Start-Transcript`Cmdleten skapar en post med hela eller delar av en PowerShell-session till en textfil. Avskriften innehåller alla kommandon som användaren skriver och alla utdata som visas i-konsolen.

Från och med Windows PowerShell 5,0 `Start-Transcript` innehåller värd namnet i det genererade fil namnet för alla avskrifter. Detta är särskilt användbart när företagets loggning är centraliserad.
Filer som skapas av `Start-Transcript` cmdleten innehåller slumpmässiga tecken i namn för att förhindra eventuell överskrivning eller duplicering när två eller fler avskrifter startas samtidigt.
Detta förhindrar även obehörig identifiering av avskrifter som lagras i en centraliserad fil resurs.

När du använder parametern **APPEND** , om mål filen inte har en byte ordnings markering (BOM) `Start-Transcript` som standard `ASCII` kodning i målfilen. Det här beteendet kan resultera i felaktig kodning av mulitbyte tecken i avskriften.

## Exempel

### Exempel 1: starta en avskrifts fil med standardinställningar

```powershell
Start-Transcript
```

Det här kommandot startar en avskrift på standard platsen för filen.

### Exempel 2: starta en avskrifts fil på en angiven plats

```powershell
Start-Transcript -Path "C:\transcripts\transcript0.txt" -NoClobber
```

Det här kommandot startar en avskrift i `Transcript0.txt` filen i `C:\transcripts` . Eftersom parametern **NoClobber** används förhindrar kommandot att eventuella befintliga filer skrivs över. `Transcript0.txt`Kommandot Miss lyckas om filen redan finns.

## Parametrar

### -Lägg till

Anger att den här cmdleten lägger till den nya avskriften i slutet av en befintlig fil. Använd parametern **Path** för att ange filen.

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

### -Force

Tillåter cmdleten att lägga till avskriften i en befintlig skrivskyddad fil. När den används i en skrivskyddad fil ändrar cmdleten fil behörighet till Read-Write. Cmdleten kan inte åsidosätta säkerhets begränsningar när den här parametern används.

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

### -IncludeInvocationHeader

Anger att denna cmdlet loggar tidsstämpeln när kommandon körs.

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

### -UseMinimalHeader

Lägga en kort rubrik till avskriften, i stället för den detaljerade rubriken som ingår som standard. Den här parametern lades till i PowerShell 6,2.

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

Anger en plats för avskrifts filen. Till skillnad från parametern **Path** används värdet för parametern **LiteralPath** exakt som det har angetts. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken. Enkla citat tecken meddelar PowerShell att inte tolka några tecken som escape-sekvenser.

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -NoClobber

Anger att denna cmdlet inte kommer att skriva över en befintlig fil. Om det finns en avskrifts fil som finns på den angivna sökvägen `Start-Transcript` skrivs filen som standard över utan varning.

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

### – OutputDirectory

Anger en angiven sökväg och mapp där du vill spara en avskrift. PowerShell tilldelar automatiskt avskrifts namnet.

```yaml
Type: System.String
Parameter Sets: ByOutputDirectory
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Anger en plats för avskrifts filen. Ange en sökväg till en `.txt` fil. Jokertecken är inte tillåtna.

Om du inte anger en sökväg, `Start-Transcript` använder sökvägen i värdet för den `$Transcript` globala variabeln. Om du inte har skapat den här variabeln `Start-Transcript` lagras avskrifterna i `$Home\My Documents directory as \PowerShell_transcript.<time-stamp>.txt` filerna.

Om någon av katalogerna i sökvägen inte finns, Miss lyckas kommandot.

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: False
Position: 0
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

## Indata

### Inget

Det går inte att skicka pipe-objekt till denna cmdlet.

## Utdata

### System. String

Denna cmdlet returnerar en sträng som innehåller ett bekräftelse meddelande och sökvägen till utdatafilen.

## Kommentarer

Om du vill stoppa en avskrift använder du `Stop-Transcript` cmdleten.

Om du vill spela in en hel session lägger du till `Start-Transcript` kommandot i din profil. Mer information finns i [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).

## Relaterade länkar

[Stopp-avskrift](Stop-Transcript.md)
