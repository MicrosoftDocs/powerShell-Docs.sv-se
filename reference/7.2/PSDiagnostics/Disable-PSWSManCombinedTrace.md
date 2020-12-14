---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/disable-pswsmancombinedtrace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSWSManCombinedTrace
ms.openlocfilehash: 690a8b050fd0e16033a585df210db340f41a83a3
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708299"
---
# <span data-ttu-id="44b97-102">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="44b97-102">Disable-PSWSManCombinedTrace</span></span>

## <span data-ttu-id="44b97-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="44b97-103">SYNOPSIS</span></span>
<span data-ttu-id="44b97-104">Stoppa inloggningssessionen som startats av Enable-PSWSManCombinedTrace.</span><span class="sxs-lookup"><span data-stu-id="44b97-104">Stop the logging session started by Enable-PSWSManCombinedTrace.</span></span>

## <span data-ttu-id="44b97-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="44b97-105">SYNTAX</span></span>

```
Disable-PSWSManCombinedTrace [<CommonParameters>]
```

## <span data-ttu-id="44b97-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="44b97-106">DESCRIPTION</span></span>

<span data-ttu-id="44b97-107">Denna cmdlet stoppar inloggningssessionen som startats av `Enable-PSWSManCombinedTrace` .</span><span class="sxs-lookup"><span data-stu-id="44b97-107">This cmdlet stops the logging session started by `Enable-PSWSManCombinedTrace`.</span></span>

<span data-ttu-id="44b97-108">Denna cmdlet använder `Stop-Trace` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="44b97-108">This cmdlet uses the `Stop-Trace` cmdlet.</span></span>

<span data-ttu-id="44b97-109">Du måste köra denna cmdlet från en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="44b97-109">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="44b97-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="44b97-110">EXAMPLES</span></span>

### <span data-ttu-id="44b97-111">Exempel 1: inaktivera den kombinerade inloggningssessionen</span><span class="sxs-lookup"><span data-stu-id="44b97-111">Example 1: Disable the combined logging session</span></span>

```powershell
Disable-PSWSManCombinedTrace
```

## <span data-ttu-id="44b97-112">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="44b97-112">PARAMETERS</span></span>

### <span data-ttu-id="44b97-113">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="44b97-113">CommonParameters</span></span>

<span data-ttu-id="44b97-114">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="44b97-114">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="44b97-115">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="44b97-115">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="44b97-116">INDATA</span><span class="sxs-lookup"><span data-stu-id="44b97-116">INPUTS</span></span>

### <span data-ttu-id="44b97-117">Inga</span><span class="sxs-lookup"><span data-stu-id="44b97-117">None</span></span>

## <span data-ttu-id="44b97-118">UTDATA</span><span class="sxs-lookup"><span data-stu-id="44b97-118">OUTPUTS</span></span>

### <span data-ttu-id="44b97-119">Inga</span><span class="sxs-lookup"><span data-stu-id="44b97-119">None</span></span>

## <span data-ttu-id="44b97-120">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="44b97-120">NOTES</span></span>

## <span data-ttu-id="44b97-121">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="44b97-121">RELATED LINKS</span></span>

[<span data-ttu-id="44b97-122">Händelse spårning</span><span class="sxs-lookup"><span data-stu-id="44b97-122">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="44b97-123">Stoppa – spåra</span><span class="sxs-lookup"><span data-stu-id="44b97-123">Stop-Trace</span></span>](stop-trace.md)

[<span data-ttu-id="44b97-124">Aktivera – PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="44b97-124">Enable-PSWSManCombinedTrace</span></span>](Enable-PSWSManCombinedTrace.md)

