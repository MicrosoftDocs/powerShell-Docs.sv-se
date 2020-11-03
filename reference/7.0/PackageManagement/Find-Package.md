---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 04/03/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/find-package?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Package
ms.openlocfilehash: 9bbcda92b98410835a2380296a06fd053c01b52c
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262802"
---
# <span data-ttu-id="3e992-103">Find-Package</span><span class="sxs-lookup"><span data-stu-id="3e992-103">Find-Package</span></span>

## <span data-ttu-id="3e992-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="3e992-104">SYNOPSIS</span></span>
<span data-ttu-id="3e992-105">Söker efter program varu paket i tillgängliga paket källor.</span><span class="sxs-lookup"><span data-stu-id="3e992-105">Finds software packages in available package sources.</span></span>

## <span data-ttu-id="3e992-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3e992-106">SYNTAX</span></span>

### <span data-ttu-id="3e992-107">NuGet</span><span class="sxs-lookup"><span data-stu-id="3e992-107">NuGet</span></span>

```
Find-Package [-IncludeDependencies] [-AllVersions] [-Source <String[]>] [-Credential <PSCredential>]
 [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [[-Name] <String[]>] [-RequiredVersion <String>]
 [-MinimumVersion <String>] [-MaximumVersion <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-ConfigFile <String>] [-SkipValidate] [-Headers <String[]>]
 [-FilterOnTag <String[]>] [-Contains <String>] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="3e992-108">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="3e992-108">PowerShellGet</span></span>

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

## <span data-ttu-id="3e992-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="3e992-109">DESCRIPTION</span></span>

<span data-ttu-id="3e992-110">`Find-Package` söker efter program varu paket som är tillgängliga i paket källor.</span><span class="sxs-lookup"><span data-stu-id="3e992-110">`Find-Package` finds software packages that are available in package sources.</span></span> <span data-ttu-id="3e992-111">`Get-PackageProvider` och `Get-PackageSource` Visa information om dina leverantörer.</span><span class="sxs-lookup"><span data-stu-id="3e992-111">`Get-PackageProvider` and `Get-PackageSource` display details about your providers.</span></span>

## <span data-ttu-id="3e992-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="3e992-112">EXAMPLES</span></span>

### <span data-ttu-id="3e992-113">Exempel 1: hitta alla tillgängliga paket från en paket leverantör</span><span class="sxs-lookup"><span data-stu-id="3e992-113">Example 1: Find all available packages from a package provider</span></span>

<span data-ttu-id="3e992-114">Det här kommandot hittar alla tillgängliga PowerShell-moduler i ett registrerat Galleri.</span><span class="sxs-lookup"><span data-stu-id="3e992-114">This command finds all available PowerShell module packages in a registered gallery.</span></span> <span data-ttu-id="3e992-115">Används `Get-PackageProvider` för att hämta leverantörs namnet.</span><span class="sxs-lookup"><span data-stu-id="3e992-115">Use `Get-PackageProvider` to get the provider name.</span></span>

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

<span data-ttu-id="3e992-116">`Find-Package` använder **Provider** -parametern för att ange providerns **NuGet**.</span><span class="sxs-lookup"><span data-stu-id="3e992-116">`Find-Package` uses the **Provider** parameter to specify the provider **NuGet**.</span></span>

### <span data-ttu-id="3e992-117">Exempel 2: hitta ett paket från en paket källa</span><span class="sxs-lookup"><span data-stu-id="3e992-117">Example 2: Find a package from a package source</span></span>

<span data-ttu-id="3e992-118">Det här kommandot hittar den senaste versionen av ett paket från en angiven paket källa.</span><span class="sxs-lookup"><span data-stu-id="3e992-118">This command finds the newest version of a package from a specified package source.</span></span> <span data-ttu-id="3e992-119">Om en paket källa inte anges `Find-Package` söker igenom alla installerade paket leverantörer och paket källor.</span><span class="sxs-lookup"><span data-stu-id="3e992-119">If a package source isn't provided, `Find-Package` searches each installed package provider and its package sources.</span></span> <span data-ttu-id="3e992-120">Används `Get-PackageSource` för att hämta källans namn.</span><span class="sxs-lookup"><span data-stu-id="3e992-120">Use `Get-PackageSource` to get the source name.</span></span>

```
Find-Package -Name NuGet.Core -Source MyNuGet
```

```Output
Name         Version   Source    Summary
----         -------   ------    -------
NuGet.Core   2.14.0    MyNuGet   NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="3e992-121">`Find-Package` använder **Name** -parametern för att ange paket namnet **NuGet. Core**.</span><span class="sxs-lookup"><span data-stu-id="3e992-121">`Find-Package` uses the **Name** parameter to specify the package name **NuGet.Core**.</span></span> <span data-ttu-id="3e992-122">Parametern **Source** anger för att söka efter paketet i **MyNuGet**.</span><span class="sxs-lookup"><span data-stu-id="3e992-122">The **Source** parameter specifies to search for the package in **MyNuGet**.</span></span>

