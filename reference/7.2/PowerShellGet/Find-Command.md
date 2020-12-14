---
external help file: PSModule-help.xml
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-command?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Command
ms.openlocfilehash: a24d66aa1ce9e353e41cc7a686ee9f910a7106fc
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94889260"
---
# <span data-ttu-id="5b430-102">Find-Command</span><span class="sxs-lookup"><span data-stu-id="5b430-102">Find-Command</span></span>

## <span data-ttu-id="5b430-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="5b430-103">SYNOPSIS</span></span>
<span data-ttu-id="5b430-104">Söker efter PowerShell-kommandon i moduler.</span><span class="sxs-lookup"><span data-stu-id="5b430-104">Finds PowerShell commands in modules.</span></span>

## <span data-ttu-id="5b430-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5b430-105">SYNTAX</span></span>

### <span data-ttu-id="5b430-106">Alla</span><span class="sxs-lookup"><span data-stu-id="5b430-106">All</span></span>

```
Find-Command [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease]
 [-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Repository <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="5b430-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="5b430-107">DESCRIPTION</span></span>

<span data-ttu-id="5b430-108">Cmdlet: en `Find-Command` hittar PowerShell-kommandon som cmdlets, alias, Functions och arbets flöden.</span><span class="sxs-lookup"><span data-stu-id="5b430-108">The `Find-Command` cmdlet finds PowerShell commands such as cmdlets, aliases, functions, and workflows.</span></span> <span data-ttu-id="5b430-109">`Find-Command` söker i moduler i registrerade databaser.</span><span class="sxs-lookup"><span data-stu-id="5b430-109">`Find-Command` searches modules in registered repositories.</span></span>

<span data-ttu-id="5b430-110">`Find-Command`Ett **PSGetCommandInfo** -objekt returneras för varje kommando som hittas av.</span><span class="sxs-lookup"><span data-stu-id="5b430-110">For each command found by `Find-Command`, a **PSGetCommandInfo** object is returned.</span></span> <span data-ttu-id="5b430-111">**PSGetCommandInfo** -objektet kan skickas ned pipelinen till `Install-Module` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5b430-111">The **PSGetCommandInfo** object can be sent down the pipeline to the `Install-Module` cmdlet.</span></span>
<span data-ttu-id="5b430-112">`Install-Module` installerar den modul som innehåller kommandot.</span><span class="sxs-lookup"><span data-stu-id="5b430-112">`Install-Module` installs the module that contains the command.</span></span>

## <span data-ttu-id="5b430-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="5b430-113">EXAMPLES</span></span>

### <span data-ttu-id="5b430-114">Exempel 1: Sök efter alla kommandon i en angiven lagrings plats</span><span class="sxs-lookup"><span data-stu-id="5b430-114">Example 1: Find all commands in a specified repository</span></span>

<span data-ttu-id="5b430-115">`Find-Command`Cmdleten söker efter moduler i en registrerad lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="5b430-115">The `Find-Command` cmdlet searches a registered repository for modules.</span></span>

```powershell
Find-Command -Repository PSGallery | Select-Object -First 10
```

```output
Name                                Version    ModuleName          Repository
----                                -------    ----------          ----------
Disable-AzureRmDataCollection       5.8.3      AzureRM.profile     PSGallery
Disable-AzureRmContextAutosave      5.8.3      AzureRM.profile     PSGallery
Enable-AzureRmDataCollection        5.8.3      AzureRM.profile     PSGallery
Enable-AzureRmContextAutosave       5.8.3      AzureRM.profile     PSGallery
Remove-AzureRmEnvironment           5.8.3      AzureRM.profile     PSGallery
Get-AzureRmEnvironment              5.8.3      AzureRM.profile     PSGallery
Set-AzureRmEnvironment              5.8.3      AzureRM.profile     PSGallery
Add-AzureRmEnvironment              5.8.3      AzureRM.profile     PSGallery
Get-AzureRmSubscription             5.8.3      AzureRM.profile     PSGallery
Connect-AzureRmAccount              5.8.3      AzureRM.profile     PSGallery
```

<span data-ttu-id="5b430-116">`Find-Command` använder parametern **lagrings plats** för att ange namnet på en registrerad databas.</span><span class="sxs-lookup"><span data-stu-id="5b430-116">`Find-Command` uses the **Repository** parameter to specify a registered repository's name.</span></span> <span data-ttu-id="5b430-117">Objekten skickas ned pipelinen.</span><span class="sxs-lookup"><span data-stu-id="5b430-117">The objects are sent down the pipeline.</span></span> <span data-ttu-id="5b430-118">`Select-Object` tar emot objekten och använder den **första** parametern för att visa de första 10 resultaten.</span><span class="sxs-lookup"><span data-stu-id="5b430-118">`Select-Object` receives the objects and uses the **First** parameter to display the first 10 results.</span></span>

### <span data-ttu-id="5b430-119">Exempel 2: hitta ett kommando efter namn</span><span class="sxs-lookup"><span data-stu-id="5b430-119">Example 2: Find a command by name</span></span>

<span data-ttu-id="5b430-120">`Find-Command` kan använda namnet på ett kommando för att hitta modulen i en lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="5b430-120">`Find-Command` can use the name of a command to locate the module in a repository.</span></span> <span data-ttu-id="5b430-121">Det är möjligt att ett kommando namn finns i flera **ModuleNames**.</span><span class="sxs-lookup"><span data-stu-id="5b430-121">It's possible that a command name exists in multiple **ModuleNames**.</span></span>

```powershell
Find-Command -Repository PSGallery -Name Get-TargetResource
```

```Output
Name                  Version    ModuleName                      Repository
----                  -------    ----------                      ----------
Get-TargetResource    3.1.0.0    xPowerShellExecutionPolicy      PSGallery
Get-TargetResource    1.0.0      xInternetExplorerHomePage       PSGallery
Get-TargetResource    1.2.0.0    SystemLocaleDsc                 PSGallery
```

<span data-ttu-id="5b430-122">`Find-Command` använder parametern **lagrings plats** för att söka i **PSGallery**.</span><span class="sxs-lookup"><span data-stu-id="5b430-122">`Find-Command` uses the **Repository** parameter to search the **PSGallery**.</span></span> <span data-ttu-id="5b430-123">Parametern **Name** anger kommandot **Get-TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="5b430-123">The **Name** parameter specifies the command **Get-TargetResource**.</span></span>

### <span data-ttu-id="5b430-124">Exempel 3: hitta kommandon efter namn och installera modulen</span><span class="sxs-lookup"><span data-stu-id="5b430-124">Example 3: Find commands by name and install the module</span></span>

<span data-ttu-id="5b430-125">`Find-Command` kan hitta kommandot och modulen och sedan skicka objektet till `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="5b430-125">`Find-Command` can locate the command and module, then send the object to `Install-Module`.</span></span> <span data-ttu-id="5b430-126">Om ett kommando ingår i flera moduler, använder du `Find-Command` parametern cmdlets **-modul-Name** .</span><span class="sxs-lookup"><span data-stu-id="5b430-126">If a command is included in multiple modules, use the `Find-Command` cmdlets **Module-Name** parameter.</span></span>
<span data-ttu-id="5b430-127">Annars kan moduler installeras som du inte vill installera.</span><span class="sxs-lookup"><span data-stu-id="5b430-127">Otherwise, modules might be installed that you didn't want to install.</span></span>

