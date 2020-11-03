---
external help file: Microsoft.PowerShell.Archive-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Archive
ms.date: 02/20/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.archive/compress-archive?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Compress-Archive
ms.openlocfilehash: 7bf349c82133b275f0539db7b78c3583d00da31c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265898"
---
# <span data-ttu-id="ee0f0-103">Compress-Archive</span><span class="sxs-lookup"><span data-stu-id="ee0f0-103">Compress-Archive</span></span>

## <span data-ttu-id="ee0f0-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="ee0f0-104">SYNOPSIS</span></span>
<span data-ttu-id="ee0f0-105">Skapar ett komprimerat arkiv eller en komprimerad fil från angivna filer och kataloger.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-105">Creates a compressed archive, or zipped file, from specified files and directories.</span></span>

## <span data-ttu-id="ee0f0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ee0f0-106">SYNTAX</span></span>

### <span data-ttu-id="ee0f0-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="ee0f0-107">Path (Default)</span></span>

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ee0f0-108">PathWithUpdate</span><span class="sxs-lookup"><span data-stu-id="ee0f0-108">PathWithUpdate</span></span>

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>] -Update
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ee0f0-109">PathWithForce</span><span class="sxs-lookup"><span data-stu-id="ee0f0-109">PathWithForce</span></span>

