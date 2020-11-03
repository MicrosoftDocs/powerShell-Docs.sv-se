---
external help file: Remove-DscConfigurationDocument.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-DscConfigurationDocument
ms.openlocfilehash: d3e9b15dfeea94921503247adc08b291eed9d7d7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266036"
---
# Remove-DscConfigurationDocument

## SAMMANFATTNING
Tar bort ett konfigurations dokument från DSC-konfigurationsdatabasen.

## SYNTAX

```
Remove-DscConfigurationDocument -Stage <Stage> [-Force] [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>]
 [-AsJob] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING
`Remove-DscConfigurationDocument`Cmdleten tar bort ett konfigurations dokument (MOF-fil) från konfigurations lagringen för Desired State Configuration (DSC) i Windows PowerShell.
Under konfigurationen `Start-DscConfiguration` kopierar cmdleten en. MOF-fil till en mapp på mål datorn.
Denna cmdlet tar bort konfigurations dokumentet och gör ytterligare rensning.

Den här cmdleten är endast tillgänglig som en del av den [samlade uppdateringen November 2014 för Windows RT 8,1, Windows 8,1 och Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) från Microsoft Support-biblioteket.

## EXEMPEL

### Exempel 1: ta bort det aktuella konfigurations dokumentet

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Remove-DscConfigurationDocument -Stage Current -CimSession $Session
```

Det första kommandot skapar en CIM-session med hjälp av cmdleten **New-CimSession** och lagrar sedan **CimSession** -objektet i variabeln $session.
I kommandot uppmanas du att ange ett lösen ord.
För mer information ange `Get-Help New-CimSession`.

Det andra kommandot tar bort det aktuella konfigurations dokumentet för den dator som anges i **CimSession** som lagras i $session.

## PARAMETRAR

### – AsJob
Anger att denna cmdlet kör kommandot som ett bakgrunds jobb.

Om du anger parametern *AsJob* , returnerar kommandot ett objekt som representerar jobbet och visar sedan kommando tolken.
Du kan fortsätta att arbeta i sessionen tills jobbet har slutförts.
Jobbet skapas på den lokala datorn och resultaten från fjärrdatorer returneras automatiskt till den lokala datorn.
Använd jobb-cmdletar för att hantera jobbet.
Använd Receive-Job-cmdleten för att hämta jobb resultatet.

Om du vill använda den här parametern måste lokala och fjärranslutna datorer konfigureras för fjärr kommunikation och i Windows Vista och senare versioner av Windows operativ system måste du öppna Windows PowerShell med alternativet Kör som administratör.
Mer information finns i [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).

Mer information om bakgrunds jobb i Windows PowerShell finns i [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) och [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md).

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

### -Force
Anger att den här cmdleten stoppar det pågående konfigurations jobbet innan det tar bort konfigurations dokumentet.
Tvingar kommandot att köras utan att fråga användaren om bekräftelse.

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

### – Steg
Anger vilket konfigurations dokument som ska tas bort.
Du kan ange flera dokument.
De acceptabla värdena för den här parametern är:

- Tillfället.
Ta bort konfigurations dokumentet som beskriver systemets aktuella tillstånd.
- Väntande.
Ta bort konfigurations dokumentet som beskriver systemets väntande tillstånd.
- Ursprungliga.
Ta bort konfigurations dokumentet som beskriver systemets tidigare tillstånd.

```yaml
Type: Microsoft.PowerShell.Cmdletization.GeneratedTypes.RemoveDscConfigurationDocument.Stage
Parameter Sets: (All)
Aliases:
Accepted values: Current, Pending, Previous

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ThrottleLimit
Anger det maximala antalet samtidiga åtgärder som kan upprättas för att köra cmdleten.
Om den här parametern utelämnas eller värdet `0` anges, beräknar Windows PowerShell en optimal begränsnings gräns för cmdleten baserat på antalet CIM-cmdletar som körs på datorn.
Begränsnings gränsen gäller endast för den aktuella cmdleten, inte sessionen eller till datorn.

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

### Inget

## UTDATA

### Inget

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Översikt över önskad tillstånds konfiguration i Windows PowerShell](/powershell/scripting/dsc/overview/dscforengineers)

[Get-DscConfiguration](Get-DscConfiguration.md)

[Get-DscConfigurationStatus](Get-DscConfigurationStatus.md)
