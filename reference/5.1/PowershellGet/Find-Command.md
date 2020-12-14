---
external help file: PSModule-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PowerShellGet
ms.date: 06/03/2019
online version: https://docs.microsoft.com/powershell/module/powershellget/find-command?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Find-Command
ms.openlocfilehash: eb305801bb6f8c84ffdf0ff34936ec3156ba5b0e
ms.sourcegitcommit: 22c93550c87af30c4895fcb9e9dd65e30d60ada0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/19/2020
ms.locfileid: "94891262"
---
# <span data-ttu-id="8c635-103">Find-Command</span><span class="sxs-lookup"><span data-stu-id="8c635-103">Find-Command</span></span>

## <span data-ttu-id="8c635-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="8c635-104">SYNOPSIS</span></span>
<span data-ttu-id="8c635-105">Söker efter PowerShell-kommandon i moduler.</span><span class="sxs-lookup"><span data-stu-id="8c635-105">Finds PowerShell commands in modules.</span></span>

## <span data-ttu-id="8c635-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8c635-106">SYNTAX</span></span>

### <span data-ttu-id="8c635-107">Alla</span><span class="sxs-lookup"><span data-stu-id="8c635-107">All</span></span>

```
Find-Command [[-Name] <String[]>] [-ModuleName <String>] [-MinimumVersion <String>]
 [-MaximumVersion <String>] [-RequiredVersion <String>] [-AllVersions] [-AllowPrerelease]
 [-Tag <String[]>] [-Filter <String>] [-Proxy <Uri>] [-ProxyCredential <PSCredential>]
 [-Repository <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="8c635-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="8c635-108">DESCRIPTION</span></span>

<span data-ttu-id="8c635-109">Cmdlet: en `Find-Command` hittar PowerShell-kommandon som cmdlets, alias, Functions och arbets flöden.</span><span class="sxs-lookup"><span data-stu-id="8c635-109">The `Find-Command` cmdlet finds PowerShell commands such as cmdlets, aliases, functions, and workflows.</span></span> <span data-ttu-id="8c635-110">`Find-Command` söker i moduler i registrerade databaser.</span><span class="sxs-lookup"><span data-stu-id="8c635-110">`Find-Command` searches modules in registered repositories.</span></span>

<span data-ttu-id="8c635-111">`Find-Command`Ett **PSGetCommandInfo** -objekt returneras för varje kommando som hittas av.</span><span class="sxs-lookup"><span data-stu-id="8c635-111">For each command found by `Find-Command`, a **PSGetCommandInfo** object is returned.</span></span> <span data-ttu-id="8c635-112">**PSGetCommandInfo** -objektet kan skickas ned pipelinen till `Install-Module` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="8c635-112">The **PSGetCommandInfo** object can be sent down the pipeline to the `Install-Module` cmdlet.</span></span>
<span data-ttu-id="8c635-113">`Install-Module` installerar den modul som innehåller kommandot.</span><span class="sxs-lookup"><span data-stu-id="8c635-113">`Install-Module` installs the module that contains the command.</span></span>

## <span data-ttu-id="8c635-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="8c635-114">EXAMPLES</span></span>

### <span data-ttu-id="8c635-115">Exempel 1: Sök efter alla kommandon i en angiven lagrings plats</span><span class="sxs-lookup"><span data-stu-id="8c635-115">Example 1: Find all commands in a specified repository</span></span>

<span data-ttu-id="8c635-116">`Find-Command`Cmdleten söker efter moduler i en registrerad lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="8c635-116">The `Find-Command` cmdlet searches a registered repository for modules.</span></span>

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

<span data-ttu-id="8c635-117">`Find-Command` använder parametern **lagrings plats** för att ange namnet på en registrerad databas.</span><span class="sxs-lookup"><span data-stu-id="8c635-117">`Find-Command` uses the **Repository** parameter to specify a registered repository's name.</span></span> <span data-ttu-id="8c635-118">Objekten skickas ned pipelinen.</span><span class="sxs-lookup"><span data-stu-id="8c635-118">The objects are sent down the pipeline.</span></span> <span data-ttu-id="8c635-119">`Select-Object` tar emot objekten och använder den **första** parametern för att visa de första 10 resultaten.</span><span class="sxs-lookup"><span data-stu-id="8c635-119">`Select-Object` receives the objects and uses the **First** parameter to display the first 10 results.</span></span>

### <span data-ttu-id="8c635-120">Exempel 2: hitta ett kommando efter namn</span><span class="sxs-lookup"><span data-stu-id="8c635-120">Example 2: Find a command by name</span></span>

<span data-ttu-id="8c635-121">`Find-Command` kan använda namnet på ett kommando för att hitta modulen i en lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="8c635-121">`Find-Command` can use the name of a command to locate the module in a repository.</span></span> <span data-ttu-id="8c635-122">Det är möjligt att ett kommando namn finns i flera **ModuleNames**.</span><span class="sxs-lookup"><span data-stu-id="8c635-122">It's possible that a command name exists in multiple **ModuleNames**.</span></span>

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

<span data-ttu-id="8c635-123">`Find-Command` använder parametern **lagrings plats** för att söka i **PSGallery**.</span><span class="sxs-lookup"><span data-stu-id="8c635-123">`Find-Command` uses the **Repository** parameter to search the **PSGallery**.</span></span> <span data-ttu-id="8c635-124">Parametern **Name** anger kommandot **Get-TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="8c635-124">The **Name** parameter specifies the command **Get-TargetResource**.</span></span>

### <span data-ttu-id="8c635-125">Exempel 3: hitta kommandon efter namn och installera modulen</span><span class="sxs-lookup"><span data-stu-id="8c635-125">Example 3: Find commands by name and install the module</span></span>

<span data-ttu-id="8c635-126">`Find-Command` kan hitta kommandot och modulen och sedan skicka objektet till `Install-Module` .</span><span class="sxs-lookup"><span data-stu-id="8c635-126">`Find-Command` can locate the command and module, then send the object to `Install-Module`.</span></span> <span data-ttu-id="8c635-127">Om ett kommando ingår i flera moduler, använder du `Find-Command` parametern cmdlets **-modul-Name** .</span><span class="sxs-lookup"><span data-stu-id="8c635-127">If a command is included in multiple modules, use the `Find-Command` cmdlets **Module-Name** parameter.</span></span>
<span data-ttu-id="8c635-128">Annars kan moduler installeras som du inte vill installera.</span><span class="sxs-lookup"><span data-stu-id="8c635-128">Otherwise, modules might be installed that you didn't want to install.</span></span>

```powershell
PS> Find-Command -Name Get-TargetResource -Repository PSGallery -ModuleName SystemLocaleDsc |
    Install-Module

