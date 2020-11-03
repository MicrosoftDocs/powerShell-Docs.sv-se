---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssessionconfiguration?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSessionConfiguration
ms.openlocfilehash: 300fc3dee2e0d625e5aea42bfdcf45ea2e8b5a7f
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268617"
---
# <span data-ttu-id="311d2-103">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="311d2-103">Get-PSSessionConfiguration</span></span>

## <span data-ttu-id="311d2-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="311d2-104">SYNOPSIS</span></span>
<span data-ttu-id="311d2-105">Hämtar de registrerade sessionsbaserade på datorn.</span><span class="sxs-lookup"><span data-stu-id="311d2-105">Gets the registered session configurations on the computer.</span></span>

## <span data-ttu-id="311d2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="311d2-106">SYNTAX</span></span>

```
Get-PSSessionConfiguration [[-Name] <String[]>] [-Force] [<CommonParameters>]
```

## <span data-ttu-id="311d2-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="311d2-107">DESCRIPTION</span></span>

<span data-ttu-id="311d2-108">`Get-PSSessionConfiguration`Cmdlet: en hämtar de sessionsinställningar som har registrerats på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="311d2-108">The `Get-PSSessionConfiguration` cmdlet gets the session configurations that have been registered on the local computer.</span></span> <span data-ttu-id="311d2-109">Det här är en avancerad cmdlet som är avsedd att användas av system administratörer för att hantera konfigurationer för anpassade sessioner för sina användare.</span><span class="sxs-lookup"><span data-stu-id="311d2-109">This is an advanced cmdlet that is designed to be used by system administrators to manage customized session configurations for their users.</span></span>

