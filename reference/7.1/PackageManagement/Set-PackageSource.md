---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 04/03/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/set-packagesource?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PackageSource
ms.openlocfilehash: ad5384f7d708cc708991d4150bf883139007ae1b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266390"
---
# <span data-ttu-id="a9f37-103">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="a9f37-103">Set-PackageSource</span></span>

## <span data-ttu-id="a9f37-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="a9f37-104">SYNOPSIS</span></span>
<span data-ttu-id="a9f37-105">Ersätter en paket källa för en angiven paket leverantör.</span><span class="sxs-lookup"><span data-stu-id="a9f37-105">Replaces a package source for a specified package provider.</span></span>

## <span data-ttu-id="a9f37-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a9f37-106">SYNTAX</span></span>

### <span data-ttu-id="a9f37-107">SourceBySearch (standard)</span><span class="sxs-lookup"><span data-stu-id="a9f37-107">SourceBySearch (Default)</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [[-Name] <String>] [-Location <String>] [-NewLocation <String>] [-NewName <String>] [-Trusted]
 [-Force] [-ForceBootstrap] [-WhatIf] [-Confirm] [-ProviderName <String>] [<CommonParameters>]
```

### <span data-ttu-id="a9f37-108">SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="a9f37-108">SourceByInputObject</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] -InputObject <PackageSource> [-Force]
 [-ForceBootstrap] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a9f37-109">NuGet: SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="a9f37-109">NuGet:SourceByInputObject</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="a9f37-110">NuGet: SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="a9f37-110">NuGet:SourceBySearch</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="a9f37-111">PowerShellGet: SourceByInputObject</span><span class="sxs-lookup"><span data-stu-id="a9f37-111">PowerShellGet:SourceByInputObject</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

### <span data-ttu-id="a9f37-112">PowerShellGet: SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="a9f37-112">PowerShellGet:SourceBySearch</span></span>

```
Set-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [-Credential <PSCredential>]
 [-NewLocation <String>] [-NewName <String>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="a9f37-113">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a9f37-113">DESCRIPTION</span></span>

<span data-ttu-id="a9f37-114">`Set-PackageSource`Ersätter en paket källa för en angiven paket leverantör.</span><span class="sxs-lookup"><span data-stu-id="a9f37-114">The `Set-PackageSource` replaces a package source for a specified package provider.</span></span> <span data-ttu-id="a9f37-115">Paket källor hanteras alltid av en paket leverantör.</span><span class="sxs-lookup"><span data-stu-id="a9f37-115">Package sources are always managed by a package provider.</span></span>

## <span data-ttu-id="a9f37-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="a9f37-116">EXAMPLES</span></span>

### <span data-ttu-id="a9f37-117">Exempel 1: ändra en paket källa</span><span class="sxs-lookup"><span data-stu-id="a9f37-117">Example 1: Change a package source</span></span>

<span data-ttu-id="a9f37-118">Det här kommandot ändrar det befintliga namnet på en paket källa.</span><span class="sxs-lookup"><span data-stu-id="a9f37-118">This command changes the existing name of a package source.</span></span> <span data-ttu-id="a9f37-119">Källan är inställd på **betrodd** , vilket eliminerar uppfrågar om du vill verifiera källan när paket installeras.</span><span class="sxs-lookup"><span data-stu-id="a9f37-119">The source is set to **Trusted** , which eliminates prompts to verify the source when packages are installed.</span></span>

```
PS C:\> Set-PackageSource -Name MyNuget -NewName NewNuGet -Trusted -ProviderName NuGet
```

## <span data-ttu-id="a9f37-120">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="a9f37-120">PARAMETERS</span></span>

### <span data-ttu-id="a9f37-121">– ConfigFile</span><span class="sxs-lookup"><span data-stu-id="a9f37-121">-ConfigFile</span></span>

<span data-ttu-id="a9f37-122">Anger en konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="a9f37-122">Specifies a configuration file.</span></span>

```yaml
Type: System.String
Parameter Sets: NuGet:SourceByInputObject, NuGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a9f37-123">-Credential</span><span class="sxs-lookup"><span data-stu-id="a9f37-123">-Credential</span></span>

<span data-ttu-id="a9f37-124">Anger ett användar konto som har behörighet att installera paket leverantörer.</span><span class="sxs-lookup"><span data-stu-id="a9f37-124">Specifies a user account that has permission to install package providers.</span></span>

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

### <span data-ttu-id="a9f37-125">-Force</span><span class="sxs-lookup"><span data-stu-id="a9f37-125">-Force</span></span>

<span data-ttu-id="a9f37-126">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="a9f37-126">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="a9f37-127">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="a9f37-127">-ForceBootstrap</span></span>

<span data-ttu-id="a9f37-128">Anger att `Set-PackageSource` paket leverantören ska installeras automatiskt av **PackageManagement** .</span><span class="sxs-lookup"><span data-stu-id="a9f37-128">Indicates that `Set-PackageSource` forces **PackageManagement** to automatically install the package provider.</span></span>

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

### <span data-ttu-id="a9f37-129">– InputObject</span><span class="sxs-lookup"><span data-stu-id="a9f37-129">-InputObject</span></span>

<span data-ttu-id="a9f37-130">Anger ett paket käll-ID-objekt som representerar det paket som du vill ändra.</span><span class="sxs-lookup"><span data-stu-id="a9f37-130">Specifies a package source ID object that represents the package that you want to change.</span></span> <span data-ttu-id="a9f37-131">Paketets käll-ID är en del av resultatet av `Get-PackageSource` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a9f37-131">Package source IDs are part of the results of the `Get-PackageSource` cmdlet.</span></span>

```yaml
Type: Microsoft.PackageManagement.Packaging.PackageSource
Parameter Sets: SourceByInputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="a9f37-132">– Plats</span><span class="sxs-lookup"><span data-stu-id="a9f37-132">-Location</span></span>

<span data-ttu-id="a9f37-133">Anger den aktuella paket käll platsen.</span><span class="sxs-lookup"><span data-stu-id="a9f37-133">Specifies the current package source location.</span></span> <span data-ttu-id="a9f37-134">Värdet kan vara en URI, en fil Sök väg eller något annat mål format som stöds av paket leverantören.</span><span class="sxs-lookup"><span data-stu-id="a9f37-134">The value can be a URI, a file path, or any other destination format supported by the package provider.</span></span>

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a9f37-135">-Name</span><span class="sxs-lookup"><span data-stu-id="a9f37-135">-Name</span></span>

<span data-ttu-id="a9f37-136">Anger namnet på en paket källa.</span><span class="sxs-lookup"><span data-stu-id="a9f37-136">Specifies a package source's name.</span></span>

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases: SourceName

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a9f37-137">– NewLocation</span><span class="sxs-lookup"><span data-stu-id="a9f37-137">-NewLocation</span></span>

<span data-ttu-id="a9f37-138">Anger den nya platsen för en paket källa.</span><span class="sxs-lookup"><span data-stu-id="a9f37-138">Specifies the new location for a package source.</span></span> <span data-ttu-id="a9f37-139">Värdet kan vara en URI, en fil Sök väg eller något annat mål format som stöds av paket leverantören.</span><span class="sxs-lookup"><span data-stu-id="a9f37-139">The value can be a URI, a file path, or any other destination format supported by the package provider.</span></span>

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

### <span data-ttu-id="a9f37-140">-Nyttnamn</span><span class="sxs-lookup"><span data-stu-id="a9f37-140">-NewName</span></span>

<span data-ttu-id="a9f37-141">Anger det nya namnet som du tilldelar till en paket källa.</span><span class="sxs-lookup"><span data-stu-id="a9f37-141">Specifies the new name you assign to a package source.</span></span>

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

### <span data-ttu-id="a9f37-142">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="a9f37-142">-PackageManagementProvider</span></span>

<span data-ttu-id="a9f37-143">Anger en paket hanterings leverantör.</span><span class="sxs-lookup"><span data-stu-id="a9f37-143">Specifies a package management provider.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a9f37-144">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="a9f37-144">-ProviderName</span></span>

<span data-ttu-id="a9f37-145">Anger ett providernamn.</span><span class="sxs-lookup"><span data-stu-id="a9f37-145">Specifies a provider name.</span></span>

```yaml
Type: System.String
Parameter Sets: SourceBySearch
Aliases: Provider
Accepted values: Bootstrap, NuGet, PowerShellGet

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a9f37-146">-Proxy</span><span class="sxs-lookup"><span data-stu-id="a9f37-146">-Proxy</span></span>

<span data-ttu-id="a9f37-147">Anger en proxyserver för begäran, i stället för att ansluta direkt till Internet resursen.</span><span class="sxs-lookup"><span data-stu-id="a9f37-147">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="a9f37-148">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="a9f37-148">-ProxyCredential</span></span>

<span data-ttu-id="a9f37-149">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="a9f37-149">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="a9f37-150">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="a9f37-150">-PublishLocation</span></span>

<span data-ttu-id="a9f37-151">Anger publicerings platsen.</span><span class="sxs-lookup"><span data-stu-id="a9f37-151">Specifies the publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a9f37-152">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="a9f37-152">-ScriptPublishLocation</span></span>

<span data-ttu-id="a9f37-153">Anger skriptets publicerings plats.</span><span class="sxs-lookup"><span data-stu-id="a9f37-153">Specifies the script publish location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a9f37-154">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="a9f37-154">-ScriptSourceLocation</span></span>

<span data-ttu-id="a9f37-155">Anger sökvägen till skript källan.</span><span class="sxs-lookup"><span data-stu-id="a9f37-155">Specifies the script source location.</span></span>

```yaml
Type: System.String
Parameter Sets: PowerShellGet:SourceByInputObject, PowerShellGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a9f37-156">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="a9f37-156">-SkipValidate</span></span>

<span data-ttu-id="a9f37-157">Växel som hoppar över verifiering av autentiseringsuppgifterna för en paket källa.</span><span class="sxs-lookup"><span data-stu-id="a9f37-157">Switch that skips validating the credentials of a package source.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: NuGet:SourceByInputObject, NuGet:SourceBySearch
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a9f37-158">– Betrodd</span><span class="sxs-lookup"><span data-stu-id="a9f37-158">-Trusted</span></span>

<span data-ttu-id="a9f37-159">Anger att källan är en betrodd paket leverantör.</span><span class="sxs-lookup"><span data-stu-id="a9f37-159">Indicates that the source is a trusted package provider.</span></span> <span data-ttu-id="a9f37-160">Betrodda källor efterfrågar inte verifiering för att installera paket.</span><span class="sxs-lookup"><span data-stu-id="a9f37-160">Trusted sources don't prompt for verification to install packages.</span></span>

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

### <span data-ttu-id="a9f37-161">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a9f37-161">-Confirm</span></span>

<span data-ttu-id="a9f37-162">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a9f37-162">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a9f37-163">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a9f37-163">-WhatIf</span></span>

<span data-ttu-id="a9f37-164">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="a9f37-164">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="a9f37-165">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="a9f37-165">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a9f37-166">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a9f37-166">CommonParameters</span></span>

<span data-ttu-id="a9f37-167">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a9f37-167">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a9f37-168">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a9f37-168">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a9f37-169">INDATA</span><span class="sxs-lookup"><span data-stu-id="a9f37-169">INPUTS</span></span>

### <span data-ttu-id="a9f37-170">`Set-PackageSource` accepterar inte inmatade pipelines.</span><span class="sxs-lookup"><span data-stu-id="a9f37-170">`Set-PackageSource` doesn't accept pipeline input.</span></span>

## <span data-ttu-id="a9f37-171">UTDATA</span><span class="sxs-lookup"><span data-stu-id="a9f37-171">OUTPUTS</span></span>

### <span data-ttu-id="a9f37-172">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="a9f37-172">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="a9f37-173">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="a9f37-173">NOTES</span></span>

## <span data-ttu-id="a9f37-174">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="a9f37-174">RELATED LINKS</span></span>

[<span data-ttu-id="a9f37-175">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="a9f37-175">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="a9f37-176">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="a9f37-176">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="a9f37-177">Registrera – PackageSource</span><span class="sxs-lookup"><span data-stu-id="a9f37-177">Register-PackageSource</span></span>](Register-PackageSource.md)

[<span data-ttu-id="a9f37-178">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="a9f37-178">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)

