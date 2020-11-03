---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enable-pssessionconfiguration?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSSessionConfiguration
ms.openlocfilehash: 237fe83af05de7a97113deb95a831d8295c9f4c4
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262640"
---
# <span data-ttu-id="ab44b-103">Enable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ab44b-103">Enable-PSSessionConfiguration</span></span>

## <span data-ttu-id="ab44b-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="ab44b-104">SYNOPSIS</span></span>
<span data-ttu-id="ab44b-105">Aktiverar sessionsinställningar på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="ab44b-105">Enables the session configurations on the local computer.</span></span>

## <span data-ttu-id="ab44b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="ab44b-106">SYNTAX</span></span>

```
Enable-PSSessionConfiguration [[-Name] <String[]>] [-Force] [-SecurityDescriptorSddl <String>]
 [-SkipNetworkProfileCheck] [-NoServiceRestart] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="ab44b-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ab44b-107">DESCRIPTION</span></span>

<span data-ttu-id="ab44b-108">`Enable-PSSessionConfiguration`Cmdleten aktiverar registrerade sessionsinställningar som har inaktiverats, till exempel med hjälp av `Disable-PSSessionConfiguration` `Disable-PSRemoting` cmdletarna eller **AccessMode** -parametern för `Register-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="ab44b-108">The `Enable-PSSessionConfiguration` cmdlet enables registered session configurations that have been disabled, such as by using the `Disable-PSSessionConfiguration` or `Disable-PSRemoting` cmdlets, or the **AccessMode** parameter of `Register-PSSessionConfiguration`.</span></span> <span data-ttu-id="ab44b-109">Det här är en avancerad cmdlet som är avsedd att användas av system administratörer för att hantera konfigurationer för anpassade sessioner för sina användare.</span><span class="sxs-lookup"><span data-stu-id="ab44b-109">This is an advanced cmdlet that is designed to be used by system administrators to manage customized session configurations for their users.</span></span>

<span data-ttu-id="ab44b-110">Utan parametrar `Enable-PSSessionConfiguration` aktiverar **Microsoft. PowerShell** -konfigurationen, som är den standard konfiguration som används för sessioner.</span><span class="sxs-lookup"><span data-stu-id="ab44b-110">Without parameters, `Enable-PSSessionConfiguration` enables the **Microsoft.PowerShell** configuration, which is the default configuration that is used for sessions.</span></span>

<span data-ttu-id="ab44b-111">`Enable-PSSessionConfiguration` tar bort inställningen **Deny_All** från säkerhets beskrivningen för de berörda sessionerna, aktiverar den lyssnare som accepterar begär Anden på alla IP-adresser och startar om WinRM-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="ab44b-111">`Enable-PSSessionConfiguration` removes the **Deny_All** setting from the security descriptor of the affected session configurations, turns on the listener that accepts requests on any IP address, and restarts the WinRM service.</span></span> <span data-ttu-id="ab44b-112">Från och med PowerShell 3,0 `Enable-PSSessionConfiguration` anger även värdet för egenskapen **Enabled** för session Configuration ( `WSMan:\<computer>\PlugIn\<SessionConfigurationName>\Enabled` ) till true.</span><span class="sxs-lookup"><span data-stu-id="ab44b-112">Beginning in PowerShell 3.0, `Enable-PSSessionConfiguration` also sets the value of the **Enabled** property of the session configuration (`WSMan:\<computer>\PlugIn\<SessionConfigurationName>\Enabled`) to True.</span></span> <span data-ttu-id="ab44b-113">Men `Enable-PSSessionConfiguration` tar inte bort eller ändrar inställningen för säkerhets beskrivningen **Network_Deny_All** ( `AccessMode=Local` ) som endast tillåter användare av den lokala datorn att använda den för att konfigurera sessionen.</span><span class="sxs-lookup"><span data-stu-id="ab44b-113">However, `Enable-PSSessionConfiguration` does not remove or change the **Network_Deny_All** (`AccessMode=Local`) security descriptor setting that allows only users of the local computer to use to the session configuration.</span></span>

## <span data-ttu-id="ab44b-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="ab44b-114">EXAMPLES</span></span>

