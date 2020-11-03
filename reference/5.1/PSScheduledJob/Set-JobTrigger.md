---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/set-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-JobTrigger
ms.openlocfilehash: 8d1b12b67ccf695e1c4b948e6eeecf292c588af4
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264627"
---
# <span data-ttu-id="5d93e-103">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="5d93e-103">Set-JobTrigger</span></span>

## <span data-ttu-id="5d93e-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="5d93e-104">SYNOPSIS</span></span>
<span data-ttu-id="5d93e-105">Ändrar jobb utlösaren för ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="5d93e-105">Changes the job trigger of a scheduled job.</span></span>

## <span data-ttu-id="5d93e-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5d93e-106">SYNTAX</span></span>

```
Set-JobTrigger [-InputObject] <ScheduledJobTrigger[]> [-DaysInterval <Int32>] [-WeeksInterval <Int32>]
 [-RandomDelay <TimeSpan>] [-At <DateTime>] [-User <String>] [-DaysOfWeek <DayOfWeek[]>] [-AtStartup]
 [-AtLogOn] [-Once] [-RepetitionInterval <TimeSpan>] [-RepetitionDuration <TimeSpan>] [-RepeatIndefinitely]
 [-Daily] [-Weekly] [-PassThru] [<CommonParameters>]
```

## <span data-ttu-id="5d93e-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="5d93e-107">DESCRIPTION</span></span>
<span data-ttu-id="5d93e-108">Cmdlet **: en Set-JobTrigger** ändrar egenskaperna för jobb utlösare för schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="5d93e-108">The **Set-JobTrigger** cmdlet changes the properties of the job triggers of scheduled jobs.</span></span>
<span data-ttu-id="5d93e-109">Du kan använda den för att ändra tid eller frekvens då jobben startar eller ändras från tidsbaserade scheman till scheman som utlöses av en inloggning eller start.</span><span class="sxs-lookup"><span data-stu-id="5d93e-109">You can use it to change the time or frequency at which the jobs start or to change from a time-based schedules to schedules that are triggered by a logon or startup.</span></span>

<span data-ttu-id="5d93e-110">En jobb utlösare definierar ett återkommande schema eller villkor för att starta ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="5d93e-110">A job trigger defines a recurring schedule or conditions for starting a scheduled job.</span></span>
<span data-ttu-id="5d93e-111">Även om jobb utlösare inte sparas på disk, kan du ändra jobb utlösare för schemalagda jobb som sparas till disk.</span><span class="sxs-lookup"><span data-stu-id="5d93e-111">Although job triggers are not saved to disk, you can change the job triggers of scheduled jobs, which are saved to disk.</span></span>

<span data-ttu-id="5d93e-112">Om du vill ändra en jobb utlösare för ett schemalagt jobb börjar du med att använda Get-JobTrigger-cmdlet för att hämta jobb utlösaren för ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="5d93e-112">To change a job trigger of a scheduled job, begin by using the Get-JobTrigger cmdlet to get the job trigger of a scheduled job.</span></span>
<span data-ttu-id="5d93e-113">Skicka sedan utlösaren till **set-JobTrigger** eller spara utlösaren i en variabel och Använd *InputObject* -parametern för cmdleten **set-JobTrigger** för att identifiera utlösaren.</span><span class="sxs-lookup"><span data-stu-id="5d93e-113">Then, pipe the trigger to **Set-JobTrigger** or save the trigger in a variable and use the *InputObject* parameter of **Set-JobTrigger** cmdlet to identify the trigger.</span></span>
<span data-ttu-id="5d93e-114">Använd de återstående parametrarna för **set-JobTrigger** för att ändra jobb utlösaren.</span><span class="sxs-lookup"><span data-stu-id="5d93e-114">Use the remaining parameters of **Set-JobTrigger** to change the job trigger.</span></span>

<span data-ttu-id="5d93e-115">När du ändrar typen för en jobb utlösare, t. ex. ändrar en jobb utlösare från en daglig eller veckovis utlösare till en *AtLogon* -utlösare, tas de ursprungliga utlösarens egenskaper bort.</span><span class="sxs-lookup"><span data-stu-id="5d93e-115">When you change the type of a job trigger, such as changing a job trigger from a daily or weekly trigger to an *AtLogon* trigger, the original trigger properties are deleted.</span></span>
<span data-ttu-id="5d93e-116">Men om du ändrar värdena för utlösaren, men inte dess typ, t. ex. om du ändrar dagar i en veckovis utlösare, ändras bara de egenskaper som du anger.</span><span class="sxs-lookup"><span data-stu-id="5d93e-116">However, if you change the values of the trigger, but not its type, such as changing the days in a weekly trigger, only the properties that you specify are changed.</span></span>
<span data-ttu-id="5d93e-117">Alla andra egenskaper för den ursprungliga jobb utlösaren behålls.</span><span class="sxs-lookup"><span data-stu-id="5d93e-117">All other properties of the original job trigger are retained.</span></span>

