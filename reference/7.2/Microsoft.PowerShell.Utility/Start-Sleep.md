---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/10/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/start-sleep?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Sleep
ms.openlocfilehash: e4d06fdd1d5a616c24a4dd7bec10ea4dadea4062
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709732"
---
# Start-Sleep

## SAMMANFATTNING
Pausar aktiviteten i ett skript eller en session under den angivna tids perioden.

## SYNTAX

### Sekunder (standard)

```
Start-Sleep [-Seconds] <Double> [<CommonParameters>]
```

### Millisekunder

```
Start-Sleep -Milliseconds <Int32> [<CommonParameters>]
```

## BESKRIVNING

`Start-Sleep`Cmdleten pausar aktiviteten i ett skript eller en session under den angivna tids perioden. Du kan använda det för många aktiviteter, till exempel vänta på att en åtgärd ska slutföras eller pausas innan en åtgärd upprepas.

## EXEMPEL

### Exempel 1: vila alla kommandon i 15 sekunder

```powershell
Start-Sleep -s 15
```

### Exempel 2: vila alla kommandon i 1,5 sekunder

Det här exemplet gör alla kommandon i sessionen i vilo läge för en och en halv på en sekund.

```powershell
Start-Sleep -Seconds 1.5
```

## PARAMETRAR

### – Millisekunder

Anger hur länge resursen är i millisekunder. Parametern kan vara förkortad som **m**.

```yaml
Type: System.Int32
Parameter Sets: Milliseconds
Aliases: ms

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – Sekunder

Anger hur länge resursen är i sekunder. Du kan utelämna parameter namnet eller så kan du förkorta det som **s**. Från och med PowerShell-6.2.0 accepterar den här parametern nu bråk värden.

```yaml
Type: System.Double
Parameter Sets: Seconds
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### System. Int32

Du kan skicka vidare antalet sekunder till `Start-Sleep` .

## UTDATA

### Inga

Denna cmdlet returnerar inga utdata.

## ANTECKNINGAR

- Du kan också referera till `Start-Sleep` med dess inbyggda alias `sleep` . Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).
- `Ctrl+C` slutar på `Start-Sleep` .
  - `Ctrl+C` delas inte ut från `[Threading.Thread]::Sleep` . Mer information finns i [metoden Thread. vilo läge](/dotnet/api/system.threading.thread.sleep).

## RELATERADE LÄNKAR

