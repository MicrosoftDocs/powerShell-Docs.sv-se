---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/18/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/clear-content?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Clear-Content
ms.openlocfilehash: 8024dc8a4a041fad783f1234477ee4b5920e7b00
ms.sourcegitcommit: bf07cffb2a66dec94bf3576e197090f958701f18
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/19/2020
ms.locfileid: "97693060"
---
# <span data-ttu-id="365ea-102">Clear-Content</span><span class="sxs-lookup"><span data-stu-id="365ea-102">Clear-Content</span></span>

## <span data-ttu-id="365ea-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="365ea-103">SYNOPSIS</span></span>
<span data-ttu-id="365ea-104">Tar bort innehållet i ett objekt, men tar inte bort objektet.</span><span class="sxs-lookup"><span data-stu-id="365ea-104">Deletes the contents of an item, but does not delete the item.</span></span>

## <span data-ttu-id="365ea-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="365ea-105">SYNTAX</span></span>

### <span data-ttu-id="365ea-106">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="365ea-106">Path (Default)</span></span>

```
Clear-Content [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-Stream <String>] [<CommonParameters>]
```

### <span data-ttu-id="365ea-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="365ea-107">LiteralPath</span></span>

```
Clear-Content -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>] [-Force]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-Stream <String>] [<CommonParameters>]
```

## <span data-ttu-id="365ea-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="365ea-108">DESCRIPTION</span></span>

<span data-ttu-id="365ea-109">`Clear-Content`Cmdleten tar bort innehållet i ett objekt, t. ex. att ta bort texten från en fil, men objektet tas inte bort.</span><span class="sxs-lookup"><span data-stu-id="365ea-109">The `Clear-Content` cmdlet deletes the contents of an item, such as deleting the text from a file, but it does not delete the item.</span></span>
<span data-ttu-id="365ea-110">Därför finns objektet, men det är tomt.</span><span class="sxs-lookup"><span data-stu-id="365ea-110">As a result, the item exists, but it is empty.</span></span>
<span data-ttu-id="365ea-111">`Clear-Content`Liknar `Clear-Item` , men den fungerar på objekt med innehåll, i stället för objekt med värden.</span><span class="sxs-lookup"><span data-stu-id="365ea-111">The `Clear-Content` is similar to `Clear-Item`, but it works on items with contents, instead of items with values.</span></span>

## <span data-ttu-id="365ea-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="365ea-112">EXAMPLES</span></span>

### <span data-ttu-id="365ea-113">Exempel 1: ta bort allt innehåll från en katalog</span><span class="sxs-lookup"><span data-stu-id="365ea-113">Example 1: Delete all content from a directory</span></span>

```powershell
Clear-Content "..\SmpUsers\*\init.txt"
```

<span data-ttu-id="365ea-114">Det här kommandot tar bort allt innehåll från "init.txt"-filer i alla under kataloger i SmpUsers-katalogen.</span><span class="sxs-lookup"><span data-stu-id="365ea-114">This command deletes all of the content from the "init.txt" files in all subdirectories of the SmpUsers directory.</span></span>
<span data-ttu-id="365ea-115">Filerna tas inte bort, men de är tomma.</span><span class="sxs-lookup"><span data-stu-id="365ea-115">The files are not deleted, but they are empty.</span></span>

### <span data-ttu-id="365ea-116">Exempel 2: ta bort innehållet för alla filer med ett jokertecken</span><span class="sxs-lookup"><span data-stu-id="365ea-116">Example 2: Delete content of all files with a wildcard</span></span>

```powershell
Clear-Content -Path "*" -Filter "*.log" -Force
```

<span data-ttu-id="365ea-117">Det här kommandot tar bort innehållet i alla filer i den aktuella katalogen med fil namns tillägget ". log", inklusive filer med attributet skrivskyddad.</span><span class="sxs-lookup"><span data-stu-id="365ea-117">This command deletes the contents of all files in the current directory with the ".log" file name extension, including files with the read-only attribute.</span></span> <span data-ttu-id="365ea-118">Asterisken ( \* ) i sökvägen representerar alla objekt i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="365ea-118">The asterisk (\*) in the path represents all items in the current directory.</span></span> <span data-ttu-id="365ea-119">**Force** -parametern gör kommandot effektivt på skrivskyddade filer.</span><span class="sxs-lookup"><span data-stu-id="365ea-119">The **Force** parameter makes the command effective on read-only files.</span></span> <span data-ttu-id="365ea-120">Om du använder ett filter för att begränsa kommandot till filer med fil namns tillägget. log i stället för att ange \* . log i sökvägen gör åtgärden snabbare.</span><span class="sxs-lookup"><span data-stu-id="365ea-120">Using a filter to restrict the command to files with the .log file name extension instead of specifying \*.log in the path makes the operation faster.</span></span>

