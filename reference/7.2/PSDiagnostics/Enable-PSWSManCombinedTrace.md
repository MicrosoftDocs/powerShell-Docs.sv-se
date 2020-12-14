---
external help file: PSDiagnostics-help.xml
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pswsmancombinedtrace?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSWSManCombinedTrace
ms.openlocfilehash: ef333edaa091e96df11a8288e9b16f133614c1e0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709697"
---
# <span data-ttu-id="2509c-102">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="2509c-102">Enable-PSWSManCombinedTrace</span></span>

## <span data-ttu-id="2509c-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="2509c-103">SYNOPSIS</span></span>
<span data-ttu-id="2509c-104">Starta en loggningsmodul med aktiverade WSMan-och PowerShell-leverantörer.</span><span class="sxs-lookup"><span data-stu-id="2509c-104">Start a logging session with the WSMan and PowerShell providers enabled.</span></span>

## <span data-ttu-id="2509c-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="2509c-105">SYNTAX</span></span>

```
Enable-PSWSManCombinedTrace [-DoNotOverwriteExistingTrace] [<CommonParameters>]
```

## <span data-ttu-id="2509c-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="2509c-106">DESCRIPTION</span></span>

<span data-ttu-id="2509c-107">Den här cmdleten startar en loggningsmodul med följande PowerShell-leverantörer aktiverade:</span><span class="sxs-lookup"><span data-stu-id="2509c-107">This cmdlet starts a logging session with the following PowerShell providers enabled:</span></span>

- <span data-ttu-id="2509c-108">Microsoft-Windows-PowerShell</span><span class="sxs-lookup"><span data-stu-id="2509c-108">Microsoft-Windows-PowerShell</span></span>
- <span data-ttu-id="2509c-109">Microsoft-Windows-WinRM</span><span class="sxs-lookup"><span data-stu-id="2509c-109">Microsoft-Windows-WinRM</span></span>

<span data-ttu-id="2509c-110">Sessionen heter "PSTrace".</span><span class="sxs-lookup"><span data-stu-id="2509c-110">The session is named 'PSTrace'.</span></span>

<span data-ttu-id="2509c-111">Denna cmdlet använder `Start-Trace` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="2509c-111">This cmdlet uses the `Start-Trace` cmdlet.</span></span>

<span data-ttu-id="2509c-112">Du måste köra denna cmdlet från en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="2509c-112">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="2509c-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="2509c-113">EXAMPLES</span></span>

### <span data-ttu-id="2509c-114">Exempel 1: starta en kombinerad Logging-session</span><span class="sxs-lookup"><span data-stu-id="2509c-114">Example 1: Start a combined logging session</span></span>

```powershell
Enable-PSWSManCombinedTrace
```

## <span data-ttu-id="2509c-115">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="2509c-115">PARAMETERS</span></span>

### <span data-ttu-id="2509c-116">-DoNotOverwriteExistingTrace</span><span class="sxs-lookup"><span data-stu-id="2509c-116">-DoNotOverwriteExistingTrace</span></span>

<span data-ttu-id="2509c-117">Som standard skrivs händelserna till "$pshome \Traces\PSTrace.etl".</span><span class="sxs-lookup"><span data-stu-id="2509c-117">By default, the events are written to "$pshome\Traces\PSTrace.etl".</span></span> <span data-ttu-id="2509c-118">När den här parametern används skapar cmdleten ett unikt fil namn: "$pshome \Traces\ PSTrace_ {GUID}. etl"</span><span class="sxs-lookup"><span data-stu-id="2509c-118">When this parameter is used, the cmdlet creates a unique filename: "$pshome\Traces\PSTrace_{guid}.etl"</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="2509c-119">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="2509c-119">CommonParameters</span></span>

<span data-ttu-id="2509c-120">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="2509c-120">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="2509c-121">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="2509c-121">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="2509c-122">INDATA</span><span class="sxs-lookup"><span data-stu-id="2509c-122">INPUTS</span></span>

### <span data-ttu-id="2509c-123">Inga</span><span class="sxs-lookup"><span data-stu-id="2509c-123">None</span></span>

## <span data-ttu-id="2509c-124">UTDATA</span><span class="sxs-lookup"><span data-stu-id="2509c-124">OUTPUTS</span></span>

### <span data-ttu-id="2509c-125">Inga</span><span class="sxs-lookup"><span data-stu-id="2509c-125">None</span></span>

## <span data-ttu-id="2509c-126">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="2509c-126">NOTES</span></span>

## <span data-ttu-id="2509c-127">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="2509c-127">RELATED LINKS</span></span>

[<span data-ttu-id="2509c-128">Händelse spårning</span><span class="sxs-lookup"><span data-stu-id="2509c-128">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="2509c-129">Starta spårning</span><span class="sxs-lookup"><span data-stu-id="2509c-129">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="2509c-130">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="2509c-130">Disable-PSWSManCombinedTrace</span></span>](Disable-PSWSManCombinedTrace.md)

