---
external help file: Get-DscConfigurationStatus.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscConfigurationStatus
ms.openlocfilehash: 0d59ce58a70eab68441ea1fe6097bbdf7792a54f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266084"
---
# Get-DscConfigurationStatus

## SAMMANFATTNING
Hämtar information om slutförda konfigurations körningar.

## SYNTAX

```
Get-DscConfigurationStatus [-All] [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob]
 [<CommonParameters>]
```

## BESKRIVNING
Cmdlet **: en get-DscConfigurationStatus** hämtar detaljerad information om slutförda konfigurations körningar i systemet.
Som standard returnerar den information om den senaste konfigurations körningen.
Denna cmdlet är användbar för att hitta historisk information om konfigurations körningar, t. ex. När konfigurationerna kördes, status för körningarna, antalet resurser i konfigurationerna och vilka resurser som har lyckats eller misslyckats.

## EXEMPEL

### Exempel 1: Hämta information om den senaste konfigurations körningen

```
PS C:\> Get-DscConfigurationStatus
```

Det här kommandot hämtar information om den senaste konfigurations körningen.

### Exempel 2: Hämta information om alla konfigurationer

```
PS C:\> Get-DscConfigurationStatus -All
```

Det här kommandot hämtar information om alla konfigurationer som kördes på systemet, inklusive konsekvens kontroll av Windows PowerShell Desired State Configuration (DSC).

### Exempel 3: Hämta information om konfigurations körningen på en fjärrdator

```
PS C:\> Get-DscConfigurationStatus -CimSession "Server01"
```

Det här kommandot hämtar konfigurations körnings information för fjärrdatorn med namnet Server01.
Detta använder WSMan-transport för att ansluta till fjärrdatorn och kräver att den anslutna användaren är administratör på fjärrdatorn.

## PARAMETRAR

### – Alla
Anger att denna cmdlet hämtar information om all konfiguration som körs på datorn, inklusive konfigurations programmet och konsekvens kontrollen.

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
Ange ett dator namn eller ett sessionsobjekt, till exempel utdata från en [New-CimSession-](/powershell/module/cimcmdlets/new-cimsession) eller [Get-CimSession-](/powershell/module/cimcmdlets/get-cimsession) cmdlet.
Standardvärdet är den aktuella sessionen på den lokala datorn.

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

### CommonParameters
Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

## UTDATA

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Översikt över önskad tillstånds konfiguration i Windows PowerShell](/powershell/scripting/dsc/overview/dscforengineers)

[Get-DscConfiguration](Get-DscConfiguration.md)

[Get-DscLocalConfigurationManager](Get-DscLocalConfigurationManager.md)

[Restore-DscConfiguration](Restore-DscConfiguration.md)

[Start-DscConfiguration](Start-DscConfiguration.md)

[Test-DscConfiguration](Test-DscConfiguration.md)
