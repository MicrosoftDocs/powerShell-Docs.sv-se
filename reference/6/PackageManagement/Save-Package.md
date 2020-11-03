---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 04/03/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/save-package?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Package
ms.openlocfilehash: f94f1e3feba96aa49d44c25f2775ac9cffd0c459
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265677"
---
# <span data-ttu-id="41478-103">Save-Package</span><span class="sxs-lookup"><span data-stu-id="41478-103">Save-Package</span></span>

## <span data-ttu-id="41478-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="41478-104">SYNOPSIS</span></span>
<span data-ttu-id="41478-105">Sparar paket på den lokala datorn utan att installera dem.</span><span class="sxs-lookup"><span data-stu-id="41478-105">Saves packages to the local computer without installing them.</span></span>

## <span data-ttu-id="41478-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="41478-106">SYNTAX</span></span>

### <span data-ttu-id="41478-107">PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="41478-107">PackageBySearch</span></span>

```
Save-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Source <String[]>] [-Path <String>] [-LiteralPath <String>]
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllVersions]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="41478-108">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="41478-108">PackageByInputObject</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] -InputObject <SoftwareIdentity>
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllVersions]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="41478-109">NuGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="41478-109">NuGet:PackageByInputObject</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ConfigFile <String>] [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>]
 [-Contains <String>] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="41478-110">NuGet</span><span class="sxs-lookup"><span data-stu-id="41478-110">NuGet</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ConfigFile <String>] [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>]
 [-Contains <String>] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="41478-111">PowerShellGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="41478-111">PowerShellGet:PackageByInputObject</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-AllowPrereleaseVersions] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [<CommonParameters>]
```

### <span data-ttu-id="41478-112">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="41478-112">PowerShellGet</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-AllowPrereleaseVersions] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [<CommonParameters>]
```

## <span data-ttu-id="41478-113">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="41478-113">DESCRIPTION</span></span>

<span data-ttu-id="41478-114">`Save-Package`Cmdleten sparar paket på den lokala datorn men installerar inte paketen.</span><span class="sxs-lookup"><span data-stu-id="41478-114">The `Save-Package` cmdlet saves packages to the local computer but doesn't install the packages.</span></span>
<span data-ttu-id="41478-115">Denna cmdlet sparar den senaste versionen av ett paket om du inte anger en **RequiredVerion**.</span><span class="sxs-lookup"><span data-stu-id="41478-115">This cmdlet saves the newest version of a package unless you specify a **RequiredVerion**.</span></span> <span data-ttu-id="41478-116">**Sökvägen** och **LiteralPath** -parametrarna är ömsesidigt uteslutande och kan inte läggas till i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="41478-116">The **Path** and **LiteralPath** parameters are mutually exclusive, and cannot be added to the same command.</span></span>

## <span data-ttu-id="41478-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="41478-117">EXAMPLES</span></span>

### <span data-ttu-id="41478-118">Exempel 1: Spara ett paket på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="41478-118">Example 1: Save a package to the local computer</span></span>

<span data-ttu-id="41478-119">I det här exemplet sparas den nyaste versionen av paketet i en katalog på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="41478-119">This example saves the newest version of the package to a directory on the local computer.</span></span> <span data-ttu-id="41478-120">Paketets beroenden laddas ned med paketet.</span><span class="sxs-lookup"><span data-stu-id="41478-120">The package's dependencies are download with the package.</span></span>

```
PS> Save-Package -Name NuGet.Core -ProviderName NuGet -Path C:\LocalPkg
```

```Output
Name                    Version    Source    Summary
----                    -------    ------    -------
Microsoft.Web.Xdt       3.0.0      Nuget     Microsoft Xml Document Transformation (XDT) enables...
NuGet.Core              2.14.0     Nuget     NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="41478-121">`Save-Package` använder parametern **Name** för att ange paketet.</span><span class="sxs-lookup"><span data-stu-id="41478-121">`Save-Package` uses the **Name** parameter to specify the package.</span></span> <span data-ttu-id="41478-122">Paketet hämtas från den lagrings plats som anges av parametern **ProviderName** .</span><span class="sxs-lookup"><span data-stu-id="41478-122">The package is downloaded from the repository specified by the **ProviderName** parameter.</span></span> <span data-ttu-id="41478-123">Parametern **Path** bestämmer var paketet sparas.</span><span class="sxs-lookup"><span data-stu-id="41478-123">The **Path** parameter determines where the package is saved.</span></span>

