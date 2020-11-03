---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/27/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/register-objectevent?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-ObjectEvent
ms.openlocfilehash: a6ed76164dbc2773393211ad8474becb499986a3
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262346"
---
# <span data-ttu-id="95392-103">Register-ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="95392-103">Register-ObjectEvent</span></span>

## <span data-ttu-id="95392-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="95392-104">SYNOPSIS</span></span>
<span data-ttu-id="95392-105">Prenumererar på händelser som genereras av ett Microsoft .NET Framework-objekt.</span><span class="sxs-lookup"><span data-stu-id="95392-105">Subscribes to the events that are generated by a Microsoft .NET Framework object.</span></span>

## <span data-ttu-id="95392-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="95392-106">SYNTAX</span></span>

```
Register-ObjectEvent [-InputObject] <PSObject> [-EventName] <String> [[-SourceIdentifier] <String>]
 [[-Action] <ScriptBlock>] [-MessageData <PSObject>] [-SupportEvent] [-Forward] [-MaxTriggerCount <Int32>]
 [<CommonParameters>]
```

## <span data-ttu-id="95392-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="95392-107">DESCRIPTION</span></span>

<span data-ttu-id="95392-108">`Register-ObjectEvent`Cmdleten prenumererar på händelser som genereras av .net-objekt på den lokala datorn eller på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="95392-108">The `Register-ObjectEvent` cmdlet subscribes to events that are generated by .NET objects on the local computer or on a remote computer.</span></span>

<span data-ttu-id="95392-109">När den prenumererade händelsen höjs, läggs den till i händelse kön i sessionen.</span><span class="sxs-lookup"><span data-stu-id="95392-109">When the subscribed event is raised, it is added to the event queue in your session.</span></span> <span data-ttu-id="95392-110">Använd cmdleten för att hämta händelser i händelse kön `Get-Event` .</span><span class="sxs-lookup"><span data-stu-id="95392-110">To get events in the event queue, use the `Get-Event` cmdlet.</span></span>

<span data-ttu-id="95392-111">Du kan använda parametrarna för `Register-ObjectEvent` för att ange egenskaps värden för de händelser som kan hjälpa dig att identifiera händelsen i kön.</span><span class="sxs-lookup"><span data-stu-id="95392-111">You can use the parameters of `Register-ObjectEvent` to specify property values of the events that can help you to identify the event in the queue.</span></span> <span data-ttu-id="95392-112">Du kan också använda **Åtgärds** parametern för att ange åtgärder som ska vidtas när en prenumerations händelse höjs och parametern **Forward** för att skicka fjärrhändelser till händelse kön i den lokala sessionen.</span><span class="sxs-lookup"><span data-stu-id="95392-112">You can also use the **Action** parameter to specify actions to take when a subscribed event is raised and the **Forward** parameter to send remote events to the event queue in the local session.</span></span>

<span data-ttu-id="95392-113">När du prenumererar på en händelse läggs en händelse prenumerant till i sessionen.</span><span class="sxs-lookup"><span data-stu-id="95392-113">When you subscribe to an event, an event subscriber is added to your session.</span></span> <span data-ttu-id="95392-114">Använd cmdleten för att hämta händelse prenumeranterna i sessionen `Get-EventSubscriber` .</span><span class="sxs-lookup"><span data-stu-id="95392-114">To get the event subscribers in the session, use the `Get-EventSubscriber` cmdlet.</span></span> <span data-ttu-id="95392-115">Om du vill avbryta prenumerationen använder du `Unregister-Event` cmdleten, som tar bort händelse prenumeranten från sessionen.</span><span class="sxs-lookup"><span data-stu-id="95392-115">To cancel the subscription, use the `Unregister-Event` cmdlet, which deletes the event subscriber from the session.</span></span>

## <span data-ttu-id="95392-116">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="95392-116">EXAMPLES</span></span>

