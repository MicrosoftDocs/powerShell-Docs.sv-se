---
external help file: Microsoft.PowerShell.Security.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Security
ms.date: 04/10/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.security/get-authenticodesignature?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-AuthenticodeSignature
ms.openlocfilehash: fa3ea8f965ea8089defa5fde7b88b18f00cd83bc
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267680"
---
# <span data-ttu-id="b7b30-103">Get-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="b7b30-103">Get-AuthenticodeSignature</span></span>

## <span data-ttu-id="b7b30-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="b7b30-104">SYNOPSIS</span></span>
<span data-ttu-id="b7b30-105">Hämtar information om Authenticode-signaturen för en fil.</span><span class="sxs-lookup"><span data-stu-id="b7b30-105">Gets information about the Authenticode signature for a file.</span></span>

## <span data-ttu-id="b7b30-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b7b30-106">SYNTAX</span></span>

### <span data-ttu-id="b7b30-107">ByPath (standard)</span><span class="sxs-lookup"><span data-stu-id="b7b30-107">ByPath (Default)</span></span>

```
Get-AuthenticodeSignature [-FilePath] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="b7b30-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="b7b30-108">ByLiteralPath</span></span>

```
Get-AuthenticodeSignature -LiteralPath <String[]> [<CommonParameters>]
```

### <span data-ttu-id="b7b30-109">ByContent</span><span class="sxs-lookup"><span data-stu-id="b7b30-109">ByContent</span></span>

```
Get-AuthenticodeSignature -SourcePathOrExtension <String[]> -Content <Byte[]> [<CommonParameters>]
```

## <span data-ttu-id="b7b30-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b7b30-110">DESCRIPTION</span></span>

<span data-ttu-id="b7b30-111">`Get-AuthenticodeSignature`Cmdleten hämtar information om Authenticode-signaturen för en fil eller ett fil innehåll som en byte mat ris.</span><span class="sxs-lookup"><span data-stu-id="b7b30-111">The `Get-AuthenticodeSignature` cmdlet gets information about the Authenticode signature for a file or file content as a byte array.</span></span> <span data-ttu-id="b7b30-112">Om filen inte är signerad hämtas informationen, men fälten är tomma.</span><span class="sxs-lookup"><span data-stu-id="b7b30-112">If the file is not signed, the information is retrieved, but the fields are blank.</span></span>

## <span data-ttu-id="b7b30-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="b7b30-113">EXAMPLES</span></span>

### <span data-ttu-id="b7b30-114">Exempel 1: Hämta Authenticode-signaturen för en fil</span><span class="sxs-lookup"><span data-stu-id="b7b30-114">Example 1: Get the Authenticode signature for a file</span></span>

```powershell
Get-AuthenticodeSignature -FilePath "C:\Test\NewScript.ps1"
```

<span data-ttu-id="b7b30-115">Det här kommandot hämtar information om Authenticode-signaturen i NewScript.ps1-filen.</span><span class="sxs-lookup"><span data-stu-id="b7b30-115">This command gets information about the Authenticode signature in the NewScript.ps1 file.</span></span> <span data-ttu-id="b7b30-116">Parametern **sökväg** används för att ange filen.</span><span class="sxs-lookup"><span data-stu-id="b7b30-116">It uses the **FilePath** parameter to specify the file.</span></span>

### <span data-ttu-id="b7b30-117">Exempel 2: Hämta Authenticode-signaturen för flera filer</span><span class="sxs-lookup"><span data-stu-id="b7b30-117">Example 2: Get the Authenticode signature for multiple files</span></span>

```powershell
Get-AuthenticodeSignature test.ps1, test1.ps1, sign-file.ps1, makexml.ps1
```

<span data-ttu-id="b7b30-118">Det här kommandot hämtar information om Authenticode-signaturen för de fyra filerna som anges på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="b7b30-118">This command gets information about the Authenticode signature for the four files listed at the command line.</span></span> <span data-ttu-id="b7b30-119">I det här exemplet utelämnas namnet på parametern **sökväg** , som är valfritt.</span><span class="sxs-lookup"><span data-stu-id="b7b30-119">In this example, the name of the **FilePath** parameter, which is optional, is omitted.</span></span>

### <span data-ttu-id="b7b30-120">Exempel 3: Hämta endast giltiga Authenticode-signaturer för flera filer</span><span class="sxs-lookup"><span data-stu-id="b7b30-120">Example 3: Get only valid Authenticode signatures for multiple files</span></span>

```powershell
Get-ChildItem $PSHOME\*.* | ForEach-object {Get-AuthenticodeSignature $_} | Where-Object {$_.status -eq "Valid"}
```

<span data-ttu-id="b7b30-121">Detta kommando visar alla filer i `$PSHOME` katalogen som har en giltig Authenticode-signatur.</span><span class="sxs-lookup"><span data-stu-id="b7b30-121">This command lists all of the files in the `$PSHOME` directory that have a valid Authenticode signature.</span></span> <span data-ttu-id="b7b30-122">Den `$PSHOME` automatiska variabeln innehåller sökvägen till PowerShell-katalogen för installationen.</span><span class="sxs-lookup"><span data-stu-id="b7b30-122">The `$PSHOME` automatic variable contains the path to the PowerShell installation directory.</span></span>

<span data-ttu-id="b7b30-123">Kommandot använder `Get-ChildItem` cmdleten för att hämta filerna i `$PSHOME` katalogen.</span><span class="sxs-lookup"><span data-stu-id="b7b30-123">The command uses the `Get-ChildItem` cmdlet to get the files in the `$PSHOME` directory.</span></span> <span data-ttu-id="b7b30-124">Det använder ett mönster i *.*</span><span class="sxs-lookup"><span data-stu-id="b7b30-124">It uses a pattern of *.*</span></span> <span data-ttu-id="b7b30-125">Om du vill utesluta kataloger (även om det också utesluter filer utan en punkt i fil namnet).</span><span class="sxs-lookup"><span data-stu-id="b7b30-125">to exclude directories (although it also excludes files without a dot in the filename).</span></span>

<span data-ttu-id="b7b30-126">Kommandot använder en pipeline-operator ( `|` ) för att skicka filerna `$PSHOME` till `ForEach-Object` -cmdleten, där `Get-AuthenticodeSignature` anropas för varje fil.</span><span class="sxs-lookup"><span data-stu-id="b7b30-126">The command uses a pipeline operator (`|`) to send the files in `$PSHOME` to the `ForEach-Object` cmdlet, where `Get-AuthenticodeSignature` is called for each file.</span></span>

<span data-ttu-id="b7b30-127">Resultatet av `Get-AuthenticodeSignature` kommandot skickas till ett `Where-Object` kommando som bara väljer de signaturkrav som har statusen giltig.</span><span class="sxs-lookup"><span data-stu-id="b7b30-127">The results of the `Get-AuthenticodeSignature` command are sent to a `Where-Object` command that selects only the signature objects with a status of Valid.</span></span>

### <span data-ttu-id="b7b30-128">Exempel 4: Hämta Authenticode-signaturen för ett fil innehåll som anges som byte mat ris</span><span class="sxs-lookup"><span data-stu-id="b7b30-128">Example 4: Get the Authenticode signature for a file content specified as byte array</span></span>

```powershell
Get-AuthenticodeSignature -Content (Get-Content foo.ps1 -AsByteStream) -SourcePathorExtension ps1
```

<span data-ttu-id="b7b30-129">Det här kommandot hämtar information om Authenticode-signaturen för innehållet i en fil.</span><span class="sxs-lookup"><span data-stu-id="b7b30-129">This command gets information about the Authenticode signature for the content of a file.</span></span> <span data-ttu-id="b7b30-130">I det här exemplet anges fil namns tillägget tillsammans med filens innehåll.</span><span class="sxs-lookup"><span data-stu-id="b7b30-130">In this example, the file extension is specified along with the content of the file.</span></span>

## <span data-ttu-id="b7b30-131">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="b7b30-131">PARAMETERS</span></span>

### <span data-ttu-id="b7b30-132">– Innehåll</span><span class="sxs-lookup"><span data-stu-id="b7b30-132">-Content</span></span>

<span data-ttu-id="b7b30-133">Innehållet i en fil som en byte-matris för vilken Authenticode-signaturen hämtas.</span><span class="sxs-lookup"><span data-stu-id="b7b30-133">Contents of a file as a byte array for which the Authenticode signature is retrieved.</span></span> <span data-ttu-id="b7b30-134">Den här parametern måste användas med parametern **SourcePathOrExtension** .</span><span class="sxs-lookup"><span data-stu-id="b7b30-134">This parameter must be used with **SourcePathOrExtension** parameter.</span></span> <span data-ttu-id="b7b30-135">Filens innehåll måste vara i Unicode-format (UTF-16LE).</span><span class="sxs-lookup"><span data-stu-id="b7b30-135">The contents of the file must be in Unicode (UTF-16LE) format.</span></span>

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

### <span data-ttu-id="b7b30-136">-Sökväg</span><span class="sxs-lookup"><span data-stu-id="b7b30-136">-FilePath</span></span>

<span data-ttu-id="b7b30-137">Anger sökvägen till filen som ska granskas.</span><span class="sxs-lookup"><span data-stu-id="b7b30-137">Specifies the path to the file to examine.</span></span> <span data-ttu-id="b7b30-138">Jokertecken tillåts, men de måste leda till en enda fil.</span><span class="sxs-lookup"><span data-stu-id="b7b30-138">Wildcards are permitted, but they must lead to a single file.</span></span> <span data-ttu-id="b7b30-139">Du behöver inte skriva in **sökväg** på kommando raden när du anger ett värde för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="b7b30-139">It is not necessary to type **FilePath** at the command line when you specify a value for this parameter.</span></span>

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

### <span data-ttu-id="b7b30-140">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b7b30-140">-LiteralPath</span></span>

<span data-ttu-id="b7b30-141">Anger sökvägen till den fil som ska undersökas.</span><span class="sxs-lookup"><span data-stu-id="b7b30-141">Specifies the path to the file being examined.</span></span> <span data-ttu-id="b7b30-142">Till skillnad från **sökväg** , används värdet för parametern **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="b7b30-142">Unlike **FilePath** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="b7b30-143">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="b7b30-143">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="b7b30-144">Om sökvägen innehåller ett escape-tecken omger du det med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="b7b30-144">If the path includes an escape character, enclose it in single quotation marks.</span></span> <span data-ttu-id="b7b30-145">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-tecken.</span><span class="sxs-lookup"><span data-stu-id="b7b30-145">Single quotation marks tell PowerShell not to interpret any characters as escape characters.</span></span>

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

### <span data-ttu-id="b7b30-146">-SourcePathOrExtension</span><span class="sxs-lookup"><span data-stu-id="b7b30-146">-SourcePathOrExtension</span></span>

<span data-ttu-id="b7b30-147">Sökväg till filen eller filtypen för det innehåll som Authenticode-signaturen hämtas för.</span><span class="sxs-lookup"><span data-stu-id="b7b30-147">Path to the file or file type of the content for which the Authenticode signature is retrieved.</span></span> <span data-ttu-id="b7b30-148">Den här parametern används med **innehåll** där fil innehåll skickas som en byte mat ris.</span><span class="sxs-lookup"><span data-stu-id="b7b30-148">This parameter is used with **Content** where file content is passed as a byte array.</span></span>

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

### <span data-ttu-id="b7b30-149">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b7b30-149">CommonParameters</span></span>

<span data-ttu-id="b7b30-150">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b7b30-150">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b7b30-151">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="b7b30-151">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="b7b30-152">INDATA</span><span class="sxs-lookup"><span data-stu-id="b7b30-152">INPUTS</span></span>

### <span data-ttu-id="b7b30-153">System. String</span><span class="sxs-lookup"><span data-stu-id="b7b30-153">System.String</span></span>

<span data-ttu-id="b7b30-154">Du kan skicka vidare en sträng som innehåller en fil Sök väg till `Get-AuthenticodeSignature` .</span><span class="sxs-lookup"><span data-stu-id="b7b30-154">You can pipe a string that contains a file path to `Get-AuthenticodeSignature`.</span></span>

## <span data-ttu-id="b7b30-155">UTDATA</span><span class="sxs-lookup"><span data-stu-id="b7b30-155">OUTPUTS</span></span>

### <span data-ttu-id="b7b30-156">System. Management. Automation. signatur</span><span class="sxs-lookup"><span data-stu-id="b7b30-156">System.Management.Automation.Signature</span></span>

<span data-ttu-id="b7b30-157">`Get-AuthenticodeSignature` Returnerar ett signatur objekt för varje signatur som det får.</span><span class="sxs-lookup"><span data-stu-id="b7b30-157">`Get-AuthenticodeSignature` returns a signature object for each signature that it gets.</span></span>

## <span data-ttu-id="b7b30-158">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="b7b30-158">NOTES</span></span>

<span data-ttu-id="b7b30-159">Information om Authenticode-signaturer i PowerShell finns [about_Signing](../Microsoft.PowerShell.Core/About/about_Signing.md).</span><span class="sxs-lookup"><span data-stu-id="b7b30-159">For information about Authenticode signatures in PowerShell, see [about_Signing](../Microsoft.PowerShell.Core/About/about_Signing.md).</span></span>

## <span data-ttu-id="b7b30-160">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="b7b30-160">RELATED LINKS</span></span>

[<span data-ttu-id="b7b30-161">Get-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="b7b30-161">Get-ExecutionPolicy</span></span>](Get-ExecutionPolicy.md)

[<span data-ttu-id="b7b30-162">Set-AuthenticodeSignature</span><span class="sxs-lookup"><span data-stu-id="b7b30-162">Set-AuthenticodeSignature</span></span>](Set-AuthenticodeSignature.md)

[<span data-ttu-id="b7b30-163">Set-ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="b7b30-163">Set-ExecutionPolicy</span></span>](Set-ExecutionPolicy.md)

[<span data-ttu-id="b7b30-164">about_Execution_Policies</span><span class="sxs-lookup"><span data-stu-id="b7b30-164">about_Execution_Policies</span></span>](../Microsoft.PowerShell.Core/About/about_Execution_Policies.md)

[<span data-ttu-id="b7b30-165">about_Signing</span><span class="sxs-lookup"><span data-stu-id="b7b30-165">about_Signing</span></span>](../Microsoft.PowerShell.Core/About/about_Signing.md)

