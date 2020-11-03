---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/new-jobtrigger?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-JobTrigger
ms.openlocfilehash: de49ab937c6f3a8187f5aecd6aafc81425b8cd00
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264645"
---
# <span data-ttu-id="3ceae-103">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3ceae-103">New-JobTrigger</span></span>

## <span data-ttu-id="3ceae-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="3ceae-104">SYNOPSIS</span></span>
<span data-ttu-id="3ceae-105">Skapar en jobb utlösare för ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="3ceae-105">Creates a job trigger for a scheduled job.</span></span>

## <span data-ttu-id="3ceae-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3ceae-106">SYNTAX</span></span>

### <span data-ttu-id="3ceae-107">En gång (standard)</span><span class="sxs-lookup"><span data-stu-id="3ceae-107">Once (Default)</span></span>

```
New-JobTrigger [-RandomDelay <TimeSpan>] -At <DateTime> [-Once] [-RepetitionInterval <TimeSpan>]
 [-RepetitionDuration <TimeSpan>] [-RepeatIndefinitely] [<CommonParameters>]
```

### <span data-ttu-id="3ceae-108">Varje dag</span><span class="sxs-lookup"><span data-stu-id="3ceae-108">Daily</span></span>

```
New-JobTrigger [-DaysInterval <Int32>] [-RandomDelay <TimeSpan>] -At <DateTime> [-Daily] [<CommonParameters>]
```

### <span data-ttu-id="3ceae-109">Varje vecka</span><span class="sxs-lookup"><span data-stu-id="3ceae-109">Weekly</span></span>

```
New-JobTrigger [-WeeksInterval <Int32>] [-RandomDelay <TimeSpan>] -At <DateTime> -DaysOfWeek <DayOfWeek[]>
 [-Weekly] [<CommonParameters>]
```

### <span data-ttu-id="3ceae-110">AtStartup</span><span class="sxs-lookup"><span data-stu-id="3ceae-110">AtStartup</span></span>

```
New-JobTrigger [-RandomDelay <TimeSpan>] [-AtStartup] [<CommonParameters>]
```

### <span data-ttu-id="3ceae-111">AtLogon</span><span class="sxs-lookup"><span data-stu-id="3ceae-111">AtLogon</span></span>

```
New-JobTrigger [-RandomDelay <TimeSpan>] [-User <String>] [-AtLogOn] [<CommonParameters>]
```

## <span data-ttu-id="3ceae-112">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="3ceae-112">DESCRIPTION</span></span>
<span data-ttu-id="3ceae-113">Cmdlet **: en New-JobTrigger** skapar en jobb utlösare som startar ett schemalagt jobb vid ett engångs-eller återkommande schema, eller när en händelse inträffar.</span><span class="sxs-lookup"><span data-stu-id="3ceae-113">The **New-JobTrigger** cmdlet creates a job trigger that starts a scheduled job on a one-time or recurring schedule, or when an event occurs.</span></span>

<span data-ttu-id="3ceae-114">Du kan använda **ScheduledJobTrigger** -objektet som **New-JobTrigger** returnerar för att ange en jobb utlösare för ett nytt eller befintligt schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="3ceae-114">You can use the **ScheduledJobTrigger** object that **New-JobTrigger** returns to set a job trigger for a new or existing scheduled job.</span></span>
<span data-ttu-id="3ceae-115">Du kan också skapa en jobb utlösare med hjälp av Get-JobTrigger cmdlet för att hämta jobb utlösaren för ett befintligt schemalagt jobb, eller genom att använda ett värde för hash-tabellen för att representera en jobb utlösare.</span><span class="sxs-lookup"><span data-stu-id="3ceae-115">You can also create a job trigger by using the Get-JobTrigger cmdlet to get the job trigger of an existing scheduled job, or by using a hash table value to represent a job trigger.</span></span>

<span data-ttu-id="3ceae-116">När du skapar en jobb utlösare granskar du standardvärdena för de alternativ som anges i New-ScheduledJobOption-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="3ceae-116">When creating a job trigger, review the default values of the options specified by the New-ScheduledJobOption cmdlet.</span></span>
<span data-ttu-id="3ceae-117">Dessa alternativ, som har samma giltiga värden och standardvärden som motsvarande alternativ i **Schemaläggaren** , påverkar schemaläggningen och tids inställningen för schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="3ceae-117">These options, which have the same valid and default values as the corresponding options in **Task Scheduler** , affect the scheduling and timing of scheduled jobs.</span></span>

<span data-ttu-id="3ceae-118">**New-JobTrigger** är en samling jobb schemaläggnings-cmdletar i PSScheduledJob-modulen som ingår i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3ceae-118">**New-JobTrigger** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="3ceae-119">Mer information om schemalagda jobb finns i avsnittet om ämnen i PSScheduledJob-modulen.</span><span class="sxs-lookup"><span data-stu-id="3ceae-119">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="3ceae-120">Importera modulen PSScheduledJob och skriv sedan: `Get-Help about_Scheduled*` eller se about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="3ceae-120">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="3ceae-121">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="3ceae-121">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="3ceae-122">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="3ceae-122">EXAMPLES</span></span>

