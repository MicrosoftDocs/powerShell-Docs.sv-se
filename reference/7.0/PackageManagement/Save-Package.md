---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 04/03/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/save-package?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Save-Package
ms.openlocfilehash: b46bf983120a71a530fdc9715b68eff0b1ce3af6
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892730"
---
# <span data-ttu-id="4e392-103">Save-Package</span><span class="sxs-lookup"><span data-stu-id="4e392-103">Save-Package</span></span>

## <span data-ttu-id="4e392-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="4e392-104">SYNOPSIS</span></span>
<span data-ttu-id="4e392-105">Sparar paket på den lokala datorn utan att installera dem.</span><span class="sxs-lookup"><span data-stu-id="4e392-105">Saves packages to the local computer without installing them.</span></span>

## <span data-ttu-id="4e392-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4e392-106">SYNTAX</span></span>

### <span data-ttu-id="4e392-107">PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="4e392-107">PackageBySearch</span></span>

```
Save-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Source <String[]>] [-Path <String>] [-LiteralPath <String>]
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllVersions]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="4e392-108">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="4e392-108">PackageByInputObject</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] -InputObject <SoftwareIdentity>
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-AllVersions]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="4e392-109">NuGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="4e392-109">NuGet:PackageByInputObject</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ConfigFile <String>] [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>]
 [-Contains <String>] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="4e392-110">NuGet</span><span class="sxs-lookup"><span data-stu-id="4e392-110">NuGet</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ConfigFile <String>] [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>]
 [-Contains <String>] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="4e392-111">PowerShellGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="4e392-111">PowerShellGet:PackageByInputObject</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-AllowPrereleaseVersions] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [<CommonParameters>]
```

### <span data-ttu-id="4e392-112">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="4e392-112">PowerShellGet</span></span>

```
Save-Package [-Path <String>] [-LiteralPath <String>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-AllowPrereleaseVersions] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [<CommonParameters>]
```

## <span data-ttu-id="4e392-113">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="4e392-113">DESCRIPTION</span></span>

<span data-ttu-id="4e392-114">`Save-Package`Cmdleten sparar paket på den lokala datorn men installerar inte paketen.</span><span class="sxs-lookup"><span data-stu-id="4e392-114">The `Save-Package` cmdlet saves packages to the local computer but doesn't install the packages.</span></span>
<span data-ttu-id="4e392-115">Denna cmdlet sparar den senaste versionen av ett paket om du inte anger en **RequiredVerion**.</span><span class="sxs-lookup"><span data-stu-id="4e392-115">This cmdlet saves the newest version of a package unless you specify a **RequiredVerion**.</span></span> <span data-ttu-id="4e392-116">**Sökvägen** och **LiteralPath** -parametrarna är ömsesidigt uteslutande och kan inte läggas till i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="4e392-116">The **Path** and **LiteralPath** parameters are mutually exclusive, and cannot be added to the same command.</span></span>

## <span data-ttu-id="4e392-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="4e392-117">EXAMPLES</span></span>

### <span data-ttu-id="4e392-118">Exempel 1: Spara ett paket på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="4e392-118">Example 1: Save a package to the local computer</span></span>

<span data-ttu-id="4e392-119">I det här exemplet sparas den nyaste versionen av paketet i en katalog på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="4e392-119">This example saves the newest version of the package to a directory on the local computer.</span></span> <span data-ttu-id="4e392-120">Paketets beroenden laddas ned med paketet.</span><span class="sxs-lookup"><span data-stu-id="4e392-120">The package's dependencies are download with the package.</span></span>

```
PS> Save-Package -Name NuGet.Core -ProviderName NuGet -Path C:\LocalPkg
```

