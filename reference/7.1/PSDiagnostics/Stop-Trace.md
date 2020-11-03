---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/27/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/stop-trace?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Trace
ms.openlocfilehash: 7331c7ca1ece02757859e75eefddd5a662353beb
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263367"
---
# <span data-ttu-id="276f2-103">Stop-Trace</span><span class="sxs-lookup"><span data-stu-id="276f2-103">Stop-Trace</span></span>

## <span data-ttu-id="276f2-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="276f2-104">SYNOPSIS</span></span>
<span data-ttu-id="276f2-105">Stoppa en loggnings session för händelse spårning.</span><span class="sxs-lookup"><span data-stu-id="276f2-105">Stop an Event Trace logging session.</span></span>

## <span data-ttu-id="276f2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="276f2-106">SYNTAX</span></span>

```
Stop-Trace [-SessionName] <Object> [-ETS] [<CommonParameters>]
```

## <span data-ttu-id="276f2-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="276f2-107">DESCRIPTION</span></span>

<span data-ttu-id="276f2-108">Denna cmdlet stoppar en loggnings session för Windows Event trace.</span><span class="sxs-lookup"><span data-stu-id="276f2-108">This cmdlet stops a Windows Event Trace logging session.</span></span>

<span data-ttu-id="276f2-109">Denna cmdlet används av följande cmdlets:</span><span class="sxs-lookup"><span data-stu-id="276f2-109">This cmdlet is used by the following cmdlets:</span></span>

- `Disable-PSWSManCombinedTrace`
- `Disable-WSManTrace`

<span data-ttu-id="276f2-110">Du måste köra denna cmdlet från en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="276f2-110">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="276f2-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="276f2-111">EXAMPLES</span></span>

### <span data-ttu-id="276f2-112">Exempel 1: stoppa en WSMan-spårningssession för spårning av loggar</span><span class="sxs-lookup"><span data-stu-id="276f2-112">Example 1: Stop a WSMan Trace logging session</span></span>

```powershell
Stop-Trace -SessionName 'wsmlog'
```

## <span data-ttu-id="276f2-113">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="276f2-113">PARAMETERS</span></span>

### <span data-ttu-id="276f2-114">-ETS</span><span class="sxs-lookup"><span data-stu-id="276f2-114">-ETS</span></span>
<span data-ttu-id="276f2-115">Skicka kommandon till Event trace-sessioner direkt utan att spara eller schemalägga.</span><span class="sxs-lookup"><span data-stu-id="276f2-115">Send commands to Event Trace Sessions directly without saving or scheduling.</span></span>

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

### <span data-ttu-id="276f2-116">-Sessionsnamn</span><span class="sxs-lookup"><span data-stu-id="276f2-116">-SessionName</span></span>
<span data-ttu-id="276f2-117">Namnet på händelsespårningssessionen som ska stoppas.</span><span class="sxs-lookup"><span data-stu-id="276f2-117">The name of the Event Trace session to be stopped.</span></span>

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

### <span data-ttu-id="276f2-118">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="276f2-118">CommonParameters</span></span>
<span data-ttu-id="276f2-119">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="276f2-119">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="276f2-120">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="276f2-120">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="276f2-121">INDATA</span><span class="sxs-lookup"><span data-stu-id="276f2-121">INPUTS</span></span>

### <span data-ttu-id="276f2-122">Inget</span><span class="sxs-lookup"><span data-stu-id="276f2-122">None</span></span>

## <span data-ttu-id="276f2-123">UTDATA</span><span class="sxs-lookup"><span data-stu-id="276f2-123">OUTPUTS</span></span>

### <span data-ttu-id="276f2-124">Inget</span><span class="sxs-lookup"><span data-stu-id="276f2-124">None</span></span>

## <span data-ttu-id="276f2-125">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="276f2-125">NOTES</span></span>

## <span data-ttu-id="276f2-126">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="276f2-126">RELATED LINKS</span></span>

[<span data-ttu-id="276f2-127">Händelse spårning</span><span class="sxs-lookup"><span data-stu-id="276f2-127">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="276f2-128">Starta spårning</span><span class="sxs-lookup"><span data-stu-id="276f2-128">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="276f2-129">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="276f2-129">Disable-PSWSManCombinedTrace</span></span>](Disable-PSWSManCombinedTrace.md)

[<span data-ttu-id="276f2-130">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="276f2-130">Disable-WSManTrace</span></span>](Disable-WSManTrace.md)

[<span data-ttu-id="276f2-131">Aktivera – PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="276f2-131">Enable-PSWSManCombinedTrace</span></span>](Enable-PSWSManCombinedTrace.md)

[<span data-ttu-id="276f2-132">Aktivera – WSManTrace</span><span class="sxs-lookup"><span data-stu-id="276f2-132">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)

