---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/05/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-rolecapability?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-RoleCapability
ms.openlocfilehash: ca6a3845920793e7825727bef455c1001c13f0f0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266343"
---
# <span data-ttu-id="20090-103">Find-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="20090-103">Find-RoleCapability</span></span>

## <span data-ttu-id="20090-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="20090-104">SYNOPSIS</span></span>
<span data-ttu-id="20090-105">Hittar roll funktioner i moduler.</span><span class="sxs-lookup"><span data-stu-id="20090-105">Finds role capabilities in modules.</span></span>

## <span data-ttu-id="20090-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="20090-106">SYNTAX</span></span>

### <span data-ttu-id="20090-107">Alla</span><span class="sxs-lookup"><span data-stu-id="20090-107">All</span></span>

```
Find-RoleCapability [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>] 
[-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease] 
[-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] 
[-Repository <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="20090-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="20090-108">DESCRIPTION</span></span>

<span data-ttu-id="20090-109">`Find-RoleCapability`Cmdleten söker igenom registrerade databaser för att hitta funktioner och moduler för PowerShell-roller.</span><span class="sxs-lookup"><span data-stu-id="20090-109">The `Find-RoleCapability` cmdlet searches registered repositories to find PowerShell role capabilities and modules.</span></span>

<span data-ttu-id="20090-110">`Find-RoleCapability`Ett **PSGetRoleCapabilityInfo** -objekt returneras för varje roll kapacitet som hittas av.</span><span class="sxs-lookup"><span data-stu-id="20090-110">For each role capability found by `Find-RoleCapability`, a **PSGetRoleCapabilityInfo** object is returned.</span></span> <span data-ttu-id="20090-111">**PSGetRoleCapabilityInfo** -objekt kan skickas ned pipelinen till `Install-Module` `Save-Module` cmdletarna eller.</span><span class="sxs-lookup"><span data-stu-id="20090-111">**PSGetRoleCapabilityInfo** objects can be sent down the pipeline to the `Install-Module` or `Save-Module` cmdlets.</span></span>

<span data-ttu-id="20090-112">Funktioner i PowerShell-rollen definierar vilka kommandon och program som är tillgängliga för en användare på en just tillräckligt JEA-slutpunkt (administration).</span><span class="sxs-lookup"><span data-stu-id="20090-112">PowerShell role capabilities define which commands and applications are available to a user at a Just Enough Administration (JEA) endpoint.</span></span> <span data-ttu-id="20090-113">Roll funktioner definieras av filer med ett `.psrc` tillägg.</span><span class="sxs-lookup"><span data-stu-id="20090-113">Role capabilities are defined by files with a `.psrc` extension.</span></span>

## <span data-ttu-id="20090-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="20090-114">EXAMPLES</span></span>

### <span data-ttu-id="20090-115">Exempel 1: hitta roll funktioner</span><span class="sxs-lookup"><span data-stu-id="20090-115">Example 1: Find role capabilities</span></span>

<span data-ttu-id="20090-116">`Find-RoleCapability` hittar roll funktioner i varje registrerad lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="20090-116">`Find-RoleCapability` finds role capabilities in each registered repository.</span></span> <span data-ttu-id="20090-117">Använd parametern **lagrings plats** om du vill söka i en speciell lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="20090-117">To search a specific repository, use the **Repository** parameter.</span></span>

```powershell
Find-RoleCapability
```

```output
Name             Version    ModuleName     Repository
----             -------    ----------     ----------
General-Lev1     1.0        JeaExamples    PSGallery
General-Lev2     1.0        JeaExamples    PSGallery
IIS-Lev1         1.0        JeaExamples    PSGallery
IIS-Lev2         1.0        JeaExamples    PSGallery
```

### <span data-ttu-id="20090-118">Exempel 2: hitta roll funktioner efter namn</span><span class="sxs-lookup"><span data-stu-id="20090-118">Example 2: Find role capabilities by name</span></span>

<span data-ttu-id="20090-119">`Find-RoleCapability` hittar roll funktioner efter namn.</span><span class="sxs-lookup"><span data-stu-id="20090-119">`Find-RoleCapability` finds role capabilities by name.</span></span> <span data-ttu-id="20090-120">Använd kommatecken för att avgränsa en mat ris namn.</span><span class="sxs-lookup"><span data-stu-id="20090-120">Use commas to separate an array of names.</span></span>

```powershell
Find-RoleCapability -Name General-Lev1, IIS-Lev2
```

```output
Name             Version    ModuleName     Repository
----             -------    ----------     ----------
General-Lev1     1.0        JeaExamples    PSGallery
IIS-Lev2         1.0        JeaExamples    PSGallery
```

### <span data-ttu-id="20090-121">Exempel 3: hitta och spara en roll kapacitets modul</span><span class="sxs-lookup"><span data-stu-id="20090-121">Example 3: Find and save a role capability's module</span></span>

<span data-ttu-id="20090-122">`Find-RoleCapability`Cmdleten hittar en roll kapacitet och skickar objektet nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="20090-122">The `Find-RoleCapability` cmdlet finds a role capability and sends the object down the pipeline.</span></span>
<span data-ttu-id="20090-123">`Save-Module` sparar roll funktionens modul i ett fil system.</span><span class="sxs-lookup"><span data-stu-id="20090-123">`Save-Module` saves the role capability's module to a file system.</span></span> <span data-ttu-id="20090-124">`Get-ChildItem` visar innehållet i modulens katalog.</span><span class="sxs-lookup"><span data-stu-id="20090-124">`Get-ChildItem` displays the contents of the module's directory.</span></span>

```
PS> Find-RoleCapability -Name General-Lev1 | Save-Module -Path C:\Test\Modules

