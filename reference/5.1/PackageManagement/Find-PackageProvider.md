---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/packagemanagement/find-packageprovider?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-PackageProvider
ms.openlocfilehash: f8ef02a4afb9491375e3a1c37a9b5846eef7e057
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892907"
---
# <span data-ttu-id="b0b5c-103">Find-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="b0b5c-103">Find-PackageProvider</span></span>

## <span data-ttu-id="b0b5c-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="b0b5c-104">SYNOPSIS</span></span>
<span data-ttu-id="b0b5c-105">Returnerar en lista med paket hanterings paket leverantörer som är tillgängliga för installation.</span><span class="sxs-lookup"><span data-stu-id="b0b5c-105">Returns a list of Package Management package providers available for installation.</span></span>

## <span data-ttu-id="b0b5c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b0b5c-106">SYNTAX</span></span>

```
Find-PackageProvider [[-Name] <String[]>] [-AllVersions] [-Source <String[]>] [-IncludeDependencies]
 [-Credential <PSCredential>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-RequiredVersion <String>]
 [-MinimumVersion <String>] [-MaximumVersion <String>] [-Force] [-ForceBootstrap] [<CommonParameters>]
```

## <span data-ttu-id="b0b5c-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b0b5c-107">DESCRIPTION</span></span>

<span data-ttu-id="b0b5c-108">Cmdleten **find-PackageProvider** hittar matchande PackageManagement-providers som är tillgängliga i paket källor som registrerats med PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="b0b5c-108">The **Find-PackageProvider** cmdlet finds matching PackageManagement providers that are available in package sources registered with PowerShellGet.</span></span>
<span data-ttu-id="b0b5c-109">Detta är paket leverantörer som är tillgängliga för installation med cmdleten Install-PackageProvider.</span><span class="sxs-lookup"><span data-stu-id="b0b5c-109">These are package providers available for installation with the Install-PackageProvider cmdlet.</span></span>
<span data-ttu-id="b0b5c-110">Som standard inkluderar detta moduler som är tillgängliga i PowerShell-galleriet med taggarna **PackageManagement** och **Provider** .</span><span class="sxs-lookup"><span data-stu-id="b0b5c-110">By default, this includes modules available in the PowerShell Gallery with the **PackageManagement** and **Provider** tags.</span></span>

<span data-ttu-id="b0b5c-111">**Find-PackageProvider** hittar också matchande paket hanterings leverantörer som är tillgängliga i paket hantering Azure Blob Store.</span><span class="sxs-lookup"><span data-stu-id="b0b5c-111">**Find-PackageProvider** also finds matching Package Management providers that are available in the Package Management Azure Blob store.</span></span>
<span data-ttu-id="b0b5c-112">Använd start program-providern för att hitta och installera dem.</span><span class="sxs-lookup"><span data-stu-id="b0b5c-112">Use the bootstrapper provider to find and install them.</span></span>

## <span data-ttu-id="b0b5c-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="b0b5c-113">EXAMPLES</span></span>

### <span data-ttu-id="b0b5c-114">Exempel 1: Sök efter alla tillgängliga paket leverantörer</span><span class="sxs-lookup"><span data-stu-id="b0b5c-114">Example 1: Find all available package providers</span></span>

```
PS C:\> Find-PackageProvider
```

<span data-ttu-id="b0b5c-115">Det här kommandot hämtar en lista över alla paket leverantörer som är tillgängliga i de databaser som stöds av paket hantering.</span><span class="sxs-lookup"><span data-stu-id="b0b5c-115">This command gets a list of all package providers that are available on the repositories supported by Package Management.</span></span>
<span data-ttu-id="b0b5c-116">Som standard är dessa paket leverantörer tillgängliga på PowerShell-galleriet och med hjälp av Start programmet för paket hantering.</span><span class="sxs-lookup"><span data-stu-id="b0b5c-116">By default, those package providers are available on the PowerShell Gallery and by using the Package Management bootstrapping application.</span></span>

### <span data-ttu-id="b0b5c-117">Exempel 2: hitta alla versioner av en provider</span><span class="sxs-lookup"><span data-stu-id="b0b5c-117">Example 2: Find all versions of a provider</span></span>

```
PS C:\> Find-PackageProvider -Name "Nuget" -AllVersions
```

<span data-ttu-id="b0b5c-118">Det här kommandot hittar alla versioner av paket leverantören som heter NuGet.</span><span class="sxs-lookup"><span data-stu-id="b0b5c-118">This command finds all versions of the package provider named Nuget.</span></span>

### <span data-ttu-id="b0b5c-119">Exempel 3: hitta en provider från en angiven källa</span><span class="sxs-lookup"><span data-stu-id="b0b5c-119">Example 3: Find a provider from a specified source</span></span>

