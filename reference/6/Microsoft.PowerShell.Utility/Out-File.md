---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-file?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-File
ms.openlocfilehash: f3cd58bffde8bcb6dab488a9e40e69d7435133e4
ms.sourcegitcommit: d757d64ea8c8af4d92596e8fbe15f2f40d48d3ac
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/22/2020
ms.locfileid: "93269577"
---
# <span data-ttu-id="3ab3c-103">Out-File</span><span class="sxs-lookup"><span data-stu-id="3ab3c-103">Out-File</span></span>

## <span data-ttu-id="3ab3c-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="3ab3c-104">SYNOPSIS</span></span>
<span data-ttu-id="3ab3c-105">Skickar utdata till en fil.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-105">Sends output to a file.</span></span>

## <span data-ttu-id="3ab3c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3ab3c-106">SYNTAX</span></span>

### <span data-ttu-id="3ab3c-107">ByPath (standard)</span><span class="sxs-lookup"><span data-stu-id="3ab3c-107">ByPath (Default)</span></span>

```
Out-File [-FilePath] <string> [[-Encoding] <Encoding>] [-Append] [-Force] [-NoClobber]
 [-Width <int>] [-NoNewline] [-InputObject <psobject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="3ab3c-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="3ab3c-108">ByLiteralPath</span></span>

```
Out-File [[-Encoding] <Encoding>] -LiteralPath <string> [-Append] [-Force] [-NoClobber]
 [-Width <int>] [-NoNewline] [-InputObject <psobject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="3ab3c-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="3ab3c-109">DESCRIPTION</span></span>

<span data-ttu-id="3ab3c-110">`Out-File`Cmdleten skickar utdata till en fil.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-110">The `Out-File` cmdlet sends output to a file.</span></span> <span data-ttu-id="3ab3c-111">Den använder implicit PowerShell: s format system för att skriva till filen.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-111">It implicitly uses PowerShell's formatting system to write to the file.</span></span> <span data-ttu-id="3ab3c-112">Filen får samma visnings representation som i terminalen.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-112">The file receives the same display representation as the terminal.</span></span> <span data-ttu-id="3ab3c-113">Det innebär att utmatningen kanske inte är idealisk för programmatisk bearbetning om inte alla indata är strängar.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-113">This means that the output may not be ideal for programmatic processing unless all input objects are strings.</span></span>
<span data-ttu-id="3ab3c-114">När du behöver ange parametrar för utdata använder du `Out-File` istället för omdirigerings operatorn ( `>` ).</span><span class="sxs-lookup"><span data-stu-id="3ab3c-114">When you need to specify parameters for the output, use `Out-File` rather than the redirection operator (`>`).</span></span> <span data-ttu-id="3ab3c-115">Mer information om omdirigering finns i [about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md).</span><span class="sxs-lookup"><span data-stu-id="3ab3c-115">For more information about redirection, see [about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md).</span></span>

## <span data-ttu-id="3ab3c-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="3ab3c-116">EXAMPLES</span></span>

### <span data-ttu-id="3ab3c-117">Exempel 1: skicka utdata och skapa en fil</span><span class="sxs-lookup"><span data-stu-id="3ab3c-117">Example 1: Send output and create a file</span></span>

<span data-ttu-id="3ab3c-118">Det här exemplet visar hur du skickar en lista över den lokala datorns processer till en fil.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-118">This example shows how to send a list of the local computer's processes to a file.</span></span> <span data-ttu-id="3ab3c-119">Om filen inte finns `Out-File` skapas filen på den angivna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-119">If the file does not exist, `Out-File` creates the file in the specified path.</span></span>

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

<span data-ttu-id="3ab3c-120">`Get-Process`Cmdleten hämtar listan över processer som körs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-120">The `Get-Process` cmdlet gets the list of processes running on the local computer.</span></span> <span data-ttu-id="3ab3c-121">**Process** objekt skickas ned pipelinen till `Out-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-121">The **Process** objects are sent down the pipeline to the `Out-File` cmdlet.</span></span> <span data-ttu-id="3ab3c-122">`Out-File` använder parametern **sökväg** och skapar en fil i den aktuella katalogen med namnet **Process.txt**.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-122">`Out-File` uses the **FilePath** parameter and creates a file in the current directory named **Process.txt**.</span></span> <span data-ttu-id="3ab3c-123">`Get-Content`Kommandot hämtar innehåll från filen och visar det i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-123">The `Get-Content` command gets content from the file and displays it in the PowerShell console.</span></span>

### <span data-ttu-id="3ab3c-124">Exempel 2: förhindra att en befintlig fil skrivs över</span><span class="sxs-lookup"><span data-stu-id="3ab3c-124">Example 2: Prevent an existing file from being overwritten</span></span>

<span data-ttu-id="3ab3c-125">Det här exemplet förhindrar att en befintlig fil skrivs över.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-125">This example prevents an existing file from being overwritten.</span></span> <span data-ttu-id="3ab3c-126">Som standard `Out-File` skriver över befintliga filer.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-126">By default, `Out-File` overwrites existing files.</span></span>

```powershell
Get-Process | Out-File -FilePath .\Process.txt -NoClobber
```

```Output
Out-File : The file 'C:\Test\Process.txt' already exists.
At line:1 char:15
+ Get-Process | Out-File -FilePath .\Process.txt -NoClobber
+               ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
```

<span data-ttu-id="3ab3c-127">`Get-Process`Cmdleten hämtar listan över processer som körs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-127">The `Get-Process` cmdlet gets the list of processes running on the local computer.</span></span> <span data-ttu-id="3ab3c-128">**Process** objekt skickas ned pipelinen till `Out-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-128">The **Process** objects are sent down the pipeline to the `Out-File` cmdlet.</span></span> <span data-ttu-id="3ab3c-129">`Out-File` använder parametern **sökväg** och försöker skriva till en fil i den aktuella katalogen med namnet **Process.txt**.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-129">`Out-File` uses the **FilePath** parameter and attempts to write to a file in the current directory named **Process.txt**.</span></span> <span data-ttu-id="3ab3c-130">Parametern **NoClobber** förhindrar att filen skrivs över och visar ett meddelande om att filen redan finns.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-130">The **NoClobber** parameter prevents the file from being overwritten and displays a message that the file already exists.</span></span>

### <span data-ttu-id="3ab3c-131">Exempel 3: skicka utdata till en fil i ASCII-format</span><span class="sxs-lookup"><span data-stu-id="3ab3c-131">Example 3: Send output to a file in ASCII format</span></span>

<span data-ttu-id="3ab3c-132">Det här exemplet visar hur du kodar utdata med en speciell kodnings typ.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-132">This example shows how to encode output with a specific encoding type.</span></span>

```powershell
$Procs = Get-Process
Out-File -FilePath .\Process.txt -InputObject $Procs -Encoding ASCII -Width 50
```

<span data-ttu-id="3ab3c-133">`Get-Process`Cmdleten hämtar listan över processer som körs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-133">The `Get-Process` cmdlet gets the list of processes running on the local computer.</span></span> <span data-ttu-id="3ab3c-134">**Process** objekt lagras i variabeln `$Procs` .</span><span class="sxs-lookup"><span data-stu-id="3ab3c-134">The **Process** objects are stored in the variable, `$Procs`.</span></span> <span data-ttu-id="3ab3c-135">`Out-File` använder parametern **sökväg** och skapar en fil i den aktuella katalogen med namnet **Process.txt**.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-135">`Out-File` uses the **FilePath** parameter and creates a file in the current directory named **Process.txt**.</span></span> <span data-ttu-id="3ab3c-136">**InputObject** -parametern överför process objekt `$Procs` till filen **Process.txt**.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-136">The **InputObject** parameter passes the process objects in `$Procs` to the file **Process.txt**.</span></span> <span data-ttu-id="3ab3c-137">**Encoding** -parametern konverterar utdata till **ASCII** -format.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-137">The **Encoding** parameter converts the output to **ASCII** format.</span></span> <span data-ttu-id="3ab3c-138">Parametern **width** begränsar varje rad i filen till 50 tecken så att vissa data kan trunkeras.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-138">The **Width** parameter limits each line in the file to 50 characters so some data might be truncated.</span></span>

### <span data-ttu-id="3ab3c-139">Exempel 4: Använd en provider och skicka utdata till en fil</span><span class="sxs-lookup"><span data-stu-id="3ab3c-139">Example 4: Use a provider and send output to a file</span></span>

<span data-ttu-id="3ab3c-140">Det här exemplet visar hur du använder `Out-File` cmdleten när du inte befinner dig i en **fil för fil Systems** leverantör.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-140">This example shows how to use the `Out-File` cmdlet when you are not in a **FileSystem** provider drive.</span></span> <span data-ttu-id="3ab3c-141">Använd `Get-PSProvider` cmdleten för att Visa providers på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-141">Use the `Get-PSProvider` cmdlet to view the providers on your local computer.</span></span> <span data-ttu-id="3ab3c-142">Mer information finns i [about_Providers](../Microsoft.Powershell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="3ab3c-142">For more information, see [about_Providers](../Microsoft.Powershell.Core/About/about_Providers.md).</span></span>

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

<span data-ttu-id="3ab3c-143">`Set-Location`Kommandot använder parametern **Path** för att ange den aktuella platsen för register leverantören `Alias:` .</span><span class="sxs-lookup"><span data-stu-id="3ab3c-143">The `Set-Location` command uses the **Path** parameter to set the current location to the registry provider `Alias:`.</span></span> <span data-ttu-id="3ab3c-144">`Get-Location`Cmdleten visar den fullständiga sökvägen för `Alias:` .</span><span class="sxs-lookup"><span data-stu-id="3ab3c-144">The `Get-Location` cmdlet displays the complete path for `Alias:`.</span></span>
<span data-ttu-id="3ab3c-145">`Get-ChildItem` skickar objekt nedåt i pipeline till `Out-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-145">`Get-ChildItem` sends objects down the pipeline to the `Out-File` cmdlet.</span></span> <span data-ttu-id="3ab3c-146">`Out-File` använder parametern **sökväg** för att ange den fullständiga sökvägen och fil namnet för utdata, **C:\TestDir\AliasNames.txt**.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-146">`Out-File` uses the **FilePath** parameter to specify the complete path and filename for the output, **C:\TestDir\AliasNames.txt**.</span></span> <span data-ttu-id="3ab3c-147">`Get-Content`Cmdleten använder parametern **Path** och visar filens innehåll i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-147">The `Get-Content` cmdlet uses the **Path** parameter and displays the file's content in the PowerShell console.</span></span>

## <span data-ttu-id="3ab3c-148">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="3ab3c-148">PARAMETERS</span></span>

### <span data-ttu-id="3ab3c-149">-Lägg till</span><span class="sxs-lookup"><span data-stu-id="3ab3c-149">-Append</span></span>

<span data-ttu-id="3ab3c-150">Lägger till utdata i slutet av en befintlig fil.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-150">Adds the output to the end of an existing file.</span></span>

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

### <span data-ttu-id="3ab3c-151">-Encoding</span><span class="sxs-lookup"><span data-stu-id="3ab3c-151">-Encoding</span></span>

<span data-ttu-id="3ab3c-152">Anger typ av kodning för mål filen.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-152">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="3ab3c-153">Standardvärdet är `utf8NoBOM`.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-153">The default value is `utf8NoBOM`.</span></span>

<span data-ttu-id="3ab3c-154">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="3ab3c-154">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="3ab3c-155">`ascii`: Använder kodningen för ASCII-teckenuppsättningen (7 bitar).</span><span class="sxs-lookup"><span data-stu-id="3ab3c-155">`ascii`: Uses the encoding for the ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="3ab3c-156">`bigendianunicode`: Kodar i UTF-16-format med big-endian byte-ordning.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-156">`bigendianunicode`: Encodes in UTF-16 format using the big-endian byte order.</span></span>
- <span data-ttu-id="3ab3c-157">`oem`: Använder standard kodning för MS-DOS-och-konsol program.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-157">`oem`: Uses the default encoding for MS-DOS and console programs.</span></span>
- <span data-ttu-id="3ab3c-158">`unicode`: Kodar i UTF-16-format med lite-endian-dataordning.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-158">`unicode`: Encodes in UTF-16 format using the little-endian byte order.</span></span>
- <span data-ttu-id="3ab3c-159">`utf7`: Kodar i UTF-7-format.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-159">`utf7`: Encodes in UTF-7 format.</span></span>
- <span data-ttu-id="3ab3c-160">`utf8`: Kodar i UTF-8-format.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-160">`utf8`: Encodes in UTF-8 format.</span></span>
- <span data-ttu-id="3ab3c-161">`utf8BOM`: Kodar i UTF-8-format med byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="3ab3c-161">`utf8BOM`: Encodes in UTF-8 format with Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="3ab3c-162">`utf8NoBOM`: Kodar i UTF-8-format utan byte ordnings tecken (BOM)</span><span class="sxs-lookup"><span data-stu-id="3ab3c-162">`utf8NoBOM`: Encodes in UTF-8 format without Byte Order Mark (BOM)</span></span>
- <span data-ttu-id="3ab3c-163">`utf32`: Kodar i UTF-32-format.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-163">`utf32`: Encodes in UTF-32 format.</span></span>

<span data-ttu-id="3ab3c-164">Från och med PowerShell 6,2 tillåter **encoding** -parametern även numeriska ID: n för registrerade tecken tabeller (som `-Encoding 1251` ) eller sträng namn för registrerade tecken tabeller (som `-Encoding "windows-1251"` ).</span><span class="sxs-lookup"><span data-stu-id="3ab3c-164">Beginning with PowerShell 6.2, the **Encoding** parameter also allows numeric IDs of registered code pages (like `-Encoding 1251`) or string names of registered code pages (like `-Encoding "windows-1251"`).</span></span> <span data-ttu-id="3ab3c-165">Mer information finns i .NET-dokumentationen för [encoding. codepage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span><span class="sxs-lookup"><span data-stu-id="3ab3c-165">For more information, see the .NET documentation for [Encoding.CodePage](/dotnet/api/system.text.encoding.codepage?view=netcore-2.2).</span></span>

```yaml
Type: System.Text.Encoding
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, OEM, Unicode, UTF7, UTF8, UTF8BOM, UTF8NoBOM, UTF32

Required: False
Position: 1
Default value: UTF8NoBOM
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3ab3c-166">-Sökväg</span><span class="sxs-lookup"><span data-stu-id="3ab3c-166">-FilePath</span></span>

<span data-ttu-id="3ab3c-167">Anger sökvägen till utdatafilen.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-167">Specifies the path to the output file.</span></span>

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

### <span data-ttu-id="3ab3c-168">-Force</span><span class="sxs-lookup"><span data-stu-id="3ab3c-168">-Force</span></span>

<span data-ttu-id="3ab3c-169">Åsidosätter det skrivskyddade attributet och skriver över en befintlig skrivskyddad fil.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-169">Overrides the read-only attribute and overwrites an existing read-only file.</span></span> <span data-ttu-id="3ab3c-170">**Force** -parametern åsidosätter inte säkerhets begränsningar.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-170">The **Force** parameter does not override security restrictions.</span></span>

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

### <span data-ttu-id="3ab3c-171">– InputObject</span><span class="sxs-lookup"><span data-stu-id="3ab3c-171">-InputObject</span></span>

<span data-ttu-id="3ab3c-172">Anger de objekt som ska skrivas till filen.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-172">Specifies the objects to be written to the file.</span></span> <span data-ttu-id="3ab3c-173">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-173">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="3ab3c-174">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="3ab3c-174">-LiteralPath</span></span>

<span data-ttu-id="3ab3c-175">Anger sökvägen till utdatafilen.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-175">Specifies the path to the output file.</span></span> <span data-ttu-id="3ab3c-176">Parametern **LiteralPath** används exakt som den har angetts.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-176">The **LiteralPath** parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="3ab3c-177">Jokertecken accepteras inte.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-177">Wildcard characters are not accepted.</span></span> <span data-ttu-id="3ab3c-178">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-178">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="3ab3c-179">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-179">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span> <span data-ttu-id="3ab3c-180">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="3ab3c-180">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="3ab3c-181">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="3ab3c-181">-NoClobber</span></span>

<span data-ttu-id="3ab3c-182">**NoClobber** förhindrar att en befintlig fil skrivs över och visar ett meddelande om att filen redan finns.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-182">**NoClobber** prevents an existing file from being overwritten and displays a message that the file already exists.</span></span> <span data-ttu-id="3ab3c-183">Om en fil finns på den angivna sökvägen skrivs filen som standard `Out-File` utan varning.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-183">By default, if a file exists in the specified path, `Out-File` overwrites the file without warning.</span></span>

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

### <span data-ttu-id="3ab3c-184">– NoNewline</span><span class="sxs-lookup"><span data-stu-id="3ab3c-184">-NoNewline</span></span>

<span data-ttu-id="3ab3c-185">Anger att innehållet som skrivs till filen inte slutar med ett rad matnings tecknet.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-185">Specifies that the content written to the file does not end with a newline character.</span></span> <span data-ttu-id="3ab3c-186">Sträng representationerna av indata-objekten sammanfogas för att bilda utdata.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-186">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="3ab3c-187">Inga blank steg eller newlines infogas mellan utgående strängar.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-187">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="3ab3c-188">Ingen ny rad läggs till efter den sista utgående strängen.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-188">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="3ab3c-189">-Bredd</span><span class="sxs-lookup"><span data-stu-id="3ab3c-189">-Width</span></span>

<span data-ttu-id="3ab3c-190">Anger antalet tecken i varje rad utdata.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-190">Specifies the number of characters in each line of output.</span></span> <span data-ttu-id="3ab3c-191">Eventuella ytterligare tecken trunkeras, inte omslutna.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-191">Any additional characters are truncated, not wrapped.</span></span> <span data-ttu-id="3ab3c-192">Om den här parametern inte används bestäms bredden av egenskaperna för värden.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-192">If this parameter is not used, the width is determined by the characteristics of the host.</span></span> <span data-ttu-id="3ab3c-193">Standardvärdet för PowerShell-konsolen är 80 tecken.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-193">The default for the PowerShell console is 80 characters.</span></span>

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

### <span data-ttu-id="3ab3c-194">-Confirm</span><span class="sxs-lookup"><span data-stu-id="3ab3c-194">-Confirm</span></span>

<span data-ttu-id="3ab3c-195">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-195">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="3ab3c-196">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="3ab3c-196">-WhatIf</span></span>

<span data-ttu-id="3ab3c-197">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-197">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="3ab3c-198">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-198">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="3ab3c-199">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3ab3c-199">CommonParameters</span></span>

<span data-ttu-id="3ab3c-200">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-200">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3ab3c-201">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="3ab3c-201">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3ab3c-202">INDATA</span><span class="sxs-lookup"><span data-stu-id="3ab3c-202">INPUTS</span></span>

### <span data-ttu-id="3ab3c-203">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="3ab3c-203">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="3ab3c-204">Du kan skicka vidare alla objekt till `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="3ab3c-204">You can pipe any object to `Out-File`.</span></span>

## <span data-ttu-id="3ab3c-205">UTDATA</span><span class="sxs-lookup"><span data-stu-id="3ab3c-205">OUTPUTS</span></span>

### <span data-ttu-id="3ab3c-206">Inget</span><span class="sxs-lookup"><span data-stu-id="3ab3c-206">None</span></span>

<span data-ttu-id="3ab3c-207">`Out-File` genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-207">`Out-File` does not generate any output.</span></span>

## <span data-ttu-id="3ab3c-208">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="3ab3c-208">NOTES</span></span>

<span data-ttu-id="3ab3c-209">Inmatnings objekt formateras automatiskt som de skulle vara i terminalen, men du kan använda en- `Format-*` cmdlet för att styra formateringen av utdata direkt till filen.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-209">Input objects are automatically formatted as they would be in the terminal, but you can use a `Format-*` cmdlet to explicitly control the formatting of the output to the file.</span></span> <span data-ttu-id="3ab3c-210">Till exempel `Get-Date | Format-List | Out-File out.txt`</span><span class="sxs-lookup"><span data-stu-id="3ab3c-210">For example, `Get-Date | Format-List | Out-File out.txt`</span></span>

<span data-ttu-id="3ab3c-211">Använd pipelinen om du vill skicka ett PowerShell-kommandos utdata till `Out-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-211">To send a PowerShell command's output to the `Out-File` cmdlet, use the pipeline.</span></span> <span data-ttu-id="3ab3c-212">Alternativt kan du lagra data i en variabel och använda parametern **InputObject** för att skicka data till `Out-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-212">Alternatively, you can store data in a variable and use the **InputObject** parameter to pass data to the `Out-File` cmdlet.</span></span>

<span data-ttu-id="3ab3c-213">`Out-File` sparar data till en fil, men genererar inga utdata-objekt till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="3ab3c-213">`Out-File` saves data to a file but it does not produce any output objects to the pipeline.</span></span>

## <span data-ttu-id="3ab3c-214">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="3ab3c-214">RELATED LINKS</span></span>

[<span data-ttu-id="3ab3c-215">about_Providers</span><span class="sxs-lookup"><span data-stu-id="3ab3c-215">about_Providers</span></span>](../Microsoft.Powershell.Core/About/about_Providers.md)

[<span data-ttu-id="3ab3c-216">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="3ab3c-216">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="3ab3c-217">Ut-standard</span><span class="sxs-lookup"><span data-stu-id="3ab3c-217">Out-Default</span></span>](../Microsoft.PowerShell.Core/Out-Default.md)

[<span data-ttu-id="3ab3c-218">Ut-värd</span><span class="sxs-lookup"><span data-stu-id="3ab3c-218">Out-Host</span></span>](../Microsoft.PowerShell.Core/Out-Host.md)

[<span data-ttu-id="3ab3c-219">Ut-null</span><span class="sxs-lookup"><span data-stu-id="3ab3c-219">Out-Null</span></span>](../Microsoft.PowerShell.Core/Out-Null.md)

[<span data-ttu-id="3ab3c-220">Out-sträng</span><span class="sxs-lookup"><span data-stu-id="3ab3c-220">Out-String</span></span>](Out-String.md)

[<span data-ttu-id="3ab3c-221">Tee – objekt</span><span class="sxs-lookup"><span data-stu-id="3ab3c-221">Tee-Object</span></span>](Tee-Object.md)
