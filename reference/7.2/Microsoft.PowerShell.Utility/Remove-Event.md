---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-event?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Event
ms.openlocfilehash: 3193de9020f2f54795bde9d5cce1bb86c4431ef9
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708354"
---
# <span data-ttu-id="e37cf-102">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="e37cf-102">Remove-Event</span></span>

## <span data-ttu-id="e37cf-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="e37cf-103">SYNOPSIS</span></span>
<span data-ttu-id="e37cf-104">Tar bort händelser från händelse kön.</span><span class="sxs-lookup"><span data-stu-id="e37cf-104">Deletes events from the event queue.</span></span>

## <span data-ttu-id="e37cf-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e37cf-105">SYNTAX</span></span>

### <span data-ttu-id="e37cf-106">BySource (standard)</span><span class="sxs-lookup"><span data-stu-id="e37cf-106">BySource (Default)</span></span>

```
Remove-Event [-SourceIdentifier] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="e37cf-107">ByIdentifier</span><span class="sxs-lookup"><span data-stu-id="e37cf-107">ByIdentifier</span></span>

```
Remove-Event [-EventIdentifier] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="e37cf-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e37cf-108">DESCRIPTION</span></span>

<span data-ttu-id="e37cf-109">`Remove-Event`Cmdleten tar bort händelser från händelse kön i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="e37cf-109">The `Remove-Event` cmdlet deletes events from the event queue in the current session.</span></span>

<span data-ttu-id="e37cf-110">Den här cmdleten tar bara bort de händelser som för närvarande finns i kön.</span><span class="sxs-lookup"><span data-stu-id="e37cf-110">This cmdlet deletes only the events currently in the queue.</span></span> <span data-ttu-id="e37cf-111">Använd cmdleten om du vill avbryta händelse registreringar eller avbryta prenumerationer `Unregister-Event` .</span><span class="sxs-lookup"><span data-stu-id="e37cf-111">To cancel event registrations or unsubscribe, use the `Unregister-Event` cmdlet.</span></span>

## <span data-ttu-id="e37cf-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="e37cf-112">EXAMPLES</span></span>

### <span data-ttu-id="e37cf-113">Exempel 1: ta bort en händelse efter käll-ID</span><span class="sxs-lookup"><span data-stu-id="e37cf-113">Example 1: Remove an event by source identifier</span></span>

```
PS C:\> Remove-Event -SourceIdentifier "ProcessStarted"
```

<span data-ttu-id="e37cf-114">Det här kommandot tar bort händelser med käll-ID för processen som startades från händelse kön.</span><span class="sxs-lookup"><span data-stu-id="e37cf-114">This command deletes events with a source identifier of Process Started from the event queue.</span></span>

### <span data-ttu-id="e37cf-115">Exempel 2: ta bort en händelse efter händelse identifierare</span><span class="sxs-lookup"><span data-stu-id="e37cf-115">Example 2: Remove an event by event identifier</span></span>

```
PS C:\> Remove-Event -EventIdentifier 30
```

<span data-ttu-id="e37cf-116">Det här kommandot tar bort händelsen med händelse-ID 30 från händelse kön.</span><span class="sxs-lookup"><span data-stu-id="e37cf-116">This command deletes the event with an event ID of 30 from the event queue.</span></span>

### <span data-ttu-id="e37cf-117">Exempel 3: ta bort alla händelser</span><span class="sxs-lookup"><span data-stu-id="e37cf-117">Example 3: Remove all events</span></span>

```
PS C:\> Get-Event | Remove-Event
```

<span data-ttu-id="e37cf-118">Det här kommandot tar bort alla händelser från händelse kön.</span><span class="sxs-lookup"><span data-stu-id="e37cf-118">This command deletes all events from the event queue.</span></span>

## <span data-ttu-id="e37cf-119">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="e37cf-119">PARAMETERS</span></span>

### <span data-ttu-id="e37cf-120">-EventIdentifier</span><span class="sxs-lookup"><span data-stu-id="e37cf-120">-EventIdentifier</span></span>

