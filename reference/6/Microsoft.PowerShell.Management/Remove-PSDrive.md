---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-psdrive?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSDrive
ms.openlocfilehash: 6f34e670a29ee65e4a37314472f89c463f0a49ab
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267249"
---
# Remove-PSDrive

## SAMMANFATTNING
Tar bort tillfälliga PowerShell-enheter och kopplar från mappade nätverks enheter.

## SYNTAX

### Namn (standard)

```
Remove-PSDrive [-Name] <String[]> [-PSProvider <String[]>] [-Scope <String>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralName

```
Remove-PSDrive [-LiteralName] <String[]> [-PSProvider <String[]>] [-Scope <String>] [-Force]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Remove-PSDrive`Cmdleten tar bort temporära PowerShell-enheter som har skapats med hjälp av `New-PSDrive` cmdleten.

Från och med Windows PowerShell 3,0 `Remove-PSDrive` kopplar även mappade nätverks enheter, inklusive, men inte begränsat till, enheter som skapats med hjälp av `Persist` parametern för `New-PSDrive` .

`Remove-PSDrive` Det går inte att ta bort fysiska eller logiska enheter i Windows.

Från och med Windows PowerShell 3,0 lägger PowerShell automatiskt till en PSDrive i fil systemet som representerar den nya enheten när en extern enhet ansluts till datorn.
Du behöver inte starta om PowerShell.
När en extern enhet kopplas bort från datorn tar PowerShell automatiskt bort den PSDrive som representerar den borttagna enheten.

## EXEMPEL

### Exempel 1: ta bort en fil system enhet

Det här kommandot tar bort en temporär fil system enhet med namnet "SMP".

```powershell
Remove-PSDrive -Name smp
```

### Exempel 2: ta bort mappade nätverks enheter

Det här kommandot använder `Remove-PSDrive` för att koppla från X: och S: mappade nätverks enheter.

```powershell
Get-PSDrive X, S | Remove-PSDrive
```

## PARAMETRAR

### -Force

Tar bort den aktuella PowerShell-enheten.

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

### -LiteralName

Anger namnet på enheten.

Värdet för **LiteralName** används precis som skrivet.
Inga tecken tolkas som jokertecken.
Om namnet innehåller escape-tecken omger du det med enkla citat tecken (').
Enkla citat tecken instruerar PowerShell att inte tolka några tecken som escape-sekvenser.

```yaml
Type: System.String[]
Parameter Sets: LiteralName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Name

Anger namnen på de enheter som ska tas bort.
Skriv inget kolon (:) efter enhets namnet.

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -PSProvider

Anger en matris med **PSProvider** -objekt.
Den här cmdleten tar bort och kopplar från alla enheter som är associerade med den angivna PowerShell-providern.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – Omfattning

Anger ett omfång för enheten.
De acceptabla värdena för den här parametern är: globalt, lokalt och skript, eller ett tal i förhållande till det aktuella omfånget. Omfattnings nummer 0 till och med antalet omfattningar. Det aktuella omfångs numret är 0 och dess överordnade är 1.
Mer information finns i [about_Scopes](../Microsoft.PowerShell.Core/About/about_Scopes.md).

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Local
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

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### System.Management.Automation.PSDriveInfo

Du kan skicka vidare ett enhets objekt, till exempel ett från `Get-PSDrive` cmdlet: en, till `Remove-PSDrive` cmdlet: en.

## UTDATA

### Inget

Denna cmdlet returnerar inga utdata.

## ANTECKNINGAR

- `Remove-PSDrive`Cmdleten är utformad för att fungera med data som exponeras av en PowerShell-Provider. Om du vill visa en lista över providers i sessionen använder du `Get-PSProvider` cmdleten. Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).

## RELATERADE LÄNKAR

[Get-PSDrive](Get-PSDrive.md)

[New-PSDrive](New-PSDrive.md)

[about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md)
