---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-event?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Event
ms.openlocfilehash: 35d5d75cad2855753504549262abd2e14af200c0
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344498"
---
# <span data-ttu-id="74f21-103">Remove-Event</span><span class="sxs-lookup"><span data-stu-id="74f21-103">Remove-Event</span></span>

## <span data-ttu-id="74f21-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="74f21-104">SYNOPSIS</span></span>
<span data-ttu-id="74f21-105">Tar bort händelser från händelse kön.</span><span class="sxs-lookup"><span data-stu-id="74f21-105">Deletes events from the event queue.</span></span>

## <span data-ttu-id="74f21-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="74f21-106">SYNTAX</span></span>

### <span data-ttu-id="74f21-107">BySource (standard)</span><span class="sxs-lookup"><span data-stu-id="74f21-107">BySource (Default)</span></span>

```
Remove-Event [-SourceIdentifier] <String> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="74f21-108">ByIdentifier</span><span class="sxs-lookup"><span data-stu-id="74f21-108">ByIdentifier</span></span>

```
Remove-Event [-EventIdentifier] <Int32> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="74f21-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="74f21-109">DESCRIPTION</span></span>

<span data-ttu-id="74f21-110">`Remove-Event`Cmdleten tar bort händelser från händelse kön i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="74f21-110">The `Remove-Event` cmdlet deletes events from the event queue in the current session.</span></span>

<span data-ttu-id="74f21-111">Den här cmdleten tar bara bort de händelser som för närvarande finns i kön.</span><span class="sxs-lookup"><span data-stu-id="74f21-111">This cmdlet deletes only the events currently in the queue.</span></span> <span data-ttu-id="74f21-112">Använd cmdleten om du vill avbryta händelse registreringar eller avbryta prenumerationer `Unregister-Event` .</span><span class="sxs-lookup"><span data-stu-id="74f21-112">To cancel event registrations or unsubscribe, use the `Unregister-Event` cmdlet.</span></span>

## <span data-ttu-id="74f21-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="74f21-113">EXAMPLES</span></span>

### <span data-ttu-id="74f21-114">Exempel 1: ta bort en händelse efter käll-ID</span><span class="sxs-lookup"><span data-stu-id="74f21-114">Example 1: Remove an event by source identifier</span></span>

```
PS C:\> Remove-Event -SourceIdentifier "ProcessStarted"
```

<span data-ttu-id="74f21-115">Det här kommandot tar bort händelser med käll-ID för processen som startades från händelse kön.</span><span class="sxs-lookup"><span data-stu-id="74f21-115">This command deletes events with a source identifier of Process Started from the event queue.</span></span>

### <span data-ttu-id="74f21-116">Exempel 2: ta bort en händelse efter händelse identifierare</span><span class="sxs-lookup"><span data-stu-id="74f21-116">Example 2: Remove an event by event identifier</span></span>

```
PS C:\> Remove-Event -EventIdentifier 30
```

<span data-ttu-id="74f21-117">Det här kommandot tar bort händelsen med händelse-ID 30 från händelse kön.</span><span class="sxs-lookup"><span data-stu-id="74f21-117">This command deletes the event with an event ID of 30 from the event queue.</span></span>

### <span data-ttu-id="74f21-118">Exempel 3: ta bort alla händelser</span><span class="sxs-lookup"><span data-stu-id="74f21-118">Example 3: Remove all events</span></span>

```
PS C:\> Get-Event | Remove-Event
```

<span data-ttu-id="74f21-119">Det här kommandot tar bort alla händelser från händelse kön.</span><span class="sxs-lookup"><span data-stu-id="74f21-119">This command deletes all events from the event queue.</span></span>

## <span data-ttu-id="74f21-120">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="74f21-120">PARAMETERS</span></span>

### <span data-ttu-id="74f21-121">-EventIdentifier</span><span class="sxs-lookup"><span data-stu-id="74f21-121">-EventIdentifier</span></span>

