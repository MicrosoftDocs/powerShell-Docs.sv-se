---
description: Certifikat
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/04/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/about/about_certificate_provider?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Certifikat leverantör
ms.openlocfilehash: 6d78c587f79bb09c66700fb71519fe0f32318386
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272492"
---
# <a name="certificate-provider"></a><span data-ttu-id="38f63-104">Certifikat leverantör</span><span class="sxs-lookup"><span data-stu-id="38f63-104">Certificate Provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="38f63-105">Providernamn</span><span class="sxs-lookup"><span data-stu-id="38f63-105">Provider name</span></span>

<span data-ttu-id="38f63-106">Certifikat</span><span class="sxs-lookup"><span data-stu-id="38f63-106">Certificate</span></span>

## <a name="drives"></a><span data-ttu-id="38f63-107">Enheter</span><span class="sxs-lookup"><span data-stu-id="38f63-107">Drives</span></span>

`Cert:`

## <a name="capabilities"></a><span data-ttu-id="38f63-108">Funktioner</span><span class="sxs-lookup"><span data-stu-id="38f63-108">Capabilities</span></span>

<span data-ttu-id="38f63-109">**ShouldProcess**</span><span class="sxs-lookup"><span data-stu-id="38f63-109">**ShouldProcess**</span></span>

## <a name="short-description"></a><span data-ttu-id="38f63-110">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="38f63-110">Short description</span></span>

<span data-ttu-id="38f63-111">Ger åtkomst till certifikat Arkiv för X. 509 och certifikat i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="38f63-111">Provides access to X.509 certificate stores and certificates in PowerShell.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="38f63-112">Detaljerad beskrivning</span><span class="sxs-lookup"><span data-stu-id="38f63-112">Detailed description</span></span>

<span data-ttu-id="38f63-113">Med PowerShell- **certifikatets** Provider kan du hämta, lägga till, ändra, rensa och ta bort certifikat och certifikat Arkiv i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="38f63-113">The PowerShell **Certificate** provider lets you get, add, change, clear, and delete certificates and certificate stores in PowerShell.</span></span>

<span data-ttu-id="38f63-114">**Certifikat** enheten är ett hierarkiskt namn område som innehåller certifikat arkiven och certifikaten på din dator.</span><span class="sxs-lookup"><span data-stu-id="38f63-114">The **Certificate** drive is a hierarchical namespace containing the certificate stores and certificates on your computer.</span></span>