```Output
Name                    Version    Source    Summary
----                    -------    ------    -------
Microsoft.Web.Xdt       3.0.0      Nuget     Microsoft Xml Document Transformation (XDT) enables...
NuGet.Core              2.14.0     Nuget     NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="4e392-121">`Save-Package` använder parametern **Name** för att ange paketet.</span><span class="sxs-lookup"><span data-stu-id="4e392-121">`Save-Package` uses the **Name** parameter to specify the package.</span></span> <span data-ttu-id="4e392-122">Paketet hämtas från den lagrings plats som anges av parametern **ProviderName** .</span><span class="sxs-lookup"><span data-stu-id="4e392-122">The package is downloaded from the repository specified by the **ProviderName** parameter.</span></span> <span data-ttu-id="4e392-123">Parametern **Path** bestämmer var paketet sparas.</span><span class="sxs-lookup"><span data-stu-id="4e392-123">The **Path** parameter determines where the package is saved.</span></span>

### <span data-ttu-id="4e392-124">Exempel 2: Spara en angiven paket version</span><span class="sxs-lookup"><span data-stu-id="4e392-124">Example 2: Save a specific package version</span></span>

<span data-ttu-id="4e392-125">I det här exemplet anges paket versionen och sparas i en katalog på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="4e392-125">This example specifies the package version and saves it to a directory on the local computer.</span></span>

```
PS> Save-Package -Name NuGet.Core -RequiredVersion 2.9.0 -ProviderName NuGet -Path C:\LocalPkg
```

```Output
Name                    Version    Source    Summary
----                    -------    ------    -------
Microsoft.Web.Xdt       3.0.0      Nuget     Microsoft Xml Document Transformation (XDT) enables...
NuGet.Core              2.9.0      Nuget     NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="4e392-126">`Save-Package` använder parametern **Name** för att ange paketet.</span><span class="sxs-lookup"><span data-stu-id="4e392-126">`Save-Package` uses the **Name** parameter to specify the package.</span></span> <span data-ttu-id="4e392-127">**RequiredVersion** anger en angiven paket version.</span><span class="sxs-lookup"><span data-stu-id="4e392-127">**RequiredVersion** indicates a specific package version.</span></span> <span data-ttu-id="4e392-128">Paketet hämtas från den lagrings plats som anges av parametern **ProviderName** .</span><span class="sxs-lookup"><span data-stu-id="4e392-128">The package is downloaded from the repository specified by the **ProviderName** parameter.</span></span> <span data-ttu-id="4e392-129">Parametern **Path** bestämmer var paketet sparas.</span><span class="sxs-lookup"><span data-stu-id="4e392-129">The **Path** parameter determines where the package is saved.</span></span>

### <span data-ttu-id="4e392-130">Exempel 3: använda Find-Package för att spara ett paket</span><span class="sxs-lookup"><span data-stu-id="4e392-130">Example 3: Use Find-Package to save a package</span></span>

<span data-ttu-id="4e392-131">Det här kommandot använder `Find-Package` för att hitta den senaste versionen av paketet och skicka objektet till `Save-Package` .</span><span class="sxs-lookup"><span data-stu-id="4e392-131">This command uses `Find-Package` to locate the newest version of the package and sends the object to `Save-Package`.</span></span>

```
PS> Find-Package -Name NuGet.Core -ProviderName NuGet | Save-Package -Path C:\LocalPkg
```

<span data-ttu-id="4e392-132">`Find-Package` använder parametern **Name** för att ange paketet.</span><span class="sxs-lookup"><span data-stu-id="4e392-132">`Find-Package` uses the **Name** parameter to specify the package.</span></span> <span data-ttu-id="4e392-133">Paketet hämtas från den lagrings plats som anges av parametern **ProviderName** .</span><span class="sxs-lookup"><span data-stu-id="4e392-133">The package is downloaded from the repository specified by the **ProviderName** parameter.</span></span> <span data-ttu-id="4e392-134">Objektet skickas ned pipelinen till `Save-Package` .</span><span class="sxs-lookup"><span data-stu-id="4e392-134">The object is sent down the pipeline to `Save-Package`.</span></span> <span data-ttu-id="4e392-135">Parametern **Path** bestämmer var paketet sparas.</span><span class="sxs-lookup"><span data-stu-id="4e392-135">The **Path** parameter determines where the package is saved.</span></span>

### <span data-ttu-id="4e392-136">Exempel 4: Spara och installera paketet</span><span class="sxs-lookup"><span data-stu-id="4e392-136">Example 4: Save and install the package</span></span>

<span data-ttu-id="4e392-137">Den senaste versionen av paketet och dess beroenden laddas ned och installeras på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="4e392-137">The newest version of the package and its dependencies are downloaded and installed on the local computer.</span></span>

```
PS> Save-Package -Name NuGet.Core -ProviderName NuGet -Path C:\LocalPkg
PS> Install-Package C:\LocalPkg\NuGet.Core.2.14.0.nupkg
```

<span data-ttu-id="4e392-138">`Save-Package` laddar ned paket filen och dess beroenden till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="4e392-138">`Save-Package` downloads the package file and its dependencies to the local computer.</span></span>
<span data-ttu-id="4e392-139">`Install-Package` installerar paketet och beroendena från den angivna katalogen.</span><span class="sxs-lookup"><span data-stu-id="4e392-139">`Install-Package` installs the package and dependencies from the specified directory.</span></span>

## <span data-ttu-id="4e392-140">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="4e392-140">PARAMETERS</span></span>

