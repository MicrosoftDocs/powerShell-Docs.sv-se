---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-pssessionconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSSessionConfiguration
ms.openlocfilehash: 978f42174d211d1ceaf7a19d4a348e1bbcaa270b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263672"
---
# Disable-PSSessionConfiguration

## SAMMANFATTNING
Inaktiverar nodkonfigurationer på den lokala datorn.

## SYNTAX

```
Disable-PSSessionConfiguration [[-Name] <String[]>] [-Force] [-NoServiceRestart] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESKRIVNING

`Disable-PSSessionConfiguration`Cmdleten inaktiverar sessionsinställningar på den lokala datorn, vilket hindrar alla användare från att använda sessionens konfigurationer för att skapa en **PSSessions** (User Managed sessions) på den lokala datorn. Det här är en avancerad cmdlet som är avsedd att användas av system administratörer för att hantera konfigurationer för anpassade sessioner för sina användare.

Från och med PowerShell 3,0 `Disable-PSSessionConfiguration` ställer cmdleten in den **aktiverade** inställningen för session konfiguration ( `WSMan:\localhost\Plugins\<SessionConfiguration>\Enabled` ) till falskt.

I PowerShell 2,0 `Disable-PSSessionConfiguration` lägger cmdleten till en **Deny_All** post till säkerhets beskrivningen för en eller flera registrerade sessioner.

Utan parametrar `Disable-PSSessionConfiguration` inaktiverar **Microsoft. PowerShell** -konfigurationen, standard konfigurationen som används för sessioner. Om användaren inte anger en annan konfiguration, förhindras både lokala och fjärranslutna användare från att skapa sessioner som ansluter till datorn.

Om du vill inaktivera alla sessionsinställningar på datorn använder du `Disable-PSRemoting` .

## EXEMPEL

### Exempel 1: inaktivera standard konfigurationen

I det här exemplet inaktive ras konfigurationen av Microsoft. PowerShell-sessionen.

```powershell
Disable-PSSessionConfiguration
```

### Exempel 2: inaktivera alla registrerade sessionsbaserade

I det här exemplet inaktive ras alla registrerade sessionsbaserade på datorn.

```powershell
Disable-PSSessionConfiguration -Name *
```

### Exempel 3: inaktivera sessionsbaserade efter namn

I det här exemplet inaktive ras alla sessionsinställningar som har namn som börjar med Microsoft. Parametern **Force** förhindrar alla användar meddelanden från cmdleten.

```powershell
Disable-PSSessionConfiguration -Name Microsoft* -Force
```

### Exempel 4: inaktivera sessionsbaserade med hjälp av pipelinen

I det här exemplet inaktive ras **MaintenanceShell** och **AdminShell** . Pipeline-operatorn (|) skickar resultatet från en `Get-PSSessionConfiguration` till `Disable-PSSessionConfiguration` .

```powershell
Get-PSSessionConfiguration -Name MaintenanceShell, AdminShell | Disable-PSSessionConfiguration
```

### Exempel 5: effekterna av att inaktivera en sessions konfiguration

I det här exemplet visas behörigheterna före och efter körningen `Disable-PSSessionConfiguration` och effekterna av att inaktivera en konfiguration av sessionen.

```
PS> Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Name                   Permission
----                   ----------
MaintenanceShell       BUILTIN\Administrators AccessAllowed
microsoft.powershell   BUILTIN\Administrators AccessAllowed
microsoft.powershell32 BUILTIN\Administrators AccessAllowed

PS> Disable-PSSessionConfiguration -Name MaintenanceShell -Force
PS> Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Name                   Permission
----                   ----------
MaintenanceShell       Everyone AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell   BUILTIN\Administrators AccessAllowed
microsoft.powershell32 BUILTIN\Administrators AccessAllowed

PS> New-PSSession -ComputerName localhost -ConfigurationName MaintenanceShell

[localhost] Connecting to remote server failed with the following error message : Access is denied.
For more information, see the about_Remote_Troubleshooting Help topic.
+ CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [], PSRemotingTransportException
+ FullyQualifiedErrorId : PSSessionOpenFailed
```

> [!NOTE]
> Att inaktivera konfigurationen förhindrar inte att du ändrar konfigurationen med hjälp av `Set-PSSessionConfiguration` cmdleten. Den förhindrar bara användning av konfigurationen.

## PARAMETRAR

### -Force

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

### -Name

Anger en matris med namn på de sessionsinställningar som ska inaktive ras. Ange ett eller flera konfigurations namn. Jokertecken är tillåtna. Du kan också skicka en sträng som innehåller ett konfigurations namn eller ett konfigurations objekt för session till `Disable-PSSessionConfiguration` .

Om du utelämnar den här parametern `Disable-PSSessionConfiguration` inaktive ras konfigurationen av Microsoft. PowerShell-sessionen.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -NoServiceRestart

Används för att förhindra omstart av WSMan-tjänsten. Du behöver inte starta om tjänsten för att inaktivera konfigurationen.

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

### Microsoft. PowerShell. commands. PSSessionConfigurationCommands # PSSessionConfiguration, system. String

Du kan skicka ett konfigurations objekt för en session eller en sträng som innehåller namnet på en sessions konfiguration till denna cmdlet.

## UTDATA

### Inget

Denna cmdlet returnerar inga objekt.

## ANTECKNINGAR

Om du vill köra denna cmdlet måste du starta PowerShell med alternativet **Kör som administratör** .

## RELATERADE LÄNKAR

[Aktivera – PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[New-PSSessionConfigurationFile](New-PSSessionConfigurationFile.md)

[Registrera – PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Test-PSSessionConfigurationFile](Test-PSSessionConfigurationFile.md)

[Avregistrera-PSSessionConfiguration](Unregister-PSSessionConfiguration.md)

[WSMan-Provider](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Session_Configurations](About/about_Session_Configurations.md)

[about_Session_Configuration_Files](About/about_Session_Configuration_Files.md)
