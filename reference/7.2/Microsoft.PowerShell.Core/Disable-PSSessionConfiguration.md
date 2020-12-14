---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/disable-pssessionconfiguration?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSSessionConfiguration
ms.openlocfilehash: c2f88431c0a09a2d4093c6523467a812812c10bc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709595"
---
# <span data-ttu-id="f358a-102">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="f358a-102">Disable-PSSessionConfiguration</span></span>

## <span data-ttu-id="f358a-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="f358a-103">SYNOPSIS</span></span>
<span data-ttu-id="f358a-104">Inaktiverar nodkonfigurationer på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="f358a-104">Disables session configurations on the local computer.</span></span>

## <span data-ttu-id="f358a-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f358a-105">SYNTAX</span></span>

```
Disable-PSSessionConfiguration [[-Name] <String[]>] [-Force] [-NoServiceRestart] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="f358a-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="f358a-106">DESCRIPTION</span></span>

<span data-ttu-id="f358a-107">`Disable-PSSessionConfiguration`Cmdleten inaktiverar sessionsinställningar på den lokala datorn, vilket hindrar alla användare från att använda sessionens konfigurationer för att skapa en **PSSessions**(User Managed sessions) på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="f358a-107">The `Disable-PSSessionConfiguration` cmdlet disables session configurations on the local computer, which prevents all users from using the session configurations to create a user-managed sessions (**PSSessions**) on the local computer.</span></span> <span data-ttu-id="f358a-108">Det här är en avancerad cmdlet som är avsedd att användas av system administratörer för att hantera konfigurationer för anpassade sessioner för sina användare.</span><span class="sxs-lookup"><span data-stu-id="f358a-108">This is an advanced cmdlet that is designed to be used by system administrators to manage customized session configurations for their users.</span></span>

<span data-ttu-id="f358a-109">Från och med PowerShell 3,0 `Disable-PSSessionConfiguration` ställer cmdleten in den **aktiverade** inställningen för session konfiguration ( `WSMan:\localhost\Plugins\<SessionConfiguration>\Enabled` ) till falskt.</span><span class="sxs-lookup"><span data-stu-id="f358a-109">Starting in PowerShell 3.0, the `Disable-PSSessionConfiguration` cmdlet sets the **Enabled** setting of the session configuration (`WSMan:\localhost\Plugins\<SessionConfiguration>\Enabled`) to False.</span></span>

<span data-ttu-id="f358a-110">I PowerShell 2,0 `Disable-PSSessionConfiguration` lägger cmdleten till en **Deny_All** post till säkerhets beskrivningen för en eller flera registrerade sessioner.</span><span class="sxs-lookup"><span data-stu-id="f358a-110">In PowerShell 2.0, the `Disable-PSSessionConfiguration` cmdlet adds a **Deny_All** entry to the security descriptor of one or more registered session configurations.</span></span>

<span data-ttu-id="f358a-111">Utan parametrar `Disable-PSSessionConfiguration` inaktiverar **Microsoft. PowerShell** -konfigurationen, standard konfigurationen som används för sessioner.</span><span class="sxs-lookup"><span data-stu-id="f358a-111">Without parameters, `Disable-PSSessionConfiguration` disables the **Microsoft.PowerShell** configuration, the default configuration used for sessions.</span></span> <span data-ttu-id="f358a-112">Om användaren inte anger en annan konfiguration, förhindras både lokala och fjärranslutna användare från att skapa sessioner som ansluter till datorn.</span><span class="sxs-lookup"><span data-stu-id="f358a-112">Unless the user specifies a different configuration, both local and remote users are effectively prevented from creating any sessions that connect to the computer.</span></span>

<span data-ttu-id="f358a-113">Om du vill inaktivera alla sessionsinställningar på datorn använder du `Disable-PSRemoting` .</span><span class="sxs-lookup"><span data-stu-id="f358a-113">To disable all session configurations on the computer, use `Disable-PSRemoting`.</span></span>

## <span data-ttu-id="f358a-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="f358a-114">EXAMPLES</span></span>

### <span data-ttu-id="f358a-115">Exempel 1: inaktivera standard konfigurationen</span><span class="sxs-lookup"><span data-stu-id="f358a-115">Example 1: Disable the default configuration</span></span>

<span data-ttu-id="f358a-116">I det här exemplet inaktive ras konfigurationen av Microsoft. PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="f358a-116">This example disables the Microsoft.PowerShell session configuration.</span></span>

```powershell
Disable-PSSessionConfiguration
```

### <span data-ttu-id="f358a-117">Exempel 2: inaktivera alla registrerade sessionsbaserade</span><span class="sxs-lookup"><span data-stu-id="f358a-117">Example 2: Disable all registered session configurations</span></span>

<span data-ttu-id="f358a-118">I det här exemplet inaktive ras alla registrerade sessionsbaserade på datorn.</span><span class="sxs-lookup"><span data-stu-id="f358a-118">This example disables all registered session configurations on the computer.</span></span>

```powershell
Disable-PSSessionConfiguration -Name *
```

### <span data-ttu-id="f358a-119">Exempel 3: inaktivera sessionsbaserade efter namn</span><span class="sxs-lookup"><span data-stu-id="f358a-119">Example 3: Disable session configurations by name</span></span>

<span data-ttu-id="f358a-120">I det här exemplet inaktive ras alla sessionsinställningar som har namn som börjar med Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f358a-120">This example disables all session configurations that have names that begin with Microsoft.</span></span> <span data-ttu-id="f358a-121">Parametern **Force** förhindrar alla användar meddelanden från cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f358a-121">The **Force** parameter suppresses all user prompts from the cmdlet.</span></span>

```powershell
Disable-PSSessionConfiguration -Name Microsoft* -Force
```

### <span data-ttu-id="f358a-122">Exempel 4: inaktivera sessionsbaserade med hjälp av pipelinen</span><span class="sxs-lookup"><span data-stu-id="f358a-122">Example 4: Disable session configurations by using the pipeline</span></span>

<span data-ttu-id="f358a-123">I det här exemplet inaktive ras **MaintenanceShell** och **AdminShell** .</span><span class="sxs-lookup"><span data-stu-id="f358a-123">This example disables the **MaintenanceShell** and **AdminShell** session configurations.</span></span> <span data-ttu-id="f358a-124">Pipeline-operatorn (|) skickar resultatet från en `Get-PSSessionConfiguration` till `Disable-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="f358a-124">The pipeline operator (|) sends the results of a `Get-PSSessionConfiguration` to `Disable-PSSessionConfiguration`.</span></span>

