---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/16/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/update-help?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Help
ms.openlocfilehash: 2851305f40c9805ae3f0fcc2a25a82a57a78cd23
ms.sourcegitcommit: d3f78120bdc9096c72aa0dfdbdd91efaf254c738
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/04/2020
ms.locfileid: "93268886"
---
# <span data-ttu-id="7242b-103">Update-Help</span><span class="sxs-lookup"><span data-stu-id="7242b-103">Update-Help</span></span>

## <span data-ttu-id="7242b-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="7242b-104">SYNOPSIS</span></span>
<span data-ttu-id="7242b-105">Laddar ned och installerar de senaste hjälpfilerna på din dator.</span><span class="sxs-lookup"><span data-stu-id="7242b-105">Downloads and installs the newest help files on your computer.</span></span>

## <span data-ttu-id="7242b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7242b-106">SYNTAX</span></span>

### <span data-ttu-id="7242b-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="7242b-107">Path (Default)</span></span>

```
Update-Help [[-Module] <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [[-SourcePath] <String[]>] [-Recurse] [[-UICulture] <CultureInfo[]>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-Force] [-Scope <UpdateHelpScope>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

### <span data-ttu-id="7242b-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="7242b-108">LiteralPath</span></span>

```
Update-Help [[-Module] <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [-LiteralPath <String[]>] [-Recurse] [[-UICulture] <CultureInfo[]>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-Force] [-Scope <UpdateHelpScope>] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="7242b-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="7242b-109">DESCRIPTION</span></span>

<span data-ttu-id="7242b-110">`Update-Help`Cmdlet: en laddar ned de senaste hjälpfilerna för PowerShell-moduler och installerar dem på din dator.</span><span class="sxs-lookup"><span data-stu-id="7242b-110">The `Update-Help` cmdlet downloads the newest help files for PowerShell modules and installs them on your computer.</span></span> <span data-ttu-id="7242b-111">Du behöver inte starta om PowerShell för att ändringen ska börja gälla.</span><span class="sxs-lookup"><span data-stu-id="7242b-111">You need not restart PowerShell to make the change effective.</span></span> <span data-ttu-id="7242b-112">Du kan använda `Get-Help` cmdleten för att visa de nya hjälpfilerna omedelbart.</span><span class="sxs-lookup"><span data-stu-id="7242b-112">You can use the `Get-Help` cmdlet to view the new help files immediately.</span></span>

<span data-ttu-id="7242b-113">`Update-Help` kontrollerar versionen för hjälpfilerna på din dator.</span><span class="sxs-lookup"><span data-stu-id="7242b-113">`Update-Help` checks the version of the help files on your computer.</span></span> <span data-ttu-id="7242b-114">Om du inte har hjälp filer för en modul eller om dina hjälpfiler är inaktuella, `Update-Help` laddar ned de senaste hjälpfilerna.</span><span class="sxs-lookup"><span data-stu-id="7242b-114">If you don't have help files for a module or if your help files are outdated, `Update-Help` downloads the newest help files.</span></span> <span data-ttu-id="7242b-115">Hjälpfilerna kan laddas ned och installeras från Internet eller en fil resurs.</span><span class="sxs-lookup"><span data-stu-id="7242b-115">The help files can be downloaded and installed from the internet or a file share.</span></span>

<span data-ttu-id="7242b-116">Utan parametrar `Update-Help` uppdaterar hjälpfilerna för moduler i sessionen och för alla installerade moduler som stöder uppdaterbar hjälp.</span><span class="sxs-lookup"><span data-stu-id="7242b-116">Without parameters, `Update-Help` updates the help files for modules in the session and for all installed modules that support Updatable Help.</span></span> <span data-ttu-id="7242b-117">Moduler som är installerade men inte inlästa i den aktuella sessionen ingår.</span><span class="sxs-lookup"><span data-stu-id="7242b-117">Modules that are installed but not loaded in the current session are included.</span></span> <span data-ttu-id="7242b-118">PowerShell-moduler lagras på en plats som anges i `$env:PSModulePath` miljö variabeln.</span><span class="sxs-lookup"><span data-stu-id="7242b-118">PowerShell modules are stored in a location listed in the `$env:PSModulePath` environment variable.</span></span> <span data-ttu-id="7242b-119">Mer information finns i [about_Updatable_Help](./About/about_Updatable_Help.md).</span><span class="sxs-lookup"><span data-stu-id="7242b-119">For more information, see [about_Updatable_Help](./About/about_Updatable_Help.md).</span></span>

<span data-ttu-id="7242b-120">Du kan använda parametern **modul** för att uppdatera hjälpfiler för en viss modul.</span><span class="sxs-lookup"><span data-stu-id="7242b-120">You can use the **Module** parameter to update help files for a particular module.</span></span> <span data-ttu-id="7242b-121">Använd parametern **värdet** för att hämta hjälpfiler på flera språk och nationella inställningar.</span><span class="sxs-lookup"><span data-stu-id="7242b-121">Use the **UICulture** parameter to download help files in multiple languages and locales.</span></span>

<span data-ttu-id="7242b-122">Du kan också använda `Update-Help` på datorer som inte är anslutna till Internet.</span><span class="sxs-lookup"><span data-stu-id="7242b-122">You can also use `Update-Help` on computers that are not connected to the internet.</span></span> <span data-ttu-id="7242b-123">Använd först cmdlet: en `Save-Help` för att hämta hjälpfiler från Internet och spara dem i en delad mapp som är tillgänglig för datorn som inte är ansluten till Internet.</span><span class="sxs-lookup"><span data-stu-id="7242b-123">First, use the `Save-Help`cmdlet to download help files from the internet and save them in a shared folder that is accessible to the system not connected to the internet.</span></span> <span data-ttu-id="7242b-124">Använd sedan **SourcePath** -parametern för `Update-Help` för att ladda ned de uppdaterade hjälpfilerna från den delade och installera dem på datorn.</span><span class="sxs-lookup"><span data-stu-id="7242b-124">Then use the **SourcePath** parameter of `Update-Help` to download the updated help files from the shared and install them on the computer.</span></span>

<span data-ttu-id="7242b-125">Du kan automatisera hjälp uppdateringar genom att lägga till `Update-Help` cmdleten i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="7242b-125">You can automate help updates by adding the `Update-Help` cmdlet to your PowerShell profile.</span></span> <span data-ttu-id="7242b-126">Som standard `Update-Help` körs bara en tid per dag på varje dator.</span><span class="sxs-lookup"><span data-stu-id="7242b-126">By default, `Update-Help` runs only one time per day on each computer.</span></span> <span data-ttu-id="7242b-127">Använd parametern **Force** om du vill åsidosätta en begränsning per dag.</span><span class="sxs-lookup"><span data-stu-id="7242b-127">To override the once-per-day limit, use the **Force** parameter.</span></span>

<span data-ttu-id="7242b-128">`Update-Help`Cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="7242b-128">The `Update-Help` cmdlet was introduced in Windows PowerShell 3.0.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7242b-129">`Update-Help` kräver administratörs behörighet i PowerShell 6,0 och nedan.</span><span class="sxs-lookup"><span data-stu-id="7242b-129">`Update-Help` requires administrative privileges in PowerShell 6.0 and below.</span></span>
> <span data-ttu-id="7242b-130">PowerShell 6,1 och högre anger standard **omfånget** till `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="7242b-130">PowerShell 6.1 and above set the default **Scope** to `CurrentUser`.</span></span>
> <span data-ttu-id="7242b-131">Före PowerShell 6,1 var **omfångs** parametern inte tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="7242b-131">Prior to PowerShell 6.1, the **Scope** parameter was not available.</span></span>
>
> <span data-ttu-id="7242b-132">Du måste vara medlem i gruppen Administratörer på datorn för att kunna uppdatera hjälpfilerna för PowerShell Core-modulerna.</span><span class="sxs-lookup"><span data-stu-id="7242b-132">You must be a member of the Administrators group on the computer to update the help files for the PowerShell Core modules.</span></span>
>
> <span data-ttu-id="7242b-133">Om du vill hämta eller uppdatera hjälpfilerna för moduler i installations katalogen för PowerShell ( `$PSHOME\Modules` ), inklusive PowerShell-modulerna, startar du PowerShell med alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="7242b-133">To download or update the help files for modules in the PowerShell installation directory (`$PSHOME\Modules`), including the PowerShell Core modules, start PowerShell by using the **Run as administrator** option.</span></span>
> <span data-ttu-id="7242b-134">Till exempel: `Start-Process pwsh.exe -Verb RunAs`.</span><span class="sxs-lookup"><span data-stu-id="7242b-134">For example: `Start-Process pwsh.exe -Verb RunAs`.</span></span>

## <span data-ttu-id="7242b-135">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="7242b-135">EXAMPLES</span></span>

### <span data-ttu-id="7242b-136">Exempel 1: uppdatera hjälpfilerna för alla moduler</span><span class="sxs-lookup"><span data-stu-id="7242b-136">Example 1: Update help files for all modules</span></span>

<span data-ttu-id="7242b-137">`Update-Help`Cmdleten uppdaterar hjälpfiler för installerade moduler som stöder uppdaterings bar hjälp.</span><span class="sxs-lookup"><span data-stu-id="7242b-137">The `Update-Help` cmdlet updates help files for installed modules that support Updatable Help.</span></span> <span data-ttu-id="7242b-138">Kultur språket för användar gränssnittet (UI) har angetts i operativ systemet.</span><span class="sxs-lookup"><span data-stu-id="7242b-138">The user-interface (UI) culture language is set in the operating system.</span></span>

```powershell
Update-Help
```

### <span data-ttu-id="7242b-139">Exempel 2: uppdatera hjälpfiler för angivna moduler</span><span class="sxs-lookup"><span data-stu-id="7242b-139">Example 2: Update help files for specified modules</span></span>

<span data-ttu-id="7242b-140">`Update-Help`Cmdleten uppdaterar endast hjälp filer för Modulnamn som börjar med **Microsoft. PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="7242b-140">The `Update-Help` cmdlet updates help files only for module names that begin with **Microsoft.PowerShell**.</span></span>

```powershell
Update-Help -Module Microsoft.PowerShell*
```

### <span data-ttu-id="7242b-141">Exempel 3: uppdatera hjälpfiler för olika språk</span><span class="sxs-lookup"><span data-stu-id="7242b-141">Example 3: Update help files for different languages</span></span>

<span data-ttu-id="7242b-142">`Update-Help`Cmdleten uppdaterar hjälpfilerna för japanska (ja-JP) och engelska (en-US) för alla moduler.</span><span class="sxs-lookup"><span data-stu-id="7242b-142">The `Update-Help` cmdlet updates the Japanese (ja-JP) and English (en-US) help files for all modules.</span></span>

<span data-ttu-id="7242b-143">Om en modul inte tillhandahåller hjälp filer för en angiven användar gränssnitts kultur visas ett fel meddelande för modulen och användar gränssnitts kulturen.</span><span class="sxs-lookup"><span data-stu-id="7242b-143">If a module doesn't provide help files for a specified UI culture, an error message is displayed for the module and UI culture.</span></span> <span data-ttu-id="7242b-144">I det här exemplet anger fel meddelandet att hjälpfilerna för **Ja-JP** inte hittades för modulen **Microsoft. PowerShell. Utility**.</span><span class="sxs-lookup"><span data-stu-id="7242b-144">In this example, the error message indicates that the **ja-JP** help files were not found for module **Microsoft.PowerShell.Utility**.</span></span>

```powershell
Update-Help -UICulture ja-JP, en-US
```

```Output
Update-Help : Failed to update Help for the module(s) 'Microsoft.PowerShell.Utility' with UI culture(s) {ja-JP}
No UI culture was found that matches the following pattern: ja-JP.
```

### <span data-ttu-id="7242b-145">Exempel 4: uppdatera hjälpfiler på flera datorer från en fil resurs</span><span class="sxs-lookup"><span data-stu-id="7242b-145">Example 4: Update help files on multiple computers from a file share</span></span>

<span data-ttu-id="7242b-146">I det här exemplet hämtas uppdaterade hjälpfiler från Internet och sparas i en fil resurs.</span><span class="sxs-lookup"><span data-stu-id="7242b-146">In this example, updated help files are downloaded from the internet and saved in a file share.</span></span> <span data-ttu-id="7242b-147">Användarautentiseringsuppgifter krävs som har behörighet att komma åt fil resursen och installera uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="7242b-147">User credentials are needed that have permissions to access the file share and install updates.</span></span> <span data-ttu-id="7242b-148">När en fil resurs används är det möjligt att uppdatera datorer som finns bakom brand väggar eller inte är anslutna till Internet.</span><span class="sxs-lookup"><span data-stu-id="7242b-148">When a file share is used, it's possible to update computers that are behind firewalls or aren't connected to the internet.</span></span>

```powershell
Save-Help -DestinationPath \\Server01\Share\PSHelp -Credential Domain01\Admin01
Invoke-Command -ComputerName (Get-Content Servers.txt) -ScriptBlock {
     Update-Help -SourcePath \\Server01\Share\PSHelp -Credential Domain01\Admin01
}
```

<span data-ttu-id="7242b-149">`Save-Help`Kommandot laddar ned de senaste hjälpfilerna för alla moduler som stöder uppdaterings bar hjälp.</span><span class="sxs-lookup"><span data-stu-id="7242b-149">The `Save-Help` command downloads the newest help files for all modules that support Updatable Help.</span></span>
<span data-ttu-id="7242b-150">Parametern **DestinationPath** sparar filerna i `\\Server01\Share\PSHelp` fil resursen.</span><span class="sxs-lookup"><span data-stu-id="7242b-150">The **DestinationPath** parameter saves the files in the `\\Server01\Share\PSHelp` file share.</span></span> <span data-ttu-id="7242b-151">Parametern **Credential** anger en användare som har behörighet att komma åt fil resursen.</span><span class="sxs-lookup"><span data-stu-id="7242b-151">The **Credential** parameter specifies a user who has permission to access the file share.</span></span>

<span data-ttu-id="7242b-152">`Invoke-Command`Cmdleten kör `Update-Help` fjärrkommandon på flera datorer.</span><span class="sxs-lookup"><span data-stu-id="7242b-152">The `Invoke-Command` cmdlet runs remote `Update-Help` commands on multiple computers.</span></span> <span data-ttu-id="7242b-153">Parametern **computername** hämtar en lista över fjärrdatorer från **Servers.txt** -filen.</span><span class="sxs-lookup"><span data-stu-id="7242b-153">The **ComputerName** parameter gets a list of remote computers from the **Servers.txt** file.</span></span> <span data-ttu-id="7242b-154">Parametern **script block** kör `Update-Help` kommandot och använder parametern **SourcePath** för att ange den fil resurs som innehåller de uppdaterade hjälpfilerna.</span><span class="sxs-lookup"><span data-stu-id="7242b-154">The **ScriptBlock** parameter runs the `Update-Help` command and uses the **SourcePath** parameter to specify the file share that contains the updated help files.</span></span> <span data-ttu-id="7242b-155">Parametern **Credential** anger en användare som kan komma åt fil resursen och köra `Update-Help` fjärrkommandot.</span><span class="sxs-lookup"><span data-stu-id="7242b-155">The **Credential** parameter specifies a user who can access the file share and run the remote `Update-Help` command.</span></span>

### <span data-ttu-id="7242b-156">Exempel 5: Hämta en lista över uppdaterade hjälpfiler</span><span class="sxs-lookup"><span data-stu-id="7242b-156">Example 5: Get a list of updated help files</span></span>

<span data-ttu-id="7242b-157">`Update-Help`Cmdleten uppdaterar hjälpen för en angiven modul.</span><span class="sxs-lookup"><span data-stu-id="7242b-157">The `Update-Help` cmdlet updates help for a specified module.</span></span> <span data-ttu-id="7242b-158">Cmdleten använder den **utförliga** gemensamma parametern för att visa en lista med de hjälpfiler som uppdaterades.</span><span class="sxs-lookup"><span data-stu-id="7242b-158">The cmdlet uses the **Verbose** common parameter to display the list of help files that were updated.</span></span> <span data-ttu-id="7242b-159">Du kan använda **utförligt** för att visa utdata för alla hjälpfiler eller hjälp filer för en speciell modul.</span><span class="sxs-lookup"><span data-stu-id="7242b-159">You can use **Verbose** to view output for all help files or help files for a specific module.</span></span>

<span data-ttu-id="7242b-160">Utan **verbose** -parametern `Update-Help` visar inte kommandots resultat.</span><span class="sxs-lookup"><span data-stu-id="7242b-160">Without the **Verbose** parameter, `Update-Help` doesn't display the results of the command.</span></span> <span data-ttu-id="7242b-161">Utdata för **utförlig** parameter är användbart för att verifiera att hjälpfilerna har uppdaterats eller om den senaste versionen är installerad.</span><span class="sxs-lookup"><span data-stu-id="7242b-161">The **Verbose** parameter output is useful to verify that the help files were updated or if the latest version is installed.</span></span>

```powershell
Update-Help -Module Microsoft.PowerShell.Utility -Verbose
```

### <span data-ttu-id="7242b-162">Exempel 6: hitta moduler som stöder uppdaterbar hjälp</span><span class="sxs-lookup"><span data-stu-id="7242b-162">Example 6: Find modules that support Updatable Help</span></span>

<span data-ttu-id="7242b-163">I det här exemplet visas moduler som stöder uppdaterbar hjälp.</span><span class="sxs-lookup"><span data-stu-id="7242b-163">This example lists modules that support Updatable Help.</span></span> <span data-ttu-id="7242b-164">Kommandot använder modulens **HelpInfoUri** -egenskap för att identifiera moduler som stöder uppdaterbar hjälp.</span><span class="sxs-lookup"><span data-stu-id="7242b-164">The command uses the module's **HelpInfoUri** property to identify modules that support Updatable Help.</span></span> <span data-ttu-id="7242b-165">Egenskapen **HelpInfoUri** innehåller en adress som omdirigeras när `Update-Help` cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="7242b-165">The **HelpInfoUri** property contains an address that is redirected when the `Update-Help` cmdlet is run.</span></span>

```powershell
Get-Module -ListAvailable | Where-Object -Property HelpInfoUri
```

```output
   Directory: C:\program files\powershell\6\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   6.1.0.0    CimCmdlets                          Core      {Get-CimAssociatedInstance... }
Manifest   1.2.2.0    Microsoft.PowerShell.Archive        Desk      {Compress-Archive... }
Manifest   6.1.0.0    Microsoft.PowerShell.Diagnostics    Core      {Get-WinEvent, New-WinEvent}

    Directory: C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules

ModuleType Version    Name                                PSEdition ExportedCommands
---------- -------    ----                                --------- ----------------
Manifest   2.0.1.0    Appx                                Core,Desk {Add-AppxPackage, ... }
Script     1.0.0.0    AssignedAccess                      Core,Desk {Clear-AssignedAccess, ... }
Manifest   1.0.0.0    BitLocker                           Core,Desk {Unlock-BitLocker, ... }
```

### <span data-ttu-id="7242b-166">Exempel 7: uppdaterade hjälp filer för inventering</span><span class="sxs-lookup"><span data-stu-id="7242b-166">Example 7: Inventory updated help files</span></span>

<span data-ttu-id="7242b-167">I det här exemplet skapar skriptet `Get-UpdateHelpVersion.ps1` en inventering av de uppdaterbara hjälpfilerna för varje modul och deras versions nummer.</span><span class="sxs-lookup"><span data-stu-id="7242b-167">In this example, the script `Get-UpdateHelpVersion.ps1` creates an inventory of the Updatable Help files for each module and their version numbers.</span></span>

<span data-ttu-id="7242b-168">Skriptet identifierar moduler som stöder uppdaterbar hjälp med hjälp av egenskapen **HelpInfoUri** för moduler.</span><span class="sxs-lookup"><span data-stu-id="7242b-168">The script identifies modules that support Updatable Help by using the **HelpInfoUri** property of modules.</span></span> <span data-ttu-id="7242b-169">För moduler som stöder uppdaterbar hjälp söker skriptet efter och tolkar hjälp informations filen (\* helpinfo.xml) för att hitta det senaste versions numret.</span><span class="sxs-lookup"><span data-stu-id="7242b-169">For modules that support Updatable Help, the script looks for and parses the help information file (\*helpinfo.xml) to find the latest version number.</span></span>

<span data-ttu-id="7242b-170">Skriptet använder klassen **PSCustomObject** och en hash-tabell för att skapa ett anpassat utgående objekt.</span><span class="sxs-lookup"><span data-stu-id="7242b-170">The script uses the **PSCustomObject** class and a hash table to create a custom output object.</span></span>

```powershell
# Get-UpdateHelpVersion.ps1
Param(
    [parameter(Mandatory=$False)]
    [String[]]
    $Module
)
$HelpInfoNamespace = @{helpInfo='http://schemas.microsoft.com/powershell/help/2010/05'}

if ($Module) { $Modules = Get-Module $Module -ListAvailable | where {$_.HelpInfoUri} }
else { $Modules = Get-Module -ListAvailable | where {$_.HelpInfoUri} }

foreach ($mModule in $Modules)
{
    $mDir = $mModule.ModuleBase

    if (Test-Path $mdir\*helpinfo.xml)
    {
        $mName=$mModule.Name
        $mNodes = dir $mdir\*helpinfo.xml -ErrorAction SilentlyContinue |
            Select-Xml -Namespace $HelpInfoNamespace -XPath "//helpInfo:UICulture"
        foreach ($mNode in $mNodes)
        {
            $mCulture=$mNode.Node.UICultureName
            $mVer=$mNode.Node.UICultureVersion

            [PSCustomObject]@{"ModuleName"=$mName; "Culture"=$mCulture; "Version"=$mVer}
        }
    }
}
```

```Output
ModuleName                              Culture                                 Version
----------                              -------                                 -------
ActiveDirectory                         en-US                                   3.0.0.0
ADCSAdministration                      en-US                                   3.0.0.0
ADCSDeployment                          en-US                                   3.0.0.0
ADDSDeployment                          en-US                                   3.0.0.0
ADFS                                    en-US                                   3.0.0.0
```

## <span data-ttu-id="7242b-171">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="7242b-171">PARAMETERS</span></span>

### <span data-ttu-id="7242b-172">-Credential</span><span class="sxs-lookup"><span data-stu-id="7242b-172">-Credential</span></span>

<span data-ttu-id="7242b-173">Anger autentiseringsuppgifter för en användare som har behörighet att komma åt fil system platsen som anges av **SourcePath**.</span><span class="sxs-lookup"><span data-stu-id="7242b-173">Specifies credentials of a user who has permission to access the file system location specified by **SourcePath**.</span></span> <span data-ttu-id="7242b-174">Den här parametern är endast giltig när **SourcePath** -eller **LiteralPath** -parametern används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="7242b-174">This parameter is valid only when the **SourcePath** or **LiteralPath** parameter is used in the command.</span></span>

<span data-ttu-id="7242b-175">Med parametern **Credential** kan du köra `Update-Help` kommandon med parametern **SourcePath** på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="7242b-175">The **Credential** parameter enables you to run `Update-Help` commands with the **SourcePath** parameter on remote computers.</span></span> <span data-ttu-id="7242b-176">Genom att ange explicita autentiseringsuppgifter kan du köra kommandot på en fjärrdator och komma åt en fil resurs på en tredje dator utan att ha påträffat ett nekat åtkomst fel eller använda CredSSP-autentisering för att delegera autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="7242b-176">By providing explicit credentials, you can run the command on a remote computer and access a file share on a third computer without encountering an access denied error or using CredSSP authentication to delegate credentials.</span></span>

<span data-ttu-id="7242b-177">Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7242b-177">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="7242b-178">Om du anger ett användar namn uppmanas du att ange lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="7242b-178">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="7242b-179">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="7242b-179">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="7242b-180">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="7242b-180">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Current user
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7242b-181">-Force</span><span class="sxs-lookup"><span data-stu-id="7242b-181">-Force</span></span>

<span data-ttu-id="7242b-182">Anger att denna cmdlet inte följer begränsningen en gång per dag, hoppar över versions kontroll och laddar ned filer som överskrider gränsen på 1 GB.</span><span class="sxs-lookup"><span data-stu-id="7242b-182">Indicates that this cmdlet doesn't follow the once-per-day limitation, skips version checking, and downloads files that exceed the 1 GB limit.</span></span>

<span data-ttu-id="7242b-183">Utan den här parametern `Update-Help` körs bara en gång under varje 24-timmarsperiod.</span><span class="sxs-lookup"><span data-stu-id="7242b-183">Without this parameter, `Update-Help` runs only once in each 24-hour period.</span></span> <span data-ttu-id="7242b-184">Hämtningar är begränsade till 1 GB okomprimerat innehåll per modul och hjälpfiler installeras bara när de är nyare än de befintliga filerna på datorn.</span><span class="sxs-lookup"><span data-stu-id="7242b-184">Downloads are limited to 1 GB of uncompressed content per module and help files are only installed when they're newer than the existing files on the computer.</span></span>

<span data-ttu-id="7242b-185">Gränsen för en gång per dag skyddar de servrar som är värdar för hjälpfilerna och gör det praktiskt för dig att lägga till ett `Update-Help` kommando i din PowerShell-profil utan att kostnaden för resurs kostnaden för upprepade anslutningar eller nedladdningar debiteras.</span><span class="sxs-lookup"><span data-stu-id="7242b-185">The once-per-day limit protects the servers that host the help files and makes it practical for you to add an `Update-Help` command to your PowerShell profile without incurring the resource cost of repeated connections or downloads.</span></span>

<span data-ttu-id="7242b-186">Om du vill uppdatera hjälpen för en modul i flera användar gränssnitts kulturer utan **Force** -parametern inkluderar du alla användar gränssnitts kulturer i samma kommando, till exempel:</span><span class="sxs-lookup"><span data-stu-id="7242b-186">To update help for a module in multiple UI cultures without the **Force** parameter, include all UI cultures in the same command, such as:</span></span>

`Update-Help -Module PSScheduledJobs -UICulture en-US, fr-FR, pt-BR`

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

### <span data-ttu-id="7242b-187">-FullyQualifiedModule</span><span class="sxs-lookup"><span data-stu-id="7242b-187">-FullyQualifiedModule</span></span>

<span data-ttu-id="7242b-188">Anger moduler med namn som anges i form av **ModuleSpecification** -objekt.</span><span class="sxs-lookup"><span data-stu-id="7242b-188">Specifies modules with names that are specified in the form of **ModuleSpecification** objects.</span></span>
<span data-ttu-id="7242b-189">Dessa moduler beskrivs i avsnittet anmärkningar i [ModuleSpecification-konstruktorn (hash)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span><span class="sxs-lookup"><span data-stu-id="7242b-189">These modules are described in the Remarks section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>

<span data-ttu-id="7242b-190">Parametern **FullyQualifiedModule** accepterar till exempel ett modulnamn som anges i formatet:</span><span class="sxs-lookup"><span data-stu-id="7242b-190">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in the format:</span></span>

`@{ModuleName = "modulename"; ModuleVersion = "version_number"}`

<span data-ttu-id="7242b-191">eller</span><span class="sxs-lookup"><span data-stu-id="7242b-191">or</span></span>

`@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}.`

<span data-ttu-id="7242b-192">**Modulnamn** och **ModuleVersion** krävs, men **GUID** är valfritt.</span><span class="sxs-lookup"><span data-stu-id="7242b-192">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span>

<span data-ttu-id="7242b-193">Du kan inte ange parametern **FullyQualifiedModule** i samma kommando som en **modul** -parameter.</span><span class="sxs-lookup"><span data-stu-id="7242b-193">You can't specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="7242b-194">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="7242b-194">-LiteralPath</span></span>

<span data-ttu-id="7242b-195">Anger mappen för uppdaterade hjälpfiler i stället för att ladda ned dem från Internet.</span><span class="sxs-lookup"><span data-stu-id="7242b-195">Specifies the folder for updated help files instead of downloading them from the internet.</span></span> <span data-ttu-id="7242b-196">Använd den här parametern eller **SourcePath** om du har använt `Save-Help` cmdleten för att hämta hjälpfiler till en katalog.</span><span class="sxs-lookup"><span data-stu-id="7242b-196">Use this parameter or **SourcePath** if you've used the `Save-Help` cmdlet to download help files to a directory.</span></span>

<span data-ttu-id="7242b-197">Du kan pipelina ett katalog objekt, till exempel från `Get-Item` `Get-ChildItem` cmdletarna eller, till `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="7242b-197">You can pipeline a directory object, such as from the `Get-Item` or `Get-ChildItem` cmdlets, to `Update-Help`.</span></span>