PS> Get-InstalledModule

Version   Name               Repository   Description
-------   ----               ----------   -----------
1.2.0.0   SystemLocaleDsc    PSGallery    This DSC Resource allows configuration of the Windows...
```

<span data-ttu-id="8c635-129">`Find-Command` använder parametern **Name** för att ange kommandot **Get-TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="8c635-129">`Find-Command` uses the **Name** parameter to specify the command **Get-TargetResource**.</span></span> <span data-ttu-id="8c635-130">Parametern **lagring** söker i **PSGallery**.</span><span class="sxs-lookup"><span data-stu-id="8c635-130">The **Repository** parameter searches the **PSGallery**.</span></span> <span data-ttu-id="8c635-131">Parametern **Modulnamn** anger den modul som du vill installera, **SystemLocaleDsc**.</span><span class="sxs-lookup"><span data-stu-id="8c635-131">The **ModuleName** parameter specifies the module you want to install, **SystemLocaleDsc**.</span></span> <span data-ttu-id="8c635-132">Objektet skickas ned pipelinen till `Install-Module` och modulen är installerad.</span><span class="sxs-lookup"><span data-stu-id="8c635-132">The object is sent down the pipeline to `Install-Module` and the module is installed.</span></span> <span data-ttu-id="8c635-133">När installationen är klar kan du använda `Get-InstalledModule` för att visa resultatet.</span><span class="sxs-lookup"><span data-stu-id="8c635-133">After the installation finishes, you can use `Get-InstalledModule` to display the results.</span></span>

### <span data-ttu-id="8c635-134">Exempel 4: hitta ett kommando och spara dess modul</span><span class="sxs-lookup"><span data-stu-id="8c635-134">Example 4: Find a command and save its module</span></span>

```
PS> Find-Command -Name Invoke-ScriptAnalyzer -Repository PSGallery | Save-Module -Path C:\Test\Modules -Verbose

