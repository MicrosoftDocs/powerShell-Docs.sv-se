---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/13/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-restmethod?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-RestMethod
ms.openlocfilehash: c89f7351e9c874cea2cc0cd5e0912e3ca0d8b0bf
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264956"
---
# Invoke-RestMethod

## Sammanfattning
Skickar en HTTP-eller HTTPS-begäran till en RESTful-webbtjänst.

## Syntax

```
Invoke-RestMethod [-Method <WebRequestMethod>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-CertificateThumbprint <String>] [-Certificate <X509Certificate>]
 [-UserAgent <String>] [-DisableKeepAlive] [-TimeoutSec <Int32>] [-Headers <IDictionary>]
 [-MaximumRedirection <Int32>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials]
 [-Body <Object>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>] [-OutFile <String>]
 [-PassThru] [<CommonParameters>]
```

## Beskrivning

`Invoke-RestMethod`Cmdlet: en skickar HTTP-och HTTPS-begäranden till en rest-webbtjänster (Representational State Transfer) som returnerar data som kan struktureras.

Windows PowerShell formaterar svaret baserat på data typen. För en RSS-eller ATOM-feed returnerar Windows PowerShell objektet eller postens XML-noder. För JavaScript Object Notation (JSON) eller XML konverterar Windows PowerShell (eller deserialiserar) innehållet till objekt.

Denna cmdlet introduceras i Windows PowerShell 3,0.

> [!NOTE]
> Som standard kan skript kod på webb sidan köras när sidan parsas för att fylla i `ParsedHtml` egenskapen. Använd **UseBasicParsing** -växeln för att ignorera detta.

## Exempel

### Exempel 1: Hämta PowerShell RSS-flödet

```powershell
Invoke-RestMethod -Uri https://devblogs.microsoft.com/powershell/feed/ |
  Format-Table -Property Title, pubDate
```

```Output
Title                                                                pubDate
-----                                                                -------
Join the PowerShell 10th Anniversary Celebration!                    Tue, 08 Nov 2016 23:00:04 +0000
DSC Resource Kit November 2016 Release                               Thu, 03 Nov 2016 00:19:07 +0000
PSScriptAnalyzer Community Call - Oct 18, 2016                       Thu, 13 Oct 2016 17:52:35 +0000
New Home for In-Box DSC Resources                                    Sat, 08 Oct 2016 07:13:10 +0000
New Social Features on Gallery                                       Fri, 30 Sep 2016 23:04:34 +0000
PowerShellGet and PackageManagement in PowerShell Gallery and GitHub Thu, 29 Sep 2016 22:21:42 +0000
PowerShell Security at DerbyCon                                      Wed, 28 Sep 2016 01:13:19 +0000
DSC Resource Kit September Release                                   Thu, 22 Sep 2016 00:25:37 +0000
PowerShell DSC and implicit remoting broken in KB3176934             Tue, 23 Aug 2016 15:07:50 +0000
PowerShell on Linux and Open Source!                                 Thu, 18 Aug 2016 15:32:02 +0000
```

Det här kommandot använder `Invoke-RestMethod` cmdleten för att hämta information från RSS-flödet för PowerShell-bloggen. Kommandot använder `Format-Table` cmdleten för att visa värdena för egenskaperna **title** och **pubDate** för varje blogg i en tabell.

### Exempel 2

I följande exempel körs en användare `Invoke-RestMethod` för att utföra en post-begäran på en intranäts webbplats i användarens organisation.

