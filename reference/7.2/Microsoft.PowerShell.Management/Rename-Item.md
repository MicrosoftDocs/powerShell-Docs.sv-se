---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/03/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-item?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-Item
ms.openlocfilehash: dec5c2c905486110e4885f29d236ab41d945fb96
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709936"
---
# <span data-ttu-id="5258c-102">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="5258c-102">Rename-Item</span></span>

## <span data-ttu-id="5258c-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="5258c-103">SYNOPSIS</span></span>
<span data-ttu-id="5258c-104">Byter namn på ett objekt i ett namn område i PowerShell-providern.</span><span class="sxs-lookup"><span data-stu-id="5258c-104">Renames an item in a PowerShell provider namespace.</span></span>

## <span data-ttu-id="5258c-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5258c-105">SYNTAX</span></span>

### <span data-ttu-id="5258c-106">ByPath (standard)</span><span class="sxs-lookup"><span data-stu-id="5258c-106">ByPath (Default)</span></span>

```
Rename-Item [-Path] <String> [-NewName] <String> [-Force] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm]  [<CommonParameters>]
```

### <span data-ttu-id="5258c-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="5258c-107">ByLiteralPath</span></span>

```
Rename-Item -LiteralPath <String> [-NewName] <String> [-Force] [-PassThru]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

## <span data-ttu-id="5258c-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="5258c-108">DESCRIPTION</span></span>

<span data-ttu-id="5258c-109">`Rename-Item`Cmdleten byter namn på ett angivet objekt.</span><span class="sxs-lookup"><span data-stu-id="5258c-109">The `Rename-Item` cmdlet changes the name of a specified item.</span></span> <span data-ttu-id="5258c-110">Den här cmdleten påverkar inte innehållet i objektet som byter namn.</span><span class="sxs-lookup"><span data-stu-id="5258c-110">This cmdlet does not affect the content of the item being renamed.</span></span>

<span data-ttu-id="5258c-111">Du kan inte använda `Rename-Item` för att flytta ett objekt, t. ex. genom att ange en sökväg tillsammans med det nya namnet.</span><span class="sxs-lookup"><span data-stu-id="5258c-111">You can't use `Rename-Item` to move an item, such as by specifying a path together with the new name.</span></span> <span data-ttu-id="5258c-112">Använd cmdleten om du vill flytta och byta namn på ett objekt `Move-Item` .</span><span class="sxs-lookup"><span data-stu-id="5258c-112">To move and rename an item, use the `Move-Item` cmdlet.</span></span>

## <span data-ttu-id="5258c-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="5258c-113">EXAMPLES</span></span>

### <span data-ttu-id="5258c-114">Exempel 1: Byt namn på en fil</span><span class="sxs-lookup"><span data-stu-id="5258c-114">Example 1: Rename a file</span></span>

<span data-ttu-id="5258c-115">Det här kommandot byter namn på filen `daily_file.txt` till `monday_file.txt` .</span><span class="sxs-lookup"><span data-stu-id="5258c-115">This command renames the file `daily_file.txt` to `monday_file.txt`.</span></span>

```powershell
Rename-Item -Path "c:\logfiles\daily_file.txt" -NewName "monday_file.txt"
```

### <span data-ttu-id="5258c-116">Exempel 2: Byt namn på och flytta ett objekt</span><span class="sxs-lookup"><span data-stu-id="5258c-116">Example 2: Rename and move an item</span></span>

<span data-ttu-id="5258c-117">Du kan inte använda `Rename-Item` både för att byta namn på och flytta ett objekt.</span><span class="sxs-lookup"><span data-stu-id="5258c-117">You can't use `Rename-Item` to both rename and move an item.</span></span> <span data-ttu-id="5258c-118">Mer specifikt kan du inte ange en sökväg till värdet för parametern **Nyttnamn** , om inte sökvägen är identisk med sökvägen som anges i parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="5258c-118">Specifically, you can't supply a path for the value of the **NewName** parameter, unless the path is identical to the path specified in the **Path** parameter.</span></span> <span data-ttu-id="5258c-119">Annars tillåts endast ett nytt namn.</span><span class="sxs-lookup"><span data-stu-id="5258c-119">Otherwise, only a new name is permitted.</span></span>

<span data-ttu-id="5258c-120">I det här exemplet görs ett försök att byta namn på `project.txt` filen i den aktuella katalogen till `old-project.txt` i `D:\Archive` katalogen.</span><span class="sxs-lookup"><span data-stu-id="5258c-120">This example attempts to rename the `project.txt` file in the current directory to `old-project.txt` in the `D:\Archive` directory.</span></span> <span data-ttu-id="5258c-121">Resultatet är det fel som visas i utdata.</span><span class="sxs-lookup"><span data-stu-id="5258c-121">The result is the error shown in the output.</span></span>

```powershell
Rename-Item -Path "project.txt" -NewName "d:\archive\old-project.txt"
```

```Output
Rename-Item : can't rename because the target specified represents a path or device name.
At line:1 char:12
+ Rename-Item <<<<  -path project.txt -NewName d:\archive\old-project.txt
+ CategoryInfo          : InvalidArgument: (:) [Rename-Item], PS>  Move-Item -Path "project.txt" -De
stination "d:\archive\old-project.txt"
```

### <span data-ttu-id="5258c-122">Exempel 3: Byt namn på en register nyckel</span><span class="sxs-lookup"><span data-stu-id="5258c-122">Example 3: Rename a registry key</span></span>

<span data-ttu-id="5258c-123">I det här exemplet byter vi namn på en register nyckel från **annonsering** till **marknadsföring**.</span><span class="sxs-lookup"><span data-stu-id="5258c-123">This example renames a registry key from **Advertising** to **Marketing**.</span></span> <span data-ttu-id="5258c-124">När kommandot har slutförts får nyckeln ett nytt namn, men register posterna i nyckeln är oförändrade.</span><span class="sxs-lookup"><span data-stu-id="5258c-124">When the command is complete, the key is renamed, but the registry entries in the key are unchanged.</span></span>

```powershell
Rename-Item -Path "HKLM:\Software\MyCompany\Advertising" -NewName "Marketing"
```

### <span data-ttu-id="5258c-125">Exempel 4: Byt namn på flera filer</span><span class="sxs-lookup"><span data-stu-id="5258c-125">Example 4: Rename multiple files</span></span>

<span data-ttu-id="5258c-126">I det här exemplet byter namn på alla `*.txt` filer i den aktuella katalogen till `*.log` .</span><span class="sxs-lookup"><span data-stu-id="5258c-126">This example renames all the `*.txt` files in the current directory to `*.log`.</span></span>

```powershell
Get-ChildItem *.txt
```

```Output
    Directory: C:\temp\files

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        10/3/2019   7:47 AM           2918 Friday.TXT
-a----        10/3/2019   7:46 AM           2918 Monday.Txt
-a----        10/3/2019   7:47 AM           2918 Wednesday.txt
```

```powershell
Get-ChildItem *.txt | Rename-Item -NewName { $_.Name -replace '.txt','.log' }
Get-ChildItem *.log
```

```Output
    Directory: C:\temp\files

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        10/3/2019   7:47 AM           2918 Friday.log
-a----        10/3/2019   7:46 AM           2918 Monday.log
-a----        10/3/2019   7:47 AM           2918 Wednesday.log
```

<span data-ttu-id="5258c-127">`Get-ChildItem`Cmdlet: en hämtar alla filer i den aktuella mappen som har ett `.txt` fil namns tillägg och rör dem `Rename-Item` .</span><span class="sxs-lookup"><span data-stu-id="5258c-127">The `Get-ChildItem` cmdlet gets all the files in the current folder that have a `.txt` file extension then pipes them to `Rename-Item`.</span></span> <span data-ttu-id="5258c-128">Värdet för **Nyttnamn** är ett skript block som körs innan värdet skickas till parametern **Nyttnamn** .</span><span class="sxs-lookup"><span data-stu-id="5258c-128">The value of **NewName** is a script block that runs before the value is submitted to the **NewName** parameter.</span></span>

<span data-ttu-id="5258c-129">I-skript blocket `$_` representerar den automatiska variabeln varje fil objekt när det kommer till kommandot via pipelinen.</span><span class="sxs-lookup"><span data-stu-id="5258c-129">In the script block, the `$_` automatic variable represents each file object as it comes to the command through the pipeline.</span></span> <span data-ttu-id="5258c-130">-Skript blocket använder `-replace` operatorn för att ersätta fil namns tillägget för varje fil med `.log` .</span><span class="sxs-lookup"><span data-stu-id="5258c-130">The script block uses the `-replace` operator to replace the file extension of each file with `.log`.</span></span> <span data-ttu-id="5258c-131">Observera att matchning med `-replace` operatorn inte är Skift läges känsligt.</span><span class="sxs-lookup"><span data-stu-id="5258c-131">Notice that matching using the `-replace` operator is not case sensitive.</span></span>

## <span data-ttu-id="5258c-132">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="5258c-132">PARAMETERS</span></span>

### <span data-ttu-id="5258c-133">-Credential</span><span class="sxs-lookup"><span data-stu-id="5258c-133">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="5258c-134">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5258c-134">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="5258c-135">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="5258c-135">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="5258c-136">-Force</span><span class="sxs-lookup"><span data-stu-id="5258c-136">-Force</span></span>

<span data-ttu-id="5258c-137">Tvingar cmdleten att byta namn på objekt som annars inte kan ändras, t. ex. dolda eller skrivskyddade filer eller skrivskyddade alias eller variabler.</span><span class="sxs-lookup"><span data-stu-id="5258c-137">Forces the cmdlet to rename items that can't otherwise be changed, such as hidden or read-only files or read-only aliases or variables.</span></span> <span data-ttu-id="5258c-138">Cmdleten kan inte ändra konstanta alias eller variabler.</span><span class="sxs-lookup"><span data-stu-id="5258c-138">The cmdlet can't change constant aliases or variables.</span></span>
<span data-ttu-id="5258c-139">Implementeringen varierar från providern till providern.</span><span class="sxs-lookup"><span data-stu-id="5258c-139">Implementation varies from provider to provider.</span></span> <span data-ttu-id="5258c-140">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="5258c-140">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

<span data-ttu-id="5258c-141">Även om du använder **Force** -parametern kan inte cmdlet: en åsidosätta säkerhets begränsningar.</span><span class="sxs-lookup"><span data-stu-id="5258c-141">Even using the **Force** parameter, the cmdlet can't override security restrictions.</span></span>

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

### <span data-ttu-id="5258c-142">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="5258c-142">-LiteralPath</span></span>

<span data-ttu-id="5258c-143">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="5258c-143">Specifies a path to one or more locations.</span></span> <span data-ttu-id="5258c-144">Värdet för **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="5258c-144">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="5258c-145">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="5258c-145">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="5258c-146">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="5258c-146">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="5258c-147">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="5258c-147">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="5258c-148">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="5258c-148">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="5258c-149">-Nyttnamn</span><span class="sxs-lookup"><span data-stu-id="5258c-149">-NewName</span></span>

<span data-ttu-id="5258c-150">Anger det nya namnet på objektet.</span><span class="sxs-lookup"><span data-stu-id="5258c-150">Specifies the new name of the item.</span></span> <span data-ttu-id="5258c-151">Ange ett namn, inte en sökväg och ett namn.</span><span class="sxs-lookup"><span data-stu-id="5258c-151">Enter only a name, not a path and name.</span></span> <span data-ttu-id="5258c-152">Om du anger en sökväg som skiljer sig från den sökväg som anges i parametern **Path** `Rename-Item` genererar ett fel.</span><span class="sxs-lookup"><span data-stu-id="5258c-152">If you enter a path that differs from the path that is specified in the **Path** parameter, `Rename-Item` generates an error.</span></span>
<span data-ttu-id="5258c-153">Använd om du vill byta namn på och flytta ett objekt `Move-Item` .</span><span class="sxs-lookup"><span data-stu-id="5258c-153">To rename and move an item, use `Move-Item`.</span></span>

<span data-ttu-id="5258c-154">Du kan inte använda jokertecken i värdet för parametern **Nyttnamn** .</span><span class="sxs-lookup"><span data-stu-id="5258c-154">You can't use wildcard characters in the value of the **NewName** parameter.</span></span> <span data-ttu-id="5258c-155">Om du vill ange ett namn för flera filer använder du **ersättnings** operatorn i ett reguljärt uttryck.</span><span class="sxs-lookup"><span data-stu-id="5258c-155">To specify a name for multiple files, use the **Replace** operator in a regular expression.</span></span> <span data-ttu-id="5258c-156">Mer information om ersättnings operatorn finns [about_Comparison_Operators](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="5258c-156">For more information about the Replace operator, see [about_Comparison_Operators](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md).</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5258c-157">– PassThru</span><span class="sxs-lookup"><span data-stu-id="5258c-157">-PassThru</span></span>

<span data-ttu-id="5258c-158">Returnerar ett objekt som representerar objektet i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="5258c-158">Returns an object that represents the item to the pipeline.</span></span> <span data-ttu-id="5258c-159">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="5258c-159">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="5258c-160">-Path</span><span class="sxs-lookup"><span data-stu-id="5258c-160">-Path</span></span>

<span data-ttu-id="5258c-161">Anger sökvägen till det objekt som ska bytas namn på.</span><span class="sxs-lookup"><span data-stu-id="5258c-161">Specifies the path of the item to rename.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="5258c-162">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5258c-162">-Confirm</span></span>

<span data-ttu-id="5258c-163">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5258c-163">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5258c-164">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5258c-164">-WhatIf</span></span>

<span data-ttu-id="5258c-165">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="5258c-165">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="5258c-166">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="5258c-166">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5258c-167">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5258c-167">CommonParameters</span></span>

<span data-ttu-id="5258c-168">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5258c-168">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5258c-169">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="5258c-169">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="5258c-170">INDATA</span><span class="sxs-lookup"><span data-stu-id="5258c-170">INPUTS</span></span>

### <span data-ttu-id="5258c-171">System. String</span><span class="sxs-lookup"><span data-stu-id="5258c-171">System.String</span></span>

<span data-ttu-id="5258c-172">Du kan skicka vidare en sträng som innehåller en sökväg till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5258c-172">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="5258c-173">UTDATA</span><span class="sxs-lookup"><span data-stu-id="5258c-173">OUTPUTS</span></span>

### <span data-ttu-id="5258c-174">Ingen eller ett objekt som representerar det omdöpta objektet.</span><span class="sxs-lookup"><span data-stu-id="5258c-174">None or an object that represents the renamed item.</span></span>

<span data-ttu-id="5258c-175">Den här cmdleten genererar ett objekt som representerar det omdöpta objektet om du anger parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="5258c-175">This cmdlet generates an object that represents the renamed item, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="5258c-176">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="5258c-176">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="5258c-177">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="5258c-177">NOTES</span></span>

<span data-ttu-id="5258c-178">`Rename-Item` är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="5258c-178">`Rename-Item` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="5258c-179">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="5258c-179">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="5258c-180">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="5258c-180">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="5258c-181">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="5258c-181">RELATED LINKS</span></span>

[<span data-ttu-id="5258c-182">Rensa objekt</span><span class="sxs-lookup"><span data-stu-id="5258c-182">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="5258c-183">Kopiera objekt</span><span class="sxs-lookup"><span data-stu-id="5258c-183">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="5258c-184">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="5258c-184">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="5258c-185">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="5258c-185">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="5258c-186">Anropa-objekt</span><span class="sxs-lookup"><span data-stu-id="5258c-186">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="5258c-187">Flytta objekt</span><span class="sxs-lookup"><span data-stu-id="5258c-187">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="5258c-188">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="5258c-188">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="5258c-189">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="5258c-189">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="5258c-190">Byt namn – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="5258c-190">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="5258c-191">Ange objekt</span><span class="sxs-lookup"><span data-stu-id="5258c-191">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="5258c-192">about_Providers</span><span class="sxs-lookup"><span data-stu-id="5258c-192">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

