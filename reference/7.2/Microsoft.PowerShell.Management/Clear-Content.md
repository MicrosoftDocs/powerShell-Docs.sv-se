---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-content?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Content
ms.openlocfilehash: 308aee6f58443bb4e1e3d9751e7bd421b8072d8d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709541"
---
# <span data-ttu-id="a1057-102">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="a1057-102">Clear-Content</span></span>

## <span data-ttu-id="a1057-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="a1057-103">SYNOPSIS</span></span>
<span data-ttu-id="a1057-104">Tar bort innehållet i ett objekt, men tar inte bort objektet.</span><span class="sxs-lookup"><span data-stu-id="a1057-104">Deletes the contents of an item, but does not delete the item.</span></span>

## <span data-ttu-id="a1057-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a1057-105">SYNTAX</span></span>

### <span data-ttu-id="a1057-106">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="a1057-106">Path (Default)</span></span>

```
Clear-Content [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-Stream <String>] [<CommonParameters>]
```

### <span data-ttu-id="a1057-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a1057-107">LiteralPath</span></span>

```
Clear-Content -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-Stream <String>] [<CommonParameters>]
```

## <span data-ttu-id="a1057-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a1057-108">DESCRIPTION</span></span>

<span data-ttu-id="a1057-109">`Clear-Content`Cmdleten tar bort innehållet i ett objekt, t. ex. att ta bort texten från en fil, men objektet tas inte bort.</span><span class="sxs-lookup"><span data-stu-id="a1057-109">The `Clear-Content` cmdlet deletes the contents of an item, such as deleting the text from a file, but it does not delete the item.</span></span>
<span data-ttu-id="a1057-110">Därför finns objektet, men det är tomt.</span><span class="sxs-lookup"><span data-stu-id="a1057-110">As a result, the item exists, but it is empty.</span></span>
<span data-ttu-id="a1057-111">`Clear-Content`Liknar `Clear-Item` , men den fungerar på objekt med innehåll, i stället för objekt med värden.</span><span class="sxs-lookup"><span data-stu-id="a1057-111">The `Clear-Content` is similar to `Clear-Item`, but it works on items with contents, instead of items with values.</span></span>

## <span data-ttu-id="a1057-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="a1057-112">EXAMPLES</span></span>

### <span data-ttu-id="a1057-113">Exempel 1: ta bort allt innehåll från en katalog</span><span class="sxs-lookup"><span data-stu-id="a1057-113">Example 1: Delete all content from a directory</span></span>

```powershell
Clear-Content "..\SmpUsers\*\init.txt"
```

<span data-ttu-id="a1057-114">Det här kommandot tar bort allt innehåll från "init.txt"-filer i alla under kataloger i SmpUsers-katalogen.</span><span class="sxs-lookup"><span data-stu-id="a1057-114">This command deletes all of the content from the "init.txt" files in all subdirectories of the SmpUsers directory.</span></span>
<span data-ttu-id="a1057-115">Filerna tas inte bort, men de är tomma.</span><span class="sxs-lookup"><span data-stu-id="a1057-115">The files are not deleted, but they are empty.</span></span>

### <span data-ttu-id="a1057-116">Exempel 2: ta bort innehållet för alla filer med ett jokertecken</span><span class="sxs-lookup"><span data-stu-id="a1057-116">Example 2: Delete content of all files with a wildcard</span></span>

```powershell
Clear-Content -Path "*" -Filter "*.log" -Force
```

<span data-ttu-id="a1057-117">Det här kommandot tar bort innehållet i alla filer i den aktuella katalogen med fil namns tillägget ". log", inklusive filer med attributet skrivskyddad.</span><span class="sxs-lookup"><span data-stu-id="a1057-117">This command deletes the contents of all files in the current directory with the ".log" file name extension, including files with the read-only attribute.</span></span>
<span data-ttu-id="a1057-118">Asterisken ( \* ) i sökvägen representerar alla objekt i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="a1057-118">The asterisk (\*) in the path represents all items in the current directory.</span></span>
<span data-ttu-id="a1057-119">**Force** -parametern gör kommandot effektivt på skrivskyddade filer.</span><span class="sxs-lookup"><span data-stu-id="a1057-119">The **Force** parameter makes the command effective on read-only files.</span></span>
<span data-ttu-id="a1057-120">Om du använder ett filter för att begränsa kommandot till filer med fil namns tillägget. log i stället för att ange \* . log i sökvägen gör åtgärden snabbare.</span><span class="sxs-lookup"><span data-stu-id="a1057-120">Using a filter to restrict the command to files with the .log file name extension instead of specifying \*.log in the path makes the operation faster.</span></span>

