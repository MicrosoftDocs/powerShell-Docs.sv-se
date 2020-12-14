---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 04/22/2020
online version: https://docs.microsoft.com/powershell/module/powershellget/set-psrepository?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSRepository
ms.openlocfilehash: 2b23a121249c5cc9037e0440dfaed17a1a9f76e9
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891565"
---
# <span data-ttu-id="cde37-103">Set-PSRepository</span><span class="sxs-lookup"><span data-stu-id="cde37-103">Set-PSRepository</span></span>

## <span data-ttu-id="cde37-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="cde37-104">SYNOPSIS</span></span>
<span data-ttu-id="cde37-105">Anger värden för en registrerad lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="cde37-105">Sets values for a registered repository.</span></span>

## <span data-ttu-id="cde37-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="cde37-106">SYNTAX</span></span>

```
Set-PSRepository [-Name] <String> [[-SourceLocation] <Uri>] [-PublishLocation <Uri>]
 [-ScriptSourceLocation <Uri>] [-ScriptPublishLocation <Uri>] [-Credential <PSCredential>]
 [-InstallationPolicy <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-PackageManagementProvider <String>] [<CommonParameters>]
```

## <span data-ttu-id="cde37-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="cde37-107">DESCRIPTION</span></span>

<span data-ttu-id="cde37-108">`Set-PSRepository`Cmdlet: en anger värden för en registrerad modul-lagringsplats.</span><span class="sxs-lookup"><span data-stu-id="cde37-108">The `Set-PSRepository` cmdlet sets values for a registered module repository.</span></span> <span data-ttu-id="cde37-109">Inställningarna är beständiga för den aktuella användaren och gäller för alla versioner av PowerShell som är installerade för den användaren.</span><span class="sxs-lookup"><span data-stu-id="cde37-109">The settings are persistent for the current user and apply to all versions of PowerShell installed for that user.</span></span>

## <span data-ttu-id="cde37-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="cde37-110">EXAMPLES</span></span>

### <span data-ttu-id="cde37-111">Exempel 1: Ange installations principen för en lagrings plats</span><span class="sxs-lookup"><span data-stu-id="cde37-111">Example 1: Set the installation policy for a repository</span></span>

```powershell
Set-PSRepository -Name "myInternalSource" -InstallationPolicy Trusted
```

<span data-ttu-id="cde37-112">Det här kommandot anger installations principen för **myInternalSource** -lagringsplatsen till **betrodd**, så att du inte tillfrågas innan du installerar moduler från den källan.</span><span class="sxs-lookup"><span data-stu-id="cde37-112">This command sets the installation policy for the **myInternalSource** repository to **Trusted**, so that you are not prompted before installing modules from that source.</span></span>

### <span data-ttu-id="cde37-113">Exempel 2: Ange käll-och publicerings platser för en lagrings plats</span><span class="sxs-lookup"><span data-stu-id="cde37-113">Example 2: Set the source and publish locations for a repository</span></span>

```powershell
Set-PSRepository -Name "myInternalSource" -SourceLocation 'https://someNuGetUrl.com/api/v2' -PublishLocation 'https://someNuGetUrl.com/api/v2/packages'
```

<span data-ttu-id="cde37-114">Det här kommandot anger käll platsen och publicerings platsen för **myInternalSource** till de angivna URI: erna.</span><span class="sxs-lookup"><span data-stu-id="cde37-114">This command sets the source location and publish location for **myInternalSource** to the specified URIs.</span></span>

## <span data-ttu-id="cde37-115">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="cde37-115">PARAMETERS</span></span>

### <span data-ttu-id="cde37-116">-Credential</span><span class="sxs-lookup"><span data-stu-id="cde37-116">-Credential</span></span>

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

### <span data-ttu-id="cde37-117">-InstallationPolicy</span><span class="sxs-lookup"><span data-stu-id="cde37-117">-InstallationPolicy</span></span>

<span data-ttu-id="cde37-118">Anger installations principen.</span><span class="sxs-lookup"><span data-stu-id="cde37-118">Specifies the installation policy.</span></span> <span data-ttu-id="cde37-119">Giltiga värden är: **betrodda**, **ej betrodda**.</span><span class="sxs-lookup"><span data-stu-id="cde37-119">Valid values are: **Trusted**, **Untrusted**.</span></span>

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

### <span data-ttu-id="cde37-120">-Name</span><span class="sxs-lookup"><span data-stu-id="cde37-120">-Name</span></span>

<span data-ttu-id="cde37-121">Anger namnet på lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="cde37-121">Specifies the name of the repository.</span></span>

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

### <span data-ttu-id="cde37-122">-PackageManagementProvider</span><span class="sxs-lookup"><span data-stu-id="cde37-122">-PackageManagementProvider</span></span>

