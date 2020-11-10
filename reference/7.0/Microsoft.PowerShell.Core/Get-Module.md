---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-module?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Module
ms.openlocfilehash: cd04565f427cdf8aebf585d978e0e8d2a5b28c09
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94391229"
---
# <span data-ttu-id="965c8-103">Get-Module</span><span class="sxs-lookup"><span data-stu-id="965c8-103">Get-Module</span></span>

## <span data-ttu-id="965c8-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="965c8-104">SYNOPSIS</span></span>
<span data-ttu-id="965c8-105">Hämtar de moduler som har importer ATS eller som kan importeras till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="965c8-105">Gets the modules that have been imported or that can be imported into the current session.</span></span>

## <span data-ttu-id="965c8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="965c8-106">SYNTAX</span></span>

### <span data-ttu-id="965c8-107">Läst in (standard)</span><span class="sxs-lookup"><span data-stu-id="965c8-107">Loaded (Default)</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-All] [<CommonParameters>]
```

### <span data-ttu-id="965c8-108">Tillgänglig</span><span class="sxs-lookup"><span data-stu-id="965c8-108">Available</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-All] [-ListAvailable]
 [-PSEdition <String>] [-SkipEditionCheck] [-Refresh] [<CommonParameters>]
```

### <span data-ttu-id="965c8-109">PsSession</span><span class="sxs-lookup"><span data-stu-id="965c8-109">PsSession</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-ListAvailable]
 [-PSEdition <String>] [-SkipEditionCheck] [-Refresh] -PSSession <PSSession> [<CommonParameters>]
```

### <span data-ttu-id="965c8-110">CimSession</span><span class="sxs-lookup"><span data-stu-id="965c8-110">CimSession</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-ListAvailable]
 [-SkipEditionCheck] [-Refresh] -CimSession <CimSession> [-CimResourceUri <Uri>] [-CimNamespace <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="965c8-111">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="965c8-111">DESCRIPTION</span></span>

<span data-ttu-id="965c8-112">Cmdlet: en `Get-Module` hämtar PowerShell-modulerna som har importer ATS, eller som kan importeras, till en PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="965c8-112">The `Get-Module` cmdlet gets the PowerShell modules that have been imported, or that can be imported, into a PowerShell session.</span></span> <span data-ttu-id="965c8-113">Module-objektet som `Get-Module` returnerar innehåller värdefull information om modulen.</span><span class="sxs-lookup"><span data-stu-id="965c8-113">The module object that `Get-Module` returns contains valuable information about the module.</span></span> <span data-ttu-id="965c8-114">Du kan också skicka modulens objekt till andra cmdletar, till exempel- `Import-Module` och- `Remove-Module` cmdlet: ar.</span><span class="sxs-lookup"><span data-stu-id="965c8-114">You can also pipe the module objects to other cmdlets, such as the `Import-Module` and `Remove-Module` cmdlets.</span></span>

<span data-ttu-id="965c8-115">Utan parametrar, `Get-Module` hämtar moduler som har importer ATS till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="965c8-115">Without parameters, `Get-Module` gets modules that have been imported into the current session.</span></span> <span data-ttu-id="965c8-116">Om du vill hämta alla installerade moduler anger du parametern **ListAvailable** .</span><span class="sxs-lookup"><span data-stu-id="965c8-116">To get all installed modules, specify the **ListAvailable** parameter.</span></span>

<span data-ttu-id="965c8-117">`Get-Module` hämtar moduler, men importerar dem inte.</span><span class="sxs-lookup"><span data-stu-id="965c8-117">`Get-Module` gets modules, but it does not import them.</span></span> <span data-ttu-id="965c8-118">Från och med Windows PowerShell 3,0 importeras moduler automatiskt när du använder ett kommando i modulen, men ett `Get-Module` kommando utlöser inte en automatisk import.</span><span class="sxs-lookup"><span data-stu-id="965c8-118">Starting in Windows PowerShell 3.0, modules are automatically imported when you use a command in the module, but a `Get-Module` command does not trigger an automatic import.</span></span> <span data-ttu-id="965c8-119">Du kan också importera modulerna till-sessionen med hjälp av `Import-Module` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="965c8-119">You can also import the modules into your session by using the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="965c8-120">Från och med Windows PowerShell 3,0 kan du hämta och importera moduler från fjärrsessioner till den lokala sessionen.</span><span class="sxs-lookup"><span data-stu-id="965c8-120">Starting in Windows PowerShell 3.0, you can get and then, import modules from remote sessions into the local session.</span></span> <span data-ttu-id="965c8-121">Den här strategin använder funktionen implicit fjärr kommunikation i PowerShell och motsvarar att använda `Import-PSSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="965c8-121">This strategy uses the Implicit Remoting feature of PowerShell and is equivalent to using the `Import-PSSession` cmdlet.</span></span> <span data-ttu-id="965c8-122">När du använder kommandon i moduler som importer ATS från en annan session körs kommandona implicit i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="965c8-122">When you use commands in modules imported from another session, the commands run implicitly in the remote session.</span></span> <span data-ttu-id="965c8-123">Med den här funktionen kan du hantera fjärrdatorn från den lokala sessionen.</span><span class="sxs-lookup"><span data-stu-id="965c8-123">This feature lets you manage the remote computer from the local session.</span></span>

<span data-ttu-id="965c8-124">Från och med Windows PowerShell 3,0 kan du också använda `Get-Module` och `Import-Module` för att hämta och importera common information Model-moduler (CIM), där cmdletarna definieras i CMDLET definition XML-filer (cdxlm).</span><span class="sxs-lookup"><span data-stu-id="965c8-124">Also, starting in Windows PowerShell 3.0, you can use `Get-Module` and `Import-Module` to get and import Common Information Model (CIM) modules, in which the cmdlets are defined in Cmdlet Definition XML (CDXML) files.</span></span> <span data-ttu-id="965c8-125">Med den här funktionen kan du använda cmdletar som implementeras i icke-hanterade kod sammansättningar, t. ex. sådana som skrivits i C++.</span><span class="sxs-lookup"><span data-stu-id="965c8-125">This feature lets you use cmdlets that are implemented in non-managed code assemblies, such as those written in C++.</span></span>

<span data-ttu-id="965c8-126">Med de här nya funktionerna `Get-Module` blir-och- `Import-Module` cmdletarna primära verktyg för att hantera heterogena företag som innehåller datorer som kör Windows-operativsystemet och datorer som kör andra operativ system.</span><span class="sxs-lookup"><span data-stu-id="965c8-126">With these new features, the `Get-Module` and `Import-Module` cmdlets become primary tools for managing heterogeneous enterprises that include computers that run the Windows operating system and computers that run other operating systems.</span></span>