```
PS C:\> Find-PackageProvider -Name "Gistprovider" -Source "PSGallery"
```

<span data-ttu-id="b0b5c-120">Det här kommandot hittar en paket leverantör som är tillgänglig med hjälp av en angiven paket källa.</span><span class="sxs-lookup"><span data-stu-id="b0b5c-120">This command finds a package provider available by using a specified package source.</span></span>

## <span data-ttu-id="b0b5c-121">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="b0b5c-121">PARAMETERS</span></span>

### <span data-ttu-id="b0b5c-122">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="b0b5c-122">-AllVersions</span></span>

<span data-ttu-id="b0b5c-123">Anger att denna cmdlet returnerar alla tillgängliga versioner av paket leverantören.</span><span class="sxs-lookup"><span data-stu-id="b0b5c-123">Indicates that this cmdlet returns all available versions of the package provider.</span></span>
<span data-ttu-id="b0b5c-124">Som standard returnerar **find-PackageProvider** endast den senaste tillgängliga versionen.</span><span class="sxs-lookup"><span data-stu-id="b0b5c-124">By default, **Find-PackageProvider** only returns the newest available version.</span></span>

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

### <span data-ttu-id="b0b5c-125">-Credential</span><span class="sxs-lookup"><span data-stu-id="b0b5c-125">-Credential</span></span>

<span data-ttu-id="b0b5c-126">Anger ett användar konto som har behörighet att söka efter paket leverantörer.</span><span class="sxs-lookup"><span data-stu-id="b0b5c-126">Specifies a user account that has permission to search for package providers.</span></span>

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

### <span data-ttu-id="b0b5c-127">-Force</span><span class="sxs-lookup"><span data-stu-id="b0b5c-127">-Force</span></span>

<span data-ttu-id="b0b5c-128">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="b0b5c-128">Forces the command to run without asking for user confirmation.</span></span>
<span data-ttu-id="b0b5c-129">Detta motsvarar för närvarande parametern *ForceBootstrap* .</span><span class="sxs-lookup"><span data-stu-id="b0b5c-129">Currently, this is equivalent to the *ForceBootstrap* parameter.</span></span>

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

### <span data-ttu-id="b0b5c-130">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="b0b5c-130">-ForceBootstrap</span></span>

<span data-ttu-id="b0b5c-131">Anger att den här cmdleten tvingar paket hantering att automatiskt installera paket leverantören.</span><span class="sxs-lookup"><span data-stu-id="b0b5c-131">Indicates that this cmdlet forces Package Management to automatically install the package provider.</span></span>

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

### <span data-ttu-id="b0b5c-132">-IncludeDependencies</span><span class="sxs-lookup"><span data-stu-id="b0b5c-132">-IncludeDependencies</span></span>

<span data-ttu-id="b0b5c-133">Anger att denna cmdlet innehåller beroenden.</span><span class="sxs-lookup"><span data-stu-id="b0b5c-133">Indicates that this cmdlet includes dependencies.</span></span>

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

### <span data-ttu-id="b0b5c-134">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="b0b5c-134">-MaximumVersion</span></span>

<span data-ttu-id="b0b5c-135">Anger den högsta tillåtna versionen av paket leverantören som du vill hitta.</span><span class="sxs-lookup"><span data-stu-id="b0b5c-135">Specifies the maximum allowed version of the package provider that you want to find.</span></span>
<span data-ttu-id="b0b5c-136">Om du inte lägger till den här parametern söker **find-PackageProvider** efter den högsta tillgängliga versionen av providern.</span><span class="sxs-lookup"><span data-stu-id="b0b5c-136">If you do not add this parameter, **Find-PackageProvider** finds the highest available version of the provider.</span></span>

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

### <span data-ttu-id="b0b5c-137">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="b0b5c-137">-MinimumVersion</span></span>

<span data-ttu-id="b0b5c-138">Anger den lägsta tillåtna versionen av paket leverantören som du vill hitta.</span><span class="sxs-lookup"><span data-stu-id="b0b5c-138">Specifies the minimum allowed version of the package provider that you want to find.</span></span>
<span data-ttu-id="b0b5c-139">Om du inte lägger till den här parametern hittar **find-PackageProvider** den högsta tillgängliga versionen av paketet som också uppfyller den högsta version som anges av parametern *MaximumVersion* .</span><span class="sxs-lookup"><span data-stu-id="b0b5c-139">If you do not add this parameter, **Find-PackageProvider** finds the highest available version of the package that also satisfies any maximum specified version specified by the *MaximumVersion* parameter.</span></span>

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

### <span data-ttu-id="b0b5c-140">-Name</span><span class="sxs-lookup"><span data-stu-id="b0b5c-140">-Name</span></span>