### <span data-ttu-id="3e992-123">Exempel 3: hitta alla versioner av ett paket</span><span class="sxs-lookup"><span data-stu-id="3e992-123">Example 3: Find all versions of a package</span></span>

<span data-ttu-id="3e992-124">Det här kommandot hittar alla tillgängliga paket versioner från en angiven Provider.</span><span class="sxs-lookup"><span data-stu-id="3e992-124">This command finds all available package versions from a specified provider.</span></span>

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

<span data-ttu-id="3e992-125">`Find-Package` använder **Name** -parametern för att ange paketet **NuGet. Core**.</span><span class="sxs-lookup"><span data-stu-id="3e992-125">`Find-Package` uses the **Name** parameter to specify the package **NuGet.Core**.</span></span> <span data-ttu-id="3e992-126">Parametern **ProviderName** anger att du vill söka efter paketet i **MyNuGet**.</span><span class="sxs-lookup"><span data-stu-id="3e992-126">The **ProviderName** parameter specifies to search for the package in **MyNuGet**.</span></span> <span data-ttu-id="3e992-127">**AllVersions** anger att alla tillgängliga versioner returneras.</span><span class="sxs-lookup"><span data-stu-id="3e992-127">**AllVersions** specifies that all available versions are returned.</span></span>

### <span data-ttu-id="3e992-128">Exempel 4: hitta ett paket med ett särskilt namn och en annan version</span><span class="sxs-lookup"><span data-stu-id="3e992-128">Example 4: Find a package with a specific name and version</span></span>

<span data-ttu-id="3e992-129">Det här kommandot hittar en specifik paket version från en angiven Provider.</span><span class="sxs-lookup"><span data-stu-id="3e992-129">This command finds a specific package version from a specified provider.</span></span>

```
Find-Package -Name NuGet.Core -ProviderName NuGet -RequiredVersion 2.9.0
```

```Output
Name          Version          Source       Summary
----          -------          ------       -------
NuGet.Core    2.9.0            MyNuGet      NuGet.Core is the core framework assembly for NuGet...
```

<span data-ttu-id="3e992-130">`Find-Package` använder **Name** -parametern för att ange paket namnet **NuGet. Core**.</span><span class="sxs-lookup"><span data-stu-id="3e992-130">`Find-Package` uses the **Name** parameter to specify the package name **NuGet.Core**.</span></span> <span data-ttu-id="3e992-131">Parametern **ProviderName** anger att du vill söka efter paketet i **NuGet**.</span><span class="sxs-lookup"><span data-stu-id="3e992-131">The **ProviderName** parameter specifies to search for the package in **NuGet**.</span></span> <span data-ttu-id="3e992-132">**RequiredVersion** anger att endast version **2.9.0** returneras.</span><span class="sxs-lookup"><span data-stu-id="3e992-132">**RequiredVersion** specifies that only version **2.9.0** is returned.</span></span>

### <span data-ttu-id="3e992-133">Exempel 5: hitta paket i flera olika versioner</span><span class="sxs-lookup"><span data-stu-id="3e992-133">Example 5: Find packages within a range of versions</span></span>

<span data-ttu-id="3e992-134">Det här kommandot hittar en uppsättning versioner för ett angivet paket.</span><span class="sxs-lookup"><span data-stu-id="3e992-134">This command finds a range of versions for a specified package.</span></span>

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

