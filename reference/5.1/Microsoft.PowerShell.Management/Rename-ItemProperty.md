---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-ItemProperty
ms.openlocfilehash: 5cbd228f78da3bf7fa70a001391bc98f63085a73
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265466"
---
# Rename-ItemProperty

## SAMMANFATTNING
Byter namn på en egenskap för ett objekt.

## SYNTAX

### Sökväg (standard)

```
Rename-ItemProperty [-Path] <String> [-Name] <String> [-NewName] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### LiteralPath

```
Rename-ItemProperty -LiteralPath <String> [-Name] <String> [-NewName] <String> [-PassThru] [-Force]
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [<CommonParameters>]
```

## BESKRIVNING

`Rename-ItemProperty`Cmdleten ändrar namnet på en angiven objekt egenskap.
Egenskapens värde har inte ändrats.
Du kan till exempel använda `Rename-ItemProperty` för att ändra namnet på en register post.

## EXEMPEL

### Exempel 1: Byt namn på en register post

Detta kommando byter namn på register posten config som finns i "HKEY_LOCAL_MACHINE\Software\SmpApplication"-nyckeln till "oldconfig".

```powershell
Rename-ItemProperty -Path HKLM:\Software\SmpApplication -Name config -NewName oldconfig
```

## PARAMETRAR

### -Credential

Anger ett användar konto som har behörighet att utföra den här åtgärden.
Standard är den aktuella användaren.

Ange ett användar namn, till exempel "user01" eller "Domain01\User01", eller ange ett **PSCredential** -objekt, t. ex. ett som genererades av `Get-Credential` cmdleten.
Om du anger ett användar namn uppmanas du att ange ett lösen ord.

> [!WARNING]
> Den här parametern stöds inte av några providrar som installeras med Windows PowerShell.

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

### -Undanta

Anger objekt som denna cmdlet utelämnar.
Värdet för den här parametern kvalificerar parametern **Path** .
Ange ett Sök vägs element eller ett mönster, till exempel "*. txt".
Jokertecken är tillåtna.

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

Anger ett filter i formatet eller språket för providern.
Värdet för den här parametern kvalificerar parametern **Path** .

Syntaxen för filtret, inklusive användning av jokertecken, är beroende av providern.
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

Tvingar cmdleten att byta namn på en egenskap för ett objekt som annars inte kan kommas åt av användaren.
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

Anger bara de objekt som cmdleten fungerar på, förutom alla andra.
Värdet för den här parametern kvalificerar parametern **Path** .
Ange ett Sök vägs element eller ett mönster, till exempel "*. txt".
Jokertecken är tillåtna.

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

Anger en sökväg för objekt egenskapen.
Till skillnad från parametern **Path** används värdet för **LiteralPath** exakt som det har angetts.
Inga tecken tolkas som jokertecken.
Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.
Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Anger det aktuella namnet på egenskapen som ska byta namn.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Nyttnamn

Anger det nya namnet för egenskapen.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – PassThru

Returnerar ett objekt som representerar egenskapen Item.
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

Anger sökvägen till det objekt som ska bytas namn på.

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### – UseTransaction

Inkluderar kommandot i den aktiva transaktionen.
Den här parametern är bara giltig medan en transaktion pågår.
Mer information finns i [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
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

Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` . Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### System. String

Du kan skicka vidare en sträng som innehåller en sökväg, men inte en literal sökväg, till denna cmdlet.

## UTDATA

### Ingen, system. Management. Automation. PSCustomObject

Den här cmdleten genererar en **PSCustomObject** som representerar egenskapen döpte item, om du anger parametern *Passthru* .
Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

`Remove-ItemProperty` är utformad för att fungera med data som exponeras av vilken provider som helst. Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` . Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## RELATERADE LÄNKAR

[Clear-ItemProperty](Clear-ItemProperty.md)

[Kopiera – ItemProperty](Copy-ItemProperty.md)

[Get-ItemProperty](Get-ItemProperty.md)

[Move-ItemProperty](Move-ItemProperty.md)

[New-ItemProperty](New-ItemProperty.md)

[Remove-ItemProperty](Remove-ItemProperty.md)

[Byt namn – objekt](Rename-Item.md)

[Set-ItemProperty](Set-ItemProperty.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