<span data-ttu-id="7242b-198">Till skillnad från värdet för **SourcePath** , används värdet för **LiteralPath** exakt som det skrivs.</span><span class="sxs-lookup"><span data-stu-id="7242b-198">Unlike the value of **SourcePath** , the value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="7242b-199">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="7242b-199">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="7242b-200">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="7242b-200">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="7242b-201">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="7242b-201">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="7242b-202">– Modul</span><span class="sxs-lookup"><span data-stu-id="7242b-202">-Module</span></span>

<span data-ttu-id="7242b-203">Uppdaterar hjälpen för de angivna modulerna.</span><span class="sxs-lookup"><span data-stu-id="7242b-203">Updates help for the specified modules.</span></span> <span data-ttu-id="7242b-204">Ange ett eller flera Modulnamn eller namn mönster i en kommaavgränsad lista eller ange en fil som visar ett modulnamn på varje rad.</span><span class="sxs-lookup"><span data-stu-id="7242b-204">Enter one or more module names or name patterns in a comma-separated list, or specify a file that lists one module name on each line.</span></span> <span data-ttu-id="7242b-205">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="7242b-205">Wildcard characters are permitted.</span></span> <span data-ttu-id="7242b-206">Du kan pipeline-moduler från `Get-Module` cmdlet: en till `Update-Help` cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="7242b-206">You can pipeline modules from the `Get-Module` cmdlet to the `Update-Help` cmdlet.</span></span>

