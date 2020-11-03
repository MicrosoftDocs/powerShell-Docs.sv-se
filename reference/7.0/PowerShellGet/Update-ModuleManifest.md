---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/08/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-modulemanifest?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-ModuleManifest
ms.openlocfilehash: 81c58a09cb6c4e6cedcc7abfa832af7bb694b0e1
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267927"
---
# <span data-ttu-id="267fc-103">Update-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="267fc-103">Update-ModuleManifest</span></span>

## <span data-ttu-id="267fc-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="267fc-104">SYNOPSIS</span></span>
<span data-ttu-id="267fc-105">Uppdaterar en modul manifest fil.</span><span class="sxs-lookup"><span data-stu-id="267fc-105">Updates a module manifest file.</span></span>

## <span data-ttu-id="267fc-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="267fc-106">SYNTAX</span></span>

### <span data-ttu-id="267fc-107">Alla</span><span class="sxs-lookup"><span data-stu-id="267fc-107">All</span></span>

```
Update-ModuleManifest [-Path] <String> [-NestedModules <Object[]>] [-Guid <Guid>] [-Author <String>]
 [-CompanyName <String>] [-Copyright <String>] [-RootModule <String>] [-ModuleVersion <Version>]
 [-Description <String>] [-ProcessorArchitecture <ProcessorArchitecture>]
 [-CompatiblePSEditions <String[]>] [-PowerShellVersion <Version>] [-ClrVersion <Version>]
 [-DotNetFrameworkVersion <Version>] [-PowerShellHostName <String>]
 [-PowerShellHostVersion <Version>] [-RequiredModules <Object[]>] [-TypesToProcess <String[]>]
 [-FormatsToProcess <String[]>] [-ScriptsToProcess <String[]>] [-RequiredAssemblies <String[]>]
 [-FileList <String[]>] [-ModuleList <Object[]>] [-FunctionsToExport <String[]>]
 [-AliasesToExport <String[]>] [-VariablesToExport <String[]>] [-CmdletsToExport <String[]>]
 [-DscResourcesToExport <String[]>] [-PrivateData <Hashtable>] [-Tags <String[]>]
 [-ProjectUri <Uri>] [-LicenseUri <Uri>] [-IconUri <Uri>] [-ReleaseNotes <String[]>]
 [-Prerelease <String>] [-HelpInfoUri <Uri>] [-PassThru] [-DefaultCommandPrefix <String>]
 [-ExternalModuleDependencies <String[]>] [-PackageManagementProviders <String[]>]
 [-RequireLicenseAcceptance] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="267fc-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="267fc-108">DESCRIPTION</span></span>

<span data-ttu-id="267fc-109">`Update-ModuleManifest`Cmdleten uppdaterar en modul manifest `.psd1` fil ()-fil.</span><span class="sxs-lookup"><span data-stu-id="267fc-109">The `Update-ModuleManifest` cmdlet updates a module manifest (`.psd1`) file.</span></span>

## <span data-ttu-id="267fc-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="267fc-110">EXAMPLES</span></span>

### <span data-ttu-id="267fc-111">Exempel 1: uppdatera ett modul manifest</span><span class="sxs-lookup"><span data-stu-id="267fc-111">Example 1: Update a module manifest</span></span>

<span data-ttu-id="267fc-112">Det här exemplet uppdaterar en befintlig modul manifest fil.</span><span class="sxs-lookup"><span data-stu-id="267fc-112">This example updates an existing module manifest file.</span></span> <span data-ttu-id="267fc-113">Ihopbuntning används för att skicka parameter värden till `Update-ModuleManifest` .</span><span class="sxs-lookup"><span data-stu-id="267fc-113">Splatting is used to pass parameter values to `Update-ModuleManifest`.</span></span> <span data-ttu-id="267fc-114">Mer information finns i [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span><span class="sxs-lookup"><span data-stu-id="267fc-114">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

```powershell
$Parms = @{
  Path = "C:\Test\TestManifest.psd1"
  Author = "TestUser1"
  CompanyName = "Contoso Corporation"
  Copyright = "(c) 2019 Contoso Corporation. All rights reserved."
}

