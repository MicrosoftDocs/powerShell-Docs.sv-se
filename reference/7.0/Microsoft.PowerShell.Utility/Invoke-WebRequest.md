---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/26/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-webrequest?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WebRequest
ms.openlocfilehash: 07c10f33b0cffd56d84ddf6aab3553a0b71e4017
ms.sourcegitcommit: 11880ca974fe2df308191c9f6dcdfe0b89c2dc67
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/27/2021
ms.locfileid: "98860719"
---
# Invoke-WebRequest

## SAMMANFATTNING
Hämtar innehåll från en webb sida på Internet.

## SYNTAX

### StandardMethod (standard)

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>]
 [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] [-Method <WebRequestMethod>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### StandardMethodNoProxy

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>]
 [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] [-Method <WebRequestMethod>] -NoProxy
 [-Body <Object>] [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>]
 [-InFile <String>] [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck]
 [-PreserveAuthorizationOnRedirect] [-SkipHeaderValidation] [<CommonParameters>]
```

### CustomMethod

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>]
 [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] -CustomMethod <String> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### CustomMethodNoProxy

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>]
 [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] -CustomMethod <String> -NoProxy
 [-Body <Object>] [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>]
 [-InFile <String>] [-OutFile <String>] [-PassThru] [-Resume] [-SkipHttpErrorCheck]
 [-PreserveAuthorizationOnRedirect] [-SkipHeaderValidation] [<CommonParameters>]
```

## BESKRIVNING

`Invoke-WebRequest`Cmdlet: en skickar HTTP-och HTTPS-begäranden till en webb sida eller en webb tjänst. Den tolkar svaret och returnerar samlingar med länkar, bilder och andra viktiga HTML-element.

Denna cmdlet introducerades i PowerShell 3,0.

