---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/unregister-event?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Unregister-Event
ms.openlocfilehash: f1f42c1e8831896feac398228e45fc0890136fff
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264806"
---
# <span data-ttu-id="3db0c-103">Unregister-Event</span><span class="sxs-lookup"><span data-stu-id="3db0c-103">Unregister-Event</span></span>

## <span data-ttu-id="3db0c-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="3db0c-104">SYNOPSIS</span></span>
<span data-ttu-id="3db0c-105">Avbryter en händelse prenumeration.</span><span class="sxs-lookup"><span data-stu-id="3db0c-105">Cancels an event subscription.</span></span>

## <span data-ttu-id="3db0c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3db0c-106">SYNTAX</span></span>

### <span data-ttu-id="3db0c-107">BySource (standard)</span><span class="sxs-lookup"><span data-stu-id="3db0c-107">BySource (Default)</span></span>

```
Unregister-Event [-SourceIdentifier] <String> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="3db0c-108">ById</span><span class="sxs-lookup"><span data-stu-id="3db0c-108">ById</span></span>

```
Unregister-Event [-SubscriptionId] <Int32> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="3db0c-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="3db0c-109">DESCRIPTION</span></span>
<span data-ttu-id="3db0c-110">Cmdleten **unregistering-Event** avbryter en händelse prenumeration som har skapats med hjälp av cmdleten register-EngineEvent, register-ObjectEvent eller Register-WmiEvent.</span><span class="sxs-lookup"><span data-stu-id="3db0c-110">The **Unregister-Event** cmdlet cancels an event subscription that was created by using the Register-EngineEvent, Register-ObjectEvent, or Register-WmiEvent cmdlet.</span></span>

<span data-ttu-id="3db0c-111">När en händelse prenumeration avbryts tas händelse prenumeranten bort från sessionen och de prenumererade händelserna läggs inte längre till i händelse kön.</span><span class="sxs-lookup"><span data-stu-id="3db0c-111">When an event subscription is canceled, the event subscriber is deleted from the session and the subscribed events are no longer added to the event queue.</span></span>
<span data-ttu-id="3db0c-112">När du avbryter en prenumeration på en händelse som skapats med hjälp av New-Event cmdleten, tas den nya händelsen också bort från sessionen.</span><span class="sxs-lookup"><span data-stu-id="3db0c-112">When you cancel a subscription to an event created by using the New-Event cmdlet, the new event is also deleted from the session.</span></span>

<span data-ttu-id="3db0c-113">**Avregistrering-händelsen** tar inte bort händelser från händelse kön.</span><span class="sxs-lookup"><span data-stu-id="3db0c-113">**Unregister-Event** does not delete events from the event queue.</span></span>
<span data-ttu-id="3db0c-114">Använd Remove-Event-cmdleten om du vill ta bort händelser.</span><span class="sxs-lookup"><span data-stu-id="3db0c-114">To delete events, use the Remove-Event cmdlet.</span></span>

## <span data-ttu-id="3db0c-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="3db0c-115">EXAMPLES</span></span>

### <span data-ttu-id="3db0c-116">Exempel 1: Avbryt en händelse prenumeration efter käll-ID</span><span class="sxs-lookup"><span data-stu-id="3db0c-116">Example 1: Cancel an event subscription by source identifier</span></span>

```
PS C:\> Unregister-Event -SourceIdentifier "ProcessStarted"
```

<span data-ttu-id="3db0c-117">Med det här kommandot avbryts händelse prenumerationen som har käll-ID: n för ProcessStarted.</span><span class="sxs-lookup"><span data-stu-id="3db0c-117">This command cancels the event subscription that has a source identifier of ProcessStarted.</span></span>

<span data-ttu-id="3db0c-118">Använd Get-Event-cmdleten för att hitta käll-ID för en händelse.</span><span class="sxs-lookup"><span data-stu-id="3db0c-118">To find the source identifier of an event, use the Get-Event cmdlet.</span></span>
<span data-ttu-id="3db0c-119">Använd cmdleten **Get-EventSubscriber** för att hitta käll-ID för en händelse prenumeration.</span><span class="sxs-lookup"><span data-stu-id="3db0c-119">To find the source identifier of an event subscription, use the **Get-EventSubscriber** cmdlet.</span></span>

### <span data-ttu-id="3db0c-120">Exempel 2: Avbryt en händelse prenumeration efter prenumerations-ID</span><span class="sxs-lookup"><span data-stu-id="3db0c-120">Example 2: Cancel an event subscription by subscription identifier</span></span>

