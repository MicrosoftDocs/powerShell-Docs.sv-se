---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 03/22/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/test-path?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Test-Path
ms.openlocfilehash: f31b4242d8febd4fdd0e03596d7394ab2990ddbb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263703"
---
# <span data-ttu-id="32d2f-103">Test-Path</span><span class="sxs-lookup"><span data-stu-id="32d2f-103">Test-Path</span></span>

## <span data-ttu-id="32d2f-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="32d2f-104">SYNOPSIS</span></span>
<span data-ttu-id="32d2f-105">Anger om alla element i en sökväg finns.</span><span class="sxs-lookup"><span data-stu-id="32d2f-105">Determines whether all elements of a path exist.</span></span>

## <span data-ttu-id="32d2f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="32d2f-106">SYNTAX</span></span>

### <span data-ttu-id="32d2f-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="32d2f-107">Path (Default)</span></span>

```
Test-Path [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-PathType <TestPathType>] [-IsValid] [-Credential <PSCredential>]
 [-OlderThan <DateTime>] [-NewerThan <DateTime>] [<CommonParameters>]
```

### <span data-ttu-id="32d2f-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="32d2f-108">LiteralPath</span></span>

```
Test-Path -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-PathType <TestPathType>] [-IsValid] [-Credential <PSCredential>]
 [-OlderThan <DateTime>] [-NewerThan <DateTime>] [<CommonParameters>]
```

## <span data-ttu-id="32d2f-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="32d2f-109">DESCRIPTION</span></span>

<span data-ttu-id="32d2f-110">`Test-Path`Cmdleten avgör om alla element i sökvägen finns.</span><span class="sxs-lookup"><span data-stu-id="32d2f-110">The `Test-Path` cmdlet determines whether all elements of the path exist.</span></span> <span data-ttu-id="32d2f-111">Den returnerar `$True` om alla element finns och `$False` om några saknas.</span><span class="sxs-lookup"><span data-stu-id="32d2f-111">It returns `$True` if all elements exist and `$False` if any are missing.</span></span> <span data-ttu-id="32d2f-112">Det kan också avgöra om sökvägen är giltig och om sökvägen leder till en behållare eller ett terminal-eller löv element.</span><span class="sxs-lookup"><span data-stu-id="32d2f-112">It can also tell whether the path syntax is valid and whether the path leads to a container or a terminal or leaf element.</span></span> <span data-ttu-id="32d2f-113">Om `Path` är blank steg är en tom sträng `$False` tillbaka.</span><span class="sxs-lookup"><span data-stu-id="32d2f-113">If the `Path` is whitespace an empty string, then `$False` is returned.</span></span> <span data-ttu-id="32d2f-114">Om matrisen `Path` är `$null` , matrisen för `$null` eller en tom matris returneras ett icke-avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="32d2f-114">If the `Path` is `$null`, array of `$null` or empty array, a non-terminating error is returned.</span></span>

## <span data-ttu-id="32d2f-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="32d2f-115">EXAMPLES</span></span>

### <span data-ttu-id="32d2f-116">Exempel 1: testa en bana</span><span class="sxs-lookup"><span data-stu-id="32d2f-116">Example 1: Test a path</span></span>

```powershell
Test-Path -Path "C:\Documents and Settings\DavidC"
```

```Output
True
```

<span data-ttu-id="32d2f-117">Det här kommandot kontrollerar om alla element i sökvägen finns, det vill säga katalogen C:, katalogen Documents and Settings och katalogen DavidC.</span><span class="sxs-lookup"><span data-stu-id="32d2f-117">This command checks whether all elements in the path exist, that is, the C: directory, the Documents and Settings directory, and the DavidC directory.</span></span> <span data-ttu-id="32d2f-118">Om några saknas returnerar cmdleten `$False` .</span><span class="sxs-lookup"><span data-stu-id="32d2f-118">If any are missing, the cmdlet returns `$False`.</span></span>
<span data-ttu-id="32d2f-119">Annars returneras `$True` .</span><span class="sxs-lookup"><span data-stu-id="32d2f-119">Otherwise, it returns `$True`.</span></span>

