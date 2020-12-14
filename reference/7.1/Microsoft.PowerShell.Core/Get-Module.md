---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-module?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Module
ms.openlocfilehash: 1f06d1e7114a84ea89097167b188ded605f81aa0
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564545"
---
# <span data-ttu-id="dc723-102">Get-Module</span><span class="sxs-lookup"><span data-stu-id="dc723-102">Get-Module</span></span>

## <span data-ttu-id="dc723-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="dc723-103">SYNOPSIS</span></span>
<span data-ttu-id="dc723-104">Lista de moduler som har importer ATS i den aktuella sessionen eller som kan importeras från PSModulePath.</span><span class="sxs-lookup"><span data-stu-id="dc723-104">List the modules imported in the current session or that can be imported from the PSModulePath.</span></span>

## <span data-ttu-id="dc723-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="dc723-105">SYNTAX</span></span>

### <span data-ttu-id="dc723-106">Läst in (standard)</span><span class="sxs-lookup"><span data-stu-id="dc723-106">Loaded (Default)</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-All] [<CommonParameters>]
```

### <span data-ttu-id="dc723-107">Tillgängligt</span><span class="sxs-lookup"><span data-stu-id="dc723-107">Available</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-All] [-ListAvailable]
 [-PSEdition <String>] [-SkipEditionCheck] [-Refresh] [<CommonParameters>]
```

### <span data-ttu-id="dc723-108">PsSession</span><span class="sxs-lookup"><span data-stu-id="dc723-108">PsSession</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-ListAvailable]
 [-PSEdition <String>] [-SkipEditionCheck] [-Refresh] -PSSession <PSSession> [<CommonParameters>]
```

### <span data-ttu-id="dc723-109">CimSession</span><span class="sxs-lookup"><span data-stu-id="dc723-109">CimSession</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-ListAvailable]
 [-SkipEditionCheck] [-Refresh] -CimSession <CimSession> [-CimResourceUri <Uri>] [-CimNamespace <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="dc723-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="dc723-110">DESCRIPTION</span></span>

<span data-ttu-id="dc723-111">`Get-Module`Cmdleten listar PowerShell-modulerna som har importer ATS, eller som kan importeras, i en PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="dc723-111">The `Get-Module` cmdlet lists the PowerShell modules that have been imported, or that can be imported, into a PowerShell session.</span></span> <span data-ttu-id="dc723-112">Utan parametrar, `Get-Module` hämtar moduler som har importer ATS till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="dc723-112">Without parameters, `Get-Module` gets modules that have been imported into the current session.</span></span> <span data-ttu-id="dc723-113">Parametern **ListAvailable** används för att visa en lista över de moduler som är tillgängliga för import från Sök vägarna som anges i PSModulePath-miljövariabeln ( `$env:PSModulePath` ).</span><span class="sxs-lookup"><span data-stu-id="dc723-113">The **ListAvailable** parameter is used to list the modules that are available to be imported from the paths specified in the PSModulePath environment variable (`$env:PSModulePath`).</span></span>

<span data-ttu-id="dc723-114">Module-objektet som `Get-Module` returnerar innehåller värdefull information om modulen.</span><span class="sxs-lookup"><span data-stu-id="dc723-114">The module object that `Get-Module` returns contains valuable information about the module.</span></span> <span data-ttu-id="dc723-115">Du kan också skicka modulens objekt till andra cmdletar, till exempel- `Import-Module` och- `Remove-Module` cmdlet: ar.</span><span class="sxs-lookup"><span data-stu-id="dc723-115">You can also pipe the module objects to other cmdlets, such as the `Import-Module` and `Remove-Module` cmdlets.</span></span>

<span data-ttu-id="dc723-116">`Get-Module` visar en lista över moduler, men importerar dem inte.</span><span class="sxs-lookup"><span data-stu-id="dc723-116">`Get-Module` lists modules, but it does not import them.</span></span> <span data-ttu-id="dc723-117">Från och med Windows PowerShell 3,0 importeras moduler automatiskt när du använder ett kommando i modulen, men ett `Get-Module` kommando utlöser inte en automatisk import.</span><span class="sxs-lookup"><span data-stu-id="dc723-117">Starting in Windows PowerShell 3.0, modules are automatically imported when you use a command in the module, but a `Get-Module` command does not trigger an automatic import.</span></span> <span data-ttu-id="dc723-118">Du kan också importera modulerna till sessionen med hjälp av `Import-Module` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="dc723-118">You can also import the modules into your session using the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="dc723-119">Från och med Windows PowerShell 3,0 kan du hämta och importera moduler från fjärrsessioner till den lokala sessionen.</span><span class="sxs-lookup"><span data-stu-id="dc723-119">Starting in Windows PowerShell 3.0, you can get and then, import modules from remote sessions into the local session.</span></span> <span data-ttu-id="dc723-120">Den här strategin använder funktionen implicit fjärr kommunikation i PowerShell och motsvarar att använda `Import-PSSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="dc723-120">This strategy uses the Implicit Remoting feature of PowerShell and is equivalent to using the `Import-PSSession` cmdlet.</span></span> <span data-ttu-id="dc723-121">När du använder kommandon i moduler som importer ATS från en annan session körs kommandona implicit i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="dc723-121">When you use commands in modules imported from another session, the commands run implicitly in the remote session.</span></span> <span data-ttu-id="dc723-122">Med den här funktionen kan du hantera fjärrdatorn från den lokala sessionen.</span><span class="sxs-lookup"><span data-stu-id="dc723-122">This feature lets you manage the remote computer from the local session.</span></span>

<span data-ttu-id="dc723-123">Från och med Windows PowerShell 3,0 kan du också använda `Get-Module` och `Import-Module` för att hämta och importera common information Model-moduler (CIM).</span><span class="sxs-lookup"><span data-stu-id="dc723-123">Also, starting in Windows PowerShell 3.0, you can use `Get-Module` and `Import-Module` to get and import Common Information Model (CIM) modules.</span></span> <span data-ttu-id="dc723-124">CIM-moduler definierar cmdletar i CDXLM-filer (cmdlet definition XML).</span><span class="sxs-lookup"><span data-stu-id="dc723-124">CIM modules define cmdlets in Cmdlet Definition XML (CDXML) files.</span></span> <span data-ttu-id="dc723-125">Med den här funktionen kan du använda cmdletar som implementeras i icke-hanterade kod sammansättningar, t. ex. sådana som skrivits i C++.</span><span class="sxs-lookup"><span data-stu-id="dc723-125">This feature lets you use cmdlets that are implemented in non-managed code assemblies, such as those written in C++.</span></span>

<span data-ttu-id="dc723-126">Implicit fjärr kommunikation kan användas för att hantera fjärrdatorer som har PowerShell-fjärrkommunikation aktive rad.</span><span class="sxs-lookup"><span data-stu-id="dc723-126">Implicit remoting can be used to manage remote computers that have PowerShell remoting enabled.</span></span>
<span data-ttu-id="dc723-127">Skapa en **PSSession** på fjärrdatorn och Använd sedan **PSSession** -parametern för `Get-Module` för att hämta PowerShell-modulerna i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="dc723-127">Create a **PSSession** on the remote computer and then use the **PSSession** parameter of `Get-Module` to get the PowerShell modules in the remote session.</span></span> <span data-ttu-id="dc723-128">När du importerar en modul från fjärrsessionen körs de importerade kommandona i sessionen på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="dc723-128">When you import a module from the remote session the imported commands run in the session on the remote computer.</span></span>

