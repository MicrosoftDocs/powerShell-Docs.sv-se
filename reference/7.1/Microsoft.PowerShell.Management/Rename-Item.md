---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 10/03/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/rename-item?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Rename-Item
ms.openlocfilehash: b5dfd3e55ceadf4141e977f0fb879ba5d05538f7
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263241"
---
# <span data-ttu-id="252e0-103">Rename-Item</span><span class="sxs-lookup"><span data-stu-id="252e0-103">Rename-Item</span></span>

## <span data-ttu-id="252e0-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="252e0-104">SYNOPSIS</span></span>
<span data-ttu-id="252e0-105">Byter namn på ett objekt i ett namn område i PowerShell-providern.</span><span class="sxs-lookup"><span data-stu-id="252e0-105">Renames an item in a PowerShell provider namespace.</span></span>

## <span data-ttu-id="252e0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="252e0-106">SYNTAX</span></span>

### <span data-ttu-id="252e0-107">ByPath (standard)</span><span class="sxs-lookup"><span data-stu-id="252e0-107">ByPath (Default)</span></span>

```
Rename-Item [-Path] <String> [-NewName] <String> [-Force] [-PassThru] [-Credential <PSCredential>]
 [-WhatIf] [-Confirm]  [<CommonParameters>]
```

### <span data-ttu-id="252e0-108">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="252e0-108">ByLiteralPath</span></span>

```
Rename-Item -LiteralPath <String> [-NewName] <String> [-Force] [-PassThru]
 [-Credential <PSCredential>] [-WhatIf] [-Confirm]  [<CommonParameters>]
```

## <span data-ttu-id="252e0-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="252e0-109">DESCRIPTION</span></span>

<span data-ttu-id="252e0-110">`Rename-Item`Cmdleten byter namn på ett angivet objekt.</span><span class="sxs-lookup"><span data-stu-id="252e0-110">The `Rename-Item` cmdlet changes the name of a specified item.</span></span> <span data-ttu-id="252e0-111">Den här cmdleten påverkar inte innehållet i objektet som byter namn.</span><span class="sxs-lookup"><span data-stu-id="252e0-111">This cmdlet does not affect the content of the item being renamed.</span></span>

<span data-ttu-id="252e0-112">Du kan inte använda `Rename-Item` för att flytta ett objekt, t. ex. genom att ange en sökväg tillsammans med det nya namnet.</span><span class="sxs-lookup"><span data-stu-id="252e0-112">You can't use `Rename-Item` to move an item, such as by specifying a path together with the new name.</span></span> <span data-ttu-id="252e0-113">Använd cmdleten om du vill flytta och byta namn på ett objekt `Move-Item` .</span><span class="sxs-lookup"><span data-stu-id="252e0-113">To move and rename an item, use the `Move-Item` cmdlet.</span></span>

## <span data-ttu-id="252e0-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="252e0-114">EXAMPLES</span></span>

### <span data-ttu-id="252e0-115">Exempel 1: Byt namn på en fil</span><span class="sxs-lookup"><span data-stu-id="252e0-115">Example 1: Rename a file</span></span>

<span data-ttu-id="252e0-116">Det här kommandot byter namn på filen `daily_file.txt` till `monday_file.txt` .</span><span class="sxs-lookup"><span data-stu-id="252e0-116">This command renames the file `daily_file.txt` to `monday_file.txt`.</span></span>

```powershell
Rename-Item -Path "c:\logfiles\daily_file.txt" -NewName "monday_file.txt"
```

### <span data-ttu-id="252e0-117">Exempel 2: Byt namn på och flytta ett objekt</span><span class="sxs-lookup"><span data-stu-id="252e0-117">Example 2: Rename and move an item</span></span>

<span data-ttu-id="252e0-118">Du kan inte använda `Rename-Item` både för att byta namn på och flytta ett objekt.</span><span class="sxs-lookup"><span data-stu-id="252e0-118">You can't use `Rename-Item` to both rename and move an item.</span></span> <span data-ttu-id="252e0-119">Mer specifikt kan du inte ange en sökväg till värdet för parametern **Nyttnamn** , om inte sökvägen är identisk med sökvägen som anges i parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="252e0-119">Specifically, you can't supply a path for the value of the **NewName** parameter, unless the path is identical to the path specified in the **Path** parameter.</span></span> <span data-ttu-id="252e0-120">Annars tillåts endast ett nytt namn.</span><span class="sxs-lookup"><span data-stu-id="252e0-120">Otherwise, only a new name is permitted.</span></span>

