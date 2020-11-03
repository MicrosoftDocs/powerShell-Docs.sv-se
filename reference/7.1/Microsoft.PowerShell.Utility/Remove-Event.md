---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-event?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Event
ms.openlocfilehash: 2ef1125320141d0a16a2a0120560efbe65017b4a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264284"
---
# <span data-ttu-id="199fe-103">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="199fe-103">Remove-Event</span></span>

## <span data-ttu-id="199fe-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="199fe-104">SYNOPSIS</span></span>
<span data-ttu-id="199fe-105">Tar bort händelser från händelse kön.</span><span class="sxs-lookup"><span data-stu-id="199fe-105">Deletes events from the event queue.</span></span>

## <span data-ttu-id="199fe-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="199fe-106">SYNTAX</span></span>

### <span data-ttu-id="199fe-107">BySource (standard)</span><span class="sxs-lookup"><span data-stu-id="199fe-107">BySource (Default)</span></span>

```
Remove-Event [-SourceIdentifier] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="199fe-108">ByIdentifier</span><span class="sxs-lookup"><span data-stu-id="199fe-108">ByIdentifier</span></span>

```
Remove-Event [-EventIdentifier] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="199fe-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="199fe-109">DESCRIPTION</span></span>
<span data-ttu-id="199fe-110">Cmdleten **Remove-Event** tar bort händelser från händelse kön i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="199fe-110">The **Remove-Event** cmdlet deletes events from the event queue in the current session.</span></span>

<span data-ttu-id="199fe-111">Den här cmdleten tar bara bort de händelser som för närvarande finns i kön.</span><span class="sxs-lookup"><span data-stu-id="199fe-111">This cmdlet deletes only the events currently in the queue.</span></span>
<span data-ttu-id="199fe-112">Om du vill avbryta händelse registreringar eller avbryta prenumerationen använder du cmdleten Unregister-Event.</span><span class="sxs-lookup"><span data-stu-id="199fe-112">To cancel event registrations or unsubscribe, use the Unregister-Event cmdlet.</span></span>

## <span data-ttu-id="199fe-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="199fe-113">EXAMPLES</span></span>

### <span data-ttu-id="199fe-114">Exempel 1: ta bort en händelse efter käll-ID</span><span class="sxs-lookup"><span data-stu-id="199fe-114">Example 1: Remove an event by source identifier</span></span>

```
PS C:\> Remove-Event -SourceIdentifier "ProcessStarted"
```

<span data-ttu-id="199fe-115">Det här kommandot tar bort händelser med käll-ID för processen som startades från händelse kön.</span><span class="sxs-lookup"><span data-stu-id="199fe-115">This command deletes events with a source identifier of Process Started from the event queue.</span></span>

### <span data-ttu-id="199fe-116">Exempel 2: ta bort en händelse efter händelse identifierare</span><span class="sxs-lookup"><span data-stu-id="199fe-116">Example 2: Remove an event by event identifier</span></span>

```
PS C:\> Remove-Event -EventIdentifier 30
```

<span data-ttu-id="199fe-117">Det här kommandot tar bort händelsen med händelse-ID 30 från händelse kön.</span><span class="sxs-lookup"><span data-stu-id="199fe-117">This command deletes the event with an event ID of 30 from the event queue.</span></span>

### <span data-ttu-id="199fe-118">Exempel 3: ta bort alla händelser</span><span class="sxs-lookup"><span data-stu-id="199fe-118">Example 3: Remove all events</span></span>

```
PS C:\> Get-Event | Remove-Event
```

<span data-ttu-id="199fe-119">Det här kommandot tar bort alla händelser från händelse kön.</span><span class="sxs-lookup"><span data-stu-id="199fe-119">This command deletes all events from the event queue.</span></span>

## <span data-ttu-id="199fe-120">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="199fe-120">PARAMETERS</span></span>

