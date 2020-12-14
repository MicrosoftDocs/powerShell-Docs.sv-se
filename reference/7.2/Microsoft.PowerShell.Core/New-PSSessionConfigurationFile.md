---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/24/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/new-pssessionconfigurationfile?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-PSSessionConfigurationFile
ms.openlocfilehash: a41c52bf163aa0a73b54e75b5192389a14da82bb
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709174"
---
# <span data-ttu-id="01779-102">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="01779-102">New-PSSessionConfigurationFile</span></span>

## <span data-ttu-id="01779-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="01779-103">SYNOPSIS</span></span>
<span data-ttu-id="01779-104">Skapar en fil som definierar en sessions konfiguration.</span><span class="sxs-lookup"><span data-stu-id="01779-104">Creates a file that defines a session configuration.</span></span>

## <span data-ttu-id="01779-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="01779-105">SYNTAX</span></span>

```
New-PSSessionConfigurationFile [-Path] <String> [-SchemaVersion <Version>] [-Guid <Guid>]
 [-Author <String>] [-Description <String>] [-CompanyName <String>] [-Copyright <String>]
 [-SessionType <SessionType>] [-TranscriptDirectory <String>] [-RunAsVirtualAccount]
 [-RunAsVirtualAccountGroups <String[]>] [-MountUserDrive] [-UserDriveMaximumSize <Int64>]
 [-GroupManagedServiceAccount <String>] [-ScriptsToProcess <String[]>]
 [-RoleDefinitions <IDictionary>] [-RequiredGroups <IDictionary>] [-LanguageMode <PSLanguageMode>]
 [-ExecutionPolicy <ExecutionPolicy>] [-PowerShellVersion <Version>] [-ModulesToImport <Object[]>]
 [-VisibleAliases <String[]>] [-VisibleCmdlets <Object[]>] [-VisibleFunctions <Object[]>]
 [-VisibleExternalCommands <String[]>] [-VisibleProviders <String[]>]
 [-AliasDefinitions <IDictionary[]>] [-FunctionDefinitions <IDictionary[]>]
 [-VariableDefinitions <Object>] [-EnvironmentVariables <IDictionary>] [-TypesToProcess <String[]>]
 [-FormatsToProcess <String[]>] [-AssembliesToLoad <String[]>] [-Full] [<CommonParameters>]
```

## <span data-ttu-id="01779-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="01779-106">DESCRIPTION</span></span>

<span data-ttu-id="01779-107">`New-PSSessionConfigurationFile`Cmdleten skapar en fil med inställningar som definierar en sessions konfiguration och miljön för de sessioner som skapas med hjälp av konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-107">The `New-PSSessionConfigurationFile` cmdlet creates a file of settings that define a session configuration and the environment of sessions that are created by using the session configuration.</span></span>
<span data-ttu-id="01779-108">Om du vill använda filen i en konfiguration av en session  använder du parametern Path `Register-PSSessionConfiguration` i `Set-PSSessionConfiguration` cmdletarna eller.</span><span class="sxs-lookup"><span data-stu-id="01779-108">To use the file in a session configuration, use the **Path** parameter of the `Register-PSSessionConfiguration` or `Set-PSSessionConfiguration` cmdlets.</span></span>

<span data-ttu-id="01779-109">Den konfigurations fil för sessionen som `New-PSSessionConfigurationFile` skapar är en läsbar textfil som innehåller en hash-tabell av konfigurations egenskaper och värden för sessioner.</span><span class="sxs-lookup"><span data-stu-id="01779-109">The session configuration file that `New-PSSessionConfigurationFile` creates is a human-readable text file that contains a hash table of the session configuration properties and values.</span></span> <span data-ttu-id="01779-110">Filen har fil `.pssc` namns tillägget.</span><span class="sxs-lookup"><span data-stu-id="01779-110">The file has a `.pssc` filename extension.</span></span>

<span data-ttu-id="01779-111">Alla parametrar för `New-PSSessionConfigurationFile` är valfria, förutom parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="01779-111">All parameters of `New-PSSessionConfigurationFile` are optional, except for the **Path** parameter.</span></span>
<span data-ttu-id="01779-112">Om du utelämnar en parameter kommenteras motsvarande nyckel i konfigurations filen för sessionen, förutom där anges i parameter beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="01779-112">If you omit a parameter, the corresponding key in the session configuration file is commented-out, except where noted in the parameter description.</span></span>

<span data-ttu-id="01779-113">En sessionsinformation, som även kallas slut punkt, är en samling inställningar på den lokala datorn som definierar miljön för PowerShell-sessioner (**PSSessions**) som ansluter till datorn.</span><span class="sxs-lookup"><span data-stu-id="01779-113">A session configuration, also known as an endpoint, is a collection of settings on the local computer that define the environment for PowerShell sessions (**PSSessions**) that connect to the computer.</span></span> <span data-ttu-id="01779-114">Alla **PSSessions** använder en konfiguration av sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-114">All **PSSessions** use a session configuration.</span></span> <span data-ttu-id="01779-115">Om du vill ange en viss sessionsinformation använder du parametern **ConfigurationName** för cmdletar som skapar en session, t. ex `New-PSSession` . cmdleten.</span><span class="sxs-lookup"><span data-stu-id="01779-115">To specify a particular session configuration, use the **ConfigurationName** parameter of cmdlets that create a session, such as the `New-PSSession` cmdlet.</span></span>

<span data-ttu-id="01779-116">En konfigurations fil för sessionen gör det enkelt att definiera en sessions konfiguration utan komplicerade skript eller kod sammansättningar.</span><span class="sxs-lookup"><span data-stu-id="01779-116">A session configuration file makes it easy to define a session configuration without complex scripts or code assemblies.</span></span> <span data-ttu-id="01779-117">Inställningarna i filen används med valfritt start skript och eventuella sammansättningar i konfigurationen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-117">The settings in the file are used with the optional startup script and any assemblies in the session configuration.</span></span>