<span data-ttu-id="b0b5c-141">Anger ett eller flera namn på en paket leverantör, eller namn på providrar med jokertecken.</span><span class="sxs-lookup"><span data-stu-id="b0b5c-141">Specifies one or more package provider module names, or provider names with wildcard characters.</span></span>
<span data-ttu-id="b0b5c-142">Separera flera paket namn med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="b0b5c-142">Separate multiple package names with commas.</span></span>

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

### <span data-ttu-id="b0b5c-143">-Proxy</span><span class="sxs-lookup"><span data-stu-id="b0b5c-143">-Proxy</span></span>

<span data-ttu-id="b0b5c-144">Anger en proxyserver för begäran, i stället för att ansluta direkt till Internet resursen.</span><span class="sxs-lookup"><span data-stu-id="b0b5c-144">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="b0b5c-145">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="b0b5c-145">-ProxyCredential</span></span>

<span data-ttu-id="b0b5c-146">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="b0b5c-146">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="b0b5c-147">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="b0b5c-147">-RequiredVersion</span></span>

<span data-ttu-id="b0b5c-148">Anger den exakta versionen av paket leverantören som du vill hitta.</span><span class="sxs-lookup"><span data-stu-id="b0b5c-148">Specifies the exact allowed version of the package provider that you want to find.</span></span>
<span data-ttu-id="b0b5c-149">Om du inte lägger till den här parametern söker **find-PackageProvider** efter den högsta tillgängliga versionen av providern som också uppfyller den högsta version som anges av parametern *MaximumVersion* .</span><span class="sxs-lookup"><span data-stu-id="b0b5c-149">If you do not add this parameter, **Find-PackageProvider** finds the highest available version of the provider that also satisfies any maximum version specified by the *MaximumVersion* parameter.</span></span>

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

### <span data-ttu-id="b0b5c-150">-Source</span><span class="sxs-lookup"><span data-stu-id="b0b5c-150">-Source</span></span>

<span data-ttu-id="b0b5c-151">Anger en eller flera paket källor.</span><span class="sxs-lookup"><span data-stu-id="b0b5c-151">Specifies one or more package sources.</span></span>
<span data-ttu-id="b0b5c-152">Du kan hämta en lista över tillgängliga paket källor med hjälp av Get-PackageSource-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b0b5c-152">You can get a list of available package sources by using the Get-PackageSource cmdlet.</span></span>

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

### <span data-ttu-id="b0b5c-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b0b5c-153">CommonParameters</span></span>

<span data-ttu-id="b0b5c-154">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b0b5c-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b0b5c-155">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b0b5c-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b0b5c-156">INDATA</span><span class="sxs-lookup"><span data-stu-id="b0b5c-156">INPUTS</span></span>

## <span data-ttu-id="b0b5c-157">UTDATA</span><span class="sxs-lookup"><span data-stu-id="b0b5c-157">OUTPUTS</span></span>

### <span data-ttu-id="b0b5c-158">Microsoft. PackageManagement. packning. SoftwareIdentity</span><span class="sxs-lookup"><span data-stu-id="b0b5c-158">Microsoft.PackageManagement.Packaging.SoftwareIdentity</span></span>

<span data-ttu-id="b0b5c-159">Denna cmdlet returnerar ett **SoftwareIdentity** -objekt.</span><span class="sxs-lookup"><span data-stu-id="b0b5c-159">This cmdlet returns a **SoftwareIdentity** object.</span></span>
<span data-ttu-id="b0b5c-160">Ett **SoftwareIdentity** -objekt kan skickas till **install-PackageProvider** för att installera resultaten av **find-PackageProvider**.</span><span class="sxs-lookup"><span data-stu-id="b0b5c-160">A **SoftwareIdentity** object can be piped into **Install-PackageProvider** to install the results of **Find-PackageProvider**.</span></span>

## <span data-ttu-id="b0b5c-161">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="b0b5c-161">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b0b5c-162">Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1.</span><span class="sxs-lookup"><span data-stu-id="b0b5c-162">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="b0b5c-163">Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="b0b5c-163">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="b0b5c-164">Använd följande kommando för att se till att du använder TLS 1,2:</span><span class="sxs-lookup"><span data-stu-id="b0b5c-164">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="b0b5c-165">Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="b0b5c-165">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="b0b5c-166">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="b0b5c-166">RELATED LINKS</span></span>

[<span data-ttu-id="b0b5c-167">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="b0b5c-167">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="b0b5c-168">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="b0b5c-168">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)

[<span data-ttu-id="b0b5c-169">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="b0b5c-169">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="b0b5c-170">Registrera – PackageSource</span><span class="sxs-lookup"><span data-stu-id="b0b5c-170">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="b0b5c-171">Installera-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="b0b5c-171">Install-PackageProvider</span></span>](Install-PackageProvider.md)
