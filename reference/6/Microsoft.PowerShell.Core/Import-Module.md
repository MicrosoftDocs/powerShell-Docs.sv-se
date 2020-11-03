---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 04/08/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/import-module?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Module
ms.openlocfilehash: 4be0e64f05f841f3cf3dfdd8b5f91fdcaa158965
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266895"
---
# <span data-ttu-id="c0c75-103">Import-Module</span><span class="sxs-lookup"><span data-stu-id="c0c75-103">Import-Module</span></span>

## <span data-ttu-id="c0c75-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="c0c75-104">SYNOPSIS</span></span>
<span data-ttu-id="c0c75-105">Lägger till moduler i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-105">Adds modules to the current session.</span></span>

## <span data-ttu-id="c0c75-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c0c75-106">SYNTAX</span></span>

### <span data-ttu-id="c0c75-107">Namn (standard)</span><span class="sxs-lookup"><span data-stu-id="c0c75-107">Name (Default)</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>]  [<CommonParameters>]
```

### <span data-ttu-id="c0c75-108">PSSession</span><span class="sxs-lookup"><span data-stu-id="c0c75-108">PSSession</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] -PSSession <PSSession>  [<CommonParameters>]
```

### <span data-ttu-id="c0c75-109">CimSession</span><span class="sxs-lookup"><span data-stu-id="c0c75-109">CimSession</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] -CimSession <CimSession> [-CimResourceUri <Uri>] [-CimNamespace <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="c0c75-110">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="c0c75-110">FullyQualifiedName</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-FullyQualifiedName] <ModuleSpecification[]>
 [-Function <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force]
 [-SkipEditionCheck] [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking]
 [-NoClobber] [-Scope <String>]  [<CommonParameters>]
```

### <span data-ttu-id="c0c75-111">FullyQualifiedNameAndPSSession</span><span class="sxs-lookup"><span data-stu-id="c0c75-111">FullyQualifiedNameAndPSSession</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-FullyQualifiedName] <ModuleSpecification[]>
 [-Function <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force]
 [-SkipEditionCheck] [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking]
 [-NoClobber] [-Scope <String>] -PSSession <PSSession>  [<CommonParameters>]
```

### <span data-ttu-id="c0c75-112">Sammansättning</span><span class="sxs-lookup"><span data-stu-id="c0c75-112">Assembly</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Assembly] <Assembly[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck]
 [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>]  [<CommonParameters>]
```

### <span data-ttu-id="c0c75-113">ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="c0c75-113">ModuleInfo</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Function <String[]>] [-Cmdlet <String[]>]
 [-Variable <String[]>] [-Alias <String[]>] [-Force] [-SkipEditionCheck] [-PassThru]
 [-AsCustomObject] [-ModuleInfo] <PSModuleInfo[]> [-ArgumentList <Object[]>] [-DisableNameChecking]
 [-NoClobber] [-Scope <String>]  [<CommonParameters>]
```

## <span data-ttu-id="c0c75-114">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="c0c75-114">DESCRIPTION</span></span>

