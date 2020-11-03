---
description: Förklarar hur du skapar och hanterar schemalagda jobb.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/psscheduledjob/about/about_scheduled_jobs_basics?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Scheduled_Jobs_Basics
ms.openlocfilehash: d957c3267959c13b705e79fb220da4048e27a435
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270969"
---
# <a name="about-scheduled-jobs-basics"></a><span data-ttu-id="8094f-104">Om grundläggande om schemalagda jobb</span><span class="sxs-lookup"><span data-stu-id="8094f-104">About Scheduled Jobs Basics</span></span>

## <a name="short-description"></a><span data-ttu-id="8094f-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="8094f-105">Short description</span></span>

<span data-ttu-id="8094f-106">Förklarar hur du skapar och hanterar schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="8094f-106">Explains how to create and manage scheduled jobs.</span></span>

## <a name="long-description"></a><span data-ttu-id="8094f-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="8094f-107">Long description</span></span>

<span data-ttu-id="8094f-108">Det här dokumentet visar hur du utför grundläggande uppgifter för att skapa och hantera schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="8094f-108">This document shows how to perform basic tasks of creating and managing scheduled jobs.</span></span> <span data-ttu-id="8094f-109">Information om mer avancerade uppgifter finns [about_Scheduled_Jobs_Advanced](about_Scheduled_Jobs_Advanced.md).</span><span class="sxs-lookup"><span data-stu-id="8094f-109">For information about more advanced tasks, see [about_Scheduled_Jobs_Advanced](about_Scheduled_Jobs_Advanced.md).</span></span>

<span data-ttu-id="8094f-110">Mer information om de cmdletar som finns i **PSScheduledJob** -modulen finns i [PSScheduledJob](xref:PSScheduledJob).</span><span class="sxs-lookup"><span data-stu-id="8094f-110">For more information about the cmdlets contained in the **PSScheduledJob** module, see [PSScheduledJob](xref:PSScheduledJob).</span></span>

## <a name="how-to-create-a-scheduled-job"></a><span data-ttu-id="8094f-111">Så här skapar du ett schemalagt jobb</span><span class="sxs-lookup"><span data-stu-id="8094f-111">How to create a scheduled job</span></span>