<span data-ttu-id="3e992-135">`Find-Package` använder **Name** -parametern för att ange paket namnet **NuGet. Core**.</span><span class="sxs-lookup"><span data-stu-id="3e992-135">`Find-Package` uses the **Name** parameter to specify the package name **NuGet.Core**.</span></span> <span data-ttu-id="3e992-136">Parametern **ProviderName** anger att du vill söka efter paketet i **NuGet**.</span><span class="sxs-lookup"><span data-stu-id="3e992-136">The **ProviderName** parameter specifies to search for the package in **NuGet**.</span></span> <span data-ttu-id="3e992-137">**MinimumVersion** anger den lägsta versions **2.7.0**.</span><span class="sxs-lookup"><span data-stu-id="3e992-137">**MinimumVersion** specifies the lowest version **2.7.0**.</span></span> <span data-ttu-id="3e992-138">**MaximumVersion** anger den högsta versions **2.9.0**.</span><span class="sxs-lookup"><span data-stu-id="3e992-138">**MaximumVersion** specifies the highest version **2.9.0**.</span></span>
<span data-ttu-id="3e992-139">**AllVersions** anger att intervallet returneras enligt vad som anges med minsta och högsta värde.</span><span class="sxs-lookup"><span data-stu-id="3e992-139">**AllVersions** determines the range is returned as specified by the minimum and maximum.</span></span>

### <span data-ttu-id="3e992-140">Exempel 6: hitta ett paket från ett fil system</span><span class="sxs-lookup"><span data-stu-id="3e992-140">Example 6: Find a package from a file system</span></span>

<span data-ttu-id="3e992-141">Det här kommandot hittar paket med fil namns tillägget `.nupkg` som lagras på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="3e992-141">This command finds packages with the file extension `.nupkg` that are stored on the local computer.</span></span>
<span data-ttu-id="3e992-142">Filerna är paket som hämtas från ett galleri, till exempel **NuGet**.</span><span class="sxs-lookup"><span data-stu-id="3e992-142">The files are packages downloaded from a gallery such as the **NuGet**.</span></span>

```
PS> Find-Package -Source C:\LocalPkg
```

```Output
Name                 Version    Source           Summary
----                 -------    ------           -------
Microsoft.Web.Xdt    3.0.0      C:\LocalPkg\     Microsoft Xml Document Transformation (XDT)...
NuGet.Core           2.14.0     C:\LocalPkg\     NuGet.Core is the core framework assembly...
```

## <span data-ttu-id="3e992-143">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="3e992-143">PARAMETERS</span></span>

### <span data-ttu-id="3e992-144">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="3e992-144">-AcceptLicense</span></span>

<span data-ttu-id="3e992-145">Accepterar automatiskt ett licens avtal om paketet kräver det.</span><span class="sxs-lookup"><span data-stu-id="3e992-145">Automatically accepts a license agreement if the package requires it.</span></span>

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

### <span data-ttu-id="3e992-146">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="3e992-146">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="3e992-147">Innehåller paket som marker ATS som en för hands version i resultaten.</span><span class="sxs-lookup"><span data-stu-id="3e992-147">Includes packages marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="3e992-148">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="3e992-148">-AllVersions</span></span>

<span data-ttu-id="3e992-149">Anger att `Find-Package` returnerar alla tillgängliga versioner av paketet.</span><span class="sxs-lookup"><span data-stu-id="3e992-149">Indicates that `Find-Package` returns all available versions of the package.</span></span> <span data-ttu-id="3e992-150">Som standard `Find-Package` returnerar endast den senaste tillgängliga versionen.</span><span class="sxs-lookup"><span data-stu-id="3e992-150">By default, `Find-Package` only returns the newest available version.</span></span>

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

### <span data-ttu-id="3e992-151">-Kommando</span><span class="sxs-lookup"><span data-stu-id="3e992-151">-Command</span></span>

<span data-ttu-id="3e992-152">Anger en matris med kommandon som genomsökts av `Find-Package` .</span><span class="sxs-lookup"><span data-stu-id="3e992-152">Specifies an array of commands searched by `Find-Package`.</span></span>

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

### <span data-ttu-id="3e992-153">– ConfigFile</span><span class="sxs-lookup"><span data-stu-id="3e992-153">-ConfigFile</span></span>

<span data-ttu-id="3e992-154">Anger en konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="3e992-154">Specifies a configuration file.</span></span>

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

### <span data-ttu-id="3e992-155">– Innehåller</span><span class="sxs-lookup"><span data-stu-id="3e992-155">-Contains</span></span>

<span data-ttu-id="3e992-156">`Find-Package` hämtar objekt om ett objekt i objektets egenskaps värden är en exakt matchning för det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="3e992-156">`Find-Package` gets objects if any item in the object's property values are an exact match for the specified value.</span></span>

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