<span data-ttu-id="c0c75-115">`Import-Module`Cmdleten lägger till en eller flera moduler i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-115">The `Import-Module` cmdlet adds one or more modules to the current session.</span></span> <span data-ttu-id="c0c75-116">Från och med PowerShell 3,0 importeras installerade moduler automatiskt till sessionen när du använder kommandon eller providrar i modulen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-116">Starting in PowerShell 3.0, installed modules are automatically imported to the session when you use any commands or providers in the module.</span></span> <span data-ttu-id="c0c75-117">Du kan dock fortfarande använda `Import-Module` kommandot för att importera en modul.</span><span class="sxs-lookup"><span data-stu-id="c0c75-117">However, you can still use the `Import-Module` command to import a module.</span></span>
<span data-ttu-id="c0c75-118">Du kan inaktivera automatisk modul import med hjälp av `$PSModuleAutoloadingPreference` Preference-variabeln.</span><span class="sxs-lookup"><span data-stu-id="c0c75-118">You can disable automatic module importing using the `$PSModuleAutoloadingPreference` preference variable.</span></span> <span data-ttu-id="c0c75-119">Mer information om `$PSModuleAutoloadingPreference` variabeln finns i [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="c0c75-119">For more information about the `$PSModuleAutoloadingPreference` variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="c0c75-120">En modul är ett paket som innehåller medlemmar som kan användas i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c0c75-120">A module is a package that contains members that can be used in PowerShell.</span></span> <span data-ttu-id="c0c75-121">Medlemmar inkluderar cmdlets, providrar, skript, funktioner, variabler och andra verktyg och filer.</span><span class="sxs-lookup"><span data-stu-id="c0c75-121">Members include cmdlets, providers, scripts, functions, variables, and other tools and files.</span></span> <span data-ttu-id="c0c75-122">När en modul har importer ATS kan du använda-modulens medlemmar i sessionen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-122">After a module is imported, you can use the module members in your session.</span></span> <span data-ttu-id="c0c75-123">Mer information om moduler finns i [about_Modules](About/about_Modules.md).</span><span class="sxs-lookup"><span data-stu-id="c0c75-123">For more information about modules, see [about_Modules](About/about_Modules.md).</span></span>

<span data-ttu-id="c0c75-124">Som standard `Import-Module` importerar alla medlemmar som modulen exporterar, men du kan använda **alias** , **funktion** , **cmdlet** och **variabel** parametrar för att begränsa vilka medlemmar som importeras.</span><span class="sxs-lookup"><span data-stu-id="c0c75-124">By default, `Import-Module` imports all members that the module exports, but you can use the **Alias** , **Function** , **Cmdlet** , and **Variable** parameters to restrict which members are imported.</span></span> <span data-ttu-id="c0c75-125">Parametern **NoClobber** förhindrar `Import-Module` import av medlemmar som har samma namn som medlemmar i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-125">The **NoClobber** parameter prevents `Import-Module` from importing members that have the same names as members in the current session.</span></span>

<span data-ttu-id="c0c75-126">`Import-Module` importerar en modul endast till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-126">`Import-Module` imports a module only into the current session.</span></span> <span data-ttu-id="c0c75-127">Om du vill importera modulen till varje ny session lägger du till ett `Import-Module` kommando i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="c0c75-127">To import the module into every new session, add an `Import-Module` command to your PowerShell profile.</span></span> <span data-ttu-id="c0c75-128">Mer information om profiler finns [about_Profiles](About/about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="c0c75-128">For more information about profiles, see [about_Profiles](About/about_Profiles.md).</span></span>

<span data-ttu-id="c0c75-129">Du kan hantera fjärranslutna Windows-datorer som har PowerShell-fjärrkommunikation aktive rad genom att skapa en **PSSession** på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="c0c75-129">You can manage remote Windows computers that have PowerShell remoting enabled by creating a **PSSession** on the remote computer.</span></span> <span data-ttu-id="c0c75-130">Använd sedan **PSSession** -parametern för `Import-Module` för att importera de moduler som är installerade på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="c0c75-130">Then use the **PSSession** parameter of `Import-Module` to import the modules that are installed on the remote computer.</span></span> <span data-ttu-id="c0c75-131">Nu kan du använda de importerade kommandona i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-131">You can now use the imported commands in the current session.</span></span> <span data-ttu-id="c0c75-132">Kommandona körs implicit på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="c0c75-132">The commands implicitly run on the remote computer.</span></span>

<span data-ttu-id="c0c75-133">Från och med Windows PowerShell 3,0 kan du använda `Import-Module` för att importera common information Model (CIM)-moduler, där cmdletarna definieras i cmdlet definition XML-filer (cdxlm).</span><span class="sxs-lookup"><span data-stu-id="c0c75-133">Starting in Windows PowerShell 3.0, you can use `Import-Module` to import Common Information Model (CIM) modules, in which the cmdlets are defined in Cmdlet Definition XML (CDXML) files.</span></span> <span data-ttu-id="c0c75-134">Med den här funktionen kan du använda cmdletar som implementeras i icke-hanterade kod sammansättningar, t. ex. sådana som skrivits i C++.</span><span class="sxs-lookup"><span data-stu-id="c0c75-134">This feature allows you to use cmdlets that are implemented in non-managed code assemblies, such as those written in C++.</span></span>

<span data-ttu-id="c0c75-135">För fjärrdatorer som inte har PowerShell-fjärrkommunikation aktive rad, inklusive datorer som inte kör Windows operativ system, kan du använda **CIMSession** -parametern för `Import-Module` för att importera CIM-moduler från fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="c0c75-135">For remote computers that don't have PowerShell remoting enabled, including computers that aren't running the Windows operating system, you can use the **CIMSession** parameter of `Import-Module` to import CIM modules from the remote computer.</span></span> <span data-ttu-id="c0c75-136">De importerade kommandona körs implicit på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="c0c75-136">The imported commands run implicitly on the remote computer.</span></span> <span data-ttu-id="c0c75-137">En **CIMSession** är en anslutning till Windows Management INSTRUMENTATION (WMI) på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="c0c75-137">A **CIMSession** is a connection to Windows Management Instrumentation (WMI) on the remote computer.</span></span>

## <span data-ttu-id="c0c75-138">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="c0c75-138">EXAMPLES</span></span>

### <span data-ttu-id="c0c75-139">Exempel 1: importera medlemmarna i en modul till den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="c0c75-139">Example 1: Import the members of a module into the current session</span></span>

<span data-ttu-id="c0c75-140">I det här exemplet importeras medlemmarna i **PSDiagnostics** -modulen till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-140">This example imports the members of the **PSDiagnostics** module into the current session.</span></span>

```powershell
Import-Module -Name PSDiagnostics
```

### <span data-ttu-id="c0c75-141">Exempel 2: importera alla moduler som anges av sökvägen till modulen</span><span class="sxs-lookup"><span data-stu-id="c0c75-141">Example 2: Import all modules specified by the module path</span></span>

<span data-ttu-id="c0c75-142">I det här exemplet importeras alla tillgängliga moduler i sökvägen som anges av `$env:PSModulePath` miljö variabeln till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-142">This example imports all available modules in the path specified by the `$env:PSModulePath` environment variable into the current session.</span></span>

```powershell
Get-Module -ListAvailable | Import-Module
```

### <span data-ttu-id="c0c75-143">Exempel 3: Importera medlemmar i flera moduler till den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="c0c75-143">Example 3: Import the members of several modules into the current session</span></span>

<span data-ttu-id="c0c75-144">I det här exemplet importeras medlemmar av **PSDiagnostics** -och **DISM** -modulerna till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-144">This example imports the members of the **PSDiagnostics** and **Dism** modules into the current session.</span></span>

```powershell
$m = Get-Module -ListAvailable PSDiagnostics, Dism
Import-Module -ModuleInfo $m
```

<span data-ttu-id="c0c75-145">`Get-Module`Cmdlet: en hämtar modulen **PSDiagnostics** och **DISM** och sparar objekten i `$m` variabeln.</span><span class="sxs-lookup"><span data-stu-id="c0c75-145">The `Get-Module` cmdlet gets the **PSDiagnostics** and **Dism** modules and saves the objects in the `$m` variable.</span></span> <span data-ttu-id="c0c75-146">**ListAvailable** -parametern krävs när du hämtar moduler som ännu inte har importer ATS till sessionen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-146">The **ListAvailable** parameter is required when you're getting modules that aren't yet imported into the session.</span></span>

<span data-ttu-id="c0c75-147">Parametern **ModuleInfo** i `Import-Module` används för att importera modulerna till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-147">The **ModuleInfo** parameter of `Import-Module` is used to import the modules into the current session.</span></span>

### <span data-ttu-id="c0c75-148">Exempel 4: importera alla moduler som anges av en sökväg</span><span class="sxs-lookup"><span data-stu-id="c0c75-148">Example 4: Import all modules specified by a path</span></span>

<span data-ttu-id="c0c75-149">I det här exemplet används en explicit sökväg för att identifiera den modul som ska importeras.</span><span class="sxs-lookup"><span data-stu-id="c0c75-149">This example uses an explicit path to identify the module to import.</span></span>

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

<span data-ttu-id="c0c75-150">Med hjälp av parametern **verbose** `Import-Module` kan du rapportera förloppet när modulen läses in.</span><span class="sxs-lookup"><span data-stu-id="c0c75-150">Using the **Verbose** parameter causes `Import-Module` to report progress as it loads the module.</span></span>
<span data-ttu-id="c0c75-151">Utan **verbose** -, **Passthru** -eller **AsCustomObject** -parametern `Import-Module` genererar inga utdata när en modul importeras.</span><span class="sxs-lookup"><span data-stu-id="c0c75-151">Without the **Verbose** , **PassThru** , or **AsCustomObject** parameter, `Import-Module` does not generate any output when it imports a module.</span></span>

### <span data-ttu-id="c0c75-152">Exempel 5: begränsa modul medlemmar som importeras till en session</span><span class="sxs-lookup"><span data-stu-id="c0c75-152">Example 5: Restrict module members imported into a session</span></span>

<span data-ttu-id="c0c75-153">I det här exemplet visas hur du begränsar vilka modulblad som importeras till sessionen och kommandots effekter i sessionen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-153">This example shows how to restrict which module members are imported into the session and the effect of this command on the session.</span></span> <span data-ttu-id="c0c75-154">**Funktions** parametern begränsar de medlemmar som importeras från modulen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-154">The **Function** parameter limits the members that are imported from the module.</span></span> <span data-ttu-id="c0c75-155">Du kan också använda parametrarna **alias** , **variabel** och **cmdlet** för att begränsa andra medlemmar som en modul importerar.</span><span class="sxs-lookup"><span data-stu-id="c0c75-155">You can also use the **Alias** , **Variable** , and **Cmdlet** parameters to restrict other members that a module imports.</span></span>

<span data-ttu-id="c0c75-156">`Get-Module`Cmdlet: en hämtar det objekt som representerar **PSDiagnostics** -modulen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-156">The `Get-Module` cmdlet gets the object that represents the **PSDiagnostics** module.</span></span> <span data-ttu-id="c0c75-157">Egenskapen **ExportedCmdlets** visar alla cmdletar som modulen exporterar, även om de inte har importer ATS.</span><span class="sxs-lookup"><span data-stu-id="c0c75-157">The **ExportedCmdlets** property lists all the cmdlets that the module exports, even though they were not all imported.</span></span>

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

<span data-ttu-id="c0c75-158">Om du använder parametern **module** för `Get-Command` cmdleten visas de kommandon som har importer ATS från **PSDiagnostics** -modulen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-158">Using the **Module** parameter of the `Get-Command` cmdlet shows the commands that were imported from the **PSDiagnostics** module.</span></span> <span data-ttu-id="c0c75-159">Resultatet bekräftar att endast `Disable-PSTrace` `Enable-PSTrace` cmdletarna och har importer ATS.</span><span class="sxs-lookup"><span data-stu-id="c0c75-159">The results confirm that only the `Disable-PSTrace` and `Enable-PSTrace` cmdlets were imported.</span></span>

### <span data-ttu-id="c0c75-160">Exempel 6: importera medlemmarna i en modul och Lägg till ett prefix</span><span class="sxs-lookup"><span data-stu-id="c0c75-160">Example 6: Import the members of a module and add a prefix</span></span>

<span data-ttu-id="c0c75-161">Det här exemplet importerar **PSDiagnostics** -modulen till den aktuella sessionen, lägger till ett prefix till medlems namnen och visar sedan de förfasta medlems namnen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-161">This example imports the **PSDiagnostics** module into the current session, adds a prefix to the member names, and then displays the prefixed member names.</span></span> <span data-ttu-id="c0c75-162">Parametern **prefix** för `Import-Module` lägger till **x** -prefixet till alla medlemmar som importeras från modulen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-162">The **Prefix** parameter of `Import-Module` adds the **x** prefix to all members that are imported from the module.</span></span> <span data-ttu-id="c0c75-163">Prefixet gäller endast medlemmarna i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-163">The prefix applies only to the members in the current session.</span></span> <span data-ttu-id="c0c75-164">Modulen ändras inte.</span><span class="sxs-lookup"><span data-stu-id="c0c75-164">It does not change the module.</span></span> <span data-ttu-id="c0c75-165">Parametern **Passthru** returnerar ett modul-objekt som representerar den importerade modulen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-165">The **PassThru** parameter returns a module object that represents the imported module.</span></span>

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

<span data-ttu-id="c0c75-166">`Get-Command` hämtar de medlemmar som har importer ATS från modulen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-166">`Get-Command` gets the members that have been imported from the module.</span></span> <span data-ttu-id="c0c75-167">Utdata visar att modulens medlemmar är korrekt fasta.</span><span class="sxs-lookup"><span data-stu-id="c0c75-167">The output shows that the module members were correctly prefixed.</span></span>

### <span data-ttu-id="c0c75-168">Exempel 7: Hämta och använda ett anpassat objekt</span><span class="sxs-lookup"><span data-stu-id="c0c75-168">Example 7: Get and use a custom object</span></span>

<span data-ttu-id="c0c75-169">Det här exemplet visar hur du hämtar och använder det anpassade objektet som returnerades av **import-module**.</span><span class="sxs-lookup"><span data-stu-id="c0c75-169">This example demonstrates how to get and use the custom object returned by **Import-Module**.</span></span>

<span data-ttu-id="c0c75-170">Anpassade objekt innehåller syntetiska medlemmar som representerar var och en av de importerade modulerna medlemmar.</span><span class="sxs-lookup"><span data-stu-id="c0c75-170">Custom objects include synthetic members that represent each of the imported module members.</span></span> <span data-ttu-id="c0c75-171">Till exempel konverteras cmdletarna och funktionerna i en modul till skript metoder för det anpassade objektet.</span><span class="sxs-lookup"><span data-stu-id="c0c75-171">For example, the cmdlets and functions in a module are converted to script methods of the custom object.</span></span>

<span data-ttu-id="c0c75-172">Anpassade objekt är användbara i skript.</span><span class="sxs-lookup"><span data-stu-id="c0c75-172">Custom objects are useful in scripting.</span></span> <span data-ttu-id="c0c75-173">De är också användbara när flera importerade objekt har samma namn.</span><span class="sxs-lookup"><span data-stu-id="c0c75-173">They are also useful when several imported objects have the same names.</span></span> <span data-ttu-id="c0c75-174">Användning av skript metoden för ett objekt motsvarar att ange det fullständigt kvalificerade namnet på en importerad medlem, inklusive dess modulnamn.</span><span class="sxs-lookup"><span data-stu-id="c0c75-174">Using the script method of an object is equivalent to specifying the fully qualified name of an imported member, including its module name.</span></span>

<span data-ttu-id="c0c75-175">Parametern **AsCustomObject** kan bara användas när du importerar en-skript-modul.</span><span class="sxs-lookup"><span data-stu-id="c0c75-175">The **AsCustomObject** parameter can be used only when importing a script module.</span></span> <span data-ttu-id="c0c75-176">Används `Get-Module` för att avgöra vilka av de tillgängliga modulerna som är en skriptbaserad modul.</span><span class="sxs-lookup"><span data-stu-id="c0c75-176">Use `Get-Module` to determine which of the available modules is a script module.</span></span>

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

<span data-ttu-id="c0c75-177">Skript modulen **show-Calendar** importeras med parametern **AsCustomObject** för att begära ett anpassat objekt och parametern **Passthru** för att returnera objektet.</span><span class="sxs-lookup"><span data-stu-id="c0c75-177">The **Show-Calendar** script module is imported using the **AsCustomObject** parameter to request a custom object and the **PassThru** parameter to return the object.</span></span> <span data-ttu-id="c0c75-178">Det resulterande anpassade objektet sparas i `$a` variabeln.</span><span class="sxs-lookup"><span data-stu-id="c0c75-178">The resulting custom object is saved in the `$a` variable.</span></span>

<span data-ttu-id="c0c75-179">`$a`Variabeln är skickas till `Get-Member` cmdleten för att visa egenskaper och metoder för det sparade objektet.</span><span class="sxs-lookup"><span data-stu-id="c0c75-179">The `$a` variable is piped to the `Get-Member` cmdlet to show the properties and methods of the saved object.</span></span> <span data-ttu-id="c0c75-180">Utdata visar skript metoden **show-Calendar** .</span><span class="sxs-lookup"><span data-stu-id="c0c75-180">The output shows a **Show-Calendar** script method.</span></span>

<span data-ttu-id="c0c75-181">Om du vill anropa skript metoden **show-Calendar** måste metod namnet omges av citat tecken, eftersom namnet innehåller ett bindestreck.</span><span class="sxs-lookup"><span data-stu-id="c0c75-181">To call the **Show-Calendar** script method, the method name must be enclosed in quotation marks because the name includes a hyphen.</span></span>

### <span data-ttu-id="c0c75-182">Exempel 8: importera en modul igen till samma session</span><span class="sxs-lookup"><span data-stu-id="c0c75-182">Example 8: Reimport a module into the same session</span></span>

<span data-ttu-id="c0c75-183">Det här exemplet visar hur du använder **Force** -parametern i `Import-Module` när du importerar om en modul till samma session.</span><span class="sxs-lookup"><span data-stu-id="c0c75-183">This example shows how to use the **Force** parameter of `Import-Module` when you're reimporting a module into the same session.</span></span> <span data-ttu-id="c0c75-184">Parametern **Force** tar bort den inlästa modulen och importerar den sedan igen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-184">The **Force** parameter removes the loaded module and then imports it again.</span></span>

```powershell
Import-Module PSDiagnostics
Import-Module PSDiagnostics -Force -Prefix PS
```

<span data-ttu-id="c0c75-185">Det första kommandot importerar **PSDiagnostics** -modulen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-185">The first command imports the **PSDiagnostics** module.</span></span> <span data-ttu-id="c0c75-186">Det andra kommandot importerar modulen igen, den här gången med hjälp av parametern **prefix** .</span><span class="sxs-lookup"><span data-stu-id="c0c75-186">The second command imports the module again, this time using the **Prefix** parameter.</span></span>

<span data-ttu-id="c0c75-187">Utan **Force** -parametern innehåller sessionen två kopior av varje **PSDiagnostics** -cmdlet, en med standard namnet och en med det förfasta namnet.</span><span class="sxs-lookup"><span data-stu-id="c0c75-187">Without the **Force** parameter, the session would include two copies of each **PSDiagnostics** cmdlet, one with the standard name and one with the prefixed name.</span></span>

### <span data-ttu-id="c0c75-188">Exempel 9: kör kommandon som har dolts av importerade kommandon</span><span class="sxs-lookup"><span data-stu-id="c0c75-188">Example 9: Run commands that have been hidden by imported commands</span></span>

<span data-ttu-id="c0c75-189">Det här exemplet visar hur du kör kommandon som har dolts av importerade kommandon.</span><span class="sxs-lookup"><span data-stu-id="c0c75-189">This example shows how to run commands that have been hidden by imported commands.</span></span> <span data-ttu-id="c0c75-190">Modulen **TestModule** innehåller en funktion med namnet `Get-Date` som returnerar året och dagen på året.</span><span class="sxs-lookup"><span data-stu-id="c0c75-190">The **TestModule** module includes a function named `Get-Date` that returns the year and day of the year.</span></span>

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

<span data-ttu-id="c0c75-191">Den första `Get-Date` cmdleten returnerar ett **datetime** -objekt med det aktuella datumet.</span><span class="sxs-lookup"><span data-stu-id="c0c75-191">The first `Get-Date` cmdlet returns a **DateTime** object with the current date.</span></span> <span data-ttu-id="c0c75-192">När du har importerat modulen **TestModule** `Get-Date` returnerar året och dagen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-192">After importing the **TestModule** module, `Get-Date` returns the year and day of the year.</span></span>

<span data-ttu-id="c0c75-193">Använda **alla** -parametrar för `Get-Command` Visa alla `Get-Date` kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-193">Using the **All** parameter of `Get-Command` show all the `Get-Date` commands in the session.</span></span> <span data-ttu-id="c0c75-194">Resultaten visar att det finns två `Get-Date` kommandon i sessionen, en funktion från modulen **TestModule** och en cmdlet från **Microsoft. PowerShell. Utility** -modulen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-194">The results show that there are two `Get-Date` commands in the session, a function from the **TestModule** module and a cmdlet from the **Microsoft.PowerShell.Utility** module.</span></span>

<span data-ttu-id="c0c75-195">Eftersom funktioner prioriteras över cmdletar `Get-Date` körs funktionen från **TestModule** -modulen i stället för `Get-Date` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c0c75-195">Because functions take precedence over cmdlets, the `Get-Date` function from the **TestModule** module runs, instead of the `Get-Date` cmdlet.</span></span> <span data-ttu-id="c0c75-196">Om du vill köra den ursprungliga versionen av `Get-Date` måste du kvalificera kommandots namn med modulnamnet.</span><span class="sxs-lookup"><span data-stu-id="c0c75-196">To run the original version of `Get-Date`, you must qualify the command name with the module name.</span></span>

<span data-ttu-id="c0c75-197">Mer information om kommando prioritet i PowerShell finns [about_Command_Precedence](about/about_Command_Precedence.md).</span><span class="sxs-lookup"><span data-stu-id="c0c75-197">For more information about command precedence in PowerShell, see [about_Command_Precedence](about/about_Command_Precedence.md).</span></span>

### <span data-ttu-id="c0c75-198">Exempel 10: importera en lägsta version av en modul</span><span class="sxs-lookup"><span data-stu-id="c0c75-198">Example 10: Import a minimum version of a module</span></span>

<span data-ttu-id="c0c75-199">I det här exemplet importeras modulen **PowerShellGet** .</span><span class="sxs-lookup"><span data-stu-id="c0c75-199">This example imports the **PowerShellGet** module.</span></span> <span data-ttu-id="c0c75-200">Den använder **MinimumVersion** -parametern för `Import-Module` för att importera version 2.0.0 eller större av modulen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-200">It uses the **MinimumVersion** parameter of `Import-Module` to import only version 2.0.0 or greater of the module.</span></span>

```powershell
Import-Module -Name PowerShellGet -MinimumVersion 2.0.0
```

<span data-ttu-id="c0c75-201">Du kan också använda parametern **RequiredVersion** för att importera en viss version av en modul eller använda parametrarna **module** och **version** för `#Requires` nyckelordet för att kräva en viss version av en modul i ett skript.</span><span class="sxs-lookup"><span data-stu-id="c0c75-201">You can also use the **RequiredVersion** parameter to import a particular version of a module, or use the **Module** and **Version** parameters of the `#Requires` keyword to require a particular version of a module in a script.</span></span>

### <span data-ttu-id="c0c75-202">Exempel 11: importera med ett fullständigt kvalificerat namn</span><span class="sxs-lookup"><span data-stu-id="c0c75-202">Example 11: Import using a fully qualified name</span></span>

<span data-ttu-id="c0c75-203">I det här exemplet importeras en angiven version av en modul med hjälp av FullyQualifiedName.</span><span class="sxs-lookup"><span data-stu-id="c0c75-203">This example imports a specific version of a module using the FullyQualifiedName.</span></span>

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

### <span data-ttu-id="c0c75-204">Exempel 12: importera med en fullständigt kvalificerad sökväg</span><span class="sxs-lookup"><span data-stu-id="c0c75-204">Example 12: Import using a fully qualified path</span></span>

<span data-ttu-id="c0c75-205">I det här exemplet importeras en särskild version av en modul med hjälp av den fullständigt kvalificerade sökvägen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-205">This example imports a specific version of a module using the fully qualified path.</span></span>

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

### <span data-ttu-id="c0c75-206">Exempel 13: importera en modul från en fjärran sluten dator</span><span class="sxs-lookup"><span data-stu-id="c0c75-206">Example 13: Import a module from a remote computer</span></span>

<span data-ttu-id="c0c75-207">Det här exemplet visar hur du använder `Import-Module` cmdleten för att importera en modul från en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="c0c75-207">This example shows how to use the `Import-Module` cmdlet to import a module from a remote computer.</span></span>
<span data-ttu-id="c0c75-208">Det här kommandot använder funktionen implicit fjärr kommunikation i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c0c75-208">This command uses the Implicit Remoting feature of PowerShell.</span></span>

<span data-ttu-id="c0c75-209">När du importerar moduler från en annan session kan du använda cmdletarna i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-209">When you import modules from another session, you can use the cmdlets in the current session.</span></span>
<span data-ttu-id="c0c75-210">Kommandon som använder cmdletarna körs dock i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-210">However, commands that use the cmdlets run in the remote session.</span></span>

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

<span data-ttu-id="c0c75-211">`New-PSSession` skapar en fjärrsession ( **PSSession** ) till Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="c0c75-211">`New-PSSession` creates a remote session ( **PSSession** ) to the Server01 computer.</span></span> <span data-ttu-id="c0c75-212">**PSSession** sparas i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="c0c75-212">The **PSSession** is saved in the `$s` variable.</span></span>

<span data-ttu-id="c0c75-213">`Get-Module`Om du kör med parametern **PSSession** ser du att **netsecurity** -modulen är installerad och tillgänglig på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="c0c75-213">Running `Get-Module` with the **PSSession** parameter shows that the **NetSecurity** module is installed and available on the remote computer.</span></span> <span data-ttu-id="c0c75-214">Det här kommandot motsvarar att använda `Invoke-Command` cmdleten för att köra `Get-Module` kommandot i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-214">This command is equivalent to using the `Invoke-Command` cmdlet to run `Get-Module` command in the remote session.</span></span> <span data-ttu-id="c0c75-215">Exempel: (`Invoke-Command $s {Get-Module -ListAvailable -Name NetSecurity`</span><span class="sxs-lookup"><span data-stu-id="c0c75-215">For example: (`Invoke-Command $s {Get-Module -ListAvailable -Name NetSecurity`</span></span>

<span data-ttu-id="c0c75-216">Om `Import-Module` du kör med **PSSession** -parametern importeras **netsecurity** -modulen från fjärrdatorn till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-216">Running `Import-Module` with the **PSSession** parameter imports the **NetSecurity** module from the remote computer into the current session.</span></span> <span data-ttu-id="c0c75-217">`Get-Command`Cmdleten används för att hämta kommandon som börjar med **Get** -och include- **brandväggen** från modulen **netsecurity** .</span><span class="sxs-lookup"><span data-stu-id="c0c75-217">The `Get-Command` cmdlet is used to get commands that begin with **Get** and include **Firewall** from the **NetSecurity** module.</span></span> <span data-ttu-id="c0c75-218">Utdata bekräftar att modulen och dess cmdlets har importer ATS till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-218">The output confirms that the module and its cmdlets were imported into the current session.</span></span>

<span data-ttu-id="c0c75-219">Därefter `Get-NetFirewallRule` hämtar cmdlet Windows Remote Management brand Väggs regler på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="c0c75-219">Next, the `Get-NetFirewallRule` cmdlet gets Windows Remote Management firewall rules on the Server01 computer.</span></span> <span data-ttu-id="c0c75-220">Detta motsvarar att använda `Invoke-Command` cmdleten för att köras `Get-NetFirewallRule` i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-220">This is equivalent to using the `Invoke-Command` cmdlet to run `Get-NetFirewallRule` on the remote session.</span></span>

### <span data-ttu-id="c0c75-221">Exempel 14: Hantera lagring på en fjärrdator utan operativ systemet Windows</span><span class="sxs-lookup"><span data-stu-id="c0c75-221">Example 14: Manage storage on a remote computer without the Windows operating system</span></span>

<span data-ttu-id="c0c75-222">I det här exemplet har administratören för datorn installerat modulen för modul identifiering, som gör att du kan använda CIM-kommandon som är utformade för providern.</span><span class="sxs-lookup"><span data-stu-id="c0c75-222">In this example, the administrator of the computer has installed the Module Discovery WMI provider, which allows you to use CIM commands that are designed for the provider.</span></span>

<span data-ttu-id="c0c75-223">`New-CimSession`Cmdleten skapar en session på den fjärranslutna datorn med namnet RSDGF03.</span><span class="sxs-lookup"><span data-stu-id="c0c75-223">The `New-CimSession` cmdlet creates a session on the remote computer named RSDGF03.</span></span> <span data-ttu-id="c0c75-224">Sessionen ansluter till WMI-tjänsten på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="c0c75-224">The session connects to the WMI service on the remote computer.</span></span> <span data-ttu-id="c0c75-225">CIM-sessionen sparas i `$cs` variabeln.</span><span class="sxs-lookup"><span data-stu-id="c0c75-225">The CIM session is saved in the `$cs` variable.</span></span>
<span data-ttu-id="c0c75-226">`Import-Module` använder **CimSession** i `$cs` för att importera modulen **Storage** CIM från RSDGF03-datorn.</span><span class="sxs-lookup"><span data-stu-id="c0c75-226">`Import-Module` uses the **CimSession** in `$cs` to import the **Storage** CIM module from the RSDGF03 computer.</span></span>

<span data-ttu-id="c0c75-227">`Get-Command`Cmdleten visar `Get-Disk` kommandot i modulen **Storage** .</span><span class="sxs-lookup"><span data-stu-id="c0c75-227">The `Get-Command` cmdlet shows the `Get-Disk` command in the **Storage** module.</span></span> <span data-ttu-id="c0c75-228">När du importerar en CIM-modul till den lokala sessionen konverterar PowerShell CDXLM-filerna för varje kommando till PowerShell-skript, som visas som funktioner i den lokala sessionen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-228">When you import a CIM module into the local session, PowerShell converts the CDXML files for each command into PowerShell scripts, which appear as functions in the local session.</span></span>

<span data-ttu-id="c0c75-229">Trots `Get-Disk` att det har skrivits i den lokala sessionen körs cmdleten implicit på den fjärrdator som den importerades från.</span><span class="sxs-lookup"><span data-stu-id="c0c75-229">Although `Get-Disk` is typed in the local session, the cmdlet implicitly runs on the remote computer from which it was imported.</span></span> <span data-ttu-id="c0c75-230">Kommandot returnerar objekt från fjärrdatorn till den lokala sessionen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-230">The command returns objects from the remote computer to the local session.</span></span>

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

## <span data-ttu-id="c0c75-231">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="c0c75-231">PARAMETERS</span></span>

### <span data-ttu-id="c0c75-232">-Alias</span><span class="sxs-lookup"><span data-stu-id="c0c75-232">-Alias</span></span>

<span data-ttu-id="c0c75-233">Anger alias som denna cmdlet importerar från modulen till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-233">Specifies the aliases that this cmdlet imports from the module into the current session.</span></span> <span data-ttu-id="c0c75-234">Ange en kommaavgränsad lista över alias.</span><span class="sxs-lookup"><span data-stu-id="c0c75-234">Enter a comma-separated list of aliases.</span></span> <span data-ttu-id="c0c75-235">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="c0c75-235">Wildcard characters are permitted.</span></span>

<span data-ttu-id="c0c75-236">Vissa moduler exporterar automatiskt markerade alias till sessionen när du importerar modulen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-236">Some modules automatically export selected aliases into your session when you import the module.</span></span>
<span data-ttu-id="c0c75-237">Med den här parametern kan du välja bland de exporterade aliasen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-237">This parameter lets you select from among the exported aliases.</span></span>

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

### <span data-ttu-id="c0c75-238">– Argument List</span><span class="sxs-lookup"><span data-stu-id="c0c75-238">-ArgumentList</span></span>

<span data-ttu-id="c0c75-239">Anger en matris med argument, eller parameter värden, som skickas till en skript-modul under `Import-Module` kommandot.</span><span class="sxs-lookup"><span data-stu-id="c0c75-239">Specifies an array of arguments, or parameter values, that are passed to a script module during the `Import-Module` command.</span></span> <span data-ttu-id="c0c75-240">Den här parametern är endast giltig när du importerar en-skript-modul.</span><span class="sxs-lookup"><span data-stu-id="c0c75-240">This parameter is valid only when you're importing a script module.</span></span>

<span data-ttu-id="c0c75-241">Du kan också referera till parametern **argument List** med dess alias, **argument**.</span><span class="sxs-lookup"><span data-stu-id="c0c75-241">You can also refer to the **ArgumentList** parameter by its alias, **args**.</span></span> <span data-ttu-id="c0c75-242">Mer information om beteendet för **argument List** finns [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span><span class="sxs-lookup"><span data-stu-id="c0c75-242">For more information about the behavior of **ArgumentList** , see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

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

### <span data-ttu-id="c0c75-243">-AsCustomObject</span><span class="sxs-lookup"><span data-stu-id="c0c75-243">-AsCustomObject</span></span>

<span data-ttu-id="c0c75-244">Anger att denna cmdlet returnerar ett anpassat objekt med medlemmar som representerar medlemmar i den importerade modulen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-244">Indicates that this cmdlet returns a custom object with members that represent the imported module members.</span></span> <span data-ttu-id="c0c75-245">Den här parametern är endast giltig för skript moduler.</span><span class="sxs-lookup"><span data-stu-id="c0c75-245">This parameter is valid only for script modules.</span></span>

<span data-ttu-id="c0c75-246">När du använder **AsCustomObject** -parametern `Import-Module` importerar modulen medlemmar till sessionen och returnerar sedan ett **PSCustomObject** -objekt i stället för ett **PSModuleInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="c0c75-246">When you use the **AsCustomObject** parameter, `Import-Module` imports the module members into the session and then returns a **PSCustomObject** object instead of a **PSModuleInfo** object.</span></span> <span data-ttu-id="c0c75-247">Du kan spara det anpassade objektet i en variabel och använda punkt notation för att anropa medlemmarna.</span><span class="sxs-lookup"><span data-stu-id="c0c75-247">You can save the custom object in a variable and use dot notation to invoke the members.</span></span>

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

### <span data-ttu-id="c0c75-248">– Sammansättning</span><span class="sxs-lookup"><span data-stu-id="c0c75-248">-Assembly</span></span>

<span data-ttu-id="c0c75-249">Anger en matris med sammansättnings objekt.</span><span class="sxs-lookup"><span data-stu-id="c0c75-249">Specifies an array of assembly objects.</span></span> <span data-ttu-id="c0c75-250">Denna cmdlet importerar de cmdlets och providers som implementeras i de angivna sammansättnings objekten.</span><span class="sxs-lookup"><span data-stu-id="c0c75-250">This cmdlet imports the cmdlets and providers implemented in the specified assembly objects.</span></span> <span data-ttu-id="c0c75-251">Ange en variabel som innehåller sammansättnings objekt eller ett kommando som skapar sammansättnings objekt.</span><span class="sxs-lookup"><span data-stu-id="c0c75-251">Enter a variable that contains assembly objects or a command that creates assembly objects.</span></span> <span data-ttu-id="c0c75-252">Du kan också skicka ett sammansättnings objekt till `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="c0c75-252">You can also pipe an assembly object to `Import-Module`.</span></span>

<span data-ttu-id="c0c75-253">När du använder den här parametern importeras bara de cmdlets och providers som implementeras av de angivna sammansättningarna.</span><span class="sxs-lookup"><span data-stu-id="c0c75-253">When you use this parameter, only the cmdlets and providers implemented by the specified assemblies are imported.</span></span> <span data-ttu-id="c0c75-254">Om modulen innehåller andra filer importeras de inte, och du kanske saknar viktiga medlemmar i modulen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-254">If the module contains other files, they aren't imported, and you might be missing important members of the module.</span></span> <span data-ttu-id="c0c75-255">Använd den här parametern för att felsöka och testa modulen, eller när du uppmanas att använda den av modulens författare.</span><span class="sxs-lookup"><span data-stu-id="c0c75-255">Use this parameter for debugging and testing the module, or when you're instructed to use it by the module author.</span></span>

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

### <span data-ttu-id="c0c75-256">-CimNamespace</span><span class="sxs-lookup"><span data-stu-id="c0c75-256">-CimNamespace</span></span>

<span data-ttu-id="c0c75-257">Anger namn området för en alternativ CIM-provider som exponerar CIM-moduler.</span><span class="sxs-lookup"><span data-stu-id="c0c75-257">Specifies the namespace of an alternate CIM provider that exposes CIM modules.</span></span> <span data-ttu-id="c0c75-258">Standardvärdet är namn området för WMI-providern för modul identifiering.</span><span class="sxs-lookup"><span data-stu-id="c0c75-258">The default value is the namespace of the Module Discovery WMI provider.</span></span>

<span data-ttu-id="c0c75-259">Använd den här parametern för att importera CIM-moduler från datorer och enheter som inte kör ett Windows-operativsystem.</span><span class="sxs-lookup"><span data-stu-id="c0c75-259">Use this parameter to import CIM modules from computers and devices that aren't running a Windows operating system.</span></span>

<span data-ttu-id="c0c75-260">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c0c75-260">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="c0c75-261">-CimResourceUri</span><span class="sxs-lookup"><span data-stu-id="c0c75-261">-CimResourceUri</span></span>

<span data-ttu-id="c0c75-262">Anger en alternativ plats för CIM-moduler.</span><span class="sxs-lookup"><span data-stu-id="c0c75-262">Specifies an alternate location for CIM modules.</span></span> <span data-ttu-id="c0c75-263">Standardvärdet är resurs-URI för WMI-providern för module-identifiering på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="c0c75-263">The default value is the resource URI of the Module Discovery WMI provider on the remote computer.</span></span>

<span data-ttu-id="c0c75-264">Använd den här parametern för att importera CIM-moduler från datorer och enheter som inte kör ett Windows-operativsystem.</span><span class="sxs-lookup"><span data-stu-id="c0c75-264">Use this parameter to import CIM modules from computers and devices that aren't running a Windows operating system.</span></span>

<span data-ttu-id="c0c75-265">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c0c75-265">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="c0c75-266">– CimSession</span><span class="sxs-lookup"><span data-stu-id="c0c75-266">-CimSession</span></span>

<span data-ttu-id="c0c75-267">Anger en CIM-session på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="c0c75-267">Specifies a CIM session on the remote computer.</span></span> <span data-ttu-id="c0c75-268">Ange en variabel som innehåller CIM-sessionen eller ett kommando som hämtar CIM-sessionen, till exempel ett [Get-CimSession](../CimCmdlets/Get-CimSession.md) -kommando.</span><span class="sxs-lookup"><span data-stu-id="c0c75-268">Enter a variable that contains the CIM session or a command that gets the CIM session, such as a [Get-CimSession](../CimCmdlets/Get-CimSession.md) command.</span></span>

<span data-ttu-id="c0c75-269">`Import-Module` använder CIM-sessionen för att importera moduler från fjärrdatorn till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-269">`Import-Module` uses the CIM session connection to import modules from the remote computer into the current session.</span></span> <span data-ttu-id="c0c75-270">När du använder kommandona från den importerade modulen i den aktuella sessionen körs kommandona på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="c0c75-270">When you use the commands from the imported module in the current session, the commands run on the remote computer.</span></span>

<span data-ttu-id="c0c75-271">Du kan använda den här parametern för att importera moduler från datorer och enheter som inte kör Windows-operativsystemet och Windows-datorer som har PowerShell, men som inte har PowerShell-fjärrkommunikation aktive rad.</span><span class="sxs-lookup"><span data-stu-id="c0c75-271">You can use this parameter to import modules from computers and devices that aren't running the Windows operating system, and Windows computers that have PowerShell, but don't have PowerShell remoting enabled.</span></span>

<span data-ttu-id="c0c75-272">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c0c75-272">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="c0c75-273">-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="c0c75-273">-Cmdlet</span></span>

<span data-ttu-id="c0c75-274">Anger en matris med cmdletar som denna cmdlet importerar från modulen till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-274">Specifies an array of cmdlets that this cmdlet imports from the module into the current session.</span></span>
<span data-ttu-id="c0c75-275">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="c0c75-275">Wildcard characters are permitted.</span></span>

<span data-ttu-id="c0c75-276">Vissa moduler exporterar automatiskt valda cmdlets till sessionen när du importerar modulen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-276">Some modules automatically export selected cmdlets into your session when you import the module.</span></span>
<span data-ttu-id="c0c75-277">Med den här parametern kan du välja bland de exporterade cmdletarna.</span><span class="sxs-lookup"><span data-stu-id="c0c75-277">This parameter lets you select from among the exported cmdlets.</span></span>

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

### <span data-ttu-id="c0c75-278">-DisableNameChecking</span><span class="sxs-lookup"><span data-stu-id="c0c75-278">-DisableNameChecking</span></span>

<span data-ttu-id="c0c75-279">Anger att denna cmdlet undertrycker meddelandet som varnar dig när du importerar en cmdlet eller funktion vars namn innehåller ett ej godkänt verb eller ett otillåtet Character.</span><span class="sxs-lookup"><span data-stu-id="c0c75-279">Indicates that this cmdlet suppresses the message that warns you when you import a cmdlet or function whose name includes an unapproved verb or a prohibited character.</span></span>

<span data-ttu-id="c0c75-280">Som standard visas följande varnings meddelande när en modul som du importerar exporterar cmdlets eller Functions som har icke-godkända verb i sina namn:</span><span class="sxs-lookup"><span data-stu-id="c0c75-280">By default, when a module that you import exports cmdlets or functions that have unapproved verbs in their names, PowerShell displays the following warning message:</span></span>

> <span data-ttu-id="c0c75-281">Varning! vissa importerade kommando namn innehåller icke-godkända verb som kan göra dem mindre synliga.</span><span class="sxs-lookup"><span data-stu-id="c0c75-281">WARNING: Some imported command names include unapproved verbs which might make them less discoverable.</span></span> <span data-ttu-id="c0c75-282">Använd verbose-parametern för mer information eller Skriv Get-Verb om du vill visa en lista över godkända verb.</span><span class="sxs-lookup"><span data-stu-id="c0c75-282">Use the Verbose parameter for more detail or type Get-Verb to see the list of approved verbs.</span></span>

<span data-ttu-id="c0c75-283">Det här meddelandet är bara en varning.</span><span class="sxs-lookup"><span data-stu-id="c0c75-283">This message is only a warning.</span></span> <span data-ttu-id="c0c75-284">Den kompletta modulen importeras fortfarande, inklusive kommandon som inte överensstämmer.</span><span class="sxs-lookup"><span data-stu-id="c0c75-284">The complete module is still imported, including the non-conforming commands.</span></span> <span data-ttu-id="c0c75-285">Även om meddelandet visas för modulen användare, bör namngivnings problemet åtgärdas av den som skapade modulen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-285">Although the message is displayed to module users, the naming problem should be fixed by the module author.</span></span>

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

### <span data-ttu-id="c0c75-286">-Force</span><span class="sxs-lookup"><span data-stu-id="c0c75-286">-Force</span></span>

<span data-ttu-id="c0c75-287">Den här parametern gör att en modul läses in eller läses in ovanpå den aktuella.</span><span class="sxs-lookup"><span data-stu-id="c0c75-287">This parameter causes a module to be loaded, or reloaded, over top of the current one.</span></span>

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

### <span data-ttu-id="c0c75-288">-FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="c0c75-288">-FullyQualifiedName</span></span>

<span data-ttu-id="c0c75-289">Anger modulens fullständigt kvalificerade namn som en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="c0c75-289">Specifies the fully qualified name of the module as a hash table.</span></span> <span data-ttu-id="c0c75-290">Värdet kan vara en kombination av strängar och hash-tabeller.</span><span class="sxs-lookup"><span data-stu-id="c0c75-290">The value can be a combination of strings and hash tables.</span></span> <span data-ttu-id="c0c75-291">Hash-tabellen har följande nycklar.</span><span class="sxs-lookup"><span data-stu-id="c0c75-291">The hash table has the following keys.</span></span>

- <span data-ttu-id="c0c75-292">`ModuleName` - **Krävs** Anger namnet på modulen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-292">`ModuleName` - **Required** Specifies the module name.</span></span>
- <span data-ttu-id="c0c75-293">`GUID` - **Valfritt** Anger modulens GUID.</span><span class="sxs-lookup"><span data-stu-id="c0c75-293">`GUID` - **Optional** Specifies the GUID of the module.</span></span>
- <span data-ttu-id="c0c75-294">Du **måste** också ange en av de tre nycklarna nedan.</span><span class="sxs-lookup"><span data-stu-id="c0c75-294">It's also **Required** to specify one of the three below keys.</span></span> <span data-ttu-id="c0c75-295">Nycklarna kan inte användas tillsammans.</span><span class="sxs-lookup"><span data-stu-id="c0c75-295">These keys can't be used together.</span></span>
  - <span data-ttu-id="c0c75-296">`ModuleVersion` -Anger en minsta godtagbar version av modulen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-296">`ModuleVersion` - Specifies a minimum acceptable version of the module.</span></span>
  - <span data-ttu-id="c0c75-297">`RequiredVersion` -Anger en exakt, obligatorisk version av modulen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-297">`RequiredVersion` - Specifies an exact, required version of the module.</span></span>
  - <span data-ttu-id="c0c75-298">`MaximumVersion` -Anger den högsta godkända versionen av modulen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-298">`MaximumVersion` - Specifies the maximum acceptable version of the module.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.ModuleSpecification[]
Parameter Sets: FullyQualifiedName, FullyQualifiedNameAndPSSession
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="c0c75-299">– Funktion</span><span class="sxs-lookup"><span data-stu-id="c0c75-299">-Function</span></span>

<span data-ttu-id="c0c75-300">Anger en matris med funktioner som denna cmdlet importerar från modulen till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-300">Specifies an array of functions that this cmdlet imports from the module into the current session.</span></span>
<span data-ttu-id="c0c75-301">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="c0c75-301">Wildcard characters are permitted.</span></span> <span data-ttu-id="c0c75-302">Vissa moduler exporterar automatiskt markerade funktioner till sessionen när du importerar modulen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-302">Some modules automatically export selected functions into your session when you import the module.</span></span> <span data-ttu-id="c0c75-303">Med den här parametern kan du välja bland de exporterade funktionerna.</span><span class="sxs-lookup"><span data-stu-id="c0c75-303">This parameter lets you select from among the exported functions.</span></span>

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

### <span data-ttu-id="c0c75-304">– Global</span><span class="sxs-lookup"><span data-stu-id="c0c75-304">-Global</span></span>

<span data-ttu-id="c0c75-305">Anger att denna cmdlet importerar moduler till det globala sessionstillståndet så att de är tillgängliga för alla kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-305">Indicates that this cmdlet imports modules into the global session state so they are available to all commands in the session.</span></span>

<span data-ttu-id="c0c75-306">Som standard, när `Import-Module` cmdlet anropas från kommando tolken, skript filen eller script block, importeras alla kommandon till det globala sessionstillståndet.</span><span class="sxs-lookup"><span data-stu-id="c0c75-306">By default, when `Import-Module` cmdlet is called from the command prompt, script file, or scriptblock, all the commands are imported into the global session state.</span></span>

<span data-ttu-id="c0c75-307">Vid anrop från en annan modul `Import-Module` importerar cmdlet kommandon i en modul, inklusive kommandon från kapslade moduler, till den anropande modulens sessionstillstånd.</span><span class="sxs-lookup"><span data-stu-id="c0c75-307">When invoked from another module, `Import-Module` cmdlet imports the commands in a module, including commands from nested modules, into the calling module's session state.</span></span>

> [!TIP]
> <span data-ttu-id="c0c75-308">Undvik att anropa inifrån `Import-Module` en modul.</span><span class="sxs-lookup"><span data-stu-id="c0c75-308">You should avoid calling `Import-Module` from within a module.</span></span> <span data-ttu-id="c0c75-309">Deklarera i stället mål-modulen som en kapslad modul i den överordnade modulens manifest.</span><span class="sxs-lookup"><span data-stu-id="c0c75-309">Instead, declare the target module as a nested module in the parent module's manifest.</span></span> <span data-ttu-id="c0c75-310">Att deklarera kapslade moduler gör det enklare att identifiera beroenden.</span><span class="sxs-lookup"><span data-stu-id="c0c75-310">Declaring nested modules improves the discoverability of dependencies.</span></span>

<span data-ttu-id="c0c75-311">Den **globala** parametern motsvarar **omfattnings** parametern med värdet **Global**.</span><span class="sxs-lookup"><span data-stu-id="c0c75-311">The **Global** parameter is equivalent to the **Scope** parameter with a value of **Global**.</span></span>

<span data-ttu-id="c0c75-312">Om du vill begränsa vilka kommandon som en modul exporterar, använder du ett `Export-ModuleMember` kommando i modulen script.</span><span class="sxs-lookup"><span data-stu-id="c0c75-312">To restrict the commands that a module exports, use an `Export-ModuleMember` command in the script module.</span></span>

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

### <span data-ttu-id="c0c75-313">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="c0c75-313">-MaximumVersion</span></span>

<span data-ttu-id="c0c75-314">Anger en högsta version.</span><span class="sxs-lookup"><span data-stu-id="c0c75-314">Specifies a maximum version.</span></span> <span data-ttu-id="c0c75-315">Den här cmdleten importerar bara en version av modulen som är mindre än eller lika med det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="c0c75-315">This cmdlet imports only a version of the module that is less than or equal to the specified value.</span></span> <span data-ttu-id="c0c75-316">Om ingen version kvalificeras `Import-Module` returneras ett fel.</span><span class="sxs-lookup"><span data-stu-id="c0c75-316">If no version qualifies, `Import-Module` returns an error.</span></span>

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

### <span data-ttu-id="c0c75-317">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="c0c75-317">-MinimumVersion</span></span>

<span data-ttu-id="c0c75-318">Anger en lägsta version.</span><span class="sxs-lookup"><span data-stu-id="c0c75-318">Specifies a minimum version.</span></span> <span data-ttu-id="c0c75-319">Den här cmdleten importerar bara en version av modulen som är större än eller lika med det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="c0c75-319">This cmdlet imports only a version of the module that is greater than or equal to the specified value.</span></span> <span data-ttu-id="c0c75-320">Använd **MinimumVersion** parameter namn eller dess alias, **version**.</span><span class="sxs-lookup"><span data-stu-id="c0c75-320">Use the **MinimumVersion** parameter name or its alias, **Version**.</span></span> <span data-ttu-id="c0c75-321">Om ingen version kvalificeras `Import-Module` genererar ett fel.</span><span class="sxs-lookup"><span data-stu-id="c0c75-321">If no version qualifies, `Import-Module` generates an error.</span></span>

<span data-ttu-id="c0c75-322">Om du vill ange en exakt version använder du parametern **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="c0c75-322">To specify an exact version, use the **RequiredVersion** parameter.</span></span> <span data-ttu-id="c0c75-323">Du kan också använda **modul** -och **versions** parametrar för **#Requires** nyckelordet för att kräva en speciell version av en modul i ett skript.</span><span class="sxs-lookup"><span data-stu-id="c0c75-323">You can also use the **Module** and **Version** parameters of the **#Requires** keyword to require a specific version of a module in a script.</span></span>

<span data-ttu-id="c0c75-324">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c0c75-324">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="c0c75-325">-ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="c0c75-325">-ModuleInfo</span></span>

<span data-ttu-id="c0c75-326">Anger en matris med modul-objekt som ska importeras.</span><span class="sxs-lookup"><span data-stu-id="c0c75-326">Specifies an array of module objects to import.</span></span> <span data-ttu-id="c0c75-327">Ange en variabel som innehåller modulens objekt, eller ett kommando som hämtar modulens objekt, till exempel följande kommando: `Get-Module -ListAvailable` .</span><span class="sxs-lookup"><span data-stu-id="c0c75-327">Enter a variable that contains the module objects, or a command that gets the module objects, such as the following command: `Get-Module -ListAvailable`.</span></span> <span data-ttu-id="c0c75-328">Du kan också skicka modul objekt till `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="c0c75-328">You can also pipe module objects to `Import-Module`.</span></span>

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

### <span data-ttu-id="c0c75-329">-Name</span><span class="sxs-lookup"><span data-stu-id="c0c75-329">-Name</span></span>

<span data-ttu-id="c0c75-330">Anger namnen på de moduler som ska importeras.</span><span class="sxs-lookup"><span data-stu-id="c0c75-330">Specifies the names of the modules to import.</span></span> <span data-ttu-id="c0c75-331">Ange namnet på modulen eller namnet på en fil i modulen, till exempel en,, eller en `.psd1` `.psm1` `.dll` `.ps1` fil.</span><span class="sxs-lookup"><span data-stu-id="c0c75-331">Enter the name of the module or the name of a file in the module, such as a `.psd1`, `.psm1`, `.dll`, or `.ps1` file.</span></span> <span data-ttu-id="c0c75-332">Fil Sök vägar är valfria.</span><span class="sxs-lookup"><span data-stu-id="c0c75-332">File paths are optional.</span></span> <span data-ttu-id="c0c75-333">Jokertecken är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="c0c75-333">Wildcard characters aren't permitted.</span></span> <span data-ttu-id="c0c75-334">Du kan också skicka namn och fil namn för moduler till `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="c0c75-334">You can also pipe module names and filenames to `Import-Module`.</span></span>

<span data-ttu-id="c0c75-335">Om du utelämnar en sökväg `Import-Module` söker du efter modulen i Sök vägarna som sparats i `$env:PSModulePath` miljö variabeln.</span><span class="sxs-lookup"><span data-stu-id="c0c75-335">If you omit a path, `Import-Module` looks for the module in the paths saved in the `$env:PSModulePath` environment variable.</span></span>

<span data-ttu-id="c0c75-336">Ange bara modulnamnet när det är möjligt.</span><span class="sxs-lookup"><span data-stu-id="c0c75-336">Specify only the module name whenever possible.</span></span> <span data-ttu-id="c0c75-337">När du anger ett fil namn importeras bara de medlemmar som implementeras i den filen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-337">When you specify a file name, only the members that are implemented in that file are imported.</span></span> <span data-ttu-id="c0c75-338">Om modulen innehåller andra filer importeras de inte, och du kanske saknar viktiga medlemmar i modulen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-338">If the module contains other files, they aren't imported, and you might be missing important members of the module.</span></span>

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

### <span data-ttu-id="c0c75-339">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="c0c75-339">-NoClobber</span></span>

<span data-ttu-id="c0c75-340">Förhindrar att du importerar kommandon som har samma namn som befintliga kommandon i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-340">Prevents importing commands that have the same names as existing commands in the current session.</span></span> <span data-ttu-id="c0c75-341">Som standard `Import-Module` importerar alla exporterade module-kommandon.</span><span class="sxs-lookup"><span data-stu-id="c0c75-341">By default, `Import-Module` imports all exported module commands.</span></span>

<span data-ttu-id="c0c75-342">Kommandon som har samma namn kan dölja eller ersätta kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-342">Commands that have the same names can hide or replace commands in the session.</span></span> <span data-ttu-id="c0c75-343">Använd **prefix** -eller **NoClobber** -parametrarna för att undvika kommando namns konflikter i en session.</span><span class="sxs-lookup"><span data-stu-id="c0c75-343">To avoid command name conflicts in a session, use the **Prefix** or **NoClobber** parameters.</span></span> <span data-ttu-id="c0c75-344">Mer information om namn konflikter och kommando prioritet finns i "moduler och namn konflikter" i [about_Modules](about/about_Modules.md) och [about_Command_Precedence](about/about_Command_Precedence.md).</span><span class="sxs-lookup"><span data-stu-id="c0c75-344">For more information about name conflicts and command precedence, see "Modules and Name Conflicts" in [about_Modules](about/about_Modules.md) and [about_Command_Precedence](about/about_Command_Precedence.md).</span></span>

<span data-ttu-id="c0c75-345">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c0c75-345">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="c0c75-346">– PassThru</span><span class="sxs-lookup"><span data-stu-id="c0c75-346">-PassThru</span></span>

<span data-ttu-id="c0c75-347">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="c0c75-347">Returns an object representing the item with which you're working.</span></span> <span data-ttu-id="c0c75-348">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="c0c75-348">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="c0c75-349">-Prefix</span><span class="sxs-lookup"><span data-stu-id="c0c75-349">-Prefix</span></span>

<span data-ttu-id="c0c75-350">Anger ett prefix som denna cmdlet lägger till i Substantiv i namnen på importerade modul medlemmar.</span><span class="sxs-lookup"><span data-stu-id="c0c75-350">Specifies a prefix that this cmdlet adds to the nouns in the names of imported module members.</span></span>

<span data-ttu-id="c0c75-351">Använd den här parametern för att undvika namn konflikter som kan uppstå när olika medlemmar i sessionen har samma namn.</span><span class="sxs-lookup"><span data-stu-id="c0c75-351">Use this parameter to avoid name conflicts that might occur when different members in the session have the same name.</span></span> <span data-ttu-id="c0c75-352">Den här parametern ändrar inte modulen och påverkar inte filer som modulen importerar för eget bruk.</span><span class="sxs-lookup"><span data-stu-id="c0c75-352">This parameter does not change the module, and it does not affect files that the module imports for its own use.</span></span> <span data-ttu-id="c0c75-353">Dessa kallas kapslade moduler.</span><span class="sxs-lookup"><span data-stu-id="c0c75-353">These are known as nested modules.</span></span> <span data-ttu-id="c0c75-354">Denna cmdlet påverkar bara namnen på medlemmar i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-354">This cmdlet affects only the names of members in the current session.</span></span>

<span data-ttu-id="c0c75-355">Om du till exempel anger prefixet UTC och sedan importerar en `Get-Date` cmdlet, är cmdleten känd i sessionen som `Get-UTCDate` och den förväxlas inte med den ursprungliga `Get-Date` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c0c75-355">For example, if you specify the prefix UTC and then import a `Get-Date` cmdlet, the cmdlet is known in the session as `Get-UTCDate`, and it is not confused with the original `Get-Date` cmdlet.</span></span>

<span data-ttu-id="c0c75-356">Värdet för den här parametern prioriteras över **DefaultCommandPrefix** -egenskapen för modulen, som anger standardprefixet.</span><span class="sxs-lookup"><span data-stu-id="c0c75-356">The value of this parameter takes precedence over the **DefaultCommandPrefix** property of the module, which specifies the default prefix.</span></span>

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

### <span data-ttu-id="c0c75-357">– PSSession</span><span class="sxs-lookup"><span data-stu-id="c0c75-357">-PSSession</span></span>

<span data-ttu-id="c0c75-358">Anger en PowerShell- **PSSession** (User-Managed session) från vilken denna cmdlet importerar moduler till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-358">Specifies a PowerShell user-managed session ( **PSSession** ) from which this cmdlet imports modules into the current session.</span></span> <span data-ttu-id="c0c75-359">Ange en variabel som innehåller ett **PSSession** eller ett kommando som hämtar en **PSSession** , till exempel ett `Get-PSSession` kommando.</span><span class="sxs-lookup"><span data-stu-id="c0c75-359">Enter a variable that contains a **PSSession** or a command that gets a **PSSession** , such as a `Get-PSSession` command.</span></span>

<span data-ttu-id="c0c75-360">När du importerar en modul från en annan session till den aktuella sessionen kan du använda cmdletar från modulen i den aktuella sessionen, precis som du skulle använda cmdlets från en lokal modul.</span><span class="sxs-lookup"><span data-stu-id="c0c75-360">When you import a module from a different session into the current session, you can use the cmdlets from the module in the current session, just as you would use cmdlets from a local module.</span></span> <span data-ttu-id="c0c75-361">Kommandon som använder fjärrcmdlets körs i fjärrsessionen, men fjärrinformationen hanteras i bakgrunden av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c0c75-361">Commands that use the remote cmdlets run in the remote session, but the remoting details are managed in the background by PowerShell.</span></span>

<span data-ttu-id="c0c75-362">Den här parametern använder funktionen implicit fjärr kommunikation i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c0c75-362">This parameter uses the Implicit Remoting feature of PowerShell.</span></span> <span data-ttu-id="c0c75-363">Det motsvarar att använda `Import-PSSession` cmdleten för att importera specifika moduler från en session.</span><span class="sxs-lookup"><span data-stu-id="c0c75-363">It is equivalent to using the `Import-PSSession` cmdlet to import particular modules from a session.</span></span>

<span data-ttu-id="c0c75-364">`Import-Module` Det går inte att importera PowerShell Core-moduler från en annan session.</span><span class="sxs-lookup"><span data-stu-id="c0c75-364">`Import-Module` cannot import PowerShell Core modules from another session.</span></span> <span data-ttu-id="c0c75-365">PowerShell Core-modulerna har namn som inleds med Microsoft. PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c0c75-365">The PowerShell Core modules have names that begin with Microsoft.PowerShell.</span></span>

<span data-ttu-id="c0c75-366">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c0c75-366">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="c0c75-367">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="c0c75-367">-RequiredVersion</span></span>

<span data-ttu-id="c0c75-368">Anger en version av modulen som denna cmdlet importerar.</span><span class="sxs-lookup"><span data-stu-id="c0c75-368">Specifies a version of the module that this cmdlet imports.</span></span> <span data-ttu-id="c0c75-369">Om versionen inte är installerad `Import-Module` genererar ett fel.</span><span class="sxs-lookup"><span data-stu-id="c0c75-369">If the version is not installed, `Import-Module` generates an error.</span></span>

<span data-ttu-id="c0c75-370">Som standard `Import-Module` importerar modulen utan att kontrol lera versions numret.</span><span class="sxs-lookup"><span data-stu-id="c0c75-370">By default, `Import-Module` imports the module without checking the version number.</span></span>

<span data-ttu-id="c0c75-371">Om du vill ange en lägsta version använder du parametern **MinimumVersion** .</span><span class="sxs-lookup"><span data-stu-id="c0c75-371">To specify a minimum version, use the **MinimumVersion** parameter.</span></span> <span data-ttu-id="c0c75-372">Du kan också använda **modul** -och **versions** parametrar för **#Requires** nyckelordet för att kräva en speciell version av en modul i ett skript.</span><span class="sxs-lookup"><span data-stu-id="c0c75-372">You can also use the **Module** and **Version** parameters of the **#Requires** keyword to require a specific version of a module in a script.</span></span>

<span data-ttu-id="c0c75-373">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c0c75-373">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="c0c75-374">Skript som använder **RequiredVersion** för att importera moduler som ingår i befintliga versioner av Windows operativ system körs inte automatiskt i framtida versioner av Windows operativ system.</span><span class="sxs-lookup"><span data-stu-id="c0c75-374">Scripts that use **RequiredVersion** to import modules that are included with existing releases of the Windows operating system don't automatically run in future releases of the Windows operating system.</span></span> <span data-ttu-id="c0c75-375">Detta beror på att PowerShell-modulens versions nummer i framtida versioner av Windows operativ system är högre än versions nummer för modul i befintliga versioner av Windows operativ system.</span><span class="sxs-lookup"><span data-stu-id="c0c75-375">This is because PowerShell module version numbers in future releases of the Windows operating system are higher than module version numbers in existing releases of the Windows operating system.</span></span>

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

### <span data-ttu-id="c0c75-376">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="c0c75-376">-Scope</span></span>

<span data-ttu-id="c0c75-377">Anger ett omfång där denna cmdlet importerar modulen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-377">Specifies a scope into which this cmdlet imports the module.</span></span>

<span data-ttu-id="c0c75-378">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="c0c75-378">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="c0c75-379">**Global**.</span><span class="sxs-lookup"><span data-stu-id="c0c75-379">**Global**.</span></span> <span data-ttu-id="c0c75-380">Tillgängligt för alla kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-380">Available to all commands in the session.</span></span> <span data-ttu-id="c0c75-381">Motsvarar den **globala** parametern.</span><span class="sxs-lookup"><span data-stu-id="c0c75-381">Equivalent to the **Global** parameter.</span></span>
- <span data-ttu-id="c0c75-382">**Lokal**.</span><span class="sxs-lookup"><span data-stu-id="c0c75-382">**Local**.</span></span> <span data-ttu-id="c0c75-383">Endast tillgängligt i det aktuella omfånget.</span><span class="sxs-lookup"><span data-stu-id="c0c75-383">Available only in the current scope.</span></span>

<span data-ttu-id="c0c75-384">Som standard, när `Import-Module` cmdlet anropas från kommando tolken, skript filen eller script block, importeras alla kommandon till det globala sessionstillståndet.</span><span class="sxs-lookup"><span data-stu-id="c0c75-384">By default, when `Import-Module` cmdlet is called from the command prompt, script file, or scriptblock, all the commands are imported into the global session state.</span></span> <span data-ttu-id="c0c75-385">Du kan använda parametern **-scope** med värdet **lokalt** för att importera modulens innehåll till skriptet eller script block-omfånget.</span><span class="sxs-lookup"><span data-stu-id="c0c75-385">You can use the **-Scope** parameter with the value of **Local** to import module content into the script or scriptblock scope.</span></span>

<span data-ttu-id="c0c75-386">Vid anrop från en annan modul `Import-Module` importerar cmdlet kommandon i en modul, inklusive kommandon från kapslade moduler, till anroparens sessionstillstånd.</span><span class="sxs-lookup"><span data-stu-id="c0c75-386">When invoked from another module, `Import-Module` cmdlet imports the commands in a module, including commands from nested modules, into the caller's session state.</span></span> <span data-ttu-id="c0c75-387">Ange `-Scope Global` eller `-Global` anger att denna cmdlet importerar moduler till det globala sessionstillståndet så att de är tillgängliga för alla kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-387">Specifying `-Scope Global` or `-Global` indicates that this cmdlet imports modules into the global session state so they are available to all commands in the session.</span></span>

<span data-ttu-id="c0c75-388">Den **globala** parametern motsvarar **omfattnings** parametern med värdet global.</span><span class="sxs-lookup"><span data-stu-id="c0c75-388">The **Global** parameter is equivalent to the **Scope** parameter with a value of Global.</span></span>

<span data-ttu-id="c0c75-389">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="c0c75-389">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="c0c75-390">– Variabel</span><span class="sxs-lookup"><span data-stu-id="c0c75-390">-Variable</span></span>

<span data-ttu-id="c0c75-391">Anger en matris med variabler som denna cmdlet importerar från modulen till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-391">Specifies an array of variables that this cmdlet imports from the module into the current session.</span></span>
<span data-ttu-id="c0c75-392">Ange en lista med variabler.</span><span class="sxs-lookup"><span data-stu-id="c0c75-392">Enter a list of variables.</span></span> <span data-ttu-id="c0c75-393">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="c0c75-393">Wildcard characters are permitted.</span></span>

<span data-ttu-id="c0c75-394">Vissa moduler exporterar automatiskt markerade variabler till sessionen när du importerar modulen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-394">Some modules automatically export selected variables into your session when you import the module.</span></span>
<span data-ttu-id="c0c75-395">Med den här parametern kan du välja bland de exporterade variablerna.</span><span class="sxs-lookup"><span data-stu-id="c0c75-395">This parameter lets you select from among the exported variables.</span></span>

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

### <span data-ttu-id="c0c75-396">-SkipEditionCheck</span><span class="sxs-lookup"><span data-stu-id="c0c75-396">-SkipEditionCheck</span></span>

<span data-ttu-id="c0c75-397">Hoppar över kontrollen i `CompatiblePSEditions` fältet.</span><span class="sxs-lookup"><span data-stu-id="c0c75-397">Skips the check on the `CompatiblePSEditions` field.</span></span>

<span data-ttu-id="c0c75-398">Tillåter inläsning av en modul från `"$($env:windir)\System32\WindowsPowerShell\v1.0\Modules"` modul-katalogen till PowerShell Core när modulen inte anges `Core` i `CompatiblePSEditions` manifest fältet.</span><span class="sxs-lookup"><span data-stu-id="c0c75-398">Allows loading a module from the `"$($env:windir)\System32\WindowsPowerShell\v1.0\Modules"` module directory into PowerShell Core when that module does not specify `Core` in the `CompatiblePSEditions` manifest field.</span></span>

<span data-ttu-id="c0c75-399">När du importerar en modul från en annan sökväg gör den här växeln ingenting, eftersom kontrollen inte utförs.</span><span class="sxs-lookup"><span data-stu-id="c0c75-399">When importing a module from another path, this switch does nothing, since the check is not performed.</span></span> <span data-ttu-id="c0c75-400">På Linux och macOS gör den här växeln ingenting.</span><span class="sxs-lookup"><span data-stu-id="c0c75-400">On Linux and macOS, this switch does nothing.</span></span>

<span data-ttu-id="c0c75-401">Mer information finns i [about_PowerShell_Editions](About/about_PowerShell_Editions.md).</span><span class="sxs-lookup"><span data-stu-id="c0c75-401">For more information, see [about_PowerShell_Editions](About/about_PowerShell_Editions.md).</span></span>

> [!WARNING]
> <span data-ttu-id="c0c75-402">`Import-Module -SkipEditionCheck` är fortfarande troligt att det inte går att importera en modul.</span><span class="sxs-lookup"><span data-stu-id="c0c75-402">`Import-Module -SkipEditionCheck` is still likely to fail to import a module.</span></span> <span data-ttu-id="c0c75-403">Även om det lyckas kan det hända att anrop av ett kommando från modulen senare Miss lyckas vid försök att använda ett inkompatibelt API.</span><span class="sxs-lookup"><span data-stu-id="c0c75-403">Even if it does succeed, invoking a command from the module may later fail when it tries to use an incompatible API.</span></span>

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

### <span data-ttu-id="c0c75-404">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c0c75-404">CommonParameters</span></span>

<span data-ttu-id="c0c75-405">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c0c75-405">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c0c75-406">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c0c75-406">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c0c75-407">INDATA</span><span class="sxs-lookup"><span data-stu-id="c0c75-407">INPUTS</span></span>

### <span data-ttu-id="c0c75-408">System. String, system. Management. Automation. PSModuleInfo, system. Reflection. Assembly</span><span class="sxs-lookup"><span data-stu-id="c0c75-408">System.String, System.Management.Automation.PSModuleInfo, System.Reflection.Assembly</span></span>

<span data-ttu-id="c0c75-409">Du kan skicka vidare ett modulnamn, module-objekt eller Assembly-objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c0c75-409">You can pipe a module name, module object, or assembly object to this cmdlet.</span></span>

## <span data-ttu-id="c0c75-410">UTDATA</span><span class="sxs-lookup"><span data-stu-id="c0c75-410">OUTPUTS</span></span>

### <span data-ttu-id="c0c75-411">Ingen, system. Management. Automation. PSModuleInfo eller system. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="c0c75-411">None, System.Management.Automation.PSModuleInfo, or System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="c0c75-412">`Import-Module`Genererar inga utdata som standard.</span><span class="sxs-lookup"><span data-stu-id="c0c75-412">By default, `Import-Module` does not generate any output.</span></span> <span data-ttu-id="c0c75-413">Om du anger parametern **Passthru** genererar cmdleten ett **system. Management. Automation. PSModuleInfo** -objekt som representerar modulen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-413">If you specify the **PassThru** parameter, the cmdlet generates a **System.Management.Automation.PSModuleInfo** object that represents the module.</span></span> <span data-ttu-id="c0c75-414">Om du anger parametern **AsCustomObject** genereras ett **PSCustomObject** -objekt.</span><span class="sxs-lookup"><span data-stu-id="c0c75-414">If you specify the **AsCustomObject** parameter, it generates a **PSCustomObject** object.</span></span>

## <span data-ttu-id="c0c75-415">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="c0c75-415">NOTES</span></span>

- <span data-ttu-id="c0c75-416">Innan du kan importera en modul måste modulen vara installerad på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="c0c75-416">Before you can import a module, the module must be installed on the local computer.</span></span> <span data-ttu-id="c0c75-417">Därför måste modul katalogen kopieras till en katalog som är tillgänglig för den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="c0c75-417">That is, the module directory must be copied to a directory that is accessible to your local computer.</span></span> <span data-ttu-id="c0c75-418">Mer information finns i [about_Modules](About/about_Modules.md).</span><span class="sxs-lookup"><span data-stu-id="c0c75-418">For more information, see [about_Modules](About/about_Modules.md).</span></span>

  <span data-ttu-id="c0c75-419">Du kan också använda parametrarna **PSSession** och **CIMSession** för att importera moduler som är installerade på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="c0c75-419">You can also use the **PSSession** and **CIMSession** parameters to import modules that are installed on remote computers.</span></span> <span data-ttu-id="c0c75-420">Kommandon som använder cmdletarna i dessa moduler körs dock i fjärrsessionen på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="c0c75-420">However, commands that use the cmdlets in these modules run in the remote session on the remote computer.</span></span>

- <span data-ttu-id="c0c75-421">Om du importerar medlemmar med samma namn och samma typ i din session, använder PowerShell medlemmen som importer ATS sist som standard.</span><span class="sxs-lookup"><span data-stu-id="c0c75-421">If you import members with the same name and the same type into your session, PowerShell uses the member imported last by default.</span></span> <span data-ttu-id="c0c75-422">Variabler och alias ersätts och originalen är inte tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="c0c75-422">Variables and aliases are replaced, and the originals aren't accessible.</span></span> <span data-ttu-id="c0c75-423">Funktioner, cmdletar och providrar är bara skuggade av de nya medlemmarna.</span><span class="sxs-lookup"><span data-stu-id="c0c75-423">Functions, cmdlets, and providers are merely shadowed by the new members.</span></span> <span data-ttu-id="c0c75-424">De kan nås genom att kvalificera kommando namnet med namnet på dess snapin-modul, modul eller funktions Sök väg.</span><span class="sxs-lookup"><span data-stu-id="c0c75-424">They can be accessed by qualifying the command name with the name of its snap-in, module, or function path.</span></span>

- <span data-ttu-id="c0c75-425">Använd cmdleten för att uppdatera formaterings data för kommandon som har importer ATS från en modul `Update-FormatData` .</span><span class="sxs-lookup"><span data-stu-id="c0c75-425">To update the formatting data for commands that have been imported from a module, use the `Update-FormatData` cmdlet.</span></span> <span data-ttu-id="c0c75-426">`Update-FormatData` uppdaterar också formaterings data för kommandon i sessionen som har importer ATS från moduler.</span><span class="sxs-lookup"><span data-stu-id="c0c75-426">`Update-FormatData` also updates the formatting data for commands in the session that were imported from modules.</span></span> <span data-ttu-id="c0c75-427">Om format filen för en modul ändras kan du köra ett `Update-FormatData` kommando för att uppdatera formateringen för importerade kommandon.</span><span class="sxs-lookup"><span data-stu-id="c0c75-427">If the formatting file for a module changes, you can run an `Update-FormatData` command to update the formatting data for imported commands.</span></span> <span data-ttu-id="c0c75-428">Du behöver inte importera modulen igen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-428">You don't need to import the module again.</span></span>

- <span data-ttu-id="c0c75-429">Från och med Windows PowerShell 3,0 paketeras de grundläggande kommandon som installeras med PowerShell i moduler.</span><span class="sxs-lookup"><span data-stu-id="c0c75-429">Starting in Windows PowerShell 3.0, the core commands that are installed with PowerShell are packaged in modules.</span></span> <span data-ttu-id="c0c75-430">I Windows PowerShell 2,0 och i värd program som skapar äldre sessioner i senare versioner av PowerShell, paketeras huvud kommandona i snapin-moduler ( **PSSnapins** ).</span><span class="sxs-lookup"><span data-stu-id="c0c75-430">In Windows PowerShell 2.0, and in host programs that create older-style sessions in later versions of PowerShell, the core commands are packaged in snap-ins ( **PSSnapins** ).</span></span> <span data-ttu-id="c0c75-431">Undantaget är **Microsoft. PowerShell. Core** , som alltid är en snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="c0c75-431">The exception is **Microsoft.PowerShell.Core** , which is always a snap-in.</span></span> <span data-ttu-id="c0c75-432">Fjärrsessioner, till exempel de som startas av `New-PSSession` cmdleten, är äldre sessioner som inkluderar grundläggande snapin-moduler.</span><span class="sxs-lookup"><span data-stu-id="c0c75-432">Also, remote sessions, such as those started by the `New-PSSession` cmdlet, are older-style sessions that include core snap-ins.</span></span>

  <span data-ttu-id="c0c75-433">Information om **CreateDefault2** -metoden som skapar nyare sessioner med Core-moduler finns i [CreateDefault2-metoden](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2).</span><span class="sxs-lookup"><span data-stu-id="c0c75-433">For information about the **CreateDefault2** method that creates newer-style sessions with core modules, see the [CreateDefault2 Method](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2).</span></span>

- <span data-ttu-id="c0c75-434">`Import-Module` Det går inte att importera PowerShell Core-moduler från en annan session.</span><span class="sxs-lookup"><span data-stu-id="c0c75-434">`Import-Module` cannot import PowerShell Core modules from another session.</span></span> <span data-ttu-id="c0c75-435">PowerShell Core-modulerna har namn som börjar med `Microsoft.PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="c0c75-435">The PowerShell Core modules have names that begin with `Microsoft.PowerShell`.</span></span>

- <span data-ttu-id="c0c75-436">I Windows PowerShell 2,0 fylldes några av egenskapsvärdena för objektet modul, till exempel egenskapsvärdena **ExportedCmdlets** och **NestedModules** , inte förrän modulen importerades och var inte tillgänglig på det modul-objekt som parametern **Passthru** returnerar.</span><span class="sxs-lookup"><span data-stu-id="c0c75-436">In Windows PowerShell 2.0, some of the property values of the module object, such as the **ExportedCmdlets** and **NestedModules** property values, were not populated until the module was imported and were not available on the module object that the **PassThru** parameter returns.</span></span> <span data-ttu-id="c0c75-437">I Windows PowerShell 3,0 fylls alla egenskaps värden i modulen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-437">In Windows PowerShell 3.0, all module property values are populated.</span></span>

- <span data-ttu-id="c0c75-438">Om du försöker importera en modul som innehåller sammansättningar med blandat läge som inte är kompatibla med Windows PowerShell 3,0 `Import-Module` returnerar ett fel meddelande som liknar följande.</span><span class="sxs-lookup"><span data-stu-id="c0c75-438">If you attempt to import a module that contains mixed-mode assemblies that aren't compatible with Windows PowerShell 3.0, `Import-Module` returns an error message like the following one.</span></span>

  > <span data-ttu-id="c0c75-439">Import-Module: blandad läges sammansättning har skapats mot version "v 2.0.50727" av körningen och kan inte läsas in i 4,0-körningsmiljön utan ytterligare konfigurations information.</span><span class="sxs-lookup"><span data-stu-id="c0c75-439">Import-Module : Mixed mode assembly is built against version 'v2.0.50727' of the runtime and cannot be loaded in the 4.0 runtime without additional configuration information.</span></span>

  <span data-ttu-id="c0c75-440">Det här felet uppstår när en modul som är avsedd för Windows PowerShell 2,0 innehåller minst en sammansättning med blandade moduler, det vill säga en sammansättning som innehåller både hanterad och icke-hanterad kod, till exempel C++ och C#.</span><span class="sxs-lookup"><span data-stu-id="c0c75-440">This error occurs when a module that is designed for Windows PowerShell 2.0 contains at least one mixed-module assembly, that is, an assembly that includes both managed and non-managed code, such as C++ and C#.</span></span>

  <span data-ttu-id="c0c75-441">Om du vill importera en modul som innehåller sammansättningar med blandat läge startar du Windows PowerShell 2,0 med hjälp av följande kommando och försöker sedan `Import-Module` igen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-441">To import a module that contains mixed-mode assemblies, start Windows PowerShell 2.0 by using the following command, and then try the `Import-Module` command again.</span></span>

  `PowerShell.exe -Version 2.0`

- <span data-ttu-id="c0c75-442">Om du vill använda funktionen CIM-sessionen måste fjärrdatorn ha WS-Management fjärr anslutning och Windows Management Instrumentation (WMI), som är Microsofts implementering av Common Information Model (CIM) standard.</span><span class="sxs-lookup"><span data-stu-id="c0c75-442">To use the CIM session feature, the remote computer must have WS-Management remoting and Windows Management Instrumentation (WMI), which is the Microsoft implementation of the Common Information Model (CIM) standard.</span></span> <span data-ttu-id="c0c75-443">Datorn måste också ha WMI-providern för modul identifiering eller en alternativ CIM-provider som har samma grundläggande funktioner.</span><span class="sxs-lookup"><span data-stu-id="c0c75-443">The computer must also have the Module Discovery WMI provider or an alternate CIM provider that has the same basic features.</span></span>

  <span data-ttu-id="c0c75-444">Du kan använda funktionen för CIM-sessionen på datorer som inte kör ett Windows-operativsystem och på Windows-datorer som har PowerShell, men inte har PowerShell-fjärrkommunikation aktive rad.</span><span class="sxs-lookup"><span data-stu-id="c0c75-444">You can use the CIM session feature on computers that aren't running a Windows operating system and on Windows computers that have PowerShell, but don't have PowerShell remoting enabled.</span></span>

  <span data-ttu-id="c0c75-445">Du kan också använda CIM-parametrarna för att hämta CIM-moduler från datorer där PowerShell-fjärrkommunikation är aktiverat, inklusive den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="c0c75-445">You can also use the CIM parameters to get CIM modules from computers that have PowerShell remoting enabled, including the local computer.</span></span> <span data-ttu-id="c0c75-446">När du skapar en CIM-session på den lokala datorn använder PowerShell DCOM, i stället för WMI, för att skapa sessionen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-446">When you create a CIM session on the local computer, PowerShell uses DCOM, instead of WMI, to create the session.</span></span>

- <span data-ttu-id="c0c75-447">Som standard `Import-Module` importerar moduler i det globala omfånget även när de anropas från ett underordnat omfång.</span><span class="sxs-lookup"><span data-stu-id="c0c75-447">By default, `Import-Module` imports modules in the global scope even when called from a descendant scope.</span></span> <span data-ttu-id="c0c75-448">Omfattningen på den översta nivån och alla underordnade omfattningar har åtkomst till modulens exporterade element.</span><span class="sxs-lookup"><span data-stu-id="c0c75-448">The top-level scope and all descendant scopes have access to the module's exported elements.</span></span>

  <span data-ttu-id="c0c75-449">I ett underordnat omfång `-Scope Local` begränsar importen till det omfånget och alla dess underordnade omfång.</span><span class="sxs-lookup"><span data-stu-id="c0c75-449">In a descendant scope, `-Scope Local` limits the import to that scope and all its descendant scopes.</span></span> <span data-ttu-id="c0c75-450">Överordnade omfattningar ser inte de importerade medlemmarna.</span><span class="sxs-lookup"><span data-stu-id="c0c75-450">Parent scopes then do not see the imported members.</span></span>

  > [!NOTE]
  > <span data-ttu-id="c0c75-451">`Get-Module` visar alla moduler som lästs in i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="c0c75-451">`Get-Module` shows all modules loaded in the current session.</span></span> <span data-ttu-id="c0c75-452">Detta inkluderar moduler som lästs in lokalt i ett underordnat omfång.</span><span class="sxs-lookup"><span data-stu-id="c0c75-452">This includes modules loaded locally in a descendant scope.</span></span> <span data-ttu-id="c0c75-453">Använd `Get-Command -Module modulename` för att se vilka medlemmar som läses in i det aktuella omfånget.</span><span class="sxs-lookup"><span data-stu-id="c0c75-453">Use `Get-Command -Module modulename` to see which members are loaded in the current scope.</span></span>

  <span data-ttu-id="c0c75-454">Om modulen innehåller klass-och uppräknings definitioner, använder du `using module` i början av skriptet.</span><span class="sxs-lookup"><span data-stu-id="c0c75-454">If the module includes class and enum definitions, use `using module` at the beginning of your script.</span></span> <span data-ttu-id="c0c75-455">Detta importerar skripten, inklusive klass-och uppräknings definitioner.</span><span class="sxs-lookup"><span data-stu-id="c0c75-455">This import the scripts, including the class and enum definitions.</span></span> <span data-ttu-id="c0c75-456">Mer information finns i [about_Using](About/about_Using.md).</span><span class="sxs-lookup"><span data-stu-id="c0c75-456">For more information, see [about_Using](About/about_Using.md).</span></span>

## <span data-ttu-id="c0c75-457">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="c0c75-457">RELATED LINKS</span></span>

[<span data-ttu-id="c0c75-458">Exportera – ModuleMember</span><span class="sxs-lookup"><span data-stu-id="c0c75-458">Export-ModuleMember</span></span>](Export-ModuleMember.md)

[<span data-ttu-id="c0c75-459">Hämta modul</span><span class="sxs-lookup"><span data-stu-id="c0c75-459">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="c0c75-460">Ny modul</span><span class="sxs-lookup"><span data-stu-id="c0c75-460">New-Module</span></span>](New-Module.md)

[<span data-ttu-id="c0c75-461">Ta bort modul</span><span class="sxs-lookup"><span data-stu-id="c0c75-461">Remove-Module</span></span>](Remove-Module.md)

[<span data-ttu-id="c0c75-462">about_PowerShell_Editions</span><span class="sxs-lookup"><span data-stu-id="c0c75-462">about_PowerShell_Editions</span></span>](About/about_PowerShell_Editions.md)
