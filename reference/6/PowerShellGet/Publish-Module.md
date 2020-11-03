---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 10/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/publish-module?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Publish-Module
ms.openlocfilehash: dd7721fbf482bca78823d9bad5b8f40f76b7d8bf
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266516"
---
# <span data-ttu-id="c6d69-103">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="c6d69-103">Publish-Module</span></span>

## <span data-ttu-id="c6d69-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="c6d69-104">SYNOPSIS</span></span>
<span data-ttu-id="c6d69-105">Publicerar en angiven modul från den lokala datorn till ett onlinegalleri.</span><span class="sxs-lookup"><span data-stu-id="c6d69-105">Publishes a specified module from the local computer to an online gallery.</span></span>

## <span data-ttu-id="c6d69-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c6d69-106">SYNTAX</span></span>

### <span data-ttu-id="c6d69-107">ModuleNameParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="c6d69-107">ModuleNameParameterSet (Default)</span></span>

```
Publish-Module -Name <String> [-RequiredVersion <String>] [-NuGetApiKey <String>]
 [-Repository <String>] [-Credential <PSCredential>] [-FormatVersion <Version>]
 [-ReleaseNotes <String[]>] [-Tags <String[]>] [-LicenseUri <Uri>] [-IconUri <Uri>]
 [-ProjectUri <Uri>] [-Exclude <String[]>] [-Force] [-AllowPrerelease] [-SkipAutomaticTags]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="c6d69-108">ModulePathParameterSet</span><span class="sxs-lookup"><span data-stu-id="c6d69-108">ModulePathParameterSet</span></span>

```
Publish-Module -Path <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-FormatVersion <Version>] [-ReleaseNotes <String[]>]
 [-Tags <String[]>] [-LicenseUri <Uri>] [-IconUri <Uri>] [-ProjectUri <Uri>] [-Force]
 [-SkipAutomaticTags] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="c6d69-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="c6d69-109">DESCRIPTION</span></span>

<span data-ttu-id="c6d69-110">`Publish-Module`Cmdleten publicerar en modul till ett NuGet-baserat galleri med hjälp av en API-nyckel som lagras som en del av en användar profil i galleriet.</span><span class="sxs-lookup"><span data-stu-id="c6d69-110">The `Publish-Module` cmdlet publishes a module to an online NuGet-based gallery by using an API key, stored as part of a user's profile in the gallery.</span></span> <span data-ttu-id="c6d69-111">Du kan ange vilken modul som ska publiceras antingen av modulens namn eller efter sökvägen till mappen som innehåller modulen.</span><span class="sxs-lookup"><span data-stu-id="c6d69-111">You can specify the module to publish either by the module's name, or by the path to the folder containing the module.</span></span>

<span data-ttu-id="c6d69-112">När du anger en modul efter namn, `Publish-Module` publicerar den första modulen som skulle hittas genom att köra `Get-Module -ListAvailable <Name>` .</span><span class="sxs-lookup"><span data-stu-id="c6d69-112">When you specify a module by name, `Publish-Module` publishes the first module that would be found by running `Get-Module -ListAvailable <Name>`.</span></span> <span data-ttu-id="c6d69-113">Om du anger en lägsta version av en modul som ska publiceras, `Publish-Module` publicerar den första modulen med en version som är större än eller lika med den lägsta version som du har angett.</span><span class="sxs-lookup"><span data-stu-id="c6d69-113">If you specify a minimum version of a module to publish, `Publish-Module` publishes the first module with a version that is greater than or equal to the minimum version that you have specified.</span></span>

<span data-ttu-id="c6d69-114">Att publicera en modul kräver metadata som visas på Galleri sidan för modulen.</span><span class="sxs-lookup"><span data-stu-id="c6d69-114">Publishing a module requires metadata that is displayed on the gallery page for the module.</span></span> <span data-ttu-id="c6d69-115">Obligatoriska metadata innehåller modulens namn, version, beskrivning och författare.</span><span class="sxs-lookup"><span data-stu-id="c6d69-115">Required metadata includes the module name, version, description, and author.</span></span> <span data-ttu-id="c6d69-116">Även om de flesta metadata tas från modulens manifest, måste vissa metadata anges i `Publish-Module` parametrar, till exempel **tag** , **ReleaseNote** , **IconUri** , **ProjectUri** och **LicenseUri** , eftersom dessa parametrar matchar fält i ett NuGet-baserat Galleri.</span><span class="sxs-lookup"><span data-stu-id="c6d69-116">Although most metadata is taken from the module manifest, some metadata must be specified in `Publish-Module` parameters, such as **Tag** , **ReleaseNote** , **IconUri** , **ProjectUri** , and **LicenseUri** , because these parameters match fields in a NuGet-based gallery.</span></span>