<span data-ttu-id="74f21-122">Anger händelse-ID: t som cmdleten tar bort.</span><span class="sxs-lookup"><span data-stu-id="74f21-122">Specifies the event identifier for which the cmdlet deletes.</span></span> <span data-ttu-id="74f21-123">En **EventIdentifier** -eller **SourceIdentifier** -parameter krävs i varje kommando.</span><span class="sxs-lookup"><span data-stu-id="74f21-123">An **EventIdentifier** or **SourceIdentifier** parameter is required in every command.</span></span>

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

### <span data-ttu-id="74f21-124">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="74f21-124">-SourceIdentifier</span></span>

<span data-ttu-id="74f21-125">Anger käll-ID: t som denna cmdlet tar bort händelser från.</span><span class="sxs-lookup"><span data-stu-id="74f21-125">Specifies the source identifier for which this cmdlet deletes events from.</span></span> <span data-ttu-id="74f21-126">Jokertecken är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="74f21-126">Wildcards are not permitted.</span></span> <span data-ttu-id="74f21-127">En **EventIdentifier** -eller **SourceIdentifier** -parameter krävs i varje kommando.</span><span class="sxs-lookup"><span data-stu-id="74f21-127">An **EventIdentifier** or **SourceIdentifier** parameter is required in every command.</span></span>

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

### <span data-ttu-id="74f21-128">-Confirm</span><span class="sxs-lookup"><span data-stu-id="74f21-128">-Confirm</span></span>

<span data-ttu-id="74f21-129">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="74f21-129">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="74f21-130">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="74f21-130">-WhatIf</span></span>

<span data-ttu-id="74f21-131">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="74f21-131">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="74f21-132">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="74f21-132">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="74f21-133">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="74f21-133">CommonParameters</span></span>

<span data-ttu-id="74f21-134">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="74f21-134">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="74f21-135">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="74f21-135">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="74f21-136">INDATA</span><span class="sxs-lookup"><span data-stu-id="74f21-136">INPUTS</span></span>

### <span data-ttu-id="74f21-137">System. Management. Automation. PSEventArgs</span><span class="sxs-lookup"><span data-stu-id="74f21-137">System.Management.Automation.PSEventArgs</span></span>

<span data-ttu-id="74f21-138">Du kan skicka vidare händelser från `Get-Event` till `Remove-Event` .</span><span class="sxs-lookup"><span data-stu-id="74f21-138">You can pipe events from `Get-Event` to `Remove-Event`.</span></span>

## <span data-ttu-id="74f21-139">UTDATA</span><span class="sxs-lookup"><span data-stu-id="74f21-139">OUTPUTS</span></span>

### <span data-ttu-id="74f21-140">Inget</span><span class="sxs-lookup"><span data-stu-id="74f21-140">None</span></span>

<span data-ttu-id="74f21-141">Cmdleten genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="74f21-141">The cmdlet does not generate any output.</span></span>

## <span data-ttu-id="74f21-142">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="74f21-142">NOTES</span></span>

<span data-ttu-id="74f21-143">Händelser, händelse prenumerationer och händelse kön finns bara i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="74f21-143">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="74f21-144">Om du stänger den aktuella sessionen ignoreras händelse kön och händelse prenumerationen avbryts.</span><span class="sxs-lookup"><span data-stu-id="74f21-144">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

## <span data-ttu-id="74f21-145">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="74f21-145">RELATED LINKS</span></span>

[<span data-ttu-id="74f21-146">Hämta händelse</span><span class="sxs-lookup"><span data-stu-id="74f21-146">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="74f21-147">Ny händelse</span><span class="sxs-lookup"><span data-stu-id="74f21-147">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="74f21-148">Registrera – EngineEvent</span><span class="sxs-lookup"><span data-stu-id="74f21-148">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="74f21-149">Registrera – ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="74f21-149">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="74f21-150">Ta bort händelse</span><span class="sxs-lookup"><span data-stu-id="74f21-150">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="74f21-151">Avregistrera-händelse</span><span class="sxs-lookup"><span data-stu-id="74f21-151">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="74f21-152">Vänta-händelse</span><span class="sxs-lookup"><span data-stu-id="74f21-152">Wait-Event</span></span>](Wait-Event.md)
