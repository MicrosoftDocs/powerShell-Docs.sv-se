---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/register-pssessionconfiguration?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-PSSessionConfiguration
ms.openlocfilehash: ce52714d93cfce55ca36f89f16e37092b35c6b24
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267429"
---
# <span data-ttu-id="bb5a7-103">Register-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="bb5a7-103">Register-PSSessionConfiguration</span></span>

## <span data-ttu-id="bb5a7-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="bb5a7-104">SYNOPSIS</span></span>
<span data-ttu-id="bb5a7-105">Skapar och registrerar en ny konfiguration av sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-105">Creates and registers a new session configuration.</span></span>

## <span data-ttu-id="bb5a7-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bb5a7-106">SYNTAX</span></span>

### <span data-ttu-id="bb5a7-107">NameParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="bb5a7-107">NameParameterSet (Default)</span></span>

```
Register-PSSessionConfiguration [-ProcessorArchitecture <String>] [-SessionType <PSSessionType>]
 [-Name] <String> [-ApplicationBase <String>] [-RunAsCredential <PSCredential>]
 [-ThreadOptions <PSThreadOptions>] [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess]
 [-StartupScript <String>] [-MaximumReceivedDataSizePerCommandMB <Double>]
 [-MaximumReceivedObjectSizeMB <Double>] [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI]
 [-Force] [-NoServiceRestart] [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>]
 [-TransportOption <PSTransportOption>] [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="bb5a7-108">AssemblyNameParameterSet</span><span class="sxs-lookup"><span data-stu-id="bb5a7-108">AssemblyNameParameterSet</span></span>

```
Register-PSSessionConfiguration [-ProcessorArchitecture <String>] [-Name] <String> [-AssemblyName] <String>
 [-ApplicationBase <String>] [-ConfigurationTypeName] <String> [-RunAsCredential <PSCredential>]
 [-ThreadOptions <PSThreadOptions>] [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess]
 [-StartupScript <String>] [-MaximumReceivedDataSizePerCommandMB <Double>]
 [-MaximumReceivedObjectSizeMB <Double>] [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI]
 [-Force] [-NoServiceRestart] [-PSVersion <Version>] [-SessionTypeOption <PSSessionTypeOption>]
 [-TransportOption <PSTransportOption>] [-ModulesToImport <Object[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="bb5a7-109">SessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="bb5a7-109">SessionConfigurationFile</span></span>

```
Register-PSSessionConfiguration [-ProcessorArchitecture <String>] [-Name] <String>
 [-RunAsCredential <PSCredential>] [-ThreadOptions <PSThreadOptions>]
 [-AccessMode <PSSessionConfigurationAccessMode>] [-UseSharedProcess] [-StartupScript <String>]
 [-MaximumReceivedDataSizePerCommandMB <Double>] [-MaximumReceivedObjectSizeMB <Double>]
 [-SecurityDescriptorSddl <String>] [-ShowSecurityDescriptorUI] [-Force] [-NoServiceRestart]
 [-TransportOption <PSTransportOption>] -Path <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="bb5a7-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="bb5a7-110">DESCRIPTION</span></span>

<span data-ttu-id="bb5a7-111">`Register-PSSessionConfiguration`Cmdleten skapar och registrerar en ny sessionshantering på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-111">The `Register-PSSessionConfiguration` cmdlet creates and registers a new session configuration on the local computer.</span></span> <span data-ttu-id="bb5a7-112">Det här är en avancerad cmdlet som du kan använda för att skapa anpassade sessioner för fjärran vändare.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-112">This is an advanced cmdlet that you can use to create custom sessions for remote users.</span></span>

<span data-ttu-id="bb5a7-113">Varje PowerShell-session ( **PSSession** ) använder en sessionshantering, även kallad en slut punkt.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-113">Every PowerShell session ( **PSSession** ) uses a session configuration, also known as an endpoint.</span></span>
<span data-ttu-id="bb5a7-114">När användarna skapar en-session som ansluter till datorn kan de välja en sessionsnyckel eller använda den standardsessions-konfiguration som registreras när du aktiverar PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-114">When users create a session that connects to the computer, they can select a session configuration or use the default session configuration that is registered when you enable PowerShell remoting.</span></span>
<span data-ttu-id="bb5a7-115">Användare kan också ange variabeln $PSSessionConfigurationName, som anger en standard konfiguration för fjärrsessioner som skapas i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-115">Users can also set the $PSSessionConfigurationName preference variable, which specifies a default configuration for remote sessions created in the current session.</span></span>

<span data-ttu-id="bb5a7-116">Konfigurationen av sessionen definierar miljön för fjärrsessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-116">The session configuration defines the environment for the remote session.</span></span> <span data-ttu-id="bb5a7-117">Konfigurationen kan avgöra vilka kommandon och språk element som är tillgängliga i sessionen, och det kan innehålla inställningar som skyddar datorn, till exempel sådana som begränsar mängden data som sessionen kan ta emot via fjärr anslutning i ett enda objekt eller kommando.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-117">The configuration can determine which commands and language elements are available in the session, and it can include settings that protect the computer, such as those that limit the amount of data that the session can receive remotely in a single object or command.</span></span> <span data-ttu-id="bb5a7-118">Säkerhets beskrivningen för konfigurationen av sessionen avgör vilka användare som har behörighet att använda sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-118">The security descriptor of the session configuration determines which users have permission to use the session configuration.</span></span>

<span data-ttu-id="bb5a7-119">Du kan definiera komponenterna i konfigurationen genom att använda en sammansättning som implementerar en ny konfigurations klass och genom att använda ett skript som körs i sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-119">You can define the elements of configuration by using an assembly that implements a new configuration class and by using a script that runs in the session.</span></span> <span data-ttu-id="bb5a7-120">Från och med PowerShell 3,0 kan du också använda en konfigurations fil för sessionen för att definiera konfigurationen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-120">Beginning in PowerShell 3.0, you can also use a session configuration file to define the session configuration.</span></span>

<span data-ttu-id="bb5a7-121">Information om sessionsdata finns [about_Session_Configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="bb5a7-121">For information about session configurations, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>
<span data-ttu-id="bb5a7-122">Information om konfigurationsfiler för sessioner finns [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span><span class="sxs-lookup"><span data-stu-id="bb5a7-122">For information about session configuration files, see [about_Session_Configuration_Files](About/about_Session_Configuration_Files.md).</span></span>

## <span data-ttu-id="bb5a7-123">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="bb5a7-123">EXAMPLES</span></span>

### <span data-ttu-id="bb5a7-124">Exempel 1: registrera en konfiguration för NewShell-sessionen</span><span class="sxs-lookup"><span data-stu-id="bb5a7-124">Example 1: Register a NewShell session configuration</span></span>

<span data-ttu-id="bb5a7-125">I det här exemplet registrerar vi konfigurationen för **NewShell** -sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-125">In this example, we register the **NewShell** session configuration.</span></span> <span data-ttu-id="bb5a7-126">Parametrarna **AssemblyName** och **ApplicationBase** anger platsen för **MyShell.dll** -filen, som anger de cmdlets och providers i konfigurationen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-126">The **AssemblyName** and **ApplicationBase** parameters specify the location of the **MyShell.dll** file, which specifies the cmdlets and providers in the session configuration.</span></span> <span data-ttu-id="bb5a7-127">Parametern **ConfigurationTypeName** anger vilken konfigurations klass som ska användas från sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-127">The **ConfigurationTypeName** parameter specifies the configuration class to use from the assembly.</span></span>

```powershell
$sessionConfiguration = @{
    Name='NewShell'
    ApplicationBase='c:\MyShells\'
    AssemblyName='MyShell.dll'
    ConfigurationTypeName='MyClass'
}
Register-PSSessionConfiguration @sessionConfiguration
```

<span data-ttu-id="bb5a7-128">Om du vill använda den här konfigurationen skriver du `New-PSSession -ConfigurationName newshell` .</span><span class="sxs-lookup"><span data-stu-id="bb5a7-128">To use this configuration, type `New-PSSession -ConfigurationName newshell`.</span></span>

### <span data-ttu-id="bb5a7-129">Exempel 2: registrera en konfiguration för MaintenanceShell-sessioner</span><span class="sxs-lookup"><span data-stu-id="bb5a7-129">Example 2: Register a MaintenanceShell session configuration</span></span>

<span data-ttu-id="bb5a7-130">Det här exemplet registrerar konfigurationen för **MaintenanceShell** på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-130">This example registers the **MaintenanceShell** session configuration on the local computer.</span></span> <span data-ttu-id="bb5a7-131">Parametern **StartupScript** anger `Maintenance.ps1` skriptet.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-131">The **StartupScript** parameter specifies the `Maintenance.ps1` script.</span></span>

```powershell
Register-PSSessionConfiguration -Name MaintenanceShell -StartupScript C:\ps-test\Maintenance.ps1
```

<span data-ttu-id="bb5a7-132">När en användare använder ett `New-PSSession` kommando och väljer **MaintenanceShell** -konfigurationen `Maintenance.ps1` körs skriptet i den nya sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-132">When a user uses a `New-PSSession` command and selects the **MaintenanceShell** configuration, the `Maintenance.ps1` script runs in the new session.</span></span> <span data-ttu-id="bb5a7-133">Skriptet kan konfigurera sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-133">The script can configure the session.</span></span> <span data-ttu-id="bb5a7-134">Detta inkluderar att importera moduler och att ställa in körnings principen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-134">This includes importing modules and setting the execution policy for the session.</span></span> <span data-ttu-id="bb5a7-135">Om skriptet genererar eventuella fel, inklusive icke-avslutande fel, `New-PSSession` Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-135">If the script generates any errors, including non-terminating errors, the `New-PSSession` command fails.</span></span>

### <span data-ttu-id="bb5a7-136">Exempel 3: registrera en konfiguration av sessionen</span><span class="sxs-lookup"><span data-stu-id="bb5a7-136">Example 3: Register a session configuration</span></span>

<span data-ttu-id="bb5a7-137">Det här exemplet registrerar konfigurationen för **AdminShell** -sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-137">This example registers the **AdminShell** session configuration.</span></span>

<span data-ttu-id="bb5a7-138">`$sessionParams`Variabeln är en hash som innehåller alla parameter värden.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-138">The `$sessionParams` variable is a hashtable containing all the parameter values.</span></span> <span data-ttu-id="bb5a7-139">Denna hash skickas till cmdleten med PowerShell-ihopbuntning.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-139">This hashtable is passed to the cmdlet using PowerShell splatting.</span></span> <span data-ttu-id="bb5a7-140">`Register-PSSessionConfiguration`Kommandot använder parametern **SecurityDescritorSDDL** för att ange SDDL i värdet för `$sddl` variabeln och parametern **MaximumReceivedObjectSizeMB** för att öka storleks gränsen för objekt.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-140">The `Register-PSSessionConfiguration` command uses the **SecurityDescritorSDDL** parameter to specify the SDDL in the value of the `$sddl` variable and the **MaximumReceivedObjectSizeMB** parameter to increase the object size limit.</span></span> <span data-ttu-id="bb5a7-141">Den använder också parametern **StartupScript** för att ange ett skript som konfigurerar sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-141">It also uses the **StartupScript** parameter to specify a script that configures the session.</span></span>

```powershell
$sddl = "O:NSG:BAD:P(A;;GA;;;BA)S:P(AU;FA;GA;;;WD)(AU;FA;SA;GWGX;;WD)"
$sessionParams = @{
    Name="AdminShell"
    SecurityDescriptorSDDL=$sddl
    MaximumReceivedObjectSizeMB=20
    StartupScript="C:\scripts\AdminShell.ps1"
}
Register-PSSessionConfiguration @sessionParams
```

### <span data-ttu-id="bb5a7-142">Exempel 4: returnera ett konfigurations container element</span><span class="sxs-lookup"><span data-stu-id="bb5a7-142">Example 4: Return a configuration container element</span></span>

<span data-ttu-id="bb5a7-143">Det här exemplet visar hur du registrerar **MaintenanceShell** -konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-143">This example shows how to register the **MaintenanceShell** configuration.</span></span>
<span data-ttu-id="bb5a7-144">`Register-PSSessionConfiguration` Returnerar ett **WSManConfigContainerElement** -objekt som lagras i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-144">`Register-PSSessionConfiguration` returns a **WSManConfigContainerElement** object stored in the `$s` variable.</span></span> <span data-ttu-id="bb5a7-145">`Format-List` visar alla egenskaper för det returnerade objektet.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-145">`Format-List` displays all the properties of the returned object.</span></span> <span data-ttu-id="bb5a7-146">Egenskapen **PSPath** visar att objektet lagras i en katalog för WSMan: Drive.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-146">The **PSPath** property shows that the object is stored in a directory of the WSMan: drive.</span></span> <span data-ttu-id="bb5a7-147">`Get-ChildItem` (alias `dir` ) visar objekten i `WSMan:\LocalHost\PlugIn` sökvägen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-147">`Get-ChildItem` (alias `dir`) displays the items in the `WSMan:\LocalHost\PlugIn` path.</span></span> <span data-ttu-id="bb5a7-148">Detta omfattar den nya **MaintenanceShell** -konfigurationen och de två standardkonfigurationer som ingår i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-148">These include the new **MaintenanceShell** configuration and the two default configurations that come with PowerShell.</span></span>

```powershell
$s = Register-PSSessionConfiguration -Name MaintenanceShell -StartupScript C:\ps-test\Maintenance.ps1
$s | Format-List -Property *
dir WSMan:\LocalHost\Plugin
```

```Output
PSPath            : Microsoft.WSMan.Management\WSMan::localhost\Plugin\MaintenanceShell
PSParentPath      : Microsoft.WSMan.Management\WSMan::localhost\Plugin
PSChildName       : MaintenanceShell
PSDrive           : WSMan
PSProvider        : Microsoft.WSMan.Management\WSMan
PSIsContainer     : True
Keys              : {Name=MaintenanceShell}
Name              : MaintenanceShell
TypeNameOfElement : Container

Name                      Type                 Keys
----                      ----                 ----
MaintenanceShell          Container            {Name=MaintenanceShell}
microsoft.powershell      Container            {Name=microsoft.powershell}
microsoft.powershell32    Container            {Name=microsoft.powershell32}
```

### <span data-ttu-id="bb5a7-149">Exempel 5: registrera en sessions konfiguration med ett start skript</span><span class="sxs-lookup"><span data-stu-id="bb5a7-149">Example 5: Register a session configuration with a startup script</span></span>

<span data-ttu-id="bb5a7-150">I det här exemplet skapar och registrerar du konfigurationen för **WithProfile** -sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-150">In this example we create and register the **WithProfile** session configuration.</span></span> <span data-ttu-id="bb5a7-151">Parametern **StartupScript** styr PowerShell för att köra det angivna skriptet för alla sessioner som använder sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-151">The **StartupScript** parameter directs PowerShell to run the specified script for any session that uses the session configuration.</span></span>

```powershell
Register-PSSessionConfiguration -Name WithProfile -StartupScript Add-Profile.ps1
```

<span data-ttu-id="bb5a7-152">Skriptet innehåller ett enda kommando som använder punkt-källa för att köra användarens **CurrentUserAllHosts** -profil i det aktuella omfånget för sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-152">The script contains a single command that uses dot sourcing to run the user's **CurrentUserAllHosts** profile in the current scope of the session.</span></span>

<span data-ttu-id="bb5a7-153">Mer information om profiler finns [about_Profiles](./About/about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="bb5a7-153">For more information about profiles, see [about_Profiles](./About/about_Profiles.md).</span></span> <span data-ttu-id="bb5a7-154">Mer information om punkt källor finns [about_Scopes](./About/about_Scopes.md).</span><span class="sxs-lookup"><span data-stu-id="bb5a7-154">For more information about dot sourcing, see [about_Scopes](./About/about_Scopes.md).</span></span>

## <span data-ttu-id="bb5a7-155">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="bb5a7-155">PARAMETERS</span></span>

### <span data-ttu-id="bb5a7-156">-AccessMode</span><span class="sxs-lookup"><span data-stu-id="bb5a7-156">-AccessMode</span></span>

<span data-ttu-id="bb5a7-157">Aktiverar och inaktiverar konfigurationen av sessionen och avgör om den kan användas för fjärranslutna eller lokala sessioner på datorn.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-157">Enables and disables the session configuration and determines whether it can be used for remote or local sessions on the computer.</span></span> <span data-ttu-id="bb5a7-158">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="bb5a7-158">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="bb5a7-159">Inaktiverat</span><span class="sxs-lookup"><span data-stu-id="bb5a7-159">Disabled.</span></span> <span data-ttu-id="bb5a7-160">Inaktiverar konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-160">Disables the session configuration.</span></span> <span data-ttu-id="bb5a7-161">Den kan inte användas för fjärran sluten eller lokal åtkomst till datorn.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-161">It cannot be used for remote or local access to the computer.</span></span>
- <span data-ttu-id="bb5a7-162">Inställningar.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-162">Local.</span></span> <span data-ttu-id="bb5a7-163">Tillåter användare av den lokala datorn att använda-sessionen för att skapa en lokal loopback-session på samma dator, men nekar åtkomst till fjärran vändare.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-163">Allows users of the local computer to use the session configuration to create a local loopback session on the same computer, but denies access to remote users.</span></span>
- <span data-ttu-id="bb5a7-164">Fjärrserveradministrationsverktyg.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-164">Remote.</span></span> <span data-ttu-id="bb5a7-165">Tillåter lokala och fjärranslutna användare att använda sessionen för att skapa sessioner och köra kommandon på den här datorn.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-165">Allows local and remote users to use the session configuration to create sessions and run commands on this computer.</span></span>

<span data-ttu-id="bb5a7-166">Standardvärdet är fjärran sluten.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-166">The default value is Remote.</span></span>

<span data-ttu-id="bb5a7-167">Andra cmdletar kan åsidosätta värdet för den här parametern senare.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-167">Other cmdlets can override the value of this parameter later.</span></span> <span data-ttu-id="bb5a7-168">Till exempel `Enable-PSRemoting` tillåter cmdleten fjärråtkomst till alla sessioner, `Enable-PSSessionConfiguration` cmdlet: en aktiverar sessionsbaserade och `Disable-PSRemoting` cmdleten förhindrar fjärråtkomst till alla konfigurationer i sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-168">For example, the `Enable-PSRemoting` cmdlet allows for remote access to all session configurations, the `Enable-PSSessionConfiguration` cmdlet enables session configurations, and the `Disable-PSRemoting` cmdlet prevents remote access to all session configurations.</span></span>

<span data-ttu-id="bb5a7-169">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-169">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="bb5a7-170">– ApplicationBase</span><span class="sxs-lookup"><span data-stu-id="bb5a7-170">-ApplicationBase</span></span>

<span data-ttu-id="bb5a7-171">Anger sökvägen till sammansättnings filen ( \* . dll) som anges i värdet för parametern **AssemblyName** .</span><span class="sxs-lookup"><span data-stu-id="bb5a7-171">Specifies the path of the assembly file (\*.dll) that is specified in the value of the **AssemblyName** parameter.</span></span> <span data-ttu-id="bb5a7-172">Använd den här parametern när värdet för parametern **AssemblyName** inte innehåller någon sökväg.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-172">Use this parameter when the value of the **AssemblyName** parameter does not include a path.</span></span> <span data-ttu-id="bb5a7-173">Standardvärdet är den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-173">The default is the current directory.</span></span>

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

### <span data-ttu-id="bb5a7-174">-AssemblyName</span><span class="sxs-lookup"><span data-stu-id="bb5a7-174">-AssemblyName</span></span>

<span data-ttu-id="bb5a7-175">Anger namnet på en sammansättnings fil ( \* . dll) där konfigurations typen definieras.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-175">Specifies the name of an assembly file (\*.dll) in which the configuration type is defined.</span></span> <span data-ttu-id="bb5a7-176">Du kan ange sökvägen till. dll i den här parametern eller i värdet för parametern **ApplicationBase** .</span><span class="sxs-lookup"><span data-stu-id="bb5a7-176">You can specify the path of the .dll in this parameter or in the value of the **ApplicationBase** parameter.</span></span>

<span data-ttu-id="bb5a7-177">Den här parametern krävs när du anger parametern **ConfigurationTypeName** .</span><span class="sxs-lookup"><span data-stu-id="bb5a7-177">This parameter is required when you specify the **ConfigurationTypeName** parameter.</span></span>

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

### <span data-ttu-id="bb5a7-178">-ConfigurationTypeName</span><span class="sxs-lookup"><span data-stu-id="bb5a7-178">-ConfigurationTypeName</span></span>

<span data-ttu-id="bb5a7-179">Anger det fullständigt kvalificerade namnet på den Microsoft .NET Framework-typ som används för den här konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-179">Specifies the fully qualified name of the Microsoft .NET Framework type that is used for this configuration.</span></span> <span data-ttu-id="bb5a7-180">Den typ som du anger måste implementera klassen **system. Management. Automation. Remoting. PSSessionConfiguration** .</span><span class="sxs-lookup"><span data-stu-id="bb5a7-180">The type that you specify must implement the **System.Management.Automation.Remoting.PSSessionConfiguration** class.</span></span>

<span data-ttu-id="bb5a7-181">Om du vill ange sammansättnings filen ( \* . dll) som implementerar konfigurations typen anger du parametrarna **AssemblyName** och **ApplicationBase** .</span><span class="sxs-lookup"><span data-stu-id="bb5a7-181">To specify the assembly file (\*.dll) that implements the configuration type, specify the **AssemblyName** and **ApplicationBase** parameters.</span></span>

<span data-ttu-id="bb5a7-182">Genom att skapa en typ kan du kontrol lera fler aspekter av konfigurationen av sessionen, till exempel exponera eller dölja vissa parametrar av cmdletar, eller ange data storlek och storleks gränser för objekt som användarna inte kan åsidosätta.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-182">Creating a type lets you control more aspects of the session configuration, such as exposing or hiding certain parameters of cmdlets, or setting data size and object size limits that users cannot override.</span></span>

<span data-ttu-id="bb5a7-183">Om du utelämnar den här parametern används **DefaultRemotePowerShellConfiguration** -klassen för konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-183">If you omit this parameter, the **DefaultRemotePowerShellConfiguration** class is used for the session configuration.</span></span>

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

### <span data-ttu-id="bb5a7-184">-Force</span><span class="sxs-lookup"><span data-stu-id="bb5a7-184">-Force</span></span>

<span data-ttu-id="bb5a7-185">Ignorerar alla användarens prompter och startar om **WinRM** -tjänsten utan att fråga.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-185">Suppresses all user prompts and restarts the **WinRM** service without prompting.</span></span> <span data-ttu-id="bb5a7-186">Att starta om tjänsten gör att konfigurations ändringen träder i kraft.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-186">Restarting the service makes the configuration change effective.</span></span>

<span data-ttu-id="bb5a7-187">Om du vill förhindra en omstart och ignorera omstarts meddelandet anger du parametern **NoServiceRestart** .</span><span class="sxs-lookup"><span data-stu-id="bb5a7-187">To prevent a restart and suppress the restart prompt, specify the **NoServiceRestart** parameter.</span></span>

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

### <span data-ttu-id="bb5a7-188">-MaximumReceivedDataSizePerCommandMB</span><span class="sxs-lookup"><span data-stu-id="bb5a7-188">-MaximumReceivedDataSizePerCommandMB</span></span>

<span data-ttu-id="bb5a7-189">Anger en gräns för mängden data som kan skickas till den här datorn i ett enda fjärran slutet kommando.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-189">Specifies a limit for the amount of data that can be sent to this computer in any single remote command.</span></span> <span data-ttu-id="bb5a7-190">Ange data storleken i megabyte (MB).</span><span class="sxs-lookup"><span data-stu-id="bb5a7-190">Enter the data size in megabytes (MB).</span></span> <span data-ttu-id="bb5a7-191">Standardvärdet är 50 MB.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-191">The default is 50 MB.</span></span>

<span data-ttu-id="bb5a7-192">Om en data storleks gräns definieras i den konfigurations typ som anges i parametern **ConfigurationTypeName** , används gränsen i konfigurations typen och värdet för den här parametern ignoreras.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-192">If a data size limit is defined in the configuration type that is specified in the **ConfigurationTypeName** parameter, the limit in the configuration type is used and the value of this parameter is ignored.</span></span>

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

### <span data-ttu-id="bb5a7-193">-MaximumReceivedObjectSizeMB</span><span class="sxs-lookup"><span data-stu-id="bb5a7-193">-MaximumReceivedObjectSizeMB</span></span>

<span data-ttu-id="bb5a7-194">Anger en gräns för mängden data som kan skickas till den här datorn i ett enda objekt.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-194">Specifies a limit for the amount of data that can be sent to this computer in any single object.</span></span>
<span data-ttu-id="bb5a7-195">Ange data storleken i megabyte.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-195">Enter the data size in megabytes.</span></span> <span data-ttu-id="bb5a7-196">Standardvärdet är 10 MB.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-196">The default is 10 MB.</span></span>

<span data-ttu-id="bb5a7-197">Om en gräns för objekt storlek definieras i den konfigurations typ som anges i parametern **ConfigurationTypeName** , används gränsen i konfigurations typen och värdet för den här parametern ignoreras.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-197">If an object size limit is defined in the configuration type that is specified in the **ConfigurationTypeName** parameter, the limit in the configuration type is used and the value of this parameter is ignored.</span></span>

```yaml
Type: System.Nullable`1[System.Double]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 10
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb5a7-198">-ModulesToImport</span><span class="sxs-lookup"><span data-stu-id="bb5a7-198">-ModulesToImport</span></span>

<span data-ttu-id="bb5a7-199">Anger de moduler som importeras automatiskt till sessioner som använder sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-199">Specifies the modules that are automatically imported into sessions that use the session configuration.</span></span>

<span data-ttu-id="bb5a7-200">Som standard importeras endast **Microsoft. PowerShell. Core** till sessioner.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-200">By default, only **Microsoft.PowerShell.Core** is imported into sessions.</span></span> <span data-ttu-id="bb5a7-201">Om inte cmdletarna är uteslutna kan du använda `Import-Module` för att lägga till moduler i sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-201">Unless the cmdlets are excluded, you can use `Import-Module` to add modules to the session.</span></span>

<span data-ttu-id="bb5a7-202">Modulerna som anges i det här parametervärdet importeras i tillägg till moduler som anges av parametern **SessionType** och de som anges i **ModulesToImport** -nyckeln i sessionens konfigurations fil ( `New-PSSessionConfigurationFile` ).</span><span class="sxs-lookup"><span data-stu-id="bb5a7-202">The modules specified in this parameter value are imported in additions to modules that are specified by the **SessionType** parameter and those listed in the **ModulesToImport** key in the session configuration file (`New-PSSessionConfigurationFile`).</span></span> <span data-ttu-id="bb5a7-203">Inställningarna i konfigurations filen för sessionen kan dock dölja de kommandon som exporteras av moduler eller hindra användarna från att använda dem.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-203">However, settings in the session configuration file can hide the commands exported by modules or prevent users from using them.</span></span>

<span data-ttu-id="bb5a7-204">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-204">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="bb5a7-205">-Name</span><span class="sxs-lookup"><span data-stu-id="bb5a7-205">-Name</span></span>

<span data-ttu-id="bb5a7-206">Anger ett namn för konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-206">Specifies a name for the session configuration.</span></span> <span data-ttu-id="bb5a7-207">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-207">This parameter is required.</span></span>

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

### <span data-ttu-id="bb5a7-208">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="bb5a7-208">-NoServiceRestart</span></span>

<span data-ttu-id="bb5a7-209">Startar inte om **WinRM** -tjänsten och inaktiverar uppmaningen att starta om tjänsten.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-209">Does not restart the **WinRM** service, and suppresses the prompt to restart the service.</span></span>

<span data-ttu-id="bb5a7-210">När du kör ett `Register-PSSessionConfiguration` kommando uppmanas du som standard att starta om **WinRM** -tjänsten för att göra den nya konfigurationen effektiv.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-210">By default, when you run a `Register-PSSessionConfiguration` command, you are prompted to restart the **WinRM** service to make the new session configuration effective.</span></span> <span data-ttu-id="bb5a7-211">Den nya konfigurationen är inte giltig förrän **WinRM** -tjänsten har startats om.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-211">Until the **WinRM** service is restarted, the new session configuration is not effective.</span></span>

<span data-ttu-id="bb5a7-212">Om du vill starta om **WinRM** -tjänsten utan att begära det anger du parametern **Force** .</span><span class="sxs-lookup"><span data-stu-id="bb5a7-212">To restart the **WinRM** service without prompting, specify the **Force** parameter.</span></span> <span data-ttu-id="bb5a7-213">Om du vill starta om **WinRM** -tjänsten manuellt använder du `Restart-Service` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-213">To restart the **WinRM** service manually, use the `Restart-Service` cmdlet.</span></span>

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

### <span data-ttu-id="bb5a7-214">-Path</span><span class="sxs-lookup"><span data-stu-id="bb5a7-214">-Path</span></span>

<span data-ttu-id="bb5a7-215">Anger sökvägen och fil namnet för en sessions konfigurations fil (. PSSC), till exempel en som skapats av `New-PSSessionConfigurationFile` .</span><span class="sxs-lookup"><span data-stu-id="bb5a7-215">Specifies the path and filename of a session configuration file (.pssc), such as one created by `New-PSSessionConfigurationFile`.</span></span> <span data-ttu-id="bb5a7-216">Om du utelämnar sökvägen är standardvärdet den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-216">If you omit the path, the default is the current directory.</span></span>

<span data-ttu-id="bb5a7-217">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-217">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="bb5a7-218">-ProcessorArchitecture</span><span class="sxs-lookup"><span data-stu-id="bb5a7-218">-ProcessorArchitecture</span></span>

<span data-ttu-id="bb5a7-219">Fastställer om en 32-eller 64-bitars version av PowerShell-processen startas i sessioner som använder den här konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-219">Determines whether a 32-bit or 64-bit version of the PowerShell process is started in sessions that use this session configuration.</span></span> <span data-ttu-id="bb5a7-220">De acceptabla värdena för den här parametern är: x86 (32-bitars) och AMD64 (64-bit).</span><span class="sxs-lookup"><span data-stu-id="bb5a7-220">The acceptable values for this parameter are: x86 (32-bit) and AMD64 (64-bit).</span></span> <span data-ttu-id="bb5a7-221">Standardvärdet bestäms av processor arkitekturen på den dator som är värd för konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-221">The default value is determined by the processor architecture of the computer that hosts the session configuration.</span></span>

<span data-ttu-id="bb5a7-222">Du kan använda den här parametern för att skapa en 32-bitars session på en 64-bitars dator.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-222">You can use this parameter to create a 32-bit session on a 64-bit computer.</span></span> <span data-ttu-id="bb5a7-223">Försök att skapa en 64-bitars process på en 32-bitars dator Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-223">Attempts to create a 64-bit process on a 32-bit computer fail.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PA
Accepted values: x86, amd64

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb5a7-224">– PSVersion</span><span class="sxs-lookup"><span data-stu-id="bb5a7-224">-PSVersion</span></span>

<span data-ttu-id="bb5a7-225">Anger versionen för PowerShell i sessioner som använder den här sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-225">Specifies the version of PowerShell in sessions that use this session configuration.</span></span>

<span data-ttu-id="bb5a7-226">Värdet för den här parametern prioriteras över värdet för **PowerShellVersion** -nyckeln i sessionens konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-226">The value of this parameter takes precedence over the value of the **PowerShellVersion** key in the session configuration file.</span></span>

<span data-ttu-id="bb5a7-227">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-227">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="bb5a7-228">-RunAsCredential</span><span class="sxs-lookup"><span data-stu-id="bb5a7-228">-RunAsCredential</span></span>

<span data-ttu-id="bb5a7-229">Anger autentiseringsuppgifter för kommandon i sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-229">Specifies credentials for commands in the session.</span></span> <span data-ttu-id="bb5a7-230">Som standard körs kommandona med behörigheterna för den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-230">By default, commands run with the permissions of the current user.</span></span>

<span data-ttu-id="bb5a7-231">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-231">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="bb5a7-232">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="bb5a7-232">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="bb5a7-233">Anger en SDDL-sträng (Security Descriptor Definition Language) för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-233">Specifies a Security Descriptor Definition Language (SDDL) string for the configuration.</span></span>

<span data-ttu-id="bb5a7-234">Den här strängen avgör vilka behörigheter som krävs för att använda den nya konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-234">This string determines the permissions that are required to use the new session configuration.</span></span> <span data-ttu-id="bb5a7-235">Om du vill använda en sessionshantering i en session måste användarna ha minst körnings behörighet (Invoke) för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-235">To use a session configuration in a session, users must have at least Execute (Invoke) permission for the configuration.</span></span>

<span data-ttu-id="bb5a7-236">Om säkerhets beskrivningen är komplex kan du överväga att använda parametern **ShowSecurityDescriptorUI** i stället för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-236">If the security descriptor is complex, consider using the **ShowSecurityDescriptorUI** parameter instead of this parameter.</span></span> <span data-ttu-id="bb5a7-237">Du kan inte använda båda parametrarna i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-237">You cannot use both parameters in the same command.</span></span>

<span data-ttu-id="bb5a7-238">Om du utelämnar den här parametern används rot-SDDL för **WinRM** -tjänsten för den här konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-238">If you omit this parameter, the root SDDL for the **WinRM** service is used for this configuration.</span></span>
<span data-ttu-id="bb5a7-239">Om du vill visa eller ändra rot-SDDL använder du WSMan-providern.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-239">To view or change the root SDDL, use the WSMan provider.</span></span> <span data-ttu-id="bb5a7-240">Till exempel `Get-Item wsman:\localhost\service\rootSDDL`.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-240">For example `Get-Item wsman:\localhost\service\rootSDDL`.</span></span> <span data-ttu-id="bb5a7-241">Om du vill ha mer information om WSMan-providern skriver du `Get-Help wsman` .</span><span class="sxs-lookup"><span data-stu-id="bb5a7-241">For more information about the WSMan provider, type `Get-Help wsman`.</span></span>

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

### <span data-ttu-id="bb5a7-242">-SessionType</span><span class="sxs-lookup"><span data-stu-id="bb5a7-242">-SessionType</span></span>

<span data-ttu-id="bb5a7-243">Anger vilken typ av session som skapas med hjälp av konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-243">Specifies the type of session that is created by using the session configuration.</span></span> <span data-ttu-id="bb5a7-244">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="bb5a7-244">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="bb5a7-245">Saknas.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-245">Empty.</span></span> <span data-ttu-id="bb5a7-246">Inga moduler läggs till i sessionen som standard.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-246">No modules are added to session by default.</span></span> <span data-ttu-id="bb5a7-247">Använd parametrarna för denna cmdlet för att lägga till moduler, funktioner, skript och andra funktioner i sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-247">Use the parameters of this cmdlet to add modules, functions, scripts, and other features to the session.</span></span>
- <span data-ttu-id="bb5a7-248">Standard.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-248">Default.</span></span> <span data-ttu-id="bb5a7-249">Lägger till Microsoft. PowerShell. core i sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-249">Adds Microsoft.PowerShell.Core to the session.</span></span> <span data-ttu-id="bb5a7-250">Den här modulen innehåller den `Import-Module` cmdlet som användare kan använda för att importera andra moduler såvida du inte uttryckligen förhindrar cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-250">This module includes the `Import-Module` cmdlet that users can use to import other modules unless you explicitly prohibit the cmdlet.</span></span>
- <span data-ttu-id="bb5a7-251">RestrictedRemoteServer.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-251">RestrictedRemoteServer.</span></span> <span data-ttu-id="bb5a7-252">Innehåller endast följande cmdlet:,,,,, `Exit-PSSession` `Get-Command` `Get-FormatData` `Get-Help` `Measure-Object` `Out-Default` och `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="bb5a7-252">Includes only the following cmdlets: `Exit-PSSession`, `Get-Command`, `Get-FormatData`, `Get-Help`, `Measure-Object`, `Out-Default`, and `Select-Object`.</span></span> <span data-ttu-id="bb5a7-253">Använd ett skript eller en sammansättning eller nycklar i konfigurations filen för sessionen för att lägga till moduler, funktioner, skript och andra funktioner i sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-253">Use a script or assembly, or the keys in the session configuration file, to add modules, functions, scripts, and other features to the session.</span></span>

<span data-ttu-id="bb5a7-254">Standardvärdet är default.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-254">The default value is Default.</span></span>

<span data-ttu-id="bb5a7-255">Värdet för den här parametern prioriteras över värdet för **SessionType** -nyckeln i sessionens konfigurations fil.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-255">The value of this parameter takes precedence over the value of the **SessionType** key in the session configuration file.</span></span>

<span data-ttu-id="bb5a7-256">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-256">This parameter was introduced in PowerShell 3.0.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSessionType
Parameter Sets: NameParameterSet
Aliases:
Accepted values: DefaultRemoteShell, Workflow

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="bb5a7-257">-SessionTypeOption</span><span class="sxs-lookup"><span data-stu-id="bb5a7-257">-SessionTypeOption</span></span>

<span data-ttu-id="bb5a7-258">Anger typspecifika alternativ för konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-258">Specifies type-specific options for the session configuration.</span></span> <span data-ttu-id="bb5a7-259">Ange ett alternativ för sessionsläge, till exempel **PSWorkflowExecutionOption** -objektet som `New-PSWorkflowExecutionOption` cmdleten returnerar.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-259">Enter a session type options object, such as the **PSWorkflowExecutionOption** object that the `New-PSWorkflowExecutionOption` cmdlet returns.</span></span>

<span data-ttu-id="bb5a7-260">Alternativen för sessioner som använder sessionen bestäms av värdena för session-alternativen och konfigurations alternativen för sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-260">The options of sessions that use the session configuration are determined by the values of session options and the session configuration options.</span></span> <span data-ttu-id="bb5a7-261">Om inget annat anges får alternativ som anges i sessionen, till exempel med hjälp av `New-PSSessionOption` cmdleten, företräde framför alternativ som angetts i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-261">Unless specified, options set in the session, such as by using the `New-PSSessionOption` cmdlet, take precedence over options set in the session configuration.</span></span> <span data-ttu-id="bb5a7-262">Värdena för sessionens alternativ får dock inte överskrida de maximala värden som angetts i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-262">However, session option values cannot exceed maximum values set in the session configuration.</span></span>

<span data-ttu-id="bb5a7-263">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-263">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="bb5a7-264">-ShowSecurityDescriptorUI</span><span class="sxs-lookup"><span data-stu-id="bb5a7-264">-ShowSecurityDescriptorUI</span></span>

<span data-ttu-id="bb5a7-265">Anger att denna cmdlet visar en egenskaps sida som hjälper dig att skapa SDDL för konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-265">Indicates that this cmdlet displays a property sheet that helps you create the SDDL for the session configuration.</span></span> <span data-ttu-id="bb5a7-266">Egenskaps sidan visas när du har angett `Register-PSSessionConfiguration` kommandot och sedan startar om **WinRM** -tjänsten.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-266">The property sheet appears after you enter the `Register-PSSessionConfiguration` command and then restart the **WinRM** service.</span></span>

<span data-ttu-id="bb5a7-267">När du anger behörigheterna för konfigurationen måste du komma ihåg att användarna måste ha minst kör (Invoke)-behörighet för att kunna använda sessionen i en session.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-267">When setting the permissions for the configuration, remember that users must have at least Execute (Invoke) permission to use the session configuration in a session.</span></span>

<span data-ttu-id="bb5a7-268">Du kan inte använda parametern **SecurityDescriptorSDDL** och den här parametern i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-268">You cannot use the **SecurityDescriptorSDDL** parameter and this parameter in the same command.</span></span>

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

### <span data-ttu-id="bb5a7-269">-StartupScript</span><span class="sxs-lookup"><span data-stu-id="bb5a7-269">-StartupScript</span></span>

<span data-ttu-id="bb5a7-270">Anger den fullständigt kvalificerade sökvägen för ett PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-270">Specifies the fully qualified path of a PowerShell script.</span></span> <span data-ttu-id="bb5a7-271">Det angivna skriptet körs i den nya sessionen som använder konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-271">The specified script runs in the new session that uses the session configuration.</span></span>

<span data-ttu-id="bb5a7-272">Du kan också använda skriptet för att konfigurera sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-272">You can use the script to additionally configure the session.</span></span> <span data-ttu-id="bb5a7-273">Om skriptet genererar ett fel, till och med ett icke-avslutande fel, skapas inte sessionen och `New-PSSession` kommandot Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-273">If the script generates an error, even a non-terminating error, the session is not created and the `New-PSSession` command fails.</span></span>

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

### <span data-ttu-id="bb5a7-274">-ThreadOptions</span><span class="sxs-lookup"><span data-stu-id="bb5a7-274">-ThreadOptions</span></span>

<span data-ttu-id="bb5a7-275">Anger hur trådar skapas och används när ett kommando körs i sessionen.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-275">Specifies how threads are created and used when a command runs in the session.</span></span> <span data-ttu-id="bb5a7-276">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="bb5a7-276">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="bb5a7-277">Default</span><span class="sxs-lookup"><span data-stu-id="bb5a7-277">Default</span></span>
- <span data-ttu-id="bb5a7-278">ReuseThread</span><span class="sxs-lookup"><span data-stu-id="bb5a7-278">ReuseThread</span></span>
- <span data-ttu-id="bb5a7-279">UseCurrentThread</span><span class="sxs-lookup"><span data-stu-id="bb5a7-279">UseCurrentThread</span></span>
- <span data-ttu-id="bb5a7-280">UseNewThread</span><span class="sxs-lookup"><span data-stu-id="bb5a7-280">UseNewThread</span></span>

<span data-ttu-id="bb5a7-281">Standardvärdet är **UseCurrentThread**.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-281">The default value is **UseCurrentThread**.</span></span>

<span data-ttu-id="bb5a7-282">Mer information finns i [PSThreadOptions-uppräkning](/dotnet/api/system.management.automation.runspaces.psthreadoptions?view=powershellsdk-1.1.0).</span><span class="sxs-lookup"><span data-stu-id="bb5a7-282">For more information, see [PSThreadOptions Enumeration](/dotnet/api/system.management.automation.runspaces.psthreadoptions?view=powershellsdk-1.1.0).</span></span>

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

### <span data-ttu-id="bb5a7-283">-TransportOption</span><span class="sxs-lookup"><span data-stu-id="bb5a7-283">-TransportOption</span></span>

<span data-ttu-id="bb5a7-284">Anger transport alternativet.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-284">Specifies the transport option.</span></span>

<span data-ttu-id="bb5a7-285">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-285">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="bb5a7-286">-UseSharedProcess</span><span class="sxs-lookup"><span data-stu-id="bb5a7-286">-UseSharedProcess</span></span>

<span data-ttu-id="bb5a7-287">Använd bara en process som värd för alla sessioner som startas av samma användare och Använd samma sessions konfiguration.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-287">Use only one process to host all sessions that are started by the same user and use the same session configuration.</span></span> <span data-ttu-id="bb5a7-288">Som standard finns varje session i en egen process.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-288">By default, each session is hosted in its own process.</span></span>

<span data-ttu-id="bb5a7-289">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-289">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="bb5a7-290">-Confirm</span><span class="sxs-lookup"><span data-stu-id="bb5a7-290">-Confirm</span></span>

<span data-ttu-id="bb5a7-291">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-291">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="bb5a7-292">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="bb5a7-292">-WhatIf</span></span>

<span data-ttu-id="bb5a7-293">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-293">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="bb5a7-294">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-294">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="bb5a7-295">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bb5a7-295">CommonParameters</span></span>

<span data-ttu-id="bb5a7-296">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-296">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bb5a7-297">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="bb5a7-297">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bb5a7-298">INDATA</span><span class="sxs-lookup"><span data-stu-id="bb5a7-298">INPUTS</span></span>

### <span data-ttu-id="bb5a7-299">Inget</span><span class="sxs-lookup"><span data-stu-id="bb5a7-299">None</span></span>

<span data-ttu-id="bb5a7-300">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-300">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="bb5a7-301">UTDATA</span><span class="sxs-lookup"><span data-stu-id="bb5a7-301">OUTPUTS</span></span>

### <span data-ttu-id="bb5a7-302">Microsoft. WSMan. Management. WSManConfigContainerElement</span><span class="sxs-lookup"><span data-stu-id="bb5a7-302">Microsoft.WSMan.Management.WSManConfigContainerElement</span></span>

## <span data-ttu-id="bb5a7-303">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="bb5a7-303">NOTES</span></span>

<span data-ttu-id="bb5a7-304">Om du vill köra denna cmdlet måste du starta PowerShell med alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="bb5a7-304">To run this cmdlet you must start PowerShell by using the **Run as administrator** option.</span></span>

<span data-ttu-id="bb5a7-305">Den här cmdleten genererar XML som representerar en plugin-konfiguration för webb tjänster för hantering (WS-Management) och skickar XML till WS-Management, som registrerar plugin-programmet på den lokala datorn ( `New-Item wsman:\localhost\plugin` ).</span><span class="sxs-lookup"><span data-stu-id="bb5a7-305">This cmdlet generates XML that represents a Web Services for Management (WS-Management) plug-in configuration and sends the XML to WS-Management, which registers the plug-in on the local computer (`New-Item wsman:\localhost\plugin`).</span></span>

<span data-ttu-id="bb5a7-306">Egenskaperna för ett konfigurations objekt för en session varierar beroende på vilka alternativ som har angetts för konfigurationen av sessionen och värdena för dessa alternativ.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-306">The properties of a session configuration object vary with the options set for the session configuration and the values of those options.</span></span> <span data-ttu-id="bb5a7-307">Dessutom har sessionsinställningar som använder en konfigurations fil för sessionen ytterligare egenskaper.</span><span class="sxs-lookup"><span data-stu-id="bb5a7-307">Also, session configurations that use a session configuration file have additional properties.</span></span>

## <span data-ttu-id="bb5a7-308">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="bb5a7-308">RELATED LINKS</span></span>

[<span data-ttu-id="bb5a7-309">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="bb5a7-309">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="bb5a7-310">Aktivera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="bb5a7-310">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="bb5a7-311">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="bb5a7-311">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="bb5a7-312">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="bb5a7-312">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="bb5a7-313">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="bb5a7-313">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="bb5a7-314">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="bb5a7-314">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="bb5a7-315">Avregistrera-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="bb5a7-315">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="bb5a7-316">WSMan-Provider</span><span class="sxs-lookup"><span data-stu-id="bb5a7-316">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="bb5a7-317">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="bb5a7-317">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="bb5a7-318">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="bb5a7-318">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
