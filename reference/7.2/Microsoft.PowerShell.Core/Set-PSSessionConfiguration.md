---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-pssessionconfiguration?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSSessionConfiguration
ms.openlocfilehash: c3c3c0bbb0436ef2e6857adc35f83e627d03f4b9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709132"
---
# <span data-ttu-id="a3a73-102">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a3a73-102">Set-PSSessionConfiguration</span></span>

## <span data-ttu-id="a3a73-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="a3a73-103">SYNOPSIS</span></span>
<span data-ttu-id="a3a73-104">Ändrar egenskaperna för en registrerad session-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a3a73-104">Changes the properties of a registered session configuration.</span></span>

## <span data-ttu-id="a3a73-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a3a73-105">SYNTAX</span></span>

### <span data-ttu-id="a3a73-106">NameParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="a3a73-106">NameParameterSet (Default)</span></span>

```
Set-PSSessionConfiguration [-Name] <String> [-ApplicationBase <String>] [-RunAsCredential <PSCredential>]
 [-ThreadOptions <PSThreadOptions>] [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess]
 [-StartupScript <String>] [-MaximumReceivedDataSizePerCommandMB <Double>]
 [-MaximumReceivedObjectSizeMB <Double>] [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI]
 [-Force] [-NoServiceRestart] [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>]
 [-TransportOption <PSTransportOption>] [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a3a73-107">AssemblyNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="a3a73-107">AssemblyNameParameterSet</span></span>

```
Set-PSSessionConfiguration [-Name] <String> [-AssemblyName] <String> [-ApplicationBase <String>]
 [-ConfigurationTypeName] <String> [-RunAsCredential <PSCredential>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>] [-TransportOption <PSTransportOption>]
 [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="a3a73-108">SessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="a3a73-108">SessionConfigurationFile</span></span>

```
Set-PSSessionConfiguration [-Name] <String> [-RunAsCredential <PSCredential>]
 [-ThreadOptions <PSThreadOptions>] [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess]
 [-StartupScript <String>] [-MaximumReceivedDataSizePerCommandMB <Double>]
 [-MaximumReceivedObjectSizeMB <Double>] [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI]
 [-Force] [-NoServiceRestart] [-TransportOption <PSTransportOption>] -Path <String> [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="a3a73-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a3a73-109">DESCRIPTION</span></span>

<span data-ttu-id="a3a73-110">`Set-PSSessionConfiguration`Cmdleten ändrar egenskaperna för sessionens konfigurationer på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="a3a73-110">The `Set-PSSessionConfiguration` cmdlet changes the properties of the session configurations on the local computer.</span></span>

<span data-ttu-id="a3a73-111">Använd parametern **Name** för att identifiera den konfiguration av sessionen som du vill ändra.</span><span class="sxs-lookup"><span data-stu-id="a3a73-111">Use the **Name** parameter to identify the session configuration that you want to change.</span></span> <span data-ttu-id="a3a73-112">Använd de andra parametrarna för att ange nya värden för egenskaperna för sessionen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-112">Use the other parameters to specify new values for the properties of the session configuration.</span></span> <span data-ttu-id="a3a73-113">Om du vill ta bort ett egenskaps värde från konfigurationen och använda standardvärdet anger du en tom sträng ("") eller värdet `$Null` för motsvarande parameter.</span><span class="sxs-lookup"><span data-stu-id="a3a73-113">To delete a property value from the configuration, and use the default value, enter an empty string ("") or a value of `$Null` for the corresponding parameter.</span></span>

<span data-ttu-id="a3a73-114">Från och med PowerShell 3,0 kan du använda en konfigurations fil för sessionen för att definiera en sessions-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a3a73-114">Starting in PowerShell 3.0, you can use a session configuration file to define a session configuration.</span></span> <span data-ttu-id="a3a73-115">Den här funktionen ger en enkel och identifierad metod för att ange och ändra egenskaperna för sessioner som använder sessionen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-115">This feature provides a simple and discoverable method for setting and changing the properties of sessions that use the session configuration.</span></span> <span data-ttu-id="a3a73-116">Om du vill ange en konfigurations fil för sessionen använder du parametern **Path** i `Set-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="a3a73-116">To specify a session configuration file, use the **Path** parameter of `Set-PSSessionConfiguration`.</span></span> <span data-ttu-id="a3a73-117">Information om konfigurationsfiler för sessioner finns [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span><span class="sxs-lookup"><span data-stu-id="a3a73-117">For information about session configuration files, see [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>
<span data-ttu-id="a3a73-118">Information om hur du skapar och ändrar en konfigurations fil för en session finns i `New-PSSessionConfigurationFile` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a3a73-118">For information about how to create and modify a session configuration file, see the `New-PSSessionConfigurationFile` cmdlet.</span></span>

<span data-ttu-id="a3a73-119">Sessionsbaserade definierar miljön för fjärrsessioner (**PSSessions**) som ansluter till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="a3a73-119">Session configurations define the environment of remote sessions (**PSSessions**) that connect to the local computer.</span></span> <span data-ttu-id="a3a73-120">Varje **PSSession** använder en konfiguration av sessionen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-120">Every **PSSession** uses a session configuration.</span></span> <span data-ttu-id="a3a73-121">Konfigurationen av sessionen bestämmer funktionerna i **PSSession**, till exempel de moduler som är tillgängliga i sessionen, vilka cmdlets som tillåts köras, språk läge, kvoter och tids gränser.</span><span class="sxs-lookup"><span data-stu-id="a3a73-121">The session configuration determines the features of the **PSSession**, such as the modules that are available in the session, the cmdlets that are permitted to run, the language mode, quotas, and timeouts.</span></span> <span data-ttu-id="a3a73-122">Säkerhets beskrivningen för konfigurationen av sessionen avgör vem som kan använda sessionen för att ansluta till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="a3a73-122">The security descriptor of the session configuration determines who can use the session configuration to connect to the local computer.</span></span> <span data-ttu-id="a3a73-123">För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="a3a73-123">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

<span data-ttu-id="a3a73-124">Använd `Get-PSSessionConfiguration` cmdleten eller WSMan-providern för att se egenskaperna för en sessions konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a3a73-124">To see the properties of a session configuration, use the `Get-PSSessionConfiguration` cmdlet or the WSMan Provider.</span></span> <span data-ttu-id="a3a73-125">Om du vill ha mer information om WSMan-providern skriver du `Get-Help WSMan` .</span><span class="sxs-lookup"><span data-stu-id="a3a73-125">For more information about the WSMan Provider, type `Get-Help WSMan`.</span></span>

## <span data-ttu-id="a3a73-126">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="a3a73-126">EXAMPLES</span></span>

### <span data-ttu-id="a3a73-127">Exempel 1: skapa och ändra en konfiguration av sessionen</span><span class="sxs-lookup"><span data-stu-id="a3a73-127">Example 1: Create and change a session configuration</span></span>

<span data-ttu-id="a3a73-128">Det här exemplet visar hur du lägger till och tar bort ett start skript från en konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a3a73-128">This example shows how to add and remove a startup script from a configuration.</span></span>

<span data-ttu-id="a3a73-129">Det första kommandot skapar **AdminShell** -konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-129">The first command creates the **AdminShell** configuration.</span></span> <span data-ttu-id="a3a73-130">Det andra kommandot lägger till `AdminConfig.ps1` skriptet i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-130">The second command adds the `AdminConfig.ps1` script to the configuration.</span></span> <span data-ttu-id="a3a73-131">Ändringen gäller när du startar om **WinRM**.</span><span class="sxs-lookup"><span data-stu-id="a3a73-131">The change is effective when you restart **WinRM**.</span></span>
<span data-ttu-id="a3a73-132">Det tredje kommandot tar bort `AdminConfig.ps1` skriptet från konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-132">The third command removes the `AdminConfig.ps1` script from the configuration.</span></span>

```powershell
Register-PSSessionConfiguration -Name "AdminShell" -AssemblyName "C:\Shells\AdminShell.dll" -ConfigurationTypeName "AdminClass"
Set-PSSessionConfiguration -Name "AdminShell" -StartupScript "AdminConfig.ps1"
Set-PSSessionConfiguration -Name "AdminShell" -StartupScript $Null
```

### <span data-ttu-id="a3a73-133">Exempel 2: Visa resultat</span><span class="sxs-lookup"><span data-stu-id="a3a73-133">Example 2: Display results</span></span>

<span data-ttu-id="a3a73-134">Det här exemplet ökar värdet för egenskapen **MaximumReceivedObjectSizeMB** till 20.</span><span class="sxs-lookup"><span data-stu-id="a3a73-134">This example increases the value of the **MaximumReceivedObjectSizeMB** property to 20.</span></span> <span data-ttu-id="a3a73-135">Det här kommandot kräver också att du startar om **WinRM** -tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a3a73-135">This command also prompts you to restart the **WinRM** service.</span></span> <span data-ttu-id="a3a73-136">Ändringen gäller inte förrän **WinRM** -tjänsten har startats om.</span><span class="sxs-lookup"><span data-stu-id="a3a73-136">The change is not effective until the **WinRM** service is restarted.</span></span>

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

### <span data-ttu-id="a3a73-137">Exempel 3: Visa resultat på olika sätt</span><span class="sxs-lookup"><span data-stu-id="a3a73-137">Example 3: Display results in different ways</span></span>

<span data-ttu-id="a3a73-138">I det här exemplet `Set-PSSessionConfiguration` ändrar Start skriptet i **MaintenanceShell** -sessionen till `Maintenance.ps1` .</span><span class="sxs-lookup"><span data-stu-id="a3a73-138">In this example, `Set-PSSessionConfiguration` changes the startup script in the **MaintenanceShell** session configuration to `Maintenance.ps1`.</span></span> <span data-ttu-id="a3a73-139">Resultatet visar ändringen och du ombeds att starta om **WinRM** -tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a3a73-139">The output shows the change and prompts you to restart the **WinRM** service.</span></span> <span data-ttu-id="a3a73-140">Svaret är "y" (Ja).</span><span class="sxs-lookup"><span data-stu-id="a3a73-140">The response is "y" (yes).</span></span>

<span data-ttu-id="a3a73-141">`Get-PSSessionConfiguration` hämtar konfigurationen för **MaintenanceShell** -sessionen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-141">`Get-PSSessionConfiguration` gets the **MaintenanceShell** session configuration.</span></span> <span data-ttu-id="a3a73-142">Pipeline-operatorn (|) skickar resultatet från kommandot till `Format-List` , som visar alla egenskaper för konfigurationsobjektet i en lista.</span><span class="sxs-lookup"><span data-stu-id="a3a73-142">The pipeline operator (|) sends the results of the command to `Format-List`, which displays all the properties of the configuration object in a list.</span></span> <span data-ttu-id="a3a73-143">Därefter visar vi initierings parametrarna för **MaintenanceShell** -konfigurationen med hjälp av WSMan-providern.</span><span class="sxs-lookup"><span data-stu-id="a3a73-143">Next, using the WSMan provider, we view the initialization parameters for the **MaintenanceShell** configuration.</span></span> <span data-ttu-id="a3a73-144">`Get-ChildItem` (alias `dir` ) hämtar de underordnade objekten i **InitializationParameters** -noden för **MaintenanceShell** -plugin-programmet.</span><span class="sxs-lookup"><span data-stu-id="a3a73-144">`Get-ChildItem` (alias `dir`) gets the child items in the **InitializationParameters** node for the **MaintenanceShell** plug-in.</span></span> <span data-ttu-id="a3a73-145">Om du vill ha mer information om WSMan-providern skriver du `Get-Help wsman` .</span><span class="sxs-lookup"><span data-stu-id="a3a73-145">For more information about the WSMan provider, type `Get-Help wsman`.</span></span>

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

## <span data-ttu-id="a3a73-146">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="a3a73-146">PARAMETERS</span></span>

### <span data-ttu-id="a3a73-147">-AccessMode</span><span class="sxs-lookup"><span data-stu-id="a3a73-147">-AccessMode</span></span>

<span data-ttu-id="a3a73-148">Aktiverar och inaktiverar konfigurationen av sessionen och avgör om den kan användas för fjärranslutna eller lokala sessioner på datorn.</span><span class="sxs-lookup"><span data-stu-id="a3a73-148">Enables and disables the session configuration and determines whether it can be used for remote or local sessions on the computer.</span></span> <span data-ttu-id="a3a73-149">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="a3a73-149">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="a3a73-150">Inaktiverat</span><span class="sxs-lookup"><span data-stu-id="a3a73-150">Disabled.</span></span> <span data-ttu-id="a3a73-151">Inaktiverar konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-151">Disables the session configuration.</span></span> <span data-ttu-id="a3a73-152">Den kan inte användas för fjärran sluten eller lokal åtkomst till datorn.</span><span class="sxs-lookup"><span data-stu-id="a3a73-152">It cannot be used for remote or local access to the computer.</span></span> <span data-ttu-id="a3a73-153">Det här värdet anger egenskapen **Enabled** för session-konfigurationen ( `WSMan:\<ComputerName>\PlugIn\<SessionConfigurationName>\Enabled` ) till **false**.</span><span class="sxs-lookup"><span data-stu-id="a3a73-153">This value sets the **Enabled** property of the session configuration (`WSMan:\<ComputerName>\PlugIn\<SessionConfigurationName>\Enabled`) to **False**.</span></span>
- <span data-ttu-id="a3a73-154">Inställningar.</span><span class="sxs-lookup"><span data-stu-id="a3a73-154">Local.</span></span> <span data-ttu-id="a3a73-155">Lägger till en **Network_Deny_All** post i säkerhets beskrivningen för konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-155">Adds a **Network_Deny_All** entry to security descriptor of the session configuration.</span></span>
  <span data-ttu-id="a3a73-156">Användare av den lokala datorn kan använda sessionen för att skapa en lokal loopback-session på samma dator, men fjärran vändare nekas åtkomst.</span><span class="sxs-lookup"><span data-stu-id="a3a73-156">Users of the local computer can use the session configuration to create a local loopback session on the same computer, but remote users are denied access.</span></span>
- <span data-ttu-id="a3a73-157">Fjärrserveradministrationsverktyg.</span><span class="sxs-lookup"><span data-stu-id="a3a73-157">Remote.</span></span> <span data-ttu-id="a3a73-158">Tar bort **Deny_All** och **Network_Deny_All** poster från säkerhets beskrivarna i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-158">Removes **Deny_All** and **Network_Deny_All** entries from the security descriptors of the session configuration.</span></span> <span data-ttu-id="a3a73-159">Användare av lokala och fjärranslutna datorer kan använda sessionen för att skapa sessioner och köra kommandon på den här datorn.</span><span class="sxs-lookup"><span data-stu-id="a3a73-159">Users of local and remote computers can use the session configuration to create sessions and run commands on this computer.</span></span>

<span data-ttu-id="a3a73-160">Standardvärdet är **fjärran sluten**.</span><span class="sxs-lookup"><span data-stu-id="a3a73-160">The default value is **Remote**.</span></span>

<span data-ttu-id="a3a73-161">Andra cmdletar kan åsidosätta värdet för den här parametern senare.</span><span class="sxs-lookup"><span data-stu-id="a3a73-161">Other cmdlets can override the value of this parameter later.</span></span> <span data-ttu-id="a3a73-162">Till exempel `Enable-PSRemoting` möjliggör cmdleten alla sessionsbaserade på datorn och tillåter fjärråtkomst till dem, och `Disable-PSRemoting` cmdleten tillåter endast lokal åtkomst till alla sessionsinställningar på datorn.</span><span class="sxs-lookup"><span data-stu-id="a3a73-162">For example, the `Enable-PSRemoting` cmdlet enables all session configurations on the computer and permits remote access to them, and the `Disable-PSRemoting` cmdlet permits only local access to all session configurations on the computer.</span></span>

<span data-ttu-id="a3a73-163">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a3a73-163">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="a3a73-164">– ApplicationBase</span><span class="sxs-lookup"><span data-stu-id="a3a73-164">-ApplicationBase</span></span>

<span data-ttu-id="a3a73-165">Anger sökvägen till sammansättnings filen ( \* . dll) som anges i värdet för parametern **AssemblyName** .</span><span class="sxs-lookup"><span data-stu-id="a3a73-165">Specifies the path of the assembly file (\*.dll) that is specified in the value of the **AssemblyName** parameter.</span></span>

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

### <span data-ttu-id="a3a73-166">-AssemblyName</span><span class="sxs-lookup"><span data-stu-id="a3a73-166">-AssemblyName</span></span>

<span data-ttu-id="a3a73-167">Anger sammansättnings namnet.</span><span class="sxs-lookup"><span data-stu-id="a3a73-167">Specifies the assembly name.</span></span> <span data-ttu-id="a3a73-168">Denna cmdlet skapar en sessionsnyckel som baseras på en klass som har definierats i en sammansättning.</span><span class="sxs-lookup"><span data-stu-id="a3a73-168">This cmdlet creates a session configuration based on a class that is defined in an assembly.</span></span>

<span data-ttu-id="a3a73-169">Ange fil namnet eller den fullständiga sökvägen till en Assembly. dll-fil som definierar en-sessions konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a3a73-169">Enter the filename or full path of an assembly .dll file that defines a session configuration.</span></span> <span data-ttu-id="a3a73-170">Om du bara anger fil namnet kan du ange sökvägen i värdet för parametern **ApplicationBase** .</span><span class="sxs-lookup"><span data-stu-id="a3a73-170">If you enter only the file name, you can enter the path in the value of the **ApplicationBase** parameter.</span></span>

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

### <span data-ttu-id="a3a73-171">-ConfigurationTypeName</span><span class="sxs-lookup"><span data-stu-id="a3a73-171">-ConfigurationTypeName</span></span>

<span data-ttu-id="a3a73-172">Anger typen av sessionsinformation som definieras i sammansättningen i parametern **AssemblyName** .</span><span class="sxs-lookup"><span data-stu-id="a3a73-172">Specifies the type of the session configuration that is defined in the assembly in the **AssemblyName** parameter.</span></span> <span data-ttu-id="a3a73-173">Den typ som du anger måste implementera klassen **system. Management. Automation. Remoting. PSSessionConfiguration** .</span><span class="sxs-lookup"><span data-stu-id="a3a73-173">The type that you specify must implement the **System.Management.Automation.Remoting.PSSessionConfiguration** class.</span></span>

<span data-ttu-id="a3a73-174">Den här parametern krävs när du anger ett sammansättnings namn.</span><span class="sxs-lookup"><span data-stu-id="a3a73-174">This parameter is required when you specify an assembly name.</span></span>

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

### <span data-ttu-id="a3a73-175">-Force</span><span class="sxs-lookup"><span data-stu-id="a3a73-175">-Force</span></span>

<span data-ttu-id="a3a73-176">Ignorerar alla användar meddelanden och startar om **WinRM** -tjänsten utan att fråga.</span><span class="sxs-lookup"><span data-stu-id="a3a73-176">Suppresses all user prompts, and restarts the **WinRM** service without prompting.</span></span> <span data-ttu-id="a3a73-177">Att starta om tjänsten gör att konfigurations ändringen träder i kraft.</span><span class="sxs-lookup"><span data-stu-id="a3a73-177">Restarting the service makes the configuration change effective.</span></span>

<span data-ttu-id="a3a73-178">Om du vill förhindra en omstart och ignorera omstarts meddelandet använder du parametern **NoServiceRestart** .</span><span class="sxs-lookup"><span data-stu-id="a3a73-178">To prevent a restart and suppress the restart prompt, use the **NoServiceRestart** parameter.</span></span>

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

### <span data-ttu-id="a3a73-179">-MaximumReceivedDataSizePerCommandMB</span><span class="sxs-lookup"><span data-stu-id="a3a73-179">-MaximumReceivedDataSizePerCommandMB</span></span>

<span data-ttu-id="a3a73-180">Anger gränsen för mängden data som kan skickas till den här datorn i ett enda fjärran slutet kommando.</span><span class="sxs-lookup"><span data-stu-id="a3a73-180">Specifies the limit on the amount of data that can be sent to this computer in any single remote command.</span></span> <span data-ttu-id="a3a73-181">Ange data storleken i megabyte (MB).</span><span class="sxs-lookup"><span data-stu-id="a3a73-181">Enter the data size in megabytes (MB).</span></span> <span data-ttu-id="a3a73-182">Standardvärdet är 50 MB.</span><span class="sxs-lookup"><span data-stu-id="a3a73-182">The default is 50 MB.</span></span>

<span data-ttu-id="a3a73-183">Om en data storleks gräns definieras i den konfigurations typ som anges i parametern **ConfigurationTypeName** används gränsen i konfigurations typen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-183">If a data size limit is defined in the configuration type that is specified in the **ConfigurationTypeName** parameter, the limit in the configuration type is used.</span></span> <span data-ttu-id="a3a73-184">Värdet för den här parametern ignoreras.</span><span class="sxs-lookup"><span data-stu-id="a3a73-184">The value of this parameter is ignored.</span></span>

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

### <span data-ttu-id="a3a73-185">-MaximumReceivedObjectSizeMB</span><span class="sxs-lookup"><span data-stu-id="a3a73-185">-MaximumReceivedObjectSizeMB</span></span>

<span data-ttu-id="a3a73-186">Anger gränserna för mängden data som kan skickas till den här datorn i ett enda objekt.</span><span class="sxs-lookup"><span data-stu-id="a3a73-186">Specifies the limits on the amount of data that can be sent to this computer in any single object.</span></span>
<span data-ttu-id="a3a73-187">Ange data storleken i megabyte.</span><span class="sxs-lookup"><span data-stu-id="a3a73-187">Enter the data size in megabytes.</span></span> <span data-ttu-id="a3a73-188">Standardvärdet är 10 MB.</span><span class="sxs-lookup"><span data-stu-id="a3a73-188">The default is 10 MB.</span></span>

<span data-ttu-id="a3a73-189">Om en gräns för objekt storlek definieras i den konfigurations typ som anges i parametern **ConfigurationTypeName** , används gränsen i konfigurations typen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-189">If an object size limit is defined in the configuration type that is specified in the **ConfigurationTypeName** parameter, the limit in the configuration type is used.</span></span> <span data-ttu-id="a3a73-190">Värdet för den här parametern ignoreras.</span><span class="sxs-lookup"><span data-stu-id="a3a73-190">The value of this parameter is ignored.</span></span>

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

### <span data-ttu-id="a3a73-191">-ModulesToImport</span><span class="sxs-lookup"><span data-stu-id="a3a73-191">-ModulesToImport</span></span>

<span data-ttu-id="a3a73-192">Anger moduler och snapin-moduler som importeras automatiskt till sessioner som använder-sessionen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-192">Specifies the modules and snap-ins that are automatically imported into sessions that use the session configuration.</span></span> <span data-ttu-id="a3a73-193">Ange modul och namn på snapin-modulen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-193">Enter the module and snap-in names.</span></span>

<span data-ttu-id="a3a73-194">Som standard importeras bara snapin-modulen **Microsoft. PowerShell. Core** till sessioner, men om inte cmdletarna utesluts kan du använda- `Import-Module` och Add-PSSnapin-cmdletarna för att lägga till moduler och snapin-moduler till sessionen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-194">By default, only the **Microsoft.PowerShell.Core** snap-in is imported into sessions, but unless the cmdlets are excluded, you can use the `Import-Module` and Add-PSSnapin cmdlets to add modules and snap-ins to the session.</span></span>

<span data-ttu-id="a3a73-195">Modulerna som anges i detta parameter värde importeras i tillägg till moduler som anges i konfigurations filen för sessionen ( `New-PSSessionConfigurationFile` ).</span><span class="sxs-lookup"><span data-stu-id="a3a73-195">The modules specified in this parameter value are imported in additions to modules specified in the session configuration file (`New-PSSessionConfigurationFile`).</span></span> <span data-ttu-id="a3a73-196">Inställningarna i konfigurations filen för sessionen kan dock dölja de kommandon som exporteras av moduler eller hindra användarna från att använda dem.</span><span class="sxs-lookup"><span data-stu-id="a3a73-196">However, settings in the session configuration file can hide the commands exported by modules or prevent users from using them.</span></span>

<span data-ttu-id="a3a73-197">Modulerna som anges i detta parameter värde ersätter listan över moduler som anges genom att använda **ModulesToImport** -parametern för `Register-PSSessionConfiguration` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a3a73-197">The modules specified in this parameter value replace the list of modules specified by using the **ModulesToImport** parameter of the `Register-PSSessionConfiguration` cmdlet.</span></span>

<span data-ttu-id="a3a73-198">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a3a73-198">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="a3a73-199">-Name</span><span class="sxs-lookup"><span data-stu-id="a3a73-199">-Name</span></span>

<span data-ttu-id="a3a73-200">Anger namnet på den sessionsinformation som du vill ändra.</span><span class="sxs-lookup"><span data-stu-id="a3a73-200">Specifies the name of the session configuration that you want to change.</span></span>

<span data-ttu-id="a3a73-201">Du kan inte använda den här parametern för att ändra namnet på konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-201">You cannot use this parameter to change the name of the session configuration.</span></span>

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

### <span data-ttu-id="a3a73-202">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="a3a73-202">-NoServiceRestart</span></span>

<span data-ttu-id="a3a73-203">Startar inte om **WinRM** -tjänsten och inaktiverar uppmaningen att starta om tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a3a73-203">Does not restart the **WinRM** service, and suppresses the prompt to restart the service.</span></span>

<span data-ttu-id="a3a73-204">När du kör `Set-PSSessionConfiguration` uppmanas du som standard att starta om **WinRM** -tjänsten för att den nya konfigurationen ska fungera.</span><span class="sxs-lookup"><span data-stu-id="a3a73-204">By default, when you run `Set-PSSessionConfiguration`, you are prompted to restart the **WinRM** service to make the new session configuration effective.</span></span> <span data-ttu-id="a3a73-205">Den nya konfigurationen är inte giltig förrän **WinRM** -tjänsten har startats om.</span><span class="sxs-lookup"><span data-stu-id="a3a73-205">Until the **WinRM** service is restarted, the new session configuration is not effective.</span></span>

<span data-ttu-id="a3a73-206">Om du vill starta om **WinRM** -tjänsten utan att begära det använder du parametern **Force** .</span><span class="sxs-lookup"><span data-stu-id="a3a73-206">To restart the **WinRM** service without prompting, use the **Force** parameter.</span></span> <span data-ttu-id="a3a73-207">Om du vill starta om **WinRM** -tjänsten manuellt använder du `Restart-Service` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a3a73-207">To restart the **WinRM** service manually, use the `Restart-Service` cmdlet.</span></span>

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

### <span data-ttu-id="a3a73-208">-Path</span><span class="sxs-lookup"><span data-stu-id="a3a73-208">-Path</span></span>

<span data-ttu-id="a3a73-209">Anger sökvägen till en sessions konfigurations fil (. PSSC), till exempel en som skapats av `New-PSSessionConfigurationFile` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a3a73-209">Specifies the path of a session configuration file (.pssc), such as one created by the `New-PSSessionConfigurationFile` cmdlet.</span></span> <span data-ttu-id="a3a73-210">Om du utelämnar sökvägen är standardvärdet den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-210">If you omit the path, the default is the current directory.</span></span>

<span data-ttu-id="a3a73-211">Information om hur du ändrar en konfigurations fil för en session finns i hjälp avsnittet för `New-PSSessionConfigurationFile` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a3a73-211">For information about how to modify a session configuration file, see the help topic for the `New-PSSessionConfigurationFile` cmdlet.</span></span>

<span data-ttu-id="a3a73-212">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a3a73-212">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="a3a73-213">– PSVersion</span><span class="sxs-lookup"><span data-stu-id="a3a73-213">-PSVersion</span></span>

<span data-ttu-id="a3a73-214">Anger versionen för PowerShell i sessioner som använder den här sessionen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-214">Specifies the version of PowerShell in sessions that use this session configuration.</span></span>

<span data-ttu-id="a3a73-215">Värdet för den här parametern prioriteras över värdet för **PowerShellVersion** -nyckeln i sessionens konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="a3a73-215">The value of this parameter takes precedence over the value of the **PowerShellVersion** key in the session configuration file.</span></span>

<span data-ttu-id="a3a73-216">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a3a73-216">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="a3a73-217">-RunAsCredential</span><span class="sxs-lookup"><span data-stu-id="a3a73-217">-RunAsCredential</span></span>

<span data-ttu-id="a3a73-218">Anger autentiseringsuppgifter för kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-218">Specifies credentials for commands in the session.</span></span> <span data-ttu-id="a3a73-219">Som standard körs kommandona med behörigheterna för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="a3a73-219">By default, commands run with the permissions of the current user.</span></span>

<span data-ttu-id="a3a73-220">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a3a73-220">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="a3a73-221">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="a3a73-221">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="a3a73-222">Anger en annan SDDL-sträng (Security Descriptor Definition Language) för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-222">Specifies a different Security Descriptor Definition Language (SDDL) string for the configuration.</span></span>

<span data-ttu-id="a3a73-223">Den här strängen avgör vilka behörigheter som krävs för att använda den nya konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-223">This string determines the permissions that are required to use the new session configuration.</span></span> <span data-ttu-id="a3a73-224">Om du vill använda en sessionshantering i en session måste användarna ha minst körnings behörighet (Invoke) för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-224">To use a session configuration in a session, users must have at least Execute(Invoke) permission for the configuration.</span></span>

<span data-ttu-id="a3a73-225">Om du vill använda standard säkerhets beskrivningen för konfigurationen anger du en tom sträng ("") eller värdet `$Null` .</span><span class="sxs-lookup"><span data-stu-id="a3a73-225">To use the default security descriptor for the configuration, enter an empty string ("") or a value of `$Null`.</span></span> <span data-ttu-id="a3a73-226">Standardvärdet är rot-SDDL i filen WSMan: Drive.</span><span class="sxs-lookup"><span data-stu-id="a3a73-226">The default is the root SDDL in the WSMan: drive.</span></span>

<span data-ttu-id="a3a73-227">Om säkerhets beskrivningen är komplex kan du överväga att använda parametern **ShowSecurityDescriptorUI** i stället för den här.</span><span class="sxs-lookup"><span data-stu-id="a3a73-227">If the security descriptor is complex, consider using the **ShowSecurityDescriptorUI** parameter instead of this one.</span></span> <span data-ttu-id="a3a73-228">Du kan inte använda båda parametrarna i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="a3a73-228">You cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="a3a73-229">-SessionTypeOption</span><span class="sxs-lookup"><span data-stu-id="a3a73-229">-SessionTypeOption</span></span>

<span data-ttu-id="a3a73-230">Anger typspecifika alternativ för konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-230">Specifies type-specific options for the session configuration.</span></span> <span data-ttu-id="a3a73-231">Ange ett alternativ för sessionsläge, till exempel **PSWorkflowExecutionOption** -objektet som `New-PSWorkflowExecutionOption` cmdleten returnerar.</span><span class="sxs-lookup"><span data-stu-id="a3a73-231">Enter a session type options object, such as the **PSWorkflowExecutionOption** object that the `New-PSWorkflowExecutionOption` cmdlet returns.</span></span>

<span data-ttu-id="a3a73-232">Alternativen för sessioner som använder sessionen bestäms av värdena för session-alternativen och konfigurations alternativen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-232">The options of sessions that use the session configuration are determined by the values of session options and the session configuration options.</span></span> <span data-ttu-id="a3a73-233">Om inget annat anges får alternativ som anges i sessionen, till exempel med hjälp av `New-PSSessionOption` cmdleten, företräde framför alternativ som angetts i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-233">Unless specified, options set in the session, such as by using the `New-PSSessionOption` cmdlet, take precedence over options set in the session configuration.</span></span> <span data-ttu-id="a3a73-234">Värdena för sessionens alternativ får dock inte överskrida de maximala värden som angetts i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-234">However, session option values cannot exceed maximum values set in the session configuration.</span></span>

<span data-ttu-id="a3a73-235">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a3a73-235">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="a3a73-236">-ShowSecurityDescriptorUI</span><span class="sxs-lookup"><span data-stu-id="a3a73-236">-ShowSecurityDescriptorUI</span></span>

<span data-ttu-id="a3a73-237">Anger att denna cmdlet är en egenskaps sida som hjälper dig att skapa en ny SDDL för konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-237">Indicates that this cmdlet a property sheet that helps you create a new SDDL for the session configuration.</span></span> <span data-ttu-id="a3a73-238">Egenskaps sidan visas när du har kört `Set-PSSessionConfiguration` kommandot och startat om **WinRM** -tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a3a73-238">The property sheet appears after you run the `Set-PSSessionConfiguration` command and then restart the **WinRM** service.</span></span>

<span data-ttu-id="a3a73-239">Kom ihåg att användarna måste ha minst körnings behörighet för att kunna använda sessionen i en session när du anger behörigheter för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-239">When you set permissions to the configuration, remember that users must have at least Execute(Invoke) permission to use the session configuration in a session.</span></span>

<span data-ttu-id="a3a73-240">Du kan inte använda parametern **SecurityDescriptorSDDL** och den här parametern i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="a3a73-240">You cannot use the **SecurityDescriptorSDDL** parameter and this parameter in the same command.</span></span>

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

### <span data-ttu-id="a3a73-241">-StartupScript</span><span class="sxs-lookup"><span data-stu-id="a3a73-241">-StartupScript</span></span>

<span data-ttu-id="a3a73-242">Anger start skriptet för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-242">Specifies the startup script for the configuration.</span></span> <span data-ttu-id="a3a73-243">Ange den fullständigt kvalificerade sökvägen till ett PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="a3a73-243">Enter the fully qualified path of a PowerShell script.</span></span> <span data-ttu-id="a3a73-244">Det angivna skriptet körs i den nya sessionen som använder konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-244">The specified script runs in the new session that uses the session configuration.</span></span>

<span data-ttu-id="a3a73-245">Om du vill ta bort ett start skript från en sessions konfiguration anger du en tom sträng ("") eller värdet `$Null` .</span><span class="sxs-lookup"><span data-stu-id="a3a73-245">To delete a startup script from a session configuration, enter an empty string ("") or a value of `$Null`.</span></span>

<span data-ttu-id="a3a73-246">Du kan använda ett start skript för att ytterligare konfigurera användarsessionen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-246">You can use a startup script to further configure the user session.</span></span> <span data-ttu-id="a3a73-247">Om skriptet genererar ett fel, till och med ett icke-avslutande fel, skapas inte sessionen och `New-PSSession` kommandot Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="a3a73-247">If the script generates an error, even a non-terminating error, the session is not created and the `New-PSSession` command fails.</span></span>

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

### <span data-ttu-id="a3a73-248">-ThreadOptions</span><span class="sxs-lookup"><span data-stu-id="a3a73-248">-ThreadOptions</span></span>

<span data-ttu-id="a3a73-249">Anger inställningen för tråd alternativ i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-249">Specifies the thread options setting in the configuration.</span></span> <span data-ttu-id="a3a73-250">Den här inställningen definierar hur trådar skapas och används när ett kommando körs i sessionen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-250">This setting defines how threads are created and used when a command is executed in the session.</span></span> <span data-ttu-id="a3a73-251">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="a3a73-251">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="a3a73-252">Standardvärde</span><span class="sxs-lookup"><span data-stu-id="a3a73-252">Default</span></span>
- <span data-ttu-id="a3a73-253">ReuseThread</span><span class="sxs-lookup"><span data-stu-id="a3a73-253">ReuseThread</span></span>
- <span data-ttu-id="a3a73-254">UseCurrentThread</span><span class="sxs-lookup"><span data-stu-id="a3a73-254">UseCurrentThread</span></span>
- <span data-ttu-id="a3a73-255">UseNewThread</span><span class="sxs-lookup"><span data-stu-id="a3a73-255">UseNewThread</span></span>

<span data-ttu-id="a3a73-256">Standardvärdet är **UseCurrentThread**.</span><span class="sxs-lookup"><span data-stu-id="a3a73-256">The default value is **UseCurrentThread**.</span></span>

<span data-ttu-id="a3a73-257">Mer information finns i [PSThreadOptions-uppräkning](/dotnet/api/system.management.automation.runspaces.psthreadoptions).</span><span class="sxs-lookup"><span data-stu-id="a3a73-257">For more information, see [PSThreadOptions Enumeration](/dotnet/api/system.management.automation.runspaces.psthreadoptions).</span></span>

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

### <span data-ttu-id="a3a73-258">-TransportOption</span><span class="sxs-lookup"><span data-stu-id="a3a73-258">-TransportOption</span></span>

<span data-ttu-id="a3a73-259">Anger transport alternativ för konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-259">Specifies the transport options for the session configuration.</span></span> <span data-ttu-id="a3a73-260">Ange ett transport alternativ objekt, till exempel **WSManConfigurationOption** -objektet som `New-PSTransportOption` cmdleten returnerar.</span><span class="sxs-lookup"><span data-stu-id="a3a73-260">Enter a transport options object, such as the **WSManConfigurationOption** object that the `New-PSTransportOption` cmdlet returns.</span></span>

<span data-ttu-id="a3a73-261">Alternativen för sessioner som använder sessionen bestäms av värdena för session-alternativen och konfigurations alternativen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-261">The options of sessions that use the session configuration are determined by the values of session options and the session configuration options.</span></span> <span data-ttu-id="a3a73-262">Om inget annat anges får alternativ som anges i sessionen, till exempel med hjälp av `New-PSSessionOption` cmdleten, företräde framför alternativ som angetts i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-262">Unless specified, options set in the session, such as by using the `New-PSSessionOption` cmdlet, take precedence over options set in the session configuration.</span></span> <span data-ttu-id="a3a73-263">Värdena för sessionens alternativ får dock inte överskrida de maximala värden som angetts i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-263">However, session option values cannot exceed maximum values set in the session configuration.</span></span>

<span data-ttu-id="a3a73-264">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a3a73-264">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="a3a73-265">-UseSharedProcess</span><span class="sxs-lookup"><span data-stu-id="a3a73-265">-UseSharedProcess</span></span>

<span data-ttu-id="a3a73-266">Använd bara en process som värd för alla sessioner som startas av samma användare och Använd samma sessions konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a3a73-266">Use only one process to host all sessions that are started by the same user and use the same session configuration.</span></span> <span data-ttu-id="a3a73-267">Som standard finns varje session i en egen process.</span><span class="sxs-lookup"><span data-stu-id="a3a73-267">By default, each session is hosted in its own process.</span></span>

<span data-ttu-id="a3a73-268">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a3a73-268">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="a3a73-269">-Confirm</span><span class="sxs-lookup"><span data-stu-id="a3a73-269">-Confirm</span></span>

<span data-ttu-id="a3a73-270">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a3a73-270">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="a3a73-271">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="a3a73-271">-WhatIf</span></span>

<span data-ttu-id="a3a73-272">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="a3a73-272">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="a3a73-273">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="a3a73-273">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="a3a73-274">-ThreadApartmentState</span><span class="sxs-lookup"><span data-stu-id="a3a73-274">-ThreadApartmentState</span></span>

<span data-ttu-id="a3a73-275">Anger Apartment-statusen för den trådad modul som ska användas.</span><span class="sxs-lookup"><span data-stu-id="a3a73-275">Specifies the apartment state of the threading module to be used.</span></span> <span data-ttu-id="a3a73-276">Godkända värden är:</span><span class="sxs-lookup"><span data-stu-id="a3a73-276">Acceptable values are:</span></span>

- <span data-ttu-id="a3a73-277">Okänt</span><span class="sxs-lookup"><span data-stu-id="a3a73-277">Unknown</span></span>
- <span data-ttu-id="a3a73-278">MTA</span><span class="sxs-lookup"><span data-stu-id="a3a73-278">MTA</span></span>
- <span data-ttu-id="a3a73-279">S</span><span class="sxs-lookup"><span data-stu-id="a3a73-279">STA</span></span>

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

### <span data-ttu-id="a3a73-280">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a3a73-280">CommonParameters</span></span>

<span data-ttu-id="a3a73-281">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a3a73-281">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a3a73-282">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a3a73-282">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a3a73-283">INDATA</span><span class="sxs-lookup"><span data-stu-id="a3a73-283">INPUTS</span></span>

### <span data-ttu-id="a3a73-284">Inga</span><span class="sxs-lookup"><span data-stu-id="a3a73-284">None</span></span>

<span data-ttu-id="a3a73-285">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a3a73-285">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="a3a73-286">UTDATA</span><span class="sxs-lookup"><span data-stu-id="a3a73-286">OUTPUTS</span></span>

### <span data-ttu-id="a3a73-287">Microsoft. WSMan. Management. WSManConfigLeafElement</span><span class="sxs-lookup"><span data-stu-id="a3a73-287">Microsoft.WSMan.Management.WSManConfigLeafElement</span></span>

## <span data-ttu-id="a3a73-288">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="a3a73-288">NOTES</span></span>

<span data-ttu-id="a3a73-289">Den här cmdleten är endast tillgänglig på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="a3a73-289">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="a3a73-290">Starta PowerShell med alternativet Kör som administratör för att köra denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a3a73-290">To run this cmdlet, start PowerShell by using the Run as administrator option.</span></span>

<span data-ttu-id="a3a73-291">`Set-PSSessionConfiguration`Cmdleten ändrar inte konfigurations namnet och **WSMan** -providern stöder inte `Rename-Item` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a3a73-291">The `Set-PSSessionConfiguration` cmdlet does not change the configuration name and the **WSMan** provider does not support the `Rename-Item` cmdlet.</span></span> <span data-ttu-id="a3a73-292">Om du vill ändra namnet på en sessions konfiguration använder du `Unregister-PSSessionConfiguration` cmdleten för att ta bort konfigurationen och använder sedan `Register-PSSessionConfiguration` cmdleten för att skapa och registrera en ny konfiguration av sessionen.</span><span class="sxs-lookup"><span data-stu-id="a3a73-292">To change the name of a session configuration, use the `Unregister-PSSessionConfiguration` cmdlet to delete the configuration and then use the `Register-PSSessionConfiguration` cmdlet to create and register a new session configuration.</span></span>

<span data-ttu-id="a3a73-293">Du kan använda `Set-PSSessionConfiguration` cmdleten för att ändra standard konfigurationerna för Microsoft. PowerShell och Microsoft. PowerShell32.</span><span class="sxs-lookup"><span data-stu-id="a3a73-293">You can use the `Set-PSSessionConfiguration` cmdlet to change the default Microsoft.PowerShell and Microsoft.PowerShell32 session configurations.</span></span> <span data-ttu-id="a3a73-294">De är inte skyddade.</span><span class="sxs-lookup"><span data-stu-id="a3a73-294">They are not protected.</span></span> <span data-ttu-id="a3a73-295">Om du vill återgå till den ursprungliga versionen av en standardsession, använder du `Unregister-PSSessionConfiguration` cmdleten för att ta bort standardsessionens konfiguration och använder sedan `Enable-PSRemoting` cmdlet: en för att återställa den.</span><span class="sxs-lookup"><span data-stu-id="a3a73-295">To revert to the original version of a default session configuration, use the `Unregister-PSSessionConfiguration` cmdlet to delete the default session configuration and then use the `Enable-PSRemoting` cmdlet to restore it.</span></span>

<span data-ttu-id="a3a73-296">Egenskaperna för ett konfigurations objekt för en session varierar beroende på vilka alternativ som har angetts för konfigurationen av sessionen och värdena för dessa alternativ.</span><span class="sxs-lookup"><span data-stu-id="a3a73-296">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="a3a73-297">Dessutom har sessionsinställningar som använder en konfigurations fil för sessionen ytterligare egenskaper.</span><span class="sxs-lookup"><span data-stu-id="a3a73-297">Also, session configurations that use a session configuration file have additional properties.</span></span>

<span data-ttu-id="a3a73-298">Du kan använda kommandona i WSMan: Drive för att ändra egenskaperna för sessionens konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="a3a73-298">You can use commands in the WSMan: drive to change the properties of session configurations.</span></span>
<span data-ttu-id="a3a73-299">Du kan dock inte använda WSMan:-enheten i PowerShell 2,0 för att ändra konfigurations egenskaper för sessionen som introduceras i PowerShell 3,0, till exempel **OutputBufferingMode**.</span><span class="sxs-lookup"><span data-stu-id="a3a73-299">However, you cannot use the WSMan: drive in PowerShell 2.0 to change session configuration properties that are introduced in PowerShell 3.0, such as **OutputBufferingMode**.</span></span> <span data-ttu-id="a3a73-300">Windows PowerShell 2,0-kommandon genererar inte ett fel, men de är inaktiva.</span><span class="sxs-lookup"><span data-stu-id="a3a73-300">Windows PowerShell 2.0 commands do not generate an error, but they are ineffective.</span></span> <span data-ttu-id="a3a73-301">Om du vill ändra de egenskaper som introduceras i PowerShell 3,0 använder du kommandot WSMan: Drive i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a3a73-301">To change properties introduced in PowerShell 3.0, use the WSMan: drive in PowerShell 3.0.</span></span>

## <span data-ttu-id="a3a73-302">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="a3a73-302">RELATED LINKS</span></span>

[<span data-ttu-id="a3a73-303">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a3a73-303">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="a3a73-304">Aktivera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a3a73-304">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="a3a73-305">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a3a73-305">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="a3a73-306">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="a3a73-306">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="a3a73-307">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="a3a73-307">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="a3a73-308">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="a3a73-308">New-PSTransportOption</span></span>](New-PSTransportOption.md)

[<span data-ttu-id="a3a73-309">Registrera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a3a73-309">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="a3a73-310">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="a3a73-310">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="a3a73-311">Avregistrera-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="a3a73-311">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="a3a73-312">WSMan-Provider</span><span class="sxs-lookup"><span data-stu-id="a3a73-312">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="a3a73-313">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="a3a73-313">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="a3a73-314">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="a3a73-314">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