```powershell
$Cred = Get-Credential

# Next, allow the use of self-signed SSL certificates.

[System.Net.ServicePointManager]::ServerCertificateValidationCallback = { $True }

# Create variables to store the values consumed by the Invoke-RestMethod command.
# The search variable contents are later embedded in the body variable.

$Server = 'server.contoso.com'
$Url = "https://${server}:8089/services/search/jobs/export"
$Search = "search index=_internal | reverse | table index,host,source,sourcetype,_raw"

# The cmdlet handles URL encoding. The body variable describes the search criteria, specifies CSV as
# the output mode, and specifies a time period for returned data that starts two days ago and ends
# one day ago. The body variable specifies values for parameters that apply to the particular REST
# API with which Invoke-RestMethod is communicating.

$Body = @{
    search = $Search
    output_mode = "csv"
    earliest_time = "-2d@d"
    latest_time = "-1d@d"
}

# Now, run the Invoke-RestMethod command with all variables in place, specifying a path and file
# name for the resulting CSV output file.

Invoke-RestMethod -Method Post -Uri $url -Credential $Cred -Body $body -OutFile output.csv

{"preview":true,"offset":0,"result":{"sourcetype":"contoso1","count":"9624"}}

{"preview":true,"offset":1,"result":{"sourcetype":"contoso2","count":"152"}}

{"preview":true,"offset":2,"result":{"sourcetype":"contoso3","count":"88494"}}

{"preview":true,"offset":3,"result":{"sourcetype":"contoso4","count":"15277"}}
```

### Exempel 3: skicka flera huvuden

Det här exemplet visar hur du skickar flera huvuden i från en `hash-table` till en REST API.

```powershell
$headers = @{
    'userId' = 'UserIDValue'
    'token' = 'TokenValue'
}
Invoke-RestMethod -Uri $uri -Method Post -Headers $headers -Body $body
```

API: er kräver ofta skickade rubriker för autentisering, validering osv.

### Exempel 3: skicka formulär data

När bröd texten är ett formulär, eller om det är utdata från ett annat `Invoke-WebRequest` anrop, anger PowerShell innehållet i formulär fälten.

Ett exempel:

```powershell
$R = Invoke-WebRequest https://website.com/login.aspx
$R.Forms[0].Name = "MyName"
$R.Forms[0].Password = "MyPassword"
Invoke-RestMethod https://website.com/service.aspx -Body $R.Forms[0]
```

## Parametrar

### -Body

Anger bröd texten i begäran. Bröd texten är innehållet i begäran som följer sidhuvuden.
Du kan också skicka ett Body-värde till `Invoke-RestMethod` .

Du kan använda **text** parametern för att ange en lista över frågeparametrar eller ange svarets innehåll.

När indatamängden är en GET-begäran och texten är en IDictionary (vanligt vis en hash-tabell), läggs bröd texten till i URI: n som frågeparametrar. För andra typer av begär Anden (till exempel POST) anges bröd texten som värdet för begär ande texten i standard namnet = värde formatet.

> [!WARNING]
> Utförliga utdata från en POST-brödtext slutar med `with -1-byte payload` , även om bröd texten både är känd och skickad i `Content-Length` http-huvudet.

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### – Certifikat

Anger det klient certifikat som används för en säker webb förfrågan. Ange en variabel som innehåller ett certifikat eller ett kommando eller uttryck som hämtar certifikatet.

Om du vill söka efter ett certifikat använder `Get-PfxCertificate` eller använder du `Get-ChildItem` cmdleten på certifikat `Cert:` enheten (). Om certifikatet inte är giltigt eller inte har tillräcklig behörighet, Miss lyckas kommandot.

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -CertificateThumbprint

Anger det digitala certifikat för offentlig nyckel (X509) för ett användar konto som har behörighet att skicka begäran. Ange certifikatets tumavtryck.

Certifikat används i klient certifikat-baserad autentisering. De kan endast mappas till lokala användar konton. de fungerar inte med domän konton.

Om du vill hämta ett tumavtryck för certifikatet använder du `Get-Item` `Get-ChildItem` kommandot eller i Windows PowerShell ( `Cert:` )-enheten.

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

### -ContentType

Anger webb begärans innehålls typ.

Om den här parametern utelämnas och metoden för begäran är POST, `Invoke-RestMethod` ställer in innehålls typen på "Application/x-www-form-urlencoded". Annars anges inte innehålls typen i anropet.

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

### -Credential

Anger ett användar konto som har behörighet att skicka begäran. Standard är den aktuella användaren.

Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten.

Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisableKeepAlive

