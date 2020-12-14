---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/import-module?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Module
ms.openlocfilehash: 6b87074f6053189b20b5cc0983f978324420c99b
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564398"
---
# <span data-ttu-id="77e9a-102">Import-Module</span><span class="sxs-lookup"><span data-stu-id="77e9a-102">Import-Module</span></span>

## <span data-ttu-id="77e9a-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="77e9a-103">SYNOPSIS</span></span>
<span data-ttu-id="77e9a-104">Lägger till moduler i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-104">Adds modules to the current session.</span></span>

## <span data-ttu-id="77e9a-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="77e9a-105">SYNTAX</span></span>

### <span data-ttu-id="77e9a-106">Namn (standard)</span><span class="sxs-lookup"><span data-stu-id="77e9a-106">Name (Default)</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-PassThru]
 [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] [<CommonParameters>]
```

### <span data-ttu-id="77e9a-107">PSSession</span><span class="sxs-lookup"><span data-stu-id="77e9a-107">PSSession</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-PassThru]
 [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] -PSSession <PSSession> [<CommonParameters>]
```

### <span data-ttu-id="77e9a-108">CimSession</span><span class="sxs-lookup"><span data-stu-id="77e9a-108">CimSession</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Name] <String[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-PassThru]
 [-AsCustomObject] [-MinimumVersion <Version>] [-MaximumVersion <String>]
 [-RequiredVersion <Version>] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] -CimSession <CimSession> [-CimResourceUri <Uri>] [-CimNamespace <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="77e9a-109">FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="77e9a-109">FullyQualifiedName</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-FullyQualifiedName] <ModuleSpecification[]>
 [-Function <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force]
 [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] [<CommonParameters>]
```

### <span data-ttu-id="77e9a-110">FullyQualifiedNameAndPSSession</span><span class="sxs-lookup"><span data-stu-id="77e9a-110">FullyQualifiedNameAndPSSession</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-FullyQualifiedName] <ModuleSpecification[]>
 [-Function <String[]>] [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force]
 [-PassThru] [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] -PSSession <PSSession> [<CommonParameters>]
```

### <span data-ttu-id="77e9a-111">Sammansättning</span><span class="sxs-lookup"><span data-stu-id="77e9a-111">Assembly</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Assembly] <Assembly[]> [-Function <String[]>]
 [-Cmdlet <String[]>] [-Variable <String[]>] [-Alias <String[]>] [-Force] [-PassThru]
 [-AsCustomObject] [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber] [-Scope <String>]
 [<CommonParameters>]
```

### <span data-ttu-id="77e9a-112">ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="77e9a-112">ModuleInfo</span></span>

```
Import-Module [-Global] [-Prefix <String>] [-Function <String[]>] [-Cmdlet <String[]>]
 [-Variable <String[]>] [-Alias <String[]>] [-Force] [-PassThru] [-AsCustomObject]
 [-ModuleInfo] <PSModuleInfo[]> [-ArgumentList <Object[]>] [-DisableNameChecking] [-NoClobber]
 [-Scope <String>] [<CommonParameters>]
```

## <span data-ttu-id="77e9a-113">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="77e9a-113">DESCRIPTION</span></span>

<span data-ttu-id="77e9a-114">`Import-Module`Cmdleten lägger till en eller flera moduler i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-114">The `Import-Module` cmdlet adds one or more modules to the current session.</span></span> <span data-ttu-id="77e9a-115">Från och med PowerShell 3,0 importeras installerade moduler automatiskt till sessionen när du använder kommandon eller providrar i modulen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-115">Starting in PowerShell 3.0, installed modules are automatically imported to the session when you use any commands or providers in the module.</span></span> <span data-ttu-id="77e9a-116">Du kan dock fortfarande använda `Import-Module` kommandot för att importera en modul.</span><span class="sxs-lookup"><span data-stu-id="77e9a-116">However, you can still use the `Import-Module` command to import a module.</span></span>
<span data-ttu-id="77e9a-117">Du kan inaktivera automatisk modul import med hjälp av `$PSModuleAutoloadingPreference` Preference-variabeln.</span><span class="sxs-lookup"><span data-stu-id="77e9a-117">You can disable automatic module importing using the `$PSModuleAutoloadingPreference` preference variable.</span></span> <span data-ttu-id="77e9a-118">Mer information om `$PSModuleAutoloadingPreference` variabeln finns i [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="77e9a-118">For more information about the `$PSModuleAutoloadingPreference` variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="77e9a-119">En modul är ett paket som innehåller medlemmar som kan användas i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="77e9a-119">A module is a package that contains members that can be used in PowerShell.</span></span> <span data-ttu-id="77e9a-120">Medlemmar inkluderar cmdlets, providrar, skript, funktioner, variabler och andra verktyg och filer.</span><span class="sxs-lookup"><span data-stu-id="77e9a-120">Members include cmdlets, providers, scripts, functions, variables, and other tools and files.</span></span> <span data-ttu-id="77e9a-121">När en modul har importer ATS kan du använda-modulens medlemmar i sessionen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-121">After a module is imported, you can use the module members in your session.</span></span> <span data-ttu-id="77e9a-122">Mer information om moduler finns i [about_Modules](About/about_Modules.md).</span><span class="sxs-lookup"><span data-stu-id="77e9a-122">For more information about modules, see [about_Modules](About/about_Modules.md).</span></span>

<span data-ttu-id="77e9a-123">Som standard `Import-Module` importerar alla medlemmar som modulen exporterar, men du kan använda **alias**, **funktion**, **cmdlet** och **variabel** parametrar för att begränsa vilka medlemmar som importeras.</span><span class="sxs-lookup"><span data-stu-id="77e9a-123">By default, `Import-Module` imports all members that the module exports, but you can use the **Alias**, **Function**, **Cmdlet**, and **Variable** parameters to restrict which members are imported.</span></span> <span data-ttu-id="77e9a-124">Parametern **NoClobber** förhindrar `Import-Module` import av medlemmar som har samma namn som medlemmar i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-124">The **NoClobber** parameter prevents `Import-Module` from importing members that have the same names as members in the current session.</span></span>

<span data-ttu-id="77e9a-125">`Import-Module` importerar en modul endast till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-125">`Import-Module` imports a module only into the current session.</span></span> <span data-ttu-id="77e9a-126">Om du vill importera modulen till varje ny session lägger du till ett `Import-Module` kommando i din PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="77e9a-126">To import the module into every new session, add an `Import-Module` command to your PowerShell profile.</span></span> <span data-ttu-id="77e9a-127">Mer information om profiler finns [about_Profiles](About/about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="77e9a-127">For more information about profiles, see [about_Profiles](About/about_Profiles.md).</span></span>

<span data-ttu-id="77e9a-128">Du kan hantera fjärranslutna Windows-datorer som har PowerShell-fjärrkommunikation aktive rad genom att skapa en **PSSession** på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="77e9a-128">You can manage remote Windows computers that have PowerShell remoting enabled by creating a **PSSession** on the remote computer.</span></span> <span data-ttu-id="77e9a-129">Använd sedan **PSSession** -parametern för `Import-Module` för att importera de moduler som är installerade på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="77e9a-129">Then use the **PSSession** parameter of `Import-Module` to import the modules that are installed on the remote computer.</span></span> <span data-ttu-id="77e9a-130">När du använder de importerade kommandona i den aktuella sessionen körs kommandona implicit på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="77e9a-130">When you use the imported commands in the current session the commands implicitly run on the remote computer.</span></span>

<span data-ttu-id="77e9a-131">Från och med Windows PowerShell 3,0 kan du använda `Import-Module` för att importera common information Model-moduler (CIM).</span><span class="sxs-lookup"><span data-stu-id="77e9a-131">Starting in Windows PowerShell 3.0, you can use `Import-Module` to import Common Information Model (CIM) modules.</span></span> <span data-ttu-id="77e9a-132">CIM-moduler definierar cmdletar i CDXLM-filer (cmdlet definition XML).</span><span class="sxs-lookup"><span data-stu-id="77e9a-132">CIM modules define cmdlets in Cmdlet Definition XML (CDXML) files.</span></span> <span data-ttu-id="77e9a-133">Med den här funktionen kan du använda cmdletar som implementeras i icke-hanterade kod sammansättningar, t. ex. sådana som skrivits i C++.</span><span class="sxs-lookup"><span data-stu-id="77e9a-133">This feature lets you use cmdlets that are implemented in non-managed code assemblies, such as those written in C++.</span></span>

<span data-ttu-id="77e9a-134">För fjärrdatorer som inte har PowerShell-fjärrkommunikation aktive rad, inklusive datorer som inte kör Windows operativ system, kan du använda **CIMSession** -parametern för `Import-Module` för att importera CIM-moduler från fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="77e9a-134">For remote computers that don't have PowerShell remoting enabled, including computers that aren't running the Windows operating system, you can use the **CIMSession** parameter of `Import-Module` to import CIM modules from the remote computer.</span></span> <span data-ttu-id="77e9a-135">De importerade kommandona körs implicit på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="77e9a-135">The imported commands run implicitly on the remote computer.</span></span> <span data-ttu-id="77e9a-136">En **CIMSession** är en anslutning till Windows Management INSTRUMENTATION (WMI) på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="77e9a-136">A **CIMSession** is a connection to Windows Management Instrumentation (WMI) on the remote computer.</span></span>

## <span data-ttu-id="77e9a-137">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="77e9a-137">EXAMPLES</span></span>

### <span data-ttu-id="77e9a-138">Exempel 1: importera medlemmarna i en modul till den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="77e9a-138">Example 1: Import the members of a module into the current session</span></span>

<span data-ttu-id="77e9a-139">I det här exemplet importeras medlemmarna i **PSDiagnostics** -modulen till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-139">This example imports the members of the **PSDiagnostics** module into the current session.</span></span>

```powershell
Import-Module -Name PSDiagnostics
```

### <span data-ttu-id="77e9a-140">Exempel 2: importera alla moduler som anges av sökvägen till modulen</span><span class="sxs-lookup"><span data-stu-id="77e9a-140">Example 2: Import all modules specified by the module path</span></span>

<span data-ttu-id="77e9a-141">I det här exemplet importeras alla tillgängliga moduler i sökvägen som anges av `$env:PSModulePath` miljö variabeln till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-141">This example imports all available modules in the path specified by the `$env:PSModulePath` environment variable into the current session.</span></span>

```powershell
Get-Module -ListAvailable | Import-Module
```

### <span data-ttu-id="77e9a-142">Exempel 3: Importera medlemmar i flera moduler till den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="77e9a-142">Example 3: Import the members of several modules into the current session</span></span>

<span data-ttu-id="77e9a-143">I det här exemplet importeras medlemmar av **PSDiagnostics** -och **DISM** -modulerna till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-143">This example imports the members of the **PSDiagnostics** and **Dism** modules into the current session.</span></span>

```powershell
$m = Get-Module -ListAvailable PSDiagnostics, Dism
Import-Module -ModuleInfo $m
```

<span data-ttu-id="77e9a-144">`Get-Module`Cmdlet: en hämtar modulen **PSDiagnostics** och **DISM** och sparar objekten i `$m` variabeln.</span><span class="sxs-lookup"><span data-stu-id="77e9a-144">The `Get-Module` cmdlet gets the **PSDiagnostics** and **Dism** modules and saves the objects in the `$m` variable.</span></span> <span data-ttu-id="77e9a-145">**ListAvailable** -parametern krävs när du hämtar moduler som ännu inte har importer ATS till sessionen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-145">The **ListAvailable** parameter is required when you're getting modules that aren't yet imported into the session.</span></span>

<span data-ttu-id="77e9a-146">Parametern **ModuleInfo** i `Import-Module` används för att importera modulerna till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-146">The **ModuleInfo** parameter of `Import-Module` is used to import the modules into the current session.</span></span>

### <span data-ttu-id="77e9a-147">Exempel 4: importera alla moduler som anges av en sökväg</span><span class="sxs-lookup"><span data-stu-id="77e9a-147">Example 4: Import all modules specified by a path</span></span>

<span data-ttu-id="77e9a-148">I det här exemplet används en explicit sökväg för att identifiera den modul som ska importeras.</span><span class="sxs-lookup"><span data-stu-id="77e9a-148">This example uses an explicit path to identify the module to import.</span></span>

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

<span data-ttu-id="77e9a-149">Med hjälp av parametern **verbose** `Import-Module` kan du rapportera förloppet när modulen läses in.</span><span class="sxs-lookup"><span data-stu-id="77e9a-149">Using the **Verbose** parameter causes `Import-Module` to report progress as it loads the module.</span></span>
<span data-ttu-id="77e9a-150">Utan **verbose**-, **Passthru**-eller **AsCustomObject** -parametern `Import-Module` genererar inga utdata när en modul importeras.</span><span class="sxs-lookup"><span data-stu-id="77e9a-150">Without the **Verbose**, **PassThru**, or **AsCustomObject** parameter, `Import-Module` does not generate any output when it imports a module.</span></span>

### <span data-ttu-id="77e9a-151">Exempel 5: begränsa modul medlemmar som importeras till en session</span><span class="sxs-lookup"><span data-stu-id="77e9a-151">Example 5: Restrict module members imported into a session</span></span>

<span data-ttu-id="77e9a-152">I det här exemplet visas hur du begränsar vilka modulblad som importeras till sessionen och kommandots effekter i sessionen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-152">This example shows how to restrict which module members are imported into the session and the effect of this command on the session.</span></span> <span data-ttu-id="77e9a-153">**Funktions** parametern begränsar de medlemmar som importeras från modulen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-153">The **Function** parameter limits the members that are imported from the module.</span></span> <span data-ttu-id="77e9a-154">Du kan också använda parametrarna **alias**, **variabel** och **cmdlet** för att begränsa andra medlemmar som en modul importerar.</span><span class="sxs-lookup"><span data-stu-id="77e9a-154">You can also use the **Alias**, **Variable**, and **Cmdlet** parameters to restrict other members that a module imports.</span></span>

<span data-ttu-id="77e9a-155">`Get-Module`Cmdlet: en hämtar det objekt som representerar **PSDiagnostics** -modulen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-155">The `Get-Module` cmdlet gets the object that represents the **PSDiagnostics** module.</span></span> <span data-ttu-id="77e9a-156">Egenskapen **ExportedCmdlets** visar alla cmdletar som modulen exporterar, även om de inte har importer ATS.</span><span class="sxs-lookup"><span data-stu-id="77e9a-156">The **ExportedCmdlets** property lists all the cmdlets that the module exports, even though they were not all imported.</span></span>

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

<span data-ttu-id="77e9a-157">Om du använder parametern **module** för `Get-Command` cmdleten visas de kommandon som har importer ATS från **PSDiagnostics** -modulen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-157">Using the **Module** parameter of the `Get-Command` cmdlet shows the commands that were imported from the **PSDiagnostics** module.</span></span> <span data-ttu-id="77e9a-158">Resultatet bekräftar att endast `Disable-PSTrace` `Enable-PSTrace` cmdletarna och har importer ATS.</span><span class="sxs-lookup"><span data-stu-id="77e9a-158">The results confirm that only the `Disable-PSTrace` and `Enable-PSTrace` cmdlets were imported.</span></span>

### <span data-ttu-id="77e9a-159">Exempel 6: importera medlemmarna i en modul och Lägg till ett prefix</span><span class="sxs-lookup"><span data-stu-id="77e9a-159">Example 6: Import the members of a module and add a prefix</span></span>

<span data-ttu-id="77e9a-160">Det här exemplet importerar **PSDiagnostics** -modulen till den aktuella sessionen, lägger till ett prefix till medlems namnen och visar sedan de förfasta medlems namnen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-160">This example imports the **PSDiagnostics** module into the current session, adds a prefix to the member names, and then displays the prefixed member names.</span></span> <span data-ttu-id="77e9a-161">Parametern **prefix** för `Import-Module` lägger till **x** -prefixet till alla medlemmar som importeras från modulen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-161">The **Prefix** parameter of `Import-Module` adds the **x** prefix to all members that are imported from the module.</span></span> <span data-ttu-id="77e9a-162">Prefixet gäller endast medlemmarna i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-162">The prefix applies only to the members in the current session.</span></span> <span data-ttu-id="77e9a-163">Modulen ändras inte.</span><span class="sxs-lookup"><span data-stu-id="77e9a-163">It does not change the module.</span></span> <span data-ttu-id="77e9a-164">Parametern **Passthru** returnerar ett modul-objekt som representerar den importerade modulen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-164">The **PassThru** parameter returns a module object that represents the imported module.</span></span>

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

<span data-ttu-id="77e9a-165">`Get-Command` hämtar de medlemmar som har importer ATS från modulen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-165">`Get-Command` gets the members that have been imported from the module.</span></span> <span data-ttu-id="77e9a-166">Utdata visar att modulens medlemmar är korrekt fasta.</span><span class="sxs-lookup"><span data-stu-id="77e9a-166">The output shows that the module members were correctly prefixed.</span></span>

### <span data-ttu-id="77e9a-167">Exempel 7: Hämta och använda ett anpassat objekt</span><span class="sxs-lookup"><span data-stu-id="77e9a-167">Example 7: Get and use a custom object</span></span>

<span data-ttu-id="77e9a-168">Det här exemplet visar hur du hämtar och använder det anpassade objektet som returnerades av `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="77e9a-168">This example demonstrates how to get and use the custom object returned by `Import-Module`.</span></span>