### <span data-ttu-id="3e992-157">-Credential</span><span class="sxs-lookup"><span data-stu-id="3e992-157">-Credential</span></span>

<span data-ttu-id="3e992-158">Anger ett användar konto som har behörighet att söka efter paket.</span><span class="sxs-lookup"><span data-stu-id="3e992-158">Specifies a user account that has permission to search for packages.</span></span>

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

### <span data-ttu-id="3e992-159">– Dscresource Keyword Supports</span><span class="sxs-lookup"><span data-stu-id="3e992-159">-DscResource</span></span>

<span data-ttu-id="3e992-160">Anger en matris med DSC-resurser (Desired State Configuration) som denna cmdlet söker.</span><span class="sxs-lookup"><span data-stu-id="3e992-160">Specifies an array of Desired State Configuration (DSC) resources that this cmdlet searches.</span></span>

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

### <span data-ttu-id="3e992-161">-Filter</span><span class="sxs-lookup"><span data-stu-id="3e992-161">-Filter</span></span>

<span data-ttu-id="3e992-162">Anger villkor för att söka efter i egenskaperna **namn** och **Beskrivning** .</span><span class="sxs-lookup"><span data-stu-id="3e992-162">Specifies terms to search for within the **Name** and **Description** properties.</span></span>

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

### <span data-ttu-id="3e992-163">-FilterOnTag</span><span class="sxs-lookup"><span data-stu-id="3e992-163">-FilterOnTag</span></span>

<span data-ttu-id="3e992-164">Anger taggen som filtrerar resultaten.</span><span class="sxs-lookup"><span data-stu-id="3e992-164">Specifies the tag that filters the results.</span></span> <span data-ttu-id="3e992-165">Resultat som inte innehåller den angivna taggen utesluts.</span><span class="sxs-lookup"><span data-stu-id="3e992-165">Results that don't contain the specified tag are excluded.</span></span>

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

### <span data-ttu-id="3e992-166">-Force</span><span class="sxs-lookup"><span data-stu-id="3e992-166">-Force</span></span>

<span data-ttu-id="3e992-167">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="3e992-167">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="3e992-168">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="3e992-168">-ForceBootstrap</span></span>

<span data-ttu-id="3e992-169">Anger att `Find-Package` paket leverantören ska installeras automatiskt av **PackageManagement** .</span><span class="sxs-lookup"><span data-stu-id="3e992-169">Indicates that `Find-Package` forces **PackageManagement** to automatically install the package provider.</span></span>

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

### <span data-ttu-id="3e992-170">– Sidhuvud</span><span class="sxs-lookup"><span data-stu-id="3e992-170">-Headers</span></span>

<span data-ttu-id="3e992-171">Anger sidhuvuden för paketet.</span><span class="sxs-lookup"><span data-stu-id="3e992-171">Specifies the headers for the package.</span></span>

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

### <span data-ttu-id="3e992-172">-IncludeDependencies</span><span class="sxs-lookup"><span data-stu-id="3e992-172">-IncludeDependencies</span></span>

<span data-ttu-id="3e992-173">Anger att denna cmdlet inkluderar paket beroenden i resultaten.</span><span class="sxs-lookup"><span data-stu-id="3e992-173">Indicates that this cmdlet includes package dependencies in the results.</span></span>

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

### <span data-ttu-id="3e992-174">– Innehåller</span><span class="sxs-lookup"><span data-stu-id="3e992-174">-Includes</span></span>

<span data-ttu-id="3e992-175">Anger om `Find-Package` alla paket i en kategori ska hittas.</span><span class="sxs-lookup"><span data-stu-id="3e992-175">Specifies whether `Find-Package` should find all packages within a category.</span></span>

<span data-ttu-id="3e992-176">De godkända värdena är följande:</span><span class="sxs-lookup"><span data-stu-id="3e992-176">The accepted values are as follows:</span></span>

- <span data-ttu-id="3e992-177">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="3e992-177">Cmdlet</span></span>
- <span data-ttu-id="3e992-178">Dscresource Keyword Supports</span><span class="sxs-lookup"><span data-stu-id="3e992-178">DscResource</span></span>
- <span data-ttu-id="3e992-179">Funktion</span><span class="sxs-lookup"><span data-stu-id="3e992-179">Function</span></span>
- <span data-ttu-id="3e992-180">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="3e992-180">RoleCapability</span></span>
- <span data-ttu-id="3e992-181">Arbetsflöde</span><span class="sxs-lookup"><span data-stu-id="3e992-181">Workflow</span></span>

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

