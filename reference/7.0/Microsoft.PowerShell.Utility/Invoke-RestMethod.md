---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/25/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-restmethod?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-RestMethod
ms.openlocfilehash: aab7ae73d223f349fc0c103332331710a3eb2efe
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262142"
---
# Invoke-RestMethod

## SAMMANFATTNING
Skickar en HTTP-eller HTTPS-begäran till en RESTful-webbtjänst.

## SYNTAX

### StandardMethod (standard)

```
Invoke-RestMethod [-Method <WebRequestMethod>] [-FollowRelLink] [-MaximumFollowRelLink <Int32>]
 [-ResponseHeadersVariable <String>] [-StatusCodeVariable <String>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### StandardMethodNoProxy

```
Invoke-RestMethod [-Method <WebRequestMethod>] [-FollowRelLink] [-MaximumFollowRelLink <Int32>]
 [-ResponseHeadersVariable <String>] [-StatusCodeVariable <String>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] -NoProxy [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### CustomMethodNoProxy

```
Invoke-RestMethod -CustomMethod <String> [-FollowRelLink] [-MaximumFollowRelLink <Int32>]
 [-ResponseHeadersVariable <String>] [-StatusCodeVariable <String>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] -NoProxy [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### CustomMethod

```
Invoke-RestMethod -CustomMethod <String> [-FollowRelLink] [-MaximumFollowRelLink <Int32>]
 [-ResponseHeadersVariable <String>] [-StatusCodeVariable <String>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

## Beskrivning

`Invoke-RestMethod`Cmdlet: en skickar HTTP-och HTTPS-begäranden till en rest-webbtjänster (Representational State Transfer) som returnerar data som kan struktureras.

PowerShell formaterar svaret baserat på data typen. För en RSS-eller ATOM-feed returnerar PowerShell objektet eller postens XML-noder. För JavaScript Object Notation (JSON) eller XML konverterar PowerShell eller deserialiserar innehållet till objekt.

Denna cmdlet introduceras i Windows PowerShell 3,0.

Från och med PowerShell 7,0 `Invoke-RestMethod` stöder proxykonfigurationen som definieras av miljövariabler. Se avsnittet [anteckningar](#notes) i den här artikeln.

## EXEMPEL

### Exempel 1: Hämta PowerShell RSS-flödet

I det här exemplet används `Invoke-RestMethod` cmdleten för att hämta information från RSS-flödet i PowerShell-bloggen. Kommandot använder `Format-Table` cmdleten för att visa värdena för egenskaperna **title** och **pubDate** för varje blogg i en tabell.

```powershell
Invoke-RestMethod -Uri https://blogs.msdn.microsoft.com/powershell/feed/ |
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

### Exempel 2: kör en POST-begäran

I det här exemplet körs en användare `Invoke-RestMethod` för att göra en post-begäran på en intranäts webbplats i användarens organisation.

```powershell
$Cred = Get-Credential
$Url = "https://server.contoso.com:8089/services/search/jobs/export"
$Body = @{
    search = "search index=_internal | reverse | table index,host,source,sourcetype,_raw"
    output_mode = "csv"
    earliest_time = "-2d@d"
    latest_time = "-1d@d"
}
Invoke-RestMethod -Method 'Post' -Uri $url -Credential $Cred -Body $body -OutFile output.csv
```

Autentiseringsuppgifterna efter frågas och lagras sedan i `$Cred` och den URL som ska vara åtkomst definieras i `$Url` .

`$Body`Variabeln beskriver Sök villkoren, anger CSV som output-läge och anger en tids period för returnerade data som börjar två dagar sedan och slutar en dag sedan. Body-variabeln anger värden för parametrar som gäller för den specifika REST API som `Invoke-RestMethod` kommunicerar med.

`Invoke-RestMethod`Kommandot körs med alla variabler på plats och anger en sökväg och ett fil namn för den resulterande CSV-utdatafilen.

### Exempel 3: Följ Relations länkar

Vissa REST API: er stöder sid brytning via Relations länkar per [RFC5988](https://tools.ietf.org/html/rfc5988#page-6). I stället för att parsa rubriken för att hämta URL: en för nästa sida kan du låta cmdlet: en göra detta åt dig. Det här exemplet returnerar de två första sidor med problem från PowerShell-GitHub-lagringsplatsen.

```powershell
$url = 'https://api.github.com/repos/powershell/powershell/issues'
Invoke-RestMethod $url -FollowRelLink -MaximumFollowRelLink 2
```

### Exempel 4: överföring av förenklad multipart/form – data

Vissa API: er kräver att det går `multipart/form-data` att överföra filer och blandat innehåll. Det här exemplet visar hur du uppdaterar en användares profil.

```powershell
$Uri = 'https://api.contoso.com/v2/profile'
$Form = @{
    firstName  = 'John'
    lastName   = 'Doe'
    email      = 'john.doe@contoso.com'
    avatar     = Get-Item -Path 'c:\Pictures\jdoe.png'
    birthday   = '1980-10-15'
    hobbies    = 'Hiking','Fishing','Jogging'
}
$Result = Invoke-RestMethod -Uri $Uri -Method Post -Form $Form
```

Profil formuläret kräver följande fält:,,,, `firstName` `lastName` `email` `avatar` `birthday` och `hobbies` . API: et förväntar sig en bild för användar profils pic som ska anges i `avatar` fältet. API: et kommer också att acceptera flera `hobbies` poster som ska skickas i samma formulär.

När du skapar en `$Form` hash-tabellen används nyckel namnen som namn på formulär fält. Som standard konverteras värdena för hash-tabellen till strängar. Om det finns ett `System.IO.FileInfo` värde skickas filens innehåll. Om det finns en samling, till exempel matriser eller listor, skickas formulär fältet flera gånger.

Genom att använda `Get-Item` på `avatar` nyckeln `FileInfo` anges objektet som värde. Resultatet är att bild data för `jdoe.png` skickas.

Om du anger en lista till `hobbies` nyckeln `hobbies` visas fältet i de här sändningarna en gång för varje List objekt.

### Exempel 5: skicka flera huvuden

API: er kräver ofta skickade rubriker för autentisering eller verifiering. Det här exemplet visar hur du skickar flera huvuden från en `hash-table` till en REST API.

```powershell
$headers = @{
    'userId' = 'UserIDValue'
    'token' = 'TokenValue'
}
Invoke-RestMethod -Uri $uri -Method Post -Headers $headers -Body $body
```

## Parametrar

### -AllowUnencryptedAuthentication

Tillåter sändning av autentiseringsuppgifter och hemligheter över okrypterade anslutningar. Som standard, anger **Credential** eller valfritt **autentiseringsalternativ** med en **URI** som inte börjar med `https://` , resulterar i ett fel och begäran avbryts för att förhindra oavsiktlig kommunikation av hemligheter i oformaterad text över okrypterade anslutningar. Om du vill åsidosätta det här beteendet på egen risk anger du parametern **AllowUnencryptedAuthentication** .

> [!WARNING]
> Att använda den här parametern är inte säkert och rekommenderas inte. Det tillhandahålls endast för kompatibilitet med äldre system som inte kan tillhandahålla krypterade anslutningar. Använd på egen risk.

Den här funktionen har lagts till i PowerShell-6.0.0.

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

### -Autentisering

Anger den explicita autentiseringstypen som ska användas för begäran. Standardvärdet är **none**.
Det går inte att använda **autentisering** med **UseDefaultCredentials**.

Tillgängliga autentiserings alternativ:

- **Ingen** : det här är standard alternativet när **autentisering** inte anges. Ingen explicit autentisering kommer att användas.
- **Basic** : kräver **autentiseringsuppgifter**. Autentiseringsuppgifterna kommer att användas för att skicka ett RFC 7617 Basic Authentication- `Authorization: Basic` huvud i formatet `base64(user:password)` .
- **Bearer** : kräver **token**. Kommer att skicka och RFC 6750- `Authorization: Bearer` huvud med angiven token. Detta är ett alias för **OAuth**
- **OAuth** : kräver **token**. Skickar ett RFC 6750- `Authorization: Bearer` huvud med angiven token. Detta är ett alias för **innehavare**

Om du anger **autentisering** åsidosätts alla `Authorization` rubriker som anges i **sidhuvuden** eller som ingår i **websessionen**.

Den här funktionen har lagts till i PowerShell-6.0.0.

```yaml
Type: Microsoft.PowerShell.Commands.WebAuthenticationType
Parameter Sets: (All)
Aliases:
Accepted values: None, Basic, Bearer, OAuth

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Body

Anger bröd texten i begäran. Bröd texten är innehållet i begäran som följer sidhuvuden.
Du kan också skicka ett Body-värde till `Invoke-RestMethod` .

Du kan använda **text** parametern för att ange en lista över frågeparametrar eller ange svarets innehåll.

När indatamängden är en GET-begäran och texten är en `IDictionary` (vanligt vis en hash-tabell) läggs bröd texten till i Uniform Resource Identifier (URI) som frågeparametrar. För andra typer av begär Anden (till exempel POST) anges bröd texten som värdet för begär ande texten i standard namnet = värde formatet.

När bröd texten är ett formulär eller om det är utdata från ett annat `Invoke-WebRequest` anrop, anger PowerShell innehållet i formulär fälten.

**Bröd text** parametern kan också acceptera ett **system .net. http. MultipartFormDataContent-** objekt. Detta underlättar `multipart/form-data` begär Anden. När ett **MultipartFormDataContent** -objekt anges för **brödtext** , åsidosätts alla innehåll relaterade rubriker som har angetts för egenskaperna **ContentType** , **headers** eller **websession** av `MultipartFormDataContent` objektets innehålls rubriker. Den här funktionen har lagts till i PowerShell-6.0.0.

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

Om du vill hämta ett tumavtryck för certifikatet använder du `Get-Item` `Get-ChildItem` kommandot eller i PowerShell- `Cert:` enheten.

> [!NOTE]
> Den här funktionen stöds för närvarande endast på Windows OS-plattformar.

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

Om den här parametern utelämnas och metoden för begäran är POST, `Invoke-RestMethod` anger innehålls typen till `application/x-www-form-urlencoded` . Annars anges inte innehålls typen i anropet.

**ContentType** kommer att åsidosättas när ett `MultipartFormDataContent` objekt anges för **brödtext**.

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

**Autentiseringsuppgifter** kan användas separat eller tillsammans med vissa parametrar för **autentiseringsprinciper** . När den används enbart skickas autentiseringsuppgifter till fjärrservern om fjärrservern skickar en begäran om autentisering av begäran. När den används med **autentiseringsalternativ** skickas autentiseringsuppgifterna uttryckligen.

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

### -CustomMethod

Anger en anpassad metod som används för webbegäran. Detta kan användas med den metod för begäran som krävs av slut punkten är inte ett tillgängligt alternativ för **metoden**. **Metoden** och **CustomMethod** kan inte användas tillsammans.

Exempel:

`Invoke-RestMethod -uri 'https://api.contoso.com/widget/' -CustomMethod 'TEST'`

Detta gör en `TEST` http-begäran till API: et.

Den här funktionen har lagts till i PowerShell-6.0.0.

```yaml
Type: System.String
Parameter Sets: CustomMethodNoProxy, CustomMethod
Aliases: CM

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -DisableKeepAlive

Anger att cmdleten anger **keepalive** -värdet i HTTP-huvudet till false. **Keepalive** är som standard sant. **Keepalive** upprättar en permanent anslutning till servern för att under lätta efterföljande begär Anden.

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

### -FollowRelLink

Anger att cmdleten ska följa Relations länkar.

Vissa REST API: er stöder sid brytning via Relations länkar per [RFC5988](https://tools.ietf.org/html/rfc5988#page-6). I stället för att parsa rubriken för att hämta URL: en för nästa sida kan du låta cmdlet: en göra detta åt dig. Använd parametern **MaximumFollowRelLink** för att ange hur många gånger du vill följa Relations länkarna.

När du använder den här växeln returnerar cmdleten en samling resultat sidor. Varje sida med resultat kan innehålla flera resultat objekt.

Den här funktionen har lagts till i PowerShell-6.0.0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: FL

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Form

Konverterar en ord lista till ett `multipart/form-data` överförings objekt. **Formulär** får inte användas med **brödtext**.
Om **ContentType** ignoreras.

Nycklarna i ord listan används som namn på formulär fält. Som standard kommer formulär värden att konverteras till sträng värden.

Om värdet är ett **system. io. fileinfo** -objekt, kommer den binära fil innehållet att skickas.
Filens namn skickas som `filename` . MIME kommer att anges som `application/octet-stream` . `Get-Item` kan användas för att förenkla tillhandahålla **system. io. fileinfo** -objektet.

```powershell
$Form = @{
    resume = Get-Item 'c:\Users\jdoe\Documents\John Doe.pdf'
}
```

Om värdet är en samlings typ, till exempel en matris eller lista skickas fältet for flera gånger. Värdena i listan kommer att behandlas som strängar som standard. Om värdet är ett **system. io. fileinfo** -objekt, kommer den binära fil innehållet att skickas. Kapslade samlingar stöds inte.

```powershell
$Form = @{
    tags     = 'Vacation', 'Italy', '2017'
    pictures = Get-ChildItem 'c:\Users\jdoe\Pictures\2017-Italy\'
}
```

I exemplet ovan anges `tags` fältet tre gånger i formuläret, en gång för varje `Vacation` , `Italy` och `2017` . `pictures`Fältet kommer också att skickas en gång för varje fil i `2017-Italy` mappen. Det binära innehållet i filerna i mappen kommer att skickas som värden.

Den här funktionen har lagts till i PowerShell-6.1.0.

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

### – Sidhuvud

Anger webb begärans rubriker. Ange en hash-tabell eller-ord lista.

Om du vill ange UserAgent-rubriker använder du parametern **useragent** . Du kan inte använda den här parametern för att ange `User-Agent` eller cookie-rubriker.

Content-relaterade rubriker, till exempel `Content-Type` kommer att åsidosättas när ett `MultipartFormDataContent` objekt anges för **brödtext**.

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

### -MaximumFollowRelLink

Anger hur många gånger som Relations länkar ska följas om **FollowRelLink** används. Du kan behöva ett mindre värde om REST API-begränsningarna beror på för många begär Anden. Standardvärdet är `[Int32]::MaxValue`. Värdet 0 (noll) förhindrar följande Relations länkar.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: ML

Required: False
Position: Named
Default value: Int32.MaxValue
Accept pipeline input: False
Accept wildcard characters: False
```

### -MaximumRedirection

Anger hur många gånger PowerShell omdirigerar en anslutning till en alternativ Uniform Resource Identifier (URI) innan anslutningen Miss lyckas. Standardvärdet är 5. Värdet 0 (noll) förhindrar all omdirigering.

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

### -MaximumRetryCount

Anger hur många gånger PowerShell försöker upprätta en anslutning när en felkod mellan 400 och 599, inklusive eller 304, tas emot. Se även **RetryIntervalSec** -parametern för att ange antal återförsök.

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

**CustomMethod** -parametern kan användas för förfrågnings metoder som inte anges ovan.

```yaml
Type: Microsoft.PowerShell.Commands.WebRequestMethod
Parameter Sets: StandardMethod, StandardMethodNoProxy
Aliases:
Accepted values: Default, Get, Head, Post, Put, Delete, Trace, Options, Merge, Patch

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Noproxy

Anger att cmdleten inte kommer att använda en proxy för att komma till målet.

Använd den här växeln när du behöver kringgå proxyn som kon figurer ATS i Internet Explorer eller en proxyserver som anges i miljön.

Den här parametern introducerades i PowerShell 6,0.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: StandardMethodNoProxy, CustomMethodNoProxy
Aliases:

Required: True
Position: Named
Default value: None
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

### -PreserveAuthorizationOnRedirect

Anger att cmdleten ska bevara `Authorization` sidhuvudet, om det finns, över omdirigeringar.

Som standard tar cmdleten bort `Authorization` sidhuvudet före omdirigeringen. Om du anger den här parametern inaktive ras den här logiken för fall där huvudet måste skickas till omdirigerings platsen.

Den här funktionen har lagts till i PowerShell-6.0.0.

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

### -Proxy

Använder en proxyserver för begäran, i stället för att ansluta direkt till Internet resursen. Ange Uniform Resource Identifier (URI) för en nätverks-proxyserver.

Den här funktionen har lagts till i PowerShell-6.0.0.

```yaml
Type: System.Uri
Parameter Sets: StandardMethod, CustomMethod
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyCredential

Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** . Standard är den aktuella användaren.

Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , **User@Domain.Com** eller ange ett `PSCredential` objekt, till exempel en som genereras av `Get-Credential` cmdleten.

Den här parametern är endast giltig när parametern **proxy** också används i kommandot. Du kan inte använda parametrarna **ProxyCredential** och **ProxyUseDefaultCredentials** i samma kommando.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: StandardMethod, CustomMethod
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProxyUseDefaultCredentials

Anger att cmdleten använder autentiseringsuppgifterna för den aktuella användaren för att få åtkomst till proxyservern som anges av parametern **proxy** .

Den här parametern är endast giltig när parametern **proxy** också används i kommandot. Du kan inte använda parametrarna **ProxyCredential** och **ProxyUseDefaultCredentials** i samma kommando.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: StandardMethod, CustomMethod
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ResponseHeadersVariable

Skapar en ord lista för svars rubriker och sparar den i värdet för den angivna variabeln. Nycklarna i ord listan innehåller fält namnen för svars huvudet som returneras av webb servern och värdena är respektive fält värden.

Den här funktionen har lagts till i PowerShell-6.0.0.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: RHV

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Återuppta

Utför ett bästa försök att återuppta hämtningen av en delvis fil. Parametern **Resume** kräver parametern **DisFile** .

**Återuppta** fungerar bara på storleken på den lokala filen och fjärrfilen och utför ingen annan validering av att den lokala filen och fjärrfilen är desamma.

Om den lokala fil storleken är mindre än fjärrfils storleken försöker cmdleten återuppta nedladdningen av filen och lägga till återstående byte i slutet av filen.

Om den lokala fil storleken är samma som fjärrfilens storlek, utförs ingen åtgärd och cmdleten förutsätter att nedladdningen redan har slutförts.

Om den lokala fil storleken är större än fjärrfilens storlek, kommer den lokala filen att skrivas över och hela fjärrfilen kommer att hämtas helt på nytt. Detta är samma sak som att använda en **fil** utan att **återuppta**.

Om fjärrservern inte har stöd för hämtning återupptas kommer den lokala filen att skrivas över och hela fjärrfilen kommer att laddas ned på nytt. Detta är samma sak som att använda en **fil** utan att **återuppta**.

Om den lokala filen inte finns kommer den lokala filen att skapas och hela fjärrfilen laddas ned helt. Detta är samma sak som att använda en **fil** utan att **återuppta**.

Den här funktionen har lagts till i PowerShell-6.1.0.

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

### -RetryIntervalSec

Anger intervallet mellan återförsök för anslutningen när en felkod mellan 400 och 599, inklusive eller 304 tas emot. Se även **MaximumRetryCount** -parametern för att ange antal återförsök.

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

### -SessionVariable

Anger en variabel för vilken denna cmdlet skapar en Webbbegäran-session och sparar den i värdet.
Ange ett variabel namn utan dollar tecknet ( `$` )-symbolen.

När du anger en sessionsvariabel `Invoke-RestMethod` skapar ett sessionsobjekt för Webbbegäran och tilldelar det till en variabel med det angivna namnet i PowerShell-sessionen. Du kan använda variabeln i din session så snart kommandot har slutförts.

Till skillnad från en fjärran sluten session är inte Webbbegäran-sessionen en permanent anslutning. Det är ett objekt som innehåller information om anslutningen och begäran, inklusive cookies, autentiseringsuppgifter, det maximala värdet för omdirigering och användar agent strängen. Du kan använda den för att dela tillstånd och data mellan webb förfrågningar.

Om du vill använda Webbbegäran-sessionen i efterföljande webb förfrågningar, anger du variabeln session i värdet för **websession** -parametern. PowerShell använder data i objektet Webbbegäran-session när den nya anslutningen upprättas. Om du vill åsidosätta ett värde i Webbbegäran-sessionen använder du en cmdlet-parameter, till exempel **useragent** eller **Credential**. Parameter värden har företräde framför värden i Webbbegäran-sessionen.

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

### -SkipCertificateCheck

Hoppar över verifierings kontroller för certifikat som innehåller alla verifieringar som förfallo datum, återkallande, betrodd rot utfärdare osv.

> [!WARNING]
> Att använda den här parametern är inte säkert och rekommenderas inte. Den här växeln är endast avsedd att användas mot kända värdar med hjälp av ett självsignerat certifikat i testnings syfte. Använd på egen risk.

Den här funktionen har lagts till i PowerShell-6.0.0.

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

### -SkipHeaderValidation

Anger att cmdleten ska lägga till huvuden i begäran utan verifiering.

Den här växeln bör användas för platser som kräver rubrik värden som inte uppfyller standarder.
Om du anger den här växeln inaktive ras verifieringen så att värdet inte kan skickas avmarkerat. När det här värdet anges läggs alla rubriker till utan verifiering.

Då inaktive ras verifieringen för värden som skickas till parametrarna **ContentType** , **headers** och **useragent** .

Den här funktionen har lagts till i PowerShell-6.0.0.

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

### -SkipHttpErrorCheck

Den här parametern gör att cmdleten ignorerar HTTP-fel status och fortsätter att bearbeta svar.
Fel Svaren skrivs till pipelinen precis som om de lyckades.

Den här parametern introducerades i PowerShell 7.

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

### -SslProtocol

Anger de SSL/TLS-protokoll som är tillåtna för webbegäran. Som standard är alla SSL/TLS-protokoll som stöds av systemet tillåtna. **SslProtocol** gör det möjligt att begränsa till vissa protokoll för efterlevnad.

**SslProtocol** använder `WebSslProtocol` flaggan Enum. Det går att ange mer än ett protokoll med hjälp av flagg notation eller kombinera flera `WebSslProtocol` alternativ med `-bor` , men det finns inte stöd för att tillhandahålla flera protokoll på alla plattformar.

> [!NOTE]
> På andra plattformar än Windows-plattformar kanske det inte går att ange `'Tls, Tls12'` som ett alternativ.

Den här funktionen har lagts till i PowerShell-6.0.0.

```yaml
Type: Microsoft.PowerShell.Commands.WebSslProtocol
Parameter Sets: (All)
Aliases:
Accepted values: Default, Tls, Tls11, Tls12

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -StatusCodeVariable

Den här parametern anger en variabel som har tilldelats ett heltals värde för en status kod. Parametern kan identifiera lyckade meddelanden eller misslyckade meddelanden när de används med parametern **SkipHttpErrorCheck** .

Mata in parameterns variabel namn som en sträng, till exempel `-StatusCodeVariable "scv"` .

Den här parametern introducerades i PowerShell 7.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -TimeoutSec

Anger hur lång tid det tar att vänta på begäran innan den går ut. Ange ett värde i sekunder. Standardvärdet 0 anger en obestämd tids gräns.

En Domain Name System-fråga (DNS) kan ta upp till 15 sekunder att returnera eller ta slut för lång tid. Om din begäran innehåller ett värdnamn som kräver lösning och du anger **TimeoutSec** till ett värde som är större än noll, men mindre än 15 sekunder, kan det ta 15 sekunder eller mer innan en WebException utlöses, och tids gränsen för din begäran görs.

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

### -Token

OAuth-eller Bearer-token som ska ingå i begäran. **Token** krävs av vissa **autentiseringsalternativ** . Den kan inte användas separat.

**Token** tar en `SecureString` som innehåller token. Använd följande för att ange token:

`Invoke-RestMethod -Uri $uri -Authentication OAuth -Token (Read-Host -AsSecureString)`

Den här parametern introducerades i PowerShell 6,0.

```yaml
Type: System.Security.SecureString
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
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

Den här parametern är föråldrad. Från och med PowerShell-6.0.0 använder alla webbegäranden enbart grundläggande parsning. Den här parametern ingår endast för bakåtkompatibilitet och all användning av den kommer inte att påverka cmdletens funktion.

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

Anger att cmdleten använder autentiseringsuppgifterna för den aktuella användaren för att skicka webb förfrågan. Detta kan inte användas med **autentisering** eller **autentiseringsuppgifter** och stöds inte på alla plattformar.

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

Standard användar agenten liknar `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` med små variationer för varje operativ system och plattform.

Om du vill testa en webbplats med den standard användar agent sträng som används av de flesta webbläsare, använder du egenskaperna för [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) -klassen, till exempel Chrome, Firefox, InternetExplorer, Opera och Safari.

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

Om du vill åsidosätta ett värde i Webbbegäran-sessionen använder du en cmdlet-parameter, till exempel **useragent** eller **Credential**. Parameter värden har företräde framför värden i Webbbegäran-sessionen. Content-relaterade rubriker, till exempel `Content-Type` , kommer också att åsidosättas när ett **MultipartFormDataContent** -objekt anges för **brödtext**.

Till skillnad från en fjärran sluten session är inte Webbbegäran-sessionen en permanent anslutning. Det är ett objekt som innehåller information om anslutningen och begäran, inklusive cookies, autentiseringsuppgifter, det maximala värdet för omdirigering och användar agent strängen. Du kan använda den för att dela tillstånd och data mellan webb förfrågningar.

Om du vill skapa en Webbbegäran-session anger du ett variabel namn, utan dollar tecken, i värdet för parametern **SessionVariable** för ett `Invoke-RestMethod` kommando. `Invoke-RestMethod` skapar sessionen och sparar den i variabeln. I efterföljande kommandon använder du variabeln som värde för **websession** -parametern.

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

## INDATA

### System. Object

Du kan skicka vidare innehållet i en webb förfrågan till `Invoke-RestMethod` .

## UTDATA

### System. Int64, system. String, System.Xml.Xmldokument

Utdata från cmdleten beror på formatet på det innehåll som hämtas.

### PSObject

Om begäran returnerar JSON-strängar `Invoke-RestMethod` returnerar en **PSObject** som representerar strängarna.

## ANTECKNINGAR

Vissa funktioner kanske inte är tillgängliga på alla plattformar.

På grund av ändringar i .NET Core 3,1 använder PowerShell 7,0 och senare egenskapen [httpclient. DefaultProxy](/dotnet/api/system.net.http.httpclient.defaultproxy?view=netcore-3.1) för att fastställa proxykonfigurationen.

Värdet för den här egenskapen bestäms av din plattform:

- **För Windows** : läser proxykonfigurationen från miljövariabler. Om dessa variabler inte är definierade härleds egenskapen från användarens proxyinställningar.
- **För MacOS** : läser proxykonfigurationen från miljövariabler. Om dessa variabler inte är definierade härleds egenskapen från systemets proxyinställningar.
- **För Linux** : läser proxykonfigurationen från miljövariabler. Om dessa variabler inte är definierade initierar egenskapen en icke-konfigurerad instans som kringgår alla adresser.

De miljövariabler som används för `DefaultProxy` initiering på Windows-och UNIX-baserade plattformar är:

- ` HTTP_PROXY`: värd namnet eller IP-adressen för den proxyserver som används för HTTP-begäranden.
- `HTTPS_PROXY`: värd namnet eller IP-adressen för den proxyserver som används på HTTPS-begäranden.
- `ALL_PROXY`: värd namnet eller IP-adressen för proxyservern som används för HTTP-och HTTPS-begäranden i fall `HTTP_PROXY` eller `HTTPS_PROXY` som inte har definierats.
- `NO_PROXY`: en kommaavgränsad lista över värdnamn som ska undantas från proxy.

## RELATERADE LÄNKAR

[ConvertTo-Json](ConvertTo-Json.md)

[ConvertFrom – JSON](ConvertFrom-Json.md)

[Anropa-webbegäran](Invoke-WebRequest.md)
