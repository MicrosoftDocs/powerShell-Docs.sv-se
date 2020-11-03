---
external help file: Microsoft.Windows.DSC.CoreConfProviders.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/update-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-DscConfiguration
ms.openlocfilehash: 13365902ab317a3daa41b9a951d5e2fa6e4f1b37
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264758"
---
# Update-DscConfiguration

## SAMMANFATTNING
Kontrollerar hämtnings servern för en uppdaterad konfiguration och tillämpar den.

## SYNTAX

### ComputerNameSet (standard)

```
Update-DscConfiguration [-Wait] [-JobName <String>] [[-ComputerName] <String[]>] [-Credential <PSCredential>]
 [-ThrottleLimit <Int32>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### CimSessionSet

```
Update-DscConfiguration [-Wait] [-JobName <String>] [-ThrottleLimit <Int32>] -CimSession <CimSession[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING
`Update-DscConfiguration`Cmdleten ansluter till en pull-server, laddar ned konfigurationen om den skiljer sig från vad som är aktuellt på noden och tillämpar sedan konfigurationen på datorn.

Den här cmdleten är endast tillgänglig som en del av den [samlade uppdateringen November 2014 för Windows RT 8,1, Windows 8,1 och Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) från Microsoft Support-biblioteket.

## EXEMPEL

### Exempel 1: uppdatera en konfiguration

```
PS C:\> Update-DscConfiguration -Wait -Verbose
```

När du har kört det här kommandot ansluter servern till den registrerade pull-tjänsten, laddar ned den senaste tilldelade konfigurationen och tillämpar den sedan.
Parametrarna-wait och-verbose är valfria.
När du arbetar interaktivt aktiverar de här parametrarna real tids feedback om förlopp och framgång eller haveri vid tillämpning av konfigurationen.

### Exempel 2: uppdatera en konfiguration genom att ansluta via en CIM-session

```
PS C:\> $Session = New-CimSession -ComputerName "Server01" -Credential ACCOUNTS\PattiFuller
PS C:\> Update-DscConfiguration -CimSession $Session -Wait
```

Det första kommandot skapar en CIM-session med hjälp av cmdleten **New-CimSession** och lagrar sedan **CimSession** -objektet i variabeln $session.
I kommandot uppmanas du att ange ett lösen ord.
För mer information ange `Get-Help New-CimSession`.

Det andra kommandot uppdaterar datorn som anges i **CimSession** som lagras i $session.
Kommandot anger parametern *wait* .
Konsolen accepterar inte ytterligare kommandon förrän det aktuella kommandot har slutförts.

## PARAMETRAR

### – CimSession
Kör cmdleten i en fjärran sluten session eller på en fjärrdator.
Ange ett dator namn eller ett sessionsobjekt, till exempel utdata från en [New-CimSession-](/powershell/module/cimcmdlets/new-cimsession) eller [Get-CimSession-](/powershell/module/cimcmdlets/get-cimsession) cmdlet.
Standardvärdet är den aktuella sessionen på den lokala datorn.

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: CimSessionSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ComputerName
Anger en matris med dator namn.
Cmdleten tillämpar konfigurations inställningarna på de datorer som parametern anger.

```yaml
Type: System.String[]
Parameter Sets: ComputerNameSet
Aliases: CN, ServerName

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Credential
Anger ett användar namn och lösen ord, som ett **PSCredential** -objekt, för mål datorn.
Om du vill hämta ett **PSCredential** -objekt använder du cmdleten Get-Credential.
För mer information ange `Get-Help Get-Credential`.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: ComputerNameSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – JobName
Anger ett eget namn för ett jobb.
Om du anger den här parametern körs cmdleten som ett jobb och den returnerar ett **jobb** objekt.

Som standard tilldelar Windows PowerShell namnet JobN där N är ett heltal.

Ange inte den här parametern om du anger parametern *wait* .

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

### – Vänta
Anger att cmdleten blockerar konsolen tills den Slutför alla konfigurations åtgärder.

Om du anger den här parametern ska du inte ange parametern *JobName* .

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

[Restore-DscConfiguration](Restore-DscConfiguration.md)

[Start-DscConfiguration](Start-DscConfiguration.md)

[Stop-DscConfiguration](Stop-DscConfiguration.md)

[Test-DscConfiguration](Test-DscConfiguration.md)
