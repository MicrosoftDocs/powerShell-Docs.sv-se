---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 05/24/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/uninstall-package?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Uninstall-Package
ms.openlocfilehash: 4be80765181e045f24b1f90243de21f38533bfba
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265671"
---
# <span data-ttu-id="59b08-103">Uninstall-Package</span><span class="sxs-lookup"><span data-stu-id="59b08-103">Uninstall-Package</span></span>

## <span data-ttu-id="59b08-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="59b08-104">SYNOPSIS</span></span>
<span data-ttu-id="59b08-105">Avinstallerar ett eller flera program varu paket.</span><span class="sxs-lookup"><span data-stu-id="59b08-105">Uninstalls one or more software packages.</span></span>

## <span data-ttu-id="59b08-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="59b08-106">SYNTAX</span></span>

### <span data-ttu-id="59b08-107">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="59b08-107">PackageByInputObject</span></span>

```
Uninstall-Package [-InputObject] <SoftwareIdentity[]> [-AllVersions] [-Force] [-ForceBootstrap]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="59b08-108">PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="59b08-108">PackageBySearch</span></span>

```
Uninstall-Package [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-ProviderName <String[]>] [<CommonParameters>]
```

### <span data-ttu-id="59b08-109">NuGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="59b08-109">NuGet:PackageByInputObject</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### <span data-ttu-id="59b08-110">NuGet: PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="59b08-110">NuGet:PackageBySearch</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### <span data-ttu-id="59b08-111">PowerShellGet: PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="59b08-111">PowerShellGet:PackageByInputObject</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-Scope <String>]
 [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber] [-SkipPublisherCheck]
 [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions] [<CommonParameters>]
```

### <span data-ttu-id="59b08-112">PowerShellGet: PackageBySearch</span><span class="sxs-lookup"><span data-stu-id="59b08-112">PowerShellGet:PackageBySearch</span></span>

```
Uninstall-Package [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-Scope <String>]
 [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber] [-SkipPublisherCheck]
 [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions] [<CommonParameters>]
```

## <span data-ttu-id="59b08-113">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="59b08-113">DESCRIPTION</span></span>

<span data-ttu-id="59b08-114">`Uninstall-Package`Cmdleten avinstallerar ett eller flera program varu paket från den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="59b08-114">The `Uninstall-Package` cmdlet uninstalls one or more software packages from the local computer.</span></span> <span data-ttu-id="59b08-115">Använd cmdleten för att hitta installerade paket `Get-Package` .</span><span class="sxs-lookup"><span data-stu-id="59b08-115">To find installed packages, use the `Get-Package` cmdlet.</span></span>

## <span data-ttu-id="59b08-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="59b08-116">EXAMPLES</span></span>

### <span data-ttu-id="59b08-117">Exempel 1: Avinstallera ett paket</span><span class="sxs-lookup"><span data-stu-id="59b08-117">Example 1: Uninstall a package</span></span>

<span data-ttu-id="59b08-118">- `Uninstall-Package` Cmdleten avinstallerar paket.</span><span class="sxs-lookup"><span data-stu-id="59b08-118">The `Uninstall-Package` cmdlet uninstalls packages.</span></span> <span data-ttu-id="59b08-119">Parametern **Name** anger det paket som ska avinstalleras.</span><span class="sxs-lookup"><span data-stu-id="59b08-119">The **Name** parameter specifies the package to uninstall.</span></span> <span data-ttu-id="59b08-120">Om flera versioner av ett paket är installerade avinstalleras den senaste versionen.</span><span class="sxs-lookup"><span data-stu-id="59b08-120">If multiple versions of a package are installed, the newest version is uninstalled.</span></span>

```
PS> Uninstall-Package -Name NuGet.Core
```

### <span data-ttu-id="59b08-121">Exempel 2: Använd pipelinen för att avinstallera ett paket</span><span class="sxs-lookup"><span data-stu-id="59b08-121">Example 2: Use the pipeline to uninstall a package</span></span>

