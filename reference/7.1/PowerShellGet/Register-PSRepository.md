---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/register-psrepository?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-PSRepository
ms.openlocfilehash: 300d3388c39a86cb732d50404ad7d8c28bd3034e
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94892199"
---
# <span data-ttu-id="afb57-103">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="afb57-103">Register-PSRepository</span></span>

## <span data-ttu-id="afb57-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="afb57-104">SYNOPSIS</span></span>
<span data-ttu-id="afb57-105">Registrerar en PowerShell-lagringsplats.</span><span class="sxs-lookup"><span data-stu-id="afb57-105">Registers a PowerShell repository.</span></span>

## <span data-ttu-id="afb57-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="afb57-106">SYNTAX</span></span>

### <span data-ttu-id="afb57-107">NameParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="afb57-107">NameParameterSet (Default)</span></span>

```
Register-PSRepository [-Name] <String> [-SourceLocation] <Uri> [-PublishLocation <Uri>]
 [-ScriptSourceLocation <Uri>] [-ScriptPublishLocation <Uri>] [-Credential <PSCredential>]
 [-InstallationPolicy <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-PackageManagementProvider <String>] [<CommonParameters>]
```

### <span data-ttu-id="afb57-108">PSGalleryParameterSet</span><span class="sxs-lookup"><span data-stu-id="afb57-108">PSGalleryParameterSet</span></span>

```
Register-PSRepository [-Default] [-InstallationPolicy <String>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="afb57-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="afb57-109">DESCRIPTION</span></span>

<span data-ttu-id="afb57-110">`Register-PSRepository`Cmdleten registrerar standard lagrings platsen för PowerShell-moduler.</span><span class="sxs-lookup"><span data-stu-id="afb57-110">The `Register-PSRepository` cmdlet registers the default repository for PowerShell modules.</span></span> <span data-ttu-id="afb57-111">När en lagrings plats har registrerats kan du referera till den från `Find-Module` `Install-Module` cmdletarna,, och `Publish-Module` .</span><span class="sxs-lookup"><span data-stu-id="afb57-111">After a repository is registered, you can reference it from the `Find-Module`, `Install-Module`, and `Publish-Module` cmdlets.</span></span> <span data-ttu-id="afb57-112">Den registrerade lagrings platsen blir standard lagrings platsen i `Find-Module` och `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="afb57-112">The registered repository becomes the default repository in `Find-Module` and `Install-Module`.</span></span>

<span data-ttu-id="afb57-113">Registrerade databaser är användarspecifika.</span><span class="sxs-lookup"><span data-stu-id="afb57-113">Registered repositories are user-specific.</span></span> <span data-ttu-id="afb57-114">De är inte registrerade i en systemövergripande kontext.</span><span class="sxs-lookup"><span data-stu-id="afb57-114">They are not registered in a system-wide context.</span></span>

<span data-ttu-id="afb57-115">Varje registrerad databas är associerad med en OneGet-paket leverantör som anges med parametern **PackageManagementProvider** .</span><span class="sxs-lookup"><span data-stu-id="afb57-115">Each registered repository is associated with a OneGet package provider, which is specified with the **PackageManagementProvider** parameter.</span></span> <span data-ttu-id="afb57-116">Varje OneGet-Provider är utformad för att samverka med en speciell typ av lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="afb57-116">Each OneGet provider is designed to interact with a specific type of repository.</span></span> <span data-ttu-id="afb57-117">NuGet-providern är till exempel utformad för att samverka med NuGet-baserade databaser.</span><span class="sxs-lookup"><span data-stu-id="afb57-117">For example, the NuGet provider is designed to interact with NuGet-based repositories.</span></span> <span data-ttu-id="afb57-118">Om en OneGet-Provider inte anges under registreringen försöker PowerShellGet hitta en OneGet-provider som kan hantera den angivna käll platsen.</span><span class="sxs-lookup"><span data-stu-id="afb57-118">If a OneGet provider is not specified during registration, PowerShellGet attempts to find a OneGet provider that can handle the specified source location.</span></span>

## <span data-ttu-id="afb57-119">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="afb57-119">EXAMPLES</span></span>

### <span data-ttu-id="afb57-120">Exempel 1: registrera en lagrings plats</span><span class="sxs-lookup"><span data-stu-id="afb57-120">Example 1: Register a repository</span></span>

```powershell
$parameters = @{
  Name = "myNuGetSource"
  SourceLocation = "https://www.myget.org/F/powershellgetdemo/api/v2"
  PublishLocation = "https://www.myget.org/F/powershellgetdemo/api/v2/Packages"
  InstallationPolicy = 'Trusted'
}
Register-PSRepository @parameters
Get-PSRepository
```

