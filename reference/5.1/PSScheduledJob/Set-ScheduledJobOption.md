---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/set-scheduledjoboption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-ScheduledJobOption
ms.openlocfilehash: 6647e9ba4e2ee49afa90dd382573d437d2deaee6
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264609"
---
# <span data-ttu-id="3e137-103">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="3e137-103">Set-ScheduledJobOption</span></span>

## <span data-ttu-id="3e137-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="3e137-104">SYNOPSIS</span></span>
<span data-ttu-id="3e137-105">Ändrar jobb alternativen för ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="3e137-105">Changes the job options of a scheduled job.</span></span>

## <span data-ttu-id="3e137-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="3e137-106">SYNTAX</span></span>

```
Set-ScheduledJobOption [-InputObject] <ScheduledJobOptions> [-PassThru] [-RunElevated] [-HideInTaskScheduler]
 [-RestartOnIdleResume] [-MultipleInstancePolicy <TaskMultipleInstancePolicy>] [-DoNotAllowDemandStart]
 [-RequireNetwork] [-StopIfGoingOffIdle] [-WakeToRun] [-ContinueIfGoingOnBattery] [-StartIfOnBattery]
 [-IdleTimeout <TimeSpan>] [-IdleDuration <TimeSpan>] [-StartIfIdle] [<CommonParameters>]
```

## <span data-ttu-id="3e137-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="3e137-107">DESCRIPTION</span></span>
<span data-ttu-id="3e137-108">Cmdlet **: en Set-ScheduledJobOptions** ändrar jobb alternativen för schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="3e137-108">The **Set-ScheduledJobOptions** cmdlet changes the job options of scheduled jobs.</span></span>

<span data-ttu-id="3e137-109">Om du vill ändra alternativen för ett schemalagt jobb börjar du med att använda Get-ScheduledJobOption-cmdlet för att hämta jobb alternativen för ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="3e137-109">To change the options of a scheduled job, begin by using the Get-ScheduledJobOption cmdlet to get the job options of a scheduled job.</span></span>
<span data-ttu-id="3e137-110">Sedan kan du ange alternativen för **set-ScheduledJobOption** eller spara alternativen i en variabel och använda *InputObject* -parametern för cmdleten **set-ScheduledJobOption** för att identifiera alternativen.</span><span class="sxs-lookup"><span data-stu-id="3e137-110">Then, pipe the options to **Set-ScheduledJobOption** or save the options in a variable and use the *InputObject* parameter of **Set-ScheduledJobOption** cmdlet to identify the options.</span></span>
<span data-ttu-id="3e137-111">Använd de återstående parametrarna för **set-ScheduledJobOption** för att ändra jobb alternativen.</span><span class="sxs-lookup"><span data-stu-id="3e137-111">Use the remaining parameters of **Set-ScheduledJobOption** to change the job options.</span></span>

<span data-ttu-id="3e137-112">Om du vill aktivera ett jobb alternativ använder du parametern som anger det alternativet.</span><span class="sxs-lookup"><span data-stu-id="3e137-112">To turn on a job option, use the parameter that sets that option.</span></span>
<span data-ttu-id="3e137-113">Om du vill inaktivera ett alternativ skriver du parameter namnet, ett kolon (:) och $False.</span><span class="sxs-lookup"><span data-stu-id="3e137-113">To turn off an option, type the parameter name, a colon (:), and $False.</span></span>
<span data-ttu-id="3e137-114">Om du till exempel vill inaktivera alternativet *RunElevated* skriver du `-RunElevated:$False` .</span><span class="sxs-lookup"><span data-stu-id="3e137-114">For example, to turn off the *RunElevated* option, type `-RunElevated:$False`.</span></span>

<span data-ttu-id="3e137-115">Varje jobb alternativ-objekt innehåller en jobb definitionen-egenskap som innehåller det schemalagda jobbet, så associationen med det schemalagda jobbet bevaras när jobb alternativen ändras.</span><span class="sxs-lookup"><span data-stu-id="3e137-115">Each job options object includes a JobDefinition property that contains the scheduled job, so the association with the scheduled job is retained when the job options are changed.</span></span>

