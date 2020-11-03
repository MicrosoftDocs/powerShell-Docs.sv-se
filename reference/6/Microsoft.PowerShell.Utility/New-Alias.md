---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-alias?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Alias
ms.openlocfilehash: f3ae6a8873b82fd0efe39f677c640917ce9dd779
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266984"
---
# New-Alias

## SAMMANFATTNING
Skapar ett nytt alias.

## SYNTAX

```
New-Alias [-Name] <String> [-Value] <String> [-Description <String>] [-Option <ScopedItemOptions>] [-PassThru]
 [-Scope <String>] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

Cmdlet: en **New-alias** skapar ett nytt alias i den aktuella PowerShell-sessionen.
Alias som skapats med hjälp av **New-alias** sparas inte när du avslutar-sessionen eller stänger PowerShell.
Du kan använda Export-Alias-cmdlet: en för att spara Ali Aset information till en fil.
Du kan senare använda **import-alias** för att hämta information om sparat alias.

## EXEMPEL

### Exempel 1: skapa ett alias för en cmdlet

```
PS C:\> New-Alias -Name "List" Get-ChildItem
```

Det här kommandot skapar en lista med namngivna alias som representerar Get-ChildItem-cmdleten.

### Exempel 2: skapa ett skrivskyddat alias för en cmdlet

```
PS C:\> New-Alias -Name "W" -Value Get-WmiObject -Description "quick wmi alias" -Option ReadOnly
PS C:\> Get-Alias -Name "W" | Format-List *
```

Det här kommandot skapar ett alias med namnet W för att representera Get-WmiObject-cmdleten.
Den skapar en beskrivning, ett snabb WMI-alias för aliaset och gör det skrivskyddat.
Den sista raden i kommandot använder Get-Alias för att hämta det nya aliaset och rör det för att Format-List för att visa all information om det.

## PARAMETRAR

### -Beskrivning

Anger en beskrivning av aliaset.
Du kan ange valfri sträng.
Om beskrivningen innehåller blank steg, omger du den med citat tecken.

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

Anger att cmdleten fungerar som Set-Alias om aliaset redan finns.

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

### -Name

Anger det nya aliaset.
Du kan använda alla alfanumeriska tecken i ett alias, men det första tecknet får inte vara en siffra.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Alternativ

Anger värdet för egenskapen **Options** för aliaset.
Giltiga värden är:

- Ingen: aliaset saknar begränsningar (standardvärde)
- ReadOnly: aliaset kan tas bort men kan inte ändras förutom med parametern **Force**
- Konstant: aliaset kan inte tas bort eller ändras
- Privat: aliaset är endast tillgängligt i det aktuella omfånget
- AllScope: aliaset kopieras till alla nya omfattningar som skapas
- Ospecificerad: inget alternativ har angetts

Om du vill se egenskapen **alternativ** för alla alias i sessionen skriver du `Get-Alias | Format-Table -Property Name, Options -AutoSize` .

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, ReadOnly, Constant, Private, AllScope, Unspecified

Required: False
Position: Named
Default value: [System.Management.Automation.ScopedItemOptions]::None
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

### – Omfattning

Anger omfånget för det nya aliaset.
De acceptabla värdena för den här parametern är:

- Global
- Lokal
- Skript
- Ett tal i förhållande till det aktuella omfånget (0 till antalet omfattningar, där 0 är det aktuella omfånget och 1 är överordnat).

Lokalt är standard.
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

### -Värde

Anger namnet på den cmdlet eller det kommando element som har ett alias.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
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

Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### Ingen eller system. Management. Automation. AliasInfo

När du använder parametern *Passthru* genererar **New-alias** ett **system. Management. Automation. AliasInfo** -objekt som representerar det nya aliaset.
Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

* Om du vill skapa ett nytt alias använder du `Set-Alias` eller `New-Alias` . Använd om du vill ändra ett alias `Set-Alias` . Använd om du vill ta bort ett alias `Remove-Item` .

## RELATERADE LÄNKAR

[Exportera-alias](Export-Alias.md)

[Get-alias](Get-Alias.md)

[Importera-alias](Import-Alias.md)

[Set-alias](Set-Alias.md)
