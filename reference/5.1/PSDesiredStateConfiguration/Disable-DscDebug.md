---
external help file: Disable-DscDebug.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/disable-dscdebug?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-DscDebug
ms.openlocfilehash: fdaba8358772f559a33117c796a923d774b009cb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266073"
---
# <span data-ttu-id="2bbbd-103">Disable-DscDebug</span><span class="sxs-lookup"><span data-stu-id="2bbbd-103">Disable-DscDebug</span></span>

## <span data-ttu-id="2bbbd-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="2bbbd-104">SYNOPSIS</span></span>
<span data-ttu-id="2bbbd-105">Stoppar fel sökning av DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="2bbbd-105">Stops debugging of DSC resources.</span></span>

## <span data-ttu-id="2bbbd-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2bbbd-106">SYNTAX</span></span>

```
Disable-DscDebug [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## <span data-ttu-id="2bbbd-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="2bbbd-107">DESCRIPTION</span></span>
<span data-ttu-id="2bbbd-108">Cmdlet **: en Disable-DscDebug** begär att DSC-motorn (önskad tillstånds konfiguration i Windows PowerShell) slutar felsöka DSC-resurser.</span><span class="sxs-lookup"><span data-stu-id="2bbbd-108">The **Disable-DscDebug** cmdlet requests that the Windows PowerShell Desired State Configuration (DSC) engine stop debugging of DSC resources.</span></span>
<span data-ttu-id="2bbbd-109">Denna cmdlet har ingen inverkan om DSC-motorn för närvarande inte är i fel söknings läge.</span><span class="sxs-lookup"><span data-stu-id="2bbbd-109">This cmdlet has no effect if the DSC engine is not currently in debugging mode.</span></span>

## <span data-ttu-id="2bbbd-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="2bbbd-110">EXAMPLES</span></span>

### <span data-ttu-id="2bbbd-111">Exempel 1: stoppa fel sökning av resurs</span><span class="sxs-lookup"><span data-stu-id="2bbbd-111">Example 1: Stop resource debugging</span></span>

```
PS C:\> Disable-DscDebug
```

<span data-ttu-id="2bbbd-112">Det här kommandot anger DSC-motorn på den lokala Configuration Manager (LCM) för att stoppa fel sökning av resurs.</span><span class="sxs-lookup"><span data-stu-id="2bbbd-112">This command indicates to the DSC engine on the Local Configuration Manager (LCM) to stop resource debugging.</span></span>

### <span data-ttu-id="2bbbd-113">Exempel 2: kontrol lera motor statusen och stoppa fel sökningen</span><span class="sxs-lookup"><span data-stu-id="2bbbd-113">Example 2: Check the engine state and stop debugging</span></span>

```
PS C:\> if((Get-DscLocalConfigurationManager).DebugMode -like '*Break*'){Disable-DscDebug}
```

<span data-ttu-id="2bbbd-114">Det här kommandot kontrollerar DSC-motorns tillstånd och stoppar fel sökning av resurs endast om det redan är i fel söknings läge</span><span class="sxs-lookup"><span data-stu-id="2bbbd-114">This command checks the DSC engine state, and stops resource debugging only if it is already in debugging mode</span></span>

## <span data-ttu-id="2bbbd-115">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="2bbbd-115">PARAMETERS</span></span>

### <span data-ttu-id="2bbbd-116">– AsJob</span><span class="sxs-lookup"><span data-stu-id="2bbbd-116">-AsJob</span></span>
<span data-ttu-id="2bbbd-117">Anger att denna cmdlet kör kommandot som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="2bbbd-117">Indicates that this cmdlet runs the command as a background job.</span></span>

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

### <span data-ttu-id="2bbbd-118">– CimSession</span><span class="sxs-lookup"><span data-stu-id="2bbbd-118">-CimSession</span></span>
<span data-ttu-id="2bbbd-119">Kör cmdleten i en fjärran sluten session eller på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="2bbbd-119">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="2bbbd-120">Ange ett dator namn eller ett sessionsobjekt, till exempel utdata från en [New-CimSession-](/powershell/module/cimcmdlets/new-cimsession) eller [Get-CimSession-](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2bbbd-120">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="2bbbd-121">Standardvärdet är den aktuella sessionen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="2bbbd-121">The default is the current session on the local computer.</span></span>

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

### <span data-ttu-id="2bbbd-122">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="2bbbd-122">-ThrottleLimit</span></span>
<span data-ttu-id="2bbbd-123">Anger det maximala antalet samtidiga åtgärder som kan upprättas för att köra cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2bbbd-123">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="2bbbd-124">Om den här parametern utelämnas eller värdet `0` anges, beräknar Windows PowerShell en optimal begränsnings gräns för cmdleten baserat på antalet CIM-cmdletar som körs på datorn.</span><span class="sxs-lookup"><span data-stu-id="2bbbd-124">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="2bbbd-125">Begränsnings gränsen gäller endast för den aktuella cmdleten, inte sessionen eller till datorn.</span><span class="sxs-lookup"><span data-stu-id="2bbbd-125">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="2bbbd-126">-Confirm</span><span class="sxs-lookup"><span data-stu-id="2bbbd-126">-Confirm</span></span>
<span data-ttu-id="2bbbd-127">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2bbbd-127">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="2bbbd-128">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="2bbbd-128">-WhatIf</span></span>
<span data-ttu-id="2bbbd-129">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="2bbbd-129">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="2bbbd-130">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="2bbbd-130">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="2bbbd-131">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2bbbd-131">CommonParameters</span></span>
<span data-ttu-id="2bbbd-132">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2bbbd-132">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2bbbd-133">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2bbbd-133">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2bbbd-134">INDATA</span><span class="sxs-lookup"><span data-stu-id="2bbbd-134">INPUTS</span></span>

## <span data-ttu-id="2bbbd-135">UTDATA</span><span class="sxs-lookup"><span data-stu-id="2bbbd-135">OUTPUTS</span></span>

## <span data-ttu-id="2bbbd-136">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="2bbbd-136">NOTES</span></span>

## <span data-ttu-id="2bbbd-137">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="2bbbd-137">RELATED LINKS</span></span>

[<span data-ttu-id="2bbbd-138">Översikt över önskad tillstånds konfiguration i Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2bbbd-138">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="2bbbd-139">Aktivera – DscDebug</span><span class="sxs-lookup"><span data-stu-id="2bbbd-139">Enable-DscDebug</span></span>](Enable-DscDebug.md)

[<span data-ttu-id="2bbbd-140">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="2bbbd-140">Get-DscConfigurationStatus</span></span>](Get-DscConfigurationStatus.md)

[<span data-ttu-id="2bbbd-141">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="2bbbd-141">Get-DscLocalConfigurationManager</span></span>](Get-DscLocalConfigurationManager.md)

[<span data-ttu-id="2bbbd-142">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2bbbd-142">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="2bbbd-143">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2bbbd-143">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="2bbbd-144">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="2bbbd-144">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)