Update-ModuleManifest @Parms
```

<span data-ttu-id="267fc-115">`$Parms` är en splat som lagrar parameter värden för **sökväg** , **författare** , **företags namn** och **Copyright**.</span><span class="sxs-lookup"><span data-stu-id="267fc-115">`$Parms` is a splat that stores the parameter values for **Path** , **Author** , **CompanyName** , and **Copyright**.</span></span> <span data-ttu-id="267fc-116">`Update-ModuleManifest` hämtar parameter värden från `@Parms` och uppdaterar modulens manifest **TestManifest.psd1**.</span><span class="sxs-lookup"><span data-stu-id="267fc-116">`Update-ModuleManifest` gets the parameter values from `@Parms` and updates the module manifest, **TestManifest.psd1**.</span></span>

## <span data-ttu-id="267fc-117">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="267fc-117">PARAMETERS</span></span>

### <span data-ttu-id="267fc-118">-AliasesToExport</span><span class="sxs-lookup"><span data-stu-id="267fc-118">-AliasesToExport</span></span>

<span data-ttu-id="267fc-119">Anger de alias som modulen exporterar.</span><span class="sxs-lookup"><span data-stu-id="267fc-119">Specifies the aliases that the module exports.</span></span> <span data-ttu-id="267fc-120">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="267fc-120">Wildcards are permitted.</span></span>

<span data-ttu-id="267fc-121">Använd den här parametern om du vill begränsa de alias som exporteras av modulen.</span><span class="sxs-lookup"><span data-stu-id="267fc-121">Use this parameter to restrict the aliases that are exported by the module.</span></span> <span data-ttu-id="267fc-122">**AliasesToExport** kan ta bort alias från listan över exporterade alias, men det går inte att lägga till alias i listan.</span><span class="sxs-lookup"><span data-stu-id="267fc-122">**AliasesToExport** can remove aliases from the list of exported aliases, but it can't add aliases to the list.</span></span>

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

### <span data-ttu-id="267fc-123">– Författare</span><span class="sxs-lookup"><span data-stu-id="267fc-123">-Author</span></span>

<span data-ttu-id="267fc-124">Anger modulens författare.</span><span class="sxs-lookup"><span data-stu-id="267fc-124">Specifies the module author.</span></span>

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

### <span data-ttu-id="267fc-125">-ClrVersion</span><span class="sxs-lookup"><span data-stu-id="267fc-125">-ClrVersion</span></span>

<span data-ttu-id="267fc-126">Anger den lägsta versionen av CLR (Common Language Runtime) för Microsoft .NET Framework som modulen kräver.</span><span class="sxs-lookup"><span data-stu-id="267fc-126">Specifies the minimum version of the Common Language Runtime (CLR) of the Microsoft .NET Framework that the module requires.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="267fc-127">-CmdletsToExport</span><span class="sxs-lookup"><span data-stu-id="267fc-127">-CmdletsToExport</span></span>

<span data-ttu-id="267fc-128">Anger de cmdletar som modulen exporterar.</span><span class="sxs-lookup"><span data-stu-id="267fc-128">Specifies the cmdlets that the module exports.</span></span> <span data-ttu-id="267fc-129">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="267fc-129">Wildcards are permitted.</span></span>

<span data-ttu-id="267fc-130">Använd den här parametern om du vill begränsa de cmdletar som exporteras av modulen.</span><span class="sxs-lookup"><span data-stu-id="267fc-130">Use this parameter to restrict the cmdlets that are exported by the module.</span></span> <span data-ttu-id="267fc-131">**CmdletsToExport** kan ta bort cmdletar från listan över exporterade cmdlets, men det går inte att lägga till cmdletar i listan.</span><span class="sxs-lookup"><span data-stu-id="267fc-131">**CmdletsToExport** can remove cmdlets from the list of exported cmdlets, but it can't add cmdlets to the list.</span></span>

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

### <span data-ttu-id="267fc-132">-Företags namn</span><span class="sxs-lookup"><span data-stu-id="267fc-132">-CompanyName</span></span>

<span data-ttu-id="267fc-133">Anger företaget eller leverantören som skapade modulen.</span><span class="sxs-lookup"><span data-stu-id="267fc-133">Specifies the company or vendor who created the module.</span></span>

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

### <span data-ttu-id="267fc-134">-CompatiblePSEditions</span><span class="sxs-lookup"><span data-stu-id="267fc-134">-CompatiblePSEditions</span></span>

<span data-ttu-id="267fc-135">Anger den kompatibla **PSEditions** för modulen.</span><span class="sxs-lookup"><span data-stu-id="267fc-135">Specifies the compatible **PSEditions** of the module.</span></span> <span data-ttu-id="267fc-136">Information om **PSEdition** finns i [moduler med kompatibla PowerShell-versioner](/powershell/scripting/gallery/concepts/module-psedition-support).</span><span class="sxs-lookup"><span data-stu-id="267fc-136">For information about **PSEdition** , see [Modules with compatible PowerShell Editions](/powershell/scripting/gallery/concepts/module-psedition-support).</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: Desktop, Core

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="267fc-137">-Confirm</span><span class="sxs-lookup"><span data-stu-id="267fc-137">-Confirm</span></span>

<span data-ttu-id="267fc-138">Du uppmanas att bekräfta innan du kör `Update-ModuleManifest` .</span><span class="sxs-lookup"><span data-stu-id="267fc-138">Prompts you for confirmation before running `Update-ModuleManifest`.</span></span>

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

### <span data-ttu-id="267fc-139">– Copyright</span><span class="sxs-lookup"><span data-stu-id="267fc-139">-Copyright</span></span>

<span data-ttu-id="267fc-140">Anger en Copyright-instruktion för modulen.</span><span class="sxs-lookup"><span data-stu-id="267fc-140">Specifies a copyright statement for the module.</span></span>

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

### <span data-ttu-id="267fc-141">-DefaultCommandPrefix</span><span class="sxs-lookup"><span data-stu-id="267fc-141">-DefaultCommandPrefix</span></span>

<span data-ttu-id="267fc-142">Anger standard kommandots prefix.</span><span class="sxs-lookup"><span data-stu-id="267fc-142">Specifies the default command prefix.</span></span>

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

### <span data-ttu-id="267fc-143">-Beskrivning</span><span class="sxs-lookup"><span data-stu-id="267fc-143">-Description</span></span>

<span data-ttu-id="267fc-144">Anger en beskrivning av modulen.</span><span class="sxs-lookup"><span data-stu-id="267fc-144">Specifies a description of the module.</span></span>

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

### <span data-ttu-id="267fc-145">-DotNetFrameworkVersion</span><span class="sxs-lookup"><span data-stu-id="267fc-145">-DotNetFrameworkVersion</span></span>

<span data-ttu-id="267fc-146">Anger den lägsta version av Microsoft .NET Framework som modulen kräver.</span><span class="sxs-lookup"><span data-stu-id="267fc-146">Specifies the minimum version of the Microsoft .NET Framework that the module requires.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="267fc-147">-DscResourcesToExport</span><span class="sxs-lookup"><span data-stu-id="267fc-147">-DscResourcesToExport</span></span>

<span data-ttu-id="267fc-148">Anger de DSC-resurser (Desired State Configuration) som modulen exporterar.</span><span class="sxs-lookup"><span data-stu-id="267fc-148">Specifies the Desired State Configuration (DSC) resources that the module exports.</span></span> <span data-ttu-id="267fc-149">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="267fc-149">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="267fc-150">-ExternalModuleDependencies</span><span class="sxs-lookup"><span data-stu-id="267fc-150">-ExternalModuleDependencies</span></span>

<span data-ttu-id="267fc-151">Anger en matris med beroenden för externa moduler.</span><span class="sxs-lookup"><span data-stu-id="267fc-151">Specifies an array of external module dependencies.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="267fc-152">– FileList</span><span class="sxs-lookup"><span data-stu-id="267fc-152">-FileList</span></span>

<span data-ttu-id="267fc-153">Anger alla objekt som ingår i modulen.</span><span class="sxs-lookup"><span data-stu-id="267fc-153">Specifies all items that are included in the module.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="267fc-154">-FormatsToProcess</span><span class="sxs-lookup"><span data-stu-id="267fc-154">-FormatsToProcess</span></span>

<span data-ttu-id="267fc-155">Anger de formateringsattribut ( `.ps1xml` ) som körs när modulen importeras.</span><span class="sxs-lookup"><span data-stu-id="267fc-155">Specifies the formatting files (`.ps1xml`) that run when the module is imported.</span></span>

<span data-ttu-id="267fc-156">När du importerar en modul kör PowerShell `Update-FormatData` cmdleten med de angivna filerna.</span><span class="sxs-lookup"><span data-stu-id="267fc-156">When you import a module, PowerShell runs the `Update-FormatData` cmdlet with the specified files.</span></span>
<span data-ttu-id="267fc-157">Eftersom filer som inte är begränsade påverkar formateringen alla sessionstillstånd i sessionen.</span><span class="sxs-lookup"><span data-stu-id="267fc-157">Because formatting files aren't scoped, they affect all session states in the session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="267fc-158">-FunctionsToExport</span><span class="sxs-lookup"><span data-stu-id="267fc-158">-FunctionsToExport</span></span>

<span data-ttu-id="267fc-159">Anger de funktioner som modulen exporterar.</span><span class="sxs-lookup"><span data-stu-id="267fc-159">Specifies the functions that the module exports.</span></span> <span data-ttu-id="267fc-160">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="267fc-160">Wildcards are permitted.</span></span>

<span data-ttu-id="267fc-161">Använd den här parametern om du vill begränsa vilka funktioner som exporteras av modulen.</span><span class="sxs-lookup"><span data-stu-id="267fc-161">Use this parameter to restrict the functions that are exported by the module.</span></span> <span data-ttu-id="267fc-162">**FunctionsToExport** kan ta bort funktioner från listan över exporterade alias, men det går inte att lägga till funktioner i listan.</span><span class="sxs-lookup"><span data-stu-id="267fc-162">**FunctionsToExport** can remove functions from the list of exported aliases, but it can't add functions to the list.</span></span>

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

### <span data-ttu-id="267fc-163">-GUID</span><span class="sxs-lookup"><span data-stu-id="267fc-163">-Guid</span></span>

<span data-ttu-id="267fc-164">Anger en unik identifierare för modulen.</span><span class="sxs-lookup"><span data-stu-id="267fc-164">Specifies a unique identifier for the module.</span></span> <span data-ttu-id="267fc-165">GUID kan användas för att skilja mellan moduler med samma namn.</span><span class="sxs-lookup"><span data-stu-id="267fc-165">The GUID can be used to distinguish among modules with the same name.</span></span>

```yaml
Type: System.Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="267fc-166">-HelpInfoUri</span><span class="sxs-lookup"><span data-stu-id="267fc-166">-HelpInfoUri</span></span>

