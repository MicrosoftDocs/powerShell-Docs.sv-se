---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 05/22/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-package?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Package
ms.openlocfilehash: c26365eb5b4833c4982fa54e742521cf72307e99
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889498"
---
# <span data-ttu-id="6d954-102">Get-Package</span><span class="sxs-lookup"><span data-stu-id="6d954-102">Get-Package</span></span>

## <span data-ttu-id="6d954-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="6d954-103">SYNOPSIS</span></span>
<span data-ttu-id="6d954-104">Returnerar en lista med alla program varu paket som har installerats med **PackageManagement**.</span><span class="sxs-lookup"><span data-stu-id="6d954-104">Returns a list of all software packages that were installed with **PackageManagement**.</span></span>

## <span data-ttu-id="6d954-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6d954-105">SYNTAX</span></span>

### <span data-ttu-id="6d954-106">NuGet</span><span class="sxs-lookup"><span data-stu-id="6d954-106">NuGet</span></span>

```
Get-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-ProviderName <String[]>]
 [-Destination <String>] [-ExcludeVersion] [-Scope <String>] [-SkipDependencies]
 [<CommonParameters>]
```

### <span data-ttu-id="6d954-107">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="6d954-107">PowerShellGet</span></span>

```
Get-Package [[-Name] <String[]>] [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-AllVersions] [-Force] [-ForceBootstrap] [-ProviderName <String[]>]
 [-Scope <String>] [-PackageManagementProvider <String>] [-Type <String>] [-AllowClobber]
 [-SkipPublisherCheck] [-InstallUpdate] [-NoPathUpdate] [-AllowPrereleaseVersions]
 [<CommonParameters>]
```

## <span data-ttu-id="6d954-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="6d954-108">DESCRIPTION</span></span>

<span data-ttu-id="6d954-109">`Get-Package`Cmdleten returnerar en lista över alla program varu paket på den lokala datorn som installerades med **PackageManagement**.</span><span class="sxs-lookup"><span data-stu-id="6d954-109">The `Get-Package` cmdlet returns a list of all software packages on the local computer that were installed with **PackageManagement**.</span></span> <span data-ttu-id="6d954-110">Du kan köra `Get-Package` på fjärrdatorer genom att köra den som en del av ett `Invoke-Command` `Enter-PSSession` kommando eller skript.</span><span class="sxs-lookup"><span data-stu-id="6d954-110">You can run `Get-Package` on remote computers by running it as part of an `Invoke-Command` or `Enter-PSSession` command or script.</span></span>

## <span data-ttu-id="6d954-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="6d954-111">EXAMPLES</span></span>

### <span data-ttu-id="6d954-112">Exempel 1: Hämta alla installerade paket</span><span class="sxs-lookup"><span data-stu-id="6d954-112">Example 1: Get all installed packages</span></span>

<span data-ttu-id="6d954-113">`Get-Package`Cmdlet: en hämtar alla paket som är installerade på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="6d954-113">The `Get-Package` cmdlet gets all packages that are installed on the local computer.</span></span>

```powershell
Get-Package
```

```Output
Name           Version      Source                                     ProviderName
----           -------      ------                                     ------------
posh-git       0.7.3        https://www.powershellgallery.com/api/v2   PowerShellGet
```

### <span data-ttu-id="6d954-114">Exempel 2: Hämta paket som är installerade på en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="6d954-114">Example 2: Get packages that are installed on a remote computer</span></span>

<span data-ttu-id="6d954-115">Det här kommandot hämtar en lista över paket som har installerats av **PackageManagement** på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="6d954-115">This command gets a list of packages that were installed by **PackageManagement** on a remote computer.</span></span> <span data-ttu-id="6d954-116">Med det här kommandot kan du ange användarens lösen ord.</span><span class="sxs-lookup"><span data-stu-id="6d954-116">This command prompts you to provide the specified user's password.</span></span>

```
PS> Invoke-Command -ComputerName Server01 -Credential CONTOSO\TestUser -ScriptBlock {Get-Package}
```