### <span data-ttu-id="32d2f-120">Exempel 2: testa sökvägen till en profil</span><span class="sxs-lookup"><span data-stu-id="32d2f-120">Example 2: Test the path of a profile</span></span>

```powershell
Test-Path -Path $profile
```

```Output
False
```

```powershell
Test-Path -Path $profile -IsValid
```

```Output
True
```

<span data-ttu-id="32d2f-121">De här kommandona testar sökvägen till PowerShell-profilen.</span><span class="sxs-lookup"><span data-stu-id="32d2f-121">These commands test the path of the PowerShell profile.</span></span>

<span data-ttu-id="32d2f-122">Det första kommandot avgör om alla element i sökvägen finns.</span><span class="sxs-lookup"><span data-stu-id="32d2f-122">The first command determines whether all elements in the path exist.</span></span> <span data-ttu-id="32d2f-123">Det andra kommandot avgör om syntaxen för sökvägen är korrekt.</span><span class="sxs-lookup"><span data-stu-id="32d2f-123">The second command determines whether the syntax of the path is correct.</span></span> <span data-ttu-id="32d2f-124">I det här fallet är sökvägen `$False` , men syntaxen är korrekt `$True` .</span><span class="sxs-lookup"><span data-stu-id="32d2f-124">In this case, the path is `$False`, but the syntax is correct `$True`.</span></span> <span data-ttu-id="32d2f-125">Dessa kommandon använder `$profile` sig av den automatiska variabeln som pekar på profilens plats, även om profilen inte finns.</span><span class="sxs-lookup"><span data-stu-id="32d2f-125">These commands use `$profile`, the automatic variable that points to the location for the profile, even if the profile does not exist.</span></span>

<span data-ttu-id="32d2f-126">Mer information om automatiska variabler finns i about_Automatic_Variables.</span><span class="sxs-lookup"><span data-stu-id="32d2f-126">For more information about automatic variables, see about_Automatic_Variables.</span></span>

### <span data-ttu-id="32d2f-127">Exempel 3: kontrol lera om det finns några filer förutom en angiven typ</span><span class="sxs-lookup"><span data-stu-id="32d2f-127">Example 3: Check whether there are any files besides a specified type</span></span>

```powershell
Test-Path -Path "C:\CAD\Commercial Buildings\*" -Exclude *.dwg
```

```Output
False
```

<span data-ttu-id="32d2f-128">Det här kommandot kontrollerar om det finns några filer i katalogen för kommersiella byggnader än. DWG-filer.</span><span class="sxs-lookup"><span data-stu-id="32d2f-128">This command checks whether there are any files in the Commercial Buildings directory other than .dwg files.</span></span>

<span data-ttu-id="32d2f-129">Kommandot använder parametern **Path** för att ange sökvägen.</span><span class="sxs-lookup"><span data-stu-id="32d2f-129">The command uses the **Path** parameter to specify the path.</span></span> <span data-ttu-id="32d2f-130">Eftersom sökvägen innehåller ett blank steg omges sökvägen av citat tecken.</span><span class="sxs-lookup"><span data-stu-id="32d2f-130">Because the path includes a space, the path is enclosed in quotation marks.</span></span> <span data-ttu-id="32d2f-131">Asterisken i slutet av sökvägen visar innehållet i den kommersiella skapande katalogen.</span><span class="sxs-lookup"><span data-stu-id="32d2f-131">The asterisk at the end of the path indicates the contents of the Commercial Building directory.</span></span> <span data-ttu-id="32d2f-132">Med långa sökvägar, till exempel den här, skriver du de första bokstäverna i sökvägen och använder sedan TABB-tangenten för att slutföra sökvägen.</span><span class="sxs-lookup"><span data-stu-id="32d2f-132">With long paths, such as this one, type the first few letters of the path, and then use the TAB key to complete the path.</span></span>

