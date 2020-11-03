---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/16/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/update-help?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Update-Help
ms.openlocfilehash: 4ef0865e81e01746fed77b73e265e68086a7a9e1
ms.sourcegitcommit: d3f78120bdc9096c72aa0dfdbdd91efaf254c738
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/04/2020
ms.locfileid: "93268875"
---
# <span data-ttu-id="f5861-103">Update-Help</span><span class="sxs-lookup"><span data-stu-id="f5861-103">Update-Help</span></span>

## <span data-ttu-id="f5861-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="f5861-104">SYNOPSIS</span></span>
<span data-ttu-id="f5861-105">Laddar ned och installerar de senaste hjälpfilerna på din dator.</span><span class="sxs-lookup"><span data-stu-id="f5861-105">Downloads and installs the newest help files on your computer.</span></span>

## <span data-ttu-id="f5861-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f5861-106">SYNTAX</span></span>

### <span data-ttu-id="f5861-107">Sökväg (standard)</span><span class="sxs-lookup"><span data-stu-id="f5861-107">Path (Default)</span></span>

```
Update-Help [[-Module] <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [[-SourcePath] <String[]>] [-Recurse] [[-UICulture] <CultureInfo[]>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f5861-108">LiteralPath</span><span class="sxs-lookup"><span data-stu-id="f5861-108">LiteralPath</span></span>

```
Update-Help [[-Module] <String[]>] [-FullyQualifiedModule <ModuleSpecification[]>]
 [-LiteralPath <String[]>] [-Recurse] [[-UICulture] <CultureInfo[]>] [-Credential <PSCredential>]
 [-UseDefaultCredentials] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f5861-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="f5861-109">DESCRIPTION</span></span>

<span data-ttu-id="f5861-110">`Update-Help`Cmdlet: en laddar ned de senaste hjälpfilerna för PowerShell-moduler och installerar dem på din dator.</span><span class="sxs-lookup"><span data-stu-id="f5861-110">The `Update-Help` cmdlet downloads the newest help files for PowerShell modules and installs them on your computer.</span></span> <span data-ttu-id="f5861-111">Du behöver inte starta om PowerShell för att ändringen ska börja gälla.</span><span class="sxs-lookup"><span data-stu-id="f5861-111">You need not restart PowerShell to make the change effective.</span></span> <span data-ttu-id="f5861-112">Du kan använda `Get-Help` cmdleten för att visa de nya hjälpfilerna omedelbart.</span><span class="sxs-lookup"><span data-stu-id="f5861-112">You can use the `Get-Help` cmdlet to view the new help files immediately.</span></span>

<span data-ttu-id="f5861-113">`Update-Help` kontrollerar versionen för hjälpfilerna på din dator.</span><span class="sxs-lookup"><span data-stu-id="f5861-113">`Update-Help` checks the version of the help files on your computer.</span></span> <span data-ttu-id="f5861-114">Om du inte har hjälp filer för en modul eller om dina hjälpfiler är inaktuella, `Update-Help` laddar ned de senaste hjälpfilerna.</span><span class="sxs-lookup"><span data-stu-id="f5861-114">If you don't have help files for a module or if your help files are outdated, `Update-Help` downloads the newest help files.</span></span> <span data-ttu-id="f5861-115">Hjälpfilerna kan laddas ned och installeras från Internet eller en fil resurs.</span><span class="sxs-lookup"><span data-stu-id="f5861-115">The help files can be downloaded and installed from the internet or a file share.</span></span>

<span data-ttu-id="f5861-116">Utan parametrar `Update-Help` uppdaterar hjälpfilerna för moduler i sessionen och för alla installerade moduler som stöder uppdaterbar hjälp.</span><span class="sxs-lookup"><span data-stu-id="f5861-116">Without parameters, `Update-Help` updates the help files for modules in the session and for all installed modules that support Updatable Help.</span></span> <span data-ttu-id="f5861-117">Moduler som är installerade men inte inlästa i den aktuella sessionen ingår.</span><span class="sxs-lookup"><span data-stu-id="f5861-117">Modules that are installed but not loaded in the current session are included.</span></span> <span data-ttu-id="f5861-118">PowerShell-moduler lagras på en plats som anges i `$env:PSModulePath` miljö variabeln.</span><span class="sxs-lookup"><span data-stu-id="f5861-118">PowerShell modules are stored in a location listed in the `$env:PSModulePath` environment variable.</span></span> <span data-ttu-id="f5861-119">Mer information finns i [about_Updatable_Help](./About/about_Updatable_Help.md).</span><span class="sxs-lookup"><span data-stu-id="f5861-119">For more information, see [about_Updatable_Help](./About/about_Updatable_Help.md).</span></span>

<span data-ttu-id="f5861-120">Du kan använda parametern **modul** för att uppdatera hjälpfiler för en viss modul.</span><span class="sxs-lookup"><span data-stu-id="f5861-120">You can use the **Module** parameter to update help files for a particular module.</span></span> <span data-ttu-id="f5861-121">Använd parametern **värdet** för att hämta hjälpfiler på flera språk och nationella inställningar.</span><span class="sxs-lookup"><span data-stu-id="f5861-121">Use the **UICulture** parameter to download help files in multiple languages and locales.</span></span>

<span data-ttu-id="f5861-122">Du kan också använda `Update-Help` på datorer som inte är anslutna till Internet.</span><span class="sxs-lookup"><span data-stu-id="f5861-122">You can also use `Update-Help` on computers that are not connected to the internet.</span></span> <span data-ttu-id="f5861-123">Använd först cmdlet: en `Save-Help` för att hämta hjälpfiler från Internet och spara dem i en delad mapp som är tillgänglig för datorn som inte är ansluten till Internet.</span><span class="sxs-lookup"><span data-stu-id="f5861-123">First, use the `Save-Help`cmdlet to download help files from the internet and save them in a shared folder that is accessible to the system not connected to the internet.</span></span> <span data-ttu-id="f5861-124">Använd sedan **SourcePath** -parametern för `Update-Help` för att ladda ned de uppdaterade hjälpfilerna från den delade och installera dem på datorn.</span><span class="sxs-lookup"><span data-stu-id="f5861-124">Then use the **SourcePath** parameter of `Update-Help` to download the updated help files from the shared and install them on the computer.</span></span>

<span data-ttu-id="f5861-125">Du kan automatisera hjälp uppdateringar genom att lägga till `Update-Help` cmdleten i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="f5861-125">You can automate help updates by adding the `Update-Help` cmdlet to your PowerShell profile.</span></span> <span data-ttu-id="f5861-126">Som standard `Update-Help` körs bara en tid per dag på varje dator.</span><span class="sxs-lookup"><span data-stu-id="f5861-126">By default, `Update-Help` runs only one time per day on each computer.</span></span> <span data-ttu-id="f5861-127">Använd parametern **Force** om du vill åsidosätta en begränsning per dag.</span><span class="sxs-lookup"><span data-stu-id="f5861-127">To override the once-per-day limit, use the **Force** parameter.</span></span>

