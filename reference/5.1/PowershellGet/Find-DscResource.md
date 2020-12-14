---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/04/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-dscresource?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-DscResource
ms.openlocfilehash: 39896c4f48d6cd8809d4a680e776d36deb65b0d8
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889869"
---
# <span data-ttu-id="7e7e6-103">Find-DscResource</span><span class="sxs-lookup"><span data-stu-id="7e7e6-103">Find-DscResource</span></span>

## <span data-ttu-id="7e7e6-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="7e7e6-104">SYNOPSIS</span></span>
<span data-ttu-id="7e7e6-105">Söker efter Desired State Configuration (DSC)-resurser.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-105">Finds Desired State Configuration (DSC) resources.</span></span>

## <span data-ttu-id="7e7e6-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7e7e6-106">SYNTAX</span></span>

### <span data-ttu-id="7e7e6-107">Alla</span><span class="sxs-lookup"><span data-stu-id="7e7e6-107">All</span></span>

```
Find-DscResource [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease]
 [-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Repository <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="7e7e6-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="7e7e6-108">DESCRIPTION</span></span>

<span data-ttu-id="7e7e6-109">`Find-DscResource`Cmdleten söker igenom registrerade databaser för att hitta DSC-resurser som ingår i moduler.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-109">The `Find-DscResource` cmdlet searches registered repositories to find DSC resources contained in modules.</span></span> <span data-ttu-id="7e7e6-110">Som standard `Find-DscResource` genomsöks alla registrerade databaser.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-110">By default `Find-DscResource` searches all registered repositories.</span></span>

<span data-ttu-id="7e7e6-111">`Find-DscResource`Ett **PSGetDscResourceInfo** -objekt returneras för varje modul som hittas av.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-111">For each module found by `Find-DscResource`, a **PSGetDscResourceInfo** object is returned.</span></span>
<span data-ttu-id="7e7e6-112">**PSGetDscResourceInfo** -objekt kan skickas ned pipelinen till `Install-Module` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-112">**PSGetDscResourceInfo** objects can be sent down the pipeline to the `Install-Module` cmdlet.</span></span>
<span data-ttu-id="7e7e6-113">`Install-Module` installerar modulen.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-113">`Install-Module` installs the module.</span></span>

## <span data-ttu-id="7e7e6-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="7e7e6-114">EXAMPLES</span></span>

### <span data-ttu-id="7e7e6-115">Exempel 1: hitta alla DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="7e7e6-115">Example 1: Find all DSC resources</span></span>

<span data-ttu-id="7e7e6-116">`Find-DscResource` Returnerar DSC-resurser från registrerade databaser.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-116">`Find-DscResource` returns DSC resources from registered repositories.</span></span> <span data-ttu-id="7e7e6-117">Använd parametern **lagrings plats** om du vill söka i en speciell lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-117">To search a specific repository, use the **Repository** parameter.</span></span>

```powershell
Find-DscResource
```

```Output
Name                           Version    ModuleName                     Repository
----                           -------    ----------                     ----------
Carbon_Privilege               2.8.1      Carbon                         PSGallery
Carbon_ScheduledTask           2.8.1      Carbon                         PSGallery
Carbon_Service                 2.8.1      Carbon                         PSGallery
PackageManagement              1.4        PackageManagement              PSGallery
PackageManagementSource        1.4        PackageManagement              PSGallery
PSModule                       2.1.4      PowerShellGet                  PSGallery
PSRepository                   2.1.4      PowerShellGet                  PSGallery
xArchive                       8.7.0.0    xPSDesiredStateConfiguration   PSGallery
xDSCWebService                 8.7.0.0    xPSDesiredStateConfiguration   PSGallery
xEnvironment                   8.7.0.0    xPSDesiredStateConfiguration   PSGallery
```

### <span data-ttu-id="7e7e6-118">Exempel 2: hitta en DSC-resurs efter namn</span><span class="sxs-lookup"><span data-stu-id="7e7e6-118">Example 2: Find a DSC resource by name</span></span>

<span data-ttu-id="7e7e6-119">`Find-DscResource` söker efter DSC-resurser efter namn.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-119">`Find-DscResource` locates DSC resources by name.</span></span> <span data-ttu-id="7e7e6-120">Använd kommatecken för att avgränsa en matris med resurs namn.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-120">Use commas to separate an array of resource names.</span></span>

```powershell
Find-DscResource -Name xWebsite, xWebApplication, xWebSiteDefaults
```

```Output
Name               Version    ModuleName            Repository
----               -------    ----------            ----------
xWebApplication    2.6.0.0    xWebAdministration    PSGallery
xWebsite           2.6.0.0    xWebAdministration    PSGallery
xWebSiteDefaults   2.6.0.0    xWebAdministration    PSGallery
```

<span data-ttu-id="7e7e6-121">`Find-DscResource` använder parametern **Name** för att hitta den angivna matrisen med DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-121">`Find-DscResource` uses the **Name** parameter to find the specified array of DSC resources.</span></span>

### <span data-ttu-id="7e7e6-122">Exempel 3: hitta en DSC-resurs och installera den</span><span class="sxs-lookup"><span data-stu-id="7e7e6-122">Example 3: Find a DSC resource and install it</span></span>

<span data-ttu-id="7e7e6-123">`Find-DscResource` hittar en DSC-resurs och skickar objektet nedåt till den pipelines som ska installeras.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-123">`Find-DscResource` locates a DSC resource and sends the object down the pipeline to be installed.</span></span>
<span data-ttu-id="7e7e6-124">Använd `Get-InstalledModule` för att visa resultaten efter installationen.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-124">After the installation, use `Get-InstalledModule` to view the results.</span></span>

<span data-ttu-id="7e7e6-125">Flera resurser från samma modul kan skickas ned pipelinen till `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="7e7e6-125">Multiple resources from the same module can be sent down the pipeline to the `Install-Module`.</span></span>
<span data-ttu-id="7e7e6-126">`Install-Module` försöker bara installera modulen en gång.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-126">`Install-Module` attempts to only install the module once.</span></span>

