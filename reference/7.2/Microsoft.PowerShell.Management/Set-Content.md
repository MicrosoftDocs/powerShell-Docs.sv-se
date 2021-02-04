---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-content?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Content
ms.openlocfilehash: d85e0219c325de998c5874224a33ac4263b787a3
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/19/2020
ms.locfileid: "97692961"
---
# <span data-ttu-id="e17b6-102">Set-Content</span><span class="sxs-lookup"><span data-stu-id="e17b6-102">Set-Content</span></span>

## <span data-ttu-id="e17b6-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="e17b6-103">SYNOPSIS</span></span>
<span data-ttu-id="e17b6-104">Skriver nytt innehåll eller ersätter befintligt innehåll i en fil.</span><span class="sxs-lookup"><span data-stu-id="e17b6-104">Writes new content or replaces existing content in a file.</span></span>

## <span data-ttu-id="e17b6-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e17b6-105">SYNTAX</span></span>

### <span data-ttu-id="e17b6-106">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="e17b6-106">Path (Default)</span></span>

```
Set-Content [-Path] <string[]> [-Value] <Object[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>]
 [-WhatIf] [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

### <span data-ttu-id="e17b6-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="e17b6-107">LiteralPath</span></span>

```
Set-Content [-Value] <Object[]> -LiteralPath <string[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>]
 [-WhatIf] [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

## <span data-ttu-id="e17b6-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e17b6-108">DESCRIPTION</span></span>

<span data-ttu-id="e17b6-109">`Set-Content` är en sträng bearbetnings-cmdlet som skriver nytt innehåll eller ersätter innehållet i en fil.</span><span class="sxs-lookup"><span data-stu-id="e17b6-109">`Set-Content` is a string-processing cmdlet that writes new content or replaces the content in a file.</span></span> <span data-ttu-id="e17b6-110">`Set-Content` ersätter det befintliga innehållet och skiljer sig från den `Add-Content` cmdlet som lägger till innehåll i en fil.</span><span class="sxs-lookup"><span data-stu-id="e17b6-110">`Set-Content` replaces the existing content and differs from the `Add-Content` cmdlet that appends content to a file.</span></span> <span data-ttu-id="e17b6-111">Om du vill skicka innehåll till `Set-Content` kan du använda parametern **Value** på kommando raden eller skicka innehåll via pipelinen.</span><span class="sxs-lookup"><span data-stu-id="e17b6-111">To send content to `Set-Content` you can use the **Value** parameter on the command line or send content through the pipeline.</span></span>

<span data-ttu-id="e17b6-112">Om du behöver skapa filer eller kataloger för följande exempel, se [New-item](New-Item.md).</span><span class="sxs-lookup"><span data-stu-id="e17b6-112">If you need to create files or directories for the following examples, see [New-Item](New-Item.md).</span></span>

## <span data-ttu-id="e17b6-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="e17b6-113">EXAMPLES</span></span>

### <span data-ttu-id="e17b6-114">Exempel 1: Ersätt innehållet i flera filer i en katalog</span><span class="sxs-lookup"><span data-stu-id="e17b6-114">Example 1: Replace the contents of multiple files in a directory</span></span>

<span data-ttu-id="e17b6-115">I det här exemplet ersätts innehållet för flera filer i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="e17b6-115">This example replaces the content for multiple files in the current directory.</span></span>

```powershell
Get-ChildItem -Path .\Test*.txt
```

```Output
Test1.txt
Test2.txt
Test3.txt
```

```powershell
Set-Content -Path .\Test*.txt -Value 'Hello, World'
Get-Content -Path .\Test*.txt
```

```Output
Hello, World
Hello, World
Hello, World
```

<span data-ttu-id="e17b6-116">`Get-ChildItem`Cmdleten använder **Sök vägs** parametern för att visa **. txt** -filer som börjar med `Test*` i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="e17b6-116">The `Get-ChildItem` cmdlet uses the **Path** parameter to list **.txt** files that begin with `Test*` in the current directory.</span></span> <span data-ttu-id="e17b6-117">`Set-Content`Cmdleten använder parametern **Path** för att ange `Test*.txt` filerna.</span><span class="sxs-lookup"><span data-stu-id="e17b6-117">The `Set-Content` cmdlet uses the **Path** parameter to specify the `Test*.txt` files.</span></span> <span data-ttu-id="e17b6-118">Parametern **Value** innehåller text strängen **Hello, World** som ersätter det befintliga innehållet i varje fil.</span><span class="sxs-lookup"><span data-stu-id="e17b6-118">The **Value** parameter provides the text string **Hello, World** that replaces the existing content in each file.</span></span> <span data-ttu-id="e17b6-119">`Get-Content`Cmdleten använder parametern **Path** för att ange `Test*.txt` filerna och visar varje fils innehåll i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="e17b6-119">The `Get-Content` cmdlet uses the **Path** parameter to specify the `Test*.txt` files and displays each file's content in the PowerShell console.</span></span>

### <span data-ttu-id="e17b6-120">Exempel 2: skapa en ny fil och skriv innehåll</span><span class="sxs-lookup"><span data-stu-id="e17b6-120">Example 2: Create a new file and write content</span></span>

<span data-ttu-id="e17b6-121">Det här exemplet skapar en ny fil och skriver aktuellt datum och tid till filen.</span><span class="sxs-lookup"><span data-stu-id="e17b6-121">This example creates a new file and writes the current date and time to the file.</span></span>

```powershell
Set-Content -Path .\DateTime.txt -Value (Get-Date)
Get-Content -Path .\DateTime.txt
```

```Output
1/30/2019 09:55:08
```

<span data-ttu-id="e17b6-122">`Set-Content` använder parametrarna **sökväg** och **värde** för att skapa en ny fil med namnet **DateTime.txt** i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="e17b6-122">`Set-Content` uses the **Path** and **Value** parameters to create a new file named **DateTime.txt** in the current directory.</span></span> <span data-ttu-id="e17b6-123">**Värde** parametern använder `Get-Date` för att hämta aktuellt datum och aktuell tid.</span><span class="sxs-lookup"><span data-stu-id="e17b6-123">The **Value** parameter uses `Get-Date` to get the current date and time.</span></span>
<span data-ttu-id="e17b6-124">`Set-Content` skriver **datetime** -objektet till filen som en sträng.</span><span class="sxs-lookup"><span data-stu-id="e17b6-124">`Set-Content` writes the **DateTime** object to the file as a string.</span></span> <span data-ttu-id="e17b6-125">`Get-Content`Cmdleten använder parametern **Path** för att visa innehållet i **DateTime.txt** i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="e17b6-125">The `Get-Content` cmdlet uses the **Path** parameter to display the content of **DateTime.txt** in the PowerShell console.</span></span>

### <span data-ttu-id="e17b6-126">Exempel 3: ersätt text i en fil</span><span class="sxs-lookup"><span data-stu-id="e17b6-126">Example 3: Replace text in a file</span></span>

<span data-ttu-id="e17b6-127">Det här kommandot ersätter alla instanser av Word i en befintlig fil.</span><span class="sxs-lookup"><span data-stu-id="e17b6-127">This command replaces all instances of word within an existing file.</span></span>

```powershell
Get-Content -Path .\Notice.txt
```

```Output
Warning
Replace Warning with a new word.
The word Warning was replaced.
```

```powershell
(Get-Content -Path .\Notice.txt) |
    ForEach-Object {$_ -Replace 'Warning', 'Caution'} |
        Set-Content -Path .\Notice.txt
Get-Content -Path .\Notice.txt
```

```Output
Caution
Replace Caution with a new word.
The word Caution was replaced.
```

<span data-ttu-id="e17b6-128">`Get-Content`Cmdleten använder parametern **Path** för att ange **Notice.txt** filen i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="e17b6-128">The `Get-Content` cmdlet uses the **Path** parameter to specify the **Notice.txt** file in the current directory.</span></span> <span data-ttu-id="e17b6-129">`Get-Content`Kommandot omges av parenteser så att kommandot slutförs innan det skickas ned pipelinen.</span><span class="sxs-lookup"><span data-stu-id="e17b6-129">The `Get-Content` command is wrapped with parentheses so that the command finishes before being sent down the pipeline.</span></span>

<span data-ttu-id="e17b6-130">Innehållet i **Notice.txt** -filen skickas ned pipelinen till `ForEach-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e17b6-130">The contents of the **Notice.txt** file are sent down the pipeline to the `ForEach-Object` cmdlet.</span></span>
<span data-ttu-id="e17b6-131">`ForEach-Object` använder den automatiska variabeln `$_` och ersätter varje förekomst av **Varning** med **försiktighet**.</span><span class="sxs-lookup"><span data-stu-id="e17b6-131">`ForEach-Object` uses the automatic variable `$_` and replaces each occurrence of **Warning** with **Caution**.</span></span> <span data-ttu-id="e17b6-132">Objekten skickas ned pipelinen till `Set-Content` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e17b6-132">The objects are sent down the pipeline to the `Set-Content` cmdlet.</span></span> <span data-ttu-id="e17b6-133">`Set-Content` använder parametern **Path** för att ange **Notice.txt** -filen och skriver det uppdaterade innehållet till filen.</span><span class="sxs-lookup"><span data-stu-id="e17b6-133">`Set-Content` uses the **Path** parameter to specify the **Notice.txt** file and writes the updated content to the file.</span></span>

<span data-ttu-id="e17b6-134">Den sista `Get-Content` cmdleten visar det uppdaterade fil innehållet i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="e17b6-134">The last `Get-Content` cmdlet displays the updated file content in the PowerShell console.</span></span>

### <span data-ttu-id="e17b6-135">Exempel 4: använda filter med Set-Content</span><span class="sxs-lookup"><span data-stu-id="e17b6-135">Example 4: Use Filters with Set-Content</span></span>

<span data-ttu-id="e17b6-136">Du kan ange ett filter för `Set-Content` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e17b6-136">You can specify a filter to the `Set-Content` cmdlet.</span></span> <span data-ttu-id="e17b6-137">När du använder filter för att kvalificera **Sök vägs** parametern måste du inkludera en efterföljande asterisk ( `*` ) för att ange innehållet i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="e17b6-137">When using filters to qualify the **Path** parameter, you need to include a trailing asterisk (`*`) to indicate the contents of the path.</span></span>

<span data-ttu-id="e17b6-138">Följande kommando anger innehållet `*.txt` för alla filer i `C:\Temp` katalogen till **värdet** Empty.</span><span class="sxs-lookup"><span data-stu-id="e17b6-138">The following command set the content all `*.txt` files in the `C:\Temp` directory to the **Value** empty.</span></span>

```powershell
Set-Content -Path C:\Temp\* -Filter *.txt -Value "Empty"
```

## <span data-ttu-id="e17b6-139">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="e17b6-139">PARAMETERS</span></span>

### <span data-ttu-id="e17b6-140">-AsByteStream</span><span class="sxs-lookup"><span data-stu-id="e17b6-140">-AsByteStream</span></span>

<span data-ttu-id="e17b6-141">Anger att innehållet ska läsas som en data ström med byte.</span><span class="sxs-lookup"><span data-stu-id="e17b6-141">Specifies that the content should be read as a stream of bytes.</span></span> <span data-ttu-id="e17b6-142">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="e17b6-142">This parameter was introduced in PowerShell 6.0.</span></span>

<span data-ttu-id="e17b6-143">En varning inträffar när du använder parametern **AsByteStream** med parametern **encoding** .</span><span class="sxs-lookup"><span data-stu-id="e17b6-143">A warning occurs when you use the **AsByteStream** parameter with the **Encoding** parameter.</span></span> <span data-ttu-id="e17b6-144">Parametern **AsByteStream** ignorerar all kodning och utdata returneras som en data ström med byte.</span><span class="sxs-lookup"><span data-stu-id="e17b6-144">The **AsByteStream** parameter ignores any encoding and the output is returned as a stream of bytes.</span></span>

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

### <span data-ttu-id="e17b6-145">-Credential</span><span class="sxs-lookup"><span data-stu-id="e17b6-145">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="e17b6-146">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e17b6-146">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="e17b6-147">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="e17b6-147">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e17b6-148">-Encoding</span><span class="sxs-lookup"><span data-stu-id="e17b6-148">-Encoding</span></span>

<span data-ttu-id="e17b6-149">Anger typ av kodning för mål filen.</span><span class="sxs-lookup"><span data-stu-id="e17b6-149">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="e17b6-150">Standardvärdet är `utf8NoBOM`.</span><span class="sxs-lookup"><span data-stu-id="e17b6-150">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="e17b6-151">Encoding är en dynamisk parameter som fil Systems leverantören lägger till i `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="e17b6-151">Encoding is a dynamic parameter that the FileSystem provider adds to `Set-Content`.</span></span> <span data-ttu-id="e17b6-152">Den här parametern fungerar bara i fil system enheter.</span><span class="sxs-lookup"><span data-stu-id="e17b6-152">This parameter works only in file system drives.</span></span>

<span data-ttu-id="e17b6-153">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="e17b6-153">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="e17b6-154">`ascii`: Använder kodningen för ASCII-teckenuppsättningen (7 bitar).</span><span class="sxs-lookup"><span data-stu-id="e17b6-154">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="e17b6-155">`bigendianunicode`: Kodar i UTF-16-format med big-endian byte-ordning.</span><span class="sxs-lookup"><span data-stu-id="e17b6-155">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="e17b6-156">`bigendianutf32`: Kodar i UTF-32-format med big-endian-dataordningen.</span><span class="sxs-lookup"><span data-stu-id="e17b6-156">`bigendianutf32`: Encodes in UTF-32 format using the big-endian byte order.</span></span>
- <span data-ttu-id="e17b6-157">`oem`: Använder standard kodning för MS-DOS-och-konsol program.</span><span class="sxs-lookup"><span data-stu-id="e17b6-157">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="e17b6-158">`unicode`: Kodar i UTF-16-format med lite-endian-dataordning.</span><span class="sxs-lookup"><span data-stu-id="e17b6-158">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="e17b6-159">`utf7`: Kodar i UTF-7-format.</span><span class="sxs-lookup"><span data-stu-id="e17b6-159">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="e17b6-160">`utf8`: Kodar i UTF-8-format.</span><span class="sxs-lookup"><span data-stu-id="e17b6-160">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="e17b6-161">`utf8BOM`: Kodar i UTF-8-format med byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="e17b6-161">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="e17b6-162">`utf8NoBOM`: Kodar i UTF-8-format utan byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="e17b6-162">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="e17b6-163">`utf32`: Kodar i UTF-32-format.</span><span class="sxs-lookup"><span data-stu-id="e17b6-163">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="e17b6-164">Från och med PowerShell 6,2 tillåter **encoding** -parametern även numeriska ID: n för registrerade tecken tabeller (som `-Encoding 1251` ) eller sträng namn för registrerade tecken tabeller (som `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="e17b6-164">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="e17b6-165">Mer information finns i .NET-dokumentationen för [encoding. codepage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span><span class="sxs-lookup"><span data-stu-id="e17b6-165">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

> [!NOTE]
> <span data-ttu-id="e17b6-166">**UTF-7** _ rekommenderas inte längre att använda.</span><span class="sxs-lookup"><span data-stu-id="e17b6-166">**UTF-7** _ is no longer recommended to use.</span></span> <span data-ttu-id="e17b6-167">I PowerShell 7,1 skrivs en varning om du anger `utf7` för parametern _ \*encoding\*\*.</span><span class="sxs-lookup"><span data-stu-id="e17b6-167">In PowerShell 7.1, a warning is written if you specify `utf7` for the _ *Encoding*\* parameter.</span></span>

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

### <span data-ttu-id="e17b6-168">-Undanta</span><span class="sxs-lookup"><span data-stu-id="e17b6-168">-Exclude</span></span>

<span data-ttu-id="e17b6-169">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="e17b6-169">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="e17b6-170">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="e17b6-170">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="e17b6-171">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="e17b6-171">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="e17b6-172">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="e17b6-172">Wildcard characters are permitted.</span></span> <span data-ttu-id="e17b6-173">Parametern **exclude** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="e17b6-173">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="e17b6-174">-Filter</span><span class="sxs-lookup"><span data-stu-id="e17b6-174">-Filter</span></span>

<span data-ttu-id="e17b6-175">Anger ett filter för att kvalificera **Sök vägs** parametern.</span><span class="sxs-lookup"><span data-stu-id="e17b6-175">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="e17b6-176">[Fil Systems](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) leverantören är den enda installerade PowerShell-providern som stöder användningen av filter.</span><span class="sxs-lookup"><span data-stu-id="e17b6-176">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="e17b6-177">Du kan hitta syntaxen för filter språket för **fil systemet** i [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="e17b6-177">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="e17b6-178">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="e17b6-178">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="e17b6-179">-Force</span><span class="sxs-lookup"><span data-stu-id="e17b6-179">-Force</span></span>

<span data-ttu-id="e17b6-180">Tvingar cmdleten att ange innehållet i en fil, även om filen är skrivskyddad.</span><span class="sxs-lookup"><span data-stu-id="e17b6-180">Forces the cmdlet to set the contents of a file, even if the file is read-only.</span></span> <span data-ttu-id="e17b6-181">Implementeringen varierar från providern till providern.</span><span class="sxs-lookup"><span data-stu-id="e17b6-181">Implementation varies from provider to provider.</span></span> <span data-ttu-id="e17b6-182">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="e17b6-182">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
<span data-ttu-id="e17b6-183">**Force** -parametern åsidosätter inte säkerhets begränsningar.</span><span class="sxs-lookup"><span data-stu-id="e17b6-183">The **Force** parameter does not override security restrictions.</span></span>

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

### <span data-ttu-id="e17b6-184">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="e17b6-184">-Include</span></span>

<span data-ttu-id="e17b6-185">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="e17b6-185">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="e17b6-186">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="e17b6-186">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="e17b6-187">Ange ett Sök vägs element eller ett mönster, till exempel `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="e17b6-187">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="e17b6-188">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="e17b6-188">Wildcard characters are permitted.</span></span> <span data-ttu-id="e17b6-189">Parametern **include** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="e17b6-189">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="e17b6-190">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="e17b6-190">-LiteralPath</span></span>

<span data-ttu-id="e17b6-191">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="e17b6-191">Specifies a path to one or more locations.</span></span> <span data-ttu-id="e17b6-192">Värdet för **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="e17b6-192">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="e17b6-193">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="e17b6-193">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="e17b6-194">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="e17b6-194">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="e17b6-195">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="e17b6-195">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="e17b6-196">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="e17b6-196">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="e17b6-197">– NoNewline</span><span class="sxs-lookup"><span data-stu-id="e17b6-197">-NoNewline</span></span>

<span data-ttu-id="e17b6-198">Sträng representationerna av indata-objekten sammanfogas för att bilda utdata.</span><span class="sxs-lookup"><span data-stu-id="e17b6-198">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="e17b6-199">Inga blank steg eller newlines infogas mellan utgående strängar.</span><span class="sxs-lookup"><span data-stu-id="e17b6-199">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="e17b6-200">Ingen ny rad läggs till efter den sista utgående strängen.</span><span class="sxs-lookup"><span data-stu-id="e17b6-200">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="e17b6-201">– PassThru</span><span class="sxs-lookup"><span data-stu-id="e17b6-201">-PassThru</span></span>

<span data-ttu-id="e17b6-202">Returnerar ett objekt som representerar innehållet.</span><span class="sxs-lookup"><span data-stu-id="e17b6-202">Returns an object that represents the content.</span></span> <span data-ttu-id="e17b6-203">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="e17b6-203">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="e17b6-204">-Path</span><span class="sxs-lookup"><span data-stu-id="e17b6-204">-Path</span></span>

<span data-ttu-id="e17b6-205">Anger sökvägen till det objekt som tar emot innehållet.</span><span class="sxs-lookup"><span data-stu-id="e17b6-205">Specifies the path of the item that receives the content.</span></span>
<span data-ttu-id="e17b6-206">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="e17b6-206">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="e17b6-207">-Stream</span><span class="sxs-lookup"><span data-stu-id="e17b6-207">-Stream</span></span>

> [!NOTE]
> <span data-ttu-id="e17b6-208">Den här parametern är endast tillgänglig i Windows.</span><span class="sxs-lookup"><span data-stu-id="e17b6-208">This Parameter is only available on Windows.</span></span>

<span data-ttu-id="e17b6-209">Anger en alternativ data ström för innehåll.</span><span class="sxs-lookup"><span data-stu-id="e17b6-209">Specifies an alternative data stream for content.</span></span> <span data-ttu-id="e17b6-210">Om data strömmen inte finns skapar den här cmdleten den.</span><span class="sxs-lookup"><span data-stu-id="e17b6-210">If the stream does not exist, this cmdlet creates it.</span></span> <span data-ttu-id="e17b6-211">Jokertecken stöds inte.</span><span class="sxs-lookup"><span data-stu-id="e17b6-211">Wildcard characters are not supported.</span></span>

<span data-ttu-id="e17b6-212">**Stream** är en dynamisk parameter som **fil Systems** leverantören lägger till i `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="e17b6-212">**Stream** is a dynamic parameter that the **FileSystem** provider adds to `Set-Content`.</span></span> <span data-ttu-id="e17b6-213">Den här parametern fungerar bara i fil system enheter.</span><span class="sxs-lookup"><span data-stu-id="e17b6-213">This parameter works only in file system drives.</span></span>

<span data-ttu-id="e17b6-214">Du kan använda `Set-Content` cmdleten för att skapa eller uppdatera innehållet i valfri alternativ data ström, till exempel `Zone.Identifier` .</span><span class="sxs-lookup"><span data-stu-id="e17b6-214">You can use the `Set-Content` cmdlet to create or update the content of any alternate data stream, such as `Zone.Identifier`.</span></span> <span data-ttu-id="e17b6-215">Vi rekommenderar dock inte detta som ett sätt att eliminera säkerhets kontroller som blockerar filer som hämtas från Internet.</span><span class="sxs-lookup"><span data-stu-id="e17b6-215">However, we do not recommend this as a way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="e17b6-216">Om du verifierar att en Hämtad fil är säker använder du `Unblock-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e17b6-216">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="e17b6-217">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="e17b6-217">This parameter was introduced in PowerShell 3.0.</span></span> <span data-ttu-id="e17b6-218">Från och med PowerShell 7,2 `Set-Content` kan du ange innehållet för alternativa data strömmar från kataloger och filer.</span><span class="sxs-lookup"><span data-stu-id="e17b6-218">As of PowerShell 7.2, `Set-Content` can set the content of alternative data streams from directories as well as files.</span></span>

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

### <span data-ttu-id="e17b6-219">-Värde</span><span class="sxs-lookup"><span data-stu-id="e17b6-219">-Value</span></span>

<span data-ttu-id="e17b6-220">Anger det nya innehållet för objektet.</span><span class="sxs-lookup"><span data-stu-id="e17b6-220">Specifies the new content for the item.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="e17b6-221">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e17b6-221">-Confirm</span></span>

<span data-ttu-id="e17b6-222">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e17b6-222">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="e17b6-223">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e17b6-223">-WhatIf</span></span>

<span data-ttu-id="e17b6-224">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="e17b6-224">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="e17b6-225">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="e17b6-225">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="e17b6-226">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e17b6-226">CommonParameters</span></span>

<span data-ttu-id="e17b6-227">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e17b6-227">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e17b6-228">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e17b6-228">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e17b6-229">INDATA</span><span class="sxs-lookup"><span data-stu-id="e17b6-229">INPUTS</span></span>

### <span data-ttu-id="e17b6-230">System. Object</span><span class="sxs-lookup"><span data-stu-id="e17b6-230">System.Object</span></span>

<span data-ttu-id="e17b6-231">Du kan skicka en pipe till ett objekt som innehåller det nya värdet för objektet `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="e17b6-231">You can pipe an object that contains the new value for the item to `Set-Content`.</span></span>

## <span data-ttu-id="e17b6-232">UTDATA</span><span class="sxs-lookup"><span data-stu-id="e17b6-232">OUTPUTS</span></span>

### <span data-ttu-id="e17b6-233">Ingen eller system. String</span><span class="sxs-lookup"><span data-stu-id="e17b6-233">None or System.String</span></span>

<span data-ttu-id="e17b6-234">När du använder parametern **Passthru** `Set-Content` genererar ett **system. String** -objekt som representerar innehållet.</span><span class="sxs-lookup"><span data-stu-id="e17b6-234">When you use the **PassThru** parameter, `Set-Content` generates a **System.String** object that represents the content.</span></span> <span data-ttu-id="e17b6-235">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="e17b6-235">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="e17b6-236">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="e17b6-236">NOTES</span></span>

- <span data-ttu-id="e17b6-237">Du kan också referera till `Set-Content` med dess inbyggda alias `sc` .</span><span class="sxs-lookup"><span data-stu-id="e17b6-237">You can also refer to `Set-Content` by its built-in alias, `sc`.</span></span>
  <span data-ttu-id="e17b6-238">Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="e17b6-238">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="e17b6-239">`Set-Content` är utformad för sträng bearbetning.</span><span class="sxs-lookup"><span data-stu-id="e17b6-239">`Set-Content` is designed for string processing.</span></span> <span data-ttu-id="e17b6-240">Om du rör icke-sträng objekt till `Set-Content` konverteras objektet till en sträng innan det skrivs.</span><span class="sxs-lookup"><span data-stu-id="e17b6-240">If you pipe non-string objects to `Set-Content`, it converts the object to a string before writing it.</span></span> <span data-ttu-id="e17b6-241">Använd om du vill skriva objekt till filer `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="e17b6-241">To write objects to files, use `Out-File`.</span></span>
- <span data-ttu-id="e17b6-242">`Set-Content`Cmdleten är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="e17b6-242">The `Set-Content` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="e17b6-243">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="e17b6-243">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="e17b6-244">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="e17b6-244">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="e17b6-245">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="e17b6-245">RELATED LINKS</span></span>

[<span data-ttu-id="e17b6-246">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="e17b6-246">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="e17b6-247">about_Automatic_Variables. MD</span><span class="sxs-lookup"><span data-stu-id="e17b6-247">about_Automatic_Variables.md</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="e17b6-248">about_Providers</span><span class="sxs-lookup"><span data-stu-id="e17b6-248">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="e17b6-249">Lägg till innehåll</span><span class="sxs-lookup"><span data-stu-id="e17b6-249">Add-Content</span></span>](Add-Content.md)

[<span data-ttu-id="e17b6-250">Rensa innehåll</span><span class="sxs-lookup"><span data-stu-id="e17b6-250">Clear-Content</span></span>](Clear-Content.md)

[<span data-ttu-id="e17b6-251">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="e17b6-251">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="e17b6-252">Hämta innehåll</span><span class="sxs-lookup"><span data-stu-id="e17b6-252">Get-Content</span></span>](Get-Content.md)

[<span data-ttu-id="e17b6-253">-Objekt</span><span class="sxs-lookup"><span data-stu-id="e17b6-253">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="e17b6-254">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="e17b6-254">New-Item</span></span>](New-Item.md)
