---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 12/03/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/invoke-restmethod?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-RestMethod
ms.openlocfilehash: 541cceacab7462cc66483a2b75abedcd5c8abb7d
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265785"
---
# <span data-ttu-id="49955-103">Invoke-RestMethod</span><span class="sxs-lookup"><span data-stu-id="49955-103">Invoke-RestMethod</span></span>

## <span data-ttu-id="49955-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="49955-104">SYNOPSIS</span></span>
<span data-ttu-id="49955-105">Skickar en HTTP-eller HTTPS-begäran till en RESTful-webbtjänst.</span><span class="sxs-lookup"><span data-stu-id="49955-105">Sends an HTTP or HTTPS request to a RESTful web service.</span></span>

## <span data-ttu-id="49955-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="49955-106">SYNTAX</span></span>

### <span data-ttu-id="49955-107">StandardMethod (standard)</span><span class="sxs-lookup"><span data-stu-id="49955-107">StandardMethod (Default)</span></span>

```
Invoke-RestMethod [-Method <WebRequestMethod>] [-FollowRelLink] [-MaximumFollowRelLink <Int32>]
 [-ResponseHeadersVariable <String>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### <span data-ttu-id="49955-108">StandardMethodNoProxy</span><span class="sxs-lookup"><span data-stu-id="49955-108">StandardMethodNoProxy</span></span>

```
Invoke-RestMethod [-Method <WebRequestMethod>] [-FollowRelLink] [-MaximumFollowRelLink <Int32>]
 [-ResponseHeadersVariable <String>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] -NoProxy [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### <span data-ttu-id="49955-109">CustomMethod</span><span class="sxs-lookup"><span data-stu-id="49955-109">CustomMethod</span></span>

```
Invoke-RestMethod -CustomMethod <String> [-FollowRelLink] [-MaximumFollowRelLink <Int32>]
 [-ResponseHeadersVariable <String>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-ProxyUseDefaultCredentials] [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

### <span data-ttu-id="49955-110">CustomMethodNoProxy</span><span class="sxs-lookup"><span data-stu-id="49955-110">CustomMethodNoProxy</span></span>

```
Invoke-RestMethod -CustomMethod <String> [-FollowRelLink] [-MaximumFollowRelLink <Int32>]
 [-ResponseHeadersVariable <String>] [-UseBasicParsing] [-Uri] <Uri>
 [-WebSession <WebRequestSession>] [-SessionVariable <String>] [-AllowUnencryptedAuthentication]
 [-Authentication <WebAuthenticationType>] [-Credential <PSCredential>] [-UseDefaultCredentials]
 [-CertificateThumbprint <String>] [-Certificate <X509Certificate>] [-SkipCertificateCheck]
 [-SslProtocol <WebSslProtocol>] [-Token <SecureString>] [-UserAgent <String>] [-DisableKeepAlive]
 [-TimeoutSec <Int32>] [-Headers <IDictionary>] [-MaximumRedirection <Int32>]
 [-MaximumRetryCount <Int32>] [-RetryIntervalSec <Int32>] -NoProxy [-Body <Object>]
 [-Form <IDictionary>] [-ContentType <String>] [-TransferEncoding <String>] [-InFile <String>]
 [-OutFile <String>] [-PassThru] [-Resume] [-PreserveAuthorizationOnRedirect]
 [-SkipHeaderValidation] [<CommonParameters>]
```

## <span data-ttu-id="49955-111">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="49955-111">Description</span></span>

<span data-ttu-id="49955-112">`Invoke-RestMethod`Cmdlet: en skickar HTTP-och HTTPS-begäranden till en rest-webbtjänster (Representational State Transfer) som returnerar data som kan struktureras.</span><span class="sxs-lookup"><span data-stu-id="49955-112">The `Invoke-RestMethod` cmdlet sends HTTP and HTTPS requests to Representational State Transfer (REST) web services that return richly structured data.</span></span>

<span data-ttu-id="49955-113">PowerShell formaterar svaret baserat på data typen.</span><span class="sxs-lookup"><span data-stu-id="49955-113">PowerShell formats the response based to the data type.</span></span> <span data-ttu-id="49955-114">För en RSS-eller ATOM-feed returnerar PowerShell objektet eller postens XML-noder.</span><span class="sxs-lookup"><span data-stu-id="49955-114">For an RSS or ATOM feed, PowerShell returns the Item or Entry XML nodes.</span></span> <span data-ttu-id="49955-115">För JavaScript Object Notation (JSON) eller XML konverterar PowerShell eller deserialiserar innehållet till objekt.</span><span class="sxs-lookup"><span data-stu-id="49955-115">For JavaScript Object Notation (JSON) or XML, PowerShell converts, or deserializes, the content into objects.</span></span>

<span data-ttu-id="49955-116">Denna cmdlet introduceras i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="49955-116">This cmdlet is introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="49955-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="49955-117">EXAMPLES</span></span>

### <span data-ttu-id="49955-118">Exempel 1: Hämta PowerShell RSS-flödet</span><span class="sxs-lookup"><span data-stu-id="49955-118">Example 1: Get the PowerShell RSS feed</span></span>

<span data-ttu-id="49955-119">I det här exemplet används `Invoke-RestMethod` cmdleten för att hämta information från RSS-flödet i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="49955-119">This example uses the `Invoke-RestMethod` cmdlet to get information from the PowerShell Blog RSS feed.</span></span> <span data-ttu-id="49955-120">Kommandot använder `Format-Table` cmdleten för att visa värdena för egenskaperna **title** och **pubDate** för varje blogg i en tabell.</span><span class="sxs-lookup"><span data-stu-id="49955-120">The command uses the `Format-Table` cmdlet to display the values of the **Title** and **pubDate** properties of each blog in a table.</span></span>

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

### <span data-ttu-id="49955-121">Exempel 2: kör en POST-begäran</span><span class="sxs-lookup"><span data-stu-id="49955-121">Example 2: Run a POST request</span></span>

<span data-ttu-id="49955-122">I det här exemplet körs en användare `Invoke-RestMethod` för att göra en post-begäran på en intranäts webbplats i användarens organisation.</span><span class="sxs-lookup"><span data-stu-id="49955-122">In this example, a user runs `Invoke-RestMethod` to do a POST request on an intranet website in the user's organization.</span></span>

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

<span data-ttu-id="49955-123">Autentiseringsuppgifterna efter frågas och lagras sedan i `$Cred` och den URL som ska vara åtkomst definieras i `$Url` .</span><span class="sxs-lookup"><span data-stu-id="49955-123">The credentials are prompted for and then stored in `$Cred` and the URL that will be access is defined in `$Url`.</span></span>

<span data-ttu-id="49955-124">`$Body`Variabeln beskriver Sök villkoren, anger CSV som output-läge och anger en tids period för returnerade data som börjar två dagar sedan och slutar en dag sedan.</span><span class="sxs-lookup"><span data-stu-id="49955-124">The `$Body` variable describes the search criteria, specifies CSV as the output mode, and specifies a time period for returned data that starts two days ago and ends one day ago.</span></span> <span data-ttu-id="49955-125">Body-variabeln anger värden för parametrar som gäller för den specifika REST API som `Invoke-RestMethod` kommunicerar med.</span><span class="sxs-lookup"><span data-stu-id="49955-125">The body variable specifies values for parameters that apply to the particular REST API with which `Invoke-RestMethod` is communicating.</span></span>

<span data-ttu-id="49955-126">`Invoke-RestMethod`Kommandot körs med alla variabler på plats och anger en sökväg och ett fil namn för den resulterande CSV-utdatafilen.</span><span class="sxs-lookup"><span data-stu-id="49955-126">The `Invoke-RestMethod` command is run with all variables in place, specifying a path and file name for the resulting CSV output file.</span></span>

### <span data-ttu-id="49955-127">Exempel 3: Följ Relations länkar</span><span class="sxs-lookup"><span data-stu-id="49955-127">Example 3: Follow relation links</span></span>

<span data-ttu-id="49955-128">Vissa REST API: er stöder sid brytning via Relations länkar per [RFC5988](https://tools.ietf.org/html/rfc5988#page-6).</span><span class="sxs-lookup"><span data-stu-id="49955-128">Some REST APIs support pagination via Relation Links per [RFC5988](https://tools.ietf.org/html/rfc5988#page-6).</span></span> <span data-ttu-id="49955-129">I stället för att parsa rubriken för att hämta URL: en för nästa sida kan du låta cmdlet: en göra detta åt dig.</span><span class="sxs-lookup"><span data-stu-id="49955-129">Instead of parsing the header to get the URL for the next page, you can have the cmdlet do this for you.</span></span> <span data-ttu-id="49955-130">Det här exemplet returnerar de två första sidor med problem från PowerShell-GitHub-lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="49955-130">This example returns the first two pages of issues from the PowerShell GitHub repository.</span></span>

```powershell
$url = 'https://api.github.com/repos/powershell/powershell/issues'
Invoke-RestMethod $url -FollowRelLink -MaximumFollowRelLink 2
```

### <span data-ttu-id="49955-131">Exempel 4: överföring av förenklad multipart/form – data</span><span class="sxs-lookup"><span data-stu-id="49955-131">Example 4: Simplified Multipart/Form-Data Submission</span></span>

<span data-ttu-id="49955-132">Vissa API: er kräver att det går `multipart/form-data` att överföra filer och blandat innehåll.</span><span class="sxs-lookup"><span data-stu-id="49955-132">Some APIs require `multipart/form-data` submissions to upload files and mixed content.</span></span> <span data-ttu-id="49955-133">Det här exemplet visar hur du uppdaterar en användares profil.</span><span class="sxs-lookup"><span data-stu-id="49955-133">This example demonstrates how to update a user's profile.</span></span>

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

<span data-ttu-id="49955-134">Profil formuläret kräver följande fält:,,,, `firstName` `lastName` `email` `avatar` `birthday` och `hobbies` .</span><span class="sxs-lookup"><span data-stu-id="49955-134">The profile form requires these fields: `firstName`, `lastName`, `email`, `avatar`, `birthday`, and `hobbies`.</span></span> <span data-ttu-id="49955-135">API: et förväntar sig en bild för användar profils pic som ska anges i `avatar` fältet.</span><span class="sxs-lookup"><span data-stu-id="49955-135">The API is expecting an image for the user profile pic to be supplied in the `avatar` field.</span></span> <span data-ttu-id="49955-136">API: et kommer också att acceptera flera `hobbies` poster som ska skickas i samma formulär.</span><span class="sxs-lookup"><span data-stu-id="49955-136">The API will also accept multiple `hobbies` entries to be submitted in the same form.</span></span>

<span data-ttu-id="49955-137">När du skapar en `$Form` hash-tabellen används nyckel namnen som namn på formulär fält.</span><span class="sxs-lookup"><span data-stu-id="49955-137">When creating the `$Form` HashTable, the key names are used as form field names.</span></span> <span data-ttu-id="49955-138">Som standard konverteras värdena för hash-tabellen till strängar.</span><span class="sxs-lookup"><span data-stu-id="49955-138">By default, the values of the HashTable will be converted to strings.</span></span> <span data-ttu-id="49955-139">Om det finns ett `System.IO.FileInfo` värde skickas filens innehåll.</span><span class="sxs-lookup"><span data-stu-id="49955-139">If a `System.IO.FileInfo` value is present, the file contents will be submitted.</span></span> <span data-ttu-id="49955-140">Om det finns en samling, till exempel matriser eller listor, skickas formulär fältet flera gånger.</span><span class="sxs-lookup"><span data-stu-id="49955-140">If a collection such as arrays or lists are present, the form field will be submitted multiple times.</span></span>

<span data-ttu-id="49955-141">Genom att använda `Get-Item` på `avatar` nyckeln `FileInfo` anges objektet som värde.</span><span class="sxs-lookup"><span data-stu-id="49955-141">By using `Get-Item` on the `avatar` key, the `FileInfo` object will be set as the value.</span></span> <span data-ttu-id="49955-142">Resultatet är att bild data för `jdoe.png` skickas.</span><span class="sxs-lookup"><span data-stu-id="49955-142">The result is that the image data for `jdoe.png` will be submitted.</span></span>

<span data-ttu-id="49955-143">Om du anger en lista till `hobbies` nyckeln `hobbies` visas fältet i de här sändningarna en gång för varje List objekt.</span><span class="sxs-lookup"><span data-stu-id="49955-143">By supplying a list to the `hobbies` key, the `hobbies` field will be present in the submissions once for each list item.</span></span>

### <span data-ttu-id="49955-144">Exempel 5: skicka flera huvuden</span><span class="sxs-lookup"><span data-stu-id="49955-144">Example 5: Pass multiple headers</span></span>

<span data-ttu-id="49955-145">API: er kräver ofta skickade rubriker för autentisering eller verifiering.</span><span class="sxs-lookup"><span data-stu-id="49955-145">APIs often require passed headers for authentication or validation.</span></span> <span data-ttu-id="49955-146">Det här exemplet visar hur du skickar flera huvuden från en `hash-table` till en REST API.</span><span class="sxs-lookup"><span data-stu-id="49955-146">This example demonstrates, how to pass multiple headers from a `hash-table` to a REST API.</span></span>

```powershell
$headers = @{
    'userId' = 'UserIDValue'
    'token' = 'TokenValue'
}
Invoke-RestMethod -Uri $uri -Method Post -Headers $headers -Body $body
```

## <span data-ttu-id="49955-147">Parametrar</span><span class="sxs-lookup"><span data-stu-id="49955-147">Parameters</span></span>

### <span data-ttu-id="49955-148">-AllowUnencryptedAuthentication</span><span class="sxs-lookup"><span data-stu-id="49955-148">-AllowUnencryptedAuthentication</span></span>

<span data-ttu-id="49955-149">Tillåter sändning av autentiseringsuppgifter och hemligheter över okrypterade anslutningar.</span><span class="sxs-lookup"><span data-stu-id="49955-149">Allows sending of credentials and secrets over unencrypted connections.</span></span> <span data-ttu-id="49955-150">Som standard, anger **Credential** eller valfritt **autentiseringsalternativ** med en **URI** som inte börjar med `https://` , resulterar i ett fel och begäran avbryts för att förhindra oavsiktlig kommunikation av hemligheter i oformaterad text över okrypterade anslutningar.</span><span class="sxs-lookup"><span data-stu-id="49955-150">By default, supplying **Credential** or any **Authentication** option with a **Uri** that does not begin with `https://` will result in an error and the request will abort to prevent unintentionally communicating secrets in plain text over unencrypted connections.</span></span> <span data-ttu-id="49955-151">Om du vill åsidosätta det här beteendet på egen risk anger du parametern **AllowUnencryptedAuthentication** .</span><span class="sxs-lookup"><span data-stu-id="49955-151">To override this behavior at your own risk, supply the **AllowUnencryptedAuthentication** parameter.</span></span>

> [!WARNING]
> <span data-ttu-id="49955-152">Att använda den här parametern är inte säkert och rekommenderas inte.</span><span class="sxs-lookup"><span data-stu-id="49955-152">Using this parameter is not secure and is not recommended.</span></span> <span data-ttu-id="49955-153">Det tillhandahålls endast för kompatibilitet med äldre system som inte kan tillhandahålla krypterade anslutningar.</span><span class="sxs-lookup"><span data-stu-id="49955-153">It is provided only for compatibility with legacy systems that cannot provide encrypted connections.</span></span> <span data-ttu-id="49955-154">Använd på egen risk.</span><span class="sxs-lookup"><span data-stu-id="49955-154">Use at your own risk.</span></span>

<span data-ttu-id="49955-155">Den här funktionen har lagts till i PowerShell-6.0.0.</span><span class="sxs-lookup"><span data-stu-id="49955-155">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="49955-156">-Autentisering</span><span class="sxs-lookup"><span data-stu-id="49955-156">-Authentication</span></span>

<span data-ttu-id="49955-157">Anger den explicita autentiseringstypen som ska användas för begäran.</span><span class="sxs-lookup"><span data-stu-id="49955-157">Specifies the explicit authentication type to use for the request.</span></span> <span data-ttu-id="49955-158">Standardvärdet är **none**.</span><span class="sxs-lookup"><span data-stu-id="49955-158">The default is **None**.</span></span>
<span data-ttu-id="49955-159">Det går inte att använda **autentisering** med **UseDefaultCredentials**.</span><span class="sxs-lookup"><span data-stu-id="49955-159">**Authentication** can't be used with **UseDefaultCredentials**.</span></span>

<span data-ttu-id="49955-160">Tillgängliga autentiserings alternativ:</span><span class="sxs-lookup"><span data-stu-id="49955-160">Available Authentication Options:</span></span>

- <span data-ttu-id="49955-161">**Ingen** : det här är standard alternativet när **autentisering** inte anges.</span><span class="sxs-lookup"><span data-stu-id="49955-161">**None** : This is the default option when **Authentication** is not supplied.</span></span> <span data-ttu-id="49955-162">Ingen explicit autentisering kommer att användas.</span><span class="sxs-lookup"><span data-stu-id="49955-162">No explicit authentication will be used.</span></span>
- <span data-ttu-id="49955-163">**Basic** : kräver **autentiseringsuppgifter**.</span><span class="sxs-lookup"><span data-stu-id="49955-163">**Basic** : Requires **Credential**.</span></span> <span data-ttu-id="49955-164">Autentiseringsuppgifterna kommer att användas för att skicka ett RFC 7617 Basic Authentication- `Authorization: Basic` huvud i formatet `base64(user:password)` .</span><span class="sxs-lookup"><span data-stu-id="49955-164">The credentials will be used to send an RFC 7617 Basic Authentication `Authorization: Basic` header in the format of `base64(user:password)`.</span></span>
- <span data-ttu-id="49955-165">**Bearer** : kräver **token**.</span><span class="sxs-lookup"><span data-stu-id="49955-165">**Bearer** : Requires **Token**.</span></span> <span data-ttu-id="49955-166">Kommer att skicka och RFC 6750- `Authorization: Bearer` huvud med angiven token.</span><span class="sxs-lookup"><span data-stu-id="49955-166">Will send and RFC 6750 `Authorization: Bearer` header with the supplied token.</span></span> <span data-ttu-id="49955-167">Detta är ett alias för **OAuth**</span><span class="sxs-lookup"><span data-stu-id="49955-167">This is an alias for **OAuth**</span></span>
- <span data-ttu-id="49955-168">**OAuth** : kräver **token**.</span><span class="sxs-lookup"><span data-stu-id="49955-168">**OAuth** : Requires **Token**.</span></span> <span data-ttu-id="49955-169">Skickar ett RFC 6750- `Authorization: Bearer` huvud med angiven token.</span><span class="sxs-lookup"><span data-stu-id="49955-169">Will send an RFC 6750 `Authorization: Bearer` header with the supplied token.</span></span> <span data-ttu-id="49955-170">Detta är ett alias för **innehavare**</span><span class="sxs-lookup"><span data-stu-id="49955-170">This is an alias for **Bearer**</span></span>

<span data-ttu-id="49955-171">Om du anger **autentisering** åsidosätts alla `Authorization` rubriker som anges i **sidhuvuden** eller som ingår i **websessionen**.</span><span class="sxs-lookup"><span data-stu-id="49955-171">Supplying **Authentication** will override any `Authorization` headers supplied to **Headers** or included in **WebSession**.</span></span>

<span data-ttu-id="49955-172">Den här funktionen har lagts till i PowerShell-6.0.0.</span><span class="sxs-lookup"><span data-stu-id="49955-172">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="49955-173">-Body</span><span class="sxs-lookup"><span data-stu-id="49955-173">-Body</span></span>

<span data-ttu-id="49955-174">Anger bröd texten i begäran.</span><span class="sxs-lookup"><span data-stu-id="49955-174">Specifies the body of the request.</span></span> <span data-ttu-id="49955-175">Bröd texten är innehållet i begäran som följer sidhuvuden.</span><span class="sxs-lookup"><span data-stu-id="49955-175">The body is the content of the request that follows the headers.</span></span>
<span data-ttu-id="49955-176">Du kan också skicka ett Body-värde till `Invoke-RestMethod` .</span><span class="sxs-lookup"><span data-stu-id="49955-176">You can also pipe a body value to `Invoke-RestMethod`.</span></span>

<span data-ttu-id="49955-177">Du kan använda **text** parametern för att ange en lista över frågeparametrar eller ange svarets innehåll.</span><span class="sxs-lookup"><span data-stu-id="49955-177">The **Body** parameter can be used to specify a list of query parameters or specify the content of the response.</span></span>

<span data-ttu-id="49955-178">När indatamängden är en GET-begäran och texten är en `IDictionary` (vanligt vis en hash-tabell) läggs bröd texten till i Uniform Resource Identifier (URI) som frågeparametrar.</span><span class="sxs-lookup"><span data-stu-id="49955-178">When the input is a GET request, and the body is an `IDictionary` (typically, a hash table), the body is added to the Uniform Resource Identifier (URI) as query parameters.</span></span> <span data-ttu-id="49955-179">För andra typer av begär Anden (till exempel POST) anges bröd texten som värdet för begär ande texten i standard namnet = värde formatet.</span><span class="sxs-lookup"><span data-stu-id="49955-179">For other request types (such as POST), the body is set as the value of the request body in the standard name=value format.</span></span>

<span data-ttu-id="49955-180">När bröd texten är ett formulär eller om det är utdata från ett annat `Invoke-WebRequest` anrop, anger PowerShell innehållet i formulär fälten.</span><span class="sxs-lookup"><span data-stu-id="49955-180">When the body is a form, or it's the output of another `Invoke-WebRequest` call, PowerShell sets the request content to the form fields.</span></span>

<span data-ttu-id="49955-181">**Bröd text** parametern kan också acceptera ett **system .net. http. MultipartFormDataContent-** objekt.</span><span class="sxs-lookup"><span data-stu-id="49955-181">The **Body** parameter may also accept a **System.Net.Http.MultipartFormDataContent** object.</span></span> <span data-ttu-id="49955-182">Detta underlättar `multipart/form-data` begär Anden.</span><span class="sxs-lookup"><span data-stu-id="49955-182">This will facilitate `multipart/form-data` requests.</span></span> <span data-ttu-id="49955-183">När ett **MultipartFormDataContent** -objekt anges för **brödtext** , åsidosätts alla innehåll relaterade rubriker som har angetts för egenskaperna **ContentType** , **headers** eller **websession** av `MultipartFormDataContent` objektets innehålls rubriker.</span><span class="sxs-lookup"><span data-stu-id="49955-183">When a **MultipartFormDataContent** object is supplied for **Body** , any content related headers supplied to the **ContentType** , **Headers** , or **WebSession** parameters will be overridden by the content headers of the `MultipartFormDataContent` object.</span></span> <span data-ttu-id="49955-184">Den här funktionen har lagts till i PowerShell-6.0.0.</span><span class="sxs-lookup"><span data-stu-id="49955-184">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="49955-185">– Certifikat</span><span class="sxs-lookup"><span data-stu-id="49955-185">-Certificate</span></span>

<span data-ttu-id="49955-186">Anger det klient certifikat som används för en säker webb förfrågan.</span><span class="sxs-lookup"><span data-stu-id="49955-186">Specifies the client certificate that is used for a secure web request.</span></span> <span data-ttu-id="49955-187">Ange en variabel som innehåller ett certifikat eller ett kommando eller uttryck som hämtar certifikatet.</span><span class="sxs-lookup"><span data-stu-id="49955-187">Enter a variable that contains a certificate or a command or expression that gets the certificate.</span></span>

<span data-ttu-id="49955-188">Om du vill söka efter ett certifikat använder `Get-PfxCertificate` eller använder du `Get-ChildItem` cmdleten på certifikat `Cert:` enheten ().</span><span class="sxs-lookup"><span data-stu-id="49955-188">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the Certificate (`Cert:`) drive.</span></span> <span data-ttu-id="49955-189">Om certifikatet inte är giltigt eller inte har tillräcklig behörighet, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="49955-189">If the certificate isn't valid or doesn't have sufficient authority, the command fails.</span></span>

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

### <span data-ttu-id="49955-190">-CertificateThumbprint</span><span class="sxs-lookup"><span data-stu-id="49955-190">-CertificateThumbprint</span></span>

<span data-ttu-id="49955-191">Anger det digitala certifikat för offentlig nyckel (X509) för ett användar konto som har behörighet att skicka begäran.</span><span class="sxs-lookup"><span data-stu-id="49955-191">Specifies the digital public key certificate (X509) of a user account that has permission to send the request.</span></span> <span data-ttu-id="49955-192">Ange certifikatets tumavtryck.</span><span class="sxs-lookup"><span data-stu-id="49955-192">Enter the certificate thumbprint of the certificate.</span></span>

<span data-ttu-id="49955-193">Certifikat används i klient certifikat-baserad autentisering.</span><span class="sxs-lookup"><span data-stu-id="49955-193">Certificates are used in client certificate-based authentication.</span></span> <span data-ttu-id="49955-194">De kan endast mappas till lokala användar konton. de fungerar inte med domän konton.</span><span class="sxs-lookup"><span data-stu-id="49955-194">They can be mapped only to local user accounts; they do not work with domain accounts.</span></span>

<span data-ttu-id="49955-195">Om du vill hämta ett tumavtryck för certifikatet använder du `Get-Item` `Get-ChildItem` kommandot eller i PowerShell- `Cert:` enheten.</span><span class="sxs-lookup"><span data-stu-id="49955-195">To get a certificate thumbprint, use the `Get-Item` or `Get-ChildItem` command in the PowerShell `Cert:` drive.</span></span>

> [!NOTE]
> <span data-ttu-id="49955-196">Den här funktionen stöds för närvarande endast på Windows OS-plattformar.</span><span class="sxs-lookup"><span data-stu-id="49955-196">This feature is currently only supported on Windows OS platforms.</span></span>

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

### <span data-ttu-id="49955-197">-ContentType</span><span class="sxs-lookup"><span data-stu-id="49955-197">-ContentType</span></span>

<span data-ttu-id="49955-198">Anger webb begärans innehålls typ.</span><span class="sxs-lookup"><span data-stu-id="49955-198">Specifies the content type of the web request.</span></span>

<span data-ttu-id="49955-199">Om den här parametern utelämnas och metoden för begäran är POST, `Invoke-RestMethod` anger innehålls typen till `application/x-www-form-urlencoded` .</span><span class="sxs-lookup"><span data-stu-id="49955-199">If this parameter is omitted and the request method is POST, `Invoke-RestMethod` sets the content type to `application/x-www-form-urlencoded`.</span></span> <span data-ttu-id="49955-200">Annars anges inte innehålls typen i anropet.</span><span class="sxs-lookup"><span data-stu-id="49955-200">Otherwise, the content type isn't specified in the call.</span></span>

<span data-ttu-id="49955-201">**ContentType** kommer att åsidosättas när ett `MultipartFormDataContent` objekt anges för **brödtext**.</span><span class="sxs-lookup"><span data-stu-id="49955-201">**ContentType** will be overridden when a `MultipartFormDataContent` object is supplied for **Body**.</span></span>

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

### <span data-ttu-id="49955-202">-Credential</span><span class="sxs-lookup"><span data-stu-id="49955-202">-Credential</span></span>

<span data-ttu-id="49955-203">Anger ett användar konto som har behörighet att skicka begäran.</span><span class="sxs-lookup"><span data-stu-id="49955-203">Specifies a user account that has permission to send the request.</span></span> <span data-ttu-id="49955-204">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="49955-204">The default is the current user.</span></span>

<span data-ttu-id="49955-205">Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="49955-205">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="49955-206">**Autentiseringsuppgifter** kan användas separat eller tillsammans med vissa parametrar för **autentiseringsprinciper** .</span><span class="sxs-lookup"><span data-stu-id="49955-206">**Credential** can be used alone or in conjunction with certain **Authentication** parameter options.</span></span> <span data-ttu-id="49955-207">När den används enbart skickas autentiseringsuppgifter till fjärrservern om fjärrservern skickar en begäran om autentisering av begäran.</span><span class="sxs-lookup"><span data-stu-id="49955-207">When used alone, it will only supply credentials to the remote server if the remote server sends an authentication challenge request.</span></span> <span data-ttu-id="49955-208">När den används med **autentiseringsalternativ** skickas autentiseringsuppgifterna uttryckligen.</span><span class="sxs-lookup"><span data-stu-id="49955-208">When used with **Authentication** options, the credentials will be explicitly sent.</span></span>

<span data-ttu-id="49955-209">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="49955-209">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="49955-210">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="49955-210">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="49955-211">-CustomMethod</span><span class="sxs-lookup"><span data-stu-id="49955-211">-CustomMethod</span></span>

<span data-ttu-id="49955-212">Anger en anpassad metod som används för webbegäran.</span><span class="sxs-lookup"><span data-stu-id="49955-212">Specifies custom method used for the web request.</span></span> <span data-ttu-id="49955-213">Detta kan användas med den metod för begäran som krävs av slut punkten är inte ett tillgängligt alternativ för **metoden**.</span><span class="sxs-lookup"><span data-stu-id="49955-213">This can be used with the Request Method required by the endpoint is not an available option on the **Method**.</span></span> <span data-ttu-id="49955-214">**Metoden** och **CustomMethod** kan inte användas tillsammans.</span><span class="sxs-lookup"><span data-stu-id="49955-214">**Method** and **CustomMethod** cannot be used together.</span></span>

<span data-ttu-id="49955-215">Exempel:</span><span class="sxs-lookup"><span data-stu-id="49955-215">Example:</span></span>

`Invoke-RestMethod -uri 'https://api.contoso.com/widget/' -CustomMethod 'TEST'`

<span data-ttu-id="49955-216">Detta gör en `TEST` http-begäran till API: et.</span><span class="sxs-lookup"><span data-stu-id="49955-216">This makes a `TEST` HTTP request to the API.</span></span>

<span data-ttu-id="49955-217">Den här funktionen har lagts till i PowerShell-6.0.0.</span><span class="sxs-lookup"><span data-stu-id="49955-217">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="49955-218">-DisableKeepAlive</span><span class="sxs-lookup"><span data-stu-id="49955-218">-DisableKeepAlive</span></span>

<span data-ttu-id="49955-219">Anger att cmdleten anger **keepalive** -värdet i HTTP-huvudet till false.</span><span class="sxs-lookup"><span data-stu-id="49955-219">Indicates that the cmdlet sets the **KeepAlive** value in the HTTP header to False.</span></span> <span data-ttu-id="49955-220">**Keepalive** är som standard sant.</span><span class="sxs-lookup"><span data-stu-id="49955-220">By default, **KeepAlive** is True.</span></span> <span data-ttu-id="49955-221">**Keepalive** upprättar en permanent anslutning till servern för att under lätta efterföljande begär Anden.</span><span class="sxs-lookup"><span data-stu-id="49955-221">**KeepAlive** establishes a persistent connection to the server to facilitate subsequent requests.</span></span>

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

### <span data-ttu-id="49955-222">-FollowRelLink</span><span class="sxs-lookup"><span data-stu-id="49955-222">-FollowRelLink</span></span>

<span data-ttu-id="49955-223">Anger att cmdleten ska följa Relations länkar.</span><span class="sxs-lookup"><span data-stu-id="49955-223">Indicates the cmdlet should follow relation links.</span></span>

<span data-ttu-id="49955-224">Vissa REST API: er stöder sid brytning via Relations länkar per [RFC5988](https://tools.ietf.org/html/rfc5988#page-6).</span><span class="sxs-lookup"><span data-stu-id="49955-224">Some REST APIs support pagination via Relation Links per [RFC5988](https://tools.ietf.org/html/rfc5988#page-6).</span></span> <span data-ttu-id="49955-225">I stället för att parsa rubriken för att hämta URL: en för nästa sida kan du låta cmdlet: en göra detta åt dig.</span><span class="sxs-lookup"><span data-stu-id="49955-225">Instead of parsing the header to get the URL for the next page, you can have the cmdlet do this for you.</span></span> <span data-ttu-id="49955-226">Använd parametern **MaximumFollowRelLink** för att ange hur många gånger du vill följa Relations länkarna.</span><span class="sxs-lookup"><span data-stu-id="49955-226">To set how many times to follow relation links, use the **MaximumFollowRelLink** parameter.</span></span>

<span data-ttu-id="49955-227">När du använder den här växeln returnerar cmdleten en samling resultat sidor.</span><span class="sxs-lookup"><span data-stu-id="49955-227">When using this switch, the cmdlet returns a collection of pages of results.</span></span> <span data-ttu-id="49955-228">Varje sida med resultat kan innehålla flera resultat objekt.</span><span class="sxs-lookup"><span data-stu-id="49955-228">Each page of results may contain multiple result items.</span></span>

<span data-ttu-id="49955-229">Den här funktionen har lagts till i PowerShell-6.0.0.</span><span class="sxs-lookup"><span data-stu-id="49955-229">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="49955-230">-Form</span><span class="sxs-lookup"><span data-stu-id="49955-230">-Form</span></span>

<span data-ttu-id="49955-231">Konverterar en ord lista till ett `multipart/form-data` överförings objekt.</span><span class="sxs-lookup"><span data-stu-id="49955-231">Converts a dictionary to a `multipart/form-data` submission.</span></span> <span data-ttu-id="49955-232">**Formulär** får inte användas med **brödtext**.</span><span class="sxs-lookup"><span data-stu-id="49955-232">**Form** may not be used with **Body**.</span></span>
<span data-ttu-id="49955-233">Om **ContentType** ignoreras.</span><span class="sxs-lookup"><span data-stu-id="49955-233">If **ContentType** will be ignored.</span></span>

<span data-ttu-id="49955-234">Nycklarna i ord listan används som namn på formulär fält.</span><span class="sxs-lookup"><span data-stu-id="49955-234">The keys of the dictionary will be used as the form field names.</span></span> <span data-ttu-id="49955-235">Som standard kommer formulär värden att konverteras till sträng värden.</span><span class="sxs-lookup"><span data-stu-id="49955-235">By default, form values will be converted to string values.</span></span>

<span data-ttu-id="49955-236">Om värdet är ett **system. io. fileinfo** -objekt, kommer den binära fil innehållet att skickas.</span><span class="sxs-lookup"><span data-stu-id="49955-236">If the value is a **System.IO.FileInfo** object, then the binary file contents will be submitted.</span></span>
<span data-ttu-id="49955-237">Filens namn skickas som `filename` .</span><span class="sxs-lookup"><span data-stu-id="49955-237">The name of the file will be submitted as the `filename`.</span></span> <span data-ttu-id="49955-238">MIME kommer att anges som `application/octet-stream` .</span><span class="sxs-lookup"><span data-stu-id="49955-238">The MIME will be set as `application/octet-stream`.</span></span> <span data-ttu-id="49955-239">`Get-Item` kan användas för att förenkla tillhandahålla **system. io. fileinfo** -objektet.</span><span class="sxs-lookup"><span data-stu-id="49955-239">`Get-Item` can be used to simplify supplying the **System.IO.FileInfo** object.</span></span>

```powershell
$Form = @{
    resume = Get-Item 'c:\Users\jdoe\Documents\John Doe.pdf'
}
```

<span data-ttu-id="49955-240">Om värdet är en samlings typ, till exempel en matris eller lista skickas fältet for flera gånger.</span><span class="sxs-lookup"><span data-stu-id="49955-240">If the value is a collection type, such as an Array or List, the for field will be submitted multiple times.</span></span> <span data-ttu-id="49955-241">Värdena i listan kommer att behandlas som strängar som standard.</span><span class="sxs-lookup"><span data-stu-id="49955-241">The values of the list will be treated as strings by default.</span></span> <span data-ttu-id="49955-242">Om värdet är ett **system. io. fileinfo** -objekt, kommer den binära fil innehållet att skickas.</span><span class="sxs-lookup"><span data-stu-id="49955-242">If the value is a **System.IO.FileInfo** object, then the binary file contents will be submitted.</span></span> <span data-ttu-id="49955-243">Kapslade samlingar stöds inte.</span><span class="sxs-lookup"><span data-stu-id="49955-243">Nested collections aren't supported.</span></span>

```powershell
$Form = @{
    tags     = 'Vacation', 'Italy', '2017'
    pictures = Get-ChildItem 'c:\Users\jdoe\Pictures\2017-Italy\'
}
```

<span data-ttu-id="49955-244">I exemplet ovan anges `tags` fältet tre gånger i formuläret, en gång för varje `Vacation` , `Italy` och `2017` .</span><span class="sxs-lookup"><span data-stu-id="49955-244">In the above example, the `tags` field will be supplied three times in the form, once for each of `Vacation`, `Italy`, and `2017`.</span></span> <span data-ttu-id="49955-245">`pictures`Fältet kommer också att skickas en gång för varje fil i `2017-Italy` mappen.</span><span class="sxs-lookup"><span data-stu-id="49955-245">The `pictures` field will also be submitted once for each file in the `2017-Italy` folder.</span></span> <span data-ttu-id="49955-246">Det binära innehållet i filerna i mappen kommer att skickas som värden.</span><span class="sxs-lookup"><span data-stu-id="49955-246">The binary contents of the files in that folder will be submitted as the values.</span></span>

<span data-ttu-id="49955-247">Den här funktionen har lagts till i PowerShell-6.1.0.</span><span class="sxs-lookup"><span data-stu-id="49955-247">This feature was added in PowerShell 6.1.0.</span></span>

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

### <span data-ttu-id="49955-248">– Sidhuvud</span><span class="sxs-lookup"><span data-stu-id="49955-248">-Headers</span></span>

<span data-ttu-id="49955-249">Anger webb begärans rubriker.</span><span class="sxs-lookup"><span data-stu-id="49955-249">Specifies the headers of the web request.</span></span> <span data-ttu-id="49955-250">Ange en hash-tabell eller-ord lista.</span><span class="sxs-lookup"><span data-stu-id="49955-250">Enter a hash table or dictionary.</span></span>

<span data-ttu-id="49955-251">Om du vill ange UserAgent-rubriker använder du parametern **useragent** .</span><span class="sxs-lookup"><span data-stu-id="49955-251">To set UserAgent headers, use the **UserAgent** parameter.</span></span> <span data-ttu-id="49955-252">Du kan inte använda den här parametern för att ange `User-Agent` eller cookie-rubriker.</span><span class="sxs-lookup"><span data-stu-id="49955-252">You cannot use this parameter to specify `User-Agent` or cookie headers.</span></span>

<span data-ttu-id="49955-253">Content-relaterade rubriker, till exempel `Content-Type` kommer att åsidosättas när ett `MultipartFormDataContent` objekt anges för **brödtext**.</span><span class="sxs-lookup"><span data-stu-id="49955-253">Content related headers, such as `Content-Type` will be overridden when a `MultipartFormDataContent` object is supplied for **Body**.</span></span>

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

### <span data-ttu-id="49955-254">-INFILE</span><span class="sxs-lookup"><span data-stu-id="49955-254">-InFile</span></span>

<span data-ttu-id="49955-255">Hämtar innehållet i webb förfrågan från en fil.</span><span class="sxs-lookup"><span data-stu-id="49955-255">Gets the content of the web request from a file.</span></span>

<span data-ttu-id="49955-256">Ange en sökväg och ett fil namn.</span><span class="sxs-lookup"><span data-stu-id="49955-256">Enter a path and file name.</span></span> <span data-ttu-id="49955-257">Om du utelämnar sökvägen är standardvärdet den aktuella platsen.</span><span class="sxs-lookup"><span data-stu-id="49955-257">If you omit the path, the default is the current location.</span></span>

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

### <span data-ttu-id="49955-258">-MaximumFollowRelLink</span><span class="sxs-lookup"><span data-stu-id="49955-258">-MaximumFollowRelLink</span></span>

<span data-ttu-id="49955-259">Anger hur många gånger som Relations länkar ska följas om **FollowRelLink** används.</span><span class="sxs-lookup"><span data-stu-id="49955-259">Specifies how many times to follow relation links if **FollowRelLink** is used.</span></span> <span data-ttu-id="49955-260">Du kan behöva ett mindre värde om REST API-begränsningarna beror på för många begär Anden.</span><span class="sxs-lookup"><span data-stu-id="49955-260">A smaller value may be needed if the REST api throttles due to too many requests.</span></span> <span data-ttu-id="49955-261">Standardvärdet är `[Int32]::MaxValue`.</span><span class="sxs-lookup"><span data-stu-id="49955-261">The default value is `[Int32]::MaxValue`.</span></span> <span data-ttu-id="49955-262">Värdet 0 (noll) förhindrar följande Relations länkar.</span><span class="sxs-lookup"><span data-stu-id="49955-262">A value of 0 (zero) prevents following relation links.</span></span>

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

### <span data-ttu-id="49955-263">-MaximumRedirection</span><span class="sxs-lookup"><span data-stu-id="49955-263">-MaximumRedirection</span></span>

<span data-ttu-id="49955-264">Anger hur många gånger PowerShell omdirigerar en anslutning till en alternativ Uniform Resource Identifier (URI) innan anslutningen Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="49955-264">Specifies how many times PowerShell redirects a connection to an alternate Uniform Resource Identifier (URI) before the connection fails.</span></span> <span data-ttu-id="49955-265">Standardvärdet är 5.</span><span class="sxs-lookup"><span data-stu-id="49955-265">The default value is 5.</span></span> <span data-ttu-id="49955-266">Värdet 0 (noll) förhindrar all omdirigering.</span><span class="sxs-lookup"><span data-stu-id="49955-266">A value of 0 (zero) prevents all redirection.</span></span>

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

### <span data-ttu-id="49955-267">-MaximumRetryCount</span><span class="sxs-lookup"><span data-stu-id="49955-267">-MaximumRetryCount</span></span>

<span data-ttu-id="49955-268">Anger hur många gånger PowerShell försöker upprätta en anslutning när en felkod mellan 400 och 599, inklusive eller 304, tas emot.</span><span class="sxs-lookup"><span data-stu-id="49955-268">Specifies how many times PowerShell retries a connection when a failure code between 400 and 599, inclusive or 304 is received.</span></span> <span data-ttu-id="49955-269">Se även **RetryIntervalSec** -parametern för att ange antal återförsök.</span><span class="sxs-lookup"><span data-stu-id="49955-269">Also see **RetryIntervalSec** parameter for specifying number of retries.</span></span>

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

### <span data-ttu-id="49955-270">-Metod</span><span class="sxs-lookup"><span data-stu-id="49955-270">-Method</span></span>

<span data-ttu-id="49955-271">Anger den metod som används för webb förfrågan.</span><span class="sxs-lookup"><span data-stu-id="49955-271">Specifies the method used for the web request.</span></span> <span data-ttu-id="49955-272">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="49955-272">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="49955-273">Default</span><span class="sxs-lookup"><span data-stu-id="49955-273">Default</span></span>
- <span data-ttu-id="49955-274">Ta bort</span><span class="sxs-lookup"><span data-stu-id="49955-274">Delete</span></span>
- <span data-ttu-id="49955-275">Hämta</span><span class="sxs-lookup"><span data-stu-id="49955-275">Get</span></span>
- <span data-ttu-id="49955-276">Head</span><span class="sxs-lookup"><span data-stu-id="49955-276">Head</span></span>
- <span data-ttu-id="49955-277">Sammanfoga</span><span class="sxs-lookup"><span data-stu-id="49955-277">Merge</span></span>
- <span data-ttu-id="49955-278">Alternativ</span><span class="sxs-lookup"><span data-stu-id="49955-278">Options</span></span>
- <span data-ttu-id="49955-279">Patch</span><span class="sxs-lookup"><span data-stu-id="49955-279">Patch</span></span>
- <span data-ttu-id="49955-280">Skicka</span><span class="sxs-lookup"><span data-stu-id="49955-280">Post</span></span>
- <span data-ttu-id="49955-281">Placera</span><span class="sxs-lookup"><span data-stu-id="49955-281">Put</span></span>
- <span data-ttu-id="49955-282">Spårning</span><span class="sxs-lookup"><span data-stu-id="49955-282">Trace</span></span>

<span data-ttu-id="49955-283">**CustomMethod** -parametern kan användas för förfrågnings metoder som inte anges ovan.</span><span class="sxs-lookup"><span data-stu-id="49955-283">The **CustomMethod** parameter can be used for Request Methods not listed above.</span></span>

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

### <span data-ttu-id="49955-284">-Noproxy</span><span class="sxs-lookup"><span data-stu-id="49955-284">-NoProxy</span></span>

<span data-ttu-id="49955-285">Anger att cmdleten inte kommer att använda en proxy för att komma till målet.</span><span class="sxs-lookup"><span data-stu-id="49955-285">Indicates that the cmdlet will not use a proxy to reach the destination.</span></span>

<span data-ttu-id="49955-286">Använd den här växeln när du behöver kringgå proxyn som kon figurer ATS i Internet Explorer eller en proxyserver som anges i miljön.</span><span class="sxs-lookup"><span data-stu-id="49955-286">When you need to bypass the proxy configured in Internet Explorer, or a proxy specified in the environment, use this switch.</span></span>

<span data-ttu-id="49955-287">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="49955-287">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="49955-288">-Fil</span><span class="sxs-lookup"><span data-stu-id="49955-288">-OutFile</span></span>

<span data-ttu-id="49955-289">Sparar svars texten i den angivna utdatafilen.</span><span class="sxs-lookup"><span data-stu-id="49955-289">Saves the response body in the specified output file.</span></span> <span data-ttu-id="49955-290">Ange en sökväg och ett fil namn.</span><span class="sxs-lookup"><span data-stu-id="49955-290">Enter a path and file name.</span></span> <span data-ttu-id="49955-291">Om du utelämnar sökvägen är standardvärdet den aktuella platsen.</span><span class="sxs-lookup"><span data-stu-id="49955-291">If you omit the path, the default is the current location.</span></span>

<span data-ttu-id="49955-292">Som standard `Invoke-RestMethod` returnerar resultatet till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="49955-292">By default, `Invoke-RestMethod` returns the results to the pipeline.</span></span> <span data-ttu-id="49955-293">Om du vill skicka resultatet till en fil och till pipelinen använder du parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="49955-293">To send the results to a file and to the pipeline, use the **Passthru** parameter.</span></span>

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

### <span data-ttu-id="49955-294">– PassThru</span><span class="sxs-lookup"><span data-stu-id="49955-294">-PassThru</span></span>

<span data-ttu-id="49955-295">Returnerar resultaten, förutom att skriva dem till en fil.</span><span class="sxs-lookup"><span data-stu-id="49955-295">Returns the results, in addition to writing them to a file.</span></span> <span data-ttu-id="49955-296">Den här parametern är endast giltig om **parametern out** också används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="49955-296">This parameter is valid only when the **OutFile** parameter is also used in the command.</span></span>

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

### <span data-ttu-id="49955-297">-PreserveAuthorizationOnRedirect</span><span class="sxs-lookup"><span data-stu-id="49955-297">-PreserveAuthorizationOnRedirect</span></span>

<span data-ttu-id="49955-298">Anger att cmdleten ska bevara `Authorization` sidhuvudet, om det finns, över omdirigeringar.</span><span class="sxs-lookup"><span data-stu-id="49955-298">Indicates the cmdlet should preserve the `Authorization` header, when present, across redirections.</span></span>

<span data-ttu-id="49955-299">Som standard tar cmdleten bort `Authorization` sidhuvudet före omdirigeringen.</span><span class="sxs-lookup"><span data-stu-id="49955-299">By default, the cmdlet strips the `Authorization` header before redirecting.</span></span> <span data-ttu-id="49955-300">Om du anger den här parametern inaktive ras den här logiken för fall där huvudet måste skickas till omdirigerings platsen.</span><span class="sxs-lookup"><span data-stu-id="49955-300">Specifying this parameter disables this logic for cases where the header needs to be sent to the redirection location.</span></span>

<span data-ttu-id="49955-301">Den här funktionen har lagts till i PowerShell-6.0.0.</span><span class="sxs-lookup"><span data-stu-id="49955-301">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="49955-302">-Proxy</span><span class="sxs-lookup"><span data-stu-id="49955-302">-Proxy</span></span>

<span data-ttu-id="49955-303">Använder en proxyserver för begäran, i stället för att ansluta direkt till Internet resursen.</span><span class="sxs-lookup"><span data-stu-id="49955-303">Uses a proxy server for the request, rather than connecting directly to the internet resource.</span></span> <span data-ttu-id="49955-304">Ange Uniform Resource Identifier (URI) för en nätverks-proxyserver.</span><span class="sxs-lookup"><span data-stu-id="49955-304">Enter the Uniform Resource Identifier (URI) of a network proxy server.</span></span>

<span data-ttu-id="49955-305">Den här funktionen har lagts till i PowerShell-6.0.0.</span><span class="sxs-lookup"><span data-stu-id="49955-305">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="49955-306">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="49955-306">-ProxyCredential</span></span>

<span data-ttu-id="49955-307">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="49955-307">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span> <span data-ttu-id="49955-308">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="49955-308">The default is the current user.</span></span>

<span data-ttu-id="49955-309">Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , **User@Domain.Com** eller ange ett `PSCredential` objekt, till exempel en som genereras av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="49955-309">Type a user name, such as **User01** or **Domain01\User01** , **User@Domain.Com** , or enter a `PSCredential` object, such as one generated by the `Get-Credential` cmdlet.</span></span>

<span data-ttu-id="49955-310">Den här parametern är endast giltig när parametern **proxy** också används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="49955-310">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="49955-311">Du kan inte använda parametrarna **ProxyCredential** och **ProxyUseDefaultCredentials** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="49955-311">You can't use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="49955-312">-ProxyUseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="49955-312">-ProxyUseDefaultCredentials</span></span>

<span data-ttu-id="49955-313">Anger att cmdleten använder autentiseringsuppgifterna för den aktuella användaren för att få åtkomst till proxyservern som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="49955-313">Indicates that the cmdlet uses the credentials of the current user to access the proxy server that is specified by the **Proxy** parameter.</span></span>

<span data-ttu-id="49955-314">Den här parametern är endast giltig när parametern **proxy** också används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="49955-314">This parameter is valid only when the **Proxy** parameter is also used in the command.</span></span> <span data-ttu-id="49955-315">Du kan inte använda parametrarna **ProxyCredential** och **ProxyUseDefaultCredentials** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="49955-315">You can't use the **ProxyCredential** and **ProxyUseDefaultCredentials** parameters in the same command.</span></span>

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

### <span data-ttu-id="49955-316">-ResponseHeadersVariable</span><span class="sxs-lookup"><span data-stu-id="49955-316">-ResponseHeadersVariable</span></span>

<span data-ttu-id="49955-317">Skapar en ord lista för svars rubriker och sparar den i värdet för den angivna variabeln.</span><span class="sxs-lookup"><span data-stu-id="49955-317">Creates a Response Headers Dictionary and saves it in the value of the specified variable.</span></span> <span data-ttu-id="49955-318">Nycklarna i ord listan innehåller fält namnen för svars huvudet som returneras av webb servern och värdena är respektive fält värden.</span><span class="sxs-lookup"><span data-stu-id="49955-318">The keys of the dictionary will contain the field names of the Response Header returned by the web server and the values will be the respective field values.</span></span>

<span data-ttu-id="49955-319">Den här funktionen har lagts till i PowerShell-6.0.0.</span><span class="sxs-lookup"><span data-stu-id="49955-319">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="49955-320">-Återuppta</span><span class="sxs-lookup"><span data-stu-id="49955-320">-Resume</span></span>

<span data-ttu-id="49955-321">Utför ett bästa försök att återuppta hämtningen av en delvis fil.</span><span class="sxs-lookup"><span data-stu-id="49955-321">Performs a best effort attempt to resume downloading a partial file.</span></span> <span data-ttu-id="49955-322">Parametern **Resume** kräver parametern **DisFile** .</span><span class="sxs-lookup"><span data-stu-id="49955-322">The **Resume** parameter requires the **OutFile** parameter.</span></span>

<span data-ttu-id="49955-323">**Återuppta** fungerar bara på storleken på den lokala filen och fjärrfilen och utför ingen annan validering av att den lokala filen och fjärrfilen är desamma.</span><span class="sxs-lookup"><span data-stu-id="49955-323">**Resume** only operates on the size of the local file and remote file and performs no other validation that the local file and the remote file are the same.</span></span>

<span data-ttu-id="49955-324">Om den lokala fil storleken är mindre än fjärrfils storleken försöker cmdleten återuppta nedladdningen av filen och lägga till återstående byte i slutet av filen.</span><span class="sxs-lookup"><span data-stu-id="49955-324">If the local file size is smaller than the remote file size, then the cmdlet will attempt to resume downloading the file and append the remaining bytes to the end of the file.</span></span>

<span data-ttu-id="49955-325">Om den lokala fil storleken är samma som fjärrfilens storlek, utförs ingen åtgärd och cmdleten förutsätter att nedladdningen redan har slutförts.</span><span class="sxs-lookup"><span data-stu-id="49955-325">If the local file size is the same as the remote file size, then no action is taken and the cmdlet assumes the download already completed.</span></span>

<span data-ttu-id="49955-326">Om den lokala fil storleken är större än fjärrfilens storlek, kommer den lokala filen att skrivas över och hela fjärrfilen kommer att hämtas helt på nytt.</span><span class="sxs-lookup"><span data-stu-id="49955-326">If the local file size is larger than the remote file size, then the local file will be overwritten and the entire remote file will be completely re-downloaded.</span></span> <span data-ttu-id="49955-327">Detta är samma sak som att använda en **fil** utan att **återuppta**.</span><span class="sxs-lookup"><span data-stu-id="49955-327">This behavior is the same as using **OutFile** without **Resume**.</span></span>

<span data-ttu-id="49955-328">Om fjärrservern inte har stöd för hämtning återupptas kommer den lokala filen att skrivas över och hela fjärrfilen kommer att laddas ned på nytt.</span><span class="sxs-lookup"><span data-stu-id="49955-328">If the remote server does not support download resuming, then the local file will be overwritten and the entire remote file will be completely re-downloaded.</span></span> <span data-ttu-id="49955-329">Detta är samma sak som att använda en **fil** utan att **återuppta**.</span><span class="sxs-lookup"><span data-stu-id="49955-329">This behavior is the same as using **OutFile** without **Resume**.</span></span>

<span data-ttu-id="49955-330">Om den lokala filen inte finns kommer den lokala filen att skapas och hela fjärrfilen laddas ned helt.</span><span class="sxs-lookup"><span data-stu-id="49955-330">If the local file doesn't exist, then the local file will be created and the entire remote file will be completely downloaded.</span></span> <span data-ttu-id="49955-331">Detta är samma sak som att använda en **fil** utan att **återuppta**.</span><span class="sxs-lookup"><span data-stu-id="49955-331">This behavior is the same as using **OutFile** without **Resume**.</span></span>

<span data-ttu-id="49955-332">Den här funktionen har lagts till i PowerShell-6.1.0.</span><span class="sxs-lookup"><span data-stu-id="49955-332">This feature was added in PowerShell 6.1.0.</span></span>

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

### <span data-ttu-id="49955-333">-RetryIntervalSec</span><span class="sxs-lookup"><span data-stu-id="49955-333">-RetryIntervalSec</span></span>

<span data-ttu-id="49955-334">Anger intervallet mellan återförsök för anslutningen när en felkod mellan 400 och 599, inklusive eller 304 tas emot.</span><span class="sxs-lookup"><span data-stu-id="49955-334">Specifies the interval between retries for the connection when a failure code between 400 and 599, inclusive or 304 is received.</span></span> <span data-ttu-id="49955-335">Se även **MaximumRetryCount** -parametern för att ange antal återförsök.</span><span class="sxs-lookup"><span data-stu-id="49955-335">Also see **MaximumRetryCount** parameter for specifying number of retries.</span></span>

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

### <span data-ttu-id="49955-336">-SessionVariable</span><span class="sxs-lookup"><span data-stu-id="49955-336">-SessionVariable</span></span>

<span data-ttu-id="49955-337">Anger en variabel för vilken denna cmdlet skapar en Webbbegäran-session och sparar den i värdet.</span><span class="sxs-lookup"><span data-stu-id="49955-337">Specifies a variable for which this cmdlet creates a web request session and saves it in the value.</span></span>
<span data-ttu-id="49955-338">Ange ett variabel namn utan dollar tecknet ( `$` )-symbolen.</span><span class="sxs-lookup"><span data-stu-id="49955-338">Enter a variable name without the dollar sign (`$`) symbol.</span></span>

<span data-ttu-id="49955-339">När du anger en sessionsvariabel `Invoke-RestMethod` skapar ett sessionsobjekt för Webbbegäran och tilldelar det till en variabel med det angivna namnet i PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="49955-339">When you specify a session variable, `Invoke-RestMethod` creates a web request session object and assigns it to a variable with the specified name in your PowerShell session.</span></span> <span data-ttu-id="49955-340">Du kan använda variabeln i din session så snart kommandot har slutförts.</span><span class="sxs-lookup"><span data-stu-id="49955-340">You can use the variable in your session as soon as the command completes.</span></span>

<span data-ttu-id="49955-341">Till skillnad från en fjärran sluten session är inte Webbbegäran-sessionen en permanent anslutning.</span><span class="sxs-lookup"><span data-stu-id="49955-341">Unlike a remote session, the web request session isn't a persistent connection.</span></span> <span data-ttu-id="49955-342">Det är ett objekt som innehåller information om anslutningen och begäran, inklusive cookies, autentiseringsuppgifter, det maximala värdet för omdirigering och användar agent strängen.</span><span class="sxs-lookup"><span data-stu-id="49955-342">It's an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="49955-343">Du kan använda den för att dela tillstånd och data mellan webb förfrågningar.</span><span class="sxs-lookup"><span data-stu-id="49955-343">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="49955-344">Om du vill använda Webbbegäran-sessionen i efterföljande webb förfrågningar, anger du variabeln session i värdet för **websession** -parametern.</span><span class="sxs-lookup"><span data-stu-id="49955-344">To use the web request session in subsequent web requests, specify the session variable in the value of the **WebSession** parameter.</span></span> <span data-ttu-id="49955-345">PowerShell använder data i objektet Webbbegäran-session när den nya anslutningen upprättas.</span><span class="sxs-lookup"><span data-stu-id="49955-345">PowerShell uses the data in the web request session object when establishing the new connection.</span></span> <span data-ttu-id="49955-346">Om du vill åsidosätta ett värde i Webbbegäran-sessionen använder du en cmdlet-parameter, till exempel **useragent** eller **Credential**.</span><span class="sxs-lookup"><span data-stu-id="49955-346">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential**.</span></span> <span data-ttu-id="49955-347">Parameter värden har företräde framför värden i Webbbegäran-sessionen.</span><span class="sxs-lookup"><span data-stu-id="49955-347">Parameter values take precedence over values in the web request session.</span></span>

<span data-ttu-id="49955-348">Du kan inte använda parametrarna **SessionVariable** och **websession** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="49955-348">You can't use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

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

### <span data-ttu-id="49955-349">-SkipCertificateCheck</span><span class="sxs-lookup"><span data-stu-id="49955-349">-SkipCertificateCheck</span></span>

<span data-ttu-id="49955-350">Hoppar över verifierings kontroller för certifikat som innehåller alla verifieringar som förfallo datum, återkallande, betrodd rot utfärdare osv.</span><span class="sxs-lookup"><span data-stu-id="49955-350">Skips certificate validation checks that include all validations such as expiration, revocation, trusted root authority, etc.</span></span>

> [!WARNING]
> <span data-ttu-id="49955-351">Att använda den här parametern är inte säkert och rekommenderas inte.</span><span class="sxs-lookup"><span data-stu-id="49955-351">Using this parameter is not secure and is not recommended.</span></span> <span data-ttu-id="49955-352">Den här växeln är endast avsedd att användas mot kända värdar med hjälp av ett självsignerat certifikat i testnings syfte.</span><span class="sxs-lookup"><span data-stu-id="49955-352">This switch is only intended to be used against known hosts using a self-signed certificate for testing purposes.</span></span> <span data-ttu-id="49955-353">Använd på egen risk.</span><span class="sxs-lookup"><span data-stu-id="49955-353">Use at your own risk.</span></span>

<span data-ttu-id="49955-354">Den här funktionen har lagts till i PowerShell-6.0.0.</span><span class="sxs-lookup"><span data-stu-id="49955-354">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="49955-355">-SkipHeaderValidation</span><span class="sxs-lookup"><span data-stu-id="49955-355">-SkipHeaderValidation</span></span>

<span data-ttu-id="49955-356">Anger att cmdleten ska lägga till huvuden i begäran utan verifiering.</span><span class="sxs-lookup"><span data-stu-id="49955-356">Indicates the cmdlet should add headers to the request without validation.</span></span>

<span data-ttu-id="49955-357">Den här växeln bör användas för platser som kräver rubrik värden som inte uppfyller standarder.</span><span class="sxs-lookup"><span data-stu-id="49955-357">This switch should be used for sites that require header values that do not conform to standards.</span></span>
<span data-ttu-id="49955-358">Om du anger den här växeln inaktive ras verifieringen så att värdet inte kan skickas avmarkerat.</span><span class="sxs-lookup"><span data-stu-id="49955-358">Specifying this switch disables validation to allow the value to be passed unchecked.</span></span> <span data-ttu-id="49955-359">När det här värdet anges läggs alla rubriker till utan verifiering.</span><span class="sxs-lookup"><span data-stu-id="49955-359">When specified, all headers are added without validation.</span></span>

<span data-ttu-id="49955-360">Då inaktive ras verifieringen för värden som skickas till parametrarna **ContentType** , **headers** och **useragent** .</span><span class="sxs-lookup"><span data-stu-id="49955-360">This will disable validation for values passed to the **ContentType** , **Headers** , and **UserAgent** parameters.</span></span>

<span data-ttu-id="49955-361">Den här funktionen har lagts till i PowerShell-6.0.0.</span><span class="sxs-lookup"><span data-stu-id="49955-361">This feature was added in PowerShell 6.0.0.</span></span>

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

### <span data-ttu-id="49955-362">-SslProtocol</span><span class="sxs-lookup"><span data-stu-id="49955-362">-SslProtocol</span></span>

<span data-ttu-id="49955-363">Anger de SSL/TLS-protokoll som är tillåtna för webbegäran.</span><span class="sxs-lookup"><span data-stu-id="49955-363">Sets the SSL/TLS protocols that are permissible for the web request.</span></span> <span data-ttu-id="49955-364">Som standard är alla SSL/TLS-protokoll som stöds av systemet tillåtna.</span><span class="sxs-lookup"><span data-stu-id="49955-364">By default all, SSL/TLS protocols supported by the system are allowed.</span></span> <span data-ttu-id="49955-365">**SslProtocol** gör det möjligt att begränsa till vissa protokoll för efterlevnad.</span><span class="sxs-lookup"><span data-stu-id="49955-365">**SslProtocol** allows for limiting to specific protocols for compliance purposes.</span></span>

<span data-ttu-id="49955-366">**SslProtocol** använder `WebSslProtocol` flaggan Enum.</span><span class="sxs-lookup"><span data-stu-id="49955-366">**SslProtocol** uses the `WebSslProtocol` Flag Enum.</span></span> <span data-ttu-id="49955-367">Det går att ange mer än ett protokoll med hjälp av flagg notation eller kombinera flera `WebSslProtocol` alternativ med `-bor` , men det finns inte stöd för att tillhandahålla flera protokoll på alla plattformar.</span><span class="sxs-lookup"><span data-stu-id="49955-367">It is possible to supply more than one protocol using flag notation or combining multiple `WebSslProtocol` options with `-bor`, however supplying multiple protocols is not supported on all platforms.</span></span>

> [!NOTE]
> <span data-ttu-id="49955-368">På andra plattformar än Windows-plattformar kanske det inte går att ange `'Tls, Tls12'` som ett alternativ.</span><span class="sxs-lookup"><span data-stu-id="49955-368">On non-Windows platforms it may not be possible to supply `'Tls, Tls12'` as an option.</span></span>

<span data-ttu-id="49955-369">Den här funktionen har lagts till i PowerShell-6.0.0.</span><span class="sxs-lookup"><span data-stu-id="49955-369">This feature was added in PowerShell 6.0.0.</span></span>

```yaml
Type: WebSslProtocol
Parameter Sets: (All)
Aliases:
Accepted values: Default, Tls, Tls11, Tls12

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="49955-370">-TimeoutSec</span><span class="sxs-lookup"><span data-stu-id="49955-370">-TimeoutSec</span></span>

<span data-ttu-id="49955-371">Anger hur lång tid det tar att vänta på begäran innan den går ut. Ange ett värde i sekunder.</span><span class="sxs-lookup"><span data-stu-id="49955-371">Specifies how long the request can be pending before it times out. Enter a value in seconds.</span></span> <span data-ttu-id="49955-372">Standardvärdet 0 anger en obestämd tids gräns.</span><span class="sxs-lookup"><span data-stu-id="49955-372">The default value, 0, specifies an indefinite time-out.</span></span>

<span data-ttu-id="49955-373">En Domain Name System-fråga (DNS) kan ta upp till 15 sekunder att returnera eller ta slut för lång tid. Om din begäran innehåller ett värdnamn som kräver lösning och du anger **TimeoutSec** till ett värde som är större än noll, men mindre än 15 sekunder, kan det ta 15 sekunder eller mer innan en WebException utlöses, och tids gränsen för din begäran görs.</span><span class="sxs-lookup"><span data-stu-id="49955-373">A Domain Name System (DNS) query can take up to 15 seconds to return or time out. If your request contains a host name that requires resolution, and you set **TimeoutSec** to a value greater than zero, but less than 15 seconds, it can take 15 seconds or more before a WebException is thrown, and your request times out.</span></span>

```yaml
Type: Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="49955-374">-Token</span><span class="sxs-lookup"><span data-stu-id="49955-374">-Token</span></span>

<span data-ttu-id="49955-375">OAuth-eller Bearer-token som ska ingå i begäran.</span><span class="sxs-lookup"><span data-stu-id="49955-375">The OAuth or Bearer token to include in the request.</span></span> <span data-ttu-id="49955-376">**Token** krävs av vissa **autentiseringsalternativ** .</span><span class="sxs-lookup"><span data-stu-id="49955-376">**Token** is required by certain **Authentication** options.</span></span> <span data-ttu-id="49955-377">Den kan inte användas separat.</span><span class="sxs-lookup"><span data-stu-id="49955-377">It can't be used independently.</span></span>

<span data-ttu-id="49955-378">**Token** tar en `SecureString` som innehåller token.</span><span class="sxs-lookup"><span data-stu-id="49955-378">**Token** takes a `SecureString` that contains the token.</span></span> <span data-ttu-id="49955-379">Använd följande för att ange token:</span><span class="sxs-lookup"><span data-stu-id="49955-379">To supply the token, manually use the following:</span></span>

`Invoke-RestMethod -Uri $uri -Authentication OAuth -Token (Read-Host -AsSecureString)`

<span data-ttu-id="49955-380">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="49955-380">This parameter was introduced in PowerShell 6.0.</span></span>

```yaml
Type: SecureString
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="49955-381">-TransferEncoding</span><span class="sxs-lookup"><span data-stu-id="49955-381">-TransferEncoding</span></span>

<span data-ttu-id="49955-382">Anger ett värde för HTTP-svarshuvuden för överförings kodning.</span><span class="sxs-lookup"><span data-stu-id="49955-382">Specifies a value for the transfer-encoding HTTP response header.</span></span> <span data-ttu-id="49955-383">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="49955-383">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="49955-384">Segment vis</span><span class="sxs-lookup"><span data-stu-id="49955-384">Chunked</span></span>
- <span data-ttu-id="49955-385">Compress</span><span class="sxs-lookup"><span data-stu-id="49955-385">Compress</span></span>
- <span data-ttu-id="49955-386">DEFLATE</span><span class="sxs-lookup"><span data-stu-id="49955-386">Deflate</span></span>
- <span data-ttu-id="49955-387">GZip</span><span class="sxs-lookup"><span data-stu-id="49955-387">GZip</span></span>
- <span data-ttu-id="49955-388">Identitet</span><span class="sxs-lookup"><span data-stu-id="49955-388">Identity</span></span>

```yaml
Type: String
Parameter Sets: (All)
Aliases:
Accepted values: chunked, compress, deflate, gzip, identity

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="49955-389">-URI</span><span class="sxs-lookup"><span data-stu-id="49955-389">-Uri</span></span>

<span data-ttu-id="49955-390">Anger Uniform Resource Identifier (URI) för den Internet resurs som webb förfrågan skickas till.</span><span class="sxs-lookup"><span data-stu-id="49955-390">Specifies the Uniform Resource Identifier (URI) of the internet resource to which the web request is sent.</span></span> <span data-ttu-id="49955-391">Den här parametern stöder HTTP-, HTTPS-, FTP-och fil värden.</span><span class="sxs-lookup"><span data-stu-id="49955-391">This parameter supports HTTP, HTTPS, FTP, and FILE values.</span></span>

<span data-ttu-id="49955-392">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="49955-392">This parameter is required.</span></span> <span data-ttu-id="49955-393">Parameter namnet ( **URI** ) är valfritt.</span><span class="sxs-lookup"><span data-stu-id="49955-393">The parameter name ( **Uri** ) is optional.</span></span>

```yaml
Type: Uri
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="49955-394">-UseBasicParsing</span><span class="sxs-lookup"><span data-stu-id="49955-394">-UseBasicParsing</span></span>

<span data-ttu-id="49955-395">Den här parametern är föråldrad.</span><span class="sxs-lookup"><span data-stu-id="49955-395">This parameter has been deprecated.</span></span> <span data-ttu-id="49955-396">Från och med PowerShell-6.0.0 använder alla webbegäranden enbart grundläggande parsning.</span><span class="sxs-lookup"><span data-stu-id="49955-396">Beginning with PowerShell 6.0.0, all Web requests use basic parsing only.</span></span> <span data-ttu-id="49955-397">Den här parametern ingår endast för bakåtkompatibilitet och all användning av den kommer inte att påverka cmdletens funktion.</span><span class="sxs-lookup"><span data-stu-id="49955-397">This parameter is included for backwards compatibility only and any use of it will have no effect on the operation of the cmdlet.</span></span>

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="49955-398">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="49955-398">-UseDefaultCredentials</span></span>

<span data-ttu-id="49955-399">Anger att cmdleten använder autentiseringsuppgifterna för den aktuella användaren för att skicka webb förfrågan.</span><span class="sxs-lookup"><span data-stu-id="49955-399">Indicates that the cmdlet uses the credentials of the current user to send the web request.</span></span> <span data-ttu-id="49955-400">Detta kan inte användas med **autentisering** eller **autentiseringsuppgifter** och stöds inte på alla plattformar.</span><span class="sxs-lookup"><span data-stu-id="49955-400">This can't be used with **Authentication** or **Credential** and may not be supported on all platforms.</span></span>

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="49955-401">– UserAgent</span><span class="sxs-lookup"><span data-stu-id="49955-401">-UserAgent</span></span>

<span data-ttu-id="49955-402">Anger en användar agent sträng för webb förfrågan.</span><span class="sxs-lookup"><span data-stu-id="49955-402">Specifies a user agent string for the web request.</span></span>

<span data-ttu-id="49955-403">Standard användar agenten liknar `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` med små variationer för varje operativ system och plattform.</span><span class="sxs-lookup"><span data-stu-id="49955-403">The default user agent is similar to `Mozilla/5.0 (Windows NT 10.0; Microsoft Windows 10.0.15063; en-US) PowerShell/6.0.0` with slight variations for each operating system and platform.</span></span>

<span data-ttu-id="49955-404">Om du vill testa en webbplats med den standard användar agent sträng som används av de flesta webbläsare, använder du egenskaperna för [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) -klassen, till exempel Chrome, Firefox, InternetExplorer, Opera och Safari.</span><span class="sxs-lookup"><span data-stu-id="49955-404">To test a website with the standard user agent string that is used by most internet browsers, use the properties of the [PSUserAgent](/dotnet/api/microsoft.powershell.commands.psuseragent) class, such as Chrome, FireFox, InternetExplorer, Opera, and Safari.</span></span>

```yaml
Type: String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="49955-405">– Websession</span><span class="sxs-lookup"><span data-stu-id="49955-405">-WebSession</span></span>

<span data-ttu-id="49955-406">Anger en Webbbegäran-session.</span><span class="sxs-lookup"><span data-stu-id="49955-406">Specifies a web request session.</span></span> <span data-ttu-id="49955-407">Ange variabel namnet, inklusive dollar tecknet ( `$` ).</span><span class="sxs-lookup"><span data-stu-id="49955-407">Enter the variable name, including the dollar sign (`$`).</span></span>

<span data-ttu-id="49955-408">Om du vill åsidosätta ett värde i Webbbegäran-sessionen använder du en cmdlet-parameter, till exempel **useragent** eller **Credential**.</span><span class="sxs-lookup"><span data-stu-id="49955-408">To override a value in the web request session, use a cmdlet parameter, such as **UserAgent** or **Credential**.</span></span> <span data-ttu-id="49955-409">Parameter värden har företräde framför värden i Webbbegäran-sessionen.</span><span class="sxs-lookup"><span data-stu-id="49955-409">Parameter values take precedence over values in the web request session.</span></span> <span data-ttu-id="49955-410">Content-relaterade rubriker, till exempel `Content-Type` , kommer också att åsidosättas när ett **MultipartFormDataContent** -objekt anges för **brödtext**.</span><span class="sxs-lookup"><span data-stu-id="49955-410">Content related headers, such as `Content-Type`, will be also be overridden when a **MultipartFormDataContent** object is supplied for **Body**.</span></span>

<span data-ttu-id="49955-411">Till skillnad från en fjärran sluten session är inte Webbbegäran-sessionen en permanent anslutning.</span><span class="sxs-lookup"><span data-stu-id="49955-411">Unlike a remote session, the web request session isn't a persistent connection.</span></span> <span data-ttu-id="49955-412">Det är ett objekt som innehåller information om anslutningen och begäran, inklusive cookies, autentiseringsuppgifter, det maximala värdet för omdirigering och användar agent strängen.</span><span class="sxs-lookup"><span data-stu-id="49955-412">It's an object that contains information about the connection and the request, including cookies, credentials, the maximum redirection value, and the user agent string.</span></span> <span data-ttu-id="49955-413">Du kan använda den för att dela tillstånd och data mellan webb förfrågningar.</span><span class="sxs-lookup"><span data-stu-id="49955-413">You can use it to share state and data among web requests.</span></span>

<span data-ttu-id="49955-414">Om du vill skapa en Webbbegäran-session anger du ett variabel namn, utan dollar tecken, i värdet för parametern **SessionVariable** för ett `Invoke-RestMethod` kommando.</span><span class="sxs-lookup"><span data-stu-id="49955-414">To create a web request session, enter a variable name, without a dollar sign, in the value of the **SessionVariable** parameter of an `Invoke-RestMethod` command.</span></span> <span data-ttu-id="49955-415">`Invoke-RestMethod` skapar sessionen och sparar den i variabeln.</span><span class="sxs-lookup"><span data-stu-id="49955-415">`Invoke-RestMethod` creates the session and saves it in the variable.</span></span> <span data-ttu-id="49955-416">I efterföljande kommandon använder du variabeln som värde för **websession** -parametern.</span><span class="sxs-lookup"><span data-stu-id="49955-416">In subsequent commands, use the variable as the value of the **WebSession** parameter.</span></span>

<span data-ttu-id="49955-417">Du kan inte använda parametrarna **SessionVariable** och **websession** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="49955-417">You can't use the **SessionVariable** and **WebSession** parameters in the same command.</span></span>

```yaml
Type: WebRequestSession
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="49955-418">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="49955-418">CommonParameters</span></span>

<span data-ttu-id="49955-419">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="49955-419">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="49955-420">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="49955-420">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="49955-421">INDATA</span><span class="sxs-lookup"><span data-stu-id="49955-421">INPUTS</span></span>

### <span data-ttu-id="49955-422">System. Object</span><span class="sxs-lookup"><span data-stu-id="49955-422">System.Object</span></span>

<span data-ttu-id="49955-423">Du kan skicka vidare innehållet i en webb förfrågan till `Invoke-RestMethod` .</span><span class="sxs-lookup"><span data-stu-id="49955-423">You can pipe the body of a web request to `Invoke-RestMethod`.</span></span>

## <span data-ttu-id="49955-424">UTDATA</span><span class="sxs-lookup"><span data-stu-id="49955-424">OUTPUTS</span></span>

### <span data-ttu-id="49955-425">System. Int64, system. String, System.Xml.Xmldokument</span><span class="sxs-lookup"><span data-stu-id="49955-425">System.Int64, System.String, System.Xml.XmlDocument</span></span>

<span data-ttu-id="49955-426">Utdata från cmdleten beror på formatet på det innehåll som hämtas.</span><span class="sxs-lookup"><span data-stu-id="49955-426">The output of the cmdlet depends upon the format of the content that is retrieved.</span></span>

### <span data-ttu-id="49955-427">PSObject</span><span class="sxs-lookup"><span data-stu-id="49955-427">PSObject</span></span>

<span data-ttu-id="49955-428">Om begäran returnerar JSON-strängar `Invoke-RestMethod` returnerar en **PSObject** som representerar strängarna.</span><span class="sxs-lookup"><span data-stu-id="49955-428">If the request returns JSON strings, `Invoke-RestMethod` returns a **PSObject** that represents the strings.</span></span>

## <span data-ttu-id="49955-429">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="49955-429">NOTES</span></span>

<span data-ttu-id="49955-430">Vissa funktioner kanske inte är tillgängliga på alla plattformar.</span><span class="sxs-lookup"><span data-stu-id="49955-430">Some features may not be available on all platforms.</span></span>

<span data-ttu-id="49955-431">Mer information om hur .NET tillhandahåller Proxy-tjänster till PowerShell finns i [komma åt Internet via en proxyserver](/dotnet/framework/network-programming/accessing-the-internet-through-a-proxy).</span><span class="sxs-lookup"><span data-stu-id="49955-431">For more information about how .NET provides proxy services to PowerShell, see [Accessing the Internet Through a Proxy](/dotnet/framework/network-programming/accessing-the-internet-through-a-proxy).</span></span>

## <span data-ttu-id="49955-432">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="49955-432">RELATED LINKS</span></span>

[<span data-ttu-id="49955-433">ConvertTo-Json</span><span class="sxs-lookup"><span data-stu-id="49955-433">ConvertTo-Json</span></span>](ConvertTo-Json.md)

[<span data-ttu-id="49955-434">ConvertFrom – JSON</span><span class="sxs-lookup"><span data-stu-id="49955-434">ConvertFrom-Json</span></span>](ConvertFrom-Json.md)

[<span data-ttu-id="49955-435">Anropa-webbegäran</span><span class="sxs-lookup"><span data-stu-id="49955-435">Invoke-WebRequest</span></span>](Invoke-WebRequest.md)
