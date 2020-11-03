---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-content?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Content
ms.openlocfilehash: 5a38fd45ff1f645df7004452b5a3c16c6f5cb74a
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262977"
---
# <span data-ttu-id="b722f-103">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="b722f-103">Clear-Content</span></span>

## <span data-ttu-id="b722f-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="b722f-104">SYNOPSIS</span></span>
<span data-ttu-id="b722f-105">Tar bort innehållet i ett objekt, men tar inte bort objektet.</span><span class="sxs-lookup"><span data-stu-id="b722f-105">Deletes the contents of an item, but does not delete the item.</span></span>

## <span data-ttu-id="b722f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b722f-106">SYNTAX</span></span>

### <span data-ttu-id="b722f-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="b722f-107">Path (Default)</span></span>

```
Clear-Content [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-Stream <String>] [<CommonParameters>]
```

### <span data-ttu-id="b722f-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b722f-108">LiteralPath</span></span>

```
Clear-Content -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-Stream <String>] [<CommonParameters>]
```

## <span data-ttu-id="b722f-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b722f-109">DESCRIPTION</span></span>

<span data-ttu-id="b722f-110">`Clear-Content`Cmdleten tar bort innehållet i ett objekt, t. ex. att ta bort texten från en fil, men objektet tas inte bort.</span><span class="sxs-lookup"><span data-stu-id="b722f-110">The `Clear-Content` cmdlet deletes the contents of an item, such as deleting the text from a file, but it does not delete the item.</span></span>
<span data-ttu-id="b722f-111">Därför finns objektet, men det är tomt.</span><span class="sxs-lookup"><span data-stu-id="b722f-111">As a result, the item exists, but it is empty.</span></span>
<span data-ttu-id="b722f-112">`Clear-Content`Liknar `Clear-Item` , men den fungerar på objekt med innehåll, i stället för objekt med värden.</span><span class="sxs-lookup"><span data-stu-id="b722f-112">The `Clear-Content` is similar to `Clear-Item`, but it works on items with contents, instead of items with values.</span></span>

## <span data-ttu-id="b722f-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="b722f-113">EXAMPLES</span></span>

### <span data-ttu-id="b722f-114">Exempel 1: ta bort allt innehåll från en katalog</span><span class="sxs-lookup"><span data-stu-id="b722f-114">Example 1: Delete all content from a directory</span></span>

```powershell
Clear-Content "..\SmpUsers\*\init.txt"
```

<span data-ttu-id="b722f-115">Det här kommandot tar bort allt innehåll från "init.txt"-filer i alla under kataloger i SmpUsers-katalogen.</span><span class="sxs-lookup"><span data-stu-id="b722f-115">This command deletes all of the content from the "init.txt" files in all subdirectories of the SmpUsers directory.</span></span>
<span data-ttu-id="b722f-116">Filerna tas inte bort, men de är tomma.</span><span class="sxs-lookup"><span data-stu-id="b722f-116">The files are not deleted, but they are empty.</span></span>

### <span data-ttu-id="b722f-117">Exempel 2: ta bort innehållet för alla filer med ett jokertecken</span><span class="sxs-lookup"><span data-stu-id="b722f-117">Example 2: Delete content of all files with a wildcard</span></span>

```powershell
Clear-Content -Path "*" -Filter "*.log" -Force
```

<span data-ttu-id="b722f-118">Det här kommandot tar bort innehållet i alla filer i den aktuella katalogen med fil namns tillägget ". log", inklusive filer med attributet skrivskyddad.</span><span class="sxs-lookup"><span data-stu-id="b722f-118">This command deletes the contents of all files in the current directory with the ".log" file name extension, including files with the read-only attribute.</span></span>
<span data-ttu-id="b722f-119">Asterisken ( \* ) i sökvägen representerar alla objekt i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="b722f-119">The asterisk (\*) in the path represents all items in the current directory.</span></span>
<span data-ttu-id="b722f-120">**Force** -parametern gör kommandot effektivt på skrivskyddade filer.</span><span class="sxs-lookup"><span data-stu-id="b722f-120">The **Force** parameter makes the command effective on read-only files.</span></span>
<span data-ttu-id="b722f-121">Om du använder ett filter för att begränsa kommandot till filer med fil namns tillägget. log i stället för att ange \* . log i sökvägen gör åtgärden snabbare.</span><span class="sxs-lookup"><span data-stu-id="b722f-121">Using a filter to restrict the command to files with the .log file name extension instead of specifying \*.log in the path makes the operation faster.</span></span>

