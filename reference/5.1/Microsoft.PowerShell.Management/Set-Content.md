---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 5/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-content?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Content
ms.openlocfilehash: 897029cab790487f6834d021bfc447060fd39812
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265419"
---
# <span data-ttu-id="96e42-103">Set-Content</span><span class="sxs-lookup"><span data-stu-id="96e42-103">Set-Content</span></span>

## <span data-ttu-id="96e42-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="96e42-104">SYNOPSIS</span></span>
<span data-ttu-id="96e42-105">Skriver nytt innehåll eller ersätter befintligt innehåll i en fil.</span><span class="sxs-lookup"><span data-stu-id="96e42-105">Writes new content or replaces existing content in a file.</span></span>

## <span data-ttu-id="96e42-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="96e42-106">SYNTAX</span></span>

### <span data-ttu-id="96e42-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="96e42-107">Path (Default)</span></span>

```
Set-Content [-Path] <string[]> [-Value] <Object[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [-NoNewline] [-Encoding <FileSystemCmdletProviderEncoding>]
 [-Stream <string>] [<CommonParameters>]
```

### <span data-ttu-id="96e42-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="96e42-108">LiteralPath</span></span>

```
Set-Content [-Value] <Object[]> -LiteralPath <string[]> [-PassThru] [-Filter <string>]
 [-Include <string[]>] [-Exclude <string[]>] [-Force] [-Credential <pscredential>] [-WhatIf]
 [-Confirm] [-UseTransaction] [-NoNewline] [-Encoding <FileSystemCmdletProviderEncoding>]
 [-Stream <string>] [<CommonParameters>]
```

## <span data-ttu-id="96e42-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="96e42-109">DESCRIPTION</span></span>

<span data-ttu-id="96e42-110">`Set-Content` är en sträng bearbetnings-cmdlet som skriver nytt innehåll eller ersätter innehållet i en fil.</span><span class="sxs-lookup"><span data-stu-id="96e42-110">`Set-Content` is a string-processing cmdlet that writes new content or replaces the content in a file.</span></span> <span data-ttu-id="96e42-111">`Set-Content` ersätter det befintliga innehållet och skiljer sig från den `Add-Content` cmdlet som lägger till innehåll i en fil.</span><span class="sxs-lookup"><span data-stu-id="96e42-111">`Set-Content` replaces the existing content and differs from the `Add-Content` cmdlet that appends content to a file.</span></span> <span data-ttu-id="96e42-112">Om du vill skicka innehåll till `Set-Content` kan du använda parametern **Value** på kommando raden eller skicka innehåll via pipelinen.</span><span class="sxs-lookup"><span data-stu-id="96e42-112">To send content to `Set-Content` you can use the **Value** parameter on the command line or send content through the pipeline.</span></span>

<span data-ttu-id="96e42-113">Om du behöver skapa filer eller kataloger för följande exempel, se [New-item](New-Item.md).</span><span class="sxs-lookup"><span data-stu-id="96e42-113">If you need to create files or directories for the following examples, see [New-Item](New-Item.md).</span></span>

## <span data-ttu-id="96e42-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="96e42-114">EXAMPLES</span></span>

### <span data-ttu-id="96e42-115">Exempel 1: Ersätt innehållet i flera filer i en katalog</span><span class="sxs-lookup"><span data-stu-id="96e42-115">Example 1: Replace the contents of multiple files in a directory</span></span>

<span data-ttu-id="96e42-116">I det här exemplet ersätts innehållet för flera filer i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="96e42-116">This example replaces the content for multiple files in the current directory.</span></span>

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

