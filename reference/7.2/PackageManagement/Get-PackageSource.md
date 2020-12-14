---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
Locale: en-US
Module Name: PackageManagement
ms.date: 03/29/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/get-packagesource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PackageSource
ms.openlocfilehash: 8b91c5b950e0e16c4ce0821ee2f96b830dab1fc2
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889484"
---
# <span data-ttu-id="d503f-102">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="d503f-102">Get-PackageSource</span></span>

## <span data-ttu-id="d503f-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="d503f-103">SYNOPSIS</span></span>
<span data-ttu-id="d503f-104">Hämtar en lista med paket källor som har registrerats för en paket leverantör.</span><span class="sxs-lookup"><span data-stu-id="d503f-104">Gets a list of package sources that are registered for a package provider.</span></span>

## <span data-ttu-id="d503f-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d503f-105">SYNTAX</span></span>

### <span data-ttu-id="d503f-106">NuGet</span><span class="sxs-lookup"><span data-stu-id="d503f-106">NuGet</span></span>

```
Get-PackageSource [[-Name] <String>] [-Location <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="d503f-107">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="d503f-107">PowerShellGet</span></span>

```
Get-PackageSource [[-Name] <String>] [-Location <String>] [-Force] [-ForceBootstrap]
 [-ProviderName <String[]>] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="d503f-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="d503f-108">DESCRIPTION</span></span>

<span data-ttu-id="d503f-109">`Get-PackageSource`Cmdleten hämtar en lista över paket källor som är registrerade med **PackageManagement** på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="d503f-109">The `Get-PackageSource` cmdlet gets a list of package sources that are registered with **PackageManagement** on the local computer.</span></span> <span data-ttu-id="d503f-110">Om du anger en paket leverantör `Get-PackageSource` hämtar bara de källor som är associerade med den angivna providern.</span><span class="sxs-lookup"><span data-stu-id="d503f-110">If you specify a package provider, `Get-PackageSource` gets only those sources that are associated with the specified provider.</span></span> <span data-ttu-id="d503f-111">Annars returnerar kommandot alla paket källor som är registrerade med **PackageManagement**.</span><span class="sxs-lookup"><span data-stu-id="d503f-111">Otherwise, the command returns all package sources that are registered with **PackageManagement**.</span></span>

## <span data-ttu-id="d503f-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="d503f-112">EXAMPLES</span></span>

### <span data-ttu-id="d503f-113">Exempel 1: Hämta alla paket källor</span><span class="sxs-lookup"><span data-stu-id="d503f-113">Example 1: Get all package sources</span></span>

<span data-ttu-id="d503f-114">`Get-PackageSource`Cmdlet: en hämtar alla paket källor som är registrerade med **PackageManagement** på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="d503f-114">The `Get-PackageSource` cmdlet gets all package sources that are registered with **PackageManagement** on the local computer.</span></span>

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

### <span data-ttu-id="d503f-115">Exempel 2: Hämta alla paket källor för en speciell Provider</span><span class="sxs-lookup"><span data-stu-id="d503f-115">Example 2: Get all package sources for a specific provider</span></span>

<span data-ttu-id="d503f-116">Det här kommandot hämtar paket källor som är registrerade för en speciell Provider.</span><span class="sxs-lookup"><span data-stu-id="d503f-116">This command gets package sources that are registered for a specific provider.</span></span>

```powershell
Get-PackageSource -ProviderName NuGet
```

```Output
Name                 ProviderName     IsTrusted  Location
----                 ------------     ---------  --------
LocalPackages        NuGet            False      C:\LocalPkg\
MyNuget              NuGet            False      https://www.nuget.org/api/v2
```

<span data-ttu-id="d503f-117">`Get-PackageSource` använder parametern **ProviderName** för att hämta paket källor som har registrerats för **NuGet** -providern.</span><span class="sxs-lookup"><span data-stu-id="d503f-117">`Get-PackageSource` uses the **ProviderName** parameter to get package sources that are registered for the **NuGet** provider.</span></span>

### <span data-ttu-id="d503f-118">Exempel 3: Hämta källor från en paket leverantör</span><span class="sxs-lookup"><span data-stu-id="d503f-118">Example 3: Get sources from a package provider</span></span>

<span data-ttu-id="d503f-119">Det här kommandot använder en paket leverantör för att hämta paket källor.</span><span class="sxs-lookup"><span data-stu-id="d503f-119">This command uses a package provider to get package sources.</span></span>

```powershell
Get-PackageProvider -Name NuGet | Get-PackageSource
```

```Output
Name                 ProviderName     IsTrusted  Location
----                 ------------     ---------  --------
LocalPackages        NuGet            False      C:\LocalPkg\
MyNuget              NuGet            False      https://www.nuget.org/api/v2
```

<span data-ttu-id="d503f-120">`Get-PackageProvider` använder **Name** -parametern ange Providerns namn, **NuGet**.</span><span class="sxs-lookup"><span data-stu-id="d503f-120">`Get-PackageProvider` uses the **Name** parameter specify the provider name, **NuGet**.</span></span> <span data-ttu-id="d503f-121">Objektet skickas ned pipelinen till `Get-PackageSource` .</span><span class="sxs-lookup"><span data-stu-id="d503f-121">The object is sent down the pipeline to `Get-PackageSource`.</span></span>

## <span data-ttu-id="d503f-122">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="d503f-122">PARAMETERS</span></span>

### <span data-ttu-id="d503f-123">– ConfigFile</span><span class="sxs-lookup"><span data-stu-id="d503f-123">-ConfigFile</span></span>

<span data-ttu-id="d503f-124">Anger en konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="d503f-124">Specifies a configuration file.</span></span>

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