### <span data-ttu-id="b722f-122">Exempel 3: Rensa alla data från en ström</span><span class="sxs-lookup"><span data-stu-id="b722f-122">Example 3: Clear all data from a stream</span></span>

<span data-ttu-id="b722f-123">Det här exemplet visar hur `Clear-Content` cmdleten rensar innehållet från en alternativ data ström och låter strömmen vara intakt.</span><span class="sxs-lookup"><span data-stu-id="b722f-123">This example shows how the `Clear-Content` cmdlet clears the content from an alternate data stream while leaving the stream intact.</span></span>

<span data-ttu-id="b722f-124">Det första kommandot använder `Get-Content` cmdleten för att hämta innehållet i zonen. identifierarens data ström i den Copy-Script.ps1 filen som hämtades från Internet.</span><span class="sxs-lookup"><span data-stu-id="b722f-124">The first command uses the `Get-Content` cmdlet to get the content of the Zone.Identifier stream in the Copy-Script.ps1 file, which was downloaded from the Internet.</span></span>

<span data-ttu-id="b722f-125">Det andra kommandot använder `Clear-Content` cmdleten för att rensa innehållet.</span><span class="sxs-lookup"><span data-stu-id="b722f-125">The second command uses the `Clear-Content` cmdlet to clear the content.</span></span>

<span data-ttu-id="b722f-126">Det tredje kommandot upprepar det första kommandot.</span><span class="sxs-lookup"><span data-stu-id="b722f-126">The third command repeats the first command.</span></span> <span data-ttu-id="b722f-127">Den verifierar att innehållet är rensat, men data strömmen är kvar.</span><span class="sxs-lookup"><span data-stu-id="b722f-127">It verifies that the content is cleared, but the stream remains.</span></span> <span data-ttu-id="b722f-128">Om strömmen har tagits bort genererar kommandot ett fel.</span><span class="sxs-lookup"><span data-stu-id="b722f-128">If the stream were deleted, the command would generate an error.</span></span>

<span data-ttu-id="b722f-129">Du kan använda en metod som den här för att rensa innehållet i en alternativ data ström.</span><span class="sxs-lookup"><span data-stu-id="b722f-129">You can use a method like this one to clear the content of an alternate data stream.</span></span> <span data-ttu-id="b722f-130">Det är dock inte det rekommenderade sättet att eliminera säkerhets kontroller som blockerar filer som hämtas från Internet.</span><span class="sxs-lookup"><span data-stu-id="b722f-130">However, it is not the recommended way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="b722f-131">Om du verifierar att en Hämtad fil är säker använder du `Unblock-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b722f-131">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

```
PS C:\> Get-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier

[ZoneTransfer]
ZoneId=3

PS C:\>Clear-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier

PS C:\>Get-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
PS C:\>
```

## <span data-ttu-id="b722f-132">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="b722f-132">PARAMETERS</span></span>

### <span data-ttu-id="b722f-133">-Stream</span><span class="sxs-lookup"><span data-stu-id="b722f-133">-Stream</span></span>

<span data-ttu-id="b722f-134">Anger en alternativ data ström för innehåll.</span><span class="sxs-lookup"><span data-stu-id="b722f-134">Specifies an alternative data stream for content.</span></span>
<span data-ttu-id="b722f-135">Om data strömmen inte finns skapar den här cmdleten den.</span><span class="sxs-lookup"><span data-stu-id="b722f-135">If the stream does not exist, this cmdlet creates it.</span></span>
<span data-ttu-id="b722f-136">Jokertecken stöds inte.</span><span class="sxs-lookup"><span data-stu-id="b722f-136">Wildcard characters are not supported.</span></span>

<span data-ttu-id="b722f-137">Stream är en dynamisk parameter som fil Systems leverantören lägger till i `Clear-Content` .</span><span class="sxs-lookup"><span data-stu-id="b722f-137">Stream is a dynamic parameter that the FileSystem provider adds to `Clear-Content`.</span></span>
<span data-ttu-id="b722f-138">Den här parametern fungerar bara i fil system enheter.</span><span class="sxs-lookup"><span data-stu-id="b722f-138">This parameter works only in file system drives.</span></span>

<span data-ttu-id="b722f-139">Du kan använda `Clear-Content` cmdleten för att ändra innehållet i zonen. unik identifierare för den alternativa data strömmen.</span><span class="sxs-lookup"><span data-stu-id="b722f-139">You can use the `Clear-Content` cmdlet to change the content of the Zone.Identifier alternate data stream.</span></span>
<span data-ttu-id="b722f-140">Vi rekommenderar dock inte detta som ett sätt att eliminera säkerhets kontroller som blockerar filer som hämtas från Internet.</span><span class="sxs-lookup"><span data-stu-id="b722f-140">However, we do not recommend this as a way to eliminate security checks that block files that are downloaded from the Internet.</span></span>
<span data-ttu-id="b722f-141">Om du verifierar att en Hämtad fil är säker använder du `Unblock-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b722f-141">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

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