### <span data-ttu-id="199fe-121">-EventIdentifier</span><span class="sxs-lookup"><span data-stu-id="199fe-121">-EventIdentifier</span></span>
<span data-ttu-id="199fe-122">Anger händelse-ID: t som cmdleten tar bort.</span><span class="sxs-lookup"><span data-stu-id="199fe-122">Specifies the event identifier for which the cmdlet deletes.</span></span>
<span data-ttu-id="199fe-123">En *EventIdentifier* -eller *SourceIdentifier* -parameter krävs i varje kommando.</span><span class="sxs-lookup"><span data-stu-id="199fe-123">An *EventIdentifier* or *SourceIdentifier* parameter is required in every command.</span></span>

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

### <span data-ttu-id="199fe-124">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="199fe-124">-SourceIdentifier</span></span>
<span data-ttu-id="199fe-125">Anger käll-ID: t som denna cmdlet tar bort händelser från.</span><span class="sxs-lookup"><span data-stu-id="199fe-125">Specifies the source identifier for which this cmdlet deletes events from.</span></span>
<span data-ttu-id="199fe-126">Jokertecken är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="199fe-126">Wildcards are not permitted.</span></span>
<span data-ttu-id="199fe-127">En *EventIdentifier* -eller *SourceIdentifier* -parameter krävs i varje kommando.</span><span class="sxs-lookup"><span data-stu-id="199fe-127">An *EventIdentifier* or *SourceIdentifier* parameter is required in every command.</span></span>

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

### <span data-ttu-id="199fe-128">-Confirm</span><span class="sxs-lookup"><span data-stu-id="199fe-128">-Confirm</span></span>
<span data-ttu-id="199fe-129">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="199fe-129">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="199fe-130">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="199fe-130">-WhatIf</span></span>
<span data-ttu-id="199fe-131">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="199fe-131">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="199fe-132">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="199fe-132">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="199fe-133">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="199fe-133">CommonParameters</span></span>
<span data-ttu-id="199fe-134">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="199fe-134">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="199fe-135">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="199fe-135">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="199fe-136">INDATA</span><span class="sxs-lookup"><span data-stu-id="199fe-136">INPUTS</span></span>

### <span data-ttu-id="199fe-137">System. Management. Automation. PSEventArgs</span><span class="sxs-lookup"><span data-stu-id="199fe-137">System.Management.Automation.PSEventArgs</span></span>
<span data-ttu-id="199fe-138">Du kan skicka vidare händelser från Get-Event för att **ta bort** händelser.</span><span class="sxs-lookup"><span data-stu-id="199fe-138">You can pipe events from Get-Event to **Remove-Event**.</span></span>

## <span data-ttu-id="199fe-139">UTDATA</span><span class="sxs-lookup"><span data-stu-id="199fe-139">OUTPUTS</span></span>

### <span data-ttu-id="199fe-140">Inget</span><span class="sxs-lookup"><span data-stu-id="199fe-140">None</span></span>
<span data-ttu-id="199fe-141">Cmdleten genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="199fe-141">The cmdlet does not generate any output.</span></span>

## <span data-ttu-id="199fe-142">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="199fe-142">NOTES</span></span>

* <span data-ttu-id="199fe-143">Händelser, händelse prenumerationer och händelse kön finns bara i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="199fe-143">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="199fe-144">Om du stänger den aktuella sessionen ignoreras händelse kön och händelse prenumerationen avbryts.</span><span class="sxs-lookup"><span data-stu-id="199fe-144">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

*

## <span data-ttu-id="199fe-145">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="199fe-145">RELATED LINKS</span></span>

[<span data-ttu-id="199fe-146">Hämta händelse</span><span class="sxs-lookup"><span data-stu-id="199fe-146">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="199fe-147">Ny händelse</span><span class="sxs-lookup"><span data-stu-id="199fe-147">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="199fe-148">Registrera – EngineEvent</span><span class="sxs-lookup"><span data-stu-id="199fe-148">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="199fe-149">Registrera – ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="199fe-149">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="199fe-150">Ta bort händelse</span><span class="sxs-lookup"><span data-stu-id="199fe-150">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="199fe-151">Avregistrera-händelse</span><span class="sxs-lookup"><span data-stu-id="199fe-151">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="199fe-152">Vänta-händelse</span><span class="sxs-lookup"><span data-stu-id="199fe-152">Wait-Event</span></span>](Wait-Event.md)