<span data-ttu-id="7242b-207">De moduler som du anger måste vara installerade på datorn, men de behöver inte importeras till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="7242b-207">The modules that you specify must be installed on the computer, but they don't have to be imported into the current session.</span></span> <span data-ttu-id="7242b-208">Du kan ange vilken modul som helst i sessionen eller vilken modul som helst som är installerad på en plats som anges i `$env:PSModulePath` miljö variabeln.</span><span class="sxs-lookup"><span data-stu-id="7242b-208">You can specify any module in the session or any module that is installed in a location listed in the `$env:PSModulePath` environment variable.</span></span>

<span data-ttu-id="7242b-209">Värdet `*` (alla) försöker att uppdatera hjälpen för alla moduler som är installerade på datorn.</span><span class="sxs-lookup"><span data-stu-id="7242b-209">A value of `*` (all) attempts to update help for all modules that are installed on the computer.</span></span>
<span data-ttu-id="7242b-210">Moduler som inte stöder uppdaterbar hjälp ingår.</span><span class="sxs-lookup"><span data-stu-id="7242b-210">Modules that don't support Updatable Help are included.</span></span> <span data-ttu-id="7242b-211">Det här värdet kan generera fel när kommandot påträffar moduler som inte stöder uppdaterbar hjälp.</span><span class="sxs-lookup"><span data-stu-id="7242b-211">This value might generate errors when the command encounters modules that don't support Updatable Help.</span></span> <span data-ttu-id="7242b-212">Kör i stället `Update-Help` utan parametrar.</span><span class="sxs-lookup"><span data-stu-id="7242b-212">Instead, run `Update-Help` without parameters.</span></span>