<span data-ttu-id="252e0-121">I det här exemplet görs ett försök att byta namn på `project.txt` filen i den aktuella katalogen till `old-project.txt` i `D:\Archive` katalogen.</span><span class="sxs-lookup"><span data-stu-id="252e0-121">This example attempts to rename the `project.txt` file in the current directory to `old-project.txt` in the `D:\Archive` directory.</span></span> <span data-ttu-id="252e0-122">Resultatet är det fel som visas i utdata.</span><span class="sxs-lookup"><span data-stu-id="252e0-122">The result is the error shown in the output.</span></span>

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

### <span data-ttu-id="252e0-123">Exempel 3: Byt namn på en register nyckel</span><span class="sxs-lookup"><span data-stu-id="252e0-123">Example 3: Rename a registry key</span></span>

<span data-ttu-id="252e0-124">I det här exemplet byter vi namn på en register nyckel från **annonsering** till **marknadsföring**.</span><span class="sxs-lookup"><span data-stu-id="252e0-124">This example renames a registry key from **Advertising** to **Marketing**.</span></span> <span data-ttu-id="252e0-125">När kommandot har slutförts får nyckeln ett nytt namn, men register posterna i nyckeln är oförändrade.</span><span class="sxs-lookup"><span data-stu-id="252e0-125">When the command is complete, the key is renamed, but the registry entries in the key are unchanged.</span></span>

```powershell
Rename-Item -Path "HKLM:\Software\MyCompany\Advertising" -NewName "Marketing"
```

### <span data-ttu-id="252e0-126">Exempel 4: Byt namn på flera filer</span><span class="sxs-lookup"><span data-stu-id="252e0-126">Example 4: Rename multiple files</span></span>

<span data-ttu-id="252e0-127">I det här exemplet byter namn på alla `*.txt` filer i den aktuella katalogen till `*.log` .</span><span class="sxs-lookup"><span data-stu-id="252e0-127">This example renames all the `*.txt` files in the current directory to `*.log`.</span></span>

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

<span data-ttu-id="252e0-128">`Get-ChildItem`Cmdlet: en hämtar alla filer i den aktuella mappen som har ett `.txt` fil namns tillägg och rör dem `Rename-Item` .</span><span class="sxs-lookup"><span data-stu-id="252e0-128">The `Get-ChildItem` cmdlet gets all the files in the current folder that have a `.txt` file extension then pipes them to `Rename-Item`.</span></span> <span data-ttu-id="252e0-129">Värdet för **Nyttnamn** är ett skript block som körs innan värdet skickas till parametern **Nyttnamn** .</span><span class="sxs-lookup"><span data-stu-id="252e0-129">The value of **NewName** is a script block that runs before the value is submitted to the **NewName** parameter.</span></span>

<span data-ttu-id="252e0-130">I-skript blocket `$_` representerar den automatiska variabeln varje fil objekt när det kommer till kommandot via pipelinen.</span><span class="sxs-lookup"><span data-stu-id="252e0-130">In the script block, the `$_` automatic variable represents each file object as it comes to the command through the pipeline.</span></span> <span data-ttu-id="252e0-131">-Skript blocket använder `-replace` operatorn för att ersätta fil namns tillägget för varje fil med `.log` .</span><span class="sxs-lookup"><span data-stu-id="252e0-131">The script block uses the `-replace` operator to replace the file extension of each file with `.log`.</span></span> <span data-ttu-id="252e0-132">Observera att matchning med `-replace` operatorn inte är Skift läges känsligt.</span><span class="sxs-lookup"><span data-stu-id="252e0-132">Notice that matching using the `-replace` operator is not case sensitive.</span></span>

## <span data-ttu-id="252e0-133">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="252e0-133">PARAMETERS</span></span>

### <span data-ttu-id="252e0-134">-Credential</span><span class="sxs-lookup"><span data-stu-id="252e0-134">-Credential</span></span>