### <span data-ttu-id="ab44b-115">Exempel 1: återaktivera Standardsessionen</span><span class="sxs-lookup"><span data-stu-id="ab44b-115">Example 1: Re-enable the default session</span></span>

<span data-ttu-id="ab44b-116">I det här exemplet återaktiveras standardsessions konfigurationen för **Microsoft. PowerShell** på datorn.</span><span class="sxs-lookup"><span data-stu-id="ab44b-116">This example re-enables the **Microsoft.PowerShell** default session configuration on the computer.</span></span>

```powershell
Enable-PSSessionConfiguration
```

### <span data-ttu-id="ab44b-117">Exempel 2: återaktivera angivna sessioner</span><span class="sxs-lookup"><span data-stu-id="ab44b-117">Example 2: Re-enable specified sessions</span></span>

<span data-ttu-id="ab44b-118">I det här exemplet återaktiveras **MaintenanceShell** -och **AdminShell** på datorn.</span><span class="sxs-lookup"><span data-stu-id="ab44b-118">This example re-enables the **MaintenanceShell** and **AdminShell** session configurations on the computer.</span></span>

```powershell
Enable-PSSessionConfiguration -Name MaintenanceShell, AdminShell
```

### <span data-ttu-id="ab44b-119">Exempel 3: återaktivera alla sessioner</span><span class="sxs-lookup"><span data-stu-id="ab44b-119">Example 3: Re-enable the all sessions</span></span>

<span data-ttu-id="ab44b-120">I det här exemplet återaktiveras alla sessionsbaserade på datorn.</span><span class="sxs-lookup"><span data-stu-id="ab44b-120">This example re-enables all session configurations on the computer.</span></span> <span data-ttu-id="ab44b-121">Dessa kommandon är likvärdiga.</span><span class="sxs-lookup"><span data-stu-id="ab44b-121">These commands are equivalent.</span></span>
<span data-ttu-id="ab44b-122">Därför kan du använda antingen.</span><span class="sxs-lookup"><span data-stu-id="ab44b-122">Therefore, you can use either.</span></span>

```powershell
Enable-PSSessionConfiguration -Name *
Get-PSSessionConfiguration | Enable-PSSessionConfiguration
```

<span data-ttu-id="ab44b-123">`Enable-PSSessionConfiguration` genererar inget fel om du aktiverar en sessionshantering som redan är aktive rad.</span><span class="sxs-lookup"><span data-stu-id="ab44b-123">`Enable-PSSessionConfiguration` does not generate an error if you enable a session configuration that is already enabled.</span></span>

### <span data-ttu-id="ab44b-124">Exempel 4: återaktivera en session och ange en ny säkerhets Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ab44b-124">Example 4: Re-enable a session and specify a new security descriptor</span></span>

<span data-ttu-id="ab44b-125">I det här exemplet återaktiveras **MaintenanceShell** och en ny säkerhets beskrivning anges för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="ab44b-125">This example re-enables the **MaintenanceShell** session configuration and specifies a new security descriptor for the configuration.</span></span>

```powershell
$sddl = "O:NSG:BAD:P(A;;GXGWGR;;;BA)(A;;GAGR;;;S-1-5-21-123456789-188441444-3100496)S:P"
Enable-PSSessionConfiguration -Name MaintenanceShell -SecurityDescriptorSDDL $sddl
```

## <span data-ttu-id="ab44b-126">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="ab44b-126">PARAMETERS</span></span>

### <span data-ttu-id="ab44b-127">-Force</span><span class="sxs-lookup"><span data-stu-id="ab44b-127">-Force</span></span>

<span data-ttu-id="ab44b-128">Anger att cmdleten inte ber dig om bekräftelse och startar om WinRM-tjänsten utan att du behöver ange något.</span><span class="sxs-lookup"><span data-stu-id="ab44b-128">Indicates that the cmdlet does not prompt you for confirmation, and restarts the WinRM service without prompting.</span></span> <span data-ttu-id="ab44b-129">Att starta om tjänsten gör att konfigurations ändringen träder i kraft.</span><span class="sxs-lookup"><span data-stu-id="ab44b-129">Restarting the service makes the configuration change effective.</span></span>

