---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-webrequest?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WebRequest
ms.openlocfilehash: 25da6262e93be3e3749aabaf4950e2fbcd91ff5c
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/10/2020
ms.locfileid: "93268958"
---
# <span data-ttu-id="82b04-103">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="82b04-103">Invoke-WebRequest</span></span>

## <span data-ttu-id="82b04-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="82b04-104">SYNOPSIS</span></span>
<span data-ttu-id="82b04-105">Hämtar innehåll från en webb sida på Internet.</span><span class="sxs-lookup"><span data-stu-id="82b04-105">Gets content from a web page on the Internet.</span></span>

## <span data-ttu-id="82b04-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="82b04-106">SYNTAX</span></span>

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>] [-SessionVariable <String>]
 [-Credential <PSCredential>] [-UseDefaultCredentials] [-CertificateThumbprint <String>]
 [-Certificate <X509Certificate>] [-UserAgent <String>] [-DisableKeepAlive] [-TimeoutSec <Int32>]
 [-Headers <IDictionary>] [-MaximumRedirection <Int32>] [-Method <WebRequestMethod>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>] [-ContentType <String>]
 [-TransferEncoding <String>] [-InFile <String>] [-OutFile <String>] [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="82b04-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="82b04-107">DESCRIPTION</span></span>

<span data-ttu-id="82b04-108">`Invoke-WebRequest`Cmdleten skickar http-, https-, FTP-och fil begär anden till en webb sida eller en webb tjänst.</span><span class="sxs-lookup"><span data-stu-id="82b04-108">The `Invoke-WebRequest` cmdlet sends HTTP, HTTPS, FTP, and FILE requests to a web page or web service.</span></span>
<span data-ttu-id="82b04-109">Den tolkar svaret och returnerar samlingar av formulär, länkar, bilder och andra viktiga HTML-element.</span><span class="sxs-lookup"><span data-stu-id="82b04-109">It parses the response and returns collections of forms, links, images, and other significant HTML elements.</span></span>

<span data-ttu-id="82b04-110">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="82b04-110">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="82b04-111">Som standard kan skript kod på webb sidan köras när sidan parsas för att fylla i `ParsedHtml` egenskapen.</span><span class="sxs-lookup"><span data-stu-id="82b04-111">By default, script code in the web page may be run when the page is being parsed to populate the `ParsedHtml` property.</span></span>
> <span data-ttu-id="82b04-112">Använd `-UseBasicParsing` växeln för att ignorera detta.</span><span class="sxs-lookup"><span data-stu-id="82b04-112">Use the `-UseBasicParsing` switch to suppress this.</span></span>

## <span data-ttu-id="82b04-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="82b04-113">EXAMPLES</span></span>

### <span data-ttu-id="82b04-114">Exempel 1: skicka en webb förfrågan</span><span class="sxs-lookup"><span data-stu-id="82b04-114">Example 1: Send a web request</span></span>

<span data-ttu-id="82b04-115">Detta kommando använder `Invoke-WebRequest` cmdleten för att skicka en webbegäran till Bing.com-webbplatsen.</span><span class="sxs-lookup"><span data-stu-id="82b04-115">This command uses the `Invoke-WebRequest` cmdlet to send a web request to the Bing.com site.</span></span>

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

<span data-ttu-id="82b04-116">Det första kommandot utfärdar begäran och sparar svaret i `$R` variabeln.</span><span class="sxs-lookup"><span data-stu-id="82b04-116">The first command issues the request and saves the response in the `$R` variable.</span></span>

<span data-ttu-id="82b04-117">Det andra kommandot filtrerar objekten i egenskapen **alleler** där egenskapen **namn** är som "\* värde" och **TagName** är "inmatat".</span><span class="sxs-lookup"><span data-stu-id="82b04-117">The second command filters the objects in the **AllElements** property where the **name** property is like "\* Value" and the **tagName** is "INPUT".</span></span> <span data-ttu-id="82b04-118">De filtrerade resultaten är skickas för `Select-Object` att välja egenskaper för **namn** och **värde** .</span><span class="sxs-lookup"><span data-stu-id="82b04-118">The filtered results are piped to `Select-Object` to select the **name** and **value** properties.</span></span>

### <span data-ttu-id="82b04-119">Exempel 2: använda en tillstånds känslig webb tjänst</span><span class="sxs-lookup"><span data-stu-id="82b04-119">Example 2: Use a stateful web service</span></span>

<span data-ttu-id="82b04-120">Det här exemplet visar hur du använder `Invoke-WebRequest` cmdleten med en tillstånds känslig webb tjänst, till exempel Facebook.</span><span class="sxs-lookup"><span data-stu-id="82b04-120">This example shows how to use the `Invoke-WebRequest` cmdlet with a stateful web service, such as Facebook.</span></span>

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

<span data-ttu-id="82b04-121">Det första kommandot använder `Invoke-WebRequest` cmdleten för att skicka en inloggnings förfrågan.</span><span class="sxs-lookup"><span data-stu-id="82b04-121">The first command uses the `Invoke-WebRequest` cmdlet to send a sign-in request.</span></span> <span data-ttu-id="82b04-122">Kommandot anger värdet "FB" för värdet för parametern **SessionVariable** och sparar resultatet i `$R` variabeln.</span><span class="sxs-lookup"><span data-stu-id="82b04-122">The command specifies a value of "FB" for the value of the **SessionVariable** parameter, and saves the result in the `$R` variable.</span></span> <span data-ttu-id="82b04-123">När kommandot har slutförts `$R` innehåller variabeln en **HtmlWebResponseObject** och `$FB` variabeln innehåller ett **WebRequestSession** -objekt.</span><span class="sxs-lookup"><span data-stu-id="82b04-123">When the command completes, the `$R` variable contains an **HtmlWebResponseObject** and the `$FB` variable contains a **WebRequestSession** object.</span></span>

<span data-ttu-id="82b04-124">När `Invoke-WebRequest` cmdleten har loggat in på Facebook anger egenskapen **statusDescription** för objektet Web Response i `$R` variabeln att användaren har loggat in.</span><span class="sxs-lookup"><span data-stu-id="82b04-124">After the `Invoke-WebRequest` cmdlet signs in to facebook, the **StatusDescription** property of the web response object in the `$R` variable indicates that the user is signed in successfully.</span></span>

### <span data-ttu-id="82b04-125">Exempel 3: Hämta länkar från en webb sida</span><span class="sxs-lookup"><span data-stu-id="82b04-125">Example 3: Get links from a web page</span></span>

<span data-ttu-id="82b04-126">Det här kommandot hämtar länkarna på en webb sida.</span><span class="sxs-lookup"><span data-stu-id="82b04-126">This command gets the links in a web page.</span></span>

```powershell
(Invoke-WebRequest -Uri "https://devblogs.microsoft.com/powershell/").Links.Href
```

<span data-ttu-id="82b04-127">`Invoke-WebRequest`Cmdleten hämtar webb sidans innehåll.</span><span class="sxs-lookup"><span data-stu-id="82b04-127">The `Invoke-WebRequest` cmdlet gets the web page content.</span></span> <span data-ttu-id="82b04-128">Sedan används egenskapen **Links** för den returnerade **HtmlWebResponseObject** för att visa egenskapen **href** för varje länk.</span><span class="sxs-lookup"><span data-stu-id="82b04-128">Then the **Links** property of the returned **HtmlWebResponseObject** is used to display the **Href** property of each link.</span></span>

### <span data-ttu-id="82b04-129">Exempel 4: fånga meddelanden som inte lyckades från Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="82b04-129">Example 4: Catch non success messages from Invoke-WebRequest</span></span>

<span data-ttu-id="82b04-130">När `Invoke-WebRequest` påträffar ett HTTP-meddelande som inte lyckades (404, 500 osv.) returnerar det inga utdata och returnerar ett avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="82b04-130">When `Invoke-WebRequest` encounters a non-success HTTP message (404, 500, etc.), it returns no output and throws a terminating error.</span></span> <span data-ttu-id="82b04-131">Om du vill fånga felet och visa **StatusCode** kan du sätta igång i ett `try/catch` block.</span><span class="sxs-lookup"><span data-stu-id="82b04-131">To catch the error and view the **StatusCode** you can enclose execution in a `try/catch` block.</span></span> <span data-ttu-id="82b04-132">I följande exempel visas hur du kan göra detta.</span><span class="sxs-lookup"><span data-stu-id="82b04-132">The following example shows how to accomplish this.</span></span>

```powershell
try
{
    $response = Invoke-WebRequest -Uri "www.microsoft.com/unkownhost" -ErrorAction Stop
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

<span data-ttu-id="82b04-133">Det första kommandot anropar `Invoke-WebRequest` med en **ErrorAction** av **stopp** , som tvingar fram `Invoke-WebRequest` ett avslutande fel vid eventuella misslyckade förfrågningar.</span><span class="sxs-lookup"><span data-stu-id="82b04-133">The first command calls `Invoke-WebRequest` with an **ErrorAction** of **Stop** , which forces `Invoke-WebRequest` to throw a terminating error on any failed requests.</span></span> <span data-ttu-id="82b04-134">Det avslutande felet fångas av `catch` blocket som hämtar **StatusCode** från **Exception** -objektet.</span><span class="sxs-lookup"><span data-stu-id="82b04-134">The terminating error is caught by the `catch` block which retrieves the **StatusCode** from the **Exception** object.</span></span>

## <span data-ttu-id="82b04-135">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="82b04-135">PARAMETERS</span></span>

### <span data-ttu-id="82b04-136">-Body</span><span class="sxs-lookup"><span data-stu-id="82b04-136">-Body</span></span>

<span data-ttu-id="82b04-137">Anger bröd texten i begäran.</span><span class="sxs-lookup"><span data-stu-id="82b04-137">Specifies the body of the request.</span></span>
<span data-ttu-id="82b04-138">Bröd texten är innehållet i begäran som följer sidhuvuden.</span><span class="sxs-lookup"><span data-stu-id="82b04-138">The body is the content of the request that follows the headers.</span></span>
<span data-ttu-id="82b04-139">Du kan också skicka ett Body-värde till `Invoke-WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="82b04-139">You can also pipe a body value to `Invoke-WebRequest`.</span></span>

<span data-ttu-id="82b04-140">Du kan använda **text** parametern för att ange en lista över frågeparametrar eller ange svarets innehåll.</span><span class="sxs-lookup"><span data-stu-id="82b04-140">The **Body** parameter can be used to specify a list of query parameters or specify the content of the response.</span></span>

<span data-ttu-id="82b04-141">När indatamängden är en GET-begäran och texten är en **IDictionary** (vanligt vis en hash-tabell), läggs bröd texten till i URI: n som frågeparametrar.</span><span class="sxs-lookup"><span data-stu-id="82b04-141">When the input is a GET request and the body is an **IDictionary** (typically, a hash table), the body is added to the URI as query parameters.</span></span> <span data-ttu-id="82b04-142">För andra GET-begäranden anges bröd texten som värdet för begär ande texten i `name=value` standardformat.</span><span class="sxs-lookup"><span data-stu-id="82b04-142">For other GET requests, the body is set as the value of the request body in the standard `name=value` format.</span></span>

<span data-ttu-id="82b04-143">När bröd texten är ett formulär, eller om det är utdata från ett `Invoke-WebRequest` anrop, anger PowerShell innehållet i formulär fälten.</span><span class="sxs-lookup"><span data-stu-id="82b04-143">When the body is a form, or it is the output of an `Invoke-WebRequest` call, PowerShell sets the request content to the form fields.</span></span>
<span data-ttu-id="82b04-144">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="82b04-144">For example:</span></span>

`$r = Invoke-WebRequest https://website.com/login.aspx`
`$r.Forms\[0\].Name = "MyName"`
`$r.Forms\[0\].Password = "MyPassword"`
`Invoke-RestMethod https://website.com/service.aspx -Body $r`

- <span data-ttu-id="82b04-145">eller</span><span class="sxs-lookup"><span data-stu-id="82b04-145">or -</span></span>

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

### <span data-ttu-id="82b04-146">– Certifikat</span><span class="sxs-lookup"><span data-stu-id="82b04-146">-Certificate</span></span>

<span data-ttu-id="82b04-147">Anger det klient certifikat som används för en säker webb förfrågan.</span><span class="sxs-lookup"><span data-stu-id="82b04-147">Specifies the client certificate that is used for a secure web request.</span></span> <span data-ttu-id="82b04-148">Ange en variabel som innehåller ett certifikat eller ett kommando eller uttryck som hämtar certifikatet.</span><span class="sxs-lookup"><span data-stu-id="82b04-148">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="82b04-149">Om du vill söka efter ett certifikat använder `Get-PfxCertificate` eller använder du `Get-ChildItem` cmdleten på **certifikat** `Cert:` enheten ().</span><span class="sxs-lookup"><span data-stu-id="82b04-149">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the **Certificate** (`Cert:`) drive.</span></span> <span data-ttu-id="82b04-150">Om certifikatet inte är giltigt eller inte har tillräcklig behörighet, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="82b04-150">If the certificate is not valid or does not have sufficient authority, the command fails.</span></span>

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

### <span data-ttu-id="82b04-151">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="82b04-151">-CertificateThumbprint</span></span>

<span data-ttu-id="82b04-152">Anger det digitala certifikat för offentlig nyckel (X509) för ett användar konto som har behörighet att skicka begäran.</span><span class="sxs-lookup"><span data-stu-id="82b04-152">Specifies the digital public key certificate (X509) of a user account that has permission to send the request.</span></span> <span data-ttu-id="82b04-153">Ange certifikatets tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="82b04-153">Enter the certificate thumbprint of the certificate.</span></span> <span data-ttu-id="82b04-154">Certifikat används i klient certifikat-baserad autentisering.</span><span class="sxs-lookup"><span data-stu-id="82b04-154">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="82b04-155">De kan endast mappas till lokala användar konton. de fungerar inte med domän konton.</span><span class="sxs-lookup"><span data-stu-id="82b04-155">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="82b04-156">Om du vill hämta ett tumavtryck för certifikatet använder du `Get-Item` `Get-ChildItem` kommandot eller i PowerShell- `Cert:` enheten.</span><span class="sxs-lookup"><span data-stu-id="82b04-156">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the PowerShell `Cert:` drive.</span></span>

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

### <span data-ttu-id="82b04-157">-ContentType</span><span class="sxs-lookup"><span data-stu-id="82b04-157">-ContentType</span></span>

<span data-ttu-id="82b04-158">Anger webb begärans innehålls typ.</span><span class="sxs-lookup"><span data-stu-id="82b04-158">Specifies the content type of the web request.</span></span>

<span data-ttu-id="82b04-159">Om den här parametern utelämnas och metoden för begäran är POST, `Invoke-WebRequest` ställer in innehålls typen på Application/x-www-form-urlencoded.</span><span class="sxs-lookup"><span data-stu-id="82b04-159">If this parameter is omitted and the request method is POST, `Invoke-WebRequest` sets the content type to application/x-www-form-urlencoded.</span></span> <span data-ttu-id="82b04-160">Annars anges inte innehålls typen i anropet.</span><span class="sxs-lookup"><span data-stu-id="82b04-160">Otherwise, the content type is not specified in the call.</span></span>

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

### <span data-ttu-id="82b04-161">-Credential</span><span class="sxs-lookup"><span data-stu-id="82b04-161">-Credential</span></span>

<span data-ttu-id="82b04-162">Anger ett användar konto som har behörighet att skicka begäran.</span><span class="sxs-lookup"><span data-stu-id="82b04-162">Specifies a user account that has permission to send the request.</span></span> <span data-ttu-id="82b04-163">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="82b04-163">The default is the current user.</span></span>

<span data-ttu-id="82b04-164">Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="82b04-164">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="82b04-165">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="82b04-165">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="82b04-166">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="82b04-166">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="82b04-167">-DisableKeepAlive</span><span class="sxs-lookup"><span data-stu-id="82b04-167">-DisableKeepAlive</span></span>

<span data-ttu-id="82b04-168">Anger att cmdleten anger **keepalive** -värdet i HTTP-huvudet till **false**.</span><span class="sxs-lookup"><span data-stu-id="82b04-168">Indicates that the cmdlet sets the **KeepAlive** value in the HTTP header to **False**.</span></span> <span data-ttu-id="82b04-169">**Keepalive** är som standard **Sant**.</span><span class="sxs-lookup"><span data-stu-id="82b04-169">By default, **KeepAlive** is **True**.</span></span> <span data-ttu-id="82b04-170">**Keepalive** upprättar en permanent anslutning till servern för att under lätta efterföljande begär Anden.</span><span class="sxs-lookup"><span data-stu-id="82b04-170">**KeepAlive** establishes a persistent connection to the server to facilitate subsequent requests.</span></span>

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

### <span data-ttu-id="82b04-171">– Sidhuvud</span><span class="sxs-lookup"><span data-stu-id="82b04-171">-Headers</span></span>

<span data-ttu-id="82b04-172">Anger webb begärans rubriker.</span><span class="sxs-lookup"><span data-stu-id="82b04-172">Specifies the headers of the web request.</span></span> <span data-ttu-id="82b04-173">Ange en hash-tabell eller-ord lista.</span><span class="sxs-lookup"><span data-stu-id="82b04-173">Enter a hash table or dictionary.</span></span>

<span data-ttu-id="82b04-174">Om du vill ange **useragent** -rubriker använder du parametern **useragent** .</span><span class="sxs-lookup"><span data-stu-id="82b04-174">To set **UserAgent** headers, use the **UserAgent** parameter.</span></span> <span data-ttu-id="82b04-175">Du kan inte använda den här parametern för att ange **useragent** -eller cookie-rubriker.</span><span class="sxs-lookup"><span data-stu-id="82b04-175">You cannot use this parameter to specify **UserAgent** or cookie headers.</span></span>

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

### <span data-ttu-id="82b04-176">-INFILE</span><span class="sxs-lookup"><span data-stu-id="82b04-176">-InFile</span></span>

<span data-ttu-id="82b04-177">Hämtar innehållet i webb förfrågan från en fil.</span><span class="sxs-lookup"><span data-stu-id="82b04-177">Gets the content of the web request from a file.</span></span>

<span data-ttu-id="82b04-178">Ange en sökväg och ett fil namn.</span><span class="sxs-lookup"><span data-stu-id="82b04-178">Enter a path and file name.</span></span> <span data-ttu-id="82b04-179">Om du utelämnar sökvägen är standardvärdet den aktuella platsen.</span><span class="sxs-lookup"><span data-stu-id="82b04-179">If you omit the path, the default is the current location.</span></span>

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

### <span data-ttu-id="82b04-180">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="82b04-180">-MaximumRedirection</span></span>

<span data-ttu-id="82b04-181">Anger hur många gånger PowerShell omdirigerar en anslutning till en alternativ Uniform Resource Identifier (URI) innan anslutningen Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="82b04-181">Specifies how many times PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="82b04-182">Standardvärdet är 5.</span><span class="sxs-lookup"><span data-stu-id="82b04-182">The default value is 5.</span></span> <span data-ttu-id="82b04-183">Värdet 0 (noll) förhindrar all omdirigering.</span><span class="sxs-lookup"><span data-stu-id="82b04-183">A value of 0 (zero) prevents all redirection.</span></span>

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

### <span data-ttu-id="82b04-184">-Metod</span><span class="sxs-lookup"><span data-stu-id="82b04-184">-Method</span></span>

<span data-ttu-id="82b04-185">Anger den metod som används för webb förfrågan.</span><span class="sxs-lookup"><span data-stu-id="82b04-185">Specifies the method used for the web request.</span></span> <span data-ttu-id="82b04-186">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="82b04-186">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="82b04-187">Default</span><span class="sxs-lookup"><span data-stu-id="82b04-187">Default</span></span>
- <span data-ttu-id="82b04-188">Ta bort</span><span class="sxs-lookup"><span data-stu-id="82b04-188">Delete</span></span>
- <span data-ttu-id="82b04-189">Hämta</span><span class="sxs-lookup"><span data-stu-id="82b04-189">Get</span></span>
- <span data-ttu-id="82b04-190">Head</span><span class="sxs-lookup"><span data-stu-id="82b04-190">Head</span></span>
- <span data-ttu-id="82b04-191">Sammanfoga</span><span class="sxs-lookup"><span data-stu-id="82b04-191">Merge</span></span>
- <span data-ttu-id="82b04-192">Alternativ</span><span class="sxs-lookup"><span data-stu-id="82b04-192">Options</span></span>
- <span data-ttu-id="82b04-193">Patch</span><span class="sxs-lookup"><span data-stu-id="82b04-193">Patch</span></span>
- <span data-ttu-id="82b04-194">Skicka</span><span class="sxs-lookup"><span data-stu-id="82b04-194">Post</span></span>
- <span data-ttu-id="82b04-195">Placera</span><span class="sxs-lookup"><span data-stu-id="82b04-195">Put</span></span>
- <span data-ttu-id="82b04-196">Spårning</span><span class="sxs-lookup"><span data-stu-id="82b04-196">Trace</span></span>

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

### <span data-ttu-id="82b04-197">-Fil</span><span class="sxs-lookup"><span data-stu-id="82b04-197">-OutFile</span></span>

<span data-ttu-id="82b04-198">Anger den utdatafil som denna cmdlet sparar svars texten för.</span><span class="sxs-lookup"><span data-stu-id="82b04-198">Specifies the output file for which this cmdlet saves the response body.</span></span> <span data-ttu-id="82b04-199">Ange en sökväg och ett fil namn.</span><span class="sxs-lookup"><span data-stu-id="82b04-199">Enter a path and file name.</span></span>
<span data-ttu-id="82b04-200">Om du utelämnar sökvägen är standardvärdet den aktuella platsen.</span><span class="sxs-lookup"><span data-stu-id="82b04-200">If you omit the path, the default is the current location.</span></span>

<span data-ttu-id="82b04-201">Som standard `Invoke-WebRequest` returnerar resultatet till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="82b04-201">By default, `Invoke-WebRequest` returns the results to the pipeline.</span></span> <span data-ttu-id="82b04-202">Om du vill skicka resultatet till en fil och till pipelinen använder du parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="82b04-202">To send the results to a file and to the pipeline, use the **Passthru** parameter.</span></span>

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

### <span data-ttu-id="82b04-203">– PassThru</span><span class="sxs-lookup"><span data-stu-id="82b04-203">-PassThru</span></span>

<span data-ttu-id="82b04-204">Anger att cmdleten returnerar resultatet, förutom att skriva dem till en fil.</span><span class="sxs-lookup"><span data-stu-id="82b04-204">Indicates that the cmdlet returns the results, in addition to writing them to a file.</span></span> <span data-ttu-id="82b04-205">Den här parametern är endast giltig om **parametern out** också används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="82b04-205">This parameter is valid only when the **OutFile** parameter is also used in the command.</span></span>

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

### <span data-ttu-id="82b04-206">-Proxy</span><span class="sxs-lookup"><span data-stu-id="82b04-206">-Proxy</span></span>

<span data-ttu-id="82b04-207">Anger en proxyserver för begäran, i stället för att ansluta direkt till Internet resursen.</span><span class="sxs-lookup"><span data-stu-id="82b04-207">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>
<span data-ttu-id="82b04-208">Ange URI för en proxyserver för nätverket.</span><span class="sxs-lookup"><span data-stu-id="82b04-208">Enter the URI of a network proxy server.</span></span>

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

### <span data-ttu-id="82b04-209">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="82b04-209">-ProxyCredential</span></span>

<span data-ttu-id="82b04-210">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="82b04-210">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span> <span data-ttu-id="82b04-211">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="82b04-211">The default is the current user.</span></span>

<span data-ttu-id="82b04-212">Ange ett användar namn, till exempel `User01` eller `Domain01\User01` , eller ange ett **PSCredential** -objekt, till exempel en som genereras av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="82b04-212">Type a user name, such as `User01` or `Domain01\User01`, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="82b04-213">Den här parametern är endast giltig när parametern **proxy** också används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="82b04-213">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="82b04-214">Du kan inte använda parametrarna **ProxyCredential** och **ProxyUseDefaultCredentials** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="82b04-214">You cannot use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="82b04-215">-ProxyUseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="82b04-215">-ProxyUseDefaultCredentials</span></span>

<span data-ttu-id="82b04-216">Anger att cmdleten använder autentiseringsuppgifterna för den aktuella användaren för att få åtkomst till proxyservern som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="82b04-216">Indicates that the cmdlet uses the credentials of the current user to access the proxy server that is specified by the **Proxy** parameter.</span></span>

<span data-ttu-id="82b04-217">Den här parametern är endast giltig när parametern **proxy** också används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="82b04-217">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="82b04-218">Du kan inte använda parametrarna **ProxyCredential** och **ProxyUseDefaultCredentials** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="82b04-218">You cannot use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="82b04-219">-SessionVariable</span><span class="sxs-lookup"><span data-stu-id="82b04-219">-SessionVariable</span></span>

<span data-ttu-id="82b04-220">Anger en variabel för vilken denna cmdlet skapar en Webbbegäran-session och sparar den i värdet.</span><span class="sxs-lookup"><span data-stu-id="82b04-220">Specifies a variable for which this cmdlet creates a web request session and saves it in the value.</span></span>
<span data-ttu-id="82b04-221">Ange ett variabel namn utan dollar tecknet ( `$` )-symbolen.</span><span class="sxs-lookup"><span data-stu-id="82b04-221">Enter a variable name without the dollar sign (`$`) symbol.</span></span>

<span data-ttu-id="82b04-222">När du anger en sessionsvariabel `Invoke-WebRequest` skapar ett sessionsobjekt för Webbbegäran och tilldelar det till en variabel med det angivna namnet i PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="82b04-222">When you specify a session variable, `Invoke-WebRequest` creates a web request session object and assigns it to a variable with the specified name in your PowerShell session.</span></span> <span data-ttu-id="82b04-223">Du kan använda variabeln i din session så snart kommandot har slutförts.</span><span class="sxs-lookup"><span data-stu-id="82b04-223">You can use the variable in your session as soon as the command completes.</span></span>

<span data-ttu-id="82b04-224">Till skillnad från en fjärran sluten session är inte Webbbegäran-sessionen en permanent anslutning.</span><span class="sxs-lookup"><span data-stu-id="82b04-224">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="82b04-225">Det är ett objekt som innehåller information om anslutningen och begäran, inklusive cookies, autentiseringsuppgifter, det maximala värdet för omdirigering och användar agent strängen.</span><span class="sxs-lookup"><span data-stu-id="82b04-225">It is an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="82b04-226">Du kan använda den för att dela tillstånd och data mellan webb förfrågningar.</span><span class="sxs-lookup"><span data-stu-id="82b04-226">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="82b04-227">Om du vill använda Webbbegäran-sessionen i efterföljande webb förfrågningar, anger du variabeln session i värdet för **websession** -parametern.</span><span class="sxs-lookup"><span data-stu-id="82b04-227">To use the web request session in subsequent web requests, specify the session variable in the value of the **WebSession** parameter.</span></span> <span data-ttu-id="82b04-228">PowerShell använder data i objektet Webbbegäran-session när den nya anslutningen upprättas.</span><span class="sxs-lookup"><span data-stu-id="82b04-228">PowerShell uses the data in the web request session object when establishing the new connection.</span></span> <span data-ttu-id="82b04-229">Om du vill åsidosätta ett värde i Webbbegäran-sessionen använder du en cmdlet-parameter, till exempel **useragent** eller **Credential**.</span><span class="sxs-lookup"><span data-stu-id="82b04-229">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential**.</span></span> <span data-ttu-id="82b04-230">Parameter värden har företräde framför värden i Webbbegäran-sessionen.</span><span class="sxs-lookup"><span data-stu-id="82b04-230">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="82b04-231">Du kan inte använda parametrarna **SessionVariable** och **websession** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="82b04-231">You cannot use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="82b04-232">-TimeoutSec</span><span class="sxs-lookup"><span data-stu-id="82b04-232">-TimeoutSec</span></span>

<span data-ttu-id="82b04-233">Anger hur lång tid det tar att vänta på begäran innan den går ut. Ange ett värde i sekunder.</span><span class="sxs-lookup"><span data-stu-id="82b04-233">Specifies how long the request can be pending before it times out. Enter a value in seconds.</span></span> <span data-ttu-id="82b04-234">Standardvärdet 0 anger en obestämd tids gräns.</span><span class="sxs-lookup"><span data-stu-id="82b04-234">The default value, 0, specifies an indefinite time-out.</span></span>

<span data-ttu-id="82b04-235">En Domain Name System-fråga (DNS) kan ta upp till 15 sekunder att returnera eller ta slut för lång tid. Om din begäran innehåller ett värdnamn som kräver lösning och du anger **TimeoutSec** till ett värde som är större än noll, men mindre än 15 sekunder, kan det ta 15 sekunder eller mer innan en **WebException** utlöses, och tids gränsen för din begäran görs.</span><span class="sxs-lookup"><span data-stu-id="82b04-235">A Domain Name System (DNS) query can take up to 15 seconds to return or time out. If your request contains a host name that requires resolution, and you set **TimeoutSec** to a value greater than zero, but less than 15 seconds, it can take 15 seconds or more before a **WebException** is thrown, and your request times out.</span></span>

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

### <span data-ttu-id="82b04-236">-TransferEncoding</span><span class="sxs-lookup"><span data-stu-id="82b04-236">-TransferEncoding</span></span>

<span data-ttu-id="82b04-237">Anger ett värde för HTTP-svarshuvuden för överförings kodning.</span><span class="sxs-lookup"><span data-stu-id="82b04-237">Specifies a value for the transfer-encoding HTTP response header.</span></span> <span data-ttu-id="82b04-238">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="82b04-238">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="82b04-239">Segment vis</span><span class="sxs-lookup"><span data-stu-id="82b04-239">Chunked</span></span>
- <span data-ttu-id="82b04-240">Compress</span><span class="sxs-lookup"><span data-stu-id="82b04-240">Compress</span></span>
- <span data-ttu-id="82b04-241">DEFLATE</span><span class="sxs-lookup"><span data-stu-id="82b04-241">Deflate</span></span>
- <span data-ttu-id="82b04-242">GZip</span><span class="sxs-lookup"><span data-stu-id="82b04-242">GZip</span></span>
- <span data-ttu-id="82b04-243">Identitet</span><span class="sxs-lookup"><span data-stu-id="82b04-243">Identity</span></span>

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

### <span data-ttu-id="82b04-244">-URI</span><span class="sxs-lookup"><span data-stu-id="82b04-244">-Uri</span></span>

<span data-ttu-id="82b04-245">Anger Uniform Resource Identifier (URI) för den Internet resurs som webb förfrågan skickas till.</span><span class="sxs-lookup"><span data-stu-id="82b04-245">Specifies the Uniform Resource Identifier (URI) of the Internet resource to which the web request is sent.</span></span> <span data-ttu-id="82b04-246">Ange en URI.</span><span class="sxs-lookup"><span data-stu-id="82b04-246">Enter a URI.</span></span> <span data-ttu-id="82b04-247">Den här parametern stöder HTTP-, HTTPS-, FTP-och fil värden.</span><span class="sxs-lookup"><span data-stu-id="82b04-247">This parameter supports HTTP, HTTPS, FTP, and FILE values.</span></span>

<span data-ttu-id="82b04-248">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="82b04-248">This parameter is required.</span></span>

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

### <span data-ttu-id="82b04-249">-UseBasicParsing</span><span class="sxs-lookup"><span data-stu-id="82b04-249">-UseBasicParsing</span></span>

<span data-ttu-id="82b04-250">Anger att cmdleten använder Response-objektet för HTML-innehåll utan Document Object Model (DOM) parsing.</span><span class="sxs-lookup"><span data-stu-id="82b04-250">Indicates that the cmdlet uses the response object for HTML content without Document Object Model (DOM) parsing.</span></span> <span data-ttu-id="82b04-251">Den här parametern krävs när Internet Explorer inte är installerat på datorerna, t. ex. på en Server Core-installation av ett Windows Server-operativsystem.</span><span class="sxs-lookup"><span data-stu-id="82b04-251">This parameter is required when Internet Explorer is not installed on the computers, such as on a Server Core installation of a Windows Server operating system.</span></span>

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

### <span data-ttu-id="82b04-252">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="82b04-252">-UseDefaultCredentials</span></span>

<span data-ttu-id="82b04-253">Anger att cmDet använder autentiseringsuppgifterna för den aktuella användaren för att skicka webb förfrågan.</span><span class="sxs-lookup"><span data-stu-id="82b04-253">Indicates that the cmdet uses the credentials of the current user to send the web request.</span></span>

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

### <span data-ttu-id="82b04-254">– UserAgent</span><span class="sxs-lookup"><span data-stu-id="82b04-254">-UserAgent</span></span>

<span data-ttu-id="82b04-255">Anger en användar agent sträng för webb förfrågan.</span><span class="sxs-lookup"><span data-stu-id="82b04-255">Specifies a user agent string for the web request.</span></span> <span data-ttu-id="82b04-256">Standard användar agenten liknar `Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0` med små variationer för varje operativ system och plattform.</span><span class="sxs-lookup"><span data-stu-id="82b04-256">The default user agent is similar to `Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0` with slight variations for each operating system and platform.</span></span>

<span data-ttu-id="82b04-257">Om du vill testa en webbplats med den standard användar agent sträng som används av de flesta webbläsare, använder du egenskaperna för [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) -klassen, till exempel Chrome, Firefox, InternetExplorer, Opera och Safari.</span><span class="sxs-lookup"><span data-stu-id="82b04-257">To test a website with the standard user agent string that is used by most Internet browsers, use the properties of the [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) class, such as Chrome, FireFox, InternetExplorer, Opera, and Safari.</span></span> <span data-ttu-id="82b04-258">Följande kommando använder till exempel användar agent strängen för Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="82b04-258">For example, the following command uses the user agent string for Internet Explorer</span></span>

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

### <span data-ttu-id="82b04-259">– Websession</span><span class="sxs-lookup"><span data-stu-id="82b04-259">-WebSession</span></span>

<span data-ttu-id="82b04-260">Anger en Webbbegäran-session.</span><span class="sxs-lookup"><span data-stu-id="82b04-260">Specifies a web request session.</span></span> <span data-ttu-id="82b04-261">Ange variabel namnet, inklusive dollar tecknet ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="82b04-261">Enter the variable name, including the dollar sign (`$`).</span></span>

<span data-ttu-id="82b04-262">Om du vill åsidosätta ett värde i Webbbegäran-sessionen använder du en cmdlet-parameter, till exempel **useragent** eller **Credential**.</span><span class="sxs-lookup"><span data-stu-id="82b04-262">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential**.</span></span> <span data-ttu-id="82b04-263">Parameter värden har företräde framför värden i Webbbegäran-sessionen.</span><span class="sxs-lookup"><span data-stu-id="82b04-263">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="82b04-264">Till skillnad från en fjärran sluten session är inte Webbbegäran-sessionen en permanent anslutning.</span><span class="sxs-lookup"><span data-stu-id="82b04-264">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="82b04-265">Det är ett objekt som innehåller information om anslutningen och begäran, inklusive cookies, autentiseringsuppgifter, det maximala värdet för omdirigering och användar agent strängen.</span><span class="sxs-lookup"><span data-stu-id="82b04-265">It is an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="82b04-266">Du kan använda den för att dela tillstånd och data mellan webb förfrågningar.</span><span class="sxs-lookup"><span data-stu-id="82b04-266">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="82b04-267">Om du vill skapa en Webbbegäran-session anger du ett variabel namn (utan dollar tecken) i värdet för parametern **SessionVariable** för ett `Invoke-WebRequest` kommando.</span><span class="sxs-lookup"><span data-stu-id="82b04-267">To create a web request session, enter a variable name (without a dollar sign) in the value of the **SessionVariable** parameter of an `Invoke-WebRequest` command.</span></span> <span data-ttu-id="82b04-268">`Invoke-WebRequest` skapar sessionen och sparar den i variabeln.</span><span class="sxs-lookup"><span data-stu-id="82b04-268">`Invoke-WebRequest` creates the session and saves it in the variable.</span></span> <span data-ttu-id="82b04-269">I efterföljande kommandon använder du variabeln som värde för **websession** -parametern.</span><span class="sxs-lookup"><span data-stu-id="82b04-269">In subsequent commands, use the variable as the value of the **WebSession** parameter.</span></span>

<span data-ttu-id="82b04-270">Du kan inte använda parametrarna **SessionVariable** och **websession** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="82b04-270">You cannot use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="82b04-271">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="82b04-271">CommonParameters</span></span>

<span data-ttu-id="82b04-272">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="82b04-272">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="82b04-273">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="82b04-273">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="82b04-274">INDATA</span><span class="sxs-lookup"><span data-stu-id="82b04-274">INPUTS</span></span>

### <span data-ttu-id="82b04-275">System. Object</span><span class="sxs-lookup"><span data-stu-id="82b04-275">System.Object</span></span>

<span data-ttu-id="82b04-276">Du kan skicka vidare innehållet i en webb förfrågan till `Invoke-WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="82b04-276">You can pipe the body of a web request to `Invoke-WebRequest`.</span></span>

## <span data-ttu-id="82b04-277">UTDATA</span><span class="sxs-lookup"><span data-stu-id="82b04-277">OUTPUTS</span></span>

### <span data-ttu-id="82b04-278">Microsoft.PowerShell.Commands.HtmlWebResponseObject</span><span class="sxs-lookup"><span data-stu-id="82b04-278">Microsoft.PowerShell.Commands.HtmlWebResponseObject</span></span>

## <span data-ttu-id="82b04-279">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="82b04-279">NOTES</span></span>

## <span data-ttu-id="82b04-280">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="82b04-280">RELATED LINKS</span></span>

[<span data-ttu-id="82b04-281">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="82b04-281">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)

[<span data-ttu-id="82b04-282">ConvertFrom – JSON</span><span class="sxs-lookup"><span data-stu-id="82b04-282">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="82b04-283">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="82b04-283">ConvertTo-Json</span></span>](ConvertTo-Json.md)
