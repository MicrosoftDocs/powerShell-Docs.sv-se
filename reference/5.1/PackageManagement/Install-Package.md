---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 05/23/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/install-package?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Installationspaket
ms.openlocfilehash: 9fcf71462e1bf411f3c7c5d8322e6b6f3a667b9f
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892822"
---
# <span data-ttu-id="79d5e-103">Installationspaket</span><span class="sxs-lookup"><span data-stu-id="79d5e-103">Install-Package</span></span>

## <span data-ttu-id="79d5e-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="79d5e-104">SYNOPSIS</span></span>
<span data-ttu-id="79d5e-105">Installerar ett eller flera program varu paket.</span><span class="sxs-lookup"><span data-stu-id="79d5e-105">Installs one or more software packages.</span></span>

## <span data-ttu-id="79d5e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="79d5e-106">SYNTAX</span></span>

### <span data-ttu-id="79d5e-107">PackageBySearch (standard)</span><span class="sxs-lookup"><span data-stu-id="79d5e-107">PackageBySearch (Default)</span></span>

```
Install-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Source <String[]>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ProviderName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="79d5e-108">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="79d5e-108">PackageByInputObject</span></span>

```
Install-Package [-InputObject] <SoftwareIdentity[]> [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="79d5e-109">Program: PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="79d5e-109">Programs:PackageBySearch</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-IncludeWindowsInstaller]
 [-IncludeSystemComponent] [<CommonParameters>]
```

### <span data-ttu-id="79d5e-110">Program: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="79d5e-110">Programs:PackageByInputObject</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-IncludeWindowsInstaller]
 [-IncludeSystemComponent] [<CommonParameters>]
```

### <span data-ttu-id="79d5e-111">MSI: PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="79d5e-111">msi:PackageBySearch</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AdditionalArguments <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="79d5e-112">MSI: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="79d5e-112">msi:PackageByInputObject</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AdditionalArguments <String[]>]
 [<CommonParameters>]
```

### <span data-ttu-id="79d5e-113">NuGet: PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="79d5e-113">NuGet:PackageBySearch</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ConfigFile <String>]
 [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>] [-Contains <String>]
 [-AllowPrereleaseVersions] [-Destination <String>] [-ExcludeVersion] [-Scope <String>]
 [-SkipDependencies] [<CommonParameters>]
```

### <span data-ttu-id="79d5e-114">NuGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="79d5e-114">NuGet:PackageByInputObject</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ConfigFile <String>]
 [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>] [-Contains <String>]
 [-AllowPrereleaseVersions] [-Destination <String>] [-ExcludeVersion] [-Scope <String>]
 [-SkipDependencies] [<CommonParameters>]
```

### <span data-ttu-id="79d5e-115">PowerShellGet: PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="79d5e-115">PowerShellGet:PackageBySearch</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AllowPrereleaseVersions]
 [-Scope <String>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [<CommonParameters>]
```