<span data-ttu-id="59b08-122">`Get-Package` söker efter ett särskilt paket och skickar **SoftwareIdentity** -objektet nedåt i pipelinen till `Uninsall-Package` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="59b08-122">`Get-Package` locates a specific package and sends the **SoftwareIdentity** object down the pipeline to the `Uninsall-Package` cmdlet.</span></span>

```
PS> Get-Package -Name NuGet.Core -RequiredVersion 2.14.0 | Uninstall-Package
```

<span data-ttu-id="59b08-123">`Get-Package`Cmdleten använder **namn** -och **RequiredVersion** -parametrarna för att ange ett paket.</span><span class="sxs-lookup"><span data-stu-id="59b08-123">The `Get-Package` cmdlet uses the **Name** and **RequiredVersion** parameters to specify a package.</span></span>
<span data-ttu-id="59b08-124">Ett **SoftwareIdentity** -objekt skickas ned pipelinen.</span><span class="sxs-lookup"><span data-stu-id="59b08-124">A **SoftwareIdentity** object is sent down the pipeline.</span></span> <span data-ttu-id="59b08-125">`Uninstall-Package`Cmdleten tar emot objektet som en **InputObject** och tar bort paketet.</span><span class="sxs-lookup"><span data-stu-id="59b08-125">The `Uninstall-Package` cmdlet receives the object as an **InputObject** and removes the package.</span></span>

<span data-ttu-id="59b08-126">Alternativt `Uninstall-Package` kan cmdleten ange ett värde för parametern **InputObject** :</span><span class="sxs-lookup"><span data-stu-id="59b08-126">As an alternative, the `Uninstall-Package` cmdlet can specify a value for the **InputObject** parameter:</span></span>

`Uninstall-Package -InputObject ( Get-Package -Name NuGet.Core -RequiredVersion 2.14.0 )`

## <span data-ttu-id="59b08-127">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="59b08-127">PARAMETERS</span></span>

### <span data-ttu-id="59b08-128">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="59b08-128">-AllowClobber</span></span>

<span data-ttu-id="59b08-129">Åsidosätter varnings meddelanden om konflikter med befintliga kommandon.</span><span class="sxs-lookup"><span data-stu-id="59b08-129">Overrides warning messages about conflicts with existing commands.</span></span> <span data-ttu-id="59b08-130">Skriver över befintliga kommandon som har samma namn som kommandon som installeras.</span><span class="sxs-lookup"><span data-stu-id="59b08-130">Overwrites existing commands that have the same name as commands being installed.</span></span>

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

### <span data-ttu-id="59b08-131">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="59b08-131">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="59b08-132">Tillåter att paket som marker ATS som för hands version avinstalleras.</span><span class="sxs-lookup"><span data-stu-id="59b08-132">Allows packages marked as prerelease to be uninstalled.</span></span>

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

### <span data-ttu-id="59b08-133">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="59b08-133">-AllVersions</span></span>

<span data-ttu-id="59b08-134">Anger att den här cmdleten avinstallerar alla versioner av paketet.</span><span class="sxs-lookup"><span data-stu-id="59b08-134">Indicates that this cmdlet uninstalls all versions of the package.</span></span>

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

### <span data-ttu-id="59b08-135">-Mål</span><span class="sxs-lookup"><span data-stu-id="59b08-135">-Destination</span></span>

<span data-ttu-id="59b08-136">Anger en sträng i sökvägen till det inmatade objektet.</span><span class="sxs-lookup"><span data-stu-id="59b08-136">Specifies a string of the path to the input object.</span></span>

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

### <span data-ttu-id="59b08-137">-ExcludeVersion</span><span class="sxs-lookup"><span data-stu-id="59b08-137">-ExcludeVersion</span></span>