Anger **keepalive** -värdet i HTTP-huvudet till false. **Keepalive** är som standard sant.
**Keepalive** upprättar en permanent anslutning till servern för att under lätta efterföljande begär Anden.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: KeepAlive
Accept pipeline input: False
Accept wildcard characters: False
```

### – Sidhuvud

Anger webb begärans rubriker. Ange en hash-tabell eller-ord lista.

Om du vill ange UserAgent-rubriker använder du parametern **useragent** . Du kan inte använda den här parametern för att ange UserAgent-eller cookie-rubriker.

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -INFILE

Hämtar innehållet i webb förfrågan från en fil.

Ange en sökväg och ett fil namn. Om du utelämnar sökvägen är standardvärdet den aktuella platsen.

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

### -MaximumRedirection

Anger hur många gånger Windows PowerShell omdirigerar en anslutning till en alternativ Uniform Resource Identifier (URI) innan anslutningen Miss lyckas. Standardvärdet är 5. Värdet 0 (noll) förhindrar all omdirigering.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### -Metod

Anger den metod som används för webb förfrågan. De acceptabla värdena för den här parametern är:

- Default
- Ta bort
- Hämta
- Head
- Sammanfoga
- Alternativ
- Patch
- Skicka
- Placera
- Spårning

```yaml
Type: Microsoft.PowerShell.Commands.WebRequestMethod
Parameter Sets: (All)
Aliases:
Accepted values: Default, Get, Head, Post, Put, Delete, Trace, Options, Merge, Patch

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### -Fil

Sparar svars texten i den angivna utdatafilen. Ange en sökväg och ett fil namn. Om du utelämnar sökvägen är standardvärdet den aktuella platsen.

Som standard `Invoke-RestMethod` returnerar resultatet till pipelinen. Om du vill skicka resultatet till en fil och till pipelinen använder du parametern **Passthru** .

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

### – PassThru

Returnerar resultaten, förutom att skriva dem till en fil. Den här parametern är endast giltig om **parametern out** också används i kommandot.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: No output
Accept pipeline input: False
Accept wildcard characters: False
```

### -Proxy

Använder en proxyserver för begäran, i stället för att ansluta direkt till Internet resursen. Ange URI för en proxyserver för nätverket.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyCredential

Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** . Standard är den aktuella användaren.

Ange ett användar namn, till exempel "user01" eller "Domain01\User01", eller ange ett **PSCredential** -objekt, t. ex. ett som genererades av `Get-Credential` cmdleten.

Den här parametern är endast giltig när parametern **proxy** också används i kommandot. Du kan inte använda parametrarna **ProxyCredential** och **ProxyUseDefaultCredentials** i samma kommando.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyUseDefaultCredentials

Använder autentiseringsuppgifterna för den aktuella användaren för att få åtkomst till proxyservern som anges av parametern **proxy** .

Den här parametern är endast giltig när parametern **proxy** också används i kommandot. Du kan inte använda parametrarna **ProxyCredential** och **ProxyUseDefaultCredentials** i samma kommando.

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

### -SessionVariable

Skapar en Webbbegäran-session och sparar den i värdet för den angivna variabeln. Ange ett variabel namn utan dollar tecknet ( `$` )-symbolen.

När du anger en sessionsvariabel `Invoke-RestMethod` skapar ett sessionsobjekt för Webbbegäran och tilldelar det till en variabel med det angivna namnet i PowerShell-sessionen. Du kan använda variabeln i din session så snart kommandot har slutförts.

Till skillnad från en fjärran sluten session är inte Webbbegäran-sessionen en permanent anslutning. Det är ett objekt som innehåller information om anslutningen och begäran, inklusive cookies, autentiseringsuppgifter, det maximala värdet för omdirigering och användar agent strängen. Du kan använda den för att dela tillstånd och data mellan webb förfrågningar.

Om du vill använda Webbbegäran-sessionen i efterföljande webb förfrågningar, anger du variabeln session i värdet för **websession** -parametern. Windows PowerShell använder data i objektet Webbbegäran-session när den nya anslutningen upprättas. Om du vill åsidosätta ett värde i Webbbegäran-sessionen använder du en cmdlet-parameter, till exempel **useragent** eller **Credential**. Parameter värden har företräde framför värden i Webbbegäran-sessionen.

Du kan inte använda parametrarna **SessionVariable** och **websession** i samma kommando.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: SV

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TimeoutSec

Anger hur lång tid det tar att vänta på begäran innan den går ut. Ange ett värde i sekunder. Standardvärdet 0 anger en obestämd tids gräns.

En Domain Name System-fråga (DNS) kan ta upp till 15 sekunder att returnera eller ta slut för lång tid. Om din begäran innehåller ett värdnamn som kräver lösning och du anger TimeoutSec till ett värde som är större än noll, men mindre än 15 sekunder, kan det ta 15 sekunder eller mer innan en WebException utlöses, och tids gränsen för din begäran görs.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 0
Accept pipeline input: False
Accept wildcard characters: False
```

