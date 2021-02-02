---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-pssessionconfiguration?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSSessionConfiguration
ms.openlocfilehash: a5aa70521841b3b05d34623ff92ebbf9e3471fd1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710495"
---
# <span data-ttu-id="3d531-102">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="3d531-102">Get-PSSessionConfiguration</span></span>

## <span data-ttu-id="3d531-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="3d531-103">SYNOPSIS</span></span>
<span data-ttu-id="3d531-104">Hämtar de registrerade sessionsbaserade på datorn.</span><span class="sxs-lookup"><span data-stu-id="3d531-104">Gets the registered session configurations on the computer.</span></span>

## <span data-ttu-id="3d531-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3d531-105">SYNTAX</span></span>

```
Get-PSSessionConfiguration [[-Name] <String[]>] [-Force] [<CommonParameters>]
```

## <span data-ttu-id="3d531-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="3d531-106">DESCRIPTION</span></span>

<span data-ttu-id="3d531-107">`Get-PSSessionConfiguration`Cmdlet: en hämtar de sessionsinställningar som har registrerats på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="3d531-107">The `Get-PSSessionConfiguration` cmdlet gets the session configurations that have been registered on the local computer.</span></span> <span data-ttu-id="3d531-108">Det här är en avancerad cmdlet som är avsedd att användas av system administratörer för att hantera konfigurationer för anpassade sessioner för sina användare.</span><span class="sxs-lookup"><span data-stu-id="3d531-108">This is an advanced cmdlet that is designed to be used by system administrators to manage customized session configurations for their users.</span></span>