<span data-ttu-id="3e137-116">Alternativen för schemalagda jobb avgör hur jobbet körs när Schemaläggaren startas.</span><span class="sxs-lookup"><span data-stu-id="3e137-116">The scheduled job options determine how the job runs when it is started by Task Scheduler.</span></span>
<span data-ttu-id="3e137-117">Dessa alternativ gäller inte när du använder Start-Job-cmdlet för att starta ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="3e137-117">These options to not apply when you use the Start-Job cmdlet to start a scheduled job.</span></span>

<span data-ttu-id="3e137-118">**Set-ScheduledJobOption** är en samling jobb schemaläggnings-cmdletar i PSScheduledJob-modulen som ingår i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3e137-118">**Set-ScheduledJobOption** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="3e137-119">Mer information om schemalagda jobb finns i avsnittet om ämnen i PSScheduledJob-modulen.</span><span class="sxs-lookup"><span data-stu-id="3e137-119">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="3e137-120">Importera modulen PSScheduledJob och skriv sedan: `Get-Help about_Scheduled*` eller se about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="3e137-120">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="3e137-121">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="3e137-121">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="3e137-122">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="3e137-122">EXAMPLES</span></span>

### <span data-ttu-id="3e137-123">Exempel 1: Ändra jobb alternativ</span><span class="sxs-lookup"><span data-stu-id="3e137-123">Example 1: Change job options</span></span>

```
PS C:\> Get-ScheduledJobOption -Name "DeployPackage"
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
WakeToRun              : False
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : False
RunWithoutNetwork      : False
DoNotAllowDemandStart  : False
MultipleInstancePolicy : IgnoreNew
JobDefinition          :

The second command uses the **Set-ScheduledJobOpton** cmdlet to change the job options so the values of the WakeToRun and RunWithoutNetwork properties are $True. The command uses the *Passthru* parameter to return the trigger after the change.
PS C:\> Get-ScheduledJobOption -Name "DeployPackage" | Set-ScheduledJobOption -WakeToRun -RequireNetwork:$False -Passthru
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
WakeToRun              : True
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : False
RunWithoutNetwork      : True
DoNotAllowDemandStart  : False
MultipleInstancePolicy : IgnoreNewJobDefinition          :
```

<span data-ttu-id="3e137-124">Det här exemplet visar hur du ändrar alternativen för ett schemalagt jobb på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="3e137-124">This example shows how to change the options of a scheduled job on the local computer.</span></span>

<span data-ttu-id="3e137-125">Det första kommandot använder cmdleten Get-ScheduledJobOption för att hämta jobb alternativen för det schemalagda jobbet DeployPackage.</span><span class="sxs-lookup"><span data-stu-id="3e137-125">The first command uses the Get-ScheduledJobOption cmdlet to get the job options of the DeployPackage scheduled job.</span></span>
<span data-ttu-id="3e137-126">Utdata visar att egenskaperna WakeToRun och RunElevated har angetts till $False.</span><span class="sxs-lookup"><span data-stu-id="3e137-126">The output shows that the WakeToRun and RunElevated properties are set to $False.</span></span>

<span data-ttu-id="3e137-127">Det här kommandot krävs inte. den ingår bara för att Visa effekterna av alternativ ändringen.</span><span class="sxs-lookup"><span data-stu-id="3e137-127">This command is not required; it is included only to show the effect of the option change.</span></span>

### <span data-ttu-id="3e137-128">Exempel 2: ändra ett alternativ för alla schemalagda Fjärrjobb</span><span class="sxs-lookup"><span data-stu-id="3e137-128">Example 2: Change an option on all remote scheduled jobs</span></span>

```
PS C:\> Invoke-Command -Computer "Server01" -ScriptBlock {Get-ScheduledJob | Get-ScheduledJobOption | Set-ScheduledJobOption -IdleTimeout 2:00:00}
```

<span data-ttu-id="3e137-129">Det här kommandot ändrar värdet för *idleTimeout* från en timme (standardvärdet) till två timmar för alla schemalagda jobb på den Server01 datorn.</span><span class="sxs-lookup"><span data-stu-id="3e137-129">This command changes the value of the *IdleTimeout* from one hour (the default value) to two hours on all scheduled jobs on the Server01 computer.</span></span>

<span data-ttu-id="3e137-130">Kommandot använder cmdleten Invoke-Command för att köra ett kommando på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="3e137-130">The command uses the Invoke-Command cmdlet to run a command on the Server01 computer.</span></span>

