---
external help file: Microsoft.PowerShell.ScheduledJob.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSScheduledJob
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/new-scheduledjoboption?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-ScheduledJobOption
ms.openlocfilehash: 35ada8d5aaa6a6c1fdc74a089308aefe13598b10
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264644"
---
# <span data-ttu-id="0f0ba-103">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="0f0ba-103">New-ScheduledJobOption</span></span>

## <span data-ttu-id="0f0ba-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="0f0ba-104">SYNOPSIS</span></span>
<span data-ttu-id="0f0ba-105">Skapar ett objekt som innehåller avancerade alternativ för ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-105">Creates an object that contains advanced options for a scheduled job.</span></span>

## <span data-ttu-id="0f0ba-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="0f0ba-106">SYNTAX</span></span>

```
New-ScheduledJobOption [-RunElevated] [-HideInTaskScheduler] [-RestartOnIdleResume]
 [-MultipleInstancePolicy <TaskMultipleInstancePolicy>] [-DoNotAllowDemandStart] [-RequireNetwork]
 [-StopIfGoingOffIdle] [-WakeToRun] [-ContinueIfGoingOnBattery] [-StartIfOnBattery] [-IdleTimeout <TimeSpan>]
 [-IdleDuration <TimeSpan>] [-StartIfIdle] [<CommonParameters>]
```

## <span data-ttu-id="0f0ba-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="0f0ba-107">DESCRIPTION</span></span>
<span data-ttu-id="0f0ba-108">Cmdlet: en **New-ScheduledJobOption** skapar ett objekt som innehåller avancerade alternativ för ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-108">The **New-ScheduledJobOption** cmdlet creates an object that contains advanced options for a scheduled job.</span></span>

<span data-ttu-id="0f0ba-109">Du kan använda **ScheduledJobOptions** -objektet som **New-ScheduledJobOption** returnerar för att ange jobb alternativ för ett nytt eller befintligt schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-109">You can use the **ScheduledJobOptions** object that **New-ScheduledJobOption** returns to set job options for a new or existing scheduled job.</span></span>
<span data-ttu-id="0f0ba-110">Du kan också ange jobb alternativ genom att använda Get-ScheduledJobOption cmdlet för att hämta jobb alternativen för ett befintligt schemalagt jobb eller genom att använda ett värde för hash-tabellen för att representera jobb alternativen.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-110">Alternatively, you can set job options by using the Get-ScheduledJobOption cmdlet to get the job options of an existing scheduled job or by using a hash table value to represent the job options.</span></span>

<span data-ttu-id="0f0ba-111">Utan parametrar genererar **New-ScheduledJobOption** ett objekt som innehåller standardvärdena för alla alternativ.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-111">Without parameters, **New-ScheduledJobOption** generates an object that contains the default values for all of the options.</span></span>
<span data-ttu-id="0f0ba-112">Eftersom alla egenskaper utom jobb definitionen-egenskapen kan redige ras kan du använda det resulterande objektet som mall och skapa standard alternativ objekt för ditt företag.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-112">Because all of the properties except for the JobDefinition property can be edited, you can use the resulting object as a template, and create standard option objects for your enterprise.</span></span>

<span data-ttu-id="0f0ba-113">När du skapar schemalagda jobb och anger alternativ för schemalagda jobb granskar du standardvärdena för alla alternativ för schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-113">When creating scheduled jobs and setting scheduled job options, review the default values of all scheduled job options.</span></span>
<span data-ttu-id="0f0ba-114">Schemalagda jobb körs bara när alla villkor som har angetts för körningen är uppfyllda.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-114">Scheduled jobs run only when all conditions set for their execution are satisfied.</span></span>

<span data-ttu-id="0f0ba-115">**New-ScheduledJobOption** är en samling jobb schemaläggnings-cmdletar i PSScheduledJob-modulen som ingår i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-115">**New-ScheduledJobOption** is one of a collection of job scheduling cmdlets in the PSScheduledJob module that is included in Windows PowerShell.</span></span>

<span data-ttu-id="0f0ba-116">Mer information om schemalagda jobb finns i avsnittet om ämnen i PSScheduledJob-modulen.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-116">For more information about Scheduled Jobs, see the About topics in the PSScheduledJob module.</span></span>
<span data-ttu-id="0f0ba-117">Importera modulen PSScheduledJob och skriv sedan: `Get-Help about_Scheduled*` eller se about_Scheduled_Jobs.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-117">Import the PSScheduledJob module and then type: `Get-Help about_Scheduled*` or see about_Scheduled_Jobs.</span></span>