<span data-ttu-id="7242b-213">Parametern **module** för `Update-Help` cmdleten accepterar inte den fullständiga sökvägen till en modul-fil eller modulens manifest fil.</span><span class="sxs-lookup"><span data-stu-id="7242b-213">The **Module** parameter of the `Update-Help` cmdlet doesn't accept the full path of a module file or module manifest file.</span></span> <span data-ttu-id="7242b-214">Om du vill uppdatera hjälpen för en modul som inte finns på en `$env:PSModulePath` plats importerar du modulen till den aktuella sessionen innan du kör `Update-Help` kommandot.</span><span class="sxs-lookup"><span data-stu-id="7242b-214">To update help for a module that isn't in a `$env:PSModulePath` location, import the module into the current session before you run the `Update-Help` command.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Name

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="7242b-215">– Rekursivt</span><span class="sxs-lookup"><span data-stu-id="7242b-215">-Recurse</span></span>

<span data-ttu-id="7242b-216">Utför en rekursiv sökning efter hjälpfilerna i den angivna katalogen.</span><span class="sxs-lookup"><span data-stu-id="7242b-216">Performs a recursive search for help files in the specified directory.</span></span> <span data-ttu-id="7242b-217">Den här parametern är endast giltig om parametern **SourcePath** används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="7242b-217">This parameter is valid only when the command uses the **SourcePath** parameter.</span></span>

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