<span data-ttu-id="59b08-138">Byt för att utesluta versions numret i mappsökvägen.</span><span class="sxs-lookup"><span data-stu-id="59b08-138">Switch to exclude the version number in the folder path.</span></span>

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

### <span data-ttu-id="59b08-139">-Force</span><span class="sxs-lookup"><span data-stu-id="59b08-139">-Force</span></span>

<span data-ttu-id="59b08-140">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="59b08-140">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="59b08-141">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="59b08-141">-ForceBootstrap</span></span>

<span data-ttu-id="59b08-142">Tvingar **PackageManagement** att automatiskt installera paket leverantören för det angivna paketet.</span><span class="sxs-lookup"><span data-stu-id="59b08-142">Forces **PackageManagement** to automatically install the package provider for the specified package.</span></span>

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

### <span data-ttu-id="59b08-143">– InputObject</span><span class="sxs-lookup"><span data-stu-id="59b08-143">-InputObject</span></span>

<span data-ttu-id="59b08-144">Accepterar pipeline-inflöde som anger paketets **SoftwareIdentity** -objekt från `Get-Package` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="59b08-144">Accepts pipeline input that specifies the package's **SoftwareIdentity** object from the `Get-Package` cmdlet.</span></span> <span data-ttu-id="59b08-145">**InputObject** accepterar **SoftwareIdentity** -objektet som ett `Get-Package` värde eller en variabel som innehåller objektet.</span><span class="sxs-lookup"><span data-stu-id="59b08-145">**InputObject** accepts the **SoftwareIdentity** object as a `Get-Package` value or a variable that contains the object.</span></span>

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

### <span data-ttu-id="59b08-146">-InstallUpdate</span><span class="sxs-lookup"><span data-stu-id="59b08-146">-InstallUpdate</span></span>

<span data-ttu-id="59b08-147">Anger att `Uninstall-Package` avinstallerar uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="59b08-147">Indicates that `Uninstall-Package` uninstalls updates.</span></span>

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

### <span data-ttu-id="59b08-148">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="59b08-148">-MaximumVersion</span></span>

<span data-ttu-id="59b08-149">Anger den högsta tillåtna paket version som du vill avinstallera.</span><span class="sxs-lookup"><span data-stu-id="59b08-149">Specifies the maximum allowed package version that you want to uninstall.</span></span> <span data-ttu-id="59b08-150">Om du inte anger den här parametern `Uninstall-Package` avinstallerar du paketets senaste version.</span><span class="sxs-lookup"><span data-stu-id="59b08-150">If you don't specify this parameter, `Uninstall-Package` uninstalls the package's newest version.</span></span>

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

### <span data-ttu-id="59b08-151">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="59b08-151">-MinimumVersion</span></span>

<span data-ttu-id="59b08-152">Anger den minsta tillåtna paket version som du vill avinstallera.</span><span class="sxs-lookup"><span data-stu-id="59b08-152">Specifies the minimum allowed package version that you want to uninstall.</span></span> <span data-ttu-id="59b08-153">Om du inte lägger till den här parametern `Uninstall-Package` avinstallerar paketets senaste version som uppfyller de versioner som anges i parametern **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="59b08-153">If you don't add this parameter, `Uninstall-Package` uninstalls the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="59b08-154">-Name</span><span class="sxs-lookup"><span data-stu-id="59b08-154">-Name</span></span>

<span data-ttu-id="59b08-155">Anger ett eller flera paket namn.</span><span class="sxs-lookup"><span data-stu-id="59b08-155">Specifies one or more package names.</span></span> <span data-ttu-id="59b08-156">Flera paket namn måste avgränsas med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="59b08-156">Multiple package names must be separated by commas.</span></span>

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

### <span data-ttu-id="59b08-157">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="59b08-157">-NoPathUpdate</span></span>

