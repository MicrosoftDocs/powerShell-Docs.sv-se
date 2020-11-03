---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/16/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-filehash?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-FileHash
ms.openlocfilehash: 6b6b0bdfe635ba0d11c4694efa8af6c23d9acdcd
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262712"
---
# <span data-ttu-id="f0b2d-103">Get-FileHash</span><span class="sxs-lookup"><span data-stu-id="f0b2d-103">Get-FileHash</span></span>

## <span data-ttu-id="f0b2d-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="f0b2d-104">SYNOPSIS</span></span>
<span data-ttu-id="f0b2d-105">Beräknar hash-värdet för en fil med hjälp av en angiven hash-algoritm.</span><span class="sxs-lookup"><span data-stu-id="f0b2d-105">Computes the hash value for a file by using a specified hash algorithm.</span></span>

## <span data-ttu-id="f0b2d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f0b2d-106">SYNTAX</span></span>

### <span data-ttu-id="f0b2d-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="f0b2d-107">Path (Default)</span></span>

```
Get-FileHash [-Path] <String[]> [[-Algorithm] <String>] [<CommonParameters>]
```

### <span data-ttu-id="f0b2d-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="f0b2d-108">LiteralPath</span></span>

```
Get-FileHash [-LiteralPath] <String[]> [[-Algorithm] <String>] [<CommonParameters>]
```

### <span data-ttu-id="f0b2d-109">StreamParameterSet</span><span class="sxs-lookup"><span data-stu-id="f0b2d-109">StreamParameterSet</span></span>

```
Get-FileHash [-InputStream] <Stream> [[-Algorithm] <String>] [<CommonParameters>]
```

## <span data-ttu-id="f0b2d-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="f0b2d-110">DESCRIPTION</span></span>

<span data-ttu-id="f0b2d-111">`Get-FileHash`Cmdleten beräknar hash-värdet för en fil med hjälp av en angiven hash-algoritm.</span><span class="sxs-lookup"><span data-stu-id="f0b2d-111">The `Get-FileHash` cmdlet computes the hash value for a file by using a specified hash algorithm.</span></span>
<span data-ttu-id="f0b2d-112">Ett hash-värde är ett unikt värde som motsvarar filens innehåll.</span><span class="sxs-lookup"><span data-stu-id="f0b2d-112">A hash value is a unique value that corresponds to the content of the file.</span></span> <span data-ttu-id="f0b2d-113">I stället för att identifiera innehållet i en fil med hjälp av dess fil namn, tillägg eller annan beteckning tilldelar en hash ett unikt värde till innehållet i en fil.</span><span class="sxs-lookup"><span data-stu-id="f0b2d-113">Rather than identifying the contents of a file by its file name, extension, or other designation, a hash assigns a unique value to the contents of a file.</span></span> <span data-ttu-id="f0b2d-114">Fil namn och tillägg kan ändras utan att ändra innehållet i filen och utan att ändra hash-värdet.</span><span class="sxs-lookup"><span data-stu-id="f0b2d-114">File names and extensions can be changed without altering the content of the file, and without changing the hash value.</span></span> <span data-ttu-id="f0b2d-115">På samma sätt kan filens innehåll ändras utan att du ändrar namnet eller tillägget.</span><span class="sxs-lookup"><span data-stu-id="f0b2d-115">Similarly, the file's content can be changed without changing the name or extension.</span></span> <span data-ttu-id="f0b2d-116">Men om du ändrar till och med ett enda bokstav i innehållet i en fil ändras filens hash-värde.</span><span class="sxs-lookup"><span data-stu-id="f0b2d-116">However, changing even a single character in the contents of a file changes the hash value of the file.</span></span>