<span data-ttu-id="8094f-112">Använd cmdleten för att skapa ett schemalagt jobb `Register-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="8094f-112">To create a scheduled job, use the `Register-ScheduledJob` cmdlet.</span></span> <span data-ttu-id="8094f-113">Cmdleten kräver ett namn och de kommandon eller skript som jobbet kör.</span><span class="sxs-lookup"><span data-stu-id="8094f-113">The cmdlet requires a name and the commands or script that the job runs.</span></span> <span data-ttu-id="8094f-114">Du kan antingen köra jobbet direkt genom att lägga till parametern **RunNow** eller skapa en jobb utlösare och ange jobb alternativ när du skapar jobbet, eller redigera ett befintligt jobb.</span><span class="sxs-lookup"><span data-stu-id="8094f-114">You can either run the job immediately by adding the **RunNow** parameter, or create a job trigger and set job options when you create the job, or edit an existing job.</span></span>

<span data-ttu-id="8094f-115">Om du vill skapa ett jobb som kör ett skript använder du parametern **sökväg** för att ange sökvägen till skript filen.</span><span class="sxs-lookup"><span data-stu-id="8094f-115">To create a job that runs a script, use the **FilePath** parameter to specify the path to the script file.</span></span> <span data-ttu-id="8094f-116">Om du vill skapa ett jobb som kör kommandon använder du parametern **script block** .</span><span class="sxs-lookup"><span data-stu-id="8094f-116">To create a job that runs commands, use the **ScriptBlock** parameter.</span></span>

<span data-ttu-id="8094f-117">`Register-ScheduledJob`Cmdlet: en skapar **ProcessJob** , som kör ett `Get-Process` kommando.</span><span class="sxs-lookup"><span data-stu-id="8094f-117">The `Register-ScheduledJob` cmdlet creates the **ProcessJob** , which runs a `Get-Process` command.</span></span> <span data-ttu-id="8094f-118">Det här schemalagda jobbet har standard jobb alternativen och ingen jobb utlösare.</span><span class="sxs-lookup"><span data-stu-id="8094f-118">This scheduled job has the default job options and no job trigger.</span></span>

```powershell
Register-ScheduledJob -Name ProcessJob -ScriptBlock { Get-Process }
```

```Output
Id         Name            Triggers        Command       Enabled
--         ----            --------        -------       -------
8          ProcessJob      {}              Get-Process   True
```

## <a name="how-to-create-a-job-trigger"></a><span data-ttu-id="8094f-119">Så här skapar du en jobb utlösare</span><span class="sxs-lookup"><span data-stu-id="8094f-119">How to create a job trigger</span></span>

<span data-ttu-id="8094f-120">Jobb utlösare startar ett schemalagt jobb automatiskt.</span><span class="sxs-lookup"><span data-stu-id="8094f-120">Job triggers start a scheduled job automatically.</span></span> <span data-ttu-id="8094f-121">En jobb utlösare kan vara ett engångs schema eller ett återkommande schema eller en händelse, till exempel när en användare loggar in eller Windows startas.</span><span class="sxs-lookup"><span data-stu-id="8094f-121">A job trigger can be one-time or recurring schedule or an event, such as when a user logs on or Windows starts.</span></span> <span data-ttu-id="8094f-122">Varje jobb kan ha noll, ett eller flera jobb utlösare.</span><span class="sxs-lookup"><span data-stu-id="8094f-122">Each job can have zero, one, or multiple job triggers.</span></span>

<span data-ttu-id="8094f-123">Använd cmdleten för att skapa en jobb utlösare `New-JobTrigger` .</span><span class="sxs-lookup"><span data-stu-id="8094f-123">To create a job trigger, use the `New-JobTrigger` cmdlet.</span></span> <span data-ttu-id="8094f-124">Följande kommando skapar en jobb utlösare som startar ett jobb varje måndag och torsdag kl. 5:00.</span><span class="sxs-lookup"><span data-stu-id="8094f-124">The following command creates a job trigger that starts a job every Monday and Thursday at 5:00 AM.</span></span>
<span data-ttu-id="8094f-125">Kommandot sparar jobb utlösaren i `$T` variabeln.</span><span class="sxs-lookup"><span data-stu-id="8094f-125">The command saves the job trigger in the `$T` variable.</span></span>

```powershell
$T = New-JobTrigger -Weekly -DaysOfWeek "Monday", "Thursday" -At "5:00 AM"
```

<span data-ttu-id="8094f-126">Jobb utlösare är valfria.</span><span class="sxs-lookup"><span data-stu-id="8094f-126">Job triggers are optional.</span></span> <span data-ttu-id="8094f-127">Du kan starta ett schemalagt jobb när som helst genom att lägga till parametern **RunNow** i ditt `Register-ScheduledJob` kommando, eller genom att använda `Start-Job` cmdletarna.</span><span class="sxs-lookup"><span data-stu-id="8094f-127">You can start a scheduled job at any time by adding the **RunNow** parameter to your `Register-ScheduledJob` command, or by using the `Start-Job` cmdlets.</span></span>

## <a name="how-to-add-a-job-trigger"></a><span data-ttu-id="8094f-128">Så här lägger du till en jobb utlösare</span><span class="sxs-lookup"><span data-stu-id="8094f-128">How to add a job trigger</span></span>

<span data-ttu-id="8094f-129">När du lägger till en jobb utlösare i ett schemalagt jobb läggs jobb utlösaren till i det schemalagda jobbets XML-fil för det schemalagda jobbet och blir en del av det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="8094f-129">When you add a job trigger to a scheduled job, the job trigger is added to the scheduled job XML file for the scheduled job and becomes part of the scheduled job.</span></span>

<span data-ttu-id="8094f-130">Du kan lägga till en jobb utlösare i ett schemalagt jobb när du skapar det schemalagda jobbet eller redigera ett befintligt jobb.</span><span class="sxs-lookup"><span data-stu-id="8094f-130">You can add a job trigger to a scheduled job when you create the scheduled job, or edit an existing job.</span></span> <span data-ttu-id="8094f-131">Du kan när som helst ändra jobb utlösaren för ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="8094f-131">You can change the job trigger of a scheduled job at any time.</span></span>

<span data-ttu-id="8094f-132">PowerShell använder vissa av de jobb utlösare som Schemaläggaren använder.</span><span class="sxs-lookup"><span data-stu-id="8094f-132">PowerShell uses some of the same job triggers that Task Scheduler uses.</span></span> <span data-ttu-id="8094f-133">Detaljerad information om jobb utlösare finns i hjälp avsnittet för cmdleten [New-JobTrigger](xref:PSScheduledJob.New-JobTrigger) .</span><span class="sxs-lookup"><span data-stu-id="8094f-133">For detailed information about job triggers, see the help topic for the [New-JobTrigger](xref:PSScheduledJob.New-JobTrigger) cmdlet.</span></span>

<span data-ttu-id="8094f-134">I följande exempel används ihopbuntning för att skapa `$JobParms` som är parameter värden som skickas till `Register-ScheduledJob` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="8094f-134">The following example uses splatting to create `$JobParms` which are parameter values that are passed to the `Register-ScheduledJob` cmdlet.</span></span> <span data-ttu-id="8094f-135">Mer information finns i [about_Splatting. MD](../../Microsoft.PowerShell.Core/About/about_Splatting.md).</span><span class="sxs-lookup"><span data-stu-id="8094f-135">For more information, see [about_Splatting.md](../../Microsoft.PowerShell.Core/About/about_Splatting.md).</span></span>
<span data-ttu-id="8094f-136">`Register-ScheduledJob`Använder `@JobParms` för att skapa ett schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="8094f-136">The `Register-ScheduledJob` uses `@JobParms` to create a scheduled job.</span></span> <span data-ttu-id="8094f-137">Den använder **Utlösar** -parametern för att ange jobb utlösaren i `$T` variabeln.</span><span class="sxs-lookup"><span data-stu-id="8094f-137">It uses the **Trigger** parameter to specify the job trigger in the `$T` variable.</span></span>

```powershell
$JobParms = @{
  Name = "ProcessJob"
  ScriptBlock = {Get-Command}
  Trigger = $T
}

