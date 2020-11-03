---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/stop-job?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Job
ms.openlocfilehash: d6f1b3a719724073919930b1f1c0839250b5d2c8
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267266"
---
# <span data-ttu-id="f0544-103">Stop-Job</span><span class="sxs-lookup"><span data-stu-id="f0544-103">Stop-Job</span></span>

## <span data-ttu-id="f0544-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="f0544-104">SYNOPSIS</span></span>
<span data-ttu-id="f0544-105">Stoppar ett PowerShell-bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="f0544-105">Stops a PowerShell background job.</span></span>

## <span data-ttu-id="f0544-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="f0544-106">SYNTAX</span></span>

### <span data-ttu-id="f0544-107">SessionIdParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="f0544-107">SessionIdParameterSet (Default)</span></span>

```
Stop-Job [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f0544-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="f0544-108">JobParameterSet</span></span>

```
Stop-Job [-Job] <Job[]> [-PassThru] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f0544-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="f0544-109">NameParameterSet</span></span>

```
Stop-Job [-PassThru] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f0544-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="f0544-110">InstanceIdParameterSet</span></span>

```
Stop-Job [-PassThru] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f0544-111">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="f0544-111">StateParameterSet</span></span>

```
Stop-Job [-PassThru] [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="f0544-112">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="f0544-112">FilterParameterSet</span></span>

```
Stop-Job [-PassThru] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="f0544-113">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="f0544-113">DESCRIPTION</span></span>

<span data-ttu-id="f0544-114">Cmdleten **stoppa-Job** stoppar PowerShell-bakgrunds jobb som pågår.</span><span class="sxs-lookup"><span data-stu-id="f0544-114">The **Stop-Job** cmdlet stops PowerShell background jobs that are in progress.</span></span>
<span data-ttu-id="f0544-115">Du kan använda den här cmdleten för att stoppa alla jobb eller stoppa valda jobb baserat på namn, ID, instans-ID eller tillstånd, eller genom att skicka ett jobb objekt till **stopp-jobb**.</span><span class="sxs-lookup"><span data-stu-id="f0544-115">You can use this cmdlet to stop all jobs or stop selected jobs based on their name, ID, instance ID, or state, or by passing a job object to **Stop-Job**.</span></span>

<span data-ttu-id="f0544-116">Du kan använda **stopp-jobb** för att stoppa bakgrunds jobb, till exempel de som startades med hjälp av Start-Job-cmdlet eller parametern *AsJob* för någon cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f0544-116">You can use **Stop-Job** to stop background jobs, such as those that were started by using the Start-Job cmdlet or the *AsJob* parameter of any cmdlet.</span></span>
<span data-ttu-id="f0544-117">När du stoppar ett bakgrunds jobb Slutför PowerShell alla uppgifter som väntar i jobbkön och avslutar sedan jobbet.</span><span class="sxs-lookup"><span data-stu-id="f0544-117">When you stop a background job, PowerShell completes all tasks that are pending in that job queue and then ends the job.</span></span>
<span data-ttu-id="f0544-118">Inga nya aktiviteter läggs till i kön när det här kommandot har skickats.</span><span class="sxs-lookup"><span data-stu-id="f0544-118">No new tasks are added to the queue after this command is submitted.</span></span>

<span data-ttu-id="f0544-119">Den här cmdleten tar inte bort bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="f0544-119">This cmdlet does not delete background jobs.</span></span>
<span data-ttu-id="f0544-120">Använd Remove-Job-cmdleten om du vill ta bort ett jobb.</span><span class="sxs-lookup"><span data-stu-id="f0544-120">To delete a job, use the Remove-Job cmdlet.</span></span>