<span data-ttu-id="f5861-128">`Update-Help`Cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="f5861-128">The `Update-Help` cmdlet was introduced in Windows PowerShell 3.0.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f5861-129">`Update-Help` kräver administratörs behörighet.</span><span class="sxs-lookup"><span data-stu-id="f5861-129">`Update-Help` requires administrative privileges.</span></span>
>
> <span data-ttu-id="f5861-130">Du måste vara medlem i gruppen Administratörer på datorn för att kunna uppdatera hjälpfilerna för PowerShell Core-modulerna.</span><span class="sxs-lookup"><span data-stu-id="f5861-130">You must be a member of the Administrators group on the computer to update the help files for the PowerShell Core modules.</span></span>
>
> <span data-ttu-id="f5861-131">Om du vill hämta eller uppdatera hjälpfilerna för moduler i installations katalogen för PowerShell ( `$PSHOME\Modules` ), inklusive PowerShell-modulerna, startar du PowerShell med alternativet Kör som administratör.</span><span class="sxs-lookup"><span data-stu-id="f5861-131">To download or update the help files for modules in the PowerShell installation directory (`$PSHOME\Modules`), including the PowerShell Core modules, start PowerShell by using the Run as administrator option.</span></span>
> <span data-ttu-id="f5861-132">Till exempel: `Start-Process powershell.exe -Verb RunAs`.</span><span class="sxs-lookup"><span data-stu-id="f5861-132">For example: `Start-Process powershell.exe -Verb RunAs`.</span></span>
>
> <span data-ttu-id="f5861-133">Du kan också uppdatera hjälpfilerna med hjälp av meny alternativet Uppdatera Windows PowerShell-hjälp i Hjälp-menyn i Windows PowerShell ISE (Integrated Scripting Environment).</span><span class="sxs-lookup"><span data-stu-id="f5861-133">You can also update help files by using the Update Windows PowerShell Help menu item in the Help menu in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>
>
> <span data-ttu-id="f5861-134">Windows PowerShell-hjälpen för Update kör en `Update-Help` cmdlet utan parametrar.</span><span class="sxs-lookup"><span data-stu-id="f5861-134">The Update Windows PowerShell Help item runs an `Update-Help` cmdlet without parameters.</span></span>
> <span data-ttu-id="f5861-135">Om du vill uppdatera hjälp för moduler i `$PSHOME` katalogen startar du Windows PowerShell ISE med hjälp av alternativet Kör som administratör.</span><span class="sxs-lookup"><span data-stu-id="f5861-135">To update help for modules in the `$PSHOME` directory, start Windows PowerShell ISE by using the Run as administrator option.</span></span>

## <span data-ttu-id="f5861-136">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="f5861-136">EXAMPLES</span></span>

### <span data-ttu-id="f5861-137">Exempel 1: uppdatera hjälpfilerna för alla moduler</span><span class="sxs-lookup"><span data-stu-id="f5861-137">Example 1: Update help files for all modules</span></span>

<span data-ttu-id="f5861-138">`Update-Help`Cmdleten uppdaterar hjälpfiler för installerade moduler som stöder uppdaterings bar hjälp.</span><span class="sxs-lookup"><span data-stu-id="f5861-138">The `Update-Help` cmdlet updates help files for installed modules that support Updatable Help.</span></span> <span data-ttu-id="f5861-139">Kultur språket för användar gränssnittet (UI) har angetts i operativ systemet.</span><span class="sxs-lookup"><span data-stu-id="f5861-139">The user-interface (UI) culture language is set in the operating system.</span></span>

```powershell
Update-Help
```

### <span data-ttu-id="f5861-140">Exempel 2: uppdatera hjälpfiler för angivna moduler</span><span class="sxs-lookup"><span data-stu-id="f5861-140">Example 2: Update help files for specified modules</span></span>

<span data-ttu-id="f5861-141">`Update-Help`Cmdleten uppdaterar endast hjälp filer för Modulnamn som börjar med **Microsoft. PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="f5861-141">The `Update-Help` cmdlet updates help files only for module names that begin with **Microsoft.PowerShell**.</span></span>

```powershell
Update-Help -Module Microsoft.PowerShell*
```

### <span data-ttu-id="f5861-142">Exempel 3: uppdatera hjälpfiler för olika språk</span><span class="sxs-lookup"><span data-stu-id="f5861-142">Example 3: Update help files for different languages</span></span>

<span data-ttu-id="f5861-143">`Update-Help`Cmdleten uppdaterar hjälpfilerna för japanska (ja-JP) och engelska (en-US) för alla moduler.</span><span class="sxs-lookup"><span data-stu-id="f5861-143">The `Update-Help` cmdlet updates the Japanese (ja-JP) and English (en-US) help files for all modules.</span></span>

<span data-ttu-id="f5861-144">Om en modul inte tillhandahåller hjälp filer för en angiven användar gränssnitts kultur visas ett fel meddelande för modulen och användar gränssnitts kulturen.</span><span class="sxs-lookup"><span data-stu-id="f5861-144">If a module doesn't provide help files for a specified UI culture, an error message is displayed for the module and UI culture.</span></span> <span data-ttu-id="f5861-145">I det här exemplet anger fel meddelandet att hjälpfilerna för **Ja-JP** inte hittades för modulen **Microsoft. PowerShell. Utility**.</span><span class="sxs-lookup"><span data-stu-id="f5861-145">In this example, the error message indicates that the **ja-JP** help files were not found for module **Microsoft.PowerShell.Utility**.</span></span>

```powershell
Update-Help -UICulture ja-JP, en-US
```

```Output
Update-Help : Failed to update Help for the module(s) 'Microsoft.PowerShell.Utility' with UI culture(s) {ja-JP}
No UI culture was found that matches the following pattern: ja-JP.
```

### <span data-ttu-id="f5861-146">Exempel 4: uppdatera hjälpfiler automatiskt</span><span class="sxs-lookup"><span data-stu-id="f5861-146">Example 4: Update help files automatically</span></span>

<span data-ttu-id="f5861-147">I det här exemplet skapas ett schemalagt jobb som uppdaterar hjälpen för alla moduler varje dag kl. 3:00.</span><span class="sxs-lookup"><span data-stu-id="f5861-147">This example creates a scheduled job that updates help for all modules every day at 3:00 AM.</span></span>

```powershell
$jobParams = @{
  Name = 'UpdateHelpJob'
  Credential = 'Domain01\User01'
  ScriptBlock = '{Update-Help}'
  Trigger = (New-JobTrigger -Daily -At "3 AM")
}
Register-ScheduledJob @jobParams
```

```Output
Id         Name            JobTriggers     Command                                  Enabled
--         ----            -----------     -------                                  -------
1          UpdateHelpJob   1               Update-Help                              True
```