Register-ScheduledJob @JobParms
```

<span data-ttu-id="8094f-138">Du kan också lägga till en jobb utlösare till ett befintligt schemalagt jobb när som helst.</span><span class="sxs-lookup"><span data-stu-id="8094f-138">You can also add a job trigger to an existing scheduled job at any time.</span></span> <span data-ttu-id="8094f-139">`Add-JobTrigger`Cmdleten lägger till jobb utlösaren i `$T` variabeln till det schemalagda **ProcessJob** -jobbet.</span><span class="sxs-lookup"><span data-stu-id="8094f-139">The `Add-JobTrigger` cmdlet adds the job trigger in the `$T` variable to the **ProcessJob** scheduled job.</span></span>

```powershell
Add-JobTrigger -Name ProcessJob -Trigger $T
```

<span data-ttu-id="8094f-140">Därför startar jobb utlösaren **ProcessJob** automatiskt varje måndag och torsdag kl. 5:00.</span><span class="sxs-lookup"><span data-stu-id="8094f-140">As a result, the job trigger starts the **ProcessJob** automatically every Monday and Thursday at 5:00 AM.</span></span>

## <a name="how-to-get-a-job-trigger"></a><span data-ttu-id="8094f-141">Så här hämtar du en jobb utlösare</span><span class="sxs-lookup"><span data-stu-id="8094f-141">How to get a job trigger</span></span>

<span data-ttu-id="8094f-142">Använd cmdleten för att hämta jobb utlösaren för ett schemalagt jobb `Get-JobTrigger` .</span><span class="sxs-lookup"><span data-stu-id="8094f-142">To get the job trigger of a scheduled job, use the `Get-JobTrigger` cmdlet.</span></span> <span data-ttu-id="8094f-143">Använd parametrarna **Name** , **ID** och **InputObject** för att ange det schemalagda jobbet, inte jobb utlösaren.</span><span class="sxs-lookup"><span data-stu-id="8094f-143">Use the **Name** , **ID** , and **InputObject** parameters to specify the scheduled job, not the job trigger.</span></span>

<span data-ttu-id="8094f-144">`Get-JobTrigger` hämtar jobb utlösaren för **ProcessJob**.</span><span class="sxs-lookup"><span data-stu-id="8094f-144">`Get-JobTrigger` gets the job trigger of the **ProcessJob**.</span></span>

```powershell
Get-JobTrigger -Name ProcessJob
```

```Output
Id   Frequency       Time                   DaysOfWeek              Enabled
--   ---------       ----                   ----------              -------
1    Weekly          11/7/2011 5:00:00 AM   {Monday, Thursday}      True
```

## <a name="how-to-create-job-options"></a><span data-ttu-id="8094f-145">Så här skapar du jobb alternativ</span><span class="sxs-lookup"><span data-stu-id="8094f-145">How to create job options</span></span>

<span data-ttu-id="8094f-146">Jobb alternativ fastställer villkor för att starta och köra jobbet.</span><span class="sxs-lookup"><span data-stu-id="8094f-146">Job options establish conditions for starting and running the job.</span></span> <span data-ttu-id="8094f-147">Varje jobb har standard jobb alternativ om du inte ändrar dem.</span><span class="sxs-lookup"><span data-stu-id="8094f-147">Every job has the default job options unless you change them.</span></span> <span data-ttu-id="8094f-148">Eftersom jobb alternativ kan förhindra att ett jobb körs vid den schemalagda tiden är det viktigt att förstå jobb alternativen och använda dem noggrant.</span><span class="sxs-lookup"><span data-stu-id="8094f-148">Because job options can prevent a job from running at the scheduled time, it is important to understand the job options and use them carefully.</span></span>

<span data-ttu-id="8094f-149">PowerShell använder samma jobb alternativ som Schemaläggaren använder.</span><span class="sxs-lookup"><span data-stu-id="8094f-149">PowerShell uses the same job options that Task Scheduler uses.</span></span> <span data-ttu-id="8094f-150">Detaljerad information om jobb alternativen finns i hjälp avsnittet för [New-ScheduledJobOption](xref:PSScheduledJob.New-ScheduledJobOption).</span><span class="sxs-lookup"><span data-stu-id="8094f-150">For detailed information about the job options, see the help topic for [New-ScheduledJobOption](xref:PSScheduledJob.New-ScheduledJobOption).</span></span>

<span data-ttu-id="8094f-151">Jobb alternativen lagras i XML-filen med schemalagt jobb.</span><span class="sxs-lookup"><span data-stu-id="8094f-151">Job options are stored in the scheduled job XML file.</span></span> <span data-ttu-id="8094f-152">Du kan ange jobb alternativ när du skapar ett schemalagt jobb eller ändrar dem när som helst.</span><span class="sxs-lookup"><span data-stu-id="8094f-152">You can set job options when you create a scheduled job or change them at any time.</span></span>

<span data-ttu-id="8094f-153">`New-ScheduledJobOption`Cmdleten skapar ett schemalagt jobb-alternativ där alternativet **WakeToRun** schemalagt jobb är inställt på True.</span><span class="sxs-lookup"><span data-stu-id="8094f-153">The `New-ScheduledJobOption` cmdlet creates a scheduled job option in which the **WakeToRun** scheduled job option is set to True.</span></span> <span data-ttu-id="8094f-154">Alternativet **WakeToRun** kör det schemalagda jobbet även om datorn är i vilo läge eller vilo läge vid den schemalagda start tiden.</span><span class="sxs-lookup"><span data-stu-id="8094f-154">The **WakeToRun** option runs the scheduled job even if the computer is in the Sleep or Hibernate state at the scheduled start time.</span></span> <span data-ttu-id="8094f-155">Kommandot sparar jobb alternativen i `$O` variabeln.</span><span class="sxs-lookup"><span data-stu-id="8094f-155">The command saves the job options in the `$O` variable.</span></span>

```powershell
$O = New-ScheduledJobOption -WakeToRun
```

## <a name="how-to-get-job-options"></a><span data-ttu-id="8094f-156">Så här hämtar du jobb alternativ</span><span class="sxs-lookup"><span data-stu-id="8094f-156">How to get job options</span></span>

<span data-ttu-id="8094f-157">Använd cmdleten för att hämta jobb alternativen för ett schemalagt jobb `Get-ScheduledJobOption` .</span><span class="sxs-lookup"><span data-stu-id="8094f-157">To get the job options of a scheduled job, use the `Get-ScheduledJobOption` cmdlet.</span></span> <span data-ttu-id="8094f-158">Använd parametrarna **Name** , **ID** och **InputObject** för att ange det schemalagda jobbet, inte jobb alternativen.</span><span class="sxs-lookup"><span data-stu-id="8094f-158">Use the **Name** , **ID** , and **InputObject** parameters to specify the scheduled job, not the job options.</span></span>

<span data-ttu-id="8094f-159">`Get-ScheduledJobOption` hämtar jobb alternativen för **ProcessJob**.</span><span class="sxs-lookup"><span data-stu-id="8094f-159">`Get-ScheduledJobOption` gets the job options of the **ProcessJob**.</span></span>

```powershell
Get-ScheduledJobOption -Name ProcessJob
```

```Output
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
MultipleInstancePolicy : IgnoreNew
JobDefinition          : Microsoft.PowerShell.ScheduledJob.ScheduledJobDefinition
```

## <a name="how-to-change-job-options"></a><span data-ttu-id="8094f-160">Ändra jobb alternativ</span><span class="sxs-lookup"><span data-stu-id="8094f-160">How to change job options</span></span>

<span data-ttu-id="8094f-161">Du kan ändra jobb alternativen för ett schemalagt jobb när du skapar ett schemalagt jobb eller redigera ett befintligt jobb.</span><span class="sxs-lookup"><span data-stu-id="8094f-161">You can change the job options of a scheduled job when you create a scheduled job or edit an existing job.</span></span>

<span data-ttu-id="8094f-162">Splatted `$JobParms` skickas till `Add-JobTrigger` cmdlet: en för att skapa process jobbet.</span><span class="sxs-lookup"><span data-stu-id="8094f-162">The splatted `$JobParms` are passed to the `Add-JobTrigger` cmdlet to create the process job.</span></span> <span data-ttu-id="8094f-163">Parametern **ScheduledJobOption** används för att ange jobb alternativen i `$O` variabeln.</span><span class="sxs-lookup"><span data-stu-id="8094f-163">It uses the **ScheduledJobOption** parameter to specify the job options in the `$O` variable.</span></span>

```powershell
$JobParms = @{
  Name = "ProcessJob"
  ScriptBlock = {Get-Process}
  ScheduledJobOption = $O
}

