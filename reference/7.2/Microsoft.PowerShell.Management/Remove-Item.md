---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 04/07/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/remove-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Item
ms.openlocfilehash: 64bdbf9bbfe023c6cb909596e266201e2165e7a6
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710170"
---
# <span data-ttu-id="a573e-102">Remove-Item</span><span class="sxs-lookup"><span data-stu-id="a573e-102">Remove-Item</span></span>

## <span data-ttu-id="a573e-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="a573e-103">SYNOPSIS</span></span>
<span data-ttu-id="a573e-104">Tar bort de angivna objekten.</span><span class="sxs-lookup"><span data-stu-id="a573e-104">Deletes the specified items.</span></span>

## <span data-ttu-id="a573e-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a573e-105">SYNTAX</span></span>

### <span data-ttu-id="a573e-106">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="a573e-106">Path (Default)</span></span>

```
Remove-Item [-Path] <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Recurse] [-Force] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-Stream <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="a573e-107">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a573e-107">LiteralPath</span></span>

```
Remove-Item -LiteralPath <String[]> [-Filter <String>] [-Include <String[]>] [-Exclude <String[]>]
 [-Recurse] [-Force] [-Credential <PSCredential>] [-WhatIf] [-Confirm] [-Stream <String[]>]
 [<CommonParameters>]