```powershell
Get-PSSessionConfiguration -Name MaintenanceShell, AdminShell | Disable-PSSessionConfiguration
```

### <span data-ttu-id="f358a-125">Exempel 5: effekterna av att inaktivera en sessions konfiguration</span><span class="sxs-lookup"><span data-stu-id="f358a-125">Example 5: Effects of disabling a session configuration</span></span>

<span data-ttu-id="f358a-126">I det här exemplet visas behörigheterna före och efter körningen `Disable-PSSessionConfiguration` och effekterna av att inaktivera en konfiguration av sessionen.</span><span class="sxs-lookup"><span data-stu-id="f358a-126">This example shows the permissions before and after running `Disable-PSSessionConfiguration` and the effect of disabling a session configuration.</span></span>

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
> <span data-ttu-id="f358a-127">Att inaktivera konfigurationen förhindrar inte att du ändrar konfigurationen med hjälp av `Set-PSSessionConfiguration` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f358a-127">Disabling the configuration does not prevent you from changing the configuration using the `Set-PSSessionConfiguration` cmdlet.</span></span> <span data-ttu-id="f358a-128">Den förhindrar bara användning av konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="f358a-128">It only prevents use of the configuration.</span></span>

## <span data-ttu-id="f358a-129">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="f358a-129">PARAMETERS</span></span>

### <span data-ttu-id="f358a-130">-Force</span><span class="sxs-lookup"><span data-stu-id="f358a-130">-Force</span></span>

<span data-ttu-id="f358a-131">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="f358a-131">Forces the command to run without asking for user confirmation.</span></span>

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

