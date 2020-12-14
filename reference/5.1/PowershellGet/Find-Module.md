---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 03/11/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-module?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Module
ms.openlocfilehash: b30e233eb9c4f4f9191ac6470f2821536dda6dc3
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889835"
---
# <span data-ttu-id="2f5b2-103">Find-Module</span><span class="sxs-lookup"><span data-stu-id="2f5b2-103">Find-Module</span></span>

## <span data-ttu-id="2f5b2-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="2f5b2-104">SYNOPSIS</span></span>
<span data-ttu-id="2f5b2-105">Söker efter moduler i en lagrings plats som matchar de angivna kriterierna.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-105">Finds modules in a repository that match specified criteria.</span></span>

## <span data-ttu-id="2f5b2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2f5b2-106">SYNTAX</span></span>

### <span data-ttu-id="2f5b2-107">Alla</span><span class="sxs-lookup"><span data-stu-id="2f5b2-107">All</span></span>

```
Find-Module [[-Name] <string[]>] [-MinimumVersion <string>] [-MaximumVersion <string>]
 [-RequiredVersion <string>] [-AllVersions] [-IncludeDependencies] [-Filter <string>]
 [-Tag <string[]>] [-Includes <string[]>] [-DscResource <string[]>] [-RoleCapability <string[]>]
 [-Command <string[]>] [-Proxy <uri>] [-ProxyCredential <pscredential>] [-Repository <string[]>]
 [-Credential <pscredential>] [-AllowPrerelease] [<CommonParameters>]
```

## <span data-ttu-id="2f5b2-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="2f5b2-108">DESCRIPTION</span></span>

<span data-ttu-id="2f5b2-109">`Find-Module`Cmdleten söker efter moduler i en lagrings plats som matchar de angivna kriterierna.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-109">The `Find-Module` cmdlet finds modules in a repository that match the specified criteria.</span></span>
<span data-ttu-id="2f5b2-110">`Find-Module` Returnerar ett **PSRepositoryItemInfo** -objekt för varje modul som hittas.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-110">`Find-Module` returns a **PSRepositoryItemInfo** object for each module it finds.</span></span> <span data-ttu-id="2f5b2-111">Objekten kan skickas ned pipelinen till-cmdlet: ar, till exempel `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="2f5b2-111">The objects can be sent down the pipeline to cmdlets such as `Install-Module`.</span></span>

<span data-ttu-id="2f5b2-112">Första gången du `Find-Module` försöker använda en lagrings plats kan du uppmanas att installera uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-112">The first time `Find-Module` attempts to use a repository, you might be prompted to install updates.</span></span>
<span data-ttu-id="2f5b2-113">Om lagrings platsen inte har registrerats med `Register-PSRepository` cmdleten returneras ett fel.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-113">If the repository source is not registered with `Register-PSRepository` cmdlet, an error is returned.</span></span>

<span data-ttu-id="2f5b2-114">`Find-Module` Returnerar den nyaste versionen av en modul om inga parametrar används som begränsar versionen.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-114">`Find-Module` returns the newest version of a module if no parameters are used that limit the version.</span></span> <span data-ttu-id="2f5b2-115">Om du vill hämta en lista över en moduls versioner använder du parametern **AllVersions**.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-115">To get a repository's list of a module's versions, use the parameter **AllVersions**.</span></span>

<span data-ttu-id="2f5b2-116">Om parametern **MinimumVersion** anges `Find-Module` returnerar modulens version som är lika med eller större än minimivärdet.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-116">If the **MinimumVersion** parameter is specified, `Find-Module` returns the module's version that is equal to or greater than the minimum.</span></span> <span data-ttu-id="2f5b2-117">Om det finns en nyare version som är tillgänglig i lagrings platsen returneras den nya versionen.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-117">If there is a newer version available in the repository, the newer version is returned.</span></span>

<span data-ttu-id="2f5b2-118">Om parametern **MaximumVersion** anges `Find-Module` returnerar den nyaste versionen av modulen som inte överskrider den angivna versionen.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-118">If the **MaximumVersion** parameter is specified, `Find-Module` returns the newest version of the module that does not exceed the version specified.</span></span>