### -TransferEncoding

Anger ett värde för HTTP-svarshuvuden för överförings kodning. De acceptabla värdena för den här parametern är:

- Segment vis
- Compress
- DEFLATE
- GZip
- Identitet

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: chunked, compress, deflate, gzip, identity

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -URI

Anger Uniform Resource Identifier (URI) för den Internet resurs som webb förfrågan skickas till. Den här parametern stöder HTTP-, HTTPS-, FTP-och fil värden.

Den här parametern är obligatorisk. Parameter namnet ( **URI** ) är valfritt.

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -UseBasicParsing

Anger att cmdleten använder grundläggande parsning. Cmdleten returnerar den råa HTML-koden i ett **String** -objekt.

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

### -UseDefaultCredentials

Använder autentiseringsuppgifterna för den aktuella användaren för att skicka webb förfrågan.

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

### – UserAgent

Anger en användar agent sträng för webb förfrågan.

Standard användar agenten liknar "Mozilla/5.0 (Windows NT; Windows NT 6,1; en-US) WindowsPowerShell/3.0 "med små variationer för varje operativ system och plattform.

Om du vill testa en webbplats med den standard användar agent sträng som används av de flesta webbläsare, använder du egenskaperna för [PSUserAgent](/dotnet/api/microsoft.powershell.commands) -klassen, till exempel Chrome, Firefox, Internet Explorer, Opera och Safari.

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

### – Websession

Anger en Webbbegäran-session. Ange variabel namnet, inklusive dollar tecknet ( `$` ).

Om du vill åsidosätta ett värde i Webbbegäran-sessionen använder du en cmdlet-parameter, till exempel **useragent** eller **Credential**. Parameter värden har företräde framför värden i Webbbegäran-sessionen.

Till skillnad från en fjärran sluten session är inte Webbbegäran-sessionen en permanent anslutning. Det är ett objekt som innehåller information om anslutningen och begäran, inklusive cookies, autentiseringsuppgifter, det maximala värdet för omdirigering och användar agent strängen. Du kan använda den för att dela tillstånd och data mellan webb förfrågningar.

Om du vill skapa en Webbbegäran-session anger du ett variabel namn (utan dollar tecken) i värdet för parametern **SessionVariable** för ett `Invoke-RestMethod` kommando. `Invoke-RestMethod` skapar sessionen och sparar den i variabeln. I efterföljande kommandon använder du variabeln som värde för **websession** -parametern.

Du kan inte använda parametrarna **SessionVariable** och **websession** i samma kommando.

```yaml
Type: Microsoft.PowerShell.Commands.WebRequestSession
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

## Indata

### System. Object

Du kan skicka vidare innehållet i en webb förfrågan till `Invoke-RestMethod` .

## Utdata

### System.Xml.Xmldokument Microsoft.PowerShell.Commands.HtmlWebResponseObject, system. String

Utdata från cmdleten beror på formatet på det innehåll som hämtas.

### PSObject

Om begäran returnerar JSON-strängar `Invoke-RestMethod` returnerar en PSObject som representerar strängarna.

## Kommentarer

## Relaterade länkar

[ConvertTo-Json](ConvertTo-Json.md)

[ConvertFrom – JSON](ConvertFrom-Json.md)

[Anropa-webbegäran](Invoke-WebRequest.md)
