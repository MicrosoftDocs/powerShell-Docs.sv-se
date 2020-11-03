---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/23/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/wait-event?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Event
ms.openlocfilehash: fd617cd145c4f36ceede9898de93cbad33cb4bf3
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262161"
---
# <span data-ttu-id="48371-103">Wait-Event</span><span class="sxs-lookup"><span data-stu-id="48371-103">Wait-Event</span></span>

## <span data-ttu-id="48371-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="48371-104">SYNOPSIS</span></span>
<span data-ttu-id="48371-105">Väntar tills en viss händelse utlöses innan körningen fortsätter att köras.</span><span class="sxs-lookup"><span data-stu-id="48371-105">Waits until a particular event is raised before continuing to run.</span></span>

## <span data-ttu-id="48371-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="48371-106">SYNTAX</span></span>

```
Wait-Event [[-SourceIdentifier] <String>] [-Timeout <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="48371-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="48371-107">DESCRIPTION</span></span>

<span data-ttu-id="48371-108">`Wait-Event`Cmdleten pausar körningen av ett skript eller en funktion tills en viss händelse har Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="48371-108">The `Wait-Event` cmdlet suspends execution of a script or function until a particular event is raised.</span></span> <span data-ttu-id="48371-109">Körningen återupptas när händelsen identifieras.</span><span class="sxs-lookup"><span data-stu-id="48371-109">Execution resumes when the event is detected.</span></span> <span data-ttu-id="48371-110">Tryck på <kbd>CTRL</kbd>C om du vill avbryta väntan + <kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="48371-110">To cancel the wait, press <kbd>CTRL</kbd>+<kbd>C</kbd>.</span></span>

<span data-ttu-id="48371-111">Den här funktionen är ett alternativ till att söka efter en händelse.</span><span class="sxs-lookup"><span data-stu-id="48371-111">This feature provides an alternative to polling for an event.</span></span> <span data-ttu-id="48371-112">Du kan också bestämma svar på en händelse på två olika sätt:</span><span class="sxs-lookup"><span data-stu-id="48371-112">It also allows you to determine the response to an event in two different ways:</span></span>

- <span data-ttu-id="48371-113">använda **Åtgärds** parametern för händelse prenumerationen</span><span class="sxs-lookup"><span data-stu-id="48371-113">using the **Action** parameter of the event subscription</span></span>
- <span data-ttu-id="48371-114">väntar på att en händelse ska returneras och svara sedan med en åtgärd</span><span class="sxs-lookup"><span data-stu-id="48371-114">waiting for an event to return and then respond with an action</span></span>

## <span data-ttu-id="48371-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="48371-115">EXAMPLES</span></span>

### <span data-ttu-id="48371-116">Exempel 1: vänta på nästa händelse</span><span class="sxs-lookup"><span data-stu-id="48371-116">Example 1: Wait for the next event</span></span>

<span data-ttu-id="48371-117">Det här exemplet väntar på nästa händelse som aktive ras.</span><span class="sxs-lookup"><span data-stu-id="48371-117">This example waits for the next event that is raised.</span></span>

```powershell
Wait-Event
```

### <span data-ttu-id="48371-118">Exempel 2: vänta på en händelse med en angiven käll-ID</span><span class="sxs-lookup"><span data-stu-id="48371-118">Example 2: Wait for an event with a specified source identifier</span></span>

<span data-ttu-id="48371-119">Det här exemplet väntar på nästa händelse som aktive ras och har en käll-ID för ProcessStarted.</span><span class="sxs-lookup"><span data-stu-id="48371-119">This example waits for the next event that is raised and that has a source identifier of ProcessStarted.</span></span>

```powershell
Wait-Event -SourceIdentifier "ProcessStarted"
```

### <span data-ttu-id="48371-120">Exempel 3: vänta tills en timer har gått ut</span><span class="sxs-lookup"><span data-stu-id="48371-120">Example 3: Wait for a timer elapsed event</span></span>

<span data-ttu-id="48371-121">I det här exemplet används `Wait-Event` cmdleten för att vänta på en timer-händelse på en timer som är inställd på 2000 millisekunder.</span><span class="sxs-lookup"><span data-stu-id="48371-121">This example uses the `Wait-Event` cmdlet to wait for a timer event on a timer that is set for 2000 milliseconds.</span></span>

```powershell
$Timer = New-Object Timers.Timer
$objectEventArgs = @{
    InputObject = $Timer
    EventName = 'Elapsed'
    SourceIdentifier = 'Timer.Elapsed'
}
Register-ObjectEvent @objectEventArgs
$Timer.Interval = 2000
$Timer.Autoreset = $False
$Timer.Enabled = $True
Wait-Event Timer.Elapsed
```

```Output
ComputerName     :
RunspaceId       : bb560b14-ff43-48d4-b801-5adc31bbc6fb
EventIdentifier  : 1
Sender           : System.Timers.Timer
SourceEventArgs  : System.Timers.ElapsedEventArgs
SourceArgs       : {System.Timers.Timer, System.Timers.ElapsedEventArgs}
SourceIdentifier : Timer.Elapsed
TimeGenerated    : 4/23/2020 2:30:37 PM
MessageData      :
```

### <span data-ttu-id="48371-122">Exempel 4: vänta på en händelse efter en angiven tids gräns</span><span class="sxs-lookup"><span data-stu-id="48371-122">Example 4: Wait for an event after a specified timeout</span></span>

<span data-ttu-id="48371-123">Det här exemplet väntar upp till 90 sekunder för nästa händelse som aktive ras och har en käll-ID för **ProcessStarted**.</span><span class="sxs-lookup"><span data-stu-id="48371-123">This example waits up to 90 seconds for the next event that is raised and that has a source identifier of **ProcessStarted**.</span></span> <span data-ttu-id="48371-124">Om den angivna tiden går ut avslutas vänte tiden.</span><span class="sxs-lookup"><span data-stu-id="48371-124">If the specified time expires, the wait ends.</span></span>

```powershell
Wait-Event -SourceIdentifier "ProcessStarted" -Timeout 90
```

## <span data-ttu-id="48371-125">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="48371-125">PARAMETERS</span></span>

### <span data-ttu-id="48371-126">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="48371-126">-SourceIdentifier</span></span>

<span data-ttu-id="48371-127">Anger käll-ID: t som denna cmdlet väntar på händelser.</span><span class="sxs-lookup"><span data-stu-id="48371-127">Specifies the source identifier that this cmdlet waits for events.</span></span>
<span data-ttu-id="48371-128">Som standard `Wait-Event` väntar alla händelser.</span><span class="sxs-lookup"><span data-stu-id="48371-128">By default, `Wait-Event` waits for any event.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="48371-129">-Timeout</span><span class="sxs-lookup"><span data-stu-id="48371-129">-Timeout</span></span>

<span data-ttu-id="48371-130">Anger den maximala tiden, i sekunder, som `Wait-Event` väntar på att händelsen ska inträffa.</span><span class="sxs-lookup"><span data-stu-id="48371-130">Specifies the maximum time, in seconds, that `Wait-Event` waits for the event to occur.</span></span> <span data-ttu-id="48371-131">Standardvärdet,-1, väntar på obestämd tid.</span><span class="sxs-lookup"><span data-stu-id="48371-131">The default, -1, waits indefinitely.</span></span> <span data-ttu-id="48371-132">Tids inställningen startar när du skickar `Wait-Event` kommandot.</span><span class="sxs-lookup"><span data-stu-id="48371-132">The timing starts when you submit the `Wait-Event` command.</span></span>

<span data-ttu-id="48371-133">Om den angivna tiden överskrids, avslutas vänte tiden och kommando tolken returnerar, även om händelsen inte har Aktiver ATS.</span><span class="sxs-lookup"><span data-stu-id="48371-133">If the specified time is exceeded, the wait ends and the command prompt returns, even if the event has not been raised.</span></span> <span data-ttu-id="48371-134">Inget fel meddelande visas.</span><span class="sxs-lookup"><span data-stu-id="48371-134">No error message is displayed.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: Named
Default value: -1
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="48371-135">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="48371-135">CommonParameters</span></span>

<span data-ttu-id="48371-136">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="48371-136">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="48371-137">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="48371-137">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="48371-138">INDATA</span><span class="sxs-lookup"><span data-stu-id="48371-138">INPUTS</span></span>

### <span data-ttu-id="48371-139">System. String</span><span class="sxs-lookup"><span data-stu-id="48371-139">System.String</span></span>

## <span data-ttu-id="48371-140">UTDATA</span><span class="sxs-lookup"><span data-stu-id="48371-140">OUTPUTS</span></span>

### <span data-ttu-id="48371-141">System. Management. Automation. PSEventArgs</span><span class="sxs-lookup"><span data-stu-id="48371-141">System.Management.Automation.PSEventArgs</span></span>

## <span data-ttu-id="48371-142">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="48371-142">NOTES</span></span>

<span data-ttu-id="48371-143">Händelser, händelse prenumerationer och händelse kön finns bara i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="48371-143">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="48371-144">Om du stänger den aktuella sessionen ignoreras händelse kön och händelse prenumerationen avbryts.</span><span class="sxs-lookup"><span data-stu-id="48371-144">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

## <span data-ttu-id="48371-145">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="48371-145">RELATED LINKS</span></span>

[<span data-ttu-id="48371-146">Hämta händelse</span><span class="sxs-lookup"><span data-stu-id="48371-146">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="48371-147">Get-EventSubscriber</span><span class="sxs-lookup"><span data-stu-id="48371-147">Get-EventSubscriber</span></span>](Get-EventSubscriber.md)

[<span data-ttu-id="48371-148">Ny händelse</span><span class="sxs-lookup"><span data-stu-id="48371-148">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="48371-149">Registrera – EngineEvent</span><span class="sxs-lookup"><span data-stu-id="48371-149">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="48371-150">Registrera – ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="48371-150">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="48371-151">Ta bort händelse</span><span class="sxs-lookup"><span data-stu-id="48371-151">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="48371-152">Avregistrera-händelse</span><span class="sxs-lookup"><span data-stu-id="48371-152">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="48371-153">Vänta-händelse</span><span class="sxs-lookup"><span data-stu-id="48371-153">Wait-Event</span></span>](Wait-Event.md)
