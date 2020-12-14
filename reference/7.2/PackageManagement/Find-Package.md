---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 04/03/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/find-package?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Package
ms.openlocfilehash: c45ff8443818580dcc57cd1a945822007ae259a8
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889631"
---
# <span data-ttu-id="5d5ea-102">Find-Package</span><span class="sxs-lookup"><span data-stu-id="5d5ea-102">Find-Package</span></span>

## <span data-ttu-id="5d5ea-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="5d5ea-103">SYNOPSIS</span></span>
<span data-ttu-id="5d5ea-104">Söker efter program varu paket i tillgängliga paket källor.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-104">Finds software packages in available package sources.</span></span>

## <span data-ttu-id="5d5ea-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5d5ea-105">SYNTAX</span></span>

### <span data-ttu-id="5d5ea-106">NuGet</span><span class="sxs-lookup"><span data-stu-id="5d5ea-106">NuGet</span></span>

```
Find-Package [-IncludeDependencies] [-AllVersions] [-Source <String[]>] [-Credential <PSCredential>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [[-Name] <String[]>] [-RequiredVersion <String>]
 [-MinimumVersion <String>] [-MaximumVersion <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-ConfigFile <String>] [-SkipValidate] [-Headers <String[]>]
 [-FilterOnTag <String[]>] [-Contains <String>] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="5d5ea-107">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="5d5ea-107">PowerShellGet</span></span>

```
Find-Package [-IncludeDependencies] [-AllVersions] [-Source <String[]>] [-Credential <PSCredential>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [[-Name] <String[]>] [-RequiredVersion <String>]
 [-MinimumVersion <String>] [-MaximumVersion <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-AllowPrereleaseVersions] [-PackageManagementProvider <String>]
 [-PublishLocation <String>] [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>]
 [-Type <String>] [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>]
 [-DscResource <String[]>] [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense]
 [<CommonParameters>]
```

## <span data-ttu-id="5d5ea-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="5d5ea-108">DESCRIPTION</span></span>

<span data-ttu-id="5d5ea-109">`Find-Package` söker efter program varu paket som är tillgängliga i paket källor.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-109">`Find-Package` finds software packages that are available in package sources.</span></span> <span data-ttu-id="5d5ea-110">`Get-PackageProvider` och `Get-PackageSource` Visa information om dina leverantörer.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-110">`Get-PackageProvider` and `Get-PackageSource` display details about your providers.</span></span>

## <span data-ttu-id="5d5ea-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="5d5ea-111">EXAMPLES</span></span>

### <span data-ttu-id="5d5ea-112">Exempel 1: hitta alla tillgängliga paket från en paket leverantör</span><span class="sxs-lookup"><span data-stu-id="5d5ea-112">Example 1: Find all available packages from a package provider</span></span>

<span data-ttu-id="5d5ea-113">Det här kommandot hittar alla tillgängliga PowerShell-moduler i ett registrerat Galleri.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-113">This command finds all available PowerShell module packages in a registered gallery.</span></span> <span data-ttu-id="5d5ea-114">Används `Get-PackageProvider` för att hämta leverantörs namnet.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-114">Use `Get-PackageProvider` to get the provider name.</span></span>

```
Find-Package -ProviderName NuGet
```

```Output
Name               Version   Source     Summary
----               -------   ------     -------
NUnit              3.11.0    MyNuGet    NUnit is a unit-testing framework for all .NET langua...
Newtonsoft.Json    12.0.1    MyNuGet    Json.NET is a popular high-performance JSON framework...
EntityFramework    6.2.0     MyNuGet    Entity Framework is Microsoft's recommended data acce...
MySql.Data         8.0.15    MyNuGet    MySql.Data.MySqlClient .Net Core Class Library
bootstrap          4.3.1     MyNuGet    Bootstrap framework in CSS. Includes fonts and JavaSc...
NuGet.Core         2.14.0    MyNuGet    NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="5d5ea-115">`Find-Package` använder **Provider** -parametern för att ange providerns **NuGet**.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-115">`Find-Package` uses the **Provider** parameter to specify the provider **NuGet**.</span></span>

### <span data-ttu-id="5d5ea-116">Exempel 2: hitta ett paket från en paket källa</span><span class="sxs-lookup"><span data-stu-id="5d5ea-116">Example 2: Find a package from a package source</span></span>

<span data-ttu-id="5d5ea-117">Det här kommandot hittar den senaste versionen av ett paket från en angiven paket källa.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-117">This command finds the newest version of a package from a specified package source.</span></span> <span data-ttu-id="5d5ea-118">Om en paket källa inte anges `Find-Package` söker igenom alla installerade paket leverantörer och paket källor.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-118">If a package source isn't provided, `Find-Package` searches each installed package provider and its package sources.</span></span> <span data-ttu-id="5d5ea-119">Används `Get-PackageSource` för att hämta källans namn.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-119">Use `Get-PackageSource` to get the source name.</span></span>

```
Find-Package -Name NuGet.Core -Source MyNuGet
```

```Output
Name         Version   Source    Summary
----         -------   ------    -------
NuGet.Core   2.14.0    MyNuGet   NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="5d5ea-120">`Find-Package` använder **Name** -parametern för att ange paket namnet **NuGet. Core**.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-120">`Find-Package` uses the **Name** parameter to specify the package name **NuGet.Core**.</span></span> <span data-ttu-id="5d5ea-121">Parametern **Source** anger för att söka efter paketet i **MyNuGet**.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-121">The **Source** parameter specifies to search for the package in **MyNuGet**.</span></span>

### <span data-ttu-id="5d5ea-122">Exempel 3: hitta alla versioner av ett paket</span><span class="sxs-lookup"><span data-stu-id="5d5ea-122">Example 3: Find all versions of a package</span></span>

<span data-ttu-id="5d5ea-123">Det här kommandot hittar alla tillgängliga paket versioner från en angiven Provider.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-123">This command finds all available package versions from a specified provider.</span></span>

```
Find-Package -Name NuGet.Core -Source MyNuGet -AllVersions
```

```Output
Name          Version          Source       Summary
----          -------          ------       -------
NuGet.Core    2.14.0           MyNuGet      NuGet.Core is the core framework assembly for NuGet...
NuGet.Core    2.14.0-rtm-832   MyNuGet      NuGet.Core is the core framework assembly for NuGet...
NuGet.Core    2.13.0           MyNuGet      NuGet.Core is the core framework assembly for NuGet...
...
NuGet.Core    1.1.229.159      MyNuGet      NuGet.Core is the core framework assembly for NuGet...
Nuget.Core    1.0.1120.104     MyNuGet      NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="5d5ea-124">`Find-Package` använder **Name** -parametern för att ange paketet **NuGet. Core**.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-124">`Find-Package` uses the **Name** parameter to specify the package **NuGet.Core**.</span></span> <span data-ttu-id="5d5ea-125">Parametern **ProviderName** anger att du vill söka efter paketet i **MyNuGet**.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-125">The **ProviderName** parameter specifies to search for the package in **MyNuGet**.</span></span> <span data-ttu-id="5d5ea-126">**AllVersions** anger att alla tillgängliga versioner returneras.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-126">**AllVersions** specifies that all available versions are returned.</span></span>

### <span data-ttu-id="5d5ea-127">Exempel 4: hitta ett paket med ett särskilt namn och en annan version</span><span class="sxs-lookup"><span data-stu-id="5d5ea-127">Example 4: Find a package with a specific name and version</span></span>

<span data-ttu-id="5d5ea-128">Det här kommandot hittar en specifik paket version från en angiven Provider.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-128">This command finds a specific package version from a specified provider.</span></span>

```
Find-Package -Name NuGet.Core -ProviderName NuGet -RequiredVersion 2.9.0
```

```Output
Name          Version          Source       Summary
----          -------          ------       -------
NuGet.Core    2.9.0            MyNuGet      NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="5d5ea-129">`Find-Package` använder **Name** -parametern för att ange paket namnet **NuGet. Core**.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-129">`Find-Package` uses the **Name** parameter to specify the package name **NuGet.Core**.</span></span> <span data-ttu-id="5d5ea-130">Parametern **ProviderName** anger att du vill söka efter paketet i **NuGet**.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-130">The **ProviderName** parameter specifies to search for the package in **NuGet**.</span></span> <span data-ttu-id="5d5ea-131">**RequiredVersion** anger att endast version **2.9.0** returneras.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-131">**RequiredVersion** specifies that only version **2.9.0** is returned.</span></span>

### <span data-ttu-id="5d5ea-132">Exempel 5: hitta paket i flera olika versioner</span><span class="sxs-lookup"><span data-stu-id="5d5ea-132">Example 5: Find packages within a range of versions</span></span>

<span data-ttu-id="5d5ea-133">Det här kommandot hittar en uppsättning versioner för ett angivet paket.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-133">This command finds a range of versions for a specified package.</span></span>

```
Find-Package -Name NuGet.Core -ProviderName NuGet -MinimumVersion 2.7.0 -MaximumVersion 2.9.0 -AllVersions
```

```Output
Name          Version          Source       Summary
----          -------          ------       -------
NuGet.Core    2.9.0            MyNuGet      NuGet.Core is the core framework assembly for NuGet...
NuGet.Core    2.8.6            MyNuGet      NuGet.Core is the core framework assembly for NuGet...
NuGet.Core    2.8.0            MyNuGet      NuGet.Core is the core framework assembly for NuGet...
NuGet.Core    2.7.0            MyNuGet      NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="5d5ea-134">`Find-Package` använder **Name** -parametern för att ange paket namnet **NuGet. Core**.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-134">`Find-Package` uses the **Name** parameter to specify the package name **NuGet.Core**.</span></span> <span data-ttu-id="5d5ea-135">Parametern **ProviderName** anger att du vill söka efter paketet i **NuGet**.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-135">The **ProviderName** parameter specifies to search for the package in **NuGet**.</span></span> <span data-ttu-id="5d5ea-136">**MinimumVersion** anger den lägsta versions **2.7.0**.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-136">**MinimumVersion** specifies the lowest version **2.7.0**.</span></span> <span data-ttu-id="5d5ea-137">**MaximumVersion** anger den högsta versions **2.9.0**.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-137">**MaximumVersion** specifies the highest version **2.9.0**.</span></span>
<span data-ttu-id="5d5ea-138">**AllVersions** anger att intervallet returneras enligt vad som anges med minsta och högsta värde.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-138">**AllVersions** determines the range is returned as specified by the minimum and maximum.</span></span>

### <span data-ttu-id="5d5ea-139">Exempel 6: hitta ett paket från ett fil system</span><span class="sxs-lookup"><span data-stu-id="5d5ea-139">Example 6: Find a package from a file system</span></span>

<span data-ttu-id="5d5ea-140">Det här kommandot hittar paket med fil namns tillägget `.nupkg` som lagras på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-140">This command finds packages with the file extension `.nupkg` that are stored on the local computer.</span></span>
<span data-ttu-id="5d5ea-141">Filerna är paket som hämtas från ett galleri, till exempel **NuGet**.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-141">The files are packages downloaded from a gallery such as the **NuGet**.</span></span>

```
PS> Find-Package -Source C:\LocalPkg
```

```Output
Name                 Version    Source           Summary
----                 -------    ------           -------
Microsoft.Web.Xdt    3.0.0      C:\LocalPkg\     Microsoft Xml Document Transformation (XDT)...
NuGet.Core           2.14.0     C:\LocalPkg\     NuGet.Core is the core framework assembly...
```

## <span data-ttu-id="5d5ea-142">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="5d5ea-142">PARAMETERS</span></span>

### <span data-ttu-id="5d5ea-143">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="5d5ea-143">-AcceptLicense</span></span>

<span data-ttu-id="5d5ea-144">Accepterar automatiskt ett licens avtal om paketet kräver det.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-144">Automatically accepts a license agreement if the package requires it.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5d5ea-145">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="5d5ea-145">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="5d5ea-146">Innehåller paket som marker ATS som en för hands version i resultaten.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-146">Includes packages marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="5d5ea-147">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="5d5ea-147">-AllVersions</span></span>

<span data-ttu-id="5d5ea-148">Anger att `Find-Package` returnerar alla tillgängliga versioner av paketet.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-148">Indicates that `Find-Package` returns all available versions of the package.</span></span> <span data-ttu-id="5d5ea-149">Som standard `Find-Package` returnerar endast den senaste tillgängliga versionen.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-149">By default, `Find-Package` only returns the newest available version.</span></span>

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

### <span data-ttu-id="5d5ea-150">-Kommando</span><span class="sxs-lookup"><span data-stu-id="5d5ea-150">-Command</span></span>

<span data-ttu-id="5d5ea-151">Anger en matris med kommandon som genomsökts av `Find-Package` .</span><span class="sxs-lookup"><span data-stu-id="5d5ea-151">Specifies an array of commands searched by `Find-Package`.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5d5ea-152">– ConfigFile</span><span class="sxs-lookup"><span data-stu-id="5d5ea-152">-ConfigFile</span></span>

<span data-ttu-id="5d5ea-153">Anger en konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-153">Specifies a configuration file.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5d5ea-154">– Innehåller</span><span class="sxs-lookup"><span data-stu-id="5d5ea-154">-Contains</span></span>

<span data-ttu-id="5d5ea-155">`Find-Package` hämtar objekt om ett objekt i objektets egenskaps värden är en exakt matchning för det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-155">`Find-Package` gets objects if any item in the object's property values are an exact match for the specified value.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5d5ea-156">-Credential</span><span class="sxs-lookup"><span data-stu-id="5d5ea-156">-Credential</span></span>

<span data-ttu-id="5d5ea-157">Anger ett användar konto som har behörighet att söka efter paket.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-157">Specifies a user account that has permission to search for packages.</span></span>

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

### <span data-ttu-id="5d5ea-158">– Dscresource Keyword Supports</span><span class="sxs-lookup"><span data-stu-id="5d5ea-158">-DscResource</span></span>

<span data-ttu-id="5d5ea-159">Anger en matris med DSC-resurser (Desired State Configuration) som denna cmdlet söker.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-159">Specifies an array of Desired State Configuration (DSC) resources that this cmdlet searches.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5d5ea-160">-Filter</span><span class="sxs-lookup"><span data-stu-id="5d5ea-160">-Filter</span></span>

<span data-ttu-id="5d5ea-161">Anger villkor för att söka efter i egenskaperna **namn** och **Beskrivning** .</span><span class="sxs-lookup"><span data-stu-id="5d5ea-161">Specifies terms to search for within the **Name** and **Description** properties.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5d5ea-162">-FilterOnTag</span><span class="sxs-lookup"><span data-stu-id="5d5ea-162">-FilterOnTag</span></span>

<span data-ttu-id="5d5ea-163">Anger taggen som filtrerar resultaten.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-163">Specifies the tag that filters the results.</span></span> <span data-ttu-id="5d5ea-164">Resultat som inte innehåller den angivna taggen utesluts.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-164">Results that don't contain the specified tag are excluded.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5d5ea-165">-Force</span><span class="sxs-lookup"><span data-stu-id="5d5ea-165">-Force</span></span>

<span data-ttu-id="5d5ea-166">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-166">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="5d5ea-167">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="5d5ea-167">-ForceBootstrap</span></span>

<span data-ttu-id="5d5ea-168">Anger att `Find-Package` paket leverantören ska installeras automatiskt av **PackageManagement** .</span><span class="sxs-lookup"><span data-stu-id="5d5ea-168">Indicates that `Find-Package` forces **PackageManagement** to automatically install the package provider.</span></span>

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

### <span data-ttu-id="5d5ea-169">– Sidhuvud</span><span class="sxs-lookup"><span data-stu-id="5d5ea-169">-Headers</span></span>

<span data-ttu-id="5d5ea-170">Anger sidhuvuden för paketet.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-170">Specifies the headers for the package.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5d5ea-171">-IncludeDependencies</span><span class="sxs-lookup"><span data-stu-id="5d5ea-171">-IncludeDependencies</span></span>

<span data-ttu-id="5d5ea-172">Anger att denna cmdlet inkluderar paket beroenden i resultaten.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-172">Indicates that this cmdlet includes package dependencies in the results.</span></span>

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

### <span data-ttu-id="5d5ea-173">– Innehåller</span><span class="sxs-lookup"><span data-stu-id="5d5ea-173">-Includes</span></span>

<span data-ttu-id="5d5ea-174">Anger om `Find-Package` alla paket i en kategori ska hittas.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-174">Specifies whether `Find-Package` should find all packages within a category.</span></span>

<span data-ttu-id="5d5ea-175">De godkända värdena är följande:</span><span class="sxs-lookup"><span data-stu-id="5d5ea-175">The accepted values are as follows:</span></span>

- <span data-ttu-id="5d5ea-176">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="5d5ea-176">Cmdlet</span></span>
- <span data-ttu-id="5d5ea-177">Dscresource Keyword Supports</span><span class="sxs-lookup"><span data-stu-id="5d5ea-177">DscResource</span></span>
- <span data-ttu-id="5d5ea-178">Funktion</span><span class="sxs-lookup"><span data-stu-id="5d5ea-178">Function</span></span>
- <span data-ttu-id="5d5ea-179">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="5d5ea-179">RoleCapability</span></span>
- <span data-ttu-id="5d5ea-180">Arbetsflöde</span><span class="sxs-lookup"><span data-stu-id="5d5ea-180">Workflow</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet
Aliases:
Accepted values: Cmdlet, DscResource, Function, RoleCapability, Workflow

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5d5ea-181">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="5d5ea-181">-MaximumVersion</span></span>

<span data-ttu-id="5d5ea-182">Anger den maximala paket version som du vill söka efter.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-182">Specifies the maximum package version that you want to find.</span></span>

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

### <span data-ttu-id="5d5ea-183">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="5d5ea-183">-MinimumVersion</span></span>

<span data-ttu-id="5d5ea-184">Anger den minsta paket version som du vill söka efter.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-184">Specifies the minimum package version that you want to find.</span></span> <span data-ttu-id="5d5ea-185">Om det finns en senare version returneras den versionen.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-185">If a higher version is available, that version is returned.</span></span>

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

### <span data-ttu-id="5d5ea-186">-Name</span><span class="sxs-lookup"><span data-stu-id="5d5ea-186">-Name</span></span>

<span data-ttu-id="5d5ea-187">Anger ett eller flera paket namn, eller paket namn med jokertecken.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-187">Specifies one or more package names, or package names with wildcard characters.</span></span> <span data-ttu-id="5d5ea-188">Separera flera paket namn med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-188">Separate multiple package names with commas.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="5d5ea-189">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="5d5ea-189">-PackageManagementProvider</span></span>

<span data-ttu-id="5d5ea-190">Anger namnet på en paket hanterings leverantör.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-190">Specifies the name of a package management provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5d5ea-191">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="5d5ea-191">-ProviderName</span></span>

<span data-ttu-id="5d5ea-192">Anger ett eller flera paket leverantörs namn.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-192">Specifies one or more package provider names.</span></span> <span data-ttu-id="5d5ea-193">Separera namn på flera paket leverantörer med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-193">Separate multiple package provider names with commas.</span></span>
<span data-ttu-id="5d5ea-194">Använd `Get-PackageProvider` för att hämta en lista över tillgängliga paket leverantörer.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-194">Use `Get-PackageProvider` to get a list of available package providers.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5d5ea-195">-Proxy</span><span class="sxs-lookup"><span data-stu-id="5d5ea-195">-Proxy</span></span>

<span data-ttu-id="5d5ea-196">Anger en proxyserver för begäran, i stället för en direkt anslutning till Internet resursen.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-196">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="5d5ea-197">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="5d5ea-197">-ProxyCredential</span></span>

<span data-ttu-id="5d5ea-198">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="5d5ea-198">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="5d5ea-199">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="5d5ea-199">-PublishLocation</span></span>

<span data-ttu-id="5d5ea-200">Anger en plats för publicering av paketet.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-200">Specifies a location for publishing the package.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5d5ea-201">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="5d5ea-201">-RequiredVersion</span></span>

<span data-ttu-id="5d5ea-202">Anger en exakt paket version som du vill söka efter.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-202">Specifies an exact package version that you want to find.</span></span>

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

### <span data-ttu-id="5d5ea-203">-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="5d5ea-203">-RoleCapability</span></span>

<span data-ttu-id="5d5ea-204">Anger en matris med roll funktioner.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-204">Specifies an array of role capabilities.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5d5ea-205">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="5d5ea-205">-ScriptPublishLocation</span></span>

<span data-ttu-id="5d5ea-206">Anger en plats för skript publicering för paketet.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-206">Specifies a script publishing location for the package.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5d5ea-207">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="5d5ea-207">-ScriptSourceLocation</span></span>

<span data-ttu-id="5d5ea-208">Anger en käll plats för skript.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-208">Specifies a script source location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5d5ea-209">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="5d5ea-209">-SkipValidate</span></span>

<span data-ttu-id="5d5ea-210">Växel som hoppar över verifiering av autentiseringsuppgifter för paket.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-210">Switch that skips package credential validation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5d5ea-211">-Source</span><span class="sxs-lookup"><span data-stu-id="5d5ea-211">-Source</span></span>

<span data-ttu-id="5d5ea-212">Anger en eller flera paket källor.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-212">Specifies one or more package sources.</span></span> <span data-ttu-id="5d5ea-213">Används `Get-PackageSource` för att hämta en lista över tillgängliga paket källor.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-213">Use `Get-PackageSource` to get a list of available package sources.</span></span> <span data-ttu-id="5d5ea-214">En fil system katalog kan användas som källa för hämtnings paket.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-214">A file system directory can be used as a source for download packages.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="5d5ea-215">-Tagga</span><span class="sxs-lookup"><span data-stu-id="5d5ea-215">-Tag</span></span>

<span data-ttu-id="5d5ea-216">Anger en eller flera strängar att söka efter i paketets metadata.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-216">Specifies one or more strings to search for in the package metadata.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5d5ea-217">-Typ</span><span class="sxs-lookup"><span data-stu-id="5d5ea-217">-Type</span></span>

<span data-ttu-id="5d5ea-218">Anger om du vill söka efter paket med en modul, ett skript eller något av alternativen.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-218">Specifies whether to search for packages with a module, a script, or either.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet
Aliases:
Accepted values: Module, Script, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5d5ea-219">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5d5ea-219">CommonParameters</span></span>

<span data-ttu-id="5d5ea-220">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-220">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5d5ea-221">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5d5ea-221">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5d5ea-222">INDATA</span><span class="sxs-lookup"><span data-stu-id="5d5ea-222">INPUTS</span></span>

### <span data-ttu-id="5d5ea-223">Inga</span><span class="sxs-lookup"><span data-stu-id="5d5ea-223">None</span></span>

<span data-ttu-id="5d5ea-224">`Find-Package` accepterar inte ininformation från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-224">`Find-Package` doesn't accept input from the pipeline.</span></span>

## <span data-ttu-id="5d5ea-225">UTDATA</span><span class="sxs-lookup"><span data-stu-id="5d5ea-225">OUTPUTS</span></span>

### <span data-ttu-id="5d5ea-226">SoftwareIdentify[]</span><span class="sxs-lookup"><span data-stu-id="5d5ea-226">SoftwareIdentify[]</span></span>

<span data-ttu-id="5d5ea-227">`Find-Package` matar ut ett **SoftwareIdentity** -objekt.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-227">`Find-Package` outputs a **SoftwareIdentity** object.</span></span>

## <span data-ttu-id="5d5ea-228">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="5d5ea-228">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5d5ea-229">Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-229">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="5d5ea-230">Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-230">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="5d5ea-231">Använd följande kommando för att se till att du använder TLS 1,2:</span><span class="sxs-lookup"><span data-stu-id="5d5ea-231">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="5d5ea-232">Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="5d5ea-232">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="5d5ea-233">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="5d5ea-233">RELATED LINKS</span></span>

[<span data-ttu-id="5d5ea-234">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="5d5ea-234">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="5d5ea-235">Get-Package</span><span class="sxs-lookup"><span data-stu-id="5d5ea-235">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="5d5ea-236">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="5d5ea-236">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="5d5ea-237">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="5d5ea-237">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="5d5ea-238">Installationspaket</span><span class="sxs-lookup"><span data-stu-id="5d5ea-238">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="5d5ea-239">Spara paket</span><span class="sxs-lookup"><span data-stu-id="5d5ea-239">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="5d5ea-240">Avinstallera paket</span><span class="sxs-lookup"><span data-stu-id="5d5ea-240">Uninstall-Package</span></span>](Uninstall-Package.md)
