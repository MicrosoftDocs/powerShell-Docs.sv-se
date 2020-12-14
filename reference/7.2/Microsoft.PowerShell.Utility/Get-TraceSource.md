---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-tracesource?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-TraceSource
ms.openlocfilehash: c196d00359c9b20b5dc1fefc0ab2b94655703f6f
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710099"
---
# <span data-ttu-id="5f52a-102">Get-TraceSource</span><span class="sxs-lookup"><span data-stu-id="5f52a-102">Get-TraceSource</span></span>

## <span data-ttu-id="5f52a-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="5f52a-103">SYNOPSIS</span></span>
<span data-ttu-id="5f52a-104">Hämtar PowerShell-komponenter som instrumenteras för spårning.</span><span class="sxs-lookup"><span data-stu-id="5f52a-104">Gets PowerShell components that are instrumented for tracing.</span></span>

## <span data-ttu-id="5f52a-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5f52a-105">SYNTAX</span></span>

```
Get-TraceSource [[-Name] <String[]>] [<CommonParameters>]
```

## <span data-ttu-id="5f52a-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="5f52a-106">DESCRIPTION</span></span>

<span data-ttu-id="5f52a-107">**Get-TraceSource** -cmdlet: en hämtar spårnings källorna för PowerShell-komponenter som används för närvarande.</span><span class="sxs-lookup"><span data-stu-id="5f52a-107">The **Get-TraceSource** cmdlet gets the trace sources for PowerShell components that are currently in use.</span></span>
<span data-ttu-id="5f52a-108">Du kan använda data för att avgöra vilka PowerShell-komponenter du kan spåra.</span><span class="sxs-lookup"><span data-stu-id="5f52a-108">You can use the data to determine which PowerShell components you can trace.</span></span>
<span data-ttu-id="5f52a-109">Vid spårning genererar komponenten detaljerade meddelanden om varje steg i den interna bearbetningen.</span><span class="sxs-lookup"><span data-stu-id="5f52a-109">When tracing, the component generates detailed messages about each step in its internal processing.</span></span>
<span data-ttu-id="5f52a-110">Utvecklare använder spårnings data för att övervaka data flöde, program körning och fel.</span><span class="sxs-lookup"><span data-stu-id="5f52a-110">Developers use the trace data to monitor data flow, program execution, and errors.</span></span>

<span data-ttu-id="5f52a-111">Spårnings-cmdletarna har utformats för PowerShell-utvecklare, men de är tillgängliga för alla användare.</span><span class="sxs-lookup"><span data-stu-id="5f52a-111">The tracing cmdlets were designed for PowerShell developers, but they are available to all users.</span></span>

## <span data-ttu-id="5f52a-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="5f52a-112">EXAMPLES</span></span>

### <span data-ttu-id="5f52a-113">Exempel 1: Hämta spårnings källor efter namn</span><span class="sxs-lookup"><span data-stu-id="5f52a-113">Example 1: Get trace sources by name</span></span>

```
PS C:\> Get-TraceSource -Name "*provider*"
```

<span data-ttu-id="5f52a-114">Det här kommandot hämtar alla spårnings källor som har namn som inkluderar providern.</span><span class="sxs-lookup"><span data-stu-id="5f52a-114">This command gets all of the trace sources that have names that include provider.</span></span>

### <span data-ttu-id="5f52a-115">Exempel 2: Hämta alla spårnings källor</span><span class="sxs-lookup"><span data-stu-id="5f52a-115">Example 2: Get all trace sources</span></span>

```
PS C:\> Get-TraceSource
```

<span data-ttu-id="5f52a-116">Det här kommandot hämtar alla PowerShell-komponenter som kan spåras.</span><span class="sxs-lookup"><span data-stu-id="5f52a-116">This command gets all of the PowerShell components that can be traced.</span></span>

## <span data-ttu-id="5f52a-117">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="5f52a-117">PARAMETERS</span></span>

### <span data-ttu-id="5f52a-118">-Name</span><span class="sxs-lookup"><span data-stu-id="5f52a-118">-Name</span></span>

<span data-ttu-id="5f52a-119">Anger spårnings källorna som ska hämtas.</span><span class="sxs-lookup"><span data-stu-id="5f52a-119">Specifies the trace sources to get.</span></span>
<span data-ttu-id="5f52a-120">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="5f52a-120">Wildcards are permitted.</span></span>
<span data-ttu-id="5f52a-121">Parameter namnets *namn* är valfritt.</span><span class="sxs-lookup"><span data-stu-id="5f52a-121">The parameter name *Name* is optional.</span></span>

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

### <span data-ttu-id="5f52a-122">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5f52a-122">CommonParameters</span></span>

<span data-ttu-id="5f52a-123">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5f52a-123">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5f52a-124">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5f52a-124">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5f52a-125">INDATA</span><span class="sxs-lookup"><span data-stu-id="5f52a-125">INPUTS</span></span>

### <span data-ttu-id="5f52a-126">System. String</span><span class="sxs-lookup"><span data-stu-id="5f52a-126">System.String</span></span>

<span data-ttu-id="5f52a-127">Du kan skicka vidare en sträng som innehåller namnet på en spårnings källa till **Get-TraceSource**.</span><span class="sxs-lookup"><span data-stu-id="5f52a-127">You can pipe a string that contains the name of a trace source to **Get-TraceSource**.</span></span>

## <span data-ttu-id="5f52a-128">UTDATA</span><span class="sxs-lookup"><span data-stu-id="5f52a-128">OUTPUTS</span></span>

### <span data-ttu-id="5f52a-129">System. Management. Automation. PSTraceSource</span><span class="sxs-lookup"><span data-stu-id="5f52a-129">System.Management.Automation.PSTraceSource</span></span>

<span data-ttu-id="5f52a-130">**Get-TraceSource** returnerar objekt som representerar spårnings källorna.</span><span class="sxs-lookup"><span data-stu-id="5f52a-130">**Get-TraceSource** returns objects that represent the trace sources.</span></span>

## <span data-ttu-id="5f52a-131">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="5f52a-131">NOTES</span></span>

## <span data-ttu-id="5f52a-132">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="5f52a-132">RELATED LINKS</span></span>

[<span data-ttu-id="5f52a-133">Set-TraceSource</span><span class="sxs-lookup"><span data-stu-id="5f52a-133">Set-TraceSource</span></span>](Set-TraceSource.md)

[<span data-ttu-id="5f52a-134">Spåra-kommando</span><span class="sxs-lookup"><span data-stu-id="5f52a-134">Trace-Command</span></span>](Trace-Command.md)

