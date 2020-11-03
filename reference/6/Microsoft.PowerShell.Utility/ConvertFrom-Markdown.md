---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: PowerShell, cmdlet, markdown
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-markdown?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Markdown
ms.openlocfilehash: efa5e65566e3b80f12f3de5ebd1277bf68c03ff0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267170"
---
# <span data-ttu-id="e9274-103">ConvertFrom-Markdown</span><span class="sxs-lookup"><span data-stu-id="e9274-103">ConvertFrom-Markdown</span></span>

## <span data-ttu-id="e9274-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="e9274-104">SYNOPSIS</span></span>
<span data-ttu-id="e9274-105">Konvertera innehållet i en sträng eller en fil till ett **MarkdownInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="e9274-105">Convert the contents of a string or a file to a **MarkdownInfo** object.</span></span>

## <span data-ttu-id="e9274-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e9274-106">SYNTAX</span></span>

### <span data-ttu-id="e9274-107">PathParamSet (standard)</span><span class="sxs-lookup"><span data-stu-id="e9274-107">PathParamSet (Default)</span></span>

```
ConvertFrom-Markdown [-Path] <String[]> [-AsVT100EncodedString] [<CommonParameters>]
```

### <span data-ttu-id="e9274-108">LiteralParamSet</span><span class="sxs-lookup"><span data-stu-id="e9274-108">LiteralParamSet</span></span>

```
ConvertFrom-Markdown -LiteralPath <String[]> [-AsVT100EncodedString] [<CommonParameters>]
```

### <span data-ttu-id="e9274-109">InputObjParamSet</span><span class="sxs-lookup"><span data-stu-id="e9274-109">InputObjParamSet</span></span>

```
ConvertFrom-Markdown -InputObject <PSObject> [-AsVT100EncodedString] [<CommonParameters>]
```

## <span data-ttu-id="e9274-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e9274-110">DESCRIPTION</span></span>

<span data-ttu-id="e9274-111">Denna cmdlet konverterar det angivna innehållet till en **MarkdownInfo**.</span><span class="sxs-lookup"><span data-stu-id="e9274-111">This cmdlet converts the specified content into a **MarkdownInfo**.</span></span> <span data-ttu-id="e9274-112">När en fil Sök väg anges för parametern **Path** konverteras innehållet i filen.</span><span class="sxs-lookup"><span data-stu-id="e9274-112">When a file path is specified for the **Path** parameter, the contents on the file are converted.</span></span> <span data-ttu-id="e9274-113">Objektet utdata har tre egenskaper:</span><span class="sxs-lookup"><span data-stu-id="e9274-113">The output object has three properties:</span></span>

- <span data-ttu-id="e9274-114">Egenskapen **token** har det abstrakta syntaxs trädet (AST) för det konverterade objektet</span><span class="sxs-lookup"><span data-stu-id="e9274-114">The **Token** property has the abstract syntax tree (AST) of the the converted object</span></span>
- <span data-ttu-id="e9274-115">**HTML-** egenskapen har HTML-konverteringen för angivna inaktuella indatamängdar</span><span class="sxs-lookup"><span data-stu-id="e9274-115">The **Html** property has the HTML conversion of the specified input</span></span>
- <span data-ttu-id="e9274-116">Egenskapen **VT100EncodedString** har den konverterade STRÄNGEN med ANSI (VT100) escape-sekvenser om parametern **AsVT100EncodedString** har angetts</span><span class="sxs-lookup"><span data-stu-id="e9274-116">The **VT100EncodedString** property has the converted string with ANSI (VT100) escape sequences if the **AsVT100EncodedString** parameter was specified</span></span>

<span data-ttu-id="e9274-117">Denna cmdlet introducerades i PowerShell 6,1.</span><span class="sxs-lookup"><span data-stu-id="e9274-117">This cmdlet was introduced in PowerShell 6.1.</span></span>

## <span data-ttu-id="e9274-118">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="e9274-118">EXAMPLES</span></span>

### <span data-ttu-id="e9274-119">Exempel 1: konvertera en fil som innehåller markdown-innehåll till HTML</span><span class="sxs-lookup"><span data-stu-id="e9274-119">Example 1: Convert a file containing Markdown content to HTML</span></span>