<span data-ttu-id="ab44b-130">Om du vill förhindra en omstart och ignorera omstarts meddelandet använder du parametern **NoServiceRestart** .</span><span class="sxs-lookup"><span data-stu-id="ab44b-130">To prevent a restart and suppress the restart prompt, use the **NoServiceRestart** parameter.</span></span>

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

### <span data-ttu-id="ab44b-131">-Name</span><span class="sxs-lookup"><span data-stu-id="ab44b-131">-Name</span></span>

<span data-ttu-id="ab44b-132">Anger namnen på de sessionsinställningar som ska aktive ras.</span><span class="sxs-lookup"><span data-stu-id="ab44b-132">Specifies the names of session configurations to enable.</span></span> <span data-ttu-id="ab44b-133">Ange ett eller flera konfigurations namn.</span><span class="sxs-lookup"><span data-stu-id="ab44b-133">Enter one or more configuration names.</span></span>
<span data-ttu-id="ab44b-134">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="ab44b-134">Wildcard characters are permitted.</span></span>

<span data-ttu-id="ab44b-135">Du kan också skicka en sträng som innehåller ett konfigurations namn eller ett konfigurations objekt för session till `Enable-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="ab44b-135">You can also pipe a string that contains a configuration name or a session configuration object to `Enable-PSSessionConfiguration`.</span></span>

<span data-ttu-id="ab44b-136">Om du utelämnar den här parametern `Enable-PSSessionConfiguration` aktiverar **Microsoft. PowerShell** -sessionen.</span><span class="sxs-lookup"><span data-stu-id="ab44b-136">If you omit this parameter, `Enable-PSSessionConfiguration` enables the **Microsoft.PowerShell** session configuration.</span></span>

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

### <span data-ttu-id="ab44b-137">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="ab44b-137">-NoServiceRestart</span></span>

<span data-ttu-id="ab44b-138">Anger att cmdleten inte startar om tjänsten.</span><span class="sxs-lookup"><span data-stu-id="ab44b-138">Indicates that the cmdlet does not restart the service.</span></span>

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

### <span data-ttu-id="ab44b-139">-SecurityDescriptorSddl</span><span class="sxs-lookup"><span data-stu-id="ab44b-139">-SecurityDescriptorSddl</span></span>

<span data-ttu-id="ab44b-140">Anger en säkerhets Beskrivning där denna cmdlet ersätter säkerhets beskrivningen i konfigurationen av sessionen.</span><span class="sxs-lookup"><span data-stu-id="ab44b-140">Specifies a security descriptor with which this cmdlet replaces the security descriptor on the session configuration.</span></span>

<span data-ttu-id="ab44b-141">Om du utelämnar den här parametern `Enable-PSSessionConfiguration` tar endast bort neka alla objekt från säkerhets beskrivningen.</span><span class="sxs-lookup"><span data-stu-id="ab44b-141">If you omit this parameter, `Enable-PSSessionConfiguration` only deletes the deny all item from the security descriptor.</span></span>

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

### <span data-ttu-id="ab44b-142">-SkipNetworkProfileCheck</span><span class="sxs-lookup"><span data-stu-id="ab44b-142">-SkipNetworkProfileCheck</span></span>

<span data-ttu-id="ab44b-143">Anger att denna cmdlet aktiverar sessionen när datorn finns i ett offentligt nätverk.</span><span class="sxs-lookup"><span data-stu-id="ab44b-143">Indicates that this cmdlet enables the session configuration when the computer is on a public network.</span></span> <span data-ttu-id="ab44b-144">Med den här parametern kan du använda en brand Väggs regel för offentliga nätverk som endast tillåter fjärråtkomst från datorer i samma lokala undernät.</span><span class="sxs-lookup"><span data-stu-id="ab44b-144">This parameter enables a firewall rule for public networks that allows remote access only from computers in the same local subnet.</span></span> <span data-ttu-id="ab44b-145">Som standard `Enable-PSSessionConfiguration` går det inte att utföra i ett offentligt nätverk.</span><span class="sxs-lookup"><span data-stu-id="ab44b-145">By default, `Enable-PSSessionConfiguration` fails on a public network.</span></span>

<span data-ttu-id="ab44b-146">Den här parametern är avsedd för klient versioner av Windows operativ system.</span><span class="sxs-lookup"><span data-stu-id="ab44b-146">This parameter is designed for client versions of the Windows operating system.</span></span> <span data-ttu-id="ab44b-147">Server versioner av Windows operativ system har en lokal brand Väggs regel för offentliga nätverk.</span><span class="sxs-lookup"><span data-stu-id="ab44b-147">Server versions of the Windows operating system have a local subnet firewall rule for public networks.</span></span> <span data-ttu-id="ab44b-148">Men om den lokala brand Väggs regeln är inaktive rad på en server version av Windows-operativsystemet, aktive ras den här parametern igen.</span><span class="sxs-lookup"><span data-stu-id="ab44b-148">However, if the local subnet firewall rule is disabled on a server version of the Windows operating system, this parameter re-enables it.</span></span>

<span data-ttu-id="ab44b-149">Om du vill ta bort den lokala under näts begränsningen och aktivera fjärråtkomst från alla platser i offentliga nätverk använder du `Set-NetFirewallRule` cmdleten i modulen netsecurity.</span><span class="sxs-lookup"><span data-stu-id="ab44b-149">To remove the local subnet restriction and enable remote access from all locations on public networks, use the `Set-NetFirewallRule` cmdlet in the NetSecurity module.</span></span> <span data-ttu-id="ab44b-150">Mer information finns i `Enable-PSRemoting`.</span><span class="sxs-lookup"><span data-stu-id="ab44b-150">For more information, see `Enable-PSRemoting`.</span></span>

<span data-ttu-id="ab44b-151">Den här parametern introducerades i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="ab44b-151">This parameter was introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="ab44b-152">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ab44b-152">-Confirm</span></span>

<span data-ttu-id="ab44b-153">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="ab44b-153">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="ab44b-154">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ab44b-154">-WhatIf</span></span>

<span data-ttu-id="ab44b-155">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="ab44b-155">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="ab44b-156">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="ab44b-156">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="ab44b-157">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="ab44b-157">CommonParameters</span></span>

<span data-ttu-id="ab44b-158">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="ab44b-158">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="ab44b-159">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ab44b-159">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="ab44b-160">INDATA</span><span class="sxs-lookup"><span data-stu-id="ab44b-160">INPUTS</span></span>

### <span data-ttu-id="ab44b-161">Microsoft. PowerShell. commands. PSSessionConfigurationCommands # PSSessionConfiguration, system. String</span><span class="sxs-lookup"><span data-stu-id="ab44b-161">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration, System.String</span></span>

<span data-ttu-id="ab44b-162">Du kan skicka ett konfigurations objekt för en session eller en sträng som innehåller namnet på en sessions konfiguration till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ab44b-162">You can pipe a session configuration object or a string that contains the name of a session configuration to this cmdlet.</span></span>

## <span data-ttu-id="ab44b-163">UTDATA</span><span class="sxs-lookup"><span data-stu-id="ab44b-163">OUTPUTS</span></span>

### <span data-ttu-id="ab44b-164">Inget</span><span class="sxs-lookup"><span data-stu-id="ab44b-164">None</span></span>

<span data-ttu-id="ab44b-165">Denna cmdlet returnerar inga objekt.</span><span class="sxs-lookup"><span data-stu-id="ab44b-165">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="ab44b-166">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="ab44b-166">NOTES</span></span>

<span data-ttu-id="ab44b-167">Om du vill använda denna cmdlet måste du starta PowerShell med alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="ab44b-167">To use this cmdlet, you must start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="ab44b-168">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="ab44b-168">RELATED LINKS</span></span>

[<span data-ttu-id="ab44b-169">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ab44b-169">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="ab44b-170">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ab44b-170">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="ab44b-171">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="ab44b-171">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="ab44b-172">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="ab44b-172">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="ab44b-173">Registrera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ab44b-173">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="ab44b-174">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ab44b-174">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="ab44b-175">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="ab44b-175">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="ab44b-176">Avregistrera-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="ab44b-176">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="ab44b-177">WSMan-Provider</span><span class="sxs-lookup"><span data-stu-id="ab44b-177">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="ab44b-178">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="ab44b-178">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="ab44b-179">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="ab44b-179">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