<span data-ttu-id="77e9a-169">Anpassade objekt innehåller syntetiska medlemmar som representerar var och en av de importerade modulerna medlemmar.</span><span class="sxs-lookup"><span data-stu-id="77e9a-169">Custom objects include synthetic members that represent each of the imported module members.</span></span> <span data-ttu-id="77e9a-170">Till exempel konverteras cmdletarna och funktionerna i en modul till skript metoder för det anpassade objektet.</span><span class="sxs-lookup"><span data-stu-id="77e9a-170">For example, the cmdlets and functions in a module are converted to script methods of the custom object.</span></span>

<span data-ttu-id="77e9a-171">Anpassade objekt är användbara i skript.</span><span class="sxs-lookup"><span data-stu-id="77e9a-171">Custom objects are useful in scripting.</span></span> <span data-ttu-id="77e9a-172">De är också användbara när flera importerade objekt har samma namn.</span><span class="sxs-lookup"><span data-stu-id="77e9a-172">They are also useful when several imported objects have the same names.</span></span> <span data-ttu-id="77e9a-173">Användning av skript metoden för ett objekt motsvarar att ange det fullständigt kvalificerade namnet på en importerad medlem, inklusive dess modulnamn.</span><span class="sxs-lookup"><span data-stu-id="77e9a-173">Using the script method of an object is equivalent to specifying the fully qualified name of an imported member, including its module name.</span></span>

<span data-ttu-id="77e9a-174">Parametern **AsCustomObject** kan bara användas när du importerar en-skript-modul.</span><span class="sxs-lookup"><span data-stu-id="77e9a-174">The **AsCustomObject** parameter can be used only when importing a script module.</span></span> <span data-ttu-id="77e9a-175">Används `Get-Module` för att avgöra vilka av de tillgängliga modulerna som är en skriptbaserad modul.</span><span class="sxs-lookup"><span data-stu-id="77e9a-175">Use `Get-Module` to determine which of the available modules is a script module.</span></span>

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

<span data-ttu-id="77e9a-176">`Show-Calendar`Modulen skript importeras med parametern **AsCustomObject** för att begära ett anpassat objekt och parametern **Passthru** för att returnera objektet.</span><span class="sxs-lookup"><span data-stu-id="77e9a-176">The `Show-Calendar` script module is imported using the **AsCustomObject** parameter to request a custom object and the **PassThru** parameter to return the object.</span></span> <span data-ttu-id="77e9a-177">Det resulterande anpassade objektet sparas i `$a` variabeln.</span><span class="sxs-lookup"><span data-stu-id="77e9a-177">The resulting custom object is saved in the `$a` variable.</span></span>

<span data-ttu-id="77e9a-178">`$a`Variabeln är skickas till `Get-Member` cmdleten för att visa egenskaper och metoder för det sparade objektet.</span><span class="sxs-lookup"><span data-stu-id="77e9a-178">The `$a` variable is piped to the `Get-Member` cmdlet to show the properties and methods of the saved object.</span></span> <span data-ttu-id="77e9a-179">Utdata visar en `Show-Calendar` skript metod.</span><span class="sxs-lookup"><span data-stu-id="77e9a-179">The output shows a `Show-Calendar` script method.</span></span>

<span data-ttu-id="77e9a-180">För att anropa `Show-Calendar` skript metoden måste metod namnet omges av citat tecken, eftersom namnet innehåller ett bindestreck.</span><span class="sxs-lookup"><span data-stu-id="77e9a-180">To call the `Show-Calendar` script method, the method name must be enclosed in quotation marks because the name includes a hyphen.</span></span>

### <span data-ttu-id="77e9a-181">Exempel 8: importera en modul igen till samma session</span><span class="sxs-lookup"><span data-stu-id="77e9a-181">Example 8: Reimport a module into the same session</span></span>

<span data-ttu-id="77e9a-182">Det här exemplet visar hur du använder **Force** -parametern i `Import-Module` när du importerar om en modul till samma session.</span><span class="sxs-lookup"><span data-stu-id="77e9a-182">This example shows how to use the **Force** parameter of `Import-Module` when you're reimporting a module into the same session.</span></span> <span data-ttu-id="77e9a-183">Parametern **Force** tar bort den inlästa modulen och importerar den sedan igen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-183">The **Force** parameter removes the loaded module and then imports it again.</span></span>

```powershell
Import-Module PSDiagnostics
Import-Module PSDiagnostics -Force -Prefix PS
```

<span data-ttu-id="77e9a-184">Det första kommandot importerar **PSDiagnostics** -modulen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-184">The first command imports the **PSDiagnostics** module.</span></span> <span data-ttu-id="77e9a-185">Det andra kommandot importerar modulen igen, den här gången med hjälp av parametern **prefix** .</span><span class="sxs-lookup"><span data-stu-id="77e9a-185">The second command imports the module again, this time using the **Prefix** parameter.</span></span>