<span data-ttu-id="267fc-167">Anger Internet adressen för modulens **HelpInfo XML-** fil.</span><span class="sxs-lookup"><span data-stu-id="267fc-167">Specifies the internet address of the module's **HelpInfo XML** file.</span></span> <span data-ttu-id="267fc-168">Ange en Uniform Resource Identifier (URI) som börjar med **http** eller **https**.</span><span class="sxs-lookup"><span data-stu-id="267fc-168">Enter a Uniform Resource Identifier (URI) that begins with **http** or **https**.</span></span>

<span data-ttu-id="267fc-169">**XML-filen HelpInfo** stöder den uppdaterbara hjälp funktionen som introducerades i PowerShell version 3,0.</span><span class="sxs-lookup"><span data-stu-id="267fc-169">The **HelpInfo XML** file supports the Updatable Help feature that was introduced in PowerShell version 3.0.</span></span> <span data-ttu-id="267fc-170">Den innehåller information om platsen för modulens nedladdnings bara hjälpfiler och versions numren för de senaste hjälpfilerna för varje språk som stöds.</span><span class="sxs-lookup"><span data-stu-id="267fc-170">It contains information about the location of the module's downloadable help files and the version numbers of the newest help files for each supported locale.</span></span>

<span data-ttu-id="267fc-171">Information om uppdaterbar hjälp finns [about_Updatable_Help](../Microsoft.PowerShell.Core/About/about_Updatable_Help.md).</span><span class="sxs-lookup"><span data-stu-id="267fc-171">For information about Updatable Help, see [about_Updatable_Help](../Microsoft.PowerShell.Core/About/about_Updatable_Help.md).</span></span>
<span data-ttu-id="267fc-172">Information om **XML-HelpInfo** finns i [stöd uppdaterings bar hjälp](/powershell/scripting/developer/module/supporting-updatable-help).</span><span class="sxs-lookup"><span data-stu-id="267fc-172">For information about the **HelpInfo XML** file, see [Supporting Updatable Help](/powershell/scripting/developer/module/supporting-updatable-help).</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="267fc-173">– IconUri</span><span class="sxs-lookup"><span data-stu-id="267fc-173">-IconUri</span></span>

