---
external help file: Get-DscConfigurationStatus.cdxml-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDesiredStateConfiguration
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-DscConfigurationStatus
ms.openlocfilehash: 0d59ce58a70eab68441ea1fe6097bbdf7792a54f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266084"
---
# <span data-ttu-id="b1812-103">Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="b1812-103">Get-DscConfigurationStatus</span></span>

## <span data-ttu-id="b1812-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="b1812-104">SYNOPSIS</span></span>
<span data-ttu-id="b1812-105">Hämtar information om slutförda konfigurations körningar.</span><span class="sxs-lookup"><span data-stu-id="b1812-105">Retrieves data about completed configuration runs.</span></span>

## <span data-ttu-id="b1812-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b1812-106">SYNTAX</span></span>

```
Get-DscConfigurationStatus [-All] [-CimSession <CimSession[]>] [-ThrottleLimit <Int32>] [-AsJob]
 [<CommonParameters>]
```

## <span data-ttu-id="b1812-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b1812-107">DESCRIPTION</span></span>
<span data-ttu-id="b1812-108">Cmdlet **: en get-DscConfigurationStatus** hämtar detaljerad information om slutförda konfigurations körningar i systemet.</span><span class="sxs-lookup"><span data-stu-id="b1812-108">The **Get-DscConfigurationStatus** cmdlet retrieves detailed information about completed configuration runs on the system.</span></span>
<span data-ttu-id="b1812-109">Som standard returnerar den information om den senaste konfigurations körningen.</span><span class="sxs-lookup"><span data-stu-id="b1812-109">By default, it returns the information about the last configuration run.</span></span>
<span data-ttu-id="b1812-110">Denna cmdlet är användbar för att hitta historisk information om konfigurations körningar, t. ex. När konfigurationerna kördes, status för körningarna, antalet resurser i konfigurationerna och vilka resurser som har lyckats eller misslyckats.</span><span class="sxs-lookup"><span data-stu-id="b1812-110">This cmdlet is useful for finding historical information about configuration runs, such as when the configurations were run, the status of the runs, the number of resources in the configurations, and which resources succeeded or failed.</span></span>

## <span data-ttu-id="b1812-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="b1812-111">EXAMPLES</span></span>

### <span data-ttu-id="b1812-112">Exempel 1: Hämta information om den senaste konfigurations körningen</span><span class="sxs-lookup"><span data-stu-id="b1812-112">Example 1: Get information on the last configuration run</span></span>

```
PS C:\> Get-DscConfigurationStatus
```

<span data-ttu-id="b1812-113">Det här kommandot hämtar information om den senaste konfigurations körningen.</span><span class="sxs-lookup"><span data-stu-id="b1812-113">This command gets information on the last configuration run.</span></span>

### <span data-ttu-id="b1812-114">Exempel 2: Hämta information om alla konfigurationer</span><span class="sxs-lookup"><span data-stu-id="b1812-114">Example 2: Get information on all configurations</span></span>

```
PS C:\> Get-DscConfigurationStatus -All
```

<span data-ttu-id="b1812-115">Det här kommandot hämtar information om alla konfigurationer som kördes på systemet, inklusive konsekvens kontroll av Windows PowerShell Desired State Configuration (DSC).</span><span class="sxs-lookup"><span data-stu-id="b1812-115">This command gets information about all the configurations that were run on the system, including the Windows PowerShell Desired State Configuration (DSC) consistency check.</span></span>

### <span data-ttu-id="b1812-116">Exempel 3: Hämta information om konfigurations körningen på en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="b1812-116">Example 3: Get information on the configuration run on a remote computer</span></span>

```
PS C:\> Get-DscConfigurationStatus -CimSession "Server01"
```

<span data-ttu-id="b1812-117">Det här kommandot hämtar konfigurations körnings information för fjärrdatorn med namnet Server01.</span><span class="sxs-lookup"><span data-stu-id="b1812-117">This command gets the configuration run details of the remote computer named Server01.</span></span>
<span data-ttu-id="b1812-118">Detta använder WSMan-transport för att ansluta till fjärrdatorn och kräver att den anslutna användaren är administratör på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="b1812-118">This uses the WSMan transport to connect to the remote computer and requires that the connecting user be an administrator on the remote computer.</span></span>

## <span data-ttu-id="b1812-119">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="b1812-119">PARAMETERS</span></span>