<span data-ttu-id="0f0ba-118">Den här cmdleten introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-118">This cmdlet was introduced in Windows PowerShell 3.0.</span></span>

## <span data-ttu-id="0f0ba-119">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="0f0ba-119">EXAMPLES</span></span>

### <span data-ttu-id="0f0ba-120">Exempel 1: skapa ett alternativ objekt för schemalagda jobb med standardvärden</span><span class="sxs-lookup"><span data-stu-id="0f0ba-120">Example 1: Create a scheduled job option object with default values</span></span>

```
PS C:\> New-ScheduledJobOption
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
RunWithoutNetwork      : True
DoNotAllowDemandStart  : False
MultipleInstancePolicy : Ignore
NewJobDefinition       :
```

<span data-ttu-id="0f0ba-121">Det här kommandot skapar ett alternativ objekt för schemalagda jobb som har alla standardvärden.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-121">This command creates a scheduled job option object that has all of the default values.</span></span>

### <span data-ttu-id="0f0ba-122">Exempel 2: skapa ett alternativ objekt för schemalagda jobb med anpassade värden</span><span class="sxs-lookup"><span data-stu-id="0f0ba-122">Example 2: Create a scheduled job option object with custom values</span></span>

```
PS C:\> New-ScheduledJobOption -RequireNetwork -StartIfOnBattery
StartIfOnBatteries     : True
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
MultipleInstancePolicy : Ignore
NewJobDefinition       :
```

<span data-ttu-id="0f0ba-123">Följande kommando skapar ett schemalagt jobb objekt som kräver nätverket och kör det schemalagda jobbet även om datorn inte är ansluten till nätström.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-123">The following command creates a scheduled job object that requires the network and runs the scheduled job even if the computer is not connected to AC power.</span></span>

<span data-ttu-id="0f0ba-124">Utdata visar att *RequireNetwork* -parametern har ändrat värdet för egenskapen RunWithoutNetwork till $false och *StartIfOnBattery* -parametern ändrade värdet för StartIfOnBatteries-egenskapen till $true.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-124">The output shows that the *RequireNetwork* parameter changed the value of the RunWithoutNetwork property to $False and the *StartIfOnBattery* parameter changed the value of the StartIfOnBatteries property to $True.</span></span>

### <span data-ttu-id="0f0ba-125">Exempel 3: Ange alternativ för ett nytt schemalagt jobb</span><span class="sxs-lookup"><span data-stu-id="0f0ba-125">Example 3: Set options for a new scheduled job</span></span>

