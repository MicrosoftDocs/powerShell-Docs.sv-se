---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 05/24/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/uninstall-package?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Package
ms.openlocfilehash: 6f22da7040413f64e9e96a7df57401a0701156bd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264530"
---
# <span data-ttu-id="28ecb-103">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="28ecb-103">Uninstall-Package</span></span>

## <span data-ttu-id="28ecb-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="28ecb-104">SYNOPSIS</span></span>
<span data-ttu-id="28ecb-105">Avinstallerar ett eller flera program varu paket.</span><span class="sxs-lookup"><span data-stu-id="28ecb-105">Uninstalls one or more software packages.</span></span>

## <span data-ttu-id="28ecb-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="28ecb-106">SYNTAX</span></span>

### <span data-ttu-id="28ecb-107">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="28ecb-107">PackageByInputObject</span></span>

```
Uninstall-Package [-InputObject] <SoftwareIdentity[]> [-AllVersions] [-Force] [-ForceBootstrap]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="28ecb-108">PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="28ecb-108">PackageBySearch</span></span>

```
Uninstall-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ProviderName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="28ecb-109">MSI: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="28ecb-109">msi:PackageByInputObject</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-AdditionalArguments <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="28ecb-110">MSI: PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="28ecb-110">msi:PackageBySearch</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-AdditionalArguments <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="28ecb-111">Program: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="28ecb-111">Programs:PackageByInputObject</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-IncludeWindowsInstaller] [-IncludeSystemComponent] [<CommonParameters>]
```

### <span data-ttu-id="28ecb-112">Program: PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="28ecb-112">Programs:PackageBySearch</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-IncludeWindowsInstaller] [-IncludeSystemComponent] [<CommonParameters>]
```

### <span data-ttu-id="28ecb-113">NuGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="28ecb-113">NuGet:PackageByInputObject</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### <span data-ttu-id="28ecb-114">NuGet: PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="28ecb-114">NuGet:PackageBySearch</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### <span data-ttu-id="28ecb-115">PowerShellGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="28ecb-115">PowerShellGet:PackageByInputObject</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-Scope <String>]
 [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber] [-SkipPublisherCheck]
 [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="28ecb-116">PowerShellGet: PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="28ecb-116">PowerShellGet:PackageBySearch</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-Scope <String>]
 [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber] [-SkipPublisherCheck]
 [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions] [<CommonParameters>]
