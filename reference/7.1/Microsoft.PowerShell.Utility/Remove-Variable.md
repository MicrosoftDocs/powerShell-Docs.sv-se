---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 07/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-variable?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Variable
ms.openlocfilehash: e6bbb1415a29b8dc3ef916ecc6c3e8bc6754583d
ms.sourcegitcommit: 84fcc90bd018ab76ac4e964d53e7c9c2b5a7b6c6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268701"
---
# Remove-Variable

## SAMMANFATTNING
Tar bort en variabel och dess värde.

## SYNTAX

```
Remove-Variable [-Name] <String[]> [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Scope <String>]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Remove-Variable`Cmdleten tar bort en variabel och dess värde från omfånget som den definieras i, till exempel den aktuella sessionen. Du kan inte använda denna cmdlet för att ta bort variabler som har angetts som konstanter eller som ägs av systemet.

## EXEMPEL

### Exempel 1: ta bort en variabel

```powershell
Remove-Variable Smp
```

Det här kommandot tar bort `$Smp` variabeln.

## PARAMETRAR

### -Undanta

Anger en matris med objekt som denna cmdlet utelämnar från åtgärden. Värdet för den här parametern kvalificerar parametern **Name** . Ange ett namn element eller ett mönster, till exempel "s *". Jokertecken är tillåtna.

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

### -Force

Anger att cmdleten tar bort en variabel även om den är skrivskyddad. Även om du använder **Force** -parametern kan cmdleten inte ta bort en konstant.

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

### -Inkludera

Anger en matris med objekt som denna cmdlet tar bort i åtgärden. Värdet för den här parametern kvalificerar parametern **Name** . Ange ett namn element eller ett mönster, till exempel s *. Jokertecken är tillåtna.

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

### -Name

Anger namnet på den variabel som ska tas bort. Parameter namnet ( **namn** ) är valfritt.
Jokertecken tillåts

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### – Omfattning

Hämtar endast variablerna i det angivna omfånget. De acceptabla värdena för den här parametern är:

- Global
- Lokal
- Skript
- Ett tal i förhållande till det aktuella omfånget (0 till antalet omfattningar, där 0 är det aktuella omfånget och 1 är överordnat)

Lokalt är standard. Mer information finns i [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).

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

Visar vad som skulle hända om cmdleten kördes. Cmdleten körs inte.

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

### System. Management. Automation. PSVariable

Du kan skicka vidare ett variabel objekt till `Remove-Variable` .

## UTDATA

### Inget

Denna cmdlet returnerar inga utdata.

## ANTECKNINGAR

- Ändringarna påverkar bara det aktuella omfånget, till exempel en session. Om du vill ta bort en variabel från alla sessioner lägger du till ett `Remove-Variable` kommando i din PowerShell-profil.

- Du kan också referera till `Remove-Variable` med dess inbyggda alias `rv` . Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).

## RELATERADE LÄNKAR

[Clear-Variable](Clear-Variable.md)

[Get-Variable](Get-Variable.md)

[Ny variabel](New-Variable.md)

[Set-Variable](Set-Variable.md)