<span data-ttu-id="965c8-127">För att hantera fjärrdatorer som kör Windows-operativsystemet med PowerShell-och PowerShell-fjärrkommunikation aktive rad, skapar du en **PSSession** på fjärrdatorn och använder sedan **PSSession** -parametern för `Get-Module` för att hämta PowerShell-modulerna i **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="965c8-127">To manage remote computers that run the Windows operating system that have PowerShell and PowerShell remoting enabled, create a **PSSession** on the remote computer and then use the **PSSession** parameter of `Get-Module` to get the PowerShell modules in the **PSSession**.</span></span> <span data-ttu-id="965c8-128">När du importerar modulerna och sedan använder de importerade kommandona i den aktuella sessionen, körs kommandona implicit i **PSSession** på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="965c8-128">When you import the modules, and then use the imported commands in the current session, the commands run implicitly in the **PSSession** on the remote computer.</span></span> <span data-ttu-id="965c8-129">Du kan använda den här strategin för att hantera fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="965c8-129">You can use this strategy to manage the remote computer.</span></span>

<span data-ttu-id="965c8-130">Du kan använda en liknande strategi för att hantera datorer som inte har PowerShell-fjärrkommunikation aktive rad.</span><span class="sxs-lookup"><span data-stu-id="965c8-130">You can use a similar strategy to manage computers that do not have PowerShell remoting enabled.</span></span>
<span data-ttu-id="965c8-131">Detta inkluderar datorer som inte kör Windows-operativsystemet och datorer som har PowerShell men inte har PowerShell-fjärrkommunikation aktive rad.</span><span class="sxs-lookup"><span data-stu-id="965c8-131">These include computers that are not running the Windows operating system, and computers that have PowerShell but do not have PowerShell remoting enabled.</span></span>

<span data-ttu-id="965c8-132">Börja med att skapa en CIM-session på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="965c8-132">Start by creating a CIM session on the remote computer.</span></span> <span data-ttu-id="965c8-133">En CIM-session är en anslutning till Windows Management Instrumentation (WMI) på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="965c8-133">A CIM session is a connection to Windows Management Instrumentation (WMI) on the remote computer.</span></span> <span data-ttu-id="965c8-134">Använd sedan **CIMSession** -parametern för `Get-Module` för att hämta CIM-moduler från CIM-sessionen.</span><span class="sxs-lookup"><span data-stu-id="965c8-134">Then use the **CIMSession** parameter of `Get-Module` to get CIM modules from the CIM session.</span></span> <span data-ttu-id="965c8-135">När du importerar en CIM-modul med hjälp av `Import-Module` cmdleten och sedan kör de importerade kommandona, körs kommandona implicit på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="965c8-135">When you import a CIM module by using the `Import-Module` cmdlet and then run the imported commands, the commands run implicitly on the remote computer.</span></span> <span data-ttu-id="965c8-136">Du kan använda den här WMI-och CIM-strategin för att hantera fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="965c8-136">You can use this WMI and CIM strategy to manage the remote computer.</span></span>

## <span data-ttu-id="965c8-137">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="965c8-137">EXAMPLES</span></span>

### <span data-ttu-id="965c8-138">Exempel 1: Hämta moduler som importer ATS till den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="965c8-138">Example 1: Get modules imported into the current session</span></span>

```powershell
Get-Module
```

<span data-ttu-id="965c8-139">Det här kommandot hämtar moduler som har importer ATS till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="965c8-139">This command gets modules that have been imported into the current session.</span></span>

### <span data-ttu-id="965c8-140">Exempel 2: Hämta installerade moduler och tillgängliga moduler</span><span class="sxs-lookup"><span data-stu-id="965c8-140">Example 2: Get installed modules and available modules</span></span>

```powershell
Get-Module -ListAvailable
```

<span data-ttu-id="965c8-141">Detta kommando hämtar de moduler som är installerade på datorn och som kan importeras till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="965c8-141">This command gets the modules that are installed on the computer and can be imported into the current session.</span></span>

