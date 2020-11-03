---
external help file: Microsoft.WSMan.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.WSMan.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.wsman.management/set-wsmaninstance?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-WSManInstance
ms.openlocfilehash: 2547efe8c3784d29fe852288a8442ac17335fe52
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268292"
---
# Set-WSManInstance

## SAMMANFATTNING
Ändrar den hanterings information som är relaterad till en resurs.

## SYNTAX

### ComputerName (standard)

```
Set-WSManInstance [-ApplicationName <String>] [-ComputerName <String>] [-Dialect <Uri>] [-FilePath <String>]
 [-Fragment <String>] [-OptionSet <Hashtable>] [-Port <Int32>] [-ResourceURI] <Uri>
 [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>] [-UseSSL] [-ValueSet <Hashtable>]
 [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>] [-CertificateThumbprint <String>]
 [<CommonParameters>]
```

### URI

```
Set-WSManInstance [-ConnectionURI <Uri>] [-Dialect <Uri>] [-FilePath <String>] [-Fragment <String>]
 [-OptionSet <Hashtable>] [-ResourceURI] <Uri> [[-SelectorSet] <Hashtable>] [-SessionOption <SessionOption>]
 [-ValueSet <Hashtable>] [-Credential <PSCredential>] [-Authentication <AuthenticationMechanism>]
 [-CertificateThumbprint <String>] [<CommonParameters>]
```

## BESKRIVNING

Set-WSManInstance-cmdleten ändrar hanterings informationen som är relaterad till en resurs.

Denna cmdlet använder WinRM-anslutningen/transport lagret för att ändra informationen.

## EXEMPEL

### Exempel 1: inaktivera en lyssnare på den lokala datorn

```powershell
Set-WSManInstance -ResourceURI winrm/config/listener -SelectorSet @{address="*";transport="https"} -ValueSet @{Enabled="false"}
```

```Output
cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
lang                  : en-US
Address               : *
Transport             : HTTPS
Port                  : 443
Hostname              :
Enabled               : false
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {127.0.0.1, 172.30.168.171, ::1, 2001:4898:0:fff:0:5efe:172.30.168.171...}
```

Detta kommando inaktiverar https-lyssnaren på den lokala datorn.

Viktigt: parametern *ValueSet* är Skift läges känslig när du matchar de angivna egenskaperna.

I det här kommandot kan du till exempel

Detta Miss lyckas: `-ValueSet @{enabled="False"}`

Detta lyckas: `-ValueSet @{Enabled="False"}`

### Exempel 2: Ange Max storlek för kuvert på den lokala datorn

```powershell
Set-WSManInstance -ResourceURI winrm/config -ValueSet @{MaxEnvelopeSizekb = "200"}
```

```Output
cfg                 : http://schemas.microsoft.com/wbem/wsman/1/config
lang                : en-US
MaxEnvelopeSizekb   : 200
MaxTimeoutms        : 60000
MaxBatchItems       : 32000
MaxProviderRequests : 4294967295
Client              : Client
Service             : Service
Winrs               : Winrs
```

Detta kommando ställer in värdet för MaxEnvelopeSizekb på 200 på den lokala datorn.

Viktigt: parametern ValueSet är Skift läges känslig när du matchar de angivna egenskaperna.

Du kan till exempel använda kommandot ovan.

Detta Miss lyckas:-ValueSet @ {MaxEnvelopeSizeKB = "200"}

Detta lyckas:-ValueSet @ {MaxEnvelopeSizekb = "200"}

### Exempel 3: inaktivera en lyssnare på en fjärrdator

```powershell
Set-WSManInstance -ResourceURI winrm/config/listener -ComputerName SERVER02 -SelectorSet @{address="*";transport="https"} -ValueSet @{Enabled="false"}
```

```Output
cfg                   : http://schemas.microsoft.com/wbem/wsman/1/config/listener
xsi                   : http://www.w3.org/2001/XMLSchema-instance
lang                  : en-US
Address               : *
Transport             : HTTPS
Port                  : 443
Hostname              :
Enabled               : false
URLPrefix             : wsman
CertificateThumbprint :
ListeningOn           : {127.0.0.1, 172.30.168.172, ::1, 2001:4898:0:fff:0:5efe:172.30.168.172...}
```

