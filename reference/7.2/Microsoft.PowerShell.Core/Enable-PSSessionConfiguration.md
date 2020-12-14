---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-pssessionconfiguration?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSSessionConfiguration
ms.openlocfilehash: 86650f33f376ccb7d1428836c9d0070e749cf0ee
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709601"
---
# <span data-ttu-id="8d3d7-102">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="8d3d7-102">Enable-PSSessionConfiguration</span></span>

## <span data-ttu-id="8d3d7-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="8d3d7-103">SYNOPSIS</span></span>
<span data-ttu-id="8d3d7-104">Aktiverar sessionsinställningar på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-104">Enables the session configurations on the local computer.</span></span>

## <span data-ttu-id="8d3d7-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="8d3d7-105">SYNTAX</span></span>

```
Enable-PSSessionConfiguration [[-Name] <String[]>] [-Force] [-SecurityDescriptorSddl <String>]
 [-SkipNetworkProfileCheck] [-NoServiceRestart] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="8d3d7-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="8d3d7-106">DESCRIPTION</span></span>

<span data-ttu-id="8d3d7-107">`Enable-PSSessionConfiguration`Cmdleten aktiverar registrerade sessionsinställningar som har inaktiverats, till exempel med hjälp av `Disable-PSSessionConfiguration` `Disable-PSRemoting` cmdletarna eller **AccessMode** -parametern för `Register-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="8d3d7-107">The `Enable-PSSessionConfiguration` cmdlet enables registered session configurations that have been disabled, such as by using the `Disable-PSSessionConfiguration` or `Disable-PSRemoting` cmdlets, or the **AccessMode** parameter of `Register-PSSessionConfiguration`.</span></span> <span data-ttu-id="8d3d7-108">Det här är en avancerad cmdlet som är avsedd att användas av system administratörer för att hantera konfigurationer för anpassade sessioner för sina användare.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-108">This is an advanced cmdlet that is designed to be used by system administrators to manage customized session configurations for their users.</span></span>

<span data-ttu-id="8d3d7-109">Utan parametrar `Enable-PSSessionConfiguration` aktiverar **Microsoft. PowerShell** -konfigurationen, som är den standard konfiguration som används för sessioner.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-109">Without parameters, `Enable-PSSessionConfiguration` enables the **Microsoft.PowerShell** configuration, which is the default configuration that is used for sessions.</span></span>

<span data-ttu-id="8d3d7-110">`Enable-PSSessionConfiguration` tar bort inställningen **Deny_All** från säkerhets beskrivningen för de berörda sessionerna, aktiverar den lyssnare som accepterar begär Anden på alla IP-adresser och startar om WinRM-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-110">`Enable-PSSessionConfiguration` removes the **Deny_All** setting from the security descriptor of the affected session configurations, turns on the listener that accepts requests on any IP address, and restarts the WinRM service.</span></span> <span data-ttu-id="8d3d7-111">Från och med PowerShell 3,0 `Enable-PSSessionConfiguration` anger även värdet för egenskapen **Enabled** för session Configuration ( `WSMan:\<computer>\PlugIn\<SessionConfigurationName>\Enabled` ) till true.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-111">Beginning in PowerShell 3.0, `Enable-PSSessionConfiguration` also sets the value of the **Enabled** property of the session configuration (`WSMan:\<computer>\PlugIn\<SessionConfigurationName>\Enabled`) to True.</span></span> <span data-ttu-id="8d3d7-112">Men `Enable-PSSessionConfiguration` tar inte bort eller ändrar inställningen för säkerhets beskrivningen **Network_Deny_All** ( `AccessMode=Local` ) som endast tillåter användare av den lokala datorn att använda den för att konfigurera sessionen.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-112">However, `Enable-PSSessionConfiguration` does not remove or change the **Network_Deny_All** (`AccessMode=Local`) security descriptor setting that allows only users of the local computer to use to the session configuration.</span></span>

## <span data-ttu-id="8d3d7-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="8d3d7-113">EXAMPLES</span></span>

### <span data-ttu-id="8d3d7-114">Exempel 1: återaktivera Standardsessionen</span><span class="sxs-lookup"><span data-stu-id="8d3d7-114">Example 1: Re-enable the default session</span></span>

<span data-ttu-id="8d3d7-115">I det här exemplet återaktiveras standardsessions konfigurationen för **Microsoft. PowerShell** på datorn.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-115">This example re-enables the **Microsoft.PowerShell** default session configuration on the computer.</span></span>

```powershell
Enable-PSSessionConfiguration
```

### <span data-ttu-id="8d3d7-116">Exempel 2: återaktivera angivna sessioner</span><span class="sxs-lookup"><span data-stu-id="8d3d7-116">Example 2: Re-enable specified sessions</span></span>

<span data-ttu-id="8d3d7-117">I det här exemplet återaktiveras **MaintenanceShell** -och **AdminShell** på datorn.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-117">This example re-enables the **MaintenanceShell** and **AdminShell** session configurations on the computer.</span></span>

