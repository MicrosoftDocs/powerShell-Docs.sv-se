---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 10/02/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/set-wsmanquickconfig?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WSManQuickConfig
ms.openlocfilehash: 5b22eb9334510267d9c4e3757b39810cfdba1fd3
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/21/2020
ms.locfileid: "93273086"
---
# Set-WSManQuickConfig

## SAMMANFATTNING
Konfigurerar den lokala datorn för fjärrhantering.

## SYNTAX

### Alla

```
Set-WSManQuickConfig [-UseSSL] [-Force] [-SkipNetworkProfileCheck] [<CommonParameters>]
```

## BESKRIVNING

`Set-WSManQuickConfig`Cmdleten konfigurerar datorn att ta emot PowerShell-fjärrkommandon som skickas med hjälp av WS-Management-tekniken (Web Services for Management).

`Set-WSManQuickConfig` utför följande åtgärder:

- Kontrollerar om WinRM-tjänsten körs. Om WinRM-tjänsten inte körs startas tjänsten.
- Anger start typen för WinRM-tjänsten till automatisk.
- Skapar en lyssnare som accepterar begär Anden på alla IP-adresser. Standard transporten är **http**.
- Aktiverar ett brand Väggs undantag för WinRM-trafik.

`Set-WSManQuickConfig`Starta PowerShell med alternativet **Kör som administratör** för att köra.

## EXEMPEL

### Exempel 1: aktivera fjärrhantering av den lokala datorn via HTTP

I det här exemplet anges konfigurationen som krävs för att aktivera fjärrhantering av den lokala datorn. Som standard skapar det här kommandot en WS-Management lyssnare på **http**.

```powershell
Set-WSManQuickConfig
```

### Exempel 2: aktivera fjärrhantering av den lokala datorn via HTTPS

I det här exemplet anges konfigurationen som krävs för att aktivera fjärrhantering av den lokala datorn. Parametern **UseSSL** anger att **https** används för att kommunicera med datorn.

```powershell
Set-WSManQuickConfig -UseSSL
```

> [!NOTE]
> **Https** kräver manuell konfiguration. Mer information finns i Beskrivning av **UseSSL** -parametern.

## PARAMETRAR

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

### -SkipNetworkProfileCheck

Konfigurerar Windows-klientversioner för fjärr kommunikation när datorn finns i ett offentligt nätverk. Med den här parametern kan du använda en brand Väggs regel för offentliga nätverk som endast tillåter fjärråtkomst från datorer i samma lokala undernät.

Den här parametern har ingen påverkan på Server versioner av Windows, som standard har en brand Väggs regel för lokalt undernät för offentliga nätverk. Om den lokala brand Väggs regeln är inaktive rad på Server versionen av Windows återaktiverar `Enable-PSRemoting` den, oavsett den här parameterns värde.

Om du vill ta bort den lokala under näts begränsningen och aktivera fjärråtkomst från alla platser i offentliga nätverk använder du `Set-NetFirewallRule` cmdleten i modulen **netsecurity** .

Den här parametern introducerades i PowerShell 3,0.

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

### -UseSSL

Anger att Secure Sockets Layer-protokollet (SSL) används för att upprätta en anslutning till fjärrdatorn. Som standard används inte SSL.

WS-Management krypterar allt PowerShell-innehåll som överförs via nätverket. Med parametern **UseSSL** kan du ange ytterligare skydd av https i stället för http. Om du använder den här parametern och SSL inte är tillgängligt på porten som används för anslutningen, Miss lyckas kommandot.

**Https** kräver manuell konfiguration av WinRM-och brand Väggs regler. Mer information finns i [så här gör du för att: Konfigurera WINRM för https](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https).

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

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Denna cmdlet accepterar inte några indatatyper.

## UTDATA

### Inget

Denna cmdlet genererar inga utdata.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Anslut-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

[Koppla från-WSMan](Disconnect-WSMan.md)

[Enable-PSRemoting](../Microsoft.PowerShell.Core/Enable-PSRemoting.md)

[Aktivera – WSManCredSSP](Enable-WSManCredSSP.md)

[Get-WSManCredSSP](Get-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[Gör så här: Konfigurera WINRM för HTTPS](https://support.microsoft.com/help/2019527/how-to-configure-winrm-for-https)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-PSSession](../Microsoft.PowerShell.Core/New-PSSession.md)

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Test-WSMan](Test-WSMan.md)