### <span data-ttu-id="365ea-121">Exempel 3: Rensa alla data från en ström</span><span class="sxs-lookup"><span data-stu-id="365ea-121">Example 3: Clear all data from a stream</span></span>

<span data-ttu-id="365ea-122">Det här exemplet visar hur `Clear-Content` cmdleten rensar innehållet från en alternativ data ström och låter strömmen vara intakt.</span><span class="sxs-lookup"><span data-stu-id="365ea-122">This example shows how the `Clear-Content` cmdlet clears the content from an alternate data stream while leaving the stream intact.</span></span>

<span data-ttu-id="365ea-123">Det första kommandot använder `Get-Content` cmdleten för att hämta innehållet i `Zone.Identifier` data strömmen i Copy-Script.ps1-filen, som hämtades från Internet.</span><span class="sxs-lookup"><span data-stu-id="365ea-123">The first command uses the `Get-Content` cmdlet to get the content of the `Zone.Identifier` stream in the Copy-Script.ps1 file, which was downloaded from the Internet.</span></span>

<span data-ttu-id="365ea-124">Det andra kommandot använder `Clear-Content` cmdleten för att rensa innehållet.</span><span class="sxs-lookup"><span data-stu-id="365ea-124">The second command uses the `Clear-Content` cmdlet to clear the content.</span></span>

<span data-ttu-id="365ea-125">Det tredje kommandot upprepar det första kommandot.</span><span class="sxs-lookup"><span data-stu-id="365ea-125">The third command repeats the first command.</span></span> <span data-ttu-id="365ea-126">Den verifierar att innehållet är rensat, men data strömmen är kvar.</span><span class="sxs-lookup"><span data-stu-id="365ea-126">It verifies that the content is cleared, but the stream remains.</span></span> <span data-ttu-id="365ea-127">Om strömmen har tagits bort genererar kommandot ett fel.</span><span class="sxs-lookup"><span data-stu-id="365ea-127">If the stream were deleted, the command would generate an error.</span></span>

<span data-ttu-id="365ea-128">Du kan använda en metod som den här för att rensa innehållet i en alternativ data ström.</span><span class="sxs-lookup"><span data-stu-id="365ea-128">You can use a method like this one to clear the content of an alternate data stream.</span></span> <span data-ttu-id="365ea-129">Det är dock inte det rekommenderade sättet att eliminera säkerhets kontroller som blockerar filer som hämtas från Internet.</span><span class="sxs-lookup"><span data-stu-id="365ea-129">However, it is not the recommended way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="365ea-130">Om du verifierar att en Hämtad fil är säker använder du `Unblock-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="365ea-130">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

```
PS C:\> Get-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier

[ZoneTransfer]
ZoneId=3

PS C:\>Clear-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier

PS C:\>Get-Content C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
PS C:\>
```

## <span data-ttu-id="365ea-131">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="365ea-131">PARAMETERS</span></span>

### <span data-ttu-id="365ea-132">-Stream</span><span class="sxs-lookup"><span data-stu-id="365ea-132">-Stream</span></span>

> [!NOTE]
> <span data-ttu-id="365ea-133">Den här parametern är endast tillgänglig i Windows.</span><span class="sxs-lookup"><span data-stu-id="365ea-133">This Parameter is only available on Windows.</span></span>

<span data-ttu-id="365ea-134">Anger en alternativ data ström för innehåll.</span><span class="sxs-lookup"><span data-stu-id="365ea-134">Specifies an alternative data stream for content.</span></span> <span data-ttu-id="365ea-135">Om data strömmen inte finns skapar den här cmdleten den.</span><span class="sxs-lookup"><span data-stu-id="365ea-135">If the stream does not exist, this cmdlet creates it.</span></span> <span data-ttu-id="365ea-136">Jokertecken stöds inte.</span><span class="sxs-lookup"><span data-stu-id="365ea-136">Wildcard characters are not supported.</span></span>

<span data-ttu-id="365ea-137">**Stream** är en dynamisk parameter som fil Systems leverantören lägger till i `Clear-Content` .</span><span class="sxs-lookup"><span data-stu-id="365ea-137">**Stream** is a dynamic parameter that the FileSystem provider adds to `Clear-Content`.</span></span> <span data-ttu-id="365ea-138">Den här parametern fungerar bara i fil system enheter och tar bort innehållet i alternativa data strömmar på både filer och kataloger.</span><span class="sxs-lookup"><span data-stu-id="365ea-138">This parameter works only in file system drives, and will clear the content of alternative data streams on both files and directories.</span></span>

<span data-ttu-id="365ea-139">Du kan använda `Clear-Content` cmdleten för att ändra innehållet i Amy alternativa data strömmar, till exempel `Zone.Identifier` .</span><span class="sxs-lookup"><span data-stu-id="365ea-139">You can use the `Clear-Content` cmdlet to change the content of amy alternate data stream, such as `Zone.Identifier`.</span></span> <span data-ttu-id="365ea-140">Vi rekommenderar dock inte detta som ett sätt att eliminera säkerhets kontroller som blockerar filer som hämtas från Internet.</span><span class="sxs-lookup"><span data-stu-id="365ea-140">However, we do not recommend this as a way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="365ea-141">Om du verifierar att en Hämtad fil är säker använder du `Unblock-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="365ea-141">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="365ea-142">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="365ea-142">This parameter was introduced in PowerShell 3.0.</span></span> <span data-ttu-id="365ea-143">Från och med PowerShell 7,2 `Clear-Content` kan ta bort innehållet i alternativa data strömmar från kataloger och filer.</span><span class="sxs-lookup"><span data-stu-id="365ea-143">As of PowerShell 7.2, `Clear-Content` can clear the content of alternative data streams from directories as well as files.</span></span>

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

