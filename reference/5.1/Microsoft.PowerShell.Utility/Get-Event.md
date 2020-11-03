---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-event?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Event
ms.openlocfilehash: f9f4edca0fce4633daeac9ac11a3ccfb09feb98a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265059"
---
# <span data-ttu-id="30b0d-103">Get-Event</span><span class="sxs-lookup"><span data-stu-id="30b0d-103">Get-Event</span></span>

## <span data-ttu-id="30b0d-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="30b0d-104">SYNOPSIS</span></span>
<span data-ttu-id="30b0d-105">Hämtar händelserna i händelse kön.</span><span class="sxs-lookup"><span data-stu-id="30b0d-105">Gets the events in the event queue.</span></span>

## <span data-ttu-id="30b0d-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="30b0d-106">SYNTAX</span></span>

### <span data-ttu-id="30b0d-107">BySource (standard)</span><span class="sxs-lookup"><span data-stu-id="30b0d-107">BySource (Default)</span></span>

```
Get-Event [[-SourceIdentifier] <String>] [<CommonParameters>]
```

### <span data-ttu-id="30b0d-108">ById</span><span class="sxs-lookup"><span data-stu-id="30b0d-108">ById</span></span>

```
Get-Event [-EventIdentifier] <Int32> [<CommonParameters>]
```

## <span data-ttu-id="30b0d-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="30b0d-109">DESCRIPTION</span></span>
<span data-ttu-id="30b0d-110">Cmdleten **Get-Event** hämtar händelser i händelse kön för Windows PowerShell för den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="30b0d-110">The **Get-Event** cmdlet gets events in the Windows PowerShell event queue for the current session.</span></span>
<span data-ttu-id="30b0d-111">Du kan hämta alla händelser eller använda parametern *EventIdentifier* eller *SourceIdentifier* för att ange händelser.</span><span class="sxs-lookup"><span data-stu-id="30b0d-111">You can get all events or use the *EventIdentifier* or *SourceIdentifier* parameter to specify the events.</span></span>

<span data-ttu-id="30b0d-112">När en händelse inträffar läggs den till i händelse kön.</span><span class="sxs-lookup"><span data-stu-id="30b0d-112">When an event occurs, it is added to the event queue.</span></span>
<span data-ttu-id="30b0d-113">Händelse kön innehåller händelser som du har registrerat, händelser som skapats med hjälp av New-Event-cmdlet och händelsen som utlöses när Windows PowerShell avslutas.</span><span class="sxs-lookup"><span data-stu-id="30b0d-113">The event queue includes events for which you have registered, events created by using the New-Event cmdlet, and the event that is raised when Windows PowerShell exits.</span></span>
<span data-ttu-id="30b0d-114">Du kan använda **Get-Event** eller Wait-Event för att hämta händelser.</span><span class="sxs-lookup"><span data-stu-id="30b0d-114">You can use **Get-Event** or Wait-Event to get the events.</span></span>

<span data-ttu-id="30b0d-115">Denna cmdlet hämtar inte händelser från Loggbokens loggarna.</span><span class="sxs-lookup"><span data-stu-id="30b0d-115">This cmdlet does not get events from the Event Viewer logs.</span></span>
<span data-ttu-id="30b0d-116">Använd Get-WinEvent eller get-EventLog för att hämta dessa händelser.</span><span class="sxs-lookup"><span data-stu-id="30b0d-116">To get those events, use Get-WinEvent or Get-EventLog.</span></span>

## <span data-ttu-id="30b0d-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="30b0d-117">EXAMPLES</span></span>

### <span data-ttu-id="30b0d-118">Exempel 1: Hämta alla händelser</span><span class="sxs-lookup"><span data-stu-id="30b0d-118">Example 1: Get all events</span></span>

```
PS C:\> Get-Event
```

<span data-ttu-id="30b0d-119">Det här kommandot hämtar alla händelser i händelse kön.</span><span class="sxs-lookup"><span data-stu-id="30b0d-119">This command gets all events in the event queue.</span></span>

