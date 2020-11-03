---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-pfxcertificate?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PfxCertificate
ms.openlocfilehash: 1be3034b1fb44b1dce1a592ea5a2c1622b54d28f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265233"
---
# <span data-ttu-id="c0628-103">Get-PfxCertificate</span><span class="sxs-lookup"><span data-stu-id="c0628-103">Get-PfxCertificate</span></span>

## <span data-ttu-id="c0628-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="c0628-104">SYNOPSIS</span></span>
<span data-ttu-id="c0628-105">Hämtar information om PFX-certifikatfiler på datorn.</span><span class="sxs-lookup"><span data-stu-id="c0628-105">Gets information about PFX certificate files on the computer.</span></span>

## <span data-ttu-id="c0628-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c0628-106">SYNTAX</span></span>

### <span data-ttu-id="c0628-107">ByPath (standard)</span><span class="sxs-lookup"><span data-stu-id="c0628-107">ByPath (Default)</span></span>

```
Get-PfxCertificate [-FilePath] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="c0628-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="c0628-108">ByLiteralPath</span></span>

```
Get-PfxCertificate -LiteralPath <String[]> [<CommonParameters>]
```

## <span data-ttu-id="c0628-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="c0628-109">DESCRIPTION</span></span>

<span data-ttu-id="c0628-110">`Get-PfxCertificate`Cmdlet: en hämtar ett objekt som representerar varje angiven PFX-certifikatfil.</span><span class="sxs-lookup"><span data-stu-id="c0628-110">The `Get-PfxCertificate` cmdlet gets an object representing each specified PFX certificate file.</span></span>
<span data-ttu-id="c0628-111">En PFX-fil innehåller både certifikatet och en privat nyckel.</span><span class="sxs-lookup"><span data-stu-id="c0628-111">A PFX file includes both the certificate and a private key.</span></span>

## <span data-ttu-id="c0628-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="c0628-112">EXAMPLES</span></span>

### <span data-ttu-id="c0628-113">Exempel 1: Hämta ett PFX-certifikat</span><span class="sxs-lookup"><span data-stu-id="c0628-113">Example 1: Get a PFX certificate</span></span>

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

<span data-ttu-id="c0628-114">Det här kommandot hämtar information om certifikat filen test. pfx i systemet.</span><span class="sxs-lookup"><span data-stu-id="c0628-114">This command gets information about the Test.pfx certificate file on the system.</span></span>

### <span data-ttu-id="c0628-115">Exempel 2: Hämta ett PFX-certifikat från en fjärran sluten dator</span><span class="sxs-lookup"><span data-stu-id="c0628-115">Example 2: Get a PFX certificate from a remote computer</span></span>

```powershell
Invoke-Command -ComputerName "Server01" -ScriptBlock {Get-PfxCertificate -FilePath "C:\Text\TestNoPassword.pfx"} -Authentication CredSSP
```

<span data-ttu-id="c0628-116">Det här kommandot hämtar en PFX-certifikatfil från fjärrdatorn Server01.</span><span class="sxs-lookup"><span data-stu-id="c0628-116">This command gets a PFX certificate file from the Server01 remote computer.</span></span> <span data-ttu-id="c0628-117">Den använder `Invoke-Command` för att köra ett `Get-PfxCertificate` kommando via fjärr anslutning.</span><span class="sxs-lookup"><span data-stu-id="c0628-117">It uses `Invoke-Command` to run a `Get-PfxCertificate` command remotely.</span></span>

<span data-ttu-id="c0628-118">När PFX-certifikatarkivet inte är lösenordsskyddad måste värdet för parametern **Authentication** `Invoke-Command` vara CredSSP.</span><span class="sxs-lookup"><span data-stu-id="c0628-118">When the PFX certificate file is not password-protected, the value of the **Authentication** parameter of `Invoke-Command` must be CredSSP.</span></span>

## <span data-ttu-id="c0628-119">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="c0628-119">PARAMETERS</span></span>

### <span data-ttu-id="c0628-120">-Sökväg</span><span class="sxs-lookup"><span data-stu-id="c0628-120">-FilePath</span></span>

<span data-ttu-id="c0628-121">Anger den fullständiga sökvägen till PFX-filen för den skyddade filen.</span><span class="sxs-lookup"><span data-stu-id="c0628-121">Specifies the full path to the PFX file of the secured file.</span></span> <span data-ttu-id="c0628-122">Om du anger ett värde för den här parametern behöver du inte skriva `-FilePath` på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="c0628-122">If you specify a value for this parameter, it is not necessary to type `-FilePath` at the command line.</span></span>

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

### <span data-ttu-id="c0628-123">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="c0628-123">-LiteralPath</span></span>

<span data-ttu-id="c0628-124">Den fullständiga sökvägen till PFX-filen för den skyddade filen.</span><span class="sxs-lookup"><span data-stu-id="c0628-124">The full path to the PFX file of the secured file.</span></span> <span data-ttu-id="c0628-125">Till skillnad från **sökväg** , används värdet för parametern **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="c0628-125">Unlike **FilePath** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="c0628-126">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="c0628-126">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="c0628-127">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="c0628-127">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="c0628-128">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="c0628-128">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="c0628-129">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c0628-129">CommonParameters</span></span>

<span data-ttu-id="c0628-130">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c0628-130">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c0628-131">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c0628-131">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c0628-132">INDATA</span><span class="sxs-lookup"><span data-stu-id="c0628-132">INPUTS</span></span>

### <span data-ttu-id="c0628-133">System. String</span><span class="sxs-lookup"><span data-stu-id="c0628-133">System.String</span></span>

<span data-ttu-id="c0628-134">Du kan skicka vidare en sträng som innehåller en fil Sök väg till `Get-PfxCertificate` .</span><span class="sxs-lookup"><span data-stu-id="c0628-134">You can pipe a string that contains a file path to `Get-PfxCertificate`.</span></span>

## <span data-ttu-id="c0628-135">UTDATA</span><span class="sxs-lookup"><span data-stu-id="c0628-135">OUTPUTS</span></span>

### <span data-ttu-id="c0628-136">System. Security. Cryptography. X509Certificates. X509Certificate2</span><span class="sxs-lookup"><span data-stu-id="c0628-136">System.Security.Cryptography.X509Certificates.X509Certificate2</span></span>

<span data-ttu-id="c0628-137">`Get-PfxCertificate` Returnerar ett objekt för varje certifikat som det får.</span><span class="sxs-lookup"><span data-stu-id="c0628-137">`Get-PfxCertificate` returns an object for each certificate that it gets.</span></span>

## <span data-ttu-id="c0628-138">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="c0628-138">NOTES</span></span>

<span data-ttu-id="c0628-139">När du använder `Invoke-Command` cmdleten för att köra ett `Get-PfxCertificate` kommando via fjärr anslutning och PFX-certifikatarkivet inte är lösenordsskyddat, måste värdet för **autentiseringsmetoden** för parametern `Invoke-Command` vara CredSSP.</span><span class="sxs-lookup"><span data-stu-id="c0628-139">When using the `Invoke-Command` cmdlet to run a `Get-PfxCertificate` command remotely, and the PFX certificate file is not password protected, the value of the **Authentication** parameter of `Invoke-Command` must be CredSSP.</span></span>

## <span data-ttu-id="c0628-140">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="c0628-140">RELATED LINKS</span></span>

[<span data-ttu-id="c0628-141">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="c0628-141">Get-AuthenticodeSignature</span></span>](Get-AuthenticodeSignature.md)

[<span data-ttu-id="c0628-142">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="c0628-142">Set-AuthenticodeSignature</span></span>](Set-AuthenticodeSignature.md)
