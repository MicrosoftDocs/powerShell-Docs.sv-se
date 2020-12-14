---
external help file: Microsoft.PowerShell.Archive-help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Archive
ms.date: 07/17/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.archive/expand-archive?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Expand-Archive
ms.openlocfilehash: a4cf8970156f524578f7c9747aef1ffbf9f3eb58
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710260"
---
# <span data-ttu-id="8399f-102">Expand-Archive</span><span class="sxs-lookup"><span data-stu-id="8399f-102">Expand-Archive</span></span>

## <span data-ttu-id="8399f-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="8399f-103">SYNOPSIS</span></span>
<span data-ttu-id="8399f-104">Extraherar filer från en angiven arkivfil (zippad) fil.</span><span class="sxs-lookup"><span data-stu-id="8399f-104">Extracts files from a specified archive (zipped) file.</span></span>

## <span data-ttu-id="8399f-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8399f-105">SYNTAX</span></span>

### <span data-ttu-id="8399f-106">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="8399f-106">Path (Default)</span></span>

```
Expand-Archive [-Path] <String> [[-DestinationPath] <String>] [-Force] [-PassThru] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="8399f-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="8399f-107">LiteralPath</span></span>

```
Expand-Archive -LiteralPath <String> [[-DestinationPath] <String>] [-Force] [-PassThru] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="8399f-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="8399f-108">DESCRIPTION</span></span>

<span data-ttu-id="8399f-109">`Expand-Archive`Cmdleten extraherar filer från en angiven zippad arkivfil till en angiven målmapp.</span><span class="sxs-lookup"><span data-stu-id="8399f-109">The `Expand-Archive` cmdlet extracts files from a specified zipped archive file to a specified destination folder.</span></span> <span data-ttu-id="8399f-110">En arkivfil gör att flera filer kan paketeras och eventuellt komprimeras till en enda zippad fil för enklare distribution och lagring.</span><span class="sxs-lookup"><span data-stu-id="8399f-110">An archive file allows multiple files to be packaged, and optionally compressed, into a single zipped file for easier distribution and storage.</span></span>

## <span data-ttu-id="8399f-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="8399f-111">EXAMPLES</span></span>

### <span data-ttu-id="8399f-112">Exempel 1: extrahera innehållet i ett arkiv</span><span class="sxs-lookup"><span data-stu-id="8399f-112">Example 1: Extract the contents of an archive</span></span>

<span data-ttu-id="8399f-113">I det här exemplet extraheras innehållet i en befintlig arkivfil till den mapp som anges av parametern **DestinationPath** .</span><span class="sxs-lookup"><span data-stu-id="8399f-113">This example extracts the contents of an existing archive file into the folder specified by the **DestinationPath** parameter.</span></span>

```powershell
Expand-Archive -LiteralPath 'C:\Archives\Draft[v1].Zip' -DestinationPath C:\Reference
```

<span data-ttu-id="8399f-114">I det här exemplet används parametern **LiteralPath** eftersom fil namnet innehåller tecken som kan tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="8399f-114">In this example, the **LiteralPath** parameter is used because the filename contains characters that could be interpreted as wildcards.</span></span>

### <span data-ttu-id="8399f-115">Exempel 2: extrahera innehållet i ett arkiv i den aktuella mappen</span><span class="sxs-lookup"><span data-stu-id="8399f-115">Example 2: Extract the contents of an archive in the current folder</span></span>

<span data-ttu-id="8399f-116">I det här exemplet extraheras innehållet i en befintlig arkivfil i den aktuella mappen till den mapp som anges av parametern **DestinationPath** .</span><span class="sxs-lookup"><span data-stu-id="8399f-116">This example extracts the contents of an existing archive file in the current folder into the folder specified by the **DestinationPath** parameter.</span></span>

```powershell
Expand-Archive -Path Draftv2.Zip -DestinationPath C:\Reference
```

## <span data-ttu-id="8399f-117">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="8399f-117">PARAMETERS</span></span>

### <span data-ttu-id="8399f-118">– DestinationPath</span><span class="sxs-lookup"><span data-stu-id="8399f-118">-DestinationPath</span></span>

<span data-ttu-id="8399f-119">Som standard `Expand-Archive` skapar en mapp på den aktuella platsen som är samma namn som zip-filen.</span><span class="sxs-lookup"><span data-stu-id="8399f-119">By default, `Expand-Archive` creates a folder in the current location that is the same name as the ZIP file.</span></span> <span data-ttu-id="8399f-120">Parametern låter dig ange sökvägen till en annan mapp.</span><span class="sxs-lookup"><span data-stu-id="8399f-120">The parameter allows you to specify the path to a different folder.</span></span> <span data-ttu-id="8399f-121">Målmappen skapas om den inte finns.</span><span class="sxs-lookup"><span data-stu-id="8399f-121">The target folder is created if it does not exist.</span></span>

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

### <span data-ttu-id="8399f-122">-Force</span><span class="sxs-lookup"><span data-stu-id="8399f-122">-Force</span></span>

<span data-ttu-id="8399f-123">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="8399f-123">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="8399f-124">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="8399f-124">-LiteralPath</span></span>