### <span data-ttu-id="3ceae-123">Exempel 1: schema</span><span class="sxs-lookup"><span data-stu-id="3ceae-123">Example 1: Once Schedule</span></span>

```
PS C:\> New-JobTrigger -Once -At "1/20/2012 3:00 AM"
```

<span data-ttu-id="3ceae-124">Det här kommandot använder cmdleten **New-JobTrigger** för att skapa en jobb utlösare som bara startar ett schemalagt jobb en gången.</span><span class="sxs-lookup"><span data-stu-id="3ceae-124">This command uses the **New-JobTrigger** cmdlet to create a job trigger that starts a scheduled job only one time.</span></span>
<span data-ttu-id="3ceae-125">Värdet för *at* -parametern är en sträng som Windows PowerShell konverterar till ett **datetime** -objekt.</span><span class="sxs-lookup"><span data-stu-id="3ceae-125">The value of the *At* parameter is a string that Windows PowerShell converts into a **DateTime** object.</span></span>
<span data-ttu-id="3ceae-126">Värdet *vid* parameter innehåller ett explicit datum, inte bara en tid.</span><span class="sxs-lookup"><span data-stu-id="3ceae-126">The *At* parameter value includes an explicit date, not just a time.</span></span>
<span data-ttu-id="3ceae-127">Om datumet utelämnas skulle utlösaren att skapas med aktuellt datum och 3:00 AM tid, vilket förmodligen motsvarar en tid i det förflutna.</span><span class="sxs-lookup"><span data-stu-id="3ceae-127">If the date were omitted, the trigger would be created with the current date and 3:00 AM time, which is likely to represent a time in the past.</span></span>

### <span data-ttu-id="3ceae-128">Exempel 2: dagligt schema</span><span class="sxs-lookup"><span data-stu-id="3ceae-128">Example 2: Daily Schedule</span></span>

```
PS C:\> New-JobTrigger -Daily -At "4:15 AM" -DaysInterval 3
Id         Frequency       Time                   DaysOfWeek              Enabled
--         ---------       ----                   ----------              -------
0          Daily           9/21/2012 4:15:00 AM                           True
```

<span data-ttu-id="3ceae-129">Det här kommandot skapar en jobb utlösare som startar ett schemalagt jobb var tredje dag kl. 4:15</span><span class="sxs-lookup"><span data-stu-id="3ceae-129">This command creates a job trigger that starts a scheduled job every 3 days at 4:15 a.m.</span></span>

<span data-ttu-id="3ceae-130">Eftersom värdet för *at* -parametern inte innehåller ett datum används det aktuella datumet som datumvärdet i **datetime** -objektet.</span><span class="sxs-lookup"><span data-stu-id="3ceae-130">Because the value of the *At* parameter does not include a date, the current date is used as the date value in the **DateTime** object.</span></span>
<span data-ttu-id="3ceae-131">Om datumet och tiden är i det förflutna, startas det schemalagda jobbet vid nästa tillfälle, vilket är 3 dagar senare från värdet *vid* parameter.</span><span class="sxs-lookup"><span data-stu-id="3ceae-131">If the date and time is in the past, the scheduled job is started at the next occurrence, which is 3 days later from the *At* parameter value.</span></span>

### <span data-ttu-id="3ceae-132">Exempel 3: vecko schema</span><span class="sxs-lookup"><span data-stu-id="3ceae-132">Example 3: Weekly Schedule</span></span>

```
PS C:\> New-JobTrigger -Weekly -DaysOfWeek Monday, Wednesday, Friday -At "23:00" -WeeksInterval 4
Id Frequency Time                  DaysOfWeek                  Enabled
-- --------- ----                  ----------                  -------
0  Weekly    9/21/2012 11:00:00 PM {Monday, Wednesday, Friday} True
```

<span data-ttu-id="3ceae-133">Det här kommandot skapar en jobb utlösare som startar ett schemalagt jobb var fjärde vecka på måndag, onsdag och fredag med 2300 timmar (11:00 PM).</span><span class="sxs-lookup"><span data-stu-id="3ceae-133">This command creates a job trigger that starts a scheduled job every 4 weeks on Monday, Wednesday, and Friday at 2300 hours (11:00 PM).</span></span>

<span data-ttu-id="3ceae-134">Du kan också ange värdet för parametern *DaysOfWeek* i heltal, till exempel `-DaysOfWeek 1, 5` .</span><span class="sxs-lookup"><span data-stu-id="3ceae-134">You can also enter the *DaysOfWeek* parameter value in integers, such as `-DaysOfWeek 1, 5`.</span></span>

### <span data-ttu-id="3ceae-135">Exempel 4: inloggnings schema</span><span class="sxs-lookup"><span data-stu-id="3ceae-135">Example 4: Logon Schedule</span></span>

```
PS C:\> New-JobTrigger -AtLogOn -User Domain01\Admin01
```

<span data-ttu-id="3ceae-136">Det här kommandot skapar en jobb utlösare som startar ett schemalagt jobb varje gång som domän administratören loggar in på datorn.</span><span class="sxs-lookup"><span data-stu-id="3ceae-136">This command creates a job trigger that starts a scheduled job whenever the domain administrator logs onto the computer.</span></span>

