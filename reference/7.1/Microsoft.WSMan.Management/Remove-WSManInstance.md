---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/remove-wsmaninstance?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-WSManInstance
ms.openlocfilehash: 6bd166942551671c581c04cb611c222378caeba1
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268268"
---
# Remove-WSManInstance

## SAMMANFATTNING
Tar bort en hanterings resurs instans.

## SYNTAX

### ComputerName (standard)

```
Remove-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-OptionSet <Hashtable>]
 [-Port <Int32>] [-ResourceURI] <Uri> [-SelectorSet] <Hashtable> [-SessionOption <SessionOption>] [-UseSSL]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### URI

```
Remove-WSManInstance [-ConnectionURI <Uri>] [-OptionSet <Hashtable>] [-ResourceURI] <Uri>
 [-SelectorSet] <Hashtable> [-SessionOption <SessionOption>] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

## BESKRIVNING

Cmdlet: en **Remove-WSManInstance** tar bort en instans av en hanterings resurs som anges i parametrarna *ResourceURI* och *SelectorSet* .

Denna cmdlet använder WinRM-anslutningen/transport lagret för att ta bort hanterings resurs instansen.

## EXEMPEL

### Exempel 1: ta bort en lyssnare

```
PS C:\> Remove-WSManInstance -ResourceUri winrm/config/Listener -SelectorSet Address=test.fabrikam.com;Transport=http
```

Detta kommando tar bort WS-Management HTTP-lyssnare på en dator.

## PARAMETRAR

### -ApplicationName

Anger program namnet i anslutningen.
Standardvärdet för parametern *ApplicationName* är WSMan.
Den fullständiga identifieraren för Fjärrslutpunkten har följande format:

\<transport\>://\<server\>:\<port\>/\<ApplicationName\>

Exempelvis: `http://server01:8080/WSMAN`

Internet Information Services (IIS), som är värd för sessionen, vidarebefordrar begär Anden med den här slut punkten till det angivna programmet.
Den här standardinställningen för WSMAN är lämplig för de flesta användnings områden.
Den här parametern är avsedd att användas om många datorer upprättar fjärr anslutningar till en dator som kör PowerShell.
I det här fallet är IIS värd för webb tjänster för hantering (WS-Management) för effektivitet.

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Autentisering

Anger vilken autentiseringsmekanism som ska användas på servern.
De acceptabla värdena för den här parametern är:

- Frö.
Basic är ett schema där användar namn och lösen ord skickas i klartext till servern eller proxyservern.
- Standard.
Använd autentiseringsmetoden som implementeras av WS-Management-protokollet.
Det här är standardinställningen.
- Nedbrytning.
Digest är ett utmaning-svar schema som använder en server angiven data sträng för utmaningen.
- Paket.
Klient datorn och servern autentiseras ömsesidigt med hjälp av Kerberos-certifikat.
- Fram.
Negotiate är ett utmaning-svar schema som förhandlar med servern eller proxyservern för att avgöra vilket schema som ska användas för autentisering.
Detta parameter värde kan till exempel användas för förhandling för att avgöra om Kerberos-protokollet eller NTLM används.
- CredSSP.
Använd CredSSP-autentisering (Credential Security Support Provider), vilket gör att användaren kan delegera autentiseringsuppgifter.
Det här alternativet är utformat för kommandon som körs på en fjärrdator men samlar in data från eller kör ytterligare kommandon på andra fjärrdatorer.

Varning! CredSSP delegerar användarautentiseringsuppgifter från den lokala datorn till en fjärrdator.
Den här metoden ökar säkerhets risken för Fjärråtgärden.
Om fjärrdatorn komprometteras, när autentiseringsuppgifter skickas till den, kan autentiseringsuppgifterna användas för att kontrol lera nätverks sessionen.

```yaml
Type: Microsoft.WSMan.Management.AuthenticationMechanism
Parameter Sets: (All)
Aliases: auth, am
Accepted values: None, Default, Digest, Negotiate, Basic, Kerberos, ClientCertificate, Credssp

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

Anger X509 (Digital Public Key Certificate) för ett användar konto som har behörighet att utföra den här åtgärden.
Ange certifikatets tumavtryck.

Certifikat används i klient certifikat-baserad autentisering.
De kan endast mappas till lokala användar konton. de fungerar inte med domän konton.

Om du vill hämta ett tumavtryck för certifikatet använder du kommandot Get-Item eller Get-ChildItem i PowerShell-certifikatet: enhet.

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

### -ComputerName

Anger den dator som hanterings åtgärden ska köras mot.
Värdet kan vara ett fullständigt kvalificerat domän namn, ett NetBIOS-namn eller en IP-adress.
Använd namnet på den lokala datorn, Använd localhost eller Använd en punkt (.) för att ange den lokala datorn.
Den lokala datorn är standard.
Om fjärrdatorn finns i en annan domän än användaren måste du använda ett fullständigt kvalificerat domän namn.
Du kan skicka ett värde för den här parametern till cmdlet: en.

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases: cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConnectionURI

Anger anslutnings slut punkten.
Formatet för den här strängen är följande:

\<Transport\>://\<Server\>:\<Port\>/\<ApplicationName\>

Följande sträng är ett korrekt formaterat värde för den här parametern:

`http://Server01:8080/WSMAN`

