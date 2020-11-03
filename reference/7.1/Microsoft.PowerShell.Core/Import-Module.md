---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/import-module?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Module
ms.openlocfilehash: 70453f50e727f89012a3e2077557bff7a81ff000
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267800"
---
# <span data-ttu-id="0f0c3-103">Import-Module</span><span class="sxs-lookup"><span data-stu-id="0f0c3-103">Import-Module</span></span>

## <span data-ttu-id="0f0c3-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="0f0c3-104">SYNOPSIS</span></span>
<span data-ttu-id="0f0c3-105">Lägger till moduler i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-105">Adds modules to the current session.</span></span>

## <span data-ttu-id="0f0c3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0f0c3-106">SYNTAX</span></span>

### <span data-ttu-id="0f0c3-107">Namn (standard)</span><span class="sxs-lookup"><span data-stu-id="0f0c3-107">Name (Default)</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>]  [<CommonParameters>]
```

### <span data-ttu-id="0f0c3-108">PSSession</span><span class="sxs-lookup"><span data-stu-id="0f0c3-108">PSSession</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] -PSSession <PSSession>  [<CommonParameters>]
```

### <span data-ttu-id="0f0c3-109">CimSession</span><span class="sxs-lookup"><span data-stu-id="0f0c3-109">CimSession</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] -CimSession <CimSession> [-CimResourceUri <Uri>] [-CimNamespace <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="0f0c3-110">UseWindowsPowerShell</span><span class="sxs-lookup"><span data-stu-id="0f0c3-110">UseWindowsPowerShell</span></span>

```
Import-Module [-Name] <string[]> -UseWindowsPowerShell [-Global] [-Prefix <string>]
 [-Function <string[]>] [-Cmdlet <string[]>] [-Variable <string[]>] [-Alias <string[]>]
 [-Force] [-PassThru] [-AsCustomObject] [-MinimumVersion <version>] [-MaximumVersion <string>]
 [-RequiredVersion <version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <string>] [<CommonParameters>]
```

### <span data-ttu-id="0f0c3-111">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="0f0c3-111">FullyQualifiedName</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-FullyQualifiedName] <ModuleSpecification[]>
 [-Function <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force]
 [-SkipEditionCheck] [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking]
 [-NoClobber] [-Scope <String>]  [<CommonParameters>]
```

### <span data-ttu-id="0f0c3-112">FullyQualifiedNameAndPSSession</span><span class="sxs-lookup"><span data-stu-id="0f0c3-112">FullyQualifiedNameAndPSSession</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-FullyQualifiedName] <ModuleSpecification[]>
 [-Function <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force]
 [-SkipEditionCheck] [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking]
 [-NoClobber] [-Scope <String>] -PSSession <PSSession>  [<CommonParameters>]
```

### <span data-ttu-id="0f0c3-113">FullyQualifiedNameAndUseWindowsPowerShell</span><span class="sxs-lookup"><span data-stu-id="0f0c3-113">FullyQualifiedNameAndUseWindowsPowerShell</span></span>

```
Import-Module [-FullyQualifiedName] <ModuleSpecification[]> -UseWindowsPowerShell [-Global]
 [-Prefix <string>] [-Function <string[]>] [-Cmdlet <string[]>] [-Variable <string[]>]
 [-Alias <string[]>] [-Force] [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>]
 [-DisableNameChecking] [-NoClobber] [-Scope <string>] [<CommonParameters>]
```

### <span data-ttu-id="0f0c3-114">Sammansättning</span><span class="sxs-lookup"><span data-stu-id="0f0c3-114">Assembly</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Assembly] <Assembly[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>]  [<CommonParameters>]
```

### <span data-ttu-id="0f0c3-115">ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="0f0c3-115">ModuleInfo</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Function <String[]>] [-Cmdlet <String[]>]
 [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck] [-PassThru]
 [-AsCustomObject] [-ModuleInfo] <PSModuleInfo[]> [-ArgumentList <Object[]>] [-DisableNameChecking]
 [-NoClobber] [-Scope <String>]  [<CommonParameters>]
```

## <span data-ttu-id="0f0c3-116">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="0f0c3-116">DESCRIPTION</span></span>

<span data-ttu-id="0f0c3-117">`Import-Module`Cmdleten lägger till en eller flera moduler i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-117">The `Import-Module` cmdlet adds one or more modules to the current session.</span></span> <span data-ttu-id="0f0c3-118">Från och med PowerShell 3,0 importeras installerade moduler automatiskt till sessionen när du använder kommandon eller providrar i modulen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-118">Starting in PowerShell 3.0, installed modules are automatically imported to the session when you use any commands or providers in the module.</span></span> <span data-ttu-id="0f0c3-119">Du kan dock fortfarande använda `Import-Module` kommandot för att importera en modul.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-119">However, you can still use the `Import-Module` command to import a module.</span></span>
<span data-ttu-id="0f0c3-120">Du kan inaktivera automatisk modul import med hjälp av `$PSModuleAutoloadingPreference` Preference-variabeln.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-120">You can disable automatic module importing using the `$PSModuleAutoloadingPreference` preference variable.</span></span> <span data-ttu-id="0f0c3-121">Mer information om `$PSModuleAutoloadingPreference` variabeln finns i [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="0f0c3-121">For more information about the `$PSModuleAutoloadingPreference` variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="0f0c3-122">En modul är ett paket som innehåller medlemmar som kan användas i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-122">A module is a package that contains members that can be used in PowerShell.</span></span> <span data-ttu-id="0f0c3-123">Medlemmar inkluderar cmdlets, providrar, skript, funktioner, variabler och andra verktyg och filer.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-123">Members include cmdlets, providers, scripts, functions, variables, and other tools and files.</span></span> <span data-ttu-id="0f0c3-124">När en modul har importer ATS kan du använda-modulens medlemmar i sessionen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-124">After a module is imported, you can use the module members in your session.</span></span> <span data-ttu-id="0f0c3-125">Mer information om moduler finns i [about_Modules](About/about_Modules.md).</span><span class="sxs-lookup"><span data-stu-id="0f0c3-125">For more information about modules, see [about_Modules](About/about_Modules.md).</span></span>

<span data-ttu-id="0f0c3-126">Som standard `Import-Module` importerar alla medlemmar som modulen exporterar, men du kan använda **alias** , **funktion** , **cmdlet** och **variabel** parametrar för att begränsa vilka medlemmar som importeras.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-126">By default, `Import-Module` imports all members that the module exports, but you can use the **Alias** , **Function** , **Cmdlet** , and **Variable** parameters to restrict which members are imported.</span></span> <span data-ttu-id="0f0c3-127">Parametern **NoClobber** förhindrar `Import-Module` import av medlemmar som har samma namn som medlemmar i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-127">The **NoClobber** parameter prevents `Import-Module` from importing members that have the same names as members in the current session.</span></span>

