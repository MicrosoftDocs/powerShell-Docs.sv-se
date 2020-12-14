---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-filehash?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-FileHash
ms.openlocfilehash: 0b31409d1da56979887e606b76ddf20532b188c1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709432"
---
# <span data-ttu-id="d1b0d-102">Get-FileHash</span><span class="sxs-lookup"><span data-stu-id="d1b0d-102">Get-FileHash</span></span>

## <span data-ttu-id="d1b0d-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="d1b0d-103">SYNOPSIS</span></span>
<span data-ttu-id="d1b0d-104">Beräknar hash-värdet för en fil med hjälp av en angiven hash-algoritm.</span><span class="sxs-lookup"><span data-stu-id="d1b0d-104">Computes the hash value for a file by using a specified hash algorithm.</span></span>

## <span data-ttu-id="d1b0d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d1b0d-105">SYNTAX</span></span>

### <span data-ttu-id="d1b0d-106">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="d1b0d-106">Path (Default)</span></span>

```
Get-FileHash [-Path] <String[]> [[-Algorithm] <String>] [<CommonParameters>]
```

### <span data-ttu-id="d1b0d-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="d1b0d-107">LiteralPath</span></span>

```
Get-FileHash [-LiteralPath] <String[]> [[-Algorithm] <String>] [<CommonParameters>]
```

### <span data-ttu-id="d1b0d-108">StreamParameterSet</span><span class="sxs-lookup"><span data-stu-id="d1b0d-108">StreamParameterSet</span></span>

```
Get-FileHash [-InputStream] <Stream> [[-Algorithm] <String>] [<CommonParameters>]
```

## <span data-ttu-id="d1b0d-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="d1b0d-109">DESCRIPTION</span></span>

<span data-ttu-id="d1b0d-110">`Get-FileHash`Cmdleten beräknar hash-värdet för en fil med hjälp av en angiven hash-algoritm.</span><span class="sxs-lookup"><span data-stu-id="d1b0d-110">The `Get-FileHash` cmdlet computes the hash value for a file by using a specified hash algorithm.</span></span>
<span data-ttu-id="d1b0d-111">Ett hash-värde är ett unikt värde som motsvarar filens innehåll.</span><span class="sxs-lookup"><span data-stu-id="d1b0d-111">A hash value is a unique value that corresponds to the content of the file.</span></span> <span data-ttu-id="d1b0d-112">I stället för att identifiera innehållet i en fil med hjälp av dess fil namn, tillägg eller annan beteckning tilldelar en hash ett unikt värde till innehållet i en fil.</span><span class="sxs-lookup"><span data-stu-id="d1b0d-112">Rather than identifying the contents of a file by its file name, extension, or other designation, a hash assigns a unique value to the contents of a file.</span></span> <span data-ttu-id="d1b0d-113">Fil namn och tillägg kan ändras utan att ändra innehållet i filen och utan att ändra hash-värdet.</span><span class="sxs-lookup"><span data-stu-id="d1b0d-113">File names and extensions can be changed without altering the content of the file, and without changing the hash value.</span></span> <span data-ttu-id="d1b0d-114">På samma sätt kan filens innehåll ändras utan att du ändrar namnet eller tillägget.</span><span class="sxs-lookup"><span data-stu-id="d1b0d-114">Similarly, the file's content can be changed without changing the name or extension.</span></span> <span data-ttu-id="d1b0d-115">Men om du ändrar till och med ett enda bokstav i innehållet i en fil ändras filens hash-värde.</span><span class="sxs-lookup"><span data-stu-id="d1b0d-115">However, changing even a single character in the contents of a file changes the hash value of the file.</span></span>

<span data-ttu-id="d1b0d-116">Syftet med hash-värden är att tillhandahålla ett kryptografiskt, säkert sätt att verifiera att innehållet i en fil inte har ändrats.</span><span class="sxs-lookup"><span data-stu-id="d1b0d-116">The purpose of hash values is to provide a cryptographically-secure way to verify that the contents of a file have not been changed.</span></span> <span data-ttu-id="d1b0d-117">Vissa hash-algoritmer, inklusive MD5 och SHA1, anses inte längre vara säkra mot angrepp, målet för en säker hash-algoritm är att göra det omöjligt att ändra innehållet i en fil, antingen av misstag eller av skadlig eller obehörig försök--och underhålla samma hash-värde.</span><span class="sxs-lookup"><span data-stu-id="d1b0d-117">While some hash algorithms, including MD5 and SHA1, are no longer considered secure against attack, the goal of a secure hash algorithm is to render it impossible to change the contents of a file -- either by accident, or by malicious or unauthorized attempt -- and maintain the same hash value.</span></span> <span data-ttu-id="d1b0d-118">Du kan också använda hash-värden för att avgöra om två olika filer har exakt samma innehåll.</span><span class="sxs-lookup"><span data-stu-id="d1b0d-118">You can also use hash values to determine if two different files have exactly the same content.</span></span> <span data-ttu-id="d1b0d-119">Om hash-värdena för två filer är identiska är innehållet i filerna också identiska.</span><span class="sxs-lookup"><span data-stu-id="d1b0d-119">If the hash values of two files are identical, the contents of the files are also identical.</span></span>