<span data-ttu-id="5d93e-118">**Set-JobTrigger** är en samling jobb schemaläggnings-cmdletar i PSScheduledJob-modulen som ingår i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5d93e-118">**Set-JobTrigger** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="5d93e-119">Mer information om schemalagda jobb finns i avsnittet om ämnen i PSScheduledJob-modulen.</span><span class="sxs-lookup"><span data-stu-id="5d93e-119">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="5d93e-120">Importera modulen PSScheduledJob och skriv sedan: `Get-Help about_Scheduled*`  eller se about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="5d93e-120">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*`  or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="5d93e-121">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="5d93e-121">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="5d93e-122">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="5d93e-122">EXAMPLES</span></span>

### <span data-ttu-id="5d93e-123">Exempel 1: ändra antalet dagar i en jobb utlösare</span><span class="sxs-lookup"><span data-stu-id="5d93e-123">Example 1: Change the days in a job trigger</span></span>

```
PS C:\> Get-JobTrigger -Name "DeployPackage"
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Weekly          9/29/2011 12:00:00 AM  {Wednesday, Saturday}   True

The second command uses the Get-JobTrigger cmdlet to get the job trigger of the DeployPackage scheduled job. A pipeline operator (|) sends the trigger to the **Set-JobTrigger** cmdlet, which changes the job trigger so that it starts the DeployPackage job on Wednesdays and Sundays. The command uses the *Passthru* parameter to return the trigger after the change.
PS C:\> Get-JobTrigger -Name "DeployPackage" | Set-JobTrigger -DaysOfWeek "Wednesday", "Sunday" -Passthru
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Weekly          9/29/2011 12:00:00 AM  {Wednesday, Sunday}     True
```

<span data-ttu-id="5d93e-124">Det här exemplet visar hur du ändrar antalet dagar i en veckovis jobb utlösare.</span><span class="sxs-lookup"><span data-stu-id="5d93e-124">This example shows how to change the days in a weekly job trigger.</span></span>

<span data-ttu-id="5d93e-125">Det första kommandot använder Get-JobTrigger-cmdlet för att hämta jobb utlösaren för det schemalagda DeployPackage-jobbet.</span><span class="sxs-lookup"><span data-stu-id="5d93e-125">The first command uses the Get-JobTrigger cmdlet to get the job trigger of the DeployPackage scheduled job.</span></span>
<span data-ttu-id="5d93e-126">Resultatet visar att utlösaren startar jobbet vid midnatt på onsdagar och lördagar.</span><span class="sxs-lookup"><span data-stu-id="5d93e-126">The output shows that the trigger starts the job at midnight on Wednesdays and Saturdays.</span></span>

<span data-ttu-id="5d93e-127">Det här kommandot krävs inte. den ingår endast för att Visa effekterna av utlösnings ändringen.</span><span class="sxs-lookup"><span data-stu-id="5d93e-127">This command is not required; it is included only to show the effect of the trigger change.</span></span>

### <span data-ttu-id="5d93e-128">Exempel 2: Ändra jobb utlösnings typen</span><span class="sxs-lookup"><span data-stu-id="5d93e-128">Example 2: Change the job trigger type</span></span>

```
PS C:\> Get-JobTrigger -Name "Inventory"
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Daily           9/27/2011 11:00:00 PM                          True
2          AtStartup                                                      True

The second command uses the **Get-JobTrigger** cmdlet to get the *AtStartup* job trigger of the Inventory job. The command uses the *TriggerID* parameter to identify the job trigger. A pipeline operator (|) sends the job trigger to the **Set-JobTrigger** cmdlet, which changes it to a weekly job trigger that runs every four weeks on Monday at midnight. The command uses the *Passthru* parameter to return the trigger after the change.
PS C:\> Get-JobTrigger -Name "Inventory" -TriggerID 2 | Set-JobTrigger -Weekly -WeeksInterval 4 -DaysOfWeek Monday -At "12:00 AM"
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Daily           9/27/2011 11:00:00 PM                          True
2          Weekly          10/31/2011 12:00:00 AM {Monday}                True
```

<span data-ttu-id="5d93e-129">Det här exemplet visar hur du ändrar vilken typ av jobb utlösare som startar ett jobb.</span><span class="sxs-lookup"><span data-stu-id="5d93e-129">This example shows how to change the type of job trigger that starts a job.</span></span>
<span data-ttu-id="5d93e-130">Kommandona i det här exemplet ersätter en utlösare för AtStartup-jobb med en veckovis utlösare.</span><span class="sxs-lookup"><span data-stu-id="5d93e-130">The commands in this example replace an AtStartup job trigger with a weekly trigger.</span></span>

<span data-ttu-id="5d93e-131">Det första kommandot använder Get-JobTrigger-cmdlet för att hämta jobb utlösaren för det schemalagda jobbet för lager.</span><span class="sxs-lookup"><span data-stu-id="5d93e-131">The first command uses the Get-JobTrigger cmdlet to get the job trigger of the Inventory scheduled job.</span></span>
<span data-ttu-id="5d93e-132">Utdata visar att jobbet har två utlösare en daglig utlösare och en *AtStartup* -utlösare.</span><span class="sxs-lookup"><span data-stu-id="5d93e-132">The output shows that the job has two triggers a daily trigger and an *AtStartup* trigger.</span></span>

<span data-ttu-id="5d93e-133">Det här kommandot krävs inte. den ingår endast för att Visa effekterna av utlösnings ändringen.</span><span class="sxs-lookup"><span data-stu-id="5d93e-133">This command is not required; it is included only to show the effect of the trigger change.</span></span>

