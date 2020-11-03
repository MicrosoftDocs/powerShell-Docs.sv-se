---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/new-wsmansessionoption?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WSManSessionOption
ms.openlocfilehash: 8996c550147ab7e0857d97b0a47baf92fac514d8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263984"
---
# New-WSManSessionOption

## SAMMANFATTNING
Skapar en hash-tabell för sessionsinställningar som ska användas som indataparametrar för WS-Management-cmdletar.

## SYNTAX

```
New-WSManSessionOption [-ProxyAccessType <ProxyAccessType>] [-ProxyAuthentication <ProxyAuthentication>]
 [-ProxyCredential <PSCredential>] [-SkipCACheck] [-SkipCNCheck] [-SkipRevocationCheck] [-SPNPort <Int32>]
 [-OperationTimeout <Int32>] [-NoEncryption] [-UseUTF16] [<CommonParameters>]
```

## BESKRIVNING
Cmdlet: en **New-WSManSessionOption** skapar en hash-tabell för WSMan-session som kan skickas till WSMan-cmdlet: ar:

- Get-WSManInstance
- Set-WSManInstance
- Invoke-WSManAction
- Connect-WSMan

## EXEMPEL

### Exempel 1: skapa en anslutning som använder anslutnings alternativ

```
PS C:\> $a = New-WSManSessionOption -OperationTimeout 30000
PS C:\> Connect-WSMan -ComputerName "server01" -SessionOption $a
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan
ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

I det här exemplet skapas en anslutning till den fjärranslutna Server01-datorn med hjälp av anslutnings alternativen som definieras av **New-WSManSessionOption**.

Det första kommandot använder **New-WSManSessionOption** för att lagra en uppsättning anslutnings inställnings alternativ i variabeln $a.
I det här fallet har sessions alternativen en anslutnings tid på 30 sekunder (30 000 millisekunder).

Det andra kommandot använder parametern *SessionOption* för att skicka de autentiseringsuppgifter som lagras i variabeln $a för att **ansluta-WSMan**.
Sedan ansluter **-WSMan** till den fjärranslutna Server01-datorn med hjälp av de angivna session alternativen.

**Connect-WSMan** används vanligt vis i kontexten för WSMan-providern för att ansluta till en fjärrdator, i det här fallet Server01-datorn.
Du kan dock använda cmdleten för att upprätta anslutningar till fjärrdatorer innan du byter till WSMan-providern.
Dessa anslutningar visas i listan **dator namn** .

## PARAMETRAR

### – Encryption
Anger att anslutningen inte använder kryptering för fjärråtgärder över HTTP.

Okrypterad trafik är som standard inte aktive rad.
Den måste vara aktive rad i den lokala konfigurationen.

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

### -OperationTimeout
Anger tids gräns i millisekunder för WS-Management åtgärden.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: OperationTimeoutMSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyAccessType
Anger den mekanism som proxyservern finns i.
De acceptabla värdena för den här parametern är:

- ProxyIEConfig.
Använd proxy-konfigurationen i Internet Explorer för den aktuella användaren.
- ProxyWinHttpConfig.
WSMan-klienten använder proxyinställningarna som kon figurer ATS för WinHTTP med hjälp av ProxyCfg.exe-verktyget.
- ProxyAutoDetect.
Framtvinga automatisk identifiering av en proxyserver.
- ProxyNoProxyServer.
Använd inte en proxyserver.
Matcha alla värdnamn lokalt.

Standardvärdet är ProxyIEConfig.

```yaml
Type: Microsoft.WSMan.Management.ProxyAccessType
Parameter Sets: (All)
Aliases:
Accepted values: ProxyIEConfig, ProxyWinHttpConfig, ProxyAutoDetect, ProxyNoProxyServer

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyAuthentication
Anger autentiseringsmetoden som ska användas vid proxyservern.
De acceptabla värdena för den här parametern är:

- Frö.
Basic är ett schema där användar namn och lösen ord skickas i klartext till servern eller proxyservern.
- Nedbrytning.
Digest är ett utmaning-svar schema som använder en server angiven data sträng för utmaningen.
- Fram.
Negotiate är ett utmaning-svar schema som förhandlar med servern eller proxyservern för att avgöra vilket schema som ska användas för autentisering.
Exempel är Kerberos-protokollet och NTLM.

Standardvärdet är Negotiate.

```yaml
Type: Microsoft.WSMan.Management.ProxyAuthentication
Parameter Sets: (All)
Aliases:
Accepted values: Negotiate, Basic, Digest

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyCredential
Anger ett användar konto som har behörighet att få åtkomst via en mellanliggande webbproxy.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SkipCACheck
Anger att när den ansluter via HTTPS, verifierar inte klienten att Server certifikatet är signerat av en betrodd certifikat utfärdare (CA).
Använd bara det här alternativet när fjärrdatorn är betrodd av en annan metod, till exempel om fjärrdatorn är en del av ett nätverk som är fysiskt säkert och isolerat eller om fjärrdatorn visas som en betrodd värd i WS-Management-konfigurationen.

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

### -SkipCNCheck
Anger att serverns certifikats allmänna namn inte behöver matcha serverns värdnamn.
Detta används endast i fjärråtgärder med hjälp av HTTPS.
Det här alternativet bör endast användas för betrodda datorer.

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

### -SkipRevocationCheck
Anger att anslutningen inte verifierar åter kallelse statusen för Server certifikatet.

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

### -SPNPort
Anger ett port nummer som ska läggas till i anslutnings tjänstens huvud namn (SPN) för fjärrservern.
Ett SPN används när autentiseringsmekanismen är Kerberos eller förhandla.

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

### -UseUTF16
Anger att anslutningen kodar begäran i UTF16-format istället för UTF8-format.
Standardvärdet är UTF8-kodning.

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

### CommonParameters
Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

## UTDATA

### SessionOption

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Anslut-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

[Koppla från-WSMan](Disconnect-WSMan.md)

[Aktivera – WSManCredSSP](Enable-WSManCredSSP.md)

[Get-WSManCredSSP](Get-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-WSManInstance](New-WSManInstance.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Test-WSMan](Test-WSMan.md)
