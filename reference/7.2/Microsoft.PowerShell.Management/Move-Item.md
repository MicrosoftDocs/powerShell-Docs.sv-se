---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 05/14/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/move-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Move-Item
ms.openlocfilehash: a47c017371fe5fe87618c11551cd1ecba76d5c60
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710429"
---
# <span data-ttu-id="7d8c6-102">Move-Item</span><span class="sxs-lookup"><span data-stu-id="7d8c6-102">Move-Item</span></span>

## <span data-ttu-id="7d8c6-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="7d8c6-103">SYNOPSIS</span></span>
<span data-ttu-id="7d8c6-104">Flyttar ett objekt från en plats till en annan.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-104">Moves an item from one location to another.</span></span>

## <span data-ttu-id="7d8c6-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7d8c6-105">SYNTAX</span></span>

### <span data-ttu-id="7d8c6-106">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="7d8c6-106">Path (Default)</span></span>

```
Move-Item [-Path] <String[]> [[-Destination] <String>] [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-PassThru] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="7d8c6-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="7d8c6-107">LiteralPath</span></span>

```
Move-Item -LiteralPath <String[]> [[-Destination] <String>] [-Force] [-Filter <String>] [-Include <String[]>]
 [-Exclude <String[]>] [-PassThru] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="7d8c6-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="7d8c6-108">DESCRIPTION</span></span>

<span data-ttu-id="7d8c6-109">`Move-Item`Cmdleten flyttar ett objekt, inklusive dess egenskaper, innehåll och underordnade objekt, från en plats till en annan plats.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-109">The `Move-Item` cmdlet moves an item, including its properties, contents, and child items, from one location to another location.</span></span> <span data-ttu-id="7d8c6-110">Platserna måste stödjas av samma provider.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-110">The locations must be supported by the same provider.</span></span>
<span data-ttu-id="7d8c6-111">Till exempel kan den flytta en fil eller under katalog från en katalog till en annan eller flytta en register under nyckel från en nyckel till en annan.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-111">For example, it can move a file or subdirectory from one directory to another or move a registry subkey from one key to another.</span></span>
<span data-ttu-id="7d8c6-112">När du flyttar ett objekt läggs det till på den nya platsen och tas bort från den ursprungliga platsen.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-112">When you move an item, it is added to the new location and deleted from its original location.</span></span>

## <span data-ttu-id="7d8c6-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="7d8c6-113">EXAMPLES</span></span>

### <span data-ttu-id="7d8c6-114">Exempel 1: flytta en fil till en annan katalog och Byt namn på den</span><span class="sxs-lookup"><span data-stu-id="7d8c6-114">Example 1: Move a file to another directory and rename it</span></span>

<span data-ttu-id="7d8c6-115">Det här kommandot flyttar `Test.txt` filen från `C:` enheten till `E:\Temp` katalogen och byter namn till den från `test.txt` till `tst.txt` .</span><span class="sxs-lookup"><span data-stu-id="7d8c6-115">This command moves the `Test.txt` file from the `C:` drive to the `E:\Temp` directory and renames it from `test.txt` to `tst.txt`.</span></span>

```powershell
Move-Item -Path C:\test.txt -Destination E:\Temp\tst.txt
```

### <span data-ttu-id="7d8c6-116">Exempel 2: flytta en katalog och dess innehåll till en annan katalog</span><span class="sxs-lookup"><span data-stu-id="7d8c6-116">Example 2: Move a directory and its contents to another directory</span></span>

<span data-ttu-id="7d8c6-117">Detta kommando flyttar `C:\Temp` katalogen och dess innehåll till `C:\Logs` katalogen.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-117">This command moves the `C:\Temp` directory and its contents to the `C:\Logs` directory.</span></span>
<span data-ttu-id="7d8c6-118">Katalogen "temp" och alla dess under kataloger och filer visas i katalogen "loggar".</span><span class="sxs-lookup"><span data-stu-id="7d8c6-118">The "Temp" directory, and all of its subdirectories and files, then appear in the "Logs" directory.</span></span>

```powershell
Move-Item -Path C:\Temp -Destination C:\Logs
```