<span data-ttu-id="77e9a-186">Utan **Force** -parametern innehåller sessionen två kopior av varje **PSDiagnostics** -cmdlet, en med standard namnet och en med det förfasta namnet.</span><span class="sxs-lookup"><span data-stu-id="77e9a-186">Without the **Force** parameter, the session would include two copies of each **PSDiagnostics** cmdlet, one with the standard name and one with the prefixed name.</span></span>

### <span data-ttu-id="77e9a-187">Exempel 9: kör kommandon som har dolts av importerade kommandon</span><span class="sxs-lookup"><span data-stu-id="77e9a-187">Example 9: Run commands that have been hidden by imported commands</span></span>

<span data-ttu-id="77e9a-188">Det här exemplet visar hur du kör kommandon som har dolts av importerade kommandon.</span><span class="sxs-lookup"><span data-stu-id="77e9a-188">This example shows how to run commands that have been hidden by imported commands.</span></span> <span data-ttu-id="77e9a-189">Modulen **TestModule** innehåller en funktion med namnet `Get-Date` som returnerar året och dagen på året.</span><span class="sxs-lookup"><span data-stu-id="77e9a-189">The **TestModule** module includes a function named `Get-Date` that returns the year and day of the year.</span></span>

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

<span data-ttu-id="77e9a-190">Den första `Get-Date` cmdleten returnerar ett **datetime** -objekt med det aktuella datumet.</span><span class="sxs-lookup"><span data-stu-id="77e9a-190">The first `Get-Date` cmdlet returns a **DateTime** object with the current date.</span></span> <span data-ttu-id="77e9a-191">När du har importerat modulen **TestModule** `Get-Date` returnerar året och dagen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-191">After importing the **TestModule** module, `Get-Date` returns the year and day of the year.</span></span>

<span data-ttu-id="77e9a-192">Använda **alla** -parametrar för `Get-Command` Visa alla `Get-Date` kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-192">Using the **All** parameter of `Get-Command` show all the `Get-Date` commands in the session.</span></span> <span data-ttu-id="77e9a-193">Resultaten visar att det finns två `Get-Date` kommandon i sessionen, en funktion från modulen **TestModule** och en cmdlet från **Microsoft. PowerShell. Utility** -modulen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-193">The results show that there are two `Get-Date` commands in the session, a function from the **TestModule** module and a cmdlet from the **Microsoft.PowerShell.Utility** module.</span></span>

<span data-ttu-id="77e9a-194">Eftersom funktioner prioriteras över cmdletar `Get-Date` körs funktionen från **TestModule** -modulen i stället för `Get-Date` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="77e9a-194">Because functions take precedence over cmdlets, the `Get-Date` function from the **TestModule** module runs, instead of the `Get-Date` cmdlet.</span></span> <span data-ttu-id="77e9a-195">Om du vill köra den ursprungliga versionen av `Get-Date` måste du kvalificera kommandots namn med modulnamnet.</span><span class="sxs-lookup"><span data-stu-id="77e9a-195">To run the original version of `Get-Date`, you must qualify the command name with the module name.</span></span>

<span data-ttu-id="77e9a-196">Mer information om kommando prioritet i PowerShell finns [about_Command_Precedence](about/about_Command_Precedence.md).</span><span class="sxs-lookup"><span data-stu-id="77e9a-196">For more information about command precedence in PowerShell, see [about_Command_Precedence](about/about_Command_Precedence.md).</span></span>

### <span data-ttu-id="77e9a-197">Exempel 10: importera en lägsta version av en modul</span><span class="sxs-lookup"><span data-stu-id="77e9a-197">Example 10: Import a minimum version of a module</span></span>

<span data-ttu-id="77e9a-198">I det här exemplet importeras modulen **PowerShellGet** .</span><span class="sxs-lookup"><span data-stu-id="77e9a-198">This example imports the **PowerShellGet** module.</span></span> <span data-ttu-id="77e9a-199">Den använder **MinimumVersion** -parametern för `Import-Module` för att importera version 2.0.0 eller större av modulen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-199">It uses the **MinimumVersion** parameter of `Import-Module` to import only version 2.0.0 or greater of the module.</span></span>

```powershell
Import-Module -Name PowerShellGet -MinimumVersion 2.0.0
```

<span data-ttu-id="77e9a-200">Du kan också använda parametern **RequiredVersion** för att importera en viss version av en modul eller använda parametrarna **module** och **version** för `#Requires` nyckelordet för att kräva en viss version av en modul i ett skript.</span><span class="sxs-lookup"><span data-stu-id="77e9a-200">You can also use the **RequiredVersion** parameter to import a particular version of a module, or use the **Module** and **Version** parameters of the `#Requires` keyword to require a particular version of a module in a script.</span></span>

### <span data-ttu-id="77e9a-201">Exempel 11: importera med ett fullständigt kvalificerat namn</span><span class="sxs-lookup"><span data-stu-id="77e9a-201">Example 11: Import using a fully qualified name</span></span>

<span data-ttu-id="77e9a-202">I det här exemplet importeras en angiven version av en modul med hjälp av FullyQualifiedName.</span><span class="sxs-lookup"><span data-stu-id="77e9a-202">This example imports a specific version of a module using the FullyQualifiedName.</span></span>

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

### <span data-ttu-id="77e9a-203">Exempel 12: importera med en fullständigt kvalificerad sökväg</span><span class="sxs-lookup"><span data-stu-id="77e9a-203">Example 12: Import using a fully qualified path</span></span>

<span data-ttu-id="77e9a-204">I det här exemplet importeras en särskild version av en modul med hjälp av den fullständigt kvalificerade sökvägen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-204">This example imports a specific version of a module using the fully qualified path.</span></span>

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

### <span data-ttu-id="77e9a-205">Exempel 13: importera en modul från en fjärran sluten dator</span><span class="sxs-lookup"><span data-stu-id="77e9a-205">Example 13: Import a module from a remote computer</span></span>

<span data-ttu-id="77e9a-206">Det här exemplet visar hur du använder `Import-Module` cmdleten för att importera en modul från en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="77e9a-206">This example shows how to use the `Import-Module` cmdlet to import a module from a remote computer.</span></span>
<span data-ttu-id="77e9a-207">Det här kommandot använder funktionen implicit fjärr kommunikation i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="77e9a-207">This command uses the Implicit Remoting feature of PowerShell.</span></span>

<span data-ttu-id="77e9a-208">När du importerar moduler från en annan session kan du använda cmdletarna i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-208">When you import modules from another session, you can use the cmdlets in the current session.</span></span>
<span data-ttu-id="77e9a-209">Kommandon som använder cmdletarna körs dock i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-209">However, commands that use the cmdlets run in the remote session.</span></span>

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

<span data-ttu-id="77e9a-210">`New-PSSession` skapar en fjärrsession (**PSSession**) till Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="77e9a-210">`New-PSSession` creates a remote session (**PSSession**) to the Server01 computer.</span></span> <span data-ttu-id="77e9a-211">**PSSession** sparas i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="77e9a-211">The **PSSession** is saved in the `$s` variable.</span></span>

<span data-ttu-id="77e9a-212">`Get-Module`Om du kör med parametern **PSSession** ser du att **netsecurity** -modulen är installerad och tillgänglig på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="77e9a-212">Running `Get-Module` with the **PSSession** parameter shows that the **NetSecurity** module is installed and available on the remote computer.</span></span> <span data-ttu-id="77e9a-213">Det här kommandot motsvarar att använda `Invoke-Command` cmdleten för att köra `Get-Module` kommandot i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-213">This command is equivalent to using the `Invoke-Command` cmdlet to run `Get-Module` command in the remote session.</span></span> <span data-ttu-id="77e9a-214">Exempel: (`Invoke-Command $s {Get-Module -ListAvailable -Name NetSecurity`</span><span class="sxs-lookup"><span data-stu-id="77e9a-214">For example: (`Invoke-Command $s {Get-Module -ListAvailable -Name NetSecurity`</span></span>

<span data-ttu-id="77e9a-215">Om `Import-Module` du kör med **PSSession** -parametern importeras **netsecurity** -modulen från fjärrdatorn till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-215">Running `Import-Module` with the **PSSession** parameter imports the **NetSecurity** module from the remote computer into the current session.</span></span> <span data-ttu-id="77e9a-216">`Get-Command`Cmdleten används för att hämta kommandon som börjar med **Get** -och include- **brandväggen** från modulen **netsecurity** .</span><span class="sxs-lookup"><span data-stu-id="77e9a-216">The `Get-Command` cmdlet is used to get commands that begin with **Get** and include **Firewall** from the **NetSecurity** module.</span></span> <span data-ttu-id="77e9a-217">Utdata bekräftar att modulen och dess cmdlets har importer ATS till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-217">The output confirms that the module and its cmdlets were imported into the current session.</span></span>

<span data-ttu-id="77e9a-218">Därefter `Get-NetFirewallRule` hämtar cmdlet Windows Remote Management brand Väggs regler på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="77e9a-218">Next, the `Get-NetFirewallRule` cmdlet gets Windows Remote Management firewall rules on the Server01 computer.</span></span> <span data-ttu-id="77e9a-219">Detta motsvarar att använda `Invoke-Command` cmdleten för att köras `Get-NetFirewallRule` i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-219">This is equivalent to using the `Invoke-Command` cmdlet to run `Get-NetFirewallRule` on the remote session.</span></span>

### <span data-ttu-id="77e9a-220">Exempel 14: Hantera lagring på en fjärrdator utan operativ systemet Windows</span><span class="sxs-lookup"><span data-stu-id="77e9a-220">Example 14: Manage storage on a remote computer without the Windows operating system</span></span>

<span data-ttu-id="77e9a-221">I det här exemplet har administratören för datorn installerat modulen för modul identifiering, som gör att du kan använda CIM-kommandon som är utformade för providern.</span><span class="sxs-lookup"><span data-stu-id="77e9a-221">In this example, the administrator of the computer has installed the Module Discovery WMI provider, which allows you to use CIM commands that are designed for the provider.</span></span>

<span data-ttu-id="77e9a-222">`New-CimSession`Cmdleten skapar en session på den fjärranslutna datorn med namnet RSDGF03.</span><span class="sxs-lookup"><span data-stu-id="77e9a-222">The `New-CimSession` cmdlet creates a session on the remote computer named RSDGF03.</span></span> <span data-ttu-id="77e9a-223">Sessionen ansluter till WMI-tjänsten på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="77e9a-223">The session connects to the WMI service on the remote computer.</span></span> <span data-ttu-id="77e9a-224">CIM-sessionen sparas i `$cs` variabeln.</span><span class="sxs-lookup"><span data-stu-id="77e9a-224">The CIM session is saved in the `$cs` variable.</span></span>
<span data-ttu-id="77e9a-225">`Import-Module` använder **CimSession** i `$cs` för att importera modulen **Storage** CIM från RSDGF03-datorn.</span><span class="sxs-lookup"><span data-stu-id="77e9a-225">`Import-Module` uses the **CimSession** in `$cs` to import the **Storage** CIM module from the RSDGF03 computer.</span></span>