<span data-ttu-id="38f63-115">**Certifikat** leverantören stöder följande cmdletar, som beskrivs i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="38f63-115">The **Certificate** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="38f63-116">Get-location</span><span class="sxs-lookup"><span data-stu-id="38f63-116">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="38f63-117">Ange plats</span><span class="sxs-lookup"><span data-stu-id="38f63-117">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="38f63-118">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="38f63-118">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="38f63-119">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="38f63-119">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [<span data-ttu-id="38f63-120">Anropa-objekt</span><span class="sxs-lookup"><span data-stu-id="38f63-120">Invoke-Item</span></span>](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [<span data-ttu-id="38f63-121">Flytta objekt</span><span class="sxs-lookup"><span data-stu-id="38f63-121">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="38f63-122">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="38f63-122">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="38f63-123">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="38f63-123">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="38f63-124">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="38f63-124">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="38f63-125">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="38f63-125">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [<span data-ttu-id="38f63-126">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="38f63-126">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [<span data-ttu-id="38f63-127">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="38f63-127">Get-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)
- [<span data-ttu-id="38f63-128">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="38f63-128">Set-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="38f63-129">Typer som exponeras av denna provider</span><span class="sxs-lookup"><span data-stu-id="38f63-129">Types exposed by this provider</span></span>

<span data-ttu-id="38f63-130">Certifikat enheten exponerar följande typer.</span><span class="sxs-lookup"><span data-stu-id="38f63-130">The Certificate drive exposes the following types.</span></span>

- <span data-ttu-id="38f63-131">Lagra platser (Microsoft. PowerShell. commands. X509StoreLocation), som är behållare på hög nivå som grupperar certifikaten för den aktuella användaren och för alla användare.</span><span class="sxs-lookup"><span data-stu-id="38f63-131">Store locations (Microsoft.PowerShell.Commands.X509StoreLocation), which are high-level containers that group the certificates for the current user and for all users.</span></span> <span data-ttu-id="38f63-132">Varje system har en CurrentUser-och LocalMachine-lagringsplats (alla användare).</span><span class="sxs-lookup"><span data-stu-id="38f63-132">Each system has a CurrentUser and LocalMachine (all users) store location.</span></span>

- <span data-ttu-id="38f63-133">Certifikat arkiv (system. Security. Cryptography. X509Certificates. X509Store), som är fysiska butiker där certifikat sparas och hanteras.</span><span class="sxs-lookup"><span data-stu-id="38f63-133">Certificates stores (System.Security.Cryptography.X509Certificates.X509Store), which are physical stores in which certificates are saved and managed.</span></span>

- <span data-ttu-id="38f63-134">X. 509 **system. Security. Cryptography. X509Certificates. X509Certificate2** -certifikat, som representerar ett X. 509-certifikat på datorn.</span><span class="sxs-lookup"><span data-stu-id="38f63-134">X.509 **System.Security.Cryptography.X509Certificates.X509Certificate2** certificates, each of which represent an X.509 certificate on the computer.</span></span>
  <span data-ttu-id="38f63-135">Certifikat identifieras av deras tumavtrycken.</span><span class="sxs-lookup"><span data-stu-id="38f63-135">Certificates are identified by their thumbprints.</span></span>

## <a name="navigating-the-certificate-drive"></a><span data-ttu-id="38f63-136">Navigera i certifikat enheten</span><span class="sxs-lookup"><span data-stu-id="38f63-136">Navigating the Certificate drive</span></span>

<span data-ttu-id="38f63-137">**Certifikat** leverantören visar certifikat namn området som `Cert:` enheten i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="38f63-137">The **Certificate** provider exposes the certificate namespace as the `Cert:` drive in PowerShell.</span></span> <span data-ttu-id="38f63-138">Det här kommandot använder `Set-Location` kommandot för att ändra den aktuella platsen till rot certifikat arkivet på LocalMachine Arkiv plats.</span><span class="sxs-lookup"><span data-stu-id="38f63-138">This command uses the `Set-Location` command to change the current location to the Root certificate store in the LocalMachine store location.</span></span> <span data-ttu-id="38f63-139">Använd ett omvänt snedstreck ( \\ ) eller ett snedstreck (/) för att ange `Cert:` enhetens nivå.</span><span class="sxs-lookup"><span data-stu-id="38f63-139">Use a backslash (\\) or a forward slash (/) to indicate a level of the `Cert:` drive.</span></span>

```powershell
Set-Location Cert:
```

<span data-ttu-id="38f63-140">Du kan också arbeta med certifikat leverantören från någon annan PowerShell-enhet.</span><span class="sxs-lookup"><span data-stu-id="38f63-140">You can also work with the certificate provider from any other PowerShell drive.</span></span> <span data-ttu-id="38f63-141">Om du vill referera till ett alias från en annan plats använder du `Cert:` enhets namnet i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="38f63-141">To reference an alias from another location, use the `Cert:` drive name in the path.</span></span>

```powershell
PS Cert:\> Set-Location -Path LocalMachine\Root
```

<span data-ttu-id="38f63-142">Om du vill återgå till en fil systemen het skriver du enhetens namn.</span><span class="sxs-lookup"><span data-stu-id="38f63-142">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="38f63-143">Skriv till exempel:</span><span class="sxs-lookup"><span data-stu-id="38f63-143">For example, type:</span></span>

```powershell
Set-Location C:
```

> [!NOTE]
> <span data-ttu-id="38f63-144">PowerShell använder alias för att ge dig ett välbekant sätt att arbeta med providerns sökvägar.</span><span class="sxs-lookup"><span data-stu-id="38f63-144">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="38f63-145">Kommandon som `dir` och `ls` är nu alias för [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` är ett alias för [set-location](xref:Microsoft.PowerShell.Management.Set-Location).</span><span class="sxs-lookup"><span data-stu-id="38f63-145">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location).</span></span>
> <span data-ttu-id="38f63-146">och `pwd` är ett alias för [Get-location](xref:Microsoft.PowerShell.Management.Get-Location).</span><span class="sxs-lookup"><span data-stu-id="38f63-146">and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

## <a name="displaying-the-contents-of-the-cert-drive"></a><span data-ttu-id="38f63-147">Visar innehållet i certifikatet: enhet</span><span class="sxs-lookup"><span data-stu-id="38f63-147">Displaying the Contents of the Cert: drive</span></span>

<span data-ttu-id="38f63-148">Detta kommando använder `Get-ChildItem` cmdleten för att Visa certifikat arkiven på CurrentUser-certifikatets lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="38f63-148">This command uses the `Get-ChildItem` cmdlet to display the certificate stores in the CurrentUser certificate store location.</span></span>

<span data-ttu-id="38f63-149">Om du inte är i `Cert:` enheten använder du en absolut sökväg.</span><span class="sxs-lookup"><span data-stu-id="38f63-149">If you are not in the `Cert:` drive, use an absolute path.</span></span>

```powershell
PS Cert:\CurrentUser\> Get-ChildItem
```

### <a name="displaying-certificate-properties-within-the-cert-drive"></a><span data-ttu-id="38f63-150">Visar certifikat egenskaper inom certifikatet: enhet</span><span class="sxs-lookup"><span data-stu-id="38f63-150">Displaying certificate properties within the Cert: drive</span></span>

<span data-ttu-id="38f63-151">Det här exemplet hämtar ett certifikat med `Get-Item` och lagrar det i en variabel.</span><span class="sxs-lookup"><span data-stu-id="38f63-151">This example gets a certificate with `Get-Item` and stores it in a variable.</span></span>
<span data-ttu-id="38f63-152">Exemplet visar de nya certifikat skript egenskaperna ( **DnsNameList** , **EnhancedKeyUsageList** , **SendAsTrustedIssuer** ) med `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="38f63-152">The example shows the new certificate script properties ( **DnsNameList** , **EnhancedKeyUsageList** , **SendAsTrustedIssuer** ) using `Select-Object`.</span></span>

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

### <a name="find-all-codesigning-certificates"></a><span data-ttu-id="38f63-153">Hitta alla samdesignande certifikat</span><span class="sxs-lookup"><span data-stu-id="38f63-153">Find all CodeSigning certificates</span></span>

<span data-ttu-id="38f63-154">Detta kommando använder parametrarna **CodeSigningCert** och **rekursivt** för `Get-ChildItem` cmdleten för att hämta alla certifikat på datorn som har kod signerings auktoritet.</span><span class="sxs-lookup"><span data-stu-id="38f63-154">This command uses the **CodeSigningCert** and **Recurse** parameters of the `Get-ChildItem` cmdlet to get all of the certificates on the computer that have code-signing authority.</span></span>

```powershell
Get-ChildItem -Path cert: -CodeSigningCert -Recurse
```

### <a name="find-expired-certificates"></a><span data-ttu-id="38f63-155">Hitta utgångna certifikat</span><span class="sxs-lookup"><span data-stu-id="38f63-155">Find expired certificates</span></span>

<span data-ttu-id="38f63-156">Det här kommandot använder **ExpiringInDays** -parametern för `Get-ChildItem` cmdleten för att hämta certifikat som upphör att gälla inom de närmaste 30 dagarna.</span><span class="sxs-lookup"><span data-stu-id="38f63-156">This command uses the **ExpiringInDays** parameter of the `Get-ChildItem` cmdlet to get certificates that will expire within the next 30 days.</span></span>

```powershell
Get-ChildItem -Path cert:\LocalMachine\WebHosting -ExpiringInDays 30
```

### <a name="find-server-ssl-certificates"></a><span data-ttu-id="38f63-157">Hitta Server SSL-certifikat</span><span class="sxs-lookup"><span data-stu-id="38f63-157">Find Server SSL Certificates</span></span>

<span data-ttu-id="38f63-158">Det här kommandot använder **SSLServerAuthentication** -parametern för `Get-ChildItem` cmdleten för att hämta alla Server-SSL-certifikat i butikerna My och webvärding.</span><span class="sxs-lookup"><span data-stu-id="38f63-158">This command uses the **SSLServerAuthentication** parameter of the `Get-ChildItem` cmdlet to get all Server SSL Certificates in the My and WebHosting stores.</span></span>

```powershell
Get-ChildItem -Path cert:\LocalMachine\My, cert:\LocalMachine\WebHosting `
  -SSLServerAuthentication
```

### <a name="find-expired-certificates-on-remote-computers"></a><span data-ttu-id="38f63-159">Hitta utgångna certifikat på fjärrdatorer</span><span class="sxs-lookup"><span data-stu-id="38f63-159">Find expired certificates on remote computers</span></span>

<span data-ttu-id="38f63-160">Det här kommandot använder `Invoke-Command` cmdleten för att köra ett `Get-ChildItem` kommando på datorerna SRV01 och Srv02.</span><span class="sxs-lookup"><span data-stu-id="38f63-160">This command uses the `Invoke-Command` cmdlet to run a `Get-ChildItem` command on the Srv01 and Srv02 computers.</span></span> <span data-ttu-id="38f63-161">Värdet noll (0) i parametern **ExpiringInDays** hämtar certifikat på de SRV01-och Srv02-datorer som har upphört att gälla.</span><span class="sxs-lookup"><span data-stu-id="38f63-161">A value of zero (0) in the **ExpiringInDays** parameter gets certificates on the Srv01 and Srv02 computers that have expired.</span></span>

```powershell
Invoke-Command -ComputerName Srv01, Srv02 {Get-ChildItem -Path cert:\* `
  -Recurse -ExpiringInDays 0}
```

### <a name="combining-filters-to-find-a-specific-set-of-certificates"></a><span data-ttu-id="38f63-162">Kombinera filter för att hitta en bestämd uppsättning certifikat</span><span class="sxs-lookup"><span data-stu-id="38f63-162">Combining filters to find a specific set of certificates</span></span>

<span data-ttu-id="38f63-163">Det här kommandot hämtar alla certifikat på LocalMachine Store-platsen som har följande attribut:</span><span class="sxs-lookup"><span data-stu-id="38f63-163">This command gets all certificates in the LocalMachine store location that have the following attributes:</span></span>

- <span data-ttu-id="38f63-164">"Fabrikam" i deras DNS-namn</span><span class="sxs-lookup"><span data-stu-id="38f63-164">"fabrikam" in their DNS name</span></span>
- <span data-ttu-id="38f63-165">"Klientautentisering" i deras EKU</span><span class="sxs-lookup"><span data-stu-id="38f63-165">"Client Authentication" in their EKU</span></span>
- <span data-ttu-id="38f63-166">ett värde för `$true` egenskapen **SendAsTrustedIssuer**</span><span class="sxs-lookup"><span data-stu-id="38f63-166">a value of `$true` for the **SendAsTrustedIssuer** property</span></span>
- <span data-ttu-id="38f63-167">förfaller inte inom de närmaste 30 dagarna.</span><span class="sxs-lookup"><span data-stu-id="38f63-167">do not expire within the next 30 days.</span></span>

<span data-ttu-id="38f63-168">Egenskapen **NotAfter** lagrar certifikatets förfallo datum.</span><span class="sxs-lookup"><span data-stu-id="38f63-168">The **NotAfter** property stores the certificate expiration date.</span></span>

```powershell
[DateTime] $ValidThrough = (Get-Date) + (New-TimeSpan -Days 30)
Get-ChildItem -Path cert:\* -Recurse -DNSName "*fabrikam*" `
  -EKU "*Client Authentication*" | Where-Object {
                                     $_.SendAsTrustedIssuer -and `
                                     $_.NotAfter -gt $ValidThrough
                                   }
```

## <a name="opening-the-certificates-mmc-snap-in"></a><span data-ttu-id="38f63-169">Öppna MMC-snapin-modulen certifikat</span><span class="sxs-lookup"><span data-stu-id="38f63-169">Opening the Certificates MMC Snap-in</span></span>

<span data-ttu-id="38f63-170">`Invoke-Item`Cmdlet: en använder standard programmet för att öppna en sökväg som du anger.</span><span class="sxs-lookup"><span data-stu-id="38f63-170">The `Invoke-Item` cmdlet will use the default application to open a path you specify.</span></span> <span data-ttu-id="38f63-171">För certifikat är standard programmet MMC-snapin-modulen certifikat.</span><span class="sxs-lookup"><span data-stu-id="38f63-171">For certificates, the default application is the Certificates MMC snap-in.</span></span>

<span data-ttu-id="38f63-172">Det här kommandot öppnar MMC-snapin-modulen certifikat för att hantera det angivna certifikatet.</span><span class="sxs-lookup"><span data-stu-id="38f63-172">This command opens the Certificates MMC snap-in to manage the specified certificate.</span></span>

```powershell
Invoke-Item cert:\CurrentUser\my\6B8223358119BB08840DEE50FD8AF9EA776CE66B
```

## <a name="copying-certificates"></a><span data-ttu-id="38f63-173">Kopiera certifikat</span><span class="sxs-lookup"><span data-stu-id="38f63-173">Copying Certificates</span></span>

<span data-ttu-id="38f63-174">Kopiering av certifikat stöds inte av **certifikat** leverantören.</span><span class="sxs-lookup"><span data-stu-id="38f63-174">Copying certificates is not supported by the **Certificate** provider.</span></span> <span data-ttu-id="38f63-175">När du försöker kopiera ett certifikat visas det här felet.</span><span class="sxs-lookup"><span data-stu-id="38f63-175">When you attempt to copy a certificate, you see this error.</span></span>

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

## <a name="moving-certificates"></a><span data-ttu-id="38f63-176">Flytta certifikat</span><span class="sxs-lookup"><span data-stu-id="38f63-176">Moving Certificates</span></span>

### <a name="move-all-ssl-server-authentication-certs-to-the-webhosting-store"></a><span data-ttu-id="38f63-177">Flytta alla SSL-certifikat för serverautentisering till webbvärds arkivet</span><span class="sxs-lookup"><span data-stu-id="38f63-177">Move all SSL Server authentication certs to the WebHosting store</span></span>

<span data-ttu-id="38f63-178">Det här kommandot använder `Move-Item` cmdleten för att flytta ett certifikat från My Store till webb värd arkivet.</span><span class="sxs-lookup"><span data-stu-id="38f63-178">This command uses the `Move-Item` cmdlet to move a certificate from the My store to the WebHosting store.</span></span>

<span data-ttu-id="38f63-179">`Move-Item` flyttar inte certifikat Arkiv och kommer inte att flytta certifikat till en annan lagrings plats, till exempel att flytta ett certifikat från LocalMachine till CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="38f63-179">`Move-Item` will not move certificate stores and it will not move certificates to a different store location, such as moving a certificate from LocalMachine to CurrentUser.</span></span> <span data-ttu-id="38f63-180">`Move-Item`Cmdleten flyttar certifikat, men flyttar inte privata nycklar.</span><span class="sxs-lookup"><span data-stu-id="38f63-180">The `Move-Item` cmdlet moves certificates, but it does not move private keys.</span></span>

<span data-ttu-id="38f63-181">Det här kommandot använder **SSLServerAuthentication** -parametern för `Get-ChildItem` cmdleten för att hämta certifikat för SSL-serverautentisering i mitt certifikat arkiv.</span><span class="sxs-lookup"><span data-stu-id="38f63-181">This command uses the **SSLServerAuthentication** parameter of the `Get-ChildItem` cmdlet to get SSL server authentication certificates in the MY certificate store.</span></span>

<span data-ttu-id="38f63-182">De returnerade certifikaten är skickas till `Move-Item` -cmdleten, som flyttar certifikaten till värd lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="38f63-182">The returned certificates are piped to the `Move-Item` cmdlet, which moves the certificates to the WebHosting store.</span></span>

```powershell
Get-ChildItem cert:\LocalMachine\My -SSLServerAuthentication | Move-Item `
  -Destination cert:\LocalMachine\WebHosting
```

## <a name="deleting-certificates-and-private-keys"></a><span data-ttu-id="38f63-183">Ta bort certifikat och privata nycklar</span><span class="sxs-lookup"><span data-stu-id="38f63-183">Deleting Certificates and Private Keys</span></span>

<span data-ttu-id="38f63-184">`Remove-Item`Cmdleten tar bort de certifikat som du anger.</span><span class="sxs-lookup"><span data-stu-id="38f63-184">The `Remove-Item` cmdlet will remove certificates that you specify.</span></span> <span data-ttu-id="38f63-185">Den `-DeleteKey` dynamiska parametern tar bort den privata nyckeln.</span><span class="sxs-lookup"><span data-stu-id="38f63-185">The `-DeleteKey` dynamic parameter deletes the private key.</span></span>

### <a name="delete-a-certificate-from-the-ca-store"></a><span data-ttu-id="38f63-186">Ta bort ett certifikat från CA-butiken</span><span class="sxs-lookup"><span data-stu-id="38f63-186">Delete a Certificate from the CA store</span></span>

<span data-ttu-id="38f63-187">Det här kommandot tar bort ett certifikat från CA-certifikatarkivet, men lämnar den tillhör ande privata nyckeln intakt.</span><span class="sxs-lookup"><span data-stu-id="38f63-187">This command deletes a certificate from the CA certificate store, but leaves the associated private key intact.</span></span>

<span data-ttu-id="38f63-188">I `Cert:` enheten `Remove-Item` stöder cmdleten bara parametrarna **DeleteKey** , **Path** , **whatIf** och **Confirm** .</span><span class="sxs-lookup"><span data-stu-id="38f63-188">In the `Cert:` drive, the `Remove-Item` cmdlet supports only the **DeleteKey** , **Path** , **WhatIf** , and **Confirm** parameters.</span></span> <span data-ttu-id="38f63-189">Alla andra parametrar ignoreras.</span><span class="sxs-lookup"><span data-stu-id="38f63-189">All other parameters are ignored.</span></span>

```powershell
Remove-Item cert:\LocalMachine\CA\5DDC44652E62BF9AA1116DC41DE44AB47C87BDD0
```

### <a name="delete-a-certificate-using-a-wildcards-in-the-dns-name"></a><span data-ttu-id="38f63-190">Ta bort ett certifikat med jokertecken i DNS-namnet</span><span class="sxs-lookup"><span data-stu-id="38f63-190">Delete a Certificate using a wildcards in the DNS name</span></span>

<span data-ttu-id="38f63-191">Det här kommandot tar bort alla certifikat som har ett DNS-namn som innehåller "Fabrikam".</span><span class="sxs-lookup"><span data-stu-id="38f63-191">This command deletes all certificates that have a DNS name that contains "Fabrikam".</span></span> <span data-ttu-id="38f63-192">Den använder **DNSName** -parametern för `Get-ChildItem` cmdleten för att hämta certifikaten och `Remove-Item` cmdleten för att ta bort dem.</span><span class="sxs-lookup"><span data-stu-id="38f63-192">It uses the **DNSName** parameter of the `Get-ChildItem` cmdlet to get the certificates and the `Remove-Item` cmdlet to delete them.</span></span>

```powershell
Get-ChildItem -Path cert:\LocalMachine -DnsName *Fabrikam* | Remove-Item
```

### <a name="delete-private-keys-from-a-remote-computer"></a><span data-ttu-id="38f63-193">Ta bort privata nycklar från en fjärran sluten dator</span><span class="sxs-lookup"><span data-stu-id="38f63-193">Delete private keys from a remote computer</span></span>

<span data-ttu-id="38f63-194">Den här serien med kommandon aktiverar delegering och tar sedan bort certifikatet och den tillhör ande privata nyckeln på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="38f63-194">This series of commands enables delegation and then deletes the certificate and associated private key on a remote computer.</span></span> <span data-ttu-id="38f63-195">Om du vill ta bort en privat nyckel på en fjärrdator måste du använda delegerade autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="38f63-195">To delete a private key on a remote computer, you must use delegated credentials.</span></span>

<span data-ttu-id="38f63-196">Använd `Enable-WSManCredSSP` cmdleten för att aktivera autentisering av Credential Security Service Provider (CredSSP) på en klient på den lokala S1-datorn.</span><span class="sxs-lookup"><span data-stu-id="38f63-196">Use the `Enable-WSManCredSSP` cmdlet to enable Credential Security Service Provider (CredSSP) authentication on a client on the S1 remote computer.</span></span>
<span data-ttu-id="38f63-197">CredSSP tillåter delegerad autentisering.</span><span class="sxs-lookup"><span data-stu-id="38f63-197">CredSSP permits delegated authentication.</span></span>

```powershell
Enable-WSManCredSSP -Role Client -DelegateComputer S1
```

<span data-ttu-id="38f63-198">Använd `Connect-WSMan` cmdleten för att ansluta S1-datorn till WinRM-tjänsten på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="38f63-198">Use the `Connect-WSMan` cmdlet to connect the S1 computer to the WinRM service on the local computer.</span></span> <span data-ttu-id="38f63-199">När det här kommandot har slutförts visas S1-datorn på den lokala `WSMan:` enheten i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="38f63-199">When this command completes, the S1 computer appears in the local `WSMan:` drive in PowerShell.</span></span>

```powershell
Connect-WSMan -ComputerName S1 -Credential Domain01\Admin01
```

<span data-ttu-id="38f63-200">Nu kan du använda cmdleten Set-Item i WSMan: Drive för att aktivera CredSSP-attributet för WinRM-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="38f63-200">Now, you can use the Set-Item cmdlet in the WSMan: drive to enable the CredSSP attribute for the WinRM service.</span></span>

```powershell
Set-Item -Path WSMan:\S1\Service\Auth\CredSSP -Value $true
```

<span data-ttu-id="38f63-201">Starta en fjärran sluten session på S1-datorn med `New-PSSession` cmdleten och ange CredSSP-autentisering.</span><span class="sxs-lookup"><span data-stu-id="38f63-201">Start a remote session on the s1 computer using the `New-PSSession` cmdlet, and specify CredSSP authentication.</span></span> <span data-ttu-id="38f63-202">Sparar sessionen i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="38f63-202">Saves the session in the `$s` variable.</span></span>

```powershell
$s  = New-PSSession S1 -Authentication CredSSP -Credential Domain01\Admin01
```

<span data-ttu-id="38f63-203">Använd slutligen `Invoke-Command` cmdleten för att köra ett `Remove-Item` kommando i sessionen i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="38f63-203">Finally, use the `Invoke-Command` cmdlet to run a `Remove-Item` command in the session in the `$s` variable.</span></span> <span data-ttu-id="38f63-204">`Remove-Item`Kommandot använder parametern **DeleteKey** för att ta bort den privata nyckeln tillsammans med det angivna certifikatet.</span><span class="sxs-lookup"><span data-stu-id="38f63-204">The `Remove-Item` command uses the **DeleteKey** parameter to remove the private key along with the specified certificate.</span></span>

```powershell
Invoke-Command -Session $s { Remove-Item `
  -Path cert:\LocalMachine\My\D2D38EBA60CAA1C12055A2E1C83B15AD450110C2 `
  -DeleteKey
  }
```

### <a name="delete-expired-certificates"></a><span data-ttu-id="38f63-205">Ta bort utgångna certifikat</span><span class="sxs-lookup"><span data-stu-id="38f63-205">Delete expired Certificates</span></span>

<span data-ttu-id="38f63-206">Det här kommandot använder **ExpiringInDays** -parametern för `Get-ChildItem` cmdleten med värdet 0 för att hämta certifikat i den webvärdskaps lager som har upphört att gälla.</span><span class="sxs-lookup"><span data-stu-id="38f63-206">This command uses the **ExpiringInDays** parameter of the `Get-ChildItem` cmdlet with a value of 0 to get certificates in the WebHosting store that have expired.</span></span>

<span data-ttu-id="38f63-207">Variabeln som innehåller de returnerade certifikaten är skickas till `Remove-Item` cmdleten, som tar bort dem.</span><span class="sxs-lookup"><span data-stu-id="38f63-207">The variable containing the returned certificates is piped to the `Remove-Item` cmdlet, which deletes them.</span></span> <span data-ttu-id="38f63-208">Kommandot använder parametern **DeleteKey** för att ta bort den privata nyckeln tillsammans med certifikatet.</span><span class="sxs-lookup"><span data-stu-id="38f63-208">The command uses the **DeleteKey** parameter to delete the private key along with the certificate.</span></span>

```powershell
$expired = Get-ChildItem cert:\LocalMachine\WebHosting -ExpiringInDays 0
$expired | Remove-Item -DeleteKey
```

## <a name="creating-certificates"></a><span data-ttu-id="38f63-209">Skapa certifikat</span><span class="sxs-lookup"><span data-stu-id="38f63-209">Creating Certificates</span></span>

<span data-ttu-id="38f63-210">`New-Item`Cmdleten skapar inga nya certifikat i **certifikat** leverantören.</span><span class="sxs-lookup"><span data-stu-id="38f63-210">The `New-Item` cmdlet does not create new certificates in the **Certificate** provider.</span></span> <span data-ttu-id="38f63-211">Använd cmdleten [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) för att skapa ett certifikat för test ändamål.</span><span class="sxs-lookup"><span data-stu-id="38f63-211">Use the [New-SelfSignedCertificate](/powershell/module/pkiclient/new-selfsignedcertificate) cmdlet to create a certificate for testing purposes.</span></span>

## <a name="creating-certificate-stores"></a><span data-ttu-id="38f63-212">Skapa certifikat Arkiv</span><span class="sxs-lookup"><span data-stu-id="38f63-212">Creating Certificate Stores</span></span>

<span data-ttu-id="38f63-213">I cert: Drive, `New-Item` skapar cmdleten certifikat Arkiv på platsen för LocalMachine-platsen.</span><span class="sxs-lookup"><span data-stu-id="38f63-213">In the Cert: drive, the `New-Item` cmdlet creates certificate stores in the LocalMachine store location.</span></span> <span data-ttu-id="38f63-214">Den har stöd för parametrarna **namn** , **sökväg** , **whatIf** och **Confirm** .</span><span class="sxs-lookup"><span data-stu-id="38f63-214">It supports the **Name** , **Path** , **WhatIf** , and **Confirm** parameters.</span></span> <span data-ttu-id="38f63-215">Alla andra parametrar ignoreras.</span><span class="sxs-lookup"><span data-stu-id="38f63-215">All other parameters are ignored.</span></span> <span data-ttu-id="38f63-216">Kommandot returnerar en **system. Security. Cryptography. X509Certificates. X509Store** som representerar det nya certifikat arkivet.</span><span class="sxs-lookup"><span data-stu-id="38f63-216">The command returns a **System.Security.Cryptography.X509Certificates.X509Store** that represents the new certificate store.</span></span>

<span data-ttu-id="38f63-217">Det här kommandot skapar ett nytt certifikat Arkiv med namnet "CustomStore" på LocalMachine-lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="38f63-217">This command creates a new certificate store named "CustomStore" in the LocalMachine store location.</span></span>

```powershell
New-Item -Path cert:\LocalMachine\CustomStore
```

### <a name="create-a-new-certificate-store-on-a-remote-computer"></a><span data-ttu-id="38f63-218">Skapa ett nytt certifikat Arkiv på en fjärran sluten dator</span><span class="sxs-lookup"><span data-stu-id="38f63-218">Create a new certificate store on a remote computer</span></span>

<span data-ttu-id="38f63-219">Det här kommandot skapar ett nytt certifikat Arkiv med namnet "HostingStore" på LocalMachine Store-platsen på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="38f63-219">This command creates a new certificate store named "HostingStore" in the LocalMachine store location on the Server01 computer.</span></span>

<span data-ttu-id="38f63-220">Kommandot använder `Invoke-Command` cmdleten för att köra ett `New-Item` kommando på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="38f63-220">The command uses the `Invoke-Command` cmdlet to run a `New-Item` command on the Server01 computer.</span></span> <span data-ttu-id="38f63-221">Kommandot returnerar en **system. Security. Cryptography. X509Certificates. X509Store** som representerar det nya certifikat arkivet.</span><span class="sxs-lookup"><span data-stu-id="38f63-221">The command returns a **System.Security.Cryptography.X509Certificates.X509Store** that represents the new certificate store.</span></span>

```powershell
Invoke-Command { New-Item -Path cert:\LocalMachine\CustomStore } `
  -ComputerName Server01
```

## <a name="creating-client-certificates-for-ws-man"></a><span data-ttu-id="38f63-222">Skapa klient certifikat för WS-Man</span><span class="sxs-lookup"><span data-stu-id="38f63-222">Creating Client Certificates for WS-Man</span></span>

<span data-ttu-id="38f63-223">Det här kommandot skapar en **ClientCertificate** -post som kan användas av **WS-Management-** klienten.</span><span class="sxs-lookup"><span data-stu-id="38f63-223">This command creates **ClientCertificate** entry that can be used by the **WS-Management** client.</span></span> <span data-ttu-id="38f63-224">Den nya **ClientCertificate** visas under katalogen **ClientCertificate** som "ClientCertificate_1234567890".</span><span class="sxs-lookup"><span data-stu-id="38f63-224">The new **ClientCertificate** will show up under the **ClientCertificate** directory as "ClientCertificate_1234567890".</span></span> <span data-ttu-id="38f63-225">Alla parametrar är obligatoriska.</span><span class="sxs-lookup"><span data-stu-id="38f63-225">All of the parameters are mandatory.</span></span> <span data-ttu-id="38f63-226">**Utfärdaren** måste vara tumavtryck för utfärdarcertifikatet.</span><span class="sxs-lookup"><span data-stu-id="38f63-226">The **Issuer** needs to be thumbprint of the issuers certificate.</span></span>

```powershell
$cred = Get-Credential
New-Item -Path WSMan:\localhost\ClientCertificate `
         -Issuer 1b3fd224d66c6413fe20d21e38b304226d192dfe `
         -URI wmicimv2/* -Credential $cred
```

## <a name="deleting-certificate-stores"></a><span data-ttu-id="38f63-227">Ta bort certifikat Arkiv</span><span class="sxs-lookup"><span data-stu-id="38f63-227">Deleting Certificate Stores</span></span>

### <a name="delete-a-certificate-store-from-a-remote-computer"></a><span data-ttu-id="38f63-228">Ta bort ett certifikat arkiv från en fjärran sluten dator</span><span class="sxs-lookup"><span data-stu-id="38f63-228">Delete a certificate store from a remote computer</span></span>

<span data-ttu-id="38f63-229">Det här kommandot använder `Invoke-Command` cmdleten för att köra ett `Remove-Item` kommando på datorerna S1 och S2.</span><span class="sxs-lookup"><span data-stu-id="38f63-229">This command uses the `Invoke-Command` cmdlet to run a `Remove-Item` command on the S1 and S2 computers.</span></span> <span data-ttu-id="38f63-230">`Remove-Item`Kommandot innehåller parametern **rekursivt** , som tar bort certifikaten i arkivet innan det tas bort.</span><span class="sxs-lookup"><span data-stu-id="38f63-230">The `Remove-Item` command includes the **Recurse** parameter, which deletes the certificates in the store before it deletes the store.</span></span>

```powershell
Invoke-Command { Remove-Item -Path cert:\LocalMachine\TestStore -Recurse } `
  -ComputerName S1, S2
```

## <a name="dynamic-parameters"></a><span data-ttu-id="38f63-231">Dynamiska parametrar</span><span class="sxs-lookup"><span data-stu-id="38f63-231">Dynamic parameters</span></span>

<span data-ttu-id="38f63-232">Dynamiska parametrar är cmdlet-parametrar som läggs till av en PowerShell-Provider och är bara tillgängliga när cmdleten används i den provider-aktiverade enheten.</span><span class="sxs-lookup"><span data-stu-id="38f63-232">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span> <span data-ttu-id="38f63-233">Dessa parametrar är giltiga i alla under kataloger i certifikat leverantören, men gäller endast för certifikat.</span><span class="sxs-lookup"><span data-stu-id="38f63-233">These parameters are valid in all subdirectories of the Certificate provider, but are effective only on certificates.</span></span>

> [!NOTE]
> <span data-ttu-id="38f63-234">Parametrar som utför filtrering mot `EnhancedKeyUsageList` egenskapen returnerar även objekt med ett tomt `EnhancedKeyUsageList` egenskaps värde.</span><span class="sxs-lookup"><span data-stu-id="38f63-234">Parameters that perform filtering against the `EnhancedKeyUsageList` property also return items with an empty `EnhancedKeyUsageList` property value.</span></span>
> <span data-ttu-id="38f63-235">Certifikat som har en tom **EnhancedKeyUsageList** kan användas i alla syfte.</span><span class="sxs-lookup"><span data-stu-id="38f63-235">Certificates that have an empty **EnhancedKeyUsageList** can be used for all purposes.</span></span>

<span data-ttu-id="38f63-236">Följande parametrar för certifikat leverantörer har introducerats om i PowerShell 7,1.</span><span class="sxs-lookup"><span data-stu-id="38f63-236">The following Certificate provider parameters were reintroduced in PowerShell 7.1.</span></span>

- <span data-ttu-id="38f63-237">DNSName</span><span class="sxs-lookup"><span data-stu-id="38f63-237">DNSName</span></span>
- <span data-ttu-id="38f63-238">DocumentEncryptionCert</span><span class="sxs-lookup"><span data-stu-id="38f63-238">DocumentEncryptionCert</span></span>
- <span data-ttu-id="38f63-239">ANVÄNDNING</span><span class="sxs-lookup"><span data-stu-id="38f63-239">EKU</span></span>
- <span data-ttu-id="38f63-240">ExpiringInDays</span><span class="sxs-lookup"><span data-stu-id="38f63-240">ExpiringInDays</span></span>
- <span data-ttu-id="38f63-241">SSLServerAuthentication</span><span class="sxs-lookup"><span data-stu-id="38f63-241">SSLServerAuthentication</span></span>

### <a name="codesigningcert-systemmanagementautomationswitchparameter"></a><span data-ttu-id="38f63-242">CodeSigningCert <system. Management. Automation. SwitchParameter></span><span class="sxs-lookup"><span data-stu-id="38f63-242">CodeSigningCert <System.Management.Automation.SwitchParameter></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="38f63-243">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="38f63-243">Cmdlets supported</span></span>

- [<span data-ttu-id="38f63-244">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="38f63-244">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)

- [<span data-ttu-id="38f63-245">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="38f63-245">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="38f63-246">Den här parametern hämtar certifikat som har "kod signering" i deras värde för egenskapen **EnhancedKeyUsageList** .</span><span class="sxs-lookup"><span data-stu-id="38f63-246">This parameter gets certificates that have "Code Signing" in their **EnhancedKeyUsageList** property value.</span></span>

### <a name="deletekey-systemmanagementautomationswitchparameter"></a><span data-ttu-id="38f63-247">DeleteKey <system. Management. Automation. SwitchParameter></span><span class="sxs-lookup"><span data-stu-id="38f63-247">DeleteKey <System.Management.Automation.SwitchParameter></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="38f63-248">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="38f63-248">Cmdlets supported</span></span>

- [<span data-ttu-id="38f63-249">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="38f63-249">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)

<span data-ttu-id="38f63-250">Den här parametern tar bort den tillhör ande privata nyckeln när certifikatet tas bort.</span><span class="sxs-lookup"><span data-stu-id="38f63-250">This parameter deletes the associated private key when it deletes the certificate.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38f63-251">Om du vill ta bort en privat nyckel som är kopplad till ett användar certifikat i `Cert:\CurrentUser` arkivet på en fjärrdator måste du använda delegerade autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="38f63-251">To delete a private key that is associated with a user certificate in the `Cert:\CurrentUser` store on a remote computer, you must use delegated credentials.</span></span> <span data-ttu-id="38f63-252">`Invoke-Command`Cmdleten stöder delegering av autentiseringsuppgifter med hjälp av **CredSSP** -parametern.</span><span class="sxs-lookup"><span data-stu-id="38f63-252">The `Invoke-Command` cmdlet supports credential delegation using the **CredSSP** parameter.</span></span> <span data-ttu-id="38f63-253">Du bör överväga eventuella säkerhets risker innan du använder `Remove-Item` med `Invoke-Command` och delegering av autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="38f63-253">You should consider any security risks before using `Remove-Item` with `Invoke-Command` and credential delegation.</span></span>

<span data-ttu-id="38f63-254">Den här parametern introducerades i PowerShell 7,1</span><span class="sxs-lookup"><span data-stu-id="38f63-254">This parameter was reintroduced in PowerShell 7.1</span></span>

### <a name="dnsname-microsoftpowershellcommandsdnsnamerepresentation"></a><span data-ttu-id="38f63-255">DnsName <Microsoft. PowerShell. commands. DnsNameRepresentation></span><span class="sxs-lookup"><span data-stu-id="38f63-255">DnsName <Microsoft.PowerShell.Commands.DnsNameRepresentation></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="38f63-256">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="38f63-256">Cmdlets supported</span></span>

- [<span data-ttu-id="38f63-257">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="38f63-257">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="38f63-258">Den här parametern hämtar certifikat som har det angivna domän namnet eller namn mönstret i certifikatets egenskap **DNSNameList** .</span><span class="sxs-lookup"><span data-stu-id="38f63-258">This parameter gets certificates that have the specified domain name or name pattern in the **DNSNameList** property of the certificate.</span></span> <span data-ttu-id="38f63-259">Värdet för den här parametern kan antingen vara "Unicode" eller "ASCII".</span><span class="sxs-lookup"><span data-stu-id="38f63-259">The value of this parameter can either be "Unicode" or "ASCII".</span></span> <span data-ttu-id="38f63-260">Punycode-värden konverteras till Unicode.</span><span class="sxs-lookup"><span data-stu-id="38f63-260">Punycode values are converted to Unicode.</span></span> <span data-ttu-id="38f63-261">Jokertecken ( `*` ) är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="38f63-261">Wildcard characters (`*`) are permitted.</span></span>

<span data-ttu-id="38f63-262">Den här parametern introducerades i PowerShell 7,1</span><span class="sxs-lookup"><span data-stu-id="38f63-262">This parameter was reintroduced in PowerShell 7.1</span></span>

### <a name="documentencryptioncert-systemmanagementautomationswitchparameter"></a><span data-ttu-id="38f63-263">DocumentEncryptionCert <system. Management. Automation. SwitchParameter></span><span class="sxs-lookup"><span data-stu-id="38f63-263">DocumentEncryptionCert <System.Management.Automation.SwitchParameter></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="38f63-264">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="38f63-264">Cmdlets supported</span></span>

- [<span data-ttu-id="38f63-265">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="38f63-265">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)

- [<span data-ttu-id="38f63-266">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="38f63-266">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="38f63-267">Den här parametern hämtar certifikat med "dokument kryptering" i deras värde för egenskapen **EnhancedKeyUsageList** .</span><span class="sxs-lookup"><span data-stu-id="38f63-267">This parameter gets certificates that have "Document Encryption" in their **EnhancedKeyUsageList** property value.</span></span>

### <a name="eku-systemstring"></a><span data-ttu-id="38f63-268">EKU <system. String></span><span class="sxs-lookup"><span data-stu-id="38f63-268">EKU <System.String></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="38f63-269">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="38f63-269">Cmdlets supported</span></span>

- [<span data-ttu-id="38f63-270">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="38f63-270">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="38f63-271">Den här parametern hämtar certifikat som har den angivna texten eller text mönstret i `EnhancedKeyUsageList` certifikatets egenskap.</span><span class="sxs-lookup"><span data-stu-id="38f63-271">This parameter gets certificates that have the specified text or text pattern in the `EnhancedKeyUsageList` property of the certificate.</span></span> <span data-ttu-id="38f63-272">Jokertecken ( `*` ) är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="38f63-272">Wildcard characters (`*`) are permitted.</span></span> <span data-ttu-id="38f63-273">`EnhancedKeyUsageList`Egenskapen innehåller det egna namnet och OID-fälten i EKU.</span><span class="sxs-lookup"><span data-stu-id="38f63-273">The `EnhancedKeyUsageList` property contains the friendly name and the OID fields of the EKU.</span></span>

<span data-ttu-id="38f63-274">Den här parametern introducerades i PowerShell 7,1</span><span class="sxs-lookup"><span data-stu-id="38f63-274">This parameter was reintroduced in PowerShell 7.1</span></span>

### <a name="expiringindays-systemint32"></a><span data-ttu-id="38f63-275">ExpiringInDays <system. Int32></span><span class="sxs-lookup"><span data-stu-id="38f63-275">ExpiringInDays <System.Int32></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="38f63-276">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="38f63-276">Cmdlets supported</span></span>

- [<span data-ttu-id="38f63-277">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="38f63-277">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="38f63-278">Den här parametern hämtar certifikat som upphör att gälla inom eller före det angivna antalet dagar.</span><span class="sxs-lookup"><span data-stu-id="38f63-278">This parameter gets certificates that are expiring in or before the specified number of days.</span></span> <span data-ttu-id="38f63-279">Värdet 0 (noll) hämtar certifikat som har upphört att gälla.</span><span class="sxs-lookup"><span data-stu-id="38f63-279">A value of 0 (zero) gets certificates that have expired.</span></span>

<span data-ttu-id="38f63-280">Den här parametern introducerades i PowerShell 7,1</span><span class="sxs-lookup"><span data-stu-id="38f63-280">This parameter was reintroduced in PowerShell 7.1</span></span>

### <a name="itemtype-string"></a><span data-ttu-id="38f63-281">ItemType \<String\></span><span class="sxs-lookup"><span data-stu-id="38f63-281">ItemType \<String\></span></span>

<span data-ttu-id="38f63-282">Med den här parametern kan du ange vilken typ av objekt som skapas av `New-Item` .</span><span class="sxs-lookup"><span data-stu-id="38f63-282">This parameter allows you to specify the type of item created by `New-Item`.</span></span>

<span data-ttu-id="38f63-283">I en `Certificate` enhet tillåts följande värden:</span><span class="sxs-lookup"><span data-stu-id="38f63-283">In a `Certificate` drive, the following values are allowed:</span></span>

- <span data-ttu-id="38f63-284">Certifikat leverantör</span><span class="sxs-lookup"><span data-stu-id="38f63-284">Certificate Provider</span></span>
- <span data-ttu-id="38f63-285">Certifikat</span><span class="sxs-lookup"><span data-stu-id="38f63-285">Certificate</span></span>
- <span data-ttu-id="38f63-286">Lagringsplats</span><span class="sxs-lookup"><span data-stu-id="38f63-286">Store</span></span>
- <span data-ttu-id="38f63-287">StoreLocation</span><span class="sxs-lookup"><span data-stu-id="38f63-287">StoreLocation</span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="38f63-288">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="38f63-288">Cmdlets Supported</span></span>

- [<span data-ttu-id="38f63-289">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="38f63-289">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)

### <a name="sslserverauthentication-systemmanagementautomationswitchparameter"></a><span data-ttu-id="38f63-290">SSLServerAuthentication <system. Management. Automation. SwitchParameter></span><span class="sxs-lookup"><span data-stu-id="38f63-290">SSLServerAuthentication <System.Management.Automation.SwitchParameter></span></span>

#### <a name="cmdlets-supported"></a><span data-ttu-id="38f63-291">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="38f63-291">Cmdlets supported</span></span>

- [<span data-ttu-id="38f63-292">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="38f63-292">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

<span data-ttu-id="38f63-293">Hämtar endast Server certifikat för SSL-webbvärd.</span><span class="sxs-lookup"><span data-stu-id="38f63-293">Gets only server certificates for SSL web hosting.</span></span> <span data-ttu-id="38f63-294">Den här parametern hämtar certifikat som har "serverautentisering" i deras `EnhancedKeyUsageList` egenskaps värde.</span><span class="sxs-lookup"><span data-stu-id="38f63-294">This parameter gets certificates that have "Server Authentication" in their `EnhancedKeyUsageList` property value.</span></span>

<span data-ttu-id="38f63-295">Den här parametern introducerades i PowerShell 7,1</span><span class="sxs-lookup"><span data-stu-id="38f63-295">This parameter was reintroduced in PowerShell 7.1</span></span>

## <a name="script-properties"></a><span data-ttu-id="38f63-296">Skript egenskaper</span><span class="sxs-lookup"><span data-stu-id="38f63-296">Script properties</span></span>

<span data-ttu-id="38f63-297">Nya skript egenskaper har lagts till i **x509Certificate2** -objektet som representerar certifikaten för att göra det enkelt att söka efter och hantera certifikaten.</span><span class="sxs-lookup"><span data-stu-id="38f63-297">New script properties have been added to the **x509Certificate2** object that represents the certificates to make it easy to search and manage the certificates.</span></span>

- <span data-ttu-id="38f63-298">`DnsNameList`: Om du vill fylla i `DnsNameList` egenskapen kopierar certifikat leverantören innehållet från DNSName-posten i SubjectAlternativeName (San)-tillägget.</span><span class="sxs-lookup"><span data-stu-id="38f63-298">`DnsNameList`: To populate the `DnsNameList` property, the Certificate provider copies the content from the DNSName entry in the SubjectAlternativeName (SAN) extension.</span></span> <span data-ttu-id="38f63-299">Om SAN-tillägget är tomt fylls egenskapen i med innehåll från certifikatets ämnes fält.</span><span class="sxs-lookup"><span data-stu-id="38f63-299">If the SAN extension is empty, the property is populated with content from the Subject field of the certificate.</span></span>

- <span data-ttu-id="38f63-300">`EnhancedKeyUsageList`: Om du vill fylla i `EnhancedKeyUsageList` egenskapen kopierar certifikat leverantören OID-egenskaperna för fältet EnhancedKeyUsage (EKU) i certifikatet och skapar ett eget namn för det.</span><span class="sxs-lookup"><span data-stu-id="38f63-300">`EnhancedKeyUsageList`: To populate the `EnhancedKeyUsageList` property, the Certificate provider copies the OID properties of the EnhancedKeyUsage (EKU) field in the certificate and creates a friendly name for it.</span></span>

- <span data-ttu-id="38f63-301">`SendAsTrustedIssuer`: Om du vill fylla i `SendAsTrustedIssuer` egenskapen kopierar certifikat leverantören `SendAsTrustedIssuer` egenskapen från certifikatet.</span><span class="sxs-lookup"><span data-stu-id="38f63-301">`SendAsTrustedIssuer`: To populate the `SendAsTrustedIssuer` property, the Certificate provider copies the `SendAsTrustedIssuer` property from the certificate.</span></span>  <span data-ttu-id="38f63-302">Mer information finns i [hantering av betrodda utfärdare för klientautentisering](/windows-server/security/tls/what-s-new-in-tls-ssl-schannel-ssp-overview#BKMK_TrustedIssuers).</span><span class="sxs-lookup"><span data-stu-id="38f63-302">For more information see [Management of trusted issuers for client authentication](/windows-server/security/tls/what-s-new-in-tls-ssl-schannel-ssp-overview#BKMK_TrustedIssuers).</span></span>

<span data-ttu-id="38f63-303">Med de här nya funktionerna kan du söka efter certifikat baserat på deras DNS-namn och förfallo datum och särskilja certifikat för klient-och serverautentisering genom att värdet för egenskaperna för utökad nyckel användning (EKU) används.</span><span class="sxs-lookup"><span data-stu-id="38f63-303">These new features let you search for certificates based on their DNS names and expiration dates, and distinguish client and server authentication certificates by the value of their Enhanced Key Usage (EKU) properties.</span></span>

## <a name="using-the-pipeline"></a><span data-ttu-id="38f63-304">Använda pipelinen</span><span class="sxs-lookup"><span data-stu-id="38f63-304">Using the pipeline</span></span>

<span data-ttu-id="38f63-305">Provider-cmdletar accepterar pipeline-ininformation.</span><span class="sxs-lookup"><span data-stu-id="38f63-305">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="38f63-306">Du kan använda pipelinen för att förenkla uppgiften genom att skicka leverantörs data från en cmdlet till en annan provider-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="38f63-306">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span>
<span data-ttu-id="38f63-307">Mer information om hur du använder pipelinen med Provider-cmdletar finns i cmdlet-referenser som finns i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="38f63-307">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="38f63-308">Få hjälp</span><span class="sxs-lookup"><span data-stu-id="38f63-308">Getting help</span></span>

<span data-ttu-id="38f63-309">Från och med Windows PowerShell 3,0 kan du hämta anpassade hjälp avsnitt för provider-cmdletar som förklarar hur dessa cmdletar fungerar i en fil systemen het.</span><span class="sxs-lookup"><span data-stu-id="38f63-309">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="38f63-310">Om du vill få hjälp avsnitten som är anpassade för fil system enheten kör du ett [Get-Help-](xref:Microsoft.PowerShell.Core.Get-Help) kommando i en fil system enhet eller använder `-Path` parametern för `Get-Help` att ange en fil system enhet.</span><span class="sxs-lookup"><span data-stu-id="38f63-310">To get the help topics that are customized for the file system drive, run a [Get-Help](xref:Microsoft.PowerShell.Core.Get-Help) command in a file system drive or use the `-Path` parameter of `Get-Help` to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path cert:
```

## <a name="see-also"></a><span data-ttu-id="38f63-311">Se även</span><span class="sxs-lookup"><span data-stu-id="38f63-311">See also</span></span>

[<span data-ttu-id="38f63-312">about_Providers</span><span class="sxs-lookup"><span data-stu-id="38f63-312">about_Providers</span></span>](../../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="38f63-313">about_Signing</span><span class="sxs-lookup"><span data-stu-id="38f63-313">about_Signing</span></span>](../../Microsoft.PowerShell.Core/About/about_Signing.md)

[<span data-ttu-id="38f63-314">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="38f63-314">Get-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Get-AuthenticodeSignature)

[<span data-ttu-id="38f63-315">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="38f63-315">Set-AuthenticodeSignature</span></span>](xref:Microsoft.PowerShell.Security.Set-AuthenticodeSignature)

[<span data-ttu-id="38f63-316">Get-PfxCertificate</span><span class="sxs-lookup"><span data-stu-id="38f63-316">Get-PfxCertificate</span></span>](xref:Microsoft.PowerShell.Security.Get-PfxCertificate)
