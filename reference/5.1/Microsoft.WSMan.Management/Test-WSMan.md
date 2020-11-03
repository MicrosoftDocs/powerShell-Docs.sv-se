---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/test-wsman?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-WSMan
ms.openlocfilehash: 3178c12dbc14b9d0841f1d924a695ae2f761f579
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/21/2020
ms.locfileid: "93273080"
---
# Test-WSMan

## SAMMANFATTNING
Testar om WinRM-tjänsten körs på en lokal dator eller fjärrdator.

## SYNTAX

```
Test-WSMan [[-ComputerName] <String>] [-Authentication <AuthenticationMechanism>] [-Port <Int32>] [-UseSSL]
 [-ApplicationName <String>] [-Credential <PSCredential>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

## BESKRIVNING
Cmdleten **test-WSMan** skickar en identifierings förfrågan som avgör om WinRM-tjänsten körs på en lokal dator eller fjärrdator.
Om den testade datorn kör tjänsten visar cmdleten WS-Management identitets schema, protokoll version, produkt leverantör och produkt version för den testade tjänsten.

## EXEMPEL

### Exempel 1: Fastställ statusen för WinRM-tjänsten

```
PS C:\> Test-WSMan
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 2.0
```

Det här kommandot avgör om WinRM-tjänsten körs på den lokala datorn eller på en fjärrdator.

### Exempel 2: Fastställ statusen för WinRM-tjänsten på en fjärrdator

```
PS C:\> Test-WSMan -ComputerName "server01"
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 0.0.0 SP: 0.0 Stack: 2.0
```

Det här kommandot avgör om WinRM-tjänsten körs på den Server01 datorn.

### Exempel 3: Fastställ status för WinRM-tjänsten och operativ system versionen

```
PS C:\> Test-WSMan -Authentication default
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 6.0.6001 SP: 1.0 Stack: 2.0
```

Det här kommandot testar för att se om tjänsten WS-Management (WinRM) körs på den lokala datorn med hjälp av parametern Authentication.

Med parametern Authentication kan **test-WSMan** returnera operativ systemets version.

### Exempel 4: Fastställ status för WinRM-tjänsten och operativ system versionen på en fjärrdator

```
PS C:\> Test-WSMan -ComputerName "server01" -Authentication default
wsmid           : http://schemas.dmtf.org/wbem/wsman/identity/1/wsmanidentity.xsd

ProtocolVersion : http://schemas.dmtf.org/wbem/wsman/1/wsman.xsd

ProductVendor   : Microsoft Corporation

ProductVersion  : OS: 6.1.7021 SP: 0.0 Stack: 2.0
```

Det här kommandot testar för att se om tjänsten WS-Management (WinRM) körs på datorn med namnet Server01 med hjälp av parametern Authentication.

Med parametern Authentication kan **test-WSMan** returnera operativ systemets version.

## PARAMETRAR

### -ApplicationName
Anger program namnet i anslutningen.
Standardvärdet för parametern *ApplicationName* är WSMan.
Den fullständiga identifieraren för Fjärrslutpunkten har följande format:

\<transport\>://\<server\>:\<port\>/\<ApplicationName\>

Exempelvis: `http://server01:8080/WSMAN`

Internet Information Services (IIS), som är värd för sessionen, vidarebefordrar begär Anden med den här slut punkten till det angivna programmet.
Den här standardinställningen för WSMAN är lämplig för de flesta användnings områden.
Den här parametern är avsedd att användas om många datorer upprättar fjärr anslutningar till en dator som kör Windows PowerShell.
I det här fallet är IIS värd för webb tjänster för hantering (WS-Management) för effektivitet.

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

Viktigt: om du inte anger parametern *Authentication* skickas **test-WSMan-** begäran till fjärrdatorn anonymt, utan att autentisering används.
Om begäran görs anonymt returneras ingen information som är speciell för operativ systemets version.
I stället visar denna cmdlet null-värden för operativ systemets version och service pack nivå (OS: 0.0.0 SP: 0,0).

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

Om du vill hämta ett tumavtryck för certifikatet använder du kommandot Get-Item eller Get-ChildItem i Windows PowerShell-certifikatet: enhet.

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
Parameter Sets: (All)
Aliases: cn

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
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

### -Port
Anger vilken port som ska användas när klienten ansluter till WinRM-tjänsten.
När transporten är HTTP är standard porten 80.
När transporten är HTTPS är standard porten 443.

När du använder HTTPS som transport måste värdet för parametern *computername* matcha serverns certifikats eget namn (CN).

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

### -UseSSL
Anger att Secure Sockets Layer-protokollet (SSL) används för att upprätta en anslutning till fjärrdatorn.
Som standard används inte SSL.

WS-Management krypterar allt Windows PowerShell-innehåll som överförs via nätverket.
Med parametern *UseSSL* kan du ange ytterligare skydd av https i stället för http.
Om SSL inte är tillgängligt på den port som används för anslutningen och du anger den här parametern, Miss lyckas kommandot.

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

### Inget
Denna cmdlet accepterar inte några indatatyper.

## UTDATA

### Inget
Denna cmdlet genererar inga utdata-objekt.

## ANTECKNINGAR

* Som standard frågar **test-WSMan-** cmdleten WinRM-tjänsten utan att använda autentisering, och den returnerar ingen information som är speciell för operativ systemets version. I stället visas null-värden för operativ system versionen och service pack nivån (OS: 0.0.0 SP: 0,0).

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

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManInstance](Set-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)
