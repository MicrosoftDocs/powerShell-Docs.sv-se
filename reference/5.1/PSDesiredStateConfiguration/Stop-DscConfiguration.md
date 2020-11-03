---
external help file: Stop-DscConfiguration.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 08/19/2019
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/stop-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-DscConfiguration
ms.openlocfilehash: 93c8585ae948dfa360a2ae8e2563670de8fd6e93
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264777"
---
# Stop-DscConfiguration

## SAMMANFATTNING
Stoppar ett konfigurations jobb som kör.

## SYNTAX

### Alla

```
Stop-DscConfiguration [-Force] [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Stop-DscConfiguration`Cmdleten stoppar ett konfigurations jobb som kör. Ange vilka datorer som denna cmdlet gäller med hjälp av Common Information Model (CIM)-sessioner. Om inget konfigurations jobb körs returnerar denna cmdlet ett varnings meddelande.

`Stop-DscConfiguration` är bara tillgängligt som en del av den [samlade uppdateringen November 2014 för Windows RT 8,1, Windows 8,1 och Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) från Microsoft Support-biblioteket. Innan du använder den här cmdleten kan du läsa informationen i [Nyheter i Windows PowerShell 5,0](/powershell/scripting/whats-new/What-s-New-in-Windows-PowerShell-50)

## EXEMPEL

### Exempel 1: stoppa ett konfigurations jobb

I det här exemplet skapas en CIM-session med hjälp av `New-CimSession` cmdleten. **CimSession** -objektet används för att stoppa körningen av ett konfigurations jobb som körs.

```powershell
$Session = New-CimSession -ComputerName Server01 -Credential ACCOUNTS\User01
Stop-DscConfiguration -CimSession $Session
```

`New-CimSession` använder parametern **computername** för att ange Server01-datorn. Parametern **Credential** anger användar kontot. **CimSession** -objektet lagras i `$Session` variabeln. När kommandot körs uppmanas du att ange användar kontots lösen ord.

`Stop-DscConfiguration` använder parametern **CimSession** och objektet som är lagrat i `$Session` för att stoppa konfigurations jobbet.

## PARAMETRAR

### – AsJob

Anger att denna cmdlet kör kommandot som ett bakgrunds jobb. Mer information om PowerShell-bakgrunds jobb finns i [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) och [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md).

Om du vill använda parametern **AsJob** måste lokala datorer och fjärrdatorer konfigureras för fjärr kommunikation. I Windows Vista och senare versioner av operativ systemet Windows måste du öppna PowerShell med alternativet **Kör som administratör** . Mer information finns i [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).

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

### – CimSession

Kör cmdleten i en fjärran sluten session eller på en fjärrdator. Ange ett dator namn eller ett sessionsobjekt, till exempel utdata från `New-CimSession` eller `Get-CimSession` .

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

### -Confirm

`Stop-DscConfiguration` har inte stöd för **Confirm** -parametern. Om parametern **Confirm** används visas ett fel.

För PowerShell-cmdletar som har stöd för **Bekräfta** kan du med hjälp av parametern fråga dig om du vill verifiera innan ett kommando körs.

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

### -Force

Tvingar kommandot att köras utan att fråga användaren om bekräftelse.

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

### -ThrottleLimit

Anger det maximala antalet samtidiga åtgärder som kan upprättas för att köra cmdleten.

Om den här parametern utelämnas eller värdet `0` anges, beräknar PowerShell en optimal begränsnings gräns baserat på antalet CIM-cmdletar som körs på datorn. Begränsnings gränsen gäller endast för den aktuella cmdleten, inte sessionen eller till datorn.

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

### Inget

## UTDATA

### Inget

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Get-CimSession](../CimCmdlets/Get-CimSession.md)

[Get-DscConfiguration](Get-DscConfiguration.md)

[Get-DscConfigurationStatus](Get-DscConfigurationStatus.md)

[New-CimSession](../CimCmdlets/New-CimSession.md)

[Restore-DscConfiguration](Restore-DscConfiguration.md)

[Start-DscConfiguration](Start-DscConfiguration.md)

[Test-DscConfiguration](Test-DscConfiguration.md)

[Uppdatera – DscConfiguration](Update-DscConfiguration.md)

[Översikt över önskad tillstånds konfiguration i Windows PowerShell](/powershell/scripting/dsc/overview/overview)