<span data-ttu-id="96e42-117">`Get-ChildItem`Cmdleten använder **Sök vägs** parametern för att visa **. txt** -filer som börjar med `Test*` i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="96e42-117">The `Get-ChildItem` cmdlet uses the **Path** parameter to list **.txt** files that begin with `Test*` in the current directory.</span></span> <span data-ttu-id="96e42-118">`Set-Content`Cmdleten använder parametern **Path** för att ange `Test*.txt` filerna.</span><span class="sxs-lookup"><span data-stu-id="96e42-118">The `Set-Content` cmdlet uses the **Path** parameter to specify the `Test*.txt` files.</span></span> <span data-ttu-id="96e42-119">Parametern **Value** innehåller text strängen **Hello, World** som ersätter det befintliga innehållet i varje fil.</span><span class="sxs-lookup"><span data-stu-id="96e42-119">The **Value** parameter provides the text string **Hello, World** that replaces the existing content in each file.</span></span> <span data-ttu-id="96e42-120">`Get-Content`Cmdleten använder parametern **Path** för att ange `Test*.txt` filerna och visar varje fils innehåll i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="96e42-120">The `Get-Content` cmdlet uses the **Path** parameter to specify the `Test*.txt` files and displays each file's content in the PowerShell console.</span></span>

### <span data-ttu-id="96e42-121">Exempel 2: skapa en ny fil och skriv innehåll</span><span class="sxs-lookup"><span data-stu-id="96e42-121">Example 2: Create a new file and write content</span></span>

<span data-ttu-id="96e42-122">Det här exemplet skapar en ny fil och skriver aktuellt datum och tid till filen.</span><span class="sxs-lookup"><span data-stu-id="96e42-122">This example creates a new file and writes the current date and time to the file.</span></span>

```powershell
Set-Content -Path .\DateTime.txt -Value (Get-Date)
Get-Content -Path .\DateTime.txt
```

```Output
1/30/2019 09:55:08
```

<span data-ttu-id="96e42-123">`Set-Content` använder parametrarna **sökväg** och **värde** för att skapa en ny fil med namnet **DateTime.txt** i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="96e42-123">`Set-Content` uses the **Path** and **Value** parameters to create a new file named **DateTime.txt** in the current directory.</span></span> <span data-ttu-id="96e42-124">**Värde** parametern använder `Get-Date` för att hämta aktuellt datum och aktuell tid.</span><span class="sxs-lookup"><span data-stu-id="96e42-124">The **Value** parameter uses `Get-Date` to get the current date and time.</span></span>
<span data-ttu-id="96e42-125">`Set-Content` skriver **datetime** -objektet till filen som en sträng.</span><span class="sxs-lookup"><span data-stu-id="96e42-125">`Set-Content` writes the **DateTime** object to the file as a string.</span></span> <span data-ttu-id="96e42-126">`Get-Content`Cmdleten använder parametern **Path** för att visa innehållet i **DateTime.txt** i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="96e42-126">The `Get-Content` cmdlet uses the **Path** parameter to display the content of **DateTime.txt** in the PowerShell console.</span></span>

### <span data-ttu-id="96e42-127">Exempel 3: ersätt text i en fil</span><span class="sxs-lookup"><span data-stu-id="96e42-127">Example 3: Replace text in a file</span></span>

<span data-ttu-id="96e42-128">Det här kommandot ersätter alla instanser av Word i en befintlig fil.</span><span class="sxs-lookup"><span data-stu-id="96e42-128">This command replaces all instances of word within an existing file.</span></span>

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

<span data-ttu-id="96e42-129">`Get-Content`Cmdleten använder parametern **Path** för att ange **Notice.txt** filen i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="96e42-129">The `Get-Content` cmdlet uses the **Path** parameter to specify the **Notice.txt** file in the current directory.</span></span> <span data-ttu-id="96e42-130">`Get-Content`Kommandot omges av parenteser så att kommandot slutförs innan det skickas ned pipelinen.</span><span class="sxs-lookup"><span data-stu-id="96e42-130">The `Get-Content` command is wrapped with parentheses so that the command finishes before being sent down the pipeline.</span></span>