```powershell
Enable-PSSessionConfiguration -Name MaintenanceShell, AdminShell
```

### <span data-ttu-id="8d3d7-118">Exempel 3: återaktivera alla sessioner</span><span class="sxs-lookup"><span data-stu-id="8d3d7-118">Example 3: Re-enable the all sessions</span></span>

<span data-ttu-id="8d3d7-119">I det här exemplet återaktiveras alla sessionsbaserade på datorn.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-119">This example re-enables all session configurations on the computer.</span></span> <span data-ttu-id="8d3d7-120">Dessa kommandon är likvärdiga.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-120">These commands are equivalent.</span></span>
<span data-ttu-id="8d3d7-121">Därför kan du använda antingen.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-121">Therefore, you can use either.</span></span>

```powershell
Enable-PSSessionConfiguration -Name *
Get-PSSessionConfiguration | Enable-PSSessionConfiguration
```

<span data-ttu-id="8d3d7-122">`Enable-PSSessionConfiguration` genererar inget fel om du aktiverar en sessionshantering som redan är aktive rad.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-122">`Enable-PSSessionConfiguration` does not generate an error if you enable a session configuration that is already enabled.</span></span>

### <span data-ttu-id="8d3d7-123">Exempel 4: återaktivera en session och ange en ny säkerhets Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8d3d7-123">Example 4: Re-enable a session and specify a new security descriptor</span></span>

<span data-ttu-id="8d3d7-124">I det här exemplet återaktiveras **MaintenanceShell** och en ny säkerhets beskrivning anges för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-124">This example re-enables the **MaintenanceShell** session configuration and specifies a new security descriptor for the configuration.</span></span>

```powershell
$sddl = "O:NSG:BAD:P(A;;GXGWGR;;;BA)(A;;GAGR;;;S-1-5-21-123456789-188441444-3100496)S:P"
Enable-PSSessionConfiguration -Name MaintenanceShell -SecurityDescriptorSDDL $sddl
```

## <span data-ttu-id="8d3d7-125">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="8d3d7-125">PARAMETERS</span></span>

### <span data-ttu-id="8d3d7-126">-Force</span><span class="sxs-lookup"><span data-stu-id="8d3d7-126">-Force</span></span>

<span data-ttu-id="8d3d7-127">Anger att cmdleten inte ber dig om bekräftelse och startar om WinRM-tjänsten utan att du behöver ange något.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-127">Indicates that the cmdlet does not prompt you for confirmation, and restarts the WinRM service without prompting.</span></span> <span data-ttu-id="8d3d7-128">Att starta om tjänsten gör att konfigurations ändringen träder i kraft.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-128">Restarting the service makes the configuration change effective.</span></span>

<span data-ttu-id="8d3d7-129">Om du vill förhindra en omstart och ignorera omstarts meddelandet använder du parametern **NoServiceRestart** .</span><span class="sxs-lookup"><span data-stu-id="8d3d7-129">To prevent a restart and suppress the restart prompt, use the **NoServiceRestart** parameter.</span></span>

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

### <span data-ttu-id="8d3d7-130">-Name</span><span class="sxs-lookup"><span data-stu-id="8d3d7-130">-Name</span></span>

<span data-ttu-id="8d3d7-131">Anger namnen på de sessionsinställningar som ska aktive ras.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-131">Specifies the names of session configurations to enable.</span></span> <span data-ttu-id="8d3d7-132">Ange ett eller flera konfigurations namn.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-132">Enter one or more configuration names.</span></span>
<span data-ttu-id="8d3d7-133">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-133">Wildcard characters are permitted.</span></span>

