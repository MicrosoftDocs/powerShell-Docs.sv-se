---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/powershellget/register-psrepository?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-PSRepository
ms.openlocfilehash: be7ffa38a0409fa7ef0d01649b863a32732e34de
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262928"
---
# <span data-ttu-id="0761f-103">Register-PSRepository</span><span class="sxs-lookup"><span data-stu-id="0761f-103">Register-PSRepository</span></span>

## <span data-ttu-id="0761f-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="0761f-104">SYNOPSIS</span></span>
<span data-ttu-id="0761f-105">Registrerar en PowerShell-lagringsplats.</span><span class="sxs-lookup"><span data-stu-id="0761f-105">Registers a PowerShell repository.</span></span>

## <span data-ttu-id="0761f-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0761f-106">SYNTAX</span></span>

### <span data-ttu-id="0761f-107">NameParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="0761f-107">NameParameterSet (Default)</span></span>

```
Register-PSRepository [-Name] <String> [-SourceLocation] <Uri> [-PublishLocation <Uri>]
 [-ScriptSourceLocation <Uri>] [-ScriptPublishLocation <Uri>] [-Credential <PSCredential>]
 [-InstallationPolicy <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-PackageManagementProvider <String>] [<CommonParameters>]
```

### <span data-ttu-id="0761f-108">PSGalleryParameterSet</span><span class="sxs-lookup"><span data-stu-id="0761f-108">PSGalleryParameterSet</span></span>

```
Register-PSRepository [-Default] [-InstallationPolicy <String>] [-Proxy <Uri>]
 [-ProxyCredential <PSCredential>] [<CommonParameters>]
```

## <span data-ttu-id="0761f-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="0761f-109">DESCRIPTION</span></span>

<span data-ttu-id="0761f-110">`Register-PSRepository`Cmdleten registrerar standard lagrings platsen för PowerShell-moduler.</span><span class="sxs-lookup"><span data-stu-id="0761f-110">The `Register-PSRepository` cmdlet registers the default repository for PowerShell modules.</span></span> <span data-ttu-id="0761f-111">När en lagrings plats har registrerats kan du referera till den från `Find-Module` `Install-Module` cmdletarna,, och `Publish-Module` .</span><span class="sxs-lookup"><span data-stu-id="0761f-111">After a repository is registered, you can reference it from the `Find-Module`, `Install-Module`, and `Publish-Module` cmdlets.</span></span> <span data-ttu-id="0761f-112">Den registrerade lagrings platsen blir standard lagrings platsen i `Find-Module` och `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="0761f-112">The registered repository becomes the default repository in `Find-Module` and `Install-Module`.</span></span>

<span data-ttu-id="0761f-113">Registrerade databaser är användarspecifika.</span><span class="sxs-lookup"><span data-stu-id="0761f-113">Registered repositories are user-specific.</span></span> <span data-ttu-id="0761f-114">De är inte registrerade i en systemövergripande kontext.</span><span class="sxs-lookup"><span data-stu-id="0761f-114">They are not registered in a system-wide context.</span></span>

<span data-ttu-id="0761f-115">Varje registrerad databas är associerad med en OneGet-paket leverantör som anges med parametern **PackageManagementProvider** .</span><span class="sxs-lookup"><span data-stu-id="0761f-115">Each registered repository is associated with a OneGet package provider, which is specified with the **PackageManagementProvider** parameter.</span></span> <span data-ttu-id="0761f-116">Varje OneGet-Provider är utformad för att samverka med en speciell typ av lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="0761f-116">Each OneGet provider is designed to interact with a specific type of repository.</span></span> <span data-ttu-id="0761f-117">NuGet-providern är till exempel utformad för att samverka med NuGet-baserade databaser.</span><span class="sxs-lookup"><span data-stu-id="0761f-117">For example, the NuGet provider is designed to interact with NuGet-based repositories.</span></span> <span data-ttu-id="0761f-118">Om en OneGet-Provider inte anges under registreringen försöker PowerShellGet hitta en OneGet-provider som kan hantera den angivna käll platsen.</span><span class="sxs-lookup"><span data-stu-id="0761f-118">If a OneGet provider is not specified during registration, PowerShellGet attempts to find a OneGet provider that can handle the specified source location.</span></span>

## <span data-ttu-id="0761f-119">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="0761f-119">EXAMPLES</span></span>

### <span data-ttu-id="0761f-120">Exempel 1: registrera en lagrings plats</span><span class="sxs-lookup"><span data-stu-id="0761f-120">Example 1: Register a repository</span></span>

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

<span data-ttu-id="0761f-121">Det första kommandot registreras `https://www.myget.org/F/powershellgetdemo/` som en lagrings plats för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="0761f-121">The first command registers `https://www.myget.org/F/powershellgetdemo/` as a repository for the current user.</span></span> <span data-ttu-id="0761f-122">När myNuGetSource har registrerats kan du uttryckligen referera till den när du söker efter, installerar och publicerar moduler.</span><span class="sxs-lookup"><span data-stu-id="0761f-122">After myNuGetSource is registered, you can explicitly reference it when searching for, installing, and publishing modules.</span></span> <span data-ttu-id="0761f-123">Eftersom parametern **PackageManagementProvider** inte anges är lagrings platsen inte uttryckligen kopplad till en OneGet-paket leverantör, så PowerShellGet avsöker tillgängliga paket leverantörer och kopplar den till NuGet-providern.</span><span class="sxs-lookup"><span data-stu-id="0761f-123">Because the **PackageManagementProvider** parameter isn't specified, the repository is not explicitly associated with a OneGet package provider, so PowerShellGet polls available package providers and associates it with the NuGet provider.</span></span>

