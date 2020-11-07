---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/unregister-event?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-Event
ms.openlocfilehash: 9373cb1c5080b95317925937ccf04baa3d335bea
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94344158"
---
# <span data-ttu-id="bd48b-103">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="bd48b-103">Unregister-Event</span></span>

## <span data-ttu-id="bd48b-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="bd48b-104">SYNOPSIS</span></span>
<span data-ttu-id="bd48b-105">Avbryter en händelse prenumeration.</span><span class="sxs-lookup"><span data-stu-id="bd48b-105">Cancels an event subscription.</span></span>

## <span data-ttu-id="bd48b-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="bd48b-106">SYNTAX</span></span>

### <span data-ttu-id="bd48b-107">BySource (standard)</span><span class="sxs-lookup"><span data-stu-id="bd48b-107">BySource (Default)</span></span>

```
Unregister-Event [-SourceIdentifier] <String> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="bd48b-108">ById</span><span class="sxs-lookup"><span data-stu-id="bd48b-108">ById</span></span>

```
Unregister-Event [-SubscriptionId] <Int32> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="bd48b-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="bd48b-109">DESCRIPTION</span></span>

<span data-ttu-id="bd48b-110">`Unregister-Event`Cmdleten avbryter en händelse prenumeration som har skapats med hjälp av `Register-EngineEvent` `Register-ObjectEvent` cmdleten,, eller `Register-WmiEvent` .</span><span class="sxs-lookup"><span data-stu-id="bd48b-110">The `Unregister-Event` cmdlet cancels an event subscription that was created by using the `Register-EngineEvent`, `Register-ObjectEvent`, or `Register-WmiEvent` cmdlet.</span></span>

<span data-ttu-id="bd48b-111">När en händelse prenumeration avbryts tas händelse prenumeranten bort från sessionen och de prenumererade händelserna läggs inte längre till i händelse kön.</span><span class="sxs-lookup"><span data-stu-id="bd48b-111">When an event subscription is canceled, the event subscriber is deleted from the session and the subscribed events are no longer added to the event queue.</span></span> <span data-ttu-id="bd48b-112">När du avbryter en prenumeration på en händelse som skapats med hjälp av `New-Event` cmdleten, tas den nya händelsen också bort från sessionen.</span><span class="sxs-lookup"><span data-stu-id="bd48b-112">When you cancel a subscription to an event created by using the `New-Event` cmdlet, the new event is also deleted from the session.</span></span>

<span data-ttu-id="bd48b-113">`Unregister-Event` tar inte bort händelser från händelse kön.</span><span class="sxs-lookup"><span data-stu-id="bd48b-113">`Unregister-Event` does not delete events from the event queue.</span></span> <span data-ttu-id="bd48b-114">Använd cmdleten om du vill ta bort händelser `Remove-Event` .</span><span class="sxs-lookup"><span data-stu-id="bd48b-114">To delete events, use the `Remove-Event` cmdlet.</span></span>

## <span data-ttu-id="bd48b-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="bd48b-115">EXAMPLES</span></span>

### <span data-ttu-id="bd48b-116">Exempel 1: Avbryt en händelse prenumeration efter käll-ID</span><span class="sxs-lookup"><span data-stu-id="bd48b-116">Example 1: Cancel an event subscription by source identifier</span></span>

```
PS C:\> Unregister-Event -SourceIdentifier "ProcessStarted"
```

<span data-ttu-id="bd48b-117">Med det här kommandot avbryts händelse prenumerationen som har käll-ID: n för ProcessStarted.</span><span class="sxs-lookup"><span data-stu-id="bd48b-117">This command cancels the event subscription that has a source identifier of ProcessStarted.</span></span>

<span data-ttu-id="bd48b-118">Använd cmdleten för att hitta käll-ID för en händelse `Get-Event` .</span><span class="sxs-lookup"><span data-stu-id="bd48b-118">To find the source identifier of an event, use the `Get-Event` cmdlet.</span></span> <span data-ttu-id="bd48b-119">Använd cmdleten för att hitta käll identifieraren för en händelse prenumeration `Get-EventSubscriber` .</span><span class="sxs-lookup"><span data-stu-id="bd48b-119">To find the source identifier of an event subscription, use the `Get-EventSubscriber` cmdlet.</span></span>

### <span data-ttu-id="bd48b-120">Exempel 2: Avbryt en händelse prenumeration efter prenumerations-ID</span><span class="sxs-lookup"><span data-stu-id="bd48b-120">Example 2: Cancel an event subscription by subscription identifier</span></span>

