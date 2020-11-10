---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/stop-job?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Job
ms.openlocfilehash: 77982029240727ff5c7c90866d1a67cf7cae794d
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94391314"
---
# <span data-ttu-id="f41aa-103">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="f41aa-103">Stop-Job</span></span>

## <span data-ttu-id="f41aa-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="f41aa-104">SYNOPSIS</span></span>
<span data-ttu-id="f41aa-105">Stoppar ett PowerShell-bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="f41aa-105">Stops a PowerShell background job.</span></span>

## <span data-ttu-id="f41aa-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f41aa-106">SYNTAX</span></span>

### <span data-ttu-id="f41aa-107">SessionIdParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="f41aa-107">SessionIdParameterSet (Default)</span></span>

```
Stop-Job [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f41aa-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="f41aa-108">JobParameterSet</span></span>

```
Stop-Job [-Job] <Job[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f41aa-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="f41aa-109">NameParameterSet</span></span>

```
Stop-Job [-PassThru] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f41aa-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="f41aa-110">InstanceIdParameterSet</span></span>

```
Stop-Job [-PassThru] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f41aa-111">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="f41aa-111">StateParameterSet</span></span>

```
Stop-Job [-PassThru] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f41aa-112">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="f41aa-112">FilterParameterSet</span></span>

```
Stop-Job [-PassThru] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f41aa-113">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="f41aa-113">DESCRIPTION</span></span>

<span data-ttu-id="f41aa-114">`Stop-Job`Cmdleten stoppar PowerShell-bakgrunds jobb som pågår.</span><span class="sxs-lookup"><span data-stu-id="f41aa-114">The `Stop-Job` cmdlet stops PowerShell background jobs that are in progress.</span></span> <span data-ttu-id="f41aa-115">Du kan använda den här cmdleten för att stoppa alla jobb eller stoppa valda jobb baserat på namn, ID, instans-ID eller tillstånd, eller genom att skicka ett jobb objekt till `Stop-Job` .</span><span class="sxs-lookup"><span data-stu-id="f41aa-115">You can use this cmdlet to stop all jobs or stop selected jobs based on their name, ID, instance ID, or state, or by passing a job object to `Stop-Job`.</span></span>

<span data-ttu-id="f41aa-116">Du kan använda `Stop-Job` för att stoppa bakgrunds jobb, till exempel de som startades med hjälp av `Start-Job` cmdleten eller parametern **AsJob** för valfri cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f41aa-116">You can use `Stop-Job` to stop background jobs, such as those that were started by using the `Start-Job` cmdlet or the **AsJob** parameter of any cmdlet.</span></span> <span data-ttu-id="f41aa-117">När du stoppar ett bakgrunds jobb Slutför PowerShell alla uppgifter som väntar i jobbkön och avslutar sedan jobbet.</span><span class="sxs-lookup"><span data-stu-id="f41aa-117">When you stop a background job, PowerShell completes all tasks that are pending in that job queue and then ends the job.</span></span> <span data-ttu-id="f41aa-118">Inga nya aktiviteter läggs till i kön när det här kommandot har skickats.</span><span class="sxs-lookup"><span data-stu-id="f41aa-118">No new tasks are added to the queue after this command is submitted.</span></span>

<span data-ttu-id="f41aa-119">Den här cmdleten tar inte bort bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="f41aa-119">This cmdlet does not delete background jobs.</span></span> <span data-ttu-id="f41aa-120">Använd cmdleten om du vill ta bort ett jobb `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="f41aa-120">To delete a job, use the `Remove-Job` cmdlet.</span></span>

<span data-ttu-id="f41aa-121">Från och med Windows PowerShell 3,0 `Stop-Job` stoppas även anpassade jobb typer, till exempel arbets flödes jobb och instanser av schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="f41aa-121">Starting in Windows PowerShell 3.0, `Stop-Job` also stops custom job types, such as workflow jobs and instances of scheduled jobs.</span></span> <span data-ttu-id="f41aa-122">Om du vill `Stop-Job` stoppa ett jobb med anpassad Jobbtyp importerar du modulen som stöder den anpassade jobb typen till sessionen innan du kör ett `Stop-Job` kommando, antingen med hjälp av `Import-Module` cmdleten eller genom att använda eller hämta en cmdlet i modulen.</span><span class="sxs-lookup"><span data-stu-id="f41aa-122">To enable `Stop-Job` to stop a job with custom job type, import the module that supports the custom job type into the session before you run a `Stop-Job` command, either by using the `Import-Module` cmdlet or by using or getting a cmdlet in the module.</span></span> <span data-ttu-id="f41aa-123">Information om en viss anpassad Jobbtyp finns i dokumentationen för den anpassade jobb typ funktionen.</span><span class="sxs-lookup"><span data-stu-id="f41aa-123">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="f41aa-124">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="f41aa-124">EXAMPLES</span></span>

### <span data-ttu-id="f41aa-125">Exempel 1: stoppa ett jobb på en fjärrdator med hjälp av Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="f41aa-125">Example 1: Stop a job on a remote computer by using Invoke-Command</span></span>

```powershell
$s = New-PSSession -ComputerName Server01 -Credential Domain01\Admin02
$j = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Invoke-Command -Session $s -ScriptBlock { Stop-job -Job $Using:j }
```

<span data-ttu-id="f41aa-126">Det här exemplet visar hur du kan använda `Stop-Job` cmdleten för att stoppa ett jobb som körs på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="f41aa-126">This example shows how to use the `Stop-Job` cmdlet to stop a job that is running on a remote computer.</span></span>

<span data-ttu-id="f41aa-127">Eftersom jobbet startades med hjälp av `Invoke-Command` cmdleten för att köra ett `Start-Job` kommando på distans, lagras jobbobjektet på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="f41aa-127">Because the job was started by using the `Invoke-Command` cmdlet to run a `Start-Job` command remotely, the job object is stored on the remote computer.</span></span> <span data-ttu-id="f41aa-128">Du måste använda ett annat `Invoke-Command` kommando om du vill köra ett `Stop-Job` kommando via fjärr anslutning.</span><span class="sxs-lookup"><span data-stu-id="f41aa-128">You must use another `Invoke-Command` command to run a `Stop-Job` command remotely.</span></span> <span data-ttu-id="f41aa-129">Mer information om fjärran sluten bakgrunds jobb finns about_Remote_Jobs.</span><span class="sxs-lookup"><span data-stu-id="f41aa-129">For more information about remote background jobs, see about_Remote_Jobs.</span></span>

<span data-ttu-id="f41aa-130">Det första kommandot skapar en PowerShell-session ( **PSSession** ) på Server01-datorn och lagrar sedan Session-objektet i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="f41aa-130">The first command creates a PowerShell session ( **PSSession** ) on the Server01 computer, and then stores the session object in the `$s` variable.</span></span> <span data-ttu-id="f41aa-131">Kommandot använder autentiseringsuppgifterna för en domän administratör.</span><span class="sxs-lookup"><span data-stu-id="f41aa-131">The command uses the credentials of a domain administrator.</span></span>

<span data-ttu-id="f41aa-132">Det andra kommandot använder `Invoke-Command` cmdleten för att köra ett `Start-Job` kommando i sessionen.</span><span class="sxs-lookup"><span data-stu-id="f41aa-132">The second command uses the `Invoke-Command` cmdlet to run a `Start-Job` command in the session.</span></span> <span data-ttu-id="f41aa-133">Kommandot i jobbet hämtar alla händelser i system händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="f41aa-133">The command in the job gets all of the events in the System event log.</span></span> <span data-ttu-id="f41aa-134">Resulterande jobb objekt lagras i `$j` variabeln.</span><span class="sxs-lookup"><span data-stu-id="f41aa-134">The resulting job object is stored in the `$j` variable.</span></span>

<span data-ttu-id="f41aa-135">Det tredje kommandot stoppar jobbet.</span><span class="sxs-lookup"><span data-stu-id="f41aa-135">The third command stops the job.</span></span> <span data-ttu-id="f41aa-136">Den använder `Invoke-Command` cmdleten för att köra ett `Stop-Job` kommando i **PSSession** på Server01.</span><span class="sxs-lookup"><span data-stu-id="f41aa-136">It uses the `Invoke-Command` cmdlet to run a `Stop-Job` command in the **PSSession** on Server01.</span></span> <span data-ttu-id="f41aa-137">Eftersom jobb objekt lagras i `$j` , vilket är en variabel på den lokala datorn, använder kommandot Använd omfångs modifieraren för att identifiera `$j` som en lokal variabel.</span><span class="sxs-lookup"><span data-stu-id="f41aa-137">Because the job objects are stored in `$j`, which is a variable on the local computer, the command uses the Using scope modifier to identify `$j` as a local variable.</span></span>
<span data-ttu-id="f41aa-138">Mer information om hur du använder omfångs modifieraren finns [about_Remote_Variables](about/about_Remote_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="f41aa-138">For more information about the Using scope modifier, see [about_Remote_Variables](about/about_Remote_Variables.md).</span></span>

<span data-ttu-id="f41aa-139">När kommandot har slutförts stoppas jobbet och **PSSession** i `$s` är tillgängligt för användning.</span><span class="sxs-lookup"><span data-stu-id="f41aa-139">When the command finishes, the job is stopped and the **PSSession** in `$s` is available for use.</span></span>

### <span data-ttu-id="f41aa-140">Exempel 2: stoppa ett bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="f41aa-140">Example 2: Stop a background job</span></span>

```powershell
Stop-Job -Name "Job1"
```

<span data-ttu-id="f41aa-141">Det här kommandot stoppar bakgrunds jobbet Job1.</span><span class="sxs-lookup"><span data-stu-id="f41aa-141">This command stops the Job1 background job.</span></span>

### <span data-ttu-id="f41aa-142">Exempel 3: stoppa flera bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="f41aa-142">Example 3: Stop several background jobs</span></span>

```powershell
Stop-Job -Id 1, 3, 4
```

<span data-ttu-id="f41aa-143">Det här kommandot stoppar tre jobb.</span><span class="sxs-lookup"><span data-stu-id="f41aa-143">This command stops three jobs.</span></span>
<span data-ttu-id="f41aa-144">Den identifierar dem med deras ID.</span><span class="sxs-lookup"><span data-stu-id="f41aa-144">It identifies them by their IDs.</span></span>

### <span data-ttu-id="f41aa-145">Exempel 4: stoppa alla bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="f41aa-145">Example 4: Stop all background jobs</span></span>

```powershell
Get-Job | Stop-Job
```

<span data-ttu-id="f41aa-146">Det här kommandot stoppar alla bakgrunds jobb i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="f41aa-146">This command stops all of the background jobs in the current session.</span></span>

### <span data-ttu-id="f41aa-147">Exempel 5: stoppa alla blockerade bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="f41aa-147">Example 5: Stop all blocked background jobs</span></span>

```powershell
Stop-Job -State Blocked
```

<span data-ttu-id="f41aa-148">Det här kommandot stoppar alla jobb som blockeras.</span><span class="sxs-lookup"><span data-stu-id="f41aa-148">This command stops all the jobs that are blocked.</span></span>

### <span data-ttu-id="f41aa-149">Exempel 6: stoppa ett jobb med hjälp av ett instans-ID</span><span class="sxs-lookup"><span data-stu-id="f41aa-149">Example 6: Stop a job by using an instance ID</span></span>

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

<span data-ttu-id="f41aa-150">Kommandona visar hur du stoppar ett jobb baserat på dess instans-ID.</span><span class="sxs-lookup"><span data-stu-id="f41aa-150">These commands show how to stop a job based on its instance ID.</span></span>

<span data-ttu-id="f41aa-151">Det första kommandot använder `Get-Job` cmdleten för att hämta jobben i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="f41aa-151">The first command uses the `Get-Job` cmdlet to get the jobs in the current session.</span></span> <span data-ttu-id="f41aa-152">Kommandot använder en pipeline-operator ( `|` ) för att skicka jobben till ett `Format-Table` kommando, som visar en tabell med de angivna egenskaperna för varje jobb.</span><span class="sxs-lookup"><span data-stu-id="f41aa-152">The command uses a pipeline operator (`|`) to send the jobs to a `Format-Table` command, which displays a table of the specified properties of each job.</span></span> <span data-ttu-id="f41aa-153">Tabellen innehåller instans-ID för varje jobb.</span><span class="sxs-lookup"><span data-stu-id="f41aa-153">The table includes the Instance ID of each job.</span></span> <span data-ttu-id="f41aa-154">Den använder en beräknad egenskap för att visa jobb status.</span><span class="sxs-lookup"><span data-stu-id="f41aa-154">It uses a calculated property to display the job state.</span></span>

<span data-ttu-id="f41aa-155">Det andra kommandot använder ett `Stop-Job` kommando som har **InstanceID** -parametern för att stoppa ett valt jobb.</span><span class="sxs-lookup"><span data-stu-id="f41aa-155">The second command uses a `Stop-Job` command that has the **InstanceID** parameter to stop a selected job.</span></span>

### <span data-ttu-id="f41aa-156">Exempel 7: stoppa ett jobb på en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="f41aa-156">Example 7: Stop a job on a remote computer</span></span>

```powershell
$j = Invoke-Command -ComputerName Server01 -ScriptBlock {Get-EventLog System} -AsJob
$j | Stop-Job -PassThru
```

```Output
Id    Name    State      HasMoreData     Location         Command
--    ----    ----       -----------     --------         -------
5     Job5    Stopped    True            user01-tablet    get-eventlog system
```

<span data-ttu-id="f41aa-157">Det här exemplet visar hur du kan använda `Stop-Job` cmdleten för att stoppa ett jobb som körs på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="f41aa-157">This example shows how to use the `Stop-Job` cmdlet to stop a job that is running on a remote computer.</span></span>

<span data-ttu-id="f41aa-158">Eftersom jobbet startades med hjälp av parametern **AsJob** i `Invoke-Command` cmdleten, finns jobbobjektet på den lokala datorn, även om jobbet körs på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="f41aa-158">Because the job was started by using the **AsJob** parameter of the `Invoke-Command` cmdlet, the job object is located on the local computer, even though the job runs on the remote computer.</span></span> <span data-ttu-id="f41aa-159">Därför kan du använda ett lokalt `Stop-Job` kommando för att stoppa jobbet.</span><span class="sxs-lookup"><span data-stu-id="f41aa-159">Therefore, you can use a local `Stop-Job` command to stop the job.</span></span>

<span data-ttu-id="f41aa-160">Det första kommandot använder `Invoke-Command` cmdleten för att starta ett bakgrunds jobb på Server01-datorn.</span><span class="sxs-lookup"><span data-stu-id="f41aa-160">The first command uses the `Invoke-Command` cmdlet to start a background job on the Server01 computer.</span></span> <span data-ttu-id="f41aa-161">Kommandot använder parametern **AsJob** för att köra fjärrkommandot som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="f41aa-161">The command uses the **AsJob** parameter to run the remote command as a background job.</span></span>

<span data-ttu-id="f41aa-162">Det här kommandot returnerar ett jobb objekt, vilket är samma jobb objekt som `Start-Job` cmdleten returnerar.</span><span class="sxs-lookup"><span data-stu-id="f41aa-162">This command returns a job object, which is the same job object that the `Start-Job` cmdlet returns.</span></span>
<span data-ttu-id="f41aa-163">Kommandot sparar jobbobjektet i `$j` variabeln.</span><span class="sxs-lookup"><span data-stu-id="f41aa-163">The command saves the job object in the `$j` variable.</span></span>

<span data-ttu-id="f41aa-164">Det andra kommandot använder en pipeline-operator för att skicka jobbet i `$j` variabeln till `Stop-Job` .</span><span class="sxs-lookup"><span data-stu-id="f41aa-164">The second command uses a pipeline operator to send the job in the `$j` variable to `Stop-Job`.</span></span> <span data-ttu-id="f41aa-165">Kommandot använder parametern **Passthru** för att dirigera `Stop-Job` för att returnera ett jobb objekt.</span><span class="sxs-lookup"><span data-stu-id="f41aa-165">The command uses the **PassThru** parameter to direct `Stop-Job` to return a job object.</span></span> <span data-ttu-id="f41aa-166">Jobb objekts visningen bekräftar att jobbets tillstånd har stoppats.</span><span class="sxs-lookup"><span data-stu-id="f41aa-166">The job object display confirms that the state of the job is Stopped.</span></span>

<span data-ttu-id="f41aa-167">Mer information om fjärran sluten bakgrunds jobb finns about_Remote_Jobs.</span><span class="sxs-lookup"><span data-stu-id="f41aa-167">For more information about remote background jobs, see about_Remote_Jobs.</span></span>

## <span data-ttu-id="f41aa-168">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="f41aa-168">PARAMETERS</span></span>

### <span data-ttu-id="f41aa-169">-Filter</span><span class="sxs-lookup"><span data-stu-id="f41aa-169">-Filter</span></span>

<span data-ttu-id="f41aa-170">Anger en hash-tabell med villkor.</span><span class="sxs-lookup"><span data-stu-id="f41aa-170">Specifies a hash table of conditions.</span></span> <span data-ttu-id="f41aa-171">Denna cmdlet stoppar jobb som uppfyller alla villkor.</span><span class="sxs-lookup"><span data-stu-id="f41aa-171">This cmdlet stops jobs that satisfy all of the conditions.</span></span>
<span data-ttu-id="f41aa-172">Ange en hash-tabell där nycklarna är jobb egenskaper och värdena är jobb egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="f41aa-172">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="f41aa-173">Den här parametern fungerar bara på anpassade jobb typer, till exempel arbets flödes jobb och schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="f41aa-173">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span> <span data-ttu-id="f41aa-174">Den fungerar inte på vanliga bakgrunds jobb, till exempel de som skapats med hjälp av `Start-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f41aa-174">It does not work on standard background jobs, such as those created by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="f41aa-175">Information om stöd för den här parametern finns i hjälp avsnittet för jobb typen.</span><span class="sxs-lookup"><span data-stu-id="f41aa-175">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="f41aa-176">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="f41aa-176">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="f41aa-177">-ID</span><span class="sxs-lookup"><span data-stu-id="f41aa-177">-Id</span></span>

<span data-ttu-id="f41aa-178">Anger ID: n för jobb som denna cmdlet stoppar.</span><span class="sxs-lookup"><span data-stu-id="f41aa-178">Specifies the IDs of jobs that this cmdlet stops.</span></span> <span data-ttu-id="f41aa-179">Standardvärdet är alla jobb i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="f41aa-179">The default is all jobs in the current session.</span></span>

<span data-ttu-id="f41aa-180">ID är ett heltal som unikt identifierar jobbet i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="f41aa-180">The ID is an integer that uniquely identifies the job in the current session.</span></span> <span data-ttu-id="f41aa-181">Det är enklare att komma ihåg och skriva än instans-ID, men det är endast unikt i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="f41aa-181">It is easier to remember and type than the instance ID, but it is unique only in the current session.</span></span> <span data-ttu-id="f41aa-182">Du kan ange ett eller flera ID: n, avgränsade med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="f41aa-182">You can type one or more IDs, separated by commas.</span></span> <span data-ttu-id="f41aa-183">Om du vill hitta ID: t för ett jobb skriver du `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="f41aa-183">To find the ID of a job, type `Get-Job`.</span></span>

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

### <span data-ttu-id="f41aa-184">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="f41aa-184">-InstanceId</span></span>

<span data-ttu-id="f41aa-185">Anger instans-ID: n för jobb som denna cmdlet stoppar.</span><span class="sxs-lookup"><span data-stu-id="f41aa-185">Specifies the instance IDs of jobs that this cmdlet stops.</span></span> <span data-ttu-id="f41aa-186">Standardvärdet är alla jobb.</span><span class="sxs-lookup"><span data-stu-id="f41aa-186">The default is all jobs.</span></span>

<span data-ttu-id="f41aa-187">Ett instans-ID är ett GUID som unikt identifierar jobbet på datorn.</span><span class="sxs-lookup"><span data-stu-id="f41aa-187">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span> <span data-ttu-id="f41aa-188">Använd om du vill hitta instans-ID: t för ett jobb `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="f41aa-188">To find the instance ID of a job, use `Get-Job`.</span></span>

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

### <span data-ttu-id="f41aa-189">– Jobb</span><span class="sxs-lookup"><span data-stu-id="f41aa-189">-Job</span></span>

<span data-ttu-id="f41aa-190">Anger de jobb som denna cmdlet stoppar.</span><span class="sxs-lookup"><span data-stu-id="f41aa-190">Specifies the jobs that this cmdlet stops.</span></span> <span data-ttu-id="f41aa-191">Ange en variabel som innehåller jobben eller ett kommando som hämtar jobben.</span><span class="sxs-lookup"><span data-stu-id="f41aa-191">Enter a variable that contains the jobs or a command that gets the jobs.</span></span> <span data-ttu-id="f41aa-192">Du kan också använda en pipeline-operatör för att skicka jobb till `Stop-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f41aa-192">You can also use a pipeline operator to submit jobs to the `Stop-Job` cmdlet.</span></span> <span data-ttu-id="f41aa-193">Som standard `Stop-Job` tar bort alla jobb som startades i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="f41aa-193">By default, `Stop-Job` deletes all jobs that were started in the current session.</span></span>

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

### <span data-ttu-id="f41aa-194">-Name</span><span class="sxs-lookup"><span data-stu-id="f41aa-194">-Name</span></span>

<span data-ttu-id="f41aa-195">Anger egna namn på jobb som denna cmdlet stoppar.</span><span class="sxs-lookup"><span data-stu-id="f41aa-195">Specifies friendly names of jobs that this cmdlet stops.</span></span> <span data-ttu-id="f41aa-196">Ange jobb namnen i en kommaavgränsad lista eller Använd jokertecken (\*) för att ange ett jobb namns mönster.</span><span class="sxs-lookup"><span data-stu-id="f41aa-196">Enter the job names in a comma-separated list or use wildcard characters (\*) to enter a job name pattern.</span></span> <span data-ttu-id="f41aa-197">Som standard `Stop-Job` stoppas alla jobb som skapas i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="f41aa-197">By default, `Stop-Job` stops all jobs created in the current session.</span></span>

<span data-ttu-id="f41aa-198">Eftersom det egna namnet inte garanterat är unikt använder du parametrarna **whatIf** och **Confirm** när du stoppar jobb efter namn.</span><span class="sxs-lookup"><span data-stu-id="f41aa-198">Because the friendly name is not guaranteed to be unique, use the **WhatIf** and **Confirm** parameters when stopping jobs by name.</span></span>

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

### <span data-ttu-id="f41aa-199">– PassThru</span><span class="sxs-lookup"><span data-stu-id="f41aa-199">-PassThru</span></span>

<span data-ttu-id="f41aa-200">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="f41aa-200">Returns an object representing the item with which you are working.</span></span> <span data-ttu-id="f41aa-201">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="f41aa-201">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="f41aa-202">– Tillstånd</span><span class="sxs-lookup"><span data-stu-id="f41aa-202">-State</span></span>

<span data-ttu-id="f41aa-203">Anger ett jobb tillstånd.</span><span class="sxs-lookup"><span data-stu-id="f41aa-203">Specifies a job state.</span></span> <span data-ttu-id="f41aa-204">Denna cmdlet stoppar endast jobb i det angivna läget.</span><span class="sxs-lookup"><span data-stu-id="f41aa-204">This cmdlet stops only jobs in the specified state.</span></span> <span data-ttu-id="f41aa-205">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="f41aa-205">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="f41aa-206">NotStarted</span><span class="sxs-lookup"><span data-stu-id="f41aa-206">NotStarted</span></span>
- <span data-ttu-id="f41aa-207">Körs</span><span class="sxs-lookup"><span data-stu-id="f41aa-207">Running</span></span>
- <span data-ttu-id="f41aa-208">Slutförd</span><span class="sxs-lookup"><span data-stu-id="f41aa-208">Completed</span></span>
- <span data-ttu-id="f41aa-209">Misslyckad</span><span class="sxs-lookup"><span data-stu-id="f41aa-209">Failed</span></span>
- <span data-ttu-id="f41aa-210">Stoppad</span><span class="sxs-lookup"><span data-stu-id="f41aa-210">Stopped</span></span>
- <span data-ttu-id="f41aa-211">Blockerad</span><span class="sxs-lookup"><span data-stu-id="f41aa-211">Blocked</span></span>
- <span data-ttu-id="f41aa-212">Inaktiverad</span><span class="sxs-lookup"><span data-stu-id="f41aa-212">Suspended</span></span>
- <span data-ttu-id="f41aa-213">Frånkopplad</span><span class="sxs-lookup"><span data-stu-id="f41aa-213">Disconnected</span></span>
- <span data-ttu-id="f41aa-214">Pausar</span><span class="sxs-lookup"><span data-stu-id="f41aa-214">Suspending</span></span>
- <span data-ttu-id="f41aa-215">Stoppas</span><span class="sxs-lookup"><span data-stu-id="f41aa-215">Stopping</span></span>

<span data-ttu-id="f41aa-216">Mer information om jobb tillstånd finns i [JobState-uppräkning](/dotnet/api/system.management.automation.jobstate).</span><span class="sxs-lookup"><span data-stu-id="f41aa-216">For more information about job states, see [JobState Enumeration](/dotnet/api/system.management.automation.jobstate).</span></span>

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

### <span data-ttu-id="f41aa-217">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f41aa-217">-Confirm</span></span>

<span data-ttu-id="f41aa-218">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f41aa-218">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f41aa-219">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f41aa-219">-WhatIf</span></span>

<span data-ttu-id="f41aa-220">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="f41aa-220">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="f41aa-221">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="f41aa-221">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="f41aa-222">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f41aa-222">CommonParameters</span></span>

<span data-ttu-id="f41aa-223">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f41aa-223">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f41aa-224">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f41aa-224">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f41aa-225">INDATA</span><span class="sxs-lookup"><span data-stu-id="f41aa-225">INPUTS</span></span>

### <span data-ttu-id="f41aa-226">System. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="f41aa-226">System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="f41aa-227">Du kan skicka vidare ett jobb objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f41aa-227">You can pipe a job object to this cmdlet.</span></span>

## <span data-ttu-id="f41aa-228">UTDATA</span><span class="sxs-lookup"><span data-stu-id="f41aa-228">OUTPUTS</span></span>

### <span data-ttu-id="f41aa-229">Ingen, system. Management. Automation. PSRemotingJob</span><span class="sxs-lookup"><span data-stu-id="f41aa-229">None, System.Management.Automation.PSRemotingJob</span></span>

<span data-ttu-id="f41aa-230">Den här cmdleten returnerar ett jobb objekt, om du anger parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="f41aa-230">This cmdlet returns a job object, if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="f41aa-231">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="f41aa-231">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="f41aa-232">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="f41aa-232">NOTES</span></span>

## <span data-ttu-id="f41aa-233">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="f41aa-233">RELATED LINKS</span></span>

[<span data-ttu-id="f41aa-234">Hämta jobb</span><span class="sxs-lookup"><span data-stu-id="f41aa-234">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="f41aa-235">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="f41aa-235">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="f41aa-236">Mottagning – jobb</span><span class="sxs-lookup"><span data-stu-id="f41aa-236">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="f41aa-237">Ta bort – jobb</span><span class="sxs-lookup"><span data-stu-id="f41aa-237">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="f41aa-238">Start – jobb</span><span class="sxs-lookup"><span data-stu-id="f41aa-238">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="f41aa-239">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="f41aa-239">Wait-Job</span></span>](Wait-Job.md)

[<span data-ttu-id="f41aa-240">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="f41aa-240">about_Job_Details</span></span>](About/about_Job_Details.md)

[<span data-ttu-id="f41aa-241">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="f41aa-241">about_Remote_Jobs</span></span>](About/about_Remote_Jobs.md)

[<span data-ttu-id="f41aa-242">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="f41aa-242">about_Remote_Variables</span></span>](About/about_Remote_Variables.md)

[<span data-ttu-id="f41aa-243">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="f41aa-243">about_Jobs</span></span>](About/about_Jobs.md)

[<span data-ttu-id="f41aa-244">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="f41aa-244">about_Scopes</span></span>](About/about_scopes.md)