```powershell
PS> Find-Command -Name Get-TargetResource -Repository PSGallery -ModuleName SystemLocaleDsc |
    Install-Module

PS> Get-InstalledModule

Version   Name               Repository   Description
-------   ----               ----------   -----------
1.2.0.0   SystemLocaleDsc    PSGallery    This DSC Resource allows configuration of the Windows...
```

<span data-ttu-id="5b430-128">`Find-Command` använder parametern **Name** för att ange kommandot **Get-TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="5b430-128">`Find-Command` uses the **Name** parameter to specify the command **Get-TargetResource**.</span></span> <span data-ttu-id="5b430-129">Parametern **lagring** söker i **PSGallery**.</span><span class="sxs-lookup"><span data-stu-id="5b430-129">The **Repository** parameter searches the **PSGallery**.</span></span> <span data-ttu-id="5b430-130">Parametern **Modulnamn** anger den modul som du vill installera, **SystemLocaleDsc**.</span><span class="sxs-lookup"><span data-stu-id="5b430-130">The **ModuleName** parameter specifies the module you want to install, **SystemLocaleDsc**.</span></span> <span data-ttu-id="5b430-131">Objektet skickas ned pipelinen till `Install-Module` och modulen är installerad.</span><span class="sxs-lookup"><span data-stu-id="5b430-131">The object is sent down the pipeline to `Install-Module` and the module is installed.</span></span> <span data-ttu-id="5b430-132">När installationen är klar kan du använda `Get-InstalledModule` för att visa resultatet.</span><span class="sxs-lookup"><span data-stu-id="5b430-132">After the installation finishes, you can use `Get-InstalledModule` to display the results.</span></span>

### <span data-ttu-id="5b430-133">Exempel 4: hitta ett kommando och spara dess modul</span><span class="sxs-lookup"><span data-stu-id="5b430-133">Example 4: Find a command and save its module</span></span>