<span data-ttu-id="8d3d7-134">Du kan också skicka en sträng som innehåller ett konfigurations namn eller ett konfigurations objekt för session till `Enable-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="8d3d7-134">You can also pipe a string that contains a configuration name or a session configuration object to `Enable-PSSessionConfiguration`.</span></span>

<span data-ttu-id="8d3d7-135">Om du utelämnar den här parametern `Enable-PSSessionConfiguration` aktiverar **Microsoft. PowerShell** -sessionen.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-135">If you omit this parameter, `Enable-PSSessionConfiguration` enables the **Microsoft.PowerShell** session configuration.</span></span>

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

### <span data-ttu-id="8d3d7-136">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="8d3d7-136">-NoServiceRestart</span></span>

<span data-ttu-id="8d3d7-137">Anger att cmdleten inte startar om tjänsten.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-137">Indicates that the cmdlet does not restart the service.</span></span>

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

### <span data-ttu-id="8d3d7-138">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="8d3d7-138">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="8d3d7-139">Anger en säkerhets Beskrivning där denna cmdlet ersätter säkerhets beskrivningen i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-139">Specifies a security descriptor with which this cmdlet replaces the security descriptor on the session configuration.</span></span>

<span data-ttu-id="8d3d7-140">Om du utelämnar den här parametern `Enable-PSSessionConfiguration` tar endast bort neka alla objekt från säkerhets beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-140">If you omit this parameter, `Enable-PSSessionConfiguration` only deletes the deny all item from the security descriptor.</span></span>

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

### <span data-ttu-id="8d3d7-141">-SkipNetworkProfileCheck</span><span class="sxs-lookup"><span data-stu-id="8d3d7-141">-SkipNetworkProfileCheck</span></span>

<span data-ttu-id="8d3d7-142">Anger att denna cmdlet aktiverar sessionen när datorn finns i ett offentligt nätverk.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-142">Indicates that this cmdlet enables the session configuration when the computer is on a public network.</span></span> <span data-ttu-id="8d3d7-143">Med den här parametern kan du använda en brand Väggs regel för offentliga nätverk som endast tillåter fjärråtkomst från datorer i samma lokala undernät.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-143">This parameter enables a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span> <span data-ttu-id="8d3d7-144">Som standard `Enable-PSSessionConfiguration` går det inte att utföra i ett offentligt nätverk.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-144">By default, `Enable-PSSessionConfiguration` fails on a public network.</span></span>

<span data-ttu-id="8d3d7-145">Den här parametern är avsedd för klient versioner av Windows operativ system.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-145">This parameter is designed for client versions of the Windows operating system.</span></span> <span data-ttu-id="8d3d7-146">Server versioner av Windows operativ system har en lokal brand Väggs regel för offentliga nätverk.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-146">Server versions of the Windows operating system have a local subnet firewall rule for public networks.</span></span> <span data-ttu-id="8d3d7-147">Men om den lokala brand Väggs regeln är inaktive rad på en server version av Windows-operativsystemet, aktive ras den här parametern igen.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-147">However, if the local subnet firewall rule is disabled on a server version of the Windows operating system, this parameter re-enables it.</span></span>

<span data-ttu-id="8d3d7-148">Om du vill ta bort den lokala under näts begränsningen och aktivera fjärråtkomst från alla platser i offentliga nätverk använder du `Set-NetFirewallRule` cmdleten i modulen netsecurity.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-148">To remove the local subnet restriction and enable remote access from all locations on public networks, use the `Set-NetFirewallRule` cmdlet in the NetSecurity module.</span></span> <span data-ttu-id="8d3d7-149">Mer information finns i `Enable-PSRemoting`.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-149">For more information, see `Enable-PSRemoting`.</span></span>

<span data-ttu-id="8d3d7-150">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-150">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="8d3d7-151">-Confirm</span><span class="sxs-lookup"><span data-stu-id="8d3d7-151">-Confirm</span></span>

<span data-ttu-id="8d3d7-152">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-152">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="8d3d7-153">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="8d3d7-153">-WhatIf</span></span>

<span data-ttu-id="8d3d7-154">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-154">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="8d3d7-155">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-155">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="8d3d7-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="8d3d7-156">CommonParameters</span></span>

<span data-ttu-id="8d3d7-157">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="8d3d7-158">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="8d3d7-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="8d3d7-159">INDATA</span><span class="sxs-lookup"><span data-stu-id="8d3d7-159">INPUTS</span></span>

### <span data-ttu-id="8d3d7-160">Microsoft. PowerShell. commands. PSSessionConfigurationCommands # PSSessionConfiguration, system. String</span><span class="sxs-lookup"><span data-stu-id="8d3d7-160">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration, System.String</span></span>

<span data-ttu-id="8d3d7-161">Du kan skicka ett konfigurations objekt för en session eller en sträng som innehåller namnet på en sessions konfiguration till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-161">You can pipe a session configuration object or a string that contains the name of a session configuration to this cmdlet.</span></span>

## <span data-ttu-id="8d3d7-162">UTDATA</span><span class="sxs-lookup"><span data-stu-id="8d3d7-162">OUTPUTS</span></span>

### <span data-ttu-id="8d3d7-163">Inga</span><span class="sxs-lookup"><span data-stu-id="8d3d7-163">None</span></span>

<span data-ttu-id="8d3d7-164">Denna cmdlet returnerar inga objekt.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-164">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="8d3d7-165">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="8d3d7-165">NOTES</span></span>

<span data-ttu-id="8d3d7-166">Den här cmdleten är endast tillgänglig på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="8d3d7-166">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="8d3d7-167">Om du vill använda denna cmdlet måste du starta PowerShell med alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="8d3d7-167">To use this cmdlet, you must start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="8d3d7-168">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="8d3d7-168">RELATED LINKS</span></span>

[<span data-ttu-id="8d3d7-169">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="8d3d7-169">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="8d3d7-170">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="8d3d7-170">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="8d3d7-171">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="8d3d7-171">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="8d3d7-172">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="8d3d7-172">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="8d3d7-173">Registrera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="8d3d7-173">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="8d3d7-174">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="8d3d7-174">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="8d3d7-175">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="8d3d7-175">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="8d3d7-176">Avregistrera-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="8d3d7-176">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="8d3d7-177">WSMan-Provider</span><span class="sxs-lookup"><span data-stu-id="8d3d7-177">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="8d3d7-178">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="8d3d7-178">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="8d3d7-179">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="8d3d7-179">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