<span data-ttu-id="3d531-109">Från och med PowerShell 3,0 kan du definiera egenskaperna för en session-konfiguration med hjälp av en PSSC-fil (session Configuration).</span><span class="sxs-lookup"><span data-stu-id="3d531-109">Beginning in PowerShell 3.0, you can define the properties of a session configuration by using a session configuration (.pssc) file.</span></span> <span data-ttu-id="3d531-110">Med den här funktionen kan du skapa anpassade och begränsade sessioner utan att skriva ett dator program.</span><span class="sxs-lookup"><span data-stu-id="3d531-110">This feature lets you create customized and restricted sessions without writing a computer program.</span></span> <span data-ttu-id="3d531-111">Mer information om konfigurationsfiler för sessioner finns [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span><span class="sxs-lookup"><span data-stu-id="3d531-111">For more information about session configuration files, see [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>

<span data-ttu-id="3d531-112">Från och med PowerShell 3,0 har nya antecknings egenskaper också lagts till i sessionens konfigurations objekt som `Get-PSSessionConfiguration` returneras.</span><span class="sxs-lookup"><span data-stu-id="3d531-112">Also, beginning in PowerShell 3.0, new note properties have been added to the session configuration object that `Get-PSSessionConfiguration` returns.</span></span> <span data-ttu-id="3d531-113">De här egenskaperna gör det enklare för användare och konfiguration av sessioner att granska och jämföra sessionsbaserade.</span><span class="sxs-lookup"><span data-stu-id="3d531-113">These properties make it easier for users and session configuration authors to examine and compare session configurations.</span></span>

<span data-ttu-id="3d531-114">Använd cmdleten för att skapa och registrera en konfiguration av en session `Register-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="3d531-114">To create and register a session configuration, use the `Register-PSSessionConfiguration` cmdlet.</span></span>
<span data-ttu-id="3d531-115">För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="3d531-115">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

## <span data-ttu-id="3d531-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="3d531-116">EXAMPLES</span></span>

### <span data-ttu-id="3d531-117">Exempel 1 – Hämta konfigurationer för sessioner på den lokala datorn</span><span class="sxs-lookup"><span data-stu-id="3d531-117">Example 1 - Get session configurations on the local computer</span></span>

```powershell
Get-PSSessionConfiguration
```

### <span data-ttu-id="3d531-118">Exempel 2 – Hämta två standardkonfigurationer för sessioner</span><span class="sxs-lookup"><span data-stu-id="3d531-118">Example 2 - Get the two default session configurations</span></span>

<span data-ttu-id="3d531-119">Kommandot använder **Name** -parametern för `Get-PSSessionConfiguration` att bara hämta sessionsinställningar med namn som börjar med "Microsoft".</span><span class="sxs-lookup"><span data-stu-id="3d531-119">The command uses the **Name** parameter of `Get-PSSessionConfiguration` to get only the session configurations with names that begin with "Microsoft".</span></span>

```powershell
Get-PSSessionConfiguration -Name Microsoft*
```

```Output
Name                      PSVersion  StartupScript        Permission
----                      ---------  -------------        ----------
microsoft.powershell      5.1                             BUILTIN\Administrators AccessAll...
microsoft.powershell32    5.1                             BUILTIN\Administrators AccessAll...
```

### <span data-ttu-id="3d531-120">Exempel 3 – Hämta egenskaperna och värdena för en konfiguration av sessionen</span><span class="sxs-lookup"><span data-stu-id="3d531-120">Example 3 - Get the properties and values of a session configuration</span></span>

<span data-ttu-id="3d531-121">I det här exemplet visas egenskaper och egenskaps värden för en sessionsfil som skapats med hjälp av en konfigurations fil för sessionen.</span><span class="sxs-lookup"><span data-stu-id="3d531-121">This example shows the properties and property values of a session configuration that was created by using a session configuration file.</span></span>

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

<span data-ttu-id="3d531-122">Exemplet använder `Get-PSSessionConfiguration` cmdleten för att hämta den fullständiga konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="3d531-122">The example uses the `Get-PSSessionConfiguration` cmdlet to get the full session configuration.</span></span> <span data-ttu-id="3d531-123">En pipeline-operator skickar fullständig sessionsinformation till `Format-List` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="3d531-123">A pipeline operator sends the Full session configuration to the `Format-List` cmdlet.</span></span> <span data-ttu-id="3d531-124">**Egenskaps** parametern med värdet `*` (alla) leder `Format-List` för att visa alla egenskaper och värden för objektet i en lista.</span><span class="sxs-lookup"><span data-stu-id="3d531-124">The **Property** parameter with a value of `*` (all) directs `Format-List` to display all the properties and values of the object in a list.</span></span>

<span data-ttu-id="3d531-125">Utdata innehåller användbar information, inklusive författaren av sessionens konfiguration, typ av session, språk läge och körnings princip för sessioner som skapas med den här konfigurationen, session kvoter och den fullständiga sökvägen till sessionens konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="3d531-125">The output includes useful information, including the author of the session configuration, the session type, language mode, and execution policy of sessions that are created with this session configuration, session quotas, and the full path to the session configuration file.</span></span>

<span data-ttu-id="3d531-126">Den här vyn av en sessions konfiguration används för sessioner som innehåller en konfigurations fil för sessionen.</span><span class="sxs-lookup"><span data-stu-id="3d531-126">This view of a session configuration is used for sessions that include a session configuration file.</span></span>
<span data-ttu-id="3d531-127">Mer information om konfigurationsfiler för sessioner finns [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span><span class="sxs-lookup"><span data-stu-id="3d531-127">For more information about session configuration files, see [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>

### <span data-ttu-id="3d531-128">Exempel 4 – ett annat sätt att titta på sessionens konfigurationer</span><span class="sxs-lookup"><span data-stu-id="3d531-128">Example 4 - Another way to look at the session configurations</span></span>

<span data-ttu-id="3d531-129">I det här exemplet används `Get-ChildItem` cmdleten (alias `dir` ) i WSMan: Provider-enheten för att titta på innehållet i plugin-noden.</span><span class="sxs-lookup"><span data-stu-id="3d531-129">This example uses the `Get-ChildItem` cmdlet (alias `dir`) in the WSMan: provider drive to look at the content of the Plugin node.</span></span> <span data-ttu-id="3d531-130">Detta är ett annat sätt att titta på sessionens konfigurationer på datorn.</span><span class="sxs-lookup"><span data-stu-id="3d531-130">This is another way to look at the session configurations on the computer.</span></span>

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

<span data-ttu-id="3d531-131">**Plugin** -noden innehåller **ContainerElement** -objekt (Microsoft. WSMan. Management. WSManConfigContainerElement) som representerar registrerade PowerShell-sessionsbaserade konfigurationer, tillsammans med andra plugin-program för WS-Management.</span><span class="sxs-lookup"><span data-stu-id="3d531-131">The **PlugIn** node contains **ContainerElement** objects (Microsoft.WSMan.Management.WSManConfigContainerElement) that represent the registered PowerShell session configurations, along with other plug-ins for WS-Management.</span></span>

### <span data-ttu-id="3d531-132">Exempel 6 – Visa sessionsinställningar på en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="3d531-132">Example 6 - View session configurations on a remote computer</span></span>

<span data-ttu-id="3d531-133">I det här exemplet visas hur du använder WSMan-providern för att Visa sessionsinställningar på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="3d531-133">This example shows how to use the WSMan provider to view the session configurations on a remote computer.</span></span> <span data-ttu-id="3d531-134">Den här metoden ger inte så mycket information som ett `Get-PSSessionConfiguration` kommando, men användaren behöver inte vara medlem i gruppen Administratörer för att köra denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3d531-134">This method does not provide as much information as a `Get-PSSessionConfiguration` command, but the user does not need to be a member of the Administrators group to run this cmdlet.</span></span>

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

<span data-ttu-id="3d531-135">`Connect-WSMan`Cmdleten ansluter till WinRM-tjänsten på fjärrdatorn Server01.</span><span class="sxs-lookup"><span data-stu-id="3d531-135">The `Connect-WSMan` cmdlet connects to the WinRM service on the Server01 remote computer.</span></span> <span data-ttu-id="3d531-136">`Get-ChildItem`Cmdleten (alias `dir` ) för WSMan: Drive hämtar objekten i **Server01\Plugin** -sökvägen.</span><span class="sxs-lookup"><span data-stu-id="3d531-136">The `Get-ChildItem` cmdlet (alias `dir`) of the WSMan: drive gets the items in the **Server01\Plugin** path.</span></span> <span data-ttu-id="3d531-137">Utdata visar objekten i plugin-katalogen på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="3d531-137">The output shows the items in the Plugin directory on the Server01 computer.</span></span> <span data-ttu-id="3d531-138">Objekten inkluderar sessionsinställningar, som är en typ av WSMan-plugin-program, tillsammans med andra typer av plugin-program på datorn.</span><span class="sxs-lookup"><span data-stu-id="3d531-138">The items include the session configurations, which are a type of WSMan plug-in, along with other types of plug-ins on the computer.</span></span>

### <span data-ttu-id="3d531-139">Exempel 7 – Hämta detaljerade sessionsinställningar från en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="3d531-139">Example 7 - Get detailed session configurations from a remote computer</span></span>

<span data-ttu-id="3d531-140">Det här exemplet visar hur du kör ett `Get-PSSessionConfiguration` kommando på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="3d531-140">This example shows how to run a `Get-PSSessionConfiguration` command on a remote computer.</span></span> <span data-ttu-id="3d531-141">Kommandot kräver att CredSSP-delegering aktive ras i klient inställningarna på den lokala datorn och i tjänst inställningarna på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="3d531-141">The command requires that CredSSP delegation be enabled in the client settings on the local computer and in the service settings on the remote computer.</span></span>

<span data-ttu-id="3d531-142">Om du vill köra kommandona i det här exemplet måste du vara medlem i gruppen Administratörer på den lokala datorn och fjärrdatorn och du måste starta PowerShell med alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="3d531-142">To run the commands in this example, you must be a member of the Administrators group on the local and remote computers and you must start PowerShell with the **Run as administrator** option.</span></span>

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

<span data-ttu-id="3d531-143">`Enable-WSManCredSSP`Cmdlet: en aktiverar **CredSSP** -delegering på Server01, den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="3d531-143">The `Enable-WSManCredSSP` cmdlet enables **CredSSP** delegation on Server01, the local computer.</span></span> <span data-ttu-id="3d531-144">`Connect-WSMan`Cmdleten ansluter till Server02-datorn.</span><span class="sxs-lookup"><span data-stu-id="3d531-144">The `Connect-WSMan` cmdlet connects to Server02 computer.</span></span> <span data-ttu-id="3d531-145">Den här åtgärden lägger till en nod för Server02 till enheten WSMan: på den lokala datorn, så att du kan visa och ändra WS-Management inställningar på Server02-datorn.</span><span class="sxs-lookup"><span data-stu-id="3d531-145">This action adds a node for Server02 to the WSMan: drive on the local computer, allowing you to view and change the WS-Management settings on the Server02 computer.</span></span> <span data-ttu-id="3d531-146">`Set-Item`Cmdleten ändrar värdet för **CredSSP** -objektet i noden tjänst på den Server02 datorn till **True**.</span><span class="sxs-lookup"><span data-stu-id="3d531-146">The `Set-Item` cmdlet changes the value of the **CredSSP** item in the Service node of the Server02 computer to **True**.</span></span> <span data-ttu-id="3d531-147">Detta konfigurerar tjänst inställningarna på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="3d531-147">This configures the service settings on the remote computer.</span></span> <span data-ttu-id="3d531-148">`Invoke-Command`Cmdleten kör `Get-PSSessionConfiguration` kommandot på Server02-datorn.</span><span class="sxs-lookup"><span data-stu-id="3d531-148">The `Invoke-Command` cmdlet runs the`Get-PSSessionConfiguration` command on the Server02 computer.</span></span> <span data-ttu-id="3d531-149">Kommandot använder parametern **Credential** och använder parametern **Authentication** med värdet **CredSSP**.</span><span class="sxs-lookup"><span data-stu-id="3d531-149">The command uses the **Credential** parameter, and it uses the **Authentication** parameter with a value of **CredSSP**.</span></span> <span data-ttu-id="3d531-150">Utdata visar sessionens konfigurationer på Server02-fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="3d531-150">The output shows the session configurations on the Server02 remote computer.</span></span>

### <span data-ttu-id="3d531-151">Exempel 8 – Hämta resurs-URI för en konfiguration av sessionen</span><span class="sxs-lookup"><span data-stu-id="3d531-151">Example 8 - Get the resource URI of a session configuration</span></span>

<span data-ttu-id="3d531-152">Det här exemplet är användbart för att ange värdet för `$PSSessionConfigurationName` variabeln Preference, som tar en resurs-URI.</span><span class="sxs-lookup"><span data-stu-id="3d531-152">This example is useful for setting the value of the `$PSSessionConfigurationName` preference variable, which takes a resource URI.</span></span>

```powershell
(Get-PSSessionConfiguration -Name CustomShell).resourceURI
```

```Output
http://schemas.microsoft.com/powershell/microsoft.CustomShell
```

<span data-ttu-id="3d531-153">`$PSSessionConfigurationName`Variabeln anger standard konfigurationen som används när du skapar en session.</span><span class="sxs-lookup"><span data-stu-id="3d531-153">The `$PSSessionConfigurationName` variable specifies the default configuration that is used when you create a session.</span></span> <span data-ttu-id="3d531-154">Den här variabeln anges på den lokala datorn, men den anger en konfiguration på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="3d531-154">This variable is set on the local computer, but it specifies a configuration on the remote computer.</span></span> <span data-ttu-id="3d531-155">Mer information om `$PSSessionConfiguration` variabeln finns i [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="3d531-155">For more information about the `$PSSessionConfiguration` variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

## <span data-ttu-id="3d531-156">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="3d531-156">PARAMETERS</span></span>

### <span data-ttu-id="3d531-157">-Force</span><span class="sxs-lookup"><span data-stu-id="3d531-157">-Force</span></span>

<span data-ttu-id="3d531-158">Inaktiverar uppmaningen att starta om WinRM-tjänsten om tjänsten inte redan körs.</span><span class="sxs-lookup"><span data-stu-id="3d531-158">Suppresses the prompt to restart the WinRM service, if the service is not already running.</span></span>

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

### <span data-ttu-id="3d531-159">-Name</span><span class="sxs-lookup"><span data-stu-id="3d531-159">-Name</span></span>

<span data-ttu-id="3d531-160">Hämtar endast sessionsdata med angivet namn eller namn mönster.</span><span class="sxs-lookup"><span data-stu-id="3d531-160">Gets only the session configurations with the specified name or name pattern.</span></span> <span data-ttu-id="3d531-161">Ange ett eller flera konfigurations namn för sessionen.</span><span class="sxs-lookup"><span data-stu-id="3d531-161">Enter one or more session configuration names.</span></span> <span data-ttu-id="3d531-162">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="3d531-162">Wildcards are permitted.</span></span>

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

### <span data-ttu-id="3d531-163">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3d531-163">CommonParameters</span></span>

<span data-ttu-id="3d531-164">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3d531-164">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3d531-165">Mer information finns i [about_CommonParameters](./About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="3d531-165">For more information, see [about_CommonParameters](./About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="3d531-166">INDATA</span><span class="sxs-lookup"><span data-stu-id="3d531-166">INPUTS</span></span>

### <span data-ttu-id="3d531-167">Inga</span><span class="sxs-lookup"><span data-stu-id="3d531-167">None</span></span>

<span data-ttu-id="3d531-168">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3d531-168">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="3d531-169">UTDATA</span><span class="sxs-lookup"><span data-stu-id="3d531-169">OUTPUTS</span></span>

### <span data-ttu-id="3d531-170">Microsoft. PowerShell. commands. PSSessionConfigurationCommands # PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="3d531-170">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration</span></span>

## <span data-ttu-id="3d531-171">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="3d531-171">NOTES</span></span>

- <span data-ttu-id="3d531-172">Starta PowerShell med alternativet **Kör som administratör** för att köra denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3d531-172">To run this cmdlet, start PowerShell with the **Run as administrator** option.</span></span>

- <span data-ttu-id="3d531-173">Om du vill visa sessionsinställningar på datorn måste du vara medlem i gruppen Administratörer på datorn.</span><span class="sxs-lookup"><span data-stu-id="3d531-173">To view the session configurations on the computer, you must be a member of the Administrators group on the computer.</span></span>

- <span data-ttu-id="3d531-174">Om du vill köra ett `Get-PSSessionConfiguration` kommando på en fjärrdator måste autentiseringen Credential Security Service Provider (CredSSP) vara aktive rad i klient inställningarna på den lokala datorn (med hjälp av `Enable-WSManCredSSP` cmdleten) och i tjänst inställningarna på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="3d531-174">To run a `Get-PSSessionConfiguration` command on a remote computer, Credential Security Service Provider (CredSSP) authentication must be enabled in the client settings on the local computer (by using the `Enable-WSManCredSSP` cmdlet) and in the service settings on the remote computer.</span></span> <span data-ttu-id="3d531-175">Du måste också använda **CredSSP** -värdet för parametern **Authentication** när du etablerar fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="3d531-175">Also, you must use the **CredSSP** value of the **Authentication** parameter when establishing the remote session.</span></span> <span data-ttu-id="3d531-176">Annars nekas åtkomst.</span><span class="sxs-lookup"><span data-stu-id="3d531-176">Otherwise, access is denied.</span></span>

- <span data-ttu-id="3d531-177">Antecknings egenskaperna för det objekt som `Get-PSSessionConfiguration` returneras visas bara för objektet när de har ett värde.</span><span class="sxs-lookup"><span data-stu-id="3d531-177">The note properties of the object that `Get-PSSessionConfiguration` returns appear on the object only when they have a value.</span></span> <span data-ttu-id="3d531-178">Endast sessionsinställningar som skapats med hjälp av en konfigurations fil för sessionen har alla definierade egenskaper.</span><span class="sxs-lookup"><span data-stu-id="3d531-178">Only session configurations that were created by using a session configuration file have all the defined properties.</span></span>

- <span data-ttu-id="3d531-179">Egenskaperna för ett konfigurations objekt för en session varierar beroende på vilka alternativ som har angetts för konfigurationen av sessionen och värdena för dessa alternativ.</span><span class="sxs-lookup"><span data-stu-id="3d531-179">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="3d531-180">Dessutom har sessionsinställningar som använder en konfigurations fil för sessionen ytterligare egenskaper.</span><span class="sxs-lookup"><span data-stu-id="3d531-180">Also, session configurations that use a session configuration file have additional properties.</span></span>

- <span data-ttu-id="3d531-181">Du kan använda kommandona i WSMan: Drive för att ändra egenskaperna för sessionens konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="3d531-181">You can use commands in the WSMan: drive to change the properties of session configurations.</span></span>
  <span data-ttu-id="3d531-182">Du kan dock inte använda WSMan:-enheten i PowerShell 2,0 för att ändra konfigurations egenskaper för sessionen som introduceras i PowerShell 3,0, till exempel **OutputBufferingMode**.</span><span class="sxs-lookup"><span data-stu-id="3d531-182">However, you cannot use the WSMan: drive in PowerShell 2.0 to change session configuration properties that are introduced in PowerShell 3.0, such as **OutputBufferingMode**.</span></span> <span data-ttu-id="3d531-183">PowerShell 2,0-kommandon genererar inte ett fel, men de är ineffektiva.</span><span class="sxs-lookup"><span data-stu-id="3d531-183">PowerShell 2.0 commands do not generate an error, but they are ineffective.</span></span> <span data-ttu-id="3d531-184">Om du vill ändra de egenskaper som introduceras i PowerShell 3,0 använder du kommandot WSMan: Drive i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="3d531-184">To change properties introduced in PowerShell 3.0, use the WSMan: drive in PowerShell 3.0.</span></span>

## <span data-ttu-id="3d531-185">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="3d531-185">RELATED LINKS</span></span>

[<span data-ttu-id="3d531-186">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="3d531-186">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="3d531-187">Aktivera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="3d531-187">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="3d531-188">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="3d531-188">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="3d531-189">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="3d531-189">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="3d531-190">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="3d531-190">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="3d531-191">Registrera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="3d531-191">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="3d531-192">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="3d531-192">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="3d531-193">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="3d531-193">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="3d531-194">Avregistrera-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="3d531-194">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="3d531-195">WSMan-Provider</span><span class="sxs-lookup"><span data-stu-id="3d531-195">WSMan Provider</span></span>](../microsoft.wsman.management/about/about_WSMan_Provider.md)

[<span data-ttu-id="3d531-196">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="3d531-196">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="3d531-197">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="3d531-197">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
