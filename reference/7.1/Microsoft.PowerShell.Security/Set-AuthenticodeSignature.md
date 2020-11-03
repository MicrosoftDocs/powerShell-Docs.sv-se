---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 04/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/set-authenticodesignature?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-AuthenticodeSignature
ms.openlocfilehash: d4bddfb506a86cb36e61f94cabf6e24fadaed527
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263829"
---
# <span data-ttu-id="ada6b-103">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="ada6b-103">Set-AuthenticodeSignature</span></span>

## <span data-ttu-id="ada6b-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="ada6b-104">SYNOPSIS</span></span>
<span data-ttu-id="ada6b-105">Lägger till en [Authenticode](/windows-hardware/drivers/install/authenticode) -signatur i ett PowerShell-skript eller en annan fil.</span><span class="sxs-lookup"><span data-stu-id="ada6b-105">Adds an [Authenticode](/windows-hardware/drivers/install/authenticode) signature to a PowerShell script or other file.</span></span>

## <span data-ttu-id="ada6b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ada6b-106">SYNTAX</span></span>

### <span data-ttu-id="ada6b-107">ByPath (standard)</span><span class="sxs-lookup"><span data-stu-id="ada6b-107">ByPath (Default)</span></span>

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] [-FilePath] <String[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ada6b-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="ada6b-108">ByLiteralPath</span></span>

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] -LiteralPath <String[]>
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ada6b-109">ByContent</span><span class="sxs-lookup"><span data-stu-id="ada6b-109">ByContent</span></span>

