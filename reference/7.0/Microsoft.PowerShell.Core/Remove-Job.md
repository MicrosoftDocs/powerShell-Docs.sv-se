---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 07/26/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/remove-job?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-Job
ms.openlocfilehash: 52db5da9057023ce9a687e1d11b0534afaabdad9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93263942"
---
# <span data-ttu-id="05fbe-103">Remove-Job</span><span class="sxs-lookup"><span data-stu-id="05fbe-103">Remove-Job</span></span>

## <span data-ttu-id="05fbe-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="05fbe-104">SYNOPSIS</span></span>
<span data-ttu-id="05fbe-105">Tar bort ett PowerShell-bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="05fbe-105">Deletes a PowerShell background job.</span></span>

## <span data-ttu-id="05fbe-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="05fbe-106">SYNTAX</span></span>

### <span data-ttu-id="05fbe-107">SessionIdParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="05fbe-107">SessionIdParameterSet (Default)</span></span>

```
Remove-Job [-Force] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="05fbe-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="05fbe-108">JobParameterSet</span></span>

```
Remove-Job [-Job] <Job[]> [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="05fbe-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="05fbe-109">NameParameterSet</span></span>

```
Remove-Job [-Force] [-Name] <String[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="05fbe-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="05fbe-110">InstanceIdParameterSet</span></span>

```
Remove-Job [-Force] [-InstanceId] <Guid[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="05fbe-111">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="05fbe-111">FilterParameterSet</span></span>

```
Remove-Job [-Force] [-Filter] <Hashtable> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="05fbe-112">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="05fbe-112">StateParameterSet</span></span>

```
Remove-Job [-State] <JobState> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### <span data-ttu-id="05fbe-113">CommandParameterSet</span><span class="sxs-lookup"><span data-stu-id="05fbe-113">CommandParameterSet</span></span>

```
Remove-Job [-Command <String[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="05fbe-114">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="05fbe-114">DESCRIPTION</span></span>

<span data-ttu-id="05fbe-115">`Remove-Job`Cmdlet: en tar bort PowerShell-bakgrunds jobb som startades av `Start-Job` cmdleten eller av cmdlets som `Invoke-Command` stöder parametern **AsJob** .</span><span class="sxs-lookup"><span data-stu-id="05fbe-115">The `Remove-Job` cmdlet deletes PowerShell background jobs that were started by the `Start-Job` cmdlet or by cmdlets such as `Invoke-Command` that support the **AsJob** parameter.</span></span>

<span data-ttu-id="05fbe-116">Du kan använda `Remove-Job` för att ta bort alla jobb eller ta bort valda jobb.</span><span class="sxs-lookup"><span data-stu-id="05fbe-116">You can use `Remove-Job` to delete all jobs or delete selected jobs.</span></span> <span data-ttu-id="05fbe-117">Jobben identifieras med **namn** , **ID** , **instans-ID** , **kommando** eller **tillstånd**.</span><span class="sxs-lookup"><span data-stu-id="05fbe-117">The jobs are identified by their **Name** , **ID** , **Instance ID** , **Command** , or **State**.</span></span> <span data-ttu-id="05fbe-118">Eller så kan ett jobb objekt skickas nedåt i pipeline till `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="05fbe-118">Or, a job object can be sent down the pipeline to `Remove-Job`.</span></span> <span data-ttu-id="05fbe-119">Utan parametrar eller parameter värden `Remove-Job` har ingen påverkan.</span><span class="sxs-lookup"><span data-stu-id="05fbe-119">Without parameters or parameter values, `Remove-Job` has no effect.</span></span>

<span data-ttu-id="05fbe-120">Eftersom PowerShell 3,0 `Remove-Job` kan ta bort anpassade jobb typer, till exempel schemalagda jobb och arbets flödes jobb.</span><span class="sxs-lookup"><span data-stu-id="05fbe-120">Since PowerShell 3.0, `Remove-Job` can delete custom job types, such as scheduled jobs and workflow jobs.</span></span> <span data-ttu-id="05fbe-121">Till exempel `Remove-Job` tar bort det schemalagda jobbet, alla instanser av det schemalagda jobbet på disken och resultatet av alla Utlös ande jobb instanser.</span><span class="sxs-lookup"><span data-stu-id="05fbe-121">For example, `Remove-Job` deletes the scheduled job, all instances of the scheduled job on disk, and the results of all triggered job instances.</span></span>

<span data-ttu-id="05fbe-122">Om du försöker ta bort ett jobb som körs `Remove-Job` Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="05fbe-122">If you try to delete a running job, `Remove-Job` fails.</span></span> <span data-ttu-id="05fbe-123">Använd `Stop-Job` cmdleten för att stoppa ett pågående jobb.</span><span class="sxs-lookup"><span data-stu-id="05fbe-123">Use the `Stop-Job` cmdlet to stop a running job.</span></span> <span data-ttu-id="05fbe-124">Eller Använd `Remove-Job` med parametern **Force** för att ta bort ett jobb som körs.</span><span class="sxs-lookup"><span data-stu-id="05fbe-124">Or, use `Remove-Job` with the **Force** parameter to delete a running job.</span></span>

<span data-ttu-id="05fbe-125">Jobb finns kvar i den globala jobb-cachen tills du tar bort bakgrunds jobbet eller stänger PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="05fbe-125">Jobs remain in the global job cache until you delete the background job or close the PowerShell session.</span></span>

## <span data-ttu-id="05fbe-126">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="05fbe-126">EXAMPLES</span></span>

### <span data-ttu-id="05fbe-127">Exempel 1: ta bort ett jobb med hjälp av dess namn</span><span class="sxs-lookup"><span data-stu-id="05fbe-127">Example 1: Delete a job by using its name</span></span>

<span data-ttu-id="05fbe-128">I det här exemplet används en variabel och pipelinen för att ta bort ett jobb efter namn.</span><span class="sxs-lookup"><span data-stu-id="05fbe-128">This example uses a variable and the pipeline to delete a job by name.</span></span>

```powershell
$batch = Get-Job -Name BatchJob
$batch | Remove-Job
```

<span data-ttu-id="05fbe-129">`Get-Job` använder parametern **Name** för att ange jobbet **BatchJob**.</span><span class="sxs-lookup"><span data-stu-id="05fbe-129">`Get-Job` uses the **Name** parameter to specify the job, **BatchJob**.</span></span> <span data-ttu-id="05fbe-130">Jobbobjektet lagras i `$batch` variabeln.</span><span class="sxs-lookup"><span data-stu-id="05fbe-130">The job object is stored in the `$batch` variable.</span></span> <span data-ttu-id="05fbe-131">Objektet i `$batch` skickas pipelinen till `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="05fbe-131">The object in `$batch` is sent down the pipeline to `Remove-Job`.</span></span>

<span data-ttu-id="05fbe-132">Ett alternativ är att använda **jobb** parametern, till exempel `Remove-Job -Job $batch` .</span><span class="sxs-lookup"><span data-stu-id="05fbe-132">An alternative is to use the **Job** parameter, such as `Remove-Job -Job $batch`.</span></span>

### <span data-ttu-id="05fbe-133">Exempel 2: ta bort alla jobb i en session</span><span class="sxs-lookup"><span data-stu-id="05fbe-133">Example 2: Delete all jobs in a session</span></span>

<span data-ttu-id="05fbe-134">I det här exemplet tas alla jobb i den aktuella PowerShell-sessionen bort.</span><span class="sxs-lookup"><span data-stu-id="05fbe-134">In this example, all the jobs in the current PowerShell session are deleted.</span></span>

```powershell
Get-job | Remove-Job
```

<span data-ttu-id="05fbe-135">`Get-Job` hämtar alla jobb i den aktuella PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="05fbe-135">`Get-Job` gets all the jobs in the current PowerShell session.</span></span> <span data-ttu-id="05fbe-136">Jobb objekten skickas ned pipelinen till `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="05fbe-136">The job objects are sent down the pipeline to `Remove-Job`.</span></span>

### <span data-ttu-id="05fbe-137">Exempel 3: ta bort NotStarted-jobb</span><span class="sxs-lookup"><span data-stu-id="05fbe-137">Example 3: Delete NotStarted jobs</span></span>

<span data-ttu-id="05fbe-138">Det här exemplet tar bort alla jobb från den aktuella PowerShell-sessionen som inte har startats.</span><span class="sxs-lookup"><span data-stu-id="05fbe-138">This example deletes all jobs from the current PowerShell session that haven't started.</span></span>

```powershell
Remove-Job -State NotStarted
```

<span data-ttu-id="05fbe-139">`Remove-Job` använder parametern **State** för att ange jobbets status.</span><span class="sxs-lookup"><span data-stu-id="05fbe-139">`Remove-Job` uses the **State** parameter to specify the job status.</span></span>

### <span data-ttu-id="05fbe-140">Exempel 4: ta bort jobb med ett eget namn</span><span class="sxs-lookup"><span data-stu-id="05fbe-140">Example 4: Delete jobs by using a friendly name</span></span>

<span data-ttu-id="05fbe-141">Det här exemplet tar bort alla jobb från den aktuella sessionen med egna namn som slutar med \* batch \* \*, inklusive jobb som kör.</span><span class="sxs-lookup"><span data-stu-id="05fbe-141">This example deletes all jobs from the current session with friendly names that end with \*batch\*\*, including jobs that are running.</span></span>

```powershell
Remove-Job -Name *batch -Force
```

<span data-ttu-id="05fbe-142">`Remove-Job` använder parametern **Name** för att ange ett jobb namns mönster.</span><span class="sxs-lookup"><span data-stu-id="05fbe-142">`Remove-Job` uses the **Name** parameter to specify a job name pattern.</span></span> <span data-ttu-id="05fbe-143">Mönstret innehåller jokertecknet asterisk ( `*` ) för att hitta alla jobb namn som slutar med **batch**.</span><span class="sxs-lookup"><span data-stu-id="05fbe-143">The pattern includes the asterisk (`*`) wildcard to find all job names that end with **batch**.</span></span> <span data-ttu-id="05fbe-144">Parametern **Force** tar bort jobb som kör.</span><span class="sxs-lookup"><span data-stu-id="05fbe-144">The **Force** parameter deletes jobs that running.</span></span>

### <span data-ttu-id="05fbe-145">Exempel 5: ta bort ett jobb som har skapats av Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="05fbe-145">Example 5: Delete a job that was created by Invoke-Command</span></span>

<span data-ttu-id="05fbe-146">Det här exemplet tar bort ett jobb som startades på en fjärrdator med hjälp `Invoke-Command` av parametern **AsJob** .</span><span class="sxs-lookup"><span data-stu-id="05fbe-146">This example removes a job that was started on a remote computer using `Invoke-Command` with the **AsJob** parameter.</span></span>

<span data-ttu-id="05fbe-147">Eftersom exemplet använder parametern **AsJob** skapas jobbobjektet på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="05fbe-147">Because the example uses the **AsJob** parameter, the job object is created on the local computer.</span></span>
<span data-ttu-id="05fbe-148">Men jobbet körs på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="05fbe-148">But, the job runs on a remote computer.</span></span> <span data-ttu-id="05fbe-149">Därför använder du lokala kommandon för att hantera jobbet.</span><span class="sxs-lookup"><span data-stu-id="05fbe-149">As a result, you use local commands to manage the job.</span></span>

```powershell
$job = Invoke-Command -ComputerName Server01 -ScriptBlock {Get-Process} -AsJob
$job | Remove-Job
```

<span data-ttu-id="05fbe-150">`Invoke-Command` kör ett jobb på den **Server01** datorn.</span><span class="sxs-lookup"><span data-stu-id="05fbe-150">`Invoke-Command` runs a job on the **Server01** computer.</span></span> <span data-ttu-id="05fbe-151">Parametern **AsJob** kör **script block** som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="05fbe-151">The **AsJob** parameter runs the **ScriptBlock** as a background job.</span></span> <span data-ttu-id="05fbe-152">Jobbobjektet lagras i `$job` variabeln.</span><span class="sxs-lookup"><span data-stu-id="05fbe-152">The job object is stored in the `$job` variable.</span></span> <span data-ttu-id="05fbe-153">Det `$job` variabla objektet skickas nedåt i pipeline till `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="05fbe-153">The `$job` variable object is sent down the pipeline to `Remove-Job`.</span></span>

### <span data-ttu-id="05fbe-154">Exempel 6: ta bort ett jobb som har skapats av Invoke-Command och Start-Job</span><span class="sxs-lookup"><span data-stu-id="05fbe-154">Example 6: Delete a job that was created by Invoke-Command and Start-Job</span></span>

<span data-ttu-id="05fbe-155">Det här exemplet visar hur du tar bort ett jobb på en fjärrdator som startades med hjälp av `Invoke-Command` att köra `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="05fbe-155">This example shows how to remove a job on a remote computer that was started by using `Invoke-Command` to run `Start-Job`.</span></span> <span data-ttu-id="05fbe-156">Jobbobjektet skapas på fjärrdatorn och fjärrkommandona används för att hantera jobbet.</span><span class="sxs-lookup"><span data-stu-id="05fbe-156">The job object is created on the remote computer and remote commands are used to manage the job.</span></span> <span data-ttu-id="05fbe-157">En permanent anslutning krävs när du kör ett `Start-Job` fjärrkommando.</span><span class="sxs-lookup"><span data-stu-id="05fbe-157">A persistent connection is required when running a remote `Start-Job` command.</span></span>

```powershell
$S = New-PSSession -ComputerName Server01
Invoke-Command -Session $S -ScriptBlock {Start-Job -ScriptBlock {Get-Process} -Name MyJob}
Invoke-Command -Session $S -ScriptBlock {Remove-Job -Name MyJob}
```

<span data-ttu-id="05fbe-158">`New-PSSession` skapar en **PSSession** , en permanent anslutning, till **Server01** -datorn.</span><span class="sxs-lookup"><span data-stu-id="05fbe-158">`New-PSSession` creates a **PSSession** , a persistent connection, to the **Server01** computer.</span></span> <span data-ttu-id="05fbe-159">Anslutningen sparas i `$S` variabeln.</span><span class="sxs-lookup"><span data-stu-id="05fbe-159">The connection is saved in the `$S` variable.</span></span>

<span data-ttu-id="05fbe-160">`Invoke-Command` ansluter till sessionen som sparats i `$S` .</span><span class="sxs-lookup"><span data-stu-id="05fbe-160">`Invoke-Command` connects to the session saved in `$S`.</span></span> <span data-ttu-id="05fbe-161">**Script block** använder `Start-Job` för att starta ett Fjärrjobb.</span><span class="sxs-lookup"><span data-stu-id="05fbe-161">The **ScriptBlock** uses `Start-Job` to start a remote job.</span></span> <span data-ttu-id="05fbe-162">Jobbet kör ett `Get-Process` kommando och använder parametern **Name** för att ange ett eget jobbnamn, **MyJob**.</span><span class="sxs-lookup"><span data-stu-id="05fbe-162">The job runs a `Get-Process` command and uses the **Name** parameter to specify a friendly job name, **MyJob**.</span></span>

<span data-ttu-id="05fbe-163">`Invoke-Command` använder `$S` sessionen och körs `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="05fbe-163">`Invoke-Command` uses the `$S` session and runs `Remove-Job`.</span></span> <span data-ttu-id="05fbe-164">Parametern **Name** anger att jobbet med namnet **MyJob** har tagits bort.</span><span class="sxs-lookup"><span data-stu-id="05fbe-164">The **Name** parameter specifies that the job named **MyJob** is deleted.</span></span>

### <span data-ttu-id="05fbe-165">Exempel 7: ta bort ett jobb med hjälp av dess InstanceId</span><span class="sxs-lookup"><span data-stu-id="05fbe-165">Example 7: Delete a job by using its InstanceId</span></span>

<span data-ttu-id="05fbe-166">Det här exemplet tar bort ett jobb baserat på dess **InstanceID**.</span><span class="sxs-lookup"><span data-stu-id="05fbe-166">This example removes a job based on its **InstanceId**.</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Process PowerShell}
$job | Format-List -Property *
Remove-Job -InstanceId ad02b942-8007-4407-87f3-d23e71955872
```

```Output
State         : Completed
HasMoreData   : True
StatusMessage :
Location      : localhost
Command       : Get-Process PowerShell
JobStateInfo  : Completed
Finished      : System.Threading.ManualResetEvent
InstanceId    : ad02b942-8007-4407-87f3-d23e71955872
Id            : 3
Name          : Job3
ChildJobs     : {Job4}
PSBeginTime   : 7/26/2019 11:36:56
PSEndTime     : 7/26/2019 11:36:57
PSJobTypeName : BackgroundJob
Output        : {}
Error         : {}
Progress      : {}
Verbose       : {}
Debug         : {}
Warning       : {}
Information   : {}
```

<span data-ttu-id="05fbe-167">`Start-Job` startar ett bakgrunds jobb och jobbobjektet sparas i `$job` variabeln.</span><span class="sxs-lookup"><span data-stu-id="05fbe-167">`Start-Job` starts a background job and the job object is saved in the `$job` variable.</span></span>

<span data-ttu-id="05fbe-168">Objektet i `$job` skickas pipelinen till `Format-List` .</span><span class="sxs-lookup"><span data-stu-id="05fbe-168">The object in `$job` is sent down the pipeline to `Format-List`.</span></span> <span data-ttu-id="05fbe-169">**Egenskaps** parametern använder en asterisk ( `*` ) för att ange att alla objekt egenskaper ska visas i en lista.</span><span class="sxs-lookup"><span data-stu-id="05fbe-169">The **Property** parameter uses an asterisk (`*`) to specify that all the object's properties are displayed in a list.</span></span>

<span data-ttu-id="05fbe-170">`Remove-Job` använder parametern **InstanceID** för att ange det jobb som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="05fbe-170">`Remove-Job` uses the **InstanceId** parameter to specify the job to delete.</span></span>

## <span data-ttu-id="05fbe-171">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="05fbe-171">PARAMETERS</span></span>

### <span data-ttu-id="05fbe-172">-Kommando</span><span class="sxs-lookup"><span data-stu-id="05fbe-172">-Command</span></span>

<span data-ttu-id="05fbe-173">Tar bort jobb som innehåller de angivna orden i kommandot.</span><span class="sxs-lookup"><span data-stu-id="05fbe-173">Deletes jobs that include the specified words in the command.</span></span> <span data-ttu-id="05fbe-174">Du kan ange en kommaavgränsad matris.</span><span class="sxs-lookup"><span data-stu-id="05fbe-174">You can enter a comma-separated array.</span></span>

```yaml
Type: System.String[]
Parameter Sets: CommandParameterSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="05fbe-175">-Confirm</span><span class="sxs-lookup"><span data-stu-id="05fbe-175">-Confirm</span></span>

<span data-ttu-id="05fbe-176">Du uppmanas att bekräfta innan körs `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="05fbe-176">Prompts you for confirmation before `Remove-Job` is run.</span></span>

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

### <span data-ttu-id="05fbe-177">-Filter</span><span class="sxs-lookup"><span data-stu-id="05fbe-177">-Filter</span></span>

<span data-ttu-id="05fbe-178">Tar bort jobb som uppfyller alla villkor som fastställs i den tillhör ande hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="05fbe-178">Deletes jobs that satisfy all the conditions established in the associated hash table.</span></span> <span data-ttu-id="05fbe-179">Ange en hash-tabell där nycklarna är jobb egenskaper och värdena är jobb egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="05fbe-179">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="05fbe-180">Den här parametern fungerar bara på anpassade jobb typer, till exempel arbets flödes jobb och schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="05fbe-180">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span> <span data-ttu-id="05fbe-181">Det fungerar inte på vanliga bakgrunds jobb, till exempel de som skapats med hjälp av `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="05fbe-181">It doesn't work on standard background jobs, such as those created by using the `Start-Job`.</span></span>

<span data-ttu-id="05fbe-182">Den här parametern introduceras i PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="05fbe-182">This parameter is introduced in PowerShell 3.0.</span></span>

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

### <span data-ttu-id="05fbe-183">-Force</span><span class="sxs-lookup"><span data-stu-id="05fbe-183">-Force</span></span>

<span data-ttu-id="05fbe-184">Tar bort ett jobb även om jobbets tillstånd **körs**.</span><span class="sxs-lookup"><span data-stu-id="05fbe-184">Deletes a job even if the job's state is **Running**.</span></span> <span data-ttu-id="05fbe-185">Om **Force** -parametern inte anges `Remove-Job` tar inte bort jobb som körs.</span><span class="sxs-lookup"><span data-stu-id="05fbe-185">If the **Force** parameter isn't specified, `Remove-Job` doesn't delete running jobs.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: SessionIdParameterSet, JobParameterSet, NameParameterSet, InstanceIdParameterSet, FilterParameterSet
Aliases: F

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="05fbe-186">-ID</span><span class="sxs-lookup"><span data-stu-id="05fbe-186">-Id</span></span>

<span data-ttu-id="05fbe-187">Tar bort bakgrunds jobb med angivet **ID**. Du kan ange en kommaavgränsad matris.</span><span class="sxs-lookup"><span data-stu-id="05fbe-187">Deletes background jobs with the specified **Id**. You can enter a comma-separated array.</span></span> <span data-ttu-id="05fbe-188">Jobbets **ID** är ett unikt heltal som identifierar ett jobb inom den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="05fbe-188">The job's **Id** is a unique integer that identifies a job within the current session.</span></span>

<span data-ttu-id="05fbe-189">Använd utan parametrar för att hitta ett jobb **-ID** `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="05fbe-189">To find a job's **Id** , use `Get-Job` without parameters.</span></span>

```yaml
Type: System.Int32[]
Parameter Sets: SessionIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="05fbe-190">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="05fbe-190">-InstanceId</span></span>

<span data-ttu-id="05fbe-191">Tar bort jobb med angivet **InstanceID**.</span><span class="sxs-lookup"><span data-stu-id="05fbe-191">Deletes jobs with the specified **InstanceId**.</span></span> <span data-ttu-id="05fbe-192">Du kan ange en kommaavgränsad matris.</span><span class="sxs-lookup"><span data-stu-id="05fbe-192">You can enter a comma-separated array.</span></span> <span data-ttu-id="05fbe-193">Ett **InstanceID** är ett unikt GUID som identifierar ett jobb.</span><span class="sxs-lookup"><span data-stu-id="05fbe-193">An **InstanceId** is a unique GUID that identifies a job.</span></span>

<span data-ttu-id="05fbe-194">Använd om du vill hitta ett jobbs **InstanceID** `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="05fbe-194">To find a job's **InstanceId** , use `Get-Job`.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="05fbe-195">– Jobb</span><span class="sxs-lookup"><span data-stu-id="05fbe-195">-Job</span></span>

<span data-ttu-id="05fbe-196">Anger vilka jobb som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="05fbe-196">Specifies the jobs to be deleted.</span></span> <span data-ttu-id="05fbe-197">Ange en variabel som innehåller jobben eller ett kommando som hämtar jobben.</span><span class="sxs-lookup"><span data-stu-id="05fbe-197">Enter a variable that contains the jobs or a command that gets the jobs.</span></span> <span data-ttu-id="05fbe-198">Du kan ange en kommaavgränsad matris.</span><span class="sxs-lookup"><span data-stu-id="05fbe-198">You can enter a comma-separated array.</span></span>

<span data-ttu-id="05fbe-199">Du kan skicka jobb objekt nedåt i pipeline till `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="05fbe-199">You can send job objects down the pipeline to `Remove-Job`.</span></span>

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: JobParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="05fbe-200">-Name</span><span class="sxs-lookup"><span data-stu-id="05fbe-200">-Name</span></span>

<span data-ttu-id="05fbe-201">Tar bara bort jobb med angivet eget namn.</span><span class="sxs-lookup"><span data-stu-id="05fbe-201">Only deletes jobs with the specified friendly name.</span></span> <span data-ttu-id="05fbe-202">Jokertecken är tillåtna.</span><span class="sxs-lookup"><span data-stu-id="05fbe-202">Wildcards are permitted.</span></span> <span data-ttu-id="05fbe-203">Du kan ange en kommaavgränsad matris.</span><span class="sxs-lookup"><span data-stu-id="05fbe-203">You can enter a comma-separated array.</span></span>

<span data-ttu-id="05fbe-204">Användarvänliga namn för jobb garanterar inte att vara unika, även inom en PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="05fbe-204">Friendly names for jobs aren't guaranteed to be unique, even within a PowerShell session.</span></span> <span data-ttu-id="05fbe-205">Använd parametrarna **whatIf** och **Confirm** när du tar bort filer efter namn.</span><span class="sxs-lookup"><span data-stu-id="05fbe-205">Use the **WhatIf** and **Confirm** parameters when you delete files by name.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="05fbe-206">– Tillstånd</span><span class="sxs-lookup"><span data-stu-id="05fbe-206">-State</span></span>

<span data-ttu-id="05fbe-207">Tar bara bort jobb med det angivna läget.</span><span class="sxs-lookup"><span data-stu-id="05fbe-207">Only deletes jobs with the specified state.</span></span> <span data-ttu-id="05fbe-208">Använd parametern **Force** om du vill ta bort jobb med statusen **körs**.</span><span class="sxs-lookup"><span data-stu-id="05fbe-208">To delete jobs with a state of **Running** , use the **Force** parameter.</span></span>

<span data-ttu-id="05fbe-209">Godkända värden:</span><span class="sxs-lookup"><span data-stu-id="05fbe-209">Accepted values:</span></span>

- <span data-ttu-id="05fbe-210">AtBreakpoint</span><span class="sxs-lookup"><span data-stu-id="05fbe-210">AtBreakpoint</span></span>
- <span data-ttu-id="05fbe-211">Blockerad</span><span class="sxs-lookup"><span data-stu-id="05fbe-211">Blocked</span></span>
- <span data-ttu-id="05fbe-212">Slutförd</span><span class="sxs-lookup"><span data-stu-id="05fbe-212">Completed</span></span>
- <span data-ttu-id="05fbe-213">Frånkopplad</span><span class="sxs-lookup"><span data-stu-id="05fbe-213">Disconnected</span></span>
- <span data-ttu-id="05fbe-214">Misslyckad</span><span class="sxs-lookup"><span data-stu-id="05fbe-214">Failed</span></span>
- <span data-ttu-id="05fbe-215">NotStarted</span><span class="sxs-lookup"><span data-stu-id="05fbe-215">NotStarted</span></span>
- <span data-ttu-id="05fbe-216">Körs</span><span class="sxs-lookup"><span data-stu-id="05fbe-216">Running</span></span>
- <span data-ttu-id="05fbe-217">Stoppad</span><span class="sxs-lookup"><span data-stu-id="05fbe-217">Stopped</span></span>
- <span data-ttu-id="05fbe-218">Stoppas</span><span class="sxs-lookup"><span data-stu-id="05fbe-218">Stopping</span></span>
- <span data-ttu-id="05fbe-219">Inaktiverad</span><span class="sxs-lookup"><span data-stu-id="05fbe-219">Suspended</span></span>
- <span data-ttu-id="05fbe-220">Pausar</span><span class="sxs-lookup"><span data-stu-id="05fbe-220">Suspending</span></span>

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: AtBreakpoint, Blocked, Completed, Disconnected, Failed, NotStarted, Running, Stopped, Stopping, Suspended, Suspending

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="05fbe-221">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="05fbe-221">-WhatIf</span></span>

<span data-ttu-id="05fbe-222">Visar vad som händer om `Remove-Job` körs.</span><span class="sxs-lookup"><span data-stu-id="05fbe-222">Shows what would happen if `Remove-Job` runs.</span></span> <span data-ttu-id="05fbe-223">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="05fbe-223">The cmdlet isn't run.</span></span>

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

### <span data-ttu-id="05fbe-224">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="05fbe-224">CommonParameters</span></span>

<span data-ttu-id="05fbe-225">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="05fbe-225">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="05fbe-226">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="05fbe-226">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="05fbe-227">INDATA</span><span class="sxs-lookup"><span data-stu-id="05fbe-227">INPUTS</span></span>

### <span data-ttu-id="05fbe-228">System. Management. Automation. job</span><span class="sxs-lookup"><span data-stu-id="05fbe-228">System.Management.Automation.Job</span></span>

<span data-ttu-id="05fbe-229">Du kan skicka ett jobb objekt nedåt i pipeline till `Remove-Job` .</span><span class="sxs-lookup"><span data-stu-id="05fbe-229">You can send a job object down the pipeline to `Remove-Job`.</span></span>

## <span data-ttu-id="05fbe-230">UTDATA</span><span class="sxs-lookup"><span data-stu-id="05fbe-230">OUTPUTS</span></span>

### <span data-ttu-id="05fbe-231">Inget</span><span class="sxs-lookup"><span data-stu-id="05fbe-231">None</span></span>

<span data-ttu-id="05fbe-232">`Remove-Job` genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="05fbe-232">`Remove-Job` doesn't generate any output.</span></span>

## <span data-ttu-id="05fbe-233">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="05fbe-233">NOTES</span></span>

<span data-ttu-id="05fbe-234">Ett PowerShell-jobb skapar en ny process.</span><span class="sxs-lookup"><span data-stu-id="05fbe-234">A PowerShell job creates a new process.</span></span> <span data-ttu-id="05fbe-235">När jobbet har slutförts avslutas processen.</span><span class="sxs-lookup"><span data-stu-id="05fbe-235">When the job completes, the process exits.</span></span> <span data-ttu-id="05fbe-236">När körs `Remove-Job` , tas jobbets tillstånd bort.</span><span class="sxs-lookup"><span data-stu-id="05fbe-236">When `Remove-Job` is run, the job's state is removed.</span></span>

<span data-ttu-id="05fbe-237">Om ett jobb avbryts innan det slutförs och processen inte har avslut ATS, tvingas processen att avslutas.</span><span class="sxs-lookup"><span data-stu-id="05fbe-237">If a job stops before completion and its process hasn't exited, the process is forcibly terminated.</span></span>

## <span data-ttu-id="05fbe-238">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="05fbe-238">RELATED LINKS</span></span>

[<span data-ttu-id="05fbe-239">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="05fbe-239">about_Jobs</span></span>](./About/about_Jobs.md)

[<span data-ttu-id="05fbe-240">about_Job_Details</span><span class="sxs-lookup"><span data-stu-id="05fbe-240">about_Job_Details</span></span>](./About/about_Job_Details.md)

[<span data-ttu-id="05fbe-241">about_Remote_Jobs</span><span class="sxs-lookup"><span data-stu-id="05fbe-241">about_Remote_Jobs</span></span>](./About/about_Remote_Jobs.md)

[<span data-ttu-id="05fbe-242">Hämta jobb</span><span class="sxs-lookup"><span data-stu-id="05fbe-242">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="05fbe-243">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="05fbe-243">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="05fbe-244">Mottagning – jobb</span><span class="sxs-lookup"><span data-stu-id="05fbe-244">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="05fbe-245">Start – jobb</span><span class="sxs-lookup"><span data-stu-id="05fbe-245">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="05fbe-246">Stoppa – jobb</span><span class="sxs-lookup"><span data-stu-id="05fbe-246">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="05fbe-247">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="05fbe-247">Wait-Job</span></span>](Wait-Job.md)