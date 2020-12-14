---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-pfxcertificate?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PfxCertificate
ms.openlocfilehash: baf06c34511217f23d876843007525b9ce17f35b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709469"
---
# <span data-ttu-id="ff1d3-102">Get-PfxCertificate</span><span class="sxs-lookup"><span data-stu-id="ff1d3-102">Get-PfxCertificate</span></span>

## <span data-ttu-id="ff1d3-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="ff1d3-103">SYNOPSIS</span></span>
<span data-ttu-id="ff1d3-104">Hämtar information om PFX-certifikatfiler på datorn.</span><span class="sxs-lookup"><span data-stu-id="ff1d3-104">Gets information about PFX certificate files on the computer.</span></span>

## <span data-ttu-id="ff1d3-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ff1d3-105">SYNTAX</span></span>

### <span data-ttu-id="ff1d3-106">ByPath (standard)</span><span class="sxs-lookup"><span data-stu-id="ff1d3-106">ByPath (Default)</span></span>

```
Get-PfxCertificate [-FilePath] <String[]> [-Password <SecureString>] [-NoPromptForPassword]
 [<CommonParameters>]
```

### <span data-ttu-id="ff1d3-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="ff1d3-107">ByLiteralPath</span></span>

```
Get-PfxCertificate -LiteralPath <String[]> [-Password <SecureString>] [-NoPromptForPassword]
 [<CommonParameters>]
```

## <span data-ttu-id="ff1d3-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ff1d3-108">DESCRIPTION</span></span>

<span data-ttu-id="ff1d3-109">`Get-PfxCertificate`Cmdlet: en hämtar ett objekt som representerar varje angiven PFX-certifikatfil.</span><span class="sxs-lookup"><span data-stu-id="ff1d3-109">The `Get-PfxCertificate` cmdlet gets an object representing each specified PFX certificate file.</span></span>
<span data-ttu-id="ff1d3-110">En PFX-fil innehåller både certifikatet och en privat nyckel.</span><span class="sxs-lookup"><span data-stu-id="ff1d3-110">A PFX file includes both the certificate and a private key.</span></span>

## <span data-ttu-id="ff1d3-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="ff1d3-111">EXAMPLES</span></span>

### <span data-ttu-id="ff1d3-112">Exempel 1: Hämta ett PFX-certifikat</span><span class="sxs-lookup"><span data-stu-id="ff1d3-112">Example 1: Get a PFX certificate</span></span>

```powershell
Get-PfxCertificate -FilePath "C:\windows\system32\Test.pfx"
```

```output
Password: ******
Signer Certificate:      David Chew (Self Certificate)
Time Certificate:
Time Stamp:
Path:                    C:\windows\system32\zap.pfx
```

<span data-ttu-id="ff1d3-113">Det här kommandot hämtar information om certifikat filen test. pfx i systemet.</span><span class="sxs-lookup"><span data-stu-id="ff1d3-113">This command gets information about the Test.pfx certificate file on the system.</span></span>

### <span data-ttu-id="ff1d3-114">Exempel 2: Hämta ett PFX-certifikat från en fjärran sluten dator</span><span class="sxs-lookup"><span data-stu-id="ff1d3-114">Example 2: Get a PFX certificate from a remote computer</span></span>

```powershell
Invoke-Command -ComputerName "Server01" -ScriptBlock {Get-PfxCertificate -FilePath "C:\Text\TestNoPassword.pfx"} -Authentication CredSSP
```

<span data-ttu-id="ff1d3-115">Det här kommandot hämtar en PFX-certifikatfil från fjärrdatorn Server01.</span><span class="sxs-lookup"><span data-stu-id="ff1d3-115">This command gets a PFX certificate file from the Server01 remote computer.</span></span> <span data-ttu-id="ff1d3-116">Den använder `Invoke-Command` för att köra ett `Get-PfxCertificate` kommando via fjärr anslutning.</span><span class="sxs-lookup"><span data-stu-id="ff1d3-116">It uses `Invoke-Command` to run a `Get-PfxCertificate` command remotely.</span></span>

<span data-ttu-id="ff1d3-117">När PFX-certifikatarkivet inte är lösenordsskyddad måste värdet för parametern **Authentication** `Invoke-Command` vara CredSSP.</span><span class="sxs-lookup"><span data-stu-id="ff1d3-117">When the PFX certificate file is not password-protected, the value of the **Authentication** parameter of `Invoke-Command` must be CredSSP.</span></span>

## <span data-ttu-id="ff1d3-118">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="ff1d3-118">PARAMETERS</span></span>

### <span data-ttu-id="ff1d3-119">-Sökväg</span><span class="sxs-lookup"><span data-stu-id="ff1d3-119">-FilePath</span></span>