<span data-ttu-id="59b08-158">**NoPathUpdate** gäller endast för `Install-Script` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="59b08-158">**NoPathUpdate** only applies to the `Install-Script` cmdlet.</span></span> <span data-ttu-id="59b08-159">**NoPathUpdate** är en dynamisk parameter som lagts till av providern och som inte stöds av `Uninstall-Package` .</span><span class="sxs-lookup"><span data-stu-id="59b08-159">**NoPathUpdate** is a dynamic parameter added by the provider and isn't supported by `Uninstall-Package`.</span></span>

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

### <span data-ttu-id="59b08-160">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="59b08-160">-PackageManagementProvider</span></span>

<span data-ttu-id="59b08-161">Anger **PackageManagement** -providern.</span><span class="sxs-lookup"><span data-stu-id="59b08-161">Specifies the **PackageManagement** provider.</span></span>

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

### <span data-ttu-id="59b08-162">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="59b08-162">-ProviderName</span></span>

<span data-ttu-id="59b08-163">Anger ett eller flera paket leverantörs namn att söka efter paket.</span><span class="sxs-lookup"><span data-stu-id="59b08-163">Specifies one or more package provider names to search for packages.</span></span> <span data-ttu-id="59b08-164">Du kan hämta paket leverantörs namn genom att köra `Get-PackageProvider` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="59b08-164">You can get package provider names by running the `Get-PackageProvider` cmdlet.</span></span>

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

### <span data-ttu-id="59b08-165">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="59b08-165">-RequiredVersion</span></span>

<span data-ttu-id="59b08-166">Anger den exakta versionen av paketet som du vill avinstallera.</span><span class="sxs-lookup"><span data-stu-id="59b08-166">Specifies the exact allowed version of the package that you want to uninstall.</span></span> <span data-ttu-id="59b08-167">Om du inte lägger till den här parametern `Uninstall-Package` avinstallerar paketets senaste version som uppfyller de versioner som anges i parametern **MaximumVersion** .</span><span class="sxs-lookup"><span data-stu-id="59b08-167">If you don't add this parameter, `Uninstall-Package` uninstalls the package's newest version that satisfies any version specified by the **MaximumVersion** parameter.</span></span>

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

### <span data-ttu-id="59b08-168">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="59b08-168">-Scope</span></span>

<span data-ttu-id="59b08-169">Anger omfånget som paketet ska avinstalleras för.</span><span class="sxs-lookup"><span data-stu-id="59b08-169">Specifies the scope for which to uninstall the package.</span></span> <span data-ttu-id="59b08-170">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="59b08-170">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="59b08-171">CurrentUser</span><span class="sxs-lookup"><span data-stu-id="59b08-171">CurrentUser</span></span>
- <span data-ttu-id="59b08-172">AllUsers</span><span class="sxs-lookup"><span data-stu-id="59b08-172">AllUsers</span></span>

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

### <span data-ttu-id="59b08-173">-SkipDependencies</span><span class="sxs-lookup"><span data-stu-id="59b08-173">-SkipDependencies</span></span>

<span data-ttu-id="59b08-174">Hoppar över avinstallationen av program varu beroenden.</span><span class="sxs-lookup"><span data-stu-id="59b08-174">Skips the uninstallation of software dependencies.</span></span>

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

### <span data-ttu-id="59b08-175">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="59b08-175">-SkipPublisherCheck</span></span>

<span data-ttu-id="59b08-176">Gör att du kan hämta en paket version som är nyare än den installerade versionen.</span><span class="sxs-lookup"><span data-stu-id="59b08-176">Allows you to get a package version that is newer than your installed version.</span></span> <span data-ttu-id="59b08-177">Till exempel ett installerat paket som har signerats digitalt av en betrodd utgivare, men en ny version inte har signerats digitalt.</span><span class="sxs-lookup"><span data-stu-id="59b08-177">For example, an installed package that is digitally signed by a trusted publisher but a new version isn't digitally signed.</span></span>

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

### <span data-ttu-id="59b08-178">-Typ</span><span class="sxs-lookup"><span data-stu-id="59b08-178">-Type</span></span>

