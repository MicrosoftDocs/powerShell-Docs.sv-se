---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pstrace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSTrace
ms.openlocfilehash: 2ec01393a46de84b59f06995473bdff6bd5b2b4f
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195029"
---
# <span data-ttu-id="56a32-102">Enable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="56a32-102">Enable-PSTrace</span></span>

## <span data-ttu-id="56a32-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="56a32-103">SYNOPSIS</span></span>
<span data-ttu-id="56a32-104">Aktiverar loggar för Microsoft-Windows-PowerShell-Händelseprovidern.</span><span class="sxs-lookup"><span data-stu-id="56a32-104">Enables the Microsoft-Windows-PowerShell event provider logs.</span></span>

## <span data-ttu-id="56a32-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="56a32-105">SYNTAX</span></span>

```
Enable-PSTrace [-Force] [-AnalyticOnly]
```

## <span data-ttu-id="56a32-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="56a32-106">DESCRIPTION</span></span>

<span data-ttu-id="56a32-107">Med den här cmdleten kan du använda händelse loggarna för drift och analys av händelse leverantören Microsoft-Windows-PowerShell.</span><span class="sxs-lookup"><span data-stu-id="56a32-107">This cmdlet enables the Operational and Analytic event logs of the Microsoft-Windows-PowerShell event provider.</span></span>

<span data-ttu-id="56a32-108">Du måste köra denna cmdlet från en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="56a32-108">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="56a32-109">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="56a32-109">EXAMPLES</span></span>

### <span data-ttu-id="56a32-110">Exempel 1: Aktivera analys händelse loggen för PowerShell</span><span class="sxs-lookup"><span data-stu-id="56a32-110">Example 1: Enable the Analytic event log for PowerShell</span></span>

<span data-ttu-id="56a32-111">I följande exempel aktive ras endast analys händelse loggen för Microsoft-Windows-PowerShell-providern.</span><span class="sxs-lookup"><span data-stu-id="56a32-111">The following example enables only the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span>

```powershell
Enable-PSTrace -AnalyticOnly
```

## <span data-ttu-id="56a32-112">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="56a32-112">PARAMETERS</span></span>

### <span data-ttu-id="56a32-113">-AnalyticOnly</span><span class="sxs-lookup"><span data-stu-id="56a32-113">-AnalyticOnly</span></span>

<span data-ttu-id="56a32-114">När den här parametern används aktiverar cmdleten analys händelse loggen för Microsoft-Windows-PowerShell-providern.</span><span class="sxs-lookup"><span data-stu-id="56a32-114">When this parameter is used, the cmdlet enables the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span> <span data-ttu-id="56a32-115">Den operativa händelse loggen har inte ändrats.</span><span class="sxs-lookup"><span data-stu-id="56a32-115">The Operational event log is not changed.</span></span>

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

### <span data-ttu-id="56a32-116">-Force</span><span class="sxs-lookup"><span data-stu-id="56a32-116">-Force</span></span>

<span data-ttu-id="56a32-117">Används för att framtvinga ändringen utan att du behöver göra något.</span><span class="sxs-lookup"><span data-stu-id="56a32-117">Used to force the change without prompting.</span></span>

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

## <span data-ttu-id="56a32-118">INDATA</span><span class="sxs-lookup"><span data-stu-id="56a32-118">INPUTS</span></span>

### <span data-ttu-id="56a32-119">Inget</span><span class="sxs-lookup"><span data-stu-id="56a32-119">None</span></span>

## <span data-ttu-id="56a32-120">UTDATA</span><span class="sxs-lookup"><span data-stu-id="56a32-120">OUTPUTS</span></span>

### <span data-ttu-id="56a32-121">System. Object</span><span class="sxs-lookup"><span data-stu-id="56a32-121">System.Object</span></span>

## <span data-ttu-id="56a32-122">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="56a32-122">NOTES</span></span>

<span data-ttu-id="56a32-123">Denna cmdlet använder `Get-LogProperties` `Set-LogProperties` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="56a32-123">This cmdlet uses the `Get-LogProperties` and `Set-LogProperties` cmdlets.</span></span>

<span data-ttu-id="56a32-124">Du måste köra denna cmdlet från en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="56a32-124">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="56a32-125">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="56a32-125">RELATED LINKS</span></span>

[<span data-ttu-id="56a32-126">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="56a32-126">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="56a32-127">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="56a32-127">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="56a32-128">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="56a32-128">Disable-PSTrace</span></span>](Disable-PSTrace.md)
