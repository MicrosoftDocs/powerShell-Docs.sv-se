---
external help file: Microsoft.PowerShell.Archive-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Archive
ms.date: 07/17/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.archive/expand-archive?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Expand-Archive
ms.openlocfilehash: 6b89512ebc786a47ae47dd2cd8f51cb532382e02
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/18/2020
ms.locfileid: "93268089"
---
# <span data-ttu-id="a89e6-103">Expand-Archive</span><span class="sxs-lookup"><span data-stu-id="a89e6-103">Expand-Archive</span></span>

## <span data-ttu-id="a89e6-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="a89e6-104">SYNOPSIS</span></span>
<span data-ttu-id="a89e6-105">Extraherar filer från en angiven arkivfil (zippad) fil.</span><span class="sxs-lookup"><span data-stu-id="a89e6-105">Extracts files from a specified archive (zipped) file.</span></span>

## <span data-ttu-id="a89e6-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a89e6-106">SYNTAX</span></span>

### <span data-ttu-id="a89e6-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="a89e6-107">Path (Default)</span></span>

```
Expand-Archive [-Path] <String> [[-DestinationPath] <String>] [-Force] [-PassThru] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a89e6-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a89e6-108">LiteralPath</span></span>

```
Expand-Archive -LiteralPath <String> [[-DestinationPath] <String>] [-Force] [-PassThru] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="a89e6-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a89e6-109">DESCRIPTION</span></span>

<span data-ttu-id="a89e6-110">`Expand-Archive`Cmdleten extraherar filer från en angiven zippad arkivfil till en angiven målmapp.</span><span class="sxs-lookup"><span data-stu-id="a89e6-110">The `Expand-Archive` cmdlet extracts files from a specified zipped archive file to a specified destination folder.</span></span> <span data-ttu-id="a89e6-111">En arkivfil gör att flera filer kan paketeras och eventuellt komprimeras till en enda zippad fil för enklare distribution och lagring.</span><span class="sxs-lookup"><span data-stu-id="a89e6-111">An archive file allows multiple files to be packaged, and optionally compressed, into a single zipped file for easier distribution and storage.</span></span>

## <span data-ttu-id="a89e6-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="a89e6-112">EXAMPLES</span></span>

### <span data-ttu-id="a89e6-113">Exempel 1: extrahera innehållet i ett arkiv</span><span class="sxs-lookup"><span data-stu-id="a89e6-113">Example 1: Extract the contents of an archive</span></span>

<span data-ttu-id="a89e6-114">I det här exemplet extraheras innehållet i en befintlig arkivfil till den mapp som anges av parametern **DestinationPath** .</span><span class="sxs-lookup"><span data-stu-id="a89e6-114">This example extracts the contents of an existing archive file into the folder specified by the **DestinationPath** parameter.</span></span>

```powershell
Expand-Archive -LiteralPath 'C:\Archives\Draft[v1].Zip' -DestinationPath C:\Reference
```

<span data-ttu-id="a89e6-115">I det här exemplet används parametern **LiteralPath** eftersom fil namnet innehåller tecken som kan tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="a89e6-115">In this example, the **LiteralPath** parameter is used because the filename contains characters that could be interpreted as wildcards.</span></span>

### <span data-ttu-id="a89e6-116">Exempel 2: extrahera innehållet i ett arkiv i den aktuella mappen</span><span class="sxs-lookup"><span data-stu-id="a89e6-116">Example 2: Extract the contents of an archive in the current folder</span></span>

<span data-ttu-id="a89e6-117">I det här exemplet extraheras innehållet i en befintlig arkivfil i den aktuella mappen till den mapp som anges av parametern **DestinationPath** .</span><span class="sxs-lookup"><span data-stu-id="a89e6-117">This example extracts the contents of an existing archive file in the current folder into the folder specified by the **DestinationPath** parameter.</span></span>

```powershell
Expand-Archive -Path Draftv2.Zip -DestinationPath C:\Reference
```

## <span data-ttu-id="a89e6-118">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="a89e6-118">PARAMETERS</span></span>

### <span data-ttu-id="a89e6-119">– DestinationPath</span><span class="sxs-lookup"><span data-stu-id="a89e6-119">-DestinationPath</span></span>

<span data-ttu-id="a89e6-120">Som standard `Expand-Archive` skapar en mapp på den aktuella platsen som är samma namn som zip-filen.</span><span class="sxs-lookup"><span data-stu-id="a89e6-120">By default, `Expand-Archive` creates a folder in the current location that is the same name as the ZIP file.</span></span> <span data-ttu-id="a89e6-121">Parametern låter dig ange sökvägen till en annan mapp.</span><span class="sxs-lookup"><span data-stu-id="a89e6-121">The parameter allows you to specify the path to a different folder.</span></span> <span data-ttu-id="a89e6-122">Målmappen skapas om den inte finns.</span><span class="sxs-lookup"><span data-stu-id="a89e6-122">The target folder is created if it does not exist.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: A folder in the current location
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a89e6-123">-Force</span><span class="sxs-lookup"><span data-stu-id="a89e6-123">-Force</span></span>

<span data-ttu-id="a89e6-124">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="a89e6-124">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="a89e6-125">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a89e6-125">-LiteralPath</span></span>