<span data-ttu-id="f0544-121">Från och med Windows PowerShell 3,0 stoppar **stopp-jobbet** även anpassade jobb typer, till exempel arbets flödes jobb och instanser av schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="f0544-121">Starting in Windows PowerShell 3.0, **Stop-Job** also stops custom job types, such as workflow jobs and instances of scheduled jobs.</span></span>
<span data-ttu-id="f0544-122">Om du vill aktivera **stoppa** jobb för att stoppa ett jobb med anpassad Jobbtyp importerar du modulen som stöder den anpassade jobb typen till sessionen innan du kör ett **Stop-jobb** -kommando, antingen genom att använda Import-Module cmdlet eller genom att använda eller hämta en cmdlet i modulen.</span><span class="sxs-lookup"><span data-stu-id="f0544-122">To enable **Stop-Job** to stop a job with custom job type, import the module that supports the custom job type into the session before you run a **Stop-Job** command, either by using the Import-Module cmdlet or by using or getting a cmdlet in the module.</span></span>
<span data-ttu-id="f0544-123">Information om en viss anpassad Jobbtyp finns i dokumentationen för den anpassade jobb typ funktionen.</span><span class="sxs-lookup"><span data-stu-id="f0544-123">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="f0544-124">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="f0544-124">EXAMPLES</span></span>

### <span data-ttu-id="f0544-125">Exempel 1: stoppa ett jobb på en fjärrdator med hjälp av Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="f0544-125">Example 1: Stop a job on a remote computer by using Invoke-Command</span></span>

```powershell
$s = New-PSSession -ComputerName Server01 -Credential Domain01\Admin02
$j = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {Get-EventLog System}}
Invoke-Command -Session $s -ScriptBlock { Stop-job -Job $Using:j }
```

<span data-ttu-id="f0544-126">Det här exemplet visar hur du använder cmdleten **stoppa-Job** för att stoppa ett jobb som körs på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="f0544-126">This example shows how to use the **Stop-Job** cmdlet to stop a job that is running on a remote computer.</span></span>

<span data-ttu-id="f0544-127">Eftersom jobbet startades med hjälp av Invoke-Command-cmdlet: en för att köra ett **Start jobb** via fjärr anslutning, lagras jobbobjektet på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="f0544-127">Because the job was started by using the Invoke-Command cmdlet to run a **Start-Job** command remotely, the job object is stored on the remote computer.</span></span>
<span data-ttu-id="f0544-128">Du måste använda ett annat **Invoke-kommando-** kommando för att köra ett **Stop-Job-** kommando via fjärr anslutning.</span><span class="sxs-lookup"><span data-stu-id="f0544-128">You must use another **Invoke-Command** command to run a **Stop-Job** command remotely.</span></span>
<span data-ttu-id="f0544-129">Mer information om fjärran sluten bakgrunds jobb finns about_Remote_Jobs.</span><span class="sxs-lookup"><span data-stu-id="f0544-129">For more information about remote background jobs, see about_Remote_Jobs.</span></span>

<span data-ttu-id="f0544-130">Det första kommandot skapar en PowerShell-session ( **PSSession** ) på Server01-datorn och lagrar sedan Session-objektet i variabeln $s.</span><span class="sxs-lookup"><span data-stu-id="f0544-130">The first command creates a PowerShell session ( **PSSession** ) on the Server01 computer, and then stores the session object in the $s variable.</span></span>
<span data-ttu-id="f0544-131">Kommandot använder autentiseringsuppgifterna för en domän administratör.</span><span class="sxs-lookup"><span data-stu-id="f0544-131">The command uses the credentials of a domain administrator.</span></span>

<span data-ttu-id="f0544-132">Det andra kommandot använder cmdleten **Invoke-Command** för att köra ett **Start jobb** kommando i sessionen.</span><span class="sxs-lookup"><span data-stu-id="f0544-132">The second command uses the **Invoke-Command** cmdlet to run a **Start-Job** command in the session.</span></span>
<span data-ttu-id="f0544-133">Kommandot i jobbet hämtar alla händelser i system händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="f0544-133">The command in the job gets all of the events in the System event log.</span></span>
<span data-ttu-id="f0544-134">Resulterande jobb objekt lagras i variabeln $j.</span><span class="sxs-lookup"><span data-stu-id="f0544-134">The resulting job object is stored in the $j variable.</span></span>

