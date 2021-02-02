---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 10/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/publish-module?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Publish-Module
ms.openlocfilehash: 2edc05ff660cfcca232af878c593c29de68eb122
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891361"
---
# <span data-ttu-id="0c4af-102">Publish-Module</span><span class="sxs-lookup"><span data-stu-id="0c4af-102">Publish-Module</span></span>

## <span data-ttu-id="0c4af-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="0c4af-103">SYNOPSIS</span></span>
<span data-ttu-id="0c4af-104">Publicerar en angiven modul från den lokala datorn till ett onlinegalleri.</span><span class="sxs-lookup"><span data-stu-id="0c4af-104">Publishes a specified module from the local computer to an online gallery.</span></span>

## <span data-ttu-id="0c4af-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0c4af-105">SYNTAX</span></span>

### <span data-ttu-id="0c4af-106">ModuleNameParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="0c4af-106">ModuleNameParameterSet (Default)</span></span>

```
Publish-Module -Name <String> [-RequiredVersion <String>] [-NuGetApiKey <String>]
 [-Repository <String>] [-Credential <PSCredential>] [-FormatVersion <Version>]
 [-ReleaseNotes <String[]>] [-Tags <String[]>] [-LicenseUri <Uri>] [-IconUri <Uri>]
 [-ProjectUri <Uri>] [-Exclude <String[]>] [-Force] [-AllowPrerelease] [-SkipAutomaticTags]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="0c4af-107">ModulePathParameterSet</span><span class="sxs-lookup"><span data-stu-id="0c4af-107">ModulePathParameterSet</span></span>

```
Publish-Module -Path <String> [-NuGetApiKey <String>] [-Repository <String>]
 [-Credential <PSCredential>] [-FormatVersion <Version>] [-ReleaseNotes <String[]>]
 [-Tags <String[]>] [-LicenseUri <Uri>] [-IconUri <Uri>] [-ProjectUri <Uri>] [-Force]
 [-SkipAutomaticTags] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="0c4af-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="0c4af-108">DESCRIPTION</span></span>

<span data-ttu-id="0c4af-109">`Publish-Module`Cmdleten publicerar en modul till ett NuGet-baserat galleri med hjälp av en API-nyckel som lagras som en del av en användar profil i galleriet.</span><span class="sxs-lookup"><span data-stu-id="0c4af-109">The `Publish-Module` cmdlet publishes a module to an online NuGet-based gallery by using an API key, stored as part of a user's profile in the gallery.</span></span> <span data-ttu-id="0c4af-110">Du kan ange vilken modul som ska publiceras antingen av modulens namn eller efter sökvägen till mappen som innehåller modulen.</span><span class="sxs-lookup"><span data-stu-id="0c4af-110">You can specify the module to publish either by the module's name, or by the path to the folder containing the module.</span></span>

<span data-ttu-id="0c4af-111">När du anger en modul efter namn, `Publish-Module` publicerar den första modulen som skulle hittas genom att köra `Get-Module -ListAvailable <Name>` .</span><span class="sxs-lookup"><span data-stu-id="0c4af-111">When you specify a module by name, `Publish-Module` publishes the first module that would be found by running `Get-Module -ListAvailable <Name>`.</span></span> <span data-ttu-id="0c4af-112">Om du anger en lägsta version av en modul som ska publiceras, `Publish-Module` publicerar den första modulen med en version som är större än eller lika med den lägsta version som du har angett.</span><span class="sxs-lookup"><span data-stu-id="0c4af-112">If you specify a minimum version of a module to publish, `Publish-Module` publishes the first module with a version that is greater than or equal to the minimum version that you have specified.</span></span>

<span data-ttu-id="0c4af-113">Att publicera en modul kräver metadata som visas på Galleri sidan för modulen.</span><span class="sxs-lookup"><span data-stu-id="0c4af-113">Publishing a module requires metadata that is displayed on the gallery page for the module.</span></span> <span data-ttu-id="0c4af-114">Obligatoriska metadata innehåller modulens namn, version, beskrivning och författare.</span><span class="sxs-lookup"><span data-stu-id="0c4af-114">Required metadata includes the module name, version, description, and author.</span></span> <span data-ttu-id="0c4af-115">Även om de flesta metadata tas från modulens manifest, måste vissa metadata anges i `Publish-Module` parametrar, till exempel **tag**, **ReleaseNote**, **IconUri**, **ProjectUri** och **LicenseUri**, eftersom dessa parametrar matchar fält i ett NuGet-baserat Galleri.</span><span class="sxs-lookup"><span data-stu-id="0c4af-115">Although most metadata is taken from the module manifest, some metadata must be specified in `Publish-Module` parameters, such as **Tag**, **ReleaseNote**, **IconUri**, **ProjectUri**, and **LicenseUri**, because these parameters match fields in a NuGet-based gallery.</span></span>