<span data-ttu-id="59b08-179">Anger om du vill söka efter paket med en modul, ett skript eller både och.</span><span class="sxs-lookup"><span data-stu-id="59b08-179">Specifies whether to search for packages with a module, a script, or both.</span></span> <span data-ttu-id="59b08-180">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="59b08-180">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="59b08-181">Modul</span><span class="sxs-lookup"><span data-stu-id="59b08-181">Module</span></span>
- <span data-ttu-id="59b08-182">Skript</span><span class="sxs-lookup"><span data-stu-id="59b08-182">Script</span></span>
- <span data-ttu-id="59b08-183">Alla</span><span class="sxs-lookup"><span data-stu-id="59b08-183">All</span></span>

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

### <span data-ttu-id="59b08-184">-Confirm</span><span class="sxs-lookup"><span data-stu-id="59b08-184">-Confirm</span></span>

<span data-ttu-id="59b08-185">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="59b08-185">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="59b08-186">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="59b08-186">-WhatIf</span></span>

<span data-ttu-id="59b08-187">Visar vad som händer om `Uninstall-Package` cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="59b08-187">Shows what would happen if `Uninstall-Package` cmdlet is run.</span></span> <span data-ttu-id="59b08-188">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="59b08-188">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="59b08-189">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="59b08-189">CommonParameters</span></span>

<span data-ttu-id="59b08-190">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="59b08-190">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="59b08-191">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="59b08-191">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="59b08-192">INDATA</span><span class="sxs-lookup"><span data-stu-id="59b08-192">INPUTS</span></span>

### <span data-ttu-id="59b08-193">`Uninstall-Package` accepterar **SoftwareIdentity** -objekt från pipelinen som inmatade.</span><span class="sxs-lookup"><span data-stu-id="59b08-193">`Uninstall-Package` accepts **SoftwareIdentity** objects from the pipeline as input.</span></span>

## <span data-ttu-id="59b08-194">UTDATA</span><span class="sxs-lookup"><span data-stu-id="59b08-194">OUTPUTS</span></span>

### <span data-ttu-id="59b08-195">`Uninstall-Package` genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="59b08-195">`Uninstall-Package` doesn't generate any output.</span></span>

## <span data-ttu-id="59b08-196">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="59b08-196">NOTES</span></span>

<span data-ttu-id="59b08-197">Att inkludera en paket leverantör i ett kommando kan göra dynamiska parametrar tillgängliga för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="59b08-197">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="59b08-198">Dynamiska parametrar är speciella för en paket leverantör.</span><span class="sxs-lookup"><span data-stu-id="59b08-198">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="59b08-199">`Get-Help`Cmdleten listar en cmdlets parameter uppsättningar och inkluderar providerns parameter uppsättning.</span><span class="sxs-lookup"><span data-stu-id="59b08-199">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span> <span data-ttu-id="59b08-200">Till exempel `Uninstall-Package` har **PowerShellGet** parameter uppsättning som innehåller `-NoPathUpdate` , `AllowClobber` , och `SkipPublisherCheck` .</span><span class="sxs-lookup"><span data-stu-id="59b08-200">For example, `Uninstall-Package` has the **PowerShellGet** parameter set that includes `-NoPathUpdate`, `AllowClobber`, and `SkipPublisherCheck`.</span></span>

## <span data-ttu-id="59b08-201">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="59b08-201">RELATED LINKS</span></span>

[<span data-ttu-id="59b08-202">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="59b08-202">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="59b08-203">Sök-paket</span><span class="sxs-lookup"><span data-stu-id="59b08-203">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="59b08-204">Get-Package</span><span class="sxs-lookup"><span data-stu-id="59b08-204">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="59b08-205">Installationspaket</span><span class="sxs-lookup"><span data-stu-id="59b08-205">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="59b08-206">Spara paket</span><span class="sxs-lookup"><span data-stu-id="59b08-206">Save-Package</span></span>](Save-Package.md)
