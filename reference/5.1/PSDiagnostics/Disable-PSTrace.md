---
external help file: PSDiagnostics-help.xml
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-pstrace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSTrace
ms.openlocfilehash: fc58e0bcfdd0b4ee7c7ee383b44f7d7f428c34c0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264752"
---
# <span data-ttu-id="c2b3c-102">Disable-PSTrace</span><span class="sxs-lookup"><span data-stu-id="c2b3c-102">Disable-PSTrace</span></span>

## <span data-ttu-id="c2b3c-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="c2b3c-103">SYNOPSIS</span></span>
<span data-ttu-id="c2b3c-104">Inaktiverar loggar för Microsoft-Windows-PowerShell-Händelseprovidern.</span><span class="sxs-lookup"><span data-stu-id="c2b3c-104">Disables the Microsoft-Windows-PowerShell event provider logs.</span></span>

## <span data-ttu-id="c2b3c-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c2b3c-105">SYNTAX</span></span>

```
Disable-PSTrace [-AnalyticOnly] [<CommonParameters>]
```

## <span data-ttu-id="c2b3c-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="c2b3c-106">DESCRIPTION</span></span>

<span data-ttu-id="c2b3c-107">Den här cmdleten inaktiverar händelse loggarna för drift och analys av händelse leverantören Microsoft-Windows-PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c2b3c-107">This cmdlet disables the Operational and Analytic event logs of the Microsoft-Windows-PowerShell event provider.</span></span>

<span data-ttu-id="c2b3c-108">Du måste köra denna cmdlet från en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="c2b3c-108">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="c2b3c-109">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="c2b3c-109">EXAMPLES</span></span>

### <span data-ttu-id="c2b3c-110">Exempel 1: inaktivera analys händelse loggen för PowerShell</span><span class="sxs-lookup"><span data-stu-id="c2b3c-110">Example 1: Disable the Analytic event log for PowerShell</span></span>

<span data-ttu-id="c2b3c-111">I följande exempel inaktive ras endast analys händelse loggen för Microsoft-Windows-PowerShell-providern.</span><span class="sxs-lookup"><span data-stu-id="c2b3c-111">The following example disables only the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span>

```powershell
Disable-PSTrace -AnalyticOnly
```

## <span data-ttu-id="c2b3c-112">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="c2b3c-112">PARAMETERS</span></span>

### <span data-ttu-id="c2b3c-113">-AnalyticOnly</span><span class="sxs-lookup"><span data-stu-id="c2b3c-113">-AnalyticOnly</span></span>

<span data-ttu-id="c2b3c-114">När den här parametern används inaktiverar cmdleten analys händelse loggen för Microsoft-Windows-PowerShell-providern.</span><span class="sxs-lookup"><span data-stu-id="c2b3c-114">When this parameter is used, the cmdlet disables the Analytic event log of the Microsoft-Windows-PowerShell provider.</span></span> <span data-ttu-id="c2b3c-115">Den operativa händelse loggen har inte ändrats.</span><span class="sxs-lookup"><span data-stu-id="c2b3c-115">The Operational event log is not changed.</span></span>

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

## <span data-ttu-id="c2b3c-116">INDATA</span><span class="sxs-lookup"><span data-stu-id="c2b3c-116">INPUTS</span></span>

### <span data-ttu-id="c2b3c-117">Inget</span><span class="sxs-lookup"><span data-stu-id="c2b3c-117">None</span></span>

## <span data-ttu-id="c2b3c-118">UTDATA</span><span class="sxs-lookup"><span data-stu-id="c2b3c-118">OUTPUTS</span></span>

### <span data-ttu-id="c2b3c-119">System. Object</span><span class="sxs-lookup"><span data-stu-id="c2b3c-119">System.Object</span></span>

## <span data-ttu-id="c2b3c-120">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="c2b3c-120">NOTES</span></span>

<span data-ttu-id="c2b3c-121">Denna cmdlet använder `Get-LogProperties` `Set-LogProperties` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="c2b3c-121">This cmdlet uses the `Get-LogProperties` and `Set-LogProperties` cmdlets.</span></span>

<span data-ttu-id="c2b3c-122">Du måste köra denna cmdlet från en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="c2b3c-122">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="c2b3c-123">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="c2b3c-123">RELATED LINKS</span></span>

[<span data-ttu-id="c2b3c-124">Get-LogProperties</span><span class="sxs-lookup"><span data-stu-id="c2b3c-124">Get-LogProperties</span></span>](Get-LogProperties.md)

[<span data-ttu-id="c2b3c-125">Set-LogProperties</span><span class="sxs-lookup"><span data-stu-id="c2b3c-125">Set-LogProperties</span></span>](Set-LogProperties.md)

[<span data-ttu-id="c2b3c-126">Aktivera – PSTrace</span><span class="sxs-lookup"><span data-stu-id="c2b3c-126">Enable-PSTrace</span></span>](Enable-PSTrace.md)