<span data-ttu-id="f5861-148">`Register-ScheduledJob`Cmdleten skapar ett schemalagt jobb som kör ett `Update-Help` kommando.</span><span class="sxs-lookup"><span data-stu-id="f5861-148">The `Register-ScheduledJob` cmdlet creates a scheduled job that runs an `Update-Help` command.</span></span> <span data-ttu-id="f5861-149">Kommandot använder parametern **Credential** för att köra `Update-Help` genom att använda autentiseringsuppgifterna för en medlem i gruppen Administratörer på datorn.</span><span class="sxs-lookup"><span data-stu-id="f5861-149">The command uses the **Credential** parameter to run `Update-Help` by using the credentials of a member of the Administrators group on the computer.</span></span> <span data-ttu-id="f5861-150">Värdet för **Utlösar** -parametern är ett `New-JobTrigger` kommando som skapar en jobb utlösare som startar jobbet varje dag kl. 3:00.</span><span class="sxs-lookup"><span data-stu-id="f5861-150">The value of the **Trigger** parameter is a `New-JobTrigger` command that creates a job trigger that starts the job every day at 3:00 AM.</span></span>

<span data-ttu-id="f5861-151">Kör `Register-ScheduledJob` -kommandot genom att starta PowerShell med hjälp av alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="f5861-151">To run the `Register-ScheduledJob` command, start PowerShell by using the **Run as administrator** option.</span></span> <span data-ttu-id="f5861-152">I PowerShell uppmanas du att ange lösen ordet för den användare som anges i parametern **Credential** .</span><span class="sxs-lookup"><span data-stu-id="f5861-152">PowerShell prompts you for the password of the user specified in the **Credential** parameter.</span></span> <span data-ttu-id="f5861-153">Autentiseringsuppgifterna lagras med det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="f5861-153">The credentials are stored with the scheduled job.</span></span> <span data-ttu-id="f5861-154">Du tillfrågas inte när jobbet körs.</span><span class="sxs-lookup"><span data-stu-id="f5861-154">You aren't prompted when the job runs.</span></span>

<span data-ttu-id="f5861-155">Du kan använda `Get-ScheduledJob` cmdleten för att visa det schemalagda jobbet, använda `Set-ScheduledJob` cmdleten för att ändra det och använda `Unregister-ScheduledJob` cmdleten för att ta bort den.</span><span class="sxs-lookup"><span data-stu-id="f5861-155">You can use the `Get-ScheduledJob` cmdlet to view the scheduled job, use the `Set-ScheduledJob` cmdlet to change it, and use the `Unregister-ScheduledJob` cmdlet to delete it.</span></span> <span data-ttu-id="f5861-156">Du kan också visa och hantera det schemalagda jobbet i Schemaläggaren på följande sökväg:</span><span class="sxs-lookup"><span data-stu-id="f5861-156">You can also view and manage the scheduled job in Task Scheduler in the following path:</span></span>

<span data-ttu-id="f5861-157">`Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs`.</span><span class="sxs-lookup"><span data-stu-id="f5861-157">`Task Scheduler Library\Microsoft\Windows\PowerShell\ScheduledJobs`.</span></span>

### <span data-ttu-id="f5861-158">Exempel 5: uppdatera hjälpfiler på flera datorer från en fil resurs</span><span class="sxs-lookup"><span data-stu-id="f5861-158">Example 5: Update help files on multiple computers from a file share</span></span>

<span data-ttu-id="f5861-159">I det här exemplet hämtas uppdaterade hjälpfiler från Internet och sparas i en fil resurs.</span><span class="sxs-lookup"><span data-stu-id="f5861-159">In this example, updated help files are downloaded from the internet and saved in a file share.</span></span> <span data-ttu-id="f5861-160">Användarautentiseringsuppgifter krävs som har behörighet att komma åt fil resursen och installera uppdateringar.</span><span class="sxs-lookup"><span data-stu-id="f5861-160">User credentials are needed that have permissions to access the file share and install updates.</span></span> <span data-ttu-id="f5861-161">När en fil resurs används är det möjligt att uppdatera datorer som finns bakom brand väggar eller inte är anslutna till Internet.</span><span class="sxs-lookup"><span data-stu-id="f5861-161">When a file share is used, it's possible to update computers that are behind firewalls or aren't connected to the internet.</span></span>

```powershell
Save-Help -DestinationPath \\Server01\Share\PSHelp -Credential Domain01\Admin01
Invoke-Command -ComputerName (Get-Content Servers.txt) -ScriptBlock {
     Update-Help -SourcePath \\Server01\Share\PSHelp -Credential Domain01\Admin01
}
```

<span data-ttu-id="f5861-162">`Save-Help`Kommandot laddar ned de senaste hjälpfilerna för alla moduler som stöder uppdaterings bar hjälp.</span><span class="sxs-lookup"><span data-stu-id="f5861-162">The `Save-Help` command downloads the newest help files for all modules that support Updatable Help.</span></span>
<span data-ttu-id="f5861-163">Parametern **DestinationPath** sparar filerna i `\\Server01\Share\PSHelp` fil resursen.</span><span class="sxs-lookup"><span data-stu-id="f5861-163">The **DestinationPath** parameter saves the files in the `\\Server01\Share\PSHelp` file share.</span></span> <span data-ttu-id="f5861-164">Parametern **Credential** anger en användare som har behörighet att komma åt fil resursen.</span><span class="sxs-lookup"><span data-stu-id="f5861-164">The **Credential** parameter specifies a user who has permission to access the file share.</span></span>

<span data-ttu-id="f5861-165">`Invoke-Command`Cmdleten kör `Update-Help` fjärrkommandon på flera datorer.</span><span class="sxs-lookup"><span data-stu-id="f5861-165">The `Invoke-Command` cmdlet runs remote `Update-Help` commands on multiple computers.</span></span> <span data-ttu-id="f5861-166">Parametern **computername** hämtar en lista över fjärrdatorer från **Servers.txt** -filen.</span><span class="sxs-lookup"><span data-stu-id="f5861-166">The **ComputerName** parameter gets a list of remote computers from the **Servers.txt** file.</span></span> <span data-ttu-id="f5861-167">Parametern **script block** kör `Update-Help` kommandot och använder parametern **SourcePath** för att ange den fil resurs som innehåller de uppdaterade hjälpfilerna.</span><span class="sxs-lookup"><span data-stu-id="f5861-167">The **ScriptBlock** parameter runs the `Update-Help` command and uses the **SourcePath** parameter to specify the file share that contains the updated help files.</span></span> <span data-ttu-id="f5861-168">Parametern **Credential** anger en användare som kan komma åt fil resursen och köra `Update-Help` fjärrkommandot.</span><span class="sxs-lookup"><span data-stu-id="f5861-168">The **Credential** parameter specifies a user who can access the file share and run the remote `Update-Help` command.</span></span>

### <span data-ttu-id="f5861-169">Exempel 6: Hämta en lista över uppdaterade hjälpfiler</span><span class="sxs-lookup"><span data-stu-id="f5861-169">Example 6: Get a list of updated help files</span></span>

