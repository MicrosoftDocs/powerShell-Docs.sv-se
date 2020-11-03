---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/move-item?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Move-Item
ms.openlocfilehash: d3637825e7570e5fb0f3ff77efbc89e9d93974a3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265538"
---
# <span data-ttu-id="ab628-103">Move-Item</span><span class="sxs-lookup"><span data-stu-id="ab628-103">Move-Item</span></span>

## <span data-ttu-id="ab628-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="ab628-104">SYNOPSIS</span></span>
<span data-ttu-id="ab628-105">Flyttar ett objekt från en plats till en annan.</span><span class="sxs-lookup"><span data-stu-id="ab628-105">Moves an item from one location to another.</span></span>

## <span data-ttu-id="ab628-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ab628-106">SYNTAX</span></span>

### <span data-ttu-id="ab628-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="ab628-107">Path (Default)</span></span>

```
Move-Item [-Path] <String[]> [[-Destination] <String>] [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-PassThru] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction]
 [<CommonParameters>]
```

### <span data-ttu-id="ab628-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="ab628-108">LiteralPath</span></span>

```
Move-Item -LiteralPath <String[]> [[-Destination] <String>] [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-PassThru] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-UseTransaction]
 [<CommonParameters>]
```

## <span data-ttu-id="ab628-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ab628-109">DESCRIPTION</span></span>

<span data-ttu-id="ab628-110">`Move-Item`Cmdleten flyttar ett objekt, inklusive dess egenskaper, innehåll och underordnade objekt, från en plats till en annan plats.</span><span class="sxs-lookup"><span data-stu-id="ab628-110">The `Move-Item` cmdlet moves an item, including its properties, contents, and child items, from one location to another location.</span></span>
<span data-ttu-id="ab628-111">Platserna måste stödjas av samma provider.</span><span class="sxs-lookup"><span data-stu-id="ab628-111">The locations must be supported by the same provider.</span></span>
<span data-ttu-id="ab628-112">Till exempel kan den flytta en fil eller under katalog från en katalog till en annan eller flytta en register under nyckel från en nyckel till en annan.</span><span class="sxs-lookup"><span data-stu-id="ab628-112">For example, it can move a file or subdirectory from one directory to another or move a registry subkey from one key to another.</span></span>
<span data-ttu-id="ab628-113">När du flyttar ett objekt läggs det till på den nya platsen och tas bort från den ursprungliga platsen.</span><span class="sxs-lookup"><span data-stu-id="ab628-113">When you move an item, it is added to the new location and deleted from its original location.</span></span>

## <span data-ttu-id="ab628-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="ab628-114">EXAMPLES</span></span>

### <span data-ttu-id="ab628-115">Exempel 1: flytta en fil till en annan katalog och Byt namn på den</span><span class="sxs-lookup"><span data-stu-id="ab628-115">Example 1: Move a file to another directory and rename it</span></span>

<span data-ttu-id="ab628-116">Det här kommandot flyttar Test.txt-filen från `C:` enheten till katalogen "E:\Temp" och byter namn på den från "test.txt" till "tst.txt".</span><span class="sxs-lookup"><span data-stu-id="ab628-116">This command moves the "Test.txt" file from the `C:` drive to the "E:\Temp" directory and renames it from "test.txt" to "tst.txt".</span></span>

```powershell
Move-Item -Path C:\test.txt -Destination E:\Temp\tst.txt
```

### <span data-ttu-id="ab628-117">Exempel 2: flytta en katalog och dess innehåll till en annan katalog</span><span class="sxs-lookup"><span data-stu-id="ab628-117">Example 2: Move a directory and its contents to another directory</span></span>

<span data-ttu-id="ab628-118">Det här kommandot flyttar "C:\Temp"-katalogen och dess innehåll till katalogen ": C:\Logs".</span><span class="sxs-lookup"><span data-stu-id="ab628-118">This command moves the "C:\Temp" directory and its contents to the "C:\Logs" directory.</span></span>
<span data-ttu-id="ab628-119">Katalogen "temp" och alla dess under kataloger och filer visas i katalogen "loggar".</span><span class="sxs-lookup"><span data-stu-id="ab628-119">The "Temp" directory, and all of its subdirectories and files, then appear in the "Logs" directory.</span></span>

```powershell
Move-Item -Path C:\Temp -Destination C:\Logs
```

### <span data-ttu-id="ab628-120">Exempel 3: flytta alla filer för ett angivet tillägg från den aktuella katalogen till en annan katalog</span><span class="sxs-lookup"><span data-stu-id="ab628-120">Example 3: Move all files of a specified extension from the current directory to another directory</span></span>

