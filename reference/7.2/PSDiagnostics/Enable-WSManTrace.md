---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-wsmantrace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-WSManTrace
ms.openlocfilehash: a9d91eab94666186c13f8d5c928d83055f6dbefa
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709312"
---
# <span data-ttu-id="d23fe-102">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="d23fe-102">Enable-WSManTrace</span></span>

## <span data-ttu-id="d23fe-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="d23fe-103">SYNOPSIS</span></span>
<span data-ttu-id="d23fe-104">Starta en inloggningssession med aktiverade WSMan-providers.</span><span class="sxs-lookup"><span data-stu-id="d23fe-104">Start a logging session with the WSMan providers enabled.</span></span>

## <span data-ttu-id="d23fe-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d23fe-105">SYNTAX</span></span>

```
Enable-WSManTrace [<CommonParameters>]
```

## <span data-ttu-id="d23fe-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="d23fe-106">DESCRIPTION</span></span>
<span data-ttu-id="d23fe-107">Den här cmdleten startar en loggningsmodul med aktiverade WSMan-providers.</span><span class="sxs-lookup"><span data-stu-id="d23fe-107">This cmdlet starts a logging session with the WSMan providers enabled.</span></span> <span data-ttu-id="d23fe-108">Följande händelse leverantörer är aktiverade:</span><span class="sxs-lookup"><span data-stu-id="d23fe-108">The following event providers are enabled:</span></span>

- <span data-ttu-id="d23fe-109">Vidarebefordran av händelser</span><span class="sxs-lookup"><span data-stu-id="d23fe-109">Event Forwarding</span></span>
- <span data-ttu-id="d23fe-110">IpmiDrv</span><span class="sxs-lookup"><span data-stu-id="d23fe-110">IpmiDrv</span></span>
- <span data-ttu-id="d23fe-111">IPMIPrv</span><span class="sxs-lookup"><span data-stu-id="d23fe-111">IPMIPrv</span></span>
- <span data-ttu-id="d23fe-112">WinRM</span><span class="sxs-lookup"><span data-stu-id="d23fe-112">WinRM</span></span>
- <span data-ttu-id="d23fe-113">WinrsCmd</span><span class="sxs-lookup"><span data-stu-id="d23fe-113">WinrsCmd</span></span>
- <span data-ttu-id="d23fe-114">WinrsExe</span><span class="sxs-lookup"><span data-stu-id="d23fe-114">WinrsExe</span></span>
- <span data-ttu-id="d23fe-115">WinrsMgr</span><span class="sxs-lookup"><span data-stu-id="d23fe-115">WinrsMgr</span></span>
- <span data-ttu-id="d23fe-116">WSManProvHost</span><span class="sxs-lookup"><span data-stu-id="d23fe-116">WSManProvHost</span></span>

<span data-ttu-id="d23fe-117">Sessionen heter "wsmlog".</span><span class="sxs-lookup"><span data-stu-id="d23fe-117">The session is named 'wsmlog'.</span></span>

<span data-ttu-id="d23fe-118">Denna cmdlet använder `Start-Trace` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="d23fe-118">This cmdlet uses the `Start-Trace` cmdlet.</span></span>

<span data-ttu-id="d23fe-119">Du måste köra denna cmdlet från en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="d23fe-119">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="d23fe-120">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="d23fe-120">EXAMPLES</span></span>

### <span data-ttu-id="d23fe-121">Exempel 1: starta en WSMan-inloggningssession.</span><span class="sxs-lookup"><span data-stu-id="d23fe-121">Example 1: Start a WSMan logging session.</span></span>

```powershell
Enable-WSManTrace
```

## <span data-ttu-id="d23fe-122">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="d23fe-122">PARAMETERS</span></span>

### <span data-ttu-id="d23fe-123">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d23fe-123">CommonParameters</span></span>

<span data-ttu-id="d23fe-124">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d23fe-124">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d23fe-125">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d23fe-125">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d23fe-126">INDATA</span><span class="sxs-lookup"><span data-stu-id="d23fe-126">INPUTS</span></span>

### <span data-ttu-id="d23fe-127">Inga</span><span class="sxs-lookup"><span data-stu-id="d23fe-127">None</span></span>

## <span data-ttu-id="d23fe-128">UTDATA</span><span class="sxs-lookup"><span data-stu-id="d23fe-128">OUTPUTS</span></span>

### <span data-ttu-id="d23fe-129">Inga</span><span class="sxs-lookup"><span data-stu-id="d23fe-129">None</span></span>

## <span data-ttu-id="d23fe-130">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="d23fe-130">NOTES</span></span>

## <span data-ttu-id="d23fe-131">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="d23fe-131">RELATED LINKS</span></span>

[<span data-ttu-id="d23fe-132">Händelse spårning</span><span class="sxs-lookup"><span data-stu-id="d23fe-132">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="d23fe-133">Starta spårning</span><span class="sxs-lookup"><span data-stu-id="d23fe-133">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="d23fe-134">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="d23fe-134">Disable-WSManTrace</span></span>](Disable-WSManTrace.md)