Add-JobTrigger @JobParms
```

<span data-ttu-id="8094f-164">Du kan också ändra jobb alternativen till ett befintligt schemalagt jobb när som helst.</span><span class="sxs-lookup"><span data-stu-id="8094f-164">You can also change the job options to an existing scheduled job at any time.</span></span>
<span data-ttu-id="8094f-165">Följande kommando använder `Set-ScheduledJobOption` cmdleten för att ändra värdet för alternativet **WakeToRun** för **ProcessJob** scheduledJob till **True**.</span><span class="sxs-lookup"><span data-stu-id="8094f-165">The following command uses the `Set-ScheduledJobOption` cmdlet to change the value of the **WakeToRun** option of the **ProcessJob** scheduledJob to **True**.</span></span>

<span data-ttu-id="8094f-166">`Set`Cmdletarna i **PSScheduledJob** -modulen, t. ex. `Set-ScheduledJobOption` cmdlet, har inte **namn** **-eller ID-** parametrar.</span><span class="sxs-lookup"><span data-stu-id="8094f-166">The `Set` cmdlets in the **PSScheduledJob** module, such as the `Set-ScheduledJobOption` cmdlet, don't have **Name** or **ID** parameters.</span></span> <span data-ttu-id="8094f-167">Du kan använda parametern **InputObject** för att ange de schemalagda jobb alternativen eller skicka ett schemalagt jobb från `Get-ScheduledJobOption` cmdlet till `Set-ScheduledJobOption` .</span><span class="sxs-lookup"><span data-stu-id="8094f-167">You can use the **InputObject** parameter to specify the scheduled job options or pipe a scheduled job from `Get-ScheduledJobOption` cmdlet to `Set-ScheduledJobOption`.</span></span>

<span data-ttu-id="8094f-168">I det här exemplet används `Get-ScheduledJob` cmdlet: en för att hämta ProcessJob.</span><span class="sxs-lookup"><span data-stu-id="8094f-168">This example uses the `Get-ScheduledJob` cmdlet to get the ProcessJob.</span></span> <span data-ttu-id="8094f-169">Den använder `Get-ScheduledJobOption` cmdleten för att hämta jobb alternativen i **ProcessJob** och `Set-ScheduledJobOption` cmdleten för att ändra **WakeToRun** -jobbets alternativ i ProcessJob till true.</span><span class="sxs-lookup"><span data-stu-id="8094f-169">It uses the `Get-ScheduledJobOption` cmdlet to get the job options in the **ProcessJob** and the `Set-ScheduledJobOption` cmdlet to change the **WakeToRun** job option in the ProcessJob to True.</span></span>

```powershell
Get-ScheduledJob -Name ProcessJob | Get-ScheduledJobOption |
 Set-ScheduledJobOption -WakeToRun