<span data-ttu-id="0761f-124">Det andra kommandot hämtar registrerade databaser och visar resultatet.</span><span class="sxs-lookup"><span data-stu-id="0761f-124">The second command gets registered repositories and displays the results.</span></span>

## <span data-ttu-id="0761f-125">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="0761f-125">PARAMETERS</span></span>

### <span data-ttu-id="0761f-126">-Credential</span><span class="sxs-lookup"><span data-stu-id="0761f-126">-Credential</span></span>

<span data-ttu-id="0761f-127">Anger autentiseringsuppgifter för ett konto som har behörighet att registrera en lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="0761f-127">Specifies credentials of an account that has rights to register a repository.</span></span>

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

### <span data-ttu-id="0761f-128">-Default</span><span class="sxs-lookup"><span data-stu-id="0761f-128">-Default</span></span>

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

### <span data-ttu-id="0761f-129">-InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="0761f-129">-InstallationPolicy</span></span>

<span data-ttu-id="0761f-130">Anger installations principen.</span><span class="sxs-lookup"><span data-stu-id="0761f-130">Specifies the installation policy.</span></span> <span data-ttu-id="0761f-131">Giltiga värden är: betrodda, ej betrodda.</span><span class="sxs-lookup"><span data-stu-id="0761f-131">Valid values are: Trusted, UnTrusted.</span></span> <span data-ttu-id="0761f-132">Standardvärdet är inte betrott.</span><span class="sxs-lookup"><span data-stu-id="0761f-132">The default value is UnTrusted.</span></span>

<span data-ttu-id="0761f-133">En plats installations princip anger PowerShell-beteende när du installerar från den lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="0761f-133">A repository's installation policy specifies PowerShell behavior when installing from that repository.</span></span> <span data-ttu-id="0761f-134">När du installerar moduler från ett ej betrott lager, uppmanas användaren att bekräfta.</span><span class="sxs-lookup"><span data-stu-id="0761f-134">When installing modules from an UnTrusted repository, the user is prompted for confirmation.</span></span>

<span data-ttu-id="0761f-135">Du kan ställa in **InstallationPolicy** med `Set-PSRepository` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="0761f-135">You can set the **InstallationPolicy** with the `Set-PSRepository` cmdlet.</span></span>

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

### <span data-ttu-id="0761f-136">-Name</span><span class="sxs-lookup"><span data-stu-id="0761f-136">-Name</span></span>