<span data-ttu-id="77e9a-226">`Get-Command`Cmdleten visar `Get-Disk` kommandot i modulen **Storage** .</span><span class="sxs-lookup"><span data-stu-id="77e9a-226">The `Get-Command` cmdlet shows the `Get-Disk` command in the **Storage** module.</span></span> <span data-ttu-id="77e9a-227">När du importerar en CIM-modul till den lokala sessionen konverterar PowerShell CDXLM-filerna för varje kommando till PowerShell-skript, som visas som funktioner i den lokala sessionen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-227">When you import a CIM module into the local session, PowerShell converts the CDXML files for each command into PowerShell scripts, which appear as functions in the local session.</span></span>

<span data-ttu-id="77e9a-228">Trots `Get-Disk` att det har skrivits i den lokala sessionen körs cmdleten implicit på den fjärrdator som den importerades från.</span><span class="sxs-lookup"><span data-stu-id="77e9a-228">Although `Get-Disk` is typed in the local session, the cmdlet implicitly runs on the remote computer from which it was imported.</span></span> <span data-ttu-id="77e9a-229">Kommandot returnerar objekt från fjärrdatorn till den lokala sessionen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-229">The command returns objects from the remote computer to the local session.</span></span>

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

## <span data-ttu-id="77e9a-230">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="77e9a-230">PARAMETERS</span></span>

### <span data-ttu-id="77e9a-231">-Alias</span><span class="sxs-lookup"><span data-stu-id="77e9a-231">-Alias</span></span>

<span data-ttu-id="77e9a-232">Anger alias som denna cmdlet importerar från modulen till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-232">Specifies the aliases that this cmdlet imports from the module into the current session.</span></span> <span data-ttu-id="77e9a-233">Ange en kommaavgränsad lista över alias.</span><span class="sxs-lookup"><span data-stu-id="77e9a-233">Enter a comma-separated list of aliases.</span></span> <span data-ttu-id="77e9a-234">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="77e9a-234">Wildcard characters are permitted.</span></span>

<span data-ttu-id="77e9a-235">Vissa moduler exporterar automatiskt markerade alias till sessionen när du importerar modulen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-235">Some modules automatically export selected aliases into your session when you import the module.</span></span>
<span data-ttu-id="77e9a-236">Med den här parametern kan du välja bland de exporterade aliasen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-236">This parameter lets you select from among the exported aliases.</span></span>

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

### <span data-ttu-id="77e9a-237">– Argument List</span><span class="sxs-lookup"><span data-stu-id="77e9a-237">-ArgumentList</span></span>

<span data-ttu-id="77e9a-238">Anger en matris med argument, eller parameter värden, som skickas till en skript-modul under `Import-Module` kommandot.</span><span class="sxs-lookup"><span data-stu-id="77e9a-238">Specifies an array of arguments, or parameter values, that are passed to a script module during the `Import-Module` command.</span></span> <span data-ttu-id="77e9a-239">Den här parametern är endast giltig när du importerar en-skript-modul.</span><span class="sxs-lookup"><span data-stu-id="77e9a-239">This parameter is valid only when you're importing a script module.</span></span>

