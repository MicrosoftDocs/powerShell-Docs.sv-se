---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-pssessionconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSSessionConfiguration
ms.openlocfilehash: 978f42174d211d1ceaf7a19d4a348e1bbcaa270b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263672"
---
# <span data-ttu-id="f7e70-103">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="f7e70-103">Disable-PSSessionConfiguration</span></span>

## <span data-ttu-id="f7e70-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="f7e70-104">SYNOPSIS</span></span>
<span data-ttu-id="f7e70-105">Inaktiverar nodkonfigurationer på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="f7e70-105">Disables session configurations on the local computer.</span></span>

## <span data-ttu-id="f7e70-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f7e70-106">SYNTAX</span></span>

```
Disable-PSSessionConfiguration [[-Name] <String[]>] [-Force] [-NoServiceRestart] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="f7e70-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="f7e70-107">DESCRIPTION</span></span>

<span data-ttu-id="f7e70-108">`Disable-PSSessionConfiguration`Cmdleten inaktiverar sessionsinställningar på den lokala datorn, vilket hindrar alla användare från att använda sessionens konfigurationer för att skapa en **PSSessions** (User Managed sessions) på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="f7e70-108">The `Disable-PSSessionConfiguration` cmdlet disables session configurations on the local computer, which prevents all users from using the session configurations to create a user-managed sessions ( **PSSessions** ) on the local computer.</span></span> <span data-ttu-id="f7e70-109">Det här är en avancerad cmdlet som är avsedd att användas av system administratörer för att hantera konfigurationer för anpassade sessioner för sina användare.</span><span class="sxs-lookup"><span data-stu-id="f7e70-109">This is an advanced cmdlet that is designed to be used by system administrators to manage customized session configurations for their users.</span></span>

<span data-ttu-id="f7e70-110">Från och med PowerShell 3,0 `Disable-PSSessionConfiguration` ställer cmdleten in den **aktiverade** inställningen för session konfiguration ( `WSMan:\localhost\Plugins\<SessionConfiguration>\Enabled` ) till falskt.</span><span class="sxs-lookup"><span data-stu-id="f7e70-110">Starting in PowerShell 3.0, the `Disable-PSSessionConfiguration` cmdlet sets the **Enabled** setting of the session configuration (`WSMan:\localhost\Plugins\<SessionConfiguration>\Enabled`) to False.</span></span>

<span data-ttu-id="f7e70-111">I PowerShell 2,0 `Disable-PSSessionConfiguration` lägger cmdleten till en **Deny_All** post till säkerhets beskrivningen för en eller flera registrerade sessioner.</span><span class="sxs-lookup"><span data-stu-id="f7e70-111">In PowerShell 2.0, the `Disable-PSSessionConfiguration` cmdlet adds a **Deny_All** entry to the security descriptor of one or more registered session configurations.</span></span>

<span data-ttu-id="f7e70-112">Utan parametrar `Disable-PSSessionConfiguration` inaktiverar **Microsoft. PowerShell** -konfigurationen, standard konfigurationen som används för sessioner.</span><span class="sxs-lookup"><span data-stu-id="f7e70-112">Without parameters, `Disable-PSSessionConfiguration` disables the **Microsoft.PowerShell** configuration, the default configuration used for sessions.</span></span> <span data-ttu-id="f7e70-113">Om användaren inte anger en annan konfiguration, förhindras både lokala och fjärranslutna användare från att skapa sessioner som ansluter till datorn.</span><span class="sxs-lookup"><span data-stu-id="f7e70-113">Unless the user specifies a different configuration, both local and remote users are effectively prevented from creating any sessions that connect to the computer.</span></span>

<span data-ttu-id="f7e70-114">Om du vill inaktivera alla sessionsinställningar på datorn använder du `Disable-PSRemoting` .</span><span class="sxs-lookup"><span data-stu-id="f7e70-114">To disable all session configurations on the computer, use `Disable-PSRemoting`.</span></span>

## <span data-ttu-id="f7e70-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="f7e70-115">EXAMPLES</span></span>

### <span data-ttu-id="f7e70-116">Exempel 1: inaktivera standard konfigurationen</span><span class="sxs-lookup"><span data-stu-id="f7e70-116">Example 1: Disable the default configuration</span></span>

<span data-ttu-id="f7e70-117">I det här exemplet inaktive ras konfigurationen av Microsoft. PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="f7e70-117">This example disables the Microsoft.PowerShell session configuration.</span></span>

```powershell
Disable-PSSessionConfiguration
```

### <span data-ttu-id="f7e70-118">Exempel 2: inaktivera alla registrerade sessionsbaserade</span><span class="sxs-lookup"><span data-stu-id="f7e70-118">Example 2: Disable all registered session configurations</span></span>

<span data-ttu-id="f7e70-119">I det här exemplet inaktive ras alla registrerade sessionsbaserade på datorn.</span><span class="sxs-lookup"><span data-stu-id="f7e70-119">This example disables all registered session configurations on the computer.</span></span>

```powershell
Disable-PSSessionConfiguration -Name *
```

### <span data-ttu-id="f7e70-120">Exempel 3: inaktivera sessionsbaserade efter namn</span><span class="sxs-lookup"><span data-stu-id="f7e70-120">Example 3: Disable session configurations by name</span></span>

<span data-ttu-id="f7e70-121">I det här exemplet inaktive ras alla sessionsinställningar som har namn som börjar med Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f7e70-121">This example disables all session configurations that have names that begin with Microsoft.</span></span> <span data-ttu-id="f7e70-122">Parametern **Force** förhindrar alla användar meddelanden från cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f7e70-122">The **Force** parameter suppresses all user prompts from the cmdlet.</span></span>

```powershell
Disable-PSSessionConfiguration -Name Microsoft* -Force
```

### <span data-ttu-id="f7e70-123">Exempel 4: inaktivera sessionsbaserade med hjälp av pipelinen</span><span class="sxs-lookup"><span data-stu-id="f7e70-123">Example 4: Disable session configurations by using the pipeline</span></span>

<span data-ttu-id="f7e70-124">I det här exemplet inaktive ras **MaintenanceShell** och **AdminShell** .</span><span class="sxs-lookup"><span data-stu-id="f7e70-124">This example disables the **MaintenanceShell** and **AdminShell** session configurations.</span></span> <span data-ttu-id="f7e70-125">Pipeline-operatorn (|) skickar resultatet från en `Get-PSSessionConfiguration` till `Disable-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="f7e70-125">The pipeline operator (|) sends the results of a `Get-PSSessionConfiguration` to `Disable-PSSessionConfiguration`.</span></span>

