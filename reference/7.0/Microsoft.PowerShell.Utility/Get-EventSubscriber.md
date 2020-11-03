---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-eventsubscriber?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-EventSubscriber
ms.openlocfilehash: 0d8808abf861390b4716e125a05cfa40b23a854a
ms.sourcegitcommit: de63e9481cf8024883060aae61fb02c59c2de662
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/03/2020
ms.locfileid: "93262713"
---
# <span data-ttu-id="d1258-103">Get-EventSubscriber</span><span class="sxs-lookup"><span data-stu-id="d1258-103">Get-EventSubscriber</span></span>

## <span data-ttu-id="d1258-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="d1258-104">SYNOPSIS</span></span>
<span data-ttu-id="d1258-105">Hämtar händelse prenumeranterna i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="d1258-105">Gets the event subscribers in the current session.</span></span>

## <span data-ttu-id="d1258-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="d1258-106">SYNTAX</span></span>

### <span data-ttu-id="d1258-107">BySource (standard)</span><span class="sxs-lookup"><span data-stu-id="d1258-107">BySource (Default)</span></span>

```
Get-EventSubscriber [[-SourceIdentifier] <String>] [-Force] [<CommonParameters>]
```

### <span data-ttu-id="d1258-108">ById</span><span class="sxs-lookup"><span data-stu-id="d1258-108">ById</span></span>

```
Get-EventSubscriber [-SubscriptionId] <Int32> [-Force] [<CommonParameters>]
```

## <span data-ttu-id="d1258-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="d1258-109">DESCRIPTION</span></span>

<span data-ttu-id="d1258-110">**Get-EventSubscriber** -cmdlet: en hämtar händelse prenumeranterna i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="d1258-110">The **Get-EventSubscriber** cmdlet gets the event subscribers in the current session.</span></span>

<span data-ttu-id="d1258-111">När du prenumererar på en händelse genom att använda en register händelse-cmdlet läggs en händelse prenumerant till i din PowerShell-session och de händelser som du har prenumererat på läggs till i händelse kön när de utlöses.</span><span class="sxs-lookup"><span data-stu-id="d1258-111">When you subscribe to an event by using a Register event cmdlet, an event subscriber is added to your PowerShell session, and the events to which you subscribed are added to your event queue whenever they are raised.</span></span>
<span data-ttu-id="d1258-112">Om du vill avbryta en händelse prenumeration tar du bort händelse prenumeranten med hjälp av Unregister-Event-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="d1258-112">To cancel an event subscription, delete the event subscriber by using the Unregister-Event cmdlet.</span></span>

## <span data-ttu-id="d1258-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="d1258-113">EXAMPLES</span></span>

### <span data-ttu-id="d1258-114">Exempel 1: Hämta händelse prenumeranten för en timer-händelse</span><span class="sxs-lookup"><span data-stu-id="d1258-114">Example 1: Get the event subscriber for a timer event</span></span>

```
PS C:\> $Timer = New-Object Timers.Timer
PS C:\> $Timer | Get-Member -Type Event
PS C:\> Register-ObjectEvent -InputObject $Timer -EventName Elapsed -SourceIdentifier Timer.Elapsed
PS C:\> Get-EventSubscriber
PS C:\> $Timer = New-Object Timers.Timer
PS C:\> $Timer | Get-Member -Type Event
TypeName: System.Timers.Timer
Name     MemberType Definition
----     ---------- ----------
Disposed Event      System.EventHandler Disposed(System.Object, System.EventArgs)
Elapsed  Event      System.Timers.ElapsedEventHandler Elapsed(System.Object, System.Timers.ElapsedEventArgs) PS C:\> Register-ObjectEvent -InputObject $Timer -EventName Elapsed -SourceIdentifier Timer.Elapsed
PS C:\> Get-EventSubscriber
SubscriptionId   : 4
SourceObject     : System.Timers.Timer
EventName        : Elapsed
SourceIdentifier : Timer.Elapsed
Action           :
HandlerDelegate  :
SupportEvent     : False
ForwardEvent     : False
```