<span data-ttu-id="267fc-174">Anger URL-adressen till en ikon för modulen.</span><span class="sxs-lookup"><span data-stu-id="267fc-174">Specifies the URL of an icon for the module.</span></span> <span data-ttu-id="267fc-175">Den angivna ikonen visas på Galleri webb sidan för modulen.</span><span class="sxs-lookup"><span data-stu-id="267fc-175">The specified icon is displayed on the gallery web page for the module.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="267fc-176">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="267fc-176">-LicenseUri</span></span>

<span data-ttu-id="267fc-177">Anger URL: en för licens villkoren för modulen.</span><span class="sxs-lookup"><span data-stu-id="267fc-177">Specifies the URL of licensing terms for the module.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="267fc-178">-ModuleList</span><span class="sxs-lookup"><span data-stu-id="267fc-178">-ModuleList</span></span>

<span data-ttu-id="267fc-179">Anger en matris med moduler som ingår i modulen.</span><span class="sxs-lookup"><span data-stu-id="267fc-179">Specifies an array of modules that are included in the module.</span></span>

<span data-ttu-id="267fc-180">Ange varje Modulnamn som en sträng eller som en hash-tabell med **Modulnamn** och **ModuleVersion** -nycklar.</span><span class="sxs-lookup"><span data-stu-id="267fc-180">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="267fc-181">Hash-tabellen kan också ha en valfri **GUID** -nyckel.</span><span class="sxs-lookup"><span data-stu-id="267fc-181">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="267fc-182">Du kan kombinera strängar och hash-tabeller i parametervärdet.</span><span class="sxs-lookup"><span data-stu-id="267fc-182">You can combine strings and hash tables in the parameter value.</span></span>

<span data-ttu-id="267fc-183">Den här nyckeln är utformad för att fungera som en modul.</span><span class="sxs-lookup"><span data-stu-id="267fc-183">This key is designed to act as a module inventory.</span></span> <span data-ttu-id="267fc-184">Modulerna som anges i värdet för den här nyckeln bearbetas inte automatiskt.</span><span class="sxs-lookup"><span data-stu-id="267fc-184">The modules that are listed in the value of this key aren't automatically processed.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="267fc-185">– ModuleVersion</span><span class="sxs-lookup"><span data-stu-id="267fc-185">-ModuleVersion</span></span>

<span data-ttu-id="267fc-186">Anger versionen för modulen.</span><span class="sxs-lookup"><span data-stu-id="267fc-186">Specifies the version of the module.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="267fc-187">-NestedModules</span><span class="sxs-lookup"><span data-stu-id="267fc-187">-NestedModules</span></span>