<span data-ttu-id="96e42-131">Innehållet i **Notice.txt** -filen skickas ned pipelinen till `ForEach-Object` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="96e42-131">The contents of the **Notice.txt** file are sent down the pipeline to the `ForEach-Object` cmdlet.</span></span>
<span data-ttu-id="96e42-132">`ForEach-Object` använder den automatiska variabeln `$_` och ersätter varje förekomst av **Varning** med **försiktighet**.</span><span class="sxs-lookup"><span data-stu-id="96e42-132">`ForEach-Object` uses the automatic variable `$_` and replaces each occurrence of **Warning** with **Caution**.</span></span> <span data-ttu-id="96e42-133">Objekten skickas ned pipelinen till `Set-Content` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="96e42-133">The objects are sent down the pipeline to the `Set-Content` cmdlet.</span></span> <span data-ttu-id="96e42-134">`Set-Content` använder parametern **Path** för att ange **Notice.txt** -filen och skriver det uppdaterade innehållet till filen.</span><span class="sxs-lookup"><span data-stu-id="96e42-134">`Set-Content` uses the **Path** parameter to specify the **Notice.txt** file and writes the updated content to the file.</span></span>

<span data-ttu-id="96e42-135">Den sista `Get-Content` cmdleten visar det uppdaterade fil innehållet i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="96e42-135">The last `Get-Content` cmdlet displays the updated file content in the PowerShell console.</span></span>

### <span data-ttu-id="96e42-136">Exempel 4: använda filter med Set-Content</span><span class="sxs-lookup"><span data-stu-id="96e42-136">Example 4: Use Filters with Set-Content</span></span>

<span data-ttu-id="96e42-137">Du kan ange ett filter för `Set-Content` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="96e42-137">You can specify a filter to the `Set-Content` cmdlet.</span></span> <span data-ttu-id="96e42-138">När du använder filter för att kvalificera **Sök vägs** parametern måste du inkludera en efterföljande asterisk ( `*` ) för att ange innehållet i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="96e42-138">When using filters to qualify the **Path** parameter, you need to include a trailing asterisk (`*`) to indicate the contents of the path.</span></span>

<span data-ttu-id="96e42-139">Följande kommando anger innehållet `*.txt` för alla filer i `C:\Temp` katalogen till **värdet** Empty.</span><span class="sxs-lookup"><span data-stu-id="96e42-139">The following command set the content all `*.txt` files in the `C:\Temp` directory to the **Value** empty.</span></span>

```powershell
Set-Content -Path C:\Temp\* -Filter *.txt -Value "Empty"
```

## <span data-ttu-id="96e42-140">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="96e42-140">PARAMETERS</span></span>

### <span data-ttu-id="96e42-141">-Credential</span><span class="sxs-lookup"><span data-stu-id="96e42-141">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="96e42-142">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="96e42-142">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="96e42-143">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="96e42-143">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="96e42-144">-Encoding</span><span class="sxs-lookup"><span data-stu-id="96e42-144">-Encoding</span></span>

<span data-ttu-id="96e42-145">Anger typ av kodning för mål filen.</span><span class="sxs-lookup"><span data-stu-id="96e42-145">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="96e42-146">Standardvärdet är `Default`.</span><span class="sxs-lookup"><span data-stu-id="96e42-146">The default value is `Default`.</span></span>