```

## <span data-ttu-id="a573e-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a573e-108">DESCRIPTION</span></span>

<span data-ttu-id="a573e-109">`Remove-Item`Cmdleten tar bort ett eller flera objekt.</span><span class="sxs-lookup"><span data-stu-id="a573e-109">The `Remove-Item` cmdlet deletes one or more items.</span></span> <span data-ttu-id="a573e-110">Eftersom det stöds av många leverantörer kan den ta bort flera olika typer av objekt, inklusive filer, mappar, register nycklar, variabler, alias och funktioner.</span><span class="sxs-lookup"><span data-stu-id="a573e-110">Because it is supported by many providers, it can delete many different types of items, including files, folders, registry keys, variables, aliases, and functions.</span></span>

## <span data-ttu-id="a573e-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="a573e-111">EXAMPLES</span></span>

### <span data-ttu-id="a573e-112">Exempel 1: ta bort filer som har fil namns tillägget</span><span class="sxs-lookup"><span data-stu-id="a573e-112">Example 1: Delete files that have any file name extension</span></span>

<span data-ttu-id="a573e-113">Det här exemplet tar bort alla filer som har namn som innehåller en punkt ( `.` ) från `C:\Test` mappen.</span><span class="sxs-lookup"><span data-stu-id="a573e-113">This example deletes all of the files that have names that include a dot (`.`) from the `C:\Test` folder.</span></span> <span data-ttu-id="a573e-114">Eftersom kommandot anger en punkt tar kommandot inte bort mappar eller filer som inte har något fil namns tillägg.</span><span class="sxs-lookup"><span data-stu-id="a573e-114">Because the command specifies a dot, the command does not delete folders or files that have no file name extension.</span></span>

```powershell
Remove-Item C:\Test\*.*
```

### <span data-ttu-id="a573e-115">Exempel 2: ta bort några av dokumentets filer i en mapp</span><span class="sxs-lookup"><span data-stu-id="a573e-115">Example 2: Delete some of the document files in a folder</span></span>

<span data-ttu-id="a573e-116">Det här exemplet tar bort från den aktuella mappen alla filer som har ett `.doc` fil namns tillägg och ett namn som inte innehåller `*1*` .</span><span class="sxs-lookup"><span data-stu-id="a573e-116">This example deletes from the current folder all files that have a `.doc` file name extension and a name that does not include `*1*`.</span></span>

```powershell
Remove-Item * -Include *.doc -Exclude *1*
```

<span data-ttu-id="a573e-117">Jokertecken ( `*` ) används för att ange innehållet i den aktuella mappen.</span><span class="sxs-lookup"><span data-stu-id="a573e-117">It uses the wildcard character (`*`) to specify the contents of the current folder.</span></span> <span data-ttu-id="a573e-118">Den använder parametrarna **include** och **exclude** för att ange vilka filer som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="a573e-118">It uses the **Include** and **Exclude** parameters to specify the files to delete.</span></span>

### <span data-ttu-id="a573e-119">Exempel 3: ta bort dolda, skrivskyddade filer</span><span class="sxs-lookup"><span data-stu-id="a573e-119">Example 3: Delete hidden, read-only files</span></span>

<span data-ttu-id="a573e-120">Det här kommandot tar bort en fil som är både *dold* och *skrivskyddad*.</span><span class="sxs-lookup"><span data-stu-id="a573e-120">This command deletes a file that is both *hidden* and *read-only*.</span></span>

```powershell
Remove-Item -Path C:\Test\hidden-RO-file.txt -Force
```

<span data-ttu-id="a573e-121">Parametern **Path** används för att ange filen.</span><span class="sxs-lookup"><span data-stu-id="a573e-121">It uses the **Path** parameter to specify the file.</span></span> <span data-ttu-id="a573e-122">Den använder **Force** -parametern för att ta bort den.</span><span class="sxs-lookup"><span data-stu-id="a573e-122">It uses the **Force** parameter to delete it.</span></span> <span data-ttu-id="a573e-123">Utan **Force** kan du inte ta bort _skrivskyddade_ eller _dolda_ filer.</span><span class="sxs-lookup"><span data-stu-id="a573e-123">Without **Force**, you cannot delete _read-only_ or _hidden_ files.</span></span>

### <span data-ttu-id="a573e-124">Exempel 4: ta bort filer i undermappar rekursivt</span><span class="sxs-lookup"><span data-stu-id="a573e-124">Example 4: Delete files in subfolders recursively</span></span>

<span data-ttu-id="a573e-125">Det här kommandot tar bort alla CSV-filer i den aktuella mappen och alla undermappar rekursivt.</span><span class="sxs-lookup"><span data-stu-id="a573e-125">This command deletes all of the CSV files in the current folder and all subfolders recursively.</span></span>

<span data-ttu-id="a573e-126">Eftersom **rekursivt** -parametern i `Remove-Item` har ett känt problem använder kommandot i det här exemplet `Get-ChildItem` för att hämta de önskade filerna och använder sedan pipeline-operatorn för att skicka dem till `Remove-Item` .</span><span class="sxs-lookup"><span data-stu-id="a573e-126">Because the **Recurse** parameter in `Remove-Item` has a known issue, the command in this example uses `Get-ChildItem` to get the desired files, and then uses the pipeline operator to pass them to `Remove-Item`.</span></span>

```powershell
Get-ChildItem * -Include *.csv -Recurse | Remove-Item
```

<span data-ttu-id="a573e-127">I `Get-ChildItem` kommandot har **sökvägen** värdet ( `*` ) som representerar innehållet i den aktuella mappen.</span><span class="sxs-lookup"><span data-stu-id="a573e-127">In the `Get-ChildItem` command, **Path** has a value of (`*`), which represents the contents of the current folder.</span></span> <span data-ttu-id="a573e-128">Den använder **inkluderar** för att ange CSV-filtypen och använder **rekursivt** för att göra hämtningen rekursiv.</span><span class="sxs-lookup"><span data-stu-id="a573e-128">It uses **Include** to specify the CSV file type, and it uses **Recurse** to make the retrieval recursive.</span></span> <span data-ttu-id="a573e-129">Om du försöker ange en filtyp som sökväg, till exempel `-Path *.csv` , tolkar cmdleten ämnet för sökningen som en fil som inte har några underordnade objekt, och **rekursivt** Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="a573e-129">If you try to specify the file type the path, such as `-Path *.csv`, the cmdlet interprets the subject of the search to be a file that has no child items, and **Recurse** fails.</span></span>

### <span data-ttu-id="a573e-130">Exempel 5: ta bort under nycklar rekursivt</span><span class="sxs-lookup"><span data-stu-id="a573e-130">Example 5: Delete subkeys recursively</span></span>

<span data-ttu-id="a573e-131">Det här kommandot tar bort register nyckeln "OldApp" och alla dess under nycklar och värden.</span><span class="sxs-lookup"><span data-stu-id="a573e-131">This command deletes the "OldApp" registry key and all its subkeys and values.</span></span> <span data-ttu-id="a573e-132">Den används `Remove-Item` för att ta bort nyckeln.</span><span class="sxs-lookup"><span data-stu-id="a573e-132">It uses `Remove-Item` to remove the key.</span></span> <span data-ttu-id="a573e-133">Sökvägen anges, men det valfria parameter namnet (**sökväg**) utelämnas.</span><span class="sxs-lookup"><span data-stu-id="a573e-133">The path is specified, but the optional parameter name (**Path**) is omitted.</span></span>

<span data-ttu-id="a573e-134">Parametern **rekursivt** tar bort allt innehåll i nyckeln "OldApp" rekursivt.</span><span class="sxs-lookup"><span data-stu-id="a573e-134">The **Recurse** parameter deletes all of the contents of the "OldApp" key recursively.</span></span> <span data-ttu-id="a573e-135">Om nyckeln innehåller under nycklar och du utelämnar parametern **rekursivt** uppmanas du att bekräfta att du vill ta bort innehållet i nyckeln.</span><span class="sxs-lookup"><span data-stu-id="a573e-135">If the key contains subkeys and you omit the **Recurse** parameter, you are prompted to confirm that you want to delete the contents of the key.</span></span>

```powershell
Remove-Item HKLM:\Software\MyCompany\OldApp -Recurse
```

### <span data-ttu-id="a573e-136">Exempel 6: ta bort filer med specialtecken</span><span class="sxs-lookup"><span data-stu-id="a573e-136">Example 6: Deleting files with special characters</span></span>

<span data-ttu-id="a573e-137">I följande exempel visas hur du tar bort filer som innehåller specialtecken som hakparenteser eller parenteser.</span><span class="sxs-lookup"><span data-stu-id="a573e-137">The following example shows how to delete files that contain special characters like brackets or parentheses.</span></span>

```powershell
Get-ChildItem
```

```Output
    Directory: C:\temp\Downloads

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a---          6/1/2018  12:19 PM           1362 myFile.txt
-a---          6/1/2018  12:30 PM           1132 myFile[1].txt
-a---          6/1/2018  12:19 PM           1283 myFile[2].txt
-a---          6/1/2018  12:19 PM           1432 myFile[3].txt

