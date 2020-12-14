---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/export-alias?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Export-Alias
ms.openlocfilehash: 9da204513ed4a17eb8dc20481b878a4a783534f6
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708719"
---
# <span data-ttu-id="3362d-102">Export-Alias</span><span class="sxs-lookup"><span data-stu-id="3362d-102">Export-Alias</span></span>

## <span data-ttu-id="3362d-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="3362d-103">SYNOPSIS</span></span>
<span data-ttu-id="3362d-104">Exporterar information om aktuella definierade alias till en fil.</span><span class="sxs-lookup"><span data-stu-id="3362d-104">Exports information about currently defined aliases to a file.</span></span>

## <span data-ttu-id="3362d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3362d-105">SYNTAX</span></span>

### <span data-ttu-id="3362d-106">ByPath (standard)</span><span class="sxs-lookup"><span data-stu-id="3362d-106">ByPath (Default)</span></span>

```
Export-Alias [-Path] <String> [[-Name] <String[]>] [-PassThru] [-As <ExportAliasFormat>] [-Append] [-Force]
 [-NoClobber] [-Description <String>] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="3362d-107">ByLiteralPath</span><span class="sxs-lookup"><span data-stu-id="3362d-107">ByLiteralPath</span></span>

```
Export-Alias -LiteralPath <String> [[-Name] <String[]>] [-PassThru] [-As <ExportAliasFormat>] [-Append]
 [-Force] [-NoClobber] [-Description <String>] [-Scope <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="3362d-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="3362d-108">DESCRIPTION</span></span>

<span data-ttu-id="3362d-109">`Export-Alias`Cmdleten exporterar aliasen i den aktuella sessionen till en fil.</span><span class="sxs-lookup"><span data-stu-id="3362d-109">The `Export-Alias` cmdlet exports the aliases in the current session to a file.</span></span>
<span data-ttu-id="3362d-110">Om utdatafilen inte finns skapas den av cmdleten.</span><span class="sxs-lookup"><span data-stu-id="3362d-110">If the output file does not exist, the cmdlet will create it.</span></span>

<span data-ttu-id="3362d-111">`Export-Alias` kan exportera alias i ett visst omfång eller med alla omfattningar, det kan generera data i CSV-format eller som en serie med Set-Alias-kommandon som du kan lägga till i en session eller till en PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="3362d-111">`Export-Alias` can export the aliases in a particular scope or all scopes, it can generate the data in CSV format or as a series of Set-Alias commands that you can add to a session or to a PowerShell profile.</span></span>

## <span data-ttu-id="3362d-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="3362d-112">EXAMPLES</span></span>

### <span data-ttu-id="3362d-113">Exempel 1: exportera ett alias</span><span class="sxs-lookup"><span data-stu-id="3362d-113">Example 1: Export an alias</span></span>

```powershell
Export-Alias -Path "alias.csv"
```

<span data-ttu-id="3362d-114">Det här kommandot exporterar aktuell aliasresurspost till en fil med namnet Alias.csv i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="3362d-114">This command exports current alias information to a file named Alias.csv in the current directory.</span></span>

### <span data-ttu-id="3362d-115">Exempel 2: exportera ett alias om inte export filen redan finns</span><span class="sxs-lookup"><span data-stu-id="3362d-115">Example 2: Export an alias unless the export file already exists</span></span>

```powershell
Export-Alias -Path "alias.csv" -NoClobber
```

<span data-ttu-id="3362d-116">Detta kommando exporterar alias i den aktuella sessionen till en Alias.csv-fil.</span><span class="sxs-lookup"><span data-stu-id="3362d-116">This command exports the aliases in the current session to an Alias.csv file.</span></span>

<span data-ttu-id="3362d-117">Eftersom parametern **NoClobber** anges kommer kommandot att Miss förväntas om det redan finns en Alias.csv fil i den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="3362d-117">Because the **NoClobber** parameter is specified, the command will fail if an Alias.csv file already exists in the current directory.</span></span>

### <span data-ttu-id="3362d-118">Exempel 3: Lägg till alias i en fil</span><span class="sxs-lookup"><span data-stu-id="3362d-118">Example 3: Append aliases to a file</span></span>

```powershell
Export-Alias -Path "alias.csv" -Append -Description "Appended Aliases" -Force
```

<span data-ttu-id="3362d-119">Detta kommando lägger till alias i den aktuella sessionen till Alias.csv-filen.</span><span class="sxs-lookup"><span data-stu-id="3362d-119">This command appends the aliases in the current session to the Alias.csv file.</span></span>

<span data-ttu-id="3362d-120">Kommandot använder parametern **Description** för att lägga till en beskrivning till kommentarerna överst i filen.</span><span class="sxs-lookup"><span data-stu-id="3362d-120">The command uses the **Description** parameter to add a description to the comments at the top of the file.</span></span>

<span data-ttu-id="3362d-121">Kommandot använder också parametern **Force** för att skriva över eventuella befintliga Alias.csv-filer, även om de har attributet skrivskyddad.</span><span class="sxs-lookup"><span data-stu-id="3362d-121">The command also uses the **Force** parameter to overwrite any existing Alias.csv files, even if they have the read-only attribute.</span></span>

### <span data-ttu-id="3362d-122">Exempel 4: exportera alias som ett skript</span><span class="sxs-lookup"><span data-stu-id="3362d-122">Example 4: Export aliases as a script</span></span>

```powershell
Export-Alias -Path "alias.ps1" -As Script
Add-Content -Path $Profile -Value (Get-Content alias.ps1)
$S = New-PSSession -ComputerName Server01
Invoke-Command -Session $S -FilePath .\alias.ps1
```

<span data-ttu-id="3362d-123">Det här exemplet visar hur du använder skript fil formatet som `Export-Alias` genereras.</span><span class="sxs-lookup"><span data-stu-id="3362d-123">This example shows how to use the script file format that `Export-Alias` generates.</span></span>

<span data-ttu-id="3362d-124">Det första kommandot exporterar aliasen i sessionen till Alias.ps1-filen.</span><span class="sxs-lookup"><span data-stu-id="3362d-124">The first command exports the aliases in the session to the Alias.ps1 file.</span></span>
<span data-ttu-id="3362d-125">Den använder parametern **as** med ett värde för skript för att skapa en fil som innehåller ett Set-Alias-kommando för varje alias.</span><span class="sxs-lookup"><span data-stu-id="3362d-125">It uses the **As** parameter with a value of Script to generate a file that contains a Set-Alias command for each alias.</span></span>

<span data-ttu-id="3362d-126">Det andra kommandot lägger till alias i Alias.ps1-filen till CurrentUser-CurrentHost profilen.</span><span class="sxs-lookup"><span data-stu-id="3362d-126">The second command adds the aliases in the Alias.ps1 file to the CurrentUser-CurrentHost profile.</span></span>
<span data-ttu-id="3362d-127">Sökvägen till profilen sparas i `$Profile` variabeln.</span><span class="sxs-lookup"><span data-stu-id="3362d-127">The path to the profile is saved in the `$Profile` variable.</span></span>
<span data-ttu-id="3362d-128">Kommandot använder `Get-Content` cmdleten för att hämta alias från Alias.ps1-filen och `Add-Content` cmdlet: en för att lägga till dem i profilen.</span><span class="sxs-lookup"><span data-stu-id="3362d-128">The command uses the `Get-Content` cmdlet to get the aliases from the Alias.ps1 file and the `Add-Content` cmdlet to add them to the profile.</span></span>
<span data-ttu-id="3362d-129">Mer information finns i about_Profiles.</span><span class="sxs-lookup"><span data-stu-id="3362d-129">For more information, see about_Profiles.</span></span>

<span data-ttu-id="3362d-130">De tredje och fjärde kommandona lägger till alias i Alias.ps1-filen till en fjärrsession på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="3362d-130">The third and fourth commands add the aliases in the Alias.ps1 file to a remote session on the Server01 computer.</span></span>
<span data-ttu-id="3362d-131">Det tredje kommandot använder `New-PSSession` cmdleten för att skapa sessionen.</span><span class="sxs-lookup"><span data-stu-id="3362d-131">The third command uses the `New-PSSession` cmdlet to create the session.</span></span>
<span data-ttu-id="3362d-132">Det fjärde kommandot använder parametern **sökväg** för `Invoke-Command` cmdleten för att köra Alias.ps1-filen i den nya sessionen.</span><span class="sxs-lookup"><span data-stu-id="3362d-132">The fourth command uses the **FilePath** parameter of the `Invoke-Command` cmdlet to run the Alias.ps1 file in the new session.</span></span>

## <span data-ttu-id="3362d-133">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="3362d-133">PARAMETERS</span></span>

### <span data-ttu-id="3362d-134">-Lägg till</span><span class="sxs-lookup"><span data-stu-id="3362d-134">-Append</span></span>

<span data-ttu-id="3362d-135">Anger att denna cmdlet lägger till utdata i den angivna filen i stället för att skriva över det befintliga innehållet i filen.</span><span class="sxs-lookup"><span data-stu-id="3362d-135">Indicates that this cmdlet appends the output to the specified file, rather than overwriting the existing contents of that file.</span></span>

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

### <span data-ttu-id="3362d-136">– Som</span><span class="sxs-lookup"><span data-stu-id="3362d-136">-As</span></span>

<span data-ttu-id="3362d-137">Anger utdataformatet.</span><span class="sxs-lookup"><span data-stu-id="3362d-137">Specifies the output format.</span></span>
<span data-ttu-id="3362d-138">CSV är standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="3362d-138">CSV is the default.</span></span>
<span data-ttu-id="3362d-139">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="3362d-139">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="3362d-140">SKV.</span><span class="sxs-lookup"><span data-stu-id="3362d-140">CSV.</span></span>
<span data-ttu-id="3362d-141">Format med kommaavgränsade värden (CSV).</span><span class="sxs-lookup"><span data-stu-id="3362d-141">Comma-separated value (CSV) format.</span></span>
- <span data-ttu-id="3362d-142">Över.</span><span class="sxs-lookup"><span data-stu-id="3362d-142">Script.</span></span>
<span data-ttu-id="3362d-143">Skapar ett `Set-Alias` kommando för varje exporterat alias.</span><span class="sxs-lookup"><span data-stu-id="3362d-143">Creates a `Set-Alias` command for each exported alias.</span></span>
<span data-ttu-id="3362d-144">Om du namnger utdatafilen med fil namns tillägget. ps1 kan du köra det som ett skript för att lägga till alias till en session.</span><span class="sxs-lookup"><span data-stu-id="3362d-144">If you name the output file with a .ps1 file name extension, you can run it as a script to add the aliases to any session.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ExportAliasFormat
Parameter Sets: (All)
Aliases:
Accepted values: Csv, Script

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3362d-145">-Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3362d-145">-Description</span></span>

<span data-ttu-id="3362d-146">Anger beskrivningen av den exporterade filen.</span><span class="sxs-lookup"><span data-stu-id="3362d-146">Specifies the description of the exported file.</span></span>
<span data-ttu-id="3362d-147">Beskrivningen visas som en kommentar överst i filen, efter rubrik informationen.</span><span class="sxs-lookup"><span data-stu-id="3362d-147">The description appears as a comment at the top of the file, following the header information.</span></span>

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

### <span data-ttu-id="3362d-148">-Force</span><span class="sxs-lookup"><span data-stu-id="3362d-148">-Force</span></span>

<span data-ttu-id="3362d-149">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="3362d-149">Forces the command to run without asking for user confirmation.</span></span>

<span data-ttu-id="3362d-150">Skriver över utdatafilen, även om det skrivskyddade attributet är inställt på filen.</span><span class="sxs-lookup"><span data-stu-id="3362d-150">Overwrites the output file, even if the read-only attribute is set on the file.</span></span>

<span data-ttu-id="3362d-151">Som standard `Export-Alias` skriver överskrivna filer utan varning, om inte attributet skrivskyddad eller dold har angetts eller parametern **NoClobber** används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="3362d-151">By default, `Export-Alias` overwrites files without warning, unless the read-only or hidden attribute is set or the **NoClobber** parameter is used in the command.</span></span>
<span data-ttu-id="3362d-152">**NoClobber** -parametern har företräde framför parametern **Force** när båda används i ett kommando.</span><span class="sxs-lookup"><span data-stu-id="3362d-152">The **NoClobber** parameter takes precedence over the **Force** parameter when both are used in a command.</span></span>

<span data-ttu-id="3362d-153">**Force** -parametern kan inte tvinga `Export-Alias` att skriva över filer med det dolda attributet.</span><span class="sxs-lookup"><span data-stu-id="3362d-153">The **Force** parameter cannot force `Export-Alias` to overwrite files with the hidden attribute.</span></span>

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

### <span data-ttu-id="3362d-154">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="3362d-154">-LiteralPath</span></span>

<span data-ttu-id="3362d-155">Anger sökvägen till utdatafilen.</span><span class="sxs-lookup"><span data-stu-id="3362d-155">Specifies the path to the output file.</span></span>
<span data-ttu-id="3362d-156">Till skillnad från **sökväg** används värdet för parametern **LiteralPath** exakt som det har angetts.</span><span class="sxs-lookup"><span data-stu-id="3362d-156">Unlike **Path**, the value of the **LiteralPath** parameter is used exactly as it is typed.</span></span>
<span data-ttu-id="3362d-157">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="3362d-157">No characters are interpreted as wildcards.</span></span>
<span data-ttu-id="3362d-158">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="3362d-158">If the path includes escape characters, enclose it in single quotation marks.</span></span>
<span data-ttu-id="3362d-159">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="3362d-159">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

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

### <span data-ttu-id="3362d-160">-Name</span><span class="sxs-lookup"><span data-stu-id="3362d-160">-Name</span></span>

<span data-ttu-id="3362d-161">Anger namnen som en matris med de alias som ska exporteras.</span><span class="sxs-lookup"><span data-stu-id="3362d-161">Specifies the names as an array of the aliases to export.</span></span>
<span data-ttu-id="3362d-162">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="3362d-162">Wildcards are permitted.</span></span>

<span data-ttu-id="3362d-163">Som standard `Export-Alias` exporteras alla alias i sessionen eller omfattningen.</span><span class="sxs-lookup"><span data-stu-id="3362d-163">By default, `Export-Alias` exports all aliases in the session or scope.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="3362d-164">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="3362d-164">-NoClobber</span></span>

<span data-ttu-id="3362d-165">Anger att denna cmdlet förhindrar att `Export-Alias` filer skrivs över, även om **Force** -parametern används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="3362d-165">Indicates that this cmdlet prevents `Export-Alias` from overwriting any files, even if the **Force** parameter is used in the command.</span></span>

<span data-ttu-id="3362d-166">Om parametern **NoClobber** utelämnas skrivs `Export-Alias` en befintlig fil över utan varning, om inte attributet skrivskyddad anges för filen.</span><span class="sxs-lookup"><span data-stu-id="3362d-166">If the **NoClobber** parameter is omitted, `Export-Alias` will overwrite an existing file without warning, unless the read-only attribute is set on the file.</span></span>
<span data-ttu-id="3362d-167">*NoClobber* prioriteras över **Force** -parametern som tillåter `Export-Alias` att en fil skrivs över med attributet skrivskyddad.</span><span class="sxs-lookup"><span data-stu-id="3362d-167">*NoClobber* takes precedence over the **Force** parameter, which permits `Export-Alias` to overwrite a file with the read-only attribute.</span></span>

<span data-ttu-id="3362d-168">*NoClobber* förhindrar inte att parametern **Lägg** till innehåll läggs till i en befintlig fil.</span><span class="sxs-lookup"><span data-stu-id="3362d-168">*NoClobber* does not prevent the **Append** parameter from adding content to an existing file.</span></span>

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

### <span data-ttu-id="3362d-169">– PassThru</span><span class="sxs-lookup"><span data-stu-id="3362d-169">-PassThru</span></span>

<span data-ttu-id="3362d-170">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="3362d-170">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="3362d-171">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="3362d-171">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="3362d-172">-Path</span><span class="sxs-lookup"><span data-stu-id="3362d-172">-Path</span></span>

<span data-ttu-id="3362d-173">Anger sökvägen till utdatafilen.</span><span class="sxs-lookup"><span data-stu-id="3362d-173">Specifies the path to the output file.</span></span>
<span data-ttu-id="3362d-174">Jokertecken tillåts, men värdet för den resulterande sökvägen måste matcha ett enda fil namn.</span><span class="sxs-lookup"><span data-stu-id="3362d-174">Wildcards are permitted, but the resulting path value must resolve to a single file name.</span></span>

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="3362d-175">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="3362d-175">-Scope</span></span>

<span data-ttu-id="3362d-176">Anger omfånget som aliasen ska exporteras från.</span><span class="sxs-lookup"><span data-stu-id="3362d-176">Specifies the scope from which the aliases should be exported.</span></span>
<span data-ttu-id="3362d-177">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="3362d-177">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="3362d-178">Global</span><span class="sxs-lookup"><span data-stu-id="3362d-178">Global</span></span>
- <span data-ttu-id="3362d-179">Lokal</span><span class="sxs-lookup"><span data-stu-id="3362d-179">Local</span></span>
- <span data-ttu-id="3362d-180">Skript</span><span class="sxs-lookup"><span data-stu-id="3362d-180">Script</span></span>
- <span data-ttu-id="3362d-181">Ett tal i förhållande till det aktuella omfånget (0 till antalet omfattningar där 0 är det aktuella omfånget och 1 är överordnat)</span><span class="sxs-lookup"><span data-stu-id="3362d-181">A number relative to the current scope (0 through the number of scopes where 0 is the current scope and 1 is its parent)</span></span>

<span data-ttu-id="3362d-182">Standardvärdet är Local.</span><span class="sxs-lookup"><span data-stu-id="3362d-182">The default value is Local.</span></span>
<span data-ttu-id="3362d-183">Mer information finns i about_Scopes.</span><span class="sxs-lookup"><span data-stu-id="3362d-183">For more information, see about_Scopes.</span></span>

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

### <span data-ttu-id="3362d-184">-Confirm</span><span class="sxs-lookup"><span data-stu-id="3362d-184">-Confirm</span></span>

<span data-ttu-id="3362d-185">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="3362d-185">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="3362d-186">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="3362d-186">-WhatIf</span></span>

<span data-ttu-id="3362d-187">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="3362d-187">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="3362d-188">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="3362d-188">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="3362d-189">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3362d-189">CommonParameters</span></span>

<span data-ttu-id="3362d-190">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3362d-190">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3362d-191">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="3362d-191">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3362d-192">INDATA</span><span class="sxs-lookup"><span data-stu-id="3362d-192">INPUTS</span></span>

### <span data-ttu-id="3362d-193">Inga.</span><span class="sxs-lookup"><span data-stu-id="3362d-193">None.</span></span>

<span data-ttu-id="3362d-194">Det går inte att skicka pipe-objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3362d-194">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="3362d-195">UTDATA</span><span class="sxs-lookup"><span data-stu-id="3362d-195">OUTPUTS</span></span>

### <span data-ttu-id="3362d-196">Ingen eller system. Management. Automation. AliasInfo</span><span class="sxs-lookup"><span data-stu-id="3362d-196">None or System.Management.Automation.AliasInfo</span></span>

<span data-ttu-id="3362d-197">När du använder parametern **Passthru** `Export-Alias` returneras ett objekt av **system. Management. Automation. AliasInfo** som representerar aliaset.</span><span class="sxs-lookup"><span data-stu-id="3362d-197">When you use the **Passthru** parameter, `Export-Alias` returns a **System.Management.Automation.AliasInfo** object that represents the alias.</span></span>
<span data-ttu-id="3362d-198">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="3362d-198">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="3362d-199">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="3362d-199">NOTES</span></span>

* <span data-ttu-id="3362d-200">Du kan bara Export-Aliases till en fil.</span><span class="sxs-lookup"><span data-stu-id="3362d-200">You can only Export-Aliases to a file.</span></span>

## <span data-ttu-id="3362d-201">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="3362d-201">RELATED LINKS</span></span>

[<span data-ttu-id="3362d-202">Get-alias</span><span class="sxs-lookup"><span data-stu-id="3362d-202">Get-Alias</span></span>](Get-Alias.md)

[<span data-ttu-id="3362d-203">Importera-alias</span><span class="sxs-lookup"><span data-stu-id="3362d-203">Import-Alias</span></span>](Import-Alias.md)

[<span data-ttu-id="3362d-204">Nytt-alias</span><span class="sxs-lookup"><span data-stu-id="3362d-204">New-Alias</span></span>](New-Alias.md)

[<span data-ttu-id="3362d-205">Set-alias</span><span class="sxs-lookup"><span data-stu-id="3362d-205">Set-Alias</span></span>](Set-Alias.md)

