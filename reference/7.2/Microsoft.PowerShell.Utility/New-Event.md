---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-event?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Event
ms.openlocfilehash: 86a4370caccb43edf62af75337afb15f3fb63d7c
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710092"
---
# <span data-ttu-id="e149c-102">New-Event</span><span class="sxs-lookup"><span data-stu-id="e149c-102">New-Event</span></span>

## <span data-ttu-id="e149c-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="e149c-103">SYNOPSIS</span></span>
<span data-ttu-id="e149c-104">Skapar en ny händelse.</span><span class="sxs-lookup"><span data-stu-id="e149c-104">Creates a new event.</span></span>

## <span data-ttu-id="e149c-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="e149c-105">SYNTAX</span></span>

```
New-Event [-SourceIdentifier] <String> [[-Sender] <PSObject>] [[-EventArguments] <PSObject[]>]
 [[-MessageData] <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="e149c-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="e149c-106">DESCRIPTION</span></span>

<span data-ttu-id="e149c-107">`New-Event`Cmdleten skapar en ny anpassad händelse.</span><span class="sxs-lookup"><span data-stu-id="e149c-107">The `New-Event` cmdlet creates a new custom event.</span></span>

<span data-ttu-id="e149c-108">Du kan använda anpassade händelser för att meddela användare om tillstånds ändringar i programmet och eventuella ändringar som programmet kan identifiera, inklusive maskinvaru-eller system villkor, program status, disk status, nätverks status eller slut för ande av ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="e149c-108">You can use custom events to notify users about state changes in your program and any change that your program can detect, including hardware or system conditions, application status, disk status, network status, or the completion of a background job.</span></span>

<span data-ttu-id="e149c-109">Anpassade händelser läggs automatiskt till i händelse kön i sessionen när de höjs. du behöver inte prenumerera på dem.</span><span class="sxs-lookup"><span data-stu-id="e149c-109">Custom events are automatically added to the event queue in your session whenever they are raised; you do not need to subscribe to them.</span></span> <span data-ttu-id="e149c-110">Men om du vill vidarebefordra en händelse till den lokala sessionen eller ange en åtgärd för att svara på händelsen, använder du `Register-EngineEvent` cmdleten för att prenumerera på den anpassade händelsen.</span><span class="sxs-lookup"><span data-stu-id="e149c-110">However, if you want to forward an event to the local session or specify an action to respond to the event, use the `Register-EngineEvent` cmdlet to subscribe to the custom event.</span></span>

<span data-ttu-id="e149c-111">När du prenumererar på en anpassad händelse läggs händelse prenumeranten till i sessionen.</span><span class="sxs-lookup"><span data-stu-id="e149c-111">When you subscribe to a custom event, the event subscriber is added to your session.</span></span> <span data-ttu-id="e149c-112">Om du avbryter händelse prenumerationen med hjälp av `Unregister-Event` cmdleten, tas händelse prenumeranten och den anpassade händelsen bort från sessionen.</span><span class="sxs-lookup"><span data-stu-id="e149c-112">If you cancel the event subscription by using the `Unregister-Event` cmdlet, the event subscriber and custom event are deleted from the session.</span></span> <span data-ttu-id="e149c-113">Om du inte prenumererar på den anpassade händelsen måste du ändra programmets villkor eller stänga PowerShell-sessionen för att ta bort händelsen.</span><span class="sxs-lookup"><span data-stu-id="e149c-113">If you do not subscribe to the custom event, to delete the event, you must change the program conditions or close the PowerShell session.</span></span>

## <span data-ttu-id="e149c-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="e149c-114">EXAMPLES</span></span>

### <span data-ttu-id="e149c-115">Exempel 1: skapa en ny händelse i händelse kön</span><span class="sxs-lookup"><span data-stu-id="e149c-115">Example 1: Create a new event in the event queue</span></span>

```
PS C:\> New-Event -SourceIdentifier Timer -Sender windows.timer -MessageData "Test"
```

<span data-ttu-id="e149c-116">Det här kommandot skapar en ny händelse i händelse kön i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e149c-116">This command creates a new event in the PowerShell event queue.</span></span> <span data-ttu-id="e149c-117">Ett **Windows. timer** -objekt används för att skicka händelsen.</span><span class="sxs-lookup"><span data-stu-id="e149c-117">It uses a **Windows.Timer** object to send the event.</span></span>

### <span data-ttu-id="e149c-118">Exempel 2: Utlös en händelse som svar på en annan händelse</span><span class="sxs-lookup"><span data-stu-id="e149c-118">Example 2: Raise an event in response to another event</span></span>

```
PS C:\> function Enable-ProcessCreationEvent
{
   $Query = New-Object System.Management.WqlEventQuery "__InstanceCreationEvent", (New-Object TimeSpan 0,0,1), "TargetInstance isa 'Win32_Process'"
   $ProcessWatcher = New-Object System.Management.ManagementEventWatcher $Query
   $Identifier = "WMI.ProcessCreated"
   Register-ObjectEvent $ProcessWatcher "EventArrived" -SupportEvent $Identifier -Action
   {
      [void] (New-Event -SourceID "PowerShell.ProcessCreated" -Sender $Args[0] -EventArguments $Args[1].SourceEventArgs.NewEvent.TargetInstance)
   }
}
```

<span data-ttu-id="e149c-119">Den här exempel funktionen använder `New-Event` cmdleten för att utlösa en händelse som svar på en annan händelse.</span><span class="sxs-lookup"><span data-stu-id="e149c-119">This sample function uses the `New-Event` cmdlet to raise an event in response to another event.</span></span> <span data-ttu-id="e149c-120">Kommandot använder `Register-ObjectEvent` cmdleten för att prenumerera på den Windows Management Instrumentation (WMI) händelse som aktive ras när en ny process skapas.</span><span class="sxs-lookup"><span data-stu-id="e149c-120">The command uses the `Register-ObjectEvent` cmdlet to subscribe to the Windows Management Instrumentation (WMI) event that is raised when a new process is created.</span></span> <span data-ttu-id="e149c-121">Kommandot använder parametern **åtgärd** för cmdleten för att anropa `New-Event` cmdleten, vilket skapar den nya händelsen.</span><span class="sxs-lookup"><span data-stu-id="e149c-121">The command uses the **Action** parameter of the cmdlet to call the `New-Event` cmdlet, which creates the new event.</span></span>

<span data-ttu-id="e149c-122">Eftersom händelser som aktive `New-Event` ras automatiskt läggs till i PowerShell-händelseloggen behöver du inte registrera dig för den händelsen.</span><span class="sxs-lookup"><span data-stu-id="e149c-122">Because the events that `New-Event` raises are automatically added to the PowerShell event queue, you do not need to register for that event.</span></span>

## <span data-ttu-id="e149c-123">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="e149c-123">PARAMETERS</span></span>

### <span data-ttu-id="e149c-124">-EventArguments</span><span class="sxs-lookup"><span data-stu-id="e149c-124">-EventArguments</span></span>

<span data-ttu-id="e149c-125">Anger ett objekt som innehåller alternativ för händelsen.</span><span class="sxs-lookup"><span data-stu-id="e149c-125">Specifies an object that contains options for the event.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e149c-126">-MessageData</span><span class="sxs-lookup"><span data-stu-id="e149c-126">-MessageData</span></span>

<span data-ttu-id="e149c-127">Anger ytterligare data som är associerade med händelsen.</span><span class="sxs-lookup"><span data-stu-id="e149c-127">Specifies additional data associated with the event.</span></span> <span data-ttu-id="e149c-128">Värdet för den här parametern visas i egenskapen **MessageData** för objektet event.</span><span class="sxs-lookup"><span data-stu-id="e149c-128">The value of this parameter appears in the **MessageData** property of the event object.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: 3
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e149c-129">-Sender</span><span class="sxs-lookup"><span data-stu-id="e149c-129">-Sender</span></span>

<span data-ttu-id="e149c-130">Anger det objekt som aktiverar händelsen.</span><span class="sxs-lookup"><span data-stu-id="e149c-130">Specifies the object that raises the event.</span></span> <span data-ttu-id="e149c-131">Standardvärdet är PowerShell-motorn.</span><span class="sxs-lookup"><span data-stu-id="e149c-131">The default is the PowerShell engine.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e149c-132">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="e149c-132">-SourceIdentifier</span></span>

<span data-ttu-id="e149c-133">Anger ett namn för den nya händelsen.</span><span class="sxs-lookup"><span data-stu-id="e149c-133">Specifies a name for the new event.</span></span> <span data-ttu-id="e149c-134">Den här parametern är obligatorisk och måste vara unik i sessionen.</span><span class="sxs-lookup"><span data-stu-id="e149c-134">This parameter is required, and it must be unique in the session.</span></span>

<span data-ttu-id="e149c-135">Värdet för den här parametern visas i händelsens **SourceIdentifier** -egenskap.</span><span class="sxs-lookup"><span data-stu-id="e149c-135">The value of this parameter appears in the **SourceIdentifier** property of the events.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="e149c-136">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="e149c-136">CommonParameters</span></span>

<span data-ttu-id="e149c-137">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="e149c-137">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="e149c-138">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e149c-138">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="e149c-139">INDATA</span><span class="sxs-lookup"><span data-stu-id="e149c-139">INPUTS</span></span>

### <span data-ttu-id="e149c-140">Inga</span><span class="sxs-lookup"><span data-stu-id="e149c-140">None</span></span>

<span data-ttu-id="e149c-141">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e149c-141">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="e149c-142">UTDATA</span><span class="sxs-lookup"><span data-stu-id="e149c-142">OUTPUTS</span></span>

### <span data-ttu-id="e149c-143">System. Management. Automation. PSEventArgs</span><span class="sxs-lookup"><span data-stu-id="e149c-143">System.Management.Automation.PSEventArgs</span></span>

## <span data-ttu-id="e149c-144">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="e149c-144">NOTES</span></span>

<span data-ttu-id="e149c-145">Inga händelse källor är tillgängliga på Linux-eller macOS-plattformarna.</span><span class="sxs-lookup"><span data-stu-id="e149c-145">No event sources available on the Linux or macOS platforms.</span></span>

<span data-ttu-id="e149c-146">Den nya anpassade händelsen, händelse prenumerationen och händelse kön finns bara i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="e149c-146">The new custom event, the event subscription, and the event queue exist only in the current session.</span></span>
<span data-ttu-id="e149c-147">Om du stänger den aktuella sessionen ignoreras händelse kön och händelse prenumerationen avbryts.</span><span class="sxs-lookup"><span data-stu-id="e149c-147">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

## <span data-ttu-id="e149c-148">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="e149c-148">RELATED LINKS</span></span>

[<span data-ttu-id="e149c-149">Hämta händelse</span><span class="sxs-lookup"><span data-stu-id="e149c-149">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="e149c-150">Registrera – EngineEvent</span><span class="sxs-lookup"><span data-stu-id="e149c-150">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="e149c-151">Registrera – ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="e149c-151">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="e149c-152">Ta bort händelse</span><span class="sxs-lookup"><span data-stu-id="e149c-152">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="e149c-153">Avregistrera-händelse</span><span class="sxs-lookup"><span data-stu-id="e149c-153">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="e149c-154">Vänta-händelse</span><span class="sxs-lookup"><span data-stu-id="e149c-154">Wait-Event</span></span>](Wait-Event.md)