URI: n måste vara fullständigt kvalificerad.

```yaml
Type: System.Uri
Parameter Sets: URI
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Credential

Anger ett användar konto som har behörighet att utföra den här åtgärden.
Standard är den aktuella användaren.
Ange ett användar namn, till exempel user01, Domain01\User01 eller User@Domain.com .
Eller ange ett **PSCredential** -objekt, till exempel ett som returneras av Get-Credential-cmdleten.
När du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases: cred, c

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -OptionSet

Anger en uppsättning växlar till en tjänst för att ändra eller förfina begärans typ.
Dessa liknar växlar som används i kommando rads gränssnitt eftersom de är specifika för specifika tjänster.
Valfritt antal alternativ kan anges.

I följande exempel visas syntaxen som skickar värdena 1, 2 och 3 för parametrarna a, b och c:

`-OptionSet @{a=1;b=2;c=3}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases: os

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Port

Anger vilken port som ska användas när klienten ansluter till WinRM-tjänsten.
När transporten är HTTP är standard porten 80.
När transporten är HTTPS är standard porten 443.

När du använder HTTPS som transport måste värdet för parametern *computername* matcha serverns certifikats eget namn (CN).
Men om parametern *SkipCNCheck* anges som en del av parametern *SessionOption* , behöver inte Certifikatets gemensamma namn matcha serverns värdnamn.
Parametern *SkipCNCheck* ska endast användas för betrodda datorer.

```yaml
Type: System.Int32
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – ResourceURI

Anger URI för resurs klassen eller-instansen.
URI: n används för att identifiera en speciell typ av resurs, till exempel diskar eller processer, på en dator.

En URI består av ett prefix och en sökväg till en resurs.
Ett exempel:

`http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_LogicalDisk`

`http://schemas.dmtf.org/wbem/wscim/1/cim-schema/2/CIM_NumericSensor`

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases: ruri

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -SelectorSet

Anger en uppsättning värdepar som används för att välja specifika hanterings resurs instanser.
Parametern *SelectorSet* används när det finns mer än en instans av resursen.
Värdet för *SelectorSet* måste vara en hash-tabell.

I följande exempel visas hur du anger ett värde för den här parametern:

`-SelectorSet @{Name="WinRM";ID="yyy"}`

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SessionOption

Anger utökade alternativ för WS-Management-sessionen.
Ange ett **SessionOption** -objekt som du skapar med hjälp av New-WSManSessionOption-cmdleten.
Om du vill ha mer information om vilka alternativ som är tillgängliga skriver du `Get-Help New-WSManSessionOption` .

```yaml
Type: Microsoft.WSMan.Management.SessionOption
Parameter Sets: (All)
Aliases: so

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseSSL

Anger att Secure Sockets Layer-protokollet (SSL) används för att upprätta en anslutning till fjärrdatorn.
Som standard används inte SSL.

WS-Management krypterar allt PowerShell-innehåll som överförs via nätverket.
Med parametern *UseSSL* kan du ange ytterligare skydd av https i stället för http.
Om SSL inte är tillgängligt på den port som används för anslutningen och du anger den här parametern, Miss lyckas kommandot.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ComputerName
Aliases: ssl

Required: False
Position: Named
Default value: None
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

* Remove-WmiObject cmdlet, en Windows Management Instrumentation (WMI)-cmdlet, liknar. **Remove-WmiObject** använder DCOM-anslutningen/transport lagret för att skapa eller uppdatera WMI-instanser.

*

## RELATERADE LÄNKAR

[Anslut-WSMan](Connect-WSMan.md)

[Disable-WSManCredSSP](Disable-WSManCredSSP.md)

[Koppla från-WSMan](Disconnect-WSMan.md)

[Aktivera – WSManCredSSP](Enable-WSManCredSSP.md)

[Get-WSManCredSSP](Get-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Test-WSMan](Test-WSMan.md)