### <span data-ttu-id="41478-124">Exempel 2: Spara en angiven paket version</span><span class="sxs-lookup"><span data-stu-id="41478-124">Example 2: Save a specific package version</span></span>

<span data-ttu-id="41478-125">I det här exemplet anges paket versionen och sparas i en katalog på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="41478-125">This example specifies the package version and saves it to a directory on the local computer.</span></span>

```
PS> Save-Package -Name NuGet.Core -RequiredVersion 2.9.0 -ProviderName NuGet -Path C:\LocalPkg
```

```Output
Name                    Version    Source    Summary
----                    -------    ------    -------
Microsoft.Web.Xdt       3.0.0      Nuget     Microsoft Xml Document Transformation (XDT) enables...
NuGet.Core              2.9.0      Nuget     NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="41478-126">`Save-Package` använder parametern **Name** för att ange paketet.</span><span class="sxs-lookup"><span data-stu-id="41478-126">`Save-Package` uses the **Name** parameter to specify the package.</span></span> <span data-ttu-id="41478-127">**RequiredVersion** anger en angiven paket version.</span><span class="sxs-lookup"><span data-stu-id="41478-127">**RequiredVersion** indicates a specific package version.</span></span> <span data-ttu-id="41478-128">Paketet hämtas från den lagrings plats som anges av parametern **ProviderName** .</span><span class="sxs-lookup"><span data-stu-id="41478-128">The package is downloaded from the repository specified by the **ProviderName** parameter.</span></span> <span data-ttu-id="41478-129">Parametern **Path** bestämmer var paketet sparas.</span><span class="sxs-lookup"><span data-stu-id="41478-129">The **Path** parameter determines where the package is saved.</span></span>

### <span data-ttu-id="41478-130">Exempel 3: använda Find-Package för att spara ett paket</span><span class="sxs-lookup"><span data-stu-id="41478-130">Example 3: Use Find-Package to save a package</span></span>

<span data-ttu-id="41478-131">Det här kommandot använder `Find-Package` för att hitta den senaste versionen av paketet och skicka objektet till `Save-Package` .</span><span class="sxs-lookup"><span data-stu-id="41478-131">This command uses `Find-Package` to locate the newest version of the package and sends the object to `Save-Package`.</span></span>

```
PS> Find-Package -Name NuGet.Core -ProviderName NuGet | Save-Package -Path C:\LocalPkg
```

<span data-ttu-id="41478-132">`Find-Package` använder parametern **Name** för att ange paketet.</span><span class="sxs-lookup"><span data-stu-id="41478-132">`Find-Package` uses the **Name** parameter to specify the package.</span></span> <span data-ttu-id="41478-133">Paketet hämtas från den lagrings plats som anges av parametern **ProviderName** .</span><span class="sxs-lookup"><span data-stu-id="41478-133">The package is downloaded from the repository specified by the **ProviderName** parameter.</span></span> <span data-ttu-id="41478-134">Objektet skickas ned pipelinen till `Save-Package` .</span><span class="sxs-lookup"><span data-stu-id="41478-134">The object is sent down the pipeline to `Save-Package`.</span></span> <span data-ttu-id="41478-135">Parametern **Path** bestämmer var paketet sparas.</span><span class="sxs-lookup"><span data-stu-id="41478-135">The **Path** parameter determines where the package is saved.</span></span>

### <span data-ttu-id="41478-136">Exempel 4: Spara och installera paketet</span><span class="sxs-lookup"><span data-stu-id="41478-136">Example 4: Save and install the package</span></span>

<span data-ttu-id="41478-137">Den senaste versionen av paketet och dess beroenden laddas ned och installeras på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="41478-137">The newest version of the package and its dependencies are downloaded and installed on the local computer.</span></span>

```
PS> Save-Package -Name NuGet.Core -ProviderName NuGet -Path C:\LocalPkg
PS> Install-Package C:\LocalPkg\NuGet.Core.2.14.0.nupkg
```

<span data-ttu-id="41478-138">`Save-Package` laddar ned paket filen och dess beroenden till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="41478-138">`Save-Package` downloads the package file and its dependencies to the local computer.</span></span>
<span data-ttu-id="41478-139">`Install-Package` installerar paketet och beroendena från den angivna katalogen.</span><span class="sxs-lookup"><span data-stu-id="41478-139">`Install-Package` installs the package and dependencies from the specified directory.</span></span>

## <span data-ttu-id="41478-140">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="41478-140">PARAMETERS</span></span>

### <span data-ttu-id="41478-141">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="41478-141">-AcceptLicense</span></span>

<span data-ttu-id="41478-142">Godkänn licens avtalet automatiskt under installationen om paketet kräver det.</span><span class="sxs-lookup"><span data-stu-id="41478-142">Automatically accept the license agreement during installation if the package requires it.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41478-143">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="41478-143">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="41478-144">Tillåter att paket som marker ATS som för hands version sparas.</span><span class="sxs-lookup"><span data-stu-id="41478-144">Allows packages marked as Prerelease to be saved.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageByInputObject, NuGet, PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41478-145">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="41478-145">-AllVersions</span></span>

<span data-ttu-id="41478-146">Anger att denna cmdlet sparar alla tillgängliga versioner av paketet.</span><span class="sxs-lookup"><span data-stu-id="41478-146">Indicates that this cmdlet saves all available versions of the package.</span></span>

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

### <span data-ttu-id="41478-147">-Kommando</span><span class="sxs-lookup"><span data-stu-id="41478-147">-Command</span></span>

<span data-ttu-id="41478-148">Anger ett eller flera kommandon som ingår i paketet.</span><span class="sxs-lookup"><span data-stu-id="41478-148">Specifies one or more commands included in the package.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41478-149">– ConfigFile</span><span class="sxs-lookup"><span data-stu-id="41478-149">-ConfigFile</span></span>

<span data-ttu-id="41478-150">Anger en konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="41478-150">Specifies a configuration File.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41478-151">– Innehåller</span><span class="sxs-lookup"><span data-stu-id="41478-151">-Contains</span></span>

<span data-ttu-id="41478-152">`Save-Package` hämtar objekt om ett objekt i objektets egenskaps värden är en exakt matchning för det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="41478-152">`Save-Package` gets objects if any item in the object's property values are an exact match for the specified value.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41478-153">-Credential</span><span class="sxs-lookup"><span data-stu-id="41478-153">-Credential</span></span>

<span data-ttu-id="41478-154">Anger ett användar konto som har behörighet att spara ett paket från en angiven paket leverantör eller källa.</span><span class="sxs-lookup"><span data-stu-id="41478-154">Specifies a user account that has permission to save a package from a specified package provider or source.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41478-155">– Dscresource Keyword Supports</span><span class="sxs-lookup"><span data-stu-id="41478-155">-DscResource</span></span>

<span data-ttu-id="41478-156">Anger en eller flera DSC-resurser (Desired State Configuration) för paketet.</span><span class="sxs-lookup"><span data-stu-id="41478-156">Specifies one or more Desired State Configuration (DSC) resources for the package.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41478-157">-Filter</span><span class="sxs-lookup"><span data-stu-id="41478-157">-Filter</span></span>

<span data-ttu-id="41478-158">Anger ett filter för paketet.</span><span class="sxs-lookup"><span data-stu-id="41478-158">Specifies a filter for the package.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41478-159">-FilterOnTag</span><span class="sxs-lookup"><span data-stu-id="41478-159">-FilterOnTag</span></span>

<span data-ttu-id="41478-160">Anger taggen som filtrerar resultaten.</span><span class="sxs-lookup"><span data-stu-id="41478-160">Specifies the tag that filters the results.</span></span> <span data-ttu-id="41478-161">Resultat som inte innehåller den angivna taggen utesluts.</span><span class="sxs-lookup"><span data-stu-id="41478-161">Results that don't contain the specified tag are excluded.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41478-162">-Force</span><span class="sxs-lookup"><span data-stu-id="41478-162">-Force</span></span>

<span data-ttu-id="41478-163">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="41478-163">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="41478-164">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="41478-164">-ForceBootstrap</span></span>

<span data-ttu-id="41478-165">Indikerar att `Save-Package` tvingar **PackageManagement** att automatiskt installera paket leverantören för det angivna paketet.</span><span class="sxs-lookup"><span data-stu-id="41478-165">Indicates that `Save-Package` forces **PackageManagement** to automatically install the package provider for the specified package.</span></span>

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

### <span data-ttu-id="41478-166">– Sidhuvud</span><span class="sxs-lookup"><span data-stu-id="41478-166">-Headers</span></span>

<span data-ttu-id="41478-167">Anger sidhuvuden för paketet.</span><span class="sxs-lookup"><span data-stu-id="41478-167">Specifies the headers for the package.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41478-168">– Innehåller</span><span class="sxs-lookup"><span data-stu-id="41478-168">-Includes</span></span>

<span data-ttu-id="41478-169">Anger vilka resurser som paketet innehåller.</span><span class="sxs-lookup"><span data-stu-id="41478-169">Indicates the resources that the package includes.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:
Accepted values: DscResource, Cmdlet, Function, Workflow, RoleCapability

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41478-170">– InputObject</span><span class="sxs-lookup"><span data-stu-id="41478-170">-InputObject</span></span>

<span data-ttu-id="41478-171">Ett program-ID-objekt som representerar det paket som du vill spara.</span><span class="sxs-lookup"><span data-stu-id="41478-171">A software ID object that represents the package that you want to save.</span></span> <span data-ttu-id="41478-172">Program-ID: n ingår i resultatet av `Find-Package` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="41478-172">Software IDs are part of the results of the `Find-Package` cmdlet.</span></span>

```yaml
Type: Microsoft.PackageManagement.Packaging.SoftwareIdentity
Parameter Sets: PackageByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="41478-173">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="41478-173">-LiteralPath</span></span>