<span data-ttu-id="f0544-135">Det tredje kommandot stoppar jobbet.</span><span class="sxs-lookup"><span data-stu-id="f0544-135">The third command stops the job.</span></span>
<span data-ttu-id="f0544-136">Den använder cmdleten **Invoke-Command** för att köra ett **stopp-Job-** kommando i **PSSession** på Server01.</span><span class="sxs-lookup"><span data-stu-id="f0544-136">It uses the **Invoke-Command** cmdlet to run a **Stop-Job** command in the **PSSession** on Server01.</span></span>
<span data-ttu-id="f0544-137">Eftersom jobb objekt lagras i $j, vilket är en variabel på den lokala datorn, använder kommandot omfångs modifieraren using för att identifiera $j som en lokal variabel.</span><span class="sxs-lookup"><span data-stu-id="f0544-137">Because the job objects are stored in $j, which is a variable on the local computer, the command uses the Using scope modifier to identify $j as a local variable.</span></span>
<span data-ttu-id="f0544-138">Mer information om hur du använder omfångs modifieraren finns [about_Remote_Variables](about/about_Remote_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="f0544-138">For more information about the Using scope modifier, see [about_Remote_Variables](about/about_Remote_Variables.md).</span></span>

<span data-ttu-id="f0544-139">När kommandot har slutförts stoppas jobbet och **PSSession** i $s är tillgängligt för användning.</span><span class="sxs-lookup"><span data-stu-id="f0544-139">When the command finishes, the job is stopped and the **PSSession** in $s is available for use.</span></span>

### <span data-ttu-id="f0544-140">Exempel 2: stoppa ett bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="f0544-140">Example 2: Stop a background job</span></span>

```powershell
Stop-Job -Name "Job1"
```

<span data-ttu-id="f0544-141">Det här kommandot stoppar bakgrunds jobbet Job1.</span><span class="sxs-lookup"><span data-stu-id="f0544-141">This command stops the Job1 background job.</span></span>

### <span data-ttu-id="f0544-142">Exempel 3: stoppa flera bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="f0544-142">Example 3: Stop several background jobs</span></span>

```powershell
Stop-Job -Id 1, 3, 4
```

<span data-ttu-id="f0544-143">Det här kommandot stoppar tre jobb.</span><span class="sxs-lookup"><span data-stu-id="f0544-143">This command stops three jobs.</span></span>
<span data-ttu-id="f0544-144">Den identifierar dem med deras ID.</span><span class="sxs-lookup"><span data-stu-id="f0544-144">It identifies them by their IDs.</span></span>

### <span data-ttu-id="f0544-145">Exempel 4: stoppa alla bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="f0544-145">Example 4: Stop all background jobs</span></span>

```powershell
Get-Job | Stop-Job
```

<span data-ttu-id="f0544-146">Det här kommandot stoppar alla bakgrunds jobb i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="f0544-146">This command stops all of the background jobs in the current session.</span></span>

### <span data-ttu-id="f0544-147">Exempel 5: stoppa alla blockerade bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="f0544-147">Example 5: Stop all blocked background jobs</span></span>

```powershell
Stop-Job -State Blocked
```

<span data-ttu-id="f0544-148">Det här kommandot stoppar alla jobb som blockeras.</span><span class="sxs-lookup"><span data-stu-id="f0544-148">This command stops all the jobs that are blocked.</span></span>

### <span data-ttu-id="f0544-149">Exempel 6: stoppa ett jobb med hjälp av ett instans-ID</span><span class="sxs-lookup"><span data-stu-id="f0544-149">Example 6: Stop a job by using an instance ID</span></span>

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

<span data-ttu-id="f0544-150">Kommandona visar hur du stoppar ett jobb baserat på dess instans-ID.</span><span class="sxs-lookup"><span data-stu-id="f0544-150">These commands show how to stop a job based on its instance ID.</span></span>

<span data-ttu-id="f0544-151">Det första kommandot använder cmdleten Get-Job för att hämta jobben i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="f0544-151">The first command uses the Get-Job cmdlet to get the jobs in the current session.</span></span>
<span data-ttu-id="f0544-152">Kommandot använder en pipeline-operator (|) för att skicka jobben till ett Format-Table-kommando, som visar en tabell med de angivna egenskaperna för varje jobb.</span><span class="sxs-lookup"><span data-stu-id="f0544-152">The command uses a pipeline operator (|) to send the jobs to a Format-Table command, which displays a table of the specified properties of each job.</span></span>
<span data-ttu-id="f0544-153">Tabellen innehåller instans-ID för varje jobb.</span><span class="sxs-lookup"><span data-stu-id="f0544-153">The table includes the Instance ID of each job.</span></span>
<span data-ttu-id="f0544-154">Den använder en beräknad egenskap för att visa jobb status.</span><span class="sxs-lookup"><span data-stu-id="f0544-154">It uses a calculated property to display the job state.</span></span>

<span data-ttu-id="f0544-155">Det andra kommandot använder ett **stopp-jobb** -kommando som har *InstanceID* -parametern för att stoppa ett valt jobb.</span><span class="sxs-lookup"><span data-stu-id="f0544-155">The second command uses a **Stop-Job** command that has the *InstanceID* parameter to stop a selected job.</span></span>

### <span data-ttu-id="f0544-156">Exempel 7: stoppa ett jobb på en fjärrdator</span><span class="sxs-lookup"><span data-stu-id="f0544-156">Example 7: Stop a job on a remote computer</span></span>

```powershell
$j = Invoke-Command -ComputerName Server01 -ScriptBlock {Get-EventLog System} -AsJob
$j | Stop-Job -PassThru
```

```Output
Id    Name    State      HasMoreData     Location         Command
--    ----    ----       -----------     --------         -------
5     Job5    Stopped    True            user01-tablet    get-eventlog system
```

<span data-ttu-id="f0544-157">Det här exemplet visar hur du använder cmdleten **stoppa-Job** för att stoppa ett jobb som körs på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="f0544-157">This example shows how to use the **Stop-Job** cmdlet to stop a job that is running on a remote computer.</span></span>

<span data-ttu-id="f0544-158">Eftersom jobbet startades med hjälp av parametern *AsJob* i cmdleten **Invoke-Command** finns jobbobjektet på den lokala datorn, även om jobbet körs på fjärrdatorn.</span><span class="sxs-lookup"><span data-stu-id="f0544-158">Because the job was started by using the *AsJob* parameter of the **Invoke-Command** cmdlet, the job object is located on the local computer, even though the job runs on the remote computer.</span></span>
<span data-ttu-id="f0544-159">Därför kan du använda ett lokalt **stopp-jobb-** kommando för att stoppa jobbet.</span><span class="sxs-lookup"><span data-stu-id="f0544-159">Therefore, you can use a local **Stop-Job** command to stop the job.</span></span>

<span data-ttu-id="f0544-160">Det första kommandot använder cmdleten **Invoke-Command** för att starta ett bakgrunds jobb på den Server01 datorn.</span><span class="sxs-lookup"><span data-stu-id="f0544-160">The first command uses the **Invoke-Command** cmdlet to start a background job on the Server01 computer.</span></span>
<span data-ttu-id="f0544-161">Kommandot använder parametern *AsJob* för att köra fjärrkommandot som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="f0544-161">The command uses the *AsJob* parameter to run the remote command as a background job.</span></span>

<span data-ttu-id="f0544-162">Det här kommandot returnerar ett jobb objekt, vilket är samma jobb objekt som cmdleten **Start-Job** returnerar.</span><span class="sxs-lookup"><span data-stu-id="f0544-162">This command returns a job object, which is the same job object that the **Start-Job** cmdlet returns.</span></span>
<span data-ttu-id="f0544-163">Kommandot sparar jobbobjektet i variabeln $j.</span><span class="sxs-lookup"><span data-stu-id="f0544-163">The command saves the job object in the $j variable.</span></span>

<span data-ttu-id="f0544-164">Det andra kommandot använder en pipeline-operator för att skicka jobbet i $j-variabeln till stopp-Job.</span><span class="sxs-lookup"><span data-stu-id="f0544-164">The second command uses a pipeline operator to send the job in the $j variable to Stop-Job.</span></span>
<span data-ttu-id="f0544-165">Kommandot använder parametern *Passthru* för att dirigera **stopp-jobb** för att returnera ett jobb objekt.</span><span class="sxs-lookup"><span data-stu-id="f0544-165">The command uses the *PassThru* parameter to direct **Stop-Job** to return a job object.</span></span>
<span data-ttu-id="f0544-166">Jobb objekts visningen bekräftar att jobbets tillstånd har stoppats.</span><span class="sxs-lookup"><span data-stu-id="f0544-166">The job object display confirms that the state of the job is Stopped.</span></span>

<span data-ttu-id="f0544-167">Mer information om fjärran sluten bakgrunds jobb finns about_Remote_Jobs.</span><span class="sxs-lookup"><span data-stu-id="f0544-167">For more information about remote background jobs, see about_Remote_Jobs.</span></span>

## <span data-ttu-id="f0544-168">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="f0544-168">PARAMETERS</span></span>

### <span data-ttu-id="f0544-169">-Filter</span><span class="sxs-lookup"><span data-stu-id="f0544-169">-Filter</span></span>

<span data-ttu-id="f0544-170">Anger en hash-tabell med villkor.</span><span class="sxs-lookup"><span data-stu-id="f0544-170">Specifies a hash table of conditions.</span></span>
<span data-ttu-id="f0544-171">Denna cmdlet stoppar jobb som uppfyller alla villkor.</span><span class="sxs-lookup"><span data-stu-id="f0544-171">This cmdlet stops jobs that satisfy all of the conditions.</span></span>
<span data-ttu-id="f0544-172">Ange en hash-tabell där nycklarna är jobb egenskaper och värdena är jobb egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="f0544-172">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="f0544-173">Den här parametern fungerar bara på anpassade jobb typer, till exempel arbets flödes jobb och schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="f0544-173">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span>
<span data-ttu-id="f0544-174">Den fungerar inte på vanliga bakgrunds jobb, till exempel de som skapats med hjälp av cmdleten **Start-Job** .</span><span class="sxs-lookup"><span data-stu-id="f0544-174">It does not work on standard background jobs, such as those created by using the **Start-Job** cmdlet.</span></span>
<span data-ttu-id="f0544-175">Information om stöd för den här parametern finns i hjälp avsnittet för jobb typen.</span><span class="sxs-lookup"><span data-stu-id="f0544-175">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="f0544-176">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="f0544-176">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="f0544-177">-ID</span><span class="sxs-lookup"><span data-stu-id="f0544-177">-Id</span></span>

<span data-ttu-id="f0544-178">Anger ID: n för jobb som denna cmdlet stoppar.</span><span class="sxs-lookup"><span data-stu-id="f0544-178">Specifies the IDs of jobs that this cmdlet stops.</span></span>
<span data-ttu-id="f0544-179">Standardvärdet är alla jobb i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="f0544-179">The default is all jobs in the current session.</span></span>

<span data-ttu-id="f0544-180">ID är ett heltal som unikt identifierar jobbet i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="f0544-180">The ID is an integer that uniquely identifies the job in the current session.</span></span>
<span data-ttu-id="f0544-181">Det är enklare att komma ihåg och skriva än instans-ID, men det är endast unikt i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="f0544-181">It is easier to remember and type than the instance ID, but it is unique only in the current session.</span></span>
<span data-ttu-id="f0544-182">Du kan ange ett eller flera ID: n, avgränsade med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="f0544-182">You can type one or more IDs, separated by commas.</span></span>
<span data-ttu-id="f0544-183">Om du vill hitta ID: t för ett jobb skriver du `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="f0544-183">To find the ID of a job, type `Get-Job`.</span></span>

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

### <span data-ttu-id="f0544-184">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="f0544-184">-InstanceId</span></span>

<span data-ttu-id="f0544-185">Anger instans-ID: n för jobb som denna cmdlet stoppar.</span><span class="sxs-lookup"><span data-stu-id="f0544-185">Specifies the instance IDs of jobs that this cmdlet stops.</span></span>
<span data-ttu-id="f0544-186">Standardvärdet är alla jobb.</span><span class="sxs-lookup"><span data-stu-id="f0544-186">The default is all jobs.</span></span>

<span data-ttu-id="f0544-187">Ett instans-ID är ett GUID som unikt identifierar jobbet på datorn.</span><span class="sxs-lookup"><span data-stu-id="f0544-187">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span>
<span data-ttu-id="f0544-188">Använd Get-Job för att hitta instans-ID för ett jobb.</span><span class="sxs-lookup"><span data-stu-id="f0544-188">To find the instance ID of a job, use Get-Job.</span></span>

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

### <span data-ttu-id="f0544-189">– Jobb</span><span class="sxs-lookup"><span data-stu-id="f0544-189">-Job</span></span>

<span data-ttu-id="f0544-190">Anger de jobb som denna cmdlet stoppar.</span><span class="sxs-lookup"><span data-stu-id="f0544-190">Specifies the jobs that this cmdlet stops.</span></span>
<span data-ttu-id="f0544-191">Ange en variabel som innehåller jobben eller ett kommando som hämtar jobben.</span><span class="sxs-lookup"><span data-stu-id="f0544-191">Enter a variable that contains the jobs or a command that gets the jobs.</span></span>
<span data-ttu-id="f0544-192">Du kan också använda en pipeline-operatör för att skicka jobb till cmdleten **stoppa-Job** .</span><span class="sxs-lookup"><span data-stu-id="f0544-192">You can also use a pipeline operator to submit jobs to the **Stop-Job** cmdlet.</span></span>
<span data-ttu-id="f0544-193">Som standard tar **stopp-jobbet** bort alla jobb som startades i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="f0544-193">By default, **Stop-Job** deletes all jobs that were started in the current session.</span></span>

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

### <span data-ttu-id="f0544-194">-Name</span><span class="sxs-lookup"><span data-stu-id="f0544-194">-Name</span></span>

<span data-ttu-id="f0544-195">Anger egna namn på jobb som denna cmdlet stoppar.</span><span class="sxs-lookup"><span data-stu-id="f0544-195">Specifies friendly names of jobs that this cmdlet stops.</span></span>
<span data-ttu-id="f0544-196">Ange jobb namnen i en kommaavgränsad lista eller Använd jokertecken (\*) för att ange ett jobb namns mönster.</span><span class="sxs-lookup"><span data-stu-id="f0544-196">Enter the job names in a comma-separated list or use wildcard characters (\*) to enter a job name pattern.</span></span>
<span data-ttu-id="f0544-197">Som standard stoppar **stopp-jobbet** alla jobb som skapats i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="f0544-197">By default, **Stop-Job** stops all jobs created in the current session.</span></span>

<span data-ttu-id="f0544-198">Eftersom det egna namnet inte garanterat är unikt använder du parametrarna *whatIf* och *Confirm* när du stoppar jobb efter namn.</span><span class="sxs-lookup"><span data-stu-id="f0544-198">Because the friendly name is not guaranteed to be unique, use the *WhatIf* and *Confirm* parameters when stopping jobs by name.</span></span>

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

### <span data-ttu-id="f0544-199">– PassThru</span><span class="sxs-lookup"><span data-stu-id="f0544-199">-PassThru</span></span>

<span data-ttu-id="f0544-200">Returnerar ett objekt som representerar det objekt som du arbetar med.</span><span class="sxs-lookup"><span data-stu-id="f0544-200">Returns an object representing the item with which you are working.</span></span>
<span data-ttu-id="f0544-201">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="f0544-201">By default, this cmdlet does not generate any output.</span></span>

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

### <span data-ttu-id="f0544-202">– Tillstånd</span><span class="sxs-lookup"><span data-stu-id="f0544-202">-State</span></span>

<span data-ttu-id="f0544-203">Anger ett jobb tillstånd.</span><span class="sxs-lookup"><span data-stu-id="f0544-203">Specifies a job state.</span></span>
<span data-ttu-id="f0544-204">Denna cmdlet stoppar endast jobb i det angivna läget.</span><span class="sxs-lookup"><span data-stu-id="f0544-204">This cmdlet stops only jobs in the specified state.</span></span>
<span data-ttu-id="f0544-205">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="f0544-205">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="f0544-206">NotStarted</span><span class="sxs-lookup"><span data-stu-id="f0544-206">NotStarted</span></span>
- <span data-ttu-id="f0544-207">Körs</span><span class="sxs-lookup"><span data-stu-id="f0544-207">Running</span></span>
- <span data-ttu-id="f0544-208">Slutförd</span><span class="sxs-lookup"><span data-stu-id="f0544-208">Completed</span></span>
- <span data-ttu-id="f0544-209">Misslyckad</span><span class="sxs-lookup"><span data-stu-id="f0544-209">Failed</span></span>
- <span data-ttu-id="f0544-210">Stoppad</span><span class="sxs-lookup"><span data-stu-id="f0544-210">Stopped</span></span>
- <span data-ttu-id="f0544-211">Blockerad</span><span class="sxs-lookup"><span data-stu-id="f0544-211">Blocked</span></span>
- <span data-ttu-id="f0544-212">Inaktiverad</span><span class="sxs-lookup"><span data-stu-id="f0544-212">Suspended</span></span>
- <span data-ttu-id="f0544-213">Frånkopplad</span><span class="sxs-lookup"><span data-stu-id="f0544-213">Disconnected</span></span>
- <span data-ttu-id="f0544-214">Pausar</span><span class="sxs-lookup"><span data-stu-id="f0544-214">Suspending</span></span>
- <span data-ttu-id="f0544-215">Stoppas</span><span class="sxs-lookup"><span data-stu-id="f0544-215">Stopping</span></span>

<span data-ttu-id="f0544-216">Mer information om jobb tillstånd finns i [JobState-uppräkning](https://msdn.microsoft.com/library/system.management.automation.jobstate) i MSDN-biblioteket.</span><span class="sxs-lookup"><span data-stu-id="f0544-216">For more information about job states, see [JobState Enumeration](https://msdn.microsoft.com/library/system.management.automation.jobstate) in the MSDN library.</span></span>

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

### <span data-ttu-id="f0544-217">-Confirm</span><span class="sxs-lookup"><span data-stu-id="f0544-217">-Confirm</span></span>

<span data-ttu-id="f0544-218">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="f0544-218">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="f0544-219">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="f0544-219">-WhatIf</span></span>

<span data-ttu-id="f0544-220">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="f0544-220">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="f0544-221">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="f0544-221">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="f0544-222">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="f0544-222">CommonParameters</span></span>

<span data-ttu-id="f0544-223">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="f0544-223">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="f0544-224">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="f0544-224">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="f0544-225">INDATA</span><span class="sxs-lookup"><span data-stu-id="f0544-225">INPUTS</span></span>

### <span data-ttu-id="f0544-226">System. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="f0544-226">System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="f0544-227">Du kan skicka vidare ett jobb objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f0544-227">You can pipe a job object to this cmdlet.</span></span>

## <span data-ttu-id="f0544-228">UTDATA</span><span class="sxs-lookup"><span data-stu-id="f0544-228">OUTPUTS</span></span>

### <span data-ttu-id="f0544-229">Ingen, system. Management. Automation. PSRemotingJob</span><span class="sxs-lookup"><span data-stu-id="f0544-229">None, System.Management.Automation.PSRemotingJob</span></span>

<span data-ttu-id="f0544-230">Den här cmdleten returnerar ett jobb objekt, om du anger parametern *Passthru* .</span><span class="sxs-lookup"><span data-stu-id="f0544-230">This cmdlet returns a job object, if you specify the *PassThru* parameter.</span></span>
<span data-ttu-id="f0544-231">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="f0544-231">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="f0544-232">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="f0544-232">NOTES</span></span>

## <span data-ttu-id="f0544-233">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="f0544-233">RELATED LINKS</span></span>

[<span data-ttu-id="f0544-234">Hämta jobb</span><span class="sxs-lookup"><span data-stu-id="f0544-234">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="f0544-235">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="f0544-235">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="f0544-236">Mottagning – jobb</span><span class="sxs-lookup"><span data-stu-id="f0544-236">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="f0544-237">Ta bort – jobb</span><span class="sxs-lookup"><span data-stu-id="f0544-237">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="f0544-238">Start – jobb</span><span class="sxs-lookup"><span data-stu-id="f0544-238">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="f0544-239">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="f0544-239">Wait-Job</span></span>](Wait-Job.md)

[<span data-ttu-id="f0544-240">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="f0544-240">about_Job_Details</span></span>](About/about_Job_Details.md)

[<span data-ttu-id="f0544-241">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="f0544-241">about_Remote_Jobs</span></span>](About/about_Remote_Jobs.md)

[<span data-ttu-id="f0544-242">about_Remote_Variables</span><span class="sxs-lookup"><span data-stu-id="f0544-242">about_Remote_Variables</span></span>](About/about_Remote_Variables.md)

[<span data-ttu-id="f0544-243">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="f0544-243">about_Jobs</span></span>](About/about_Jobs.md)

[<span data-ttu-id="f0544-244">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="f0544-244">about_Scopes</span></span>](About/about_scopes.md)

