---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/reset-computermachinepassword?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Reset-ComputerMachinePassword
ms.openlocfilehash: 1484bc83b9503ce43420b833a1b78b3c4215d98a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265431"
---
# Reset-ComputerMachinePassword

## SAMMANFATTNING
Återställer dator kontots lösen ord för datorn.

## SYNTAX

```
Reset-ComputerMachinePassword [-Server <String>] [-Credential <PSCredential>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESKRIVNING
Cmdleten **Reset-ComputerMachinePassword** ändrar lösen ordet för det dator konto som datorerna använder för att autentisera till domän kontrol Lanterna i domänen.
Du kan använda den för att återställa lösen ordet för den lokala datorn.

## EXEMPEL

### Exempel 1: Återställ lösen ordet för den lokala datorn

```
PS C:\> Reset-ComputerMachinePassword
```

Det här kommandot återställer dator lösen ordet för den lokala datorn.
Kommandot körs med autentiseringsuppgifterna för den aktuella användaren.

### Exempel 2: återställa lösen ordet för den lokala datorn med hjälp av en angiven domänkontrollant

```
PS C:\> Reset-ComputerMachinePassword -Server "DC01" -Credential Domain01\Admin01
```

Det här kommandot återställer dator lösen ordet för den lokala datorn med hjälp av DC01-domänkontrollanten.
Den använder parametern *Credential* för att ange ett användar konto som har behörighet att återställa ett dator lösen ord i domänen.

### Exempel 3: återställa lösen ordet på en fjärrdator

```
$cred = Get-Credential
PS C:\> Invoke-Command -ComputerName "Server01" -ScriptBlock {Reset-ComputerMachinePassword -Credential $using:cred}
```

Det här kommandot använder cmdleten Invoke-Command för att köra ett **Reset-ComputerMachinePassword-** kommando på Server01-fjärrdatorn.

Mer information om fjärrkommandon i Windows PowerShell finns about_Remote och **Invoke-Command**.

## PARAMETRAR

### -Credential
Anger ett användar konto som har behörighet att utföra den här åtgärden.
Standard är den aktuella användaren.

Ange ett användar namn, till exempel user01 eller Domain01\User01, eller ange ett **PSCredential** -objekt, till exempel ett som genereras av Get-Credential cmdlet.
Om du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.

Den här parametern introducerades i Windows PowerShell 3,0.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Server
Anger namnet på en domänkontrollant som ska användas när denna cmdlet anger lösen ordet för dator kontot.

Den här parametern är valfri.
Om du utelämnar den här parametern väljs en domänkontrollant för att betjäna kommandot.

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
Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### Inget
Denna cmdlet genererar inga utdata.

## ANTECKNINGAR

## RELATERADE LÄNKAR

## RELATERADE LÄNKAR
