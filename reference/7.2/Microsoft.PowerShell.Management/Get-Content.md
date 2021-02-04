---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-content?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Content
ms.openlocfilehash: 078b7c8561bf5821e9cf2791caceaad8152c926a
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/19/2020
ms.locfileid: "97693051"
---
# <span data-ttu-id="bfcca-102">Get-Content</span><span class="sxs-lookup"><span data-stu-id="bfcca-102">Get-Content</span></span>

## <span data-ttu-id="bfcca-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="bfcca-103">SYNOPSIS</span></span>
<span data-ttu-id="bfcca-104">Hämtar innehållet i objektet på den angivna platsen.</span><span class="sxs-lookup"><span data-stu-id="bfcca-104">Gets the content of the item at the specified location.</span></span>

## <span data-ttu-id="bfcca-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bfcca-105">SYNTAX</span></span>

### <span data-ttu-id="bfcca-106">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="bfcca-106">Path (Default)</span></span>

```
Get-Content [-ReadCount <Int64>] [-TotalCount <Int64>] [-Tail <Int32>] [-Path] <String[]>
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Credential <PSCredential>]
 [-Delimiter <String>] [-Wait] [-Raw] [-Encoding <Encoding>] [-AsByteStream] [-Stream <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="bfcca-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="bfcca-107">LiteralPath</span></span>

```
Get-Content [-ReadCount <Int64>] [-TotalCount <Int64>] [-Tail <Int32>] -LiteralPath <String[]>
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Credential <PSCredential>]
 [-Delimiter <String>] [-Wait] [-Raw] [-Encoding <Encoding>] [-AsByteStream] [-Stream <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="bfcca-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="bfcca-108">DESCRIPTION</span></span>

<span data-ttu-id="bfcca-109">`Get-Content`Cmdleten hämtar innehållet för objektet på den plats som anges av sökvägen, till exempel texten i en fil eller innehållet i en funktion.</span><span class="sxs-lookup"><span data-stu-id="bfcca-109">The `Get-Content` cmdlet gets the content of the item at the location specified by the path, such as the text in a file or the content of a function.</span></span> <span data-ttu-id="bfcca-110">För filer läser innehållet en rad i taget och returnerar en samling objekt som representerar en rad med innehåll.</span><span class="sxs-lookup"><span data-stu-id="bfcca-110">For files, the content is read one line at a time and returns a collection of objects, each of which represents a line of content.</span></span>

<span data-ttu-id="bfcca-111">Från och med PowerShell 3,0 `Get-Content` kan även ett angivet antal rader hämtas från början eller slutet av ett objekt.</span><span class="sxs-lookup"><span data-stu-id="bfcca-111">Beginning in PowerShell 3.0, `Get-Content` can also get a specified number of lines from the beginning or end of an item.</span></span>

## <span data-ttu-id="bfcca-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="bfcca-112">EXAMPLES</span></span>

### <span data-ttu-id="bfcca-113">Exempel 1: hämta innehållet i en textfil</span><span class="sxs-lookup"><span data-stu-id="bfcca-113">Example 1: Get the content of a text file</span></span>

<span data-ttu-id="bfcca-114">Det här exemplet hämtar innehållet i en fil i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="bfcca-114">This example gets the content of a file in the current directory.</span></span> <span data-ttu-id="bfcca-115">`LineNumbers.txt`Filen innehåller 100 rader i formatet, **Detta är rad X** och används i flera exempel.</span><span class="sxs-lookup"><span data-stu-id="bfcca-115">The `LineNumbers.txt` file contains 100 lines in the format, **This is Line X** and is used in several examples.</span></span>

```powershell
1..100 | ForEach-Object { Add-Content -Path .\LineNumbers.txt -Value "This is line $_." }
Get-Content -Path .\LineNumbers.txt
```

```Output
This is Line 1
This is Line 2
...
This is line 99.
This is line 100.
```

<span data-ttu-id="bfcca-116">Mat ris värdena 1-100 skickas ned pipelinen till `ForEach-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="bfcca-116">The array values 1-100 are sent down the pipeline to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="bfcca-117">`ForEach-Object` använder ett-skript block med `Add-Content` cmdleten för att skapa `LineNumbers.txt` filen.</span><span class="sxs-lookup"><span data-stu-id="bfcca-117">`ForEach-Object` uses a script block with the `Add-Content` cmdlet to create the `LineNumbers.txt` file.</span></span> <span data-ttu-id="bfcca-118">Variabeln `$_` representerar mat ris värden som varje objekt skickas nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="bfcca-118">The variable `$_` represents the array values as each object is sent down the pipeline.</span></span> <span data-ttu-id="bfcca-119">`Get-Content`Cmdleten använder parametern **Path** för att ange `LineNumbers.txt` filen och visar innehållet i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="bfcca-119">The `Get-Content` cmdlet uses the **Path** parameter to specify the `LineNumbers.txt` file and displays the content in the PowerShell console.</span></span>

### <span data-ttu-id="bfcca-120">Exempel 2: begränsa antalet rader Get-Content returnerar</span><span class="sxs-lookup"><span data-stu-id="bfcca-120">Example 2: Limit the number of lines Get-Content returns</span></span>

<span data-ttu-id="bfcca-121">Det här kommandot hämtar de fem första raderna i en fil.</span><span class="sxs-lookup"><span data-stu-id="bfcca-121">This command gets the first five lines of a file.</span></span> <span data-ttu-id="bfcca-122">Parametern **totalCount** används för att hämta de första fem innehålls raderna.</span><span class="sxs-lookup"><span data-stu-id="bfcca-122">The **TotalCount** parameter is used to gets the first five lines of content.</span></span> <span data-ttu-id="bfcca-123">I det här exemplet används `LineNumbers.txt` filen som skapades i exempel 1.</span><span class="sxs-lookup"><span data-stu-id="bfcca-123">This example uses the `LineNumbers.txt` file that was created in Example 1.</span></span>

```powershell
Get-Content -Path .\LineNumbers.txt -TotalCount 5
```

```Output
This is Line 1
This is Line 2
This is Line 3
This is Line 4
This is Line 5
```

### <span data-ttu-id="bfcca-124">Exempel 3: Hämta en bestämd innehålls rad från en textfil</span><span class="sxs-lookup"><span data-stu-id="bfcca-124">Example 3: Get a specific line of content from a text file</span></span>

<span data-ttu-id="bfcca-125">Det här kommandot hämtar ett särskilt antal rader från en fil och visar sedan bara den sista raden i innehållet.</span><span class="sxs-lookup"><span data-stu-id="bfcca-125">This command gets a specific number of lines from a file and then displays only the last line of that content.</span></span> <span data-ttu-id="bfcca-126">Parametern **totalCount** hämtar de första 25 innehålls raderna.</span><span class="sxs-lookup"><span data-stu-id="bfcca-126">The **TotalCount** parameter gets the first 25 lines of content.</span></span> <span data-ttu-id="bfcca-127">I det här exemplet används `LineNumbers.txt` filen som skapades i exempel 1.</span><span class="sxs-lookup"><span data-stu-id="bfcca-127">This example uses the `LineNumbers.txt` file that was created in Example 1.</span></span>

```powershell
(Get-Content -Path .\LineNumbers.txt -TotalCount 25)[-1]
```

```Output
This is Line 25
```

<span data-ttu-id="bfcca-128">`Get-Content`Kommandot omges av parenteser så att kommandot slutförs innan du fortsätter till nästa steg.</span><span class="sxs-lookup"><span data-stu-id="bfcca-128">The `Get-Content` command is wrapped in parentheses so that the command completes before going to the next step.</span></span> <span data-ttu-id="bfcca-129">`Get-Content`Returnerar en matris med rader. Detta gör att du kan lägga till index notation efter parentesen för att hämta ett angivet rad nummer.</span><span class="sxs-lookup"><span data-stu-id="bfcca-129">`Get-Content`returns an array of lines, this allows you to add the index notation after the parenthesis to retrieve a specific line number.</span></span> <span data-ttu-id="bfcca-130">I det här fallet `[-1]` anger indexet det sista indexet i den returnerade matrisen med 25 hämtade rader.</span><span class="sxs-lookup"><span data-stu-id="bfcca-130">In this case, the `[-1]` index specifies the last index in the returned array of 25 retrieved lines.</span></span>

### <span data-ttu-id="bfcca-131">Exempel 4: hämta den sista raden i en textfil</span><span class="sxs-lookup"><span data-stu-id="bfcca-131">Example 4: Get the last line of a text file</span></span>

<span data-ttu-id="bfcca-132">Det här kommandot hämtar den första raden och den sista raden i innehållet från en fil.</span><span class="sxs-lookup"><span data-stu-id="bfcca-132">This command gets the first line and last line of content from a file.</span></span> <span data-ttu-id="bfcca-133">I det här exemplet används `LineNumbers.txt` filen som skapades i exempel 1.</span><span class="sxs-lookup"><span data-stu-id="bfcca-133">This example uses the `LineNumbers.txt` file that was created in Example 1.</span></span>

```powershell
Get-Item -Path .\LineNumbers.txt | Get-Content -Tail 1
```

```Output
This is Line 100
```

<span data-ttu-id="bfcca-134">I det här exemplet används `Get-Item` cmdleten för att demonstrera att du kan skicka filer till- `Get-Content` parametern.</span><span class="sxs-lookup"><span data-stu-id="bfcca-134">This example uses the `Get-Item` cmdlet to demonstrate that you can pipe files into the `Get-Content` parameter.</span></span> <span data-ttu-id="bfcca-135">Parametern **pilslut** hämtar den sista raden i filen.</span><span class="sxs-lookup"><span data-stu-id="bfcca-135">The **Tail** parameter gets the last line of the file.</span></span> <span data-ttu-id="bfcca-136">Den här metoden är snabbare än att hämta alla rader och använda `[-1]` index notation.</span><span class="sxs-lookup"><span data-stu-id="bfcca-136">This method is faster than retrieving all of the lines and using the `[-1]` index notation.</span></span>

### <span data-ttu-id="bfcca-137">Exempel 5: hämta innehållet i en alternativ data ström</span><span class="sxs-lookup"><span data-stu-id="bfcca-137">Example 5: Get the content of an alternate data stream</span></span>

<span data-ttu-id="bfcca-138">Det här exemplet beskriver hur du använder **Stream** -parametern för att hämta innehållet i en alternativ data ström för filer som lagras på en Windows NTFS-volym.</span><span class="sxs-lookup"><span data-stu-id="bfcca-138">This example describes how to use the **Stream** parameter to get the content of an alternate data stream for files stored on a Windows NTFS volume.</span></span> <span data-ttu-id="bfcca-139">I det här exemplet `Set-Content` används cmdleten för att skapa exempel innehåll i en fil med namnet `Stream.txt` .</span><span class="sxs-lookup"><span data-stu-id="bfcca-139">In this example, the `Set-Content` cmdlet is used to create sample content in a file named `Stream.txt`.</span></span>

```powershell
Set-Content -Path .\Stream.txt -Value 'This is the content of the Stream.txt file'
# Specify a wildcard to the Stream parameter to display all streams of the recently created file.
Get-Item -Path .\Stream.txt -Stream *
```

```Output
PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\Test\Stream.txt::$DATA
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\Test
PSChildName   : Stream.txt::$DATA
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\Test\Stream.txt
Stream        : :$DATA
Length        : 44
```

```powershell
# Retrieve the content of the primary, or $DATA stream.    # Retrieve the content of the primary stream. Note the singlequotes to prevent variable substitution.
Get-Content -Path .\Stream.txt -Stream $DATA    Get-Content -Path .\Stream.txt -Stream ':$DATA'
```

```Output
This is the content of the Stream.txt file
```

```powershell
# Alternative way to get the same content.
Get-Content -Path .\Stream.txt -Stream ""
# The primary stream doesn't need to be specified to get the primary stream of the file.
# This gets the same data as the prior two examples.
Get-Content -Path .\Stream.txt
```

```Output
This is the content of the Stream.txt file
```

```powershell
# The primary stream doesn't need to be specified to get the primary stream of the file.
# This gets the same data as the prior two examples.
Get-Content -Path .\Stream.txt
```

```powershell
# Use the Stream parameter of Add-Content to create a new Stream containing sample content.
Add-Content -Path .\Stream.txt -Stream NewStream -Value 'Added a stream named NewStream to Stream.txt'
# Use Get-Item to verify the stream was created.
Get-Item -Path .\Stream.txt -Stream *
```

```Output
PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\Test\Stream.txt::$DATA
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\Test
PSChildName   : Stream.txt::$DATA
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\Test\Stream.txt
Stream        : :$DATA
Length        : 44

PSPath        : Microsoft.PowerShell.Core\FileSystem::C:\Test\Stream.txt:NewStream
PSParentPath  : Microsoft.PowerShell.Core\FileSystem::C:\Test
PSChildName   : Stream.txt:NewStream
PSDrive       : C
PSProvider    : Microsoft.PowerShell.Core\FileSystem
PSIsContainer : False
FileName      : C:\Test\Stream.txt
Stream        : NewStream
Length        : 46
```

```powershell
# Retrieve the content of your newly created Stream.
Get-Content -Path .\Stream.txt -Stream NewStream
```

```Output
Added a stream named NewStream to Stream.txt
```

<span data-ttu-id="bfcca-140">**Stream** -parametern är en dynamisk parameter för [fil Systems leverantören](../microsoft.powershell.core/about/about_filesystem_provider.md#stream-systemstring).</span><span class="sxs-lookup"><span data-stu-id="bfcca-140">The **Stream** parameter is a dynamic parameter of the [FileSystem provider](../microsoft.powershell.core/about/about_filesystem_provider.md#stream-systemstring).</span></span>
<span data-ttu-id="bfcca-141">Som standard `Get-Content` hämtar endast data från standardvärdet eller `:$DATA` Stream.</span><span class="sxs-lookup"><span data-stu-id="bfcca-141">By default `Get-Content` only retrieves data from the default, or `:$DATA` stream.</span></span> <span data-ttu-id="bfcca-142">**Strömmar** kan användas för att lagra dolda data, till exempel attribut, säkerhets inställningar eller andra data.</span><span class="sxs-lookup"><span data-stu-id="bfcca-142">**Streams** can be used to store hidden data such as attributes, security settings, or other data.</span></span> <span data-ttu-id="bfcca-143">De kan också lagras på kataloger utan att vara underordnade objekt.</span><span class="sxs-lookup"><span data-stu-id="bfcca-143">They can also be stored on directories without being child items.</span></span>

### <span data-ttu-id="bfcca-144">Exempel 6: Hämta RAW-innehåll</span><span class="sxs-lookup"><span data-stu-id="bfcca-144">Example 6: Get raw content</span></span>

<span data-ttu-id="bfcca-145">Kommandona i det här exemplet hämtar innehållet i en fil som en sträng, i stället för en sträng mat ris.</span><span class="sxs-lookup"><span data-stu-id="bfcca-145">The commands in this example get the contents of a file as one string, instead of an array of strings.</span></span> <span data-ttu-id="bfcca-146">Som standard, utan den **obearbetade** dynamiska parametern, returneras innehållet som en matris med rad matnings strängar.</span><span class="sxs-lookup"><span data-stu-id="bfcca-146">By default, without the **Raw** dynamic parameter, content is returned as an array of newline-delimited strings.</span></span> <span data-ttu-id="bfcca-147">I det här exemplet används `LineNumbers.txt` filen som skapades i exemplet</span><span class="sxs-lookup"><span data-stu-id="bfcca-147">This example uses the `LineNumbers.txt` file that was created in Example</span></span>
1.

```powershell
$raw = Get-Content -Path .\LineNumbers.txt -Raw
$lines = Get-Content -Path .\LineNumbers.txt
Write-Host "Raw contains $($raw.Count) lines."
Write-Host "Lines contains $($lines.Count) lines."
```

```Output
Raw contains 1 lines.
Lines contains 100 lines.
```

### <span data-ttu-id="bfcca-148">Exempel 7: använda filter med Get-Content</span><span class="sxs-lookup"><span data-stu-id="bfcca-148">Example 7: Use Filters with Get-Content</span></span>

<span data-ttu-id="bfcca-149">Du kan ange ett filter för `Get-Content` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="bfcca-149">You can specify a filter to the `Get-Content` cmdlet.</span></span> <span data-ttu-id="bfcca-150">När du använder filter för att kvalificera **Sök vägs** parametern måste du inkludera en efterföljande asterisk ( `*` ) för att ange innehållet i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="bfcca-150">When using filters to qualify the **Path** parameter, you need to include a trailing asterisk (`*`) to indicate the contents of the path.</span></span>

<span data-ttu-id="bfcca-151">Följande kommando hämtar innehållet för alla `*.log` filer i `C:\Temp` katalogen.</span><span class="sxs-lookup"><span data-stu-id="bfcca-151">The following command gets the content of all `*.log` files in the `C:\Temp` directory.</span></span>

```powershell
Get-Content -Path C:\Temp\* -Filter *.log
```

### <span data-ttu-id="bfcca-152">Exempel 8: Hämta fil innehåll som en byte mat ris</span><span class="sxs-lookup"><span data-stu-id="bfcca-152">Example 8: Get file contents as a byte array</span></span>

<span data-ttu-id="bfcca-153">Det här exemplet visar hur du hämtar innehållet i en fil som ett `[byte[]]` enda objekt.</span><span class="sxs-lookup"><span data-stu-id="bfcca-153">This example demonstrates how to get the contents of a file as a `[byte[]]` as a single object.</span></span>

```powershell
$byteArray = Get-Content -Path C:\temp\test.txt -AsByteStream -Raw
Get-Member -InputObject $bytearray
```

```Output
   TypeName: System.Byte[]

Name           MemberType            Definition
----           ----------            ----------
Count          AliasProperty         Count = Length
Add            Method                int IList.Add(System.Object value)
```

<span data-ttu-id="bfcca-154">Det första kommandot använder parametern **AsByteStream** för att hämta data strömmen av byte från filen.</span><span class="sxs-lookup"><span data-stu-id="bfcca-154">The first command uses the **AsByteStream** parameter to get the stream of bytes from the file.</span></span>
<span data-ttu-id="bfcca-155">Parametern **RAW** ser till att byte returneras som en `[System.Byte[]]` .</span><span class="sxs-lookup"><span data-stu-id="bfcca-155">The **Raw** parameter ensures that the bytes are returned as a `[System.Byte[]]`.</span></span> <span data-ttu-id="bfcca-156">Om den **råa** parametern saknas är returvärdet en data ström med byte, som tolkas av PowerShell som `[System.Object[]]` .</span><span class="sxs-lookup"><span data-stu-id="bfcca-156">If the **Raw** parameter was absent, the return value is a stream of bytes, which is interpreted by PowerShell as `[System.Object[]]`.</span></span>

## <span data-ttu-id="bfcca-157">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="bfcca-157">PARAMETERS</span></span>

### <span data-ttu-id="bfcca-158">-Path</span><span class="sxs-lookup"><span data-stu-id="bfcca-158">-Path</span></span>

<span data-ttu-id="bfcca-159">Anger sökvägen till ett objekt där `Get-Content` hämtar innehållet.</span><span class="sxs-lookup"><span data-stu-id="bfcca-159">Specifies the path to an item where `Get-Content` gets the content.</span></span> <span data-ttu-id="bfcca-160">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="bfcca-160">Wildcard characters are permitted.</span></span> <span data-ttu-id="bfcca-161">Sök vägarna måste vara sökvägar till objekt, inte behållare.</span><span class="sxs-lookup"><span data-stu-id="bfcca-161">The paths must be paths to items, not to containers.</span></span> <span data-ttu-id="bfcca-162">Du måste till exempel ange en sökväg till en eller flera filer, inte en sökväg till en katalog.</span><span class="sxs-lookup"><span data-stu-id="bfcca-162">For example, you must specify a path to one or more files, not a path to a directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="bfcca-163">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="bfcca-163">-LiteralPath</span></span>

<span data-ttu-id="bfcca-164">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="bfcca-164">Specifies a path to one or more locations.</span></span> <span data-ttu-id="bfcca-165">Värdet för **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="bfcca-165">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="bfcca-166">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="bfcca-166">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="bfcca-167">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="bfcca-167">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="bfcca-168">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="bfcca-168">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="bfcca-169">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="bfcca-169">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bfcca-170">-ReadCount</span><span class="sxs-lookup"><span data-stu-id="bfcca-170">-ReadCount</span></span>

<span data-ttu-id="bfcca-171">Anger hur många rader med innehåll som skickas via pipelinen i taget.</span><span class="sxs-lookup"><span data-stu-id="bfcca-171">Specifies how many lines of content are sent through the pipeline at a time.</span></span> <span data-ttu-id="bfcca-172">Standardvärdet är 1.</span><span class="sxs-lookup"><span data-stu-id="bfcca-172">The default value is 1.</span></span>
<span data-ttu-id="bfcca-173">Värdet 0 (noll) skickar allt innehåll på en och samma tidpunkt.</span><span class="sxs-lookup"><span data-stu-id="bfcca-173">A value of 0 (zero) sends all of the content at one time.</span></span>

<span data-ttu-id="bfcca-174">Den här parametern ändrar inte det innehåll som visas, men det påverkar hur lång tid det tar att visa innehållet.</span><span class="sxs-lookup"><span data-stu-id="bfcca-174">This parameter does not change the content displayed, but it does affect the time it takes to display the content.</span></span> <span data-ttu-id="bfcca-175">När värdet för **ReadCount** ökar, kommer tiden det tar att returnera den första raden att öka, men den totala tiden för åtgärden minskar.</span><span class="sxs-lookup"><span data-stu-id="bfcca-175">As the value of **ReadCount** increases, the time it takes to return the first line increases, but the total time for the operation decreases.</span></span> <span data-ttu-id="bfcca-176">Detta kan göra en märkbar skillnad i stora objekt.</span><span class="sxs-lookup"><span data-stu-id="bfcca-176">This can make a perceptible difference in large items.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 1
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bfcca-177">– TotalCount</span><span class="sxs-lookup"><span data-stu-id="bfcca-177">-TotalCount</span></span>

<span data-ttu-id="bfcca-178">Anger antalet rader från början av en fil eller ett annat objekt.</span><span class="sxs-lookup"><span data-stu-id="bfcca-178">Specifies the number of lines from the beginning of a file or other item.</span></span> <span data-ttu-id="bfcca-179">Standardvärdet är-1 (alla rader).</span><span class="sxs-lookup"><span data-stu-id="bfcca-179">The default is -1 (all lines).</span></span>

<span data-ttu-id="bfcca-180">Du kan använda **totalCount** -parameterns namn eller dess alias, **först** eller **Head**.</span><span class="sxs-lookup"><span data-stu-id="bfcca-180">You can use the **TotalCount** parameter name or its aliases, **First** or **Head**.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases: First, Head

Required: False
Position: Named
Default value: -1
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bfcca-181">-Pilslut</span><span class="sxs-lookup"><span data-stu-id="bfcca-181">-Tail</span></span>

<span data-ttu-id="bfcca-182">Anger antalet rader från slutet av en fil eller ett annat objekt.</span><span class="sxs-lookup"><span data-stu-id="bfcca-182">Specifies the number of lines from the end of a file or other item.</span></span> <span data-ttu-id="bfcca-183">Du kan använda **slutet** av parameter namnet eller dess alias, **sist**.</span><span class="sxs-lookup"><span data-stu-id="bfcca-183">You can use the **Tail** parameter name or its alias, **Last**.</span></span> <span data-ttu-id="bfcca-184">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bfcca-184">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: Last

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bfcca-185">-Filter</span><span class="sxs-lookup"><span data-stu-id="bfcca-185">-Filter</span></span>

<span data-ttu-id="bfcca-186">Anger ett filter för att kvalificera **Sök vägs** parametern.</span><span class="sxs-lookup"><span data-stu-id="bfcca-186">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="bfcca-187">[Fil Systems](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) leverantören är den enda installerade PowerShell-providern som stöder användningen av filter.</span><span class="sxs-lookup"><span data-stu-id="bfcca-187">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="bfcca-188">Du kan hitta syntaxen för filter språket för **fil systemet** i [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="bfcca-188">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="bfcca-189">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="bfcca-189">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="bfcca-190">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="bfcca-190">-Include</span></span>

<span data-ttu-id="bfcca-191">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="bfcca-191">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="bfcca-192">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="bfcca-192">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="bfcca-193">Ange ett Sök vägs element eller ett mönster, till exempel `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="bfcca-193">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="bfcca-194">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="bfcca-194">Wildcard characters are permitted.</span></span> <span data-ttu-id="bfcca-195">Parametern **include** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="bfcca-195">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="bfcca-196">-Undanta</span><span class="sxs-lookup"><span data-stu-id="bfcca-196">-Exclude</span></span>

<span data-ttu-id="bfcca-197">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="bfcca-197">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span>
<span data-ttu-id="bfcca-198">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="bfcca-198">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="bfcca-199">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="bfcca-199">Enter a path element or pattern, such as `*.txt`.</span></span>
<span data-ttu-id="bfcca-200">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="bfcca-200">Wildcard characters are permitted.</span></span>

<span data-ttu-id="bfcca-201">Parametern **exclude** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="bfcca-201">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="bfcca-202">-Force</span><span class="sxs-lookup"><span data-stu-id="bfcca-202">-Force</span></span>

<span data-ttu-id="bfcca-203">**Force** åsidosätter ett skrivskyddat attribut eller skapar kataloger för att slutföra en fil Sök väg.</span><span class="sxs-lookup"><span data-stu-id="bfcca-203">**Force** will override a read-only attribute or create directories to complete a file path.</span></span> <span data-ttu-id="bfcca-204">**Force** -parametern försöker inte ändra fil behörigheter eller Åsidosätt säkerhets begränsningar.</span><span class="sxs-lookup"><span data-stu-id="bfcca-204">The **Force** parameter does not attempt to change file permissions or override security restrictions.</span></span>

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

### <span data-ttu-id="bfcca-205">-Credential</span><span class="sxs-lookup"><span data-stu-id="bfcca-205">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="bfcca-206">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bfcca-206">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="bfcca-207">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="bfcca-207">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bfcca-208">-Avgränsare</span><span class="sxs-lookup"><span data-stu-id="bfcca-208">-Delimiter</span></span>

<span data-ttu-id="bfcca-209">Anger den avgränsare som `Get-Content` används för att dela upp filen i objekt när den läses.</span><span class="sxs-lookup"><span data-stu-id="bfcca-209">Specifies the delimiter that `Get-Content` uses to divide the file into objects while it reads.</span></span> <span data-ttu-id="bfcca-210">Standardvärdet är `\n` rad slutet.</span><span class="sxs-lookup"><span data-stu-id="bfcca-210">The default is `\n`, the end-of-line character.</span></span> <span data-ttu-id="bfcca-211">När du läser en textfil `Get-Content` returnerar en samling sträng objekt, som var och en slutar med ett rad sluts tecken.</span><span class="sxs-lookup"><span data-stu-id="bfcca-211">When reading a text file, `Get-Content` returns a collection of string objects, each of which ends with an end-of-line character.</span></span> <span data-ttu-id="bfcca-212">När du anger en avgränsare som inte finns i filen `Get-Content` returneras hela filen som ett enkelt, icke-avgränsat objekt.</span><span class="sxs-lookup"><span data-stu-id="bfcca-212">When you enter a delimiter that does not exist in the file, `Get-Content` returns the entire file as a single, undelimited object.</span></span>

<span data-ttu-id="bfcca-213">Du kan använda den här parametern för att dela upp en stor fil i mindre filer genom att ange en fil avgränsare, som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="bfcca-213">You can use this parameter to split a large file into smaller files by specifying a file separator, as the delimiter.</span></span> <span data-ttu-id="bfcca-214">Avgränsaren bevaras (tas inte bort) och blir det sista objektet i varje fil avsnitt.</span><span class="sxs-lookup"><span data-stu-id="bfcca-214">The delimiter is preserved (not discarded) and becomes the last item in each file section.</span></span>

<span data-ttu-id="bfcca-215">**Avgränsaren** är en dynamisk parameter som **fil Systems** leverantören lägger till i `Get-Content` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="bfcca-215">**Delimiter** is a dynamic parameter that the **FileSystem** provider adds to the `Get-Content` cmdlet.</span></span> <span data-ttu-id="bfcca-216">Den här parametern fungerar bara i fil system enheter.</span><span class="sxs-lookup"><span data-stu-id="bfcca-216">This parameter works only in file system drives.</span></span>

> [!NOTE]
> <span data-ttu-id="bfcca-217">När värdet för **avgränsare** -parametern är en tom sträng `Get-Content` returnerar inte något.</span><span class="sxs-lookup"><span data-stu-id="bfcca-217">Currently, when the value of the **Delimiter** parameter is an empty string, `Get-Content` does not return anything.</span></span> <span data-ttu-id="bfcca-218">Detta är ett känt problem.</span><span class="sxs-lookup"><span data-stu-id="bfcca-218">This is a known issue.</span></span> <span data-ttu-id="bfcca-219">För att tvinga fram `Get-Content` att returnera hela filen som en enda, unavgränsad sträng.</span><span class="sxs-lookup"><span data-stu-id="bfcca-219">To force `Get-Content` to return the entire file as a single, undelimited string.</span></span> <span data-ttu-id="bfcca-220">Ange ett värde som inte finns i filen.</span><span class="sxs-lookup"><span data-stu-id="bfcca-220">Enter a value that does not exist in the file.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: End-of-line character
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bfcca-221">– Vänta</span><span class="sxs-lookup"><span data-stu-id="bfcca-221">-Wait</span></span>

<span data-ttu-id="bfcca-222">Ser till att filen är öppen när alla befintliga rader har skrivits ut.</span><span class="sxs-lookup"><span data-stu-id="bfcca-222">Keeps the file open after all existing lines have been output.</span></span> <span data-ttu-id="bfcca-223">Vid väntan, `Get-Content` kontrollerar filen en gång i sekunden och utvärderar nya rader om den är tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="bfcca-223">While waiting, `Get-Content` checks the file once each second and outputs new lines if present.</span></span> <span data-ttu-id="bfcca-224">Du kan avbryta **väntan** genom att trycka på **CTRL + C**.</span><span class="sxs-lookup"><span data-stu-id="bfcca-224">You can interrupt **Wait** by pressing **CTRL+C**.</span></span> <span data-ttu-id="bfcca-225">Väntan avslutas också om filen tas bort, i vilket fall ett icke-avslutande fel rapporteras.</span><span class="sxs-lookup"><span data-stu-id="bfcca-225">Waiting also ends if the file gets deleted, in which case a non-terminating error is reported.</span></span>

<span data-ttu-id="bfcca-226">**Wait** är en dynamisk parameter som fil system leverantören lägger till i `Get-Content` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="bfcca-226">**Wait** is a dynamic parameter that the FileSystem provider adds to the `Get-Content` cmdlet.</span></span> <span data-ttu-id="bfcca-227">Den här parametern fungerar bara i fil system enheter.</span><span class="sxs-lookup"><span data-stu-id="bfcca-227">This parameter works only in file system drives.</span></span> <span data-ttu-id="bfcca-228">**Väntan** kan inte kombineras med **RAW**.</span><span class="sxs-lookup"><span data-stu-id="bfcca-228">**Wait** cannot be combined with **Raw**.</span></span>

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

### <span data-ttu-id="bfcca-229">– RAW</span><span class="sxs-lookup"><span data-stu-id="bfcca-229">-Raw</span></span>

<span data-ttu-id="bfcca-230">Ignorerar rad matnings tecken och returnerar hela innehållet i en fil i en sträng med newlines bevarad.</span><span class="sxs-lookup"><span data-stu-id="bfcca-230">Ignores newline characters and returns the entire contents of a file in one string with the newlines preserved.</span></span> <span data-ttu-id="bfcca-231">Som standard används rad matnings tecken i en fil som avgränsare för att separera indata till en sträng mat ris.</span><span class="sxs-lookup"><span data-stu-id="bfcca-231">By default, newline characters in a file are used as delimiters to separate the input into an array of strings.</span></span> <span data-ttu-id="bfcca-232">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bfcca-232">This parameter was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="bfcca-233">**RAW** är en dynamisk parameter som **fil** Systems leverantören lägger till i `Get-Content` cmdleten den här parametern fungerar endast i fil system enheter.</span><span class="sxs-lookup"><span data-stu-id="bfcca-233">**Raw** is a dynamic parameter that the **FileSystem** provider adds to the `Get-Content` cmdlet This parameter works only in file system drives.</span></span>

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

### <span data-ttu-id="bfcca-234">-Encoding</span><span class="sxs-lookup"><span data-stu-id="bfcca-234">-Encoding</span></span>

<span data-ttu-id="bfcca-235">Anger typ av kodning för mål filen.</span><span class="sxs-lookup"><span data-stu-id="bfcca-235">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="bfcca-236">Standardvärdet är `utf8NoBOM`.</span><span class="sxs-lookup"><span data-stu-id="bfcca-236">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="bfcca-237">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="bfcca-237">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="bfcca-238">`ascii`: Använder kodningen för ASCII-teckenuppsättningen (7 bitar).</span><span class="sxs-lookup"><span data-stu-id="bfcca-238">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="bfcca-239">`bigendianunicode`: Kodar i UTF-16-format med big-endian byte-ordning.</span><span class="sxs-lookup"><span data-stu-id="bfcca-239">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="bfcca-240">`bigendianutf32`: Kodar i UTF-32-format med big-endian-dataordningen.</span><span class="sxs-lookup"><span data-stu-id="bfcca-240">`bigendianutf32`: Encodes in UTF-32 format using the big-endian byte order.</span></span>
- <span data-ttu-id="bfcca-241">`oem`: Använder standard kodning för MS-DOS-och-konsol program.</span><span class="sxs-lookup"><span data-stu-id="bfcca-241">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="bfcca-242">`unicode`: Kodar i UTF-16-format med lite-endian-dataordning.</span><span class="sxs-lookup"><span data-stu-id="bfcca-242">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="bfcca-243">`utf7`: Kodar i UTF-7-format.</span><span class="sxs-lookup"><span data-stu-id="bfcca-243">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="bfcca-244">`utf8`: Kodar i UTF-8-format.</span><span class="sxs-lookup"><span data-stu-id="bfcca-244">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="bfcca-245">`utf8BOM`: Kodar i UTF-8-format med byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="bfcca-245">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="bfcca-246">`utf8NoBOM`: Kodar i UTF-8-format utan byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="bfcca-246">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="bfcca-247">`utf32`: Kodar i UTF-32-format.</span><span class="sxs-lookup"><span data-stu-id="bfcca-247">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="bfcca-248">Encoding är en dynamisk parameter som **fil Systems** leverantören lägger till i `Get-Content` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="bfcca-248">Encoding is a dynamic parameter that the **FileSystem** provider adds to the `Get-Content` cmdlet.</span></span>
<span data-ttu-id="bfcca-249">Den här parametern är endast tillgänglig i fil system enheter.</span><span class="sxs-lookup"><span data-stu-id="bfcca-249">This parameter is available only in file system drives.</span></span>

<span data-ttu-id="bfcca-250">När du läser från och skriver till binära filer använder du parametern **AsByteStream** och värdet 0 för parametern **ReadCount** .</span><span class="sxs-lookup"><span data-stu-id="bfcca-250">When reading from and writing to binary files, use the **AsByteStream** parameter and a value of 0 for the **ReadCount** parameter.</span></span> <span data-ttu-id="bfcca-251">Ett **ReadCount** -värde på 0 läser hela filen i en enda Läs åtgärd.</span><span class="sxs-lookup"><span data-stu-id="bfcca-251">A **ReadCount** value of 0 reads the entire file in a single read operation.</span></span> <span data-ttu-id="bfcca-252">Standardvärdet för **ReadCount** , 1, läser en byte i varje Läs åtgärd och konverterar varje byte till ett separat objekt, vilket orsakar fel när du använder `Set-Content` cmdleten för att skriva byte till en fil om du inte använder parametern **AsByteStream** .</span><span class="sxs-lookup"><span data-stu-id="bfcca-252">The default **ReadCount** value, 1, reads one byte in each read operation and converts each byte into a separate object, which causes errors when you use the `Set-Content` cmdlet to write the bytes to a file unless you use **AsByteStream** parameter.</span></span>

<span data-ttu-id="bfcca-253">Från och med PowerShell 6,2 tillåter **encoding** -parametern även numeriska ID: n för registrerade tecken tabeller (som `-Encoding 1251` ) eller sträng namn för registrerade tecken tabeller (som `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="bfcca-253">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="bfcca-254">Mer information finns i .NET-dokumentationen för [encoding. codepage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span><span class="sxs-lookup"><span data-stu-id="bfcca-254">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

> [!NOTE]
> <span data-ttu-id="bfcca-255">**UTF-7** _ rekommenderas inte längre att använda.</span><span class="sxs-lookup"><span data-stu-id="bfcca-255">**UTF-7** _ is no longer recommended to use.</span></span> <span data-ttu-id="bfcca-256">I PowerShell 7,1 skrivs en varning om du anger `utf7` för parametern _ \*encoding\*\*.</span><span class="sxs-lookup"><span data-stu-id="bfcca-256">In PowerShell 7.1, a warning is written if you specify `utf7` for the _ *Encoding*\* parameter.</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bfcca-257">-Stream</span><span class="sxs-lookup"><span data-stu-id="bfcca-257">-Stream</span></span>

> [!NOTE]
> <span data-ttu-id="bfcca-258">Den här parametern är endast tillgänglig i Windows.</span><span class="sxs-lookup"><span data-stu-id="bfcca-258">This Parameter is only available on Windows.</span></span>

<span data-ttu-id="bfcca-259">Hämtar innehållet i den angivna alternativa NTFS-filströmen från filen.</span><span class="sxs-lookup"><span data-stu-id="bfcca-259">Gets the contents of the specified alternate NTFS file stream from the file.</span></span> <span data-ttu-id="bfcca-260">Ange data ström namnet.</span><span class="sxs-lookup"><span data-stu-id="bfcca-260">Enter the stream name.</span></span>
<span data-ttu-id="bfcca-261">Jokertecken stöds inte.</span><span class="sxs-lookup"><span data-stu-id="bfcca-261">Wildcards are not supported.</span></span>

<span data-ttu-id="bfcca-262">**Stream** är en dynamisk parameter som **fil Systems** leverantören lägger till i `Get-Content` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="bfcca-262">**Stream** is a dynamic parameter that the **FileSystem** provider adds to the `Get-Content` cmdlet.</span></span>
<span data-ttu-id="bfcca-263">Den här parametern fungerar bara i fil system enheter på Windows-system.</span><span class="sxs-lookup"><span data-stu-id="bfcca-263">This parameter works only in file system drives on Windows systems.</span></span>

<span data-ttu-id="bfcca-264">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bfcca-264">This parameter was introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="bfcca-265">I PowerShell 7,2 kan Get-Content hämta innehållet i alternativa data strömmar från kataloger och filer.</span><span class="sxs-lookup"><span data-stu-id="bfcca-265">In PowerShell 7.2, Get-Content can retrieve the content of alternative data streams from directories as well as files.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bfcca-266">-AsByteStream</span><span class="sxs-lookup"><span data-stu-id="bfcca-266">-AsByteStream</span></span>

<span data-ttu-id="bfcca-267">Anger att innehållet ska läsas som en data ström med byte.</span><span class="sxs-lookup"><span data-stu-id="bfcca-267">Specifies that the content should be read as a stream of bytes.</span></span> <span data-ttu-id="bfcca-268">**AsByteStream** -parametern introducerades i Windows PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="bfcca-268">The **AsByteStream** parameter was introduced in Windows PowerShell 6.0.</span></span>

<span data-ttu-id="bfcca-269">En varning inträffar när du använder parametern **AsByteStream** med parametern **encoding** .</span><span class="sxs-lookup"><span data-stu-id="bfcca-269">A warning occurs when you use the **AsByteStream** parameter with the **Encoding** parameter.</span></span> <span data-ttu-id="bfcca-270">Parametern **AsByteStream** ignorerar all kodning och utdata returneras som en data ström med byte.</span><span class="sxs-lookup"><span data-stu-id="bfcca-270">The **AsByteStream** parameter ignores any encoding and the output is returned as a stream of bytes.</span></span>

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

### <span data-ttu-id="bfcca-271">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bfcca-271">CommonParameters</span></span>

<span data-ttu-id="bfcca-272">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bfcca-272">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bfcca-273">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="bfcca-273">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bfcca-274">INDATA</span><span class="sxs-lookup"><span data-stu-id="bfcca-274">INPUTS</span></span>

### <span data-ttu-id="bfcca-275">System. Int64, system. string [], system. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="bfcca-275">System.Int64, System.String[], System.Management.Automation.PSCredential</span></span>

<span data-ttu-id="bfcca-276">Du kan skicka vidare antalet läsningar, totalt antal, sökvägar eller autentiseringsuppgifter till `Get-Content` .</span><span class="sxs-lookup"><span data-stu-id="bfcca-276">You can pipe the read count, total count, paths, or credentials to `Get-Content`.</span></span>

## <span data-ttu-id="bfcca-277">UTDATA</span><span class="sxs-lookup"><span data-stu-id="bfcca-277">OUTPUTS</span></span>

### <span data-ttu-id="bfcca-278">System. byte, system. String</span><span class="sxs-lookup"><span data-stu-id="bfcca-278">System.Byte, System.String</span></span>

<span data-ttu-id="bfcca-279">`Get-Content` Returnerar strängar eller byte.</span><span class="sxs-lookup"><span data-stu-id="bfcca-279">`Get-Content` returns strings or bytes.</span></span> <span data-ttu-id="bfcca-280">Utdatatypen beror på vilken typ av innehåll som du anger som indata.</span><span class="sxs-lookup"><span data-stu-id="bfcca-280">The output type depends upon the type of content that you specify as input.</span></span>

## <span data-ttu-id="bfcca-281">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="bfcca-281">NOTES</span></span>

<span data-ttu-id="bfcca-282">`Get-Content`Cmdleten är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="bfcca-282">The `Get-Content` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="bfcca-283">Använd cmdleten för att hämta providers i sessionen `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="bfcca-283">To get the providers in your session, use the `Get-PSProvider` cmdlet.</span></span> <span data-ttu-id="bfcca-284">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="bfcca-284">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="bfcca-285">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="bfcca-285">RELATED LINKS</span></span>

[<span data-ttu-id="bfcca-286">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="bfcca-286">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="bfcca-287">about_Providers</span><span class="sxs-lookup"><span data-stu-id="bfcca-287">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="bfcca-288">Lägg till innehåll</span><span class="sxs-lookup"><span data-stu-id="bfcca-288">Add-Content</span></span>](Add-Content.md)

[<span data-ttu-id="bfcca-289">Rensa innehåll</span><span class="sxs-lookup"><span data-stu-id="bfcca-289">Clear-Content</span></span>](Clear-Content.md)

[<span data-ttu-id="bfcca-290">-Objekt</span><span class="sxs-lookup"><span data-stu-id="bfcca-290">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="bfcca-291">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="bfcca-291">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="bfcca-292">Ange innehåll</span><span class="sxs-lookup"><span data-stu-id="bfcca-292">Set-Content</span></span>](Set-Content.md)