## <span data-ttu-id="c6d69-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="c6d69-117">EXAMPLES</span></span>

### <span data-ttu-id="c6d69-118">Exempel 1: publicera en modul</span><span class="sxs-lookup"><span data-stu-id="c6d69-118">Example 1: Publish a module</span></span>

<span data-ttu-id="c6d69-119">I det här exemplet publiceras MyDscModule i online-galleriet med hjälp av API-nyckeln för att ange module-kontots onlinegalleri.</span><span class="sxs-lookup"><span data-stu-id="c6d69-119">In this example, MyDscModule is published to the online gallery by using the API key to indicate the module owner's online gallery account.</span></span> <span data-ttu-id="c6d69-120">Om MyDscModule inte är en giltig manifest-modul som anger namn, version, beskrivning och författare inträffar ett fel.</span><span class="sxs-lookup"><span data-stu-id="c6d69-120">If MyDscModule is not a valid manifest module that specifies a name, version, description, and author, an error occurs.</span></span>

```powershell
Publish-Module -Name "MyDscModule" -NuGetApiKey "11e4b435-6cb4-4bf7-8611-5162ed75eb73"
```

### <span data-ttu-id="c6d69-121">Exempel 2: publicera en modul med metadata för galleriet</span><span class="sxs-lookup"><span data-stu-id="c6d69-121">Example 2: Publish a module with gallery metadata</span></span>

<span data-ttu-id="c6d69-122">I det här exemplet publiceras MyDscModule i online-galleriet med hjälp av API-nyckeln för att ange modulens ägares Galleri konto.</span><span class="sxs-lookup"><span data-stu-id="c6d69-122">In this example, MyDscModule is published to the online gallery by using the API key to indicate the module owner's gallery account.</span></span> <span data-ttu-id="c6d69-123">De ytterligare metadata som anges visas på webb sidan för modulen i galleriet.</span><span class="sxs-lookup"><span data-stu-id="c6d69-123">The additional metadata provided is displayed on the webpage for the module in the gallery.</span></span> <span data-ttu-id="c6d69-124">Ägaren lägger till två söktaggar för modulen, relaterad den till Active Directory. en kort versions anteckning har lagts till.</span><span class="sxs-lookup"><span data-stu-id="c6d69-124">The owner adds two search tags for the module, relating it to Active Directory; a brief release note is added.</span></span> <span data-ttu-id="c6d69-125">Om MyDscModule inte är en giltig manifest-modul som anger namn, version, beskrivning och författare inträffar ett fel.</span><span class="sxs-lookup"><span data-stu-id="c6d69-125">If MyDscModule is not a valid manifest module that specifies a name, version, description, and author, an error occurs.</span></span>

```powershell
Publish-Module -Name "MyDscModule" -NuGetApiKey "11e4b435-6cb4-4bf7-8611-5162ed75eb73" -LicenseUri "http://contoso.com/license" -Tag "Active Directory","DSC" -ReleaseNote "Updated the ActiveDirectory DSC Resources to support adding users."
```

## <span data-ttu-id="c6d69-126">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="c6d69-126">PARAMETERS</span></span>

### <span data-ttu-id="c6d69-127">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="c6d69-127">-AllowPrerelease</span></span>

<span data-ttu-id="c6d69-128">Gör det möjligt att publicera moduler som är markerade som för hands versioner.</span><span class="sxs-lookup"><span data-stu-id="c6d69-128">Allows modules marked as prerelease to be published.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c6d69-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="c6d69-129">-Confirm</span></span>

<span data-ttu-id="c6d69-130">Du uppmanas att bekräfta innan du kör `Publish-Module` .</span><span class="sxs-lookup"><span data-stu-id="c6d69-130">Prompts you for confirmation before running the `Publish-Module`.</span></span>

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