<span data-ttu-id="2f5b2-119">Om parametern **RequiredVersion** anges `Find-Module` returnerar endast den version som är en exakt matchning till den angivna versionen.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-119">If the **RequiredVersion** parameter is specified, `Find-Module` only returns the module version that is an exact match to the specified version.</span></span> <span data-ttu-id="2f5b2-120">`Find-Module` söker igenom alla tillgängliga moduler eftersom namn konflikter mellan källor kan uppstå.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-120">`Find-Module` searches through all available modules, because name conflicts between sources can occur.</span></span>

<span data-ttu-id="2f5b2-121">I följande exempel används [PowerShell-galleriet](https://www.powershellgallery.com/) som den enda registrerade lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-121">The following examples use the [PowerShell Gallery](https://www.powershellgallery.com/) as the only registered repository.</span></span> <span data-ttu-id="2f5b2-122">`Get-PSRepository` visar de registrerade databaserna.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-122">`Get-PSRepository` displays the registered repositories.</span></span> <span data-ttu-id="2f5b2-123">Om du har flera registrerade databaser använder du `-Repository` parametern för att ange namnet på lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-123">If you have multiple registered repositories, use the `-Repository` parameter to specify the repository's name.</span></span>

## <span data-ttu-id="2f5b2-124">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="2f5b2-124">EXAMPLES</span></span>

### <span data-ttu-id="2f5b2-125">Exempel 1: hitta en modul efter namn</span><span class="sxs-lookup"><span data-stu-id="2f5b2-125">Example 1: Find a module by name</span></span>

<span data-ttu-id="2f5b2-126">I det här exemplet hittas en modul i standard lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-126">This example finds a module in the default repository.</span></span>

```powershell
Find-Module -Name PowerShellGet
```

```Output
Version   Name              Repository           Description
-------   ----              ----------           -----------
2.1.0     PowerShellGet     PSGallery            PowerShell module with commands for discovering...
```

<span data-ttu-id="2f5b2-127">`Find-Module`Cmdleten använder **Name** -parametern för att ange **PowerShellGet** -modulen.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-127">The `Find-Module` cmdlet uses the **Name** parameter to specify the **PowerShellGet** module.</span></span>

### <span data-ttu-id="2f5b2-128">Exempel 2: hitta moduler med liknande namn</span><span class="sxs-lookup"><span data-stu-id="2f5b2-128">Example 2: Find modules with similar names</span></span>

<span data-ttu-id="2f5b2-129">I det här exemplet används jokertecknet asterisk ( `*` ) för att hitta moduler med liknande namn.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-129">This example uses the asterisk (`*`) wildcard to find modules with similar names.</span></span>

```powershell
Find-Module -Name PowerShell*
```

```Output
Version   Name                            Repository    Description
-------   ----                            ----------    -----------
0.4.0     powershell-yaml                 PSGallery     Powershell module for serializing and...
2.1.0     PowerShellGet                   PSGallery     PowerShell module with commands for...
1.9       Powershell.Helper.Extension     PSGallery     # Powershell.Helper.Extension...
3.1       PowerShellHumanizer             PSGallery     PowerShell Humanizer wraps Humanizer...
4.0       PowerShellISEModule             PSGallery     a module that adds capability to the ISE
```

<span data-ttu-id="2f5b2-130">`Find-Module`Cmdleten använder **Name** -parametern med jokertecknet asterisk ( `*` ) för att hitta alla moduler som innehåller **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-130">The `Find-Module` cmdlet uses the **Name** parameter with the asterisk (`*`) wildcard to find all modules that contain **PowerShell**.</span></span>

### <span data-ttu-id="2f5b2-131">Exempel 3: hitta en modul efter lägsta version</span><span class="sxs-lookup"><span data-stu-id="2f5b2-131">Example 3: Find a module by minimum version</span></span>

<span data-ttu-id="2f5b2-132">Det här exemplet söker efter en moduls lägsta version.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-132">This example searches for a module's minimum version.</span></span> <span data-ttu-id="2f5b2-133">Om lagrings platsen innehåller en nyare version av modulen returneras den nya versionen.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-133">If the repository contains a newer version of the module, the newer version is returned.</span></span>

```powershell
Find-Module -Name PowerShellGet -MinimumVersion 1.6.5
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
2.1.0     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

<span data-ttu-id="2f5b2-134">`Find-Module`Cmdleten använder **Name** -parametern för att ange **PowerShellGet** -modulen.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-134">The `Find-Module` cmdlet uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="2f5b2-135">**MinimumVersion** anger version **1.6.5**.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-135">The **MinimumVersion** specifies version **1.6.5**.</span></span> <span data-ttu-id="2f5b2-136">`Find-Module` Returnerar PowerShellGet version **2.1.0** eftersom den överskrider den lägsta versionen och den mest aktuella versionen.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-136">`Find-Module` returns PowerShellGet version **2.1.0** because it exceeds the minimum version and is the most current version.</span></span>

### <span data-ttu-id="2f5b2-137">Exempel 4: hitta en modul efter en version</span><span class="sxs-lookup"><span data-stu-id="2f5b2-137">Example 4: Find a module by specific version</span></span>

<span data-ttu-id="2f5b2-138">Det här exemplet returnerar ett objekt som representerar en moduls aktuella version.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-138">This example returns an object that represents a module's specific version.</span></span> <span data-ttu-id="2f5b2-139">Om den angivna versionen inte hittas returneras ett fel.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-139">If the specified version is not found, an error is returned.</span></span>

```powershell
Find-Module -Name PowerShellGet -RequiredVersion 1.6.5
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
1.6.5     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

<span data-ttu-id="2f5b2-140">`Find-Module`Cmdleten använder **Name** -parametern för att ange **PowerShellGet** -modulen.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-140">The `Find-Module` cmdlet uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="2f5b2-141">Parametern **RequiredVersion** anger version **1.6.5**.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-141">The **RequiredVersion** parameter specifies version **1.6.5**.</span></span>

### <span data-ttu-id="2f5b2-142">Exempel 5: hitta en modul i ett särskilt lager</span><span class="sxs-lookup"><span data-stu-id="2f5b2-142">Example 5: Find a module in a specific repository</span></span>

<span data-ttu-id="2f5b2-143">I det här exemplet används parametern **lagrings plats** för att hitta en modul i en angiven lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-143">This example uses the **Repository** parameter to find a module in a specific repository.</span></span>

```powershell
Find-Module -Name PowerShellGet -Repository PSGallery
```

```Output
Version   Name             Repository     Description
-------   ----             ----------     -----------
2.1.0     PowerShellGet    PSGallery      PowerShell module with commands for discovering...
```

<span data-ttu-id="2f5b2-144">`Find-Module`Cmdleten använder **Name** -parametern för att ange **PowerShellGet** -modulen.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-144">The `Find-Module` cmdlet uses the **Name** parameter to specify the **PowerShellGet** module.</span></span> <span data-ttu-id="2f5b2-145">Parametern för **lagrings platsen** anger att söka i **PSGallery** -lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-145">The **Repository** parameter specifies to search the **PSGallery** repository.</span></span>

### <span data-ttu-id="2f5b2-146">Exempel 6: hitta en modul i flera databaser</span><span class="sxs-lookup"><span data-stu-id="2f5b2-146">Example 6: Find a module in multiple repositories</span></span>

<span data-ttu-id="2f5b2-147">I det här exemplet används `Register-PSRepository` för att ange en lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-147">This example uses the `Register-PSRepository` to specify a repository.</span></span> <span data-ttu-id="2f5b2-148">`Find-Module` använder lagrings platsen för att söka efter en modul.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-148">`Find-Module` uses the repository to search for a module.</span></span>

```powershell
Register-PSRepository -Name MySource -SourceLocation https://www.myget.org/F/powershellgetdemo/
Find-Module -Name Contoso* -Repository PSGallery, MySource
```

```Output
Repository    Version   Name             Description
----------    -------   ----             -----------
PSGallery     2.0.0.0   ContosoServer    Cmdlets and DSC resources for managing Contoso Server...
MySource      1.2.0.0   ContosoClient    Cmdlets and DSC resources for managing Contoso Client...
```

<span data-ttu-id="2f5b2-149">`Register-PSRepository`Cmdleten registrerar en ny lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-149">The `Register-PSRepository` cmdlet registers a new repository.</span></span> <span data-ttu-id="2f5b2-150">Parametern **Name** tilldelar namnet **källa**.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-150">The **Name** parameter assigns the name **MySource**.</span></span> <span data-ttu-id="2f5b2-151">Parametern **SourceLocation** anger lagrings platsens adress.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-151">The **SourceLocation** parameter specifies the repository's address.</span></span>

<span data-ttu-id="2f5b2-152">`Find-Module`Cmdleten använder **Name** -parametern med jokertecknet asterisk ( `*` ) för att ange **contoso** -modulen.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-152">The `Find-Module` cmdlet uses the **Name** parameter with the asterisk (`*`) wildcard to specify the **Contoso** module.</span></span> <span data-ttu-id="2f5b2-153">Parametern **lagrings plats** anger för att söka i två databaser, **PSGallery** och **källa**.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-153">The **Repository** parameter specifies to search two repositories, **PSGallery** and **MySource**.</span></span>

### <span data-ttu-id="2f5b2-154">Exempel 7: hitta en modul som innehåller en DSC-resurs</span><span class="sxs-lookup"><span data-stu-id="2f5b2-154">Example 7: Find a module that contains a DSC resource</span></span>

<span data-ttu-id="2f5b2-155">Det här kommandot returnerar moduler som innehåller DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-155">This command returns modules that contain DSC resources.</span></span> <span data-ttu-id="2f5b2-156">Parametern **includes** har fyra fördefinierade funktioner som används för att söka i lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-156">The **Includes** parameter has four predefined functionalities that are used to search the repository.</span></span> <span data-ttu-id="2f5b2-157">Använd Tabb-Complete för att visa de fyra funktionerna som stöds av parametern **includes** .</span><span class="sxs-lookup"><span data-stu-id="2f5b2-157">Use tab-complete to display the four functionalities supported by the **Includes** parameter.</span></span>

```powershell
Find-Module -Repository PSGallery -Includes DscResource
```

```Output
Version     Name                            Repository    Description
-------     ----                            ----------    -----------
2.7.0       Carbon                          PSGallery     Carbon is a PowerShell module...
8.5.0.0     xPSDesiredStateConfiguration    PSGallery     The xPSDesiredStateConfiguration module...
1.3.1       PackageManagement               PSGallery     PackageManagement (a.k.a. OneGet) is...
2.7.0.0     xWindowsUpdate                  PSGallery     Module with DSC Resources...
3.2.0.0     xCertificate                    PSGallery     This module includes DSC resources...
3.1.0.0     xPowerShellExecutionPolicy      PSGallery     This DSC resource can change the user...
```

<span data-ttu-id="2f5b2-158">`Find-Module`Cmdlet: en använder parametern **lagrings plats** för att söka i lagrings platsen, **PSGallery**.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-158">The `Find-Module` cmdlet uses the **Repository** parameter to search the repository, **PSGallery**.</span></span>
<span data-ttu-id="2f5b2-159">Parametern **includes** anger **dscresource Keyword Supports**, som är en funktion som parametern kan söka efter i lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-159">The **Includes** parameter specifies **DscResource**, which is a functionality that the parameter can search for in the repository.</span></span>

### <span data-ttu-id="2f5b2-160">Exempel 8: hitta en modul med ett filter</span><span class="sxs-lookup"><span data-stu-id="2f5b2-160">Example 8: Find a module with a filter</span></span>

<span data-ttu-id="2f5b2-161">I det här exemplet används ett filter för att söka efter moduler.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-161">In this example, to find modules, a filter is used to search the repository.</span></span>

<span data-ttu-id="2f5b2-162">För en NuGet-baserad lagring söker **filter** parametern igenom igenom namnet, beskrivningen och taggarna för argumentet.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-162">For a NuGet-based repository, the **Filter** parameter searches through the name, description, and tags for the argument.</span></span>

```powershell
Find-Module -Filter AppDomain
```

```Output
Version    Name              Repository           Description
-------    ----              ----------           -----------
1.0.0.0  AppDomainConfig     PSGallery            Manipulate AppDomain configuration...
1.1.0    ClassExplorer       PSGallery            Quickly search the AppDomain for classes...
```

<span data-ttu-id="2f5b2-163">`Find-Module`Cmdleten använder **filter** parametern för att söka i lagrings platsen för **AppDomain**.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-163">The `Find-Module` cmdlet uses the **Filter** parameter to search the repository for **AppDomain**.</span></span>

## <span data-ttu-id="2f5b2-164">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="2f5b2-164">PARAMETERS</span></span>

### <span data-ttu-id="2f5b2-165">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="2f5b2-165">-AllowPrerelease</span></span>

<span data-ttu-id="2f5b2-166">Innehåller i de resultat moduler som marker ATS som en för hands version.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-166">Includes in the results modules marked as a pre-release.</span></span>

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

### <span data-ttu-id="2f5b2-167">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="2f5b2-167">-AllVersions</span></span>

<span data-ttu-id="2f5b2-168">Anger om du vill inkludera alla versioner av en modul i resultaten.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-168">Specifies to include all versions of a module in the results.</span></span> <span data-ttu-id="2f5b2-169">Du kan inte använda parametern **AllVersions** med parametrarna **MinimumVersion**, **MaximumVersion** eller **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="2f5b2-169">You cannot use the **AllVersions** parameter with the **MinimumVersion**, **MaximumVersion**, or **RequiredVersion** parameters.</span></span>

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

### <span data-ttu-id="2f5b2-170">-Kommando</span><span class="sxs-lookup"><span data-stu-id="2f5b2-170">-Command</span></span>

<span data-ttu-id="2f5b2-171">Anger en matris med kommandon som ska hittas i moduler.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-171">Specifies an array of commands to find in modules.</span></span> <span data-ttu-id="2f5b2-172">Ett kommando kan vara en funktion eller ett arbets flöde.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-172">A command can be a function or workflow.</span></span>

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

### <span data-ttu-id="2f5b2-173">-Credential</span><span class="sxs-lookup"><span data-stu-id="2f5b2-173">-Credential</span></span>

<span data-ttu-id="2f5b2-174">Anger ett användar konto som har behörighet att installera en modul för en angiven paket leverantör eller källa.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-174">Specifies a user account that has rights to install a module for a specified package provider or source.</span></span>

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

### <span data-ttu-id="2f5b2-175">– Dscresource Keyword Supports</span><span class="sxs-lookup"><span data-stu-id="2f5b2-175">-DscResource</span></span>

<span data-ttu-id="2f5b2-176">Anger namnet eller en del av namnet på moduler som innehåller DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-176">Specifies the name, or part of the name, of modules that contain DSC resources.</span></span> <span data-ttu-id="2f5b2-177">Per PowerShell-konventioner utför en **eller** -sökning när du anger flera argument.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-177">Per PowerShell conventions, performs an **OR** search when you provide multiple arguments.</span></span>

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

### <span data-ttu-id="2f5b2-178">-Filter</span><span class="sxs-lookup"><span data-stu-id="2f5b2-178">-Filter</span></span>

<span data-ttu-id="2f5b2-179">Anger ett filter baserat på **PackageManagement** -providerspecifika söksyntax.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-179">Specifies a filter based on the **PackageManagement** provider-specific search syntax.</span></span> <span data-ttu-id="2f5b2-180">För NuGet-moduler är den här parametern motsvarigheten till sökning med hjälp av Sök fältet på [PowerShell-galleriet](https://www.powershellgallery.com/) webbplats.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-180">For NuGet modules, this parameter is the equivalent of searching by using the Search bar on the [PowerShell Gallery](https://www.powershellgallery.com/) website.</span></span>

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

### <span data-ttu-id="2f5b2-181">-IncludeDependencies</span><span class="sxs-lookup"><span data-stu-id="2f5b2-181">-IncludeDependencies</span></span>

<span data-ttu-id="2f5b2-182">Anger att den här åtgärden inkluderar alla moduler som är beroende av den modul som anges i parametern **Name** .</span><span class="sxs-lookup"><span data-stu-id="2f5b2-182">Indicates that this operation includes all modules that are dependent upon the module specified in the **Name** parameter.</span></span>

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

### <span data-ttu-id="2f5b2-183">– Innehåller</span><span class="sxs-lookup"><span data-stu-id="2f5b2-183">-Includes</span></span>

<span data-ttu-id="2f5b2-184">Returnerar bara de moduler som innehåller vissa typer av PowerShell-funktioner.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-184">Returns only those modules that include specific kinds of PowerShell functionality.</span></span> <span data-ttu-id="2f5b2-185">Till exempel kanske du bara vill hitta moduler som innehåller **dscresource Keyword Supports**.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-185">For example, you might only want to find modules that include **DSCResource**.</span></span> <span data-ttu-id="2f5b2-186">De acceptabla värdena för den här parametern är följande:</span><span class="sxs-lookup"><span data-stu-id="2f5b2-186">The acceptable values for this parameter are as follows:</span></span>

- <span data-ttu-id="2f5b2-187">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2f5b2-187">Cmdlet</span></span>
- <span data-ttu-id="2f5b2-188">Dscresource Keyword Supports</span><span class="sxs-lookup"><span data-stu-id="2f5b2-188">DscResource</span></span>
- <span data-ttu-id="2f5b2-189">Funktion</span><span class="sxs-lookup"><span data-stu-id="2f5b2-189">Function</span></span>
- <span data-ttu-id="2f5b2-190">RoleCapability</span><span class="sxs-lookup"><span data-stu-id="2f5b2-190">RoleCapability</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:
Accepted values: DscResource, Cmdlet, Function, RoleCapability

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2f5b2-191">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="2f5b2-191">-MaximumVersion</span></span>

<span data-ttu-id="2f5b2-192">Anger den maximala eller senaste versionen av modulen som ska ingå i Sök resultaten.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-192">Specifies the maximum, or latest, version of the module to include in the search results.</span></span>
<span data-ttu-id="2f5b2-193">Det går inte att använda **MaximumVersion** och **RequiredVersion** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-193">**MaximumVersion** and **RequiredVersion** cannot be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2f5b2-194">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="2f5b2-194">-MinimumVersion</span></span>

<span data-ttu-id="2f5b2-195">Anger den lägsta version av modulen som ska tas med i resultaten.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-195">Specifies the minimum version of the module to include in results.</span></span> <span data-ttu-id="2f5b2-196">Det går inte att använda **MinimumVersion** och **RequiredVersion** i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-196">**MinimumVersion** and **RequiredVersion** cannot be used in the same command.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2f5b2-197">-Name</span><span class="sxs-lookup"><span data-stu-id="2f5b2-197">-Name</span></span>

<span data-ttu-id="2f5b2-198">Anger namnen på de moduler som ska sökas efter i lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-198">Specifies the names of modules to search for in the repository.</span></span> <span data-ttu-id="2f5b2-199">En kommaavgränsad lista med Modulnamn accepteras.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-199">A comma-separated list of module names is accepted.</span></span> <span data-ttu-id="2f5b2-200">Jokertecken accepteras.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-200">Wildcards are accepted.</span></span>

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

### <span data-ttu-id="2f5b2-201">-Proxy</span><span class="sxs-lookup"><span data-stu-id="2f5b2-201">-Proxy</span></span>

<span data-ttu-id="2f5b2-202">Anger en proxyserver för begäran, i stället för att ansluta direkt till Internet resursen.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-202">Specifies a proxy server for the request, rather than connecting directly to the Internet resource.</span></span>

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

### <span data-ttu-id="2f5b2-203">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="2f5b2-203">-ProxyCredential</span></span>

<span data-ttu-id="2f5b2-204">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="2f5b2-204">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="2f5b2-205">– Databas</span><span class="sxs-lookup"><span data-stu-id="2f5b2-205">-Repository</span></span>

<span data-ttu-id="2f5b2-206">Använd parametern **lagrings plats** för att ange vilken lagrings plats som ska sökas efter en modul.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-206">Use the **Repository** parameter to specify which repository to search for a module.</span></span> <span data-ttu-id="2f5b2-207">Används när flera databaser har registrerats.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-207">Used when multiple repositories are registered.</span></span> <span data-ttu-id="2f5b2-208">Accepterar en kommaavgränsad lista över databaser.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-208">Accepts a comma-separated list of repositories.</span></span> <span data-ttu-id="2f5b2-209">Använd om du vill registrera en lagrings plats `Register-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="2f5b2-209">To register a repository, use `Register-PSRepository`.</span></span> <span data-ttu-id="2f5b2-210">Använd om du vill visa registrerade databaser `Get-PSRepository` .</span><span class="sxs-lookup"><span data-stu-id="2f5b2-210">To display registered repositories, use `Get-PSRepository`.</span></span>

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

### <span data-ttu-id="2f5b2-211">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="2f5b2-211">-RequiredVersion</span></span>

<span data-ttu-id="2f5b2-212">Anger det exakta versions numret för den modul som ska tas med i resultaten.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-212">Specifies the exact version number of the module to include in the results.</span></span> <span data-ttu-id="2f5b2-213">**RequiredVersion** kan inte användas i samma kommando som **MinimumVersion** eller **MaximumVersion**.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-213">**RequiredVersion** cannot be used in the same command as **MinimumVersion** or **MaximumVersion**.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="2f5b2-214">-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="2f5b2-214">-RoleCapability</span></span>

<span data-ttu-id="2f5b2-215">Anger en matris med roll funktioner.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-215">Specifies an array of role capabilities.</span></span>

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

### <span data-ttu-id="2f5b2-216">-Tagga</span><span class="sxs-lookup"><span data-stu-id="2f5b2-216">-Tag</span></span>

<span data-ttu-id="2f5b2-217">Anger en matris med taggar.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-217">Specifies an array of tags.</span></span> <span data-ttu-id="2f5b2-218">Exempel taggar är **DesiredStateConfiguration**, **DSC**, **DSCResourceKit** eller **PSModule**.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-218">Example tags include **DesiredStateConfiguration**, **DSC**, **DSCResourceKit**, or **PSModule**.</span></span>

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

### <span data-ttu-id="2f5b2-219">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2f5b2-219">CommonParameters</span></span>

<span data-ttu-id="2f5b2-220">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-220">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2f5b2-221">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2f5b2-221">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2f5b2-222">INDATA</span><span class="sxs-lookup"><span data-stu-id="2f5b2-222">INPUTS</span></span>

## <span data-ttu-id="2f5b2-223">UTDATA</span><span class="sxs-lookup"><span data-stu-id="2f5b2-223">OUTPUTS</span></span>

### <span data-ttu-id="2f5b2-224">PSRepositoryItemInfo</span><span class="sxs-lookup"><span data-stu-id="2f5b2-224">PSRepositoryItemInfo</span></span>

<span data-ttu-id="2f5b2-225">`Find-Module` skapar **PSRepositoryItemInfo** -objekt som kan skickas ned pipelinen till-cmdlet: ar, till exempel `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="2f5b2-225">`Find-Module` creates **PSRepositoryItemInfo** objects that can be sent down the pipeline to cmdlets such as `Install-Module`.</span></span>

## <span data-ttu-id="2f5b2-226">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="2f5b2-226">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2f5b2-227">Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-227">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="2f5b2-228">Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-228">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="2f5b2-229">Använd följande kommando för att se till att du använder TLS 1,2:</span><span class="sxs-lookup"><span data-stu-id="2f5b2-229">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="2f5b2-230">Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="2f5b2-230">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="2f5b2-231">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="2f5b2-231">RELATED LINKS</span></span>

[<span data-ttu-id="2f5b2-232">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="2f5b2-232">Get-PSRepository</span></span>](Get-PSRepository.md)

[<span data-ttu-id="2f5b2-233">Installera-modul</span><span class="sxs-lookup"><span data-stu-id="2f5b2-233">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="2f5b2-234">Publicera-modul</span><span class="sxs-lookup"><span data-stu-id="2f5b2-234">Publish-Module</span></span>](Publish-Module.md)

[<span data-ttu-id="2f5b2-235">Spara-modul</span><span class="sxs-lookup"><span data-stu-id="2f5b2-235">Save-Module</span></span>](Save-Module.md)

[<span data-ttu-id="2f5b2-236">Avinstallera-modul</span><span class="sxs-lookup"><span data-stu-id="2f5b2-236">Uninstall-Module</span></span>](Uninstall-Module.md)

[<span data-ttu-id="2f5b2-237">Update-modul</span><span class="sxs-lookup"><span data-stu-id="2f5b2-237">Update-Module</span></span>](Update-Module.md)

[<span data-ttu-id="2f5b2-238">Registrera – PSRepository</span><span class="sxs-lookup"><span data-stu-id="2f5b2-238">Register-PSRepository</span></span>](Register-PSRepository.md)