### <span data-ttu-id="b722f-142">-Credential</span><span class="sxs-lookup"><span data-stu-id="b722f-142">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="b722f-143">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b722f-143">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="b722f-144">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="b722f-144">To impersonate another user, or elevate your credentials when running this cmdlet, use Invoke-Command.</span></span>

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

### <span data-ttu-id="b722f-145">-Undanta</span><span class="sxs-lookup"><span data-stu-id="b722f-145">-Exclude</span></span>

<span data-ttu-id="b722f-146">Anger, som en sträng mat ris, strängar som denna cmdlet utelämnar från sökvägen till innehållet.</span><span class="sxs-lookup"><span data-stu-id="b722f-146">Specifies, as a string array, strings that this cmdlet omits from the path to the content.</span></span>
<span data-ttu-id="b722f-147">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="b722f-147">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="b722f-148">Ange ett Sök vägs element eller ett mönster, till exempel "\*. txt".</span><span class="sxs-lookup"><span data-stu-id="b722f-148">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="b722f-149">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="b722f-149">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="b722f-150">-Filter</span><span class="sxs-lookup"><span data-stu-id="b722f-150">-Filter</span></span>

<span data-ttu-id="b722f-151">Anger ett filter i providerns format eller språk.</span><span class="sxs-lookup"><span data-stu-id="b722f-151">Specifies a filter in the provider's format or language.</span></span>
<span data-ttu-id="b722f-152">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="b722f-152">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="b722f-153">Syntaxen för filtret, inklusive användning av jokertecken, beror på providern.</span><span class="sxs-lookup"><span data-stu-id="b722f-153">The syntax of the filter, including the use of wildcards, depends on the provider.</span></span>
<span data-ttu-id="b722f-154">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när objekten hämtas, i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="b722f-154">Filters are more efficient than other parameters, because the provider applies them when retrieving the objects, rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="b722f-155">-Force</span><span class="sxs-lookup"><span data-stu-id="b722f-155">-Force</span></span>

<span data-ttu-id="b722f-156">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="b722f-156">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="b722f-157">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="b722f-157">-Include</span></span>

<span data-ttu-id="b722f-158">Anger, som en sträng mat ris, innehåll som denna cmdlet rensar.</span><span class="sxs-lookup"><span data-stu-id="b722f-158">Specifies, as a string array, content that this cmdlet clears.</span></span>
<span data-ttu-id="b722f-159">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="b722f-159">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="b722f-160">Ange ett Sök vägs element eller ett mönster, till exempel "\*. txt".</span><span class="sxs-lookup"><span data-stu-id="b722f-160">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="b722f-161">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="b722f-161">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="b722f-162">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="b722f-162">-LiteralPath</span></span>

<span data-ttu-id="b722f-163">Anger sökvägar till objekten som innehållet tas bort från.</span><span class="sxs-lookup"><span data-stu-id="b722f-163">Specifies the paths to the items from which content is deleted.</span></span>
<span data-ttu-id="b722f-164">Till skillnad från parametern **Path** används värdet för **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="b722f-164">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="b722f-165">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="b722f-165">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="b722f-166">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="b722f-166">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="b722f-167">Enkla citat tecken ser till att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="b722f-167">Single quotation marks tell having PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="b722f-168">-Path</span><span class="sxs-lookup"><span data-stu-id="b722f-168">-Path</span></span>