### <span data-ttu-id="a1057-121">Exempel 3: Rensa alla data från en ström</span><span class="sxs-lookup"><span data-stu-id="a1057-121">Example 3: Clear all data from a stream</span></span>

<span data-ttu-id="a1057-122">Det här exemplet visar hur `Clear-Content` cmdleten rensar innehållet från en alternativ data ström och låter strömmen vara intakt.</span><span class="sxs-lookup"><span data-stu-id="a1057-122">This example shows how the `Clear-Content` cmdlet clears the content from an alternate data stream while leaving the stream intact.</span></span>

<span data-ttu-id="a1057-123">Det första kommandot använder `Get-Content` cmdleten för att hämta innehållet i zonen. identifierarens data ström i den Copy-Script.ps1 filen som hämtades från Internet.</span><span class="sxs-lookup"><span data-stu-id="a1057-123">The first command uses the `Get-Content` cmdlet to get the content of the Zone.Identifier stream in the Copy-Script.ps1 file, which was downloaded from the Internet.</span></span>

<span data-ttu-id="a1057-124">Det andra kommandot använder `Clear-Content` cmdleten för att rensa innehållet.</span><span class="sxs-lookup"><span data-stu-id="a1057-124">The second command uses the `Clear-Content` cmdlet to clear the content.</span></span>

<span data-ttu-id="a1057-125">Det tredje kommandot upprepar det första kommandot.</span><span class="sxs-lookup"><span data-stu-id="a1057-125">The third command repeats the first command.</span></span> <span data-ttu-id="a1057-126">Den verifierar att innehållet är rensat, men data strömmen är kvar.</span><span class="sxs-lookup"><span data-stu-id="a1057-126">It verifies that the content is cleared, but the stream remains.</span></span> <span data-ttu-id="a1057-127">Om strömmen har tagits bort genererar kommandot ett fel.</span><span class="sxs-lookup"><span data-stu-id="a1057-127">If the stream were deleted, the command would generate an error.</span></span>

<span data-ttu-id="a1057-128">Du kan använda en metod som den här för att rensa innehållet i en alternativ data ström.</span><span class="sxs-lookup"><span data-stu-id="a1057-128">You can use a method like this one to clear the content of an alternate data stream.</span></span> <span data-ttu-id="a1057-129">Det är dock inte det rekommenderade sättet att eliminera säkerhets kontroller som blockerar filer som hämtas från Internet.</span><span class="sxs-lookup"><span data-stu-id="a1057-129">However, it is not the recommended way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="a1057-130">Om du verifierar att en Hämtad fil är säker använder du `Unblock-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a1057-130">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

```
PS C:\> Get-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier

[ZoneTransfer]
ZoneId=3

PS C:\>Clear-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier

PS C:\>Get-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
PS C:\>
```

## <span data-ttu-id="a1057-131">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="a1057-131">PARAMETERS</span></span>

### <span data-ttu-id="a1057-132">-Stream</span><span class="sxs-lookup"><span data-stu-id="a1057-132">-Stream</span></span>

<span data-ttu-id="a1057-133">Anger en alternativ data ström för innehåll.</span><span class="sxs-lookup"><span data-stu-id="a1057-133">Specifies an alternative data stream for content.</span></span>
<span data-ttu-id="a1057-134">Om data strömmen inte finns skapar den här cmdleten den.</span><span class="sxs-lookup"><span data-stu-id="a1057-134">If the stream does not exist, this cmdlet creates it.</span></span>
<span data-ttu-id="a1057-135">Jokertecken stöds inte.</span><span class="sxs-lookup"><span data-stu-id="a1057-135">Wildcard characters are not supported.</span></span>

<span data-ttu-id="a1057-136">Stream är en dynamisk parameter som fil Systems leverantören lägger till i `Clear-Content` .</span><span class="sxs-lookup"><span data-stu-id="a1057-136">Stream is a dynamic parameter that the FileSystem provider adds to `Clear-Content`.</span></span>
<span data-ttu-id="a1057-137">Den här parametern fungerar bara i fil system enheter.</span><span class="sxs-lookup"><span data-stu-id="a1057-137">This parameter works only in file system drives.</span></span>

<span data-ttu-id="a1057-138">Du kan använda `Clear-Content` cmdleten för att ändra innehållet i zonen. unik identifierare för den alternativa data strömmen.</span><span class="sxs-lookup"><span data-stu-id="a1057-138">You can use the `Clear-Content` cmdlet to change the content of the Zone.Identifier alternate data stream.</span></span>
<span data-ttu-id="a1057-139">Vi rekommenderar dock inte detta som ett sätt att eliminera säkerhets kontroller som blockerar filer som hämtas från Internet.</span><span class="sxs-lookup"><span data-stu-id="a1057-139">However, we do not recommend this as a way to eliminate security checks that block files that are downloaded from the Internet.</span></span>
<span data-ttu-id="a1057-140">Om du verifierar att en Hämtad fil är säker använder du `Unblock-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a1057-140">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

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

