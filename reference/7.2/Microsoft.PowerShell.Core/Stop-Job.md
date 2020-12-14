---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/stop-job?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Job
ms.openlocfilehash: 479c099d2d5daf1cc50c5c645be053ff4ae02bdc
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709979"
---
# <span data-ttu-id="20e31-102">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="20e31-102">Stop-Job</span></span>

## <span data-ttu-id="20e31-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="20e31-103">SYNOPSIS</span></span>
<span data-ttu-id="20e31-104">Stoppar ett PowerShell-bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="20e31-104">Stops a PowerShell background job.</span></span>

## <span data-ttu-id="20e31-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="20e31-105">SYNTAX</span></span>

### <span data-ttu-id="20e31-106">SessionIdParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="20e31-106">SessionIdParameterSet (Default)</span></span>

```
Stop-Job [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="20e31-107">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="20e31-107">JobParameterSet</span></span>

```
Stop-Job [-Job] <Job[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="20e31-108">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="20e31-108">NameParameterSet</span></span>

```
Stop-Job [-PassThru] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="20e31-109">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="20e31-109">InstanceIdParameterSet</span></span>

```
Stop-Job [-PassThru] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="20e31-110">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="20e31-110">StateParameterSet</span></span>

```
Stop-Job [-PassThru] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="20e31-111">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="20e31-111">FilterParameterSet</span></span>

```
Stop-Job [-PassThru] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="20e31-112">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="20e31-112">DESCRIPTION</span></span>

<span data-ttu-id="20e31-113">`Stop-Job`Cmdleten stoppar PowerShell-bakgrunds jobb som pågår.</span><span class="sxs-lookup"><span data-stu-id="20e31-113">The `Stop-Job` cmdlet stops PowerShell background jobs that are in progress.</span></span> <span data-ttu-id="20e31-114">Du kan använda den här cmdleten för att stoppa alla jobb eller stoppa valda jobb baserat på namn, ID, instans-ID eller tillstånd, eller genom att skicka ett jobb objekt till `Stop-Job` .</span><span class="sxs-lookup"><span data-stu-id="20e31-114">You can use this cmdlet to stop all jobs or stop selected jobs based on their name, ID, instance ID, or state, or by passing a job object to `Stop-Job`.</span></span>

<span data-ttu-id="20e31-115">Du kan använda `Stop-Job` för att stoppa bakgrunds jobb, till exempel de som startades med hjälp av `Start-Job` cmdleten eller parametern **AsJob** för valfri cmdlet.</span><span class="sxs-lookup"><span data-stu-id="20e31-115">You can use `Stop-Job` to stop background jobs, such as those that were started by using the `Start-Job` cmdlet or the **AsJob** parameter of any cmdlet.</span></span> <span data-ttu-id="20e31-116">När du stoppar ett bakgrunds jobb Slutför PowerShell alla uppgifter som väntar i jobbkön och avslutar sedan jobbet.</span><span class="sxs-lookup"><span data-stu-id="20e31-116">When you stop a background job, PowerShell completes all tasks that are pending in that job queue and then ends the job.</span></span> <span data-ttu-id="20e31-117">Inga nya aktiviteter läggs till i kön när det här kommandot har skickats.</span><span class="sxs-lookup"><span data-stu-id="20e31-117">No new tasks are added to the queue after this command is submitted.</span></span>

<span data-ttu-id="20e31-118">Den här cmdleten tar inte bort bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="20e31-118">This cmdlet does not delete background jobs.</span></span> <span data-ttu-id="20e31-119">Använd cmdleten om du vill ta bort ett jobb `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="20e31-119">To delete a job, use the `Remove-Job` cmdlet.</span></span>

<span data-ttu-id="20e31-120">Från och med Windows PowerShell 3,0 `Stop-Job` stoppas även anpassade jobb typer, till exempel arbets flödes jobb och instanser av schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="20e31-120">Starting in Windows PowerShell 3.0, `Stop-Job` also stops custom job types, such as workflow jobs and instances of scheduled jobs.</span></span> <span data-ttu-id="20e31-121">Om du vill `Stop-Job` stoppa ett jobb med anpassad Jobbtyp importerar du modulen som stöder den anpassade jobb typen till sessionen innan du kör ett `Stop-Job` kommando, antingen med hjälp av `Import-Module` cmdleten eller genom att använda eller hämta en cmdlet i modulen.</span><span class="sxs-lookup"><span data-stu-id="20e31-121">To enable `Stop-Job` to stop a job with custom job type, import the module that supports the custom job type into the session before you run a `Stop-Job` command, either by using the `Import-Module` cmdlet or by using or getting a cmdlet in the module.</span></span> <span data-ttu-id="20e31-122">Information om en viss anpassad Jobbtyp finns i dokumentationen för den anpassade jobb typ funktionen.</span><span class="sxs-lookup"><span data-stu-id="20e31-122">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="20e31-123">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="20e31-123">EXAMPLES</span></span>

### <span data-ttu-id="20e31-124">Exempel 1: stoppa ett jobb på en fjärrdator med hjälp av Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="20e31-124">Example 1: Stop a job on a remote computer by using Invoke-Command</span></span>

```powershell
$s = New-PSSession -ComputerName Server01 -Credential Domain01\Admin02
$j = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Invoke-Command -Session $s -ScriptBlock { Stop-job -Job $Using:j }
```

<span data-ttu-id="20e31-125">Det här exemplet visar hur du kan använda `Stop-Job` cmdleten för att stoppa ett jobb som körs på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="20e31-125">This example shows how to use the `Stop-Job` cmdlet to stop a job that is running on a remote computer.</span></span>

<span data-ttu-id="20e31-126">Eftersom jobbet startades med hjälp av `Invoke-Command` cmdleten för att köra ett `Start-Job` kommando på distans, lagras jobbobjektet på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="20e31-126">Because the job was started by using the `Invoke-Command` cmdlet to run a `Start-Job` command remotely, the job object is stored on the remote computer.</span></span> <span data-ttu-id="20e31-127">Du måste använda ett annat `Invoke-Command` kommando om du vill köra ett `Stop-Job` kommando via fjärr anslutning.</span><span class="sxs-lookup"><span data-stu-id="20e31-127">You must use another `Invoke-Command` command to run a `Stop-Job` command remotely.</span></span> <span data-ttu-id="20e31-128">Mer information om fjärran sluten bakgrunds jobb finns about_Remote_Jobs.</span><span class="sxs-lookup"><span data-stu-id="20e31-128">For more information about remote background jobs, see about_Remote_Jobs.</span></span>

<span data-ttu-id="20e31-129">Det första kommandot skapar en PowerShell-session (**PSSession**) på Server01-datorn och lagrar sedan Session-objektet i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="20e31-129">The first command creates a PowerShell session (**PSSession**) on the Server01 computer, and then stores the session object in the `$s` variable.</span></span> <span data-ttu-id="20e31-130">Kommandot använder autentiseringsuppgifterna för en domän administratör.</span><span class="sxs-lookup"><span data-stu-id="20e31-130">The command uses the credentials of a domain administrator.</span></span>

<span data-ttu-id="20e31-131">Det andra kommandot använder `Invoke-Command` cmdleten för att köra ett `Start-Job` kommando i sessionen.</span><span class="sxs-lookup"><span data-stu-id="20e31-131">The second command uses the `Invoke-Command` cmdlet to run a `Start-Job` command in the session.</span></span> <span data-ttu-id="20e31-132">Kommandot i jobbet hämtar alla händelser i system händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="20e31-132">The command in the job gets all of the events in the System event log.</span></span> <span data-ttu-id="20e31-133">Resulterande jobb objekt lagras i `$j` variabeln.</span><span class="sxs-lookup"><span data-stu-id="20e31-133">The resulting job object is stored in the `$j` variable.</span></span>

<span data-ttu-id="20e31-134">Det tredje kommandot stoppar jobbet.</span><span class="sxs-lookup"><span data-stu-id="20e31-134">The third command stops the job.</span></span> <span data-ttu-id="20e31-135">Den använder `Invoke-Command` cmdleten för att köra ett `Stop-Job` kommando i **PSSession** på Server01.</span><span class="sxs-lookup"><span data-stu-id="20e31-135">It uses the `Invoke-Command` cmdlet to run a `Stop-Job` command in the **PSSession** on Server01.</span></span> <span data-ttu-id="20e31-136">Eftersom jobb objekt lagras i `$j` , vilket är en variabel på den lokala datorn, använder kommandot Använd omfångs modifieraren för att identifiera `$j` som en lokal variabel.</span><span class="sxs-lookup"><span data-stu-id="20e31-136">Because the job objects are stored in `$j`, which is a variable on the local computer, the command uses the Using scope modifier to identify `$j` as a local variable.</span></span>
<span data-ttu-id="20e31-137">Mer information om hur du använder omfångs modifieraren finns [about_Remote_Variables](about/about_Remote_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="20e31-137">For more information about the Using scope modifier, see [about_Remote_Variables](about/about_Remote_Variables.md).</span></span>

<span data-ttu-id="20e31-138">När kommandot har slutförts stoppas jobbet och **PSSession** i `$s` är tillgängligt för användning.</span><span class="sxs-lookup"><span data-stu-id="20e31-138">When the command finishes, the job is stopped and the **PSSession** in `$s` is available for use.</span></span>

### <span data-ttu-id="20e31-139">Exempel 2: stoppa ett bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="20e31-139">Example 2: Stop a background job</span></span>

```powershell
Stop-Job -Name "Job1"
```

<span data-ttu-id="20e31-140">Det här kommandot stoppar bakgrunds jobbet Job1.</span><span class="sxs-lookup"><span data-stu-id="20e31-140">This command stops the Job1 background job.</span></span>

### <span data-ttu-id="20e31-141">Exempel 3: stoppa flera bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="20e31-141">Example 3: Stop several background jobs</span></span>

```powershell
Stop-Job -Id 1, 3, 4
```

<span data-ttu-id="20e31-142">Det här kommandot stoppar tre jobb.</span><span class="sxs-lookup"><span data-stu-id="20e31-142">This command stops three jobs.</span></span>
<span data-ttu-id="20e31-143">Den identifierar dem med deras ID.</span><span class="sxs-lookup"><span data-stu-id="20e31-143">It identifies them by their IDs.</span></span>

### <span data-ttu-id="20e31-144">Exempel 4: stoppa alla bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="20e31-144">Example 4: Stop all background jobs</span></span>

```powershell
Get-Job | Stop-Job
```

<span data-ttu-id="20e31-145">Det här kommandot stoppar alla bakgrunds jobb i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="20e31-145">This command stops all of the background jobs in the current session.</span></span>

### <span data-ttu-id="20e31-146">Exempel 5: stoppa alla blockerade bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="20e31-146">Example 5: Stop all blocked background jobs</span></span>

```powershell
Stop-Job -State Blocked
```

<span data-ttu-id="20e31-147">Det här kommandot stoppar alla jobb som blockeras.</span><span class="sxs-lookup"><span data-stu-id="20e31-147">This command stops all the jobs that are blocked.</span></span>

### <span data-ttu-id="20e31-148">Exempel 6: stoppa ett jobb med hjälp av ett instans-ID</span><span class="sxs-lookup"><span data-stu-id="20e31-148">Example 6: Stop a job by using an instance ID</span></span>

```powershell
Get-Job | Format-Table ID, Name, Command, @{Label="State";Expression={$_.JobStateInfo.State}},
InstanceID -Auto
```

```Output
Id Name Command                 State  InstanceId
-- ---- -------                 -----  ----------
1 Job1 start-service schedule Running 05abb67a-2932-4bd5-b331-c0254b8d9146
3 Job3 start-service schedule Running c03cbd45-19f3-4558-ba94-ebe41b68ad03
5 Job5 get-service s*         Blocked e3bbfed1-9c53-401a-a2c3-a8db34336adf
```

```powershell
Stop-Job -InstanceId e3bbfed1-9c53-401a-a2c3-a8db34336adf
```

<span data-ttu-id="20e31-149">Kommandona visar hur du stoppar ett jobb baserat på dess instans-ID.</span><span class="sxs-lookup"><span data-stu-id="20e31-149">These commands show how to stop a job based on its instance ID.</span></span>

<span data-ttu-id="20e31-150">Det första kommandot använder `Get-Job` cmdleten för att hämta jobben i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="20e31-150">The first command uses the `Get-Job` cmdlet to get the jobs in the current session.</span></span> <span data-ttu-id="20e31-151">Kommandot använder en pipeline-operator ( `|` ) för att skicka jobben till ett `Format-Table` kommando, som visar en tabell med de angivna egenskaperna för varje jobb.</span><span class="sxs-lookup"><span data-stu-id="20e31-151">The command uses a pipeline operator (`|`) to send the jobs to a `Format-Table` command, which displays a table of the specified properties of each job.</span></span> <span data-ttu-id="20e31-152">Tabellen innehåller instans-ID för varje jobb.</span><span class="sxs-lookup"><span data-stu-id="20e31-152">The table includes the Instance ID of each job.</span></span> <span data-ttu-id="20e31-153">Den använder en beräknad egenskap för att visa jobb status.</span><span class="sxs-lookup"><span data-stu-id="20e31-153">It uses a calculated property to display the job state.</span></span>

<span data-ttu-id="20e31-154">Det andra kommandot använder ett `Stop-Job` kommando som har **InstanceID** -parametern för att stoppa ett valt jobb.</span><span class="sxs-lookup"><span data-stu-id="20e31-154">The second command uses a `Stop-Job` command that has the **InstanceID** parameter to stop a selected job.</span></span>

### <span data-ttu-id="20e31-155">Exempel 7: stoppa ett jobb på en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="20e31-155">Example 7: Stop a job on a remote computer</span></span>

```powershell
$j = Invoke-Command -ComputerName Server01 -ScriptBlock {Get-EventLog System} -AsJob
$j | Stop-Job -PassThru
```

```Output
Id    Name    State      HasMoreData     Location         Command
--    ----    ----       -----------     --------         -------
5     Job5    Stopped    True            user01-tablet    get-eventlog system
```

<span data-ttu-id="20e31-156">Det här exemplet visar hur du kan använda `Stop-Job` cmdleten för att stoppa ett jobb som körs på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="20e31-156">This example shows how to use the `Stop-Job` cmdlet to stop a job that is running on a remote computer.</span></span>

<span data-ttu-id="20e31-157">Eftersom jobbet startades med hjälp av parametern **AsJob** i `Invoke-Command` cmdleten, finns jobbobjektet på den lokala datorn, även om jobbet körs på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="20e31-157">Because the job was started by using the **AsJob** parameter of the `Invoke-Command` cmdlet, the job object is located on the local computer, even though the job runs on the remote computer.</span></span> <span data-ttu-id="20e31-158">Därför kan du använda ett lokalt `Stop-Job` kommando för att stoppa jobbet.</span><span class="sxs-lookup"><span data-stu-id="20e31-158">Therefore, you can use a local `Stop-Job` command to stop the job.</span></span>

<span data-ttu-id="20e31-159">Det första kommandot använder `Invoke-Command` cmdleten för att starta ett bakgrunds jobb på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="20e31-159">The first command uses the `Invoke-Command` cmdlet to start a background job on the Server01 computer.</span></span> <span data-ttu-id="20e31-160">Kommandot använder parametern **AsJob** för att köra fjärrkommandot som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="20e31-160">The command uses the **AsJob** parameter to run the remote command as a background job.</span></span>

<span data-ttu-id="20e31-161">Det här kommandot returnerar ett jobb objekt, vilket är samma jobb objekt som `Start-Job` cmdleten returnerar.</span><span class="sxs-lookup"><span data-stu-id="20e31-161">This command returns a job object, which is the same job object that the `Start-Job` cmdlet returns.</span></span>
<span data-ttu-id="20e31-162">Kommandot sparar jobbobjektet i `$j` variabeln.</span><span class="sxs-lookup"><span data-stu-id="20e31-162">The command saves the job object in the `$j` variable.</span></span>

<span data-ttu-id="20e31-163">Det andra kommandot använder en pipeline-operator för att skicka jobbet i `$j` variabeln till `Stop-Job` .</span><span class="sxs-lookup"><span data-stu-id="20e31-163">The second command uses a pipeline operator to send the job in the `$j` variable to `Stop-Job`.</span></span> <span data-ttu-id="20e31-164">Kommandot använder parametern **Passthru** för att dirigera `Stop-Job` för att returnera ett jobb objekt.</span><span class="sxs-lookup"><span data-stu-id="20e31-164">The command uses the **PassThru** parameter to direct `Stop-Job` to return a job object.</span></span> <span data-ttu-id="20e31-165">Jobb objekts visningen bekräftar att jobbets tillstånd har stoppats.</span><span class="sxs-lookup"><span data-stu-id="20e31-165">The job object display confirms that the state of the job is Stopped.</span></span>

<span data-ttu-id="20e31-166">Mer information om fjärran sluten bakgrunds jobb finns about_Remote_Jobs.</span><span class="sxs-lookup"><span data-stu-id="20e31-166">For more information about remote background jobs, see about_Remote_Jobs.</span></span>

## <span data-ttu-id="20e31-167">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="20e31-167">PARAMETERS</span></span>

### <span data-ttu-id="20e31-168">-Filter</span><span class="sxs-lookup"><span data-stu-id="20e31-168">-Filter</span></span>

<span data-ttu-id="20e31-169">Anger en hash-tabell med villkor.</span><span class="sxs-lookup"><span data-stu-id="20e31-169">Specifies a hash table of conditions.</span></span> <span data-ttu-id="20e31-170">Denna cmdlet stoppar jobb som uppfyller alla villkor.</span><span class="sxs-lookup"><span data-stu-id="20e31-170">This cmdlet stops jobs that satisfy all of the conditions.</span></span>
<span data-ttu-id="20e31-171">Ange en hash-tabell där nycklarna är jobb egenskaper och värdena är jobb egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="20e31-171">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="20e31-172">Den här parametern fungerar bara på anpassade jobb typer, till exempel arbets flödes jobb och schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="20e31-172">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span> <span data-ttu-id="20e31-173">Den fungerar inte på vanliga bakgrunds jobb, till exempel de som skapats med hjälp av `Start-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="20e31-173">It does not work on standard background jobs, such as those created by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="20e31-174">Information om stöd för den här parametern finns i hjälp avsnittet för jobb typen.</span><span class="sxs-lookup"><span data-stu-id="20e31-174">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="20e31-175">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="20e31-175">This parameter was introduced in Windows PowerShell 3.0.</span></span>

```yaml
Type: System.Collections.Hashtable
Parameter Sets: FilterParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="20e31-176">-ID</span><span class="sxs-lookup"><span data-stu-id="20e31-176">-Id</span></span>

<span data-ttu-id="20e31-177">Anger ID: n för jobb som denna cmdlet stoppar.</span><span class="sxs-lookup"><span data-stu-id="20e31-177">Specifies the IDs of jobs that this cmdlet stops.</span></span> <span data-ttu-id="20e31-178">Standardvärdet är alla jobb i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="20e31-178">The default is all jobs in the current session.</span></span>

<span data-ttu-id="20e31-179">ID är ett heltal som unikt identifierar jobbet i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="20e31-179">The ID is an integer that uniquely identifies the job in the current session.</span></span> <span data-ttu-id="20e31-180">Det är enklare att komma ihåg och skriva än instans-ID, men det är endast unikt i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="20e31-180">It is easier to remember and type than the instance ID, but it is unique only in the current session.</span></span> <span data-ttu-id="20e31-181">Du kan ange ett eller flera ID: n, avgränsade med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="20e31-181">You can type one or more IDs, separated by commas.</span></span> <span data-ttu-id="20e31-182">Om du vill hitta ID: t för ett jobb skriver du `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="20e31-182">To find the ID of a job, type `Get-Job`.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="20e31-183">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="20e31-183">-InstanceId</span></span>

<span data-ttu-id="20e31-184">Anger instans-ID: n för jobb som denna cmdlet stoppar.</span><span class="sxs-lookup"><span data-stu-id="20e31-184">Specifies the instance IDs of jobs that this cmdlet stops.</span></span> <span data-ttu-id="20e31-185">Standardvärdet är alla jobb.</span><span class="sxs-lookup"><span data-stu-id="20e31-185">The default is all jobs.</span></span>

<span data-ttu-id="20e31-186">Ett instans-ID är ett GUID som unikt identifierar jobbet på datorn.</span><span class="sxs-lookup"><span data-stu-id="20e31-186">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span> <span data-ttu-id="20e31-187">Använd om du vill hitta instans-ID: t för ett jobb `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="20e31-187">To find the instance ID of a job, use `Get-Job`.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="20e31-188">– Jobb</span><span class="sxs-lookup"><span data-stu-id="20e31-188">-Job</span></span>

<span data-ttu-id="20e31-189">Anger de jobb som denna cmdlet stoppar.</span><span class="sxs-lookup"><span data-stu-id="20e31-189">Specifies the jobs that this cmdlet stops.</span></span> <span data-ttu-id="20e31-190">Ange en variabel som innehåller jobben eller ett kommando som hämtar jobben.</span><span class="sxs-lookup"><span data-stu-id="20e31-190">Enter a variable that contains the jobs or a command that gets the jobs.</span></span> <span data-ttu-id="20e31-191">Du kan också använda en pipeline-operatör för att skicka jobb till `Stop-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="20e31-191">You can also use a pipeline operator to submit jobs to the `Stop-Job` cmdlet.</span></span> <span data-ttu-id="20e31-192">Som standard `Stop-Job` tar bort alla jobb som startades i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="20e31-192">By default, `Stop-Job` deletes all jobs that were started in the current session.</span></span>

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="20e31-193">-Name</span><span class="sxs-lookup"><span data-stu-id="20e31-193">-Name</span></span>

<span data-ttu-id="20e31-194">Anger egna namn på jobb som denna cmdlet stoppar.</span><span class="sxs-lookup"><span data-stu-id="20e31-194">Specifies friendly names of jobs that this cmdlet stops.</span></span> <span data-ttu-id="20e31-195">Ange jobb namnen i en kommaavgränsad lista eller Använd jokertecken (\*) för att ange ett jobb namns mönster.</span><span class="sxs-lookup"><span data-stu-id="20e31-195">Enter the job names in a comma-separated list or use wildcard characters (\*) to enter a job name pattern.</span></span> <span data-ttu-id="20e31-196">Som standard `Stop-Job` stoppas alla jobb som skapas i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="20e31-196">By default, `Stop-Job` stops all jobs created in the current session.</span></span>

<span data-ttu-id="20e31-197">Eftersom det egna namnet inte garanterat är unikt använder du parametrarna **whatIf** och **Confirm** när du stoppar jobb efter namn.</span><span class="sxs-lookup"><span data-stu-id="20e31-197">Because the friendly name is not guaranteed to be unique, use the **WhatIf** and **Confirm** parameters when stopping jobs by name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="20e31-198">– PassThru</span><span class="sxs-lookup"><span data-stu-id="20e31-198">-PassThru</span></span>

<span data-ttu-id="20e31-199">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="20e31-199">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="20e31-200">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="20e31-200">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="20e31-201">– Tillstånd</span><span class="sxs-lookup"><span data-stu-id="20e31-201">-State</span></span>

<span data-ttu-id="20e31-202">Anger ett jobb tillstånd.</span><span class="sxs-lookup"><span data-stu-id="20e31-202">Specifies a job state.</span></span> <span data-ttu-id="20e31-203">Denna cmdlet stoppar endast jobb i det angivna läget.</span><span class="sxs-lookup"><span data-stu-id="20e31-203">This cmdlet stops only jobs in the specified state.</span></span> <span data-ttu-id="20e31-204">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="20e31-204">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="20e31-205">NotStarted</span><span class="sxs-lookup"><span data-stu-id="20e31-205">NotStarted</span></span>
- <span data-ttu-id="20e31-206">Körs</span><span class="sxs-lookup"><span data-stu-id="20e31-206">Running</span></span>
- <span data-ttu-id="20e31-207">Slutförd</span><span class="sxs-lookup"><span data-stu-id="20e31-207">Completed</span></span>
- <span data-ttu-id="20e31-208">Misslyckad</span><span class="sxs-lookup"><span data-stu-id="20e31-208">Failed</span></span>
- <span data-ttu-id="20e31-209">Stoppad</span><span class="sxs-lookup"><span data-stu-id="20e31-209">Stopped</span></span>
- <span data-ttu-id="20e31-210">Blockerad</span><span class="sxs-lookup"><span data-stu-id="20e31-210">Blocked</span></span>
- <span data-ttu-id="20e31-211">Inaktiverad</span><span class="sxs-lookup"><span data-stu-id="20e31-211">Suspended</span></span>
- <span data-ttu-id="20e31-212">Frånkopplad</span><span class="sxs-lookup"><span data-stu-id="20e31-212">Disconnected</span></span>
- <span data-ttu-id="20e31-213">Pausar</span><span class="sxs-lookup"><span data-stu-id="20e31-213">Suspending</span></span>
- <span data-ttu-id="20e31-214">Stoppas</span><span class="sxs-lookup"><span data-stu-id="20e31-214">Stopping</span></span>

<span data-ttu-id="20e31-215">Mer information om jobb tillstånd finns i [JobState-uppräkning](/dotnet/api/system.management.automation.jobstate).</span><span class="sxs-lookup"><span data-stu-id="20e31-215">For more information about job states, see [JobState Enumeration](/dotnet/api/system.management.automation.jobstate).</span></span>

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: True
Position: 0
Default value: All jobs
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="20e31-216">-Confirm</span><span class="sxs-lookup"><span data-stu-id="20e31-216">-Confirm</span></span>

<span data-ttu-id="20e31-217">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="20e31-217">Prompts you for confirmation before running the cmdlet.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="20e31-218">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="20e31-218">-WhatIf</span></span>

<span data-ttu-id="20e31-219">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="20e31-219">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="20e31-220">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="20e31-220">The cmdlet is not run.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="20e31-221">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="20e31-221">CommonParameters</span></span>

<span data-ttu-id="20e31-222">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="20e31-222">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="20e31-223">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="20e31-223">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="20e31-224">INDATA</span><span class="sxs-lookup"><span data-stu-id="20e31-224">INPUTS</span></span>

### <span data-ttu-id="20e31-225">System. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="20e31-225">System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="20e31-226">Du kan skicka vidare ett jobb objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="20e31-226">You can pipe a job object to this cmdlet.</span></span>

## <span data-ttu-id="20e31-227">UTDATA</span><span class="sxs-lookup"><span data-stu-id="20e31-227">OUTPUTS</span></span>

### <span data-ttu-id="20e31-228">Ingen, system. Management. Automation. PSRemotingJob</span><span class="sxs-lookup"><span data-stu-id="20e31-228">None, System.Management.Automation.PSRemotingJob</span></span>

<span data-ttu-id="20e31-229">Den här cmdleten returnerar ett jobb objekt, om du anger parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="20e31-229">This cmdlet returns a job object, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="20e31-230">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="20e31-230">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="20e31-231">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="20e31-231">NOTES</span></span>

## <span data-ttu-id="20e31-232">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="20e31-232">RELATED LINKS</span></span>

[<span data-ttu-id="20e31-233">Hämta jobb</span><span class="sxs-lookup"><span data-stu-id="20e31-233">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="20e31-234">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="20e31-234">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="20e31-235">Mottagning – jobb</span><span class="sxs-lookup"><span data-stu-id="20e31-235">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="20e31-236">Ta bort – jobb</span><span class="sxs-lookup"><span data-stu-id="20e31-236">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="20e31-237">Start – jobb</span><span class="sxs-lookup"><span data-stu-id="20e31-237">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="20e31-238">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="20e31-238">Wait-Job</span></span>](Wait-Job.md)

[<span data-ttu-id="20e31-239">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="20e31-239">about_Job_Details</span></span>](About/about_Job_Details.md)

[<span data-ttu-id="20e31-240">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="20e31-240">about_Remote_Jobs</span></span>](About/about_Remote_Jobs.md)

[<span data-ttu-id="20e31-241">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="20e31-241">about_Remote_Variables</span></span>](About/about_Remote_Variables.md)

[<span data-ttu-id="20e31-242">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="20e31-242">about_Jobs</span></span>](About/about_Jobs.md)

[<span data-ttu-id="20e31-243">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="20e31-243">about_Scopes</span></span>](About/about_scopes.md)