### <span data-ttu-id="f358a-132">-Name</span><span class="sxs-lookup"><span data-stu-id="f358a-132">-Name</span></span>

<span data-ttu-id="f358a-133">Anger en matris med namn på de sessionsinställningar som ska inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="f358a-133">Specifies an array of names of session configurations to disable.</span></span> <span data-ttu-id="f358a-134">Ange ett eller flera konfigurations namn.</span><span class="sxs-lookup"><span data-stu-id="f358a-134">Enter one or more configuration names.</span></span> <span data-ttu-id="f358a-135">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="f358a-135">Wildcard characters are permitted.</span></span> <span data-ttu-id="f358a-136">Du kan också skicka en sträng som innehåller ett konfigurations namn eller ett konfigurations objekt för session till `Disable-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="f358a-136">You can also pipe a string that contains a configuration name or a session configuration object to `Disable-PSSessionConfiguration`.</span></span>

<span data-ttu-id="f358a-137">Om du utelämnar den här parametern `Disable-PSSessionConfiguration` inaktive ras konfigurationen av Microsoft. PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="f358a-137">If you omit this parameter, `Disable-PSSessionConfiguration` disables the Microsoft.PowerShell session configuration.</span></span>

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

### <span data-ttu-id="f358a-138">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="f358a-138">-NoServiceRestart</span></span>

<span data-ttu-id="f358a-139">Används för att förhindra omstart av WSMan-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="f358a-139">Used to prevent the restart of the WSMan service.</span></span> <span data-ttu-id="f358a-140">Du behöver inte starta om tjänsten för att inaktivera konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="f358a-140">It is not necessary to restart the service to disable the configuration.</span></span>

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

### <span data-ttu-id="f358a-141">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f358a-141">-Confirm</span></span>

<span data-ttu-id="f358a-142">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f358a-142">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f358a-143">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f358a-143">-WhatIf</span></span>

<span data-ttu-id="f358a-144">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="f358a-144">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="f358a-145">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="f358a-145">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="f358a-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f358a-146">CommonParameters</span></span>

<span data-ttu-id="f358a-147">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f358a-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f358a-148">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f358a-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f358a-149">INDATA</span><span class="sxs-lookup"><span data-stu-id="f358a-149">INPUTS</span></span>

### <span data-ttu-id="f358a-150">Microsoft. PowerShell. commands. PSSessionConfigurationCommands # PSSessionConfiguration, system. String</span><span class="sxs-lookup"><span data-stu-id="f358a-150">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration, System.String</span></span>

<span data-ttu-id="f358a-151">Du kan skicka ett konfigurations objekt för en session eller en sträng som innehåller namnet på en sessions konfiguration till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f358a-151">You can pipe a session configuration object or a string that contains the name of a session configuration to this cmdlet.</span></span>

## <span data-ttu-id="f358a-152">UTDATA</span><span class="sxs-lookup"><span data-stu-id="f358a-152">OUTPUTS</span></span>

### <span data-ttu-id="f358a-153">Inga</span><span class="sxs-lookup"><span data-stu-id="f358a-153">None</span></span>

<span data-ttu-id="f358a-154">Denna cmdlet returnerar inga objekt.</span><span class="sxs-lookup"><span data-stu-id="f358a-154">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="f358a-155">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="f358a-155">NOTES</span></span>

<span data-ttu-id="f358a-156">Den här cmdleten är endast tillgänglig på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="f358a-156">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="f358a-157">Om du vill köra denna cmdlet måste du starta PowerShell med alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="f358a-157">To run this cmdlet you must start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="f358a-158">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="f358a-158">RELATED LINKS</span></span>

[<span data-ttu-id="f358a-159">Aktivera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="f358a-159">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="f358a-160">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="f358a-160">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="f358a-161">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="f358a-161">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="f358a-162">Registrera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="f358a-162">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="f358a-163">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="f358a-163">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="f358a-164">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="f358a-164">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="f358a-165">Avregistrera-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="f358a-165">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="f358a-166">WSMan-Provider</span><span class="sxs-lookup"><span data-stu-id="f358a-166">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="f358a-167">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="f358a-167">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="f358a-168">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="f358a-168">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
