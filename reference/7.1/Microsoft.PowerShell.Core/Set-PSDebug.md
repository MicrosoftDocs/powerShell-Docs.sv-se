---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 08/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-psdebug?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSDebug
ms.openlocfilehash: a0b5d7e86f9d63b487bc093feb18ecc7a4496999
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267296"
---
# Set-PSDebug

## SAMMANFATTNING
Aktiverar och inaktiverar funktioner för skript fel sökning, ställer in spårnings nivå och växlar till strikt läge.

## SYNTAX

### på

```
Set-PSDebug [-Trace <Int32>] [-Step] [-Strict] [<CommonParameters>]
```

### av

```
Set-PSDebug [-Off] [<CommonParameters>]
```

## BESKRIVNING

`Set-PSDebug`Cmdleten aktiverar och inaktiverar funktioner för skript fel sökning, ställer in spårnings nivån och växlar till strikt läge. Som standard är PowerShell-felsöknings funktionerna inaktiverade.

När **spårnings** parametern har värdet `1` , spåras varje rad med skript när den körs. När parametern har värdet `2` , spåras även variabel tilldelningar, funktions anrop och skript anrop. Om du anger parametern **steg** uppmanas du innan varje rad i skriptet körs.

## EXEMPEL

### Exempel 1: Ange spårnings nivå

Det här exemplet anger spårnings nivån till `2` och kör sedan ett skript som visar siffrorna 1, 2 och
3.

```powershell
Set-PSDebug -Trace 2; foreach ($i in 1..3) {$i}
```

```Output
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in  >>>> 1..3) {$i}
DEBUG:     ! SET $foreach = 'IEnumerator'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $i = '1'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in 1..3) { >>>> $i}
1
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $i = '2'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in 1..3) { >>>> $i}
2
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $i = '3'.
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ($i in 1..3) { >>>> $i}
3
DEBUG:    1+ Set-PSDebug -Trace 2; foreach ( >>>> $i in 1..3) {$i}
DEBUG:     ! SET $foreach = ''.
```

### Exempel 2: Aktivera stegning

Det här exemplet aktiverar stegning och kör sedan ett skript som visar siffrorna 1, 2 och 3.

```powershell
Set-PSDebug -Step; foreach ($i in 1..3) {$i}
```

```Output
Continue with this operation?
   1+ Set-PSDebug -Step; foreach ($i in  >>>> 1..3) {$i}
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): A
DEBUG:    1+ Set-PSDebug -Step; foreach ($i in  >>>> 1..3) {$i}
1
2
3
```

### Exempel 3: Använd strikt läge

I det här exemplet placeras PowerShell i strikt läge och försöker komma åt en variabel som inte har ett tilldelat värde.

```powershell
Set-PSDebug -Strict; $NewVar
```

```Output
The variable '$NewVar' cannot be retrieved because it has not been set.
At line:1 char:22
+ Set-PSDebug -Strict; $NewVar
```

### Exempel 4: inaktivera fel söknings funktioner

Det här exemplet stänger av alla fel söknings funktioner och kör sedan ett skript som visar siffrorna 1, 2 och 3.

```powershell
Set-PSDebug -Off; foreach ($i in 1..3) {$i}
```

```Output
1
2
3
```

## PARAMETRAR

### -Av

Inaktiverar alla funktioner för fel sökning av skript.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: off
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### – Steg

Aktiverar skript stegning. Innan varje rad körs, kommer PowerShell att bli ombedd att stoppa, fortsätta eller ange en ny tolknings nivå för att kontrol lera status för skriptet.

Genom att ange **steg** parametern anges automatiskt spårnings nivån `1` .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: on
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### – Strikt

Anger att variabler måste tilldelas ett värde innan de refereras till i ett skript. Om en variabel refererar till innan ett värde tilldelas, returnerar PowerShell ett undantags fel. Detta motsvarar `Set-StrictMode -Version 1` . Mer information finns i [set-StrictMode](Set-StrictMode.md).

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: on
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -Spåra

Anger spårnings nivån för varje rad i ett skript. Varje rad spåras när den körs.

De acceptabla värdena för den här parametern är följande:

- 0: inaktivera skript spårning.
- 1: spåra skript rader när de körs.
- 2: spåra skript rader, variabel tilldelningar, funktions anrop och skript.

```yaml
Type: System.Int32
Parameter Sets: on
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Du kan inte pipeline-ininformation till denna cmdlet.

## UTDATA

### Inget

Denna cmdlet returnerar inga utdata.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[about_Debuggers](./About/about_Debuggers.md)

[Fel sökning – process](../Microsoft.PowerShell.Management/Debug-Process.md)

[Set-PSBreakpoint](../Microsoft.PowerShell.Utility/Set-PSBreakpoint.md)

[Set-StrictMode](Set-StrictMode.md)

[Skriv-debug](../Microsoft.PowerShell.Utility/Write-Debug.md)