```
Set-AuthenticodeSignature [-Certificate] <X509Certificate2> [-IncludeChain <String>]
 [-TimestampServer <String>] [-HashAlgorithm <String>] [-Force] -SourcePathOrExtension <String[]>
 -Content <Byte[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ada6b-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ada6b-110">DESCRIPTION</span></span>

<span data-ttu-id="ada6b-111">`Set-AuthenticodeSignature`Cmdleten lägger till en Authenticode-signatur till alla filer som stöder SIP (subject Interface Package).</span><span class="sxs-lookup"><span data-stu-id="ada6b-111">The `Set-AuthenticodeSignature` cmdlet adds an Authenticode signature to any file that supports Subject Interface Package (SIP).</span></span>

<span data-ttu-id="ada6b-112">I en PowerShell-skriptfil tar signaturen formen av ett textblock som anger slutet på de instruktioner som körs i skriptet.</span><span class="sxs-lookup"><span data-stu-id="ada6b-112">In a PowerShell script file, the signature takes the form of a block of text that indicates the end of the instructions that are executed in the script.</span></span> <span data-ttu-id="ada6b-113">Om det finns en signatur i filen när denna cmdlet körs, tas signaturen bort.</span><span class="sxs-lookup"><span data-stu-id="ada6b-113">If there is a signature in the file when this cmdlet runs, that signature is removed.</span></span>

## <span data-ttu-id="ada6b-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="ada6b-114">EXAMPLES</span></span>

### <span data-ttu-id="ada6b-115">Exempel 1 – signera ett skript med ett certifikat från det lokala certifikat arkivet</span><span class="sxs-lookup"><span data-stu-id="ada6b-115">Example 1 - Sign a script using a certificate from the local certificate store</span></span>

<span data-ttu-id="ada6b-116">De här kommandona hämtar ett kod signerings certifikat från PowerShell-certifikat leverantören och använder det för att signera ett PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="ada6b-116">These commands retrieve a code-signing certificate from the PowerShell certificate provider and use it to sign a PowerShell script.</span></span>

```powershell
$cert=Get-ChildItem -Path Cert:\CurrentUser\My -CodeSigningCert
Set-AuthenticodeSignature -FilePath PsTestInternet2.ps1 -Certificate $cert
```

<span data-ttu-id="ada6b-117">Det första kommandot använder `Get-ChildItem` cmdleten och PowerShell-certifikat leverantören för att hämta certifikaten i under `Cert:\CurrentUser\My` katalogen i certifikat arkivet.</span><span class="sxs-lookup"><span data-stu-id="ada6b-117">The first command uses the `Get-ChildItem` cmdlet and the PowerShell certificate provider to get the certificates in the `Cert:\CurrentUser\My` subdirectory of the certificate store.</span></span> <span data-ttu-id="ada6b-118">`Cert:`Enheten är den enhet som exponeras av certifikat leverantören.</span><span class="sxs-lookup"><span data-stu-id="ada6b-118">The `Cert:` drive is the drive exposed by the certificate provider.</span></span> <span data-ttu-id="ada6b-119">Parametern **CodeSigningCert** , som endast stöds av certifikat leverantören, begränsar de certifikat som hämtas till dem med kod signerings utfärdare.</span><span class="sxs-lookup"><span data-stu-id="ada6b-119">The **CodeSigningCert** parameter, which is supported only by the certificate provider, limits the certificates retrieved to those with code-signing authority.</span></span> <span data-ttu-id="ada6b-120">Kommandot lagrar resultatet i `$cert` variabeln.</span><span class="sxs-lookup"><span data-stu-id="ada6b-120">The command stores the result in the `$cert` variable.</span></span>

<span data-ttu-id="ada6b-121">Det andra kommandot använder `Set-AuthenticodeSignature` cmdleten för att signera `PSTestInternet2.ps1` skriptet.</span><span class="sxs-lookup"><span data-stu-id="ada6b-121">The second command uses the `Set-AuthenticodeSignature` cmdlet to sign the `PSTestInternet2.ps1` script.</span></span> <span data-ttu-id="ada6b-122">Parametern **sökväg** används för att ange namnet på skriptet och parametern **Certificate** för att ange att certifikatet lagras i `$cert` variabeln.</span><span class="sxs-lookup"><span data-stu-id="ada6b-122">It uses the **FilePath** parameter to specify the name of the script and the **Certificate** parameter to specify that the certificate is stored in the `$cert` variable.</span></span>

> [!NOTE]
> <span data-ttu-id="ada6b-123">Om du använder parametern **CodeSigningCert** med `Get-ChildItem` returneras bara certifikat som har kod signerings auktoritet och innehåller en privat nyckel.</span><span class="sxs-lookup"><span data-stu-id="ada6b-123">Using the **CodeSigningCert** parameter with `Get-ChildItem` only returns certificates that have code-signing authority and contain a private key.</span></span> <span data-ttu-id="ada6b-124">Om det inte finns någon privat nyckel kan certifikaten inte användas för signering.</span><span class="sxs-lookup"><span data-stu-id="ada6b-124">If there is no private key, the certificates cannot be used for signing.</span></span>

### <span data-ttu-id="ada6b-125">Exempel 2 – signera ett skript med ett certifikat från en PFX-fil</span><span class="sxs-lookup"><span data-stu-id="ada6b-125">Example 2 - Sign a script using a certificate from a PFX file</span></span>

<span data-ttu-id="ada6b-126">Dessa kommandon använder `Get-PfxCertificate` cmdleten för att läsa in ett kod signerings certifikat.</span><span class="sxs-lookup"><span data-stu-id="ada6b-126">These commands use the `Get-PfxCertificate` cmdlet to load a code signing certificate.</span></span> <span data-ttu-id="ada6b-127">Använd den sedan för att signera ett PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="ada6b-127">Then, use it to sign a PowerShell script.</span></span>

```powershell
$cert = Get-PfxCertificate -FilePath C:\Test\Mysign.pfx
Set-AuthenticodeSignature -FilePath ServerProps.ps1 -Certificate $cert
```

<span data-ttu-id="ada6b-128">Det första kommandot använder `Get-PfxCertificate` cmdleten för att läsa in C:\Test\MySign.PFX-certifikatet i `$cert` variabeln.</span><span class="sxs-lookup"><span data-stu-id="ada6b-128">The first command uses the `Get-PfxCertificate` cmdlet to load the C:\Test\MySign.pfx certificate into the `$cert` variable.</span></span>

<span data-ttu-id="ada6b-129">Det andra kommandot använder `Set-AuthenticodeSignature` för att signera skriptet.</span><span class="sxs-lookup"><span data-stu-id="ada6b-129">The second command uses `Set-AuthenticodeSignature` to sign the script.</span></span> <span data-ttu-id="ada6b-130">Parametern **FilePath** `Set-AuthenticodeSignature` pathname i anger sökvägen till skript filen som signeras och parametern **cert** skickar `$cert` variabeln som innehåller certifikatet till `Set-AuthenticodeSignature` .</span><span class="sxs-lookup"><span data-stu-id="ada6b-130">The **FilePath** parameter of `Set-AuthenticodeSignature` specifies the path to the script file being signed and the **Cert** parameter passes the `$cert` variable containing the certificate to `Set-AuthenticodeSignature`.</span></span>

<span data-ttu-id="ada6b-131">Om certifikat filen är lösenordsskyddad, uppmanas du att ange lösen ordet i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ada6b-131">If the certificate file is password protected, PowerShell prompts you for the password.</span></span>

### <span data-ttu-id="ada6b-132">Exempel 3 – Lägg till en signatur som innehåller rot utfärdaren</span><span class="sxs-lookup"><span data-stu-id="ada6b-132">Example 3 - Add a signature that includes the root authority</span></span>

<span data-ttu-id="ada6b-133">Det här kommandot lägger till en digital signatur som innehåller rot utfärdaren i förtroende kedjan och den är signerad av en tredjeparts tids stämplings Server.</span><span class="sxs-lookup"><span data-stu-id="ada6b-133">This command adds a digital signature that includes the root authority in the trust chain, and it is signed by a third-party timestamp server.</span></span>

```powershell
Set-AuthenticodeSignature -FilePath c:\scripts\Remodel.ps1 -Certificate $cert -IncludeChain All -TimestampServer "http://timestamp.fabrikam.com/scripts/timstamper.dll"
```

<span data-ttu-id="ada6b-134">Kommandot använder parametern **sökväg** för att ange vilket skript som signeras och parametern **certifikat** för att ange det certifikat som sparas i `$cert` variabeln.</span><span class="sxs-lookup"><span data-stu-id="ada6b-134">The command uses the **FilePath** parameter to specify the script being signed and the **Certificate** parameter to specify the certificate that is saved in the `$cert` variable.</span></span> <span data-ttu-id="ada6b-135">Parametern **IncludeChain** används för att inkludera alla signaturer i förtroende kedjan, inklusive rot utfärdaren.</span><span class="sxs-lookup"><span data-stu-id="ada6b-135">It uses the **IncludeChain** parameter to include all of the signatures in the trust chain, including the root authority.</span></span> <span data-ttu-id="ada6b-136">Den använder också parametern **TimeStampServer** för att lägga till en tidstämpel i signaturen.</span><span class="sxs-lookup"><span data-stu-id="ada6b-136">It also uses the **TimeStampServer** parameter to add a timestamp to the signature.</span></span>
<span data-ttu-id="ada6b-137">Detta förhindrar att skriptet kraschar när certifikatet upphör att gälla.</span><span class="sxs-lookup"><span data-stu-id="ada6b-137">This prevents the script from failing when the certificate expires.</span></span>

## <span data-ttu-id="ada6b-138">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="ada6b-138">PARAMETERS</span></span>

### <span data-ttu-id="ada6b-139">– Certifikat</span><span class="sxs-lookup"><span data-stu-id="ada6b-139">-Certificate</span></span>

<span data-ttu-id="ada6b-140">Anger det certifikat som ska användas för att signera skriptet eller filen.</span><span class="sxs-lookup"><span data-stu-id="ada6b-140">Specifies the certificate that will be used to sign the script or file.</span></span> <span data-ttu-id="ada6b-141">Ange en variabel som lagrar ett objekt som representerar certifikatet eller ett uttryck som hämtar certifikatet.</span><span class="sxs-lookup"><span data-stu-id="ada6b-141">Enter a variable that stores an object representing the certificate or an expression that gets the certificate.</span></span>

<span data-ttu-id="ada6b-142">Om du vill söka efter ett certifikat använder `Get-PfxCertificate` eller använder du `Get-ChildItem` cmdleten i certifikat `Cert:` enheten.</span><span class="sxs-lookup"><span data-stu-id="ada6b-142">To find a certificate, use `Get-PfxCertificate` or use the `Get-ChildItem` cmdlet in the Certificate `Cert:` drive.</span></span> <span data-ttu-id="ada6b-143">Om certifikatet inte är giltigt eller saknar `code-signing` behörighet, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="ada6b-143">If the certificate is not valid or does not have `code-signing` authority, the command fails.</span></span>

```yaml
Type: System.Security.Cryptography.X509Certificates.X509Certificate2
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ada6b-144">-Sökväg</span><span class="sxs-lookup"><span data-stu-id="ada6b-144">-FilePath</span></span>

