---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/connect-wsman?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Connect-WSMan
ms.openlocfilehash: d06ede0e27713b1a309aa2ed265f02881d34124e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267357"
---
# Connect-WSMan

## SAMMANFATTNING
Ansluter till WinRM-tjänsten på en fjärrdator.

## SYNTAX

### ComputerName (standard)

```
Connect-WSMan [-ApplicationName <String>] [[-ComputerName] <String>] [-OptionSet <Hashtable>] [-Port <Int32>]
 [-SessionOption <SessionOption>] [-UseSSL] [-Credential <PSCredential>]
 [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>] [<CommonParameters>]
```

### URI

```
Connect-WSMan [-ConnectionURI <Uri>] [-OptionSet <Hashtable>] [-Port <Int32>] [-SessionOption <SessionOption>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

## BESKRIVNING
Cmdleten **Connect-WSMan** ansluter till WinRM-tjänsten på en fjärrdator och upprättar en permanent anslutning till fjärrdatorn.
Du kan använda denna cmdlet i kontexten för WSMan-providern för att ansluta till WinRM-tjänsten på en fjärrdator.
Du kan dock även använda denna cmdlet för att ansluta till WinRM-tjänsten på en fjärrdator innan du ändrar till WSMan-providern.
Den fjärranslutna datorn visas i rot katalogen för WSMan-providern.

Explicita autentiseringsuppgifter krävs när klient-och serverdatorer finns i olika domäner eller arbets grupper.

Information om hur du kopplar från tjänsten WinRM på en fjärrdator finns i Disconnect-WSMan-cmdleten.

## EXEMPEL

### Exempel 1: Anslut till en fjärrdator

```
PS C:\> Connect-WSMan -ComputerName "server01"
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan

ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

Det här kommandot skapar en anslutning till den fjärranslutna Server01-datorn.

Cmdleten **Connect-WSMan** används vanligt vis i kontexten för WSMan-providern för att ansluta till en fjärrdator, i det här fallet Server01-datorn.
Du kan dock använda cmdleten för att upprätta anslutningar till fjärrdatorer innan du byter till WSMan-providern.
Dessa anslutningar visas i listan **dator namn** .

### Exempel 2: Anslut till en fjärrdator med hjälp av administratörsautentiseringsuppgifter

```
PS C:\> $cred = Get-Credential Administrator
PS C:\> Connect-WSMan -ComputerName "server01" -Credential $cred
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan

ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

Det här kommandot skapar en anslutning till fjärrsystemet Server01 med hjälp av autentiseringsuppgifter för administratörs kontot.

Det första kommandot använder Get-Credential-cmdlet för att hämta autentiseringsuppgifter för administratören och lagrar dem i $cred-variabeln.
**Get-Credential** uppmanas att ange ett lösen ord för användar namn och lösen ord via en dialog ruta eller på kommando raden, beroende på systemets register inställningar.

Det andra kommandot använder parametern *Credential* för att skicka autentiseringsuppgifterna som lagras i $cred till **Connect-WSMan**.
**Anslut-WSMan** ansluter sedan till Server01 för fjärrsystemet med hjälp av administratörs behörighet.

### Exempel 3: Anslut till en fjärran sluten dator över en angiven port

```
PS C:\> Connect-WSMan -ComputerName "server01" -Port 80
PS C:\> cd wsman:
PS WSMan:\>
PS WSMan:\> dir
WSManConfig: Microsoft.WSMan.Management\WSMan::WSMan
ComputerName                                  Type
------------                                  ----
localhost                                     Container
server01                                      Container
```

Det här kommandot skapar en anslutning till fjärran Server01-datorn via port 80.

### Exempel 4: Anslut till en fjärrdator med hjälp av anslutnings alternativ

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

I det här exemplet skapas en anslutning till den fjärranslutna Server01-datorn med hjälp av anslutnings alternativen som definieras i kommandot **New-WSManSessionOption** .

Det första kommandot använder **New-WSManSessionOption** för att lagra en uppsättning anslutnings inställnings alternativ i variabeln $a.
I det här fallet har sessions alternativen en anslutnings tid på 30 sekunder (30 000 millisekunder).

Det andra kommandot använder parametern *SessionOption* för att skicka de autentiseringsuppgifter som lagras i variabeln $a för att **ansluta-WSMan**.
Sedan ansluter **-WSMan** till den fjärranslutna Server01-datorn med hjälp av de angivna session alternativen.

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
Position: 0
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
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
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
Denna cmdlet genererar inga utdata.

## ANTECKNINGAR

* Du kan köra hanterings kommandon eller fråga hanterings data på en fjärrdator utan att skapa en WS-Management session. Du kan göra detta med hjälp av *computername* -parametrarna för Invoke-WSManAction och get-WSManInstance. När du använder parametern *computername* skapar PowerShell en tillfällig anslutning som används för det enskilda kommandot. När kommandot har körts stängs anslutningen.

*

## RELATERADE LÄNKAR

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

[Test-WSMan](Test-WSMan.md)
