---
external help file: PSDiagnostics-help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSDiagnostics
ms.date: 11/29/2018
online version: https://docs.microsoft.com/powershell/module/psdiagnostics/enable-pswsmancombinedtrace?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Enable-PSWSManCombinedTrace
ms.openlocfilehash: f6b14ea6cda7d83792f7b51b854471a2cb62bfb5
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93261890"
---
# <span data-ttu-id="52cd1-103">Enable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="52cd1-103">Enable-PSWSManCombinedTrace</span></span>

## <span data-ttu-id="52cd1-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="52cd1-104">SYNOPSIS</span></span>
<span data-ttu-id="52cd1-105">Starta en loggningsmodul med aktiverade WSMan-och PowerShell-leverantörer.</span><span class="sxs-lookup"><span data-stu-id="52cd1-105">Start a logging session with the WSMan and PowerShell providers enabled.</span></span>

## <span data-ttu-id="52cd1-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="52cd1-106">SYNTAX</span></span>

```
Enable-PSWSManCombinedTrace [-DoNotOverwriteExistingTrace] [<CommonParameters>]
```

## <span data-ttu-id="52cd1-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="52cd1-107">DESCRIPTION</span></span>

<span data-ttu-id="52cd1-108">Den här cmdleten startar en loggningsmodul med följande PowerShell-leverantörer aktiverade:</span><span class="sxs-lookup"><span data-stu-id="52cd1-108">This cmdlet starts a logging session with the following PowerShell providers enabled:</span></span>

- <span data-ttu-id="52cd1-109">Microsoft-Windows-PowerShell</span><span class="sxs-lookup"><span data-stu-id="52cd1-109">Microsoft-Windows-PowerShell</span></span>
- <span data-ttu-id="52cd1-110">Microsoft-Windows-WinRM</span><span class="sxs-lookup"><span data-stu-id="52cd1-110">Microsoft-Windows-WinRM</span></span>

<span data-ttu-id="52cd1-111">Sessionen heter "PSTrace".</span><span class="sxs-lookup"><span data-stu-id="52cd1-111">The session is named 'PSTrace'.</span></span>

<span data-ttu-id="52cd1-112">Denna cmdlet använder `Start-Trace` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="52cd1-112">This cmdlet uses the `Start-Trace` cmdlet.</span></span>

<span data-ttu-id="52cd1-113">Du måste köra denna cmdlet från en upphöjd PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="52cd1-113">You must run this cmdlet from an elevated PowerShell session.</span></span>

## <span data-ttu-id="52cd1-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="52cd1-114">EXAMPLES</span></span>

### <span data-ttu-id="52cd1-115">Exempel 1: starta en kombinerad Logging-session</span><span class="sxs-lookup"><span data-stu-id="52cd1-115">Example 1: Start a combined logging session</span></span>

```powershell
Enable-PSWSManCombinedTrace
```

## <span data-ttu-id="52cd1-116">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="52cd1-116">PARAMETERS</span></span>

### <span data-ttu-id="52cd1-117">-DoNotOverwriteExistingTrace</span><span class="sxs-lookup"><span data-stu-id="52cd1-117">-DoNotOverwriteExistingTrace</span></span>

<span data-ttu-id="52cd1-118">Som standard skrivs händelserna till "$pshome \Traces\PSTrace.etl".</span><span class="sxs-lookup"><span data-stu-id="52cd1-118">By default, the events are written to "$pshome\Traces\PSTrace.etl".</span></span> <span data-ttu-id="52cd1-119">När den här parametern används skapar cmdleten ett unikt fil namn: "$pshome \Traces\ PSTrace_ {GUID}. etl"</span><span class="sxs-lookup"><span data-stu-id="52cd1-119">When this parameter is used, the cmdlet creates a unique filename: "$pshome\Traces\PSTrace_{guid}.etl"</span></span>

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

### <span data-ttu-id="52cd1-120">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="52cd1-120">CommonParameters</span></span>

<span data-ttu-id="52cd1-121">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="52cd1-121">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="52cd1-122">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="52cd1-122">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="52cd1-123">INDATA</span><span class="sxs-lookup"><span data-stu-id="52cd1-123">INPUTS</span></span>

### <span data-ttu-id="52cd1-124">Inget</span><span class="sxs-lookup"><span data-stu-id="52cd1-124">None</span></span>

## <span data-ttu-id="52cd1-125">UTDATA</span><span class="sxs-lookup"><span data-stu-id="52cd1-125">OUTPUTS</span></span>

### <span data-ttu-id="52cd1-126">Inget</span><span class="sxs-lookup"><span data-stu-id="52cd1-126">None</span></span>

## <span data-ttu-id="52cd1-127">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="52cd1-127">NOTES</span></span>

## <span data-ttu-id="52cd1-128">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="52cd1-128">RELATED LINKS</span></span>

[<span data-ttu-id="52cd1-129">Händelse spårning</span><span class="sxs-lookup"><span data-stu-id="52cd1-129">Event Tracing</span></span>](/windows/desktop/ETW/event-tracing-portal)

[<span data-ttu-id="52cd1-130">Starta spårning</span><span class="sxs-lookup"><span data-stu-id="52cd1-130">Start-Trace</span></span>](start-trace.md)

[<span data-ttu-id="52cd1-131">Disable-PSWSManCombinedTrace</span><span class="sxs-lookup"><span data-stu-id="52cd1-131">Disable-PSWSManCombinedTrace</span></span>](Disable-PSWSManCombinedTrace.md)