### <span data-ttu-id="30b0d-120">Exempel 2: Hämta händelser efter käll-ID</span><span class="sxs-lookup"><span data-stu-id="30b0d-120">Example 2: Get events by source identifier</span></span>

```
PS C:\> Get-Event -SourceIdentifier "PowerShell.ProcessCreated"
```

<span data-ttu-id="30b0d-121">Det här kommandot hämtar händelser där värdet för egenskapen SourceIdentifier är PowerShell. ProcessCreated.</span><span class="sxs-lookup"><span data-stu-id="30b0d-121">This command gets events in which the value of the SourceIdentifier property is PowerShell.ProcessCreated.</span></span>

### <span data-ttu-id="30b0d-122">Exempel 3: Hämta en händelse baserat på den tid det genererades</span><span class="sxs-lookup"><span data-stu-id="30b0d-122">Example 3: Get an event based on the time it was generated</span></span>

```
PS C:\> $Events = Get-Event
PS C:\> $Events[0] | Format-List -Property *
ComputerName     :
RunspaceId       : c2153740-256d-46c0-a57c-b805917d1b7b
EventIdentifier  : 1
Sender           : System.Management.ManagementEventWatcher
SourceEventArgs  : System.Management.EventArrivedEventArgs
SourceArgs       : {System.Management.ManagementEventWatcher, System.Management.EventArrivedEventArgs}
SourceIdentifier : ProcessStarted
TimeGenerated    : 11/13/2008 12:09:32 PM
MessageData      : PS C:\> Get-Event | Where {$_.TimeGenerated -ge "11/13/2008 12:15:00 PM"}
ComputerName     :
RunspaceId       : c2153740-256d-46c0-a57c-b8059325d1a0
EventIdentifier  : 1
Sender           : System.Management.ManagementEventWatcher
SourceEventArgs  : System.Management.EventArrivedEventArgs
SourceArgs       : {System.Management.ManagementEventWatcher, System.Management.EventArrivedEventArgs}
SourceIdentifier : ProcessStarted
TimeGenerated    : 11/13/2008 12:15:00 PM
MessageData      :
```

<span data-ttu-id="30b0d-123">Det här exemplet visar hur du hämtar händelser genom att använda andra egenskaper än SourceIdentifier.</span><span class="sxs-lookup"><span data-stu-id="30b0d-123">This example shows how to get events by using properties other than SourceIdentifier.</span></span>

<span data-ttu-id="30b0d-124">Det första kommandot hämtar alla händelser i händelse kön och sparar dem i variabeln $Events.</span><span class="sxs-lookup"><span data-stu-id="30b0d-124">The first command gets all events in the event queue and saves them in the $Events variable.</span></span>

<span data-ttu-id="30b0d-125">Det andra kommandot använder mat ris notation för att hämta den första (0-index) händelsen i matrisen i variabeln $Events.</span><span class="sxs-lookup"><span data-stu-id="30b0d-125">The second command uses array notation to get the first (0-index) event in the array in the $Events variable.</span></span>
<span data-ttu-id="30b0d-126">Kommandot använder en pipeline-operator (|) för att skicka händelsen till kommandot Format-List, som visar alla egenskaper för händelsen i en lista.</span><span class="sxs-lookup"><span data-stu-id="30b0d-126">The command uses a pipeline operator (|) to send the event to the Format-List command, which displays all properties of the event in a list.</span></span>
<span data-ttu-id="30b0d-127">På så sätt kan du undersöka egenskaperna för händelseobjektet.</span><span class="sxs-lookup"><span data-stu-id="30b0d-127">This allows you to examine the properties of the event object.</span></span>

<span data-ttu-id="30b0d-128">Det tredje kommandot visar hur du använder Where-Object-cmdlet för att hämta en händelse baserat på den tidpunkt då den genererades.</span><span class="sxs-lookup"><span data-stu-id="30b0d-128">The third command shows how to use the Where-Object cmdlet to get an event based on the time that it was generated.</span></span>