<span data-ttu-id="b722f-169">Anger sökvägar till objekten som innehållet tas bort från.</span><span class="sxs-lookup"><span data-stu-id="b722f-169">Specifies the paths to the items from which content is deleted.</span></span>
<span data-ttu-id="b722f-170">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="b722f-170">Wildcards are permitted.</span></span>
<span data-ttu-id="b722f-171">Sök vägarna måste vara sökvägar till objekt, inte behållare.</span><span class="sxs-lookup"><span data-stu-id="b722f-171">The paths must be paths to items, not to containers.</span></span>
<span data-ttu-id="b722f-172">Du måste till exempel ange en sökväg till en eller flera filer, inte en sökväg till en katalog.</span><span class="sxs-lookup"><span data-stu-id="b722f-172">For example, you must specify a path to one or more files, not a path to a directory.</span></span>
<span data-ttu-id="b722f-173">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="b722f-173">Wildcards are permitted.</span></span>
<span data-ttu-id="b722f-174">Den här parametern är obligatorisk, men parameter namnet (sökväg) är valfritt.</span><span class="sxs-lookup"><span data-stu-id="b722f-174">This parameter is required, but the parameter name ("Path") is optional.</span></span>

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

### <span data-ttu-id="b722f-175">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b722f-175">-Confirm</span></span>

<span data-ttu-id="b722f-176">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b722f-176">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b722f-177">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b722f-177">-WhatIf</span></span>

<span data-ttu-id="b722f-178">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="b722f-178">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="b722f-179">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="b722f-179">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b722f-180">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b722f-180">CommonParameters</span></span>

<span data-ttu-id="b722f-181">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="b722f-181">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="b722f-182">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="b722f-182">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="b722f-183">INDATA</span><span class="sxs-lookup"><span data-stu-id="b722f-183">INPUTS</span></span>

### <span data-ttu-id="b722f-184">Inget</span><span class="sxs-lookup"><span data-stu-id="b722f-184">None</span></span>

<span data-ttu-id="b722f-185">Det går inte att skicka pipe-objekt till `Clear-Content` .</span><span class="sxs-lookup"><span data-stu-id="b722f-185">You cannot pipe objects to `Clear-Content`.</span></span>

## <span data-ttu-id="b722f-186">UTDATA</span><span class="sxs-lookup"><span data-stu-id="b722f-186">OUTPUTS</span></span>

### <span data-ttu-id="b722f-187">Inget</span><span class="sxs-lookup"><span data-stu-id="b722f-187">None</span></span>

<span data-ttu-id="b722f-188">Denna cmdlet returnerar inga objekt.</span><span class="sxs-lookup"><span data-stu-id="b722f-188">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="b722f-189">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="b722f-189">NOTES</span></span>

<span data-ttu-id="b722f-190">Du kan använda `Clear-Content` med PowerShell-filsystem-providern och med andra leverantörer som hanterar innehåll.</span><span class="sxs-lookup"><span data-stu-id="b722f-190">You can use `Clear-Content` with the PowerShell FileSystem provider and with other providers that manipulate content.</span></span>
<span data-ttu-id="b722f-191">Om du vill rensa objekt som inte anses vara innehåll, till exempel objekt som hanteras av PowerShell-certifikatet eller register leverantörer, använder du `Clear-Item` .</span><span class="sxs-lookup"><span data-stu-id="b722f-191">To clear items that are not considered to be content, such as items managed by the PowerShell Certificate or Registry providers, use `Clear-Item`.</span></span>

<span data-ttu-id="b722f-192">`Clear-Content`Cmdleten är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="b722f-192">The `Clear-Content` cmdlet is designed to work with the data exposed by any provider.</span></span>
<span data-ttu-id="b722f-193">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="b722f-193">To list the providers available in your session, type `Get-PsProvider`.</span></span>
<span data-ttu-id="b722f-194">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="b722f-194">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="b722f-195">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="b722f-195">RELATED LINKS</span></span>

[<span data-ttu-id="b722f-196">Lägg till innehåll</span><span class="sxs-lookup"><span data-stu-id="b722f-196">Add-Content</span></span>](Add-Content.md)

[<span data-ttu-id="b722f-197">Hämta innehåll</span><span class="sxs-lookup"><span data-stu-id="b722f-197">Get-Content</span></span>](Get-Content.md)

[<span data-ttu-id="b722f-198">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="b722f-198">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="b722f-199">Ange innehåll</span><span class="sxs-lookup"><span data-stu-id="b722f-199">Set-Content</span></span>](Set-Content.md)

[<span data-ttu-id="b722f-200">about_Providers</span><span class="sxs-lookup"><span data-stu-id="b722f-200">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