```powershell
Get-PSSessionConfiguration -Name MaintenanceShell, AdminShell | Disable-PSSessionConfiguration
```

### <span data-ttu-id="f7e70-126">Exempel 5: effekterna av att inaktivera en sessions konfiguration</span><span class="sxs-lookup"><span data-stu-id="f7e70-126">Example 5: Effects of disabling a session configuration</span></span>

<span data-ttu-id="f7e70-127">I det här exemplet visas behörigheterna före och efter körningen `Disable-PSSessionConfiguration` och effekterna av att inaktivera en konfiguration av sessionen.</span><span class="sxs-lookup"><span data-stu-id="f7e70-127">This example shows the permissions before and after running `Disable-PSSessionConfiguration` and the effect of disabling a session configuration.</span></span>

```
PS> Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Name                   Permission
----                   ----------
MaintenanceShell       BUILTIN\Administrators AccessAllowed
microsoft.powershell   BUILTIN\Administrators AccessAllowed
microsoft.powershell32 BUILTIN\Administrators AccessAllowed

PS> Disable-PSSessionConfiguration -Name MaintenanceShell -Force
PS> Get-PSSessionConfiguration | Format-Table -Property Name, Permission -Auto

Name                   Permission
----                   ----------
MaintenanceShell       Everyone AccessDenied, BUILTIN\Administrators AccessAllowed
microsoft.powershell   BUILTIN\Administrators AccessAllowed
microsoft.powershell32 BUILTIN\Administrators AccessAllowed

PS> New-PSSession -ComputerName localhost -ConfigurationName MaintenanceShell

[localhost] Connecting to remote server failed with the following error message : Access is denied.
For more information, see the about_Remote_Troubleshooting Help topic.
+ CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [], PSRemotingTransportException
+ FullyQualifiedErrorId : PSSessionOpenFailed
```

> [!NOTE]
> <span data-ttu-id="f7e70-128">Att inaktivera konfigurationen förhindrar inte att du ändrar konfigurationen med hjälp av `Set-PSSessionConfiguration` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f7e70-128">Disabling the configuration does not prevent you from changing the configuration using the `Set-PSSessionConfiguration` cmdlet.</span></span> <span data-ttu-id="f7e70-129">Den förhindrar bara användning av konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="f7e70-129">It only prevents use of the configuration.</span></span>