### <span data-ttu-id="7d8c6-119">Exempel 3: flytta alla filer för ett angivet tillägg från den aktuella katalogen till en annan katalog</span><span class="sxs-lookup"><span data-stu-id="7d8c6-119">Example 3: Move all files of a specified extension from the current directory to another directory</span></span>

<span data-ttu-id="7d8c6-120">Detta kommando flyttar alla textfiler ( `*.txt` ) i den aktuella katalogen (som representeras av en punkt ( `.` )) till `C:\Logs` katalogen.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-120">This command moves all of the text files (`*.txt`) in the current directory (represented by a dot (`.`)) to the `C:\Logs` directory.</span></span>

```powershell
Move-Item -Path .\*.txt -Destination C:\Logs
```

### <span data-ttu-id="7d8c6-121">Exempel 4: flytta alla filer i ett angivet tillägg rekursivt från den aktuella katalogen till en annan katalog</span><span class="sxs-lookup"><span data-stu-id="7d8c6-121">Example 4: Recursively move all files of a specified extension from the current directory to another directory</span></span>

<span data-ttu-id="7d8c6-122">Det här kommandot flyttar alla textfiler från den aktuella katalogen och alla under kataloger, rekursivt, till katalogen "C:\TextFiles".</span><span class="sxs-lookup"><span data-stu-id="7d8c6-122">This command moves all of the text files from the current directory and all subdirectories, recursively, to the "C:\TextFiles" directory.</span></span>

```powershell
Get-ChildItem -Path ".\*.txt" -Recurse | Move-Item -Destination "C:\TextFiles"
```

<span data-ttu-id="7d8c6-123">Kommandot använder `Get-ChildItem` cmdleten för att hämta alla underordnade objekt i den aktuella katalogen (representeras av punkten \[ . \] ) och dess under kataloger som har *fil namns tillägget ". txt". Parametern **rekursivt** används för att göra hämtningen rekursiv och include-parametern för att begränsa hämtningen till "*. txt"-filer.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-123">The command uses the `Get-ChildItem` cmdlet to get all of the child items in the current directory (represented by the dot \[.\]) and its subdirectories that have a "*.txt" file name extension. It uses the **Recurse** parameter to make the retrieval recursive and the Include parameter to limit the retrieval to "*.txt" files.</span></span>

<span data-ttu-id="7d8c6-124">Pipeline-operatorn ( `|` ) skickar resultatet från det här kommandot till `Move-Item` , som flyttar textfilerna till katalogen "TextFiles".</span><span class="sxs-lookup"><span data-stu-id="7d8c6-124">The pipeline operator (`|`) sends the results of this command to `Move-Item`, which moves the text files to the "TextFiles" directory.</span></span>

<span data-ttu-id="7d8c6-125">Om filer som ska flyttas till "C:\Textfiles" har samma namn, `Move-Item` visar ett fel och fortsätter, men flyttar bara en fil med varje namn till "C:\Textfiles".</span><span class="sxs-lookup"><span data-stu-id="7d8c6-125">If files that are to be moved to "C:\Textfiles" have the same name, `Move-Item` displays an error and continues, but it moves only one file with each name to "C:\Textfiles".</span></span>
<span data-ttu-id="7d8c6-126">De andra filerna finns kvar i sina ursprungliga kataloger.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-126">The other files remain in their original directories.</span></span>

<span data-ttu-id="7d8c6-127">Om katalogen "textfiles" (eller något annat element i mål Sök vägen) inte finns, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-127">If the "Textfiles" directory (or any other element of the destination path) does not exist, the command fails.</span></span>
<span data-ttu-id="7d8c6-128">Den saknade katalogen skapas inte åt dig, även om du använder **Force** -parametern.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-128">The missing directory is not created for you, even if you use the **Force** parameter.</span></span>
<span data-ttu-id="7d8c6-129">`Move-Item` flyttar det första objektet till en fil med namnet "textfiles" och visar sedan ett fel som förklarar att filen redan finns.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-129">`Move-Item` moves the first item to a file called "Textfiles" and then displays an error explaining that the file already exists.</span></span>