Med det här kommandot inaktive ras https-lyssnaren på fjärrdatorn SERVER02.

Viktigt: parametern ValueSet är Skift läges känslig när du matchar de angivna egenskaperna.

Du kan till exempel använda kommandot ovan.

Detta Miss lyckas:-ValueSet @ {Enabled = "false"}

Detta lyckas:-ValueSet @ {Enabled = "false"}

## PARAMETRAR

### -ApplicationName

Anger program namnet i anslutningen.
Standardvärdet för parametern ApplicationName är "WSMAN".
Den fullständiga identifieraren för Fjärrslutpunkten har följande format:

\<transport\>://\<server\>:\<port\>/\<ApplicationName\>

Ett exempel:

`http://server01:8080/WSMAN`

Internet Information Services (IIS), som är värd för sessionen, vidarebefordrar begär Anden med den här slut punkten till det angivna programmet.
Den här standardinställningen för "WSMAN" är lämplig för de flesta användnings områden.
Den här parametern är avsedd att användas när flera datorer upprättar fjärr anslutningar till en dator som kör Windows PowerShell.
I det här fallet är IIS värd för webb tjänster för hantering (WS-Management) för effektivitet.

```yaml
Type: System.String
Parameter Sets: ComputerName
Aliases:

Required: False
Position: Named
Default value: Wsman
Accept pipeline input: False
Accept wildcard characters: False
```

### -Autentisering

Anger vilken autentiseringsmekanism som ska användas på servern.
Möjliga värden:

- Basic: Basic är ett schema där användar namn och lösen ord skickas i klartext till servern eller proxyservern.
- Standard: Använd autentiseringsmetoden som implementeras av WS-Management-protokollet. Det här är standardinställningen.
- Digest: Digest är ett utmaning-svar schema som använder en server angiven data sträng för utmaningen.
- Kerberos: klient datorn och servern autentiseras ömsesidigt med hjälp av Kerberos-certifikat.
- Förhandla: Negotiate är ett utmaning-svar schema som förhandlar med servern eller proxyservern för att avgöra vilket schema som ska användas för autentisering. Detta parameter värde tillåter till exempel förhandling för att avgöra om Kerberos-protokollet eller NTLM används.
- CredSSP: Använd CredSSP-autentisering (Credential Security Support Provider), vilket gör att användaren kan delegera autentiseringsuppgifter. Det här alternativet är utformat för kommandon som körs på en fjärrdator men samlar in data från eller kör ytterligare kommandon på andra fjärrdatorer.

Varning! CredSSP delegerar användarens autentiseringsuppgifter från den lokala datorn till en fjärran sluten dator.
Den här metoden ökar säkerhets risken för Fjärråtgärden.
Om fjärrdatorn komprometteras, när autentiseringsuppgifter skickas till den, kan autentiseringsuppgifterna användas för att kontrol lera nätverks sessionen.

```yaml
Type: Microsoft.WSMan.Management.AuthenticationMechanism
Parameter Sets: (All)
Aliases: auth, am

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

Anger den dator som du vill köra hanterings åtgärden mot.
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
Default value: Localhost
Accept pipeline input: False
Accept wildcard characters: False
```

### -ConnectionURI

Anger anslutnings slut punkten.
Formatet för den här strängen är:

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
Ange ett användar namn, till exempel "user01", "Domain01\User01" eller " User@Domain.com ".
Eller ange ett PSCredential-objekt, till exempel ett som returneras av Get-Credential-cmdleten.
När du anger ett användar namn uppmanas du att ange ett lösen ord.

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

### – Dialekt

Anger dialekten som ska användas i filtrets predikat.
Detta kan vara vilken dialekt som helst som stöds av fjärrtjänsten.
Följande alias kan användas för dialekt-URI: n:

- WQL `http://schemas.microsoft.com/wbem/wsman/1/WQL`
- Select `http://schemas.microsoft.com/wbem/wsman/1/wsman/SelectorFilter`
- Föreningar `http://schemas.dmtf.org/wbem/wsman/1/cimbinding/associationFilter`

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: http://schemas.microsoft.com/wbem/wsman/1/WQL
Accept pipeline input: False
Accept wildcard characters: False
```

### -Sökväg

Anger sökvägen till en fil som används för att uppdatera en hanterings resurs.
Du anger hanterings resursen med hjälp av parametern ResourceURI och parametern SelectorSet.
Följande kommando använder till exempel parametern sökväg:

`Invoke-WSManAction -action StopService -resourceuri wmicimv2/Win32_Service -SelectorSet @{Name="spooler"} -FilePath:c:\input.xml -authentication default`

Det här kommandot anropar metoden Stop service i Spooler-tjänsten genom att använda indata från en fil.
Filen Input.xml innehåller följande innehåll:

`<p:StopService_INPUT xmlns:p="http://schemas.microsoft.com/wbem/wsman/1/wmi/root/cimv2/Win32_Service" />`

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Path

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – Fragment

Anger ett avsnitt inuti instansen som ska uppdateras eller hämtas för den angivna åtgärden.
Om du till exempel vill hämta statusen för en Spooler-tjänst anger du "-fragment status".

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

### -OptionSet

Skickar en uppsättning växlar till en tjänst för att ändra eller förfina begärans natur.
Dessa liknar växlar som används i kommando rads gränssnitt eftersom de är specifika för specifika tjänster.
Valfritt antal alternativ kan anges.

I följande exempel visas syntaxen som skickar värdena 1, 2 och 3 för parametrarna a, b och c:

-OptionSet @ {a = 1; b = 2; c = 3}

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
När du använder HTTPS som transport måste värdet för parametern ComputerName matcha serverns certifikats eget namn (CN).
Men om parametern SkipCNCheck anges som en del av parametern SessionOption, behöver inte Certifikatets gemensamma namn matcha serverns värdnamn.
Parametern SkipCNCheck ska endast användas för betrodda datorer.

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

Innehåller Uniform Resource Identifier (URI) för resurs klassen eller-instansen.
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
Parametern SelectorSet används när det finns mer än en instans av resursen.
Värdet för parametern SelectorSet måste vara en hash-tabell.
I följande exempel visas hur du anger ett värde för den här parametern:

-SelectorSet @ {Name = "WinRM"; ID = "YYY"}

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### -SessionOption

Definierar en uppsättning utökade alternativ för WS-Management-sessionen.
Ange ett SessionOption-objekt som du skapar med hjälp av New-WSManSessionOption-cmdleten.
Mer information om tillgängliga alternativ finns i New-WSManSessionOption.

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

Anger att Secure Sockets Layer (SSL)-protokollet ska användas för att upprätta en anslutning till fjärrdatorn.
Som standard används inte SSL.

WS-Management krypterar allt Windows PowerShell-innehåll som överförs via nätverket.
Med parametern UseSSL kan du ange ytterligare skydd av HTTPS i stället för HTTP.
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

### -ValueSet

Anger en hash-tabell som hjälper dig att ändra en hanterings resurs.
Du anger hanterings resursen med hjälp av parametern ResourceURI och parametern SelectorSet.
Värdet för parametern ValueSet måste vara en hash-tabell.

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

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

[Aktivera – WSManCredSSP](Enable-WSManCredSSP.md)

[Get-WSManCredSSP](Get-WSManCredSSP.md)

[Get-WSManInstance](Get-WSManInstance.md)

[Invoke-WSManAction](Invoke-WSManAction.md)

[New-WSManInstance](New-WSManInstance.md)

[New-WSManSessionOption](New-WSManSessionOption.md)

[Remove-WSManInstance](Remove-WSManInstance.md)

[Set-WSManQuickConfig](Set-WSManQuickConfig.md)

[Test-WSMan](Test-WSMan.md)