<span data-ttu-id="3e137-131">Fjärrkommandot börjar med ett Get-ScheduledJob-kommando som hämtar alla schemalagda jobb på datorn.</span><span class="sxs-lookup"><span data-stu-id="3e137-131">The remote command begins with a Get-ScheduledJob command that gets all scheduled jobs on the computer.</span></span>
<span data-ttu-id="3e137-132">De schemalagda jobben är skickas till Get-ScheduledJobOption-cmdleten, som hämtar jobb alternativen för de schemalagda jobben.</span><span class="sxs-lookup"><span data-stu-id="3e137-132">The scheduled jobs are piped to the Get-ScheduledJobOption cmdlet, which gets the job options of the scheduled jobs.</span></span>
<span data-ttu-id="3e137-133">Varje jobb alternativ-objekt innehåller en jobb definitionen-egenskap som innehåller det schemalagda jobbet, så objektets alternativ förblir kopplade till det schemalagda jobbet även om det ändras.</span><span class="sxs-lookup"><span data-stu-id="3e137-133">Each job options object contains a JobDefinition property that contains the scheduled job, so the options object remains associated with the scheduled job even when it is changed.</span></span>

<span data-ttu-id="3e137-134">Jobb utlösarna är skickas till cmdleten **set-ScheduledJobOption** , som ändrar värdet för alternativet *idleTimeout* till två timmar (2:00:00).</span><span class="sxs-lookup"><span data-stu-id="3e137-134">The job triggers are piped to the **Set-ScheduledJobOption** cmdlet, which changes the value of the *IdleTimeout* option to two hours (2:00:00).</span></span>

## <span data-ttu-id="3e137-135">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="3e137-135">PARAMETERS</span></span>

### <span data-ttu-id="3e137-136">-ContinueIfGoingOnBattery</span><span class="sxs-lookup"><span data-stu-id="3e137-136">-ContinueIfGoingOnBattery</span></span>
<span data-ttu-id="3e137-137">Stoppa inte det schemalagda jobbet om datorn växlar till batteri drift (koppla från växel ström) medan jobbet körs.</span><span class="sxs-lookup"><span data-stu-id="3e137-137">Do not stop the scheduled job if the computer switches to battery power (disconnects from AC power) while the job is running.</span></span>
<span data-ttu-id="3e137-138">Schemalagda jobb stoppas som standard när datorn kopplas från växel ström.</span><span class="sxs-lookup"><span data-stu-id="3e137-138">By default, scheduled jobs stop when the computer disconnects from AC power.</span></span>

<span data-ttu-id="3e137-139">Parametern *ContinueIfGoingOnBattery* anger värdet för egenskapen StopIfGoingOnBatteries för schemalagda jobb till $true.</span><span class="sxs-lookup"><span data-stu-id="3e137-139">The *ContinueIfGoingOnBattery* parameter sets the value of the StopIfGoingOnBatteries property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="3e137-140">-DoNotAllowDemandStart</span><span class="sxs-lookup"><span data-stu-id="3e137-140">-DoNotAllowDemandStart</span></span>
<span data-ttu-id="3e137-141">Starta bara jobbet när det utlöses.</span><span class="sxs-lookup"><span data-stu-id="3e137-141">Start the job only when it is triggered.</span></span>
<span data-ttu-id="3e137-142">Användare kan inte starta jobbet manuellt, t. ex. med hjälp av körnings funktionen i Schemaläggaren.</span><span class="sxs-lookup"><span data-stu-id="3e137-142">Users cannot start the job manually, such as by using the Run feature in Task Scheduler.</span></span>

<span data-ttu-id="3e137-143">Den här parametern påverkar endast Schemaläggaren.</span><span class="sxs-lookup"><span data-stu-id="3e137-143">This parameter only affects Task Scheduler.</span></span>
<span data-ttu-id="3e137-144">Den förhindrar inte att användare använder Start-Job cmdlet för att starta jobbet.</span><span class="sxs-lookup"><span data-stu-id="3e137-144">It does not prevents users from using the Start-Job cmdlet to start the job.</span></span>