<span data-ttu-id="01779-118">Mer information om sessionsinställningar och konfigurationsfiler för sessioner finns i [about_Session_Configurations](About/about_Session_Configurations.md) och [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span><span class="sxs-lookup"><span data-stu-id="01779-118">For more information about session configurations and session configuration files, see [about_Session_Configurations](About/about_Session_Configurations.md) and [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>

<span data-ttu-id="01779-119">Denna cmdlet introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="01779-119">This cmdlet was introduced in PowerShell 3.0.</span></span>

## <span data-ttu-id="01779-120">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="01779-120">EXAMPLES</span></span>

### <span data-ttu-id="01779-121">Exempel 1: skapa och använda en nolanguage-session</span><span class="sxs-lookup"><span data-stu-id="01779-121">Example 1: Creating and using a NoLanguage session</span></span>

<span data-ttu-id="01779-122">Det här exemplet visar hur du skapar och effekterna av att använda en icke-språk-session.</span><span class="sxs-lookup"><span data-stu-id="01779-122">This example show how to create and the effects of using a no-language session.</span></span>

<span data-ttu-id="01779-123">Stegen är:</span><span class="sxs-lookup"><span data-stu-id="01779-123">The steps include:</span></span>

1. <span data-ttu-id="01779-124">Skapa en ny konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="01779-124">Create a new configuration file.</span></span>
1. <span data-ttu-id="01779-125">Registrera konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="01779-125">Register the configuration.</span></span>
1. <span data-ttu-id="01779-126">Skapa en ny session som använder-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="01779-126">Create a new session that uses the configuration.</span></span>
1. <span data-ttu-id="01779-127">Kör kommandon i den nya sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-127">Run commands in that new session.</span></span>

<span data-ttu-id="01779-128">Om du vill köra kommandona i det här exemplet startar du PowerShell med alternativet Kör som administratör.</span><span class="sxs-lookup"><span data-stu-id="01779-128">To run the commands in this example, start PowerShell by using the Run as administrator option.</span></span> <span data-ttu-id="01779-129">Det här alternativet krävs för att köra `Register-PSSessionConfiguration` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="01779-129">This option is required to run the `Register-PSSessionConfiguration` cmdlet.</span></span>

```powershell
New-PSSessionConfigurationFile -Path .\NoLanguage.pssc -LanguageMode NoLanguage
Register-PSSessionConfiguration -Path .\NoLanguage.pssc -Name NoLanguage -Force
$NoLanguageSession = New-PSSession -ComputerName Srv01 -ConfigurationName NoLanguage
Invoke-Command -Session $NoLanguageSession -ScriptBlock {
  if ((Get-Date) -lt '1January2099') {'Before'} else {'After'}
}
```

```Output
The syntax is not supported by this runspace. This might be because it is in no-language mode.
    + CategoryInfo          : ParserError: (if ((Get-Date) ...') {'Before'}  :String) [], ParseException
    + FullyQualifiedErrorId : ScriptsNotAllowed
    + PSComputerName        : localhost
```

<span data-ttu-id="01779-130">I det här exemplet `Invoke-Command` Miss lyckas det eftersom **LanguageMode** är inställt på **nolanguage**.</span><span class="sxs-lookup"><span data-stu-id="01779-130">In this example, the `Invoke-Command` fails because the **LanguageMode** is set to **NoLanguage**.</span></span>

### <span data-ttu-id="01779-131">Exempel 2: skapa och använda en RestrictedLanguage-session</span><span class="sxs-lookup"><span data-stu-id="01779-131">Example 2: Creating and using a RestrictedLanguage session</span></span>

<span data-ttu-id="01779-132">Det här exemplet visar hur du skapar och effekterna av att använda en icke-språk-session.</span><span class="sxs-lookup"><span data-stu-id="01779-132">This example show how to create and the effects of using a no-language session.</span></span>

<span data-ttu-id="01779-133">Stegen är:</span><span class="sxs-lookup"><span data-stu-id="01779-133">The steps include:</span></span>

1. <span data-ttu-id="01779-134">Skapa en ny konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="01779-134">Create a new configuration file.</span></span>
1. <span data-ttu-id="01779-135">Registrera konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="01779-135">Register the configuration.</span></span>
1. <span data-ttu-id="01779-136">Skapa en ny session som använder-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="01779-136">Create a new session that uses the configuration.</span></span>
1. <span data-ttu-id="01779-137">Kör kommandon i den nya sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-137">Run commands in that new session.</span></span>

<span data-ttu-id="01779-138">Om du vill köra kommandona i det här exemplet startar du PowerShell med alternativet Kör som administratör.</span><span class="sxs-lookup"><span data-stu-id="01779-138">To run the commands in this example, start PowerShell by using the Run as administrator option.</span></span> <span data-ttu-id="01779-139">Det här alternativet krävs för att köra `Register-PSSessionConfiguration` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="01779-139">This option is required to run the `Register-PSSessionConfiguration` cmdlet.</span></span>

```powershell
New-PSSessionConfigurationFile -Path .\NoLanguage.pssc -LanguageMode RestrictedLanguage
Register-PSSessionConfiguration -Path .\NoLanguage.pssc -Name RestrictedLanguage -Force
$RestrictedSession = New-PSSession -ComputerName Srv01 -ConfigurationName RestrictedLanguage
Invoke-Command -Session $RestrictedSession -ScriptBlock {
  if ((Get-Date) -lt '1January2099') {'Before'} else {'After'}
}
```

```Output
Before
```

<span data-ttu-id="01779-140">I det här exemplet `Invoke-Command` lyckas det eftersom **LanguageMode** är inställt på **RestrictedLanguage**.</span><span class="sxs-lookup"><span data-stu-id="01779-140">In this example, the `Invoke-Command` succeeds because the **LanguageMode** is set to **RestrictedLanguage**.</span></span>

### <span data-ttu-id="01779-141">Exempel 3: ändra en konfigurations fil för sessionen</span><span class="sxs-lookup"><span data-stu-id="01779-141">Example 3: Changing a Session Configuration File</span></span>

<span data-ttu-id="01779-142">Det här exemplet visar hur du ändrar den konfigurations fil för sessionen som används i en befintlig session med namnet "ITTasks".</span><span class="sxs-lookup"><span data-stu-id="01779-142">This example shows how to change the session configuration file that is used in an existing session named "ITTasks".</span></span> <span data-ttu-id="01779-143">Tidigare hade dessa sessioner bara de viktigaste modulerna och en intern **ITTasks** -modul.</span><span class="sxs-lookup"><span data-stu-id="01779-143">Previously, these sessions had only the core modules and an internal **ITTasks** module.</span></span> <span data-ttu-id="01779-144">Administratören vill lägga till **PSScheduledJob** -modulen i sessioner som skapats med hjälp av ITTasks-sessionens konfiguration.</span><span class="sxs-lookup"><span data-stu-id="01779-144">The administrator wants to add the **PSScheduledJob** module to sessions created by using the ITTasks session configuration.</span></span>

```powershell
New-PSSessionConfigurationFile -Path .\New-ITTasks.pssc -ModulesToImport Microsoft*, ITTasks, PSScheduledJob
Set-PSSessionConfiguration -Name ITTasks -Path .\New-ITTasks.pssc
```

<span data-ttu-id="01779-145">`New-PSSessionConfigurationFile`Cmdleten för att skapa en konfigurations fil för sessionen som importerar de nödvändiga modulerna.</span><span class="sxs-lookup"><span data-stu-id="01779-145">The `New-PSSessionConfigurationFile` cmdlet to create a session configuration file that imports the required modules.</span></span> <span data-ttu-id="01779-146">`Set-PSSessionConfiguration`Cmdlet: en ersätter den aktuella konfigurations filen med den nya.</span><span class="sxs-lookup"><span data-stu-id="01779-146">The `Set-PSSessionConfiguration` cmdlet replaces the current configuration file with the new one.</span></span> <span data-ttu-id="01779-147">Den här nya konfigurationen påverkar endast nya sessioner som skapats efter ändringen.</span><span class="sxs-lookup"><span data-stu-id="01779-147">This new configuration only affects new sessions created after the change.</span></span>
<span data-ttu-id="01779-148">Befintliga "ITTasks"-sessioner påverkas inte.</span><span class="sxs-lookup"><span data-stu-id="01779-148">Existing "ITTasks" sessions are not affected.</span></span>

### <span data-ttu-id="01779-149">Exempel 4: redigera en konfigurations fil för sessionen</span><span class="sxs-lookup"><span data-stu-id="01779-149">Example 4: Editing a Session Configuration File</span></span>

<span data-ttu-id="01779-150">Det här exemplet visar hur du ändrar en sessionsinformation genom att redigera den aktiva sessionens konfigurations kopia av konfigurations filen.</span><span class="sxs-lookup"><span data-stu-id="01779-150">This example shows how to change a session configuration by editing the active session configuration copy of the configuration file.</span></span> <span data-ttu-id="01779-151">Om du vill ändra konfigurations filen för sessionen måste du ha fullständig behörighet till filen.</span><span class="sxs-lookup"><span data-stu-id="01779-151">To modify the session configuration copy of the configuration file, you must have full control access to the file.</span></span> <span data-ttu-id="01779-152">Detta kan kräva att du ändrar behörigheterna för filen.</span><span class="sxs-lookup"><span data-stu-id="01779-152">This may require you to change the permissions on the file.</span></span>

<span data-ttu-id="01779-153">I det här scenariot vill vi lägga till ett nytt alias för `Select-String` cmdleten genom att redigera den aktiva konfigurations filen.</span><span class="sxs-lookup"><span data-stu-id="01779-153">In this scenario, we want to add a new alias for the `Select-String` cmdlet by editing the active configuration file.</span></span>

<span data-ttu-id="01779-154">Exempel koden nedan utför följande steg för att göra den här ändringen:</span><span class="sxs-lookup"><span data-stu-id="01779-154">The example code below performs the following steps to make this change:</span></span>

1. <span data-ttu-id="01779-155">Hämta konfigurations filens sökväg för ITConfig-sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-155">Get the configuration file path for the ITConfig session.</span></span>
1. <span data-ttu-id="01779-156">Användaren redigerar konfigurations filen med **Notepad.exe** för att ändra **AliasDefinitions** -värdet enligt följande: `AliasDefinitions = @(@{Name='slst';Value='Select-String'})` .</span><span class="sxs-lookup"><span data-stu-id="01779-156">The user edits the configuration file using **Notepad.exe** to change the **AliasDefinitions** value as follows: `AliasDefinitions = @(@{Name='slst';Value='Select-String'})`.</span></span>
1. <span data-ttu-id="01779-157">Testa den uppdaterade konfigurations filen.</span><span class="sxs-lookup"><span data-stu-id="01779-157">Test the updated configuration file.</span></span>

```powershell
$ITConfig = Get-PSSessionConfiguration -Name ITConfig
notepad.exe $ITConfig.ConfigFilePath
Test-PSSessionConfigurationFile -Path $ITConfig.ConfigFilePath
```

```Output
True
```

<span data-ttu-id="01779-158">Använd **verbose** -parametern med `Test-PSSessionConfigurationFile` för att visa eventuella fel som har identifierats.</span><span class="sxs-lookup"><span data-stu-id="01779-158">Use the **Verbose** parameter with `Test-PSSessionConfigurationFile` to display any errors that are detected.</span></span> <span data-ttu-id="01779-159">Cmdleten returnerar `$True` om inga fel har identifierats i filen.</span><span class="sxs-lookup"><span data-stu-id="01779-159">The cmdlet returns `$True` if no errors are detected in the file.</span></span>

### <span data-ttu-id="01779-160">Exempel 5: skapa en exempel konfigurations fil</span><span class="sxs-lookup"><span data-stu-id="01779-160">Example 5: Create a sample configuration file</span></span>

<span data-ttu-id="01779-161">I det här exemplet visas ett `New-PSSessionConfigurationFile` kommando som använder alla cmdlet-parametrar.</span><span class="sxs-lookup"><span data-stu-id="01779-161">This example shows a `New-PSSessionConfigurationFile` command that uses all the cmdlet parameters.</span></span>
<span data-ttu-id="01779-162">Den ingår för att visa rätt indataformat för varje parameter.</span><span class="sxs-lookup"><span data-stu-id="01779-162">It is included to show the correct input format for each parameter.</span></span>

<span data-ttu-id="01779-163">Den resulterande SampleFile. PSSC visas i utdata.</span><span class="sxs-lookup"><span data-stu-id="01779-163">The resulting SampleFile.pssc is displayed in the output.</span></span>

```powershell
$configSettings = @{
    Path = '.\SampleFile.pssc'
    SchemaVersion = '1.0.0.0'
    Author = 'User01'
    Copyright = '(c) Fabrikam Corporation. All rights reserved.'
    CompanyName = 'Fabrikam Corporation'
    Description = 'This is a sample file.'
    ExecutionPolicy = 'AllSigned'
    PowerShellVersion = '3.0'
    LanguageMode = 'FullLanguage'
    SessionType = 'Default'
    EnvironmentVariables = @{TESTSHARE='\\Test2\Test'}
    ModulesToImport = @{ModuleName='PSScheduledJob'; ModuleVersion='1.0.0.0'; GUID='50cdb55f-5ab7-489f-9e94-4ec21ff51e59'},'PSDiagnostics'
    AssembliesToLoad = 'System.Web.Services','FSharp.Compiler.CodeDom.dll'
    TypesToProcess = 'Types1.ps1xml','Types2.ps1xml'
    FormatsToProcess = 'CustomFormats.ps1xml'
    ScriptsToProcess = 'Get-Inputs.ps1'
    AliasDefinitions = @{Name='hlp';Value='Get-Help';Description='Gets help.';Options='AllScope'},
        @{Name='Update';Value='Update-Help';Description='Updates help';Options='ReadOnly'}
    FunctionDefinitions = @{Name='Get-Function';ScriptBlock={Get-Command -CommandType Function};Options='ReadOnly'}
    VariableDefinitions = @{Name='WarningPreference';Value='SilentlyContinue'}
    VisibleAliases = 'c*','g*','i*','s*'
    VisibleCmdlets = 'Get*'
    VisibleFunctions = 'Get*'
    VisibleProviders = 'FileSystem','Function','Variable'
    RunAsVirtualAccount = $true
    RunAsVirtualAccountGroups = 'Backup Operators'
}
New-PSSessionConfigurationFile @configSettings
Get-Content SampleFile.pssc
```

```Output
@{

# Version number of the schema used for this document
SchemaVersion = '1.0.0.0'

# ID used to uniquely identify this document
GUID = '1caeff7f-27ca-4360-97cf-37846f594235'

# Author of this document
Author = 'User01'

# Description of the functionality provided by these settings
Description = 'This is a sample file.'

# Company associated with this document
CompanyName = 'Fabrikam Corporation'

# Copyright statement for this document
Copyright = '(c) Fabrikam Corporation. All rights reserved.'

# Session type defaults to apply for this session configuration. Can be 'RestrictedRemoteServer' (recommended), 'Empty', or 'Default'
SessionType = 'Default'

# Directory to place session transcripts for this session configuration
# TranscriptDirectory = 'C:\Transcripts\'

# Whether to run this session configuration as the machine's (virtual) administrator account
RunAsVirtualAccount = $true

# Groups associated with machine's (virtual) administrator account
RunAsVirtualAccountGroups = 'Backup Operators'

# Scripts to run when applied to a session
ScriptsToProcess = 'Get-Inputs.ps1'

# User roles (security groups), and the role capabilities that should be applied to them when applied to a session
# RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\SqlManaged' = @{ RoleCapabilityFiles = 'C:\RoleCapability\SqlManaged.psrc' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }

# Language mode to apply when applied to a session. Can be 'NoLanguage' (recommended), 'RestrictedLanguage', 'ConstrainedLanguage', or 'FullLanguage'
LanguageMode = 'FullLanguage'

# Execution policy to apply when applied to a session
ExecutionPolicy = 'AllSigned'

# Version of the PowerShell engine to use when applied to a session
PowerShellVersion = '3.0'

# Modules to import when applied to a session
ModulesToImport = @{
    'GUID' = '50cdb55f-5ab7-489f-9e94-4ec21ff51e59'
    'ModuleName' = 'PSScheduledJob'
    'ModuleVersion' = '1.0.0.0' }, 'PSDiagnostics'

# Aliases to make visible when applied to a session
VisibleAliases = 'c*', 'g*', 'i*', 's*'

# Cmdlets to make visible when applied to a session
VisibleCmdlets = 'Get*'

# Functions to make visible when applied to a session
VisibleFunctions = 'Get*'

# Providers to make visible when applied to a session
VisibleProviders = 'FileSystem', 'Function', 'Variable'

# Aliases to be defined when applied to a session
AliasDefinitions = @{
    'Description' = 'Gets help.'
    'Name' = 'hlp'
    'Options' = 'AllScope'
    'Value' = 'Get-Help' }, @{
    'Description' = 'Updates help'
    'Name' = 'Update'
    'Options' = 'ReadOnly'
    'Value' = 'Update-Help' }

# Functions to define when applied to a session
FunctionDefinitions = @{
    'Name' = 'Get-Function'
    'Options' = 'ReadOnly'
    'ScriptBlock' = {Get-Command -CommandType Function} }

# Variables to define when applied to a session
VariableDefinitions = @{
    'Name' = 'WarningPreference'
    'Value' = 'SilentlyContinue' }

# Environment variables to define when applied to a session
EnvironmentVariables = @{
    'TESTSHARE' = '\\Test2\Test' }

# Type files (.ps1xml) to load when applied to a session
TypesToProcess = 'Types1.ps1xml', 'Types2.ps1xml'

# Format files (.ps1xml) to load when applied to a session
FormatsToProcess = 'CustomFormats.ps1xml'

# Assemblies to load when applied to a session
AssembliesToLoad = 'System.Web.Services', 'FSharp.Compiler.CodeDom.dll'

}
```

## <span data-ttu-id="01779-164">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="01779-164">PARAMETERS</span></span>

### <span data-ttu-id="01779-165">-AliasDefinitions</span><span class="sxs-lookup"><span data-stu-id="01779-165">-AliasDefinitions</span></span>

<span data-ttu-id="01779-166">Lägger till angivna alias till sessioner som använder sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-166">Adds the specified aliases to sessions that use the session configuration.</span></span> <span data-ttu-id="01779-167">Ange en hash-tabell med följande nycklar:</span><span class="sxs-lookup"><span data-stu-id="01779-167">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="01779-168">Namn – namnet på aliaset.</span><span class="sxs-lookup"><span data-stu-id="01779-168">Name - Name of the alias.</span></span> <span data-ttu-id="01779-169">Den här nyckeln är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="01779-169">This key is required.</span></span>
- <span data-ttu-id="01779-170">Value – kommandot som aliaset representerar.</span><span class="sxs-lookup"><span data-stu-id="01779-170">Value - The command that the alias represents.</span></span> <span data-ttu-id="01779-171">Den här nyckeln är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="01779-171">This key is required.</span></span>
- <span data-ttu-id="01779-172">Beskrivning – en text sträng som beskriver aliaset.</span><span class="sxs-lookup"><span data-stu-id="01779-172">Description - A text string that describes the alias.</span></span> <span data-ttu-id="01779-173">Den här nyckeln är valfri.</span><span class="sxs-lookup"><span data-stu-id="01779-173">This key is optional.</span></span>
- <span data-ttu-id="01779-174">Alternativ-Alternativ för alias.</span><span class="sxs-lookup"><span data-stu-id="01779-174">Options - Alias options.</span></span> <span data-ttu-id="01779-175">Den här nyckeln är valfri.</span><span class="sxs-lookup"><span data-stu-id="01779-175">This key is optional.</span></span> <span data-ttu-id="01779-176">Standardvärdet är **none**.</span><span class="sxs-lookup"><span data-stu-id="01779-176">The default value is **None**.</span></span> <span data-ttu-id="01779-177">De acceptabla värdena för den här parametern är: none, ReadOnly, Constant, Private eller AllScope.</span><span class="sxs-lookup"><span data-stu-id="01779-177">The acceptable values for this parameter are: None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="01779-178">Exempel: `@{Name='hlp';Value='Get-Help';Description='Gets help';Options='ReadOnly'}`</span><span class="sxs-lookup"><span data-stu-id="01779-178">For example: `@{Name='hlp';Value='Get-Help';Description='Gets help';Options='ReadOnly'}`</span></span>

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="01779-179">-AssembliesToLoad</span><span class="sxs-lookup"><span data-stu-id="01779-179">-AssembliesToLoad</span></span>

<span data-ttu-id="01779-180">Anger de sammansättningar som ska läsas in i de sessioner som använder-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="01779-180">Specifies the assemblies to load into the sessions that use the session configuration.</span></span>

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

### <span data-ttu-id="01779-181">– Författare</span><span class="sxs-lookup"><span data-stu-id="01779-181">-Author</span></span>

<span data-ttu-id="01779-182">Anger författaren till sessionen eller konfigurations filen.</span><span class="sxs-lookup"><span data-stu-id="01779-182">Specifies the author of the session configuration or the configuration file.</span></span> <span data-ttu-id="01779-183">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="01779-183">The default is the current user.</span></span> <span data-ttu-id="01779-184">Värdet för den här parametern visas i konfigurations filen för sessionen, men det är inte en egenskap för sessionens konfigurations objekt.</span><span class="sxs-lookup"><span data-stu-id="01779-184">The value of this parameter is visible in the session configuration file, but it is not a property of the session configuration object.</span></span>

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

### <span data-ttu-id="01779-185">-Företags namn</span><span class="sxs-lookup"><span data-stu-id="01779-185">-CompanyName</span></span>

<span data-ttu-id="01779-186">Anger det företag som skapade konfigurationen av sessionen eller konfigurations filen.</span><span class="sxs-lookup"><span data-stu-id="01779-186">Specifies the company that created the session configuration or the configuration file.</span></span> <span data-ttu-id="01779-187">Standardvärdet är **Okänt**.</span><span class="sxs-lookup"><span data-stu-id="01779-187">The default value is **Unknown**.</span></span> <span data-ttu-id="01779-188">Värdet för den här parametern visas i konfigurations filen för sessionen, men det är inte en egenskap för sessionens konfigurations objekt.</span><span class="sxs-lookup"><span data-stu-id="01779-188">The value of this parameter is visible in the session configuration file, but it is not a property of the session configuration object.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: Unknown
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="01779-189">– Copyright</span><span class="sxs-lookup"><span data-stu-id="01779-189">-Copyright</span></span>

<span data-ttu-id="01779-190">Anger en Copyright-sessionens konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="01779-190">Specifies a copyright the session configuration file.</span></span> <span data-ttu-id="01779-191">Värdet för den här parametern visas i konfigurations filen för sessionen, men det är inte en egenskap för sessionens konfigurations objekt.</span><span class="sxs-lookup"><span data-stu-id="01779-191">The value of this parameter is visible in the session configuration file, but it is not a property of the session configuration object.</span></span>

<span data-ttu-id="01779-192">Om du utelämnar den här parametern `New-PSSessionConfigurationFile` genererar en Copyright-instruktion med hjälp av värdet för parametern **Author** .</span><span class="sxs-lookup"><span data-stu-id="01779-192">If you omit this parameter, `New-PSSessionConfigurationFile` generates a copyright statement by using the value of the **Author** parameter.</span></span>

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

### <span data-ttu-id="01779-193">-Beskrivning</span><span class="sxs-lookup"><span data-stu-id="01779-193">-Description</span></span>

<span data-ttu-id="01779-194">Anger en beskrivning av konfigurationen av sessionen eller sessionens konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="01779-194">Specifies a description of the session configuration or the session configuration file.</span></span> <span data-ttu-id="01779-195">Värdet för den här parametern visas i konfigurations filen för sessionen, men det är inte en egenskap för sessionens konfigurations objekt.</span><span class="sxs-lookup"><span data-stu-id="01779-195">The value of this parameter is visible in the session configuration file, but it is not a property of the session configuration object.</span></span>

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

### <span data-ttu-id="01779-196">– EnvironmentVariables</span><span class="sxs-lookup"><span data-stu-id="01779-196">-EnvironmentVariables</span></span>

<span data-ttu-id="01779-197">Lägger till miljövariabler i sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-197">Adds environment variables to the session.</span></span> <span data-ttu-id="01779-198">Ange en hash-tabell där nycklarna är miljö variabel namnen och värdena är Miljövariabelns värden.</span><span class="sxs-lookup"><span data-stu-id="01779-198">Enter a hash table in which the keys are the environment variable names and the values are the environment variable values.</span></span>

<span data-ttu-id="01779-199">Exempel: `EnvironmentVariables=@{TestShare='\\Server01\TestShare'}`</span><span class="sxs-lookup"><span data-stu-id="01779-199">For example: `EnvironmentVariables=@{TestShare='\\Server01\TestShare'}`</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="01779-200">– ExecutionPolicy</span><span class="sxs-lookup"><span data-stu-id="01779-200">-ExecutionPolicy</span></span>

<span data-ttu-id="01779-201">Anger körnings principen för sessioner som använder sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-201">Specifies the execution policy of sessions that use the session configuration.</span></span> <span data-ttu-id="01779-202">Om du utelämnar den här parametern, är värdet för **ExecutionPolicy** -nyckeln i konfigurations filen för sessionen **begränsad**.</span><span class="sxs-lookup"><span data-stu-id="01779-202">If you omit this parameter, the value of the **ExecutionPolicy** key in the session configuration file is **Restricted**.</span></span> <span data-ttu-id="01779-203">Information om körnings principer i PowerShell finns [about_Execution_Policies](about/about_Execution_Policies.md).</span><span class="sxs-lookup"><span data-stu-id="01779-203">For information about execution policies in PowerShell, see [about_Execution_Policies](about/about_Execution_Policies.md).</span></span>

```yaml
Type: Microsoft.PowerShell.ExecutionPolicy
Parameter Sets: (All)
Aliases:
Accepted values: Unrestricted, RemoteSigned, AllSigned, Restricted, Default, Bypass, Undefined

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="01779-204">-FormatsToProcess</span><span class="sxs-lookup"><span data-stu-id="01779-204">-FormatsToProcess</span></span>

<span data-ttu-id="01779-205">Anger de formateringsattribut (. ps1xml) som körs i sessioner som använder sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-205">Specifies the formatting files (.ps1xml) that run in sessions that use the session configuration.</span></span>
<span data-ttu-id="01779-206">Värdet för den här parametern måste vara en fullständig eller absolut sökväg till filerna.</span><span class="sxs-lookup"><span data-stu-id="01779-206">The value of this parameter must be a full or absolute path of the formatting files.</span></span>

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

### <span data-ttu-id="01779-207">– Fullständig</span><span class="sxs-lookup"><span data-stu-id="01779-207">-Full</span></span>

<span data-ttu-id="01779-208">Anger att den här åtgärden innehåller alla möjliga konfigurations egenskaper i sessionens konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="01779-208">Indicates that this operation includes all possible configuration properties in the session configuration file.</span></span>

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

### <span data-ttu-id="01779-209">-FunctionDefinitions</span><span class="sxs-lookup"><span data-stu-id="01779-209">-FunctionDefinitions</span></span>

<span data-ttu-id="01779-210">Lägger till angivna funktioner till sessioner som använder-sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-210">Adds the specified functions to sessions that use the session configuration.</span></span> <span data-ttu-id="01779-211">Ange en hash-tabell med följande nycklar:</span><span class="sxs-lookup"><span data-stu-id="01779-211">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="01779-212">Namn – namnet på funktionen.</span><span class="sxs-lookup"><span data-stu-id="01779-212">Name - Name of the function.</span></span> <span data-ttu-id="01779-213">Den här nyckeln är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="01779-213">This key is required.</span></span>
- <span data-ttu-id="01779-214">Script block – Function-brödtext.</span><span class="sxs-lookup"><span data-stu-id="01779-214">ScriptBlock - Function body.</span></span> <span data-ttu-id="01779-215">Ange ett skript block.</span><span class="sxs-lookup"><span data-stu-id="01779-215">Enter a script block.</span></span> <span data-ttu-id="01779-216">Den här nyckeln är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="01779-216">This key is required.</span></span>
- <span data-ttu-id="01779-217">Alternativ-funktions alternativ.</span><span class="sxs-lookup"><span data-stu-id="01779-217">Options - Function options.</span></span> <span data-ttu-id="01779-218">Den här nyckeln är valfri.</span><span class="sxs-lookup"><span data-stu-id="01779-218">This key is optional.</span></span> <span data-ttu-id="01779-219">Standardvärdet är **none**.</span><span class="sxs-lookup"><span data-stu-id="01779-219">The default value is **None**.</span></span> <span data-ttu-id="01779-220">De acceptabla värdena för den här parametern är: none, ReadOnly, Constant, Private eller AllScope.</span><span class="sxs-lookup"><span data-stu-id="01779-220">The acceptable values for this parameter are: None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="01779-221">Exempel: `@{Name='Get-PowerShellProcess';ScriptBlock={Get-Process PowerShell};Options='AllScope'}`</span><span class="sxs-lookup"><span data-stu-id="01779-221">For example: `@{Name='Get-PowerShellProcess';ScriptBlock={Get-Process PowerShell};Options='AllScope'}`</span></span>

```yaml
Type: System.Collections.IDictionary[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="01779-222">– GroupManagedServiceAccount</span><span class="sxs-lookup"><span data-stu-id="01779-222">-GroupManagedServiceAccount</span></span>

<span data-ttu-id="01779-223">Konfigurerar sessioner som använder den här konfigurationen för att köras under kontexten för det angivna grupphanterade tjänst kontot.</span><span class="sxs-lookup"><span data-stu-id="01779-223">Configures sessions using this session configuration to run under the context of the specified Group Managed Service Account.</span></span> <span data-ttu-id="01779-224">Datorn där den här konfigurationen för sessionen registreras måste ha behörighet att begära gMSA-lösenordet för att sessioner ska kunna skapas.</span><span class="sxs-lookup"><span data-stu-id="01779-224">The machine where this session configuration is registered must have permission to request the gMSA password in order for sessions to be created successfully.</span></span> <span data-ttu-id="01779-225">Det går inte att använda det här fältet med parametern **RunAsVirtualAccount** .</span><span class="sxs-lookup"><span data-stu-id="01779-225">This field cannot be used with the **RunAsVirtualAccount** parameter.</span></span>

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

### <span data-ttu-id="01779-226">-GUID</span><span class="sxs-lookup"><span data-stu-id="01779-226">-Guid</span></span>

<span data-ttu-id="01779-227">Anger en unik identifierare för sessionens konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="01779-227">Specifies a unique identifier for the session configuration file.</span></span> <span data-ttu-id="01779-228">Om du utelämnar den här parametern `New-PSSessionConfigurationFile` genererar ett GUID för filen.</span><span class="sxs-lookup"><span data-stu-id="01779-228">If you omit this parameter, `New-PSSessionConfigurationFile` generates a GUID for the file.</span></span> <span data-ttu-id="01779-229">Om du vill skapa ett nytt GUID i PowerShell skriver du `New-Guid` .</span><span class="sxs-lookup"><span data-stu-id="01779-229">To create a new GUID in PowerShell, type `New-Guid`.</span></span>

```yaml
Type: System.Guid
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="01779-230">-LanguageMode</span><span class="sxs-lookup"><span data-stu-id="01779-230">-LanguageMode</span></span>

<span data-ttu-id="01779-231">Bestämmer vilka element i PowerShell-språket som tillåts i sessioner som använder den här konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="01779-231">Determines which elements of the PowerShell language are permitted in sessions that use this session configuration.</span></span> <span data-ttu-id="01779-232">Du kan använda den här parametern för att begränsa vilka kommandon som specifika användare kan köra på datorn.</span><span class="sxs-lookup"><span data-stu-id="01779-232">You can use this parameter to restrict the commands that particular users can run on the computer.</span></span>

<span data-ttu-id="01779-233">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="01779-233">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="01779-234">FullLanguage – alla språk element är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="01779-234">FullLanguage - All language elements are permitted.</span></span>
- <span data-ttu-id="01779-235">ConstrainedLanguage-kommandon som innehåller skript som ska utvärderas tillåts inte.</span><span class="sxs-lookup"><span data-stu-id="01779-235">ConstrainedLanguage - Commands that contain scripts to be evaluated are not allowed.</span></span> <span data-ttu-id="01779-236">ConstrainedLanguage-läget begränsar användar åtkomsten till Microsoft .NET Ramverks typer, objekt eller metoder.</span><span class="sxs-lookup"><span data-stu-id="01779-236">The ConstrainedLanguage mode restricts user access to Microsoft .NET Framework types, objects, or methods.</span></span>
- <span data-ttu-id="01779-237">Nolanguage – användarna kan köra cmdlets och functions, men får inte använda några språk element, till exempel skript block, variabler eller operatörer.</span><span class="sxs-lookup"><span data-stu-id="01779-237">NoLanguage - Users may run cmdlets and functions, but are not permitted to use any language elements, such as script blocks, variables, or operators.</span></span>
- <span data-ttu-id="01779-238">RestrictedLanguage – användarna kan köra cmdlets och functions, men får inte använda skript block eller variabler förutom följande tillåtna variabler: `$PSCulture` , `$PSUICulture` ,, `$True` `$False` , och `$Null` .</span><span class="sxs-lookup"><span data-stu-id="01779-238">RestrictedLanguage - Users may run cmdlets and functions, but are not permitted to use script blocks or variables except for the following permitted variables: `$PSCulture`, `$PSUICulture`, `$True`, `$False`, and `$Null`.</span></span> <span data-ttu-id="01779-239">Användare får bara använda de grundläggande jämförelse operatorerna ( `-eq` , `-gt` , `-lt` ).</span><span class="sxs-lookup"><span data-stu-id="01779-239">Users may use only the basic comparison operators (`-eq`, `-gt`, `-lt`).</span></span> <span data-ttu-id="01779-240">Tilldelnings instruktioner, egenskaps referenser och metod anrop är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="01779-240">Assignment statements, property references, and method calls are not permitted.</span></span>

<span data-ttu-id="01779-241">Standardvärdet för parametern **LanguageMode** är beroende av värdet för parametern **SessionType** .</span><span class="sxs-lookup"><span data-stu-id="01779-241">The default value of the **LanguageMode** parameter depends on the value of the **SessionType** parameter.</span></span>

- <span data-ttu-id="01779-242">Tomt – inget språk</span><span class="sxs-lookup"><span data-stu-id="01779-242">Empty - NoLanguage</span></span>
- <span data-ttu-id="01779-243">RestrictedRemoteServer – inget språk</span><span class="sxs-lookup"><span data-stu-id="01779-243">RestrictedRemoteServer - NoLanguage</span></span>
- <span data-ttu-id="01779-244">Standard – FullLanguage</span><span class="sxs-lookup"><span data-stu-id="01779-244">Default - FullLanguage</span></span>

```yaml
Type: System.Management.Automation.PSLanguageMode
Parameter Sets: (All)
Aliases:
Accepted values: FullLanguage, RestrictedLanguage, NoLanguage, ConstrainedLanguage

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="01779-245">-ModulesToImport</span><span class="sxs-lookup"><span data-stu-id="01779-245">-ModulesToImport</span></span>

<span data-ttu-id="01779-246">Anger moduler och snapin-moduler som importeras automatiskt till sessioner som använder-sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-246">Specifies the modules and snap-ins that are automatically imported into sessions that use the session configuration.</span></span>

<span data-ttu-id="01779-247">Som standard importeras bara snapin-modulen **Microsoft. PowerShell. Core** till fjärrsessioner, men om inte cmdletarna undantas kan användarna använda `Import-Module` `Add-PSSnapin` cmdletarna och för att lägga till moduler och snapin-moduler till sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-247">By default, only the **Microsoft.PowerShell.Core** snap-in is imported into remote sessions, but unless the cmdlets are excluded, users can use the `Import-Module` and `Add-PSSnapin` cmdlets to add modules and snap-ins to the session.</span></span>

<span data-ttu-id="01779-248">Varje modul eller snapin-modul i värdet för den här parametern kan representeras av en sträng eller som en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="01779-248">Each module or snap-in in the value of this parameter can be represented by a string or as a hash table.</span></span> <span data-ttu-id="01779-249">En modul sträng består bara av namnet på modulen eller snapin-modulen.</span><span class="sxs-lookup"><span data-stu-id="01779-249">A module string consists only of the name of the module or snap-in.</span></span> <span data-ttu-id="01779-250">En modul hash-tabell kan innehålla **Modulnamn**, **ModuleVersion** och **GUID** -nycklar.</span><span class="sxs-lookup"><span data-stu-id="01779-250">A module hash table can include **ModuleName**, **ModuleVersion**, and **GUID** keys.</span></span> <span data-ttu-id="01779-251">Endast nyckeln **Modulnamn** krävs.</span><span class="sxs-lookup"><span data-stu-id="01779-251">Only the **ModuleName** key is required.</span></span>

<span data-ttu-id="01779-252">Följande värde består till exempel av en sträng och en hash-tabell.</span><span class="sxs-lookup"><span data-stu-id="01779-252">For example, the following value consists of a string and a hash table.</span></span> <span data-ttu-id="01779-253">En valfri kombination av strängar och hash-tabeller, i vilken ordning som helst, är giltig.</span><span class="sxs-lookup"><span data-stu-id="01779-253">Any combination of strings and hash tables, in any order, is valid.</span></span>

`'TroubleshootingPack', @{ModuleName='PSDiagnostics'; ModuleVersion='1.0.0.0';GUID='c61d6278-02a3-4618-ae37-a524d40a7f44'}`

<span data-ttu-id="01779-254">Värdet för **ModulesToImport** -parametern för `Register-PSSessionConfiguration` cmdleten har företräde framför värdet för **ModulesToImport** -nyckeln i sessionens konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="01779-254">The value of the **ModulesToImport** parameter of the `Register-PSSessionConfiguration` cmdlet takes precedence over the value of the **ModulesToImport** key in the session configuration file.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="01779-255">-MountUserDrive</span><span class="sxs-lookup"><span data-stu-id="01779-255">-MountUserDrive</span></span>

<span data-ttu-id="01779-256">Konfigurerar sessioner som använder den här sessionen för att exponera `User:` PSDrive.</span><span class="sxs-lookup"><span data-stu-id="01779-256">Configures sessions that use this session configuration to expose the `User:` PSDrive.</span></span> <span data-ttu-id="01779-257">Användar enheter är unika för varje användare som ansluter och låter användare kopiera data till och från PowerShell-slutpunkter även om fil system leverantören inte visas.</span><span class="sxs-lookup"><span data-stu-id="01779-257">User drives are unique for each connecting user and allow users to copy data to and from PowerShell endpoints even if the File System provider is not exposed.</span></span> <span data-ttu-id="01779-258">Användar enhets rötter skapas under `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\` .</span><span class="sxs-lookup"><span data-stu-id="01779-258">User drive roots are created under `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\DriveRoots\`.</span></span> <span data-ttu-id="01779-259">För varje användare som ansluter till slut punkten skapas en mapp med namnet `$env:USERDOMAIN_$env:USERNAME` .</span><span class="sxs-lookup"><span data-stu-id="01779-259">For each user connecting to the endpoint, a folder is created with the name `$env:USERDOMAIN_$env:USERNAME`.</span></span>

<span data-ttu-id="01779-260">Innehållet i användar enheten behålls över användarsessioner och tas inte bort automatiskt.</span><span class="sxs-lookup"><span data-stu-id="01779-260">Contents in the user drive persist across user sessions and are not automatically removed.</span></span> <span data-ttu-id="01779-261">Som standard kan användare bara lagra upp till 50 MB data i användar enheten.</span><span class="sxs-lookup"><span data-stu-id="01779-261">By default, users can only store up to 50MB of data in the user drive.</span></span> <span data-ttu-id="01779-262">Detta kan anpassas med parametern **UserDriveMaximumSize** .</span><span class="sxs-lookup"><span data-stu-id="01779-262">This can be customized with the **UserDriveMaximumSize** parameter.</span></span>

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

### <span data-ttu-id="01779-263">-Path</span><span class="sxs-lookup"><span data-stu-id="01779-263">-Path</span></span>

<span data-ttu-id="01779-264">Anger sökvägen och fil namnet för sessionens konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="01779-264">Specifies the path and filename of the session configuration file.</span></span> <span data-ttu-id="01779-265">Filen måste ha ett `.pssc` fil namns tillägg.</span><span class="sxs-lookup"><span data-stu-id="01779-265">The file must have a `.pssc` file name extension.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="01779-266">– PowerShellVersion</span><span class="sxs-lookup"><span data-stu-id="01779-266">-PowerShellVersion</span></span>

<span data-ttu-id="01779-267">Anger versionen för PowerShell-motorn i sessioner som använder-sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-267">Specifies the version of the PowerShell engine in sessions that use the session configuration.</span></span> <span data-ttu-id="01779-268">De acceptabla värdena för den här parametern är: 2,0 och 3,0.</span><span class="sxs-lookup"><span data-stu-id="01779-268">The acceptable values for this parameter are: 2.0 and 3.0.</span></span> <span data-ttu-id="01779-269">Om du utelämnar den här parametern är **PowerShellVersion** -nyckeln kommenterad och den senaste versionen av PowerShell körs i sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-269">If you omit this parameter, the **PowerShellVersion** key is commented-out and newest version of PowerShell runs in the session.</span></span>

<span data-ttu-id="01779-270">Värdet för **PSVersion** -parametern för `Register-PSSessionConfiguration` cmdleten har företräde framför värdet för **PowerShellVersion** -nyckeln i sessionens konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="01779-270">The value of the **PSVersion** parameter of the `Register-PSSessionConfiguration` cmdlet takes precedence over the value of the **PowerShellVersion** key in the session configuration file.</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="01779-271">-RequiredGroups</span><span class="sxs-lookup"><span data-stu-id="01779-271">-RequiredGroups</span></span>

<span data-ttu-id="01779-272">Anger villkorliga åtkomst regler för användare som ansluter till sessioner som använder den här konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="01779-272">Specifies conditional access rules for users connecting to sessions that use this session configuration.</span></span>

<span data-ttu-id="01779-273">Ange en hash-tabell om du vill skapa en lista över regler med endast 1 nyckel per hash-tabell, "och" eller "eller", och ange värdet till en matris med säkerhets grupp namn eller ytterligare hash.</span><span class="sxs-lookup"><span data-stu-id="01779-273">Enter a hashtable to compose your list of rules using only 1 key per hashtable, 'And' or 'Or', and set the value to an array of security group names or additional hashtables.</span></span>

<span data-ttu-id="01779-274">Exempel som kräver att användare ansluter användare till medlemmar i en enda grupp: `@{ And = 'MyRequiredGroup' }`</span><span class="sxs-lookup"><span data-stu-id="01779-274">Example requiring connecting users to be members of a single group: `@{ And = 'MyRequiredGroup' }`</span></span>

<span data-ttu-id="01779-275">Exempel som kräver att användare tillhöra grupp A, eller både grupper B och C, för att få åtkomst till slut punkten: `@{ Or = 'GroupA', @{ And = 'GroupB', 'GroupC' } }`</span><span class="sxs-lookup"><span data-stu-id="01779-275">Example requiring users to belong to group A, or both groups B and C, to access the endpoint: `@{ Or = 'GroupA', @{ And = 'GroupB', 'GroupC' } }`</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="01779-276">-RoleDefinitions</span><span class="sxs-lookup"><span data-stu-id="01779-276">-RoleDefinitions</span></span>

<span data-ttu-id="01779-277">Anger mappningen mellan säkerhets grupper (eller användare) och roll funktioner.</span><span class="sxs-lookup"><span data-stu-id="01779-277">Specifies the mapping between security groups (or users) and role capabilities.</span></span> <span data-ttu-id="01779-278">Användarna beviljas åtkomst till alla roll funktioner som gäller för deras grupp medlemskap vid tidpunkten då sessionen skapas.</span><span class="sxs-lookup"><span data-stu-id="01779-278">Users will be granted access to all role capabilities which apply to their group membership at the time the session is created.</span></span>

<span data-ttu-id="01779-279">Ange en hash-tabell där nycklarna är namnet på säkerhets gruppen och värdena är hash-tabeller som innehåller en lista över roll funktioner som ska göras tillgängliga för säkerhets gruppen.</span><span class="sxs-lookup"><span data-stu-id="01779-279">Enter a hash table in which the keys are the name of the security group and the values are hash tables that contain a list of role capabilities that should be made available to the security group.</span></span>

<span data-ttu-id="01779-280">Exempel: `@{'Contoso\Level 2 Helpdesk Users' = @{ RoleCapabilities = 'Maintenance', 'ADHelpDesk' }}`</span><span class="sxs-lookup"><span data-stu-id="01779-280">For example: `@{'Contoso\Level 2 Helpdesk Users' = @{ RoleCapabilities = 'Maintenance', 'ADHelpDesk' }}`</span></span>

```yaml
Type: System.Collections.IDictionary
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="01779-281">-RunAsVirtualAccount</span><span class="sxs-lookup"><span data-stu-id="01779-281">-RunAsVirtualAccount</span></span>

<span data-ttu-id="01779-282">Konfigurerar sessioner som använder den här sessionen att köras som datorns (virtuellt) administratörs konto.</span><span class="sxs-lookup"><span data-stu-id="01779-282">Configures sessions using this session configuration to be run as the computer's (virtual) administrator account.</span></span> <span data-ttu-id="01779-283">Det går inte att använda det här fältet med parametern **GroupManagedServiceAccount** .</span><span class="sxs-lookup"><span data-stu-id="01779-283">This field cannot be used with the **GroupManagedServiceAccount** parameter.</span></span>

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

### <span data-ttu-id="01779-284">-RunAsVirtualAccountGroups</span><span class="sxs-lookup"><span data-stu-id="01779-284">-RunAsVirtualAccountGroups</span></span>

<span data-ttu-id="01779-285">Anger de säkerhets grupper som ska associeras med det virtuella kontot när en session som använder sessionen körs som ett virtuellt konto.</span><span class="sxs-lookup"><span data-stu-id="01779-285">Specifies the security groups to be associated with the virtual account when a session that uses the session configuration is run as a virtual account.</span></span> <span data-ttu-id="01779-286">Om det utelämnas tillhör det virtuella kontot domän administratörer på domän kontroller och administratörer på alla andra datorer.</span><span class="sxs-lookup"><span data-stu-id="01779-286">If omitted, the virtual account belongs to Domain Admins on domain controllers and Administrators on all other computers.</span></span>

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

### <span data-ttu-id="01779-287">-Schema</span><span class="sxs-lookup"><span data-stu-id="01779-287">-SchemaVersion</span></span>

<span data-ttu-id="01779-288">Anger versionen för fil schema för sessions konfiguration.</span><span class="sxs-lookup"><span data-stu-id="01779-288">Specifies the version of the session configuration file schema.</span></span> <span data-ttu-id="01779-289">Standardvärdet är "1.0.0.0".</span><span class="sxs-lookup"><span data-stu-id="01779-289">The default value is "1.0.0.0".</span></span>

```yaml
Type: System.Version
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="01779-290">-ScriptsToProcess</span><span class="sxs-lookup"><span data-stu-id="01779-290">-ScriptsToProcess</span></span>

<span data-ttu-id="01779-291">Lägger till angivna skript till sessioner som använder-sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-291">Adds the specified scripts to sessions that use the session configuration.</span></span> <span data-ttu-id="01779-292">Ange sökväg och fil namn för skripten.</span><span class="sxs-lookup"><span data-stu-id="01779-292">Enter the path and file names of the scripts.</span></span> <span data-ttu-id="01779-293">Värdet för den här parametern måste vara en fullständig eller absolut sökväg till skript fil namn.</span><span class="sxs-lookup"><span data-stu-id="01779-293">The value of this parameter must be a full or absolute path of script file names.</span></span>

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

### <span data-ttu-id="01779-294">-SessionType</span><span class="sxs-lookup"><span data-stu-id="01779-294">-SessionType</span></span>

<span data-ttu-id="01779-295">Anger vilken typ av session som skapas med hjälp av konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-295">Specifies the type of session that is created by using the session configuration.</span></span> <span data-ttu-id="01779-296">Standardvärdet är default.</span><span class="sxs-lookup"><span data-stu-id="01779-296">The default value is Default.</span></span> <span data-ttu-id="01779-297">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="01779-297">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="01779-298">Tom-inga moduler läggs till i sessionen som standard.</span><span class="sxs-lookup"><span data-stu-id="01779-298">Empty - No modules are added to session by default.</span></span> <span data-ttu-id="01779-299">Använd parametrarna för denna cmdlet för att lägga till moduler, funktioner, skript och andra funktioner i sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-299">Use the parameters of this cmdlet to add modules, functions, scripts, and other features to the session.</span></span> <span data-ttu-id="01779-300">Det här alternativet är utformat för att skapa anpassade sessioner genom att lägga till valda kommandon.</span><span class="sxs-lookup"><span data-stu-id="01779-300">This option is designed for you to create custom sessions by adding selected commands.</span></span> <span data-ttu-id="01779-301">Om du inte lägger till kommandon i en tom session är sessionen begränsad till uttryck och kanske inte kan användas.</span><span class="sxs-lookup"><span data-stu-id="01779-301">If you do not add commands to an empty session, the session is limited to expressions and might not be usable.</span></span>
- <span data-ttu-id="01779-302">Standard – lägger till Microsoft. PowerShell. Core-modulen i sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-302">Default - Adds the Microsoft.PowerShell.Core module to the session.</span></span> <span data-ttu-id="01779-303">Den här modulen innehåller den `Import-Module` cmdlet som användare kan använda för att importera andra moduler om du inte uttryckligen tillåter denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="01779-303">This module includes the `Import-Module` cmdlet that users can use to import other modules unless you explicitly prohibit this cmdlet.</span></span>
- <span data-ttu-id="01779-304">RestrictedRemoteServer.</span><span class="sxs-lookup"><span data-stu-id="01779-304">RestrictedRemoteServer.</span></span> <span data-ttu-id="01779-305">Innehåller endast följande proxy-funktioner:,,,,, `Exit-PSSession` `Get-Command` `Get-FormatData` `Get-Help` `Measure-Object` `Out-Default` och `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="01779-305">Includes only the following proxy functions: `Exit-PSSession`, `Get-Command`, `Get-FormatData`, `Get-Help`, `Measure-Object`, `Out-Default`, and `Select-Object`.</span></span>
  <span data-ttu-id="01779-306">Använd parametrarna för denna cmdlet för att lägga till moduler, funktioner, skript och andra funktioner i sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-306">Use the parameters of this cmdlet to add modules, functions, scripts, and other features to the session.</span></span>

```yaml
Type: System.Management.Automation.Remoting.SessionType
Parameter Sets: (All)
Aliases:
Accepted values: Empty, RestrictedRemoteServer, Default

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="01779-307">-TranscriptDirectory</span><span class="sxs-lookup"><span data-stu-id="01779-307">-TranscriptDirectory</span></span>

<span data-ttu-id="01779-308">Anger katalog för att placera sessions avskrifter för sessioner som använder den här sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-308">Specifies the directory to place session transcripts for sessions using this session configuration.</span></span>

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

### <span data-ttu-id="01779-309">-TypesToProcess</span><span class="sxs-lookup"><span data-stu-id="01779-309">-TypesToProcess</span></span>

<span data-ttu-id="01779-310">Lägger till de angivna `.ps1xml` exempelfilerna i sessioner som använder-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="01779-310">Adds the specified `.ps1xml` type files to sessions that use the session configuration.</span></span> <span data-ttu-id="01779-311">Ange typ fil namn.</span><span class="sxs-lookup"><span data-stu-id="01779-311">Enter the type filenames.</span></span> <span data-ttu-id="01779-312">Värdet för den här parametern måste vara en fullständig eller absolut sökväg för att ange fil namn.</span><span class="sxs-lookup"><span data-stu-id="01779-312">The value of this parameter must be a full or absolute path to type filenames.</span></span>

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

### <span data-ttu-id="01779-313">-UserDriveMaximumSize</span><span class="sxs-lookup"><span data-stu-id="01779-313">-UserDriveMaximumSize</span></span>

<span data-ttu-id="01779-314">Anger den maximala storleken för användar enheter som exponeras i sessioner som använder den här konfigurationen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-314">Specifies the maximum size for user drives exposed in sessions that use this session configuration.</span></span>
<span data-ttu-id="01779-315">Vid utelämnad är standard storleken för varje `User:` enhets rot 50 MB.</span><span class="sxs-lookup"><span data-stu-id="01779-315">When omitted, the default size of each `User:` drive root is 50MB.</span></span>

<span data-ttu-id="01779-316">Den här parametern ska användas med **MountUserDrive**.</span><span class="sxs-lookup"><span data-stu-id="01779-316">This parameter should be used with **MountUserDrive**.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="01779-317">-VariableDefinitions</span><span class="sxs-lookup"><span data-stu-id="01779-317">-VariableDefinitions</span></span>

<span data-ttu-id="01779-318">Lägger till angivna variabler i sessioner som använder sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-318">Adds the specified variables to sessions that use the session configuration.</span></span> <span data-ttu-id="01779-319">Ange en hash-tabell med följande nycklar:</span><span class="sxs-lookup"><span data-stu-id="01779-319">Enter a hash table with the following keys:</span></span>

- <span data-ttu-id="01779-320">Namn på variabeln.</span><span class="sxs-lookup"><span data-stu-id="01779-320">Name - Name of the variable.</span></span> <span data-ttu-id="01779-321">Den här nyckeln är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="01779-321">This key is required.</span></span>
- <span data-ttu-id="01779-322">Värde – variabel värde.</span><span class="sxs-lookup"><span data-stu-id="01779-322">Value - Variable value.</span></span> <span data-ttu-id="01779-323">Den här nyckeln är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="01779-323">This key is required.</span></span>
- <span data-ttu-id="01779-324">Alternativ-variabel alternativ.</span><span class="sxs-lookup"><span data-stu-id="01779-324">Options - Variable options.</span></span> <span data-ttu-id="01779-325">Den här nyckeln är valfri.</span><span class="sxs-lookup"><span data-stu-id="01779-325">This key is optional.</span></span> <span data-ttu-id="01779-326">Standardvärdet är **none**.</span><span class="sxs-lookup"><span data-stu-id="01779-326">The default value is **None**.</span></span> <span data-ttu-id="01779-327">De acceptabla värdena för den här parametern är: none, ReadOnly, Constant, Private eller AllScope.</span><span class="sxs-lookup"><span data-stu-id="01779-327">The acceptable values for this parameter are: None, ReadOnly, Constant, Private, or AllScope.</span></span>

<span data-ttu-id="01779-328">Exempel: `@{Name='WarningPreference';Value='SilentlyContinue';Options='AllScope'}`</span><span class="sxs-lookup"><span data-stu-id="01779-328">For example: `@{Name='WarningPreference';Value='SilentlyContinue';Options='AllScope'}`</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="01779-329">-VisibleAliases</span><span class="sxs-lookup"><span data-stu-id="01779-329">-VisibleAliases</span></span>

<span data-ttu-id="01779-330">Begränsar alias i sessionen till de som anges i värdet för den här parametern, plus alla alias som du definierar i parametern **AliasDefinition** .</span><span class="sxs-lookup"><span data-stu-id="01779-330">Limits the aliases in the session to those specified in the value of this parameter, plus any aliases that you define in the **AliasDefinition** parameter.</span></span> <span data-ttu-id="01779-331">Jokertecken stöds.</span><span class="sxs-lookup"><span data-stu-id="01779-331">Wildcard characters are supported.</span></span> <span data-ttu-id="01779-332">Som standard visas alla alias som definieras av PowerShell-motorn och alla alias som moduler exporterar i sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-332">By default, all aliases that are defined by the PowerShell engine and all aliases that modules export are visible in the session.</span></span>

<span data-ttu-id="01779-333">Exempel: `VisibleAliases='gcm', 'gp'`</span><span class="sxs-lookup"><span data-stu-id="01779-333">For example: `VisibleAliases='gcm', 'gp'`</span></span>

<span data-ttu-id="01779-334">När en **Visible** -parameter ingår i sessionens konfigurations fil, tar PowerShell bort `Import-Module` cmdleten och dess ipmo-alias från sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-334">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its ipmo alias from the session.</span></span>

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

### <span data-ttu-id="01779-335">-VisibleCmdlets</span><span class="sxs-lookup"><span data-stu-id="01779-335">-VisibleCmdlets</span></span>

<span data-ttu-id="01779-336">Begränsar cmdletarna i sessionen till de som anges i värdet för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="01779-336">Limits the cmdlets in the session to those specified in the value of this parameter.</span></span> <span data-ttu-id="01779-337">Jokertecken och kvalificerade namn för module stöds.</span><span class="sxs-lookup"><span data-stu-id="01779-337">Wildcard characters and Module Qualified Names are supported.</span></span>

<span data-ttu-id="01779-338">Som standard visas alla cmdlets som moduler i sessionen exportera i sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-338">By default, all cmdlets that modules in the session export are visible in the session.</span></span> <span data-ttu-id="01779-339">Använd parametrarna **SessionType** och **ModulesToImport** för att avgöra vilka moduler och snapin-moduler som importeras till sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-339">Use the **SessionType** and **ModulesToImport** parameters to determine which modules and snap-ins are imported into the session.</span></span> <span data-ttu-id="01779-340">Om inga moduler i **ModulesToImport** exponerar cmdleten försöker lämplig modul läsas in automatiskt.</span><span class="sxs-lookup"><span data-stu-id="01779-340">If no modules in **ModulesToImport** expose the cmdlet, the appropriate module will attempt to be autoloaded.</span></span>

<span data-ttu-id="01779-341">När en **Visible** -parameter ingår i sessionens konfigurations fil, tar PowerShell bort `Import-Module` cmdleten och dess ipmo-alias från sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-341">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its ipmo alias from the session.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="01779-342">-VisibleExternalCommands</span><span class="sxs-lookup"><span data-stu-id="01779-342">-VisibleExternalCommands</span></span>

<span data-ttu-id="01779-343">Begränsar de externa binärfiler, skript och kommandon som kan köras i sessionen till de som anges i värdet för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="01779-343">Limits the external binaries, scripts, and commands that can be executed in the session to those specified in the value of this parameter.</span></span> <span data-ttu-id="01779-344">Jokertecken stöds.</span><span class="sxs-lookup"><span data-stu-id="01779-344">Wildcard characters are supported.</span></span>

<span data-ttu-id="01779-345">Som standard visas inga externa kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-345">By default, no external commands are visible in the session.</span></span>

<span data-ttu-id="01779-346">När en **Visible** -parameter ingår i sessionens konfigurations fil, tar PowerShell bort `Import-Module` cmdleten och dess ipmo-alias från sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-346">When any **Visible** parameter is included in the session configuration file, PowerShell, removes the `Import-Module` cmdlet and its ipmo alias from the session.</span></span>

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

### <span data-ttu-id="01779-347">-VisibleFunctions</span><span class="sxs-lookup"><span data-stu-id="01779-347">-VisibleFunctions</span></span>

<span data-ttu-id="01779-348">Begränsar funktionerna i sessionen till de som anges i värdet för den här parametern, plus de funktioner som du definierar i parametern **FunctionDefinition** .</span><span class="sxs-lookup"><span data-stu-id="01779-348">Limits the functions in the session to those specified in the value of this parameter, plus any functions that you define in the **FunctionDefinition** parameter.</span></span> <span data-ttu-id="01779-349">Jokertecken stöds.</span><span class="sxs-lookup"><span data-stu-id="01779-349">Wildcard characters are supported.</span></span>

<span data-ttu-id="01779-350">Som standard visas alla funktioner som moduler i sessionen exporterar i sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-350">By default, all functions that modules in the session export are visible in the session.</span></span> <span data-ttu-id="01779-351">Använd parametrarna **SessionType** och **ModulesToImport** för att avgöra vilka moduler och snapin-moduler som importeras till sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-351">Use the **SessionType** and **ModulesToImport** parameters to determine which modules and snap-ins are imported into the session.</span></span>

<span data-ttu-id="01779-352">När en **Visible** -parameter ingår i sessionens konfigurations fil, tar PowerShell bort `Import-Module` cmdleten och dess ipmo-alias från sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-352">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its ipmo alias from the session.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="01779-353">-VisibleProviders</span><span class="sxs-lookup"><span data-stu-id="01779-353">-VisibleProviders</span></span>

<span data-ttu-id="01779-354">Begränsar PowerShell-providern i sessionen till de som anges i värdet för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="01779-354">Limits the PowerShell providers in the session to those specified in the value of this parameter.</span></span>
<span data-ttu-id="01779-355">Jokertecken stöds.</span><span class="sxs-lookup"><span data-stu-id="01779-355">Wildcard characters are supported.</span></span>

<span data-ttu-id="01779-356">Som standard visas alla providers som moduler i sessionen exportera i sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-356">By default, all providers that modules in the session export are visible in the session.</span></span> <span data-ttu-id="01779-357">Använd parametrarna **SessionType** och **ModulesToImport** för att avgöra vilka moduler som importeras till sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-357">Use the **SessionType** and **ModulesToImport** parameters to determine which modules are imported into the session.</span></span>

<span data-ttu-id="01779-358">När en **Visible** -parameter ingår i sessionens konfigurations fil, tar PowerShell bort `Import-Module` cmdleten och dess `ipmo` alias från sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-358">When any **Visible** parameter is included in the session configuration file, PowerShell removes the `Import-Module` cmdlet and its `ipmo` alias from the session.</span></span>

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

### <span data-ttu-id="01779-359">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="01779-359">CommonParameters</span></span>

<span data-ttu-id="01779-360">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="01779-360">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="01779-361">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="01779-361">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="01779-362">INDATA</span><span class="sxs-lookup"><span data-stu-id="01779-362">INPUTS</span></span>

### <span data-ttu-id="01779-363">Inga</span><span class="sxs-lookup"><span data-stu-id="01779-363">None</span></span>

<span data-ttu-id="01779-364">Det går inte att skicka några objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="01779-364">You cannot pipe any objects to this cmdlet.</span></span>

## <span data-ttu-id="01779-365">UTDATA</span><span class="sxs-lookup"><span data-stu-id="01779-365">OUTPUTS</span></span>

### <span data-ttu-id="01779-366">Inga</span><span class="sxs-lookup"><span data-stu-id="01779-366">None</span></span>

<span data-ttu-id="01779-367">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="01779-367">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="01779-368">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="01779-368">NOTES</span></span>

<span data-ttu-id="01779-369">Den här cmdleten är endast tillgänglig på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="01779-369">This cmdlet is only available on Windows platforms.</span></span>

- <span data-ttu-id="01779-370">Parametrar, till exempel **VisibleCmdlets** och **VisibleProviders**, importerar inte objekt till sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-370">Parameters, such as **VisibleCmdlets** and **VisibleProviders**, do not import items into the session.</span></span> <span data-ttu-id="01779-371">De väljer i stället bland de objekt som har importer ATS till sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-371">Instead, they select from among the items imported into the session.</span></span> <span data-ttu-id="01779-372">Om värdet för **VisibleProviders** -parametern till exempel är certifikat leverantören, men parametern **ModulesToImport** inte anger den **Microsoft. PowerShell. Security** -modul som innehåller certifikat leverantören, visas inte certifikat leverantören i sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-372">For example, if the value of the **VisibleProviders** parameter is the Certificate provider, but the **ModulesToImport** parameter does not specify the **Microsoft.PowerShell.Security** module that contains the Certificate provider, the Certificate provider is not visible in the session.</span></span>
- <span data-ttu-id="01779-373">`New-PSSessionConfigurationFile` skapar en konfigurations fil för sessionen som har fil namns tillägget. PSSC i den sökväg som du anger i parametern **Path** .</span><span class="sxs-lookup"><span data-stu-id="01779-373">`New-PSSessionConfigurationFile` creates a session configuration file that has a .pssc file name extension in the path that you specify in the **Path** parameter.</span></span> <span data-ttu-id="01779-374">När du använder sessionens konfigurations fil för att skapa en konfiguration av sessionen, `Register-PSSessionConfiguration` kopierar cmdleten konfigurations filen och sparar en aktiv kopia av filen i katalogen **SessionConfig** i `$PSHOME` katalogen.</span><span class="sxs-lookup"><span data-stu-id="01779-374">When you use the session configuration file to create a session configuration, the `Register-PSSessionConfiguration` cmdlet copies the configuration file and saves an active copy of the file in the **SessionConfig** subdirectory of the `$PSHOME` directory.</span></span>

  <span data-ttu-id="01779-375">**ConfigFilePath** -egenskapen för sessionen innehåller den fullständigt kvalificerade sökvägen till den aktiva sessionens konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="01779-375">The **ConfigFilePath** property of the session configuration contains the fully qualified path of the active session configuration file.</span></span> <span data-ttu-id="01779-376">Du kan ändra den aktiva konfigurations filen i `$PSHOME` katalogen när som helst med valfri text redigerare.</span><span class="sxs-lookup"><span data-stu-id="01779-376">You can modify the active configuration file in the `$PSHOME` directory at any time using any text editor.</span></span> <span data-ttu-id="01779-377">De ändringar du gör påverkar alla nya sessioner som använder sessionen, men inte befintliga sessioner.</span><span class="sxs-lookup"><span data-stu-id="01779-377">The changes that you make affect all new sessions that use the session configuration, but not existing sessions.</span></span>

  <span data-ttu-id="01779-378">Använd `Test-PSSessionConfigurationFile` cmdleten för att kontrol lera att konfigurations filens poster är giltiga innan du använder en redige rad konfigurations fil för sessionen.</span><span class="sxs-lookup"><span data-stu-id="01779-378">Before using an edited session configuration file, use the `Test-PSSessionConfigurationFile` cmdlet to verify that the configuration file entries are valid.</span></span>

## <span data-ttu-id="01779-379">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="01779-379">RELATED LINKS</span></span>

[<span data-ttu-id="01779-380">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="01779-380">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="01779-381">Aktivera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="01779-381">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="01779-382">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="01779-382">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="01779-383">Registrera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="01779-383">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="01779-384">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="01779-384">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="01779-385">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="01779-385">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="01779-386">Avregistrera-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="01779-386">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="01779-387">WSMan-Provider</span><span class="sxs-lookup"><span data-stu-id="01779-387">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="01779-388">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="01779-388">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="01779-389">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="01779-389">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
