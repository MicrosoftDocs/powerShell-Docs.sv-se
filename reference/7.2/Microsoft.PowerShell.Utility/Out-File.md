---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-file?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-File
ms.openlocfilehash: e3a066957ab1e6935049003f8ccf55aee8bb7c94
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709072"
---
# <span data-ttu-id="9ee1d-102">Out-File</span><span class="sxs-lookup"><span data-stu-id="9ee1d-102">Out-File</span></span>

## <span data-ttu-id="9ee1d-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="9ee1d-103">SYNOPSIS</span></span>
<span data-ttu-id="9ee1d-104">Skickar utdata till en fil.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-104">Sends output to a file.</span></span>

## <span data-ttu-id="9ee1d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9ee1d-105">SYNTAX</span></span>

### <span data-ttu-id="9ee1d-106">ByPath (standard)</span><span class="sxs-lookup"><span data-stu-id="9ee1d-106">ByPath (Default)</span></span>

```
Out-File [-FilePath] <string> [[-Encoding] <Encoding>] [-Append] [-Force] [-NoClobber]
 [-Width <int>] [-NoNewline] [-InputObject <psobject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="9ee1d-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="9ee1d-107">ByLiteralPath</span></span>

```
Out-File [[-Encoding] <Encoding>] -LiteralPath <string> [-Append] [-Force] [-NoClobber]
 [-Width <int>] [-NoNewline] [-InputObject <psobject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="9ee1d-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="9ee1d-108">DESCRIPTION</span></span>

<span data-ttu-id="9ee1d-109">`Out-File`Cmdleten skickar utdata till en fil.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-109">The `Out-File` cmdlet sends output to a file.</span></span> <span data-ttu-id="9ee1d-110">Den använder implicit PowerShell: s format system för att skriva till filen.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-110">It implicitly uses PowerShell's formatting system to write to the file.</span></span> <span data-ttu-id="9ee1d-111">Filen får samma visnings representation som i terminalen.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-111">The file receives the same display representation as the terminal.</span></span> <span data-ttu-id="9ee1d-112">Det innebär att utmatningen kanske inte är idealisk för programmatisk bearbetning om inte alla indata är strängar.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-112">This means that the output may not be ideal for programmatic processing unless all input objects are strings.</span></span>
<span data-ttu-id="9ee1d-113">När du behöver ange parametrar för utdata använder du `Out-File` istället för omdirigerings operatorn ( `>` ).</span><span class="sxs-lookup"><span data-stu-id="9ee1d-113">When you need to specify parameters for the output, use `Out-File` rather than the redirection operator (`>`).</span></span> <span data-ttu-id="9ee1d-114">Mer information om omdirigering finns i [about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md).</span><span class="sxs-lookup"><span data-stu-id="9ee1d-114">For more information about redirection, see [about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md).</span></span>

## <span data-ttu-id="9ee1d-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="9ee1d-115">EXAMPLES</span></span>

### <span data-ttu-id="9ee1d-116">Exempel 1: skicka utdata och skapa en fil</span><span class="sxs-lookup"><span data-stu-id="9ee1d-116">Example 1: Send output and create a file</span></span>

<span data-ttu-id="9ee1d-117">Det här exemplet visar hur du skickar en lista över den lokala datorns processer till en fil.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-117">This example shows how to send a list of the local computer's processes to a file.</span></span> <span data-ttu-id="9ee1d-118">Om filen inte finns `Out-File` skapas filen på den angivna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-118">If the file does not exist, `Out-File` creates the file in the specified path.</span></span>

```powershell
Get-Process | Out-File -FilePath .\Process.txt
Get-Content -Path .\Process.txt
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     29    22.39      35.40      10.98   42764   9 Application
     53    99.04     113.96       0.00   32664   0 CcmExec
     27    96.62     112.43     113.00   17720   9 Code
```

<span data-ttu-id="9ee1d-119">`Get-Process`Cmdleten hämtar listan över processer som körs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-119">The `Get-Process` cmdlet gets the list of processes running on the local computer.</span></span> <span data-ttu-id="9ee1d-120">**Process** objekt skickas ned pipelinen till `Out-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-120">The **Process** objects are sent down the pipeline to the `Out-File` cmdlet.</span></span> <span data-ttu-id="9ee1d-121">`Out-File` använder parametern **sökväg** och skapar en fil i den aktuella katalogen med namnet **Process.txt**.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-121">`Out-File` uses the **FilePath** parameter and creates a file in the current directory named **Process.txt**.</span></span> <span data-ttu-id="9ee1d-122">`Get-Content`Kommandot hämtar innehåll från filen och visar det i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-122">The `Get-Content` command gets content from the file and displays it in the PowerShell console.</span></span>

### <span data-ttu-id="9ee1d-123">Exempel 2: förhindra att en befintlig fil skrivs över</span><span class="sxs-lookup"><span data-stu-id="9ee1d-123">Example 2: Prevent an existing file from being overwritten</span></span>

<span data-ttu-id="9ee1d-124">Det här exemplet förhindrar att en befintlig fil skrivs över.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-124">This example prevents an existing file from being overwritten.</span></span> <span data-ttu-id="9ee1d-125">Som standard `Out-File` skriver över befintliga filer.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-125">By default, `Out-File` overwrites existing files.</span></span>

```powershell
Get-Process | Out-File -FilePath .\Process.txt -NoClobber
```

```Output
Out-File : The file 'C:\Test\Process.txt' already exists.
At line:1 char:15
+ Get-Process | Out-File -FilePath .\Process.txt -NoClobber
+               ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
```

<span data-ttu-id="9ee1d-126">`Get-Process`Cmdleten hämtar listan över processer som körs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-126">The `Get-Process` cmdlet gets the list of processes running on the local computer.</span></span> <span data-ttu-id="9ee1d-127">**Process** objekt skickas ned pipelinen till `Out-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-127">The **Process** objects are sent down the pipeline to the `Out-File` cmdlet.</span></span> <span data-ttu-id="9ee1d-128">`Out-File` använder parametern **sökväg** och försöker skriva till en fil i den aktuella katalogen med namnet **Process.txt**.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-128">`Out-File` uses the **FilePath** parameter and attempts to write to a file in the current directory named **Process.txt**.</span></span> <span data-ttu-id="9ee1d-129">Parametern **NoClobber** förhindrar att filen skrivs över och visar ett meddelande om att filen redan finns.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-129">The **NoClobber** parameter prevents the file from being overwritten and displays a message that the file already exists.</span></span>

### <span data-ttu-id="9ee1d-130">Exempel 3: skicka utdata till en fil i ASCII-format</span><span class="sxs-lookup"><span data-stu-id="9ee1d-130">Example 3: Send output to a file in ASCII format</span></span>

<span data-ttu-id="9ee1d-131">Det här exemplet visar hur du kodar utdata med en speciell kodnings typ.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-131">This example shows how to encode output with a specific encoding type.</span></span>

```powershell
$Procs = Get-Process
Out-File -FilePath .\Process.txt -InputObject $Procs -Encoding ASCII -Width 50
```

<span data-ttu-id="9ee1d-132">`Get-Process`Cmdleten hämtar listan över processer som körs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-132">The `Get-Process` cmdlet gets the list of processes running on the local computer.</span></span> <span data-ttu-id="9ee1d-133">**Process** objekt lagras i variabeln `$Procs` .</span><span class="sxs-lookup"><span data-stu-id="9ee1d-133">The **Process** objects are stored in the variable, `$Procs`.</span></span> <span data-ttu-id="9ee1d-134">`Out-File` använder parametern **sökväg** och skapar en fil i den aktuella katalogen med namnet **Process.txt**.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-134">`Out-File` uses the **FilePath** parameter and creates a file in the current directory named **Process.txt**.</span></span> <span data-ttu-id="9ee1d-135">**InputObject** -parametern överför process objekt `$Procs` till filen **Process.txt**.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-135">The **InputObject** parameter passes the process objects in `$Procs` to the file **Process.txt**.</span></span> <span data-ttu-id="9ee1d-136">**Encoding** -parametern konverterar utdata till **ASCII** -format.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-136">The **Encoding** parameter converts the output to **ASCII** format.</span></span> <span data-ttu-id="9ee1d-137">Parametern **width** begränsar varje rad i filen till 50 tecken så att vissa data kan trunkeras.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-137">The **Width** parameter limits each line in the file to 50 characters so some data might be truncated.</span></span>

### <span data-ttu-id="9ee1d-138">Exempel 4: Använd en provider och skicka utdata till en fil</span><span class="sxs-lookup"><span data-stu-id="9ee1d-138">Example 4: Use a provider and send output to a file</span></span>

<span data-ttu-id="9ee1d-139">Det här exemplet visar hur du använder `Out-File` cmdleten när du inte befinner dig i en **fil för fil Systems** leverantör.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-139">This example shows how to use the `Out-File` cmdlet when you are not in a **FileSystem** provider drive.</span></span> <span data-ttu-id="9ee1d-140">Använd `Get-PSProvider` cmdleten för att Visa providers på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-140">Use the `Get-PSProvider` cmdlet to view the providers on your local computer.</span></span> <span data-ttu-id="9ee1d-141">Mer information finns i [about_Providers](../Microsoft.Powershell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="9ee1d-141">For more information, see [about_Providers](../Microsoft.Powershell.Core/About/about_Providers.md).</span></span>

```
PS> Set-Location -Path Alias:

PS> Get-Location

Path
----
Alias:\

PS> Get-ChildItem | Out-File -FilePath C:\TestDir\AliasNames.txt

PS> Get-Content -Path C:\TestDir\AliasNames.txt

CommandType     Name
-----------     ----
Alias           % -> ForEach-Object
Alias           ? -> Where-Object
Alias           ac -> Add-Content
Alias           cat -> Get-Content
```

<span data-ttu-id="9ee1d-142">`Set-Location`Kommandot använder parametern **Path** för att ange den aktuella platsen för register leverantören `Alias:` .</span><span class="sxs-lookup"><span data-stu-id="9ee1d-142">The `Set-Location` command uses the **Path** parameter to set the current location to the registry provider `Alias:`.</span></span> <span data-ttu-id="9ee1d-143">`Get-Location`Cmdleten visar den fullständiga sökvägen för `Alias:` .</span><span class="sxs-lookup"><span data-stu-id="9ee1d-143">The `Get-Location` cmdlet displays the complete path for `Alias:`.</span></span>
<span data-ttu-id="9ee1d-144">`Get-ChildItem` skickar objekt nedåt i pipeline till `Out-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-144">`Get-ChildItem` sends objects down the pipeline to the `Out-File` cmdlet.</span></span> <span data-ttu-id="9ee1d-145">`Out-File` använder parametern **sökväg** för att ange den fullständiga sökvägen och fil namnet för utdata, **C:\TestDir\AliasNames.txt**.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-145">`Out-File` uses the **FilePath** parameter to specify the complete path and filename for the output, **C:\TestDir\AliasNames.txt**.</span></span> <span data-ttu-id="9ee1d-146">`Get-Content`Cmdleten använder parametern **Path** och visar filens innehåll i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-146">The `Get-Content` cmdlet uses the **Path** parameter and displays the file's content in the PowerShell console.</span></span>

## <span data-ttu-id="9ee1d-147">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="9ee1d-147">PARAMETERS</span></span>

### <span data-ttu-id="9ee1d-148">-Lägg till</span><span class="sxs-lookup"><span data-stu-id="9ee1d-148">-Append</span></span>

<span data-ttu-id="9ee1d-149">Lägger till utdata i slutet av en befintlig fil.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-149">Adds the output to the end of an existing file.</span></span>

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

### <span data-ttu-id="9ee1d-150">-Encoding</span><span class="sxs-lookup"><span data-stu-id="9ee1d-150">-Encoding</span></span>

<span data-ttu-id="9ee1d-151">Anger typ av kodning för mål filen.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-151">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="9ee1d-152">Standardvärdet är `utf8NoBOM`.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-152">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="9ee1d-153">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="9ee1d-153">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="9ee1d-154">`ascii`: Använder kodningen för ASCII-teckenuppsättningen (7 bitar).</span><span class="sxs-lookup"><span data-stu-id="9ee1d-154">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="9ee1d-155">`bigendianunicode`: Kodar i UTF-16-format med big-endian byte-ordning.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-155">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="9ee1d-156">`bigendianutf32`: Kodar i UTF-32-format med big-endian-dataordningen.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-156">`bigendianutf32`: Encodes in UTF-32 format using the big-endian byte order.</span></span>
- <span data-ttu-id="9ee1d-157">`oem`: Använder standard kodning för MS-DOS-och-konsol program.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-157">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="9ee1d-158">`unicode`: Kodar i UTF-16-format med lite-endian-dataordning.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-158">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="9ee1d-159">`utf7`: Kodar i UTF-7-format.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-159">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="9ee1d-160">`utf8`: Kodar i UTF-8-format.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-160">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="9ee1d-161">`utf8BOM`: Kodar i UTF-8-format med byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="9ee1d-161">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="9ee1d-162">`utf8NoBOM`: Kodar i UTF-8-format utan byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="9ee1d-162">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="9ee1d-163">`utf32`: Kodar i UTF-32-format.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-163">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="9ee1d-164">Från och med PowerShell 6,2 tillåter **encoding** -parametern även numeriska ID: n för registrerade tecken tabeller (som `-Encoding 1251` ) eller sträng namn för registrerade tecken tabeller (som `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="9ee1d-164">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="9ee1d-165">Mer information finns i .NET-dokumentationen för [encoding. codepage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span><span class="sxs-lookup"><span data-stu-id="9ee1d-165">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

> [!NOTE]
> <span data-ttu-id="9ee1d-166">**UTF-7** _ rekommenderas inte längre att använda.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-166">**UTF-7** _ is no longer recommended to use.</span></span> <span data-ttu-id="9ee1d-167">I PowerShell 7,1 skrivs en varning om du anger `utf7` för parametern _ \*encoding\*\*.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-167">In PowerShell 7.1, a warning is written if you specify `utf7` for the _ *Encoding*\* parameter.</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, BigEndianUTF32, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: 1
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9ee1d-168">-Sökväg</span><span class="sxs-lookup"><span data-stu-id="9ee1d-168">-FilePath</span></span>

<span data-ttu-id="9ee1d-169">Anger sökvägen till utdatafilen.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-169">Specifies the path to the output file.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases: Path

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9ee1d-170">-Force</span><span class="sxs-lookup"><span data-stu-id="9ee1d-170">-Force</span></span>

<span data-ttu-id="9ee1d-171">Åsidosätter det skrivskyddade attributet och skriver över en befintlig skrivskyddad fil.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-171">Overrides the read-only attribute and overwrites an existing read-only file.</span></span> <span data-ttu-id="9ee1d-172">**Force** -parametern åsidosätter inte säkerhets begränsningar.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-172">The **Force** parameter does not override security restrictions.</span></span>

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

### <span data-ttu-id="9ee1d-173">– InputObject</span><span class="sxs-lookup"><span data-stu-id="9ee1d-173">-InputObject</span></span>

<span data-ttu-id="9ee1d-174">Anger de objekt som ska skrivas till filen.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-174">Specifies the objects to be written to the file.</span></span> <span data-ttu-id="9ee1d-175">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-175">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="9ee1d-176">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="9ee1d-176">-LiteralPath</span></span>

<span data-ttu-id="9ee1d-177">Anger sökvägen till utdatafilen.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-177">Specifies the path to the output file.</span></span> <span data-ttu-id="9ee1d-178">Parametern **LiteralPath** används exakt som den har angetts.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-178">The **LiteralPath** parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="9ee1d-179">Jokertecken accepteras inte.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-179">Wildcard characters are not accepted.</span></span> <span data-ttu-id="9ee1d-180">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-180">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="9ee1d-181">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-181">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span> <span data-ttu-id="9ee1d-182">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="9ee1d-182">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="9ee1d-183">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="9ee1d-183">-NoClobber</span></span>

<span data-ttu-id="9ee1d-184">**NoClobber** förhindrar att en befintlig fil skrivs över och visar ett meddelande om att filen redan finns.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-184">**NoClobber** prevents an existing file from being overwritten and displays a message that the file already exists.</span></span> <span data-ttu-id="9ee1d-185">Om en fil finns på den angivna sökvägen skrivs filen som standard `Out-File` utan varning.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-185">By default, if a file exists in the specified path, `Out-File` overwrites the file without warning.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9ee1d-186">– NoNewline</span><span class="sxs-lookup"><span data-stu-id="9ee1d-186">-NoNewline</span></span>

<span data-ttu-id="9ee1d-187">Anger att innehållet som skrivs till filen inte slutar med ett rad matnings tecknet.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-187">Specifies that the content written to the file does not end with a newline character.</span></span> <span data-ttu-id="9ee1d-188">Sträng representationerna av indata-objekten sammanfogas för att bilda utdata.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-188">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="9ee1d-189">Inga blank steg eller newlines infogas mellan utgående strängar.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-189">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="9ee1d-190">Ingen ny rad läggs till efter den sista utgående strängen.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-190">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="9ee1d-191">-Bredd</span><span class="sxs-lookup"><span data-stu-id="9ee1d-191">-Width</span></span>

<span data-ttu-id="9ee1d-192">Anger antalet tecken i varje rad utdata.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-192">Specifies the number of characters in each line of output.</span></span> <span data-ttu-id="9ee1d-193">Eventuella ytterligare tecken trunkeras, inte omslutna.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-193">Any additional characters are truncated, not wrapped.</span></span> <span data-ttu-id="9ee1d-194">Om den här parametern inte används bestäms bredden av egenskaperna för värden.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-194">If this parameter is not used, the width is determined by the characteristics of the host.</span></span> <span data-ttu-id="9ee1d-195">Standardvärdet för PowerShell-konsolen är 80 tecken.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-195">The default for the PowerShell console is 80 characters.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9ee1d-196">-Confirm</span><span class="sxs-lookup"><span data-stu-id="9ee1d-196">-Confirm</span></span>

<span data-ttu-id="9ee1d-197">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-197">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="9ee1d-198">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="9ee1d-198">-WhatIf</span></span>

<span data-ttu-id="9ee1d-199">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-199">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="9ee1d-200">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-200">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="9ee1d-201">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9ee1d-201">CommonParameters</span></span>

<span data-ttu-id="9ee1d-202">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-202">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9ee1d-203">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9ee1d-203">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9ee1d-204">INDATA</span><span class="sxs-lookup"><span data-stu-id="9ee1d-204">INPUTS</span></span>

### <span data-ttu-id="9ee1d-205">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="9ee1d-205">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="9ee1d-206">Du kan skicka vidare alla objekt till `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="9ee1d-206">You can pipe any object to `Out-File`.</span></span>

## <span data-ttu-id="9ee1d-207">UTDATA</span><span class="sxs-lookup"><span data-stu-id="9ee1d-207">OUTPUTS</span></span>

### <span data-ttu-id="9ee1d-208">Inga</span><span class="sxs-lookup"><span data-stu-id="9ee1d-208">None</span></span>

<span data-ttu-id="9ee1d-209">`Out-File` genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-209">`Out-File` does not generate any output.</span></span>

## <span data-ttu-id="9ee1d-210">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="9ee1d-210">NOTES</span></span>

<span data-ttu-id="9ee1d-211">Inmatnings objekt formateras automatiskt som de skulle vara i terminalen, men du kan använda en- `Format-*` cmdlet för att styra formateringen av utdata direkt till filen.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-211">Input objects are automatically formatted as they would be in the terminal, but you can use a `Format-*` cmdlet to explicitly control the formatting of the output to the file.</span></span> <span data-ttu-id="9ee1d-212">Till exempel `Get-Date | Format-List | Out-File out.txt`</span><span class="sxs-lookup"><span data-stu-id="9ee1d-212">For example, `Get-Date | Format-List | Out-File out.txt`</span></span>

<span data-ttu-id="9ee1d-213">Använd pipelinen om du vill skicka ett PowerShell-kommandos utdata till `Out-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-213">To send a PowerShell command's output to the `Out-File` cmdlet, use the pipeline.</span></span> <span data-ttu-id="9ee1d-214">Alternativt kan du lagra data i en variabel och använda parametern **InputObject** för att skicka data till `Out-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-214">Alternatively, you can store data in a variable and use the **InputObject** parameter to pass data to the `Out-File` cmdlet.</span></span>

<span data-ttu-id="9ee1d-215">`Out-File` sparar data till en fil, men genererar inga utdata-objekt till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="9ee1d-215">`Out-File` saves data to a file but it does not produce any output objects to the pipeline.</span></span>

## <span data-ttu-id="9ee1d-216">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="9ee1d-216">RELATED LINKS</span></span>

[<span data-ttu-id="9ee1d-217">about_Providers</span><span class="sxs-lookup"><span data-stu-id="9ee1d-217">about_Providers</span></span>](../Microsoft.Powershell.Core/About/about_Providers.md)

[<span data-ttu-id="9ee1d-218">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="9ee1d-218">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="9ee1d-219">Ut-standard</span><span class="sxs-lookup"><span data-stu-id="9ee1d-219">Out-Default</span></span>](../Microsoft.PowerShell.Core/Out-Default.md)

[<span data-ttu-id="9ee1d-220">Ut-värd</span><span class="sxs-lookup"><span data-stu-id="9ee1d-220">Out-Host</span></span>](../Microsoft.PowerShell.Core/Out-Host.md)

[<span data-ttu-id="9ee1d-221">Ut-null</span><span class="sxs-lookup"><span data-stu-id="9ee1d-221">Out-Null</span></span>](../Microsoft.PowerShell.Core/Out-Null.md)

[<span data-ttu-id="9ee1d-222">Out-sträng</span><span class="sxs-lookup"><span data-stu-id="9ee1d-222">Out-String</span></span>](Out-String.md)

[<span data-ttu-id="9ee1d-223">Tee – objekt</span><span class="sxs-lookup"><span data-stu-id="9ee1d-223">Tee-Object</span></span>](Tee-Object.md)

