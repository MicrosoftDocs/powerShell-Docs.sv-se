---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/clear-variable?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Variable
ms.openlocfilehash: e42371a58b49a25a9aaf0cc60551ff4bf27e2ec4
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267765"
---
# Clear-Variable

## SAMMANFATTNING
Tar bort värdet för en variabel.

## SYNTAX

```
Clear-Variable [-Name] <String[]> [-Include <String[]>] [-Exclude <String[]>] [-Force] [-PassThru]
 [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

Cmdleten **Clear-Variable** tar bort data som lagras i en variabel, men den tar inte bort variabeln.
Det innebär att variabelns värde är NULL (tomt).
Om variabeln har en angiven data-eller objekt typ, bevarar denna cmdlet den typ av objekt som lagras i variabeln.

## EXEMPEL

### Exempel 1: ta bort värdet för globala variabler som börjar med en Sök sträng

```
PS C:\> Clear-Variable my* -Scope Global
```

Det här kommandot tar bort värdet för globala variabler som har namn som börjar med My.

### Exempel 2: ta bort en variabel i ett underordnat område, men inte över överordnat område

```
PS C:\> $a=3
PS C:\> &{ Clear-Variable a }
PS C:\> $a
3
```

De här kommandona visar att att rensa en variabel i ett underordnat omfång inte rensar värdet i det överordnade omfånget.
Det första kommandot ställer in värdet för variabeln $A till 3.
Det andra kommandot använder operatorn Invoke (&) för att köra kommandot **Clear-Variable** i ett nytt omfång.
Variabeln har rensats i det underordnade omfånget (även om den inte finns), men den har inte rensats i det lokala omfånget.
Det tredje kommandot, som hämtar värdet för $A, visar att värdet 3 inte påverkas.

### Exempel 3: ta bort värdet för den angivna variabeln

```
PS C:\> Clear-Variable -Name "Processes"
```

Det här kommandot tar bort värdet för variabeln med namnet processs.
När cmdleten har slutfört åtgärden finns variabeln som heter processer fortfarande, men värdet är null.

## PARAMETRAR

### -Undanta

Anger en matris med objekt som denna cmdlet utelämnar i åtgärden.
Värdet för den här parametern kvalificerar parametern *Name* .
Ange ett namn element eller ett mönster, till exempel "s *".
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

### -Force

Tillåter cmdleten att ta bort en variabel även om den är skrivskyddad.
Cmdleten kan inte ta bort konstanter även om du använder Force-parametern.

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

Anger en matris med objekt som denna cmdlet inkluderar i åtgärden.
Värdet för den här parametern kvalificerar parametern *Name* .
Ange ett namn element eller ett mönster, till exempel "s *".
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

### -Name

Anger namnet på den variabel som ska rensas.
Jokertecken är tillåtna.
Den här parametern är obligatorisk, men parameter namnet ("name") är valfritt.

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

Anger omfattningen som detta alias är giltigt i.

De acceptabla värdena för den här parametern är:

- Global
- Lokal
- Skript

Du kan också använda ett tal i förhållande till det aktuella omfånget (0 till antalet omfattningar, där 0 är det aktuella omfånget och 1 är överordnat).
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

### Ingen eller system. Management. Automation. PSVariable

När du använder parametern *Passthru* genererar denna cmdlet ett **system. Management. Automation. PSVariable** -objekt som representerar den rensade variabeln.
Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

* Om du vill ta bort en variabel, tillsammans med dess värde, använder du Remove-Variable eller ta bort objekt.

  Den här cmdleten tar inte bort värdena för variabler som anges som konstanter eller ägs av systemet, även om du använder *Force* -parametern.

  Om den variabel som du tar bort inte finns, har cmdleten ingen inverkan.
Den skapar inte en variabel med ett null-värde.

  Du kan också referera till **Clear-Variable** med dess inbyggda alias, CLV.
Mer information finns i about_Aliases.

*

## RELATERADE LÄNKAR

[Get-Variable](Get-Variable.md)

[Ny variabel](New-Variable.md)

[Ta bort variabel](Remove-Variable.md)

[Set-Variable](Set-Variable.md)

