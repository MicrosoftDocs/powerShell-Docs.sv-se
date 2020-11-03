---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-webrequest?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WebRequest
ms.openlocfilehash: 09270fd74fd256858faacaae399e05b40985ddb5
ms.sourcegitcommit: 9a6b6714ded4edb5119f1b82a253608018ea6b98
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/10/2020
ms.locfileid: "93269109"
---
# <span data-ttu-id="c8c9e-103">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="c8c9e-103">Invoke-WebRequest</span></span>

## <span data-ttu-id="c8c9e-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="c8c9e-104">SYNOPSIS</span></span>
<span data-ttu-id="c8c9e-105">Hämtar innehåll från en webb sida på Internet.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-105">Gets content from a web page on the internet.</span></span>

## <span data-ttu-id="c8c9e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c8c9e-106">SYNTAX</span></span>

### <span data-ttu-id="c8c9e-107">StandardMethod (standard)</span><span class="sxs-lookup"><span data-stu-id="c8c9e-107">StandardMethod (Default)</span></span>

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
 [-OutFile <String>] [-PassThru] [-Resume] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### <span data-ttu-id="c8c9e-108">StandardMethodNoProxy</span><span class="sxs-lookup"><span data-stu-id="c8c9e-108">StandardMethodNoProxy</span></span>

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>]
 [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] [-Method <WebRequestMethod>] -NoProxy
 [-Body <Object>] [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>]
 [-InFile <String>] [-OutFile <String>] [-PassThru] [-Resume] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### <span data-ttu-id="c8c9e-109">CustomMethod</span><span class="sxs-lookup"><span data-stu-id="c8c9e-109">CustomMethod</span></span>

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
 [-OutFile <String>] [-PassThru] [-Resume] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### <span data-ttu-id="c8c9e-110">CustomMethodNoProxy</span><span class="sxs-lookup"><span data-stu-id="c8c9e-110">CustomMethodNoProxy</span></span>