```

## <a name="how-to-get-scheduled-job-instances"></a><span data-ttu-id="8094f-170">Så här hämtar du schemalagda jobb instanser</span><span class="sxs-lookup"><span data-stu-id="8094f-170">How to get scheduled job instances</span></span>

<span data-ttu-id="8094f-171">När ett schemalagt jobb startas skapar PowerShell en jobb instans som liknar ett standard bakgrunds jobb i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8094f-171">When a scheduled job is started, PowerShell creates a job instance that is similar to a standard PowerShell background job.</span></span> <span data-ttu-id="8094f-172">Du kan använda jobb-cmdletar, till exempel `Get-Job` `Stop-Job` och `Receive-Job` för att hantera jobb instanser.</span><span class="sxs-lookup"><span data-stu-id="8094f-172">You can use the job cmdlets, such as `Get-Job`, `Stop-Job` and `Receive-Job` to manage the job instances.</span></span>

> [!NOTE]
> <span data-ttu-id="8094f-173">Om du vill använda jobb-cmdletar på instanser av schemalagda jobb måste **PSScheduledJob** -modulen importeras till-sessionen.</span><span class="sxs-lookup"><span data-stu-id="8094f-173">To use the job cmdlets on instances of scheduled jobs, the **PSScheduledJob** module must be imported into the session.</span></span> <span data-ttu-id="8094f-174">Om du vill importera **PSScheduledJob** -modulen skriver du `Import-Module PSScheduledJob` eller använder en schemalagd jobb-cmdlet, till exempel `Get-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="8094f-174">To import the **PSScheduledJob** module, type `Import-Module PSScheduledJob` or use any scheduled job cmdlet, such as `Get-ScheduledJob`.</span></span>

