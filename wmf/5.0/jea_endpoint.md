---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 66db78cfb136f22cad9078d7113dad085ee667a5
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188436"
---
# <a name="creating-and-connecting-to-a-jea-endpoint"></a><span data-ttu-id="445a4-102">Skapa och ansluta till en JEA-slutpunkt</span><span class="sxs-lookup"><span data-stu-id="445a4-102">Creating and Connecting to a JEA Endpoint</span></span>
<span data-ttu-id="445a4-103">Om du vill skapa en JEA-slutpunkt som du behöver skapa och registrera en särskilt konfigurerade PowerShell-Session konfigurationsfil, vilken kan genereras med den **ny PSSessionConfigurationFile** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="445a4-103">To create a JEA endpoint, you need to create and register a specially-configured PowerShell Session Configuration file, which can be generated with the **New-PSSessionConfigurationFile** cmdlet.</span></span>

```powershell
New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -TranscriptDirectory "C:\ProgramData\JEATranscripts" -RunAsVirtualAccount -RoleDefinitions @{ 'CONTOSO\NonAdmin_Operators' = @{ RoleCapabilities = 'Maintenance' }} -Path "$env:ProgramData\JEAConfiguration\Demo.pssc"
```

<span data-ttu-id="445a4-104">Detta skapar en konfigurationsfil för sessionen som ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="445a4-104">This will create a session configuration file that looks like this:</span></span>
```powershell
@{

# Version number of the schema used for this document
SchemaVersion = '2.0.0.0'

# ID used to uniquely identify this document
GUID = 'a384fdd3-5830-4a2c-ac86-cdd1822c3afd'

# Author of this document
Author = 'Administrator'

# Description of the functionality provided by these settings
# Description = ''

# Session type defaults to apply for this session configuration. Can be 'RestrictedRemoteServer' (recommended), 'Empty', or 'Default'
SessionType = 'RestrictedRemoteServer'

# Directory to place session transcripts for this session configuration
TranscriptDirectory = 'C:\ProgramData\JEATranscripts'

# Whether to run this session configuration as the machine's (virtual) administrator account
RunAsVirtualAccount = $true

# Groups associated with machine's (virtual) administrator account
# RunAsVirtualAccountGroups = 'Remote Desktop Users', 'Remote Management Users'

# Scripts to run when applied to a session
# ScriptsToProcess = 'C:\ConfigData\InitScript1.ps1', 'C:\ConfigData\InitScript2.ps1'

# User roles (security groups), and the Role Capabilities that should be applied to them when applied to a session
RoleDefinitions = @{
    'CONTOSO\NonAdmin_Operators' = @{
        'RoleCapabilities' = 'Maintenance' } }

}
```
<span data-ttu-id="445a4-105">När du skapar en JEA slutpunkt måste du ange följande parametrar för kommandot (och motsvarande nycklar i filen):</span><span class="sxs-lookup"><span data-stu-id="445a4-105">When creating a JEA endpoint, the following parameters of the command (and corresponding keys in the file) must be set:</span></span>
1.  <span data-ttu-id="445a4-106">SessionType till RestrictedRemoteServer</span><span class="sxs-lookup"><span data-stu-id="445a4-106">SessionType to RestrictedRemoteServer</span></span>
2.  <span data-ttu-id="445a4-107">RunAsVirtualAccount till **$true**</span><span class="sxs-lookup"><span data-stu-id="445a4-107">RunAsVirtualAccount to **$true**</span></span>
3.  <span data-ttu-id="445a4-108">TranscriptPath till katalogen där ”över axel” betyg sparas efter varje session</span><span class="sxs-lookup"><span data-stu-id="445a4-108">TranscriptPath to the directory where “over the shoulder” transcripts will be saved after each session</span></span>
4.  <span data-ttu-id="445a4-109">RoleDefinitions till en hash-tabell som definierar vilka grupper som har åtkomst till vilka ”roll funktioner”.</span><span class="sxs-lookup"><span data-stu-id="445a4-109">RoleDefinitions to a hashtable that defines which groups have access to which “Role Capabilities.”</span></span>  <span data-ttu-id="445a4-110">Det här fältet definierar **som** kan göra **vad** på den här slutpunkten.</span><span class="sxs-lookup"><span data-stu-id="445a4-110">This field defines **who** can do **what** on this endpoint.</span></span>   <span data-ttu-id="445a4-111">Rollen funktioner är särskilda filer som förklaras inom kort.</span><span class="sxs-lookup"><span data-stu-id="445a4-111">Role Capabilities are special files that will be explained shortly.</span></span>