<span data-ttu-id="ab628-121">Det här kommandot flyttar alla textfiler ("\*. txt") i den aktuella katalogen (som representeras av en punkt ()) till katalogen ": C:\Logs".</span><span class="sxs-lookup"><span data-stu-id="ab628-121">This command moves all of the text files ("\*.txt") in the current directory (represented by a dot ('.')) to the "C:\Logs" directory.</span></span>

```powershell
Move-Item -Path .\*.txt -Destination C:\Logs
```

### <span data-ttu-id="ab628-122">Exempel 4: flytta alla filer i ett angivet tillägg rekursivt från den aktuella katalogen till en annan katalog</span><span class="sxs-lookup"><span data-stu-id="ab628-122">Example 4: Recursively move all files of a specified extension from the current directory to another directory</span></span>

<span data-ttu-id="ab628-123">Det här kommandot flyttar alla textfiler från den aktuella katalogen och alla under kataloger, rekursivt, till katalogen "C:\TextFiles".</span><span class="sxs-lookup"><span data-stu-id="ab628-123">This command moves all of the text files from the current directory and all subdirectories, recursively, to the "C:\TextFiles" directory.</span></span>

<span data-ttu-id="ab628-124">Kommandot använder `Get-ChildItem` cmdleten för att hämta alla underordnade objekt i den aktuella katalogen (representeras av punkten \[ . \] ) och dess under kataloger som har *fil namns tillägget ". txt". Parametern **rekursivt** används för att göra hämtningen rekursiv och include-parametern för att begränsa hämtningen till "*. txt"-filer.</span><span class="sxs-lookup"><span data-stu-id="ab628-124">The command uses the `Get-ChildItem` cmdlet to get all of the child items in the current directory (represented by the dot \[.\]) and its subdirectories that have a " *.txt" file name extension. It uses the **Recurse** parameter to make the retrieval recursive and the Include parameter to limit the retrieval to "*.txt" files.</span></span>

<span data-ttu-id="ab628-125">Pipeline-operatorn ( `|` ) skickar resultatet från det här kommandot till `Move-Item` , som flyttar textfilerna till katalogen "TextFiles".</span><span class="sxs-lookup"><span data-stu-id="ab628-125">The pipeline operator (`|`) sends the results of this command to `Move-Item`, which moves the text files to the "TextFiles" directory.</span></span>

<span data-ttu-id="ab628-126">Om filer som ska flyttas till "C:\Textfiles" har samma namn, `Move-Item` visar ett fel och fortsätter, men flyttar bara en fil med varje namn till "C:\Textfiles".</span><span class="sxs-lookup"><span data-stu-id="ab628-126">If files that are to be moved to "C:\Textfiles" have the same name, `Move-Item` displays an error and continues, but it moves only one file with each name to "C:\Textfiles".</span></span>
<span data-ttu-id="ab628-127">De andra filerna finns kvar i sina ursprungliga kataloger.</span><span class="sxs-lookup"><span data-stu-id="ab628-127">The other files remain in their original directories.</span></span>

<span data-ttu-id="ab628-128">Om katalogen "textfiles" (eller något annat element i mål Sök vägen) inte finns, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="ab628-128">If the "Textfiles" directory (or any other element of the destination path) does not exist, the command fails.</span></span>
<span data-ttu-id="ab628-129">Den saknade katalogen skapas inte åt dig, även om du använder **Force** -parametern.</span><span class="sxs-lookup"><span data-stu-id="ab628-129">The missing directory is not created for you, even if you use the **Force** parameter.</span></span>
<span data-ttu-id="ab628-130">`Move-Item` flyttar det första objektet till en fil med namnet "textfiles" och visar sedan ett fel som förklarar att filen redan finns.</span><span class="sxs-lookup"><span data-stu-id="ab628-130">`Move-Item` moves the first item to a file called "Textfiles" and then displays an error explaining that the file already exists.</span></span>

