---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-tracesource?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TraceSource
ms.openlocfilehash: 7d57e7cff0dc3ca0eff36dbe38e240efdd324060
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265016"
---
# <span data-ttu-id="c5c1b-103">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="c5c1b-103">Get-TraceSource</span></span>

## <span data-ttu-id="c5c1b-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="c5c1b-104">SYNOPSIS</span></span>
<span data-ttu-id="c5c1b-105">Hämtar PowerShell-komponenter som instrumenteras för spårning.</span><span class="sxs-lookup"><span data-stu-id="c5c1b-105">Gets PowerShell components that are instrumented for tracing.</span></span>

## <span data-ttu-id="c5c1b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c5c1b-106">SYNTAX</span></span>

```
Get-TraceSource [[-Name] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="c5c1b-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="c5c1b-107">DESCRIPTION</span></span>

<span data-ttu-id="c5c1b-108">**Get-TraceSource** -cmdlet: en hämtar spårnings källorna för PowerShell-komponenter som används för närvarande.</span><span class="sxs-lookup"><span data-stu-id="c5c1b-108">The **Get-TraceSource** cmdlet gets the trace sources for PowerShell components that are currently in use.</span></span>
<span data-ttu-id="c5c1b-109">Du kan använda data för att avgöra vilka PowerShell-komponenter du kan spåra.</span><span class="sxs-lookup"><span data-stu-id="c5c1b-109">You can use the data to determine which PowerShell components you can trace.</span></span>
<span data-ttu-id="c5c1b-110">Vid spårning genererar komponenten detaljerade meddelanden om varje steg i den interna bearbetningen.</span><span class="sxs-lookup"><span data-stu-id="c5c1b-110">When tracing, the component generates detailed messages about each step in its internal processing.</span></span>
<span data-ttu-id="c5c1b-111">Utvecklare använder spårnings data för att övervaka data flöde, program körning och fel.</span><span class="sxs-lookup"><span data-stu-id="c5c1b-111">Developers use the trace data to monitor data flow, program execution, and errors.</span></span>

<span data-ttu-id="c5c1b-112">Spårnings-cmdletarna har utformats för PowerShell-utvecklare, men de är tillgängliga för alla användare.</span><span class="sxs-lookup"><span data-stu-id="c5c1b-112">The tracing cmdlets were designed for PowerShell developers, but they are available to all users.</span></span>

## <span data-ttu-id="c5c1b-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="c5c1b-113">EXAMPLES</span></span>

### <span data-ttu-id="c5c1b-114">Exempel 1: Hämta spårnings källor efter namn</span><span class="sxs-lookup"><span data-stu-id="c5c1b-114">Example 1: Get trace sources by name</span></span>

```
PS C:\> Get-TraceSource -Name "*provider*"
```

<span data-ttu-id="c5c1b-115">Det här kommandot hämtar alla spårnings källor som har namn som inkluderar providern.</span><span class="sxs-lookup"><span data-stu-id="c5c1b-115">This command gets all of the trace sources that have names that include provider.</span></span>

### <span data-ttu-id="c5c1b-116">Exempel 2: Hämta alla spårnings källor</span><span class="sxs-lookup"><span data-stu-id="c5c1b-116">Example 2: Get all trace sources</span></span>

```
PS C:\> Get-TraceSource
```

<span data-ttu-id="c5c1b-117">Det här kommandot hämtar alla PowerShell-komponenter som kan spåras.</span><span class="sxs-lookup"><span data-stu-id="c5c1b-117">This command gets all of the PowerShell components that can be traced.</span></span>

## <span data-ttu-id="c5c1b-118">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="c5c1b-118">PARAMETERS</span></span>

### <span data-ttu-id="c5c1b-119">-Name</span><span class="sxs-lookup"><span data-stu-id="c5c1b-119">-Name</span></span>

<span data-ttu-id="c5c1b-120">Anger spårnings källorna som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="c5c1b-120">Specifies the trace sources to get.</span></span>
<span data-ttu-id="c5c1b-121">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="c5c1b-121">Wildcards are permitted.</span></span>
<span data-ttu-id="c5c1b-122">Parameter namnets *namn* är valfritt.</span><span class="sxs-lookup"><span data-stu-id="c5c1b-122">The parameter name *Name* is optional.</span></span>

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### <span data-ttu-id="c5c1b-123">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c5c1b-123">CommonParameters</span></span>

<span data-ttu-id="c5c1b-124">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c5c1b-124">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c5c1b-125">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c5c1b-125">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c5c1b-126">INDATA</span><span class="sxs-lookup"><span data-stu-id="c5c1b-126">INPUTS</span></span>

### <span data-ttu-id="c5c1b-127">System. String</span><span class="sxs-lookup"><span data-stu-id="c5c1b-127">System.String</span></span>

<span data-ttu-id="c5c1b-128">Du kan skicka vidare en sträng som innehåller namnet på en spårnings källa till **Get-TraceSource**.</span><span class="sxs-lookup"><span data-stu-id="c5c1b-128">You can pipe a string that contains the name of a trace source to **Get-TraceSource**.</span></span>

## <span data-ttu-id="c5c1b-129">UTDATA</span><span class="sxs-lookup"><span data-stu-id="c5c1b-129">OUTPUTS</span></span>

### <span data-ttu-id="c5c1b-130">System. Management. Automation. PSTraceSource</span><span class="sxs-lookup"><span data-stu-id="c5c1b-130">System.Management.Automation.PSTraceSource</span></span>

<span data-ttu-id="c5c1b-131">**Get-TraceSource** returnerar objekt som representerar spårnings källorna.</span><span class="sxs-lookup"><span data-stu-id="c5c1b-131">**Get-TraceSource** returns objects that represent the trace sources.</span></span>

## <span data-ttu-id="c5c1b-132">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="c5c1b-132">NOTES</span></span>

## <span data-ttu-id="c5c1b-133">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="c5c1b-133">RELATED LINKS</span></span>

[<span data-ttu-id="c5c1b-134">Set-TraceSource</span><span class="sxs-lookup"><span data-stu-id="c5c1b-134">Set-TraceSource</span></span>](Set-TraceSource.md)

[<span data-ttu-id="c5c1b-135">Spåra-kommando</span><span class="sxs-lookup"><span data-stu-id="c5c1b-135">Trace-Command</span></span>](Trace-Command.md)