### <span data-ttu-id="7242b-218">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="7242b-218">-Scope</span></span>

<span data-ttu-id="7242b-219">Anger system omfånget där hjälpen uppdateras.</span><span class="sxs-lookup"><span data-stu-id="7242b-219">Specifies the system scope where help is updated.</span></span> <span data-ttu-id="7242b-220">Uppdateringar i **allusers** -omfånget kräver administratörs behörighet för Windows-system.</span><span class="sxs-lookup"><span data-stu-id="7242b-220">Updates at the **AllUsers** scope require administrative privileges on Windows systems.</span></span> <span data-ttu-id="7242b-221">`-Scope`Parametern introducerades i PowerShell Core version 6,1.</span><span class="sxs-lookup"><span data-stu-id="7242b-221">The `-Scope` parameter was introduced in PowerShell Core version 6.1.</span></span>

<span data-ttu-id="7242b-222">**CurrentUser** är standard omfånget för hjälp av filer i PowerShell 6,1 och senare.</span><span class="sxs-lookup"><span data-stu-id="7242b-222">**CurrentUser** is the default scope for help files in PowerShell 6.1 and above.</span></span> <span data-ttu-id="7242b-223">**Allusers** kan anges för att installera eller uppdatera hjälpen för alla användare.</span><span class="sxs-lookup"><span data-stu-id="7242b-223">**AllUsers** can be specified to install or update help for all users.</span></span> <span data-ttu-id="7242b-224">Behörigheter för UNIX-system `sudo` krävs för att du ska kunna uppdatera hjälpen för alla användare.</span><span class="sxs-lookup"><span data-stu-id="7242b-224">On Unix systems `sudo` privileges are required to update help for all users.</span></span> <span data-ttu-id="7242b-225">Exempelvis: `sudo pwsh -c Update-Help`</span><span class="sxs-lookup"><span data-stu-id="7242b-225">For example: `sudo pwsh -c Update-Help`</span></span>