<span data-ttu-id="6d954-117">`Invoke-Command` använder parametern **computername** för att ange en fjärrdator, **Server01**.</span><span class="sxs-lookup"><span data-stu-id="6d954-117">`Invoke-Command` uses the **ComputerName** parameter to specify a remote computer, **Server01**.</span></span> <span data-ttu-id="6d954-118">Parametern **Credential** anger en domän och ett användar namn med behörigheter att köra kommandon på datorn.</span><span class="sxs-lookup"><span data-stu-id="6d954-118">The **Credential** parameter specifies a domain and user name with permissions to run commands on the computer.</span></span> <span data-ttu-id="6d954-119">Parametern **script block** kör `Get-Package` cmdleten på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="6d954-119">The **ScriptBlock** parameter runs the `Get-Package` cmdlet on the remote computer.</span></span>

### <span data-ttu-id="6d954-120">Exempel 3: Hämta paket för en angiven Provider</span><span class="sxs-lookup"><span data-stu-id="6d954-120">Example 3: Get packages for a specified provider</span></span>

<span data-ttu-id="6d954-121">Detta kommando hämtar program varu paket som är installerade på den lokala datorn från en speciell Provider.</span><span class="sxs-lookup"><span data-stu-id="6d954-121">This command gets software packages installed on the local computer from a specific provider.</span></span>

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

<span data-ttu-id="6d954-122">`Get-Package` använder parametern **ProviderName** för att ange en speciell Provider, **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="6d954-122">`Get-Package` uses the **ProviderName** parameter to specify a specific provider, **PowerShellGet**.</span></span>
<span data-ttu-id="6d954-123">Parametern **alla-versioner** visar varje version som är installerad.</span><span class="sxs-lookup"><span data-stu-id="6d954-123">The **All-Versions** parameter displays each version that is installed.</span></span>

### <span data-ttu-id="6d954-124">Exempel 4: Hämta en exakt version av ett visst paket</span><span class="sxs-lookup"><span data-stu-id="6d954-124">Example 4: Get an exact version of a specific package</span></span>

<span data-ttu-id="6d954-125">Det här kommandot hämtar en angiven version av ett installerat paket.</span><span class="sxs-lookup"><span data-stu-id="6d954-125">This command gets a specific version of an installed package.</span></span> <span data-ttu-id="6d954-126">Mer än en version av ett paket kan installeras.</span><span class="sxs-lookup"><span data-stu-id="6d954-126">More than one version of a package can be installed.</span></span>

```powershell
Get-Package -Name PackageManagement -ProviderName PowerShellGet -RequiredVersion 1.3.1
```

```Output
Name                  Version      Source                                     ProviderName
----                  -------      ------                                     ------------
PackageManagement     1.3.1        https://www.powershellgallery.com/api/v2   PowerShellGet
```

<span data-ttu-id="6d954-127">`Get-Package` använder parametern **Name** för att ange paket namnet, **PackageManagement**.</span><span class="sxs-lookup"><span data-stu-id="6d954-127">`Get-Package` uses **Name** parameter to specify the package name, **PackageManagement**.</span></span> <span data-ttu-id="6d954-128">Parametern **ProviderName** anger providern, **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="6d954-128">The **ProviderName** parameter specifies the provider, **PowerShellGet**.</span></span> <span data-ttu-id="6d954-129">Den **obligatoriska version-** parametern anger en installerad version.</span><span class="sxs-lookup"><span data-stu-id="6d954-129">The **Required-Version** parameter specifies an installed version.</span></span>

### <span data-ttu-id="6d954-130">Exempel 5: Avinstallera ett paket</span><span class="sxs-lookup"><span data-stu-id="6d954-130">Example 5: Uninstall a package</span></span>

<span data-ttu-id="6d954-131">Det här exemplet hämtar paket information och avinstallerar sedan paketet.</span><span class="sxs-lookup"><span data-stu-id="6d954-131">This example gets package information and then uninstalls the package.</span></span>

```powershell
Get-Package -Name posh-git -RequiredVersion 0.7.3 | Uninstall-Package
```

<span data-ttu-id="6d954-132">`Get-Package` använder **Name** -parametern för att ange paket namnet, **posh-git**.</span><span class="sxs-lookup"><span data-stu-id="6d954-132">`Get-Package` uses the **Name** parameter to specify the package name, **posh-git**.</span></span> <span data-ttu-id="6d954-133">Parametern **RequiredVersion** är en angiven version av paketet.</span><span class="sxs-lookup"><span data-stu-id="6d954-133">The **RequiredVersion** parameter is a specific version of the package.</span></span> <span data-ttu-id="6d954-134">Objektet skickas ned pipelinen till `Uninstall-Package` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6d954-134">The object is sent down the pipeline to the `Uninstall-Package` cmdlet.</span></span> <span data-ttu-id="6d954-135">`Uninstall-Package` tar bort paketet.</span><span class="sxs-lookup"><span data-stu-id="6d954-135">`Uninstall-Package` removes the package.</span></span>