<span data-ttu-id="ff1d3-120">Anger den fullständiga sökvägen till PFX-filen för den skyddade filen.</span><span class="sxs-lookup"><span data-stu-id="ff1d3-120">Specifies the full path to the PFX file of the secured file.</span></span> <span data-ttu-id="ff1d3-121">Om du anger ett värde för den här parametern behöver du inte skriva `-FilePath` på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="ff1d3-121">If you specify a value for this parameter, it is not necessary to type `-FilePath` at the command line.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="ff1d3-122">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="ff1d3-122">-LiteralPath</span></span>

<span data-ttu-id="ff1d3-123">Den fullständiga sökvägen till PFX-filen för den skyddade filen.</span><span class="sxs-lookup"><span data-stu-id="ff1d3-123">The full path to the PFX file of the secured file.</span></span> <span data-ttu-id="ff1d3-124">Till skillnad från **sökväg**, används värdet för parametern **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="ff1d3-124">Unlike **FilePath**, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="ff1d3-125">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="ff1d3-125">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="ff1d3-126">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="ff1d3-126">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="ff1d3-127">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="ff1d3-127">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="ff1d3-128">-NoPromptForPassword</span><span class="sxs-lookup"><span data-stu-id="ff1d3-128">-NoPromptForPassword</span></span>

<span data-ttu-id="ff1d3-129">Förhindrar att du uppmanas att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="ff1d3-129">Suppresses prompting for a password.</span></span>

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

### <span data-ttu-id="ff1d3-130">-Password</span><span class="sxs-lookup"><span data-stu-id="ff1d3-130">-Password</span></span>

<span data-ttu-id="ff1d3-131">Anger ett lösen ord som krävs för att komma åt en `.pfx` certifikat fil.</span><span class="sxs-lookup"><span data-stu-id="ff1d3-131">Specifies a password required to access a `.pfx` certificate file.</span></span>

<span data-ttu-id="ff1d3-132">Den här parametern introducerades i PowerShell 6,1.</span><span class="sxs-lookup"><span data-stu-id="ff1d3-132">This parameter was introduced in PowerShell 6.1.</span></span>

> [!NOTE]
> <span data-ttu-id="ff1d3-133">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="ff1d3-133">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="ff1d3-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ff1d3-134">CommonParameters</span></span>

<span data-ttu-id="ff1d3-135">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ff1d3-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ff1d3-136">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ff1d3-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ff1d3-137">INDATA</span><span class="sxs-lookup"><span data-stu-id="ff1d3-137">INPUTS</span></span>

### <span data-ttu-id="ff1d3-138">System. String</span><span class="sxs-lookup"><span data-stu-id="ff1d3-138">System.String</span></span>

<span data-ttu-id="ff1d3-139">Du kan skicka vidare en sträng som innehåller en fil Sök väg till `Get-PfxCertificate` .</span><span class="sxs-lookup"><span data-stu-id="ff1d3-139">You can pipe a string that contains a file path to `Get-PfxCertificate`.</span></span>

## <span data-ttu-id="ff1d3-140">UTDATA</span><span class="sxs-lookup"><span data-stu-id="ff1d3-140">OUTPUTS</span></span>

### <span data-ttu-id="ff1d3-141">System. Security. Cryptography. X509Certificates. X509Certificate2</span><span class="sxs-lookup"><span data-stu-id="ff1d3-141">System.Security.Cryptography.X509Certificates.X509Certificate2</span></span>

<span data-ttu-id="ff1d3-142">`Get-PfxCertificate` Returnerar ett objekt för varje certifikat som det får.</span><span class="sxs-lookup"><span data-stu-id="ff1d3-142">`Get-PfxCertificate` returns an object for each certificate that it gets.</span></span>

## <span data-ttu-id="ff1d3-143">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="ff1d3-143">NOTES</span></span>

<span data-ttu-id="ff1d3-144">När du använder `Invoke-Command` cmdleten för att köra ett `Get-PfxCertificate` kommando via fjärr anslutning och PFX-certifikatarkivet inte är lösenordsskyddat, måste värdet för **autentiseringsmetoden** för parametern `Invoke-Command` vara CredSSP.</span><span class="sxs-lookup"><span data-stu-id="ff1d3-144">When using the `Invoke-Command` cmdlet to run a `Get-PfxCertificate` command remotely, and the PFX certificate file is not password protected, the value of the **Authentication** parameter of `Invoke-Command` must be CredSSP.</span></span>

## <span data-ttu-id="ff1d3-145">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="ff1d3-145">RELATED LINKS</span></span>

[<span data-ttu-id="ff1d3-146">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="ff1d3-146">Get-AuthenticodeSignature</span></span>](Get-AuthenticodeSignature.md)

[<span data-ttu-id="ff1d3-147">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="ff1d3-147">Set-AuthenticodeSignature</span></span>](Set-AuthenticodeSignature.md)

