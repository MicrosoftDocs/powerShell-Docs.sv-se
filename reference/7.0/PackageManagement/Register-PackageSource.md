---
external help file: Microsoft.PowerShell.PackageManagement.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PackageManagement
ms.date: 04/01/2019
online version: https://docs.microsoft.com/powershell/module/packagemanagement/register-packagesource?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-PackageSource
ms.openlocfilehash: ee51729726c9f10dc7842130b65e671f909ac234
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262437"
---
# <span data-ttu-id="70ed8-103">Register-PackageSource</span><span class="sxs-lookup"><span data-stu-id="70ed8-103">Register-PackageSource</span></span>

## <span data-ttu-id="70ed8-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="70ed8-104">SYNOPSIS</span></span>
<span data-ttu-id="70ed8-105">Lägger till en paket källa för en angiven paket leverantör.</span><span class="sxs-lookup"><span data-stu-id="70ed8-105">Adds a package source for a specified package provider.</span></span>

## <span data-ttu-id="70ed8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="70ed8-106">SYNTAX</span></span>

### <span data-ttu-id="70ed8-107">SourceBySearch</span><span class="sxs-lookup"><span data-stu-id="70ed8-107">SourceBySearch</span></span>

```
Register-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [[-Name] <String>]
 [[-Location] <String>] [-Credential <PSCredential>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ProviderName <String>] [<CommonParameters>]
```

### <span data-ttu-id="70ed8-108">NuGet</span><span class="sxs-lookup"><span data-stu-id="70ed8-108">NuGet</span></span>

```
Register-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [[-Name] <String>]
 [[-Location] <String>] [-Credential <PSCredential>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-ConfigFile <String>] [-SkipValidate] [<CommonParameters>]
```

### <span data-ttu-id="70ed8-109">PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="70ed8-109">PowerShellGet</span></span>

```
Register-PackageSource [-Proxy <Uri>] [-ProxyCredential <PSCredential>] [[-Name] <String>]
 [[-Location] <String>] [-Credential <PSCredential>] [-Trusted] [-Force] [-ForceBootstrap] [-WhatIf]
 [-Confirm] [-PackageManagementProvider <String>] [-PublishLocation <String>]
 [-ScriptSourceLocation <String>] [-ScriptPublishLocation <String>] [<CommonParameters>]
```

## <span data-ttu-id="70ed8-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="70ed8-110">DESCRIPTION</span></span>

<span data-ttu-id="70ed8-111">`Register-PackageSource`Cmdleten lägger till en paket källa för en angiven paket leverantör.</span><span class="sxs-lookup"><span data-stu-id="70ed8-111">The `Register-PackageSource` cmdlet adds a package source for a specified package provider.</span></span> <span data-ttu-id="70ed8-112">Paket källor hanteras alltid av en paket leverantör.</span><span class="sxs-lookup"><span data-stu-id="70ed8-112">Package sources are always managed by a package provider.</span></span> <span data-ttu-id="70ed8-113">Om paket leverantören inte kan lägga till eller ersätta en paket källa genererar providern ett fel meddelande.</span><span class="sxs-lookup"><span data-stu-id="70ed8-113">If the package provider cannot add or replace a package source, the provider generates an error message.</span></span>

## <span data-ttu-id="70ed8-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="70ed8-114">EXAMPLES</span></span>

### <span data-ttu-id="70ed8-115">Exempel 1: registrera en paket källa för NuGet-providern</span><span class="sxs-lookup"><span data-stu-id="70ed8-115">Example 1: Register a package source for the NuGet provider</span></span>