<span data-ttu-id="96e42-147">Encoding är en dynamisk parameter som fil Systems leverantören lägger till i `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="96e42-147">Encoding is a dynamic parameter that the FileSystem provider adds to `Set-Content`.</span></span> <span data-ttu-id="96e42-148">Den här parametern fungerar bara i fil system enheter.</span><span class="sxs-lookup"><span data-stu-id="96e42-148">This parameter works only in file system drives.</span></span>

<span data-ttu-id="96e42-149">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="96e42-149">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="96e42-150">`Ascii` Använder ASCII-teckenuppsättning (7-bitars).</span><span class="sxs-lookup"><span data-stu-id="96e42-150">`Ascii` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="96e42-151">`BigEndianUnicode` Använder UTF-16 med big-endian byte-ordningen.</span><span class="sxs-lookup"><span data-stu-id="96e42-151">`BigEndianUnicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="96e42-152">`BigEndianUTF32` Använder UTF-32 med big-endian byte-ordningen.</span><span class="sxs-lookup"><span data-stu-id="96e42-152">`BigEndianUTF32` Uses UTF-32 with the big-endian byte order.</span></span>
- <span data-ttu-id="96e42-153">`Byte` Kodar en uppsättning tecken i en sekvens med byte.</span><span class="sxs-lookup"><span data-stu-id="96e42-153">`Byte` Encodes a set of characters into a sequence of bytes.</span></span>
- <span data-ttu-id="96e42-154">`Default` Använder kodningen som motsvarar systemets aktiva tecken tabell (vanligt vis ANSI).</span><span class="sxs-lookup"><span data-stu-id="96e42-154">`Default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="96e42-155">`Oem` Använder kodningen som motsvarar systemets aktuella OEM Code-sida.</span><span class="sxs-lookup"><span data-stu-id="96e42-155">`Oem` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="96e42-156">`String` Samma som `Unicode` .</span><span class="sxs-lookup"><span data-stu-id="96e42-156">`String` Same as `Unicode`.</span></span>
- <span data-ttu-id="96e42-157">`Unicode` Använder UTF-16 med en liten-endian-order.</span><span class="sxs-lookup"><span data-stu-id="96e42-157">`Unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="96e42-158">`Unknown` Samma som `Unicode` .</span><span class="sxs-lookup"><span data-stu-id="96e42-158">`Unknown` Same as `Unicode`.</span></span>
- <span data-ttu-id="96e42-159">`UTF7` Använder UTF-7.</span><span class="sxs-lookup"><span data-stu-id="96e42-159">`UTF7` Uses UTF-7.</span></span>
- <span data-ttu-id="96e42-160">`UTF8` Använder UTF-8.</span><span class="sxs-lookup"><span data-stu-id="96e42-160">`UTF8` Uses UTF-8.</span></span>
- <span data-ttu-id="96e42-161">`UTF32` Använder UTF-32 med en liten-endian-order.</span><span class="sxs-lookup"><span data-stu-id="96e42-161">`UTF32` Uses UTF-32 with the little-endian byte order.</span></span>

