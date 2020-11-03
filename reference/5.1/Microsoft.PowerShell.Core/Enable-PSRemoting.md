---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-psremoting?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSRemoting
ms.openlocfilehash: 0c8c386ab376afde3d15fcd29b3f653b3f738f63
ms.sourcegitcommit: 0e0f45d0d8deb8c9088a4f4a32218edde052b686
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/17/2020
ms.locfileid: "93268065"
---
# Enable-PSRemoting

## SAMMANFATTNING
Konfigurerar datorn att ta emot fjärrkommandon.

## SYNTAX

```
Enable-PSRemoting [-Force] [-SkipNetworkProfileCheck] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Enable-PSRemoting`Cmdleten konfigurerar datorn att ta emot PowerShell-fjärrkommandon som skickas med hjälp av WS-Management teknik.

PowerShell-fjärrkommunikation är aktiverat som standard på Windows Server 2012. Du kan använda `Enable-PSRemoting` för att aktivera PowerShell-fjärrkommunikation i andra versioner av Windows som stöds och återaktivera fjärr kommunikation på Windows Server 2012 om den inaktive ras.

Du behöver bara köra det här kommandot en gången på varje dator som ska ta emot kommandon. Du behöver inte köra den på datorer som bara skickar kommandon. Eftersom konfigurationen startar lyssnare, är det försiktig att bara köra den där det behövs.

Från och med PowerShell 3,0 `Enable-PSRemoting` kan cmdlet: en aktivera PowerShell-fjärrkommunikation på klient versioner av Windows när datorn finns i ett offentligt nätverk. Mer information finns i beskrivningen av parametern **SkipNetworkProfileCheck** .

`Enable-PSRemoting`Cmdleten utför följande åtgärder:

- Kör cmdleten [set-WSManQuickConfig](../Microsoft.WSMan.Management/Set-WSManQuickConfig.md) som utför följande uppgifter:
  - Startar tjänsten WinRM.
  - Ställer in start typen på WinRM-tjänsten till automatisk.
  - Skapar en lyssnare som accepterar begär Anden på alla IP-adresser.
  - Aktiverar ett brand Väggs undantag för WS-Management kommunikation.
  - Registrerar konfigurationerna för **Microsoft. PowerShell** och **Microsoft. PowerShell. Workflow** -sessioner, om de inte redan har registrerats.
  - Registrerar konfigurationen för **Microsoft. PowerShell32** -sessionen på 64-bitars datorer, om den inte redan är registrerad.
  - Aktiverar alla konfigurationer för sessioner.
  - Ändrar säkerhets beskrivningen för alla sessionsinställningar för att tillåta fjärråtkomst.
- Startar om WinRM-tjänsten för att göra föregående ändringar gällande.

Om du vill köra denna cmdlet på Windows-plattformen startar du PowerShell med alternativet Kör som administratör. Detta gäller inte för Linux-eller MacOS-versioner av PowerShell.

> [!CAUTION]
> På system som har både PowerShell 3,0 och PowerShell 2,0 ska du inte använda PowerShell 2,0 för att köra `Enable-PSRemoting` `Disable-PSRemoting` cmdletarna och. Kommandona kan verka fungera, men fjärrkommunikationen är inte korrekt konfigurerad. Fjärrkommandon och senare försöker aktivera och inaktivera fjärr kommunikation fungerar sannolikt inte.

## EXEMPEL

### Exempel 1: Konfigurera en dator för att ta emot fjärrkommandon

Det här kommandot konfigurerar datorn att ta emot fjärrkommandon.

```powershell
Enable-PSRemoting
```

### Exempel 2: Konfigurera en dator för att ta emot fjärrkommandon utan att bekräfta en bekräftelse

Det här kommandot konfigurerar datorn att ta emot fjärrkommandon.
**Force** -parametern förhindrar användarens prompter.

```powershell
Enable-PSRemoting -Force
```

### Exempel 3: Tillåt fjärråtkomst på klienter

Det här exemplet visar hur du tillåter fjärråtkomst från offentliga nätverk på klient versioner av Windows operativ system. Namnet på brand Väggs regeln kan vara olika för olika versioner av Windows.
Använd `Get-NetFirewallRule` om du vill visa en lista över regler. Innan du aktiverar brand Väggs regeln kan du Visa säkerhets inställningarna i regeln för att kontrol lera att konfigurationen är lämplig för din miljö.

```powershell
Get-NetFirewallRule -Name 'WINRM*' | Select-Object Name
```

```Output
Name
----
WINRM-HTTP-In-TCP-NoScope
WINRM-HTTP-In-TCP
WINRM-HTTP-Compat-In-TCP-NoScope
WINRM-HTTP-Compat-In-TCP
```

```powershell
Enable-PSRemoting -SkipNetworkProfileCheck -Force
Set-NetFirewallRule -Name 'WINRM-HTTP-In-TCP' -RemoteAddress Any
```