<span data-ttu-id="f5861-170">`Update-Help`Cmdleten uppdaterar hjälpen för en angiven modul.</span><span class="sxs-lookup"><span data-stu-id="f5861-170">The `Update-Help` cmdlet updates help for a specified module.</span></span> <span data-ttu-id="f5861-171">Cmdleten använder den **utförliga** gemensamma parametern för att visa en lista med de hjälpfiler som uppdaterades.</span><span class="sxs-lookup"><span data-stu-id="f5861-171">The cmdlet uses the **Verbose** common parameter to display the list of help files that were updated.</span></span> <span data-ttu-id="f5861-172">Du kan använda **utförligt** för att visa utdata för alla hjälpfiler eller hjälp filer för en speciell modul.</span><span class="sxs-lookup"><span data-stu-id="f5861-172">You can use **Verbose** to view output for all help files or help files for a specific module.</span></span>

<span data-ttu-id="f5861-173">Utan **verbose** -parametern `Update-Help` visar inte kommandots resultat.</span><span class="sxs-lookup"><span data-stu-id="f5861-173">Without the **Verbose** parameter, `Update-Help` doesn't display the results of the command.</span></span> <span data-ttu-id="f5861-174">Utdata för **utförlig** parameter är användbart för att verifiera att hjälpfilerna har uppdaterats eller om den senaste versionen är installerad.</span><span class="sxs-lookup"><span data-stu-id="f5861-174">The **Verbose** parameter output is useful to verify that the help files were updated or if the latest version is installed.</span></span>

```powershell
Update-Help -Module Microsoft.PowerShell.Utility -Verbose
```

### <span data-ttu-id="f5861-175">Exempel 7: hitta moduler som stöder uppdaterbar hjälp</span><span class="sxs-lookup"><span data-stu-id="f5861-175">Example 7: Find modules that support Updatable Help</span></span>

<span data-ttu-id="f5861-176">I det här exemplet visas moduler som stöder uppdaterbar hjälp.</span><span class="sxs-lookup"><span data-stu-id="f5861-176">This example lists modules that support Updatable Help.</span></span> <span data-ttu-id="f5861-177">Kommandot använder modulens **HelpInfoUri** -egenskap för att identifiera moduler som stöder uppdaterbar hjälp.</span><span class="sxs-lookup"><span data-stu-id="f5861-177">The command uses the module's **HelpInfoUri** property to identify modules that support Updatable Help.</span></span> <span data-ttu-id="f5861-178">Egenskapen **HelpInfoUri** innehåller en adress som omdirigeras när `Update-Help` cmdleten körs.</span><span class="sxs-lookup"><span data-stu-id="f5861-178">The **HelpInfoUri** property contains an address that is redirected when the `Update-Help` cmdlet is run.</span></span>

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

### <span data-ttu-id="f5861-179">Exempel 8: uppdaterade hjälp filer för inventering</span><span class="sxs-lookup"><span data-stu-id="f5861-179">Example 8: Inventory updated help files</span></span>

<span data-ttu-id="f5861-180">I det här exemplet skapar skriptet `Get-UpdateHelpVersion.ps1` en inventering av de uppdaterbara hjälpfilerna för varje modul och deras versions nummer.</span><span class="sxs-lookup"><span data-stu-id="f5861-180">In this example, the script `Get-UpdateHelpVersion.ps1` creates an inventory of the Updatable Help files for each module and their version numbers.</span></span>

<span data-ttu-id="f5861-181">Skriptet identifierar moduler som stöder uppdaterbar hjälp med hjälp av egenskapen **HelpInfoUri** för moduler.</span><span class="sxs-lookup"><span data-stu-id="f5861-181">The script identifies modules that support Updatable Help by using the **HelpInfoUri** property of modules.</span></span> <span data-ttu-id="f5861-182">För moduler som stöder uppdaterbar hjälp söker skriptet efter och tolkar hjälp informations filen (\* helpinfo.xml) för att hitta det senaste versions numret.</span><span class="sxs-lookup"><span data-stu-id="f5861-182">For modules that support Updatable Help, the script looks for and parses the help information file (\*helpinfo.xml) to find the latest version number.</span></span>

<span data-ttu-id="f5861-183">Skriptet använder klassen **PSCustomObject** och en hash-tabell för att skapa ett anpassat utgående objekt.</span><span class="sxs-lookup"><span data-stu-id="f5861-183">The script uses the **PSCustomObject** class and a hash table to create a custom output object.</span></span>

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

## <span data-ttu-id="f5861-184">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="f5861-184">PARAMETERS</span></span>

### <span data-ttu-id="f5861-185">-Credential</span><span class="sxs-lookup"><span data-stu-id="f5861-185">-Credential</span></span>

<span data-ttu-id="f5861-186">Anger autentiseringsuppgifter för en användare som har behörighet att komma åt fil system platsen som anges av **SourcePath**.</span><span class="sxs-lookup"><span data-stu-id="f5861-186">Specifies credentials of a user who has permission to access the file system location specified by **SourcePath**.</span></span> <span data-ttu-id="f5861-187">Den här parametern är endast giltig när **SourcePath** -eller **LiteralPath** -parametern används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="f5861-187">This parameter is valid only when the **SourcePath** or **LiteralPath** parameter is used in the command.</span></span>

<span data-ttu-id="f5861-188">Med parametern **Credential** kan du köra `Update-Help` kommandon med parametern **SourcePath** på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="f5861-188">The **Credential** parameter enables you to run `Update-Help` commands with the **SourcePath** parameter on remote computers.</span></span> <span data-ttu-id="f5861-189">Genom att ange explicita autentiseringsuppgifter kan du köra kommandot på en fjärrdator och komma åt en fil resurs på en tredje dator utan att ha påträffat ett nekat åtkomst fel eller använda CredSSP-autentisering för att delegera autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="f5861-189">By providing explicit credentials, you can run the command on a remote computer and access a file share on a third computer without encountering an access denied error or using CredSSP authentication to delegate credentials.</span></span>

<span data-ttu-id="f5861-190">Ange ett användar namn, till exempel **user01** eller **Domain01\User01** , eller ange ett **PSCredential** -objekt som genererats av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f5861-190">Type a user name, such as **User01** or **Domain01\User01** , or enter a **PSCredential** object generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="f5861-191">Om du anger ett användar namn uppmanas du att ange lösen ordet.</span><span class="sxs-lookup"><span data-stu-id="f5861-191">If you type a user name, you're prompted to enter the password.</span></span>

<span data-ttu-id="f5861-192">Autentiseringsuppgifterna lagras i ett [PSCredential](/dotnet/api/system.management.automation.pscredential) -objekt och lösen ordet lagras som en [SecureString](/dotnet/api/system.security.securestring).</span><span class="sxs-lookup"><span data-stu-id="f5861-192">Credentials are stored in a [PSCredential](/dotnet/api/system.management.automation.pscredential) object and the password is stored as a [SecureString](/dotnet/api/system.security.securestring).</span></span>

