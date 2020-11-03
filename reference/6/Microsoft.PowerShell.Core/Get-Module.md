---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 5/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-module?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Module
ms.openlocfilehash: b3444b0670794b9cc65329cbaabc7e26dd131f64
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266654"
---
# <span data-ttu-id="8ad43-103">Get-Module</span><span class="sxs-lookup"><span data-stu-id="8ad43-103">Get-Module</span></span>

## <span data-ttu-id="8ad43-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="8ad43-104">SYNOPSIS</span></span>
<span data-ttu-id="8ad43-105">Hämtar de moduler som har importer ATS eller som kan importeras till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="8ad43-105">Gets the modules that have been imported or that can be imported into the current session.</span></span>

## <span data-ttu-id="8ad43-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8ad43-106">SYNTAX</span></span>

### <span data-ttu-id="8ad43-107">Läst in (standard)</span><span class="sxs-lookup"><span data-stu-id="8ad43-107">Loaded (Default)</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-All] [<CommonParameters>]
```

### <span data-ttu-id="8ad43-108">Tillgänglig</span><span class="sxs-lookup"><span data-stu-id="8ad43-108">Available</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-All] [-ListAvailable]
 [-PSEdition <String>] [-SkipEditionCheck] [-Refresh] [<CommonParameters>]
```

### <span data-ttu-id="8ad43-109">PsSession</span><span class="sxs-lookup"><span data-stu-id="8ad43-109">PsSession</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-ListAvailable]
 [-PSEdition <String>] [-SkipEditionCheck] [-Refresh] -PSSession <PSSession> [<CommonParameters>]
```

### <span data-ttu-id="8ad43-110">CimSession</span><span class="sxs-lookup"><span data-stu-id="8ad43-110">CimSession</span></span>

```
Get-Module [[-Name] <String[]>] [-FullyQualifiedName <ModuleSpecification[]>] [-ListAvailable]
 [-SkipEditionCheck] [-Refresh] -CimSession <CimSession> [-CimResourceUri <Uri>] [-CimNamespace <String>]
 [<CommonParameters>]
```

## <span data-ttu-id="8ad43-111">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="8ad43-111">DESCRIPTION</span></span>

<span data-ttu-id="8ad43-112">Cmdlet: en `Get-Module` hämtar PowerShell-modulerna som har importer ATS, eller som kan importeras, till en PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="8ad43-112">The `Get-Module` cmdlet gets the PowerShell modules that have been imported, or that can be imported, into a PowerShell session.</span></span>
<span data-ttu-id="8ad43-113">Module-objektet som `Get-Module` returnerar innehåller värdefull information om modulen.</span><span class="sxs-lookup"><span data-stu-id="8ad43-113">The module object that `Get-Module` returns contains valuable information about the module.</span></span>
<span data-ttu-id="8ad43-114">Du kan också skicka modulens objekt till andra cmdletar, till exempel- `Import-Module` och- `Remove-Module` cmdlet: ar.</span><span class="sxs-lookup"><span data-stu-id="8ad43-114">You can also pipe the module objects to other cmdlets, such as the `Import-Module` and `Remove-Module` cmdlets.</span></span>

<span data-ttu-id="8ad43-115">Utan parametrar, `Get-Module` hämtar moduler som har importer ATS till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="8ad43-115">Without parameters, `Get-Module` gets modules that have been imported into the current session.</span></span>
<span data-ttu-id="8ad43-116">Om du vill hämta alla installerade moduler anger du parametern **ListAvailable** .</span><span class="sxs-lookup"><span data-stu-id="8ad43-116">To get all installed modules, specify the **ListAvailable** parameter.</span></span>

<span data-ttu-id="8ad43-117">`Get-Module` hämtar moduler, men importerar dem inte.</span><span class="sxs-lookup"><span data-stu-id="8ad43-117">`Get-Module` gets modules, but it does not import them.</span></span>
<span data-ttu-id="8ad43-118">Från och med Windows PowerShell 3,0 importeras moduler automatiskt när du använder ett kommando i modulen, men ett `Get-Module` kommando utlöser inte en automatisk import.</span><span class="sxs-lookup"><span data-stu-id="8ad43-118">Starting in Windows PowerShell 3.0, modules are automatically imported when you use a command in the module, but a `Get-Module` command does not trigger an automatic import.</span></span>
<span data-ttu-id="8ad43-119">Du kan också importera modulerna till-sessionen med hjälp av `Import-Module` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="8ad43-119">You can also import the modules into your session by using the `Import-Module` cmdlet.</span></span>

<span data-ttu-id="8ad43-120">Från och med Windows PowerShell 3,0 kan du hämta och importera moduler från fjärrsessioner till den lokala sessionen.</span><span class="sxs-lookup"><span data-stu-id="8ad43-120">Starting in Windows PowerShell 3.0, you can get and then, import modules from remote sessions into the local session.</span></span>
<span data-ttu-id="8ad43-121">Den här strategin använder funktionen implicit fjärr kommunikation i PowerShell och motsvarar att använda `Import-PSSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="8ad43-121">This strategy uses the Implicit Remoting feature of PowerShell and is equivalent to using the `Import-PSSession` cmdlet.</span></span>
<span data-ttu-id="8ad43-122">När du använder kommandon i moduler som importer ATS från en annan session körs kommandona implicit i fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="8ad43-122">When you use commands in modules imported from another session, the commands run implicitly in the remote session.</span></span> <span data-ttu-id="8ad43-123">Med den här funktionen kan du hantera fjärrdatorn från den lokala sessionen.</span><span class="sxs-lookup"><span data-stu-id="8ad43-123">This feature lets you manage the remote computer from the local session.</span></span>

<span data-ttu-id="8ad43-124">Från och med Windows PowerShell 3,0 kan du också använda `Get-Module` och `Import-Module` för att hämta och importera common information Model-moduler (CIM), där cmdletarna definieras i CMDLET definition XML-filer (cdxlm).</span><span class="sxs-lookup"><span data-stu-id="8ad43-124">Also, starting in Windows PowerShell 3.0, you can use `Get-Module` and `Import-Module` to get and import Common Information Model (CIM) modules, in which the cmdlets are defined in Cmdlet Definition XML (CDXML) files.</span></span>
<span data-ttu-id="8ad43-125">Med den här funktionen kan du använda cmdletar som implementeras i icke-hanterade kod sammansättningar, t. ex. sådana som skrivits i C++.</span><span class="sxs-lookup"><span data-stu-id="8ad43-125">This feature lets you use cmdlets that are implemented in non-managed code assemblies, such as those written in C++.</span></span>

<span data-ttu-id="8ad43-126">Med de här nya funktionerna `Get-Module` blir-och- `Import-Module` cmdletarna primära verktyg för att hantera heterogena företag som innehåller datorer som kör Windows-operativsystemet och datorer som kör andra operativ system.</span><span class="sxs-lookup"><span data-stu-id="8ad43-126">With these new features, the `Get-Module` and `Import-Module` cmdlets become primary tools for managing heterogeneous enterprises that include computers that run the Windows operating system and computers that run other operating systems.</span></span>

