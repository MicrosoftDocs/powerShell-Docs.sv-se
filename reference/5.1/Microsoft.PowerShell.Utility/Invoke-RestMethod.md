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
# <span data-ttu-id="27c94-103">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="27c94-103">Invoke-RestMethod</span></span>

## <span data-ttu-id="27c94-104">Sammanfattning</span><span class="sxs-lookup"><span data-stu-id="27c94-104">Synopsis</span></span>
<span data-ttu-id="27c94-105">Skickar en HTTP-eller HTTPS-begäran till en RESTful-webbtjänst.</span><span class="sxs-lookup"><span data-stu-id="27c94-105">Sends an HTTP or HTTPS request to a RESTful web service.</span></span>

## <span data-ttu-id="27c94-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="27c94-106">Syntax</span></span>

```
Invoke-RestMethod [-Method <WebRequestMethod>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-CertificateThumbprint <String>] [-Certificate <X509Certificate>]
 [-UserAgent <String>] [-DisableKeepAlive] [-TimeoutSec <Int32>] [-Headers <IDictionary>]
 [-MaximumRedirection <Int32>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials]
 [-Body <Object>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>] [-OutFile <String>]
 [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="27c94-107">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="27c94-107">Description</span></span>

<span data-ttu-id="27c94-108">`Invoke-RestMethod`Cmdlet: en skickar HTTP-och HTTPS-begäranden till en rest-webbtjänster (Representational State Transfer) som returnerar data som kan struktureras.</span><span class="sxs-lookup"><span data-stu-id="27c94-108">The `Invoke-RestMethod` cmdlet sends HTTP and HTTPS requests to Representational State Transfer (REST) web services that returns richly structured data.</span></span>

<span data-ttu-id="27c94-109">Windows PowerShell formaterar svaret baserat på data typen.</span><span class="sxs-lookup"><span data-stu-id="27c94-109">Windows PowerShell formats the response based to the data type.</span></span> <span data-ttu-id="27c94-110">För en RSS-eller ATOM-feed returnerar Windows PowerShell objektet eller postens XML-noder.</span><span class="sxs-lookup"><span data-stu-id="27c94-110">For an RSS or ATOM feed, Windows PowerShell returns the Item or Entry XML nodes.</span></span> <span data-ttu-id="27c94-111">För JavaScript Object Notation (JSON) eller XML konverterar Windows PowerShell (eller deserialiserar) innehållet till objekt.</span><span class="sxs-lookup"><span data-stu-id="27c94-111">For JavaScript Object Notation (JSON) or XML, Windows PowerShell converts (or deserializes) the content into objects.</span></span>

<span data-ttu-id="27c94-112">Denna cmdlet introduceras i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="27c94-112">This cmdlet is introduced in Windows PowerShell 3.0.</span></span>

> [!NOTE]
> <span data-ttu-id="27c94-113">Som standard kan skript kod på webb sidan köras när sidan parsas för att fylla i `ParsedHtml` egenskapen.</span><span class="sxs-lookup"><span data-stu-id="27c94-113">By default, script code in the web page may be run when the page is being parsed to populate the `ParsedHtml` property.</span></span> <span data-ttu-id="27c94-114">Använd **UseBasicParsing** -växeln för att ignorera detta.</span><span class="sxs-lookup"><span data-stu-id="27c94-114">Use the **UseBasicParsing** switch to suppress this.</span></span>

## <span data-ttu-id="27c94-115">Exempel</span><span class="sxs-lookup"><span data-stu-id="27c94-115">Examples</span></span>

### <span data-ttu-id="27c94-116">Exempel 1: Hämta PowerShell RSS-flödet</span><span class="sxs-lookup"><span data-stu-id="27c94-116">Example 1: Get the PowerShell RSS feed</span></span>

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

<span data-ttu-id="27c94-117">Det här kommandot använder `Invoke-RestMethod` cmdleten för att hämta information från RSS-flödet för PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="27c94-117">This command uses the `Invoke-RestMethod` cmdlet to get information from the PowerShell Blog RSS feed.</span></span> <span data-ttu-id="27c94-118">Kommandot använder `Format-Table` cmdleten för att visa värdena för egenskaperna **title** och **pubDate** för varje blogg i en tabell.</span><span class="sxs-lookup"><span data-stu-id="27c94-118">The command uses the `Format-Table` cmdlet to display the values of the **Title** and **pubDate** properties of each blog in a table.</span></span>

### <span data-ttu-id="27c94-119">Exempel 2</span><span class="sxs-lookup"><span data-stu-id="27c94-119">Example 2</span></span>

<span data-ttu-id="27c94-120">I följande exempel körs en användare `Invoke-RestMethod` för att utföra en post-begäran på en intranäts webbplats i användarens organisation.</span><span class="sxs-lookup"><span data-stu-id="27c94-120">In the following example, a user runs `Invoke-RestMethod` to perform a POST request on an intranet website in the user's organization.</span></span>

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

### <span data-ttu-id="27c94-121">Exempel 3: skicka flera huvuden</span><span class="sxs-lookup"><span data-stu-id="27c94-121">Example 3: Pass multiple headers</span></span>

<span data-ttu-id="27c94-122">Det här exemplet visar hur du skickar flera huvuden i från en `hash-table` till en REST API.</span><span class="sxs-lookup"><span data-stu-id="27c94-122">This example demonstrates, how to pass multiple headers in from a `hash-table` to a REST API.</span></span>

```powershell
$headers = @{
    'userId' = 'UserIDValue'
    'token' = 'TokenValue'
}
Invoke-RestMethod -Uri $uri -Method Post -Headers $headers -Body $body
```

<span data-ttu-id="27c94-123">API: er kräver ofta skickade rubriker för autentisering, validering osv.</span><span class="sxs-lookup"><span data-stu-id="27c94-123">APIs often require passed headers for authentication, validation etc.</span></span>

### <span data-ttu-id="27c94-124">Exempel 3: skicka formulär data</span><span class="sxs-lookup"><span data-stu-id="27c94-124">Example 3: Submitting form data</span></span>

<span data-ttu-id="27c94-125">När bröd texten är ett formulär, eller om det är utdata från ett annat `Invoke-WebRequest` anrop, anger PowerShell innehållet i formulär fälten.</span><span class="sxs-lookup"><span data-stu-id="27c94-125">When the body is a form, or it is the output of another `Invoke-WebRequest` call, PowerShell sets the request content to the form fields.</span></span>

<span data-ttu-id="27c94-126">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="27c94-126">For example:</span></span>

```powershell
$R = Invoke-WebRequest https://website.com/login.aspx
$R.Forms[0].Name = "MyName"
$R.Forms[0].Password = "MyPassword"
Invoke-RestMethod https://website.com/service.aspx -Body $R.Forms[0]
```

## <span data-ttu-id="27c94-127">Parametrar</span><span class="sxs-lookup"><span data-stu-id="27c94-127">Parameters</span></span>

### <span data-ttu-id="27c94-128">-Body</span><span class="sxs-lookup"><span data-stu-id="27c94-128">-Body</span></span>

<span data-ttu-id="27c94-129">Anger bröd texten i begäran.</span><span class="sxs-lookup"><span data-stu-id="27c94-129">Specifies the body of the request.</span></span> <span data-ttu-id="27c94-130">Bröd texten är innehållet i begäran som följer sidhuvuden.</span><span class="sxs-lookup"><span data-stu-id="27c94-130">The body is the content of the request that follows the headers.</span></span>
<span data-ttu-id="27c94-131">Du kan också skicka ett Body-värde till `Invoke-RestMethod` .</span><span class="sxs-lookup"><span data-stu-id="27c94-131">You can also pipe a body value to `Invoke-RestMethod`.</span></span>

<span data-ttu-id="27c94-132">Du kan använda **text** parametern för att ange en lista över frågeparametrar eller ange svarets innehåll.</span><span class="sxs-lookup"><span data-stu-id="27c94-132">The **Body** parameter can be used to specify a list of query parameters or specify the content of the response.</span></span>

<span data-ttu-id="27c94-133">När indatamängden är en GET-begäran och texten är en IDictionary (vanligt vis en hash-tabell), läggs bröd texten till i URI: n som frågeparametrar.</span><span class="sxs-lookup"><span data-stu-id="27c94-133">When the input is a GET request, and the body is an IDictionary (typically, a hash table), the body is added to the URI as query parameters.</span></span> <span data-ttu-id="27c94-134">För andra typer av begär Anden (till exempel POST) anges bröd texten som värdet för begär ande texten i standard namnet = värde formatet.</span><span class="sxs-lookup"><span data-stu-id="27c94-134">For other request types (such as POST), the body is set as the value of the request body in the standard name=value format.</span></span>

> [!WARNING]
> <span data-ttu-id="27c94-135">Utförliga utdata från en POST-brödtext slutar med `with -1-byte payload` , även om bröd texten både är känd och skickad i `Content-Length` http-huvudet.</span><span class="sxs-lookup"><span data-stu-id="27c94-135">The verbose output of a POST body will end with `with -1-byte payload`, even though the size of the body is both known and sent in the `Content-Length` HTTP header.</span></span>

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

### <span data-ttu-id="27c94-136">– Certifikat</span><span class="sxs-lookup"><span data-stu-id="27c94-136">-Certificate</span></span>

<span data-ttu-id="27c94-137">Anger det klient certifikat som används för en säker webb förfrågan.</span><span class="sxs-lookup"><span data-stu-id="27c94-137">Specifies the client certificate that is used for a secure web request.</span></span> <span data-ttu-id="27c94-138">Ange en variabel som innehåller ett certifikat eller ett kommando eller uttryck som hämtar certifikatet.</span><span class="sxs-lookup"><span data-stu-id="27c94-138">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="27c94-139">Om du vill söka efter ett certifikat använder `Get-PfxCertificate` eller använder du `Get-ChildItem` cmdleten på certifikat `Cert:` enheten ().</span><span class="sxs-lookup"><span data-stu-id="27c94-139">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the Certificate (`Cert:`) drive.</span></span> <span data-ttu-id="27c94-140">Om certifikatet inte är giltigt eller inte har tillräcklig behörighet, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="27c94-140">If the certificate is not valid or does not have sufficient authority, the command fails.</span></span>

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

### <span data-ttu-id="27c94-141">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="27c94-141">-CertificateThumbprint</span></span>

<span data-ttu-id="27c94-142">Anger det digitala certifikat för offentlig nyckel (X509) för ett användar konto som har behörighet att skicka begäran.</span><span class="sxs-lookup"><span data-stu-id="27c94-142">Specifies the digital public key certificate (X509) of a user account that has permission to send the request.</span></span> <span data-ttu-id="27c94-143">Ange certifikatets tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="27c94-143">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="27c94-144">Certifikat används i klient certifikat-baserad autentisering.</span><span class="sxs-lookup"><span data-stu-id="27c94-144">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="27c94-145">De kan endast mappas till lokala användar konton. de fungerar inte med domän konton.</span><span class="sxs-lookup"><span data-stu-id="27c94-145">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="27c94-146">Om du vill hämta ett tumavtryck för certifikatet använder du `Get-Item` `Get-ChildItem` kommandot eller i Windows PowerShell ( `Cert:` )-enheten.</span><span class="sxs-lookup"><span data-stu-id="27c94-146">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the Windows PowerShell (`Cert:`) drive.</span></span>

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

### <span data-ttu-id="27c94-147">-ContentType</span><span class="sxs-lookup"><span data-stu-id="27c94-147">-ContentType</span></span>

<span data-ttu-id="27c94-148">Anger webb begärans innehålls typ.</span><span class="sxs-lookup"><span data-stu-id="27c94-148">Specifies the content type of the web request.</span></span>

<span data-ttu-id="27c94-149">Om den här parametern utelämnas och metoden för begäran är POST, `Invoke-RestMethod` ställer in innehålls typen på "Application/x-www-form-urlencoded".</span><span class="sxs-lookup"><span data-stu-id="27c94-149">If this parameter is omitted and the request method is POST, `Invoke-RestMethod` sets the content type to "application/x-www-form-urlencoded".</span></span> <span data-ttu-id="27c94-150">Annars anges inte innehålls typen i anropet.</span><span class="sxs-lookup"><span data-stu-id="27c94-150">Otherwise, the content type is not specified in the call.</span></span>

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

### <span data-ttu-id="27c94-151">-Credential</span><span class="sxs-lookup"><span data-stu-id="27c94-151">-Credential</span></span>

<span data-ttu-id="27c94-152">Anger ett användar konto som har behörighet att skicka begäran.</span><span class="sxs-lookup"><span data-stu-id="27c94-152">Specifies a user account that has permission to send the request.</span></span> <span data-ttu-id="27c94-153">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="27c94-153">The default is the current user.</span></span>

<span data-ttu-id="27c94-154">Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="27c94-154">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="27c94-155">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="27c94-155">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="27c94-156">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="27c94-156">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="27c94-157">-DisableKeepAlive</span><span class="sxs-lookup"><span data-stu-id="27c94-157">-DisableKeepAlive</span></span>

<span data-ttu-id="27c94-158">Anger **keepalive** -värdet i HTTP-huvudet till false.</span><span class="sxs-lookup"><span data-stu-id="27c94-158">Sets the **KeepAlive** value in the HTTP header to False.</span></span> <span data-ttu-id="27c94-159">**Keepalive** är som standard sant.</span><span class="sxs-lookup"><span data-stu-id="27c94-159">By default, **KeepAlive** is True.</span></span>
<span data-ttu-id="27c94-160">**Keepalive** upprättar en permanent anslutning till servern för att under lätta efterföljande begär Anden.</span><span class="sxs-lookup"><span data-stu-id="27c94-160">**KeepAlive** establishes a persistent connection to the server to facilitate subsequent requests.</span></span>

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

### <span data-ttu-id="27c94-161">– Sidhuvud</span><span class="sxs-lookup"><span data-stu-id="27c94-161">-Headers</span></span>

<span data-ttu-id="27c94-162">Anger webb begärans rubriker.</span><span class="sxs-lookup"><span data-stu-id="27c94-162">Specifies the headers of the web request.</span></span> <span data-ttu-id="27c94-163">Ange en hash-tabell eller-ord lista.</span><span class="sxs-lookup"><span data-stu-id="27c94-163">Enter a hash table or dictionary.</span></span>

<span data-ttu-id="27c94-164">Om du vill ange UserAgent-rubriker använder du parametern **useragent** .</span><span class="sxs-lookup"><span data-stu-id="27c94-164">To set UserAgent headers, use the **UserAgent** parameter.</span></span> <span data-ttu-id="27c94-165">Du kan inte använda den här parametern för att ange UserAgent-eller cookie-rubriker.</span><span class="sxs-lookup"><span data-stu-id="27c94-165">You cannot use this parameter to specify UserAgent or cookie headers.</span></span>

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

### <span data-ttu-id="27c94-166">-INFILE</span><span class="sxs-lookup"><span data-stu-id="27c94-166">-InFile</span></span>

<span data-ttu-id="27c94-167">Hämtar innehållet i webb förfrågan från en fil.</span><span class="sxs-lookup"><span data-stu-id="27c94-167">Gets the content of the web request from a file.</span></span>

<span data-ttu-id="27c94-168">Ange en sökväg och ett fil namn.</span><span class="sxs-lookup"><span data-stu-id="27c94-168">Enter a path and file name.</span></span> <span data-ttu-id="27c94-169">Om du utelämnar sökvägen är standardvärdet den aktuella platsen.</span><span class="sxs-lookup"><span data-stu-id="27c94-169">If you omit the path, the default is the current location.</span></span>

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

### <span data-ttu-id="27c94-170">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="27c94-170">-MaximumRedirection</span></span>

<span data-ttu-id="27c94-171">Anger hur många gånger Windows PowerShell omdirigerar en anslutning till en alternativ Uniform Resource Identifier (URI) innan anslutningen Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="27c94-171">Determines how many times Windows PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="27c94-172">Standardvärdet är 5.</span><span class="sxs-lookup"><span data-stu-id="27c94-172">The default value is 5.</span></span> <span data-ttu-id="27c94-173">Värdet 0 (noll) förhindrar all omdirigering.</span><span class="sxs-lookup"><span data-stu-id="27c94-173">A value of 0 (zero) prevents all redirection.</span></span>

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

### <span data-ttu-id="27c94-174">-Metod</span><span class="sxs-lookup"><span data-stu-id="27c94-174">-Method</span></span>

<span data-ttu-id="27c94-175">Anger den metod som används för webb förfrågan.</span><span class="sxs-lookup"><span data-stu-id="27c94-175">Specifies the method used for the web request.</span></span> <span data-ttu-id="27c94-176">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="27c94-176">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="27c94-177">Default</span><span class="sxs-lookup"><span data-stu-id="27c94-177">Default</span></span>
- <span data-ttu-id="27c94-178">Ta bort</span><span class="sxs-lookup"><span data-stu-id="27c94-178">Delete</span></span>
- <span data-ttu-id="27c94-179">Hämta</span><span class="sxs-lookup"><span data-stu-id="27c94-179">Get</span></span>
- <span data-ttu-id="27c94-180">Head</span><span class="sxs-lookup"><span data-stu-id="27c94-180">Head</span></span>
- <span data-ttu-id="27c94-181">Sammanfoga</span><span class="sxs-lookup"><span data-stu-id="27c94-181">Merge</span></span>
- <span data-ttu-id="27c94-182">Alternativ</span><span class="sxs-lookup"><span data-stu-id="27c94-182">Options</span></span>
- <span data-ttu-id="27c94-183">Patch</span><span class="sxs-lookup"><span data-stu-id="27c94-183">Patch</span></span>
- <span data-ttu-id="27c94-184">Skicka</span><span class="sxs-lookup"><span data-stu-id="27c94-184">Post</span></span>
- <span data-ttu-id="27c94-185">Placera</span><span class="sxs-lookup"><span data-stu-id="27c94-185">Put</span></span>
- <span data-ttu-id="27c94-186">Spårning</span><span class="sxs-lookup"><span data-stu-id="27c94-186">Trace</span></span>

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

### <span data-ttu-id="27c94-187">-Fil</span><span class="sxs-lookup"><span data-stu-id="27c94-187">-OutFile</span></span>

<span data-ttu-id="27c94-188">Sparar svars texten i den angivna utdatafilen.</span><span class="sxs-lookup"><span data-stu-id="27c94-188">Saves the response body in the specified output file.</span></span> <span data-ttu-id="27c94-189">Ange en sökväg och ett fil namn.</span><span class="sxs-lookup"><span data-stu-id="27c94-189">Enter a path and file name.</span></span> <span data-ttu-id="27c94-190">Om du utelämnar sökvägen är standardvärdet den aktuella platsen.</span><span class="sxs-lookup"><span data-stu-id="27c94-190">If you omit the path, the default is the current location.</span></span>

<span data-ttu-id="27c94-191">Som standard `Invoke-RestMethod` returnerar resultatet till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="27c94-191">By default, `Invoke-RestMethod` returns the results to the pipeline.</span></span> <span data-ttu-id="27c94-192">Om du vill skicka resultatet till en fil och till pipelinen använder du parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="27c94-192">To send the results to a file and to the pipeline, use the **Passthru** parameter.</span></span>

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

### <span data-ttu-id="27c94-193">– PassThru</span><span class="sxs-lookup"><span data-stu-id="27c94-193">-PassThru</span></span>

<span data-ttu-id="27c94-194">Returnerar resultaten, förutom att skriva dem till en fil.</span><span class="sxs-lookup"><span data-stu-id="27c94-194">Returns the results, in addition to writing them to a file.</span></span> <span data-ttu-id="27c94-195">Den här parametern är endast giltig om **parametern out** också används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="27c94-195">This parameter is valid only when the **OutFile** parameter is also used in the command.</span></span>

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

### <span data-ttu-id="27c94-196">-Proxy</span><span class="sxs-lookup"><span data-stu-id="27c94-196">-Proxy</span></span>

<span data-ttu-id="27c94-197">Använder en proxyserver för begäran, i stället för att ansluta direkt till Internet resursen.</span><span class="sxs-lookup"><span data-stu-id="27c94-197">Uses a proxy server for the request, rather than connecting directly to the Internet resource.</span></span> <span data-ttu-id="27c94-198">Ange URI för en proxyserver för nätverket.</span><span class="sxs-lookup"><span data-stu-id="27c94-198">Enter the URI of a network proxy server.</span></span>

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

### <span data-ttu-id="27c94-199">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="27c94-199">-ProxyCredential</span></span>

<span data-ttu-id="27c94-200">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="27c94-200">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span> <span data-ttu-id="27c94-201">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="27c94-201">The default is the current user.</span></span>

<span data-ttu-id="27c94-202">Ange ett användar namn, till exempel "user01" eller "Domain01\User01", eller ange ett **PSCredential** -objekt, t. ex. ett som genererades av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="27c94-202">Type a user name, such as "User01" or "Domain01\User01", or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="27c94-203">Den här parametern är endast giltig när parametern **proxy** också används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="27c94-203">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="27c94-204">Du kan inte använda parametrarna **ProxyCredential** och **ProxyUseDefaultCredentials** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="27c94-204">You cannot use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="27c94-205">-ProxyUseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="27c94-205">-ProxyUseDefaultCredentials</span></span>

<span data-ttu-id="27c94-206">Använder autentiseringsuppgifterna för den aktuella användaren för att få åtkomst till proxyservern som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="27c94-206">Uses the credentials of the current user to access the proxy server that is specified by the **Proxy** parameter.</span></span>

<span data-ttu-id="27c94-207">Den här parametern är endast giltig när parametern **proxy** också används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="27c94-207">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="27c94-208">Du kan inte använda parametrarna **ProxyCredential** och **ProxyUseDefaultCredentials** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="27c94-208">You cannot use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="27c94-209">-SessionVariable</span><span class="sxs-lookup"><span data-stu-id="27c94-209">-SessionVariable</span></span>

<span data-ttu-id="27c94-210">Skapar en Webbbegäran-session och sparar den i värdet för den angivna variabeln.</span><span class="sxs-lookup"><span data-stu-id="27c94-210">Creates a web request session and saves it in the value of the specified variable.</span></span> <span data-ttu-id="27c94-211">Ange ett variabel namn utan dollar tecknet ( `$` )-symbolen.</span><span class="sxs-lookup"><span data-stu-id="27c94-211">Enter a variable name without the dollar sign (`$`) symbol.</span></span>

<span data-ttu-id="27c94-212">När du anger en sessionsvariabel `Invoke-RestMethod` skapar ett sessionsobjekt för Webbbegäran och tilldelar det till en variabel med det angivna namnet i PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="27c94-212">When you specify a session variable, `Invoke-RestMethod` creates a web request session object and assigns it to a variable with the specified name in your PowerShell session.</span></span> <span data-ttu-id="27c94-213">Du kan använda variabeln i din session så snart kommandot har slutförts.</span><span class="sxs-lookup"><span data-stu-id="27c94-213">You can use the variable in your session as soon as the command completes.</span></span>

<span data-ttu-id="27c94-214">Till skillnad från en fjärran sluten session är inte Webbbegäran-sessionen en permanent anslutning.</span><span class="sxs-lookup"><span data-stu-id="27c94-214">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="27c94-215">Det är ett objekt som innehåller information om anslutningen och begäran, inklusive cookies, autentiseringsuppgifter, det maximala värdet för omdirigering och användar agent strängen.</span><span class="sxs-lookup"><span data-stu-id="27c94-215">It is an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="27c94-216">Du kan använda den för att dela tillstånd och data mellan webb förfrågningar.</span><span class="sxs-lookup"><span data-stu-id="27c94-216">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="27c94-217">Om du vill använda Webbbegäran-sessionen i efterföljande webb förfrågningar, anger du variabeln session i värdet för **websession** -parametern.</span><span class="sxs-lookup"><span data-stu-id="27c94-217">To use the web request session in subsequent web requests, specify the session variable in the value of the **WebSession** parameter.</span></span> <span data-ttu-id="27c94-218">Windows PowerShell använder data i objektet Webbbegäran-session när den nya anslutningen upprättas.</span><span class="sxs-lookup"><span data-stu-id="27c94-218">Windows PowerShell uses the data in the web request session object when establishing the new connection.</span></span> <span data-ttu-id="27c94-219">Om du vill åsidosätta ett värde i Webbbegäran-sessionen använder du en cmdlet-parameter, till exempel **useragent** eller **Credential**.</span><span class="sxs-lookup"><span data-stu-id="27c94-219">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential**.</span></span> <span data-ttu-id="27c94-220">Parameter värden har företräde framför värden i Webbbegäran-sessionen.</span><span class="sxs-lookup"><span data-stu-id="27c94-220">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="27c94-221">Du kan inte använda parametrarna **SessionVariable** och **websession** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="27c94-221">You cannot use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="27c94-222">-TimeoutSec</span><span class="sxs-lookup"><span data-stu-id="27c94-222">-TimeoutSec</span></span>

<span data-ttu-id="27c94-223">Anger hur lång tid det tar att vänta på begäran innan den går ut. Ange ett värde i sekunder.</span><span class="sxs-lookup"><span data-stu-id="27c94-223">Specifies how long the request can be pending before it times out. Enter a value in seconds.</span></span> <span data-ttu-id="27c94-224">Standardvärdet 0 anger en obestämd tids gräns.</span><span class="sxs-lookup"><span data-stu-id="27c94-224">The default value, 0, specifies an indefinite time-out.</span></span>

<span data-ttu-id="27c94-225">En Domain Name System-fråga (DNS) kan ta upp till 15 sekunder att returnera eller ta slut för lång tid. Om din begäran innehåller ett värdnamn som kräver lösning och du anger TimeoutSec till ett värde som är större än noll, men mindre än 15 sekunder, kan det ta 15 sekunder eller mer innan en WebException utlöses, och tids gränsen för din begäran görs.</span><span class="sxs-lookup"><span data-stu-id="27c94-225">A Domain Name System (DNS) query can take up to 15 seconds to return or time out. If your request contains a host name that requires resolution, and you set TimeoutSec to a value greater than zero, but less than 15 seconds, it can take 15 seconds or more before a WebException is thrown, and your request times out.</span></span>

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

### <span data-ttu-id="27c94-226">-TransferEncoding</span><span class="sxs-lookup"><span data-stu-id="27c94-226">-TransferEncoding</span></span>

<span data-ttu-id="27c94-227">Anger ett värde för HTTP-svarshuvuden för överförings kodning.</span><span class="sxs-lookup"><span data-stu-id="27c94-227">Specifies a value for the transfer-encoding HTTP response header.</span></span> <span data-ttu-id="27c94-228">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="27c94-228">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="27c94-229">Segment vis</span><span class="sxs-lookup"><span data-stu-id="27c94-229">Chunked</span></span>
- <span data-ttu-id="27c94-230">Compress</span><span class="sxs-lookup"><span data-stu-id="27c94-230">Compress</span></span>
- <span data-ttu-id="27c94-231">DEFLATE</span><span class="sxs-lookup"><span data-stu-id="27c94-231">Deflate</span></span>
- <span data-ttu-id="27c94-232">GZip</span><span class="sxs-lookup"><span data-stu-id="27c94-232">GZip</span></span>
- <span data-ttu-id="27c94-233">Identitet</span><span class="sxs-lookup"><span data-stu-id="27c94-233">Identity</span></span>

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

### <span data-ttu-id="27c94-234">-URI</span><span class="sxs-lookup"><span data-stu-id="27c94-234">-Uri</span></span>

<span data-ttu-id="27c94-235">Anger Uniform Resource Identifier (URI) för den Internet resurs som webb förfrågan skickas till.</span><span class="sxs-lookup"><span data-stu-id="27c94-235">Specifies the Uniform Resource Identifier (URI) of the Internet resource to which the web request is sent.</span></span> <span data-ttu-id="27c94-236">Den här parametern stöder HTTP-, HTTPS-, FTP-och fil värden.</span><span class="sxs-lookup"><span data-stu-id="27c94-236">This parameter supports HTTP, HTTPS, FTP, and FILE values.</span></span>

<span data-ttu-id="27c94-237">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="27c94-237">This parameter is required.</span></span> <span data-ttu-id="27c94-238">Parameter namnet ( **URI** ) är valfritt.</span><span class="sxs-lookup"><span data-stu-id="27c94-238">The parameter name ( **Uri** ) is optional.</span></span>

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

### <span data-ttu-id="27c94-239">-UseBasicParsing</span><span class="sxs-lookup"><span data-stu-id="27c94-239">-UseBasicParsing</span></span>

<span data-ttu-id="27c94-240">Anger att cmdleten använder grundläggande parsning.</span><span class="sxs-lookup"><span data-stu-id="27c94-240">Indicates that the cmdlet uses basic parsing.</span></span> <span data-ttu-id="27c94-241">Cmdleten returnerar den råa HTML-koden i ett **String** -objekt.</span><span class="sxs-lookup"><span data-stu-id="27c94-241">The cmdlet returns the raw HTML in a **String** object.</span></span>

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

### <span data-ttu-id="27c94-242">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="27c94-242">-UseDefaultCredentials</span></span>

<span data-ttu-id="27c94-243">Använder autentiseringsuppgifterna för den aktuella användaren för att skicka webb förfrågan.</span><span class="sxs-lookup"><span data-stu-id="27c94-243">Uses the credentials of the current user to send the web request.</span></span>

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

### <span data-ttu-id="27c94-244">– UserAgent</span><span class="sxs-lookup"><span data-stu-id="27c94-244">-UserAgent</span></span>

<span data-ttu-id="27c94-245">Anger en användar agent sträng för webb förfrågan.</span><span class="sxs-lookup"><span data-stu-id="27c94-245">Specifies a user agent string for the web request.</span></span>

<span data-ttu-id="27c94-246">Standard användar agenten liknar "Mozilla/5.0 (Windows NT; Windows NT 6,1; en-US) WindowsPowerShell/3.0 "med små variationer för varje operativ system och plattform.</span><span class="sxs-lookup"><span data-stu-id="27c94-246">The default user agent is similar to "Mozilla/5.0 (Windows NT; Windows NT 6.1; en-US) WindowsPowerShell/3.0" with slight variations for each operating system and platform.</span></span>

<span data-ttu-id="27c94-247">Om du vill testa en webbplats med den standard användar agent sträng som används av de flesta webbläsare, använder du egenskaperna för [PSUserAgent](/dotnet/api/microsoft.powershell.commands) -klassen, till exempel Chrome, Firefox, Internet Explorer, Opera och Safari.</span><span class="sxs-lookup"><span data-stu-id="27c94-247">To test a website with the standard user agent string that is used by most Internet browsers, use the properties of the [PSUserAgent](/dotnet/api/microsoft.powershell.commands) class, such as Chrome, FireFox, Internet Explorer, Opera, and Safari.</span></span>

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

### <span data-ttu-id="27c94-248">– Websession</span><span class="sxs-lookup"><span data-stu-id="27c94-248">-WebSession</span></span>

<span data-ttu-id="27c94-249">Anger en Webbbegäran-session.</span><span class="sxs-lookup"><span data-stu-id="27c94-249">Specifies a web request session.</span></span> <span data-ttu-id="27c94-250">Ange variabel namnet, inklusive dollar tecknet ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="27c94-250">Enter the variable name, including the dollar sign (`$`).</span></span>

<span data-ttu-id="27c94-251">Om du vill åsidosätta ett värde i Webbbegäran-sessionen använder du en cmdlet-parameter, till exempel **useragent** eller **Credential**.</span><span class="sxs-lookup"><span data-stu-id="27c94-251">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential**.</span></span> <span data-ttu-id="27c94-252">Parameter värden har företräde framför värden i Webbbegäran-sessionen.</span><span class="sxs-lookup"><span data-stu-id="27c94-252">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="27c94-253">Till skillnad från en fjärran sluten session är inte Webbbegäran-sessionen en permanent anslutning.</span><span class="sxs-lookup"><span data-stu-id="27c94-253">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="27c94-254">Det är ett objekt som innehåller information om anslutningen och begäran, inklusive cookies, autentiseringsuppgifter, det maximala värdet för omdirigering och användar agent strängen.</span><span class="sxs-lookup"><span data-stu-id="27c94-254">It is an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="27c94-255">Du kan använda den för att dela tillstånd och data mellan webb förfrågningar.</span><span class="sxs-lookup"><span data-stu-id="27c94-255">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="27c94-256">Om du vill skapa en Webbbegäran-session anger du ett variabel namn (utan dollar tecken) i värdet för parametern **SessionVariable** för ett `Invoke-RestMethod` kommando.</span><span class="sxs-lookup"><span data-stu-id="27c94-256">To create a web request session, enter a variable name (without a dollar sign) in the value of the **SessionVariable** parameter of an `Invoke-RestMethod` command.</span></span> <span data-ttu-id="27c94-257">`Invoke-RestMethod` skapar sessionen och sparar den i variabeln.</span><span class="sxs-lookup"><span data-stu-id="27c94-257">`Invoke-RestMethod` creates the session and saves it in the variable.</span></span> <span data-ttu-id="27c94-258">I efterföljande kommandon använder du variabeln som värde för **websession** -parametern.</span><span class="sxs-lookup"><span data-stu-id="27c94-258">In subsequent commands, use the variable as the value of the **WebSession** parameter.</span></span>

<span data-ttu-id="27c94-259">Du kan inte använda parametrarna **SessionVariable** och **websession** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="27c94-259">You cannot use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="27c94-260">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="27c94-260">CommonParameters</span></span>

<span data-ttu-id="27c94-261">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="27c94-261">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="27c94-262">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="27c94-262">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="27c94-263">Indata</span><span class="sxs-lookup"><span data-stu-id="27c94-263">Inputs</span></span>

### <span data-ttu-id="27c94-264">System. Object</span><span class="sxs-lookup"><span data-stu-id="27c94-264">System.Object</span></span>

<span data-ttu-id="27c94-265">Du kan skicka vidare innehållet i en webb förfrågan till `Invoke-RestMethod` .</span><span class="sxs-lookup"><span data-stu-id="27c94-265">You can pipe the body of a web request to `Invoke-RestMethod`.</span></span>

## <span data-ttu-id="27c94-266">Utdata</span><span class="sxs-lookup"><span data-stu-id="27c94-266">Outputs</span></span>

### <span data-ttu-id="27c94-267">System.Xml.Xmldokument Microsoft.PowerShell.Commands.HtmlWebResponseObject, system. String</span><span class="sxs-lookup"><span data-stu-id="27c94-267">System.Xml.XmlDocument, Microsoft.PowerShell.Commands.HtmlWebResponseObject, System.String</span></span>

<span data-ttu-id="27c94-268">Utdata från cmdleten beror på formatet på det innehåll som hämtas.</span><span class="sxs-lookup"><span data-stu-id="27c94-268">The output of the cmdlet depends upon the format of the content that is retrieved.</span></span>

### <span data-ttu-id="27c94-269">PSObject</span><span class="sxs-lookup"><span data-stu-id="27c94-269">PSObject</span></span>

<span data-ttu-id="27c94-270">Om begäran returnerar JSON-strängar `Invoke-RestMethod` returnerar en PSObject som representerar strängarna.</span><span class="sxs-lookup"><span data-stu-id="27c94-270">If the request returns JSON strings, `Invoke-RestMethod` returns a PSObject that represents the strings.</span></span>

## <span data-ttu-id="27c94-271">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="27c94-271">Notes</span></span>

## <span data-ttu-id="27c94-272">Relaterade länkar</span><span class="sxs-lookup"><span data-stu-id="27c94-272">Related Links</span></span>

[<span data-ttu-id="27c94-273">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="27c94-273">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="27c94-274">ConvertFrom – JSON</span><span class="sxs-lookup"><span data-stu-id="27c94-274">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="27c94-275">Anropa-webbegäran</span><span class="sxs-lookup"><span data-stu-id="27c94-275">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)