PS> Get-ChildItem -Path C:\Test\Modules\JeaExamples\1.0\

    Directory: C:\Test\Modules\JeaExamples\1.0

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----          6/4/2019    16:37                RoleCapabilities
-a----          2/5/2019    18:46           1702 CreateRegisterPSSC.ps1
-a----          2/5/2019    18:46           7656 JeaExamples.psd1
-a----         10/1/2018    08:16            595 JeaExamples.psm1
```

<span data-ttu-id="20090-125">`Find-RoleCapability` använder **Name** -parametern för att ange den **allmänna-Lev1** roll funktionen.</span><span class="sxs-lookup"><span data-stu-id="20090-125">`Find-RoleCapability` uses the **Name** parameter to specify the **General-Lev1** role capability.</span></span>
<span data-ttu-id="20090-126">Objektet skickas ned pipelinen.</span><span class="sxs-lookup"><span data-stu-id="20090-126">The object is sent down the pipeline.</span></span> <span data-ttu-id="20090-127">`Save-Module` använder parametern **Path** för fil systemets plats för att spara modulen.</span><span class="sxs-lookup"><span data-stu-id="20090-127">`Save-Module` uses the **Path** parameter for the file system location to save the module.</span></span> <span data-ttu-id="20090-128">När modulen har sparats `Get-ChildItem` anger modulens **sökväg** och visar innehållet i **JeaExamples** -modulens katalog.</span><span class="sxs-lookup"><span data-stu-id="20090-128">After the module is saved, `Get-ChildItem` specifies the module's **Path** and displays the contents of the **JeaExamples** module's directory.</span></span>

### <span data-ttu-id="20090-129">Exempel 4: Sök efter och installera en roll kapacitets modul</span><span class="sxs-lookup"><span data-stu-id="20090-129">Example 4: Find and install a role capability's module</span></span>

<span data-ttu-id="20090-130">`Find-RoleCapability` söker efter modulen och skickar objektet nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="20090-130">`Find-RoleCapability` finds the module and sends the object down the pipeline.</span></span> <span data-ttu-id="20090-131">`Install-Module` installerar modulen.</span><span class="sxs-lookup"><span data-stu-id="20090-131">`Install-Module` installs the module.</span></span> <span data-ttu-id="20090-132">Efter installationen använder `Get-InstalledModule` du för att se resultatet.</span><span class="sxs-lookup"><span data-stu-id="20090-132">After the installation, use `Get-InstalledModule` to see the results.</span></span>

```
PS> Find-RoleCapability -Name General-Lev1 | Install-Module -Verbose

VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/JeaExamples/1.0.0'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/JeaExamples/1.0.0'.
VERBOSE: Completed downloading 'JeaExamples'.
VERBOSE: InstallPackageLocal' - name='JeaExamples', version='1.0',
VERBOSE: Validating the 'JeaExamples' module contents
VERBOSE: Test-ModuleManifest successfully validated the module manifest file
VERBOSE: Module 'JeaExamples' was installed successfully to path

PS> Get-InstalledModule