```
PS> Find-Command -Name Invoke-ScriptAnalyzer -Repository PSGallery | Save-Module -Path C:\Test\Modules -Verbose

VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/PSScriptAnalyzer/1.18.0'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/PSScriptAnalyzer/1.18.0'.
VERBOSE: Completed downloading 'PSScriptAnalyzer'.
VERBOSE: Module 'PSScriptAnalyzer' was saved successfully to path 'C:\Test\Modules\PSScriptAnalyzer\1.18.0'.
```

<span data-ttu-id="5b430-134">`Find-Command` använder parametrarna **namn** och **lagrings plats** för att söka efter kommandot **Invoke-ScriptAnalyzer** i **PSGallery** -lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="5b430-134">`Find-Command` uses the **Name** and **Repository** parameters to search for the command **Invoke-ScriptAnalyzer** in the **PSGallery** repository.</span></span> <span data-ttu-id="5b430-135">Objektet skickas ned pipelinen till `Save-Module` .</span><span class="sxs-lookup"><span data-stu-id="5b430-135">The object is sent down the pipeline to `Save-Module`.</span></span> <span data-ttu-id="5b430-136">Parametern **Path** bestämmer var du vill spara modulen.</span><span class="sxs-lookup"><span data-stu-id="5b430-136">The **Path** parameter determines the location to save the module.</span></span> <span data-ttu-id="5b430-137">**Verbose** är en valfri parameter, men visar status utdata i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="5b430-137">**Verbose** is an optional parameter, but displays status output in the PowerShell console.</span></span> <span data-ttu-id="5b430-138">Utförliga utdata är bra för fel sökning.</span><span class="sxs-lookup"><span data-stu-id="5b430-138">The verbose output is beneficial for troubleshooting.</span></span>

## <span data-ttu-id="5b430-139">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="5b430-139">PARAMETERS</span></span>

### <span data-ttu-id="5b430-140">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="5b430-140">-AllowPrerelease</span></span>

<span data-ttu-id="5b430-141">Innehåller moduler som är markerade som en för hands version i resultaten.</span><span class="sxs-lookup"><span data-stu-id="5b430-141">Includes modules marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="5b430-142">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="5b430-142">-AllVersions</span></span>

<span data-ttu-id="5b430-143">Anger att denna cmdlet hämtar alla versioner av en modul.</span><span class="sxs-lookup"><span data-stu-id="5b430-143">Indicates that this cmdlet gets all versions of a module.</span></span>

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

### <span data-ttu-id="5b430-144">-Filter</span><span class="sxs-lookup"><span data-stu-id="5b430-144">-Filter</span></span>

<span data-ttu-id="5b430-145">Söker efter moduler baserat på **PackageManagement** -providerns söksyntax.</span><span class="sxs-lookup"><span data-stu-id="5b430-145">Finds modules based on the **PackageManagement** provider's search syntax.</span></span> <span data-ttu-id="5b430-146">Ange till exempel ord att söka efter i egenskaperna **Modulnamn** och **Description** .</span><span class="sxs-lookup"><span data-stu-id="5b430-146">For example, specify words to search for within the **ModuleName** and **Description** properties.</span></span>

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

### <span data-ttu-id="5b430-147">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="5b430-147">-MaximumVersion</span></span>

<span data-ttu-id="5b430-148">Anger den maximala version av modulen som ska tas med i resultaten.</span><span class="sxs-lookup"><span data-stu-id="5b430-148">Specifies the maximum version of the module to include in results.</span></span> <span data-ttu-id="5b430-149">Parametrarna **MaximumVersion** och **RequiredVersion** kan inte användas i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="5b430-149">The **MaximumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="5b430-150">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="5b430-150">-MinimumVersion</span></span>

<span data-ttu-id="5b430-151">Anger den lägsta version av modulen som ska tas med i resultaten.</span><span class="sxs-lookup"><span data-stu-id="5b430-151">Specifies the minimum version of the module to include in results.</span></span> <span data-ttu-id="5b430-152">Parametrarna **MinimumVersion** och **RequiredVersion** kan inte användas i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="5b430-152">The **MinimumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="5b430-153">-Modulnamn</span><span class="sxs-lookup"><span data-stu-id="5b430-153">-ModuleName</span></span>

<span data-ttu-id="5b430-154">Anger namnet på en modul för att söka efter kommandon.</span><span class="sxs-lookup"><span data-stu-id="5b430-154">Specifies the name of a module to search for commands.</span></span> <span data-ttu-id="5b430-155">Standardvärdet är alla moduler.</span><span class="sxs-lookup"><span data-stu-id="5b430-155">The default is all modules.</span></span>

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