<span data-ttu-id="d1b0d-120">Som standard `Get-FileHash` använder cmdleten SHA256-algoritmen, men alla hash-algoritmer som stöds av mål operativ systemet kan användas.</span><span class="sxs-lookup"><span data-stu-id="d1b0d-120">By default, the `Get-FileHash` cmdlet uses the SHA256 algorithm, although any hash algorithm that is supported by the target operating system can be used.</span></span>

## <span data-ttu-id="d1b0d-121">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="d1b0d-121">EXAMPLES</span></span>

### <span data-ttu-id="d1b0d-122">Exempel 1: beräkna hash-värdet för en fil</span><span class="sxs-lookup"><span data-stu-id="d1b0d-122">Example 1: Compute the hash value for a file</span></span>

<span data-ttu-id="d1b0d-123">I det här exemplet används `Get-FileHash` cmdleten för att beräkna hash-värdet för `/etc/apt/sources.list` filen.</span><span class="sxs-lookup"><span data-stu-id="d1b0d-123">This example uses the `Get-FileHash` cmdlet to compute the hash value for the `/etc/apt/sources.list` file.</span></span> <span data-ttu-id="d1b0d-124">Den hash-algoritm som används är standard **SHA256**.</span><span class="sxs-lookup"><span data-stu-id="d1b0d-124">The hash algorithm used is the default, **SHA256**.</span></span> <span data-ttu-id="d1b0d-125">Utdata är skickas till `Format-List` cmdleten för att formatera utdata som en lista.</span><span class="sxs-lookup"><span data-stu-id="d1b0d-125">The output is piped to the `Format-List` cmdlet to format the output as a list.</span></span>

```powershell
Get-FileHash /etc/apt/sources.list | Format-List
```

```Output
Algorithm : SHA256
Hash      : 3CBCFDDEC145E3382D592266BE193E5BE53443138EE6AB6CA09FF20DF609E268
Path      : /etc/apt/sources.list
```

### <span data-ttu-id="d1b0d-126">Exempel 2: beräkna hash-värdet för en ISO-fil</span><span class="sxs-lookup"><span data-stu-id="d1b0d-126">Example 2: Compute the hash value for an ISO file</span></span>

<span data-ttu-id="d1b0d-127">I det här exemplet används `Get-FileHash` cmdleten och **SHA384** -algoritmen för att beräkna hash-värdet för en ISO-fil som en administratör har hämtat från Internet.</span><span class="sxs-lookup"><span data-stu-id="d1b0d-127">This example uses the `Get-FileHash` cmdlet and the **SHA384** algorithm to compute the hash value for an ISO file that an administrator has downloaded from the internet.</span></span> <span data-ttu-id="d1b0d-128">Utdata är skickas till `Format-List` cmdleten för att formatera utdata som en lista.</span><span class="sxs-lookup"><span data-stu-id="d1b0d-128">The output is piped to the `Format-List` cmdlet to format the output as a list.</span></span>

```powershell
Get-FileHash C:\Users\user1\Downloads\Contoso8_1_ENT.iso -Algorithm SHA384 | Format-List
```

```Output
Algorithm : SHA384
Hash      : 20AB1C2EE19FC96A7C66E33917D191A24E3CE9DAC99DB7C786ACCE31E559144FEAFC695C58E508E2EBBC9D3C96F21FA3
Path      : C:\Users\user1\Downloads\Contoso8_1_ENT.iso
```

### <span data-ttu-id="d1b0d-129">Exempel 3: beräkna hash-värdet för en ström</span><span class="sxs-lookup"><span data-stu-id="d1b0d-129">Example 3: Compute the hash value of a stream</span></span>