Som standard `Enable-PSRemoting` skapar nätverks regler som tillåter fjärråtkomst från privata nätverk och domän nätverk. Kommandot använder parametern **SkipNetworkProfileCheck** för att tillåta fjärråtkomst från offentliga nätverk i samma lokala undernät. Kommandot anger **Force** -parametern för att ignorera bekräftelse meddelanden.

**SkipNetworkProfileCheck** -parametern påverkar inte Server versioner av Windows operativ system, som tillåter fjärråtkomst från offentliga nätverk i samma lokala undernät som standard.

`Set-NetFirewallRule`Cmdleten i modulen **netsecurity** lägger till en brand Väggs regel som tillåter fjärråtkomst från offentliga nätverk från valfri fjärrplats. Detta omfattar platser i olika undernät.

> [!NOTE]
> Namnet på brand Väggs regeln kan vara olika beroende på Windows-versionen. Använd `Get-NetFirewallRule` cmdleten för att visa namnen på reglerna i systemet.

## PARAMETRAR

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

### -SkipNetworkProfileCheck

Anger att denna cmdlet aktiverar fjärr kommunikation på klient versioner av Windows operativ system när datorn är i ett offentligt nätverk. Med den här parametern kan du använda en brand Väggs regel för offentliga nätverk som endast tillåter fjärråtkomst från datorer i samma lokala undernät.

Den här parametern påverkar inte Server versioner av Windows operativ system, som som standard har en lokal brand Väggs regel för offentliga nätverk. Om den lokala brand Väggs regeln är inaktive rad på en server version `Enable-PSRemoting` aktiverar du den igen, oavsett värdet för den här parametern.

Om du vill ta bort den lokala under näts begränsningen och aktivera fjärråtkomst från alla platser i offentliga nätverk använder du `Set-NetFirewallRule` cmdleten i modulen **netsecurity** .

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

### System. String

Denna cmdlet returnerar strängar som beskriver dess resultat.

## ANTECKNINGAR

I PowerShell 3,0 `Enable-PSRemoting` skapar följande brand Väggs undantag för WS-Management kommunikation.

I Server versioner av Windows-operativsystemet `Enable-PSRemoting` skapar brand Väggs regler för privata nätverk och domän nätverk som tillåter fjärråtkomst, och skapar en brand Väggs regel för offentliga nätverk som endast tillåter fjärråtkomst från datorer i samma lokala undernät.

I PowerShell 3,0 i klient versioner av Windows operativ system `Enable-PSRemoting` skapas brand Väggs regler för privata nätverk och domän nätverk som tillåter obegränsad fjärråtkomst. Om du vill skapa en brand Väggs regel för offentliga nätverk som tillåter fjärråtkomst från samma lokala undernät använder du parametern **SkipNetworkProfileCheck** .

På klient-eller Server versioner av Windows-operativsystemet, för att skapa en brand Väggs regel för offentliga nätverk som tar bort begränsningen lokalt undernät och tillåter fjärråtkomst, använder du `Set-NetFirewallRule` cmdleten i modulen netsecurity för att köra följande kommando: `Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any`

I PowerShell 2,0 `Enable-PSRemoting` skapar följande brand Väggs undantag för WS-Management kommunikation.

I Server versioner av Windows operativ system skapas brand Väggs regler för alla nätverk som tillåter fjärråtkomst.

`Enable-PSRemoting`I PowerShell 2,0 skapar ett brand Väggs undantag endast för domän platser och privata nätverks platser på klient versioner av Windows operativ system. För att minimera säkerhets riskerna `Enable-PSRemoting` skapar inte en brand Väggs regel för offentliga nätverk på klient versioner av Windows. När den aktuella nätverks platsen är offentlig `Enable-PSRemoting` returnerar följande meddelande: det går inte att kontrol lera status för brand väggen.

Med början i PowerShell 3,0, `Enable-PSRemoting` aktiverar alla sessionsinställningar genom att ställa in värdet för egenskapen **Enabled** för alla sessioner `$True` .

I PowerShell 2,0 `Enable-PSRemoting` tar bort inställningen **Deny_All** från säkerhets beskrivningen för sessionsbaserade. I PowerShell 3,0 `Enable-PSRemoting` tar bort **Deny_All** och **Network_Deny_All** inställningar. Detta ger fjärråtkomst till sessionsbaserade konfigurationer som har reserver ATS för lokal användning.

## RELATERADE LÄNKAR

[Disable-PSSessionConfiguration](Disable-PSSessionConfiguration.md)

[Aktivera – PSSessionConfiguration](Enable-PSSessionConfiguration.md)

[Get-PSSessionConfiguration](Get-PSSessionConfiguration.md)

[Registrera – PSSessionConfiguration](Register-PSSessionConfiguration.md)

[Set-PSSessionConfiguration](Set-PSSessionConfiguration.md)

[Disable-PSRemoting](Disable-PSRemoting.md)

[WSMan-Provider](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[about_Remote](About/about_Remote.md)

[about_Session_Configurations](About/about_Session_Configurations.md)