### <span data-ttu-id="b1812-120">– Alla</span><span class="sxs-lookup"><span data-stu-id="b1812-120">-All</span></span>
<span data-ttu-id="b1812-121">Anger att denna cmdlet hämtar information om all konfiguration som körs på datorn, inklusive konfigurations programmet och konsekvens kontrollen.</span><span class="sxs-lookup"><span data-stu-id="b1812-121">Indicates that this cmdlet retrieves information about all the configuration runs on the computer, including the configuration application and the consistency check.</span></span>

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

### <span data-ttu-id="b1812-122">– AsJob</span><span class="sxs-lookup"><span data-stu-id="b1812-122">-AsJob</span></span>
<span data-ttu-id="b1812-123">Anger att denna cmdlet kör kommandot som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="b1812-123">Indicates that this cmdlet runs the command as a background job.</span></span>

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

### <span data-ttu-id="b1812-124">– CimSession</span><span class="sxs-lookup"><span data-stu-id="b1812-124">-CimSession</span></span>
<span data-ttu-id="b1812-125">Kör cmdleten i en fjärran sluten session eller på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="b1812-125">Runs the cmdlet in a remote session or on a remote computer.</span></span>
<span data-ttu-id="b1812-126">Ange ett dator namn eller ett sessionsobjekt, till exempel utdata från en [New-CimSession-](/powershell/module/cimcmdlets/new-cimsession) eller [Get-CimSession-](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b1812-126">Enter a computer name or a session object, such as the output of a [New-CimSession](/powershell/module/cimcmdlets/new-cimsession) or [Get-CimSession](/powershell/module/cimcmdlets/get-cimsession) cmdlet.</span></span>
<span data-ttu-id="b1812-127">Standardvärdet är den aktuella sessionen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="b1812-127">The default is the current session on the local computer.</span></span>

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

### <span data-ttu-id="b1812-128">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="b1812-128">-ThrottleLimit</span></span>
<span data-ttu-id="b1812-129">Anger det maximala antalet samtidiga åtgärder som kan upprättas för att köra cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b1812-129">Specifies the maximum number of concurrent operations that can be established to run the cmdlet.</span></span>
<span data-ttu-id="b1812-130">Om den här parametern utelämnas eller värdet `0` anges, beräknar Windows PowerShell en optimal begränsnings gräns för cmdleten baserat på antalet CIM-cmdletar som körs på datorn.</span><span class="sxs-lookup"><span data-stu-id="b1812-130">If this parameter is omitted or a value of `0` is entered, then Windows PowerShell calculates an optimum throttle limit for the cmdlet based on the number of CIM cmdlets that are running on the computer.</span></span>
<span data-ttu-id="b1812-131">Begränsnings gränsen gäller endast för den aktuella cmdleten, inte sessionen eller till datorn.</span><span class="sxs-lookup"><span data-stu-id="b1812-131">The throttle limit applies only to the current cmdlet, not to the session or to the computer.</span></span>

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

### <span data-ttu-id="b1812-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b1812-132">CommonParameters</span></span>
<span data-ttu-id="b1812-133">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b1812-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b1812-134">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b1812-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b1812-135">INDATA</span><span class="sxs-lookup"><span data-stu-id="b1812-135">INPUTS</span></span>

## <span data-ttu-id="b1812-136">UTDATA</span><span class="sxs-lookup"><span data-stu-id="b1812-136">OUTPUTS</span></span>

## <span data-ttu-id="b1812-137">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="b1812-137">NOTES</span></span>

## <span data-ttu-id="b1812-138">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="b1812-138">RELATED LINKS</span></span>

[<span data-ttu-id="b1812-139">Översikt över önskad tillstånds konfiguration i Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b1812-139">Windows PowerShell Desired State Configuration Overview</span></span>](/powershell/scripting/dsc/overview/dscforengineers)

[<span data-ttu-id="b1812-140">Get-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="b1812-140">Get-DscConfiguration</span></span>](Get-DscConfiguration.md)

[<span data-ttu-id="b1812-141">Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="b1812-141">Get-DscLocalConfigurationManager</span></span>](Get-DscLocalConfigurationManager.md)

[<span data-ttu-id="b1812-142">Restore-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="b1812-142">Restore-DscConfiguration</span></span>](Restore-DscConfiguration.md)

[<span data-ttu-id="b1812-143">Start-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="b1812-143">Start-DscConfiguration</span></span>](Start-DscConfiguration.md)

[<span data-ttu-id="b1812-144">Test-DscConfiguration</span><span class="sxs-lookup"><span data-stu-id="b1812-144">Test-DscConfiguration</span></span>](Test-DscConfiguration.md)