### <span data-ttu-id="3ceae-137">Exempel 5: använda en slumpmässig fördröjning</span><span class="sxs-lookup"><span data-stu-id="3ceae-137">Example 5: Using a Random Delay</span></span>

```
PS C:\> New-JobTrigger -Daily -At 1:00 -RandomDelay 00:20:00
```

<span data-ttu-id="3ceae-138">Det här kommandot skapar en jobb utlösare som startar ett schemalagt jobb varje dag på 1:00 i morgon.</span><span class="sxs-lookup"><span data-stu-id="3ceae-138">This command creates a job trigger that starts a scheduled job every day at 1:00 in the morning.</span></span>
<span data-ttu-id="3ceae-139">Kommandot använder parametern *RandomDelay* för att ange maximal fördröjning till 20 minuter.</span><span class="sxs-lookup"><span data-stu-id="3ceae-139">The command uses the *RandomDelay* parameter to set the maximum delay to 20 minutes.</span></span>
<span data-ttu-id="3ceae-140">Det innebär att jobbet körs varje dag mellan 1:00 och 1:20, med intervallet varierande pseudo-slumpvis.</span><span class="sxs-lookup"><span data-stu-id="3ceae-140">As a result, the job runs every day between 1:00 AM and 1:20 AM, with the interval varying pseudo-randomly.</span></span>

<span data-ttu-id="3ceae-141">Du kan använda en slumpmässig fördröjning för sampling, belastnings utjämning och andra administrativa uppgifter.</span><span class="sxs-lookup"><span data-stu-id="3ceae-141">You can use a random delay for sampling, load balancing, and other administrative tasks.</span></span>
<span data-ttu-id="3ceae-142">När du anger fördröjning svärdet granskar du effektiva och standardvärden för New-ScheduledJobOption-cmdleten och koordinerar fördröjningen med alternativ inställningarna.</span><span class="sxs-lookup"><span data-stu-id="3ceae-142">When setting the delay value, review the effective and default values of the New-ScheduledJobOption cmdlet and coordinate the delay with the option settings.</span></span>

### <span data-ttu-id="3ceae-143">Exempel 6: skapa en jobb utlösare för ett nytt schemalagt jobb</span><span class="sxs-lookup"><span data-stu-id="3ceae-143">Example 6: Create a Job Trigger for a New Scheduled Job</span></span>

```
The first command uses the **New-JobTrigger** cmdlet to create a job trigger that starts a job every Monday, Wednesday, and Friday at 12:01 AM. The command saves the job trigger in the $T variable.
PS C:\> $T = New-JobTrigger -Weekly -DaysOfWeek 1,3,5 -At 12:01AM


The second command uses the Register-ScheduledJob cmdlet to create a scheduled job that starts a job every Monday, Wednesday, and Friday at 12:01 AM. The value of the *Trigger* parameter is the trigger that is stored in the $T variable.
PS C:\> Register-ScheduledJob -Name Test-HelpFiles -FilePath C:\Scripts\Test-HelpFiles.ps1 -Trigger $T
```

<span data-ttu-id="3ceae-144">Dessa kommandon använder en jobb utlösare för att skapa ett nytt schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="3ceae-144">These commands use a job trigger to create a new scheduled job.</span></span>

### <span data-ttu-id="3ceae-145">Exempel 7: Lägg till en jobb utlösare i ett schemalagt jobb</span><span class="sxs-lookup"><span data-stu-id="3ceae-145">Example 7: Add a Job Trigger to a Scheduled Job</span></span>

```
PS C:\> Add-JobTrigger -Name SynchronizeApps -Trigger (New-JobTrigger -Daily -At 3:10AM)
```

<span data-ttu-id="3ceae-146">Det här exemplet visar hur du lägger till en jobb utlösare i ett befintligt schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="3ceae-146">This example shows how to add a job trigger to an existing scheduled job.</span></span>
<span data-ttu-id="3ceae-147">Du kan lägga till flera jobb utlösare till ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="3ceae-147">You can add multiple job triggers to any scheduled job.</span></span>

<span data-ttu-id="3ceae-148">Kommandot använder cmdleten Add-JobTrigger för att lägga till jobb utlösaren i det schemalagda jobbet SynchronizeApps.</span><span class="sxs-lookup"><span data-stu-id="3ceae-148">The command uses the Add-JobTrigger cmdlet to add the job trigger to the SynchronizeApps scheduled job.</span></span>
<span data-ttu-id="3ceae-149">Värdet för *Utlösar* -parametern är ett **New-JobTrigger-** kommando som kör jobbet varje dag kl. 3:10.</span><span class="sxs-lookup"><span data-stu-id="3ceae-149">The value of the *Trigger* parameter is a **New-JobTrigger** command that runs the job every day at 3:10 AM.</span></span>

<span data-ttu-id="3ceae-150">När kommandot har slutförts är SynchronizeApps ett schemalagt jobb som körs vid de tidpunkter som anges av jobb utlösaren.</span><span class="sxs-lookup"><span data-stu-id="3ceae-150">When the command completes, SynchronizeApps is a scheduled job that runs at the times specified by the job trigger.</span></span>

