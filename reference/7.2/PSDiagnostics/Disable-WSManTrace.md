---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-wsmantrace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-WSManTrace
ms.openlocfilehash: 647a7676eddf2175bf29e02b3482cc9c7c4d8ebe
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709060"
---
# <span data-ttu-id="59bd2-102">Disable-WSManTrace</span><span class="sxs-lookup"><span data-stu-id="59bd2-102">Disable-WSManTrace</span></span>

## <span data-ttu-id="59bd2-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="59bd2-103">SYNOPSIS</span></span>
<span data-ttu-id="59bd2-104">Stoppa WSMan-inloggningssessionen som startades av Enable-WSManTrace.</span><span class="sxs-lookup"><span data-stu-id="59bd2-104">Stop the WSMan logging session started by Enable-WSManTrace.</span></span>

## <span data-ttu-id="59bd2-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="59bd2-105">SYNTAX</span></span>

```
Disable-WSManTrace [<CommonParameters>]
```

## <span data-ttu-id="59bd2-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="59bd2-106">DESCRIPTION</span></span>
<span data-ttu-id="59bd2-107">Den här cmdleten stoppar WSMan-inloggningssessionen som startats av Enable-WSManTrace.</span><span class="sxs-lookup"><span data-stu-id="59bd2-107">This cmdlet stops the WSMan logging session started by Enable-WSManTrace.</span></span>

<span data-ttu-id="59bd2-108">Denna cmdlet använder `Stop-Trace` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="59bd2-108">This cmdlet uses the `Stop-Trace` cmdlet.</span></span>

<span data-ttu-id="59bd2-109">Du måste köra denna cmdlet från en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="59bd2-109">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="59bd2-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="59bd2-110">EXAMPLES</span></span>

### <span data-ttu-id="59bd2-111">Exempel 1: stoppa en WSMan-spårning</span><span class="sxs-lookup"><span data-stu-id="59bd2-111">Example 1: Stop a WSMan trace</span></span>

```powershell
Disable-WSManTrace
```

## <span data-ttu-id="59bd2-112">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="59bd2-112">PARAMETERS</span></span>

### <span data-ttu-id="59bd2-113">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="59bd2-113">CommonParameters</span></span>

<span data-ttu-id="59bd2-114">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="59bd2-114">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="59bd2-115">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="59bd2-115">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="59bd2-116">INDATA</span><span class="sxs-lookup"><span data-stu-id="59bd2-116">INPUTS</span></span>

### <span data-ttu-id="59bd2-117">Inga</span><span class="sxs-lookup"><span data-stu-id="59bd2-117">None</span></span>

## <span data-ttu-id="59bd2-118">UTDATA</span><span class="sxs-lookup"><span data-stu-id="59bd2-118">OUTPUTS</span></span>

### <span data-ttu-id="59bd2-119">Inga</span><span class="sxs-lookup"><span data-stu-id="59bd2-119">None</span></span>

## <span data-ttu-id="59bd2-120">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="59bd2-120">NOTES</span></span>

## <span data-ttu-id="59bd2-121">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="59bd2-121">RELATED LINKS</span></span>

[<span data-ttu-id="59bd2-122">Händelse spårning</span><span class="sxs-lookup"><span data-stu-id="59bd2-122">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="59bd2-123">Stoppa – spåra</span><span class="sxs-lookup"><span data-stu-id="59bd2-123">Stop-Trace</span></span>](stop-trace.md)

[<span data-ttu-id="59bd2-124">Aktivera – WSManTrace</span><span class="sxs-lookup"><span data-stu-id="59bd2-124">Enable-WSManTrace</span></span>](Enable-WSManTrace.md)