### <span data-ttu-id="c6d69-131">-Credential</span><span class="sxs-lookup"><span data-stu-id="c6d69-131">-Credential</span></span>

<span data-ttu-id="c6d69-132">Anger ett användar konto som har behörighet att publicera en modul för en angiven paket leverantör eller källa.</span><span class="sxs-lookup"><span data-stu-id="c6d69-132">Specifies a user account that has rights to publish a module for a specified package provider or source.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c6d69-133">-Undanta</span><span class="sxs-lookup"><span data-stu-id="c6d69-133">-Exclude</span></span>

<span data-ttu-id="c6d69-134">Definierar filer som ska undantas från den publicerade modulen.</span><span class="sxs-lookup"><span data-stu-id="c6d69-134">Defines files to exclude from the published module.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c6d69-135">-Force</span><span class="sxs-lookup"><span data-stu-id="c6d69-135">-Force</span></span>

<span data-ttu-id="c6d69-136">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="c6d69-136">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="c6d69-137">-FormatVersion</span><span class="sxs-lookup"><span data-stu-id="c6d69-137">-FormatVersion</span></span>

<span data-ttu-id="c6d69-138">Accepterar endast giltiga värden som anges av attributet **ValidateSet** .</span><span class="sxs-lookup"><span data-stu-id="c6d69-138">Accepts only valid values specified by the **ValidateSet** attribute.</span></span>

<span data-ttu-id="c6d69-139">Mer information finns i [ValidateSet-attributets deklaration](/powershell/scripting/developer/cmdlet/validateset-attribute-declaration) och [ValidateSetAttribute](/dotnet/api/system.management.automation.validatesetattribute).</span><span class="sxs-lookup"><span data-stu-id="c6d69-139">For more information, see [ValidateSet Attribute Declaration](/powershell/scripting/developer/cmdlet/validateset-attribute-declaration) and [ValidateSetAttribute](/dotnet/api/system.management.automation.validatesetattribute).</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:
Accepted values: 2.0

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c6d69-140">– IconUri</span><span class="sxs-lookup"><span data-stu-id="c6d69-140">-IconUri</span></span>

<span data-ttu-id="c6d69-141">Anger URL-adressen till en ikon för modulen.</span><span class="sxs-lookup"><span data-stu-id="c6d69-141">Specifies the URL of an icon for the module.</span></span> <span data-ttu-id="c6d69-142">Den angivna ikonen visas på Galleri webb sidan för modulen.</span><span class="sxs-lookup"><span data-stu-id="c6d69-142">The specified icon is displayed on the gallery webpage for the module.</span></span>

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

### <span data-ttu-id="c6d69-143">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="c6d69-143">-LicenseUri</span></span>

<span data-ttu-id="c6d69-144">Anger webb adressen till licens villkoren för den modul som du vill publicera.</span><span class="sxs-lookup"><span data-stu-id="c6d69-144">Specifies the URL of licensing terms for the module you want to publish.</span></span>

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

### <span data-ttu-id="c6d69-145">-Name</span><span class="sxs-lookup"><span data-stu-id="c6d69-145">-Name</span></span>

<span data-ttu-id="c6d69-146">Anger namnet på den modul som du vill publicera.</span><span class="sxs-lookup"><span data-stu-id="c6d69-146">Specifies the name of the module that you want to publish.</span></span> <span data-ttu-id="c6d69-147">`Publish-Module` söker efter det angivna modulnamnet i `$Env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="c6d69-147">`Publish-Module` searches for the specified module name in `$Env:PSModulePath`.</span></span>

```yaml
Type: System.String
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c6d69-148">-NuGetApiKey</span><span class="sxs-lookup"><span data-stu-id="c6d69-148">-NuGetApiKey</span></span>

<span data-ttu-id="c6d69-149">Anger den API-nyckel som du vill använda för att publicera en modul i onlinegalleri.</span><span class="sxs-lookup"><span data-stu-id="c6d69-149">Specifies the API key that you want to use to publish a module to the online gallery.</span></span> <span data-ttu-id="c6d69-150">API-nyckeln är en del av din profil i Onlinegalleri, och du hittar den på sidan användar konto i galleriet.</span><span class="sxs-lookup"><span data-stu-id="c6d69-150">The API key is part of your profile in the online gallery, and can be found on your user account page in the gallery.</span></span> <span data-ttu-id="c6d69-151">API-nyckeln är NuGet funktioner.</span><span class="sxs-lookup"><span data-stu-id="c6d69-151">The API key is NuGet-specific functionality.</span></span>

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