### <span data-ttu-id="3ceae-151">Exempel 8: skapa en utlösare för återkommande jobb</span><span class="sxs-lookup"><span data-stu-id="3ceae-151">Example 8: Create a repeating job trigger</span></span>

```
PS C:\> New-JobTrigger -Once -At "09/12/2013 1:00:00" -RepetitionInterval (New-TimeSpan -Hours 1) -RepetitionDuration (New-Timespan -Hours 48)
```

<span data-ttu-id="3ceae-152">Det här kommandot skapar en jobb utlösare som kör ett jobb var 60: e minut i 48 timmar från den 12 september 2013 vid 1:00.</span><span class="sxs-lookup"><span data-stu-id="3ceae-152">This command creates a job trigger that runs a job every 60 minutes for 48 hours beginning on September 12, 2013 at 1:00 AM.</span></span>

### <span data-ttu-id="3ceae-153">Exempel 9: stoppa en utlösare för upprepad utskrift</span><span class="sxs-lookup"><span data-stu-id="3ceae-153">Example 9: Stop a repeating job trigger</span></span>

```
PS C:\> Get-JobTrigger -Name SecurityCheck | Set-JobTrigger -RepetitionInterval 0:00 -RepetitionDuration 0:00
```

<span data-ttu-id="3ceae-154">Med det här kommandot stoppas SecurityCheck-jobbet, som aktive ras för körning var 60: e minut tills jobb utlösaren upphör att gälla.</span><span class="sxs-lookup"><span data-stu-id="3ceae-154">This command forcibly stops the SecurityCheck job, which is triggered to run every 60 minutes until its job trigger expires.</span></span>

<span data-ttu-id="3ceae-155">För att förhindra att jobbet upprepas använder kommandot Get-JobTrigger för att hämta jobb utlösaren för SecurityCheck-jobbet och cmdleten Set-JobTrigger för att ändra upprepnings intervallet och upprepnings tiden för jobb utlösaren till noll (0).</span><span class="sxs-lookup"><span data-stu-id="3ceae-155">To prevent the job from repeating, the command uses the Get-JobTrigger to get the job trigger of the SecurityCheck job and the Set-JobTrigger cmdlet to change the repetition interval and repetition duration of the job trigger to zero (0).</span></span>

### <span data-ttu-id="3ceae-156">Exempel 10: skapa en jobb utlösare per timme</span><span class="sxs-lookup"><span data-stu-id="3ceae-156">Example 10: Create an hourly job trigger</span></span>

```
PS C:\> New-JobTrigger -Once -At "9/21/2012 0am" -RepetitionInterval (New-TimeSpan -Hour 12) -RepetitionDuration ([TimeSpan]::MaxValue)
```

<span data-ttu-id="3ceae-157">Följande kommando skapar en jobb utlösare som kör ett schemalagt jobb en gång var 12: e timme under en obestämd tids period.</span><span class="sxs-lookup"><span data-stu-id="3ceae-157">The following command creates a job trigger that runs a scheduled job once every 12 hours for an indefinite period of time.</span></span>
<span data-ttu-id="3ceae-158">Schemat börjar i morgon (9/21/2012) vid midnatt (0:00 AM).</span><span class="sxs-lookup"><span data-stu-id="3ceae-158">The schedule begins tomorrow (9/21/2012) at midnight (0:00 AM).</span></span>

## <span data-ttu-id="3ceae-159">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="3ceae-159">PARAMETERS</span></span>

### <span data-ttu-id="3ceae-160">– På</span><span class="sxs-lookup"><span data-stu-id="3ceae-160">-At</span></span>
<span data-ttu-id="3ceae-161">Startar jobbet vid angivet datum och tid.</span><span class="sxs-lookup"><span data-stu-id="3ceae-161">Starts the job at the specified date and time.</span></span>
<span data-ttu-id="3ceae-162">Ange ett **datetime** -objekt, till exempel ett som Get-Date cmdlet returnerar, eller en sträng som kan konverteras till ett datum och en tid, till exempel "April 19, 2012 15:00", "12/31" eller "3am".</span><span class="sxs-lookup"><span data-stu-id="3ceae-162">Enter a **DateTime** object, such as one that the Get-Date cmdlet returns, or a string that can be converted to a date and time, such as "April 19, 2012 15:00", "12/31", or "3am".</span></span>
<span data-ttu-id="3ceae-163">Om du inte anger ett element i datumet, till exempel året, har datumet i utlösaren motsvarande element från det aktuella datumet.</span><span class="sxs-lookup"><span data-stu-id="3ceae-163">If you don't specify an element of the date, such as the year, the date in the trigger has the corresponding element from the current date.</span></span>

<span data-ttu-id="3ceae-164">När du använder parametern *Once* ställer du in värdet för parametern *at* till ett framtida datum och en framtida tidpunkt.</span><span class="sxs-lookup"><span data-stu-id="3ceae-164">When using the *Once* parameter, set the value of the *At* parameter to a future date and time.</span></span>
<span data-ttu-id="3ceae-165">Eftersom standard datumet i ett **datetime** -objekt är det aktuella datumet, om du anger en tid före den aktuella tiden utan ett explicit datum, skapas jobb utlösaren för en tid i det förflutna.</span><span class="sxs-lookup"><span data-stu-id="3ceae-165">Because the default date in a **DateTime** object is the current date, if you specify a time before the current time without an explicit date, the job trigger is created for a time in the past.</span></span>