### <span data-ttu-id="3e992-182">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="3e992-182">-MaximumVersion</span></span>

<span data-ttu-id="3e992-183">Anger den maximala paket version som du vill söka efter.</span><span class="sxs-lookup"><span data-stu-id="3e992-183">Specifies the maximum package version that you want to find.</span></span>

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

### <span data-ttu-id="3e992-184">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="3e992-184">-MinimumVersion</span></span>

<span data-ttu-id="3e992-185">Anger den minsta paket version som du vill söka efter.</span><span class="sxs-lookup"><span data-stu-id="3e992-185">Specifies the minimum package version that you want to find.</span></span> <span data-ttu-id="3e992-186">Om det finns en senare version returneras den versionen.</span><span class="sxs-lookup"><span data-stu-id="3e992-186">If a higher version is available, that version is returned.</span></span>

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

### <span data-ttu-id="3e992-187">-Name</span><span class="sxs-lookup"><span data-stu-id="3e992-187">-Name</span></span>

<span data-ttu-id="3e992-188">Anger ett eller flera paket namn, eller paket namn med jokertecken.</span><span class="sxs-lookup"><span data-stu-id="3e992-188">Specifies one or more package names, or package names with wildcard characters.</span></span> <span data-ttu-id="3e992-189">Separera flera paket namn med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="3e992-189">Separate multiple package names with commas.</span></span>

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

### <span data-ttu-id="3e992-190">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="3e992-190">-PackageManagementProvider</span></span>

<span data-ttu-id="3e992-191">Anger namnet på en paket hanterings leverantör.</span><span class="sxs-lookup"><span data-stu-id="3e992-191">Specifies the name of a package management provider.</span></span>

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

### <span data-ttu-id="3e992-192">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="3e992-192">-ProviderName</span></span>

<span data-ttu-id="3e992-193">Anger ett eller flera paket leverantörs namn.</span><span class="sxs-lookup"><span data-stu-id="3e992-193">Specifies one or more package provider names.</span></span> <span data-ttu-id="3e992-194">Separera namn på flera paket leverantörer med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="3e992-194">Separate multiple package provider names with commas.</span></span>
<span data-ttu-id="3e992-195">Använd `Get-PackageProvider` för att hämta en lista över tillgängliga paket leverantörer.</span><span class="sxs-lookup"><span data-stu-id="3e992-195">Use `Get-PackageProvider` to get a list of available package providers.</span></span>

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

### <span data-ttu-id="3e992-196">-Proxy</span><span class="sxs-lookup"><span data-stu-id="3e992-196">-Proxy</span></span>

<span data-ttu-id="3e992-197">Anger en proxyserver för begäran, i stället för en direkt anslutning till Internet resursen.</span><span class="sxs-lookup"><span data-stu-id="3e992-197">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="3e992-198">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="3e992-198">-ProxyCredential</span></span>

<span data-ttu-id="3e992-199">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="3e992-199">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="3e992-200">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="3e992-200">-PublishLocation</span></span>

<span data-ttu-id="3e992-201">Anger en plats för publicering av paketet.</span><span class="sxs-lookup"><span data-stu-id="3e992-201">Specifies a location for publishing the package.</span></span>

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

### <span data-ttu-id="3e992-202">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="3e992-202">-RequiredVersion</span></span>

<span data-ttu-id="3e992-203">Anger en exakt paket version som du vill söka efter.</span><span class="sxs-lookup"><span data-stu-id="3e992-203">Specifies an exact package version that you want to find.</span></span>

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

### <span data-ttu-id="3e992-204">-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="3e992-204">-RoleCapability</span></span>

<span data-ttu-id="3e992-205">Anger en matris med roll funktioner.</span><span class="sxs-lookup"><span data-stu-id="3e992-205">Specifies an array of role capabilities.</span></span>

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

### <span data-ttu-id="3e992-206">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="3e992-206">-ScriptPublishLocation</span></span>

<span data-ttu-id="3e992-207">Anger en plats för skript publicering för paketet.</span><span class="sxs-lookup"><span data-stu-id="3e992-207">Specifies a script publishing location for the package.</span></span>

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