<span data-ttu-id="96e42-162">Encoding är en dynamisk parameter som fil Systems leverantören lägger till i `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="96e42-162">Encoding is a dynamic parameter that the FileSystem provider adds to `Set-Content`.</span></span> <span data-ttu-id="96e42-163">Den här parametern fungerar bara i fil system enheter.</span><span class="sxs-lookup"><span data-stu-id="96e42-163">This parameter works only in file system drives.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, Byte, Default, OEM, String, Unicode, Unknown, UTF7, UTF8, UTF32

Required: False
Position: Named
Default value: Default
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="96e42-164">-Undanta</span><span class="sxs-lookup"><span data-stu-id="96e42-164">-Exclude</span></span>

<span data-ttu-id="96e42-165">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="96e42-165">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="96e42-166">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="96e42-166">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="96e42-167">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="96e42-167">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="96e42-168">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="96e42-168">Wildcard characters are permitted.</span></span> <span data-ttu-id="96e42-169">Parametern **exclude** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="96e42-169">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="96e42-170">-Filter</span><span class="sxs-lookup"><span data-stu-id="96e42-170">-Filter</span></span>

<span data-ttu-id="96e42-171">Anger ett filter för att kvalificera **Sök vägs** parametern.</span><span class="sxs-lookup"><span data-stu-id="96e42-171">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="96e42-172">[Fil Systems](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) leverantören är den enda installerade PowerShell-providern som stöder användningen av filter.</span><span class="sxs-lookup"><span data-stu-id="96e42-172">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="96e42-173">Du kan hitta syntaxen för filter språket för **fil systemet** i [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="96e42-173">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="96e42-174">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="96e42-174">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="96e42-175">-Force</span><span class="sxs-lookup"><span data-stu-id="96e42-175">-Force</span></span>

<span data-ttu-id="96e42-176">Tvingar cmdleten att ange innehållet i en fil, även om filen är skrivskyddad.</span><span class="sxs-lookup"><span data-stu-id="96e42-176">Forces the cmdlet to set the contents of a file, even if the file is read-only.</span></span> <span data-ttu-id="96e42-177">Implementeringen varierar från providern till providern.</span><span class="sxs-lookup"><span data-stu-id="96e42-177">Implementation varies from provider to provider.</span></span> <span data-ttu-id="96e42-178">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="96e42-178">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>
<span data-ttu-id="96e42-179">**Force** -parametern åsidosätter inte säkerhets begränsningar.</span><span class="sxs-lookup"><span data-stu-id="96e42-179">The **Force** parameter does not override security restrictions.</span></span>

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

### <span data-ttu-id="96e42-180">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="96e42-180">-Include</span></span>

<span data-ttu-id="96e42-181">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="96e42-181">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="96e42-182">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="96e42-182">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="96e42-183">Ange ett Sök vägs element eller ett mönster, till exempel `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="96e42-183">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="96e42-184">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="96e42-184">Wildcard characters are permitted.</span></span> <span data-ttu-id="96e42-185">Parametern **include** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="96e42-185">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="96e42-186">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="96e42-186">-LiteralPath</span></span>

<span data-ttu-id="96e42-187">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="96e42-187">Specifies a path to one or more locations.</span></span> <span data-ttu-id="96e42-188">Värdet för **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="96e42-188">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="96e42-189">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="96e42-189">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="96e42-190">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="96e42-190">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="96e42-191">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="96e42-191">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="96e42-192">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="96e42-192">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="96e42-193">– NoNewline</span><span class="sxs-lookup"><span data-stu-id="96e42-193">-NoNewline</span></span>

<span data-ttu-id="96e42-194">Sträng representationerna av indata-objekten sammanfogas för att bilda utdata.</span><span class="sxs-lookup"><span data-stu-id="96e42-194">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="96e42-195">Inga blank steg eller newlines infogas mellan utgående strängar.</span><span class="sxs-lookup"><span data-stu-id="96e42-195">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="96e42-196">Ingen ny rad läggs till efter den sista utgående strängen.</span><span class="sxs-lookup"><span data-stu-id="96e42-196">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="96e42-197">– PassThru</span><span class="sxs-lookup"><span data-stu-id="96e42-197">-PassThru</span></span>

<span data-ttu-id="96e42-198">Returnerar ett objekt som representerar innehållet.</span><span class="sxs-lookup"><span data-stu-id="96e42-198">Returns an object that represents the content.</span></span> <span data-ttu-id="96e42-199">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="96e42-199">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="96e42-200">-Path</span><span class="sxs-lookup"><span data-stu-id="96e42-200">-Path</span></span>

<span data-ttu-id="96e42-201">Anger sökvägen till det objekt som tar emot innehållet.</span><span class="sxs-lookup"><span data-stu-id="96e42-201">Specifies the path of the item that receives the content.</span></span>
<span data-ttu-id="96e42-202">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="96e42-202">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="96e42-203">-Stream</span><span class="sxs-lookup"><span data-stu-id="96e42-203">-Stream</span></span>