### <span data-ttu-id="79d5e-116">PowerShellGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="79d5e-116">PowerShellGet:PackageByInputObject</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AllowPrereleaseVersions]
 [-Scope <String>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [<CommonParameters>]
```

## <span data-ttu-id="79d5e-117">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="79d5e-117">DESCRIPTION</span></span>

<span data-ttu-id="79d5e-118">`Install-Package`Cmdleten installerar ett eller flera program varu paket på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="79d5e-118">The `Install-Package` cmdlet installs one or more software packages on the local computer.</span></span> <span data-ttu-id="79d5e-119">Om du har flera program varu källor använder du `Get-PackageProvider` och `Get-PackageSource` för att visa information om dina leverantörer.</span><span class="sxs-lookup"><span data-stu-id="79d5e-119">If you have multiple software sources, use `Get-PackageProvider` and `Get-PackageSource` to display details about your providers.</span></span>

## <span data-ttu-id="79d5e-120">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="79d5e-120">EXAMPLES</span></span>

### <span data-ttu-id="79d5e-121">Exempel 1: installera ett paket efter paket namn</span><span class="sxs-lookup"><span data-stu-id="79d5e-121">Example 1: Install a package by package name</span></span>

<span data-ttu-id="79d5e-122">`Install-Package`Cmdleten installerar ett program varu paket och dess beroenden.</span><span class="sxs-lookup"><span data-stu-id="79d5e-122">The `Install-Package` cmdlet installs a software package and its dependencies.</span></span>

```
PS> Install-Package -Name NuGet.Core -Source MyNuGet -Credential Contoso\TestUser
```

<span data-ttu-id="79d5e-123">`Install-Package` använder parametrar för att ange paket **namn** och **källa**.</span><span class="sxs-lookup"><span data-stu-id="79d5e-123">`Install-Package` uses parameters to specify the packages **Name** and **Source**.</span></span> <span data-ttu-id="79d5e-124">Parametern **Credential** använder ett domän användar konto med behörighet att installera paket.</span><span class="sxs-lookup"><span data-stu-id="79d5e-124">The **Credential** parameter uses a domain user account with permissions to install packages.</span></span> <span data-ttu-id="79d5e-125">Kommandot efterfrågar lösen ordet för användar kontot.</span><span class="sxs-lookup"><span data-stu-id="79d5e-125">The command prompts you for the user account password.</span></span>

### <span data-ttu-id="79d5e-126">Exempel 2: använda Find-Package för att installera ett paket</span><span class="sxs-lookup"><span data-stu-id="79d5e-126">Example 2: Use Find-Package to install a package</span></span>

<span data-ttu-id="79d5e-127">I det här exemplet skickas det objekt som returnerades av till `Find-Package` pipelinen och installeras av `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="79d5e-127">In this example, the object returned by `Find-Package` is sent down the pipeline and installed by `Install-Package`.</span></span>

```
PS> Find-Package -Name NuGet.Core -Source MyNuGet | Install-Package
```

<span data-ttu-id="79d5e-128">`Find-Package` använder **namn** -och **käll** parametrarna för att hitta ett paket.</span><span class="sxs-lookup"><span data-stu-id="79d5e-128">`Find-Package` uses the **Name** and **Source** parameters to locate a package.</span></span> <span data-ttu-id="79d5e-129">Objektet skickas ned pipelinen och `Install-Package` installerar paketet på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="79d5e-129">The object is sent down the pipeline and `Install-Package` installs the package on the local computer.</span></span>

### <span data-ttu-id="79d5e-130">Exempel 3: installera paket genom att ange ett versions intervall</span><span class="sxs-lookup"><span data-stu-id="79d5e-130">Example 3: Install packages by specifying a range of versions</span></span>

<span data-ttu-id="79d5e-131">`Install-Package` använder parametrarna **MinimumVersion** och **MaximumVersion** för att ange ett antal program varu versioner.</span><span class="sxs-lookup"><span data-stu-id="79d5e-131">`Install-Package` uses the **MinimumVersion** and **MaximumVersion** parameters to specify a range of software versions.</span></span>

```
PS> Install-Package -Name NuGet.Core -Source MyNuGet -MinimumVersion 2.8.0 -MaximumVersion 2.9.0
```

<span data-ttu-id="79d5e-132">`Install-Package` använder **namn** -och **käll** parametrarna för att hitta ett paket.</span><span class="sxs-lookup"><span data-stu-id="79d5e-132">`Install-Package` uses the **Name** and **Source** parameters to find a package.</span></span> <span data-ttu-id="79d5e-133">Parametrarna **MinimumVersion** och **MaximumVersion** anger ett antal program varu versioner.</span><span class="sxs-lookup"><span data-stu-id="79d5e-133">The **MinimumVersion** and **MaximumVersion** parameters specify a range of software versions.</span></span> <span data-ttu-id="79d5e-134">Den högsta versionen i intervallet är installerad.</span><span class="sxs-lookup"><span data-stu-id="79d5e-134">The highest version in the range is installed.</span></span>

## <span data-ttu-id="79d5e-135">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="79d5e-135">PARAMETERS</span></span>

### <span data-ttu-id="79d5e-136">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="79d5e-136">-AcceptLicense</span></span>

 <span data-ttu-id="79d5e-137">**AcceptLicense** accepterar automatiskt licens avtalet under installationen.</span><span class="sxs-lookup"><span data-stu-id="79d5e-137">**AcceptLicense** automatically accepts the license agreement during installation.</span></span>

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

### <span data-ttu-id="79d5e-138">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="79d5e-138">-AllowClobber</span></span>

<span data-ttu-id="79d5e-139">Åsidosätter varnings meddelanden om konflikter med befintliga kommandon.</span><span class="sxs-lookup"><span data-stu-id="79d5e-139">Overrides warning messages about conflicts with existing commands.</span></span> <span data-ttu-id="79d5e-140">Skriver över befintliga kommandon som har samma namn som kommandon som installeras.</span><span class="sxs-lookup"><span data-stu-id="79d5e-140">Overwrites existing commands that have the same name as commands being installed.</span></span>

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

### <span data-ttu-id="79d5e-141">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="79d5e-141">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="79d5e-142">Tillåter installation av paket som marker ATS som för hands version.</span><span class="sxs-lookup"><span data-stu-id="79d5e-142">Allows the installation of packages marked as prerelease.</span></span>

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

### <span data-ttu-id="79d5e-143">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="79d5e-143">-AllVersions</span></span>

<span data-ttu-id="79d5e-144">`Install-Package` installerar alla tillgängliga versioner av paketet.</span><span class="sxs-lookup"><span data-stu-id="79d5e-144">`Install-Package` installs all available versions of the package.</span></span> <span data-ttu-id="79d5e-145">Som standard är endast den senaste versionen installerad.</span><span class="sxs-lookup"><span data-stu-id="79d5e-145">By default, only the newest version is installed.</span></span>

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

### <span data-ttu-id="79d5e-146">-Kommando</span><span class="sxs-lookup"><span data-stu-id="79d5e-146">-Command</span></span>

<span data-ttu-id="79d5e-147">Anger ett eller flera kommandon som `Install-Package` söker.</span><span class="sxs-lookup"><span data-stu-id="79d5e-147">Specifies one or more commands that `Install-Package` searches.</span></span>

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

### <span data-ttu-id="79d5e-148">– ConfigFile</span><span class="sxs-lookup"><span data-stu-id="79d5e-148">-ConfigFile</span></span>

<span data-ttu-id="79d5e-149">Anger en sökväg som innehåller en konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="79d5e-149">Specifies a path that contains a configuration file.</span></span>

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

### <span data-ttu-id="79d5e-150">– Innehåller</span><span class="sxs-lookup"><span data-stu-id="79d5e-150">-Contains</span></span>

<span data-ttu-id="79d5e-151">`Install-Package` hämtar objekt om parametern **innehåller** anger ett värde som matchar något av objektets egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="79d5e-151">`Install-Package` gets objects if the **Contains** parameter specifies a value that matches any of the object's property values.</span></span>

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

### <span data-ttu-id="79d5e-152">-Credential</span><span class="sxs-lookup"><span data-stu-id="79d5e-152">-Credential</span></span>

<span data-ttu-id="79d5e-153">Anger ett användar konto som har behörighet att komma åt datorn och köra kommandon.</span><span class="sxs-lookup"><span data-stu-id="79d5e-153">Specifies a user account that has permission to access the computer and run commands.</span></span> <span data-ttu-id="79d5e-154">Ange ett användar namn, till exempel **user01**, **Domain01\User01**, eller ange ett **PSCredential** -objekt som genereras av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="79d5e-154">Type a user name, such as **User01**, **Domain01\User01**, or enter a **PSCredential** object, generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="79d5e-155">Om du anger ett användar namn uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="79d5e-155">If you type a user name, you're prompted for a password.</span></span>

<span data-ttu-id="79d5e-156">När parametern **Credential** inte anges `Install-Package` använder den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="79d5e-156">When the **Credential** parameter isn't specified, `Install-Package` uses the current user.</span></span>

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

### <span data-ttu-id="79d5e-157">-Mål</span><span class="sxs-lookup"><span data-stu-id="79d5e-157">-Destination</span></span>

<span data-ttu-id="79d5e-158">Anger en sökväg till ett indatamängds objekt.</span><span class="sxs-lookup"><span data-stu-id="79d5e-158">Specifies a path to an input object.</span></span>

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

### <span data-ttu-id="79d5e-159">– Dscresource Keyword Supports</span><span class="sxs-lookup"><span data-stu-id="79d5e-159">-DscResource</span></span>

<span data-ttu-id="79d5e-160">Anger en eller flera DSC-resurser (Desired State Configuration) som genomsöks av `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="79d5e-160">Specifies one or more Desired State Configuration (DSC) resources that are searched by `Install-Package`.</span></span> <span data-ttu-id="79d5e-161">Använd `Find-DscResource` cmdleten för att hitta DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="79d5e-161">Use the `Find-DscResource` cmdlet to find DSC resources.</span></span>

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

### <span data-ttu-id="79d5e-162">-ExcludeVersion</span><span class="sxs-lookup"><span data-stu-id="79d5e-162">-ExcludeVersion</span></span>

<span data-ttu-id="79d5e-163">Byt för att utesluta versions numret i mappsökvägen.</span><span class="sxs-lookup"><span data-stu-id="79d5e-163">Switch to exclude the version number in the folder path.</span></span>

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

### <span data-ttu-id="79d5e-164">-Filter</span><span class="sxs-lookup"><span data-stu-id="79d5e-164">-Filter</span></span>

<span data-ttu-id="79d5e-165">Anger villkor för att söka efter i egenskaperna **namn** och **Beskrivning** .</span><span class="sxs-lookup"><span data-stu-id="79d5e-165">Specifies terms to search for within the **Name** and **Description** properties.</span></span>

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

### <span data-ttu-id="79d5e-166">-FilterOnTag</span><span class="sxs-lookup"><span data-stu-id="79d5e-166">-FilterOnTag</span></span>

<span data-ttu-id="79d5e-167">Anger en tagg som filtrerar resultat och utesluter resultat som inte innehåller den angivna taggen.</span><span class="sxs-lookup"><span data-stu-id="79d5e-167">Specifies a tag that filters results and excludes results that don't contain the specified tag.</span></span>

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

### <span data-ttu-id="79d5e-168">-Force</span><span class="sxs-lookup"><span data-stu-id="79d5e-168">-Force</span></span>

<span data-ttu-id="79d5e-169">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="79d5e-169">Forces the command to run without asking for user confirmation.</span></span> <span data-ttu-id="79d5e-170">Åsidosätter begränsningar som förhindrar att `Install-Package` de lyckas, med undantag för säkerhet.</span><span class="sxs-lookup"><span data-stu-id="79d5e-170">Overrides restrictions that prevent `Install-Package` from succeeding, with the exception of security.</span></span>

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

### <span data-ttu-id="79d5e-171">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="79d5e-171">-ForceBootstrap</span></span>

<span data-ttu-id="79d5e-172">Tvingar **PackageManagement** att automatiskt installera paket leverantören för det angivna paketet.</span><span class="sxs-lookup"><span data-stu-id="79d5e-172">Forces **PackageManagement** to automatically install the package provider for the specified package.</span></span>

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

### <span data-ttu-id="79d5e-173">– Sidhuvud</span><span class="sxs-lookup"><span data-stu-id="79d5e-173">-Headers</span></span>

<span data-ttu-id="79d5e-174">Anger paket rubrikerna.</span><span class="sxs-lookup"><span data-stu-id="79d5e-174">Specifies the package headers.</span></span>

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

### <span data-ttu-id="79d5e-175">– Innehåller</span><span class="sxs-lookup"><span data-stu-id="79d5e-175">-Includes</span></span>

<span data-ttu-id="79d5e-176">Anger om `Install-Package` alla paket typer ska hittas.</span><span class="sxs-lookup"><span data-stu-id="79d5e-176">Specifies whether `Install-Package` should find all package types.</span></span> <span data-ttu-id="79d5e-177">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="79d5e-177">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="79d5e-178">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="79d5e-178">Cmdlet</span></span>
- <span data-ttu-id="79d5e-179">Dscresource Keyword Supports</span><span class="sxs-lookup"><span data-stu-id="79d5e-179">DscResource</span></span>
- <span data-ttu-id="79d5e-180">Funktion</span><span class="sxs-lookup"><span data-stu-id="79d5e-180">Function</span></span>
- <span data-ttu-id="79d5e-181">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="79d5e-181">RoleCapability</span></span>
- <span data-ttu-id="79d5e-182">Arbetsflöde</span><span class="sxs-lookup"><span data-stu-id="79d5e-182">Workflow</span></span>

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

### <span data-ttu-id="79d5e-183">– InputObject</span><span class="sxs-lookup"><span data-stu-id="79d5e-183">-InputObject</span></span>

<span data-ttu-id="79d5e-184">Accepterar pipeline-ininformation.</span><span class="sxs-lookup"><span data-stu-id="79d5e-184">Accepts pipeline input.</span></span> <span data-ttu-id="79d5e-185">Anger ett paket med paketets **SoftwareIdentity** -typ.</span><span class="sxs-lookup"><span data-stu-id="79d5e-185">Specifies a package by using the package's **SoftwareIdentity** type.</span></span>
<span data-ttu-id="79d5e-186">`Find-Package` matar ut ett **SoftwareIdentity** -objekt.</span><span class="sxs-lookup"><span data-stu-id="79d5e-186">`Find-Package` outputs a **SoftwareIdentity** object.</span></span>

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

### <span data-ttu-id="79d5e-187">-InstallUpdate</span><span class="sxs-lookup"><span data-stu-id="79d5e-187">-InstallUpdate</span></span>

<span data-ttu-id="79d5e-188">Anger att `Install-Package` uppdateringar installeras.</span><span class="sxs-lookup"><span data-stu-id="79d5e-188">Indicates that `Install-Package` installs updates.</span></span>

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

### <span data-ttu-id="79d5e-189">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="79d5e-189">-MaximumVersion</span></span>

<span data-ttu-id="79d5e-190">Anger den högsta tillåtna paket version som du vill installera.</span><span class="sxs-lookup"><span data-stu-id="79d5e-190">Specifies the maximum allowed package version that you want to install.</span></span> <span data-ttu-id="79d5e-191">Om du inte anger den här parametern `Install-Package` installeras paketets senaste version.</span><span class="sxs-lookup"><span data-stu-id="79d5e-191">If you don't specify this parameter, `Install-Package` installs the package's newest version.</span></span>

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

### <span data-ttu-id="79d5e-192">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="79d5e-192">-MinimumVersion</span></span>

<span data-ttu-id="79d5e-193">Anger den minsta tillåtna paket version som du vill installera.</span><span class="sxs-lookup"><span data-stu-id="79d5e-193">Specifies the minimum allowed package version that you want to install.</span></span> <span data-ttu-id="79d5e-194">Om du inte lägger till den här parametern `Install-Package` installerar paketets senaste version som uppfyller de versioner som anges i parametern **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="79d5e-194">If you don't add this parameter, `Install-Package` installs the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="79d5e-195">-Name</span><span class="sxs-lookup"><span data-stu-id="79d5e-195">-Name</span></span>

<span data-ttu-id="79d5e-196">Anger ett eller flera paket namn.</span><span class="sxs-lookup"><span data-stu-id="79d5e-196">Specifies one or more package names.</span></span> <span data-ttu-id="79d5e-197">Flera paket namn måste avgränsas med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="79d5e-197">Multiple package names must be separated by commas.</span></span>

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

### <span data-ttu-id="79d5e-198">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="79d5e-198">-NoPathUpdate</span></span>

<span data-ttu-id="79d5e-199">**NoPathUpdate** gäller endast för `Install-Script` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="79d5e-199">**NoPathUpdate** only applies to the `Install-Script` cmdlet.</span></span> <span data-ttu-id="79d5e-200">**NoPathUpdate** är en dynamisk parameter som lagts till av providern och som inte stöds av `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="79d5e-200">**NoPathUpdate** is a dynamic parameter added by the provider and isn't supported by `Install-Package`.</span></span>

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

### <span data-ttu-id="79d5e-201">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="79d5e-201">-PackageManagementProvider</span></span>

<span data-ttu-id="79d5e-202">Anger namnet på **PackageManagement** -providern.</span><span class="sxs-lookup"><span data-stu-id="79d5e-202">Specifies the name of the **PackageManagement** provider.</span></span>

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

### <span data-ttu-id="79d5e-203">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="79d5e-203">-ProviderName</span></span>

<span data-ttu-id="79d5e-204">Anger ett eller flera paket leverantörs namn som du vill använda för att begränsa paket sökningen.</span><span class="sxs-lookup"><span data-stu-id="79d5e-204">Specifies one or more package provider names to which to scope your package search.</span></span> <span data-ttu-id="79d5e-205">Du kan hämta paket leverantörs namn genom att köra `Get-PackageProvider` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="79d5e-205">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>

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

### <span data-ttu-id="79d5e-206">-Proxy</span><span class="sxs-lookup"><span data-stu-id="79d5e-206">-Proxy</span></span>

<span data-ttu-id="79d5e-207">Anger en proxyserver för begäran, i stället för att ansluta direkt till en Internet resurs.</span><span class="sxs-lookup"><span data-stu-id="79d5e-207">Specifies a proxy server for the request, rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="79d5e-208">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="79d5e-208">-ProxyCredential</span></span>

<span data-ttu-id="79d5e-209">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="79d5e-209">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="79d5e-210">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="79d5e-210">-PublishLocation</span></span>

<span data-ttu-id="79d5e-211">Anger sökvägen till paketets publicerade plats.</span><span class="sxs-lookup"><span data-stu-id="79d5e-211">Specifies the path to a package's published location.</span></span>

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

### <span data-ttu-id="79d5e-212">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="79d5e-212">-RequiredVersion</span></span>

<span data-ttu-id="79d5e-213">Anger den exakta versionen av paketet som du vill installera.</span><span class="sxs-lookup"><span data-stu-id="79d5e-213">Specifies the exact allowed version of the package that you want to install.</span></span> <span data-ttu-id="79d5e-214">Om du inte lägger till den här parametern `Install-Package` installerar paketets senaste version som uppfyller de versioner som anges i parametern **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="79d5e-214">If you don't add this parameter, `Install-Package` installs the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="79d5e-215">-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="79d5e-215">-RoleCapability</span></span>

<span data-ttu-id="79d5e-216">Anger en matris med roll funktioner.</span><span class="sxs-lookup"><span data-stu-id="79d5e-216">Specifies an array of role capabilities.</span></span>

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

### <span data-ttu-id="79d5e-217">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="79d5e-217">-Scope</span></span>

<span data-ttu-id="79d5e-218">Anger omfånget som paketet ska installeras för.</span><span class="sxs-lookup"><span data-stu-id="79d5e-218">Specifies the scope for which to install the package.</span></span> <span data-ttu-id="79d5e-219">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="79d5e-219">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="79d5e-220">CurrentUser</span><span class="sxs-lookup"><span data-stu-id="79d5e-220">CurrentUser</span></span>
- <span data-ttu-id="79d5e-221">AllUsers</span><span class="sxs-lookup"><span data-stu-id="79d5e-221">AllUsers</span></span>

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

### <span data-ttu-id="79d5e-222">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="79d5e-222">-ScriptPublishLocation</span></span>

<span data-ttu-id="79d5e-223">Anger sökvägen till ett skripts publicerade plats.</span><span class="sxs-lookup"><span data-stu-id="79d5e-223">Specifies the path to a script's published location.</span></span>

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

### <span data-ttu-id="79d5e-224">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="79d5e-224">-ScriptSourceLocation</span></span>

<span data-ttu-id="79d5e-225">Anger sökvägen till skript källan.</span><span class="sxs-lookup"><span data-stu-id="79d5e-225">Specifies the script source location.</span></span>

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

### <span data-ttu-id="79d5e-226">-SkipDependencies</span><span class="sxs-lookup"><span data-stu-id="79d5e-226">-SkipDependencies</span></span>

<span data-ttu-id="79d5e-227">Hoppar över installationen av program varu beroenden.</span><span class="sxs-lookup"><span data-stu-id="79d5e-227">Skips the installation of software dependencies.</span></span>

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

### <span data-ttu-id="79d5e-228">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="79d5e-228">-SkipPublisherCheck</span></span>

<span data-ttu-id="79d5e-229">Gör att du kan hämta en paket version som är nyare än den installerade versionen.</span><span class="sxs-lookup"><span data-stu-id="79d5e-229">Allows you to get a package version that is newer than your installed version.</span></span> <span data-ttu-id="79d5e-230">Till exempel ett installerat paket som har signerats digitalt av en betrodd utgivare, men en ny version inte har signerats digitalt.</span><span class="sxs-lookup"><span data-stu-id="79d5e-230">For example, an installed package that is digitally signed by a trusted publisher but a new version isn't digitally signed.</span></span>

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

### <span data-ttu-id="79d5e-231">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="79d5e-231">-SkipValidate</span></span>

<span data-ttu-id="79d5e-232">Växel som hoppar över verifiering av autentiseringsuppgifterna för ett paket.</span><span class="sxs-lookup"><span data-stu-id="79d5e-232">Switch that skips validating the credentials of a package.</span></span>

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

### <span data-ttu-id="79d5e-233">-Source</span><span class="sxs-lookup"><span data-stu-id="79d5e-233">-Source</span></span>

<span data-ttu-id="79d5e-234">Anger en eller flera paket källor.</span><span class="sxs-lookup"><span data-stu-id="79d5e-234">Specifies one or more package sources.</span></span> <span data-ttu-id="79d5e-235">Flera paket käll namn måste avgränsas med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="79d5e-235">Multiple package source names must be separated by commas.</span></span>
<span data-ttu-id="79d5e-236">Du kan hämta paketets käll namn genom att köra `Get-PackageSource` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="79d5e-236">You can get package source names by running the `Get-PackageSource` cmdlet.</span></span>

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

### <span data-ttu-id="79d5e-237">-Tagga</span><span class="sxs-lookup"><span data-stu-id="79d5e-237">-Tag</span></span>

<span data-ttu-id="79d5e-238">Anger en eller flera strängar att söka efter i paketets metadata.</span><span class="sxs-lookup"><span data-stu-id="79d5e-238">Specifies one or more strings to search for in the package metadata.</span></span>

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

### <span data-ttu-id="79d5e-239">-Typ</span><span class="sxs-lookup"><span data-stu-id="79d5e-239">-Type</span></span>

<span data-ttu-id="79d5e-240">Anger om du vill söka efter paket med en modul, ett skript eller både och.</span><span class="sxs-lookup"><span data-stu-id="79d5e-240">Specifies whether to search for packages with a module, a script, or both.</span></span> <span data-ttu-id="79d5e-241">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="79d5e-241">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="79d5e-242">Modul</span><span class="sxs-lookup"><span data-stu-id="79d5e-242">Module</span></span>
- <span data-ttu-id="79d5e-243">Skript</span><span class="sxs-lookup"><span data-stu-id="79d5e-243">Script</span></span>
- <span data-ttu-id="79d5e-244">Alla</span><span class="sxs-lookup"><span data-stu-id="79d5e-244">All</span></span>

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

### <span data-ttu-id="79d5e-245">-Confirm</span><span class="sxs-lookup"><span data-stu-id="79d5e-245">-Confirm</span></span>

<span data-ttu-id="79d5e-246">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="79d5e-246">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="79d5e-247">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="79d5e-247">-WhatIf</span></span>

<span data-ttu-id="79d5e-248">Visar vad som händer om `Install-Package` cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="79d5e-248">Shows what would happen if `Install-Package` cmdlet is run.</span></span> <span data-ttu-id="79d5e-249">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="79d5e-249">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="79d5e-250">-AdditionalArguments</span><span class="sxs-lookup"><span data-stu-id="79d5e-250">-AdditionalArguments</span></span>

<span data-ttu-id="79d5e-251">Anger ett eller flera ytterligare argument för installationen.</span><span class="sxs-lookup"><span data-stu-id="79d5e-251">Specifies one or more additional arguments for installation.</span></span>

```yaml
Type: System.String[]
Parameter Sets: msi:PackageBySearch, msi:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="79d5e-252">-IncludeSystemComponent</span><span class="sxs-lookup"><span data-stu-id="79d5e-252">-IncludeSystemComponent</span></span>

<span data-ttu-id="79d5e-253">Anger att denna cmdlet inkluderar system komponenter i resultaten.</span><span class="sxs-lookup"><span data-stu-id="79d5e-253">Indicates that this cmdlet includes system components in the results.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Programs:PackageBySearch, Programs:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="79d5e-254">-IncludeWindowsInstaller</span><span class="sxs-lookup"><span data-stu-id="79d5e-254">-IncludeWindowsInstaller</span></span>

<span data-ttu-id="79d5e-255">Anger att denna cmdlet inkluderar Windows Installer i resultatet.</span><span class="sxs-lookup"><span data-stu-id="79d5e-255">Indicates that this cmdlet includes the Windows installer in the results.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Programs:PackageBySearch, Programs:PackageByInputObject
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="79d5e-256">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="79d5e-256">CommonParameters</span></span>

<span data-ttu-id="79d5e-257">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="79d5e-257">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="79d5e-258">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="79d5e-258">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="79d5e-259">INDATA</span><span class="sxs-lookup"><span data-stu-id="79d5e-259">INPUTS</span></span>

### <span data-ttu-id="79d5e-260">`Install-Package` accepterar ininformation från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="79d5e-260">`Install-Package` accepts input from the pipeline.</span></span>

## <span data-ttu-id="79d5e-261">UTDATA</span><span class="sxs-lookup"><span data-stu-id="79d5e-261">OUTPUTS</span></span>

### <span data-ttu-id="79d5e-262">SoftwareIdentity []</span><span class="sxs-lookup"><span data-stu-id="79d5e-262">SoftwareIdentity[]</span></span>

## <span data-ttu-id="79d5e-263">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="79d5e-263">NOTES</span></span>

<span data-ttu-id="79d5e-264">Att inkludera en paket leverantör i ett kommando kan göra dynamiska parametrar tillgängliga för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="79d5e-264">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="79d5e-265">Dynamiska parametrar är speciella för en paket leverantör.</span><span class="sxs-lookup"><span data-stu-id="79d5e-265">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="79d5e-266">`Get-Help`Cmdleten listar en cmdlets parameter uppsättningar och inkluderar providerns parameter uppsättning.</span><span class="sxs-lookup"><span data-stu-id="79d5e-266">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span> <span data-ttu-id="79d5e-267">Till exempel `Install-Package` har **PowerShellGet** parameter uppsättning som innehåller `-NoPathUpdate` , `AllowClobber` , och `SkipPublisherCheck` .</span><span class="sxs-lookup"><span data-stu-id="79d5e-267">For example, `Install-Package` has the **PowerShellGet** parameter set that includes `-NoPathUpdate`, `AllowClobber`, and `SkipPublisherCheck`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="79d5e-268">Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1.</span><span class="sxs-lookup"><span data-stu-id="79d5e-268">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="79d5e-269">Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="79d5e-269">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="79d5e-270">Använd följande kommando för att se till att du använder TLS 1,2:</span><span class="sxs-lookup"><span data-stu-id="79d5e-270">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="79d5e-271">Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="79d5e-271">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="79d5e-272">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="79d5e-272">RELATED LINKS</span></span>

[<span data-ttu-id="79d5e-273">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="79d5e-273">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="79d5e-274">Find-Dscresource Keyword Supports</span><span class="sxs-lookup"><span data-stu-id="79d5e-274">Find-DscResource</span></span>](../PowershellGet/Find-DscResource.md)

[<span data-ttu-id="79d5e-275">Get – hjälp</span><span class="sxs-lookup"><span data-stu-id="79d5e-275">Get-Help</span></span>](../Microsoft.PowerShell.Core/Get-Help.md)

[<span data-ttu-id="79d5e-276">Get-Package</span><span class="sxs-lookup"><span data-stu-id="79d5e-276">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="79d5e-277">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="79d5e-277">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="79d5e-278">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="79d5e-278">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="79d5e-279">Sök-paket</span><span class="sxs-lookup"><span data-stu-id="79d5e-279">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="79d5e-280">Spara paket</span><span class="sxs-lookup"><span data-stu-id="79d5e-280">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="79d5e-281">Avinstallera paket</span><span class="sxs-lookup"><span data-stu-id="79d5e-281">Uninstall-Package</span></span>](Uninstall-Package.md)
