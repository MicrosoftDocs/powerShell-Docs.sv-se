---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 05/23/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/install-package?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Installationspaket
ms.openlocfilehash: 1518be0d34733e36217b46cbbf496e580ec7b649
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889436"
---
# <span data-ttu-id="76137-102">Installationspaket</span><span class="sxs-lookup"><span data-stu-id="76137-102">Install-Package</span></span>

## <span data-ttu-id="76137-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="76137-103">SYNOPSIS</span></span>
<span data-ttu-id="76137-104">Installerar ett eller flera program varu paket.</span><span class="sxs-lookup"><span data-stu-id="76137-104">Installs one or more software packages.</span></span>

## <span data-ttu-id="76137-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="76137-105">SYNTAX</span></span>

### <span data-ttu-id="76137-106">PackageBySearch (standard)</span><span class="sxs-lookup"><span data-stu-id="76137-106">PackageBySearch (Default)</span></span>

```
Install-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Source <String[]>] [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ProviderName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="76137-107">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="76137-107">PackageByInputObject</span></span>

```
Install-Package [-InputObject] <SoftwareIdentity[]> [-Credential <PSCredential>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="76137-108">NuGet: PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="76137-108">NuGet:PackageBySearch</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ConfigFile <String>]
 [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>] [-Contains <String>]
 [-AllowPrereleaseVersions] [-Destination <String>] [-ExcludeVersion] [-Scope <String>]
 [-SkipDependencies] [<CommonParameters>]
```

### <span data-ttu-id="76137-109">NuGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="76137-109">NuGet:PackageByInputObject</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ConfigFile <String>]
 [-SkipValidate] [-Headers <String[]>] [-FilterOnTag <String[]>] [-Contains <String>]
 [-AllowPrereleaseVersions] [-Destination <String>] [-ExcludeVersion] [-Scope <String>]
 [-SkipDependencies] [<CommonParameters>]
```