<span data-ttu-id="ada6b-145">Anger sökvägen till en fil som signeras.</span><span class="sxs-lookup"><span data-stu-id="ada6b-145">Specifies the path to a file that is being signed.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ada6b-146">-Force</span><span class="sxs-lookup"><span data-stu-id="ada6b-146">-Force</span></span>

<span data-ttu-id="ada6b-147">Tillåter cmdleten att lägga till en signatur i en skrivskyddad fil.</span><span class="sxs-lookup"><span data-stu-id="ada6b-147">Allows the cmdlet to append a signature to a read-only file.</span></span> <span data-ttu-id="ada6b-148">Även om du använder **Force** -parametern kan inte cmdlet: en åsidosätta säkerhets begränsningar.</span><span class="sxs-lookup"><span data-stu-id="ada6b-148">Even using the **Force** parameter, the cmdlet cannot override security restrictions.</span></span>

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

### <span data-ttu-id="ada6b-149">– HashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="ada6b-149">-HashAlgorithm</span></span>

<span data-ttu-id="ada6b-150">Anger den hash-algoritm som Windows använder för att beräkna den digitala signaturen för filen.</span><span class="sxs-lookup"><span data-stu-id="ada6b-150">Specifies the hashing algorithm that Windows uses to compute the digital signature for the file.</span></span>

