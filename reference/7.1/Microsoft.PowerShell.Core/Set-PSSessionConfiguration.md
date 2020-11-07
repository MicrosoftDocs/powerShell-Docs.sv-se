---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-pssessionconfiguration?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSSessionConfiguration
ms.openlocfilehash: 788e7b9d261a862658f4cf7453f35228dd3ffab6
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94345858"
---
# <span data-ttu-id="6a5bc-103">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="6a5bc-103">Set-PSSessionConfiguration</span></span>

## <span data-ttu-id="6a5bc-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="6a5bc-104">SYNOPSIS</span></span>
<span data-ttu-id="6a5bc-105">Ändrar egenskaperna för en registrerad session-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-105">Changes the properties of a registered session configuration.</span></span>

## <span data-ttu-id="6a5bc-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6a5bc-106">SYNTAX</span></span>

### <span data-ttu-id="6a5bc-107">NameParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="6a5bc-107">NameParameterSet (Default)</span></span>

```
Set-PSSessionConfiguration [-Name] <String> [-ApplicationBase <String>] [-RunAsCredential <PSCredential>]
 [-ThreadOptions <PSThreadOptions>] [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess]
 [-StartupScript <String>] [-MaximumReceivedDataSizePerCommandMB <Double>]
 [-MaximumReceivedObjectSizeMB <Double>] [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI]
 [-Force] [-NoServiceRestart] [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>]
 [-TransportOption <PSTransportOption>] [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6a5bc-108">AssemblyNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="6a5bc-108">AssemblyNameParameterSet</span></span>

```
Set-PSSessionConfiguration [-Name] <String> [-AssemblyName] <String> [-ApplicationBase <String>]
 [-ConfigurationTypeName] <String> [-RunAsCredential <PSCredential>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>] [-TransportOption <PSTransportOption>]
 [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="6a5bc-109">SessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="6a5bc-109">SessionConfigurationFile</span></span>

```
Set-PSSessionConfiguration [-Name] <String> [-RunAsCredential <PSCredential>]
 [-ThreadOptions <PSThreadOptions>] [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess]
 [-StartupScript <String>] [-MaximumReceivedDataSizePerCommandMB <Double>]
 [-MaximumReceivedObjectSizeMB <Double>] [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI]
 [-Force] [-NoServiceRestart] [-TransportOption <PSTransportOption>] -Path <String> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="6a5bc-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="6a5bc-110">DESCRIPTION</span></span>

<span data-ttu-id="6a5bc-111">`Set-PSSessionConfiguration`Cmdleten ändrar egenskaperna för sessionens konfigurationer på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-111">The `Set-PSSessionConfiguration` cmdlet changes the properties of the session configurations on the local computer.</span></span>

<span data-ttu-id="6a5bc-112">Använd parametern **Name** för att identifiera den konfiguration av sessionen som du vill ändra.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-112">Use the **Name** parameter to identify the session configuration that you want to change.</span></span> <span data-ttu-id="6a5bc-113">Använd de andra parametrarna för att ange nya värden för egenskaperna för sessionen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-113">Use the other parameters to specify new values for the properties of the session configuration.</span></span> <span data-ttu-id="6a5bc-114">Om du vill ta bort ett egenskaps värde från konfigurationen och använda standardvärdet anger du en tom sträng ("") eller värdet `$Null` för motsvarande parameter.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-114">To delete a property value from the configuration, and use the default value, enter an empty string ("") or a value of `$Null` for the corresponding parameter.</span></span>

<span data-ttu-id="6a5bc-115">Från och med PowerShell 3,0 kan du använda en konfigurations fil för sessionen för att definiera en sessions-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-115">Starting in PowerShell 3.0, you can use a session configuration file to define a session configuration.</span></span> <span data-ttu-id="6a5bc-116">Den här funktionen ger en enkel och identifierad metod för att ange och ändra egenskaperna för sessioner som använder sessionen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-116">This feature provides a simple and discoverable method for setting and changing the properties of sessions that use the session configuration.</span></span> <span data-ttu-id="6a5bc-117">Om du vill ange en konfigurations fil för sessionen använder du parametern **Path** i `Set-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="6a5bc-117">To specify a session configuration file, use the **Path** parameter of `Set-PSSessionConfiguration`.</span></span> <span data-ttu-id="6a5bc-118">Information om konfigurationsfiler för sessioner finns [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span><span class="sxs-lookup"><span data-stu-id="6a5bc-118">For information about session configuration files, see [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>
<span data-ttu-id="6a5bc-119">Information om hur du skapar och ändrar en konfigurations fil för en session finns i `New-PSSessionConfigurationFile` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-119">For information about how to create and modify a session configuration file, see the `New-PSSessionConfigurationFile` cmdlet.</span></span>

<span data-ttu-id="6a5bc-120">Sessionsbaserade definierar miljön för fjärrsessioner ( **PSSessions** ) som ansluter till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-120">Session configurations define the environment of remote sessions ( **PSSessions** ) that connect to the local computer.</span></span> <span data-ttu-id="6a5bc-121">Varje **PSSession** använder en konfiguration av sessionen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-121">Every **PSSession** uses a session configuration.</span></span> <span data-ttu-id="6a5bc-122">Konfigurationen av sessionen bestämmer funktionerna i **PSSession** , till exempel de moduler som är tillgängliga i sessionen, vilka cmdlets som tillåts köras, språk läge, kvoter och tids gränser.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-122">The session configuration determines the features of the **PSSession** , such as the modules that are available in the session, the cmdlets that are permitted to run, the language mode, quotas, and timeouts.</span></span> <span data-ttu-id="6a5bc-123">Säkerhets beskrivningen för konfigurationen av sessionen avgör vem som kan använda sessionen för att ansluta till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-123">The security descriptor of the session configuration determines who can use the session configuration to connect to the local computer.</span></span> <span data-ttu-id="6a5bc-124">För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="6a5bc-124">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

<span data-ttu-id="6a5bc-125">Använd `Get-PSSessionConfiguration` cmdleten eller WSMan-providern för att se egenskaperna för en sessions konfiguration.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-125">To see the properties of a session configuration, use the `Get-PSSessionConfiguration` cmdlet or the WSMan Provider.</span></span> <span data-ttu-id="6a5bc-126">Om du vill ha mer information om WSMan-providern skriver du `Get-Help WSMan` .</span><span class="sxs-lookup"><span data-stu-id="6a5bc-126">For more information about the WSMan Provider, type `Get-Help WSMan`.</span></span>

## <span data-ttu-id="6a5bc-127">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="6a5bc-127">EXAMPLES</span></span>

### <span data-ttu-id="6a5bc-128">Exempel 1: skapa och ändra en konfiguration av sessionen</span><span class="sxs-lookup"><span data-stu-id="6a5bc-128">Example 1: Create and change a session configuration</span></span>

<span data-ttu-id="6a5bc-129">Det här exemplet visar hur du lägger till och tar bort ett start skript från en konfiguration.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-129">This example shows how to add and remove a startup script from a configuration.</span></span>

<span data-ttu-id="6a5bc-130">Det första kommandot skapar **AdminShell** -konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-130">The first command creates the **AdminShell** configuration.</span></span> <span data-ttu-id="6a5bc-131">Det andra kommandot lägger till `AdminConfig.ps1` skriptet i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-131">The second command adds the `AdminConfig.ps1` script to the configuration.</span></span> <span data-ttu-id="6a5bc-132">Ändringen gäller när du startar om **WinRM**.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-132">The change is effective when you restart **WinRM**.</span></span>
<span data-ttu-id="6a5bc-133">Det tredje kommandot tar bort `AdminConfig.ps1` skriptet från konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-133">The third command removes the `AdminConfig.ps1` script from the configuration.</span></span>

```powershell
Register-PSSessionConfiguration -Name "AdminShell" -AssemblyName "C:\Shells\AdminShell.dll" -ConfigurationTypeName "AdminClass"
Set-PSSessionConfiguration -Name "AdminShell" -StartupScript "AdminConfig.ps1"
Set-PSSessionConfiguration -Name "AdminShell" -StartupScript $Null
```

### <span data-ttu-id="6a5bc-134">Exempel 2: Visa resultat</span><span class="sxs-lookup"><span data-stu-id="6a5bc-134">Example 2: Display results</span></span>

<span data-ttu-id="6a5bc-135">Det här exemplet ökar värdet för egenskapen **MaximumReceivedObjectSizeMB** till 20.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-135">This example increases the value of the **MaximumReceivedObjectSizeMB** property to 20.</span></span> <span data-ttu-id="6a5bc-136">Det här kommandot kräver också att du startar om **WinRM** -tjänsten.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-136">This command also prompts you to restart the **WinRM** service.</span></span> <span data-ttu-id="6a5bc-137">Ändringen gäller inte förrän **WinRM** -tjänsten har startats om.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-137">The change is not effective until the **WinRM** service is restarted.</span></span>

```powershell
Set-PSSessionConfiguration -Name "IncObj" -MaximumReceivedObjectSizeMB 20
```

```Output
WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin\IncObj\InitializationParameters

ParamName                       ParamValue
---------                       ----------
psmaximumreceivedobjectsizemb   20

"Restart WinRM service"
WinRM service need to be restarted to make the changes effective. Do you want to run the command "restart-service winrm"?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): y
```

### <span data-ttu-id="6a5bc-138">Exempel 3: Visa resultat på olika sätt</span><span class="sxs-lookup"><span data-stu-id="6a5bc-138">Example 3: Display results in different ways</span></span>

<span data-ttu-id="6a5bc-139">I det här exemplet `Set-PSSessionConfiguration` ändrar Start skriptet i **MaintenanceShell** -sessionen till `Maintenance.ps1` .</span><span class="sxs-lookup"><span data-stu-id="6a5bc-139">In this example, `Set-PSSessionConfiguration` changes the startup script in the **MaintenanceShell** session configuration to `Maintenance.ps1`.</span></span> <span data-ttu-id="6a5bc-140">Resultatet visar ändringen och du ombeds att starta om **WinRM** -tjänsten.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-140">The output shows the change and prompts you to restart the **WinRM** service.</span></span> <span data-ttu-id="6a5bc-141">Svaret är "y" (Ja).</span><span class="sxs-lookup"><span data-stu-id="6a5bc-141">The response is "y" (yes).</span></span>

<span data-ttu-id="6a5bc-142">`Get-PSSessionConfiguration` hämtar konfigurationen för **MaintenanceShell** -sessionen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-142">`Get-PSSessionConfiguration` gets the **MaintenanceShell** session configuration.</span></span> <span data-ttu-id="6a5bc-143">Pipeline-operatorn (|) skickar resultatet från kommandot till `Format-List` , som visar alla egenskaper för konfigurationsobjektet i en lista.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-143">The pipeline operator (|) sends the results of the command to `Format-List`, which displays all the properties of the configuration object in a list.</span></span> <span data-ttu-id="6a5bc-144">Därefter visar vi initierings parametrarna för **MaintenanceShell** -konfigurationen med hjälp av WSMan-providern.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-144">Next, using the WSMan provider, we view the initialization parameters for the **MaintenanceShell** configuration.</span></span> <span data-ttu-id="6a5bc-145">`Get-ChildItem` (alias `dir` ) hämtar de underordnade objekten i **InitializationParameters** -noden för **MaintenanceShell** -plugin-programmet.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-145">`Get-ChildItem` (alias `dir`) gets the child items in the **InitializationParameters** node for the **MaintenanceShell** plug-in.</span></span> <span data-ttu-id="6a5bc-146">Om du vill ha mer information om WSMan-providern skriver du `Get-Help wsman` .</span><span class="sxs-lookup"><span data-stu-id="6a5bc-146">For more information about the WSMan provider, type `Get-Help wsman`.</span></span>

```powershell
Set-PSSessionConfiguration -Name "MaintenanceShell" -StartupScript "C:\ps-test\Maintenance.ps1"
```

```Output
WSManConfig: Microsoft.WSMan.Management\WSMan::localhost\Plugin\MaintenanceShell\InitializationParameters

ParamName            ParamValue
---------            ----------
startupscript        c:\ps-test\Mainte...

"Restart WinRM service"
WinRM service need to be restarted to make the changes effective. Do you want to run
the command "restart-service winrm"?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): y

```

```powershell
Get-PSSessionConfiguration MaintenanceShell | Format-List -Property *
```

```Output
xmlns            : http://schemas.microsoft.com/wbem/wsman/1/config/PluginConfiguration
Name             : MaintenanceShell
Filename         : %windir%\system32\pwrshplugin.dll
SDKVersion       : 1
XmlRenderingType : text
lang             : en-US
PSVersion        : 2.0
startupscript    : c:\ps-test\Maintenance.ps1
ResourceUri      : http://schemas.microsoft.com/powershell/MaintenanceShell
SupportsOptions  : true
ExactMatch       : true
Capability       : {Shell}
Permission       :
```

```powershell
dir WSMan:\localhost\Plugin\MaintenanceShell\InitializationParameters
```

```Output
ParamName     ParamValue
---------     ----------
PSVersion     2.0
startupscript c:\ps-test\Maintenance.ps1
```

## <span data-ttu-id="6a5bc-147">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="6a5bc-147">PARAMETERS</span></span>

### <span data-ttu-id="6a5bc-148">-AccessMode</span><span class="sxs-lookup"><span data-stu-id="6a5bc-148">-AccessMode</span></span>

<span data-ttu-id="6a5bc-149">Aktiverar och inaktiverar konfigurationen av sessionen och avgör om den kan användas för fjärranslutna eller lokala sessioner på datorn.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-149">Enables and disables the session configuration and determines whether it can be used for remote or local sessions on the computer.</span></span> <span data-ttu-id="6a5bc-150">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="6a5bc-150">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="6a5bc-151">Inaktiverat</span><span class="sxs-lookup"><span data-stu-id="6a5bc-151">Disabled.</span></span> <span data-ttu-id="6a5bc-152">Inaktiverar konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-152">Disables the session configuration.</span></span> <span data-ttu-id="6a5bc-153">Den kan inte användas för fjärran sluten eller lokal åtkomst till datorn.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-153">It cannot be used for remote or local access to the computer.</span></span> <span data-ttu-id="6a5bc-154">Det här värdet anger egenskapen **Enabled** för session-konfigurationen ( `WSMan:\<ComputerName>\PlugIn\<SessionConfigurationName>\Enabled` ) till **false**.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-154">This value sets the **Enabled** property of the session configuration (`WSMan:\<ComputerName>\PlugIn\<SessionConfigurationName>\Enabled`) to **False**.</span></span>
- <span data-ttu-id="6a5bc-155">Inställningar.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-155">Local.</span></span> <span data-ttu-id="6a5bc-156">Lägger till en **Network_Deny_All** post i säkerhets beskrivningen för konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-156">Adds a **Network_Deny_All** entry to security descriptor of the session configuration.</span></span>
  <span data-ttu-id="6a5bc-157">Användare av den lokala datorn kan använda sessionen för att skapa en lokal loopback-session på samma dator, men fjärran vändare nekas åtkomst.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-157">Users of the local computer can use the session configuration to create a local loopback session on the same computer, but remote users are denied access.</span></span>
- <span data-ttu-id="6a5bc-158">Fjärrserveradministrationsverktyg.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-158">Remote.</span></span> <span data-ttu-id="6a5bc-159">Tar bort **Deny_All** och **Network_Deny_All** poster från säkerhets beskrivarna i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-159">Removes **Deny_All** and **Network_Deny_All** entries from the security descriptors of the session configuration.</span></span> <span data-ttu-id="6a5bc-160">Användare av lokala och fjärranslutna datorer kan använda sessionen för att skapa sessioner och köra kommandon på den här datorn.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-160">Users of local and remote computers can use the session configuration to create sessions and run commands on this computer.</span></span>

<span data-ttu-id="6a5bc-161">Standardvärdet är **fjärran sluten**.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-161">The default value is **Remote**.</span></span>

<span data-ttu-id="6a5bc-162">Andra cmdletar kan åsidosätta värdet för den här parametern senare.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-162">Other cmdlets can override the value of this parameter later.</span></span> <span data-ttu-id="6a5bc-163">Till exempel `Enable-PSRemoting` möjliggör cmdleten alla sessionsbaserade på datorn och tillåter fjärråtkomst till dem, och `Disable-PSRemoting` cmdleten tillåter endast lokal åtkomst till alla sessionsinställningar på datorn.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-163">For example, the `Enable-PSRemoting` cmdlet enables all session configurations on the computer and permits remote access to them, and the `Disable-PSRemoting` cmdlet permits only local access to all session configurations on the computer.</span></span>

<span data-ttu-id="6a5bc-164">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-164">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSessionConfigurationAccessMode
Parameter Sets: (All)
Aliases:
Accepted values: Disabled, Local, Remote

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a5bc-165">– ApplicationBase</span><span class="sxs-lookup"><span data-stu-id="6a5bc-165">-ApplicationBase</span></span>

<span data-ttu-id="6a5bc-166">Anger sökvägen till sammansättnings filen ( \* . dll) som anges i värdet för parametern **AssemblyName** .</span><span class="sxs-lookup"><span data-stu-id="6a5bc-166">Specifies the path of the assembly file (\*.dll) that is specified in the value of the **AssemblyName** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a5bc-167">-AssemblyName</span><span class="sxs-lookup"><span data-stu-id="6a5bc-167">-AssemblyName</span></span>

<span data-ttu-id="6a5bc-168">Anger sammansättnings namnet.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-168">Specifies the assembly name.</span></span> <span data-ttu-id="6a5bc-169">Denna cmdlet skapar en sessionsnyckel som baseras på en klass som har definierats i en sammansättning.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-169">This cmdlet creates a session configuration based on a class that is defined in an assembly.</span></span>

<span data-ttu-id="6a5bc-170">Ange fil namnet eller den fullständiga sökvägen till en Assembly. dll-fil som definierar en-sessions konfiguration.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-170">Enter the filename or full path of an assembly .dll file that defines a session configuration.</span></span> <span data-ttu-id="6a5bc-171">Om du bara anger fil namnet kan du ange sökvägen i värdet för parametern **ApplicationBase** .</span><span class="sxs-lookup"><span data-stu-id="6a5bc-171">If you enter only the file name, you can enter the path in the value of the **ApplicationBase** parameter.</span></span>

```yaml
Type: System.String
Parameter Sets: AssemblyNameParameterSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a5bc-172">-ConfigurationTypeName</span><span class="sxs-lookup"><span data-stu-id="6a5bc-172">-ConfigurationTypeName</span></span>

<span data-ttu-id="6a5bc-173">Anger typen av sessionsinformation som definieras i sammansättningen i parametern **AssemblyName** .</span><span class="sxs-lookup"><span data-stu-id="6a5bc-173">Specifies the type of the session configuration that is defined in the assembly in the **AssemblyName** parameter.</span></span> <span data-ttu-id="6a5bc-174">Den typ som du anger måste implementera klassen **system. Management. Automation. Remoting. PSSessionConfiguration** .</span><span class="sxs-lookup"><span data-stu-id="6a5bc-174">The type that you specify must implement the **System.Management.Automation.Remoting.PSSessionConfiguration** class.</span></span>

<span data-ttu-id="6a5bc-175">Den här parametern krävs när du anger ett sammansättnings namn.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-175">This parameter is required when you specify an assembly name.</span></span>

```yaml
Type: System.String
Parameter Sets: AssemblyNameParameterSet
Aliases:

Required: True
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a5bc-176">-Force</span><span class="sxs-lookup"><span data-stu-id="6a5bc-176">-Force</span></span>

<span data-ttu-id="6a5bc-177">Ignorerar alla användar meddelanden och startar om **WinRM** -tjänsten utan att fråga.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-177">Suppresses all user prompts, and restarts the **WinRM** service without prompting.</span></span> <span data-ttu-id="6a5bc-178">Att starta om tjänsten gör att konfigurations ändringen träder i kraft.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-178">Restarting the service makes the configuration change effective.</span></span>

<span data-ttu-id="6a5bc-179">Om du vill förhindra en omstart och ignorera omstarts meddelandet använder du parametern **NoServiceRestart** .</span><span class="sxs-lookup"><span data-stu-id="6a5bc-179">To prevent a restart and suppress the restart prompt, use the **NoServiceRestart** parameter.</span></span>

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

### <span data-ttu-id="6a5bc-180">-MaximumReceivedDataSizePerCommandMB</span><span class="sxs-lookup"><span data-stu-id="6a5bc-180">-MaximumReceivedDataSizePerCommandMB</span></span>

<span data-ttu-id="6a5bc-181">Anger gränsen för mängden data som kan skickas till den här datorn i ett enda fjärran slutet kommando.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-181">Specifies the limit on the amount of data that can be sent to this computer in any single remote command.</span></span> <span data-ttu-id="6a5bc-182">Ange data storleken i megabyte (MB).</span><span class="sxs-lookup"><span data-stu-id="6a5bc-182">Enter the data size in megabytes (MB).</span></span> <span data-ttu-id="6a5bc-183">Standardvärdet är 50 MB.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-183">The default is 50 MB.</span></span>

<span data-ttu-id="6a5bc-184">Om en data storleks gräns definieras i den konfigurations typ som anges i parametern **ConfigurationTypeName** används gränsen i konfigurations typen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-184">If a data size limit is defined in the configuration type that is specified in the **ConfigurationTypeName** parameter, the limit in the configuration type is used.</span></span> <span data-ttu-id="6a5bc-185">Värdet för den här parametern ignoreras.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-185">The value of this parameter is ignored.</span></span>

```yaml
Type: System.Nullable`1[System.Double]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a5bc-186">-MaximumReceivedObjectSizeMB</span><span class="sxs-lookup"><span data-stu-id="6a5bc-186">-MaximumReceivedObjectSizeMB</span></span>

<span data-ttu-id="6a5bc-187">Anger gränserna för mängden data som kan skickas till den här datorn i ett enda objekt.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-187">Specifies the limits on the amount of data that can be sent to this computer in any single object.</span></span>
<span data-ttu-id="6a5bc-188">Ange data storleken i megabyte.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-188">Enter the data size in megabytes.</span></span> <span data-ttu-id="6a5bc-189">Standardvärdet är 10 MB.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-189">The default is 10 MB.</span></span>

<span data-ttu-id="6a5bc-190">Om en gräns för objekt storlek definieras i den konfigurations typ som anges i parametern **ConfigurationTypeName** , används gränsen i konfigurations typen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-190">If an object size limit is defined in the configuration type that is specified in the **ConfigurationTypeName** parameter, the limit in the configuration type is used.</span></span> <span data-ttu-id="6a5bc-191">Värdet för den här parametern ignoreras.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-191">The value of this parameter is ignored.</span></span>

```yaml
Type: System.Nullable`1[System.Double]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a5bc-192">-ModulesToImport</span><span class="sxs-lookup"><span data-stu-id="6a5bc-192">-ModulesToImport</span></span>

<span data-ttu-id="6a5bc-193">Anger moduler och snapin-moduler som importeras automatiskt till sessioner som använder-sessionen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-193">Specifies the modules and snap-ins that are automatically imported into sessions that use the session configuration.</span></span> <span data-ttu-id="6a5bc-194">Ange modul och namn på snapin-modulen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-194">Enter the module and snap-in names.</span></span>

<span data-ttu-id="6a5bc-195">Som standard importeras bara snapin-modulen **Microsoft. PowerShell. Core** till sessioner, men om inte cmdletarna utesluts kan du använda- `Import-Module` och Add-PSSnapin-cmdletarna för att lägga till moduler och snapin-moduler till sessionen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-195">By default, only the **Microsoft.PowerShell.Core** snap-in is imported into sessions, but unless the cmdlets are excluded, you can use the `Import-Module` and Add-PSSnapin cmdlets to add modules and snap-ins to the session.</span></span>

<span data-ttu-id="6a5bc-196">Modulerna som anges i detta parameter värde importeras i tillägg till moduler som anges i konfigurations filen för sessionen ( `New-PSSessionConfigurationFile` ).</span><span class="sxs-lookup"><span data-stu-id="6a5bc-196">The modules specified in this parameter value are imported in additions to modules specified in the session configuration file (`New-PSSessionConfigurationFile`).</span></span> <span data-ttu-id="6a5bc-197">Inställningarna i konfigurations filen för sessionen kan dock dölja de kommandon som exporteras av moduler eller hindra användarna från att använda dem.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-197">However, settings in the session configuration file can hide the commands exported by modules or prevent users from using them.</span></span>

<span data-ttu-id="6a5bc-198">Modulerna som anges i detta parameter värde ersätter listan över moduler som anges genom att använda **ModulesToImport** -parametern för `Register-PSSessionConfiguration` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-198">The modules specified in this parameter value replace the list of modules specified by using the **ModulesToImport** parameter of the `Register-PSSessionConfiguration` cmdlet.</span></span>

<span data-ttu-id="6a5bc-199">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-199">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a5bc-200">-Name</span><span class="sxs-lookup"><span data-stu-id="6a5bc-200">-Name</span></span>

<span data-ttu-id="6a5bc-201">Anger namnet på den sessionsinformation som du vill ändra.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-201">Specifies the name of the session configuration that you want to change.</span></span>

<span data-ttu-id="6a5bc-202">Du kan inte använda den här parametern för att ändra namnet på konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-202">You cannot use this parameter to change the name of the session configuration.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="6a5bc-203">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="6a5bc-203">-NoServiceRestart</span></span>

<span data-ttu-id="6a5bc-204">Startar inte om **WinRM** -tjänsten och inaktiverar uppmaningen att starta om tjänsten.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-204">Does not restart the **WinRM** service, and suppresses the prompt to restart the service.</span></span>

<span data-ttu-id="6a5bc-205">När du kör `Set-PSSessionConfiguration` uppmanas du som standard att starta om **WinRM** -tjänsten för att den nya konfigurationen ska fungera.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-205">By default, when you run `Set-PSSessionConfiguration`, you are prompted to restart the **WinRM** service to make the new session configuration effective.</span></span> <span data-ttu-id="6a5bc-206">Den nya konfigurationen är inte giltig förrän **WinRM** -tjänsten har startats om.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-206">Until the **WinRM** service is restarted, the new session configuration is not effective.</span></span>

<span data-ttu-id="6a5bc-207">Om du vill starta om **WinRM** -tjänsten utan att begära det använder du parametern **Force** .</span><span class="sxs-lookup"><span data-stu-id="6a5bc-207">To restart the **WinRM** service without prompting, use the **Force** parameter.</span></span> <span data-ttu-id="6a5bc-208">Om du vill starta om **WinRM** -tjänsten manuellt använder du `Restart-Service` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-208">To restart the **WinRM** service manually, use the `Restart-Service` cmdlet.</span></span>

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

### <span data-ttu-id="6a5bc-209">-Path</span><span class="sxs-lookup"><span data-stu-id="6a5bc-209">-Path</span></span>

<span data-ttu-id="6a5bc-210">Anger sökvägen till en sessions konfigurations fil (. PSSC), till exempel en som skapats av `New-PSSessionConfigurationFile` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-210">Specifies the path of a session configuration file (.pssc), such as one created by the `New-PSSessionConfigurationFile` cmdlet.</span></span> <span data-ttu-id="6a5bc-211">Om du utelämnar sökvägen är standardvärdet den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-211">If you omit the path, the default is the current directory.</span></span>

<span data-ttu-id="6a5bc-212">Information om hur du ändrar en konfigurations fil för en session finns i hjälp avsnittet för `New-PSSessionConfigurationFile` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-212">For information about how to modify a session configuration file, see the help topic for the `New-PSSessionConfigurationFile` cmdlet.</span></span>

<span data-ttu-id="6a5bc-213">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-213">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.String
Parameter Sets: SessionConfigurationFile
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a5bc-214">– PSVersion</span><span class="sxs-lookup"><span data-stu-id="6a5bc-214">-PSVersion</span></span>

<span data-ttu-id="6a5bc-215">Anger versionen för PowerShell i sessioner som använder den här sessionen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-215">Specifies the version of PowerShell in sessions that use this session configuration.</span></span>

<span data-ttu-id="6a5bc-216">Värdet för den här parametern prioriteras över värdet för **PowerShellVersion** -nyckeln i sessionens konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-216">The value of this parameter takes precedence over the value of the **PowerShellVersion** key in the session configuration file.</span></span>

<span data-ttu-id="6a5bc-217">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-217">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Version
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases: PowerShellVersion

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a5bc-218">-RunAsCredential</span><span class="sxs-lookup"><span data-stu-id="6a5bc-218">-RunAsCredential</span></span>

<span data-ttu-id="6a5bc-219">Anger autentiseringsuppgifter för kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-219">Specifies credentials for commands in the session.</span></span> <span data-ttu-id="6a5bc-220">Som standard körs kommandona med behörigheterna för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-220">By default, commands run with the permissions of the current user.</span></span>

<span data-ttu-id="6a5bc-221">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-221">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a5bc-222">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="6a5bc-222">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="6a5bc-223">Anger en annan SDDL-sträng (Security Descriptor Definition Language) för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-223">Specifies a different Security Descriptor Definition Language (SDDL) string for the configuration.</span></span>

<span data-ttu-id="6a5bc-224">Den här strängen avgör vilka behörigheter som krävs för att använda den nya konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-224">This string determines the permissions that are required to use the new session configuration.</span></span> <span data-ttu-id="6a5bc-225">Om du vill använda en sessionshantering i en session måste användarna ha minst körnings behörighet (Invoke) för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-225">To use a session configuration in a session, users must have at least Execute(Invoke) permission for the configuration.</span></span>

<span data-ttu-id="6a5bc-226">Om du vill använda standard säkerhets beskrivningen för konfigurationen anger du en tom sträng ("") eller värdet `$Null` .</span><span class="sxs-lookup"><span data-stu-id="6a5bc-226">To use the default security descriptor for the configuration, enter an empty string ("") or a value of `$Null`.</span></span> <span data-ttu-id="6a5bc-227">Standardvärdet är rot-SDDL i filen WSMan: Drive.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-227">The default is the root SDDL in the WSMan: drive.</span></span>

<span data-ttu-id="6a5bc-228">Om säkerhets beskrivningen är komplex kan du överväga att använda parametern **ShowSecurityDescriptorUI** i stället för den här.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-228">If the security descriptor is complex, consider using the **ShowSecurityDescriptorUI** parameter instead of this one.</span></span> <span data-ttu-id="6a5bc-229">Du kan inte använda båda parametrarna i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-229">You cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="6a5bc-230">-SessionTypeOption</span><span class="sxs-lookup"><span data-stu-id="6a5bc-230">-SessionTypeOption</span></span>

<span data-ttu-id="6a5bc-231">Anger typspecifika alternativ för konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-231">Specifies type-specific options for the session configuration.</span></span> <span data-ttu-id="6a5bc-232">Ange ett alternativ för sessionsläge, till exempel **PSWorkflowExecutionOption** -objektet som `New-PSWorkflowExecutionOption` cmdleten returnerar.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-232">Enter a session type options object, such as the **PSWorkflowExecutionOption** object that the `New-PSWorkflowExecutionOption` cmdlet returns.</span></span>

<span data-ttu-id="6a5bc-233">Alternativen för sessioner som använder sessionen bestäms av värdena för session-alternativen och konfigurations alternativen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-233">The options of sessions that use the session configuration are determined by the values of session options and the session configuration options.</span></span> <span data-ttu-id="6a5bc-234">Om inget annat anges får alternativ som anges i sessionen, till exempel med hjälp av `New-PSSessionOption` cmdleten, företräde framför alternativ som angetts i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-234">Unless specified, options set in the session, such as by using the `New-PSSessionOption` cmdlet, take precedence over options set in the session configuration.</span></span> <span data-ttu-id="6a5bc-235">Värdena för sessionens alternativ får dock inte överskrida de maximala värden som angetts i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-235">However, session option values cannot exceed maximum values set in the session configuration.</span></span>

<span data-ttu-id="6a5bc-236">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-236">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSSessionTypeOption
Parameter Sets: NameParameterSet, AssemblyNameParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a5bc-237">-ShowSecurityDescriptorUI</span><span class="sxs-lookup"><span data-stu-id="6a5bc-237">-ShowSecurityDescriptorUI</span></span>

<span data-ttu-id="6a5bc-238">Anger att denna cmdlet är en egenskaps sida som hjälper dig att skapa en ny SDDL för konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-238">Indicates that this cmdlet a property sheet that helps you create a new SDDL for the session configuration.</span></span> <span data-ttu-id="6a5bc-239">Egenskaps sidan visas när du har kört `Set-PSSessionConfiguration` kommandot och startat om **WinRM** -tjänsten.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-239">The property sheet appears after you run the `Set-PSSessionConfiguration` command and then restart the **WinRM** service.</span></span>

<span data-ttu-id="6a5bc-240">Kom ihåg att användarna måste ha minst körnings behörighet för att kunna använda sessionen i en session när du anger behörigheter för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-240">When you set permissions to the configuration, remember that users must have at least Execute(Invoke) permission to use the session configuration in a session.</span></span>

<span data-ttu-id="6a5bc-241">Du kan inte använda parametern **SecurityDescriptorSDDL** och den här parametern i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-241">You cannot use the **SecurityDescriptorSDDL** parameter and this parameter in the same command.</span></span>

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

### <span data-ttu-id="6a5bc-242">-StartupScript</span><span class="sxs-lookup"><span data-stu-id="6a5bc-242">-StartupScript</span></span>

<span data-ttu-id="6a5bc-243">Anger start skriptet för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-243">Specifies the startup script for the configuration.</span></span> <span data-ttu-id="6a5bc-244">Ange den fullständigt kvalificerade sökvägen till ett PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-244">Enter the fully qualified path of a PowerShell script.</span></span> <span data-ttu-id="6a5bc-245">Det angivna skriptet körs i den nya sessionen som använder konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-245">The specified script runs in the new session that uses the session configuration.</span></span>

<span data-ttu-id="6a5bc-246">Om du vill ta bort ett start skript från en sessions konfiguration anger du en tom sträng ("") eller värdet `$Null` .</span><span class="sxs-lookup"><span data-stu-id="6a5bc-246">To delete a startup script from a session configuration, enter an empty string ("") or a value of `$Null`.</span></span>

<span data-ttu-id="6a5bc-247">Du kan använda ett start skript för att ytterligare konfigurera användarsessionen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-247">You can use a startup script to further configure the user session.</span></span> <span data-ttu-id="6a5bc-248">Om skriptet genererar ett fel, till och med ett icke-avslutande fel, skapas inte sessionen och `New-PSSession` kommandot Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-248">If the script generates an error, even a non-terminating error, the session is not created and the `New-PSSession` command fails.</span></span>

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

### <span data-ttu-id="6a5bc-249">-ThreadOptions</span><span class="sxs-lookup"><span data-stu-id="6a5bc-249">-ThreadOptions</span></span>

<span data-ttu-id="6a5bc-250">Anger inställningen för tråd alternativ i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-250">Specifies the thread options setting in the configuration.</span></span> <span data-ttu-id="6a5bc-251">Den här inställningen definierar hur trådar skapas och används när ett kommando körs i sessionen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-251">This setting defines how threads are created and used when a command is executed in the session.</span></span> <span data-ttu-id="6a5bc-252">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="6a5bc-252">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="6a5bc-253">Standard</span><span class="sxs-lookup"><span data-stu-id="6a5bc-253">Default</span></span>
- <span data-ttu-id="6a5bc-254">ReuseThread</span><span class="sxs-lookup"><span data-stu-id="6a5bc-254">ReuseThread</span></span>
- <span data-ttu-id="6a5bc-255">UseCurrentThread</span><span class="sxs-lookup"><span data-stu-id="6a5bc-255">UseCurrentThread</span></span>
- <span data-ttu-id="6a5bc-256">UseNewThread</span><span class="sxs-lookup"><span data-stu-id="6a5bc-256">UseNewThread</span></span>

<span data-ttu-id="6a5bc-257">Standardvärdet är **UseCurrentThread**.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-257">The default value is **UseCurrentThread**.</span></span>

<span data-ttu-id="6a5bc-258">Mer information finns i [PSThreadOptions-uppräkning](/dotnet/api/system.management.automation.runspaces.psthreadoptions).</span><span class="sxs-lookup"><span data-stu-id="6a5bc-258">For more information, see [PSThreadOptions Enumeration](/dotnet/api/system.management.automation.runspaces.psthreadoptions).</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSThreadOptions
Parameter Sets: (All)
Aliases:
Accepted values: Default, UseNewThread, ReuseThread, UseCurrentThread

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a5bc-259">-TransportOption</span><span class="sxs-lookup"><span data-stu-id="6a5bc-259">-TransportOption</span></span>

<span data-ttu-id="6a5bc-260">Anger transport alternativ för konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-260">Specifies the transport options for the session configuration.</span></span> <span data-ttu-id="6a5bc-261">Ange ett transport alternativ objekt, till exempel **WSManConfigurationOption** -objektet som `New-PSTransportOption` cmdleten returnerar.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-261">Enter a transport options object, such as the **WSManConfigurationOption** object that the `New-PSTransportOption` cmdlet returns.</span></span>

<span data-ttu-id="6a5bc-262">Alternativen för sessioner som använder sessionen bestäms av värdena för session-alternativen och konfigurations alternativen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-262">The options of sessions that use the session configuration are determined by the values of session options and the session configuration options.</span></span> <span data-ttu-id="6a5bc-263">Om inget annat anges får alternativ som anges i sessionen, till exempel med hjälp av `New-PSSessionOption` cmdleten, företräde framför alternativ som angetts i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-263">Unless specified, options set in the session, such as by using the `New-PSSessionOption` cmdlet, take precedence over options set in the session configuration.</span></span> <span data-ttu-id="6a5bc-264">Värdena för sessionens alternativ får dock inte överskrida de maximala värden som angetts i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-264">However, session option values cannot exceed maximum values set in the session configuration.</span></span>

<span data-ttu-id="6a5bc-265">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-265">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.PSTransportOption
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a5bc-266">-UseSharedProcess</span><span class="sxs-lookup"><span data-stu-id="6a5bc-266">-UseSharedProcess</span></span>

<span data-ttu-id="6a5bc-267">Använd bara en process som värd för alla sessioner som startas av samma användare och Använd samma sessions konfiguration.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-267">Use only one process to host all sessions that are started by the same user and use the same session configuration.</span></span> <span data-ttu-id="6a5bc-268">Som standard finns varje session i en egen process.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-268">By default, each session is hosted in its own process.</span></span>

<span data-ttu-id="6a5bc-269">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-269">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="6a5bc-270">-Confirm</span><span class="sxs-lookup"><span data-stu-id="6a5bc-270">-Confirm</span></span>

<span data-ttu-id="6a5bc-271">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-271">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a5bc-272">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="6a5bc-272">-WhatIf</span></span>

<span data-ttu-id="6a5bc-273">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-273">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="6a5bc-274">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-274">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a5bc-275">-ThreadApartmentState</span><span class="sxs-lookup"><span data-stu-id="6a5bc-275">-ThreadApartmentState</span></span>

<span data-ttu-id="6a5bc-276">Anger Apartment-statusen för den trådad modul som ska användas.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-276">Specifies the apartment state of the threading module to be used.</span></span> <span data-ttu-id="6a5bc-277">Godkända värden är:</span><span class="sxs-lookup"><span data-stu-id="6a5bc-277">Acceptable values are:</span></span>

- <span data-ttu-id="6a5bc-278">Okänt</span><span class="sxs-lookup"><span data-stu-id="6a5bc-278">Unknown</span></span>
- <span data-ttu-id="6a5bc-279">MTA</span><span class="sxs-lookup"><span data-stu-id="6a5bc-279">MTA</span></span>
- <span data-ttu-id="6a5bc-280">S</span><span class="sxs-lookup"><span data-stu-id="6a5bc-280">STA</span></span>

```yaml
Type: System.Threading.ApartmentState
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a5bc-281">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6a5bc-281">CommonParameters</span></span>

<span data-ttu-id="6a5bc-282">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-282">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6a5bc-283">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="6a5bc-283">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6a5bc-284">INDATA</span><span class="sxs-lookup"><span data-stu-id="6a5bc-284">INPUTS</span></span>

### <span data-ttu-id="6a5bc-285">Inget</span><span class="sxs-lookup"><span data-stu-id="6a5bc-285">None</span></span>

<span data-ttu-id="6a5bc-286">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-286">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="6a5bc-287">UTDATA</span><span class="sxs-lookup"><span data-stu-id="6a5bc-287">OUTPUTS</span></span>

### <span data-ttu-id="6a5bc-288">Microsoft. WSMan. Management. WSManConfigLeafElement</span><span class="sxs-lookup"><span data-stu-id="6a5bc-288">Microsoft.WSMan.Management.WSManConfigLeafElement</span></span>

## <span data-ttu-id="6a5bc-289">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="6a5bc-289">NOTES</span></span>

<span data-ttu-id="6a5bc-290">Den här cmdleten är endast tillgänglig på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-290">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="6a5bc-291">Starta PowerShell med alternativet Kör som administratör för att köra denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-291">To run this cmdlet, start PowerShell by using the Run as administrator option.</span></span>

<span data-ttu-id="6a5bc-292">`Set-PSSessionConfiguration`Cmdleten ändrar inte konfigurations namnet och **WSMan** -providern stöder inte `Rename-Item` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-292">The `Set-PSSessionConfiguration` cmdlet does not change the configuration name and the **WSMan** provider does not support the `Rename-Item` cmdlet.</span></span> <span data-ttu-id="6a5bc-293">Om du vill ändra namnet på en sessions konfiguration använder du `Unregister-PSSessionConfiguration` cmdleten för att ta bort konfigurationen och använder sedan `Register-PSSessionConfiguration` cmdleten för att skapa och registrera en ny konfiguration av sessionen.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-293">To change the name of a session configuration, use the `Unregister-PSSessionConfiguration` cmdlet to delete the configuration and then use the `Register-PSSessionConfiguration` cmdlet to create and register a new session configuration.</span></span>

<span data-ttu-id="6a5bc-294">Du kan använda `Set-PSSessionConfiguration` cmdleten för att ändra standard konfigurationerna för Microsoft. PowerShell och Microsoft. PowerShell32.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-294">You can use the `Set-PSSessionConfiguration` cmdlet to change the default Microsoft.PowerShell and Microsoft.PowerShell32 session configurations.</span></span> <span data-ttu-id="6a5bc-295">De är inte skyddade.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-295">They are not protected.</span></span> <span data-ttu-id="6a5bc-296">Om du vill återgå till den ursprungliga versionen av en standardsession, använder du `Unregister-PSSessionConfiguration` cmdleten för att ta bort standardsessionens konfiguration och använder sedan `Enable-PSRemoting` cmdlet: en för att återställa den.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-296">To revert to the original version of a default session configuration, use the `Unregister-PSSessionConfiguration` cmdlet to delete the default session configuration and then use the `Enable-PSRemoting` cmdlet to restore it.</span></span>

<span data-ttu-id="6a5bc-297">Egenskaperna för ett konfigurations objekt för en session varierar beroende på vilka alternativ som har angetts för konfigurationen av sessionen och värdena för dessa alternativ.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-297">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="6a5bc-298">Dessutom har sessionsinställningar som använder en konfigurations fil för sessionen ytterligare egenskaper.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-298">Also, session configurations that use a session configuration file have additional properties.</span></span>

<span data-ttu-id="6a5bc-299">Du kan använda kommandona i WSMan: Drive för att ändra egenskaperna för sessionens konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-299">You can use commands in the WSMan: drive to change the properties of session configurations.</span></span>
<span data-ttu-id="6a5bc-300">Du kan dock inte använda WSMan:-enheten i PowerShell 2,0 för att ändra konfigurations egenskaper för sessionen som introduceras i PowerShell 3,0, till exempel **OutputBufferingMode**.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-300">However, you cannot use the WSMan: drive in PowerShell 2.0 to change session configuration properties that are introduced in PowerShell 3.0, such as **OutputBufferingMode**.</span></span> <span data-ttu-id="6a5bc-301">Windows PowerShell 2,0-kommandon genererar inte ett fel, men de är inaktiva.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-301">Windows PowerShell 2.0 commands do not generate an error, but they are ineffective.</span></span> <span data-ttu-id="6a5bc-302">Om du vill ändra de egenskaper som introduceras i PowerShell 3,0 använder du kommandot WSMan: Drive i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6a5bc-302">To change properties introduced in PowerShell 3.0, use the WSMan: drive in PowerShell 3.0.</span></span>

## <span data-ttu-id="6a5bc-303">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="6a5bc-303">RELATED LINKS</span></span>

[<span data-ttu-id="6a5bc-304">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="6a5bc-304">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="6a5bc-305">Aktivera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="6a5bc-305">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="6a5bc-306">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="6a5bc-306">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="6a5bc-307">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="6a5bc-307">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="6a5bc-308">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="6a5bc-308">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="6a5bc-309">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="6a5bc-309">New-PSTransportOption</span></span>](New-PSTransportOption.md)

[<span data-ttu-id="6a5bc-310">Registrera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="6a5bc-310">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="6a5bc-311">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="6a5bc-311">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="6a5bc-312">Avregistrera-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="6a5bc-312">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="6a5bc-313">WSMan-Provider</span><span class="sxs-lookup"><span data-stu-id="6a5bc-313">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="6a5bc-314">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="6a5bc-314">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="6a5bc-315">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="6a5bc-315">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