### <span data-ttu-id="d503f-125">-Force</span><span class="sxs-lookup"><span data-stu-id="d503f-125">-Force</span></span>

<span data-ttu-id="d503f-126">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="d503f-126">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="d503f-127">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="d503f-127">-ForceBootstrap</span></span>

<span data-ttu-id="d503f-128">Anger att den här cmdleten tvingar **PackageManagement** att automatiskt installera en paket leverantör.</span><span class="sxs-lookup"><span data-stu-id="d503f-128">Indicates that this cmdlet forces **PackageManagement** to automatically install a package provider.</span></span>

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

### <span data-ttu-id="d503f-129">– Plats</span><span class="sxs-lookup"><span data-stu-id="d503f-129">-Location</span></span>

<span data-ttu-id="d503f-130">Anger platsen för en paket hanterings källa eller lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="d503f-130">Specifies the location of a package management source or repository.</span></span>

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

### <span data-ttu-id="d503f-131">-Name</span><span class="sxs-lookup"><span data-stu-id="d503f-131">-Name</span></span>

<span data-ttu-id="d503f-132">Anger namnet på en paket hanterings källa.</span><span class="sxs-lookup"><span data-stu-id="d503f-132">Specifies the name of a package management source.</span></span>

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

### <span data-ttu-id="d503f-133">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="d503f-133">-PackageManagementProvider</span></span>

<span data-ttu-id="d503f-134">Anger en paket hanterings leverantör.</span><span class="sxs-lookup"><span data-stu-id="d503f-134">Specifies a package management provider.</span></span>

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

### <span data-ttu-id="d503f-135">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="d503f-135">-ProviderName</span></span>

<span data-ttu-id="d503f-136">Anger ett eller flera paket leverantörs namn.</span><span class="sxs-lookup"><span data-stu-id="d503f-136">Specifies one or more package provider names.</span></span> <span data-ttu-id="d503f-137">Separera namn på flera paket leverantörer med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="d503f-137">Separate multiple package provider names with commas.</span></span>
<span data-ttu-id="d503f-138">Använd `Get-PackageProvider` för att hämta en lista över tillgängliga paket leverantörer.</span><span class="sxs-lookup"><span data-stu-id="d503f-138">Use `Get-PackageProvider` to get a list of available package providers.</span></span>

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

### <span data-ttu-id="d503f-139">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="d503f-139">-PublishLocation</span></span>

<span data-ttu-id="d503f-140">Anger publicerings platsen för paket källan.</span><span class="sxs-lookup"><span data-stu-id="d503f-140">Specifies the publish location for the package source.</span></span>

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

### <span data-ttu-id="d503f-141">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="d503f-141">-ScriptPublishLocation</span></span>

<span data-ttu-id="d503f-142">Anger skriptets publicerings plats.</span><span class="sxs-lookup"><span data-stu-id="d503f-142">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="d503f-143">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="d503f-143">-ScriptSourceLocation</span></span>

<span data-ttu-id="d503f-144">Anger sökvägen till skript källan.</span><span class="sxs-lookup"><span data-stu-id="d503f-144">Specifies the script source location.</span></span>

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

### <span data-ttu-id="d503f-145">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="d503f-145">-SkipValidate</span></span>

<span data-ttu-id="d503f-146">Växel som hoppar över verifiering av autentiseringsuppgifterna för en paket källa.</span><span class="sxs-lookup"><span data-stu-id="d503f-146">Switch that skips validating the credentials of a package source.</span></span>

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

### <span data-ttu-id="d503f-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d503f-147">CommonParameters</span></span>

<span data-ttu-id="d503f-148">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d503f-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d503f-149">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d503f-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d503f-150">INDATA</span><span class="sxs-lookup"><span data-stu-id="d503f-150">INPUTS</span></span>

## <span data-ttu-id="d503f-151">UTDATA</span><span class="sxs-lookup"><span data-stu-id="d503f-151">OUTPUTS</span></span>

### <span data-ttu-id="d503f-152">PackageSource[]</span><span class="sxs-lookup"><span data-stu-id="d503f-152">PackageSource[]</span></span>

<span data-ttu-id="d503f-153">Anger en eller flera paket källor.</span><span class="sxs-lookup"><span data-stu-id="d503f-153">Specifies one or more package sources.</span></span>

## <span data-ttu-id="d503f-154">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="d503f-154">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d503f-155">Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1.</span><span class="sxs-lookup"><span data-stu-id="d503f-155">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="d503f-156">Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="d503f-156">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="d503f-157">Använd följande kommando för att se till att du använder TLS 1,2:</span><span class="sxs-lookup"><span data-stu-id="d503f-157">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="d503f-158">Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="d503f-158">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="d503f-159">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="d503f-159">RELATED LINKS</span></span>

[<span data-ttu-id="d503f-160">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="d503f-160">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="d503f-161">Sök-paket</span><span class="sxs-lookup"><span data-stu-id="d503f-161">Find-Package</span></span>](Find-Package.md)

[<span data-ttu-id="d503f-162">Get-Package</span><span class="sxs-lookup"><span data-stu-id="d503f-162">Get-Package</span></span>](Get-Package.md)

[<span data-ttu-id="d503f-163">Get-PackageProvider</span><span class="sxs-lookup"><span data-stu-id="d503f-163">Get-PackageProvider</span></span>](Get-PackageProvider.md)

[<span data-ttu-id="d503f-164">Registrera – PackageSource</span><span class="sxs-lookup"><span data-stu-id="d503f-164">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="d503f-165">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="d503f-165">Set-PackageSource</span></span>](Set-PackageSource.md)

[<span data-ttu-id="d503f-166">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="d503f-166">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
