---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-pswsmancombinedtrace?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSWSManCombinedTrace
ms.openlocfilehash: dc817a2f8629744ce4bdcf428530713e76c3d044
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/02/2020
ms.locfileid: "93261551"
---
# <span data-ttu-id="4477e-103">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="4477e-103">Disable-PSWSManCombinedTrace</span></span>

## <span data-ttu-id="4477e-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="4477e-104">SYNOPSIS</span></span>
<span data-ttu-id="4477e-105">Stoppa inloggningssessionen som startats av Enable-PSWSManCombinedTrace.</span><span class="sxs-lookup"><span data-stu-id="4477e-105">Stop the logging session started by Enable-PSWSManCombinedTrace.</span></span>

## <span data-ttu-id="4477e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4477e-106">SYNTAX</span></span>

```
Disable-PSWSManCombinedTrace [<CommonParameters>]
```

## <span data-ttu-id="4477e-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="4477e-107">DESCRIPTION</span></span>

<span data-ttu-id="4477e-108">Denna cmdlet stoppar inloggningssessionen som startats av `Enable-PSWSManCombinedTrace` .</span><span class="sxs-lookup"><span data-stu-id="4477e-108">This cmdlet stops the logging session started by `Enable-PSWSManCombinedTrace`.</span></span>

<span data-ttu-id="4477e-109">Denna cmdlet använder `Stop-Trace` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4477e-109">This cmdlet uses the `Stop-Trace` cmdlet.</span></span>

<span data-ttu-id="4477e-110">Du måste köra denna cmdlet från en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="4477e-110">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="4477e-111">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="4477e-111">EXAMPLES</span></span>

### <span data-ttu-id="4477e-112">Exempel 1: inaktivera den kombinerade inloggningssessionen</span><span class="sxs-lookup"><span data-stu-id="4477e-112">Example 1: Disable the combined logging session</span></span>

```powershell
Disable-PSWSManCombinedTrace
```

## <span data-ttu-id="4477e-113">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="4477e-113">PARAMETERS</span></span>

### <span data-ttu-id="4477e-114">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4477e-114">CommonParameters</span></span>

<span data-ttu-id="4477e-115">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4477e-115">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4477e-116">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4477e-116">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4477e-117">INDATA</span><span class="sxs-lookup"><span data-stu-id="4477e-117">INPUTS</span></span>

### <span data-ttu-id="4477e-118">Inget</span><span class="sxs-lookup"><span data-stu-id="4477e-118">None</span></span>

## <span data-ttu-id="4477e-119">UTDATA</span><span class="sxs-lookup"><span data-stu-id="4477e-119">OUTPUTS</span></span>

### <span data-ttu-id="4477e-120">Inget</span><span class="sxs-lookup"><span data-stu-id="4477e-120">None</span></span>

## <span data-ttu-id="4477e-121">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="4477e-121">NOTES</span></span>

## <span data-ttu-id="4477e-122">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="4477e-122">RELATED LINKS</span></span>

[<span data-ttu-id="4477e-123">Händelse spårning</span><span class="sxs-lookup"><span data-stu-id="4477e-123">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="4477e-124">Stoppa – spåra</span><span class="sxs-lookup"><span data-stu-id="4477e-124">Stop-Trace</span></span>](stop-trace.md)

[<span data-ttu-id="4477e-125">Aktivera – PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="4477e-125">Enable-PSWSManCombinedTrace</span></span>](Enable-PSWSManCombinedTrace.md)
