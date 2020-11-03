---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-event?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-Event
ms.openlocfilehash: df78675e6593fcc7378f151002c1861a68c081b4
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93261903"
---
# <span data-ttu-id="fb4be-103">New-Event</span><span class="sxs-lookup"><span data-stu-id="fb4be-103">New-Event</span></span>

## <span data-ttu-id="fb4be-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="fb4be-104">SYNOPSIS</span></span>
<span data-ttu-id="fb4be-105">Skapar en ny händelse.</span><span class="sxs-lookup"><span data-stu-id="fb4be-105">Creates a new event.</span></span>

## <span data-ttu-id="fb4be-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="fb4be-106">SYNTAX</span></span>

```
New-Event [-SourceIdentifier] <String> [[-Sender] <PSObject>] [[-EventArguments] <PSObject[]>]
 [[-MessageData] <PSObject>] [<CommonParameters>]
```

## <span data-ttu-id="fb4be-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="fb4be-107">DESCRIPTION</span></span>

<span data-ttu-id="fb4be-108">Cmdleten **New-Event** skapar en ny anpassad händelse.</span><span class="sxs-lookup"><span data-stu-id="fb4be-108">The **New-Event** cmdlet creates a new custom event.</span></span>

<span data-ttu-id="fb4be-109">Du kan använda anpassade händelser för att meddela användare om tillstånds ändringar i programmet och eventuella ändringar som programmet kan identifiera, inklusive maskinvaru-eller system villkor, program status, disk status, nätverks status eller slut för ande av ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="fb4be-109">You can use custom events to notify users about state changes in your program and any change that your program can detect, including hardware or system conditions, application status, disk status, network status, or the completion of a background job.</span></span>

<span data-ttu-id="fb4be-110">Anpassade händelser läggs automatiskt till i händelse kön i sessionen när de höjs. du behöver inte prenumerera på dem.</span><span class="sxs-lookup"><span data-stu-id="fb4be-110">Custom events are automatically added to the event queue in your session whenever they are raised; you do not need to subscribe to them.</span></span>
<span data-ttu-id="fb4be-111">Men om du vill vidarebefordra en händelse till den lokala sessionen eller ange en åtgärd för att svara på händelsen, använder du Register-EngineEvent cmdlet för att prenumerera på den anpassade händelsen.</span><span class="sxs-lookup"><span data-stu-id="fb4be-111">However, if you want to forward an event to the local session or specify an action to respond to the event, use the Register-EngineEvent cmdlet to subscribe to the custom event.</span></span>

<span data-ttu-id="fb4be-112">När du prenumererar på en anpassad händelse läggs händelse prenumeranten till i sessionen.</span><span class="sxs-lookup"><span data-stu-id="fb4be-112">When you subscribe to a custom event, the event subscriber is added to your session.</span></span>
<span data-ttu-id="fb4be-113">Om du avbryter händelse prenumerationen med hjälp av Unregister-Event cmdleten, tas händelse prenumeranten och den anpassade händelsen bort från sessionen.</span><span class="sxs-lookup"><span data-stu-id="fb4be-113">If you cancel the event subscription by using the Unregister-Event cmdlet, the event subscriber and custom event are deleted from the session.</span></span>
<span data-ttu-id="fb4be-114">Om du inte prenumererar på den anpassade händelsen måste du ändra programmets villkor eller stänga PowerShell-sessionen för att ta bort händelsen.</span><span class="sxs-lookup"><span data-stu-id="fb4be-114">If you do not subscribe to the custom event, to delete the event, you must change the program conditions or close the PowerShell session.</span></span>

## <span data-ttu-id="fb4be-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="fb4be-115">EXAMPLES</span></span>

### <span data-ttu-id="fb4be-116">Exempel 1: skapa en ny händelse i händelse kön</span><span class="sxs-lookup"><span data-stu-id="fb4be-116">Example 1: Create a new event in the event queue</span></span>

```
PS C:\> New-Event -SourceIdentifier Timer -Sender windows.timer -MessageData "Test"
```

<span data-ttu-id="fb4be-117">Det här kommandot skapar en ny händelse i händelse kön i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fb4be-117">This command creates a new event in the PowerShell event queue.</span></span>
<span data-ttu-id="fb4be-118">Ett **Windows. timer** -objekt används för att skicka händelsen.</span><span class="sxs-lookup"><span data-stu-id="fb4be-118">It uses a **Windows.Timer** object to send the event.</span></span>

### <span data-ttu-id="fb4be-119">Exempel 2: Utlös en händelse som svar på en annan händelse</span><span class="sxs-lookup"><span data-stu-id="fb4be-119">Example 2: Raise an event in response to another event</span></span>

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

<span data-ttu-id="fb4be-120">Den här exempel funktionen använder cmdleten **New-Event** för att utlösa en händelse som svar på en annan händelse.</span><span class="sxs-lookup"><span data-stu-id="fb4be-120">This sample function uses the **New-Event** cmdlet to raise an event in response to another event.</span></span>
<span data-ttu-id="fb4be-121">Kommandot använder Register-ObjectEvent-cmdlet för att prenumerera på händelsen Windows Management Instrumentation (WMI) som aktive ras när en ny process skapas.</span><span class="sxs-lookup"><span data-stu-id="fb4be-121">The command uses the Register-ObjectEvent cmdlet to subscribe to the Windows Management Instrumentation (WMI) event that is raised when a new process is created.</span></span>
<span data-ttu-id="fb4be-122">Kommandot använder parametern *åtgärd* för cmdleten för att anropa cmdleten **New-Event** , som skapar den nya händelsen.</span><span class="sxs-lookup"><span data-stu-id="fb4be-122">The command uses the *Action* parameter of the cmdlet to call the **New-Event** cmdlet, which creates the new event.</span></span>