<span data-ttu-id="70ed8-116">Det här kommandot registrerar en paket källa, en webbaserad plats för **NuGet** -providern.</span><span class="sxs-lookup"><span data-stu-id="70ed8-116">This command registers a package source, a web-based location for the **NuGet** provider.</span></span> <span data-ttu-id="70ed8-117">Som standard är källorna inte betrodda.</span><span class="sxs-lookup"><span data-stu-id="70ed8-117">By default, sources aren't trusted.</span></span> <span data-ttu-id="70ed8-118">Du uppmanas att bekräfta att källan är betrodd innan paket installeras.</span><span class="sxs-lookup"><span data-stu-id="70ed8-118">You are prompted to confirm the source is trusted before packages are installed.</span></span> <span data-ttu-id="70ed8-119">Om du vill åsidosätta standardvärdet använder du `-Trusted` parametern.</span><span class="sxs-lookup"><span data-stu-id="70ed8-119">To override the default, use the `-Trusted` parameter.</span></span>

```powershell
Register-PackageSource -Name MyNuGet -Location https://www.nuget.org/api/v2 -ProviderName NuGet
```

```Output
Name          ProviderName     IsTrusted  Location
----          ------------     ---------  --------
MyNuGet       NuGet            False      https://www.nuget.org/api/v2
```

## <span data-ttu-id="70ed8-120">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="70ed8-120">PARAMETERS</span></span>

### <span data-ttu-id="70ed8-121">– ConfigFile</span><span class="sxs-lookup"><span data-stu-id="70ed8-121">-ConfigFile</span></span>

<span data-ttu-id="70ed8-122">Anger en konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="70ed8-122">Specifies a configuration file.</span></span>

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

### <span data-ttu-id="70ed8-123">-Credential</span><span class="sxs-lookup"><span data-stu-id="70ed8-123">-Credential</span></span>

<span data-ttu-id="70ed8-124">Anger ett användar konto som har behörighet att komma åt den autentiserade platsen.</span><span class="sxs-lookup"><span data-stu-id="70ed8-124">Specifies a user account that has permission to access the authenticated location.</span></span>

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

### <span data-ttu-id="70ed8-125">-Force</span><span class="sxs-lookup"><span data-stu-id="70ed8-125">-Force</span></span>

<span data-ttu-id="70ed8-126">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="70ed8-126">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="70ed8-127">-ForceBootstrap</span><span class="sxs-lookup"><span data-stu-id="70ed8-127">-ForceBootstrap</span></span>

<span data-ttu-id="70ed8-128">Anger att paket leverantören installeras automatiskt av den här cmdleten.</span><span class="sxs-lookup"><span data-stu-id="70ed8-128">Indicates that this cmdlet automatically installs the package provider.</span></span>

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

### <span data-ttu-id="70ed8-129">– Plats</span><span class="sxs-lookup"><span data-stu-id="70ed8-129">-Location</span></span>

<span data-ttu-id="70ed8-130">Anger paketets käll plats.</span><span class="sxs-lookup"><span data-stu-id="70ed8-130">Specifies the package source location.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="70ed8-131">-Name</span><span class="sxs-lookup"><span data-stu-id="70ed8-131">-Name</span></span>

<span data-ttu-id="70ed8-132">Anger namnet på den paket källa som ska registreras.</span><span class="sxs-lookup"><span data-stu-id="70ed8-132">Specifies the name of the package source to register.</span></span>

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

### <span data-ttu-id="70ed8-133">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="70ed8-133">-PackageManagementProvider</span></span>

<span data-ttu-id="70ed8-134">Anger paket hanterings leverantören.</span><span class="sxs-lookup"><span data-stu-id="70ed8-134">Specifies the Package Management provider.</span></span>

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

### <span data-ttu-id="70ed8-135">-ProviderName</span><span class="sxs-lookup"><span data-stu-id="70ed8-135">-ProviderName</span></span>

<span data-ttu-id="70ed8-136">Anger paket leverantörens namn.</span><span class="sxs-lookup"><span data-stu-id="70ed8-136">Specifies the package provider's name.</span></span>

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

### <span data-ttu-id="70ed8-137">-Proxy</span><span class="sxs-lookup"><span data-stu-id="70ed8-137">-Proxy</span></span>