### <span data-ttu-id="a1057-141">-Credential</span><span class="sxs-lookup"><span data-stu-id="a1057-141">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="a1057-142">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a1057-142">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="a1057-143">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="a1057-143">To impersonate another user, or elevate your credentials when running this cmdlet, use Invoke-Command.</span></span>

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

### <span data-ttu-id="a1057-144">-Undanta</span><span class="sxs-lookup"><span data-stu-id="a1057-144">-Exclude</span></span>

<span data-ttu-id="a1057-145">Anger, som en sträng mat ris, strängar som denna cmdlet utelämnar från sökvägen till innehållet.</span><span class="sxs-lookup"><span data-stu-id="a1057-145">Specifies, as a string array, strings that this cmdlet omits from the path to the content.</span></span>
<span data-ttu-id="a1057-146">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="a1057-146">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="a1057-147">Ange ett Sök vägs element eller ett mönster, till exempel "\*. txt".</span><span class="sxs-lookup"><span data-stu-id="a1057-147">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="a1057-148">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="a1057-148">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="a1057-149">-Filter</span><span class="sxs-lookup"><span data-stu-id="a1057-149">-Filter</span></span>

<span data-ttu-id="a1057-150">Anger ett filter i providerns format eller språk.</span><span class="sxs-lookup"><span data-stu-id="a1057-150">Specifies a filter in the provider's format or language.</span></span>
<span data-ttu-id="a1057-151">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="a1057-151">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="a1057-152">Syntaxen för filtret, inklusive användning av jokertecken, beror på providern.</span><span class="sxs-lookup"><span data-stu-id="a1057-152">The syntax of the filter, including the use of wildcards, depends on the provider.</span></span>
<span data-ttu-id="a1057-153">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när objekten hämtas, i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="a1057-153">Filters are more efficient than other parameters, because the provider applies them when retrieving the objects, rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="a1057-154">-Force</span><span class="sxs-lookup"><span data-stu-id="a1057-154">-Force</span></span>

<span data-ttu-id="a1057-155">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="a1057-155">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="a1057-156">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="a1057-156">-Include</span></span>

<span data-ttu-id="a1057-157">Anger, som en sträng mat ris, innehåll som denna cmdlet rensar.</span><span class="sxs-lookup"><span data-stu-id="a1057-157">Specifies, as a string array, content that this cmdlet clears.</span></span>
<span data-ttu-id="a1057-158">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="a1057-158">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="a1057-159">Ange ett Sök vägs element eller ett mönster, till exempel "\*. txt".</span><span class="sxs-lookup"><span data-stu-id="a1057-159">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="a1057-160">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="a1057-160">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="a1057-161">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a1057-161">-LiteralPath</span></span>

<span data-ttu-id="a1057-162">Anger sökvägar till objekten som innehållet tas bort från.</span><span class="sxs-lookup"><span data-stu-id="a1057-162">Specifies the paths to the items from which content is deleted.</span></span>
<span data-ttu-id="a1057-163">Till skillnad från parametern **Path** används värdet för **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="a1057-163">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="a1057-164">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="a1057-164">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="a1057-165">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="a1057-165">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="a1057-166">Enkla citat tecken ser till att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="a1057-166">Single quotation marks tell having PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="a1057-167">-Path</span><span class="sxs-lookup"><span data-stu-id="a1057-167">-Path</span></span>