<span data-ttu-id="7d8c6-130">`Get-ChildItem`Inte heller flyttar dolda filer som standard.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-130">Also, by default, `Get-ChildItem` does not move hidden files.</span></span>
<span data-ttu-id="7d8c6-131">Om du vill flytta dolda filer använder du parametern **Force** med `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="7d8c6-131">To move hidden files, use the **Force** parameter with `Get-ChildItem`.</span></span>

> [!NOTE]
> <span data-ttu-id="7d8c6-132">I Windows PowerShell 2,0  `Get-ChildItem` måste värdet för **Sök vägs** parametern vara en behållare när du använder rekursivt-parametern för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-132">In Windows PowerShell 2.0, when using the **Recurse** parameter of the `Get-ChildItem` cmdlet, the value of the **Path** parameter must be a container.</span></span>
> <span data-ttu-id="7d8c6-133">Använd parametern **include** för att ange fil namns filtret. txt ( `Get-ChildItem -Path .\* -Include *.txt -Recurse | Move-Item -Destination C:\TextFiles` ).</span><span class="sxs-lookup"><span data-stu-id="7d8c6-133">Use the **Include** parameter to specify the .txt file name extension filter (`Get-ChildItem -Path .\* -Include *.txt -Recurse | Move-Item -Destination C:\TextFiles`).</span></span>

### <span data-ttu-id="7d8c6-134">Exempel 5: flytta register nycklar och värden till en annan nyckel</span><span class="sxs-lookup"><span data-stu-id="7d8c6-134">Example 5: Move registry keys and values to another key</span></span>

<span data-ttu-id="7d8c6-135">Det här kommandot flyttar register nycklar och värden i register nyckeln "mina företag" i `HKLM\Software` till nyckeln "MyNewCompany".</span><span class="sxs-lookup"><span data-stu-id="7d8c6-135">This command moves the registry keys and values within the "MyCompany" registry key in `HKLM\Software` to the "MyNewCompany" key.</span></span>
<span data-ttu-id="7d8c6-136">Jokertecknet ( `*` ) anger att innehållet i nyckeln "företaget" ska flyttas, inte själva nyckeln.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-136">The wildcard character (`*`) indicates that the contents of the "MyCompany" key should be moved, not the key itself.</span></span>
<span data-ttu-id="7d8c6-137">I det här kommandot utelämnas de valfria **Sök vägs** -och **mål** parameter namnen.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-137">In this command, the optional **Path** and **Destination** parameter names are omitted.</span></span>

```powershell
Move-Item "HKLM:\software\mycompany\*" "HKLM:\software\mynewcompany"
```

### <span data-ttu-id="7d8c6-138">Exempel 6: flytta en katalog och dess innehåll till en under katalog till den angivna katalogen</span><span class="sxs-lookup"><span data-stu-id="7d8c6-138">Example 6: Move a directory and its contents to a subdirectory of the specified directory</span></span>

<span data-ttu-id="7d8c6-139">Detta kommando flyttar katalogen "loggar \[ september \` 06 \] " (och dess innehåll) till katalogen "logs \[ 2006 \] ".</span><span class="sxs-lookup"><span data-stu-id="7d8c6-139">This command moves the "Logs\[Sept\`06\]" directory (and its contents) into the "Logs\[2006\]" directory.</span></span>

```powershell
Move-Item -LiteralPath 'Logs[Sept`06]' -Destination 'Logs[2006]'
```

<span data-ttu-id="7d8c6-140">Parametern **LiteralPath** används i stället för **Path**, eftersom det ursprungliga katalog namnet innehåller vänster hak paren tes tecken (" \[ " och " \] ").</span><span class="sxs-lookup"><span data-stu-id="7d8c6-140">The **LiteralPath** parameter is used instead of **Path**, because the original directory name includes left bracket and right bracket characters ("\[" and "\]").</span></span>
<span data-ttu-id="7d8c6-141">Sökvägen omges också av enkla citat tecken (""), så att bakstrecks symbolen ( \` ) inte tolkas.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-141">The path is also enclosed in single quotation marks (' '), so that the backtick symbol (\`) is not misinterpreted.</span></span>

<span data-ttu-id="7d8c6-142">**Mål** parametern kräver ingen literal sökväg, eftersom mål variabeln också måste omges av enkla citat tecken, eftersom den innehåller hakparenteser som kan vara feltolkade.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-142">The **Destination** parameter does not require a literal path, because the Destination variable also must be enclosed in single quotation marks, because it includes brackets that can be misinterpreted.</span></span>

## <span data-ttu-id="7d8c6-143">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="7d8c6-143">PARAMETERS</span></span>

### <span data-ttu-id="7d8c6-144">-Credential</span><span class="sxs-lookup"><span data-stu-id="7d8c6-144">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="7d8c6-145">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-145">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="7d8c6-146">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="7d8c6-146">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="7d8c6-147">-Mål</span><span class="sxs-lookup"><span data-stu-id="7d8c6-147">-Destination</span></span>

<span data-ttu-id="7d8c6-148">Anger sökvägen till den plats där objekten flyttas.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-148">Specifies the path to the location where the items are being moved.</span></span>
<span data-ttu-id="7d8c6-149">Standardvärdet är den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-149">The default is the current directory.</span></span>
<span data-ttu-id="7d8c6-150">Jokertecken tillåts, men resultatet måste ange en enda plats.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-150">Wildcards are permitted, but the result must specify a single location.</span></span>

<span data-ttu-id="7d8c6-151">Om du vill byta namn på objektet som flyttas anger du ett nytt namn i värdet för **mål** parametern.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-151">To rename the item being moved, specify a new name in the value of the **Destination** parameter.</span></span>

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

### <span data-ttu-id="7d8c6-152">-Undanta</span><span class="sxs-lookup"><span data-stu-id="7d8c6-152">-Exclude</span></span>

<span data-ttu-id="7d8c6-153">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-153">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="7d8c6-154">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="7d8c6-154">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="7d8c6-155">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="7d8c6-155">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="7d8c6-156">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-156">Wildcard characters are permitted.</span></span> <span data-ttu-id="7d8c6-157">Parametern **exclude** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-157">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="7d8c6-158">-Filter</span><span class="sxs-lookup"><span data-stu-id="7d8c6-158">-Filter</span></span>

<span data-ttu-id="7d8c6-159">Anger ett filter för att kvalificera **Sök vägs** parametern.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-159">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="7d8c6-160">[Fil Systems](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) leverantören är den enda installerade PowerShell-providern som stöder användningen av filter.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-160">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="7d8c6-161">Du kan hitta syntaxen för filter språket för **fil systemet** i [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="7d8c6-161">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="7d8c6-162">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-162">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="7d8c6-163">-Force</span><span class="sxs-lookup"><span data-stu-id="7d8c6-163">-Force</span></span>

<span data-ttu-id="7d8c6-164">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-164">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="7d8c6-165">Implementeringen varierar från providern till providern.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-165">Implementation varies from provider to provider.</span></span>
<span data-ttu-id="7d8c6-166">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="7d8c6-166">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

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

### <span data-ttu-id="7d8c6-167">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="7d8c6-167">-Include</span></span>

<span data-ttu-id="7d8c6-168">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-168">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="7d8c6-169">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="7d8c6-169">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="7d8c6-170">Ange ett Sök vägs element eller ett mönster, till exempel `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="7d8c6-170">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="7d8c6-171">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-171">Wildcard characters are permitted.</span></span> <span data-ttu-id="7d8c6-172">Parametern **include** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-172">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="7d8c6-173">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="7d8c6-173">-LiteralPath</span></span>