<span data-ttu-id="3ceae-166">**Datetime** -objekt och strängar som konverteras till **datetime** -objekt justeras automatiskt så att de är kompatibla med de datum-och tids format som valts för den lokala datorn i region och språk på kontroll panelen.</span><span class="sxs-lookup"><span data-stu-id="3ceae-166">**DateTime** objects, and strings that are converted to **DateTime** objects, are automatically adjusted to be compatible with the date and time formats selected for the local computer in Region and Language in Control Panel.</span></span>

```yaml
Type: System.DateTime
Parameter Sets: Once, Daily, Weekly
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3ceae-167">-AtLogOn</span><span class="sxs-lookup"><span data-stu-id="3ceae-167">-AtLogOn</span></span>
<span data-ttu-id="3ceae-168">Startar det schemalagda jobbet när de angivna användarna loggar in på datorn.</span><span class="sxs-lookup"><span data-stu-id="3ceae-168">Starts the scheduled job when the specified users log on to the computer.</span></span>
<span data-ttu-id="3ceae-169">Använd *användar* parametern för att ange en användare.</span><span class="sxs-lookup"><span data-stu-id="3ceae-169">To specify a user, use the *User* parameter.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AtLogon
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3ceae-170">-AtStartup</span><span class="sxs-lookup"><span data-stu-id="3ceae-170">-AtStartup</span></span>
<span data-ttu-id="3ceae-171">Startar det schemalagda jobbet när Windows startas.</span><span class="sxs-lookup"><span data-stu-id="3ceae-171">Starts the scheduled job when Windows starts.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: AtStartup
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3ceae-172">– Varje dag</span><span class="sxs-lookup"><span data-stu-id="3ceae-172">-Daily</span></span>
<span data-ttu-id="3ceae-173">Anger ett återkommande schema för dagligt jobb.</span><span class="sxs-lookup"><span data-stu-id="3ceae-173">Specifies a recurring daily job schedule.</span></span>
<span data-ttu-id="3ceae-174">Använd de andra parametrarna i den *dagliga* parameter uppsättningen för att ange schema information.</span><span class="sxs-lookup"><span data-stu-id="3ceae-174">Use the other parameters in the *Daily* parameter set to specify the schedule details.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Daily
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3ceae-175">-DaysInterval</span><span class="sxs-lookup"><span data-stu-id="3ceae-175">-DaysInterval</span></span>
<span data-ttu-id="3ceae-176">Anger antalet dagar mellan förekomster enligt ett dagligt schema.</span><span class="sxs-lookup"><span data-stu-id="3ceae-176">Specifies the number of days between occurrences on a daily schedule.</span></span>
<span data-ttu-id="3ceae-177">Värdet 3 startar till exempel det schemalagda jobbet på dagar 1, 4, 7 och så vidare.</span><span class="sxs-lookup"><span data-stu-id="3ceae-177">For example, a value of 3 starts the scheduled job on days 1, 4, 7 and so on.</span></span>
<span data-ttu-id="3ceae-178">Standardvärdet är 1.</span><span class="sxs-lookup"><span data-stu-id="3ceae-178">The default value is 1.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Daily
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3ceae-179">-DaysOfWeek</span><span class="sxs-lookup"><span data-stu-id="3ceae-179">-DaysOfWeek</span></span>
<span data-ttu-id="3ceae-180">Anger vecko dagarna som ett schemalagt vecko jobb körs på.</span><span class="sxs-lookup"><span data-stu-id="3ceae-180">Specifies the days of the week on which a weekly scheduled job runs.</span></span>
<span data-ttu-id="3ceae-181">Ange dag namn, till exempel "måndag" eller heltal 0-6, där 0 representerar söndag.</span><span class="sxs-lookup"><span data-stu-id="3ceae-181">Enter day names, such as "Monday" or integers 0-6, where 0 represents Sunday.</span></span>
<span data-ttu-id="3ceae-182">Den här parametern krävs i den veckobaserade parameter uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="3ceae-182">This parameter is required in the Weekly parameter set.</span></span>

<span data-ttu-id="3ceae-183">Dag namn konverteras till deras heltals värden i jobb utlösaren.</span><span class="sxs-lookup"><span data-stu-id="3ceae-183">Day names are converted to their integer values in the job trigger.</span></span>
<span data-ttu-id="3ceae-184">När du omger dag namn inom citat tecken i ett kommando, omger du varje dag med separata citat tecken, till exempel "måndag", "tisdag".</span><span class="sxs-lookup"><span data-stu-id="3ceae-184">When you enclose day names in quotation marks in a command, enclose each day name in separate quotation marks, such as "Monday", "Tuesday".</span></span>
<span data-ttu-id="3ceae-185">Om du omger flera dag namn i ett enkelt citat tecken, summeras motsvarande heltals värden.</span><span class="sxs-lookup"><span data-stu-id="3ceae-185">If you enclose multiple day names in a single quotation mark pair, the corresponding integer values are summed.</span></span>
<span data-ttu-id="3ceae-186">Till exempel "måndag, tisdag" (1, 2) resulterar i värdet "onsdag" (3).</span><span class="sxs-lookup"><span data-stu-id="3ceae-186">For example, "Monday, Tuesday" (1, 2) results in a value of "Wednesday" (3).</span></span>

```yaml
Type: System.DayOfWeek[]
Parameter Sets: Weekly
Aliases:
Accepted values: Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3ceae-187">– En gång</span><span class="sxs-lookup"><span data-stu-id="3ceae-187">-Once</span></span>
<span data-ttu-id="3ceae-188">Anger en icke-återkommande (en tid) eller ett anpassat upprepat schema.</span><span class="sxs-lookup"><span data-stu-id="3ceae-188">Specifies a non-recurring (one time) or custom repeating schedule.</span></span>
<span data-ttu-id="3ceae-189">Om du vill skapa ett upprepat schema använder du parametern *Once* med parametrarna *RepetitionDuration* och *RepetitionInterval* .</span><span class="sxs-lookup"><span data-stu-id="3ceae-189">To create a repeating schedule, use the *Once* parameter with the *RepetitionDuration* and *RepetitionInterval* parameters.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Once
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3ceae-190">-RandomDelay</span><span class="sxs-lookup"><span data-stu-id="3ceae-190">-RandomDelay</span></span>
<span data-ttu-id="3ceae-191">Aktiverar en slumpmässig fördröjning som börjar vid den schemalagda start tiden och anger högsta fördröjnings värde.</span><span class="sxs-lookup"><span data-stu-id="3ceae-191">Enables a random delay that begins at the scheduled start time, and sets the maximum delay value.</span></span>
<span data-ttu-id="3ceae-192">Längden på fördröjningen är att ställa in pseudo – slumpvis för varje start och varierar från ingen fördröjning till den tid som anges av värdet för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="3ceae-192">The length of the delay is set pseudo-randomly for each start and varies from no delay to the time specified by the value of this parameter.</span></span>
<span data-ttu-id="3ceae-193">Standardvärdet noll (00:00:00), inaktiverar slumpmässig fördröjning.</span><span class="sxs-lookup"><span data-stu-id="3ceae-193">The default value, zero (00:00:00), disables the random delay.</span></span>