```powershell
ConvertFrom-Markdown -Path .\README.md
```

<span data-ttu-id="e9274-120">**MarkdownInfo** -objektet returneras.</span><span class="sxs-lookup"><span data-stu-id="e9274-120">The **MarkdownInfo** object is returned.</span></span> <span data-ttu-id="e9274-121">Egenskapen **tokens** har AST-värdet för det konverterade innehållet i `README.md` filen.</span><span class="sxs-lookup"><span data-stu-id="e9274-121">The **Tokens** property has the AST of the converted content of the `README.md` file.</span></span> <span data-ttu-id="e9274-122">**HTML** -egenskapen har HTML-konverterat innehåll i `README.md` filen.</span><span class="sxs-lookup"><span data-stu-id="e9274-122">The **Html** property has the HTML converted content of the `README.md` file.</span></span>

### <span data-ttu-id="e9274-123">Exempel 2: konvertera en fil som innehåller markdown-innehåll till en VT100-kodad sträng</span><span class="sxs-lookup"><span data-stu-id="e9274-123">Example 2: Convert a file containing Markdown content to a VT100-encoded string</span></span>

```powershell
ConvertFrom-Markdown -Path .\README.md -AsVT100EncodedString
```

<span data-ttu-id="e9274-124">**MarkdownInfo** -objektet returneras.</span><span class="sxs-lookup"><span data-stu-id="e9274-124">The **MarkdownInfo** object is returned.</span></span> <span data-ttu-id="e9274-125">Egenskapen **tokens** har AST-värdet för det konverterade innehållet i `README.md` filen.</span><span class="sxs-lookup"><span data-stu-id="e9274-125">The **Tokens** property has the AST of the converted content of the `README.md` file.</span></span> <span data-ttu-id="e9274-126">Egenskapen **VT100EncodedString** har den VT100-kodade sträng konverterade `README.md` filens innehåll.</span><span class="sxs-lookup"><span data-stu-id="e9274-126">The **VT100EncodedString** property has the VT100-encoded string converted content of the `README.md` file.</span></span>

### <span data-ttu-id="e9274-127">Exempel 3: konvertera indatamängds objekt som innehåller markdown-innehåll till en VT100-kodad sträng</span><span class="sxs-lookup"><span data-stu-id="e9274-127">Example 3: Convert input object containing Markdown content to a VT100-encoded string</span></span>

```powershell
Get-Item .\README.md | ConvertFrom-Markdown -AsVT100EncodedString
```

<span data-ttu-id="e9274-128">**MarkdownInfo** -objektet returneras.</span><span class="sxs-lookup"><span data-stu-id="e9274-128">The **MarkdownInfo** object is returned.</span></span> <span data-ttu-id="e9274-129">**Fileinfo** -objektet från `Get-Item` konverteras till en VT100-kodad sträng.</span><span class="sxs-lookup"><span data-stu-id="e9274-129">The **FileInfo** object from `Get-Item` is converted to a VT100-encoded string.</span></span> <span data-ttu-id="e9274-130">Egenskapen **tokens** har AST-värdet för det konverterade innehållet i `README.md` filen.</span><span class="sxs-lookup"><span data-stu-id="e9274-130">The **Tokens** property has the AST of the converted content of the `README.md` file.</span></span> <span data-ttu-id="e9274-131">Egenskapen **VT100EncodedString** har den VT100-kodade sträng konverterade `README.md` filens innehåll.</span><span class="sxs-lookup"><span data-stu-id="e9274-131">The **VT100EncodedString** property has the VT100-encoded string converted content of the `README.md` file.</span></span>

### <span data-ttu-id="e9274-132">Exempel 4: konvertera en sträng som innehåller markdown-innehåll till en VT100-kodad sträng</span><span class="sxs-lookup"><span data-stu-id="e9274-132">Example 4: Convert a string containing Markdown content to a VT100-encoded string</span></span>

```powershell
"**Bold text**" | ConvertFrom-Markdown -AsVT100EncodedString
```