## <span data-ttu-id="0c4af-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="0c4af-116">EXAMPLES</span></span>

### <span data-ttu-id="0c4af-117">Exempel 1: publicera en modul</span><span class="sxs-lookup"><span data-stu-id="0c4af-117">Example 1: Publish a module</span></span>

<span data-ttu-id="0c4af-118">I det här exemplet publiceras MyDscModule i online-galleriet med hjälp av API-nyckeln för att ange module-kontots onlinegalleri.</span><span class="sxs-lookup"><span data-stu-id="0c4af-118">In this example, MyDscModule is published to the online gallery by using the API key to indicate the module owner's online gallery account.</span></span> <span data-ttu-id="0c4af-119">Om MyDscModule inte är en giltig manifest-modul som anger namn, version, beskrivning och författare inträffar ett fel.</span><span class="sxs-lookup"><span data-stu-id="0c4af-119">If MyDscModule is not a valid manifest module that specifies a name, version, description, and author, an error occurs.</span></span>

```powershell
Publish-Module -Name "MyDscModule" -NuGetApiKey "11e4b435-6cb4-4bf7-8611-5162ed75eb73"
```

### <span data-ttu-id="0c4af-120">Exempel 2: publicera en modul med metadata för galleriet</span><span class="sxs-lookup"><span data-stu-id="0c4af-120">Example 2: Publish a module with gallery metadata</span></span>

<span data-ttu-id="0c4af-121">I det här exemplet publiceras MyDscModule i online-galleriet med hjälp av API-nyckeln för att ange modulens ägares Galleri konto.</span><span class="sxs-lookup"><span data-stu-id="0c4af-121">In this example, MyDscModule is published to the online gallery by using the API key to indicate the module owner's gallery account.</span></span> <span data-ttu-id="0c4af-122">De ytterligare metadata som anges visas på webb sidan för modulen i galleriet.</span><span class="sxs-lookup"><span data-stu-id="0c4af-122">The additional metadata provided is displayed on the webpage for the module in the gallery.</span></span> <span data-ttu-id="0c4af-123">Ägaren lägger till två söktaggar för modulen, relaterad den till Active Directory. en kort versions anteckning har lagts till.</span><span class="sxs-lookup"><span data-stu-id="0c4af-123">The owner adds two search tags for the module, relating it to Active Directory; a brief release note is added.</span></span> <span data-ttu-id="0c4af-124">Om MyDscModule inte är en giltig manifest-modul som anger namn, version, beskrivning och författare inträffar ett fel.</span><span class="sxs-lookup"><span data-stu-id="0c4af-124">If MyDscModule is not a valid manifest module that specifies a name, version, description, and author, an error occurs.</span></span>

```powershell
Publish-Module -Name "MyDscModule" -NuGetApiKey "11e4b435-6cb4-4bf7-8611-5162ed75eb73" -LicenseUri "http://contoso.com/license" -Tag "Active Directory","DSC" -ReleaseNote "Updated the ActiveDirectory DSC Resources to support adding users."
```

## <span data-ttu-id="0c4af-125">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="0c4af-125">PARAMETERS</span></span>

### <span data-ttu-id="0c4af-126">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="0c4af-126">-AllowPrerelease</span></span>

<span data-ttu-id="0c4af-127">Gör det möjligt att publicera moduler som är markerade som för hands versioner.</span><span class="sxs-lookup"><span data-stu-id="0c4af-127">Allows modules marked as prerelease to be published.</span></span>

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

### <span data-ttu-id="0c4af-128">-Confirm</span><span class="sxs-lookup"><span data-stu-id="0c4af-128">-Confirm</span></span>

<span data-ttu-id="0c4af-129">Du uppmanas att bekräfta innan du kör `Publish-Module` .</span><span class="sxs-lookup"><span data-stu-id="0c4af-129">Prompts you for confirmation before running the `Publish-Module`.</span></span>

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

### <span data-ttu-id="0c4af-130">-Credential</span><span class="sxs-lookup"><span data-stu-id="0c4af-130">-Credential</span></span>

