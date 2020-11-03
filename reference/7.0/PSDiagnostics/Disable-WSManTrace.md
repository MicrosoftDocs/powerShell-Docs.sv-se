---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-wsmantrace?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-WSManTrace
ms.openlocfilehash: 5e91477cd840e895c25207bd5355686e0c24d473
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/02/2020
ms.locfileid: "93261699"
---
# <span data-ttu-id="bd914-103">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="bd914-103">Disable-WSManTrace</span></span>

## <span data-ttu-id="bd914-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="bd914-104">SYNOPSIS</span></span>
<span data-ttu-id="bd914-105">Stoppa WSMan-inloggningssessionen som startades av Enable-WSManTrace.</span><span class="sxs-lookup"><span data-stu-id="bd914-105">Stop the WSMan logging session started by Enable-WSManTrace.</span></span>

## <span data-ttu-id="bd914-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bd914-106">SYNTAX</span></span>

```
Disable-WSManTrace [<CommonParameters>]
```

## <span data-ttu-id="bd914-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="bd914-107">DESCRIPTION</span></span>
<span data-ttu-id="bd914-108">Den här cmdleten stoppar WSMan-inloggningssessionen som startats av Enable-WSManTrace.</span><span class="sxs-lookup"><span data-stu-id="bd914-108">This cmdlet stops the WSMan logging session started by Enable-WSManTrace.</span></span>

<span data-ttu-id="bd914-109">Denna cmdlet använder `Stop-Trace` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="bd914-109">This cmdlet uses the `Stop-Trace` cmdlet.</span></span>

<span data-ttu-id="bd914-110">Du måste köra denna cmdlet från en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="bd914-110">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="bd914-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="bd914-111">EXAMPLES</span></span>

### <span data-ttu-id="bd914-112">Exempel 1: stoppa en WSMan-spårning</span><span class="sxs-lookup"><span data-stu-id="bd914-112">Example 1: Stop a WSMan trace</span></span>

```powershell
Disable-WSManTrace
```

## <span data-ttu-id="bd914-113">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="bd914-113">PARAMETERS</span></span>

### <span data-ttu-id="bd914-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bd914-114">CommonParameters</span></span>

<span data-ttu-id="bd914-115">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bd914-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bd914-116">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="bd914-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bd914-117">INDATA</span><span class="sxs-lookup"><span data-stu-id="bd914-117">INPUTS</span></span>

### <span data-ttu-id="bd914-118">Inget</span><span class="sxs-lookup"><span data-stu-id="bd914-118">None</span></span>

## <span data-ttu-id="bd914-119">UTDATA</span><span class="sxs-lookup"><span data-stu-id="bd914-119">OUTPUTS</span></span>

### <span data-ttu-id="bd914-120">Inget</span><span class="sxs-lookup"><span data-stu-id="bd914-120">None</span></span>

## <span data-ttu-id="bd914-121">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="bd914-121">NOTES</span></span>

## <span data-ttu-id="bd914-122">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="bd914-122">RELATED LINKS</span></span>

[<span data-ttu-id="bd914-123">Händelse spårning</span><span class="sxs-lookup"><span data-stu-id="bd914-123">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="bd914-124">Stoppa – spåra</span><span class="sxs-lookup"><span data-stu-id="bd914-124">Stop-Trace</span></span>](stop-trace.md)

[<span data-ttu-id="bd914-125">Aktivera – WSManTrace</span><span class="sxs-lookup"><span data-stu-id="bd914-125">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)