### <span data-ttu-id="76137-110">PowerShellGet: PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="76137-110">PowerShellGet:PackageBySearch</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AllowPrereleaseVersions]
 [-Scope <String>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [<CommonParameters>]
```

### <span data-ttu-id="76137-111">PowerShellGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="76137-111">PowerShellGet:PackageByInputObject</span></span>

```
Install-Package [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-AllowPrereleaseVersions]
 [-Scope <String>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [-Type <String>]
 [-Filter <String>] [-Tag <String[]>] [-Includes <String[]>] [-DscResource <String[]>]
 [-RoleCapability <String[]>] [-Command <String[]>] [-AcceptLicense] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [<CommonParameters>]
```

## <span data-ttu-id="76137-112">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="76137-112">DESCRIPTION</span></span>

<span data-ttu-id="76137-113">`Install-Package`Cmdleten installerar ett eller flera program varu paket på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="76137-113">The `Install-Package` cmdlet installs one or more software packages on the local computer.</span></span> <span data-ttu-id="76137-114">Om du har flera program varu källor använder du `Get-PackageProvider` och `Get-PackageSource` för att visa information om dina leverantörer.</span><span class="sxs-lookup"><span data-stu-id="76137-114">If you have multiple software sources, use `Get-PackageProvider` and `Get-PackageSource` to display details about your providers.</span></span>

## <span data-ttu-id="76137-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="76137-115">EXAMPLES</span></span>

### <span data-ttu-id="76137-116">Exempel 1: installera ett paket efter paket namn</span><span class="sxs-lookup"><span data-stu-id="76137-116">Example 1: Install a package by package name</span></span>

<span data-ttu-id="76137-117">`Install-Package`Cmdleten installerar ett program varu paket och dess beroenden.</span><span class="sxs-lookup"><span data-stu-id="76137-117">The `Install-Package` cmdlet installs a software package and its dependencies.</span></span>

```
PS> Install-Package -Name NuGet.Core -Source MyNuGet -Credential Contoso\TestUser
```

<span data-ttu-id="76137-118">`Install-Package` använder parametrar för att ange paket **namn** och **källa**.</span><span class="sxs-lookup"><span data-stu-id="76137-118">`Install-Package` uses parameters to specify the packages **Name** and **Source**.</span></span> <span data-ttu-id="76137-119">Parametern **Credential** använder ett domän användar konto med behörighet att installera paket.</span><span class="sxs-lookup"><span data-stu-id="76137-119">The **Credential** parameter uses a domain user account with permissions to install packages.</span></span> <span data-ttu-id="76137-120">Kommandot efterfrågar lösen ordet för användar kontot.</span><span class="sxs-lookup"><span data-stu-id="76137-120">The command prompts you for the user account password.</span></span>

### <span data-ttu-id="76137-121">Exempel 2: använda Find-Package för att installera ett paket</span><span class="sxs-lookup"><span data-stu-id="76137-121">Example 2: Use Find-Package to install a package</span></span>

<span data-ttu-id="76137-122">I det här exemplet skickas det objekt som returnerades av till `Find-Package` pipelinen och installeras av `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="76137-122">In this example, the object returned by `Find-Package` is sent down the pipeline and installed by `Install-Package`.</span></span>

```
PS> Find-Package -Name NuGet.Core -Source MyNuGet | Install-Package
```

<span data-ttu-id="76137-123">`Find-Package` använder **namn** -och **käll** parametrarna för att hitta ett paket.</span><span class="sxs-lookup"><span data-stu-id="76137-123">`Find-Package` uses the **Name** and **Source** parameters to locate a package.</span></span> <span data-ttu-id="76137-124">Objektet skickas ned pipelinen och `Install-Package` installerar paketet på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="76137-124">The object is sent down the pipeline and `Install-Package` installs the package on the local computer.</span></span>

### <span data-ttu-id="76137-125">Exempel 3: installera paket genom att ange ett versions intervall</span><span class="sxs-lookup"><span data-stu-id="76137-125">Example 3: Install packages by specifying a range of versions</span></span>

<span data-ttu-id="76137-126">`Install-Package` använder parametrarna **MinimumVersion** och **MaximumVersion** för att ange ett antal program varu versioner.</span><span class="sxs-lookup"><span data-stu-id="76137-126">`Install-Package` uses the **MinimumVersion** and **MaximumVersion** parameters to specify a range of software versions.</span></span>

```
PS> Install-Package -Name NuGet.Core -Source MyNuGet -MinimumVersion 2.8.0 -MaximumVersion 2.9.0
```

<span data-ttu-id="76137-127">`Install-Package` använder **namn** -och **käll** parametrarna för att hitta ett paket.</span><span class="sxs-lookup"><span data-stu-id="76137-127">`Install-Package` uses the **Name** and **Source** parameters to find a package.</span></span> <span data-ttu-id="76137-128">Parametrarna **MinimumVersion** och **MaximumVersion** anger ett antal program varu versioner.</span><span class="sxs-lookup"><span data-stu-id="76137-128">The **MinimumVersion** and **MaximumVersion** parameters specify a range of software versions.</span></span> <span data-ttu-id="76137-129">Den högsta versionen i intervallet är installerad.</span><span class="sxs-lookup"><span data-stu-id="76137-129">The highest version in the range is installed.</span></span>

## <span data-ttu-id="76137-130">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="76137-130">PARAMETERS</span></span>

### <span data-ttu-id="76137-131">-AcceptLicense</span><span class="sxs-lookup"><span data-stu-id="76137-131">-AcceptLicense</span></span>

 <span data-ttu-id="76137-132">**AcceptLicense** accepterar automatiskt licens avtalet under installationen.</span><span class="sxs-lookup"><span data-stu-id="76137-132">**AcceptLicense** automatically accepts the license agreement during installation.</span></span>

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

### <span data-ttu-id="76137-133">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="76137-133">-AllowClobber</span></span>

<span data-ttu-id="76137-134">Åsidosätter varnings meddelanden om konflikter med befintliga kommandon.</span><span class="sxs-lookup"><span data-stu-id="76137-134">Overrides warning messages about conflicts with existing commands.</span></span> <span data-ttu-id="76137-135">Skriver över befintliga kommandon som har samma namn som kommandon som installeras.</span><span class="sxs-lookup"><span data-stu-id="76137-135">Overwrites existing commands that have the same name as commands being installed.</span></span>

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

### <span data-ttu-id="76137-136">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="76137-136">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="76137-137">Tillåter installation av paket som marker ATS som för hands version.</span><span class="sxs-lookup"><span data-stu-id="76137-137">Allows the installation of packages marked as prerelease.</span></span>

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

### <span data-ttu-id="76137-138">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="76137-138">-AllVersions</span></span>

<span data-ttu-id="76137-139">`Install-Package` installerar alla tillgängliga versioner av paketet.</span><span class="sxs-lookup"><span data-stu-id="76137-139">`Install-Package` installs all available versions of the package.</span></span> <span data-ttu-id="76137-140">Som standard är endast den senaste versionen installerad.</span><span class="sxs-lookup"><span data-stu-id="76137-140">By default, only the newest version is installed.</span></span>

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

### <span data-ttu-id="76137-141">-Kommando</span><span class="sxs-lookup"><span data-stu-id="76137-141">-Command</span></span>

<span data-ttu-id="76137-142">Anger ett eller flera kommandon som `Install-Package` söker.</span><span class="sxs-lookup"><span data-stu-id="76137-142">Specifies one or more commands that `Install-Package` searches.</span></span>

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

### <span data-ttu-id="76137-143">– ConfigFile</span><span class="sxs-lookup"><span data-stu-id="76137-143">-ConfigFile</span></span>

<span data-ttu-id="76137-144">Anger en sökväg som innehåller en konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="76137-144">Specifies a path that contains a configuration file.</span></span>

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

### <span data-ttu-id="76137-145">– Innehåller</span><span class="sxs-lookup"><span data-stu-id="76137-145">-Contains</span></span>

<span data-ttu-id="76137-146">`Install-Package` hämtar objekt om parametern **innehåller** anger ett värde som matchar något av objektets egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="76137-146">`Install-Package` gets objects if the **Contains** parameter specifies a value that matches any of the object's property values.</span></span>

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

### <span data-ttu-id="76137-147">-Credential</span><span class="sxs-lookup"><span data-stu-id="76137-147">-Credential</span></span>

<span data-ttu-id="76137-148">Anger ett användar konto som har behörighet att komma åt datorn och köra kommandon.</span><span class="sxs-lookup"><span data-stu-id="76137-148">Specifies a user account that has permission to access the computer and run commands.</span></span> <span data-ttu-id="76137-149">Ange ett användar namn, till exempel **user01**, **Domain01\User01**, eller ange ett **PSCredential** -objekt som genereras av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="76137-149">Type a user name, such as **User01**, **Domain01\User01**, or enter a **PSCredential** object, generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="76137-150">Om du anger ett användar namn uppmanas du att ange ett lösen ord.</span><span class="sxs-lookup"><span data-stu-id="76137-150">If you type a user name, you're prompted for a password.</span></span>

<span data-ttu-id="76137-151">När parametern **Credential** inte anges `Install-Package` använder den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="76137-151">When the **Credential** parameter isn't specified, `Install-Package` uses the current user.</span></span>

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

### <span data-ttu-id="76137-152">-Mål</span><span class="sxs-lookup"><span data-stu-id="76137-152">-Destination</span></span>

<span data-ttu-id="76137-153">Anger en sökväg till ett indatamängds objekt.</span><span class="sxs-lookup"><span data-stu-id="76137-153">Specifies a path to an input object.</span></span>

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

### <span data-ttu-id="76137-154">– Dscresource Keyword Supports</span><span class="sxs-lookup"><span data-stu-id="76137-154">-DscResource</span></span>

<span data-ttu-id="76137-155">Anger en eller flera DSC-resurser (Desired State Configuration) som genomsöks av `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="76137-155">Specifies one or more Desired State Configuration (DSC) resources that are searched by `Install-Package`.</span></span> <span data-ttu-id="76137-156">Använd `Find-DscResource` cmdleten för att hitta DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="76137-156">Use the `Find-DscResource` cmdlet to find DSC resources.</span></span>

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

### <span data-ttu-id="76137-157">-ExcludeVersion</span><span class="sxs-lookup"><span data-stu-id="76137-157">-ExcludeVersion</span></span>

<span data-ttu-id="76137-158">Byt för att utesluta versions numret i mappsökvägen.</span><span class="sxs-lookup"><span data-stu-id="76137-158">Switch to exclude the version number in the folder path.</span></span>

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

### <span data-ttu-id="76137-159">-Filter</span><span class="sxs-lookup"><span data-stu-id="76137-159">-Filter</span></span>

<span data-ttu-id="76137-160">Anger villkor för att söka efter i egenskaperna **namn** och **Beskrivning** .</span><span class="sxs-lookup"><span data-stu-id="76137-160">Specifies terms to search for within the **Name** and **Description** properties.</span></span>

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

### <span data-ttu-id="76137-161">-FilterOnTag</span><span class="sxs-lookup"><span data-stu-id="76137-161">-FilterOnTag</span></span>

<span data-ttu-id="76137-162">Anger en tagg som filtrerar resultat och utesluter resultat som inte innehåller den angivna taggen.</span><span class="sxs-lookup"><span data-stu-id="76137-162">Specifies a tag that filters results and excludes results that don't contain the specified tag.</span></span>

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

### <span data-ttu-id="76137-163">-Force</span><span class="sxs-lookup"><span data-stu-id="76137-163">-Force</span></span>

<span data-ttu-id="76137-164">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="76137-164">Forces the command to run without asking for user confirmation.</span></span> <span data-ttu-id="76137-165">Åsidosätter begränsningar som förhindrar att `Install-Package` de lyckas, med undantag för säkerhet.</span><span class="sxs-lookup"><span data-stu-id="76137-165">Overrides restrictions that prevent `Install-Package` from succeeding, with the exception of security.</span></span>

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

### <span data-ttu-id="76137-166">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="76137-166">-ForceBootstrap</span></span>

<span data-ttu-id="76137-167">Tvingar **PackageManagement** att automatiskt installera paket leverantören för det angivna paketet.</span><span class="sxs-lookup"><span data-stu-id="76137-167">Forces **PackageManagement** to automatically install the package provider for the specified package.</span></span>

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

### <span data-ttu-id="76137-168">– Sidhuvud</span><span class="sxs-lookup"><span data-stu-id="76137-168">-Headers</span></span>

<span data-ttu-id="76137-169">Anger paket rubrikerna.</span><span class="sxs-lookup"><span data-stu-id="76137-169">Specifies the package headers.</span></span>

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

### <span data-ttu-id="76137-170">– Innehåller</span><span class="sxs-lookup"><span data-stu-id="76137-170">-Includes</span></span>

<span data-ttu-id="76137-171">Anger om `Install-Package` alla paket typer ska hittas.</span><span class="sxs-lookup"><span data-stu-id="76137-171">Specifies whether `Install-Package` should find all package types.</span></span> <span data-ttu-id="76137-172">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="76137-172">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="76137-173">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="76137-173">Cmdlet</span></span>
- <span data-ttu-id="76137-174">Dscresource Keyword Supports</span><span class="sxs-lookup"><span data-stu-id="76137-174">DscResource</span></span>
- <span data-ttu-id="76137-175">Funktion</span><span class="sxs-lookup"><span data-stu-id="76137-175">Function</span></span>
- <span data-ttu-id="76137-176">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="76137-176">RoleCapability</span></span>
- <span data-ttu-id="76137-177">Arbetsflöde</span><span class="sxs-lookup"><span data-stu-id="76137-177">Workflow</span></span>

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

### <span data-ttu-id="76137-178">– InputObject</span><span class="sxs-lookup"><span data-stu-id="76137-178">-InputObject</span></span>

<span data-ttu-id="76137-179">Accepterar pipeline-ininformation.</span><span class="sxs-lookup"><span data-stu-id="76137-179">Accepts pipeline input.</span></span> <span data-ttu-id="76137-180">Anger ett paket med paketets **SoftwareIdentity** -typ.</span><span class="sxs-lookup"><span data-stu-id="76137-180">Specifies a package by using the package's **SoftwareIdentity** type.</span></span>
<span data-ttu-id="76137-181">`Find-Package` matar ut ett **SoftwareIdentity** -objekt.</span><span class="sxs-lookup"><span data-stu-id="76137-181">`Find-Package` outputs a **SoftwareIdentity** object.</span></span>

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

### <span data-ttu-id="76137-182">-InstallUpdate</span><span class="sxs-lookup"><span data-stu-id="76137-182">-InstallUpdate</span></span>

<span data-ttu-id="76137-183">Anger att `Install-Package` uppdateringar installeras.</span><span class="sxs-lookup"><span data-stu-id="76137-183">Indicates that `Install-Package` installs updates.</span></span>

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

### <span data-ttu-id="76137-184">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="76137-184">-MaximumVersion</span></span>

<span data-ttu-id="76137-185">Anger den högsta tillåtna paket version som du vill installera.</span><span class="sxs-lookup"><span data-stu-id="76137-185">Specifies the maximum allowed package version that you want to install.</span></span> <span data-ttu-id="76137-186">Om du inte anger den här parametern `Install-Package` installeras paketets senaste version.</span><span class="sxs-lookup"><span data-stu-id="76137-186">If you don't specify this parameter, `Install-Package` installs the package's newest version.</span></span>

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

### <span data-ttu-id="76137-187">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="76137-187">-MinimumVersion</span></span>

<span data-ttu-id="76137-188">Anger den minsta tillåtna paket version som du vill installera.</span><span class="sxs-lookup"><span data-stu-id="76137-188">Specifies the minimum allowed package version that you want to install.</span></span> <span data-ttu-id="76137-189">Om du inte lägger till den här parametern `Install-Package` installerar paketets senaste version som uppfyller de versioner som anges i parametern **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="76137-189">If you don't add this parameter, `Install-Package` installs the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="76137-190">-Name</span><span class="sxs-lookup"><span data-stu-id="76137-190">-Name</span></span>

<span data-ttu-id="76137-191">Anger ett eller flera paket namn.</span><span class="sxs-lookup"><span data-stu-id="76137-191">Specifies one or more package names.</span></span> <span data-ttu-id="76137-192">Flera paket namn måste avgränsas med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="76137-192">Multiple package names must be separated by commas.</span></span>

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

### <span data-ttu-id="76137-193">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="76137-193">-NoPathUpdate</span></span>

<span data-ttu-id="76137-194">**NoPathUpdate** gäller endast för `Install-Script` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="76137-194">**NoPathUpdate** only applies to the `Install-Script` cmdlet.</span></span> <span data-ttu-id="76137-195">**NoPathUpdate** är en dynamisk parameter som lagts till av providern och som inte stöds av `Install-Package` .</span><span class="sxs-lookup"><span data-stu-id="76137-195">**NoPathUpdate** is a dynamic parameter added by the provider and isn't supported by `Install-Package`.</span></span>

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

### <span data-ttu-id="76137-196">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="76137-196">-PackageManagementProvider</span></span>

<span data-ttu-id="76137-197">Anger namnet på **PackageManagement** -providern.</span><span class="sxs-lookup"><span data-stu-id="76137-197">Specifies the name of the **PackageManagement** provider.</span></span>

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

### <span data-ttu-id="76137-198">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="76137-198">-ProviderName</span></span>

<span data-ttu-id="76137-199">Anger ett eller flera paket leverantörs namn som du vill använda för att begränsa paket sökningen.</span><span class="sxs-lookup"><span data-stu-id="76137-199">Specifies one or more package provider names to which to scope your package search.</span></span> <span data-ttu-id="76137-200">Du kan hämta paket leverantörs namn genom att köra `Get-PackageProvider` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="76137-200">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>

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

### <span data-ttu-id="76137-201">-Proxy</span><span class="sxs-lookup"><span data-stu-id="76137-201">-Proxy</span></span>

<span data-ttu-id="76137-202">Anger en proxyserver för begäran, i stället för att ansluta direkt till en Internet resurs.</span><span class="sxs-lookup"><span data-stu-id="76137-202">Specifies a proxy server for the request, rather than connecting directly to an internet resource.</span></span>

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

### <span data-ttu-id="76137-203">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="76137-203">-ProxyCredential</span></span>

<span data-ttu-id="76137-204">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="76137-204">Specifies a user account that has permission to use the proxy server specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="76137-205">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="76137-205">-PublishLocation</span></span>

<span data-ttu-id="76137-206">Anger sökvägen till paketets publicerade plats.</span><span class="sxs-lookup"><span data-stu-id="76137-206">Specifies the path to a package's published location.</span></span>

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

### <span data-ttu-id="76137-207">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="76137-207">-RequiredVersion</span></span>

<span data-ttu-id="76137-208">Anger den exakta versionen av paketet som du vill installera.</span><span class="sxs-lookup"><span data-stu-id="76137-208">Specifies the exact allowed version of the package that you want to install.</span></span> <span data-ttu-id="76137-209">Om du inte lägger till den här parametern `Install-Package` installerar paketets senaste version som uppfyller de versioner som anges i parametern **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="76137-209">If you don't add this parameter, `Install-Package` installs the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="76137-210">-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="76137-210">-RoleCapability</span></span>

<span data-ttu-id="76137-211">Anger en matris med roll funktioner.</span><span class="sxs-lookup"><span data-stu-id="76137-211">Specifies an array of role capabilities.</span></span>

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

### <span data-ttu-id="76137-212">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="76137-212">-Scope</span></span>

<span data-ttu-id="76137-213">Anger omfånget som paketet ska installeras för.</span><span class="sxs-lookup"><span data-stu-id="76137-213">Specifies the scope for which to install the package.</span></span> <span data-ttu-id="76137-214">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="76137-214">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="76137-215">CurrentUser</span><span class="sxs-lookup"><span data-stu-id="76137-215">CurrentUser</span></span>
- <span data-ttu-id="76137-216">AllUsers</span><span class="sxs-lookup"><span data-stu-id="76137-216">AllUsers</span></span>

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

### <span data-ttu-id="76137-217">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="76137-217">-ScriptPublishLocation</span></span>

<span data-ttu-id="76137-218">Anger sökvägen till ett skripts publicerade plats.</span><span class="sxs-lookup"><span data-stu-id="76137-218">Specifies the path to a script's published location.</span></span>

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

### <span data-ttu-id="76137-219">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="76137-219">-ScriptSourceLocation</span></span>

<span data-ttu-id="76137-220">Anger sökvägen till skript källan.</span><span class="sxs-lookup"><span data-stu-id="76137-220">Specifies the script source location.</span></span>

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

### <span data-ttu-id="76137-221">-SkipDependencies</span><span class="sxs-lookup"><span data-stu-id="76137-221">-SkipDependencies</span></span>

<span data-ttu-id="76137-222">Hoppar över installationen av program varu beroenden.</span><span class="sxs-lookup"><span data-stu-id="76137-222">Skips the installation of software dependencies.</span></span>

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

### <span data-ttu-id="76137-223">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="76137-223">-SkipPublisherCheck</span></span>

<span data-ttu-id="76137-224">Gör att du kan hämta en paket version som är nyare än den installerade versionen.</span><span class="sxs-lookup"><span data-stu-id="76137-224">Allows you to get a package version that is newer than your installed version.</span></span> <span data-ttu-id="76137-225">Till exempel ett installerat paket som har signerats digitalt av en betrodd utgivare, men en ny version inte har signerats digitalt.</span><span class="sxs-lookup"><span data-stu-id="76137-225">For example, an installed package that is digitally signed by a trusted publisher but a new version isn't digitally signed.</span></span>

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

### <span data-ttu-id="76137-226">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="76137-226">-SkipValidate</span></span>

<span data-ttu-id="76137-227">Växel som hoppar över verifiering av autentiseringsuppgifterna för ett paket.</span><span class="sxs-lookup"><span data-stu-id="76137-227">Switch that skips validating the credentials of a package.</span></span>

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

### <span data-ttu-id="76137-228">-Source</span><span class="sxs-lookup"><span data-stu-id="76137-228">-Source</span></span>

<span data-ttu-id="76137-229">Anger en eller flera paket källor.</span><span class="sxs-lookup"><span data-stu-id="76137-229">Specifies one or more package sources.</span></span> <span data-ttu-id="76137-230">Flera paket käll namn måste avgränsas med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="76137-230">Multiple package source names must be separated by commas.</span></span>
<span data-ttu-id="76137-231">Du kan hämta paketets käll namn genom att köra `Get-PackageSource` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="76137-231">You can get package source names by running the `Get-PackageSource` cmdlet.</span></span>

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

### <span data-ttu-id="76137-232">-Tagga</span><span class="sxs-lookup"><span data-stu-id="76137-232">-Tag</span></span>

<span data-ttu-id="76137-233">Anger en eller flera strängar att söka efter i paketets metadata.</span><span class="sxs-lookup"><span data-stu-id="76137-233">Specifies one or more strings to search for in the package metadata.</span></span>

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

### <span data-ttu-id="76137-234">-Typ</span><span class="sxs-lookup"><span data-stu-id="76137-234">-Type</span></span>

<span data-ttu-id="76137-235">Anger om du vill söka efter paket med en modul, ett skript eller både och.</span><span class="sxs-lookup"><span data-stu-id="76137-235">Specifies whether to search for packages with a module, a script, or both.</span></span> <span data-ttu-id="76137-236">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="76137-236">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="76137-237">Modul</span><span class="sxs-lookup"><span data-stu-id="76137-237">Module</span></span>
- <span data-ttu-id="76137-238">Skript</span><span class="sxs-lookup"><span data-stu-id="76137-238">Script</span></span>
- <span data-ttu-id="76137-239">Alla</span><span class="sxs-lookup"><span data-stu-id="76137-239">All</span></span>

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

### <span data-ttu-id="76137-240">-Confirm</span><span class="sxs-lookup"><span data-stu-id="76137-240">-Confirm</span></span>

<span data-ttu-id="76137-241">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="76137-241">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="76137-242">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="76137-242">-WhatIf</span></span>

<span data-ttu-id="76137-243">Visar vad som händer om `Install-Package` cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="76137-243">Shows what would happen if `Install-Package` cmdlet is run.</span></span> <span data-ttu-id="76137-244">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="76137-244">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="76137-245">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="76137-245">CommonParameters</span></span>

<span data-ttu-id="76137-246">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="76137-246">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="76137-247">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="76137-247">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="76137-248">INDATA</span><span class="sxs-lookup"><span data-stu-id="76137-248">INPUTS</span></span>

### <span data-ttu-id="76137-249">`Install-Package` accepterar ininformation från pipelinen.</span><span class="sxs-lookup"><span data-stu-id="76137-249">`Install-Package` accepts input from the pipeline.</span></span>

## <span data-ttu-id="76137-250">UTDATA</span><span class="sxs-lookup"><span data-stu-id="76137-250">OUTPUTS</span></span>

### <span data-ttu-id="76137-251">SoftwareIdentity []</span><span class="sxs-lookup"><span data-stu-id="76137-251">SoftwareIdentity[]</span></span>

## <span data-ttu-id="76137-252">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="76137-252">NOTES</span></span>

<span data-ttu-id="76137-253">Att inkludera en paket leverantör i ett kommando kan göra dynamiska parametrar tillgängliga för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="76137-253">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="76137-254">Dynamiska parametrar är speciella för en paket leverantör.</span><span class="sxs-lookup"><span data-stu-id="76137-254">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="76137-255">`Get-Help`Cmdleten listar en cmdlets parameter uppsättningar och inkluderar providerns parameter uppsättning.</span><span class="sxs-lookup"><span data-stu-id="76137-255">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span> <span data-ttu-id="76137-256">Till exempel `Install-Package` har **PowerShellGet** parameter uppsättning som innehåller `-NoPathUpdate` , `AllowClobber` , och `SkipPublisherCheck` .</span><span class="sxs-lookup"><span data-stu-id="76137-256">For example, `Install-Package` has the **PowerShellGet** parameter set that includes `-NoPathUpdate`, `AllowClobber`, and `SkipPublisherCheck`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="76137-257">Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1.</span><span class="sxs-lookup"><span data-stu-id="76137-257">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="76137-258">Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="76137-258">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="76137-259">Använd följande kommando för att se till att du använder TLS 1,2:</span><span class="sxs-lookup"><span data-stu-id="76137-259">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="76137-260">Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="76137-260">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="76137-261">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="76137-261">RELATED LINKS</span></span>

[<span data-ttu-id="76137-262">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="76137-262">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="76137-263">Find-Dscresource Keyword Supports</span><span class="sxs-lookup"><span data-stu-id="76137-263">Find-DscResource</span></span>](../PowershellGet/Find-DscResource.md)

[<span data-ttu-id="76137-264">Get – hjälp</span><span class="sxs-lookup"><span data-stu-id="76137-264">Get-Help</span></span>](../Microsoft.PowerShell.Core/Get-Help.md)

[<span data-ttu-id="76137-265">Get-Package</span><span class="sxs-lookup"><span data-stu-id="76137-265">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="76137-266">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="76137-266">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="76137-267">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="76137-267">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="76137-268">Sök-paket</span><span class="sxs-lookup"><span data-stu-id="76137-268">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="76137-269">Spara paket</span><span class="sxs-lookup"><span data-stu-id="76137-269">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="76137-270">Avinstallera paket</span><span class="sxs-lookup"><span data-stu-id="76137-270">Uninstall-Package</span></span>](Uninstall-Package.md)