<span data-ttu-id="96e42-204">Anger en alternativ data ström för innehåll.</span><span class="sxs-lookup"><span data-stu-id="96e42-204">Specifies an alternative data stream for content.</span></span> <span data-ttu-id="96e42-205">Om data strömmen inte finns skapar den här cmdleten den.</span><span class="sxs-lookup"><span data-stu-id="96e42-205">If the stream does not exist, this cmdlet creates it.</span></span> <span data-ttu-id="96e42-206">Jokertecken stöds inte.</span><span class="sxs-lookup"><span data-stu-id="96e42-206">Wildcard characters are not supported.</span></span>

<span data-ttu-id="96e42-207">**Stream** är en dynamisk parameter som **fil Systems** leverantören lägger till i `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="96e42-207">**Stream** is a dynamic parameter that the **FileSystem** provider adds to `Set-Content`.</span></span> <span data-ttu-id="96e42-208">Den här parametern fungerar bara i fil system enheter.</span><span class="sxs-lookup"><span data-stu-id="96e42-208">This parameter works only in file system drives.</span></span>

<span data-ttu-id="96e42-209">Du kan använda `Set-Content` cmdleten för att ändra innehållet i **zonen. unik identifierare** för den alternativa data strömmen.</span><span class="sxs-lookup"><span data-stu-id="96e42-209">You can use the `Set-Content` cmdlet to change the content of the **Zone.Identifier** alternate data stream.</span></span> <span data-ttu-id="96e42-210">Vi rekommenderar dock inte detta som ett sätt att eliminera säkerhets kontroller som blockerar filer som hämtas från Internet.</span><span class="sxs-lookup"><span data-stu-id="96e42-210">However, we do not recommend this as a way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="96e42-211">Om du verifierar att en Hämtad fil är säker använder du `Unblock-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="96e42-211">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="96e42-212">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="96e42-212">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="96e42-213">– UseTransaction</span><span class="sxs-lookup"><span data-stu-id="96e42-213">-UseTransaction</span></span>

