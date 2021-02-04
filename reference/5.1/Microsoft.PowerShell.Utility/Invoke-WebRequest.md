---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/26/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-webrequest?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WebRequest
ms.openlocfilehash: f3545065d4879830a5051ef687f210c7fbd1251e
ms.sourcegitcommit: 11880ca974fe2df308191c9f6dcdfe0b89c2dc67
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/27/2021
ms.locfileid: "98860670"
---
# Invoke-WebRequest

## SAMMANFATTNING
Hämtar innehåll från en webb sida på Internet.

## SYNTAX

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>] [-SessionVariable <String>]
 [-Credential <PSCredential>] [-UseDefaultCredentials] [-CertificateThumbprint <String>]
 [-Certificate <X509Certificate>] [-UserAgent <String>] [-DisableKeepAlive] [-TimeoutSec <Int32>]
 [-Headers <IDictionary>] [-MaximumRedirection <Int32>] [-Method <WebRequestMethod>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>] [-ContentType <String>]
 [-TransferEncoding <String>] [-InFile <String>] [-OutFile <String>] [-PassThru] [<CommonParameters>]
```

## BESKRIVNING

`Invoke-WebRequest`Cmdleten skickar http-, https-, FTP-och fil begär anden till en webb sida eller en webb tjänst.
Den tolkar svaret och returnerar samlingar av formulär, länkar, bilder och andra viktiga HTML-element.

Den här cmdleten introducerades i Windows PowerShell 3,0.

> [!NOTE]
> Som standard kan skript kod på webb sidan köras när sidan parsas för att fylla i `ParsedHtml` egenskapen.
> Använd `-UseBasicParsing` växeln för att ignorera detta.

## EXEMPEL

### Exempel 1: skicka en webb förfrågan

Detta kommando använder `Invoke-WebRequest` cmdleten för att skicka en webbegäran till Bing.com-webbplatsen.

```powershell
$R = Invoke-WebRequest -URI https://www.bing.com?q=how+many+feet+in+a+mile
$R.AllElements | Where-Object {
    $_.name -like "* Value" -and $_.tagName -eq "INPUT"
} | Select-Object Name, Value
```

```Output
name       value
----       -----
From Value 1
To Value   5280
```

Det första kommandot utfärdar begäran och sparar svaret i `$R` variabeln.

Det andra kommandot filtrerar objekten i egenskapen **alleler** där egenskapen **namn** är som "* värde" och **TagName** är "inmatat". De filtrerade resultaten är skickas för `Select-Object` att välja egenskaper för **namn** och **värde** .

### Exempel 2: använda en tillstånds känslig webb tjänst

Det här exemplet visar hur du använder `Invoke-WebRequest` cmdleten med en tillstånds känslig webb tjänst, till exempel Facebook.

```powershell
$R = Invoke-WebRequest https://www.facebook.com/login.php -SessionVariable fb
# This command stores the first form in the Forms property of the $R variable in the $Form variable.
$Form = $R.Forms[0]
# This command shows the fields available in the Form.
$Form.fields
```

```Output
Key                     Value
---                     -----
...
email
pass
...
```

```powershell
# These commands populate the username and password of the respective Form fields.
$Form.Fields["email"]="User01@Fabrikam.com"
$Form.Fields["pass"]="P@ssw0rd"
# This command creates the Uri that will be used to log in to facebook.
# The value of the Uri parameter is the value of the Action property of the form.
$Uri = "https://www.facebook.com" + $Form.Action
# Now the Invoke-WebRequest cmdlet is used to sign into the Facebook web service.
# The WebRequestSession object in the $FB variable is passed as the value of the WebSession parameter.
# The value of the Body parameter is the hash table in the Fields property of the form.
# The value of the *Method* parameter is POST. The command saves the output in the $R variable.
$R = Invoke-WebRequest -Uri $Uri -WebSession $FB -Method POST -Body $Form.Fields
$R.StatusDescription
```

Det första kommandot använder `Invoke-WebRequest` cmdleten för att skicka en inloggnings förfrågan. Kommandot anger värdet "FB" för värdet för parametern **SessionVariable** och sparar resultatet i `$R` variabeln. När kommandot har slutförts `$R` innehåller variabeln en **HtmlWebResponseObject** och `$FB` variabeln innehåller ett **WebRequestSession** -objekt.

När `Invoke-WebRequest` cmdleten har loggat in på Facebook anger egenskapen **statusDescription** för objektet Web Response i `$R` variabeln att användaren har loggat in.

### Exempel 3: Hämta länkar från en webb sida

Det här kommandot hämtar länkarna på en webb sida.

```powershell
(Invoke-WebRequest -Uri "https://devblogs.microsoft.com/powershell/").Links.Href
```

`Invoke-WebRequest`Cmdleten hämtar webb sidans innehåll. Sedan används egenskapen **Links** för den returnerade **HtmlWebResponseObject** för att visa egenskapen **href** för varje länk.

### Exempel 4: fånga meddelanden som inte lyckades från Invoke-WebRequest

När `Invoke-WebRequest` påträffar ett HTTP-meddelande som inte lyckades (404, 500 osv.) returnerar det inga utdata och returnerar ett avslutande fel. Om du vill fånga felet och visa **StatusCode** kan du sätta igång i ett `try/catch` block. I följande exempel visas hur du kan göra detta.

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

### -Body

Anger bröd texten i begäran.
Bröd texten är innehållet i begäran som följer sidhuvuden.
Du kan också skicka ett Body-värde till `Invoke-WebRequest` .

Du kan använda **text** parametern för att ange en lista över frågeparametrar eller ange svarets innehåll.

När indatamängden är en GET-begäran och texten är en **IDictionary** (vanligt vis en hash-tabell), läggs bröd texten till i URI: n som frågeparametrar. För andra GET-begäranden anges bröd texten som värdet för begär ande texten i `name=value` standardformat.

När bröd texten är ett formulär, eller om det är utdata från ett `Invoke-WebRequest` anrop, anger PowerShell innehållet i formulär fälten.
Exempel:

`$r = Invoke-WebRequest https://website.com/login.aspx`
`$r.Forms\[0\].Name = "MyName"`
`$r.Forms\[0\].Password = "MyPassword"`
`Invoke-RestMethod https://website.com/service.aspx -Body $r`