<span data-ttu-id="d1b0d-130">I det här exemplet kommer vi att använda **system .net. WebClient** för att ladda ned ett paket från [PowerShell-release-sidan](https://github.com/PowerShell/PowerShell/releases/tag/v6.2.4).</span><span class="sxs-lookup"><span data-stu-id="d1b0d-130">For this example, we get are using **System.Net.WebClient** to download a package from the [Powershell release page](https://github.com/PowerShell/PowerShell/releases/tag/v6.2.4).</span></span> <span data-ttu-id="d1b0d-131">På sidan version dokumenteras också SHA256-hashen för varje paket fil.</span><span class="sxs-lookup"><span data-stu-id="d1b0d-131">The release page also documents the SHA256 hash of each package file.</span></span> <span data-ttu-id="d1b0d-132">Vi kan jämföra det publicerade hash-värdet med det som vi beräknar med `Get-FileHash` .</span><span class="sxs-lookup"><span data-stu-id="d1b0d-132">We can compare the published hash value with the one we calculate with `Get-FileHash`.</span></span>

```powershell
$wc = [System.Net.WebClient]::new()
$pkgurl = 'https://github.com/PowerShell/PowerShell/releases/download/v6.2.4/powershell_6.2.4-1.debian.9_amd64.deb'
$publishedHash = '8E28E54D601F0751922DE24632C1E716B4684876255CF82304A9B19E89A9CCAC'
$FileHash = Get-FileHash -InputStream ($wc.OpenRead($pkgurl))
$FileHash.Hash -eq $publishedHash
```

```Output
True
```

### <span data-ttu-id="d1b0d-133">Exempel 4: beräkna hashen för en sträng</span><span class="sxs-lookup"><span data-stu-id="d1b0d-133">Example 4: Compute the hash of a string</span></span>

<span data-ttu-id="d1b0d-134">PowerShell tillhandahåller ingen cmdlet för att beräkna hashen för en sträng.</span><span class="sxs-lookup"><span data-stu-id="d1b0d-134">PowerShell does not provide a cmdlet to compute the hash of a string.</span></span> <span data-ttu-id="d1b0d-135">Du kan dock skriva en sträng till en data ström och använda parametern **InputStream** för `Get-FileHash` för att hämta hash-värdet.</span><span class="sxs-lookup"><span data-stu-id="d1b0d-135">However, you can write a string to a stream and use the **InputStream** parameter of `Get-FileHash` to get the hash value.</span></span>

```powershell
$stringAsStream = [System.IO.MemoryStream]::new()
$writer = [System.IO.StreamWriter]::new($stringAsStream)
$writer.write("Hello world")
$writer.Flush()
$stringAsStream.Position = 0
Get-FileHash -InputStream $stringAsStream | Select-Object Hash
```

```Output
Hash
----
64EC88CA00B268E5BA1A35678A1B5316D212F4F366B2477232534A8AECA37F3C
```

## <span data-ttu-id="d1b0d-136">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="d1b0d-136">PARAMETERS</span></span>

### <span data-ttu-id="d1b0d-137">-Algoritm</span><span class="sxs-lookup"><span data-stu-id="d1b0d-137">-Algorithm</span></span>

<span data-ttu-id="d1b0d-138">Anger den kryptografiska hash-funktion som ska användas för att beräkna hash-värdet för innehållet i den angivna filen eller data strömmen.</span><span class="sxs-lookup"><span data-stu-id="d1b0d-138">Specifies the cryptographic hash function to use for computing the hash value of the contents of the specified file or stream.</span></span> <span data-ttu-id="d1b0d-139">En kryptografisk hash-funktion har egenskapen det är omöjligt att hitta två olika filer med samma hash-värde.</span><span class="sxs-lookup"><span data-stu-id="d1b0d-139">A cryptographic hash function has the property that it is infeasible to find two different files with the same hash value.</span></span> <span data-ttu-id="d1b0d-140">Hash-funktioner används ofta med digitala signaturer och för data integritet.</span><span class="sxs-lookup"><span data-stu-id="d1b0d-140">Hash functions are commonly used with digital signatures and for data integrity.</span></span> <span data-ttu-id="d1b0d-141">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="d1b0d-141">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="d1b0d-142">SHA1</span><span class="sxs-lookup"><span data-stu-id="d1b0d-142">SHA1</span></span>
- <span data-ttu-id="d1b0d-143">SHA256</span><span class="sxs-lookup"><span data-stu-id="d1b0d-143">SHA256</span></span>
- <span data-ttu-id="d1b0d-144">SHA384</span><span class="sxs-lookup"><span data-stu-id="d1b0d-144">SHA384</span></span>
- <span data-ttu-id="d1b0d-145">SHA512</span><span class="sxs-lookup"><span data-stu-id="d1b0d-145">SHA512</span></span>
- <span data-ttu-id="d1b0d-146">MD5</span><span class="sxs-lookup"><span data-stu-id="d1b0d-146">MD5</span></span>

<span data-ttu-id="d1b0d-147">Om inget värde anges, eller om parametern utelämnas, är standardvärdet SHA256.</span><span class="sxs-lookup"><span data-stu-id="d1b0d-147">If no value is specified, or if the parameter is omitted, the default value is SHA256.</span></span>

<span data-ttu-id="d1b0d-148">Av säkerhets skäl bör MD5 och SHA1, som inte längre anses vara säkra, endast användas för enkel ändrings validering och ska inte användas för att generera hash-värden för filer som kräver skydd mot angrepp eller manipulering.</span><span class="sxs-lookup"><span data-stu-id="d1b0d-148">For security reasons, MD5 and SHA1, which are no longer considered secure, should only be used for simple change validation, and should not be used to generate hash values for files that require protection from attack or tampering.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: SHA1, SHA256, SHA384, SHA512, MD5

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d1b0d-149">– InputStream</span><span class="sxs-lookup"><span data-stu-id="d1b0d-149">-InputStream</span></span>

<span data-ttu-id="d1b0d-150">Anger indataströmmen.</span><span class="sxs-lookup"><span data-stu-id="d1b0d-150">Specifies the input stream.</span></span>

```yaml
Type: System.IO.Stream
Parameter Sets: StreamParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d1b0d-151">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="d1b0d-151">-LiteralPath</span></span>

<span data-ttu-id="d1b0d-152">Anger sökvägen till en fil.</span><span class="sxs-lookup"><span data-stu-id="d1b0d-152">Specifies the path to a file.</span></span> <span data-ttu-id="d1b0d-153">Till skillnad från parametern **Path** används värdet för parametern **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="d1b0d-153">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="d1b0d-154">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="d1b0d-154">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="d1b0d-155">Om sökvägen innehåller escape-tecken omger du sökvägen med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="d1b0d-155">If the path includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="d1b0d-156">Enkla citat tecken instruerar PowerShell att inte tolka tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="d1b0d-156">Single quotation marks instruct PowerShell not to interpret characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="d1b0d-157">-Path</span><span class="sxs-lookup"><span data-stu-id="d1b0d-157">-Path</span></span>

<span data-ttu-id="d1b0d-158">Anger sökvägen till en eller flera filer som en matris.</span><span class="sxs-lookup"><span data-stu-id="d1b0d-158">Specifies the path to one or more files as an array.</span></span> <span data-ttu-id="d1b0d-159">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="d1b0d-159">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="d1b0d-160">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d1b0d-160">CommonParameters</span></span>

<span data-ttu-id="d1b0d-161">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d1b0d-161">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d1b0d-162">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d1b0d-162">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d1b0d-163">INDATA</span><span class="sxs-lookup"><span data-stu-id="d1b0d-163">INPUTS</span></span>

### <span data-ttu-id="d1b0d-164">System. String</span><span class="sxs-lookup"><span data-stu-id="d1b0d-164">System.String</span></span>

<span data-ttu-id="d1b0d-165">Du kan skicka vidare en sträng till den `Get-FileHash` cmdlet som innehåller en sökväg till en eller flera filer.</span><span class="sxs-lookup"><span data-stu-id="d1b0d-165">You can pipe a string to the `Get-FileHash` cmdlet that contains a path to one or more files.</span></span>

## <span data-ttu-id="d1b0d-166">UTDATA</span><span class="sxs-lookup"><span data-stu-id="d1b0d-166">OUTPUTS</span></span>

### <span data-ttu-id="d1b0d-167">Microsoft. PowerShell. Utility. FileHash</span><span class="sxs-lookup"><span data-stu-id="d1b0d-167">Microsoft.Powershell.Utility.FileHash</span></span>

<span data-ttu-id="d1b0d-168">`Get-FileHash` Returnerar ett objekt som representerar sökvägen till den angivna filen, värdet för den beräknade hashen och algoritmen som används för att beräkna hashen.</span><span class="sxs-lookup"><span data-stu-id="d1b0d-168">`Get-FileHash` returns an object that represents the path to the specified file, the value of the computed hash, and the algorithm used to compute the hash.</span></span>

## <span data-ttu-id="d1b0d-169">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="d1b0d-169">NOTES</span></span>

## <span data-ttu-id="d1b0d-170">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="d1b0d-170">RELATED LINKS</span></span>

[<span data-ttu-id="d1b0d-171">Format-List</span><span class="sxs-lookup"><span data-stu-id="d1b0d-171">Format-List</span></span>](Format-List.md)