<span data-ttu-id="267fc-188">Anger skript moduler ( `.psm1` ) och binära moduler ( `.dll` ) som importeras till modulens sessionstillstånd.</span><span class="sxs-lookup"><span data-stu-id="267fc-188">Specifies script modules (`.psm1`) and binary modules (`.dll`) that are imported into the module's session state.</span></span> <span data-ttu-id="267fc-189">Filerna i **NestedModules** -nyckeln körs i den ordning som de är listade i värdet.</span><span class="sxs-lookup"><span data-stu-id="267fc-189">The files in the **NestedModules** key run in the order in which they're listed in the value.</span></span>

<span data-ttu-id="267fc-190">Ange varje Modulnamn som en sträng eller som en hash-tabell med **Modulnamn** och **ModuleVersion** -nycklar.</span><span class="sxs-lookup"><span data-stu-id="267fc-190">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="267fc-191">Hash-tabellen kan också ha en valfri **GUID** -nyckel.</span><span class="sxs-lookup"><span data-stu-id="267fc-191">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="267fc-192">Du kan kombinera strängar och hash-tabeller i parametervärdet.</span><span class="sxs-lookup"><span data-stu-id="267fc-192">You can combine strings and hash tables in the parameter value.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="267fc-193">-PackageManagementProviders</span><span class="sxs-lookup"><span data-stu-id="267fc-193">-PackageManagementProviders</span></span>

<span data-ttu-id="267fc-194">Anger en matris med paket hanterings leverantörer.</span><span class="sxs-lookup"><span data-stu-id="267fc-194">Specifies an array of package management providers.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="267fc-195">– PassThru</span><span class="sxs-lookup"><span data-stu-id="267fc-195">-PassThru</span></span>

<span data-ttu-id="267fc-196">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="267fc-196">Returns an object representing the item with which you're working.</span></span> <span data-ttu-id="267fc-197">Som standard `Update-ModuleManifest` genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="267fc-197">By default, `Update-ModuleManifest` doesn't generate any output.</span></span>

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

### <span data-ttu-id="267fc-198">-Path</span><span class="sxs-lookup"><span data-stu-id="267fc-198">-Path</span></span>

<span data-ttu-id="267fc-199">Anger sökvägen och fil namnet för modulens manifest.</span><span class="sxs-lookup"><span data-stu-id="267fc-199">Specifies the path and file name of the module manifest.</span></span> <span data-ttu-id="267fc-200">Ange en sökväg och ett fil namn med ett `.psd1` fil namns tillägg, till exempel `$PSHOME\Modules\MyModule\MyModule.psd1` .</span><span class="sxs-lookup"><span data-stu-id="267fc-200">Enter a path and file name with a `.psd1` file name extension, such as `$PSHOME\Modules\MyModule\MyModule.psd1`.</span></span>

<span data-ttu-id="267fc-201">Om du anger sökvägen till en befintlig fil `Update-ModuleManifest` ersätts filen utan varning om inte filen har attributet skrivskyddad.</span><span class="sxs-lookup"><span data-stu-id="267fc-201">If you specify the path to an existing file, `Update-ModuleManifest` replaces the file without warning unless the file has the read-only attribute.</span></span>

<span data-ttu-id="267fc-202">Manifestet ska finnas i modulens katalog och manifest filens namn ska vara samma som modulens katalog namn, men med ett `.psd1` tillägg.</span><span class="sxs-lookup"><span data-stu-id="267fc-202">The manifest should be located in the module's directory, and the manifest file name should be the same as the module directory name, but with a `.psd1` extension.</span></span>

<span data-ttu-id="267fc-203">Du kan inte använda variabler, t `$PSHOME` . ex. eller `$HOME` , som svar på en prompt för värdet för en **Sök vägs** parameter.</span><span class="sxs-lookup"><span data-stu-id="267fc-203">You can't use variables, such as `$PSHOME` or `$HOME`, in response to a prompt for a **Path** parameter value.</span></span> <span data-ttu-id="267fc-204">Om du vill använda en variabel inkluderar du parametern **Path** i kommandot.</span><span class="sxs-lookup"><span data-stu-id="267fc-204">To use a variable, include the **Path** parameter in the command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="267fc-205">-PowerShellHostName</span><span class="sxs-lookup"><span data-stu-id="267fc-205">-PowerShellHostName</span></span>

<span data-ttu-id="267fc-206">Anger namnet på PowerShell-värdservern som modulen kräver.</span><span class="sxs-lookup"><span data-stu-id="267fc-206">Specifies the name of the PowerShell host program that the module requires.</span></span> <span data-ttu-id="267fc-207">Ange namnet på värd programmet, till exempel PowerShell ISE värd eller ConsoleHost.</span><span class="sxs-lookup"><span data-stu-id="267fc-207">Enter the name of the host program, such as PowerShell ISE Host or ConsoleHost.</span></span> <span data-ttu-id="267fc-208">Jokertecken är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="267fc-208">Wildcards aren't permitted.</span></span>

