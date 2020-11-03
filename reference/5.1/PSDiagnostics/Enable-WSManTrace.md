---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-wsmantrace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-WSManTrace
ms.openlocfilehash: 08c9d61f210761e2ed7a3a5014812b2bd362201b
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264729"
---
# <span data-ttu-id="c39a9-103">Enable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="c39a9-103">Enable-WSManTrace</span></span>

## <span data-ttu-id="c39a9-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="c39a9-104">SYNOPSIS</span></span>
<span data-ttu-id="c39a9-105">Starta en inloggningssession med aktiverade WSMan-providers.</span><span class="sxs-lookup"><span data-stu-id="c39a9-105">Start a logging session with the WSMan providers enabled.</span></span>

## <span data-ttu-id="c39a9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c39a9-106">SYNTAX</span></span>

```
Enable-WSManTrace [<CommonParameters>]
```

## <span data-ttu-id="c39a9-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="c39a9-107">DESCRIPTION</span></span>
<span data-ttu-id="c39a9-108">Den här cmdleten startar en loggningsmodul med aktiverade WSMan-providers.</span><span class="sxs-lookup"><span data-stu-id="c39a9-108">This cmdlet starts a logging session with the WSMan providers enabled.</span></span> <span data-ttu-id="c39a9-109">Följande händelse leverantörer är aktiverade:</span><span class="sxs-lookup"><span data-stu-id="c39a9-109">The following event providers are enabled:</span></span>

- <span data-ttu-id="c39a9-110">Vidarebefordran av händelser</span><span class="sxs-lookup"><span data-stu-id="c39a9-110">Event Forwarding</span></span>
- <span data-ttu-id="c39a9-111">IpmiDrv</span><span class="sxs-lookup"><span data-stu-id="c39a9-111">IpmiDrv</span></span>
- <span data-ttu-id="c39a9-112">IPMIPrv</span><span class="sxs-lookup"><span data-stu-id="c39a9-112">IPMIPrv</span></span>
- <span data-ttu-id="c39a9-113">WinRM</span><span class="sxs-lookup"><span data-stu-id="c39a9-113">WinRM</span></span>
- <span data-ttu-id="c39a9-114">WinrsCmd</span><span class="sxs-lookup"><span data-stu-id="c39a9-114">WinrsCmd</span></span>
- <span data-ttu-id="c39a9-115">WinrsExe</span><span class="sxs-lookup"><span data-stu-id="c39a9-115">WinrsExe</span></span>
- <span data-ttu-id="c39a9-116">WinrsMgr</span><span class="sxs-lookup"><span data-stu-id="c39a9-116">WinrsMgr</span></span>
- <span data-ttu-id="c39a9-117">WSManProvHost</span><span class="sxs-lookup"><span data-stu-id="c39a9-117">WSManProvHost</span></span>

<span data-ttu-id="c39a9-118">Sessionen heter "wsmlog".</span><span class="sxs-lookup"><span data-stu-id="c39a9-118">The session is named 'wsmlog'.</span></span>

<span data-ttu-id="c39a9-119">Denna cmdlet använder `Start-Trace` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c39a9-119">This cmdlet uses the `Start-Trace` cmdlet.</span></span>

<span data-ttu-id="c39a9-120">Du måste köra denna cmdlet från en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="c39a9-120">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="c39a9-121">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="c39a9-121">EXAMPLES</span></span>

### <span data-ttu-id="c39a9-122">Exempel 1: starta en WSMan-inloggningssession.</span><span class="sxs-lookup"><span data-stu-id="c39a9-122">Example 1: Start a WSMan logging session.</span></span>

```powershell
Enable-WSManTrace
```

## <span data-ttu-id="c39a9-123">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="c39a9-123">PARAMETERS</span></span>

### <span data-ttu-id="c39a9-124">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c39a9-124">CommonParameters</span></span>

<span data-ttu-id="c39a9-125">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c39a9-125">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c39a9-126">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c39a9-126">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c39a9-127">INDATA</span><span class="sxs-lookup"><span data-stu-id="c39a9-127">INPUTS</span></span>

### <span data-ttu-id="c39a9-128">Inget</span><span class="sxs-lookup"><span data-stu-id="c39a9-128">None</span></span>

## <span data-ttu-id="c39a9-129">UTDATA</span><span class="sxs-lookup"><span data-stu-id="c39a9-129">OUTPUTS</span></span>

### <span data-ttu-id="c39a9-130">System. Object</span><span class="sxs-lookup"><span data-stu-id="c39a9-130">System.Object</span></span>

## <span data-ttu-id="c39a9-131">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="c39a9-131">NOTES</span></span>

## <span data-ttu-id="c39a9-132">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="c39a9-132">RELATED LINKS</span></span>

[<span data-ttu-id="c39a9-133">Händelse spårning</span><span class="sxs-lookup"><span data-stu-id="c39a9-133">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="c39a9-134">Starta spårning</span><span class="sxs-lookup"><span data-stu-id="c39a9-134">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="c39a9-135">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="c39a9-135">Disable-WSManTrace</span></span>](Disable-WSManTrace.md)
