---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 07/30/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/register-wmievent?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register-WmiEvent
ms.openlocfilehash: be29ce6376dea7686c0c063cc5528fbc7d840a9d
ms.sourcegitcommit: 41b072f0b6046d619b0e7f758982783fb648a3d5
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/31/2020
ms.locfileid: "93268821"
---
# <span data-ttu-id="44a87-103">Register-WmiEvent</span><span class="sxs-lookup"><span data-stu-id="44a87-103">Register-WmiEvent</span></span>

## <span data-ttu-id="44a87-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="44a87-104">SYNOPSIS</span></span>
<span data-ttu-id="44a87-105">Prenumererar på en Windows Management Instrumentation (WMI)-händelse.</span><span class="sxs-lookup"><span data-stu-id="44a87-105">Subscribes to a Windows Management Instrumentation (WMI) event.</span></span>

## <span data-ttu-id="44a87-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="44a87-106">SYNTAX</span></span>

### <span data-ttu-id="44a87-107">klass (standard)</span><span class="sxs-lookup"><span data-stu-id="44a87-107">class (Default)</span></span>

```
Register-WmiEvent [-Namespace <String>] [-Credential <PSCredential>] [-ComputerName <String>] [-Class] <String>
 [-Timeout <Int64>] [[-SourceIdentifier] <String>] [[-Action] <ScriptBlock>] [-MessageData <PSObject>]
 [-SupportEvent] [-Forward] [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

### <span data-ttu-id="44a87-108">DocumentDB</span><span class="sxs-lookup"><span data-stu-id="44a87-108">query</span></span>

```
Register-WmiEvent [-Namespace <String>] [-Credential <PSCredential>] [-ComputerName <String>] [-Query] <String>
 [-Timeout <Int64>] [[-SourceIdentifier] <String>] [[-Action] <ScriptBlock>] [-MessageData <PSObject>]
 [-SupportEvent] [-Forward] [-MaxTriggerCount <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="44a87-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="44a87-109">DESCRIPTION</span></span>

<span data-ttu-id="44a87-110">`Register-WmiEvent`Cmdleten prenumererar på Windows Management Instrumentation (WMI)-händelser på den lokala datorn eller på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="44a87-110">The `Register-WmiEvent` cmdlet subscribes to Windows Management Instrumentation (WMI) events on the local computer or on a remote computer.</span></span>

<span data-ttu-id="44a87-111">När den prenumererade WMI-händelsen höjs, läggs den till i händelse kön i din lokala session även om händelsen inträffar på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="44a87-111">When the subscribed WMI event is raised, it is added to the event queue in your local session even if the event occurs on a remote computer.</span></span> <span data-ttu-id="44a87-112">Använd cmdleten för att hämta händelser i händelse kön `Get-Event` .</span><span class="sxs-lookup"><span data-stu-id="44a87-112">To get events in the event queue, use the `Get-Event` cmdlet.</span></span>

<span data-ttu-id="44a87-113">Du kan använda parametrarna för `Register-WmiEvent` för att prenumerera på händelser på fjärrdatorer och ange egenskaps värden för de händelser som kan hjälpa dig att identifiera händelsen i kön.</span><span class="sxs-lookup"><span data-stu-id="44a87-113">You can use the parameters of `Register-WmiEvent` to subscribe to events on remote computers and to specify the property values of the events that can help you identify the event in the queue.</span></span> <span data-ttu-id="44a87-114">Du kan också använda **Åtgärds** parametern för att ange åtgärder som ska vidtas när en prenumeration aktive ras.</span><span class="sxs-lookup"><span data-stu-id="44a87-114">You can also use the **Action** parameter to specify actions to take when a subscribed event is raised.</span></span>

<span data-ttu-id="44a87-115">När du prenumererar på en händelse läggs en händelse prenumerant till i sessionen.</span><span class="sxs-lookup"><span data-stu-id="44a87-115">When you subscribe to an event, an event subscriber is added to your session.</span></span> <span data-ttu-id="44a87-116">Använd cmdleten för att hämta händelse prenumeranterna i sessionen `Get-EventSubscriber` .</span><span class="sxs-lookup"><span data-stu-id="44a87-116">To get the event subscribers in the session, use the `Get-EventSubscriber` cmdlet.</span></span> <span data-ttu-id="44a87-117">Om du vill avbryta prenumerationen använder du `Unregister-Event` cmdleten, som tar bort händelse prenumeranten från sessionen.</span><span class="sxs-lookup"><span data-stu-id="44a87-117">To cancel the subscription, use the `Unregister-Event` cmdlet, which deletes the event subscriber from the session.</span></span>

<span data-ttu-id="44a87-118">Nya Common Information Model-cmdlet: ar, introducerade Windows PowerShell 3,0, utför samma uppgifter som WMI-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="44a87-118">New Common Information Model (CIM) cmdlets, introduced Windows PowerShell 3.0, perform the same tasks as the WMI cmdlets.</span></span> <span data-ttu-id="44a87-119">CIM-cmdlets följer WS-Management (WSMan)-standarder och med CIM-standarden, som gör att cmdlets kan använda samma metoder för att hantera datorer som kör Windows-operativsystemet och de som kör andra operativ system.</span><span class="sxs-lookup"><span data-stu-id="44a87-119">The CIM cmdlets comply with WS-Management (WSMan) standards and with the CIM standard, which enables the cmdlets to use the same techniques to manage computers that run the Windows operating system and those that run other operating systems.</span></span> <span data-ttu-id="44a87-120">I stället för att använda bör `Register-WmiEvent` du överväga att använda cmdleten [register-CimIndicationEvent](../cimcmdlets/register-cimindicationevent.md) .</span><span class="sxs-lookup"><span data-stu-id="44a87-120">Instead of using `Register-WmiEvent`, consider using the [Register-CimIndicationEvent](../cimcmdlets/register-cimindicationevent.md) cmdlet.</span></span>

## <span data-ttu-id="44a87-121">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="44a87-121">EXAMPLES</span></span>

### <span data-ttu-id="44a87-122">Exempel 1: prenumerera på händelser som genererats av en klass</span><span class="sxs-lookup"><span data-stu-id="44a87-122">Example 1: Subscribe to events generated by a class</span></span>

<span data-ttu-id="44a87-123">Det här kommandot prenumererar på händelser som genererats av klassen **Win32_ProcessStartTrace** .</span><span class="sxs-lookup"><span data-stu-id="44a87-123">This command subscribes to the events generated by the **Win32_ProcessStartTrace** class.</span></span> <span data-ttu-id="44a87-124">Den här klassen aktiverar en händelse när en process startar.</span><span class="sxs-lookup"><span data-stu-id="44a87-124">This class raises an event whenever a process starts.</span></span>

```powershell
Register-WmiEvent -Class 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted"
```

### <span data-ttu-id="44a87-125">Exempel 2: prenumerera på skapande händelser för en process</span><span class="sxs-lookup"><span data-stu-id="44a87-125">Example 2: Subscribe to creation events for a process</span></span>

<span data-ttu-id="44a87-126">Det här kommandot använder en fråga för att prenumerera på händelser för Win32_process instans skapande.</span><span class="sxs-lookup"><span data-stu-id="44a87-126">This command uses a query to subscribe to Win32_process instance creation events.</span></span>

```powershell
$wmiParameters = @{
  Query = "select * from __instancecreationevent within 5 where targetinstance isa 'win32_process'"
  SourceIdentifier = "WMIProcess"
  MessageData = "Test 01"
  TimeOut = 500
}
Register-WmiEvent @wmiParameters
```

### <span data-ttu-id="44a87-127">Exempel 3: Använd en åtgärd för att svara på en händelse</span><span class="sxs-lookup"><span data-stu-id="44a87-127">Example 3: Use an action to respond to an event</span></span>

<span data-ttu-id="44a87-128">Det här exemplet visar hur du använder en åtgärd för att svara på en händelse.</span><span class="sxs-lookup"><span data-stu-id="44a87-128">This example shows how to use an action to respond to an event.</span></span> <span data-ttu-id="44a87-129">I det här fallet `Start-Process` skrivs alla kommandon i den aktuella sessionen till en XML-fil när en process startar.</span><span class="sxs-lookup"><span data-stu-id="44a87-129">In this case, when a process starts, any `Start-Process` commands in the current session are written to an XML file.</span></span>

```powershell
$action = { Get-History | where { $_.commandline -like "*start-process*" } | export-cliXml "commandHistory.clixml" }
Register-WmiEvent -Class 'Win32_ProcessStartTrace' -SourceIdentifier "ProcessStarted" -Action $action
```

```Output
Id    Name            State      HasMoreData   Location  Command
--    ----            -----      -----------   --------  -------
1     ProcessStarted  NotStarted False                   get-history | where {...
```

<span data-ttu-id="44a87-130">När du använder **Åtgärds** parametern, `Register-WmiEvent` returnerar ett bakgrunds jobb som representerar händelse åtgärden.</span><span class="sxs-lookup"><span data-stu-id="44a87-130">When you use the **Action** parameter, `Register-WmiEvent` returns a background job that represents the event action.</span></span> <span data-ttu-id="44a87-131">Du kan använda **jobb** -cmdletar, till exempel `Get-Job` och `Receive-Job` , för att hantera händelse jobbet.</span><span class="sxs-lookup"><span data-stu-id="44a87-131">You can use the **Job** cmdlets, such as `Get-Job` and `Receive-Job`, to manage the event job.</span></span>

<span data-ttu-id="44a87-132">Mer information finns i artikeln om jobb.</span><span class="sxs-lookup"><span data-stu-id="44a87-132">For more information, see about_Jobs.</span></span>

### <span data-ttu-id="44a87-133">Exempel 4: registrera dig för händelser på en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="44a87-133">Example 4: Register for events on a remote computer</span></span>

<span data-ttu-id="44a87-134">Det här exemplet registrerar händelser på fjärrdatorn Server01.</span><span class="sxs-lookup"><span data-stu-id="44a87-134">This example registers for events on the Server01 remote computer.</span></span>

```powershell
Register-WmiEvent -Class 'Win32_ProcessStartTrace' -SourceIdentifier "Start" -Computername Server01
Get-Event -SourceIdentifier "Start"
```

<span data-ttu-id="44a87-135">WMI returnerar händelserna till den lokala datorn och lagrar dem i händelse kön i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="44a87-135">WMI returns the events to the local computer and stores them in the event queue in the current session.</span></span> <span data-ttu-id="44a87-136">Hämta händelserna genom att köra ett lokalt `Get-Event` kommando.</span><span class="sxs-lookup"><span data-stu-id="44a87-136">To retrieve the events, run a local `Get-Event` command.</span></span>

## <span data-ttu-id="44a87-137">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="44a87-137">PARAMETERS</span></span>

### <span data-ttu-id="44a87-138">-Åtgärd</span><span class="sxs-lookup"><span data-stu-id="44a87-138">-Action</span></span>

<span data-ttu-id="44a87-139">Anger kommandon som hanterar händelser.</span><span class="sxs-lookup"><span data-stu-id="44a87-139">Specifies commands that handle the events.</span></span> <span data-ttu-id="44a87-140">Kommandona i **Åtgärds** parametern körs när en händelse höjs i stället för att skicka händelsen till händelse kön.</span><span class="sxs-lookup"><span data-stu-id="44a87-140">The commands in the **Action** parameter run when an event is raised instead of sending the event to the event queue.</span></span> <span data-ttu-id="44a87-141">Omge kommandoen med klammerparenteser ( `{}` ) för att skapa ett skript block.</span><span class="sxs-lookup"><span data-stu-id="44a87-141">Enclose the commands in braces (`{}`) to create a script block.</span></span>

<span data-ttu-id="44a87-142">Värdet för **åtgärden** kan omfatta `$Event` `$EventSubscriber` variablerna,, `$Sender` , `$EventArgs` och för `$Args` Automatiska variabler, som innehåller information om händelsen till **Åtgärds** skript blocket.</span><span class="sxs-lookup"><span data-stu-id="44a87-142">The value of **Action** can include the `$Event`, `$EventSubscriber`, `$Sender`, `$EventArgs`, and `$Args` automatic variables, which provide information about the event to the **Action** script block.</span></span> <span data-ttu-id="44a87-143">Mer information finns i about_Automatic_Variables.</span><span class="sxs-lookup"><span data-stu-id="44a87-143">For more information, see about_Automatic_Variables.</span></span>

<span data-ttu-id="44a87-144">När du anger en åtgärd `Register-WmiEvent` returnerar ett händelse jobb objekt som representerar den åtgärden.</span><span class="sxs-lookup"><span data-stu-id="44a87-144">When you specify an action, `Register-WmiEvent` returns an event job object that represents that action.</span></span> <span data-ttu-id="44a87-145">Du kan använda de cmdlet: ar som innehåller **jobbet** Substantiv ( **jobb** -cmdletar) för att hantera händelse jobbet.</span><span class="sxs-lookup"><span data-stu-id="44a87-145">You can use the cmdlets that contain the **Job** noun (the **Job** cmdlets) to manage the event job.</span></span>

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

### <span data-ttu-id="44a87-146">– Klass</span><span class="sxs-lookup"><span data-stu-id="44a87-146">-Class</span></span>

<span data-ttu-id="44a87-147">Anger händelsen som du prenumererar på.</span><span class="sxs-lookup"><span data-stu-id="44a87-147">Specifies the event to which you are subscribing.</span></span> <span data-ttu-id="44a87-148">Ange den WMI-klass som genererar händelserna.</span><span class="sxs-lookup"><span data-stu-id="44a87-148">Enter the WMI class that generates the events.</span></span> <span data-ttu-id="44a87-149">Det krävs en **klass** -eller **frågeparameter** -parameter i varje kommando.</span><span class="sxs-lookup"><span data-stu-id="44a87-149">A **Class** or **Query** parameter is required in every command.</span></span>

```yaml
Type: System.String
Parameter Sets: class
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="44a87-150">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="44a87-150">-ComputerName</span></span>

<span data-ttu-id="44a87-151">Anger namnet på den dator där kommandot körs.</span><span class="sxs-lookup"><span data-stu-id="44a87-151">Specifies the name of the computer on which the command runs.</span></span> <span data-ttu-id="44a87-152">Standard är den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="44a87-152">The default is the local computer.</span></span>

<span data-ttu-id="44a87-153">Ange NetBIOS-namn, en IP-adress eller ett fullständigt kvalificerat domän namn för datorn.</span><span class="sxs-lookup"><span data-stu-id="44a87-153">Type the NetBIOS name, an IP address, or a fully qualified domain name of the computer.</span></span> <span data-ttu-id="44a87-154">Om du vill ange den lokala datorn skriver du datorns namn, en punkt ( `.` ) eller localhost.</span><span class="sxs-lookup"><span data-stu-id="44a87-154">To specify the local computer, type the computer name, a dot (`.`), or localhost.</span></span>

<span data-ttu-id="44a87-155">Den här parametern är inte beroende av Windows PowerShell-fjärrkommunikation.</span><span class="sxs-lookup"><span data-stu-id="44a87-155">This parameter does not rely on Windows PowerShell remoting.</span></span> <span data-ttu-id="44a87-156">Du kan använda parametern **computername** även om datorn inte är konfigurerad för att köra fjärrkommandon.</span><span class="sxs-lookup"><span data-stu-id="44a87-156">You can use the **ComputerName** parameter even if your computer is not configured to run remote commands.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Cn

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="44a87-157">-Credential</span><span class="sxs-lookup"><span data-stu-id="44a87-157">-Credential</span></span>

<span data-ttu-id="44a87-158">Anger ett användar konto som har behörighet att utföra den här åtgärden.</span><span class="sxs-lookup"><span data-stu-id="44a87-158">Specifies a user account that has permission to perform this action.</span></span> <span data-ttu-id="44a87-159">Standard är den aktuella användaren.</span><span class="sxs-lookup"><span data-stu-id="44a87-159">The default is the current user.</span></span>

<span data-ttu-id="44a87-160">Ange ett användar namn, till exempel user01 eller Domain01\User01, eller ange ett **PSCredential** -objekt, t. ex. ett som genererades av `Get-Credential` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="44a87-160">Type a user name, such as User01 or Domain01\User01, or enter a **PSCredential** object, such as one generated by the `Get-Credential` cmdlet.</span></span> <span data-ttu-id="44a87-161">Om du anger ett användar namn uppmanas du att ange ett lösen ord i den här cmdleten.</span><span class="sxs-lookup"><span data-stu-id="44a87-161">If you type a user name, this cmdlet prompts you for a password.</span></span>

```yaml
Type: System.Management.Automation.PSCredential
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="44a87-162">-Forward</span><span class="sxs-lookup"><span data-stu-id="44a87-162">-Forward</span></span>

<span data-ttu-id="44a87-163">Anger att denna cmdlet skickar händelser för den här prenumerationen till sessionen på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="44a87-163">Indicates that this cmdlet sends events for this subscription to the session on the local computer.</span></span>
<span data-ttu-id="44a87-164">Använd den här parametern när du registrerar händelser på en fjärrdator eller i en fjärran sluten session.</span><span class="sxs-lookup"><span data-stu-id="44a87-164">Use this parameter when you are registering for events on a remote computer or in a remote session.</span></span>

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

### <span data-ttu-id="44a87-165">-MaxTriggerCount</span><span class="sxs-lookup"><span data-stu-id="44a87-165">-MaxTriggerCount</span></span>

<span data-ttu-id="44a87-166">Anger maximalt antal utlösare.</span><span class="sxs-lookup"><span data-stu-id="44a87-166">Specifies the maximum trigger count.</span></span>

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

### <span data-ttu-id="44a87-167">-MessageData</span><span class="sxs-lookup"><span data-stu-id="44a87-167">-MessageData</span></span>

<span data-ttu-id="44a87-168">Anger eventuella ytterligare data som ska associeras med den här händelse prenumerationen.</span><span class="sxs-lookup"><span data-stu-id="44a87-168">Specifies any additional data to be associated with this event subscription.</span></span> <span data-ttu-id="44a87-169">Värdet för den här parametern visas i egenskapen **MessageData** för alla händelser som är associerade med den här prenumerationen.</span><span class="sxs-lookup"><span data-stu-id="44a87-169">The value of this parameter appears in the **MessageData** property of all events associated with this subscription.</span></span>

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

### <span data-ttu-id="44a87-170">– Namnrymd</span><span class="sxs-lookup"><span data-stu-id="44a87-170">-Namespace</span></span>

<span data-ttu-id="44a87-171">Anger namn området för WMI-klassen.</span><span class="sxs-lookup"><span data-stu-id="44a87-171">Specifies the namespace of the WMI class.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: NS

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="44a87-172">– Fråga</span><span class="sxs-lookup"><span data-stu-id="44a87-172">-Query</span></span>

<span data-ttu-id="44a87-173">Anger en fråga i WMI Query Language (WQL) som identifierar händelse klassen WMI, t `select * from __InstanceDeletionEvent` . ex.:.</span><span class="sxs-lookup"><span data-stu-id="44a87-173">Specifies a query in WMI Query Language (WQL) that identifies the WMI event class, such as: `select * from __InstanceDeletionEvent`.</span></span>

```yaml
Type: System.String
Parameter Sets: query
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="44a87-174">-SourceIdentifier</span><span class="sxs-lookup"><span data-stu-id="44a87-174">-SourceIdentifier</span></span>

<span data-ttu-id="44a87-175">Anger ett namn som du väljer för prenumerationen.</span><span class="sxs-lookup"><span data-stu-id="44a87-175">Specifies a name that you select for the subscription.</span></span> <span data-ttu-id="44a87-176">Det namn du väljer måste vara unikt i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="44a87-176">The name that you select must be unique in the current session.</span></span> <span data-ttu-id="44a87-177">Standardvärdet är det GUID som Windows PowerShell tilldelar.</span><span class="sxs-lookup"><span data-stu-id="44a87-177">The default value is the GUID that Windows PowerShell assigns.</span></span>

<span data-ttu-id="44a87-178">Värdet för den här parametern visas i värdet för egenskapen **SourceIdentifier** för Subscriber-objektet och för alla händelse objekt som är associerade med den här prenumerationen.</span><span class="sxs-lookup"><span data-stu-id="44a87-178">The value of this parameter appears in the value of the **SourceIdentifier** property of the subscriber object and of all event objects associated with this subscription.</span></span>

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

### <span data-ttu-id="44a87-179">-SupportEvent</span><span class="sxs-lookup"><span data-stu-id="44a87-179">-SupportEvent</span></span>

<span data-ttu-id="44a87-180">Anger att denna cmdlet döljer händelse prenumerationen.</span><span class="sxs-lookup"><span data-stu-id="44a87-180">Indicates that this cmdlet hides the event subscription.</span></span> <span data-ttu-id="44a87-181">Använd den här parametern när den aktuella prenumerationen är en del av en mer komplex metod för registrering av händelser och den bör inte identifieras separat.</span><span class="sxs-lookup"><span data-stu-id="44a87-181">Use this parameter when the current subscription is part of a more complex event registration mechanism and it should not be discovered independently.</span></span>

<span data-ttu-id="44a87-182">Om du vill visa eller avbryta en prenumeration som har skapats med hjälp av parametern **SupportEvent** anger du **Force** -parametern `Get-EventSubscriber` för `Unregister-Event` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="44a87-182">To view or cancel a subscription that was created by using the **SupportEvent** parameter, specify the **Force** parameter of the `Get-EventSubscriber` and `Unregister-Event` cmdlets.</span></span>

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

### <span data-ttu-id="44a87-183">-Timeout</span><span class="sxs-lookup"><span data-stu-id="44a87-183">-Timeout</span></span>

<span data-ttu-id="44a87-184">Anger hur lång tid Windows PowerShell väntar på att kommandot ska slutföras.</span><span class="sxs-lookup"><span data-stu-id="44a87-184">Specifies how long Windows PowerShell waits for this command to finish.</span></span>

<span data-ttu-id="44a87-185">Standardvärdet, 0 (noll), innebär att det inte finns någon tids gräns och det gör att Windows PowerShell väntar oändligt.</span><span class="sxs-lookup"><span data-stu-id="44a87-185">The default value, 0 (zero), means that there is no time-out, and it causes Windows PowerShell to wait indefinitely.</span></span>

```yaml
Type: System.Int64
Parameter Sets: (All)
Aliases: TimeoutMSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="44a87-186">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="44a87-186">CommonParameters</span></span>

<span data-ttu-id="44a87-187">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="44a87-187">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="44a87-188">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="44a87-188">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="44a87-189">INDATA</span><span class="sxs-lookup"><span data-stu-id="44a87-189">INPUTS</span></span>

### <span data-ttu-id="44a87-190">Inget</span><span class="sxs-lookup"><span data-stu-id="44a87-190">None</span></span>

<span data-ttu-id="44a87-191">Det går inte att skicka pipe-objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="44a87-191">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="44a87-192">UTDATA</span><span class="sxs-lookup"><span data-stu-id="44a87-192">OUTPUTS</span></span>

### <span data-ttu-id="44a87-193">Inget</span><span class="sxs-lookup"><span data-stu-id="44a87-193">None</span></span>

<span data-ttu-id="44a87-194">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="44a87-194">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="44a87-195">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="44a87-195">NOTES</span></span>

<span data-ttu-id="44a87-196">Om du vill använda den här cmdleten i Windows Vista eller en senare version av operativ systemet Windows startar du Windows PowerShell med alternativet Kör som administratör.</span><span class="sxs-lookup"><span data-stu-id="44a87-196">To use this cmdlet in Windows Vista or a later version of the Windows operating system, start Windows PowerShell by using the Run as administrator option.</span></span>

<span data-ttu-id="44a87-197">Händelser, händelse prenumerationer och händelse kön finns bara i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="44a87-197">Events, event subscriptions, and the event queue exist only in the current session.</span></span> <span data-ttu-id="44a87-198">Om du stänger den aktuella sessionen ignoreras händelse kön och händelse prenumerationen avbryts.</span><span class="sxs-lookup"><span data-stu-id="44a87-198">If you close the current session, the event queue is discarded and the event subscription is canceled.</span></span>

## <span data-ttu-id="44a87-199">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="44a87-199">RELATED LINKS</span></span>