<span data-ttu-id="311d2-110">Från och med PowerShell 3,0 kan du definiera egenskaperna för en session-konfiguration med hjälp av en PSSC-fil (session Configuration).</span><span class="sxs-lookup"><span data-stu-id="311d2-110">Beginning in PowerShell 3.0, you can define the properties of a session configuration by using a session configuration (.pssc) file.</span></span> <span data-ttu-id="311d2-111">Med den här funktionen kan du skapa anpassade och begränsade sessioner utan att skriva ett dator program.</span><span class="sxs-lookup"><span data-stu-id="311d2-111">This feature lets you create customized and restricted sessions without writing a computer program.</span></span> <span data-ttu-id="311d2-112">Mer information om konfigurationsfiler för sessioner finns [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span><span class="sxs-lookup"><span data-stu-id="311d2-112">For more information about session configuration files, see [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>

<span data-ttu-id="311d2-113">Från och med PowerShell 3,0 har nya antecknings egenskaper också lagts till i sessionens konfigurations objekt som `Get-PSSessionConfiguration` returneras.</span><span class="sxs-lookup"><span data-stu-id="311d2-113">Also, beginning in PowerShell 3.0, new note properties have been added to the session configuration object that `Get-PSSessionConfiguration` returns.</span></span> <span data-ttu-id="311d2-114">De här egenskaperna gör det enklare för användare och konfiguration av sessioner att granska och jämföra sessionsbaserade.</span><span class="sxs-lookup"><span data-stu-id="311d2-114">These properties make it easier for users and session configuration authors to examine and compare session configurations.</span></span>

<span data-ttu-id="311d2-115">Använd cmdleten för att skapa och registrera en konfiguration av en session `Register-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="311d2-115">To create and register a session configuration, use the `Register-PSSessionConfiguration` cmdlet.</span></span>
<span data-ttu-id="311d2-116">För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="311d2-116">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

## <span data-ttu-id="311d2-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="311d2-117">EXAMPLES</span></span>

### <span data-ttu-id="311d2-118">Exempel 1 – Hämta konfigurationer för sessioner på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="311d2-118">Example 1 - Get session configurations on the local computer</span></span>

```powershell
Get-PSSessionConfiguration
```

### <span data-ttu-id="311d2-119">Exempel 2 – Hämta två standardkonfigurationer för sessioner</span><span class="sxs-lookup"><span data-stu-id="311d2-119">Example 2 - Get the two default session configurations</span></span>

<span data-ttu-id="311d2-120">Kommandot använder **Name** -parametern för `Get-PSSessionConfiguration` att bara hämta sessionsinställningar med namn som börjar med "Microsoft".</span><span class="sxs-lookup"><span data-stu-id="311d2-120">The command uses the **Name** parameter of `Get-PSSessionConfiguration` to get only the session configurations with names that begin with "Microsoft".</span></span>

```powershell
Get-PSSessionConfiguration -Name Microsoft*
```

```Output
Name                      PSVersion  StartupScript        Permission
----                      ---------  -------------        ----------
microsoft.powershell      5.1                             BUILTIN\Administrators AccessAll...
microsoft.powershell32    5.1                             BUILTIN\Administrators AccessAll...
```

### <span data-ttu-id="311d2-121">Exempel 3 – Hämta egenskaperna och värdena för en konfiguration av sessionen</span><span class="sxs-lookup"><span data-stu-id="311d2-121">Example 3 - Get the properties and values of a session configuration</span></span>

<span data-ttu-id="311d2-122">I det här exemplet visas egenskaper och egenskaps värden för en sessionsfil som skapats med hjälp av en konfigurations fil för sessionen.</span><span class="sxs-lookup"><span data-stu-id="311d2-122">This example shows the properties and property values of a session configuration that was created by using a session configuration file.</span></span>

```powershell
Get-PSSessionConfiguration -Name Full  | Format-List -Property *
```

```Output
Copyright                     : (c) 2011 User01. All rights reserved.
AliasDefinitions              : {System.Collections.Hashtable}
SessionType                   : Default
CompanyName                   : Unknown
GUID                          : 1e9cb265-dae0-4bd3-89a9-8338a47698a1
Author                        : User01
ExecutionPolicy               : Restricted
SchemaVersion                 : 1.0.0.0
LanguageMode                  : FullLanguage
Architecture                  : 64
Filename                      : %windir%\system32\pwrshplugin.dll
ResourceUri                   : http://schemas.microsoft.com/powershell/Full
MaxConcurrentCommandsPerShell : 1500
UseSharedProcess              : false
ProcessIdleTimeoutSec         : 0
xmlns                         : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
MaxConcurrentUsers            : 10
lang                          : en-US
SupportsOptions               : true
ExactMatch                    : true
configfilepath                : C:\WINDOWS\System32\WindowsPowerShell\v1.0\SessionConfig\Full_1e9cb265-dae0-4bd3-89a9-8338a47698a1.pssc
RunAsUser                     :
IdleTimeoutms                 : 7200000
PSVersion                     : 3.0
OutputBufferingMode           : Block
AutoRestart                   : false
MaxShells                     : 300
MaxMemoryPerShellMB           : 1024
MaxIdleTimeoutms              : 43200000
SDKVersion                    : 1
Name                          : Full
XmlRenderingType              : text
Capability                    : {Shell}
RunAsPassword                 :
MaxProcessesPerShell          : 25
Enabled                       : True
MaxShellsPerUser              : 30
Permission                    :
```

<span data-ttu-id="311d2-123">Exemplet använder `Get-PSSessionConfiguration` cmdleten för att hämta den fullständiga konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="311d2-123">The example uses the `Get-PSSessionConfiguration` cmdlet to get the full session configuration.</span></span> <span data-ttu-id="311d2-124">En pipeline-operator skickar fullständig sessionsinformation till `Format-List` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="311d2-124">A pipeline operator sends the Full session configuration to the `Format-List` cmdlet.</span></span> <span data-ttu-id="311d2-125">**Egenskaps** parametern med värdet `*` (alla) leder `Format-List` för att visa alla egenskaper och värden för objektet i en lista.</span><span class="sxs-lookup"><span data-stu-id="311d2-125">The **Property** parameter with a value of `*` (all) directs `Format-List` to display all the properties and values of the object in a list.</span></span>

<span data-ttu-id="311d2-126">Utdata innehåller användbar information, inklusive författaren av sessionens konfiguration, typ av session, språk läge och körnings princip för sessioner som skapas med den här konfigurationen, session kvoter och den fullständiga sökvägen till sessionens konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="311d2-126">The output includes useful information, including the author of the session configuration, the session type, language mode, and execution policy of sessions that are created with this session configuration, session quotas, and the full path to the session configuration file.</span></span>

<span data-ttu-id="311d2-127">Den här vyn av en sessions konfiguration används för sessioner som innehåller en konfigurations fil för sessionen.</span><span class="sxs-lookup"><span data-stu-id="311d2-127">This view of a session configuration is used for sessions that include a session configuration file.</span></span>
<span data-ttu-id="311d2-128">Mer information om konfigurationsfiler för sessioner finns [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span><span class="sxs-lookup"><span data-stu-id="311d2-128">For more information about session configuration files, see [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>

### <span data-ttu-id="311d2-129">Exempel 4 – ett annat sätt att titta på sessionens konfigurationer</span><span class="sxs-lookup"><span data-stu-id="311d2-129">Example 4 - Another way to look at the session configurations</span></span>

<span data-ttu-id="311d2-130">I det här exemplet används `Get-ChildItem` cmdleten (alias `dir` ) i WSMan: Provider-enheten för att titta på innehållet i plugin-noden.</span><span class="sxs-lookup"><span data-stu-id="311d2-130">This example uses the `Get-ChildItem` cmdlet (alias `dir`) in the WSMan: provider drive to look at the content of the Plugin node.</span></span> <span data-ttu-id="311d2-131">Detta är ett annat sätt att titta på sessionens konfigurationer på datorn.</span><span class="sxs-lookup"><span data-stu-id="311d2-131">This is another way to look at the session configurations on the computer.</span></span>

```powershell
dir wsman:\localhost\plugin
```

```Output
Type            Keys                                Name
----            ----                                ----
Container       {Name=Event Forwarding Plugin}      Event Forwarding Plugin
Container       {Name=Full}                         Full
Container       {Name=microsoft.powershell}         microsoft.powershell
Container       {Name=microsoft.powershell.workf... microsoft.powershell.workflow
Container       {Name=microsoft.powershell32}       microsoft.powershell32
Container       {Name=microsoft.ServerManager}      microsoft.ServerManager
Container       {Name=WMI Provider}                 WMI Provider
```

<span data-ttu-id="311d2-132">**Plugin** -noden innehåller **ContainerElement** -objekt (Microsoft. WSMan. Management. WSManConfigContainerElement) som representerar registrerade PowerShell-sessionsbaserade konfigurationer, tillsammans med andra plugin-program för WS-Management.</span><span class="sxs-lookup"><span data-stu-id="311d2-132">The **PlugIn** node contains **ContainerElement** objects (Microsoft.WSMan.Management.WSManConfigContainerElement) that represent the registered PowerShell session configurations, along with other plug-ins for WS-Management.</span></span>

### <span data-ttu-id="311d2-133">Exempel 6 – Visa sessionsinställningar på en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="311d2-133">Example 6 - View session configurations on a remote computer</span></span>

<span data-ttu-id="311d2-134">I det här exemplet visas hur du använder WSMan-providern för att Visa sessionsinställningar på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="311d2-134">This example shows how to use the WSMan provider to view the session configurations on a remote computer.</span></span> <span data-ttu-id="311d2-135">Den här metoden ger inte så mycket information som ett `Get-PSSessionConfiguration` kommando, men användaren behöver inte vara medlem i gruppen Administratörer för att köra denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="311d2-135">This method does not provide as much information as a `Get-PSSessionConfiguration` command, but the user does not need to be a member of the Administrators group to run this cmdlet.</span></span>

```powershell
Connect-WSMan -ComputerName Server01
dir WSMan:\Server01\Plugin
```

```Output
   WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin

Type            Keys                                Name
----            ----                                ----
Container       {Name=Empty}                        Empty
Container       {Name=Event Forwarding Plugin}      Event Forwarding Plugin
Container       {Name=Full}                         Full
Container       {Name=microsoft.powershell}         microsoft.powershell
Container       {Name=microsoft.powershell.workf... microsoft.powershell.workflow
Container       {Name=microsoft.powershell32}       microsoft.powershell32
Container       {Name=microsoft.ServerManager}      microsoft.ServerManager
Container       {Name=NoLanguage}                   NoLanguage
Container       {Name=RestrictedLang}               RestrictedLang
Container       {Name=RRS}                          RRS
Container       {Name=SEL Plugin}                   SEL Plugin
Container       {Name=WithProfile}                  WithProfile
Container       {Name=WMI Provider}                 WMI Provider
```

<span data-ttu-id="311d2-136">`Connect-WSMan`Cmdleten ansluter till WinRM-tjänsten på fjärrdatorn Server01.</span><span class="sxs-lookup"><span data-stu-id="311d2-136">The `Connect-WSMan` cmdlet connects to the WinRM service on the Server01 remote computer.</span></span> <span data-ttu-id="311d2-137">`Get-ChildItem`Cmdleten (alias `dir` ) för WSMan: Drive hämtar objekten i **Server01\Plugin** -sökvägen.</span><span class="sxs-lookup"><span data-stu-id="311d2-137">The `Get-ChildItem` cmdlet (alias `dir`) of the WSMan: drive gets the items in the **Server01\Plugin** path.</span></span> <span data-ttu-id="311d2-138">Utdata visar objekten i plugin-katalogen på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="311d2-138">The output shows the items in the Plugin directory on the Server01 computer.</span></span> <span data-ttu-id="311d2-139">Objekten inkluderar sessionsinställningar, som är en typ av WSMan-plugin-program, tillsammans med andra typer av plugin-program på datorn.</span><span class="sxs-lookup"><span data-stu-id="311d2-139">The items include the session configurations, which are a type of WSMan plug-in, along with other types of plug-ins on the computer.</span></span>

### <span data-ttu-id="311d2-140">Exempel 7 – Hämta detaljerade sessionsinställningar från en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="311d2-140">Example 7 - Get detailed session configurations from a remote computer</span></span>

<span data-ttu-id="311d2-141">Det här exemplet visar hur du kör ett `Get-PSSessionConfiguration` kommando på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="311d2-141">This example shows how to run a `Get-PSSessionConfiguration` command on a remote computer.</span></span> <span data-ttu-id="311d2-142">Kommandot kräver att CredSSP-delegering aktive ras i klient inställningarna på den lokala datorn och i tjänst inställningarna på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="311d2-142">The command requires that CredSSP delegation be enabled in the client settings on the local computer and in the service settings on the remote computer.</span></span>

<span data-ttu-id="311d2-143">Om du vill köra kommandona i det här exemplet måste du vara medlem i gruppen Administratörer på den lokala datorn och fjärrdatorn och du måste starta PowerShell med alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="311d2-143">To run the commands in this example, you must be a member of the Administrators group on the local and remote computers and you must start PowerShell with the **Run as administrator** option.</span></span>

```powershell
Enable-WSManCredSSP -Delegate Server02
Connect-WSMan Server02
Set-Item WSMan:\Server02*\Service\Auth\CredSSP -Value $true
Invoke-Command -ScriptBlock {Get-PSSessionConfiguration} -ComputerName Server02 -Authentication CredSSP -Credential Domain01\Admin01
```

```Output
Name                      PSVersion  StartupScript        Permission                          PSComputerName
----                      ---------  -------------        ----------                          --------------
microsoft.powershell      5.1                             BUILTIN\Administrators AccessAll... server02.corp.fabrikam.com
microsoft.powershell32    5.1                             BUILTIN\Administrators AccessAll... server02.corp.fabrikam.com
MyX86Shell                5.1        c:\test\x86Shell.ps1 BUILTIN\Administrators AccessAll... server02.corp.fabrikam.com
```

<span data-ttu-id="311d2-144">`Enable-WSManCredSSP`Cmdlet: en aktiverar **CredSSP** -delegering på Server01, den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="311d2-144">The `Enable-WSManCredSSP` cmdlet enables **CredSSP** delegation on Server01, the local computer.</span></span> <span data-ttu-id="311d2-145">`Connect-WSMan`Cmdleten ansluter till Server02-datorn.</span><span class="sxs-lookup"><span data-stu-id="311d2-145">The `Connect-WSMan` cmdlet connects to Server02 computer.</span></span> <span data-ttu-id="311d2-146">Den här åtgärden lägger till en nod för Server02 till enheten WSMan: på den lokala datorn, så att du kan visa och ändra WS-Management inställningar på Server02-datorn.</span><span class="sxs-lookup"><span data-stu-id="311d2-146">This action adds a node for Server02 to the WSMan: drive on the local computer, allowing you to view and change the WS-Management settings on the Server02 computer.</span></span> <span data-ttu-id="311d2-147">`Set-Item`Cmdleten ändrar värdet för **CredSSP** -objektet i noden tjänst på den Server02 datorn till **True**.</span><span class="sxs-lookup"><span data-stu-id="311d2-147">The `Set-Item` cmdlet changes the value of the **CredSSP** item in the Service node of the Server02 computer to **True**.</span></span> <span data-ttu-id="311d2-148">Detta konfigurerar tjänst inställningarna på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="311d2-148">This configures the service settings on the remote computer.</span></span> <span data-ttu-id="311d2-149">`Invoke-Command`Cmdleten kör `Get-PSSessionConfiguration` kommandot på Server02-datorn.</span><span class="sxs-lookup"><span data-stu-id="311d2-149">The `Invoke-Command` cmdlet runs the`Get-PSSessionConfiguration` command on the Server02 computer.</span></span> <span data-ttu-id="311d2-150">Kommandot använder parametern **Credential** och använder parametern **Authentication** med värdet **CredSSP**.</span><span class="sxs-lookup"><span data-stu-id="311d2-150">The command uses the **Credential** parameter, and it uses the **Authentication** parameter with a value of **CredSSP**.</span></span> <span data-ttu-id="311d2-151">Utdata visar sessionens konfigurationer på Server02-fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="311d2-151">The output shows the session configurations on the Server02 remote computer.</span></span>

### <span data-ttu-id="311d2-152">Exempel 8 – Hämta resurs-URI för en konfiguration av sessionen</span><span class="sxs-lookup"><span data-stu-id="311d2-152">Example 8 - Get the resource URI of a session configuration</span></span>

<span data-ttu-id="311d2-153">Det här exemplet är användbart för att ange värdet för `$PSSessionConfigurationName` variabeln Preference, som tar en resurs-URI.</span><span class="sxs-lookup"><span data-stu-id="311d2-153">This example is useful for setting the value of the `$PSSessionConfigurationName` preference variable, which takes a resource URI.</span></span>

```powershell
(Get-PSSessionConfiguration -Name CustomShell).resourceURI
```

```Output
http://schemas.microsoft.com/powershell/microsoft.CustomShell
```

<span data-ttu-id="311d2-154">`$PSSessionConfigurationName`Variabeln anger standard konfigurationen som används när du skapar en session.</span><span class="sxs-lookup"><span data-stu-id="311d2-154">The `$PSSessionConfigurationName` variable specifies the default configuration that is used when you create a session.</span></span> <span data-ttu-id="311d2-155">Den här variabeln anges på den lokala datorn, men den anger en konfiguration på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="311d2-155">This variable is set on the local computer, but it specifies a configuration on the remote computer.</span></span> <span data-ttu-id="311d2-156">Mer information om `$PSSessionConfiguration` variabeln finns i [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="311d2-156">For more information about the `$PSSessionConfiguration` variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

## <span data-ttu-id="311d2-157">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="311d2-157">PARAMETERS</span></span>

### <span data-ttu-id="311d2-158">-Force</span><span class="sxs-lookup"><span data-stu-id="311d2-158">-Force</span></span>

<span data-ttu-id="311d2-159">Inaktiverar uppmaningen att starta om WinRM-tjänsten om tjänsten inte redan körs.</span><span class="sxs-lookup"><span data-stu-id="311d2-159">Suppresses the prompt to restart the WinRM service, if the service is not already running.</span></span>

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

### <span data-ttu-id="311d2-160">-Name</span><span class="sxs-lookup"><span data-stu-id="311d2-160">-Name</span></span>

<span data-ttu-id="311d2-161">Hämtar endast sessionsdata med angivet namn eller namn mönster.</span><span class="sxs-lookup"><span data-stu-id="311d2-161">Gets only the session configurations with the specified name or name pattern.</span></span> <span data-ttu-id="311d2-162">Ange ett eller flera konfigurations namn för sessionen.</span><span class="sxs-lookup"><span data-stu-id="311d2-162">Enter one or more session configuration names.</span></span> <span data-ttu-id="311d2-163">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="311d2-163">Wildcards are permitted.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: All session configurations on the local computer
Accept pipeline input: False
Accept wildcard characters: True
```

### <span data-ttu-id="311d2-164">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="311d2-164">CommonParameters</span></span>

<span data-ttu-id="311d2-165">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="311d2-165">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="311d2-166">Mer information finns i [about_CommonParameters](./About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="311d2-166">For more information, see [about_CommonParameters](./About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="311d2-167">INDATA</span><span class="sxs-lookup"><span data-stu-id="311d2-167">INPUTS</span></span>

### <span data-ttu-id="311d2-168">Inget</span><span class="sxs-lookup"><span data-stu-id="311d2-168">None</span></span>

<span data-ttu-id="311d2-169">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="311d2-169">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="311d2-170">UTDATA</span><span class="sxs-lookup"><span data-stu-id="311d2-170">OUTPUTS</span></span>

### <span data-ttu-id="311d2-171">Microsoft. PowerShell. commands. PSSessionConfigurationCommands # PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="311d2-171">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration</span></span>

## <span data-ttu-id="311d2-172">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="311d2-172">NOTES</span></span>

- <span data-ttu-id="311d2-173">Starta PowerShell med alternativet **Kör som administratör** för att köra denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="311d2-173">To run this cmdlet, start PowerShell with the **Run as administrator** option.</span></span>

- <span data-ttu-id="311d2-174">Om du vill visa sessionsinställningar på datorn måste du vara medlem i gruppen Administratörer på datorn.</span><span class="sxs-lookup"><span data-stu-id="311d2-174">To view the session configurations on the computer, you must be a member of the Administrators group on the computer.</span></span>

- <span data-ttu-id="311d2-175">Om du vill köra ett `Get-PSSessionConfiguration` kommando på en fjärrdator måste autentiseringen Credential Security Service Provider (CredSSP) vara aktive rad i klient inställningarna på den lokala datorn (med hjälp av `Enable-WSManCredSSP` cmdleten) och i tjänst inställningarna på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="311d2-175">To run a `Get-PSSessionConfiguration` command on a remote computer, Credential Security Service Provider (CredSSP) authentication must be enabled in the client settings on the local computer (by using the `Enable-WSManCredSSP` cmdlet) and in the service settings on the remote computer.</span></span> <span data-ttu-id="311d2-176">Du måste också använda **CredSSP** -värdet för parametern **Authentication** när du etablerar fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="311d2-176">Also, you must use the **CredSSP** value of the **Authentication** parameter when establishing the remote session.</span></span> <span data-ttu-id="311d2-177">Annars nekas åtkomst.</span><span class="sxs-lookup"><span data-stu-id="311d2-177">Otherwise, access is denied.</span></span>

- <span data-ttu-id="311d2-178">Antecknings egenskaperna för det objekt som `Get-PSSessionConfiguration` returneras visas bara för objektet när de har ett värde.</span><span class="sxs-lookup"><span data-stu-id="311d2-178">The note properties of the object that `Get-PSSessionConfiguration` returns appear on the object only when they have a value.</span></span> <span data-ttu-id="311d2-179">Endast sessionsinställningar som skapats med hjälp av en konfigurations fil för sessionen har alla definierade egenskaper.</span><span class="sxs-lookup"><span data-stu-id="311d2-179">Only session configurations that were created by using a session configuration file have all the defined properties.</span></span>

- <span data-ttu-id="311d2-180">Egenskaperna för ett konfigurations objekt för en session varierar beroende på vilka alternativ som har angetts för konfigurationen av sessionen och värdena för dessa alternativ.</span><span class="sxs-lookup"><span data-stu-id="311d2-180">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="311d2-181">Dessutom har sessionsinställningar som använder en konfigurations fil för sessionen ytterligare egenskaper.</span><span class="sxs-lookup"><span data-stu-id="311d2-181">Also, session configurations that use a session configuration file have additional properties.</span></span>

- <span data-ttu-id="311d2-182">Du kan använda kommandona i WSMan: Drive för att ändra egenskaperna för sessionens konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="311d2-182">You can use commands in the WSMan: drive to change the properties of session configurations.</span></span>
  <span data-ttu-id="311d2-183">Du kan dock inte använda WSMan:-enheten i PowerShell 2,0 för att ändra konfigurations egenskaper för sessionen som introduceras i PowerShell 3,0, till exempel **OutputBufferingMode**.</span><span class="sxs-lookup"><span data-stu-id="311d2-183">However, you cannot use the WSMan: drive in PowerShell 2.0 to change session configuration properties that are introduced in PowerShell 3.0, such as **OutputBufferingMode**.</span></span> <span data-ttu-id="311d2-184">PowerShell 2,0-kommandon genererar inte ett fel, men de är ineffektiva.</span><span class="sxs-lookup"><span data-stu-id="311d2-184">PowerShell 2.0 commands do not generate an error, but they are ineffective.</span></span> <span data-ttu-id="311d2-185">Om du vill ändra de egenskaper som introduceras i PowerShell 3,0 använder du kommandot WSMan: Drive i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="311d2-185">To change properties introduced in PowerShell 3.0, use the WSMan: drive in PowerShell 3.0.</span></span>

## <span data-ttu-id="311d2-186">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="311d2-186">RELATED LINKS</span></span>

[<span data-ttu-id="311d2-187">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="311d2-187">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="311d2-188">Aktivera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="311d2-188">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="311d2-189">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="311d2-189">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="311d2-190">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="311d2-190">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="311d2-191">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="311d2-191">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="311d2-192">Registrera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="311d2-192">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="311d2-193">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="311d2-193">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="311d2-194">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="311d2-194">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="311d2-195">Avregistrera-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="311d2-195">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="311d2-196">WSMan-Provider</span><span class="sxs-lookup"><span data-stu-id="311d2-196">WSMan Provider</span></span>](../microsoft.wsman.management/about/about_WSMan_Provider.md)

[<span data-ttu-id="311d2-197">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="311d2-197">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="311d2-198">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="311d2-198">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)