<span data-ttu-id="d1258-115">I det här exemplet används kommandot **Get-EventSubscriber** för att hämta händelse prenumeranten för en timer-händelse.</span><span class="sxs-lookup"><span data-stu-id="d1258-115">This example uses a **Get-EventSubscriber** command to get the event subscriber for a timer event.</span></span>

<span data-ttu-id="d1258-116">Det första kommandot använder cmdleten New-Object för att skapa en instans av ett Timer-objekt.</span><span class="sxs-lookup"><span data-stu-id="d1258-116">The first command uses the New-Object cmdlet to create an instance of a timer object.</span></span>
<span data-ttu-id="d1258-117">Det sparar det nya timer-objektet i $Timer-variabeln.</span><span class="sxs-lookup"><span data-stu-id="d1258-117">It saves the new timer object in the $Timer variable.</span></span>

<span data-ttu-id="d1258-118">Det andra kommandot använder cmdleten Get-Member för att visa de händelser som är tillgängliga för Timer-objekt.</span><span class="sxs-lookup"><span data-stu-id="d1258-118">The second command uses the Get-Member cmdlet to display the events that are available for timer objects.</span></span>
<span data-ttu-id="d1258-119">Kommandot använder typ parametern för cmdleten **Get-Member** med värdet event.</span><span class="sxs-lookup"><span data-stu-id="d1258-119">The command uses the Type parameter of the **Get-Member** cmdlet with a value of Event.</span></span>

<span data-ttu-id="d1258-120">Det tredje kommandot använder Register-ObjectEvent-cmdleten för att registrera för den förflutna händelsen för det tidsinställda objektet.</span><span class="sxs-lookup"><span data-stu-id="d1258-120">The third command uses the Register-ObjectEvent cmdlet to register for the Elapsed event on the timer object.</span></span>

<span data-ttu-id="d1258-121">Det fjärde kommandot använder cmdleten **Get-EventSubscriber** för att hämta händelse prenumeranten för den förflutna händelsen.</span><span class="sxs-lookup"><span data-stu-id="d1258-121">The fourth command uses the **Get-EventSubscriber** cmdlet to get the event subscriber for the Elapsed event.</span></span>

### <span data-ttu-id="d1258-122">Exempel 2: Använd den dynamiska modulen i PSEventJob i egenskapen Action för händelse prenumeranten</span><span class="sxs-lookup"><span data-stu-id="d1258-122">Example 2: Use the dynamic module in PSEventJob in the Action property of the event subscriber</span></span>

```
PS C:\> $Timer = New-Object Timers.Timer
PS C:\> $Timer.Interval = 500
PS C:\> Register-ObjectEvent -InputObject $Timer -EventName Elapsed -SourceIdentifier Timer.Random -Action { $Random = Get-Random -Min 0 -Max 100 }

Id  Name           State      HasMoreData  Location  Command
--  ----           -----      -----------  --------  -------
3   Timer.Random   NotStarted False                  $Random = Get-Random ...

PS C:\> $Timer.Enabled = $True
PS C:\> $Subscriber = Get-EventSubscriber -SourceIdentifier Timer.Random
PS C:\> ($Subscriber.action).gettype().fullname
System.Management.Automation.PSEventJob
PS C:\> $Subscriber.action | Format-List -Property *

State         : Running
Module        : __DynamicModule_6b5cbe82-d634-41d1-ae5e-ad7fe8d57fe0
StatusMessage :
HasMoreData   : True
Location      :
Command       : $random = Get-Random -Min 0 -Max 100
JobStateInfo  : Running
Finished      : System.Threading.ManualResetEvent
InstanceId    : 88944290-133d-4b44-8752-f901bd8012e2
Id            : 1
Name          : Timer.Random
ChildJobs     : {}
...

PS C:\> & $Subscriber.action.module {$Random}
96
PS C:\> & $Subscriber.action.module {$Random}
23
```