<span data-ttu-id="ab628-131">`Get-ChildItem`Inte heller flyttar dolda filer som standard.</span><span class="sxs-lookup"><span data-stu-id="ab628-131">Also, by default, `Get-ChildItem` does not move hidden files.</span></span>
<span data-ttu-id="ab628-132">Om du vill flytta dolda filer använder du parametern **Force** med `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="ab628-132">To move hidden files, use the **Force** parameter with `Get-ChildItem`.</span></span>

<span data-ttu-id="ab628-133">Obs! i Windows PowerShell 2,0 **Recurse** `Get-ChildItem` måste värdet för **Sök vägs** parametern vara en behållare när du använder rekursivt-parametern för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ab628-133">Note: In Windows PowerShell 2.0, when using the **Recurse** parameter of the `Get-ChildItem` cmdlet, the value of the **Path** parameter must be a container.</span></span>
<span data-ttu-id="ab628-134">Använd parametern **include** för att ange fil namns filtret. txt ( `Get-ChildItem -Path .\* -Include *.txt -Recurse | Move-Item -Destination C:\TextFiles` ).</span><span class="sxs-lookup"><span data-stu-id="ab628-134">Use the **Include** parameter to specify the .txt file name extension filter (`Get-ChildItem -Path .\* -Include *.txt -Recurse | Move-Item -Destination C:\TextFiles`).</span></span>

```powershell
Get-ChildItem -Path ".\*.txt" -Recurse | Move-Item -Destination "C:\TextFiles"
```

### <span data-ttu-id="ab628-135">Exempel 5: flytta register nycklar och värden till en annan nyckel</span><span class="sxs-lookup"><span data-stu-id="ab628-135">Example 5: Move registry keys and values to another key</span></span>

<span data-ttu-id="ab628-136">Detta kommando flyttar register nycklar och värden i register nyckeln "mina företag" i "HKLM\Software" till nyckeln "MyNewCompany".</span><span class="sxs-lookup"><span data-stu-id="ab628-136">This command moves the registry keys and values within the "MyCompany" registry key in "HKLM\Software" to the "MyNewCompany" key.</span></span>
<span data-ttu-id="ab628-137">Jokertecknet (\*) anger att innehållet i nyckeln "företaget" ska flyttas, inte själva nyckeln.</span><span class="sxs-lookup"><span data-stu-id="ab628-137">The wildcard character ('\*') indicates that the contents of the "MyCompany" key should be moved, not the key itself.</span></span>
<span data-ttu-id="ab628-138">I det här kommandot utelämnas de valfria **Sök vägs** -och **mål** parameter namnen.</span><span class="sxs-lookup"><span data-stu-id="ab628-138">In this command, the optional **Path** and **Destination** parameter names are omitted.</span></span>

```powershell
Move-Item "HKLM:\software\mycompany\*" "HKLM:\software\mynewcompany"
```

### <span data-ttu-id="ab628-139">Exempel 6: flytta en katalog och dess innehåll till en under katalog till den angivna katalogen</span><span class="sxs-lookup"><span data-stu-id="ab628-139">Example 6: Move a directory and its contents to a subdirectory of the specified directory</span></span>

<span data-ttu-id="ab628-140">Detta kommando flyttar katalogen "loggar \[ september \` 06 \] " (och dess innehåll) till katalogen "logs \[ 2006 \] ".</span><span class="sxs-lookup"><span data-stu-id="ab628-140">This command moves the "Logs\[Sept\`06\]" directory (and its contents) into the "Logs\[2006\]" directory.</span></span>

<span data-ttu-id="ab628-141">Parametern **LiteralPath** används i stället för **Path** , eftersom det ursprungliga katalog namnet innehåller vänster hak paren tes tecken (" \[ " och " \] ").</span><span class="sxs-lookup"><span data-stu-id="ab628-141">The **LiteralPath** parameter is used instead of **Path** , because the original directory name includes left bracket and right bracket characters ("\[" and "\]").</span></span>
<span data-ttu-id="ab628-142">Sökvägen omges också av enkla citat tecken (""), så att bakstrecks symbolen ( \` ) inte tolkas.</span><span class="sxs-lookup"><span data-stu-id="ab628-142">The path is also enclosed in single quotation marks (' '), so that the backtick symbol (\`) is not misinterpreted.</span></span>

<span data-ttu-id="ab628-143">**Mål** parametern kräver ingen literal sökväg, eftersom mål variabeln också måste omges av enkla citat tecken, eftersom den innehåller hakparenteser som kan vara feltolkade.</span><span class="sxs-lookup"><span data-stu-id="ab628-143">The **Destination** parameter does not require a literal path, because the Destination variable also must be enclosed in single quotation marks, because it includes brackets that can be misinterpreted.</span></span>

```powershell
Move-Item -LiteralPath 'Logs[Sept`06]' -Destination 'Logs[2006]'
```

## <span data-ttu-id="ab628-144">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="ab628-144">PARAMETERS</span></span>

### <span data-ttu-id="ab628-145">-Credential</span><span class="sxs-lookup"><span data-stu-id="ab628-145">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="ab628-146">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ab628-146">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="ab628-147">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="ab628-147">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="ab628-148">-Mål</span><span class="sxs-lookup"><span data-stu-id="ab628-148">-Destination</span></span>

<span data-ttu-id="ab628-149">Anger sökvägen till den plats där objekten flyttas.</span><span class="sxs-lookup"><span data-stu-id="ab628-149">Specifies the path to the location where the items are being moved.</span></span>
<span data-ttu-id="ab628-150">Standardvärdet är den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="ab628-150">The default is the current directory.</span></span>
<span data-ttu-id="ab628-151">Jokertecken tillåts, men resultatet måste ange en enda plats.</span><span class="sxs-lookup"><span data-stu-id="ab628-151">Wildcards are permitted, but the result must specify a single location.</span></span>

<span data-ttu-id="ab628-152">Om du vill byta namn på objektet som flyttas anger du ett nytt namn i värdet för **mål** parametern.</span><span class="sxs-lookup"><span data-stu-id="ab628-152">To rename the item being moved, specify a new name in the value of the **Destination** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: Current directory
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="ab628-153">-Undanta</span><span class="sxs-lookup"><span data-stu-id="ab628-153">-Exclude</span></span>

<span data-ttu-id="ab628-154">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar från åtgärden.</span><span class="sxs-lookup"><span data-stu-id="ab628-154">Specifies, as a string array, an item or items that this cmdlet excludes from the operation.</span></span>
<span data-ttu-id="ab628-155">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="ab628-155">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="ab628-156">Ange ett Sök vägs element eller ett mönster, till exempel "\*. txt".</span><span class="sxs-lookup"><span data-stu-id="ab628-156">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="ab628-157">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="ab628-157">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="ab628-158">-Filter</span><span class="sxs-lookup"><span data-stu-id="ab628-158">-Filter</span></span>

<span data-ttu-id="ab628-159">Anger ett filter i formatet eller språket för providern.</span><span class="sxs-lookup"><span data-stu-id="ab628-159">Specifies a filter in the format or language of the provider.</span></span>
<span data-ttu-id="ab628-160">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="ab628-160">The value of this parameter qualifies the **Path** parameter.</span></span>

<span data-ttu-id="ab628-161">Syntaxen för filtret, inklusive användning av jokertecken, är beroende av providern.</span><span class="sxs-lookup"><span data-stu-id="ab628-161">The syntax of the filter, including the use of wildcard characters, depends on the provider.</span></span>
<span data-ttu-id="ab628-162">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="ab628-162">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="ab628-163">-Force</span><span class="sxs-lookup"><span data-stu-id="ab628-163">-Force</span></span>

<span data-ttu-id="ab628-164">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="ab628-164">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="ab628-165">Implementeringen varierar från providern till providern.</span><span class="sxs-lookup"><span data-stu-id="ab628-165">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="ab628-166">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="ab628-166">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="ab628-167">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="ab628-167">-Include</span></span>

<span data-ttu-id="ab628-168">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet flyttar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="ab628-168">Specifies, as a string array, an item or items that this cmdlet moves in the operation.</span></span>
<span data-ttu-id="ab628-169">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="ab628-169">The value of this parameter qualifies the **Path** parameter.</span></span>
<span data-ttu-id="ab628-170">Ange ett Sök vägs element eller ett mönster, till exempel "\*. txt".</span><span class="sxs-lookup"><span data-stu-id="ab628-170">Enter a path element or pattern, such as "\*.txt".</span></span>
<span data-ttu-id="ab628-171">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="ab628-171">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="ab628-172">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="ab628-172">-LiteralPath</span></span>

<span data-ttu-id="ab628-173">Anger sökvägen till objektets aktuella plats.</span><span class="sxs-lookup"><span data-stu-id="ab628-173">Specifies the path to the current location of the items.</span></span>
<span data-ttu-id="ab628-174">Till skillnad från parametern **Path** används värdet för **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="ab628-174">Unlike the **Path** parameter, the value of **LiteralPath** is used exactly as it is typed.</span></span>
<span data-ttu-id="ab628-175">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="ab628-175">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="ab628-176">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="ab628-176">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="ab628-177">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="ab628-177">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="ab628-178">– PassThru</span><span class="sxs-lookup"><span data-stu-id="ab628-178">-PassThru</span></span>

<span data-ttu-id="ab628-179">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="ab628-179">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="ab628-180">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="ab628-180">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="ab628-181">-Path</span><span class="sxs-lookup"><span data-stu-id="ab628-181">-Path</span></span>

<span data-ttu-id="ab628-182">Anger sökvägen till objektets aktuella plats.</span><span class="sxs-lookup"><span data-stu-id="ab628-182">Specifies the path to the current location of the items.</span></span>
<span data-ttu-id="ab628-183">Standardvärdet är den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="ab628-183">The default is the current directory.</span></span>
<span data-ttu-id="ab628-184">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="ab628-184">Wildcard characters are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: Current directory
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="ab628-185">– UseTransaction</span><span class="sxs-lookup"><span data-stu-id="ab628-185">-UseTransaction</span></span>

<span data-ttu-id="ab628-186">Inkluderar kommandot i den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="ab628-186">Includes the command in the active transaction.</span></span>
<span data-ttu-id="ab628-187">Den här parametern är bara giltig medan en transaktion pågår.</span><span class="sxs-lookup"><span data-stu-id="ab628-187">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="ab628-188">Mer information finns i about_Transactions.</span><span class="sxs-lookup"><span data-stu-id="ab628-188">For more information, see about_Transactions.</span></span>

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

### <span data-ttu-id="ab628-189">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ab628-189">-Confirm</span></span>

<span data-ttu-id="ab628-190">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ab628-190">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ab628-191">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ab628-191">-WhatIf</span></span>

<span data-ttu-id="ab628-192">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="ab628-192">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="ab628-193">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="ab628-193">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="ab628-194">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ab628-194">CommonParameters</span></span>

<span data-ttu-id="ab628-195">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="ab628-195">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="ab628-196">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="ab628-196">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="ab628-197">INDATA</span><span class="sxs-lookup"><span data-stu-id="ab628-197">INPUTS</span></span>

### <span data-ttu-id="ab628-198">System. String</span><span class="sxs-lookup"><span data-stu-id="ab628-198">System.String</span></span>

<span data-ttu-id="ab628-199">Du kan skicka vidare en sträng som innehåller en sökväg till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ab628-199">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="ab628-200">UTDATA</span><span class="sxs-lookup"><span data-stu-id="ab628-200">OUTPUTS</span></span>

### <span data-ttu-id="ab628-201">Ingen eller ett objekt som representerar det flyttade objektet.</span><span class="sxs-lookup"><span data-stu-id="ab628-201">None or an object representing the moved item.</span></span>

<span data-ttu-id="ab628-202">När du använder parametern *Passthru* genererar denna cmdlet ett objekt som representerar det flyttade objektet.</span><span class="sxs-lookup"><span data-stu-id="ab628-202">When you use the *PassThru* parameter, this cmdlet generates an object representing the moved item.</span></span>
<span data-ttu-id="ab628-203">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="ab628-203">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="ab628-204">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="ab628-204">NOTES</span></span>

<span data-ttu-id="ab628-205">Den här cmdleten flyttar filer mellan enheter som stöds av samma provider, men kommer bara att flytta kataloger inom samma enhet.</span><span class="sxs-lookup"><span data-stu-id="ab628-205">This cmdlet will move files between drives that are supported by the same provider, but it will move directories only within the same drive.</span></span>

<span data-ttu-id="ab628-206">Eftersom ett `Move-Item` kommando flyttar egenskaper, innehåll och underordnade objekt i ett objekt, är alla flyttningar rekursiva som standard.</span><span class="sxs-lookup"><span data-stu-id="ab628-206">Because a `Move-Item` command moves the properties, contents, and child items of an item, all moves are recursive by default.</span></span>

<span data-ttu-id="ab628-207">Denna cmdlet är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="ab628-207">This cmdlet is designed to work with the data exposed by any provider.</span></span>
<span data-ttu-id="ab628-208">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="ab628-208">To list the providers available in your session, type `Get-PSProvider`.</span></span>
<span data-ttu-id="ab628-209">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="ab628-209">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="ab628-210">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="ab628-210">RELATED LINKS</span></span>

[<span data-ttu-id="ab628-211">Rensa objekt</span><span class="sxs-lookup"><span data-stu-id="ab628-211">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="ab628-212">Kopiera objekt</span><span class="sxs-lookup"><span data-stu-id="ab628-212">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="ab628-213">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="ab628-213">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="ab628-214">Anropa-objekt</span><span class="sxs-lookup"><span data-stu-id="ab628-214">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="ab628-215">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="ab628-215">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="ab628-216">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="ab628-216">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="ab628-217">Byt namn – objekt</span><span class="sxs-lookup"><span data-stu-id="ab628-217">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="ab628-218">Ange objekt</span><span class="sxs-lookup"><span data-stu-id="ab628-218">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="ab628-219">about_Providers</span><span class="sxs-lookup"><span data-stu-id="ab628-219">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)