## <span data-ttu-id="6d954-136">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="6d954-136">PARAMETERS</span></span>

### <span data-ttu-id="6d954-137">-AllowClobber</span><span class="sxs-lookup"><span data-stu-id="6d954-137">-AllowClobber</span></span>

<span data-ttu-id="6d954-138">Åsidosätter varnings meddelanden om konflikter med befintliga kommandon.</span><span class="sxs-lookup"><span data-stu-id="6d954-138">Overrides warning messages about conflicts with existing commands.</span></span> <span data-ttu-id="6d954-139">Skriver över befintliga kommandon som har samma namn som kommandon som installeras av en modul.</span><span class="sxs-lookup"><span data-stu-id="6d954-139">Overwrites existing commands that have the same name as commands being installed by a module.</span></span>

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

### <span data-ttu-id="6d954-140">-AllowPrereleaseVersions</span><span class="sxs-lookup"><span data-stu-id="6d954-140">-AllowPrereleaseVersions</span></span>

<span data-ttu-id="6d954-141">Innehåller paket som marker ATS som en för hands version i resultaten.</span><span class="sxs-lookup"><span data-stu-id="6d954-141">Includes packages marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="6d954-142">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="6d954-142">-AllVersions</span></span>

<span data-ttu-id="6d954-143">Anger att `Get-Package` returnerar alla tillgängliga versioner av paketet.</span><span class="sxs-lookup"><span data-stu-id="6d954-143">Indicates that `Get-Package` returns all available versions of the package.</span></span> <span data-ttu-id="6d954-144">Som standard `Get-Package` returnerar endast den senaste tillgängliga versionen.</span><span class="sxs-lookup"><span data-stu-id="6d954-144">By default, `Get-Package` only returns the newest available version.</span></span>

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

### <span data-ttu-id="6d954-145">-Mål</span><span class="sxs-lookup"><span data-stu-id="6d954-145">-Destination</span></span>

<span data-ttu-id="6d954-146">Anger sökvägen till en katalog som innehåller extraherade paketfiler.</span><span class="sxs-lookup"><span data-stu-id="6d954-146">Specifies the path to a directory that contains extracted package files.</span></span>

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

### <span data-ttu-id="6d954-147">-ExcludeVersion</span><span class="sxs-lookup"><span data-stu-id="6d954-147">-ExcludeVersion</span></span>

<span data-ttu-id="6d954-148">Byt för att utesluta versions numret i mappsökvägen.</span><span class="sxs-lookup"><span data-stu-id="6d954-148">Switch to exclude the version number in the folder path.</span></span>

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

### <span data-ttu-id="6d954-149">-Force</span><span class="sxs-lookup"><span data-stu-id="6d954-149">-Force</span></span>

<span data-ttu-id="6d954-150">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="6d954-150">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="6d954-151">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="6d954-151">-ForceBootstrap</span></span>

<span data-ttu-id="6d954-152">Anger att `Get-Package` paket leverantören ska installeras automatiskt av **PackageManagement** .</span><span class="sxs-lookup"><span data-stu-id="6d954-152">Indicates that `Get-Package` forces **PackageManagement** to automatically install the package provider.</span></span>

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

### <span data-ttu-id="6d954-153">-InstallUpdate</span><span class="sxs-lookup"><span data-stu-id="6d954-153">-InstallUpdate</span></span>

<span data-ttu-id="6d954-154">Anger att den här cmdleten installerar uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="6d954-154">Indicates that this cmdlet installs updates.</span></span>

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

### <span data-ttu-id="6d954-155">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="6d954-155">-MaximumVersion</span></span>

<span data-ttu-id="6d954-156">Anger den maximala paket version som du vill söka efter.</span><span class="sxs-lookup"><span data-stu-id="6d954-156">Specifies the maximum package version that you want to find.</span></span>

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

### <span data-ttu-id="6d954-157">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="6d954-157">-MinimumVersion</span></span>