<span data-ttu-id="0761f-137">Anger namnet på den lagrings plats som ska registreras.</span><span class="sxs-lookup"><span data-stu-id="0761f-137">Specifies the name of the repository to register.</span></span> <span data-ttu-id="0761f-138">Du kan använda det här namnet för att ange lagrings platsen i-cmdlet: ar, till exempel `Find-Module` och `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="0761f-138">You can use this name to specify the repository in cmdlets such as `Find-Module` and `Install-Module`.</span></span>

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

### <span data-ttu-id="0761f-139">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="0761f-139">-PackageManagementProvider</span></span>

<span data-ttu-id="0761f-140">Anger en OneGet-paket leverantör.</span><span class="sxs-lookup"><span data-stu-id="0761f-140">Specifies a OneGet package provider.</span></span> <span data-ttu-id="0761f-141">Om du inte anger något värde för den här parametern avsöker PowerShellGet de tillgängliga paket leverantörer och kopplar den här lagrings platsen till den första paket leverantören som anger att den kan hantera lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="0761f-141">If you don't specify a value for this parameter, PowerShellGet polls available package providers and associates this repository with the first package provider that indicates it can handle the repository.</span></span>

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

### <span data-ttu-id="0761f-142">-Proxy</span><span class="sxs-lookup"><span data-stu-id="0761f-142">-Proxy</span></span>

<span data-ttu-id="0761f-143">Anger en proxyserver för begäran, i stället för att ansluta direkt till Internet resursen.</span><span class="sxs-lookup"><span data-stu-id="0761f-143">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="0761f-144">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="0761f-144">-ProxyCredential</span></span>

<span data-ttu-id="0761f-145">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="0761f-145">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="0761f-146">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="0761f-146">-PublishLocation</span></span>

<span data-ttu-id="0761f-147">Anger URI för publicerings platsen.</span><span class="sxs-lookup"><span data-stu-id="0761f-147">Specifies the URI of the publish location.</span></span> <span data-ttu-id="0761f-148">För NuGet-baserade databaser liknar publicerings platsen till exempel `https://someNuGetUrl.com/api/v2/Packages` .</span><span class="sxs-lookup"><span data-stu-id="0761f-148">For example, for NuGet-based repositories, the publish location is similar to `https://someNuGetUrl.com/api/v2/Packages`.</span></span>

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

### <span data-ttu-id="0761f-149">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="0761f-149">-ScriptPublishLocation</span></span>

<span data-ttu-id="0761f-150">Anger skriptets publicerings plats.</span><span class="sxs-lookup"><span data-stu-id="0761f-150">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="0761f-151">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="0761f-151">-ScriptSourceLocation</span></span>

<span data-ttu-id="0761f-152">Anger sökvägen till skript källan.</span><span class="sxs-lookup"><span data-stu-id="0761f-152">Specifies the script source location.</span></span>

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

### <span data-ttu-id="0761f-153">– SourceLocation</span><span class="sxs-lookup"><span data-stu-id="0761f-153">-SourceLocation</span></span>

<span data-ttu-id="0761f-154">Anger URI för identifiering och installation av moduler från den här lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="0761f-154">Specifies the URI for discovering and installing modules from this repository.</span></span> <span data-ttu-id="0761f-155">En URI kan vara en NuGet Server-feed (den vanligaste situationen), HTTP, HTTPS, FTP eller File location.</span><span class="sxs-lookup"><span data-stu-id="0761f-155">A URI can be a NuGet server feed (most common situation), HTTP, HTTPS, FTP or file location.</span></span>

<span data-ttu-id="0761f-156">För NuGet-baserade databaser liknar till exempel käll platsen `https://someNuGetUrl.com/api/v2` .</span><span class="sxs-lookup"><span data-stu-id="0761f-156">For example, for NuGet-based repositories, the source location is similar to `https://someNuGetUrl.com/api/v2`.</span></span>

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

### <span data-ttu-id="0761f-157">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0761f-157">CommonParameters</span></span>

<span data-ttu-id="0761f-158">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0761f-158">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0761f-159">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="0761f-159">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0761f-160">INDATA</span><span class="sxs-lookup"><span data-stu-id="0761f-160">INPUTS</span></span>

### <span data-ttu-id="0761f-161">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="0761f-161">System.Management.Automation.PSCredential</span></span>

### <span data-ttu-id="0761f-162">System. URI</span><span class="sxs-lookup"><span data-stu-id="0761f-162">System.Uri</span></span>

## <span data-ttu-id="0761f-163">UTDATA</span><span class="sxs-lookup"><span data-stu-id="0761f-163">OUTPUTS</span></span>

### <span data-ttu-id="0761f-164">System. Object</span><span class="sxs-lookup"><span data-stu-id="0761f-164">System.Object</span></span>

## <span data-ttu-id="0761f-165">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="0761f-165">NOTES</span></span>

## <span data-ttu-id="0761f-166">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="0761f-166">RELATED LINKS</span></span>

[<span data-ttu-id="0761f-167">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="0761f-167">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="0761f-168">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="0761f-168">Set-PSRepository</span></span>](Set-PSRepository.md)

[<span data-ttu-id="0761f-169">Avregistrera-PSRepository</span><span class="sxs-lookup"><span data-stu-id="0761f-169">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)
