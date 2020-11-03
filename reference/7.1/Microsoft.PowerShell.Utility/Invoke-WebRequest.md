---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-webrequest?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-WebRequest
ms.openlocfilehash: bb23f2ed01573a3f67c19f45db495cd86ecefe0c
ms.sourcegitcommit: 69b08b28ee2ef3168065672a23b9b6f0c578c95b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/09/2020
ms.locfileid: "93269438"
---
# <span data-ttu-id="99a99-103">Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="99a99-103">Invoke-WebRequest</span></span>

## <span data-ttu-id="99a99-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="99a99-104">SYNOPSIS</span></span>
<span data-ttu-id="99a99-105">Hämtar innehåll från en webb sida på Internet.</span><span class="sxs-lookup"><span data-stu-id="99a99-105">Gets content from a web page on the internet.</span></span>

## <span data-ttu-id="99a99-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="99a99-106">SYNTAX</span></span>

### <span data-ttu-id="99a99-107">StandardMethod (standard)</span><span class="sxs-lookup"><span data-stu-id="99a99-107">StandardMethod (Default)</span></span>

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

### <span data-ttu-id="99a99-108">StandardMethodNoProxy</span><span class="sxs-lookup"><span data-stu-id="99a99-108">StandardMethodNoProxy</span></span>

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

### <span data-ttu-id="99a99-109">CustomMethod</span><span class="sxs-lookup"><span data-stu-id="99a99-109">CustomMethod</span></span>

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

### <span data-ttu-id="99a99-110">CustomMethodNoProxy</span><span class="sxs-lookup"><span data-stu-id="99a99-110">CustomMethodNoProxy</span></span>

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

## <span data-ttu-id="99a99-111">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="99a99-111">DESCRIPTION</span></span>

<span data-ttu-id="99a99-112">`Invoke-WebRequest`Cmdlet: en skickar HTTP-och HTTPS-begäranden till en webb sida eller en webb tjänst.</span><span class="sxs-lookup"><span data-stu-id="99a99-112">The `Invoke-WebRequest` cmdlet sends HTTP and HTTPS requests to a web page or web service.</span></span> <span data-ttu-id="99a99-113">Den tolkar svaret och returnerar samlingar med länkar, bilder och andra viktiga HTML-element.</span><span class="sxs-lookup"><span data-stu-id="99a99-113">It parses the response and returns collections of links, images, and other significant HTML elements.</span></span>