<span data-ttu-id="dc723-129">Du kan använda en liknande strategi för att hantera datorer som inte har PowerShell-fjärrkommunikation aktive rad.</span><span class="sxs-lookup"><span data-stu-id="dc723-129">You can use a similar strategy to manage computers that do not have PowerShell remoting enabled.</span></span>
<span data-ttu-id="dc723-130">Detta inkluderar datorer som inte kör Windows-operativsystemet och datorer som har PowerShell men inte har PowerShell-fjärrkommunikation aktive rad.</span><span class="sxs-lookup"><span data-stu-id="dc723-130">These include computers that are not running the Windows operating system, and computers that have PowerShell but do not have PowerShell remoting enabled.</span></span>

<span data-ttu-id="dc723-131">Börja med att skapa en CIM-session på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="dc723-131">Start by creating a CIM session on the remote computer.</span></span> <span data-ttu-id="dc723-132">En CIM-session är en anslutning till Windows Management Instrumentation (WMI) på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="dc723-132">A CIM session is a connection to Windows Management Instrumentation (WMI) on the remote computer.</span></span> <span data-ttu-id="dc723-133">Använd sedan **CIMSession** -parametern för `Get-Module` för att hämta CIM-moduler från CIM-sessionen.</span><span class="sxs-lookup"><span data-stu-id="dc723-133">Then use the **CIMSession** parameter of `Get-Module` to get CIM modules from the CIM session.</span></span> <span data-ttu-id="dc723-134">När du importerar en CIM-modul med hjälp av `Import-Module` cmdleten och sedan kör de importerade kommandona, körs kommandona implicit på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="dc723-134">When you import a CIM module by using the `Import-Module` cmdlet and then run the imported commands, the commands run implicitly on the remote computer.</span></span> <span data-ttu-id="dc723-135">Du kan använda den här WMI-och CIM-strategin för att hantera fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="dc723-135">You can use this WMI and CIM strategy to manage the remote computer.</span></span>

## <span data-ttu-id="dc723-136">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="dc723-136">EXAMPLES</span></span>

### <span data-ttu-id="dc723-137">Exempel 1: Hämta moduler som importer ATS till den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="dc723-137">Example 1: Get modules imported into the current session</span></span>

```powershell
Get-Module
```

<span data-ttu-id="dc723-138">Det här kommandot hämtar moduler som har importer ATS till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="dc723-138">This command gets modules that have been imported into the current session.</span></span>

### <span data-ttu-id="dc723-139">Exempel 2: Hämta installerade moduler och tillgängliga moduler</span><span class="sxs-lookup"><span data-stu-id="dc723-139">Example 2: Get installed modules and available modules</span></span>

```powershell
Get-Module -ListAvailable
```

<span data-ttu-id="dc723-140">Detta kommando hämtar de moduler som är installerade på datorn och som kan importeras till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="dc723-140">This command gets the modules that are installed on the computer and can be imported into the current session.</span></span>