<span data-ttu-id="fb4be-123">Eftersom händelserna som **nya** händelser aktive ras automatiskt läggs till i PowerShell-händelseloggen behöver du inte registrera dig för den händelsen.</span><span class="sxs-lookup"><span data-stu-id="fb4be-123">Because the events that **New-Event** raises are automatically added to the PowerShell event queue, you do not need to register for that event.</span></span>

## <span data-ttu-id="fb4be-124">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="fb4be-124">PARAMETERS</span></span>

### <span data-ttu-id="fb4be-125">-EventArguments</span><span class="sxs-lookup"><span data-stu-id="fb4be-125">-EventArguments</span></span>

<span data-ttu-id="fb4be-126">Anger ett objekt som innehåller alternativ för händelsen.</span><span class="sxs-lookup"><span data-stu-id="fb4be-126">Specifies an object that contains options for the event.</span></span>

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

### <span data-ttu-id="fb4be-127">-MessageData</span><span class="sxs-lookup"><span data-stu-id="fb4be-127">-MessageData</span></span>

<span data-ttu-id="fb4be-128">Anger ytterligare data som är associerade med händelsen.</span><span class="sxs-lookup"><span data-stu-id="fb4be-128">Specifies additional data associated with the event.</span></span>
<span data-ttu-id="fb4be-129">Värdet för den här parametern visas i egenskapen **MessageData** för objektet event.</span><span class="sxs-lookup"><span data-stu-id="fb4be-129">The value of this parameter appears in the **MessageData** property of the event object.</span></span>

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

### <span data-ttu-id="fb4be-130">-Sender</span><span class="sxs-lookup"><span data-stu-id="fb4be-130">-Sender</span></span>

<span data-ttu-id="fb4be-131">Anger det objekt som aktiverar händelsen.</span><span class="sxs-lookup"><span data-stu-id="fb4be-131">Specifies the object that raises the event.</span></span>
<span data-ttu-id="fb4be-132">Standardvärdet är PowerShell-motorn.</span><span class="sxs-lookup"><span data-stu-id="fb4be-132">The default is the PowerShell engine.</span></span>

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

### <span data-ttu-id="fb4be-133">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="fb4be-133">-SourceIdentifier</span></span>

<span data-ttu-id="fb4be-134">Anger ett namn för den nya händelsen.</span><span class="sxs-lookup"><span data-stu-id="fb4be-134">Specifies a name for the new event.</span></span>
<span data-ttu-id="fb4be-135">Den här parametern är obligatorisk och måste vara unik i sessionen.</span><span class="sxs-lookup"><span data-stu-id="fb4be-135">This parameter is required, and it must be unique in the session.</span></span>

<span data-ttu-id="fb4be-136">Värdet för den här parametern visas i händelsens **SourceIdentifier** -egenskap.</span><span class="sxs-lookup"><span data-stu-id="fb4be-136">The value of this parameter appears in the **SourceIdentifier** property of the events.</span></span>

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

### <span data-ttu-id="fb4be-137">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="fb4be-137">CommonParameters</span></span>

<span data-ttu-id="fb4be-138">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="fb4be-138">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="fb4be-139">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="fb4be-139">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="fb4be-140">INDATA</span><span class="sxs-lookup"><span data-stu-id="fb4be-140">INPUTS</span></span>

### <span data-ttu-id="fb4be-141">Inget</span><span class="sxs-lookup"><span data-stu-id="fb4be-141">None</span></span>

<span data-ttu-id="fb4be-142">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fb4be-142">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="fb4be-143">UTDATA</span><span class="sxs-lookup"><span data-stu-id="fb4be-143">OUTPUTS</span></span>

### <span data-ttu-id="fb4be-144">System. Management. Automation. PSEventArgs</span><span class="sxs-lookup"><span data-stu-id="fb4be-144">System.Management.Automation.PSEventArgs</span></span>

## <span data-ttu-id="fb4be-145">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="fb4be-145">NOTES</span></span>

<span data-ttu-id="fb4be-146">Den nya anpassade händelsen, händelse prenumerationen och händelse kön finns bara i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="fb4be-146">The new custom event, the event subscription, and the event queue exist only in the current session.</span></span> <span data-ttu-id="fb4be-147">Om du stänger den aktuella sessionen ignoreras händelse kön och händelse prenumerationen avbryts.</span><span class="sxs-lookup"><span data-stu-id="fb4be-147">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

## <span data-ttu-id="fb4be-148">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="fb4be-148">RELATED LINKS</span></span>

[<span data-ttu-id="fb4be-149">Hämta händelse</span><span class="sxs-lookup"><span data-stu-id="fb4be-149">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="fb4be-150">Registrera – EngineEvent</span><span class="sxs-lookup"><span data-stu-id="fb4be-150">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="fb4be-151">Registrera – ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="fb4be-151">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="fb4be-152">Ta bort händelse</span><span class="sxs-lookup"><span data-stu-id="fb4be-152">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="fb4be-153">Avregistrera-händelse</span><span class="sxs-lookup"><span data-stu-id="fb4be-153">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="fb4be-154">Vänta-händelse</span><span class="sxs-lookup"><span data-stu-id="fb4be-154">Wait-Event</span></span>](Wait-Event.md)