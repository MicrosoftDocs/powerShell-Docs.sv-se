---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/set-pssessionconfiguration?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSSessionConfiguration
ms.openlocfilehash: c1d0d0bc2452e7f05fd47574dedeb4a1b9686fad
ms.sourcegitcommit: 37abf054ad9eda8813be8ff4487803b10e1842ef
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/23/2020
ms.locfileid: "93268533"
---
# <span data-ttu-id="81215-103">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="81215-103">Set-PSSessionConfiguration</span></span>

## <span data-ttu-id="81215-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="81215-104">SYNOPSIS</span></span>
<span data-ttu-id="81215-105">Ändrar egenskaperna för en registrerad session-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="81215-105">Changes the properties of a registered session configuration.</span></span>

## <span data-ttu-id="81215-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="81215-106">SYNTAX</span></span>

### <span data-ttu-id="81215-107">NameParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="81215-107">NameParameterSet (Default)</span></span>

```
Set-PSSessionConfiguration [-Name] <String> [-ApplicationBase <String>] [-RunAsCredential <PSCredential>]
 [-ThreadApartmentState <ApartmentState>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>] [-TransportOption <PSTransportOption>]
 [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="81215-108">AssemblyNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="81215-108">AssemblyNameParameterSet</span></span>

```
Set-PSSessionConfiguration [-Name] <String> [-AssemblyName] <String> [-ApplicationBase <String>]
 [-ConfigurationTypeName] <String> [-RunAsCredential <PSCredential>] [-ThreadApartmentState <ApartmentState>]
 [-ThreadOptions <PSThreadOptions>] [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess]
 [-StartupScript <String>] [-MaximumReceivedDataSizePerCommandMB <Double>]
 [-MaximumReceivedObjectSizeMB <Double>] [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI]
 [-Force] [-NoServiceRestart] [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>]
 [-TransportOption <PSTransportOption>] [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="81215-109">SessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="81215-109">SessionConfigurationFile</span></span>

```
Set-PSSessionConfiguration [-Name] <String> [-RunAsCredential <PSCredential>]
 [-ThreadApartmentState <ApartmentState>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-TransportOption <PSTransportOption>] -Path <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="81215-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="81215-110">DESCRIPTION</span></span>

<span data-ttu-id="81215-111">`Set-PSSessionConfiguration`Cmdleten ändrar egenskaperna för sessionens konfigurationer på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="81215-111">The `Set-PSSessionConfiguration` cmdlet changes the properties of the session configurations on the local computer.</span></span>

<span data-ttu-id="81215-112">Använd parametern **Name** för att identifiera den konfiguration av sessionen som du vill ändra.</span><span class="sxs-lookup"><span data-stu-id="81215-112">Use the **Name** parameter to identify the session configuration that you want to change.</span></span> <span data-ttu-id="81215-113">Använd de andra parametrarna för att ange nya värden för egenskaperna för sessionen.</span><span class="sxs-lookup"><span data-stu-id="81215-113">Use the other parameters to specify new values for the properties of the session configuration.</span></span> <span data-ttu-id="81215-114">Om du vill ta bort ett egenskaps värde från konfigurationen och använda standardvärdet anger du en tom sträng ("") eller värdet `$Null` för motsvarande parameter.</span><span class="sxs-lookup"><span data-stu-id="81215-114">To delete a property value from the configuration, and use the default value, enter an empty string ("") or a value of `$Null` for the corresponding parameter.</span></span>

<span data-ttu-id="81215-115">Från och med PowerShell 3,0 kan du använda en konfigurations fil för sessionen för att definiera en sessions-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="81215-115">Starting in PowerShell 3.0, you can use a session configuration file to define a session configuration.</span></span> <span data-ttu-id="81215-116">Den här funktionen ger en enkel och identifierad metod för att ange och ändra egenskaperna för sessioner som använder sessionen.</span><span class="sxs-lookup"><span data-stu-id="81215-116">This feature provides a simple and discoverable method for setting and changing the properties of sessions that use the session configuration.</span></span> <span data-ttu-id="81215-117">Om du vill ange en konfigurations fil för sessionen använder du parametern **Path** i `Set-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="81215-117">To specify a session configuration file, use the **Path** parameter of `Set-PSSessionConfiguration`.</span></span> <span data-ttu-id="81215-118">Information om konfigurationsfiler för sessioner finns [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span><span class="sxs-lookup"><span data-stu-id="81215-118">For information about session configuration files, see [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>
<span data-ttu-id="81215-119">Information om hur du skapar och ändrar en konfigurations fil för en session finns i `New-PSSessionConfigurationFile` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="81215-119">For information about how to create and modify a session configuration file, see the `New-PSSessionConfigurationFile` cmdlet.</span></span>

<span data-ttu-id="81215-120">Sessionsbaserade definierar miljön för fjärrsessioner ( **PSSessions** ) som ansluter till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="81215-120">Session configurations define the environment of remote sessions ( **PSSessions** ) that connect to the local computer.</span></span> <span data-ttu-id="81215-121">Varje **PSSession** använder en konfiguration av sessionen.</span><span class="sxs-lookup"><span data-stu-id="81215-121">Every **PSSession** uses a session configuration.</span></span> <span data-ttu-id="81215-122">Konfigurationen av sessionen bestämmer funktionerna i **PSSession** , till exempel de moduler som är tillgängliga i sessionen, vilka cmdlets som tillåts köras, språk läge, kvoter och tids gränser.</span><span class="sxs-lookup"><span data-stu-id="81215-122">The session configuration determines the features of the **PSSession** , such as the modules that are available in the session, the cmdlets that are permitted to run, the language mode, quotas, and timeouts.</span></span> <span data-ttu-id="81215-123">Säkerhets beskrivningen för konfigurationen av sessionen avgör vem som kan använda sessionen för att ansluta till den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="81215-123">The security descriptor of the session configuration determines who can use the session configuration to connect to the local computer.</span></span> <span data-ttu-id="81215-124">För ytterligare information om sessionskonfigurationer, se [about_Session_Configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="81215-124">For more information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

<span data-ttu-id="81215-125">Använd `Get-PSSessionConfiguration` cmdleten eller WSMan-providern för att se egenskaperna för en sessions konfiguration.</span><span class="sxs-lookup"><span data-stu-id="81215-125">To see the properties of a session configuration, use the `Get-PSSessionConfiguration` cmdlet or the WSMan Provider.</span></span> <span data-ttu-id="81215-126">Om du vill ha mer information om WSMan-providern skriver du `Get-Help WSMan` .</span><span class="sxs-lookup"><span data-stu-id="81215-126">For more information about the WSMan Provider, type `Get-Help WSMan`.</span></span>

## <span data-ttu-id="81215-127">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="81215-127">EXAMPLES</span></span>

### <span data-ttu-id="81215-128">Exempel 1: skapa och ändra en konfiguration av sessionen</span><span class="sxs-lookup"><span data-stu-id="81215-128">Example 1: Create and change a session configuration</span></span>

<span data-ttu-id="81215-129">Det här exemplet visar hur du lägger till och tar bort ett start skript från en konfiguration.</span><span class="sxs-lookup"><span data-stu-id="81215-129">This example shows how to add and remove a startup script from a configuration.</span></span>

<span data-ttu-id="81215-130">Det första kommandot skapar **AdminShell** -konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="81215-130">The first command creates the **AdminShell** configuration.</span></span> <span data-ttu-id="81215-131">Det andra kommandot lägger till `AdminConfig.ps1` skriptet i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="81215-131">The second command adds the `AdminConfig.ps1` script to the configuration.</span></span> <span data-ttu-id="81215-132">Ändringen gäller när du startar om **WinRM**.</span><span class="sxs-lookup"><span data-stu-id="81215-132">The change is effective when you restart **WinRM**.</span></span>
<span data-ttu-id="81215-133">Det tredje kommandot tar bort `AdminConfig.ps1` skriptet från konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="81215-133">The third command removes the `AdminConfig.ps1` script from the configuration.</span></span>

```powershell
Register-PSSessionConfiguration -Name "AdminShell" -AssemblyName "C:\Shells\AdminShell.dll" -ConfigurationTypeName "AdminClass"
Set-PSSessionConfiguration -Name "AdminShell" -StartupScript "AdminConfig.ps1"
Set-PSSessionConfiguration -Name "AdminShell" -StartupScript $Null
```

### <span data-ttu-id="81215-134">Exempel 2: Visa resultat</span><span class="sxs-lookup"><span data-stu-id="81215-134">Example 2: Display results</span></span>

<span data-ttu-id="81215-135">Det här exemplet ökar värdet för egenskapen **MaximumReceivedObjectSizeMB** till 20.</span><span class="sxs-lookup"><span data-stu-id="81215-135">This example increases the value of the **MaximumReceivedObjectSizeMB** property to 20.</span></span> <span data-ttu-id="81215-136">Det här kommandot kräver också att du startar om **WinRM** -tjänsten.</span><span class="sxs-lookup"><span data-stu-id="81215-136">This command also prompts you to restart the **WinRM** service.</span></span> <span data-ttu-id="81215-137">Ändringen gäller inte förrän **WinRM** -tjänsten har startats om.</span><span class="sxs-lookup"><span data-stu-id="81215-137">The change is not effective until the **WinRM** service is restarted.</span></span>

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

### <span data-ttu-id="81215-138">Exempel 3: Visa resultat på olika sätt</span><span class="sxs-lookup"><span data-stu-id="81215-138">Example 3: Display results in different ways</span></span>

<span data-ttu-id="81215-139">I det här exemplet `Set-PSSessionConfiguration` ändrar Start skriptet i **MaintenanceShell** -sessionen till `Maintenance.ps1` .</span><span class="sxs-lookup"><span data-stu-id="81215-139">In this example, `Set-PSSessionConfiguration` changes the startup script in the **MaintenanceShell** session configuration to `Maintenance.ps1`.</span></span> <span data-ttu-id="81215-140">Resultatet visar ändringen och du ombeds att starta om **WinRM** -tjänsten.</span><span class="sxs-lookup"><span data-stu-id="81215-140">The output shows the change and prompts you to restart the **WinRM** service.</span></span> <span data-ttu-id="81215-141">Svaret är "y" (Ja).</span><span class="sxs-lookup"><span data-stu-id="81215-141">The response is "y" (yes).</span></span>

<span data-ttu-id="81215-142">`Get-PSSessionConfiguration` hämtar konfigurationen för **MaintenanceShell** -sessionen.</span><span class="sxs-lookup"><span data-stu-id="81215-142">`Get-PSSessionConfiguration` gets the **MaintenanceShell** session configuration.</span></span> <span data-ttu-id="81215-143">Pipeline-operatorn (|) skickar resultatet från kommandot till `Format-List` , som visar alla egenskaper för konfigurationsobjektet i en lista.</span><span class="sxs-lookup"><span data-stu-id="81215-143">The pipeline operator (|) sends the results of the command to `Format-List`, which displays all the properties of the configuration object in a list.</span></span> <span data-ttu-id="81215-144">Därefter visar vi initierings parametrarna för **MaintenanceShell** -konfigurationen med hjälp av WSMan-providern.</span><span class="sxs-lookup"><span data-stu-id="81215-144">Next, using the WSMan provider, we view the initialization parameters for the **MaintenanceShell** configuration.</span></span> <span data-ttu-id="81215-145">`Get-ChildItem` (alias `dir` ) hämtar de underordnade objekten i **InitializationParameters** -noden för **MaintenanceShell** -plugin-programmet.</span><span class="sxs-lookup"><span data-stu-id="81215-145">`Get-ChildItem` (alias `dir`) gets the child items in the **InitializationParameters** node for the **MaintenanceShell** plug-in.</span></span> <span data-ttu-id="81215-146">Om du vill ha mer information om WSMan-providern skriver du `Get-Help wsman` .</span><span class="sxs-lookup"><span data-stu-id="81215-146">For more information about the WSMan provider, type `Get-Help wsman`.</span></span>

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

## <span data-ttu-id="81215-147">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="81215-147">PARAMETERS</span></span>

### <span data-ttu-id="81215-148">-AccessMode</span><span class="sxs-lookup"><span data-stu-id="81215-148">-AccessMode</span></span>

<span data-ttu-id="81215-149">Aktiverar och inaktiverar konfigurationen av sessionen och avgör om den kan användas för fjärranslutna eller lokala sessioner på datorn.</span><span class="sxs-lookup"><span data-stu-id="81215-149">Enables and disables the session configuration and determines whether it can be used for remote or local sessions on the computer.</span></span> <span data-ttu-id="81215-150">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="81215-150">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="81215-151">Inaktiverat</span><span class="sxs-lookup"><span data-stu-id="81215-151">Disabled.</span></span> <span data-ttu-id="81215-152">Inaktiverar konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="81215-152">Disables the session configuration.</span></span> <span data-ttu-id="81215-153">Den kan inte användas för fjärran sluten eller lokal åtkomst till datorn.</span><span class="sxs-lookup"><span data-stu-id="81215-153">It cannot be used for remote or local access to the computer.</span></span> <span data-ttu-id="81215-154">Det här värdet anger egenskapen **Enabled** för session-konfigurationen ( `WSMan:\<ComputerName>\PlugIn\<SessionConfigurationName>\Enabled` ) till **false**.</span><span class="sxs-lookup"><span data-stu-id="81215-154">This value sets the **Enabled** property of the session configuration (`WSMan:\<ComputerName>\PlugIn\<SessionConfigurationName>\Enabled`) to **False**.</span></span>
- <span data-ttu-id="81215-155">Inställningar.</span><span class="sxs-lookup"><span data-stu-id="81215-155">Local.</span></span> <span data-ttu-id="81215-156">Lägger till en **Network_Deny_All** post i säkerhets beskrivningen för konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="81215-156">Adds a **Network_Deny_All** entry to security descriptor of the session configuration.</span></span>
  <span data-ttu-id="81215-157">Användare av den lokala datorn kan använda sessionen för att skapa en lokal loopback-session på samma dator, men fjärran vändare nekas åtkomst.</span><span class="sxs-lookup"><span data-stu-id="81215-157">Users of the local computer can use the session configuration to create a local loopback session on the same computer, but remote users are denied access.</span></span>
- <span data-ttu-id="81215-158">Fjärrserveradministrationsverktyg.</span><span class="sxs-lookup"><span data-stu-id="81215-158">Remote.</span></span> <span data-ttu-id="81215-159">Tar bort **Deny_All** och **Network_Deny_All** poster från säkerhets beskrivarna i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="81215-159">Removes **Deny_All** and **Network_Deny_All** entries from the security descriptors of the session configuration.</span></span> <span data-ttu-id="81215-160">Användare av lokala och fjärranslutna datorer kan använda sessionen för att skapa sessioner och köra kommandon på den här datorn.</span><span class="sxs-lookup"><span data-stu-id="81215-160">Users of local and remote computers can use the session configuration to create sessions and run commands on this computer.</span></span>

<span data-ttu-id="81215-161">Standardvärdet är **fjärran sluten**.</span><span class="sxs-lookup"><span data-stu-id="81215-161">The default value is **Remote**.</span></span>

<span data-ttu-id="81215-162">Andra cmdletar kan åsidosätta värdet för den här parametern senare.</span><span class="sxs-lookup"><span data-stu-id="81215-162">Other cmdlets can override the value of this parameter later.</span></span> <span data-ttu-id="81215-163">Till exempel `Enable-PSRemoting` möjliggör cmdleten alla sessionsbaserade på datorn och tillåter fjärråtkomst till dem, och `Disable-PSRemoting` cmdleten tillåter endast lokal åtkomst till alla sessionsinställningar på datorn.</span><span class="sxs-lookup"><span data-stu-id="81215-163">For example, the `Enable-PSRemoting` cmdlet enables all session configurations on the computer and permits remote access to them, and the `Disable-PSRemoting` cmdlet permits only local access to all session configurations on the computer.</span></span>

<span data-ttu-id="81215-164">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="81215-164">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="81215-165">– ApplicationBase</span><span class="sxs-lookup"><span data-stu-id="81215-165">-ApplicationBase</span></span>

<span data-ttu-id="81215-166">Anger sökvägen till sammansättnings filen ( \* . dll) som anges i värdet för parametern **AssemblyName** .</span><span class="sxs-lookup"><span data-stu-id="81215-166">Specifies the path of the assembly file (\*.dll) that is specified in the value of the **AssemblyName** parameter.</span></span>

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

### <span data-ttu-id="81215-167">-AssemblyName</span><span class="sxs-lookup"><span data-stu-id="81215-167">-AssemblyName</span></span>

<span data-ttu-id="81215-168">Anger sammansättnings namnet.</span><span class="sxs-lookup"><span data-stu-id="81215-168">Specifies the assembly name.</span></span> <span data-ttu-id="81215-169">Denna cmdlet skapar en sessionsnyckel som baseras på en klass som har definierats i en sammansättning.</span><span class="sxs-lookup"><span data-stu-id="81215-169">This cmdlet creates a session configuration based on a class that is defined in an assembly.</span></span>

<span data-ttu-id="81215-170">Ange fil namnet eller den fullständiga sökvägen till en Assembly. dll-fil som definierar en-sessions konfiguration.</span><span class="sxs-lookup"><span data-stu-id="81215-170">Enter the filename or full path of an assembly .dll file that defines a session configuration.</span></span> <span data-ttu-id="81215-171">Om du bara anger fil namnet kan du ange sökvägen i värdet för parametern **ApplicationBase** .</span><span class="sxs-lookup"><span data-stu-id="81215-171">If you enter only the file name, you can enter the path in the value of the **ApplicationBase** parameter.</span></span>

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

### <span data-ttu-id="81215-172">-ConfigurationTypeName</span><span class="sxs-lookup"><span data-stu-id="81215-172">-ConfigurationTypeName</span></span>

<span data-ttu-id="81215-173">Anger typen av sessionsinformation som definieras i sammansättningen i parametern **AssemblyName** .</span><span class="sxs-lookup"><span data-stu-id="81215-173">Specifies the type of the session configuration that is defined in the assembly in the **AssemblyName** parameter.</span></span> <span data-ttu-id="81215-174">Den typ som du anger måste implementera klassen **system. Management. Automation. Remoting. PSSessionConfiguration** .</span><span class="sxs-lookup"><span data-stu-id="81215-174">The type that you specify must implement the **System.Management.Automation.Remoting.PSSessionConfiguration** class.</span></span>

<span data-ttu-id="81215-175">Den här parametern krävs när du anger ett sammansättnings namn.</span><span class="sxs-lookup"><span data-stu-id="81215-175">This parameter is required when you specify an assembly name.</span></span>

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

### <span data-ttu-id="81215-176">-Force</span><span class="sxs-lookup"><span data-stu-id="81215-176">-Force</span></span>

<span data-ttu-id="81215-177">Ignorerar alla användar meddelanden och startar om **WinRM** -tjänsten utan att fråga.</span><span class="sxs-lookup"><span data-stu-id="81215-177">Suppresses all user prompts, and restarts the **WinRM** service without prompting.</span></span> <span data-ttu-id="81215-178">Att starta om tjänsten gör att konfigurations ändringen träder i kraft.</span><span class="sxs-lookup"><span data-stu-id="81215-178">Restarting the service makes the configuration change effective.</span></span>

<span data-ttu-id="81215-179">Om du vill förhindra en omstart och ignorera omstarts meddelandet använder du parametern **NoServiceRestart** .</span><span class="sxs-lookup"><span data-stu-id="81215-179">To prevent a restart and suppress the restart prompt, use the **NoServiceRestart** parameter.</span></span>

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

### <span data-ttu-id="81215-180">-MaximumReceivedDataSizePerCommandMB</span><span class="sxs-lookup"><span data-stu-id="81215-180">-MaximumReceivedDataSizePerCommandMB</span></span>

<span data-ttu-id="81215-181">Anger gränsen för mängden data som kan skickas till den här datorn i ett enda fjärran slutet kommando.</span><span class="sxs-lookup"><span data-stu-id="81215-181">Specifies the limit on the amount of data that can be sent to this computer in any single remote command.</span></span> <span data-ttu-id="81215-182">Ange data storleken i megabyte (MB).</span><span class="sxs-lookup"><span data-stu-id="81215-182">Enter the data size in megabytes (MB).</span></span> <span data-ttu-id="81215-183">Standardvärdet är 50 MB.</span><span class="sxs-lookup"><span data-stu-id="81215-183">The default is 50 MB.</span></span>

<span data-ttu-id="81215-184">Om en data storleks gräns definieras i den konfigurations typ som anges i parametern **ConfigurationTypeName** används gränsen i konfigurations typen.</span><span class="sxs-lookup"><span data-stu-id="81215-184">If a data size limit is defined in the configuration type that is specified in the **ConfigurationTypeName** parameter, the limit in the configuration type is used.</span></span> <span data-ttu-id="81215-185">Värdet för den här parametern ignoreras.</span><span class="sxs-lookup"><span data-stu-id="81215-185">The value of this parameter is ignored.</span></span>

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

### <span data-ttu-id="81215-186">-MaximumReceivedObjectSizeMB</span><span class="sxs-lookup"><span data-stu-id="81215-186">-MaximumReceivedObjectSizeMB</span></span>

<span data-ttu-id="81215-187">Anger gränserna för mängden data som kan skickas till den här datorn i ett enda objekt.</span><span class="sxs-lookup"><span data-stu-id="81215-187">Specifies the limits on the amount of data that can be sent to this computer in any single object.</span></span>
<span data-ttu-id="81215-188">Ange data storleken i megabyte.</span><span class="sxs-lookup"><span data-stu-id="81215-188">Enter the data size in megabytes.</span></span> <span data-ttu-id="81215-189">Standardvärdet är 10 MB.</span><span class="sxs-lookup"><span data-stu-id="81215-189">The default is 10 MB.</span></span>

<span data-ttu-id="81215-190">Om en gräns för objekt storlek definieras i den konfigurations typ som anges i parametern **ConfigurationTypeName** , används gränsen i konfigurations typen.</span><span class="sxs-lookup"><span data-stu-id="81215-190">If an object size limit is defined in the configuration type that is specified in the **ConfigurationTypeName** parameter, the limit in the configuration type is used.</span></span> <span data-ttu-id="81215-191">Värdet för den här parametern ignoreras.</span><span class="sxs-lookup"><span data-stu-id="81215-191">The value of this parameter is ignored.</span></span>

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

### <span data-ttu-id="81215-192">-ModulesToImport</span><span class="sxs-lookup"><span data-stu-id="81215-192">-ModulesToImport</span></span>

<span data-ttu-id="81215-193">Anger moduler och snapin-moduler som importeras automatiskt till sessioner som använder-sessionen.</span><span class="sxs-lookup"><span data-stu-id="81215-193">Specifies the modules and snap-ins that are automatically imported into sessions that use the session configuration.</span></span> <span data-ttu-id="81215-194">Ange modul och namn på snapin-modulen.</span><span class="sxs-lookup"><span data-stu-id="81215-194">Enter the module and snap-in names.</span></span>

<span data-ttu-id="81215-195">Som standard importeras bara snapin-modulen **Microsoft. PowerShell. Core** till sessioner, men om inte cmdletarna utesluts kan du använda- `Import-Module` och Add-PSSnapin-cmdletarna för att lägga till moduler och snapin-moduler till sessionen.</span><span class="sxs-lookup"><span data-stu-id="81215-195">By default, only the **Microsoft.PowerShell.Core** snap-in is imported into sessions, but unless the cmdlets are excluded, you can use the `Import-Module` and Add-PSSnapin cmdlets to add modules and snap-ins to the session.</span></span>

<span data-ttu-id="81215-196">Modulerna som anges i detta parameter värde importeras i tillägg till moduler som anges i konfigurations filen för sessionen ( `New-PSSessionConfigurationFile` ).</span><span class="sxs-lookup"><span data-stu-id="81215-196">The modules specified in this parameter value are imported in additions to modules specified in the session configuration file (`New-PSSessionConfigurationFile`).</span></span> <span data-ttu-id="81215-197">Inställningarna i konfigurations filen för sessionen kan dock dölja de kommandon som exporteras av moduler eller hindra användarna från att använda dem.</span><span class="sxs-lookup"><span data-stu-id="81215-197">However, settings in the session configuration file can hide the commands exported by modules or prevent users from using them.</span></span>

<span data-ttu-id="81215-198">Modulerna som anges i detta parameter värde ersätter listan över moduler som anges genom att använda **ModulesToImport** -parametern för `Register-PSSessionConfiguration` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="81215-198">The modules specified in this parameter value replace the list of modules specified by using the **ModulesToImport** parameter of the `Register-PSSessionConfiguration` cmdlet.</span></span>

<span data-ttu-id="81215-199">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="81215-199">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="81215-200">-Name</span><span class="sxs-lookup"><span data-stu-id="81215-200">-Name</span></span>

<span data-ttu-id="81215-201">Anger namnet på den sessionsinformation som du vill ändra.</span><span class="sxs-lookup"><span data-stu-id="81215-201">Specifies the name of the session configuration that you want to change.</span></span>

<span data-ttu-id="81215-202">Du kan inte använda den här parametern för att ändra namnet på konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="81215-202">You cannot use this parameter to change the name of the session configuration.</span></span>

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

### <span data-ttu-id="81215-203">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="81215-203">-NoServiceRestart</span></span>

<span data-ttu-id="81215-204">Startar inte om **WinRM** -tjänsten och inaktiverar uppmaningen att starta om tjänsten.</span><span class="sxs-lookup"><span data-stu-id="81215-204">Does not restart the **WinRM** service, and suppresses the prompt to restart the service.</span></span>

<span data-ttu-id="81215-205">När du kör `Set-PSSessionConfiguration` uppmanas du som standard att starta om **WinRM** -tjänsten för att den nya konfigurationen ska fungera.</span><span class="sxs-lookup"><span data-stu-id="81215-205">By default, when you run `Set-PSSessionConfiguration`, you are prompted to restart the **WinRM** service to make the new session configuration effective.</span></span> <span data-ttu-id="81215-206">Den nya konfigurationen är inte giltig förrän **WinRM** -tjänsten har startats om.</span><span class="sxs-lookup"><span data-stu-id="81215-206">Until the **WinRM** service is restarted, the new session configuration is not effective.</span></span>

<span data-ttu-id="81215-207">Om du vill starta om **WinRM** -tjänsten utan att begära det använder du parametern **Force** .</span><span class="sxs-lookup"><span data-stu-id="81215-207">To restart the **WinRM** service without prompting, use the **Force** parameter.</span></span> <span data-ttu-id="81215-208">Om du vill starta om **WinRM** -tjänsten manuellt använder du `Restart-Service` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="81215-208">To restart the **WinRM** service manually, use the `Restart-Service` cmdlet.</span></span>

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

### <span data-ttu-id="81215-209">-Path</span><span class="sxs-lookup"><span data-stu-id="81215-209">-Path</span></span>

<span data-ttu-id="81215-210">Anger sökvägen till en sessions konfigurations fil (. PSSC), till exempel en som skapats av `New-PSSessionConfigurationFile` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="81215-210">Specifies the path of a session configuration file (.pssc), such as one created by the `New-PSSessionConfigurationFile` cmdlet.</span></span> <span data-ttu-id="81215-211">Om du utelämnar sökvägen är standardvärdet den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="81215-211">If you omit the path, the default is the current directory.</span></span>

<span data-ttu-id="81215-212">Information om hur du ändrar en konfigurations fil för en session finns i hjälp avsnittet för `New-PSSessionConfigurationFile` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="81215-212">For information about how to modify a session configuration file, see the help topic for the `New-PSSessionConfigurationFile` cmdlet.</span></span>

<span data-ttu-id="81215-213">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="81215-213">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="81215-214">– PSVersion</span><span class="sxs-lookup"><span data-stu-id="81215-214">-PSVersion</span></span>

<span data-ttu-id="81215-215">Anger versionen för PowerShell i sessioner som använder den här sessionen.</span><span class="sxs-lookup"><span data-stu-id="81215-215">Specifies the version of PowerShell in sessions that use this session configuration.</span></span>

<span data-ttu-id="81215-216">Värdet för den här parametern prioriteras över värdet för **PowerShellVersion** -nyckeln i sessionens konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="81215-216">The value of this parameter takes precedence over the value of the **PowerShellVersion** key in the session configuration file.</span></span>

<span data-ttu-id="81215-217">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="81215-217">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="81215-218">-RunAsCredential</span><span class="sxs-lookup"><span data-stu-id="81215-218">-RunAsCredential</span></span>

<span data-ttu-id="81215-219">Anger autentiseringsuppgifter för kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="81215-219">Specifies credentials for commands in the session.</span></span> <span data-ttu-id="81215-220">Som standard körs kommandona med behörigheterna för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="81215-220">By default, commands run with the permissions of the current user.</span></span>

<span data-ttu-id="81215-221">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="81215-221">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="81215-222">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="81215-222">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="81215-223">Anger en annan SDDL-sträng (Security Descriptor Definition Language) för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="81215-223">Specifies a different Security Descriptor Definition Language (SDDL) string for the configuration.</span></span>

<span data-ttu-id="81215-224">Den här strängen avgör vilka behörigheter som krävs för att använda den nya konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="81215-224">This string determines the permissions that are required to use the new session configuration.</span></span> <span data-ttu-id="81215-225">Om du vill använda en sessionshantering i en session måste användarna ha minst körnings behörighet (Invoke) för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="81215-225">To use a session configuration in a session, users must have at least Execute(Invoke) permission for the configuration.</span></span>

<span data-ttu-id="81215-226">Om du vill använda standard säkerhets beskrivningen för konfigurationen anger du en tom sträng ("") eller värdet `$Null` .</span><span class="sxs-lookup"><span data-stu-id="81215-226">To use the default security descriptor for the configuration, enter an empty string ("") or a value of `$Null`.</span></span> <span data-ttu-id="81215-227">Standardvärdet är rot-SDDL i filen WSMan: Drive.</span><span class="sxs-lookup"><span data-stu-id="81215-227">The default is the root SDDL in the WSMan: drive.</span></span>

<span data-ttu-id="81215-228">Om säkerhets beskrivningen är komplex kan du överväga att använda parametern **ShowSecurityDescriptorUI** i stället för den här.</span><span class="sxs-lookup"><span data-stu-id="81215-228">If the security descriptor is complex, consider using the **ShowSecurityDescriptorUI** parameter instead of this one.</span></span> <span data-ttu-id="81215-229">Du kan inte använda båda parametrarna i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="81215-229">You cannot use both parameters in the same command.</span></span>

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

### <span data-ttu-id="81215-230">-SessionTypeOption</span><span class="sxs-lookup"><span data-stu-id="81215-230">-SessionTypeOption</span></span>

<span data-ttu-id="81215-231">Anger typspecifika alternativ för konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="81215-231">Specifies type-specific options for the session configuration.</span></span> <span data-ttu-id="81215-232">Ange ett alternativ för sessionsläge, till exempel **PSWorkflowExecutionOption** -objektet som `New-PSWorkflowExecutionOption` cmdleten returnerar.</span><span class="sxs-lookup"><span data-stu-id="81215-232">Enter a session type options object, such as the **PSWorkflowExecutionOption** object that the `New-PSWorkflowExecutionOption` cmdlet returns.</span></span>

<span data-ttu-id="81215-233">Alternativen för sessioner som använder sessionen bestäms av värdena för session-alternativen och konfigurations alternativen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="81215-233">The options of sessions that use the session configuration are determined by the values of session options and the session configuration options.</span></span> <span data-ttu-id="81215-234">Om inget annat anges får alternativ som anges i sessionen, till exempel med hjälp av `New-PSSessionOption` cmdleten, företräde framför alternativ som angetts i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="81215-234">Unless specified, options set in the session, such as by using the `New-PSSessionOption` cmdlet, take precedence over options set in the session configuration.</span></span> <span data-ttu-id="81215-235">Värdena för sessionens alternativ får dock inte överskrida de maximala värden som angetts i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="81215-235">However, session option values cannot exceed maximum values set in the session configuration.</span></span>

<span data-ttu-id="81215-236">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="81215-236">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="81215-237">-ShowSecurityDescriptorUI</span><span class="sxs-lookup"><span data-stu-id="81215-237">-ShowSecurityDescriptorUI</span></span>

<span data-ttu-id="81215-238">Anger att denna cmdlet är en egenskaps sida som hjälper dig att skapa en ny SDDL för konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="81215-238">Indicates that this cmdlet a property sheet that helps you create a new SDDL for the session configuration.</span></span> <span data-ttu-id="81215-239">Egenskaps sidan visas när du har kört `Set-PSSessionConfiguration` kommandot och startat om **WinRM** -tjänsten.</span><span class="sxs-lookup"><span data-stu-id="81215-239">The property sheet appears after you run the `Set-PSSessionConfiguration` command and then restart the **WinRM** service.</span></span>

<span data-ttu-id="81215-240">Kom ihåg att användarna måste ha minst körnings behörighet för att kunna använda sessionen i en session när du anger behörigheter för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="81215-240">When you set permissions to the configuration, remember that users must have at least Execute(Invoke) permission to use the session configuration in a session.</span></span>

<span data-ttu-id="81215-241">Du kan inte använda parametern **SecurityDescriptorSDDL** och den här parametern i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="81215-241">You cannot use the **SecurityDescriptorSDDL** parameter and this parameter in the same command.</span></span>

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

### <span data-ttu-id="81215-242">-StartupScript</span><span class="sxs-lookup"><span data-stu-id="81215-242">-StartupScript</span></span>

<span data-ttu-id="81215-243">Anger start skriptet för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="81215-243">Specifies the startup script for the configuration.</span></span> <span data-ttu-id="81215-244">Ange den fullständigt kvalificerade sökvägen till ett PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="81215-244">Enter the fully qualified path of a PowerShell script.</span></span> <span data-ttu-id="81215-245">Det angivna skriptet körs i den nya sessionen som använder konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="81215-245">The specified script runs in the new session that uses the session configuration.</span></span>

<span data-ttu-id="81215-246">Om du vill ta bort ett start skript från en sessions konfiguration anger du en tom sträng ("") eller värdet `$Null` .</span><span class="sxs-lookup"><span data-stu-id="81215-246">To delete a startup script from a session configuration, enter an empty string ("") or a value of `$Null`.</span></span>

<span data-ttu-id="81215-247">Du kan använda ett start skript för att ytterligare konfigurera användarsessionen.</span><span class="sxs-lookup"><span data-stu-id="81215-247">You can use a startup script to further configure the user session.</span></span> <span data-ttu-id="81215-248">Om skriptet genererar ett fel, till och med ett icke-avslutande fel, skapas inte sessionen och `New-PSSession` kommandot Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="81215-248">If the script generates an error, even a non-terminating error, the session is not created and the `New-PSSession` command fails.</span></span>

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

### <span data-ttu-id="81215-249">-ThreadOptions</span><span class="sxs-lookup"><span data-stu-id="81215-249">-ThreadOptions</span></span>

<span data-ttu-id="81215-250">Anger inställningen för tråd alternativ i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="81215-250">Specifies the thread options setting in the configuration.</span></span> <span data-ttu-id="81215-251">Den här inställningen definierar hur trådar skapas och används när ett kommando körs i sessionen.</span><span class="sxs-lookup"><span data-stu-id="81215-251">This setting defines how threads are created and used when a command is executed in the session.</span></span> <span data-ttu-id="81215-252">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="81215-252">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="81215-253">Default</span><span class="sxs-lookup"><span data-stu-id="81215-253">Default</span></span>
- <span data-ttu-id="81215-254">ReuseThread</span><span class="sxs-lookup"><span data-stu-id="81215-254">ReuseThread</span></span>
- <span data-ttu-id="81215-255">UseCurrentThread</span><span class="sxs-lookup"><span data-stu-id="81215-255">UseCurrentThread</span></span>
- <span data-ttu-id="81215-256">UseNewThread</span><span class="sxs-lookup"><span data-stu-id="81215-256">UseNewThread</span></span>

<span data-ttu-id="81215-257">Standardvärdet är **UseCurrentThread**.</span><span class="sxs-lookup"><span data-stu-id="81215-257">The default value is **UseCurrentThread**.</span></span>

<span data-ttu-id="81215-258">Mer information finns i [PSThreadOptions-uppräkning](/dotnet/api/system.management.automation.runspaces.psthreadoptions).</span><span class="sxs-lookup"><span data-stu-id="81215-258">For more information, see [PSThreadOptions Enumeration](/dotnet/api/system.management.automation.runspaces.psthreadoptions).</span></span>

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

### <span data-ttu-id="81215-259">-TransportOption</span><span class="sxs-lookup"><span data-stu-id="81215-259">-TransportOption</span></span>

<span data-ttu-id="81215-260">Anger transport alternativ för konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="81215-260">Specifies the transport options for the session configuration.</span></span> <span data-ttu-id="81215-261">Ange ett transport alternativ objekt, till exempel **WSManConfigurationOption** -objektet som `New-PSTransportOption` cmdleten returnerar.</span><span class="sxs-lookup"><span data-stu-id="81215-261">Enter a transport options object, such as the **WSManConfigurationOption** object that the `New-PSTransportOption` cmdlet returns.</span></span>

<span data-ttu-id="81215-262">Alternativen för sessioner som använder sessionen bestäms av värdena för session-alternativen och konfigurations alternativen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="81215-262">The options of sessions that use the session configuration are determined by the values of session options and the session configuration options.</span></span> <span data-ttu-id="81215-263">Om inget annat anges får alternativ som anges i sessionen, till exempel med hjälp av `New-PSSessionOption` cmdleten, företräde framför alternativ som angetts i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="81215-263">Unless specified, options set in the session, such as by using the `New-PSSessionOption` cmdlet, take precedence over options set in the session configuration.</span></span> <span data-ttu-id="81215-264">Värdena för sessionens alternativ får dock inte överskrida de maximala värden som angetts i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="81215-264">However, session option values cannot exceed maximum values set in the session configuration.</span></span>

<span data-ttu-id="81215-265">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="81215-265">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="81215-266">-UseSharedProcess</span><span class="sxs-lookup"><span data-stu-id="81215-266">-UseSharedProcess</span></span>

<span data-ttu-id="81215-267">Använd bara en process som värd för alla sessioner som startas av samma användare och Använd samma sessions konfiguration.</span><span class="sxs-lookup"><span data-stu-id="81215-267">Use only one process to host all sessions that are started by the same user and use the same session configuration.</span></span> <span data-ttu-id="81215-268">Som standard finns varje session i en egen process.</span><span class="sxs-lookup"><span data-stu-id="81215-268">By default, each session is hosted in its own process.</span></span>

<span data-ttu-id="81215-269">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="81215-269">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="81215-270">-Confirm</span><span class="sxs-lookup"><span data-stu-id="81215-270">-Confirm</span></span>

<span data-ttu-id="81215-271">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="81215-271">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="81215-272">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="81215-272">-WhatIf</span></span>

<span data-ttu-id="81215-273">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="81215-273">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="81215-274">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="81215-274">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="81215-275">-ThreadApartmentState</span><span class="sxs-lookup"><span data-stu-id="81215-275">-ThreadApartmentState</span></span>

<span data-ttu-id="81215-276">Anger Apartment-statusen för den trådad modul som ska användas.</span><span class="sxs-lookup"><span data-stu-id="81215-276">Specifies the apartment state of the threading module to be used.</span></span> <span data-ttu-id="81215-277">Godkända värden är:</span><span class="sxs-lookup"><span data-stu-id="81215-277">Acceptable values are:</span></span>

- <span data-ttu-id="81215-278">Okänt</span><span class="sxs-lookup"><span data-stu-id="81215-278">Unknown</span></span>
- <span data-ttu-id="81215-279">MTA</span><span class="sxs-lookup"><span data-stu-id="81215-279">MTA</span></span>
- <span data-ttu-id="81215-280">S</span><span class="sxs-lookup"><span data-stu-id="81215-280">STA</span></span>

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

### <span data-ttu-id="81215-281">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="81215-281">CommonParameters</span></span>

<span data-ttu-id="81215-282">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="81215-282">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="81215-283">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="81215-283">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="81215-284">INDATA</span><span class="sxs-lookup"><span data-stu-id="81215-284">INPUTS</span></span>

### <span data-ttu-id="81215-285">Inget</span><span class="sxs-lookup"><span data-stu-id="81215-285">None</span></span>

<span data-ttu-id="81215-286">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="81215-286">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="81215-287">UTDATA</span><span class="sxs-lookup"><span data-stu-id="81215-287">OUTPUTS</span></span>

### <span data-ttu-id="81215-288">Microsoft. WSMan. Management. WSManConfigLeafElement</span><span class="sxs-lookup"><span data-stu-id="81215-288">Microsoft.WSMan.Management.WSManConfigLeafElement</span></span>

## <span data-ttu-id="81215-289">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="81215-289">NOTES</span></span>

<span data-ttu-id="81215-290">Starta PowerShell med alternativet Kör som administratör för att köra denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="81215-290">To run this cmdlet, start PowerShell by using the Run as administrator option.</span></span>

<span data-ttu-id="81215-291">`Set-PSSessionConfiguration`Cmdleten ändrar inte konfigurations namnet och **WSMan** -providern stöder inte `Rename-Item` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="81215-291">The `Set-PSSessionConfiguration` cmdlet does not change the configuration name and the **WSMan** provider does not support the `Rename-Item` cmdlet.</span></span> <span data-ttu-id="81215-292">Om du vill ändra namnet på en sessions konfiguration använder du `Unregister-PSSessionConfiguration` cmdleten för att ta bort konfigurationen och använder sedan `Register-PSSessionConfiguration` cmdleten för att skapa och registrera en ny konfiguration av sessionen.</span><span class="sxs-lookup"><span data-stu-id="81215-292">To change the name of a session configuration, use the `Unregister-PSSessionConfiguration` cmdlet to delete the configuration and then use the `Register-PSSessionConfiguration` cmdlet to create and register a new session configuration.</span></span>

<span data-ttu-id="81215-293">Du kan använda `Set-PSSessionConfiguration` cmdleten för att ändra standard konfigurationerna för Microsoft. PowerShell och Microsoft. PowerShell32.</span><span class="sxs-lookup"><span data-stu-id="81215-293">You can use the `Set-PSSessionConfiguration` cmdlet to change the default Microsoft.PowerShell and Microsoft.PowerShell32 session configurations.</span></span> <span data-ttu-id="81215-294">De är inte skyddade.</span><span class="sxs-lookup"><span data-stu-id="81215-294">They are not protected.</span></span> <span data-ttu-id="81215-295">Om du vill återgå till den ursprungliga versionen av en standardsession, använder du `Unregister-PSSessionConfiguration` cmdleten för att ta bort standardsessionens konfiguration och använder sedan `Enable-PSRemoting` cmdlet: en för att återställa den.</span><span class="sxs-lookup"><span data-stu-id="81215-295">To revert to the original version of a default session configuration, use the `Unregister-PSSessionConfiguration` cmdlet to delete the default session configuration and then use the `Enable-PSRemoting` cmdlet to restore it.</span></span>

<span data-ttu-id="81215-296">Egenskaperna för ett konfigurations objekt för en session varierar beroende på vilka alternativ som har angetts för konfigurationen av sessionen och värdena för dessa alternativ.</span><span class="sxs-lookup"><span data-stu-id="81215-296">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="81215-297">Dessutom har sessionsinställningar som använder en konfigurations fil för sessionen ytterligare egenskaper.</span><span class="sxs-lookup"><span data-stu-id="81215-297">Also, session configurations that use a session configuration file have additional properties.</span></span>

<span data-ttu-id="81215-298">Du kan använda kommandona i WSMan: Drive för att ändra egenskaperna för sessionens konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="81215-298">You can use commands in the WSMan: drive to change the properties of session configurations.</span></span>
<span data-ttu-id="81215-299">Du kan dock inte använda WSMan:-enheten i PowerShell 2,0 för att ändra konfigurations egenskaper för sessionen som introduceras i PowerShell 3,0, till exempel **OutputBufferingMode**.</span><span class="sxs-lookup"><span data-stu-id="81215-299">However, you cannot use the WSMan: drive in PowerShell 2.0 to change session configuration properties that are introduced in PowerShell 3.0, such as **OutputBufferingMode**.</span></span> <span data-ttu-id="81215-300">Windows PowerShell 2,0-kommandon genererar inte ett fel, men de är inaktiva.</span><span class="sxs-lookup"><span data-stu-id="81215-300">Windows PowerShell 2.0 commands do not generate an error, but they are ineffective.</span></span> <span data-ttu-id="81215-301">Om du vill ändra de egenskaper som introduceras i PowerShell 3,0 använder du kommandot WSMan: Drive i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="81215-301">To change properties introduced in PowerShell 3.0, use the WSMan: drive in PowerShell 3.0.</span></span>

## <span data-ttu-id="81215-302">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="81215-302">RELATED LINKS</span></span>

[<span data-ttu-id="81215-303">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="81215-303">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="81215-304">Aktivera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="81215-304">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="81215-305">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="81215-305">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="81215-306">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="81215-306">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="81215-307">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="81215-307">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="81215-308">New-PSTransportOption</span><span class="sxs-lookup"><span data-stu-id="81215-308">New-PSTransportOption</span></span>](New-PSTransportOption.md)

[<span data-ttu-id="81215-309">Registrera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="81215-309">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="81215-310">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="81215-310">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="81215-311">Avregistrera-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="81215-311">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="81215-312">WSMan-Provider</span><span class="sxs-lookup"><span data-stu-id="81215-312">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="81215-313">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="81215-313">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="81215-314">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="81215-314">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