```powershell
Find-DscResource -Name xWebsite | Install-Module
```

<span data-ttu-id="7e7e6-127">`Find-DscResource` använder parametern **Name** för att hitta resursen med namnet **xWebsite**.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-127">`Find-DscResource` uses the **Name** parameter to find the resource named **xWebsite**.</span></span> <span data-ttu-id="7e7e6-128">Objektet skickas ned pipelinen till `Install-Module` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-128">The object is sent down the pipeline to the `Install-Module` cmdlet.</span></span> <span data-ttu-id="7e7e6-129">`Install-Module` installerar **xWebAdministration** -modulen för resursen.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-129">`Install-Module` installs the **xWebAdministration** module for the resource.</span></span>

### <span data-ttu-id="7e7e6-130">Exempel 4: hitta alla DSC-resurser i en modul</span><span class="sxs-lookup"><span data-stu-id="7e7e6-130">Example 4: Find all DSC resources in a module</span></span>

<span data-ttu-id="7e7e6-131">`Find-DscResource` hittar alla DSC-resurser som ingår i en angiven modul.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-131">`Find-DscResource` finds all the DSC resources contained in a specified module.</span></span> <span data-ttu-id="7e7e6-132">Som standard visas den aktuella versionen.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-132">By default, the current version is displayed.</span></span> <span data-ttu-id="7e7e6-133">Om du vill visa andra versioner använder du parametrarna **AllVersions** eller **RequiredVersions** .</span><span class="sxs-lookup"><span data-stu-id="7e7e6-133">To display other versions, use the **AllVersions** or **RequiredVersions** parameters.</span></span>

```powershell
Find-DscResource -ModuleName xWebAdministration
```