<span data-ttu-id="7242b-226">Godkända värden är:</span><span class="sxs-lookup"><span data-stu-id="7242b-226">The acceptable values are:</span></span>

- <span data-ttu-id="7242b-227">CurrentUser</span><span class="sxs-lookup"><span data-stu-id="7242b-227">CurrentUser</span></span>
- <span data-ttu-id="7242b-228">AllUsers</span><span class="sxs-lookup"><span data-stu-id="7242b-228">AllUsers</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.UpdateHelpScope
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: CurrentUser
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="7242b-229">-SourcePath</span><span class="sxs-lookup"><span data-stu-id="7242b-229">-SourcePath</span></span>

<span data-ttu-id="7242b-230">Anger en fil system katalog där `Update-Help` uppdaterade hjälpfiler hämtas, i stället för att de hämtas från Internet.</span><span class="sxs-lookup"><span data-stu-id="7242b-230">Specifies a file system folder where `Update-Help` gets updated help files, instead of downloading them from the internet.</span></span> <span data-ttu-id="7242b-231">Ange sökvägen till en mapp.</span><span class="sxs-lookup"><span data-stu-id="7242b-231">Enter the path of a folder.</span></span> <span data-ttu-id="7242b-232">Ange inte ett fil namn eller fil namns tillägg.</span><span class="sxs-lookup"><span data-stu-id="7242b-232">Don't specify a file name or file name extension.</span></span> <span data-ttu-id="7242b-233">Du kan pipelina en mapp, till exempel en från `Get-Item` -eller `Get-ChildItem` -cmdlet: ar, till `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="7242b-233">You can pipeline a folder, such as one from the `Get-Item` or `Get-ChildItem` cmdlets, to `Update-Help`.</span></span>

<span data-ttu-id="7242b-234">Som standard `Update-Help` hämtar de uppdaterade hjälpfilerna från Internet.</span><span class="sxs-lookup"><span data-stu-id="7242b-234">By default, `Update-Help` downloads updated help files from the internet.</span></span> <span data-ttu-id="7242b-235">Använd **SourcePath** när du har använt `Save-Help` cmdleten för att hämta uppdaterade hjälpfiler till en katalog.</span><span class="sxs-lookup"><span data-stu-id="7242b-235">Use **SourcePath** when you've used the `Save-Help` cmdlet to download updated help files to a directory.</span></span>