### <span data-ttu-id="4e392-141">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="4e392-141">-AcceptLicense</span></span>

<span data-ttu-id="4e392-142">Godkänn licens avtalet automatiskt under installationen om paketet kräver det.</span><span class="sxs-lookup"><span data-stu-id="4e392-142">Automatically accept the license agreement during installation if the package requires it.</span></span>

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

### <span data-ttu-id="4e392-143">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="4e392-143">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="4e392-144">Tillåter att paket som marker ATS som för hands version sparas.</span><span class="sxs-lookup"><span data-stu-id="4e392-144">Allows packages marked as Prerelease to be saved.</span></span>

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

### <span data-ttu-id="4e392-145">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="4e392-145">-AllVersions</span></span>

<span data-ttu-id="4e392-146">Anger att denna cmdlet sparar alla tillgängliga versioner av paketet.</span><span class="sxs-lookup"><span data-stu-id="4e392-146">Indicates that this cmdlet saves all available versions of the package.</span></span>

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

### <span data-ttu-id="4e392-147">-Kommando</span><span class="sxs-lookup"><span data-stu-id="4e392-147">-Command</span></span>

<span data-ttu-id="4e392-148">Anger ett eller flera kommandon som ingår i paketet.</span><span class="sxs-lookup"><span data-stu-id="4e392-148">Specifies one or more commands included in the package.</span></span>

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

### <span data-ttu-id="4e392-149">– ConfigFile</span><span class="sxs-lookup"><span data-stu-id="4e392-149">-ConfigFile</span></span>

<span data-ttu-id="4e392-150">Anger en konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="4e392-150">Specifies a configuration File.</span></span>

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

### <span data-ttu-id="4e392-151">– Innehåller</span><span class="sxs-lookup"><span data-stu-id="4e392-151">-Contains</span></span>

<span data-ttu-id="4e392-152">`Save-Package` hämtar objekt om ett objekt i objektets egenskaps värden är en exakt matchning för det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="4e392-152">`Save-Package` gets objects if any item in the object's property values are an exact match for the specified value.</span></span>

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

### <span data-ttu-id="4e392-153">-Credential</span><span class="sxs-lookup"><span data-stu-id="4e392-153">-Credential</span></span>

<span data-ttu-id="4e392-154">Anger ett användar konto som har behörighet att spara ett paket från en angiven paket leverantör eller källa.</span><span class="sxs-lookup"><span data-stu-id="4e392-154">Specifies a user account that has permission to save a package from a specified package provider or source.</span></span>

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

### <span data-ttu-id="4e392-155">– Dscresource Keyword Supports</span><span class="sxs-lookup"><span data-stu-id="4e392-155">-DscResource</span></span>

<span data-ttu-id="4e392-156">Anger en eller flera DSC-resurser (Desired State Configuration) för paketet.</span><span class="sxs-lookup"><span data-stu-id="4e392-156">Specifies one or more Desired State Configuration (DSC) resources for the package.</span></span>

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

### <span data-ttu-id="4e392-157">-Filter</span><span class="sxs-lookup"><span data-stu-id="4e392-157">-Filter</span></span>

<span data-ttu-id="4e392-158">Anger ett filter för paketet.</span><span class="sxs-lookup"><span data-stu-id="4e392-158">Specifies a filter for the package.</span></span>

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

### <span data-ttu-id="4e392-159">-FilterOnTag</span><span class="sxs-lookup"><span data-stu-id="4e392-159">-FilterOnTag</span></span>

<span data-ttu-id="4e392-160">Anger taggen som filtrerar resultaten.</span><span class="sxs-lookup"><span data-stu-id="4e392-160">Specifies the tag that filters the results.</span></span> <span data-ttu-id="4e392-161">Resultat som inte innehåller den angivna taggen utesluts.</span><span class="sxs-lookup"><span data-stu-id="4e392-161">Results that don't contain the specified tag are excluded.</span></span>

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

### <span data-ttu-id="4e392-162">-Force</span><span class="sxs-lookup"><span data-stu-id="4e392-162">-Force</span></span>

<span data-ttu-id="4e392-163">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="4e392-163">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="4e392-164">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="4e392-164">-ForceBootstrap</span></span>

<span data-ttu-id="4e392-165">Indikerar att `Save-Package` tvingar **PackageManagement** att automatiskt installera paket leverantören för det angivna paketet.</span><span class="sxs-lookup"><span data-stu-id="4e392-165">Indicates that `Save-Package` forces **PackageManagement** to automatically install the package provider for the specified package.</span></span>

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