<span data-ttu-id="ada6b-151">För PowerShell 3,0 är standardvärdet SHA256, som är algoritmen för Windows standard-hashing.</span><span class="sxs-lookup"><span data-stu-id="ada6b-151">For PowerShell 3.0, the default is SHA256, which is the Windows default hashing algorithm.</span></span> <span data-ttu-id="ada6b-152">För PowerShell 2,0 är standardvärdet SHA1.</span><span class="sxs-lookup"><span data-stu-id="ada6b-152">For PowerShell 2.0, the default is SHA1.</span></span> <span data-ttu-id="ada6b-153">Filer som är signerade med en annan hash-algoritm kanske inte kan identifieras på andra system.</span><span class="sxs-lookup"><span data-stu-id="ada6b-153">Files that are signed with a different hashing algorithm might not be recognized on other systems.</span></span> <span data-ttu-id="ada6b-154">Vilka algoritmer som stöds beror på vilken version av operativ systemet som används.</span><span class="sxs-lookup"><span data-stu-id="ada6b-154">Which algorithms are supported depends on the version of the operating system.</span></span>

<span data-ttu-id="ada6b-155">En lista över möjliga värden finns i [HashAlgorithmName struct](/dotnet/api/system.security.cryptography.hashalgorithmname?view=netframework-4.7.2#properties).</span><span class="sxs-lookup"><span data-stu-id="ada6b-155">For a list of possible values, see [HashAlgorithmName Struct](/dotnet/api/system.security.cryptography.hashalgorithmname?view=netframework-4.7.2#properties).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: SHA256
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ada6b-156">-IncludeChain</span><span class="sxs-lookup"><span data-stu-id="ada6b-156">-IncludeChain</span></span>

<span data-ttu-id="ada6b-157">Avgör vilka certifikat i certifikat förtroende kedjan som ingår i den digitala signaturen.</span><span class="sxs-lookup"><span data-stu-id="ada6b-157">Determines which certificates in the certificate trust chain are included in the digital signature.</span></span>
<span data-ttu-id="ada6b-158">**NotRoot** är standardinställningen.</span><span class="sxs-lookup"><span data-stu-id="ada6b-158">**NotRoot** is the default.</span></span>

<span data-ttu-id="ada6b-159">Giltiga värden är:</span><span class="sxs-lookup"><span data-stu-id="ada6b-159">Valid values are:</span></span>

- <span data-ttu-id="ada6b-160">Undertecknare: innehåller bara signerarens certifikat.</span><span class="sxs-lookup"><span data-stu-id="ada6b-160">Signer: Includes only the signer's certificate.</span></span>
- <span data-ttu-id="ada6b-161">NotRoot: innehåller alla certifikat i certifikat kedjan, förutom rot utfärdaren.</span><span class="sxs-lookup"><span data-stu-id="ada6b-161">NotRoot: Includes all of the certificates in the certificate chain, except for the root authority.</span></span>
- <span data-ttu-id="ada6b-162">Alla: innehåller alla certifikat i certifikat kedjan.</span><span class="sxs-lookup"><span data-stu-id="ada6b-162">All: Includes all the certificates in the certificate chain.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: NotRoot
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ada6b-163">-TimestampServer</span><span class="sxs-lookup"><span data-stu-id="ada6b-163">-TimestampServer</span></span>

<span data-ttu-id="ada6b-164">Använder den angivna tids stämplings servern för att lägga till en tidstämpel i signaturen.</span><span class="sxs-lookup"><span data-stu-id="ada6b-164">Uses the specified time stamp server to add a time stamp to the signature.</span></span> <span data-ttu-id="ada6b-165">Ange URL: en för tids stämplings servern som en sträng.</span><span class="sxs-lookup"><span data-stu-id="ada6b-165">Type the URL of the time stamp server as a string.</span></span>

<span data-ttu-id="ada6b-166">Tidsstämpeln representerar den exakta tiden som certifikatet lades till i filen.</span><span class="sxs-lookup"><span data-stu-id="ada6b-166">The time stamp represents the exact time that the certificate was added to the file.</span></span> <span data-ttu-id="ada6b-167">En tidsstämpel förhindrar skriptet från att fungera om certifikatet upphör att gälla eftersom användare och program kan verifiera att certifikatet är giltigt vid tidpunkten för signeringen.</span><span class="sxs-lookup"><span data-stu-id="ada6b-167">A time stamp prevents the script from failing if the certificate expires because users and programs can verify that the certificate was valid at the time of signing.</span></span>

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

### <span data-ttu-id="ada6b-168">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="ada6b-168">-LiteralPath</span></span>

<span data-ttu-id="ada6b-169">Anger sökvägen till en fil som signeras.</span><span class="sxs-lookup"><span data-stu-id="ada6b-169">Specifies the path to a file that is being signed.</span></span> <span data-ttu-id="ada6b-170">Till skillnad från **sökväg** , används värdet för parametern **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="ada6b-170">Unlike **FilePath** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="ada6b-171">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="ada6b-171">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="ada6b-172">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="ada6b-172">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="ada6b-173">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="ada6b-173">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ada6b-174">-SourcePathOrExtension</span><span class="sxs-lookup"><span data-stu-id="ada6b-174">-SourcePathOrExtension</span></span>

<span data-ttu-id="ada6b-175">Sökväg till filen eller filtypen för innehållet som den digitala signaturen ska läggas till för.</span><span class="sxs-lookup"><span data-stu-id="ada6b-175">Path to the file or file type of the content for which the digital signature is added.</span></span> <span data-ttu-id="ada6b-176">Den här parametern används med **innehåll** där fil innehåll skickas som en byte mat ris.</span><span class="sxs-lookup"><span data-stu-id="ada6b-176">This parameter is used with **Content** where file content is passed as a byte array.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ada6b-177">– Innehåll</span><span class="sxs-lookup"><span data-stu-id="ada6b-177">-Content</span></span>

<span data-ttu-id="ada6b-178">Innehållet i en fil som en byte-matris för vilken den digitala signaturen läggs till.</span><span class="sxs-lookup"><span data-stu-id="ada6b-178">Contents of a file as a byte array for which the digital signature is added.</span></span> <span data-ttu-id="ada6b-179">Den här parametern måste användas med parametern **SourcePathOrExtension** .</span><span class="sxs-lookup"><span data-stu-id="ada6b-179">This parameter must be used with **SourcePathOrExtension** parameter.</span></span> <span data-ttu-id="ada6b-180">Filens innehåll måste vara i Unicode-format (UTF-16LE).</span><span class="sxs-lookup"><span data-stu-id="ada6b-180">The contents of the file must be in Unicode (UTF-16LE) format.</span></span>

```yaml
Type: System.Byte[]
Parameter Sets: ByContent
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ada6b-181">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ada6b-181">-Confirm</span></span>

<span data-ttu-id="ada6b-182">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ada6b-182">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ada6b-183">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ada6b-183">-WhatIf</span></span>

<span data-ttu-id="ada6b-184">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="ada6b-184">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="ada6b-185">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="ada6b-185">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ada6b-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ada6b-186">CommonParameters</span></span>

<span data-ttu-id="ada6b-187">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ada6b-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ada6b-188">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ada6b-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ada6b-189">INDATA</span><span class="sxs-lookup"><span data-stu-id="ada6b-189">INPUTS</span></span>

### <span data-ttu-id="ada6b-190">System. String</span><span class="sxs-lookup"><span data-stu-id="ada6b-190">System.String</span></span>

<span data-ttu-id="ada6b-191">Du kan skicka vidare en sträng som innehåller fil Sök vägen till `Set-AuthenticodeSignature` .</span><span class="sxs-lookup"><span data-stu-id="ada6b-191">You can pipe a string that contains the file path to `Set-AuthenticodeSignature`.</span></span>

## <span data-ttu-id="ada6b-192">UTDATA</span><span class="sxs-lookup"><span data-stu-id="ada6b-192">OUTPUTS</span></span>

### <span data-ttu-id="ada6b-193">System. Management. Automation. signatur</span><span class="sxs-lookup"><span data-stu-id="ada6b-193">System.Management.Automation.Signature</span></span>

## <span data-ttu-id="ada6b-194">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="ada6b-194">NOTES</span></span>

## <span data-ttu-id="ada6b-195">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="ada6b-195">RELATED LINKS</span></span>

[<span data-ttu-id="ada6b-196">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="ada6b-196">Get-AuthenticodeSignature</span></span>](Get-AuthenticodeSignature.md)

[<span data-ttu-id="ada6b-197">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="ada6b-197">Get-ExecutionPolicy</span></span>](Get-ExecutionPolicy.md)

[<span data-ttu-id="ada6b-198">Get-PfxCertificate</span><span class="sxs-lookup"><span data-stu-id="ada6b-198">Get-PfxCertificate</span></span>](Get-PfxCertificate.md)

[<span data-ttu-id="ada6b-199">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="ada6b-199">Set-ExecutionPolicy</span></span>](Set-ExecutionPolicy.md)

[<span data-ttu-id="ada6b-200">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="ada6b-200">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[<span data-ttu-id="ada6b-201">about_Signing</span><span class="sxs-lookup"><span data-stu-id="ada6b-201">about_Signing</span></span>](../Microsoft.PowerShell.Core/About/about_Signing.md)