```
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-CompressionLevel <String>] -Force
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ee0f0-110">LiteralPathWithUpdate</span><span class="sxs-lookup"><span data-stu-id="ee0f0-110">LiteralPathWithUpdate</span></span>

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 -Update [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ee0f0-111">LiteralPathWithForce</span><span class="sxs-lookup"><span data-stu-id="ee0f0-111">LiteralPathWithForce</span></span>

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 -Force [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="ee0f0-112">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="ee0f0-112">LiteralPath</span></span>

```
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-CompressionLevel <String>]
 [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ee0f0-113">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ee0f0-113">DESCRIPTION</span></span>

<span data-ttu-id="ee0f0-114">`Compress-Archive`Cmdleten skapar en komprimerad eller zippad Arkiv fil från en eller flera angivna filer eller kataloger.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-114">The `Compress-Archive` cmdlet creates a compressed, or zipped, archive file from one or more specified files or directories.</span></span> <span data-ttu-id="ee0f0-115">Ett arkiv paketerar flera filer, med valfri komprimering, i en enda zippad fil för enklare distribution och lagring.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-115">An archive packages multiple files, with optional compression, into a single zipped file for easier distribution and storage.</span></span> <span data-ttu-id="ee0f0-116">En arkivfil kan komprimeras med hjälp av den Compression-algoritm som anges av parametern **CompressionLevel** .</span><span class="sxs-lookup"><span data-stu-id="ee0f0-116">An archive file can be compressed by using the compression algorithm specified by the **CompressionLevel** parameter.</span></span>

<span data-ttu-id="ee0f0-117">`Compress-Archive`Cmdlet: en använder Microsoft .NET API [System.IO.Compression.Zip-arkivet](/dotnet/api/system.io.compression.ziparchive) för att komprimera filer.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-117">The `Compress-Archive` cmdlet uses the Microsoft .NET API [System.IO.Compression.ZipArchive](/dotnet/api/system.io.compression.ziparchive) to compress files.</span></span>
<span data-ttu-id="ee0f0-118">Den maximala fil storleken är 2 GB eftersom det finns en begränsning i det underliggande API: et.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-118">The maximum file size is 2 GB because there's a limitation of the underlying API.</span></span>

<span data-ttu-id="ee0f0-119">Några exempel använder ihopbuntning för att minska rad längden för kod exemplen.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-119">Some examples use splatting to reduce the line length of the code samples.</span></span> <span data-ttu-id="ee0f0-120">Mer information finns i [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span><span class="sxs-lookup"><span data-stu-id="ee0f0-120">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

## <span data-ttu-id="ee0f0-121">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="ee0f0-121">EXAMPLES</span></span>

### <span data-ttu-id="ee0f0-122">Exempel 1: komprimera filer för att skapa en arkivfil</span><span class="sxs-lookup"><span data-stu-id="ee0f0-122">Example 1: Compress files to create an archive file</span></span>

<span data-ttu-id="ee0f0-123">Det här exemplet komprimerar filer från olika kataloger och skapar en Arkiv fil.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-123">This example compresses files from different directories and creates an archive file.</span></span> <span data-ttu-id="ee0f0-124">Ett jokertecken används för att hämta alla filer med ett visst fil namns tillägg.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-124">A wildcard is used to get all files with a particular file extension.</span></span> <span data-ttu-id="ee0f0-125">Det finns ingen katalog struktur i Arkiv filen eftersom **sökvägen** bara anger fil namn.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-125">There's no directory structure in the archive file because the **Path** only specifies file names.</span></span>

```powershell
$compress = @{
  Path = "C:\Reference\Draftdoc.docx", "C:\Reference\Images\*.vsd"
  CompressionLevel = "Fastest"
  DestinationPath = "C:\Archives\Draft.Zip"
}
Compress-Archive @compress
```

<span data-ttu-id="ee0f0-126">Parametern **Path** accepterar vissa fil namn och fil namn med jokertecken `*.vsd` .</span><span class="sxs-lookup"><span data-stu-id="ee0f0-126">The **Path** parameter accepts specific file names and file names with wildcards, `*.vsd`.</span></span> <span data-ttu-id="ee0f0-127">**Sökvägen** använder en kommaavgränsad lista för att hämta filer från olika kataloger.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-127">The **Path** uses a comma-separated list to get files from different directories.</span></span> <span data-ttu-id="ee0f0-128">Komprimerings nivån är **snabbast** för att minska bearbetnings tiden.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-128">The compression level is **Fastest** to reduce processing time.</span></span> <span data-ttu-id="ee0f0-129">Parametern **DestinationPath** anger platsen för `Draft.zip` filen.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-129">The **DestinationPath** parameter specifies the location for the `Draft.zip` file.</span></span> <span data-ttu-id="ee0f0-130">`Draft.zip`Filen innehåller `Draftdoc.docx` och alla filer med `.vsd` fil namns tillägget.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-130">The `Draft.zip` file contains `Draftdoc.docx` and all the files with a `.vsd` extension.</span></span>

### <span data-ttu-id="ee0f0-131">Exempel 2: komprimera filer med en LiteralPath</span><span class="sxs-lookup"><span data-stu-id="ee0f0-131">Example 2: Compress files using a LiteralPath</span></span>

<span data-ttu-id="ee0f0-132">I det här exemplet komprimeras vissa namngivna filer och en ny arkivfil skapas.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-132">This example compresses specific named files and creates a new archive file.</span></span> <span data-ttu-id="ee0f0-133">Det finns ingen katalog struktur i Arkiv filen eftersom **sökvägen** bara anger fil namn.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-133">There's no directory structure in the archive file because the **Path** only specifies file names.</span></span>

```powershell
$compress = @{
LiteralPath= "C:\Reference\Draft Doc.docx", "C:\Reference\Images\diagram2.vsd"
CompressionLevel = "Fastest"
DestinationPath = "C:\Archives\Draft.Zip"
}
Compress-Archive @compress
```

<span data-ttu-id="ee0f0-134">Absoluta sökvägar och fil namn används eftersom **LiteralPath** -parametern inte accepterar jokertecken.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-134">Absolute path and file names are used because the **LiteralPath** parameter doesn't accept wildcards.</span></span> <span data-ttu-id="ee0f0-135">**Sökvägen** använder en kommaavgränsad lista för att hämta filer från olika kataloger.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-135">The **Path** uses a comma-separated list to get files from different directories.</span></span> <span data-ttu-id="ee0f0-136">Komprimerings nivån är **snabbast** för att minska bearbetnings tiden.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-136">The compression level is **Fastest** to reduce processing time.</span></span> <span data-ttu-id="ee0f0-137">Parametern **DestinationPath** anger platsen för `Draft.zip` filen.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-137">The **DestinationPath** parameter specifies the location for the `Draft.zip` file.</span></span> <span data-ttu-id="ee0f0-138">`Draft.zip`Filen innehåller `Draftdoc.docx` och `diagram2.vsd` .</span><span class="sxs-lookup"><span data-stu-id="ee0f0-138">The `Draft.zip` file only contains `Draftdoc.docx` and `diagram2.vsd`.</span></span>

### <span data-ttu-id="ee0f0-139">Exempel 3: komprimera en katalog som innehåller rot katalogen</span><span class="sxs-lookup"><span data-stu-id="ee0f0-139">Example 3: Compress a directory that includes the root directory</span></span>

<span data-ttu-id="ee0f0-140">Det här exemplet komprimerar en katalog och skapar en arkivfil som **innehåller** rot katalogen och alla dess filer och under kataloger.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-140">This example compresses a directory and creates an archive file that **includes** the root directory, and all its files and subdirectories.</span></span> <span data-ttu-id="ee0f0-141">Arkiv filen har en katalog struktur eftersom **sökvägen** anger en rot Katalog.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-141">The archive file has a directory structure because the **Path** specifies a root directory.</span></span>

```powershell
Compress-Archive -Path C:\Reference -DestinationPath C:\Archives\Draft.zip
```

<span data-ttu-id="ee0f0-142">`Compress-Archive` använder parametern **Path** för att ange rot katalogen `C:\Reference` .</span><span class="sxs-lookup"><span data-stu-id="ee0f0-142">`Compress-Archive` uses the **Path** parameter to specify the root directory, `C:\Reference`.</span></span> <span data-ttu-id="ee0f0-143">Parametern **DestinationPath** anger platsen för Arkiv filen.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-143">The **DestinationPath** parameter specifies the location for the archive file.</span></span> <span data-ttu-id="ee0f0-144">`Draft.zip`Arkivet innehåller `Reference` rot katalogen och alla dess filer och under kataloger.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-144">The `Draft.zip` archive includes the `Reference` root directory, and all its files and subdirectories.</span></span>

### <span data-ttu-id="ee0f0-145">Exempel 4: komprimera en katalog som undantar rot katalogen</span><span class="sxs-lookup"><span data-stu-id="ee0f0-145">Example 4: Compress a directory that excludes the root directory</span></span>

<span data-ttu-id="ee0f0-146">Det här exemplet komprimerar en katalog och skapar en arkivfil som **undantar** rot katalogen eftersom **sökvägen** använder en asterisk () som `*` jokertecken.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-146">This example compresses a directory and creates an archive file that **excludes** the root directory because the **Path** uses an asterisk (`*`) wildcard.</span></span> <span data-ttu-id="ee0f0-147">Arkivet innehåller en katalog struktur som innehåller rot katalogens filer och under kataloger.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-147">The archive contains a directory structure that contains the root directory's files and subdirectories.</span></span>

```powershell
Compress-Archive -Path C:\Reference\* -DestinationPath C:\Archives\Draft.zip
```

<span data-ttu-id="ee0f0-148">`Compress-Archive` använder parametern **Path** för att ange rot katalogen, `C:\Reference` med jokertecknet asterisk ( `*` ).</span><span class="sxs-lookup"><span data-stu-id="ee0f0-148">`Compress-Archive` uses the **Path** parameter to specify the root directory, `C:\Reference` with an asterisk (`*`) wildcard.</span></span> <span data-ttu-id="ee0f0-149">Parametern **DestinationPath** anger platsen för Arkiv filen.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-149">The **DestinationPath** parameter specifies the location for the archive file.</span></span> <span data-ttu-id="ee0f0-150">`Draft.zip`Arkivet innehåller rot katalogens filer och under kataloger.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-150">The `Draft.zip` archive contains the root directory's files and subdirectories.</span></span> <span data-ttu-id="ee0f0-151">`Reference`Rot katalogen är exkluderad från arkivet.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-151">The `Reference` root directory is excluded from the archive.</span></span>

### <span data-ttu-id="ee0f0-152">Exempel 5: komprimera bara filerna i en rot Katalog</span><span class="sxs-lookup"><span data-stu-id="ee0f0-152">Example 5: Compress only the files in a root directory</span></span>

<span data-ttu-id="ee0f0-153">I det här exemplet komprimeras bara filerna i en rot Katalog och en Arkiv fil skapas.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-153">This example compresses only the files in a root directory and creates an archive file.</span></span> <span data-ttu-id="ee0f0-154">Det finns ingen katalog struktur i arkivet eftersom endast filer komprimeras.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-154">There's no directory structure in the archive because only files are compressed.</span></span>

```powershell
Compress-Archive -Path C:\Reference\*.* -DestinationPath C:\Archives\Draft.zip
```

<span data-ttu-id="ee0f0-155">`Compress-Archive` använder parametern **Path** för att ange rot katalogen, `C:\Reference` med ett jokertecken ( **Star-dot-Star** `*.*` ).</span><span class="sxs-lookup"><span data-stu-id="ee0f0-155">`Compress-Archive` uses the **Path** parameter to specify the root directory, `C:\Reference` with a **star-dot-star** (`*.*`) wildcard.</span></span> <span data-ttu-id="ee0f0-156">Parametern **DestinationPath** anger platsen för Arkiv filen.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-156">The **DestinationPath** parameter specifies the location for the archive file.</span></span> <span data-ttu-id="ee0f0-157">`Draft.zip`Arkivet innehåller bara `Reference` rot katalogen filer och rot katalogen är exkluderad.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-157">The `Draft.zip` archive only contains the `Reference` root directory's files and the root directory is excluded.</span></span>

### <span data-ttu-id="ee0f0-158">Exempel 6: Använd pipelinen för att arkivera filer</span><span class="sxs-lookup"><span data-stu-id="ee0f0-158">Example 6: Use the pipeline to archive files</span></span>

<span data-ttu-id="ee0f0-159">Det här exemplet skickar filer ned pipelinen för att skapa ett arkiv.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-159">This example sends files down the pipeline to create an archive.</span></span> <span data-ttu-id="ee0f0-160">Det finns ingen katalog struktur i Arkiv filen eftersom **sökvägen** bara anger fil namn.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-160">There's no directory structure in the archive file because the **Path** only specifies file names.</span></span>

```powershell
Get-ChildItem -Path C:\Reference\Afile.txt, C:\Reference\Images\Bfile.txt |
  Compress-Archive -DestinationPath C:\Archives\PipelineFiles.zip
```

<span data-ttu-id="ee0f0-161">`Get-ChildItem` använder parametern **Path** för att ange två filer från olika kataloger.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-161">`Get-ChildItem` uses the **Path** parameter to specify two files from different directories.</span></span> <span data-ttu-id="ee0f0-162">Varje fil representeras av ett **fileinfo** -objekt och skickas till pipelinen `Compress-Archive` .</span><span class="sxs-lookup"><span data-stu-id="ee0f0-162">Each file is represented by a **FileInfo** object and is sent down the pipeline to `Compress-Archive`.</span></span>
<span data-ttu-id="ee0f0-163">De två angivna filerna arkiveras i `PipelineFiles.zip` .</span><span class="sxs-lookup"><span data-stu-id="ee0f0-163">The two specified files are archived in `PipelineFiles.zip`.</span></span>

### <span data-ttu-id="ee0f0-164">Exempel 7: Använd pipelinen för att arkivera en katalog</span><span class="sxs-lookup"><span data-stu-id="ee0f0-164">Example 7: Use the pipeline to archive a directory</span></span>

<span data-ttu-id="ee0f0-165">I det här exemplet skickas en katalog ned i pipeline för att skapa ett arkiv.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-165">This example sends a directory down the pipeline to create an archive.</span></span> <span data-ttu-id="ee0f0-166">Filer skickas som **fileinfo** -objekt och kataloger som **DirectoryInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-166">Files are sent as **FileInfo** objects and directories as **DirectoryInfo** objects.</span></span> <span data-ttu-id="ee0f0-167">Arkivets katalog struktur innehåller inte rot katalogen, men dess filer och under kataloger ingår i arkivet.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-167">The archive's directory structure doesn't include the root directory, but its files and subdirectories are included in the archive.</span></span>

```powershell
Get-ChildItem -Path C:\LogFiles | Compress-Archive -DestinationPath C:\Archives\PipelineDir.zip
```

<span data-ttu-id="ee0f0-168">`Get-ChildItem` använder parametern **Path** för att ange `C:\LogFiles` rot katalogen.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-168">`Get-ChildItem` uses the **Path** parameter to specify the `C:\LogFiles` root directory.</span></span> <span data-ttu-id="ee0f0-169">Varje **fileinfo** -och **DirectoryInfo** -objekt skickas ned pipelinen.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-169">Each **FileInfo** and **DirectoryInfo** object is sent down the pipeline.</span></span>

<span data-ttu-id="ee0f0-170">`Compress-Archive` lägger till varje objekt i `PipelineDir.zip` arkivet.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-170">`Compress-Archive` adds each object to the `PipelineDir.zip` archive.</span></span> <span data-ttu-id="ee0f0-171">Parametern **Path** har inte angetts eftersom pipeline-objekten tas emot i parameter position 0.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-171">The **Path** parameter isn't specified because the pipeline objects are received into parameter position 0.</span></span>

### <span data-ttu-id="ee0f0-172">Exempel 8: hur rekursion kan påverka Arkiv</span><span class="sxs-lookup"><span data-stu-id="ee0f0-172">Example 8: How recursion can affect archives</span></span>

<span data-ttu-id="ee0f0-173">Det här exemplet visar hur rekursion kan duplicera filer i arkivet.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-173">This example shows how recursion can duplicate files in your archive.</span></span> <span data-ttu-id="ee0f0-174">Om du till exempel använder `Get-ChildItem` med parametern **rekursivt** .</span><span class="sxs-lookup"><span data-stu-id="ee0f0-174">For example, if you use `Get-ChildItem` with the **Recurse** parameter.</span></span> <span data-ttu-id="ee0f0-175">Som rekursion-processer skickas varje **fileinfo** -och **DirectoryInfo** -objekt nedåt i pipelinen och läggs till i arkivet.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-175">As recursion processes, each **FileInfo** and **DirectoryInfo** object is sent down the pipeline and added to the archive.</span></span>

```powershell
Get-ChildItem -Path C:\TestLog -Recurse |
  Compress-Archive -DestinationPath C:\Archives\PipelineRecurse.zip
```

<span data-ttu-id="ee0f0-176">`C:\TestLog`Katalogen innehåller inte några filer.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-176">The `C:\TestLog` directory doesn't contain any files.</span></span> <span data-ttu-id="ee0f0-177">Den innehåller en under katalog med namnet `testsub` som innehåller `testlog.txt` filen.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-177">It does contain a subdirectory named `testsub` that contains the `testlog.txt` file.</span></span>

<span data-ttu-id="ee0f0-178">`Get-ChildItem` använder parametern **Path** för att ange rot katalogen `C:\TestLog` .</span><span class="sxs-lookup"><span data-stu-id="ee0f0-178">`Get-ChildItem` uses the **Path** parameter to specify the root directory, `C:\TestLog`.</span></span> <span data-ttu-id="ee0f0-179">**Rekursivt** -parametern bearbetar filer och kataloger.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-179">The **Recurse** parameter processes the files and directories.</span></span> <span data-ttu-id="ee0f0-180">Ett **DirectoryInfo** -objekt skapas för `testsub` och ett **fileinfo** -objekt `testlog.txt` .</span><span class="sxs-lookup"><span data-stu-id="ee0f0-180">A **DirectoryInfo** object is created for `testsub` and a **FileInfo** object `testlog.txt`.</span></span>

<span data-ttu-id="ee0f0-181">Varje objekt skickas ned pipelinen till `Compress-Archive` .</span><span class="sxs-lookup"><span data-stu-id="ee0f0-181">Each object is sent down the pipeline to `Compress-Archive`.</span></span> <span data-ttu-id="ee0f0-182">**DestinationPath** anger platsen för Arkiv filen.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-182">The **DestinationPath** specifies the location for the archive file.</span></span> <span data-ttu-id="ee0f0-183">Parametern **Path** har inte angetts eftersom pipeline-objekten tas emot i parameter position 0.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-183">The **Path** parameter isn't specified because the pipeline objects are received into parameter position 0.</span></span>

<span data-ttu-id="ee0f0-184">Följande sammanfattning beskriver det `PipelineRecurse.zip` arkiverade innehållet som innehåller en duplicerad fil:</span><span class="sxs-lookup"><span data-stu-id="ee0f0-184">The following summary describes the `PipelineRecurse.zip` archive's contents that contains a duplicate file:</span></span>

- <span data-ttu-id="ee0f0-185">**DirectoryInfo** -objektet skapar `testsub` katalogen och innehåller `testlog.txt` filen som visar den ursprungliga katalog strukturen.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-185">The **DirectoryInfo** object creates the `testsub` directory and contains the `testlog.txt` file, which reflects the original directory structure.</span></span>
- <span data-ttu-id="ee0f0-186">**Fileinfo** -objektet skapar en dubblett `testlog.txt` i arkivets rot.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-186">The **FileInfo** object creates a duplicate `testlog.txt` in the archive's root.</span></span> <span data-ttu-id="ee0f0-187">Den duplicerade filen skapas eftersom rekursion skickade ett fil objekt till `Compress-Archive` .</span><span class="sxs-lookup"><span data-stu-id="ee0f0-187">The duplicate file is created because recursion sent a file object to `Compress-Archive`.</span></span> <span data-ttu-id="ee0f0-188">Det här beteendet är förväntat eftersom varje objekt som skickas i pipelinen läggs till i arkivet.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-188">This behavior is expected because each object sent down the pipeline is added to the archive.</span></span>

### <span data-ttu-id="ee0f0-189">Exempel 9: uppdatera en befintlig arkivfil</span><span class="sxs-lookup"><span data-stu-id="ee0f0-189">Example 9: Update an existing archive file</span></span>

<span data-ttu-id="ee0f0-190">Det här exemplet uppdaterar en befintlig arkivfil, `Draft.Zip` i `C:\Archives` katalogen.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-190">This example updates an existing archive file, `Draft.Zip`, in the `C:\Archives` directory.</span></span> <span data-ttu-id="ee0f0-191">I det här exemplet innehåller den befintliga Arkiv filen rot katalogen och dess filer och under kataloger.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-191">In this example, the existing archive file contains the root directory, and its files and subdirectories.</span></span>

```powershell
Compress-Archive -Path C:\Reference -Update -DestinationPath C:\Archives\Draft.Zip
```

<span data-ttu-id="ee0f0-192">Kommandot uppdateras `Draft.Zip` med nyare versioner av befintliga filer i `C:\Reference` katalogen och dess under kataloger.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-192">The command updates `Draft.Zip` with newer versions of existing files in the `C:\Reference` directory and its subdirectories.</span></span> <span data-ttu-id="ee0f0-193">Och nya filer som har lagts till i `C:\Reference` eller dess under kataloger ingår i det uppdaterade `Draft.Zip` arkivet.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-193">And, new files that were added to `C:\Reference` or its subdirectories are included in the updated `Draft.Zip` archive.</span></span>

## <span data-ttu-id="ee0f0-194">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="ee0f0-194">PARAMETERS</span></span>

### <span data-ttu-id="ee0f0-195">-CompressionLevel</span><span class="sxs-lookup"><span data-stu-id="ee0f0-195">-CompressionLevel</span></span>

<span data-ttu-id="ee0f0-196">Anger hur mycket komprimering som ska gälla när du skapar arkiv filen.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-196">Specifies how much compression to apply when you're creating the archive file.</span></span> <span data-ttu-id="ee0f0-197">Snabbare komprimering kräver kortare tid för att skapa filen, men kan resultera i större fil storlekar.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-197">Faster compression requires less time to create the file, but can result in larger file sizes.</span></span>

<span data-ttu-id="ee0f0-198">Om den här parametern inte anges använder kommandot standardvärdet, **optimal**.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-198">If this parameter isn't specified, the command uses the default value, **Optimal**.</span></span>

<span data-ttu-id="ee0f0-199">Följande är de acceptabla värdena för den här parametern:</span><span class="sxs-lookup"><span data-stu-id="ee0f0-199">The following are the acceptable values for this parameter:</span></span>

- <span data-ttu-id="ee0f0-200">**Snabbast**.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-200">**Fastest**.</span></span> <span data-ttu-id="ee0f0-201">Använd den snabbaste komprimerings metoden som är tillgänglig för att minska bearbetnings tiden.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-201">Use the fastest compression method available to reduce processing time.</span></span> <span data-ttu-id="ee0f0-202">Snabbare komprimering kan resultera i större fil storlekar.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-202">Faster compression can result in larger file sizes.</span></span>
- <span data-ttu-id="ee0f0-203">**Nocompression**.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-203">**NoCompression**.</span></span> <span data-ttu-id="ee0f0-204">Komprimerar inte källfilerna.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-204">Doesn't compress the source files.</span></span>
- <span data-ttu-id="ee0f0-205">**Optimalt**.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-205">**Optimal**.</span></span> <span data-ttu-id="ee0f0-206">Bearbetnings tiden beror på fil storleken.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-206">Processing time is dependent on file size.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Optimal, NoCompression, Fastest

Required: False
Position: Named
Default value: Optimal
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ee0f0-207">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ee0f0-207">-Confirm</span></span>

<span data-ttu-id="ee0f0-208">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-208">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ee0f0-209">– DestinationPath</span><span class="sxs-lookup"><span data-stu-id="ee0f0-209">-DestinationPath</span></span>

<span data-ttu-id="ee0f0-210">Den här parametern är obligatorisk och anger sökvägen till den arkiverade utdatafilen.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-210">This parameter is required and specifies the path to the archive output file.</span></span> <span data-ttu-id="ee0f0-211">**DestinationPath** ska innehålla namnet på den zippade filen och antingen den absoluta eller relativa sökvägen till den zippade filen.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-211">The **DestinationPath** should include the name of the zipped file, and either the absolute or relative path to the zipped file.</span></span>

<span data-ttu-id="ee0f0-212">Om fil namnet i **DestinationPath** inte har något `.zip` fil namns tillägg lägger cmdleten till `.zip` fil namns tillägget.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-212">If the file name in **DestinationPath** doesn't have a `.zip` file name extension, the cmdlet adds the `.zip` file name extension.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ee0f0-213">-Force</span><span class="sxs-lookup"><span data-stu-id="ee0f0-213">-Force</span></span>

<span data-ttu-id="ee0f0-214">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-214">Forces the command to run without asking for user confirmation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PathWithForce, LiteralPathWithForce
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ee0f0-215">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="ee0f0-215">-LiteralPath</span></span>

<span data-ttu-id="ee0f0-216">Anger sökvägen eller Sök vägarna till de filer som du vill lägga till i den arkiverade zip-filen.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-216">Specifies the path or paths to the files that you want to add to the archive zipped file.</span></span> <span data-ttu-id="ee0f0-217">Till skillnad från parametern **Path** används värdet för **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-217">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="ee0f0-218">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-218">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="ee0f0-219">Om sökvägen innehåller escape-tecken, omger du varje escape-tecken inom enkla citat tecken för att instruera PowerShell att inte tolka några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-219">If the path includes escape characters, enclose each escape character in single quotation marks, to instruct PowerShell not to interpret any characters as escape sequences.</span></span>
<span data-ttu-id="ee0f0-220">Om du vill ange flera sökvägar och inkludera filer på flera platser i den zippade filen använder du kommatecken för att avgränsa Sök vägarna.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-220">To specify multiple paths, and include files in multiple locations in your output zipped file, use commas to separate the paths.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPathWithUpdate, LiteralPathWithForce, LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="ee0f0-221">– PassThru</span><span class="sxs-lookup"><span data-stu-id="ee0f0-221">-PassThru</span></span>

<span data-ttu-id="ee0f0-222">Gör att cmdleten genererar ett fil objekt som representerar den skapade arkivfil.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-222">Causes the cmdlet to output a file object representing the archive file created.</span></span>

<span data-ttu-id="ee0f0-223">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-223">This parameter was introduced in PowerShell 6.0.</span></span>

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

### <span data-ttu-id="ee0f0-224">-Path</span><span class="sxs-lookup"><span data-stu-id="ee0f0-224">-Path</span></span>

<span data-ttu-id="ee0f0-225">Anger sökvägen eller Sök vägarna till de filer som du vill lägga till i den arkiverade zip-filen.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-225">Specifies the path or paths to the files that you want to add to the archive zipped file.</span></span> <span data-ttu-id="ee0f0-226">Om du vill ange flera sökvägar och inkludera filer på flera platser använder du kommatecken för att avgränsa Sök vägarna.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-226">To specify multiple paths, and include files in multiple locations, use commas to separate the paths.</span></span>

<span data-ttu-id="ee0f0-227">Den här parametern accepterar jokertecken.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-227">This parameter accepts wildcard characters.</span></span> <span data-ttu-id="ee0f0-228">Med jokertecken kan du lägga till alla filer i en katalog till Arkiv filen.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-228">Wildcard characters allow you to add all files in a directory to your archive file.</span></span>

<span data-ttu-id="ee0f0-229">Att använda jokertecken med en rot Katalog påverkar arkivets innehåll:</span><span class="sxs-lookup"><span data-stu-id="ee0f0-229">Using wildcards with a root directory affects the archive's contents:</span></span>

- <span data-ttu-id="ee0f0-230">Om du vill skapa ett arkiv som **innehåller** rot katalogen och alla dess filer och under kataloger, anger du rot katalogen i **sökvägen** utan jokertecken.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-230">To create an archive that **includes** the root directory, and all its files and subdirectories, specify the root directory in the **Path** without wildcards.</span></span> <span data-ttu-id="ee0f0-231">Exempelvis: `-Path C:\Reference`</span><span class="sxs-lookup"><span data-stu-id="ee0f0-231">For example: `-Path C:\Reference`</span></span>
- <span data-ttu-id="ee0f0-232">Om du vill skapa ett arkiv som **undantar** rot katalogen, men zips alla filer och under kataloger, använder du jokertecknet asterisk ( `*` ).</span><span class="sxs-lookup"><span data-stu-id="ee0f0-232">To create an archive that **excludes** the root directory, but zips all its files and subdirectories, use the asterisk (`*`) wildcard.</span></span> <span data-ttu-id="ee0f0-233">Exempelvis: `-Path C:\Reference\*`</span><span class="sxs-lookup"><span data-stu-id="ee0f0-233">For example: `-Path C:\Reference\*`</span></span>
- <span data-ttu-id="ee0f0-234">Om du vill skapa ett arkiv som endast zips filerna i rot katalogen använder du jokertecknet **Star-dot-Star** ( `*.*` ).</span><span class="sxs-lookup"><span data-stu-id="ee0f0-234">To create an archive that only zips the files in the root directory, use the **star-dot-star** (`*.*`) wildcard.</span></span> <span data-ttu-id="ee0f0-235">Under kataloger i roten ingår inte i arkivet.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-235">Subdirectories of the root aren't included in the archive.</span></span> <span data-ttu-id="ee0f0-236">Exempelvis: `-Path C:\Reference\*.*`</span><span class="sxs-lookup"><span data-stu-id="ee0f0-236">For example: `-Path C:\Reference\*.*`</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path, PathWithUpdate, PathWithForce
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="ee0f0-237">-Uppdatera</span><span class="sxs-lookup"><span data-stu-id="ee0f0-237">-Update</span></span>

<span data-ttu-id="ee0f0-238">Uppdaterar det angivna arkivet genom att ersätta äldre fil versioner i arkivet med nyare fil versioner som har samma namn.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-238">Updates the specified archive by replacing older file versions in the archive with newer file versions that have the same names.</span></span> <span data-ttu-id="ee0f0-239">Du kan också lägga till den här parametern för att lägga till filer i ett befintligt arkiv.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-239">You can also add this parameter to add files to an existing archive.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PathWithUpdate, LiteralPathWithUpdate
Aliases:

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="ee0f0-240">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ee0f0-240">-WhatIf</span></span>

<span data-ttu-id="ee0f0-241">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-241">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="ee0f0-242">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-242">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="ee0f0-243">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ee0f0-243">CommonParameters</span></span>

<span data-ttu-id="ee0f0-244">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-244">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ee0f0-245">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ee0f0-245">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ee0f0-246">INDATA</span><span class="sxs-lookup"><span data-stu-id="ee0f0-246">INPUTS</span></span>

### <span data-ttu-id="ee0f0-247">System. String</span><span class="sxs-lookup"><span data-stu-id="ee0f0-247">System.String</span></span>

<span data-ttu-id="ee0f0-248">Du kan skicka vidare en sträng som innehåller en sökväg till en eller flera filer.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-248">You can pipe a string that contains a path to one or more files.</span></span>

## <span data-ttu-id="ee0f0-249">UTDATA</span><span class="sxs-lookup"><span data-stu-id="ee0f0-249">OUTPUTS</span></span>

### <span data-ttu-id="ee0f0-250">System. IO. FileInfo</span><span class="sxs-lookup"><span data-stu-id="ee0f0-250">System.IO.FileInfo</span></span>

<span data-ttu-id="ee0f0-251">Cmdleten returnerar bara ett **fileinfo** -objekt när du använder parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="ee0f0-251">The cmdlet only returns a **FileInfo** object when you use the **PassThru** parameter.</span></span>

## <span data-ttu-id="ee0f0-252">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="ee0f0-252">NOTES</span></span>

<span data-ttu-id="ee0f0-253">Med rekursion och skicka objekt nedåt kan pipelinen duplicera filer i arkivet.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-253">Using recursion and sending objects down the pipeline can duplicate files in your archive.</span></span> <span data-ttu-id="ee0f0-254">Om du till exempel använder `Get-ChildItem` med parametern **rekursivt** , läggs varje **fileinfo** -och **DirectoryInfo** -objekt som skickas ned pipelinen till arkivet.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-254">For example, if you use `Get-ChildItem` with the **Recurse** parameter, each **FileInfo** and **DirectoryInfo** object that's sent down the pipeline is added to the archive.</span></span>

<span data-ttu-id="ee0f0-255">[Zip-filspecifikationen](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) anger inte ett standardiserat sätt för kodnings fil namn som innehåller icke-ASCII-tecken.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-255">The [ZIP file specification](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) does not specify a standard way of encoding filenames that contain non-ASCII characters.</span></span> <span data-ttu-id="ee0f0-256">Cmdlet: en `Compress-Archive` använder UTF-8-kodning.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-256">The `Compress-Archive` cmdlet uses UTF-8 encoding.</span></span> <span data-ttu-id="ee0f0-257">Andra ZIP-arkiv verktyg kan använda ett annat kodnings schema.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-257">Other ZIP archive tools may use a different encoding scheme.</span></span> <span data-ttu-id="ee0f0-258">När filer extraheras med fil namn som inte lagras med UTF-8-kodning, `Expand-Archive` används det råa värde som finns i arkivet.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-258">When extracting files with filenames not stored using UTF-8 encoding, `Expand-Archive` uses the raw value found in the archive.</span></span> <span data-ttu-id="ee0f0-259">Detta kan resultera i ett fil namn som skiljer sig från käll fil namnet som lagras i arkivet.</span><span class="sxs-lookup"><span data-stu-id="ee0f0-259">This can result in a filename that is different than the source filename stored in the archive.</span></span>

## <span data-ttu-id="ee0f0-260">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="ee0f0-260">RELATED LINKS</span></span>

[<span data-ttu-id="ee0f0-261">Expandera – arkivera</span><span class="sxs-lookup"><span data-stu-id="ee0f0-261">Expand-Archive</span></span>](Expand-Archive.md)

[<span data-ttu-id="ee0f0-262">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="ee0f0-262">Get-ChildItem</span></span>](../Microsoft.PowerShell.Management/Get-ChildItem.md)