### <span data-ttu-id="30b0d-129">Exempel 4: Hämta en händelse efter dess identifierare</span><span class="sxs-lookup"><span data-stu-id="30b0d-129">Example 4: Get an event by its identifier</span></span>

```
PS C:\> Get-Event -EventIdentifier 2
```

<span data-ttu-id="30b0d-130">Det här kommandot hämtar händelsen med händelse-ID 2.</span><span class="sxs-lookup"><span data-stu-id="30b0d-130">This command gets the event with an event identifier of 2.</span></span>

## <span data-ttu-id="30b0d-131">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="30b0d-131">PARAMETERS</span></span>

### <span data-ttu-id="30b0d-132">-EventIdentifier</span><span class="sxs-lookup"><span data-stu-id="30b0d-132">-EventIdentifier</span></span>
<span data-ttu-id="30b0d-133">Anger händelse identifierare som denna cmdlet hämtar händelser för.</span><span class="sxs-lookup"><span data-stu-id="30b0d-133">Specifies the event identifiers for which this cmdlet gets events.</span></span>

```yaml
Type: System.Int32
Parameter Sets: ById
Aliases: Id

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="30b0d-134">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="30b0d-134">-SourceIdentifier</span></span>
<span data-ttu-id="30b0d-135">Anger käll identifierare för vilka denna cmdlet hämtar händelser.</span><span class="sxs-lookup"><span data-stu-id="30b0d-135">Specifies source identifiers for which this cmdlet gets events.</span></span>
<span data-ttu-id="30b0d-136">Standardvärdet är alla händelser i händelse kön.</span><span class="sxs-lookup"><span data-stu-id="30b0d-136">The default is all events in the event queue.</span></span>
<span data-ttu-id="30b0d-137">Jokertecken är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="30b0d-137">Wildcards are not permitted.</span></span>

```yaml
Type: System.String
Parameter Sets: BySource
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="30b0d-138">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="30b0d-138">CommonParameters</span></span>
<span data-ttu-id="30b0d-139">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="30b0d-139">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="30b0d-140">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="30b0d-140">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="30b0d-141">INDATA</span><span class="sxs-lookup"><span data-stu-id="30b0d-141">INPUTS</span></span>

### <span data-ttu-id="30b0d-142">Inget</span><span class="sxs-lookup"><span data-stu-id="30b0d-142">None</span></span>
<span data-ttu-id="30b0d-143">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="30b0d-143">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="30b0d-144">UTDATA</span><span class="sxs-lookup"><span data-stu-id="30b0d-144">OUTPUTS</span></span>

### <span data-ttu-id="30b0d-145">System. Management. Automation. PSEventArgs</span><span class="sxs-lookup"><span data-stu-id="30b0d-145">System.Management.Automation.PSEventArgs</span></span>
<span data-ttu-id="30b0d-146">**Get-Event** returnerar ett **PSEventArgs** -objekt för varje händelse.</span><span class="sxs-lookup"><span data-stu-id="30b0d-146">**Get-Event** returns a **PSEventArgs** object for each event.</span></span>
<span data-ttu-id="30b0d-147">Om du vill se en beskrivning av objektet skriver `Get-Help Get-Event -Full` du och läser avsnittet anteckningar i hjälp avsnittet.</span><span class="sxs-lookup"><span data-stu-id="30b0d-147">To see a description of this object, type `Get-Help Get-Event -Full` and see the Notes section of the help topic.</span></span>

## <span data-ttu-id="30b0d-148">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="30b0d-148">NOTES</span></span>

* <span data-ttu-id="30b0d-149">Händelser, händelse prenumerationer och händelse kön finns bara i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="30b0d-149">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="30b0d-150">Om du stänger den aktuella sessionen ignoreras händelse kön och händelse prenumerationen avbryts.</span><span class="sxs-lookup"><span data-stu-id="30b0d-150">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

  <span data-ttu-id="30b0d-151">Cmdleten **Get-Event** returnerar ett **PSEventArgs** -objekt ( **system. Management. Automation. PSEventArgs** ) med följande egenskaper:</span><span class="sxs-lookup"><span data-stu-id="30b0d-151">The **Get-Event** cmdlet returns a **PSEventArgs** object ( **System.Management.Automation.PSEventArgs** ) with the following properties:</span></span>

  - <span data-ttu-id="30b0d-152">Namnet.</span><span class="sxs-lookup"><span data-stu-id="30b0d-152">ComputerName.</span></span>