<span data-ttu-id="0c4af-131">Anger ett användar konto som har behörighet att publicera en modul för en angiven paket leverantör eller källa.</span><span class="sxs-lookup"><span data-stu-id="0c4af-131">Specifies a user account that has rights to publish a module for a specified package provider or source.</span></span>

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

### <span data-ttu-id="0c4af-132">-Undanta</span><span class="sxs-lookup"><span data-stu-id="0c4af-132">-Exclude</span></span>

<span data-ttu-id="0c4af-133">Definierar filer som ska undantas från den publicerade modulen.</span><span class="sxs-lookup"><span data-stu-id="0c4af-133">Defines files to exclude from the published module.</span></span>

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

### <span data-ttu-id="0c4af-134">-Force</span><span class="sxs-lookup"><span data-stu-id="0c4af-134">-Force</span></span>

<span data-ttu-id="0c4af-135">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="0c4af-135">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="0c4af-136">-FormatVersion</span><span class="sxs-lookup"><span data-stu-id="0c4af-136">-FormatVersion</span></span>

<span data-ttu-id="0c4af-137">Accepterar endast giltiga värden som anges av attributet **ValidateSet** .</span><span class="sxs-lookup"><span data-stu-id="0c4af-137">Accepts only valid values specified by the **ValidateSet** attribute.</span></span>

<span data-ttu-id="0c4af-138">Mer information finns i [ValidateSet-attributets deklaration](/powershell/scripting/developer/cmdlet/validateset-attribute-declaration) och [ValidateSetAttribute](/dotnet/api/system.management.automation.validatesetattribute).</span><span class="sxs-lookup"><span data-stu-id="0c4af-138">For more information, see [ValidateSet Attribute Declaration](/powershell/scripting/developer/cmdlet/validateset-attribute-declaration) and [ValidateSetAttribute](/dotnet/api/system.management.automation.validatesetattribute).</span></span>

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

### <span data-ttu-id="0c4af-139">– IconUri</span><span class="sxs-lookup"><span data-stu-id="0c4af-139">-IconUri</span></span>

<span data-ttu-id="0c4af-140">Anger URL-adressen till en ikon för modulen.</span><span class="sxs-lookup"><span data-stu-id="0c4af-140">Specifies the URL of an icon for the module.</span></span> <span data-ttu-id="0c4af-141">Den angivna ikonen visas på Galleri webb sidan för modulen.</span><span class="sxs-lookup"><span data-stu-id="0c4af-141">The specified icon is displayed on the gallery webpage for the module.</span></span>

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

### <span data-ttu-id="0c4af-142">-LicenseUri</span><span class="sxs-lookup"><span data-stu-id="0c4af-142">-LicenseUri</span></span>

<span data-ttu-id="0c4af-143">Anger webb adressen till licens villkoren för den modul som du vill publicera.</span><span class="sxs-lookup"><span data-stu-id="0c4af-143">Specifies the URL of licensing terms for the module you want to publish.</span></span>

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

### <span data-ttu-id="0c4af-144">-Name</span><span class="sxs-lookup"><span data-stu-id="0c4af-144">-Name</span></span>

<span data-ttu-id="0c4af-145">Anger namnet på den modul som du vill publicera.</span><span class="sxs-lookup"><span data-stu-id="0c4af-145">Specifies the name of the module that you want to publish.</span></span> <span data-ttu-id="0c4af-146">`Publish-Module` söker efter det angivna modulnamnet i `$Env:PSModulePath` .</span><span class="sxs-lookup"><span data-stu-id="0c4af-146">`Publish-Module` searches for the specified module name in `$Env:PSModulePath`.</span></span>

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

### <span data-ttu-id="0c4af-147">-NuGetApiKey</span><span class="sxs-lookup"><span data-stu-id="0c4af-147">-NuGetApiKey</span></span>

<span data-ttu-id="0c4af-148">Anger den API-nyckel som du vill använda för att publicera en modul i onlinegalleri.</span><span class="sxs-lookup"><span data-stu-id="0c4af-148">Specifies the API key that you want to use to publish a module to the online gallery.</span></span> <span data-ttu-id="0c4af-149">API-nyckeln är en del av din profil i Onlinegalleri, och du hittar den på sidan användar konto i galleriet.</span><span class="sxs-lookup"><span data-stu-id="0c4af-149">The API key is part of your profile in the online gallery, and can be found on your user account page in the gallery.</span></span> <span data-ttu-id="0c4af-150">API-nyckeln är NuGet funktioner.</span><span class="sxs-lookup"><span data-stu-id="0c4af-150">The API key is NuGet-specific functionality.</span></span>

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

