---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-psremoting?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSRemoting
ms.openlocfilehash: 4d00b875aab2e175465b262a320e7b16893c255c
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94347388"
---
# Enable-PSRemoting

## SAMMANFATTNING
Konfigurerar datorn att ta emot fjärrkommandon.

## SYNTAX

```
Enable-PSRemoting [-Force] [-SkipNetworkProfileCheck] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Enable-PSRemoting`Cmdleten konfigurerar datorn att ta emot PowerShell-fjärrkommandon som skickas med hjälp av WS-Management teknik. WS-Management-baserad PowerShell-fjärrkommunikation stöds för närvarande endast på Windows-plattformen.

PowerShell-fjärrkommunikation är aktiverat som standard på Windows Server-plattformar. Du kan använda `Enable-PSRemoting` för att aktivera PowerShell-fjärrkommunikation i andra versioner av Windows som stöds och återaktivera fjärr kommunikation om den blir inaktive rad.

Du behöver bara köra det här kommandot en gången på varje dator som ska ta emot kommandon. Du behöver inte köra den på datorer som bara skickar kommandon. Eftersom konfigurationen startar lyssnare för att acceptera fjärr anslutningar, är det försiktig att bara köra den där det behövs.

Att aktivera PowerShell-fjärrkommunikation i klient versioner av Windows när datorn är i ett offentligt nätverk är normalt inte tillåten, men du kan hoppa över den här begränsningen genom att använda parametern **SkipNetworkProfileCheck** . Mer information finns i beskrivningen av parametern **SkipNetworkProfileCheck** .

Det kan finnas flera PowerShell-installationer sida vid sida på en enda dator. Vid körning `Enable-PSRemoting` konfigureras en slut punkt för Fjärrslutpunkter för den speciella installations version som du kör cmdleten i. Så om du kör `Enable-PSRemoting` powershell 6,2 konfigureras en slut punkt för fjärr kommunikation som kör powershell 6,2. Om du kör `Enable-PSRemoting` PowerShell 7 – för hands version konfigureras en fjärrslutpunkt som kör PowerShell 7 – för hands version.

`Enable-PSRemoting` skapar två slut punkts konfigurationer för fjärrkörning vid behov. Om slut punkts konfigurationerna redan finns är de bara säkra att de är aktiverade. De skapade konfigurationerna är identiska men har olika namn. Ett har ett enkelt namn som motsvarar den PowerShell-version som är värd för sessionen. Det andra konfigurations namnet innehåller mer detaljerad information om den PowerShell-version som är värd för sessionen. Om du till exempel kör `Enable-PSRemoting` i PowerShell 6,2 får du två konfigurerade slut punkter med namnet **PowerShell. 6** , **PowerShell. 6.2.2**.
På så sätt kan du skapa en anslutning till den senaste PowerShell 6-värd versionen med hjälp av det enkla namnet **PowerShell. 6**. Eller så kan du ansluta till en angiven PowerShell-värd version med längre namnet **PowerShell. 6.2.2**.

Om du vill använda de nyligen aktiverade slut punkterna för fjärr kommunikation måste du ange dem med hjälp av namn med parametern **ConfigurationName** när du skapar en fjärr anslutning med `Invoke-Command` `New-PSSession` `Enter-PSSession` cmdletarna,,. Mer information finns i exempel 4.

`Enable-PSRemoting`Cmdleten utför följande åtgärder:

- Kör cmdleten [set-WSManQuickConfig](../Microsoft.WSMan.Management/Set-WSManQuickConfig.md) som utför följande uppgifter:
  - Startar tjänsten WinRM.
  - Ställer in start typen på WinRM-tjänsten till automatisk.
  - Skapar en lyssnare som accepterar begär Anden på alla IP-adresser.
  - Aktiverar ett brand Väggs undantag för WS-Management kommunikation.
  - Skapar de enkla och långa namn för sessionens slut punkts konfiguration vid behov.
  - Aktiverar alla konfigurationer för sessioner.
  - Ändrar säkerhets beskrivningen för alla sessionsinställningar för att tillåta fjärråtkomst.
- Startar om WinRM-tjänsten för att göra föregående ändringar gällande.

Om du vill köra denna cmdlet på Windows-plattformen startar du PowerShell med alternativet Kör som administratör. Denna cmdlet är inte tillgänglig på Linux-eller MacOS-versioner av PowerShell.

> [!CAUTION]
> Denna cmdlet påverkar inte konfigurationer för Fjärrslutpunkter som skapats av Windows PowerShell.
> Den påverkar bara slut punkter som skapats med PowerShell version 6 och senare. Om du vill aktivera och inaktivera PowerShell-Fjärrslutpunkter som finns i Windows PowerShell kör du `Enable-PSRemoting` cmdleten inifrån en Windows PowerShell-session.