<span data-ttu-id="30b0d-153">Namnet på datorn där händelsen inträffade.</span><span class="sxs-lookup"><span data-stu-id="30b0d-153">The name of the computer on which the event occurred.</span></span>
<span data-ttu-id="30b0d-154">Det här egenskap svärdet fylls bara i när händelsen vidarebefordras från en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="30b0d-154">This property value is populated only when the event is forwarded from a remote computer.</span></span>

  - <span data-ttu-id="30b0d-155">RunspaceId.</span><span class="sxs-lookup"><span data-stu-id="30b0d-155">RunspaceId.</span></span>
<span data-ttu-id="30b0d-156">Ett GUID som unikt identifierar den session där händelsen inträffade.</span><span class="sxs-lookup"><span data-stu-id="30b0d-156">A GUID that uniquely identifies the session in which the event occurred.</span></span>
<span data-ttu-id="30b0d-157">Det här egenskap svärdet fylls bara i när händelsen vidarebefordras från en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="30b0d-157">This property value is populated only when the event is forwarded from a remote computer.</span></span>

  - <span data-ttu-id="30b0d-158">EventIdentifier.</span><span class="sxs-lookup"><span data-stu-id="30b0d-158">EventIdentifier.</span></span>
<span data-ttu-id="30b0d-159">Ett heltal (Int32) som unikt identifierar händelse aviseringen i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="30b0d-159">An integer (Int32) that uniquely identifies the event notification in the current session.</span></span>

  - <span data-ttu-id="30b0d-160">Ingen.</span><span class="sxs-lookup"><span data-stu-id="30b0d-160">Sender.</span></span>
<span data-ttu-id="30b0d-161">Objektet som genererade händelsen.</span><span class="sxs-lookup"><span data-stu-id="30b0d-161">The object that generated the event.</span></span>
<span data-ttu-id="30b0d-162">I värdet för parametern *åtgärd* innehåller $Sender automatisk variabel objektet Sender.</span><span class="sxs-lookup"><span data-stu-id="30b0d-162">In the value of the *Action* parameter, the $Sender automatic variable contains the sender object.</span></span>

  - <span data-ttu-id="30b0d-163">SourceEventArgs.</span><span class="sxs-lookup"><span data-stu-id="30b0d-163">SourceEventArgs.</span></span>
<span data-ttu-id="30b0d-164">Den första parametern som härleds från EventArgs, om den finns.</span><span class="sxs-lookup"><span data-stu-id="30b0d-164">The first parameter that derives from EventArgs, if it exists.</span></span>
<span data-ttu-id="30b0d-165">I en tidsinställd händelse där signaturen har skickat av formulär objekt, timers. ElapsedEventArgs e, skulle egenskapen SourceEventArgs innehålla timers. ElapsedEventArgs.</span><span class="sxs-lookup"><span data-stu-id="30b0d-165">For example, in a timer elapsed event in which the signature has the form Object sender, Timers.ElapsedEventArgs e, the SourceEventArgs property would contain the Timers.ElapsedEventArgs.</span></span>
<span data-ttu-id="30b0d-166">I värdet för parametern *åtgärd* innehåller den $EventArgs automatiska variabeln det här värdet.</span><span class="sxs-lookup"><span data-stu-id="30b0d-166">In the value of the *Action* parameter, the $EventArgs automatic variable contains this value.</span></span>

  - <span data-ttu-id="30b0d-167">SourceArgs.</span><span class="sxs-lookup"><span data-stu-id="30b0d-167">SourceArgs.</span></span>
