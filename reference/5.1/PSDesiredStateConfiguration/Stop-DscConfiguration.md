---
external help file: Stop-DscConfiguration.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 08/19/2019
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/stop-dscconfiguration?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-DscConfiguration
ms.openlocfilehash: 93c8585ae948dfa360a2ae8e2563670de8fd6e93
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264777"
---
# <span data-ttu-id="162dc-103">Stop-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="162dc-103">Stop-DscConfiguration</span></span>

## <span data-ttu-id="162dc-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="162dc-104">SYNOPSIS</span></span>
<span data-ttu-id="162dc-105">Stoppar ett konfigurations jobb som kör.</span><span class="sxs-lookup"><span data-stu-id="162dc-105">Stops a configuration job that is running.</span></span>

## <span data-ttu-id="162dc-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="162dc-106">SYNTAX</span></span>

### <span data-ttu-id="162dc-107">Alla</span><span class="sxs-lookup"><span data-stu-id="162dc-107">All</span></span>

```
Stop-DscConfiguration [-Force] [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob]
 [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="162dc-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="162dc-108">DESCRIPTION</span></span>

<span data-ttu-id="162dc-109">`Stop-DscConfiguration`Cmdleten stoppar ett konfigurations jobb som kör.</span><span class="sxs-lookup"><span data-stu-id="162dc-109">The `Stop-DscConfiguration` cmdlet stops a configuration job that is running.</span></span> <span data-ttu-id="162dc-110">Ange vilka datorer som denna cmdlet gäller med hjälp av Common Information Model (CIM)-sessioner.</span><span class="sxs-lookup"><span data-stu-id="162dc-110">Specify which computers this cmdlet applies to by using Common Information Model (CIM) sessions.</span></span> <span data-ttu-id="162dc-111">Om inget konfigurations jobb körs returnerar denna cmdlet ett varnings meddelande.</span><span class="sxs-lookup"><span data-stu-id="162dc-111">If there's no configuration job running, this cmdlet returns a warning message.</span></span>

<span data-ttu-id="162dc-112">`Stop-DscConfiguration` är bara tillgängligt som en del av den [samlade uppdateringen November 2014 för Windows RT 8,1, Windows 8,1 och Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) från Microsoft Support-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="162dc-112">`Stop-DscConfiguration` is only available as part of the [November 2014 update rollup for Windows RT 8.1, Windows 8.1, and Windows Server 2012 R2](https://support.microsoft.com/kb/3000850) from the Microsoft Support library.</span></span> <span data-ttu-id="162dc-113">Innan du använder den här cmdleten kan du läsa informationen i [Nyheter i Windows PowerShell 5,0](/powershell/scripting/whats-new/What-s-New-in-Windows-PowerShell-50)</span><span class="sxs-lookup"><span data-stu-id="162dc-113">Before you use this cmdlet, review the information in [What's New in Windows PowerShell 5.0](/powershell/scripting/whats-new/What-s-New-in-Windows-PowerShell-50)</span></span>

## <span data-ttu-id="162dc-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="162dc-114">EXAMPLES</span></span>

### <span data-ttu-id="162dc-115">Exempel 1: stoppa ett konfigurations jobb</span><span class="sxs-lookup"><span data-stu-id="162dc-115">Example 1: Stop a configuration job</span></span>

<span data-ttu-id="162dc-116">I det här exemplet skapas en CIM-session med hjälp av `New-CimSession` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="162dc-116">In this example, a CIM session is created using the `New-CimSession` cmdlet.</span></span> <span data-ttu-id="162dc-117">**CimSession** -objektet används för att stoppa körningen av ett konfigurations jobb som körs.</span><span class="sxs-lookup"><span data-stu-id="162dc-117">The **CimSession** object is used to stop a running configuration job.</span></span>

```powershell
$Session = New-CimSession -ComputerName Server01 -Credential ACCOUNTS\User01
Stop-DscConfiguration -CimSession $Session
```

<span data-ttu-id="162dc-118">`New-CimSession` använder parametern **computername** för att ange Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="162dc-118">`New-CimSession` uses the **ComputerName** parameter to specify the Server01 computer.</span></span> <span data-ttu-id="162dc-119">Parametern **Credential** anger användar kontot.</span><span class="sxs-lookup"><span data-stu-id="162dc-119">The **Credential** parameter specifies the user account.</span></span> <span data-ttu-id="162dc-120">**CimSession** -objektet lagras i `$Session` variabeln.</span><span class="sxs-lookup"><span data-stu-id="162dc-120">The **CimSession** object is stored in the `$Session` variable.</span></span> <span data-ttu-id="162dc-121">När kommandot körs uppmanas du att ange användar kontots lösen ord.</span><span class="sxs-lookup"><span data-stu-id="162dc-121">When the command is run, you're prompted for the user account's password.</span></span>

<span data-ttu-id="162dc-122">`Stop-DscConfiguration` använder parametern **CimSession** och objektet som är lagrat i `$Session` för att stoppa konfigurations jobbet.</span><span class="sxs-lookup"><span data-stu-id="162dc-122">`Stop-DscConfiguration` uses the **CimSession** parameter and the object stored in `$Session` to stop the configuration job.</span></span>

## <span data-ttu-id="162dc-123">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="162dc-123">PARAMETERS</span></span>

### <span data-ttu-id="162dc-124">– AsJob</span><span class="sxs-lookup"><span data-stu-id="162dc-124">-AsJob</span></span>

<span data-ttu-id="162dc-125">Anger att denna cmdlet kör kommandot som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="162dc-125">Indicates that this cmdlet runs the command as a background job.</span></span> <span data-ttu-id="162dc-126">Mer information om PowerShell-bakgrunds jobb finns i [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) och [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="162dc-126">For more information about PowerShell background jobs, see [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md) and [about_Remote_Jobs](../Microsoft.PowerShell.Core/About/about_Remote_Jobs.md).</span></span>

<span data-ttu-id="162dc-127">Om du vill använda parametern **AsJob** måste lokala datorer och fjärrdatorer konfigureras för fjärr kommunikation.</span><span class="sxs-lookup"><span data-stu-id="162dc-127">To use the **AsJob** parameter, the local and remote computers must be configured for remoting.</span></span> <span data-ttu-id="162dc-128">I Windows Vista och senare versioner av operativ systemet Windows måste du öppna PowerShell med alternativet **Kör som administratör** .</span><span class="sxs-lookup"><span data-stu-id="162dc-128">On Windows Vista and later versions of the Windows operating system, you must open PowerShell with the **Run as administrator** option.</span></span> <span data-ttu-id="162dc-129">Mer information finns i [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span><span class="sxs-lookup"><span data-stu-id="162dc-129">For more information, see [about_Remote_Requirements](../Microsoft.PowerShell.Core/About/about_Remote_Requirements.md).</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="162dc-130">– CimSession</span><span class="sxs-lookup"><span data-stu-id="162dc-130">-CimSession</span></span>

<span data-ttu-id="162dc-131">Kör cmdleten i en fjärran sluten session eller på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="162dc-131">Runs the cmdlet in a remote session or on a remote computer.</span></span> <span data-ttu-id="162dc-132">Ange ett dator namn eller ett sessionsobjekt, till exempel utdata från `New-CimSession` eller `Get-CimSession` .</span><span class="sxs-lookup"><span data-stu-id="162dc-132">Enter a computer name or a session object, such as the output from `New-CimSession` or `Get-CimSession`.</span></span>

```yaml
Type: Microsoft.Management.Infrastructure.CimSession[]
Parameter Sets: (All)
Aliases: Session

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="162dc-133">-Confirm</span><span class="sxs-lookup"><span data-stu-id="162dc-133">-Confirm</span></span>