<span data-ttu-id="dc723-141">`Get-Module` söker efter tillgängliga moduler i sökvägen som anges av variabeln **$env:P smodulepath** -miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="dc723-141">`Get-Module` looks for available modules in the path specified by the **$env:PSModulePath** environment variable.</span></span> <span data-ttu-id="dc723-142">Mer information om **PSModulePath** finns i [about_Modules](About/about_Modules.md) och [about_Environment_Variables](About/about_Environment_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="dc723-142">For more information about **PSModulePath**, see [about_Modules](About/about_Modules.md) and [about_Environment_Variables](About/about_Environment_Variables.md).</span></span>

### <span data-ttu-id="dc723-143">Exempel 3: Hämta alla exporterade filer</span><span class="sxs-lookup"><span data-stu-id="dc723-143">Example 3: Get all exported files</span></span>

```powershell
Get-Module -ListAvailable -All
```

<span data-ttu-id="dc723-144">Det här kommandot hämtar alla exporterade filer för alla tillgängliga moduler.</span><span class="sxs-lookup"><span data-stu-id="dc723-144">This command gets all of the exported files for all available modules.</span></span>

### <span data-ttu-id="dc723-145">Exempel 4: Hämta en modul med dess fullständigt kvalificerade namn</span><span class="sxs-lookup"><span data-stu-id="dc723-145">Example 4: Get a module by its fully qualified name</span></span>

```powershell
$FullyQualifedName = @{ModuleName="Microsoft.PowerShell.Management";ModuleVersion="3.1.0.0"}
Get-Module -FullyQualifiedName $FullyQualifedName | Format-Table -Property Name,Version
```

```Output
Name                             Version
----                             -------
Microsoft.PowerShell.Management  3.1.0.0
```

<span data-ttu-id="dc723-146">Detta kommando hämtar modulen **Microsoft. PowerShell. Management** genom att ange det fullständigt kvalificerade namnet på modulen med hjälp av parametern **FullyQualifiedName** .</span><span class="sxs-lookup"><span data-stu-id="dc723-146">This command gets the **Microsoft.PowerShell.Management** module by specifying the fully qualified name of the module by using the **FullyQualifiedName** parameter.</span></span> <span data-ttu-id="dc723-147">Kommandot rör sedan resultatet i `Format-Table` cmdleten för att formatera resultatet som en tabell med **namn** och **version** som kolumn rubriker.</span><span class="sxs-lookup"><span data-stu-id="dc723-147">The command then pipes the results into the `Format-Table` cmdlet to format the results as a table with **Name** and **Version** as the column headings.</span></span>

### <span data-ttu-id="dc723-148">Exempel 5: Hämta egenskaper för en modul</span><span class="sxs-lookup"><span data-stu-id="dc723-148">Example 5: Get properties of a module</span></span>

```powershell
Get-Module | Get-Member -MemberType Property | Format-Table Name
```

```Output
Name
----
AccessMode
Author
ClrVersion
CompanyName
Copyright
Definition
Description
DotNetFrameworkVersion
ExportedAliases
ExportedCmdlets
ExportedCommands
ExportedFormatFiles
ExportedFunctions
ExportedTypeFiles
ExportedVariables
ExportedWorkflows
FileList
Guid
HelpInfoUri
LogPipelineExecutionDetails
ModuleBase
ModuleList
ModuleType
Name
NestedModules
OnRemove
Path
PowerShellHostName
PowerShellHostVersion
PowerShellVersion
PrivateData
ProcessorArchitecture
RequiredAssemblies
RequiredModules
RootModule
Scripts
SessionState
Version
```

<span data-ttu-id="dc723-149">Det här kommandot hämtar egenskaperna för det **PSModuleInfo** -objekt som `Get-Module` returneras.</span><span class="sxs-lookup"><span data-stu-id="dc723-149">This command gets the properties of the **PSModuleInfo** object that `Get-Module` returns.</span></span> <span data-ttu-id="dc723-150">Det finns ett objekt för varje modul-fil.</span><span class="sxs-lookup"><span data-stu-id="dc723-150">There is one object for each module file.</span></span>

<span data-ttu-id="dc723-151">Du kan använda egenskaperna för att formatera och filtrera modulens objekt.</span><span class="sxs-lookup"><span data-stu-id="dc723-151">You can use the properties to format and filter the module objects.</span></span> <span data-ttu-id="dc723-152">Mer information om egenskaperna finns i PSModuleInfo- [Egenskaper](/dotnet/api/system.management.automation.psmoduleinfo).</span><span class="sxs-lookup"><span data-stu-id="dc723-152">For more information about the properties, see [PSModuleInfo Properties](/dotnet/api/system.management.automation.psmoduleinfo).</span></span>

<span data-ttu-id="dc723-153">Utdata innehåller de nya egenskaperna, till exempel **författare** och **företags namn**, som introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="dc723-153">The output includes the new properties, such as **Author** and **CompanyName**, that were introduced in Windows PowerShell 3.0.</span></span>

### <span data-ttu-id="dc723-154">Exempel 6: gruppera alla moduler efter namn</span><span class="sxs-lookup"><span data-stu-id="dc723-154">Example 6: Group all modules by name</span></span>

```powershell
Get-Module -ListAvailable -All | Format-Table -Property Name, Moduletype, Path -Groupby Name
```

```Output
Name: AppLocker

Name      ModuleType Path
----      ---------- ----
AppLocker   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\AppLocker\AppLocker.psd1


   Name: Appx

Name ModuleType Path
---- ---------- ----
Appx   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Appx\en-US\Appx.psd1
Appx   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Appx\Appx.psd1
Appx     Script C:\Windows\system32\WindowsPowerShell\v1.0\Modules\Appx\Appx.psm1


   Name: BestPractices

Name          ModuleType Path
----          ---------- ----
BestPractices   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\BestPractices\BestPractices.psd1


   Name: BitsTransfer

Name         ModuleType Path
----         ---------- ----
BitsTransfer   Manifest C:\Windows\system32\WindowsPowerShell\v1.0\Modules\BitsTransfer\BitsTransfer.psd1
```

<span data-ttu-id="dc723-155">Det här kommandot hämtar alla modulblad, både importerade och tillgängliga, och grupperar dem efter modulnamn.</span><span class="sxs-lookup"><span data-stu-id="dc723-155">This command gets all module files, both imported and available, and then groups them by module name.</span></span> <span data-ttu-id="dc723-156">På så sätt kan du se de module-filer som varje skript exporterar.</span><span class="sxs-lookup"><span data-stu-id="dc723-156">This lets you see the module files that each script is exporting.</span></span>

### <span data-ttu-id="dc723-157">Exempel 7: Visa innehållet i ett modul-manifest</span><span class="sxs-lookup"><span data-stu-id="dc723-157">Example 7: Display the contents of a module manifest</span></span>

<span data-ttu-id="dc723-158">Dessa kommandon visar innehållet i modulens manifest för Windows PowerShell-modulen **BitsTransfer** .</span><span class="sxs-lookup"><span data-stu-id="dc723-158">These commands display the contents of the module manifest for the Windows PowerShell **BitsTransfer** module.</span></span>

<span data-ttu-id="dc723-159">Moduler måste inte ha MANIFEST-filer.</span><span class="sxs-lookup"><span data-stu-id="dc723-159">Modules are not required to have manifest files.</span></span> <span data-ttu-id="dc723-160">När de har en manifest fil, krävs manifest filen bara för att inkludera ett versions nummer.</span><span class="sxs-lookup"><span data-stu-id="dc723-160">When they do have a manifest file, the manifest file is required only to include a version number.</span></span> <span data-ttu-id="dc723-161">Manifest filen innehåller dock ofta användbar information om en modul, dess krav och dess innehåll.</span><span class="sxs-lookup"><span data-stu-id="dc723-161">However, manifest files often provide useful information about a module, its requirements, and its contents.</span></span>

```powershell
# First command
$m = Get-Module -list -Name BitsTransfer

# Second command
Get-Content $m.Path
```

```Output
@ {
    GUID               = "{8FA5064B-8479-4c5c-86EA-0D311FE48875}"
    Author             = "Microsoft Corporation"
    CompanyName        = "Microsoft Corporation"
    Copyright          = "Microsoft Corporation. All rights reserved."
    ModuleVersion      = "1.0.0.0"
    Description        = "Windows PowerShell File Transfer Module"
    PowerShellVersion  = "2.0"
    CLRVersion         = "2.0"
    NestedModules      = "Microsoft.BackgroundIntelligentTransfer.Management"
    FormatsToProcess   = "FileTransfer.Format.ps1xml"
    RequiredAssemblies = Join-Path $psScriptRoot "Microsoft.BackgroundIntelligentTransfer.Management.Interop.dll"
}
```

<span data-ttu-id="dc723-162">Det första kommandot hämtar PSModuleInfo-objektet som representerar BitsTransfer-modulen.</span><span class="sxs-lookup"><span data-stu-id="dc723-162">The first command gets the PSModuleInfo object that represents BitsTransfer module.</span></span> <span data-ttu-id="dc723-163">Objektet sparas i `$m` variabeln.</span><span class="sxs-lookup"><span data-stu-id="dc723-163">It saves the object in the `$m` variable.</span></span>

<span data-ttu-id="dc723-164">Det andra kommandot använder `Get-Content` cmdleten för att hämta innehållet i manifest filen på den angivna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="dc723-164">The second command uses the `Get-Content` cmdlet to get the content of the manifest file in the specified path.</span></span> <span data-ttu-id="dc723-165">Den använder punkt notation för att hämta sökvägen till manifest filen, som lagras i objektets Sök vägs egenskap.</span><span class="sxs-lookup"><span data-stu-id="dc723-165">It uses dot notation to get the path to the manifest file, which is stored in the Path property of the object.</span></span> <span data-ttu-id="dc723-166">Utdata visar innehållet i modulens manifest.</span><span class="sxs-lookup"><span data-stu-id="dc723-166">The output shows the contents of the module manifest.</span></span>

### <span data-ttu-id="dc723-167">Exempel 8: Visa filer i modulens katalog</span><span class="sxs-lookup"><span data-stu-id="dc723-167">Example 8: List files in module directory</span></span>

```powershell
dir (Get-Module -ListAvailable FileTransfer).ModuleBase
```

```Output
Directory: C:\Windows\system32\WindowsPowerShell\v1.0\Modules\FileTransfer
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        12/16/2008  12:36 PM            en-US
-a---        11/19/2008  11:30 PM      16184 FileTransfer.Format.ps1xml
-a---        11/20/2008  11:30 PM       1044 FileTransfer.psd1
-a---        12/16/2008  12:20 AM     108544 Microsoft.BackgroundIntelligentTransfer.Management.Interop.dll
```

<span data-ttu-id="dc723-168">Det här kommandot visar filerna i modulens katalog.</span><span class="sxs-lookup"><span data-stu-id="dc723-168">This command lists the files in the directory of the module.</span></span> <span data-ttu-id="dc723-169">Detta är ett annat sätt att avgöra vad som finns i en modul innan du importerar den.</span><span class="sxs-lookup"><span data-stu-id="dc723-169">This is another way to determine what is in a module before you import it.</span></span> <span data-ttu-id="dc723-170">Vissa moduler kan ha hjälpfiler eller ReadMe-filer som beskriver modulen.</span><span class="sxs-lookup"><span data-stu-id="dc723-170">Some modules might have help files or ReadMe files that describe the module.</span></span>

### <span data-ttu-id="dc723-171">Exempel 9: Hämta moduler som är installerade på en dator</span><span class="sxs-lookup"><span data-stu-id="dc723-171">Example 9: Get modules installed on a computer</span></span>

```powershell
$s = New-PSSession -ComputerName Server01

Get-Module -PSSession $s -ListAvailable
```

<span data-ttu-id="dc723-172">De här kommandona hämtar de moduler som är installerade på den Server01 datorn.</span><span class="sxs-lookup"><span data-stu-id="dc723-172">These commands get the modules that are installed on the Server01 computer.</span></span>

<span data-ttu-id="dc723-173">Det första kommandot använder `New-PSSession` cmdleten för att skapa en **PSSession** på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="dc723-173">The first command uses the `New-PSSession` cmdlet to create a **PSSession** on the Server01 computer.</span></span> <span data-ttu-id="dc723-174">Kommandot sparar **PSSession** i variabeln $s.</span><span class="sxs-lookup"><span data-stu-id="dc723-174">The command saves the **PSSession** in the $s variable.</span></span>

<span data-ttu-id="dc723-175">Det andra kommandot använder parametrarna **PSSession** och **ListAvailable** för `Get-Module` för att hämta modulerna i **PSSession** i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="dc723-175">The second command uses the **PSSession** and **ListAvailable** parameters of `Get-Module` to get the modules in the **PSSession** in the `$s` variable.</span></span>

<span data-ttu-id="dc723-176">Om du rör moduler från andra sessioner till `Import-Module` cmdlet: en `Import-Module` importerar modulen till den aktuella sessionen med hjälp av funktionen implicit fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="dc723-176">If you pipe modules from other sessions to the `Import-Module` cmdlet, `Import-Module` imports the module into the current session by using the implicit remoting feature.</span></span> <span data-ttu-id="dc723-177">Detta motsvarar att använda `Import-PSSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="dc723-177">This is equivalent to using the `Import-PSSession` cmdlet.</span></span> <span data-ttu-id="dc723-178">Du kan använda cmdlets från modulen i den aktuella sessionen, men kommandon som använder dessa cmdlets kör i själva verket fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="dc723-178">You can use the cmdlets from the module in the current session, but commands that use these cmdlets actually run the remote session.</span></span> <span data-ttu-id="dc723-179">Mer information finns i [`Import-Module`](Import-Module.md) och [`Import-PSSession`](../Microsoft.PowerShell.Utility/Import-PSSession.md) .</span><span class="sxs-lookup"><span data-stu-id="dc723-179">For more information, see [`Import-Module`](Import-Module.md) and [`Import-PSSession`](../Microsoft.PowerShell.Utility/Import-PSSession.md).</span></span>

### <span data-ttu-id="dc723-180">Exempel 10: hantera en dator som inte kör Windows operativ system</span><span class="sxs-lookup"><span data-stu-id="dc723-180">Example 10: Manage a computer that does not run the Windows operating system</span></span>

<span data-ttu-id="dc723-181">Med kommandona i det här exemplet kan du hantera lagrings systemen på en fjärrdator som inte kör Windows-operativsystemet.</span><span class="sxs-lookup"><span data-stu-id="dc723-181">The commands in this example enable you to manage the storage systems of a remote computer that is not running the Windows operating system.</span></span>
<span data-ttu-id="dc723-182">I det här exemplet, eftersom datorns administratör har installerat WMI-providern för modul identifiering, kan CIM-kommandon använda standardvärdena, som är utformade för providern.</span><span class="sxs-lookup"><span data-stu-id="dc723-182">In this example, because the administrator of the computer has installed the Module Discovery WMI provider, the CIM commands can use the default values, which are designed for the provider.</span></span>

```powershell
$cs = New-CimSession -ComputerName RSDGF03
Get-Module -CimSession $cs -Name Storage | Import-Module
Get-Command Get-Disk
```

```Output
CommandType     Name                  ModuleName
-----------     ----                  ----------
Function        Get-Disk              Storage
```

```powershell
Get-Disk
```

```Output
Number Friendly Name              OperationalStatus          Total Size Partition Style
------ -------------              -----------------          ---------- ---------------
0      Virtual HD ATA Device      Online                          40 GB MBR
```

<span data-ttu-id="dc723-183">Det första kommandot använder `New-CimSession` cmdleten för att skapa en session på RSDGF03-fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="dc723-183">The first command uses the `New-CimSession` cmdlet to create a session on the RSDGF03 remote computer.</span></span> <span data-ttu-id="dc723-184">Sessionen ansluter till WMI på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="dc723-184">The session connects to WMI on the remote computer.</span></span> <span data-ttu-id="dc723-185">Kommandot sparar CIM-sessionen i `$cs` variabeln.</span><span class="sxs-lookup"><span data-stu-id="dc723-185">The command saves the CIM session in the `$cs` variable.</span></span>

<span data-ttu-id="dc723-186">Det andra kommandot använder CIM-sessionen i `$cs` variabeln för att köra ett `Get-Module` kommando på RSDGF03-datorn.</span><span class="sxs-lookup"><span data-stu-id="dc723-186">The second command uses the CIM session in the `$cs` variable to run a `Get-Module` command on the RSDGF03 computer.</span></span> <span data-ttu-id="dc723-187">Kommandot använder name-parametern för att ange Storage-modulen.</span><span class="sxs-lookup"><span data-stu-id="dc723-187">The command uses the Name parameter to specify the Storage module.</span></span> <span data-ttu-id="dc723-188">Kommandot använder en pipeline-operator (|) för att skicka modulen till `Import-Module` cmdleten, som importerar den till den lokala sessionen.</span><span class="sxs-lookup"><span data-stu-id="dc723-188">The command uses a pipeline operator (|) to send the Storage module to the `Import-Module` cmdlet, which imports it into the local session.</span></span>

<span data-ttu-id="dc723-189">Det tredje kommandot kör `Get-Command` cmdleten i `Get-Disk` kommandot i modulen Storage.</span><span class="sxs-lookup"><span data-stu-id="dc723-189">The third command runs the `Get-Command` cmdlet on the `Get-Disk` command in the Storage module.</span></span>
<span data-ttu-id="dc723-190">När du importerar en CIM-modul till den lokala sessionen konverterar PowerShell de CDXLM-filer som representerar CIM-modulen till PowerShell-skript, som visas som funktioner i den lokala sessionen.</span><span class="sxs-lookup"><span data-stu-id="dc723-190">When you import a CIM module into the local session, PowerShell converts the CDXML files that represent the CIM module into PowerShell scripts, which appear as functions in the local session.</span></span>

<span data-ttu-id="dc723-191">Det fjärde kommandot kör `Get-Disk` kommandot.</span><span class="sxs-lookup"><span data-stu-id="dc723-191">The fourth command runs the `Get-Disk` command.</span></span> <span data-ttu-id="dc723-192">Även om kommandot skrivs i den lokala sessionen körs det implicit på den fjärrdator som den importerades från.</span><span class="sxs-lookup"><span data-stu-id="dc723-192">Although the command is typed in the local session, it runs implicitly on the remote computer from which it was imported.</span></span> <span data-ttu-id="dc723-193">Kommandot hämtar objekt från fjärrdatorn och returnerar dem till den lokala sessionen.</span><span class="sxs-lookup"><span data-stu-id="dc723-193">The command gets objects from the remote computer and returns them to the local session.</span></span>

## <span data-ttu-id="dc723-194">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="dc723-194">PARAMETERS</span></span>

### <span data-ttu-id="dc723-195">– Alla</span><span class="sxs-lookup"><span data-stu-id="dc723-195">-All</span></span>

<span data-ttu-id="dc723-196">Anger att denna cmdlet hämtar alla moduler i varje modul, inklusive kapslade moduler, manifest (. psd1)-filer, skriptfiler (. psm1) och binärfiler (. dll) för filer.</span><span class="sxs-lookup"><span data-stu-id="dc723-196">Indicates that this cmdlet gets all modules in each module folder, including nested modules, manifest (.psd1) files, script module (.psm1) files, and binary module (.dll) files.</span></span> <span data-ttu-id="dc723-197">Utan den här parametern `Get-Module` hämtas bara standardmodulen i varje modul-mapp.</span><span class="sxs-lookup"><span data-stu-id="dc723-197">Without this parameter, `Get-Module` gets only the default module in each module folder.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Loaded, Available
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dc723-198">-CimNamespace</span><span class="sxs-lookup"><span data-stu-id="dc723-198">-CimNamespace</span></span>

<span data-ttu-id="dc723-199">Anger namn området för en alternativ CIM-provider som exponerar CIM-moduler.</span><span class="sxs-lookup"><span data-stu-id="dc723-199">Specifies the namespace of an alternate CIM provider that exposes CIM modules.</span></span> <span data-ttu-id="dc723-200">Standardvärdet är namn området för WMI-providern för modul identifiering.</span><span class="sxs-lookup"><span data-stu-id="dc723-200">The default value is the namespace of the Module Discovery WMI provider.</span></span>

<span data-ttu-id="dc723-201">Använd den här parametern för att hämta CIM-moduler från datorer och enheter som inte kör Windows operativ system.</span><span class="sxs-lookup"><span data-stu-id="dc723-201">Use this parameter to get CIM modules from computers and devices that are not running the Windows operating system.</span></span>

<span data-ttu-id="dc723-202">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="dc723-202">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="dc723-203">-CimResourceUri</span><span class="sxs-lookup"><span data-stu-id="dc723-203">-CimResourceUri</span></span>

<span data-ttu-id="dc723-204">Anger en alternativ plats för CIM-moduler.</span><span class="sxs-lookup"><span data-stu-id="dc723-204">Specifies an alternate location for CIM modules.</span></span> <span data-ttu-id="dc723-205">Standardvärdet är resurs-URI för WMI-providern för module-identifiering på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="dc723-205">The default value is the resource URI of the Module Discovery WMI provider on the remote computer.</span></span>

<span data-ttu-id="dc723-206">Använd den här parametern för att hämta CIM-moduler från datorer och enheter som inte kör Windows operativ system.</span><span class="sxs-lookup"><span data-stu-id="dc723-206">Use this parameter to get CIM modules from computers and devices that are not running the Windows operating system.</span></span>

<span data-ttu-id="dc723-207">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="dc723-207">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="dc723-208">– CimSession</span><span class="sxs-lookup"><span data-stu-id="dc723-208">-CimSession</span></span>

<span data-ttu-id="dc723-209">Anger en CIM-session på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="dc723-209">Specifies a CIM session on the remote computer.</span></span> <span data-ttu-id="dc723-210">Ange en variabel som innehåller CIM-sessionen eller ett kommando som hämtar CIM-sessionen, till exempel ett [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) -kommando.</span><span class="sxs-lookup"><span data-stu-id="dc723-210">Enter a variable that contains the CIM session or a command that gets the CIM session, such as a [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) command.</span></span>

<span data-ttu-id="dc723-211">`Get-Module` använder CIM-sessionen för att hämta moduler från fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="dc723-211">`Get-Module` uses the CIM session connection to get modules from the remote computer.</span></span> <span data-ttu-id="dc723-212">När du importerar modulen med hjälp av `Import-Module` cmdleten och använder kommandona från den importerade modulen i den aktuella sessionen, körs de kommandon som faktiskt körs på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="dc723-212">When you import the module by using the `Import-Module` cmdlet and use the commands from the imported module in the current session, the commands actually run on the remote computer.</span></span>

<span data-ttu-id="dc723-213">Du kan använda den här parametern för att hämta moduler från datorer och enheter som inte kör Windows-operativsystemet och datorer som har PowerShell, men som inte har PowerShell-fjärrkommunikation aktive rad.</span><span class="sxs-lookup"><span data-stu-id="dc723-213">You can use this parameter to get modules from computers and devices that are not running the Windows operating system, and computers that have PowerShell, but do not have PowerShell remoting enabled.</span></span>

<span data-ttu-id="dc723-214">Parametern **CimSession** hämtar alla moduler i **CimSession**.</span><span class="sxs-lookup"><span data-stu-id="dc723-214">The **CimSession** parameter gets all modules in the **CIMSession**.</span></span> <span data-ttu-id="dc723-215">Du kan dock endast importera CIM-baserade och CDXLM-baserade moduler (cmdlet definition XML).</span><span class="sxs-lookup"><span data-stu-id="dc723-215">However, you can import only CIM-based and Cmdlet Definition XML (CDXML)-based modules.</span></span>

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

### <span data-ttu-id="dc723-216">-FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="dc723-216">-FullyQualifiedName</span></span>

<span data-ttu-id="dc723-217">Anger moduler med namn som anges i form av **ModuleSpecification** -objekt.</span><span class="sxs-lookup"><span data-stu-id="dc723-217">Specifies modules with names that are specified in the form of **ModuleSpecification** objects.</span></span> <span data-ttu-id="dc723-218">Se avsnittet anmärkningar i [ModuleSpecification-konstruktorn (hash)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span><span class="sxs-lookup"><span data-stu-id="dc723-218">See the Remarks section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>

<span data-ttu-id="dc723-219">**FullyQualifiedModule** -parametern accepterar till exempel ett modulnamn som anges i något av följande format:</span><span class="sxs-lookup"><span data-stu-id="dc723-219">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in either of these formats:</span></span>

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

<span data-ttu-id="dc723-220">**Modulnamn** och **ModuleVersion** krävs, men **GUID** är valfritt.</span><span class="sxs-lookup"><span data-stu-id="dc723-220">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span> <span data-ttu-id="dc723-221">Det går inte att ange parametern **FullyQualifiedModule** i samma kommando som en **modul** -parameter.</span><span class="sxs-lookup"><span data-stu-id="dc723-221">You cannot specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span> <span data-ttu-id="dc723-222">de två parametrarna kan inte anges samtidigt.</span><span class="sxs-lookup"><span data-stu-id="dc723-222">the two parameters are mutually exclusive.</span></span>

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

### <span data-ttu-id="dc723-223">– ListAvailable</span><span class="sxs-lookup"><span data-stu-id="dc723-223">-ListAvailable</span></span>

<span data-ttu-id="dc723-224">Anger att denna cmdlet hämtar alla installerade moduler.</span><span class="sxs-lookup"><span data-stu-id="dc723-224">Indicates that this cmdlet gets all installed modules.</span></span> <span data-ttu-id="dc723-225">`Get-Module` hämtar moduler i sökvägar som anges i miljövariabeln **PSModulePath** .</span><span class="sxs-lookup"><span data-stu-id="dc723-225">`Get-Module` gets modules in paths listed in the **PSModulePath** environment variable.</span></span> <span data-ttu-id="dc723-226">Utan den här parametern `Get-Module` hämtas bara de moduler som båda anges i miljövariabeln **PSModulePath** och som läses in i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="dc723-226">Without this parameter, `Get-Module` gets only the modules that are both listed in the **PSModulePath** environment variable, and that are loaded in the current session.</span></span> <span data-ttu-id="dc723-227">**ListAvailable** returnerar inte information om moduler som inte finns i miljövariabeln **PSModulePath** , även om modulerna har lästs in i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="dc723-227">**ListAvailable** does not return information about modules that are not found in the **PSModulePath** environment variable, even if those modules are loaded in the current session.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Available, PsSession, CimSession
Aliases:

Required: True (Available), False (PsSession, CimSession)
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dc723-228">-Name</span><span class="sxs-lookup"><span data-stu-id="dc723-228">-Name</span></span>

<span data-ttu-id="dc723-229">Anger namn eller namn mönster för moduler som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="dc723-229">Specifies names or name patterns of modules that this cmdlet gets.</span></span> <span data-ttu-id="dc723-230">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="dc723-230">Wildcard characters are permitted.</span></span> <span data-ttu-id="dc723-231">Du kan också skicka namnen till `Get-Module` .</span><span class="sxs-lookup"><span data-stu-id="dc723-231">You can also pipe the names to `Get-Module`.</span></span> <span data-ttu-id="dc723-232">Det går inte att ange parametern **FullyQualifiedName** i samma kommando som en **namn** parameter.</span><span class="sxs-lookup"><span data-stu-id="dc723-232">You cannot specify the **FullyQualifiedName** parameter in the same command as a **Name** parameter.</span></span>

<span data-ttu-id="dc723-233">**Namnet** kan inte acceptera ett modul-GUID som värde.</span><span class="sxs-lookup"><span data-stu-id="dc723-233">**Name** cannot accept a module GUID as a value.</span></span>
<span data-ttu-id="dc723-234">Om du vill returnera moduler genom att ange ett GUID använder du **FullyQualifiedName** i stället.</span><span class="sxs-lookup"><span data-stu-id="dc723-234">To return modules by specifying a GUID, use **FullyQualifiedName** instead.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="dc723-235">– PSEdition</span><span class="sxs-lookup"><span data-stu-id="dc723-235">-PSEdition</span></span>

<span data-ttu-id="dc723-236">Hämtar de moduler som stöder den angivna versionen av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dc723-236">Gets the modules that support specified edition of PowerShell.</span></span>

<span data-ttu-id="dc723-237">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="dc723-237">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="dc723-238">Skrivbord</span><span class="sxs-lookup"><span data-stu-id="dc723-238">Desktop</span></span>
- <span data-ttu-id="dc723-239">Kärna</span><span class="sxs-lookup"><span data-stu-id="dc723-239">Core</span></span>

<span data-ttu-id="dc723-240">Get-Module cmdleten kontrollerar egenskapen **CompatiblePSEditions** för **PSModuleInfo** -objektet för det angivna värdet och returnerar bara de moduler som har angetts.</span><span class="sxs-lookup"><span data-stu-id="dc723-240">The Get-Module cmdlet checks **CompatiblePSEditions** property of **PSModuleInfo** object for the specified value and returns only those modules that have it set.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="dc723-241">**Desktop Edition:** bygger på .NET Framework och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på fullständiga utgåvor av Windows, till exempel Server Core och Windows Desktop.</span><span class="sxs-lookup"><span data-stu-id="dc723-241">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
> - <span data-ttu-id="dc723-242">**Core Edition:** bygger på .NET Core och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på begränsade utgåvor av Windows som Nano Server och Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="dc723-242">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

```yaml
Type: System.String
Parameter Sets: PsSession, Available
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dc723-243">– PSSession</span><span class="sxs-lookup"><span data-stu-id="dc723-243">-PSSession</span></span>

<span data-ttu-id="dc723-244">Hämtar modulerna i den angivna användar hanterade PowerShell-sessionen (**PSSession**).</span><span class="sxs-lookup"><span data-stu-id="dc723-244">Gets the modules in the specified user-managed PowerShell session (**PSSession**).</span></span> <span data-ttu-id="dc723-245">Ange en variabel som innehåller sessionen, ett kommando som hämtar sessionen, till exempel ett `Get-PSSession` kommando eller ett kommando som skapar sessionen, till exempel ett `New-PSSession` kommando.</span><span class="sxs-lookup"><span data-stu-id="dc723-245">Enter a variable that contains the session, a command that gets the session, such as a `Get-PSSession` command, or a command that creates the session, such as a `New-PSSession` command.</span></span>

<span data-ttu-id="dc723-246">När sessionen är ansluten till en fjärrdator måste du ange parametern **ListAvailable** .</span><span class="sxs-lookup"><span data-stu-id="dc723-246">When the session is connected to a remote computer, you must specify the **ListAvailable** parameter.</span></span>

<span data-ttu-id="dc723-247">Ett `Get-Module` kommando som använder parametern **PSSession** är detsamma som att använda `Invoke-Command` cmdleten för att köra ett `Get-Module -ListAvailable` kommando i en **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="dc723-247">A `Get-Module` command that uses the **PSSession** parameter is equivalent to using the `Invoke-Command` cmdlet to run a `Get-Module -ListAvailable` command in a **PSSession**.</span></span>

<span data-ttu-id="dc723-248">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="dc723-248">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession
Parameter Sets: PsSession
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dc723-249">-Uppdatera</span><span class="sxs-lookup"><span data-stu-id="dc723-249">-Refresh</span></span>

<span data-ttu-id="dc723-250">Anger att denna cmdlet uppdaterar cacheminnet för installerade kommandon.</span><span class="sxs-lookup"><span data-stu-id="dc723-250">Indicates that this cmdlet refreshes the cache of installed commands.</span></span> <span data-ttu-id="dc723-251">Kommandots cacheminne skapas när sessionen startar.</span><span class="sxs-lookup"><span data-stu-id="dc723-251">The command cache is created when the session starts.</span></span> <span data-ttu-id="dc723-252">Den gör det möjligt för `Get-Command` cmdleten att hämta kommandon från moduler som inte importeras till sessionen.</span><span class="sxs-lookup"><span data-stu-id="dc723-252">It enables the `Get-Command` cmdlet to get commands from modules that are not imported into the session.</span></span>

<span data-ttu-id="dc723-253">Den här parametern är utformad för utvecklings-och testnings scenarier där innehållet i moduler har ändrats sedan sessionen startades.</span><span class="sxs-lookup"><span data-stu-id="dc723-253">This parameter is designed for development and testing scenarios in which the contents of modules have changed since the session started.</span></span>

<span data-ttu-id="dc723-254">När du anger parametern **Refresh** i ett kommando måste du ange **ListAvailable**.</span><span class="sxs-lookup"><span data-stu-id="dc723-254">When you specify the **Refresh** parameter in a command, you must specify **ListAvailable**.</span></span>

<span data-ttu-id="dc723-255">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="dc723-255">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Available, PsSession, CimSession
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dc723-256">-SkipEditionCheck</span><span class="sxs-lookup"><span data-stu-id="dc723-256">-SkipEditionCheck</span></span>

<span data-ttu-id="dc723-257">Hoppar över kontrollen av `CompatiblePSEditions` fältet.</span><span class="sxs-lookup"><span data-stu-id="dc723-257">Skips the check of the `CompatiblePSEditions` field.</span></span>

<span data-ttu-id="dc723-258">Som standard kommer Get-Module att utelämna moduler i `%windir%\System32\WindowsPowerShell\v1.0\Modules` katalogen som inte anges `Core` i `CompatiblePSEditions` fältet.</span><span class="sxs-lookup"><span data-stu-id="dc723-258">By default, Get-Module will omit modules in the `%windir%\System32\WindowsPowerShell\v1.0\Modules` directory that do not specify `Core` in the `CompatiblePSEditions` field.</span></span> <span data-ttu-id="dc723-259">När den här växeln har angetts kommer moduler utan att `Core` inkluderas, så att moduler under Windows PowerShell-modulens sökväg som är inkompatibla med PowerShell-kärnan returneras.</span><span class="sxs-lookup"><span data-stu-id="dc723-259">When this switch is set, modules without `Core` will be included, so that modules under the Windows PowerShell module path that are incompatible with PowerShell Core will be returned.</span></span>

<span data-ttu-id="dc723-260">I macOS och Linux gör den här parametern ingenting.</span><span class="sxs-lookup"><span data-stu-id="dc723-260">On macOS and Linux, this parameter does nothing.</span></span>

<span data-ttu-id="dc723-261">Se [about_PowerShell_Editions](About/about_PowerShell_Editions.md) för mer information.</span><span class="sxs-lookup"><span data-stu-id="dc723-261">See [about_PowerShell_Editions](About/about_PowerShell_Editions.md) for more information.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Available, PsSession, CimSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="dc723-262">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="dc723-262">CommonParameters</span></span>

<span data-ttu-id="dc723-263">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="dc723-263">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="dc723-264">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="dc723-264">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="dc723-265">INDATA</span><span class="sxs-lookup"><span data-stu-id="dc723-265">INPUTS</span></span>

### <span data-ttu-id="dc723-266">System. String</span><span class="sxs-lookup"><span data-stu-id="dc723-266">System.String</span></span>

<span data-ttu-id="dc723-267">Du kan skicka pipe-modulnamn till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dc723-267">You can pipe module names to this cmdlet.</span></span>

## <span data-ttu-id="dc723-268">UTDATA</span><span class="sxs-lookup"><span data-stu-id="dc723-268">OUTPUTS</span></span>

### <span data-ttu-id="dc723-269">System. Management. Automation. PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="dc723-269">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="dc723-270">Denna cmdlet returnerar objekt som representerar moduler.</span><span class="sxs-lookup"><span data-stu-id="dc723-270">This cmdlet returns objects that represent modules.</span></span>
<span data-ttu-id="dc723-271">När du anger parametern **ListAvailable** `Get-Module` returnerar ett **ModuleInfoGrouping** -objekt, som är en typ av **PSModuleInfo** -objekt som har samma egenskaper och metoder.</span><span class="sxs-lookup"><span data-stu-id="dc723-271">When you specify the **ListAvailable** parameter, `Get-Module` returns a **ModuleInfoGrouping** object, which is a type of **PSModuleInfo** object that has the same properties and methods.</span></span>

## <span data-ttu-id="dc723-272">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="dc723-272">NOTES</span></span>

- <span data-ttu-id="dc723-273">Från och med Windows PowerShell 3,0 paketeras kärn kommandona som ingår i PowerShell i moduler.</span><span class="sxs-lookup"><span data-stu-id="dc723-273">Beginning in Windows PowerShell 3.0, the core commands that are included in PowerShell are packaged in modules.</span></span> <span data-ttu-id="dc723-274">Undantaget är **Microsoft. PowerShell. Core**, som är en snapin-modul (**PSSnapin**).</span><span class="sxs-lookup"><span data-stu-id="dc723-274">The exception is **Microsoft.PowerShell.Core**, which is a snap-in (**PSSnapin**).</span></span> <span data-ttu-id="dc723-275">Som standard läggs bara snapin-modulen **Microsoft. PowerShell. Core** till i sessionen.</span><span class="sxs-lookup"><span data-stu-id="dc723-275">By default, only the **Microsoft.PowerShell.Core** snap-in is added to the session.</span></span> <span data-ttu-id="dc723-276">Moduler importeras automatiskt vid första användningen och du kan använda `Import-Module` cmdleten för att importera dem.</span><span class="sxs-lookup"><span data-stu-id="dc723-276">Modules are imported automatically on first use and you can use the `Import-Module` cmdlet to import them.</span></span>

- <span data-ttu-id="dc723-277">I Windows PowerShell 2,0 och i värd program som skapar äldre sessioner i senare versioner av PowerShell, paketeras huvud kommandona i snapin-moduler (**PSSnapins**).</span><span class="sxs-lookup"><span data-stu-id="dc723-277">In Windows PowerShell 2.0, and in host programs that create older-style sessions in later versions of PowerShell, the core commands are packaged in snap-ins (**PSSnapins**).</span></span> <span data-ttu-id="dc723-278">Undantaget är **Microsoft. PowerShell. Core**, som alltid är en snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="dc723-278">The exception is **Microsoft.PowerShell.Core**, which is always a snap-in.</span></span> <span data-ttu-id="dc723-279">Fjärrsessioner, till exempel de som startas av `New-PSSession` cmdleten, är äldre sessioner som inkluderar grundläggande snapin-moduler.</span><span class="sxs-lookup"><span data-stu-id="dc723-279">Also, remote sessions, such as those started by the `New-PSSession` cmdlet, are older-style sessions that include core snap-ins.</span></span>

  <span data-ttu-id="dc723-280">Information om **CreateDefault2** -metoden som skapar nyare sessioner med Core-moduler finns i CreateDefault2- [metoden](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2).</span><span class="sxs-lookup"><span data-stu-id="dc723-280">For information about the **CreateDefault2** method that creates newer-style sessions with core modules, see [CreateDefault2 Method](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2).</span></span>

- <span data-ttu-id="dc723-281">`Get-Module` hämtar endast moduler i platser som lagras i värdet för **PSModulePath** -miljövariabeln ($env:P smodulepath).</span><span class="sxs-lookup"><span data-stu-id="dc723-281">`Get-Module` only gets modules in locations that are stored in the value of the **PSModulePath** environment variable ($env:PSModulePath).</span></span> <span data-ttu-id="dc723-282">`Import-Module`Cmdleten kan importera moduler på andra platser, men du kan inte använda `Get-Module` cmdleten för att hämta dem.</span><span class="sxs-lookup"><span data-stu-id="dc723-282">The `Import-Module` cmdlet can import modules in other locations, but you cannot use the `Get-Module` cmdlet to get them.</span></span>

- <span data-ttu-id="dc723-283">Från och med PowerShell 3,0 har nya egenskaper också lagts till i objektet som returnerar och `Get-Module` gör det lättare att lära sig om moduler, även innan de importeras.</span><span class="sxs-lookup"><span data-stu-id="dc723-283">Also, starting in PowerShell 3.0, new properties have been added to the object that `Get-Module` returns that make it easier to learn about modules even before they are imported.</span></span> <span data-ttu-id="dc723-284">Alla egenskaper fylls i före importen.</span><span class="sxs-lookup"><span data-stu-id="dc723-284">All properties are populated before importing.</span></span> <span data-ttu-id="dc723-285">Dessa inkluderar **ExportedCommands**-, **ExportedCmdlets** -och **ExportedFunctions** -egenskaperna som visar de kommandon som modulen exporterar.</span><span class="sxs-lookup"><span data-stu-id="dc723-285">These include the **ExportedCommands**, **ExportedCmdlets** and **ExportedFunctions** properties that list the commands that the module exports.</span></span>

- <span data-ttu-id="dc723-286">Parametern **ListAvailable** hämtar endast välformulerade moduler, det vill säga mappar som innehåller minst en fil vars bas namn är samma som namnet på mappen module.</span><span class="sxs-lookup"><span data-stu-id="dc723-286">The **ListAvailable** parameter gets only well-formed modules, that is, folders that contain at least one file whose base name is the same as the name of the module folder.</span></span> <span data-ttu-id="dc723-287">Bas namnet är namnet utan fil namns tillägget.</span><span class="sxs-lookup"><span data-stu-id="dc723-287">The base name is the name without the file name extension.</span></span> <span data-ttu-id="dc723-288">Mappar som innehåller filer som har olika namn anses vara behållare, men inte moduler.</span><span class="sxs-lookup"><span data-stu-id="dc723-288">Folders that contain files that have different names are considered to be containers, but not modules.</span></span>

  <span data-ttu-id="dc723-289">Om du vill hämta moduler som har implementerats som DLL-filer, men som inte är omslutna i en modul, anger du både **ListAvailable** och **alla** parametrar.</span><span class="sxs-lookup"><span data-stu-id="dc723-289">To get modules that are implemented as DLL files, but are not enclosed in a module folder, specify both the **ListAvailable** and **All** parameters.</span></span>

- <span data-ttu-id="dc723-290">Om du vill använda funktionen CIM-sessionen måste fjärrdatorn ha WS-Management fjärr anslutning och Windows Management Instrumentation (WMI), som är Microsofts implementering av Common Information Model (CIM) standard.</span><span class="sxs-lookup"><span data-stu-id="dc723-290">To use the CIM session feature, the remote computer must have WS-Management remoting and Windows Management Instrumentation (WMI), which is the Microsoft implementation of the Common Information Model (CIM) standard.</span></span> <span data-ttu-id="dc723-291">Datorn måste också ha WMI-providern för modul identifiering eller en alternativ WMI-provider som har samma grundläggande funktioner.</span><span class="sxs-lookup"><span data-stu-id="dc723-291">The computer must also have the Module Discovery WMI provider or an alternate WMI provider that has the same basic features.</span></span>

  <span data-ttu-id="dc723-292">Du kan använda funktionen för CIM-sessionen på datorer som inte kör Windows-operativsystemet och på Windows-datorer med PowerShell, men inte har PowerShell-fjärrkommunikation aktive rad.</span><span class="sxs-lookup"><span data-stu-id="dc723-292">You can use the CIM session feature on computers that are not running the Windows operating system and on Windows computers that have PowerShell, but do not have PowerShell remoting enabled.</span></span>

  <span data-ttu-id="dc723-293">Du kan också använda CIM-parametrarna för att hämta CIM-moduler från datorer där PowerShell-fjärrkommunikation är aktiverat.</span><span class="sxs-lookup"><span data-stu-id="dc723-293">You can also use the CIM parameters to get CIM modules from computers that have PowerShell remoting enabled.</span></span> <span data-ttu-id="dc723-294">Detta inkluderar den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="dc723-294">This includes the local computer.</span></span> <span data-ttu-id="dc723-295">När du skapar en CIM-session på den lokala datorn använder PowerShell DCOM, i stället för WMI, för att skapa sessionen.</span><span class="sxs-lookup"><span data-stu-id="dc723-295">When you create a CIM session on the local computer, PowerShell uses DCOM, instead of WMI, to create the session.</span></span>

## <span data-ttu-id="dc723-296">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="dc723-296">RELATED LINKS</span></span>

[<span data-ttu-id="dc723-297">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="dc723-297">Get-CimSession</span></span>](../CimCmdlets/Get-CimSession.md)

[<span data-ttu-id="dc723-298">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="dc723-298">New-CimSession</span></span>](../CimCmdlets/New-CimSession.md)

[<span data-ttu-id="dc723-299">about_Modules</span><span class="sxs-lookup"><span data-stu-id="dc723-299">about_Modules</span></span>](About/about_Modules.md)

[<span data-ttu-id="dc723-300">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="dc723-300">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="dc723-301">Importera-modul</span><span class="sxs-lookup"><span data-stu-id="dc723-301">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="dc723-302">Importera – PSSession</span><span class="sxs-lookup"><span data-stu-id="dc723-302">Import-PSSession</span></span>](../Microsoft.PowerShell.Utility/Import-PSSession.md)

[<span data-ttu-id="dc723-303">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="dc723-303">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="dc723-304">Ta bort modul</span><span class="sxs-lookup"><span data-stu-id="dc723-304">Remove-Module</span></span>](Remove-Module.md)

[<span data-ttu-id="dc723-305">about_PowerShell_Editions</span><span class="sxs-lookup"><span data-stu-id="dc723-305">about_PowerShell_Editions</span></span>](About/about_PowerShell_Editions.md)