```

## <span data-ttu-id="28ecb-117">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="28ecb-117">DESCRIPTION</span></span>

<span data-ttu-id="28ecb-118">`Uninstall-Package`Cmdleten avinstallerar ett eller flera program varu paket från den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="28ecb-118">The `Uninstall-Package` cmdlet uninstalls one or more software packages from the local computer.</span></span> <span data-ttu-id="28ecb-119">Använd cmdleten för att hitta installerade paket `Get-Package` .</span><span class="sxs-lookup"><span data-stu-id="28ecb-119">To find installed packages, use the `Get-Package` cmdlet.</span></span>

## <span data-ttu-id="28ecb-120">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="28ecb-120">EXAMPLES</span></span>

### <span data-ttu-id="28ecb-121">Exempel 1: Avinstallera ett paket</span><span class="sxs-lookup"><span data-stu-id="28ecb-121">Example 1: Uninstall a package</span></span>

<span data-ttu-id="28ecb-122">- `Uninstall-Package` Cmdleten avinstallerar paket.</span><span class="sxs-lookup"><span data-stu-id="28ecb-122">The `Uninstall-Package` cmdlet uninstalls packages.</span></span> <span data-ttu-id="28ecb-123">Parametern **Name** anger det paket som ska avinstalleras.</span><span class="sxs-lookup"><span data-stu-id="28ecb-123">The **Name** parameter specifies the package to uninstall.</span></span> <span data-ttu-id="28ecb-124">Om flera versioner av ett paket är installerade avinstalleras den senaste versionen.</span><span class="sxs-lookup"><span data-stu-id="28ecb-124">If multiple versions of a package are installed, the newest version is uninstalled.</span></span>

```
PS> Uninstall-Package -Name NuGet.Core
```

### <span data-ttu-id="28ecb-125">Exempel 2: Använd pipelinen för att avinstallera ett paket</span><span class="sxs-lookup"><span data-stu-id="28ecb-125">Example 2: Use the pipeline to uninstall a package</span></span>

<span data-ttu-id="28ecb-126">`Get-Package` söker efter ett särskilt paket och skickar **SoftwareIdentity** -objektet nedåt i pipelinen till `Uninsall-Package` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="28ecb-126">`Get-Package` locates a specific package and sends the **SoftwareIdentity** object down the pipeline to the `Uninsall-Package` cmdlet.</span></span>

```
PS> Get-Package -Name NuGet.Core -RequiredVersion 2.14.0 | Uninstall-Package
```

<span data-ttu-id="28ecb-127">`Get-Package`Cmdleten använder **namn** -och **RequiredVersion** -parametrarna för att ange ett paket.</span><span class="sxs-lookup"><span data-stu-id="28ecb-127">The `Get-Package` cmdlet uses the **Name** and **RequiredVersion** parameters to specify a package.</span></span>
<span data-ttu-id="28ecb-128">Ett **SoftwareIdentity** -objekt skickas ned pipelinen.</span><span class="sxs-lookup"><span data-stu-id="28ecb-128">A **SoftwareIdentity** object is sent down the pipeline.</span></span> <span data-ttu-id="28ecb-129">`Uninstall-Package`Cmdleten tar emot objektet som en **InputObject** och tar bort paketet.</span><span class="sxs-lookup"><span data-stu-id="28ecb-129">The `Uninstall-Package` cmdlet receives the object as an **InputObject** and removes the package.</span></span>

<span data-ttu-id="28ecb-130">Alternativt `Uninstall-Package` kan cmdleten ange ett värde för parametern **InputObject** :</span><span class="sxs-lookup"><span data-stu-id="28ecb-130">As an alternative, the `Uninstall-Package` cmdlet can specify a value for the **InputObject** parameter:</span></span>

`Uninstall-Package -InputObject ( Get-Package -Name NuGet.Core -RequiredVersion 2.14.0 )`

## <span data-ttu-id="28ecb-131">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="28ecb-131">PARAMETERS</span></span>

### <span data-ttu-id="28ecb-132">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="28ecb-132">-AllowClobber</span></span>

<span data-ttu-id="28ecb-133">Åsidosätter varnings meddelanden om konflikter med befintliga kommandon.</span><span class="sxs-lookup"><span data-stu-id="28ecb-133">Overrides warning messages about conflicts with existing commands.</span></span> <span data-ttu-id="28ecb-134">Skriver över befintliga kommandon som har samma namn som kommandon som installeras.</span><span class="sxs-lookup"><span data-stu-id="28ecb-134">Overwrites existing commands that have the same name as commands being installed.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="28ecb-135">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="28ecb-135">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="28ecb-136">Tillåter att paket som marker ATS som för hands version avinstalleras.</span><span class="sxs-lookup"><span data-stu-id="28ecb-136">Allows packages marked as prerelease to be uninstalled.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="28ecb-137">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="28ecb-137">-AllVersions</span></span>

<span data-ttu-id="28ecb-138">Anger att den här cmdleten avinstallerar alla versioner av paketet.</span><span class="sxs-lookup"><span data-stu-id="28ecb-138">Indicates that this cmdlet uninstalls all versions of the package.</span></span>

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

### <span data-ttu-id="28ecb-139">-Mål</span><span class="sxs-lookup"><span data-stu-id="28ecb-139">-Destination</span></span>

<span data-ttu-id="28ecb-140">Anger en sträng i sökvägen till det inmatade objektet.</span><span class="sxs-lookup"><span data-stu-id="28ecb-140">Specifies a string of the path to the input object.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageByInputObject, NuGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="28ecb-141">-ExcludeVersion</span><span class="sxs-lookup"><span data-stu-id="28ecb-141">-ExcludeVersion</span></span>

<span data-ttu-id="28ecb-142">Byt för att utesluta versions numret i mappsökvägen.</span><span class="sxs-lookup"><span data-stu-id="28ecb-142">Switch to exclude the version number in the folder path.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageByInputObject, NuGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="28ecb-143">-Force</span><span class="sxs-lookup"><span data-stu-id="28ecb-143">-Force</span></span>

<span data-ttu-id="28ecb-144">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="28ecb-144">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="28ecb-145">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="28ecb-145">-ForceBootstrap</span></span>

<span data-ttu-id="28ecb-146">Tvingar **PackageManagement** att automatiskt installera paket leverantören för det angivna paketet.</span><span class="sxs-lookup"><span data-stu-id="28ecb-146">Forces **PackageManagement** to automatically install the package provider for the specified package.</span></span>

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

### <span data-ttu-id="28ecb-147">– InputObject</span><span class="sxs-lookup"><span data-stu-id="28ecb-147">-InputObject</span></span>

<span data-ttu-id="28ecb-148">Accepterar pipeline-inflöde som anger paketets **SoftwareIdentity** -objekt från `Get-Package` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="28ecb-148">Accepts pipeline input that specifies the package's **SoftwareIdentity** object from the `Get-Package` cmdlet.</span></span> <span data-ttu-id="28ecb-149">**InputObject** accepterar **SoftwareIdentity** -objektet som ett `Get-Package` värde eller en variabel som innehåller objektet.</span><span class="sxs-lookup"><span data-stu-id="28ecb-149">**InputObject** accepts the **SoftwareIdentity** object as a `Get-Package` value or a variable that contains the object.</span></span>

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

### <span data-ttu-id="28ecb-150">-InstallUpdate</span><span class="sxs-lookup"><span data-stu-id="28ecb-150">-InstallUpdate</span></span>

<span data-ttu-id="28ecb-151">Anger att `Uninstall-Package` avinstallerar uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="28ecb-151">Indicates that `Uninstall-Package` uninstalls updates.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="28ecb-152">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="28ecb-152">-MaximumVersion</span></span>

<span data-ttu-id="28ecb-153">Anger den högsta tillåtna paket version som du vill avinstallera.</span><span class="sxs-lookup"><span data-stu-id="28ecb-153">Specifies the maximum allowed package version that you want to uninstall.</span></span> <span data-ttu-id="28ecb-154">Om du inte anger den här parametern `Uninstall-Package` avinstallerar du paketets senaste version.</span><span class="sxs-lookup"><span data-stu-id="28ecb-154">If you don't specify this parameter, `Uninstall-Package` uninstalls the package's newest version.</span></span>

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

### <span data-ttu-id="28ecb-155">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="28ecb-155">-MinimumVersion</span></span>

<span data-ttu-id="28ecb-156">Anger den minsta tillåtna paket version som du vill avinstallera.</span><span class="sxs-lookup"><span data-stu-id="28ecb-156">Specifies the minimum allowed package version that you want to uninstall.</span></span> <span data-ttu-id="28ecb-157">Om du inte lägger till den här parametern `Uninstall-Package` avinstallerar paketets senaste version som uppfyller de versioner som anges i parametern **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="28ecb-157">If you don't add this parameter, `Uninstall-Package` uninstalls the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="28ecb-158">-Name</span><span class="sxs-lookup"><span data-stu-id="28ecb-158">-Name</span></span>

<span data-ttu-id="28ecb-159">Anger ett eller flera paket namn.</span><span class="sxs-lookup"><span data-stu-id="28ecb-159">Specifies one or more package names.</span></span> <span data-ttu-id="28ecb-160">Flera paket namn måste avgränsas med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="28ecb-160">Multiple package names must be separated by commas.</span></span>

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

### <span data-ttu-id="28ecb-161">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="28ecb-161">-NoPathUpdate</span></span>

<span data-ttu-id="28ecb-162">**NoPathUpdate** gäller endast för `Install-Script` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="28ecb-162">**NoPathUpdate** only applies to the `Install-Script` cmdlet.</span></span> <span data-ttu-id="28ecb-163">**NoPathUpdate** är en dynamisk parameter som lagts till av providern och som inte stöds av `Uninstall-Package` .</span><span class="sxs-lookup"><span data-stu-id="28ecb-163">**NoPathUpdate** is a dynamic parameter added by the provider and isn't supported by `Uninstall-Package`.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="28ecb-164">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="28ecb-164">-PackageManagementProvider</span></span>

<span data-ttu-id="28ecb-165">Anger **PackageManagement** -providern.</span><span class="sxs-lookup"><span data-stu-id="28ecb-165">Specifies the **PackageManagement** provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="28ecb-166">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="28ecb-166">-ProviderName</span></span>

<span data-ttu-id="28ecb-167">Anger ett eller flera paket leverantörs namn att söka efter paket.</span><span class="sxs-lookup"><span data-stu-id="28ecb-167">Specifies one or more package provider names to search for packages.</span></span> <span data-ttu-id="28ecb-168">Du kan hämta paket leverantörs namn genom att köra `Get-PackageProvider` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="28ecb-168">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>

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

### <span data-ttu-id="28ecb-169">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="28ecb-169">-RequiredVersion</span></span>

<span data-ttu-id="28ecb-170">Anger den exakta versionen av paketet som du vill avinstallera.</span><span class="sxs-lookup"><span data-stu-id="28ecb-170">Specifies the exact allowed version of the package that you want to uninstall.</span></span> <span data-ttu-id="28ecb-171">Om du inte lägger till den här parametern `Uninstall-Package` avinstallerar paketets senaste version som uppfyller de versioner som anges i parametern **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="28ecb-171">If you don't add this parameter, `Uninstall-Package` uninstalls the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="28ecb-172">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="28ecb-172">-Scope</span></span>

<span data-ttu-id="28ecb-173">Anger omfånget som paketet ska avinstalleras för.</span><span class="sxs-lookup"><span data-stu-id="28ecb-173">Specifies the scope for which to uninstall the package.</span></span> <span data-ttu-id="28ecb-174">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="28ecb-174">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="28ecb-175">CurrentUser</span><span class="sxs-lookup"><span data-stu-id="28ecb-175">CurrentUser</span></span>
- <span data-ttu-id="28ecb-176">AllUsers</span><span class="sxs-lookup"><span data-stu-id="28ecb-176">AllUsers</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:PackageByInputObject, NuGet:PackageBySearch, PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="28ecb-177">-SkipDependencies</span><span class="sxs-lookup"><span data-stu-id="28ecb-177">-SkipDependencies</span></span>

<span data-ttu-id="28ecb-178">Hoppar över avinstallationen av program varu beroenden.</span><span class="sxs-lookup"><span data-stu-id="28ecb-178">Skips the uninstallation of software dependencies.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:PackageByInputObject, NuGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="28ecb-179">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="28ecb-179">-SkipPublisherCheck</span></span>

<span data-ttu-id="28ecb-180">Gör att du kan hämta en paket version som är nyare än den installerade versionen.</span><span class="sxs-lookup"><span data-stu-id="28ecb-180">Allows you to get a package version that is newer than your installed version.</span></span> <span data-ttu-id="28ecb-181">Till exempel ett installerat paket som har signerats digitalt av en betrodd utgivare, men en ny version inte har signerats digitalt.</span><span class="sxs-lookup"><span data-stu-id="28ecb-181">For example, an installed package that is digitally signed by a trusted publisher but a new version isn't digitally signed.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="28ecb-182">-Typ</span><span class="sxs-lookup"><span data-stu-id="28ecb-182">-Type</span></span>

<span data-ttu-id="28ecb-183">Anger om du vill söka efter paket med en modul, ett skript eller både och.</span><span class="sxs-lookup"><span data-stu-id="28ecb-183">Specifies whether to search for packages with a module, a script, or both.</span></span> <span data-ttu-id="28ecb-184">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="28ecb-184">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="28ecb-185">Modul</span><span class="sxs-lookup"><span data-stu-id="28ecb-185">Module</span></span>
- <span data-ttu-id="28ecb-186">Skript</span><span class="sxs-lookup"><span data-stu-id="28ecb-186">Script</span></span>
- <span data-ttu-id="28ecb-187">Alla</span><span class="sxs-lookup"><span data-stu-id="28ecb-187">All</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:PackageByInputObject, PowerShellGet:PackageBySearch
Aliases:
Accepted values: Module, Script, All

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="28ecb-188">-Confirm</span><span class="sxs-lookup"><span data-stu-id="28ecb-188">-Confirm</span></span>

<span data-ttu-id="28ecb-189">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="28ecb-189">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="28ecb-190">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="28ecb-190">-WhatIf</span></span>

<span data-ttu-id="28ecb-191">Visar vad som händer om `Uninstall-Package` cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="28ecb-191">Shows what would happen if `Uninstall-Package` cmdlet is run.</span></span> <span data-ttu-id="28ecb-192">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="28ecb-192">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="28ecb-193">-AdditionalArguments</span><span class="sxs-lookup"><span data-stu-id="28ecb-193">-AdditionalArguments</span></span>

<span data-ttu-id="28ecb-194">Anger ytterligare argument.</span><span class="sxs-lookup"><span data-stu-id="28ecb-194">Specifies additional arguments.</span></span>

```yaml
Type: System.String[]
Parameter Sets: msi:PackageByInputObject, msi:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="28ecb-195">-IncludeSystemComponent</span><span class="sxs-lookup"><span data-stu-id="28ecb-195">-IncludeSystemComponent</span></span>