<span data-ttu-id="3e137-145">Parametern *DoNotAllowDemandStart* anger värdet för egenskapen DoNotAllowDemandStart för schemalagda jobb till $true.</span><span class="sxs-lookup"><span data-stu-id="3e137-145">The *DoNotAllowDemandStart* parameter sets the value of the DoNotAllowDemandStart property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="3e137-146">-HideInTaskScheduler</span><span class="sxs-lookup"><span data-stu-id="3e137-146">-HideInTaskScheduler</span></span>
<span data-ttu-id="3e137-147">Visa inte jobbet i Schemaläggaren.</span><span class="sxs-lookup"><span data-stu-id="3e137-147">Do not display the job in Task Scheduler.</span></span>
<span data-ttu-id="3e137-148">Det här värdet påverkar endast den dator där jobbet körs.</span><span class="sxs-lookup"><span data-stu-id="3e137-148">This value affects only the computer on which the job runs.</span></span>
<span data-ttu-id="3e137-149">Som standard visas schemalagda aktiviteter i Schemaläggaren.</span><span class="sxs-lookup"><span data-stu-id="3e137-149">By default, scheduled tasks appear in Task Scheduler.</span></span>

<span data-ttu-id="3e137-150">Även om en aktivitet är dold kan användarna Visa uppgiften genom att välja Visa **dolda aktiviteter** i Schemaläggaren.</span><span class="sxs-lookup"><span data-stu-id="3e137-150">Even if a task is hidden, users can display the task by selecting the **Show hidden tasks** view option in Task Scheduler.</span></span>

<span data-ttu-id="3e137-151">Parametern *HideInTaskScheduler* anger värdet för egenskapen ShowInTaskScheduler för schemalagda jobb till $false.</span><span class="sxs-lookup"><span data-stu-id="3e137-151">The *HideInTaskScheduler* parameter sets the value of the ShowInTaskScheduler property of scheduled jobs to $False.</span></span>

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

### <span data-ttu-id="3e137-152">-IdleDuration</span><span class="sxs-lookup"><span data-stu-id="3e137-152">-IdleDuration</span></span>
<span data-ttu-id="3e137-153">Anger hur länge datorn måste vara inaktiv innan jobbet startas.</span><span class="sxs-lookup"><span data-stu-id="3e137-153">Specifies how long the computer must be idle before the job starts.</span></span>
<span data-ttu-id="3e137-154">Standardvärdet är 10 minuter.</span><span class="sxs-lookup"><span data-stu-id="3e137-154">The default value is 10 minutes.</span></span>
<span data-ttu-id="3e137-155">Om datorn inte är inaktiv under den angivna tiden innan värdet för *idleTimeout* går ut, körs inte det schemalagda jobbet förrän nästa schemalagda tid, om det finns.</span><span class="sxs-lookup"><span data-stu-id="3e137-155">If the computer is not idle for the specified duration before the value of *IdleTimeout* expires, the scheduled job does not run until the next scheduled time, if any.</span></span>

<span data-ttu-id="3e137-156">Ange ett TimeSpan-objekt, till exempel ett som genereras av New-TimeSpan-cmdleten, eller ange ett värde i \<hours\> : \<minutes\> : \<seconds\> format som automatiskt konverteras till ett **TimeSpan** -objekt.</span><span class="sxs-lookup"><span data-stu-id="3e137-156">Enter a timespan object, such as one generated by the New-TimeSpan cmdlet, or enter a value in \<hours\>:\<minutes\>:\<seconds\> format that is automatically converted to a **TimeSpan** object.</span></span>

<span data-ttu-id="3e137-157">Använd parametern *StartIfIdle* om du vill aktivera det här värdet.</span><span class="sxs-lookup"><span data-stu-id="3e137-157">To enable this value, use the *StartIfIdle* parameter.</span></span>
<span data-ttu-id="3e137-158">Som standard är egenskapen StartIfNotIdle för schemalagda jobb inställd på $True och Windows PowerShell ignorerar värdena *IdleDuration* och *idleTimeout* .</span><span class="sxs-lookup"><span data-stu-id="3e137-158">By default, the StartIfNotIdle property of scheduled jobs is set to $True and Windows PowerShell ignores the *IdleDuration* and *IdleTimeout* values.</span></span>

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

### <span data-ttu-id="3e137-159">-IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="3e137-159">-IdleTimeout</span></span>
<span data-ttu-id="3e137-160">Anger hur länge datorn måste vara inaktiv innan jobbet startas.</span><span class="sxs-lookup"><span data-stu-id="3e137-160">Specifies how long the computer must be idle before the job starts.</span></span>
<span data-ttu-id="3e137-161">Standardvärdet är 10 minuter.</span><span class="sxs-lookup"><span data-stu-id="3e137-161">The default value is 10 minutes.</span></span>
<span data-ttu-id="3e137-162">Om datorn inte är inaktiv under den angivna tiden innan värdet för **idleTimeout** går ut, körs inte det schemalagda jobbet förrän nästa schemalagda tid, om det finns.</span><span class="sxs-lookup"><span data-stu-id="3e137-162">If the computer is not idle for the specified duration before the value of **IdleTimeout** expires, the scheduled job does not run until the next scheduled time, if any.</span></span>