```
The first command creates a **ScheduledJobOptions** object with the *RunElevated* parameter. It saves the object in the $RunAsAdmin variable.
PS C:\> $RunAsAdmin = New-ScheduledJobOption -RunElevated

The second command uses the Register-ScheduledJob cmdlet to create a new scheduled job. The value of the *ScheduledJobOption* parameter is the option object in the value of the $RunAsAdmin variable.
PS C:\> Register-ScheduledJob -Name Backup -FilePath D:\Scripts\Backup.ps1 -Trigger $Mondays -ScheduledJobOption $RunAsAdmin

The third command uses the Get-ScheduledJobOption cmdlet to get the job options of the Backup scheduled job.The cmdlet output shows that the RunElevated property is set to $True and the JobDefinition property of the job option object is now populated with the scheduled job object for the Backup scheduled job.
PS C:\> Get-ScheduledJobOption -Name Backup
StartIfOnBatteries     : False
StopIfGoingOnBatteries : True
WakeToRun              : False
StartIfNotIdle         : True
StopIfGoingOffIdle     : False
RestartOnIdleResume    : False
IdleDuration           : 00:10:00
IdleTimeout            : 01:00:00
ShowInTaskScheduler    : True
RunElevated            : True
RunWithoutNetwork      : True
DoNotAllowDemandStart  : False
MultipleInstancePolicy : IgnoreNew
JobDefinition          : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

<span data-ttu-id="0f0ba-126">Det här exemplet visar hur du använder **ScheduledJobOptions** -objektet som **New-ScheduledJobOption** returnerar för att ange alternativ för ett nytt schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-126">This example shows how to use the **ScheduledJobOptions** object that **New-ScheduledJobOption** returns to set the options for a new scheduled job.</span></span>

### <span data-ttu-id="0f0ba-127">Exempel 4: sortera egenskaperna för ett alternativ objekt för schemalagda jobb</span><span class="sxs-lookup"><span data-stu-id="0f0ba-127">Example 4: Sort the properties of a scheduled job option object</span></span>

```
PS C:\> $Options = New-ScheduledJobOption -WakeToRun
PS C:\> $Options.PSObject.Properties | Sort-Object -Property Name | Format-Table -Property Name, Value -Autosize
Name                       Value
----                       -----
DoNotAllowDemandStart      False
IdleDuration            00:10:00
IdleTimeout             01:00:00
JobDefinition
MultipleInstancePolicy IgnoreNew
RestartOnIdleResume        False
RunElevated                False
RunWithoutNetwork           True
ShowInTaskScheduler         True
StartIfNotIdle              True
StartIfOnBatteries         False
StopIfGoingOffIdle         False
StopIfGoingOnBatteries      True
WakeToRun                   True
```

<span data-ttu-id="0f0ba-128">Det här exemplet visar hur du sorterar egenskaperna för ett **ScheduledJobOptions** -objekt i alfabetisk ordning för enkel läsning.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-128">This example shows how to sort the properties of a **ScheduledJobOptions** object in alphabetical order for easy reading.</span></span>

<span data-ttu-id="0f0ba-129">Det första kommandot använder cmdleten **New-ScheduledJobOption** för att skapa ett **ScheduledJobOptions** -objekt.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-129">The first command uses the **New-ScheduledJobOption** cmdlet to create a **ScheduledJobOptions** object.</span></span>
<span data-ttu-id="0f0ba-130">Kommandot använder parametern *WakeToRun* och sparar det resulterande objektet i variabeln $Options.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-130">The command uses the *WakeToRun* parameter and saves the resulting object in the $Options variable.</span></span>

<span data-ttu-id="0f0ba-131">För att hämta egenskaperna för $Options som objekt använder det andra kommandot egenskapen **PSObject** för alla Windows PowerShell-objekt och dess egenskap egenskaper.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-131">To get the properties of $Options as objects, the second command uses the **PSObject** property of all Windows PowerShell objects and its Properties property.</span></span>
<span data-ttu-id="0f0ba-132">Kommandot rör sedan egenskaps objekt till Sort-Object-cmdlet, som sorterar egenskaperna i bokstavs ordning efter namn och sedan till Format-Table-cmdleten, som visar namn och värden för egenskaperna i en tabell.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-132">The command then pipes the property objects to the Sort-Object cmdlet, which sorts the properties in alphabetical order by name, and then to the Format-Table cmdlet, which displays the names and values of the properties in a table.</span></span>

<span data-ttu-id="0f0ba-133">Det här formatet gör det mycket enklare att hitta egenskapen WakeToRun för **ScheduledJobOptions** -objektet i $Options och för att kontrol lera att dess värde har ändrats från $False till $true.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-133">This format makes it much easier to find the WakeToRun property of the **ScheduledJobOptions** object in $Options and to verify that its value was changed from $False to $True.</span></span>

## <span data-ttu-id="0f0ba-134">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="0f0ba-134">PARAMETERS</span></span>

### <span data-ttu-id="0f0ba-135">-ContinueIfGoingOnBattery</span><span class="sxs-lookup"><span data-stu-id="0f0ba-135">-ContinueIfGoingOnBattery</span></span>
<span data-ttu-id="0f0ba-136">Stoppa inte det schemalagda jobbet om datorn växlar till batteri drift (koppla från växel ström) medan jobbet körs.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-136">Do not stop the scheduled job if the computer switches to battery power (disconnects from AC power) while the job is running.</span></span>
<span data-ttu-id="0f0ba-137">Schemalagda jobb stoppas som standard när datorn kopplas från växel ström.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-137">By default, scheduled jobs stop when the computer disconnects from AC power.</span></span>

<span data-ttu-id="0f0ba-138">Parametern *ContinueIfGoingOnBattery* anger värdet för egenskapen StopIfGoingOnBatteries för schemalagda jobb till $true.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-138">The *ContinueIfGoingOnBattery* parameter sets the value of the StopIfGoingOnBatteries property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="0f0ba-139">-DoNotAllowDemandStart</span><span class="sxs-lookup"><span data-stu-id="0f0ba-139">-DoNotAllowDemandStart</span></span>
<span data-ttu-id="0f0ba-140">Starta bara jobbet när det utlöses.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-140">Start the job only when it is triggered.</span></span>
<span data-ttu-id="0f0ba-141">Användare kan inte starta jobbet manuellt, t. ex. med hjälp av körnings funktionen i Schemaläggaren.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-141">Users cannot start the job manually, such as by using the Run feature in Task Scheduler.</span></span>

<span data-ttu-id="0f0ba-142">Den här parametern påverkar endast Schemaläggaren.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-142">This parameter only affects Task Scheduler.</span></span>
<span data-ttu-id="0f0ba-143">Den förhindrar inte att användare använder Start-Job cmdlet för att starta jobbet.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-143">It does not prevents users from using the Start-Job cmdlet to start the job.</span></span>

<span data-ttu-id="0f0ba-144">Parametern *DoNotAllowDemandStart* anger värdet för egenskapen DoNotAllowDemandStart för schemalagda jobb till $true.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-144">The *DoNotAllowDemandStart* parameter sets the value of the DoNotAllowDemandStart property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="0f0ba-145">-HideInTaskScheduler</span><span class="sxs-lookup"><span data-stu-id="0f0ba-145">-HideInTaskScheduler</span></span>
<span data-ttu-id="0f0ba-146">Visa inte jobbet i Schemaläggaren.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-146">Do not display the job in Task Scheduler.</span></span>
<span data-ttu-id="0f0ba-147">Det här värdet påverkar endast den dator där jobbet körs.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-147">This value affects only the computer on which the job runs.</span></span>
<span data-ttu-id="0f0ba-148">Som standard visas schemalagda aktiviteter i Schemaläggaren.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-148">By default, scheduled tasks appear in Task Scheduler.</span></span>

<span data-ttu-id="0f0ba-149">Även om en aktivitet är dold kan användarna Visa uppgiften genom att välja Visa dolda aktiviteter i Schemaläggaren.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-149">Even if a task is hidden, users can display the task by selecting the Show hidden tasks view option in Task Scheduler.</span></span>

<span data-ttu-id="0f0ba-150">Parametern *HideInTaskScheduler* anger värdet för egenskapen ShowInTaskScheduler för schemalagda jobb till $false.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-150">The *HideInTaskScheduler* parameter sets the value of the ShowInTaskScheduler property of scheduled jobs to $False.</span></span>

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

### <span data-ttu-id="0f0ba-151">-IdleDuration</span><span class="sxs-lookup"><span data-stu-id="0f0ba-151">-IdleDuration</span></span>
<span data-ttu-id="0f0ba-152">Anger hur länge datorn måste vara inaktiv innan jobbet startas.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-152">Specifies how long the computer must be idle before the job starts.</span></span>
<span data-ttu-id="0f0ba-153">Standardvärdet är 10 minuter.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-153">The default value is 10 minutes.</span></span>
<span data-ttu-id="0f0ba-154">Om datorn inte är inaktiv under den angivna tiden innan värdet för *idleTimeout* går ut, körs inte det schemalagda jobbet förrän nästa schemalagda tid, om det finns.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-154">If the computer is not idle for the specified duration before the value of *IdleTimeout* expires, the scheduled job does not run until the next scheduled time, if any.</span></span>

<span data-ttu-id="0f0ba-155">Ange ett **TimeSpan** -objekt, till exempel ett som genereras av New-TimeSpan-cmdleten, eller ange ett värde i \<hours\> : \<minutes\> : \<seconds\> format som automatiskt konverteras till ett **TimeSpan** -objekt.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-155">Enter a **TimeSpan** object, such as one generated by the New-TimeSpan cmdlet, or enter a value in \<hours\>:\<minutes\>:\<seconds\> format  that is automatically converted to a **TimeSpan** object.</span></span>

<span data-ttu-id="0f0ba-156">Använd parametern *StartIfIdle* om du vill aktivera det här värdet.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-156">To enable this value, use the *StartIfIdle* parameter.</span></span>
<span data-ttu-id="0f0ba-157">Som standard är egenskapen StartIfNotIdle för schemalagda jobb inställd på $True och Windows PowerShell ignorerar värdena *IdleDuration* och *idleTimeout* .</span><span class="sxs-lookup"><span data-stu-id="0f0ba-157">By default, the StartIfNotIdle property of scheduled jobs is set to $True and Windows PowerShell ignores the *IdleDuration* and *IdleTimeout* values.</span></span>

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

### <span data-ttu-id="0f0ba-158">-IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="0f0ba-158">-IdleTimeout</span></span>
<span data-ttu-id="0f0ba-159">Anger hur länge det schemalagda jobbet väntar på att datorn ska vara inaktiv.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-159">Specifies how long the scheduled job waits for the computer to be idle.</span></span>
<span data-ttu-id="0f0ba-160">Om tids gränsen går ut innan datorn förblir inaktiv under den tids period som anges av parametern *IdleDuration* , körs inte jobbet förrän nästa schemalagda tid, om det finns.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-160">If this timeout expires before the computer remains idle for the time period that is specified by the *IdleDuration* parameter, the job does not run until the next scheduled time, if any.</span></span>
<span data-ttu-id="0f0ba-161">Standardvärdet är en timme.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-161">The default value is one hour.</span></span>

<span data-ttu-id="0f0ba-162">Ange ett **TimeSpan** -objekt, till exempel ett som genereras av New-TimeSpan-cmdleten, eller ange ett värde i \<hours\> : \<minutes\> : \<seconds\> format som automatiskt konverteras till ett **TimeSpan** -objekt.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-162">Enter a **TimeSpan** object, such as one generated by the New-TimeSpan cmdlet, or enter a value in \<hours\>:\<minutes\>:\<seconds\> format that is automatically converted to a **TimeSpan** object.</span></span>

<span data-ttu-id="0f0ba-163">Använd parametern *StartIfIdle* om du vill aktivera det här värdet.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-163">To enable this value, use the *StartIfIdle* parameter.</span></span>
<span data-ttu-id="0f0ba-164">Som standard är egenskapen StartIfNotIdle för schemalagda jobb inställd på $True och Windows PowerShell ignorerar värdena *IdleDuration* och *idleTimeout* .</span><span class="sxs-lookup"><span data-stu-id="0f0ba-164">By default, the StartIfNotIdle property of scheduled jobs is set to $True and Windows PowerShell ignores the *IdleDuration* and *IdleTimeout* values.</span></span>

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

### <span data-ttu-id="0f0ba-165">-MultipleInstancePolicy</span><span class="sxs-lookup"><span data-stu-id="0f0ba-165">-MultipleInstancePolicy</span></span>
<span data-ttu-id="0f0ba-166">Fastställer hur systemet svarar på en begäran om att starta en instans av ett schemalagt jobb medan en annan instans av jobbet körs.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-166">Determines how the system responds to a request to start an instance of a scheduled job while another instance of the job is running.</span></span>
<span data-ttu-id="0f0ba-167">Standardvärdet är IgnoreNew.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-167">The default value is IgnoreNew.</span></span>
<span data-ttu-id="0f0ba-168">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="0f0ba-168">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="0f0ba-169">IgnoreNew.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-169">IgnoreNew.</span></span>
<span data-ttu-id="0f0ba-170">Den nya jobb instansen ignoreras.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-170">The new job instance is ignored.</span></span>
- <span data-ttu-id="0f0ba-171">Via.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-171">Parallel.</span></span>
<span data-ttu-id="0f0ba-172">Den nya jobb instansen startar omedelbart.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-172">The new job instance starts immediately.</span></span>
- <span data-ttu-id="0f0ba-173">Köjobb.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-173">Queue.</span></span>
<span data-ttu-id="0f0ba-174">Den nya jobb instansen startar så snart den aktuella instansen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-174">The new job instance starts as soon as the current instance completes.</span></span>
- <span data-ttu-id="0f0ba-175">StopExisting.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-175">StopExisting.</span></span>
<span data-ttu-id="0f0ba-176">Den aktuella instansen av jobbet stoppas och den nya instansen startar.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-176">The current instance of the job stops and the new instance starts.</span></span>

<span data-ttu-id="0f0ba-177">För att köra jobbet måste alla villkor för projektschemat uppfyllas.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-177">To run the job, all conditions for the job schedule must be met.</span></span>
<span data-ttu-id="0f0ba-178">Om till exempel de villkor som anges av parametrarna *RequireNetwork* , *IdleDuration* och *idleTimeout* inte är uppfyllda, startas inte jobb instansen, oavsett värdet för den här parametern.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-178">For example, if the conditions that are set by the *RequireNetwork* , *IdleDuration* , and *IdleTimeout* parameters are not satisfied, the job instance is not started, regardless of the value of this parameter.</span></span>

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

### <span data-ttu-id="0f0ba-179">-RequireNetwork</span><span class="sxs-lookup"><span data-stu-id="0f0ba-179">-RequireNetwork</span></span>
<span data-ttu-id="0f0ba-180">Kör bara det schemalagda jobbet när nätverks anslutningar är tillgängliga.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-180">Runs the scheduled job only when network connections are available.</span></span>

<span data-ttu-id="0f0ba-181">Om du anger den här parametern och nätverket inte är tillgängligt vid den schemalagda start tiden, körs inte jobbet förrän nästa schemalagda start tid, om något.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-181">If you specify this parameter and the network is not available at the scheduled start time, the job does not run until the next scheduled start time, if any.</span></span>

<span data-ttu-id="0f0ba-182">Parametern *RequireNetwork* anger värdet för egenskapen RunWithoutNetwork för schemalagda jobb till $false.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-182">The *RequireNetwork* parameter sets the value of the RunWithoutNetwork property of scheduled jobs to $False.</span></span>

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

### <span data-ttu-id="0f0ba-183">-RestartOnIdleResume</span><span class="sxs-lookup"><span data-stu-id="0f0ba-183">-RestartOnIdleResume</span></span>
<span data-ttu-id="0f0ba-184">Startar om ett schemalagt jobb när datorn blir inaktiv.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-184">Restarts a scheduled job when the computer becomes idle.</span></span>
<span data-ttu-id="0f0ba-185">Den här parametern fungerar med parametern *StopIfGoingOffIdle* , som pausar ett pågående schemalagt jobb om datorn blir aktiv (lämnar inaktivt läge).</span><span class="sxs-lookup"><span data-stu-id="0f0ba-185">This parameter works with the *StopIfGoingOffIdle* parameter, which suspends a running scheduled job if the computer becomes active (leaves the idle state).</span></span>

<span data-ttu-id="0f0ba-186">Parametern *RestartOnIdleResume* anger värdet för egenskapen RestartOnIdleResume för schemalagda jobb till $true.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-186">The *RestartOnIdleResume* parameter sets the value of the RestartOnIdleResume property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="0f0ba-187">-RunElevated</span><span class="sxs-lookup"><span data-stu-id="0f0ba-187">-RunElevated</span></span>
<span data-ttu-id="0f0ba-188">Kör det schemalagda jobbet med behörigheterna för en medlem i gruppen Administratörer på den dator där jobbet körs.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-188">Runs the scheduled job with the permissions of a member of the Administrators group on the computer on which the job runs.</span></span>

<span data-ttu-id="0f0ba-189">Om du vill aktivera ett schemalagt jobb som ska köras med administratörs behörighet använder du parametern *Credential* i Register-ScheduledJob för att ange explicita autentiseringsuppgifter för jobbet.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-189">To enable a scheduled job to run with Administrator permissions, use the *Credential* parameter of Register-ScheduledJob to provide explicit credential for the job.</span></span>

<span data-ttu-id="0f0ba-190">Parametern *RunElevated* anger värdet för egenskapen RunElevated för schemalagda jobb till $true.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-190">The *RunElevated* parameter sets the value of the RunElevated property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="0f0ba-191">-StartIfIdle</span><span class="sxs-lookup"><span data-stu-id="0f0ba-191">-StartIfIdle</span></span>
<span data-ttu-id="0f0ba-192">Startar det schemalagda jobbet om datorn har varit inaktiv under den tid som anges av parametern *IdleDuration* innan den tid som anges av parametern *idleTimeout* upphör att gälla.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-192">Starts the scheduled job if the computer has been idle for the time specified by the *IdleDuration* parameter before the time specified by the *IdleTimeout* parameter expires.</span></span>

<span data-ttu-id="0f0ba-193">Som standard ignoreras parametrarna *IdleDuration* och *idleTimeout* och jobbet startar vid den schemalagda start tiden även om datorn är upptagen.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-193">By default, the *IdleDuration* and *IdleTimeout* parameters are ignored and the job starts at the scheduled start time even if the computer is busy.</span></span>

<span data-ttu-id="0f0ba-194">Om du anger den här parametern och datorn är upptagen (inte inaktiv) vid den schemalagda start tiden, körs inte jobbet förrän nästa schemalagda start tid, om det finns någon.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-194">If you specify this parameter and the computer is busy (not idle) at the scheduled start time, the job does not run until the next scheduled start time, if any.</span></span>

<span data-ttu-id="0f0ba-195">Parametern *StartIfIdle* anger värdet för egenskapen StartIfNotIdle för schemalagda jobb till $false.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-195">The *StartIfIdle* parameter sets the value of the StartIfNotIdle property of scheduled jobs to $False.</span></span>

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

### <span data-ttu-id="0f0ba-196">-StartIfOnBattery</span><span class="sxs-lookup"><span data-stu-id="0f0ba-196">-StartIfOnBattery</span></span>
<span data-ttu-id="0f0ba-197">Startar det schemalagda jobbet även om datorn körs på batterier vid den schemalagda start tiden.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-197">Starts the scheduled job even if the computer is running on batteries at the scheduled start time.</span></span>
<span data-ttu-id="0f0ba-198">Standardvärdet är $False.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-198">The default value is $False.</span></span>

<span data-ttu-id="0f0ba-199">Parametern *StartIfOnBattery* anger värdet för egenskapen StartIfOnBatteries för schemalagda jobb till $true.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-199">The *StartIfOnBattery* parameter sets the value of the StartIfOnBatteries property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="0f0ba-200">-StopIfGoingOffIdle</span><span class="sxs-lookup"><span data-stu-id="0f0ba-200">-StopIfGoingOffIdle</span></span>
<span data-ttu-id="0f0ba-201">Pausar ett pågående schemalagt jobb om datorn blir aktiv (inte inaktiv) medan jobbet körs.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-201">Suspends a running scheduled job if the computer becomes active (not idle) while the job is running.</span></span>

<span data-ttu-id="0f0ba-202">Som standard är ett schemalagt jobb som pausas när datorn aktive ras när datorn blir inaktiv igen.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-202">By default, a scheduled job that is suspended when the computer becomes active resumes when the computer becomes idle again.</span></span>
<span data-ttu-id="0f0ba-203">Om du vill ändra det här standard beteendet använder du parametern *RestartOnIdleResume* .</span><span class="sxs-lookup"><span data-stu-id="0f0ba-203">To change this default behavior, use the *RestartOnIdleResume* parameter.</span></span>

<span data-ttu-id="0f0ba-204">Parametern *StopIfGoingOffIdle* anger värdet för egenskapen StopIfGoingOffIdle för schemalagda jobb till $true.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-204">The *StopIfGoingOffIdle* parameter sets the value of the StopIfGoingOffIdle property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="0f0ba-205">-WakeToRun</span><span class="sxs-lookup"><span data-stu-id="0f0ba-205">-WakeToRun</span></span>
<span data-ttu-id="0f0ba-206">Aktiverar datorn från vilo läge eller vilo läge vid den schemalagda start tiden så att den kan köra jobbet.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-206">Wakes the computer from a Hibernate or Sleep state at the scheduled start time so it can run the job.</span></span>
<span data-ttu-id="0f0ba-207">Som standard körs inte jobbet om datorn är i vilo läge eller vilo läge vid den schemalagda start tiden.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-207">By default, if the computer is in a Hibernate or Sleep state at the scheduled start time, the job does not run.</span></span>

<span data-ttu-id="0f0ba-208">Parametern *WakeToRun* anger värdet för egenskapen WakeToRun för schemalagda jobb till $true.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-208">The *WakeToRun* parameter sets the value of the WakeToRun property of scheduled jobs to $True.</span></span>

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

### <span data-ttu-id="0f0ba-209">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="0f0ba-209">CommonParameters</span></span>
<span data-ttu-id="0f0ba-210">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-210">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="0f0ba-211">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="0f0ba-211">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="0f0ba-212">INDATA</span><span class="sxs-lookup"><span data-stu-id="0f0ba-212">INPUTS</span></span>

### <span data-ttu-id="0f0ba-213">Inget</span><span class="sxs-lookup"><span data-stu-id="0f0ba-213">None</span></span>
<span data-ttu-id="0f0ba-214">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-214">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="0f0ba-215">UTDATA</span><span class="sxs-lookup"><span data-stu-id="0f0ba-215">OUTPUTS</span></span>

### <span data-ttu-id="0f0ba-216">Microsoft. PowerShell. ScheduledJob. ScheduledJobOptions</span><span class="sxs-lookup"><span data-stu-id="0f0ba-216">Microsoft.PowerShell.ScheduledJob.ScheduledJobOptions</span></span>

## <span data-ttu-id="0f0ba-217">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="0f0ba-217">NOTES</span></span>

* <span data-ttu-id="0f0ba-218">Du kan använda **ScheduledJobOptions** -objektet som **New-ScheduledJobOption** skapar som värdet för parametern *ScheduledJobOption* i Register-ScheduledJob-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="0f0ba-218">You can use the **ScheduledJobOptions** object that **New-ScheduledJobOption** creates as the value of the *ScheduledJobOption* parameter of the Register-ScheduledJob cmdlet.</span></span> <span data-ttu-id="0f0ba-219">*ScheduledJobOption* -parametern kan dock också ta ett värde för hash-tabell som anger egenskaperna för **ScheduledJobOptions** -objektet och deras värden, till exempel:</span><span class="sxs-lookup"><span data-stu-id="0f0ba-219">However, the *ScheduledJobOption* parameter can also take a hash table value that specifies the properties of the **ScheduledJobOptions** object and their values, such as:</span></span>

  `@{ShowInTaskScheduler=$False; RunElevated=$True; IdleDuration="00:05"}`

## <span data-ttu-id="0f0ba-220">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="0f0ba-220">RELATED LINKS</span></span>

[<span data-ttu-id="0f0ba-221">Add-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="0f0ba-221">Add-JobTrigger</span></span>](Add-JobTrigger.md)

[<span data-ttu-id="0f0ba-222">Disable-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="0f0ba-222">Disable-JobTrigger</span></span>](Disable-JobTrigger.md)

[<span data-ttu-id="0f0ba-223">Disable-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="0f0ba-223">Disable-ScheduledJob</span></span>](Disable-ScheduledJob.md)

[<span data-ttu-id="0f0ba-224">Aktivera – JobTrigger</span><span class="sxs-lookup"><span data-stu-id="0f0ba-224">Enable-JobTrigger</span></span>](Enable-JobTrigger.md)

[<span data-ttu-id="0f0ba-225">Aktivera – ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="0f0ba-225">Enable-ScheduledJob</span></span>](Enable-ScheduledJob.md)

[<span data-ttu-id="0f0ba-226">Get-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="0f0ba-226">Get-JobTrigger</span></span>](Get-JobTrigger.md)

[<span data-ttu-id="0f0ba-227">Get-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="0f0ba-227">Get-ScheduledJob</span></span>](Get-ScheduledJob.md)

[<span data-ttu-id="0f0ba-228">Get-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="0f0ba-228">Get-ScheduledJobOption</span></span>](Get-ScheduledJobOption.md)

[<span data-ttu-id="0f0ba-229">New-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="0f0ba-229">New-JobTrigger</span></span>](New-JobTrigger.md)

[<span data-ttu-id="0f0ba-230">New-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="0f0ba-230">New-ScheduledJobOption</span></span>](New-ScheduledJobOption.md)

[<span data-ttu-id="0f0ba-231">Registrera – ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="0f0ba-231">Register-ScheduledJob</span></span>](Register-ScheduledJob.md)

[<span data-ttu-id="0f0ba-232">Remove-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="0f0ba-232">Remove-JobTrigger</span></span>](Remove-JobTrigger.md)

[<span data-ttu-id="0f0ba-233">Set-JobTrigger</span><span class="sxs-lookup"><span data-stu-id="0f0ba-233">Set-JobTrigger</span></span>](Set-JobTrigger.md)

[<span data-ttu-id="0f0ba-234">Set-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="0f0ba-234">Set-ScheduledJob</span></span>](Set-ScheduledJob.md)

[<span data-ttu-id="0f0ba-235">Set-ScheduledJobOption</span><span class="sxs-lookup"><span data-stu-id="0f0ba-235">Set-ScheduledJobOption</span></span>](Set-ScheduledJobOption.md)

[<span data-ttu-id="0f0ba-236">Avregistrera-ScheduledJob</span><span class="sxs-lookup"><span data-stu-id="0f0ba-236">Unregister-ScheduledJob</span></span>](Unregister-ScheduledJob.md)