## EXEMPEL

### Exempel 1: Konfigurera en dator för att ta emot fjärrkommandon

Det här kommandot konfigurerar datorn att ta emot fjärrkommandon.

```powershell
Enable-PSRemoting
```

```Output
WARNING: PowerShell remoting has been enabled only for PowerShell Core configurations and does not
affect Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect
all PowerShell remoting configurations.
```

### Exempel 2: Konfigurera en dator för att ta emot fjärrkommandon utan att bekräfta en bekräftelse

Det här kommandot konfigurerar datorn att ta emot fjärrkommandon.
**Force** -parametern förhindrar användarens prompter.

```powershell
Enable-PSRemoting -Force
```

```Output
WARNING: PowerShell remoting has been enabled only for PowerShell Core configurations and does not
affect Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect
all PowerShell remoting configurations.
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

### Exempel 4: skapa en fjärrsession till den nyligen aktiverade slut punkts konfigurationen

Det här exemplet visar hur du aktiverar PowerShell-fjärrkommunikation på en dator, hittar de konfigurerade slut punkts namnen och skapar en fjärrsession till en av slut punkterna.

Det första kommandot aktiverar PowerShell-fjärrkommunikation på datorn.

Det andra kommandot visar slut punkts konfigurationerna.

Det tredje kommandot skapar en PowerShell-fjärrsession till samma dator och anger **PowerShell. 6** -slutpunkten efter namn. Fjärrsessionen kommer att vara värd för den senaste PowerShell 6-versionen (6.2.2).

Det sista kommandot använder `$PSVersionTable` variabeln i fjärrsessionen för att visa den PowerShell-version som är värd för sessionen.

```powershell
Enable-PSRemoting -Force

Get-PSSessionConfiguration

$session = New-PSSession -ComputerName localhost -ConfigurationName PowerShell.6

Invoke-Command -Session $session -ScriptBlock { $PSVersionTable }
```

```Output
WARNING: PowerShell remoting has been enabled only for PowerShell Core configurations and does not
affect Windows PowerShell remoting configurations. Run this cmdlet in Windows PowerShell to affect
all PowerShell remoting configurations.

Name          : PowerShell.6
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                BUILTIN\Remote Management Users AccessAllowed

Name          : PowerShell.6.2.2
PSVersion     : 6.2
StartupScript :
RunAsUser     :
Permission    : NT AUTHORITY\INTERACTIVE AccessAllowed, BUILTIN\Administrators AccessAllowed,
                BUILTIN\Remote Management Users AccessAllowed

Name                           Value
----                           -----
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0…}
PSEdition                      Core
PSRemotingProtocolVersion      2.3
Platform                       Win32NT
SerializationVersion           1.1.0.1
GitCommitId                    6.2.2
WSManStackVersion              3.0
PSVersion                      6.2.2
OS                             Microsoft Windows 10.0.18363
```

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

Den här cmdleten är endast tillgänglig på Windows-plattformar.

I Server versioner av Windows-operativsystemet `Enable-PSRemoting` skapar brand Väggs regler för privata nätverk och domän nätverk som tillåter fjärråtkomst, och skapar en brand Väggs regel för offentliga nätverk som endast tillåter fjärråtkomst från datorer i samma lokala undernät.

I klient versioner av Windows operativ system `Enable-PSRemoting` skapar brand Väggs regler för privata nätverk och domän nätverk som tillåter obegränsad fjärråtkomst. Om du vill skapa en brand Väggs regel för offentliga nätverk som tillåter fjärråtkomst från samma lokala undernät använder du parametern **SkipNetworkProfileCheck** .

På klient-eller Server versioner av Windows-operativsystemet, för att skapa en brand Väggs regel för offentliga nätverk som tar bort begränsningen lokalt undernät och tillåter fjärråtkomst, använder du `Set-NetFirewallRule` cmdleten i modulen netsecurity för att köra följande kommando: `Set-NetFirewallRule -Name "WINRM-HTTP-In-TCP-PUBLIC" -RemoteAddress Any`

`Enable-PSRemoting` aktiverar alla sessionsinställningar genom att ställa in värdet för egenskapen **Enabled** för alla sessioner till `$True` .

`Enable-PSRemoting` tar bort inställningarna för **Deny_All** och **Network_Deny_All** . Detta ger fjärråtkomst till sessionsbaserade konfigurationer som har reserver ATS för lokal användning.

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
