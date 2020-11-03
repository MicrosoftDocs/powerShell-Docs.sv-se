---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 5/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-variable?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Variable
ms.openlocfilehash: 128bdd997e006723a69997e1419efd2f012e97f6
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93263192"
---
# Get-Variable

## SAMMANFATTNING
Hämtar variablerna i den aktuella konsolen.

## SYNTAX

```
Get-Variable [[-Name] <String[]>] [-ValueOnly] [-Include <String[]>] [-Exclude <String[]>] [-Scope <String>]
 [<CommonParameters>]
```

## BESKRIVNING

`Get-Variable`Cmdlet: en hämtar PowerShell-variablerna i den aktuella konsolen.
Du kan bara hämta värdena för variablerna genom att ange parametern **ValueOnly** , och du kan filtrera variablerna som returneras efter namn.

## EXEMPEL

### Exempel 1: Hämta variabler per bokstav

Det här kommandot hämtar variabler med namn som börjar med bokstaven m.
Kommandot hämtar också variablernas värde.

```powershell
Get-Variable m*
```

### Exempel 2: Hämta variabel värden efter bokstav

Det här kommandot hämtar bara värdena för variabler som har namn som börjar med m.

```powershell
Get-Variable m* -ValueOnly
```

### Exempel 3: Hämta variabler med två bokstäver

Det här kommandot hämtar information om variablerna som börjar med bokstaven M eller bokstaven P.

```powershell
Get-Variable -Include M*,P*
```

### Exempel 4: Hämta variabler efter omfång

Det första kommandot hämtar bara de variabler som har definierats i det lokala omfånget.
Det motsvarar `Get-Variable -Scope Local` och kan förkortas som `gv -s 0` .

Det andra kommandot använder `Compare-Object` cmdleten för att hitta variablerna som har definierats i det överordnade omfånget (område 1), men är bara synliga i det lokala omfånget (omfånget 0).

```powershell
Get-Variable -Scope 0
Compare-Object (Get-Variable -Scope 0) (Get-Variable -Scope 1)
```

## PARAMETRAR

### -Undanta

Anger en matris med objekt som denna cmdlet exkluderar från åtgärden.
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

### -Inkludera

Anger en matris med objekt som cmdleten ska fungera på, förutom alla andra.
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

Anger namnet på variabeln.
Jokertecken är tillåtna.
Du kan också skicka ett variabel namn till `Get-Variable` .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### – Omfattning

Anger variablerna i omfånget. De acceptabla värdena för den här parametern är:

- **Global**
- **Inställningar**
- **Över**
- Ett tal i förhållande till det aktuella omfånget (0 till antalet omfattningar, där 0 är det aktuella omfånget och 1 är överordnat)

**Lokalt** är standard.
Mer information finns i [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).

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

### -ValueOnly

Anger att denna cmdlet endast hämtar värdet för variabeln.

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

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### System. String

Du kan skicka vidare en sträng som innehåller variabel namnet till `Get-Variable` .

## UTDATA

### System. Management. Automation. PSVariable

Denna cmdlet returnerar ett **system. Management. AutomationPSVariable** -objekt för varje variabel som det får. Objekt typen är beroende av variabeln.

### System. Object []

När du anger parametern **ValueOnly** , om den angivna variabelns värde är en samling, `Get-Variable` returnerar en `[System.Object[]]` . Det här beteendet förhindrar normal pipeline-åtgärd från att bearbeta variabelns värden en i taget. En lösning för att tvinga samlings uppräkning är att omge `Get-Variable` kommandot med parentes.

## ANTECKNINGAR

- Denna cmdlet hanterar inte miljövariabler. Om du vill hantera miljövariabler kan du använda miljövariabeln Provider.

## RELATERADE LÄNKAR

[Clear-Variable](Clear-Variable.md)

[Ny variabel](New-Variable.md)

[Ta bort variabel](Remove-Variable.md)

[Set-Variable](Set-Variable.md)
