---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 04/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-authenticodesignature?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-AuthenticodeSignature
ms.openlocfilehash: b1b470fb1dd23cd404b7f5fea4981b39f206ae87
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685334"
---
# <span data-ttu-id="68775-103">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="68775-103">Get-AuthenticodeSignature</span></span>

## <span data-ttu-id="68775-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="68775-104">SYNOPSIS</span></span>
<span data-ttu-id="68775-105">Hämtar information om Authenticode-signaturen för en fil.</span><span class="sxs-lookup"><span data-stu-id="68775-105">Gets information about the Authenticode signature for a file.</span></span>

## <span data-ttu-id="68775-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="68775-106">SYNTAX</span></span>

### <span data-ttu-id="68775-107">ByPath (standard)</span><span class="sxs-lookup"><span data-stu-id="68775-107">ByPath (Default)</span></span>

```
Get-AuthenticodeSignature [-FilePath] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="68775-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="68775-108">ByLiteralPath</span></span>

```
Get-AuthenticodeSignature -LiteralPath <String[]> [<CommonParameters>]
```

### <span data-ttu-id="68775-109">ByContent</span><span class="sxs-lookup"><span data-stu-id="68775-109">ByContent</span></span>

```
Get-AuthenticodeSignature -SourcePathOrExtension <String[]> -Content <Byte[]> [<CommonParameters>]
```

## <span data-ttu-id="68775-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="68775-110">DESCRIPTION</span></span>

<span data-ttu-id="68775-111">`Get-AuthenticodeSignature`Cmdleten hämtar information om Authenticode-signaturen för en fil eller ett fil innehåll som en byte mat ris.</span><span class="sxs-lookup"><span data-stu-id="68775-111">The `Get-AuthenticodeSignature` cmdlet gets information about the Authenticode signature for a file or file content as a byte array.</span></span>
<span data-ttu-id="68775-112">Om filen är både inbäddad signerad och Windows Catalog signerad, används Windows Catalog-signaturen.</span><span class="sxs-lookup"><span data-stu-id="68775-112">If the file is both embedded signed and Windows catalog signed, the Windows catalog signature is used.</span></span>
<span data-ttu-id="68775-113">Om filen inte är signerad hämtas informationen, men fälten är tomma.</span><span class="sxs-lookup"><span data-stu-id="68775-113">If the file is not signed, the information is retrieved, but the fields are blank.</span></span>

## <span data-ttu-id="68775-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="68775-114">EXAMPLES</span></span>

### <span data-ttu-id="68775-115">Exempel 1: Hämta Authenticode-signaturen för en fil</span><span class="sxs-lookup"><span data-stu-id="68775-115">Example 1: Get the Authenticode signature for a file</span></span>

```powershell
Get-AuthenticodeSignature -FilePath "C:\Test\NewScript.ps1"
```

<span data-ttu-id="68775-116">Det här kommandot hämtar information om Authenticode-signaturen i NewScript.ps1-filen.</span><span class="sxs-lookup"><span data-stu-id="68775-116">This command gets information about the Authenticode signature in the NewScript.ps1 file.</span></span> <span data-ttu-id="68775-117">Parametern **sökväg** används för att ange filen.</span><span class="sxs-lookup"><span data-stu-id="68775-117">It uses the **FilePath** parameter to specify the file.</span></span>

### <span data-ttu-id="68775-118">Exempel 2: Hämta Authenticode-signaturen för flera filer</span><span class="sxs-lookup"><span data-stu-id="68775-118">Example 2: Get the Authenticode signature for multiple files</span></span>

```powershell
Get-AuthenticodeSignature test.ps1, test1.ps1, sign-file.ps1, makexml.ps1
```

<span data-ttu-id="68775-119">Det här kommandot hämtar information om Authenticode-signaturen för de fyra filerna som anges på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="68775-119">This command gets information about the Authenticode signature for the four files listed at the command line.</span></span> <span data-ttu-id="68775-120">I det här exemplet utelämnas namnet på parametern **sökväg** , som är valfritt.</span><span class="sxs-lookup"><span data-stu-id="68775-120">In this example, the name of the **FilePath** parameter, which is optional, is omitted.</span></span>

### <span data-ttu-id="68775-121">Exempel 3: Hämta endast giltiga Authenticode-signaturer för flera filer</span><span class="sxs-lookup"><span data-stu-id="68775-121">Example 3: Get only valid Authenticode signatures for multiple files</span></span>

```powershell
Get-ChildItem $PSHOME\*.* | ForEach-object {Get-AuthenticodeSignature $_} | Where-Object {$_.status -eq "Valid"}
```

<span data-ttu-id="68775-122">Detta kommando visar alla filer i `$PSHOME` katalogen som har en giltig Authenticode-signatur.</span><span class="sxs-lookup"><span data-stu-id="68775-122">This command lists all of the files in the `$PSHOME` directory that have a valid Authenticode signature.</span></span> <span data-ttu-id="68775-123">Den `$PSHOME` automatiska variabeln innehåller sökvägen till PowerShell-katalogen för installationen.</span><span class="sxs-lookup"><span data-stu-id="68775-123">The `$PSHOME` automatic variable contains the path to the PowerShell installation directory.</span></span>

<span data-ttu-id="68775-124">Kommandot använder `Get-ChildItem` cmdleten för att hämta filerna i `$PSHOME` katalogen.</span><span class="sxs-lookup"><span data-stu-id="68775-124">The command uses the `Get-ChildItem` cmdlet to get the files in the `$PSHOME` directory.</span></span> <span data-ttu-id="68775-125">Det använder ett mönster i *.*</span><span class="sxs-lookup"><span data-stu-id="68775-125">It uses a pattern of *.*</span></span> <span data-ttu-id="68775-126">Om du vill utesluta kataloger (även om det också utesluter filer utan en punkt i fil namnet).</span><span class="sxs-lookup"><span data-stu-id="68775-126">to exclude directories (although it also excludes files without a dot in the filename).</span></span>

<span data-ttu-id="68775-127">Kommandot använder en pipeline-operator ( `|` ) för att skicka filerna `$PSHOME` till `ForEach-Object` -cmdleten, där `Get-AuthenticodeSignature` anropas för varje fil.</span><span class="sxs-lookup"><span data-stu-id="68775-127">The command uses a pipeline operator (`|`) to send the files in `$PSHOME` to the `ForEach-Object` cmdlet, where `Get-AuthenticodeSignature` is called for each file.</span></span>

<span data-ttu-id="68775-128">Resultatet av `Get-AuthenticodeSignature` kommandot skickas till ett `Where-Object` kommando som bara väljer de signaturkrav som har statusen giltig.</span><span class="sxs-lookup"><span data-stu-id="68775-128">The results of the `Get-AuthenticodeSignature` command are sent to a `Where-Object` command that selects only the signature objects with a status of Valid.</span></span>

### <span data-ttu-id="68775-129">Exempel 4: Hämta Authenticode-signaturen för ett fil innehåll som anges som byte mat ris</span><span class="sxs-lookup"><span data-stu-id="68775-129">Example 4: Get the Authenticode signature for a file content specified as byte array</span></span>

```powershell
Get-AuthenticodeSignature -Content (Get-Content foo.ps1 -AsByteStream) -SourcePathorExtension ps1
```

<span data-ttu-id="68775-130">Det här kommandot hämtar information om Authenticode-signaturen för innehållet i en fil.</span><span class="sxs-lookup"><span data-stu-id="68775-130">This command gets information about the Authenticode signature for the content of a file.</span></span> <span data-ttu-id="68775-131">I det här exemplet anges fil namns tillägget tillsammans med filens innehåll.</span><span class="sxs-lookup"><span data-stu-id="68775-131">In this example, the file extension is specified along with the content of the file.</span></span>

## <span data-ttu-id="68775-132">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="68775-132">PARAMETERS</span></span>

### <span data-ttu-id="68775-133">– Innehåll</span><span class="sxs-lookup"><span data-stu-id="68775-133">-Content</span></span>

<span data-ttu-id="68775-134">Innehållet i en fil som en byte-matris för vilken Authenticode-signaturen hämtas.</span><span class="sxs-lookup"><span data-stu-id="68775-134">Contents of a file as a byte array for which the Authenticode signature is retrieved.</span></span> <span data-ttu-id="68775-135">Den här parametern måste användas med parametern **SourcePathOrExtension** .</span><span class="sxs-lookup"><span data-stu-id="68775-135">This parameter must be used with **SourcePathOrExtension** parameter.</span></span> <span data-ttu-id="68775-136">Filens innehåll måste vara i Unicode-format (UTF-16LE).</span><span class="sxs-lookup"><span data-stu-id="68775-136">The contents of the file must be in Unicode (UTF-16LE) format.</span></span>

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

### <span data-ttu-id="68775-137">-Sökväg</span><span class="sxs-lookup"><span data-stu-id="68775-137">-FilePath</span></span>

<span data-ttu-id="68775-138">Anger sökvägen till filen som ska granskas.</span><span class="sxs-lookup"><span data-stu-id="68775-138">Specifies the path to the file to examine.</span></span> <span data-ttu-id="68775-139">Jokertecken tillåts, men de måste leda till en enda fil.</span><span class="sxs-lookup"><span data-stu-id="68775-139">Wildcards are permitted, but they must lead to a single file.</span></span> <span data-ttu-id="68775-140">Du behöver inte skriva in **sökväg** på kommando raden när du anger ett värde för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="68775-140">It is not necessary to type **FilePath** at the command line when you specify a value for this parameter.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="68775-141">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="68775-141">-LiteralPath</span></span>

<span data-ttu-id="68775-142">Anger sökvägen till den fil som ska undersökas.</span><span class="sxs-lookup"><span data-stu-id="68775-142">Specifies the path to the file being examined.</span></span> <span data-ttu-id="68775-143">Till skillnad från **sökväg**, används värdet för parametern **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="68775-143">Unlike **FilePath**, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="68775-144">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="68775-144">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="68775-145">Om sökvägen innehåller ett escape-tecken omger du det med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="68775-145">If the path includes an escape character, enclose it in single quotation marks.</span></span> <span data-ttu-id="68775-146">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-tecken.</span><span class="sxs-lookup"><span data-stu-id="68775-146">Single quotation marks tell PowerShell not to interpret any characters as escape characters.</span></span>

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

### <span data-ttu-id="68775-147">-SourcePathOrExtension</span><span class="sxs-lookup"><span data-stu-id="68775-147">-SourcePathOrExtension</span></span>

<span data-ttu-id="68775-148">Sökväg till filen eller filtypen för det innehåll som Authenticode-signaturen hämtas för.</span><span class="sxs-lookup"><span data-stu-id="68775-148">Path to the file or file type of the content for which the Authenticode signature is retrieved.</span></span> <span data-ttu-id="68775-149">Den här parametern används med **innehåll** där fil innehåll skickas som en byte mat ris.</span><span class="sxs-lookup"><span data-stu-id="68775-149">This parameter is used with **Content** where file content is passed as a byte array.</span></span>

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

### <span data-ttu-id="68775-150">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="68775-150">CommonParameters</span></span>

<span data-ttu-id="68775-151">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="68775-151">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="68775-152">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="68775-152">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="68775-153">INDATA</span><span class="sxs-lookup"><span data-stu-id="68775-153">INPUTS</span></span>

### <span data-ttu-id="68775-154">System. String</span><span class="sxs-lookup"><span data-stu-id="68775-154">System.String</span></span>

<span data-ttu-id="68775-155">Du kan skicka vidare en sträng som innehåller en fil Sök väg till `Get-AuthenticodeSignature` .</span><span class="sxs-lookup"><span data-stu-id="68775-155">You can pipe a string that contains a file path to `Get-AuthenticodeSignature`.</span></span>

## <span data-ttu-id="68775-156">UTDATA</span><span class="sxs-lookup"><span data-stu-id="68775-156">OUTPUTS</span></span>

### <span data-ttu-id="68775-157">System. Management. Automation. signatur</span><span class="sxs-lookup"><span data-stu-id="68775-157">System.Management.Automation.Signature</span></span>

<span data-ttu-id="68775-158">`Get-AuthenticodeSignature` Returnerar ett signatur objekt för varje signatur som det får.</span><span class="sxs-lookup"><span data-stu-id="68775-158">`Get-AuthenticodeSignature` returns a signature object for each signature that it gets.</span></span>

## <span data-ttu-id="68775-159">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="68775-159">NOTES</span></span>

<span data-ttu-id="68775-160">Den här cmdleten är endast tillgänglig på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="68775-160">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="68775-161">Information om Authenticode-signaturer i PowerShell finns [about_Signing](../Microsoft.PowerShell.Core/About/about_Signing.md).</span><span class="sxs-lookup"><span data-stu-id="68775-161">For information about Authenticode signatures in PowerShell, see [about_Signing](../Microsoft.PowerShell.Core/About/about_Signing.md).</span></span>

## <span data-ttu-id="68775-162">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="68775-162">RELATED LINKS</span></span>

[<span data-ttu-id="68775-163">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="68775-163">Get-ExecutionPolicy</span></span>](Get-ExecutionPolicy.md)

[<span data-ttu-id="68775-164">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="68775-164">Set-AuthenticodeSignature</span></span>](Set-AuthenticodeSignature.md)

[<span data-ttu-id="68775-165">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="68775-165">Set-ExecutionPolicy</span></span>](Set-ExecutionPolicy.md)

[<span data-ttu-id="68775-166">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="68775-166">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[<span data-ttu-id="68775-167">about_Signing</span><span class="sxs-lookup"><span data-stu-id="68775-167">about_Signing</span></span>](../Microsoft.PowerShell.Core/About/about_Signing.md)