### <span data-ttu-id="5d93e-134">Exempel 3: ändra användaren på en utlösare för Fjärrjobb</span><span class="sxs-lookup"><span data-stu-id="5d93e-134">Example 3: Change the user on a remote job trigger</span></span>

```
PS C:\> Invoke-Command -ComputerName "Server01" -ScriptBlock {Get-ScheduledJob | Get-JobTrigger | Where-Object {$_.User} | Set-JobTrigger -User "Domain01/Admin02"}
```

<span data-ttu-id="5d93e-135">Det här kommandot ändrar användaren i alla *AtLogon* jobb-utlösare för schemalagda jobb på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="5d93e-135">This command changes the user in all *AtLogon* job triggers of scheduled jobs on the Server01 computer.</span></span>

<span data-ttu-id="5d93e-136">Kommandot använder cmdleten Invoke-Command för att köra ett kommando på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="5d93e-136">The command uses the Invoke-Command cmdlet to run a command on the Server01 computer.</span></span>

<span data-ttu-id="5d93e-137">Fjärrkommandot börjar med ett Get-ScheduledJob-kommando som hämtar alla schemalagda jobb på datorn.</span><span class="sxs-lookup"><span data-stu-id="5d93e-137">The remote command begins with a Get-ScheduledJob command that gets all scheduled jobs on the computer.</span></span>
<span data-ttu-id="5d93e-138">De schemalagda jobben är skickas till Get-JobTrigger-cmdleten, som hämtar jobb utlösarna för de schemalagda jobben.</span><span class="sxs-lookup"><span data-stu-id="5d93e-138">The scheduled jobs are piped to the Get-JobTrigger cmdlet, which gets the job triggers of the scheduled jobs.</span></span>
<span data-ttu-id="5d93e-139">Varje jobb utlösare innehåller en jobb definitionen-egenskap som innehåller det schemalagda jobbet, så utlösaren förblir kopplad till det schemalagda jobbet även om den ändras.</span><span class="sxs-lookup"><span data-stu-id="5d93e-139">Each job trigger contains a JobDefinition property that contains the scheduled job, so the trigger remains associated with the scheduled job even when it is changed.</span></span>

<span data-ttu-id="5d93e-140">Jobb utlösarna är skickas till Where-Object-cmdleten, som hämtar jobb utlösare som har egenskapen User.</span><span class="sxs-lookup"><span data-stu-id="5d93e-140">The job triggers are piped to the Where-Object cmdlet, which gets job triggers that have the User property.</span></span>
<span data-ttu-id="5d93e-141">De valda jobb utlösarna är skickas till cmdleten **set-JobTrigger** , som ändrar användaren till Domain01\Admin02.</span><span class="sxs-lookup"><span data-stu-id="5d93e-141">The selected job triggers are piped to the **Set-JobTrigger** cmdlet, which changes the user to Domain01\Admin02.</span></span>

### <span data-ttu-id="5d93e-142">Exempel 4: ändra en av många jobb utlösare</span><span class="sxs-lookup"><span data-stu-id="5d93e-142">Example 4: Change one of many job triggers</span></span>