<span data-ttu-id="32d2f-133">Kommandot anger parametern **exclude** för att ange filer som ska utelämnas från utvärderingen.</span><span class="sxs-lookup"><span data-stu-id="32d2f-133">The command specifies the **Exclude** parameter to specify files that will be omitted from the evaluation.</span></span>

<span data-ttu-id="32d2f-134">I det här fallet, eftersom katalogen bara innehåller. DWG-filer, blir resultatet `$False` .</span><span class="sxs-lookup"><span data-stu-id="32d2f-134">In this case, because the directory contains only .dwg files, the result is `$False`.</span></span>

### <span data-ttu-id="32d2f-135">Exempel 4: Sök efter en fil</span><span class="sxs-lookup"><span data-stu-id="32d2f-135">Example 4: Check for a file</span></span>

```powershell
Test-Path -Path $profile -PathType leaf
```

```Output
True
```

<span data-ttu-id="32d2f-136">Det här kommandot kontrollerar om sökvägen som lagras i `$profile` variabeln leder till en fil.</span><span class="sxs-lookup"><span data-stu-id="32d2f-136">This command checks whether the path stored in the `$profile` variable leads to a file.</span></span> <span data-ttu-id="32d2f-137">I det här fallet, eftersom PowerShell-profilen är en `.ps1` fil, returnerar cmdleten `$True` .</span><span class="sxs-lookup"><span data-stu-id="32d2f-137">In this case, because the PowerShell profile is a `.ps1` file, the cmdlet returns `$True`.</span></span>

### <span data-ttu-id="32d2f-138">Exempel 5: kontrol lera sökvägar i registret</span><span class="sxs-lookup"><span data-stu-id="32d2f-138">Example 5: Check paths in the Registry</span></span>

<span data-ttu-id="32d2f-139">Dessa kommandon används `Test-Path` med PowerShell-dataprovidern.</span><span class="sxs-lookup"><span data-stu-id="32d2f-139">These commands use `Test-Path` with the PowerShell registry provider.</span></span>

<span data-ttu-id="32d2f-140">Det första kommandot testar om register Sök vägen för register nyckeln för **Microsoft. PowerShell** är korrekt i systemet.</span><span class="sxs-lookup"><span data-stu-id="32d2f-140">The first command tests whether the registry path of the **Microsoft.PowerShell** registry key is correct on the system.</span></span> <span data-ttu-id="32d2f-141">Om PowerShell är korrekt installerat returnerar cmdleten `$True` .</span><span class="sxs-lookup"><span data-stu-id="32d2f-141">If PowerShell is installed correctly, the cmdlet returns `$True`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="32d2f-142">`Test-Path` fungerar inte korrekt med alla PowerShell-leverantörer.</span><span class="sxs-lookup"><span data-stu-id="32d2f-142">`Test-Path` does not work correctly with all PowerShell providers.</span></span> <span data-ttu-id="32d2f-143">Du kan till exempel använda `Test-Path` för att testa sökvägen till en register nyckel, men om du använder den för att testa sökvägen till en register post returneras den alltid `$False` , även om register posten finns.</span><span class="sxs-lookup"><span data-stu-id="32d2f-143">For example, you can use `Test-Path` to test the path of a registry key, but if you use it to test the path of a registry entry, it always returns `$False`, even if the registry entry is present.</span></span>

```powershell
Test-Path -Path "HKLM:\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell"
```

```Output
True
```

```powershell
Test-Path -Path "HKLM:\Software\Microsoft\PowerShell\1\ShellIds\Microsoft.PowerShell\ExecutionPolicy"
```

```Output
False
```

### <span data-ttu-id="32d2f-144">Exempel 6: testa om en fil är nyare än ett angivet datum</span><span class="sxs-lookup"><span data-stu-id="32d2f-144">Example 6: Test if a file is newer than a specified date</span></span>