<span data-ttu-id="445a4-112">Fältet RoleDefinitions definierar vilka grupper som hade tillgång till vilka funktioner i rollen.</span><span class="sxs-lookup"><span data-stu-id="445a4-112">The RoleDefinitions field defines which groups had access to which Role Capabilities.</span></span>  <span data-ttu-id="445a4-113">En roll-funktion är en fil som definierar en uppsättning funktioner som kan användas för anslutning av användare.</span><span class="sxs-lookup"><span data-stu-id="445a4-113">A Role Capability is a file that defines a set of capabilities that will be exposed to connecting users.</span></span>  <span data-ttu-id="445a4-114">Du kan skapa rollen funktioner med den **ny PSRoleCapabilityFile** kommando.</span><span class="sxs-lookup"><span data-stu-id="445a4-114">You can create Role Capabilities with the **New-PSRoleCapabilityFile** command.</span></span>

```powershell
New-PSRoleCapabilityFile -Path "$env:ProgramFiles\WindowsPowerShell\Modules\DemoModule\RoleCapabilities\Maintenance.psrc"
```

<span data-ttu-id="445a4-115">Detta skapar en mall för rollen funktion som ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="445a4-115">This will generate a template role capability that looks like this:</span></span>
```
@{

# ID used to uniquely identify this document
GUID = '9287a34f-3f0e-4fbe-9dd7-f1361ba9fd65'

# Author of this document
Author = 'Administrator'

# Description of the functionality provided by these settings
# Description = ''

# Company associated with this document
CompanyName = 'Unknown'

# Copyright statement for this document
Copyright = '(c) 2015 Administrator. All rights reserved.'

# Modules to import when applied to a session
# ModulesToImport = 'MyCustomModule', @{ ModuleName = 'MyCustomModule'; ModuleVersion = '1.0.0.0'; GUID = '4d30d5f0-cb16-4898-812d-f20a6c596bdf' }

# Aliases to make visible when applied to a session
# VisibleAliases = 'Item1', 'Item2'

# Cmdlets to make visible when applied to a session
# VisibleCmdlets = 'Invoke-Cmdlet1', @{ Name = 'Invoke-Cmdlet2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }

# Functions to make visible when applied to a session
# VisibleFunctions = 'Invoke-Function1', @{ Name = 'Invoke-Function2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }

# External commands (scripts and applications) to make visible when applied to a session
# VisibleExternalCommands = 'Item1', 'Item2'

# Providers to make visible when applied to a session
# VisibleProviders = 'Item1', 'Item2'

# Scripts to run when applied to a session
# ScriptsToProcess = 'C:\ConfigData\InitScript1.ps1', 'C:\ConfigData\InitScript2.ps1'

# Aliases to be defined when applied to a session
# AliasDefinitions = @{ Name = 'Alias1'; Value = 'Invoke-Alias1'}, @{ Name = 'Alias2'; Value = 'Invoke-Alias2'}

# Functions to define when applied to a session
# FunctionDefinitions = @{ Name = 'MyFunction'; ScriptBlock = { param($MyInput) $MyInput } }

# Variables to define when applied to a session
# VariableDefinitions = @{ Name = 'Variable1'; Value = { 'Dynamic' + 'InitialValue' } }, @{ Name = 'Variable2'; Value = 'StaticInitialValue' }

# Environment variables to define when applied to a session
# EnvironmentVariables = @{ Variable1 = 'Value1'; Variable2 = 'Value2' }

# Type files (.ps1xml) to load when applied to a session
# TypesToProcess = 'C:\ConfigData\MyTypes.ps1xml', 'C:\ConfigData\OtherTypes.ps1xml'

# Format files (.ps1xml) to load when applied to a session
# FormatsToProcess = 'C:\ConfigData\MyFormats.ps1xml', 'C:\ConfigData\OtherFormats.ps1xml'

# Assemblies to load when applied to a session
# AssembliesToLoad = 'System.Web', 'System.OtherAssembly, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a'

}

```
<span data-ttu-id="445a4-116">Rollen funktioner måste sparas som en giltig PowerShell-modul i en katalog med namnet ”RoleCapabilities” för att användas av en JEA sessionskonfiguration.</span><span class="sxs-lookup"><span data-stu-id="445a4-116">To be used by a JEA session configuration, Role Capabilities must be saved as a valid PowerShell module in a directory named “RoleCapabilities”.</span></span> <span data-ttu-id="445a4-117">En modul kan ha flera rollen funktionsfiler, om så önskas.</span><span class="sxs-lookup"><span data-stu-id="445a4-117">A module may have multiple role capability files, if desired.</span></span>