### <span data-ttu-id="4e392-166">– Sidhuvud</span><span class="sxs-lookup"><span data-stu-id="4e392-166">-Headers</span></span>

<span data-ttu-id="4e392-167">Anger sidhuvuden för paketet.</span><span class="sxs-lookup"><span data-stu-id="4e392-167">Specifies the headers for the package.</span></span>

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

### <span data-ttu-id="4e392-168">– Innehåller</span><span class="sxs-lookup"><span data-stu-id="4e392-168">-Includes</span></span>

<span data-ttu-id="4e392-169">Anger vilka resurser som paketet innehåller.</span><span class="sxs-lookup"><span data-stu-id="4e392-169">Indicates the resources that the package includes.</span></span>

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

### <span data-ttu-id="4e392-170">– InputObject</span><span class="sxs-lookup"><span data-stu-id="4e392-170">-InputObject</span></span>

<span data-ttu-id="4e392-171">Ett program-ID-objekt som representerar det paket som du vill spara.</span><span class="sxs-lookup"><span data-stu-id="4e392-171">A software ID object that represents the package that you want to save.</span></span> <span data-ttu-id="4e392-172">Program-ID: n ingår i resultatet av `Find-Package` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4e392-172">Software IDs are part of the results of the `Find-Package` cmdlet.</span></span>

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

### <span data-ttu-id="4e392-173">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="4e392-173">-LiteralPath</span></span>

<span data-ttu-id="4e392-174">Anger den litterala sökvägen till vilken du vill spara paketet.</span><span class="sxs-lookup"><span data-stu-id="4e392-174">Specifies the literal path to which you want to save the package.</span></span> <span data-ttu-id="4e392-175">Du kan inte lägga till både den här parametern och parametern **Path** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="4e392-175">You cannot add both this parameter and the **Path** parameter to the same command.</span></span>

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

### <span data-ttu-id="4e392-176">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="4e392-176">-MaximumVersion</span></span>

<span data-ttu-id="4e392-177">Anger den högsta versionen av paketet som du vill spara.</span><span class="sxs-lookup"><span data-stu-id="4e392-177">Specifies the maximum version of the package that you want to save.</span></span>

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

### <span data-ttu-id="4e392-178">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="4e392-178">-MinimumVersion</span></span>

<span data-ttu-id="4e392-179">Anger den lägsta version av paketet som du vill hitta.</span><span class="sxs-lookup"><span data-stu-id="4e392-179">Specifies the minimum version of the package that you want to find.</span></span>

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

### <span data-ttu-id="4e392-180">-Name</span><span class="sxs-lookup"><span data-stu-id="4e392-180">-Name</span></span>

<span data-ttu-id="4e392-181">Anger ett eller flera paket namn.</span><span class="sxs-lookup"><span data-stu-id="4e392-181">Specifies one or more package names.</span></span>

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

### <span data-ttu-id="4e392-182">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="4e392-182">-PackageManagementProvider</span></span>

<span data-ttu-id="4e392-183">Anger en paket hanterings leverantör.</span><span class="sxs-lookup"><span data-stu-id="4e392-183">Specifies a package management provider.</span></span>

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

### <span data-ttu-id="4e392-184">-Path</span><span class="sxs-lookup"><span data-stu-id="4e392-184">-Path</span></span>

<span data-ttu-id="4e392-185">Anger platsen på den lokala datorn där paketet ska lagras.</span><span class="sxs-lookup"><span data-stu-id="4e392-185">Specifies the location on the local computer to store the package.</span></span>

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

### <span data-ttu-id="4e392-186">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="4e392-186">-ProviderName</span></span>

<span data-ttu-id="4e392-187">Anger ett eller flera providernamn.</span><span class="sxs-lookup"><span data-stu-id="4e392-187">Specifies one or more provider names.</span></span>

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

### <span data-ttu-id="4e392-188">-Proxy</span><span class="sxs-lookup"><span data-stu-id="4e392-188">-Proxy</span></span>

<span data-ttu-id="4e392-189">Anger en proxyserver för begäran, i stället för en direkt anslutning till Internet resursen.</span><span class="sxs-lookup"><span data-stu-id="4e392-189">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="4e392-190">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="4e392-190">-ProxyCredential</span></span>

<span data-ttu-id="4e392-191">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="4e392-191">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="4e392-192">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="4e392-192">-PublishLocation</span></span>

<span data-ttu-id="4e392-193">Anger publicerings platsen.</span><span class="sxs-lookup"><span data-stu-id="4e392-193">Specifies the publish location.</span></span>

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

