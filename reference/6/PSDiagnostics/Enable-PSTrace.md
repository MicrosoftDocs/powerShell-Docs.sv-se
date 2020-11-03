---
external help file: PSDiagnostics-help.xml
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pstrace?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSTrace
ms.openlocfilehash: d5008d5105b18b5a3d0423cab4282735e3d382d8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263954"
---
# <span data-ttu-id="3ba02-102">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="3ba02-102">Enable-PSTrace</span></span>

## <span data-ttu-id="3ba02-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="3ba02-103">SYNOPSIS</span></span>
<span data-ttu-id="3ba02-104">Aktiverar loggar för Microsoft-Windows-PowerShell-Händelseprovidern.</span><span class="sxs-lookup"><span data-stu-id="3ba02-104">Enables the Microsoft-Windows-PowerShell event provider logs.</span></span>

## <span data-ttu-id="3ba02-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3ba02-105">SYNTAX</span></span>

```
Enable-PSTrace [-Force] [-AnalyticOnly] [<CommonParameters>]
```

## <span data-ttu-id="3ba02-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="3ba02-106">DESCRIPTION</span></span>

<span data-ttu-id="3ba02-107">Med den här cmdleten kan du använda händelse loggarna för drift och analys av händelse leverantören Microsoft-Windows-PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3ba02-107">This cmdlet enables the Operational and Analytic event logs of the Microsoft-Windows-PowerShell event provider.</span></span>

<span data-ttu-id="3ba02-108">Du måste köra denna cmdlet från en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="3ba02-108">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="3ba02-109">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="3ba02-109">EXAMPLES</span></span>

### <span data-ttu-id="3ba02-110">Exempel 1: Aktivera analys händelse loggen för PowerShell</span><span class="sxs-lookup"><span data-stu-id="3ba02-110">Example 1: Enable the Analytic event log for PowerShell</span></span>

<span data-ttu-id="3ba02-111">I följande exempel aktive ras endast analys händelse loggen för Microsoft-Windows-PowerShell-providern.</span><span class="sxs-lookup"><span data-stu-id="3ba02-111">The following example enables only the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span>

```powershell
Enable-PSTrace -AnalyticOnly
```

## <span data-ttu-id="3ba02-112">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="3ba02-112">PARAMETERS</span></span>

### <span data-ttu-id="3ba02-113">-AnalyticOnly</span><span class="sxs-lookup"><span data-stu-id="3ba02-113">-AnalyticOnly</span></span>

<span data-ttu-id="3ba02-114">När den här parametern används aktiverar cmdleten analys händelse loggen för Microsoft-Windows-PowerShell-providern.</span><span class="sxs-lookup"><span data-stu-id="3ba02-114">When this parameter is used, the cmdlet enables the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span> <span data-ttu-id="3ba02-115">Den operativa händelse loggen har inte ändrats.</span><span class="sxs-lookup"><span data-stu-id="3ba02-115">The Operational event log is not changed.</span></span>

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

### <span data-ttu-id="3ba02-116">-Force</span><span class="sxs-lookup"><span data-stu-id="3ba02-116">-Force</span></span>

<span data-ttu-id="3ba02-117">Används för att framtvinga ändringen utan att du behöver göra något.</span><span class="sxs-lookup"><span data-stu-id="3ba02-117">Used to force the change without prompting.</span></span>

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

### <span data-ttu-id="3ba02-118">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3ba02-118">CommonParameters</span></span>
<span data-ttu-id="3ba02-119">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3ba02-119">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3ba02-120">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="3ba02-120">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3ba02-121">INDATA</span><span class="sxs-lookup"><span data-stu-id="3ba02-121">INPUTS</span></span>

### <span data-ttu-id="3ba02-122">Inget</span><span class="sxs-lookup"><span data-stu-id="3ba02-122">None</span></span>

## <span data-ttu-id="3ba02-123">UTDATA</span><span class="sxs-lookup"><span data-stu-id="3ba02-123">OUTPUTS</span></span>

### <span data-ttu-id="3ba02-124">Inget</span><span class="sxs-lookup"><span data-stu-id="3ba02-124">None</span></span>

## <span data-ttu-id="3ba02-125">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="3ba02-125">NOTES</span></span>

<span data-ttu-id="3ba02-126">Denna cmdlet använder `Get-LogProperties` `Set-LogProperties` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="3ba02-126">This cmdlet uses the `Get-LogProperties` and `Set-LogProperties` cmdlets.</span></span>

<span data-ttu-id="3ba02-127">Du måste köra denna cmdlet från en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="3ba02-127">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="3ba02-128">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="3ba02-128">RELATED LINKS</span></span>

[<span data-ttu-id="3ba02-129">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="3ba02-129">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="3ba02-130">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="3ba02-130">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="3ba02-131">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="3ba02-131">Disable-PSTrace</span></span>](Disable-PSTrace.md)