### <span data-ttu-id="0c4af-151">-Path</span><span class="sxs-lookup"><span data-stu-id="0c4af-151">-Path</span></span>

<span data-ttu-id="0c4af-152">Anger sökvägen till den modul som du vill publicera.</span><span class="sxs-lookup"><span data-stu-id="0c4af-152">Specifies the path to the module that you want to publish.</span></span> <span data-ttu-id="0c4af-153">Den här parametern godkänner sökvägen till mappen som innehåller modulen.</span><span class="sxs-lookup"><span data-stu-id="0c4af-153">This parameter accepts the path to the folder that contains the module.</span></span>

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

### <span data-ttu-id="0c4af-154">-ProjectUri</span><span class="sxs-lookup"><span data-stu-id="0c4af-154">-ProjectUri</span></span>

<span data-ttu-id="0c4af-155">Anger webb adressen till en webb sida om projektet.</span><span class="sxs-lookup"><span data-stu-id="0c4af-155">Specifies the URL of a webpage about this project.</span></span>

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

### <span data-ttu-id="0c4af-156">-ReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="0c4af-156">-ReleaseNotes</span></span>

<span data-ttu-id="0c4af-157">Anger en sträng som innehåller viktig information eller kommentarer som du vill ska vara tillgängliga för användare av den här versionen av modulen.</span><span class="sxs-lookup"><span data-stu-id="0c4af-157">Specifies a string containing release notes or comments that you want to be available to users of this version of the module.</span></span>

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

### <span data-ttu-id="0c4af-158">– Databas</span><span class="sxs-lookup"><span data-stu-id="0c4af-158">-Repository</span></span>

<span data-ttu-id="0c4af-159">Anger det egna namnet på en lagrings plats som har registrerats genom att köra `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="0c4af-159">Specifies the friendly name of a repository that has been registered by running `Register-PSRepository`.</span></span> <span data-ttu-id="0c4af-160">Lagrings platsen måste ha en **PublishLocation**, vilket är en giltig NUGET-URI.</span><span class="sxs-lookup"><span data-stu-id="0c4af-160">The repository must have a **PublishLocation**, which is a valid NuGet URI.</span></span>
<span data-ttu-id="0c4af-161">**PublishLocation** kan anges genom att köra `Set-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="0c4af-161">The **PublishLocation** can be set by running `Set-PSRepository`.</span></span>

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

### <span data-ttu-id="0c4af-162">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="0c4af-162">-RequiredVersion</span></span>

<span data-ttu-id="0c4af-163">Anger den exakta versionen av en enda modul som ska publiceras.</span><span class="sxs-lookup"><span data-stu-id="0c4af-163">Specifies the exact version of a single module to publish.</span></span>

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

### <span data-ttu-id="0c4af-164">-SkipAutomaticTags</span><span class="sxs-lookup"><span data-stu-id="0c4af-164">-SkipAutomaticTags</span></span>

<span data-ttu-id="0c4af-165">Tar bort kommandon och resurser från att inkluderas som taggar.</span><span class="sxs-lookup"><span data-stu-id="0c4af-165">Removes commands and resources from being included as tags.</span></span> <span data-ttu-id="0c4af-166">Hoppar över automatiskt tillägg av taggar i en modul.</span><span class="sxs-lookup"><span data-stu-id="0c4af-166">Skips automatically adding tags to a module.</span></span>

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

### <span data-ttu-id="0c4af-167">– Taggar</span><span class="sxs-lookup"><span data-stu-id="0c4af-167">-Tags</span></span>

<span data-ttu-id="0c4af-168">Lägger till en eller flera taggar till den modul som du publicerar.</span><span class="sxs-lookup"><span data-stu-id="0c4af-168">Adds one or more tags to the module that you are publishing.</span></span> <span data-ttu-id="0c4af-169">Exempel taggar är DesiredStateConfiguration, DSC, DSCResourceKit eller PSModule.</span><span class="sxs-lookup"><span data-stu-id="0c4af-169">Example tags include DesiredStateConfiguration, DSC, DSCResourceKit, or PSModule.</span></span> <span data-ttu-id="0c4af-170">Avgränsa flera taggar med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="0c4af-170">Separate multiple tags with commas.</span></span>

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

### <span data-ttu-id="0c4af-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="0c4af-171">-WhatIf</span></span>