```Output
Name                                Version    ModuleName              Repository
----                                -------    ----------              ----------
WebApplicationHandler               2.6.0.0    xWebAdministration      PSGallery
xIisFeatureDelegation               2.6.0.0    xWebAdministration      PSGallery
xIisHandler                         2.6.0.0    xWebAdministration      PSGallery
xIisLogging                         2.6.0.0    xWebAdministration      PSGallery
```

<span data-ttu-id="7e7e6-134">`Find-DscResource` använder **Modulnamn** -parametern för att ange **XWEBADMINISTRATION** och hitta DSC-resurserna som finns i modulen.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-134">`Find-DscResource` uses the **ModuleName** parameter to specify the **xWebAdministration** and find the DSC resources contained in the module.</span></span> <span data-ttu-id="7e7e6-135">Den aktuella versionen av varje resurs visas.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-135">The current version of each resource is displayed.</span></span>

### <span data-ttu-id="7e7e6-136">Exempel 5: hitta en DSC-resurs efter tagg och nödvändig version</span><span class="sxs-lookup"><span data-stu-id="7e7e6-136">Example 5: Find a DSC resource by tag and required version</span></span>

<span data-ttu-id="7e7e6-137">DSC-resurser kan hittas med parametrarna **tag** och **RequiredVersion**.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-137">DSC resources can be located using the parameters **Tag** and **RequiredVersion**.</span></span> <span data-ttu-id="7e7e6-138">**Tagg** visar den aktuella versionen av varje resurs som innehåller den angivna taggen i lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-138">**Tag** displays the current version of every resource that contains the specified tag in the repository.</span></span>
<span data-ttu-id="7e7e6-139">**RequiredVersion** kräver att parametern **Modulnamn** och parametern **Name** är valfri.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-139">**RequiredVersion** needs the **ModuleName** parameter and the **Name** parameter is optional.</span></span> <span data-ttu-id="7e7e6-140">**Namn** -och **Modulnamn** -parametrarna begränsar utdata.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-140">The **Name** and **ModuleName** parameters limit the output.</span></span> <span data-ttu-id="7e7e6-141">Använd parametern **AllVersions** för att visa tillgängliga versioner av en DSC-resurs.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-141">Use the **AllVersions** parameter to display a DSC resource's available versions.</span></span>

```powershell
Find-DscResource -ModuleName xWebAdministration -Tag DSC -RequiredVersion 1.20
```

```output
Name                    Version    ModuleName             Repository
----                    -------    ----------             ----------
xIisFeatureDelegation   1.20.0.0   xWebAdministration     PSGallery
xIisHandler             1.20.0.0   xWebAdministration     PSGallery
xIisLogging             1.20.0.0   xWebAdministration     PSGallery
xIisMimeTypeMapping     1.20.0.0   xWebAdministration     PSGallery
```

### <span data-ttu-id="7e7e6-142">Exempel 6: hitta en resurs med hjälp av ett filter</span><span class="sxs-lookup"><span data-stu-id="7e7e6-142">Example 6: Find a resource by using a filter</span></span>

<span data-ttu-id="7e7e6-143">`Find-DscResource` söker efter alla resurser och använder **filter** parametern för att ange resultaten efter **domän**.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-143">`Find-DscResource` finds all resources and uses the **Filter** parameter to specify the results by **Domain**.</span></span> <span data-ttu-id="7e7e6-144">**Filter** parametern hittar filtervärdet i objektets beskrivning eller modulens namn.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-144">The **Filter** parameter finds the filter value in the object's description or module name.</span></span> <span data-ttu-id="7e7e6-145">Använd `Select-Object` cmdleten för att visa egenskaperna för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-145">Use the `Select-Object` cmdlet to view an object's properties.</span></span>

```powershell
Find-DscResource -Filter Domain
```