<span data-ttu-id="d1258-123">Det här exemplet visar hur du använder den dynamiska modulen i **PSEventJob** -objektet i egenskapen Action för händelse prenumeranten.</span><span class="sxs-lookup"><span data-stu-id="d1258-123">This example shows how to use the dynamic module in the **PSEventJob** object in the Action property of the event subscriber.</span></span>

<span data-ttu-id="d1258-124">Det första kommandot använder cmdleten New-Object för att skapa ett Timer-objekt.</span><span class="sxs-lookup"><span data-stu-id="d1258-124">The first command uses the New-Object cmdlet to create a timer object.</span></span>
<span data-ttu-id="d1258-125">Det andra kommandot anger intervallet för timer till 500 (millisekunder).</span><span class="sxs-lookup"><span data-stu-id="d1258-125">The second command sets the interval of the timer to 500 (milliseconds).</span></span>

<span data-ttu-id="d1258-126">Det tredje kommandot använder Register-ObjectEvent-cmdleten för att registrera den förflutna händelsen för objektet timer.</span><span class="sxs-lookup"><span data-stu-id="d1258-126">The third command uses the Register-ObjectEvent cmdlet to register the Elapsed event of the timer object.</span></span>
<span data-ttu-id="d1258-127">Kommandot innehåller en åtgärd som hanterar händelsen.</span><span class="sxs-lookup"><span data-stu-id="d1258-127">The command includes an action that handles the event.</span></span>
<span data-ttu-id="d1258-128">När tidsintervallet förflyter, utlöses en händelse och kommandona i åtgärden körs.</span><span class="sxs-lookup"><span data-stu-id="d1258-128">Whenever the timer interval elapses, an event is raised and the commands in the action run.</span></span>
<span data-ttu-id="d1258-129">I det här fallet genererar Get-Random-cmdleten ett slumpmässigt nummer mellan 0 och 100 och sparar det i variabeln $Random.</span><span class="sxs-lookup"><span data-stu-id="d1258-129">In this case, the Get-Random cmdlet generates a random number between 0 and 100 and saves it in the $Random variable.</span></span>
<span data-ttu-id="d1258-130">Händelsens käll-ID är timer. Random.</span><span class="sxs-lookup"><span data-stu-id="d1258-130">The source identifier of the event is Timer.Random.</span></span>

<span data-ttu-id="d1258-131">När du använder en *Åtgärds* parameter i ett **register-ObjectEvent** -kommando returnerar kommandot ett **PSEventJob** -objekt som representerar åtgärden.</span><span class="sxs-lookup"><span data-stu-id="d1258-131">When you use an *Action* parameter in a **Register-ObjectEvent** command, the command returns a **PSEventJob** object that represents the action.</span></span>

<span data-ttu-id="d1258-132">Det fjärde kommandot aktiverar timern.</span><span class="sxs-lookup"><span data-stu-id="d1258-132">The fourth command enables the timer.</span></span>

<span data-ttu-id="d1258-133">Det femte kommandot använder cmdleten **Get-EventSubscriber** för att hämta händelse prenumeranten för timern. slumpmässig händelse.</span><span class="sxs-lookup"><span data-stu-id="d1258-133">The fifth command uses the **Get-EventSubscriber** cmdlet to get the event subscriber of the Timer.Random event.</span></span>
<span data-ttu-id="d1258-134">Objektet för händelse prenumerationer sparas i variabeln $Subscriber.</span><span class="sxs-lookup"><span data-stu-id="d1258-134">It saves the event subscriber object in the $Subscriber variable.</span></span>

<span data-ttu-id="d1258-135">Det sjätte kommandot visar att egenskapen Action för Event Subscriber-objektet innehåller ett **PSEventJob** -objekt.</span><span class="sxs-lookup"><span data-stu-id="d1258-135">The sixth command shows that the Action property of the event subscriber object contains a **PSEventJob** object.</span></span>
<span data-ttu-id="d1258-136">I själva verket innehåller det samma **PSEventJob** -objekt som kommandot **register-ObjectEvent** returnerade.</span><span class="sxs-lookup"><span data-stu-id="d1258-136">In fact, it contains the same **PSEventJob** object that the **Register-ObjectEvent** command returned.</span></span>