```
Invoke-WebRequest [-UseBasicParsing] [-Uri] <Uri> [-WebSession <WebRequestSession>]
 [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] -CustomMethod <String> -NoProxy
 [-Body <Object>] [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>]
 [-InFile <String>] [-OutFile <String>] [-PassThru] [-Resume] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

## <span data-ttu-id="c8c9e-111">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="c8c9e-111">DESCRIPTION</span></span>

<span data-ttu-id="c8c9e-112">`Invoke-WebRequest`Cmdlet: en skickar HTTP-och HTTPS-begäranden till en webb sida eller en webb tjänst.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-112">The `Invoke-WebRequest` cmdlet sends HTTP and HTTPS requests to a web page or web service.</span></span> <span data-ttu-id="c8c9e-113">Den tolkar svaret och returnerar samlingar med länkar, bilder och andra viktiga HTML-element.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-113">It parses the response and returns collections of links, images, and other significant HTML elements.</span></span>

<span data-ttu-id="c8c9e-114">Denna cmdlet introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-114">This cmdlet was introduced in PowerShell 3.0.</span></span>

## <span data-ttu-id="c8c9e-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="c8c9e-115">EXAMPLES</span></span>

### <span data-ttu-id="c8c9e-116">Exempel 1: skicka en webb förfrågan</span><span class="sxs-lookup"><span data-stu-id="c8c9e-116">Example 1: Send a web request</span></span>

<span data-ttu-id="c8c9e-117">I det här exemplet används `Invoke-WebRequest` cmdleten för att skicka en webbegäran till Bing.com-webbplatsen.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-117">This example uses the `Invoke-WebRequest` cmdlet to send a web request to the Bing.com site.</span></span>

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

<span data-ttu-id="c8c9e-118">Det första kommandot utfärdar begäran och sparar svaret i `$Response` variabeln.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-118">The first command issues the request and saves the response in the `$Response` variable.</span></span>

<span data-ttu-id="c8c9e-119">Det andra kommandot hämtar alla **InputField** där **namn** -egenskapen är som `"* Value"` .</span><span class="sxs-lookup"><span data-stu-id="c8c9e-119">The second command gets any **InputField** where the **Name** property is like `"* Value"`.</span></span> <span data-ttu-id="c8c9e-120">De filtrerade resultaten är skickas för `Select-Object` att välja egenskaper för **namn** och **värde** .</span><span class="sxs-lookup"><span data-stu-id="c8c9e-120">The filtered results are piped to `Select-Object` to select the **Name** and **Value** properties.</span></span>

### <span data-ttu-id="c8c9e-121">Exempel 2: använda en tillstånds känslig webb tjänst</span><span class="sxs-lookup"><span data-stu-id="c8c9e-121">Example 2: Use a stateful web service</span></span>

<span data-ttu-id="c8c9e-122">Det här exemplet visar hur du använder `Invoke-WebRequest` cmdleten med en tillstånds känslig webb tjänst.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-122">This example shows how to use the `Invoke-WebRequest` cmdlet with a stateful web service.</span></span>

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

<span data-ttu-id="c8c9e-123">Det första anropet för att `Invoke-WebRequest` skicka en inloggnings förfrågan.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-123">The first call to `Invoke-WebRequest` sends a sign-in request.</span></span> <span data-ttu-id="c8c9e-124">Kommandot anger värdet "session" för värdet för parametern **-SessionVariable** och sparar resultatet i `$LoginResponse` variabeln.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-124">The command specifies a value of "Session" for the value of the **-SessionVariable** parameter, and saves the result in the `$LoginResponse` variable.</span></span> <span data-ttu-id="c8c9e-125">När kommandot har slutförts `$LoginResponse` innehåller variabeln en `BasicHtmlWebResponseObject` och `$Session` variabeln innehåller ett `WebRequestSession` objekt.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-125">When the command completes, the `$LoginResponse` variable contains an `BasicHtmlWebResponseObject` and the `$Session` variable contains a `WebRequestSession` object.</span></span> <span data-ttu-id="c8c9e-126">Detta loggar användaren på platsen.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-126">This logs the user into the site.</span></span>

<span data-ttu-id="c8c9e-127">Anropet till `$Session` själva visar `WebRequestSession` objektet i variabeln.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-127">The call to `$Session` by itself shows the `WebRequestSession` object in the variable.</span></span>

<span data-ttu-id="c8c9e-128">Det andra anropet för att `Invoke-WebRequest` Hämta användarens profil som kräver att användaren är inloggad på platsen.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-128">The second call to `Invoke-WebRequest` fetches the user's profile which requires that the user be logged into the site.</span></span> <span data-ttu-id="c8c9e-129">De sessionsdata som lagras i `$Session` variabeln används för att tillhandahålla sessionscookies till den plats som skapas under inloggningen.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-129">The session data stored in the `$Session` variable is used to provide session cookies to the site created during the login.</span></span> <span data-ttu-id="c8c9e-130">Resultatet sparas i `$ProfileResponse` variabeln.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-130">The result is saved in the `$ProfileResponse` variable.</span></span>

<span data-ttu-id="c8c9e-131">Anropet till `$ProfileResponse` själva visar `BasicHtmlWebResponseObject` i variabeln.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-131">The call to `$ProfileResponse` by itself shows the `BasicHtmlWebResponseObject` in the variable.</span></span>

### <span data-ttu-id="c8c9e-132">Exempel 3: Hämta länkar från en webb sida</span><span class="sxs-lookup"><span data-stu-id="c8c9e-132">Example 3: Get links from a web page</span></span>

<span data-ttu-id="c8c9e-133">Det här exemplet hämtar länkarna på en webb sida.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-133">This example gets the links in a web page.</span></span> <span data-ttu-id="c8c9e-134">Den använder `Invoke-WebRequest` cmdleten för att hämta innehållet på webb sidan.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-134">It uses the `Invoke-WebRequest` cmdlet to get the web page content.</span></span> <span data-ttu-id="c8c9e-135">Sedan använder den egenskapen **Links** för den `BasicHtmlWebResponseObject` som `Invoke-WebRequest` returnerar och egenskapen **href** för varje länk.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-135">Then it uses the **Links** property of the `BasicHtmlWebResponseObject` that `Invoke-WebRequest` returns, and the **Href** property of each link.</span></span>

```powershell
(Invoke-WebRequest -Uri "https://aka.ms/pscore6-docs").Links.Href
```

### <span data-ttu-id="c8c9e-136">Exempel 4: skriver svars innehållet till en fil med hjälp av den kodning som definierats på den begärda sidan.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-136">Example 4: Writes the response content to a file using the encoding defined in the requested page.</span></span>

<span data-ttu-id="c8c9e-137">I det här exemplet används `Invoke-WebRequest` cmdleten för att hämta webb sidans innehåll på en PowerShell-dokumentations sida.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-137">This example uses the `Invoke-WebRequest` cmdlet to retrieve the web page content of a PowerShell documentation page.</span></span>

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

<span data-ttu-id="c8c9e-138">Det första kommandot hämtar sidan och sparar objektet Response i `$Response` variabeln.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-138">The first command retrieves the page and saves the response object in the `$Response` variable.</span></span>

<span data-ttu-id="c8c9e-139">Det andra kommandot skapar en `StreamWriter` som ska användas för att skriva svars innehållet till en fil.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-139">The second command creates a `StreamWriter` to use to write the response content to a file.</span></span> <span data-ttu-id="c8c9e-140">Egenskapen **encoding** för Response-objektet används för att ange filens kodning.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-140">The **Encoding** property of the response object is used to set the encoding for the file.</span></span>

<span data-ttu-id="c8c9e-141">De slutliga kommandona skriver **innehålls** egenskapen till filen och tar sedan bort `StreamWriter` .</span><span class="sxs-lookup"><span data-stu-id="c8c9e-141">The final few commands write the **Content** property to the file then disposes the `StreamWriter`.</span></span>

<span data-ttu-id="c8c9e-142">Observera att **encoding** -egenskapen är null om Webbbegäran inte returnerar text innehåll.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-142">Note that the **Encoding** property is null if the web request doesn't return text content.</span></span>

### <span data-ttu-id="c8c9e-143">Exempel 5: skicka en multipart-/formulär data fil</span><span class="sxs-lookup"><span data-stu-id="c8c9e-143">Example 5: Submit a multipart/form-data file</span></span>

<span data-ttu-id="c8c9e-144">I det här exemplet används `Invoke-WebRequest` cmdleten Ladda upp en fil som ett `multipart/form-data` överförings objekt.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-144">This example uses the `Invoke-WebRequest` cmdlet upload a file as a `multipart/form-data` submission.</span></span> <span data-ttu-id="c8c9e-145">Filen `c:\document.txt` skickas som ett formulär fält `document` med `Content-Type` för `text/plain` .</span><span class="sxs-lookup"><span data-stu-id="c8c9e-145">The file `c:\document.txt` is submitted as the form field `document` with the `Content-Type` of `text/plain`.</span></span>

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

### <span data-ttu-id="c8c9e-146">Exempel 6: överföring av förenklad multipart/form – data</span><span class="sxs-lookup"><span data-stu-id="c8c9e-146">Example 6: Simplified Multipart/Form-Data Submission</span></span>

<span data-ttu-id="c8c9e-147">Vissa API: er kräver att det går `multipart/form-data` att överföra filer och blandat innehåll.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-147">Some APIs require `multipart/form-data` submissions to upload files and mixed content.</span></span> <span data-ttu-id="c8c9e-148">I det här exemplet visas hur du uppdaterar en användar profil.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-148">This example demonstrates updating a user profile.</span></span>

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

<span data-ttu-id="c8c9e-149">Profil formuläret kräver följande fält:,,,, `firstName` `lastName` `email` `avatar` `birthday` och `hobbies` .</span><span class="sxs-lookup"><span data-stu-id="c8c9e-149">The profile form requires these fields: `firstName`, `lastName`, `email`, `avatar`, `birthday`, and `hobbies`.</span></span> <span data-ttu-id="c8c9e-150">API: et förväntar sig en bild för användar profils pic som ska anges i `avatar` fältet.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-150">The API is expecting an image for the user profile pic to be supplied in the `avatar` field.</span></span> <span data-ttu-id="c8c9e-151">API: et accepterar också `hobbies` att flera poster skickas i samma formulär.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-151">The API also accepts multiple `hobbies` entries to be submitted in the same form.</span></span>

<span data-ttu-id="c8c9e-152">När du skapar en `$Form` hash-tabellen används nyckel namnen som namn på formulär fält.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-152">When creating the `$Form` HashTable, the key names are used as form field names.</span></span> <span data-ttu-id="c8c9e-153">Som standard konverteras värdena för hash-tabellen till strängar.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-153">By default, the values of the HashTable are converted to strings.</span></span> <span data-ttu-id="c8c9e-154">Om det finns ett **system. io. fileinfo** -värde skickas filens innehåll.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-154">If a **System.IO.FileInfo** value is present, the file contents are submitted.</span></span> <span data-ttu-id="c8c9e-155">Om det finns en samling, till exempel matriser eller listor, skickas formulär fältet flera gånger.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-155">If a collection such as arrays or lists are present, the form field is submitted multiple times.</span></span>

<span data-ttu-id="c8c9e-156">Genom `Get-Item` att använda på `avatar` nyckeln `FileInfo` anges objektet som värde.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-156">By using `Get-Item` on the `avatar` key, the `FileInfo` object is set as the value.</span></span> <span data-ttu-id="c8c9e-157">Resultatet är att avbildnings data för `jdoe.png` skickas.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-157">The result is that the image data for `jdoe.png` is submitted.</span></span>

<span data-ttu-id="c8c9e-158">Om du anger en lista till `hobbies` nyckeln, finns `hobbies` fältet i under sändningarna en gång för varje List objekt.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-158">By supplying a list to the `hobbies` key, the `hobbies` field is present in the submissions once for each list item.</span></span>

### <span data-ttu-id="c8c9e-159">Exempel 7: fånga meddelanden som inte lyckades från Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="c8c9e-159">Example 7: Catch non success messages from Invoke-WebRequest</span></span>

<span data-ttu-id="c8c9e-160">När `Invoke-WebRequest` påträffar ett HTTP-meddelande som inte lyckades (404, 500 osv.) returnerar det inga utdata och returnerar ett avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-160">When `Invoke-WebRequest` encounters a non-success HTTP message (404, 500, etc.), it returns no output and throws a terminating error.</span></span> <span data-ttu-id="c8c9e-161">Om du vill fånga felet och visa **StatusCode** kan du sätta igång i ett `try/catch` block.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-161">To catch the error and view the **StatusCode** you can enclose execution in a `try/catch` block.</span></span>

```powershell
try
{
    $Response = Invoke-WebRequest -Uri "www.microsoft.com/unkownhost" -ErrorAction Stop
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

<span data-ttu-id="c8c9e-162">Kommandot anropar `Invoke-WebRequest` med en **ErrorAction** av **stopp** , som tvingar fram `Invoke-WebRequest` ett avslutande fel vid eventuella misslyckade förfrågningar.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-162">The command calls `Invoke-WebRequest` with an **ErrorAction** of **Stop** , which forces `Invoke-WebRequest` to throw a terminating error on any failed requests.</span></span> <span data-ttu-id="c8c9e-163">Det avslutande felet fångas av `catch` blocket som hämtar **StatusCode** från **Exception** -objektet.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-163">The terminating error is caught by the `catch` block which retrieves the **StatusCode** from the **Exception** object.</span></span>

## <span data-ttu-id="c8c9e-164">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="c8c9e-164">PARAMETERS</span></span>

### <span data-ttu-id="c8c9e-165">-AllowUnencryptedAuthentication</span><span class="sxs-lookup"><span data-stu-id="c8c9e-165">-AllowUnencryptedAuthentication</span></span>

<span data-ttu-id="c8c9e-166">Tillåter sändning av autentiseringsuppgifter och hemligheter över okrypterade anslutningar.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-166">Allows sending of credentials and secrets over unencrypted connections.</span></span> <span data-ttu-id="c8c9e-167">Som standard anger **Credential** eller valfritt **autentiseringsalternativ** med en **URI** som inte börjar med `https://` resulterar i ett fel och begäran avbryts för att förhindra oavsiktlig kommunikation av hemligheter i oformaterad text över okrypterade anslutningar.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-167">By default, supplying **Credential** or any **Authentication** option with a **Uri** that does not begin with `https://` results in an error and the request is aborted to prevent unintentionally communicating secrets in plain text over unencrypted connections.</span></span> <span data-ttu-id="c8c9e-168">Om du vill åsidosätta det här beteendet på egen risk anger du parametern **AllowUnencryptedAuthentication** .</span><span class="sxs-lookup"><span data-stu-id="c8c9e-168">To override this behavior at your own risk, supply the **AllowUnencryptedAuthentication** parameter.</span></span>

> [!WARNING]
> <span data-ttu-id="c8c9e-169">Att använda den här parametern är inte säkert och rekommenderas inte.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-169">Using this parameter is not secure and is not recommended.</span></span> <span data-ttu-id="c8c9e-170">Det tillhandahålls endast för kompatibilitet med äldre system som inte kan tillhandahålla krypterade anslutningar.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-170">It is provided only for compatibility with legacy systems that cannot provide encrypted connections.</span></span> <span data-ttu-id="c8c9e-171">Använd på egen risk.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-171">Use at your own risk.</span></span>

<span data-ttu-id="c8c9e-172">Den här funktionen har lagts till i PowerShell-6.0.0.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-172">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="c8c9e-173">-Autentisering</span><span class="sxs-lookup"><span data-stu-id="c8c9e-173">-Authentication</span></span>

<span data-ttu-id="c8c9e-174">Anger den explicita autentiseringstypen som ska användas för begäran.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-174">Specifies the explicit authentication type to use for the request.</span></span> <span data-ttu-id="c8c9e-175">Standardvärdet är **none**.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-175">The default is **None**.</span></span>
<span data-ttu-id="c8c9e-176">Det går inte att använda **autentisering** med **UseDefaultCredentials**.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-176">**Authentication** cannot be used with **UseDefaultCredentials**.</span></span>

<span data-ttu-id="c8c9e-177">Tillgängliga autentiserings alternativ:</span><span class="sxs-lookup"><span data-stu-id="c8c9e-177">Available Authentication Options:</span></span>

- <span data-ttu-id="c8c9e-178">**Ingen** : det här är standard alternativet när **autentisering** inte anges. ingen explicit autentisering används.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-178">**None** : This is the default option when **Authentication** isn't supplied; no explicit authentication is used.</span></span>
- <span data-ttu-id="c8c9e-179">**Basic** : kräver **autentiseringsuppgifter**.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-179">**Basic** : Requires **Credential**.</span></span> <span data-ttu-id="c8c9e-180">Autentiseringsuppgifterna skickas i ett RFC 7617 Basic Authentication-huvud i formatet `base64(user:password)` .</span><span class="sxs-lookup"><span data-stu-id="c8c9e-180">The credentials are sent in an RFC 7617 Basic Authentication header in the format of `base64(user:password)`.</span></span>
- <span data-ttu-id="c8c9e-181">**Bearer** : kräver **token**.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-181">**Bearer** : Requires **Token**.</span></span> <span data-ttu-id="c8c9e-182">Skickar ett RFC 6750- `Authorization: Bearer` huvud med angiven token.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-182">Sends an RFC 6750 `Authorization: Bearer` header with the supplied token.</span></span> <span data-ttu-id="c8c9e-183">Detta är ett alias för **OAuth**</span><span class="sxs-lookup"><span data-stu-id="c8c9e-183">This is an alias for **OAuth**</span></span>
- <span data-ttu-id="c8c9e-184">**OAuth** : kräver **token**.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-184">**OAuth** : Requires **Token**.</span></span> <span data-ttu-id="c8c9e-185">Skickar ett RFC 6750- `Authorization: Bearer` huvud med angiven token.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-185">Sends an RFC 6750 `Authorization: Bearer` header with the supplied token.</span></span> <span data-ttu-id="c8c9e-186">Detta är ett alias för **innehavare**</span><span class="sxs-lookup"><span data-stu-id="c8c9e-186">This is an alias for **Bearer**</span></span>

<span data-ttu-id="c8c9e-187">Att tillhandahålla **autentisering** åsidosätter alla `Authorization` rubriker som har angetts för **sidhuvuden** eller ingår i **websession**.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-187">Supplying **Authentication** overrides any `Authorization` headers supplied to **Headers** or included in **WebSession**.</span></span>

<span data-ttu-id="c8c9e-188">Den här funktionen har lagts till i PowerShell-6.0.0.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-188">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="c8c9e-189">-Body</span><span class="sxs-lookup"><span data-stu-id="c8c9e-189">-Body</span></span>

<span data-ttu-id="c8c9e-190">Anger bröd texten i begäran.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-190">Specifies the body of the request.</span></span> <span data-ttu-id="c8c9e-191">Bröd texten är innehållet i begäran som följer sidhuvuden.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-191">The body is the content of the request that follows the headers.</span></span>
<span data-ttu-id="c8c9e-192">Du kan också skicka ett Body-värde till `Invoke-WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="c8c9e-192">You can also pipe a body value to `Invoke-WebRequest`.</span></span>

<span data-ttu-id="c8c9e-193">Du kan använda **text** parametern för att ange en lista över frågeparametrar eller ange svarets innehåll.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-193">The **Body** parameter can be used to specify a list of query parameters or specify the content of the response.</span></span>

<span data-ttu-id="c8c9e-194">När indatamängden är en GET-begäran och texten är en `IDictionary` (vanligt vis en hash-tabell) läggs bröd texten till i URI: n som frågeparametrar.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-194">When the input is a GET request and the body is an `IDictionary` (typically, a hash table), the body is added to the URI as query parameters.</span></span> <span data-ttu-id="c8c9e-195">För andra typer av begär Anden (till exempel POST) anges bröd texten som värde för begär ande texten i `name=value` standardformat.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-195">For other request types (such as POST), the body is set as the value of the request body in the standard `name=value` format.</span></span>

<span data-ttu-id="c8c9e-196">**Bröd text** parametern kan också acceptera ett `System.Net.Http.MultipartFormDataContent` objekt.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-196">The **Body** parameter may also accept a `System.Net.Http.MultipartFormDataContent` object.</span></span> <span data-ttu-id="c8c9e-197">Detta underlättar `multipart/form-data` förfrågningar.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-197">This facilitates `multipart/form-data` requests.</span></span> <span data-ttu-id="c8c9e-198">När ett **MultipartFormDataContent** -objekt anges för **brödtext** , åsidosätts alla innehåll relaterade rubriker som har angetts för egenskaperna **ContentType** , **headers** eller **websession** av **MultipartFormDataContent** -objektets innehålls rubriker.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-198">When a **MultipartFormDataContent** object is supplied for **Body** , any Content related headers supplied to the **ContentType** , **Headers** , or **WebSession** parameters is overridden by the Content headers of the **MultipartFormDataContent** object.</span></span> <span data-ttu-id="c8c9e-199">Den här funktionen har lagts till i PowerShell-6.0.0.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-199">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="c8c9e-200">– Certifikat</span><span class="sxs-lookup"><span data-stu-id="c8c9e-200">-Certificate</span></span>

<span data-ttu-id="c8c9e-201">Anger det klient certifikat som används för en säker webb förfrågan.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-201">Specifies the client certificate that's used for a secure web request.</span></span> <span data-ttu-id="c8c9e-202">Ange en variabel som innehåller ett certifikat eller ett kommando eller uttryck som hämtar certifikatet.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-202">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="c8c9e-203">Om du vill söka efter ett certifikat använder `Get-PfxCertificate` eller använder du `Get-ChildItem` cmdleten på certifikat `Cert:` enheten ().</span><span class="sxs-lookup"><span data-stu-id="c8c9e-203">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the Certificate (`Cert:`) drive.</span></span> <span data-ttu-id="c8c9e-204">Om certifikatet inte är giltigt eller inte har tillräcklig behörighet, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-204">If the certificate isn't valid or doesn't have sufficient authority, the command fails.</span></span>

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

### <span data-ttu-id="c8c9e-205">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="c8c9e-205">-CertificateThumbprint</span></span>

<span data-ttu-id="c8c9e-206">Anger det digitala certifikat för offentlig nyckel (X509) för ett användar konto som har behörighet att skicka begäran.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-206">Specifies the digital public key certificate (X509) of a user account that has permission to send the request.</span></span> <span data-ttu-id="c8c9e-207">Ange certifikatets tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-207">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="c8c9e-208">Certifikat används i klient certifikat-baserad autentisering.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-208">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="c8c9e-209">De kan endast mappas till lokala användar konton. de fungerar inte med domän konton.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-209">They can be mapped only to local user accounts; they don't work with domain accounts.</span></span>

<span data-ttu-id="c8c9e-210">Om du vill hämta ett tumavtryck för certifikatet använder du `Get-Item` `Get-ChildItem` kommandot eller i PowerShell- `Cert:` enheten.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-210">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the PowerShell `Cert:` drive.</span></span>

> [!NOTE]
> <span data-ttu-id="c8c9e-211">Den här funktionen stöds för närvarande endast på Windows OS-plattformar.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-211">This feature is currently only supported on Windows OS platforms.</span></span>

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

### <span data-ttu-id="c8c9e-212">-ContentType</span><span class="sxs-lookup"><span data-stu-id="c8c9e-212">-ContentType</span></span>

<span data-ttu-id="c8c9e-213">Anger webb begärans innehålls typ.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-213">Specifies the content type of the web request.</span></span>

<span data-ttu-id="c8c9e-214">Om den här parametern utelämnas och metoden för begäran är POST, `Invoke-WebRequest` anger innehålls typen till `application/x-www-form-urlencoded` .</span><span class="sxs-lookup"><span data-stu-id="c8c9e-214">If this parameter is omitted and the request method is POST, `Invoke-WebRequest` sets the content type to `application/x-www-form-urlencoded`.</span></span> <span data-ttu-id="c8c9e-215">Annars anges inte innehålls typen i anropet.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-215">Otherwise, the content type isn't specified in the call.</span></span>

<span data-ttu-id="c8c9e-216">**ContentType** åsidosätts när ett **MultipartFormDataContent** -objekt anges för **brödtext**.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-216">**ContentType** is overridden when a **MultipartFormDataContent** object is supplied for **Body**.</span></span>

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

### <span data-ttu-id="c8c9e-217">-Credential</span><span class="sxs-lookup"><span data-stu-id="c8c9e-217">-Credential</span></span>

<span data-ttu-id="c8c9e-218">Anger ett användar konto som har behörighet att skicka begäran.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-218">Specifies a user account that has permission to send the request.</span></span> <span data-ttu-id="c8c9e-219">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-219">The default is the current user.</span></span>

<span data-ttu-id="c8c9e-220">Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-220">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="c8c9e-221">**Autentiseringsuppgifter** kan användas separat eller tillsammans med vissa parametrar för **autentiseringsprinciper** .</span><span class="sxs-lookup"><span data-stu-id="c8c9e-221">**Credential** can be used alone or in conjunction with certain **Authentication** parameter options.</span></span> <span data-ttu-id="c8c9e-222">När den används enbart, anger den bara autentiseringsuppgifter för fjärrservern om fjärrservern skickar en begäran om autentisering av begäran.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-222">When used alone, it only supplies credentials to the remote server if the remote server sends an authentication challenge request.</span></span> <span data-ttu-id="c8c9e-223">När den används med **autentiseringsalternativ** skickas autentiseringsuppgifterna uttryckligen.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-223">When used with **Authentication** options, the credentials are explicitly sent.</span></span>

<span data-ttu-id="c8c9e-224">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="c8c9e-224">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="c8c9e-225">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="c8c9e-225">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="c8c9e-226">-CustomMethod</span><span class="sxs-lookup"><span data-stu-id="c8c9e-226">-CustomMethod</span></span>

<span data-ttu-id="c8c9e-227">Anger en anpassad metod som används för webb förfrågan.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-227">Specifies a custom method used for the web request.</span></span> <span data-ttu-id="c8c9e-228">Detta kan användas om den begär ande metoden som krävs av slut punkten inte är ett tillgängligt alternativ för **metoden**.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-228">This can be used if the Request Method required by the endpoint isn't an available option on the **Method**.</span></span> <span data-ttu-id="c8c9e-229">**Metoden** och **CustomMethod** kan inte användas tillsammans.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-229">**Method** and **CustomMethod** can't be used together.</span></span>

<span data-ttu-id="c8c9e-230">Det här exemplet gör en `TEST` http-begäran till API: et:</span><span class="sxs-lookup"><span data-stu-id="c8c9e-230">This example makes a `TEST` HTTP request to the API:</span></span>

`Invoke-WebRequest -uri 'https://api.contoso.com/widget/' -CustomMethod 'TEST'`

<span data-ttu-id="c8c9e-231">Den här funktionen har lagts till i PowerShell-6.0.0.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-231">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="c8c9e-232">-DisableKeepAlive</span><span class="sxs-lookup"><span data-stu-id="c8c9e-232">-DisableKeepAlive</span></span>

<span data-ttu-id="c8c9e-233">Anger att cmdleten anger **keepalive** -värdet i HTTP-huvudet till **false**.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-233">Indicates that the cmdlet sets the **KeepAlive** value in the HTTP header to **False**.</span></span> <span data-ttu-id="c8c9e-234">**Keepalive** är som standard **Sant**.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-234">By default, **KeepAlive** is **True**.</span></span> <span data-ttu-id="c8c9e-235">**Keepalive** upprättar en permanent anslutning till servern för att under lätta efterföljande begär Anden.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-235">**KeepAlive** establishes a persistent connection to the server to facilitate subsequent requests.</span></span>

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

### <span data-ttu-id="c8c9e-236">-Form</span><span class="sxs-lookup"><span data-stu-id="c8c9e-236">-Form</span></span>

<span data-ttu-id="c8c9e-237">Konverterar en ord lista till ett `multipart/form-data` överförings objekt.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-237">Converts a dictionary to a `multipart/form-data` submission.</span></span> <span data-ttu-id="c8c9e-238">**Formulär** får inte användas med **brödtext**.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-238">**Form** may not be used with **Body**.</span></span>
<span data-ttu-id="c8c9e-239">Om **ContentType** används ignoreras det.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-239">If **ContentType** is used, it's ignored.</span></span>

<span data-ttu-id="c8c9e-240">Nycklarna i ord listan används som formulär fält namn.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-240">The keys of the dictionary are used as the form field names.</span></span> <span data-ttu-id="c8c9e-241">Som standard konverteras formulär värden till sträng värden.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-241">By default, form values are converted to string values.</span></span>

<span data-ttu-id="c8c9e-242">Om värdet är ett **system. io. fileinfo** -objekt, skickas filen med binärfilen.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-242">If the value is a **System.IO.FileInfo** object, then the binary file contents are submitted.</span></span> <span data-ttu-id="c8c9e-243">Namnet på filen skickas in som **filename** -egenskapen.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-243">The name of the file is submitted as the **filename** property.</span></span> <span data-ttu-id="c8c9e-244">MIME-typen anges som `application/octet-stream` .</span><span class="sxs-lookup"><span data-stu-id="c8c9e-244">The MIME type is set as `application/octet-stream`.</span></span> <span data-ttu-id="c8c9e-245">`Get-Item` kan användas för att förenkla tillhandahålla **system. io. fileinfo** -objektet.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-245">`Get-Item` can be used to simplify supplying the **System.IO.FileInfo** object.</span></span>

```powershell
$Form = @{
    resume = Get-Item 'c:\Users\jdoe\Documents\John Doe.pdf'
}
```

<span data-ttu-id="c8c9e-246">Om värdet är en samlings typ, sådana matriser eller listor skickas fältet for flera gånger.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-246">If the value is a collection type, such Arrays or Lists, the for field are submitted multiple times.</span></span>
<span data-ttu-id="c8c9e-247">Värdena i listan behandlas som strängar som standard.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-247">The values of the list are treated as strings by default.</span></span> <span data-ttu-id="c8c9e-248">Om värdet är ett **system. io. fileinfo** -objekt, skickas filen med binärfilen.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-248">If the value is a **System.IO.FileInfo** object, then the binary file contents are submitted.</span></span> <span data-ttu-id="c8c9e-249">Kapslade samlingar stöds inte.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-249">Nested collections aren't supported.</span></span>

```powershell
$Form = @{
    tags     = 'Vacation', 'Italy', '2017'
    pictures = Get-ChildItem 'c:\Users\jdoe\Pictures\2017-Italy\'
}
```

<span data-ttu-id="c8c9e-250">I exemplet ovan `tags` anges fältet tre gånger i formuläret, en gång för var och en av `Vacation` , `Italy` och `2017` .</span><span class="sxs-lookup"><span data-stu-id="c8c9e-250">In the above example the `tags` field are supplied three times in the form, once for each of `Vacation`, `Italy`, and `2017`.</span></span> <span data-ttu-id="c8c9e-251">`pictures`Fältet skickas också en gång för varje fil i `2017-Italy` mappen.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-251">The `pictures` field is also submitted once for each file in the `2017-Italy` folder.</span></span> <span data-ttu-id="c8c9e-252">Det binära innehållet i filerna i mappen skickas som värden.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-252">The binary contents of the files in that folder are submitted as the values.</span></span>

<span data-ttu-id="c8c9e-253">Den här funktionen har lagts till i PowerShell-6.1.0.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-253">This feature was added in PowerShell 6.1.0.</span></span>

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

### <span data-ttu-id="c8c9e-254">– Sidhuvud</span><span class="sxs-lookup"><span data-stu-id="c8c9e-254">-Headers</span></span>

<span data-ttu-id="c8c9e-255">Anger webb begärans rubriker.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-255">Specifies the headers of the web request.</span></span> <span data-ttu-id="c8c9e-256">Ange en hash-tabell eller-ord lista.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-256">Enter a hash table or dictionary.</span></span>

<span data-ttu-id="c8c9e-257">Om du vill ange UserAgent-rubriker använder du parametern **useragent** .</span><span class="sxs-lookup"><span data-stu-id="c8c9e-257">To set UserAgent headers, use the **UserAgent** parameter.</span></span> <span data-ttu-id="c8c9e-258">Du kan inte använda den här parametern för att ange **användar agent** eller cookie-rubriker.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-258">You can't use this parameter to specify **User-Agent** or cookie headers.</span></span>

<span data-ttu-id="c8c9e-259">Content-relaterade rubriker, som `Content-Type` åsidosätts när ett **MultipartFormDataContent** -objekt anges för **brödtext**.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-259">Content related headers, such as `Content-Type` is overridden when a **MultipartFormDataContent** object is supplied for **Body**.</span></span>

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

### <span data-ttu-id="c8c9e-260">-INFILE</span><span class="sxs-lookup"><span data-stu-id="c8c9e-260">-InFile</span></span>

<span data-ttu-id="c8c9e-261">Hämtar innehållet i webb förfrågan från en fil.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-261">Gets the content of the web request from a file.</span></span> <span data-ttu-id="c8c9e-262">Ange en sökväg och ett fil namn.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-262">Enter a path and file name.</span></span> <span data-ttu-id="c8c9e-263">Om du utelämnar sökvägen är standardvärdet den aktuella platsen.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-263">If you omit the path, the default is the current location.</span></span>

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

### <span data-ttu-id="c8c9e-264">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="c8c9e-264">-MaximumRedirection</span></span>

<span data-ttu-id="c8c9e-265">Anger hur många gånger PowerShell omdirigerar en anslutning till en alternativ Uniform Resource Identifier (URI) innan anslutningen Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-265">Specifies how many times PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="c8c9e-266">Standardvärdet är 5.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-266">The default value is 5.</span></span> <span data-ttu-id="c8c9e-267">Värdet 0 (noll) förhindrar all omdirigering.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-267">A value of 0 (zero) prevents all redirection.</span></span>

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

### <span data-ttu-id="c8c9e-268">-MaximumRetryCount</span><span class="sxs-lookup"><span data-stu-id="c8c9e-268">-MaximumRetryCount</span></span>

<span data-ttu-id="c8c9e-269">Anger hur många gånger PowerShell försöker upprätta en anslutning när en felkod mellan 400 och 599, inklusive eller 304, tas emot.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-269">Specifies how many times PowerShell retries a connection when a failure code between 400 and 599, inclusive or 304 is received.</span></span> <span data-ttu-id="c8c9e-270">Se även **RetryIntervalSec** -parametern för att ange antal återförsök.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-270">Also see **RetryIntervalSec** parameter for specifying number of retries.</span></span>

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

### <span data-ttu-id="c8c9e-271">-Metod</span><span class="sxs-lookup"><span data-stu-id="c8c9e-271">-Method</span></span>

<span data-ttu-id="c8c9e-272">Anger den metod som används för webb förfrågan.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-272">Specifies the method used for the web request.</span></span> <span data-ttu-id="c8c9e-273">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="c8c9e-273">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="c8c9e-274">Default</span><span class="sxs-lookup"><span data-stu-id="c8c9e-274">Default</span></span>
- <span data-ttu-id="c8c9e-275">Ta bort</span><span class="sxs-lookup"><span data-stu-id="c8c9e-275">Delete</span></span>
- <span data-ttu-id="c8c9e-276">Hämta</span><span class="sxs-lookup"><span data-stu-id="c8c9e-276">Get</span></span>
- <span data-ttu-id="c8c9e-277">Head</span><span class="sxs-lookup"><span data-stu-id="c8c9e-277">Head</span></span>
- <span data-ttu-id="c8c9e-278">Sammanfoga</span><span class="sxs-lookup"><span data-stu-id="c8c9e-278">Merge</span></span>
- <span data-ttu-id="c8c9e-279">Alternativ</span><span class="sxs-lookup"><span data-stu-id="c8c9e-279">Options</span></span>
- <span data-ttu-id="c8c9e-280">Patch</span><span class="sxs-lookup"><span data-stu-id="c8c9e-280">Patch</span></span>
- <span data-ttu-id="c8c9e-281">Skicka</span><span class="sxs-lookup"><span data-stu-id="c8c9e-281">Post</span></span>
- <span data-ttu-id="c8c9e-282">Placera</span><span class="sxs-lookup"><span data-stu-id="c8c9e-282">Put</span></span>
- <span data-ttu-id="c8c9e-283">Spårning</span><span class="sxs-lookup"><span data-stu-id="c8c9e-283">Trace</span></span>

<span data-ttu-id="c8c9e-284">**CustomMethod** -parametern kan användas för förfrågnings metoder som inte anges ovan.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-284">The **CustomMethod** parameter can be used for Request Methods not listed above.</span></span>

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

### <span data-ttu-id="c8c9e-285">-Noproxy</span><span class="sxs-lookup"><span data-stu-id="c8c9e-285">-NoProxy</span></span>

<span data-ttu-id="c8c9e-286">Anger att cmdleten inte ska använda en proxy för att komma till målet.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-286">Indicates that the cmdlet shouldn't use a proxy to reach the destination.</span></span> <span data-ttu-id="c8c9e-287">Använd den här växeln när du behöver kringgå proxyn som kon figurer ATS i miljön.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-287">When you need to bypass the proxy configured in the environment, use this switch.</span></span> <span data-ttu-id="c8c9e-288">Den här funktionen har lagts till i PowerShell-6.0.0.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-288">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="c8c9e-289">-Fil</span><span class="sxs-lookup"><span data-stu-id="c8c9e-289">-OutFile</span></span>

<span data-ttu-id="c8c9e-290">Anger den utdatafil som denna cmdlet sparar svars texten för.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-290">Specifies the output file for which this cmdlet saves the response body.</span></span> <span data-ttu-id="c8c9e-291">Ange en sökväg och ett fil namn.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-291">Enter a path and file name.</span></span>
<span data-ttu-id="c8c9e-292">Om du utelämnar sökvägen är standardvärdet den aktuella platsen.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-292">If you omit the path, the default is the current location.</span></span>

<span data-ttu-id="c8c9e-293">Som standard `Invoke-WebRequest` returnerar resultatet till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-293">By default, `Invoke-WebRequest` returns the results to the pipeline.</span></span> <span data-ttu-id="c8c9e-294">Om du vill skicka resultatet till en fil och till pipelinen använder du parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="c8c9e-294">To send the results to a file and to the pipeline, use the **Passthru** parameter.</span></span>

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

### <span data-ttu-id="c8c9e-295">– PassThru</span><span class="sxs-lookup"><span data-stu-id="c8c9e-295">-PassThru</span></span>

<span data-ttu-id="c8c9e-296">Anger att cmdleten returnerar resultatet, förutom att skriva dem till en fil.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-296">Indicates that the cmdlet returns the results, in addition to writing them to a file.</span></span> <span data-ttu-id="c8c9e-297">Den här parametern är endast giltig om **parametern out** också används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-297">This parameter is valid only when the **OutFile** parameter is also used in the command.</span></span>

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

### <span data-ttu-id="c8c9e-298">-PreserveAuthorizationOnRedirect</span><span class="sxs-lookup"><span data-stu-id="c8c9e-298">-PreserveAuthorizationOnRedirect</span></span>

<span data-ttu-id="c8c9e-299">Anger att cmdleten ska bevara `Authorization` sidhuvudet, om det finns, över omdirigeringar.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-299">Indicates the cmdlet should preserve the `Authorization` header, when present, across redirections.</span></span>

<span data-ttu-id="c8c9e-300">Som standard tar cmdleten bort `Authorization` sidhuvudet före omdirigeringen.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-300">By default, the cmdlet strips the `Authorization` header before redirecting.</span></span> <span data-ttu-id="c8c9e-301">Om du anger den här parametern inaktive ras den här logiken för fall där huvudet måste skickas till omdirigerings platsen.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-301">Specifying this parameter disables this logic for cases where the header needs to be sent to the redirection location.</span></span>

<span data-ttu-id="c8c9e-302">Den här funktionen har lagts till i PowerShell-6.0.0.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-302">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="c8c9e-303">-Proxy</span><span class="sxs-lookup"><span data-stu-id="c8c9e-303">-Proxy</span></span>

<span data-ttu-id="c8c9e-304">Anger en proxyserver för begäran, i stället för att ansluta direkt till Internet resursen.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-304">Specifies a proxy server for the request, rather than connecting directly to the internet resource.</span></span>
<span data-ttu-id="c8c9e-305">Ange URI för en proxyserver för nätverket.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-305">Enter the URI of a network proxy server.</span></span>

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

### <span data-ttu-id="c8c9e-306">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="c8c9e-306">-ProxyCredential</span></span>

<span data-ttu-id="c8c9e-307">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="c8c9e-307">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span> <span data-ttu-id="c8c9e-308">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-308">The default is the current user.</span></span>

<span data-ttu-id="c8c9e-309">Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , **User@Domain.Com** eller ange ett `PSCredential` objekt, till exempel en som genereras av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-309">Type a user name, such as **User01** or **Domain01\User01** , **User@Domain.Com** , or enter a `PSCredential` object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="c8c9e-310">Den här parametern är endast giltig när parametern **proxy** också används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-310">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="c8c9e-311">Du kan inte använda parametrarna **ProxyCredential** och **ProxyUseDefaultCredentials** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-311">You can't use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="c8c9e-312">-ProxyUseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="c8c9e-312">-ProxyUseDefaultCredentials</span></span>

<span data-ttu-id="c8c9e-313">Anger att cmdleten använder autentiseringsuppgifterna för den aktuella användaren för att få åtkomst till proxyservern som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="c8c9e-313">Indicates that the cmdlet uses the credentials of the current user to access the proxy server that is specified by the **Proxy** parameter.</span></span>

<span data-ttu-id="c8c9e-314">Den här parametern är endast giltig när parametern **proxy** också används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-314">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="c8c9e-315">Du kan inte använda parametrarna **ProxyCredential** och **ProxyUseDefaultCredentials** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-315">You can't use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="c8c9e-316">-Återuppta</span><span class="sxs-lookup"><span data-stu-id="c8c9e-316">-Resume</span></span>

<span data-ttu-id="c8c9e-317">Utför ett bästa försök att återuppta hämtningen av en delvis fil.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-317">Performs a best effort attempt to resume downloading a partial file.</span></span> <span data-ttu-id="c8c9e-318">**Återställningen** kräver en **fil**.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-318">**Resume** requires **OutFile**.</span></span>

<span data-ttu-id="c8c9e-319">**Återuppta** fungerar bara på storleken på den lokala filen och fjärrfilen och utför ingen annan validering av att den lokala filen och fjärrfilen är desamma.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-319">**Resume** only operates on the size of the local file and remote file and performs no other validation that the local file and the remote file are the same.</span></span>

<span data-ttu-id="c8c9e-320">Om den lokala fil storleken är mindre än fjärrfils storleken försöker cmdleten återuppta nedladdningen av filen och lägga till återstående byte i slutet av filen.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-320">If the local file size is smaller than the remote file size, then the cmdlet attempts to resume downloading the file and append the remaining bytes to the end of the file.</span></span>

<span data-ttu-id="c8c9e-321">Om den lokala fil storleken är samma som fjärrfilens storlek, utförs ingen åtgärd och cmdleten förutsätter att nedladdningen redan är slutförd.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-321">If the local file size is the same as the remote file size, then no action is taken and the cmdlet assumes the download already complete.</span></span>

<span data-ttu-id="c8c9e-322">Om den lokala fil storleken är större än fjärrfilens storlek, skrivs den lokala filen över och hela fjärrfilen laddas ned igen.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-322">If the local file size is larger than the remote file size, then the local file is overwritten and the entire remote file is re-downloaded.</span></span> <span data-ttu-id="c8c9e-323">Detta är samma sak som att använda en **fil** utan att **återuppta**.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-323">This behavior is the same as using **OutFile** without **Resume**.</span></span>

<span data-ttu-id="c8c9e-324">Om fjärrservern inte stöder hämtnings återställning, skrivs den lokala filen över och hela fjärrfilen laddas ned igen.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-324">If the remote server does not support download resuming, then the local file is overwritten and the entire remote file is re-downloaded.</span></span> <span data-ttu-id="c8c9e-325">Detta är samma sak som att använda en **fil** utan att **återuppta**.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-325">This behavior is the same as using **OutFile** without **Resume**.</span></span>

<span data-ttu-id="c8c9e-326">Om den lokala filen inte finns skapas den lokala filen och hela fjärrfilen laddas ned.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-326">If the local file does not exist, then the local file is created and the entire remote file is downloaded.</span></span> <span data-ttu-id="c8c9e-327">Detta är samma sak som att använda en **fil** utan att **återuppta**.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-327">This behavior is the same as using **OutFile** without **Resume**.</span></span>

<span data-ttu-id="c8c9e-328">Den här funktionen har lagts till i PowerShell-6.1.0.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-328">This feature was added in PowerShell 6.1.0.</span></span>

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

### <span data-ttu-id="c8c9e-329">-RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="c8c9e-329">-RetryIntervalSec</span></span>

<span data-ttu-id="c8c9e-330">Anger intervallet mellan återförsök för anslutningen när en felkod mellan 400 och 599, inklusive eller 304 tas emot.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-330">Specifies the interval between retries for the connection when a failure code between 400 and 599, inclusive or 304 is received.</span></span> <span data-ttu-id="c8c9e-331">Se även **MaximumRetryCount** -parametern för att ange antal återförsök.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-331">Also see **MaximumRetryCount** parameter for specifying number of retries.</span></span>

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

### <span data-ttu-id="c8c9e-332">-SessionVariable</span><span class="sxs-lookup"><span data-stu-id="c8c9e-332">-SessionVariable</span></span>

<span data-ttu-id="c8c9e-333">Anger en variabel för vilken denna cmdlet skapar en Webbbegäran-session och sparar den i värdet.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-333">Specifies a variable for which this cmdlet creates a web request session and saves it in the value.</span></span>
<span data-ttu-id="c8c9e-334">Ange ett variabel namn utan dollar tecknet ( `$` )-symbolen.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-334">Enter a variable name without the dollar sign (`$`) symbol.</span></span>

<span data-ttu-id="c8c9e-335">När du anger en sessionsvariabel `Invoke-WebRequest` skapar ett sessionsobjekt för Webbbegäran och tilldelar det till en variabel med det angivna namnet i PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-335">When you specify a session variable, `Invoke-WebRequest` creates a web request session object and assigns it to a variable with the specified name in your PowerShell session.</span></span> <span data-ttu-id="c8c9e-336">Du kan använda variabeln i din session så snart kommandot har slutförts.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-336">You can use the variable in your session as soon as the command completes.</span></span>

<span data-ttu-id="c8c9e-337">Till skillnad från en fjärran sluten session är inte Webbbegäran-sessionen en permanent anslutning.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-337">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="c8c9e-338">Det är ett objekt som innehåller information om anslutningen och begäran, inklusive cookies, autentiseringsuppgifter, det maximala värdet för omdirigering och användar agent strängen.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-338">It's an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="c8c9e-339">Du kan använda den för att dela tillstånd och data mellan webb förfrågningar.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-339">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="c8c9e-340">Om du vill använda Webbbegäran-sessionen i efterföljande webb förfrågningar, anger du variabeln session i värdet för **websession** -parametern.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-340">To use the web request session in subsequent web requests, specify the session variable in the value of the **WebSession** parameter.</span></span> <span data-ttu-id="c8c9e-341">PowerShell använder data i objektet Webbbegäran-session när den nya anslutningen upprättas.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-341">PowerShell uses the data in the web request session object when establishing the new connection.</span></span> <span data-ttu-id="c8c9e-342">Om du vill åsidosätta ett värde i Webbbegäran-sessionen använder du en cmdlet-parameter, till exempel **useragent** eller **Credential**.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-342">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential**.</span></span> <span data-ttu-id="c8c9e-343">Parameter värden har företräde framför värden i Webbbegäran-sessionen.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-343">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="c8c9e-344">Du kan inte använda parametrarna **SessionVariable** och **websession** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-344">You can't use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="c8c9e-345">-SkipCertificateCheck</span><span class="sxs-lookup"><span data-stu-id="c8c9e-345">-SkipCertificateCheck</span></span>

<span data-ttu-id="c8c9e-346">Hoppar över certifikat verifierings kontroller.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-346">Skips certificate validation checks.</span></span> <span data-ttu-id="c8c9e-347">Detta omfattar alla verifieringar som förfallo datum, åter kallelse, betrodd rot utfärdare osv.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-347">This includes all validations such as expiration, revocation, trusted root authority, etc.</span></span>

> [!WARNING]
> <span data-ttu-id="c8c9e-348">Att använda den här parametern är inte säkert och rekommenderas inte.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-348">Using this parameter is not secure and is not recommended.</span></span> <span data-ttu-id="c8c9e-349">Den här växeln är endast avsedd att användas mot kända värdar med hjälp av ett självsignerat certifikat i testnings syfte.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-349">This switch is only intended to be used against known hosts using a self-signed certificate for testing purposes.</span></span> <span data-ttu-id="c8c9e-350">Använd på egen risk.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-350">Use at your own risk.</span></span>

<span data-ttu-id="c8c9e-351">Den här funktionen har lagts till i PowerShell-6.0.0.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-351">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="c8c9e-352">-SkipHeaderValidation</span><span class="sxs-lookup"><span data-stu-id="c8c9e-352">-SkipHeaderValidation</span></span>

<span data-ttu-id="c8c9e-353">Anger att cmdleten ska lägga till huvuden i begäran utan verifiering.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-353">Indicates the cmdlet should add headers to the request without validation.</span></span>

<span data-ttu-id="c8c9e-354">Den här växeln bör användas för platser som kräver rubrik värden som inte uppfyller standarder.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-354">This switch should be used for sites that require header values that do not conform to standards.</span></span>
<span data-ttu-id="c8c9e-355">Om du anger den här växeln inaktive ras verifieringen så att värdet inte kan skickas avmarkerat.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-355">Specifying this switch disables validation to allow the value to be passed unchecked.</span></span> <span data-ttu-id="c8c9e-356">När det här värdet anges läggs alla rubriker till utan verifiering.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-356">When specified, all headers are added without validation.</span></span>

<span data-ttu-id="c8c9e-357">Den här växeln inaktiverar verifiering av värden som skickas till parametrarna **ContentType** , **headers** och **useragent** .</span><span class="sxs-lookup"><span data-stu-id="c8c9e-357">This switch disables validation for values passed to the **ContentType** , **Headers** and **UserAgent** parameters.</span></span>

<span data-ttu-id="c8c9e-358">Den här funktionen har lagts till i PowerShell-6.0.0.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-358">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="c8c9e-359">-SslProtocol</span><span class="sxs-lookup"><span data-stu-id="c8c9e-359">-SslProtocol</span></span>

<span data-ttu-id="c8c9e-360">Anger de SSL/TLS-protokoll som är tillåtna för webbegäran.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-360">Sets the SSL/TLS protocols that are permissible for the web request.</span></span> <span data-ttu-id="c8c9e-361">Som standard är alla SSL/TLS-protokoll som stöds av systemet tillåtna.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-361">By default all, SSL/TLS protocols supported by the system are allowed.</span></span> <span data-ttu-id="c8c9e-362">**SslProtocol** gör det möjligt att begränsa till vissa protokoll för efterlevnad.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-362">**SslProtocol** allows for limiting to specific protocols for compliance purposes.</span></span>

<span data-ttu-id="c8c9e-363">**SslProtocol** använder **WebSslProtocol** -flaggan Enum.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-363">**SslProtocol** uses the **WebSslProtocol** Flag Enum.</span></span> <span data-ttu-id="c8c9e-364">Det går att ange mer än ett protokoll med hjälp av flagg notation eller kombinera flera **WebSslProtocol** -alternativ med **bor** , men det finns inte stöd för att tillhandahålla flera protokoll på alla plattformar.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-364">It is possible to supply more than one protocol using flag notation or combining multiple **WebSslProtocol** options with **bor** , however supplying multiple protocols is not supported on all platforms.</span></span>

> [!NOTE]
> <span data-ttu-id="c8c9e-365">På andra plattformar än Windows-plattformar kanske det inte går att ange `'Tls, Tls12'` som ett alternativ.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-365">On non-Windows platforms it may not be possible to supply `'Tls, Tls12'` as an option.</span></span>

<span data-ttu-id="c8c9e-366">Den här funktionen har lagts till i PowerShell-6.0.0.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-366">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="c8c9e-367">-TimeoutSec</span><span class="sxs-lookup"><span data-stu-id="c8c9e-367">-TimeoutSec</span></span>

<span data-ttu-id="c8c9e-368">Anger hur lång tid det tar att vänta på begäran innan den går ut. Ange ett värde i sekunder.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-368">Specifies how long the request can be pending before it times out. Enter a value in seconds.</span></span> <span data-ttu-id="c8c9e-369">Standardvärdet 0 anger en obestämd tids gräns.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-369">The default value, 0, specifies an indefinite time-out.</span></span>

<span data-ttu-id="c8c9e-370">En Domain Name System-fråga (DNS) kan ta upp till 15 sekunder att returnera eller ta slut för lång tid. Om din begäran innehåller ett värdnamn som kräver lösning och du anger **TimeoutSec** till ett värde som är större än noll, men mindre än 15 sekunder, kan det ta 15 sekunder eller mer innan en WebException utlöses, och tids gränsen för din begäran görs.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-370">A Domain Name System (DNS) query can take up to 15 seconds to return or time out. If your request contains a host name that requires resolution, and you set **TimeoutSec** to a value greater than zero, but less than 15 seconds, it can take 15 seconds or more before a WebException is thrown, and your request times out.</span></span>

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

### <span data-ttu-id="c8c9e-371">-Token</span><span class="sxs-lookup"><span data-stu-id="c8c9e-371">-Token</span></span>

<span data-ttu-id="c8c9e-372">OAuth-eller Bearer-token som ska ingå i begäran.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-372">The OAuth or Bearer token to include in the request.</span></span> <span data-ttu-id="c8c9e-373">**Token** krävs av vissa **autentiseringsalternativ** .</span><span class="sxs-lookup"><span data-stu-id="c8c9e-373">**Token** is required by certain **Authentication** options.</span></span> <span data-ttu-id="c8c9e-374">Den kan inte användas separat.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-374">It cannot be used independently.</span></span>

<span data-ttu-id="c8c9e-375">**Token** tar en `SecureString` med token.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-375">**Token** takes a `SecureString` containing the token.</span></span> <span data-ttu-id="c8c9e-376">Använd följande för att ange token manuellt:</span><span class="sxs-lookup"><span data-stu-id="c8c9e-376">To supply the token manually use the following:</span></span>

`Invoke-WebRequest -Uri $uri -Authentication OAuth -Token (Read-Host -AsSecureString)`

<span data-ttu-id="c8c9e-377">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-377">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="c8c9e-378">-TransferEncoding</span><span class="sxs-lookup"><span data-stu-id="c8c9e-378">-TransferEncoding</span></span>

<span data-ttu-id="c8c9e-379">Anger ett värde för HTTP-svarshuvuden för överförings kodning.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-379">Specifies a value for the transfer-encoding HTTP response header.</span></span> <span data-ttu-id="c8c9e-380">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="c8c9e-380">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="c8c9e-381">Segment vis</span><span class="sxs-lookup"><span data-stu-id="c8c9e-381">Chunked</span></span>
- <span data-ttu-id="c8c9e-382">Compress</span><span class="sxs-lookup"><span data-stu-id="c8c9e-382">Compress</span></span>
- <span data-ttu-id="c8c9e-383">DEFLATE</span><span class="sxs-lookup"><span data-stu-id="c8c9e-383">Deflate</span></span>
- <span data-ttu-id="c8c9e-384">GZip</span><span class="sxs-lookup"><span data-stu-id="c8c9e-384">GZip</span></span>
- <span data-ttu-id="c8c9e-385">Identitet</span><span class="sxs-lookup"><span data-stu-id="c8c9e-385">Identity</span></span>

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

### <span data-ttu-id="c8c9e-386">-URI</span><span class="sxs-lookup"><span data-stu-id="c8c9e-386">-Uri</span></span>

<span data-ttu-id="c8c9e-387">Anger Uniform Resource Identifier (URI) för den Internet resurs som webb förfrågan skickas till.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-387">Specifies the Uniform Resource Identifier (URI) of the internet resource to which the web request is sent.</span></span> <span data-ttu-id="c8c9e-388">Ange en URI.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-388">Enter a URI.</span></span> <span data-ttu-id="c8c9e-389">Den här parametern stöder endast HTTP eller HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-389">This parameter supports HTTP or HTTPS only.</span></span>

<span data-ttu-id="c8c9e-390">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-390">This parameter is required.</span></span> <span data-ttu-id="c8c9e-391">Parameter namnet **URI** är valfritt.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-391">The parameter name **Uri** is optional.</span></span>

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

### <span data-ttu-id="c8c9e-392">-UseBasicParsing</span><span class="sxs-lookup"><span data-stu-id="c8c9e-392">-UseBasicParsing</span></span>

<span data-ttu-id="c8c9e-393">Den här parametern är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-393">This parameter has been deprecated.</span></span> <span data-ttu-id="c8c9e-394">Från och med PowerShell-6.0.0 använder alla webbegäranden enbart grundläggande parsning.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-394">Beginning with PowerShell 6.0.0, all Web requests use basic parsing only.</span></span> <span data-ttu-id="c8c9e-395">Den här parametern ingår endast för bakåtkompatibilitet och all användning av den har ingen påverkan på driften av cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-395">This parameter is included for backwards compatibility only and any use of it has no effect on the operation of the cmdlet.</span></span>

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

### <span data-ttu-id="c8c9e-396">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="c8c9e-396">-UseDefaultCredentials</span></span>

<span data-ttu-id="c8c9e-397">Anger att cmdleten använder autentiseringsuppgifterna för den aktuella användaren för att skicka webb förfrågan.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-397">Indicates that the cmdlet uses the credentials of the current user to send the web request.</span></span> <span data-ttu-id="c8c9e-398">Detta kan inte användas med **autentisering** eller **autentiseringsuppgifter** och stöds inte på alla plattformar.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-398">This can't be used with **Authentication** or **Credential** and may not be supported on all platforms.</span></span>

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

### <span data-ttu-id="c8c9e-399">– UserAgent</span><span class="sxs-lookup"><span data-stu-id="c8c9e-399">-UserAgent</span></span>

<span data-ttu-id="c8c9e-400">Anger en användar agent sträng för webb förfrågan.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-400">Specifies a user agent string for the web request.</span></span>

<span data-ttu-id="c8c9e-401">Standard användar agenten liknar `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` med små variationer för varje operativ system och plattform.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-401">The default user agent is similar to `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` with slight variations for each operating system and platform.</span></span>

<span data-ttu-id="c8c9e-402">Om du vill testa en webbplats med den standard användar agent sträng som används av de flesta webbläsare, använder du egenskaperna för [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) -klassen, till exempel Chrome, Firefox, InternetExplorer, Opera och Safari.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-402">To test a website with the standard user agent string that is used by most internet browsers, use the properties of the [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) class, such as Chrome, FireFox, InternetExplorer, Opera, and Safari.</span></span>

<span data-ttu-id="c8c9e-403">Följande kommando använder till exempel användar agent strängen för Internet Explorer:</span><span class="sxs-lookup"><span data-stu-id="c8c9e-403">For example, the following command uses the user agent string for Internet Explorer:</span></span>

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

### <span data-ttu-id="c8c9e-404">– Websession</span><span class="sxs-lookup"><span data-stu-id="c8c9e-404">-WebSession</span></span>

<span data-ttu-id="c8c9e-405">Anger en Webbbegäran-session.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-405">Specifies a web request session.</span></span> <span data-ttu-id="c8c9e-406">Ange variabel namnet, inklusive dollar tecknet ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="c8c9e-406">Enter the variable name, including the dollar sign (`$`).</span></span>

<span data-ttu-id="c8c9e-407">Om du vill åsidosätta ett värde i Webbbegäran-sessionen använder du en cmdlet-parameter, till exempel **useragent** eller **Credential**.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-407">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential**.</span></span> <span data-ttu-id="c8c9e-408">Parameter värden har företräde framför värden i Webbbegäran-sessionen.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-408">Parameter values take precedence over values in the web request session.</span></span> <span data-ttu-id="c8c9e-409">Content-relaterade rubriker, till exempel `Content-Type` , åsidosätts också när ett **MultipartFormDataContent** -objekt anges för **brödtext**.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-409">Content related headers, such as `Content-Type`, are also be overridden when a **MultipartFormDataContent** object is supplied for **Body**.</span></span>

<span data-ttu-id="c8c9e-410">Till skillnad från en fjärran sluten session är inte Webbbegäran-sessionen en permanent anslutning.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-410">Unlike a remote session, the web request session isn't a persistent connection.</span></span> <span data-ttu-id="c8c9e-411">Det är ett objekt som innehåller information om anslutningen och begäran, inklusive cookies, autentiseringsuppgifter, det maximala värdet för omdirigering och användar agent strängen.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-411">It's an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="c8c9e-412">Du kan använda den för att dela tillstånd och data mellan webb förfrågningar.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-412">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="c8c9e-413">Om du vill skapa en Webbbegäran-session anger du ett variabel namn, utan dollar tecken, i värdet för parametern **SessionVariable** för ett `Invoke-WebRequest` kommando.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-413">To create a web request session, enter a variable name, without a dollar sign, in the value of the **SessionVariable** parameter of an `Invoke-WebRequest` command.</span></span> <span data-ttu-id="c8c9e-414">`Invoke-WebRequest` skapar sessionen och sparar den i variabeln.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-414">`Invoke-WebRequest` creates the session and saves it in the variable.</span></span> <span data-ttu-id="c8c9e-415">I efterföljande kommandon använder du variabeln som värde för **websession** -parametern.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-415">In subsequent commands, use the variable as the value of the **WebSession** parameter.</span></span>

<span data-ttu-id="c8c9e-416">Du kan inte använda parametrarna **SessionVariable** och **websession** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-416">You can't use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="c8c9e-417">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c8c9e-417">CommonParameters</span></span>

<span data-ttu-id="c8c9e-418">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-418">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c8c9e-419">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c8c9e-419">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c8c9e-420">INDATA</span><span class="sxs-lookup"><span data-stu-id="c8c9e-420">INPUTS</span></span>

### <span data-ttu-id="c8c9e-421">System. Object</span><span class="sxs-lookup"><span data-stu-id="c8c9e-421">System.Object</span></span>

<span data-ttu-id="c8c9e-422">Du kan skicka vidare innehållet i en webb förfrågan till `Invoke-WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="c8c9e-422">You can pipe the body of a web request to `Invoke-WebRequest`.</span></span>

## <span data-ttu-id="c8c9e-423">UTDATA</span><span class="sxs-lookup"><span data-stu-id="c8c9e-423">OUTPUTS</span></span>

### <span data-ttu-id="c8c9e-424">Microsoft. PowerShell. commands. BasicHtmlWebResponseObject</span><span class="sxs-lookup"><span data-stu-id="c8c9e-424">Microsoft.PowerShell.Commands.BasicHtmlWebResponseObject</span></span>

## <span data-ttu-id="c8c9e-425">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="c8c9e-425">NOTES</span></span>

<span data-ttu-id="c8c9e-426">Från och med PowerShell 6.0.0 `Invoke-WebRequest` har endast stöd för grundläggande tolkning.</span><span class="sxs-lookup"><span data-stu-id="c8c9e-426">Beginning with PowerShell 6.0.0 `Invoke-WebRequest` supports basic parsing only.</span></span>

<span data-ttu-id="c8c9e-427">Mer information om objekt typen **Microsoft. PowerShell. commands. BasicHtmlWebResponseObject** finns i [BasicHtmlWebResponseObject](/dotnet/api/microsoft.powershell.commands.basichtmlwebresponseobject).</span><span class="sxs-lookup"><span data-stu-id="c8c9e-427">For more information about the **Microsoft.PowerShell.Commands.BasicHtmlWebResponseObject** object type, see [BasicHtmlWebResponseObject](/dotnet/api/microsoft.powershell.commands.basichtmlwebresponseobject).</span></span>

<span data-ttu-id="c8c9e-428">Mer information om hur .NET tillhandahåller Proxy-tjänster till PowerShell finns i [komma åt Internet via en proxyserver](/dotnet/framework/network-programming/accessing-the-internet-through-a-proxy).</span><span class="sxs-lookup"><span data-stu-id="c8c9e-428">For more information about how .NET provides proxy services to PowerShell, see [Accessing the Internet Through a Proxy](/dotnet/framework/network-programming/accessing-the-internet-through-a-proxy).</span></span>

## <span data-ttu-id="c8c9e-429">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="c8c9e-429">RELATED LINKS</span></span>

[<span data-ttu-id="c8c9e-430">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="c8c9e-430">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)

[<span data-ttu-id="c8c9e-431">ConvertFrom – JSON</span><span class="sxs-lookup"><span data-stu-id="c8c9e-431">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="c8c9e-432">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="c8c9e-432">ConvertTo-Json</span></span>](ConvertTo-Json.md)
