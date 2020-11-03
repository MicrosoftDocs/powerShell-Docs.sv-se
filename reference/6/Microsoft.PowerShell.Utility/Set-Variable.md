---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-variable?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Variable
ms.openlocfilehash: 392f7d4be1e174e9ce270f4351adefbca4fe38e5
ms.sourcegitcommit: fcf7bd222f5ee3fdbe21ffddcae47050cffe7e42
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/03/2020
ms.locfileid: "93273602"
---
# Set-Variable

## SAMMANFATTNING
Anger värdet för en variabel. Skapar variabeln om en med det begärda namnet inte finns.

## SYNTAX

```
Set-Variable [-Name] <String[]> [[-Value] <Object>] [-Include <String[]>] [-Exclude <String[]>]
 [-Description <String>] [-Option <ScopedItemOptions>] [-Force] [-Visibility <SessionStateEntryVisibility>]
 [-PassThru] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Set-Variable`Cmdlet: en tilldelar ett värde till en angiven variabel eller ändrar det aktuella värdet. Om variabeln inte finns skapar cmdleten den.

## EXEMPEL

### Exempel 1: Ange en variabel och hämta dess värde

De här kommandona ställer in värdet för `$desc` variabeln till `A description` och hämtar värdet för variabeln.

```powershell
Set-Variable -Name "desc" -Value "A description"
Get-Variable -Name "desc"
```

```Output
Name                           Value
----                           -----
desc                           A description
```

### Exempel 2: Ange en global, skrivskyddad variabel

I det här exemplet skapas en global, skrivskyddad variabel som innehåller alla processer i systemet och sedan visas alla egenskaper för variabeln.

```powershell
Set-Variable -Name "processes" -Value (Get-Process) -Option constant -Scope global -Description "All processes" -PassThru |
    Format-List -Property *
```

Kommandot använder `Set-Variable` cmdleten för att skapa variabeln. Parametern **Passthru** används för att skapa ett objekt som representerar den nya variabeln och använder pipelinen ( `|` ) för att skicka objektet till `Format-List` cmdleten. Den använder **egenskaps** parametern för `Format-List` med värdet all () för `*` att visa alla egenskaper för den nya variabeln.

Värdet `(Get-Process)` omges av parenteser för att säkerställa att det körs innan det lagras i variabeln. Annars innehåller variabeln orden " **Get-process** ".

### Exempel 3: förstå offentliga eller privata variabler

Det här exemplet visar hur du ändrar synligheten för en variabel till `Private` . Den här variabeln kan läsas och ändras av skript med de behörigheter som krävs, men den är inte synlig för användaren.

```
PS C:\> New-Variable -Name "counter" -Visibility Public -Value 26
PS C:\> $Counter
26

PS C:\> Get-Variable c*

Name                  Value
----                  -----
Culture               en-US
ConsoleFileName
ConfirmPreference     High
CommandLineParameters {}
Counter               26

PS C:\> Set-Variable -Name "counter" -Visibility Private
PS C:\> Get-Variable c*

Name                  Value
----                  -----
Culture               en-US
ConsoleFileName
ConfirmPreference     High
CommandLineParameters {}

PS C:\> $counter
"Cannot access the variable '$counter' because it is a private variable"

PS C:\> .\use-counter.ps1
#Commands completed successfully.
```

Det här kommandot visar hur du ändrar synligheten för en variabel till privat. Den här variabeln kan läsas och ändras av skript med de behörigheter som krävs, men den är inte synlig för användaren.

## PARAMETRAR

### -Beskrivning

Anger beskrivningen av variabeln.

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

### -Undanta

Anger en matris med objekt som denna cmdlet exkluderar från åtgärden. Värdet för den här parametern kvalificerar parametern **Path** . Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .
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

Gör att du kan skapa en variabel med samma namn som en befintlig skrivskyddad variabel eller ändra värdet för en skrivskyddad variabel.

Som standard kan du skriva över en variabel, om inte variabeln har ett alternativ värde för `ReadOnly` eller `Constant` . Mer information finns i **alternativ** parametern.

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

Anger en matris med objekt som denna cmdlet inkluderar i åtgärden. Värdet för den här parametern kvalificerar parametern **Name** . Ange ett namn eller namn mönster, till exempel `c*` . Jokertecken är tillåtna.

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

Anger variabelns namn.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Alternativ

Anger värdet för egenskapen **Options** för variabeln.

Giltiga värden är:

- `None`: Anger inga alternativ. ("Ingen" är standard.)
- `ReadOnly`: Kan tas bort. Kan inte ändras, med undantag för parametern Force.
- `Constant`: Kan inte tas bort eller ändras. `Constant` är endast giltig när du skapar en variabel. Det går inte att ändra alternativen för en befintlig variabel till `Constant` .
- `Private`: Variabeln är endast tillgänglig i det aktuella omfånget.
- `AllScope`: Variabeln kopieras till alla nya omfattningar som skapas.

```yaml
Type: System.Management.Automation.ScopedItemOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, ReadOnly, Constant, Private, AllScope, Unspecified

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – PassThru

Returnerar ett objekt som representerar den nya variabeln. Som standard genererar denna cmdlet inga utdata.

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

### – Omfattning

Anger variabelns omfång. De acceptabla värdena för den här parametern är:

- Global
- Lokal
- Skript
- Privat
- Ett tal i förhållande till det aktuella omfånget (0 till antalet omfattningar, där 0 är det aktuella omfånget och 1 är överordnat).

Lokalt är standard.

Mer information finns i [about_Scopes](../Microsoft.PowerShell.Core/About/about_scopes.md).

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

### -Värde

Anger värdet för variabeln.

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

### -Synlighet

Bestämmer om variabeln är synlig utanför den session där den skapades. Den här parametern är avsedd för användning i skript och kommandon som skickas till andra användare.

Giltiga värden är:

- Offentlig: variabeln är synlig. ("Offentlig" är standard.)
- Privat: variabeln är inte synlig.

När en variabel är privat visas den inte i listor med variabler, till exempel de som returneras av `Get-Variable` eller i visar **variabeln:** enhet. Kommandon för att läsa eller ändra värdet för en privat variabel returnerar ett fel. Användaren kan dock köra kommandon som använder en privat variabel om kommandona skrevs i den session där variabeln definierades.

```yaml
Type: System.Management.Automation.SessionStateEntryVisibility
Parameter Sets: (All)
Aliases:
Accepted values: Public, Private

Required: False
Position: Named
Default value: Public
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

### System. Object

Du kan skicka ett objekt som representerar värdet för variabeln till `Set-Variable` .

## UTDATA

### Ingen eller system. Management. Automation. PSVariable

När du använder parametern **Passthru** `Set-Variable` genereras ett **system. Management. Automation. PSVariable** -objekt som representerar den nya eller ändrade variabeln.
Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Clear-Variable](Clear-Variable.md)

[Get-Variable](Get-Variable.md)

[Ny variabel](New-Variable.md)

[Ta bort variabel](Remove-Variable.md)
