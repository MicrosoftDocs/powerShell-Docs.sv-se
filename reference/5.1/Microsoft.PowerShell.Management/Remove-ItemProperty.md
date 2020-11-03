---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-itemproperty?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-ItemProperty
ms.openlocfilehash: 9ae9c0e7c17a6a63da5487cce138ddce129b975b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265478"
---
# Remove-ItemProperty

## SAMMANFATTNING
Tar bort egenskapen och dess värde från ett objekt.

## SYNTAX

### Sökväg (standard)

```
Remove-ItemProperty [-Path] <String[]> [-Name] <String[]> [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction] [<CommonParameters>]
```

### LiteralPath

```
Remove-ItemProperty -LiteralPath <String[]> [-Name] <String[]> [-Force] [-Filter <String>]
 [-Include <String[]>] [-Exclude <String[]>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [-UseTransaction] [<CommonParameters>]
```

## BESKRIVNING

`Remove-ItemProperty`Cmdleten tar bort en egenskap och dess värde från ett objekt.
Du kan använda den för att ta bort register värden och de data som de lagrar.

## EXEMPEL

### Exempel 1: ta bort ett register värde

Det här kommandot tar bort registervärdet "SmpProperty" och dess data från under nyckeln "SmpApplication" för register nyckeln "HKEY_LOCAL_MACHINE\Software".

Eftersom kommandot utfärdas från en fil system enhet ( `PS C:\>` ), innehåller det den fullständigt kvalificerade sökvägen till "SmpApplication"-under nyckeln, inklusive enheten, `HKLM:` och nyckeln "Software".

Parametern **Name** används för att identifiera det register värde som tas bort.

```powershell
Remove-ItemProperty -Path "HKLM:\Software\SmpApplication" -Name "SmpProperty"
```

### Exempel 2: ta bort ett register värde från HKCU-platsen

De här kommandona tar bort registervärdet "Options" och dess data från under nyckeln "mitt" i "HKEY_CURRENT_USER\Software\MyCompany".

Det första kommandot använder `Set-Location` cmdleten för att ändra den aktuella platsen till **HKEY_CURRENT_USER** enhet ( `HKCU:` ) och under nyckeln "Software\MyCompany\MyApp".

Det andra kommandot använder `Remove-ItemProperty` för att ta bort register värden för "alternativ" och dess data från under nyckeln "mitt".
Eftersom **sökvägen** är obligatorisk använder kommandot en punkt (".") för att ange den aktuella platsen.
**Namnet** används för att ange vilket register värde som ska tas bort.
Parametern **Confirm** används för att begära en användar fråga innan värdet tas bort.

```
PS C:\> Set-Location HKCU:\Software\MyCompany\MyApp
PS HKCU:\Software\MyCompany\MyApp> Remove-ItemProperty -Path . -Name "Options" -Confirm
```

### Exempel 3: ta bort ett register värde med hjälp av pipelinen

Det här kommandot tar bort registervärdet "NoOfEmployees" och dess data från register nyckeln "HKLM\Software\MyCompany".

Kommandot använder `Get-Item` cmdleten för att hämta ett objekt som representerar register nyckeln.
En pipeline-operator () används `|` för att skicka objektet till `Remove-ItemProperty` .
Sedan använder den **Name** -parametern för `Remove-ItemProperty` att ange namnet på registervärdet.

```powershell
Get-Item -Path HKLM:\Software\MyCompany | Remove-ItemProperty -Name NoOfEmployees
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

Tvingar cmdleten att ta bort en egenskap för ett objekt som annars inte kan kommas åt av användaren.
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

Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden.
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

Anger sökvägen till egenskapens aktuella plats.
Till skillnad från parametern **Path** används värdet för **LiteralPath** exakt som det har angetts.
Inga tecken tolkas som jokertecken.
Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.
Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

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

### -Name

Anger namnen på de egenskaper som ska tas bort.
Jokertecken är tillåtna.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: PSProperty

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Path

Anger sökvägen till det objekt vars egenskaper tas bort.
Jokertecken är tillåtna.

```yaml
Type: System.String[]
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
Mer information finns i about_Transactions.

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

### Inget

Denna cmdlet returnerar inga utdata.

## ANTECKNINGAR

I PowerShell-registerposten betraktas register värden som egenskaper för en register nyckel eller under nyckel. Du kan använda **ItemProperty** -cmdletar för att hantera dessa värden.

`Remove-ItemProperty` är utformad för att fungera med data som exponeras av vilken provider som helst. Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` . Mer information finns i about_Providers.

## RELATERADE LÄNKAR

[Hämta objekt](Get-Item.md)

[Clear-ItemProperty](Clear-ItemProperty.md)

[Kopiera – ItemProperty](Copy-ItemProperty.md)

[Get-ItemProperty](Get-ItemProperty.md)

[Move-ItemProperty](Move-ItemProperty.md)

[New-ItemProperty](New-ItemProperty.md)

[Ta bort objekt](Remove-Item.md)

[Byt namn – ItemProperty](Rename-ItemProperty.md)

[Set-ItemProperty](Set-ItemProperty.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
