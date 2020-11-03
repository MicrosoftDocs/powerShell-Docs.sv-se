---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-file?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-File
ms.openlocfilehash: 71602cb0621c835257f556a0a9db15bd754a3aee
ms.sourcegitcommit: d757d64ea8c8af4d92596e8fbe15f2f40d48d3ac
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/22/2020
ms.locfileid: "93269583"
---
# <span data-ttu-id="f9ac1-103">Out-File</span><span class="sxs-lookup"><span data-stu-id="f9ac1-103">Out-File</span></span>

## <span data-ttu-id="f9ac1-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="f9ac1-104">SYNOPSIS</span></span>
<span data-ttu-id="f9ac1-105">Skickar utdata till en fil.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-105">Sends output to a file.</span></span>

## <span data-ttu-id="f9ac1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f9ac1-106">SYNTAX</span></span>

### <span data-ttu-id="f9ac1-107">ByPath (standard)</span><span class="sxs-lookup"><span data-stu-id="f9ac1-107">ByPath (Default)</span></span>

```
Out-File [-FilePath] <string> [[-Encoding] <string>] [-Append] [-Force] [-NoClobber] [-Width <int>]
 [-NoNewline] [-InputObject <psobject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f9ac1-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="f9ac1-108">ByLiteralPath</span></span>

```
Out-File [[-Encoding] <string>] -LiteralPath <string> [-Append] [-Force] [-NoClobber] [-Width <int>]
 [-NoNewline] [-InputObject <psobject>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f9ac1-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="f9ac1-109">DESCRIPTION</span></span>

<span data-ttu-id="f9ac1-110">`Out-File`Cmdleten skickar utdata till en fil.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-110">The `Out-File` cmdlet sends output to a file.</span></span> <span data-ttu-id="f9ac1-111">Den använder implicit PowerShell: s format system för att skriva till filen.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-111">It implicitly uses PowerShell's formatting system to write to the file.</span></span> <span data-ttu-id="f9ac1-112">Filen får samma visnings representation som i terminalen.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-112">The file receives the same display representation as the terminal.</span></span> <span data-ttu-id="f9ac1-113">Det innebär att utmatningen kanske inte är idealisk för programmatisk bearbetning om inte alla indata är strängar.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-113">This means that the output may not be ideal for programmatic processing unless all input objects are strings.</span></span>
<span data-ttu-id="f9ac1-114">När du behöver ange parametrar för utdata använder du `Out-File` istället för omdirigerings operatorn ( `>` ).</span><span class="sxs-lookup"><span data-stu-id="f9ac1-114">When you need to specify parameters for the output, use `Out-File` rather than the redirection operator (`>`).</span></span> <span data-ttu-id="f9ac1-115">Mer information om omdirigering finns i [about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md).</span><span class="sxs-lookup"><span data-stu-id="f9ac1-115">For more information about redirection, see [about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md).</span></span>

## <span data-ttu-id="f9ac1-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="f9ac1-116">EXAMPLES</span></span>

### <span data-ttu-id="f9ac1-117">Exempel 1: skicka utdata och skapa en fil</span><span class="sxs-lookup"><span data-stu-id="f9ac1-117">Example 1: Send output and create a file</span></span>

<span data-ttu-id="f9ac1-118">Det här exemplet visar hur du skickar en lista över den lokala datorns processer till en fil.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-118">This example shows how to send a list of the local computer's processes to a file.</span></span> <span data-ttu-id="f9ac1-119">Om filen inte finns `Out-File` skapas filen på den angivna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-119">If the file does not exist, `Out-File` creates the file in the specified path.</span></span>

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

<span data-ttu-id="f9ac1-120">`Get-Process`Cmdleten hämtar listan över processer som körs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-120">The `Get-Process` cmdlet gets the list of processes running on the local computer.</span></span> <span data-ttu-id="f9ac1-121">**Process** objekt skickas ned pipelinen till `Out-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-121">The **Process** objects are sent down the pipeline to the `Out-File` cmdlet.</span></span> <span data-ttu-id="f9ac1-122">`Out-File` använder parametern **sökväg** och skapar en fil i den aktuella katalogen med namnet **Process.txt**.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-122">`Out-File` uses the **FilePath** parameter and creates a file in the current directory named **Process.txt**.</span></span> <span data-ttu-id="f9ac1-123">`Get-Content`Kommandot hämtar innehåll från filen och visar det i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-123">The `Get-Content` command gets content from the file and displays it in the PowerShell console.</span></span>

### <span data-ttu-id="f9ac1-124">Exempel 2: förhindra att en befintlig fil skrivs över</span><span class="sxs-lookup"><span data-stu-id="f9ac1-124">Example 2: Prevent an existing file from being overwritten</span></span>

<span data-ttu-id="f9ac1-125">Det här exemplet förhindrar att en befintlig fil skrivs över.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-125">This example prevents an existing file from being overwritten.</span></span> <span data-ttu-id="f9ac1-126">Som standard `Out-File` skriver över befintliga filer.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-126">By default, `Out-File` overwrites existing files.</span></span>

```powershell
Get-Process | Out-File -FilePath .\Process.txt -NoClobber
```

```Output
Out-File : The file 'C:\Test\Process.txt' already exists.
At line:1 char:15
+ Get-Process | Out-File -FilePath .\Process.txt -NoClobber
+               ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
```

<span data-ttu-id="f9ac1-127">`Get-Process`Cmdleten hämtar listan över processer som körs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-127">The `Get-Process` cmdlet gets the list of processes running on the local computer.</span></span> <span data-ttu-id="f9ac1-128">**Process** objekt skickas ned pipelinen till `Out-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-128">The **Process** objects are sent down the pipeline to the `Out-File` cmdlet.</span></span> <span data-ttu-id="f9ac1-129">`Out-File` använder parametern **sökväg** och försöker skriva till en fil i den aktuella katalogen med namnet **Process.txt**.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-129">`Out-File` uses the **FilePath** parameter and attempts to write to a file in the current directory named **Process.txt**.</span></span> <span data-ttu-id="f9ac1-130">Parametern **NoClobber** förhindrar att filen skrivs över och visar ett meddelande om att filen redan finns.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-130">The **NoClobber** parameter prevents the file from being overwritten and displays a message that the file already exists.</span></span>

### <span data-ttu-id="f9ac1-131">Exempel 3: skicka utdata till en fil i ASCII-format</span><span class="sxs-lookup"><span data-stu-id="f9ac1-131">Example 3: Send output to a file in ASCII format</span></span>

<span data-ttu-id="f9ac1-132">Det här exemplet visar hur du kodar utdata med en speciell kodnings typ.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-132">This example shows how to encode output with a specific encoding type.</span></span>

```powershell
$Procs = Get-Process
Out-File -FilePath .\Process.txt -InputObject $Procs -Encoding ASCII -Width 50
```

<span data-ttu-id="f9ac1-133">`Get-Process`Cmdleten hämtar listan över processer som körs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-133">The `Get-Process` cmdlet gets the list of processes running on the local computer.</span></span> <span data-ttu-id="f9ac1-134">**Process** objekt lagras i variabeln `$Procs` .</span><span class="sxs-lookup"><span data-stu-id="f9ac1-134">The **Process** objects are stored in the variable, `$Procs`.</span></span> <span data-ttu-id="f9ac1-135">`Out-File` använder parametern **sökväg** och skapar en fil i den aktuella katalogen med namnet **Process.txt**.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-135">`Out-File` uses the **FilePath** parameter and creates a file in the current directory named **Process.txt**.</span></span> <span data-ttu-id="f9ac1-136">**InputObject** -parametern överför process objekt `$Procs` till filen **Process.txt**.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-136">The **InputObject** parameter passes the process objects in `$Procs` to the file **Process.txt**.</span></span> <span data-ttu-id="f9ac1-137">**Encoding** -parametern konverterar utdata till **ASCII** -format.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-137">The **Encoding** parameter converts the output to **ASCII** format.</span></span> <span data-ttu-id="f9ac1-138">Parametern **width** begränsar varje rad i filen till 50 tecken så att vissa data kan trunkeras.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-138">The **Width** parameter limits each line in the file to 50 characters so some data might be truncated.</span></span>

### <span data-ttu-id="f9ac1-139">Exempel 4: Använd en provider och skicka utdata till en fil</span><span class="sxs-lookup"><span data-stu-id="f9ac1-139">Example 4: Use a provider and send output to a file</span></span>

<span data-ttu-id="f9ac1-140">Det här exemplet visar hur du använder `Out-File` cmdleten när du inte befinner dig i en **fil för fil Systems** leverantör.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-140">This example shows how to use the `Out-File` cmdlet when you are not in a **FileSystem** provider drive.</span></span> <span data-ttu-id="f9ac1-141">Använd `Get-PSProvider` cmdleten för att Visa providers på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-141">Use the `Get-PSProvider` cmdlet to view the providers on your local computer.</span></span> <span data-ttu-id="f9ac1-142">Mer information finns i [about_Providers](../Microsoft.Powershell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="f9ac1-142">For more information, see [about_Providers](../Microsoft.Powershell.Core/About/about_Providers.md).</span></span>

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

<span data-ttu-id="f9ac1-143">`Set-Location`Kommandot använder parametern **Path** för att ange den aktuella platsen för register leverantören `Alias:` .</span><span class="sxs-lookup"><span data-stu-id="f9ac1-143">The `Set-Location` command uses the **Path** parameter to set the current location to the registry provider `Alias:`.</span></span> <span data-ttu-id="f9ac1-144">`Get-Location`Cmdleten visar den fullständiga sökvägen för `Alias:` .</span><span class="sxs-lookup"><span data-stu-id="f9ac1-144">The `Get-Location` cmdlet displays the complete path for `Alias:`.</span></span>
<span data-ttu-id="f9ac1-145">`Get-ChildItem` skickar objekt nedåt i pipeline till `Out-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-145">`Get-ChildItem` sends objects down the pipeline to the `Out-File` cmdlet.</span></span> <span data-ttu-id="f9ac1-146">`Out-File` använder parametern **sökväg** för att ange den fullständiga sökvägen och fil namnet för utdata, **C:\TestDir\AliasNames.txt**.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-146">`Out-File` uses the **FilePath** parameter to specify the complete path and filename for the output, **C:\TestDir\AliasNames.txt**.</span></span> <span data-ttu-id="f9ac1-147">`Get-Content`Cmdleten använder parametern **Path** och visar filens innehåll i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-147">The `Get-Content` cmdlet uses the **Path** parameter and displays the file's content in the PowerShell console.</span></span>

## <span data-ttu-id="f9ac1-148">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="f9ac1-148">PARAMETERS</span></span>

### <span data-ttu-id="f9ac1-149">-Lägg till</span><span class="sxs-lookup"><span data-stu-id="f9ac1-149">-Append</span></span>

<span data-ttu-id="f9ac1-150">Lägger till utdata i slutet av en befintlig fil.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-150">Adds the output to the end of an existing file.</span></span> <span data-ttu-id="f9ac1-151">Om ingen **kodning** anges använder cmdlet: en standard kodning.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-151">If no **Encoding** is specified, the cmdlet uses the default encoding.</span></span> <span data-ttu-id="f9ac1-152">Kodningen kanske inte matchar mål filens kodning.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-152">That encoding may not match the encoding of the target file.</span></span> <span data-ttu-id="f9ac1-153">Detta är samma sak som omdirigerings operatorn ( `>>` ).</span><span class="sxs-lookup"><span data-stu-id="f9ac1-153">This is the same behavior as the redirection operator (`>>`).</span></span>

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

### <span data-ttu-id="f9ac1-154">-Encoding</span><span class="sxs-lookup"><span data-stu-id="f9ac1-154">-Encoding</span></span>

<span data-ttu-id="f9ac1-155">Anger typ av kodning för mål filen.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-155">Specifies the type of encoding for the target file.</span></span> <span data-ttu-id="f9ac1-156">Standardvärdet är `unicode`.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-156">The default value is `unicode`.</span></span>

<span data-ttu-id="f9ac1-157">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="f9ac1-157">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="f9ac1-158">`ascii` Använder ASCII-teckenuppsättning (7-bitars).</span><span class="sxs-lookup"><span data-stu-id="f9ac1-158">`ascii` Uses ASCII (7-bit) character set.</span></span>
- <span data-ttu-id="f9ac1-159">`bigendianunicode` Använder UTF-16 med big-endian byte-ordningen.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-159">`bigendianunicode` Uses UTF-16 with the big-endian byte order.</span></span>
- <span data-ttu-id="f9ac1-160">`default` Använder kodningen som motsvarar systemets aktiva tecken tabell (vanligt vis ANSI).</span><span class="sxs-lookup"><span data-stu-id="f9ac1-160">`default` Uses the encoding that corresponds to the system's active code page (usually ANSI).</span></span>
- <span data-ttu-id="f9ac1-161">`oem` Använder kodningen som motsvarar systemets aktuella OEM Code-sida.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-161">`oem` Uses the encoding that corresponds to the system's current OEM code page.</span></span>
- <span data-ttu-id="f9ac1-162">`string` Samma som `unicode` .</span><span class="sxs-lookup"><span data-stu-id="f9ac1-162">`string` Same as `unicode`.</span></span>
- <span data-ttu-id="f9ac1-163">`unicode` Använder UTF-16 med en liten-endian-order.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-163">`unicode` Uses UTF-16 with the little-endian byte order.</span></span>
- <span data-ttu-id="f9ac1-164">`unknown` Samma som `unicode` .</span><span class="sxs-lookup"><span data-stu-id="f9ac1-164">`unknown` Same as `unicode`.</span></span>
- <span data-ttu-id="f9ac1-165">`utf7` Använder UTF-7.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-165">`utf7` Uses UTF-7.</span></span>
- <span data-ttu-id="f9ac1-166">`utf8` Använder UTF-8.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-166">`utf8` Uses UTF-8.</span></span>
- <span data-ttu-id="f9ac1-167">`utf32` Använder UTF-32 med en liten-endian-order.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-167">`utf32` Uses UTF-32 with the little-endian byte order.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: ASCII, BigEndianUnicode, Default, OEM, String, Unicode, Unknown, UTF7, UTF8, UTF32

Required: False
Position: 1
Default value: Unicode
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f9ac1-168">-Sökväg</span><span class="sxs-lookup"><span data-stu-id="f9ac1-168">-FilePath</span></span>

<span data-ttu-id="f9ac1-169">Anger sökvägen till utdatafilen.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-169">Specifies the path to the output file.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f9ac1-170">-Force</span><span class="sxs-lookup"><span data-stu-id="f9ac1-170">-Force</span></span>

<span data-ttu-id="f9ac1-171">Åsidosätter det skrivskyddade attributet och skriver över en befintlig skrivskyddad fil.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-171">Overrides the read-only attribute and overwrites an existing read-only file.</span></span> <span data-ttu-id="f9ac1-172">**Force** -parametern åsidosätter inte säkerhets begränsningar.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-172">The **Force** parameter does not override security restrictions.</span></span>

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

### <span data-ttu-id="f9ac1-173">– InputObject</span><span class="sxs-lookup"><span data-stu-id="f9ac1-173">-InputObject</span></span>

<span data-ttu-id="f9ac1-174">Anger de objekt som ska skrivas till filen.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-174">Specifies the objects to be written to the file.</span></span> <span data-ttu-id="f9ac1-175">Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-175">Enter a variable that contains the objects or type a command or expression that gets the objects.</span></span>

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

### <span data-ttu-id="f9ac1-176">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="f9ac1-176">-LiteralPath</span></span>

<span data-ttu-id="f9ac1-177">Anger sökvägen till utdatafilen.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-177">Specifies the path to the output file.</span></span> <span data-ttu-id="f9ac1-178">Parametern **LiteralPath** används exakt som den har angetts.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-178">The **LiteralPath** parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="f9ac1-179">Jokertecken accepteras inte.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-179">Wildcard characters are not accepted.</span></span> <span data-ttu-id="f9ac1-180">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-180">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="f9ac1-181">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-181">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span> <span data-ttu-id="f9ac1-182">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="f9ac1-182">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f9ac1-183">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="f9ac1-183">-NoClobber</span></span>

<span data-ttu-id="f9ac1-184">**NoClobber** förhindrar att en befintlig fil skrivs över och visar ett meddelande om att filen redan finns.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-184">**NoClobber** prevents an existing file from being overwritten and displays a message that the file already exists.</span></span> <span data-ttu-id="f9ac1-185">Om en fil finns på den angivna sökvägen skrivs filen som standard `Out-File` utan varning.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-185">By default, if a file exists in the specified path, `Out-File` overwrites the file without warning.</span></span>

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

### <span data-ttu-id="f9ac1-186">– NoNewline</span><span class="sxs-lookup"><span data-stu-id="f9ac1-186">-NoNewline</span></span>

<span data-ttu-id="f9ac1-187">Anger att innehållet som skrivs till filen inte slutar med ett rad matnings tecknet.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-187">Specifies that the content written to the file does not end with a newline character.</span></span> <span data-ttu-id="f9ac1-188">Sträng representationerna av indata-objekten sammanfogas för att bilda utdata.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-188">The string representations of the input objects are concatenated to form the output.</span></span> <span data-ttu-id="f9ac1-189">Inga blank steg eller newlines infogas mellan utgående strängar.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-189">No spaces or newlines are inserted between the output strings.</span></span> <span data-ttu-id="f9ac1-190">Ingen ny rad läggs till efter den sista utgående strängen.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-190">No newline is added after the last output string.</span></span>

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

### <span data-ttu-id="f9ac1-191">-Bredd</span><span class="sxs-lookup"><span data-stu-id="f9ac1-191">-Width</span></span>

<span data-ttu-id="f9ac1-192">Anger antalet tecken i varje rad utdata.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-192">Specifies the number of characters in each line of output.</span></span> <span data-ttu-id="f9ac1-193">Eventuella ytterligare tecken trunkeras, inte omslutna.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-193">Any additional characters are truncated, not wrapped.</span></span> <span data-ttu-id="f9ac1-194">Om den här parametern inte används bestäms bredden av egenskaperna för värden.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-194">If this parameter is not used, the width is determined by the characteristics of the host.</span></span> <span data-ttu-id="f9ac1-195">Standardvärdet för PowerShell-konsolen är 80 tecken.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-195">The default for the PowerShell console is 80 characters.</span></span>

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

### <span data-ttu-id="f9ac1-196">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f9ac1-196">-Confirm</span></span>

<span data-ttu-id="f9ac1-197">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-197">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f9ac1-198">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f9ac1-198">-WhatIf</span></span>

<span data-ttu-id="f9ac1-199">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-199">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="f9ac1-200">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-200">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="f9ac1-201">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f9ac1-201">CommonParameters</span></span>

<span data-ttu-id="f9ac1-202">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-202">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f9ac1-203">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f9ac1-203">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f9ac1-204">INDATA</span><span class="sxs-lookup"><span data-stu-id="f9ac1-204">INPUTS</span></span>

### <span data-ttu-id="f9ac1-205">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="f9ac1-205">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="f9ac1-206">Du kan skicka vidare alla objekt till `Out-File` .</span><span class="sxs-lookup"><span data-stu-id="f9ac1-206">You can pipe any object to `Out-File`.</span></span>

## <span data-ttu-id="f9ac1-207">UTDATA</span><span class="sxs-lookup"><span data-stu-id="f9ac1-207">OUTPUTS</span></span>

### <span data-ttu-id="f9ac1-208">Inget</span><span class="sxs-lookup"><span data-stu-id="f9ac1-208">None</span></span>

<span data-ttu-id="f9ac1-209">`Out-File` genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-209">`Out-File` does not generate any output.</span></span>

## <span data-ttu-id="f9ac1-210">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="f9ac1-210">NOTES</span></span>

<span data-ttu-id="f9ac1-211">Inmatnings objekt formateras automatiskt som de skulle vara i terminalen, men du kan använda en- `Format-*` cmdlet för att styra formateringen av utdata direkt till filen.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-211">Input objects are automatically formatted as they would be in the terminal, but you can use a `Format-*` cmdlet to explicitly control the formatting of the output to the file.</span></span> <span data-ttu-id="f9ac1-212">Till exempel `Get-Date | Format-List | Out-File out.txt`</span><span class="sxs-lookup"><span data-stu-id="f9ac1-212">For example, `Get-Date | Format-List | Out-File out.txt`</span></span>

<span data-ttu-id="f9ac1-213">Använd pipelinen om du vill skicka ett PowerShell-kommandos utdata till `Out-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-213">To send a PowerShell command's output to the `Out-File` cmdlet, use the pipeline.</span></span> <span data-ttu-id="f9ac1-214">Alternativt kan du lagra data i en variabel och använda parametern **InputObject** för att skicka data till `Out-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-214">Alternatively, you can store data in a variable and use the **InputObject** parameter to pass data to the `Out-File` cmdlet.</span></span>

<span data-ttu-id="f9ac1-215">`Out-File` sparar data till en fil, men genererar inga utdata-objekt till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="f9ac1-215">`Out-File` saves data to a file but it does not produce any output objects to the pipeline.</span></span>

## <span data-ttu-id="f9ac1-216">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="f9ac1-216">RELATED LINKS</span></span>

[<span data-ttu-id="f9ac1-217">about_Providers</span><span class="sxs-lookup"><span data-stu-id="f9ac1-217">about_Providers</span></span>](../Microsoft.Powershell.Core/About/about_Providers.md)

[<span data-ttu-id="f9ac1-218">about_Quoting_Rules</span><span class="sxs-lookup"><span data-stu-id="f9ac1-218">about_Quoting_Rules</span></span>](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md)

[<span data-ttu-id="f9ac1-219">Ut-standard</span><span class="sxs-lookup"><span data-stu-id="f9ac1-219">Out-Default</span></span>](../Microsoft.PowerShell.Core/Out-Default.md)

[<span data-ttu-id="f9ac1-220">Out-GridView</span><span class="sxs-lookup"><span data-stu-id="f9ac1-220">Out-GridView</span></span>](Out-GridView.md)

[<span data-ttu-id="f9ac1-221">Ut-värd</span><span class="sxs-lookup"><span data-stu-id="f9ac1-221">Out-Host</span></span>](../Microsoft.PowerShell.Core/Out-Host.md)

[<span data-ttu-id="f9ac1-222">Ut-null</span><span class="sxs-lookup"><span data-stu-id="f9ac1-222">Out-Null</span></span>](../Microsoft.PowerShell.Core/Out-Null.md)

[<span data-ttu-id="f9ac1-223">Out-Printer</span><span class="sxs-lookup"><span data-stu-id="f9ac1-223">Out-Printer</span></span>](Out-Printer.md)

[<span data-ttu-id="f9ac1-224">Out-sträng</span><span class="sxs-lookup"><span data-stu-id="f9ac1-224">Out-String</span></span>](Out-String.md)

[<span data-ttu-id="f9ac1-225">Tee – objekt</span><span class="sxs-lookup"><span data-stu-id="f9ac1-225">Tee-Object</span></span>](Tee-Object.md)
