---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-expression?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-Expression
ms.openlocfilehash: f0fca430b4a378b88498a96ab6c9dc0f4d4881a4
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264957"
---
# Invoke-Expression

## SAMMANFATTNING
Kör kommandon eller uttryck på den lokala datorn.

## SYNTAX

```
Invoke-Expression [-Command] <String> [<CommonParameters>]
```

## BESKRIVNING

`Invoke-Expression`Cmdleten utvärderar eller kör en angiven sträng som ett kommando och returnerar resultatet av uttrycket eller kommandot. Utan `Invoke-Expression` , returneras en sträng som skickats på kommando raden (avskärmad) oförändrad.

Uttryck utvärderas och körs i det aktuella omfånget. Mer information finns i [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).

> [!CAUTION]
> Vidta rimliga försiktighets åtgärder när du använder `Invoke-Expression` cmdleten i skript. När `Invoke-Expression` du använder för att köra ett kommando som användaren anger, kontrollerar du att kommandot är säkert att köra innan du kör det. I allmänhet är det bäst att utforma ditt skript med fördefinierade ingångs alternativ i stället för att tillåta fri hands text.

## EXEMPEL

### Exempel 1: utvärdera ett uttryck

```powershell
$Command = "Get-Process"
$Command
```

```Output
Get-Process
```

```powershell
Invoke-Expression $Command
```

```Output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id   ProcessName
-------  ------    -----      ----- -----   ------     --   -----------
296       4       1572       1956    20       0.53     1348   AdtAgent
270       6       1328       800     34       0.06     2396   alg
67        2       620        484     20       0.22     716    ati2evxx
1060      15      12904      11840   74       11.48    892    CcmExec
1400      33      25280      37544   223      38.44    2564   communicator
...
```

Det här exemplet demonstrerar användningen av `Invoke-Expression` för att utvärdera ett uttryck. Utan `Invoke-Expression` , skrivs uttrycket ut, men utvärderas inte.

Det första kommandot tilldelar värdet `Get-Process` (en sträng) till `$Command` variabeln.

Det andra kommandot visar resultatet av att skriva variabel namnet på kommando raden. PowerShell upprepar strängen.

Det tredje kommandot använder `Invoke-Expression` för att utvärdera strängen.

### Exempel 2: kör ett skript på den lokala datorn

```powershell
Invoke-Expression -Command "C:\ps-test\testscript.ps1"
"C:\ps-test\testscript.ps1" | Invoke-Expression
```

Dessa kommandon används `Invoke-Expression` för att köra ett skript TestScript.ps1 på den lokala datorn. De två kommandona är likvärdiga. Först används **kommando** parametern för att ange kommandot som ska köras.
Den andra använder en pipeline-operator ( `|` ) för att skicka kommando strängen till `Invoke-Expression` .

### Exempel 3: köra ett kommando i en variabel

```powershell
$Command = 'Get-Process | where {$_.cpu -gt 1000}'
Invoke-Expression $Command
```

I det här exemplet körs en kommando sträng som sparas i `$Command` variabeln.

Kommando strängen omges av enkla citat tecken eftersom den innehåller en variabel, `$_` som representerar det aktuella objektet. Om den omges av dubbla citat tecken `$_` skulle variabeln ersättas av sitt värde innan den sparades i `$Command` variabeln.

### Exempel 4: Hämta och kör en cmdlet Help-exempel

```powershell
$Cmdlet_name = "Get-EventLog"
$Example_number = 1
$Example_code = (Get-Help $Cmdlet_name).examples.example[($Example_number-1)].code
Invoke-Expression $Example_code
```

Det här kommandot hämtar och kör det första exemplet i `Get-EventLog` Hjälp avsnittet för cmdleten.

Om du vill köra ett exempel på en annan cmdlet ändrar du värdet för `$Cmdlet_name` variabeln till namnet på cmdleten. Och ändra `$Example_number` variabeln till det exempel nummer som du vill köra. Kommandot Miss lyckas om exempel numret inte är giltigt.

## PARAMETRAR

### -Kommando

Anger det kommando eller uttryck som ska köras. Skriv kommandot eller uttrycket eller ange en variabel som innehåller kommandot eller uttrycket. **Kommando** parametern måste anges.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### System. String eller PSObject

Du kan skicka vidare ett objekt som representerar kommandot till `Invoke-Expression` .
Använd den `$Input` automatiska variabeln för att representera inobjekten i kommandot.

## UTDATA

### PSObject

Returnerar utdata som genereras av det anropade kommandot (värdet för **kommando** parametern).

## ANTECKNINGAR

I de flesta fall anropar du uttryck med PowerShell: s anrops operator och uppnår samma resultat.
Anrops operatorn är en säkrare metod. Mer information finns i [about_Operators](../microsoft.powershell.core/about/about_operators.md#call-operator-).

## RELATERADE LÄNKAR

[Invoke-kommando](../Microsoft.PowerShell.Core/Invoke-Command.md)

[about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md)
