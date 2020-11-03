---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 03/29/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-packagesource?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PackageSource
ms.openlocfilehash: 8910f7b72d29614a9e92786ace517f99ee07fe76
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265694"
---
# <span data-ttu-id="d57f7-103">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="d57f7-103">Get-PackageSource</span></span>

## <span data-ttu-id="d57f7-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="d57f7-104">SYNOPSIS</span></span>
<span data-ttu-id="d57f7-105">Hämtar en lista med paket källor som har registrerats för en paket leverantör.</span><span class="sxs-lookup"><span data-stu-id="d57f7-105">Gets a list of package sources that are registered for a package provider.</span></span>

## <span data-ttu-id="d57f7-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d57f7-106">SYNTAX</span></span>

### <span data-ttu-id="d57f7-107">NuGet</span><span class="sxs-lookup"><span data-stu-id="d57f7-107">NuGet</span></span>

```
Get-PackageSource [[-Name] <String>] [-Location <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="d57f7-108">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="d57f7-108">PowerShellGet</span></span>

```
Get-PackageSource [[-Name] <String>] [-Location <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="d57f7-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="d57f7-109">DESCRIPTION</span></span>

<span data-ttu-id="d57f7-110">`Get-PackageSource`Cmdleten hämtar en lista över paket källor som är registrerade med **PackageManagement** på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="d57f7-110">The `Get-PackageSource` cmdlet gets a list of package sources that are registered with **PackageManagement** on the local computer.</span></span> <span data-ttu-id="d57f7-111">Om du anger en paket leverantör `Get-PackageSource` hämtar bara de källor som är associerade med den angivna providern.</span><span class="sxs-lookup"><span data-stu-id="d57f7-111">If you specify a package provider, `Get-PackageSource` gets only those sources that are associated with the specified provider.</span></span> <span data-ttu-id="d57f7-112">Annars returnerar kommandot alla paket källor som är registrerade med **PackageManagement**.</span><span class="sxs-lookup"><span data-stu-id="d57f7-112">Otherwise, the command returns all package sources that are registered with **PackageManagement**.</span></span>

## <span data-ttu-id="d57f7-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="d57f7-113">EXAMPLES</span></span>

### <span data-ttu-id="d57f7-114">Exempel 1: Hämta alla paket källor</span><span class="sxs-lookup"><span data-stu-id="d57f7-114">Example 1: Get all package sources</span></span>

<span data-ttu-id="d57f7-115">`Get-PackageSource`Cmdlet: en hämtar alla paket källor som är registrerade med **PackageManagement** på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="d57f7-115">The `Get-PackageSource` cmdlet gets all package sources that are registered with **PackageManagement** on the local computer.</span></span>

```powershell
Get-PackageSource
```

```Output
Name                 ProviderName     IsTrusted  Location
----                 ------------     ---------  --------
LocalPackages        NuGet            False      C:\LocalPkg\
MyNuget              NuGet            False      https://www.nuget.org/api/v2
PSGallery            PowerShellGet    False      https://www.powershellgallery.com/api/v2
```

### <span data-ttu-id="d57f7-116">Exempel 2: Hämta alla paket källor för en speciell Provider</span><span class="sxs-lookup"><span data-stu-id="d57f7-116">Example 2: Get all package sources for a specific provider</span></span>

<span data-ttu-id="d57f7-117">Det här kommandot hämtar paket källor som är registrerade för en speciell Provider.</span><span class="sxs-lookup"><span data-stu-id="d57f7-117">This command gets package sources that are registered for a specific provider.</span></span>

```powershell
Get-PackageSource -ProviderName NuGet
```

```Output
Name                 ProviderName     IsTrusted  Location
----                 ------------     ---------  --------
LocalPackages        NuGet            False      C:\LocalPkg\
MyNuget              NuGet            False      https://www.nuget.org/api/v2
```

<span data-ttu-id="d57f7-118">`Get-PackageSource` använder parametern **ProviderName** för att hämta paket källor som har registrerats för **NuGet** -providern.</span><span class="sxs-lookup"><span data-stu-id="d57f7-118">`Get-PackageSource` uses the **ProviderName** parameter to get package sources that are registered for the **NuGet** provider.</span></span>

### <span data-ttu-id="d57f7-119">Exempel 3: Hämta källor från en paket leverantör</span><span class="sxs-lookup"><span data-stu-id="d57f7-119">Example 3: Get sources from a package provider</span></span>

<span data-ttu-id="d57f7-120">Det här kommandot använder en paket leverantör för att hämta paket källor.</span><span class="sxs-lookup"><span data-stu-id="d57f7-120">This command uses a package provider to get package sources.</span></span>

```powershell
Get-PackageProvider -Name NuGet | Get-PackageSource
```

```Output
Name                 ProviderName     IsTrusted  Location
----                 ------------     ---------  --------
LocalPackages        NuGet            False      C:\LocalPkg\
MyNuget              NuGet            False      https://www.nuget.org/api/v2
```

<span data-ttu-id="d57f7-121">`Get-PackageProvider` använder **Name** -parametern ange Providerns namn, **NuGet**.</span><span class="sxs-lookup"><span data-stu-id="d57f7-121">`Get-PackageProvider` uses the **Name** parameter specify the provider name, **NuGet**.</span></span> <span data-ttu-id="d57f7-122">Objektet skickas ned pipelinen till `Get-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="d57f7-122">The object is sent down the pipeline to `Get-PackageSource`.</span></span>

## <span data-ttu-id="d57f7-123">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="d57f7-123">PARAMETERS</span></span>

### <span data-ttu-id="d57f7-124">– ConfigFile</span><span class="sxs-lookup"><span data-stu-id="d57f7-124">-ConfigFile</span></span>

<span data-ttu-id="d57f7-125">Anger en konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="d57f7-125">Specifies a configuration file.</span></span>

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

### <span data-ttu-id="d57f7-126">-Force</span><span class="sxs-lookup"><span data-stu-id="d57f7-126">-Force</span></span>

<span data-ttu-id="d57f7-127">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="d57f7-127">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="d57f7-128">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="d57f7-128">-ForceBootstrap</span></span>

<span data-ttu-id="d57f7-129">Anger att den här cmdleten tvingar **PackageManagement** att automatiskt installera en paket leverantör.</span><span class="sxs-lookup"><span data-stu-id="d57f7-129">Indicates that this cmdlet forces **PackageManagement** to automatically install a package provider.</span></span>

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

### <span data-ttu-id="d57f7-130">– Plats</span><span class="sxs-lookup"><span data-stu-id="d57f7-130">-Location</span></span>

<span data-ttu-id="d57f7-131">Anger platsen för en paket hanterings källa eller lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="d57f7-131">Specifies the location of a package management source or repository.</span></span>

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

### <span data-ttu-id="d57f7-132">-Name</span><span class="sxs-lookup"><span data-stu-id="d57f7-132">-Name</span></span>

<span data-ttu-id="d57f7-133">Anger namnet på en paket hanterings källa.</span><span class="sxs-lookup"><span data-stu-id="d57f7-133">Specifies the name of a package management source.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d57f7-134">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="d57f7-134">-PackageManagementProvider</span></span>

<span data-ttu-id="d57f7-135">Anger en paket hanterings leverantör.</span><span class="sxs-lookup"><span data-stu-id="d57f7-135">Specifies a package management provider.</span></span>

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

### <span data-ttu-id="d57f7-136">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="d57f7-136">-ProviderName</span></span>

<span data-ttu-id="d57f7-137">Anger ett eller flera paket leverantörs namn.</span><span class="sxs-lookup"><span data-stu-id="d57f7-137">Specifies one or more package provider names.</span></span> <span data-ttu-id="d57f7-138">Separera namn på flera paket leverantörer med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="d57f7-138">Separate multiple package provider names with commas.</span></span>
<span data-ttu-id="d57f7-139">Använd `Get-PackageProvider` för att hämta en lista över tillgängliga paket leverantörer.</span><span class="sxs-lookup"><span data-stu-id="d57f7-139">Use `Get-PackageProvider` to get a list of available package providers.</span></span>

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

### <span data-ttu-id="d57f7-140">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="d57f7-140">-PublishLocation</span></span>

<span data-ttu-id="d57f7-141">Anger publicerings platsen för paket källan.</span><span class="sxs-lookup"><span data-stu-id="d57f7-141">Specifies the publish location for the package source.</span></span>

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

### <span data-ttu-id="d57f7-142">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="d57f7-142">-ScriptPublishLocation</span></span>

<span data-ttu-id="d57f7-143">Anger skriptets publicerings plats.</span><span class="sxs-lookup"><span data-stu-id="d57f7-143">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="d57f7-144">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="d57f7-144">-ScriptSourceLocation</span></span>

<span data-ttu-id="d57f7-145">Anger sökvägen till skript källan.</span><span class="sxs-lookup"><span data-stu-id="d57f7-145">Specifies the script source location.</span></span>

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

### <span data-ttu-id="d57f7-146">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="d57f7-146">-SkipValidate</span></span>

<span data-ttu-id="d57f7-147">Växel som hoppar över verifiering av autentiseringsuppgifterna för en paket källa.</span><span class="sxs-lookup"><span data-stu-id="d57f7-147">Switch that skips validating the credentials of a package source.</span></span>

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

### <span data-ttu-id="d57f7-148">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d57f7-148">CommonParameters</span></span>

<span data-ttu-id="d57f7-149">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d57f7-149">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d57f7-150">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d57f7-150">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d57f7-151">INDATA</span><span class="sxs-lookup"><span data-stu-id="d57f7-151">INPUTS</span></span>

## <span data-ttu-id="d57f7-152">UTDATA</span><span class="sxs-lookup"><span data-stu-id="d57f7-152">OUTPUTS</span></span>

### <span data-ttu-id="d57f7-153">PackageSource[]</span><span class="sxs-lookup"><span data-stu-id="d57f7-153">PackageSource[]</span></span>

<span data-ttu-id="d57f7-154">Anger en eller flera paket källor.</span><span class="sxs-lookup"><span data-stu-id="d57f7-154">Specifies one or more package sources.</span></span>

## <span data-ttu-id="d57f7-155">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="d57f7-155">NOTES</span></span>

## <span data-ttu-id="d57f7-156">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="d57f7-156">RELATED LINKS</span></span>

[<span data-ttu-id="d57f7-157">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="d57f7-157">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="d57f7-158">Sök-paket</span><span class="sxs-lookup"><span data-stu-id="d57f7-158">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="d57f7-159">Get-Package</span><span class="sxs-lookup"><span data-stu-id="d57f7-159">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="d57f7-160">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="d57f7-160">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="d57f7-161">Registrera – PackageSource</span><span class="sxs-lookup"><span data-stu-id="d57f7-161">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="d57f7-162">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="d57f7-162">Set-PackageSource</span></span>](Set-PackageSource.md)

[<span data-ttu-id="d57f7-163">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="d57f7-163">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