<span data-ttu-id="8094f-175">Om du vill hämta alla instanser av schemalagda PowerShell-jobb och alla aktiva standard jobb använder du `Get-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="8094f-175">To get all instances of PowerShell scheduled jobs, and all active standard jobs, use the `Get-Job` cmdlet.</span></span> <span data-ttu-id="8094f-176">`Import-Module`Cmdleten importerar modulen **PSScheduledJob** och `Get-Job` hämtar jobben på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="8094f-176">The `Import-Module` cmdlet imports the **PSScheduledJob** module and `Get-Job` gets the jobs on the local computer.</span></span>

```powershell
Import-Module PSScheduledJob
Get-Job
```

<span data-ttu-id="8094f-177">`Get-Job` hämtar instanser av **ProcessJob** på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="8094f-177">`Get-Job` gets instances of **ProcessJob** on the local computer.</span></span>

```powershell
Get-Job -Name ProcessJob
```

```Output
Id     Name        PSJobTypeName  State    HasMoreData   Location   Command
--     ----        ------------   -----    -----------   --------   -------
45     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
46     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
47     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
48     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
49     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
50     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
51     ProcessJob  PSScheduledJob Completed       True   localhost   Get-Process
```

<span data-ttu-id="8094f-178">Standard visningen visar inte start tiden, vilket normalt särskiljer instanser av samma schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="8094f-178">The default display does not show the start time, which typically distinguishes instances of the same scheduled job.</span></span>

<span data-ttu-id="8094f-179">`Get-Job`Cmdleten skickar objekt nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="8094f-179">The `Get-Job` cmdlet sends objects down the pipeline.</span></span> <span data-ttu-id="8094f-180">`Format-Table`Cmdleten visar egenskaperna **namn** , **ID** och **BeginTime** för det schemalagda jobbet.</span><span class="sxs-lookup"><span data-stu-id="8094f-180">The `Format-Table` cmdlet displays the **Name** , **ID** , and **BeginTime** properties of the scheduled job.</span></span>

```powershell
Get-Job ProcessJob | Format-Table -Property Name, ID, BeginTime
```

```Output
Name       Id BeginTime
----       -- ---------
ProcessJob 43 11/2/2011 3:00:02 AM
ProcessJob 44 11/3/2011 3:00:02 AM
ProcessJob 45 11/4/2011 3:00:02 AM
ProcessJob 46 11/5/2011 3:00:02 AM
ProcessJob 47 11/6/2011 3:00:02 AM
ProcessJob 48 11/7/2011 12:00:01 AM
ProcessJob 49 11/7/2011 3:00:02 AM
ProcessJob 50 11/8/2011 3:00:02 AM
```

## <a name="get-scheduled-job-results"></a><span data-ttu-id="8094f-181">Hämta schemalagt jobb resultat</span><span class="sxs-lookup"><span data-stu-id="8094f-181">Get scheduled job results</span></span>

<span data-ttu-id="8094f-182">Använd cmdleten för att hämta resultatet av en instans av ett schemalagt jobb `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="8094f-182">To get the results of an instance of a scheduled job, use the `Receive-Job` cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="8094f-183">Om du vill använda jobb-cmdletar på instanser av schemalagda jobb måste **PSScheduledJob** -modulen importeras till-sessionen.</span><span class="sxs-lookup"><span data-stu-id="8094f-183">To use the Job cmdlets on instances of scheduled jobs, the **PSScheduledJob** module must be imported into the session.</span></span> <span data-ttu-id="8094f-184">Om du vill importera **PSScheduledJob** -modulen skriver du `Import-Module PSScheduledJob` eller använder en schemalagd jobb-cmdlet, till exempel `Get-ScheduledJob` .</span><span class="sxs-lookup"><span data-stu-id="8094f-184">To import the **PSScheduledJob** module, type `Import-Module PSScheduledJob` or use any scheduled job cmdlet, such as `Get-ScheduledJob`.</span></span>