### <span data-ttu-id="3e992-208">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="3e992-208">-ScriptSourceLocation</span></span>

<span data-ttu-id="3e992-209">Anger en käll plats för skript.</span><span class="sxs-lookup"><span data-stu-id="3e992-209">Specifies a script source location.</span></span>

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

### <span data-ttu-id="3e992-210">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="3e992-210">-SkipValidate</span></span>

<span data-ttu-id="3e992-211">Växel som hoppar över verifiering av autentiseringsuppgifter för paket.</span><span class="sxs-lookup"><span data-stu-id="3e992-211">Switch that skips package credential validation.</span></span>

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

### <span data-ttu-id="3e992-212">-Source</span><span class="sxs-lookup"><span data-stu-id="3e992-212">-Source</span></span>

<span data-ttu-id="3e992-213">Anger en eller flera paket källor.</span><span class="sxs-lookup"><span data-stu-id="3e992-213">Specifies one or more package sources.</span></span> <span data-ttu-id="3e992-214">Används `Get-PackageSource` för att hämta en lista över tillgängliga paket källor.</span><span class="sxs-lookup"><span data-stu-id="3e992-214">Use `Get-PackageSource` to get a list of available package sources.</span></span> <span data-ttu-id="3e992-215">En fil system katalog kan användas som källa för hämtnings paket.</span><span class="sxs-lookup"><span data-stu-id="3e992-215">A file system directory can be used as a source for download packages.</span></span>

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

### <span data-ttu-id="3e992-216">-Tagga</span><span class="sxs-lookup"><span data-stu-id="3e992-216">-Tag</span></span>

<span data-ttu-id="3e992-217">Anger en eller flera strängar att söka efter i paketets metadata.</span><span class="sxs-lookup"><span data-stu-id="3e992-217">Specifies one or more strings to search for in the package metadata.</span></span>

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

### <span data-ttu-id="3e992-218">-Typ</span><span class="sxs-lookup"><span data-stu-id="3e992-218">-Type</span></span>

<span data-ttu-id="3e992-219">Anger om du vill söka efter paket med en modul, ett skript eller något av alternativen.</span><span class="sxs-lookup"><span data-stu-id="3e992-219">Specifies whether to search for packages with a module, a script, or either.</span></span>

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

### <span data-ttu-id="3e992-220">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3e992-220">CommonParameters</span></span>

<span data-ttu-id="3e992-221">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3e992-221">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3e992-222">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="3e992-222">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3e992-223">INDATA</span><span class="sxs-lookup"><span data-stu-id="3e992-223">INPUTS</span></span>

### <span data-ttu-id="3e992-224">Inget</span><span class="sxs-lookup"><span data-stu-id="3e992-224">None</span></span>

<span data-ttu-id="3e992-225">`Find-Package` accepterar inte ininformation från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="3e992-225">`Find-Package` doesn't accept input from the pipeline.</span></span>

## <span data-ttu-id="3e992-226">UTDATA</span><span class="sxs-lookup"><span data-stu-id="3e992-226">OUTPUTS</span></span>

### <span data-ttu-id="3e992-227">SoftwareIdentify[]</span><span class="sxs-lookup"><span data-stu-id="3e992-227">SoftwareIdentify[]</span></span>

<span data-ttu-id="3e992-228">`Find-Package` matar ut ett **SoftwareIdentity** -objekt.</span><span class="sxs-lookup"><span data-stu-id="3e992-228">`Find-Package` outputs a **SoftwareIdentity** object.</span></span>

## <span data-ttu-id="3e992-229">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="3e992-229">NOTES</span></span>

## <span data-ttu-id="3e992-230">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="3e992-230">RELATED LINKS</span></span>

[<span data-ttu-id="3e992-231">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="3e992-231">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="3e992-232">Get-Package</span><span class="sxs-lookup"><span data-stu-id="3e992-232">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="3e992-233">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="3e992-233">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="3e992-234">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="3e992-234">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="3e992-235">Installationspaket</span><span class="sxs-lookup"><span data-stu-id="3e992-235">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="3e992-236">Spara paket</span><span class="sxs-lookup"><span data-stu-id="3e992-236">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="3e992-237">Avinstallera paket</span><span class="sxs-lookup"><span data-stu-id="3e992-237">Uninstall-Package</span></span>](Uninstall-Package.md)