### <span data-ttu-id="95392-117">Exempel 1: prenumerera på händelser när en ny process startar</span><span class="sxs-lookup"><span data-stu-id="95392-117">Example 1: Subscribe to events when a new process starts</span></span>

<span data-ttu-id="95392-118">Det här exemplet prenumererar på händelser som genereras när en ny process startar.</span><span class="sxs-lookup"><span data-stu-id="95392-118">This example subscribes to events generated when a new process starts.</span></span>

<span data-ttu-id="95392-119">Kommandot använder **ManagementEventWatcher** -objektet för att hämta **EventArrived** -händelser.</span><span class="sxs-lookup"><span data-stu-id="95392-119">The command uses the **ManagementEventWatcher** object to get **EventArrived** events.</span></span> <span data-ttu-id="95392-120">Ett Query-objekt anger att händelserna är instans skapande händelser för klassen **Win32_Process** .</span><span class="sxs-lookup"><span data-stu-id="95392-120">A query object specifies that the events are instance creation events for the **Win32_Process** class.</span></span>

```powershell
$queryParameters = '__InstanceCreationEvent', (New-Object TimeSpan 0,0,1),
    "TargetInstance isa 'Win32_Process'"
$Query = New-Object System.Management.WqlEventQuery -ArgumentList $queryParameters
$ProcessWatcher = New-Object System.Management.ManagementEventWatcher $Query
Register-ObjectEvent -InputObject $ProcessWatcher -EventName "EventArrived"
```

### <span data-ttu-id="95392-121">Exempel 2: Ange en åtgärd för att svara på en händelse</span><span class="sxs-lookup"><span data-stu-id="95392-121">Example 2: Specify an action to respond to an event</span></span>

<span data-ttu-id="95392-122">När du anger en åtgärd läggs inte händelser som aktive ras till i händelse kön.</span><span class="sxs-lookup"><span data-stu-id="95392-122">When you specify an action, events that are raised are not added to the event queue.</span></span> <span data-ttu-id="95392-123">I stället svarar åtgärden på händelsen.</span><span class="sxs-lookup"><span data-stu-id="95392-123">Instead, the action responds to the event.</span></span> <span data-ttu-id="95392-124">I det här exemplet utlöses en ny **ProcessCreated** -händelse när en instans skapas, vilket innebär att en ny process startas.</span><span class="sxs-lookup"><span data-stu-id="95392-124">In this example, when an instance creation event is raised indicating that a new process is started, a new **ProcessCreated** event is raised.</span></span>

```powershell
$queryParameters = '__InstanceCreationEvent', (New-Object TimeSpan 0,0,1),
    "TargetInstance isa 'Win32_Process'"
$Query = New-Object System.Management.WqlEventQuery -ArgumentList $queryParameters
$ProcessWatcher = New-Object System.Management.ManagementEventWatcher $query
$newEventArgs = @{
    SourceIdentifier = 'PowerShell.ProcessCreated'
    Sender = $Sender
    EventArguments = $EventArgs.NewEvent.TargetInstance
}
$Action = { New-Event @newEventArgs }
Register-ObjectEvent -InputObject $ProcessWatcher -EventName "EventArrived" -Action $Action
```

```Output
Id   Name               PSJobTypeName   State       HasMoreData   Location   Command
--   ----               -------------   -----       -----------   --------   -------
 5   3db2d67a-efff-...                 NotStarted   False                    New-Event @newEventArgs
```

<span data-ttu-id="95392-125">Åtgärden använder sig av `$Sender` och `$EventArgs` Automatiska variabler som endast fylls i för händelse åtgärder.</span><span class="sxs-lookup"><span data-stu-id="95392-125">The action uses the `$Sender` and `$EventArgs` automatic variables which are populated only for event actions.</span></span>