### <span data-ttu-id="365ea-144">-Credential</span><span class="sxs-lookup"><span data-stu-id="365ea-144">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="365ea-145">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="365ea-145">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="365ea-146">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="365ea-146">To impersonate another user, or elevate your credentials when running this cmdlet, use Invoke-Command.</span></span>

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

### <span data-ttu-id="365ea-147">-Undanta</span><span class="sxs-lookup"><span data-stu-id="365ea-147">-Exclude</span></span>

<span data-ttu-id="365ea-148">Anger, som en sträng mat ris, strängar som denna cmdlet utelämnar från sökvägen till innehållet.</span><span class="sxs-lookup"><span data-stu-id="365ea-148">Specifies, as a string array, strings that this cmdlet omits from the path to the content.</span></span> <span data-ttu-id="365ea-149">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="365ea-149">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="365ea-150">Ange ett Sök vägs element eller ett mönster, till exempel "\*. txt".</span><span class="sxs-lookup"><span data-stu-id="365ea-150">Enter a path element or pattern, such as "\*.txt".</span></span> <span data-ttu-id="365ea-151">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="365ea-151">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="365ea-152">-Filter</span><span class="sxs-lookup"><span data-stu-id="365ea-152">-Filter</span></span>

<span data-ttu-id="365ea-153">Anger ett filter i providerns format eller språk.</span><span class="sxs-lookup"><span data-stu-id="365ea-153">Specifies a filter in the provider's format or language.</span></span> <span data-ttu-id="365ea-154">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="365ea-154">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="365ea-155">Syntaxen för filtret, inklusive användning av jokertecken, beror på providern.</span><span class="sxs-lookup"><span data-stu-id="365ea-155">The syntax of the filter, including the use of wildcards, depends on the provider.</span></span> <span data-ttu-id="365ea-156">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när objekten hämtas, i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="365ea-156">Filters are more efficient than other parameters, because the provider applies them when retrieving the objects, rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="365ea-157">-Force</span><span class="sxs-lookup"><span data-stu-id="365ea-157">-Force</span></span>

<span data-ttu-id="365ea-158">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="365ea-158">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="365ea-159">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="365ea-159">-Include</span></span>

<span data-ttu-id="365ea-160">Anger, som en sträng mat ris, innehåll som denna cmdlet rensar.</span><span class="sxs-lookup"><span data-stu-id="365ea-160">Specifies, as a string array, content that this cmdlet clears.</span></span> <span data-ttu-id="365ea-161">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="365ea-161">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="365ea-162">Ange ett Sök vägs element eller ett mönster, till exempel "\*. txt".</span><span class="sxs-lookup"><span data-stu-id="365ea-162">Enter a path element or pattern, such as "\*.txt".</span></span> <span data-ttu-id="365ea-163">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="365ea-163">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="365ea-164">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="365ea-164">-LiteralPath</span></span>

<span data-ttu-id="365ea-165">Anger sökvägar till objekten som innehållet tas bort från.</span><span class="sxs-lookup"><span data-stu-id="365ea-165">Specifies the paths to the items from which content is deleted.</span></span> <span data-ttu-id="365ea-166">Till skillnad från parametern **Path** används värdet för **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="365ea-166">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="365ea-167">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="365ea-167">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="365ea-168">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="365ea-168">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="365ea-169">Enkla citat tecken ser till att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="365ea-169">Single quotation marks tell having PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="365ea-170">-Path</span><span class="sxs-lookup"><span data-stu-id="365ea-170">-Path</span></span>