<span data-ttu-id="162dc-134">`Stop-DscConfiguration` har inte stöd för **Confirm** -parametern.</span><span class="sxs-lookup"><span data-stu-id="162dc-134">`Stop-DscConfiguration` doesn't support the **Confirm** parameter.</span></span> <span data-ttu-id="162dc-135">Om parametern **Confirm** används visas ett fel.</span><span class="sxs-lookup"><span data-stu-id="162dc-135">If the **Confirm** parameter is used, an error is displayed.</span></span>

<span data-ttu-id="162dc-136">För PowerShell-cmdletar som har stöd för **Bekräfta** kan du med hjälp av parametern fråga dig om du vill verifiera innan ett kommando körs.</span><span class="sxs-lookup"><span data-stu-id="162dc-136">For PowerShell cmdlets that support **Confirm** , using the parameter prompts you for verification before a command is run.</span></span>

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

### <span data-ttu-id="162dc-137">-Force</span><span class="sxs-lookup"><span data-stu-id="162dc-137">-Force</span></span>

<span data-ttu-id="162dc-138">Tvingar kommandot att köras utan att fråga användaren om bekräftelse.</span><span class="sxs-lookup"><span data-stu-id="162dc-138">Forces the command to run without asking for user confirmation.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="162dc-139">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="162dc-139">-ThrottleLimit</span></span>