```
PS C:\> Unregister-Event -SubscriptionId 2
```

<span data-ttu-id="3db0c-121">Med det här kommandot avbryts händelse prenumerationen som har ett prenumerations-ID på 2.</span><span class="sxs-lookup"><span data-stu-id="3db0c-121">This command cancels the event subscription that has a subscription identifier of 2.</span></span>

<span data-ttu-id="3db0c-122">Använd cmdleten **Get-EventSubscriber** för att hitta prenumerations-ID för en händelse prenumeration.</span><span class="sxs-lookup"><span data-stu-id="3db0c-122">To find the subscription identifier of an event subscription, use the **Get-EventSubscriber** cmdlet.</span></span>

### <span data-ttu-id="3db0c-123">Exempel 3: Avbryt alla händelse prenumerationer</span><span class="sxs-lookup"><span data-stu-id="3db0c-123">Example 3: Cancel all event subscriptions</span></span>

```
PS C:\> Get-EventSubscriber -Force | Unregister-Event -Force
```

<span data-ttu-id="3db0c-124">Detta kommando avbryter alla händelse prenumerationer i sessionen.</span><span class="sxs-lookup"><span data-stu-id="3db0c-124">This command cancels all event subscriptions in the session.</span></span>

<span data-ttu-id="3db0c-125">Kommandot använder cmdleten **Get-EventSubscriber** för att hämta alla händelse prenumeranter i sessionen, inklusive de prenumeranter som är dolda med parametern *SupportEvent* för cmdletarna för händelse registrering.</span><span class="sxs-lookup"><span data-stu-id="3db0c-125">The command uses the **Get-EventSubscriber** cmdlet to get all event subscriber objects in the session, including the subscribers that are hidden by using the *SupportEvent* parameter of the event registration cmdlets.</span></span>

<span data-ttu-id="3db0c-126">Den använder en pipeline-operator (|) för att skicka prenumerantens objekt för att **avregistrera-händelse** , som tar bort dem från sessionen.</span><span class="sxs-lookup"><span data-stu-id="3db0c-126">It uses a pipeline operator (|) to send the subscriber objects to **Unregister-Event** , which deletes them from the session.</span></span>
<span data-ttu-id="3db0c-127">För att slutföra uppgiften krävs även *Force* -parametern vid **avregistrering – händelse**.</span><span class="sxs-lookup"><span data-stu-id="3db0c-127">To complete the task, the *Force* parameter is also required on **Unregister-Event**.</span></span>

## <span data-ttu-id="3db0c-128">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="3db0c-128">PARAMETERS</span></span>

### <span data-ttu-id="3db0c-129">-Force</span><span class="sxs-lookup"><span data-stu-id="3db0c-129">-Force</span></span>
<span data-ttu-id="3db0c-130">Avbryter alla händelse prenumerationer, inklusive prenumerationer som har dolts med hjälp av parametern *SupportEvent* i **register-ObjectEvent** , **register-WmiEvent** och **register-EngineEvent**.</span><span class="sxs-lookup"><span data-stu-id="3db0c-130">Cancels all event subscriptions, including subscriptions that were hidden by using the *SupportEvent* parameter of **Register-ObjectEvent** , **Register-WmiEvent** , and **Register-EngineEvent**.</span></span>

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

### <span data-ttu-id="3db0c-131">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="3db0c-131">-SourceIdentifier</span></span>
<span data-ttu-id="3db0c-132">Anger ett käll-ID som den här cmdleten avbryter händelse prenumerationer.</span><span class="sxs-lookup"><span data-stu-id="3db0c-132">Specifies a source identifier that this cmdlet cancels event subscriptions.</span></span>

<span data-ttu-id="3db0c-133">En *SourceIdentifier* -eller *SubscriptionId* -parameter måste inkluderas i varje kommando.</span><span class="sxs-lookup"><span data-stu-id="3db0c-133">A *SourceIdentifier* or *SubscriptionId* parameter must be included in every command.</span></span>

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

### <span data-ttu-id="3db0c-134">-SubscriptionId</span><span class="sxs-lookup"><span data-stu-id="3db0c-134">-SubscriptionId</span></span>
<span data-ttu-id="3db0c-135">Anger ett ID för käll-ID som den här cmdleten avbryter händelse prenumerationer.</span><span class="sxs-lookup"><span data-stu-id="3db0c-135">Specifies a source identifier ID that this cmdlet cancels event subscriptions.</span></span>