<span data-ttu-id="3e137-163">Ange ett TimeSpan-objekt, till exempel ett som genereras av New-TimeSpan-cmdleten, eller ange ett värde i \<hours\> : \<minutes\> : \<seconds\> format som automatiskt konverteras till ett **TimeSpan** -objekt.</span><span class="sxs-lookup"><span data-stu-id="3e137-163">Enter a timespan object, such as one generated by the New-TimeSpan cmdlet, or enter a value in \<hours\>:\<minutes\>:\<seconds\> format that is automatically converted to a **TimeSpan** object.</span></span>

<span data-ttu-id="3e137-164">Använd parametern *StartIfIdle* om du vill aktivera det här värdet.</span><span class="sxs-lookup"><span data-stu-id="3e137-164">To enable this value, use the *StartIfIdle* parameter.</span></span>
<span data-ttu-id="3e137-165">Som standard är egenskapen StartIfNotIdle för schemalagda jobb inställd på $True och Windows PowerShell ignorerar värdena *IdleDuration* och *idleTimeout* .</span><span class="sxs-lookup"><span data-stu-id="3e137-165">By default, the StartIfNotIdle property of scheduled jobs is set to $True and Windows PowerShell ignores the *IdleDuration* and *IdleTimeout* values.</span></span>

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

### <span data-ttu-id="3e137-166">– InputObject</span><span class="sxs-lookup"><span data-stu-id="3e137-166">-InputObject</span></span>
<span data-ttu-id="3e137-167">Anger jobb alternativen.</span><span class="sxs-lookup"><span data-stu-id="3e137-167">Specifies the job options.</span></span>
<span data-ttu-id="3e137-168">Ange en variabel som innehåller **ScheduledJobOptions** -objekt eller Skriv ett kommando eller uttryck som hämtar **ScheduledJobOptions** -objekt, till exempel ett Get-ScheduledJobOption-kommando.</span><span class="sxs-lookup"><span data-stu-id="3e137-168">Enter a variable that contains **ScheduledJobOptions** objects or type a command or expression that gets **ScheduledJobOptions** objects, such as a Get-ScheduledJobOption command.</span></span>
<span data-ttu-id="3e137-169">Du kan också skicka ett **ScheduledJobOptions** -objekt till **set-ScheduledJobOption**.</span><span class="sxs-lookup"><span data-stu-id="3e137-169">You can also pipe a **ScheduledJobOptions** object to **Set-ScheduledJobOption**.</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="3e137-170">-MultipleInstancePolicy</span><span class="sxs-lookup"><span data-stu-id="3e137-170">-MultipleInstancePolicy</span></span>
<span data-ttu-id="3e137-171">Fastställer hur systemet svarar på en begäran om att starta en instans av ett schemalagt jobb medan en annan instans av jobbet körs.</span><span class="sxs-lookup"><span data-stu-id="3e137-171">Determines how the system responds to a request to start an instance of a scheduled job while another instance of the job is running.</span></span>
<span data-ttu-id="3e137-172">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="3e137-172">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="3e137-173">IgnoreNew.</span><span class="sxs-lookup"><span data-stu-id="3e137-173">IgnoreNew.</span></span>
<span data-ttu-id="3e137-174">Den nya jobb instansen ignoreras.</span><span class="sxs-lookup"><span data-stu-id="3e137-174">The new job instance is ignored.</span></span>
<span data-ttu-id="3e137-175">Detta är standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="3e137-175">This is the default value.</span></span>
- <span data-ttu-id="3e137-176">Via.</span><span class="sxs-lookup"><span data-stu-id="3e137-176">Parallel.</span></span>
<span data-ttu-id="3e137-177">Den nya jobb instansen startar omedelbart.</span><span class="sxs-lookup"><span data-stu-id="3e137-177">The new job instance starts immediately.</span></span>
- <span data-ttu-id="3e137-178">Köjobb.</span><span class="sxs-lookup"><span data-stu-id="3e137-178">Queue.</span></span>
<span data-ttu-id="3e137-179">Den nya jobb instansen startar så snart den aktuella instansen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="3e137-179">The new job instance starts as soon as the current instance completes.</span></span>
- <span data-ttu-id="3e137-180">StopExisting.</span><span class="sxs-lookup"><span data-stu-id="3e137-180">StopExisting.</span></span>
<span data-ttu-id="3e137-181">Den aktuella instansen av jobbet stoppas och den nya instansen startar.</span><span class="sxs-lookup"><span data-stu-id="3e137-181">The current instance of the job stop and the new instance starts.</span></span>