### <span data-ttu-id="c6d69-152">-Path</span><span class="sxs-lookup"><span data-stu-id="c6d69-152">-Path</span></span>

<span data-ttu-id="c6d69-153">Anger sökvägen till den modul som du vill publicera.</span><span class="sxs-lookup"><span data-stu-id="c6d69-153">Specifies the path to the module that you want to publish.</span></span> <span data-ttu-id="c6d69-154">Den här parametern godkänner sökvägen till mappen som innehåller modulen.</span><span class="sxs-lookup"><span data-stu-id="c6d69-154">This parameter accepts the path to the folder that contains the module.</span></span>

```yaml
Type: System.String
Parameter Sets: ModulePathParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="c6d69-155">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="c6d69-155">-ProjectUri</span></span>

<span data-ttu-id="c6d69-156">Anger webb adressen till en webb sida om projektet.</span><span class="sxs-lookup"><span data-stu-id="c6d69-156">Specifies the URL of a webpage about this project.</span></span>

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

### <span data-ttu-id="c6d69-157">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="c6d69-157">-ReleaseNotes</span></span>

<span data-ttu-id="c6d69-158">Anger en sträng som innehåller viktig information eller kommentarer som du vill ska vara tillgängliga för användare av den här versionen av modulen.</span><span class="sxs-lookup"><span data-stu-id="c6d69-158">Specifies a string containing release notes or comments that you want to be available to users of this version of the module.</span></span>

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

### <span data-ttu-id="c6d69-159">– Databas</span><span class="sxs-lookup"><span data-stu-id="c6d69-159">-Repository</span></span>

<span data-ttu-id="c6d69-160">Anger det egna namnet på en lagrings plats som har registrerats genom att köra `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="c6d69-160">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span> <span data-ttu-id="c6d69-161">Lagrings platsen måste ha en **PublishLocation** , vilket är en giltig NUGET-URI.</span><span class="sxs-lookup"><span data-stu-id="c6d69-161">The repository must have a **PublishLocation** , which is a valid NuGet URI.</span></span>
<span data-ttu-id="c6d69-162">**PublishLocation** kan anges genom att köra `Set-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="c6d69-162">The **PublishLocation** can be set by running `Set-PSRepository`.</span></span>

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

### <span data-ttu-id="c6d69-163">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="c6d69-163">-RequiredVersion</span></span>

<span data-ttu-id="c6d69-164">Anger den exakta versionen av en enda modul som ska publiceras.</span><span class="sxs-lookup"><span data-stu-id="c6d69-164">Specifies the exact version of a single module to publish.</span></span>

```yaml
Type: System.String
Parameter Sets: ModuleNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c6d69-165">-SkipAutomaticTags</span><span class="sxs-lookup"><span data-stu-id="c6d69-165">-SkipAutomaticTags</span></span>

<span data-ttu-id="c6d69-166">Tar bort kommandon och resurser från att inkluderas som taggar.</span><span class="sxs-lookup"><span data-stu-id="c6d69-166">Removes commands and resources from being included as tags.</span></span> <span data-ttu-id="c6d69-167">Hoppar över automatiskt tillägg av taggar i en modul.</span><span class="sxs-lookup"><span data-stu-id="c6d69-167">Skips automatically adding tags to a module.</span></span>

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

### <span data-ttu-id="c6d69-168">– Taggar</span><span class="sxs-lookup"><span data-stu-id="c6d69-168">-Tags</span></span>

<span data-ttu-id="c6d69-169">Lägger till en eller flera taggar till den modul som du publicerar.</span><span class="sxs-lookup"><span data-stu-id="c6d69-169">Adds one or more tags to the module that you are publishing.</span></span> <span data-ttu-id="c6d69-170">Exempel taggar är DesiredStateConfiguration, DSC, DSCResourceKit eller PSModule.</span><span class="sxs-lookup"><span data-stu-id="c6d69-170">Example tags include DesiredStateConfiguration, DSC, DSCResourceKit, or PSModule.</span></span> <span data-ttu-id="c6d69-171">Avgränsa flera taggar med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="c6d69-171">Separate multiple tags with commas.</span></span>

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