<span data-ttu-id="7242b-236">Om du vill ange ett standardvärde för **SourcePath** går du till **Grupprincip** , **dator konfiguration** och **anger standard Sök vägen för uppdatering-hjälpen**.</span><span class="sxs-lookup"><span data-stu-id="7242b-236">To specify a default value for **SourcePath** , go to **Group Policy** , **Computer Configuration** , and **Set the default source path for Update-Help**.</span></span> <span data-ttu-id="7242b-237">Den här grupprincip inställningen hindrar användare från `Update-Help` att använda för att hämta hjälpfiler från Internet.</span><span class="sxs-lookup"><span data-stu-id="7242b-237">This Group Policy setting prevents users from using `Update-Help` to download help files from the internet.</span></span>
<span data-ttu-id="7242b-238">Mer information finns i [about_Group_Policy_Settings](./About/about_Group_Policy_Settings.md).</span><span class="sxs-lookup"><span data-stu-id="7242b-238">For more information, see [about_Group_Policy_Settings](./About/about_Group_Policy_Settings.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases: Path

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7242b-239">– Värdet</span><span class="sxs-lookup"><span data-stu-id="7242b-239">-UICulture</span></span>

<span data-ttu-id="7242b-240">Anger GRÄNSSNITTs språk värden som `Update-Help` används för att hämta uppdaterade hjälpfiler.</span><span class="sxs-lookup"><span data-stu-id="7242b-240">Specifies UI culture values that `Update-Help` uses to get updated help files.</span></span> <span data-ttu-id="7242b-241">Ange en eller flera språk koder, till exempel **es-es** , en variabel som innehåller kultur objekt eller ett kommando som hämtar kultur objekt, till exempel ett `Get-Culture` eller- `Get-UICulture` kommando.</span><span class="sxs-lookup"><span data-stu-id="7242b-241">Enter one or more language codes, such as **es-ES** , a variable that contains culture objects, or a command that gets culture objects, such as a `Get-Culture` or `Get-UICulture` command.</span></span> <span data-ttu-id="7242b-242">Jokertecken är inte tillåtna och du kan inte skicka en del språk kod, till exempel **de**.</span><span class="sxs-lookup"><span data-stu-id="7242b-242">Wildcard characters aren't permitted and you can't submit a partial language code, such as **de**.</span></span>

<span data-ttu-id="7242b-243">Som standard `Update-Help` får hjälpfilerna i användar gränssnitts kulturen angetts för operativ systemet.</span><span class="sxs-lookup"><span data-stu-id="7242b-243">By default, `Update-Help` gets help files in the UI culture set for the operating system.</span></span> <span data-ttu-id="7242b-244">Om du anger parametern **värdet** letar du `Update-Help` bara efter hjälp för den angivna användar gränssnitts kulturen.</span><span class="sxs-lookup"><span data-stu-id="7242b-244">If you specify the **UICulture** parameter, `Update-Help` looks for help only for the specified UI culture.</span></span>

> [!NOTE]
> <span data-ttu-id="7242b-245">Ubuntu 18,04 ändrade standard språk inställningen till `C.UTF.8` , vilket inte är en känd kultur för användar gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="7242b-245">Ubuntu 18.04 changed the default locale setting to `C.UTF.8`, which is not a recognized UI culture.</span></span> <span data-ttu-id="7242b-246">`Update-Help` Det går tyst att ladda ned hjälpen om du inte använder den här parametern med ett språk som stöds `en-US` .</span><span class="sxs-lookup"><span data-stu-id="7242b-246">`Update-Help` silently fails to download help unless you use this parameter with a supported locale like `en-US`.</span></span> <span data-ttu-id="7242b-247">Detta kan inträffa på vilken plattform som helst som använder ett värde som inte stöds.</span><span class="sxs-lookup"><span data-stu-id="7242b-247">This could occur on any platform that uses an unsupported value.</span></span>

<span data-ttu-id="7242b-248">Kommandon som använder parametern **värdet** fungerar bara när modulen tillhandahåller hjälpfiler för den angivna kulturen för användar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="7242b-248">Commands that use the **UICulture** parameter succeed only when the module provides help files for the specified UI culture.</span></span> <span data-ttu-id="7242b-249">Om kommandot Miss lyckas eftersom den angivna användar gränssnitts kulturen inte stöds visas ett fel meddelande.</span><span class="sxs-lookup"><span data-stu-id="7242b-249">If the command fails because the specified UI culture isn't supported, an error message is displayed.</span></span>

```yaml
Type: System.Globalization.CultureInfo[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7242b-250">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="7242b-250">-UseDefaultCredentials</span></span>

<span data-ttu-id="7242b-251">Anger att `Update-Help` Kör kommandot, inklusive hämtning av Internet, med hjälp av den aktuella användarens autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="7242b-251">Indicates that `Update-Help` runs the command, including the internet download, by using the credentials of the current user.</span></span> <span data-ttu-id="7242b-252">Som standard körs kommandot utan explicita autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="7242b-252">By default, the command runs without explicit credentials.</span></span>

<span data-ttu-id="7242b-253">Den här parametern är endast effektiv när webb hämtningen använder NTLM (NT LAN Manager), Negotiate eller Kerberos-baserad autentisering.</span><span class="sxs-lookup"><span data-stu-id="7242b-253">This parameter is effective only when the web download uses NT LAN Manager (NTLM), negotiate, or Kerberos-based authentication.</span></span>

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

### <span data-ttu-id="7242b-254">-Confirm</span><span class="sxs-lookup"><span data-stu-id="7242b-254">-Confirm</span></span>

<span data-ttu-id="7242b-255">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7242b-255">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7242b-256">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="7242b-256">-WhatIf</span></span>

<span data-ttu-id="7242b-257">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="7242b-257">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="7242b-258">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="7242b-258">The cmdlet isn't run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="7242b-259">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7242b-259">CommonParameters</span></span>

<span data-ttu-id="7242b-260">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7242b-260">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7242b-261">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="7242b-261">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7242b-262">INDATA</span><span class="sxs-lookup"><span data-stu-id="7242b-262">INPUTS</span></span>

### <span data-ttu-id="7242b-263">System. IO. DirectoryInfo</span><span class="sxs-lookup"><span data-stu-id="7242b-263">System.IO.DirectoryInfo</span></span>

<span data-ttu-id="7242b-264">Du kan skicka en katalog Sök väg till `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="7242b-264">You can pipe a directory path to `Update-Help`.</span></span>

### <span data-ttu-id="7242b-265">System. Management. Automation. PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="7242b-265">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="7242b-266">Du kan skicka ett modul-objekt från `Get-Module` cmdlet: en till `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="7242b-266">You can pipe a module object from the `Get-Module` cmdlet to `Update-Help`.</span></span>

## <span data-ttu-id="7242b-267">UTDATA</span><span class="sxs-lookup"><span data-stu-id="7242b-267">OUTPUTS</span></span>

### <span data-ttu-id="7242b-268">Inget</span><span class="sxs-lookup"><span data-stu-id="7242b-268">None</span></span>

<span data-ttu-id="7242b-269">`Update-Help` genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="7242b-269">`Update-Help` doesn't generate any output.</span></span>

## <span data-ttu-id="7242b-270">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="7242b-270">NOTES</span></span>

<span data-ttu-id="7242b-271">Om du vill uppdatera hjälpen för PowerShell Core-modulerna som innehåller de kommandon som är installerade med PowerShell eller någon modul i `$PSHOME\Modules` katalogen startar du PowerShell med alternativet att **köra som administratör**.</span><span class="sxs-lookup"><span data-stu-id="7242b-271">To update help for the PowerShell Core modules, that contain the commands that are installed with PowerShell, or any module in the `$PSHOME\Modules` directory, start PowerShell with the option to **Run as administrator**.</span></span>

<span data-ttu-id="7242b-272">Endast medlemmar i gruppen Administratörer på datorn kan uppdatera hjälpen för PowerShell Core-modulerna, kommandon som installeras tillsammans med PowerShell och för moduler i `$PSHOME\Modules` mappen.</span><span class="sxs-lookup"><span data-stu-id="7242b-272">Only members of the Administrators group on the computer can update help for the PowerShell Core modules, the commands that are installed together with PowerShell, and for modules in the `$PSHOME\Modules` folder.</span></span> <span data-ttu-id="7242b-273">Om du inte har behörighet att uppdatera hjälpfiler kan du läsa hjälpfilerna online.</span><span class="sxs-lookup"><span data-stu-id="7242b-273">If you don't have permission to update help files, you can read the help files online.</span></span> <span data-ttu-id="7242b-274">Till exempel `Get-Help Update-Help -Online`.</span><span class="sxs-lookup"><span data-stu-id="7242b-274">For example, `Get-Help Update-Help -Online`.</span></span>

<span data-ttu-id="7242b-275">Moduler är den minsta enheten för uppdaterbar hjälp.</span><span class="sxs-lookup"><span data-stu-id="7242b-275">Modules are the smallest unit of updatable help.</span></span> <span data-ttu-id="7242b-276">Du kan inte uppdatera hjälpen för en viss cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7242b-276">You can't update help for a particular cmdlet.</span></span> <span data-ttu-id="7242b-277">Om du vill hitta modulen som innehåller en viss cmdlet använder du egenskapen **Modulnamn** för `Get-Command` cmdleten, till exempel `(Get-Command Update-Help).ModuleName` .</span><span class="sxs-lookup"><span data-stu-id="7242b-277">To find the module that contains a particular cmdlet, use the **ModuleName** property of the `Get-Command` cmdlet, for example, `(Get-Command Update-Help).ModuleName`.</span></span>

<span data-ttu-id="7242b-278">Eftersom hjälpfiler installeras i modul-katalogen `Update-Help` kan cmdleten bara installera den uppdaterade hjälp filen för moduler som är installerade på datorn.</span><span class="sxs-lookup"><span data-stu-id="7242b-278">Because help files are installed in the module directory, the `Update-Help` cmdlet can install updated help file only for modules that are installed on the computer.</span></span> <span data-ttu-id="7242b-279">Men `Save-Help` cmdleten kan spara hjälp för moduler som inte är installerade på datorn.</span><span class="sxs-lookup"><span data-stu-id="7242b-279">However, the `Save-Help` cmdlet can save help for modules that aren't installed on the computer.</span></span>

<span data-ttu-id="7242b-280">Om `Update-Help` det inte går att hitta uppdaterade hjälpfiler för en modul, eller om det inte går att hitta en uppdaterad hjälp på det angivna språket, fortsätter den tyst utan att ett fel meddelande visas.</span><span class="sxs-lookup"><span data-stu-id="7242b-280">If `Update-Help` can't find updated help files for a module, or can't find updated help in the specified language, it continues silently without displaying an error message.</span></span> <span data-ttu-id="7242b-281">Använd **verbose** -parametern för att se information om status och förlopp.</span><span class="sxs-lookup"><span data-stu-id="7242b-281">To see status and progress details, use the **Verbose** parameter.</span></span>

<span data-ttu-id="7242b-282">`Update-Help`Cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="7242b-282">The `Update-Help` cmdlet was introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="7242b-283">Den fungerar inte i tidigare versioner av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7242b-283">It doesn't work in earlier versions of PowerShell.</span></span> <span data-ttu-id="7242b-284">På datorer som har både Windows PowerShell 2,0 och Windows PowerShell 3,0 använder du `Update-Help` cmdleten i en Windows PowerShell 3,0-session för att hämta och uppdatera hjälpfiler.</span><span class="sxs-lookup"><span data-stu-id="7242b-284">On computers that have both Windows PowerShell 2.0 and Windows PowerShell 3.0, use the `Update-Help` cmdlet in a Windows PowerShell 3.0 session to download and update help files.</span></span> <span data-ttu-id="7242b-285">Hjälpfilerna är tillgängliga för både Windows PowerShell 2,0 och Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="7242b-285">The help files are available to both Windows PowerShell 2.0 and Windows PowerShell 3.0.</span></span>

<span data-ttu-id="7242b-286">`Update-Help` `Save-Help` Cmdletarna och använder följande portar för att hämta hjälpfiler: port 80 för http och port 443 för https.</span><span class="sxs-lookup"><span data-stu-id="7242b-286">The `Update-Help` and `Save-Help` cmdlets use the following ports to download help files: Port 80 for HTTP and port 443 for HTTPS.</span></span>

<span data-ttu-id="7242b-287">`Update-Help` stöder alla moduler och snapin-moduler för PowerShell Core. Den har inte stöd för några andra snapin-moduler.</span><span class="sxs-lookup"><span data-stu-id="7242b-287">`Update-Help` supports all modules and the PowerShell Core snap-ins. It doesn't support any other snap-ins.</span></span>

<span data-ttu-id="7242b-288">Om du vill uppdatera hjälpen för en modul på en plats som inte finns med i `$env:PSModulePath` miljövariabeln importerar du modulen till den aktuella sessionen och kör sedan ett `Update-Help` kommando.</span><span class="sxs-lookup"><span data-stu-id="7242b-288">To update help for a module in a location that isn't listed in the `$env:PSModulePath` environment variable, import the module into the current session and then run an `Update-Help` command.</span></span> <span data-ttu-id="7242b-289">Kör `Update-Help` utan parametrar eller Använd parametern **module** för att ange modulnamnet.</span><span class="sxs-lookup"><span data-stu-id="7242b-289">Run `Update-Help` without parameters or use the **Module** parameter to specify the module name.</span></span> <span data-ttu-id="7242b-290">Parametern **module** för `Update-Help` `Save-Help` cmdletarna och accepterar inte den fullständiga sökvägen till en modul fil eller modulens manifest fil.</span><span class="sxs-lookup"><span data-stu-id="7242b-290">The **Module** parameter of the `Update-Help` and `Save-Help` cmdlets doesn't accept the full path of a module file or module manifest file.</span></span>

<span data-ttu-id="7242b-291">Alla moduler kan stödja uppdaterings bar hjälp.</span><span class="sxs-lookup"><span data-stu-id="7242b-291">Any module can support Updatable Help.</span></span> <span data-ttu-id="7242b-292">Instruktioner för att stödja uppdaterings bar hjälp i de moduler som du skapar finns i [support uppdaterings bara hjälp](/powershell/scripting/developer/module/supporting-updatable-help).</span><span class="sxs-lookup"><span data-stu-id="7242b-292">For instructions for supporting Updatable Help in the modules that you author, see [Supporting Updatable Help](/powershell/scripting/developer/module/supporting-updatable-help).</span></span>

<span data-ttu-id="7242b-293">`Update-Help` `Save-Help` Cmdletarna och stöds inte på Windows Preinstallation Environment (Windows PE).</span><span class="sxs-lookup"><span data-stu-id="7242b-293">The `Update-Help` and `Save-Help` cmdlets are not supported on Windows Preinstallation Environment (Windows PE).</span></span>

## <span data-ttu-id="7242b-294">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="7242b-294">RELATED LINKS</span></span>

[<span data-ttu-id="7242b-295">Get-Culture</span><span class="sxs-lookup"><span data-stu-id="7242b-295">Get-Culture</span></span>](../Microsoft.PowerShell.Utility/Get-Culture.md)

[<span data-ttu-id="7242b-296">Get – hjälp</span><span class="sxs-lookup"><span data-stu-id="7242b-296">Get-Help</span></span>](Get-Help.md)

[<span data-ttu-id="7242b-297">Hämta modul</span><span class="sxs-lookup"><span data-stu-id="7242b-297">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="7242b-298">Get-värdet</span><span class="sxs-lookup"><span data-stu-id="7242b-298">Get-UICulture</span></span>](../Microsoft.PowerShell.Utility/Get-UICulture.md)

[<span data-ttu-id="7242b-299">Start – jobb</span><span class="sxs-lookup"><span data-stu-id="7242b-299">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="7242b-300">Spara – hjälp</span><span class="sxs-lookup"><span data-stu-id="7242b-300">Save-Help</span></span>](Save-Help.md)