<span data-ttu-id="965c8-142">`Get-Module` söker efter tillgängliga moduler i sökvägen som anges av variabeln **$env:P smodulepath** -miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="965c8-142">`Get-Module` looks for available modules in the path specified by the **$env:PSModulePath** environment variable.</span></span> <span data-ttu-id="965c8-143">Mer information om **PSModulePath** finns i [about_Modules](About/about_Modules.md) och [about_Environment_Variables](About/about_Environment_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="965c8-143">For more information about **PSModulePath** , see [about_Modules](About/about_Modules.md) and [about_Environment_Variables](About/about_Environment_Variables.md).</span></span>

### <span data-ttu-id="965c8-144">Exempel 3: Hämta alla exporterade filer</span><span class="sxs-lookup"><span data-stu-id="965c8-144">Example 3: Get all exported files</span></span>

```powershell
Get-Module -ListAvailable -All
```

<span data-ttu-id="965c8-145">Det här kommandot hämtar alla exporterade filer för alla tillgängliga moduler.</span><span class="sxs-lookup"><span data-stu-id="965c8-145">This command gets all of the exported files for all available modules.</span></span>

### <span data-ttu-id="965c8-146">Exempel 4: Hämta en modul med dess fullständigt kvalificerade namn</span><span class="sxs-lookup"><span data-stu-id="965c8-146">Example 4: Get a module by its fully qualified name</span></span>

```powershell
$FullyQualifedName = @{ModuleName="Microsoft.PowerShell.Management";ModuleVersion="3.1.0.0"}
Get-Module -FullyQualifiedName $FullyQualifedName | Format-Table -Property Name,Version
```

```Output
Name                             Version
----                             -------
Microsoft.PowerShell.Management  3.1.0.0
```

<span data-ttu-id="965c8-147">Detta kommando hämtar modulen **Microsoft. PowerShell. Management** genom att ange det fullständigt kvalificerade namnet på modulen med hjälp av parametern **FullyQualifiedName** .</span><span class="sxs-lookup"><span data-stu-id="965c8-147">This command gets the **Microsoft.PowerShell.Management** module by specifying the fully qualified name of the module by using the **FullyQualifiedName** parameter.</span></span> <span data-ttu-id="965c8-148">Kommandot rör sedan resultatet i `Format-Table` cmdleten för att formatera resultatet som en tabell med **namn** och **version** som kolumn rubriker.</span><span class="sxs-lookup"><span data-stu-id="965c8-148">The command then pipes the results into the `Format-Table` cmdlet to format the results as a table with **Name** and **Version** as the column headings.</span></span>

### <span data-ttu-id="965c8-149">Exempel 5: Hämta egenskaper för en modul</span><span class="sxs-lookup"><span data-stu-id="965c8-149">Example 5: Get properties of a module</span></span>

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

<span data-ttu-id="965c8-150">Det här kommandot hämtar egenskaperna för det **PSModuleInfo** -objekt som `Get-Module` returneras.</span><span class="sxs-lookup"><span data-stu-id="965c8-150">This command gets the properties of the **PSModuleInfo** object that `Get-Module` returns.</span></span> <span data-ttu-id="965c8-151">Det finns ett objekt för varje modul-fil.</span><span class="sxs-lookup"><span data-stu-id="965c8-151">There is one object for each module file.</span></span>

<span data-ttu-id="965c8-152">Du kan använda egenskaperna för att formatera och filtrera modulens objekt.</span><span class="sxs-lookup"><span data-stu-id="965c8-152">You can use the properties to format and filter the module objects.</span></span> <span data-ttu-id="965c8-153">Mer information om egenskaperna finns i PSModuleInfo- [Egenskaper](/dotnet/api/system.management.automation.psmoduleinfo).</span><span class="sxs-lookup"><span data-stu-id="965c8-153">For more information about the properties, see [PSModuleInfo Properties](/dotnet/api/system.management.automation.psmoduleinfo).</span></span>

<span data-ttu-id="965c8-154">Utdata innehåller de nya egenskaperna, till exempel **författare** och **företags namn** , som introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="965c8-154">The output includes the new properties, such as **Author** and **CompanyName** , that were introduced in Windows PowerShell 3.0.</span></span>

### <span data-ttu-id="965c8-155">Exempel 6: gruppera alla moduler efter namn</span><span class="sxs-lookup"><span data-stu-id="965c8-155">Example 6: Group all modules by name</span></span>

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

<span data-ttu-id="965c8-156">Det här kommandot hämtar alla modulblad, både importerade och tillgängliga, och grupperar dem efter modulnamn.</span><span class="sxs-lookup"><span data-stu-id="965c8-156">This command gets all module files, both imported and available, and then groups them by module name.</span></span> <span data-ttu-id="965c8-157">På så sätt kan du se de module-filer som varje skript exporterar.</span><span class="sxs-lookup"><span data-stu-id="965c8-157">This lets you see the module files that each script is exporting.</span></span>

### <span data-ttu-id="965c8-158">Exempel 7: Visa innehållet i ett modul-manifest</span><span class="sxs-lookup"><span data-stu-id="965c8-158">Example 7: Display the contents of a module manifest</span></span>

<span data-ttu-id="965c8-159">Dessa kommandon visar innehållet i modulens manifest för Windows PowerShell-modulen **BitsTransfer** .</span><span class="sxs-lookup"><span data-stu-id="965c8-159">These commands display the contents of the module manifest for the Windows PowerShell **BitsTransfer** module.</span></span>

<span data-ttu-id="965c8-160">Moduler måste inte ha MANIFEST-filer.</span><span class="sxs-lookup"><span data-stu-id="965c8-160">Modules are not required to have manifest files.</span></span> <span data-ttu-id="965c8-161">När de har en manifest fil, krävs manifest filen bara för att inkludera ett versions nummer.</span><span class="sxs-lookup"><span data-stu-id="965c8-161">When they do have a manifest file, the manifest file is required only to include a version number.</span></span> <span data-ttu-id="965c8-162">Manifest filen innehåller dock ofta användbar information om en modul, dess krav och dess innehåll.</span><span class="sxs-lookup"><span data-stu-id="965c8-162">However, manifest files often provide useful information about a module, its requirements, and its contents.</span></span>

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

<span data-ttu-id="965c8-163">Det första kommandot hämtar PSModuleInfo-objektet som representerar BitsTransfer-modulen.</span><span class="sxs-lookup"><span data-stu-id="965c8-163">The first command gets the PSModuleInfo object that represents BitsTransfer module.</span></span> <span data-ttu-id="965c8-164">Objektet sparas i `$m` variabeln.</span><span class="sxs-lookup"><span data-stu-id="965c8-164">It saves the object in the `$m` variable.</span></span>

<span data-ttu-id="965c8-165">Det andra kommandot använder `Get-Content` cmdleten för att hämta innehållet i manifest filen på den angivna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="965c8-165">The second command uses the `Get-Content` cmdlet to get the content of the manifest file in the specified path.</span></span> <span data-ttu-id="965c8-166">Den använder punkt notation för att hämta sökvägen till manifest filen, som lagras i objektets Sök vägs egenskap.</span><span class="sxs-lookup"><span data-stu-id="965c8-166">It uses dot notation to get the path to the manifest file, which is stored in the Path property of the object.</span></span> <span data-ttu-id="965c8-167">Utdata visar innehållet i modulens manifest.</span><span class="sxs-lookup"><span data-stu-id="965c8-167">The output shows the contents of the module manifest.</span></span>

### <span data-ttu-id="965c8-168">Exempel 8: Visa filer i modulens katalog</span><span class="sxs-lookup"><span data-stu-id="965c8-168">Example 8: List files in module directory</span></span>

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

<span data-ttu-id="965c8-169">Det här kommandot visar filerna i modulens katalog.</span><span class="sxs-lookup"><span data-stu-id="965c8-169">This command lists the files in the directory of the module.</span></span> <span data-ttu-id="965c8-170">Detta är ett annat sätt att avgöra vad som finns i en modul innan du importerar den.</span><span class="sxs-lookup"><span data-stu-id="965c8-170">This is another way to determine what is in a module before you import it.</span></span> <span data-ttu-id="965c8-171">Vissa moduler kan ha hjälpfiler eller ReadMe-filer som beskriver modulen.</span><span class="sxs-lookup"><span data-stu-id="965c8-171">Some modules might have help files or ReadMe files that describe the module.</span></span>

### <span data-ttu-id="965c8-172">Exempel 9: Hämta moduler som är installerade på en dator</span><span class="sxs-lookup"><span data-stu-id="965c8-172">Example 9: Get modules installed on a computer</span></span>

```powershell
$s = New-PSSession -ComputerName Server01

Get-Module -PSSession $s -ListAvailable
```

<span data-ttu-id="965c8-173">De här kommandona hämtar de moduler som är installerade på den Server01 datorn.</span><span class="sxs-lookup"><span data-stu-id="965c8-173">These commands get the modules that are installed on the Server01 computer.</span></span>

<span data-ttu-id="965c8-174">Det första kommandot använder `New-PSSession` cmdleten för att skapa en **PSSession** på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="965c8-174">The first command uses the `New-PSSession` cmdlet to create a **PSSession** on the Server01 computer.</span></span> <span data-ttu-id="965c8-175">Kommandot sparar **PSSession** i variabeln $s.</span><span class="sxs-lookup"><span data-stu-id="965c8-175">The command saves the **PSSession** in the $s variable.</span></span>

<span data-ttu-id="965c8-176">Det andra kommandot använder parametrarna **PSSession** och **ListAvailable** för `Get-Module` för att hämta modulerna i **PSSession** i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="965c8-176">The second command uses the **PSSession** and **ListAvailable** parameters of `Get-Module` to get the modules in the **PSSession** in the `$s` variable.</span></span>

<span data-ttu-id="965c8-177">Om du rör moduler från andra sessioner till `Import-Module` cmdlet: en `Import-Module` importerar modulen till den aktuella sessionen med hjälp av funktionen implicit fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="965c8-177">If you pipe modules from other sessions to the `Import-Module` cmdlet, `Import-Module` imports the module into the current session by using the implicit remoting feature.</span></span> <span data-ttu-id="965c8-178">Detta motsvarar att använda `Import-PSSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="965c8-178">This is equivalent to using the `Import-PSSession` cmdlet.</span></span> <span data-ttu-id="965c8-179">Du kan använda cmdlets från modulen i den aktuella sessionen, men kommandon som använder dessa cmdlets kör i själva verket fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="965c8-179">You can use the cmdlets from the module in the current session, but commands that use these cmdlets actually run the remote session.</span></span> <span data-ttu-id="965c8-180">Mer information finns i [`Import-Module`](Import-Module.md) och [`Import-PSSession`](../Microsoft.PowerShell.Utility/Import-PSSession.md) .</span><span class="sxs-lookup"><span data-stu-id="965c8-180">For more information, see [`Import-Module`](Import-Module.md) and [`Import-PSSession`](../Microsoft.PowerShell.Utility/Import-PSSession.md).</span></span>

### <span data-ttu-id="965c8-181">Exempel 10: hantera en dator som inte kör Windows operativ system</span><span class="sxs-lookup"><span data-stu-id="965c8-181">Example 10: Manage a computer that does not run the Windows operating system</span></span>

<span data-ttu-id="965c8-182">Med kommandona i det här exemplet kan du hantera lagrings systemen på en fjärrdator som inte kör Windows-operativsystemet.</span><span class="sxs-lookup"><span data-stu-id="965c8-182">The commands in this example enable you to manage the storage systems of a remote computer that is not running the Windows operating system.</span></span>
<span data-ttu-id="965c8-183">I det här exemplet, eftersom datorns administratör har installerat WMI-providern för modul identifiering, kan CIM-kommandon använda standardvärdena, som är utformade för providern.</span><span class="sxs-lookup"><span data-stu-id="965c8-183">In this example, because the administrator of the computer has installed the Module Discovery WMI provider, the CIM commands can use the default values, which are designed for the provider.</span></span>

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

<span data-ttu-id="965c8-184">Det första kommandot använder `New-CimSession` cmdleten för att skapa en session på RSDGF03-fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="965c8-184">The first command uses the `New-CimSession` cmdlet to create a session on the RSDGF03 remote computer.</span></span> <span data-ttu-id="965c8-185">Sessionen ansluter till WMI på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="965c8-185">The session connects to WMI on the remote computer.</span></span> <span data-ttu-id="965c8-186">Kommandot sparar CIM-sessionen i `$cs` variabeln.</span><span class="sxs-lookup"><span data-stu-id="965c8-186">The command saves the CIM session in the `$cs` variable.</span></span>

<span data-ttu-id="965c8-187">Det andra kommandot använder CIM-sessionen i `$cs` variabeln för att köra ett `Get-Module` kommando på RSDGF03-datorn.</span><span class="sxs-lookup"><span data-stu-id="965c8-187">The second command uses the CIM session in the `$cs` variable to run a `Get-Module` command on the RSDGF03 computer.</span></span> <span data-ttu-id="965c8-188">Kommandot använder name-parametern för att ange Storage-modulen.</span><span class="sxs-lookup"><span data-stu-id="965c8-188">The command uses the Name parameter to specify the Storage module.</span></span> <span data-ttu-id="965c8-189">Kommandot använder en pipeline-operator (|) för att skicka modulen till `Import-Module` cmdleten, som importerar den till den lokala sessionen.</span><span class="sxs-lookup"><span data-stu-id="965c8-189">The command uses a pipeline operator (|) to send the Storage module to the `Import-Module` cmdlet, which imports it into the local session.</span></span>

<span data-ttu-id="965c8-190">Det tredje kommandot kör `Get-Command` cmdleten i `Get-Disk` kommandot i modulen Storage.</span><span class="sxs-lookup"><span data-stu-id="965c8-190">The third command runs the `Get-Command` cmdlet on the `Get-Disk` command in the Storage module.</span></span>
<span data-ttu-id="965c8-191">När du importerar en CIM-modul till den lokala sessionen konverterar PowerShell de CDXLM-filer som representerar CIM-modulen till PowerShell-skript, som visas som funktioner i den lokala sessionen.</span><span class="sxs-lookup"><span data-stu-id="965c8-191">When you import a CIM module into the local session, PowerShell converts the CDXML files that represent the CIM module into PowerShell scripts, which appear as functions in the local session.</span></span>

<span data-ttu-id="965c8-192">Det fjärde kommandot kör `Get-Disk` kommandot.</span><span class="sxs-lookup"><span data-stu-id="965c8-192">The fourth command runs the `Get-Disk` command.</span></span> <span data-ttu-id="965c8-193">Även om kommandot skrivs i den lokala sessionen körs det implicit på den fjärrdator som den importerades från.</span><span class="sxs-lookup"><span data-stu-id="965c8-193">Although the command is typed in the local session, it runs implicitly on the remote computer from which it was imported.</span></span> <span data-ttu-id="965c8-194">Kommandot hämtar objekt från fjärrdatorn och returnerar dem till den lokala sessionen.</span><span class="sxs-lookup"><span data-stu-id="965c8-194">The command gets objects from the remote computer and returns them to the local session.</span></span>

## <span data-ttu-id="965c8-195">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="965c8-195">PARAMETERS</span></span>

### <span data-ttu-id="965c8-196">– Alla</span><span class="sxs-lookup"><span data-stu-id="965c8-196">-All</span></span>

<span data-ttu-id="965c8-197">Anger att denna cmdlet hämtar alla moduler i varje modul, inklusive kapslade moduler, manifest (. psd1)-filer, skriptfiler (. psm1) och binärfiler (. dll) för filer.</span><span class="sxs-lookup"><span data-stu-id="965c8-197">Indicates that this cmdlet gets all modules in each module folder, including nested modules, manifest (.psd1) files, script module (.psm1) files, and binary module (.dll) files.</span></span> <span data-ttu-id="965c8-198">Utan den här parametern `Get-Module` hämtas bara standardmodulen i varje modul-mapp.</span><span class="sxs-lookup"><span data-stu-id="965c8-198">Without this parameter, `Get-Module` gets only the default module in each module folder.</span></span>

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

### <span data-ttu-id="965c8-199">-CimNamespace</span><span class="sxs-lookup"><span data-stu-id="965c8-199">-CimNamespace</span></span>

<span data-ttu-id="965c8-200">Anger namn området för en alternativ CIM-provider som exponerar CIM-moduler.</span><span class="sxs-lookup"><span data-stu-id="965c8-200">Specifies the namespace of an alternate CIM provider that exposes CIM modules.</span></span> <span data-ttu-id="965c8-201">Standardvärdet är namn området för WMI-providern för modul identifiering.</span><span class="sxs-lookup"><span data-stu-id="965c8-201">The default value is the namespace of the Module Discovery WMI provider.</span></span>

<span data-ttu-id="965c8-202">Använd den här parametern för att hämta CIM-moduler från datorer och enheter som inte kör Windows operativ system.</span><span class="sxs-lookup"><span data-stu-id="965c8-202">Use this parameter to get CIM modules from computers and devices that are not running the Windows operating system.</span></span>

<span data-ttu-id="965c8-203">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="965c8-203">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="965c8-204">-CimResourceUri</span><span class="sxs-lookup"><span data-stu-id="965c8-204">-CimResourceUri</span></span>

<span data-ttu-id="965c8-205">Anger en alternativ plats för CIM-moduler.</span><span class="sxs-lookup"><span data-stu-id="965c8-205">Specifies an alternate location for CIM modules.</span></span> <span data-ttu-id="965c8-206">Standardvärdet är resurs-URI för WMI-providern för module-identifiering på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="965c8-206">The default value is the resource URI of the Module Discovery WMI provider on the remote computer.</span></span>

<span data-ttu-id="965c8-207">Använd den här parametern för att hämta CIM-moduler från datorer och enheter som inte kör Windows operativ system.</span><span class="sxs-lookup"><span data-stu-id="965c8-207">Use this parameter to get CIM modules from computers and devices that are not running the Windows operating system.</span></span>

<span data-ttu-id="965c8-208">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="965c8-208">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="965c8-209">– CimSession</span><span class="sxs-lookup"><span data-stu-id="965c8-209">-CimSession</span></span>

<span data-ttu-id="965c8-210">Anger en CIM-session på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="965c8-210">Specifies a CIM session on the remote computer.</span></span> <span data-ttu-id="965c8-211">Ange en variabel som innehåller CIM-sessionen eller ett kommando som hämtar CIM-sessionen, till exempel ett [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) -kommando.</span><span class="sxs-lookup"><span data-stu-id="965c8-211">Enter a variable that contains the CIM session or a command that gets the CIM session, such as a [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) command.</span></span>

<span data-ttu-id="965c8-212">`Get-Module` använder CIM-sessionen för att hämta moduler från fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="965c8-212">`Get-Module` uses the CIM session connection to get modules from the remote computer.</span></span> <span data-ttu-id="965c8-213">När du importerar modulen med hjälp av `Import-Module` cmdleten och använder kommandona från den importerade modulen i den aktuella sessionen, körs de kommandon som faktiskt körs på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="965c8-213">When you import the module by using the `Import-Module` cmdlet and use the commands from the imported module in the current session, the commands actually run on the remote computer.</span></span>

<span data-ttu-id="965c8-214">Du kan använda den här parametern för att hämta moduler från datorer och enheter som inte kör Windows-operativsystemet och datorer som har PowerShell, men som inte har PowerShell-fjärrkommunikation aktive rad.</span><span class="sxs-lookup"><span data-stu-id="965c8-214">You can use this parameter to get modules from computers and devices that are not running the Windows operating system, and computers that have PowerShell, but do not have PowerShell remoting enabled.</span></span>

<span data-ttu-id="965c8-215">Parametern **CimSession** hämtar alla moduler i **CimSession**.</span><span class="sxs-lookup"><span data-stu-id="965c8-215">The **CimSession** parameter gets all modules in the **CIMSession**.</span></span> <span data-ttu-id="965c8-216">Du kan dock endast importera CIM-baserade och CDXLM-baserade moduler (cmdlet definition XML).</span><span class="sxs-lookup"><span data-stu-id="965c8-216">However, you can import only CIM-based and Cmdlet Definition XML (CDXML)-based modules.</span></span>

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

### <span data-ttu-id="965c8-217">-FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="965c8-217">-FullyQualifiedName</span></span>

<span data-ttu-id="965c8-218">Anger moduler med namn som anges i form av **ModuleSpecification** -objekt.</span><span class="sxs-lookup"><span data-stu-id="965c8-218">Specifies modules with names that are specified in the form of **ModuleSpecification** objects.</span></span> <span data-ttu-id="965c8-219">Se avsnittet anmärkningar i [ModuleSpecification-konstruktorn (hash)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span><span class="sxs-lookup"><span data-stu-id="965c8-219">See the Remarks section of [ModuleSpecification Constructor (Hashtable)](/dotnet/api/microsoft.powershell.commands.modulespecification.-ctor#Microsoft_PowerShell_Commands_ModuleSpecification__ctor_System_Collections_Hashtable_).</span></span>

<span data-ttu-id="965c8-220">**FullyQualifiedModule** -parametern accepterar till exempel ett modulnamn som anges i något av följande format:</span><span class="sxs-lookup"><span data-stu-id="965c8-220">For example, the **FullyQualifiedModule** parameter accepts a module name that is specified in either of these formats:</span></span>

- `@{ModuleName = "modulename"; ModuleVersion = "version_number"}`
- `@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}`

<span data-ttu-id="965c8-221">**Modulnamn** och **ModuleVersion** krävs, men **GUID** är valfritt.</span><span class="sxs-lookup"><span data-stu-id="965c8-221">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span> <span data-ttu-id="965c8-222">Det går inte att ange parametern **FullyQualifiedModule** i samma kommando som en **modul** -parameter.</span><span class="sxs-lookup"><span data-stu-id="965c8-222">You cannot specify the **FullyQualifiedModule** parameter in the same command as a **Module** parameter.</span></span> <span data-ttu-id="965c8-223">de två parametrarna kan inte anges samtidigt.</span><span class="sxs-lookup"><span data-stu-id="965c8-223">the two parameters are mutually exclusive.</span></span>

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

### <span data-ttu-id="965c8-224">– ListAvailable</span><span class="sxs-lookup"><span data-stu-id="965c8-224">-ListAvailable</span></span>

<span data-ttu-id="965c8-225">Anger att denna cmdlet hämtar alla installerade moduler.</span><span class="sxs-lookup"><span data-stu-id="965c8-225">Indicates that this cmdlet gets all installed modules.</span></span> <span data-ttu-id="965c8-226">`Get-Module` hämtar moduler i sökvägar som anges i miljövariabeln **PSModulePath** .</span><span class="sxs-lookup"><span data-stu-id="965c8-226">`Get-Module` gets modules in paths listed in the **PSModulePath** environment variable.</span></span> <span data-ttu-id="965c8-227">Utan den här parametern `Get-Module` hämtas bara de moduler som båda anges i miljövariabeln **PSModulePath** och som läses in i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="965c8-227">Without this parameter, `Get-Module` gets only the modules that are both listed in the **PSModulePath** environment variable, and that are loaded in the current session.</span></span> <span data-ttu-id="965c8-228">**ListAvailable** returnerar inte information om moduler som inte finns i miljövariabeln **PSModulePath** , även om modulerna har lästs in i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="965c8-228">**ListAvailable** does not return information about modules that are not found in the **PSModulePath** environment variable, even if those modules are loaded in the current session.</span></span>

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

### <span data-ttu-id="965c8-229">-Name</span><span class="sxs-lookup"><span data-stu-id="965c8-229">-Name</span></span>

<span data-ttu-id="965c8-230">Anger namn eller namn mönster för moduler som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="965c8-230">Specifies names or name patterns of modules that this cmdlet gets.</span></span> <span data-ttu-id="965c8-231">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="965c8-231">Wildcard characters are permitted.</span></span> <span data-ttu-id="965c8-232">Du kan också skicka namnen till `Get-Module` .</span><span class="sxs-lookup"><span data-stu-id="965c8-232">You can also pipe the names to `Get-Module`.</span></span> <span data-ttu-id="965c8-233">Det går inte att ange parametern **FullyQualifiedName** i samma kommando som en **namn** parameter.</span><span class="sxs-lookup"><span data-stu-id="965c8-233">You cannot specify the **FullyQualifiedName** parameter in the same command as a **Name** parameter.</span></span>

<span data-ttu-id="965c8-234">**Namnet** kan inte acceptera ett modul-GUID som värde.</span><span class="sxs-lookup"><span data-stu-id="965c8-234">**Name** cannot accept a module GUID as a value.</span></span>
<span data-ttu-id="965c8-235">Om du vill returnera moduler genom att ange ett GUID använder du **FullyQualifiedName** i stället.</span><span class="sxs-lookup"><span data-stu-id="965c8-235">To return modules by specifying a GUID, use **FullyQualifiedName** instead.</span></span>

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

### <span data-ttu-id="965c8-236">– PSEdition</span><span class="sxs-lookup"><span data-stu-id="965c8-236">-PSEdition</span></span>

<span data-ttu-id="965c8-237">Hämtar de moduler som stöder den angivna versionen av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="965c8-237">Gets the modules that support specified edition of PowerShell.</span></span>

<span data-ttu-id="965c8-238">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="965c8-238">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="965c8-239">Skrivbord</span><span class="sxs-lookup"><span data-stu-id="965c8-239">Desktop</span></span>
- <span data-ttu-id="965c8-240">Kärna</span><span class="sxs-lookup"><span data-stu-id="965c8-240">Core</span></span>

<span data-ttu-id="965c8-241">Get-Module cmdleten kontrollerar egenskapen **CompatiblePSEditions** för **PSModuleInfo** -objektet för det angivna värdet och returnerar bara de moduler som har angetts.</span><span class="sxs-lookup"><span data-stu-id="965c8-241">The Get-Module cmdlet checks **CompatiblePSEditions** property of **PSModuleInfo** object for the specified value and returns only those modules that have it set.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="965c8-242">**Desktop Edition:** bygger på .NET Framework och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på fullständiga utgåvor av Windows, till exempel Server Core och Windows Desktop.</span><span class="sxs-lookup"><span data-stu-id="965c8-242">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
> - <span data-ttu-id="965c8-243">**Core Edition:** bygger på .NET Core och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på begränsade utgåvor av Windows som Nano Server och Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="965c8-243">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

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

### <span data-ttu-id="965c8-244">– PSSession</span><span class="sxs-lookup"><span data-stu-id="965c8-244">-PSSession</span></span>

<span data-ttu-id="965c8-245">Hämtar modulerna i den angivna användar hanterade PowerShell-sessionen ( **PSSession** ).</span><span class="sxs-lookup"><span data-stu-id="965c8-245">Gets the modules in the specified user-managed PowerShell session ( **PSSession** ).</span></span> <span data-ttu-id="965c8-246">Ange en variabel som innehåller sessionen, ett kommando som hämtar sessionen, till exempel ett `Get-PSSession` kommando eller ett kommando som skapar sessionen, till exempel ett `New-PSSession` kommando.</span><span class="sxs-lookup"><span data-stu-id="965c8-246">Enter a variable that contains the session, a command that gets the session, such as a `Get-PSSession` command, or a command that creates the session, such as a `New-PSSession` command.</span></span>

<span data-ttu-id="965c8-247">När sessionen är ansluten till en fjärrdator måste du ange parametern **ListAvailable** .</span><span class="sxs-lookup"><span data-stu-id="965c8-247">When the session is connected to a remote computer, you must specify the **ListAvailable** parameter.</span></span>

<span data-ttu-id="965c8-248">Ett `Get-Module` kommando som använder parametern **PSSession** är detsamma som att använda `Invoke-Command` cmdleten för att köra ett `Get-Module -ListAvailable` kommando i en **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="965c8-248">A `Get-Module` command that uses the **PSSession** parameter is equivalent to using the `Invoke-Command` cmdlet to run a `Get-Module -ListAvailable` command in a **PSSession**.</span></span>

<span data-ttu-id="965c8-249">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="965c8-249">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="965c8-250">-Uppdatera</span><span class="sxs-lookup"><span data-stu-id="965c8-250">-Refresh</span></span>

<span data-ttu-id="965c8-251">Anger att denna cmdlet uppdaterar cacheminnet för installerade kommandon.</span><span class="sxs-lookup"><span data-stu-id="965c8-251">Indicates that this cmdlet refreshes the cache of installed commands.</span></span> <span data-ttu-id="965c8-252">Kommandots cacheminne skapas när sessionen startar.</span><span class="sxs-lookup"><span data-stu-id="965c8-252">The command cache is created when the session starts.</span></span> <span data-ttu-id="965c8-253">Den gör det möjligt för `Get-Command` cmdleten att hämta kommandon från moduler som inte importeras till sessionen.</span><span class="sxs-lookup"><span data-stu-id="965c8-253">It enables the `Get-Command` cmdlet to get commands from modules that are not imported into the session.</span></span>

<span data-ttu-id="965c8-254">Den här parametern är utformad för utvecklings-och testnings scenarier där innehållet i moduler har ändrats sedan sessionen startades.</span><span class="sxs-lookup"><span data-stu-id="965c8-254">This parameter is designed for development and testing scenarios in which the contents of modules have changed since the session started.</span></span>

<span data-ttu-id="965c8-255">När du anger parametern **Refresh** i ett kommando måste du ange **ListAvailable**.</span><span class="sxs-lookup"><span data-stu-id="965c8-255">When you specify the **Refresh** parameter in a command, you must specify **ListAvailable**.</span></span>

<span data-ttu-id="965c8-256">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="965c8-256">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="965c8-257">-SkipEditionCheck</span><span class="sxs-lookup"><span data-stu-id="965c8-257">-SkipEditionCheck</span></span>

<span data-ttu-id="965c8-258">Hoppar över kontrollen av `CompatiblePSEditions` fältet.</span><span class="sxs-lookup"><span data-stu-id="965c8-258">Skips the check of the `CompatiblePSEditions` field.</span></span>

<span data-ttu-id="965c8-259">Som standard kommer Get-Module att utelämna moduler i `%windir%\System32\WindowsPowerShell\v1.0\Modules` katalogen som inte anges `Core` i `CompatiblePSEditions` fältet.</span><span class="sxs-lookup"><span data-stu-id="965c8-259">By default, Get-Module will omit modules in the `%windir%\System32\WindowsPowerShell\v1.0\Modules` directory that do not specify `Core` in the `CompatiblePSEditions` field.</span></span> <span data-ttu-id="965c8-260">När den här växeln har angetts kommer moduler utan att `Core` inkluderas, så att moduler under Windows PowerShell-modulens sökväg som är inkompatibla med PowerShell-kärnan returneras.</span><span class="sxs-lookup"><span data-stu-id="965c8-260">When this switch is set, modules without `Core` will be included, so that modules under the Windows PowerShell module path that are incompatible with PowerShell Core will be returned.</span></span>

<span data-ttu-id="965c8-261">I macOS och Linux gör den här parametern ingenting.</span><span class="sxs-lookup"><span data-stu-id="965c8-261">On macOS and Linux, this parameter does nothing.</span></span>

<span data-ttu-id="965c8-262">Se [about_PowerShell_Editions](About/about_PowerShell_Editions.md) för mer information.</span><span class="sxs-lookup"><span data-stu-id="965c8-262">See [about_PowerShell_Editions](About/about_PowerShell_Editions.md) for more information.</span></span>

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

### <span data-ttu-id="965c8-263">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="965c8-263">CommonParameters</span></span>

<span data-ttu-id="965c8-264">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="965c8-264">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="965c8-265">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="965c8-265">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="965c8-266">INDATA</span><span class="sxs-lookup"><span data-stu-id="965c8-266">INPUTS</span></span>

### <span data-ttu-id="965c8-267">System. String</span><span class="sxs-lookup"><span data-stu-id="965c8-267">System.String</span></span>

<span data-ttu-id="965c8-268">Du kan skicka pipe-modulnamn till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="965c8-268">You can pipe module names to this cmdlet.</span></span>

## <span data-ttu-id="965c8-269">UTDATA</span><span class="sxs-lookup"><span data-stu-id="965c8-269">OUTPUTS</span></span>

### <span data-ttu-id="965c8-270">System. Management. Automation. PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="965c8-270">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="965c8-271">Denna cmdlet returnerar objekt som representerar moduler.</span><span class="sxs-lookup"><span data-stu-id="965c8-271">This cmdlet returns objects that represent modules.</span></span>
<span data-ttu-id="965c8-272">När du anger parametern **ListAvailable** `Get-Module` returnerar ett **ModuleInfoGrouping** -objekt, som är en typ av **PSModuleInfo** -objekt som har samma egenskaper och metoder.</span><span class="sxs-lookup"><span data-stu-id="965c8-272">When you specify the **ListAvailable** parameter, `Get-Module` returns a **ModuleInfoGrouping** object, which is a type of **PSModuleInfo** object that has the same properties and methods.</span></span>

## <span data-ttu-id="965c8-273">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="965c8-273">NOTES</span></span>

- <span data-ttu-id="965c8-274">Från och med Windows PowerShell 3,0 paketeras kärn kommandona som ingår i PowerShell i moduler.</span><span class="sxs-lookup"><span data-stu-id="965c8-274">Beginning in Windows PowerShell 3.0, the core commands that are included in PowerShell are packaged in modules.</span></span> <span data-ttu-id="965c8-275">Undantaget är **Microsoft. PowerShell. Core** , som är en snapin-modul ( **PSSnapin** ).</span><span class="sxs-lookup"><span data-stu-id="965c8-275">The exception is **Microsoft.PowerShell.Core** , which is a snap-in ( **PSSnapin** ).</span></span> <span data-ttu-id="965c8-276">Som standard läggs bara snapin-modulen **Microsoft. PowerShell. Core** till i sessionen.</span><span class="sxs-lookup"><span data-stu-id="965c8-276">By default, only the **Microsoft.PowerShell.Core** snap-in is added to the session.</span></span>
<span data-ttu-id="965c8-277">Moduler importeras automatiskt vid första användningen och du kan använda `Import-Module` cmdleten för att importera dem.</span><span class="sxs-lookup"><span data-stu-id="965c8-277">Modules are imported automatically on first use and you can use the `Import-Module` cmdlet to import them.</span></span>
- <span data-ttu-id="965c8-278">Från och med Windows PowerShell 3,0 paketeras de grundläggande kommandon som installeras med PowerShell i moduler.</span><span class="sxs-lookup"><span data-stu-id="965c8-278">Starting in Windows PowerShell 3.0, the core commands that are installed with PowerShell are packaged in modules.</span></span> <span data-ttu-id="965c8-279">I Windows PowerShell 2,0 och i värd program som skapar äldre sessioner i senare versioner av PowerShell, paketeras huvud kommandona i snapin-moduler ( **PSSnapins** ).</span><span class="sxs-lookup"><span data-stu-id="965c8-279">In Windows PowerShell 2.0, and in host programs that create older-style sessions in later versions of PowerShell, the core commands are packaged in snap-ins ( **PSSnapins** ).</span></span> <span data-ttu-id="965c8-280">Undantaget är **Microsoft. PowerShell. Core** , som alltid är en snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="965c8-280">The exception is **Microsoft.PowerShell.Core** , which is always a snap-in.</span></span> <span data-ttu-id="965c8-281">Fjärrsessioner, till exempel de som startas av `New-PSSession` cmdleten, är äldre sessioner som inkluderar grundläggande snapin-moduler.</span><span class="sxs-lookup"><span data-stu-id="965c8-281">Also, remote sessions, such as those started by the `New-PSSession` cmdlet, are older-style sessions that include core snap-ins.</span></span>

  <span data-ttu-id="965c8-282">Information om **CreateDefault2** -metoden som skapar nyare sessioner med Core-moduler finns i CreateDefault2- [metoden](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2).</span><span class="sxs-lookup"><span data-stu-id="965c8-282">For information about the **CreateDefault2** method that creates newer-style sessions with core modules, see [CreateDefault2 Method](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2).</span></span>

- <span data-ttu-id="965c8-283">`Get-Module` hämtar endast moduler i platser som lagras i värdet för **PSModulePath** -miljövariabeln ($env:P smodulepath).</span><span class="sxs-lookup"><span data-stu-id="965c8-283">`Get-Module` only gets modules in locations that are stored in the value of the **PSModulePath** environment variable ($env:PSModulePath).</span></span> <span data-ttu-id="965c8-284">Du kan använda parametern **Path** för `Import-Module` cmdlet: en för att importera moduler på andra platser, men du kan inte använda `Get-Module` cmdleten för att hämta dem.</span><span class="sxs-lookup"><span data-stu-id="965c8-284">You can use the **Path** parameter of the `Import-Module` cmdlet to import modules in other locations, but you cannot use the `Get-Module` cmdlet to get them.</span></span>
- <span data-ttu-id="965c8-285">Från och med PowerShell 3,0 har nya egenskaper också lagts till i objektet som returnerar och `Get-Module` gör det lättare att lära sig om moduler, även innan de importeras.</span><span class="sxs-lookup"><span data-stu-id="965c8-285">Also, starting in PowerShell 3.0, new properties have been added to the object that `Get-Module` returns that make it easier to learn about modules even before they are imported.</span></span> <span data-ttu-id="965c8-286">Alla egenskaper fylls i före importen.</span><span class="sxs-lookup"><span data-stu-id="965c8-286">All properties are populated before importing.</span></span> <span data-ttu-id="965c8-287">Dessa inkluderar **ExportedCommands** -, **ExportedCmdlets** -och **ExportedFunctions** -egenskaperna som visar de kommandon som modulen exporterar.</span><span class="sxs-lookup"><span data-stu-id="965c8-287">These include the **ExportedCommands** , **ExportedCmdlets** and **ExportedFunctions** properties that list the commands that the module exports.</span></span>
- <span data-ttu-id="965c8-288">Parametern **ListAvailable** hämtar endast välformulerade moduler, det vill säga mappar som innehåller minst en fil vars bas namn är samma som namnet på mappen module.</span><span class="sxs-lookup"><span data-stu-id="965c8-288">The **ListAvailable** parameter gets only well-formed modules, that is, folders that contain at least one file whose base name is the same as the name of the module folder.</span></span> <span data-ttu-id="965c8-289">Bas namnet är namnet utan fil namns tillägget.</span><span class="sxs-lookup"><span data-stu-id="965c8-289">The base name is the name without the file name extension.</span></span> <span data-ttu-id="965c8-290">Mappar som innehåller filer som har olika namn anses vara behållare, men inte moduler.</span><span class="sxs-lookup"><span data-stu-id="965c8-290">Folders that contain files that have different names are considered to be containers, but not modules.</span></span>

  <span data-ttu-id="965c8-291">Om du vill hämta moduler som har implementerats som DLL-filer, men som inte är omslutna i en modul-mapp, anger du både **ListAvailable** och **alla** parametrar.</span><span class="sxs-lookup"><span data-stu-id="965c8-291">To get modules that are implemented as .dll files, but are not enclosed in a module folder, specify both the **ListAvailable** and **All** parameters.</span></span>

- <span data-ttu-id="965c8-292">Om du vill använda funktionen CIM-sessionen måste fjärrdatorn ha WS-Management fjärr anslutning och Windows Management Instrumentation (WMI), som är Microsofts implementering av Common Information Model (CIM) standard.</span><span class="sxs-lookup"><span data-stu-id="965c8-292">To use the CIM session feature, the remote computer must have WS-Management remoting and Windows Management Instrumentation (WMI), which is the Microsoft implementation of the Common Information Model (CIM) standard.</span></span> <span data-ttu-id="965c8-293">Datorn måste också ha WMI-providern för modul identifiering eller en alternativ WMI-provider som har samma grundläggande funktioner.</span><span class="sxs-lookup"><span data-stu-id="965c8-293">The computer must also have the Module Discovery WMI provider or an alternate WMI provider that has the same basic features.</span></span>

  <span data-ttu-id="965c8-294">Du kan använda funktionen för CIM-sessionen på datorer som inte kör Windows-operativsystemet och på Windows-datorer med PowerShell, men inte har PowerShell-fjärrkommunikation aktive rad.</span><span class="sxs-lookup"><span data-stu-id="965c8-294">You can use the CIM session feature on computers that are not running the Windows operating system and on Windows computers that have PowerShell, but do not have PowerShell remoting enabled.</span></span>

  <span data-ttu-id="965c8-295">Du kan också använda CIM-parametrarna för att hämta CIM-moduler från datorer där PowerShell-fjärrkommunikation är aktiverat.</span><span class="sxs-lookup"><span data-stu-id="965c8-295">You can also use the CIM parameters to get CIM modules from computers that have PowerShell remoting enabled.</span></span> <span data-ttu-id="965c8-296">Detta inkluderar den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="965c8-296">This includes the local computer.</span></span>
<span data-ttu-id="965c8-297">När du skapar en CIM-session på den lokala datorn använder PowerShell DCOM, i stället för WMI, för att skapa sessionen.</span><span class="sxs-lookup"><span data-stu-id="965c8-297">When you create a CIM session on the local computer, PowerShell uses DCOM, instead of WMI, to create the session.</span></span>

## <span data-ttu-id="965c8-298">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="965c8-298">RELATED LINKS</span></span>

[<span data-ttu-id="965c8-299">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="965c8-299">Get-CimSession</span></span>](../CimCmdlets/Get-CimSession.md)

[<span data-ttu-id="965c8-300">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="965c8-300">New-CimSession</span></span>](../CimCmdlets/New-CimSession.md)

[<span data-ttu-id="965c8-301">about_Modules</span><span class="sxs-lookup"><span data-stu-id="965c8-301">about_Modules</span></span>](About/about_Modules.md)

[<span data-ttu-id="965c8-302">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="965c8-302">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="965c8-303">Importera-modul</span><span class="sxs-lookup"><span data-stu-id="965c8-303">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="965c8-304">Importera – PSSession</span><span class="sxs-lookup"><span data-stu-id="965c8-304">Import-PSSession</span></span>](../Microsoft.PowerShell.Utility/Import-PSSession.md)

[<span data-ttu-id="965c8-305">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="965c8-305">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="965c8-306">Ta bort modul</span><span class="sxs-lookup"><span data-stu-id="965c8-306">Remove-Module</span></span>](Remove-Module.md)

[<span data-ttu-id="965c8-307">about_PowerShell_Editions</span><span class="sxs-lookup"><span data-stu-id="965c8-307">about_PowerShell_Editions</span></span>](About/about_PowerShell_Editions.md)
