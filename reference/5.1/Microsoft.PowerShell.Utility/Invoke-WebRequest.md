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
# <span data-ttu-id="4c316-102">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="4c316-102">Invoke-WebRequest</span></span>

## <span data-ttu-id="4c316-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="4c316-103">SYNOPSIS</span></span>
<span data-ttu-id="4c316-104">Hämtar innehåll från en webb sida på Internet.</span><span class="sxs-lookup"><span data-stu-id="4c316-104">Gets content from a web page on the Internet.</span></span>

## <span data-ttu-id="4c316-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4c316-105">SYNTAX</span></span>

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>] [-SessionVariable <String>]
 [-Credential <PSCredential>] [-UseDefaultCredentials] [-CertificateThumbprint <String>]
 [-Certificate <X509Certificate>] [-UserAgent <String>] [-DisableKeepAlive] [-TimeoutSec <Int32>]
 [-Headers <IDictionary>] [-MaximumRedirection <Int32>] [-Method <WebRequestMethod>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>] [-ContentType <String>]
 [-TransferEncoding <String>] [-InFile <String>] [-OutFile <String>] [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="4c316-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="4c316-106">DESCRIPTION</span></span>

<span data-ttu-id="4c316-107">`Invoke-WebRequest`Cmdleten skickar http-, https-, FTP-och fil begär anden till en webb sida eller en webb tjänst.</span><span class="sxs-lookup"><span data-stu-id="4c316-107">The `Invoke-WebRequest` cmdlet sends HTTP, HTTPS, FTP, and FILE requests to a web page or web service.</span></span>
<span data-ttu-id="4c316-108">Den tolkar svaret och returnerar samlingar av formulär, länkar, bilder och andra viktiga HTML-element.</span><span class="sxs-lookup"><span data-stu-id="4c316-108">It parses the response and returns collections of forms, links, images, and other significant HTML elements.</span></span>

<span data-ttu-id="4c316-109">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="4c316-109">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="4c316-110">Som standard kan skript kod på webb sidan köras när sidan parsas för att fylla i `ParsedHtml` egenskapen.</span><span class="sxs-lookup"><span data-stu-id="4c316-110">By default, script code in the web page may be run when the page is being parsed to populate the `ParsedHtml` property.</span></span>
> <span data-ttu-id="4c316-111">Använd `-UseBasicParsing` växeln för att ignorera detta.</span><span class="sxs-lookup"><span data-stu-id="4c316-111">Use the `-UseBasicParsing` switch to suppress this.</span></span>

## <span data-ttu-id="4c316-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="4c316-112">EXAMPLES</span></span>

### <span data-ttu-id="4c316-113">Exempel 1: skicka en webb förfrågan</span><span class="sxs-lookup"><span data-stu-id="4c316-113">Example 1: Send a web request</span></span>

<span data-ttu-id="4c316-114">Detta kommando använder `Invoke-WebRequest` cmdleten för att skicka en webbegäran till Bing.com-webbplatsen.</span><span class="sxs-lookup"><span data-stu-id="4c316-114">This command uses the `Invoke-WebRequest` cmdlet to send a web request to the Bing.com site.</span></span>

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

<span data-ttu-id="4c316-115">Det första kommandot utfärdar begäran och sparar svaret i `$R` variabeln.</span><span class="sxs-lookup"><span data-stu-id="4c316-115">The first command issues the request and saves the response in the `$R` variable.</span></span>

<span data-ttu-id="4c316-116">Det andra kommandot filtrerar objekten i egenskapen **alleler** där egenskapen **namn** är som "\* värde" och **TagName** är "inmatat".</span><span class="sxs-lookup"><span data-stu-id="4c316-116">The second command filters the objects in the **AllElements** property where the **name** property is like "\* Value" and the **tagName** is "INPUT".</span></span> <span data-ttu-id="4c316-117">De filtrerade resultaten är skickas för `Select-Object` att välja egenskaper för **namn** och **värde** .</span><span class="sxs-lookup"><span data-stu-id="4c316-117">The filtered results are piped to `Select-Object` to select the **name** and **value** properties.</span></span>

### <span data-ttu-id="4c316-118">Exempel 2: använda en tillstånds känslig webb tjänst</span><span class="sxs-lookup"><span data-stu-id="4c316-118">Example 2: Use a stateful web service</span></span>

<span data-ttu-id="4c316-119">Det här exemplet visar hur du använder `Invoke-WebRequest` cmdleten med en tillstånds känslig webb tjänst, till exempel Facebook.</span><span class="sxs-lookup"><span data-stu-id="4c316-119">This example shows how to use the `Invoke-WebRequest` cmdlet with a stateful web service, such as Facebook.</span></span>

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

<span data-ttu-id="4c316-120">Det första kommandot använder `Invoke-WebRequest` cmdleten för att skicka en inloggnings förfrågan.</span><span class="sxs-lookup"><span data-stu-id="4c316-120">The first command uses the `Invoke-WebRequest` cmdlet to send a sign-in request.</span></span> <span data-ttu-id="4c316-121">Kommandot anger värdet "FB" för värdet för parametern **SessionVariable** och sparar resultatet i `$R` variabeln.</span><span class="sxs-lookup"><span data-stu-id="4c316-121">The command specifies a value of "FB" for the value of the **SessionVariable** parameter, and saves the result in the `$R` variable.</span></span> <span data-ttu-id="4c316-122">När kommandot har slutförts `$R` innehåller variabeln en **HtmlWebResponseObject** och `$FB` variabeln innehåller ett **WebRequestSession** -objekt.</span><span class="sxs-lookup"><span data-stu-id="4c316-122">When the command completes, the `$R` variable contains an **HtmlWebResponseObject** and the `$FB` variable contains a **WebRequestSession** object.</span></span>

<span data-ttu-id="4c316-123">När `Invoke-WebRequest` cmdleten har loggat in på Facebook anger egenskapen **statusDescription** för objektet Web Response i `$R` variabeln att användaren har loggat in.</span><span class="sxs-lookup"><span data-stu-id="4c316-123">After the `Invoke-WebRequest` cmdlet signs in to facebook, the **StatusDescription** property of the web response object in the `$R` variable indicates that the user is signed in successfully.</span></span>

### <span data-ttu-id="4c316-124">Exempel 3: Hämta länkar från en webb sida</span><span class="sxs-lookup"><span data-stu-id="4c316-124">Example 3: Get links from a web page</span></span>

<span data-ttu-id="4c316-125">Det här kommandot hämtar länkarna på en webb sida.</span><span class="sxs-lookup"><span data-stu-id="4c316-125">This command gets the links in a web page.</span></span>

```powershell
(Invoke-WebRequest -Uri "https://devblogs.microsoft.com/powershell/").Links.Href
```

<span data-ttu-id="4c316-126">`Invoke-WebRequest`Cmdleten hämtar webb sidans innehåll.</span><span class="sxs-lookup"><span data-stu-id="4c316-126">The `Invoke-WebRequest` cmdlet gets the web page content.</span></span> <span data-ttu-id="4c316-127">Sedan används egenskapen **Links** för den returnerade **HtmlWebResponseObject** för att visa egenskapen **href** för varje länk.</span><span class="sxs-lookup"><span data-stu-id="4c316-127">Then the **Links** property of the returned **HtmlWebResponseObject** is used to display the **Href** property of each link.</span></span>

### <span data-ttu-id="4c316-128">Exempel 4: fånga meddelanden som inte lyckades från Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="4c316-128">Example 4: Catch non success messages from Invoke-WebRequest</span></span>

<span data-ttu-id="4c316-129">När `Invoke-WebRequest` påträffar ett HTTP-meddelande som inte lyckades (404, 500 osv.) returnerar det inga utdata och returnerar ett avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="4c316-129">When `Invoke-WebRequest` encounters a non-success HTTP message (404, 500, etc.), it returns no output and throws a terminating error.</span></span> <span data-ttu-id="4c316-130">Om du vill fånga felet och visa **StatusCode** kan du sätta igång i ett `try/catch` block.</span><span class="sxs-lookup"><span data-stu-id="4c316-130">To catch the error and view the **StatusCode** you can enclose execution in a `try/catch` block.</span></span> <span data-ttu-id="4c316-131">I följande exempel visas hur du kan göra detta.</span><span class="sxs-lookup"><span data-stu-id="4c316-131">The following example shows how to accomplish this.</span></span>

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

<span data-ttu-id="4c316-132">Det avslutande felet fångas av `catch` blocket, som hämtar **StatusCode** från **Exception** -objektet.</span><span class="sxs-lookup"><span data-stu-id="4c316-132">The terminating error is caught by the `catch` block, which retrieves the **StatusCode** from the **Exception** object.</span></span>

## <span data-ttu-id="4c316-133">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="4c316-133">PARAMETERS</span></span>

### <span data-ttu-id="4c316-134">-Body</span><span class="sxs-lookup"><span data-stu-id="4c316-134">-Body</span></span>

<span data-ttu-id="4c316-135">Anger bröd texten i begäran.</span><span class="sxs-lookup"><span data-stu-id="4c316-135">Specifies the body of the request.</span></span>
<span data-ttu-id="4c316-136">Bröd texten är innehållet i begäran som följer sidhuvuden.</span><span class="sxs-lookup"><span data-stu-id="4c316-136">The body is the content of the request that follows the headers.</span></span>
<span data-ttu-id="4c316-137">Du kan också skicka ett Body-värde till `Invoke-WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="4c316-137">You can also pipe a body value to `Invoke-WebRequest`.</span></span>

<span data-ttu-id="4c316-138">Du kan använda **text** parametern för att ange en lista över frågeparametrar eller ange svarets innehåll.</span><span class="sxs-lookup"><span data-stu-id="4c316-138">The **Body** parameter can be used to specify a list of query parameters or specify the content of the response.</span></span>

<span data-ttu-id="4c316-139">När indatamängden är en GET-begäran och texten är en **IDictionary** (vanligt vis en hash-tabell), läggs bröd texten till i URI: n som frågeparametrar.</span><span class="sxs-lookup"><span data-stu-id="4c316-139">When the input is a GET request and the body is an **IDictionary** (typically, a hash table), the body is added to the URI as query parameters.</span></span> <span data-ttu-id="4c316-140">För andra GET-begäranden anges bröd texten som värdet för begär ande texten i `name=value` standardformat.</span><span class="sxs-lookup"><span data-stu-id="4c316-140">For other GET requests, the body is set as the value of the request body in the standard `name=value` format.</span></span>

<span data-ttu-id="4c316-141">När bröd texten är ett formulär, eller om det är utdata från ett `Invoke-WebRequest` anrop, anger PowerShell innehållet i formulär fälten.</span><span class="sxs-lookup"><span data-stu-id="4c316-141">When the body is a form, or it is the output of an `Invoke-WebRequest` call, PowerShell sets the request content to the form fields.</span></span>
<span data-ttu-id="4c316-142">Exempel:</span><span class="sxs-lookup"><span data-stu-id="4c316-142">For example:</span></span>

`$r = Invoke-WebRequest https://website.com/login.aspx`
`$r.Forms\[0\].Name = "MyName"`
`$r.Forms\[0\].Password = "MyPassword"`
`Invoke-RestMethod https://website.com/service.aspx -Body $r`

- <span data-ttu-id="4c316-143">eller</span><span class="sxs-lookup"><span data-stu-id="4c316-143">or -</span></span>

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

### <span data-ttu-id="4c316-144">– Certifikat</span><span class="sxs-lookup"><span data-stu-id="4c316-144">-Certificate</span></span>

<span data-ttu-id="4c316-145">Anger det klient certifikat som används för en säker webb förfrågan.</span><span class="sxs-lookup"><span data-stu-id="4c316-145">Specifies the client certificate that is used for a secure web request.</span></span> <span data-ttu-id="4c316-146">Ange en variabel som innehåller ett certifikat eller ett kommando eller uttryck som hämtar certifikatet.</span><span class="sxs-lookup"><span data-stu-id="4c316-146">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="4c316-147">Om du vill söka efter ett certifikat använder `Get-PfxCertificate` eller använder du `Get-ChildItem` cmdleten på **certifikat** `Cert:` enheten ().</span><span class="sxs-lookup"><span data-stu-id="4c316-147">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the **Certificate** (`Cert:`) drive.</span></span> <span data-ttu-id="4c316-148">Om certifikatet inte är giltigt eller inte har tillräcklig behörighet, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="4c316-148">If the certificate is not valid or does not have sufficient authority, the command fails.</span></span>

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

### <span data-ttu-id="4c316-149">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="4c316-149">-CertificateThumbprint</span></span>

<span data-ttu-id="4c316-150">Anger det digitala certifikat för offentlig nyckel (X509) för ett användar konto som har behörighet att skicka begäran.</span><span class="sxs-lookup"><span data-stu-id="4c316-150">Specifies the digital public key certificate (X509) of a user account that has permission to send the request.</span></span> <span data-ttu-id="4c316-151">Ange certifikatets tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="4c316-151">Enter the certificate thumbprint of the certificate.</span></span> <span data-ttu-id="4c316-152">Certifikat används i klient certifikat-baserad autentisering.</span><span class="sxs-lookup"><span data-stu-id="4c316-152">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="4c316-153">De kan endast mappas till lokala användar konton. de fungerar inte med domän konton.</span><span class="sxs-lookup"><span data-stu-id="4c316-153">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="4c316-154">Om du vill hämta ett tumavtryck för certifikatet använder du `Get-Item` `Get-ChildItem` kommandot eller i PowerShell- `Cert:` enheten.</span><span class="sxs-lookup"><span data-stu-id="4c316-154">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the PowerShell `Cert:` drive.</span></span>

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

### <span data-ttu-id="4c316-155">-ContentType</span><span class="sxs-lookup"><span data-stu-id="4c316-155">-ContentType</span></span>

<span data-ttu-id="4c316-156">Anger webb begärans innehålls typ.</span><span class="sxs-lookup"><span data-stu-id="4c316-156">Specifies the content type of the web request.</span></span>

<span data-ttu-id="4c316-157">Om den här parametern utelämnas och metoden för begäran är POST, `Invoke-WebRequest` ställer in innehålls typen på Application/x-www-form-urlencoded.</span><span class="sxs-lookup"><span data-stu-id="4c316-157">If this parameter is omitted and the request method is POST, `Invoke-WebRequest` sets the content type to application/x-www-form-urlencoded.</span></span> <span data-ttu-id="4c316-158">Annars anges inte innehålls typen i anropet.</span><span class="sxs-lookup"><span data-stu-id="4c316-158">Otherwise, the content type is not specified in the call.</span></span>

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

### <span data-ttu-id="4c316-159">-Credential</span><span class="sxs-lookup"><span data-stu-id="4c316-159">-Credential</span></span>

<span data-ttu-id="4c316-160">Anger ett användar konto som har behörighet att skicka begäran.</span><span class="sxs-lookup"><span data-stu-id="4c316-160">Specifies a user account that has permission to send the request.</span></span> <span data-ttu-id="4c316-161">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="4c316-161">The default is the current user.</span></span>

<span data-ttu-id="4c316-162">Ange ett användar namn, till exempel **user01** eller **Domain01\User01**, eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4c316-162">Type a user name, such as **User01** or **Domain01\User01**, or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="4c316-163">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="4c316-163">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="4c316-164">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="4c316-164">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="4c316-165">-DisableKeepAlive</span><span class="sxs-lookup"><span data-stu-id="4c316-165">-DisableKeepAlive</span></span>

<span data-ttu-id="4c316-166">Anger att cmdleten anger **keepalive** -värdet i HTTP-huvudet till **false**.</span><span class="sxs-lookup"><span data-stu-id="4c316-166">Indicates that the cmdlet sets the **KeepAlive** value in the HTTP header to **False**.</span></span> <span data-ttu-id="4c316-167">**Keepalive** är som standard **Sant**.</span><span class="sxs-lookup"><span data-stu-id="4c316-167">By default, **KeepAlive** is **True**.</span></span> <span data-ttu-id="4c316-168">**Keepalive** upprättar en permanent anslutning till servern för att under lätta efterföljande begär Anden.</span><span class="sxs-lookup"><span data-stu-id="4c316-168">**KeepAlive** establishes a persistent connection to the server to facilitate subsequent requests.</span></span>

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

### <span data-ttu-id="4c316-169">– Sidhuvud</span><span class="sxs-lookup"><span data-stu-id="4c316-169">-Headers</span></span>

<span data-ttu-id="4c316-170">Anger webb begärans rubriker.</span><span class="sxs-lookup"><span data-stu-id="4c316-170">Specifies the headers of the web request.</span></span> <span data-ttu-id="4c316-171">Ange en hash-tabell eller-ord lista.</span><span class="sxs-lookup"><span data-stu-id="4c316-171">Enter a hash table or dictionary.</span></span>

<span data-ttu-id="4c316-172">Om du vill ange **useragent** -rubriker använder du parametern **useragent** .</span><span class="sxs-lookup"><span data-stu-id="4c316-172">To set **UserAgent** headers, use the **UserAgent** parameter.</span></span> <span data-ttu-id="4c316-173">Du kan inte använda den här parametern för att ange **useragent** -eller cookie-rubriker.</span><span class="sxs-lookup"><span data-stu-id="4c316-173">You cannot use this parameter to specify **UserAgent** or cookie headers.</span></span>

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

### <span data-ttu-id="4c316-174">-INFILE</span><span class="sxs-lookup"><span data-stu-id="4c316-174">-InFile</span></span>

<span data-ttu-id="4c316-175">Hämtar innehållet i webb förfrågan från en fil.</span><span class="sxs-lookup"><span data-stu-id="4c316-175">Gets the content of the web request from a file.</span></span>

<span data-ttu-id="4c316-176">Ange en sökväg och ett fil namn.</span><span class="sxs-lookup"><span data-stu-id="4c316-176">Enter a path and file name.</span></span> <span data-ttu-id="4c316-177">Om du utelämnar sökvägen är standardvärdet den aktuella platsen.</span><span class="sxs-lookup"><span data-stu-id="4c316-177">If you omit the path, the default is the current location.</span></span>

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

### <span data-ttu-id="4c316-178">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="4c316-178">-MaximumRedirection</span></span>

<span data-ttu-id="4c316-179">Anger hur många gånger PowerShell omdirigerar en anslutning till en alternativ Uniform Resource Identifier (URI) innan anslutningen Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="4c316-179">Specifies how many times PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="4c316-180">Standardvärdet är 5.</span><span class="sxs-lookup"><span data-stu-id="4c316-180">The default value is 5.</span></span> <span data-ttu-id="4c316-181">Värdet 0 (noll) förhindrar all omdirigering.</span><span class="sxs-lookup"><span data-stu-id="4c316-181">A value of 0 (zero) prevents all redirection.</span></span>

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

### <span data-ttu-id="4c316-182">-Metod</span><span class="sxs-lookup"><span data-stu-id="4c316-182">-Method</span></span>

<span data-ttu-id="4c316-183">Anger den metod som används för webb förfrågan.</span><span class="sxs-lookup"><span data-stu-id="4c316-183">Specifies the method used for the web request.</span></span> <span data-ttu-id="4c316-184">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="4c316-184">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="4c316-185">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="4c316-185">Default</span></span>
- <span data-ttu-id="4c316-186">Ta bort</span><span class="sxs-lookup"><span data-stu-id="4c316-186">Delete</span></span>
- <span data-ttu-id="4c316-187">Hämta</span><span class="sxs-lookup"><span data-stu-id="4c316-187">Get</span></span>
- <span data-ttu-id="4c316-188">Head</span><span class="sxs-lookup"><span data-stu-id="4c316-188">Head</span></span>
- <span data-ttu-id="4c316-189">Sammanfoga</span><span class="sxs-lookup"><span data-stu-id="4c316-189">Merge</span></span>
- <span data-ttu-id="4c316-190">Alternativ</span><span class="sxs-lookup"><span data-stu-id="4c316-190">Options</span></span>
- <span data-ttu-id="4c316-191">Patch</span><span class="sxs-lookup"><span data-stu-id="4c316-191">Patch</span></span>
- <span data-ttu-id="4c316-192">Skicka</span><span class="sxs-lookup"><span data-stu-id="4c316-192">Post</span></span>
- <span data-ttu-id="4c316-193">Placera</span><span class="sxs-lookup"><span data-stu-id="4c316-193">Put</span></span>
- <span data-ttu-id="4c316-194">Spårning</span><span class="sxs-lookup"><span data-stu-id="4c316-194">Trace</span></span>

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

### <span data-ttu-id="4c316-195">-Fil</span><span class="sxs-lookup"><span data-stu-id="4c316-195">-OutFile</span></span>

<span data-ttu-id="4c316-196">Anger den utdatafil som denna cmdlet sparar svars texten för.</span><span class="sxs-lookup"><span data-stu-id="4c316-196">Specifies the output file for which this cmdlet saves the response body.</span></span> <span data-ttu-id="4c316-197">Ange en sökväg och ett fil namn.</span><span class="sxs-lookup"><span data-stu-id="4c316-197">Enter a path and file name.</span></span>
<span data-ttu-id="4c316-198">Om du utelämnar sökvägen är standardvärdet den aktuella platsen.</span><span class="sxs-lookup"><span data-stu-id="4c316-198">If you omit the path, the default is the current location.</span></span>

<span data-ttu-id="4c316-199">Som standard `Invoke-WebRequest` returnerar resultatet till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="4c316-199">By default, `Invoke-WebRequest` returns the results to the pipeline.</span></span> <span data-ttu-id="4c316-200">Om du vill skicka resultatet till en fil och till pipelinen använder du parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="4c316-200">To send the results to a file and to the pipeline, use the **Passthru** parameter.</span></span>

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

### <span data-ttu-id="4c316-201">– PassThru</span><span class="sxs-lookup"><span data-stu-id="4c316-201">-PassThru</span></span>

<span data-ttu-id="4c316-202">Anger att cmdleten returnerar resultatet, förutom att skriva dem till en fil.</span><span class="sxs-lookup"><span data-stu-id="4c316-202">Indicates that the cmdlet returns the results, in addition to writing them to a file.</span></span> <span data-ttu-id="4c316-203">Den här parametern är endast giltig om **parametern out** också används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="4c316-203">This parameter is valid only when the **OutFile** parameter is also used in the command.</span></span>

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

### <span data-ttu-id="4c316-204">-Proxy</span><span class="sxs-lookup"><span data-stu-id="4c316-204">-Proxy</span></span>

<span data-ttu-id="4c316-205">Anger en proxyserver för begäran, i stället för att ansluta direkt till Internet resursen.</span><span class="sxs-lookup"><span data-stu-id="4c316-205">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>
<span data-ttu-id="4c316-206">Ange URI för en proxyserver för nätverket.</span><span class="sxs-lookup"><span data-stu-id="4c316-206">Enter the URI of a network proxy server.</span></span>

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

### <span data-ttu-id="4c316-207">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="4c316-207">-ProxyCredential</span></span>

<span data-ttu-id="4c316-208">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="4c316-208">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span> <span data-ttu-id="4c316-209">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="4c316-209">The default is the current user.</span></span>

<span data-ttu-id="4c316-210">Ange ett användar namn, till exempel `User01` eller `Domain01\User01` , eller ange ett **PSCredential** -objekt, till exempel en som genereras av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4c316-210">Type a user name, such as `User01` or `Domain01\User01`, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="4c316-211">Den här parametern är endast giltig när parametern **proxy** också används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="4c316-211">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="4c316-212">Du kan inte använda parametrarna **ProxyCredential** och **ProxyUseDefaultCredentials** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="4c316-212">You cannot use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="4c316-213">-ProxyUseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="4c316-213">-ProxyUseDefaultCredentials</span></span>

<span data-ttu-id="4c316-214">Anger att cmdleten använder autentiseringsuppgifterna för den aktuella användaren för att få åtkomst till proxyservern som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="4c316-214">Indicates that the cmdlet uses the credentials of the current user to access the proxy server that is specified by the **Proxy** parameter.</span></span>

<span data-ttu-id="4c316-215">Den här parametern är endast giltig när parametern **proxy** också används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="4c316-215">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="4c316-216">Du kan inte använda parametrarna **ProxyCredential** och **ProxyUseDefaultCredentials** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="4c316-216">You cannot use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="4c316-217">-SessionVariable</span><span class="sxs-lookup"><span data-stu-id="4c316-217">-SessionVariable</span></span>

<span data-ttu-id="4c316-218">Anger en variabel för vilken denna cmdlet skapar en Webbbegäran-session och sparar den i värdet.</span><span class="sxs-lookup"><span data-stu-id="4c316-218">Specifies a variable for which this cmdlet creates a web request session and saves it in the value.</span></span>
<span data-ttu-id="4c316-219">Ange ett variabel namn utan dollar tecknet ( `$` )-symbolen.</span><span class="sxs-lookup"><span data-stu-id="4c316-219">Enter a variable name without the dollar sign (`$`) symbol.</span></span>

<span data-ttu-id="4c316-220">När du anger en sessionsvariabel `Invoke-WebRequest` skapar ett sessionsobjekt för Webbbegäran och tilldelar det till en variabel med det angivna namnet i PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="4c316-220">When you specify a session variable, `Invoke-WebRequest` creates a web request session object and assigns it to a variable with the specified name in your PowerShell session.</span></span> <span data-ttu-id="4c316-221">Du kan använda variabeln i din session så snart kommandot har slutförts.</span><span class="sxs-lookup"><span data-stu-id="4c316-221">You can use the variable in your session as soon as the command completes.</span></span>

<span data-ttu-id="4c316-222">Till skillnad från en fjärran sluten session är inte Webbbegäran-sessionen en permanent anslutning.</span><span class="sxs-lookup"><span data-stu-id="4c316-222">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="4c316-223">Det är ett objekt som innehåller information om anslutningen och begäran, inklusive cookies, autentiseringsuppgifter, det maximala värdet för omdirigering och användar agent strängen.</span><span class="sxs-lookup"><span data-stu-id="4c316-223">It is an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="4c316-224">Du kan använda den för att dela tillstånd och data mellan webb förfrågningar.</span><span class="sxs-lookup"><span data-stu-id="4c316-224">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="4c316-225">Om du vill använda Webbbegäran-sessionen i efterföljande webb förfrågningar, anger du variabeln session i värdet för **websession** -parametern.</span><span class="sxs-lookup"><span data-stu-id="4c316-225">To use the web request session in subsequent web requests, specify the session variable in the value of the **WebSession** parameter.</span></span> <span data-ttu-id="4c316-226">PowerShell använder data i objektet Webbbegäran-session när den nya anslutningen upprättas.</span><span class="sxs-lookup"><span data-stu-id="4c316-226">PowerShell uses the data in the web request session object when establishing the new connection.</span></span> <span data-ttu-id="4c316-227">Om du vill åsidosätta ett värde i Webbbegäran-sessionen använder du en cmdlet-parameter, till exempel **useragent** eller **Credential**.</span><span class="sxs-lookup"><span data-stu-id="4c316-227">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential**.</span></span> <span data-ttu-id="4c316-228">Parameter värden har företräde framför värden i Webbbegäran-sessionen.</span><span class="sxs-lookup"><span data-stu-id="4c316-228">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="4c316-229">Du kan inte använda parametrarna **SessionVariable** och **websession** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="4c316-229">You cannot use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="4c316-230">-TimeoutSec</span><span class="sxs-lookup"><span data-stu-id="4c316-230">-TimeoutSec</span></span>

<span data-ttu-id="4c316-231">Anger hur lång tid det tar att vänta på begäran innan den går ut. Ange ett värde i sekunder.</span><span class="sxs-lookup"><span data-stu-id="4c316-231">Specifies how long the request can be pending before it times out. Enter a value in seconds.</span></span> <span data-ttu-id="4c316-232">Standardvärdet 0 anger en obestämd tids gräns.</span><span class="sxs-lookup"><span data-stu-id="4c316-232">The default value, 0, specifies an indefinite time-out.</span></span>

<span data-ttu-id="4c316-233">En Domain Name System-fråga (DNS) kan ta upp till 15 sekunder att returnera eller ta slut för lång tid. Om din begäran innehåller ett värdnamn som kräver lösning och du anger **TimeoutSec** till ett värde som är större än noll, men mindre än 15 sekunder, kan det ta 15 sekunder eller mer innan en **WebException** utlöses, och tids gränsen för din begäran görs.</span><span class="sxs-lookup"><span data-stu-id="4c316-233">A Domain Name System (DNS) query can take up to 15 seconds to return or time out. If your request contains a host name that requires resolution, and you set **TimeoutSec** to a value greater than zero, but less than 15 seconds, it can take 15 seconds or more before a **WebException** is thrown, and your request times out.</span></span>

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

### <span data-ttu-id="4c316-234">-TransferEncoding</span><span class="sxs-lookup"><span data-stu-id="4c316-234">-TransferEncoding</span></span>

<span data-ttu-id="4c316-235">Anger ett värde för HTTP-svarshuvuden för överförings kodning.</span><span class="sxs-lookup"><span data-stu-id="4c316-235">Specifies a value for the transfer-encoding HTTP response header.</span></span> <span data-ttu-id="4c316-236">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="4c316-236">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="4c316-237">Segment vis</span><span class="sxs-lookup"><span data-stu-id="4c316-237">Chunked</span></span>
- <span data-ttu-id="4c316-238">Compress</span><span class="sxs-lookup"><span data-stu-id="4c316-238">Compress</span></span>
- <span data-ttu-id="4c316-239">DEFLATE</span><span class="sxs-lookup"><span data-stu-id="4c316-239">Deflate</span></span>
- <span data-ttu-id="4c316-240">GZip</span><span class="sxs-lookup"><span data-stu-id="4c316-240">GZip</span></span>
- <span data-ttu-id="4c316-241">Identitet</span><span class="sxs-lookup"><span data-stu-id="4c316-241">Identity</span></span>

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

### <span data-ttu-id="4c316-242">-URI</span><span class="sxs-lookup"><span data-stu-id="4c316-242">-Uri</span></span>

<span data-ttu-id="4c316-243">Anger Uniform Resource Identifier (URI) för den Internet resurs som webb förfrågan skickas till.</span><span class="sxs-lookup"><span data-stu-id="4c316-243">Specifies the Uniform Resource Identifier (URI) of the Internet resource to which the web request is sent.</span></span> <span data-ttu-id="4c316-244">Ange en URI.</span><span class="sxs-lookup"><span data-stu-id="4c316-244">Enter a URI.</span></span> <span data-ttu-id="4c316-245">Den här parametern stöder HTTP-, HTTPS-, FTP-och fil värden.</span><span class="sxs-lookup"><span data-stu-id="4c316-245">This parameter supports HTTP, HTTPS, FTP, and FILE values.</span></span>

<span data-ttu-id="4c316-246">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="4c316-246">This parameter is required.</span></span>

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

### <span data-ttu-id="4c316-247">-UseBasicParsing</span><span class="sxs-lookup"><span data-stu-id="4c316-247">-UseBasicParsing</span></span>

<span data-ttu-id="4c316-248">Anger att cmdleten använder Response-objektet för HTML-innehåll utan Document Object Model (DOM) parsing.</span><span class="sxs-lookup"><span data-stu-id="4c316-248">Indicates that the cmdlet uses the response object for HTML content without Document Object Model (DOM) parsing.</span></span> <span data-ttu-id="4c316-249">Den här parametern krävs när Internet Explorer inte är installerat på datorerna, t. ex. på en Server Core-installation av ett Windows Server-operativsystem.</span><span class="sxs-lookup"><span data-stu-id="4c316-249">This parameter is required when Internet Explorer is not installed on the computers, such as on a Server Core installation of a Windows Server operating system.</span></span>

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

### <span data-ttu-id="4c316-250">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="4c316-250">-UseDefaultCredentials</span></span>

<span data-ttu-id="4c316-251">Anger att cmDet använder autentiseringsuppgifterna för den aktuella användaren för att skicka webb förfrågan.</span><span class="sxs-lookup"><span data-stu-id="4c316-251">Indicates that the cmdet uses the credentials of the current user to send the web request.</span></span>

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

### <span data-ttu-id="4c316-252">– UserAgent</span><span class="sxs-lookup"><span data-stu-id="4c316-252">-UserAgent</span></span>

<span data-ttu-id="4c316-253">Anger en användar agent sträng för webb förfrågan.</span><span class="sxs-lookup"><span data-stu-id="4c316-253">Specifies a user agent string for the web request.</span></span> <span data-ttu-id="4c316-254">Standard användar agenten liknar `Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0` med små variationer för varje operativ system och plattform.</span><span class="sxs-lookup"><span data-stu-id="4c316-254">The default user agent is similar to `Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0` with slight variations for each operating system and platform.</span></span>

<span data-ttu-id="4c316-255">Om du vill testa en webbplats med den standard användar agent sträng som används av de flesta webbläsare, använder du egenskaperna för [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) -klassen, till exempel Chrome, Firefox, InternetExplorer, Opera och Safari.</span><span class="sxs-lookup"><span data-stu-id="4c316-255">To test a website with the standard user agent string that is used by most Internet browsers, use the properties of the [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) class, such as Chrome, FireFox, InternetExplorer, Opera, and Safari.</span></span> <span data-ttu-id="4c316-256">Följande kommando använder till exempel användar agent strängen för Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="4c316-256">For example, the following command uses the user agent string for Internet Explorer</span></span>

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

### <span data-ttu-id="4c316-257">– Websession</span><span class="sxs-lookup"><span data-stu-id="4c316-257">-WebSession</span></span>

<span data-ttu-id="4c316-258">Anger en Webbbegäran-session.</span><span class="sxs-lookup"><span data-stu-id="4c316-258">Specifies a web request session.</span></span> <span data-ttu-id="4c316-259">Ange variabel namnet, inklusive dollar tecknet ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="4c316-259">Enter the variable name, including the dollar sign (`$`).</span></span>

<span data-ttu-id="4c316-260">Om du vill åsidosätta ett värde i Webbbegäran-sessionen använder du en cmdlet-parameter, till exempel **useragent** eller **Credential**.</span><span class="sxs-lookup"><span data-stu-id="4c316-260">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential**.</span></span> <span data-ttu-id="4c316-261">Parameter värden har företräde framför värden i Webbbegäran-sessionen.</span><span class="sxs-lookup"><span data-stu-id="4c316-261">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="4c316-262">Till skillnad från en fjärran sluten session är inte Webbbegäran-sessionen en permanent anslutning.</span><span class="sxs-lookup"><span data-stu-id="4c316-262">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="4c316-263">Det är ett objekt som innehåller information om anslutningen och begäran, inklusive cookies, autentiseringsuppgifter, det maximala värdet för omdirigering och användar agent strängen.</span><span class="sxs-lookup"><span data-stu-id="4c316-263">It is an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="4c316-264">Du kan använda den för att dela tillstånd och data mellan webb förfrågningar.</span><span class="sxs-lookup"><span data-stu-id="4c316-264">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="4c316-265">Om du vill skapa en Webbbegäran-session anger du ett variabel namn (utan dollar tecken) i värdet för parametern **SessionVariable** för ett `Invoke-WebRequest` kommando.</span><span class="sxs-lookup"><span data-stu-id="4c316-265">To create a web request session, enter a variable name (without a dollar sign) in the value of the **SessionVariable** parameter of an `Invoke-WebRequest` command.</span></span> <span data-ttu-id="4c316-266">`Invoke-WebRequest` skapar sessionen och sparar den i variabeln.</span><span class="sxs-lookup"><span data-stu-id="4c316-266">`Invoke-WebRequest` creates the session and saves it in the variable.</span></span> <span data-ttu-id="4c316-267">I efterföljande kommandon använder du variabeln som värde för **websession** -parametern.</span><span class="sxs-lookup"><span data-stu-id="4c316-267">In subsequent commands, use the variable as the value of the **WebSession** parameter.</span></span>

<span data-ttu-id="4c316-268">Du kan inte använda parametrarna **SessionVariable** och **websession** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="4c316-268">You cannot use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="4c316-269">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4c316-269">CommonParameters</span></span>

<span data-ttu-id="4c316-270">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="4c316-270">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="4c316-271">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4c316-271">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4c316-272">INDATA</span><span class="sxs-lookup"><span data-stu-id="4c316-272">INPUTS</span></span>

### <span data-ttu-id="4c316-273">System. Object</span><span class="sxs-lookup"><span data-stu-id="4c316-273">System.Object</span></span>

<span data-ttu-id="4c316-274">Du kan skicka vidare innehållet i en webb förfrågan till `Invoke-WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="4c316-274">You can pipe the body of a web request to `Invoke-WebRequest`.</span></span>

## <span data-ttu-id="4c316-275">UTDATA</span><span class="sxs-lookup"><span data-stu-id="4c316-275">OUTPUTS</span></span>

### <span data-ttu-id="4c316-276">Microsoft.PowerShell.Commands.HtmlWebResponseObject</span><span class="sxs-lookup"><span data-stu-id="4c316-276">Microsoft.PowerShell.Commands.HtmlWebResponseObject</span></span>

## <span data-ttu-id="4c316-277">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="4c316-277">NOTES</span></span>

## <span data-ttu-id="4c316-278">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="4c316-278">RELATED LINKS</span></span>

[<span data-ttu-id="4c316-279">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="4c316-279">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)

[<span data-ttu-id="4c316-280">ConvertFrom – JSON</span><span class="sxs-lookup"><span data-stu-id="4c316-280">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="4c316-281">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="4c316-281">ConvertTo-Json</span></span>](ConvertTo-Json.md)
