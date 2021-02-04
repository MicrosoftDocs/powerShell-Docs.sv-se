---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-content?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Content
ms.openlocfilehash: b6a8d0f68717849711a794c9482e03d4ea081e1d
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/19/2020
ms.locfileid: "97692646"
---
# <span data-ttu-id="d4ac7-102">Get-Content</span><span class="sxs-lookup"><span data-stu-id="d4ac7-102">Get-Content</span></span>

## <span data-ttu-id="d4ac7-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="d4ac7-103">SYNOPSIS</span></span>
<span data-ttu-id="d4ac7-104">Hämtar innehållet i objektet på den angivna platsen.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-104">Gets the content of the item at the specified location.</span></span>

## <span data-ttu-id="d4ac7-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d4ac7-105">SYNTAX</span></span>

### <span data-ttu-id="d4ac7-106">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="d4ac7-106">Path (Default)</span></span>

```
Get-Content [-ReadCount <Int64>] [-TotalCount <Int64>] [-Tail <Int32>] [-Path] <String[]>
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Credential <PSCredential>]
 [-Delimiter <String>] [-Wait] [-Raw] [-Encoding <Encoding>] [-AsByteStream] [-Stream <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="d4ac7-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="d4ac7-107">LiteralPath</span></span>

```
Get-Content [-ReadCount <Int64>] [-TotalCount <Int64>] [-Tail <Int32>] -LiteralPath <String[]>
 [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force] [-Credential <PSCredential>]
 [-Delimiter <String>] [-Wait] [-Raw] [-Encoding <Encoding>] [-AsByteStream] [-Stream <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="d4ac7-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="d4ac7-108">DESCRIPTION</span></span>

<span data-ttu-id="d4ac7-109">`Get-Content`Cmdleten hämtar innehållet för objektet på den plats som anges av sökvägen, till exempel texten i en fil eller innehållet i en funktion.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-109">The `Get-Content` cmdlet gets the content of the item at the location specified by the path, such as the text in a file or the content of a function.</span></span> <span data-ttu-id="d4ac7-110">För filer läser innehållet en rad i taget och returnerar en samling objekt som representerar en rad med innehåll.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-110">For files, the content is read one line at a time and returns a collection of objects, each of which represents a line of content.</span></span>

<span data-ttu-id="d4ac7-111">Från och med PowerShell 3,0 `Get-Content` kan även ett angivet antal rader hämtas från början eller slutet av ett objekt.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-111">Beginning in PowerShell 3.0, `Get-Content` can also get a specified number of lines from the beginning or end of an item.</span></span>

## <span data-ttu-id="d4ac7-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="d4ac7-112">EXAMPLES</span></span>

### <span data-ttu-id="d4ac7-113">Exempel 1: hämta innehållet i en textfil</span><span class="sxs-lookup"><span data-stu-id="d4ac7-113">Example 1: Get the content of a text file</span></span>

<span data-ttu-id="d4ac7-114">Det här exemplet hämtar innehållet i en fil i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-114">This example gets the content of a file in the current directory.</span></span> <span data-ttu-id="d4ac7-115">`LineNumbers.txt`Filen innehåller 100 rader i formatet, **Detta är rad X** och används i flera exempel.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-115">The `LineNumbers.txt` file contains 100 lines in the format, **This is Line X** and is used in several examples.</span></span>

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

<span data-ttu-id="d4ac7-116">Mat ris värdena 1-100 skickas ned pipelinen till `ForEach-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-116">The array values 1-100 are sent down the pipeline to the `ForEach-Object` cmdlet.</span></span> <span data-ttu-id="d4ac7-117">`ForEach-Object` använder ett-skript block med `Add-Content` cmdleten för att skapa `LineNumbers.txt` filen.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-117">`ForEach-Object` uses a script block with the `Add-Content` cmdlet to create the `LineNumbers.txt` file.</span></span> <span data-ttu-id="d4ac7-118">Variabeln `$_` representerar mat ris värden som varje objekt skickas nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-118">The variable `$_` represents the array values as each object is sent down the pipeline.</span></span> <span data-ttu-id="d4ac7-119">`Get-Content`Cmdleten använder parametern **Path** för att ange `LineNumbers.txt` filen och visar innehållet i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-119">The `Get-Content` cmdlet uses the **Path** parameter to specify the `LineNumbers.txt` file and displays the content in the PowerShell console.</span></span>

### <span data-ttu-id="d4ac7-120">Exempel 2: begränsa antalet rader Get-Content returnerar</span><span class="sxs-lookup"><span data-stu-id="d4ac7-120">Example 2: Limit the number of lines Get-Content returns</span></span>

<span data-ttu-id="d4ac7-121">Det här kommandot hämtar de fem första raderna i en fil.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-121">This command gets the first five lines of a file.</span></span> <span data-ttu-id="d4ac7-122">Parametern **totalCount** används för att hämta de första fem innehålls raderna.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-122">The **TotalCount** parameter is used to gets the first five lines of content.</span></span> <span data-ttu-id="d4ac7-123">I det här exemplet används `LineNumbers.txt` filen som skapades i exempel 1.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-123">This example uses the `LineNumbers.txt` file that was created in Example 1.</span></span>

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

### <span data-ttu-id="d4ac7-124">Exempel 3: Hämta en bestämd innehålls rad från en textfil</span><span class="sxs-lookup"><span data-stu-id="d4ac7-124">Example 3: Get a specific line of content from a text file</span></span>

<span data-ttu-id="d4ac7-125">Det här kommandot hämtar ett särskilt antal rader från en fil och visar sedan bara den sista raden i innehållet.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-125">This command gets a specific number of lines from a file and then displays only the last line of that content.</span></span> <span data-ttu-id="d4ac7-126">Parametern **totalCount** hämtar de första 25 innehålls raderna.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-126">The **TotalCount** parameter gets the first 25 lines of content.</span></span> <span data-ttu-id="d4ac7-127">I det här exemplet används `LineNumbers.txt` filen som skapades i exempel 1.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-127">This example uses the `LineNumbers.txt` file that was created in Example 1.</span></span>

```powershell
(Get-Content -Path .\LineNumbers.txt -TotalCount 25)[-1]
```

```Output
This is Line 25
```

<span data-ttu-id="d4ac7-128">`Get-Content`Kommandot omges av parenteser så att kommandot slutförs innan du fortsätter till nästa steg.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-128">The `Get-Content` command is wrapped in parentheses so that the command completes before going to the next step.</span></span> <span data-ttu-id="d4ac7-129">`Get-Content`Returnerar en matris med rader. Detta gör att du kan lägga till index notation efter parentesen för att hämta ett angivet rad nummer.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-129">`Get-Content`returns an array of lines, this allows you to add the index notation after the parenthesis to retrieve a specific line number.</span></span> <span data-ttu-id="d4ac7-130">I det här fallet `[-1]` anger indexet det sista indexet i den returnerade matrisen med 25 hämtade rader.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-130">In this case, the `[-1]` index specifies the last index in the returned array of 25 retrieved lines.</span></span>

### <span data-ttu-id="d4ac7-131">Exempel 4: hämta den sista raden i en textfil</span><span class="sxs-lookup"><span data-stu-id="d4ac7-131">Example 4: Get the last line of a text file</span></span>

<span data-ttu-id="d4ac7-132">Det här kommandot hämtar den första raden och den sista raden i innehållet från en fil.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-132">This command gets the first line and last line of content from a file.</span></span> <span data-ttu-id="d4ac7-133">I det här exemplet används `LineNumbers.txt` filen som skapades i exempel 1.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-133">This example uses the `LineNumbers.txt` file that was created in Example 1.</span></span>

```powershell
Get-Item -Path .\LineNumbers.txt | Get-Content -Tail 1
```

```Output
This is Line 100
```

<span data-ttu-id="d4ac7-134">I det här exemplet används `Get-Item` cmdleten för att demonstrera att du kan skicka filer till- `Get-Content` parametern.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-134">This example uses the `Get-Item` cmdlet to demonstrate that you can pipe files into the `Get-Content` parameter.</span></span> <span data-ttu-id="d4ac7-135">Parametern **pilslut** hämtar den sista raden i filen.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-135">The **Tail** parameter gets the last line of the file.</span></span> <span data-ttu-id="d4ac7-136">Den här metoden är snabbare än att hämta alla rader och använda `[-1]` index notation.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-136">This method is faster than retrieving all of the lines and using the `[-1]` index notation.</span></span>

### <span data-ttu-id="d4ac7-137">Exempel 5: hämta innehållet i en alternativ data ström</span><span class="sxs-lookup"><span data-stu-id="d4ac7-137">Example 5: Get the content of an alternate data stream</span></span>

<span data-ttu-id="d4ac7-138">Det här exemplet beskriver hur du använder **Stream** -parametern för att hämta innehållet i en alternativ data ström för filer som lagras på en Windows NTFS-volym.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-138">This example describes how to use the **Stream** parameter to get the content of an alternate data stream for files stored on a Windows NTFS volume.</span></span> <span data-ttu-id="d4ac7-139">I det här exemplet `Set-Content` används cmdleten för att skapa exempel innehåll i en fil med namnet `Stream.txt` .</span><span class="sxs-lookup"><span data-stu-id="d4ac7-139">In this example, the `Set-Content` cmdlet is used to create sample content in a file named `Stream.txt`.</span></span>

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
# Retrieve the content of the primary, or $DATA stream.
Get-Content -Path .\Stream.txt -Stream $DATA
```

```Output
This is the content of the Stream.txt file
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

<span data-ttu-id="d4ac7-140">**Stream** -parametern är en dynamisk parameter för [fil Systems leverantören](../microsoft.powershell.core/about/about_filesystem_provider.md#stream-systemstring).</span><span class="sxs-lookup"><span data-stu-id="d4ac7-140">The **Stream** parameter is a dynamic parameter of the [FileSystem provider](../microsoft.powershell.core/about/about_filesystem_provider.md#stream-systemstring).</span></span>
<span data-ttu-id="d4ac7-141">Som standard `Get-Content` hämtar endast data från standardvärdet eller `:$DATA` Stream.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-141">By default `Get-Content` only retrieves data from the default, or `:$DATA` stream.</span></span> <span data-ttu-id="d4ac7-142">**Strömmar** kan användas för att lagra dolda data, till exempel attribut, säkerhets inställningar eller andra data.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-142">**Streams** can be used to store hidden data such as attributes, security settings, or other data.</span></span> <span data-ttu-id="d4ac7-143">De kan också lagras på kataloger utan att vara underordnade objekt.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-143">They can also be stored on directories without being child items.</span></span>

### <span data-ttu-id="d4ac7-144">Exempel 6: Hämta RAW-innehåll</span><span class="sxs-lookup"><span data-stu-id="d4ac7-144">Example 6: Get raw content</span></span>

<span data-ttu-id="d4ac7-145">Kommandona i det här exemplet hämtar innehållet i en fil som en sträng, i stället för en sträng mat ris.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-145">The commands in this example get the contents of a file as one string, instead of an array of strings.</span></span> <span data-ttu-id="d4ac7-146">Som standard, utan den **obearbetade** dynamiska parametern, returneras innehållet som en matris med rad matnings strängar.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-146">By default, without the **Raw** dynamic parameter, content is returned as an array of newline-delimited strings.</span></span> <span data-ttu-id="d4ac7-147">I det här exemplet används `LineNumbers.txt` filen som skapades i exemplet</span><span class="sxs-lookup"><span data-stu-id="d4ac7-147">This example uses the `LineNumbers.txt` file that was created in Example</span></span>
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

### <span data-ttu-id="d4ac7-148">Exempel 7: använda filter med Get-Content</span><span class="sxs-lookup"><span data-stu-id="d4ac7-148">Example 7: Use Filters with Get-Content</span></span>

<span data-ttu-id="d4ac7-149">Du kan ange ett filter för `Get-Content` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-149">You can specify a filter to the `Get-Content` cmdlet.</span></span> <span data-ttu-id="d4ac7-150">När du använder filter för att kvalificera **Sök vägs** parametern måste du inkludera en efterföljande asterisk ( `*` ) för att ange innehållet i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-150">When using filters to qualify the **Path** parameter, you need to include a trailing asterisk (`*`) to indicate the contents of the path.</span></span>

<span data-ttu-id="d4ac7-151">Följande kommando hämtar innehållet för alla `*.log` filer i `C:\Temp` katalogen.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-151">The following command gets the content of all `*.log` files in the `C:\Temp` directory.</span></span>

```powershell
Get-Content -Path C:\Temp\* -Filter *.log
```

### <span data-ttu-id="d4ac7-152">Exempel 8: Hämta fil innehåll som en byte mat ris</span><span class="sxs-lookup"><span data-stu-id="d4ac7-152">Example 8: Get file contents as a byte array</span></span>

<span data-ttu-id="d4ac7-153">Det här exemplet visar hur du hämtar innehållet i en fil som ett `[byte[]]` enda objekt.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-153">This example demonstrates how to get the contents of a file as a `[byte[]]` as a single object.</span></span>

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

<span data-ttu-id="d4ac7-154">Det första kommandot använder parametern **AsByteStream** för att hämta data strömmen av byte från filen.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-154">The first command uses the **AsByteStream** parameter to get the stream of bytes from the file.</span></span>
<span data-ttu-id="d4ac7-155">Parametern **RAW** ser till att byte returneras som en `[System.Byte[]]` .</span><span class="sxs-lookup"><span data-stu-id="d4ac7-155">The **Raw** parameter ensures that the bytes are returned as a `[System.Byte[]]`.</span></span> <span data-ttu-id="d4ac7-156">Om den **råa** parametern saknas är returvärdet en data ström med byte, som tolkas av PowerShell som `[System.Object[]]` .</span><span class="sxs-lookup"><span data-stu-id="d4ac7-156">If the **Raw** parameter was absent, the return value is a stream of bytes, which is interpreted by PowerShell as `[System.Object[]]`.</span></span>

## <span data-ttu-id="d4ac7-157">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="d4ac7-157">PARAMETERS</span></span>

### <span data-ttu-id="d4ac7-158">-Path</span><span class="sxs-lookup"><span data-stu-id="d4ac7-158">-Path</span></span>

<span data-ttu-id="d4ac7-159">Anger sökvägen till ett objekt där `Get-Content` hämtar innehållet.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-159">Specifies the path to an item where `Get-Content` gets the content.</span></span> <span data-ttu-id="d4ac7-160">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-160">Wildcard characters are permitted.</span></span> <span data-ttu-id="d4ac7-161">Sök vägarna måste vara sökvägar till objekt, inte behållare.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-161">The paths must be paths to items, not to containers.</span></span> <span data-ttu-id="d4ac7-162">Du måste till exempel ange en sökväg till en eller flera filer, inte en sökväg till en katalog.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-162">For example, you must specify a path to one or more files, not a path to a directory.</span></span>

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

### <span data-ttu-id="d4ac7-163">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="d4ac7-163">-LiteralPath</span></span>

<span data-ttu-id="d4ac7-164">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-164">Specifies a path to one or more locations.</span></span> <span data-ttu-id="d4ac7-165">Värdet för **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-165">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="d4ac7-166">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-166">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="d4ac7-167">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-167">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="d4ac7-168">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-168">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="d4ac7-169">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="d4ac7-169">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="d4ac7-170">-ReadCount</span><span class="sxs-lookup"><span data-stu-id="d4ac7-170">-ReadCount</span></span>

<span data-ttu-id="d4ac7-171">Anger hur många rader med innehåll som skickas via pipelinen i taget.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-171">Specifies how many lines of content are sent through the pipeline at a time.</span></span> <span data-ttu-id="d4ac7-172">Standardvärdet är 1.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-172">The default value is 1.</span></span>
<span data-ttu-id="d4ac7-173">Värdet 0 (noll) skickar allt innehåll på en och samma tidpunkt.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-173">A value of 0 (zero) sends all of the content at one time.</span></span>

<span data-ttu-id="d4ac7-174">Den här parametern ändrar inte det innehåll som visas, men det påverkar hur lång tid det tar att visa innehållet.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-174">This parameter does not change the content displayed, but it does affect the time it takes to display the content.</span></span> <span data-ttu-id="d4ac7-175">När värdet för **ReadCount** ökar, kommer tiden det tar att returnera den första raden att öka, men den totala tiden för åtgärden minskar.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-175">As the value of **ReadCount** increases, the time it takes to return the first line increases, but the total time for the operation decreases.</span></span> <span data-ttu-id="d4ac7-176">Detta kan göra en märkbar skillnad i stora objekt.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-176">This can make a perceptible difference in large items.</span></span>

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

### <span data-ttu-id="d4ac7-177">– TotalCount</span><span class="sxs-lookup"><span data-stu-id="d4ac7-177">-TotalCount</span></span>

<span data-ttu-id="d4ac7-178">Anger antalet rader från början av en fil eller ett annat objekt.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-178">Specifies the number of lines from the beginning of a file or other item.</span></span> <span data-ttu-id="d4ac7-179">Standardvärdet är-1 (alla rader).</span><span class="sxs-lookup"><span data-stu-id="d4ac7-179">The default is -1 (all lines).</span></span>

<span data-ttu-id="d4ac7-180">Du kan använda **totalCount** -parameterns namn eller dess alias, **först** eller **Head**.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-180">You can use the **TotalCount** parameter name or its aliases, **First** or **Head**.</span></span>

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

### <span data-ttu-id="d4ac7-181">-Pilslut</span><span class="sxs-lookup"><span data-stu-id="d4ac7-181">-Tail</span></span>

<span data-ttu-id="d4ac7-182">Anger antalet rader från slutet av en fil eller ett annat objekt.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-182">Specifies the number of lines from the end of a file or other item.</span></span> <span data-ttu-id="d4ac7-183">Du kan använda **slutet** av parameter namnet eller dess alias, **sist**.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-183">You can use the **Tail** parameter name or its alias, **Last**.</span></span> <span data-ttu-id="d4ac7-184">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-184">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="d4ac7-185">-Filter</span><span class="sxs-lookup"><span data-stu-id="d4ac7-185">-Filter</span></span>

<span data-ttu-id="d4ac7-186">Anger ett filter för att kvalificera **Sök vägs** parametern.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-186">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="d4ac7-187">[Fil Systems](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) leverantören är den enda installerade PowerShell-providern som stöder användningen av filter.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-187">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="d4ac7-188">Du kan hitta syntaxen för filter språket för **fil systemet** i [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="d4ac7-188">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="d4ac7-189">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-189">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="d4ac7-190">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="d4ac7-190">-Include</span></span>

<span data-ttu-id="d4ac7-191">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-191">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="d4ac7-192">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="d4ac7-192">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="d4ac7-193">Ange ett Sök vägs element eller ett mönster, till exempel `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="d4ac7-193">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="d4ac7-194">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-194">Wildcard characters are permitted.</span></span> <span data-ttu-id="d4ac7-195">Parametern **include** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-195">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="d4ac7-196">-Undanta</span><span class="sxs-lookup"><span data-stu-id="d4ac7-196">-Exclude</span></span>

<span data-ttu-id="d4ac7-197">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-197">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span>
<span data-ttu-id="d4ac7-198">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="d4ac7-198">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="d4ac7-199">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="d4ac7-199">Enter a path element or pattern, such as `*.txt`.</span></span>
<span data-ttu-id="d4ac7-200">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-200">Wildcard characters are permitted.</span></span>

<span data-ttu-id="d4ac7-201">Parametern **exclude** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-201">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="d4ac7-202">-Force</span><span class="sxs-lookup"><span data-stu-id="d4ac7-202">-Force</span></span>

<span data-ttu-id="d4ac7-203">**Force** åsidosätter ett skrivskyddat attribut eller skapar kataloger för att slutföra en fil Sök väg.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-203">**Force** will override a read-only attribute or create directories to complete a file path.</span></span> <span data-ttu-id="d4ac7-204">**Force** -parametern försöker inte ändra fil behörigheter eller Åsidosätt säkerhets begränsningar.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-204">The **Force** parameter does not attempt to change file permissions or override security restrictions.</span></span>

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

### <span data-ttu-id="d4ac7-205">-Credential</span><span class="sxs-lookup"><span data-stu-id="d4ac7-205">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="d4ac7-206">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-206">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="d4ac7-207">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="d4ac7-207">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="d4ac7-208">-Avgränsare</span><span class="sxs-lookup"><span data-stu-id="d4ac7-208">-Delimiter</span></span>

<span data-ttu-id="d4ac7-209">Anger den avgränsare som `Get-Content` används för att dela upp filen i objekt när den läses.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-209">Specifies the delimiter that `Get-Content` uses to divide the file into objects while it reads.</span></span> <span data-ttu-id="d4ac7-210">Standardvärdet är `\n` rad slutet.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-210">The default is `\n`, the end-of-line character.</span></span> <span data-ttu-id="d4ac7-211">När du läser en textfil `Get-Content` returnerar en samling sträng objekt, som var och en slutar med ett rad sluts tecken.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-211">When reading a text file, `Get-Content` returns a collection of string objects, each of which ends with an end-of-line character.</span></span> <span data-ttu-id="d4ac7-212">När du anger en avgränsare som inte finns i filen `Get-Content` returneras hela filen som ett enkelt, icke-avgränsat objekt.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-212">When you enter a delimiter that does not exist in the file, `Get-Content` returns the entire file as a single, undelimited object.</span></span>

<span data-ttu-id="d4ac7-213">Du kan använda den här parametern för att dela upp en stor fil i mindre filer genom att ange en fil avgränsare, som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-213">You can use this parameter to split a large file into smaller files by specifying a file separator, as the delimiter.</span></span> <span data-ttu-id="d4ac7-214">Avgränsaren bevaras (tas inte bort) och blir det sista objektet i varje fil avsnitt.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-214">The delimiter is preserved (not discarded) and becomes the last item in each file section.</span></span>

<span data-ttu-id="d4ac7-215">**Avgränsaren** är en dynamisk parameter som **fil Systems** leverantören lägger till i `Get-Content` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-215">**Delimiter** is a dynamic parameter that the **FileSystem** provider adds to the `Get-Content` cmdlet.</span></span> <span data-ttu-id="d4ac7-216">Den här parametern fungerar bara i fil system enheter.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-216">This parameter works only in file system drives.</span></span>

> [!NOTE]
> <span data-ttu-id="d4ac7-217">När värdet för **avgränsare** -parametern är en tom sträng `Get-Content` returnerar inte något.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-217">Currently, when the value of the **Delimiter** parameter is an empty string, `Get-Content` does not return anything.</span></span> <span data-ttu-id="d4ac7-218">Detta är ett känt problem.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-218">This is a known issue.</span></span> <span data-ttu-id="d4ac7-219">För att tvinga fram `Get-Content` att returnera hela filen som en enda, unavgränsad sträng.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-219">To force `Get-Content` to return the entire file as a single, undelimited string.</span></span> <span data-ttu-id="d4ac7-220">Ange ett värde som inte finns i filen.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-220">Enter a value that does not exist in the file.</span></span>

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

### <span data-ttu-id="d4ac7-221">– Vänta</span><span class="sxs-lookup"><span data-stu-id="d4ac7-221">-Wait</span></span>

<span data-ttu-id="d4ac7-222">Ser till att filen är öppen när alla befintliga rader har skrivits ut.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-222">Keeps the file open after all existing lines have been output.</span></span> <span data-ttu-id="d4ac7-223">Vid väntan, `Get-Content` kontrollerar filen en gång i sekunden och utvärderar nya rader om den är tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-223">While waiting, `Get-Content` checks the file once each second and outputs new lines if present.</span></span> <span data-ttu-id="d4ac7-224">Du kan avbryta **väntan** genom att trycka på **CTRL + C**.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-224">You can interrupt **Wait** by pressing **CTRL+C**.</span></span> <span data-ttu-id="d4ac7-225">Väntan avslutas också om filen tas bort, i vilket fall ett icke-avslutande fel rapporteras.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-225">Waiting also ends if the file gets deleted, in which case a non-terminating error is reported.</span></span>

<span data-ttu-id="d4ac7-226">**Wait** är en dynamisk parameter som fil system leverantören lägger till i `Get-Content` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-226">**Wait** is a dynamic parameter that the FileSystem provider adds to the `Get-Content` cmdlet.</span></span> <span data-ttu-id="d4ac7-227">Den här parametern fungerar bara i fil system enheter.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-227">This parameter works only in file system drives.</span></span> <span data-ttu-id="d4ac7-228">**Väntan** kan inte kombineras med **RAW**.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-228">**Wait** cannot be combined with **Raw**.</span></span>

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

### <span data-ttu-id="d4ac7-229">– RAW</span><span class="sxs-lookup"><span data-stu-id="d4ac7-229">-Raw</span></span>

<span data-ttu-id="d4ac7-230">Ignorerar rad matnings tecken och returnerar hela innehållet i en fil i en sträng med newlines bevarad.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-230">Ignores newline characters and returns the entire contents of a file in one string with the newlines preserved.</span></span> <span data-ttu-id="d4ac7-231">Som standard används rad matnings tecken i en fil som avgränsare för att separera indata till en sträng mat ris.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-231">By default, newline characters in a file are used as delimiters to separate the input into an array of strings.</span></span> <span data-ttu-id="d4ac7-232">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-232">This parameter was introduced in PowerShell 3.0.</span></span>

<span data-ttu-id="d4ac7-233">**RAW** är en dynamisk parameter som **fil** Systems leverantören lägger till i `Get-Content` cmdleten den här parametern fungerar endast i fil system enheter.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-233">**Raw** is a dynamic parameter that the **FileSystem** provider adds to the `Get-Content` cmdlet This parameter works only in file system drives.</span></span>

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

### <span data-ttu-id="d4ac7-234">-Encoding</span><span class="sxs-lookup"><span data-stu-id="d4ac7-234">-Encoding</span></span>

<span data-ttu-id="d4ac7-235">Anger typ av kodning för mål filen.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-235">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="d4ac7-236">Standardvärdet är `utf8NoBOM`.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-236">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="d4ac7-237">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="d4ac7-237">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="d4ac7-238">`ascii`: Använder kodningen för ASCII-teckenuppsättningen (7 bitar).</span><span class="sxs-lookup"><span data-stu-id="d4ac7-238">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="d4ac7-239">`bigendianunicode`: Kodar i UTF-16-format med big-endian byte-ordning.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-239">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="d4ac7-240">`bigendianutf32`: Kodar i UTF-32-format med big-endian-dataordningen.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-240">`bigendianutf32`: Encodes in UTF-32 format using the big-endian byte order.</span></span>
- <span data-ttu-id="d4ac7-241">`oem`: Använder standard kodning för MS-DOS-och-konsol program.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-241">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="d4ac7-242">`unicode`: Kodar i UTF-16-format med lite-endian-dataordning.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-242">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="d4ac7-243">`utf7`: Kodar i UTF-7-format.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-243">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="d4ac7-244">`utf8`: Kodar i UTF-8-format.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-244">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="d4ac7-245">`utf8BOM`: Kodar i UTF-8-format med byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="d4ac7-245">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="d4ac7-246">`utf8NoBOM`: Kodar i UTF-8-format utan byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="d4ac7-246">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="d4ac7-247">`utf32`: Kodar i UTF-32-format.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-247">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="d4ac7-248">Encoding är en dynamisk parameter som **fil Systems** leverantören lägger till i `Get-Content` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-248">Encoding is a dynamic parameter that the **FileSystem** provider adds to the `Get-Content` cmdlet.</span></span>
<span data-ttu-id="d4ac7-249">Den här parametern är endast tillgänglig i fil system enheter.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-249">This parameter is available only in file system drives.</span></span>

<span data-ttu-id="d4ac7-250">När du läser från och skriver till binära filer använder du parametern **AsByteStream** och värdet 0 för parametern **ReadCount** .</span><span class="sxs-lookup"><span data-stu-id="d4ac7-250">When reading from and writing to binary files, use the **AsByteStream** parameter and a value of 0 for the **ReadCount** parameter.</span></span> <span data-ttu-id="d4ac7-251">Ett **ReadCount** -värde på 0 läser hela filen i en enda Läs åtgärd.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-251">A **ReadCount** value of 0 reads the entire file in a single read operation.</span></span> <span data-ttu-id="d4ac7-252">Standardvärdet för **ReadCount** , 1, läser en byte i varje Läs åtgärd och konverterar varje byte till ett separat objekt, vilket orsakar fel när du använder `Set-Content` cmdleten för att skriva byte till en fil om du inte använder parametern **AsByteStream** .</span><span class="sxs-lookup"><span data-stu-id="d4ac7-252">The default **ReadCount** value, 1, reads one byte in each read operation and converts each byte into a separate object, which causes errors when you use the `Set-Content` cmdlet to write the bytes to a file unless you use **AsByteStream** parameter.</span></span>

<span data-ttu-id="d4ac7-253">Från och med PowerShell 6,2 tillåter **encoding** -parametern även numeriska ID: n för registrerade tecken tabeller (som `-Encoding 1251` ) eller sträng namn för registrerade tecken tabeller (som `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="d4ac7-253">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="d4ac7-254">Mer information finns i .NET-dokumentationen för [encoding. codepage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span><span class="sxs-lookup"><span data-stu-id="d4ac7-254">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

> [!NOTE]
> <span data-ttu-id="d4ac7-255">**UTF-7** _ rekommenderas inte längre att använda.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-255">**UTF-7** _ is no longer recommended to use.</span></span> <span data-ttu-id="d4ac7-256">I PowerShell 7,1 skrivs en varning om du anger `utf7` för parametern _ \*encoding\*\*.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-256">In PowerShell 7.1, a warning is written if you specify `utf7` for the _ *Encoding*\* parameter.</span></span>

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

### <span data-ttu-id="d4ac7-257">-Stream</span><span class="sxs-lookup"><span data-stu-id="d4ac7-257">-Stream</span></span>

> [!NOTE]
> <span data-ttu-id="d4ac7-258">Den här parametern är endast tillgänglig i Windows.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-258">This Parameter is only available on Windows.</span></span>

<span data-ttu-id="d4ac7-259">Hämtar innehållet i den angivna alternativa NTFS-filströmen från filen.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-259">Gets the contents of the specified alternate NTFS file stream from the file.</span></span> <span data-ttu-id="d4ac7-260">Ange data ström namnet.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-260">Enter the stream name.</span></span>
<span data-ttu-id="d4ac7-261">Jokertecken stöds inte.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-261">Wildcards are not supported.</span></span>

<span data-ttu-id="d4ac7-262">**Stream** är en dynamisk parameter som **fil Systems** leverantören lägger till i `Get-Content` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-262">**Stream** is a dynamic parameter that the **FileSystem** provider adds to the `Get-Content` cmdlet.</span></span>
<span data-ttu-id="d4ac7-263">Den här parametern fungerar bara i fil system enheter på Windows-system.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-263">This parameter works only in file system drives on Windows systems.</span></span> <span data-ttu-id="d4ac7-264">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-264">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="d4ac7-265">-AsByteStream</span><span class="sxs-lookup"><span data-stu-id="d4ac7-265">-AsByteStream</span></span>

<span data-ttu-id="d4ac7-266">Anger att innehållet ska läsas som en data ström med byte.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-266">Specifies that the content should be read as a stream of bytes.</span></span> <span data-ttu-id="d4ac7-267">**AsByteStream** -parametern introducerades i Windows PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-267">The **AsByteStream** parameter was introduced in Windows PowerShell 6.0.</span></span>

<span data-ttu-id="d4ac7-268">En varning inträffar när du använder parametern **AsByteStream** med parametern **encoding** .</span><span class="sxs-lookup"><span data-stu-id="d4ac7-268">A warning occurs when you use the **AsByteStream** parameter with the **Encoding** parameter.</span></span> <span data-ttu-id="d4ac7-269">Parametern **AsByteStream** ignorerar all kodning och utdata returneras som en data ström med byte.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-269">The **AsByteStream** parameter ignores any encoding and the output is returned as a stream of bytes.</span></span>

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

### <span data-ttu-id="d4ac7-270">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d4ac7-270">CommonParameters</span></span>

<span data-ttu-id="d4ac7-271">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-271">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d4ac7-272">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d4ac7-272">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d4ac7-273">INDATA</span><span class="sxs-lookup"><span data-stu-id="d4ac7-273">INPUTS</span></span>

### <span data-ttu-id="d4ac7-274">System. Int64, system. string [], system. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="d4ac7-274">System.Int64, System.String[], System.Management.Automation.PSCredential</span></span>

<span data-ttu-id="d4ac7-275">Du kan skicka vidare antalet läsningar, totalt antal, sökvägar eller autentiseringsuppgifter till `Get-Content` .</span><span class="sxs-lookup"><span data-stu-id="d4ac7-275">You can pipe the read count, total count, paths, or credentials to `Get-Content`.</span></span>

## <span data-ttu-id="d4ac7-276">UTDATA</span><span class="sxs-lookup"><span data-stu-id="d4ac7-276">OUTPUTS</span></span>

### <span data-ttu-id="d4ac7-277">System. byte, system. String</span><span class="sxs-lookup"><span data-stu-id="d4ac7-277">System.Byte, System.String</span></span>

<span data-ttu-id="d4ac7-278">`Get-Content` Returnerar strängar eller byte.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-278">`Get-Content` returns strings or bytes.</span></span> <span data-ttu-id="d4ac7-279">Utdatatypen beror på vilken typ av innehåll som du anger som indata.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-279">The output type depends upon the type of content that you specify as input.</span></span>

## <span data-ttu-id="d4ac7-280">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="d4ac7-280">NOTES</span></span>

<span data-ttu-id="d4ac7-281">`Get-Content`Cmdleten är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="d4ac7-281">The `Get-Content` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="d4ac7-282">Använd cmdleten för att hämta providers i sessionen `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="d4ac7-282">To get the providers in your session, use the `Get-PSProvider` cmdlet.</span></span> <span data-ttu-id="d4ac7-283">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="d4ac7-283">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="d4ac7-284">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="d4ac7-284">RELATED LINKS</span></span>

[<span data-ttu-id="d4ac7-285">about_Automatic_Variables</span><span class="sxs-lookup"><span data-stu-id="d4ac7-285">about_Automatic_Variables</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="d4ac7-286">about_Providers</span><span class="sxs-lookup"><span data-stu-id="d4ac7-286">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="d4ac7-287">Lägg till innehåll</span><span class="sxs-lookup"><span data-stu-id="d4ac7-287">Add-Content</span></span>](Add-Content.md)

[<span data-ttu-id="d4ac7-288">Rensa innehåll</span><span class="sxs-lookup"><span data-stu-id="d4ac7-288">Clear-Content</span></span>](Clear-Content.md)

[<span data-ttu-id="d4ac7-289">-Objekt</span><span class="sxs-lookup"><span data-stu-id="d4ac7-289">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="d4ac7-290">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="d4ac7-290">Get-PSProvider</span></span>](Get-PSProvider.md)

[<span data-ttu-id="d4ac7-291">Ange innehåll</span><span class="sxs-lookup"><span data-stu-id="d4ac7-291">Set-Content</span></span>](Set-Content.md)