```
PS C:\> Unregister-Event -SubscriptionId 2
```

<span data-ttu-id="bd48b-121">Med det här kommandot avbryts händelse prenumerationen som har ett prenumerations-ID på 2.</span><span class="sxs-lookup"><span data-stu-id="bd48b-121">This command cancels the event subscription that has a subscription identifier of 2.</span></span>

<span data-ttu-id="bd48b-122">Använd cmdleten för att hitta prenumerations-ID för en händelse prenumeration `Get-EventSubscriber` .</span><span class="sxs-lookup"><span data-stu-id="bd48b-122">To find the subscription identifier of an event subscription, use the `Get-EventSubscriber` cmdlet.</span></span>

### <span data-ttu-id="bd48b-123">Exempel 3: Avbryt alla händelse prenumerationer</span><span class="sxs-lookup"><span data-stu-id="bd48b-123">Example 3: Cancel all event subscriptions</span></span>

```
PS C:\> Get-EventSubscriber -Force | Unregister-Event -Force
```

<span data-ttu-id="bd48b-124">Detta kommando avbryter alla händelse prenumerationer i sessionen.</span><span class="sxs-lookup"><span data-stu-id="bd48b-124">This command cancels all event subscriptions in the session.</span></span>

<span data-ttu-id="bd48b-125">Kommandot använder `Get-EventSubscriber` cmdleten för att hämta alla Event Subscriber-objekt i sessionen, inklusive de prenumeranter som är dolda med hjälp av parametern **SupportEvent** för cmdletarna för händelse registrering.</span><span class="sxs-lookup"><span data-stu-id="bd48b-125">The command uses the `Get-EventSubscriber` cmdlet to get all event subscriber objects in the session, including the subscribers that are hidden by using the **SupportEvent** parameter of the event registration cmdlets.</span></span>

<span data-ttu-id="bd48b-126">Den använder en pipeline-operator ( `|` ) för att skicka prenumerantens objekt till `Unregister-Event` , vilket tar bort dem från sessionen.</span><span class="sxs-lookup"><span data-stu-id="bd48b-126">It uses a pipeline operator (`|`) to send the subscriber objects to `Unregister-Event`, which deletes them from the session.</span></span> <span data-ttu-id="bd48b-127">För att slutföra uppgiften krävs även **Force** -parametern på `Unregister-Event` .</span><span class="sxs-lookup"><span data-stu-id="bd48b-127">To complete the task, the **Force** parameter is also required on `Unregister-Event`.</span></span>

## <span data-ttu-id="bd48b-128">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="bd48b-128">PARAMETERS</span></span>

### <span data-ttu-id="bd48b-129">-Force</span><span class="sxs-lookup"><span data-stu-id="bd48b-129">-Force</span></span>

<span data-ttu-id="bd48b-130">Avbryter alla händelse prenumerationer, inklusive prenumerationer som har dolts med hjälp av parametern **SupportEvent** i `Register-ObjectEvent` , `Register-WmiEvent` och `Register-EngineEvent` .</span><span class="sxs-lookup"><span data-stu-id="bd48b-130">Cancels all event subscriptions, including subscriptions that were hidden by using the **SupportEvent** parameter of `Register-ObjectEvent`, `Register-WmiEvent`, and `Register-EngineEvent`.</span></span>

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

### <span data-ttu-id="bd48b-131">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="bd48b-131">-SourceIdentifier</span></span>

<span data-ttu-id="bd48b-132">Anger ett käll-ID som den här cmdleten avbryter händelse prenumerationer.</span><span class="sxs-lookup"><span data-stu-id="bd48b-132">Specifies a source identifier that this cmdlet cancels event subscriptions.</span></span>

<span data-ttu-id="bd48b-133">En **SourceIdentifier** -eller **SubscriptionId** -parameter måste inkluderas i varje kommando.</span><span class="sxs-lookup"><span data-stu-id="bd48b-133">A **SourceIdentifier** or **SubscriptionId** parameter must be included in every command.</span></span>