<span data-ttu-id="f0b2d-117">Syftet med hash-värden är att tillhandahålla ett kryptografiskt, säkert sätt att verifiera att innehållet i en fil inte har ändrats.</span><span class="sxs-lookup"><span data-stu-id="f0b2d-117">The purpose of hash values is to provide a cryptographically-secure way to verify that the contents of a file have not been changed.</span></span> <span data-ttu-id="f0b2d-118">Vissa hash-algoritmer, inklusive MD5 och SHA1, anses inte längre vara säkra mot angrepp, målet för en säker hash-algoritm är att göra det omöjligt att ändra innehållet i en fil, antingen av misstag eller av skadlig eller obehörig försök--och underhålla samma hash-värde.</span><span class="sxs-lookup"><span data-stu-id="f0b2d-118">While some hash algorithms, including MD5 and SHA1, are no longer considered secure against attack, the goal of a secure hash algorithm is to render it impossible to change the contents of a file -- either by accident, or by malicious or unauthorized attempt -- and maintain the same hash value.</span></span> <span data-ttu-id="f0b2d-119">Du kan också använda hash-värden för att avgöra om två olika filer har exakt samma innehåll.</span><span class="sxs-lookup"><span data-stu-id="f0b2d-119">You can also use hash values to determine if two different files have exactly the same content.</span></span> <span data-ttu-id="f0b2d-120">Om hash-värdena för två filer är identiska är innehållet i filerna också identiska.</span><span class="sxs-lookup"><span data-stu-id="f0b2d-120">If the hash values of two files are identical, the contents of the files are also identical.</span></span>

<span data-ttu-id="f0b2d-121">Som standard `Get-FileHash` använder cmdleten SHA256-algoritmen, men alla hash-algoritmer som stöds av mål operativ systemet kan användas.</span><span class="sxs-lookup"><span data-stu-id="f0b2d-121">By default, the `Get-FileHash` cmdlet uses the SHA256 algorithm, although any hash algorithm that is supported by the target operating system can be used.</span></span>

## <span data-ttu-id="f0b2d-122">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="f0b2d-122">EXAMPLES</span></span>

### <span data-ttu-id="f0b2d-123">Exempel 1: beräkna hash-värdet för en fil</span><span class="sxs-lookup"><span data-stu-id="f0b2d-123">Example 1: Compute the hash value for a file</span></span>

<span data-ttu-id="f0b2d-124">I det här exemplet används `Get-FileHash` cmdleten för att beräkna hash-värdet för `/etc/apt/sources.list` filen.</span><span class="sxs-lookup"><span data-stu-id="f0b2d-124">This example uses the `Get-FileHash` cmdlet to compute the hash value for the `/etc/apt/sources.list` file.</span></span> <span data-ttu-id="f0b2d-125">Den hash-algoritm som används är standard **SHA256**.</span><span class="sxs-lookup"><span data-stu-id="f0b2d-125">The hash algorithm used is the default, **SHA256**.</span></span> <span data-ttu-id="f0b2d-126">Utdata är skickas till `Format-List` cmdleten för att formatera utdata som en lista.</span><span class="sxs-lookup"><span data-stu-id="f0b2d-126">The output is piped to the `Format-List` cmdlet to format the output as a list.</span></span>

```powershell
Get-FileHash /etc/apt/sources.list | Format-List
```

```Output
Algorithm : SHA256
Hash      : 3CBCFDDEC145E3382D592266BE193E5BE53443138EE6AB6CA09FF20DF609E268
Path      : /etc/apt/sources.list
```

### <span data-ttu-id="f0b2d-127">Exempel 2: beräkna hash-värdet för en ISO-fil</span><span class="sxs-lookup"><span data-stu-id="f0b2d-127">Example 2: Compute the hash value for an ISO file</span></span>

<span data-ttu-id="f0b2d-128">I det här exemplet används `Get-FileHash` cmdleten och **SHA384** -algoritmen för att beräkna hash-värdet för en ISO-fil som en administratör har hämtat från Internet.</span><span class="sxs-lookup"><span data-stu-id="f0b2d-128">This example uses the `Get-FileHash` cmdlet and the **SHA384** algorithm to compute the hash value for an ISO file that an administrator has downloaded from the internet.</span></span> <span data-ttu-id="f0b2d-129">Utdata är skickas till `Format-List` cmdleten för att formatera utdata som en lista.</span><span class="sxs-lookup"><span data-stu-id="f0b2d-129">The output is piped to the `Format-List` cmdlet to format the output as a list.</span></span>

```powershell
Get-FileHash C:\Users\user1\Downloads\Contoso8_1_ENT.iso -Algorithm SHA384 | Format-List
```

```Output
Algorithm : SHA384
Hash      : 20AB1C2EE19FC96A7C66E33917D191A24E3CE9DAC99DB7C786ACCE31E559144FEAFC695C58E508E2EBBC9D3C96F21FA3
Path      : C:\Users\user1\Downloads\Contoso8_1_ENT.iso
```