<span data-ttu-id="6d954-158">Anger den minsta paket version som du vill söka efter.</span><span class="sxs-lookup"><span data-stu-id="6d954-158">Specifies the minimum package version that you want to find.</span></span> <span data-ttu-id="6d954-159">Om det finns en senare version returneras den versionen.</span><span class="sxs-lookup"><span data-stu-id="6d954-159">If a higher version is available, that version is returned.</span></span>

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

### <span data-ttu-id="6d954-160">-Name</span><span class="sxs-lookup"><span data-stu-id="6d954-160">-Name</span></span>

<span data-ttu-id="6d954-161">Anger ett eller flera paket namn, eller paket namn med jokertecken.</span><span class="sxs-lookup"><span data-stu-id="6d954-161">Specifies one or more package names, or package names with wildcard characters.</span></span> <span data-ttu-id="6d954-162">Separera flera paket namn med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="6d954-162">Separate multiple package names with commas.</span></span>

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

### <span data-ttu-id="6d954-163">-NoPathUpdate</span><span class="sxs-lookup"><span data-stu-id="6d954-163">-NoPathUpdate</span></span>

<span data-ttu-id="6d954-164">**NoPathUpdate** gäller endast för `Install-Script` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6d954-164">**NoPathUpdate** only applies to the `Install-Script` cmdlet.</span></span> <span data-ttu-id="6d954-165">**NoPathUpdate** är en dynamisk parameter som lagts till av providern och som inte stöds av `Get-Package` .</span><span class="sxs-lookup"><span data-stu-id="6d954-165">**NoPathUpdate** is a dynamic parameter added by the provider and isn't supported by `Get-Package`.</span></span>

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

### <span data-ttu-id="6d954-166">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="6d954-166">-PackageManagementProvider</span></span>

<span data-ttu-id="6d954-167">Anger namnet på en paket hanterings leverantör.</span><span class="sxs-lookup"><span data-stu-id="6d954-167">Specifies the name of a package management provider.</span></span>

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

### <span data-ttu-id="6d954-168">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="6d954-168">-ProviderName</span></span>

<span data-ttu-id="6d954-169">Anger ett eller flera paket leverantörs namn.</span><span class="sxs-lookup"><span data-stu-id="6d954-169">Specifies one or more package provider names.</span></span> <span data-ttu-id="6d954-170">Separera namn på flera paket leverantörer med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="6d954-170">Separate multiple package provider names with commas.</span></span>
<span data-ttu-id="6d954-171">Använd `Get-PackageProvider` för att hämta en lista över tillgängliga paket leverantörer.</span><span class="sxs-lookup"><span data-stu-id="6d954-171">Use `Get-PackageProvider` to get a list of available package providers.</span></span>

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

### <span data-ttu-id="6d954-172">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="6d954-172">-RequiredVersion</span></span>

<span data-ttu-id="6d954-173">Anger den exakta versionen av paketet som ska hittas.</span><span class="sxs-lookup"><span data-stu-id="6d954-173">Specifies the exact version of the package to find.</span></span>

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

### <span data-ttu-id="6d954-174">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="6d954-174">-Scope</span></span>

<span data-ttu-id="6d954-175">Anger Sök omfånget för paketet.</span><span class="sxs-lookup"><span data-stu-id="6d954-175">Specifies the search scope for the package.</span></span>

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

### <span data-ttu-id="6d954-176">-SkipDependencies</span><span class="sxs-lookup"><span data-stu-id="6d954-176">-SkipDependencies</span></span>

<span data-ttu-id="6d954-177">Växel som anger att sökning efter eventuella paket beroenden ska hoppas över.</span><span class="sxs-lookup"><span data-stu-id="6d954-177">Switch that specifies to skip finding any package dependencies.</span></span>

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

### <span data-ttu-id="6d954-178">-SkipPublisherCheck</span><span class="sxs-lookup"><span data-stu-id="6d954-178">-SkipPublisherCheck</span></span>

<span data-ttu-id="6d954-179">Gör att du kan hämta en paket version som är nyare än den installerade versionen.</span><span class="sxs-lookup"><span data-stu-id="6d954-179">Allows you to get a package version that is newer than your installed version.</span></span> <span data-ttu-id="6d954-180">Till exempel ett installerat paket som har signerats digitalt av en betrodd utgivare, men en ny version inte har signerats digitalt.</span><span class="sxs-lookup"><span data-stu-id="6d954-180">For example, an installed package that is digitally signed by a trusted publisher but a new version isn't digitally signed.</span></span>

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