<span data-ttu-id="41478-174">Anger den litterala sökvägen till vilken du vill spara paketet.</span><span class="sxs-lookup"><span data-stu-id="41478-174">Specifies the literal path to which you want to save the package.</span></span> <span data-ttu-id="41478-175">Du kan inte lägga till både den här parametern och parametern **Path** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="41478-175">You cannot add both this parameter and the **Path** parameter to the same command.</span></span>

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

### <span data-ttu-id="41478-176">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="41478-176">-MaximumVersion</span></span>

<span data-ttu-id="41478-177">Anger den högsta versionen av paketet som du vill spara.</span><span class="sxs-lookup"><span data-stu-id="41478-177">Specifies the maximum version of the package that you want to save.</span></span>

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41478-178">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="41478-178">-MinimumVersion</span></span>

<span data-ttu-id="41478-179">Anger den lägsta version av paketet som du vill hitta.</span><span class="sxs-lookup"><span data-stu-id="41478-179">Specifies the minimum version of the package that you want to find.</span></span>

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41478-180">-Name</span><span class="sxs-lookup"><span data-stu-id="41478-180">-Name</span></span>

<span data-ttu-id="41478-181">Anger ett eller flera paket namn.</span><span class="sxs-lookup"><span data-stu-id="41478-181">Specifies one or more package names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="41478-182">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="41478-182">-PackageManagementProvider</span></span>

