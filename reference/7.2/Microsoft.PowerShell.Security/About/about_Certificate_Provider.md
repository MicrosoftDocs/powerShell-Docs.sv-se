---
description: Certifikat
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/about/about_certificate_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Certifikat leverantör
ms.openlocfilehash: 78536024e8e953a70485a7d950b187ba9a3fc405
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709895"
---
# <a name="certificate-provider"></a><span data-ttu-id="1c66d-103">Certifikat leverantör</span><span class="sxs-lookup"><span data-stu-id="1c66d-103">Certificate Provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="1c66d-104">Providernamn</span><span class="sxs-lookup"><span data-stu-id="1c66d-104">Provider name</span></span>

<span data-ttu-id="1c66d-105">Certifikat</span><span class="sxs-lookup"><span data-stu-id="1c66d-105">Certificate</span></span>

## <a name="drives"></a><span data-ttu-id="1c66d-106">Enheter</span><span class="sxs-lookup"><span data-stu-id="1c66d-106">Drives</span></span>

`Cert:`

## <a name="capabilities"></a><span data-ttu-id="1c66d-107">Funktioner</span><span class="sxs-lookup"><span data-stu-id="1c66d-107">Capabilities</span></span>

<span data-ttu-id="1c66d-108">**ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="1c66d-108">**ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="1c66d-109">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="1c66d-109">Short description</span></span>

<span data-ttu-id="1c66d-110">Ger åtkomst till certifikat Arkiv för X. 509 och certifikat i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1c66d-110">Provides access to X.509 certificate stores and certificates in PowerShell.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="1c66d-111">Detaljerad beskrivning</span><span class="sxs-lookup"><span data-stu-id="1c66d-111">Detailed description</span></span>

<span data-ttu-id="1c66d-112">Med PowerShell- **certifikatets** Provider kan du hämta, lägga till, ändra, rensa och ta bort certifikat och certifikat Arkiv i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1c66d-112">The PowerShell **Certificate** provider lets you get, add, change, clear, and delete certificates and certificate stores in PowerShell.</span></span>

<span data-ttu-id="1c66d-113">**Certifikat** enheten är ett hierarkiskt namn område som innehåller certifikat arkiven och certifikaten på din dator.</span><span class="sxs-lookup"><span data-stu-id="1c66d-113">The **Certificate** drive is a hierarchical namespace containing the certificate stores and certificates on your computer.</span></span>