<span data-ttu-id="32d2f-145">Det här kommandot använder parametern **NewerThan** Dynamic för att avgöra om filen PowerShell.exe på datorn är nyare än den 13 juli 2009.</span><span class="sxs-lookup"><span data-stu-id="32d2f-145">This command uses the **NewerThan** dynamic parameter to determine whether the "PowerShell.exe" file on the computer is newer than "July 13, 2009".</span></span>

<span data-ttu-id="32d2f-146">Parametern NewerThan fungerar bara i fil system enheter.</span><span class="sxs-lookup"><span data-stu-id="32d2f-146">The NewerThan parameter works only in file system drives.</span></span>

```powershell
Test-Path $pshome\PowerShell.exe -NewerThan "July 13, 2009"
```

```Output
True
```

### <span data-ttu-id="32d2f-147">Exempel 7: testa en sökväg med null som värde</span><span class="sxs-lookup"><span data-stu-id="32d2f-147">Example 7: Test a path with null as the value</span></span>

<span data-ttu-id="32d2f-148">Felet som returnerades för `null` , matrisen `null` eller den tomma matrisen är ett icke-avslutande fel.</span><span class="sxs-lookup"><span data-stu-id="32d2f-148">The error returned for `null`, array of `null` or empty array is a non-terminating error.</span></span> <span data-ttu-id="32d2f-149">Det kan vara undertryckt med `-ErrorAction SilentlyContinue` .</span><span class="sxs-lookup"><span data-stu-id="32d2f-149">It can be suppress by using `-ErrorAction SilentlyContinue`.</span></span> <span data-ttu-id="32d2f-150">I följande exempel visas alla fall där felet returneras `NullPathNotPermitted` .</span><span class="sxs-lookup"><span data-stu-id="32d2f-150">The following example shows all cases which return the `NullPathNotPermitted` error.</span></span>

```powershell
Test-Path $null
Test-Path $null, $null
Test-Path @()
```

```Output
Test-Path : Cannot bind argument to parameter 'Path' because it is null.
At line:1 char:11
+ Test-Path $null
+           ~~~~~
    + CategoryInfo          : InvalidData: (:) [Test-Path], ParameterBindingValidationException
    + FullyQualifiedErrorId : ParameterArgumentValidationErrorNullNotAllowed,Microsoft.PowerShell.Commands.TestPathCommand
```

### <span data-ttu-id="32d2f-151">Exempel 8: testa en sökväg med blank steg som värde</span><span class="sxs-lookup"><span data-stu-id="32d2f-151">Example 8: Test a path with whitespace as the value</span></span>

<span data-ttu-id="32d2f-152">När ett blank steg eller en tom sträng anges för `-Path` parametern returneras **false**.</span><span class="sxs-lookup"><span data-stu-id="32d2f-152">When a whitespace or empty string is provided for the the `-Path` parameter, it returns **False**.</span></span>
<span data-ttu-id="32d2f-153">I följande exempel visas blank steg och en tom sträng.</span><span class="sxs-lookup"><span data-stu-id="32d2f-153">The following example show whitespace and empty string.</span></span>

```powershell
Test-Path ' '
Test-Path ''
```

```Output
False
False
```

## <span data-ttu-id="32d2f-154">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="32d2f-154">PARAMETERS</span></span>

### <span data-ttu-id="32d2f-155">-Credential</span><span class="sxs-lookup"><span data-stu-id="32d2f-155">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="32d2f-156">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="32d2f-156">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="32d2f-157">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="32d2f-157">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="32d2f-158">-Undanta</span><span class="sxs-lookup"><span data-stu-id="32d2f-158">-Exclude</span></span>

<span data-ttu-id="32d2f-159">Anger objekt som denna cmdlet utelämnar.</span><span class="sxs-lookup"><span data-stu-id="32d2f-159">Specifies items that this cmdlet omits.</span></span> <span data-ttu-id="32d2f-160">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="32d2f-160">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="32d2f-161">Ange ett Sök vägs element eller ett mönster, till exempel "\*. txt".</span><span class="sxs-lookup"><span data-stu-id="32d2f-161">Enter a path element or pattern, such as "\*.txt".</span></span> <span data-ttu-id="32d2f-162">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="32d2f-162">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="32d2f-163">-Filter</span><span class="sxs-lookup"><span data-stu-id="32d2f-163">-Filter</span></span>