<span data-ttu-id="41478-183">Anger en paket hanterings leverantör.</span><span class="sxs-lookup"><span data-stu-id="41478-183">Specifies a package management provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41478-184">-Path</span><span class="sxs-lookup"><span data-stu-id="41478-184">-Path</span></span>

<span data-ttu-id="41478-185">Anger platsen på den lokala datorn där paketet ska lagras.</span><span class="sxs-lookup"><span data-stu-id="41478-185">Specifies the location on the local computer to store the package.</span></span>

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

### <span data-ttu-id="41478-186">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="41478-186">-ProviderName</span></span>

<span data-ttu-id="41478-187">Anger ett eller flera providernamn.</span><span class="sxs-lookup"><span data-stu-id="41478-187">Specifies one or more provider names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="41478-188">-Proxy</span><span class="sxs-lookup"><span data-stu-id="41478-188">-Proxy</span></span>

<span data-ttu-id="41478-189">Anger en proxyserver för begäran, i stället för en direkt anslutning till Internet resursen.</span><span class="sxs-lookup"><span data-stu-id="41478-189">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="41478-190">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="41478-190">-ProxyCredential</span></span>

<span data-ttu-id="41478-191">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="41478-191">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41478-192">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="41478-192">-PublishLocation</span></span>

<span data-ttu-id="41478-193">Anger publicerings platsen.</span><span class="sxs-lookup"><span data-stu-id="41478-193">Specifies the publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41478-194">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="41478-194">-RequiredVersion</span></span>