<span data-ttu-id="3e137-182">För att köra jobbet måste alla villkor för projektschemat uppfyllas.</span><span class="sxs-lookup"><span data-stu-id="3e137-182">To run the job, all conditions for the job schedule must be met.</span></span>
<span data-ttu-id="3e137-183">Om till exempel de villkor som anges av parametrarna *RequireNetwork* , *IdleDuration* och *idleTimeout* inte är uppfyllda, startas inte jobb instansen, oavsett värdet för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="3e137-183">For example, if the conditions that are set by the *RequireNetwork* , *IdleDuration* , and *IdleTimeout* parameters are not satisfied, the job instance is not started, regardless of the value of this parameter.</span></span>

```yaml
Type: Microsoft.PowerShell.ScheduledJob.TaskMultipleInstancePolicy
Parameter Sets: (All)
Aliases:
Accepted values: None, IgnoreNew, Parallel, Queue, StopExisting

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="3e137-184">– PassThru</span><span class="sxs-lookup"><span data-stu-id="3e137-184">-PassThru</span></span>
<span data-ttu-id="3e137-185">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="3e137-185">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="3e137-186">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="3e137-186">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="3e137-187">-RequireNetwork</span><span class="sxs-lookup"><span data-stu-id="3e137-187">-RequireNetwork</span></span>
<span data-ttu-id="3e137-188">Kör bara det schemalagda jobbet när nätverks anslutningar är tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="3e137-188">Runs the scheduled job only when network connections are available.</span></span>

<span data-ttu-id="3e137-189">Om du anger den här parametern och nätverket inte är tillgängligt vid den schemalagda start tiden, körs inte jobbet förrän nästa schemalagda start tid, om något.</span><span class="sxs-lookup"><span data-stu-id="3e137-189">If you specify this parameter and the network is not available at the scheduled start time, the job does not run until the next scheduled start time, if any.</span></span>

<span data-ttu-id="3e137-190">Parametern *RequireNetwork* anger värdet för egenskapen RunWithoutNetwork för schemalagda jobb till $false.</span><span class="sxs-lookup"><span data-stu-id="3e137-190">The *RequireNetwork* parameter sets the value of the RunWithoutNetwork property of scheduled jobs to $False.</span></span>

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

### <span data-ttu-id="3e137-191">-RestartOnIdleResume</span><span class="sxs-lookup"><span data-stu-id="3e137-191">-RestartOnIdleResume</span></span>
<span data-ttu-id="3e137-192">Startar om ett schemalagt jobb när datorn blir inaktiv.</span><span class="sxs-lookup"><span data-stu-id="3e137-192">Restarts a scheduled job when the computer becomes idle.</span></span>
<span data-ttu-id="3e137-193">Den här parametern fungerar med parametern *StopIfGoingOffIdle* , som pausar ett pågående schemalagt jobb om datorn blir aktiv (lämnar inaktivt läge).</span><span class="sxs-lookup"><span data-stu-id="3e137-193">This parameter works with the *StopIfGoingOffIdle* parameter, which suspends a running scheduled job if the computer becomes active (leaves the idle state).</span></span>

<span data-ttu-id="3e137-194">Parametern *RestartOnIdleResume* anger värdet för egenskapen RestartOnIdleResume för schemalagda jobb till $true.</span><span class="sxs-lookup"><span data-stu-id="3e137-194">The *RestartOnIdleResume* parameter sets the value of the RestartOnIdleResume property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="3e137-195">-RunElevated</span><span class="sxs-lookup"><span data-stu-id="3e137-195">-RunElevated</span></span>
<span data-ttu-id="3e137-196">Kör det schemalagda jobbet med behörigheterna för en medlem i gruppen Administratörer på den dator där jobbet körs.</span><span class="sxs-lookup"><span data-stu-id="3e137-196">Runs the scheduled job with the permissions of a member of the Administrators group on the computer on which the job runs.</span></span>

<span data-ttu-id="3e137-197">Om du vill aktivera ett schemalagt jobb som ska köras med administratörs behörighet använder du parametern *Credential* i Register-ScheduledJob för att ange explicita autentiseringsuppgifter för jobbet.</span><span class="sxs-lookup"><span data-stu-id="3e137-197">To enable a scheduled job to run with Administrator permissions, use the *Credential* parameter of Register-ScheduledJob to provide explicit credential for the job.</span></span>

<span data-ttu-id="3e137-198">Parametern **RunElevated** anger värdet för egenskapen **RunElevated** för schemalagda jobb till true.</span><span class="sxs-lookup"><span data-stu-id="3e137-198">The **RunElevated** parameter sets the value of the **RunElevated** property of scheduled jobs to True.</span></span>

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

### <span data-ttu-id="3e137-199">-StartIfIdle</span><span class="sxs-lookup"><span data-stu-id="3e137-199">-StartIfIdle</span></span>
<span data-ttu-id="3e137-200">Startar det schemalagda jobbet om datorn har varit inaktiv under den tid som anges av parametern **IdleDuration** innan den tid som anges av parametern *idleTimeout* upphör att gälla.</span><span class="sxs-lookup"><span data-stu-id="3e137-200">Starts the scheduled job if the computer has been idle for the time specified by the **IdleDuration** parameter before the time specified by the *IdleTimeout* parameter expires.</span></span>

<span data-ttu-id="3e137-201">Som standard ignoreras parametrarna *IdleDuration* och *idleTimeout* och jobbet startar vid den schemalagda start tiden även om datorn är upptagen.</span><span class="sxs-lookup"><span data-stu-id="3e137-201">By default, the *IdleDuration* and *IdleTimeout* parameters are ignored and the job starts at the scheduled start time even if the computer is busy.</span></span>

<span data-ttu-id="3e137-202">Om du anger den här parametern och datorn är upptagen (inte inaktiv) vid den schemalagda start tiden, körs inte jobbet förrän nästa schemalagda start tid, om det finns någon.</span><span class="sxs-lookup"><span data-stu-id="3e137-202">If you specify this parameter and the computer is busy (not idle) at the scheduled start time, the job does not run until the next scheduled start time, if any.</span></span>

<span data-ttu-id="3e137-203">Parametern *StartIfIdle* anger värdet för egenskapen **StartIfNotIdle** för schemalagda jobb till false.</span><span class="sxs-lookup"><span data-stu-id="3e137-203">The *StartIfIdle* parameter sets the value of the **StartIfNotIdle** property of scheduled jobs to False.</span></span>

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

### <span data-ttu-id="3e137-204">-StartIfOnBattery</span><span class="sxs-lookup"><span data-stu-id="3e137-204">-StartIfOnBattery</span></span>
<span data-ttu-id="3e137-205">Startar det schemalagda jobbet även om datorn körs på batterier vid den schemalagda start tiden.</span><span class="sxs-lookup"><span data-stu-id="3e137-205">Starts the scheduled job even if the computer is running on batteries at the scheduled start time.</span></span>
<span data-ttu-id="3e137-206">Standardvärdet är false.</span><span class="sxs-lookup"><span data-stu-id="3e137-206">The default value is False.</span></span>

<span data-ttu-id="3e137-207">Parametern *StartIfOnBattery* anger värdet för egenskapen **StartIfOnBatteries** för schemalagda jobb till $true.</span><span class="sxs-lookup"><span data-stu-id="3e137-207">The *StartIfOnBattery* parameter sets the value of the **StartIfOnBatteries** property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="3e137-208">-StopIfGoingOffIdle</span><span class="sxs-lookup"><span data-stu-id="3e137-208">-StopIfGoingOffIdle</span></span>
<span data-ttu-id="3e137-209">Pausar ett pågående schemalagt jobb om datorn blir aktiv (inte inaktiv) medan jobbet körs.</span><span class="sxs-lookup"><span data-stu-id="3e137-209">Suspends a running scheduled job if the computer becomes active (not idle) while the job is running.</span></span>

<span data-ttu-id="3e137-210">Som standard är ett schemalagt jobb som pausas när datorn aktive ras när datorn blir inaktiv igen.</span><span class="sxs-lookup"><span data-stu-id="3e137-210">By default, a scheduled job that is suspended when the computer becomes active resumes when the computer becomes idle again.</span></span>
<span data-ttu-id="3e137-211">Om du vill ändra det här standard beteendet använder du parametern *RestartOnIdleResume* .</span><span class="sxs-lookup"><span data-stu-id="3e137-211">To change this default behavior, use the *RestartOnIdleResume* parameter.</span></span>

<span data-ttu-id="3e137-212">Parametern *StopIfGoingOffIdle* anger värdet för egenskapen StopIfGoingOffIdle för schemalagda jobb till $true.</span><span class="sxs-lookup"><span data-stu-id="3e137-212">The *StopIfGoingOffIdle* parameter sets the value of the StopIfGoingOffIdle property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="3e137-213">-WakeToRun</span><span class="sxs-lookup"><span data-stu-id="3e137-213">-WakeToRun</span></span>
<span data-ttu-id="3e137-214">Aktiverar datorn från vilo läge eller vilo läge vid den schemalagda start tiden så att den kan köra jobbet.</span><span class="sxs-lookup"><span data-stu-id="3e137-214">Wakes the computer from a Hibernate or Sleep state at the scheduled start time so it can run the job.</span></span>
<span data-ttu-id="3e137-215">Som standard körs inte jobbet om datorn är i vilo läge eller vilo läge vid den schemalagda start tiden.</span><span class="sxs-lookup"><span data-stu-id="3e137-215">By default, if the computer is in a Hibernate or Sleep state at the scheduled start time, the job does not run.</span></span>

<span data-ttu-id="3e137-216">Parametern *WakeToRun* anger värdet för egenskapen WakeToRun för schemalagda jobb till $true.</span><span class="sxs-lookup"><span data-stu-id="3e137-216">The *WakeToRun* parameter sets the value of the WakeToRun property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="3e137-217">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="3e137-217">CommonParameters</span></span>
<span data-ttu-id="3e137-218">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="3e137-218">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="3e137-219">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="3e137-219">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="3e137-220">INDATA</span><span class="sxs-lookup"><span data-stu-id="3e137-220">INPUTS</span></span>

### <span data-ttu-id="3e137-221">Microsoft. PowerShell. ScheduledJob. ScheduledJobOptions</span><span class="sxs-lookup"><span data-stu-id="3e137-221">Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions</span></span>
<span data-ttu-id="3e137-222">Du kan skicka ett objekt med alternativ för schemalagda jobb till **set-ScheduledJobOption**.</span><span class="sxs-lookup"><span data-stu-id="3e137-222">You can pipe a scheduled job options object to **Set-ScheduledJobOption**.</span></span>

## <span data-ttu-id="3e137-223">UTDATA</span><span class="sxs-lookup"><span data-stu-id="3e137-223">OUTPUTS</span></span>

### <span data-ttu-id="3e137-224">Ingen eller Microsoft. PowerShell. ScheduledJob. ScheduledJobOptions</span><span class="sxs-lookup"><span data-stu-id="3e137-224">None or Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions</span></span>
<span data-ttu-id="3e137-225">När du använder parametern *Passthru* returnerar **set-ScheduledJobOption** de jobb alternativ som ändrades.</span><span class="sxs-lookup"><span data-stu-id="3e137-225">When you use the *Passthru* parameter, **Set-ScheduledJobOption** returns the job options that were changed.</span></span>
<span data-ttu-id="3e137-226">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="3e137-226">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="3e137-227">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="3e137-227">NOTES</span></span>

## <span data-ttu-id="3e137-228">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="3e137-228">RELATED LINKS</span></span>

[<span data-ttu-id="3e137-229">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3e137-229">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="3e137-230">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3e137-230">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="3e137-231">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3e137-231">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="3e137-232">Aktivera – JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3e137-232">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="3e137-233">Aktivera – ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3e137-233">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="3e137-234">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3e137-234">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="3e137-235">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3e137-235">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="3e137-236">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="3e137-236">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="3e137-237">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3e137-237">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="3e137-238">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="3e137-238">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="3e137-239">Registrera – ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3e137-239">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="3e137-240">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3e137-240">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="3e137-241">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="3e137-241">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="3e137-242">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3e137-242">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="3e137-243">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="3e137-243">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="3e137-244">Avregistrera-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="3e137-244">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