<span data-ttu-id="e37cf-121">Anger händelse-ID: t som cmdleten tar bort.</span><span class="sxs-lookup"><span data-stu-id="e37cf-121">Specifies the event identifier for which the cmdlet deletes.</span></span> <span data-ttu-id="e37cf-122">En **EventIdentifier** -eller **SourceIdentifier** -parameter krävs i varje kommando.</span><span class="sxs-lookup"><span data-stu-id="e37cf-122">An **EventIdentifier** or **SourceIdentifier** parameter is required in every command.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ByIdentifier
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="e37cf-123">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="e37cf-123">-SourceIdentifier</span></span>

<span data-ttu-id="e37cf-124">Anger käll-ID: t som denna cmdlet tar bort händelser från.</span><span class="sxs-lookup"><span data-stu-id="e37cf-124">Specifies the source identifier for which this cmdlet deletes events from.</span></span> <span data-ttu-id="e37cf-125">Jokertecken är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="e37cf-125">Wildcards are not permitted.</span></span> <span data-ttu-id="e37cf-126">En **EventIdentifier** -eller **SourceIdentifier** -parameter krävs i varje kommando.</span><span class="sxs-lookup"><span data-stu-id="e37cf-126">An **EventIdentifier** or **SourceIdentifier** parameter is required in every command.</span></span>

```yaml
Type: System.String
Parameter Sets: BySource
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e37cf-127">-Confirm</span><span class="sxs-lookup"><span data-stu-id="e37cf-127">-Confirm</span></span>

<span data-ttu-id="e37cf-128">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="e37cf-128">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e37cf-129">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="e37cf-129">-WhatIf</span></span>

<span data-ttu-id="e37cf-130">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="e37cf-130">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="e37cf-131">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="e37cf-131">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e37cf-132">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e37cf-132">CommonParameters</span></span>

<span data-ttu-id="e37cf-133">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e37cf-133">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e37cf-134">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e37cf-134">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e37cf-135">INDATA</span><span class="sxs-lookup"><span data-stu-id="e37cf-135">INPUTS</span></span>

### <span data-ttu-id="e37cf-136">System. Management. Automation. PSEventArgs</span><span class="sxs-lookup"><span data-stu-id="e37cf-136">System.Management.Automation.PSEventArgs</span></span>

<span data-ttu-id="e37cf-137">Du kan skicka vidare händelser från `Get-Event` till `Remove-Event` .</span><span class="sxs-lookup"><span data-stu-id="e37cf-137">You can pipe events from `Get-Event` to `Remove-Event`.</span></span>

## <span data-ttu-id="e37cf-138">UTDATA</span><span class="sxs-lookup"><span data-stu-id="e37cf-138">OUTPUTS</span></span>

### <span data-ttu-id="e37cf-139">Inga</span><span class="sxs-lookup"><span data-stu-id="e37cf-139">None</span></span>

<span data-ttu-id="e37cf-140">Cmdleten genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="e37cf-140">The cmdlet does not generate any output.</span></span>

## <span data-ttu-id="e37cf-141">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="e37cf-141">NOTES</span></span>

<span data-ttu-id="e37cf-142">Inga händelse källor är tillgängliga på Linux-eller macOS-plattformarna.</span><span class="sxs-lookup"><span data-stu-id="e37cf-142">No event sources available on the Linux or macOS platforms.</span></span>

<span data-ttu-id="e37cf-143">Händelser, händelse prenumerationer och händelse kön finns bara i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="e37cf-143">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="e37cf-144">Om du stänger den aktuella sessionen ignoreras händelse kön och händelse prenumerationen avbryts.</span><span class="sxs-lookup"><span data-stu-id="e37cf-144">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

## <span data-ttu-id="e37cf-145">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="e37cf-145">RELATED LINKS</span></span>

[<span data-ttu-id="e37cf-146">Hämta händelse</span><span class="sxs-lookup"><span data-stu-id="e37cf-146">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="e37cf-147">Ny händelse</span><span class="sxs-lookup"><span data-stu-id="e37cf-147">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="e37cf-148">Registrera – EngineEvent</span><span class="sxs-lookup"><span data-stu-id="e37cf-148">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="e37cf-149">Registrera – ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="e37cf-149">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="e37cf-150">Ta bort händelse</span><span class="sxs-lookup"><span data-stu-id="e37cf-150">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="e37cf-151">Avregistrera-händelse</span><span class="sxs-lookup"><span data-stu-id="e37cf-151">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="e37cf-152">Vänta-händelse</span><span class="sxs-lookup"><span data-stu-id="e37cf-152">Wait-Event</span></span>](Wait-Event.md)
