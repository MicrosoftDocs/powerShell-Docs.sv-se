---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 05/23/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/install-package?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Installationspaket
ms.openlocfilehash: 32d3f86a78001fce896f8cf282eb6854f31a54ab
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891395"
---
# <span data-ttu-id="1c9e5-103">Installationspaket</span><span class="sxs-lookup"><span data-stu-id="1c9e5-103">Install-Package</span></span>

## <span data-ttu-id="1c9e5-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="1c9e5-104">SYNOPSIS</span></span>
<span data-ttu-id="1c9e5-105">Installerar ett eller flera program varu paket.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-105">Installs one or more software packages.</span></span>

## <span data-ttu-id="1c9e5-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="1c9e5-106">SYNTAX</span></span>

### <span data-ttu-id="1c9e5-107">PackageBySearch (standard)</span><span class="sxs-lookup"><span data-stu-id="1c9e5-107">PackageBySearch (Default)</span></span>

```
Install-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Source <String[]>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ProviderName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="1c9e5-108">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="1c9e5-108">PackageByInputObject</span></span>

```
Install-Package [-InputObject] <SoftwareIdentity[]> [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="1c9e5-109">NuGet: PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="1c9e5-109">NuGet:PackageBySearch</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ConfigFile <String>]
 [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>] [-Contains <String>]
 [-AllowPrereleaseVersions] [-Destination <String>] [-ExcludeVersion] [-Scope <String>]
 [-SkipDependencies] [<CommonParameters>]
```

### <span data-ttu-id="1c9e5-110">NuGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="1c9e5-110">NuGet:PackageByInputObject</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ConfigFile <String>]
 [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>] [-Contains <String>]
 [-AllowPrereleaseVersions] [-Destination <String>] [-ExcludeVersion] [-Scope <String>]
 [-SkipDependencies] [<CommonParameters>]
```