> [!NOTE]
> <span data-ttu-id="252e0-135">Den här parametern stöds inte av några providrar som installeras med PowerShell.</span><span class="sxs-lookup"><span data-stu-id="252e0-135">This parameter is not supported by any providers installed with PowerShell.</span></span> <span data-ttu-id="252e0-136">Om du vill personifiera en annan användare eller öka dina autentiseringsuppgifter när du kör denna cmdlet, använder du [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span><span class="sxs-lookup"><span data-stu-id="252e0-136">To impersonate another user, or elevate your credentials when running this cmdlet, use [Invoke-Command](../Microsoft.PowerShell.Core/Invoke-Command.md).</span></span>

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

### <span data-ttu-id="252e0-137">-Force</span><span class="sxs-lookup"><span data-stu-id="252e0-137">-Force</span></span>

<span data-ttu-id="252e0-138">Tvingar cmdleten att byta namn på objekt som annars inte kan ändras, t. ex. dolda eller skrivskyddade filer eller skrivskyddade alias eller variabler.</span><span class="sxs-lookup"><span data-stu-id="252e0-138">Forces the cmdlet to rename items that can't otherwise be changed, such as hidden or read-only files or read-only aliases or variables.</span></span> <span data-ttu-id="252e0-139">Cmdleten kan inte ändra konstanta alias eller variabler.</span><span class="sxs-lookup"><span data-stu-id="252e0-139">The cmdlet can't change constant aliases or variables.</span></span>
<span data-ttu-id="252e0-140">Implementeringen varierar från providern till providern.</span><span class="sxs-lookup"><span data-stu-id="252e0-140">Implementation varies from provider to provider.</span></span> <span data-ttu-id="252e0-141">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="252e0-141">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

<span data-ttu-id="252e0-142">Även om du använder **Force** -parametern kan inte cmdlet: en åsidosätta säkerhets begränsningar.</span><span class="sxs-lookup"><span data-stu-id="252e0-142">Even using the **Force** parameter, the cmdlet can't override security restrictions.</span></span>

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

### <span data-ttu-id="252e0-143">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="252e0-143">-LiteralPath</span></span>

<span data-ttu-id="252e0-144">Anger en sökväg till en eller flera platser.</span><span class="sxs-lookup"><span data-stu-id="252e0-144">Specifies a path to one or more locations.</span></span> <span data-ttu-id="252e0-145">Värdet för **LiteralPath** används exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="252e0-145">The value of **LiteralPath** is used exactly as it is typed.</span></span> <span data-ttu-id="252e0-146">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="252e0-146">No characters are interpreted as wildcards.</span></span> <span data-ttu-id="252e0-147">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="252e0-147">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="252e0-148">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="252e0-148">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

<span data-ttu-id="252e0-149">Mer information finns i [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span><span class="sxs-lookup"><span data-stu-id="252e0-149">For more information, see [about_Quoting_Rules](../Microsoft.Powershell.Core/About/about_Quoting_Rules.md).</span></span>

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

### <span data-ttu-id="252e0-150">-Nyttnamn</span><span class="sxs-lookup"><span data-stu-id="252e0-150">-NewName</span></span>

<span data-ttu-id="252e0-151">Anger det nya namnet på objektet.</span><span class="sxs-lookup"><span data-stu-id="252e0-151">Specifies the new name of the item.</span></span> <span data-ttu-id="252e0-152">Ange ett namn, inte en sökväg och ett namn.</span><span class="sxs-lookup"><span data-stu-id="252e0-152">Enter only a name, not a path and name.</span></span> <span data-ttu-id="252e0-153">Om du anger en sökväg som skiljer sig från den sökväg som anges i parametern **Path** `Rename-Item` genererar ett fel.</span><span class="sxs-lookup"><span data-stu-id="252e0-153">If you enter a path that differs from the path that is specified in the **Path** parameter, `Rename-Item` generates an error.</span></span>
<span data-ttu-id="252e0-154">Använd om du vill byta namn på och flytta ett objekt `Move-Item` .</span><span class="sxs-lookup"><span data-stu-id="252e0-154">To rename and move an item, use `Move-Item`.</span></span>

<span data-ttu-id="252e0-155">Du kan inte använda jokertecken i värdet för parametern **Nyttnamn** .</span><span class="sxs-lookup"><span data-stu-id="252e0-155">You can't use wildcard characters in the value of the **NewName** parameter.</span></span> <span data-ttu-id="252e0-156">Om du vill ange ett namn för flera filer använder du **ersättnings** operatorn i ett reguljärt uttryck.</span><span class="sxs-lookup"><span data-stu-id="252e0-156">To specify a name for multiple files, use the **Replace** operator in a regular expression.</span></span> <span data-ttu-id="252e0-157">Mer information om ersättnings operatorn finns [about_Comparison_Operators](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md).</span><span class="sxs-lookup"><span data-stu-id="252e0-157">For more information about the Replace operator, see [about_Comparison_Operators](../Microsoft.PowerShell.Core/About/about_Comparison_Operators.md).</span></span>

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

### <span data-ttu-id="252e0-158">– PassThru</span><span class="sxs-lookup"><span data-stu-id="252e0-158">-PassThru</span></span>

<span data-ttu-id="252e0-159">Returnerar ett objekt som representerar objektet i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="252e0-159">Returns an object that represents the item to the pipeline.</span></span> <span data-ttu-id="252e0-160">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="252e0-160">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="252e0-161">-Path</span><span class="sxs-lookup"><span data-stu-id="252e0-161">-Path</span></span>

<span data-ttu-id="252e0-162">Anger sökvägen till det objekt som ska bytas namn på.</span><span class="sxs-lookup"><span data-stu-id="252e0-162">Specifies the path of the item to rename.</span></span>

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

### <span data-ttu-id="252e0-163">-Confirm</span><span class="sxs-lookup"><span data-stu-id="252e0-163">-Confirm</span></span>

<span data-ttu-id="252e0-164">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="252e0-164">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="252e0-165">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="252e0-165">-WhatIf</span></span>

<span data-ttu-id="252e0-166">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="252e0-166">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="252e0-167">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="252e0-167">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="252e0-168">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="252e0-168">CommonParameters</span></span>

<span data-ttu-id="252e0-169">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="252e0-169">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="252e0-170">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="252e0-170">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="252e0-171">INDATA</span><span class="sxs-lookup"><span data-stu-id="252e0-171">INPUTS</span></span>

### <span data-ttu-id="252e0-172">System. String</span><span class="sxs-lookup"><span data-stu-id="252e0-172">System.String</span></span>

<span data-ttu-id="252e0-173">Du kan skicka vidare en sträng som innehåller en sökväg till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="252e0-173">You can pipe a string that contains a path to this cmdlet.</span></span>

## <span data-ttu-id="252e0-174">UTDATA</span><span class="sxs-lookup"><span data-stu-id="252e0-174">OUTPUTS</span></span>

### <span data-ttu-id="252e0-175">Ingen eller ett objekt som representerar det omdöpta objektet.</span><span class="sxs-lookup"><span data-stu-id="252e0-175">None or an object that represents the renamed item.</span></span>

<span data-ttu-id="252e0-176">Den här cmdleten genererar ett objekt som representerar det omdöpta objektet om du anger parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="252e0-176">This cmdlet generates an object that represents the renamed item, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="252e0-177">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="252e0-177">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="252e0-178">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="252e0-178">NOTES</span></span>

<span data-ttu-id="252e0-179">`Rename-Item` är utformad för att fungera med data som exponeras av vilken provider som helst.</span><span class="sxs-lookup"><span data-stu-id="252e0-179">`Rename-Item` is designed to work with the data exposed by any provider.</span></span> <span data-ttu-id="252e0-180">Om du vill visa en lista över tillgängliga providers i din session skriver du `Get-PsProvider` .</span><span class="sxs-lookup"><span data-stu-id="252e0-180">To list the providers available in your session, type `Get-PsProvider`.</span></span> <span data-ttu-id="252e0-181">Mer information finns i [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="252e0-181">For more information, see [about_Providers](../Microsoft.PowerShell.Core/About/about_Providers.md).</span></span>

## <span data-ttu-id="252e0-182">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="252e0-182">RELATED LINKS</span></span>

[<span data-ttu-id="252e0-183">Rensa objekt</span><span class="sxs-lookup"><span data-stu-id="252e0-183">Clear-Item</span></span>](Clear-Item.md)

[<span data-ttu-id="252e0-184">Kopiera objekt</span><span class="sxs-lookup"><span data-stu-id="252e0-184">Copy-Item</span></span>](Copy-Item.md)

[<span data-ttu-id="252e0-185">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="252e0-185">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="252e0-186">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="252e0-186">Get-Item</span></span>](Get-Item.md)

[<span data-ttu-id="252e0-187">Anropa-objekt</span><span class="sxs-lookup"><span data-stu-id="252e0-187">Invoke-Item</span></span>](Invoke-Item.md)

[<span data-ttu-id="252e0-188">Flytta objekt</span><span class="sxs-lookup"><span data-stu-id="252e0-188">Move-Item</span></span>](Move-Item.md)

[<span data-ttu-id="252e0-189">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="252e0-189">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="252e0-190">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="252e0-190">Remove-Item</span></span>](Remove-Item.md)

[<span data-ttu-id="252e0-191">Byt namn – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="252e0-191">Rename-ItemProperty</span></span>](Rename-ItemProperty.md)

[<span data-ttu-id="252e0-192">Ange objekt</span><span class="sxs-lookup"><span data-stu-id="252e0-192">Set-Item</span></span>](Set-Item.md)

[<span data-ttu-id="252e0-193">about_Providers</span><span class="sxs-lookup"><span data-stu-id="252e0-193">about_Providers</span></span>](../Microsoft.PowerShell.Core/About/about_Providers.md)

