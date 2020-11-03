---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/add-content?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-Content
ms.openlocfilehash: 291ec8f3a3958aa726fafb8032b996296272a21e
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264015"
---
# <span data-ttu-id="eaa57-103">Add-Content</span><span class="sxs-lookup"><span data-stu-id="eaa57-103">Add-Content</span></span>

## <span data-ttu-id="eaa57-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="eaa57-104">SYNOPSIS</span></span>
<span data-ttu-id="eaa57-105">Lägger till innehåll till de angivna objekten, till exempel att lägga till ord i en fil.</span><span class="sxs-lookup"><span data-stu-id="eaa57-105">Adds content to the specified items, such as adding words to a file.</span></span>

## <span data-ttu-id="eaa57-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="eaa57-106">SYNTAX</span></span>

### <span data-ttu-id="eaa57-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="eaa57-107">Path (Default)</span></span>

```
Add-Content [-Path] <string[]> [-Value] <Object[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

### <span data-ttu-id="eaa57-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="eaa57-108">LiteralPath</span></span>

```
Add-Content [-Value] <Object[]> -LiteralPath <string[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-NoNewline] [-Encoding <Encoding>] [-AsByteStream] [-Stream <string>]
 [<CommonParameters>]
```

## <span data-ttu-id="eaa57-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="eaa57-109">DESCRIPTION</span></span>

<span data-ttu-id="eaa57-110">`Add-Content`Cmdleten lägger till innehåll i ett angivet objekt eller en angiven fil.</span><span class="sxs-lookup"><span data-stu-id="eaa57-110">The `Add-Content` cmdlet appends content to a specified item or file.</span></span> <span data-ttu-id="eaa57-111">Du kan ange innehållet genom att skriva innehållet i kommandot eller genom att ange ett objekt som innehåller innehållet.</span><span class="sxs-lookup"><span data-stu-id="eaa57-111">You can specify the content by typing the content in the command or by specifying an object that contains the content.</span></span>

<span data-ttu-id="eaa57-112">Om du behöver skapa filer eller kataloger för följande exempel, se [New-item](New-Item.md).</span><span class="sxs-lookup"><span data-stu-id="eaa57-112">If you need to create files or directories for the following examples, see [New-Item](New-Item.md).</span></span>

## <span data-ttu-id="eaa57-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="eaa57-113">EXAMPLES</span></span>

### <span data-ttu-id="eaa57-114">Exempel 1: Lägg till en sträng till alla textfiler med ett undantag</span><span class="sxs-lookup"><span data-stu-id="eaa57-114">Example 1: Add a string to all text files with an exception</span></span>

<span data-ttu-id="eaa57-115">I det här exemplet läggs ett värde till i textfiler i den aktuella katalogen, men filer som är baserade på fil namnet exkluderas.</span><span class="sxs-lookup"><span data-stu-id="eaa57-115">This example appends a value to text files in the current directory but excludes files based on their file name.</span></span>

```powershell
Add-Content -Path .\*.txt -Exclude help* -Value 'End of file'
```

<span data-ttu-id="eaa57-116">Parametern **Path** anger alla `.txt` filer i den aktuella katalogen, men parametern **exclude** ignorerar fil namn som matchar det angivna mönstret.</span><span class="sxs-lookup"><span data-stu-id="eaa57-116">The **Path** parameter specifies all `.txt` files in the current directory, but the **Exclude** parameter ignores file names that match the specified pattern.</span></span> <span data-ttu-id="eaa57-117">Parametern **Value** anger text strängen som skrivs till filerna.</span><span class="sxs-lookup"><span data-stu-id="eaa57-117">The **Value** parameter specifies the text string that is written to the files.</span></span>

### <span data-ttu-id="eaa57-118">Exempel 2: Lägg till ett datum i slutet av de angivna filerna</span><span class="sxs-lookup"><span data-stu-id="eaa57-118">Example 2: Add a date to the end of the specified files</span></span>

<span data-ttu-id="eaa57-119">I det här exemplet läggs datumet till i den aktuella katalogen och datumet visas i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="eaa57-119">This example appends the date to files in the current directory and displays the date in the PowerShell console.</span></span>

```powershell
Add-Content -Path .\DateTimeFile1.log, .\DateTimeFile2.log -Value (Get-Date) -PassThru
Get-Content -Path .\DateTimeFile1.log
```

```Output
Tuesday, May 14, 2019 8:24:27 AM
Tuesday, May 14, 2019 8:24:27 AM
5/14/2019 8:24:27 AM
```

<span data-ttu-id="eaa57-120">`Add-Content`Cmdleten skapar två nya filer i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="eaa57-120">The `Add-Content` cmdlet creates two new files in the current directory.</span></span> <span data-ttu-id="eaa57-121">Parametern **Value** innehåller utdata från `Get-Date` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="eaa57-121">The **Value** parameter contains the output of the `Get-Date` cmdlet.</span></span> <span data-ttu-id="eaa57-122">Parametern **Passthru** matar ut det tillagda innehållet i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="eaa57-122">The **PassThru** parameter outputs the added contents to the pipeline.</span></span>
<span data-ttu-id="eaa57-123">Eftersom det inte finns någon annan cmdlet för att ta emot utdata visas den i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="eaa57-123">Because there is no other cmdlet to receive the output, it is displayed in the PowerShell console.</span></span>
<span data-ttu-id="eaa57-124">`Get-Content`Cmdleten visar den uppdaterade filen `DateTimeFile1.log` .</span><span class="sxs-lookup"><span data-stu-id="eaa57-124">The `Get-Content` cmdlet displays the updated file, `DateTimeFile1.log`.</span></span>

### <span data-ttu-id="eaa57-125">Exempel 3: lägga till innehållet i en angiven fil till en annan fil</span><span class="sxs-lookup"><span data-stu-id="eaa57-125">Example 3: Add the contents of a specified file to another file</span></span>

<span data-ttu-id="eaa57-126">Det här exemplet hämtar innehållet från en fil och lagrar innehållet i en variabel.</span><span class="sxs-lookup"><span data-stu-id="eaa57-126">This example gets the content from a file and stores the content in a variable.</span></span> <span data-ttu-id="eaa57-127">Variabeln används för att lägga till innehållet i en annan fil.</span><span class="sxs-lookup"><span data-stu-id="eaa57-127">The variable is used to append the content into another file.</span></span>

```powershell
$From = Get-Content -Path .\CopyFromFile.txt
Add-Content -Path .\CopyToFile.txt -Value $From
Get-Content -Path .\CopyToFile.txt
```

- <span data-ttu-id="eaa57-128">`Get-Content`Cmdleten hämtar innehållet `CopyFromFile.txt` i och lagrar innehållet i `$From` variabeln.</span><span class="sxs-lookup"><span data-stu-id="eaa57-128">The `Get-Content` cmdlet gets the contents of `CopyFromFile.txt` and stores the contents in the `$From` variable.</span></span>
- <span data-ttu-id="eaa57-129">`Add-Content`Cmdleten uppdaterar `CopyToFile.txt` filen med hjälp av innehållet i `$From` variabeln.</span><span class="sxs-lookup"><span data-stu-id="eaa57-129">The `Add-Content` cmdlet updates the `CopyToFile.txt` file using the contents of the `$From` variable.</span></span>
- <span data-ttu-id="eaa57-130">`Get-Content`Cmdleten visar CopyToFile.txt.</span><span class="sxs-lookup"><span data-stu-id="eaa57-130">The `Get-Content` cmdlet displays CopyToFile.txt.</span></span>

### <span data-ttu-id="eaa57-131">Exempel 4: Lägg till innehållet i en angiven fil till en annan fil med pipelinen</span><span class="sxs-lookup"><span data-stu-id="eaa57-131">Example 4: Add the contents of a specified file to another file using the pipeline</span></span>

<span data-ttu-id="eaa57-132">Det här exemplet hämtar innehållet från en fil och rör den till `Add-Content` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="eaa57-132">This example gets the content from a file and pipes it to the `Add-Content` cmdlet.</span></span>

```powershell
Get-Content -Path .\CopyFromFile.txt | Add-Content -Path .\CopyToFile.txt
Get-Content -Path .\CopyToFile.txt
```

<span data-ttu-id="eaa57-133">`Get-Content`Cmdlet: en hämtar innehållet i `CopyFromFile.txt` .</span><span class="sxs-lookup"><span data-stu-id="eaa57-133">The `Get-Content` cmdlet gets the contents of `CopyFromFile.txt`.</span></span> <span data-ttu-id="eaa57-134">Resultaten är skickas till `Add-Content` cmdleten, som uppdaterar `CopyToFile.txt` .</span><span class="sxs-lookup"><span data-stu-id="eaa57-134">The results are piped to the `Add-Content` cmdlet, which updates the `CopyToFile.txt`.</span></span>
<span data-ttu-id="eaa57-135">Den sista `Get-Content` cmdleten visas `CopyToFile.txt` .</span><span class="sxs-lookup"><span data-stu-id="eaa57-135">The last `Get-Content` cmdlet displays `CopyToFile.txt`.</span></span>

### <span data-ttu-id="eaa57-136">Exempel 5: skapa en ny fil och kopiera innehåll</span><span class="sxs-lookup"><span data-stu-id="eaa57-136">Example 5: Create a new file and copy content</span></span>

<span data-ttu-id="eaa57-137">Det här exemplet skapar en ny fil och kopierar en befintlig fils innehåll till den nya filen.</span><span class="sxs-lookup"><span data-stu-id="eaa57-137">This example creates a new file and copies an existing file's content into the new file.</span></span>

```powershell
Add-Content -Path .\NewFile.txt -Value (Get-Content -Path .\CopyFromFile.txt)
Get-Content -Path .\NewFile.txt
```

- <span data-ttu-id="eaa57-138">`Add-Content`Cmdleten använder **sökvägen** och **värde** parametrarna för att skapa en ny fil i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="eaa57-138">The `Add-Content` cmdlet uses the **Path** and **Value** parameters to create a new file in the current directory.</span></span>
- <span data-ttu-id="eaa57-139">`Get-Content`Cmdlet: en hämtar innehållet i en befintlig fil `CopyFromFile.txt` och skickar den till **värde** parametern.</span><span class="sxs-lookup"><span data-stu-id="eaa57-139">The `Get-Content` cmdlet gets the contents of an existing file, `CopyFromFile.txt` and passes it to the **Value** parameter.</span></span> <span data-ttu-id="eaa57-140">Parenteserna runt `Get-Content` cmdleten ser till att kommandot slutförs innan `Add-Content` kommandot börjar.</span><span class="sxs-lookup"><span data-stu-id="eaa57-140">The parentheses around the `Get-Content` cmdlet ensure that the command finishes before the `Add-Content` command begins.</span></span>
- <span data-ttu-id="eaa57-141">`Get-Content`Cmdleten visar innehållet i den nya filen `NewFile.txt` .</span><span class="sxs-lookup"><span data-stu-id="eaa57-141">The `Get-Content` cmdlet displays the contents of the new file, `NewFile.txt`.</span></span>

### <span data-ttu-id="eaa57-142">Exempel 6: Lägg till innehåll i en skrivskyddad fil</span><span class="sxs-lookup"><span data-stu-id="eaa57-142">Example 6: Add content to a read-only file</span></span>

<span data-ttu-id="eaa57-143">Det här kommandot lägger till ett värde till filen även om Filattributet **IsReadOnly** har angetts till **True**.</span><span class="sxs-lookup"><span data-stu-id="eaa57-143">This command adds a value to the file even if the **IsReadOnly** file attribute is set to **True**.</span></span>
<span data-ttu-id="eaa57-144">Stegen för att skapa en skrivskyddad fil ingår i exemplet.</span><span class="sxs-lookup"><span data-stu-id="eaa57-144">The steps to create a read-only file are included in the example.</span></span>

```powershell
New-Item -Path .\IsReadOnlyTextFile.txt -ItemType File
Set-ItemProperty -Path .\IsReadOnlyTextFile.txt -Name IsReadOnly -Value $True
Get-ChildItem -Path .\IsReadOnlyTextFile.txt
Add-Content -Path .\IsReadOnlyTextFile.txt -Value 'Add value to read-only text file' -Force
Get-Content -Path .\IsReadOnlyTextFile.txt
```

```Output
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-ar--         1/28/2019     13:35              0 IsReadOnlyTextFile.txt
```

- <span data-ttu-id="eaa57-145">`New-Item`Cmdleten använder parametrarna **Path** och **itemType** för att skapa filen `IsReadOnlyTextFile.txt` i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="eaa57-145">The `New-Item` cmdlet uses the **Path** and **ItemType** parameters to create the file `IsReadOnlyTextFile.txt` in the current directory.</span></span>
- <span data-ttu-id="eaa57-146">`Set-ItemProperty`Cmdleten använder **namn** -och **värde** parametrarna för att ändra filens **IsReadOnly** -egenskap till true.</span><span class="sxs-lookup"><span data-stu-id="eaa57-146">The `Set-ItemProperty` cmdlet uses the **Name** and **Value** parameters to change the file's **IsReadOnly** property to True.</span></span>
- <span data-ttu-id="eaa57-147">`Get-ChildItem`Cmdleten visar att filen är tom (0) och har attributet skrivskyddad ( `r` ).</span><span class="sxs-lookup"><span data-stu-id="eaa57-147">The `Get-ChildItem` cmdlet shows the file is empty (0) and has the read-only attribute (`r`).</span></span>
- <span data-ttu-id="eaa57-148">`Add-Content`Cmdleten använder parametern **Path** för att ange filen.</span><span class="sxs-lookup"><span data-stu-id="eaa57-148">The `Add-Content` cmdlet uses the **Path** parameter to specify the file.</span></span> <span data-ttu-id="eaa57-149">Parametern **Value** innehåller text strängen som ska läggas till i filen.</span><span class="sxs-lookup"><span data-stu-id="eaa57-149">The **Value** parameter includes the text string to append to the file.</span></span> <span data-ttu-id="eaa57-150">Parametern **Force** skriver texten till den skrivskyddade filen.</span><span class="sxs-lookup"><span data-stu-id="eaa57-150">The **Force** parameter writes the text to the read-only file.</span></span>
- <span data-ttu-id="eaa57-151">`Get-Content`Cmdleten använder parametern **Path** för att visa filens innehåll.</span><span class="sxs-lookup"><span data-stu-id="eaa57-151">The `Get-Content` cmdlet uses the **Path** parameter to display the file's contents.</span></span>

<span data-ttu-id="eaa57-152">Om du vill ta bort det skrivskyddade attributet använder du `Set-ItemProperty` kommandot med **värdet** parameter inställt på `False` .</span><span class="sxs-lookup"><span data-stu-id="eaa57-152">To remove the read-only attribute, use the `Set-ItemProperty` command with the **Value** parameter set to `False`.</span></span>

### <span data-ttu-id="eaa57-153">Exempel 7: använda filter med Add-Content</span><span class="sxs-lookup"><span data-stu-id="eaa57-153">Example 7: Use Filters with Add-Content</span></span>

<span data-ttu-id="eaa57-154">Du kan ange ett filter för `Add-Content` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="eaa57-154">You can specify a filter to the `Add-Content` cmdlet.</span></span> <span data-ttu-id="eaa57-155">När du använder filter för att kvalificera **Sök vägs** parametern måste du inkludera en efterföljande asterisk ( `*` ) för att ange innehållet i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="eaa57-155">When using filters to qualify the **Path** parameter, you need to include a trailing asterisk (`*`) to indicate the contents of the path.</span></span>

<span data-ttu-id="eaa57-156">Följande kommando lägger till ordet "utfört" på innehållet i alla `*.txt` filer i `C:\Temp` katalogen.</span><span class="sxs-lookup"><span data-stu-id="eaa57-156">The following command adds the word "Done" the content of all `*.txt` files in the `C:\Temp` directory.</span></span>

```powershell
Add-Content -Path C:\Temp\* -Filter *.txt -Value "Done"
```

## <span data-ttu-id="eaa57-157">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="eaa57-157">PARAMETERS</span></span>

### <span data-ttu-id="eaa57-158">-AsByteStream</span><span class="sxs-lookup"><span data-stu-id="eaa57-158">-AsByteStream</span></span>

<span data-ttu-id="eaa57-159">Anger att innehållet ska läsas som en data ström med byte.</span><span class="sxs-lookup"><span data-stu-id="eaa57-159">Specifies that the content should be read as a stream of bytes.</span></span> <span data-ttu-id="eaa57-160">Den här parametern introducerades i PowerShell 6,0.</span><span class="sxs-lookup"><span data-stu-id="eaa57-160">This parameter was introduced in PowerShell 6.0.</span></span>

<span data-ttu-id="eaa57-161">En varning inträffar när du använder parametern **AsByteStream** med parametern **encoding** .</span><span class="sxs-lookup"><span data-stu-id="eaa57-161">A warning occurs when you use the **AsByteStream** parameter with the **Encoding** parameter.</span></span> <span data-ttu-id="eaa57-162">Parametern **AsByteStream** ignorerar all kodning och utdata returneras som en data ström med byte.</span><span class="sxs-lookup"><span data-stu-id="eaa57-162">The **AsByteStream** parameter ignores any encoding and the output is returned as a stream of bytes.</span></span>

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

### <span data-ttu-id="eaa57-163">-Credential</span><span class="sxs-lookup"><span data-stu-id="eaa57-163">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="eaa57-164">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="eaa57-164">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="eaa57-165">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="eaa57-165">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="eaa57-166">-Encoding</span><span class="sxs-lookup"><span data-stu-id="eaa57-166">-Encoding</span></span>

<span data-ttu-id="eaa57-167">Anger typ av kodning för mål filen.</span><span class="sxs-lookup"><span data-stu-id="eaa57-167">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="eaa57-168">Standardvärdet är `utf8NoBOM`.</span><span class="sxs-lookup"><span data-stu-id="eaa57-168">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="eaa57-169">Encoding är en dynamisk parameter som fil Systems leverantören lägger till i `Add-Content` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="eaa57-169">Encoding is a dynamic parameter that the FileSystem provider adds to the `Add-Content` cmdlet.</span></span> <span data-ttu-id="eaa57-170">Den här parametern fungerar bara i fil system enheter.</span><span class="sxs-lookup"><span data-stu-id="eaa57-170">This parameter works only in file system drives.</span></span>

<span data-ttu-id="eaa57-171">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="eaa57-171">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="eaa57-172">`ascii`: Använder kodningen för ASCII-teckenuppsättningen (7 bitar).</span><span class="sxs-lookup"><span data-stu-id="eaa57-172">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="eaa57-173">`bigendianunicode`: Kodar i UTF-16-format med big-endian byte-ordning.</span><span class="sxs-lookup"><span data-stu-id="eaa57-173">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="eaa57-174">`oem`: Använder standard kodning för MS-DOS-och-konsol program.</span><span class="sxs-lookup"><span data-stu-id="eaa57-174">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="eaa57-175">`unicode`: Kodar i UTF-16-format med lite-endian-dataordning.</span><span class="sxs-lookup"><span data-stu-id="eaa57-175">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="eaa57-176">`utf7`: Kodar i UTF-7-format.</span><span class="sxs-lookup"><span data-stu-id="eaa57-176">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="eaa57-177">`utf8`: Kodar i UTF-8-format.</span><span class="sxs-lookup"><span data-stu-id="eaa57-177">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="eaa57-178">`utf8BOM`: Kodar i UTF-8-format med byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="eaa57-178">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="eaa57-179">`utf8NoBOM`: Kodar i UTF-8-format utan byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="eaa57-179">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="eaa57-180">`utf32`: Kodar i UTF-32-format.</span><span class="sxs-lookup"><span data-stu-id="eaa57-180">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="eaa57-181">Från och med PowerShell 6,2 tillåter **encoding** -parametern även numeriska ID: n för registrerade tecken tabeller (som `-Encoding 1251` ) eller sträng namn för registrerade tecken tabeller (som `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="eaa57-181">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="eaa57-182">Mer information finns i .NET-dokumentationen för [encoding. codepage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span><span class="sxs-lookup"><span data-stu-id="eaa57-182">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: Named
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="eaa57-183">-Undanta</span><span class="sxs-lookup"><span data-stu-id="eaa57-183">-Exclude</span></span>

<span data-ttu-id="eaa57-184">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="eaa57-184">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="eaa57-185">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="eaa57-185">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="eaa57-186">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="eaa57-186">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="eaa57-187">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="eaa57-187">Wildcard characters are permitted.</span></span> <span data-ttu-id="eaa57-188">Parametern **exclude** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="eaa57-188">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="eaa57-189">-Filter</span><span class="sxs-lookup"><span data-stu-id="eaa57-189">-Filter</span></span>

<span data-ttu-id="eaa57-190">Anger ett filter för att kvalificera **Sök vägs** parametern.</span><span class="sxs-lookup"><span data-stu-id="eaa57-190">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="eaa57-191">[Fil Systems](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) leverantören är den enda installerade PowerShell-providern som stöder användningen av filter.</span><span class="sxs-lookup"><span data-stu-id="eaa57-191">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="eaa57-192">Du kan hitta syntaxen för filter språket för **fil systemet** i [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="eaa57-192">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="eaa57-193">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="eaa57-193">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="eaa57-194">-Force</span><span class="sxs-lookup"><span data-stu-id="eaa57-194">-Force</span></span>

<span data-ttu-id="eaa57-195">Åsidosätter det skrivskyddade attributet så att du kan lägga till innehåll i en skrivskyddad fil.</span><span class="sxs-lookup"><span data-stu-id="eaa57-195">Overrides the read-only attribute, allowing you to add content to a read-only file.</span></span> <span data-ttu-id="eaa57-196">**Tvinga** åsidosätter till exempel det skrivskyddade attributet eller skapa kataloger för att slutföra en fil Sök väg, men kommer inte att försöka ändra fil behörigheter.</span><span class="sxs-lookup"><span data-stu-id="eaa57-196">For example, **Force** will override the read-only attribute or create directories to complete a file path, but it will not attempt to change file permissions.</span></span>

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

### <span data-ttu-id="eaa57-197">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="eaa57-197">-Include</span></span>

<span data-ttu-id="eaa57-198">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="eaa57-198">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="eaa57-199">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="eaa57-199">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="eaa57-200">Ange ett Sök vägs element eller ett mönster, till exempel `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="eaa57-200">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="eaa57-201">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="eaa57-201">Wildcard characters are permitted.</span></span> <span data-ttu-id="eaa57-202">Parametern **include** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="eaa57-202">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="eaa57-203">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="eaa57-203">-LiteralPath</span></span>

<span data-ttu-id="eaa57-204">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="eaa57-204">Specifies a path to one or more locations.</span></span> <span data-ttu-id="eaa57-205">Värdet för **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="eaa57-205">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="eaa57-206">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="eaa57-206">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="eaa57-207">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="eaa57-207">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="eaa57-208">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="eaa57-208">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="eaa57-209">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="eaa57-209">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="eaa57-210">– NoNewline</span><span class="sxs-lookup"><span data-stu-id="eaa57-210">-NoNewline</span></span>

<span data-ttu-id="eaa57-211">Anger att denna cmdlet inte lägger till en ny rad eller vagn retur i innehållet.</span><span class="sxs-lookup"><span data-stu-id="eaa57-211">Indicates that this cmdlet does not add a new line or carriage return to the content.</span></span>

<span data-ttu-id="eaa57-212">Sträng representationerna av indata-objekten sammanfogas för att bilda utdata.</span><span class="sxs-lookup"><span data-stu-id="eaa57-212">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="eaa57-213">Inga blank steg eller newlines infogas mellan utgående strängar.</span><span class="sxs-lookup"><span data-stu-id="eaa57-213">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="eaa57-214">Ingen ny rad läggs till efter den sista utgående strängen.</span><span class="sxs-lookup"><span data-stu-id="eaa57-214">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="eaa57-215">– PassThru</span><span class="sxs-lookup"><span data-stu-id="eaa57-215">-PassThru</span></span>

<span data-ttu-id="eaa57-216">Returnerar ett objekt som representerar det tillagda innehållet.</span><span class="sxs-lookup"><span data-stu-id="eaa57-216">Returns an object representing the added content.</span></span> <span data-ttu-id="eaa57-217">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="eaa57-217">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="eaa57-218">-Path</span><span class="sxs-lookup"><span data-stu-id="eaa57-218">-Path</span></span>

<span data-ttu-id="eaa57-219">Anger sökvägen till de objekt som tar emot det ytterligare innehållet.</span><span class="sxs-lookup"><span data-stu-id="eaa57-219">Specifies the path to the items that receive the additional content.</span></span>
<span data-ttu-id="eaa57-220">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="eaa57-220">Wildcard characters are permitted.</span></span>
<span data-ttu-id="eaa57-221">Sök vägarna måste vara sökvägar till objekt, inte behållare.</span><span class="sxs-lookup"><span data-stu-id="eaa57-221">The paths must be paths to items, not to containers.</span></span>
<span data-ttu-id="eaa57-222">Du måste till exempel ange en sökväg till en eller flera filer, inte en sökväg till en katalog.</span><span class="sxs-lookup"><span data-stu-id="eaa57-222">For example, you must specify a path to one or more files, not a path to a directory.</span></span>
<span data-ttu-id="eaa57-223">Om du anger flera sökvägar använder du kommatecken för att avgränsa Sök vägarna.</span><span class="sxs-lookup"><span data-stu-id="eaa57-223">If you specify multiple paths, use commas to separate the paths.</span></span>

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

### <span data-ttu-id="eaa57-224">-Stream</span><span class="sxs-lookup"><span data-stu-id="eaa57-224">-Stream</span></span>

<span data-ttu-id="eaa57-225">Anger en alternativ data ström för innehåll.</span><span class="sxs-lookup"><span data-stu-id="eaa57-225">Specifies an alternative data stream for content.</span></span> <span data-ttu-id="eaa57-226">Om data strömmen inte finns skapar den här cmdleten den.</span><span class="sxs-lookup"><span data-stu-id="eaa57-226">If the stream does not exist, this cmdlet creates it.</span></span> <span data-ttu-id="eaa57-227">Jokertecken stöds inte.</span><span class="sxs-lookup"><span data-stu-id="eaa57-227">Wildcard characters are not supported.</span></span>

<span data-ttu-id="eaa57-228">**Stream** är en dynamisk parameter som fil Systems leverantören lägger till i `Add-Content` .</span><span class="sxs-lookup"><span data-stu-id="eaa57-228">**Stream** is a dynamic parameter that the FileSystem provider adds to `Add-Content`.</span></span> <span data-ttu-id="eaa57-229">Den här parametern fungerar bara i fil system enheter.</span><span class="sxs-lookup"><span data-stu-id="eaa57-229">This parameter works only in file system drives.</span></span>

<span data-ttu-id="eaa57-230">Du kan använda `Add-Content` cmdleten för att ändra innehållet i **zonen. unik identifierare** för den alternativa data strömmen.</span><span class="sxs-lookup"><span data-stu-id="eaa57-230">You can use the `Add-Content` cmdlet to change the content of the **Zone.Identifier** alternate data stream.</span></span> <span data-ttu-id="eaa57-231">Vi rekommenderar dock inte detta som ett sätt att eliminera säkerhets kontroller som blockerar filer som hämtas från Internet.</span><span class="sxs-lookup"><span data-stu-id="eaa57-231">However, we do not recommend this as a way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="eaa57-232">Om du verifierar att en Hämtad fil är säker använder du `Unblock-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="eaa57-232">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="eaa57-233">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="eaa57-233">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="eaa57-234">-Värde</span><span class="sxs-lookup"><span data-stu-id="eaa57-234">-Value</span></span>

<span data-ttu-id="eaa57-235">Anger det innehåll som ska läggas till.</span><span class="sxs-lookup"><span data-stu-id="eaa57-235">Specifies the content to be added.</span></span> <span data-ttu-id="eaa57-236">Skriv en Citerad sträng, till exempel **den här informationen endast för intern användning** eller ange ett objekt som innehåller innehåll, till exempel det **datetime** -objekt som `Get-Date` genereras.</span><span class="sxs-lookup"><span data-stu-id="eaa57-236">Type a quoted string, such as **This data is for internal use only** , or specify an object that contains content, such as the **DateTime** object that `Get-Date` generates.</span></span>

<span data-ttu-id="eaa57-237">Du kan inte ange innehållet i en fil genom att ange dess sökväg, eftersom sökvägen bara är en sträng.</span><span class="sxs-lookup"><span data-stu-id="eaa57-237">You cannot specify the contents of a file by typing its path, because the path is just a string.</span></span>
<span data-ttu-id="eaa57-238">Du kan använda ett `Get-Content` kommando för att hämta innehållet och skicka det till **värde** parametern.</span><span class="sxs-lookup"><span data-stu-id="eaa57-238">You can use a `Get-Content` command to get the content and pass it to the **Value** parameter.</span></span>

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

### <span data-ttu-id="eaa57-239">-Confirm</span><span class="sxs-lookup"><span data-stu-id="eaa57-239">-Confirm</span></span>

<span data-ttu-id="eaa57-240">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="eaa57-240">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="eaa57-241">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="eaa57-241">-WhatIf</span></span>

<span data-ttu-id="eaa57-242">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="eaa57-242">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="eaa57-243">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="eaa57-243">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="eaa57-244">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="eaa57-244">CommonParameters</span></span>

<span data-ttu-id="eaa57-245">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="eaa57-245">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="eaa57-246">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="eaa57-246">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="eaa57-247">INDATA</span><span class="sxs-lookup"><span data-stu-id="eaa57-247">INPUTS</span></span>

### <span data-ttu-id="eaa57-248">System. Object, system. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="eaa57-248">System.Object, System.Management.Automation.PSCredential</span></span>

<span data-ttu-id="eaa57-249">Du kan skicka pipe-värden, sökvägar eller autentiseringsuppgifter till `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="eaa57-249">You can pipe values, paths, or credentials to `Set-Content`.</span></span>

## <span data-ttu-id="eaa57-250">UTDATA</span><span class="sxs-lookup"><span data-stu-id="eaa57-250">OUTPUTS</span></span>

### <span data-ttu-id="eaa57-251">Ingen eller system. String</span><span class="sxs-lookup"><span data-stu-id="eaa57-251">None or System.String</span></span>

<span data-ttu-id="eaa57-252">När du använder parametern **Passthru** `Add-Content` genererar ett **system. String** -objekt som representerar innehållet.</span><span class="sxs-lookup"><span data-stu-id="eaa57-252">When you use the **PassThru** parameter, `Add-Content` generates a **System.String** object that represents the content.</span></span> <span data-ttu-id="eaa57-253">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="eaa57-253">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="eaa57-254">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="eaa57-254">NOTES</span></span>

- <span data-ttu-id="eaa57-255">När du rör ett objekt till `Add-Content` konverteras objektet till en sträng innan det läggs till i objektet.</span><span class="sxs-lookup"><span data-stu-id="eaa57-255">When you pipe an object to `Add-Content`, the object is converted to a string before it is added to the item.</span></span> <span data-ttu-id="eaa57-256">Objekt typen bestämmer sträng formatet, men formatet kan vara ett annat än standard visningen av objektet.</span><span class="sxs-lookup"><span data-stu-id="eaa57-256">The object type determines the string format, but the format might be different than the default display of the object.</span></span> <span data-ttu-id="eaa57-257">Om du vill kontrol lera sträng formatet använder du formateringsegenskaperna för sändnings-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="eaa57-257">To control the string format, use the formatting parameters of the sending cmdlet.</span></span>
- <span data-ttu-id="eaa57-258">Du kan också referera till `Add-Content` med dess inbyggda alias `ac` .</span><span class="sxs-lookup"><span data-stu-id="eaa57-258">You can also refer to `Add-Content` by its built-in alias, `ac`.</span></span> <span data-ttu-id="eaa57-259">Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="eaa57-259">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="eaa57-260">`Add-Content`Cmdleten är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="eaa57-260">The `Add-Content` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="eaa57-261">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="eaa57-261">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="eaa57-262">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="eaa57-262">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="eaa57-263">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="eaa57-263">RELATED LINKS</span></span>

[<span data-ttu-id="eaa57-264">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="eaa57-264">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="eaa57-265">about_Providers</span><span class="sxs-lookup"><span data-stu-id="eaa57-265">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="eaa57-266">Rensa innehåll</span><span class="sxs-lookup"><span data-stu-id="eaa57-266">Clear-Content</span></span>](Clear-Content.md)

[<span data-ttu-id="eaa57-267">Hämta innehåll</span><span class="sxs-lookup"><span data-stu-id="eaa57-267">Get-Content</span></span>](Get-Content.md)

[<span data-ttu-id="eaa57-268">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="eaa57-268">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="eaa57-269">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="eaa57-269">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="eaa57-270">Ange innehåll</span><span class="sxs-lookup"><span data-stu-id="eaa57-270">Set-Content</span></span>](Set-Content.md)