```Output
Name                SourceLocation          OneGetProvider       InstallationPolicy
----                --------------          --------------       ------------------
PSGallery           http://go.micro...      NuGet                Untrusted
myNuGetSource       https://myget.c...      NuGet                Trusted
```

<span data-ttu-id="afb57-121">Det första kommandot registreras `https://www.myget.org/F/powershellgetdemo/` som en lagrings plats för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="afb57-121">The first command registers `https://www.myget.org/F/powershellgetdemo/` as a repository for the current user.</span></span> <span data-ttu-id="afb57-122">När myNuGetSource har registrerats kan du uttryckligen referera till den när du söker efter, installerar och publicerar moduler.</span><span class="sxs-lookup"><span data-stu-id="afb57-122">After myNuGetSource is registered, you can explicitly reference it when searching for, installing, and publishing modules.</span></span> <span data-ttu-id="afb57-123">Eftersom parametern **PackageManagementProvider** inte anges är lagrings platsen inte uttryckligen kopplad till en OneGet-paket leverantör, så PowerShellGet avsöker tillgängliga paket leverantörer och kopplar den till NuGet-providern.</span><span class="sxs-lookup"><span data-stu-id="afb57-123">Because the **PackageManagementProvider** parameter isn't specified, the repository is not explicitly associated with a OneGet package provider, so PowerShellGet polls available package providers and associates it with the NuGet provider.</span></span>

<span data-ttu-id="afb57-124">Det andra kommandot hämtar registrerade databaser och visar resultatet.</span><span class="sxs-lookup"><span data-stu-id="afb57-124">The second command gets registered repositories and displays the results.</span></span>

## <span data-ttu-id="afb57-125">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="afb57-125">PARAMETERS</span></span>

### <span data-ttu-id="afb57-126">-Credential</span><span class="sxs-lookup"><span data-stu-id="afb57-126">-Credential</span></span>

<span data-ttu-id="afb57-127">Anger autentiseringsuppgifter för ett konto som har behörighet att registrera en lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="afb57-127">Specifies credentials of an account that has rights to register a repository.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="afb57-128">-Default</span><span class="sxs-lookup"><span data-stu-id="afb57-128">-Default</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PSGalleryParameterSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="afb57-129">-InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="afb57-129">-InstallationPolicy</span></span>

<span data-ttu-id="afb57-130">Anger installations principen.</span><span class="sxs-lookup"><span data-stu-id="afb57-130">Specifies the installation policy.</span></span> <span data-ttu-id="afb57-131">Giltiga värden är: betrodda, ej betrodda.</span><span class="sxs-lookup"><span data-stu-id="afb57-131">Valid values are: Trusted, UnTrusted.</span></span> <span data-ttu-id="afb57-132">Standardvärdet är inte betrott.</span><span class="sxs-lookup"><span data-stu-id="afb57-132">The default value is UnTrusted.</span></span>

<span data-ttu-id="afb57-133">En plats installations princip anger PowerShell-beteende när du installerar från den lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="afb57-133">A repository's installation policy specifies PowerShell behavior when installing from that repository.</span></span> <span data-ttu-id="afb57-134">När du installerar moduler från ett ej betrott lager, uppmanas användaren att bekräfta.</span><span class="sxs-lookup"><span data-stu-id="afb57-134">When installing modules from an UnTrusted repository, the user is prompted for confirmation.</span></span>

<span data-ttu-id="afb57-135">Du kan ställa in **InstallationPolicy** med `Set-PSRepository` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="afb57-135">You can set the **InstallationPolicy** with the `Set-PSRepository` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Trusted, Untrusted

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="afb57-136">-Name</span><span class="sxs-lookup"><span data-stu-id="afb57-136">-Name</span></span>

