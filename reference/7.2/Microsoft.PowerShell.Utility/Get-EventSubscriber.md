---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-eventsubscriber?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-EventSubscriber
ms.openlocfilehash: b8f55770770fa9077f654d382818386cc480c638
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709768"
---
# <span data-ttu-id="dcc03-102">Get-EventSubscriber</span><span class="sxs-lookup"><span data-stu-id="dcc03-102">Get-EventSubscriber</span></span>

## <span data-ttu-id="dcc03-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="dcc03-103">SYNOPSIS</span></span>
<span data-ttu-id="dcc03-104">Hämtar händelse prenumeranterna i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="dcc03-104">Gets the event subscribers in the current session.</span></span>

## <span data-ttu-id="dcc03-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="dcc03-105">SYNTAX</span></span>

### <span data-ttu-id="dcc03-106">BySource (standard)</span><span class="sxs-lookup"><span data-stu-id="dcc03-106">BySource (Default)</span></span>

```
Get-EventSubscriber [[-SourceIdentifier] <String>] [-Force] [<CommonParameters>]
```

### <span data-ttu-id="dcc03-107">ById</span><span class="sxs-lookup"><span data-stu-id="dcc03-107">ById</span></span>

```
Get-EventSubscriber [-SubscriptionId] <Int32> [-Force] [<CommonParameters>]
```

## <span data-ttu-id="dcc03-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="dcc03-108">DESCRIPTION</span></span>

<span data-ttu-id="dcc03-109">**Get-EventSubscriber** -cmdlet: en hämtar händelse prenumeranterna i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="dcc03-109">The **Get-EventSubscriber** cmdlet gets the event subscribers in the current session.</span></span>

<span data-ttu-id="dcc03-110">När du prenumererar på en händelse genom att använda en register händelse-cmdlet läggs en händelse prenumerant till i din PowerShell-session och de händelser som du har prenumererat på läggs till i händelse kön när de utlöses.</span><span class="sxs-lookup"><span data-stu-id="dcc03-110">When you subscribe to an event by using a Register event cmdlet, an event subscriber is added to your PowerShell session, and the events to which you subscribed are added to your event queue whenever they are raised.</span></span>
<span data-ttu-id="dcc03-111">Om du vill avbryta en händelse prenumeration tar du bort händelse prenumeranten med hjälp av Unregister-Event-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="dcc03-111">To cancel an event subscription, delete the event subscriber by using the Unregister-Event cmdlet.</span></span>

## <span data-ttu-id="dcc03-112">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="dcc03-112">EXAMPLES</span></span>

### <span data-ttu-id="dcc03-113">Exempel 1: Hämta händelse prenumeranten för en timer-händelse</span><span class="sxs-lookup"><span data-stu-id="dcc03-113">Example 1: Get the event subscriber for a timer event</span></span>

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

<span data-ttu-id="dcc03-114">I det här exemplet används kommandot **Get-EventSubscriber** för att hämta händelse prenumeranten för en timer-händelse.</span><span class="sxs-lookup"><span data-stu-id="dcc03-114">This example uses a **Get-EventSubscriber** command to get the event subscriber for a timer event.</span></span>

<span data-ttu-id="dcc03-115">Det första kommandot använder cmdleten New-Object för att skapa en instans av ett Timer-objekt.</span><span class="sxs-lookup"><span data-stu-id="dcc03-115">The first command uses the New-Object cmdlet to create an instance of a timer object.</span></span>
<span data-ttu-id="dcc03-116">Det sparar det nya timer-objektet i $Timer-variabeln.</span><span class="sxs-lookup"><span data-stu-id="dcc03-116">It saves the new timer object in the $Timer variable.</span></span>

<span data-ttu-id="dcc03-117">Det andra kommandot använder cmdleten Get-Member för att visa de händelser som är tillgängliga för Timer-objekt.</span><span class="sxs-lookup"><span data-stu-id="dcc03-117">The second command uses the Get-Member cmdlet to display the events that are available for timer objects.</span></span>
<span data-ttu-id="dcc03-118">Kommandot använder typ parametern för cmdleten **Get-Member** med värdet event.</span><span class="sxs-lookup"><span data-stu-id="dcc03-118">The command uses the Type parameter of the **Get-Member** cmdlet with a value of Event.</span></span>

<span data-ttu-id="dcc03-119">Det tredje kommandot använder Register-ObjectEvent-cmdleten för att registrera för den förflutna händelsen för det tidsinställda objektet.</span><span class="sxs-lookup"><span data-stu-id="dcc03-119">The third command uses the Register-ObjectEvent cmdlet to register for the Elapsed event on the timer object.</span></span>

