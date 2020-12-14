---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/stop-trace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Trace
ms.openlocfilehash: 5727ae52326830fa16012722d0b801b7d43e50dd
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708590"
---
# <span data-ttu-id="6a52f-102">Stop-Trace</span><span class="sxs-lookup"><span data-stu-id="6a52f-102">Stop-Trace</span></span>

## <span data-ttu-id="6a52f-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="6a52f-103">SYNOPSIS</span></span>
<span data-ttu-id="6a52f-104">Stoppa en loggnings session för händelse spårning.</span><span class="sxs-lookup"><span data-stu-id="6a52f-104">Stop an Event Trace logging session.</span></span>

## <span data-ttu-id="6a52f-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6a52f-105">SYNTAX</span></span>

```
Stop-Trace [-SessionName] <Object> [-ETS] [<CommonParameters>]
```

## <span data-ttu-id="6a52f-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="6a52f-106">DESCRIPTION</span></span>

<span data-ttu-id="6a52f-107">Denna cmdlet stoppar en loggnings session för Windows Event trace.</span><span class="sxs-lookup"><span data-stu-id="6a52f-107">This cmdlet stops a Windows Event Trace logging session.</span></span>

<span data-ttu-id="6a52f-108">Denna cmdlet används av följande cmdlets:</span><span class="sxs-lookup"><span data-stu-id="6a52f-108">This cmdlet is used by the following cmdlets:</span></span>

- `Disable-PSWSManCombinedTrace`
- `Disable-WSManTrace`

<span data-ttu-id="6a52f-109">Du måste köra denna cmdlet från en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="6a52f-109">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="6a52f-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="6a52f-110">EXAMPLES</span></span>

### <span data-ttu-id="6a52f-111">Exempel 1: stoppa en WSMan-spårningssession för spårning av loggar</span><span class="sxs-lookup"><span data-stu-id="6a52f-111">Example 1: Stop a WSMan Trace logging session</span></span>

```powershell
Stop-Trace -SessionName 'wsmlog'
```

## <span data-ttu-id="6a52f-112">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="6a52f-112">PARAMETERS</span></span>

### <span data-ttu-id="6a52f-113">-ETS</span><span class="sxs-lookup"><span data-stu-id="6a52f-113">-ETS</span></span>
<span data-ttu-id="6a52f-114">Skicka kommandon till Event trace-sessioner direkt utan att spara eller schemalägga.</span><span class="sxs-lookup"><span data-stu-id="6a52f-114">Send commands to Event Trace Sessions directly without saving or scheduling.</span></span>

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

### <span data-ttu-id="6a52f-115">-Sessionsnamn</span><span class="sxs-lookup"><span data-stu-id="6a52f-115">-SessionName</span></span>
<span data-ttu-id="6a52f-116">Namnet på händelsespårningssessionen som ska stoppas.</span><span class="sxs-lookup"><span data-stu-id="6a52f-116">The name of the Event Trace session to be stopped.</span></span>

```yaml
Type: System.Object
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="6a52f-117">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6a52f-117">CommonParameters</span></span>
<span data-ttu-id="6a52f-118">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6a52f-118">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6a52f-119">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="6a52f-119">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6a52f-120">INDATA</span><span class="sxs-lookup"><span data-stu-id="6a52f-120">INPUTS</span></span>

### <span data-ttu-id="6a52f-121">Inga</span><span class="sxs-lookup"><span data-stu-id="6a52f-121">None</span></span>

## <span data-ttu-id="6a52f-122">UTDATA</span><span class="sxs-lookup"><span data-stu-id="6a52f-122">OUTPUTS</span></span>

### <span data-ttu-id="6a52f-123">Inga</span><span class="sxs-lookup"><span data-stu-id="6a52f-123">None</span></span>

## <span data-ttu-id="6a52f-124">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="6a52f-124">NOTES</span></span>

## <span data-ttu-id="6a52f-125">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="6a52f-125">RELATED LINKS</span></span>

[<span data-ttu-id="6a52f-126">Händelse spårning</span><span class="sxs-lookup"><span data-stu-id="6a52f-126">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="6a52f-127">Starta spårning</span><span class="sxs-lookup"><span data-stu-id="6a52f-127">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="6a52f-128">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="6a52f-128">Disable-PSWSManCombinedTrace</span></span>](Disable-PSWSManCombinedTrace.md)

[<span data-ttu-id="6a52f-129">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="6a52f-129">Disable-WSManTrace</span></span>](Disable-WSManTrace.md)

[<span data-ttu-id="6a52f-130">Aktivera – PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="6a52f-130">Enable-PSWSManCombinedTrace</span></span>](Enable-PSWSManCombinedTrace.md)

[<span data-ttu-id="6a52f-131">Aktivera – WSManTrace</span><span class="sxs-lookup"><span data-stu-id="6a52f-131">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)