> [!NOTE]
> <span data-ttu-id="f5861-193">Mer information om **SecureString** -data skydd finns i [hur säker är SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span><span class="sxs-lookup"><span data-stu-id="f5861-193">For more information about **SecureString** data protection, see [How secure is SecureString?](/dotnet/api/system.security.securestring#how-secure-is-securestring).</span></span>

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

### <span data-ttu-id="f5861-194">-Force</span><span class="sxs-lookup"><span data-stu-id="f5861-194">-Force</span></span>

<span data-ttu-id="f5861-195">Anger att denna cmdlet inte följer begränsningen en gång per dag, hoppar över versions kontroll och laddar ned filer som överskrider gränsen på 1 GB.</span><span class="sxs-lookup"><span data-stu-id="f5861-195">Indicates that this cmdlet doesn't follow the once-per-day limitation, skips version checking, and downloads files that exceed the 1 GB limit.</span></span>

<span data-ttu-id="f5861-196">Utan den här parametern `Update-Help` körs bara en gång under varje 24-timmarsperiod.</span><span class="sxs-lookup"><span data-stu-id="f5861-196">Without this parameter, `Update-Help` runs only once in each 24-hour period.</span></span> <span data-ttu-id="f5861-197">Hämtningar är begränsade till 1 GB okomprimerat innehåll per modul och hjälpfiler installeras bara när de är nyare än de befintliga filerna på datorn.</span><span class="sxs-lookup"><span data-stu-id="f5861-197">Downloads are limited to 1 GB of uncompressed content per module and help files are only installed when they're newer than the existing files on the computer.</span></span>

<span data-ttu-id="f5861-198">Gränsen för en gång per dag skyddar de servrar som är värdar för hjälpfilerna och gör det praktiskt för dig att lägga till ett `Update-Help` kommando i din PowerShell-profil utan att kostnaden för resurs kostnaden för upprepade anslutningar eller nedladdningar debiteras.</span><span class="sxs-lookup"><span data-stu-id="f5861-198">The once-per-day limit protects the servers that host the help files and makes it practical for you to add an `Update-Help` command to your PowerShell profile without incurring the resource cost of repeated connections or downloads.</span></span>

<span data-ttu-id="f5861-199">Om du vill uppdatera hjälpen för en modul i flera användar gränssnitts kulturer utan **Force** -parametern inkluderar du alla användar gränssnitts kulturer i samma kommando, till exempel:</span><span class="sxs-lookup"><span data-stu-id="f5861-199">To update help for a module in multiple UI cultures without the **Force** parameter, include all UI cultures in the same command, such as:</span></span>

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

### <span data-ttu-id="f5861-200">-FullyQualifiedModule</span><span class="sxs-lookup"><span data-stu-id="f5861-200">-FullyQualifiedModule</span></span>

<span data-ttu-id="f5861-201">Anger moduler med namn som anges i form av **ModuleSpecification** -objekt.</span><span class="sxs-lookup"><span data-stu-id="f5861-201">Specifies modules with names that are specified in the form of **ModuleSpecification** objects.</span></span>
<span data-ttu-id="f5861-202">Dessa moduler beskrivs i avsnittet anmärkningar i [ModuleSpecification-konstruktorn (hash)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span><span class="sxs-lookup"><span data-stu-id="f5861-202">These modules are described in the Remarks section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor?view=powershellsdk-1.1.0#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>

<span data-ttu-id="f5861-203">Parametern **FullyQualifiedModule** accepterar till exempel ett modulnamn som anges i formatet:</span><span class="sxs-lookup"><span data-stu-id="f5861-203">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in the format:</span></span>

`@{ModuleName = "modulename"; ModuleVersion = "version_number"}`

<span data-ttu-id="f5861-204">eller</span><span class="sxs-lookup"><span data-stu-id="f5861-204">or</span></span>

`@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}.`

<span data-ttu-id="f5861-205">**Modulnamn** och **ModuleVersion** krävs, men **GUID** är valfritt.</span><span class="sxs-lookup"><span data-stu-id="f5861-205">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span>

<span data-ttu-id="f5861-206">Du kan inte ange parametern **FullyQualifiedModule** i samma kommando som en **modul** -parameter.</span><span class="sxs-lookup"><span data-stu-id="f5861-206">You can't specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span>

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

### <span data-ttu-id="f5861-207">-LiteralPath</span><span class="sxs-lookup"><span data-stu-id="f5861-207">-LiteralPath</span></span>

<span data-ttu-id="f5861-208">Anger mappen för uppdaterade hjälpfiler i stället för att ladda ned dem från Internet.</span><span class="sxs-lookup"><span data-stu-id="f5861-208">Specifies the folder for updated help files instead of downloading them from the internet.</span></span> <span data-ttu-id="f5861-209">Använd den här parametern eller **SourcePath** om du har använt `Save-Help` cmdleten för att hämta hjälpfiler till en katalog.</span><span class="sxs-lookup"><span data-stu-id="f5861-209">Use this parameter or **SourcePath** if you've used the `Save-Help` cmdlet to download help files to a directory.</span></span>

<span data-ttu-id="f5861-210">Du kan pipelina ett katalog objekt, till exempel från `Get-Item` `Get-ChildItem` cmdletarna eller, till `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="f5861-210">You can pipeline a directory object, such as from the `Get-Item` or `Get-ChildItem` cmdlets, to `Update-Help`.</span></span>

<span data-ttu-id="f5861-211">Till skillnad från värdet för **SourcePath** , används värdet för **LiteralPath** exakt som det skrivs.</span><span class="sxs-lookup"><span data-stu-id="f5861-211">Unlike the value of **SourcePath** , the value of **LiteralPath** is used exactly as it's typed.</span></span> <span data-ttu-id="f5861-212">Inga tecken tolkas som jokertecken.</span><span class="sxs-lookup"><span data-stu-id="f5861-212">No characters are interpreted as wildcard characters.</span></span> <span data-ttu-id="f5861-213">Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.</span><span class="sxs-lookup"><span data-stu-id="f5861-213">If the path includes escape characters, enclose it in single quotation marks.</span></span> <span data-ttu-id="f5861-214">Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.</span><span class="sxs-lookup"><span data-stu-id="f5861-214">Single quotation marks tell PowerShell not to interpret any characters as escape sequences.</span></span>

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="f5861-215">– Modul</span><span class="sxs-lookup"><span data-stu-id="f5861-215">-Module</span></span>

<span data-ttu-id="f5861-216">Uppdaterar hjälpen för de angivna modulerna.</span><span class="sxs-lookup"><span data-stu-id="f5861-216">Updates help for the specified modules.</span></span> <span data-ttu-id="f5861-217">Ange ett eller flera Modulnamn eller namn mönster i en kommaavgränsad lista eller ange en fil som visar ett modulnamn på varje rad.</span><span class="sxs-lookup"><span data-stu-id="f5861-217">Enter one or more module names or name patterns in a comma-separated list, or specify a file that lists one module name on each line.</span></span> <span data-ttu-id="f5861-218">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="f5861-218">Wildcard characters are permitted.</span></span> <span data-ttu-id="f5861-219">Du kan pipeline-moduler från `Get-Module` cmdlet: en till `Update-Help` cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="f5861-219">You can pipeline modules from the `Get-Module` cmdlet to the `Update-Help` cmdlet.</span></span>

<span data-ttu-id="f5861-220">De moduler som du anger måste vara installerade på datorn, men de behöver inte importeras till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="f5861-220">The modules that you specify must be installed on the computer, but they don't have to be imported into the current session.</span></span> <span data-ttu-id="f5861-221">Du kan ange vilken modul som helst i sessionen eller vilken modul som helst som är installerad på en plats som anges i `$env:PSModulePath` miljö variabeln.</span><span class="sxs-lookup"><span data-stu-id="f5861-221">You can specify any module in the session or any module that is installed in a location listed in the `$env:PSModulePath` environment variable.</span></span>

<span data-ttu-id="f5861-222">Värdet `*` (alla) försöker att uppdatera hjälpen för alla moduler som är installerade på datorn.</span><span class="sxs-lookup"><span data-stu-id="f5861-222">A value of `*` (all) attempts to update help for all modules that are installed on the computer.</span></span>
<span data-ttu-id="f5861-223">Moduler som inte stöder uppdaterbar hjälp ingår.</span><span class="sxs-lookup"><span data-stu-id="f5861-223">Modules that don't support Updatable Help are included.</span></span> <span data-ttu-id="f5861-224">Det här värdet kan generera fel när kommandot påträffar moduler som inte stöder uppdaterbar hjälp.</span><span class="sxs-lookup"><span data-stu-id="f5861-224">This value might generate errors when the command encounters modules that don't support Updatable Help.</span></span> <span data-ttu-id="f5861-225">Kör i stället `Update-Help` utan parametrar.</span><span class="sxs-lookup"><span data-stu-id="f5861-225">Instead, run `Update-Help` without parameters.</span></span>

<span data-ttu-id="f5861-226">Parametern **module** för `Update-Help` cmdleten accepterar inte den fullständiga sökvägen till en modul-fil eller modulens manifest fil.</span><span class="sxs-lookup"><span data-stu-id="f5861-226">The **Module** parameter of the `Update-Help` cmdlet doesn't accept the full path of a module file or module manifest file.</span></span> <span data-ttu-id="f5861-227">Om du vill uppdatera hjälpen för en modul som inte finns på en `$env:PSModulePath` plats importerar du modulen till den aktuella sessionen innan du kör `Update-Help` kommandot.</span><span class="sxs-lookup"><span data-stu-id="f5861-227">To update help for a module that isn't in a `$env:PSModulePath` location, import the module into the current session before you run the `Update-Help` command.</span></span>

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

### <span data-ttu-id="f5861-228">– Rekursivt</span><span class="sxs-lookup"><span data-stu-id="f5861-228">-Recurse</span></span>

<span data-ttu-id="f5861-229">Utför en rekursiv sökning efter hjälpfilerna i den angivna katalogen.</span><span class="sxs-lookup"><span data-stu-id="f5861-229">Performs a recursive search for help files in the specified directory.</span></span> <span data-ttu-id="f5861-230">Den här parametern är endast giltig om parametern **SourcePath** används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="f5861-230">This parameter is valid only when the command uses the **SourcePath** parameter.</span></span>

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

### <span data-ttu-id="f5861-231">-SourcePath</span><span class="sxs-lookup"><span data-stu-id="f5861-231">-SourcePath</span></span>

<span data-ttu-id="f5861-232">Anger en fil system katalog där `Update-Help` uppdaterade hjälpfiler hämtas, i stället för att de hämtas från Internet.</span><span class="sxs-lookup"><span data-stu-id="f5861-232">Specifies a file system folder where `Update-Help` gets updated help files, instead of downloading them from the internet.</span></span> <span data-ttu-id="f5861-233">Ange sökvägen till en mapp.</span><span class="sxs-lookup"><span data-stu-id="f5861-233">Enter the path of a folder.</span></span> <span data-ttu-id="f5861-234">Ange inte ett fil namn eller fil namns tillägg.</span><span class="sxs-lookup"><span data-stu-id="f5861-234">Don't specify a file name or file name extension.</span></span> <span data-ttu-id="f5861-235">Du kan pipelina en mapp, till exempel en från `Get-Item` -eller `Get-ChildItem` -cmdlet: ar, till `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="f5861-235">You can pipeline a folder, such as one from the `Get-Item` or `Get-ChildItem` cmdlets, to `Update-Help`.</span></span>

<span data-ttu-id="f5861-236">Som standard `Update-Help` hämtar de uppdaterade hjälpfilerna från Internet.</span><span class="sxs-lookup"><span data-stu-id="f5861-236">By default, `Update-Help` downloads updated help files from the internet.</span></span> <span data-ttu-id="f5861-237">Använd **SourcePath** när du har använt `Save-Help` cmdleten för att hämta uppdaterade hjälpfiler till en katalog.</span><span class="sxs-lookup"><span data-stu-id="f5861-237">Use **SourcePath** when you've used the `Save-Help` cmdlet to download updated help files to a directory.</span></span>

<span data-ttu-id="f5861-238">Om du vill ange ett standardvärde för **SourcePath** går du till **Grupprincip** , **dator konfiguration** och **anger standard Sök vägen för uppdatering-hjälpen**.</span><span class="sxs-lookup"><span data-stu-id="f5861-238">To specify a default value for **SourcePath** , go to **Group Policy** , **Computer Configuration** , and **Set the default source path for Update-Help**.</span></span> <span data-ttu-id="f5861-239">Den här grupprincip inställningen hindrar användare från `Update-Help` att använda för att hämta hjälpfiler från Internet.</span><span class="sxs-lookup"><span data-stu-id="f5861-239">This Group Policy setting prevents users from using `Update-Help` to download help files from the internet.</span></span>
<span data-ttu-id="f5861-240">Mer information finns i [about_Group_Policy_Settings](./About/about_Group_Policy_Settings.md).</span><span class="sxs-lookup"><span data-stu-id="f5861-240">For more information, see [about_Group_Policy_Settings](./About/about_Group_Policy_Settings.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="f5861-241">– Värdet</span><span class="sxs-lookup"><span data-stu-id="f5861-241">-UICulture</span></span>

<span data-ttu-id="f5861-242">Anger GRÄNSSNITTs språk värden som `Update-Help` används för att hämta uppdaterade hjälpfiler.</span><span class="sxs-lookup"><span data-stu-id="f5861-242">Specifies UI culture values that `Update-Help` uses to get updated help files.</span></span> <span data-ttu-id="f5861-243">Ange en eller flera språk koder, till exempel **es-es** , en variabel som innehåller kultur objekt eller ett kommando som hämtar kultur objekt, till exempel ett `Get-Culture` eller- `Get-UICulture` kommando.</span><span class="sxs-lookup"><span data-stu-id="f5861-243">Enter one or more language codes, such as **es-ES** , a variable that contains culture objects, or a command that gets culture objects, such as a `Get-Culture` or `Get-UICulture` command.</span></span> <span data-ttu-id="f5861-244">Jokertecken är inte tillåtna och du kan inte skicka en del språk kod, till exempel **de**.</span><span class="sxs-lookup"><span data-stu-id="f5861-244">Wildcard characters aren't permitted and you can't submit a partial language code, such as **de**.</span></span>

<span data-ttu-id="f5861-245">Som standard `Update-Help` får hjälpfilerna i användar gränssnitts kulturen angetts för operativ systemet.</span><span class="sxs-lookup"><span data-stu-id="f5861-245">By default, `Update-Help` gets help files in the UI culture set for the operating system.</span></span> <span data-ttu-id="f5861-246">Om du anger parametern **värdet** letar du `Update-Help` bara efter hjälp för den angivna användar gränssnitts kulturen.</span><span class="sxs-lookup"><span data-stu-id="f5861-246">If you specify the **UICulture** parameter, `Update-Help` looks for help only for the specified UI culture.</span></span>

<span data-ttu-id="f5861-247">Kommandon som använder parametern **värdet** fungerar bara när modulen tillhandahåller hjälpfiler för den angivna kulturen för användar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="f5861-247">Commands that use the **UICulture** parameter succeed only when the module provides help files for the specified UI culture.</span></span> <span data-ttu-id="f5861-248">Om kommandot Miss lyckas eftersom den angivna användar gränssnitts kulturen inte stöds visas ett fel meddelande.</span><span class="sxs-lookup"><span data-stu-id="f5861-248">If the command fails because the specified UI culture isn't supported, an error message is displayed.</span></span>

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

### <span data-ttu-id="f5861-249">-UseDefaultCredentials</span><span class="sxs-lookup"><span data-stu-id="f5861-249">-UseDefaultCredentials</span></span>

<span data-ttu-id="f5861-250">Anger att `Update-Help` Kör kommandot, inklusive hämtning av Internet, med hjälp av den aktuella användarens autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="f5861-250">Indicates that `Update-Help` runs the command, including the internet download, by using the credentials of the current user.</span></span> <span data-ttu-id="f5861-251">Som standard körs kommandot utan explicita autentiseringsuppgifter.</span><span class="sxs-lookup"><span data-stu-id="f5861-251">By default, the command runs without explicit credentials.</span></span>

<span data-ttu-id="f5861-252">Den här parametern är endast effektiv när webb hämtningen använder NTLM (NT LAN Manager), Negotiate eller Kerberos-baserad autentisering.</span><span class="sxs-lookup"><span data-stu-id="f5861-252">This parameter is effective only when the web download uses NT LAN Manager (NTLM), negotiate, or Kerberos-based authentication.</span></span>

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

### <span data-ttu-id="f5861-253">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f5861-253">-Confirm</span></span>

<span data-ttu-id="f5861-254">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f5861-254">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f5861-255">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f5861-255">-WhatIf</span></span>

<span data-ttu-id="f5861-256">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="f5861-256">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="f5861-257">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="f5861-257">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="f5861-258">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f5861-258">CommonParameters</span></span>

<span data-ttu-id="f5861-259">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f5861-259">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f5861-260">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f5861-260">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f5861-261">INDATA</span><span class="sxs-lookup"><span data-stu-id="f5861-261">INPUTS</span></span>

### <span data-ttu-id="f5861-262">System. IO. DirectoryInfo</span><span class="sxs-lookup"><span data-stu-id="f5861-262">System.IO.DirectoryInfo</span></span>

<span data-ttu-id="f5861-263">Du kan skicka en katalog Sök väg till `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="f5861-263">You can pipe a directory path to `Update-Help`.</span></span>

### <span data-ttu-id="f5861-264">System. Management. Automation. PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="f5861-264">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="f5861-265">Du kan skicka ett modul-objekt från `Get-Module` cmdlet: en till `Update-Help` .</span><span class="sxs-lookup"><span data-stu-id="f5861-265">You can pipe a module object from the `Get-Module` cmdlet to `Update-Help`.</span></span>

## <span data-ttu-id="f5861-266">UTDATA</span><span class="sxs-lookup"><span data-stu-id="f5861-266">OUTPUTS</span></span>

### <span data-ttu-id="f5861-267">Inget</span><span class="sxs-lookup"><span data-stu-id="f5861-267">None</span></span>

<span data-ttu-id="f5861-268">`Update-Help` genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="f5861-268">`Update-Help` doesn't generate any output.</span></span>

## <span data-ttu-id="f5861-269">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="f5861-269">NOTES</span></span>

<span data-ttu-id="f5861-270">Om du vill uppdatera hjälpen för PowerShell Core-modulerna som innehåller de kommandon som är installerade med PowerShell eller någon modul i `$PSHOME\Modules` katalogen startar du PowerShell med alternativet att **köra som administratör**.</span><span class="sxs-lookup"><span data-stu-id="f5861-270">To update help for the PowerShell Core modules, that contain the commands that are installed with PowerShell, or any module in the `$PSHOME\Modules` directory, start PowerShell with the option to **Run as administrator**.</span></span>

<span data-ttu-id="f5861-271">Endast medlemmar i gruppen Administratörer på datorn kan uppdatera hjälpen för PowerShell Core-modulerna, kommandon som installeras tillsammans med PowerShell och för moduler i `$PSHOME\Modules` mappen.</span><span class="sxs-lookup"><span data-stu-id="f5861-271">Only members of the Administrators group on the computer can update help for the PowerShell Core modules, the commands that are installed together with PowerShell, and for modules in the `$PSHOME\Modules` folder.</span></span> <span data-ttu-id="f5861-272">Om du inte har behörighet att uppdatera hjälpfiler kan du läsa hjälpfilerna online.</span><span class="sxs-lookup"><span data-stu-id="f5861-272">If you don't have permission to update help files, you can read the help files online.</span></span> <span data-ttu-id="f5861-273">Till exempel `Get-Help Update-Help -Online`.</span><span class="sxs-lookup"><span data-stu-id="f5861-273">For example, `Get-Help Update-Help -Online`.</span></span>

<span data-ttu-id="f5861-274">Moduler är den minsta enheten för uppdaterbar hjälp.</span><span class="sxs-lookup"><span data-stu-id="f5861-274">Modules are the smallest unit of updatable help.</span></span> <span data-ttu-id="f5861-275">Du kan inte uppdatera hjälpen för en viss cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f5861-275">You can't update help for a particular cmdlet.</span></span> <span data-ttu-id="f5861-276">Om du vill hitta modulen som innehåller en viss cmdlet använder du egenskapen **Modulnamn** för `Get-Command` cmdleten, till exempel `(Get-Command Update-Help).ModuleName` .</span><span class="sxs-lookup"><span data-stu-id="f5861-276">To find the module that contains a particular cmdlet, use the **ModuleName** property of the `Get-Command` cmdlet, for example, `(Get-Command Update-Help).ModuleName`.</span></span>

<span data-ttu-id="f5861-277">Eftersom hjälpfiler installeras i modul-katalogen `Update-Help` kan cmdleten bara installera den uppdaterade hjälp filen för moduler som är installerade på datorn.</span><span class="sxs-lookup"><span data-stu-id="f5861-277">Because help files are installed in the module directory, the `Update-Help` cmdlet can install updated help file only for modules that are installed on the computer.</span></span> <span data-ttu-id="f5861-278">Men `Save-Help` cmdleten kan spara hjälp för moduler som inte är installerade på datorn.</span><span class="sxs-lookup"><span data-stu-id="f5861-278">However, the `Save-Help` cmdlet can save help for modules that aren't installed on the computer.</span></span>

<span data-ttu-id="f5861-279">Om `Update-Help` det inte går att hitta uppdaterade hjälpfiler för en modul, eller om det inte går att hitta en uppdaterad hjälp på det angivna språket, fortsätter den tyst utan att ett fel meddelande visas.</span><span class="sxs-lookup"><span data-stu-id="f5861-279">If `Update-Help` can't find updated help files for a module, or can't find updated help in the specified language, it continues silently without displaying an error message.</span></span> <span data-ttu-id="f5861-280">Använd **verbose** -parametern för att se information om status och förlopp.</span><span class="sxs-lookup"><span data-stu-id="f5861-280">To see status and progress details, use the **Verbose** parameter.</span></span>

<span data-ttu-id="f5861-281">`Update-Help`Cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="f5861-281">The `Update-Help` cmdlet was introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="f5861-282">Den fungerar inte i tidigare versioner av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f5861-282">It doesn't work in earlier versions of PowerShell.</span></span> <span data-ttu-id="f5861-283">På datorer som har både Windows PowerShell 2,0 och Windows PowerShell 3,0 använder du `Update-Help` cmdleten i en Windows PowerShell 3,0-session för att hämta och uppdatera hjälpfiler.</span><span class="sxs-lookup"><span data-stu-id="f5861-283">On computers that have both Windows PowerShell 2.0 and Windows PowerShell 3.0, use the `Update-Help` cmdlet in a Windows PowerShell 3.0 session to download and update help files.</span></span> <span data-ttu-id="f5861-284">Hjälpfilerna är tillgängliga för både Windows PowerShell 2,0 och Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="f5861-284">The help files are available to both Windows PowerShell 2.0 and Windows PowerShell 3.0.</span></span>

<span data-ttu-id="f5861-285">`Update-Help` `Save-Help` Cmdletarna och använder följande portar för att hämta hjälpfiler: port 80 för http och port 443 för https.</span><span class="sxs-lookup"><span data-stu-id="f5861-285">The `Update-Help` and `Save-Help` cmdlets use the following ports to download help files: Port 80 for HTTP and port 443 for HTTPS.</span></span>

<span data-ttu-id="f5861-286">`Update-Help` stöder alla moduler och snapin-moduler för PowerShell Core. Den har inte stöd för några andra snapin-moduler.</span><span class="sxs-lookup"><span data-stu-id="f5861-286">`Update-Help` supports all modules and the PowerShell Core snap-ins. It doesn't support any other snap-ins.</span></span>

<span data-ttu-id="f5861-287">Om du vill uppdatera hjälpen för en modul på en plats som inte finns med i `$env:PSModulePath` miljövariabeln importerar du modulen till den aktuella sessionen och kör sedan ett `Update-Help` kommando.</span><span class="sxs-lookup"><span data-stu-id="f5861-287">To update help for a module in a location that isn't listed in the `$env:PSModulePath` environment variable, import the module into the current session and then run an `Update-Help` command.</span></span> <span data-ttu-id="f5861-288">Kör `Update-Help` utan parametrar eller Använd parametern **module** för att ange modulnamnet.</span><span class="sxs-lookup"><span data-stu-id="f5861-288">Run `Update-Help` without parameters or use the **Module** parameter to specify the module name.</span></span> <span data-ttu-id="f5861-289">Parametern **module** för `Update-Help` `Save-Help` cmdletarna och accepterar inte den fullständiga sökvägen till en modul fil eller modulens manifest fil.</span><span class="sxs-lookup"><span data-stu-id="f5861-289">The **Module** parameter of the `Update-Help` and `Save-Help` cmdlets doesn't accept the full path of a module file or module manifest file.</span></span>

<span data-ttu-id="f5861-290">Alla moduler kan stödja uppdaterings bar hjälp.</span><span class="sxs-lookup"><span data-stu-id="f5861-290">Any module can support Updatable Help.</span></span> <span data-ttu-id="f5861-291">Instruktioner för att stödja uppdaterings bar hjälp i de moduler som du skapar finns i [support uppdaterings bara hjälp](/powershell/scripting/developer/module/supporting-updatable-help).</span><span class="sxs-lookup"><span data-stu-id="f5861-291">For instructions for supporting Updatable Help in the modules that you author, see [Supporting Updatable Help](/powershell/scripting/developer/module/supporting-updatable-help).</span></span>

<span data-ttu-id="f5861-292">`Update-Help` `Save-Help` Cmdletarna och stöds inte på Windows Preinstallation Environment (Windows PE).</span><span class="sxs-lookup"><span data-stu-id="f5861-292">The `Update-Help` and `Save-Help` cmdlets are not supported on Windows Preinstallation Environment (Windows PE).</span></span>

## <span data-ttu-id="f5861-293">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="f5861-293">RELATED LINKS</span></span>

[<span data-ttu-id="f5861-294">Get-Culture</span><span class="sxs-lookup"><span data-stu-id="f5861-294">Get-Culture</span></span>](../Microsoft.PowerShell.Utility/Get-Culture.md)

[<span data-ttu-id="f5861-295">Get – hjälp</span><span class="sxs-lookup"><span data-stu-id="f5861-295">Get-Help</span></span>](Get-Help.md)

[<span data-ttu-id="f5861-296">Hämta modul</span><span class="sxs-lookup"><span data-stu-id="f5861-296">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="f5861-297">Get-värdet</span><span class="sxs-lookup"><span data-stu-id="f5861-297">Get-UICulture</span></span>](../Microsoft.PowerShell.Utility/Get-UICulture.md)

[<span data-ttu-id="f5861-298">Start – jobb</span><span class="sxs-lookup"><span data-stu-id="f5861-298">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="f5861-299">Spara – hjälp</span><span class="sxs-lookup"><span data-stu-id="f5861-299">Save-Help</span></span>](Save-Help.md)
