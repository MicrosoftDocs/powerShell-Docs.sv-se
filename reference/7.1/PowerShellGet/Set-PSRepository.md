---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/set-psrepository?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSRepository
ms.openlocfilehash: 5b9addd42ca655436ad12d624afd39fa6747dadf
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264057"
---
# <span data-ttu-id="f53ef-103">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="f53ef-103">Set-PSRepository</span></span>

## <span data-ttu-id="f53ef-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="f53ef-104">SYNOPSIS</span></span>
<span data-ttu-id="f53ef-105">Anger värden för en registrerad lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="f53ef-105">Sets values for a registered repository.</span></span>

## <span data-ttu-id="f53ef-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f53ef-106">SYNTAX</span></span>

```
Set-PSRepository [-Name] <String> [[-SourceLocation] <Uri>] [-PublishLocation <Uri>]
 [-ScriptSourceLocation <Uri>] [-ScriptPublishLocation <Uri>] [-Credential <PSCredential>]
 [-InstallationPolicy <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-PackageManagementProvider <String>] [<CommonParameters>]
```

## <span data-ttu-id="f53ef-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="f53ef-107">DESCRIPTION</span></span>

<span data-ttu-id="f53ef-108">`Set-PSRepository`Cmdlet: en anger värden för en registrerad modul-lagringsplats.</span><span class="sxs-lookup"><span data-stu-id="f53ef-108">The `Set-PSRepository` cmdlet sets values for a registered module repository.</span></span> <span data-ttu-id="f53ef-109">Inställningarna är beständiga för den aktuella användaren och gäller för alla versioner av PowerShell som är installerade för den användaren.</span><span class="sxs-lookup"><span data-stu-id="f53ef-109">The settings are persistent for the current user and apply to all versions of PowerShell installed for that user.</span></span>

## <span data-ttu-id="f53ef-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="f53ef-110">EXAMPLES</span></span>

### <span data-ttu-id="f53ef-111">Exempel 1: Ange installations principen för en lagrings plats</span><span class="sxs-lookup"><span data-stu-id="f53ef-111">Example 1: Set the installation policy for a repository</span></span>

```powershell
Set-PSRepository -Name "myInternalSource" -InstallationPolicy Trusted
```

<span data-ttu-id="f53ef-112">Det här kommandot anger installations principen för **myInternalSource** -lagringsplatsen till **betrodd** , så att du inte tillfrågas innan du installerar moduler från den källan.</span><span class="sxs-lookup"><span data-stu-id="f53ef-112">This command sets the installation policy for the **myInternalSource** repository to **Trusted** , so that you are not prompted before installing modules from that source.</span></span>

### <span data-ttu-id="f53ef-113">Exempel 2: Ange käll-och publicerings platser för en lagrings plats</span><span class="sxs-lookup"><span data-stu-id="f53ef-113">Example 2: Set the source and publish locations for a repository</span></span>

```powershell
Set-PSRepository -Name "myInternalSource" -SourceLocation 'https://someNuGetUrl.com/api/v2' -PublishLocation 'https://someNuGetUrl.com/api/v2/packages'
```

<span data-ttu-id="f53ef-114">Det här kommandot anger käll platsen och publicerings platsen för **myInternalSource** till de angivna URI: erna.</span><span class="sxs-lookup"><span data-stu-id="f53ef-114">This command sets the source location and publish location for **myInternalSource** to the specified URIs.</span></span>

## <span data-ttu-id="f53ef-115">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="f53ef-115">PARAMETERS</span></span>

### <span data-ttu-id="f53ef-116">-Credential</span><span class="sxs-lookup"><span data-stu-id="f53ef-116">-Credential</span></span>

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

### <span data-ttu-id="f53ef-117">-InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="f53ef-117">-InstallationPolicy</span></span>

<span data-ttu-id="f53ef-118">Anger installations principen.</span><span class="sxs-lookup"><span data-stu-id="f53ef-118">Specifies the installation policy.</span></span> <span data-ttu-id="f53ef-119">Giltiga värden är: **betrodda** , **ej betrodda**.</span><span class="sxs-lookup"><span data-stu-id="f53ef-119">Valid values are: **Trusted** , **Untrusted**.</span></span>

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

### <span data-ttu-id="f53ef-120">-Name</span><span class="sxs-lookup"><span data-stu-id="f53ef-120">-Name</span></span>