<span data-ttu-id="d1258-137">Det sjunde kommandot använder Format-List-cmdleten för att visa alla egenskaper för **PSEventJob** -objektet i åtgärds egenskapen i en lista.</span><span class="sxs-lookup"><span data-stu-id="d1258-137">The seventh command uses the Format-List cmdlet to display all of the properties of the **PSEventJob** object in the Action property in a list.</span></span>
<span data-ttu-id="d1258-138">Resultatet visar att **PSEventJob** -objektet har en modul-egenskap som innehåller en dynamisk skript-modul som implementerar åtgärden.</span><span class="sxs-lookup"><span data-stu-id="d1258-138">The result reveals that the **PSEventJob** object has a Module property that contains a dynamic script module that implements the action.</span></span>

<span data-ttu-id="d1258-139">Återstående kommandon använder anrops operatorn (&) för att anropa kommandot i modulen och Visa värdet för $Random-variabeln.</span><span class="sxs-lookup"><span data-stu-id="d1258-139">The remaining commands use the call operator (&) to invoke the command in the module and display the value of the $Random variable.</span></span>
<span data-ttu-id="d1258-140">Du kan använda anrops operatorn för att anropa alla kommandon i en modul, inklusive kommandon som inte exporteras.</span><span class="sxs-lookup"><span data-stu-id="d1258-140">You can use the call operator to invoke any command in a module, including commands that are not exported.</span></span>
<span data-ttu-id="d1258-141">I det här fallet visar kommandona det slumpmässiga talet som genereras när den förflutna händelsen inträffar.</span><span class="sxs-lookup"><span data-stu-id="d1258-141">In this case, the commands show the random number that is being generated when the Elapsed event occurs.</span></span>

<span data-ttu-id="d1258-142">Mer information om moduler finns i [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).</span><span class="sxs-lookup"><span data-stu-id="d1258-142">For more information about modules, see [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).</span></span>

## <span data-ttu-id="d1258-143">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="d1258-143">PARAMETERS</span></span>

### <span data-ttu-id="d1258-144">-Force</span><span class="sxs-lookup"><span data-stu-id="d1258-144">-Force</span></span>

<span data-ttu-id="d1258-145">Anger att denna cmdlet hämtar alla händelse prenumeranter, inklusive prenumeranter av händelser som är dolda med hjälp av parametern *SupportEvent* i register-ObjectEvent, register-WmiEvent och register-EngineEvent.</span><span class="sxs-lookup"><span data-stu-id="d1258-145">Indicates that this cmdlet gets all event subscribers, including subscribers for events that are hidden by using the *SupportEvent* parameter of Register-ObjectEvent, Register-WmiEvent, and Register-EngineEvent.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="d1258-146">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="d1258-146">-SourceIdentifier</span></span>

<span data-ttu-id="d1258-147">Anger egenskap svärdet för **SourceIdentifier** som endast hämtar händelse prenumeranter.</span><span class="sxs-lookup"><span data-stu-id="d1258-147">Specifies the **SourceIdentifier** property value that gets only the event subscribers.</span></span>
<span data-ttu-id="d1258-148">Som standard hämtar **Get-EventSubscriber** alla händelse prenumeranter i sessionen.</span><span class="sxs-lookup"><span data-stu-id="d1258-148">By default, **Get-EventSubscriber** gets all event subscribers in the session.</span></span>
<span data-ttu-id="d1258-149">Jokertecken är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="d1258-149">Wildcards are not permitted.</span></span>
<span data-ttu-id="d1258-150">Den här parametern är Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="d1258-150">This parameter is case-sensitive.</span></span>

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

### <span data-ttu-id="d1258-151">-SubscriptionId</span><span class="sxs-lookup"><span data-stu-id="d1258-151">-SubscriptionId</span></span>

<span data-ttu-id="d1258-152">Anger prenumerations-ID: n som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="d1258-152">Specifies the subscription identifier that this cmdlet gets.</span></span>
<span data-ttu-id="d1258-153">Som standard hämtar **Get-EventSubscriber** alla händelse prenumeranter i sessionen.</span><span class="sxs-lookup"><span data-stu-id="d1258-153">By default, **Get-EventSubscriber** gets all event subscribers in the session.</span></span>

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

