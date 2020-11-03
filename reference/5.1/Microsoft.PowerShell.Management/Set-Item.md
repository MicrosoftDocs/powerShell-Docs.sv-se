---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-item?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Item
ms.openlocfilehash: c49cc60ec6ebf3f62a94f5511b55d578337be804
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265412"
---
# Set-Item

## SAMMANFATTNING
Ändrar värdet för ett objekt till det värde som anges i kommandot.

## SYNTAX

### Sökväg (standard)

```
Set-Item [-Path] <String[]> [[-Value] <Object>] [-Force] [-PassThru] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### LiteralPath

```
Set-Item -LiteralPath <String[]> [[-Value] <Object>] [-Force] [-PassThru] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

## BESKRIVNING

`Set-Item`Cmdleten ändrar värdet för ett objekt, till exempel en variabel eller register nyckel, till det värde som anges i kommandot.

## EXEMPEL

### Exempel 1: skapa ett alias

Det här kommandot skapar ett alias för NP för anteckningar.

```powershell
Set-Item -Path alias:np -Value "c:\windows\notepad.exe"
```

### Exempel 2: ändra värdet för en miljö variabel

Det här kommandot ändrar värdet för UserRole-miljövariabeln till administratör.

```powershell
Set-Item -Path env:UserRole -Value "Administrator"
```

### Exempel 3: ändra prompt-funktionen

Det här kommandot ändrar prompt-funktionen så att den visar tiden före sökvägen.

```powershell
Set-Item -Path function:prompt -Value {'PS '+ (Get-Date -Format t) + " " + (Get-Location) + '> '}
```

### Exempel 4: Ange alternativ för din prompt-funktion

Det här kommandot anger **AllScope** -och **ReadOnly** -alternativen för prompt-funktionen.
Det här kommandot använder den dynamiska parametern **alternativ** i `Set-Item` .
**Alternativ** -parametern är bara tillgänglig `Set-Item` när du använder den med **alias** -eller **funktions** leverantören.

```powershell
Set-Item -Path function:prompt -Options "AllScope,ReadOnly"
```

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

Tvingar cmdleten att ange objekt som annars inte kan ändras, till exempel skrivskyddat alias eller variabler. Cmdleten kan inte ändra konstanta alias eller variabler.
Implementeringen varierar från providern till providern.
Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).
Även om du använder *Force* -parametern kan inte cmdlet: en åsidosätta säkerhets begränsningar.

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
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – PassThru

Skickar ett objekt som representerar objektet till pipelinen.
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

Anger en sökväg till objektets placering.
Jokertecken är tillåtna.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
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

### -Värde

Anger ett nytt värde för objektet.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
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

Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` . Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### System. Object

Du kan skicka ett objekt som representerar det nya värdet för objektet till denna cmdlet.

## UTDATA

### Ingen eller ett objekt som representerar det nya eller ändrade objektet.

Denna cmdlet genererar ett objekt som representerar objektet, om du anger parametern *Passthru* .
Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

- `Set-Item` stöds inte av PowerShell-filsystem-providern. Om du vill ändra värdena för objekt i fil systemet använder du `Set-Content` cmdleten.
- I register enheterna `HKLM:` och `HKCU:` `Set-Item` ändrar data i (standard) värdet för en register nyckel.
  - Om du vill skapa och ändra namn på register nycklar använder du `New-Item` `Rename-Item` cmdleten och.
  - Använd `New-ItemProperty` cmdletarna, och för att ändra namn och data i register värden `Set-ItemProperty` `Rename-ItemProperty` .
- `Set-Item` är utformad för att fungera med data som exponeras av vilken provider som helst.
  Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PsProvider` .
  Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## RELATERADE LÄNKAR

[Rensa objekt](Clear-Item.md)

[Kopiera objekt](Copy-Item.md)

[Hämta objekt](Get-Item.md)

[Anropa-objekt](Invoke-Item.md)

[Flytta objekt](Move-Item.md)

[Nytt objekt](New-Item.md)

[Ta bort objekt](Remove-Item.md)

[Byt namn – objekt](Rename-Item.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