<span data-ttu-id="dcc03-120">Det fjärde kommandot använder cmdleten **Get-EventSubscriber** för att hämta händelse prenumeranten för den förflutna händelsen.</span><span class="sxs-lookup"><span data-stu-id="dcc03-120">The fourth command uses the **Get-EventSubscriber** cmdlet to get the event subscriber for the Elapsed event.</span></span>

### <span data-ttu-id="dcc03-121">Exempel 2: Använd den dynamiska modulen i PSEventJob i egenskapen Action för händelse prenumeranten</span><span class="sxs-lookup"><span data-stu-id="dcc03-121">Example 2: Use the dynamic module in PSEventJob in the Action property of the event subscriber</span></span>

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

<span data-ttu-id="dcc03-122">Det här exemplet visar hur du använder den dynamiska modulen i **PSEventJob** -objektet i egenskapen Action för händelse prenumeranten.</span><span class="sxs-lookup"><span data-stu-id="dcc03-122">This example shows how to use the dynamic module in the **PSEventJob** object in the Action property of the event subscriber.</span></span>

<span data-ttu-id="dcc03-123">Det första kommandot använder cmdleten New-Object för att skapa ett Timer-objekt.</span><span class="sxs-lookup"><span data-stu-id="dcc03-123">The first command uses the New-Object cmdlet to create a timer object.</span></span>
<span data-ttu-id="dcc03-124">Det andra kommandot anger intervallet för timer till 500 (millisekunder).</span><span class="sxs-lookup"><span data-stu-id="dcc03-124">The second command sets the interval of the timer to 500 (milliseconds).</span></span>

<span data-ttu-id="dcc03-125">Det tredje kommandot använder Register-ObjectEvent-cmdleten för att registrera den förflutna händelsen för objektet timer.</span><span class="sxs-lookup"><span data-stu-id="dcc03-125">The third command uses the Register-ObjectEvent cmdlet to register the Elapsed event of the timer object.</span></span>
<span data-ttu-id="dcc03-126">Kommandot innehåller en åtgärd som hanterar händelsen.</span><span class="sxs-lookup"><span data-stu-id="dcc03-126">The command includes an action that handles the event.</span></span>
<span data-ttu-id="dcc03-127">När tidsintervallet förflyter, utlöses en händelse och kommandona i åtgärden körs.</span><span class="sxs-lookup"><span data-stu-id="dcc03-127">Whenever the timer interval elapses, an event is raised and the commands in the action run.</span></span>
<span data-ttu-id="dcc03-128">I det här fallet genererar Get-Random-cmdleten ett slumpmässigt nummer mellan 0 och 100 och sparar det i variabeln $Random.</span><span class="sxs-lookup"><span data-stu-id="dcc03-128">In this case, the Get-Random cmdlet generates a random number between 0 and 100 and saves it in the $Random variable.</span></span>
<span data-ttu-id="dcc03-129">Händelsens käll-ID är timer. Random.</span><span class="sxs-lookup"><span data-stu-id="dcc03-129">The source identifier of the event is Timer.Random.</span></span>

<span data-ttu-id="dcc03-130">När du använder en *Åtgärds* parameter i ett **register-ObjectEvent** -kommando returnerar kommandot ett **PSEventJob** -objekt som representerar åtgärden.</span><span class="sxs-lookup"><span data-stu-id="dcc03-130">When you use an *Action* parameter in a **Register-ObjectEvent** command, the command returns a **PSEventJob** object that represents the action.</span></span>

<span data-ttu-id="dcc03-131">Det fjärde kommandot aktiverar timern.</span><span class="sxs-lookup"><span data-stu-id="dcc03-131">The fourth command enables the timer.</span></span>

<span data-ttu-id="dcc03-132">Det femte kommandot använder cmdleten **Get-EventSubscriber** för att hämta händelse prenumeranten för timern. slumpmässig händelse.</span><span class="sxs-lookup"><span data-stu-id="dcc03-132">The fifth command uses the **Get-EventSubscriber** cmdlet to get the event subscriber of the Timer.Random event.</span></span>
<span data-ttu-id="dcc03-133">Objektet för händelse prenumerationer sparas i variabeln $Subscriber.</span><span class="sxs-lookup"><span data-stu-id="dcc03-133">It saves the event subscriber object in the $Subscriber variable.</span></span>

<span data-ttu-id="dcc03-134">Det sjätte kommandot visar att egenskapen Action för Event Subscriber-objektet innehåller ett **PSEventJob** -objekt.</span><span class="sxs-lookup"><span data-stu-id="dcc03-134">The sixth command shows that the Action property of the event subscriber object contains a **PSEventJob** object.</span></span>
<span data-ttu-id="dcc03-135">I själva verket innehåller det samma **PSEventJob** -objekt som kommandot **register-ObjectEvent** returnerade.</span><span class="sxs-lookup"><span data-stu-id="dcc03-135">In fact, it contains the same **PSEventJob** object that the **Register-ObjectEvent** command returned.</span></span>