<span data-ttu-id="f53ef-121">Anger namnet på lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="f53ef-121">Specifies the name of the repository.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f53ef-122">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="f53ef-122">-PackageManagementProvider</span></span>

<span data-ttu-id="f53ef-123">Anger paket hanterings leverantören.</span><span class="sxs-lookup"><span data-stu-id="f53ef-123">Specifies the package management provider.</span></span>

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

### <span data-ttu-id="f53ef-124">-Proxy</span><span class="sxs-lookup"><span data-stu-id="f53ef-124">-Proxy</span></span>

<span data-ttu-id="f53ef-125">Anger en proxyserver för begäran, i stället för att ansluta direkt till Internet resursen.</span><span class="sxs-lookup"><span data-stu-id="f53ef-125">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="f53ef-126">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="f53ef-126">-ProxyCredential</span></span>

<span data-ttu-id="f53ef-127">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="f53ef-127">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="f53ef-128">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="f53ef-128">-PublishLocation</span></span>

<span data-ttu-id="f53ef-129">Anger URI för publicerings platsen.</span><span class="sxs-lookup"><span data-stu-id="f53ef-129">Specifies the URI of the publish location.</span></span> <span data-ttu-id="f53ef-130">För NuGet-baserade databaser liknar publicerings platsen till exempel `https://someNuGetUrl.com/api/v2/Packages` .</span><span class="sxs-lookup"><span data-stu-id="f53ef-130">For example, for NuGet-based repositories, the publish location is similar to `https://someNuGetUrl.com/api/v2/Packages`.</span></span>

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

### <span data-ttu-id="f53ef-131">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="f53ef-131">-ScriptPublishLocation</span></span>

<span data-ttu-id="f53ef-132">Anger skriptets publicerings plats.</span><span class="sxs-lookup"><span data-stu-id="f53ef-132">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="f53ef-133">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="f53ef-133">-ScriptSourceLocation</span></span>

<span data-ttu-id="f53ef-134">Anger sökvägen till skript källan.</span><span class="sxs-lookup"><span data-stu-id="f53ef-134">Specifies the script source location.</span></span>

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

### <span data-ttu-id="f53ef-135">– SourceLocation</span><span class="sxs-lookup"><span data-stu-id="f53ef-135">-SourceLocation</span></span>

<span data-ttu-id="f53ef-136">Anger URI för identifiering och installation av moduler från den här lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="f53ef-136">Specifies the URI for discovering and installing modules from this repository.</span></span> <span data-ttu-id="f53ef-137">För NuGet-baserade databaser liknar till exempel käll platsen `https://someNuGetUrl.com/api/v2` .</span><span class="sxs-lookup"><span data-stu-id="f53ef-137">For example, for NuGet-based repositories, the source location is similar to `https://someNuGetUrl.com/api/v2`.</span></span>

```yaml
Type: System.Uri
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f53ef-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f53ef-138">CommonParameters</span></span>

<span data-ttu-id="f53ef-139">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f53ef-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f53ef-140">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f53ef-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f53ef-141">INDATA</span><span class="sxs-lookup"><span data-stu-id="f53ef-141">INPUTS</span></span>

### <span data-ttu-id="f53ef-142">System. String</span><span class="sxs-lookup"><span data-stu-id="f53ef-142">System.String</span></span>

### <span data-ttu-id="f53ef-143">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="f53ef-143">System.Management.Automation.PSCredential</span></span>

### <span data-ttu-id="f53ef-144">System. URI</span><span class="sxs-lookup"><span data-stu-id="f53ef-144">System.Uri</span></span>

## <span data-ttu-id="f53ef-145">UTDATA</span><span class="sxs-lookup"><span data-stu-id="f53ef-145">OUTPUTS</span></span>

### <span data-ttu-id="f53ef-146">System. Object</span><span class="sxs-lookup"><span data-stu-id="f53ef-146">System.Object</span></span>

## <span data-ttu-id="f53ef-147">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="f53ef-147">NOTES</span></span>

## <span data-ttu-id="f53ef-148">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="f53ef-148">RELATED LINKS</span></span>

[<span data-ttu-id="f53ef-149">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="f53ef-149">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="f53ef-150">Registrera – PSRepository</span><span class="sxs-lookup"><span data-stu-id="f53ef-150">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="f53ef-151">Avregistrera-PSRepository</span><span class="sxs-lookup"><span data-stu-id="f53ef-151">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)