```
PS C:\> Get-JobTrigger -Name "SecurityCheck"
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
1          Daily           4/24/2013 3:00:00 AM                           True
2          Weekly          4/24/2013 4:00:00 PM   {Sunday}                True
3          Once            4/24/2013 4:00:00 PM                           True

The second command uses the **TriggerID** parameter of the **Get-JobTrigger** cmdlet to get the *Once* trigger of the SecurityCheck scheduled job. The command pipes the trigger to the Format-List cmdlet, which displays all of the properties of the *Once* job trigger.The output shows that the trigger starts the job once every hour (RepetitionInterval = 1 hour) for one day (RepetitionDuration = 1 day).
PS C:\> Get-JobTrigger -Name "SecurityCheck" -TriggerID 3 | Format-List -Property *
At                 : 4/24/2012 4:00:00 PM
DaysOfWeek         :
Interval           : 1
Frequency          : Once
RandomDelay        : 00:00:00
RepetitionInterval : 01:00:00
RepetitionDuration : 1.00:00:00
User               :
Id                 : 3
Enabled            : True
JobDefinition      : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition

The third command changes the repetition interval of the job trigger from one hour to 90 minutes. The command does not return any output.
PS C:\> Get-JobTrigger -Name "SecurityCheck" -TriggerId 3 | Set-JobTrigger -RepetitionInterval (New-TimeSpan -Minutes 90)

The fourth command displays the effect of the change.The output shows that the trigger starts the job once every 90 minutes (RepetitionInterval = 1 hour, 30 minutes) for one day (RepetitionDuration = 1 day).
PS C:\> Get-JobTrigger -Name "SecurityCheck" -TriggerID 3 | Format-List -Property *
At                 : 4/24/2012 4:00:00 PM
DaysOfWeek         :
Interval           : 1
Frequency          : Once
RandomDelay        : 00:00:00
RepetitionInterval : 01:30:00
RepetitionDuration : 1.00:00:00
User               :
Id                 : 3
Enabled            : True
JobDefinition      : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

<span data-ttu-id="5d93e-143">Kommandona i det här exemplet ändrar upprepnings intervallet för *en gång* jobb utlösare för SecurityCheck schemalagda jobb från var 60: e minut till var 90 minut.</span><span class="sxs-lookup"><span data-stu-id="5d93e-143">The commands in this example changes the repetition interval of the *Once* job trigger of SecurityCheck scheduled job from every 60 minutes to every 90 minutes.</span></span>
<span data-ttu-id="5d93e-144">Det schemalagda SecurityCheck-jobbet har tre jobb utlösare, så kommandona använder parametern *TriggerId* i Get-JobTrigger-cmdlet för att identifiera den jobb utlösare som ändras.</span><span class="sxs-lookup"><span data-stu-id="5d93e-144">The SecurityCheck scheduled job has three job triggers, so the commands use the *TriggerId* parameter of the Get-JobTrigger cmdlet to identify the job trigger that is being changed.</span></span>

<span data-ttu-id="5d93e-145">Det första kommandot använder cmdleten **Get-JobTrigger** för att hämta alla jobb utlösare för det schemalagda SecurityCheck-jobbet.</span><span class="sxs-lookup"><span data-stu-id="5d93e-145">The first command uses the **Get-JobTrigger** cmdlet to get all job triggers of the SecurityCheck scheduled job.</span></span>
<span data-ttu-id="5d93e-146">Utdata, som visar ID: n för jobb utlösare, visar att den *när* jobb utlösaren har ett ID på 3.</span><span class="sxs-lookup"><span data-stu-id="5d93e-146">The output, which displays the IDs of the job triggers, reveals that the *Once* job trigger has an ID of 3.</span></span>

## <span data-ttu-id="5d93e-147">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="5d93e-147">PARAMETERS</span></span>

### <span data-ttu-id="5d93e-148">– På</span><span class="sxs-lookup"><span data-stu-id="5d93e-148">-At</span></span>
<span data-ttu-id="5d93e-149">Startar jobbet vid angivet datum och tid.</span><span class="sxs-lookup"><span data-stu-id="5d93e-149">Starts the job at the specified date and time.</span></span>
<span data-ttu-id="5d93e-150">Ange ett **datetime** -objekt, till exempel ett som Get-Date cmdlet returnerar, eller en sträng som kan konverteras till en tid, till exempel "April 19, 2012 15:00", "12/31/2013 9:00 PM" eller "3am".</span><span class="sxs-lookup"><span data-stu-id="5d93e-150">Enter a **DateTime** object, such as one that the Get-Date cmdlet returns, or a string that can be converted to a time, such as "April 19, 2012 15:00", "12/31/2013 9:00 PM", or "3am".</span></span>

<span data-ttu-id="5d93e-151">Om du inte anger ett element i **datetime** -objektet, till exempel sekunder, ändras inte det element som ingår i jobb utlösaren.</span><span class="sxs-lookup"><span data-stu-id="5d93e-151">If you don't specify an element of the **DateTime** object, such as seconds, that element of the job trigger is not changed.</span></span>
<span data-ttu-id="5d93e-152">Om den ursprungliga jobb utlösaren inte innehåller ett **datetime** -objekt och du utelämnar ett element, skapas jobb utlösaren med motsvarande element från aktuellt datum och aktuell tid.</span><span class="sxs-lookup"><span data-stu-id="5d93e-152">If the original job trigger didn't include a **DateTime** object and you omit an element, the job trigger is created with the corresponding element from the current date and time.</span></span>

<span data-ttu-id="5d93e-153">När du använder parametern *Once* ställer du in värdet för parametern *at* på ett visst datum och en viss tid.</span><span class="sxs-lookup"><span data-stu-id="5d93e-153">When using the *Once* parameter, set the value of the *At* parameter to a particular date and time.</span></span>
<span data-ttu-id="5d93e-154">Eftersom standard datumet i ett **datetime** -objekt är det aktuella datumet, ställer du in en tid före den aktuella tiden utan ett explicit datum resulterar i en jobb utlösare för en tid i det förflutna.</span><span class="sxs-lookup"><span data-stu-id="5d93e-154">Because the default date in a **DateTime** object is the current date, setting a time before the current time without an explicit date results in a job trigger for a time in the past.</span></span>

<span data-ttu-id="5d93e-155">**Datetime** -objekt och strängar som konverteras till **datetime** -objekt justeras automatiskt så att de är kompatibla med de datum-och tids format som valts för den lokala datorn i region och språk på kontroll panelen.</span><span class="sxs-lookup"><span data-stu-id="5d93e-155">**DateTime** objects, and strings that are converted to **DateTime** objects, are automatically adjusted to be compatible with the date and time formats selected for the local computer in Region and Language in Control Panel.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5d93e-156">-AtLogOn</span><span class="sxs-lookup"><span data-stu-id="5d93e-156">-AtLogOn</span></span>
<span data-ttu-id="5d93e-157">Startar det schemalagda jobbet när de angivna användarna loggar in på datorn.</span><span class="sxs-lookup"><span data-stu-id="5d93e-157">Starts the scheduled job when the specified users log on to the computer.</span></span>
<span data-ttu-id="5d93e-158">Använd *användar* parametern för att ange en användare.</span><span class="sxs-lookup"><span data-stu-id="5d93e-158">To specify a user, use the *User* parameter.</span></span>

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

### <span data-ttu-id="5d93e-159">-AtStartup</span><span class="sxs-lookup"><span data-stu-id="5d93e-159">-AtStartup</span></span>
<span data-ttu-id="5d93e-160">Startar det schemalagda jobbet när Windows startas.</span><span class="sxs-lookup"><span data-stu-id="5d93e-160">Starts the scheduled job when Windows starts.</span></span>

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

### <span data-ttu-id="5d93e-161">– Varje dag</span><span class="sxs-lookup"><span data-stu-id="5d93e-161">-Daily</span></span>
<span data-ttu-id="5d93e-162">Anger ett återkommande schema för dagligt jobb.</span><span class="sxs-lookup"><span data-stu-id="5d93e-162">Specifies a recurring daily job schedule.</span></span>
<span data-ttu-id="5d93e-163">Använd de andra parametrarna i den *dagliga* parameter uppsättningen för att ange schema information.</span><span class="sxs-lookup"><span data-stu-id="5d93e-163">Use the other parameters in the *Daily* parameter set to specify the schedule details.</span></span>

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

### <span data-ttu-id="5d93e-164">-DaysInterval</span><span class="sxs-lookup"><span data-stu-id="5d93e-164">-DaysInterval</span></span>
<span data-ttu-id="5d93e-165">Anger antalet dagar mellan förekomster enligt ett dagligt schema.</span><span class="sxs-lookup"><span data-stu-id="5d93e-165">Specifies the number of days between occurrences on a daily schedule.</span></span>
<span data-ttu-id="5d93e-166">Värdet 3 startar till exempel det schemalagda jobbet på dagar 1, 4, 7 och så vidare.</span><span class="sxs-lookup"><span data-stu-id="5d93e-166">For example, a value of 3 starts the scheduled job on days 1, 4, 7 and so on.</span></span>
<span data-ttu-id="5d93e-167">Standardvärdet är 1.</span><span class="sxs-lookup"><span data-stu-id="5d93e-167">The default value is 1.</span></span>

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

### <span data-ttu-id="5d93e-168">-DaysOfWeek</span><span class="sxs-lookup"><span data-stu-id="5d93e-168">-DaysOfWeek</span></span>
<span data-ttu-id="5d93e-169">Anger vecko dagarna som ett schemalagt vecko jobb körs på.</span><span class="sxs-lookup"><span data-stu-id="5d93e-169">Specifies the days of the week on which a weekly scheduled job runs.</span></span>
<span data-ttu-id="5d93e-170">Ange dag namn, till exempel måndag, torsdag, heltal 0-6, där 0 representerar söndag eller en asterisk ( \* ) som representerar varje dag.</span><span class="sxs-lookup"><span data-stu-id="5d93e-170">Enter day names, such as Monday, Thursday, integers 0-6, where 0 represents Sunday, or an asterisk (\*) to represent every day.</span></span>
<span data-ttu-id="5d93e-171">Den här parametern krävs i den veckobaserade parameter uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="5d93e-171">This parameter is required in the Weekly parameter set.</span></span>

<span data-ttu-id="5d93e-172">Dag namn konverteras till deras heltals värden i jobb utlösaren.</span><span class="sxs-lookup"><span data-stu-id="5d93e-172">Day names are converted to their integer values in the job trigger.</span></span>
<span data-ttu-id="5d93e-173">När du omger dag namn inom citat tecken i ett kommando, omger du varje dag med separata citat tecken, till exempel "måndag", "tisdag".</span><span class="sxs-lookup"><span data-stu-id="5d93e-173">When you enclose day names in quotation marks in a command, enclose each day name in separate quotation marks, such as "Monday", "Tuesday".</span></span>
<span data-ttu-id="5d93e-174">Om du omger flera dag namn i ett enkelt citat tecken, summeras motsvarande heltals värden.</span><span class="sxs-lookup"><span data-stu-id="5d93e-174">If you enclose multiple day names in a single quotation mark pair, the corresponding integer values are summed.</span></span>
<span data-ttu-id="5d93e-175">Till exempel "måndag, tisdag" (1, 2) resulterar i värdet "onsdag" (3).</span><span class="sxs-lookup"><span data-stu-id="5d93e-175">For example, "Monday, Tuesday" (1, 2) results in a value of "Wednesday" (3).</span></span>

```yaml
Type: System.DayOfWeek[]
Parameter Sets: (All)
Aliases:
Accepted values: Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5d93e-176">– InputObject</span><span class="sxs-lookup"><span data-stu-id="5d93e-176">-InputObject</span></span>
<span data-ttu-id="5d93e-177">Anger jobb utlösare.</span><span class="sxs-lookup"><span data-stu-id="5d93e-177">Specifies the job triggers.</span></span>
<span data-ttu-id="5d93e-178">Ange en variabel som innehåller **ScheduledJobTrigger** -objekt eller Skriv ett kommando eller uttryck som hämtar **ScheduledJobTrigger** -objekt, till exempel ett Get-JobTrigger-kommando.</span><span class="sxs-lookup"><span data-stu-id="5d93e-178">Enter a variable that contains **ScheduledJobTrigger** objects or type a command or expression that gets **ScheduledJobTrigger** objects, such as a Get-JobTrigger command.</span></span>
<span data-ttu-id="5d93e-179">Du kan också skicka ett **ScheduledJobTrigger** -objekt till **set-JobTrigger**.</span><span class="sxs-lookup"><span data-stu-id="5d93e-179">You can also pipe a **ScheduledJobTrigger** object to **Set-JobTrigger**.</span></span>