<span data-ttu-id="267fc-209">Om du vill hitta namnet på ett värd program skriver du i programmet `$Host.Name` .</span><span class="sxs-lookup"><span data-stu-id="267fc-209">To find the name of a host program, in the program, type `$Host.Name`.</span></span>

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

### <span data-ttu-id="267fc-210">-PowerShellHostVersion</span><span class="sxs-lookup"><span data-stu-id="267fc-210">-PowerShellHostVersion</span></span>

<span data-ttu-id="267fc-211">Anger den lägsta versionen av PowerShell-värd programmet som fungerar med modulen.</span><span class="sxs-lookup"><span data-stu-id="267fc-211">Specifies the minimum version of the PowerShell host program that works with the module.</span></span> <span data-ttu-id="267fc-212">Ange ett versions nummer, till exempel 1,1.</span><span class="sxs-lookup"><span data-stu-id="267fc-212">Enter a version number, such as 1.1.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="267fc-213">– PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="267fc-213">-PowerShellVersion</span></span>

<span data-ttu-id="267fc-214">Anger den lägsta version av PowerShell som kommer att fungera med den här modulen.</span><span class="sxs-lookup"><span data-stu-id="267fc-214">Specifies the minimum version of PowerShell that will work with this module.</span></span> <span data-ttu-id="267fc-215">Du kan till exempel ange 3,0, 4,0 eller 5,0 som värde för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="267fc-215">For example, you can specify 3.0, 4.0, or 5.0 as the value of this parameter.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="267fc-216">-För hands version</span><span class="sxs-lookup"><span data-stu-id="267fc-216">-Prerelease</span></span>

<span data-ttu-id="267fc-217">Anger att modulen är för hands version.</span><span class="sxs-lookup"><span data-stu-id="267fc-217">Indicates the module is prerelease.</span></span>

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

### <span data-ttu-id="267fc-218">-PrivateData</span><span class="sxs-lookup"><span data-stu-id="267fc-218">-PrivateData</span></span>

<span data-ttu-id="267fc-219">Anger data som skickas till modulen när den importeras.</span><span class="sxs-lookup"><span data-stu-id="267fc-219">Specifies data that is passed to the module when it's imported.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="267fc-220">-ProcessorArchitecture</span><span class="sxs-lookup"><span data-stu-id="267fc-220">-ProcessorArchitecture</span></span>

<span data-ttu-id="267fc-221">Anger den processor arkitektur som modulen kräver.</span><span class="sxs-lookup"><span data-stu-id="267fc-221">Specifies the processor architecture that the module requires.</span></span>

<span data-ttu-id="267fc-222">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="267fc-222">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="267fc-223">Amd64</span><span class="sxs-lookup"><span data-stu-id="267fc-223">Amd64</span></span>
- <span data-ttu-id="267fc-224">Koppling</span><span class="sxs-lookup"><span data-stu-id="267fc-224">Arm</span></span>
- <span data-ttu-id="267fc-225">IA64</span><span class="sxs-lookup"><span data-stu-id="267fc-225">IA64</span></span>
- <span data-ttu-id="267fc-226">MSIL</span><span class="sxs-lookup"><span data-stu-id="267fc-226">MSIL</span></span>
- <span data-ttu-id="267fc-227">Ingen (okänd eller ospecificerad)</span><span class="sxs-lookup"><span data-stu-id="267fc-227">None (unknown or unspecified)</span></span>
- <span data-ttu-id="267fc-228">X86</span><span class="sxs-lookup"><span data-stu-id="267fc-228">X86</span></span>

