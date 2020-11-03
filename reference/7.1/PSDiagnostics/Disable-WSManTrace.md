---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-wsmantrace?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-WSManTrace
ms.openlocfilehash: 5566fb2e11311990cea76e6802c84985795c3553
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/02/2020
ms.locfileid: "93261598"
---
# <span data-ttu-id="a8573-103">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="a8573-103">Disable-WSManTrace</span></span>

## <span data-ttu-id="a8573-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="a8573-104">SYNOPSIS</span></span>
<span data-ttu-id="a8573-105">Stoppa WSMan-inloggningssessionen som startades av Enable-WSManTrace.</span><span class="sxs-lookup"><span data-stu-id="a8573-105">Stop the WSMan logging session started by Enable-WSManTrace.</span></span>

## <span data-ttu-id="a8573-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a8573-106">SYNTAX</span></span>

```
Disable-WSManTrace [<CommonParameters>]
```

## <span data-ttu-id="a8573-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a8573-107">DESCRIPTION</span></span>
<span data-ttu-id="a8573-108">Den här cmdleten stoppar WSMan-inloggningssessionen som startats av Enable-WSManTrace.</span><span class="sxs-lookup"><span data-stu-id="a8573-108">This cmdlet stops the WSMan logging session started by Enable-WSManTrace.</span></span>

<span data-ttu-id="a8573-109">Denna cmdlet använder `Stop-Trace` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a8573-109">This cmdlet uses the `Stop-Trace` cmdlet.</span></span>

<span data-ttu-id="a8573-110">Du måste köra denna cmdlet från en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="a8573-110">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="a8573-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="a8573-111">EXAMPLES</span></span>

### <span data-ttu-id="a8573-112">Exempel 1: stoppa en WSMan-spårning</span><span class="sxs-lookup"><span data-stu-id="a8573-112">Example 1: Stop a WSMan trace</span></span>

```powershell
Disable-WSManTrace
```

## <span data-ttu-id="a8573-113">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="a8573-113">PARAMETERS</span></span>

### <span data-ttu-id="a8573-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a8573-114">CommonParameters</span></span>

<span data-ttu-id="a8573-115">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a8573-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a8573-116">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a8573-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a8573-117">INDATA</span><span class="sxs-lookup"><span data-stu-id="a8573-117">INPUTS</span></span>

### <span data-ttu-id="a8573-118">Inget</span><span class="sxs-lookup"><span data-stu-id="a8573-118">None</span></span>

## <span data-ttu-id="a8573-119">UTDATA</span><span class="sxs-lookup"><span data-stu-id="a8573-119">OUTPUTS</span></span>

### <span data-ttu-id="a8573-120">Inget</span><span class="sxs-lookup"><span data-stu-id="a8573-120">None</span></span>

## <span data-ttu-id="a8573-121">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="a8573-121">NOTES</span></span>

## <span data-ttu-id="a8573-122">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="a8573-122">RELATED LINKS</span></span>

[<span data-ttu-id="a8573-123">Händelse spårning</span><span class="sxs-lookup"><span data-stu-id="a8573-123">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="a8573-124">Stoppa – spåra</span><span class="sxs-lookup"><span data-stu-id="a8573-124">Stop-Trace</span></span>](stop-trace.md)

[<span data-ttu-id="a8573-125">Aktivera – WSManTrace</span><span class="sxs-lookup"><span data-stu-id="a8573-125">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)
