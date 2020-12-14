---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 05/22/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-package?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Package
ms.openlocfilehash: bac0fe878a8dd370bda159d785740a4692ae6479
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94890584"
---
# <span data-ttu-id="9b091-103">Get-Package</span><span class="sxs-lookup"><span data-stu-id="9b091-103">Get-Package</span></span>

## <span data-ttu-id="9b091-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="9b091-104">SYNOPSIS</span></span>
<span data-ttu-id="9b091-105">Returnerar en lista med alla program varu paket som har installerats med **PackageManagement**.</span><span class="sxs-lookup"><span data-stu-id="9b091-105">Returns a list of all software packages that were installed with **PackageManagement**.</span></span>

## <span data-ttu-id="9b091-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9b091-106">SYNTAX</span></span>

### <span data-ttu-id="9b091-107">NuGet</span><span class="sxs-lookup"><span data-stu-id="9b091-107">NuGet</span></span>

```
Get-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-ProviderName <String[]>]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### <span data-ttu-id="9b091-108">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="9b091-108">PowerShellGet</span></span>

```
Get-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-ProviderName <String[]>]
 [-Scope <String>] [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions]
 [<CommonParameters>]
```

## <span data-ttu-id="9b091-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="9b091-109">DESCRIPTION</span></span>

<span data-ttu-id="9b091-110">`Get-Package`Cmdleten returnerar en lista över alla program varu paket på den lokala datorn som installerades med **PackageManagement**.</span><span class="sxs-lookup"><span data-stu-id="9b091-110">The `Get-Package` cmdlet returns a list of all software packages on the local computer that were installed with **PackageManagement**.</span></span> <span data-ttu-id="9b091-111">Du kan köra `Get-Package` på fjärrdatorer genom att köra den som en del av ett `Invoke-Command` `Enter-PSSession` kommando eller skript.</span><span class="sxs-lookup"><span data-stu-id="9b091-111">You can run `Get-Package` on remote computers by running it as part of an `Invoke-Command` or `Enter-PSSession` command or script.</span></span>

## <span data-ttu-id="9b091-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="9b091-112">EXAMPLES</span></span>

### <span data-ttu-id="9b091-113">Exempel 1: Hämta alla installerade paket</span><span class="sxs-lookup"><span data-stu-id="9b091-113">Example 1: Get all installed packages</span></span>

<span data-ttu-id="9b091-114">`Get-Package`Cmdlet: en hämtar alla paket som är installerade på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="9b091-114">The `Get-Package` cmdlet gets all packages that are installed on the local computer.</span></span>

```powershell
Get-Package
```

```Output
Name           Version      Source                                     ProviderName
----           -------      ------                                     ------------
posh-git       0.7.3        https://www.powershellgallery.com/api/v2   PowerShellGet
```

### <span data-ttu-id="9b091-115">Exempel 2: Hämta paket som är installerade på en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="9b091-115">Example 2: Get packages that are installed on a remote computer</span></span>

<span data-ttu-id="9b091-116">Det här kommandot hämtar en lista över paket som har installerats av **PackageManagement** på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="9b091-116">This command gets a list of packages that were installed by **PackageManagement** on a remote computer.</span></span> <span data-ttu-id="9b091-117">Med det här kommandot kan du ange användarens lösen ord.</span><span class="sxs-lookup"><span data-stu-id="9b091-117">This command prompts you to provide the specified user's password.</span></span>

```
PS> Invoke-Command -ComputerName Server01 -Credential CONTOSO\TestUser -ScriptBlock {Get-Package}
```

<span data-ttu-id="9b091-118">`Invoke-Command` använder parametern **computername** för att ange en fjärrdator, **Server01**.</span><span class="sxs-lookup"><span data-stu-id="9b091-118">`Invoke-Command` uses the **ComputerName** parameter to specify a remote computer, **Server01**.</span></span> <span data-ttu-id="9b091-119">Parametern **Credential** anger en domän och ett användar namn med behörigheter att köra kommandon på datorn.</span><span class="sxs-lookup"><span data-stu-id="9b091-119">The **Credential** parameter specifies a domain and user name with permissions to run commands on the computer.</span></span> <span data-ttu-id="9b091-120">Parametern **script block** kör `Get-Package` cmdleten på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="9b091-120">The **ScriptBlock** parameter runs the `Get-Package` cmdlet on the remote computer.</span></span>

### <span data-ttu-id="9b091-121">Exempel 3: Hämta paket för en angiven Provider</span><span class="sxs-lookup"><span data-stu-id="9b091-121">Example 3: Get packages for a specified provider</span></span>

<span data-ttu-id="9b091-122">Detta kommando hämtar program varu paket som är installerade på den lokala datorn från en speciell Provider.</span><span class="sxs-lookup"><span data-stu-id="9b091-122">This command gets software packages installed on the local computer from a specific provider.</span></span>

```powershell
Get-Package -ProviderName PowerShellGet -AllVersions
```

```Output
Name                  Version      Source                                     ProviderName
----                  -------      ------                                     ------------
PackageManagement     1.2.2        https://www.powershellgallery.com/api/v2   PowerShellGet
PackageManagement     1.3.1        https://www.powershellgallery.com/api/v2   PowerShellGet
posh-git              0.7.3        https://www.powershellgallery.com/api/v2   PowerShellGet
PowerShellGet         2.0.1        https://www.powershellgallery.com/api/v2   PowerShellGet
```

<span data-ttu-id="9b091-123">`Get-Package` använder parametern **ProviderName** för att ange en speciell Provider, **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="9b091-123">`Get-Package` uses the **ProviderName** parameter to specify a specific provider, **PowerShellGet**.</span></span>
<span data-ttu-id="9b091-124">Parametern **alla-versioner** visar varje version som är installerad.</span><span class="sxs-lookup"><span data-stu-id="9b091-124">The **All-Versions** parameter displays each version that is installed.</span></span>

### <span data-ttu-id="9b091-125">Exempel 4: Hämta en exakt version av ett visst paket</span><span class="sxs-lookup"><span data-stu-id="9b091-125">Example 4: Get an exact version of a specific package</span></span>

<span data-ttu-id="9b091-126">Det här kommandot hämtar en angiven version av ett installerat paket.</span><span class="sxs-lookup"><span data-stu-id="9b091-126">This command gets a specific version of an installed package.</span></span> <span data-ttu-id="9b091-127">Mer än en version av ett paket kan installeras.</span><span class="sxs-lookup"><span data-stu-id="9b091-127">More than one version of a package can be installed.</span></span>

```powershell
Get-Package -Name PackageManagement -ProviderName PowerShellGet -RequiredVersion 1.3.1
```

```Output
Name                  Version      Source                                     ProviderName
----                  -------      ------                                     ------------
PackageManagement     1.3.1        https://www.powershellgallery.com/api/v2   PowerShellGet
```

<span data-ttu-id="9b091-128">`Get-Package` använder parametern **Name** för att ange paket namnet, **PackageManagement**.</span><span class="sxs-lookup"><span data-stu-id="9b091-128">`Get-Package` uses **Name** parameter to specify the package name, **PackageManagement**.</span></span> <span data-ttu-id="9b091-129">Parametern **ProviderName** anger providern, **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="9b091-129">The **ProviderName** parameter specifies the provider, **PowerShellGet**.</span></span> <span data-ttu-id="9b091-130">Den **obligatoriska version-** parametern anger en installerad version.</span><span class="sxs-lookup"><span data-stu-id="9b091-130">The **Required-Version** parameter specifies an installed version.</span></span>

### <span data-ttu-id="9b091-131">Exempel 5: Avinstallera ett paket</span><span class="sxs-lookup"><span data-stu-id="9b091-131">Example 5: Uninstall a package</span></span>

<span data-ttu-id="9b091-132">Det här exemplet hämtar paket information och avinstallerar sedan paketet.</span><span class="sxs-lookup"><span data-stu-id="9b091-132">This example gets package information and then uninstalls the package.</span></span>

```powershell
Get-Package -Name posh-git -RequiredVersion 0.7.3 | Uninstall-Package
```

<span data-ttu-id="9b091-133">`Get-Package` använder **Name** -parametern för att ange paket namnet, **posh-git**.</span><span class="sxs-lookup"><span data-stu-id="9b091-133">`Get-Package` uses the **Name** parameter to specify the package name, **posh-git**.</span></span> <span data-ttu-id="9b091-134">Parametern **RequiredVersion** är en angiven version av paketet.</span><span class="sxs-lookup"><span data-stu-id="9b091-134">The **RequiredVersion** parameter is a specific version of the package.</span></span> <span data-ttu-id="9b091-135">Objektet skickas ned pipelinen till `Uninstall-Package` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="9b091-135">The object is sent down the pipeline to the `Uninstall-Package` cmdlet.</span></span> <span data-ttu-id="9b091-136">`Uninstall-Package` tar bort paketet.</span><span class="sxs-lookup"><span data-stu-id="9b091-136">`Uninstall-Package` removes the package.</span></span>

## <span data-ttu-id="9b091-137">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="9b091-137">PARAMETERS</span></span>

### <span data-ttu-id="9b091-138">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="9b091-138">-AllowClobber</span></span>

<span data-ttu-id="9b091-139">Åsidosätter varnings meddelanden om konflikter med befintliga kommandon.</span><span class="sxs-lookup"><span data-stu-id="9b091-139">Overrides warning messages about conflicts with existing commands.</span></span> <span data-ttu-id="9b091-140">Skriver över befintliga kommandon som har samma namn som kommandon som installeras av en modul.</span><span class="sxs-lookup"><span data-stu-id="9b091-140">Overwrites existing commands that have the same name as commands being installed by a module.</span></span>

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

### <span data-ttu-id="9b091-141">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="9b091-141">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="9b091-142">Innehåller paket som marker ATS som en för hands version i resultaten.</span><span class="sxs-lookup"><span data-stu-id="9b091-142">Includes packages marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="9b091-143">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="9b091-143">-AllVersions</span></span>

<span data-ttu-id="9b091-144">Anger att `Get-Package` returnerar alla tillgängliga versioner av paketet.</span><span class="sxs-lookup"><span data-stu-id="9b091-144">Indicates that `Get-Package` returns all available versions of the package.</span></span> <span data-ttu-id="9b091-145">Som standard `Get-Package` returnerar endast den senaste tillgängliga versionen.</span><span class="sxs-lookup"><span data-stu-id="9b091-145">By default, `Get-Package` only returns the newest available version.</span></span>

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

### <span data-ttu-id="9b091-146">-Mål</span><span class="sxs-lookup"><span data-stu-id="9b091-146">-Destination</span></span>

<span data-ttu-id="9b091-147">Anger sökvägen till en katalog som innehåller extraherade paketfiler.</span><span class="sxs-lookup"><span data-stu-id="9b091-147">Specifies the path to a directory that contains extracted package files.</span></span>

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

### <span data-ttu-id="9b091-148">-ExcludeVersion</span><span class="sxs-lookup"><span data-stu-id="9b091-148">-ExcludeVersion</span></span>

<span data-ttu-id="9b091-149">Byt för att utesluta versions numret i mappsökvägen.</span><span class="sxs-lookup"><span data-stu-id="9b091-149">Switch to exclude the version number in the folder path.</span></span>

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

### <span data-ttu-id="9b091-150">-Force</span><span class="sxs-lookup"><span data-stu-id="9b091-150">-Force</span></span>

<span data-ttu-id="9b091-151">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="9b091-151">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="9b091-152">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="9b091-152">-ForceBootstrap</span></span>

<span data-ttu-id="9b091-153">Anger att `Get-Package` paket leverantören ska installeras automatiskt av **PackageManagement** .</span><span class="sxs-lookup"><span data-stu-id="9b091-153">Indicates that `Get-Package` forces **PackageManagement** to automatically install the package provider.</span></span>

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

### <span data-ttu-id="9b091-154">-InstallUpdate</span><span class="sxs-lookup"><span data-stu-id="9b091-154">-InstallUpdate</span></span>

<span data-ttu-id="9b091-155">Anger att den här cmdleten installerar uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="9b091-155">Indicates that this cmdlet installs updates.</span></span>

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

### <span data-ttu-id="9b091-156">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="9b091-156">-MaximumVersion</span></span>

<span data-ttu-id="9b091-157">Anger den maximala paket version som du vill söka efter.</span><span class="sxs-lookup"><span data-stu-id="9b091-157">Specifies the maximum package version that you want to find.</span></span>

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

### <span data-ttu-id="9b091-158">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="9b091-158">-MinimumVersion</span></span>

<span data-ttu-id="9b091-159">Anger den minsta paket version som du vill söka efter.</span><span class="sxs-lookup"><span data-stu-id="9b091-159">Specifies the minimum package version that you want to find.</span></span> <span data-ttu-id="9b091-160">Om det finns en senare version returneras den versionen.</span><span class="sxs-lookup"><span data-stu-id="9b091-160">If a higher version is available, that version is returned.</span></span>

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

### <span data-ttu-id="9b091-161">-Name</span><span class="sxs-lookup"><span data-stu-id="9b091-161">-Name</span></span>

<span data-ttu-id="9b091-162">Anger ett eller flera paket namn, eller paket namn med jokertecken.</span><span class="sxs-lookup"><span data-stu-id="9b091-162">Specifies one or more package names, or package names with wildcard characters.</span></span> <span data-ttu-id="9b091-163">Separera flera paket namn med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="9b091-163">Separate multiple package names with commas.</span></span>

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

### <span data-ttu-id="9b091-164">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="9b091-164">-NoPathUpdate</span></span>

<span data-ttu-id="9b091-165">**NoPathUpdate** gäller endast för `Install-Script` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9b091-165">**NoPathUpdate** only applies to the `Install-Script` cmdlet.</span></span> <span data-ttu-id="9b091-166">**NoPathUpdate** är en dynamisk parameter som lagts till av providern och som inte stöds av `Get-Package` .</span><span class="sxs-lookup"><span data-stu-id="9b091-166">**NoPathUpdate** is a dynamic parameter added by the provider and isn't supported by `Get-Package`.</span></span>

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

### <span data-ttu-id="9b091-167">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="9b091-167">-PackageManagementProvider</span></span>

<span data-ttu-id="9b091-168">Anger namnet på en paket hanterings leverantör.</span><span class="sxs-lookup"><span data-stu-id="9b091-168">Specifies the name of a package management provider.</span></span>

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

### <span data-ttu-id="9b091-169">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="9b091-169">-ProviderName</span></span>

<span data-ttu-id="9b091-170">Anger ett eller flera paket leverantörs namn.</span><span class="sxs-lookup"><span data-stu-id="9b091-170">Specifies one or more package provider names.</span></span> <span data-ttu-id="9b091-171">Separera namn på flera paket leverantörer med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="9b091-171">Separate multiple package provider names with commas.</span></span>
<span data-ttu-id="9b091-172">Använd `Get-PackageProvider` för att hämta en lista över tillgängliga paket leverantörer.</span><span class="sxs-lookup"><span data-stu-id="9b091-172">Use `Get-PackageProvider` to get a list of available package providers.</span></span>

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

### <span data-ttu-id="9b091-173">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="9b091-173">-RequiredVersion</span></span>

<span data-ttu-id="9b091-174">Anger den exakta versionen av paketet som ska hittas.</span><span class="sxs-lookup"><span data-stu-id="9b091-174">Specifies the exact version of the package to find.</span></span>

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

### <span data-ttu-id="9b091-175">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="9b091-175">-Scope</span></span>

<span data-ttu-id="9b091-176">Anger Sök omfånget för paketet.</span><span class="sxs-lookup"><span data-stu-id="9b091-176">Specifies the search scope for the package.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: CurrentUser, AllUsers

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="9b091-177">-SkipDependencies</span><span class="sxs-lookup"><span data-stu-id="9b091-177">-SkipDependencies</span></span>

<span data-ttu-id="9b091-178">Växel som anger att sökning efter eventuella paket beroenden ska hoppas över.</span><span class="sxs-lookup"><span data-stu-id="9b091-178">Switch that specifies to skip finding any package dependencies.</span></span>

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

### <span data-ttu-id="9b091-179">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="9b091-179">-SkipPublisherCheck</span></span>

<span data-ttu-id="9b091-180">Gör att du kan hämta en paket version som är nyare än den installerade versionen.</span><span class="sxs-lookup"><span data-stu-id="9b091-180">Allows you to get a package version that is newer than your installed version.</span></span> <span data-ttu-id="9b091-181">Till exempel ett installerat paket som har signerats digitalt av en betrodd utgivare, men en ny version inte har signerats digitalt.</span><span class="sxs-lookup"><span data-stu-id="9b091-181">For example, an installed package that is digitally signed by a trusted publisher but a new version isn't digitally signed.</span></span>

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

### <span data-ttu-id="9b091-182">-Typ</span><span class="sxs-lookup"><span data-stu-id="9b091-182">-Type</span></span>

<span data-ttu-id="9b091-183">Anger om du vill söka efter paket med en modul, ett skript eller något av alternativen.</span><span class="sxs-lookup"><span data-stu-id="9b091-183">Specifies whether to search for packages with a module, a script, or either.</span></span>

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

### <span data-ttu-id="9b091-184">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9b091-184">CommonParameters</span></span>

<span data-ttu-id="9b091-185">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9b091-185">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9b091-186">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9b091-186">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9b091-187">INDATA</span><span class="sxs-lookup"><span data-stu-id="9b091-187">INPUTS</span></span>

## <span data-ttu-id="9b091-188">UTDATA</span><span class="sxs-lookup"><span data-stu-id="9b091-188">OUTPUTS</span></span>

### <span data-ttu-id="9b091-189">SoftwareIdentity []</span><span class="sxs-lookup"><span data-stu-id="9b091-189">SoftwareIdentity[]</span></span>

## <span data-ttu-id="9b091-190">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="9b091-190">NOTES</span></span>

<span data-ttu-id="9b091-191">Att inkludera en paket leverantör i ett kommando kan göra dynamiska parametrar tillgängliga för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9b091-191">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="9b091-192">Dynamiska parametrar är speciella för en paket leverantör.</span><span class="sxs-lookup"><span data-stu-id="9b091-192">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="9b091-193">`Get-Help`Cmdleten listar en cmdlets parameter uppsättningar och inkluderar providerns parameter uppsättning.</span><span class="sxs-lookup"><span data-stu-id="9b091-193">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span> <span data-ttu-id="9b091-194">Till exempel `Get-Package` har **PowerShellGet** parameter uppsättning som innehåller `-NoPathUpdate` , `AllowClobber` , och `SkipPublisherCheck` .</span><span class="sxs-lookup"><span data-stu-id="9b091-194">For example, `Get-Package` has the **PowerShellGet** parameter set that includes `-NoPathUpdate`, `AllowClobber`, and `SkipPublisherCheck`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9b091-195">Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1.</span><span class="sxs-lookup"><span data-stu-id="9b091-195">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="9b091-196">Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="9b091-196">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="9b091-197">Använd följande kommando för att se till att du använder TLS 1,2:</span><span class="sxs-lookup"><span data-stu-id="9b091-197">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="9b091-198">Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="9b091-198">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="9b091-199">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="9b091-199">RELATED LINKS</span></span>

[<span data-ttu-id="9b091-200">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="9b091-200">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="9b091-201">Retur-PSSession</span><span class="sxs-lookup"><span data-stu-id="9b091-201">Enter-PSSession</span></span>](../Microsoft.PowerShell.Core/Enter-PSSession.md)

[<span data-ttu-id="9b091-202">Sök-paket</span><span class="sxs-lookup"><span data-stu-id="9b091-202">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="9b091-203">Get – hjälp</span><span class="sxs-lookup"><span data-stu-id="9b091-203">Get-Help</span></span>](../Microsoft.PowerShell.Core/Get-Help.md)

[<span data-ttu-id="9b091-204">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="9b091-204">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="9b091-205">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="9b091-205">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="9b091-206">Installationspaket</span><span class="sxs-lookup"><span data-stu-id="9b091-206">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="9b091-207">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="9b091-207">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="9b091-208">Spara paket</span><span class="sxs-lookup"><span data-stu-id="9b091-208">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="9b091-209">Avinstallera paket</span><span class="sxs-lookup"><span data-stu-id="9b091-209">Uninstall-Package</span></span>](Uninstall-Package.md)