Version    Name            Repository     Description
-------    ----            ----------     -----------
1.0        JeaExamples     PSGallery      Some example Jea roles for general server maintenance...
```

<span data-ttu-id="20090-133">`Find-RoleCapability` använder **Name** -parametern för att ange den **allmänna-Lev1** roll funktionen.</span><span class="sxs-lookup"><span data-stu-id="20090-133">`Find-RoleCapability` uses the **Name** parameter to specify the **General-Lev1** role capability.</span></span>
<span data-ttu-id="20090-134">Objektet skickas ned pipelinen.</span><span class="sxs-lookup"><span data-stu-id="20090-134">The object is sent down the pipeline.</span></span> <span data-ttu-id="20090-135">`Install-Module` använder **verbose** -parametern för att visa status meddelanden under installationen.</span><span class="sxs-lookup"><span data-stu-id="20090-135">`Install-Module` uses the **Verbose** parameter to display status messages during the installation.</span></span> <span data-ttu-id="20090-136">När installationen är färdig `Get-InstalledModule` bekräftar utdata att **JeaExamples** -modulen har installerats.</span><span class="sxs-lookup"><span data-stu-id="20090-136">After the install is finished, the `Get-InstalledModule` output confirms that the **JeaExamples** module was installed.</span></span>

## <span data-ttu-id="20090-137">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="20090-137">PARAMETERS</span></span>

### <span data-ttu-id="20090-138">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="20090-138">-AllowPrerelease</span></span>

<span data-ttu-id="20090-139">Innehåller resurser som marker ATS som en för hands version i resultaten.</span><span class="sxs-lookup"><span data-stu-id="20090-139">Includes resources marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="20090-140">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="20090-140">-AllVersions</span></span>

<span data-ttu-id="20090-141">Anger att denna cmdlet hämtar alla versioner av en modul.</span><span class="sxs-lookup"><span data-stu-id="20090-141">Indicates that this cmdlet gets all versions of a module.</span></span> <span data-ttu-id="20090-142">Parametern **AllVersions** visar var och en av modulernas tillgängliga versioner.</span><span class="sxs-lookup"><span data-stu-id="20090-142">The **AllVersions** parameter displays each of a module's available versions.</span></span>

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

### <span data-ttu-id="20090-143">-Filter</span><span class="sxs-lookup"><span data-stu-id="20090-143">-Filter</span></span>

<span data-ttu-id="20090-144">Söker efter resurser baserat på **PackageManagement** -providerns söksyntax.</span><span class="sxs-lookup"><span data-stu-id="20090-144">Finds resources based on the **PackageManagement** provider's search syntax.</span></span> <span data-ttu-id="20090-145">Ange till exempel ord att söka efter i egenskaperna **Modulnamn** och **Description** .</span><span class="sxs-lookup"><span data-stu-id="20090-145">For example, specify words to search for within the **ModuleName** and **Description** properties.</span></span>

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

### <span data-ttu-id="20090-146">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="20090-146">-MaximumVersion</span></span>

<span data-ttu-id="20090-147">Anger den maximala version av modulen som ska tas med i resultaten.</span><span class="sxs-lookup"><span data-stu-id="20090-147">Specifies the maximum version of the module to include in results.</span></span> <span data-ttu-id="20090-148">Parametrarna **MaximumVersion** och **RequiredVersion** kan inte användas i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="20090-148">The **MaximumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="20090-149">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="20090-149">-MinimumVersion</span></span>

<span data-ttu-id="20090-150">Anger den lägsta version av modulen som ska tas med i resultaten.</span><span class="sxs-lookup"><span data-stu-id="20090-150">Specifies the minimum version of the module to include in results.</span></span> <span data-ttu-id="20090-151">Parametrarna **MinimumVersion** och **RequiredVersion** kan inte användas i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="20090-151">The **MinimumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="20090-152">-Modulnamn</span><span class="sxs-lookup"><span data-stu-id="20090-152">-ModuleName</span></span>

<span data-ttu-id="20090-153">Anger namnet på den modul som du vill söka efter roll funktioner i.</span><span class="sxs-lookup"><span data-stu-id="20090-153">Specifies the name of the module in which to search for role capabilities.</span></span> <span data-ttu-id="20090-154">Standardvärdet är alla moduler.</span><span class="sxs-lookup"><span data-stu-id="20090-154">The default is all modules.</span></span>

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

### <span data-ttu-id="20090-155">-Name</span><span class="sxs-lookup"><span data-stu-id="20090-155">-Name</span></span>

<span data-ttu-id="20090-156">Anger namnet på en roll funktion.</span><span class="sxs-lookup"><span data-stu-id="20090-156">Specifies the name of a role capability.</span></span> <span data-ttu-id="20090-157">Standardvärdet är alla roll funktioner.</span><span class="sxs-lookup"><span data-stu-id="20090-157">The default is all role capabilities.</span></span> <span data-ttu-id="20090-158">Använd kommatecken för att avgränsa en matris med resurs namn.</span><span class="sxs-lookup"><span data-stu-id="20090-158">Use commas to separate an array of resource names.</span></span>

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

### <span data-ttu-id="20090-159">-Proxy</span><span class="sxs-lookup"><span data-stu-id="20090-159">-Proxy</span></span>

<span data-ttu-id="20090-160">Anger en proxyserver för begäran, i stället för en direkt anslutning till Internet resursen.</span><span class="sxs-lookup"><span data-stu-id="20090-160">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="20090-161">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="20090-161">-ProxyCredential</span></span>

<span data-ttu-id="20090-162">Anger ett användar konto med behörighet att använda den proxyserver som anges i parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="20090-162">Specifies a user account with permission to use the proxy server specified in the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="20090-163">– Databas</span><span class="sxs-lookup"><span data-stu-id="20090-163">-Repository</span></span>

<span data-ttu-id="20090-164">Anger en lagrings plats för att söka efter roll funktioner.</span><span class="sxs-lookup"><span data-stu-id="20090-164">Specifies a repository to search for role capabilities.</span></span> <span data-ttu-id="20090-165">Använd kommatecken för att avgränsa en matris med lagrings namn.</span><span class="sxs-lookup"><span data-stu-id="20090-165">Use commas to separate an array of repository names.</span></span>

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

### <span data-ttu-id="20090-166">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="20090-166">-RequiredVersion</span></span>

<span data-ttu-id="20090-167">Anger modulens exakta versions nummer som ska ingå i resultaten.</span><span class="sxs-lookup"><span data-stu-id="20090-167">Specifies the module's exact version number to include in the results.</span></span> <span data-ttu-id="20090-168">Parametrarna **RequiredVersion** och **MinimumVersion** kan inte användas i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="20090-168">The **RequiredVersion** and the **MinimumVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="20090-169">-Tagga</span><span class="sxs-lookup"><span data-stu-id="20090-169">-Tag</span></span>

<span data-ttu-id="20090-170">Anger taggar som kategoriserar moduler i en lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="20090-170">Specifies tags that categorize modules in a repository.</span></span> <span data-ttu-id="20090-171">Använd kommatecken för att avgränsa en matris med taggar.</span><span class="sxs-lookup"><span data-stu-id="20090-171">Use commas to separate an array of tags.</span></span>

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

### <span data-ttu-id="20090-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="20090-172">CommonParameters</span></span>

<span data-ttu-id="20090-173">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="20090-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="20090-174">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="20090-174">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="20090-175">INDATA</span><span class="sxs-lookup"><span data-stu-id="20090-175">INPUTS</span></span>

### <span data-ttu-id="20090-176">System. URI</span><span class="sxs-lookup"><span data-stu-id="20090-176">System.Uri</span></span>

### <span data-ttu-id="20090-177">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="20090-177">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="20090-178">UTDATA</span><span class="sxs-lookup"><span data-stu-id="20090-178">OUTPUTS</span></span>

### <span data-ttu-id="20090-179">PSGetRoleCapabilityInfo</span><span class="sxs-lookup"><span data-stu-id="20090-179">PSGetRoleCapabilityInfo</span></span>

<span data-ttu-id="20090-180">`Find-RoleCapability`Cmdleten returnerar ett **PSGetRoleCapabilityInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="20090-180">The `Find-RoleCapability` cmdlet returns a **PSGetRoleCapabilityInfo** object.</span></span>

## <span data-ttu-id="20090-181">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="20090-181">NOTES</span></span>

## <span data-ttu-id="20090-182">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="20090-182">RELATED LINKS</span></span>

[<span data-ttu-id="20090-183">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="20090-183">Get-ChildItem</span></span>](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[<span data-ttu-id="20090-184">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="20090-184">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="20090-185">Installera-modul</span><span class="sxs-lookup"><span data-stu-id="20090-185">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="20090-186">New-PSRoleCapabilityFile</span><span class="sxs-lookup"><span data-stu-id="20090-186">New-PSRoleCapabilityFile</span></span>](../Microsoft.PowerShell.Core/New-PSRoleCapabilityFile.md)

[<span data-ttu-id="20090-187">Spara-modul</span><span class="sxs-lookup"><span data-stu-id="20090-187">Save-Module</span></span>](Save-Module.md)