<span data-ttu-id="1c66d-114">**Certifikat** leverantören stöder följande cmdletar, som beskrivs i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="1c66d-114">The **Certificate** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="1c66d-115">Get-location</span><span class="sxs-lookup"><span data-stu-id="1c66d-115">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="1c66d-116">Ange plats</span><span class="sxs-lookup"><span data-stu-id="1c66d-116">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="1c66d-117">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="1c66d-117">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="1c66d-118">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="1c66d-118">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [<span data-ttu-id="1c66d-119">Anropa-objekt</span><span class="sxs-lookup"><span data-stu-id="1c66d-119">Invoke-Item</span></span>](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [<span data-ttu-id="1c66d-120">Flytta objekt</span><span class="sxs-lookup"><span data-stu-id="1c66d-120">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="1c66d-121">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="1c66d-121">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="1c66d-122">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="1c66d-122">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="1c66d-123">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="1c66d-123">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="1c66d-124">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="1c66d-124">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [<span data-ttu-id="1c66d-125">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="1c66d-125">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [<span data-ttu-id="1c66d-126">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="1c66d-126">Get-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)
- [<span data-ttu-id="1c66d-127">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="1c66d-127">Set-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="1c66d-128">Typer som exponeras av denna provider</span><span class="sxs-lookup"><span data-stu-id="1c66d-128">Types exposed by this provider</span></span>

<span data-ttu-id="1c66d-129">Certifikat enheten exponerar följande typer.</span><span class="sxs-lookup"><span data-stu-id="1c66d-129">The Certificate drive exposes the following types.</span></span>

- <span data-ttu-id="1c66d-130">Lagra platser (Microsoft. PowerShell. commands. X509StoreLocation), som är behållare på hög nivå som grupperar certifikaten för den aktuella användaren och för alla användare.</span><span class="sxs-lookup"><span data-stu-id="1c66d-130">Store locations (Microsoft.PowerShell.Commands.X509StoreLocation), which are high-level containers that group the certificates for the current user and for all users.</span></span> <span data-ttu-id="1c66d-131">Varje system har en CurrentUser-och LocalMachine-lagringsplats (alla användare).</span><span class="sxs-lookup"><span data-stu-id="1c66d-131">Each system has a CurrentUser and LocalMachine (all users) store location.</span></span>

- <span data-ttu-id="1c66d-132">Certifikat arkiv (system. Security. Cryptography. X509Certificates. X509Store), som är fysiska butiker där certifikat sparas och hanteras.</span><span class="sxs-lookup"><span data-stu-id="1c66d-132">Certificates stores (System.Security.Cryptography.X509Certificates.X509Store), which are physical stores in which certificates are saved and managed.</span></span>

- <span data-ttu-id="1c66d-133">X. 509 **system. Security. Cryptography. X509Certificates. X509Certificate2** -certifikat, som representerar ett X. 509-certifikat på datorn.</span><span class="sxs-lookup"><span data-stu-id="1c66d-133">X.509 **System.Security.Cryptography.X509Certificates.X509Certificate2** certificates, each of which represent an X.509 certificate on the computer.</span></span>
  <span data-ttu-id="1c66d-134">Certifikat identifieras av deras tumavtrycken.</span><span class="sxs-lookup"><span data-stu-id="1c66d-134">Certificates are identified by their thumbprints.</span></span>

## <a name="navigating-the-certificate-drive"></a><span data-ttu-id="1c66d-135">Navigera i certifikat enheten</span><span class="sxs-lookup"><span data-stu-id="1c66d-135">Navigating the Certificate drive</span></span>

<span data-ttu-id="1c66d-136">**Certifikat** leverantören visar certifikat namn området som `Cert:` enheten i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1c66d-136">The **Certificate** provider exposes the certificate namespace as the `Cert:` drive in PowerShell.</span></span> <span data-ttu-id="1c66d-137">Det här kommandot använder `Set-Location` kommandot för att ändra den aktuella platsen till rot certifikat arkivet på LocalMachine Arkiv plats.</span><span class="sxs-lookup"><span data-stu-id="1c66d-137">This command uses the `Set-Location` command to change the current location to the Root certificate store in the LocalMachine store location.</span></span> <span data-ttu-id="1c66d-138">Använd ett omvänt snedstreck ( \\ ) eller ett snedstreck (/) för att ange `Cert:` enhetens nivå.</span><span class="sxs-lookup"><span data-stu-id="1c66d-138">Use a backslash (\\) or a forward slash (/) to indicate a level of the `Cert:` drive.</span></span>

```powershell
Set-Location Cert:
```

<span data-ttu-id="1c66d-139">Du kan också arbeta med certifikat leverantören från någon annan PowerShell-enhet.</span><span class="sxs-lookup"><span data-stu-id="1c66d-139">You can also work with the certificate provider from any other PowerShell drive.</span></span> <span data-ttu-id="1c66d-140">Om du vill referera till ett alias från en annan plats använder du `Cert:` enhets namnet i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="1c66d-140">To reference an alias from another location, use the `Cert:` drive name in the path.</span></span>

```powershell
PS Cert:\> Set-Location -Path LocalMachine\Root
```

<span data-ttu-id="1c66d-141">Om du vill återgå till en fil systemen het skriver du enhetens namn.</span><span class="sxs-lookup"><span data-stu-id="1c66d-141">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="1c66d-142">Skriv till exempel:</span><span class="sxs-lookup"><span data-stu-id="1c66d-142">For example, type:</span></span>

```powershell
Set-Location C:
```

> [!NOTE]
> <span data-ttu-id="1c66d-143">PowerShell använder alias för att ge dig ett välbekant sätt att arbeta med providerns sökvägar.</span><span class="sxs-lookup"><span data-stu-id="1c66d-143">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="1c66d-144">Kommandon som `dir` och `ls` är nu alias för [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` är ett alias för [set-location](xref:Microsoft.PowerShell.Management.Set-Location).</span><span class="sxs-lookup"><span data-stu-id="1c66d-144">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span>
> <span data-ttu-id="1c66d-145">och `pwd` är ett alias för [Get-location](xref:Microsoft.PowerShell.Management.Get-Location).</span><span class="sxs-lookup"><span data-stu-id="1c66d-145">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

## <a name="displaying-the-contents-of-the-cert-drive"></a><span data-ttu-id="1c66d-146">Visar innehållet i certifikatet: enhet</span><span class="sxs-lookup"><span data-stu-id="1c66d-146">Displaying the Contents of the Cert: drive</span></span>

<span data-ttu-id="1c66d-147">Detta kommando använder `Get-ChildItem` cmdleten för att Visa certifikat arkiven på CurrentUser-certifikatets lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="1c66d-147">This command uses the `Get-ChildItem` cmdlet to display the certificate stores in the CurrentUser certificate store location.</span></span>

<span data-ttu-id="1c66d-148">Om du inte är i `Cert:` enheten använder du en absolut sökväg.</span><span class="sxs-lookup"><span data-stu-id="1c66d-148">If you are not in the `Cert:` drive, use an absolute path.</span></span>

```powershell
PS Cert:\CurrentUser\> Get-ChildItem
```

### <a name="displaying-certificate-properties-within-the-cert-drive"></a><span data-ttu-id="1c66d-149">Visar certifikat egenskaper inom certifikatet: enhet</span><span class="sxs-lookup"><span data-stu-id="1c66d-149">Displaying certificate properties within the Cert: drive</span></span>

<span data-ttu-id="1c66d-150">Det här exemplet hämtar ett certifikat med `Get-Item` och lagrar det i en variabel.</span><span class="sxs-lookup"><span data-stu-id="1c66d-150">This example gets a certificate with `Get-Item` and stores it in a variable.</span></span>
<span data-ttu-id="1c66d-151">Exemplet visar de nya certifikat skript egenskaperna (**DnsNameList**, **EnhancedKeyUsageList**, **SendAsTrustedIssuer**) med `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="1c66d-151">The example shows the new certificate script properties (**DnsNameList**, **EnhancedKeyUsageList**, **SendAsTrustedIssuer**) using `Select-Object`.</span></span>

```powershell
$c = Get-Item cert:\LocalMachine\My\52A149D0393CE8A8D4AF0B172ED667A9E3A1F44E
$c | Format-List DnsNameList, EnhancedKeyUsageList, SendAsTrustedIssuer
```

```output
DnsNameList          : {SERVER01.contoso.com}
EnhancedKeyUsageList : {WiFi-Machine (1.3.6.1.4.1.311.42.2.6),
                       Client Authentication (1.3.6.1.5.5.7.3.2)}
SendAsTrustedIssuer  : False
```

### <a name="find-all-codesigning-certificates"></a><span data-ttu-id="1c66d-152">Hitta alla samdesignande certifikat</span><span class="sxs-lookup"><span data-stu-id="1c66d-152">Find all CodeSigning certificates</span></span>

<span data-ttu-id="1c66d-153">Detta kommando använder parametrarna **CodeSigningCert** och **rekursivt** för `Get-ChildItem` cmdleten för att hämta alla certifikat på datorn som har kod signerings auktoritet.</span><span class="sxs-lookup"><span data-stu-id="1c66d-153">This command uses the **CodeSigningCert** and **Recurse** parameters of the `Get-ChildItem` cmdlet to get all of the certificates on the computer that have code-signing authority.</span></span>

```powershell
Get-ChildItem -Path cert: -CodeSigningCert -Recurse
```

### <a name="find-expired-certificates"></a><span data-ttu-id="1c66d-154">Hitta utgångna certifikat</span><span class="sxs-lookup"><span data-stu-id="1c66d-154">Find expired certificates</span></span>

<span data-ttu-id="1c66d-155">Det här kommandot använder **ExpiringInDays** -parametern för `Get-ChildItem` cmdleten för att hämta certifikat som upphör att gälla inom de närmaste 30 dagarna.</span><span class="sxs-lookup"><span data-stu-id="1c66d-155">This command uses the **ExpiringInDays** parameter of the `Get-ChildItem` cmdlet to get certificates that will expire within the next 30 days.</span></span>

```powershell
Get-ChildItem -Path cert:\LocalMachine\WebHosting -ExpiringInDays 30
```

### <a name="find-server-ssl-certificates"></a><span data-ttu-id="1c66d-156">Hitta Server SSL-certifikat</span><span class="sxs-lookup"><span data-stu-id="1c66d-156">Find Server SSL Certificates</span></span>

<span data-ttu-id="1c66d-157">Det här kommandot använder **SSLServerAuthentication** -parametern för `Get-ChildItem` cmdleten för att hämta alla Server-SSL-certifikat i butikerna My och webvärding.</span><span class="sxs-lookup"><span data-stu-id="1c66d-157">This command uses the **SSLServerAuthentication** parameter of the `Get-ChildItem` cmdlet to get all Server SSL Certificates in the My and WebHosting stores.</span></span>

```powershell
Get-ChildItem -Path cert:\LocalMachine\My, cert:\LocalMachine\WebHosting `
  -SSLServerAuthentication
```

### <a name="find-expired-certificates-on-remote-computers"></a><span data-ttu-id="1c66d-158">Hitta utgångna certifikat på fjärrdatorer</span><span class="sxs-lookup"><span data-stu-id="1c66d-158">Find expired certificates on remote computers</span></span>

<span data-ttu-id="1c66d-159">Det här kommandot använder `Invoke-Command` cmdleten för att köra ett `Get-ChildItem` kommando på datorerna SRV01 och Srv02.</span><span class="sxs-lookup"><span data-stu-id="1c66d-159">This command uses the `Invoke-Command` cmdlet to run a `Get-ChildItem` command on the Srv01 and Srv02 computers.</span></span> <span data-ttu-id="1c66d-160">Värdet noll (0) i parametern **ExpiringInDays** hämtar certifikat på de SRV01-och Srv02-datorer som har upphört att gälla.</span><span class="sxs-lookup"><span data-stu-id="1c66d-160">A value of zero (0) in the **ExpiringInDays** parameter gets certificates on the Srv01 and Srv02 computers that have expired.</span></span>

```powershell
Invoke-Command -ComputerName Srv01, Srv02 {Get-ChildItem -Path cert:\* `
  -Recurse -ExpiringInDays 0}
```

### <a name="combining-filters-to-find-a-specific-set-of-certificates"></a><span data-ttu-id="1c66d-161">Kombinera filter för att hitta en bestämd uppsättning certifikat</span><span class="sxs-lookup"><span data-stu-id="1c66d-161">Combining filters to find a specific set of certificates</span></span>

<span data-ttu-id="1c66d-162">Det här kommandot hämtar alla certifikat på LocalMachine Store-platsen som har följande attribut:</span><span class="sxs-lookup"><span data-stu-id="1c66d-162">This command gets all certificates in the LocalMachine store location that have the following attributes:</span></span>

- <span data-ttu-id="1c66d-163">"Fabrikam" i deras DNS-namn</span><span class="sxs-lookup"><span data-stu-id="1c66d-163">"fabrikam" in their DNS name</span></span>
- <span data-ttu-id="1c66d-164">"Klientautentisering" i deras EKU</span><span class="sxs-lookup"><span data-stu-id="1c66d-164">"Client Authentication" in their EKU</span></span>
- <span data-ttu-id="1c66d-165">ett värde för `$true` egenskapen **SendAsTrustedIssuer**</span><span class="sxs-lookup"><span data-stu-id="1c66d-165">a value of `$true` for the **SendAsTrustedIssuer** property</span></span>
- <span data-ttu-id="1c66d-166">förfaller inte inom de närmaste 30 dagarna.</span><span class="sxs-lookup"><span data-stu-id="1c66d-166">do not expire within the next 30 days.</span></span>

<span data-ttu-id="1c66d-167">Egenskapen **NotAfter** lagrar certifikatets förfallo datum.</span><span class="sxs-lookup"><span data-stu-id="1c66d-167">The **NotAfter** property stores the certificate expiration date.</span></span>

```powershell
[DateTime] $ValidThrough = (Get-Date) + (New-TimeSpan -Days 30)
Get-ChildItem -Path cert:\* -Recurse -DNSName "*fabrikam*" `
  -EKU "*Client Authentication*" | Where-Object {
                                     $_.SendAsTrustedIssuer -and `
                                     $_.NotAfter -gt $ValidThrough
                                   }
```

## <a name="opening-the-certificates-mmc-snap-in"></a><span data-ttu-id="1c66d-168">Öppna MMC-snapin-modulen certifikat</span><span class="sxs-lookup"><span data-stu-id="1c66d-168">Opening the Certificates MMC Snap-in</span></span>

<span data-ttu-id="1c66d-169">`Invoke-Item`Cmdlet: en använder standard programmet för att öppna en sökväg som du anger.</span><span class="sxs-lookup"><span data-stu-id="1c66d-169">The `Invoke-Item` cmdlet will use the default application to open a path you specify.</span></span> <span data-ttu-id="1c66d-170">För certifikat är standard programmet MMC-snapin-modulen certifikat.</span><span class="sxs-lookup"><span data-stu-id="1c66d-170">For certificates, the default application is the Certificates MMC snap-in.</span></span>

<span data-ttu-id="1c66d-171">Det här kommandot öppnar MMC-snapin-modulen certifikat för att hantera det angivna certifikatet.</span><span class="sxs-lookup"><span data-stu-id="1c66d-171">This command opens the Certificates MMC snap-in to manage the specified certificate.</span></span>

```powershell
Invoke-Item cert:\CurrentUser\my\6B8223358119BB08840DEE50FD8AF9EA776CE66B
```

## <a name="copying-certificates"></a><span data-ttu-id="1c66d-172">Kopiera certifikat</span><span class="sxs-lookup"><span data-stu-id="1c66d-172">Copying Certificates</span></span>

<span data-ttu-id="1c66d-173">Kopiering av certifikat stöds inte av **certifikat** leverantören.</span><span class="sxs-lookup"><span data-stu-id="1c66d-173">Copying certificates is not supported by the **Certificate** provider.</span></span> <span data-ttu-id="1c66d-174">När du försöker kopiera ett certifikat visas det här felet.</span><span class="sxs-lookup"><span data-stu-id="1c66d-174">When you attempt to copy a certificate, you see this error.</span></span>

```
$path = "Cert:\LocalMachine\Root\E2C0F6662D3C569705B4B31FE2CBF3434094B254"
PS Cert:\LocalMachine\> Copy-Item -Path $path -Destination .\CA\
Copy-Item : Provider operation stopped because the provider does not support
this operation.
At line:1 char:1
+ Copy-Item -Path $path -Destination .\CA\
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotImplemented: (:) [Copy-Item],
                              PSNotSupportedException
    + FullyQualifiedErrorId : NotSupported,
                              Microsoft.PowerShell.Commands.CopyItemCommand
```

## <a name="moving-certificates"></a><span data-ttu-id="1c66d-175">Flytta certifikat</span><span class="sxs-lookup"><span data-stu-id="1c66d-175">Moving Certificates</span></span>

### <a name="move-all-ssl-server-authentication-certs-to-the-webhosting-store"></a><span data-ttu-id="1c66d-176">Flytta alla SSL-certifikat för serverautentisering till webbvärds arkivet</span><span class="sxs-lookup"><span data-stu-id="1c66d-176">Move all SSL Server authentication certs to the WebHosting store</span></span>

<span data-ttu-id="1c66d-177">Det här kommandot använder `Move-Item` cmdleten för att flytta ett certifikat från My Store till webb värd arkivet.</span><span class="sxs-lookup"><span data-stu-id="1c66d-177">This command uses the `Move-Item` cmdlet to move a certificate from the My store to the WebHosting store.</span></span>

<span data-ttu-id="1c66d-178">`Move-Item` flyttar inte certifikat Arkiv och kommer inte att flytta certifikat till en annan lagrings plats, till exempel att flytta ett certifikat från LocalMachine till CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="1c66d-178">`Move-Item` will not move certificate stores and it will not move certificates to a different store location, such as moving a certificate from LocalMachine to CurrentUser.</span></span> <span data-ttu-id="1c66d-179">`Move-Item`Cmdleten flyttar certifikat, men flyttar inte privata nycklar.</span><span class="sxs-lookup"><span data-stu-id="1c66d-179">The `Move-Item` cmdlet moves certificates, but it does not move private keys.</span></span>

<span data-ttu-id="1c66d-180">Det här kommandot använder **SSLServerAuthentication** -parametern för `Get-ChildItem` cmdleten för att hämta certifikat för SSL-serverautentisering i mitt certifikat arkiv.</span><span class="sxs-lookup"><span data-stu-id="1c66d-180">This command uses the **SSLServerAuthentication** parameter of the `Get-ChildItem` cmdlet to get SSL server authentication certificates in the MY certificate store.</span></span>

<span data-ttu-id="1c66d-181">De returnerade certifikaten är skickas till `Move-Item` -cmdleten, som flyttar certifikaten till värd lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="1c66d-181">The returned certificates are piped to the `Move-Item` cmdlet, which moves the certificates to the WebHosting store.</span></span>

```powershell
Get-ChildItem cert:\LocalMachine\My -SSLServerAuthentication | Move-Item `
  -Destination cert:\LocalMachine\WebHosting
```

## <a name="deleting-certificates-and-private-keys"></a><span data-ttu-id="1c66d-182">Ta bort certifikat och privata nycklar</span><span class="sxs-lookup"><span data-stu-id="1c66d-182">Deleting Certificates and Private Keys</span></span>

<span data-ttu-id="1c66d-183">`Remove-Item`Cmdleten tar bort de certifikat som du anger.</span><span class="sxs-lookup"><span data-stu-id="1c66d-183">The `Remove-Item` cmdlet will remove certificates that you specify.</span></span> <span data-ttu-id="1c66d-184">Den `-DeleteKey` dynamiska parametern tar bort den privata nyckeln.</span><span class="sxs-lookup"><span data-stu-id="1c66d-184">The `-DeleteKey` dynamic parameter deletes the private key.</span></span>

### <a name="delete-a-certificate-from-the-ca-store"></a><span data-ttu-id="1c66d-185">Ta bort ett certifikat från CA-butiken</span><span class="sxs-lookup"><span data-stu-id="1c66d-185">Delete a Certificate from the CA store</span></span>

<span data-ttu-id="1c66d-186">Det här kommandot tar bort ett certifikat från CA-certifikatarkivet, men lämnar den tillhör ande privata nyckeln intakt.</span><span class="sxs-lookup"><span data-stu-id="1c66d-186">This command deletes a certificate from the CA certificate store, but leaves the associated private key intact.</span></span>

<span data-ttu-id="1c66d-187">I `Cert:` enheten `Remove-Item` stöder cmdleten bara parametrarna **DeleteKey**, **Path**, **whatIf** och **Confirm** .</span><span class="sxs-lookup"><span data-stu-id="1c66d-187">In the `Cert:` drive, the `Remove-Item` cmdlet supports only the **DeleteKey**, **Path**, **WhatIf**, and **Confirm** parameters.</span></span> <span data-ttu-id="1c66d-188">Alla andra parametrar ignoreras.</span><span class="sxs-lookup"><span data-stu-id="1c66d-188">All other parameters are ignored.</span></span>

```powershell
Remove-Item cert:\LocalMachine\CA\5DDC44652E62BF9AA1116DC41DE44AB47C87BDD0
```

### <a name="delete-a-certificate-using-a-wildcards-in-the-dns-name"></a><span data-ttu-id="1c66d-189">Ta bort ett certifikat med jokertecken i DNS-namnet</span><span class="sxs-lookup"><span data-stu-id="1c66d-189">Delete a Certificate using a wildcards in the DNS name</span></span>

<span data-ttu-id="1c66d-190">Det här kommandot tar bort alla certifikat som har ett DNS-namn som innehåller "Fabrikam".</span><span class="sxs-lookup"><span data-stu-id="1c66d-190">This command deletes all certificates that have a DNS name that contains "Fabrikam".</span></span> <span data-ttu-id="1c66d-191">Den använder **DNSName** -parametern för `Get-ChildItem` cmdleten för att hämta certifikaten och `Remove-Item` cmdleten för att ta bort dem.</span><span class="sxs-lookup"><span data-stu-id="1c66d-191">It uses the **DNSName** parameter of the `Get-ChildItem` cmdlet to get the certificates and the `Remove-Item` cmdlet to delete them.</span></span>

```powershell
Get-ChildItem -Path cert:\LocalMachine -DnsName *Fabrikam* | Remove-Item
```

### <a name="delete-private-keys-from-a-remote-computer"></a><span data-ttu-id="1c66d-192">Ta bort privata nycklar från en fjärran sluten dator</span><span class="sxs-lookup"><span data-stu-id="1c66d-192">Delete private keys from a remote computer</span></span>

<span data-ttu-id="1c66d-193">Den här serien med kommandon aktiverar delegering och tar sedan bort certifikatet och den tillhör ande privata nyckeln på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="1c66d-193">This series of commands enables delegation and then deletes the certificate and associated private key on a remote computer.</span></span> <span data-ttu-id="1c66d-194">Om du vill ta bort en privat nyckel på en fjärrdator måste du använda delegerade autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="1c66d-194">To delete a private key on a remote computer, you must use delegated credentials.</span></span>

<span data-ttu-id="1c66d-195">Använd `Enable-WSManCredSSP` cmdleten för att aktivera autentisering av Credential Security Service Provider (CredSSP) på en klient på den lokala S1-datorn.</span><span class="sxs-lookup"><span data-stu-id="1c66d-195">Use the `Enable-WSManCredSSP` cmdlet to enable Credential Security Service Provider (CredSSP) authentication on a client on the S1 remote computer.</span></span>
<span data-ttu-id="1c66d-196">CredSSP tillåter delegerad autentisering.</span><span class="sxs-lookup"><span data-stu-id="1c66d-196">CredSSP permits delegated authentication.</span></span>

```powershell
Enable-WSManCredSSP -Role Client -DelegateComputer S1
```

<span data-ttu-id="1c66d-197">Använd `Connect-WSMan` cmdleten för att ansluta S1-datorn till WinRM-tjänsten på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="1c66d-197">Use the `Connect-WSMan` cmdlet to connect the S1 computer to the WinRM service on the local computer.</span></span> <span data-ttu-id="1c66d-198">När det här kommandot har slutförts visas S1-datorn på den lokala `WSMan:` enheten i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1c66d-198">When this command completes, the S1 computer appears in the local `WSMan:` drive in PowerShell.</span></span>

```powershell
Connect-WSMan -ComputerName S1 -Credential Domain01\Admin01
```

<span data-ttu-id="1c66d-199">Nu kan du använda cmdleten Set-Item i WSMan: Drive för att aktivera CredSSP-attributet för WinRM-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="1c66d-199">Now, you can use the Set-Item cmdlet in the WSMan: drive to enable the CredSSP attribute for the WinRM service.</span></span>

```powershell
Set-Item -Path WSMan:\S1\Service\Auth\CredSSP -Value $true
```

<span data-ttu-id="1c66d-200">Starta en fjärran sluten session på S1-datorn med `New-PSSession` cmdleten och ange CredSSP-autentisering.</span><span class="sxs-lookup"><span data-stu-id="1c66d-200">Start a remote session on the s1 computer using the `New-PSSession` cmdlet, and specify CredSSP authentication.</span></span> <span data-ttu-id="1c66d-201">Sparar sessionen i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="1c66d-201">Saves the session in the `$s` variable.</span></span>

```powershell
$s  = New-PSSession S1 -Authentication CredSSP -Credential Domain01\Admin01
```

<span data-ttu-id="1c66d-202">Använd slutligen `Invoke-Command` cmdleten för att köra ett `Remove-Item` kommando i sessionen i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="1c66d-202">Finally, use the `Invoke-Command` cmdlet to run a `Remove-Item` command in the session in the `$s` variable.</span></span> <span data-ttu-id="1c66d-203">`Remove-Item`Kommandot använder parametern **DeleteKey** för att ta bort den privata nyckeln tillsammans med det angivna certifikatet.</span><span class="sxs-lookup"><span data-stu-id="1c66d-203">The `Remove-Item` command uses the **DeleteKey** parameter to remove the private key along with the specified certificate.</span></span>

```powershell
Invoke-Command -Session $s { Remove-Item `
  -Path cert:\LocalMachine\My\D2D38EBA60CAA1C12055A2E1C83B15AD450110C2 `
  -DeleteKey
  }
```

### <a name="delete-expired-certificates"></a><span data-ttu-id="1c66d-204">Ta bort utgångna certifikat</span><span class="sxs-lookup"><span data-stu-id="1c66d-204">Delete expired Certificates</span></span>

<span data-ttu-id="1c66d-205">Det här kommandot använder **ExpiringInDays** -parametern för `Get-ChildItem` cmdleten med värdet 0 för att hämta certifikat i den webvärdskaps lager som har upphört att gälla.</span><span class="sxs-lookup"><span data-stu-id="1c66d-205">This command uses the **ExpiringInDays** parameter of the `Get-ChildItem` cmdlet with a value of 0 to get certificates in the WebHosting store that have expired.</span></span>

<span data-ttu-id="1c66d-206">Variabeln som innehåller de returnerade certifikaten är skickas till `Remove-Item` cmdleten, som tar bort dem.</span><span class="sxs-lookup"><span data-stu-id="1c66d-206">The variable containing the returned certificates is piped to the `Remove-Item` cmdlet, which deletes them.</span></span> <span data-ttu-id="1c66d-207">Kommandot använder parametern **DeleteKey** för att ta bort den privata nyckeln tillsammans med certifikatet.</span><span class="sxs-lookup"><span data-stu-id="1c66d-207">The command uses the **DeleteKey** parameter to delete the private key along with the certificate.</span></span>

```powershell
$expired = Get-ChildItem cert:\LocalMachine\WebHosting -ExpiringInDays 0
$expired | Remove-Item -DeleteKey
```

## <a name="creating-certificates"></a><span data-ttu-id="1c66d-208">Skapa certifikat</span><span class="sxs-lookup"><span data-stu-id="1c66d-208">Creating Certificates</span></span>

<span data-ttu-id="1c66d-209">`New-Item`Cmdleten skapar inga nya certifikat i **certifikat** leverantören.</span><span class="sxs-lookup"><span data-stu-id="1c66d-209">The `New-Item` cmdlet does not create new certificates in the **Certificate** provider.</span></span> <span data-ttu-id="1c66d-210">Använd cmdleten [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) för att skapa ett certifikat för test ändamål.</span><span class="sxs-lookup"><span data-stu-id="1c66d-210">Use the [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet to create a certificate for testing purposes.</span></span>

## <a name="creating-certificate-stores"></a><span data-ttu-id="1c66d-211">Skapa certifikat Arkiv</span><span class="sxs-lookup"><span data-stu-id="1c66d-211">Creating Certificate Stores</span></span>

<span data-ttu-id="1c66d-212">I cert: Drive, `New-Item` skapar cmdleten certifikat Arkiv på platsen för LocalMachine-platsen.</span><span class="sxs-lookup"><span data-stu-id="1c66d-212">In the Cert: drive, the `New-Item` cmdlet creates certificate stores in the LocalMachine store location.</span></span> <span data-ttu-id="1c66d-213">Den har stöd för parametrarna **namn**, **sökväg**, **whatIf** och **Confirm** .</span><span class="sxs-lookup"><span data-stu-id="1c66d-213">It supports the **Name**, **Path**, **WhatIf**, and **Confirm** parameters.</span></span> <span data-ttu-id="1c66d-214">Alla andra parametrar ignoreras.</span><span class="sxs-lookup"><span data-stu-id="1c66d-214">All other parameters are ignored.</span></span> <span data-ttu-id="1c66d-215">Kommandot returnerar en **system. Security. Cryptography. X509Certificates. X509Store** som representerar det nya certifikat arkivet.</span><span class="sxs-lookup"><span data-stu-id="1c66d-215">The command returns a **System.Security.Cryptography.X509Certificates.X509Store** that represents the new certificate store.</span></span>

<span data-ttu-id="1c66d-216">Det här kommandot skapar ett nytt certifikat Arkiv med namnet "CustomStore" på LocalMachine-lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="1c66d-216">This command creates a new certificate store named "CustomStore" in the LocalMachine store location.</span></span>

```powershell
New-Item -Path cert:\LocalMachine\CustomStore
```

### <a name="create-a-new-certificate-store-on-a-remote-computer"></a><span data-ttu-id="1c66d-217">Skapa ett nytt certifikat Arkiv på en fjärran sluten dator</span><span class="sxs-lookup"><span data-stu-id="1c66d-217">Create a new certificate store on a remote computer</span></span>

<span data-ttu-id="1c66d-218">Det här kommandot skapar ett nytt certifikat Arkiv med namnet "HostingStore" på LocalMachine Store-platsen på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="1c66d-218">This command creates a new certificate store named "HostingStore" in the LocalMachine store location on the Server01 computer.</span></span>

<span data-ttu-id="1c66d-219">Kommandot använder `Invoke-Command` cmdleten för att köra ett `New-Item` kommando på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="1c66d-219">The command uses the `Invoke-Command` cmdlet to run a `New-Item` command on the Server01 computer.</span></span> <span data-ttu-id="1c66d-220">Kommandot returnerar en **system. Security. Cryptography. X509Certificates. X509Store** som representerar det nya certifikat arkivet.</span><span class="sxs-lookup"><span data-stu-id="1c66d-220">The command returns a **System.Security.Cryptography.X509Certificates.X509Store** that represents the new certificate store.</span></span>

```powershell
Invoke-Command { New-Item -Path cert:\LocalMachine\CustomStore } `
  -ComputerName Server01
```

## <a name="creating-client-certificates-for-ws-man"></a><span data-ttu-id="1c66d-221">Skapa klient certifikat för WS-Man</span><span class="sxs-lookup"><span data-stu-id="1c66d-221">Creating Client Certificates for WS-Man</span></span>

<span data-ttu-id="1c66d-222">Det här kommandot skapar en **ClientCertificate** -post som kan användas av **WS-Management-** klienten.</span><span class="sxs-lookup"><span data-stu-id="1c66d-222">This command creates **ClientCertificate** entry that can be used by the **WS-Management** client.</span></span> <span data-ttu-id="1c66d-223">Den nya **ClientCertificate** visas under katalogen **ClientCertificate** som "ClientCertificate_1234567890".</span><span class="sxs-lookup"><span data-stu-id="1c66d-223">The new **ClientCertificate** will show up under the **ClientCertificate** directory as "ClientCertificate_1234567890".</span></span> <span data-ttu-id="1c66d-224">Alla parametrar är obligatoriska.</span><span class="sxs-lookup"><span data-stu-id="1c66d-224">All of the parameters are mandatory.</span></span> <span data-ttu-id="1c66d-225">**Utfärdaren** måste vara tumavtryck för utfärdarcertifikatet.</span><span class="sxs-lookup"><span data-stu-id="1c66d-225">The **Issuer** needs to be thumbprint of the issuers certificate.</span></span>

```powershell
$cred = Get-Credential
New-Item -Path WSMan:\localhost\ClientCertificate `
         -Issuer 1b3fd224d66c6413fe20d21e38b304226d192dfe `
         -URI wmicimv2/* -Credential $cred
```

## <a name="deleting-certificate-stores"></a><span data-ttu-id="1c66d-226">Ta bort certifikat Arkiv</span><span class="sxs-lookup"><span data-stu-id="1c66d-226">Deleting Certificate Stores</span></span>

### <a name="delete-a-certificate-store-from-a-remote-computer"></a><span data-ttu-id="1c66d-227">Ta bort ett certifikat arkiv från en fjärran sluten dator</span><span class="sxs-lookup"><span data-stu-id="1c66d-227">Delete a certificate store from a remote computer</span></span>

<span data-ttu-id="1c66d-228">Det här kommandot använder `Invoke-Command` cmdleten för att köra ett `Remove-Item` kommando på datorerna S1 och S2.</span><span class="sxs-lookup"><span data-stu-id="1c66d-228">This command uses the `Invoke-Command` cmdlet to run a `Remove-Item` command on the S1 and S2 computers.</span></span> <span data-ttu-id="1c66d-229">`Remove-Item`Kommandot innehåller parametern **rekursivt** , som tar bort certifikaten i arkivet innan det tas bort.</span><span class="sxs-lookup"><span data-stu-id="1c66d-229">The `Remove-Item` command includes the **Recurse** parameter, which deletes the certificates in the store before it deletes the store.</span></span>

```powershell
Invoke-Command { Remove-Item -Path cert:\LocalMachine\TestStore -Recurse } `
  -ComputerName S1, S2
```

## <a name="dynamic-parameters"></a><span data-ttu-id="1c66d-230">Dynamiska parametrar</span><span class="sxs-lookup"><span data-stu-id="1c66d-230">Dynamic parameters</span></span>

<span data-ttu-id="1c66d-231">Dynamiska parametrar är cmdlet-parametrar som läggs till av en PowerShell-Provider och är bara tillgängliga när cmdleten används i den provider-aktiverade enheten.</span><span class="sxs-lookup"><span data-stu-id="1c66d-231">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span> <span data-ttu-id="1c66d-232">Dessa parametrar är giltiga i alla under kataloger i certifikat leverantören, men gäller endast för certifikat.</span><span class="sxs-lookup"><span data-stu-id="1c66d-232">These parameters are valid in all subdirectories of the Certificate provider, but are effective only on certificates.</span></span>

> [!NOTE]
> <span data-ttu-id="1c66d-233">Parametrar som utför filtrering mot `EnhancedKeyUsageList` egenskapen returnerar även objekt med ett tomt `EnhancedKeyUsageList` egenskaps värde.</span><span class="sxs-lookup"><span data-stu-id="1c66d-233">Parameters that perform filtering against the `EnhancedKeyUsageList` property also return items with an empty `EnhancedKeyUsageList` property value.</span></span>
> <span data-ttu-id="1c66d-234">Certifikat som har en tom **EnhancedKeyUsageList** kan användas i alla syfte.</span><span class="sxs-lookup"><span data-stu-id="1c66d-234">Certificates that have an empty **EnhancedKeyUsageList** can be used for all purposes.</span></span>

<span data-ttu-id="1c66d-235">Följande parametrar för certifikat leverantörer har introducerats om i PowerShell 7,1.</span><span class="sxs-lookup"><span data-stu-id="1c66d-235">The following Certificate provider parameters were reintroduced in PowerShell 7.1.</span></span>

- <span data-ttu-id="1c66d-236">DNSName</span><span class="sxs-lookup"><span data-stu-id="1c66d-236">DNSName</span></span>
- <span data-ttu-id="1c66d-237">DocumentEncryptionCert</span><span class="sxs-lookup"><span data-stu-id="1c66d-237">DocumentEncryptionCert</span></span>
- <span data-ttu-id="1c66d-238">ANVÄNDNING</span><span class="sxs-lookup"><span data-stu-id="1c66d-238">EKU</span></span>
- <span data-ttu-id="1c66d-239">ExpiringInDays</span><span class="sxs-lookup"><span data-stu-id="1c66d-239">ExpiringInDays</span></span>
- <span data-ttu-id="1c66d-240">SSLServerAuthentication</span><span class="sxs-lookup"><span data-stu-id="1c66d-240">SSLServerAuthentication</span></span>

### <a name="codesigningcert-systemmanagementautomationswitchparameter"></a><span data-ttu-id="1c66d-241">CodeSigningCert <system. Management. Automation. SwitchParameter></span><span class="sxs-lookup"><span data-stu-id="1c66d-241">CodeSigningCert <System.Management.Automation.SwitchParameter></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="1c66d-242">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="1c66d-242">Cmdlets supported</span></span>

- [<span data-ttu-id="1c66d-243">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="1c66d-243">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)

- [<span data-ttu-id="1c66d-244">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="1c66d-244">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="1c66d-245">Den här parametern hämtar certifikat som har "kod signering" i deras värde för egenskapen **EnhancedKeyUsageList** .</span><span class="sxs-lookup"><span data-stu-id="1c66d-245">This parameter gets certificates that have "Code Signing" in their **EnhancedKeyUsageList** property value.</span></span>

### <a name="deletekey-systemmanagementautomationswitchparameter"></a><span data-ttu-id="1c66d-246">DeleteKey <system. Management. Automation. SwitchParameter></span><span class="sxs-lookup"><span data-stu-id="1c66d-246">DeleteKey <System.Management.Automation.SwitchParameter></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="1c66d-247">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="1c66d-247">Cmdlets supported</span></span>

- [<span data-ttu-id="1c66d-248">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="1c66d-248">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)

<span data-ttu-id="1c66d-249">Den här parametern tar bort den tillhör ande privata nyckeln när certifikatet tas bort.</span><span class="sxs-lookup"><span data-stu-id="1c66d-249">This parameter deletes the associated private key when it deletes the certificate.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1c66d-250">Om du vill ta bort en privat nyckel som är kopplad till ett användar certifikat i `Cert:\CurrentUser` arkivet på en fjärrdator måste du använda delegerade autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="1c66d-250">To delete a private key that is associated with a user certificate in the `Cert:\CurrentUser` store on a remote computer, you must use delegated credentials.</span></span> <span data-ttu-id="1c66d-251">`Invoke-Command`Cmdleten stöder delegering av autentiseringsuppgifter med hjälp av **CredSSP** -parametern.</span><span class="sxs-lookup"><span data-stu-id="1c66d-251">The `Invoke-Command` cmdlet supports credential delegation using the **CredSSP** parameter.</span></span> <span data-ttu-id="1c66d-252">Du bör överväga eventuella säkerhets risker innan du använder `Remove-Item` med `Invoke-Command` och delegering av autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="1c66d-252">You should consider any security risks before using `Remove-Item` with `Invoke-Command` and credential delegation.</span></span>

<span data-ttu-id="1c66d-253">Den här parametern introducerades i PowerShell 7,1</span><span class="sxs-lookup"><span data-stu-id="1c66d-253">This parameter was reintroduced in PowerShell 7.1</span></span>

### <a name="dnsname-microsoftpowershellcommandsdnsnamerepresentation"></a><span data-ttu-id="1c66d-254">DnsName <Microsoft. PowerShell. commands. DnsNameRepresentation></span><span class="sxs-lookup"><span data-stu-id="1c66d-254">DnsName <Microsoft.PowerShell.Commands.DnsNameRepresentation></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="1c66d-255">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="1c66d-255">Cmdlets supported</span></span>

- [<span data-ttu-id="1c66d-256">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="1c66d-256">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="1c66d-257">Den här parametern hämtar certifikat som har det angivna domän namnet eller namn mönstret i certifikatets egenskap **DNSNameList** .</span><span class="sxs-lookup"><span data-stu-id="1c66d-257">This parameter gets certificates that have the specified domain name or name pattern in the **DNSNameList** property of the certificate.</span></span> <span data-ttu-id="1c66d-258">Värdet för den här parametern kan antingen vara "Unicode" eller "ASCII".</span><span class="sxs-lookup"><span data-stu-id="1c66d-258">The value of this parameter can either be "Unicode" or "ASCII".</span></span> <span data-ttu-id="1c66d-259">Punycode-värden konverteras till Unicode.</span><span class="sxs-lookup"><span data-stu-id="1c66d-259">Punycode values are converted to Unicode.</span></span> <span data-ttu-id="1c66d-260">Jokertecken ( `*` ) är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="1c66d-260">Wildcard characters (`*`) are permitted.</span></span>

<span data-ttu-id="1c66d-261">Den här parametern introducerades i PowerShell 7,1</span><span class="sxs-lookup"><span data-stu-id="1c66d-261">This parameter was reintroduced in PowerShell 7.1</span></span>

### <a name="documentencryptioncert-systemmanagementautomationswitchparameter"></a><span data-ttu-id="1c66d-262">DocumentEncryptionCert <system. Management. Automation. SwitchParameter></span><span class="sxs-lookup"><span data-stu-id="1c66d-262">DocumentEncryptionCert <System.Management.Automation.SwitchParameter></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="1c66d-263">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="1c66d-263">Cmdlets supported</span></span>

- [<span data-ttu-id="1c66d-264">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="1c66d-264">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)

- [<span data-ttu-id="1c66d-265">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="1c66d-265">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="1c66d-266">Den här parametern hämtar certifikat med "dokument kryptering" i deras värde för egenskapen **EnhancedKeyUsageList** .</span><span class="sxs-lookup"><span data-stu-id="1c66d-266">This parameter gets certificates that have "Document Encryption" in their **EnhancedKeyUsageList** property value.</span></span>

### <a name="eku-systemstring"></a><span data-ttu-id="1c66d-267">EKU <system. String></span><span class="sxs-lookup"><span data-stu-id="1c66d-267">EKU <System.String></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="1c66d-268">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="1c66d-268">Cmdlets supported</span></span>

- [<span data-ttu-id="1c66d-269">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="1c66d-269">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="1c66d-270">Den här parametern hämtar certifikat som har den angivna texten eller text mönstret i `EnhancedKeyUsageList` certifikatets egenskap.</span><span class="sxs-lookup"><span data-stu-id="1c66d-270">This parameter gets certificates that have the specified text or text pattern in the `EnhancedKeyUsageList` property of the certificate.</span></span> <span data-ttu-id="1c66d-271">Jokertecken ( `*` ) är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="1c66d-271">Wildcard characters (`*`) are permitted.</span></span> <span data-ttu-id="1c66d-272">`EnhancedKeyUsageList`Egenskapen innehåller det egna namnet och OID-fälten i EKU.</span><span class="sxs-lookup"><span data-stu-id="1c66d-272">The `EnhancedKeyUsageList` property contains the friendly name and the OID fields of the EKU.</span></span>

<span data-ttu-id="1c66d-273">Den här parametern introducerades i PowerShell 7,1</span><span class="sxs-lookup"><span data-stu-id="1c66d-273">This parameter was reintroduced in PowerShell 7.1</span></span>

### <a name="expiringindays-systemint32"></a><span data-ttu-id="1c66d-274">ExpiringInDays <system. Int32></span><span class="sxs-lookup"><span data-stu-id="1c66d-274">ExpiringInDays <System.Int32></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="1c66d-275">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="1c66d-275">Cmdlets supported</span></span>

- [<span data-ttu-id="1c66d-276">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="1c66d-276">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="1c66d-277">Den här parametern hämtar certifikat som upphör att gälla inom eller före det angivna antalet dagar.</span><span class="sxs-lookup"><span data-stu-id="1c66d-277">This parameter gets certificates that are expiring in or before the specified number of days.</span></span> <span data-ttu-id="1c66d-278">Värdet 0 (noll) hämtar certifikat som har upphört att gälla.</span><span class="sxs-lookup"><span data-stu-id="1c66d-278">A value of 0 (zero) gets certificates that have expired.</span></span>

<span data-ttu-id="1c66d-279">Den här parametern introducerades i PowerShell 7,1</span><span class="sxs-lookup"><span data-stu-id="1c66d-279">This parameter was reintroduced in PowerShell 7.1</span></span>

### <a name="itemtype-string"></a><span data-ttu-id="1c66d-280">ItemType \<String\></span><span class="sxs-lookup"><span data-stu-id="1c66d-280">ItemType \<String\></span></span>

<span data-ttu-id="1c66d-281">Med den här parametern kan du ange vilken typ av objekt som skapas av `New-Item` .</span><span class="sxs-lookup"><span data-stu-id="1c66d-281">This parameter allows you to specify the type of item created by `New-Item`.</span></span>

<span data-ttu-id="1c66d-282">I en `Certificate` enhet tillåts följande värden:</span><span class="sxs-lookup"><span data-stu-id="1c66d-282">In a `Certificate` drive, the following values are allowed:</span></span>

- <span data-ttu-id="1c66d-283">Certifikat leverantör</span><span class="sxs-lookup"><span data-stu-id="1c66d-283">Certificate Provider</span></span>
- <span data-ttu-id="1c66d-284">Certifikat</span><span class="sxs-lookup"><span data-stu-id="1c66d-284">Certificate</span></span>
- <span data-ttu-id="1c66d-285">Lagringsplats</span><span class="sxs-lookup"><span data-stu-id="1c66d-285">Store</span></span>
- <span data-ttu-id="1c66d-286">StoreLocation</span><span class="sxs-lookup"><span data-stu-id="1c66d-286">StoreLocation</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="1c66d-287">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="1c66d-287">Cmdlets Supported</span></span>

- [<span data-ttu-id="1c66d-288">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="1c66d-288">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="sslserverauthentication-systemmanagementautomationswitchparameter"></a><span data-ttu-id="1c66d-289">SSLServerAuthentication <system. Management. Automation. SwitchParameter></span><span class="sxs-lookup"><span data-stu-id="1c66d-289">SSLServerAuthentication <System.Management.Automation.SwitchParameter></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="1c66d-290">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="1c66d-290">Cmdlets supported</span></span>

- [<span data-ttu-id="1c66d-291">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="1c66d-291">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="1c66d-292">Hämtar endast Server certifikat för SSL-webbvärd.</span><span class="sxs-lookup"><span data-stu-id="1c66d-292">Gets only server certificates for SSL web hosting.</span></span> <span data-ttu-id="1c66d-293">Den här parametern hämtar certifikat som har "serverautentisering" i deras `EnhancedKeyUsageList` egenskaps värde.</span><span class="sxs-lookup"><span data-stu-id="1c66d-293">This parameter gets certificates that have "Server Authentication" in their `EnhancedKeyUsageList` property value.</span></span>

<span data-ttu-id="1c66d-294">Den här parametern introducerades i PowerShell 7,1</span><span class="sxs-lookup"><span data-stu-id="1c66d-294">This parameter was reintroduced in PowerShell 7.1</span></span>

## <a name="script-properties"></a><span data-ttu-id="1c66d-295">Skript egenskaper</span><span class="sxs-lookup"><span data-stu-id="1c66d-295">Script properties</span></span>

<span data-ttu-id="1c66d-296">Nya skript egenskaper har lagts till i **x509Certificate2** -objektet som representerar certifikaten för att göra det enkelt att söka efter och hantera certifikaten.</span><span class="sxs-lookup"><span data-stu-id="1c66d-296">New script properties have been added to the **x509Certificate2** object that represents the certificates to make it easy to search and manage the certificates.</span></span>

- <span data-ttu-id="1c66d-297">`DnsNameList`: Om du vill fylla i `DnsNameList` egenskapen kopierar certifikat leverantören innehållet från DNSName-posten i SubjectAlternativeName (San)-tillägget.</span><span class="sxs-lookup"><span data-stu-id="1c66d-297">`DnsNameList`: To populate the `DnsNameList` property, the Certificate provider copies the content from the DNSName entry in the SubjectAlternativeName (SAN) extension.</span></span> <span data-ttu-id="1c66d-298">Om SAN-tillägget är tomt fylls egenskapen i med innehåll från certifikatets ämnes fält.</span><span class="sxs-lookup"><span data-stu-id="1c66d-298">If the SAN extension is empty, the property is populated with content from the Subject field of the certificate.</span></span>

- <span data-ttu-id="1c66d-299">`EnhancedKeyUsageList`: Om du vill fylla i `EnhancedKeyUsageList` egenskapen kopierar certifikat leverantören OID-egenskaperna för fältet EnhancedKeyUsage (EKU) i certifikatet och skapar ett eget namn för det.</span><span class="sxs-lookup"><span data-stu-id="1c66d-299">`EnhancedKeyUsageList`: To populate the `EnhancedKeyUsageList` property, the Certificate provider copies the OID properties of the EnhancedKeyUsage (EKU) field in the certificate and creates a friendly name for it.</span></span>

- <span data-ttu-id="1c66d-300">`SendAsTrustedIssuer`: Om du vill fylla i `SendAsTrustedIssuer` egenskapen kopierar certifikat leverantören `SendAsTrustedIssuer` egenskapen från certifikatet.</span><span class="sxs-lookup"><span data-stu-id="1c66d-300">`SendAsTrustedIssuer`: To populate the `SendAsTrustedIssuer` property, the Certificate provider copies the `SendAsTrustedIssuer` property from the certificate.</span></span>  <span data-ttu-id="1c66d-301">Mer information finns i [hantering av betrodda utfärdare för klientautentisering](/windows-server/security/tls/what-s-new-in-tls-ssl-schannel-ssp-overview#BKMK_TrustedIssuers).</span><span class="sxs-lookup"><span data-stu-id="1c66d-301">For more information see [Management of trusted issuers for client authentication](/windows-server/security/tls/what-s-new-in-tls-ssl-schannel-ssp-overview#BKMK_TrustedIssuers).</span></span>

<span data-ttu-id="1c66d-302">Med de här nya funktionerna kan du söka efter certifikat baserat på deras DNS-namn och förfallo datum och särskilja certifikat för klient-och serverautentisering genom att värdet för egenskaperna för utökad nyckel användning (EKU) används.</span><span class="sxs-lookup"><span data-stu-id="1c66d-302">These new features let you search for certificates based on their DNS names and expiration dates, and distinguish client and server authentication certificates by the value of their Enhanced Key Usage (EKU) properties.</span></span>

## <a name="using-the-pipeline"></a><span data-ttu-id="1c66d-303">Använda pipelinen</span><span class="sxs-lookup"><span data-stu-id="1c66d-303">Using the pipeline</span></span>

<span data-ttu-id="1c66d-304">Provider-cmdletar accepterar pipeline-ininformation.</span><span class="sxs-lookup"><span data-stu-id="1c66d-304">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="1c66d-305">Du kan använda pipelinen för att förenkla uppgiften genom att skicka leverantörs data från en cmdlet till en annan provider-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1c66d-305">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="1c66d-306">Mer information om hur du använder pipelinen med Provider-cmdletar finns i cmdlet-referenser som finns i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="1c66d-306">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="1c66d-307">Få hjälp</span><span class="sxs-lookup"><span data-stu-id="1c66d-307">Getting help</span></span>

<span data-ttu-id="1c66d-308">Från och med Windows PowerShell 3,0 kan du hämta anpassade hjälp avsnitt för provider-cmdletar som förklarar hur dessa cmdletar fungerar i en fil systemen het.</span><span class="sxs-lookup"><span data-stu-id="1c66d-308">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="1c66d-309">Om du vill få hjälp avsnitten som är anpassade för fil system enheten kör du ett [Get-Help-](xref:Microsoft.PowerShell.Core.Get-Help) kommando i en fil system enhet eller använder `-Path` parametern för `Get-Help` att ange en fil system enhet.</span><span class="sxs-lookup"><span data-stu-id="1c66d-309">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of `Get-Help` to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path cert:
```

## <a name="see-also"></a><span data-ttu-id="1c66d-310">Se även</span><span class="sxs-lookup"><span data-stu-id="1c66d-310">See also</span></span>

[<span data-ttu-id="1c66d-311">about_Providers</span><span class="sxs-lookup"><span data-stu-id="1c66d-311">about_Providers</span></span>](../../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="1c66d-312">about_Signing</span><span class="sxs-lookup"><span data-stu-id="1c66d-312">about_Signing</span></span>](../../Microsoft.PowerShell.Core/About/about_Signing.md)

[<span data-ttu-id="1c66d-313">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="1c66d-313">Get-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)

[<span data-ttu-id="1c66d-314">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="1c66d-314">Set-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

[<span data-ttu-id="1c66d-315">Get-PfxCertificate</span><span class="sxs-lookup"><span data-stu-id="1c66d-315">Get-PfxCertificate</span></span>](xref:Microsoft.PowerShell.Security.Get-PfxCertificate)