<span data-ttu-id="0f0c3-128">`Import-Module` importerar en modul endast till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-128">`Import-Module` imports a module only into the current session.</span></span> <span data-ttu-id="0f0c3-129">Om du vill importera modulen till varje ny session lägger du till ett `Import-Module` kommando i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-129">To import the module into every new session, add an `Import-Module` command to your PowerShell profile.</span></span> <span data-ttu-id="0f0c3-130">Mer information om profiler finns [about_Profiles](About/about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="0f0c3-130">For more information about profiles, see [about_Profiles](About/about_Profiles.md).</span></span>

<span data-ttu-id="0f0c3-131">Du kan hantera fjärranslutna Windows-datorer som har PowerShell-fjärrkommunikation aktive rad genom att skapa en **PSSession** på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-131">You can manage remote Windows computers that have PowerShell remoting enabled by creating a **PSSession** on the remote computer.</span></span> <span data-ttu-id="0f0c3-132">Använd sedan **PSSession** -parametern för `Import-Module` för att importera de moduler som är installerade på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-132">Then use the **PSSession** parameter of `Import-Module` to import the modules that are installed on the remote computer.</span></span> <span data-ttu-id="0f0c3-133">Nu kan du använda de importerade kommandona i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-133">You can now use the imported commands in the current session.</span></span> <span data-ttu-id="0f0c3-134">Kommandona körs implicit på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-134">The commands implicitly run on the remote computer.</span></span>

<span data-ttu-id="0f0c3-135">Från och med Windows PowerShell 3,0 kan du använda `Import-Module` för att importera common information Model (CIM)-moduler, där cmdletarna definieras i cmdlet definition XML-filer (cdxlm).</span><span class="sxs-lookup"><span data-stu-id="0f0c3-135">Starting in Windows PowerShell 3.0, you can use `Import-Module` to import Common Information Model (CIM) modules, in which the cmdlets are defined in Cmdlet Definition XML (CDXML) files.</span></span> <span data-ttu-id="0f0c3-136">Med den här funktionen kan du använda cmdletar som implementeras i icke-hanterade kod sammansättningar, t. ex. sådana som skrivits i C++.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-136">This feature allows you to use cmdlets that are implemented in non-managed code assemblies, such as those written in C++.</span></span>

<span data-ttu-id="0f0c3-137">För fjärrdatorer som inte har PowerShell-fjärrkommunikation aktive rad, inklusive datorer som inte kör Windows operativ system, kan du använda **CIMSession** -parametern för `Import-Module` för att importera CIM-moduler från fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-137">For remote computers that don't have PowerShell remoting enabled, including computers that aren't running the Windows operating system, you can use the **CIMSession** parameter of `Import-Module` to import CIM modules from the remote computer.</span></span> <span data-ttu-id="0f0c3-138">De importerade kommandona körs implicit på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-138">The imported commands run implicitly on the remote computer.</span></span> <span data-ttu-id="0f0c3-139">En **CIMSession** är en anslutning till Windows Management INSTRUMENTATION (WMI) på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-139">A **CIMSession** is a connection to Windows Management Instrumentation (WMI) on the remote computer.</span></span>

## <span data-ttu-id="0f0c3-140">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="0f0c3-140">EXAMPLES</span></span>

### <span data-ttu-id="0f0c3-141">Exempel 1: importera medlemmarna i en modul till den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="0f0c3-141">Example 1: Import the members of a module into the current session</span></span>

<span data-ttu-id="0f0c3-142">I det här exemplet importeras medlemmarna i **PSDiagnostics** -modulen till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-142">This example imports the members of the **PSDiagnostics** module into the current session.</span></span>

```powershell
Import-Module -Name PSDiagnostics
```

### <span data-ttu-id="0f0c3-143">Exempel 2: importera alla moduler som anges av sökvägen till modulen</span><span class="sxs-lookup"><span data-stu-id="0f0c3-143">Example 2: Import all modules specified by the module path</span></span>

<span data-ttu-id="0f0c3-144">I det här exemplet importeras alla tillgängliga moduler i sökvägen som anges av `$env:PSModulePath` miljö variabeln till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-144">This example imports all available modules in the path specified by the `$env:PSModulePath` environment variable into the current session.</span></span>

```powershell
Get-Module -ListAvailable | Import-Module
```

### <span data-ttu-id="0f0c3-145">Exempel 3: Importera medlemmar i flera moduler till den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="0f0c3-145">Example 3: Import the members of several modules into the current session</span></span>

<span data-ttu-id="0f0c3-146">I det här exemplet importeras medlemmar av **PSDiagnostics** -och **DISM** -modulerna till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-146">This example imports the members of the **PSDiagnostics** and **Dism** modules into the current session.</span></span>

```powershell
$m = Get-Module -ListAvailable PSDiagnostics, Dism
Import-Module -ModuleInfo $m
```

<span data-ttu-id="0f0c3-147">`Get-Module`Cmdlet: en hämtar modulen **PSDiagnostics** och **DISM** och sparar objekten i `$m` variabeln.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-147">The `Get-Module` cmdlet gets the **PSDiagnostics** and **Dism** modules and saves the objects in the `$m` variable.</span></span> <span data-ttu-id="0f0c3-148">**ListAvailable** -parametern krävs när du hämtar moduler som ännu inte har importer ATS till sessionen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-148">The **ListAvailable** parameter is required when you're getting modules that aren't yet imported into the session.</span></span>

<span data-ttu-id="0f0c3-149">Parametern **ModuleInfo** i `Import-Module` används för att importera modulerna till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-149">The **ModuleInfo** parameter of `Import-Module` is used to import the modules into the current session.</span></span>

### <span data-ttu-id="0f0c3-150">Exempel 4: importera alla moduler som anges av en sökväg</span><span class="sxs-lookup"><span data-stu-id="0f0c3-150">Example 4: Import all modules specified by a path</span></span>

<span data-ttu-id="0f0c3-151">I det här exemplet används en explicit sökväg för att identifiera den modul som ska importeras.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-151">This example uses an explicit path to identify the module to import.</span></span>

```powershell
Import-Module -Name c:\ps-test\modules\test -Verbose
```

```Output
VERBOSE: Loading module from path 'C:\ps-test\modules\Test\Test.psm1'.
VERBOSE: Exporting function 'my-parm'.
VERBOSE: Exporting function 'Get-Parameter'.
VERBOSE: Exporting function 'Get-Specification'.
VERBOSE: Exporting function 'Get-SpecDetails'.
```

<span data-ttu-id="0f0c3-152">Med hjälp av parametern **verbose** `Import-Module` kan du rapportera förloppet när modulen läses in.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-152">Using the **Verbose** parameter causes `Import-Module` to report progress as it loads the module.</span></span>
<span data-ttu-id="0f0c3-153">Utan **verbose** -, **Passthru** -eller **AsCustomObject** -parametern `Import-Module` genererar inga utdata när en modul importeras.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-153">Without the **Verbose** , **PassThru** , or **AsCustomObject** parameter, `Import-Module` does not generate any output when it imports a module.</span></span>

### <span data-ttu-id="0f0c3-154">Exempel 5: begränsa modul medlemmar som importeras till en session</span><span class="sxs-lookup"><span data-stu-id="0f0c3-154">Example 5: Restrict module members imported into a session</span></span>

<span data-ttu-id="0f0c3-155">I det här exemplet visas hur du begränsar vilka modulblad som importeras till sessionen och kommandots effekter i sessionen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-155">This example shows how to restrict which module members are imported into the session and the effect of this command on the session.</span></span> <span data-ttu-id="0f0c3-156">**Funktions** parametern begränsar de medlemmar som importeras från modulen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-156">The **Function** parameter limits the members that are imported from the module.</span></span> <span data-ttu-id="0f0c3-157">Du kan också använda parametrarna **alias** , **variabel** och **cmdlet** för att begränsa andra medlemmar som en modul importerar.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-157">You can also use the **Alias** , **Variable** , and **Cmdlet** parameters to restrict other members that a module imports.</span></span>

<span data-ttu-id="0f0c3-158">`Get-Module`Cmdlet: en hämtar det objekt som representerar **PSDiagnostics** -modulen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-158">The `Get-Module` cmdlet gets the object that represents the **PSDiagnostics** module.</span></span> <span data-ttu-id="0f0c3-159">Egenskapen **ExportedCmdlets** visar alla cmdletar som modulen exporterar, även om de inte har importer ATS.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-159">The **ExportedCmdlets** property lists all the cmdlets that the module exports, even though they were not all imported.</span></span>

```powershell
Import-Module PSDiagnostics -Function Disable-PSTrace, Enable-PSTrace
(Get-Module PSDiagnostics).ExportedCommands
```

```Output
Key                          Value
---                          -----
Disable-PSTrace              Disable-PSTrace
Disable-PSWSManCombinedTrace Disable-PSWSManCombinedTrace
Disable-WSManTrace           Disable-WSManTrace
Enable-PSTrace               Enable-PSTrace
Enable-PSWSManCombinedTrace  Enable-PSWSManCombinedTrace
Enable-WSManTrace            Enable-WSManTrace
Get-LogProperties            Get-LogProperties
Set-LogProperties            Set-LogProperties
Start-Trace                  Start-Trace
Stop-Trace                   Stop-Trace
```

```powershell
Get-Command -Module PSDiagnostics
```

```Output
CommandType     Name                 Version    Source
-----------     ----                 -------    ------
Function        Disable-PSTrace      6.1.0.0    PSDiagnostics
Function        Enable-PSTrace       6.1.0.0    PSDiagnostics
```

<span data-ttu-id="0f0c3-160">Om du använder parametern **module** för `Get-Command` cmdleten visas de kommandon som har importer ATS från **PSDiagnostics** -modulen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-160">Using the **Module** parameter of the `Get-Command` cmdlet shows the commands that were imported from the **PSDiagnostics** module.</span></span> <span data-ttu-id="0f0c3-161">Resultatet bekräftar att endast `Disable-PSTrace` `Enable-PSTrace` cmdletarna och har importer ATS.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-161">The results confirm that only the `Disable-PSTrace` and `Enable-PSTrace` cmdlets were imported.</span></span>

### <span data-ttu-id="0f0c3-162">Exempel 6: importera medlemmarna i en modul och Lägg till ett prefix</span><span class="sxs-lookup"><span data-stu-id="0f0c3-162">Example 6: Import the members of a module and add a prefix</span></span>

<span data-ttu-id="0f0c3-163">Det här exemplet importerar **PSDiagnostics** -modulen till den aktuella sessionen, lägger till ett prefix till medlems namnen och visar sedan de förfasta medlems namnen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-163">This example imports the **PSDiagnostics** module into the current session, adds a prefix to the member names, and then displays the prefixed member names.</span></span> <span data-ttu-id="0f0c3-164">Parametern **prefix** för `Import-Module` lägger till **x** -prefixet till alla medlemmar som importeras från modulen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-164">The **Prefix** parameter of `Import-Module` adds the **x** prefix to all members that are imported from the module.</span></span> <span data-ttu-id="0f0c3-165">Prefixet gäller endast medlemmarna i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-165">The prefix applies only to the members in the current session.</span></span> <span data-ttu-id="0f0c3-166">Modulen ändras inte.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-166">It does not change the module.</span></span> <span data-ttu-id="0f0c3-167">Parametern **Passthru** returnerar ett modul-objekt som representerar den importerade modulen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-167">The **PassThru** parameter returns a module object that represents the imported module.</span></span>

```powershell
Import-Module PSDiagnostics -Prefix x -PassThru
```

```Output
ModuleType Version    Name               ExportedCommands
---------- -------    ----               ----------------
Script     6.1.0.0    PSDiagnostics      {Disable-xPSTrace, Disable-xPSWSManCombinedTrace, Disable-xW...
```

```powershell
Get-Command -Module PSDiagnostics
```

```Output
CommandType     Name                                   Version    Source
-----------     ----                                   -------    ------
Function        Disable-xPSTrace                       6.1.0.0    PSDiagnostics
Function        Disable-xPSWSManCombinedTrace          6.1.0.0    PSDiagnostics
Function        Disable-xWSManTrace                    6.1.0.0    PSDiagnostics
Function        Enable-xPSTrace                        6.1.0.0    PSDiagnostics
Function        Enable-xPSWSManCombinedTrace           6.1.0.0    PSDiagnostics
Function        Enable-xWSManTrace                     6.1.0.0    PSDiagnostics
Function        Get-xLogProperties                     6.1.0.0    PSDiagnostics
Function        Set-xLogProperties                     6.1.0.0    PSDiagnostics
Function        Start-xTrace                           6.1.0.0    PSDiagnostics
Function        Stop-xTrace                            6.1.0.0    PSDiagnostics
```

<span data-ttu-id="0f0c3-168">`Get-Command` hämtar de medlemmar som har importer ATS från modulen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-168">`Get-Command` gets the members that have been imported from the module.</span></span> <span data-ttu-id="0f0c3-169">Utdata visar att modulens medlemmar är korrekt fasta.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-169">The output shows that the module members were correctly prefixed.</span></span>

### <span data-ttu-id="0f0c3-170">Exempel 7: Hämta och använda ett anpassat objekt</span><span class="sxs-lookup"><span data-stu-id="0f0c3-170">Example 7: Get and use a custom object</span></span>

<span data-ttu-id="0f0c3-171">Det här exemplet visar hur du hämtar och använder det anpassade objektet som returnerades av **import-module**.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-171">This example demonstrates how to get and use the custom object returned by **Import-Module**.</span></span>

<span data-ttu-id="0f0c3-172">Anpassade objekt innehåller syntetiska medlemmar som representerar var och en av de importerade modulerna medlemmar.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-172">Custom objects include synthetic members that represent each of the imported module members.</span></span> <span data-ttu-id="0f0c3-173">Till exempel konverteras cmdletarna och funktionerna i en modul till skript metoder för det anpassade objektet.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-173">For example, the cmdlets and functions in a module are converted to script methods of the custom object.</span></span>

<span data-ttu-id="0f0c3-174">Anpassade objekt är användbara i skript.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-174">Custom objects are useful in scripting.</span></span> <span data-ttu-id="0f0c3-175">De är också användbara när flera importerade objekt har samma namn.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-175">They are also useful when several imported objects have the same names.</span></span> <span data-ttu-id="0f0c3-176">Användning av skript metoden för ett objekt motsvarar att ange det fullständigt kvalificerade namnet på en importerad medlem, inklusive dess modulnamn.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-176">Using the script method of an object is equivalent to specifying the fully qualified name of an imported member, including its module name.</span></span>

<span data-ttu-id="0f0c3-177">Parametern **AsCustomObject** kan bara användas när du importerar en-skript-modul.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-177">The **AsCustomObject** parameter can be used only when importing a script module.</span></span> <span data-ttu-id="0f0c3-178">Används `Get-Module` för att avgöra vilka av de tillgängliga modulerna som är en skriptbaserad modul.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-178">Use `Get-Module` to determine which of the available modules is a script module.</span></span>

```powershell
Get-Module -List | Format-Table -Property Name, ModuleType -AutoSize
```

```Output
Name          ModuleType
----          ----------
Show-Calendar     Script
BitsTransfer    Manifest
PSDiagnostics   Manifest
TestCmdlets       Script
...
```

```powershell
$a = Import-Module -Name Show-Calendar -AsCustomObject -Passthru
$a | Get-Member
```

```Output
    TypeName: System.Management.Automation.PSCustomObject
Name          MemberType   Definition
----          ----------   ----------
Equals        Method       bool Equals(System.Object obj)
GetHashCode   Method       int GetHashCode()
GetType       Method       type GetType()
ToString      Method       string ToString()
Show-Calendar ScriptMethod System.Object Show-Calendar();
```

```powershell
$a."Show-Calendar"()
```

<span data-ttu-id="0f0c3-179">Skript modulen **show-Calendar** importeras med parametern **AsCustomObject** för att begära ett anpassat objekt och parametern **Passthru** för att returnera objektet.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-179">The **Show-Calendar** script module is imported using the **AsCustomObject** parameter to request a custom object and the **PassThru** parameter to return the object.</span></span> <span data-ttu-id="0f0c3-180">Det resulterande anpassade objektet sparas i `$a` variabeln.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-180">The resulting custom object is saved in the `$a` variable.</span></span>

<span data-ttu-id="0f0c3-181">`$a`Variabeln är skickas till `Get-Member` cmdleten för att visa egenskaper och metoder för det sparade objektet.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-181">The `$a` variable is piped to the `Get-Member` cmdlet to show the properties and methods of the saved object.</span></span> <span data-ttu-id="0f0c3-182">Utdata visar skript metoden **show-Calendar** .</span><span class="sxs-lookup"><span data-stu-id="0f0c3-182">The output shows a **Show-Calendar** script method.</span></span>

<span data-ttu-id="0f0c3-183">Om du vill anropa skript metoden **show-Calendar** måste metod namnet omges av citat tecken, eftersom namnet innehåller ett bindestreck.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-183">To call the **Show-Calendar** script method, the method name must be enclosed in quotation marks because the name includes a hyphen.</span></span>

### <span data-ttu-id="0f0c3-184">Exempel 8: importera en modul igen till samma session</span><span class="sxs-lookup"><span data-stu-id="0f0c3-184">Example 8: Reimport a module into the same session</span></span>

<span data-ttu-id="0f0c3-185">Det här exemplet visar hur du använder **Force** -parametern i `Import-Module` när du importerar om en modul till samma session.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-185">This example shows how to use the **Force** parameter of `Import-Module` when you're reimporting a module into the same session.</span></span> <span data-ttu-id="0f0c3-186">Parametern **Force** tar bort den inlästa modulen och importerar den sedan igen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-186">The **Force** parameter removes the loaded module and then imports it again.</span></span>

```powershell
Import-Module PSDiagnostics
Import-Module PSDiagnostics -Force -Prefix PS
```

<span data-ttu-id="0f0c3-187">Det första kommandot importerar **PSDiagnostics** -modulen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-187">The first command imports the **PSDiagnostics** module.</span></span> <span data-ttu-id="0f0c3-188">Det andra kommandot importerar modulen igen, den här gången med hjälp av parametern **prefix** .</span><span class="sxs-lookup"><span data-stu-id="0f0c3-188">The second command imports the module again, this time using the **Prefix** parameter.</span></span>

<span data-ttu-id="0f0c3-189">Utan **Force** -parametern innehåller sessionen två kopior av varje **PSDiagnostics** -cmdlet, en med standard namnet och en med det förfasta namnet.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-189">Without the **Force** parameter, the session would include two copies of each **PSDiagnostics** cmdlet, one with the standard name and one with the prefixed name.</span></span>

### <span data-ttu-id="0f0c3-190">Exempel 9: kör kommandon som har dolts av importerade kommandon</span><span class="sxs-lookup"><span data-stu-id="0f0c3-190">Example 9: Run commands that have been hidden by imported commands</span></span>

<span data-ttu-id="0f0c3-191">Det här exemplet visar hur du kör kommandon som har dolts av importerade kommandon.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-191">This example shows how to run commands that have been hidden by imported commands.</span></span> <span data-ttu-id="0f0c3-192">Modulen **TestModule** innehåller en funktion med namnet `Get-Date` som returnerar året och dagen på året.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-192">The **TestModule** module includes a function named `Get-Date` that returns the year and day of the year.</span></span>

```powershell
Get-Date
```

```Output
Thursday, August 15, 2019 2:26:12 PM
```

```powershell
Import-Module TestModule
Get-Date
```

```Output
19227
```

```powershell
Get-Command Get-Date -All | Format-Table -Property CommandType, Name, ModuleName -AutoSize
```

```Output
CommandType     Name         ModuleName
-----------     ----         ----------
Function        Get-Date     TestModule
Cmdlet          Get-Date     Microsoft.PowerShell.Utility
```

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

```Output
Thursday, August 15, 2019 2:28:31 PM
```

<span data-ttu-id="0f0c3-193">Den första `Get-Date` cmdleten returnerar ett **datetime** -objekt med det aktuella datumet.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-193">The first `Get-Date` cmdlet returns a **DateTime** object with the current date.</span></span> <span data-ttu-id="0f0c3-194">När du har importerat modulen **TestModule** `Get-Date` returnerar året och dagen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-194">After importing the **TestModule** module, `Get-Date` returns the year and day of the year.</span></span>

<span data-ttu-id="0f0c3-195">Använda **alla** -parametrar för `Get-Command` Visa alla `Get-Date` kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-195">Using the **All** parameter of `Get-Command` show all the `Get-Date` commands in the session.</span></span> <span data-ttu-id="0f0c3-196">Resultaten visar att det finns två `Get-Date` kommandon i sessionen, en funktion från modulen **TestModule** och en cmdlet från **Microsoft. PowerShell. Utility** -modulen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-196">The results show that there are two `Get-Date` commands in the session, a function from the **TestModule** module and a cmdlet from the **Microsoft.PowerShell.Utility** module.</span></span>

<span data-ttu-id="0f0c3-197">Eftersom funktioner prioriteras över cmdletar `Get-Date` körs funktionen från **TestModule** -modulen i stället för `Get-Date` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-197">Because functions take precedence over cmdlets, the `Get-Date` function from the **TestModule** module runs, instead of the `Get-Date` cmdlet.</span></span> <span data-ttu-id="0f0c3-198">Om du vill köra den ursprungliga versionen av `Get-Date` måste du kvalificera kommandots namn med modulnamnet.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-198">To run the original version of `Get-Date`, you must qualify the command name with the module name.</span></span>

<span data-ttu-id="0f0c3-199">Mer information om kommando prioritet i PowerShell finns [about_Command_Precedence](about/about_Command_Precedence.md).</span><span class="sxs-lookup"><span data-stu-id="0f0c3-199">For more information about command precedence in PowerShell, see [about_Command_Precedence](about/about_Command_Precedence.md).</span></span>

### <span data-ttu-id="0f0c3-200">Exempel 10: importera en lägsta version av en modul</span><span class="sxs-lookup"><span data-stu-id="0f0c3-200">Example 10: Import a minimum version of a module</span></span>

<span data-ttu-id="0f0c3-201">I det här exemplet importeras modulen **PowerShellGet** .</span><span class="sxs-lookup"><span data-stu-id="0f0c3-201">This example imports the **PowerShellGet** module.</span></span> <span data-ttu-id="0f0c3-202">Den använder **MinimumVersion** -parametern för `Import-Module` för att importera version 2.0.0 eller större av modulen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-202">It uses the **MinimumVersion** parameter of `Import-Module` to import only version 2.0.0 or greater of the module.</span></span>

```powershell
Import-Module -Name PowerShellGet -MinimumVersion 2.0.0
```

<span data-ttu-id="0f0c3-203">Du kan också använda parametern **RequiredVersion** för att importera en viss version av en modul eller använda parametrarna **module** och **version** för `#Requires` nyckelordet för att kräva en viss version av en modul i ett skript.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-203">You can also use the **RequiredVersion** parameter to import a particular version of a module, or use the **Module** and **Version** parameters of the `#Requires` keyword to require a particular version of a module in a script.</span></span>

### <span data-ttu-id="0f0c3-204">Exempel 11: importera med ett fullständigt kvalificerat namn</span><span class="sxs-lookup"><span data-stu-id="0f0c3-204">Example 11: Import using a fully qualified name</span></span>

<span data-ttu-id="0f0c3-205">I det här exemplet importeras en angiven version av en modul med hjälp av FullyQualifiedName.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-205">This example imports a specific version of a module using the FullyQualifiedName.</span></span>

```powershell
PS> Get-Module -ListAvailable PowerShellGet | Select-Object Name, Version

Name          Version
----          -------
PowerShellGet 2.2.1
PowerShellGet 2.1.3
PowerShellGet 2.1.2
PowerShellGet 1.0.0.1

PS> Import-Module -FullyQualifiedName @{ModuleName = 'PowerShellGet'; ModuleVersion = '2.1.3' }
```

### <span data-ttu-id="0f0c3-206">Exempel 12: importera med en fullständigt kvalificerad sökväg</span><span class="sxs-lookup"><span data-stu-id="0f0c3-206">Example 12: Import using a fully qualified path</span></span>

<span data-ttu-id="0f0c3-207">I det här exemplet importeras en särskild version av en modul med hjälp av den fullständigt kvalificerade sökvägen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-207">This example imports a specific version of a module using the fully qualified path.</span></span>

```powershell
PS> Get-Module -ListAvailable PowerShellGet | Select-Object Path

Path
----
C:\Program Files\PowerShell\Modules\PowerShellGet\2.2.1\PowerShellGet.psd1
C:\program files\powershell\6\Modules\PowerShellGet\PowerShellGet.psd1
C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\2.1.2\PowerShellGet.psd1
C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.0.0.1\PowerShellGet.psd1

PS> Import-Module -Name 'C:\Program Files\PowerShell\Modules\PowerShellGet\2.2.1\PowerShellGet.psd1'
```

### <span data-ttu-id="0f0c3-208">Exempel 13: importera en modul från en fjärran sluten dator</span><span class="sxs-lookup"><span data-stu-id="0f0c3-208">Example 13: Import a module from a remote computer</span></span>

<span data-ttu-id="0f0c3-209">Det här exemplet visar hur du använder `Import-Module` cmdleten för att importera en modul från en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-209">This example shows how to use the `Import-Module` cmdlet to import a module from a remote computer.</span></span>
<span data-ttu-id="0f0c3-210">Det här kommandot använder funktionen implicit fjärr kommunikation i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-210">This command uses the Implicit Remoting feature of PowerShell.</span></span>

<span data-ttu-id="0f0c3-211">När du importerar moduler från en annan session kan du använda cmdletarna i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-211">When you import modules from another session, you can use the cmdlets in the current session.</span></span>
<span data-ttu-id="0f0c3-212">Kommandon som använder cmdletarna körs dock i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-212">However, commands that use the cmdlets run in the remote session.</span></span>

```powershell
$s = New-PSSession -ComputerName Server01
Get-Module -PSSession $s -ListAvailable -Name NetSecurity
```

```Output
ModuleType Name             ExportedCommands
---------- ----             ----------------
Manifest   NetSecurity      {New-NetIPsecAuthProposal, New-NetIPsecMainModeCryptoProposal, New-Ne...
```

```powershell
Import-Module -PSSession $s -Name NetSecurity
Get-Command -Module NetSecurity -Name Get-*Firewall*
```

```Output
CommandType     Name                                               ModuleName
-----------     ----                                               ----------
Function        Get-NetFirewallAddressFilter                       NetSecurity
Function        Get-NetFirewallApplicationFilter                   NetSecurity
Function        Get-NetFirewallInterfaceFilter                     NetSecurity
Function        Get-NetFirewallInterfaceTypeFilter                 NetSecurity
Function        Get-NetFirewallPortFilter                          NetSecurity
Function        Get-NetFirewallProfile                             NetSecurity
Function        Get-NetFirewallRule                                NetSecurity
Function        Get-NetFirewallSecurityFilter                      NetSecurity
Function        Get-NetFirewallServiceFilter                       NetSecurity
Function        Get-NetFirewallSetting                             NetSecurity
```

```powershell
Get-NetFirewallRule -DisplayName "Windows Remote Management*" |
  Format-Table -Property DisplayName, Name -AutoSize
```

```Output
DisplayName                                              Name
-----------                                              ----
Windows Remote Management (HTTP-In)                      WINRM-HTTP-In-TCP
Windows Remote Management (HTTP-In)                      WINRM-HTTP-In-TCP-PUBLIC
Windows Remote Management - Compatibility Mode (HTTP-In) WINRM-HTTP-Compat-In-TCP
```

<span data-ttu-id="0f0c3-213">`New-PSSession` skapar en fjärrsession ( **PSSession** ) till Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-213">`New-PSSession` creates a remote session ( **PSSession** ) to the Server01 computer.</span></span> <span data-ttu-id="0f0c3-214">**PSSession** sparas i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-214">The **PSSession** is saved in the `$s` variable.</span></span>

<span data-ttu-id="0f0c3-215">`Get-Module`Om du kör med parametern **PSSession** ser du att **netsecurity** -modulen är installerad och tillgänglig på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-215">Running `Get-Module` with the **PSSession** parameter shows that the **NetSecurity** module is installed and available on the remote computer.</span></span> <span data-ttu-id="0f0c3-216">Det här kommandot motsvarar att använda `Invoke-Command` cmdleten för att köra `Get-Module` kommandot i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-216">This command is equivalent to using the `Invoke-Command` cmdlet to run `Get-Module` command in the remote session.</span></span> <span data-ttu-id="0f0c3-217">Exempel: (`Invoke-Command $s {Get-Module -ListAvailable -Name NetSecurity`</span><span class="sxs-lookup"><span data-stu-id="0f0c3-217">For example: (`Invoke-Command $s {Get-Module -ListAvailable -Name NetSecurity`</span></span>

<span data-ttu-id="0f0c3-218">Om `Import-Module` du kör med **PSSession** -parametern importeras **netsecurity** -modulen från fjärrdatorn till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-218">Running `Import-Module` with the **PSSession** parameter imports the **NetSecurity** module from the remote computer into the current session.</span></span> <span data-ttu-id="0f0c3-219">`Get-Command`Cmdleten används för att hämta kommandon som börjar med **Get** -och include- **brandväggen** från modulen **netsecurity** .</span><span class="sxs-lookup"><span data-stu-id="0f0c3-219">The `Get-Command` cmdlet is used to get commands that begin with **Get** and include **Firewall** from the **NetSecurity** module.</span></span> <span data-ttu-id="0f0c3-220">Utdata bekräftar att modulen och dess cmdlets har importer ATS till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-220">The output confirms that the module and its cmdlets were imported into the current session.</span></span>

<span data-ttu-id="0f0c3-221">Därefter `Get-NetFirewallRule` hämtar cmdlet Windows Remote Management brand Väggs regler på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-221">Next, the `Get-NetFirewallRule` cmdlet gets Windows Remote Management firewall rules on the Server01 computer.</span></span> <span data-ttu-id="0f0c3-222">Detta motsvarar att använda `Invoke-Command` cmdleten för att köras `Get-NetFirewallRule` i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-222">This is equivalent to using the `Invoke-Command` cmdlet to run `Get-NetFirewallRule` on the remote session.</span></span>

### <span data-ttu-id="0f0c3-223">Exempel 14: Hantera lagring på en fjärrdator utan operativ systemet Windows</span><span class="sxs-lookup"><span data-stu-id="0f0c3-223">Example 14: Manage storage on a remote computer without the Windows operating system</span></span>

<span data-ttu-id="0f0c3-224">I det här exemplet har administratören för datorn installerat modulen för modul identifiering, som gör att du kan använda CIM-kommandon som är utformade för providern.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-224">In this example, the administrator of the computer has installed the Module Discovery WMI provider, which allows you to use CIM commands that are designed for the provider.</span></span>

<span data-ttu-id="0f0c3-225">`New-CimSession`Cmdleten skapar en session på den fjärranslutna datorn med namnet RSDGF03.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-225">The `New-CimSession` cmdlet creates a session on the remote computer named RSDGF03.</span></span> <span data-ttu-id="0f0c3-226">Sessionen ansluter till WMI-tjänsten på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-226">The session connects to the WMI service on the remote computer.</span></span> <span data-ttu-id="0f0c3-227">CIM-sessionen sparas i `$cs` variabeln.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-227">The CIM session is saved in the `$cs` variable.</span></span>
<span data-ttu-id="0f0c3-228">`Import-Module` använder **CimSession** i `$cs` för att importera modulen **Storage** CIM från RSDGF03-datorn.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-228">`Import-Module` uses the **CimSession** in `$cs` to import the **Storage** CIM module from the RSDGF03 computer.</span></span>

<span data-ttu-id="0f0c3-229">`Get-Command`Cmdleten visar `Get-Disk` kommandot i modulen **Storage** .</span><span class="sxs-lookup"><span data-stu-id="0f0c3-229">The `Get-Command` cmdlet shows the `Get-Disk` command in the **Storage** module.</span></span> <span data-ttu-id="0f0c3-230">När du importerar en CIM-modul till den lokala sessionen konverterar PowerShell CDXLM-filerna för varje kommando till PowerShell-skript, som visas som funktioner i den lokala sessionen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-230">When you import a CIM module into the local session, PowerShell converts the CDXML files for each command into PowerShell scripts, which appear as functions in the local session.</span></span>

<span data-ttu-id="0f0c3-231">Trots `Get-Disk` att det har skrivits i den lokala sessionen körs cmdleten implicit på den fjärrdator som den importerades från.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-231">Although `Get-Disk` is typed in the local session, the cmdlet implicitly runs on the remote computer from which it was imported.</span></span> <span data-ttu-id="0f0c3-232">Kommandot returnerar objekt från fjärrdatorn till den lokala sessionen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-232">The command returns objects from the remote computer to the local session.</span></span>

```powershell
$cs = New-CimSession -ComputerName RSDGF03
Import-Module -CimSession $cs -Name Storage
# Importing a CIM module, converts the CDXML files for each command into PowerShell scripts.
# These appear as functions in the local session.
Get-Command Get-Disk
```

```Output
CommandType     Name                  ModuleName
-----------     ----                  ----------
Function        Get-Disk              Storage
```

```powershell
# Use implicit remoting to query disks on the remote computer from which the module was imported.
Get-Disk
```

```Output
Number Friendly Name           OperationalStatus  Total Size Partition Style
------ -------------           -----------------  ---------- ---------------
0      Virtual HD ATA Device   Online                  40 GB MBR
```

## <span data-ttu-id="0f0c3-233">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="0f0c3-233">PARAMETERS</span></span>

### <span data-ttu-id="0f0c3-234">-Alias</span><span class="sxs-lookup"><span data-stu-id="0f0c3-234">-Alias</span></span>

<span data-ttu-id="0f0c3-235">Anger alias som denna cmdlet importerar från modulen till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-235">Specifies the aliases that this cmdlet imports from the module into the current session.</span></span> <span data-ttu-id="0f0c3-236">Ange en kommaavgränsad lista över alias.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-236">Enter a comma-separated list of aliases.</span></span> <span data-ttu-id="0f0c3-237">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-237">Wildcard characters are permitted.</span></span>

<span data-ttu-id="0f0c3-238">Vissa moduler exporterar automatiskt markerade alias till sessionen när du importerar modulen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-238">Some modules automatically export selected aliases into your session when you import the module.</span></span>
<span data-ttu-id="0f0c3-239">Med den här parametern kan du välja bland de exporterade aliasen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-239">This parameter lets you select from among the exported aliases.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="0f0c3-240">– Argument List</span><span class="sxs-lookup"><span data-stu-id="0f0c3-240">-ArgumentList</span></span>

<span data-ttu-id="0f0c3-241">Anger en matris med argument, eller parameter värden, som skickas till en skript-modul under `Import-Module` kommandot.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-241">Specifies an array of arguments, or parameter values, that are passed to a script module during the `Import-Module` command.</span></span> <span data-ttu-id="0f0c3-242">Den här parametern är endast giltig när du importerar en-skript-modul.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-242">This parameter is valid only when you're importing a script module.</span></span>

<span data-ttu-id="0f0c3-243">Du kan också referera till parametern **argument List** med dess alias, **argument**.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-243">You can also refer to the **ArgumentList** parameter by its alias, **args**.</span></span> <span data-ttu-id="0f0c3-244">Mer information om beteendet för **argument List** finns [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span><span class="sxs-lookup"><span data-stu-id="0f0c3-244">For more information about the behavior of **ArgumentList** , see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0f0c3-245">-AsCustomObject</span><span class="sxs-lookup"><span data-stu-id="0f0c3-245">-AsCustomObject</span></span>

<span data-ttu-id="0f0c3-246">Anger att denna cmdlet returnerar ett anpassat objekt med medlemmar som representerar medlemmar i den importerade modulen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-246">Indicates that this cmdlet returns a custom object with members that represent the imported module members.</span></span> <span data-ttu-id="0f0c3-247">Den här parametern är endast giltig för skript moduler.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-247">This parameter is valid only for script modules.</span></span>

<span data-ttu-id="0f0c3-248">När du använder **AsCustomObject** -parametern `Import-Module` importerar modulen medlemmar till sessionen och returnerar sedan ett **PSCustomObject** -objekt i stället för ett **PSModuleInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-248">When you use the **AsCustomObject** parameter, `Import-Module` imports the module members into the session and then returns a **PSCustomObject** object instead of a **PSModuleInfo** object.</span></span> <span data-ttu-id="0f0c3-249">Du kan spara det anpassade objektet i en variabel och använda punkt notation för att anropa medlemmarna.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-249">You can save the custom object in a variable and use dot notation to invoke the members.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0f0c3-250">– Sammansättning</span><span class="sxs-lookup"><span data-stu-id="0f0c3-250">-Assembly</span></span>

<span data-ttu-id="0f0c3-251">Anger en matris med sammansättnings objekt.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-251">Specifies an array of assembly objects.</span></span> <span data-ttu-id="0f0c3-252">Denna cmdlet importerar de cmdlets och providers som implementeras i de angivna sammansättnings objekten.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-252">This cmdlet imports the cmdlets and providers implemented in the specified assembly objects.</span></span> <span data-ttu-id="0f0c3-253">Ange en variabel som innehåller sammansättnings objekt eller ett kommando som skapar sammansättnings objekt.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-253">Enter a variable that contains assembly objects or a command that creates assembly objects.</span></span> <span data-ttu-id="0f0c3-254">Du kan också skicka ett sammansättnings objekt till `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="0f0c3-254">You can also pipe an assembly object to `Import-Module`.</span></span>

<span data-ttu-id="0f0c3-255">När du använder den här parametern importeras bara de cmdlets och providers som implementeras av de angivna sammansättningarna.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-255">When you use this parameter, only the cmdlets and providers implemented by the specified assemblies are imported.</span></span> <span data-ttu-id="0f0c3-256">Om modulen innehåller andra filer importeras de inte, och du kanske saknar viktiga medlemmar i modulen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-256">If the module contains other files, they aren't imported, and you might be missing important members of the module.</span></span> <span data-ttu-id="0f0c3-257">Använd den här parametern för att felsöka och testa modulen, eller när du uppmanas att använda den av modulens författare.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-257">Use this parameter for debugging and testing the module, or when you're instructed to use it by the module author.</span></span>

```yaml
Type: System.Reflection.Assembly[]
Parameter Sets: Assembly
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="0f0c3-258">-CimNamespace</span><span class="sxs-lookup"><span data-stu-id="0f0c3-258">-CimNamespace</span></span>

<span data-ttu-id="0f0c3-259">Anger namn området för en alternativ CIM-provider som exponerar CIM-moduler.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-259">Specifies the namespace of an alternate CIM provider that exposes CIM modules.</span></span> <span data-ttu-id="0f0c3-260">Standardvärdet är namn området för WMI-providern för modul identifiering.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-260">The default value is the namespace of the Module Discovery WMI provider.</span></span>

<span data-ttu-id="0f0c3-261">Använd den här parametern för att importera CIM-moduler från datorer och enheter som inte kör ett Windows-operativsystem.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-261">Use this parameter to import CIM modules from computers and devices that aren't running a Windows operating system.</span></span>

<span data-ttu-id="0f0c3-262">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-262">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0f0c3-263">-CimResourceUri</span><span class="sxs-lookup"><span data-stu-id="0f0c3-263">-CimResourceUri</span></span>

<span data-ttu-id="0f0c3-264">Anger en alternativ plats för CIM-moduler.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-264">Specifies an alternate location for CIM modules.</span></span> <span data-ttu-id="0f0c3-265">Standardvärdet är resurs-URI för WMI-providern för module-identifiering på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-265">The default value is the resource URI of the Module Discovery WMI provider on the remote computer.</span></span>

<span data-ttu-id="0f0c3-266">Använd den här parametern för att importera CIM-moduler från datorer och enheter som inte kör ett Windows-operativsystem.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-266">Use this parameter to import CIM modules from computers and devices that aren't running a Windows operating system.</span></span>

<span data-ttu-id="0f0c3-267">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-267">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Uri
Parameter Sets: CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0f0c3-268">– CimSession</span><span class="sxs-lookup"><span data-stu-id="0f0c3-268">-CimSession</span></span>

<span data-ttu-id="0f0c3-269">Anger en CIM-session på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-269">Specifies a CIM session on the remote computer.</span></span> <span data-ttu-id="0f0c3-270">Ange en variabel som innehåller CIM-sessionen eller ett kommando som hämtar CIM-sessionen, till exempel ett [Get-CimSession](../CimCmdlets/Get-CimSession.md) -kommando.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-270">Enter a variable that contains the CIM session or a command that gets the CIM session, such as a [Get-CimSession](../CimCmdlets/Get-CimSession.md) command.</span></span>

<span data-ttu-id="0f0c3-271">`Import-Module` använder CIM-sessionen för att importera moduler från fjärrdatorn till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-271">`Import-Module` uses the CIM session connection to import modules from the remote computer into the current session.</span></span> <span data-ttu-id="0f0c3-272">När du använder kommandona från den importerade modulen i den aktuella sessionen körs kommandona på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-272">When you use the commands from the imported module in the current session, the commands run on the remote computer.</span></span>

<span data-ttu-id="0f0c3-273">Du kan använda den här parametern för att importera moduler från datorer och enheter som inte kör Windows-operativsystemet och Windows-datorer som har PowerShell, men som inte har PowerShell-fjärrkommunikation aktive rad.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-273">You can use this parameter to import modules from computers and devices that aren't running the Windows operating system, and Windows computers that have PowerShell, but don't have PowerShell remoting enabled.</span></span>

<span data-ttu-id="0f0c3-274">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-274">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession
Parameter Sets: CimSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0f0c3-275">-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="0f0c3-275">-Cmdlet</span></span>

<span data-ttu-id="0f0c3-276">Anger en matris med cmdletar som denna cmdlet importerar från modulen till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-276">Specifies an array of cmdlets that this cmdlet imports from the module into the current session.</span></span>
<span data-ttu-id="0f0c3-277">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-277">Wildcard characters are permitted.</span></span>

<span data-ttu-id="0f0c3-278">Vissa moduler exporterar automatiskt valda cmdlets till sessionen när du importerar modulen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-278">Some modules automatically export selected cmdlets into your session when you import the module.</span></span>
<span data-ttu-id="0f0c3-279">Med den här parametern kan du välja bland de exporterade cmdletarna.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-279">This parameter lets you select from among the exported cmdlets.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="0f0c3-280">-DisableNameChecking</span><span class="sxs-lookup"><span data-stu-id="0f0c3-280">-DisableNameChecking</span></span>

<span data-ttu-id="0f0c3-281">Anger att denna cmdlet undertrycker meddelandet som varnar dig när du importerar en cmdlet eller funktion vars namn innehåller ett ej godkänt verb eller ett otillåtet Character.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-281">Indicates that this cmdlet suppresses the message that warns you when you import a cmdlet or function whose name includes an unapproved verb or a prohibited character.</span></span>

<span data-ttu-id="0f0c3-282">Som standard visas följande varnings meddelande när en modul som du importerar exporterar cmdlets eller Functions som har icke-godkända verb i sina namn:</span><span class="sxs-lookup"><span data-stu-id="0f0c3-282">By default, when a module that you import exports cmdlets or functions that have unapproved verbs in their names, PowerShell displays the following warning message:</span></span>

> <span data-ttu-id="0f0c3-283">Varning! vissa importerade kommando namn innehåller icke-godkända verb som kan göra dem mindre synliga.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-283">WARNING: Some imported command names include unapproved verbs which might make them less discoverable.</span></span> <span data-ttu-id="0f0c3-284">Använd verbose-parametern för mer information eller Skriv Get-Verb om du vill visa en lista över godkända verb.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-284">Use the Verbose parameter for more detail or type Get-Verb to see the list of approved verbs.</span></span>

<span data-ttu-id="0f0c3-285">Det här meddelandet är bara en varning.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-285">This message is only a warning.</span></span> <span data-ttu-id="0f0c3-286">Den kompletta modulen importeras fortfarande, inklusive kommandon som inte överensstämmer.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-286">The complete module is still imported, including the non-conforming commands.</span></span> <span data-ttu-id="0f0c3-287">Även om meddelandet visas för modulen användare, bör namngivnings problemet åtgärdas av den som skapade modulen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-287">Although the message is displayed to module users, the naming problem should be fixed by the module author.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0f0c3-288">-Force</span><span class="sxs-lookup"><span data-stu-id="0f0c3-288">-Force</span></span>

<span data-ttu-id="0f0c3-289">Den här parametern gör att en modul läses in eller läses in ovanpå den aktuella.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-289">This parameter causes a module to be loaded, or reloaded, over top of the current one.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0f0c3-290">-FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="0f0c3-290">-FullyQualifiedName</span></span>

<span data-ttu-id="0f0c3-291">Anger modulens fullständigt kvalificerade namn som en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-291">Specifies the fully qualified name of the module as a hash table.</span></span> <span data-ttu-id="0f0c3-292">Värdet kan vara en kombination av strängar och hash-tabeller.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-292">The value can be a combination of strings and hash tables.</span></span> <span data-ttu-id="0f0c3-293">Hash-tabellen har följande nycklar.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-293">The hash table has the following keys.</span></span>

- <span data-ttu-id="0f0c3-294">`ModuleName` - **Krävs** Anger namnet på modulen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-294">`ModuleName` - **Required** Specifies the module name.</span></span>
- <span data-ttu-id="0f0c3-295">`GUID` - **Valfritt** Anger modulens GUID.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-295">`GUID` - **Optional** Specifies the GUID of the module.</span></span>
- <span data-ttu-id="0f0c3-296">Du **måste** också ange en av de tre nycklarna nedan.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-296">It's also **Required** to specify one of the three below keys.</span></span> <span data-ttu-id="0f0c3-297">Nycklarna kan inte användas tillsammans.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-297">These keys can't be used together.</span></span>
  - <span data-ttu-id="0f0c3-298">`ModuleVersion` -Anger en minsta godtagbar version av modulen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-298">`ModuleVersion` - Specifies a minimum acceptable version of the module.</span></span>
  - <span data-ttu-id="0f0c3-299">`RequiredVersion` -Anger en exakt, obligatorisk version av modulen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-299">`RequiredVersion` - Specifies an exact, required version of the module.</span></span>
  - <span data-ttu-id="0f0c3-300">`MaximumVersion` -Anger den högsta godkända versionen av modulen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-300">`MaximumVersion` - Specifies the maximum acceptable version of the module.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: FullyQualifiedName, FullyQualifiedNameAndPSSession, FullyQualifiedNameAndWinCompat
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="0f0c3-301">– Funktion</span><span class="sxs-lookup"><span data-stu-id="0f0c3-301">-Function</span></span>

<span data-ttu-id="0f0c3-302">Anger en matris med funktioner som denna cmdlet importerar från modulen till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-302">Specifies an array of functions that this cmdlet imports from the module into the current session.</span></span>
<span data-ttu-id="0f0c3-303">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-303">Wildcard characters are permitted.</span></span> <span data-ttu-id="0f0c3-304">Vissa moduler exporterar automatiskt markerade funktioner till sessionen när du importerar modulen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-304">Some modules automatically export selected functions into your session when you import the module.</span></span> <span data-ttu-id="0f0c3-305">Med den här parametern kan du välja bland de exporterade funktionerna.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-305">This parameter lets you select from among the exported functions.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="0f0c3-306">– Global</span><span class="sxs-lookup"><span data-stu-id="0f0c3-306">-Global</span></span>

<span data-ttu-id="0f0c3-307">Anger att denna cmdlet importerar moduler till det globala sessionstillståndet så att de är tillgängliga för alla kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-307">Indicates that this cmdlet imports modules into the global session state so they are available to all commands in the session.</span></span>

<span data-ttu-id="0f0c3-308">Som standard, när `Import-Module` cmdlet anropas från kommando tolken, skript filen eller script block, importeras alla kommandon till det globala sessionstillståndet.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-308">By default, when `Import-Module` cmdlet is called from the command prompt, script file, or scriptblock, all the commands are imported into the global session state.</span></span>

<span data-ttu-id="0f0c3-309">Vid anrop från en annan modul `Import-Module` importerar cmdlet kommandon i en modul, inklusive kommandon från kapslade moduler, till den anropande modulens sessionstillstånd.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-309">When invoked from another module, `Import-Module` cmdlet imports the commands in a module, including commands from nested modules, into the calling module's session state.</span></span>

> [!TIP]
> <span data-ttu-id="0f0c3-310">Undvik att anropa inifrån `Import-Module` en modul.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-310">You should avoid calling `Import-Module` from within a module.</span></span> <span data-ttu-id="0f0c3-311">Deklarera i stället mål-modulen som en kapslad modul i den överordnade modulens manifest.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-311">Instead, declare the target module as a nested module in the parent module's manifest.</span></span> <span data-ttu-id="0f0c3-312">Att deklarera kapslade moduler gör det enklare att identifiera beroenden.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-312">Declaring nested modules improves the discoverability of dependencies.</span></span>

<span data-ttu-id="0f0c3-313">Den **globala** parametern motsvarar **omfattnings** parametern med värdet **Global**.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-313">The **Global** parameter is equivalent to the **Scope** parameter with a value of **Global**.</span></span>

<span data-ttu-id="0f0c3-314">Om du vill begränsa vilka kommandon som en modul exporterar, använder du ett `Export-ModuleMember` kommando i modulen script.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-314">To restrict the commands that a module exports, use an `Export-ModuleMember` command in the script module.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0f0c3-315">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="0f0c3-315">-MaximumVersion</span></span>

<span data-ttu-id="0f0c3-316">Anger en högsta version.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-316">Specifies a maximum version.</span></span> <span data-ttu-id="0f0c3-317">Den här cmdleten importerar bara en version av modulen som är mindre än eller lika med det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-317">This cmdlet imports only a version of the module that is less than or equal to the specified value.</span></span> <span data-ttu-id="0f0c3-318">Om ingen version kvalificeras `Import-Module` returneras ett fel.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-318">If no version qualifies, `Import-Module` returns an error.</span></span>

```yaml
Type: System.String
Parameter Sets: Name, PSSession, CimSession, WinCompat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0f0c3-319">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="0f0c3-319">-MinimumVersion</span></span>

<span data-ttu-id="0f0c3-320">Anger en lägsta version.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-320">Specifies a minimum version.</span></span> <span data-ttu-id="0f0c3-321">Den här cmdleten importerar bara en version av modulen som är större än eller lika med det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-321">This cmdlet imports only a version of the module that is greater than or equal to the specified value.</span></span> <span data-ttu-id="0f0c3-322">Använd **MinimumVersion** parameter namn eller dess alias, **version**.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-322">Use the **MinimumVersion** parameter name or its alias, **Version**.</span></span> <span data-ttu-id="0f0c3-323">Om ingen version kvalificeras `Import-Module` genererar ett fel.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-323">If no version qualifies, `Import-Module` generates an error.</span></span>

<span data-ttu-id="0f0c3-324">Om du vill ange en exakt version använder du parametern **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="0f0c3-324">To specify an exact version, use the **RequiredVersion** parameter.</span></span> <span data-ttu-id="0f0c3-325">Du kan också använda **modul** -och **versions** parametrar för **#Requires** nyckelordet för att kräva en speciell version av en modul i ett skript.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-325">You can also use the **Module** and **Version** parameters of the **#Requires** keyword to require a specific version of a module in a script.</span></span>

<span data-ttu-id="0f0c3-326">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-326">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Version
Parameter Sets: Name, PSSession, CimSession, WinCompat
Aliases: Version

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0f0c3-327">-ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="0f0c3-327">-ModuleInfo</span></span>

<span data-ttu-id="0f0c3-328">Anger en matris med modul-objekt som ska importeras.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-328">Specifies an array of module objects to import.</span></span> <span data-ttu-id="0f0c3-329">Ange en variabel som innehåller modulens objekt, eller ett kommando som hämtar modulens objekt, till exempel följande kommando: `Get-Module -ListAvailable` .</span><span class="sxs-lookup"><span data-stu-id="0f0c3-329">Enter a variable that contains the module objects, or a command that gets the module objects, such as the following command: `Get-Module -ListAvailable`.</span></span> <span data-ttu-id="0f0c3-330">Du kan också skicka modul objekt till `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="0f0c3-330">You can also pipe module objects to `Import-Module`.</span></span>

```yaml
Type: System.Management.Automation.PSModuleInfo[]
Parameter Sets: ModuleInfo
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="0f0c3-331">-Name</span><span class="sxs-lookup"><span data-stu-id="0f0c3-331">-Name</span></span>

<span data-ttu-id="0f0c3-332">Anger namnen på de moduler som ska importeras.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-332">Specifies the names of the modules to import.</span></span> <span data-ttu-id="0f0c3-333">Ange namnet på modulen eller namnet på en fil i modulen, till exempel en,, eller en `.psd1` `.psm1` `.dll` `.ps1` fil.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-333">Enter the name of the module or the name of a file in the module, such as a `.psd1`, `.psm1`, `.dll`, or `.ps1` file.</span></span> <span data-ttu-id="0f0c3-334">Fil Sök vägar är valfria.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-334">File paths are optional.</span></span> <span data-ttu-id="0f0c3-335">Jokertecken är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-335">Wildcard characters aren't permitted.</span></span> <span data-ttu-id="0f0c3-336">Du kan också skicka namn och fil namn för moduler till `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="0f0c3-336">You can also pipe module names and filenames to `Import-Module`.</span></span>

<span data-ttu-id="0f0c3-337">Om du utelämnar en sökväg `Import-Module` söker du efter modulen i Sök vägarna som sparats i `$env:PSModulePath` miljö variabeln.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-337">If you omit a path, `Import-Module` looks for the module in the paths saved in the `$env:PSModulePath` environment variable.</span></span>

<span data-ttu-id="0f0c3-338">Ange bara modulnamnet när det är möjligt.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-338">Specify only the module name whenever possible.</span></span> <span data-ttu-id="0f0c3-339">När du anger ett fil namn importeras bara de medlemmar som implementeras i den filen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-339">When you specify a file name, only the members that are implemented in that file are imported.</span></span> <span data-ttu-id="0f0c3-340">Om modulen innehåller andra filer importeras de inte, och du kanske saknar viktiga medlemmar i modulen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-340">If the module contains other files, they aren't imported, and you might be missing important members of the module.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name, PSSession, CimSession, WinCompat
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="0f0c3-341">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="0f0c3-341">-NoClobber</span></span>

<span data-ttu-id="0f0c3-342">Förhindrar att du importerar kommandon som har samma namn som befintliga kommandon i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-342">Prevents importing commands that have the same names as existing commands in the current session.</span></span> <span data-ttu-id="0f0c3-343">Som standard `Import-Module` importerar alla exporterade module-kommandon.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-343">By default, `Import-Module` imports all exported module commands.</span></span>

<span data-ttu-id="0f0c3-344">Kommandon som har samma namn kan dölja eller ersätta kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-344">Commands that have the same names can hide or replace commands in the session.</span></span> <span data-ttu-id="0f0c3-345">Använd **prefix** -eller **NoClobber** -parametrarna för att undvika kommando namns konflikter i en session.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-345">To avoid command name conflicts in a session, use the **Prefix** or **NoClobber** parameters.</span></span> <span data-ttu-id="0f0c3-346">Mer information om namn konflikter och kommando prioritet finns i "moduler och namn konflikter" i [about_Modules](about/about_Modules.md) och [about_Command_Precedence](about/about_Command_Precedence.md).</span><span class="sxs-lookup"><span data-stu-id="0f0c3-346">For more information about name conflicts and command precedence, see "Modules and Name Conflicts" in [about_Modules](about/about_Modules.md) and [about_Command_Precedence](about/about_Command_Precedence.md).</span></span>

<span data-ttu-id="0f0c3-347">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-347">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: NoOverwrite

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0f0c3-348">– PassThru</span><span class="sxs-lookup"><span data-stu-id="0f0c3-348">-PassThru</span></span>

<span data-ttu-id="0f0c3-349">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-349">Returns an object representing the item with which you're working.</span></span> <span data-ttu-id="0f0c3-350">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-350">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0f0c3-351">-Prefix</span><span class="sxs-lookup"><span data-stu-id="0f0c3-351">-Prefix</span></span>

<span data-ttu-id="0f0c3-352">Anger ett prefix som denna cmdlet lägger till i Substantiv i namnen på importerade modul medlemmar.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-352">Specifies a prefix that this cmdlet adds to the nouns in the names of imported module members.</span></span>

<span data-ttu-id="0f0c3-353">Använd den här parametern för att undvika namn konflikter som kan uppstå när olika medlemmar i sessionen har samma namn.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-353">Use this parameter to avoid name conflicts that might occur when different members in the session have the same name.</span></span> <span data-ttu-id="0f0c3-354">Den här parametern ändrar inte modulen och påverkar inte filer som modulen importerar för eget bruk.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-354">This parameter does not change the module, and it does not affect files that the module imports for its own use.</span></span> <span data-ttu-id="0f0c3-355">Dessa kallas kapslade moduler.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-355">These are known as nested modules.</span></span> <span data-ttu-id="0f0c3-356">Denna cmdlet påverkar bara namnen på medlemmar i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-356">This cmdlet affects only the names of members in the current session.</span></span>

<span data-ttu-id="0f0c3-357">Om du till exempel anger prefixet UTC och sedan importerar en `Get-Date` cmdlet, är cmdleten känd i sessionen som `Get-UTCDate` och den förväxlas inte med den ursprungliga `Get-Date` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-357">For example, if you specify the prefix UTC and then import a `Get-Date` cmdlet, the cmdlet is known in the session as `Get-UTCDate`, and it is not confused with the original `Get-Date` cmdlet.</span></span>

<span data-ttu-id="0f0c3-358">Värdet för den här parametern prioriteras över **DefaultCommandPrefix** -egenskapen för modulen, som anger standardprefixet.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-358">The value of this parameter takes precedence over the **DefaultCommandPrefix** property of the module, which specifies the default prefix.</span></span>

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

### <span data-ttu-id="0f0c3-359">– PSSession</span><span class="sxs-lookup"><span data-stu-id="0f0c3-359">-PSSession</span></span>

<span data-ttu-id="0f0c3-360">Anger en PowerShell- **PSSession** (User-Managed session) från vilken denna cmdlet importerar moduler till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-360">Specifies a PowerShell user-managed session ( **PSSession** ) from which this cmdlet imports modules into the current session.</span></span> <span data-ttu-id="0f0c3-361">Ange en variabel som innehåller ett **PSSession** eller ett kommando som hämtar en **PSSession** , till exempel ett `Get-PSSession` kommando.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-361">Enter a variable that contains a **PSSession** or a command that gets a **PSSession** , such as a `Get-PSSession` command.</span></span>

<span data-ttu-id="0f0c3-362">När du importerar en modul från en annan session till den aktuella sessionen kan du använda cmdletar från modulen i den aktuella sessionen, precis som du skulle använda cmdlets från en lokal modul.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-362">When you import a module from a different session into the current session, you can use the cmdlets from the module in the current session, just as you would use cmdlets from a local module.</span></span> <span data-ttu-id="0f0c3-363">Kommandon som använder fjärrcmdlets körs i fjärrsessionen, men fjärrinformationen hanteras i bakgrunden av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-363">Commands that use the remote cmdlets run in the remote session, but the remoting details are managed in the background by PowerShell.</span></span>

<span data-ttu-id="0f0c3-364">Den här parametern använder funktionen implicit fjärr kommunikation i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-364">This parameter uses the Implicit Remoting feature of PowerShell.</span></span> <span data-ttu-id="0f0c3-365">Det motsvarar att använda `Import-PSSession` cmdleten för att importera specifika moduler från en session.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-365">It is equivalent to using the `Import-PSSession` cmdlet to import particular modules from a session.</span></span>

<span data-ttu-id="0f0c3-366">`Import-Module` Det går inte att importera PowerShell Core-moduler från en annan session.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-366">`Import-Module` cannot import PowerShell Core modules from another session.</span></span> <span data-ttu-id="0f0c3-367">PowerShell Core-modulerna har namn som inleds med Microsoft. PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-367">The PowerShell Core modules have names that begin with Microsoft.PowerShell.</span></span>

<span data-ttu-id="0f0c3-368">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-368">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: PSSession, FullyQualifiedNameAndPSSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0f0c3-369">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="0f0c3-369">-RequiredVersion</span></span>

<span data-ttu-id="0f0c3-370">Anger en version av modulen som denna cmdlet importerar.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-370">Specifies a version of the module that this cmdlet imports.</span></span> <span data-ttu-id="0f0c3-371">Om versionen inte är installerad `Import-Module` genererar ett fel.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-371">If the version is not installed, `Import-Module` generates an error.</span></span>

<span data-ttu-id="0f0c3-372">Som standard `Import-Module` importerar modulen utan att kontrol lera versions numret.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-372">By default, `Import-Module` imports the module without checking the version number.</span></span>

<span data-ttu-id="0f0c3-373">Om du vill ange en lägsta version använder du parametern **MinimumVersion** .</span><span class="sxs-lookup"><span data-stu-id="0f0c3-373">To specify a minimum version, use the **MinimumVersion** parameter.</span></span> <span data-ttu-id="0f0c3-374">Du kan också använda **modul** -och **versions** parametrar för **#Requires** nyckelordet för att kräva en speciell version av en modul i ett skript.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-374">You can also use the **Module** and **Version** parameters of the **#Requires** keyword to require a specific version of a module in a script.</span></span>

<span data-ttu-id="0f0c3-375">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-375">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="0f0c3-376">Skript som använder **RequiredVersion** för att importera moduler som ingår i befintliga versioner av Windows operativ system körs inte automatiskt i framtida versioner av Windows operativ system.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-376">Scripts that use **RequiredVersion** to import modules that are included with existing releases of the Windows operating system don't automatically run in future releases of the Windows operating system.</span></span> <span data-ttu-id="0f0c3-377">Detta beror på att PowerShell-modulens versions nummer i framtida versioner av Windows operativ system är högre än versions nummer för modul i befintliga versioner av Windows operativ system.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-377">This is because PowerShell module version numbers in future releases of the Windows operating system are higher than module version numbers in existing releases of the Windows operating system.</span></span>

```yaml
Type: System.Version
Parameter Sets: Name, PSSession, CimSession, WinCompat
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0f0c3-378">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="0f0c3-378">-Scope</span></span>

<span data-ttu-id="0f0c3-379">Anger ett omfång där denna cmdlet importerar modulen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-379">Specifies a scope into which this cmdlet imports the module.</span></span>

<span data-ttu-id="0f0c3-380">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="0f0c3-380">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="0f0c3-381">**Global**.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-381">**Global**.</span></span> <span data-ttu-id="0f0c3-382">Tillgängligt för alla kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-382">Available to all commands in the session.</span></span> <span data-ttu-id="0f0c3-383">Motsvarar den **globala** parametern.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-383">Equivalent to the **Global** parameter.</span></span>
- <span data-ttu-id="0f0c3-384">**Lokal**.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-384">**Local**.</span></span> <span data-ttu-id="0f0c3-385">Endast tillgängligt i det aktuella omfånget.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-385">Available only in the current scope.</span></span>

<span data-ttu-id="0f0c3-386">Som standard, när `Import-Module` cmdlet anropas från kommando tolken, skript filen eller script block, importeras alla kommandon till det globala sessionstillståndet.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-386">By default, when `Import-Module` cmdlet is called from the command prompt, script file, or scriptblock, all the commands are imported into the global session state.</span></span> <span data-ttu-id="0f0c3-387">Du kan använda parametern **-scope** med värdet **lokalt** för att importera modulens innehåll till skriptet eller script block-omfånget.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-387">You can use the **-Scope** parameter with the value of **Local** to import module content into the script or scriptblock scope.</span></span>

<span data-ttu-id="0f0c3-388">Vid anrop från en annan modul `Import-Module` importerar cmdlet kommandon i en modul, inklusive kommandon från kapslade moduler, till anroparens sessionstillstånd.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-388">When invoked from another module, `Import-Module` cmdlet imports the commands in a module, including commands from nested modules, into the caller's session state.</span></span> <span data-ttu-id="0f0c3-389">Ange `-Scope Global` eller `-Global` anger att denna cmdlet importerar moduler till det globala sessionstillståndet så att de är tillgängliga för alla kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-389">Specifying `-Scope Global` or `-Global` indicates that this cmdlet imports modules into the global session state so they are available to all commands in the session.</span></span>

<span data-ttu-id="0f0c3-390">Den **globala** parametern motsvarar **omfattnings** parametern med värdet global.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-390">The **Global** parameter is equivalent to the **Scope** parameter with a value of Global.</span></span>

<span data-ttu-id="0f0c3-391">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-391">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:
Accepted values: Local, Global

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0f0c3-392">– Variabel</span><span class="sxs-lookup"><span data-stu-id="0f0c3-392">-Variable</span></span>

<span data-ttu-id="0f0c3-393">Anger en matris med variabler som denna cmdlet importerar från modulen till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-393">Specifies an array of variables that this cmdlet imports from the module into the current session.</span></span>
<span data-ttu-id="0f0c3-394">Ange en lista med variabler.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-394">Enter a list of variables.</span></span> <span data-ttu-id="0f0c3-395">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-395">Wildcard characters are permitted.</span></span>

<span data-ttu-id="0f0c3-396">Vissa moduler exporterar automatiskt markerade variabler till sessionen när du importerar modulen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-396">Some modules automatically export selected variables into your session when you import the module.</span></span>
<span data-ttu-id="0f0c3-397">Med den här parametern kan du välja bland de exporterade variablerna.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-397">This parameter lets you select from among the exported variables.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="0f0c3-398">-SkipEditionCheck</span><span class="sxs-lookup"><span data-stu-id="0f0c3-398">-SkipEditionCheck</span></span>

<span data-ttu-id="0f0c3-399">Hoppar över kontrollen i `CompatiblePSEditions` fältet.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-399">Skips the check on the `CompatiblePSEditions` field.</span></span>

<span data-ttu-id="0f0c3-400">Tillåter inläsning av en modul från `"$($env:windir)\System32\WindowsPowerShell\v1.0\Modules"` modul-katalogen till PowerShell Core när modulen inte anges `Core` i `CompatiblePSEditions` manifest fältet.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-400">Allows loading a module from the `"$($env:windir)\System32\WindowsPowerShell\v1.0\Modules"` module directory into PowerShell Core when that module does not specify `Core` in the `CompatiblePSEditions` manifest field.</span></span>

<span data-ttu-id="0f0c3-401">När du importerar en modul från en annan sökväg gör den här växeln ingenting, eftersom kontrollen inte utförs.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-401">When importing a module from another path, this switch does nothing, since the check is not performed.</span></span> <span data-ttu-id="0f0c3-402">På Linux och macOS gör den här växeln ingenting.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-402">On Linux and macOS, this switch does nothing.</span></span>

<span data-ttu-id="0f0c3-403">Mer information finns i [about_PowerShell_Editions](About/about_PowerShell_Editions.md).</span><span class="sxs-lookup"><span data-stu-id="0f0c3-403">For more information, see [about_PowerShell_Editions](About/about_PowerShell_Editions.md).</span></span>

> [!WARNING]
> <span data-ttu-id="0f0c3-404">`Import-Module -SkipEditionCheck` är fortfarande troligt att det inte går att importera en modul.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-404">`Import-Module -SkipEditionCheck` is still likely to fail to import a module.</span></span> <span data-ttu-id="0f0c3-405">Även om det lyckas kan det hända att anrop av ett kommando från modulen senare Miss lyckas vid försök att använda ett inkompatibelt API.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-405">Even if it does succeed, invoking a command from the module may later fail when it tries to use an incompatible API.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Name, PSSession, CimSession, FullyQualifiedName, FullyQualifiedNameAndPSSession, Assembly, ModuleInfo
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0f0c3-406">-UseWindowsPowerShell</span><span class="sxs-lookup"><span data-stu-id="0f0c3-406">-UseWindowsPowerShell</span></span>

<span data-ttu-id="0f0c3-407">Läser in modulen med Windows PowerShell-kompatibilitet.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-407">Loads module using Windows PowerShell Compatibility functionality.</span></span> <span data-ttu-id="0f0c3-408">Se [about_Windows_PowerShell_Compatibility](About/about_Windows_PowerShell_Compatibility.md) för mer information.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-408">See [about_Windows_PowerShell_Compatibility](About/about_Windows_PowerShell_Compatibility.md) for more information.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: WinCompat, FullyQualifiedNameAndWinCompat
Aliases: UseWinPS

Required: True
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="0f0c3-409">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0f0c3-409">CommonParameters</span></span>

<span data-ttu-id="0f0c3-410">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-410">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0f0c3-411">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="0f0c3-411">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0f0c3-412">INDATA</span><span class="sxs-lookup"><span data-stu-id="0f0c3-412">INPUTS</span></span>

### <span data-ttu-id="0f0c3-413">System. String, system. Management. Automation. PSModuleInfo, system. Reflection. Assembly</span><span class="sxs-lookup"><span data-stu-id="0f0c3-413">System.String, System.Management.Automation.PSModuleInfo, System.Reflection.Assembly</span></span>

<span data-ttu-id="0f0c3-414">Du kan skicka vidare ett modulnamn, module-objekt eller Assembly-objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-414">You can pipe a module name, module object, or assembly object to this cmdlet.</span></span>

## <span data-ttu-id="0f0c3-415">UTDATA</span><span class="sxs-lookup"><span data-stu-id="0f0c3-415">OUTPUTS</span></span>

### <span data-ttu-id="0f0c3-416">Ingen, system. Management. Automation. PSModuleInfo eller system. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="0f0c3-416">None, System.Management.Automation.PSModuleInfo, or System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="0f0c3-417">`Import-Module`Genererar inga utdata som standard.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-417">By default, `Import-Module` does not generate any output.</span></span> <span data-ttu-id="0f0c3-418">Om du anger parametern **Passthru** genererar cmdleten ett **system. Management. Automation. PSModuleInfo** -objekt som representerar modulen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-418">If you specify the **PassThru** parameter, the cmdlet generates a **System.Management.Automation.PSModuleInfo** object that represents the module.</span></span> <span data-ttu-id="0f0c3-419">Om du anger parametern **AsCustomObject** genereras ett **PSCustomObject** -objekt.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-419">If you specify the **AsCustomObject** parameter, it generates a **PSCustomObject** object.</span></span>

## <span data-ttu-id="0f0c3-420">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="0f0c3-420">NOTES</span></span>

- <span data-ttu-id="0f0c3-421">Innan du kan importera en modul måste modulen vara installerad på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-421">Before you can import a module, the module must be installed on the local computer.</span></span> <span data-ttu-id="0f0c3-422">Därför måste modul katalogen kopieras till en katalog som är tillgänglig för den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-422">That is, the module directory must be copied to a directory that is accessible to your local computer.</span></span> <span data-ttu-id="0f0c3-423">Mer information finns i [about_Modules](About/about_Modules.md).</span><span class="sxs-lookup"><span data-stu-id="0f0c3-423">For more information, see [about_Modules](About/about_Modules.md).</span></span>

  <span data-ttu-id="0f0c3-424">Du kan också använda parametrarna **PSSession** och **CIMSession** för att importera moduler som är installerade på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-424">You can also use the **PSSession** and **CIMSession** parameters to import modules that are installed on remote computers.</span></span> <span data-ttu-id="0f0c3-425">Kommandon som använder cmdletarna i dessa moduler körs dock i fjärrsessionen på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-425">However, commands that use the cmdlets in these modules run in the remote session on the remote computer.</span></span>

- <span data-ttu-id="0f0c3-426">Om du importerar medlemmar med samma namn och samma typ i din session, använder PowerShell medlemmen som importer ATS sist som standard.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-426">If you import members with the same name and the same type into your session, PowerShell uses the member imported last by default.</span></span> <span data-ttu-id="0f0c3-427">Variabler och alias ersätts och originalen är inte tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-427">Variables and aliases are replaced, and the originals aren't accessible.</span></span> <span data-ttu-id="0f0c3-428">Funktioner, cmdletar och providrar är bara skuggade av de nya medlemmarna.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-428">Functions, cmdlets, and providers are merely shadowed by the new members.</span></span> <span data-ttu-id="0f0c3-429">De kan nås genom att kvalificera kommando namnet med namnet på dess snapin-modul, modul eller funktions Sök väg.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-429">They can be accessed by qualifying the command name with the name of its snap-in, module, or function path.</span></span>

- <span data-ttu-id="0f0c3-430">Använd cmdleten för att uppdatera formaterings data för kommandon som har importer ATS från en modul `Update-FormatData` .</span><span class="sxs-lookup"><span data-stu-id="0f0c3-430">To update the formatting data for commands that have been imported from a module, use the `Update-FormatData` cmdlet.</span></span> <span data-ttu-id="0f0c3-431">`Update-FormatData` uppdaterar också formaterings data för kommandon i sessionen som har importer ATS från moduler.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-431">`Update-FormatData` also updates the formatting data for commands in the session that were imported from modules.</span></span> <span data-ttu-id="0f0c3-432">Om format filen för en modul ändras kan du köra ett `Update-FormatData` kommando för att uppdatera formateringen för importerade kommandon.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-432">If the formatting file for a module changes, you can run an `Update-FormatData` command to update the formatting data for imported commands.</span></span> <span data-ttu-id="0f0c3-433">Du behöver inte importera modulen igen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-433">You don't need to import the module again.</span></span>

- <span data-ttu-id="0f0c3-434">Från och med Windows PowerShell 3,0 paketeras de grundläggande kommandon som installeras med PowerShell i moduler.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-434">Starting in Windows PowerShell 3.0, the core commands that are installed with PowerShell are packaged in modules.</span></span> <span data-ttu-id="0f0c3-435">I Windows PowerShell 2,0 och i värd program som skapar äldre sessioner i senare versioner av PowerShell, paketeras huvud kommandona i snapin-moduler ( **PSSnapins** ).</span><span class="sxs-lookup"><span data-stu-id="0f0c3-435">In Windows PowerShell 2.0, and in host programs that create older-style sessions in later versions of PowerShell, the core commands are packaged in snap-ins ( **PSSnapins** ).</span></span> <span data-ttu-id="0f0c3-436">Undantaget är **Microsoft. PowerShell. Core** , som alltid är en snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-436">The exception is **Microsoft.PowerShell.Core** , which is always a snap-in.</span></span> <span data-ttu-id="0f0c3-437">Fjärrsessioner, till exempel de som startas av `New-PSSession` cmdleten, är äldre sessioner som inkluderar grundläggande snapin-moduler.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-437">Also, remote sessions, such as those started by the `New-PSSession` cmdlet, are older-style sessions that include core snap-ins.</span></span>

  <span data-ttu-id="0f0c3-438">Information om **CreateDefault2** -metoden som skapar nyare sessioner med Core-moduler finns i [CreateDefault2-metoden](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2).</span><span class="sxs-lookup"><span data-stu-id="0f0c3-438">For information about the **CreateDefault2** method that creates newer-style sessions with core modules, see the [CreateDefault2 Method](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2).</span></span>

- <span data-ttu-id="0f0c3-439">`Import-Module` Det går inte att importera PowerShell Core-moduler från en annan session.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-439">`Import-Module` cannot import PowerShell Core modules from another session.</span></span> <span data-ttu-id="0f0c3-440">PowerShell Core-modulerna har namn som börjar med `Microsoft.PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="0f0c3-440">The PowerShell Core modules have names that begin with `Microsoft.PowerShell`.</span></span>

- <span data-ttu-id="0f0c3-441">I Windows PowerShell 2,0 fylldes några av egenskapsvärdena för objektet modul, till exempel egenskapsvärdena **ExportedCmdlets** och **NestedModules** , inte förrän modulen importerades och var inte tillgänglig på det modul-objekt som parametern **Passthru** returnerar.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-441">In Windows PowerShell 2.0, some of the property values of the module object, such as the **ExportedCmdlets** and **NestedModules** property values, were not populated until the module was imported and were not available on the module object that the **PassThru** parameter returns.</span></span> <span data-ttu-id="0f0c3-442">I Windows PowerShell 3,0 fylls alla egenskaps värden i modulen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-442">In Windows PowerShell 3.0, all module property values are populated.</span></span>

- <span data-ttu-id="0f0c3-443">Om du försöker importera en modul som innehåller sammansättningar med blandat läge som inte är kompatibla med Windows PowerShell 3,0 `Import-Module` returnerar ett fel meddelande som liknar följande.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-443">If you attempt to import a module that contains mixed-mode assemblies that aren't compatible with Windows PowerShell 3.0, `Import-Module` returns an error message like the following one.</span></span>

  > <span data-ttu-id="0f0c3-444">Import-Module: blandad läges sammansättning har skapats mot version "v 2.0.50727" av körningen och kan inte läsas in i 4,0-körningsmiljön utan ytterligare konfigurations information.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-444">Import-Module : Mixed mode assembly is built against version 'v2.0.50727' of the runtime and cannot be loaded in the 4.0 runtime without additional configuration information.</span></span>

  <span data-ttu-id="0f0c3-445">Det här felet uppstår när en modul som är avsedd för Windows PowerShell 2,0 innehåller minst en sammansättning med blandade moduler, det vill säga en sammansättning som innehåller både hanterad och icke-hanterad kod, till exempel C++ och C#.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-445">This error occurs when a module that is designed for Windows PowerShell 2.0 contains at least one mixed-module assembly, that is, an assembly that includes both managed and non-managed code, such as C++ and C#.</span></span>

  <span data-ttu-id="0f0c3-446">Om du vill importera en modul som innehåller sammansättningar med blandat läge startar du Windows PowerShell 2,0 med hjälp av följande kommando och försöker sedan `Import-Module` igen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-446">To import a module that contains mixed-mode assemblies, start Windows PowerShell 2.0 by using the following command, and then try the `Import-Module` command again.</span></span>

  `PowerShell.exe -Version 2.0`

- <span data-ttu-id="0f0c3-447">Om du vill använda funktionen CIM-sessionen måste fjärrdatorn ha WS-Management fjärr anslutning och Windows Management Instrumentation (WMI), som är Microsofts implementering av Common Information Model (CIM) standard.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-447">To use the CIM session feature, the remote computer must have WS-Management remoting and Windows Management Instrumentation (WMI), which is the Microsoft implementation of the Common Information Model (CIM) standard.</span></span> <span data-ttu-id="0f0c3-448">Datorn måste också ha WMI-providern för modul identifiering eller en alternativ CIM-provider som har samma grundläggande funktioner.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-448">The computer must also have the Module Discovery WMI provider or an alternate CIM provider that has the same basic features.</span></span>

  <span data-ttu-id="0f0c3-449">Du kan använda funktionen för CIM-sessionen på datorer som inte kör ett Windows-operativsystem och på Windows-datorer som har PowerShell, men inte har PowerShell-fjärrkommunikation aktive rad.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-449">You can use the CIM session feature on computers that aren't running a Windows operating system and on Windows computers that have PowerShell, but don't have PowerShell remoting enabled.</span></span>

  <span data-ttu-id="0f0c3-450">Du kan också använda CIM-parametrarna för att hämta CIM-moduler från datorer där PowerShell-fjärrkommunikation är aktiverat, inklusive den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-450">You can also use the CIM parameters to get CIM modules from computers that have PowerShell remoting enabled, including the local computer.</span></span> <span data-ttu-id="0f0c3-451">När du skapar en CIM-session på den lokala datorn använder PowerShell DCOM, i stället för WMI, för att skapa sessionen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-451">When you create a CIM session on the local computer, PowerShell uses DCOM, instead of WMI, to create the session.</span></span>

- <span data-ttu-id="0f0c3-452">Som standard `Import-Module` importerar moduler i det globala omfånget även när de anropas från ett underordnat omfång.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-452">By default, `Import-Module` imports modules in the global scope even when called from a descendant scope.</span></span> <span data-ttu-id="0f0c3-453">Omfattningen på den översta nivån och alla underordnade omfattningar har åtkomst till modulens exporterade element.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-453">The top-level scope and all descendant scopes have access to the module's exported elements.</span></span>

  <span data-ttu-id="0f0c3-454">I ett underordnat omfång `-Scope Local` begränsar importen till det omfånget och alla dess underordnade omfång.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-454">In a descendant scope, `-Scope Local` limits the import to that scope and all its descendant scopes.</span></span> <span data-ttu-id="0f0c3-455">Överordnade omfattningar ser inte de importerade medlemmarna.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-455">Parent scopes then do not see the imported members.</span></span>

  > [!NOTE]
  > <span data-ttu-id="0f0c3-456">`Get-Module` visar alla moduler som lästs in i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-456">`Get-Module` shows all modules loaded in the current session.</span></span> <span data-ttu-id="0f0c3-457">Detta inkluderar moduler som lästs in lokalt i ett underordnat omfång.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-457">This includes modules loaded locally in a descendant scope.</span></span> <span data-ttu-id="0f0c3-458">Använd `Get-Command -Module modulename` för att se vilka medlemmar som läses in i det aktuella omfånget.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-458">Use `Get-Command -Module modulename` to see which members are loaded in the current scope.</span></span>

  <span data-ttu-id="0f0c3-459">Om modulen innehåller klass-och uppräknings definitioner, använder du `using module` i början av skriptet.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-459">If the module includes class and enum definitions, use `using module` at the beginning of your script.</span></span> <span data-ttu-id="0f0c3-460">Detta importerar skripten, inklusive klass-och uppräknings definitioner.</span><span class="sxs-lookup"><span data-stu-id="0f0c3-460">This import the scripts, including the class and enum definitions.</span></span> <span data-ttu-id="0f0c3-461">Mer information finns i [about_Using](About/about_Using.md).</span><span class="sxs-lookup"><span data-stu-id="0f0c3-461">For more information, see [about_Using](About/about_Using.md).</span></span>

## <span data-ttu-id="0f0c3-462">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="0f0c3-462">RELATED LINKS</span></span>

[<span data-ttu-id="0f0c3-463">Exportera – ModuleMember</span><span class="sxs-lookup"><span data-stu-id="0f0c3-463">Export-ModuleMember</span></span>](Export-ModuleMember.md)

[<span data-ttu-id="0f0c3-464">Hämta modul</span><span class="sxs-lookup"><span data-stu-id="0f0c3-464">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="0f0c3-465">Ny modul</span><span class="sxs-lookup"><span data-stu-id="0f0c3-465">New-Module</span></span>](New-Module.md)

[<span data-ttu-id="0f0c3-466">Ta bort modul</span><span class="sxs-lookup"><span data-stu-id="0f0c3-466">Remove-Module</span></span>](Remove-Module.md)

[<span data-ttu-id="0f0c3-467">about_PowerShell_Editions</span><span class="sxs-lookup"><span data-stu-id="0f0c3-467">about_PowerShell_Editions</span></span>](About/about_PowerShell_Editions.md)