<span data-ttu-id="77e9a-240">Du kan också referera till parametern **argument List** med dess alias, **argument**.</span><span class="sxs-lookup"><span data-stu-id="77e9a-240">You can also refer to the **ArgumentList** parameter by its alias, **args**.</span></span> <span data-ttu-id="77e9a-241">Mer information om beteendet för **argument List** finns [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span><span class="sxs-lookup"><span data-stu-id="77e9a-241">For more information about the behavior of **ArgumentList**, see [about_Splatting](about/about_Splatting.md#splatting-with-arrays).</span></span>

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

### <span data-ttu-id="77e9a-242">-AsCustomObject</span><span class="sxs-lookup"><span data-stu-id="77e9a-242">-AsCustomObject</span></span>

<span data-ttu-id="77e9a-243">Anger att denna cmdlet returnerar ett anpassat objekt med medlemmar som representerar medlemmar i den importerade modulen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-243">Indicates that this cmdlet returns a custom object with members that represent the imported module members.</span></span> <span data-ttu-id="77e9a-244">Den här parametern är endast giltig för skript moduler.</span><span class="sxs-lookup"><span data-stu-id="77e9a-244">This parameter is valid only for script modules.</span></span>

<span data-ttu-id="77e9a-245">När du använder **AsCustomObject** -parametern `Import-Module` importerar modulen medlemmar till sessionen och returnerar sedan ett **PSCustomObject** -objekt i stället för ett **PSModuleInfo** -objekt.</span><span class="sxs-lookup"><span data-stu-id="77e9a-245">When you use the **AsCustomObject** parameter, `Import-Module` imports the module members into the session and then returns a **PSCustomObject** object instead of a **PSModuleInfo** object.</span></span> <span data-ttu-id="77e9a-246">Du kan spara det anpassade objektet i en variabel och använda punkt notation för att anropa medlemmarna.</span><span class="sxs-lookup"><span data-stu-id="77e9a-246">You can save the custom object in a variable and use dot notation to invoke the members.</span></span>

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

### <span data-ttu-id="77e9a-247">– Sammansättning</span><span class="sxs-lookup"><span data-stu-id="77e9a-247">-Assembly</span></span>

<span data-ttu-id="77e9a-248">Anger en matris med sammansättnings objekt.</span><span class="sxs-lookup"><span data-stu-id="77e9a-248">Specifies an array of assembly objects.</span></span> <span data-ttu-id="77e9a-249">Denna cmdlet importerar de cmdlets och providers som implementeras i de angivna sammansättnings objekten.</span><span class="sxs-lookup"><span data-stu-id="77e9a-249">This cmdlet imports the cmdlets and providers implemented in the specified assembly objects.</span></span> <span data-ttu-id="77e9a-250">Ange en variabel som innehåller sammansättnings objekt eller ett kommando som skapar sammansättnings objekt.</span><span class="sxs-lookup"><span data-stu-id="77e9a-250">Enter a variable that contains assembly objects or a command that creates assembly objects.</span></span> <span data-ttu-id="77e9a-251">Du kan också skicka ett sammansättnings objekt till `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="77e9a-251">You can also pipe an assembly object to `Import-Module`.</span></span>

<span data-ttu-id="77e9a-252">När du använder den här parametern importeras bara de cmdlets och providers som implementeras av de angivna sammansättningarna.</span><span class="sxs-lookup"><span data-stu-id="77e9a-252">When you use this parameter, only the cmdlets and providers implemented by the specified assemblies are imported.</span></span> <span data-ttu-id="77e9a-253">Om modulen innehåller andra filer importeras de inte, och du kanske saknar viktiga medlemmar i modulen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-253">If the module contains other files, they aren't imported, and you might be missing important members of the module.</span></span> <span data-ttu-id="77e9a-254">Använd den här parametern för att felsöka och testa modulen, eller när du uppmanas att använda den av modulens författare.</span><span class="sxs-lookup"><span data-stu-id="77e9a-254">Use this parameter for debugging and testing the module, or when you're instructed to use it by the module author.</span></span>

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

### <span data-ttu-id="77e9a-255">-CimNamespace</span><span class="sxs-lookup"><span data-stu-id="77e9a-255">-CimNamespace</span></span>

<span data-ttu-id="77e9a-256">Anger namn området för en alternativ CIM-provider som exponerar CIM-moduler.</span><span class="sxs-lookup"><span data-stu-id="77e9a-256">Specifies the namespace of an alternate CIM provider that exposes CIM modules.</span></span> <span data-ttu-id="77e9a-257">Standardvärdet är namn området för WMI-providern för modul identifiering.</span><span class="sxs-lookup"><span data-stu-id="77e9a-257">The default value is the namespace of the Module Discovery WMI provider.</span></span>

<span data-ttu-id="77e9a-258">Använd den här parametern för att importera CIM-moduler från datorer och enheter som inte kör ett Windows-operativsystem.</span><span class="sxs-lookup"><span data-stu-id="77e9a-258">Use this parameter to import CIM modules from computers and devices that aren't running a Windows operating system.</span></span>

<span data-ttu-id="77e9a-259">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="77e9a-259">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="77e9a-260">-CimResourceUri</span><span class="sxs-lookup"><span data-stu-id="77e9a-260">-CimResourceUri</span></span>

<span data-ttu-id="77e9a-261">Anger en alternativ plats för CIM-moduler.</span><span class="sxs-lookup"><span data-stu-id="77e9a-261">Specifies an alternate location for CIM modules.</span></span> <span data-ttu-id="77e9a-262">Standardvärdet är resurs-URI för WMI-providern för module-identifiering på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="77e9a-262">The default value is the resource URI of the Module Discovery WMI provider on the remote computer.</span></span>

<span data-ttu-id="77e9a-263">Använd den här parametern för att importera CIM-moduler från datorer och enheter som inte kör ett Windows-operativsystem.</span><span class="sxs-lookup"><span data-stu-id="77e9a-263">Use this parameter to import CIM modules from computers and devices that aren't running a Windows operating system.</span></span>

<span data-ttu-id="77e9a-264">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="77e9a-264">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="77e9a-265">– CimSession</span><span class="sxs-lookup"><span data-stu-id="77e9a-265">-CimSession</span></span>

<span data-ttu-id="77e9a-266">Anger en CIM-session på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="77e9a-266">Specifies a CIM session on the remote computer.</span></span> <span data-ttu-id="77e9a-267">Ange en variabel som innehåller CIM-sessionen eller ett kommando som hämtar CIM-sessionen, till exempel ett [Get-CimSession](../CimCmdlets/Get-CimSession.md) -kommando.</span><span class="sxs-lookup"><span data-stu-id="77e9a-267">Enter a variable that contains the CIM session or a command that gets the CIM session, such as a [Get-CimSession](../CimCmdlets/Get-CimSession.md) command.</span></span>

<span data-ttu-id="77e9a-268">`Import-Module` använder CIM-sessionen för att importera moduler från fjärrdatorn till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-268">`Import-Module` uses the CIM session connection to import modules from the remote computer into the current session.</span></span> <span data-ttu-id="77e9a-269">När du använder kommandona från den importerade modulen i den aktuella sessionen körs kommandona på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="77e9a-269">When you use the commands from the imported module in the current session, the commands run on the remote computer.</span></span>

<span data-ttu-id="77e9a-270">Du kan använda den här parametern för att importera moduler från datorer och enheter som inte kör Windows-operativsystemet och Windows-datorer som har PowerShell, men som inte har PowerShell-fjärrkommunikation aktive rad.</span><span class="sxs-lookup"><span data-stu-id="77e9a-270">You can use this parameter to import modules from computers and devices that aren't running the Windows operating system, and Windows computers that have PowerShell, but don't have PowerShell remoting enabled.</span></span>

<span data-ttu-id="77e9a-271">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="77e9a-271">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="77e9a-272">-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="77e9a-272">-Cmdlet</span></span>

<span data-ttu-id="77e9a-273">Anger en matris med cmdletar som denna cmdlet importerar från modulen till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-273">Specifies an array of cmdlets that this cmdlet imports from the module into the current session.</span></span>
<span data-ttu-id="77e9a-274">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="77e9a-274">Wildcard characters are permitted.</span></span>

<span data-ttu-id="77e9a-275">Vissa moduler exporterar automatiskt valda cmdlets till sessionen när du importerar modulen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-275">Some modules automatically export selected cmdlets into your session when you import the module.</span></span>
<span data-ttu-id="77e9a-276">Med den här parametern kan du välja bland de exporterade cmdletarna.</span><span class="sxs-lookup"><span data-stu-id="77e9a-276">This parameter lets you select from among the exported cmdlets.</span></span>

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

### <span data-ttu-id="77e9a-277">-DisableNameChecking</span><span class="sxs-lookup"><span data-stu-id="77e9a-277">-DisableNameChecking</span></span>

<span data-ttu-id="77e9a-278">Anger att denna cmdlet undertrycker meddelandet som varnar dig när du importerar en cmdlet eller funktion vars namn innehåller ett ej godkänt verb eller ett otillåtet Character.</span><span class="sxs-lookup"><span data-stu-id="77e9a-278">Indicates that this cmdlet suppresses the message that warns you when you import a cmdlet or function whose name includes an unapproved verb or a prohibited character.</span></span>

<span data-ttu-id="77e9a-279">Som standard visas följande varnings meddelande när en modul som du importerar exporterar cmdlets eller Functions som har icke-godkända verb i sina namn:</span><span class="sxs-lookup"><span data-stu-id="77e9a-279">By default, when a module that you import exports cmdlets or functions that have unapproved verbs in their names, PowerShell displays the following warning message:</span></span>

> <span data-ttu-id="77e9a-280">Varning! vissa importerade kommando namn innehåller icke-godkända verb som kan göra dem mindre synliga.</span><span class="sxs-lookup"><span data-stu-id="77e9a-280">WARNING: Some imported command names include unapproved verbs which might make them less discoverable.</span></span> <span data-ttu-id="77e9a-281">Använd verbose-parametern för mer information eller Skriv Get-Verb om du vill visa en lista över godkända verb.</span><span class="sxs-lookup"><span data-stu-id="77e9a-281">Use the Verbose parameter for more detail or type Get-Verb to see the list of approved verbs.</span></span>

<span data-ttu-id="77e9a-282">Det här meddelandet är bara en varning.</span><span class="sxs-lookup"><span data-stu-id="77e9a-282">This message is only a warning.</span></span> <span data-ttu-id="77e9a-283">Den kompletta modulen importeras fortfarande, inklusive kommandon som inte överensstämmer.</span><span class="sxs-lookup"><span data-stu-id="77e9a-283">The complete module is still imported, including the non-conforming commands.</span></span> <span data-ttu-id="77e9a-284">Även om meddelandet visas för modulen användare, bör namngivnings problemet åtgärdas av den som skapade modulen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-284">Although the message is displayed to module users, the naming problem should be fixed by the module author.</span></span>

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

### <span data-ttu-id="77e9a-285">-Force</span><span class="sxs-lookup"><span data-stu-id="77e9a-285">-Force</span></span>

<span data-ttu-id="77e9a-286">Den här parametern gör att en modul läses in eller läses in ovanpå den aktuella.</span><span class="sxs-lookup"><span data-stu-id="77e9a-286">This parameter causes a module to be loaded, or reloaded, over top of the current one.</span></span>

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

### <span data-ttu-id="77e9a-287">-FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="77e9a-287">-FullyQualifiedName</span></span>

<span data-ttu-id="77e9a-288">Anger modulens fullständigt kvalificerade namn som en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="77e9a-288">Specifies the fully qualified name of the module as a hash table.</span></span> <span data-ttu-id="77e9a-289">Värdet kan vara en kombination av strängar och hash-tabeller.</span><span class="sxs-lookup"><span data-stu-id="77e9a-289">The value can be a combination of strings and hash tables.</span></span> <span data-ttu-id="77e9a-290">Hash-tabellen har följande nycklar.</span><span class="sxs-lookup"><span data-stu-id="77e9a-290">The hash table has the following keys.</span></span>

- <span data-ttu-id="77e9a-291">`ModuleName` - **Krävs** Anger namnet på modulen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-291">`ModuleName` - **Required** Specifies the module name.</span></span>
- <span data-ttu-id="77e9a-292">`GUID` - **Valfritt** Anger modulens GUID.</span><span class="sxs-lookup"><span data-stu-id="77e9a-292">`GUID` - **Optional** Specifies the GUID of the module.</span></span>
- <span data-ttu-id="77e9a-293">Du **måste** också ange en av de tre nycklarna nedan.</span><span class="sxs-lookup"><span data-stu-id="77e9a-293">It's also **Required** to specify one of the three below keys.</span></span> <span data-ttu-id="77e9a-294">Nycklarna kan inte användas tillsammans.</span><span class="sxs-lookup"><span data-stu-id="77e9a-294">These keys can't be used together.</span></span>
  - <span data-ttu-id="77e9a-295">`ModuleVersion` -Anger en minsta godtagbar version av modulen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-295">`ModuleVersion` - Specifies a minimum acceptable version of the module.</span></span>
  - <span data-ttu-id="77e9a-296">`RequiredVersion` -Anger en exakt, obligatorisk version av modulen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-296">`RequiredVersion` - Specifies an exact, required version of the module.</span></span>
  - <span data-ttu-id="77e9a-297">`MaximumVersion` -Anger den högsta godkända versionen av modulen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-297">`MaximumVersion` - Specifies the maximum acceptable version of the module.</span></span>

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

### <span data-ttu-id="77e9a-298">– Funktion</span><span class="sxs-lookup"><span data-stu-id="77e9a-298">-Function</span></span>

<span data-ttu-id="77e9a-299">Anger en matris med funktioner som denna cmdlet importerar från modulen till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-299">Specifies an array of functions that this cmdlet imports from the module into the current session.</span></span>
<span data-ttu-id="77e9a-300">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="77e9a-300">Wildcard characters are permitted.</span></span> <span data-ttu-id="77e9a-301">Vissa moduler exporterar automatiskt markerade funktioner till sessionen när du importerar modulen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-301">Some modules automatically export selected functions into your session when you import the module.</span></span> <span data-ttu-id="77e9a-302">Med den här parametern kan du välja bland de exporterade funktionerna.</span><span class="sxs-lookup"><span data-stu-id="77e9a-302">This parameter lets you select from among the exported functions.</span></span>

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

### <span data-ttu-id="77e9a-303">– Global</span><span class="sxs-lookup"><span data-stu-id="77e9a-303">-Global</span></span>

<span data-ttu-id="77e9a-304">Anger att denna cmdlet importerar moduler till det globala sessionstillståndet så att de är tillgängliga för alla kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-304">Indicates that this cmdlet imports modules into the global session state so they are available to all commands in the session.</span></span>

<span data-ttu-id="77e9a-305">Som standard, när `Import-Module` cmdlet anropas från kommando tolken, skript filen eller script block, importeras alla kommandon till det globala sessionstillståndet.</span><span class="sxs-lookup"><span data-stu-id="77e9a-305">By default, when `Import-Module` cmdlet is called from the command prompt, script file, or scriptblock, all the commands are imported into the global session state.</span></span>

<span data-ttu-id="77e9a-306">Vid anrop från en annan modul `Import-Module` importerar cmdlet kommandon i en modul, inklusive kommandon från kapslade moduler, till den anropande modulens sessionstillstånd.</span><span class="sxs-lookup"><span data-stu-id="77e9a-306">When invoked from another module, `Import-Module` cmdlet imports the commands in a module, including commands from nested modules, into the calling module's session state.</span></span>

> [!TIP]
> <span data-ttu-id="77e9a-307">Undvik att anropa inifrån `Import-Module` en modul.</span><span class="sxs-lookup"><span data-stu-id="77e9a-307">You should avoid calling `Import-Module` from within a module.</span></span> <span data-ttu-id="77e9a-308">Deklarera i stället mål-modulen som en kapslad modul i den överordnade modulens manifest.</span><span class="sxs-lookup"><span data-stu-id="77e9a-308">Instead, declare the target module as a nested module in the parent module's manifest.</span></span> <span data-ttu-id="77e9a-309">Att deklarera kapslade moduler gör det enklare att identifiera beroenden.</span><span class="sxs-lookup"><span data-stu-id="77e9a-309">Declaring nested modules improves the discoverability of dependencies.</span></span>

<span data-ttu-id="77e9a-310">Den **globala** parametern motsvarar **omfattnings** parametern med värdet **Global**.</span><span class="sxs-lookup"><span data-stu-id="77e9a-310">The **Global** parameter is equivalent to the **Scope** parameter with a value of **Global**.</span></span>

<span data-ttu-id="77e9a-311">Om du vill begränsa vilka kommandon som en modul exporterar, använder du ett `Export-ModuleMember` kommando i modulen script.</span><span class="sxs-lookup"><span data-stu-id="77e9a-311">To restrict the commands that a module exports, use an `Export-ModuleMember` command in the script module.</span></span>

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

### <span data-ttu-id="77e9a-312">– MaximumVersion</span><span class="sxs-lookup"><span data-stu-id="77e9a-312">-MaximumVersion</span></span>

<span data-ttu-id="77e9a-313">Anger en högsta version.</span><span class="sxs-lookup"><span data-stu-id="77e9a-313">Specifies a maximum version.</span></span> <span data-ttu-id="77e9a-314">Den här cmdleten importerar bara en version av modulen som är mindre än eller lika med det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="77e9a-314">This cmdlet imports only a version of the module that is less than or equal to the specified value.</span></span> <span data-ttu-id="77e9a-315">Om ingen version kvalificeras `Import-Module` returneras ett fel.</span><span class="sxs-lookup"><span data-stu-id="77e9a-315">If no version qualifies, `Import-Module` returns an error.</span></span>

```yaml
Type: System.String
Parameter Sets: Name, PSSession, CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="77e9a-316">– MinimumVersion</span><span class="sxs-lookup"><span data-stu-id="77e9a-316">-MinimumVersion</span></span>

<span data-ttu-id="77e9a-317">Anger en lägsta version.</span><span class="sxs-lookup"><span data-stu-id="77e9a-317">Specifies a minimum version.</span></span> <span data-ttu-id="77e9a-318">Den här cmdleten importerar bara en version av modulen som är större än eller lika med det angivna värdet.</span><span class="sxs-lookup"><span data-stu-id="77e9a-318">This cmdlet imports only a version of the module that is greater than or equal to the specified value.</span></span> <span data-ttu-id="77e9a-319">Använd **MinimumVersion** parameter namn eller dess alias, **version**.</span><span class="sxs-lookup"><span data-stu-id="77e9a-319">Use the **MinimumVersion** parameter name or its alias, **Version**.</span></span> <span data-ttu-id="77e9a-320">Om ingen version kvalificeras `Import-Module` genererar ett fel.</span><span class="sxs-lookup"><span data-stu-id="77e9a-320">If no version qualifies, `Import-Module` generates an error.</span></span>

<span data-ttu-id="77e9a-321">Om du vill ange en exakt version använder du parametern **RequiredVersion** .</span><span class="sxs-lookup"><span data-stu-id="77e9a-321">To specify an exact version, use the **RequiredVersion** parameter.</span></span> <span data-ttu-id="77e9a-322">Du kan också använda **modul** -och **versions** parametrar för **#Requires** nyckelordet för att kräva en speciell version av en modul i ett skript.</span><span class="sxs-lookup"><span data-stu-id="77e9a-322">You can also use the **Module** and **Version** parameters of the **#Requires** keyword to require a specific version of a module in a script.</span></span>

<span data-ttu-id="77e9a-323">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="77e9a-323">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Version
Parameter Sets: Name, PSSession, CimSession
Aliases: Version

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="77e9a-324">-ModuleInfo</span><span class="sxs-lookup"><span data-stu-id="77e9a-324">-ModuleInfo</span></span>

<span data-ttu-id="77e9a-325">Anger en matris med modul-objekt som ska importeras.</span><span class="sxs-lookup"><span data-stu-id="77e9a-325">Specifies an array of module objects to import.</span></span> <span data-ttu-id="77e9a-326">Ange en variabel som innehåller modulens objekt, eller ett kommando som hämtar modulens objekt, till exempel följande kommando: `Get-Module -ListAvailable` .</span><span class="sxs-lookup"><span data-stu-id="77e9a-326">Enter a variable that contains the module objects, or a command that gets the module objects, such as the following command: `Get-Module -ListAvailable`.</span></span> <span data-ttu-id="77e9a-327">Du kan också skicka modul objekt till `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="77e9a-327">You can also pipe module objects to `Import-Module`.</span></span>

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

### <span data-ttu-id="77e9a-328">-Name</span><span class="sxs-lookup"><span data-stu-id="77e9a-328">-Name</span></span>

<span data-ttu-id="77e9a-329">Anger namnen på de moduler som ska importeras.</span><span class="sxs-lookup"><span data-stu-id="77e9a-329">Specifies the names of the modules to import.</span></span> <span data-ttu-id="77e9a-330">Ange namnet på modulen eller namnet på en fil i modulen, till exempel en,, eller en `.psd1` `.psm1` `.dll` `.ps1` fil.</span><span class="sxs-lookup"><span data-stu-id="77e9a-330">Enter the name of the module or the name of a file in the module, such as a `.psd1`, `.psm1`, `.dll`, or `.ps1` file.</span></span> <span data-ttu-id="77e9a-331">Fil Sök vägar är valfria.</span><span class="sxs-lookup"><span data-stu-id="77e9a-331">File paths are optional.</span></span> <span data-ttu-id="77e9a-332">Jokertecken är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="77e9a-332">Wildcard characters aren't permitted.</span></span> <span data-ttu-id="77e9a-333">Du kan också skicka namn och fil namn för moduler till `Import-Module` .</span><span class="sxs-lookup"><span data-stu-id="77e9a-333">You can also pipe module names and filenames to `Import-Module`.</span></span>

<span data-ttu-id="77e9a-334">Om du utelämnar en sökväg `Import-Module` söker du efter modulen i Sök vägarna som sparats i `$env:PSModulePath` miljö variabeln.</span><span class="sxs-lookup"><span data-stu-id="77e9a-334">If you omit a path, `Import-Module` looks for the module in the paths saved in the `$env:PSModulePath` environment variable.</span></span>

<span data-ttu-id="77e9a-335">Ange bara modulnamnet när det är möjligt.</span><span class="sxs-lookup"><span data-stu-id="77e9a-335">Specify only the module name whenever possible.</span></span> <span data-ttu-id="77e9a-336">När du anger ett fil namn importeras bara de medlemmar som implementeras i den filen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-336">When you specify a file name, only the members that are implemented in that file are imported.</span></span> <span data-ttu-id="77e9a-337">Om modulen innehåller andra filer importeras de inte, och du kanske saknar viktiga medlemmar i modulen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-337">If the module contains other files, they aren't imported, and you might be missing important members of the module.</span></span>

> [!NOTE]
> <span data-ttu-id="77e9a-338">Även om det är möjligt att importera en skript `.ps1` fil () som en modul, är skriptfilerna vanligt vis inte strukturerat som script modules File ( `.psm1` )-fil.</span><span class="sxs-lookup"><span data-stu-id="77e9a-338">While it is possible to import a script (`.ps1`) file as a module, script files are usually not structured like script modules file (`.psm1`) file.</span></span> <span data-ttu-id="77e9a-339">Att importera en skript fil garanterar inte att den kan användas som en modul.</span><span class="sxs-lookup"><span data-stu-id="77e9a-339">Importing a script file does not guarantee that it is usable as a module.</span></span> <span data-ttu-id="77e9a-340">Mer information finns i [about_Modules](about/about_Modules.md).</span><span class="sxs-lookup"><span data-stu-id="77e9a-340">For more information, see [about_Modules](about/about_Modules.md).</span></span>

```yaml
Type: System.String[]
Parameter Sets: Name, PSSession, CimSession
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="77e9a-341">-NoClobber</span><span class="sxs-lookup"><span data-stu-id="77e9a-341">-NoClobber</span></span>

<span data-ttu-id="77e9a-342">Förhindrar att du importerar kommandon som har samma namn som befintliga kommandon i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-342">Prevents importing commands that have the same names as existing commands in the current session.</span></span> <span data-ttu-id="77e9a-343">Som standard `Import-Module` importerar alla exporterade module-kommandon.</span><span class="sxs-lookup"><span data-stu-id="77e9a-343">By default, `Import-Module` imports all exported module commands.</span></span>

<span data-ttu-id="77e9a-344">Kommandon som har samma namn kan dölja eller ersätta kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-344">Commands that have the same names can hide or replace commands in the session.</span></span> <span data-ttu-id="77e9a-345">Använd **prefix** -eller **NoClobber** -parametrarna för att undvika kommando namns konflikter i en session.</span><span class="sxs-lookup"><span data-stu-id="77e9a-345">To avoid command name conflicts in a session, use the **Prefix** or **NoClobber** parameters.</span></span> <span data-ttu-id="77e9a-346">Mer information om namn konflikter och kommando prioritet finns i "moduler och namn konflikter" i [about_Modules](about/about_Modules.md) och [about_Command_Precedence](about/about_Command_Precedence.md).</span><span class="sxs-lookup"><span data-stu-id="77e9a-346">For more information about name conflicts and command precedence, see "Modules and Name Conflicts" in [about_Modules](about/about_Modules.md) and [about_Command_Precedence](about/about_Command_Precedence.md).</span></span>

<span data-ttu-id="77e9a-347">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="77e9a-347">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="77e9a-348">– PassThru</span><span class="sxs-lookup"><span data-stu-id="77e9a-348">-PassThru</span></span>

<span data-ttu-id="77e9a-349">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="77e9a-349">Returns an object representing the item with which you're working.</span></span> <span data-ttu-id="77e9a-350">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="77e9a-350">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="77e9a-351">-Prefix</span><span class="sxs-lookup"><span data-stu-id="77e9a-351">-Prefix</span></span>

<span data-ttu-id="77e9a-352">Anger ett prefix som denna cmdlet lägger till i Substantiv i namnen på importerade modul medlemmar.</span><span class="sxs-lookup"><span data-stu-id="77e9a-352">Specifies a prefix that this cmdlet adds to the nouns in the names of imported module members.</span></span>

<span data-ttu-id="77e9a-353">Använd den här parametern för att undvika namn konflikter som kan uppstå när olika medlemmar i sessionen har samma namn.</span><span class="sxs-lookup"><span data-stu-id="77e9a-353">Use this parameter to avoid name conflicts that might occur when different members in the session have the same name.</span></span> <span data-ttu-id="77e9a-354">Den här parametern ändrar inte modulen och påverkar inte filer som modulen importerar för eget bruk.</span><span class="sxs-lookup"><span data-stu-id="77e9a-354">This parameter does not change the module, and it does not affect files that the module imports for its own use.</span></span> <span data-ttu-id="77e9a-355">Dessa kallas kapslade moduler.</span><span class="sxs-lookup"><span data-stu-id="77e9a-355">These are known as nested modules.</span></span> <span data-ttu-id="77e9a-356">Denna cmdlet påverkar bara namnen på medlemmar i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-356">This cmdlet affects only the names of members in the current session.</span></span>

<span data-ttu-id="77e9a-357">Om du till exempel anger prefixet UTC och sedan importerar en `Get-Date` cmdlet, är cmdleten känd i sessionen som `Get-UTCDate` och den förväxlas inte med den ursprungliga `Get-Date` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="77e9a-357">For example, if you specify the prefix UTC and then import a `Get-Date` cmdlet, the cmdlet is known in the session as `Get-UTCDate`, and it is not confused with the original `Get-Date` cmdlet.</span></span>

<span data-ttu-id="77e9a-358">Värdet för den här parametern prioriteras över **DefaultCommandPrefix** -egenskapen för modulen, som anger standardprefixet.</span><span class="sxs-lookup"><span data-stu-id="77e9a-358">The value of this parameter takes precedence over the **DefaultCommandPrefix** property of the module, which specifies the default prefix.</span></span>

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

### <span data-ttu-id="77e9a-359">– PSSession</span><span class="sxs-lookup"><span data-stu-id="77e9a-359">-PSSession</span></span>

<span data-ttu-id="77e9a-360">Anger en PowerShell-**PSSession**(User-Managed session) från vilken denna cmdlet importerar moduler till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-360">Specifies a PowerShell user-managed session (**PSSession**) from which this cmdlet imports modules into the current session.</span></span> <span data-ttu-id="77e9a-361">Ange en variabel som innehåller ett **PSSession** eller ett kommando som hämtar en **PSSession**, till exempel ett `Get-PSSession` kommando.</span><span class="sxs-lookup"><span data-stu-id="77e9a-361">Enter a variable that contains a **PSSession** or a command that gets a **PSSession**, such as a `Get-PSSession` command.</span></span>

<span data-ttu-id="77e9a-362">När du importerar en modul från en annan session till den aktuella sessionen kan du använda cmdletar från modulen i den aktuella sessionen, precis som du skulle använda cmdlets från en lokal modul.</span><span class="sxs-lookup"><span data-stu-id="77e9a-362">When you import a module from a different session into the current session, you can use the cmdlets from the module in the current session, just as you would use cmdlets from a local module.</span></span> <span data-ttu-id="77e9a-363">Kommandon som använder fjärrcmdlets körs i fjärrsessionen, men fjärrinformationen hanteras i bakgrunden av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="77e9a-363">Commands that use the remote cmdlets run in the remote session, but the remoting details are managed in the background by PowerShell.</span></span>

<span data-ttu-id="77e9a-364">Den här parametern använder funktionen implicit fjärr kommunikation i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="77e9a-364">This parameter uses the Implicit Remoting feature of PowerShell.</span></span> <span data-ttu-id="77e9a-365">Det motsvarar att använda `Import-PSSession` cmdleten för att importera specifika moduler från en session.</span><span class="sxs-lookup"><span data-stu-id="77e9a-365">It is equivalent to using the `Import-PSSession` cmdlet to import particular modules from a session.</span></span>

<span data-ttu-id="77e9a-366">`Import-Module` Det går inte att importera PowerShell Core-moduler från en annan session.</span><span class="sxs-lookup"><span data-stu-id="77e9a-366">`Import-Module` cannot import PowerShell Core modules from another session.</span></span> <span data-ttu-id="77e9a-367">PowerShell Core-modulerna har namn som inleds med Microsoft. PowerShell.</span><span class="sxs-lookup"><span data-stu-id="77e9a-367">The PowerShell Core modules have names that begin with Microsoft.PowerShell.</span></span>

<span data-ttu-id="77e9a-368">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="77e9a-368">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="77e9a-369">– RequiredVersion</span><span class="sxs-lookup"><span data-stu-id="77e9a-369">-RequiredVersion</span></span>

<span data-ttu-id="77e9a-370">Anger en version av modulen som denna cmdlet importerar.</span><span class="sxs-lookup"><span data-stu-id="77e9a-370">Specifies a version of the module that this cmdlet imports.</span></span> <span data-ttu-id="77e9a-371">Om versionen inte är installerad `Import-Module` genererar ett fel.</span><span class="sxs-lookup"><span data-stu-id="77e9a-371">If the version is not installed, `Import-Module` generates an error.</span></span>

<span data-ttu-id="77e9a-372">Som standard `Import-Module` importerar modulen utan att kontrol lera versions numret.</span><span class="sxs-lookup"><span data-stu-id="77e9a-372">By default, `Import-Module` imports the module without checking the version number.</span></span>

<span data-ttu-id="77e9a-373">Om du vill ange en lägsta version använder du parametern **MinimumVersion** .</span><span class="sxs-lookup"><span data-stu-id="77e9a-373">To specify a minimum version, use the **MinimumVersion** parameter.</span></span> <span data-ttu-id="77e9a-374">Du kan också använda **modul** -och **versions** parametrar för **#Requires** nyckelordet för att kräva en speciell version av en modul i ett skript.</span><span class="sxs-lookup"><span data-stu-id="77e9a-374">You can also use the **Module** and **Version** parameters of the **#Requires** keyword to require a specific version of a module in a script.</span></span>

<span data-ttu-id="77e9a-375">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="77e9a-375">This parameter was introduced in Windows PowerShell 3.0.</span></span>

<span data-ttu-id="77e9a-376">Skript som använder **RequiredVersion** för att importera moduler som ingår i befintliga versioner av Windows operativ system körs inte automatiskt i framtida versioner av Windows operativ system.</span><span class="sxs-lookup"><span data-stu-id="77e9a-376">Scripts that use **RequiredVersion** to import modules that are included with existing releases of the Windows operating system don't automatically run in future releases of the Windows operating system.</span></span> <span data-ttu-id="77e9a-377">Detta beror på att PowerShell-modulens versions nummer i framtida versioner av Windows operativ system är högre än versions nummer för modul i befintliga versioner av Windows operativ system.</span><span class="sxs-lookup"><span data-stu-id="77e9a-377">This is because PowerShell module version numbers in future releases of the Windows operating system are higher than module version numbers in existing releases of the Windows operating system.</span></span>

```yaml
Type: System.Version
Parameter Sets: Name, PSSession, CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="77e9a-378">– Omfattning</span><span class="sxs-lookup"><span data-stu-id="77e9a-378">-Scope</span></span>

<span data-ttu-id="77e9a-379">Anger ett omfång där denna cmdlet importerar modulen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-379">Specifies a scope into which this cmdlet imports the module.</span></span>

<span data-ttu-id="77e9a-380">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="77e9a-380">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="77e9a-381">**Global**.</span><span class="sxs-lookup"><span data-stu-id="77e9a-381">**Global**.</span></span> <span data-ttu-id="77e9a-382">Tillgängligt för alla kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-382">Available to all commands in the session.</span></span> <span data-ttu-id="77e9a-383">Motsvarar den **globala** parametern.</span><span class="sxs-lookup"><span data-stu-id="77e9a-383">Equivalent to the **Global** parameter.</span></span>
- <span data-ttu-id="77e9a-384">**Lokal**.</span><span class="sxs-lookup"><span data-stu-id="77e9a-384">**Local**.</span></span> <span data-ttu-id="77e9a-385">Endast tillgängligt i det aktuella omfånget.</span><span class="sxs-lookup"><span data-stu-id="77e9a-385">Available only in the current scope.</span></span>

<span data-ttu-id="77e9a-386">Som standard, när `Import-Module` cmdlet anropas från kommando tolken, skript filen eller script block, importeras alla kommandon till det globala sessionstillståndet.</span><span class="sxs-lookup"><span data-stu-id="77e9a-386">By default, when `Import-Module` cmdlet is called from the command prompt, script file, or scriptblock, all the commands are imported into the global session state.</span></span> <span data-ttu-id="77e9a-387">Du kan använda- `-Scope Local` parametern för att importera modul innehåll till skriptet eller script block-omfånget.</span><span class="sxs-lookup"><span data-stu-id="77e9a-387">You can use the `-Scope Local` parameter to import module content into the script or scriptblock scope.</span></span>

<span data-ttu-id="77e9a-388">Vid anrop från en annan modul `Import-Module` importerar cmdlet kommandon i en modul, inklusive kommandon från kapslade moduler, till anroparens sessionstillstånd.</span><span class="sxs-lookup"><span data-stu-id="77e9a-388">When invoked from another module, `Import-Module` cmdlet imports the commands in a module, including commands from nested modules, into the caller's session state.</span></span> <span data-ttu-id="77e9a-389">Ange `-Scope Global` eller `-Global` anger att denna cmdlet importerar moduler till det globala sessionstillståndet så att de är tillgängliga för alla kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-389">Specifying `-Scope Global` or `-Global` indicates that this cmdlet imports modules into the global session state so they are available to all commands in the session.</span></span>

<span data-ttu-id="77e9a-390">Den **globala** parametern motsvarar **omfattnings** parametern med värdet **Global**.</span><span class="sxs-lookup"><span data-stu-id="77e9a-390">The **Global** parameter is equivalent to the **Scope** parameter with a value of **Global**.</span></span>

<span data-ttu-id="77e9a-391">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="77e9a-391">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="77e9a-392">– Variabel</span><span class="sxs-lookup"><span data-stu-id="77e9a-392">-Variable</span></span>

<span data-ttu-id="77e9a-393">Anger en matris med variabler som denna cmdlet importerar från modulen till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-393">Specifies an array of variables that this cmdlet imports from the module into the current session.</span></span>
<span data-ttu-id="77e9a-394">Ange en lista med variabler.</span><span class="sxs-lookup"><span data-stu-id="77e9a-394">Enter a list of variables.</span></span> <span data-ttu-id="77e9a-395">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="77e9a-395">Wildcard characters are permitted.</span></span>

<span data-ttu-id="77e9a-396">Vissa moduler exporterar automatiskt markerade variabler till sessionen när du importerar modulen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-396">Some modules automatically export selected variables into your session when you import the module.</span></span>
<span data-ttu-id="77e9a-397">Med den här parametern kan du välja bland de exporterade variablerna.</span><span class="sxs-lookup"><span data-stu-id="77e9a-397">This parameter lets you select from among the exported variables.</span></span>

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

### <span data-ttu-id="77e9a-398">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="77e9a-398">CommonParameters</span></span>
<span data-ttu-id="77e9a-399">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="77e9a-399">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="77e9a-400">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="77e9a-400">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="77e9a-401">INDATA</span><span class="sxs-lookup"><span data-stu-id="77e9a-401">INPUTS</span></span>

### <span data-ttu-id="77e9a-402">System. String, system. Management. Automation. PSModuleInfo, system. Reflection. Assembly</span><span class="sxs-lookup"><span data-stu-id="77e9a-402">System.String, System.Management.Automation.PSModuleInfo, System.Reflection.Assembly</span></span>

<span data-ttu-id="77e9a-403">Du kan skicka vidare ett modulnamn, module-objekt eller Assembly-objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="77e9a-403">You can pipe a module name, module object, or assembly object to this cmdlet.</span></span>

## <span data-ttu-id="77e9a-404">UTDATA</span><span class="sxs-lookup"><span data-stu-id="77e9a-404">OUTPUTS</span></span>

### <span data-ttu-id="77e9a-405">Ingen, system. Management. Automation. PSModuleInfo eller system. Management. Automation. PSCustomObject</span><span class="sxs-lookup"><span data-stu-id="77e9a-405">None, System.Management.Automation.PSModuleInfo, or System.Management.Automation.PSCustomObject</span></span>

<span data-ttu-id="77e9a-406">`Import-Module`Genererar inga utdata som standard.</span><span class="sxs-lookup"><span data-stu-id="77e9a-406">By default, `Import-Module` does not generate any output.</span></span> <span data-ttu-id="77e9a-407">Om du anger parametern **Passthru** genererar cmdleten ett **system. Management. Automation. PSModuleInfo** -objekt som representerar modulen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-407">If you specify the **PassThru** parameter, the cmdlet generates a **System.Management.Automation.PSModuleInfo** object that represents the module.</span></span> <span data-ttu-id="77e9a-408">Om du anger parametern **AsCustomObject** genereras ett **PSCustomObject** -objekt.</span><span class="sxs-lookup"><span data-stu-id="77e9a-408">If you specify the **AsCustomObject** parameter, it generates a **PSCustomObject** object.</span></span>

## <span data-ttu-id="77e9a-409">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="77e9a-409">NOTES</span></span>

- <span data-ttu-id="77e9a-410">Innan du kan importera en modul måste modulen vara installerad på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="77e9a-410">Before you can import a module, the module must be installed on the local computer.</span></span> <span data-ttu-id="77e9a-411">Därför måste modul katalogen kopieras till en katalog som är tillgänglig för den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="77e9a-411">That is, the module directory must be copied to a directory that is accessible to your local computer.</span></span> <span data-ttu-id="77e9a-412">Mer information finns i [about_Modules](About/about_Modules.md).</span><span class="sxs-lookup"><span data-stu-id="77e9a-412">For more information, see [about_Modules](About/about_Modules.md).</span></span>

  <span data-ttu-id="77e9a-413">Du kan också använda parametrarna **PSSession** och **CIMSession** för att importera moduler som är installerade på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="77e9a-413">You can also use the **PSSession** and **CIMSession** parameters to import modules that are installed on remote computers.</span></span> <span data-ttu-id="77e9a-414">Kommandon som använder cmdletarna i dessa moduler körs dock i fjärrsessionen på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="77e9a-414">However, commands that use the cmdlets in these modules run in the remote session on the remote computer.</span></span>

- <span data-ttu-id="77e9a-415">Om du importerar medlemmar med samma namn och samma typ i din session, använder PowerShell medlemmen som importer ATS sist som standard.</span><span class="sxs-lookup"><span data-stu-id="77e9a-415">If you import members with the same name and the same type into your session, PowerShell uses the member imported last by default.</span></span> <span data-ttu-id="77e9a-416">Variabler och alias ersätts och originalen är inte tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="77e9a-416">Variables and aliases are replaced, and the originals aren't accessible.</span></span> <span data-ttu-id="77e9a-417">Funktioner, cmdletar och providrar är bara skuggade av de nya medlemmarna.</span><span class="sxs-lookup"><span data-stu-id="77e9a-417">Functions, cmdlets, and providers are merely shadowed by the new members.</span></span> <span data-ttu-id="77e9a-418">De kan nås genom att kvalificera kommando namnet med namnet på dess snapin-modul, modul eller funktions Sök väg.</span><span class="sxs-lookup"><span data-stu-id="77e9a-418">They can be accessed by qualifying the command name with the name of its snap-in, module, or function path.</span></span>

- <span data-ttu-id="77e9a-419">Använd cmdleten för att uppdatera formaterings data för kommandon som har importer ATS från en modul `Update-FormatData` .</span><span class="sxs-lookup"><span data-stu-id="77e9a-419">To update the formatting data for commands that have been imported from a module, use the `Update-FormatData` cmdlet.</span></span> <span data-ttu-id="77e9a-420">`Update-FormatData` uppdaterar också formaterings data för kommandon i sessionen som har importer ATS från moduler.</span><span class="sxs-lookup"><span data-stu-id="77e9a-420">`Update-FormatData` also updates the formatting data for commands in the session that were imported from modules.</span></span> <span data-ttu-id="77e9a-421">Om format filen för en modul ändras kan du köra ett `Update-FormatData` kommando för att uppdatera formateringen för importerade kommandon.</span><span class="sxs-lookup"><span data-stu-id="77e9a-421">If the formatting file for a module changes, you can run an `Update-FormatData` command to update the formatting data for imported commands.</span></span> <span data-ttu-id="77e9a-422">Du behöver inte importera modulen igen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-422">You don't need to import the module again.</span></span>

- <span data-ttu-id="77e9a-423">Från och med Windows PowerShell 3,0 paketeras de grundläggande kommandon som installeras med PowerShell i moduler.</span><span class="sxs-lookup"><span data-stu-id="77e9a-423">Starting in Windows PowerShell 3.0, the core commands that are installed with PowerShell are packaged in modules.</span></span> <span data-ttu-id="77e9a-424">I Windows PowerShell 2,0 och i värd program som skapar äldre sessioner i senare versioner av PowerShell, paketeras huvud kommandona i snapin-moduler (**PSSnapins**).</span><span class="sxs-lookup"><span data-stu-id="77e9a-424">In Windows PowerShell 2.0, and in host programs that create older-style sessions in later versions of PowerShell, the core commands are packaged in snap-ins (**PSSnapins**).</span></span> <span data-ttu-id="77e9a-425">Undantaget är **Microsoft. PowerShell. Core**, som alltid är en snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="77e9a-425">The exception is **Microsoft.PowerShell.Core**, which is always a snap-in.</span></span> <span data-ttu-id="77e9a-426">Fjärrsessioner, till exempel de som startas av `New-PSSession` cmdleten, är äldre sessioner som inkluderar grundläggande snapin-moduler.</span><span class="sxs-lookup"><span data-stu-id="77e9a-426">Also, remote sessions, such as those started by the `New-PSSession` cmdlet, are older-style sessions that include core snap-ins.</span></span>

  <span data-ttu-id="77e9a-427">Information om **CreateDefault2** -metoden som skapar nyare sessioner med Core-moduler finns i [CreateDefault2-metoden](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2).</span><span class="sxs-lookup"><span data-stu-id="77e9a-427">For information about the **CreateDefault2** method that creates newer-style sessions with core modules, see the [CreateDefault2 Method](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2).</span></span>

- <span data-ttu-id="77e9a-428">I Windows PowerShell 2,0 fylldes några av egenskapsvärdena för objektet modul, till exempel egenskapsvärdena **ExportedCmdlets** och **NestedModules** , inte förrän modulen importerades.</span><span class="sxs-lookup"><span data-stu-id="77e9a-428">In Windows PowerShell 2.0, some of the property values of the module object, such as the **ExportedCmdlets** and **NestedModules** property values, were not populated until the module was imported.</span></span>

- <span data-ttu-id="77e9a-429">Om du försöker importera en modul som innehåller sammansättningar med blandat läge som inte är kompatibla med Windows PowerShell 3.0 +, `Import-Module` returnerar ett fel meddelande som liknar följande.</span><span class="sxs-lookup"><span data-stu-id="77e9a-429">If you attempt to import a module that contains mixed-mode assemblies that aren't compatible with Windows PowerShell 3.0+, `Import-Module` returns an error message like the following one.</span></span>

  > <span data-ttu-id="77e9a-430">Import-Module: blandad läges sammansättning har skapats mot version "v 2.0.50727" av körningen och kan inte läsas in i 4,0-körningsmiljön utan ytterligare konfigurations information.</span><span class="sxs-lookup"><span data-stu-id="77e9a-430">Import-Module : Mixed mode assembly is built against version 'v2.0.50727' of the runtime and cannot be loaded in the 4.0 runtime without additional configuration information.</span></span>

  <span data-ttu-id="77e9a-431">Felet uppstår när en modul som är avsedd för Windows PowerShell 2,0 innehåller minst en sammansättning med blandat moduler.</span><span class="sxs-lookup"><span data-stu-id="77e9a-431">This error occurs when a module that is designed for Windows PowerShell 2.0 contains at least one mixed-module assembly.</span></span> <span data-ttu-id="77e9a-432">En sammansättning med blandade moduler som innehåller både hanterad och icke-hanterad kod, till exempel C++ och C#.</span><span class="sxs-lookup"><span data-stu-id="77e9a-432">A mixed-module assembly that includes both managed and non-managed code, such as C++ and C#.</span></span>

  <span data-ttu-id="77e9a-433">Om du vill importera en modul som innehåller sammansättningar med blandat läge startar du Windows PowerShell 2,0 med hjälp av följande kommando och försöker sedan `Import-Module` igen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-433">To import a module that contains mixed-mode assemblies, start Windows PowerShell 2.0 by using the following command, and then try the `Import-Module` command again.</span></span>

  `PowerShell.exe -Version 2.0`

- <span data-ttu-id="77e9a-434">Om du vill använda funktionen CIM-sessionen måste fjärrdatorn ha WS-Management fjärr anslutning och Windows Management Instrumentation (WMI), som är Microsofts implementering av Common Information Model (CIM) standard.</span><span class="sxs-lookup"><span data-stu-id="77e9a-434">To use the CIM session feature, the remote computer must have WS-Management remoting and Windows Management Instrumentation (WMI), which is the Microsoft implementation of the Common Information Model (CIM) standard.</span></span> <span data-ttu-id="77e9a-435">Datorn måste också ha WMI-providern för modul identifiering eller en alternativ CIM-provider som har samma grundläggande funktioner.</span><span class="sxs-lookup"><span data-stu-id="77e9a-435">The computer must also have the Module Discovery WMI provider or an alternate CIM provider that has the same basic features.</span></span>

  <span data-ttu-id="77e9a-436">Du kan använda funktionen för CIM-sessionen på datorer som inte kör ett Windows-operativsystem och på Windows-datorer som har PowerShell, men inte har PowerShell-fjärrkommunikation aktive rad.</span><span class="sxs-lookup"><span data-stu-id="77e9a-436">You can use the CIM session feature on computers that aren't running a Windows operating system and on Windows computers that have PowerShell, but don't have PowerShell remoting enabled.</span></span>

  <span data-ttu-id="77e9a-437">Du kan också använda CIM-parametrarna för att hämta CIM-moduler från datorer där PowerShell-fjärrkommunikation är aktiverat, inklusive den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="77e9a-437">You can also use the CIM parameters to get CIM modules from computers that have PowerShell remoting enabled, including the local computer.</span></span> <span data-ttu-id="77e9a-438">När du skapar en CIM-session på den lokala datorn använder PowerShell DCOM, i stället för WMI, för att skapa sessionen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-438">When you create a CIM session on the local computer, PowerShell uses DCOM, instead of WMI, to create the session.</span></span>

- <span data-ttu-id="77e9a-439">Som standard `Import-Module` importerar moduler i det globala omfånget även när de anropas från ett underordnat omfång.</span><span class="sxs-lookup"><span data-stu-id="77e9a-439">By default, `Import-Module` imports modules in the global scope even when called from a descendant scope.</span></span> <span data-ttu-id="77e9a-440">Omfattningen på den översta nivån och alla underordnade omfattningar har åtkomst till modulens exporterade element.</span><span class="sxs-lookup"><span data-stu-id="77e9a-440">The top-level scope and all descendant scopes have access to the module's exported elements.</span></span>

  <span data-ttu-id="77e9a-441">I ett underordnat omfång `-Scope Local` begränsar importen till det omfånget och alla dess underordnade omfång.</span><span class="sxs-lookup"><span data-stu-id="77e9a-441">In a descendant scope, `-Scope Local` limits the import to that scope and all its descendant scopes.</span></span> <span data-ttu-id="77e9a-442">Överordnade omfattningar ser inte de importerade medlemmarna.</span><span class="sxs-lookup"><span data-stu-id="77e9a-442">Parent scopes then do not see the imported members.</span></span>

  > [!NOTE]
  > <span data-ttu-id="77e9a-443">`Get-Module` visar alla moduler som lästs in i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-443">`Get-Module` shows all modules loaded in the current session.</span></span> <span data-ttu-id="77e9a-444">Detta inkluderar moduler som lästs in lokalt i ett underordnat omfång.</span><span class="sxs-lookup"><span data-stu-id="77e9a-444">This includes modules loaded locally in a descendant scope.</span></span> <span data-ttu-id="77e9a-445">Använd `Get-Command -Module modulename` för att se vilka medlemmar som läses in i det aktuella omfånget.</span><span class="sxs-lookup"><span data-stu-id="77e9a-445">Use `Get-Command -Module modulename` to see which members are loaded in the current scope.</span></span>

  <span data-ttu-id="77e9a-446">`Import-Module` läser inte in definitioner av klass och Enum i modulen.</span><span class="sxs-lookup"><span data-stu-id="77e9a-446">`Import-Module` does not load class and enum definitions in the module.</span></span> <span data-ttu-id="77e9a-447">Använd `using module` instruktionen i början av skriptet.</span><span class="sxs-lookup"><span data-stu-id="77e9a-447">Use the `using module` statement at the beginning of your script.</span></span> <span data-ttu-id="77e9a-448">Detta importerar modulen, inklusive klass-och uppräknings definitioner.</span><span class="sxs-lookup"><span data-stu-id="77e9a-448">This imports the module, including the class and enum definitions.</span></span> <span data-ttu-id="77e9a-449">Mer information finns i [about_Using](About/about_Using.md).</span><span class="sxs-lookup"><span data-stu-id="77e9a-449">For more information, see [about_Using](About/about_Using.md).</span></span>

## <span data-ttu-id="77e9a-450">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="77e9a-450">RELATED LINKS</span></span>

[<span data-ttu-id="77e9a-451">about_Modules</span><span class="sxs-lookup"><span data-stu-id="77e9a-451">about_Modules</span></span>](about/about_Modules.md)

[<span data-ttu-id="77e9a-452">Exportera – ModuleMember</span><span class="sxs-lookup"><span data-stu-id="77e9a-452">Export-ModuleMember</span></span>](Export-ModuleMember.md)

[<span data-ttu-id="77e9a-453">Hämta modul</span><span class="sxs-lookup"><span data-stu-id="77e9a-453">Get-Module</span></span>](Get-Module.md)

[<span data-ttu-id="77e9a-454">Ny modul</span><span class="sxs-lookup"><span data-stu-id="77e9a-454">New-Module</span></span>](New-Module.md)

[<span data-ttu-id="77e9a-455">Ta bort modul</span><span class="sxs-lookup"><span data-stu-id="77e9a-455">Remove-Module</span></span>](Remove-Module.md)