### <span data-ttu-id="1c9e5-111">PowerShellGet: PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="1c9e5-111">PowerShellGet:PackageBySearch</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AllowPrereleaseVersions]
 [-Scope <String>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [<CommonParameters>]
```

### <span data-ttu-id="1c9e5-112">PowerShellGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="1c9e5-112">PowerShellGet:PackageByInputObject</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AllowPrereleaseVersions]
 [-Scope <String>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [<CommonParameters>]
```

## <span data-ttu-id="1c9e5-113">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="1c9e5-113">DESCRIPTION</span></span>

<span data-ttu-id="1c9e5-114">`Install-Package`Cmdleten installerar ett eller flera program varu paket på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-114">The `Install-Package` cmdlet installs one or more software packages on the local computer.</span></span> <span data-ttu-id="1c9e5-115">Om du har flera program varu källor använder du `Get-PackageProvider` och `Get-PackageSource` för att visa information om dina leverantörer.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-115">If you have multiple software sources, use `Get-PackageProvider` and `Get-PackageSource` to display details about your providers.</span></span>

## <span data-ttu-id="1c9e5-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="1c9e5-116">EXAMPLES</span></span>

### <span data-ttu-id="1c9e5-117">Exempel 1: installera ett paket efter paket namn</span><span class="sxs-lookup"><span data-stu-id="1c9e5-117">Example 1: Install a package by package name</span></span>

<span data-ttu-id="1c9e5-118">`Install-Package`Cmdleten installerar ett program varu paket och dess beroenden.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-118">The `Install-Package` cmdlet installs a software package and its dependencies.</span></span>

```
PS> Install-Package -Name NuGet.Core -Source MyNuGet -Credential Contoso\TestUser
```

<span data-ttu-id="1c9e5-119">`Install-Package` använder parametrar för att ange paket **namn** och **källa**.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-119">`Install-Package` uses parameters to specify the packages **Name** and **Source**.</span></span> <span data-ttu-id="1c9e5-120">Parametern **Credential** använder ett domän användar konto med behörighet att installera paket.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-120">The **Credential** parameter uses a domain user account with permissions to install packages.</span></span> <span data-ttu-id="1c9e5-121">Kommandot efterfrågar lösen ordet för användar kontot.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-121">The command prompts you for the user account password.</span></span>

### <span data-ttu-id="1c9e5-122">Exempel 2: använda Find-Package för att installera ett paket</span><span class="sxs-lookup"><span data-stu-id="1c9e5-122">Example 2: Use Find-Package to install a package</span></span>

<span data-ttu-id="1c9e5-123">I det här exemplet skickas det objekt som returnerades av till `Find-Package` pipelinen och installeras av `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="1c9e5-123">In this example, the object returned by `Find-Package` is sent down the pipeline and installed by `Install-Package`.</span></span>

```
PS> Find-Package -Name NuGet.Core -Source MyNuGet | Install-Package
```

<span data-ttu-id="1c9e5-124">`Find-Package` använder **namn** -och **käll** parametrarna för att hitta ett paket.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-124">`Find-Package` uses the **Name** and **Source** parameters to locate a package.</span></span> <span data-ttu-id="1c9e5-125">Objektet skickas ned pipelinen och `Install-Package` installerar paketet på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-125">The object is sent down the pipeline and `Install-Package` installs the package on the local computer.</span></span>

### <span data-ttu-id="1c9e5-126">Exempel 3: installera paket genom att ange ett versions intervall</span><span class="sxs-lookup"><span data-stu-id="1c9e5-126">Example 3: Install packages by specifying a range of versions</span></span>

<span data-ttu-id="1c9e5-127">`Install-Package` använder parametrarna **MinimumVersion** och **MaximumVersion** för att ange ett antal program varu versioner.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-127">`Install-Package` uses the **MinimumVersion** and **MaximumVersion** parameters to specify a range of software versions.</span></span>

```
PS> Install-Package -Name NuGet.Core -Source MyNuGet -MinimumVersion 2.8.0 -MaximumVersion 2.9.0
```

<span data-ttu-id="1c9e5-128">`Install-Package` använder **namn** -och **käll** parametrarna för att hitta ett paket.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-128">`Install-Package` uses the **Name** and **Source** parameters to find a package.</span></span> <span data-ttu-id="1c9e5-129">Parametrarna **MinimumVersion** och **MaximumVersion** anger ett antal program varu versioner.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-129">The **MinimumVersion** and **MaximumVersion** parameters specify a range of software versions.</span></span> <span data-ttu-id="1c9e5-130">Den högsta versionen i intervallet är installerad.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-130">The highest version in the range is installed.</span></span>

## <span data-ttu-id="1c9e5-131">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="1c9e5-131">PARAMETERS</span></span>

### <span data-ttu-id="1c9e5-132">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="1c9e5-132">-AcceptLicense</span></span>

 <span data-ttu-id="1c9e5-133">**AcceptLicense** accepterar automatiskt licens avtalet under installationen.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-133">**AcceptLicense** automatically accepts the license agreement during installation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c9e5-134">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="1c9e5-134">-AllowClobber</span></span>

<span data-ttu-id="1c9e5-135">Åsidosätter varnings meddelanden om konflikter med befintliga kommandon.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-135">Overrides warning messages about conflicts with existing commands.</span></span> <span data-ttu-id="1c9e5-136">Skriver över befintliga kommandon som har samma namn som kommandon som installeras.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-136">Overwrites existing commands that have the same name as commands being installed.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c9e5-137">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="1c9e5-137">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="1c9e5-138">Tillåter installation av paket som marker ATS som för hands version.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-138">Allows the installation of packages marked as prerelease.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject, PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c9e5-139">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="1c9e5-139">-AllVersions</span></span>

<span data-ttu-id="1c9e5-140">`Install-Package` installerar alla tillgängliga versioner av paketet.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-140">`Install-Package` installs all available versions of the package.</span></span> <span data-ttu-id="1c9e5-141">Som standard är endast den senaste versionen installerad.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-141">By default, only the newest version is installed.</span></span>

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

### <span data-ttu-id="1c9e5-142">-Kommando</span><span class="sxs-lookup"><span data-stu-id="1c9e5-142">-Command</span></span>

<span data-ttu-id="1c9e5-143">Anger ett eller flera kommandon som `Install-Package` söker.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-143">Specifies one or more commands that `Install-Package` searches.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c9e5-144">– ConfigFile</span><span class="sxs-lookup"><span data-stu-id="1c9e5-144">-ConfigFile</span></span>

<span data-ttu-id="1c9e5-145">Anger en sökväg som innehåller en konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-145">Specifies a path that contains a configuration file.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c9e5-146">– Innehåller</span><span class="sxs-lookup"><span data-stu-id="1c9e5-146">-Contains</span></span>

<span data-ttu-id="1c9e5-147">`Install-Package` hämtar objekt om parametern **innehåller** anger ett värde som matchar något av objektets egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-147">`Install-Package` gets objects if the **Contains** parameter specifies a value that matches any of the object's property values.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c9e5-148">-Credential</span><span class="sxs-lookup"><span data-stu-id="1c9e5-148">-Credential</span></span>

<span data-ttu-id="1c9e5-149">Anger ett användar konto som har behörighet att komma åt datorn och köra kommandon.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-149">Specifies a user account that has permission to access the computer and run commands.</span></span> <span data-ttu-id="1c9e5-150">Ange ett användar namn, till exempel **user01**, **Domain01\User01**, eller ange ett **PSCredential** -objekt som genereras av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-150">Type a user name, such as **User01**, **Domain01\User01**, or enter a **PSCredential** object, generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="1c9e5-151">Om du anger ett användar namn uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-151">If you type a user name, you're prompted for a password.</span></span>

<span data-ttu-id="1c9e5-152">När parametern **Credential** inte anges `Install-Package` använder den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-152">When the **Credential** parameter isn't specified, `Install-Package` uses the current user.</span></span>

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

### <span data-ttu-id="1c9e5-153">-Mål</span><span class="sxs-lookup"><span data-stu-id="1c9e5-153">-Destination</span></span>

<span data-ttu-id="1c9e5-154">Anger en sökväg till ett indatamängds objekt.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-154">Specifies a path to an input object.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c9e5-155">– Dscresource Keyword Supports</span><span class="sxs-lookup"><span data-stu-id="1c9e5-155">-DscResource</span></span>

<span data-ttu-id="1c9e5-156">Anger en eller flera DSC-resurser (Desired State Configuration) som genomsöks av `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="1c9e5-156">Specifies one or more Desired State Configuration (DSC) resources that are searched by `Install-Package`.</span></span> <span data-ttu-id="1c9e5-157">Använd `Find-DscResource` cmdleten för att hitta DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-157">Use the `Find-DscResource` cmdlet to find DSC resources.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c9e5-158">-ExcludeVersion</span><span class="sxs-lookup"><span data-stu-id="1c9e5-158">-ExcludeVersion</span></span>

<span data-ttu-id="1c9e5-159">Byt för att utesluta versions numret i mappsökvägen.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-159">Switch to exclude the version number in the folder path.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c9e5-160">-Filter</span><span class="sxs-lookup"><span data-stu-id="1c9e5-160">-Filter</span></span>

<span data-ttu-id="1c9e5-161">Anger villkor för att söka efter i egenskaperna **namn** och **Beskrivning** .</span><span class="sxs-lookup"><span data-stu-id="1c9e5-161">Specifies terms to search for within the **Name** and **Description** properties.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c9e5-162">-FilterOnTag</span><span class="sxs-lookup"><span data-stu-id="1c9e5-162">-FilterOnTag</span></span>

<span data-ttu-id="1c9e5-163">Anger en tagg som filtrerar resultat och utesluter resultat som inte innehåller den angivna taggen.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-163">Specifies a tag that filters results and excludes results that don't contain the specified tag.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c9e5-164">-Force</span><span class="sxs-lookup"><span data-stu-id="1c9e5-164">-Force</span></span>

<span data-ttu-id="1c9e5-165">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-165">Forces the command to run without asking for user confirmation.</span></span> <span data-ttu-id="1c9e5-166">Åsidosätter begränsningar som förhindrar att `Install-Package` de lyckas, med undantag för säkerhet.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-166">Overrides restrictions that prevent `Install-Package` from succeeding, with the exception of security.</span></span>

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

### <span data-ttu-id="1c9e5-167">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="1c9e5-167">-ForceBootstrap</span></span>

<span data-ttu-id="1c9e5-168">Tvingar **PackageManagement** att automatiskt installera paket leverantören för det angivna paketet.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-168">Forces **PackageManagement** to automatically install the package provider for the specified package.</span></span>

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

### <span data-ttu-id="1c9e5-169">– Sidhuvud</span><span class="sxs-lookup"><span data-stu-id="1c9e5-169">-Headers</span></span>

<span data-ttu-id="1c9e5-170">Anger paket rubrikerna.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-170">Specifies the package headers.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c9e5-171">– Innehåller</span><span class="sxs-lookup"><span data-stu-id="1c9e5-171">-Includes</span></span>

<span data-ttu-id="1c9e5-172">Anger om `Install-Package` alla paket typer ska hittas.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-172">Specifies whether `Install-Package` should find all package types.</span></span> <span data-ttu-id="1c9e5-173">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="1c9e5-173">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="1c9e5-174">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1c9e5-174">Cmdlet</span></span>
- <span data-ttu-id="1c9e5-175">Dscresource Keyword Supports</span><span class="sxs-lookup"><span data-stu-id="1c9e5-175">DscResource</span></span>
- <span data-ttu-id="1c9e5-176">Funktion</span><span class="sxs-lookup"><span data-stu-id="1c9e5-176">Function</span></span>
- <span data-ttu-id="1c9e5-177">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="1c9e5-177">RoleCapability</span></span>
- <span data-ttu-id="1c9e5-178">Arbetsflöde</span><span class="sxs-lookup"><span data-stu-id="1c9e5-178">Workflow</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:
Accepted values: Cmdlet, DscResource, Function, RoleCapability, Workflow

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c9e5-179">– InputObject</span><span class="sxs-lookup"><span data-stu-id="1c9e5-179">-InputObject</span></span>

<span data-ttu-id="1c9e5-180">Accepterar pipeline-ininformation.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-180">Accepts pipeline input.</span></span> <span data-ttu-id="1c9e5-181">Anger ett paket med paketets **SoftwareIdentity** -typ.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-181">Specifies a package by using the package's **SoftwareIdentity** type.</span></span>
<span data-ttu-id="1c9e5-182">`Find-Package` matar ut ett **SoftwareIdentity** -objekt.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-182">`Find-Package` outputs a **SoftwareIdentity** object.</span></span>

```yaml
Type: Microsoft.PackageManagement.Packaging.SoftwareIdentity[]
Parameter Sets: PackageByInputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="1c9e5-183">-InstallUpdate</span><span class="sxs-lookup"><span data-stu-id="1c9e5-183">-InstallUpdate</span></span>

<span data-ttu-id="1c9e5-184">Anger att `Install-Package` uppdateringar installeras.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-184">Indicates that `Install-Package` installs updates.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c9e5-185">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="1c9e5-185">-MaximumVersion</span></span>

<span data-ttu-id="1c9e5-186">Anger den högsta tillåtna paket version som du vill installera.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-186">Specifies the maximum allowed package version that you want to install.</span></span> <span data-ttu-id="1c9e5-187">Om du inte anger den här parametern `Install-Package` installeras paketets senaste version.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-187">If you don't specify this parameter, `Install-Package` installs the package's newest version.</span></span>

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

### <span data-ttu-id="1c9e5-188">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="1c9e5-188">-MinimumVersion</span></span>

<span data-ttu-id="1c9e5-189">Anger den minsta tillåtna paket version som du vill installera.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-189">Specifies the minimum allowed package version that you want to install.</span></span> <span data-ttu-id="1c9e5-190">Om du inte lägger till den här parametern `Install-Package` installerar paketets senaste version som uppfyller de versioner som anges i parametern **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="1c9e5-190">If you don't add this parameter, `Install-Package` installs the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="1c9e5-191">-Name</span><span class="sxs-lookup"><span data-stu-id="1c9e5-191">-Name</span></span>

<span data-ttu-id="1c9e5-192">Anger ett eller flera paket namn.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-192">Specifies one or more package names.</span></span> <span data-ttu-id="1c9e5-193">Flera paket namn måste avgränsas med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-193">Multiple package names must be separated by commas.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PackageBySearch
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c9e5-194">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="1c9e5-194">-NoPathUpdate</span></span>

<span data-ttu-id="1c9e5-195">**NoPathUpdate** gäller endast för `Install-Script` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-195">**NoPathUpdate** only applies to the `Install-Script` cmdlet.</span></span> <span data-ttu-id="1c9e5-196">**NoPathUpdate** är en dynamisk parameter som lagts till av providern och som inte stöds av `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="1c9e5-196">**NoPathUpdate** is a dynamic parameter added by the provider and isn't supported by `Install-Package`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c9e5-197">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="1c9e5-197">-PackageManagementProvider</span></span>

<span data-ttu-id="1c9e5-198">Anger namnet på **PackageManagement** -providern.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-198">Specifies the name of the **PackageManagement** provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c9e5-199">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="1c9e5-199">-ProviderName</span></span>

<span data-ttu-id="1c9e5-200">Anger ett eller flera paket leverantörs namn som du vill använda för att begränsa paket sökningen.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-200">Specifies one or more package provider names to which to scope your package search.</span></span> <span data-ttu-id="1c9e5-201">Du kan hämta paket leverantörs namn genom att köra `Get-PackageProvider` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-201">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>

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

### <span data-ttu-id="1c9e5-202">-Proxy</span><span class="sxs-lookup"><span data-stu-id="1c9e5-202">-Proxy</span></span>

<span data-ttu-id="1c9e5-203">Anger en proxyserver för begäran, i stället för att ansluta direkt till en Internet resurs.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-203">Specifies a proxy server for the request, rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="1c9e5-204">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="1c9e5-204">-ProxyCredential</span></span>

<span data-ttu-id="1c9e5-205">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="1c9e5-205">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="1c9e5-206">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="1c9e5-206">-PublishLocation</span></span>

<span data-ttu-id="1c9e5-207">Anger sökvägen till paketets publicerade plats.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-207">Specifies the path to a package's published location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c9e5-208">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="1c9e5-208">-RequiredVersion</span></span>

<span data-ttu-id="1c9e5-209">Anger den exakta versionen av paketet som du vill installera.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-209">Specifies the exact allowed version of the package that you want to install.</span></span> <span data-ttu-id="1c9e5-210">Om du inte lägger till den här parametern `Install-Package` installerar paketets senaste version som uppfyller de versioner som anges i parametern **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="1c9e5-210">If you don't add this parameter, `Install-Package` installs the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="1c9e5-211">-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="1c9e5-211">-RoleCapability</span></span>

<span data-ttu-id="1c9e5-212">Anger en matris med roll funktioner.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-212">Specifies an array of role capabilities.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c9e5-213">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="1c9e5-213">-Scope</span></span>

<span data-ttu-id="1c9e5-214">Anger omfånget som paketet ska installeras för.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-214">Specifies the scope for which to install the package.</span></span> <span data-ttu-id="1c9e5-215">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="1c9e5-215">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="1c9e5-216">CurrentUser</span><span class="sxs-lookup"><span data-stu-id="1c9e5-216">CurrentUser</span></span>
- <span data-ttu-id="1c9e5-217">AllUsers</span><span class="sxs-lookup"><span data-stu-id="1c9e5-217">AllUsers</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject, PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c9e5-218">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="1c9e5-218">-ScriptPublishLocation</span></span>

<span data-ttu-id="1c9e5-219">Anger sökvägen till ett skripts publicerade plats.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-219">Specifies the path to a script's published location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c9e5-220">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="1c9e5-220">-ScriptSourceLocation</span></span>

<span data-ttu-id="1c9e5-221">Anger sökvägen till skript källan.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-221">Specifies the script source location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c9e5-222">-SkipDependencies</span><span class="sxs-lookup"><span data-stu-id="1c9e5-222">-SkipDependencies</span></span>

<span data-ttu-id="1c9e5-223">Hoppar över installationen av program varu beroenden.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-223">Skips the installation of software dependencies.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c9e5-224">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="1c9e5-224">-SkipPublisherCheck</span></span>

<span data-ttu-id="1c9e5-225">Gör att du kan hämta en paket version som är nyare än den installerade versionen.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-225">Allows you to get a package version that is newer than your installed version.</span></span> <span data-ttu-id="1c9e5-226">Till exempel ett installerat paket som har signerats digitalt av en betrodd utgivare, men en ny version inte har signerats digitalt.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-226">For example, an installed package that is digitally signed by a trusted publisher but a new version isn't digitally signed.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c9e5-227">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="1c9e5-227">-SkipValidate</span></span>

<span data-ttu-id="1c9e5-228">Växel som hoppar över verifiering av autentiseringsuppgifterna för ett paket.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-228">Switch that skips validating the credentials of a package.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageBySearch, NuGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c9e5-229">-Source</span><span class="sxs-lookup"><span data-stu-id="1c9e5-229">-Source</span></span>

<span data-ttu-id="1c9e5-230">Anger en eller flera paket källor.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-230">Specifies one or more package sources.</span></span> <span data-ttu-id="1c9e5-231">Flera paket käll namn måste avgränsas med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-231">Multiple package source names must be separated by commas.</span></span>
<span data-ttu-id="1c9e5-232">Du kan hämta paketets käll namn genom att köra `Get-PackageSource` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-232">You can get package source names by running the `Get-PackageSource` cmdlet.</span></span>

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

### <span data-ttu-id="1c9e5-233">-Tagga</span><span class="sxs-lookup"><span data-stu-id="1c9e5-233">-Tag</span></span>

<span data-ttu-id="1c9e5-234">Anger en eller flera strängar att söka efter i paketets metadata.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-234">Specifies one or more strings to search for in the package metadata.</span></span>

```yaml
Type: System.String[]
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c9e5-235">-Typ</span><span class="sxs-lookup"><span data-stu-id="1c9e5-235">-Type</span></span>

<span data-ttu-id="1c9e5-236">Anger om du vill söka efter paket med en modul, ett skript eller både och.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-236">Specifies whether to search for packages with a module, a script, or both.</span></span> <span data-ttu-id="1c9e5-237">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="1c9e5-237">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="1c9e5-238">Modul</span><span class="sxs-lookup"><span data-stu-id="1c9e5-238">Module</span></span>
- <span data-ttu-id="1c9e5-239">Skript</span><span class="sxs-lookup"><span data-stu-id="1c9e5-239">Script</span></span>
- <span data-ttu-id="1c9e5-240">Alla</span><span class="sxs-lookup"><span data-stu-id="1c9e5-240">All</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageBySearch, PowerShellGet:PackageByInputObject
Aliases:
Accepted values: Module, Script, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="1c9e5-241">-Confirm</span><span class="sxs-lookup"><span data-stu-id="1c9e5-241">-Confirm</span></span>

<span data-ttu-id="1c9e5-242">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-242">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="1c9e5-243">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="1c9e5-243">-WhatIf</span></span>

<span data-ttu-id="1c9e5-244">Visar vad som händer om `Install-Package` cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-244">Shows what would happen if `Install-Package` cmdlet is run.</span></span> <span data-ttu-id="1c9e5-245">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-245">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="1c9e5-246">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="1c9e5-246">CommonParameters</span></span>

<span data-ttu-id="1c9e5-247">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-247">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="1c9e5-248">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="1c9e5-248">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="1c9e5-249">INDATA</span><span class="sxs-lookup"><span data-stu-id="1c9e5-249">INPUTS</span></span>

### <span data-ttu-id="1c9e5-250">`Install-Package` accepterar ininformation från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-250">`Install-Package` accepts input from the pipeline.</span></span>

## <span data-ttu-id="1c9e5-251">UTDATA</span><span class="sxs-lookup"><span data-stu-id="1c9e5-251">OUTPUTS</span></span>

### <span data-ttu-id="1c9e5-252">SoftwareIdentity []</span><span class="sxs-lookup"><span data-stu-id="1c9e5-252">SoftwareIdentity[]</span></span>

## <span data-ttu-id="1c9e5-253">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="1c9e5-253">NOTES</span></span>

<span data-ttu-id="1c9e5-254">Att inkludera en paket leverantör i ett kommando kan göra dynamiska parametrar tillgängliga för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-254">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="1c9e5-255">Dynamiska parametrar är speciella för en paket leverantör.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-255">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="1c9e5-256">`Get-Help`Cmdleten listar en cmdlets parameter uppsättningar och inkluderar providerns parameter uppsättning.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-256">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span> <span data-ttu-id="1c9e5-257">Till exempel `Install-Package` har **PowerShellGet** parameter uppsättning som innehåller `-NoPathUpdate` , `AllowClobber` , och `SkipPublisherCheck` .</span><span class="sxs-lookup"><span data-stu-id="1c9e5-257">For example, `Install-Package` has the **PowerShellGet** parameter set that includes `-NoPathUpdate`, `AllowClobber`, and `SkipPublisherCheck`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1c9e5-258">Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-258">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="1c9e5-259">Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-259">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="1c9e5-260">Använd följande kommando för att se till att du använder TLS 1,2:</span><span class="sxs-lookup"><span data-stu-id="1c9e5-260">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="1c9e5-261">Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="1c9e5-261">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="1c9e5-262">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="1c9e5-262">RELATED LINKS</span></span>

[<span data-ttu-id="1c9e5-263">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="1c9e5-263">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="1c9e5-264">Find-Dscresource Keyword Supports</span><span class="sxs-lookup"><span data-stu-id="1c9e5-264">Find-DscResource</span></span>](../PowershellGet/Find-DscResource.md)

[<span data-ttu-id="1c9e5-265">Get – hjälp</span><span class="sxs-lookup"><span data-stu-id="1c9e5-265">Get-Help</span></span>](../Microsoft.PowerShell.Core/Get-Help.md)

[<span data-ttu-id="1c9e5-266">Get-Package</span><span class="sxs-lookup"><span data-stu-id="1c9e5-266">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="1c9e5-267">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="1c9e5-267">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="1c9e5-268">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="1c9e5-268">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="1c9e5-269">Sök-paket</span><span class="sxs-lookup"><span data-stu-id="1c9e5-269">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="1c9e5-270">Spara paket</span><span class="sxs-lookup"><span data-stu-id="1c9e5-270">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="1c9e5-271">Avinstallera paket</span><span class="sxs-lookup"><span data-stu-id="1c9e5-271">Uninstall-Package</span></span>](Uninstall-Package.md)