<span data-ttu-id="99a99-114">Denna cmdlet introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="99a99-114">This cmdlet was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="99a99-115">Från och med PowerShell 7,0 `Invoke-WebRequest` stöder proxykonfigurationen som definieras av miljövariabler.</span><span class="sxs-lookup"><span data-stu-id="99a99-115">Beginning in PowerShell 7.0, `Invoke-WebRequest` supports proxy configuration defined by environment variables.</span></span> <span data-ttu-id="99a99-116">Se avsnittet [anteckningar](#notes) i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="99a99-116">See the [Notes](#notes) section of this article.</span></span>

## <span data-ttu-id="99a99-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="99a99-117">EXAMPLES</span></span>

### <span data-ttu-id="99a99-118">Exempel 1: skicka en webb förfrågan</span><span class="sxs-lookup"><span data-stu-id="99a99-118">Example 1: Send a web request</span></span>

<span data-ttu-id="99a99-119">I det här exemplet används `Invoke-WebRequest` cmdleten för att skicka en webbegäran till Bing.com-webbplatsen.</span><span class="sxs-lookup"><span data-stu-id="99a99-119">This example uses the `Invoke-WebRequest` cmdlet to send a web request to the Bing.com site.</span></span>

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

<span data-ttu-id="99a99-120">Det första kommandot utfärdar begäran och sparar svaret i `$Response` variabeln.</span><span class="sxs-lookup"><span data-stu-id="99a99-120">The first command issues the request and saves the response in the `$Response` variable.</span></span>

<span data-ttu-id="99a99-121">Det andra kommandot hämtar alla **InputField** där **namn** -egenskapen är som `"* Value"` .</span><span class="sxs-lookup"><span data-stu-id="99a99-121">The second command gets any **InputField** where the **Name** property is like `"* Value"`.</span></span> <span data-ttu-id="99a99-122">De filtrerade resultaten är skickas för `Select-Object` att välja egenskaper för **namn** och **värde** .</span><span class="sxs-lookup"><span data-stu-id="99a99-122">The filtered results are piped to `Select-Object` to select the **Name** and **Value** properties.</span></span>

### <span data-ttu-id="99a99-123">Exempel 2: använda en tillstånds känslig webb tjänst</span><span class="sxs-lookup"><span data-stu-id="99a99-123">Example 2: Use a stateful web service</span></span>

<span data-ttu-id="99a99-124">Det här exemplet visar hur du använder `Invoke-WebRequest` cmdleten med en tillstånds känslig webb tjänst.</span><span class="sxs-lookup"><span data-stu-id="99a99-124">This example shows how to use the `Invoke-WebRequest` cmdlet with a stateful web service.</span></span>

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

<span data-ttu-id="99a99-125">Det första anropet för att `Invoke-WebRequest` skicka en inloggnings förfrågan.</span><span class="sxs-lookup"><span data-stu-id="99a99-125">The first call to `Invoke-WebRequest` sends a sign-in request.</span></span> <span data-ttu-id="99a99-126">Kommandot anger värdet "session" för värdet för parametern **-SessionVariable** och sparar resultatet i `$LoginResponse` variabeln.</span><span class="sxs-lookup"><span data-stu-id="99a99-126">The command specifies a value of "Session" for the value of the **-SessionVariable** parameter, and saves the result in the `$LoginResponse` variable.</span></span> <span data-ttu-id="99a99-127">När kommandot har slutförts `$LoginResponse` innehåller variabeln en `BasicHtmlWebResponseObject` och `$Session` variabeln innehåller ett `WebRequestSession` objekt.</span><span class="sxs-lookup"><span data-stu-id="99a99-127">When the command completes, the `$LoginResponse` variable contains an `BasicHtmlWebResponseObject` and the `$Session` variable contains a `WebRequestSession` object.</span></span> <span data-ttu-id="99a99-128">Detta loggar användaren på platsen.</span><span class="sxs-lookup"><span data-stu-id="99a99-128">This logs the user into the site.</span></span>

<span data-ttu-id="99a99-129">Anropet till `$Session` själva visar `WebRequestSession` objektet i variabeln.</span><span class="sxs-lookup"><span data-stu-id="99a99-129">The call to `$Session` by itself shows the `WebRequestSession` object in the variable.</span></span>

<span data-ttu-id="99a99-130">Det andra anropet för att `Invoke-WebRequest` Hämta användarens profil som kräver att användaren är inloggad på platsen.</span><span class="sxs-lookup"><span data-stu-id="99a99-130">The second call to `Invoke-WebRequest` fetches the user's profile which requires that the user be logged into the site.</span></span> <span data-ttu-id="99a99-131">De sessionsdata som lagras i `$Session` variabeln används för att tillhandahålla sessionscookies till den plats som skapas under inloggningen.</span><span class="sxs-lookup"><span data-stu-id="99a99-131">The session data stored in the `$Session` variable is used to provide session cookies to the site created during the login.</span></span> <span data-ttu-id="99a99-132">Resultatet sparas i `$ProfileResponse` variabeln.</span><span class="sxs-lookup"><span data-stu-id="99a99-132">The result is saved in the `$ProfileResponse` variable.</span></span>

<span data-ttu-id="99a99-133">Anropet till `$ProfileResponse` själva visar `BasicHtmlWebResponseObject` i variabeln.</span><span class="sxs-lookup"><span data-stu-id="99a99-133">The call to `$ProfileResponse` by itself shows the `BasicHtmlWebResponseObject` in the variable.</span></span>

### <span data-ttu-id="99a99-134">Exempel 3: Hämta länkar från en webb sida</span><span class="sxs-lookup"><span data-stu-id="99a99-134">Example 3: Get links from a web page</span></span>

<span data-ttu-id="99a99-135">Det här exemplet hämtar länkarna på en webb sida.</span><span class="sxs-lookup"><span data-stu-id="99a99-135">This example gets the links in a web page.</span></span> <span data-ttu-id="99a99-136">Den använder `Invoke-WebRequest` cmdleten för att hämta innehållet på webb sidan.</span><span class="sxs-lookup"><span data-stu-id="99a99-136">It uses the `Invoke-WebRequest` cmdlet to get the web page content.</span></span> <span data-ttu-id="99a99-137">Sedan använder den egenskapen **Links** för den `BasicHtmlWebResponseObject` som `Invoke-WebRequest` returnerar och egenskapen **href** för varje länk.</span><span class="sxs-lookup"><span data-stu-id="99a99-137">Then it uses the **Links** property of the `BasicHtmlWebResponseObject` that `Invoke-WebRequest` returns, and the **Href** property of each link.</span></span>

```powershell
(Invoke-WebRequest -Uri "https://aka.ms/pscore6-docs").Links.Href
```

### <span data-ttu-id="99a99-138">Exempel 4: skriver svars innehållet till en fil med hjälp av den kodning som definierats på den begärda sidan.</span><span class="sxs-lookup"><span data-stu-id="99a99-138">Example 4: Writes the response content to a file using the encoding defined in the requested page.</span></span>

<span data-ttu-id="99a99-139">I det här exemplet används `Invoke-WebRequest` cmdleten för att hämta webb sidans innehåll på en PowerShell-dokumentations sida.</span><span class="sxs-lookup"><span data-stu-id="99a99-139">This example uses the `Invoke-WebRequest` cmdlet to retrieve the web page content of a PowerShell documentation page.</span></span>

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

<span data-ttu-id="99a99-140">Det första kommandot hämtar sidan och sparar objektet Response i `$Response` variabeln.</span><span class="sxs-lookup"><span data-stu-id="99a99-140">The first command retrieves the page and saves the response object in the `$Response` variable.</span></span>

<span data-ttu-id="99a99-141">Det andra kommandot skapar en `StreamWriter` som ska användas för att skriva svars innehållet till en fil.</span><span class="sxs-lookup"><span data-stu-id="99a99-141">The second command creates a `StreamWriter` to use to write the response content to a file.</span></span> <span data-ttu-id="99a99-142">Egenskapen **encoding** för Response-objektet används för att ange filens kodning.</span><span class="sxs-lookup"><span data-stu-id="99a99-142">The **Encoding** property of the response object is used to set the encoding for the file.</span></span>

<span data-ttu-id="99a99-143">De slutliga kommandona skriver **innehålls** egenskapen till filen och tar sedan bort `StreamWriter` .</span><span class="sxs-lookup"><span data-stu-id="99a99-143">The final few commands write the **Content** property to the file then disposes the `StreamWriter`.</span></span>

<span data-ttu-id="99a99-144">Observera att **encoding** -egenskapen är null om Webbbegäran inte returnerar text innehåll.</span><span class="sxs-lookup"><span data-stu-id="99a99-144">Note that the **Encoding** property is null if the web request doesn't return text content.</span></span>

### <span data-ttu-id="99a99-145">Exempel 5: skicka en multipart-/formulär data fil</span><span class="sxs-lookup"><span data-stu-id="99a99-145">Example 5: Submit a multipart/form-data file</span></span>

<span data-ttu-id="99a99-146">I det här exemplet används `Invoke-WebRequest` cmdleten Ladda upp en fil som ett `multipart/form-data` överförings objekt.</span><span class="sxs-lookup"><span data-stu-id="99a99-146">This example uses the `Invoke-WebRequest` cmdlet upload a file as a `multipart/form-data` submission.</span></span> <span data-ttu-id="99a99-147">Filen `c:\document.txt` skickas som ett formulär fält `document` med `Content-Type` för `text/plain` .</span><span class="sxs-lookup"><span data-stu-id="99a99-147">The file `c:\document.txt` is submitted as the form field `document` with the `Content-Type` of `text/plain`.</span></span>

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

### <span data-ttu-id="99a99-148">Exempel 6: överföring av förenklad multipart/form – data</span><span class="sxs-lookup"><span data-stu-id="99a99-148">Example 6: Simplified Multipart/Form-Data Submission</span></span>

<span data-ttu-id="99a99-149">Vissa API: er kräver att det går `multipart/form-data` att överföra filer och blandat innehåll.</span><span class="sxs-lookup"><span data-stu-id="99a99-149">Some APIs require `multipart/form-data` submissions to upload files and mixed content.</span></span> <span data-ttu-id="99a99-150">I det här exemplet visas hur du uppdaterar en användar profil.</span><span class="sxs-lookup"><span data-stu-id="99a99-150">This example demonstrates updating a user profile.</span></span>

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

<span data-ttu-id="99a99-151">Profil formuläret kräver följande fält:,,,, `firstName` `lastName` `email` `avatar` `birthday` och `hobbies` .</span><span class="sxs-lookup"><span data-stu-id="99a99-151">The profile form requires these fields: `firstName`, `lastName`, `email`, `avatar`, `birthday`, and `hobbies`.</span></span> <span data-ttu-id="99a99-152">API: et förväntar sig en bild för användar profils pic som ska anges i `avatar` fältet.</span><span class="sxs-lookup"><span data-stu-id="99a99-152">The API is expecting an image for the user profile pic to be supplied in the `avatar` field.</span></span> <span data-ttu-id="99a99-153">API: et accepterar också `hobbies` att flera poster skickas i samma formulär.</span><span class="sxs-lookup"><span data-stu-id="99a99-153">The API also accepts multiple `hobbies` entries to be submitted in the same form.</span></span>

<span data-ttu-id="99a99-154">När du skapar en `$Form` hash-tabellen används nyckel namnen som namn på formulär fält.</span><span class="sxs-lookup"><span data-stu-id="99a99-154">When creating the `$Form` HashTable, the key names are used as form field names.</span></span> <span data-ttu-id="99a99-155">Som standard konverteras värdena för hash-tabellen till strängar.</span><span class="sxs-lookup"><span data-stu-id="99a99-155">By default, the values of the HashTable are converted to strings.</span></span> <span data-ttu-id="99a99-156">Om det finns ett **system. io. fileinfo** -värde skickas filens innehåll.</span><span class="sxs-lookup"><span data-stu-id="99a99-156">If a **System.IO.FileInfo** value is present, the file contents are submitted.</span></span> <span data-ttu-id="99a99-157">Om det finns en samling, till exempel matriser eller listor, skickas formulär fältet flera gånger.</span><span class="sxs-lookup"><span data-stu-id="99a99-157">If a collection such as arrays or lists are present, the form field is submitted multiple times.</span></span>

<span data-ttu-id="99a99-158">Genom `Get-Item` att använda på `avatar` nyckeln `FileInfo` anges objektet som värde.</span><span class="sxs-lookup"><span data-stu-id="99a99-158">By using `Get-Item` on the `avatar` key, the `FileInfo` object is set as the value.</span></span> <span data-ttu-id="99a99-159">Resultatet är att avbildnings data för `jdoe.png` skickas.</span><span class="sxs-lookup"><span data-stu-id="99a99-159">The result is that the image data for `jdoe.png` is submitted.</span></span>

<span data-ttu-id="99a99-160">Om du anger en lista till `hobbies` nyckeln, finns `hobbies` fältet i under sändningarna en gång för varje List objekt.</span><span class="sxs-lookup"><span data-stu-id="99a99-160">By supplying a list to the `hobbies` key, the `hobbies` field is present in the submissions once for each list item.</span></span>

### <span data-ttu-id="99a99-161">Exempel 7: fånga meddelanden som inte lyckades från Invoke-WebRequest</span><span class="sxs-lookup"><span data-stu-id="99a99-161">Example 7: Catch non success messages from Invoke-WebRequest</span></span>

<span data-ttu-id="99a99-162">När `Invoke-WebRequest` påträffar ett HTTP-meddelande som inte lyckades (404, 500 osv.) returnerar det inga utdata och returnerar ett avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="99a99-162">When `Invoke-WebRequest` encounters a non-success HTTP message (404, 500, etc.), it returns no output and throws a terminating error.</span></span> <span data-ttu-id="99a99-163">Om du vill fånga felet och visa **StatusCode** kan du sätta igång i ett `try/catch` block.</span><span class="sxs-lookup"><span data-stu-id="99a99-163">To catch the error and view the **StatusCode** you can enclose execution in a `try/catch` block.</span></span>

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

<span data-ttu-id="99a99-164">Kommandot anropar `Invoke-WebRequest` med en **ErrorAction** av **stopp** , som tvingar fram `Invoke-WebRequest` ett avslutande fel vid eventuella misslyckade förfrågningar.</span><span class="sxs-lookup"><span data-stu-id="99a99-164">The command calls `Invoke-WebRequest` with an **ErrorAction** of **Stop** , which forces `Invoke-WebRequest` to throw a terminating error on any failed requests.</span></span> <span data-ttu-id="99a99-165">Det avslutande felet fångas av `catch` blocket som hämtar **StatusCode** från **Exception** -objektet.</span><span class="sxs-lookup"><span data-stu-id="99a99-165">The terminating error is caught by the `catch` block which retrieves the **StatusCode** from the **Exception** object.</span></span>

## <span data-ttu-id="99a99-166">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="99a99-166">PARAMETERS</span></span>

### <span data-ttu-id="99a99-167">-AllowUnencryptedAuthentication</span><span class="sxs-lookup"><span data-stu-id="99a99-167">-AllowUnencryptedAuthentication</span></span>

<span data-ttu-id="99a99-168">Tillåter sändning av autentiseringsuppgifter och hemligheter över okrypterade anslutningar.</span><span class="sxs-lookup"><span data-stu-id="99a99-168">Allows sending of credentials and secrets over unencrypted connections.</span></span> <span data-ttu-id="99a99-169">Som standard anger **Credential** eller valfritt **autentiseringsalternativ** med en **URI** som inte börjar med `https://` resulterar i ett fel och begäran avbryts för att förhindra oavsiktlig kommunikation av hemligheter i oformaterad text över okrypterade anslutningar.</span><span class="sxs-lookup"><span data-stu-id="99a99-169">By default, supplying **Credential** or any **Authentication** option with a **Uri** that does not begin with `https://` results in an error and the request is aborted to prevent unintentionally communicating secrets in plain text over unencrypted connections.</span></span> <span data-ttu-id="99a99-170">Om du vill åsidosätta det här beteendet på egen risk anger du parametern **AllowUnencryptedAuthentication** .</span><span class="sxs-lookup"><span data-stu-id="99a99-170">To override this behavior at your own risk, supply the **AllowUnencryptedAuthentication** parameter.</span></span>

> [!WARNING]
> <span data-ttu-id="99a99-171">Att använda den här parametern är inte säkert och rekommenderas inte.</span><span class="sxs-lookup"><span data-stu-id="99a99-171">Using this parameter is not secure and is not recommended.</span></span> <span data-ttu-id="99a99-172">Det tillhandahålls endast för kompatibilitet med äldre system som inte kan tillhandahålla krypterade anslutningar.</span><span class="sxs-lookup"><span data-stu-id="99a99-172">It is provided only for compatibility with legacy systems that cannot provide encrypted connections.</span></span> <span data-ttu-id="99a99-173">Använd på egen risk.</span><span class="sxs-lookup"><span data-stu-id="99a99-173">Use at your own risk.</span></span>

<span data-ttu-id="99a99-174">Den här funktionen har lagts till i PowerShell-6.0.0.</span><span class="sxs-lookup"><span data-stu-id="99a99-174">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="99a99-175">-Autentisering</span><span class="sxs-lookup"><span data-stu-id="99a99-175">-Authentication</span></span>

<span data-ttu-id="99a99-176">Anger den explicita autentiseringstypen som ska användas för begäran.</span><span class="sxs-lookup"><span data-stu-id="99a99-176">Specifies the explicit authentication type to use for the request.</span></span> <span data-ttu-id="99a99-177">Standardvärdet är **none**.</span><span class="sxs-lookup"><span data-stu-id="99a99-177">The default is **None**.</span></span>
<span data-ttu-id="99a99-178">Det går inte att använda **autentisering** med **UseDefaultCredentials**.</span><span class="sxs-lookup"><span data-stu-id="99a99-178">**Authentication** cannot be used with **UseDefaultCredentials**.</span></span>

<span data-ttu-id="99a99-179">Tillgängliga autentiserings alternativ:</span><span class="sxs-lookup"><span data-stu-id="99a99-179">Available Authentication Options:</span></span>

- <span data-ttu-id="99a99-180">**Ingen** : det här är standard alternativet när **autentisering** inte anges. ingen explicit autentisering används.</span><span class="sxs-lookup"><span data-stu-id="99a99-180">**None** : This is the default option when **Authentication** isn't supplied; no explicit authentication is used.</span></span>
- <span data-ttu-id="99a99-181">**Basic** : kräver **autentiseringsuppgifter**.</span><span class="sxs-lookup"><span data-stu-id="99a99-181">**Basic** : Requires **Credential**.</span></span> <span data-ttu-id="99a99-182">Autentiseringsuppgifterna skickas i ett RFC 7617 Basic Authentication-huvud i formatet `base64(user:password)` .</span><span class="sxs-lookup"><span data-stu-id="99a99-182">The credentials are sent in an RFC 7617 Basic Authentication header in the format of `base64(user:password)`.</span></span>
- <span data-ttu-id="99a99-183">**Bearer** : kräver **token**.</span><span class="sxs-lookup"><span data-stu-id="99a99-183">**Bearer** : Requires **Token**.</span></span> <span data-ttu-id="99a99-184">Skickar ett RFC 6750- `Authorization: Bearer` huvud med angiven token.</span><span class="sxs-lookup"><span data-stu-id="99a99-184">Sends an RFC 6750 `Authorization: Bearer` header with the supplied token.</span></span> <span data-ttu-id="99a99-185">Detta är ett alias för **OAuth**</span><span class="sxs-lookup"><span data-stu-id="99a99-185">This is an alias for **OAuth**</span></span>
- <span data-ttu-id="99a99-186">**OAuth** : kräver **token**.</span><span class="sxs-lookup"><span data-stu-id="99a99-186">**OAuth** : Requires **Token**.</span></span> <span data-ttu-id="99a99-187">Skickar ett RFC 6750- `Authorization: Bearer` huvud med angiven token.</span><span class="sxs-lookup"><span data-stu-id="99a99-187">Sends an RFC 6750 `Authorization: Bearer` header with the supplied token.</span></span> <span data-ttu-id="99a99-188">Detta är ett alias för **innehavare**</span><span class="sxs-lookup"><span data-stu-id="99a99-188">This is an alias for **Bearer**</span></span>

<span data-ttu-id="99a99-189">Att tillhandahålla **autentisering** åsidosätter alla `Authorization` rubriker som har angetts för **sidhuvuden** eller ingår i **websession**.</span><span class="sxs-lookup"><span data-stu-id="99a99-189">Supplying **Authentication** overrides any `Authorization` headers supplied to **Headers** or included in **WebSession**.</span></span>

<span data-ttu-id="99a99-190">Den här funktionen har lagts till i PowerShell-6.0.0.</span><span class="sxs-lookup"><span data-stu-id="99a99-190">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="99a99-191">-Body</span><span class="sxs-lookup"><span data-stu-id="99a99-191">-Body</span></span>

<span data-ttu-id="99a99-192">Anger bröd texten i begäran.</span><span class="sxs-lookup"><span data-stu-id="99a99-192">Specifies the body of the request.</span></span> <span data-ttu-id="99a99-193">Bröd texten är innehållet i begäran som följer sidhuvuden.</span><span class="sxs-lookup"><span data-stu-id="99a99-193">The body is the content of the request that follows the headers.</span></span>
<span data-ttu-id="99a99-194">Du kan också skicka ett Body-värde till `Invoke-WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="99a99-194">You can also pipe a body value to `Invoke-WebRequest`.</span></span>

<span data-ttu-id="99a99-195">Du kan använda **text** parametern för att ange en lista över frågeparametrar eller ange svarets innehåll.</span><span class="sxs-lookup"><span data-stu-id="99a99-195">The **Body** parameter can be used to specify a list of query parameters or specify the content of the response.</span></span>

<span data-ttu-id="99a99-196">När indatamängden är en GET-begäran och texten är en `IDictionary` (vanligt vis en hash-tabell) läggs bröd texten till i URI: n som frågeparametrar.</span><span class="sxs-lookup"><span data-stu-id="99a99-196">When the input is a GET request and the body is an `IDictionary` (typically, a hash table), the body is added to the URI as query parameters.</span></span> <span data-ttu-id="99a99-197">För andra typer av begär Anden (till exempel POST) anges bröd texten som värde för begär ande texten i `name=value` standardformat.</span><span class="sxs-lookup"><span data-stu-id="99a99-197">For other request types (such as POST), the body is set as the value of the request body in the standard `name=value` format.</span></span>

<span data-ttu-id="99a99-198">**Bröd text** parametern kan också acceptera ett `System.Net.Http.MultipartFormDataContent` objekt.</span><span class="sxs-lookup"><span data-stu-id="99a99-198">The **Body** parameter may also accept a `System.Net.Http.MultipartFormDataContent` object.</span></span> <span data-ttu-id="99a99-199">Detta underlättar `multipart/form-data` förfrågningar.</span><span class="sxs-lookup"><span data-stu-id="99a99-199">This facilitates `multipart/form-data` requests.</span></span> <span data-ttu-id="99a99-200">När ett **MultipartFormDataContent** -objekt anges för **brödtext** , åsidosätts alla innehåll relaterade rubriker som har angetts för egenskaperna **ContentType** , **headers** eller **websession** av **MultipartFormDataContent** -objektets innehålls rubriker.</span><span class="sxs-lookup"><span data-stu-id="99a99-200">When a **MultipartFormDataContent** object is supplied for **Body** , any Content related headers supplied to the **ContentType** , **Headers** , or **WebSession** parameters is overridden by the Content headers of the **MultipartFormDataContent** object.</span></span> <span data-ttu-id="99a99-201">Den här funktionen har lagts till i PowerShell-6.0.0.</span><span class="sxs-lookup"><span data-stu-id="99a99-201">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="99a99-202">– Certifikat</span><span class="sxs-lookup"><span data-stu-id="99a99-202">-Certificate</span></span>

<span data-ttu-id="99a99-203">Anger det klient certifikat som används för en säker webb förfrågan.</span><span class="sxs-lookup"><span data-stu-id="99a99-203">Specifies the client certificate that's used for a secure web request.</span></span> <span data-ttu-id="99a99-204">Ange en variabel som innehåller ett certifikat eller ett kommando eller uttryck som hämtar certifikatet.</span><span class="sxs-lookup"><span data-stu-id="99a99-204">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="99a99-205">Om du vill söka efter ett certifikat använder `Get-PfxCertificate` eller använder du `Get-ChildItem` cmdleten på certifikat `Cert:` enheten ().</span><span class="sxs-lookup"><span data-stu-id="99a99-205">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the Certificate (`Cert:`) drive.</span></span> <span data-ttu-id="99a99-206">Om certifikatet inte är giltigt eller inte har tillräcklig behörighet, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="99a99-206">If the certificate isn't valid or doesn't have sufficient authority, the command fails.</span></span>

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

### <span data-ttu-id="99a99-207">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="99a99-207">-CertificateThumbprint</span></span>

<span data-ttu-id="99a99-208">Anger det digitala certifikat för offentlig nyckel (X509) för ett användar konto som har behörighet att skicka begäran.</span><span class="sxs-lookup"><span data-stu-id="99a99-208">Specifies the digital public key certificate (X509) of a user account that has permission to send the request.</span></span> <span data-ttu-id="99a99-209">Ange certifikatets tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="99a99-209">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="99a99-210">Certifikat används i klient certifikat-baserad autentisering.</span><span class="sxs-lookup"><span data-stu-id="99a99-210">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="99a99-211">De kan endast mappas till lokala användar konton. de fungerar inte med domän konton.</span><span class="sxs-lookup"><span data-stu-id="99a99-211">They can be mapped only to local user accounts; they don't work with domain accounts.</span></span>

<span data-ttu-id="99a99-212">Om du vill hämta ett tumavtryck för certifikatet använder du `Get-Item` `Get-ChildItem` kommandot eller i PowerShell- `Cert:` enheten.</span><span class="sxs-lookup"><span data-stu-id="99a99-212">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the PowerShell `Cert:` drive.</span></span>

> [!NOTE]
> <span data-ttu-id="99a99-213">Den här funktionen stöds för närvarande endast på Windows OS-plattformar.</span><span class="sxs-lookup"><span data-stu-id="99a99-213">This feature is currently only supported on Windows OS platforms.</span></span>

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

### <span data-ttu-id="99a99-214">-ContentType</span><span class="sxs-lookup"><span data-stu-id="99a99-214">-ContentType</span></span>

<span data-ttu-id="99a99-215">Anger webb begärans innehålls typ.</span><span class="sxs-lookup"><span data-stu-id="99a99-215">Specifies the content type of the web request.</span></span>

<span data-ttu-id="99a99-216">Om den här parametern utelämnas och metoden för begäran är POST, `Invoke-WebRequest` anger innehålls typen till `application/x-www-form-urlencoded` .</span><span class="sxs-lookup"><span data-stu-id="99a99-216">If this parameter is omitted and the request method is POST, `Invoke-WebRequest` sets the content type to `application/x-www-form-urlencoded`.</span></span> <span data-ttu-id="99a99-217">Annars anges inte innehålls typen i anropet.</span><span class="sxs-lookup"><span data-stu-id="99a99-217">Otherwise, the content type isn't specified in the call.</span></span>

<span data-ttu-id="99a99-218">**ContentType** åsidosätts när ett **MultipartFormDataContent** -objekt anges för **brödtext**.</span><span class="sxs-lookup"><span data-stu-id="99a99-218">**ContentType** is overridden when a **MultipartFormDataContent** object is supplied for **Body**.</span></span>

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

### <span data-ttu-id="99a99-219">-Credential</span><span class="sxs-lookup"><span data-stu-id="99a99-219">-Credential</span></span>

<span data-ttu-id="99a99-220">Anger ett användar konto som har behörighet att skicka begäran.</span><span class="sxs-lookup"><span data-stu-id="99a99-220">Specifies a user account that has permission to send the request.</span></span> <span data-ttu-id="99a99-221">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="99a99-221">The default is the current user.</span></span>

<span data-ttu-id="99a99-222">Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="99a99-222">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="99a99-223">**Autentiseringsuppgifter** kan användas separat eller tillsammans med vissa parametrar för **autentiseringsprinciper** .</span><span class="sxs-lookup"><span data-stu-id="99a99-223">**Credential** can be used alone or in conjunction with certain **Authentication** parameter options.</span></span> <span data-ttu-id="99a99-224">När den används enbart, anger den bara autentiseringsuppgifter för fjärrservern om fjärrservern skickar en begäran om autentisering av begäran.</span><span class="sxs-lookup"><span data-stu-id="99a99-224">When used alone, it only supplies credentials to the remote server if the remote server sends an authentication challenge request.</span></span> <span data-ttu-id="99a99-225">När den används med **autentiseringsalternativ** skickas autentiseringsuppgifterna uttryckligen.</span><span class="sxs-lookup"><span data-stu-id="99a99-225">When used with **Authentication** options, the credentials are explicitly sent.</span></span>

<span data-ttu-id="99a99-226">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="99a99-226">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="99a99-227">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="99a99-227">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="99a99-228">-CustomMethod</span><span class="sxs-lookup"><span data-stu-id="99a99-228">-CustomMethod</span></span>

<span data-ttu-id="99a99-229">Anger en anpassad metod som används för webb förfrågan.</span><span class="sxs-lookup"><span data-stu-id="99a99-229">Specifies a custom method used for the web request.</span></span> <span data-ttu-id="99a99-230">Detta kan användas om den begär ande metoden som krävs av slut punkten inte är ett tillgängligt alternativ för **metoden**.</span><span class="sxs-lookup"><span data-stu-id="99a99-230">This can be used if the Request Method required by the endpoint isn't an available option on the **Method**.</span></span> <span data-ttu-id="99a99-231">**Metoden** och **CustomMethod** kan inte användas tillsammans.</span><span class="sxs-lookup"><span data-stu-id="99a99-231">**Method** and **CustomMethod** can't be used together.</span></span>

<span data-ttu-id="99a99-232">Det här exemplet gör en `TEST` http-begäran till API: et:</span><span class="sxs-lookup"><span data-stu-id="99a99-232">This example makes a `TEST` HTTP request to the API:</span></span>

`Invoke-WebRequest -uri 'https://api.contoso.com/widget/' -CustomMethod 'TEST'`

<span data-ttu-id="99a99-233">Den här funktionen har lagts till i PowerShell-6.0.0.</span><span class="sxs-lookup"><span data-stu-id="99a99-233">This feature was added in PowerShell 6.0.0.</span></span>

```yaml
Type: System.String
Parameter Sets: CustomMethod, CustomMethodNoProxy
Aliases: CM

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="99a99-234">-DisableKeepAlive</span><span class="sxs-lookup"><span data-stu-id="99a99-234">-DisableKeepAlive</span></span>

<span data-ttu-id="99a99-235">Anger att cmdleten anger **keepalive** -värdet i HTTP-huvudet till **false**.</span><span class="sxs-lookup"><span data-stu-id="99a99-235">Indicates that the cmdlet sets the **KeepAlive** value in the HTTP header to **False**.</span></span> <span data-ttu-id="99a99-236">**Keepalive** är som standard **Sant**.</span><span class="sxs-lookup"><span data-stu-id="99a99-236">By default, **KeepAlive** is **True**.</span></span> <span data-ttu-id="99a99-237">**Keepalive** upprättar en permanent anslutning till servern för att under lätta efterföljande begär Anden.</span><span class="sxs-lookup"><span data-stu-id="99a99-237">**KeepAlive** establishes a persistent connection to the server to facilitate subsequent requests.</span></span>

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

### <span data-ttu-id="99a99-238">-Form</span><span class="sxs-lookup"><span data-stu-id="99a99-238">-Form</span></span>

<span data-ttu-id="99a99-239">Konverterar en ord lista till ett `multipart/form-data` överförings objekt.</span><span class="sxs-lookup"><span data-stu-id="99a99-239">Converts a dictionary to a `multipart/form-data` submission.</span></span> <span data-ttu-id="99a99-240">**Formulär** får inte användas med **brödtext**.</span><span class="sxs-lookup"><span data-stu-id="99a99-240">**Form** may not be used with **Body**.</span></span>
<span data-ttu-id="99a99-241">Om **ContentType** används ignoreras det.</span><span class="sxs-lookup"><span data-stu-id="99a99-241">If **ContentType** is used, it's ignored.</span></span>

<span data-ttu-id="99a99-242">Nycklarna i ord listan används som formulär fält namn.</span><span class="sxs-lookup"><span data-stu-id="99a99-242">The keys of the dictionary are used as the form field names.</span></span> <span data-ttu-id="99a99-243">Som standard konverteras formulär värden till sträng värden.</span><span class="sxs-lookup"><span data-stu-id="99a99-243">By default, form values are converted to string values.</span></span>

<span data-ttu-id="99a99-244">Om värdet är ett **system. io. fileinfo** -objekt, skickas filen med binärfilen.</span><span class="sxs-lookup"><span data-stu-id="99a99-244">If the value is a **System.IO.FileInfo** object, then the binary file contents are submitted.</span></span> <span data-ttu-id="99a99-245">Namnet på filen skickas in som **filename** -egenskapen.</span><span class="sxs-lookup"><span data-stu-id="99a99-245">The name of the file is submitted as the **filename** property.</span></span> <span data-ttu-id="99a99-246">MIME-typen anges som `application/octet-stream` .</span><span class="sxs-lookup"><span data-stu-id="99a99-246">The MIME type is set as `application/octet-stream`.</span></span> <span data-ttu-id="99a99-247">`Get-Item` kan användas för att förenkla tillhandahålla **system. io. fileinfo** -objektet.</span><span class="sxs-lookup"><span data-stu-id="99a99-247">`Get-Item` can be used to simplify supplying the **System.IO.FileInfo** object.</span></span>

```powershell
$Form = @{
    resume = Get-Item 'c:\Users\jdoe\Documents\John Doe.pdf'
}
```

<span data-ttu-id="99a99-248">Om värdet är en samlings typ, sådana matriser eller listor skickas fältet for flera gånger.</span><span class="sxs-lookup"><span data-stu-id="99a99-248">If the value is a collection type, such Arrays or Lists, the for field are submitted multiple times.</span></span>
<span data-ttu-id="99a99-249">Värdena i listan behandlas som strängar som standard.</span><span class="sxs-lookup"><span data-stu-id="99a99-249">The values of the list are treated as strings by default.</span></span> <span data-ttu-id="99a99-250">Om värdet är ett **system. io. fileinfo** -objekt, skickas filen med binärfilen.</span><span class="sxs-lookup"><span data-stu-id="99a99-250">If the value is a **System.IO.FileInfo** object, then the binary file contents are submitted.</span></span> <span data-ttu-id="99a99-251">Kapslade samlingar stöds inte.</span><span class="sxs-lookup"><span data-stu-id="99a99-251">Nested collections aren't supported.</span></span>

```powershell
$Form = @{
    tags     = 'Vacation', 'Italy', '2017'
    pictures = Get-ChildItem 'c:\Users\jdoe\Pictures\2017-Italy\'
}
```

<span data-ttu-id="99a99-252">I exemplet ovan `tags` anges fältet tre gånger i formuläret, en gång för var och en av `Vacation` , `Italy` och `2017` .</span><span class="sxs-lookup"><span data-stu-id="99a99-252">In the above example the `tags` field are supplied three times in the form, once for each of `Vacation`, `Italy`, and `2017`.</span></span> <span data-ttu-id="99a99-253">`pictures`Fältet skickas också en gång för varje fil i `2017-Italy` mappen.</span><span class="sxs-lookup"><span data-stu-id="99a99-253">The `pictures` field is also submitted once for each file in the `2017-Italy` folder.</span></span> <span data-ttu-id="99a99-254">Det binära innehållet i filerna i mappen skickas som värden.</span><span class="sxs-lookup"><span data-stu-id="99a99-254">The binary contents of the files in that folder are submitted as the values.</span></span>

<span data-ttu-id="99a99-255">Den här funktionen har lagts till i PowerShell-6.1.0.</span><span class="sxs-lookup"><span data-stu-id="99a99-255">This feature was added in PowerShell 6.1.0.</span></span>

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

### <span data-ttu-id="99a99-256">– Sidhuvud</span><span class="sxs-lookup"><span data-stu-id="99a99-256">-Headers</span></span>

<span data-ttu-id="99a99-257">Anger webb begärans rubriker.</span><span class="sxs-lookup"><span data-stu-id="99a99-257">Specifies the headers of the web request.</span></span> <span data-ttu-id="99a99-258">Ange en hash-tabell eller-ord lista.</span><span class="sxs-lookup"><span data-stu-id="99a99-258">Enter a hash table or dictionary.</span></span>

<span data-ttu-id="99a99-259">Om du vill ange UserAgent-rubriker använder du parametern **useragent** .</span><span class="sxs-lookup"><span data-stu-id="99a99-259">To set UserAgent headers, use the **UserAgent** parameter.</span></span> <span data-ttu-id="99a99-260">Du kan inte använda den här parametern för att ange **användar agent** eller cookie-rubriker.</span><span class="sxs-lookup"><span data-stu-id="99a99-260">You can't use this parameter to specify **User-Agent** or cookie headers.</span></span>

<span data-ttu-id="99a99-261">Content-relaterade rubriker, som `Content-Type` åsidosätts när ett **MultipartFormDataContent** -objekt anges för **brödtext**.</span><span class="sxs-lookup"><span data-stu-id="99a99-261">Content related headers, such as `Content-Type` is overridden when a **MultipartFormDataContent** object is supplied for **Body**.</span></span>

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

### <span data-ttu-id="99a99-262">-INFILE</span><span class="sxs-lookup"><span data-stu-id="99a99-262">-InFile</span></span>

<span data-ttu-id="99a99-263">Hämtar innehållet i webb förfrågan från en fil.</span><span class="sxs-lookup"><span data-stu-id="99a99-263">Gets the content of the web request from a file.</span></span> <span data-ttu-id="99a99-264">Ange en sökväg och ett fil namn.</span><span class="sxs-lookup"><span data-stu-id="99a99-264">Enter a path and file name.</span></span> <span data-ttu-id="99a99-265">Om du utelämnar sökvägen är standardvärdet den aktuella platsen.</span><span class="sxs-lookup"><span data-stu-id="99a99-265">If you omit the path, the default is the current location.</span></span>

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

### <span data-ttu-id="99a99-266">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="99a99-266">-MaximumRedirection</span></span>

<span data-ttu-id="99a99-267">Anger hur många gånger PowerShell omdirigerar en anslutning till en alternativ Uniform Resource Identifier (URI) innan anslutningen Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="99a99-267">Specifies how many times PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="99a99-268">Standardvärdet är 5.</span><span class="sxs-lookup"><span data-stu-id="99a99-268">The default value is 5.</span></span> <span data-ttu-id="99a99-269">Värdet 0 (noll) förhindrar all omdirigering.</span><span class="sxs-lookup"><span data-stu-id="99a99-269">A value of 0 (zero) prevents all redirection.</span></span>

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

### <span data-ttu-id="99a99-270">-MaximumRetryCount</span><span class="sxs-lookup"><span data-stu-id="99a99-270">-MaximumRetryCount</span></span>

<span data-ttu-id="99a99-271">Anger hur många gånger PowerShell försöker upprätta en anslutning när en felkod mellan 400 och 599, inklusive eller 304, tas emot.</span><span class="sxs-lookup"><span data-stu-id="99a99-271">Specifies how many times PowerShell retries a connection when a failure code between 400 and 599, inclusive or 304 is received.</span></span> <span data-ttu-id="99a99-272">Se även **RetryIntervalSec** -parametern för att ange antal återförsök.</span><span class="sxs-lookup"><span data-stu-id="99a99-272">Also see **RetryIntervalSec** parameter for specifying number of retries.</span></span>

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

### <span data-ttu-id="99a99-273">-Metod</span><span class="sxs-lookup"><span data-stu-id="99a99-273">-Method</span></span>

<span data-ttu-id="99a99-274">Anger den metod som används för webb förfrågan.</span><span class="sxs-lookup"><span data-stu-id="99a99-274">Specifies the method used for the web request.</span></span> <span data-ttu-id="99a99-275">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="99a99-275">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="99a99-276">Default</span><span class="sxs-lookup"><span data-stu-id="99a99-276">Default</span></span>
- <span data-ttu-id="99a99-277">Ta bort</span><span class="sxs-lookup"><span data-stu-id="99a99-277">Delete</span></span>
- <span data-ttu-id="99a99-278">Hämta</span><span class="sxs-lookup"><span data-stu-id="99a99-278">Get</span></span>
- <span data-ttu-id="99a99-279">Head</span><span class="sxs-lookup"><span data-stu-id="99a99-279">Head</span></span>
- <span data-ttu-id="99a99-280">Sammanfoga</span><span class="sxs-lookup"><span data-stu-id="99a99-280">Merge</span></span>
- <span data-ttu-id="99a99-281">Alternativ</span><span class="sxs-lookup"><span data-stu-id="99a99-281">Options</span></span>
- <span data-ttu-id="99a99-282">Patch</span><span class="sxs-lookup"><span data-stu-id="99a99-282">Patch</span></span>
- <span data-ttu-id="99a99-283">Skicka</span><span class="sxs-lookup"><span data-stu-id="99a99-283">Post</span></span>
- <span data-ttu-id="99a99-284">Placera</span><span class="sxs-lookup"><span data-stu-id="99a99-284">Put</span></span>
- <span data-ttu-id="99a99-285">Spårning</span><span class="sxs-lookup"><span data-stu-id="99a99-285">Trace</span></span>

<span data-ttu-id="99a99-286">**CustomMethod** -parametern kan användas för förfrågnings metoder som inte anges ovan.</span><span class="sxs-lookup"><span data-stu-id="99a99-286">The **CustomMethod** parameter can be used for Request Methods not listed above.</span></span>

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

### <span data-ttu-id="99a99-287">-Noproxy</span><span class="sxs-lookup"><span data-stu-id="99a99-287">-NoProxy</span></span>

<span data-ttu-id="99a99-288">Anger att cmdleten inte ska använda en proxy för att komma till målet.</span><span class="sxs-lookup"><span data-stu-id="99a99-288">Indicates that the cmdlet shouldn't use a proxy to reach the destination.</span></span> <span data-ttu-id="99a99-289">Använd den här växeln när du behöver kringgå proxyn som kon figurer ATS i miljön.</span><span class="sxs-lookup"><span data-stu-id="99a99-289">When you need to bypass the proxy configured in the environment, use this switch.</span></span> <span data-ttu-id="99a99-290">Den här funktionen har lagts till i PowerShell-6.0.0.</span><span class="sxs-lookup"><span data-stu-id="99a99-290">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="99a99-291">-Fil</span><span class="sxs-lookup"><span data-stu-id="99a99-291">-OutFile</span></span>

<span data-ttu-id="99a99-292">Anger den utdatafil som denna cmdlet sparar svars texten för.</span><span class="sxs-lookup"><span data-stu-id="99a99-292">Specifies the output file for which this cmdlet saves the response body.</span></span> <span data-ttu-id="99a99-293">Ange en sökväg och ett fil namn.</span><span class="sxs-lookup"><span data-stu-id="99a99-293">Enter a path and file name.</span></span>
<span data-ttu-id="99a99-294">Om du utelämnar sökvägen är standardvärdet den aktuella platsen.</span><span class="sxs-lookup"><span data-stu-id="99a99-294">If you omit the path, the default is the current location.</span></span> <span data-ttu-id="99a99-295">Namnet behandlas som en literal sökväg.</span><span class="sxs-lookup"><span data-stu-id="99a99-295">The name is treated as a literal path.</span></span>
<span data-ttu-id="99a99-296">Namn som innehåller hakparenteser ( `[]` ) måste omges av enkla citat tecken ( `'` ).</span><span class="sxs-lookup"><span data-stu-id="99a99-296">Names that contain brackets (`[]`) must be enclosed in single quotes (`'`).</span></span>

<span data-ttu-id="99a99-297">Som standard `Invoke-WebRequest` returnerar resultatet till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="99a99-297">By default, `Invoke-WebRequest` returns the results to the pipeline.</span></span> <span data-ttu-id="99a99-298">Om du vill skicka resultatet till en fil och till pipelinen använder du parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="99a99-298">To send the results to a file and to the pipeline, use the **Passthru** parameter.</span></span>

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

### <span data-ttu-id="99a99-299">– PassThru</span><span class="sxs-lookup"><span data-stu-id="99a99-299">-PassThru</span></span>

<span data-ttu-id="99a99-300">Anger att cmdleten returnerar resultatet, förutom att skriva dem till en fil.</span><span class="sxs-lookup"><span data-stu-id="99a99-300">Indicates that the cmdlet returns the results, in addition to writing them to a file.</span></span> <span data-ttu-id="99a99-301">Den här parametern är endast giltig om **parametern out** också används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="99a99-301">This parameter is valid only when the **OutFile** parameter is also used in the command.</span></span>

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

### <span data-ttu-id="99a99-302">-PreserveAuthorizationOnRedirect</span><span class="sxs-lookup"><span data-stu-id="99a99-302">-PreserveAuthorizationOnRedirect</span></span>

<span data-ttu-id="99a99-303">Anger att cmdleten ska bevara `Authorization` sidhuvudet, om det finns, över omdirigeringar.</span><span class="sxs-lookup"><span data-stu-id="99a99-303">Indicates the cmdlet should preserve the `Authorization` header, when present, across redirections.</span></span>

<span data-ttu-id="99a99-304">Som standard tar cmdleten bort `Authorization` sidhuvudet före omdirigeringen.</span><span class="sxs-lookup"><span data-stu-id="99a99-304">By default, the cmdlet strips the `Authorization` header before redirecting.</span></span> <span data-ttu-id="99a99-305">Om du anger den här parametern inaktive ras den här logiken för fall där huvudet måste skickas till omdirigerings platsen.</span><span class="sxs-lookup"><span data-stu-id="99a99-305">Specifying this parameter disables this logic for cases where the header needs to be sent to the redirection location.</span></span>

<span data-ttu-id="99a99-306">Den här funktionen har lagts till i PowerShell-6.0.0.</span><span class="sxs-lookup"><span data-stu-id="99a99-306">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="99a99-307">-Proxy</span><span class="sxs-lookup"><span data-stu-id="99a99-307">-Proxy</span></span>

<span data-ttu-id="99a99-308">Anger en proxyserver för begäran, i stället för att ansluta direkt till Internet resursen.</span><span class="sxs-lookup"><span data-stu-id="99a99-308">Specifies a proxy server for the request, rather than connecting directly to the internet resource.</span></span>
<span data-ttu-id="99a99-309">Ange URI för en proxyserver för nätverket.</span><span class="sxs-lookup"><span data-stu-id="99a99-309">Enter the URI of a network proxy server.</span></span>

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

### <span data-ttu-id="99a99-310">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="99a99-310">-ProxyCredential</span></span>

<span data-ttu-id="99a99-311">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="99a99-311">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span> <span data-ttu-id="99a99-312">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="99a99-312">The default is the current user.</span></span>

<span data-ttu-id="99a99-313">Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , **User@Domain.Com** eller ange ett `PSCredential` objekt, till exempel en som genereras av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="99a99-313">Type a user name, such as **User01** or **Domain01\User01** , **User@Domain.Com** , or enter a `PSCredential` object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="99a99-314">Den här parametern är endast giltig när parametern **proxy** också används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="99a99-314">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="99a99-315">Du kan inte använda parametrarna **ProxyCredential** och **ProxyUseDefaultCredentials** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="99a99-315">You can't use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="99a99-316">-ProxyUseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="99a99-316">-ProxyUseDefaultCredentials</span></span>

<span data-ttu-id="99a99-317">Anger att cmdleten använder autentiseringsuppgifterna för den aktuella användaren för att få åtkomst till proxyservern som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="99a99-317">Indicates that the cmdlet uses the credentials of the current user to access the proxy server that is specified by the **Proxy** parameter.</span></span>

<span data-ttu-id="99a99-318">Den här parametern är endast giltig när parametern **proxy** också används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="99a99-318">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="99a99-319">Du kan inte använda parametrarna **ProxyCredential** och **ProxyUseDefaultCredentials** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="99a99-319">You can't use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="99a99-320">-Återuppta</span><span class="sxs-lookup"><span data-stu-id="99a99-320">-Resume</span></span>

<span data-ttu-id="99a99-321">Utför ett bästa försök att återuppta hämtningen av en delvis fil.</span><span class="sxs-lookup"><span data-stu-id="99a99-321">Performs a best effort attempt to resume downloading a partial file.</span></span> <span data-ttu-id="99a99-322">**Återställningen** kräver en **fil**.</span><span class="sxs-lookup"><span data-stu-id="99a99-322">**Resume** requires **OutFile**.</span></span>

<span data-ttu-id="99a99-323">**Återuppta** fungerar bara på storleken på den lokala filen och fjärrfilen och utför ingen annan validering av att den lokala filen och fjärrfilen är desamma.</span><span class="sxs-lookup"><span data-stu-id="99a99-323">**Resume** only operates on the size of the local file and remote file and performs no other validation that the local file and the remote file are the same.</span></span>

<span data-ttu-id="99a99-324">Om den lokala fil storleken är mindre än fjärrfils storleken försöker cmdleten återuppta nedladdningen av filen och lägga till återstående byte i slutet av filen.</span><span class="sxs-lookup"><span data-stu-id="99a99-324">If the local file size is smaller than the remote file size, then the cmdlet attempts to resume downloading the file and append the remaining bytes to the end of the file.</span></span>

<span data-ttu-id="99a99-325">Om den lokala fil storleken är samma som fjärrfilens storlek, utförs ingen åtgärd och cmdleten förutsätter att nedladdningen redan är slutförd.</span><span class="sxs-lookup"><span data-stu-id="99a99-325">If the local file size is the same as the remote file size, then no action is taken and the cmdlet assumes the download already complete.</span></span>

<span data-ttu-id="99a99-326">Om den lokala fil storleken är större än fjärrfilens storlek, skrivs den lokala filen över och hela fjärrfilen laddas ned igen.</span><span class="sxs-lookup"><span data-stu-id="99a99-326">If the local file size is larger than the remote file size, then the local file is overwritten and the entire remote file is re-downloaded.</span></span> <span data-ttu-id="99a99-327">Detta är samma sak som att använda en **fil** utan att **återuppta**.</span><span class="sxs-lookup"><span data-stu-id="99a99-327">This behavior is the same as using **OutFile** without **Resume**.</span></span>

<span data-ttu-id="99a99-328">Om fjärrservern inte stöder hämtnings återställning, skrivs den lokala filen över och hela fjärrfilen laddas ned igen.</span><span class="sxs-lookup"><span data-stu-id="99a99-328">If the remote server does not support download resuming, then the local file is overwritten and the entire remote file is re-downloaded.</span></span> <span data-ttu-id="99a99-329">Detta är samma sak som att använda en **fil** utan att **återuppta**.</span><span class="sxs-lookup"><span data-stu-id="99a99-329">This behavior is the same as using **OutFile** without **Resume**.</span></span>

<span data-ttu-id="99a99-330">Om den lokala filen inte finns skapas den lokala filen och hela fjärrfilen laddas ned.</span><span class="sxs-lookup"><span data-stu-id="99a99-330">If the local file does not exist, then the local file is created and the entire remote file is downloaded.</span></span> <span data-ttu-id="99a99-331">Detta är samma sak som att använda en **fil** utan att **återuppta**.</span><span class="sxs-lookup"><span data-stu-id="99a99-331">This behavior is the same as using **OutFile** without **Resume**.</span></span>

<span data-ttu-id="99a99-332">Den här funktionen har lagts till i PowerShell-6.1.0.</span><span class="sxs-lookup"><span data-stu-id="99a99-332">This feature was added in PowerShell 6.1.0.</span></span>

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

### <span data-ttu-id="99a99-333">-RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="99a99-333">-RetryIntervalSec</span></span>

<span data-ttu-id="99a99-334">Anger intervallet mellan återförsök för anslutningen när en felkod mellan 400 och 599, inklusive eller 304 tas emot.</span><span class="sxs-lookup"><span data-stu-id="99a99-334">Specifies the interval between retries for the connection when a failure code between 400 and 599, inclusive or 304 is received.</span></span> <span data-ttu-id="99a99-335">Se även **MaximumRetryCount** -parametern för att ange antal återförsök.</span><span class="sxs-lookup"><span data-stu-id="99a99-335">Also see **MaximumRetryCount** parameter for specifying number of retries.</span></span>

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

### <span data-ttu-id="99a99-336">-SessionVariable</span><span class="sxs-lookup"><span data-stu-id="99a99-336">-SessionVariable</span></span>

<span data-ttu-id="99a99-337">Anger en variabel för vilken denna cmdlet skapar en Webbbegäran-session och sparar den i värdet.</span><span class="sxs-lookup"><span data-stu-id="99a99-337">Specifies a variable for which this cmdlet creates a web request session and saves it in the value.</span></span>
<span data-ttu-id="99a99-338">Ange ett variabel namn utan dollar tecknet ( `$` )-symbolen.</span><span class="sxs-lookup"><span data-stu-id="99a99-338">Enter a variable name without the dollar sign (`$`) symbol.</span></span>

<span data-ttu-id="99a99-339">När du anger en sessionsvariabel `Invoke-WebRequest` skapar ett sessionsobjekt för Webbbegäran och tilldelar det till en variabel med det angivna namnet i PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="99a99-339">When you specify a session variable, `Invoke-WebRequest` creates a web request session object and assigns it to a variable with the specified name in your PowerShell session.</span></span> <span data-ttu-id="99a99-340">Du kan använda variabeln i din session så snart kommandot har slutförts.</span><span class="sxs-lookup"><span data-stu-id="99a99-340">You can use the variable in your session as soon as the command completes.</span></span>

<span data-ttu-id="99a99-341">Till skillnad från en fjärran sluten session är inte Webbbegäran-sessionen en permanent anslutning.</span><span class="sxs-lookup"><span data-stu-id="99a99-341">Unlike a remote session, the web request session is not a persistent connection.</span></span> <span data-ttu-id="99a99-342">Det är ett objekt som innehåller information om anslutningen och begäran, inklusive cookies, autentiseringsuppgifter, det maximala värdet för omdirigering och användar agent strängen.</span><span class="sxs-lookup"><span data-stu-id="99a99-342">It's an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="99a99-343">Du kan använda den för att dela tillstånd och data mellan webb förfrågningar.</span><span class="sxs-lookup"><span data-stu-id="99a99-343">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="99a99-344">Om du vill använda Webbbegäran-sessionen i efterföljande webb förfrågningar, anger du variabeln session i värdet för **websession** -parametern.</span><span class="sxs-lookup"><span data-stu-id="99a99-344">To use the web request session in subsequent web requests, specify the session variable in the value of the **WebSession** parameter.</span></span> <span data-ttu-id="99a99-345">PowerShell använder data i objektet Webbbegäran-session när den nya anslutningen upprättas.</span><span class="sxs-lookup"><span data-stu-id="99a99-345">PowerShell uses the data in the web request session object when establishing the new connection.</span></span> <span data-ttu-id="99a99-346">Om du vill åsidosätta ett värde i Webbbegäran-sessionen använder du en cmdlet-parameter, till exempel **useragent** eller **Credential**.</span><span class="sxs-lookup"><span data-stu-id="99a99-346">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential**.</span></span> <span data-ttu-id="99a99-347">Parameter värden har företräde framför värden i Webbbegäran-sessionen.</span><span class="sxs-lookup"><span data-stu-id="99a99-347">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="99a99-348">Du kan inte använda parametrarna **SessionVariable** och **websession** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="99a99-348">You can't use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="99a99-349">-SkipCertificateCheck</span><span class="sxs-lookup"><span data-stu-id="99a99-349">-SkipCertificateCheck</span></span>

<span data-ttu-id="99a99-350">Hoppar över certifikat verifierings kontroller.</span><span class="sxs-lookup"><span data-stu-id="99a99-350">Skips certificate validation checks.</span></span> <span data-ttu-id="99a99-351">Detta omfattar alla verifieringar som förfallo datum, åter kallelse, betrodd rot utfärdare osv.</span><span class="sxs-lookup"><span data-stu-id="99a99-351">This includes all validations such as expiration, revocation, trusted root authority, etc.</span></span>

> [!WARNING]
> <span data-ttu-id="99a99-352">Att använda den här parametern är inte säkert och rekommenderas inte.</span><span class="sxs-lookup"><span data-stu-id="99a99-352">Using this parameter is not secure and is not recommended.</span></span> <span data-ttu-id="99a99-353">Den här växeln är endast avsedd att användas mot kända värdar med hjälp av ett självsignerat certifikat i testnings syfte.</span><span class="sxs-lookup"><span data-stu-id="99a99-353">This switch is only intended to be used against known hosts using a self-signed certificate for testing purposes.</span></span> <span data-ttu-id="99a99-354">Använd på egen risk.</span><span class="sxs-lookup"><span data-stu-id="99a99-354">Use at your own risk.</span></span>

<span data-ttu-id="99a99-355">Den här funktionen har lagts till i PowerShell-6.0.0.</span><span class="sxs-lookup"><span data-stu-id="99a99-355">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="99a99-356">-SkipHeaderValidation</span><span class="sxs-lookup"><span data-stu-id="99a99-356">-SkipHeaderValidation</span></span>

<span data-ttu-id="99a99-357">Anger att cmdleten ska lägga till huvuden i begäran utan verifiering.</span><span class="sxs-lookup"><span data-stu-id="99a99-357">Indicates the cmdlet should add headers to the request without validation.</span></span>

<span data-ttu-id="99a99-358">Den här växeln bör användas för platser som kräver rubrik värden som inte uppfyller standarder.</span><span class="sxs-lookup"><span data-stu-id="99a99-358">This switch should be used for sites that require header values that do not conform to standards.</span></span>
<span data-ttu-id="99a99-359">Om du anger den här växeln inaktive ras verifieringen så att värdet inte kan skickas avmarkerat.</span><span class="sxs-lookup"><span data-stu-id="99a99-359">Specifying this switch disables validation to allow the value to be passed unchecked.</span></span> <span data-ttu-id="99a99-360">När det här värdet anges läggs alla rubriker till utan verifiering.</span><span class="sxs-lookup"><span data-stu-id="99a99-360">When specified, all headers are added without validation.</span></span>

<span data-ttu-id="99a99-361">Den här växeln inaktiverar verifiering av värden som skickas till parametrarna **ContentType** , **headers** och **useragent** .</span><span class="sxs-lookup"><span data-stu-id="99a99-361">This switch disables validation for values passed to the **ContentType** , **Headers** and **UserAgent** parameters.</span></span>

<span data-ttu-id="99a99-362">Den här funktionen har lagts till i PowerShell-6.0.0.</span><span class="sxs-lookup"><span data-stu-id="99a99-362">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="99a99-363">-SkipHttpErrorCheck</span><span class="sxs-lookup"><span data-stu-id="99a99-363">-SkipHttpErrorCheck</span></span>

<span data-ttu-id="99a99-364">Den här parametern gör att cmdleten ignorerar HTTP-fel status och fortsätter att bearbeta svar.</span><span class="sxs-lookup"><span data-stu-id="99a99-364">This parameter causes the cmdlet to ignore HTTP error statuses and continue to process responses.</span></span>
<span data-ttu-id="99a99-365">Fel Svaren skrivs till pipelinen precis som om de lyckades.</span><span class="sxs-lookup"><span data-stu-id="99a99-365">The error responses are written to the pipeline just as if they were successful.</span></span>

<span data-ttu-id="99a99-366">Den här parametern introducerades i PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="99a99-366">This parameter was introduced in PowerShell 7.</span></span>

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

### <span data-ttu-id="99a99-367">-SslProtocol</span><span class="sxs-lookup"><span data-stu-id="99a99-367">-SslProtocol</span></span>

<span data-ttu-id="99a99-368">Anger de SSL/TLS-protokoll som är tillåtna för webbegäran.</span><span class="sxs-lookup"><span data-stu-id="99a99-368">Sets the SSL/TLS protocols that are permissible for the web request.</span></span> <span data-ttu-id="99a99-369">Som standard är alla SSL/TLS-protokoll som stöds av systemet tillåtna.</span><span class="sxs-lookup"><span data-stu-id="99a99-369">By default all, SSL/TLS protocols supported by the system are allowed.</span></span> <span data-ttu-id="99a99-370">**SslProtocol** gör det möjligt att begränsa till vissa protokoll för efterlevnad.</span><span class="sxs-lookup"><span data-stu-id="99a99-370">**SslProtocol** allows for limiting to specific protocols for compliance purposes.</span></span>

<span data-ttu-id="99a99-371">**SslProtocol** använder **WebSslProtocol** -flaggan Enum.</span><span class="sxs-lookup"><span data-stu-id="99a99-371">**SslProtocol** uses the **WebSslProtocol** Flag Enum.</span></span> <span data-ttu-id="99a99-372">Det går att ange mer än ett protokoll med hjälp av flagg notation eller kombinera flera **WebSslProtocol** -alternativ med **bor** , men det finns inte stöd för att tillhandahålla flera protokoll på alla plattformar.</span><span class="sxs-lookup"><span data-stu-id="99a99-372">It is possible to supply more than one protocol using flag notation or combining multiple **WebSslProtocol** options with **bor** , however supplying multiple protocols is not supported on all platforms.</span></span>

> [!NOTE]
> <span data-ttu-id="99a99-373">På andra plattformar än Windows-plattformar kanske det inte går att tillhandahålla `Tls` eller `Tls12` som ett alternativ.</span><span class="sxs-lookup"><span data-stu-id="99a99-373">On non-Windows platforms it may not be possible to supply `Tls` or `Tls12` as an option.</span></span> <span data-ttu-id="99a99-374">Stöd för `Tls13` är inte tillgängligt på alla operativ system och måste kontrol leras per operativ system.</span><span class="sxs-lookup"><span data-stu-id="99a99-374">Support for `Tls13` is not available on all operating systems and will need to be verified on a per operating system basis.</span></span>

<span data-ttu-id="99a99-375">Den här funktionen har lagts till i PowerShell-6.0.0 och stöd för `Tls13` har lagts till i powershell 7,1.</span><span class="sxs-lookup"><span data-stu-id="99a99-375">This feature was added in PowerShell 6.0.0 and support for `Tls13` was added in PowerShell 7.1.</span></span>

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

### <span data-ttu-id="99a99-376">-TimeoutSec</span><span class="sxs-lookup"><span data-stu-id="99a99-376">-TimeoutSec</span></span>

<span data-ttu-id="99a99-377">Anger hur lång tid det tar att vänta på begäran innan den går ut. Ange ett värde i sekunder.</span><span class="sxs-lookup"><span data-stu-id="99a99-377">Specifies how long the request can be pending before it times out. Enter a value in seconds.</span></span> <span data-ttu-id="99a99-378">Standardvärdet 0 anger en obestämd tids gräns.</span><span class="sxs-lookup"><span data-stu-id="99a99-378">The default value, 0, specifies an indefinite time-out.</span></span>

<span data-ttu-id="99a99-379">En Domain Name System-fråga (DNS) kan ta upp till 15 sekunder att returnera eller ta slut för lång tid. Om din begäran innehåller ett värdnamn som kräver lösning och du anger **TimeoutSec** till ett värde som är större än noll, men mindre än 15 sekunder, kan det ta 15 sekunder eller mer innan en WebException utlöses, och tids gränsen för din begäran görs.</span><span class="sxs-lookup"><span data-stu-id="99a99-379">A Domain Name System (DNS) query can take up to 15 seconds to return or time out. If your request contains a host name that requires resolution, and you set **TimeoutSec** to a value greater than zero, but less than 15 seconds, it can take 15 seconds or more before a WebException is thrown, and your request times out.</span></span>

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

### <span data-ttu-id="99a99-380">-Token</span><span class="sxs-lookup"><span data-stu-id="99a99-380">-Token</span></span>

<span data-ttu-id="99a99-381">OAuth-eller Bearer-token som ska ingå i begäran.</span><span class="sxs-lookup"><span data-stu-id="99a99-381">The OAuth or Bearer token to include in the request.</span></span> <span data-ttu-id="99a99-382">**Token** krävs av vissa **autentiseringsalternativ** .</span><span class="sxs-lookup"><span data-stu-id="99a99-382">**Token** is required by certain **Authentication** options.</span></span> <span data-ttu-id="99a99-383">Den kan inte användas separat.</span><span class="sxs-lookup"><span data-stu-id="99a99-383">It cannot be used independently.</span></span>

<span data-ttu-id="99a99-384">**Token** tar en `SecureString` med token.</span><span class="sxs-lookup"><span data-stu-id="99a99-384">**Token** takes a `SecureString` containing the token.</span></span> <span data-ttu-id="99a99-385">Använd följande för att ange token manuellt:</span><span class="sxs-lookup"><span data-stu-id="99a99-385">To supply the token manually use the following:</span></span>

`Invoke-WebRequest -Uri $uri -Authentication OAuth -Token (Read-Host -AsSecureString)`

<span data-ttu-id="99a99-386">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="99a99-386">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="99a99-387">-TransferEncoding</span><span class="sxs-lookup"><span data-stu-id="99a99-387">-TransferEncoding</span></span>

<span data-ttu-id="99a99-388">Anger ett värde för HTTP-svarshuvuden för överförings kodning.</span><span class="sxs-lookup"><span data-stu-id="99a99-388">Specifies a value for the transfer-encoding HTTP response header.</span></span> <span data-ttu-id="99a99-389">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="99a99-389">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="99a99-390">Segment vis</span><span class="sxs-lookup"><span data-stu-id="99a99-390">Chunked</span></span>
- <span data-ttu-id="99a99-391">Compress</span><span class="sxs-lookup"><span data-stu-id="99a99-391">Compress</span></span>
- <span data-ttu-id="99a99-392">DEFLATE</span><span class="sxs-lookup"><span data-stu-id="99a99-392">Deflate</span></span>
- <span data-ttu-id="99a99-393">GZip</span><span class="sxs-lookup"><span data-stu-id="99a99-393">GZip</span></span>
- <span data-ttu-id="99a99-394">Identitet</span><span class="sxs-lookup"><span data-stu-id="99a99-394">Identity</span></span>

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

### <span data-ttu-id="99a99-395">-URI</span><span class="sxs-lookup"><span data-stu-id="99a99-395">-Uri</span></span>

<span data-ttu-id="99a99-396">Anger Uniform Resource Identifier (URI) för den Internet resurs som webb förfrågan skickas till.</span><span class="sxs-lookup"><span data-stu-id="99a99-396">Specifies the Uniform Resource Identifier (URI) of the internet resource to which the web request is sent.</span></span> <span data-ttu-id="99a99-397">Ange en URI.</span><span class="sxs-lookup"><span data-stu-id="99a99-397">Enter a URI.</span></span> <span data-ttu-id="99a99-398">Den här parametern stöder endast HTTP eller HTTPS.</span><span class="sxs-lookup"><span data-stu-id="99a99-398">This parameter supports HTTP or HTTPS only.</span></span>

<span data-ttu-id="99a99-399">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="99a99-399">This parameter is required.</span></span> <span data-ttu-id="99a99-400">Parameter namnet **URI** är valfritt.</span><span class="sxs-lookup"><span data-stu-id="99a99-400">The parameter name **Uri** is optional.</span></span>

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

### <span data-ttu-id="99a99-401">-UseBasicParsing</span><span class="sxs-lookup"><span data-stu-id="99a99-401">-UseBasicParsing</span></span>

<span data-ttu-id="99a99-402">Den här parametern är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="99a99-402">This parameter has been deprecated.</span></span> <span data-ttu-id="99a99-403">Från och med PowerShell-6.0.0 använder alla webbegäranden enbart grundläggande parsning.</span><span class="sxs-lookup"><span data-stu-id="99a99-403">Beginning with PowerShell 6.0.0, all Web requests use basic parsing only.</span></span> <span data-ttu-id="99a99-404">Den här parametern ingår endast för bakåtkompatibilitet och all användning av den har ingen påverkan på driften av cmdleten.</span><span class="sxs-lookup"><span data-stu-id="99a99-404">This parameter is included for backwards compatibility only and any use of it has no effect on the operation of the cmdlet.</span></span>

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

### <span data-ttu-id="99a99-405">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="99a99-405">-UseDefaultCredentials</span></span>

<span data-ttu-id="99a99-406">Anger att cmdleten använder autentiseringsuppgifterna för den aktuella användaren för att skicka webb förfrågan.</span><span class="sxs-lookup"><span data-stu-id="99a99-406">Indicates that the cmdlet uses the credentials of the current user to send the web request.</span></span> <span data-ttu-id="99a99-407">Detta kan inte användas med **autentisering** eller **autentiseringsuppgifter** och stöds inte på alla plattformar.</span><span class="sxs-lookup"><span data-stu-id="99a99-407">This can't be used with **Authentication** or **Credential** and may not be supported on all platforms.</span></span>

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

### <span data-ttu-id="99a99-408">– UserAgent</span><span class="sxs-lookup"><span data-stu-id="99a99-408">-UserAgent</span></span>

<span data-ttu-id="99a99-409">Anger en användar agent sträng för webb förfrågan.</span><span class="sxs-lookup"><span data-stu-id="99a99-409">Specifies a user agent string for the web request.</span></span>

<span data-ttu-id="99a99-410">Standard användar agenten liknar `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` med små variationer för varje operativ system och plattform.</span><span class="sxs-lookup"><span data-stu-id="99a99-410">The default user agent is similar to `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` with slight variations for each operating system and platform.</span></span>

<span data-ttu-id="99a99-411">Om du vill testa en webbplats med den standard användar agent sträng som används av de flesta webbläsare, använder du egenskaperna för [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) -klassen, till exempel Chrome, Firefox, InternetExplorer, Opera och Safari.</span><span class="sxs-lookup"><span data-stu-id="99a99-411">To test a website with the standard user agent string that is used by most internet browsers, use the properties of the [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) class, such as Chrome, FireFox, InternetExplorer, Opera, and Safari.</span></span>

<span data-ttu-id="99a99-412">Följande kommando använder till exempel användar agent strängen för Internet Explorer:</span><span class="sxs-lookup"><span data-stu-id="99a99-412">For example, the following command uses the user agent string for Internet Explorer:</span></span>

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

### <span data-ttu-id="99a99-413">– Websession</span><span class="sxs-lookup"><span data-stu-id="99a99-413">-WebSession</span></span>

<span data-ttu-id="99a99-414">Anger en Webbbegäran-session.</span><span class="sxs-lookup"><span data-stu-id="99a99-414">Specifies a web request session.</span></span> <span data-ttu-id="99a99-415">Ange variabel namnet, inklusive dollar tecknet ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="99a99-415">Enter the variable name, including the dollar sign (`$`).</span></span>

<span data-ttu-id="99a99-416">Om du vill åsidosätta ett värde i Webbbegäran-sessionen använder du en cmdlet-parameter, till exempel **useragent** eller **Credential**.</span><span class="sxs-lookup"><span data-stu-id="99a99-416">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential**.</span></span> <span data-ttu-id="99a99-417">Parameter värden har företräde framför värden i Webbbegäran-sessionen.</span><span class="sxs-lookup"><span data-stu-id="99a99-417">Parameter values take precedence over values in the web request session.</span></span> <span data-ttu-id="99a99-418">Content-relaterade rubriker, till exempel `Content-Type` , åsidosätts också när ett **MultipartFormDataContent** -objekt anges för **brödtext**.</span><span class="sxs-lookup"><span data-stu-id="99a99-418">Content related headers, such as `Content-Type`, are also be overridden when a **MultipartFormDataContent** object is supplied for **Body**.</span></span>

<span data-ttu-id="99a99-419">Till skillnad från en fjärran sluten session är inte Webbbegäran-sessionen en permanent anslutning.</span><span class="sxs-lookup"><span data-stu-id="99a99-419">Unlike a remote session, the web request session isn't a persistent connection.</span></span> <span data-ttu-id="99a99-420">Det är ett objekt som innehåller information om anslutningen och begäran, inklusive cookies, autentiseringsuppgifter, det maximala värdet för omdirigering och användar agent strängen.</span><span class="sxs-lookup"><span data-stu-id="99a99-420">It's an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="99a99-421">Du kan använda den för att dela tillstånd och data mellan webb förfrågningar.</span><span class="sxs-lookup"><span data-stu-id="99a99-421">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="99a99-422">Om du vill skapa en Webbbegäran-session anger du ett variabel namn, utan dollar tecken, i värdet för parametern **SessionVariable** för ett `Invoke-WebRequest` kommando.</span><span class="sxs-lookup"><span data-stu-id="99a99-422">To create a web request session, enter a variable name, without a dollar sign, in the value of the **SessionVariable** parameter of an `Invoke-WebRequest` command.</span></span> <span data-ttu-id="99a99-423">`Invoke-WebRequest` skapar sessionen och sparar den i variabeln.</span><span class="sxs-lookup"><span data-stu-id="99a99-423">`Invoke-WebRequest` creates the session and saves it in the variable.</span></span> <span data-ttu-id="99a99-424">I efterföljande kommandon använder du variabeln som värde för **websession** -parametern.</span><span class="sxs-lookup"><span data-stu-id="99a99-424">In subsequent commands, use the variable as the value of the **WebSession** parameter.</span></span>

<span data-ttu-id="99a99-425">Du kan inte använda parametrarna **SessionVariable** och **websession** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="99a99-425">You can't use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="99a99-426">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="99a99-426">CommonParameters</span></span>

<span data-ttu-id="99a99-427">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="99a99-427">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="99a99-428">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="99a99-428">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="99a99-429">INDATA</span><span class="sxs-lookup"><span data-stu-id="99a99-429">INPUTS</span></span>

### <span data-ttu-id="99a99-430">System. Object</span><span class="sxs-lookup"><span data-stu-id="99a99-430">System.Object</span></span>

<span data-ttu-id="99a99-431">Du kan skicka vidare innehållet i en webb förfrågan till `Invoke-WebRequest` .</span><span class="sxs-lookup"><span data-stu-id="99a99-431">You can pipe the body of a web request to `Invoke-WebRequest`.</span></span>

## <span data-ttu-id="99a99-432">UTDATA</span><span class="sxs-lookup"><span data-stu-id="99a99-432">OUTPUTS</span></span>

### <span data-ttu-id="99a99-433">Microsoft. PowerShell. commands. BasicHtmlWebResponseObject</span><span class="sxs-lookup"><span data-stu-id="99a99-433">Microsoft.PowerShell.Commands.BasicHtmlWebResponseObject</span></span>

## <span data-ttu-id="99a99-434">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="99a99-434">NOTES</span></span>

<span data-ttu-id="99a99-435">Från och med PowerShell 6.0.0 `Invoke-WebRequest` har endast stöd för grundläggande tolkning.</span><span class="sxs-lookup"><span data-stu-id="99a99-435">Beginning with PowerShell 6.0.0 `Invoke-WebRequest` supports basic parsing only.</span></span>

<span data-ttu-id="99a99-436">Mer information finns i [BasicHtmlWebResponseObject](/dotnet/api/microsoft.powershell.commands.basichtmlwebresponseobject).</span><span class="sxs-lookup"><span data-stu-id="99a99-436">For more information, see [BasicHtmlWebResponseObject](/dotnet/api/microsoft.powershell.commands.basichtmlwebresponseobject).</span></span>

<span data-ttu-id="99a99-437">På grund av ändringar i .NET Core 3,1 använder PowerShell 7,0 och senare egenskapen [httpclient. DefaultProxy](/dotnet/api/system.net.http.httpclient.defaultproxy?view=netcore-3.1) för att fastställa proxykonfigurationen.</span><span class="sxs-lookup"><span data-stu-id="99a99-437">Because of changes in .NET Core 3.1, PowerShell 7.0 and higher use the [HttpClient.DefaultProxy](/dotnet/api/system.net.http.httpclient.defaultproxy?view=netcore-3.1) Property to determine the proxy configuration.</span></span>

<span data-ttu-id="99a99-438">Värdet för den här egenskapen bestäms av din plattform:</span><span class="sxs-lookup"><span data-stu-id="99a99-438">The value of this property is determined by your platform:</span></span>

- <span data-ttu-id="99a99-439">**För Windows** : läser proxykonfigurationen från miljövariabler.</span><span class="sxs-lookup"><span data-stu-id="99a99-439">**For Windows** : Reads proxy configuration from environment variables.</span></span> <span data-ttu-id="99a99-440">Om dessa variabler inte är definierade härleds egenskapen från användarens proxyinställningar.</span><span class="sxs-lookup"><span data-stu-id="99a99-440">If those variables are not defined the property is derived from the user's proxy settings.</span></span>
- <span data-ttu-id="99a99-441">**För MacOS** : läser proxykonfigurationen från miljövariabler.</span><span class="sxs-lookup"><span data-stu-id="99a99-441">**For macOS** : Reads proxy configuration from environment variables.</span></span> <span data-ttu-id="99a99-442">Om dessa variabler inte är definierade härleds egenskapen från systemets proxyinställningar.</span><span class="sxs-lookup"><span data-stu-id="99a99-442">If those variables are not defined the property is derived from the system's proxy settings.</span></span>
- <span data-ttu-id="99a99-443">**För Linux** : läser proxykonfigurationen från miljövariabler.</span><span class="sxs-lookup"><span data-stu-id="99a99-443">**For Linux** : Reads proxy configuration from environment variables.</span></span> <span data-ttu-id="99a99-444">Om dessa variabler inte är definierade initierar egenskapen en icke-konfigurerad instans som kringgår alla adresser.</span><span class="sxs-lookup"><span data-stu-id="99a99-444">If those variables are not defined the property initializes a non-configured instance that bypasses all addresses.</span></span>

<span data-ttu-id="99a99-445">De miljövariabler som används för `DefaultProxy` initiering på Windows-och UNIX-baserade plattformar är:</span><span class="sxs-lookup"><span data-stu-id="99a99-445">The environment variables used for `DefaultProxy` initialization on Windows and Unix-based platforms are:</span></span>

- <span data-ttu-id="99a99-446">` HTTP_PROXY`: värd namnet eller IP-adressen för den proxyserver som används för HTTP-begäranden.</span><span class="sxs-lookup"><span data-stu-id="99a99-446">` HTTP_PROXY`: the hostname or IP address of the proxy server used on HTTP requests.</span></span>
- <span data-ttu-id="99a99-447">`HTTPS_PROXY`: värd namnet eller IP-adressen för den proxyserver som används på HTTPS-begäranden.</span><span class="sxs-lookup"><span data-stu-id="99a99-447">`HTTPS_PROXY`: the hostname or IP address of the proxy server used on HTTPS requests.</span></span>
- <span data-ttu-id="99a99-448">`ALL_PROXY`: värd namnet eller IP-adressen för proxyservern som används för HTTP-och HTTPS-begäranden i fall `HTTP_PROXY` eller `HTTPS_PROXY` som inte har definierats.</span><span class="sxs-lookup"><span data-stu-id="99a99-448">`ALL_PROXY`: the hostname or IP address of the proxy server used on HTTP and HTTPS requests in case `HTTP_PROXY` or `HTTPS_PROXY` are not defined.</span></span>
- <span data-ttu-id="99a99-449">`NO_PROXY`: en kommaavgränsad lista över värdnamn som ska undantas från proxy.</span><span class="sxs-lookup"><span data-stu-id="99a99-449">`NO_PROXY`: a comma-separated list of hostnames that should be excluded from proxying.</span></span>

## <span data-ttu-id="99a99-450">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="99a99-450">RELATED LINKS</span></span>

[<span data-ttu-id="99a99-451">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="99a99-451">Invoke-RestMethod</span></span>](Invoke-RestMethod.md)

[<span data-ttu-id="99a99-452">ConvertFrom – JSON</span><span class="sxs-lookup"><span data-stu-id="99a99-452">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="99a99-453">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="99a99-453">ConvertTo-Json</span></span>](ConvertTo-Json.md)
