---
external help file: Microsoft.PowerShell.ConsoleHost.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Host
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.host/start-transcript?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Transcript
ms.openlocfilehash: 2e4380163c7dc34c84460a1cfef3ef2f4b33507b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264476"
---
# Start-Transcript

## SAMMANFATTNING
Skapar en post med hela eller delar av en PowerShell-session till en textfil.

## SYNTAX

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

## BESKRIVNING

`Start-Transcript`Cmdleten skapar en post med hela eller delar av en PowerShell-session till en textfil. Avskriften innehåller alla kommandon som användaren skriver och alla utdata som visas i-konsolen.

Från och med Windows PowerShell 5,0 `Start-Transcript` innehåller värd namnet i det genererade fil namnet för alla avskrifter. Detta är särskilt användbart när företagets loggning är centraliserad.
Filer som skapas av `Start-Transcript` cmdleten innehåller slumpmässiga tecken i namn för att förhindra eventuell överskrivning eller duplicering när två eller fler avskrifter startas samtidigt.
Detta förhindrar även obehörig identifiering av avskrifter som lagras i en centraliserad fil resurs.

## EXEMPEL

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

## PARAMETRAR

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

## INDATA

### Inget

Det går inte att skicka pipe-objekt till denna cmdlet.

## UTDATA

### System. String

Denna cmdlet returnerar en sträng som innehåller ett bekräftelse meddelande och sökvägen till utdatafilen.

## ANTECKNINGAR

Om du vill stoppa en avskrift använder du `Stop-Transcript` cmdleten.

Om du vill spela in en hel session lägger du till `Start-Transcript` kommandot i din profil. Mer information finns i [about_Profiles](../Microsoft.PowerShell.Core/About/about_Profiles.md).

## RELATERADE LÄNKAR

[Stopp-avskrift](Stop-Transcript.md)
