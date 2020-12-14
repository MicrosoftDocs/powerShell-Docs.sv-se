---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 07/08/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/update-modulemanifest?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-ModuleManifest
ms.openlocfilehash: 4f00450257178cac72d03303358150fd9f5cd26b
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891824"
---
# <span data-ttu-id="c70bc-102">Update-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="c70bc-102">Update-ModuleManifest</span></span>

## <span data-ttu-id="c70bc-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="c70bc-103">SYNOPSIS</span></span>
<span data-ttu-id="c70bc-104">Uppdaterar en modul manifest fil.</span><span class="sxs-lookup"><span data-stu-id="c70bc-104">Updates a module manifest file.</span></span>

## <span data-ttu-id="c70bc-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c70bc-105">SYNTAX</span></span>

### <span data-ttu-id="c70bc-106">Alla</span><span class="sxs-lookup"><span data-stu-id="c70bc-106">All</span></span>

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

## <span data-ttu-id="c70bc-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="c70bc-107">DESCRIPTION</span></span>

<span data-ttu-id="c70bc-108">`Update-ModuleManifest`Cmdleten uppdaterar en modul manifest `.psd1` fil ()-fil.</span><span class="sxs-lookup"><span data-stu-id="c70bc-108">The `Update-ModuleManifest` cmdlet updates a module manifest (`.psd1`) file.</span></span>

## <span data-ttu-id="c70bc-109">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="c70bc-109">EXAMPLES</span></span>

### <span data-ttu-id="c70bc-110">Exempel 1: uppdatera ett modul manifest</span><span class="sxs-lookup"><span data-stu-id="c70bc-110">Example 1: Update a module manifest</span></span>