<span data-ttu-id="32d2f-164">Anger ett filter i formatet eller språket för providern.</span><span class="sxs-lookup"><span data-stu-id="32d2f-164">Specifies a filter in the format or language of the provider.</span></span> <span data-ttu-id="32d2f-165">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="32d2f-165">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="32d2f-166">Syntaxen för filtret, inklusive användning av jokertecken, är beroende av providern.</span><span class="sxs-lookup"><span data-stu-id="32d2f-166">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span> <span data-ttu-id="32d2f-167">Filter är mer effektiva än andra parametrar, eftersom providern använder dem när den hämtar objekt i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="32d2f-167">Filters are more efficient than other parameters, because the provider applies them when it retrieves the objects instead of having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="32d2f-168">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="32d2f-168">-Include</span></span>

<span data-ttu-id="32d2f-169">Anger sökvägar som denna cmdlet testar.</span><span class="sxs-lookup"><span data-stu-id="32d2f-169">Specifies paths that this cmdlet tests.</span></span> <span data-ttu-id="32d2f-170">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="32d2f-170">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="32d2f-171">Ange ett Sök vägs element eller ett mönster, till exempel "\*. txt".</span><span class="sxs-lookup"><span data-stu-id="32d2f-171">Enter a path element or pattern, such as "\*.txt".</span></span> <span data-ttu-id="32d2f-172">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="32d2f-172">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="32d2f-173">-IsValid</span><span class="sxs-lookup"><span data-stu-id="32d2f-173">-IsValid</span></span>

<span data-ttu-id="32d2f-174">Anger att den här cmdleten testar syntaxen för sökvägen, oavsett om elementen i sökvägen finns.</span><span class="sxs-lookup"><span data-stu-id="32d2f-174">Indicates that this cmdlet tests the syntax of the path, regardless of whether the elements of the path exist.</span></span> <span data-ttu-id="32d2f-175">Den här cmdleten returnerar `$True` om syntaxen för sökvägen är giltig och `$False` inte.</span><span class="sxs-lookup"><span data-stu-id="32d2f-175">This cmdlet returns `$True` if the path syntax is valid and `$False` if it is not.</span></span>

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

### <span data-ttu-id="32d2f-176">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="32d2f-176">-LiteralPath</span></span>

<span data-ttu-id="32d2f-177">Anger en sökväg som ska testas.</span><span class="sxs-lookup"><span data-stu-id="32d2f-177">Specifies a path to be tested.</span></span> <span data-ttu-id="32d2f-178">Till skillnad från **sökväg** används värdet för parametern **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="32d2f-178">Unlike **Path** , the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span> <span data-ttu-id="32d2f-179">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="32d2f-179">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="32d2f-180">Om sökvägen innehåller tecken som kan tolkas av PowerShell som escape-sekvenser måste du omge sökvägen med enkla citat tecken så att de inte tolkas.</span><span class="sxs-lookup"><span data-stu-id="32d2f-180">If the path includes characters that could be interpreted by PowerShell as escape sequences, you must enclose the path in single quote so that they won't be interpreted.</span></span>

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

### <span data-ttu-id="32d2f-181">-NewerThan</span><span class="sxs-lookup"><span data-stu-id="32d2f-181">-NewerThan</span></span>

<span data-ttu-id="32d2f-182">Ange en tid som ett **datetime** -objekt.</span><span class="sxs-lookup"><span data-stu-id="32d2f-182">Specify a time as a **DateTime** object.</span></span>

```yaml
Type: System.Nullable`1[System.DateTime]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="32d2f-183">-OlderThan</span><span class="sxs-lookup"><span data-stu-id="32d2f-183">-OlderThan</span></span>

