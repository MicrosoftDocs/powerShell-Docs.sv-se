---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/find-packageprovider?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-PackageProvider
ms.openlocfilehash: 664e6064580f9212c25632a1146d1ac67f2308bf
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264279"
---
# <span data-ttu-id="4b505-103">Find-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="4b505-103">Find-PackageProvider</span></span>

## <span data-ttu-id="4b505-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="4b505-104">SYNOPSIS</span></span>
<span data-ttu-id="4b505-105">Returnerar en lista med paket hanterings paket leverantörer som är tillgängliga för installation.</span><span class="sxs-lookup"><span data-stu-id="4b505-105">Returns a list of Package Management package providers available for installation.</span></span>

## <span data-ttu-id="4b505-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4b505-106">SYNTAX</span></span>

```
Find-PackageProvider [[-Name] <String[]>] [-AllVersions] [-Source <String[]>] [-IncludeDependencies]
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-RequiredVersion <String>]
 [-MinimumVersion <String>] [-MaximumVersion <String>] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## <span data-ttu-id="4b505-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="4b505-107">DESCRIPTION</span></span>

<span data-ttu-id="4b505-108">Cmdleten **find-PackageProvider** hittar matchande PackageManagement-providers som är tillgängliga i paket källor som registrerats med PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="4b505-108">The **Find-PackageProvider** cmdlet finds matching PackageManagement providers that are available in package sources registered with PowerShellGet.</span></span>
<span data-ttu-id="4b505-109">Detta är paket leverantörer som är tillgängliga för installation med cmdleten Install-PackageProvider.</span><span class="sxs-lookup"><span data-stu-id="4b505-109">These are package providers available for installation with the Install-PackageProvider cmdlet.</span></span>
<span data-ttu-id="4b505-110">Som standard inkluderar detta moduler som är tillgängliga i PowerShell-galleriet med taggarna **PackageManagement** och **Provider** .</span><span class="sxs-lookup"><span data-stu-id="4b505-110">By default, this includes modules available in the PowerShell Gallery with the **PackageManagement** and **Provider** tags.</span></span>

<span data-ttu-id="4b505-111">**Find-PackageProvider** hittar också matchande paket hanterings leverantörer som är tillgängliga i paket hantering Azure Blob Store.</span><span class="sxs-lookup"><span data-stu-id="4b505-111">**Find-PackageProvider** also finds matching Package Management providers that are available in the Package Management Azure Blob store.</span></span>
<span data-ttu-id="4b505-112">Använd start program-providern för att hitta och installera dem.</span><span class="sxs-lookup"><span data-stu-id="4b505-112">Use the bootstrapper provider to find and install them.</span></span>

## <span data-ttu-id="4b505-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="4b505-113">EXAMPLES</span></span>

### <span data-ttu-id="4b505-114">Exempel 1: Sök efter alla tillgängliga paket leverantörer</span><span class="sxs-lookup"><span data-stu-id="4b505-114">Example 1: Find all available package providers</span></span>

```
PS C:\> Find-PackageProvider
```

<span data-ttu-id="4b505-115">Det här kommandot hämtar en lista över alla paket leverantörer som är tillgängliga i de databaser som stöds av paket hantering.</span><span class="sxs-lookup"><span data-stu-id="4b505-115">This command gets a list of all package providers that are available on the repositories supported by Package Management.</span></span>
<span data-ttu-id="4b505-116">Som standard är dessa paket leverantörer tillgängliga på PowerShell-galleriet och med hjälp av Start programmet för paket hantering.</span><span class="sxs-lookup"><span data-stu-id="4b505-116">By default, those package providers are available on the PowerShell Gallery and by using the Package Management bootstrapping application.</span></span>

### <span data-ttu-id="4b505-117">Exempel 2: hitta alla versioner av en provider</span><span class="sxs-lookup"><span data-stu-id="4b505-117">Example 2: Find all versions of a provider</span></span>

```
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
```

<span data-ttu-id="4b505-118">Det här kommandot hittar alla versioner av paket leverantören som heter NuGet.</span><span class="sxs-lookup"><span data-stu-id="4b505-118">This command finds all versions of the package provider named Nuget.</span></span>

### <span data-ttu-id="4b505-119">Exempel 3: hitta en provider från en angiven källa</span><span class="sxs-lookup"><span data-stu-id="4b505-119">Example 3: Find a provider from a specified source</span></span>

```
PS C:\> Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"
```

<span data-ttu-id="4b505-120">Det här kommandot hittar en paket leverantör som är tillgänglig med hjälp av en angiven paket källa.</span><span class="sxs-lookup"><span data-stu-id="4b505-120">This command finds a package provider available by using a specified package source.</span></span>

## <span data-ttu-id="4b505-121">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="4b505-121">PARAMETERS</span></span>

### <span data-ttu-id="4b505-122">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="4b505-122">-AllVersions</span></span>

<span data-ttu-id="4b505-123">Anger att denna cmdlet returnerar alla tillgängliga versioner av paket leverantören.</span><span class="sxs-lookup"><span data-stu-id="4b505-123">Indicates that this cmdlet returns all available versions of the package provider.</span></span>
<span data-ttu-id="4b505-124">Som standard returnerar **find-PackageProvider** endast den senaste tillgängliga versionen.</span><span class="sxs-lookup"><span data-stu-id="4b505-124">By default, **Find-PackageProvider** only returns the newest available version.</span></span>

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

### <span data-ttu-id="4b505-125">-Credential</span><span class="sxs-lookup"><span data-stu-id="4b505-125">-Credential</span></span>

<span data-ttu-id="4b505-126">Anger ett användar konto som har behörighet att söka efter paket leverantörer.</span><span class="sxs-lookup"><span data-stu-id="4b505-126">Specifies a user account that has permission to search for package providers.</span></span>

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

### <span data-ttu-id="4b505-127">-Force</span><span class="sxs-lookup"><span data-stu-id="4b505-127">-Force</span></span>

<span data-ttu-id="4b505-128">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="4b505-128">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="4b505-129">Detta motsvarar för närvarande parametern *ForceBootstrap* .</span><span class="sxs-lookup"><span data-stu-id="4b505-129">Currently, this is equivalent to the *ForceBootstrap* parameter.</span></span>

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

### <span data-ttu-id="4b505-130">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="4b505-130">-ForceBootstrap</span></span>

<span data-ttu-id="4b505-131">Anger att den här cmdleten tvingar paket hantering att automatiskt installera paket leverantören.</span><span class="sxs-lookup"><span data-stu-id="4b505-131">Indicates that this cmdlet forces Package Management to automatically install the package provider.</span></span>

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

### <span data-ttu-id="4b505-132">-IncludeDependencies</span><span class="sxs-lookup"><span data-stu-id="4b505-132">-IncludeDependencies</span></span>

<span data-ttu-id="4b505-133">Anger att denna cmdlet innehåller beroenden.</span><span class="sxs-lookup"><span data-stu-id="4b505-133">Indicates that this cmdlet includes dependencies.</span></span>

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

### <span data-ttu-id="4b505-134">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="4b505-134">-MaximumVersion</span></span>

<span data-ttu-id="4b505-135">Anger den högsta tillåtna versionen av paket leverantören som du vill hitta.</span><span class="sxs-lookup"><span data-stu-id="4b505-135">Specifies the maximum allowed version of the package provider that you want to find.</span></span>
<span data-ttu-id="4b505-136">Om du inte lägger till den här parametern söker **find-PackageProvider** efter den högsta tillgängliga versionen av providern.</span><span class="sxs-lookup"><span data-stu-id="4b505-136">If you do not add this parameter, **Find-PackageProvider** finds the highest available version of the provider.</span></span>

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

### <span data-ttu-id="4b505-137">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="4b505-137">-MinimumVersion</span></span>

<span data-ttu-id="4b505-138">Anger den lägsta tillåtna versionen av paket leverantören som du vill hitta.</span><span class="sxs-lookup"><span data-stu-id="4b505-138">Specifies the minimum allowed version of the package provider that you want to find.</span></span>
<span data-ttu-id="4b505-139">Om du inte lägger till den här parametern hittar **find-PackageProvider** den högsta tillgängliga versionen av paketet som också uppfyller den högsta version som anges av parametern *MaximumVersion* .</span><span class="sxs-lookup"><span data-stu-id="4b505-139">If you do not add this parameter, **Find-PackageProvider** finds the highest available version of the package that also satisfies any maximum specified version specified by the *MaximumVersion* parameter.</span></span>

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

### <span data-ttu-id="4b505-140">-Name</span><span class="sxs-lookup"><span data-stu-id="4b505-140">-Name</span></span>

<span data-ttu-id="4b505-141">Anger ett eller flera namn på en paket leverantör, eller namn på providrar med jokertecken.</span><span class="sxs-lookup"><span data-stu-id="4b505-141">Specifies one or more package provider module names, or provider names with wildcard characters.</span></span>
<span data-ttu-id="4b505-142">Separera flera paket namn med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="4b505-142">Separate multiple package names with commas.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="4b505-143">-Proxy</span><span class="sxs-lookup"><span data-stu-id="4b505-143">-Proxy</span></span>

<span data-ttu-id="4b505-144">Anger en proxyserver för begäran, i stället för att ansluta direkt till Internet resursen.</span><span class="sxs-lookup"><span data-stu-id="4b505-144">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="4b505-145">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="4b505-145">-ProxyCredential</span></span>

<span data-ttu-id="4b505-146">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="4b505-146">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="4b505-147">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="4b505-147">-RequiredVersion</span></span>

<span data-ttu-id="4b505-148">Anger den exakta versionen av paket leverantören som du vill hitta.</span><span class="sxs-lookup"><span data-stu-id="4b505-148">Specifies the exact allowed version of the package provider that you want to find.</span></span>
<span data-ttu-id="4b505-149">Om du inte lägger till den här parametern söker **find-PackageProvider** efter den högsta tillgängliga versionen av providern som också uppfyller den högsta version som anges av parametern *MaximumVersion* .</span><span class="sxs-lookup"><span data-stu-id="4b505-149">If you do not add this parameter, **Find-PackageProvider** finds the highest available version of the provider that also satisfies any maximum version specified by the *MaximumVersion* parameter.</span></span>

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

### <span data-ttu-id="4b505-150">-Source</span><span class="sxs-lookup"><span data-stu-id="4b505-150">-Source</span></span>

<span data-ttu-id="4b505-151">Anger en eller flera paket källor.</span><span class="sxs-lookup"><span data-stu-id="4b505-151">Specifies one or more package sources.</span></span>
<span data-ttu-id="4b505-152">Du kan hämta en lista över tillgängliga paket källor med hjälp av Get-PackageSource-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4b505-152">You can get a list of available package sources by using the Get-PackageSource cmdlet.</span></span>

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

### <span data-ttu-id="4b505-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4b505-153">CommonParameters</span></span>

<span data-ttu-id="4b505-154">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4b505-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4b505-155">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4b505-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4b505-156">INDATA</span><span class="sxs-lookup"><span data-stu-id="4b505-156">INPUTS</span></span>

## <span data-ttu-id="4b505-157">UTDATA</span><span class="sxs-lookup"><span data-stu-id="4b505-157">OUTPUTS</span></span>

### <span data-ttu-id="4b505-158">Microsoft. PackageManagement. packning. SoftwareIdentity</span><span class="sxs-lookup"><span data-stu-id="4b505-158">Microsoft.PackageManagement.Packaging.SoftwareIdentity</span></span>

<span data-ttu-id="4b505-159">Denna cmdlet returnerar ett **SoftwareIdentity** -objekt.</span><span class="sxs-lookup"><span data-stu-id="4b505-159">This cmdlet returns a **SoftwareIdentity** object.</span></span>
<span data-ttu-id="4b505-160">Ett **SoftwareIdentity** -objekt kan skickas till **install-PackageProvider** för att installera resultaten av **find-PackageProvider**.</span><span class="sxs-lookup"><span data-stu-id="4b505-160">A **SoftwareIdentity** object can be piped into **Install-PackageProvider** to install the results of **Find-PackageProvider**.</span></span>

## <span data-ttu-id="4b505-161">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="4b505-161">NOTES</span></span>

## <span data-ttu-id="4b505-162">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="4b505-162">RELATED LINKS</span></span>

[<span data-ttu-id="4b505-163">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="4b505-163">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="4b505-164">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="4b505-164">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)

[<span data-ttu-id="4b505-165">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="4b505-165">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="4b505-166">Registrera – PackageSource</span><span class="sxs-lookup"><span data-stu-id="4b505-166">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="4b505-167">Installera-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="4b505-167">Install-PackageProvider</span></span>](Install-PackageProvider.md)