<span data-ttu-id="30b0d-168">Alla parametrar för den ursprungliga händelse under skriften.</span><span class="sxs-lookup"><span data-stu-id="30b0d-168">All parameters of the original event signature.</span></span>
<span data-ttu-id="30b0d-169">För en standardsignatur för händelser \[ representerar $args 0 \] avsändaren och $args \[ 1 \] representerar SourceEventArgs.</span><span class="sxs-lookup"><span data-stu-id="30b0d-169">For a standard event signature, $Args\[0\] represents the sender, and $Args\[1\] represents the SourceEventArgs.</span></span>
<span data-ttu-id="30b0d-170">I värdet för parametern *åtgärd* innehåller den $args automatiska variabeln det här värdet.</span><span class="sxs-lookup"><span data-stu-id="30b0d-170">In the value of the *Action* parameter, the $Args automatic variable contains this value.</span></span>

  - <span data-ttu-id="30b0d-171">SourceIdentifier.</span><span class="sxs-lookup"><span data-stu-id="30b0d-171">SourceIdentifier.</span></span>
<span data-ttu-id="30b0d-172">En sträng som identifierar händelse prenumerationen.</span><span class="sxs-lookup"><span data-stu-id="30b0d-172">A string that identifies the event subscription.</span></span>
<span data-ttu-id="30b0d-173">I värdet för parametern *åtgärd* innehåller egenskapen SourceIdentifier för den automatiska variabeln $Event det här värdet.</span><span class="sxs-lookup"><span data-stu-id="30b0d-173">In the value of the *Action* parameter, the SourceIdentifier property of the $Event automatic variable contains this value.</span></span>

  - <span data-ttu-id="30b0d-174">TimeGenerated.</span><span class="sxs-lookup"><span data-stu-id="30b0d-174">TimeGenerated.</span></span>
<span data-ttu-id="30b0d-175">Ett **datetime** -objekt som representerar tiden då händelsen genererades.</span><span class="sxs-lookup"><span data-stu-id="30b0d-175">A **DateTime** object that represents the time at which the event was generated.</span></span>
<span data-ttu-id="30b0d-176">I värdet för parametern *åtgärd* innehåller egenskapen TimeGenerated för den automatiska variabeln $Event det här värdet.</span><span class="sxs-lookup"><span data-stu-id="30b0d-176">In the value of the *Action* parameter, the TimeGenerated property of the $Event automatic variable contains this value.</span></span>

  <span data-ttu-id="30b0d-177">--MessageData.</span><span class="sxs-lookup"><span data-stu-id="30b0d-177">--MessageData.</span></span>
<span data-ttu-id="30b0d-178">Data som är associerade med händelse prenumerationen.</span><span class="sxs-lookup"><span data-stu-id="30b0d-178">Data associated with the event subscription.</span></span>
<span data-ttu-id="30b0d-179">Användarna anger dessa data när de registrerar en händelse.</span><span class="sxs-lookup"><span data-stu-id="30b0d-179">Users specify this data when they register an event.</span></span>
<span data-ttu-id="30b0d-180">I värdet för parametern *åtgärd* innehåller egenskapen MessageData för den automatiska variabeln $Event det här värdet.</span><span class="sxs-lookup"><span data-stu-id="30b0d-180">In the value of the *Action* parameter, the MessageData property of the $Event automatic variable contains this value.</span></span>

*

## <span data-ttu-id="30b0d-181">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="30b0d-181">RELATED LINKS</span></span>

[<span data-ttu-id="30b0d-182">Ny händelse</span><span class="sxs-lookup"><span data-stu-id="30b0d-182">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="30b0d-183">Registrera – EngineEvent</span><span class="sxs-lookup"><span data-stu-id="30b0d-183">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="30b0d-184">Registrera – ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="30b0d-184">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="30b0d-185">Ta bort händelse</span><span class="sxs-lookup"><span data-stu-id="30b0d-185">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="30b0d-186">Avregistrera-händelse</span><span class="sxs-lookup"><span data-stu-id="30b0d-186">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="30b0d-187">Vänta-händelse</span><span class="sxs-lookup"><span data-stu-id="30b0d-187">Wait-Event</span></span>](Wait-Event.md)