<span data-ttu-id="32d2f-184">Ange en tid som ett **datetime** -objekt.</span><span class="sxs-lookup"><span data-stu-id="32d2f-184">Specify a time as a **DateTime** object.</span></span>

```yaml
Type: System.Nullable`1[System.DateTime]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="32d2f-185">-Path</span><span class="sxs-lookup"><span data-stu-id="32d2f-185">-Path</span></span>

<span data-ttu-id="32d2f-186">Anger en sökväg som ska testas.</span><span class="sxs-lookup"><span data-stu-id="32d2f-186">Specifies a path to be tested.</span></span> <span data-ttu-id="32d2f-187">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="32d2f-187">Wildcard characters are permitted.</span></span> <span data-ttu-id="32d2f-188">Om sökvägen innehåller blank steg, omger du den med citat tecken.</span><span class="sxs-lookup"><span data-stu-id="32d2f-188">If the path includes spaces, enclose it in quotation marks.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="32d2f-189">-PathType</span><span class="sxs-lookup"><span data-stu-id="32d2f-189">-PathType</span></span>

<span data-ttu-id="32d2f-190">Anger typen för det sista elementet i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="32d2f-190">Specifies the type of the final element in the path.</span></span> <span data-ttu-id="32d2f-191">Den här cmdleten returnerar `$True` om elementet är av den angivna typen och `$False` om det inte är det.</span><span class="sxs-lookup"><span data-stu-id="32d2f-191">This cmdlet returns `$True` if the element is of the specified type and `$False` if it is not.</span></span> <span data-ttu-id="32d2f-192">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="32d2f-192">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="32d2f-193">Fönster.</span><span class="sxs-lookup"><span data-stu-id="32d2f-193">Container.</span></span>
  <span data-ttu-id="32d2f-194">Ett-element som innehåller andra element, till exempel en katalog eller register nyckel.</span><span class="sxs-lookup"><span data-stu-id="32d2f-194">An element that contains other elements, such as a directory or registry key.</span></span>
- <span data-ttu-id="32d2f-195">Nod.</span><span class="sxs-lookup"><span data-stu-id="32d2f-195">Leaf.</span></span>
  <span data-ttu-id="32d2f-196">Ett element som inte innehåller andra element, till exempel en fil.</span><span class="sxs-lookup"><span data-stu-id="32d2f-196">An element that does not contain other elements, such as a file.</span></span>
- <span data-ttu-id="32d2f-197">Helst.</span><span class="sxs-lookup"><span data-stu-id="32d2f-197">Any.</span></span>
  <span data-ttu-id="32d2f-198">Antingen en behållare eller ett löv.</span><span class="sxs-lookup"><span data-stu-id="32d2f-198">Either a container or a leaf.</span></span>

<span data-ttu-id="32d2f-199">Anger om det sista elementet i sökvägen är av en viss typ.</span><span class="sxs-lookup"><span data-stu-id="32d2f-199">Tells whether the final element in the path is of a particular type.</span></span>

