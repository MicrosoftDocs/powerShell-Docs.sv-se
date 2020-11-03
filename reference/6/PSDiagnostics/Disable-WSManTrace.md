---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-wsmantrace?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-WSManTrace
ms.openlocfilehash: f7ec371e0d9826dc095fbf71c4785cae2856875b
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/02/2020
ms.locfileid: "93261547"
---
# <span data-ttu-id="3218c-103">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="3218c-103">Disable-WSManTrace</span></span>

## <span data-ttu-id="3218c-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="3218c-104">SYNOPSIS</span></span>
<span data-ttu-id="3218c-105">Stoppa WSMan-inloggningssessionen som startades av Enable-WSManTrace.</span><span class="sxs-lookup"><span data-stu-id="3218c-105">Stop the WSMan logging session started by Enable-WSManTrace.</span></span>

## <span data-ttu-id="3218c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3218c-106">SYNTAX</span></span>

```
Disable-WSManTrace [<CommonParameters>]
```

## <span data-ttu-id="3218c-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="3218c-107">DESCRIPTION</span></span>
<span data-ttu-id="3218c-108">Den här cmdleten stoppar WSMan-inloggningssessionen som startats av Enable-WSManTrace.</span><span class="sxs-lookup"><span data-stu-id="3218c-108">This cmdlet stops the WSMan logging session started by Enable-WSManTrace.</span></span>

<span data-ttu-id="3218c-109">Denna cmdlet använder `Stop-Trace` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="3218c-109">This cmdlet uses the `Stop-Trace` cmdlet.</span></span>

<span data-ttu-id="3218c-110">Du måste köra denna cmdlet från en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="3218c-110">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="3218c-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="3218c-111">EXAMPLES</span></span>

### <span data-ttu-id="3218c-112">Exempel 1: stoppa en WSMan-spårning</span><span class="sxs-lookup"><span data-stu-id="3218c-112">Example 1: Stop a WSMan trace</span></span>

```powershell
Disable-WSManTrace
```

## <span data-ttu-id="3218c-113">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="3218c-113">PARAMETERS</span></span>

### <span data-ttu-id="3218c-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3218c-114">CommonParameters</span></span>

<span data-ttu-id="3218c-115">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3218c-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3218c-116">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="3218c-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3218c-117">INDATA</span><span class="sxs-lookup"><span data-stu-id="3218c-117">INPUTS</span></span>

### <span data-ttu-id="3218c-118">Inget</span><span class="sxs-lookup"><span data-stu-id="3218c-118">None</span></span>

## <span data-ttu-id="3218c-119">UTDATA</span><span class="sxs-lookup"><span data-stu-id="3218c-119">OUTPUTS</span></span>

### <span data-ttu-id="3218c-120">Inget</span><span class="sxs-lookup"><span data-stu-id="3218c-120">None</span></span>

## <span data-ttu-id="3218c-121">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="3218c-121">NOTES</span></span>

## <span data-ttu-id="3218c-122">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="3218c-122">RELATED LINKS</span></span>

[<span data-ttu-id="3218c-123">Händelse spårning</span><span class="sxs-lookup"><span data-stu-id="3218c-123">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="3218c-124">Stoppa – spåra</span><span class="sxs-lookup"><span data-stu-id="3218c-124">Stop-Trace</span></span>](stop-trace.md)

[<span data-ttu-id="3218c-125">Aktivera – WSManTrace</span><span class="sxs-lookup"><span data-stu-id="3218c-125">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)