```yaml
Type: System.String
Parameter Sets: BySource
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bd48b-134">-SubscriptionId</span><span class="sxs-lookup"><span data-stu-id="bd48b-134">-SubscriptionId</span></span>

<span data-ttu-id="bd48b-135">Anger ett ID för käll-ID som den här cmdleten avbryter händelse prenumerationer.</span><span class="sxs-lookup"><span data-stu-id="bd48b-135">Specifies a source identifier ID that this cmdlet cancels event subscriptions.</span></span>

<span data-ttu-id="bd48b-136">En **SourceIdentifier** -eller **SubscriptionId** -parameter måste inkluderas i varje kommando.</span><span class="sxs-lookup"><span data-stu-id="bd48b-136">A **SourceIdentifier** or **SubscriptionId** parameter must be included in every command.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ById
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="bd48b-137">-Confirm</span><span class="sxs-lookup"><span data-stu-id="bd48b-137">-Confirm</span></span>

<span data-ttu-id="bd48b-138">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="bd48b-138">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="bd48b-139">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="bd48b-139">-WhatIf</span></span>

<span data-ttu-id="bd48b-140">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="bd48b-140">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="bd48b-141">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="bd48b-141">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="bd48b-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="bd48b-142">CommonParameters</span></span>

<span data-ttu-id="bd48b-143">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="bd48b-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="bd48b-144">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="bd48b-144">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="bd48b-145">INDATA</span><span class="sxs-lookup"><span data-stu-id="bd48b-145">INPUTS</span></span>

### <span data-ttu-id="bd48b-146">System. Management. Automation. PSEventSubscriber</span><span class="sxs-lookup"><span data-stu-id="bd48b-146">System.Management.Automation.PSEventSubscriber</span></span>

<span data-ttu-id="bd48b-147">Du kan skicka vidare utdata från `Get-EventSubscriber` till `Unregister-Event` .</span><span class="sxs-lookup"><span data-stu-id="bd48b-147">You can pipe the output from `Get-EventSubscriber` to `Unregister-Event`.</span></span>

## <span data-ttu-id="bd48b-148">UTDATA</span><span class="sxs-lookup"><span data-stu-id="bd48b-148">OUTPUTS</span></span>

### <span data-ttu-id="bd48b-149">Inget</span><span class="sxs-lookup"><span data-stu-id="bd48b-149">None</span></span>

<span data-ttu-id="bd48b-150">Denna cmdlet returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="bd48b-150">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="bd48b-151">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="bd48b-151">NOTES</span></span>

<span data-ttu-id="bd48b-152">Inga händelse källor är tillgängliga på Linux-eller macOS-plattformarna.</span><span class="sxs-lookup"><span data-stu-id="bd48b-152">No event sources available on the Linux or macOS platforms.</span></span>

<span data-ttu-id="bd48b-153">Händelser, händelse prenumerationer och händelse kön finns bara i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="bd48b-153">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="bd48b-154">Om du stänger den aktuella sessionen ignoreras händelse kön och händelse prenumerationen avbryts.</span><span class="sxs-lookup"><span data-stu-id="bd48b-154">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

<span data-ttu-id="bd48b-155">`Unregister-Event` Det går inte att ta bort händelser som skapats med `New-Event` cmdleten om du inte har prenumererat på händelsen med hjälp av `Register-EngineEvent` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="bd48b-155">`Unregister-Event` cannot delete events created by using the `New-Event` cmdlet unless you have subscribed to the event by using the `Register-EngineEvent` cmdlet.</span></span> <span data-ttu-id="bd48b-156">Om du vill ta bort en anpassad händelse från sessionen måste du ta bort den program mässigt eller stänga sessionen.</span><span class="sxs-lookup"><span data-stu-id="bd48b-156">To delete a custom event from the session, you must remove it programmatically or close the session.</span></span>

## <span data-ttu-id="bd48b-157">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="bd48b-157">RELATED LINKS</span></span>

[<span data-ttu-id="bd48b-158">Hämta händelse</span><span class="sxs-lookup"><span data-stu-id="bd48b-158">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="bd48b-159">Get-EventSubscriber</span><span class="sxs-lookup"><span data-stu-id="bd48b-159">Get-EventSubscriber</span></span>](Get-EventSubscriber.md)

[<span data-ttu-id="bd48b-160">Ny händelse</span><span class="sxs-lookup"><span data-stu-id="bd48b-160">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="bd48b-161">Registrera – EngineEvent</span><span class="sxs-lookup"><span data-stu-id="bd48b-161">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="bd48b-162">Registrera – ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="bd48b-162">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="bd48b-163">Ta bort händelse</span><span class="sxs-lookup"><span data-stu-id="bd48b-163">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="bd48b-164">Avregistrera-händelse</span><span class="sxs-lookup"><span data-stu-id="bd48b-164">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="bd48b-165">Vänta-händelse</span><span class="sxs-lookup"><span data-stu-id="bd48b-165">Wait-Event</span></span>](Wait-Event.md)
