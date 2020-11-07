---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/unregister-pssessionconfiguration?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PSSessionConfiguration
ms.openlocfilehash: 842b30951f24b0cc4211ddf45892d9e430e2dc82
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347473"
---
# Unregister-PSSessionConfiguration

## SAMMANFATTNING
Tar bort registrerade sessionsbaserade från datorn.

## SYNTAX

```
Unregister-PSSessionConfiguration [-Name] <String> [-Force] [-NoServiceRestart] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESKRIVNING

`Unregister-PSSessionConfiguration`Cmdleten tar bort registrerade sessionsbaserade från datorn. Denna cmdlet är utformad för att system administratörer ska kunna hantera konfigurationer för anpassade sessioner för användare.

För att ändringen ska börja gälla `Unregister-PSSessionConfiguration` startar om **WinRM** -tjänsten. För att förhindra omstarten anger du parametern **NoServiceRestart** .

Om du av misstag tar bort standard konfigurationerna för **Microsoft. PowerShell** eller **Microsoft. PowerShell32** använder du `Enable-PSRemoting` cmdleten för att återställa dem. Mer information finns i [about_Session_Configurations](About/about_Session_Configurations.md).

## EXEMPEL

### Exempel 1: ta bort en konfiguration av sessionen

I det här exemplet tas konfigurationen för **MaintenanceShell** -sessionen bort från datorn.

```powershell
Unregister-PSSessionConfiguration -Name "MaintenanceShell"
```

### Exempel 2: ta bort en sessions konfiguration och starta om WinRM-tjänsten

I det här exemplet tar vi bort **MaintenanceShell** -konfigurationen och startar om WinRM-tjänsten. Parametern **Force** undertrycker alla användar meddelanden för att starta om **WinRM** -tjänsten utan att fråga.

```powershell
Unregister-PSSessionConfiguration -Name MaintenanceShell -Force
```

### Exempel 3: ta bort alla konfigurationer för sessioner

I det här exemplet visas två sätt att ta bort alla sessionsinställningar på datorn. Båda kommandona har samma resultat och kan användas utbytbart.

```
Unregister-PSSessionConfiguration -Name *
Get-PSSessionConfiguration -Name * | Unregister-PSSessionConfiguration
```

### Exempel 4: avregistrera utan omstart

Det här exemplet visar effekterna av att använda parametern **NoServiceRestart** för att förhindra en omstart av tjänsten som skulle störa eventuella sessioner på datorn.

```
PS> Unregister-PSSessionConfiguration -Name "MaintenanceShell" -NoServiceRestart
PS> Get-PSSessionConfiguration -Name "MaintenanceShell"

Get-PSSessionConfiguration -Name MaintenanceShell : No Session Configuration matches criteria "MaintenanceShell".
+ CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
+ FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException

PS> New-PSSession -ConfigurationName "MaintenanceShell"

Id Name      ComputerName    State    Configuration         Availability
-- ----      ------------    -----    -------------         ------------
1 Session1  localhost       Opened   MaintenanceShell      Available

PS> Restart-Service winrm
PS> New-PSSession -ConfigurationName MaintenanceShell

[localhost] Connecting to remote server failed with the following error message :
 The WS-Management service cannot process the request.
 The resource URI (http://schemas.microsoft.com/powershell/MaintenanceShell) was not found in the WS-Management catalog.
 The catalog contains the metadata that describes resources, or logical endpoints.
 For more information, see the about_Remote_Troubleshooting Help topic.
 + CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [], PSRemotingTransportException
 + FullyQualifiedErrorId : PSSessionOpenFailed
```

`Unregister-PSSessionConfiguration`Konfiguration av **MaintenanceShell** -sessionen tas bort.
Men eftersom kommandot använder parametern **NoServiceRestart** startas inte **WinRM** -tjänsten om och ändringen är inte helt effektiv.

Sedan försöker du `Get-PSSessionConfiguration` Hämta **MaintenanceShell** -sessionen. Eftersom sessionen har tagits bort från WS-Management resurs tabell `Get-PSSessionConfiguration` kan den inte returnera den.

`New-PSSession`Cmdleten skapar en session med hjälp av **MaintenanceShell** -konfigurationen. Kommandot lyckades. Därefter startar vi om **WinRM** -tjänsten.

Slutligen `New-PSSession` försöker cmdleten skapa en session som använder **MaintenanceShell** -konfigurationen. Den här gången Miss lyckas sessionen eftersom **MaintenanceShell** -konfigurationen togs bort när WinRM-tjänsten startades om.

## PARAMETRAR

### -Force

Anger att cmdleten inte ber dig om bekräftelse och startar om **WinRM** -tjänsten utan att du behöver ange något. Att starta om tjänsten gör att konfigurations ändringen träder i kraft.

Om du vill förhindra en omstart och ignorera omstarts meddelandet använder du parametern **NoServiceRestart** .

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

### -Name

Anger namnen på de sessionsinställningar som ska tas bort. Ange ett konfigurations namn för sessionen eller ett namn mönster för konfigurationen. Jokertecken är tillåtna. Den här parametern är obligatorisk.

Du kan också skicka en session med konfigurationer till `Unregister-PSSessionConfiguration` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -NoServiceRestart

Anger att denna cmdlet inte startar om **WinRM** -tjänsten och förhindrar uppmaningen att starta om tjänsten.

När du kör ett `Unregister-PSSessionConfiguration` kommando uppmanas du som standard att starta om **WinRM** -tjänsten för att ändringen ska börja gälla. Innan **WinRM** -tjänsten har startats om kan användarna fortfarande använda den oregistrerade sessionen, trots att `Get-PSSessionConfiguration` den inte hittar den.

Om du vill starta om **WinRM** -tjänsten utan att begära det anger du parametern **Force** . Om du vill starta om **WinRM** -tjänsten manuellt använder du `Restart-Service` cmdleten.

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

### Microsoft. PowerShell. commands. PSSessionConfigurationCommands # PSSessionConfiguration

Du kan skicka vidare ett konfigurations objekt `Get-PSSessionConfiguration` för sessionen från till denna cmdlet.

## UTDATA

### Inget

Denna cmdlet returnerar inga objekt.

## ANTECKNINGAR

Den här cmdleten är endast tillgänglig på Windows-plattformar.

Om du vill köra denna cmdlet måste du starta PowerShell med alternativet **Kör som administratör** .

## RELATERADE LÄNKAR

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Aktivera – PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[New-PSSessionOption](New-PSSessionOption.md)

[Registrera – PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Avregistrera-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan-Provider](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)
