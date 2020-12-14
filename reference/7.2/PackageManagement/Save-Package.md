---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 04/03/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/save-package?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Package
ms.openlocfilehash: 93ec8264bad588e38554daddcdf5dc9befce053e
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889358"
---
# <span data-ttu-id="26fa7-102">Save-Package</span><span class="sxs-lookup"><span data-stu-id="26fa7-102">Save-Package</span></span>

## <span data-ttu-id="26fa7-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="26fa7-103">SYNOPSIS</span></span>
<span data-ttu-id="26fa7-104">Sparar paket på den lokala datorn utan att installera dem.</span><span class="sxs-lookup"><span data-stu-id="26fa7-104">Saves packages to the local computer without installing them.</span></span>

## <span data-ttu-id="26fa7-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="26fa7-105">SYNTAX</span></span>

### <span data-ttu-id="26fa7-106">PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="26fa7-106">PackageBySearch</span></span>

```
Save-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Source <String[]>] [-Path <String>] [-LiteralPath <String>]
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllVersions]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="26fa7-107">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="26fa7-107">PackageByInputObject</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] -InputObject <SoftwareIdentity>
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllVersions]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="26fa7-108">NuGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="26fa7-108">NuGet:PackageByInputObject</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ConfigFile <String>] [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>]
 [-Contains <String>] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="26fa7-109">NuGet</span><span class="sxs-lookup"><span data-stu-id="26fa7-109">NuGet</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ConfigFile <String>] [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>]
 [-Contains <String>] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="26fa7-110">PowerShellGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="26fa7-110">PowerShellGet:PackageByInputObject</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-AllowPrereleaseVersions] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [<CommonParameters>]
```

### <span data-ttu-id="26fa7-111">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="26fa7-111">PowerShellGet</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-AllowPrereleaseVersions] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [<CommonParameters>]
```

## <span data-ttu-id="26fa7-112">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="26fa7-112">DESCRIPTION</span></span>

<span data-ttu-id="26fa7-113">`Save-Package`Cmdleten sparar paket på den lokala datorn men installerar inte paketen.</span><span class="sxs-lookup"><span data-stu-id="26fa7-113">The `Save-Package` cmdlet saves packages to the local computer but doesn't install the packages.</span></span>
<span data-ttu-id="26fa7-114">Denna cmdlet sparar den senaste versionen av ett paket om du inte anger en **RequiredVerion**.</span><span class="sxs-lookup"><span data-stu-id="26fa7-114">This cmdlet saves the newest version of a package unless you specify a **RequiredVerion**.</span></span> <span data-ttu-id="26fa7-115">**Sökvägen** och **LiteralPath** -parametrarna är ömsesidigt uteslutande och kan inte läggas till i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="26fa7-115">The **Path** and **LiteralPath** parameters are mutually exclusive, and cannot be added to the same command.</span></span>

## <span data-ttu-id="26fa7-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="26fa7-116">EXAMPLES</span></span>

### <span data-ttu-id="26fa7-117">Exempel 1: Spara ett paket på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="26fa7-117">Example 1: Save a package to the local computer</span></span>

<span data-ttu-id="26fa7-118">I det här exemplet sparas den nyaste versionen av paketet i en katalog på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="26fa7-118">This example saves the newest version of the package to a directory on the local computer.</span></span> <span data-ttu-id="26fa7-119">Paketets beroenden laddas ned med paketet.</span><span class="sxs-lookup"><span data-stu-id="26fa7-119">The package's dependencies are download with the package.</span></span>

```
PS> Save-Package -Name NuGet.Core -ProviderName NuGet -Path C:\LocalPkg
```

```Output
Name                    Version    Source    Summary
----                    -------    ------    -------
Microsoft.Web.Xdt       3.0.0      Nuget     Microsoft Xml Document Transformation (XDT) enables...
NuGet.Core              2.14.0     Nuget     NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="26fa7-120">`Save-Package` använder parametern **Name** för att ange paketet.</span><span class="sxs-lookup"><span data-stu-id="26fa7-120">`Save-Package` uses the **Name** parameter to specify the package.</span></span> <span data-ttu-id="26fa7-121">Paketet hämtas från den lagrings plats som anges av parametern **ProviderName** .</span><span class="sxs-lookup"><span data-stu-id="26fa7-121">The package is downloaded from the repository specified by the **ProviderName** parameter.</span></span> <span data-ttu-id="26fa7-122">Parametern **Path** bestämmer var paketet sparas.</span><span class="sxs-lookup"><span data-stu-id="26fa7-122">The **Path** parameter determines where the package is saved.</span></span>

