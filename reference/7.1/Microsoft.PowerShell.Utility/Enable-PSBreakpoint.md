---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/09/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/enable-psbreakpoint?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSBreakpoint
ms.openlocfilehash: 547739d6482e86bc558245bc5c5f04eddcfe9614
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266445"
---
# Enable-PSBreakpoint

## SAMMANFATTNING
Aktiverar Bryt punkterna i den aktuella konsolen.

## SYNTAX

### ID (standard)

```
Enable-PSBreakpoint [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Brytning

```
Enable-PSBreakpoint [-PassThru] [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESKRIVNING

`Enable-PSBreakpoint`Cmdleten aktiverar inaktiverade Bryt punkter igen. Du kan använda den för att aktivera alla Bryt punkter eller vissa Bryt punkter genom att tillhandahålla Bryt punkts objekt eller ID: n.

En Bryt punkt är en punkt i ett skript där körningen stoppas tillfälligt så att du kan granska status för skriptet. Nyligen skapade Bryt punkter aktive ras automatiskt, men kan inaktive ras med `Disable-PSBreakpoint` .

Den här cmdleten ändrar tekniskt värde för egenskapen **Enabled** för ett Bryt punkts objekt till **Sant**.

`Enable-PSBreakpoint` är en av flera cmdletar utformade för fel sökning av PowerShell-skript. Mer information om PowerShell-felsökaren finns i [about_Debuggers](../Microsoft.PowerShell.Core/About/about_Debuggers.md).

## EXEMPEL

### Exempel 1: Aktivera alla Bryt punkter

Det här exemplet aktiverar alla Bryt punkter i den aktuella sessionen.

```powershell
Get-PSBreakpoint | Enable-PSBreakpoint
```

Med hjälp av alias kan det här exemplet vara förkortat som `gbp | ebp` .

### Exempel 2: Aktivera Bryt punkter efter ID

Det här exemplet aktiverar flera Bryt punkter med deras Bryt punkts-ID.

```powershell
Enable-PSBreakpoint -Id 0, 1, 5
```

### Exempel 3: Aktivera en inaktive rad Bryt punkt

I det här exemplet återaktiveras en Bryt punkt som har inaktiverats.

```powershell
$B = Set-PSBreakpoint -Script "sample.ps1" -Variable Name -PassThru
$B | Enable-PSBreakpoint -PassThru
```

```Output
AccessMode : Write
Variable   : Name
Action     :
Enabled    : False
HitCount   : 0
Id         : 0
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1

AccessMode : Write
Variable   : Name
Action     :
Enabled    : True
HitCount   : 0
Id         : 0
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

`Set-PSBreakpoint` skapar en Bryt punkt för **Name** -variabeln i `Sample.ps1` skriptet som sparar objektet Bryt punkt i `$B` variabeln. Parametern **Passthru** visar värdet för egenskapen **Enabled** för Bryt punkten som **false**.

`Enable-PSBreakpoint` aktiverar Bryt punkten igen. Igen, med parametern **Passthru** , ser vi att värdet för egenskapen **Enabled** är **True**.

### Exempel 4: Aktivera Bryt punkter med en variabel

Det här exemplet aktiverar en uppsättning Bryt punkter med hjälp av Bryt punkts objekt.

```powershell
$B = Get-PSBreakpoint -Id 3, 5
Enable-PSBreakpoint -Breakpoint $B
```

`Get-PSBreakpoint` hämtar Bryt punkterna och sparar dem i `$B` variabeln. Med hjälp av **Bryt punkts** parametern kan `Enable-PSBreakpoint` du aktivera Bryt punkterna.

Det här exemplet motsvarar att köra `Enable-PSBreakpoint -Id 3, 5` .

## PARAMETRAR

### – Bryt punkt

Anger Bryt punkter som ska aktive ras. Ange en variabel som innehåller Bryt punkter eller ett kommando som hämtar Bryt punkts objekt, till exempel `Get-PSBreakpoint` . Du kan också skicka Bryt punkts objekt till `Enable-PSBreakpoint` .

```yaml
Type: System.Management.Automation.Breakpoint[]
Parameter Sets: Breakpoint
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ID

Anger **ID-** numren för de Bryt punkter som ska aktive ras. Standardvärdet är alla Bryt punkter.
Ange **ID: t** efter nummer eller i en variabel. Du kan inte skicka pipe **-ID-** nummer till `Enable-PSBreakpoint` . Använd cmdleten för att hitta **ID: t** för en Bryt punkt `Get-PSBreakpoint` .

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – PassThru

Returnerar ett objekt som representerar den Bryt punkt som Aktiver ATS. Som standard genererar denna cmdlet inga utdata.

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

### System. Management. Automation. Bryt punkt

Du kan skicka ett Bryt punkts objekt till `Enable-PSBreakpoint` .

## UTDATA

### Ingen eller system. Management. Automation. Bryt punkt

När du använder parametern **Passthru** `Enable-PSBreakpoint` returnerar ett Bryt punkts objekt som representerar den Bryt punkten som har Aktiver ATS. Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

- `Enable-PSBreakpoint`Cmdleten genererar inget fel om du försöker aktivera en Bryt punkt som redan är aktive rad. Det innebär att du kan aktivera alla Bryt punkter utan fel, även när bara några är inaktiverade.

- Bryt punkter aktive ras när du skapar dem med hjälp av `Set-PSBreakpoint` cmdleten. Du behöver inte aktivera nyligen skapade Bryt punkter.

## RELATERADE LÄNKAR

[Disable-PSBreakpoint](Disable-PSBreakpoint.md)

[Get-PSBreakpoint](Get-PSBreakpoint.md)

[Get-PSCallStack](Get-PSCallStack.md)

[Remove-PSBreakpoint](Remove-PSBreakpoint.md)

[Set-PSBreakpoint](Set-PSBreakpoint.md)