<span data-ttu-id="dcc03-136">Det sjunde kommandot använder Format-List-cmdleten för att visa alla egenskaper för **PSEventJob** -objektet i åtgärds egenskapen i en lista.</span><span class="sxs-lookup"><span data-stu-id="dcc03-136">The seventh command uses the Format-List cmdlet to display all of the properties of the **PSEventJob** object in the Action property in a list.</span></span>
<span data-ttu-id="dcc03-137">Resultatet visar att **PSEventJob** -objektet har en modul-egenskap som innehåller en dynamisk skript-modul som implementerar åtgärden.</span><span class="sxs-lookup"><span data-stu-id="dcc03-137">The result reveals that the **PSEventJob** object has a Module property that contains a dynamic script module that implements the action.</span></span>

<span data-ttu-id="dcc03-138">Återstående kommandon använder anrops operatorn (&) för att anropa kommandot i modulen och Visa värdet för $Random-variabeln.</span><span class="sxs-lookup"><span data-stu-id="dcc03-138">The remaining commands use the call operator (&) to invoke the command in the module and display the value of the $Random variable.</span></span>
<span data-ttu-id="dcc03-139">Du kan använda anrops operatorn för att anropa alla kommandon i en modul, inklusive kommandon som inte exporteras.</span><span class="sxs-lookup"><span data-stu-id="dcc03-139">You can use the call operator to invoke any command in a module, including commands that are not exported.</span></span>
<span data-ttu-id="dcc03-140">I det här fallet visar kommandona det slumpmässiga talet som genereras när den förflutna händelsen inträffar.</span><span class="sxs-lookup"><span data-stu-id="dcc03-140">In this case, the commands show the random number that is being generated when the Elapsed event occurs.</span></span>

<span data-ttu-id="dcc03-141">Mer information om moduler finns i [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).</span><span class="sxs-lookup"><span data-stu-id="dcc03-141">For more information about modules, see [about_Modules](../Microsoft.PowerShell.Core/About/about_Modules.md).</span></span>

## <span data-ttu-id="dcc03-142">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="dcc03-142">PARAMETERS</span></span>

### <span data-ttu-id="dcc03-143">-Force</span><span class="sxs-lookup"><span data-stu-id="dcc03-143">-Force</span></span>

<span data-ttu-id="dcc03-144">Anger att denna cmdlet hämtar alla händelse prenumeranter, inklusive prenumeranter av händelser som är dolda med hjälp av parametern *SupportEvent* i register-ObjectEvent, register-WmiEvent och register-EngineEvent.</span><span class="sxs-lookup"><span data-stu-id="dcc03-144">Indicates that this cmdlet gets all event subscribers, including subscribers for events that are hidden by using the *SupportEvent* parameter of Register-ObjectEvent, Register-WmiEvent, and Register-EngineEvent.</span></span>

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

### <span data-ttu-id="dcc03-145">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="dcc03-145">-SourceIdentifier</span></span>

<span data-ttu-id="dcc03-146">Anger egenskap svärdet för **SourceIdentifier** som endast hämtar händelse prenumeranter.</span><span class="sxs-lookup"><span data-stu-id="dcc03-146">Specifies the **SourceIdentifier** property value that gets only the event subscribers.</span></span>
<span data-ttu-id="dcc03-147">Som standard hämtar **Get-EventSubscriber** alla händelse prenumeranter i sessionen.</span><span class="sxs-lookup"><span data-stu-id="dcc03-147">By default, **Get-EventSubscriber** gets all event subscribers in the session.</span></span>
<span data-ttu-id="dcc03-148">Jokertecken är inte tillåtna.</span><span class="sxs-lookup"><span data-stu-id="dcc03-148">Wildcards are not permitted.</span></span>
<span data-ttu-id="dcc03-149">Den här parametern är Skift läges känslig.</span><span class="sxs-lookup"><span data-stu-id="dcc03-149">This parameter is case-sensitive.</span></span>

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

### <span data-ttu-id="dcc03-150">-SubscriptionId</span><span class="sxs-lookup"><span data-stu-id="dcc03-150">-SubscriptionId</span></span>

<span data-ttu-id="dcc03-151">Anger prenumerations-ID: n som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="dcc03-151">Specifies the subscription identifier that this cmdlet gets.</span></span>
<span data-ttu-id="dcc03-152">Som standard hämtar **Get-EventSubscriber** alla händelse prenumeranter i sessionen.</span><span class="sxs-lookup"><span data-stu-id="dcc03-152">By default, **Get-EventSubscriber** gets all event subscribers in the session.</span></span>

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