<span data-ttu-id="5d93e-180">Om du anger flera jobb utlösare gör **set-JobTrigger** samma ändringar i alla jobb utlösare.</span><span class="sxs-lookup"><span data-stu-id="5d93e-180">If you specify multiple job triggers, **Set-JobTrigger** makes the same changes to all job triggers.</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="5d93e-181">– En gång</span><span class="sxs-lookup"><span data-stu-id="5d93e-181">-Once</span></span>
<span data-ttu-id="5d93e-182">Anger ett schema som inte är återkommande (en tid).</span><span class="sxs-lookup"><span data-stu-id="5d93e-182">Specifies a non-recurring (one time) schedule.</span></span>

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

### <span data-ttu-id="5d93e-183">– PassThru</span><span class="sxs-lookup"><span data-stu-id="5d93e-183">-PassThru</span></span>
<span data-ttu-id="5d93e-184">Returnerar de jobb utlösare som har ändrats.</span><span class="sxs-lookup"><span data-stu-id="5d93e-184">Returns the job triggers that changed.</span></span>
<span data-ttu-id="5d93e-185">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="5d93e-185">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="5d93e-186">-RandomDelay</span><span class="sxs-lookup"><span data-stu-id="5d93e-186">-RandomDelay</span></span>
<span data-ttu-id="5d93e-187">Aktiverar en slumpmässig fördröjning som börjar vid den schemalagda start tiden och anger högsta fördröjnings värde.</span><span class="sxs-lookup"><span data-stu-id="5d93e-187">Enables a random delay that begins at the scheduled start time, and sets the maximum delay value.</span></span>
<span data-ttu-id="5d93e-188">Längden på fördröjningen är att ställa in pseudo – slumpvis för varje start och varierar från ingen fördröjning till den tid som anges av värdet för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="5d93e-188">The length of the delay is set pseudo-randomly for each start and varies from no delay to the time specified by the value of this parameter.</span></span>
<span data-ttu-id="5d93e-189">Standardvärdet noll (00:00:00), inaktiverar slumpmässig fördröjning.</span><span class="sxs-lookup"><span data-stu-id="5d93e-189">The default value, zero (00:00:00), disables the random delay.</span></span>