<span data-ttu-id="c70bc-111">Det här exemplet uppdaterar en befintlig modul manifest fil.</span><span class="sxs-lookup"><span data-stu-id="c70bc-111">This example updates an existing module manifest file.</span></span> <span data-ttu-id="c70bc-112">Ihopbuntning används för att skicka parameter värden till `Update-ModuleManifest` .</span><span class="sxs-lookup"><span data-stu-id="c70bc-112">Splatting is used to pass parameter values to `Update-ModuleManifest`.</span></span> <span data-ttu-id="c70bc-113">Mer information finns i [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span><span class="sxs-lookup"><span data-stu-id="c70bc-113">For more information, see [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>

```powershell
$Parms = @{
  Path = "C:\Test\TestManifest.psd1"
  Author = "TestUser1"
  CompanyName = "Contoso Corporation"
  Copyright = "(c) 2019 Contoso Corporation. All rights reserved."
}

Update-ModuleManifest @Parms
```

<span data-ttu-id="c70bc-114">`$Parms` är en splat som lagrar parameter värden för **sökväg**, **författare**, **företags namn** och **Copyright**.</span><span class="sxs-lookup"><span data-stu-id="c70bc-114">`$Parms` is a splat that stores the parameter values for **Path**, **Author**, **CompanyName**, and **Copyright**.</span></span> <span data-ttu-id="c70bc-115">`Update-ModuleManifest` hämtar parameter värden från `@Parms` och uppdaterar modulens manifest **TestManifest.psd1**.</span><span class="sxs-lookup"><span data-stu-id="c70bc-115">`Update-ModuleManifest` gets the parameter values from `@Parms` and updates the module manifest, **TestManifest.psd1**.</span></span>

## <span data-ttu-id="c70bc-116">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="c70bc-116">PARAMETERS</span></span>

### <span data-ttu-id="c70bc-117">-AliasesToExport</span><span class="sxs-lookup"><span data-stu-id="c70bc-117">-AliasesToExport</span></span>

<span data-ttu-id="c70bc-118">Anger de alias som modulen exporterar.</span><span class="sxs-lookup"><span data-stu-id="c70bc-118">Specifies the aliases that the module exports.</span></span> <span data-ttu-id="c70bc-119">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="c70bc-119">Wildcards are permitted.</span></span>

<span data-ttu-id="c70bc-120">Använd den här parametern om du vill begränsa de alias som exporteras av modulen.</span><span class="sxs-lookup"><span data-stu-id="c70bc-120">Use this parameter to restrict the aliases that are exported by the module.</span></span> <span data-ttu-id="c70bc-121">**AliasesToExport** kan ta bort alias från listan över exporterade alias, men det går inte att lägga till alias i listan.</span><span class="sxs-lookup"><span data-stu-id="c70bc-121">**AliasesToExport** can remove aliases from the list of exported aliases, but it can't add aliases to the list.</span></span>

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

### <span data-ttu-id="c70bc-122">– Författare</span><span class="sxs-lookup"><span data-stu-id="c70bc-122">-Author</span></span>

<span data-ttu-id="c70bc-123">Anger modulens författare.</span><span class="sxs-lookup"><span data-stu-id="c70bc-123">Specifies the module author.</span></span>

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

### <span data-ttu-id="c70bc-124">-ClrVersion</span><span class="sxs-lookup"><span data-stu-id="c70bc-124">-ClrVersion</span></span>

<span data-ttu-id="c70bc-125">Anger den lägsta versionen av CLR (Common Language Runtime) för Microsoft .NET Framework som modulen kräver.</span><span class="sxs-lookup"><span data-stu-id="c70bc-125">Specifies the minimum version of the Common Language Runtime (CLR) of the Microsoft .NET Framework that the module requires.</span></span>

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

### <span data-ttu-id="c70bc-126">-CmdletsToExport</span><span class="sxs-lookup"><span data-stu-id="c70bc-126">-CmdletsToExport</span></span>

<span data-ttu-id="c70bc-127">Anger de cmdletar som modulen exporterar.</span><span class="sxs-lookup"><span data-stu-id="c70bc-127">Specifies the cmdlets that the module exports.</span></span> <span data-ttu-id="c70bc-128">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="c70bc-128">Wildcards are permitted.</span></span>

<span data-ttu-id="c70bc-129">Använd den här parametern om du vill begränsa de cmdletar som exporteras av modulen.</span><span class="sxs-lookup"><span data-stu-id="c70bc-129">Use this parameter to restrict the cmdlets that are exported by the module.</span></span> <span data-ttu-id="c70bc-130">**CmdletsToExport** kan ta bort cmdletar från listan över exporterade cmdlets, men det går inte att lägga till cmdletar i listan.</span><span class="sxs-lookup"><span data-stu-id="c70bc-130">**CmdletsToExport** can remove cmdlets from the list of exported cmdlets, but it can't add cmdlets to the list.</span></span>

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

### <span data-ttu-id="c70bc-131">-Företags namn</span><span class="sxs-lookup"><span data-stu-id="c70bc-131">-CompanyName</span></span>

<span data-ttu-id="c70bc-132">Anger företaget eller leverantören som skapade modulen.</span><span class="sxs-lookup"><span data-stu-id="c70bc-132">Specifies the company or vendor who created the module.</span></span>

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

### <span data-ttu-id="c70bc-133">-CompatiblePSEditions</span><span class="sxs-lookup"><span data-stu-id="c70bc-133">-CompatiblePSEditions</span></span>

<span data-ttu-id="c70bc-134">Anger den kompatibla **PSEditions** för modulen.</span><span class="sxs-lookup"><span data-stu-id="c70bc-134">Specifies the compatible **PSEditions** of the module.</span></span> <span data-ttu-id="c70bc-135">Information om **PSEdition** finns i [moduler med kompatibla PowerShell-versioner](/powershell/scripting/gallery/concepts/module-psedition-support).</span><span class="sxs-lookup"><span data-stu-id="c70bc-135">For information about **PSEdition**, see [Modules with compatible PowerShell Editions](/powershell/scripting/gallery/concepts/module-psedition-support).</span></span>

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

### <span data-ttu-id="c70bc-136">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c70bc-136">-Confirm</span></span>

<span data-ttu-id="c70bc-137">Du uppmanas att bekräfta innan du kör `Update-ModuleManifest` .</span><span class="sxs-lookup"><span data-stu-id="c70bc-137">Prompts you for confirmation before running `Update-ModuleManifest`.</span></span>

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

### <span data-ttu-id="c70bc-138">– Copyright</span><span class="sxs-lookup"><span data-stu-id="c70bc-138">-Copyright</span></span>

<span data-ttu-id="c70bc-139">Anger en Copyright-instruktion för modulen.</span><span class="sxs-lookup"><span data-stu-id="c70bc-139">Specifies a copyright statement for the module.</span></span>

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

### <span data-ttu-id="c70bc-140">-DefaultCommandPrefix</span><span class="sxs-lookup"><span data-stu-id="c70bc-140">-DefaultCommandPrefix</span></span>

<span data-ttu-id="c70bc-141">Anger standard kommandots prefix.</span><span class="sxs-lookup"><span data-stu-id="c70bc-141">Specifies the default command prefix.</span></span>

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

### <span data-ttu-id="c70bc-142">-Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c70bc-142">-Description</span></span>

<span data-ttu-id="c70bc-143">Anger en beskrivning av modulen.</span><span class="sxs-lookup"><span data-stu-id="c70bc-143">Specifies a description of the module.</span></span>

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

### <span data-ttu-id="c70bc-144">-DotNetFrameworkVersion</span><span class="sxs-lookup"><span data-stu-id="c70bc-144">-DotNetFrameworkVersion</span></span>

<span data-ttu-id="c70bc-145">Anger den lägsta version av Microsoft .NET Framework som modulen kräver.</span><span class="sxs-lookup"><span data-stu-id="c70bc-145">Specifies the minimum version of the Microsoft .NET Framework that the module requires.</span></span>

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

### <span data-ttu-id="c70bc-146">-DscResourcesToExport</span><span class="sxs-lookup"><span data-stu-id="c70bc-146">-DscResourcesToExport</span></span>

<span data-ttu-id="c70bc-147">Anger de DSC-resurser (Desired State Configuration) som modulen exporterar.</span><span class="sxs-lookup"><span data-stu-id="c70bc-147">Specifies the Desired State Configuration (DSC) resources that the module exports.</span></span> <span data-ttu-id="c70bc-148">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="c70bc-148">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="c70bc-149">-ExternalModuleDependencies</span><span class="sxs-lookup"><span data-stu-id="c70bc-149">-ExternalModuleDependencies</span></span>

<span data-ttu-id="c70bc-150">Anger en matris med beroenden för externa moduler.</span><span class="sxs-lookup"><span data-stu-id="c70bc-150">Specifies an array of external module dependencies.</span></span>

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

### <span data-ttu-id="c70bc-151">– FileList</span><span class="sxs-lookup"><span data-stu-id="c70bc-151">-FileList</span></span>

<span data-ttu-id="c70bc-152">Anger alla objekt som ingår i modulen.</span><span class="sxs-lookup"><span data-stu-id="c70bc-152">Specifies all items that are included in the module.</span></span>

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

### <span data-ttu-id="c70bc-153">-FormatsToProcess</span><span class="sxs-lookup"><span data-stu-id="c70bc-153">-FormatsToProcess</span></span>

<span data-ttu-id="c70bc-154">Anger de formateringsattribut ( `.ps1xml` ) som körs när modulen importeras.</span><span class="sxs-lookup"><span data-stu-id="c70bc-154">Specifies the formatting files (`.ps1xml`) that run when the module is imported.</span></span>

<span data-ttu-id="c70bc-155">När du importerar en modul kör PowerShell `Update-FormatData` cmdleten med de angivna filerna.</span><span class="sxs-lookup"><span data-stu-id="c70bc-155">When you import a module, PowerShell runs the `Update-FormatData` cmdlet with the specified files.</span></span>
<span data-ttu-id="c70bc-156">Eftersom filer som inte är begränsade påverkar formateringen alla sessionstillstånd i sessionen.</span><span class="sxs-lookup"><span data-stu-id="c70bc-156">Because formatting files aren't scoped, they affect all session states in the session.</span></span>

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

### <span data-ttu-id="c70bc-157">-FunctionsToExport</span><span class="sxs-lookup"><span data-stu-id="c70bc-157">-FunctionsToExport</span></span>

<span data-ttu-id="c70bc-158">Anger de funktioner som modulen exporterar.</span><span class="sxs-lookup"><span data-stu-id="c70bc-158">Specifies the functions that the module exports.</span></span> <span data-ttu-id="c70bc-159">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="c70bc-159">Wildcards are permitted.</span></span>

<span data-ttu-id="c70bc-160">Använd den här parametern om du vill begränsa vilka funktioner som exporteras av modulen.</span><span class="sxs-lookup"><span data-stu-id="c70bc-160">Use this parameter to restrict the functions that are exported by the module.</span></span> <span data-ttu-id="c70bc-161">**FunctionsToExport** kan ta bort funktioner från listan över exporterade alias, men det går inte att lägga till funktioner i listan.</span><span class="sxs-lookup"><span data-stu-id="c70bc-161">**FunctionsToExport** can remove functions from the list of exported aliases, but it can't add functions to the list.</span></span>

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

### <span data-ttu-id="c70bc-162">-GUID</span><span class="sxs-lookup"><span data-stu-id="c70bc-162">-Guid</span></span>

<span data-ttu-id="c70bc-163">Anger en unik identifierare för modulen.</span><span class="sxs-lookup"><span data-stu-id="c70bc-163">Specifies a unique identifier for the module.</span></span> <span data-ttu-id="c70bc-164">GUID kan användas för att skilja mellan moduler med samma namn.</span><span class="sxs-lookup"><span data-stu-id="c70bc-164">The GUID can be used to distinguish among modules with the same name.</span></span>

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

### <span data-ttu-id="c70bc-165">-HelpInfoUri</span><span class="sxs-lookup"><span data-stu-id="c70bc-165">-HelpInfoUri</span></span>

<span data-ttu-id="c70bc-166">Anger Internet adressen för modulens **HelpInfo XML-** fil.</span><span class="sxs-lookup"><span data-stu-id="c70bc-166">Specifies the internet address of the module's **HelpInfo XML** file.</span></span> <span data-ttu-id="c70bc-167">Ange en Uniform Resource Identifier (URI) som börjar med **http** eller **https**.</span><span class="sxs-lookup"><span data-stu-id="c70bc-167">Enter a Uniform Resource Identifier (URI) that begins with **http** or **https**.</span></span>

<span data-ttu-id="c70bc-168">**XML-filen HelpInfo** stöder den uppdaterbara hjälp funktionen som introducerades i PowerShell version 3,0.</span><span class="sxs-lookup"><span data-stu-id="c70bc-168">The **HelpInfo XML** file supports the Updatable Help feature that was introduced in PowerShell version 3.0.</span></span> <span data-ttu-id="c70bc-169">Den innehåller information om platsen för modulens nedladdnings bara hjälpfiler och versions numren för de senaste hjälpfilerna för varje språk som stöds.</span><span class="sxs-lookup"><span data-stu-id="c70bc-169">It contains information about the location of the module's downloadable help files and the version numbers of the newest help files for each supported locale.</span></span>

<span data-ttu-id="c70bc-170">Information om uppdaterbar hjälp finns [about_Updatable_Help](../Microsoft.PowerShell.Core/About/about_Updatable_Help.md).</span><span class="sxs-lookup"><span data-stu-id="c70bc-170">For information about Updatable Help, see [about_Updatable_Help](../Microsoft.PowerShell.Core/About/about_Updatable_Help.md).</span></span>
<span data-ttu-id="c70bc-171">Information om **XML-HelpInfo** finns i [stöd uppdaterings bar hjälp](/powershell/scripting/developer/module/supporting-updatable-help).</span><span class="sxs-lookup"><span data-stu-id="c70bc-171">For information about the **HelpInfo XML** file, see [Supporting Updatable Help](/powershell/scripting/developer/module/supporting-updatable-help).</span></span>

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

### <span data-ttu-id="c70bc-172">– IconUri</span><span class="sxs-lookup"><span data-stu-id="c70bc-172">-IconUri</span></span>

<span data-ttu-id="c70bc-173">Anger URL-adressen till en ikon för modulen.</span><span class="sxs-lookup"><span data-stu-id="c70bc-173">Specifies the URL of an icon for the module.</span></span> <span data-ttu-id="c70bc-174">Den angivna ikonen visas på Galleri webb sidan för modulen.</span><span class="sxs-lookup"><span data-stu-id="c70bc-174">The specified icon is displayed on the gallery web page for the module.</span></span>

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

### <span data-ttu-id="c70bc-175">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="c70bc-175">-LicenseUri</span></span>

<span data-ttu-id="c70bc-176">Anger URL: en för licens villkoren för modulen.</span><span class="sxs-lookup"><span data-stu-id="c70bc-176">Specifies the URL of licensing terms for the module.</span></span>

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

### <span data-ttu-id="c70bc-177">-ModuleList</span><span class="sxs-lookup"><span data-stu-id="c70bc-177">-ModuleList</span></span>

<span data-ttu-id="c70bc-178">Anger en matris med moduler som ingår i modulen.</span><span class="sxs-lookup"><span data-stu-id="c70bc-178">Specifies an array of modules that are included in the module.</span></span>

<span data-ttu-id="c70bc-179">Ange varje Modulnamn som en sträng eller som en hash-tabell med **Modulnamn** och **ModuleVersion** -nycklar.</span><span class="sxs-lookup"><span data-stu-id="c70bc-179">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="c70bc-180">Hash-tabellen kan också ha en valfri **GUID** -nyckel.</span><span class="sxs-lookup"><span data-stu-id="c70bc-180">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="c70bc-181">Du kan kombinera strängar och hash-tabeller i parametervärdet.</span><span class="sxs-lookup"><span data-stu-id="c70bc-181">You can combine strings and hash tables in the parameter value.</span></span>

<span data-ttu-id="c70bc-182">Den här nyckeln är utformad för att fungera som en modul.</span><span class="sxs-lookup"><span data-stu-id="c70bc-182">This key is designed to act as a module inventory.</span></span> <span data-ttu-id="c70bc-183">Modulerna som anges i värdet för den här nyckeln bearbetas inte automatiskt.</span><span class="sxs-lookup"><span data-stu-id="c70bc-183">The modules that are listed in the value of this key aren't automatically processed.</span></span>

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

### <span data-ttu-id="c70bc-184">– ModuleVersion</span><span class="sxs-lookup"><span data-stu-id="c70bc-184">-ModuleVersion</span></span>

<span data-ttu-id="c70bc-185">Anger versionen för modulen.</span><span class="sxs-lookup"><span data-stu-id="c70bc-185">Specifies the version of the module.</span></span>

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

### <span data-ttu-id="c70bc-186">-NestedModules</span><span class="sxs-lookup"><span data-stu-id="c70bc-186">-NestedModules</span></span>

<span data-ttu-id="c70bc-187">Anger skript moduler ( `.psm1` ) och binära moduler ( `.dll` ) som importeras till modulens sessionstillstånd.</span><span class="sxs-lookup"><span data-stu-id="c70bc-187">Specifies script modules (`.psm1`) and binary modules (`.dll`) that are imported into the module's session state.</span></span> <span data-ttu-id="c70bc-188">Filerna i **NestedModules** -nyckeln körs i den ordning som de är listade i värdet.</span><span class="sxs-lookup"><span data-stu-id="c70bc-188">The files in the **NestedModules** key run in the order in which they're listed in the value.</span></span>

<span data-ttu-id="c70bc-189">Ange varje Modulnamn som en sträng eller som en hash-tabell med **Modulnamn** och **ModuleVersion** -nycklar.</span><span class="sxs-lookup"><span data-stu-id="c70bc-189">Enter each module name as a string or as a hash table with **ModuleName** and **ModuleVersion** keys.</span></span> <span data-ttu-id="c70bc-190">Hash-tabellen kan också ha en valfri **GUID** -nyckel.</span><span class="sxs-lookup"><span data-stu-id="c70bc-190">The hash table can also have an optional **GUID** key.</span></span> <span data-ttu-id="c70bc-191">Du kan kombinera strängar och hash-tabeller i parametervärdet.</span><span class="sxs-lookup"><span data-stu-id="c70bc-191">You can combine strings and hash tables in the parameter value.</span></span>

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

### <span data-ttu-id="c70bc-192">-PackageManagementProviders</span><span class="sxs-lookup"><span data-stu-id="c70bc-192">-PackageManagementProviders</span></span>

<span data-ttu-id="c70bc-193">Anger en matris med paket hanterings leverantörer.</span><span class="sxs-lookup"><span data-stu-id="c70bc-193">Specifies an array of package management providers.</span></span>

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

### <span data-ttu-id="c70bc-194">– PassThru</span><span class="sxs-lookup"><span data-stu-id="c70bc-194">-PassThru</span></span>

<span data-ttu-id="c70bc-195">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="c70bc-195">Returns an object representing the item with which you're working.</span></span> <span data-ttu-id="c70bc-196">Som standard `Update-ModuleManifest` genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="c70bc-196">By default, `Update-ModuleManifest` doesn't generate any output.</span></span>

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

### <span data-ttu-id="c70bc-197">-Path</span><span class="sxs-lookup"><span data-stu-id="c70bc-197">-Path</span></span>

<span data-ttu-id="c70bc-198">Anger sökvägen och fil namnet för modulens manifest.</span><span class="sxs-lookup"><span data-stu-id="c70bc-198">Specifies the path and file name of the module manifest.</span></span> <span data-ttu-id="c70bc-199">Ange en sökväg och ett fil namn med ett `.psd1` fil namns tillägg, till exempel `$PSHOME\Modules\MyModule\MyModule.psd1` .</span><span class="sxs-lookup"><span data-stu-id="c70bc-199">Enter a path and file name with a `.psd1` file name extension, such as `$PSHOME\Modules\MyModule\MyModule.psd1`.</span></span>

<span data-ttu-id="c70bc-200">Om du anger sökvägen till en befintlig fil `Update-ModuleManifest` ersätts filen utan varning om inte filen har attributet skrivskyddad.</span><span class="sxs-lookup"><span data-stu-id="c70bc-200">If you specify the path to an existing file, `Update-ModuleManifest` replaces the file without warning unless the file has the read-only attribute.</span></span>

<span data-ttu-id="c70bc-201">Manifestet ska finnas i modulens katalog och manifest filens namn ska vara samma som modulens katalog namn, men med ett `.psd1` tillägg.</span><span class="sxs-lookup"><span data-stu-id="c70bc-201">The manifest should be located in the module's directory, and the manifest file name should be the same as the module directory name, but with a `.psd1` extension.</span></span>

<span data-ttu-id="c70bc-202">Du kan inte använda variabler, t `$PSHOME` . ex. eller `$HOME` , som svar på en prompt för värdet för en **Sök vägs** parameter.</span><span class="sxs-lookup"><span data-stu-id="c70bc-202">You can't use variables, such as `$PSHOME` or `$HOME`, in response to a prompt for a **Path** parameter value.</span></span> <span data-ttu-id="c70bc-203">Om du vill använda en variabel inkluderar du parametern **Path** i kommandot.</span><span class="sxs-lookup"><span data-stu-id="c70bc-203">To use a variable, include the **Path** parameter in the command.</span></span>

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

### <span data-ttu-id="c70bc-204">-PowerShellHostName</span><span class="sxs-lookup"><span data-stu-id="c70bc-204">-PowerShellHostName</span></span>

<span data-ttu-id="c70bc-205">Anger namnet på PowerShell-värdservern som modulen kräver.</span><span class="sxs-lookup"><span data-stu-id="c70bc-205">Specifies the name of the PowerShell host program that the module requires.</span></span> <span data-ttu-id="c70bc-206">Ange namnet på värd programmet, till exempel PowerShell ISE värd eller ConsoleHost.</span><span class="sxs-lookup"><span data-stu-id="c70bc-206">Enter the name of the host program, such as PowerShell ISE Host or ConsoleHost.</span></span> <span data-ttu-id="c70bc-207">Jokertecken är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="c70bc-207">Wildcards aren't permitted.</span></span>

<span data-ttu-id="c70bc-208">Om du vill hitta namnet på ett värd program skriver du i programmet `$Host.Name` .</span><span class="sxs-lookup"><span data-stu-id="c70bc-208">To find the name of a host program, in the program, type `$Host.Name`.</span></span>

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

### <span data-ttu-id="c70bc-209">-PowerShellHostVersion</span><span class="sxs-lookup"><span data-stu-id="c70bc-209">-PowerShellHostVersion</span></span>

<span data-ttu-id="c70bc-210">Anger den lägsta versionen av PowerShell-värd programmet som fungerar med modulen.</span><span class="sxs-lookup"><span data-stu-id="c70bc-210">Specifies the minimum version of the PowerShell host program that works with the module.</span></span> <span data-ttu-id="c70bc-211">Ange ett versions nummer, till exempel 1,1.</span><span class="sxs-lookup"><span data-stu-id="c70bc-211">Enter a version number, such as 1.1.</span></span>

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

### <span data-ttu-id="c70bc-212">– PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="c70bc-212">-PowerShellVersion</span></span>

<span data-ttu-id="c70bc-213">Anger den lägsta version av PowerShell som kommer att fungera med den här modulen.</span><span class="sxs-lookup"><span data-stu-id="c70bc-213">Specifies the minimum version of PowerShell that will work with this module.</span></span> <span data-ttu-id="c70bc-214">Du kan till exempel ange 3,0, 4,0 eller 5,0 som värde för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="c70bc-214">For example, you can specify 3.0, 4.0, or 5.0 as the value of this parameter.</span></span>

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

### <span data-ttu-id="c70bc-215">-För hands version</span><span class="sxs-lookup"><span data-stu-id="c70bc-215">-Prerelease</span></span>

<span data-ttu-id="c70bc-216">Anger att modulen är för hands version.</span><span class="sxs-lookup"><span data-stu-id="c70bc-216">Indicates the module is prerelease.</span></span>

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

### <span data-ttu-id="c70bc-217">-PrivateData</span><span class="sxs-lookup"><span data-stu-id="c70bc-217">-PrivateData</span></span>

<span data-ttu-id="c70bc-218">Anger data som skickas till modulen när den importeras.</span><span class="sxs-lookup"><span data-stu-id="c70bc-218">Specifies data that is passed to the module when it's imported.</span></span>

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

### <span data-ttu-id="c70bc-219">-ProcessorArchitecture</span><span class="sxs-lookup"><span data-stu-id="c70bc-219">-ProcessorArchitecture</span></span>

<span data-ttu-id="c70bc-220">Anger den processor arkitektur som modulen kräver.</span><span class="sxs-lookup"><span data-stu-id="c70bc-220">Specifies the processor architecture that the module requires.</span></span>

<span data-ttu-id="c70bc-221">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="c70bc-221">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="c70bc-222">Amd64</span><span class="sxs-lookup"><span data-stu-id="c70bc-222">Amd64</span></span>
- <span data-ttu-id="c70bc-223">Koppling</span><span class="sxs-lookup"><span data-stu-id="c70bc-223">Arm</span></span>
- <span data-ttu-id="c70bc-224">IA64</span><span class="sxs-lookup"><span data-stu-id="c70bc-224">IA64</span></span>
- <span data-ttu-id="c70bc-225">MSIL</span><span class="sxs-lookup"><span data-stu-id="c70bc-225">MSIL</span></span>
- <span data-ttu-id="c70bc-226">Ingen (okänd eller ospecificerad)</span><span class="sxs-lookup"><span data-stu-id="c70bc-226">None (unknown or unspecified)</span></span>
- <span data-ttu-id="c70bc-227">X86</span><span class="sxs-lookup"><span data-stu-id="c70bc-227">X86</span></span>

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

### <span data-ttu-id="c70bc-228">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="c70bc-228">-ProjectUri</span></span>

<span data-ttu-id="c70bc-229">Anger webb adressen till en webb sida om projektet.</span><span class="sxs-lookup"><span data-stu-id="c70bc-229">Specifies the URL of a web page about this project.</span></span>

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

### <span data-ttu-id="c70bc-230">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="c70bc-230">-ReleaseNotes</span></span>

<span data-ttu-id="c70bc-231">Anger en sträng mat ris som innehåller viktig information eller kommentarer som du vill ska vara tillgängliga för den här versionen av skriptet.</span><span class="sxs-lookup"><span data-stu-id="c70bc-231">Specifies a string array that contains release notes or comments that you want available for this version of the script.</span></span>

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

### <span data-ttu-id="c70bc-232">-RequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="c70bc-232">-RequireLicenseAcceptance</span></span>

<span data-ttu-id="c70bc-233">Anger att licens godkännande krävs för modulen.</span><span class="sxs-lookup"><span data-stu-id="c70bc-233">Specifies that a license acceptance is required for the module.</span></span>

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

### <span data-ttu-id="c70bc-234">-RequiredAssemblies</span><span class="sxs-lookup"><span data-stu-id="c70bc-234">-RequiredAssemblies</span></span>

<span data-ttu-id="c70bc-235">Anger de Assembly ( `.dll` )-filer som modulen kräver.</span><span class="sxs-lookup"><span data-stu-id="c70bc-235">Specifies the assembly (`.dll`) files that the module requires.</span></span> <span data-ttu-id="c70bc-236">Ange sammansättnings fil namnen.</span><span class="sxs-lookup"><span data-stu-id="c70bc-236">Enter the assembly file names.</span></span>
<span data-ttu-id="c70bc-237">PowerShell läser in de angivna sammansättningarna innan du uppdaterar typer eller format, importerar kapslade moduler eller importerar filen som anges i värdet för nyckeln **RootModule** .</span><span class="sxs-lookup"><span data-stu-id="c70bc-237">PowerShell loads the specified assemblies before updating types or formats, importing nested modules, or importing the module file that is specified in the value of the **RootModule** key.</span></span>

<span data-ttu-id="c70bc-238">Använd den här parametern för att ange alla sammansättningar som modulen kräver, inklusive sammansättningar som måste läsas in för att uppdatera all formatering eller skriva filer som listas i **FormatsToProcess** -eller **TypesToProcess** -nycklarna, även om dessa sammansättningar också visas som binära moduler i **NestedModules** -nyckeln.</span><span class="sxs-lookup"><span data-stu-id="c70bc-238">Use this parameter to specify all the assemblies that the module requires, including assemblies that must be loaded to update any formatting or type files that are listed in the **FormatsToProcess** or **TypesToProcess** keys, even if those assemblies are also listed as binary modules in the **NestedModules** key.</span></span>

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

### <span data-ttu-id="c70bc-239">-RequiredModules</span><span class="sxs-lookup"><span data-stu-id="c70bc-239">-RequiredModules</span></span>

<span data-ttu-id="c70bc-240">Anger moduler som måste vara i det globala sessionstillståndet.</span><span class="sxs-lookup"><span data-stu-id="c70bc-240">Specifies modules that must be in the global session state.</span></span> <span data-ttu-id="c70bc-241">Om de moduler som krävs inte är i det globala sessionstillståndet importeras de av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c70bc-241">If the required modules aren't in the global session state, PowerShell imports them.</span></span> <span data-ttu-id="c70bc-242">Om de moduler som krävs inte är tillgängliga, `Import-Module` Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="c70bc-242">If the required modules aren't available, the `Import-Module` command fails.</span></span>

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

### <span data-ttu-id="c70bc-243">-RootModule</span><span class="sxs-lookup"><span data-stu-id="c70bc-243">-RootModule</span></span>

<span data-ttu-id="c70bc-244">Anger modulens primära eller rot fil.</span><span class="sxs-lookup"><span data-stu-id="c70bc-244">Specifies the primary or root file of the module.</span></span> <span data-ttu-id="c70bc-245">Ange fil namnet för ett skript ( `.ps1` ), en skriptbaserad modul ( `.psm1` ), ett modul manifest ( `.psd1` ), en sammansättning ( `.dll` ), en XML-fil () för cmdlet-definition ( `.cdxml` ) eller ett arbets flöde ( `.xaml` ).</span><span class="sxs-lookup"><span data-stu-id="c70bc-245">Enter the file name of a script (`.ps1`), a script module (`.psm1`), a module manifest (`.psd1`), an assembly (`.dll`), a cmdlet definition XML file (`.cdxml`), or a workflow (`.xaml`).</span></span> <span data-ttu-id="c70bc-246">När modulen importeras importeras medlemmar som exporteras från rot-modul filen till anroparens sessionstillstånd.</span><span class="sxs-lookup"><span data-stu-id="c70bc-246">When the module is imported, the members that are exported from the root module file are imported into the caller's session state.</span></span>

<span data-ttu-id="c70bc-247">Om en modul har en manifest fil och ingen rot fil har angetts i **RootModule** -nyckeln blir manifestet den primära filen för modulen.</span><span class="sxs-lookup"><span data-stu-id="c70bc-247">If a module has a manifest file and no root file has been specified in the **RootModule** key, the manifest becomes the primary file for the module.</span></span> <span data-ttu-id="c70bc-248">Och är modulen en manifest-modul (ModuleType = manifest).</span><span class="sxs-lookup"><span data-stu-id="c70bc-248">And, the module becomes a manifest module (ModuleType = Manifest).</span></span>

<span data-ttu-id="c70bc-249">För att exportera medlemmar från `.psm1` eller `.dll` filer i en modul som har ett manifest, måste namnen på filerna anges i värdena för **RootModule** -eller **NestedModules** -nycklarna i manifestet.</span><span class="sxs-lookup"><span data-stu-id="c70bc-249">To export members from `.psm1` or `.dll` files in a module that has a manifest, the names of those files must be specified in the values of the **RootModule** or **NestedModules** keys in the manifest.</span></span> <span data-ttu-id="c70bc-250">Annars exporteras inte deras medlemmar.</span><span class="sxs-lookup"><span data-stu-id="c70bc-250">Otherwise, their members aren't exported.</span></span>

<span data-ttu-id="c70bc-251">I PowerShell 2,0 kallades den här nyckeln för **ModuleToProcess**.</span><span class="sxs-lookup"><span data-stu-id="c70bc-251">In PowerShell 2.0, this key was called **ModuleToProcess**.</span></span>

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

### <span data-ttu-id="c70bc-252">-ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="c70bc-252">-ScriptsToProcess</span></span>

<span data-ttu-id="c70bc-253">Anger skript ( `.ps1` )-filer som körs i anroparens sessionstillstånd när modulen importeras.</span><span class="sxs-lookup"><span data-stu-id="c70bc-253">Specifies script (`.ps1`) files that run in the caller's session state when the module is imported.</span></span>
<span data-ttu-id="c70bc-254">Du kan använda dessa skript för att förbereda en miljö, precis som du kan använda ett inloggnings skript.</span><span class="sxs-lookup"><span data-stu-id="c70bc-254">You can use these scripts to prepare an environment, just as you might use a login script.</span></span>

<span data-ttu-id="c70bc-255">Använd nyckeln **NestedModules** för att ange skript som körs i modulens sessionstillstånd.</span><span class="sxs-lookup"><span data-stu-id="c70bc-255">To specify scripts that run in the module's session state, use the **NestedModules** key.</span></span>

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

### <span data-ttu-id="c70bc-256">– Taggar</span><span class="sxs-lookup"><span data-stu-id="c70bc-256">-Tags</span></span>

<span data-ttu-id="c70bc-257">Anger en matris med taggar.</span><span class="sxs-lookup"><span data-stu-id="c70bc-257">Specifies an array of tags.</span></span>

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

### <span data-ttu-id="c70bc-258">-TypesToProcess</span><span class="sxs-lookup"><span data-stu-id="c70bc-258">-TypesToProcess</span></span>

<span data-ttu-id="c70bc-259">Anger de typ filer ( `.ps1xml` ) som körs när modulen importeras.</span><span class="sxs-lookup"><span data-stu-id="c70bc-259">Specifies the type files (`.ps1xml`) that run when the module is imported.</span></span>

<span data-ttu-id="c70bc-260">När du importerar modulen kör PowerShell `Update-TypeData` cmdleten med de angivna filerna.</span><span class="sxs-lookup"><span data-stu-id="c70bc-260">When you import the module, PowerShell runs the `Update-TypeData` cmdlet with the specified files.</span></span>
<span data-ttu-id="c70bc-261">Eftersom filtypen inte är begränsad, påverkar de alla sessionstillstånd i sessionen.</span><span class="sxs-lookup"><span data-stu-id="c70bc-261">Because type files aren't scoped, they affect all session states in the session.</span></span>

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

### <span data-ttu-id="c70bc-262">-VariablesToExport</span><span class="sxs-lookup"><span data-stu-id="c70bc-262">-VariablesToExport</span></span>

<span data-ttu-id="c70bc-263">Anger de variabler som modulen exporterar.</span><span class="sxs-lookup"><span data-stu-id="c70bc-263">Specifies the variables that the module exports.</span></span> <span data-ttu-id="c70bc-264">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="c70bc-264">Wildcards are permitted.</span></span>

<span data-ttu-id="c70bc-265">Använd den här parametern om du vill begränsa de variabler som exporteras av modulen.</span><span class="sxs-lookup"><span data-stu-id="c70bc-265">Use this parameter to restrict the variables that are exported by the module.</span></span> <span data-ttu-id="c70bc-266">**VariablesToExport** kan ta bort variabler från listan över exporterade variabler, men det går inte att lägga till variabler i listan.</span><span class="sxs-lookup"><span data-stu-id="c70bc-266">**VariablesToExport** can remove variables from the list of exported variables, but it can't add variables to the list.</span></span>

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

### <span data-ttu-id="c70bc-267">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c70bc-267">-WhatIf</span></span>

<span data-ttu-id="c70bc-268">Visar vad som händer om `Update-ModuleManifest` körs.</span><span class="sxs-lookup"><span data-stu-id="c70bc-268">Shows what would happen if `Update-ModuleManifest` runs.</span></span> <span data-ttu-id="c70bc-269">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="c70bc-269">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="c70bc-270">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c70bc-270">CommonParameters</span></span>

<span data-ttu-id="c70bc-271">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c70bc-271">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c70bc-272">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c70bc-272">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c70bc-273">INDATA</span><span class="sxs-lookup"><span data-stu-id="c70bc-273">INPUTS</span></span>

### <span data-ttu-id="c70bc-274">System. String</span><span class="sxs-lookup"><span data-stu-id="c70bc-274">System.String</span></span>

## <span data-ttu-id="c70bc-275">UTDATA</span><span class="sxs-lookup"><span data-stu-id="c70bc-275">OUTPUTS</span></span>

### <span data-ttu-id="c70bc-276">System. Object</span><span class="sxs-lookup"><span data-stu-id="c70bc-276">System.Object</span></span>

## <span data-ttu-id="c70bc-277">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="c70bc-277">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c70bc-278">Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1.</span><span class="sxs-lookup"><span data-stu-id="c70bc-278">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="c70bc-279">Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="c70bc-279">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="c70bc-280">Använd följande kommando för att se till att du använder TLS 1,2:</span><span class="sxs-lookup"><span data-stu-id="c70bc-280">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="c70bc-281">Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="c70bc-281">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="c70bc-282">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="c70bc-282">RELATED LINKS</span></span>