- eller

`Invoke-RestMethod https://website.com/service.aspx -Body $r.Forms\[0\]`

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

Om du vill söka efter ett certifikat använder `Get-PfxCertificate` eller använder du `Get-ChildItem` cmdleten på **certifikat** `Cert:` enheten (). Om certifikatet inte är giltigt eller inte har tillräcklig behörighet, Miss lyckas kommandot.

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

Anger det digitala certifikat för offentlig nyckel (X509) för ett användar konto som har behörighet att skicka begäran. Ange certifikatets tumavtryck. Certifikat används i klient certifikat-baserad autentisering. De kan endast mappas till lokala användar konton. de fungerar inte med domän konton.

Om du vill hämta ett tumavtryck för certifikatet använder du `Get-Item` `Get-ChildItem` kommandot eller i PowerShell- `Cert:` enheten.

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

Om den här parametern utelämnas och metoden för begäran är POST, `Invoke-WebRequest` ställer in innehålls typen på Application/x-www-form-urlencoded. Annars anges inte innehålls typen i anropet.

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

Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).

> [!NOTE]
> Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).

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

### – Sidhuvud

Anger webb begärans rubriker. Ange en hash-tabell eller-ord lista.

Om du vill ange **useragent** -rubriker använder du parametern **useragent** . Du kan inte använda den här parametern för att ange **useragent** -eller cookie-rubriker.

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

```yaml
Type: Microsoft.PowerShell.Commands.WebRequestMethod
Parameter Sets: (All)
Aliases:
Accepted values: Default, Get, Head, Post, Put, Delete, Trace, Options, Merge, Patch

Required: False
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

### -Proxy

Anger en proxyserver för begäran, i stället för att ansluta direkt till Internet resursen.
Ange URI för en proxyserver för nätverket.

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

Ange ett användar namn, till exempel `User01` eller `Domain01\User01` , eller ange ett **PSCredential** -objekt, till exempel en som genereras av `Get-Credential` cmdleten.

Den här parametern är endast giltig när parametern **proxy** också används i kommandot. Du kan inte använda parametrarna **ProxyCredential** och **ProxyUseDefaultCredentials** i samma kommando.

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

### -ProxyUseDefaultCredentials

Anger att cmdleten använder autentiseringsuppgifterna för den aktuella användaren för att få åtkomst till proxyservern som anges av parametern **proxy** .

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

### -TimeoutSec

Anger hur lång tid det tar att vänta på begäran innan den går ut. Ange ett värde i sekunder. Standardvärdet 0 anger en obestämd tids gräns.

En Domain Name System-fråga (DNS) kan ta upp till 15 sekunder att returnera eller ta slut för lång tid. Om din begäran innehåller ett värdnamn som kräver lösning och du anger **TimeoutSec** till ett värde som är större än noll, men mindre än 15 sekunder, kan det ta 15 sekunder eller mer innan en **WebException** utlöses, och tids gränsen för din begäran görs.

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

Anger Uniform Resource Identifier (URI) för den Internet resurs som webb förfrågan skickas till. Ange en URI. Den här parametern stöder HTTP-, HTTPS-, FTP-och fil värden.

Den här parametern är obligatorisk.

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

Anger att cmdleten använder Response-objektet för HTML-innehåll utan Document Object Model (DOM) parsing. Den här parametern krävs när Internet Explorer inte är installerat på datorerna, t. ex. på en Server Core-installation av ett Windows Server-operativsystem.

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

Anger att cmDet använder autentiseringsuppgifterna för den aktuella användaren för att skicka webb förfrågan.

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

Anger en användar agent sträng för webb förfrågan. Standard användar agenten liknar `Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0` med små variationer för varje operativ system och plattform.

Om du vill testa en webbplats med den standard användar agent sträng som används av de flesta webbläsare, använder du egenskaperna för [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) -klassen, till exempel Chrome, Firefox, InternetExplorer, Opera och Safari. Följande kommando använder till exempel användar agent strängen för Internet Explorer

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

Om du vill skapa en Webbbegäran-session anger du ett variabel namn (utan dollar tecken) i värdet för parametern **SessionVariable** för ett `Invoke-WebRequest` kommando. `Invoke-WebRequest` skapar sessionen och sparar den i variabeln. I efterföljande kommandon använder du variabeln som värde för **websession** -parametern.

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

Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` . Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Object

Du kan skicka vidare innehållet i en webb förfrågan till `Invoke-WebRequest` .

## UTDATA

### Microsoft.PowerShell.Commands.HtmlWebResponseObject

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Invoke-RestMethod](Invoke-RestMethod.md)

[ConvertFrom – JSON](ConvertFrom-Json.md)

[ConvertTo-Json](ConvertTo-Json.md)