<span data-ttu-id="afb57-137">Anger namnet på den lagrings plats som ska registreras.</span><span class="sxs-lookup"><span data-stu-id="afb57-137">Specifies the name of the repository to register.</span></span> <span data-ttu-id="afb57-138">Du kan använda det här namnet för att ange lagrings platsen i-cmdlet: ar, till exempel `Find-Module` och `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="afb57-138">You can use this name to specify the repository in cmdlets such as `Find-Module` and `Install-Module`.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="afb57-139">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="afb57-139">-PackageManagementProvider</span></span>

<span data-ttu-id="afb57-140">Anger en OneGet-paket leverantör.</span><span class="sxs-lookup"><span data-stu-id="afb57-140">Specifies a OneGet package provider.</span></span> <span data-ttu-id="afb57-141">Om du inte anger något värde för den här parametern avsöker PowerShellGet de tillgängliga paket leverantörer och kopplar den här lagrings platsen till den första paket leverantören som anger att den kan hantera lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="afb57-141">If you don't specify a value for this parameter, PowerShellGet polls available package providers and associates this repository with the first package provider that indicates it can handle the repository.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="afb57-142">-Proxy</span><span class="sxs-lookup"><span data-stu-id="afb57-142">-Proxy</span></span>

<span data-ttu-id="afb57-143">Anger en proxyserver för begäran, i stället för att ansluta direkt till Internet resursen.</span><span class="sxs-lookup"><span data-stu-id="afb57-143">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="afb57-144">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="afb57-144">-ProxyCredential</span></span>

<span data-ttu-id="afb57-145">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="afb57-145">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="afb57-146">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="afb57-146">-PublishLocation</span></span>

<span data-ttu-id="afb57-147">Anger URI för publicerings platsen.</span><span class="sxs-lookup"><span data-stu-id="afb57-147">Specifies the URI of the publish location.</span></span> <span data-ttu-id="afb57-148">För NuGet-baserade databaser liknar publicerings platsen till exempel `https://someNuGetUrl.com/api/v2/Packages` .</span><span class="sxs-lookup"><span data-stu-id="afb57-148">For example, for NuGet-based repositories, the publish location is similar to `https://someNuGetUrl.com/api/v2/Packages`.</span></span>

```yaml
Type: System.Uri
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="afb57-149">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="afb57-149">-ScriptPublishLocation</span></span>

<span data-ttu-id="afb57-150">Anger skriptets publicerings plats.</span><span class="sxs-lookup"><span data-stu-id="afb57-150">Specifies the script publish location.</span></span>

```yaml
Type: System.Uri
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="afb57-151">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="afb57-151">-ScriptSourceLocation</span></span>

<span data-ttu-id="afb57-152">Anger sökvägen till skript källan.</span><span class="sxs-lookup"><span data-stu-id="afb57-152">Specifies the script source location.</span></span>

```yaml
Type: System.Uri
Parameter Sets: NameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="afb57-153">– SourceLocation</span><span class="sxs-lookup"><span data-stu-id="afb57-153">-SourceLocation</span></span>

<span data-ttu-id="afb57-154">Anger URI för identifiering och installation av moduler från den här lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="afb57-154">Specifies the URI for discovering and installing modules from this repository.</span></span> <span data-ttu-id="afb57-155">En URI kan vara en NuGet Server-feed (den vanligaste situationen), HTTP, HTTPS, FTP eller File location.</span><span class="sxs-lookup"><span data-stu-id="afb57-155">A URI can be a NuGet server feed (most common situation), HTTP, HTTPS, FTP or file location.</span></span>

<span data-ttu-id="afb57-156">För NuGet-baserade databaser liknar till exempel käll platsen `https://someNuGetUrl.com/api/v2` .</span><span class="sxs-lookup"><span data-stu-id="afb57-156">For example, for NuGet-based repositories, the source location is similar to `https://someNuGetUrl.com/api/v2`.</span></span>

```yaml
Type: System.Uri
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="afb57-157">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="afb57-157">CommonParameters</span></span>

<span data-ttu-id="afb57-158">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="afb57-158">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="afb57-159">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="afb57-159">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="afb57-160">INDATA</span><span class="sxs-lookup"><span data-stu-id="afb57-160">INPUTS</span></span>

### <span data-ttu-id="afb57-161">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="afb57-161">System.Management.Automation.PSCredential</span></span>

### <span data-ttu-id="afb57-162">System. URI</span><span class="sxs-lookup"><span data-stu-id="afb57-162">System.Uri</span></span>

## <span data-ttu-id="afb57-163">UTDATA</span><span class="sxs-lookup"><span data-stu-id="afb57-163">OUTPUTS</span></span>

### <span data-ttu-id="afb57-164">System. Object</span><span class="sxs-lookup"><span data-stu-id="afb57-164">System.Object</span></span>

## <span data-ttu-id="afb57-165">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="afb57-165">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="afb57-166">Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1.</span><span class="sxs-lookup"><span data-stu-id="afb57-166">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="afb57-167">Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="afb57-167">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="afb57-168">Använd följande kommando för att se till att du använder TLS 1,2:</span><span class="sxs-lookup"><span data-stu-id="afb57-168">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="afb57-169">Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="afb57-169">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="afb57-170">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="afb57-170">RELATED LINKS</span></span>

[<span data-ttu-id="afb57-171">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="afb57-171">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="afb57-172">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="afb57-172">Set-PSRepository</span></span>](Set-PSRepository.md)

[<span data-ttu-id="afb57-173">Avregistrera-PSRepository</span><span class="sxs-lookup"><span data-stu-id="afb57-173">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)
