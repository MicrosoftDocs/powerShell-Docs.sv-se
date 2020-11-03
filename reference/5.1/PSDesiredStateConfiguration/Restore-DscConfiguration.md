---
external help file: Restore-DSCConfiguration.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/restore-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Restore-DscConfiguration
ms.openlocfilehash: 823032f7665d9ec83faa59c37560510e049efdd2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266031"
---
# Restore-DscConfiguration

## SAMMANFATTNING
Återanvänder den tidigare konfigurationen för noden.

## SYNTAX

```
Restore-DscConfiguration [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESKRIVNING
**Restore-DscConfiguration-** cmdleten tillämpar den tidigare konfigurationen för noden, om det finns en tidigare konfiguration.
Ange datorer med hjälp av Common Information Model (CIM)-sessioner.
Om du inte anger en måldator återställer cmdleten konfigurationen av den lokala datorn.
Om det inte finns någon tidigare konfiguration för en viss nod, returnerar denna cmdlet ett fel meddelande.

Denna cmdlet stöder inte **Confirm** -parametern.

## EXEMPEL

### Exempel 1: Återställ konfigurationen för den lokala datorn

```
PS C:\> Restore-DscConfiguration
```

Det här kommandot återställer konfigurationen för den lokala datorn.

### Exempel 2: Återställa konfigurationen för en angiven dator

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Restore-DscConfiguration -CimSession $Session
```

I det här exemplet återställs konfigurationen på en dator som anges av en CIM-session.
I exemplet skapas en CIM-session för en dator med namnet Server01 för användning med cmdleten.
Du kan också skapa en matris med CIM-sessioner för att tillämpa cmdleten på flera angivna datorer.

Det första kommandot skapar en CIM-session med hjälp av cmdleten **New-CimSession** och lagrar sedan **CimSession** -objektet i variabeln $session.
I kommandot uppmanas du att ange ett lösen ord.
För mer information ange `Get-Help New-CimSession`.

Det andra kommandot återställer konfigurationen för de datorer som identifieras av de **CimSession** -objekt som lagras i variabeln $session, i det här fallet datorn med namnet Server01.

## PARAMETRAR

### – AsJob
Anger att denna cmdlet kör kommandot som ett bakgrunds jobb.

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

### – CimSession
Kör cmdleten i en fjärran sluten session eller på en fjärrdator.
Ange ett dator namn eller ett sessionsobjekt, till exempel utdata från en **New-CimSession-** eller **Get-CimSession-** cmdlet.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: (All)
Aliases: Session

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit
Anger det maximala antalet samtidiga åtgärder som kan upprättas för att köra cmdleten.

```yaml
Type: System.Int32
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

## UTDATA

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Översikt över önskad tillstånds konfiguration i Windows PowerShell](/powershell/scripting/dsc/overview/dscforengineers)

[Get-DscConfiguration](Get-DscConfiguration.md)

[Get-DscConfigurationStatus](Get-DscConfigurationStatus.md)

[Start-DscConfiguration](Start-DscConfiguration.md)

[Test-DscConfiguration](Test-DscConfiguration.md)