```

```powershell
Get-ChildItem | Where-Object Name -Like '*`[*'
```

```Output
    Directory: C:\temp\Downloads

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a---          6/1/2018  12:30 PM           1132 myFile[1].txt
-a---          6/1/2018  12:19 PM           1283 myFile[2].txt
-a---          6/1/2018  12:19 PM           1432 myFile[3].txt

```

```powershell
Get-ChildItem | Where-Object Name -Like '*`[*' | ForEach-Object { Remove-Item -LiteralPath $_.Name }
Get-ChildItem
```

```Output
    Directory: C:\temp\Downloads

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a---          6/1/2018  12:19 PM           1362 myFile.txt
```

### <span data-ttu-id="a573e-138">Exempel 7: ta bort en alternativ data ström</span><span class="sxs-lookup"><span data-stu-id="a573e-138">Example 7: Remove an alternate data stream</span></span>

<span data-ttu-id="a573e-139">Det här exemplet visar hur du använder den dynamiska **Stream** -parametern för `Remove-Item` cmdleten för att ta bort en alternativ data ström.</span><span class="sxs-lookup"><span data-stu-id="a573e-139">This example shows how to use the **Stream** dynamic parameter of the `Remove-Item` cmdlet to delete an alternate data stream.</span></span> <span data-ttu-id="a573e-140">Data Ströms parametern introduceras i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a573e-140">The stream parameter is introduced in Windows PowerShell 3.0.</span></span>

```powershell
Get-Item C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
```

```Output
   FileName: \\C:\Test\Copy-Script.ps1

Stream                   Length
------                   ------
Zone.Identifier              26