```output
Name                    Version    ModuleName                 Repository
----                    -------    ----------                 ---------
xComputer               4.1.0.0    xComputerManagement        PSGallery
Computer                6.4.0.0    ComputerManagementDsc      PSGallery
xDSCDomainjoin          1.1        xDSCDomainjoin             PSGallery
xDisk                   1.0        xDisk                      PSGallery
xDSCFirewall            1.6.21     xDSCFirewall               PSGallery
dmAwsTagInstance        1.0.1      domainAwsDSCResources      PSGallery
```

## <span data-ttu-id="7e7e6-146">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="7e7e6-146">PARAMETERS</span></span>

### <span data-ttu-id="7e7e6-147">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="7e7e6-147">-AllowPrerelease</span></span>

<span data-ttu-id="7e7e6-148">Innehåller resurser som marker ATS som en för hands version i resultaten.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-148">Includes resources marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="7e7e6-149">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="7e7e6-149">-AllVersions</span></span>

<span data-ttu-id="7e7e6-150">Parametern **AllVersions** visar var och en av en DSC-resurs tillgängliga versioner.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-150">The **AllVersions** parameter displays each of a DSC resource's available versions.</span></span> <span data-ttu-id="7e7e6-151">Du kan inte använda parametern **AllVersions** med parametrarna **MinimumVersion**, **MaximumVersion** eller **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="7e7e6-151">You can't use the **AllVersions** parameter with the **MinimumVersion**, **MaximumVersion**, or **RequiredVersion** parameters.</span></span>

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

### <span data-ttu-id="7e7e6-152">-Filter</span><span class="sxs-lookup"><span data-stu-id="7e7e6-152">-Filter</span></span>

<span data-ttu-id="7e7e6-153">Söker efter resurser baserat på **PackageManagement** -providerns söksyntax.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-153">Finds resources based on the **PackageManagement** provider's search syntax.</span></span> <span data-ttu-id="7e7e6-154">Ange till exempel ord att söka efter i egenskaperna **Modulnamn** och **Description** .</span><span class="sxs-lookup"><span data-stu-id="7e7e6-154">For example, specify words to search for within the **ModuleName** and **Description** properties.</span></span>

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

### <span data-ttu-id="7e7e6-155">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="7e7e6-155">-MaximumVersion</span></span>

<span data-ttu-id="7e7e6-156">Anger den maximala resurs version som ska tas med i resultaten.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-156">Specifies the maximum version of the resource to include in results.</span></span> <span data-ttu-id="7e7e6-157">Parametrarna **MaximumVersion** och **RequiredVersion** kan inte användas i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-157">The **MaximumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="7e7e6-158">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="7e7e6-158">-MinimumVersion</span></span>

<span data-ttu-id="7e7e6-159">Anger den lägsta resurs version som ska tas med i resultaten.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-159">Specifies the minimum version of the resource to include in results.</span></span> <span data-ttu-id="7e7e6-160">Parametrarna **MinimumVersion** och **RequiredVersion** kan inte användas i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-160">The **MinimumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="7e7e6-161">-Modulnamn</span><span class="sxs-lookup"><span data-stu-id="7e7e6-161">-ModuleName</span></span>

<span data-ttu-id="7e7e6-162">Anger en modul som innehåller DSC-resursen.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-162">Specifies a module that contains the DSC resource.</span></span>

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

### <span data-ttu-id="7e7e6-163">-Name</span><span class="sxs-lookup"><span data-stu-id="7e7e6-163">-Name</span></span>

<span data-ttu-id="7e7e6-164">Anger namnet på en resurs.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-164">Specifies the name of a resource.</span></span> <span data-ttu-id="7e7e6-165">Standardvärdet är alla resurser.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-165">The default is all resources.</span></span> <span data-ttu-id="7e7e6-166">Använd kommatecken för att avgränsa en matris med resurs namn.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-166">Use commas to separate an array of resource names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7e7e6-167">-Proxy</span><span class="sxs-lookup"><span data-stu-id="7e7e6-167">-Proxy</span></span>