<span data-ttu-id="5d93e-190">Ange ett TimeSpan-objekt, till exempel ett som returneras av New-TimeSpan-cmdleten, eller ange ett värde i \<hours\> : \<minutes\> : \<seconds\> format, som automatiskt konverteras till ett TimeSpan-objekt.</span><span class="sxs-lookup"><span data-stu-id="5d93e-190">Enter a timespan object, such as one returned by the New-TimeSpan cmdlet, or enter a value in \<hours\>:\<minutes\>:\<seconds\> format, which is automatically converted to a timespan object.</span></span>

```yaml
Type: System.TimeSpan
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5d93e-191">-RepeatIndefinitely</span><span class="sxs-lookup"><span data-stu-id="5d93e-191">-RepeatIndefinitely</span></span>
<span data-ttu-id="5d93e-192">Den här parametern, som är tillgänglig från och med Windows PowerShell 4,0, eliminerar behovet av att ange ett **TimeSpan. MaxValue** -värde för parametern *RepetitionDuration* för att köra ett schemalagt jobb upprepade gånger, under obestämd tid.</span><span class="sxs-lookup"><span data-stu-id="5d93e-192">This parameter, available starting in Windows PowerShell 4.0, eliminates the necessity of specifying a **TimeSpan.MaxValue** value for the *RepetitionDuration* parameter to run a scheduled job repeatedly, for an indefinite period.</span></span>

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

### <span data-ttu-id="5d93e-193">-RepetitionDuration</span><span class="sxs-lookup"><span data-stu-id="5d93e-193">-RepetitionDuration</span></span>
<span data-ttu-id="5d93e-194">Upprepar jobbet tills den angivna tiden upphör att gälla.</span><span class="sxs-lookup"><span data-stu-id="5d93e-194">Repeats the job until the specified time expires.</span></span>
<span data-ttu-id="5d93e-195">Upprepnings frekvensen bestäms av värdet för parametern *RepetitionInterval* .</span><span class="sxs-lookup"><span data-stu-id="5d93e-195">The repetition frequency is determined by the value of the *RepetitionInterval* parameter.</span></span>
<span data-ttu-id="5d93e-196">Om värdet för **RepetitionInterval** till exempel är 5 minuter och värdet för *RepetitionDuration* är 2 timmar utlöses jobbet var femte minut i två timmar.</span><span class="sxs-lookup"><span data-stu-id="5d93e-196">For example, if the value of **RepetitionInterval** is 5 minutes and the value of *RepetitionDuration* is 2 hours, the job is triggered every five minutes for two hours.</span></span>

<span data-ttu-id="5d93e-197">Ange ett TimeSpan-objekt, till exempel ett som New-TimeSpan cmdlet returnerar eller en sträng som kan konverteras till ett TimeSpan-objekt, till exempel "1:05:30".</span><span class="sxs-lookup"><span data-stu-id="5d93e-197">Enter a timespan object, such as one that the New-TimeSpan cmdlet returns or a string that can be converted to a timespan object, such as "1:05:30".</span></span>

<span data-ttu-id="5d93e-198">Om du vill köra ett jobb oändligt lägger du till parametern *RepeatIndefinitely* i stället.</span><span class="sxs-lookup"><span data-stu-id="5d93e-198">To run a job indefinitely, add the *RepeatIndefinitely* parameter instead.</span></span>

<span data-ttu-id="5d93e-199">Om du vill stoppa ett jobb innan jobbets repetitions varaktighet upphör att gälla, ställer du in värdet för **RepetitionDuration** på noll (0).</span><span class="sxs-lookup"><span data-stu-id="5d93e-199">To stop a job before the job trigger repetition duration expires, set the **RepetitionDuration** value to zero (0).</span></span>

<span data-ttu-id="5d93e-200">Om du vill ändra varaktigheten eller upprepnings intervallet för en *gång* jobb utlösare måste kommandot innehålla parametrarna **RepetitionInterval** och **RepetitionDuration** .</span><span class="sxs-lookup"><span data-stu-id="5d93e-200">To change the repetition duration or repetition interval of a *Once* job trigger, the command must include both the **RepetitionInterval** and **RepetitionDuration** parameters.</span></span>
<span data-ttu-id="5d93e-201">Om du vill ändra varaktighet eller upprepnings intervall för andra typer av jobb utlösare måste kommandot inkludera parametrarna *Once* , *at* , *RepetitionInterval* och *RepetitionDuration* .</span><span class="sxs-lookup"><span data-stu-id="5d93e-201">To change the repetition duration or repetition intervals of other types of job triggers, the command must include the *Once* , *At* , *RepetitionInterval* and *RepetitionDuration* parameters.</span></span>

```yaml
Type: System.TimeSpan
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5d93e-202">-RepetitionInterval</span><span class="sxs-lookup"><span data-stu-id="5d93e-202">-RepetitionInterval</span></span>
<span data-ttu-id="5d93e-203">Upprepar jobbet vid det angivna tidsintervallet.</span><span class="sxs-lookup"><span data-stu-id="5d93e-203">Repeats the job at the specified time interval.</span></span>
<span data-ttu-id="5d93e-204">Om värdet för den här parametern till exempel är 2 timmar utlöses jobbet varannan timme.</span><span class="sxs-lookup"><span data-stu-id="5d93e-204">For example, if the value of this parameter is 2 hours, the job is triggered every two hours.</span></span>
<span data-ttu-id="5d93e-205">Standardvärdet, 0, upprepar inte jobbet.</span><span class="sxs-lookup"><span data-stu-id="5d93e-205">The default value, 0, does not repeat the job.</span></span>