### <span data-ttu-id="26fa7-123">Exempel 2: Spara en angiven paket version</span><span class="sxs-lookup"><span data-stu-id="26fa7-123">Example 2: Save a specific package version</span></span>

<span data-ttu-id="26fa7-124">I det här exemplet anges paket versionen och sparas i en katalog på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="26fa7-124">This example specifies the package version and saves it to a directory on the local computer.</span></span>

```
PS> Save-Package -Name NuGet.Core -RequiredVersion 2.9.0 -ProviderName NuGet -Path C:\LocalPkg
```

```Output
Name                    Version    Source    Summary
----                    -------    ------    -------
Microsoft.Web.Xdt       3.0.0      Nuget     Microsoft Xml Document Transformation (XDT) enables...
NuGet.Core              2.9.0      Nuget     NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="26fa7-125">`Save-Package` använder parametern **Name** för att ange paketet.</span><span class="sxs-lookup"><span data-stu-id="26fa7-125">`Save-Package` uses the **Name** parameter to specify the package.</span></span> <span data-ttu-id="26fa7-126">**RequiredVersion** anger en angiven paket version.</span><span class="sxs-lookup"><span data-stu-id="26fa7-126">**RequiredVersion** indicates a specific package version.</span></span> <span data-ttu-id="26fa7-127">Paketet hämtas från den lagrings plats som anges av parametern **ProviderName** .</span><span class="sxs-lookup"><span data-stu-id="26fa7-127">The package is downloaded from the repository specified by the **ProviderName** parameter.</span></span> <span data-ttu-id="26fa7-128">Parametern **Path** bestämmer var paketet sparas.</span><span class="sxs-lookup"><span data-stu-id="26fa7-128">The **Path** parameter determines where the package is saved.</span></span>

### <span data-ttu-id="26fa7-129">Exempel 3: använda Find-Package för att spara ett paket</span><span class="sxs-lookup"><span data-stu-id="26fa7-129">Example 3: Use Find-Package to save a package</span></span>

<span data-ttu-id="26fa7-130">Det här kommandot använder `Find-Package` för att hitta den senaste versionen av paketet och skicka objektet till `Save-Package` .</span><span class="sxs-lookup"><span data-stu-id="26fa7-130">This command uses `Find-Package` to locate the newest version of the package and sends the object to `Save-Package`.</span></span>

```
PS> Find-Package -Name NuGet.Core -ProviderName NuGet | Save-Package -Path C:\LocalPkg
```

<span data-ttu-id="26fa7-131">`Find-Package` använder parametern **Name** för att ange paketet.</span><span class="sxs-lookup"><span data-stu-id="26fa7-131">`Find-Package` uses the **Name** parameter to specify the package.</span></span> <span data-ttu-id="26fa7-132">Paketet hämtas från den lagrings plats som anges av parametern **ProviderName** .</span><span class="sxs-lookup"><span data-stu-id="26fa7-132">The package is downloaded from the repository specified by the **ProviderName** parameter.</span></span> <span data-ttu-id="26fa7-133">Objektet skickas ned pipelinen till `Save-Package` .</span><span class="sxs-lookup"><span data-stu-id="26fa7-133">The object is sent down the pipeline to `Save-Package`.</span></span> <span data-ttu-id="26fa7-134">Parametern **Path** bestämmer var paketet sparas.</span><span class="sxs-lookup"><span data-stu-id="26fa7-134">The **Path** parameter determines where the package is saved.</span></span>

### <span data-ttu-id="26fa7-135">Exempel 4: Spara och installera paketet</span><span class="sxs-lookup"><span data-stu-id="26fa7-135">Example 4: Save and install the package</span></span>

<span data-ttu-id="26fa7-136">Den senaste versionen av paketet och dess beroenden laddas ned och installeras på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="26fa7-136">The newest version of the package and its dependencies are downloaded and installed on the local computer.</span></span>

```
PS> Save-Package -Name NuGet.Core -ProviderName NuGet -Path C:\LocalPkg
PS> Install-Package C:\LocalPkg\NuGet.Core.2.14.0.nupkg
```

<span data-ttu-id="26fa7-137">`Save-Package` laddar ned paket filen och dess beroenden till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="26fa7-137">`Save-Package` downloads the package file and its dependencies to the local computer.</span></span>
<span data-ttu-id="26fa7-138">`Install-Package` installerar paketet och beroendena från den angivna katalogen.</span><span class="sxs-lookup"><span data-stu-id="26fa7-138">`Install-Package` installs the package and dependencies from the specified directory.</span></span>

## <span data-ttu-id="26fa7-139">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="26fa7-139">PARAMETERS</span></span>

### <span data-ttu-id="26fa7-140">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="26fa7-140">-AcceptLicense</span></span>

<span data-ttu-id="26fa7-141">Godkänn licens avtalet automatiskt under installationen om paketet kräver det.</span><span class="sxs-lookup"><span data-stu-id="26fa7-141">Automatically accept the license agreement during installation if the package requires it.</span></span>

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

### <span data-ttu-id="26fa7-142">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="26fa7-142">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="26fa7-143">Tillåter att paket som marker ATS som för hands version sparas.</span><span class="sxs-lookup"><span data-stu-id="26fa7-143">Allows packages marked as Prerelease to be saved.</span></span>

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

### <span data-ttu-id="26fa7-144">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="26fa7-144">-AllVersions</span></span>

<span data-ttu-id="26fa7-145">Anger att denna cmdlet sparar alla tillgängliga versioner av paketet.</span><span class="sxs-lookup"><span data-stu-id="26fa7-145">Indicates that this cmdlet saves all available versions of the package.</span></span>

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

### <span data-ttu-id="26fa7-146">-Kommando</span><span class="sxs-lookup"><span data-stu-id="26fa7-146">-Command</span></span>

<span data-ttu-id="26fa7-147">Anger ett eller flera kommandon som ingår i paketet.</span><span class="sxs-lookup"><span data-stu-id="26fa7-147">Specifies one or more commands included in the package.</span></span>

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

### <span data-ttu-id="26fa7-148">– ConfigFile</span><span class="sxs-lookup"><span data-stu-id="26fa7-148">-ConfigFile</span></span>

<span data-ttu-id="26fa7-149">Anger en konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="26fa7-149">Specifies a configuration File.</span></span>

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

### <span data-ttu-id="26fa7-150">– Innehåller</span><span class="sxs-lookup"><span data-stu-id="26fa7-150">-Contains</span></span>

<span data-ttu-id="26fa7-151">`Save-Package` hämtar objekt om ett objekt i objektets egenskaps värden är en exakt matchning för det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="26fa7-151">`Save-Package` gets objects if any item in the object's property values are an exact match for the specified value.</span></span>

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

### <span data-ttu-id="26fa7-152">-Credential</span><span class="sxs-lookup"><span data-stu-id="26fa7-152">-Credential</span></span>

<span data-ttu-id="26fa7-153">Anger ett användar konto som har behörighet att spara ett paket från en angiven paket leverantör eller källa.</span><span class="sxs-lookup"><span data-stu-id="26fa7-153">Specifies a user account that has permission to save a package from a specified package provider or source.</span></span>

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

### <span data-ttu-id="26fa7-154">– Dscresource Keyword Supports</span><span class="sxs-lookup"><span data-stu-id="26fa7-154">-DscResource</span></span>

<span data-ttu-id="26fa7-155">Anger en eller flera DSC-resurser (Desired State Configuration) för paketet.</span><span class="sxs-lookup"><span data-stu-id="26fa7-155">Specifies one or more Desired State Configuration (DSC) resources for the package.</span></span>

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

### <span data-ttu-id="26fa7-156">-Filter</span><span class="sxs-lookup"><span data-stu-id="26fa7-156">-Filter</span></span>

<span data-ttu-id="26fa7-157">Anger ett filter för paketet.</span><span class="sxs-lookup"><span data-stu-id="26fa7-157">Specifies a filter for the package.</span></span>

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

### <span data-ttu-id="26fa7-158">-FilterOnTag</span><span class="sxs-lookup"><span data-stu-id="26fa7-158">-FilterOnTag</span></span>

<span data-ttu-id="26fa7-159">Anger taggen som filtrerar resultaten.</span><span class="sxs-lookup"><span data-stu-id="26fa7-159">Specifies the tag that filters the results.</span></span> <span data-ttu-id="26fa7-160">Resultat som inte innehåller den angivna taggen utesluts.</span><span class="sxs-lookup"><span data-stu-id="26fa7-160">Results that don't contain the specified tag are excluded.</span></span>

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

### <span data-ttu-id="26fa7-161">-Force</span><span class="sxs-lookup"><span data-stu-id="26fa7-161">-Force</span></span>

<span data-ttu-id="26fa7-162">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="26fa7-162">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="26fa7-163">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="26fa7-163">-ForceBootstrap</span></span>

<span data-ttu-id="26fa7-164">Indikerar att `Save-Package` tvingar **PackageManagement** att automatiskt installera paket leverantören för det angivna paketet.</span><span class="sxs-lookup"><span data-stu-id="26fa7-164">Indicates that `Save-Package` forces **PackageManagement** to automatically install the package provider for the specified package.</span></span>

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

### <span data-ttu-id="26fa7-165">– Sidhuvud</span><span class="sxs-lookup"><span data-stu-id="26fa7-165">-Headers</span></span>

<span data-ttu-id="26fa7-166">Anger sidhuvuden för paketet.</span><span class="sxs-lookup"><span data-stu-id="26fa7-166">Specifies the headers for the package.</span></span>

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

### <span data-ttu-id="26fa7-167">– Innehåller</span><span class="sxs-lookup"><span data-stu-id="26fa7-167">-Includes</span></span>

<span data-ttu-id="26fa7-168">Anger vilka resurser som paketet innehåller.</span><span class="sxs-lookup"><span data-stu-id="26fa7-168">Indicates the resources that the package includes.</span></span>

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

### <span data-ttu-id="26fa7-169">– InputObject</span><span class="sxs-lookup"><span data-stu-id="26fa7-169">-InputObject</span></span>

<span data-ttu-id="26fa7-170">Ett program-ID-objekt som representerar det paket som du vill spara.</span><span class="sxs-lookup"><span data-stu-id="26fa7-170">A software ID object that represents the package that you want to save.</span></span> <span data-ttu-id="26fa7-171">Program-ID: n ingår i resultatet av `Find-Package` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="26fa7-171">Software IDs are part of the results of the `Find-Package` cmdlet.</span></span>

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

### <span data-ttu-id="26fa7-172">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="26fa7-172">-LiteralPath</span></span>

<span data-ttu-id="26fa7-173">Anger den litterala sökvägen till vilken du vill spara paketet.</span><span class="sxs-lookup"><span data-stu-id="26fa7-173">Specifies the literal path to which you want to save the package.</span></span> <span data-ttu-id="26fa7-174">Du kan inte lägga till både den här parametern och parametern **Path** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="26fa7-174">You cannot add both this parameter and the **Path** parameter to the same command.</span></span>

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

### <span data-ttu-id="26fa7-175">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="26fa7-175">-MaximumVersion</span></span>

<span data-ttu-id="26fa7-176">Anger den högsta versionen av paketet som du vill spara.</span><span class="sxs-lookup"><span data-stu-id="26fa7-176">Specifies the maximum version of the package that you want to save.</span></span>

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

### <span data-ttu-id="26fa7-177">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="26fa7-177">-MinimumVersion</span></span>

<span data-ttu-id="26fa7-178">Anger den lägsta version av paketet som du vill hitta.</span><span class="sxs-lookup"><span data-stu-id="26fa7-178">Specifies the minimum version of the package that you want to find.</span></span>

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

### <span data-ttu-id="26fa7-179">-Name</span><span class="sxs-lookup"><span data-stu-id="26fa7-179">-Name</span></span>

<span data-ttu-id="26fa7-180">Anger ett eller flera paket namn.</span><span class="sxs-lookup"><span data-stu-id="26fa7-180">Specifies one or more package names.</span></span>

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

### <span data-ttu-id="26fa7-181">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="26fa7-181">-PackageManagementProvider</span></span>

<span data-ttu-id="26fa7-182">Anger en paket hanterings leverantör.</span><span class="sxs-lookup"><span data-stu-id="26fa7-182">Specifies a package management provider.</span></span>

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

### <span data-ttu-id="26fa7-183">-Path</span><span class="sxs-lookup"><span data-stu-id="26fa7-183">-Path</span></span>

<span data-ttu-id="26fa7-184">Anger platsen på den lokala datorn där paketet ska lagras.</span><span class="sxs-lookup"><span data-stu-id="26fa7-184">Specifies the location on the local computer to store the package.</span></span>

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

### <span data-ttu-id="26fa7-185">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="26fa7-185">-ProviderName</span></span>

<span data-ttu-id="26fa7-186">Anger ett eller flera providernamn.</span><span class="sxs-lookup"><span data-stu-id="26fa7-186">Specifies one or more provider names.</span></span>

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

### <span data-ttu-id="26fa7-187">-Proxy</span><span class="sxs-lookup"><span data-stu-id="26fa7-187">-Proxy</span></span>

<span data-ttu-id="26fa7-188">Anger en proxyserver för begäran, i stället för en direkt anslutning till Internet resursen.</span><span class="sxs-lookup"><span data-stu-id="26fa7-188">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="26fa7-189">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="26fa7-189">-ProxyCredential</span></span>

<span data-ttu-id="26fa7-190">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="26fa7-190">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="26fa7-191">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="26fa7-191">-PublishLocation</span></span>

<span data-ttu-id="26fa7-192">Anger publicerings platsen.</span><span class="sxs-lookup"><span data-stu-id="26fa7-192">Specifies the publish location.</span></span>

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

### <span data-ttu-id="26fa7-193">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="26fa7-193">-RequiredVersion</span></span>

<span data-ttu-id="26fa7-194">Anger den exakta versionen av paketet som ska sparas.</span><span class="sxs-lookup"><span data-stu-id="26fa7-194">Specifies the exact version of the package to save.</span></span>

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

### <span data-ttu-id="26fa7-195">-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="26fa7-195">-RoleCapability</span></span>

<span data-ttu-id="26fa7-196">Anger en matris med roll funktioner.</span><span class="sxs-lookup"><span data-stu-id="26fa7-196">Specifies an array of role capabilities.</span></span>

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

### <span data-ttu-id="26fa7-197">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="26fa7-197">-ScriptPublishLocation</span></span>

<span data-ttu-id="26fa7-198">Anger skriptets publicerings plats.</span><span class="sxs-lookup"><span data-stu-id="26fa7-198">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="26fa7-199">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="26fa7-199">-ScriptSourceLocation</span></span>

<span data-ttu-id="26fa7-200">Anger sökvägen till skript källan.</span><span class="sxs-lookup"><span data-stu-id="26fa7-200">Specifies the script source location.</span></span>

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

### <span data-ttu-id="26fa7-201">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="26fa7-201">-SkipValidate</span></span>

<span data-ttu-id="26fa7-202">Växel som hoppar över verifiering av autentiseringsuppgifterna för ett paket.</span><span class="sxs-lookup"><span data-stu-id="26fa7-202">Switch that skips validating the credentials of a package.</span></span>

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

### <span data-ttu-id="26fa7-203">-Source</span><span class="sxs-lookup"><span data-stu-id="26fa7-203">-Source</span></span>

<span data-ttu-id="26fa7-204">Anger en eller flera paket källor.</span><span class="sxs-lookup"><span data-stu-id="26fa7-204">Specifies one or more package sources.</span></span>

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

### <span data-ttu-id="26fa7-205">-Tagga</span><span class="sxs-lookup"><span data-stu-id="26fa7-205">-Tag</span></span>

<span data-ttu-id="26fa7-206">Anger en tagg att söka efter inom paketets metadata.</span><span class="sxs-lookup"><span data-stu-id="26fa7-206">Specifies a tag to search for within the package metadata.</span></span>

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

### <span data-ttu-id="26fa7-207">-Typ</span><span class="sxs-lookup"><span data-stu-id="26fa7-207">-Type</span></span>

<span data-ttu-id="26fa7-208">Anger om du vill söka efter paket med en modul, ett skript eller något av alternativen.</span><span class="sxs-lookup"><span data-stu-id="26fa7-208">Specifies whether to search for packages with a module, a script, or either.</span></span>

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

### <span data-ttu-id="26fa7-209">-Confirm</span><span class="sxs-lookup"><span data-stu-id="26fa7-209">-Confirm</span></span>

<span data-ttu-id="26fa7-210">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="26fa7-210">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="26fa7-211">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="26fa7-211">-WhatIf</span></span>

<span data-ttu-id="26fa7-212">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="26fa7-212">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="26fa7-213">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="26fa7-213">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="26fa7-214">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="26fa7-214">CommonParameters</span></span>

<span data-ttu-id="26fa7-215">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="26fa7-215">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="26fa7-216">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="26fa7-216">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="26fa7-217">INDATA</span><span class="sxs-lookup"><span data-stu-id="26fa7-217">INPUTS</span></span>

### <span data-ttu-id="26fa7-218">`Save-Package` accepterar objekt från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="26fa7-218">`Save-Package` accepts objects from the pipeline.</span></span>

## <span data-ttu-id="26fa7-219">UTDATA</span><span class="sxs-lookup"><span data-stu-id="26fa7-219">OUTPUTS</span></span>

### <span data-ttu-id="26fa7-220">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="26fa7-220">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="26fa7-221">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="26fa7-221">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="26fa7-222">Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1.</span><span class="sxs-lookup"><span data-stu-id="26fa7-222">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="26fa7-223">Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="26fa7-223">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="26fa7-224">Använd följande kommando för att se till att du använder TLS 1,2:</span><span class="sxs-lookup"><span data-stu-id="26fa7-224">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="26fa7-225">Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="26fa7-225">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="26fa7-226">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="26fa7-226">RELATED LINKS</span></span>

[<span data-ttu-id="26fa7-227">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="26fa7-227">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="26fa7-228">Get-Package</span><span class="sxs-lookup"><span data-stu-id="26fa7-228">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="26fa7-229">Installationspaket</span><span class="sxs-lookup"><span data-stu-id="26fa7-229">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="26fa7-230">Spara paket</span><span class="sxs-lookup"><span data-stu-id="26fa7-230">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="26fa7-231">Avinstallera paket</span><span class="sxs-lookup"><span data-stu-id="26fa7-231">Uninstall-Package</span></span>](Uninstall-Package.md)