<span data-ttu-id="8399f-125">Anger sökvägen till en Arkiv fil.</span><span class="sxs-lookup"><span data-stu-id="8399f-125">Specifies the path to an archive file.</span></span> <span data-ttu-id="8399f-126">Till skillnad från parametern **Path** används värdet för **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="8399f-126">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="8399f-127">Jokertecken stöds inte.</span><span class="sxs-lookup"><span data-stu-id="8399f-127">Wildcard characters are not supported.</span></span> <span data-ttu-id="8399f-128">Om sökvägen innehåller escape-tecken, omger du varje escape-tecken inom enkla citat tecken för att instruera PowerShell att inte tolka några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="8399f-128">If the path includes escape characters, enclose each escape character in single quotation marks, to instruct PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="8399f-129">– PassThru</span><span class="sxs-lookup"><span data-stu-id="8399f-129">-PassThru</span></span>

<span data-ttu-id="8399f-130">Gör att cmdleten skickar en lista med filerna expanderade från arkivet.</span><span class="sxs-lookup"><span data-stu-id="8399f-130">Causes the cmdlet to output a list of the files expanded from the archive.</span></span>

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

### <span data-ttu-id="8399f-131">-Path</span><span class="sxs-lookup"><span data-stu-id="8399f-131">-Path</span></span>

<span data-ttu-id="8399f-132">Anger sökvägen till Arkiv filen.</span><span class="sxs-lookup"><span data-stu-id="8399f-132">Specifies the path to the archive file.</span></span>

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

### <span data-ttu-id="8399f-133">-Confirm</span><span class="sxs-lookup"><span data-stu-id="8399f-133">-Confirm</span></span>

<span data-ttu-id="8399f-134">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="8399f-134">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="8399f-135">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="8399f-135">-WhatIf</span></span>

<span data-ttu-id="8399f-136">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="8399f-136">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="8399f-137">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="8399f-137">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="8399f-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8399f-138">CommonParameters</span></span>
<span data-ttu-id="8399f-139">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8399f-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8399f-140">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8399f-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8399f-141">INDATA</span><span class="sxs-lookup"><span data-stu-id="8399f-141">INPUTS</span></span>

### <span data-ttu-id="8399f-142">System. String</span><span class="sxs-lookup"><span data-stu-id="8399f-142">System.String</span></span>

<span data-ttu-id="8399f-143">Du kan skicka vidare en sträng som innehåller en sökväg till en befintlig arkivfil.</span><span class="sxs-lookup"><span data-stu-id="8399f-143">You can pipe a string that contains a path to an existing archive file.</span></span>

## <span data-ttu-id="8399f-144">UTDATA</span><span class="sxs-lookup"><span data-stu-id="8399f-144">OUTPUTS</span></span>

### <span data-ttu-id="8399f-145">System. IO. FileSystemInfo</span><span class="sxs-lookup"><span data-stu-id="8399f-145">System.IO.FileSystemInfo</span></span>

<span data-ttu-id="8399f-146">När `-PassThru` parametern används, matar cmdleten ut en lista över filer som har expanderats från arkivet.</span><span class="sxs-lookup"><span data-stu-id="8399f-146">When the `-PassThru` parameter is used, the cmdlet outputs a list of files that were expanded from the archive.</span></span>

## <span data-ttu-id="8399f-147">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="8399f-147">NOTES</span></span>

<span data-ttu-id="8399f-148">[Zip-filspecifikationen](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) anger inte ett standardiserat sätt för kodnings fil namn som innehåller icke-ASCII-tecken.</span><span class="sxs-lookup"><span data-stu-id="8399f-148">The [ZIP file specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) does not specify a standard way of encoding filenames that contain non-ASCII characters.</span></span> <span data-ttu-id="8399f-149">Cmdlet: en `Compress-Archive` använder UTF-8-kodning.</span><span class="sxs-lookup"><span data-stu-id="8399f-149">The `Compress-Archive` cmdlet uses UTF-8 encoding.</span></span> <span data-ttu-id="8399f-150">Andra ZIP-arkiv verktyg kan använda ett annat kodnings schema.</span><span class="sxs-lookup"><span data-stu-id="8399f-150">Other ZIP archive tools may use a different encoding scheme.</span></span> <span data-ttu-id="8399f-151">När filer extraheras med fil namn som inte lagras med UTF-8-kodning, `Expand-Archive` används det råa värde som finns i arkivet.</span><span class="sxs-lookup"><span data-stu-id="8399f-151">When extracting files with filenames not stored using UTF-8 encoding, `Expand-Archive` uses the raw value found in the archive.</span></span> <span data-ttu-id="8399f-152">Detta kan resultera i ett fil namn som skiljer sig från käll fil namnet som lagras i arkivet.</span><span class="sxs-lookup"><span data-stu-id="8399f-152">This can result in a filename that is different than the source filename stored in the archive.</span></span>

## <span data-ttu-id="8399f-153">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="8399f-153">RELATED LINKS</span></span>

[<span data-ttu-id="8399f-154">Komprimera – arkivera</span><span class="sxs-lookup"><span data-stu-id="8399f-154">Compress-Archive</span></span>](compress-archive.md)
