---
external help file: Enable-DscDebug.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/enable-dscdebug?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-DscDebug
ms.openlocfilehash: 136481c5a1945c3d5cbd1ca7fc8ce5f580c39b0f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266079"
---
# <span data-ttu-id="47ff0-103">Enable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="47ff0-103">Enable-DscDebug</span></span>

## <span data-ttu-id="47ff0-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="47ff0-104">SYNOPSIS</span></span>
<span data-ttu-id="47ff0-105">Startar fel sökning av alla DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="47ff0-105">Starts debugging of all DSC resources.</span></span>

## <span data-ttu-id="47ff0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="47ff0-106">SYNTAX</span></span>

```
Enable-DscDebug [-BreakAll] [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="47ff0-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="47ff0-107">DESCRIPTION</span></span>
<span data-ttu-id="47ff0-108">Cmdlet: en **Enable-DscDebug** aktiverar Windows PowerShell-resurs fel sökning för önskad tillstånds konfiguration (DSC) av DSC-motorn, som även kallas lokal Configuration Manager (LCM).</span><span class="sxs-lookup"><span data-stu-id="47ff0-108">The **Enable-DscDebug** cmdlet enables Windows PowerShell Desired State Configuration (DSC) resource debugging by the DSC engine, which is also known as the Local Configuration Manager (LCM).</span></span>
<span data-ttu-id="47ff0-109">Som standard bryts alla resurs instanser i fel söknings programmet.</span><span class="sxs-lookup"><span data-stu-id="47ff0-109">By default, all resource instances break into the debugger.</span></span>

## <span data-ttu-id="47ff0-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="47ff0-110">EXAMPLES</span></span>

### <span data-ttu-id="47ff0-111">Exempel 1: starta fel sökning</span><span class="sxs-lookup"><span data-stu-id="47ff0-111">Example 1: Start debugging</span></span>

```
PS C:\> Enable-DscDebug -BreakAll
```

<span data-ttu-id="47ff0-112">Det här kommandot anger till DSC-motorn eller LCM för att starta resurs fel sökning.</span><span class="sxs-lookup"><span data-stu-id="47ff0-112">This command indicates to the DSC engine or LCM to start resource debugging.</span></span>
<span data-ttu-id="47ff0-113">Nästa gång konfigurationen körs anger processen fel söknings programmet.</span><span class="sxs-lookup"><span data-stu-id="47ff0-113">The next time the configuration is run, the process enters the debugger.</span></span>

### <span data-ttu-id="47ff0-114">Exempel 2: starta fjärrfelsökning</span><span class="sxs-lookup"><span data-stu-id="47ff0-114">Example 2: Start remote debugging</span></span>

```
PS C:\> Enable-DscDebug -BreakAll -CimSession DeploymentServer
```

<span data-ttu-id="47ff0-115">Det här kommandot anger till den DSC-motor som fjärrdatorn ska starta fel sökning av resurs.</span><span class="sxs-lookup"><span data-stu-id="47ff0-115">This command indicates to the DSC engine of the remote computer to start resource debugging.</span></span>

## <span data-ttu-id="47ff0-116">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="47ff0-116">PARAMETERS</span></span>

### <span data-ttu-id="47ff0-117">– AsJob</span><span class="sxs-lookup"><span data-stu-id="47ff0-117">-AsJob</span></span>
<span data-ttu-id="47ff0-118">Anger att denna cmdlet kör kommandot som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="47ff0-118">Indicates that this cmdlet runs the command as a background job.</span></span>

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

### <span data-ttu-id="47ff0-119">-BreakAll</span><span class="sxs-lookup"><span data-stu-id="47ff0-119">-BreakAll</span></span>
<span data-ttu-id="47ff0-120">Anger att alla resurser anger fel sökaren när en konfiguration körs.</span><span class="sxs-lookup"><span data-stu-id="47ff0-120">Indicates that all resources enter the debugger when a configuration runs.</span></span>

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

### <span data-ttu-id="47ff0-121">– CimSession</span><span class="sxs-lookup"><span data-stu-id="47ff0-121">-CimSession</span></span>
<span data-ttu-id="47ff0-122">Kör cmdleten i en fjärran sluten session eller på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="47ff0-122">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="47ff0-123">Ange ett dator namn eller ett sessionsobjekt, till exempel utdata från en [New-CimSession-](/powershell/module/cimcmdlets/new-cimsession) eller [Get-CimSession-](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="47ff0-123">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="47ff0-124">Standardvärdet är den aktuella sessionen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="47ff0-124">The default is the current session on the local computer.</span></span>

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

### <span data-ttu-id="47ff0-125">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="47ff0-125">-ThrottleLimit</span></span>
<span data-ttu-id="47ff0-126">Anger det maximala antalet samtidiga åtgärder som kan upprättas för att köra cmdleten.</span><span class="sxs-lookup"><span data-stu-id="47ff0-126">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="47ff0-127">Om den här parametern utelämnas eller värdet `0` anges, beräknar Windows PowerShell en optimal begränsnings gräns för cmdleten baserat på antalet CIM-cmdletar som körs på datorn.</span><span class="sxs-lookup"><span data-stu-id="47ff0-127">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="47ff0-128">Begränsnings gränsen gäller endast för den aktuella cmdleten, inte sessionen eller till datorn.</span><span class="sxs-lookup"><span data-stu-id="47ff0-128">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="47ff0-129">-Confirm</span><span class="sxs-lookup"><span data-stu-id="47ff0-129">-Confirm</span></span>
<span data-ttu-id="47ff0-130">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="47ff0-130">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="47ff0-131">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="47ff0-131">-WhatIf</span></span>
<span data-ttu-id="47ff0-132">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="47ff0-132">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="47ff0-133">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="47ff0-133">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="47ff0-134">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="47ff0-134">CommonParameters</span></span>
<span data-ttu-id="47ff0-135">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="47ff0-135">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="47ff0-136">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="47ff0-136">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="47ff0-137">INDATA</span><span class="sxs-lookup"><span data-stu-id="47ff0-137">INPUTS</span></span>

## <span data-ttu-id="47ff0-138">UTDATA</span><span class="sxs-lookup"><span data-stu-id="47ff0-138">OUTPUTS</span></span>

## <span data-ttu-id="47ff0-139">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="47ff0-139">NOTES</span></span>

## <span data-ttu-id="47ff0-140">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="47ff0-140">RELATED LINKS</span></span>

[<span data-ttu-id="47ff0-141">Översikt över önskad tillstånds konfiguration i Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="47ff0-141">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="47ff0-142">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="47ff0-142">Disable-DscDebug</span></span>](Disable-DscDebug.md)

[<span data-ttu-id="47ff0-143">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="47ff0-143">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="47ff0-144">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="47ff0-144">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="47ff0-145">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="47ff0-145">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="47ff0-146">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="47ff0-146">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="47ff0-147">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="47ff0-147">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)
