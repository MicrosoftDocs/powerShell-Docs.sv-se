---
external help file: PSDiagnostics-help.xml
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-pstrace?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSTrace
ms.openlocfilehash: 3f99869825b2255d3f5487c48b6eaa90a4ae901f
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263937"
---
# <span data-ttu-id="075fe-102">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="075fe-102">Disable-PSTrace</span></span>

## <span data-ttu-id="075fe-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="075fe-103">SYNOPSIS</span></span>
<span data-ttu-id="075fe-104">Inaktiverar loggar för Microsoft-Windows-PowerShell-Händelseprovidern.</span><span class="sxs-lookup"><span data-stu-id="075fe-104">Disables the Microsoft-Windows-PowerShell event provider logs.</span></span>

## <span data-ttu-id="075fe-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="075fe-105">SYNTAX</span></span>

```
Disable-PSTrace [-AnalyticOnly] [<CommonParameters>]
```

## <span data-ttu-id="075fe-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="075fe-106">DESCRIPTION</span></span>

<span data-ttu-id="075fe-107">Den här cmdleten inaktiverar händelse loggarna för drift och analys av händelse leverantören Microsoft-Windows-PowerShell.</span><span class="sxs-lookup"><span data-stu-id="075fe-107">This cmdlet disables the Operational and Analytic event logs of the Microsoft-Windows-PowerShell event provider.</span></span>

<span data-ttu-id="075fe-108">Du måste köra denna cmdlet från en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="075fe-108">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="075fe-109">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="075fe-109">EXAMPLES</span></span>

### <span data-ttu-id="075fe-110">Exempel 1: inaktivera analys händelse loggen för PowerShell</span><span class="sxs-lookup"><span data-stu-id="075fe-110">Example 1: Disable the Analytic event log for PowerShell</span></span>

<span data-ttu-id="075fe-111">I följande exempel inaktive ras endast analys händelse loggen för Microsoft-Windows-PowerShell-providern.</span><span class="sxs-lookup"><span data-stu-id="075fe-111">The following example disables only the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span>

```powershell
Disable-PSTrace -AnalyticOnly
```

## <span data-ttu-id="075fe-112">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="075fe-112">PARAMETERS</span></span>

### <span data-ttu-id="075fe-113">-AnalyticOnly</span><span class="sxs-lookup"><span data-stu-id="075fe-113">-AnalyticOnly</span></span>

<span data-ttu-id="075fe-114">När den här parametern används inaktiverar cmdleten analys händelse loggen för Microsoft-Windows-PowerShell-providern.</span><span class="sxs-lookup"><span data-stu-id="075fe-114">When this parameter is used, the cmdlet disables the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span> <span data-ttu-id="075fe-115">Den operativa händelse loggen har inte ändrats.</span><span class="sxs-lookup"><span data-stu-id="075fe-115">The Operational event log is not changed.</span></span>

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

### <span data-ttu-id="075fe-116">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="075fe-116">CommonParameters</span></span>
<span data-ttu-id="075fe-117">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="075fe-117">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="075fe-118">Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="075fe-118">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="075fe-119">INDATA</span><span class="sxs-lookup"><span data-stu-id="075fe-119">INPUTS</span></span>

### <span data-ttu-id="075fe-120">Inget</span><span class="sxs-lookup"><span data-stu-id="075fe-120">None</span></span>

## <span data-ttu-id="075fe-121">UTDATA</span><span class="sxs-lookup"><span data-stu-id="075fe-121">OUTPUTS</span></span>

### <span data-ttu-id="075fe-122">Inget</span><span class="sxs-lookup"><span data-stu-id="075fe-122">None</span></span>

## <span data-ttu-id="075fe-123">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="075fe-123">NOTES</span></span>

<span data-ttu-id="075fe-124">Denna cmdlet använder `Get-LogProperties` `Set-LogProperties` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="075fe-124">This cmdlet uses the `Get-LogProperties` and `Set-LogProperties` cmdlets.</span></span>

<span data-ttu-id="075fe-125">Du måste köra denna cmdlet från en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="075fe-125">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="075fe-126">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="075fe-126">RELATED LINKS</span></span>

[<span data-ttu-id="075fe-127">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="075fe-127">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="075fe-128">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="075fe-128">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="075fe-129">Aktivera – PSTrace</span><span class="sxs-lookup"><span data-stu-id="075fe-129">Enable-PSTrace</span></span>](Enable-PSTrace.md)
