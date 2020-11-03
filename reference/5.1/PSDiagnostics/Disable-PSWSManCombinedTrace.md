---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-pswsmancombinedtrace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSWSManCombinedTrace
ms.openlocfilehash: 4a98941de072b9b57b89a25bc180c0ee391d8b63
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264747"
---
# <span data-ttu-id="7a64a-103">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="7a64a-103">Disable-PSWSManCombinedTrace</span></span>

## <span data-ttu-id="7a64a-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="7a64a-104">SYNOPSIS</span></span>
<span data-ttu-id="7a64a-105">Stoppa inloggningssessionen som startats av Enable-PSWSManCombinedTrace.</span><span class="sxs-lookup"><span data-stu-id="7a64a-105">Stop the logging session started by Enable-PSWSManCombinedTrace.</span></span>

## <span data-ttu-id="7a64a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="7a64a-106">SYNTAX</span></span>

```
Disable-PSWSManCombinedTrace [<CommonParameters>]
```

## <span data-ttu-id="7a64a-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="7a64a-107">DESCRIPTION</span></span>

<span data-ttu-id="7a64a-108">Denna cmdlet stoppar inloggningssessionen som startats av `Enable-PSWSManCombinedTrace` .</span><span class="sxs-lookup"><span data-stu-id="7a64a-108">This cmdlet stops the logging session started by `Enable-PSWSManCombinedTrace`.</span></span>

<span data-ttu-id="7a64a-109">Denna cmdlet använder `Stop-Trace` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7a64a-109">This cmdlet uses the `Stop-Trace` cmdlet.</span></span>

<span data-ttu-id="7a64a-110">Du måste köra denna cmdlet från en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="7a64a-110">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="7a64a-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="7a64a-111">EXAMPLES</span></span>

### <span data-ttu-id="7a64a-112">Exempel 1: inaktivera den kombinerade inloggningssessionen</span><span class="sxs-lookup"><span data-stu-id="7a64a-112">Example 1: Disable the combined logging session</span></span>

```powershell
Disable-PSWSManCombinedTrace
```

## <span data-ttu-id="7a64a-113">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="7a64a-113">PARAMETERS</span></span>

### <span data-ttu-id="7a64a-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="7a64a-114">CommonParameters</span></span>

<span data-ttu-id="7a64a-115">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="7a64a-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="7a64a-116">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="7a64a-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="7a64a-117">INDATA</span><span class="sxs-lookup"><span data-stu-id="7a64a-117">INPUTS</span></span>

### <span data-ttu-id="7a64a-118">Inget</span><span class="sxs-lookup"><span data-stu-id="7a64a-118">None</span></span>

## <span data-ttu-id="7a64a-119">UTDATA</span><span class="sxs-lookup"><span data-stu-id="7a64a-119">OUTPUTS</span></span>

### <span data-ttu-id="7a64a-120">System. Object</span><span class="sxs-lookup"><span data-stu-id="7a64a-120">System.Object</span></span>

## <span data-ttu-id="7a64a-121">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="7a64a-121">NOTES</span></span>

## <span data-ttu-id="7a64a-122">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="7a64a-122">RELATED LINKS</span></span>

[<span data-ttu-id="7a64a-123">Händelse spårning</span><span class="sxs-lookup"><span data-stu-id="7a64a-123">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="7a64a-124">Stoppa – spåra</span><span class="sxs-lookup"><span data-stu-id="7a64a-124">Stop-Trace</span></span>](stop-trace.md)

[<span data-ttu-id="7a64a-125">Aktivera – PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="7a64a-125">Enable-PSWSManCombinedTrace</span></span>](Enable-PSWSManCombinedTrace.md)
