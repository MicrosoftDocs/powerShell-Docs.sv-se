---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pswsmancombinedtrace?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSWSManCombinedTrace
ms.openlocfilehash: f67b5d9fe8da48cca5fd4ec7d2056a4702d3ff16
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264734"
---
# <span data-ttu-id="c89db-103">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="c89db-103">Enable-PSWSManCombinedTrace</span></span>

## <span data-ttu-id="c89db-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="c89db-104">SYNOPSIS</span></span>
<span data-ttu-id="c89db-105">Starta en loggningsmodul med aktiverade WSMan-och PowerShell-leverantörer.</span><span class="sxs-lookup"><span data-stu-id="c89db-105">Start a logging session with the WSMan and PowerShell providers enabled.</span></span>

## <span data-ttu-id="c89db-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="c89db-106">SYNTAX</span></span>

```
Enable-PSWSManCombinedTrace [-DoNotOverwriteExistingTrace] [<CommonParameters>]
```

## <span data-ttu-id="c89db-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="c89db-107">DESCRIPTION</span></span>

<span data-ttu-id="c89db-108">Den här cmdleten startar en loggningsmodul med följande PowerShell-leverantörer aktiverade:</span><span class="sxs-lookup"><span data-stu-id="c89db-108">This cmdlet starts a logging session with the following PowerShell providers enabled:</span></span>

- <span data-ttu-id="c89db-109">Microsoft-Windows-PowerShell</span><span class="sxs-lookup"><span data-stu-id="c89db-109">Microsoft-Windows-PowerShell</span></span>
- <span data-ttu-id="c89db-110">Microsoft-Windows-WinRM</span><span class="sxs-lookup"><span data-stu-id="c89db-110">Microsoft-Windows-WinRM</span></span>

<span data-ttu-id="c89db-111">Sessionen heter "PSTrace".</span><span class="sxs-lookup"><span data-stu-id="c89db-111">The session is named 'PSTrace'.</span></span>

<span data-ttu-id="c89db-112">Denna cmdlet använder `Start-Trace` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c89db-112">This cmdlet uses the `Start-Trace` cmdlet.</span></span>

<span data-ttu-id="c89db-113">Du måste köra denna cmdlet från en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="c89db-113">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="c89db-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="c89db-114">EXAMPLES</span></span>

### <span data-ttu-id="c89db-115">Exempel 1: starta en kombinerad Logging-session</span><span class="sxs-lookup"><span data-stu-id="c89db-115">Example 1: Start a combined logging session</span></span>

```powershell
Enable-PSWSManCombinedTrace
```

## <span data-ttu-id="c89db-116">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="c89db-116">PARAMETERS</span></span>

### <span data-ttu-id="c89db-117">-DoNotOverwriteExistingTrace</span><span class="sxs-lookup"><span data-stu-id="c89db-117">-DoNotOverwriteExistingTrace</span></span>

<span data-ttu-id="c89db-118">Som standard skrivs händelserna till "$pshome \Traces\PSTrace.etl".</span><span class="sxs-lookup"><span data-stu-id="c89db-118">By default, the events are written to "$pshome\Traces\PSTrace.etl".</span></span> <span data-ttu-id="c89db-119">När den här parametern används skapar cmdleten ett unikt fil namn: "$pshome \Traces\ PSTrace_ {GUID}. etl"</span><span class="sxs-lookup"><span data-stu-id="c89db-119">When this parameter is used, the cmdlet creates a unique filename: "$pshome\Traces\PSTrace_{guid}.etl"</span></span>

```yaml
Type: SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="c89db-120">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="c89db-120">CommonParameters</span></span>

<span data-ttu-id="c89db-121">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="c89db-121">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="c89db-122">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="c89db-122">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="c89db-123">INDATA</span><span class="sxs-lookup"><span data-stu-id="c89db-123">INPUTS</span></span>

### <span data-ttu-id="c89db-124">Inget</span><span class="sxs-lookup"><span data-stu-id="c89db-124">None</span></span>

## <span data-ttu-id="c89db-125">UTDATA</span><span class="sxs-lookup"><span data-stu-id="c89db-125">OUTPUTS</span></span>

### <span data-ttu-id="c89db-126">System. Object</span><span class="sxs-lookup"><span data-stu-id="c89db-126">System.Object</span></span>

## <span data-ttu-id="c89db-127">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="c89db-127">NOTES</span></span>

## <span data-ttu-id="c89db-128">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="c89db-128">RELATED LINKS</span></span>

[<span data-ttu-id="c89db-129">Händelse spårning</span><span class="sxs-lookup"><span data-stu-id="c89db-129">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="c89db-130">Starta spårning</span><span class="sxs-lookup"><span data-stu-id="c89db-130">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="c89db-131">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="c89db-131">Disable-PSWSManCombinedTrace</span></span>](Disable-PSWSManCombinedTrace.md)
