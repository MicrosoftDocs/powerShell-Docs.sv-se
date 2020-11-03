---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 08/19/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-content?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Content
ms.openlocfilehash: bb9345470aa58dac7c14e1443c0fe4c12e7563a6
ms.sourcegitcommit: 9a8bb1b459b5939c95e1f6d9499fcb13d01a58c4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/25/2020
ms.locfileid: "93269313"
---
# <span data-ttu-id="2ab27-103">Set-Content</span><span class="sxs-lookup"><span data-stu-id="2ab27-103">Set-Content</span></span>

## <span data-ttu-id="2ab27-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="2ab27-104">SYNOPSIS</span></span>
<span data-ttu-id="2ab27-105">Skriver nytt innehåll eller ersätter befintligt innehåll i en fil.</span><span class="sxs-lookup"><span data-stu-id="2ab27-105">Writes new content or replaces existing content in a file.</span></span>

## <span data-ttu-id="2ab27-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2ab27-106">SYNTAX</span></span>

### <span data-ttu-id="2ab27-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="2ab27-107">Path (Default)</span></span>

```
Set-Content [-Path] <string[]> [-Value] <Object[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>]
 [-WhatIf] [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

### <span data-ttu-id="2ab27-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="2ab27-108">LiteralPath</span></span>

```
Set-Content [-Value] <Object[]> -LiteralPath <string[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>]
 [-WhatIf] [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

## <span data-ttu-id="2ab27-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="2ab27-109">DESCRIPTION</span></span>

<span data-ttu-id="2ab27-110">`Set-Content` är en sträng bearbetnings-cmdlet som skriver nytt innehåll eller ersätter innehållet i en fil.</span><span class="sxs-lookup"><span data-stu-id="2ab27-110">`Set-Content` is a string-processing cmdlet that writes new content or replaces the content in a file.</span></span> <span data-ttu-id="2ab27-111">`Set-Content` ersätter det befintliga innehållet och skiljer sig från den `Add-Content` cmdlet som lägger till innehåll i en fil.</span><span class="sxs-lookup"><span data-stu-id="2ab27-111">`Set-Content` replaces the existing content and differs from the `Add-Content` cmdlet that appends content to a file.</span></span> <span data-ttu-id="2ab27-112">Om du vill skicka innehåll till `Set-Content` kan du använda parametern **Value** på kommando raden eller skicka innehåll via pipelinen.</span><span class="sxs-lookup"><span data-stu-id="2ab27-112">To send content to `Set-Content` you can use the **Value** parameter on the command line or send content through the pipeline.</span></span>

<span data-ttu-id="2ab27-113">Om du behöver skapa filer eller kataloger för följande exempel, se [New-item](New-Item.md).</span><span class="sxs-lookup"><span data-stu-id="2ab27-113">If you need to create files or directories for the following examples, see [New-Item](New-Item.md).</span></span>

## <span data-ttu-id="2ab27-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="2ab27-114">EXAMPLES</span></span>

### <span data-ttu-id="2ab27-115">Exempel 1: Ersätt innehållet i flera filer i en katalog</span><span class="sxs-lookup"><span data-stu-id="2ab27-115">Example 1: Replace the contents of multiple files in a directory</span></span>

<span data-ttu-id="2ab27-116">I det här exemplet ersätts innehållet för flera filer i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="2ab27-116">This example replaces the content for multiple files in the current directory.</span></span>

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

<span data-ttu-id="2ab27-117">`Get-ChildItem`Cmdleten använder **Sök vägs** parametern för att visa **. txt** -filer som börjar med `Test*` i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="2ab27-117">The `Get-ChildItem` cmdlet uses the **Path** parameter to list **.txt** files that begin with `Test*` in the current directory.</span></span> <span data-ttu-id="2ab27-118">`Set-Content`Cmdleten använder parametern **Path** för att ange `Test*.txt` filerna.</span><span class="sxs-lookup"><span data-stu-id="2ab27-118">The `Set-Content` cmdlet uses the **Path** parameter to specify the `Test*.txt` files.</span></span> <span data-ttu-id="2ab27-119">Parametern **Value** innehåller text strängen **Hello, World** som ersätter det befintliga innehållet i varje fil.</span><span class="sxs-lookup"><span data-stu-id="2ab27-119">The **Value** parameter provides the text string **Hello, World** that replaces the existing content in each file.</span></span> <span data-ttu-id="2ab27-120">`Get-Content`Cmdleten använder parametern **Path** för att ange `Test*.txt` filerna och visar varje fils innehåll i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="2ab27-120">The `Get-Content` cmdlet uses the **Path** parameter to specify the `Test*.txt` files and displays each file's content in the PowerShell console.</span></span>

### <span data-ttu-id="2ab27-121">Exempel 2: skapa en ny fil och skriv innehåll</span><span class="sxs-lookup"><span data-stu-id="2ab27-121">Example 2: Create a new file and write content</span></span>

<span data-ttu-id="2ab27-122">Det här exemplet skapar en ny fil och skriver aktuellt datum och tid till filen.</span><span class="sxs-lookup"><span data-stu-id="2ab27-122">This example creates a new file and writes the current date and time to the file.</span></span>

```powershell
Set-Content -Path .\DateTime.txt -Value (Get-Date)
Get-Content -Path .\DateTime.txt
```

```Output
1/30/2019 09:55:08
```

<span data-ttu-id="2ab27-123">`Set-Content` använder parametrarna **sökväg** och **värde** för att skapa en ny fil med namnet **DateTime.txt** i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="2ab27-123">`Set-Content` uses the **Path** and **Value** parameters to create a new file named **DateTime.txt** in the current directory.</span></span> <span data-ttu-id="2ab27-124">**Värde** parametern använder `Get-Date` för att hämta aktuellt datum och aktuell tid.</span><span class="sxs-lookup"><span data-stu-id="2ab27-124">The **Value** parameter uses `Get-Date` to get the current date and time.</span></span>
<span data-ttu-id="2ab27-125">`Set-Content` skriver **datetime** -objektet till filen som en sträng.</span><span class="sxs-lookup"><span data-stu-id="2ab27-125">`Set-Content` writes the **DateTime** object to the file as a string.</span></span> <span data-ttu-id="2ab27-126">`Get-Content`Cmdleten använder parametern **Path** för att visa innehållet i **DateTime.txt** i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="2ab27-126">The `Get-Content` cmdlet uses the **Path** parameter to display the content of **DateTime.txt** in the PowerShell console.</span></span>

### <span data-ttu-id="2ab27-127">Exempel 3: ersätt text i en fil</span><span class="sxs-lookup"><span data-stu-id="2ab27-127">Example 3: Replace text in a file</span></span>

<span data-ttu-id="2ab27-128">Det här kommandot ersätter alla instanser av Word i en befintlig fil.</span><span class="sxs-lookup"><span data-stu-id="2ab27-128">This command replaces all instances of word within an existing file.</span></span>

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

<span data-ttu-id="2ab27-129">`Get-Content`Cmdleten använder parametern **Path** för att ange **Notice.txt** filen i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="2ab27-129">The `Get-Content` cmdlet uses the **Path** parameter to specify the **Notice.txt** file in the current directory.</span></span> <span data-ttu-id="2ab27-130">`Get-Content`Kommandot omges av parenteser så att kommandot slutförs innan det skickas ned pipelinen.</span><span class="sxs-lookup"><span data-stu-id="2ab27-130">The `Get-Content` command is wrapped with parentheses so that the command finishes before being sent down the pipeline.</span></span>

<span data-ttu-id="2ab27-131">Innehållet i **Notice.txt** -filen skickas ned pipelinen till `ForEach-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2ab27-131">The contents of the **Notice.txt** file are sent down the pipeline to the `ForEach-Object` cmdlet.</span></span>
<span data-ttu-id="2ab27-132">`ForEach-Object` använder den automatiska variabeln `$_` och ersätter varje förekomst av **Varning** med **försiktighet**.</span><span class="sxs-lookup"><span data-stu-id="2ab27-132">`ForEach-Object` uses the automatic variable `$_` and replaces each occurrence of **Warning** with **Caution**.</span></span> <span data-ttu-id="2ab27-133">Objekten skickas ned pipelinen till `Set-Content` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2ab27-133">The objects are sent down the pipeline to the `Set-Content` cmdlet.</span></span> <span data-ttu-id="2ab27-134">`Set-Content` använder parametern **Path** för att ange **Notice.txt** -filen och skriver det uppdaterade innehållet till filen.</span><span class="sxs-lookup"><span data-stu-id="2ab27-134">`Set-Content` uses the **Path** parameter to specify the **Notice.txt** file and writes the updated content to the file.</span></span>

<span data-ttu-id="2ab27-135">Den sista `Get-Content` cmdleten visar det uppdaterade fil innehållet i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="2ab27-135">The last `Get-Content` cmdlet displays the updated file content in the PowerShell console.</span></span>

### <span data-ttu-id="2ab27-136">Exempel 4: använda filter med Set-Content</span><span class="sxs-lookup"><span data-stu-id="2ab27-136">Example 4: Use Filters with Set-Content</span></span>

<span data-ttu-id="2ab27-137">Du kan ange ett filter för `Set-Content` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2ab27-137">You can specify a filter to the `Set-Content` cmdlet.</span></span> <span data-ttu-id="2ab27-138">När du använder filter för att kvalificera **Sök vägs** parametern måste du inkludera en efterföljande asterisk ( `*` ) för att ange innehållet i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="2ab27-138">When using filters to qualify the **Path** parameter, you need to include a trailing asterisk (`*`) to indicate the contents of the path.</span></span>

<span data-ttu-id="2ab27-139">Följande kommando anger innehållet `*.txt` för alla filer i `C:\Temp` katalogen till **värdet** Empty.</span><span class="sxs-lookup"><span data-stu-id="2ab27-139">The following command set the content all `*.txt` files in the `C:\Temp` directory to the **Value** empty.</span></span>

```powershell
Set-Content -Path C:\Temp\* -Filter *.txt -Value "Empty"
```

## <span data-ttu-id="2ab27-140">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="2ab27-140">PARAMETERS</span></span>

### <span data-ttu-id="2ab27-141">-AsByteStream</span><span class="sxs-lookup"><span data-stu-id="2ab27-141">-AsByteStream</span></span>

<span data-ttu-id="2ab27-142">Anger att innehållet ska läsas som en data ström med byte.</span><span class="sxs-lookup"><span data-stu-id="2ab27-142">Specifies that the content should be read as a stream of bytes.</span></span> <span data-ttu-id="2ab27-143">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="2ab27-143">This parameter was introduced in PowerShell 6.0.</span></span>

<span data-ttu-id="2ab27-144">En varning inträffar när du använder parametern **AsByteStream** med parametern **encoding** .</span><span class="sxs-lookup"><span data-stu-id="2ab27-144">A warning occurs when you use the **AsByteStream** parameter with the **Encoding** parameter.</span></span> <span data-ttu-id="2ab27-145">Parametern **AsByteStream** ignorerar all kodning och utdata returneras som en data ström med byte.</span><span class="sxs-lookup"><span data-stu-id="2ab27-145">The **AsByteStream** parameter ignores any encoding and the output is returned as a stream of bytes.</span></span>

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

### <span data-ttu-id="2ab27-146">-Credential</span><span class="sxs-lookup"><span data-stu-id="2ab27-146">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="2ab27-147">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2ab27-147">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="2ab27-148">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="2ab27-148">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="2ab27-149">-Encoding</span><span class="sxs-lookup"><span data-stu-id="2ab27-149">-Encoding</span></span>

<span data-ttu-id="2ab27-150">Anger typ av kodning för mål filen.</span><span class="sxs-lookup"><span data-stu-id="2ab27-150">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="2ab27-151">Standardvärdet är `utf8NoBOM`.</span><span class="sxs-lookup"><span data-stu-id="2ab27-151">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="2ab27-152">Encoding är en dynamisk parameter som fil Systems leverantören lägger till i `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="2ab27-152">Encoding is a dynamic parameter that the FileSystem provider adds to `Set-Content`.</span></span> <span data-ttu-id="2ab27-153">Den här parametern fungerar bara i fil system enheter.</span><span class="sxs-lookup"><span data-stu-id="2ab27-153">This parameter works only in file system drives.</span></span>

<span data-ttu-id="2ab27-154">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="2ab27-154">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="2ab27-155">`ascii`: Använder kodningen för ASCII-teckenuppsättningen (7 bitar).</span><span class="sxs-lookup"><span data-stu-id="2ab27-155">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="2ab27-156">`bigendianunicode`: Kodar i UTF-16-format med big-endian byte-ordning.</span><span class="sxs-lookup"><span data-stu-id="2ab27-156">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="2ab27-157">`bigendianutf32`: Kodar i UTF-32-format med big-endian-dataordningen.</span><span class="sxs-lookup"><span data-stu-id="2ab27-157">`bigendianutf32`: Encodes in UTF-32 format using the big-endian byte order.</span></span>
- <span data-ttu-id="2ab27-158">`oem`: Använder standard kodning för MS-DOS-och-konsol program.</span><span class="sxs-lookup"><span data-stu-id="2ab27-158">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="2ab27-159">`unicode`: Kodar i UTF-16-format med lite-endian-dataordning.</span><span class="sxs-lookup"><span data-stu-id="2ab27-159">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="2ab27-160">`utf7`: Kodar i UTF-7-format.</span><span class="sxs-lookup"><span data-stu-id="2ab27-160">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="2ab27-161">`utf8`: Kodar i UTF-8-format.</span><span class="sxs-lookup"><span data-stu-id="2ab27-161">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="2ab27-162">`utf8BOM`: Kodar i UTF-8-format med byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="2ab27-162">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="2ab27-163">`utf8NoBOM`: Kodar i UTF-8-format utan byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="2ab27-163">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="2ab27-164">`utf32`: Kodar i UTF-32-format.</span><span class="sxs-lookup"><span data-stu-id="2ab27-164">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="2ab27-165">Från och med PowerShell 6,2 tillåter **encoding** -parametern även numeriska ID: n för registrerade tecken tabeller (som `-Encoding 1251` ) eller sträng namn för registrerade tecken tabeller (som `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="2ab27-165">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="2ab27-166">Mer information finns i .NET-dokumentationen för [encoding. codepage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span><span class="sxs-lookup"><span data-stu-id="2ab27-166">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

> [!NOTE]
> <span data-ttu-id="2ab27-167">**UTF-7** \* rekommenderas inte längre att använda.</span><span class="sxs-lookup"><span data-stu-id="2ab27-167">**UTF-7** \* is no longer recommended to use.</span></span> <span data-ttu-id="2ab27-168">I PowerShell 7,1 skrivs en varning om du anger `utf7` för **kodnings** parametern.</span><span class="sxs-lookup"><span data-stu-id="2ab27-168">In PowerShell 7.1, a warning is written if you specify `utf7` for the **Encoding** parameter.</span></span>

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

### <span data-ttu-id="2ab27-169">-Undanta</span><span class="sxs-lookup"><span data-stu-id="2ab27-169">-Exclude</span></span>

<span data-ttu-id="2ab27-170">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="2ab27-170">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="2ab27-171">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="2ab27-171">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="2ab27-172">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="2ab27-172">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="2ab27-173">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="2ab27-173">Wildcard characters are permitted.</span></span> <span data-ttu-id="2ab27-174">Parametern **exclude** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="2ab27-174">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="2ab27-175">-Filter</span><span class="sxs-lookup"><span data-stu-id="2ab27-175">-Filter</span></span>

<span data-ttu-id="2ab27-176">Anger ett filter för att kvalificera **Sök vägs** parametern.</span><span class="sxs-lookup"><span data-stu-id="2ab27-176">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="2ab27-177">[Fil Systems](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) leverantören är den enda installerade PowerShell-providern som stöder användningen av filter.</span><span class="sxs-lookup"><span data-stu-id="2ab27-177">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="2ab27-178">Du kan hitta syntaxen för filter språket för **fil systemet** i [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="2ab27-178">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="2ab27-179">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="2ab27-179">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="2ab27-180">-Force</span><span class="sxs-lookup"><span data-stu-id="2ab27-180">-Force</span></span>

<span data-ttu-id="2ab27-181">Tvingar cmdleten att ange innehållet i en fil, även om filen är skrivskyddad.</span><span class="sxs-lookup"><span data-stu-id="2ab27-181">Forces the cmdlet to set the contents of a file, even if the file is read-only.</span></span> <span data-ttu-id="2ab27-182">Implementeringen varierar från providern till providern.</span><span class="sxs-lookup"><span data-stu-id="2ab27-182">Implementation varies from provider to provider.</span></span> <span data-ttu-id="2ab27-183">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="2ab27-183">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
<span data-ttu-id="2ab27-184">**Force** -parametern åsidosätter inte säkerhets begränsningar.</span><span class="sxs-lookup"><span data-stu-id="2ab27-184">The **Force** parameter does not override security restrictions.</span></span>

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

### <span data-ttu-id="2ab27-185">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="2ab27-185">-Include</span></span>

<span data-ttu-id="2ab27-186">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="2ab27-186">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="2ab27-187">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="2ab27-187">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="2ab27-188">Ange ett Sök vägs element eller ett mönster, till exempel `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="2ab27-188">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="2ab27-189">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="2ab27-189">Wildcard characters are permitted.</span></span> <span data-ttu-id="2ab27-190">Parametern **include** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="2ab27-190">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="2ab27-191">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="2ab27-191">-LiteralPath</span></span>

<span data-ttu-id="2ab27-192">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="2ab27-192">Specifies a path to one or more locations.</span></span> <span data-ttu-id="2ab27-193">Värdet för **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="2ab27-193">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="2ab27-194">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="2ab27-194">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="2ab27-195">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="2ab27-195">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="2ab27-196">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="2ab27-196">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="2ab27-197">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="2ab27-197">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="2ab27-198">– NoNewline</span><span class="sxs-lookup"><span data-stu-id="2ab27-198">-NoNewline</span></span>

<span data-ttu-id="2ab27-199">Sträng representationerna av indata-objekten sammanfogas för att bilda utdata.</span><span class="sxs-lookup"><span data-stu-id="2ab27-199">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="2ab27-200">Inga blank steg eller newlines infogas mellan utgående strängar.</span><span class="sxs-lookup"><span data-stu-id="2ab27-200">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="2ab27-201">Ingen ny rad läggs till efter den sista utgående strängen.</span><span class="sxs-lookup"><span data-stu-id="2ab27-201">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="2ab27-202">– PassThru</span><span class="sxs-lookup"><span data-stu-id="2ab27-202">-PassThru</span></span>

<span data-ttu-id="2ab27-203">Returnerar ett objekt som representerar innehållet.</span><span class="sxs-lookup"><span data-stu-id="2ab27-203">Returns an object that represents the content.</span></span> <span data-ttu-id="2ab27-204">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="2ab27-204">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="2ab27-205">-Path</span><span class="sxs-lookup"><span data-stu-id="2ab27-205">-Path</span></span>

<span data-ttu-id="2ab27-206">Anger sökvägen till det objekt som tar emot innehållet.</span><span class="sxs-lookup"><span data-stu-id="2ab27-206">Specifies the path of the item that receives the content.</span></span>
<span data-ttu-id="2ab27-207">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="2ab27-207">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="2ab27-208">-Stream</span><span class="sxs-lookup"><span data-stu-id="2ab27-208">-Stream</span></span>

<span data-ttu-id="2ab27-209">Anger en alternativ data ström för innehåll.</span><span class="sxs-lookup"><span data-stu-id="2ab27-209">Specifies an alternative data stream for content.</span></span> <span data-ttu-id="2ab27-210">Om data strömmen inte finns skapar den här cmdleten den.</span><span class="sxs-lookup"><span data-stu-id="2ab27-210">If the stream does not exist, this cmdlet creates it.</span></span> <span data-ttu-id="2ab27-211">Jokertecken stöds inte.</span><span class="sxs-lookup"><span data-stu-id="2ab27-211">Wildcard characters are not supported.</span></span>

<span data-ttu-id="2ab27-212">**Stream** är en dynamisk parameter som **fil Systems** leverantören lägger till i `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="2ab27-212">**Stream** is a dynamic parameter that the **FileSystem** provider adds to `Set-Content`.</span></span> <span data-ttu-id="2ab27-213">Den här parametern fungerar bara i fil system enheter.</span><span class="sxs-lookup"><span data-stu-id="2ab27-213">This parameter works only in file system drives.</span></span>

<span data-ttu-id="2ab27-214">Du kan använda `Set-Content` cmdleten för att ändra innehållet i **zonen. unik identifierare** för den alternativa data strömmen.</span><span class="sxs-lookup"><span data-stu-id="2ab27-214">You can use the `Set-Content` cmdlet to change the content of the **Zone.Identifier** alternate data stream.</span></span> <span data-ttu-id="2ab27-215">Vi rekommenderar dock inte detta som ett sätt att eliminera säkerhets kontroller som blockerar filer som hämtas från Internet.</span><span class="sxs-lookup"><span data-stu-id="2ab27-215">However, we do not recommend this as a way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="2ab27-216">Om du verifierar att en Hämtad fil är säker använder du `Unblock-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2ab27-216">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="2ab27-217">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="2ab27-217">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="2ab27-218">-Värde</span><span class="sxs-lookup"><span data-stu-id="2ab27-218">-Value</span></span>

<span data-ttu-id="2ab27-219">Anger det nya innehållet för objektet.</span><span class="sxs-lookup"><span data-stu-id="2ab27-219">Specifies the new content for the item.</span></span>

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

### <span data-ttu-id="2ab27-220">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2ab27-220">-Confirm</span></span>

<span data-ttu-id="2ab27-221">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2ab27-221">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="2ab27-222">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2ab27-222">-WhatIf</span></span>

<span data-ttu-id="2ab27-223">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="2ab27-223">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="2ab27-224">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="2ab27-224">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="2ab27-225">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2ab27-225">CommonParameters</span></span>

<span data-ttu-id="2ab27-226">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="2ab27-226">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span>
<span data-ttu-id="2ab27-227">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="2ab27-227">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="2ab27-228">INDATA</span><span class="sxs-lookup"><span data-stu-id="2ab27-228">INPUTS</span></span>

### <span data-ttu-id="2ab27-229">System. Object</span><span class="sxs-lookup"><span data-stu-id="2ab27-229">System.Object</span></span>

<span data-ttu-id="2ab27-230">Du kan skicka en pipe till ett objekt som innehåller det nya värdet för objektet `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="2ab27-230">You can pipe an object that contains the new value for the item to `Set-Content`.</span></span>

## <span data-ttu-id="2ab27-231">UTDATA</span><span class="sxs-lookup"><span data-stu-id="2ab27-231">OUTPUTS</span></span>

### <span data-ttu-id="2ab27-232">Ingen eller system. String</span><span class="sxs-lookup"><span data-stu-id="2ab27-232">None or System.String</span></span>

<span data-ttu-id="2ab27-233">När du använder parametern **Passthru** `Set-Content` genererar ett **system. String** -objekt som representerar innehållet.</span><span class="sxs-lookup"><span data-stu-id="2ab27-233">When you use the **PassThru** parameter, `Set-Content` generates a **System.String** object that represents the content.</span></span> <span data-ttu-id="2ab27-234">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="2ab27-234">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="2ab27-235">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="2ab27-235">NOTES</span></span>

- <span data-ttu-id="2ab27-236">Du kan också referera till `Set-Content` med dess inbyggda alias `sc` .</span><span class="sxs-lookup"><span data-stu-id="2ab27-236">You can also refer to `Set-Content` by its built-in alias, `sc`.</span></span>
  <span data-ttu-id="2ab27-237">Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="2ab27-237">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="2ab27-238">`Set-Content` är utformad för sträng bearbetning.</span><span class="sxs-lookup"><span data-stu-id="2ab27-238">`Set-Content` is designed for string processing.</span></span> <span data-ttu-id="2ab27-239">Om du rör icke-sträng objekt till `Set-Content` konverteras objektet till en sträng innan det skrivs.</span><span class="sxs-lookup"><span data-stu-id="2ab27-239">If you pipe non-string objects to `Set-Content`, it converts the object to a string before writing it.</span></span> <span data-ttu-id="2ab27-240">Använd om du vill skriva objekt till filer `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="2ab27-240">To write objects to files, use `Out-File`.</span></span>
- <span data-ttu-id="2ab27-241">`Set-Content`Cmdleten är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="2ab27-241">The `Set-Content` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="2ab27-242">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="2ab27-242">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="2ab27-243">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="2ab27-243">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="2ab27-244">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="2ab27-244">RELATED LINKS</span></span>

[<span data-ttu-id="2ab27-245">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="2ab27-245">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="2ab27-246">about_Automatic_Variables. MD</span><span class="sxs-lookup"><span data-stu-id="2ab27-246">about_Automatic_Variables.md</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="2ab27-247">about_Providers</span><span class="sxs-lookup"><span data-stu-id="2ab27-247">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="2ab27-248">Lägg till innehåll</span><span class="sxs-lookup"><span data-stu-id="2ab27-248">Add-Content</span></span>](Add-Content.md)

[<span data-ttu-id="2ab27-249">Rensa innehåll</span><span class="sxs-lookup"><span data-stu-id="2ab27-249">Clear-Content</span></span>](Clear-Content.md)

[<span data-ttu-id="2ab27-250">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="2ab27-250">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="2ab27-251">Hämta innehåll</span><span class="sxs-lookup"><span data-stu-id="2ab27-251">Get-Content</span></span>](Get-Content.md)

[<span data-ttu-id="2ab27-252">-Objekt</span><span class="sxs-lookup"><span data-stu-id="2ab27-252">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="2ab27-253">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="2ab27-253">New-Item</span></span>](New-Item.md)