## <span data-ttu-id="f7e70-130">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="f7e70-130">PARAMETERS</span></span>

### <span data-ttu-id="f7e70-131">-Force</span><span class="sxs-lookup"><span data-stu-id="f7e70-131">-Force</span></span>

<span data-ttu-id="f7e70-132">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="f7e70-132">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="f7e70-133">-Name</span><span class="sxs-lookup"><span data-stu-id="f7e70-133">-Name</span></span>

<span data-ttu-id="f7e70-134">Anger en matris med namn på de sessionsinställningar som ska inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="f7e70-134">Specifies an array of names of session configurations to disable.</span></span> <span data-ttu-id="f7e70-135">Ange ett eller flera konfigurations namn.</span><span class="sxs-lookup"><span data-stu-id="f7e70-135">Enter one or more configuration names.</span></span> <span data-ttu-id="f7e70-136">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="f7e70-136">Wildcard characters are permitted.</span></span> <span data-ttu-id="f7e70-137">Du kan också skicka en sträng som innehåller ett konfigurations namn eller ett konfigurations objekt för session till `Disable-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="f7e70-137">You can also pipe a string that contains a configuration name or a session configuration object to `Disable-PSSessionConfiguration`.</span></span>

<span data-ttu-id="f7e70-138">Om du utelämnar den här parametern `Disable-PSSessionConfiguration` inaktive ras konfigurationen av Microsoft. PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="f7e70-138">If you omit this parameter, `Disable-PSSessionConfiguration` disables the Microsoft.PowerShell session configuration.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="f7e70-139">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="f7e70-139">-NoServiceRestart</span></span>

<span data-ttu-id="f7e70-140">Används för att förhindra omstart av WSMan-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="f7e70-140">Used to prevent the restart of the WSMan service.</span></span> <span data-ttu-id="f7e70-141">Du behöver inte starta om tjänsten för att inaktivera konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="f7e70-141">It is not necessary to restart the service to disable the configuration.</span></span>

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

### <span data-ttu-id="f7e70-142">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f7e70-142">-Confirm</span></span>

<span data-ttu-id="f7e70-143">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f7e70-143">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f7e70-144">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f7e70-144">-WhatIf</span></span>

<span data-ttu-id="f7e70-145">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="f7e70-145">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="f7e70-146">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="f7e70-146">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="f7e70-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f7e70-147">CommonParameters</span></span>

<span data-ttu-id="f7e70-148">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f7e70-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f7e70-149">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f7e70-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f7e70-150">INDATA</span><span class="sxs-lookup"><span data-stu-id="f7e70-150">INPUTS</span></span>

### <span data-ttu-id="f7e70-151">Microsoft. PowerShell. commands. PSSessionConfigurationCommands # PSSessionConfiguration, system. String</span><span class="sxs-lookup"><span data-stu-id="f7e70-151">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration, System.String</span></span>

<span data-ttu-id="f7e70-152">Du kan skicka ett konfigurations objekt för en session eller en sträng som innehåller namnet på en sessions konfiguration till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f7e70-152">You can pipe a session configuration object or a string that contains the name of a session configuration to this cmdlet.</span></span>

## <span data-ttu-id="f7e70-153">UTDATA</span><span class="sxs-lookup"><span data-stu-id="f7e70-153">OUTPUTS</span></span>

### <span data-ttu-id="f7e70-154">Inget</span><span class="sxs-lookup"><span data-stu-id="f7e70-154">None</span></span>

<span data-ttu-id="f7e70-155">Denna cmdlet returnerar inga objekt.</span><span class="sxs-lookup"><span data-stu-id="f7e70-155">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="f7e70-156">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="f7e70-156">NOTES</span></span>

<span data-ttu-id="f7e70-157">Om du vill köra denna cmdlet måste du starta PowerShell med alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="f7e70-157">To run this cmdlet you must start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="f7e70-158">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="f7e70-158">RELATED LINKS</span></span>

[<span data-ttu-id="f7e70-159">Aktivera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="f7e70-159">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="f7e70-160">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="f7e70-160">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="f7e70-161">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="f7e70-161">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="f7e70-162">Registrera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="f7e70-162">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="f7e70-163">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="f7e70-163">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="f7e70-164">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="f7e70-164">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="f7e70-165">Avregistrera-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="f7e70-165">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="f7e70-166">WSMan-Provider</span><span class="sxs-lookup"><span data-stu-id="f7e70-166">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="f7e70-167">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="f7e70-167">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="f7e70-168">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="f7e70-168">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