<span data-ttu-id="cde37-123">Anger paket hanterings leverantören.</span><span class="sxs-lookup"><span data-stu-id="cde37-123">Specifies the package management provider.</span></span>

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

### <span data-ttu-id="cde37-124">-Proxy</span><span class="sxs-lookup"><span data-stu-id="cde37-124">-Proxy</span></span>

<span data-ttu-id="cde37-125">Anger en proxyserver för begäran, i stället för att ansluta direkt till Internet resursen.</span><span class="sxs-lookup"><span data-stu-id="cde37-125">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="cde37-126">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="cde37-126">-ProxyCredential</span></span>

<span data-ttu-id="cde37-127">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="cde37-127">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="cde37-128">-PublishLocation</span><span class="sxs-lookup"><span data-stu-id="cde37-128">-PublishLocation</span></span>

<span data-ttu-id="cde37-129">Anger URI för publicerings platsen.</span><span class="sxs-lookup"><span data-stu-id="cde37-129">Specifies the URI of the publish location.</span></span> <span data-ttu-id="cde37-130">För NuGet-baserade databaser liknar publicerings platsen till exempel `https://someNuGetUrl.com/api/v2/Packages` .</span><span class="sxs-lookup"><span data-stu-id="cde37-130">For example, for NuGet-based repositories, the publish location is similar to `https://someNuGetUrl.com/api/v2/Packages`.</span></span>

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

### <span data-ttu-id="cde37-131">-ScriptPublishLocation</span><span class="sxs-lookup"><span data-stu-id="cde37-131">-ScriptPublishLocation</span></span>

<span data-ttu-id="cde37-132">Anger skriptets publicerings plats.</span><span class="sxs-lookup"><span data-stu-id="cde37-132">Specifies the script publish location.</span></span>

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

### <span data-ttu-id="cde37-133">-ScriptSourceLocation</span><span class="sxs-lookup"><span data-stu-id="cde37-133">-ScriptSourceLocation</span></span>

<span data-ttu-id="cde37-134">Anger sökvägen till skript källan.</span><span class="sxs-lookup"><span data-stu-id="cde37-134">Specifies the script source location.</span></span>

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

### <span data-ttu-id="cde37-135">– SourceLocation</span><span class="sxs-lookup"><span data-stu-id="cde37-135">-SourceLocation</span></span>

<span data-ttu-id="cde37-136">Anger URI för identifiering och installation av moduler från den här lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="cde37-136">Specifies the URI for discovering and installing modules from this repository.</span></span> <span data-ttu-id="cde37-137">För NuGet-baserade databaser liknar till exempel käll platsen `https://someNuGetUrl.com/api/v2` .</span><span class="sxs-lookup"><span data-stu-id="cde37-137">For example, for NuGet-based repositories, the source location is similar to `https://someNuGetUrl.com/api/v2`.</span></span>

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

### <span data-ttu-id="cde37-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="cde37-138">CommonParameters</span></span>

<span data-ttu-id="cde37-139">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="cde37-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="cde37-140">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="cde37-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="cde37-141">INDATA</span><span class="sxs-lookup"><span data-stu-id="cde37-141">INPUTS</span></span>

### <span data-ttu-id="cde37-142">System. String</span><span class="sxs-lookup"><span data-stu-id="cde37-142">System.String</span></span>

### <span data-ttu-id="cde37-143">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="cde37-143">System.Management.Automation.PSCredential</span></span>

### <span data-ttu-id="cde37-144">System. URI</span><span class="sxs-lookup"><span data-stu-id="cde37-144">System.Uri</span></span>

## <span data-ttu-id="cde37-145">UTDATA</span><span class="sxs-lookup"><span data-stu-id="cde37-145">OUTPUTS</span></span>

### <span data-ttu-id="cde37-146">System. Object</span><span class="sxs-lookup"><span data-stu-id="cde37-146">System.Object</span></span>

## <span data-ttu-id="cde37-147">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="cde37-147">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cde37-148">Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1.</span><span class="sxs-lookup"><span data-stu-id="cde37-148">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="cde37-149">Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="cde37-149">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="cde37-150">Använd följande kommando för att se till att du använder TLS 1,2:</span><span class="sxs-lookup"><span data-stu-id="cde37-150">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="cde37-151">Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="cde37-151">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="cde37-152">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="cde37-152">RELATED LINKS</span></span>

[<span data-ttu-id="cde37-153">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="cde37-153">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="cde37-154">Registrera – PSRepository</span><span class="sxs-lookup"><span data-stu-id="cde37-154">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="cde37-155">Avregistrera-PSRepository</span><span class="sxs-lookup"><span data-stu-id="cde37-155">Unregister-PSRepository</span></span>](Unregister-PSRepository.md)
