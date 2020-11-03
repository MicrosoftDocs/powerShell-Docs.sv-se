---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/install-packageprovider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Install-PackageProvider
ms.openlocfilehash: 4e6940b655622444f0ac6c8f01cd7e77f854b109
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264543"
---
# <span data-ttu-id="7ac2f-103">Install-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="7ac2f-103">Install-PackageProvider</span></span>

## <span data-ttu-id="7ac2f-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="7ac2f-104">SYNOPSIS</span></span>
<span data-ttu-id="7ac2f-105">Installerar en eller flera leverantörer av paket hanterings paket.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-105">Installs one or more Package Management package providers.</span></span>

## <span data-ttu-id="7ac2f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7ac2f-106">SYNTAX</span></span>

### <span data-ttu-id="7ac2f-107">PackageBySearch (standard)</span><span class="sxs-lookup"><span data-stu-id="7ac2f-107">PackageBySearch (Default)</span></span>

```
Install-PackageProvider [-Name] <String[]> [-RequiredVersion <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-Credential <PSCredential>] [-Scope <String>] [-Source <String[]>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="7ac2f-108">PackageByInputObject</span><span class="sxs-lookup"><span data-stu-id="7ac2f-108">PackageByInputObject</span></span>

```
Install-PackageProvider [-Scope <String>] [-InputObject] <SoftwareIdentity[]> [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [-AllVersions] [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="7ac2f-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="7ac2f-109">DESCRIPTION</span></span>
<span data-ttu-id="7ac2f-110">Cmdleten **install-PackageProvider** installerar matchande paket hanterings leverantörer som är tillgängliga i paket källor som registrerats med **PowerShellGet**.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-110">The **Install-PackageProvider** cmdlet installs matching Package Management providers that are available in package sources registered with **PowerShellGet**.</span></span>
<span data-ttu-id="7ac2f-111">Som standard inkluderar detta moduler som är tillgängliga i Windows-PowerShell-galleriet med taggen **PackageManagement** .</span><span class="sxs-lookup"><span data-stu-id="7ac2f-111">By default, this includes modules available in the Windows PowerShell Gallery with the **PackageManagement** tag.</span></span>
<span data-ttu-id="7ac2f-112">**PowerShellGet** paket hanterings leverantör används för att hitta leverantörer i dessa databaser.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-112">The **PowerShellGet** Package Management provider is used for finding providers in these repositories.</span></span>

<span data-ttu-id="7ac2f-113">Denna cmdlet installerar även matchande paket hanterings leverantörer som är tillgängliga med Start programmet för paket hantering.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-113">This cmdlet also installs matching Package Management providers that are available using the Package Management bootstrapping application.</span></span>

<span data-ttu-id="7ac2f-114">Den här cmdleten installerar även matchande paket hanterings leverantörer som är tillgängliga i paket hantering Azure Blob Store.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-114">This cmdlet also installs matching Package Management providers that are available in the Package Management Azure Blob store.</span></span>
<span data-ttu-id="7ac2f-115">Använd start program-providern för att hitta och installera dem.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-115">Use the bootstrapper provider to find and install them.</span></span>

<span data-ttu-id="7ac2f-116">För att kunna köra första gången kräver PackageManagement en Internet anslutning för att ladda ned NuGet-paket leverantören.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-116">In order to execute the first time, PackageManagement requires an internet connection to download the Nuget package provider.</span></span>
<span data-ttu-id="7ac2f-117">Men om datorn inte har någon Internet anslutning och du behöver använda NuGet-eller PowerShellGet-providern kan du hämta dem på en annan dator och kopiera dem till mål datorn.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-117">However, if your computer does not have an internet connection and you need to use the Nuget or PowerShellGet provider, you can download them on another computer and copy them to your target computer.</span></span>
<span data-ttu-id="7ac2f-118">Använd följande steg för att göra detta:</span><span class="sxs-lookup"><span data-stu-id="7ac2f-118">Use the following steps to do this:</span></span>

1.
<span data-ttu-id="7ac2f-119">Kör `Install-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201 -Force` för att installera providern från en dator med en Internet anslutning.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-119">Run `Install-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201 -Force` to install the provider from a computer with an internet connection.</span></span>

2.
<span data-ttu-id="7ac2f-120">Efter installationen kan du hitta providern som är installerad i `$env:ProgramFiles\PackageManagement\ReferenceAssemblies\\\<ProviderName\>\\\<ProviderVersion\>` eller `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\\\<ProviderName\>\\\<ProviderVersion\>` .</span><span class="sxs-lookup"><span data-stu-id="7ac2f-120">After the install, you can find the provider installed in `$env:ProgramFiles\PackageManagement\ReferenceAssemblies\\\<ProviderName\>\\\<ProviderVersion\>` or `$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies\\\<ProviderName\>\\\<ProviderVersion\>`.</span></span>

3.
<span data-ttu-id="7ac2f-121">Placera \<ProviderName\> mappen, som i det här fallet är mappen NuGet, på motsvarande plats på mål datorn.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-121">Place the \<ProviderName\> folder, which in this case is the Nuget folder, in the corresponding location on your target computer.</span></span>
<span data-ttu-id="7ac2f-122">Om mål datorn är Nano Server måste du köra **install-PackageProvider** från Nano Server för att ladda ned rätt NuGet-binärfiler.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-122">If your target computer is a Nano server, you need to run **Install-PackageProvider** from Nano Server to download the correct Nuget binaries.</span></span>

4.
<span data-ttu-id="7ac2f-123">Starta om PowerShell för att automatiskt läsa in paket leverantören.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-123">Restart PowerShell to auto-load the package provider.</span></span>
<span data-ttu-id="7ac2f-124">Du kan också köra `Get-PackageProvider -ListAvailable` för att visa en lista över alla paket leverantörer som är tillgängliga på datorn.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-124">Alternatively, run `Get-PackageProvider -ListAvailable` to list all the package providers available on the computer.</span></span>
<span data-ttu-id="7ac2f-125">Använd sedan `Import-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201` för att importera providern till den aktuella Windows PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-125">Then use `Import-PackageProvider -Name NuGet -RequiredVersion 2.8.5.201` to import the provider to the current Windows PowerShell session.</span></span>

## <span data-ttu-id="7ac2f-126">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="7ac2f-126">EXAMPLES</span></span>

### <span data-ttu-id="7ac2f-127">Exempel 1: installera en Package provider från PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="7ac2f-127">Example 1: Install a package provider from the PowerShell Gallery</span></span>

```
PS C:\> Install-PackageProvider -Name "Gistprovider" -Verbose
```

<span data-ttu-id="7ac2f-128">Det här kommandot installerar Gistprovider från PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-128">This command installs the Gistprovider from the PowerShell Gallery.</span></span>

### <span data-ttu-id="7ac2f-129">Exempel 2: installera en angiven version av en paket leverantör</span><span class="sxs-lookup"><span data-stu-id="7ac2f-129">Example 2: Install a specified version of a package provider</span></span>

```
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
PS C:\> Install-PackageProvider -Name "Nuget" -RequiredVersion "2.8.5.216" -Force
```

<span data-ttu-id="7ac2f-130">I det här exemplet installeras en angiven version av NuGet-paket leverantören.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-130">This example installs a specified version of the Nuget package provider.</span></span>

<span data-ttu-id="7ac2f-131">Det första kommandot hittar alla versioner av paket leverantören som heter NuGet.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-131">The first command finds all versions of the package provider named Nuget.</span></span>
<span data-ttu-id="7ac2f-132">Det andra kommandot installerar en angiven version av NuGet-paket leverantören.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-132">The second command installs a specified version of the Nuget package provider.</span></span>

### <span data-ttu-id="7ac2f-133">Exempel 3: hitta en provider och installera den</span><span class="sxs-lookup"><span data-stu-id="7ac2f-133">Example 3: Find a provider and install it</span></span>

```
PS C:\> Find-PackageProvider -Name "Gistprovider" | Install-PackageProvider -Verbose
```

<span data-ttu-id="7ac2f-134">Det här kommandot använder **find-PackageProvider** och pipelinen för att söka efter registrerings enheten och installera den.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-134">This command uses **Find-PackageProvider** and the pipeline to search for the Gist provider and install it.</span></span>

### <span data-ttu-id="7ac2f-135">Exempel 4: installera en provider till den aktuella användarens modul-mapp</span><span class="sxs-lookup"><span data-stu-id="7ac2f-135">Example 4: Install a provider to the current user's module folder</span></span>

```
PS C:\> Install-PackageProvider -Name Gistprovider -Verbose -Scope CurrentUser
```

<span data-ttu-id="7ac2f-136">Det här kommandot installerar en paket leverantör som $env: LOCALAPPDATA\PackageManagement\ProviderAssemblies så att endast den aktuella användaren kan använda den.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-136">This command installs a package provider to $env:LOCALAPPDATA\PackageManagement\ProviderAssemblies so that only the current user can use it.</span></span>

## <span data-ttu-id="7ac2f-137">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="7ac2f-137">PARAMETERS</span></span>

### <span data-ttu-id="7ac2f-138">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="7ac2f-138">-AllVersions</span></span>
<span data-ttu-id="7ac2f-139">Anger att denna cmdlet installerar alla tillgängliga versioner av paket leverantören.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-139">Indicates that this cmdlet installs all available versions of the package provider.</span></span>
<span data-ttu-id="7ac2f-140">Som standard returnerar **install-PackageProvider** endast den senaste tillgängliga versionen.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-140">By default, **Install-PackageProvider** only returns the highest available version.</span></span>

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

### <span data-ttu-id="7ac2f-141">-Credential</span><span class="sxs-lookup"><span data-stu-id="7ac2f-141">-Credential</span></span>
<span data-ttu-id="7ac2f-142">Anger ett användar konto som har behörighet att installera paket leverantörer.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-142">Specifies a user account that has permission to install package providers.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: PackageBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7ac2f-143">-Force</span><span class="sxs-lookup"><span data-stu-id="7ac2f-143">-Force</span></span>
<span data-ttu-id="7ac2f-144">Anger att denna cmdlet tvingar alla åtgärder med denna cmdlet som kan tvingas.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-144">Indicates that this cmdlet forces all actions with this cmdlet that can be forced.</span></span>
<span data-ttu-id="7ac2f-145">För närvarande innebär detta att *Force* -parametern fungerar på samma sätt som parametern *ForceBootstrap* .</span><span class="sxs-lookup"><span data-stu-id="7ac2f-145">Currently, this means the *Force* parameter acts the same as the *ForceBootstrap* parameter.</span></span>

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

### <span data-ttu-id="7ac2f-146">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="7ac2f-146">-ForceBootstrap</span></span>
<span data-ttu-id="7ac2f-147">Anger att paket leverantören installeras automatiskt av den här cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-147">Indicates that this cmdlet automatically installs the package provider.</span></span>

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

### <span data-ttu-id="7ac2f-148">– InputObject</span><span class="sxs-lookup"><span data-stu-id="7ac2f-148">-InputObject</span></span>
<span data-ttu-id="7ac2f-149">Anger ett **SoftwareIdentity** -objekt.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-149">Specifies a **SoftwareIdentity** object.</span></span>
<span data-ttu-id="7ac2f-150">Använd **find-PackageProvider** -cmdlet: en för att hämta ett **SoftwareIdentity** -objekt till pipe i **install-PackageProvider**.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-150">Use the **Find-PackageProvider** cmdlet to obtain a **SoftwareIdentity** object to pipe into **Install-PackageProvider**.</span></span>

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

### <span data-ttu-id="7ac2f-151">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="7ac2f-151">-MaximumVersion</span></span>
<span data-ttu-id="7ac2f-152">Anger den högsta tillåtna versionen av paket leverantören som du vill installera.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-152">Specifies the maximum allowed version of the package provider that you want to install.</span></span>
<span data-ttu-id="7ac2f-153">Om du inte lägger till den här parametern installerar **install-PackageProvider** den högsta tillgängliga versionen av providern.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-153">If you do not add this parameter, **Install-PackageProvider** installs the highest available version of the provider.</span></span>

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

### <span data-ttu-id="7ac2f-154">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="7ac2f-154">-MinimumVersion</span></span>
<span data-ttu-id="7ac2f-155">Anger den lägsta tillåtna versionen av paket leverantören som du vill installera.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-155">Specifies the minimum allowed version of the package provider that you want to install.</span></span>
<span data-ttu-id="7ac2f-156">Om du inte lägger till den här parametern installerar **install-PackageProvider** den högsta tillgängliga versionen av paketet som också uppfyller eventuella krav som anges av parametern *MaximumVersion* .</span><span class="sxs-lookup"><span data-stu-id="7ac2f-156">If you do not add this parameter, **Install-PackageProvider** installs the highest available version of the package that also satisfies any requirement specified by the *MaximumVersion* parameter.</span></span>

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

### <span data-ttu-id="7ac2f-157">-Name</span><span class="sxs-lookup"><span data-stu-id="7ac2f-157">-Name</span></span>
<span data-ttu-id="7ac2f-158">Anger ett eller flera namn på moduler för paket leverantör.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-158">Specifies one or more package provider module names.</span></span>
<span data-ttu-id="7ac2f-159">Separera flera paket namn med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-159">Separate multiple package names with commas.</span></span>
<span data-ttu-id="7ac2f-160">Jokertecken stöds inte.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-160">Wildcard characters are not supported.</span></span>

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

### <span data-ttu-id="7ac2f-161">-Proxy</span><span class="sxs-lookup"><span data-stu-id="7ac2f-161">-Proxy</span></span>
<span data-ttu-id="7ac2f-162">Anger en proxyserver för begäran, i stället för att ansluta direkt till Internet resursen.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-162">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="7ac2f-163">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="7ac2f-163">-ProxyCredential</span></span>
<span data-ttu-id="7ac2f-164">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="7ac2f-164">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="7ac2f-165">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="7ac2f-165">-RequiredVersion</span></span>
<span data-ttu-id="7ac2f-166">Anger den exakta versionen av paket leverantören som du vill installera.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-166">Specifies the exact allowed version of the package provider that you want to install.</span></span>
<span data-ttu-id="7ac2f-167">Om du inte lägger till den här parametern installerar **install-PackageProvider** den högsta tillgängliga versionen av providern som också uppfyller den högsta version som anges av parametern *MaximumVersion* .</span><span class="sxs-lookup"><span data-stu-id="7ac2f-167">If you do not add this parameter, **Install-PackageProvider** installs the highest available version of the provider that also satisfies any maximum version specified by the *MaximumVersion* parameter.</span></span>

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

### <span data-ttu-id="7ac2f-168">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="7ac2f-168">-Scope</span></span>
<span data-ttu-id="7ac2f-169">Anger providerns installations omfång.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-169">Specifies the installation scope of the provider.</span></span>
<span data-ttu-id="7ac2f-170">De acceptabla värdena för den här parametern är: **allusers** och **CurrentUser**.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-170">The acceptable values for this parameter are: **AllUsers** and **CurrentUser**.</span></span>

<span data-ttu-id="7ac2f-171">**Allusers** -scopet installerar providrar på en plats som är tillgänglig för alla användare av datorn.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-171">The **AllUsers** scope installs providers in a location that is accessible to all users of the computer.</span></span>
<span data-ttu-id="7ac2f-172">Som standard är detta **$env:P rogramfiles\packagemanagement\providerassemblies.**</span><span class="sxs-lookup"><span data-stu-id="7ac2f-172">By default, this is **$env:ProgramFiles\PackageManagement\ProviderAssemblies.**</span></span>

<span data-ttu-id="7ac2f-173">**CurrentUser** -scopet installerar providrar på en plats där de endast är tillgängliga för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-173">The **CurrentUser** scope installs providers in a location where they are only accessible to the current user.</span></span>
<span data-ttu-id="7ac2f-174">Som standard är detta **$env: LOCALAPPDATA\PackageManagement\ProviderAssemblies.**</span><span class="sxs-lookup"><span data-stu-id="7ac2f-174">By default, this is **$env:LOCALAPPDATA\PackageManagement\ProviderAssemblies.**</span></span>

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

### <span data-ttu-id="7ac2f-175">-Source</span><span class="sxs-lookup"><span data-stu-id="7ac2f-175">-Source</span></span>
<span data-ttu-id="7ac2f-176">Anger en eller flera paket källor.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-176">Specifies one or more package sources.</span></span>
<span data-ttu-id="7ac2f-177">Använd Get-PackageSource-cmdlet för att hämta en lista över tillgängliga paket källor.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-177">Use the Get-PackageSource cmdlet to get a list of available package sources.</span></span>

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

### <span data-ttu-id="7ac2f-178">-Confirm</span><span class="sxs-lookup"><span data-stu-id="7ac2f-178">-Confirm</span></span>
<span data-ttu-id="7ac2f-179">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-179">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="7ac2f-180">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="7ac2f-180">-WhatIf</span></span>
<span data-ttu-id="7ac2f-181">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-181">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="7ac2f-182">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-182">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="7ac2f-183">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7ac2f-183">CommonParameters</span></span>
<span data-ttu-id="7ac2f-184">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-184">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7ac2f-185">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="7ac2f-185">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7ac2f-186">INDATA</span><span class="sxs-lookup"><span data-stu-id="7ac2f-186">INPUTS</span></span>

### <span data-ttu-id="7ac2f-187">Microsoft. PackageManagement. packning. SoftwareIdentity</span><span class="sxs-lookup"><span data-stu-id="7ac2f-187">Microsoft.PackageManagement.Packaging.SoftwareIdentity</span></span>
<span data-ttu-id="7ac2f-188">Du kan skicka ett **SoftwareIdentity** -objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-188">You can pipe a **SoftwareIdentity** object to this cmdlet.</span></span>
<span data-ttu-id="7ac2f-189">Använd Find-PackageProvider för att hämta ett **SoftwareIdentity** -objekt som kan skickass till **install-PackageProvider**.</span><span class="sxs-lookup"><span data-stu-id="7ac2f-189">Use Find-PackageProvider to get a **SoftwareIdentity** object that can be piped into **Install-PackageProvider**.</span></span>

## <span data-ttu-id="7ac2f-190">UTDATA</span><span class="sxs-lookup"><span data-stu-id="7ac2f-190">OUTPUTS</span></span>

## <span data-ttu-id="7ac2f-191">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="7ac2f-191">NOTES</span></span>

## <span data-ttu-id="7ac2f-192">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="7ac2f-192">RELATED LINKS</span></span>

[<span data-ttu-id="7ac2f-193">Find-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="7ac2f-193">Find-PackageProvider</span></span>](Find-PackageProvider.md)

[<span data-ttu-id="7ac2f-194">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="7ac2f-194">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="7ac2f-195">Importera – PackageProvider</span><span class="sxs-lookup"><span data-stu-id="7ac2f-195">Import-PackageProvider</span></span>](Import-PackageProvider.md)