<span data-ttu-id="41478-195">Anger den exakta versionen av paketet som ska sparas.</span><span class="sxs-lookup"><span data-stu-id="41478-195">Specifies the exact version of the package to save.</span></span>

```yaml
Type: System.String
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41478-196">-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="41478-196">-RoleCapability</span></span>

<span data-ttu-id="41478-197">Anger en matris med roll funktioner.</span><span class="sxs-lookup"><span data-stu-id="41478-197">Specifies an array of role capabilities.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41478-198">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="41478-198">-ScriptPublishLocation</span></span>

<span data-ttu-id="41478-199">Anger skriptets publicerings plats.</span><span class="sxs-lookup"><span data-stu-id="41478-199">Specifies the script publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41478-200">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="41478-200">-ScriptSourceLocation</span></span>

<span data-ttu-id="41478-201">Anger sökvägen till skript källan.</span><span class="sxs-lookup"><span data-stu-id="41478-201">Specifies the script source location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41478-202">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="41478-202">-SkipValidate</span></span>

<span data-ttu-id="41478-203">Växel som hoppar över verifiering av autentiseringsuppgifterna för ett paket.</span><span class="sxs-lookup"><span data-stu-id="41478-203">Switch that skips validating the credentials of a package.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageByInputObject, NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41478-204">-Source</span><span class="sxs-lookup"><span data-stu-id="41478-204">-Source</span></span>

<span data-ttu-id="41478-205">Anger en eller flera paket källor.</span><span class="sxs-lookup"><span data-stu-id="41478-205">Specifies one or more package sources.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="41478-206">-Tagga</span><span class="sxs-lookup"><span data-stu-id="41478-206">-Tag</span></span>

<span data-ttu-id="41478-207">Anger en tagg att söka efter inom paketets metadata.</span><span class="sxs-lookup"><span data-stu-id="41478-207">Specifies a tag to search for within the package metadata.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41478-208">-Typ</span><span class="sxs-lookup"><span data-stu-id="41478-208">-Type</span></span>

<span data-ttu-id="41478-209">Anger om du vill söka efter paket med en modul, ett skript eller något av alternativen.</span><span class="sxs-lookup"><span data-stu-id="41478-209">Specifies whether to search for packages with a module, a script, or either.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet
Aliases:
Accepted values: Module, Script, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="41478-210">-Confirm</span><span class="sxs-lookup"><span data-stu-id="41478-210">-Confirm</span></span>

<span data-ttu-id="41478-211">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="41478-211">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="41478-212">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="41478-212">-WhatIf</span></span>

<span data-ttu-id="41478-213">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="41478-213">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="41478-214">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="41478-214">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="41478-215">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="41478-215">CommonParameters</span></span>

<span data-ttu-id="41478-216">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="41478-216">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="41478-217">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="41478-217">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="41478-218">INDATA</span><span class="sxs-lookup"><span data-stu-id="41478-218">INPUTS</span></span>

### <span data-ttu-id="41478-219">`Save-Package` accepterar objekt från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="41478-219">`Save-Package` accepts objects from the pipeline.</span></span>

## <span data-ttu-id="41478-220">UTDATA</span><span class="sxs-lookup"><span data-stu-id="41478-220">OUTPUTS</span></span>

### <span data-ttu-id="41478-221">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="41478-221">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="41478-222">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="41478-222">NOTES</span></span>

## <span data-ttu-id="41478-223">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="41478-223">RELATED LINKS</span></span>

[<span data-ttu-id="41478-224">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="41478-224">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="41478-225">Get-Package</span><span class="sxs-lookup"><span data-stu-id="41478-225">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="41478-226">Installationspaket</span><span class="sxs-lookup"><span data-stu-id="41478-226">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="41478-227">Spara paket</span><span class="sxs-lookup"><span data-stu-id="41478-227">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="41478-228">Avinstallera paket</span><span class="sxs-lookup"><span data-stu-id="41478-228">Uninstall-Package</span></span>](Uninstall-Package.md)