<span data-ttu-id="8ad43-127">För att hantera fjärrdatorer som kör Windows-operativsystemet med PowerShell-och PowerShell-fjärrkommunikation aktive rad, skapar du en **PSSession** på fjärrdatorn och använder sedan **PSSession** -parametern för `Get-Module` för att hämta PowerShell-modulerna i **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="8ad43-127">To manage remote computers that run the Windows operating system that have PowerShell and PowerShell remoting enabled, create a **PSSession** on the remote computer and then use the **PSSession** parameter of `Get-Module` to get the PowerShell modules in the **PSSession**.</span></span>
<span data-ttu-id="8ad43-128">När du importerar modulerna och sedan använder de importerade kommandona i den aktuella sessionen, körs kommandona implicit i **PSSession** på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="8ad43-128">When you import the modules, and then use the imported commands in the current session, the commands run implicitly in the **PSSession** on the remote computer.</span></span>
<span data-ttu-id="8ad43-129">Du kan använda den här strategin för att hantera fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="8ad43-129">You can use this strategy to manage the remote computer.</span></span>

<span data-ttu-id="8ad43-130">Du kan använda en liknande strategi för att hantera datorer som inte har PowerShell-fjärrkommunikation aktive rad.</span><span class="sxs-lookup"><span data-stu-id="8ad43-130">You can use a similar strategy to manage computers that do not have PowerShell remoting enabled.</span></span>
<span data-ttu-id="8ad43-131">Detta inkluderar datorer som inte kör Windows-operativsystemet och datorer som har PowerShell men inte har PowerShell-fjärrkommunikation aktive rad.</span><span class="sxs-lookup"><span data-stu-id="8ad43-131">These include computers that are not running the Windows operating system, and computers that have PowerShell but do not have PowerShell remoting enabled.</span></span>

<span data-ttu-id="8ad43-132">Börja med att skapa en CIM-session på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="8ad43-132">Start by creating a CIM session on the remote computer.</span></span>
<span data-ttu-id="8ad43-133">En CIM-session är en anslutning till Windows Management Instrumentation (WMI) på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="8ad43-133">A CIM session is a connection to Windows Management Instrumentation (WMI) on the remote computer.</span></span>
<span data-ttu-id="8ad43-134">Använd sedan **CIMSession** -parametern för `Get-Module` för att hämta CIM-moduler från CIM-sessionen.</span><span class="sxs-lookup"><span data-stu-id="8ad43-134">Then use the **CIMSession** parameter of `Get-Module` to get CIM modules from the CIM session.</span></span>
<span data-ttu-id="8ad43-135">När du importerar en CIM-modul med hjälp av `Import-Module` cmdleten och sedan kör de importerade kommandona, körs kommandona implicit på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="8ad43-135">When you import a CIM module by using the `Import-Module` cmdlet and then run the imported commands, the commands run implicitly on the remote computer.</span></span>
<span data-ttu-id="8ad43-136">Du kan använda den här WMI-och CIM-strategin för att hantera fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="8ad43-136">You can use this WMI and CIM strategy to manage the remote computer.</span></span>

## <span data-ttu-id="8ad43-137">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="8ad43-137">EXAMPLES</span></span>

### <span data-ttu-id="8ad43-138">Exempel 1: Hämta moduler som importer ATS till den aktuella sessionen</span><span class="sxs-lookup"><span data-stu-id="8ad43-138">Example 1: Get modules imported into the current session</span></span>

```powershell
Get-Module
```

<span data-ttu-id="8ad43-139">Det här kommandot hämtar moduler som har importer ATS till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="8ad43-139">This command gets modules that have been imported into the current session.</span></span>

### <span data-ttu-id="8ad43-140">Exempel 2: Hämta installerade moduler och tillgängliga moduler</span><span class="sxs-lookup"><span data-stu-id="8ad43-140">Example 2: Get installed modules and available modules</span></span>

```powershell
Get-Module -ListAvailable
```

<span data-ttu-id="8ad43-141">Detta kommando hämtar de moduler som är installerade på datorn och som kan importeras till den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="8ad43-141">This command gets the modules that are installed on the computer and can be imported into the current session.</span></span>