### <span data-ttu-id="5b430-156">-Name</span><span class="sxs-lookup"><span data-stu-id="5b430-156">-Name</span></span>

<span data-ttu-id="5b430-157">Anger kommando namnet som ska sökas efter i en lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="5b430-157">Specifies the command name to search for in a repository.</span></span> <span data-ttu-id="5b430-158">Använd kommatecken för att avgränsa en matris med kommando namn.</span><span class="sxs-lookup"><span data-stu-id="5b430-158">Use commas to separate an array of command names.</span></span>

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

### <span data-ttu-id="5b430-159">-Proxy</span><span class="sxs-lookup"><span data-stu-id="5b430-159">-Proxy</span></span>

<span data-ttu-id="5b430-160">Anger en proxyserver för begäran, i stället för en direkt anslutning till Internet resursen.</span><span class="sxs-lookup"><span data-stu-id="5b430-160">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="5b430-161">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="5b430-161">-ProxyCredential</span></span>

<span data-ttu-id="5b430-162">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="5b430-162">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="5b430-163">– Databas</span><span class="sxs-lookup"><span data-stu-id="5b430-163">-Repository</span></span>

<span data-ttu-id="5b430-164">Anger den lagrings plats som ska sökas efter kommandon.</span><span class="sxs-lookup"><span data-stu-id="5b430-164">Specifies the repository to search for commands.</span></span> <span data-ttu-id="5b430-165">Använd kommatecken för att avgränsa en matris med lagrings namn.</span><span class="sxs-lookup"><span data-stu-id="5b430-165">Use commas to separate an array of repository names.</span></span> <span data-ttu-id="5b430-166">Standardvärdet är alla databaser.</span><span class="sxs-lookup"><span data-stu-id="5b430-166">The default is all repositories.</span></span>

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

### <span data-ttu-id="5b430-167">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="5b430-167">-RequiredVersion</span></span>

<span data-ttu-id="5b430-168">Anger den version av modulen som ska tas med i resultaten.</span><span class="sxs-lookup"><span data-stu-id="5b430-168">Specifies the version of the module to include in the results.</span></span>

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

### <span data-ttu-id="5b430-169">-Tagga</span><span class="sxs-lookup"><span data-stu-id="5b430-169">-Tag</span></span>

<span data-ttu-id="5b430-170">Anger taggar som kategoriserar moduler i en lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="5b430-170">Specifies tags that categorize modules in a repository.</span></span> <span data-ttu-id="5b430-171">Använd kommatecken för att avgränsa en matris med taggar.</span><span class="sxs-lookup"><span data-stu-id="5b430-171">Use commas to separate an array of tags.</span></span>

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

### <span data-ttu-id="5b430-172">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5b430-172">CommonParameters</span></span>

<span data-ttu-id="5b430-173">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5b430-173">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5b430-174">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5b430-174">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5b430-175">INDATA</span><span class="sxs-lookup"><span data-stu-id="5b430-175">INPUTS</span></span>

## <span data-ttu-id="5b430-176">UTDATA</span><span class="sxs-lookup"><span data-stu-id="5b430-176">OUTPUTS</span></span>

### <span data-ttu-id="5b430-177">PSGetCommandInfo</span><span class="sxs-lookup"><span data-stu-id="5b430-177">PSGetCommandInfo</span></span>

<span data-ttu-id="5b430-178">`Find-Command` matar ut ett **PSGetCommandInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="5b430-178">`Find-Command` outputs a **PSGetCommandInfo** object.</span></span>

## <span data-ttu-id="5b430-179">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="5b430-179">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5b430-180">Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1.</span><span class="sxs-lookup"><span data-stu-id="5b430-180">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="5b430-181">Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="5b430-181">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="5b430-182">Använd följande kommando för att se till att du använder TLS 1,2:</span><span class="sxs-lookup"><span data-stu-id="5b430-182">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="5b430-183">Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="5b430-183">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="5b430-184">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="5b430-184">RELATED LINKS</span></span>

[<span data-ttu-id="5b430-185">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="5b430-185">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="5b430-186">Installera-modul</span><span class="sxs-lookup"><span data-stu-id="5b430-186">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="5b430-187">Spara-modul</span><span class="sxs-lookup"><span data-stu-id="5b430-187">Save-Module</span></span>](Save-Module.md)

[<span data-ttu-id="5b430-188">Select-Object</span><span class="sxs-lookup"><span data-stu-id="5b430-188">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="5b430-189">Avinstallera-modul</span><span class="sxs-lookup"><span data-stu-id="5b430-189">Uninstall-Module</span></span>](Uninstall-Module.md)
