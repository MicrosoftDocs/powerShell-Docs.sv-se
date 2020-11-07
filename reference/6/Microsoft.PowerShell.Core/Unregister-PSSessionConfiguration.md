---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 03/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/unregister-pssessionconfiguration?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-PSSessionConfiguration
ms.openlocfilehash: f9cc2f83ec0fca1c957c670e13ac7b455c322adb
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94345355"
---
# <span data-ttu-id="5f111-103">Unregister-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="5f111-103">Unregister-PSSessionConfiguration</span></span>

## <span data-ttu-id="5f111-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="5f111-104">SYNOPSIS</span></span>
<span data-ttu-id="5f111-105">Tar bort registrerade sessionsbaserade från datorn.</span><span class="sxs-lookup"><span data-stu-id="5f111-105">Deletes registered session configurations from the computer.</span></span>

## <span data-ttu-id="5f111-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5f111-106">SYNTAX</span></span>

```
Unregister-PSSessionConfiguration [-Name] <String> [-Force] [-NoServiceRestart] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="5f111-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="5f111-107">DESCRIPTION</span></span>

<span data-ttu-id="5f111-108">`Unregister-PSSessionConfiguration`Cmdleten tar bort registrerade sessionsbaserade från datorn.</span><span class="sxs-lookup"><span data-stu-id="5f111-108">The `Unregister-PSSessionConfiguration` cmdlet deletes registered session configurations from the computer.</span></span> <span data-ttu-id="5f111-109">Denna cmdlet är utformad för att system administratörer ska kunna hantera konfigurationer för anpassade sessioner för användare.</span><span class="sxs-lookup"><span data-stu-id="5f111-109">This cmdlet is designed for system administrators to manage customized session configurations for users.</span></span>

<span data-ttu-id="5f111-110">För att ändringen ska börja gälla `Unregister-PSSessionConfiguration` startar om **WinRM** -tjänsten.</span><span class="sxs-lookup"><span data-stu-id="5f111-110">To make the change effective, `Unregister-PSSessionConfiguration` restarts the **WinRM** service.</span></span> <span data-ttu-id="5f111-111">För att förhindra omstarten anger du parametern **NoServiceRestart** .</span><span class="sxs-lookup"><span data-stu-id="5f111-111">To prevent the restart, specify the **NoServiceRestart** parameter.</span></span>

<span data-ttu-id="5f111-112">Om du av misstag tar bort standard konfigurationerna för **Microsoft. PowerShell** eller **Microsoft. PowerShell32** använder du `Enable-PSRemoting` cmdleten för att återställa dem.</span><span class="sxs-lookup"><span data-stu-id="5f111-112">If you accidentally delete the default **Microsoft.PowerShell** or **Microsoft.PowerShell32** session configurations, use the `Enable-PSRemoting` cmdlet to restore them.</span></span> <span data-ttu-id="5f111-113">Mer information finns i [about_Session_Configurations](About/about_Session_Configurations.md).</span><span class="sxs-lookup"><span data-stu-id="5f111-113">For more information, see [about_Session_Configurations](About/about_Session_Configurations.md).</span></span>

## <span data-ttu-id="5f111-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="5f111-114">EXAMPLES</span></span>

### <span data-ttu-id="5f111-115">Exempel 1: ta bort en konfiguration av sessionen</span><span class="sxs-lookup"><span data-stu-id="5f111-115">Example 1: Delete a session configuration</span></span>

<span data-ttu-id="5f111-116">I det här exemplet tas konfigurationen för **MaintenanceShell** -sessionen bort från datorn.</span><span class="sxs-lookup"><span data-stu-id="5f111-116">This example deletes the **MaintenanceShell** session configuration from the computer.</span></span>

```powershell
Unregister-PSSessionConfiguration -Name "MaintenanceShell"
```

### <span data-ttu-id="5f111-117">Exempel 2: ta bort en sessions konfiguration och starta om WinRM-tjänsten</span><span class="sxs-lookup"><span data-stu-id="5f111-117">Example 2: Delete a session configuration and restart the WinRM service</span></span>

<span data-ttu-id="5f111-118">I det här exemplet tar vi bort **MaintenanceShell** -konfigurationen och startar om WinRM-tjänsten.</span><span class="sxs-lookup"><span data-stu-id="5f111-118">In this example, we delete the **MaintenanceShell** configuration and restart the WinRM service.</span></span> <span data-ttu-id="5f111-119">Parametern **Force** undertrycker alla användar meddelanden för att starta om **WinRM** -tjänsten utan att fråga.</span><span class="sxs-lookup"><span data-stu-id="5f111-119">The **Force** parameter suppresses all user messages to restart the **WinRM** service without prompting.</span></span>

```powershell
Unregister-PSSessionConfiguration -Name MaintenanceShell -Force
```

### <span data-ttu-id="5f111-120">Exempel 3: ta bort alla konfigurationer för sessioner</span><span class="sxs-lookup"><span data-stu-id="5f111-120">Example 3: Delete all session configurations</span></span>

<span data-ttu-id="5f111-121">I det här exemplet visas två sätt att ta bort alla sessionsinställningar på datorn.</span><span class="sxs-lookup"><span data-stu-id="5f111-121">This examples show two ways to delete all the session configurations on the computer.</span></span> <span data-ttu-id="5f111-122">Båda kommandona har samma resultat och kan användas utbytbart.</span><span class="sxs-lookup"><span data-stu-id="5f111-122">Both commands have the same effect and can be used interchangeably.</span></span>

```
Unregister-PSSessionConfiguration -Name *
Get-PSSessionConfiguration -Name * | Unregister-PSSessionConfiguration
```

### <span data-ttu-id="5f111-123">Exempel 4: avregistrera utan omstart</span><span class="sxs-lookup"><span data-stu-id="5f111-123">Example 4: Unregister without a restart</span></span>

<span data-ttu-id="5f111-124">Det här exemplet visar effekterna av att använda parametern **NoServiceRestart** för att förhindra en omstart av tjänsten som skulle störa eventuella sessioner på datorn.</span><span class="sxs-lookup"><span data-stu-id="5f111-124">This example shows the effect of using the **NoServiceRestart** parameter to prevent a service restart that would disrupt any sessions on the computer.</span></span>

```
PS> Unregister-PSSessionConfiguration -Name "MaintenanceShell" -NoServiceRestart
PS> Get-PSSessionConfiguration -Name "MaintenanceShell"