Från och med PowerShell 7,0 `Invoke-WebRequest` stöder proxykonfigurationen som definieras av miljövariabler. Se avsnittet [anteckningar](#notes) i den här artikeln.

## EXEMPEL

### Exempel 1: skicka en webb förfrågan

I det här exemplet används `Invoke-WebRequest` cmdleten för att skicka en webbegäran till Bing.com-webbplatsen.

```powershell
$Response = Invoke-WebRequest -URI https://www.bing.com/search?q=how+many+feet+in+a+mile
$Response.InputFields | Where-Object {
    $_.name -like "* Value*"
} | Select-Object Name, Value
```

```Output
name       value
----       -----
From Value 1
To Value   5280
```

Det första kommandot utfärdar begäran och sparar svaret i `$Response` variabeln.

Det andra kommandot hämtar alla **InputField** där **namn** -egenskapen är som `"* Value"` . De filtrerade resultaten är skickas för `Select-Object` att välja egenskaper för **namn** och **värde** .

### Exempel 2: använda en tillstånds känslig webb tjänst

Det här exemplet visar hur du använder `Invoke-WebRequest` cmdleten med en tillstånds känslig webb tjänst.

```powershell
$Body = @{
    User = 'jdoe'
    password = 'P@S$w0rd!'
}
$LoginResponse = Invoke-WebRequest 'https://www.contoso.com/login/' -SessionVariable 'Session' -Body $Body -Method 'POST'

$Session

$ProfileResponse = Invoke-WebRequest 'https://www.contoso.com/profile/' -WebSession $Session

$ProfileResponse
```

Det första anropet för att `Invoke-WebRequest` skicka en inloggnings förfrågan. Kommandot anger värdet "session" för värdet för parametern **-SessionVariable** och sparar resultatet i `$LoginResponse` variabeln. När kommandot har slutförts `$LoginResponse` innehåller variabeln en `BasicHtmlWebResponseObject` och `$Session` variabeln innehåller ett `WebRequestSession` objekt. Detta loggar användaren på platsen.

Anropet till `$Session` själva visar `WebRequestSession` objektet i variabeln.

Det andra anropet för att `Invoke-WebRequest` Hämta användarens profil som kräver att användaren är inloggad på platsen. De sessionsdata som lagras i `$Session` variabeln används för att tillhandahålla sessionscookies till den plats som skapas under inloggningen. Resultatet sparas i `$ProfileResponse` variabeln.

Anropet till `$ProfileResponse` själva visar `BasicHtmlWebResponseObject` i variabeln.

### Exempel 3: Hämta länkar från en webb sida

Det här exemplet hämtar länkarna på en webb sida. Den använder `Invoke-WebRequest` cmdleten för att hämta innehållet på webb sidan. Sedan använder den egenskapen **Links** för den `BasicHtmlWebResponseObject` som `Invoke-WebRequest` returnerar och egenskapen **href** för varje länk.

```powershell
(Invoke-WebRequest -Uri "https://aka.ms/pscore6-docs").Links.Href
```

### Exempel 4: skriver svars innehållet till en fil med hjälp av den kodning som definierats på den begärda sidan.

I det här exemplet används `Invoke-WebRequest` cmdleten för att hämta webb sidans innehåll på en PowerShell-dokumentations sida.

```powershell
$Response = Invoke-WebRequest -Uri "https://aka.ms/pscore6-docs"
$Stream = [System.IO.StreamWriter]::new('.\docspage.html', $false, $Response.Encoding)
try {
    $Stream.Write($Response.Content)
}
finally {
    $Stream.Dispose()
}
```

Det första kommandot hämtar sidan och sparar objektet Response i `$Response` variabeln.

Det andra kommandot skapar en `StreamWriter` som ska användas för att skriva svars innehållet till en fil. Egenskapen **encoding** för Response-objektet används för att ange filens kodning.

De slutliga kommandona skriver **innehålls** egenskapen till filen och tar sedan bort `StreamWriter` .

Observera att **encoding** -egenskapen är null om Webbbegäran inte returnerar text innehåll.

### Exempel 5: skicka en multipart-/formulär data fil

I det här exemplet används `Invoke-WebRequest` cmdleten Ladda upp en fil som ett `multipart/form-data` överförings objekt. Filen `c:\document.txt` skickas som ett formulär fält `document` med `Content-Type` för `text/plain` .

```powershell
$FilePath = 'c:\document.txt'
$FieldName = 'document'
$ContentType = 'text/plain'

$FileStream = [System.IO.FileStream]::new($filePath, [System.IO.FileMode]::Open)
$FileHeader = [System.Net.Http.Headers.ContentDispositionHeaderValue]::new('form-data')
$FileHeader.Name = $FieldName
$FileHeader.FileName = Split-Path -leaf $FilePath
$FileContent = [System.Net.Http.StreamContent]::new($FileStream)
$FileContent.Headers.ContentDisposition = $FileHeader
$FileContent.Headers.ContentType = [System.Net.Http.Headers.MediaTypeHeaderValue]::Parse($ContentType)

$MultipartContent = [System.Net.Http.MultipartFormDataContent]::new()
$MultipartContent.Add($FileContent)

$Response = Invoke-WebRequest -Body $MultipartContent -Method 'POST' -Uri 'https://api.contoso.com/upload'
```

### Exempel 6: överföring av förenklad multipart/form – data

Vissa API: er kräver att det går `multipart/form-data` att överföra filer och blandat innehåll. I det här exemplet visas hur du uppdaterar en användar profil.

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
$Result = Invoke-WebRequest -Uri $Uri -Method Post -Form $Form
```

Profil formuläret kräver följande fält:,,,, `firstName` `lastName` `email` `avatar` `birthday` och `hobbies` . API: et förväntar sig en bild för användar profils pic som ska anges i `avatar` fältet. API: et accepterar också `hobbies` att flera poster skickas i samma formulär.

När du skapar en `$Form` hash-tabellen används nyckel namnen som namn på formulär fält. Som standard konverteras värdena för hash-tabellen till strängar. Om det finns ett **system. io. fileinfo** -värde skickas filens innehåll. Om det finns en samling, till exempel matriser eller listor, skickas formulär fältet flera gånger.

Genom `Get-Item` att använda på `avatar` nyckeln `FileInfo` anges objektet som värde. Resultatet är att avbildnings data för `jdoe.png` skickas.

Om du anger en lista till `hobbies` nyckeln, finns `hobbies` fältet i under sändningarna en gång för varje List objekt.

### Exempel 7: fånga meddelanden som inte lyckades från Invoke-WebRequest

När `Invoke-WebRequest` påträffar ett HTTP-meddelande som inte lyckades (404, 500 osv.) returnerar det inga utdata och returnerar ett avslutande fel. Om du vill fånga felet och visa **StatusCode** kan du sätta igång i ett `try/catch` block.

```powershell
try
{
    $Response = Invoke-WebRequest -Uri "www.microsoft.com/unkownhost"
    # This will only execute if the Invoke-WebRequest is successful.
    $StatusCode = $Response.StatusCode
}
catch
{
    $StatusCode = $_.Exception.Response.StatusCode.value__
}
$StatusCode
```

```Output
404
```

Det avslutande felet fångas av `catch` blocket, som hämtar **StatusCode** från **Exception** -objektet.

## PARAMETRAR

### -AllowUnencryptedAuthentication

Tillåter sändning av autentiseringsuppgifter och hemligheter över okrypterade anslutningar. Som standard anger **Credential** eller valfritt **autentiseringsalternativ** med en **URI** som inte börjar med `https://` resulterar i ett fel och begäran avbryts för att förhindra oavsiktlig kommunikation av hemligheter i oformaterad text över okrypterade anslutningar. Om du vill åsidosätta det här beteendet på egen risk anger du parametern **AllowUnencryptedAuthentication** .

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

- **Ingen**: det här är standard alternativet när **autentisering** inte anges. ingen explicit autentisering används.
- **Basic**: kräver **autentiseringsuppgifter**. Autentiseringsuppgifterna skickas i ett RFC 7617 Basic Authentication-huvud i formatet `base64(user:password)` .
- **Bearer**: kräver **token**. Skickar ett RFC 6750- `Authorization: Bearer` huvud med angiven token. Detta är ett alias för **OAuth**
- **OAuth**: kräver **token**. Skickar ett RFC 6750- `Authorization: Bearer` huvud med angiven token. Detta är ett alias för **innehavare**

Att tillhandahålla **autentisering** åsidosätter alla `Authorization` rubriker som har angetts för **sidhuvuden** eller ingår i **websession**.

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
Du kan också skicka ett Body-värde till `Invoke-WebRequest` .

Du kan använda **text** parametern för att ange en lista över frågeparametrar eller ange svarets innehåll.

När indatamängden är en GET-begäran och texten är en `IDictionary` (vanligt vis en hash-tabell) läggs bröd texten till i URI: n som frågeparametrar. För andra typer av begär Anden (till exempel POST) anges bröd texten som värde för begär ande texten i `name=value` standardformat.

**Bröd text** parametern kan också acceptera ett `System.Net.Http.MultipartFormDataContent` objekt. Detta underlättar `multipart/form-data` förfrågningar. När ett **MultipartFormDataContent** -objekt anges för **brödtext**, åsidosätts alla innehåll relaterade rubriker som har angetts för egenskaperna **ContentType**, **headers** eller **websession** av **MultipartFormDataContent** -objektets innehålls rubriker. Den här funktionen har lagts till i PowerShell-6.0.0.

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

Om den här parametern utelämnas och metoden för begäran är POST, `Invoke-WebRequest` anger innehålls typen till `application/x-www-form-urlencoded` . Annars anges inte innehålls typen i anropet.

**ContentType** åsidosätts när ett **MultipartFormDataContent** -objekt anges för **brödtext**.

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

Ange ett användar namn, till exempel **user01** eller **Domain01\User01**, eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten.

**Autentiseringsuppgifter** kan användas separat eller tillsammans med vissa parametrar för **autentiseringsprinciper** . När den används enbart, anger den bara autentiseringsuppgifter för fjärrservern om fjärrservern skickar en begäran om autentisering av begäran. När den används med **autentiseringsalternativ** skickas autentiseringsuppgifterna uttryckligen.

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

Anger en anpassad metod som används för webb förfrågan. Detta kan användas om den begär ande metoden som krävs av slut punkten inte är ett tillgängligt alternativ för **metoden**. **Metoden** och **CustomMethod** kan inte användas tillsammans.

Det här exemplet gör en `TEST` http-begäran till API: et:

`Invoke-WebRequest -uri 'https://api.contoso.com/widget/' -CustomMethod 'TEST'`

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

Anger att cmdleten anger **keepalive** -värdet i HTTP-huvudet till **false**. **Keepalive** är som standard **Sant**. **Keepalive** upprättar en permanent anslutning till servern för att under lätta efterföljande begär Anden.

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

### -Form

Konverterar en ord lista till ett `multipart/form-data` överförings objekt. **Formulär** får inte användas med **brödtext**.
Om **ContentType** används ignoreras det.

Nycklarna i ord listan används som formulär fält namn. Som standard konverteras formulär värden till sträng värden.

Om värdet är ett **system. io. fileinfo** -objekt, skickas filen med binärfilen. Namnet på filen skickas in som **filename** -egenskapen. MIME-typen anges som `application/octet-stream` . `Get-Item` kan användas för att förenkla tillhandahålla **system. io. fileinfo** -objektet.

```powershell
$Form = @{
    resume = Get-Item 'c:\Users\jdoe\Documents\John Doe.pdf'
}
```

Om värdet är en samlings typ, sådana matriser eller listor skickas fältet for flera gånger.
Värdena i listan behandlas som strängar som standard. Om värdet är ett **system. io. fileinfo** -objekt, skickas filen med binärfilen. Kapslade samlingar stöds inte.

```powershell
$Form = @{
    tags     = 'Vacation', 'Italy', '2017'
    pictures = Get-ChildItem 'c:\Users\jdoe\Pictures\2017-Italy\'
}
```

I exemplet ovan `tags` anges fältet tre gånger i formuläret, en gång för var och en av `Vacation` , `Italy` och `2017` . `pictures`Fältet skickas också en gång för varje fil i `2017-Italy` mappen. Det binära innehållet i filerna i mappen skickas som värden.

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

Om du vill ange UserAgent-rubriker använder du parametern **useragent** . Du kan inte använda den här parametern för att ange **användar agent** eller cookie-rubriker.

Content-relaterade rubriker, som `Content-Type` åsidosätts när ett **MultipartFormDataContent** -objekt anges för **brödtext**.

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

Hämtar innehållet i webb förfrågan från en fil. Ange en sökväg och ett fil namn. Om du utelämnar sökvägen är standardvärdet den aktuella platsen.

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

Anger hur många gånger PowerShell omdirigerar en anslutning till en alternativ Uniform Resource Identifier (URI) innan anslutningen Miss lyckas. Standardvärdet är 5. Värdet 0 (noll) förhindrar all omdirigering.

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

- Standardvärde
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

Anger att cmdleten inte ska använda en proxy för att komma till målet. Använd den här växeln när du behöver kringgå proxyn som kon figurer ATS i miljön. Den här funktionen har lagts till i PowerShell-6.0.0.

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

Anger den utdatafil som denna cmdlet sparar svars texten för. Ange en sökväg och ett fil namn.
Om du utelämnar sökvägen är standardvärdet den aktuella platsen.

Som standard `Invoke-WebRequest` returnerar resultatet till pipelinen. Om du vill skicka resultatet till en fil och till pipelinen använder du parametern **Passthru** .

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

Anger att cmdleten returnerar resultatet, förutom att skriva dem till en fil. Den här parametern är endast giltig om **parametern out** också används i kommandot.

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

Anger en proxyserver för begäran, i stället för att ansluta direkt till Internet resursen.
Ange URI för en proxyserver för nätverket.

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

Ange ett användar namn, till exempel **user01** eller **Domain01\User01**, **User@Domain.Com** eller ange ett `PSCredential` objekt, till exempel en som genereras av `Get-Credential` cmdleten.

Den här parametern är endast giltig när parametern **proxy** också används i kommandot. Du kan inte använda parametrarna **ProxyCredential** och **ProxyUseDefaultCredentials** i samma kommando.

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: StandardMethod, CustomMethod
Aliases:

Required: False
Position: Named
Default value: Current user
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

### -Återuppta

Utför ett bästa försök att återuppta hämtningen av en delvis fil. **Återställningen** kräver en **fil**.

**Återuppta** fungerar bara på storleken på den lokala filen och fjärrfilen och utför ingen annan validering av att den lokala filen och fjärrfilen är desamma.

Om den lokala fil storleken är mindre än fjärrfils storleken försöker cmdleten återuppta nedladdningen av filen och lägga till återstående byte i slutet av filen.

Om den lokala fil storleken är samma som fjärrfilens storlek, utförs ingen åtgärd och cmdleten förutsätter att nedladdningen redan är slutförd.

Om den lokala fil storleken är större än fjärrfilens storlek, skrivs den lokala filen över och hela fjärrfilen laddas ned igen. Detta är samma sak som att använda en **fil** utan att **återuppta**.

Om fjärrservern inte stöder hämtnings återställning, skrivs den lokala filen över och hela fjärrfilen laddas ned igen. Detta är samma sak som att använda en **fil** utan att **återuppta**.

Om den lokala filen inte finns skapas den lokala filen och hela fjärrfilen laddas ned. Detta är samma sak som att använda en **fil** utan att **återuppta**.

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

När du anger en sessionsvariabel `Invoke-WebRequest` skapar ett sessionsobjekt för Webbbegäran och tilldelar det till en variabel med det angivna namnet i PowerShell-sessionen. Du kan använda variabeln i din session så snart kommandot har slutförts.

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

Hoppar över certifikat verifierings kontroller. Detta omfattar alla verifieringar som förfallo datum, åter kallelse, betrodd rot utfärdare osv.

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

Den här växeln inaktiverar verifiering av värden som skickas till parametrarna **ContentType**, **headers** och **useragent** .

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

**SslProtocol** använder **WebSslProtocol** -flaggan Enum. Det går att ange mer än ett protokoll med hjälp av flagg notation eller kombinera flera **WebSslProtocol** -alternativ med **bor**, men det finns inte stöd för att tillhandahålla flera protokoll på alla plattformar.

> [!NOTE]
> På andra plattformar än Windows-plattformar kanske det inte går att tillhandahålla `Tls` eller `Tls12` som ett alternativ.

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

### -TimeoutSec

Anger hur lång tid det tar att vänta på begäran innan den går ut. Ange ett värde i sekunder. Standardvärdet 0 anger en obestämd tids gräns.

En Domain Name System-fråga (DNS) kan ta upp till 15 sekunder att returnera eller ta slut för lång tid. Om din begäran innehåller ett värdnamn som kräver lösning och du anger **TimeoutSec** till ett värde som är större än noll, men mindre än 15 sekunder, kan det ta 15 sekunder eller mer innan en WebException utlöses, och tids gränsen för din begäran görs.

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

### -Token

OAuth-eller Bearer-token som ska ingå i begäran. **Token** krävs av vissa **autentiseringsalternativ** . Den kan inte användas separat.

**Token** tar en `SecureString` med token. Använd följande för att ange token manuellt:

`Invoke-WebRequest -Uri $uri -Authentication OAuth -Token (Read-Host -AsSecureString)`

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

Anger Uniform Resource Identifier (URI) för den Internet resurs som webb förfrågan skickas till. Ange en URI. Den här parametern stöder endast HTTP eller HTTPS.

Den här parametern är obligatorisk. Parameter namnet **URI** är valfritt.

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

Den här parametern är föråldrad. Från och med PowerShell-6.0.0 använder alla webbegäranden enbart grundläggande parsning. Den här parametern ingår endast för bakåtkompatibilitet och all användning av den har ingen påverkan på driften av cmdleten.

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

Följande kommando använder till exempel användar agent strängen för Internet Explorer:

```powershell
Invoke-WebRequest -Uri https://website.com/ -UserAgent ([Microsoft.PowerShell.Commands.PSUserAgent]::InternetExplorer)
```

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

Om du vill åsidosätta ett värde i Webbbegäran-sessionen använder du en cmdlet-parameter, till exempel **useragent** eller **Credential**. Parameter värden har företräde framför värden i Webbbegäran-sessionen. Content-relaterade rubriker, till exempel `Content-Type` , åsidosätts också när ett **MultipartFormDataContent** -objekt anges för **brödtext**.

Till skillnad från en fjärran sluten session är inte Webbbegäran-sessionen en permanent anslutning. Det är ett objekt som innehåller information om anslutningen och begäran, inklusive cookies, autentiseringsuppgifter, det maximala värdet för omdirigering och användar agent strängen. Du kan använda den för att dela tillstånd och data mellan webb förfrågningar.

Om du vill skapa en Webbbegäran-session anger du ett variabel namn, utan dollar tecken, i värdet för parametern **SessionVariable** för ett `Invoke-WebRequest` kommando. `Invoke-WebRequest` skapar sessionen och sparar den i variabeln. I efterföljande kommandon använder du variabeln som värde för **websession** -parametern.

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

Du kan skicka vidare innehållet i en webb förfrågan till `Invoke-WebRequest` .

## UTDATA

### Microsoft. PowerShell. commands. BasicHtmlWebResponseObject

## ANTECKNINGAR

Från och med PowerShell 6.0.0 `Invoke-WebRequest` har endast stöd för grundläggande tolkning.

Mer information finns i [BasicHtmlWebResponseObject](/dotnet/api/microsoft.powershell.commands.basichtmlwebresponseobject).

På grund av ändringar i .NET Core 3,1 använder PowerShell 7,0 och senare egenskapen [httpclient. DefaultProxy](/dotnet/api/system.net.http.httpclient.defaultproxy?view=netcore-3.1) för att fastställa proxykonfigurationen.

Värdet för den här egenskapen bestäms av din plattform:

- **För Windows**: läser proxykonfigurationen från miljövariabler. Om dessa variabler inte är definierade härleds egenskapen från användarens proxyinställningar.
- **För MacOS**: läser proxykonfigurationen från miljövariabler. Om dessa variabler inte är definierade härleds egenskapen från systemets proxyinställningar.
- **För Linux**: läser proxykonfigurationen från miljövariabler. Om dessa variabler inte är definierade initierar egenskapen en icke-konfigurerad instans som kringgår alla adresser.

De miljövariabler som används för `DefaultProxy` initiering på Windows-och UNIX-baserade plattformar är:

- ` HTTP_PROXY`: värd namnet eller IP-adressen för den proxyserver som används för HTTP-begäranden.
- `HTTPS_PROXY`: värd namnet eller IP-adressen för den proxyserver som används på HTTPS-begäranden.
- `ALL_PROXY`: värd namnet eller IP-adressen för proxyservern som används för HTTP-och HTTPS-begäranden i fall `HTTP_PROXY` eller `HTTPS_PROXY` som inte har definierats.
- `NO_PROXY`: en kommaavgränsad lista över värdnamn som ska undantas från proxy.

## RELATERADE LÄNKAR

[Invoke-RestMethod](Invoke-RestMethod.md)

[ConvertFrom – JSON](ConvertFrom-Json.md)

[ConvertTo-Json](ConvertTo-Json.md)