<span data-ttu-id="95392-126">`Register-ObjectEvent`Kommandot returnerar ett jobb objekt som representerar åtgärden, som körs som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="95392-126">The `Register-ObjectEvent` command returns a job object that represents the action, which runs as a background job.</span></span> <span data-ttu-id="95392-127">Du kan använda jobb-cmdletar, till exempel `Get-Job` och `Receive-Job` , för att hantera bakgrunds jobbet.</span><span class="sxs-lookup"><span data-stu-id="95392-127">You can use the Job cmdlets, such as `Get-Job` and `Receive-Job`, to manage the background job.</span></span> <span data-ttu-id="95392-128">Mer information finns i artikeln [om jobb](../Microsoft.PowerShell.Core/About/about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="95392-128">For more information, see [about_Jobs](../Microsoft.PowerShell.Core/About/about_Jobs.md).</span></span>

### <span data-ttu-id="95392-129">Exempel 3: prenumerera på objekt händelser på fjärrdatorer</span><span class="sxs-lookup"><span data-stu-id="95392-129">Example 3: Subscribe to object events on remote computers</span></span>

<span data-ttu-id="95392-130">Det här exemplet visar hur du prenumererar på objekt händelser på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="95392-130">This example shows how to subscribe to object events on remote computers.</span></span> <span data-ttu-id="95392-131">I det här exemplet används `Enable-ProcessCreationEvent` funktionen som definieras i `ProcessCreationEvent.ps1` skript filen.</span><span class="sxs-lookup"><span data-stu-id="95392-131">This example uses the `Enable-ProcessCreationEvent` function that is defined in the `ProcessCreationEvent.ps1` script file.</span></span> <span data-ttu-id="95392-132">Det här skriptet är tillgängligt för alla datorer i exemplet.</span><span class="sxs-lookup"><span data-stu-id="95392-132">This script is available to all computers in the example.</span></span>

```powershell
# ProcessCreationEvent.ps1
function  Enable-ProcessCreationEvent {
    $queryParameters = "__InstanceCreationEvent", (New-Object TimeSpan 0,0,1),
        "TargetInstance isa 'Win32_Process'"
    $Query = New-Object System.Management.WqlEventQuery -ArgumentList $queryParameters

    $objectEventArgs = @{
        Input = New-Object System.Management.ManagementEventWatcher $Query
        EventName = 'EventArrived'
        SourceIdentifier = 'WMI.ProcessCreated'
        MessageData = 'Test'
        Forward = $True
    }
    Register-ObjectEvent @objectEventArgs
}

$S = New-PSSession -ComputerName "Server01, Server02"
Invoke-Command -Session $S -FilePath ProcessCreationEvent.ps1
Invoke-Command -Session $S { Enable-ProcessCreationEvent }
```

<span data-ttu-id="95392-133">Den första vi skapar **PSSessions** på två fjärrdatorer och sparar dem i `$S` variabeln.</span><span class="sxs-lookup"><span data-stu-id="95392-133">The first we create **PSSessions** on two remote computers and save them in the `$S` variable.</span></span> <span data-ttu-id="95392-134">Sedan `Invoke-Command` kör cmdleten `ProcessCreationEvent.ps1` skriptet i varje PSSessions i `$S` .</span><span class="sxs-lookup"><span data-stu-id="95392-134">Next, the `Invoke-Command` cmdlet run the `ProcessCreationEvent.ps1` script in the each of the PSSessions in `$S`.</span></span> <span data-ttu-id="95392-135">Den här åtgärden skapar `Enable-ProcessCreationEvent` funktionen i fjärrsessionerna.</span><span class="sxs-lookup"><span data-stu-id="95392-135">This action creates the `Enable-ProcessCreationEvent` function in the remote sessions.</span></span>
<span data-ttu-id="95392-136">Slutligen kör vi `Enable-ProcessCreationEvent` funktionen i fjärrsessionerna.</span><span class="sxs-lookup"><span data-stu-id="95392-136">Finally, we run the `Enable-ProcessCreationEvent` function in the remote sessions.</span></span>

 <span data-ttu-id="95392-137">Funktionen innehåller ett- `Register-ObjectEvent` kommando som prenumererar på händelser för att skapa instanser på **Win32_Process** -objektet genom **ManagementEventWatcher** -objektet och dess **EventArrived** -händelse.</span><span class="sxs-lookup"><span data-stu-id="95392-137">The function includes a `Register-ObjectEvent` command that subscribes to instance creation events on the **Win32_Process** object through the **ManagementEventWatcher** object and its **EventArrived** event.</span></span>

### <span data-ttu-id="95392-138">Exempel 4: Använd den dynamiska modulen i PSEventJob-objektet</span><span class="sxs-lookup"><span data-stu-id="95392-138">Example 4: Use the dynamic module in the PSEventJob object</span></span>

<span data-ttu-id="95392-139">Det här exemplet visar hur du använder den dynamiska modulen i **PSEventJob** -objektet som skapas när du inkluderar en **åtgärd** i en händelse registrering.</span><span class="sxs-lookup"><span data-stu-id="95392-139">This example shows how to use the dynamic module in the **PSEventJob** object that is created when you include an **Action** in an event registration.</span></span> <span data-ttu-id="95392-140">Först createand vi och aktiverar ett Timer-objekt och anger sedan intervallet för timer till 500 (millisekunder).</span><span class="sxs-lookup"><span data-stu-id="95392-140">First we createand and enable a timer object, then set the interval of the timer to 500 (milliseconds).</span></span> <span data-ttu-id="95392-141">`Register-ObjectEvent`Cmdlet: en registrerar händelsen **förfluten tid** för objektet timer.</span><span class="sxs-lookup"><span data-stu-id="95392-141">The `Register-ObjectEvent` cmdlet registers the **Elapsed** event of the timer object.</span></span> <span data-ttu-id="95392-142">**PSEventJob** -objektet sparas i `$Job` variabeln och finns också i **Åtgärds** egenskapen för händelse prenumeranten.</span><span class="sxs-lookup"><span data-stu-id="95392-142">The **PSEventJob** object is saved in the `$Job` variable and is also available in the **Action** property of the event subscriber.</span></span> <span data-ttu-id="95392-143">Mer information finns i [Get-EventSubscriber](Get-EventSubscriber.md).</span><span class="sxs-lookup"><span data-stu-id="95392-143">For more information, see [Get-EventSubscriber](Get-EventSubscriber.md).</span></span>

<span data-ttu-id="95392-144">När timer-intervallet förflyter, utlöses en händelse och åtgärden utförs.</span><span class="sxs-lookup"><span data-stu-id="95392-144">Whenever the timer interval elapses, an event is raised and the action is executed.</span></span> <span data-ttu-id="95392-145">I det här fallet `Get-Random` genererar cmdleten ett slumpmässigt nummer mellan 0 och 100 och sparar det i `$Random` variabeln.</span><span class="sxs-lookup"><span data-stu-id="95392-145">In this case, the `Get-Random` cmdlet generates a random number between 0 and 100 and saves it in the `$Random` variable.</span></span>

```powershell
$Timer = New-Object Timers.Timer
$Timer.Interval = 500
$Timer.Enabled = $True
$objectEventArgs = @{
    InputObject = $Timer
    EventName = 'Elapsed'
    SourceIdentifier = 'Timer.Random'
    Action = {$Random = Get-Random -Min 0 -Max 100}
}
$Job = Register-ObjectEvent @objectEventArgs
$Job | Format-List -Property *
& $Job.module {$Random}
& $Job.module {$Random}
```

```Output
State         : Running
Module        : __DynamicModule_53113769-31f2-42dc-830b-8749325e28d6
StatusMessage :
HasMoreData   : True
Location      :
Command       : $Random = Get-Random -Min 0 -Max 100
JobStateInfo  : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : 47b5ec9f-bfe3-4605-860a-4674e5d44ca8
Id            : 7
Name          : Timer.Random
ChildJobs     : {}
PSBeginTime   : 6/27/2019 10:19:06 AM
PSEndTime     :
PSJobTypeName :
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
Information   : {}
60
47
```

<span data-ttu-id="95392-146">**PSEventJob** har en **modul** -egenskap som innehåller en dynamisk skript-modul som implementerar åtgärden.</span><span class="sxs-lookup"><span data-stu-id="95392-146">The **PSEventJob** has a **Module** property that contains a dynamic script module that implements the action.</span></span> <span data-ttu-id="95392-147">Med hjälp av anrops operatorn ( `&` ) anropar vi kommandot i modulen för att visa värdet för `$Random` variabeln.</span><span class="sxs-lookup"><span data-stu-id="95392-147">Using the call operator (`&`),  we invoke the command in the module to display the value of the `$Random` variable.</span></span>

<span data-ttu-id="95392-148">Mer information om moduler finns i [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).</span><span class="sxs-lookup"><span data-stu-id="95392-148">For more information about modules, see [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).</span></span>

## <span data-ttu-id="95392-149">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="95392-149">PARAMETERS</span></span>

### <span data-ttu-id="95392-150">-Åtgärd</span><span class="sxs-lookup"><span data-stu-id="95392-150">-Action</span></span>

<span data-ttu-id="95392-151">Anger kommandon för att hantera händelsen.</span><span class="sxs-lookup"><span data-stu-id="95392-151">Specifies the commands to handle the event.</span></span> <span data-ttu-id="95392-152">Kommandona i **åtgärden** körs när en händelse höjs, i stället för att skicka händelsen till händelse kön.</span><span class="sxs-lookup"><span data-stu-id="95392-152">The commands in the **Action** run when an event is raised, instead of sending the event to the event queue.</span></span> <span data-ttu-id="95392-153">Omge kommandoen med klammerparenteser ({}) för att skapa ett skript block.</span><span class="sxs-lookup"><span data-stu-id="95392-153">Enclose the commands in braces ( { } ) to create a script block.</span></span>

<span data-ttu-id="95392-154">Värdet för **Åtgärds** parametern kan innehålla `$Event` `$EventSubscriber` variablerna,, `$Sender` , `$EventArgs` och `$Args` .</span><span class="sxs-lookup"><span data-stu-id="95392-154">The value of the **Action** parameter can include the `$Event`, `$EventSubscriber`, `$Sender`, `$EventArgs`, and `$Args` automatic variables.</span></span> <span data-ttu-id="95392-155">Dessa variabler ger information om händelsen till **Åtgärds** skript blocket.</span><span class="sxs-lookup"><span data-stu-id="95392-155">These variables provide information about the event to the **Action** script block.</span></span> <span data-ttu-id="95392-156">Mer information finns i [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="95392-156">For more information, see [about_Automatic_Variables](../Microsoft.PowerShell.Core/About/about_Automatic_Variables.md).</span></span>

<span data-ttu-id="95392-157">När du anger en åtgärd `Register-ObjectEvent` returnerar ett händelse jobb objekt som representerar den åtgärden.</span><span class="sxs-lookup"><span data-stu-id="95392-157">When you specify an action, `Register-ObjectEvent` returns an event job object that represents that action.</span></span> <span data-ttu-id="95392-158">Du kan använda jobb-cmdletar för att hantera händelse jobbet.</span><span class="sxs-lookup"><span data-stu-id="95392-158">You can use the Job cmdlets to manage the event job.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: 101
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="95392-159">– EventName</span><span class="sxs-lookup"><span data-stu-id="95392-159">-EventName</span></span>

<span data-ttu-id="95392-160">Anger händelsen som du prenumererar på.</span><span class="sxs-lookup"><span data-stu-id="95392-160">Specifies the event to which you are subscribing.</span></span>

<span data-ttu-id="95392-161">Värdet för den här parametern måste vara namnet på händelsen som .NET-objektet exponerar.</span><span class="sxs-lookup"><span data-stu-id="95392-161">The value of this parameter must be the name of the event that the .NET object exposes.</span></span> <span data-ttu-id="95392-162">Klassen **ManagementEventWatcher** har till exempel händelser som heter **EventArrived** och **stoppats**.</span><span class="sxs-lookup"><span data-stu-id="95392-162">For example, the **ManagementEventWatcher** class has events named **EventArrived** and **Stopped**.</span></span> <span data-ttu-id="95392-163">Använd cmdleten för att hitta händelse namnet för en händelse `Get-Member` .</span><span class="sxs-lookup"><span data-stu-id="95392-163">To find the event name of an event, use the `Get-Member` cmdlet.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="95392-164">-Forward</span><span class="sxs-lookup"><span data-stu-id="95392-164">-Forward</span></span>

<span data-ttu-id="95392-165">Anger att cmdleten skickar händelser för den här prenumerationen till en fjärran sluten session.</span><span class="sxs-lookup"><span data-stu-id="95392-165">Indicates that the cmdlet sends events for this subscription to a remote session.</span></span> <span data-ttu-id="95392-166">Använd den här parametern när du registrerar händelser på en fjärrdator eller i en fjärran sluten session.</span><span class="sxs-lookup"><span data-stu-id="95392-166">Use this parameter when you are registering for events on a remote computer or in a remote session.</span></span>

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

### <span data-ttu-id="95392-167">– InputObject</span><span class="sxs-lookup"><span data-stu-id="95392-167">-InputObject</span></span>

<span data-ttu-id="95392-168">Anger det .NET-objekt som genererar händelserna.</span><span class="sxs-lookup"><span data-stu-id="95392-168">Specifies the .NET object that generates the events.</span></span> <span data-ttu-id="95392-169">Ange en variabel som innehåller objektet eller Skriv ett kommando eller uttryck som hämtar objektet.</span><span class="sxs-lookup"><span data-stu-id="95392-169">Enter a variable that contains the object, or type a command or expression that gets the object.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="95392-170">-MaxTriggerCount</span><span class="sxs-lookup"><span data-stu-id="95392-170">-MaxTriggerCount</span></span>

<span data-ttu-id="95392-171">Anger det maximala antalet gånger som en händelse kan utlösas.</span><span class="sxs-lookup"><span data-stu-id="95392-171">Specifies the maximum number of times an event can be triggered.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="95392-172">-MessageData</span><span class="sxs-lookup"><span data-stu-id="95392-172">-MessageData</span></span>

<span data-ttu-id="95392-173">Anger eventuella ytterligare data som ska associeras med den här händelse prenumerationen.</span><span class="sxs-lookup"><span data-stu-id="95392-173">Specifies any additional data to be associated with this event subscription.</span></span> <span data-ttu-id="95392-174">Värdet för den här parametern visas i egenskapen MessageData för alla händelser som är associerade med den här prenumerationen.</span><span class="sxs-lookup"><span data-stu-id="95392-174">The value of this parameter appears in the MessageData property of all events associated with this subscription.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="95392-175">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="95392-175">-SourceIdentifier</span></span>

<span data-ttu-id="95392-176">Anger ett namn som du väljer för prenumerationen.</span><span class="sxs-lookup"><span data-stu-id="95392-176">Specifies a name that you select for the subscription.</span></span> <span data-ttu-id="95392-177">Det namn du väljer måste vara unikt i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="95392-177">The name that you select must be unique in the current session.</span></span> <span data-ttu-id="95392-178">Standardvärdet är det GUID som PowerShell tilldelar.</span><span class="sxs-lookup"><span data-stu-id="95392-178">The default value is the GUID that PowerShell assigns.</span></span>

<span data-ttu-id="95392-179">Värdet för den här parametern visas i värdet för egenskapen **SourceIdentifier** för Subscriber-objektet och alla händelse objekt som är associerade med den här prenumerationen.</span><span class="sxs-lookup"><span data-stu-id="95392-179">The value of this parameter appears in the value of the **SourceIdentifier** property of the subscriber object and all event objects associated with this subscription.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 100
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="95392-180">-SupportEvent</span><span class="sxs-lookup"><span data-stu-id="95392-180">-SupportEvent</span></span>

<span data-ttu-id="95392-181">Anger att cmdleten döljer händelse prenumerationen.</span><span class="sxs-lookup"><span data-stu-id="95392-181">Indicates that the cmdlet hides the event subscription.</span></span> <span data-ttu-id="95392-182">Använd den här parametern när den aktuella prenumerationen är en del av en mer komplex metod för registrering av händelser och inte bör identifieras separat.</span><span class="sxs-lookup"><span data-stu-id="95392-182">Use this parameter when the current subscription is part of a more complex event registration mechanism and should not be discovered independently.</span></span>

<span data-ttu-id="95392-183">Om du vill visa eller avbryta en prenumeration som har skapats med parametern **SupportEvent** använder du parametern **Force** i `Get-EventSubscriber` `Unregister-Event` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="95392-183">To view or cancel a subscription that was created with the **SupportEvent** parameter, use the **Force** parameter of the `Get-EventSubscriber` and `Unregister-Event` cmdlets.</span></span>

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

### <span data-ttu-id="95392-184">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="95392-184">CommonParameters</span></span>

<span data-ttu-id="95392-185">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="95392-185">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="95392-186">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="95392-186">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="95392-187">INDATA</span><span class="sxs-lookup"><span data-stu-id="95392-187">INPUTS</span></span>

### <span data-ttu-id="95392-188">Inget</span><span class="sxs-lookup"><span data-stu-id="95392-188">None</span></span>

<span data-ttu-id="95392-189">Det går inte att skicka pipe-objekt till `Register-ObjectEvent` .</span><span class="sxs-lookup"><span data-stu-id="95392-189">You cannot pipe objects to `Register-ObjectEvent`.</span></span>

## <span data-ttu-id="95392-190">UTDATA</span><span class="sxs-lookup"><span data-stu-id="95392-190">OUTPUTS</span></span>

### <span data-ttu-id="95392-191">Ingen eller system. Management. Automation. PSEventJob</span><span class="sxs-lookup"><span data-stu-id="95392-191">None or System.Management.Automation.PSEventJob</span></span>

<span data-ttu-id="95392-192">När du använder parametern **åtgärd** `Register-ObjectEvent` returnerar objektet **system. Management. Automation. PSEventJob** .</span><span class="sxs-lookup"><span data-stu-id="95392-192">When you use the **Action** parameter, `Register-ObjectEvent` returns a **System.Management.Automation.PSEventJob** object.</span></span> <span data-ttu-id="95392-193">Annars genererar den inga utdata.</span><span class="sxs-lookup"><span data-stu-id="95392-193">Otherwise, it does not generate any output.</span></span>

## <span data-ttu-id="95392-194">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="95392-194">NOTES</span></span>

<span data-ttu-id="95392-195">Händelser, händelse prenumerationer och händelse kön finns bara i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="95392-195">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="95392-196">Om du stänger den aktuella sessionen ignoreras händelse kön och händelse prenumerationen avbryts.</span><span class="sxs-lookup"><span data-stu-id="95392-196">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

## <span data-ttu-id="95392-197">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="95392-197">RELATED LINKS</span></span>

[<span data-ttu-id="95392-198">Hämta händelse</span><span class="sxs-lookup"><span data-stu-id="95392-198">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="95392-199">Ny händelse</span><span class="sxs-lookup"><span data-stu-id="95392-199">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="95392-200">Registrera – EngineEvent</span><span class="sxs-lookup"><span data-stu-id="95392-200">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="95392-201">Ta bort händelse</span><span class="sxs-lookup"><span data-stu-id="95392-201">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="95392-202">Avregistrera-händelse</span><span class="sxs-lookup"><span data-stu-id="95392-202">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="95392-203">Vänta-händelse</span><span class="sxs-lookup"><span data-stu-id="95392-203">Wait-Event</span></span>](Wait-Event.md)