<span data-ttu-id="3ceae-194">Ange ett TimeSpan-objekt, till exempel ett som returneras av New-TimeSpan-cmdleten, eller ange ett värde i \<hours\> : \<minutes\> : \<seconds\> format, som automatiskt konverteras till ett **TimeSpan** -objekt.</span><span class="sxs-lookup"><span data-stu-id="3ceae-194">Enter a timespan object, such as one returned by the New-TimeSpan cmdlet, or enter a value in \<hours\>:\<minutes\>:\<seconds\> format, which is automatically converted to a **TimeSpan** object.</span></span>

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

### <span data-ttu-id="3ceae-195">-RepeatIndefinitely</span><span class="sxs-lookup"><span data-stu-id="3ceae-195">-RepeatIndefinitely</span></span>
<span data-ttu-id="3ceae-196">Den här parametern, som är tillgänglig från och med Windows PowerShell 4,0, eliminerar behovet av att ange ett **TimeSpan. MaxValue** -värde för parametern *RepetitionDuration* för att köra ett schemalagt jobb upprepade gånger, under obestämd tid.</span><span class="sxs-lookup"><span data-stu-id="3ceae-196">This parameter, available starting in Windows PowerShell 4.0, eliminates the necessity of specifying a **TimeSpan.MaxValue** value for the *RepetitionDuration* parameter to run a scheduled job repeatedly, for an indefinite period.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Once
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3ceae-197">-RepetitionDuration</span><span class="sxs-lookup"><span data-stu-id="3ceae-197">-RepetitionDuration</span></span>
<span data-ttu-id="3ceae-198">Upprepar jobbet tills den angivna tiden upphör att gälla.</span><span class="sxs-lookup"><span data-stu-id="3ceae-198">Repeats the job until the specified time expires.</span></span>
<span data-ttu-id="3ceae-199">Upprepnings frekvensen bestäms av värdet för parametern *RepetitionInterval* .</span><span class="sxs-lookup"><span data-stu-id="3ceae-199">The repetition frequency is determined by the value of the *RepetitionInterval* parameter.</span></span>
<span data-ttu-id="3ceae-200">Om värdet för **RepetitionInterval** till exempel är 5 minuter och värdet för **RepetitionDuration** är 2 timmar utlöses jobbet var femte minut i två timmar.</span><span class="sxs-lookup"><span data-stu-id="3ceae-200">For example, if the value of **RepetitionInterval** is 5 minutes and the value of **RepetitionDuration** is 2 hours, the job is triggered every five minutes for two hours.</span></span>

<span data-ttu-id="3ceae-201">Ange ett TimeSpan-objekt, till exempel ett som New-TimeSpan cmdlet returnerar eller en sträng som kan konverteras till ett TimeSpan-objekt, till exempel "1:05:30".</span><span class="sxs-lookup"><span data-stu-id="3ceae-201">Enter a timespan object, such as one that the New-TimeSpan cmdlet returns or a string that can be converted to a timespan object, such as "1:05:30".</span></span>