<span data-ttu-id="7d8c6-174">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-174">Specifies a path to one or more locations.</span></span> <span data-ttu-id="7d8c6-175">Värdet för **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-175">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="7d8c6-176">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-176">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="7d8c6-177">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-177">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="7d8c6-178">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-178">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="7d8c6-179">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="7d8c6-179">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="7d8c6-180">– PassThru</span><span class="sxs-lookup"><span data-stu-id="7d8c6-180">-PassThru</span></span>

<span data-ttu-id="7d8c6-181">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-181">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="7d8c6-182">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-182">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="7d8c6-183">-Path</span><span class="sxs-lookup"><span data-stu-id="7d8c6-183">-Path</span></span>

<span data-ttu-id="7d8c6-184">Anger sökvägen till objektets aktuella plats.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-184">Specifies the path to the current location of the items.</span></span>
<span data-ttu-id="7d8c6-185">Standardvärdet är den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-185">The default is the current directory.</span></span>
<span data-ttu-id="7d8c6-186">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-186">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="7d8c6-187">-Confirm</span><span class="sxs-lookup"><span data-stu-id="7d8c6-187">-Confirm</span></span>

<span data-ttu-id="7d8c6-188">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-188">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="7d8c6-189">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="7d8c6-189">-WhatIf</span></span>