<span data-ttu-id="28ecb-196">Anger att den här cmdleten avinstallerar system komponenter.</span><span class="sxs-lookup"><span data-stu-id="28ecb-196">Specifies that this cmdlet uninstalls system components.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Programs:PackageByInputObject, Programs:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="28ecb-197">-IncludeWindowsInstaller</span><span class="sxs-lookup"><span data-stu-id="28ecb-197">-IncludeWindowsInstaller</span></span>

<span data-ttu-id="28ecb-198">Anger att den här cmdleten avinstallerar paketet via Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="28ecb-198">Indicates that this cmdlet uninstalls the package through Windows Installer.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Programs:PackageByInputObject, Programs:PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="28ecb-199">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="28ecb-199">CommonParameters</span></span>

<span data-ttu-id="28ecb-200">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="28ecb-200">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="28ecb-201">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="28ecb-201">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="28ecb-202">INDATA</span><span class="sxs-lookup"><span data-stu-id="28ecb-202">INPUTS</span></span>

### <span data-ttu-id="28ecb-203">`Uninstall-Package` accepterar **SoftwareIdentity** -objekt från pipelinen som inmatade.</span><span class="sxs-lookup"><span data-stu-id="28ecb-203">`Uninstall-Package` accepts **SoftwareIdentity** objects from the pipeline as input.</span></span>