<span data-ttu-id="3ceae-202">Om du vill köra ett jobb oändligt lägger du till parametern *RepeatIndefinitely* i stället.</span><span class="sxs-lookup"><span data-stu-id="3ceae-202">To run a job indefinitely, add the *RepeatIndefinitely* parameter instead.</span></span>

<span data-ttu-id="3ceae-203">Om du vill stoppa ett jobb innan jobbets repetitions varaktighet upphör att gälla, använder du Set-JobTrigger cmdlet för att ange värdet noll (0) för *RepetitionDuration* -värdet.</span><span class="sxs-lookup"><span data-stu-id="3ceae-203">To stop a job before the job trigger repetition duration expires, use the Set-JobTrigger cmdlet to set the *RepetitionDuration* value to zero (0).</span></span>

<span data-ttu-id="3ceae-204">Den här parametern är endast giltig när parametrarna *Once* , *at* och *RepetitionInterval* används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="3ceae-204">This parameter is valid only when the *Once* , *At* and *RepetitionInterval* parameters are used in the command.</span></span>

```yaml
Type: System.TimeSpan
Parameter Sets: Once
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3ceae-205">-RepetitionInterval</span><span class="sxs-lookup"><span data-stu-id="3ceae-205">-RepetitionInterval</span></span>
<span data-ttu-id="3ceae-206">Upprepar jobbet vid det angivna tidsintervallet.</span><span class="sxs-lookup"><span data-stu-id="3ceae-206">Repeats the job at the specified time interval.</span></span>
<span data-ttu-id="3ceae-207">Om värdet för den här parametern till exempel är 2 timmar utlöses jobbet varannan timme.</span><span class="sxs-lookup"><span data-stu-id="3ceae-207">For example, if the value of this parameter is 2 hours, the job is triggered every two hours.</span></span>
<span data-ttu-id="3ceae-208">Standardvärdet, 0, upprepar inte jobbet.</span><span class="sxs-lookup"><span data-stu-id="3ceae-208">The default value, 0, does not repeat the job.</span></span>

<span data-ttu-id="3ceae-209">Ange ett TimeSpan-objekt, till exempel ett som New-TimeSpan cmdlet returnerar eller en sträng som kan konverteras till ett TimeSpan-objekt, till exempel "1:05:30".</span><span class="sxs-lookup"><span data-stu-id="3ceae-209">Enter a timespan object, such as one that the New-TimeSpan cmdlet returns or a string that can be converted to a timespan object, such as "1:05:30".</span></span>

<span data-ttu-id="3ceae-210">Den här parametern är endast giltig när parametrarna *Once* , *at* och *RepetitionDuration* används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="3ceae-210">This parameter is valid only when the *Once* , *At* , and *RepetitionDuration* parameters are used in the command.</span></span>

```yaml
Type: System.TimeSpan
Parameter Sets: Once
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3ceae-211">-User</span><span class="sxs-lookup"><span data-stu-id="3ceae-211">-User</span></span>
<span data-ttu-id="3ceae-212">Anger de användare som utlöser en *AtLogon* början av ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="3ceae-212">Specifies the users who trigger an *AtLogon* start of a scheduled job.</span></span>
<span data-ttu-id="3ceae-213">Ange namnet på en användare i \<UserName\> eller \<Domain\Username\> formatera eller ange en asterisk ( \* ) för att representera alla användare.</span><span class="sxs-lookup"><span data-stu-id="3ceae-213">Enter the name of a user in \<UserName\> or \<Domain\Username\> format or enter an asterisk (\*) to represent all users.</span></span>
<span data-ttu-id="3ceae-214">Standardvärdet är alla användare.</span><span class="sxs-lookup"><span data-stu-id="3ceae-214">The default value is all users.</span></span>

```yaml
Type: System.String
Parameter Sets: AtLogon
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3ceae-215">– Varje vecka</span><span class="sxs-lookup"><span data-stu-id="3ceae-215">-Weekly</span></span>
<span data-ttu-id="3ceae-216">Anger ett återkommande veckovis jobb schema.</span><span class="sxs-lookup"><span data-stu-id="3ceae-216">Specifies a recurring weekly job schedule.</span></span>
<span data-ttu-id="3ceae-217">Använd de andra parametrarna i vecko parametern set för att ange schema information.</span><span class="sxs-lookup"><span data-stu-id="3ceae-217">Use the other parameters in the Weekly parameter set to specify the schedule details.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Weekly
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3ceae-218">-WeeksInterval</span><span class="sxs-lookup"><span data-stu-id="3ceae-218">-WeeksInterval</span></span>
<span data-ttu-id="3ceae-219">Anger antalet veckor mellan förekomster för ett vecko jobb schema.</span><span class="sxs-lookup"><span data-stu-id="3ceae-219">Specifies the number of weeks between occurrences on a weekly job schedule.</span></span>
<span data-ttu-id="3ceae-220">Värdet 3 startar till exempel det schemalagda jobbet på veckor 1, 4, 7 och så vidare.</span><span class="sxs-lookup"><span data-stu-id="3ceae-220">For example, a value of 3 starts the scheduled job on weeks 1, 4, 7 and so on.</span></span>
<span data-ttu-id="3ceae-221">Standardvärdet är 1.</span><span class="sxs-lookup"><span data-stu-id="3ceae-221">The default value is 1.</span></span>

```yaml
Type: System.Int32
Parameter Sets: Weekly
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3ceae-222">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3ceae-222">CommonParameters</span></span>
<span data-ttu-id="3ceae-223">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3ceae-223">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3ceae-224">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="3ceae-224">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3ceae-225">INDATA</span><span class="sxs-lookup"><span data-stu-id="3ceae-225">INPUTS</span></span>