<span data-ttu-id="162dc-140">Anger det maximala antalet samtidiga åtgärder som kan upprättas för att köra cmdleten.</span><span class="sxs-lookup"><span data-stu-id="162dc-140">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>

<span data-ttu-id="162dc-141">Om den här parametern utelämnas eller värdet `0` anges, beräknar PowerShell en optimal begränsnings gräns baserat på antalet CIM-cmdletar som körs på datorn.</span><span class="sxs-lookup"><span data-stu-id="162dc-141">If this parameter is omitted or a value of `0` is entered, PowerShell calculates an optimum throttle limit based on the number of CIM cmdlets that are running on the computer.</span></span> <span data-ttu-id="162dc-142">Begränsnings gränsen gäller endast för den aktuella cmdleten, inte sessionen eller till datorn.</span><span class="sxs-lookup"><span data-stu-id="162dc-142">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="162dc-143">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="162dc-143">-WhatIf</span></span>

<span data-ttu-id="162dc-144">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="162dc-144">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="162dc-145">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="162dc-145">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="162dc-146">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="162dc-146">CommonParameters</span></span>

<span data-ttu-id="162dc-147">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="162dc-147">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="162dc-148">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="162dc-148">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="162dc-149">INDATA</span><span class="sxs-lookup"><span data-stu-id="162dc-149">INPUTS</span></span>

### <span data-ttu-id="162dc-150">Inget</span><span class="sxs-lookup"><span data-stu-id="162dc-150">None</span></span>

## <span data-ttu-id="162dc-151">UTDATA</span><span class="sxs-lookup"><span data-stu-id="162dc-151">OUTPUTS</span></span>

### <span data-ttu-id="162dc-152">Inget</span><span class="sxs-lookup"><span data-stu-id="162dc-152">None</span></span>

## <span data-ttu-id="162dc-153">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="162dc-153">NOTES</span></span>

## <span data-ttu-id="162dc-154">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="162dc-154">RELATED LINKS</span></span>

[<span data-ttu-id="162dc-155">Get-CimSession</span><span class="sxs-lookup"><span data-stu-id="162dc-155">Get-CimSession</span></span>](../CimCmdlets/Get-CimSession.md)

[<span data-ttu-id="162dc-156">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="162dc-156">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="162dc-157">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="162dc-157">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="162dc-158">New-CimSession</span><span class="sxs-lookup"><span data-stu-id="162dc-158">New-CimSession</span></span>](../CimCmdlets/New-CimSession.md)

[<span data-ttu-id="162dc-159">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="162dc-159">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="162dc-160">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="162dc-160">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="162dc-161">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="162dc-161">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)

[<span data-ttu-id="162dc-162">Uppdatera – DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="162dc-162">Update-DscConfiguration</span></span>](Update-DscConfiguration.md)

[<span data-ttu-id="162dc-163">Översikt över önskad tillstånds konfiguration i Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="162dc-163">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/overview)