### <span data-ttu-id="d1258-154">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d1258-154">CommonParameters</span></span>

<span data-ttu-id="d1258-155">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="d1258-155">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="d1258-156">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="d1258-156">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="d1258-157">INDATA</span><span class="sxs-lookup"><span data-stu-id="d1258-157">INPUTS</span></span>

### <span data-ttu-id="d1258-158">Inget</span><span class="sxs-lookup"><span data-stu-id="d1258-158">None</span></span>

<span data-ttu-id="d1258-159">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d1258-159">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="d1258-160">UTDATA</span><span class="sxs-lookup"><span data-stu-id="d1258-160">OUTPUTS</span></span>

### <span data-ttu-id="d1258-161">System. Management. Automation. PSEventSubscriber</span><span class="sxs-lookup"><span data-stu-id="d1258-161">System.Management.Automation.PSEventSubscriber</span></span>

<span data-ttu-id="d1258-162">**Get-EventSubscriber** returnerar ett objekt som representerar varje händelse prenumerant.</span><span class="sxs-lookup"><span data-stu-id="d1258-162">**Get-EventSubscriber** returns an object that represents each event subscriber.</span></span>

## <span data-ttu-id="d1258-163">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="d1258-163">NOTES</span></span>

* <span data-ttu-id="d1258-164">New-Event-cmdleten, som skapar en anpassad händelse, genererar ingen prenumerant.</span><span class="sxs-lookup"><span data-stu-id="d1258-164">The New-Event cmdlet, which creates a custom event, does not generate a subscriber.</span></span> <span data-ttu-id="d1258-165">Därför kommer **Get-EventSubscriber** -cmdlet: en inte hitta ett Subscriber-objekt för dessa händelser.</span><span class="sxs-lookup"><span data-stu-id="d1258-165">Therefore, the **Get-EventSubscriber** cmdlet will not find a subscriber object for these events.</span></span> <span data-ttu-id="d1258-166">Om du använder Register-EngineEvent-cmdlet: en för att prenumerera på en anpassad händelse (för att vidarebefordra händelsen eller för att ange en åtgärd), kommer **Get-EventSubscriber** att hitta den prenumerant som **Registrera-EngineEvent** genererar.</span><span class="sxs-lookup"><span data-stu-id="d1258-166">However, if you use the Register-EngineEvent cmdlet to subscribe to a custom event (in order to forward the event or to specify an action), **Get-EventSubscriber** will find the subscriber that **Register-EngineEvent** generates.</span></span>

  <span data-ttu-id="d1258-167">Händelser, händelse prenumerationer och händelse kön finns bara i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="d1258-167">Events, event subscriptions, and the event queue exist only in the current session.</span></span>
<span data-ttu-id="d1258-168">Om du stänger den aktuella sessionen ignoreras händelse kön och händelse prenumerationen avbryts.</span><span class="sxs-lookup"><span data-stu-id="d1258-168">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

*

## <span data-ttu-id="d1258-169">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="d1258-169">RELATED LINKS</span></span>

[<span data-ttu-id="d1258-170">Hämta händelse</span><span class="sxs-lookup"><span data-stu-id="d1258-170">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="d1258-171">Ny händelse</span><span class="sxs-lookup"><span data-stu-id="d1258-171">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="d1258-172">Registrera – EngineEvent</span><span class="sxs-lookup"><span data-stu-id="d1258-172">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="d1258-173">Registrera – ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="d1258-173">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="d1258-174">Ta bort händelse</span><span class="sxs-lookup"><span data-stu-id="d1258-174">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="d1258-175">Avregistrera-händelse</span><span class="sxs-lookup"><span data-stu-id="d1258-175">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="d1258-176">Vänta-händelse</span><span class="sxs-lookup"><span data-stu-id="d1258-176">Wait-Event</span></span>](Wait-Event.md)