### <span data-ttu-id="c6d69-172">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="c6d69-172">-WhatIf</span></span>

<span data-ttu-id="c6d69-173">Visar vad som händer om `Publish-Module` körningarna körs.</span><span class="sxs-lookup"><span data-stu-id="c6d69-173">Shows what would happen if the `Publish-Module` runs.</span></span> <span data-ttu-id="c6d69-174">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="c6d69-174">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="c6d69-175">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c6d69-175">CommonParameters</span></span>

<span data-ttu-id="c6d69-176">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c6d69-176">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c6d69-177">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c6d69-177">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c6d69-178">INDATA</span><span class="sxs-lookup"><span data-stu-id="c6d69-178">INPUTS</span></span>

### <span data-ttu-id="c6d69-179">System. String</span><span class="sxs-lookup"><span data-stu-id="c6d69-179">System.String</span></span>

### <span data-ttu-id="c6d69-180">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="c6d69-180">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="c6d69-181">UTDATA</span><span class="sxs-lookup"><span data-stu-id="c6d69-181">OUTPUTS</span></span>

### <span data-ttu-id="c6d69-182">System. Object</span><span class="sxs-lookup"><span data-stu-id="c6d69-182">System.Object</span></span>

## <span data-ttu-id="c6d69-183">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="c6d69-183">NOTES</span></span>

<span data-ttu-id="c6d69-184">`Publish-Module` körs på PowerShell 3,0 eller senare versioner av PowerShell på Windows 7 eller Windows 2008 R2 och senare versioner av Windows.</span><span class="sxs-lookup"><span data-stu-id="c6d69-184">`Publish-Module` runs on PowerShell 3.0 or later releases of PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>

<span data-ttu-id="c6d69-185">Att publicera en modul kräver metadata som visas på Galleri sidan för modulen.</span><span class="sxs-lookup"><span data-stu-id="c6d69-185">Publishing a module requires metadata that is displayed on the gallery page for the module.</span></span> <span data-ttu-id="c6d69-186">Obligatoriska metadata innehåller modulens namn, version, beskrivning och författare.</span><span class="sxs-lookup"><span data-stu-id="c6d69-186">Required metadata includes the module name, version, description, and author.</span></span> <span data-ttu-id="c6d69-187">De flesta metadata tas från modulens manifest, men vissa metadata kan anges i `Publish-Module` parametrar, t. ex. **tagg** , **ReleaseNote** , **IconUri** , **ProjectUri** och **LicenseUri**.</span><span class="sxs-lookup"><span data-stu-id="c6d69-187">Most metadata is taken from the module manifest, but some metadata can be specified in `Publish-Module` parameters, such as **Tag** , **ReleaseNote** , **IconUri** , **ProjectUri** , and **LicenseUri**.</span></span> <span data-ttu-id="c6d69-188">Mer information finns i [paket manifest värden som påverkar PowerShell-galleriet användar gränssnittet](/powershell/scripting/gallery/concepts/package-manifest-affecting-ui).</span><span class="sxs-lookup"><span data-stu-id="c6d69-188">For more information, see [Package manifest values that impact the PowerShell Gallery UI](/powershell/scripting/gallery/concepts/package-manifest-affecting-ui).</span></span>

## <span data-ttu-id="c6d69-189">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="c6d69-189">RELATED LINKS</span></span>

[<span data-ttu-id="c6d69-190">Sök-modul</span><span class="sxs-lookup"><span data-stu-id="c6d69-190">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="c6d69-191">Installera-modul</span><span class="sxs-lookup"><span data-stu-id="c6d69-191">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="c6d69-192">Registrera – PSRepository</span><span class="sxs-lookup"><span data-stu-id="c6d69-192">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="c6d69-193">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="c6d69-193">Set-PSRepository</span></span>](Set-PSRepository.md)

[<span data-ttu-id="c6d69-194">Avinstallera-modul</span><span class="sxs-lookup"><span data-stu-id="c6d69-194">Uninstall-Module</span></span>](Uninstall-Module.md)

[<span data-ttu-id="c6d69-195">Update-modul</span><span class="sxs-lookup"><span data-stu-id="c6d69-195">Update-Module</span></span>](Update-Module.md)