<span data-ttu-id="365ea-171">Anger sökvägar till objekten som innehållet tas bort från.</span><span class="sxs-lookup"><span data-stu-id="365ea-171">Specifies the paths to the items from which content is deleted.</span></span> <span data-ttu-id="365ea-172">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="365ea-172">Wildcards are permitted.</span></span> <span data-ttu-id="365ea-173">Sök vägarna måste vara sökvägar till objekt, inte behållare.</span><span class="sxs-lookup"><span data-stu-id="365ea-173">The paths must be paths to items, not to containers.</span></span> <span data-ttu-id="365ea-174">Du måste till exempel ange en sökväg till en eller flera filer, inte en sökväg till en katalog.</span><span class="sxs-lookup"><span data-stu-id="365ea-174">For example, you must specify a path to one or more files, not a path to a directory.</span></span> <span data-ttu-id="365ea-175">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="365ea-175">Wildcards are permitted.</span></span> <span data-ttu-id="365ea-176">Den här parametern är obligatorisk, men parameter namnet (sökväg) är valfritt.</span><span class="sxs-lookup"><span data-stu-id="365ea-176">This parameter is required, but the parameter name ("Path") is optional.</span></span>

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

### <span data-ttu-id="365ea-177">-Confirm</span><span class="sxs-lookup"><span data-stu-id="365ea-177">-Confirm</span></span>

<span data-ttu-id="365ea-178">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="365ea-178">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="365ea-179">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="365ea-179">-WhatIf</span></span>

<span data-ttu-id="365ea-180">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="365ea-180">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="365ea-181">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="365ea-181">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="365ea-182">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="365ea-182">CommonParameters</span></span>

<span data-ttu-id="365ea-183">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="365ea-183">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="365ea-184">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="365ea-184">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="365ea-185">INDATA</span><span class="sxs-lookup"><span data-stu-id="365ea-185">INPUTS</span></span>

### <span data-ttu-id="365ea-186">Inget</span><span class="sxs-lookup"><span data-stu-id="365ea-186">None</span></span>

<span data-ttu-id="365ea-187">Det går inte att skicka pipe-objekt till `Clear-Content` .</span><span class="sxs-lookup"><span data-stu-id="365ea-187">You cannot pipe objects to `Clear-Content`.</span></span>

## <span data-ttu-id="365ea-188">UTDATA</span><span class="sxs-lookup"><span data-stu-id="365ea-188">OUTPUTS</span></span>

### <span data-ttu-id="365ea-189">Inget</span><span class="sxs-lookup"><span data-stu-id="365ea-189">None</span></span>

<span data-ttu-id="365ea-190">Denna cmdlet returnerar inga objekt.</span><span class="sxs-lookup"><span data-stu-id="365ea-190">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="365ea-191">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="365ea-191">NOTES</span></span>

<span data-ttu-id="365ea-192">Du kan använda `Clear-Content` med PowerShell-filsystem-providern och med andra leverantörer som hanterar innehåll.</span><span class="sxs-lookup"><span data-stu-id="365ea-192">You can use `Clear-Content` with the PowerShell FileSystem provider and with other providers that manipulate content.</span></span> <span data-ttu-id="365ea-193">Om du vill rensa objekt som inte anses vara innehåll, till exempel objekt som hanteras av PowerShell-certifikatet eller register leverantörer, använder du `Clear-Item` .</span><span class="sxs-lookup"><span data-stu-id="365ea-193">To clear items that are not considered to be content, such as items managed by the PowerShell Certificate or Registry providers, use `Clear-Item`.</span></span>

<span data-ttu-id="365ea-194">`Clear-Content`Cmdleten är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="365ea-194">The `Clear-Content` cmdlet is designed to work with the data exposed by any provider.</span></span>
<span data-ttu-id="365ea-195">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="365ea-195">To list the providers available in your session, type `Get-PsProvider`.</span></span>
<span data-ttu-id="365ea-196">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="365ea-196">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="365ea-197">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="365ea-197">RELATED LINKS</span></span>

[<span data-ttu-id="365ea-198">Lägg till innehåll</span><span class="sxs-lookup"><span data-stu-id="365ea-198">Add-Content</span></span>](Add-Content.md)

[<span data-ttu-id="365ea-199">Hämta innehåll</span><span class="sxs-lookup"><span data-stu-id="365ea-199">Get-Content</span></span>](Get-Content.md)

[<span data-ttu-id="365ea-200">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="365ea-200">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="365ea-201">Ange innehåll</span><span class="sxs-lookup"><span data-stu-id="365ea-201">Set-Content</span></span>](Set-Content.md)

[<span data-ttu-id="365ea-202">about_Providers</span><span class="sxs-lookup"><span data-stu-id="365ea-202">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