<span data-ttu-id="e9274-133">**MarkdownInfo** -objektet returneras.</span><span class="sxs-lookup"><span data-stu-id="e9274-133">The **MarkdownInfo** object is returned.</span></span> <span data-ttu-id="e9274-134">Den angivna strängen `**Bold text**` konverteras till en VT100-kodad sträng och är tillgänglig i egenskapen **VT100EncodedString** .</span><span class="sxs-lookup"><span data-stu-id="e9274-134">The specified string `**Bold text**` is converted to a VT100-encoded string and available in **VT100EncodedString** property.</span></span>

## <span data-ttu-id="e9274-135">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="e9274-135">PARAMETERS</span></span>

### <span data-ttu-id="e9274-136">-AsVT100EncodedString</span><span class="sxs-lookup"><span data-stu-id="e9274-136">-AsVT100EncodedString</span></span>

<span data-ttu-id="e9274-137">Anger om utdata ska kodas som en sträng med VT100 Escape-koder.</span><span class="sxs-lookup"><span data-stu-id="e9274-137">Specifies if the output should be encoded as a string with VT100 escape codes.</span></span>

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

### <span data-ttu-id="e9274-138">– InputObject</span><span class="sxs-lookup"><span data-stu-id="e9274-138">-InputObject</span></span>

<span data-ttu-id="e9274-139">Anger det objekt som ska konverteras.</span><span class="sxs-lookup"><span data-stu-id="e9274-139">Specifies the object to be converted.</span></span> <span data-ttu-id="e9274-140">När ett objekt av typen **system. String** anges konverteras strängen.</span><span class="sxs-lookup"><span data-stu-id="e9274-140">When an object of type **System.String** is specified, the string is converted.</span></span> <span data-ttu-id="e9274-141">När ett objekt av typen **system. io. fileinfo** anges konverteras innehållet i den fil som anges av objektet.</span><span class="sxs-lookup"><span data-stu-id="e9274-141">When an object of type **System.IO.FileInfo** is specified, the contents of the file specified by the object are converted.</span></span> <span data-ttu-id="e9274-142">Objekt av någon annan typ resulterar i ett fel.</span><span class="sxs-lookup"><span data-stu-id="e9274-142">Objects of any other type result in an error.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: InputObjParamSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e9274-143">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="e9274-143">-LiteralPath</span></span>

<span data-ttu-id="e9274-144">Anger en sökväg till filen som ska konverteras.</span><span class="sxs-lookup"><span data-stu-id="e9274-144">Specifies a path to the file to be converted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralParamSet
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e9274-145">-Path</span><span class="sxs-lookup"><span data-stu-id="e9274-145">-Path</span></span>

<span data-ttu-id="e9274-146">Anger en sökväg till filen som ska konverteras.</span><span class="sxs-lookup"><span data-stu-id="e9274-146">Specifies a path to the file to be converted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PathParamSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="e9274-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e9274-147">CommonParameters</span></span>

<span data-ttu-id="e9274-148">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e9274-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e9274-149">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e9274-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e9274-150">INDATA</span><span class="sxs-lookup"><span data-stu-id="e9274-150">INPUTS</span></span>

### <span data-ttu-id="e9274-151">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="e9274-151">System.Management.Automation.PSObject</span></span>

## <span data-ttu-id="e9274-152">UTDATA</span><span class="sxs-lookup"><span data-stu-id="e9274-152">OUTPUTS</span></span>

### <span data-ttu-id="e9274-153">Microsoft. PowerShell. MarkdownRender. MarkdownInfo</span><span class="sxs-lookup"><span data-stu-id="e9274-153">Microsoft.PowerShell.MarkdownRender.MarkdownInfo</span></span>

## <span data-ttu-id="e9274-154">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="e9274-154">NOTES</span></span>

## <span data-ttu-id="e9274-155">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="e9274-155">RELATED LINKS</span></span>

[<span data-ttu-id="e9274-156">Markdown-tolkare</span><span class="sxs-lookup"><span data-stu-id="e9274-156">Markdown Parser</span></span>](https://github.com/lunet-io/markdig)

[<span data-ttu-id="e9274-157">ANSI Escape-kod</span><span class="sxs-lookup"><span data-stu-id="e9274-157">ANSI escape code</span></span>](https://wikipedia.org/wiki/ANSI_escape_code)