### <span data-ttu-id="4e392-194">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="4e392-194">-RequiredVersion</span></span>

<span data-ttu-id="4e392-195">Anger den exakta versionen av paketet som ska sparas.</span><span class="sxs-lookup"><span data-stu-id="4e392-195">Specifies the exact version of the package to save.</span></span>

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

### <span data-ttu-id="4e392-196">-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="4e392-196">-RoleCapability</span></span>

<span data-ttu-id="4e392-197">Anger en matris med roll funktioner.</span><span class="sxs-lookup"><span data-stu-id="4e392-197">Specifies an array of role capabilities.</span></span>

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

### <span data-ttu-id="4e392-198">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="4e392-198">-ScriptPublishLocation</span></span>

<span data-ttu-id="4e392-199">Anger skriptets publicerings plats.</span><span class="sxs-lookup"><span data-stu-id="4e392-199">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="4e392-200">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="4e392-200">-ScriptSourceLocation</span></span>

<span data-ttu-id="4e392-201">Anger sökvägen till skript källan.</span><span class="sxs-lookup"><span data-stu-id="4e392-201">Specifies the script source location.</span></span>

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

### <span data-ttu-id="4e392-202">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="4e392-202">-SkipValidate</span></span>

<span data-ttu-id="4e392-203">Växel som hoppar över verifiering av autentiseringsuppgifterna för ett paket.</span><span class="sxs-lookup"><span data-stu-id="4e392-203">Switch that skips validating the credentials of a package.</span></span>

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

### <span data-ttu-id="4e392-204">-Source</span><span class="sxs-lookup"><span data-stu-id="4e392-204">-Source</span></span>

<span data-ttu-id="4e392-205">Anger en eller flera paket källor.</span><span class="sxs-lookup"><span data-stu-id="4e392-205">Specifies one or more package sources.</span></span>

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

### <span data-ttu-id="4e392-206">-Tagga</span><span class="sxs-lookup"><span data-stu-id="4e392-206">-Tag</span></span>

<span data-ttu-id="4e392-207">Anger en tagg att söka efter inom paketets metadata.</span><span class="sxs-lookup"><span data-stu-id="4e392-207">Specifies a tag to search for within the package metadata.</span></span>

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

### <span data-ttu-id="4e392-208">-Typ</span><span class="sxs-lookup"><span data-stu-id="4e392-208">-Type</span></span>

<span data-ttu-id="4e392-209">Anger om du vill söka efter paket med en modul, ett skript eller något av alternativen.</span><span class="sxs-lookup"><span data-stu-id="4e392-209">Specifies whether to search for packages with a module, a script, or either.</span></span>

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

### <span data-ttu-id="4e392-210">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4e392-210">-Confirm</span></span>

<span data-ttu-id="4e392-211">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4e392-211">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="4e392-212">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4e392-212">-WhatIf</span></span>

<span data-ttu-id="4e392-213">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="4e392-213">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="4e392-214">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="4e392-214">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="4e392-215">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4e392-215">CommonParameters</span></span>

<span data-ttu-id="4e392-216">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4e392-216">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4e392-217">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4e392-217">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4e392-218">INDATA</span><span class="sxs-lookup"><span data-stu-id="4e392-218">INPUTS</span></span>

### <span data-ttu-id="4e392-219">`Save-Package` accepterar objekt från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="4e392-219">`Save-Package` accepts objects from the pipeline.</span></span>

## <span data-ttu-id="4e392-220">UTDATA</span><span class="sxs-lookup"><span data-stu-id="4e392-220">OUTPUTS</span></span>

### <span data-ttu-id="4e392-221">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="4e392-221">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="4e392-222">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="4e392-222">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4e392-223">Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1.</span><span class="sxs-lookup"><span data-stu-id="4e392-223">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="4e392-224">Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="4e392-224">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="4e392-225">Använd följande kommando för att se till att du använder TLS 1,2:</span><span class="sxs-lookup"><span data-stu-id="4e392-225">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="4e392-226">Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="4e392-226">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="4e392-227">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="4e392-227">RELATED LINKS</span></span>

[<span data-ttu-id="4e392-228">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="4e392-228">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="4e392-229">Get-Package</span><span class="sxs-lookup"><span data-stu-id="4e392-229">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="4e392-230">Installationspaket</span><span class="sxs-lookup"><span data-stu-id="4e392-230">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="4e392-231">Spara paket</span><span class="sxs-lookup"><span data-stu-id="4e392-231">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="4e392-232">Avinstallera paket</span><span class="sxs-lookup"><span data-stu-id="4e392-232">Uninstall-Package</span></span>](Uninstall-Package.md)