<span data-ttu-id="a1057-168">Anger sökvägar till objekten som innehållet tas bort från.</span><span class="sxs-lookup"><span data-stu-id="a1057-168">Specifies the paths to the items from which content is deleted.</span></span>
<span data-ttu-id="a1057-169">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="a1057-169">Wildcards are permitted.</span></span>
<span data-ttu-id="a1057-170">Sök vägarna måste vara sökvägar till objekt, inte behållare.</span><span class="sxs-lookup"><span data-stu-id="a1057-170">The paths must be paths to items, not to containers.</span></span>
<span data-ttu-id="a1057-171">Du måste till exempel ange en sökväg till en eller flera filer, inte en sökväg till en katalog.</span><span class="sxs-lookup"><span data-stu-id="a1057-171">For example, you must specify a path to one or more files, not a path to a directory.</span></span>
<span data-ttu-id="a1057-172">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="a1057-172">Wildcards are permitted.</span></span>
<span data-ttu-id="a1057-173">Den här parametern är obligatorisk, men parameter namnet (sökväg) är valfritt.</span><span class="sxs-lookup"><span data-stu-id="a1057-173">This parameter is required, but the parameter name ("Path") is optional.</span></span>

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

### <span data-ttu-id="a1057-174">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a1057-174">-Confirm</span></span>

<span data-ttu-id="a1057-175">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a1057-175">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a1057-176">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a1057-176">-WhatIf</span></span>

<span data-ttu-id="a1057-177">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="a1057-177">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="a1057-178">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="a1057-178">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a1057-179">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a1057-179">CommonParameters</span></span>

<span data-ttu-id="a1057-180">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="a1057-180">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="a1057-181">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="a1057-181">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="a1057-182">INDATA</span><span class="sxs-lookup"><span data-stu-id="a1057-182">INPUTS</span></span>

### <span data-ttu-id="a1057-183">Inga</span><span class="sxs-lookup"><span data-stu-id="a1057-183">None</span></span>

<span data-ttu-id="a1057-184">Det går inte att skicka pipe-objekt till `Clear-Content` .</span><span class="sxs-lookup"><span data-stu-id="a1057-184">You cannot pipe objects to `Clear-Content`.</span></span>

## <span data-ttu-id="a1057-185">UTDATA</span><span class="sxs-lookup"><span data-stu-id="a1057-185">OUTPUTS</span></span>

### <span data-ttu-id="a1057-186">Inga</span><span class="sxs-lookup"><span data-stu-id="a1057-186">None</span></span>

<span data-ttu-id="a1057-187">Denna cmdlet returnerar inga objekt.</span><span class="sxs-lookup"><span data-stu-id="a1057-187">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="a1057-188">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="a1057-188">NOTES</span></span>

<span data-ttu-id="a1057-189">Du kan använda `Clear-Content` med PowerShell-filsystem-providern och med andra leverantörer som hanterar innehåll.</span><span class="sxs-lookup"><span data-stu-id="a1057-189">You can use `Clear-Content` with the PowerShell FileSystem provider and with other providers that manipulate content.</span></span>
<span data-ttu-id="a1057-190">Om du vill rensa objekt som inte anses vara innehåll, till exempel objekt som hanteras av PowerShell-certifikatet eller register leverantörer, använder du `Clear-Item` .</span><span class="sxs-lookup"><span data-stu-id="a1057-190">To clear items that are not considered to be content, such as items managed by the PowerShell Certificate or Registry providers, use `Clear-Item`.</span></span>

<span data-ttu-id="a1057-191">`Clear-Content`Cmdleten är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="a1057-191">The `Clear-Content` cmdlet is designed to work with the data exposed by any provider.</span></span>
<span data-ttu-id="a1057-192">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="a1057-192">To list the providers available in your session, type `Get-PsProvider`.</span></span>
<span data-ttu-id="a1057-193">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="a1057-193">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="a1057-194">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="a1057-194">RELATED LINKS</span></span>

[<span data-ttu-id="a1057-195">Lägg till innehåll</span><span class="sxs-lookup"><span data-stu-id="a1057-195">Add-Content</span></span>](Add-Content.md)

[<span data-ttu-id="a1057-196">Hämta innehåll</span><span class="sxs-lookup"><span data-stu-id="a1057-196">Get-Content</span></span>](Get-Content.md)

[<span data-ttu-id="a1057-197">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="a1057-197">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="a1057-198">Ange innehåll</span><span class="sxs-lookup"><span data-stu-id="a1057-198">Set-Content</span></span>](Set-Content.md)

[<span data-ttu-id="a1057-199">about_Providers</span><span class="sxs-lookup"><span data-stu-id="a1057-199">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