<span data-ttu-id="0c4af-172">Visar vad som händer om `Publish-Module` körningarna körs.</span><span class="sxs-lookup"><span data-stu-id="0c4af-172">Shows what would happen if the `Publish-Module` runs.</span></span> <span data-ttu-id="0c4af-173">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="0c4af-173">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="0c4af-174">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0c4af-174">CommonParameters</span></span>

<span data-ttu-id="0c4af-175">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0c4af-175">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0c4af-176">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="0c4af-176">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0c4af-177">INDATA</span><span class="sxs-lookup"><span data-stu-id="0c4af-177">INPUTS</span></span>

### <span data-ttu-id="0c4af-178">System. String</span><span class="sxs-lookup"><span data-stu-id="0c4af-178">System.String</span></span>

### <span data-ttu-id="0c4af-179">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="0c4af-179">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="0c4af-180">UTDATA</span><span class="sxs-lookup"><span data-stu-id="0c4af-180">OUTPUTS</span></span>

### <span data-ttu-id="0c4af-181">System. Object</span><span class="sxs-lookup"><span data-stu-id="0c4af-181">System.Object</span></span>

## <span data-ttu-id="0c4af-182">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="0c4af-182">NOTES</span></span>

<span data-ttu-id="0c4af-183">`Publish-Module` körs på PowerShell 3,0 eller senare versioner av PowerShell på Windows 7 eller Windows 2008 R2 och senare versioner av Windows.</span><span class="sxs-lookup"><span data-stu-id="0c4af-183">`Publish-Module` runs on PowerShell 3.0 or later releases of PowerShell, on Windows 7 or Windows 2008 R2 and later releases of Windows.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0c4af-184">Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1.</span><span class="sxs-lookup"><span data-stu-id="0c4af-184">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="0c4af-185">Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="0c4af-185">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="0c4af-186">Använd följande kommando för att se till att du använder TLS 1,2:</span><span class="sxs-lookup"><span data-stu-id="0c4af-186">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="0c4af-187">Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="0c4af-187">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

<span data-ttu-id="0c4af-188">Att publicera en modul kräver metadata som visas på Galleri sidan för modulen.</span><span class="sxs-lookup"><span data-stu-id="0c4af-188">Publishing a module requires metadata that is displayed on the gallery page for the module.</span></span> <span data-ttu-id="0c4af-189">Obligatoriska metadata innehåller modulens namn, version, beskrivning och författare.</span><span class="sxs-lookup"><span data-stu-id="0c4af-189">Required metadata includes the module name, version, description, and author.</span></span> <span data-ttu-id="0c4af-190">De flesta metadata tas från modulens manifest, men vissa metadata kan anges i `Publish-Module` parametrar, t. ex. **tagg**, **ReleaseNote**, **IconUri**, **ProjectUri** och **LicenseUri**.</span><span class="sxs-lookup"><span data-stu-id="0c4af-190">Most metadata is taken from the module manifest, but some metadata can be specified in `Publish-Module` parameters, such as **Tag**, **ReleaseNote**, **IconUri**, **ProjectUri**, and **LicenseUri**.</span></span> <span data-ttu-id="0c4af-191">Mer information finns i [paket manifest värden som påverkar PowerShell-galleriet användar gränssnittet](/powershell/scripting/gallery/concepts/package-manifest-affecting-ui).</span><span class="sxs-lookup"><span data-stu-id="0c4af-191">For more information, see [Package manifest values that impact the PowerShell Gallery UI](/powershell/scripting/gallery/concepts/package-manifest-affecting-ui).</span></span>

## <span data-ttu-id="0c4af-192">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="0c4af-192">RELATED LINKS</span></span>

[<span data-ttu-id="0c4af-193">Sök-modul</span><span class="sxs-lookup"><span data-stu-id="0c4af-193">Find-Module</span></span>](Find-Module.md)

[<span data-ttu-id="0c4af-194">Installera-modul</span><span class="sxs-lookup"><span data-stu-id="0c4af-194">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="0c4af-195">Registrera – PSRepository</span><span class="sxs-lookup"><span data-stu-id="0c4af-195">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="0c4af-196">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="0c4af-196">Set-PSRepository</span></span>](Set-PSRepository.md)

[<span data-ttu-id="0c4af-197">Avinstallera-modul</span><span class="sxs-lookup"><span data-stu-id="0c4af-197">Uninstall-Module</span></span>](Uninstall-Module.md)

[<span data-ttu-id="0c4af-198">Update-modul</span><span class="sxs-lookup"><span data-stu-id="0c4af-198">Update-Module</span></span>](Update-Module.md)