<span data-ttu-id="3db0c-136">En *SourceIdentifier* -eller *SubscriptionId* -parameter måste inkluderas i varje kommando.</span><span class="sxs-lookup"><span data-stu-id="3db0c-136">A *SourceIdentifier* or *SubscriptionId* parameter must be included in every command.</span></span>

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

### <span data-ttu-id="3db0c-137">-Confirm</span><span class="sxs-lookup"><span data-stu-id="3db0c-137">-Confirm</span></span>
<span data-ttu-id="3db0c-138">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="3db0c-138">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="3db0c-139">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="3db0c-139">-WhatIf</span></span>
<span data-ttu-id="3db0c-140">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="3db0c-140">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="3db0c-141">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="3db0c-141">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="3db0c-142">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3db0c-142">CommonParameters</span></span>
<span data-ttu-id="3db0c-143">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3db0c-143">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3db0c-144">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="3db0c-144">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3db0c-145">INDATA</span><span class="sxs-lookup"><span data-stu-id="3db0c-145">INPUTS</span></span>

### <span data-ttu-id="3db0c-146">System. Management. Automation. PSEventSubscriber</span><span class="sxs-lookup"><span data-stu-id="3db0c-146">System.Management.Automation.PSEventSubscriber</span></span>
<span data-ttu-id="3db0c-147">Du kan skicka vidare utdata från Get-EventSubscriber till **avregistrera-händelse**.</span><span class="sxs-lookup"><span data-stu-id="3db0c-147">You can pipe the output from Get-EventSubscriber to **Unregister-Event**.</span></span>

## <span data-ttu-id="3db0c-148">UTDATA</span><span class="sxs-lookup"><span data-stu-id="3db0c-148">OUTPUTS</span></span>

### <span data-ttu-id="3db0c-149">Inget</span><span class="sxs-lookup"><span data-stu-id="3db0c-149">None</span></span>
<span data-ttu-id="3db0c-150">Denna cmdlet returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="3db0c-150">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="3db0c-151">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="3db0c-151">NOTES</span></span>

* <span data-ttu-id="3db0c-152">Händelser, händelse prenumerationer och händelse kön finns bara i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="3db0c-152">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="3db0c-153">Om du stänger den aktuella sessionen ignoreras händelse kön och händelse prenumerationen avbryts.</span><span class="sxs-lookup"><span data-stu-id="3db0c-153">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

  <span data-ttu-id="3db0c-154">**Avregistrering-händelsen** kan inte ta bort händelser som skapats med hjälp av New-Event cmdlet om du inte har prenumererat på händelsen med hjälp av cmdleten **register-EngineEvent** .</span><span class="sxs-lookup"><span data-stu-id="3db0c-154">**Unregister-Event** cannot delete events created by using the New-Event cmdlet unless you have subscribed to the event by using the **Register-EngineEvent** cmdlet.</span></span>
<span data-ttu-id="3db0c-155">Om du vill ta bort en anpassad händelse från sessionen måste du ta bort den program mässigt eller stänga sessionen.</span><span class="sxs-lookup"><span data-stu-id="3db0c-155">To delete a custom event from the session, you must remove it programmatically or close the session.</span></span>

*

## <span data-ttu-id="3db0c-156">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="3db0c-156">RELATED LINKS</span></span>

[<span data-ttu-id="3db0c-157">Hämta händelse</span><span class="sxs-lookup"><span data-stu-id="3db0c-157">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="3db0c-158">Get-EventSubscriber</span><span class="sxs-lookup"><span data-stu-id="3db0c-158">Get-EventSubscriber</span></span>](Get-EventSubscriber.md)

[<span data-ttu-id="3db0c-159">Ny händelse</span><span class="sxs-lookup"><span data-stu-id="3db0c-159">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="3db0c-160">Registrera – EngineEvent</span><span class="sxs-lookup"><span data-stu-id="3db0c-160">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="3db0c-161">Registrera – ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="3db0c-161">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="3db0c-162">Ta bort händelse</span><span class="sxs-lookup"><span data-stu-id="3db0c-162">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="3db0c-163">Avregistrera-händelse</span><span class="sxs-lookup"><span data-stu-id="3db0c-163">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="3db0c-164">Vänta-händelse</span><span class="sxs-lookup"><span data-stu-id="3db0c-164">Wait-Event</span></span>](Wait-Event.md)