<span data-ttu-id="70ed8-138">Anger en proxyserver för begäran, i stället för en direkt anslutning till Internet resursen.</span><span class="sxs-lookup"><span data-stu-id="70ed8-138">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="70ed8-139">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="70ed8-139">-ProxyCredential</span></span>

<span data-ttu-id="70ed8-140">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="70ed8-140">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="70ed8-141">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="70ed8-141">-PublishLocation</span></span>

<span data-ttu-id="70ed8-142">Anger publicerings platsen.</span><span class="sxs-lookup"><span data-stu-id="70ed8-142">Specifies the publish location.</span></span>

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

### <span data-ttu-id="70ed8-143">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="70ed8-143">-ScriptPublishLocation</span></span>

<span data-ttu-id="70ed8-144">Anger skriptets publicerings plats.</span><span class="sxs-lookup"><span data-stu-id="70ed8-144">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="70ed8-145">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="70ed8-145">-ScriptSourceLocation</span></span>

<span data-ttu-id="70ed8-146">Anger sökvägen till skript källan.</span><span class="sxs-lookup"><span data-stu-id="70ed8-146">Specifies the script source location.</span></span>

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

### <span data-ttu-id="70ed8-147">-SkipValidate</span><span class="sxs-lookup"><span data-stu-id="70ed8-147">-SkipValidate</span></span>

<span data-ttu-id="70ed8-148">Växel som hoppar över verifiering av autentiseringsuppgifterna för en paket källa.</span><span class="sxs-lookup"><span data-stu-id="70ed8-148">Switch that skips validating the credentials of a package source.</span></span>

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

### <span data-ttu-id="70ed8-149">– Betrodd</span><span class="sxs-lookup"><span data-stu-id="70ed8-149">-Trusted</span></span>

<span data-ttu-id="70ed8-150">Anger att paket källan är betrodd.</span><span class="sxs-lookup"><span data-stu-id="70ed8-150">Indicates that the package source is trusted.</span></span>

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

### <span data-ttu-id="70ed8-151">-Confirm</span><span class="sxs-lookup"><span data-stu-id="70ed8-151">-Confirm</span></span>

<span data-ttu-id="70ed8-152">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="70ed8-152">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="70ed8-153">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="70ed8-153">-WhatIf</span></span>

<span data-ttu-id="70ed8-154">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="70ed8-154">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="70ed8-155">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="70ed8-155">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="70ed8-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="70ed8-156">CommonParameters</span></span>

<span data-ttu-id="70ed8-157">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="70ed8-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="70ed8-158">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="70ed8-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="70ed8-159">INDATA</span><span class="sxs-lookup"><span data-stu-id="70ed8-159">INPUTS</span></span>

## <span data-ttu-id="70ed8-160">UTDATA</span><span class="sxs-lookup"><span data-stu-id="70ed8-160">OUTPUTS</span></span>

## <span data-ttu-id="70ed8-161">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="70ed8-161">NOTES</span></span>

## <span data-ttu-id="70ed8-162">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="70ed8-162">RELATED LINKS</span></span>

[<span data-ttu-id="70ed8-163">about_PackageManagement</span><span class="sxs-lookup"><span data-stu-id="70ed8-163">about_PackageManagement</span></span>](../Microsoft.PowerShell.Core/About/about_PackageManagement.md)

[<span data-ttu-id="70ed8-164">Get-PackageSource</span><span class="sxs-lookup"><span data-stu-id="70ed8-164">Get-PackageSource</span></span>](Get-PackageSource.md)

[<span data-ttu-id="70ed8-165">Set-PackageSource</span><span class="sxs-lookup"><span data-stu-id="70ed8-165">Set-PackageSource</span></span>](Set-PackageSource.md)

[<span data-ttu-id="70ed8-166">Unregister-PackageSource</span><span class="sxs-lookup"><span data-stu-id="70ed8-166">Unregister-PackageSource</span></span>](Unregister-PackageSource.md)