<span data-ttu-id="8ad43-142">`Get-Module` söker efter tillgängliga moduler i sökvägen som anges av variabeln **$env:P smodulepath** -miljövariabeln.</span><span class="sxs-lookup"><span data-stu-id="8ad43-142">`Get-Module` looks for available modules in the path specified by the **$env:PSModulePath** environment variable.</span></span>
<span data-ttu-id="8ad43-143">Mer information om **PSModulePath** finns i [about_Modules](About/about_Modules.md) och [about_Environment_Variables](About/about_Environment_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="8ad43-143">For more information about **PSModulePath** , see [about_Modules](About/about_Modules.md) and [about_Environment_Variables](About/about_Environment_Variables.md).</span></span>

### <span data-ttu-id="8ad43-144">Exempel 3: Hämta alla exporterade filer</span><span class="sxs-lookup"><span data-stu-id="8ad43-144">Example 3: Get all exported files</span></span>

```powershell
Get-Module -ListAvailable -All
```

<span data-ttu-id="8ad43-145">Det här kommandot hämtar alla exporterade filer för alla tillgängliga moduler.</span><span class="sxs-lookup"><span data-stu-id="8ad43-145">This command gets all of the exported files for all available modules.</span></span>

### <span data-ttu-id="8ad43-146">Exempel 4: Hämta en modul med dess fullständigt kvalificerade namn</span><span class="sxs-lookup"><span data-stu-id="8ad43-146">Example 4: Get a module by its fully qualified name</span></span>

```powershell
$FullyQualifedName = @{ModuleName="Microsoft.PowerShell.Management";ModuleVersion="3.1.0.0"}
  Get-Module -FullyQualifiedName $FullyQualifedName | Format-Table -Property Name,Version
```

```Output
Name                             Version
----                             -------
Microsoft.PowerShell.Management  3.1.0.0
```

<span data-ttu-id="8ad43-147">Detta kommando hämtar modulen **Microsoft. PowerShell. Management** genom att ange det fullständigt kvalificerade namnet på modulen med hjälp av parametern **FullyQualifiedName** .</span><span class="sxs-lookup"><span data-stu-id="8ad43-147">This command gets the **Microsoft.PowerShell.Management** module by specifying the fully qualified name of the module by using the **FullyQualifiedName** parameter.</span></span>
<span data-ttu-id="8ad43-148">Kommandot rör sedan resultatet i `Format-Table` cmdleten för att formatera resultatet som en tabell med **namn** och **version** som kolumn rubriker.</span><span class="sxs-lookup"><span data-stu-id="8ad43-148">The command then pipes the results into the `Format-Table` cmdlet to format the results as a table with **Name** and **Version** as the column headings.</span></span>

### <span data-ttu-id="8ad43-149">Exempel 5: Hämta egenskaper för en modul</span><span class="sxs-lookup"><span data-stu-id="8ad43-149">Example 5: Get properties of a module</span></span>

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

<span data-ttu-id="8ad43-150">Det här kommandot hämtar egenskaperna för det **PSModuleInfo** -objekt som `Get-Module` returneras.</span><span class="sxs-lookup"><span data-stu-id="8ad43-150">This command gets the properties of the **PSModuleInfo** object that `Get-Module` returns.</span></span>
<span data-ttu-id="8ad43-151">Det finns ett objekt för varje modul-fil.</span><span class="sxs-lookup"><span data-stu-id="8ad43-151">There is one object for each module file.</span></span>

<span data-ttu-id="8ad43-152">Du kan använda egenskaperna för att formatera och filtrera modulens objekt.</span><span class="sxs-lookup"><span data-stu-id="8ad43-152">You can use the properties to format and filter the module objects.</span></span>
<span data-ttu-id="8ad43-153">Mer information om egenskaperna finns i PSModuleInfo- [Egenskaper](/dotnet/api/system.management.automation.psmoduleinfo).</span><span class="sxs-lookup"><span data-stu-id="8ad43-153">For more information about the properties, see [PSModuleInfo Properties](/dotnet/api/system.management.automation.psmoduleinfo).</span></span>

<span data-ttu-id="8ad43-154">Utdata innehåller de nya egenskaperna, till exempel **författare** och **företags namn** , som introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8ad43-154">The output includes the new properties, such as **Author** and **CompanyName** , that were introduced in Windows PowerShell 3.0.</span></span>

### <span data-ttu-id="8ad43-155">Exempel 6: gruppera alla moduler efter namn</span><span class="sxs-lookup"><span data-stu-id="8ad43-155">Example 6: Group all modules by name</span></span>

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

<span data-ttu-id="8ad43-156">Det här kommandot hämtar alla modulblad, både importerade och tillgängliga, och grupperar dem efter modulnamn.</span><span class="sxs-lookup"><span data-stu-id="8ad43-156">This command gets all module files, both imported and available, and then groups them by module name.</span></span> <span data-ttu-id="8ad43-157">På så sätt kan du se de module-filer som varje skript exporterar.</span><span class="sxs-lookup"><span data-stu-id="8ad43-157">This lets you see the module files that each script is exporting.</span></span>

### <span data-ttu-id="8ad43-158">Exempel 7: Visa innehållet i ett modul-manifest</span><span class="sxs-lookup"><span data-stu-id="8ad43-158">Example 7: Display the contents of a module manifest</span></span>

<span data-ttu-id="8ad43-159">Dessa kommandon visar innehållet i modulens manifest för PowerShell-modulen för **BitsTransfer** .</span><span class="sxs-lookup"><span data-stu-id="8ad43-159">These commands display the contents of the module manifest for the PowerShell **BitsTransfer** module.</span></span>

<span data-ttu-id="8ad43-160">Moduler måste inte ha MANIFEST-filer.</span><span class="sxs-lookup"><span data-stu-id="8ad43-160">Modules are not required to have manifest files.</span></span>
<span data-ttu-id="8ad43-161">När de har en manifest fil, krävs manifest filen bara för att inkludera ett versions nummer.</span><span class="sxs-lookup"><span data-stu-id="8ad43-161">When they do have a manifest file, the manifest file is required only to include a version number.</span></span>
<span data-ttu-id="8ad43-162">Manifest filen innehåller dock ofta användbar information om en modul, dess krav och dess innehåll.</span><span class="sxs-lookup"><span data-stu-id="8ad43-162">However, manifest files often provide useful information about a module, its requirements, and its contents.</span></span>

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

<span data-ttu-id="8ad43-163">Det första kommandot hämtar PSModuleInfo-objektet som representerar BitsTransfer-modulen.</span><span class="sxs-lookup"><span data-stu-id="8ad43-163">The first command gets the PSModuleInfo object that represents BitsTransfer module.</span></span> <span data-ttu-id="8ad43-164">Objektet sparas i `$m` variabeln.</span><span class="sxs-lookup"><span data-stu-id="8ad43-164">It saves the object in the `$m` variable.</span></span>

<span data-ttu-id="8ad43-165">Det andra kommandot använder `Get-Content` cmdleten för att hämta innehållet i manifest filen på den angivna sökvägen.</span><span class="sxs-lookup"><span data-stu-id="8ad43-165">The second command uses the `Get-Content` cmdlet to get the content of the manifest file in the specified path.</span></span> <span data-ttu-id="8ad43-166">Den använder punkt notation för att hämta sökvägen till manifest filen, som lagras i objektets Sök vägs egenskap.</span><span class="sxs-lookup"><span data-stu-id="8ad43-166">It uses dot notation to get the path to the manifest file, which is stored in the Path property of the object.</span></span> <span data-ttu-id="8ad43-167">Utdata visar innehållet i modulens manifest.</span><span class="sxs-lookup"><span data-stu-id="8ad43-167">The output shows the contents of the module manifest.</span></span>

### <span data-ttu-id="8ad43-168">Exempel 8: Visa filer i modulens katalog</span><span class="sxs-lookup"><span data-stu-id="8ad43-168">Example 8: List files in module directory</span></span>

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

<span data-ttu-id="8ad43-169">Det här kommandot visar filerna i modulens katalog.</span><span class="sxs-lookup"><span data-stu-id="8ad43-169">This command lists the files in the directory of the module.</span></span>
<span data-ttu-id="8ad43-170">Detta är ett annat sätt att avgöra vad som finns i en modul innan du importerar den.</span><span class="sxs-lookup"><span data-stu-id="8ad43-170">This is another way to determine what is in a module before you import it.</span></span>
<span data-ttu-id="8ad43-171">Vissa moduler kan ha hjälpfiler eller ReadMe-filer som beskriver modulen.</span><span class="sxs-lookup"><span data-stu-id="8ad43-171">Some modules might have help files or ReadMe files that describe the module.</span></span>

### <span data-ttu-id="8ad43-172">Exempel 9: Hämta moduler som är installerade på en dator</span><span class="sxs-lookup"><span data-stu-id="8ad43-172">Example 9: Get modules installed on a computer</span></span>

```powershell
$s = New-PSSession -ComputerName Server01

Get-Module -PSSession $s -ListAvailable
```

<span data-ttu-id="8ad43-173">De här kommandona hämtar de moduler som är installerade på den Server01 datorn.</span><span class="sxs-lookup"><span data-stu-id="8ad43-173">These commands get the modules that are installed on the Server01 computer.</span></span>

<span data-ttu-id="8ad43-174">Det första kommandot använder `New-PSSession` cmdleten för att skapa en **PSSession** på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="8ad43-174">The first command uses the `New-PSSession` cmdlet to create a **PSSession** on the Server01 computer.</span></span> <span data-ttu-id="8ad43-175">Kommandot sparar **PSSession** i variabeln $s.</span><span class="sxs-lookup"><span data-stu-id="8ad43-175">The command saves the **PSSession** in the $s variable.</span></span>

<span data-ttu-id="8ad43-176">Det andra kommandot använder parametrarna **PSSession** och **ListAvailable** för `Get-Module` för att hämta modulerna i **PSSession** i variabeln $s.</span><span class="sxs-lookup"><span data-stu-id="8ad43-176">The second command uses the **PSSession** and **ListAvailable** parameters of `Get-Module` to get the modules in the **PSSession** in the $s variable.</span></span>

<span data-ttu-id="8ad43-177">Om du rör moduler från andra sessioner till `Import-Module` cmdlet: en `Import-Module` importerar modulen till den aktuella sessionen med hjälp av funktionen implicit fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="8ad43-177">If you pipe modules from other sessions to the `Import-Module` cmdlet, `Import-Module` imports the module into the current session by using the implicit remoting feature.</span></span>
<span data-ttu-id="8ad43-178">Detta motsvarar att använda `Import-PSSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="8ad43-178">This is equivalent to using the `Import-PSSession` cmdlet.</span></span>
<span data-ttu-id="8ad43-179">Du kan använda cmdlets från modulen i den aktuella sessionen, men kommandon som använder dessa cmdlets kör i själva verket fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="8ad43-179">You can use the cmdlets from the module in the current session, but commands that use these cmdlets actually run the remote session.</span></span>
<span data-ttu-id="8ad43-180">Mer information finns i [`Import-Module`](Import-Module.md) och [`Import-PSSession`](../Microsoft.PowerShell.Utility/Import-PSSession.md) .</span><span class="sxs-lookup"><span data-stu-id="8ad43-180">For more information, see [`Import-Module`](Import-Module.md) and [`Import-PSSession`](../Microsoft.PowerShell.Utility/Import-PSSession.md).</span></span>

### <span data-ttu-id="8ad43-181">Exempel 10: hantera en dator som inte kör Windows operativ system</span><span class="sxs-lookup"><span data-stu-id="8ad43-181">Example 10: Manage a computer that does not run the Windows operating system</span></span>

<span data-ttu-id="8ad43-182">Med kommandona i det här exemplet kan du hantera lagrings systemen på en fjärrdator som inte kör Windows-operativsystemet.</span><span class="sxs-lookup"><span data-stu-id="8ad43-182">The commands in this example enable you to manage the storage systems of a remote computer that is not running the Windows operating system.</span></span>
<span data-ttu-id="8ad43-183">I det här exemplet, eftersom datorns administratör har installerat WMI-providern för modul identifiering, kan CIM-kommandon använda standardvärdena, som är utformade för providern.</span><span class="sxs-lookup"><span data-stu-id="8ad43-183">In this example, because the administrator of the computer has installed the Module Discovery WMI provider, the CIM commands can use the default values, which are designed for the provider.</span></span>

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

<span data-ttu-id="8ad43-184">Det första kommandot använder `New-CimSession` cmdleten för att skapa en session på RSDGF03-fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="8ad43-184">The first command uses the `New-CimSession` cmdlet to create a session on the RSDGF03 remote computer.</span></span> <span data-ttu-id="8ad43-185">Sessionen ansluter till WMI på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="8ad43-185">The session connects to WMI on the remote computer.</span></span> <span data-ttu-id="8ad43-186">Kommandot sparar CIM-sessionen i `$cs` variabeln.</span><span class="sxs-lookup"><span data-stu-id="8ad43-186">The command saves the CIM session in the `$cs` variable.</span></span>

<span data-ttu-id="8ad43-187">Det andra kommandot använder CIM-sessionen i `$cs` variabeln för att köra ett `Get-Module` kommando på RSDGF03-datorn.</span><span class="sxs-lookup"><span data-stu-id="8ad43-187">The second command uses the CIM session in the `$cs` variable to run a `Get-Module` command on the RSDGF03 computer.</span></span> <span data-ttu-id="8ad43-188">Kommandot använder name-parametern för att ange Storage-modulen.</span><span class="sxs-lookup"><span data-stu-id="8ad43-188">The command uses the Name parameter to specify the Storage module.</span></span> <span data-ttu-id="8ad43-189">Kommandot använder en pipeline-operator (|) för att skicka modulen till `Import-Module` cmdleten, som importerar den till den lokala sessionen.</span><span class="sxs-lookup"><span data-stu-id="8ad43-189">The command uses a pipeline operator (|) to send the Storage module to the `Import-Module` cmdlet, which imports it into the local session.</span></span>

<span data-ttu-id="8ad43-190">Det tredje kommandot kör `Get-Command` cmdleten i `Get-Disk` kommandot i modulen Storage.</span><span class="sxs-lookup"><span data-stu-id="8ad43-190">The third command runs the `Get-Command` cmdlet on the `Get-Disk` command in the Storage module.</span></span>
<span data-ttu-id="8ad43-191">När du importerar en CIM-modul till den lokala sessionen konverterar PowerShell de CDXLM-filer som representerar CIM-modulen till PowerShell-skript, som visas som funktioner i den lokala sessionen.</span><span class="sxs-lookup"><span data-stu-id="8ad43-191">When you import a CIM module into the local session, PowerShell converts the CDXML files that represent the CIM module into PowerShell scripts, which appear as functions in the local session.</span></span>

<span data-ttu-id="8ad43-192">Det fjärde kommandot kör `Get-Disk` kommandot.</span><span class="sxs-lookup"><span data-stu-id="8ad43-192">The fourth command runs the `Get-Disk` command.</span></span> <span data-ttu-id="8ad43-193">Även om kommandot skrivs i den lokala sessionen körs det implicit på den fjärrdator som den importerades från.</span><span class="sxs-lookup"><span data-stu-id="8ad43-193">Although the command is typed in the local session, it runs implicitly on the remote computer from which it was imported.</span></span> <span data-ttu-id="8ad43-194">Kommandot hämtar objekt från fjärrdatorn och returnerar dem till den lokala sessionen.</span><span class="sxs-lookup"><span data-stu-id="8ad43-194">The command gets objects from the remote computer and returns them to the local session.</span></span>

## <span data-ttu-id="8ad43-195">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="8ad43-195">PARAMETERS</span></span>

### <span data-ttu-id="8ad43-196">– Alla</span><span class="sxs-lookup"><span data-stu-id="8ad43-196">-All</span></span>

<span data-ttu-id="8ad43-197">Anger att denna cmdlet hämtar alla moduler i varje modul, inklusive kapslade moduler, manifest (. psd1)-filer, skriptfiler (. psm1) och binärfiler (. dll) för filer.</span><span class="sxs-lookup"><span data-stu-id="8ad43-197">Indicates that this cmdlet gets all modules in each module folder, including nested modules, manifest (.psd1) files, script module (.psm1) files, and binary module (.dll) files.</span></span>
<span data-ttu-id="8ad43-198">Utan den här parametern `Get-Module` hämtas bara standardmodulen i varje modul-mapp.</span><span class="sxs-lookup"><span data-stu-id="8ad43-198">Without this parameter, `Get-Module` gets only the default module in each module folder.</span></span>

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

### <span data-ttu-id="8ad43-199">-CimNamespace</span><span class="sxs-lookup"><span data-stu-id="8ad43-199">-CimNamespace</span></span>

<span data-ttu-id="8ad43-200">Anger namn området för en alternativ CIM-provider som exponerar CIM-moduler.</span><span class="sxs-lookup"><span data-stu-id="8ad43-200">Specifies the namespace of an alternate CIM provider that exposes CIM modules.</span></span>
<span data-ttu-id="8ad43-201">Standardvärdet är namn området för WMI-providern för modul identifiering.</span><span class="sxs-lookup"><span data-stu-id="8ad43-201">The default value is the namespace of the Module Discovery WMI provider.</span></span>

<span data-ttu-id="8ad43-202">Använd den här parametern för att hämta CIM-moduler från datorer och enheter som inte kör Windows operativ system.</span><span class="sxs-lookup"><span data-stu-id="8ad43-202">Use this parameter to get CIM modules from computers and devices that are not running the Windows operating system.</span></span>

<span data-ttu-id="8ad43-203">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8ad43-203">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="8ad43-204">-CimResourceUri</span><span class="sxs-lookup"><span data-stu-id="8ad43-204">-CimResourceUri</span></span>

<span data-ttu-id="8ad43-205">Anger en alternativ plats för CIM-moduler.</span><span class="sxs-lookup"><span data-stu-id="8ad43-205">Specifies an alternate location for CIM modules.</span></span>
<span data-ttu-id="8ad43-206">Standardvärdet är resurs-URI för WMI-providern för module-identifiering på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="8ad43-206">The default value is the resource URI of the Module Discovery WMI provider on the remote computer.</span></span>

<span data-ttu-id="8ad43-207">Använd den här parametern för att hämta CIM-moduler från datorer och enheter som inte kör Windows operativ system.</span><span class="sxs-lookup"><span data-stu-id="8ad43-207">Use this parameter to get CIM modules from computers and devices that are not running the Windows operating system.</span></span>

<span data-ttu-id="8ad43-208">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8ad43-208">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="8ad43-209">– CimSession</span><span class="sxs-lookup"><span data-stu-id="8ad43-209">-CimSession</span></span>

<span data-ttu-id="8ad43-210">Anger en CIM-session på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="8ad43-210">Specifies a CIM session on the remote computer.</span></span>
<span data-ttu-id="8ad43-211">Ange en variabel som innehåller CIM-sessionen eller ett kommando som hämtar CIM-sessionen, till exempel ett [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) -kommando.</span><span class="sxs-lookup"><span data-stu-id="8ad43-211">Enter a variable that contains the CIM session or a command that gets the CIM session, such as a [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) command.</span></span>

<span data-ttu-id="8ad43-212">`Get-Module` använder CIM-sessionen för att hämta moduler från fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="8ad43-212">`Get-Module` uses the CIM session connection to get modules from the remote computer.</span></span>
<span data-ttu-id="8ad43-213">När du importerar modulen med hjälp av `Import-Module` cmdleten och använder kommandona från den importerade modulen i den aktuella sessionen, körs de kommandon som faktiskt körs på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="8ad43-213">When you import the module by using the `Import-Module` cmdlet and use the commands from the imported module in the current session, the commands actually run on the remote computer.</span></span>

<span data-ttu-id="8ad43-214">Du kan använda den här parametern för att hämta moduler från datorer och enheter som inte kör Windows-operativsystemet och datorer som har PowerShell, men som inte har PowerShell-fjärrkommunikation aktive rad.</span><span class="sxs-lookup"><span data-stu-id="8ad43-214">You can use this parameter to get modules from computers and devices that are not running the Windows operating system, and computers that have PowerShell, but do not have PowerShell remoting enabled.</span></span>

<span data-ttu-id="8ad43-215">Parametern **CimSession** hämtar alla moduler i **CimSession**.</span><span class="sxs-lookup"><span data-stu-id="8ad43-215">The **CimSession** parameter gets all modules in the **CIMSession**.</span></span>
<span data-ttu-id="8ad43-216">Du kan dock endast importera CIM-baserade och CDXLM-baserade moduler (cmdlet definition XML).</span><span class="sxs-lookup"><span data-stu-id="8ad43-216">However, you can import only CIM-based and Cmdlet Definition XML (CDXML)-based modules.</span></span>

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

### <span data-ttu-id="8ad43-217">-FullyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="8ad43-217">-FullyQualifiedName</span></span>

<span data-ttu-id="8ad43-218">Anger namn på moduler i form av **ModuleSpecification** -objekt.</span><span class="sxs-lookup"><span data-stu-id="8ad43-218">Specifies names of modules in the form of **ModuleSpecification** objects.</span></span>
<span data-ttu-id="8ad43-219">Dessa objekt beskrivs i avsnittet anmärkningar i [ModuleSpecification-konstruktorn (hash)](https://msdn.microsoft.com/library/jj136290) i MSDN-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="8ad43-219">These objects are described in the Remarks section of [ModuleSpecification Constructor (Hashtable)](https://msdn.microsoft.com/library/jj136290) in the MSDN library.</span></span>
<span data-ttu-id="8ad43-220">**FullyQualifiedName** -parametern accepterar till exempel ett modulnamn som anges i följande format:</span><span class="sxs-lookup"><span data-stu-id="8ad43-220">For example, the **FullyQualifiedName** parameter accepts a module name that is specified in the following formats:</span></span>

- <span data-ttu-id="8ad43-221">@ {Modulnamn = "Modulnamn"; ModuleVersion = "version_number"}</span><span class="sxs-lookup"><span data-stu-id="8ad43-221">@{ModuleName = "modulename"; ModuleVersion = "version_number"}</span></span>
- <span data-ttu-id="8ad43-222">@ {Modulnamn = "Modulnamn"; ModuleVersion = "version_number"; GUID = "GUID"}</span><span class="sxs-lookup"><span data-stu-id="8ad43-222">@{ModuleName = "modulename"; ModuleVersion = "version_number"; Guid = "GUID"}</span></span>

<span data-ttu-id="8ad43-223">**Modulnamn** och **ModuleVersion** krävs, men **GUID** är valfritt.</span><span class="sxs-lookup"><span data-stu-id="8ad43-223">**ModuleName** and **ModuleVersion** are required, but **Guid** is optional.</span></span>

<span data-ttu-id="8ad43-224">Det går inte att ange parametern **FullyQualifiedName** i samma kommando som en **namn** parameter.</span><span class="sxs-lookup"><span data-stu-id="8ad43-224">You cannot specify the **FullyQualifiedName** parameter in the same command as a **Name** parameter.</span></span>

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

### <span data-ttu-id="8ad43-225">– ListAvailable</span><span class="sxs-lookup"><span data-stu-id="8ad43-225">-ListAvailable</span></span>

<span data-ttu-id="8ad43-226">Anger att denna cmdlet hämtar alla installerade moduler.</span><span class="sxs-lookup"><span data-stu-id="8ad43-226">Indicates that this cmdlet gets all installed modules.</span></span>
<span data-ttu-id="8ad43-227">`Get-Module` hämtar moduler i sökvägar som anges i miljövariabeln **PSModulePath** .</span><span class="sxs-lookup"><span data-stu-id="8ad43-227">`Get-Module` gets modules in paths listed in the **PSModulePath** environment variable.</span></span>
<span data-ttu-id="8ad43-228">Utan den här parametern `Get-Module` hämtas bara de moduler som båda anges i miljövariabeln **PSModulePath** och som läses in i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="8ad43-228">Without this parameter, `Get-Module` gets only the modules that are both listed in the **PSModulePath** environment variable, and that are loaded in the current session.</span></span>
<span data-ttu-id="8ad43-229">**ListAvailable** returnerar inte information om moduler som inte finns i miljövariabeln **PSModulePath** , även om modulerna har lästs in i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="8ad43-229">**ListAvailable** does not return information about modules that are not found in the **PSModulePath** environment variable, even if those modules are loaded in the current session.</span></span>

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

### <span data-ttu-id="8ad43-230">-Name</span><span class="sxs-lookup"><span data-stu-id="8ad43-230">-Name</span></span>

<span data-ttu-id="8ad43-231">Anger namn eller namn mönster för moduler som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="8ad43-231">Specifies names or name patterns of modules that this cmdlet gets.</span></span>
<span data-ttu-id="8ad43-232">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="8ad43-232">Wildcard characters are permitted.</span></span>
<span data-ttu-id="8ad43-233">Du kan också skicka namnen till `Get-Module` .</span><span class="sxs-lookup"><span data-stu-id="8ad43-233">You can also pipe the names to `Get-Module`.</span></span>
<span data-ttu-id="8ad43-234">Det går inte att ange parametern **FullyQualifiedName** i samma kommando som en **namn** parameter.</span><span class="sxs-lookup"><span data-stu-id="8ad43-234">You cannot specify the **FullyQualifiedName** parameter in the same command as a **Name** parameter.</span></span>

<span data-ttu-id="8ad43-235">**Namnet** kan inte acceptera ett modul-GUID som värde.</span><span class="sxs-lookup"><span data-stu-id="8ad43-235">**Name** cannot accept a module GUID as a value.</span></span>
<span data-ttu-id="8ad43-236">Om du vill returnera moduler genom att ange ett GUID använder du **FullyQualifiedName** i stället.</span><span class="sxs-lookup"><span data-stu-id="8ad43-236">To return modules by specifying a GUID, use **FullyQualifiedName** instead.</span></span>

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

### <span data-ttu-id="8ad43-237">– PSSession</span><span class="sxs-lookup"><span data-stu-id="8ad43-237">-PSSession</span></span>

<span data-ttu-id="8ad43-238">Hämtar modulerna i den angivna användar hanterade PowerShell-sessionen ( **PSSession** ).</span><span class="sxs-lookup"><span data-stu-id="8ad43-238">Gets the modules in the specified user-managed PowerShell session ( **PSSession** ).</span></span>
<span data-ttu-id="8ad43-239">Ange en variabel som innehåller sessionen, ett kommando som hämtar sessionen, till exempel ett `Get-PSSession` kommando eller ett kommando som skapar sessionen, till exempel ett `New-PSSession` kommando.</span><span class="sxs-lookup"><span data-stu-id="8ad43-239">Enter a variable that contains the session, a command that gets the session, such as a `Get-PSSession` command, or a command that creates the session, such as a `New-PSSession` command.</span></span>

<span data-ttu-id="8ad43-240">När sessionen är ansluten till en fjärrdator måste du ange parametern **ListAvailable** .</span><span class="sxs-lookup"><span data-stu-id="8ad43-240">When the session is connected to a remote computer, you must specify the **ListAvailable** parameter.</span></span>

<span data-ttu-id="8ad43-241">Ett `Get-Module` kommando som använder parametern **PSSession** är detsamma som att använda `Invoke-Command` cmdleten för att köra ett `Get-Module -ListAvailable` kommando i en **PSSession**.</span><span class="sxs-lookup"><span data-stu-id="8ad43-241">A `Get-Module` command that uses the **PSSession** parameter is equivalent to using the `Invoke-Command` cmdlet to run a `Get-Module -ListAvailable` command in a **PSSession**.</span></span>

<span data-ttu-id="8ad43-242">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8ad43-242">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="8ad43-243">-Uppdatera</span><span class="sxs-lookup"><span data-stu-id="8ad43-243">-Refresh</span></span>

<span data-ttu-id="8ad43-244">Anger att denna cmdlet uppdaterar cacheminnet för installerade kommandon.</span><span class="sxs-lookup"><span data-stu-id="8ad43-244">Indicates that this cmdlet refreshes the cache of installed commands.</span></span>
<span data-ttu-id="8ad43-245">Kommandots cacheminne skapas när sessionen startar.</span><span class="sxs-lookup"><span data-stu-id="8ad43-245">The command cache is created when the session starts.</span></span>
<span data-ttu-id="8ad43-246">Den gör det möjligt för `Get-Command` cmdleten att hämta kommandon från moduler som inte importeras till sessionen.</span><span class="sxs-lookup"><span data-stu-id="8ad43-246">It enables the `Get-Command` cmdlet to get commands from modules that are not imported into the session.</span></span>

<span data-ttu-id="8ad43-247">Den här parametern är utformad för utvecklings-och testnings scenarier där innehållet i moduler har ändrats sedan sessionen startades.</span><span class="sxs-lookup"><span data-stu-id="8ad43-247">This parameter is designed for development and testing scenarios in which the contents of modules have changed since the session started.</span></span>

<span data-ttu-id="8ad43-248">När du anger parametern **Refresh** i ett kommando måste du ange **ListAvailable**.</span><span class="sxs-lookup"><span data-stu-id="8ad43-248">When you specify the **Refresh** parameter in a command, you must specify **ListAvailable**.</span></span>

<span data-ttu-id="8ad43-249">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8ad43-249">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="8ad43-250">– PSEdition</span><span class="sxs-lookup"><span data-stu-id="8ad43-250">-PSEdition</span></span>

<span data-ttu-id="8ad43-251">Hämtar de moduler som stöder den angivna versionen av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8ad43-251">Gets the modules that support specified edition of PowerShell.</span></span>

<span data-ttu-id="8ad43-252">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="8ad43-252">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="8ad43-253">Skrivbord</span><span class="sxs-lookup"><span data-stu-id="8ad43-253">Desktop</span></span>
- <span data-ttu-id="8ad43-254">Kärna</span><span class="sxs-lookup"><span data-stu-id="8ad43-254">Core</span></span>

<span data-ttu-id="8ad43-255">Get-Module cmdleten kontrollerar egenskapen **CompatiblePSEditions** för **PSModuleInfo** -objektet för det angivna värdet och returnerar bara de moduler som har angetts.</span><span class="sxs-lookup"><span data-stu-id="8ad43-255">The Get-Module cmdlet checks **CompatiblePSEditions** property of **PSModuleInfo** object for the specified value and returns only those modules that have it set.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="8ad43-256">**Desktop Edition:** Byggd på .NET Framework gäller för Windows PowerShell 5,1 och tidigare på de flesta Windows-versioner.</span><span class="sxs-lookup"><span data-stu-id="8ad43-256">**Desktop Edition:** Built on .NET Framework, applies to Windows PowerShell 5.1 and below on most Windows editions.</span></span>
> - <span data-ttu-id="8ad43-257">**Core-utgåva:** Bygger på .NET Core, gäller för PowerShell Core 6,0 och senare, samt vissa utgåvor av Windows PowerShell 5,1 som skapats för Windows IoT och Windows Nanoserver.</span><span class="sxs-lookup"><span data-stu-id="8ad43-257">**Core Edition:** Built on .NET Core, applies to PowerShell Core 6.0 and above, as well as some editions of Windows PowerShell 5.1 built for Windows IoT and Windows Nanoserver.</span></span> <span data-ttu-id="8ad43-258">> versionen av den aktuella PowerShell-sessionen kan hittas med `$PSEdition` variabeln.</span><span class="sxs-lookup"><span data-stu-id="8ad43-258">> The edition of the current PowerShell session can be found with the `$PSEdition` variable.</span></span>

```yaml
Type: System.String
Parameter Sets: Available, PsSession
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="8ad43-259">-SkipEditionCheck</span><span class="sxs-lookup"><span data-stu-id="8ad43-259">-SkipEditionCheck</span></span>

<span data-ttu-id="8ad43-260">Hoppar över kontrollen av `CompatiblePSEditions` fältet.</span><span class="sxs-lookup"><span data-stu-id="8ad43-260">Skips the check of the `CompatiblePSEditions` field.</span></span>

<span data-ttu-id="8ad43-261">Som standard kommer Get-Module att utelämna moduler i `%windir%\System32\WindowsPowerShell\v1.0\Modules` katalogen som inte anges `Core` i `CompatiblePSEditions` fältet.</span><span class="sxs-lookup"><span data-stu-id="8ad43-261">By default, Get-Module will omit modules in the `%windir%\System32\WindowsPowerShell\v1.0\Modules` directory that do not specify `Core` in the `CompatiblePSEditions` field.</span></span>
<span data-ttu-id="8ad43-262">När den här växeln har angetts kommer moduler utan att `Core` inkluderas, så att moduler under Windows PowerShell-modulens sökväg som är inkompatibla med PowerShell-kärnan returneras.</span><span class="sxs-lookup"><span data-stu-id="8ad43-262">When this switch is set, modules without `Core` will be included, so that modules under the Windows PowerShell module path that are incompatible with PowerShell Core will be returned.</span></span>

<span data-ttu-id="8ad43-263">I macOS och Linux gör den här parametern ingenting.</span><span class="sxs-lookup"><span data-stu-id="8ad43-263">On macOS and Linux, this parameter does nothing.</span></span>

<span data-ttu-id="8ad43-264">Se [about_PowerShell_Editions](About/about_PowerShell_Editions.md) för mer information.</span><span class="sxs-lookup"><span data-stu-id="8ad43-264">See [about_PowerShell_Editions](About/about_PowerShell_Editions.md) for more information.</span></span>

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

### <span data-ttu-id="8ad43-265">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8ad43-265">CommonParameters</span></span>

<span data-ttu-id="8ad43-266">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8ad43-266">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8ad43-267">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8ad43-267">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8ad43-268">INDATA</span><span class="sxs-lookup"><span data-stu-id="8ad43-268">INPUTS</span></span>

### <span data-ttu-id="8ad43-269">System. String</span><span class="sxs-lookup"><span data-stu-id="8ad43-269">System.String</span></span>

<span data-ttu-id="8ad43-270">Du kan skicka pipe-modulnamn till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8ad43-270">You can pipe module names to this cmdlet.</span></span>

## <span data-ttu-id="8ad43-271">UTDATA</span><span class="sxs-lookup"><span data-stu-id="8ad43-271">OUTPUTS</span></span>

### <span data-ttu-id="8ad43-272">System. Management. Automation. PSModuleInfo</span><span class="sxs-lookup"><span data-stu-id="8ad43-272">System.Management.Automation.PSModuleInfo</span></span>

<span data-ttu-id="8ad43-273">Denna cmdlet returnerar objekt som representerar moduler.</span><span class="sxs-lookup"><span data-stu-id="8ad43-273">This cmdlet returns objects that represent modules.</span></span>
<span data-ttu-id="8ad43-274">När du anger parametern **ListAvailable** `Get-Module` returnerar ett **ModuleInfoGrouping** -objekt, som är en typ av **PSModuleInfo** -objekt som har samma egenskaper och metoder.</span><span class="sxs-lookup"><span data-stu-id="8ad43-274">When you specify the **ListAvailable** parameter, `Get-Module` returns a **ModuleInfoGrouping** object, which is a type of **PSModuleInfo** object that has the same properties and methods.</span></span>

## <span data-ttu-id="8ad43-275">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="8ad43-275">NOTES</span></span>

- <span data-ttu-id="8ad43-276">Från och med Windows PowerShell 3,0 paketeras kärn kommandona som ingår i PowerShell i moduler.</span><span class="sxs-lookup"><span data-stu-id="8ad43-276">Beginning in Windows PowerShell 3.0, the core commands that are included in PowerShell are packaged in modules.</span></span> <span data-ttu-id="8ad43-277">Undantaget är **Microsoft. PowerShell. Core** , som är en snapin-modul ( **PSSnapin** ).</span><span class="sxs-lookup"><span data-stu-id="8ad43-277">The exception is **Microsoft.PowerShell.Core** , which is a snap-in ( **PSSnapin** ).</span></span> <span data-ttu-id="8ad43-278">Som standard läggs bara snapin-modulen **Microsoft. PowerShell. Core** till i sessionen.</span><span class="sxs-lookup"><span data-stu-id="8ad43-278">By default, only the **Microsoft.PowerShell.Core** snap-in is added to the session.</span></span>
<span data-ttu-id="8ad43-279">Moduler importeras automatiskt vid första användningen och du kan använda `Import-Module` cmdleten för att importera dem.</span><span class="sxs-lookup"><span data-stu-id="8ad43-279">Modules are imported automatically on first use and you can use the `Import-Module` cmdlet to import them.</span></span>
- <span data-ttu-id="8ad43-280">Från och med Windows PowerShell 3,0 paketeras de grundläggande kommandon som installeras med PowerShell i moduler.</span><span class="sxs-lookup"><span data-stu-id="8ad43-280">Starting in Windows PowerShell 3.0, the core commands that are installed with PowerShell are packaged in modules.</span></span> <span data-ttu-id="8ad43-281">I Windows PowerShell 2,0 och i värd program som skapar äldre sessioner i senare versioner av PowerShell, paketeras huvud kommandona i snapin-moduler ( **PSSnapins** ).</span><span class="sxs-lookup"><span data-stu-id="8ad43-281">In Windows PowerShell 2.0, and in host programs that create older-style sessions in later versions of PowerShell, the core commands are packaged in snap-ins ( **PSSnapins** ).</span></span> <span data-ttu-id="8ad43-282">Undantaget är **Microsoft. PowerShell. Core** , som alltid är en snapin-modul.</span><span class="sxs-lookup"><span data-stu-id="8ad43-282">The exception is **Microsoft.PowerShell.Core** , which is always a snap-in.</span></span> <span data-ttu-id="8ad43-283">Fjärrsessioner, till exempel de som startas av `New-PSSession` cmdleten, är äldre sessioner som inkluderar grundläggande snapin-moduler.</span><span class="sxs-lookup"><span data-stu-id="8ad43-283">Also, remote sessions, such as those started by the `New-PSSession` cmdlet, are older-style sessions that include core snap-ins.</span></span>

  <span data-ttu-id="8ad43-284">Information om **CreateDefault2** -metoden som skapar nyare sessioner med Core-moduler finns i CreateDefault2- [metoden](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2) i MSDN-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="8ad43-284">For information about the **CreateDefault2** method that creates newer-style sessions with core modules, see [CreateDefault2 Method](/dotnet/api/system.management.automation.runspaces.initialsessionstate.createdefault2) in the MSDN library.</span></span>

- <span data-ttu-id="8ad43-285">`Get-Module` hämtar endast moduler i platser som lagras i värdet för **PSModulePath** -miljövariabeln ($env:P smodulepath).</span><span class="sxs-lookup"><span data-stu-id="8ad43-285">`Get-Module` only gets modules in locations that are stored in the value of the **PSModulePath** environment variable ($env:PSModulePath).</span></span> <span data-ttu-id="8ad43-286">Du kan använda parametern **Path** för `Import-Module` cmdlet: en för att importera moduler på andra platser, men du kan inte använda `Get-Module` cmdleten för att hämta dem.</span><span class="sxs-lookup"><span data-stu-id="8ad43-286">You can use the **Path** parameter of the `Import-Module` cmdlet to import modules in other locations, but you cannot use the `Get-Module` cmdlet to get them.</span></span>
- <span data-ttu-id="8ad43-287">Från och med PowerShell 3,0 har nya egenskaper också lagts till i objektet som returnerar och `Get-Module` gör det lättare att lära sig om moduler, även innan de importeras.</span><span class="sxs-lookup"><span data-stu-id="8ad43-287">Also, starting in PowerShell 3.0, new properties have been added to the object that `Get-Module` returns that make it easier to learn about modules even before they are imported.</span></span> <span data-ttu-id="8ad43-288">Alla egenskaper fylls i före importen.</span><span class="sxs-lookup"><span data-stu-id="8ad43-288">All properties are populated before importing.</span></span> <span data-ttu-id="8ad43-289">Dessa inkluderar **ExportedCommands** -, **ExportedCmdlets** -och **ExportedFunctions** -egenskaperna som visar de kommandon som modulen exporterar.</span><span class="sxs-lookup"><span data-stu-id="8ad43-289">These include the **ExportedCommands** , **ExportedCmdlets** and **ExportedFunctions** properties that list the commands that the module exports.</span></span>
- <span data-ttu-id="8ad43-290">Parametern **ListAvailable** hämtar endast välformulerade moduler, det vill säga mappar som innehåller minst en fil vars bas namn är samma som namnet på mappen module.</span><span class="sxs-lookup"><span data-stu-id="8ad43-290">The **ListAvailable** parameter gets only well-formed modules, that is, folders that contain at least one file whose base name is the same as the name of the module folder.</span></span> <span data-ttu-id="8ad43-291">Bas namnet är namnet utan fil namns tillägget.</span><span class="sxs-lookup"><span data-stu-id="8ad43-291">The base name is the name without the file name extension.</span></span> <span data-ttu-id="8ad43-292">Mappar som innehåller filer som har olika namn anses vara behållare, men inte moduler.</span><span class="sxs-lookup"><span data-stu-id="8ad43-292">Folders that contain files that have different names are considered to be containers, but not modules.</span></span>

  <span data-ttu-id="8ad43-293">Om du vill hämta moduler som har implementerats som DLL-filer, men som inte är omslutna i en modul-mapp, anger du både **ListAvailable** och **alla** parametrar.</span><span class="sxs-lookup"><span data-stu-id="8ad43-293">To get modules that are implemented as .dll files, but are not enclosed in a module folder, specify both the **ListAvailable** and **All** parameters.</span></span>

- <span data-ttu-id="8ad43-294">Om du vill använda funktionen CIM-sessionen måste fjärrdatorn ha WS-Management fjärr anslutning och Windows Management Instrumentation (WMI), som är Microsofts implementering av Common Information Model (CIM) standard.</span><span class="sxs-lookup"><span data-stu-id="8ad43-294">To use the CIM session feature, the remote computer must have WS-Management remoting and Windows Management Instrumentation (WMI), which is the Microsoft implementation of the Common Information Model (CIM) standard.</span></span> <span data-ttu-id="8ad43-295">Datorn måste också ha WMI-providern för modul identifiering eller en alternativ WMI-provider som har samma grundläggande funktioner.</span><span class="sxs-lookup"><span data-stu-id="8ad43-295">The computer must also have the Module Discovery WMI provider or an alternate WMI provider that has the same basic features.</span></span>

  <span data-ttu-id="8ad43-296">Du kan använda funktionen för CIM-sessionen på datorer som inte kör Windows-operativsystemet och på Windows-datorer med PowerShell, men inte har PowerShell-fjärrkommunikation aktive rad.</span><span class="sxs-lookup"><span data-stu-id="8ad43-296">You can use the CIM session feature on computers that are not running the Windows operating system and on Windows computers that have PowerShell, but do not have PowerShell remoting enabled.</span></span>

  <span data-ttu-id="8ad43-297">Du kan också använda CIM-parametrarna för att hämta CIM-moduler från datorer där PowerShell-fjärrkommunikation är aktiverat.</span><span class="sxs-lookup"><span data-stu-id="8ad43-297">You can also use the CIM parameters to get CIM modules from computers that have PowerShell remoting enabled.</span></span> <span data-ttu-id="8ad43-298">Detta inkluderar den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="8ad43-298">This includes the local computer.</span></span>
<span data-ttu-id="8ad43-299">När du skapar en CIM-session på den lokala datorn använder PowerShell DCOM, i stället för WMI, för att skapa sessionen.</span><span class="sxs-lookup"><span data-stu-id="8ad43-299">When you create a CIM session on the local computer, PowerShell uses DCOM, instead of WMI, to create the session.</span></span>

## <span data-ttu-id="8ad43-300">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="8ad43-300">RELATED LINKS</span></span>

[<span data-ttu-id="8ad43-301">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="8ad43-301">Get-CimSession</span></span>](../CimCmdlets/Get-CimSession.md)

[<span data-ttu-id="8ad43-302">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="8ad43-302">New-CimSession</span></span>](../CimCmdlets/New-CimSession.md)

[<span data-ttu-id="8ad43-303">about_Modules</span><span class="sxs-lookup"><span data-stu-id="8ad43-303">about_Modules</span></span>](About/about_Modules.md)

[<span data-ttu-id="8ad43-304">Get-PSSession</span><span class="sxs-lookup"><span data-stu-id="8ad43-304">Get-PSSession</span></span>](Get-PSSession.md)

[<span data-ttu-id="8ad43-305">Importera-modul</span><span class="sxs-lookup"><span data-stu-id="8ad43-305">Import-Module</span></span>](Import-Module.md)

[<span data-ttu-id="8ad43-306">Importera – PSSession</span><span class="sxs-lookup"><span data-stu-id="8ad43-306">Import-PSSession</span></span>](../Microsoft.PowerShell.Utility/Import-PSSession.md)

[<span data-ttu-id="8ad43-307">New-PSSession</span><span class="sxs-lookup"><span data-stu-id="8ad43-307">New-PSSession</span></span>](New-PSSession.md)

[<span data-ttu-id="8ad43-308">Ta bort modul</span><span class="sxs-lookup"><span data-stu-id="8ad43-308">Remove-Module</span></span>](Remove-Module.md)

[<span data-ttu-id="8ad43-309">about_PowerShell_Editions</span><span class="sxs-lookup"><span data-stu-id="8ad43-309">about_PowerShell_Editions</span></span>](About/about_PowerShell_Editions.md)