<span data-ttu-id="5d93e-206">Ange ett TimeSpan-objekt, till exempel ett som New-TimeSpan cmdlet returnerar eller en sträng som kan konverteras till ett TimeSpan-objekt, till exempel "1:05:30".</span><span class="sxs-lookup"><span data-stu-id="5d93e-206">Enter a timespan object, such as one that the New-TimeSpan cmdlet returns or a string that can be converted to a timespan object, such as "1:05:30".</span></span>

<span data-ttu-id="5d93e-207">Om du vill ändra varaktigheten eller upprepnings intervallet för en **gång** jobb utlösare måste kommandot innehålla parametrarna **RepetitionInterval** och **RepetitionDuration** .</span><span class="sxs-lookup"><span data-stu-id="5d93e-207">To change the repetition duration or repetition interval of a **Once** job trigger, the command must include both the **RepetitionInterval** and **RepetitionDuration** parameters.</span></span>
<span data-ttu-id="5d93e-208">Om du vill ändra varaktighet eller upprepnings intervall för andra typer av jobb utlösare måste kommandot inkludera parametrarna **Once** , **at** , **RepetitionInterval** och **RepetitionDuration** .</span><span class="sxs-lookup"><span data-stu-id="5d93e-208">To change the repetition duration or repetition intervals of other types of job triggers, the command must include the **Once** , **At** , **RepetitionInterval** and **RepetitionDuration** parameters.</span></span>