### <span data-ttu-id="6d954-181">-Typ</span><span class="sxs-lookup"><span data-stu-id="6d954-181">-Type</span></span>

<span data-ttu-id="6d954-182">Anger om du vill söka efter paket med en modul, ett skript eller något av alternativen.</span><span class="sxs-lookup"><span data-stu-id="6d954-182">Specifies whether to search for packages with a module, a script, or either.</span></span>

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

### <span data-ttu-id="6d954-183">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6d954-183">CommonParameters</span></span>

<span data-ttu-id="6d954-184">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6d954-184">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6d954-185">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="6d954-185">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6d954-186">INDATA</span><span class="sxs-lookup"><span data-stu-id="6d954-186">INPUTS</span></span>

## <span data-ttu-id="6d954-187">UTDATA</span><span class="sxs-lookup"><span data-stu-id="6d954-187">OUTPUTS</span></span>

### <span data-ttu-id="6d954-188">SoftwareIdentity []</span><span class="sxs-lookup"><span data-stu-id="6d954-188">SoftwareIdentity[]</span></span>

## <span data-ttu-id="6d954-189">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="6d954-189">NOTES</span></span>

<span data-ttu-id="6d954-190">Att inkludera en paket leverantör i ett kommando kan göra dynamiska parametrar tillgängliga för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6d954-190">Including a package provider in a command can make dynamic parameters available to a cmdlet.</span></span> <span data-ttu-id="6d954-191">Dynamiska parametrar är speciella för en paket leverantör.</span><span class="sxs-lookup"><span data-stu-id="6d954-191">Dynamic parameters are specific to a package provider.</span></span> <span data-ttu-id="6d954-192">`Get-Help`Cmdleten listar en cmdlets parameter uppsättningar och inkluderar providerns parameter uppsättning.</span><span class="sxs-lookup"><span data-stu-id="6d954-192">The `Get-Help` cmdlet lists a cmdlet's parameter sets and includes the provider's parameter set.</span></span> <span data-ttu-id="6d954-193">Till exempel `Get-Package` har **PowerShellGet** parameter uppsättning som innehåller `-NoPathUpdate` , `AllowClobber` , och `SkipPublisherCheck` .</span><span class="sxs-lookup"><span data-stu-id="6d954-193">For example, `Get-Package` has the **PowerShellGet** parameter set that includes `-NoPathUpdate`, `AllowClobber`, and `SkipPublisherCheck`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6d954-194">Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1.</span><span class="sxs-lookup"><span data-stu-id="6d954-194">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="6d954-195">Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="6d954-195">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="6d954-196">Använd följande kommando för att se till att du använder TLS 1,2:</span><span class="sxs-lookup"><span data-stu-id="6d954-196">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="6d954-197">Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="6d954-197">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="6d954-198">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="6d954-198">RELATED LINKS</span></span>

[<span data-ttu-id="6d954-199">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="6d954-199">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="6d954-200">Retur-PSSession</span><span class="sxs-lookup"><span data-stu-id="6d954-200">Enter-PSSession</span></span>](../Microsoft.PowerShell.Core/Enter-PSSession.md)

[<span data-ttu-id="6d954-201">Sök-paket</span><span class="sxs-lookup"><span data-stu-id="6d954-201">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="6d954-202">Get – hjälp</span><span class="sxs-lookup"><span data-stu-id="6d954-202">Get-Help</span></span>](../Microsoft.PowerShell.Core/Get-Help.md)

[<span data-ttu-id="6d954-203">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="6d954-203">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="6d954-204">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="6d954-204">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="6d954-205">Installationspaket</span><span class="sxs-lookup"><span data-stu-id="6d954-205">Install-Package</span></span>](Install-Package.md)

[<span data-ttu-id="6d954-206">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="6d954-206">Invoke-Command</span></span>](../Microsoft.PowerShell.Core/Invoke-Command.md)

[<span data-ttu-id="6d954-207">Spara paket</span><span class="sxs-lookup"><span data-stu-id="6d954-207">Save-Package</span></span>](Save-Package.md)

[<span data-ttu-id="6d954-208">Avinstallera paket</span><span class="sxs-lookup"><span data-stu-id="6d954-208">Uninstall-Package</span></span>](Uninstall-Package.md)