```yaml
Type: System.Reflection.ProcessorArchitecture
Parameter Sets: (All)
Aliases:
Accepted values: None, MSIL, X86, IA64, Amd64, Arm

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="267fc-229">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="267fc-229">-ProjectUri</span></span>

<span data-ttu-id="267fc-230">Anger webb adressen till en webb sida om projektet.</span><span class="sxs-lookup"><span data-stu-id="267fc-230">Specifies the URL of a web page about this project.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="267fc-231">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="267fc-231">-ReleaseNotes</span></span>

<span data-ttu-id="267fc-232">Anger en sträng mat ris som innehåller viktig information eller kommentarer som du vill ska vara tillgängliga för den här versionen av skriptet.</span><span class="sxs-lookup"><span data-stu-id="267fc-232">Specifies a string array that contains release notes or comments that you want available for this version of the script.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="267fc-233">-RequiredAssemblies</span><span class="sxs-lookup"><span data-stu-id="267fc-233">-RequiredAssemblies</span></span>

<span data-ttu-id="267fc-234">Anger de Assembly ( `.dll` )-filer som modulen kräver.</span><span class="sxs-lookup"><span data-stu-id="267fc-234">Specifies the assembly (`.dll`) files that the module requires.</span></span> <span data-ttu-id="267fc-235">Ange sammansättnings fil namnen.</span><span class="sxs-lookup"><span data-stu-id="267fc-235">Enter the assembly file names.</span></span>
<span data-ttu-id="267fc-236">PowerShell läser in de angivna sammansättningarna innan du uppdaterar typer eller format, importerar kapslade moduler eller importerar filen som anges i värdet för nyckeln **RootModule** .</span><span class="sxs-lookup"><span data-stu-id="267fc-236">PowerShell loads the specified assemblies before updating types or formats, importing nested modules, or importing the module file that is specified in the value of the **RootModule** key.</span></span>

<span data-ttu-id="267fc-237">Använd den här parametern för att ange alla sammansättningar som modulen kräver, inklusive sammansättningar som måste läsas in för att uppdatera all formatering eller skriva filer som listas i **FormatsToProcess** -eller **TypesToProcess** -nycklarna, även om dessa sammansättningar också visas som binära moduler i **NestedModules** -nyckeln.</span><span class="sxs-lookup"><span data-stu-id="267fc-237">Use this parameter to specify all the assemblies that the module requires, including assemblies that must be loaded to update any formatting or type files that are listed in the **FormatsToProcess** or **TypesToProcess** keys, even if those assemblies are also listed as binary modules in the **NestedModules** key.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="267fc-238">-RequiredModules</span><span class="sxs-lookup"><span data-stu-id="267fc-238">-RequiredModules</span></span>

<span data-ttu-id="267fc-239">Anger moduler som måste vara i det globala sessionstillståndet.</span><span class="sxs-lookup"><span data-stu-id="267fc-239">Specifies modules that must be in the global session state.</span></span> <span data-ttu-id="267fc-240">Om de moduler som krävs inte är i det globala sessionstillståndet importeras de av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="267fc-240">If the required modules aren't in the global session state, PowerShell imports them.</span></span> <span data-ttu-id="267fc-241">Om de moduler som krävs inte är tillgängliga, `Import-Module` Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="267fc-241">If the required modules aren't available, the `Import-Module` command fails.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="267fc-242">-RequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="267fc-242">-RequireLicenseAcceptance</span></span>

<span data-ttu-id="267fc-243">Anger att licens godkännande krävs för modulen.</span><span class="sxs-lookup"><span data-stu-id="267fc-243">Specifies that a license acceptance is required for the module.</span></span>

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

### <span data-ttu-id="267fc-244">-RootModule</span><span class="sxs-lookup"><span data-stu-id="267fc-244">-RootModule</span></span>

<span data-ttu-id="267fc-245">Anger modulens primära eller rot fil.</span><span class="sxs-lookup"><span data-stu-id="267fc-245">Specifies the primary or root file of the module.</span></span> <span data-ttu-id="267fc-246">Ange fil namnet för ett skript ( `.ps1` ), en skriptbaserad modul ( `.psm1` ), ett modul manifest ( `.psd1` ), en sammansättning ( `.dll` ), en XML-fil () för cmdlet-definition ( `.cdxml` ) eller ett arbets flöde ( `.xaml` ).</span><span class="sxs-lookup"><span data-stu-id="267fc-246">Enter the file name of a script (`.ps1`), a script module (`.psm1`), a module manifest (`.psd1`), an assembly (`.dll`), a cmdlet definition XML file (`.cdxml`), or a workflow (`.xaml`).</span></span> <span data-ttu-id="267fc-247">När modulen importeras importeras medlemmar som exporteras från rot-modul filen till anroparens sessionstillstånd.</span><span class="sxs-lookup"><span data-stu-id="267fc-247">When the module is imported, the members that are exported from the root module file are imported into the caller's session state.</span></span>

<span data-ttu-id="267fc-248">Om en modul har en manifest fil och ingen rot fil har angetts i **RootModule** -nyckeln blir manifestet den primära filen för modulen.</span><span class="sxs-lookup"><span data-stu-id="267fc-248">If a module has a manifest file and no root file has been specified in the **RootModule** key, the manifest becomes the primary file for the module.</span></span> <span data-ttu-id="267fc-249">Och är modulen en manifest-modul (ModuleType = manifest).</span><span class="sxs-lookup"><span data-stu-id="267fc-249">And, the module becomes a manifest module (ModuleType = Manifest).</span></span>

<span data-ttu-id="267fc-250">För att exportera medlemmar från `.psm1` eller `.dll` filer i en modul som har ett manifest, måste namnen på filerna anges i värdena för **RootModule** -eller **NestedModules** -nycklarna i manifestet.</span><span class="sxs-lookup"><span data-stu-id="267fc-250">To export members from `.psm1` or `.dll` files in a module that has a manifest, the names of those files must be specified in the values of the **RootModule** or **NestedModules** keys in the manifest.</span></span> <span data-ttu-id="267fc-251">Annars exporteras inte deras medlemmar.</span><span class="sxs-lookup"><span data-stu-id="267fc-251">Otherwise, their members aren't exported.</span></span>

<span data-ttu-id="267fc-252">I PowerShell 2,0 kallades den här nyckeln för **ModuleToProcess**.</span><span class="sxs-lookup"><span data-stu-id="267fc-252">In PowerShell 2.0, this key was called **ModuleToProcess**.</span></span>

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

### <span data-ttu-id="267fc-253">-ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="267fc-253">-ScriptsToProcess</span></span>

<span data-ttu-id="267fc-254">Anger skript ( `.ps1` )-filer som körs i anroparens sessionstillstånd när modulen importeras.</span><span class="sxs-lookup"><span data-stu-id="267fc-254">Specifies script (`.ps1`) files that run in the caller's session state when the module is imported.</span></span>
<span data-ttu-id="267fc-255">Du kan använda dessa skript för att förbereda en miljö, precis som du kan använda ett inloggnings skript.</span><span class="sxs-lookup"><span data-stu-id="267fc-255">You can use these scripts to prepare an environment, just as you might use a login script.</span></span>

<span data-ttu-id="267fc-256">Använd nyckeln **NestedModules** för att ange skript som körs i modulens sessionstillstånd.</span><span class="sxs-lookup"><span data-stu-id="267fc-256">To specify scripts that run in the module's session state, use the **NestedModules** key.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="267fc-257">– Taggar</span><span class="sxs-lookup"><span data-stu-id="267fc-257">-Tags</span></span>

<span data-ttu-id="267fc-258">Anger en matris med taggar.</span><span class="sxs-lookup"><span data-stu-id="267fc-258">Specifies an array of tags.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="267fc-259">-TypesToProcess</span><span class="sxs-lookup"><span data-stu-id="267fc-259">-TypesToProcess</span></span>

<span data-ttu-id="267fc-260">Anger de typ filer ( `.ps1xml` ) som körs när modulen importeras.</span><span class="sxs-lookup"><span data-stu-id="267fc-260">Specifies the type files (`.ps1xml`) that run when the module is imported.</span></span>

<span data-ttu-id="267fc-261">När du importerar modulen kör PowerShell `Update-TypeData` cmdleten med de angivna filerna.</span><span class="sxs-lookup"><span data-stu-id="267fc-261">When you import the module, PowerShell runs the `Update-TypeData` cmdlet with the specified files.</span></span>
<span data-ttu-id="267fc-262">Eftersom filtypen inte är begränsad, påverkar de alla sessionstillstånd i sessionen.</span><span class="sxs-lookup"><span data-stu-id="267fc-262">Because type files aren't scoped, they affect all session states in the session.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="267fc-263">-VariablesToExport</span><span class="sxs-lookup"><span data-stu-id="267fc-263">-VariablesToExport</span></span>

<span data-ttu-id="267fc-264">Anger de variabler som modulen exporterar.</span><span class="sxs-lookup"><span data-stu-id="267fc-264">Specifies the variables that the module exports.</span></span> <span data-ttu-id="267fc-265">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="267fc-265">Wildcards are permitted.</span></span>

<span data-ttu-id="267fc-266">Använd den här parametern om du vill begränsa de variabler som exporteras av modulen.</span><span class="sxs-lookup"><span data-stu-id="267fc-266">Use this parameter to restrict the variables that are exported by the module.</span></span> <span data-ttu-id="267fc-267">**VariablesToExport** kan ta bort variabler från listan över exporterade variabler, men det går inte att lägga till variabler i listan.</span><span class="sxs-lookup"><span data-stu-id="267fc-267">**VariablesToExport** can remove variables from the list of exported variables, but it can't add variables to the list.</span></span>

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

### <span data-ttu-id="267fc-268">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="267fc-268">-WhatIf</span></span>

<span data-ttu-id="267fc-269">Visar vad som händer om `Update-ModuleManifest` körs.</span><span class="sxs-lookup"><span data-stu-id="267fc-269">Shows what would happen if `Update-ModuleManifest` runs.</span></span> <span data-ttu-id="267fc-270">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="267fc-270">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="267fc-271">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="267fc-271">CommonParameters</span></span>

<span data-ttu-id="267fc-272">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="267fc-272">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="267fc-273">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="267fc-273">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="267fc-274">INDATA</span><span class="sxs-lookup"><span data-stu-id="267fc-274">INPUTS</span></span>

### <span data-ttu-id="267fc-275">System. String</span><span class="sxs-lookup"><span data-stu-id="267fc-275">System.String</span></span>

## <span data-ttu-id="267fc-276">UTDATA</span><span class="sxs-lookup"><span data-stu-id="267fc-276">OUTPUTS</span></span>

### <span data-ttu-id="267fc-277">System. Object</span><span class="sxs-lookup"><span data-stu-id="267fc-277">System.Object</span></span>

## <span data-ttu-id="267fc-278">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="267fc-278">NOTES</span></span>

## <span data-ttu-id="267fc-279">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="267fc-279">RELATED LINKS</span></span>
