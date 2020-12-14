---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/05/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-rolecapability?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-RoleCapability
ms.openlocfilehash: a84dee14872ad5a7d0f7bac8e0057dc527855074
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94890400"
---
# <span data-ttu-id="662cc-102">Find-RoleCapability</span><span class="sxs-lookup"><span data-stu-id="662cc-102">Find-RoleCapability</span></span>

## <span data-ttu-id="662cc-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="662cc-103">SYNOPSIS</span></span>
<span data-ttu-id="662cc-104">Hittar roll funktioner i moduler.</span><span class="sxs-lookup"><span data-stu-id="662cc-104">Finds role capabilities in modules.</span></span>

## <span data-ttu-id="662cc-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="662cc-105">SYNTAX</span></span>

### <span data-ttu-id="662cc-106">Alla</span><span class="sxs-lookup"><span data-stu-id="662cc-106">All</span></span>

```
Find-RoleCapability [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>] 
[-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease] 
[-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>] 
[-Repository <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="662cc-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="662cc-107">DESCRIPTION</span></span>

<span data-ttu-id="662cc-108">`Find-RoleCapability`Cmdleten söker igenom registrerade databaser för att hitta funktioner och moduler för PowerShell-roller.</span><span class="sxs-lookup"><span data-stu-id="662cc-108">The `Find-RoleCapability` cmdlet searches registered repositories to find PowerShell role capabilities and modules.</span></span>

<span data-ttu-id="662cc-109">`Find-RoleCapability`Ett **PSGetRoleCapabilityInfo** -objekt returneras för varje roll kapacitet som hittas av.</span><span class="sxs-lookup"><span data-stu-id="662cc-109">For each role capability found by `Find-RoleCapability`, a **PSGetRoleCapabilityInfo** object is returned.</span></span> <span data-ttu-id="662cc-110">**PSGetRoleCapabilityInfo** -objekt kan skickas ned pipelinen till `Install-Module` `Save-Module` cmdletarna eller.</span><span class="sxs-lookup"><span data-stu-id="662cc-110">**PSGetRoleCapabilityInfo** objects can be sent down the pipeline to the `Install-Module` or `Save-Module` cmdlets.</span></span>

<span data-ttu-id="662cc-111">Funktioner i PowerShell-rollen definierar vilka kommandon och program som är tillgängliga för en användare på en just tillräckligt JEA-slutpunkt (administration).</span><span class="sxs-lookup"><span data-stu-id="662cc-111">PowerShell role capabilities define which commands and applications are available to a user at a Just Enough Administration (JEA) endpoint.</span></span> <span data-ttu-id="662cc-112">Roll funktioner definieras av filer med ett `.psrc` tillägg.</span><span class="sxs-lookup"><span data-stu-id="662cc-112">Role capabilities are defined by files with a `.psrc` extension.</span></span>

## <span data-ttu-id="662cc-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="662cc-113">EXAMPLES</span></span>

### <span data-ttu-id="662cc-114">Exempel 1: hitta roll funktioner</span><span class="sxs-lookup"><span data-stu-id="662cc-114">Example 1: Find role capabilities</span></span>

<span data-ttu-id="662cc-115">`Find-RoleCapability` hittar roll funktioner i varje registrerad lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="662cc-115">`Find-RoleCapability` finds role capabilities in each registered repository.</span></span> <span data-ttu-id="662cc-116">Använd parametern **lagrings plats** om du vill söka i en speciell lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="662cc-116">To search a specific repository, use the **Repository** parameter.</span></span>

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

### <span data-ttu-id="662cc-117">Exempel 2: hitta roll funktioner efter namn</span><span class="sxs-lookup"><span data-stu-id="662cc-117">Example 2: Find role capabilities by name</span></span>

<span data-ttu-id="662cc-118">`Find-RoleCapability` hittar roll funktioner efter namn.</span><span class="sxs-lookup"><span data-stu-id="662cc-118">`Find-RoleCapability` finds role capabilities by name.</span></span> <span data-ttu-id="662cc-119">Använd kommatecken för att avgränsa en mat ris namn.</span><span class="sxs-lookup"><span data-stu-id="662cc-119">Use commas to separate an array of names.</span></span>

```powershell
Find-RoleCapability -Name General-Lev1, IIS-Lev2
```

```output
Name             Version    ModuleName     Repository
----             -------    ----------     ----------
General-Lev1     1.0        JeaExamples    PSGallery
IIS-Lev2         1.0        JeaExamples    PSGallery
```

### <span data-ttu-id="662cc-120">Exempel 3: hitta och spara en roll kapacitets modul</span><span class="sxs-lookup"><span data-stu-id="662cc-120">Example 3: Find and save a role capability's module</span></span>

<span data-ttu-id="662cc-121">`Find-RoleCapability`Cmdleten hittar en roll kapacitet och skickar objektet nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="662cc-121">The `Find-RoleCapability` cmdlet finds a role capability and sends the object down the pipeline.</span></span>
<span data-ttu-id="662cc-122">`Save-Module` sparar roll funktionens modul i ett fil system.</span><span class="sxs-lookup"><span data-stu-id="662cc-122">`Save-Module` saves the role capability's module to a file system.</span></span> <span data-ttu-id="662cc-123">`Get-ChildItem` visar innehållet i modulens katalog.</span><span class="sxs-lookup"><span data-stu-id="662cc-123">`Get-ChildItem` displays the contents of the module's directory.</span></span>

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

<span data-ttu-id="662cc-124">`Find-RoleCapability` använder **Name** -parametern för att ange den **allmänna-Lev1** roll funktionen.</span><span class="sxs-lookup"><span data-stu-id="662cc-124">`Find-RoleCapability` uses the **Name** parameter to specify the **General-Lev1** role capability.</span></span>
<span data-ttu-id="662cc-125">Objektet skickas ned pipelinen.</span><span class="sxs-lookup"><span data-stu-id="662cc-125">The object is sent down the pipeline.</span></span> <span data-ttu-id="662cc-126">`Save-Module` använder parametern **Path** för fil systemets plats för att spara modulen.</span><span class="sxs-lookup"><span data-stu-id="662cc-126">`Save-Module` uses the **Path** parameter for the file system location to save the module.</span></span> <span data-ttu-id="662cc-127">När modulen har sparats `Get-ChildItem` anger modulens **sökväg** och visar innehållet i **JeaExamples** -modulens katalog.</span><span class="sxs-lookup"><span data-stu-id="662cc-127">After the module is saved, `Get-ChildItem` specifies the module's **Path** and displays the contents of the **JeaExamples** module's directory.</span></span>

### <span data-ttu-id="662cc-128">Exempel 4: Sök efter och installera en roll kapacitets modul</span><span class="sxs-lookup"><span data-stu-id="662cc-128">Example 4: Find and install a role capability's module</span></span>

<span data-ttu-id="662cc-129">`Find-RoleCapability` söker efter modulen och skickar objektet nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="662cc-129">`Find-RoleCapability` finds the module and sends the object down the pipeline.</span></span> <span data-ttu-id="662cc-130">`Install-Module` installerar modulen.</span><span class="sxs-lookup"><span data-stu-id="662cc-130">`Install-Module` installs the module.</span></span> <span data-ttu-id="662cc-131">Efter installationen använder `Get-InstalledModule` du för att se resultatet.</span><span class="sxs-lookup"><span data-stu-id="662cc-131">After the installation, use `Get-InstalledModule` to see the results.</span></span>

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

<span data-ttu-id="662cc-132">`Find-RoleCapability` använder **Name** -parametern för att ange den **allmänna-Lev1** roll funktionen.</span><span class="sxs-lookup"><span data-stu-id="662cc-132">`Find-RoleCapability` uses the **Name** parameter to specify the **General-Lev1** role capability.</span></span>
<span data-ttu-id="662cc-133">Objektet skickas ned pipelinen.</span><span class="sxs-lookup"><span data-stu-id="662cc-133">The object is sent down the pipeline.</span></span> <span data-ttu-id="662cc-134">`Install-Module` använder **verbose** -parametern för att visa status meddelanden under installationen.</span><span class="sxs-lookup"><span data-stu-id="662cc-134">`Install-Module` uses the **Verbose** parameter to display status messages during the installation.</span></span> <span data-ttu-id="662cc-135">När installationen är färdig `Get-InstalledModule` bekräftar utdata att **JeaExamples** -modulen har installerats.</span><span class="sxs-lookup"><span data-stu-id="662cc-135">After the install is finished, the `Get-InstalledModule` output confirms that the **JeaExamples** module was installed.</span></span>

## <span data-ttu-id="662cc-136">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="662cc-136">PARAMETERS</span></span>

### <span data-ttu-id="662cc-137">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="662cc-137">-AllowPrerelease</span></span>

<span data-ttu-id="662cc-138">Innehåller resurser som marker ATS som en för hands version i resultaten.</span><span class="sxs-lookup"><span data-stu-id="662cc-138">Includes resources marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="662cc-139">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="662cc-139">-AllVersions</span></span>

<span data-ttu-id="662cc-140">Anger att denna cmdlet hämtar alla versioner av en modul.</span><span class="sxs-lookup"><span data-stu-id="662cc-140">Indicates that this cmdlet gets all versions of a module.</span></span> <span data-ttu-id="662cc-141">Parametern **AllVersions** visar var och en av modulernas tillgängliga versioner.</span><span class="sxs-lookup"><span data-stu-id="662cc-141">The **AllVersions** parameter displays each of a module's available versions.</span></span>

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

### <span data-ttu-id="662cc-142">-Filter</span><span class="sxs-lookup"><span data-stu-id="662cc-142">-Filter</span></span>

<span data-ttu-id="662cc-143">Söker efter resurser baserat på **PackageManagement** -providerns söksyntax.</span><span class="sxs-lookup"><span data-stu-id="662cc-143">Finds resources based on the **PackageManagement** provider's search syntax.</span></span> <span data-ttu-id="662cc-144">Ange till exempel ord att söka efter i egenskaperna **Modulnamn** och **Description** .</span><span class="sxs-lookup"><span data-stu-id="662cc-144">For example, specify words to search for within the **ModuleName** and **Description** properties.</span></span>

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

### <span data-ttu-id="662cc-145">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="662cc-145">-MaximumVersion</span></span>

<span data-ttu-id="662cc-146">Anger den maximala version av modulen som ska tas med i resultaten.</span><span class="sxs-lookup"><span data-stu-id="662cc-146">Specifies the maximum version of the module to include in results.</span></span> <span data-ttu-id="662cc-147">Parametrarna **MaximumVersion** och **RequiredVersion** kan inte användas i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="662cc-147">The **MaximumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="662cc-148">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="662cc-148">-MinimumVersion</span></span>

<span data-ttu-id="662cc-149">Anger den lägsta version av modulen som ska tas med i resultaten.</span><span class="sxs-lookup"><span data-stu-id="662cc-149">Specifies the minimum version of the module to include in results.</span></span> <span data-ttu-id="662cc-150">Parametrarna **MinimumVersion** och **RequiredVersion** kan inte användas i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="662cc-150">The **MinimumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="662cc-151">-Modulnamn</span><span class="sxs-lookup"><span data-stu-id="662cc-151">-ModuleName</span></span>

<span data-ttu-id="662cc-152">Anger namnet på den modul som du vill söka efter roll funktioner i.</span><span class="sxs-lookup"><span data-stu-id="662cc-152">Specifies the name of the module in which to search for role capabilities.</span></span> <span data-ttu-id="662cc-153">Standardvärdet är alla moduler.</span><span class="sxs-lookup"><span data-stu-id="662cc-153">The default is all modules.</span></span>

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

### <span data-ttu-id="662cc-154">-Name</span><span class="sxs-lookup"><span data-stu-id="662cc-154">-Name</span></span>

<span data-ttu-id="662cc-155">Anger namnet på en roll funktion.</span><span class="sxs-lookup"><span data-stu-id="662cc-155">Specifies the name of a role capability.</span></span> <span data-ttu-id="662cc-156">Standardvärdet är alla roll funktioner.</span><span class="sxs-lookup"><span data-stu-id="662cc-156">The default is all role capabilities.</span></span> <span data-ttu-id="662cc-157">Använd kommatecken för att avgränsa en matris med resurs namn.</span><span class="sxs-lookup"><span data-stu-id="662cc-157">Use commas to separate an array of resource names.</span></span>

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

### <span data-ttu-id="662cc-158">-Proxy</span><span class="sxs-lookup"><span data-stu-id="662cc-158">-Proxy</span></span>

<span data-ttu-id="662cc-159">Anger en proxyserver för begäran, i stället för en direkt anslutning till Internet resursen.</span><span class="sxs-lookup"><span data-stu-id="662cc-159">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="662cc-160">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="662cc-160">-ProxyCredential</span></span>

<span data-ttu-id="662cc-161">Anger ett användar konto med behörighet att använda den proxyserver som anges i parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="662cc-161">Specifies a user account with permission to use the proxy server specified in the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="662cc-162">– Databas</span><span class="sxs-lookup"><span data-stu-id="662cc-162">-Repository</span></span>

<span data-ttu-id="662cc-163">Anger en lagrings plats för att söka efter roll funktioner.</span><span class="sxs-lookup"><span data-stu-id="662cc-163">Specifies a repository to search for role capabilities.</span></span> <span data-ttu-id="662cc-164">Använd kommatecken för att avgränsa en matris med lagrings namn.</span><span class="sxs-lookup"><span data-stu-id="662cc-164">Use commas to separate an array of repository names.</span></span>

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

### <span data-ttu-id="662cc-165">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="662cc-165">-RequiredVersion</span></span>

<span data-ttu-id="662cc-166">Anger modulens exakta versions nummer som ska ingå i resultaten.</span><span class="sxs-lookup"><span data-stu-id="662cc-166">Specifies the module's exact version number to include in the results.</span></span> <span data-ttu-id="662cc-167">Parametrarna **RequiredVersion** och **MinimumVersion** kan inte användas i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="662cc-167">The **RequiredVersion** and the **MinimumVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="662cc-168">-Tagga</span><span class="sxs-lookup"><span data-stu-id="662cc-168">-Tag</span></span>

<span data-ttu-id="662cc-169">Anger taggar som kategoriserar moduler i en lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="662cc-169">Specifies tags that categorize modules in a repository.</span></span> <span data-ttu-id="662cc-170">Använd kommatecken för att avgränsa en matris med taggar.</span><span class="sxs-lookup"><span data-stu-id="662cc-170">Use commas to separate an array of tags.</span></span>

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

### <span data-ttu-id="662cc-171">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="662cc-171">CommonParameters</span></span>

<span data-ttu-id="662cc-172">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="662cc-172">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="662cc-173">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="662cc-173">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="662cc-174">INDATA</span><span class="sxs-lookup"><span data-stu-id="662cc-174">INPUTS</span></span>

### <span data-ttu-id="662cc-175">System. URI</span><span class="sxs-lookup"><span data-stu-id="662cc-175">System.Uri</span></span>

### <span data-ttu-id="662cc-176">System. Management. Automation. PSCredential</span><span class="sxs-lookup"><span data-stu-id="662cc-176">System.Management.Automation.PSCredential</span></span>

## <span data-ttu-id="662cc-177">UTDATA</span><span class="sxs-lookup"><span data-stu-id="662cc-177">OUTPUTS</span></span>

### <span data-ttu-id="662cc-178">PSGetRoleCapabilityInfo</span><span class="sxs-lookup"><span data-stu-id="662cc-178">PSGetRoleCapabilityInfo</span></span>

<span data-ttu-id="662cc-179">`Find-RoleCapability`Cmdleten returnerar ett **PSGetRoleCapabilityInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="662cc-179">The `Find-RoleCapability` cmdlet returns a **PSGetRoleCapabilityInfo** object.</span></span>

## <span data-ttu-id="662cc-180">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="662cc-180">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="662cc-181">Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1.</span><span class="sxs-lookup"><span data-stu-id="662cc-181">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="662cc-182">Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="662cc-182">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="662cc-183">Använd följande kommando för att se till att du använder TLS 1,2:</span><span class="sxs-lookup"><span data-stu-id="662cc-183">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="662cc-184">Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="662cc-184">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="662cc-185">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="662cc-185">RELATED LINKS</span></span>

[<span data-ttu-id="662cc-186">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="662cc-186">Get-ChildItem</span></span>](../Microsoft.PowerShell.Management/Get-ChildItem.md)

[<span data-ttu-id="662cc-187">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="662cc-187">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="662cc-188">Installera-modul</span><span class="sxs-lookup"><span data-stu-id="662cc-188">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="662cc-189">New-PSRoleCapabilityFile</span><span class="sxs-lookup"><span data-stu-id="662cc-189">New-PSRoleCapabilityFile</span></span>](../Microsoft.PowerShell.Core/New-PSRoleCapabilityFile.md)

[<span data-ttu-id="662cc-190">Spara-modul</span><span class="sxs-lookup"><span data-stu-id="662cc-190">Save-Module</span></span>](Save-Module.md)