<span data-ttu-id="a89e6-126">Anger sökvägen till en Arkiv fil.</span><span class="sxs-lookup"><span data-stu-id="a89e6-126">Specifies the path to an archive file.</span></span> <span data-ttu-id="a89e6-127">Till skillnad från parametern **Path** används värdet för **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="a89e6-127">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="a89e6-128">Jokertecken stöds inte.</span><span class="sxs-lookup"><span data-stu-id="a89e6-128">Wildcard characters are not supported.</span></span> <span data-ttu-id="a89e6-129">Om sökvägen innehåller escape-tecken, omger du varje escape-tecken inom enkla citat tecken för att instruera PowerShell att inte tolka några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="a89e6-129">If the path includes escape characters, enclose each escape character in single quotation marks, to instruct PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a89e6-130">– PassThru</span><span class="sxs-lookup"><span data-stu-id="a89e6-130">-PassThru</span></span>

<span data-ttu-id="a89e6-131">Gör att cmdleten skickar en lista med filerna expanderade från arkivet.</span><span class="sxs-lookup"><span data-stu-id="a89e6-131">Causes the cmdlet to output a list of the files expanded from the archive.</span></span>

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

### <span data-ttu-id="a89e6-132">-Path</span><span class="sxs-lookup"><span data-stu-id="a89e6-132">-Path</span></span>

<span data-ttu-id="a89e6-133">Anger sökvägen till Arkiv filen.</span><span class="sxs-lookup"><span data-stu-id="a89e6-133">Specifies the path to the archive file.</span></span>

```yaml
Type: System.String
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a89e6-134">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a89e6-134">-Confirm</span></span>

<span data-ttu-id="a89e6-135">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a89e6-135">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a89e6-136">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a89e6-136">-WhatIf</span></span>

<span data-ttu-id="a89e6-137">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="a89e6-137">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="a89e6-138">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="a89e6-138">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a89e6-139">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a89e6-139">CommonParameters</span></span>
<span data-ttu-id="a89e6-140">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a89e6-140">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a89e6-141">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a89e6-141">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a89e6-142">INDATA</span><span class="sxs-lookup"><span data-stu-id="a89e6-142">INPUTS</span></span>

### <span data-ttu-id="a89e6-143">System. String</span><span class="sxs-lookup"><span data-stu-id="a89e6-143">System.String</span></span>

<span data-ttu-id="a89e6-144">Du kan skicka vidare en sträng som innehåller en sökväg till en befintlig arkivfil.</span><span class="sxs-lookup"><span data-stu-id="a89e6-144">You can pipe a string that contains a path to an existing archive file.</span></span>

## <span data-ttu-id="a89e6-145">UTDATA</span><span class="sxs-lookup"><span data-stu-id="a89e6-145">OUTPUTS</span></span>

### <span data-ttu-id="a89e6-146">System. IO. FileSystemInfo</span><span class="sxs-lookup"><span data-stu-id="a89e6-146">System.IO.FileSystemInfo</span></span>

<span data-ttu-id="a89e6-147">När `-PassThru` parametern används, matar cmdleten ut en lista över filer som har expanderats från arkivet.</span><span class="sxs-lookup"><span data-stu-id="a89e6-147">When the `-PassThru` parameter is used, the cmdlet outputs a list of files that were expanded from the archive.</span></span>

## <span data-ttu-id="a89e6-148">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="a89e6-148">NOTES</span></span>

<span data-ttu-id="a89e6-149">[Zip-filspecifikationen](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) anger inte ett standardiserat sätt för kodnings fil namn som innehåller icke-ASCII-tecken.</span><span class="sxs-lookup"><span data-stu-id="a89e6-149">The [ZIP file specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) does not specify a standard way of encoding filenames that contain non-ASCII characters.</span></span> <span data-ttu-id="a89e6-150">Cmdlet: en `Compress-Archive` använder UTF-8-kodning.</span><span class="sxs-lookup"><span data-stu-id="a89e6-150">The `Compress-Archive` cmdlet uses UTF-8 encoding.</span></span> <span data-ttu-id="a89e6-151">Andra ZIP-arkiv verktyg kan använda ett annat kodnings schema.</span><span class="sxs-lookup"><span data-stu-id="a89e6-151">Other ZIP archive tools may use a different encoding scheme.</span></span> <span data-ttu-id="a89e6-152">När filer extraheras med fil namn som inte lagras med UTF-8-kodning, `Expand-Archive` används det råa värde som finns i arkivet.</span><span class="sxs-lookup"><span data-stu-id="a89e6-152">When extracting files with filenames not stored using UTF-8 encoding, `Expand-Archive` uses the raw value found in the archive.</span></span> <span data-ttu-id="a89e6-153">Detta kan resultera i ett fil namn som skiljer sig från käll fil namnet som lagras i arkivet.</span><span class="sxs-lookup"><span data-stu-id="a89e6-153">This can result in a filename that is different than the source filename stored in the archive.</span></span>

## <span data-ttu-id="a89e6-154">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="a89e6-154">RELATED LINKS</span></span>

[<span data-ttu-id="a89e6-155">Komprimera – arkivera</span><span class="sxs-lookup"><span data-stu-id="a89e6-155">Compress-Archive</span></span>](compress-archive.md)
