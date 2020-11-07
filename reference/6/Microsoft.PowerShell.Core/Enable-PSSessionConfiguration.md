---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-pssessionconfiguration?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSSessionConfiguration
ms.openlocfilehash: df7f288f4ca609a6b53c9ba33d86ba73078f60eb
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94345450"
---
# Enable-PSSessionConfiguration

## SAMMANFATTNING
Aktiverar sessionsinställningar på den lokala datorn.

## SYNTAX

```
Enable-PSSessionConfiguration [[-Name] <String[]>] [-Force] [-SecurityDescriptorSddl <String>]
 [-SkipNetworkProfileCheck] [-NoServiceRestart] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Enable-PSSessionConfiguration`Cmdleten aktiverar registrerade sessionsinställningar som har inaktiverats, till exempel med hjälp av `Disable-PSSessionConfiguration` `Disable-PSRemoting` cmdletarna eller **AccessMode** -parametern för `Register-PSSessionConfiguration` . Det här är en avancerad cmdlet som är avsedd att användas av system administratörer för att hantera konfigurationer för anpassade sessioner för sina användare.

Utan parametrar `Enable-PSSessionConfiguration` aktiverar **Microsoft. PowerShell** -konfigurationen, som är den standard konfiguration som används för sessioner.

`Enable-PSSessionConfiguration` tar bort inställningen **Deny_All** från säkerhets beskrivningen för de berörda sessionerna, aktiverar den lyssnare som accepterar begär Anden på alla IP-adresser och startar om WinRM-tjänsten. Från och med PowerShell 3,0 `Enable-PSSessionConfiguration` anger även värdet för egenskapen **Enabled** för session Configuration ( `WSMan:\<computer>\PlugIn\<SessionConfigurationName>\Enabled` ) till true. Men `Enable-PSSessionConfiguration` tar inte bort eller ändrar inställningen för säkerhets beskrivningen **Network_Deny_All** ( `AccessMode=Local` ) som endast tillåter användare av den lokala datorn att använda den för att konfigurera sessionen.

## EXEMPEL

### Exempel 1: återaktivera Standardsessionen

I det här exemplet återaktiveras standardsessions konfigurationen för **Microsoft. PowerShell** på datorn.

```powershell
Enable-PSSessionConfiguration
```

### Exempel 2: återaktivera angivna sessioner

I det här exemplet återaktiveras **MaintenanceShell** -och **AdminShell** på datorn.

```powershell
Enable-PSSessionConfiguration -Name MaintenanceShell, AdminShell
```

### Exempel 3: återaktivera alla sessioner

I det här exemplet återaktiveras alla sessionsbaserade på datorn. Dessa kommandon är likvärdiga.
Därför kan du använda antingen.

```powershell
Enable-PSSessionConfiguration -Name *
Get-PSSessionConfiguration | Enable-PSSessionConfiguration
```

`Enable-PSSessionConfiguration` genererar inget fel om du aktiverar en sessionshantering som redan är aktive rad.

### Exempel 4: återaktivera en session och ange en ny säkerhets Beskrivning

I det här exemplet återaktiveras **MaintenanceShell** och en ny säkerhets beskrivning anges för konfigurationen.

```powershell
$sddl = "O:NSG:BAD:P(A;;GXGWGR;;;BA)(A;;GAGR;;;S-1-5-21-123456789-188441444-3100496)S:P"
Enable-PSSessionConfiguration -Name MaintenanceShell -SecurityDescriptorSDDL $sddl
```

## PARAMETRAR

### -Force

Anger att cmdleten inte ber dig om bekräftelse och startar om WinRM-tjänsten utan att du behöver ange något. Att starta om tjänsten gör att konfigurations ändringen träder i kraft.

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

Anger namnen på de sessionsinställningar som ska aktive ras. Ange ett eller flera konfigurations namn.
Jokertecken är tillåtna.

Du kan också skicka en sträng som innehåller ett konfigurations namn eller ett konfigurations objekt för session till `Enable-PSSessionConfiguration` .

Om du utelämnar den här parametern `Enable-PSSessionConfiguration` aktiverar **Microsoft. PowerShell** -sessionen.

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

Anger att cmdleten inte startar om tjänsten.

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

### -SecurityDescriptorSddl

Anger en säkerhets Beskrivning där denna cmdlet ersätter säkerhets beskrivningen i konfigurationen av sessionen.

Om du utelämnar den här parametern `Enable-PSSessionConfiguration` tar endast bort neka alla objekt från säkerhets beskrivningen.

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

### -SkipNetworkProfileCheck

Anger att denna cmdlet aktiverar sessionen när datorn finns i ett offentligt nätverk. Med den här parametern kan du använda en brand Väggs regel för offentliga nätverk som endast tillåter fjärråtkomst från datorer i samma lokala undernät. Som standard `Enable-PSSessionConfiguration` går det inte att utföra i ett offentligt nätverk.

Den här parametern är avsedd för klient versioner av Windows operativ system. Server versioner av Windows operativ system har en lokal brand Väggs regel för offentliga nätverk. Men om den lokala brand Väggs regeln är inaktive rad på en server version av Windows-operativsystemet, aktive ras den här parametern igen.

Om du vill ta bort den lokala under näts begränsningen och aktivera fjärråtkomst från alla platser i offentliga nätverk använder du `Set-NetFirewallRule` cmdleten i modulen netsecurity. Mer information finns i `Enable-PSRemoting`.

Den här parametern introducerades i PowerShell 3,0.

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

Den här cmdleten är endast tillgänglig på Windows-plattformar.

Om du vill använda denna cmdlet måste du starta PowerShell med alternativet **Kör som administratör** .

## RELATERADE LÄNKAR

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

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