### <span data-ttu-id="dcc03-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="dcc03-153">CommonParameters</span></span>

<span data-ttu-id="dcc03-154">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="dcc03-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="dcc03-155">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="dcc03-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="dcc03-156">INDATA</span><span class="sxs-lookup"><span data-stu-id="dcc03-156">INPUTS</span></span>

### <span data-ttu-id="dcc03-157">Inga</span><span class="sxs-lookup"><span data-stu-id="dcc03-157">None</span></span>

<span data-ttu-id="dcc03-158">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dcc03-158">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="dcc03-159">UTDATA</span><span class="sxs-lookup"><span data-stu-id="dcc03-159">OUTPUTS</span></span>

### <span data-ttu-id="dcc03-160">System. Management. Automation. PSEventSubscriber</span><span class="sxs-lookup"><span data-stu-id="dcc03-160">System.Management.Automation.PSEventSubscriber</span></span>

<span data-ttu-id="dcc03-161">**Get-EventSubscriber** returnerar ett objekt som representerar varje händelse prenumerant.</span><span class="sxs-lookup"><span data-stu-id="dcc03-161">**Get-EventSubscriber** returns an object that represents each event subscriber.</span></span>

## <span data-ttu-id="dcc03-162">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="dcc03-162">NOTES</span></span>

* <span data-ttu-id="dcc03-163">New-Event-cmdleten, som skapar en anpassad händelse, genererar ingen prenumerant.</span><span class="sxs-lookup"><span data-stu-id="dcc03-163">The New-Event cmdlet, which creates a custom event, does not generate a subscriber.</span></span> <span data-ttu-id="dcc03-164">Därför kommer **Get-EventSubscriber** -cmdlet: en inte hitta ett Subscriber-objekt för dessa händelser.</span><span class="sxs-lookup"><span data-stu-id="dcc03-164">Therefore, the **Get-EventSubscriber** cmdlet will not find a subscriber object for these events.</span></span> <span data-ttu-id="dcc03-165">Om du använder Register-EngineEvent-cmdlet: en för att prenumerera på en anpassad händelse (för att vidarebefordra händelsen eller för att ange en åtgärd), kommer **Get-EventSubscriber** att hitta den prenumerant som **Registrera-EngineEvent** genererar.</span><span class="sxs-lookup"><span data-stu-id="dcc03-165">However, if you use the Register-EngineEvent cmdlet to subscribe to a custom event (in order to forward the event or to specify an action), **Get-EventSubscriber** will find the subscriber that **Register-EngineEvent** generates.</span></span>

  <span data-ttu-id="dcc03-166">Händelser, händelse prenumerationer och händelse kön finns bara i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="dcc03-166">Events, event subscriptions, and the event queue exist only in the current session.</span></span>
<span data-ttu-id="dcc03-167">Om du stänger den aktuella sessionen ignoreras händelse kön och händelse prenumerationen avbryts.</span><span class="sxs-lookup"><span data-stu-id="dcc03-167">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

*

## <span data-ttu-id="dcc03-168">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="dcc03-168">RELATED LINKS</span></span>

[<span data-ttu-id="dcc03-169">Hämta händelse</span><span class="sxs-lookup"><span data-stu-id="dcc03-169">Get-Event</span></span>](Get-Event.md)

[<span data-ttu-id="dcc03-170">Ny händelse</span><span class="sxs-lookup"><span data-stu-id="dcc03-170">New-Event</span></span>](New-Event.md)

[<span data-ttu-id="dcc03-171">Registrera – EngineEvent</span><span class="sxs-lookup"><span data-stu-id="dcc03-171">Register-EngineEvent</span></span>](Register-EngineEvent.md)

[<span data-ttu-id="dcc03-172">Registrera – ObjectEvent</span><span class="sxs-lookup"><span data-stu-id="dcc03-172">Register-ObjectEvent</span></span>](Register-ObjectEvent.md)

[<span data-ttu-id="dcc03-173">Ta bort händelse</span><span class="sxs-lookup"><span data-stu-id="dcc03-173">Remove-Event</span></span>](Remove-Event.md)

[<span data-ttu-id="dcc03-174">Avregistrera-händelse</span><span class="sxs-lookup"><span data-stu-id="dcc03-174">Unregister-Event</span></span>](Unregister-Event.md)

[<span data-ttu-id="dcc03-175">Vänta-händelse</span><span class="sxs-lookup"><span data-stu-id="dcc03-175">Wait-Event</span></span>](Wait-Event.md)