```yaml
Type: System.TimeSpan
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5d93e-209">-User</span><span class="sxs-lookup"><span data-stu-id="5d93e-209">-User</span></span>
<span data-ttu-id="5d93e-210">Anger de användare som utlöser en *AtLogon* början av ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="5d93e-210">Specifies the users who trigger an *AtLogon* start of a scheduled job.</span></span>
<span data-ttu-id="5d93e-211">Ange namnet på en användare i \<UserName\> eller \<Domain\Username\> formatera eller ange en asterisk ( \* ) för att representera alla användare.</span><span class="sxs-lookup"><span data-stu-id="5d93e-211">Enter the name of a user in \<UserName\> or \<Domain\Username\> format or enter an asterisk (\*) to represent all users.</span></span>
<span data-ttu-id="5d93e-212">Standardvärdet är alla användare.</span><span class="sxs-lookup"><span data-stu-id="5d93e-212">The default value is all users.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5d93e-213">– Varje vecka</span><span class="sxs-lookup"><span data-stu-id="5d93e-213">-Weekly</span></span>
<span data-ttu-id="5d93e-214">Anger ett återkommande veckovis jobb schema.</span><span class="sxs-lookup"><span data-stu-id="5d93e-214">Specifies a recurring weekly job schedule.</span></span>
<span data-ttu-id="5d93e-215">Använd de andra parametrarna i *vecko* parametern set för att ange schema information.</span><span class="sxs-lookup"><span data-stu-id="5d93e-215">Use the other parameters in the *Weekly* parameter set to specify the schedule details.</span></span>

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

### <span data-ttu-id="5d93e-216">-WeeksInterval</span><span class="sxs-lookup"><span data-stu-id="5d93e-216">-WeeksInterval</span></span>
<span data-ttu-id="5d93e-217">Anger antalet veckor mellan förekomster för ett vecko jobb schema.</span><span class="sxs-lookup"><span data-stu-id="5d93e-217">Specifies the number of weeks between occurrences on a weekly job schedule.</span></span>
<span data-ttu-id="5d93e-218">Värdet 3 startar till exempel det schemalagda jobbet på veckor 1, 4, 7 och så vidare.</span><span class="sxs-lookup"><span data-stu-id="5d93e-218">For example, a value of 3 starts the scheduled job on weeks 1, 4, 7 and so on.</span></span>
<span data-ttu-id="5d93e-219">Standardvärdet är 1.</span><span class="sxs-lookup"><span data-stu-id="5d93e-219">The default value is 1.</span></span>

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

### <span data-ttu-id="5d93e-220">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5d93e-220">CommonParameters</span></span>
<span data-ttu-id="5d93e-221">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5d93e-221">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5d93e-222">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5d93e-222">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5d93e-223">INDATA</span><span class="sxs-lookup"><span data-stu-id="5d93e-223">INPUTS</span></span>

### <span data-ttu-id="5d93e-224">Microsoft. PowerShell. ScheduledJob. ScheduledJobTrigger</span><span class="sxs-lookup"><span data-stu-id="5d93e-224">Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger</span></span>
<span data-ttu-id="5d93e-225">Du kan skicka flera jobb utlösare till **set-JobTrigger**.</span><span class="sxs-lookup"><span data-stu-id="5d93e-225">You can pipe multiple job triggers to **Set-JobTrigger**.</span></span>

## <span data-ttu-id="5d93e-226">UTDATA</span><span class="sxs-lookup"><span data-stu-id="5d93e-226">OUTPUTS</span></span>

### <span data-ttu-id="5d93e-227">Ingen eller Microsoft. PowerShell. ScheduledJob. ScheduledJobTrigger</span><span class="sxs-lookup"><span data-stu-id="5d93e-227">None or Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger</span></span>
<span data-ttu-id="5d93e-228">När du använder *Passthru* -parametern returnerar **set-JobTrigger** de jobb utlösare som har ändrats.</span><span class="sxs-lookup"><span data-stu-id="5d93e-228">When you use the *Passthru* parameter, **Set-JobTrigger** returns the job triggers that were changed.</span></span>
<span data-ttu-id="5d93e-229">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="5d93e-229">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="5d93e-230">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="5d93e-230">NOTES</span></span>

* <span data-ttu-id="5d93e-231">Jobb utlösare har en JobDefintion-egenskap som kopplar dem till det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="5d93e-231">Job triggers have a JobDefintion property that associates them with the scheduled job.</span></span> <span data-ttu-id="5d93e-232">När du ändrar jobb utlösaren för ett schemalagt jobb ändras jobbet.</span><span class="sxs-lookup"><span data-stu-id="5d93e-232">When you change the job trigger of a scheduled job, the job is changed.</span></span> <span data-ttu-id="5d93e-233">Du behöver inte använda ett Set-ScheduledJob-kommando för att tillämpa den ändrade utlösaren på det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="5d93e-233">You do not need to use a Set-ScheduledJob command to apply the changed trigger to the scheduled job.</span></span>

## <span data-ttu-id="5d93e-234">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="5d93e-234">RELATED LINKS</span></span>

[<span data-ttu-id="5d93e-235">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="5d93e-235">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="5d93e-236">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="5d93e-236">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="5d93e-237">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="5d93e-237">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="5d93e-238">Aktivera – JobTrigger</span><span class="sxs-lookup"><span data-stu-id="5d93e-238">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="5d93e-239">Aktivera – ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="5d93e-239">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="5d93e-240">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="5d93e-240">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="5d93e-241">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="5d93e-241">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="5d93e-242">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="5d93e-242">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="5d93e-243">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="5d93e-243">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="5d93e-244">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="5d93e-244">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="5d93e-245">Registrera – ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="5d93e-245">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="5d93e-246">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="5d93e-246">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="5d93e-247">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="5d93e-247">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="5d93e-248">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="5d93e-248">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="5d93e-249">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="5d93e-249">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="5d93e-250">Avregistrera-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="5d93e-250">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