<span data-ttu-id="8094f-185">I det här exemplet får du resultatet från den senaste instansen av det schemalagda **ProcessJob** -jobbet (ID = 51).</span><span class="sxs-lookup"><span data-stu-id="8094f-185">This examples gets the results of the newest instance of the **ProcessJob** scheduled job (ID = 51).</span></span>

```powershell
Import-Module PSScheduledJob
Receive-Job -ID 51 -Keep
```

<span data-ttu-id="8094f-186">Resultatet av schemalagda jobb sparas på disk, så parametern **Keep** of `Receive-Job` är inte obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="8094f-186">The results of scheduled jobs are saved on disk, so the **Keep** parameter of `Receive-Job` is not required.</span></span> <span data-ttu-id="8094f-187">Men utan parametern **Keep** kan du bara hämta resultatet av ett schemalagt jobb en gång i varje PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="8094f-187">However, without the **Keep** parameter, you can get the results of a scheduled job only once in each PowerShell session.</span></span> <span data-ttu-id="8094f-188">Starta en ny PowerShell-session genom att skriva `PowerShell` eller öppna ett nytt PowerShell-fönster.</span><span class="sxs-lookup"><span data-stu-id="8094f-188">To start a new PowerShell session, type `PowerShell` or open a new PowerShell window.</span></span>

## <a name="see-also"></a><span data-ttu-id="8094f-189">Se även</span><span class="sxs-lookup"><span data-stu-id="8094f-189">See also</span></span>

[<span data-ttu-id="8094f-190">about_Scheduled_Jobs_Advanced</span><span class="sxs-lookup"><span data-stu-id="8094f-190">about_Scheduled_Jobs_Advanced</span></span>](about_Scheduled_Jobs_Advanced.md)

[<span data-ttu-id="8094f-191">about_Scheduled_Jobs_Troubleshooting</span><span class="sxs-lookup"><span data-stu-id="8094f-191">about_Scheduled_Jobs_Troubleshooting</span></span>](about_Scheduled_Jobs_Troubleshooting.md)

[<span data-ttu-id="8094f-192">about_Scheduled_Jobs</span><span class="sxs-lookup"><span data-stu-id="8094f-192">about_Scheduled_Jobs</span></span>](about_Scheduled_Jobs.md)

[<span data-ttu-id="8094f-193">about_Splatting. MD</span><span class="sxs-lookup"><span data-stu-id="8094f-193">about_Splatting.md</span></span>](../../Microsoft.PowerShell.Core/About/about_Splatting.md)

<span data-ttu-id="8094f-194">Cmdletar för [PSScheduledJob](xref:PSScheduledJob) -modul</span><span class="sxs-lookup"><span data-stu-id="8094f-194">[PSScheduledJob](xref:PSScheduledJob) module cmdlets</span></span>

[<span data-ttu-id="8094f-195">Schemaläggaren</span><span class="sxs-lookup"><span data-stu-id="8094f-195">Task Scheduler</span></span>](/windows/desktop/TaskSchd/task-scheduler-reference)