```

```powershell
Remove-Item C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
Get-Item C:\Test\Copy-Script.ps1 -Stream Zone.Identifier
```

```Output
Get-Item : Could not open alternate data stream 'Zone.Identifier' of file 'C:\Test\Copy-Script.ps1'.
At line:1 char:1
+ Get-Item 'C:\Test\Copy-Script.ps1' -Stream Zone.Identifier
+ [!INCLUDE[]()][!INCLUDE[]()][!INCLUDE[]()][!INCLUDE[]()][!INCLUDE[]()]~~
    + CategoryInfo          : ObjectNotFound: (C:\Test\Copy-Script.ps1:String) [Get-Item], FileNotFoundE
   xception
    + FullyQualifiedErrorId : AlternateDataStreamNotFound,Microsoft.PowerShell.Commands.GetItemCommand

```

<span data-ttu-id="a573e-141">**Stream** -parametern `Get-Item` hämtar filens **zon. Identifier** -dataström. `Copy-Script.ps1`</span><span class="sxs-lookup"><span data-stu-id="a573e-141">The **Stream** parameter `Get-Item` gets the **Zone.Identifier** stream of the `Copy-Script.ps1` file.</span></span> <span data-ttu-id="a573e-142">`Remove-Item` använder **Stream** -parametern för att ta bort filens överordnade- **ID** .</span><span class="sxs-lookup"><span data-stu-id="a573e-142">`Remove-Item` uses the **Stream** parameter to remove the **Zone.Identifier** stream of the file.</span></span> <span data-ttu-id="a573e-143">Slutligen `Get-Item` visar cmdleten att **zonen. identifierarens** data ström har tagits bort.</span><span class="sxs-lookup"><span data-stu-id="a573e-143">Finally, the `Get-Item` cmdlet shows that the **Zone.Identifier** stream was deleted.</span></span>

## <span data-ttu-id="a573e-144">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="a573e-144">PARAMETERS</span></span>

### <span data-ttu-id="a573e-145">-Credential</span><span class="sxs-lookup"><span data-stu-id="a573e-145">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="a573e-146">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a573e-146">This parameter is not supported by any providers installed with PowerShell.</span></span>
> <span data-ttu-id="a573e-147">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="a573e-147">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="a573e-148">-Undanta</span><span class="sxs-lookup"><span data-stu-id="a573e-148">-Exclude</span></span>

<span data-ttu-id="a573e-149">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet exkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="a573e-149">Specifies, as a string array, an item or items that this cmdlet excludes in the operation.</span></span> <span data-ttu-id="a573e-150">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="a573e-150">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="a573e-151">Ange ett Sök vägs element eller ett mönster, till exempel `*.txt` .</span><span class="sxs-lookup"><span data-stu-id="a573e-151">Enter a path element or pattern, such as `*.txt`.</span></span> <span data-ttu-id="a573e-152">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="a573e-152">Wildcard characters are permitted.</span></span> <span data-ttu-id="a573e-153">Parametern **exclude** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="a573e-153">The **Exclude** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="a573e-154">-Filter</span><span class="sxs-lookup"><span data-stu-id="a573e-154">-Filter</span></span>

<span data-ttu-id="a573e-155">Anger ett filter för att kvalificera **Sök vägs** parametern.</span><span class="sxs-lookup"><span data-stu-id="a573e-155">Specifies a filter to qualify the **Path** parameter.</span></span> <span data-ttu-id="a573e-156">[Fil Systems](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) leverantören är den enda installerade PowerShell-providern som stöder användningen av filter.</span><span class="sxs-lookup"><span data-stu-id="a573e-156">The [FileSystem](../Microsoft.PowerShell.Core/About/about_FileSystem_Provider.md) provider is the only installed PowerShell provider that supports the use of filters.</span></span> <span data-ttu-id="a573e-157">Du kan hitta syntaxen för filter språket för **fil systemet** i [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span><span class="sxs-lookup"><span data-stu-id="a573e-157">You can find the syntax for the **FileSystem** filter language in [about_Wildcards](../Microsoft.PowerShell.Core/About/about_Wildcards.md).</span></span>
<span data-ttu-id="a573e-158">Filter är mer effektiva än andra parametrar, eftersom providern tillämpar dem när cmdleten hämtar objekten i stället för att ha PowerShell filtrera objekten när de har hämtats.</span><span class="sxs-lookup"><span data-stu-id="a573e-158">Filters are more efficient than other parameters, because the provider applies them when the cmdlet gets the objects rather than having PowerShell filter the objects after they are retrieved.</span></span>

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

### <span data-ttu-id="a573e-159">-Force</span><span class="sxs-lookup"><span data-stu-id="a573e-159">-Force</span></span>

<span data-ttu-id="a573e-160">Tvingar cmdleten att ta bort objekt som inte kan ändras på annat sätt, t. ex. dolda eller skrivskyddade filer eller skrivskyddade alias eller variabler.</span><span class="sxs-lookup"><span data-stu-id="a573e-160">Forces the cmdlet to remove items that cannot otherwise be changed, such as hidden or read-only files or read-only aliases or variables.</span></span> <span data-ttu-id="a573e-161">Cmdleten kan inte ta bort konstanta alias eller variabler.</span><span class="sxs-lookup"><span data-stu-id="a573e-161">The cmdlet cannot remove constant aliases or variables.</span></span>
<span data-ttu-id="a573e-162">Implementeringen varierar från providern till providern.</span><span class="sxs-lookup"><span data-stu-id="a573e-162">Implementation varies from provider to provider.</span></span> <span data-ttu-id="a573e-163">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="a573e-163">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span> <span data-ttu-id="a573e-164">Även om du använder **Force** -parametern kan inte cmdlet: en åsidosätta säkerhets begränsningar.</span><span class="sxs-lookup"><span data-stu-id="a573e-164">Even using the **Force** parameter, the cmdlet cannot override security restrictions.</span></span>

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

### <span data-ttu-id="a573e-165">-Inkludera</span><span class="sxs-lookup"><span data-stu-id="a573e-165">-Include</span></span>

<span data-ttu-id="a573e-166">Anger, som en sträng mat ris, ett objekt eller objekt som denna cmdlet inkluderar i åtgärden.</span><span class="sxs-lookup"><span data-stu-id="a573e-166">Specifies, as a string array, an item or items that this cmdlet includes in the operation.</span></span> <span data-ttu-id="a573e-167">Värdet för den här parametern kvalificerar parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="a573e-167">The value of this parameter qualifies the **Path** parameter.</span></span> <span data-ttu-id="a573e-168">Ange ett Sök vägs element eller ett mönster, till exempel `"*.txt"` .</span><span class="sxs-lookup"><span data-stu-id="a573e-168">Enter a path element or pattern, such as `"*.txt"`.</span></span> <span data-ttu-id="a573e-169">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="a573e-169">Wildcard characters are permitted.</span></span> <span data-ttu-id="a573e-170">Parametern **include** är endast effektiv när kommandot innehåller innehållet i ett objekt, t. ex `C:\Windows\*` ., där jokertecknet anger innehållet i `C:\Windows` katalogen.</span><span class="sxs-lookup"><span data-stu-id="a573e-170">The **Include** parameter is effective only when the command includes the contents of an item, such as `C:\Windows\*`, where the wildcard character specifies the contents of the `C:\Windows` directory.</span></span>

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

### <span data-ttu-id="a573e-171">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="a573e-171">-LiteralPath</span></span>

<span data-ttu-id="a573e-172">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="a573e-172">Specifies a path to one or more locations.</span></span> <span data-ttu-id="a573e-173">Värdet för **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="a573e-173">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="a573e-174">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="a573e-174">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="a573e-175">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="a573e-175">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="a573e-176">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="a573e-176">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="a573e-177">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="a573e-177">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="a573e-178">-Path</span><span class="sxs-lookup"><span data-stu-id="a573e-178">-Path</span></span>

<span data-ttu-id="a573e-179">Anger en sökväg till de objekt som tas bort.</span><span class="sxs-lookup"><span data-stu-id="a573e-179">Specifies a path of the items being removed.</span></span>
<span data-ttu-id="a573e-180">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="a573e-180">Wildcard characters are permitted.</span></span>

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

### <span data-ttu-id="a573e-181">– Rekursivt</span><span class="sxs-lookup"><span data-stu-id="a573e-181">-Recurse</span></span>

<span data-ttu-id="a573e-182">Anger att denna cmdlet tar bort objekten på de angivna platserna och i alla underordnade objekt på platserna.</span><span class="sxs-lookup"><span data-stu-id="a573e-182">Indicates that this cmdlet deletes the items in the specified locations and in all child items of the locations.</span></span>

<span data-ttu-id="a573e-183">När den används med parametern **include** kanske **rekursivt** -parametern inte tar bort alla undermappar eller alla underordnade objekt.</span><span class="sxs-lookup"><span data-stu-id="a573e-183">When it is used with the **Include** parameter, the **Recurse** parameter might not delete all subfolders or all child items.</span></span> <span data-ttu-id="a573e-184">Detta är ett känt problem.</span><span class="sxs-lookup"><span data-stu-id="a573e-184">This is a known issue.</span></span> <span data-ttu-id="a573e-185">Som en lösning kan `Get-ChildItem -Recurse` du prova att skicka kommandots resultat till `Remove-Item` , enligt beskrivningen i "exempel 4" i det här avsnittet.</span><span class="sxs-lookup"><span data-stu-id="a573e-185">As a workaround, try piping results of the `Get-ChildItem -Recurse` command to `Remove-Item`, as described in "Example 4" in this topic.</span></span>

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

### <span data-ttu-id="a573e-186">-Stream</span><span class="sxs-lookup"><span data-stu-id="a573e-186">-Stream</span></span>

<span data-ttu-id="a573e-187">**Stream** -parametern är en dynamisk parameter som fil Systems leverantören lägger till i `Remove-Item` .</span><span class="sxs-lookup"><span data-stu-id="a573e-187">The **Stream** parameter is a dynamic parameter that the FileSystem provider adds to `Remove-Item`.</span></span>
<span data-ttu-id="a573e-188">Den här parametern fungerar bara i fil system enheter.</span><span class="sxs-lookup"><span data-stu-id="a573e-188">This parameter works only in file system drives.</span></span>

<span data-ttu-id="a573e-189">Du kan använda `Remove-Item` för att ta bort en alternativ data ström.</span><span class="sxs-lookup"><span data-stu-id="a573e-189">You can use `Remove-Item` to delete an alternative data stream.</span></span> <span data-ttu-id="a573e-190">Det är dock inte det rekommenderade sättet att eliminera säkerhets kontroller som blockerar filer som hämtas från Internet.</span><span class="sxs-lookup"><span data-stu-id="a573e-190">However, it is not the recommended way to eliminate security checks that block files that are downloaded from the Internet.</span></span> <span data-ttu-id="a573e-191">Om du verifierar att en Hämtad fil är säker använder du `Unblock-File` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a573e-191">If you verify that a downloaded file is safe, use the `Unblock-File` cmdlet.</span></span>

<span data-ttu-id="a573e-192">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a573e-192">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="a573e-193">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a573e-193">-Confirm</span></span>

<span data-ttu-id="a573e-194">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a573e-194">Prompts you for confirmation before running the cmdlet.</span></span> <span data-ttu-id="a573e-195">Mer information finns i följande artiklar:</span><span class="sxs-lookup"><span data-stu-id="a573e-195">For more information, see the following articles:</span></span>

- [<span data-ttu-id="a573e-196">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="a573e-196">about_Preference_Variables</span></span>](../microsoft.powershell.core/about/about_preference_variables.md#confirmpreference)
- [<span data-ttu-id="a573e-197">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="a573e-197">about_Functions_CmdletBindingAttribute</span></span>](../microsoft.powershell.core/about/about_functions_cmdletbindingattribute.md?#confirmimpact)

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

### <span data-ttu-id="a573e-198">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a573e-198">-WhatIf</span></span>

<span data-ttu-id="a573e-199">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="a573e-199">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="a573e-200">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="a573e-200">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a573e-201">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a573e-201">CommonParameters</span></span>

<span data-ttu-id="a573e-202">Denna cmdlet stöder de gemensamma parametrarna:,,,,,,,, `-Debug` `-ErrorAction` `-ErrorVariable` `-InformationAction` `-InformationVariable` `-OutVariable` `-OutBuffer` `-PipelineVariable` `-Verbose` `-WarningAction` , och `-WarningVariable` .</span><span class="sxs-lookup"><span data-stu-id="a573e-202">This cmdlet supports the common parameters: `-Debug`, `-ErrorAction`, `-ErrorVariable`, `-InformationAction`, `-InformationVariable`, `-OutVariable`, `-OutBuffer`, `-PipelineVariable`, `-Verbose`, `-WarningAction`, and `-WarningVariable`.</span></span> <span data-ttu-id="a573e-203">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="a573e-203">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="a573e-204">INDATA</span><span class="sxs-lookup"><span data-stu-id="a573e-204">INPUTS</span></span>

### <span data-ttu-id="a573e-205">System. String</span><span class="sxs-lookup"><span data-stu-id="a573e-205">System.String</span></span>

<span data-ttu-id="a573e-206">Du kan skicka vidare en sträng som innehåller en sökväg, men inte en literal sökväg, till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a573e-206">You can pipe a string that contains a path, but not a literal path, to this cmdlet.</span></span>

## <span data-ttu-id="a573e-207">UTDATA</span><span class="sxs-lookup"><span data-stu-id="a573e-207">OUTPUTS</span></span>

### <span data-ttu-id="a573e-208">Inga</span><span class="sxs-lookup"><span data-stu-id="a573e-208">None</span></span>

<span data-ttu-id="a573e-209">Denna cmdlet returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="a573e-209">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="a573e-210">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="a573e-210">NOTES</span></span>

<span data-ttu-id="a573e-211">`Remove-Item`Cmdleten är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="a573e-211">The `Remove-Item` cmdlet is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="a573e-212">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="a573e-212">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="a573e-213">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="a573e-213">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

<span data-ttu-id="a573e-214">När du försöker ta bort en mapp som innehåller objekt utan att använda parametern **rekursivt** , uppmanas cmdleten att bekräfta.</span><span class="sxs-lookup"><span data-stu-id="a573e-214">When you try to delete a folder that contains items without using the **Recurse** parameter, the cmdlet prompts for confirmation.</span></span> <span data-ttu-id="a573e-215">`-Confirm:$false`Om du använder ignoreras inte prompten.</span><span class="sxs-lookup"><span data-stu-id="a573e-215">Using `-Confirm:$false` does not suppress the prompt.</span></span> <span data-ttu-id="a573e-216">Det här är avsiktligt.</span><span class="sxs-lookup"><span data-stu-id="a573e-216">This is by design.</span></span>

## <span data-ttu-id="a573e-217">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="a573e-217">RELATED LINKS</span></span>

[<span data-ttu-id="a573e-218">Rensa objekt</span><span class="sxs-lookup"><span data-stu-id="a573e-218">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="a573e-219">Kopiera objekt</span><span class="sxs-lookup"><span data-stu-id="a573e-219">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="a573e-220">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="a573e-220">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="a573e-221">Anropa-objekt</span><span class="sxs-lookup"><span data-stu-id="a573e-221">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="a573e-222">Flytta objekt</span><span class="sxs-lookup"><span data-stu-id="a573e-222">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="a573e-223">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="a573e-223">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="a573e-224">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="a573e-224">Remove-ItemProperty</span></span>](Remove-ItemProperty.md)

[<span data-ttu-id="a573e-225">Byt namn – objekt</span><span class="sxs-lookup"><span data-stu-id="a573e-225">Rename-Item</span></span>](Rename-Item.md)

[<span data-ttu-id="a573e-226">Ange objekt</span><span class="sxs-lookup"><span data-stu-id="a573e-226">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="a573e-227">about_Providers</span><span class="sxs-lookup"><span data-stu-id="a573e-227">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

[<span data-ttu-id="a573e-228">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="a573e-228">about_Preference_Variables</span></span>](../microsoft.powershell.core/about/about_preference_variables.md#confirmpreference)

[<span data-ttu-id="a573e-229">about_Functions_CmdletBindingAttribute</span><span class="sxs-lookup"><span data-stu-id="a573e-229">about_Functions_CmdletBindingAttribute</span></span>](../microsoft.powershell.core/about/about_functions_cmdletbindingattribute.md?#confirmimpact)