<span data-ttu-id="445a4-118">För att börja konfigurera vilka cmdlets, funktioner, alias och skript som en användare kan komma åt när du ansluter till en session JEA, att lägga till dina egna regler i filen rollen kapaciteten att följa de kommenterade ut mallar.</span><span class="sxs-lookup"><span data-stu-id="445a4-118">To start configuring which cmdlets, functions, aliases, and scripts a user may access when connecting to a JEA session, add your own rules to the Role Capability file following the commented out templates.</span></span> <span data-ttu-id="445a4-119">För en djupare inblick i hur du kan konfigurera rollen funktioner checka ut hela [upplevelse guiden](http://aka.ms/JEA).</span><span class="sxs-lookup"><span data-stu-id="445a4-119">For a deeper look into how you can configure Role Capabilities, check out the full [experience guide](http://aka.ms/JEA).</span></span>

<span data-ttu-id="445a4-120">Slutligen, när du är klar med att anpassa sessionskonfigurationen och relaterade funktioner för rollen registrera den här konfigurationen och skapa slutpunkten genom att köra **Register-PSSessionConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="445a4-120">Finally, once you have finished customizing your session configuration and related Role Capabilities, register this session configuration and create the endpoint by running **Register-PSSessionConfiguration**.</span></span>

```powershell
Register-PSSessionConfiguration -Name Maintenance -Path "C:\ProgramData\JEAConfiguration\Demo.pssc"
```

## <a name="connect-to-a-jea-endpoint"></a><span data-ttu-id="445a4-121">Ansluta till en JEA slutpunkt</span><span class="sxs-lookup"><span data-stu-id="445a4-121">Connect to a JEA Endpoint</span></span>
<span data-ttu-id="445a4-122">Ansluter till en slutpunkt för JEA fungerar på samma sätt som ansluter till alla andra PowerShell endpoint fungerar.</span><span class="sxs-lookup"><span data-stu-id="445a4-122">Connecting to a JEA Endpoint works the same way connecting to any other PowerShell endpoint works.</span></span>  <span data-ttu-id="445a4-123">Du behöver bara ange namnet på slutpunkten JEA som ”ConfigurationName”-parametern för **New-PSSession**, **Invoke-Command**, eller **Enter-PSSession**.</span><span class="sxs-lookup"><span data-stu-id="445a4-123">You simply have to give your JEA endpoint name as the “ConfigurationName” parameter for **New-PSSession**, **Invoke-Command**, or **Enter-PSSession**.</span></span>

```powershell
Enter-PSSession -ConfigurationName Maintenance -ComputerName localhost
```
<span data-ttu-id="445a4-124">När du har anslutit till sessionen JEA begränsas du kör kommandon godkända av roll-funktionerna som du har åtkomst till.</span><span class="sxs-lookup"><span data-stu-id="445a4-124">Once you have connected to the JEA session, you will be limited to running the commands whitelisted in the Role Capabilities that you have access to.</span></span> <span data-ttu-id="445a4-125">Ett fel inträffar om du försöker köra ett kommando som inte är tillåtet för din roll.</span><span class="sxs-lookup"><span data-stu-id="445a4-125">If you try to run any command not allowed for your role, you will encounter an error.</span></span>
