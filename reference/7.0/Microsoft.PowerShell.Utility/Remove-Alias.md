---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/24/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-alias?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Alias
ms.openlocfilehash: 6f98a910e43b87793ac4f2af8ffb069d3e5d47ba
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262335"
---
# Remove-Alias

## SAMMANFATTNING
Ta bort ett alias från den aktuella sessionen.

## SYNTAX

### Standard (standard)

```
Remove-Alias [-Name] <String[]> [-Scope <String>] [-Force] [<CommonParameters>]
```

## BESKRIVNING

`Remove-Alias`Cmdleten tar bort ett alias från den aktuella PowerShell-sessionen. Använd parametern **Force** om du vill ta bort ett alias med **alternativ** egenskapen inställd på **skrivskyddad**.

`Remove-Alias`Cmdleten introducerades i PowerShell 6,0.

## EXEMPEL

### Exempel 1 – ta bort ett alias

I det här exemplet tas ett alias `del` som heter som representerar `Remove-Item` cmdleten bort.

```powershell
Remove-Alias -Name del
```

### Exempel 2 – ta bort alla icke-konstanta alias

I det här exemplet tas alla alias från den aktuella PowerShell-sessionen bort, förutom alias med egenskapen **alternativ** inställd på **konstant**. När kommandot har körts är aliasen tillgängliga i andra PowerShell-sessioner eller nya PowerShell-sessioner.

```powershell
Get-Alias | Where-Object { $_.Options -NE "Constant" } | Remove-Alias -Force
```

`Get-Alias` hämtar alla alias i PowerShell-sessionen och skickar objekten nedåt i pipelinen.
`Where-Object` använder ett-skript block och egenskapen automatisk variabel ( `$_` ) och **alternativ** representerar det aktuella pipeline-objektet. Parametern **Ne** (inte lika med) väljer objekt som inte har något **alternativ** värde inställt på **konstant**. `Remove-Alias` använder **Force** -parametern för att ta bort alias, inklusive skrivskyddade alias, från PowerShell-sessionen.

## PARAMETRAR

### -Force

Anger att cmdleten tar bort ett alias, inklusive alias med **alternativ** egenskapen inställd på **skrivskyddad**. Parametern **Force** kan inte ta bort ett alias med en **alternativ** egenskap inställd på **konstant**.

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

### -Name

Anger namnet på det alias som ska tas bort.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### – Omfattning

Påverkar endast alias i det angivna omfånget. Standard omfånget är **lokalt**. Mer information finns i [about_Scopes](../microsoft.powershell.core/about/about_scopes.md).

De acceptabla värdena för den här parametern är:

- Global
- Lokal
- Skript
- Ett tal i förhållande till det aktuella omfånget (0 till antalet omfattningar, där 0 är det aktuella omfånget och 1 är överordnat)

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System.String[]

Du kan skicka ett aliasresurspost till **Remove-alias**.

## UTDATA

### Inget

Denna cmdlet returnerar inga utdata.

## ANTECKNINGAR

Ändringarna påverkar bara det aktuella omfånget. Om du vill ta bort ett alias från alla sessioner lägger du till kommandot **Remove-alias** i din PowerShell-profil.

Mer information finns i [about_Aliases](../microsoft.powershell.core/about/about_aliases.md).

## RELATERADE LÄNKAR

[about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[Exportera-alias](Export-Alias.md)

[Get-alias](Get-Alias.md)

[Importera-alias](Import-Alias.md)

[Nytt-alias](New-Alias.md)

[Set-alias](Set-Alias.md)

[Where-objekt](../Microsoft.PowerShell.Core/Where-Object.md)