Get-PSSessionConfiguration -Name MaintenanceShell : No Session Configuration matches criteria "MaintenanceShell".
+ CategoryInfo          : NotSpecified: (:) [Write-Error], WriteErrorException
+ FullyQualifiedErrorId : Microsoft.PowerShell.Commands.WriteErrorException

PS> New-PSSession -ConfigurationName "MaintenanceShell"

Id Name      ComputerName    State    Configuration         Availability
-- ----      ------------    -----    -------------         ------------
1 Session1  localhost       Opened   MaintenanceShell      Available

PS> Restart-Service winrm
PS> New-PSSession -ConfigurationName MaintenanceShell

[localhost] Connecting to remote server failed with the following error message :
 The WS-Management service cannot process the request.
 The resource URI (http://schemas.microsoft.com/powershell/MaintenanceShell) was not found in the WS-Management catalog.
 The catalog contains the metadata that describes resources, or logical endpoints.
 For more information, see the about_Remote_Troubleshooting Help topic.
 + CategoryInfo          : OpenError: (System.Manageme....RemoteRunspace:RemoteRunspace) [], PSRemotingTransportException
 + FullyQualifiedErrorId : PSSessionOpenFailed
```

<span data-ttu-id="5f111-125">`Unregister-PSSessionConfiguration`Konfiguration av **MaintenanceShell** -sessionen tas bort.</span><span class="sxs-lookup"><span data-stu-id="5f111-125">The `Unregister-PSSessionConfiguration` deletes the **MaintenanceShell** session configuration.</span></span>
<span data-ttu-id="5f111-126">Men eftersom kommandot använder parametern **NoServiceRestart** startas inte **WinRM** -tjänsten om och ändringen är inte helt effektiv.</span><span class="sxs-lookup"><span data-stu-id="5f111-126">However, because the command uses the **NoServiceRestart** parameter, the **WinRM** service is not restarted and the change is not yet completely effective.</span></span>

<span data-ttu-id="5f111-127">Sedan försöker du `Get-PSSessionConfiguration` Hämta **MaintenanceShell** -sessionen.</span><span class="sxs-lookup"><span data-stu-id="5f111-127">Next, the `Get-PSSessionConfiguration` tries to get the **MaintenanceShell** session.</span></span> <span data-ttu-id="5f111-128">Eftersom sessionen har tagits bort från WS-Management resurs tabell `Get-PSSessionConfiguration` kan den inte returnera den.</span><span class="sxs-lookup"><span data-stu-id="5f111-128">Because the session has been removed from the WS-Management resource table, `Get-PSSessionConfiguration` cannot return it.</span></span>

<span data-ttu-id="5f111-129">`New-PSSession`Cmdleten skapar en session med hjälp av **MaintenanceShell** -konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="5f111-129">The `New-PSSession` cmdlet creates a session using the **MaintenanceShell** configuration.</span></span> <span data-ttu-id="5f111-130">Kommandot lyckades.</span><span class="sxs-lookup"><span data-stu-id="5f111-130">The command succeeds.</span></span> <span data-ttu-id="5f111-131">Därefter startar vi om **WinRM** -tjänsten.</span><span class="sxs-lookup"><span data-stu-id="5f111-131">Next, we restart the **WinRM** service.</span></span>

<span data-ttu-id="5f111-132">Slutligen `New-PSSession` försöker cmdleten skapa en session som använder **MaintenanceShell** -konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="5f111-132">Finally, the `New-PSSession` cmdlet tries to create a session that uses the **MaintenanceShell** configuration.</span></span> <span data-ttu-id="5f111-133">Den här gången Miss lyckas sessionen eftersom **MaintenanceShell** -konfigurationen togs bort när WinRM-tjänsten startades om.</span><span class="sxs-lookup"><span data-stu-id="5f111-133">This time, the session fails because the **MaintenanceShell** configuration was deleted when the WinRM service restarted.</span></span>

## <span data-ttu-id="5f111-134">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="5f111-134">PARAMETERS</span></span>

### <span data-ttu-id="5f111-135">-Force</span><span class="sxs-lookup"><span data-stu-id="5f111-135">-Force</span></span>

<span data-ttu-id="5f111-136">Anger att cmdleten inte ber dig om bekräftelse och startar om **WinRM** -tjänsten utan att du behöver ange något.</span><span class="sxs-lookup"><span data-stu-id="5f111-136">Indicates that the cmdlet does not prompt you for confirmation, and restarts the **WinRM** service without prompting.</span></span> <span data-ttu-id="5f111-137">Att starta om tjänsten gör att konfigurations ändringen träder i kraft.</span><span class="sxs-lookup"><span data-stu-id="5f111-137">Restarting the service makes the configuration change effective.</span></span>

<span data-ttu-id="5f111-138">Om du vill förhindra en omstart och ignorera omstarts meddelandet använder du parametern **NoServiceRestart** .</span><span class="sxs-lookup"><span data-stu-id="5f111-138">To prevent a restart and suppress the restart prompt, use the **NoServiceRestart** parameter.</span></span>

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

### <span data-ttu-id="5f111-139">-Name</span><span class="sxs-lookup"><span data-stu-id="5f111-139">-Name</span></span>

<span data-ttu-id="5f111-140">Anger namnen på de sessionsinställningar som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="5f111-140">Specifies the names of the session configurations to delete.</span></span> <span data-ttu-id="5f111-141">Ange ett konfigurations namn för sessionen eller ett namn mönster för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="5f111-141">Enter one session configuration name or a configuration name pattern.</span></span> <span data-ttu-id="5f111-142">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="5f111-142">Wildcard characters are permitted.</span></span> <span data-ttu-id="5f111-143">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="5f111-143">This parameter is required.</span></span>

<span data-ttu-id="5f111-144">Du kan också skicka en session med konfigurationer till `Unregister-PSSessionConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="5f111-144">You can also pipe a session configurations to `Unregister-PSSessionConfiguration`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="5f111-145">-NoServiceRestart</span><span class="sxs-lookup"><span data-stu-id="5f111-145">-NoServiceRestart</span></span>

<span data-ttu-id="5f111-146">Anger att denna cmdlet inte startar om **WinRM** -tjänsten och förhindrar uppmaningen att starta om tjänsten.</span><span class="sxs-lookup"><span data-stu-id="5f111-146">Indicates that this cmdlet does not restart the **WinRM** service, and suppresses the prompt to restart the service.</span></span>

<span data-ttu-id="5f111-147">När du kör ett `Unregister-PSSessionConfiguration` kommando uppmanas du som standard att starta om **WinRM** -tjänsten för att ändringen ska börja gälla.</span><span class="sxs-lookup"><span data-stu-id="5f111-147">By default, when you run an `Unregister-PSSessionConfiguration` command, you are prompted to restart the **WinRM** service to make the change effective.</span></span> <span data-ttu-id="5f111-148">Innan **WinRM** -tjänsten har startats om kan användarna fortfarande använda den oregistrerade sessionen, trots att `Get-PSSessionConfiguration` den inte hittar den.</span><span class="sxs-lookup"><span data-stu-id="5f111-148">Until the **WinRM** service is restarted, users can still use the unregistered session configuration, even though `Get-PSSessionConfiguration` does not find it.</span></span>

<span data-ttu-id="5f111-149">Om du vill starta om **WinRM** -tjänsten utan att begära det anger du parametern **Force** .</span><span class="sxs-lookup"><span data-stu-id="5f111-149">To restart the **WinRM** service without prompting, specify the **Force** parameter.</span></span> <span data-ttu-id="5f111-150">Om du vill starta om **WinRM** -tjänsten manuellt använder du `Restart-Service` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5f111-150">To restart the **WinRM** service manually, use the `Restart-Service` cmdlet.</span></span>

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

### <span data-ttu-id="5f111-151">-Confirm</span><span class="sxs-lookup"><span data-stu-id="5f111-151">-Confirm</span></span>

<span data-ttu-id="5f111-152">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5f111-152">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="5f111-153">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="5f111-153">-WhatIf</span></span>

<span data-ttu-id="5f111-154">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="5f111-154">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="5f111-155">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="5f111-155">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="5f111-156">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5f111-156">CommonParameters</span></span>

<span data-ttu-id="5f111-157">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5f111-157">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5f111-158">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5f111-158">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5f111-159">INDATA</span><span class="sxs-lookup"><span data-stu-id="5f111-159">INPUTS</span></span>

### <span data-ttu-id="5f111-160">Microsoft. PowerShell. commands. PSSessionConfigurationCommands # PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="5f111-160">Microsoft.PowerShell.Commands.PSSessionConfigurationCommands#PSSessionConfiguration</span></span>

<span data-ttu-id="5f111-161">Du kan skicka vidare ett konfigurations objekt `Get-PSSessionConfiguration` för sessionen från till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5f111-161">You can pipe a session configuration object from `Get-PSSessionConfiguration` to this cmdlet.</span></span>

## <span data-ttu-id="5f111-162">UTDATA</span><span class="sxs-lookup"><span data-stu-id="5f111-162">OUTPUTS</span></span>

### <span data-ttu-id="5f111-163">Inget</span><span class="sxs-lookup"><span data-stu-id="5f111-163">None</span></span>

<span data-ttu-id="5f111-164">Denna cmdlet returnerar inga objekt.</span><span class="sxs-lookup"><span data-stu-id="5f111-164">This cmdlet does not return any objects.</span></span>

## <span data-ttu-id="5f111-165">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="5f111-165">NOTES</span></span>

<span data-ttu-id="5f111-166">Den här cmdleten är endast tillgänglig på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="5f111-166">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="5f111-167">Om du vill köra denna cmdlet måste du starta PowerShell med alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="5f111-167">To run this cmdlet you must start PowerShell by using the **Run as administrator** option.</span></span>

## <span data-ttu-id="5f111-168">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="5f111-168">RELATED LINKS</span></span>

[<span data-ttu-id="5f111-169">Disable-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="5f111-169">Disable-PSSessionConfiguration</span></span>](Disable-PSSessionConfiguration.md)

[<span data-ttu-id="5f111-170">Aktivera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="5f111-170">Enable-PSSessionConfiguration</span></span>](Enable-PSSessionConfiguration.md)

[<span data-ttu-id="5f111-171">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="5f111-171">Get-PSSessionConfiguration</span></span>](Get-PSSessionConfiguration.md)

[<span data-ttu-id="5f111-172">New-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="5f111-172">New-PSSessionConfigurationFile</span></span>](New-PSSessionConfigurationFile.md)

[<span data-ttu-id="5f111-173">New-PSSessionOption</span><span class="sxs-lookup"><span data-stu-id="5f111-173">New-PSSessionOption</span></span>](New-PSSessionOption.md)

[<span data-ttu-id="5f111-174">Registrera – PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="5f111-174">Register-PSSessionConfiguration</span></span>](Register-PSSessionConfiguration.md)

[<span data-ttu-id="5f111-175">Set-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="5f111-175">Set-PSSessionConfiguration</span></span>](Set-PSSessionConfiguration.md)

[<span data-ttu-id="5f111-176">Test-PSSessionConfigurationFile</span><span class="sxs-lookup"><span data-stu-id="5f111-176">Test-PSSessionConfigurationFile</span></span>](Test-PSSessionConfigurationFile.md)

[<span data-ttu-id="5f111-177">Avregistrera-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="5f111-177">Unregister-PSSessionConfiguration</span></span>](Unregister-PSSessionConfiguration.md)

[<span data-ttu-id="5f111-178">WSMan-Provider</span><span class="sxs-lookup"><span data-stu-id="5f111-178">WSMan Provider</span></span>](../Microsoft.WsMan.Management/About/about_WSMan_Provider.md)

[<span data-ttu-id="5f111-179">about_Session_Configurations</span><span class="sxs-lookup"><span data-stu-id="5f111-179">about_Session_Configurations</span></span>](About/about_Session_Configurations.md)

[<span data-ttu-id="5f111-180">about_Session_Configuration_Files</span><span class="sxs-lookup"><span data-stu-id="5f111-180">about_Session_Configuration_Files</span></span>](About/about_Session_Configuration_Files.md)