> [!CAUTION]
>
> <span data-ttu-id="32d2f-200">Upp till PowerShell-version 6.1.2 när **IsValid** -och **PathType** -växlarna anges tillsammans `Test-Path` ignorerar cmdleten **PathType** -växeln och validerar bara den syntaktiska sökvägen utan att verifiera Sök vägs typen.</span><span class="sxs-lookup"><span data-stu-id="32d2f-200">Up to PowerShell version 6.1.2, when the **IsValid** and **PathType** switches are specified together, the `Test-Path` cmdlet ignores the **PathType** switch and only validates the syntactic path without validating the path type.</span></span>
>
> <span data-ttu-id="32d2f-201">Enligt [problem #8607](https://github.com/PowerShell/PowerShell/issues/8607)kan det vara en avbrytande ändring i en framtida version, där **IsValid** -och **PathType** -växlarna tillhör separata parameter uppsättningar och därför inte kan användas tillsammans för att undvika denna förvirring.</span><span class="sxs-lookup"><span data-stu-id="32d2f-201">According to [issue #8607](https://github.com/PowerShell/PowerShell/issues/8607), fixing this behavior may be a breaking change in a future version, where the **IsValid** and **PathType** switches belong to separate parameter sets, and thus, cannot be used together avoiding this confusion.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.TestPathType
Parameter Sets: (All)
Aliases: Type
Accepted values: Any, Container, Leaf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="32d2f-202">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="32d2f-202">CommonParameters</span></span>

<span data-ttu-id="32d2f-203">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="32d2f-203">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="32d2f-204">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="32d2f-204">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="32d2f-205">INDATA</span><span class="sxs-lookup"><span data-stu-id="32d2f-205">INPUTS</span></span>

### <span data-ttu-id="32d2f-206">System. String</span><span class="sxs-lookup"><span data-stu-id="32d2f-206">System.String</span></span>

<span data-ttu-id="32d2f-207">Du kan skicka vidare en sträng som innehåller en sökväg, men inte en literal sökväg, till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="32d2f-207">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="32d2f-208">UTDATA</span><span class="sxs-lookup"><span data-stu-id="32d2f-208">OUTPUTS</span></span>

### <span data-ttu-id="32d2f-209">System. Boolean</span><span class="sxs-lookup"><span data-stu-id="32d2f-209">System.Boolean</span></span>

<span data-ttu-id="32d2f-210">Cmdleten returnerar ett **booleskt** värde.</span><span class="sxs-lookup"><span data-stu-id="32d2f-210">The cmdlet returns a **Boolean** value.</span></span>

## <span data-ttu-id="32d2f-211">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="32d2f-211">NOTES</span></span>

<span data-ttu-id="32d2f-212">Cmdlet: arna som innehåller **sökvägen** Substantiv ( **Sök vägs** -cmdletarna) fungerar med Sök vägs namn och returnerar namnen i ett koncist format som alla PowerShell-leverantörer kan tolka.</span><span class="sxs-lookup"><span data-stu-id="32d2f-212">The cmdlets that contain the **Path** noun (the **Path** cmdlets) work with path names and return the names in a concise format that all PowerShell providers can interpret.</span></span> <span data-ttu-id="32d2f-213">De är utformade för användning i program och skript där du vill visa hela eller delar av ett Sök vägs namn i ett visst format.</span><span class="sxs-lookup"><span data-stu-id="32d2f-213">They are designed for use in programs and scripts where you want to display all or part of a path name in a particular format.</span></span>
<span data-ttu-id="32d2f-214">Använd dem på samma sätt som du använder **logsdirectory** , **Normpath** , **realpath** , **Join** eller andra Sök vägs manipulerare.</span><span class="sxs-lookup"><span data-stu-id="32d2f-214">Use them as you would use **Dirname** , **Normpath** , **Realpath** , **Join** , or other path manipulators.</span></span>

<span data-ttu-id="32d2f-215">`Test-Path`Är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="32d2f-215">The `Test-Path` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="32d2f-216">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="32d2f-216">To list the providers available in your session, type `Get-PSProvider`.</span></span> <span data-ttu-id="32d2f-217">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="32d2f-217">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="32d2f-218">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="32d2f-218">RELATED LINKS</span></span>

[<span data-ttu-id="32d2f-219">Konvertera-sökväg</span><span class="sxs-lookup"><span data-stu-id="32d2f-219">Convert-Path</span></span>](Convert-Path.md)

[<span data-ttu-id="32d2f-220">Anslut till sökväg</span><span class="sxs-lookup"><span data-stu-id="32d2f-220">Join-Path</span></span>](Join-Path.md)

[<span data-ttu-id="32d2f-221">Lös-sökväg</span><span class="sxs-lookup"><span data-stu-id="32d2f-221">Resolve-Path</span></span>](Resolve-Path.md)

[<span data-ttu-id="32d2f-222">Dela-sökväg</span><span class="sxs-lookup"><span data-stu-id="32d2f-222">Split-Path</span></span>](Split-Path.md)