## <span data-ttu-id="28ecb-204">UTDATA</span><span class="sxs-lookup"><span data-stu-id="28ecb-204">OUTPUTS</span></span>

### <span data-ttu-id="28ecb-205">`Uninstall-Package` genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="28ecb-205">`Uninstall-Package` doesn't generate any output.</span></span>

## <span data-ttu-id="28ecb-206">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="28ecb-206">NOTES</span></span>

<span data-ttu-id="28ecb-207">Att inkludera en paket leverantör i ett kommando kan göra dynamiska parametrar tillgängliga för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="28ecb-207">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="28ecb-208">Dynamiska parametrar är speciella för en paket leverantör.</span><span class="sxs-lookup"><span data-stu-id="28ecb-208">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="28ecb-209">`Get-Help`Cmdleten listar en cmdlets parameter uppsättningar och inkluderar providerns parameter uppsättning.</span><span class="sxs-lookup"><span data-stu-id="28ecb-209">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span> <span data-ttu-id="28ecb-210">Till exempel `Uninstall-Package` har **PowerShellGet** parameter uppsättning som innehåller `-NoPathUpdate` , `AllowClobber` , och `SkipPublisherCheck` .</span><span class="sxs-lookup"><span data-stu-id="28ecb-210">For example, `Uninstall-Package` has the **PowerShellGet** parameter set that includes `-NoPathUpdate`, `AllowClobber`, and `SkipPublisherCheck`.</span></span>

## <span data-ttu-id="28ecb-211">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="28ecb-211">RELATED LINKS</span></span>

[<span data-ttu-id="28ecb-212">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="28ecb-212">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="28ecb-213">Sök-paket</span><span class="sxs-lookup"><span data-stu-id="28ecb-213">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="28ecb-214">Get-Package</span><span class="sxs-lookup"><span data-stu-id="28ecb-214">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="28ecb-215">Installationspaket</span><span class="sxs-lookup"><span data-stu-id="28ecb-215">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="28ecb-216">Spara paket</span><span class="sxs-lookup"><span data-stu-id="28ecb-216">Save-Package</span></span>](Save-Package.md)