### <span data-ttu-id="f0b2d-130">Exempel 3: beräkna hash-värdet för en ström</span><span class="sxs-lookup"><span data-stu-id="f0b2d-130">Example 3: Compute the hash value of a stream</span></span>

<span data-ttu-id="f0b2d-131">I det här exemplet kommer vi att använda **system .net. WebClient** för att ladda ned ett paket från [PowerShell-release-sidan](https://github.com/PowerShell/PowerShell/releases/tag/v6.2.4).</span><span class="sxs-lookup"><span data-stu-id="f0b2d-131">For this example, we get are using **System.Net.WebClient** to download a package from the [Powershell release page](https://github.com/PowerShell/PowerShell/releases/tag/v6.2.4).</span></span> <span data-ttu-id="f0b2d-132">På sidan version dokumenteras också SHA256-hashen för varje paket fil.</span><span class="sxs-lookup"><span data-stu-id="f0b2d-132">The release page also documents the SHA256 hash of each package file.</span></span> <span data-ttu-id="f0b2d-133">Vi kan jämföra det publicerade hash-värdet med det som vi beräknar med `Get-FileHash` .</span><span class="sxs-lookup"><span data-stu-id="f0b2d-133">We can compare the published hash value with the one we calculate with `Get-FileHash`.</span></span>

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

### <span data-ttu-id="f0b2d-134">Exempel 4: beräkna hashen för en sträng</span><span class="sxs-lookup"><span data-stu-id="f0b2d-134">Example 4: Compute the hash of a string</span></span>

<span data-ttu-id="f0b2d-135">PowerShell tillhandahåller ingen cmdlet för att beräkna hashen för en sträng.</span><span class="sxs-lookup"><span data-stu-id="f0b2d-135">PowerShell does not provide a cmdlet to compute the hash of a string.</span></span> <span data-ttu-id="f0b2d-136">Du kan dock skriva en sträng till en data ström och använda parametern **InputStream** för `Get-FileHash` för att hämta hash-värdet.</span><span class="sxs-lookup"><span data-stu-id="f0b2d-136">However, you can write a string to a stream and use the **InputStream** parameter of `Get-FileHash` to get the hash value.</span></span>

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

## <span data-ttu-id="f0b2d-137">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="f0b2d-137">PARAMETERS</span></span>

### <span data-ttu-id="f0b2d-138">-Algoritm</span><span class="sxs-lookup"><span data-stu-id="f0b2d-138">-Algorithm</span></span>

<span data-ttu-id="f0b2d-139">Anger den kryptografiska hash-funktion som ska användas för att beräkna hash-värdet för innehållet i den angivna filen eller data strömmen.</span><span class="sxs-lookup"><span data-stu-id="f0b2d-139">Specifies the cryptographic hash function to use for computing the hash value of the contents of the specified file or stream.</span></span> <span data-ttu-id="f0b2d-140">En kryptografisk hash-funktion har egenskapen det är omöjligt att hitta två olika filer med samma hash-värde.</span><span class="sxs-lookup"><span data-stu-id="f0b2d-140">A cryptographic hash function has the property that it is infeasible to find two different files with the same hash value.</span></span> <span data-ttu-id="f0b2d-141">Hash-funktioner används ofta med digitala signaturer och för data integritet.</span><span class="sxs-lookup"><span data-stu-id="f0b2d-141">Hash functions are commonly used with digital signatures and for data integrity.</span></span> <span data-ttu-id="f0b2d-142">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="f0b2d-142">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="f0b2d-143">SHA1</span><span class="sxs-lookup"><span data-stu-id="f0b2d-143">SHA1</span></span>
- <span data-ttu-id="f0b2d-144">SHA256</span><span class="sxs-lookup"><span data-stu-id="f0b2d-144">SHA256</span></span>
- <span data-ttu-id="f0b2d-145">SHA384</span><span class="sxs-lookup"><span data-stu-id="f0b2d-145">SHA384</span></span>
- <span data-ttu-id="f0b2d-146">SHA512</span><span class="sxs-lookup"><span data-stu-id="f0b2d-146">SHA512</span></span>
- <span data-ttu-id="f0b2d-147">MD5</span><span class="sxs-lookup"><span data-stu-id="f0b2d-147">MD5</span></span>

<span data-ttu-id="f0b2d-148">Om inget värde anges, eller om parametern utelämnas, är standardvärdet SHA256.</span><span class="sxs-lookup"><span data-stu-id="f0b2d-148">If no value is specified, or if the parameter is omitted, the default value is SHA256.</span></span>

<span data-ttu-id="f0b2d-149">Av säkerhets skäl bör MD5 och SHA1, som inte längre anses vara säkra, endast användas för enkel ändrings validering och ska inte användas för att generera hash-värden för filer som kräver skydd mot angrepp eller manipulering.</span><span class="sxs-lookup"><span data-stu-id="f0b2d-149">For security reasons, MD5 and SHA1, which are no longer considered secure, should only be used for simple change validation, and should not be used to generate hash values for files that require protection from attack or tampering.</span></span>

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

### <span data-ttu-id="f0b2d-150">– InputStream</span><span class="sxs-lookup"><span data-stu-id="f0b2d-150">-InputStream</span></span>

<span data-ttu-id="f0b2d-151">Anger indataströmmen.</span><span class="sxs-lookup"><span data-stu-id="f0b2d-151">Specifies the input stream.</span></span>

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

### <span data-ttu-id="f0b2d-152">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="f0b2d-152">-LiteralPath</span></span>

<span data-ttu-id="f0b2d-153">Anger sökvägen till en fil.</span><span class="sxs-lookup"><span data-stu-id="f0b2d-153">Specifies the path to a file.</span></span> <span data-ttu-id="f0b2d-154">Till skillnad från parametern **Path** används värdet för parametern **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="f0b2d-154">Unlike the **Path** parameter, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="f0b2d-155">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="f0b2d-155">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="f0b2d-156">Om sökvägen innehåller escape-tecken omger du sökvägen med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="f0b2d-156">If the path includes escape characters, enclose the path in single quotation marks.</span></span> <span data-ttu-id="f0b2d-157">Enkla citat tecken instruerar PowerShell att inte tolka tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="f0b2d-157">Single quotation marks instruct PowerShell not to interpret characters as escape sequences.</span></span>

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

### <span data-ttu-id="f0b2d-158">-Path</span><span class="sxs-lookup"><span data-stu-id="f0b2d-158">-Path</span></span>

<span data-ttu-id="f0b2d-159">Anger sökvägen till en eller flera filer som en matris.</span><span class="sxs-lookup"><span data-stu-id="f0b2d-159">Specifies the path to one or more files as an array.</span></span> <span data-ttu-id="f0b2d-160">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="f0b2d-160">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="f0b2d-161">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f0b2d-161">CommonParameters</span></span>

<span data-ttu-id="f0b2d-162">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f0b2d-162">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f0b2d-163">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f0b2d-163">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f0b2d-164">INDATA</span><span class="sxs-lookup"><span data-stu-id="f0b2d-164">INPUTS</span></span>

### <span data-ttu-id="f0b2d-165">System. String</span><span class="sxs-lookup"><span data-stu-id="f0b2d-165">System.String</span></span>

<span data-ttu-id="f0b2d-166">Du kan skicka vidare en sträng till den `Get-FileHash` cmdlet som innehåller en sökväg till en eller flera filer.</span><span class="sxs-lookup"><span data-stu-id="f0b2d-166">You can pipe a string to the `Get-FileHash` cmdlet that contains a path to one or more files.</span></span>

## <span data-ttu-id="f0b2d-167">UTDATA</span><span class="sxs-lookup"><span data-stu-id="f0b2d-167">OUTPUTS</span></span>

### <span data-ttu-id="f0b2d-168">Microsoft. PowerShell. Utility. FileHash</span><span class="sxs-lookup"><span data-stu-id="f0b2d-168">Microsoft.Powershell.Utility.FileHash</span></span>

<span data-ttu-id="f0b2d-169">`Get-FileHash` Returnerar ett objekt som representerar sökvägen till den angivna filen, värdet för den beräknade hashen och algoritmen som används för att beräkna hashen.</span><span class="sxs-lookup"><span data-stu-id="f0b2d-169">`Get-FileHash` returns an object that represents the path to the specified file, the value of the computed hash, and the algorithm used to compute the hash.</span></span>

## <span data-ttu-id="f0b2d-170">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="f0b2d-170">NOTES</span></span>

## <span data-ttu-id="f0b2d-171">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="f0b2d-171">RELATED LINKS</span></span>

[<span data-ttu-id="f0b2d-172">Format-List</span><span class="sxs-lookup"><span data-stu-id="f0b2d-172">Format-List</span></span>](Format-List.md)