<span data-ttu-id="96e42-214">Inkluderar kommandot i den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="96e42-214">Includes the command in the active transaction.</span></span> <span data-ttu-id="96e42-215">Den här parametern är bara giltig medan en transaktion pågår.</span><span class="sxs-lookup"><span data-stu-id="96e42-215">This parameter is valid only when a transaction is in progress.</span></span> <span data-ttu-id="96e42-216">Mer information finns i [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span><span class="sxs-lookup"><span data-stu-id="96e42-216">For more information, see [about_Transactions](../Microsoft.PowerShell.Core/About/about_Transactions.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="96e42-217">-Värde</span><span class="sxs-lookup"><span data-stu-id="96e42-217">-Value</span></span>

<span data-ttu-id="96e42-218">Anger det nya innehållet för objektet.</span><span class="sxs-lookup"><span data-stu-id="96e42-218">Specifies the new content for the item.</span></span>

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

### <span data-ttu-id="96e42-219">-Confirm</span><span class="sxs-lookup"><span data-stu-id="96e42-219">-Confirm</span></span>

<span data-ttu-id="96e42-220">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="96e42-220">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="96e42-221">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="96e42-221">-WhatIf</span></span>

<span data-ttu-id="96e42-222">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="96e42-222">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="96e42-223">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="96e42-223">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="96e42-224">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="96e42-224">CommonParameters</span></span>

<span data-ttu-id="96e42-225">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="96e42-225">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span>
<span data-ttu-id="96e42-226">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="96e42-226">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="96e42-227">INDATA</span><span class="sxs-lookup"><span data-stu-id="96e42-227">INPUTS</span></span>

### <span data-ttu-id="96e42-228">System. Object</span><span class="sxs-lookup"><span data-stu-id="96e42-228">System.Object</span></span>

<span data-ttu-id="96e42-229">Du kan skicka en pipe till ett objekt som innehåller det nya värdet för objektet `Set-Content` .</span><span class="sxs-lookup"><span data-stu-id="96e42-229">You can pipe an object that contains the new value for the item to `Set-Content`.</span></span>

## <span data-ttu-id="96e42-230">UTDATA</span><span class="sxs-lookup"><span data-stu-id="96e42-230">OUTPUTS</span></span>

### <span data-ttu-id="96e42-231">Ingen eller system. String</span><span class="sxs-lookup"><span data-stu-id="96e42-231">None or System.String</span></span>

<span data-ttu-id="96e42-232">När du använder parametern **Passthru** `Set-Content` genererar ett **system. String** -objekt som representerar innehållet.</span><span class="sxs-lookup"><span data-stu-id="96e42-232">When you use the **PassThru** parameter, `Set-Content` generates a **System.String** object that represents the content.</span></span> <span data-ttu-id="96e42-233">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="96e42-233">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="96e42-234">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="96e42-234">NOTES</span></span>

- <span data-ttu-id="96e42-235">Du kan också referera till `Set-Content` med dess inbyggda alias `sc` .</span><span class="sxs-lookup"><span data-stu-id="96e42-235">You can also refer to `Set-Content` by its built-in alias, `sc`.</span></span>
  <span data-ttu-id="96e42-236">Mer information finns i [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span><span class="sxs-lookup"><span data-stu-id="96e42-236">For more information, see [about_Aliases](../Microsoft.PowerShell.Core/About/about_Aliases.md).</span></span>
- <span data-ttu-id="96e42-237">`Set-Content` är utformad för sträng bearbetning.</span><span class="sxs-lookup"><span data-stu-id="96e42-237">`Set-Content` is designed for string processing.</span></span> <span data-ttu-id="96e42-238">Om du rör icke-sträng objekt till `Set-Content` konverteras objektet till en sträng innan det skrivs.</span><span class="sxs-lookup"><span data-stu-id="96e42-238">If you pipe non-string objects to `Set-Content`, it converts the object to a string before writing it.</span></span> <span data-ttu-id="96e42-239">Använd om du vill skriva objekt till filer `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="96e42-239">To write objects to files, use `Out-File`.</span></span>
- <span data-ttu-id="96e42-240">`Set-Content`Cmdleten är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="96e42-240">The `Set-Content` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="96e42-241">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="96e42-241">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="96e42-242">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="96e42-242">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="96e42-243">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="96e42-243">RELATED LINKS</span></span>

[<span data-ttu-id="96e42-244">about_Aliases</span><span class="sxs-lookup"><span data-stu-id="96e42-244">about_Aliases</span></span>](../Microsoft.PowerShell.Core/About/about_Aliases.md)

[<span data-ttu-id="96e42-245">about_Automatic_Variables. MD</span><span class="sxs-lookup"><span data-stu-id="96e42-245">about_Automatic_Variables.md</span></span>](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md)

[<span data-ttu-id="96e42-246">about_Providers</span><span class="sxs-lookup"><span data-stu-id="96e42-246">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="96e42-247">about_Transactions</span><span class="sxs-lookup"><span data-stu-id="96e42-247">about_Transactions</span></span>](../Microsoft.PowerShell.Core/About/about_Transactions.md)

[<span data-ttu-id="96e42-248">Lägg till innehåll</span><span class="sxs-lookup"><span data-stu-id="96e42-248">Add-Content</span></span>](Add-Content.md)

[<span data-ttu-id="96e42-249">Rensa innehåll</span><span class="sxs-lookup"><span data-stu-id="96e42-249">Clear-Content</span></span>](Clear-Content.md)

[<span data-ttu-id="96e42-250">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="96e42-250">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="96e42-251">Hämta innehåll</span><span class="sxs-lookup"><span data-stu-id="96e42-251">Get-Content</span></span>](Get-Content.md)

[<span data-ttu-id="96e42-252">-Objekt</span><span class="sxs-lookup"><span data-stu-id="96e42-252">ForEach-Object</span></span>](../Microsoft.PowerShell.Core/ForEach-Object.md)

[<span data-ttu-id="96e42-253">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="96e42-253">New-Item</span></span>](New-Item.md)