<span data-ttu-id="7e7e6-168">Anger en proxyserver för begäran, i stället för en direkt anslutning till Internet resursen.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-168">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="7e7e6-169">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="7e7e6-169">-ProxyCredential</span></span>

<span data-ttu-id="7e7e6-170">Anger ett användar konto med behörighet att använda den proxyserver som anges i parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="7e7e6-170">Specifies a user account with permission to use the proxy server specified in the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="7e7e6-171">– Databas</span><span class="sxs-lookup"><span data-stu-id="7e7e6-171">-Repository</span></span>

<span data-ttu-id="7e7e6-172">Anger en lagrings plats för att söka efter resurser.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-172">Specifies a repository to search for resources.</span></span> <span data-ttu-id="7e7e6-173">Använd kommatecken för att avgränsa en matris med lagrings namn.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-173">Use commas to separate an array of repository names.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7e7e6-174">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="7e7e6-174">-RequiredVersion</span></span>

<span data-ttu-id="7e7e6-175">Anger modulens exakta versions nummer som ska ingå i resultaten.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-175">Specifies the module's exact version number to include in the results.</span></span> <span data-ttu-id="7e7e6-176">Parametrarna **RequiredVersion** och **MinimumVersion** kan inte användas i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-176">The **RequiredVersion** and the **MinimumVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="7e7e6-177">-Tagga</span><span class="sxs-lookup"><span data-stu-id="7e7e6-177">-Tag</span></span>

<span data-ttu-id="7e7e6-178">Anger taggar som kategoriserar moduler i en lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-178">Specifies tags that categorize modules in a repository.</span></span> <span data-ttu-id="7e7e6-179">Använd kommatecken för att avgränsa en matris med taggar.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-179">Use commas to separate an array of tags.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7e7e6-180">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7e7e6-180">CommonParameters</span></span>

<span data-ttu-id="7e7e6-181">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-181">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7e7e6-182">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="7e7e6-182">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7e7e6-183">INDATA</span><span class="sxs-lookup"><span data-stu-id="7e7e6-183">INPUTS</span></span>

## <span data-ttu-id="7e7e6-184">UTDATA</span><span class="sxs-lookup"><span data-stu-id="7e7e6-184">OUTPUTS</span></span>

### <span data-ttu-id="7e7e6-185">PSGetDscResourceInfo</span><span class="sxs-lookup"><span data-stu-id="7e7e6-185">PSGetDscResourceInfo</span></span>

<span data-ttu-id="7e7e6-186">`Find-DscResource` Returnerar ett **PSGetDscResourceInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-186">`Find-DscResource` returns a **PSGetDscResourceInfo** object.</span></span>

## <span data-ttu-id="7e7e6-187">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="7e7e6-187">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7e7e6-188">Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-188">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="7e7e6-189">Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-189">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="7e7e6-190">Använd följande kommando för att se till att du använder TLS 1,2:</span><span class="sxs-lookup"><span data-stu-id="7e7e6-190">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="7e7e6-191">Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="7e7e6-191">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="7e7e6-192">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="7e7e6-192">RELATED LINKS</span></span>

[<span data-ttu-id="7e7e6-193">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="7e7e6-193">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="7e7e6-194">Installera-modul</span><span class="sxs-lookup"><span data-stu-id="7e7e6-194">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="7e7e6-195">Registrera – PSRepository</span><span class="sxs-lookup"><span data-stu-id="7e7e6-195">Register-PSRepository</span></span>](Register-PSRepository.md)

[<span data-ttu-id="7e7e6-196">Select-Object</span><span class="sxs-lookup"><span data-stu-id="7e7e6-196">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="7e7e6-197">Avinstallera-modul</span><span class="sxs-lookup"><span data-stu-id="7e7e6-197">Uninstall-Module</span></span>](Uninstall-Module.md)