<span data-ttu-id="7d8c6-190">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-190">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="7d8c6-191">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-191">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="7d8c6-192">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7d8c6-192">CommonParameters</span></span>

<span data-ttu-id="7d8c6-193">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="7d8c6-193">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="7d8c6-194">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="7d8c6-194">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="7d8c6-195">INDATA</span><span class="sxs-lookup"><span data-stu-id="7d8c6-195">INPUTS</span></span>

### <span data-ttu-id="7d8c6-196">System. String</span><span class="sxs-lookup"><span data-stu-id="7d8c6-196">System.String</span></span>

<span data-ttu-id="7d8c6-197">Du kan skicka vidare en sträng som innehåller en sökväg till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-197">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="7d8c6-198">UTDATA</span><span class="sxs-lookup"><span data-stu-id="7d8c6-198">OUTPUTS</span></span>

### <span data-ttu-id="7d8c6-199">Ingen eller ett objekt som representerar det flyttade objektet</span><span class="sxs-lookup"><span data-stu-id="7d8c6-199">None or an object representing the moved item</span></span>

<span data-ttu-id="7d8c6-200">När du använder parametern *Passthru* genererar denna cmdlet ett objekt som representerar det flyttade objektet.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-200">When you use the *PassThru* parameter, this cmdlet generates an object representing the moved item.</span></span>
<span data-ttu-id="7d8c6-201">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-201">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="7d8c6-202">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="7d8c6-202">NOTES</span></span>

- <span data-ttu-id="7d8c6-203">Den här cmdleten flyttar filer mellan enheter som stöds av samma provider, men kommer bara att flytta kataloger inom samma enhet.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-203">This cmdlet will move files between drives that are supported by the same provider, but it will move directories only within the same drive.</span></span>
- <span data-ttu-id="7d8c6-204">Eftersom ett `Move-Item` kommando flyttar egenskaper, innehåll och underordnade objekt i ett objekt, är alla flyttningar rekursiva som standard.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-204">Because a `Move-Item` command moves the properties, contents, and child items of an item, all moves are recursive by default.</span></span>
- <span data-ttu-id="7d8c6-205">Denna cmdlet är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="7d8c6-205">This cmdlet is designed to work with the data exposed by any provider.</span></span>
  <span data-ttu-id="7d8c6-206">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PSProvider` .</span><span class="sxs-lookup"><span data-stu-id="7d8c6-206">To list the providers available in your session, type `Get-PSProvider`.</span></span>
  <span data-ttu-id="7d8c6-207">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="7d8c6-207">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="7d8c6-208">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="7d8c6-208">RELATED LINKS</span></span>

[<span data-ttu-id="7d8c6-209">Rensa objekt</span><span class="sxs-lookup"><span data-stu-id="7d8c6-209">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="7d8c6-210">Kopiera objekt</span><span class="sxs-lookup"><span data-stu-id="7d8c6-210">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="7d8c6-211">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="7d8c6-211">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="7d8c6-212">Anropa-objekt</span><span class="sxs-lookup"><span data-stu-id="7d8c6-212">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="7d8c6-213">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="7d8c6-213">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="7d8c6-214">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="7d8c6-214">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="7d8c6-215">Byt namn – objekt</span><span class="sxs-lookup"><span data-stu-id="7d8c6-215">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="7d8c6-216">Ange objekt</span><span class="sxs-lookup"><span data-stu-id="7d8c6-216">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="7d8c6-217">about_Providers</span><span class="sxs-lookup"><span data-stu-id="7d8c6-217">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