### <span data-ttu-id="3ceae-226">Inget</span><span class="sxs-lookup"><span data-stu-id="3ceae-226">None</span></span>
<span data-ttu-id="3ceae-227">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3ceae-227">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="3ceae-228">UTDATA</span><span class="sxs-lookup"><span data-stu-id="3ceae-228">OUTPUTS</span></span>

### <span data-ttu-id="3ceae-229">Microsoft. PowerShell. ScheduledJob. ScheduledJobTrigger</span><span class="sxs-lookup"><span data-stu-id="3ceae-229">Microsoft.PowerShell.ScheduledJob.ScheduledJobTrigger</span></span>

## <span data-ttu-id="3ceae-230">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="3ceae-230">NOTES</span></span>

* <span data-ttu-id="3ceae-231">Jobb utlösare sparas inte på disk.</span><span class="sxs-lookup"><span data-stu-id="3ceae-231">Job triggers are not saved to disk.</span></span> <span data-ttu-id="3ceae-232">Schemalagda jobb sparas dock på disk och du kan använda Get-JobTrigger för att hämta jobb utlösaren för schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="3ceae-232">However, scheduled jobs are saved to disk, and you can use the Get-JobTrigger to get the job trigger of any scheduled job.</span></span>
* <span data-ttu-id="3ceae-233">**New-JobTrigger** förhindrar inte att du skapar en jobb utlösare som inte kommer att köra ett schemalagt jobb, till exempel engångs utlösare för ett datum som redan har infallit.</span><span class="sxs-lookup"><span data-stu-id="3ceae-233">**New-JobTrigger** does not prevent you from creating a job trigger that will not run a scheduled job, such as one-time trigger for a date in the past.</span></span>
* <span data-ttu-id="3ceae-234">Register-ScheduledJob cmdleten accepterar ett ScheduledJobTrigger-objekt, till exempel en som returneras av cmdletarna **New-JobTrigger** eller Get-JobTrigger eller en hash-tabell med utlösarens värden.</span><span class="sxs-lookup"><span data-stu-id="3ceae-234">The Register-ScheduledJob cmdlet accepts a ScheduledJobTrigger object, such as one returned by the **New-JobTrigger** or Get-JobTrigger cmdlets, or a hash table with trigger values.</span></span>

  <span data-ttu-id="3ceae-235">Om du vill skicka en hash-tabell använder du följande nycklar.</span><span class="sxs-lookup"><span data-stu-id="3ceae-235">To submit a hash table, use the following keys.</span></span>

  <span data-ttu-id="3ceae-236">`@{Frequency="Once" (or Daily, Weekly, AtStartup, AtLogon);At="3am"` (eller en giltig tids sträng); `DaysOfWeek="Monday", "Wednesday"` (eller valfri kombination av dag namn); `Interval=2` (eller ett giltigt frekvens intervall); `RandomDelay="30minutes"` (eller en giltig TimeSpan-sträng); `User="Domain1\User01` (eller en giltig användare, används endast med värdet för *AtLogon* )}</span><span class="sxs-lookup"><span data-stu-id="3ceae-236">`@{Frequency="Once" (or Daily, Weekly, AtStartup, AtLogon);At="3am"` (or any valid time string); `DaysOfWeek="Monday", "Wednesday"` (or any combination of day names); `Interval=2` (or any valid frequency interval); `RandomDelay="30minutes"` (or any valid timespan string); `User="Domain1\User01` (or any valid user; used only with the *AtLogon* frequency value) }</span></span>

## <span data-ttu-id="3ceae-237">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="3ceae-237">RELATED LINKS</span></span>

[<span data-ttu-id="3ceae-238">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3ceae-238">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="3ceae-239">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3ceae-239">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="3ceae-240">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3ceae-240">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="3ceae-241">Aktivera – JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3ceae-241">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="3ceae-242">Aktivera – ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3ceae-242">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="3ceae-243">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3ceae-243">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="3ceae-244">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3ceae-244">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="3ceae-245">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="3ceae-245">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="3ceae-246">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3ceae-246">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="3ceae-247">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="3ceae-247">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="3ceae-248">Registrera – ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3ceae-248">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="3ceae-249">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3ceae-249">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="3ceae-250">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3ceae-250">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="3ceae-251">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3ceae-251">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="3ceae-252">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="3ceae-252">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="3ceae-253">Avregistrera-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3ceae-253">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