VERBOSE: Downloading 'https://www.powershellgallery.com/api/v2/package/PSScriptAnalyzer/1.18.0'.
VERBOSE: Completed downloading 'https://www.powershellgallery.com/api/v2/package/PSScriptAnalyzer/1.18.0'.
VERBOSE: Completed downloading 'PSScriptAnalyzer'.
VERBOSE: Module 'PSScriptAnalyzer' was saved successfully to path 'C:\Test\Modules\PSScriptAnalyzer\1.18.0'.
```

<span data-ttu-id="8c635-135">`Find-Command` använder parametrarna **namn** och **lagrings plats** för att söka efter kommandot **Invoke-ScriptAnalyzer** i **PSGallery** -lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="8c635-135">`Find-Command` uses the **Name** and **Repository** parameters to search for the command **Invoke-ScriptAnalyzer** in the **PSGallery** repository.</span></span> <span data-ttu-id="8c635-136">Objektet skickas ned pipelinen till `Save-Module` .</span><span class="sxs-lookup"><span data-stu-id="8c635-136">The object is sent down the pipeline to `Save-Module`.</span></span> <span data-ttu-id="8c635-137">Parametern **Path** bestämmer var du vill spara modulen.</span><span class="sxs-lookup"><span data-stu-id="8c635-137">The **Path** parameter determines the location to save the module.</span></span> <span data-ttu-id="8c635-138">**Verbose** är en valfri parameter, men visar status utdata i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="8c635-138">**Verbose** is an optional parameter, but displays status output in the PowerShell console.</span></span> <span data-ttu-id="8c635-139">Utförliga utdata är bra för fel sökning.</span><span class="sxs-lookup"><span data-stu-id="8c635-139">The verbose output is beneficial for troubleshooting.</span></span>

## <span data-ttu-id="8c635-140">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="8c635-140">PARAMETERS</span></span>

### <span data-ttu-id="8c635-141">-AllowPrerelease</span><span class="sxs-lookup"><span data-stu-id="8c635-141">-AllowPrerelease</span></span>

<span data-ttu-id="8c635-142">Innehåller moduler som är markerade som en för hands version i resultaten.</span><span class="sxs-lookup"><span data-stu-id="8c635-142">Includes modules marked as a prerelease in the results.</span></span>

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

### <span data-ttu-id="8c635-143">-AllVersions</span><span class="sxs-lookup"><span data-stu-id="8c635-143">-AllVersions</span></span>

<span data-ttu-id="8c635-144">Anger att denna cmdlet hämtar alla versioner av en modul.</span><span class="sxs-lookup"><span data-stu-id="8c635-144">Indicates that this cmdlet gets all versions of a module.</span></span>

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

### <span data-ttu-id="8c635-145">-Filter</span><span class="sxs-lookup"><span data-stu-id="8c635-145">-Filter</span></span>

<span data-ttu-id="8c635-146">Söker efter moduler baserat på **PackageManagement** -providerns söksyntax.</span><span class="sxs-lookup"><span data-stu-id="8c635-146">Finds modules based on the **PackageManagement** provider's search syntax.</span></span> <span data-ttu-id="8c635-147">Ange till exempel ord att söka efter i egenskaperna **Modulnamn** och **Description** .</span><span class="sxs-lookup"><span data-stu-id="8c635-147">For example, specify words to search for within the **ModuleName** and **Description** properties.</span></span>

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

### <span data-ttu-id="8c635-148">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="8c635-148">-MaximumVersion</span></span>

<span data-ttu-id="8c635-149">Anger den maximala version av modulen som ska tas med i resultaten.</span><span class="sxs-lookup"><span data-stu-id="8c635-149">Specifies the maximum version of the module to include in results.</span></span> <span data-ttu-id="8c635-150">Parametrarna **MaximumVersion** och **RequiredVersion** kan inte användas i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="8c635-150">The **MaximumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="8c635-151">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="8c635-151">-MinimumVersion</span></span>

<span data-ttu-id="8c635-152">Anger den lägsta version av modulen som ska tas med i resultaten.</span><span class="sxs-lookup"><span data-stu-id="8c635-152">Specifies the minimum version of the module to include in results.</span></span> <span data-ttu-id="8c635-153">Parametrarna **MinimumVersion** och **RequiredVersion** kan inte användas i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="8c635-153">The **MinimumVersion** and the **RequiredVersion** parameters can't be used in the same command.</span></span>

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

### <span data-ttu-id="8c635-154">-Modulnamn</span><span class="sxs-lookup"><span data-stu-id="8c635-154">-ModuleName</span></span>

<span data-ttu-id="8c635-155">Anger namnet på en modul för att söka efter kommandon.</span><span class="sxs-lookup"><span data-stu-id="8c635-155">Specifies the name of a module to search for commands.</span></span> <span data-ttu-id="8c635-156">Standardvärdet är alla moduler.</span><span class="sxs-lookup"><span data-stu-id="8c635-156">The default is all modules.</span></span>

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

### <span data-ttu-id="8c635-157">-Name</span><span class="sxs-lookup"><span data-stu-id="8c635-157">-Name</span></span>

<span data-ttu-id="8c635-158">Anger kommando namnet som ska sökas efter i en lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="8c635-158">Specifies the command name to search for in a repository.</span></span> <span data-ttu-id="8c635-159">Använd kommatecken för att avgränsa en matris med kommando namn.</span><span class="sxs-lookup"><span data-stu-id="8c635-159">Use commas to separate an array of command names.</span></span>

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

### <span data-ttu-id="8c635-160">-Proxy</span><span class="sxs-lookup"><span data-stu-id="8c635-160">-Proxy</span></span>

<span data-ttu-id="8c635-161">Anger en proxyserver för begäran, i stället för en direkt anslutning till Internet resursen.</span><span class="sxs-lookup"><span data-stu-id="8c635-161">Specifies a proxy server for the request, rather than a direct connection to the internet resource.</span></span>

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

### <span data-ttu-id="8c635-162">-ProxyCredential</span><span class="sxs-lookup"><span data-stu-id="8c635-162">-ProxyCredential</span></span>

<span data-ttu-id="8c635-163">Anger ett användar konto som har behörighet att använda den proxyserver som anges av parametern **proxy** .</span><span class="sxs-lookup"><span data-stu-id="8c635-163">Specifies a user account that has permission to use the proxy server that is specified by the **Proxy** parameter.</span></span>

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

### <span data-ttu-id="8c635-164">– Databas</span><span class="sxs-lookup"><span data-stu-id="8c635-164">-Repository</span></span>

<span data-ttu-id="8c635-165">Anger den lagrings plats som ska sökas efter kommandon.</span><span class="sxs-lookup"><span data-stu-id="8c635-165">Specifies the repository to search for commands.</span></span> <span data-ttu-id="8c635-166">Använd kommatecken för att avgränsa en matris med lagrings namn.</span><span class="sxs-lookup"><span data-stu-id="8c635-166">Use commas to separate an array of repository names.</span></span> <span data-ttu-id="8c635-167">Standardvärdet är alla databaser.</span><span class="sxs-lookup"><span data-stu-id="8c635-167">The default is all repositories.</span></span>

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

### <span data-ttu-id="8c635-168">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="8c635-168">-RequiredVersion</span></span>

<span data-ttu-id="8c635-169">Anger den version av modulen som ska tas med i resultaten.</span><span class="sxs-lookup"><span data-stu-id="8c635-169">Specifies the version of the module to include in the results.</span></span>

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

### <span data-ttu-id="8c635-170">-Tagga</span><span class="sxs-lookup"><span data-stu-id="8c635-170">-Tag</span></span>

<span data-ttu-id="8c635-171">Anger taggar som kategoriserar moduler i en lagrings plats.</span><span class="sxs-lookup"><span data-stu-id="8c635-171">Specifies tags that categorize modules in a repository.</span></span> <span data-ttu-id="8c635-172">Använd kommatecken för att avgränsa en matris med taggar.</span><span class="sxs-lookup"><span data-stu-id="8c635-172">Use commas to separate an array of tags.</span></span>

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

### <span data-ttu-id="8c635-173">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8c635-173">CommonParameters</span></span>

<span data-ttu-id="8c635-174">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8c635-174">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8c635-175">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8c635-175">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8c635-176">INDATA</span><span class="sxs-lookup"><span data-stu-id="8c635-176">INPUTS</span></span>

## <span data-ttu-id="8c635-177">UTDATA</span><span class="sxs-lookup"><span data-stu-id="8c635-177">OUTPUTS</span></span>

### <span data-ttu-id="8c635-178">PSGetCommandInfo</span><span class="sxs-lookup"><span data-stu-id="8c635-178">PSGetCommandInfo</span></span>

<span data-ttu-id="8c635-179">`Find-Command` matar ut ett **PSGetCommandInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="8c635-179">`Find-Command` outputs a **PSGetCommandInfo** object.</span></span>

## <span data-ttu-id="8c635-180">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="8c635-180">NOTES</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8c635-181">Från och med april 2020 stöder PowerShell-galleriet inte längre Transport Layer Security (TLS), version 1,0 och 1,1.</span><span class="sxs-lookup"><span data-stu-id="8c635-181">As of April 2020, the PowerShell Gallery no longer supports Transport Layer Security (TLS) versions 1.0 and 1.1.</span></span> <span data-ttu-id="8c635-182">Om du inte använder TLS 1,2 eller senare visas ett fel meddelande när du försöker få åtkomst till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="8c635-182">If you are not using TLS 1.2 or higher, you will receive an error when trying to access the PowerShell Gallery.</span></span> <span data-ttu-id="8c635-183">Använd följande kommando för att se till att du använder TLS 1,2:</span><span class="sxs-lookup"><span data-stu-id="8c635-183">Use the following command to ensure you are using TLS 1.2:</span></span>
>
> `[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`
>
> <span data-ttu-id="8c635-184">Mer information finns i [meddelandet](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) i PowerShell-bloggen.</span><span class="sxs-lookup"><span data-stu-id="8c635-184">For more information, see the [announcement](https://devblogs.microsoft.com/powershell/powershell-gallery-tls-support/) in the PowerShell blog.</span></span>

## <span data-ttu-id="8c635-185">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="8c635-185">RELATED LINKS</span></span>

[<span data-ttu-id="8c635-186">Get-InstalledModule</span><span class="sxs-lookup"><span data-stu-id="8c635-186">Get-InstalledModule</span></span>](Get-InstalledModule.md)

[<span data-ttu-id="8c635-187">Installera-modul</span><span class="sxs-lookup"><span data-stu-id="8c635-187">Install-Module</span></span>](Install-Module.md)

[<span data-ttu-id="8c635-188">Spara-modul</span><span class="sxs-lookup"><span data-stu-id="8c635-188">Save-Module</span></span>](Save-Module.md)

[<span data-ttu-id="8c635-189">Select-Object</span><span class="sxs-lookup"><span data-stu-id="8c635-189">Select-Object</span></span>](../Microsoft.PowerShell.Utility/Select-Object.md)

[<span data-ttu-id="8c635-190">Avinstallera-modul</span><span class="sxs-lookup"><span data-stu-id="8c635-190">Uninstall-Module</span></span>](Uninstall-Module.md)
