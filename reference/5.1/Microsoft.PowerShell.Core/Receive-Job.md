---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/receive-job?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Receive-Job
ms.openlocfilehash: 7b872c2a28943ee3d2b9ab27459ddb87722cc954
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264219"
---
# <span data-ttu-id="048a2-103">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="048a2-103">Receive-Job</span></span>

## <span data-ttu-id="048a2-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="048a2-104">SYNOPSIS</span></span>
<span data-ttu-id="048a2-105">Hämtar resultatet av PowerShell-bakgrunds jobben i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="048a2-105">Gets the results of the PowerShell background jobs in the current session.</span></span>

## <span data-ttu-id="048a2-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="048a2-106">SYNTAX</span></span>

### <span data-ttu-id="048a2-107">Plats (standard)</span><span class="sxs-lookup"><span data-stu-id="048a2-107">Location (Default)</span></span>

```
Receive-Job [-Job] <Job[]> [[-Location] <String[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### <span data-ttu-id="048a2-108">Session</span><span class="sxs-lookup"><span data-stu-id="048a2-108">Session</span></span>

```
Receive-Job [-Job] <Job[]> [[-Session] <PSSession[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### <span data-ttu-id="048a2-109">ComputerName</span><span class="sxs-lookup"><span data-stu-id="048a2-109">ComputerName</span></span>

```
Receive-Job [-Job] <Job[]> [[-ComputerName] <String[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### <span data-ttu-id="048a2-110">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="048a2-110">NameParameterSet</span></span>

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="048a2-111">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="048a2-111">InstanceIdParameterSet</span></span>

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-InstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="048a2-112">SessionIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="048a2-112">SessionIdParameterSet</span></span>

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-Id] <Int32[]> [<CommonParameters>]
```

## <span data-ttu-id="048a2-113">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="048a2-113">DESCRIPTION</span></span>

<span data-ttu-id="048a2-114">`Receive-Job`Cmdlet: en hämtar resultatet av PowerShell bakgrunds jobb, t. ex. de som har startats med hjälp av `Start-Job` cmdleten eller parametern **AsJob** för valfri cmdlet.</span><span class="sxs-lookup"><span data-stu-id="048a2-114">The `Receive-Job` cmdlet gets the results of PowerShell background jobs, such as those started by using the `Start-Job` cmdlet or the **AsJob** parameter of any cmdlet.</span></span>
<span data-ttu-id="048a2-115">Du kan få resultaten av alla jobb eller identifiera jobb efter namn, ID, instans-ID, dator namn, plats eller session eller genom att skicka ett jobb objekt.</span><span class="sxs-lookup"><span data-stu-id="048a2-115">You can get the results of all jobs or identify jobs by their name, ID, instance ID, computer name, location, or session, or by submitting a job object.</span></span>

<span data-ttu-id="048a2-116">När du startar ett PowerShell-bakgrunds jobb startar jobbet, men resultaten visas inte direkt.</span><span class="sxs-lookup"><span data-stu-id="048a2-116">When you start a PowerShell background job, the job starts, but the results do not appear immediately.</span></span> <span data-ttu-id="048a2-117">I stället returnerar kommandot ett objekt som representerar bakgrunds jobbet.</span><span class="sxs-lookup"><span data-stu-id="048a2-117">Instead, the command returns an object that represents the background job.</span></span>
<span data-ttu-id="048a2-118">Jobbobjektet innehåller användbar information om jobbet, men det innehåller inte resultatet.</span><span class="sxs-lookup"><span data-stu-id="048a2-118">The job object contains useful information about the job, but it does not contain the results.</span></span>
<span data-ttu-id="048a2-119">Med den här metoden kan du fortsätta att arbeta i sessionen medan jobbet körs.</span><span class="sxs-lookup"><span data-stu-id="048a2-119">This method lets you continue to work in the session while the job runs.</span></span>
<span data-ttu-id="048a2-120">Mer information om bakgrunds jobb i PowerShell finns [about_Jobs](./About/about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="048a2-120">For more information about background jobs in PowerShell, see [about_Jobs](./About/about_Jobs.md).</span></span>

<span data-ttu-id="048a2-121">`Receive-Job`Cmdlet: en hämtar de resultat som har genererats vid den tidpunkt då `Receive-Job` kommandot skickas.</span><span class="sxs-lookup"><span data-stu-id="048a2-121">The `Receive-Job` cmdlet gets the results that have been generated by the time that the `Receive-Job` command is submitted.</span></span>
<span data-ttu-id="048a2-122">Om resultatet inte har slutförts ännu kan du köra ytterligare `Receive-Job` kommandon för att få återstående resultat.</span><span class="sxs-lookup"><span data-stu-id="048a2-122">If the results are not yet complete, you can run additional `Receive-Job` commands to get the remaining results.</span></span>

<span data-ttu-id="048a2-123">Som standard tas jobb resultaten bort från systemet när du tar emot dem, men du kan använda parametern **Keep** för att spara resultaten så att du kan ta emot dem igen.</span><span class="sxs-lookup"><span data-stu-id="048a2-123">By default, job results are deleted from the system when you receive them, but you can use the **Keep** parameter to save the results so that you can receive them again.</span></span>
<span data-ttu-id="048a2-124">Om du vill ta bort jobb resultaten kör du `Receive-Job` kommandot igen utan parametern **Keep** , stänger sessionen eller använder `Remove-Job` cmdleten för att ta bort jobbet från sessionen.</span><span class="sxs-lookup"><span data-stu-id="048a2-124">To delete the job results, run the `Receive-Job` command again without the **Keep** parameter, close the session, or use the `Remove-Job` cmdlet to delete the job from the session.</span></span>

<span data-ttu-id="048a2-125">Från och med Windows PowerShell 3,0 `Receive-Job` får även resultaten av anpassade jobb typer, till exempel arbets flödes jobb och instanser av schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="048a2-125">Starting in Windows PowerShell 3.0, `Receive-Job` also gets the results of custom job types, such as workflow jobs and instances of scheduled jobs.</span></span>
<span data-ttu-id="048a2-126">Om du vill göra `Receive-Job` det möjligt att hämta resultatet av en anpassad Jobbtyp importerar du modulen som stöder den anpassade jobb typen till sessionen innan den kör ett `Receive-Job` kommando, antingen med hjälp av `Import-Module` cmdleten eller genom att använda eller hämta en cmdlet i modulen.</span><span class="sxs-lookup"><span data-stu-id="048a2-126">To enable `Receive-Job` to get the results a custom job type, import the module that supports the custom job type into the session before it runs a `Receive-Job` command, either by using the `Import-Module` cmdlet or by using or getting a cmdlet in the module.</span></span>
<span data-ttu-id="048a2-127">Information om en viss anpassad Jobbtyp finns i dokumentationen för den anpassade jobb typ funktionen.</span><span class="sxs-lookup"><span data-stu-id="048a2-127">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="048a2-128">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="048a2-128">EXAMPLES</span></span>

### <span data-ttu-id="048a2-129">Exempel 1: få resultat för ett visst jobb</span><span class="sxs-lookup"><span data-stu-id="048a2-129">Example 1: Get results for a particular job</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
Receive-Job -Job $job
```

<span data-ttu-id="048a2-130">Dessa kommandon använder **jobb** parametern för `Receive-Job` för att hämta resultatet av ett visst jobb.</span><span class="sxs-lookup"><span data-stu-id="048a2-130">These commands use the **Job** parameter of `Receive-Job` to get the results of a particular job.</span></span>

<span data-ttu-id="048a2-131">Det första kommandot startar ett jobb med `Start-Job` och lagrar jobbobjektet i `$job` variabeln.</span><span class="sxs-lookup"><span data-stu-id="048a2-131">The first command starts a job with `Start-Job` and stores the job object in the `$job` variable.</span></span>

<span data-ttu-id="048a2-132">Det andra kommandot använder `Receive-Job` cmdleten för att hämta resultatet av jobbet.</span><span class="sxs-lookup"><span data-stu-id="048a2-132">The second command uses the `Receive-Job` cmdlet to get the results of the job.</span></span>
<span data-ttu-id="048a2-133">Den använder **jobb** parametern för att ange jobbet.</span><span class="sxs-lookup"><span data-stu-id="048a2-133">It uses the **Job** parameter to specify the job.</span></span>

### <span data-ttu-id="048a2-134">Exempel 2: Använd parametern Keep</span><span class="sxs-lookup"><span data-stu-id="048a2-134">Example 2: Use the Keep parameter</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Service dhcp, fakeservice}
$job | Receive-Job -Keep
```

```Output
Cannot find any service with service name 'fakeservice'.
    + CategoryInfo          : ObjectNotFound: (fakeservice:String) [Get-Service], ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.GetServiceCommand
    + PSComputerName        : localhost

Status   Name               DisplayName
------   ----               -----------
Running  dhcp               DHCP Client
```

```powershell
$job | Receive-Job -Keep
```

```output
Cannot find any service with service name 'fakeservice'.
    + CategoryInfo          : ObjectNotFound: (fakeservice:String) [Get-Service], ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.GetServiceCommand
    + PSComputerName        : localhost

Status   Name               DisplayName
------   ----               -----------
Running  dhcp               DHCP Client
```

<span data-ttu-id="048a2-135">I det här exemplet lagras ett jobb i `$job` variabeln och det rör sig om jobbet till `Receive-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="048a2-135">This example stores a job in the `$job` variable, and pipes the job to the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="048a2-136">`-Keep`Parametern används också för att tillåta att alla sammanställda data ström data hämtas igen efter den första vyn.</span><span class="sxs-lookup"><span data-stu-id="048a2-136">The `-Keep` parameter is also used to allow all aggregated stream data to be retrieved again after first view.</span></span>

### <span data-ttu-id="048a2-137">Exempel 3: få resultat från flera bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="048a2-137">Example 3: Get results of several background jobs</span></span>

<span data-ttu-id="048a2-138">När du använder **AsJob** -parametern för `Invoke-Command` för att starta ett jobb skapas jobbobjektet på den lokala datorn, även om jobbet körs på fjärrdatorerna.</span><span class="sxs-lookup"><span data-stu-id="048a2-138">When you use the **AsJob** parameter of `Invoke-Command` to start a job, the job object is created on the local computer, even though the job runs on the remote computers.</span></span>
<span data-ttu-id="048a2-139">Därför använder du lokala kommandon för att hantera jobbet.</span><span class="sxs-lookup"><span data-stu-id="048a2-139">As a result, you use local commands to manage the job.</span></span>

<span data-ttu-id="048a2-140">När du använder **AsJob** returnerar PowerShell dessutom ett jobb objekt som innehåller ett underordnat jobb för varje jobb som startades.</span><span class="sxs-lookup"><span data-stu-id="048a2-140">Also, when you use **AsJob** , PowerShell returns one job object that contains a child job for each job that was started.</span></span> <span data-ttu-id="048a2-141">I det här fallet innehåller jobbobjektet tre underordnade jobb, ett för varje jobb på varje fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="048a2-141">In this case, the job object contains three child jobs, one for each job on each remote computer.</span></span>

```powershell
# Use the Invoke-Command cmdlet with the -AsJob parameter to start a background job that runs a Get-Service command on three remote computers.
# Store the resulting job object in the $j variable
$j = Invoke-Command -ComputerName Server01, Server02, Server03 -ScriptBlock {Get-Service} -AsJob
# Display the value of the **ChildJobs** property of the job object in $j.
# The display shows that the command created three child jobs, one for the job on each remote computer.
# You could also use the -IncludeChildJobs parameter of the Get-Job cmdlet.
$j.ChildJobs
```

```Output
Id   Name     State      HasMoreData   Location       Command
--   ----     -----      -----------   --------       -------
2    Job2     Completed  True          Server01       Get-Service
3    Job3     Completed  True          Server02       Get-Service
4    Job4     Completed  True          Server03       Get-Service
```

```powershell
# Use the Receive-Job cmdlet to get the results of just the Job3 child job that ran on the Server02 computer.
# Use the *Keep* parameter to allow you to view the aggregated stream data more than once.
Receive-Job -Name Job3 -Keep
```

```Output
Status  Name        DisplayName                        PSComputerName
------  ----------- -----------                        --------------
Running AeLookupSvc Application Experience             Server02
Stopped ALG         Application Layer Gateway Service  Server02
Running Appinfo     Application Information            Server02
Running AppMgmt     Application Management             Server02
```

### <span data-ttu-id="048a2-142">Exempel 4: få resultat från bakgrunds jobb på flera fjärrdatorer</span><span class="sxs-lookup"><span data-stu-id="048a2-142">Example 4: Get results of background jobs on multiple remote computers</span></span>

```powershell
# Use the New-PSSession cmdlet to create three user-managed PSSessions on three servers, and save the sessions in the $s variable.
$s = New-PSSession -ComputerName Server01, Server02, Server03
# Use Invoke-Command run a Start-Job command in each of the PSSessions in the $s variable.
# The job outputs the ComputerName of each server.
# Save the job objects in the $j variable.
$j = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {$env:COMPUTERNAME}}
# To confirm that these job objects are from the remote machines, run Get-Job to show no local jobs running.
Get-Job
```

```Output

```

```powershell
# Display the three job objects in $j.
# Note that the Localhost location is not the local computer, but instead localhost as it relates to the job on each Server.
$j
```

```Output
Id   Name     State      HasMoreData   Location   Command
--   ----     -----      -----------   --------   -------
1    Job1     Completed  True          Localhost  $env:COMPUTERNAME
2    Job2     Completed  True          Localhost  $env:COMPUTERNAME
3    Job3     Completed  True          Localhost  $env:COMPUTERNAME
```

```powershell
# Use Invoke-Command to run a Receive-Job command in each of the sessions in the $s variable and save the results in the $Results variable.
# The Receive-Job command must be run in each session because the jobs were run locally on each server.
$results = Invoke-Command -Session $s -ScriptBlock {Receive-Job -Job $Using:j}
```

```Output
Server01
Server02
Server03
```

<span data-ttu-id="048a2-143">I det här exemplet visas hur du får resultaten av bakgrunds jobb som körs på tre fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="048a2-143">This example shows how to get the results of background jobs run on three remote computers.</span></span>
<span data-ttu-id="048a2-144">Till skillnad från föregående exempel, `Invoke-Command` som använder för att köra `Start-Job` kommandot, startade de tre oberoende jobben på var och en av de tre datorerna.</span><span class="sxs-lookup"><span data-stu-id="048a2-144">Unlike the previous example, using `Invoke-Command` to run the `Start-Job` command actually started three independent jobs on each of the three computers.</span></span> <span data-ttu-id="048a2-145">Därför returnerade kommandot tre jobb objekt som representerar tre jobb som körs lokalt på tre olika datorer.</span><span class="sxs-lookup"><span data-stu-id="048a2-145">As a result, the command returned three job objects representing three jobs run locally on three different computers.</span></span>

> [!NOTE]
> <span data-ttu-id="048a2-146">I det sista kommandot, eftersom `$j` är en lokal variabel, använder-skript blocket **using** scope modifierare för att identifiera `$j` variabeln.</span><span class="sxs-lookup"><span data-stu-id="048a2-146">In the last command, because `$j` is a local variable, the script block uses the **Using** scope modifier to identify the `$j` variable.</span></span> <span data-ttu-id="048a2-147">Mer information om hur du **använder** omfångs modifieraren finns [about_Remote_Variables](./About/about_Remote_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="048a2-147">For more information about the **Using** scope modifier, see [about_Remote_Variables](./About/about_Remote_Variables.md).</span></span>

### <span data-ttu-id="048a2-148">Exempel 5: åtkomst till underordnade jobb</span><span class="sxs-lookup"><span data-stu-id="048a2-148">Example 5: Access child jobs</span></span>

<span data-ttu-id="048a2-149">`-Keep`Parametern bevarar statusen för de aggregerade strömmarna för ett jobb så att det kan visas igen.</span><span class="sxs-lookup"><span data-stu-id="048a2-149">The `-Keep` parameter preserves the state of the aggregated streams of a job so that it can be viewed again.</span></span> <span data-ttu-id="048a2-150">Utan den här parametern raderas alla aggregerade data ström data när jobbet tas emot.</span><span class="sxs-lookup"><span data-stu-id="048a2-150">Without this parameter all aggregated stream data is erased when the job is received.</span></span> <span data-ttu-id="048a2-151">Mer information finns i [about_Job_Details](About/about_Job_Details.md#child-jobs)</span><span class="sxs-lookup"><span data-stu-id="048a2-151">For more information, see [about_Job_Details](About/about_Job_Details.md#child-jobs)</span></span>

> [!NOTE]
> <span data-ttu-id="048a2-152">De aggregerade strömmarna inkluderar strömmarna för alla underordnade jobb.</span><span class="sxs-lookup"><span data-stu-id="048a2-152">The aggregated streams include the streams of all child jobs.</span></span> <span data-ttu-id="048a2-153">Du kan fortfarande komma åt de enskilda data strömmarna via jobbobjektet och underordnade jobb objekt.</span><span class="sxs-lookup"><span data-stu-id="048a2-153">You can still reach the individual streams of data through the job object and child job objects.</span></span>

```powershell
Start-Job -Name TestJob -ScriptBlock {dir C:\, Z:\}
# Without the Keep parameter, aggregated child job data is displayed once.
# Then destroyed.
Receive-Job -Name TestJob
```

```output
    Directory: C:\

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-r---        1/24/2019   7:11 AM                Program Files
d-r---        2/13/2019   8:32 AM                Program Files (x86)
d-r---        10/3/2018  11:47 AM                Users
d-----         2/7/2019   1:52 AM                Windows
Cannot find drive. A drive with the name 'Z' does not exist.
    + CategoryInfo          : ObjectNotFound: (Z:String) [Get-ChildItem], DriveNotFoundException
    + FullyQualifiedErrorId : DriveNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
    + PSComputerName        : localhost
```

```powershell
# It would seem that the child job data is gone.
Receive-Job -Name TestJob
```

```output

```

```powershell
# Using the object model, you can still retrieve child job data and streams.
$job = Get-Job -Name TestJob
$job.ChildJobs[0].Error
```

```output
Cannot find drive. A drive with the name 'Z' does not exist.
    + CategoryInfo          : ObjectNotFound: (Z:String) [Get-ChildItem], DriveNotFoundException
    + FullyQualifiedErrorId : DriveNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
    + PSComputerName        : localhost
```

## <span data-ttu-id="048a2-154">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="048a2-154">PARAMETERS</span></span>

### <span data-ttu-id="048a2-155">-AutoRemoveJob</span><span class="sxs-lookup"><span data-stu-id="048a2-155">-AutoRemoveJob</span></span>

<span data-ttu-id="048a2-156">Anger att den här cmdleten tar bort jobbet när det har returnerat jobb resultatet.</span><span class="sxs-lookup"><span data-stu-id="048a2-156">Indicates that this cmdlet deletes the job after it returns the job results.</span></span>
<span data-ttu-id="048a2-157">Om jobbet har fler resultat tas jobbet fortfarande bort, men `Receive-Job` visar ett meddelande.</span><span class="sxs-lookup"><span data-stu-id="048a2-157">If the job has more results, the job is still deleted, but `Receive-Job` displays a message.</span></span>

<span data-ttu-id="048a2-158">Den här parametern fungerar bara på anpassade jobb typer.</span><span class="sxs-lookup"><span data-stu-id="048a2-158">This parameter works only on custom job types.</span></span>
<span data-ttu-id="048a2-159">Den är utformad för instanser av jobb typer som sparar jobbet eller typen utanför sessionen, till exempel instanser av schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="048a2-159">It is designed for instances of job types that save the job or the type outside of the session, such as instances of scheduled jobs.</span></span>

<span data-ttu-id="048a2-160">Den här parametern kan inte användas utan parametern **wait** .</span><span class="sxs-lookup"><span data-stu-id="048a2-160">This parameter cannot be used without the **Wait** parameter.</span></span>

<span data-ttu-id="048a2-161">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="048a2-161">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="048a2-162">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="048a2-162">-ComputerName</span></span>

<span data-ttu-id="048a2-163">Anger en matris med namn på datorer.</span><span class="sxs-lookup"><span data-stu-id="048a2-163">Specifies an array of names of computers.</span></span>

<span data-ttu-id="048a2-164">Den här parametern väljs bland de jobb resultat som lagras på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="048a2-164">This parameter selects from among the job results that are stored on the local computer.</span></span>
<span data-ttu-id="048a2-165">Den hämtar inte data för jobb som körs på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="048a2-165">It does not get data for jobs run on remote computers.</span></span>
<span data-ttu-id="048a2-166">Om du vill hämta jobb resultat som lagras på fjärrdatorer använder du `Invoke-Command` cmdleten för att fjärrköra ett `Receive-Job` kommando.</span><span class="sxs-lookup"><span data-stu-id="048a2-166">To get job results that are stored on remote computers, use the `Invoke-Command` cmdlet to run a `Receive-Job` command remotely.</span></span>

```yaml
Type: System.String[]
Parameter Sets: ComputerName
Aliases: Cn

Required: False
Position: 1
Default value: All computers available
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### <span data-ttu-id="048a2-167">-Force</span><span class="sxs-lookup"><span data-stu-id="048a2-167">-Force</span></span>

<span data-ttu-id="048a2-168">Anger att denna cmdlet fortsätter att vänta om jobb är i tillståndet **Suspended** eller **disconnectd** .</span><span class="sxs-lookup"><span data-stu-id="048a2-168">Indicates that this cmdlet continues waiting if jobs are in the **Suspended** or **Disconnected** state.</span></span> <span data-ttu-id="048a2-169">Som standard returnerar **wait** -parametern i `Receive-Job` returnerar eller avbryter vänte tiden när jobben är i något av följande tillstånd:</span><span class="sxs-lookup"><span data-stu-id="048a2-169">By default, the **Wait** parameter of `Receive-Job` returns, or terminates the wait, when jobs are in one of the following states:</span></span>

- <span data-ttu-id="048a2-170">Slutförd</span><span class="sxs-lookup"><span data-stu-id="048a2-170">Completed</span></span>
- <span data-ttu-id="048a2-171">Misslyckad</span><span class="sxs-lookup"><span data-stu-id="048a2-171">Failed</span></span>
- <span data-ttu-id="048a2-172">Stoppad</span><span class="sxs-lookup"><span data-stu-id="048a2-172">Stopped</span></span>
- <span data-ttu-id="048a2-173">Inaktiverad</span><span class="sxs-lookup"><span data-stu-id="048a2-173">Suspended</span></span>
- <span data-ttu-id="048a2-174">Frånkopplad.</span><span class="sxs-lookup"><span data-stu-id="048a2-174">Disconnected.</span></span>

<span data-ttu-id="048a2-175">Parametern **Force** är giltig endast om parametern **wait** också används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="048a2-175">The **Force** parameter is valid only when the **Wait** parameter is also used in the command.</span></span>

<span data-ttu-id="048a2-176">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="048a2-176">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="048a2-177">-ID</span><span class="sxs-lookup"><span data-stu-id="048a2-177">-Id</span></span>

<span data-ttu-id="048a2-178">Anger en matris med ID: n.</span><span class="sxs-lookup"><span data-stu-id="048a2-178">Specifies an array of IDs.</span></span>
<span data-ttu-id="048a2-179">Den här cmdleten hämtar resultatet av jobb med de angivna ID: na.</span><span class="sxs-lookup"><span data-stu-id="048a2-179">This cmdlet gets the results of jobs with the specified IDs.</span></span>

<span data-ttu-id="048a2-180">ID är ett heltal som unikt identifierar jobbet i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="048a2-180">The ID is an integer that uniquely identifies the job in the current session.</span></span>
<span data-ttu-id="048a2-181">Det är enklare att komma ihåg och skriva än instans-ID, men det är endast unikt i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="048a2-181">It is easier to remember and type than the instance ID, but it is unique only in the current session.</span></span> <span data-ttu-id="048a2-182">Du kan ange ett eller flera ID: n avgränsade med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="048a2-182">You can type one or more IDs separated by commas.</span></span>
<span data-ttu-id="048a2-183">Använd om du vill hitta ID: t för ett jobb `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="048a2-183">To find the ID of a job, use `Get-Job`.</span></span>

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

### <span data-ttu-id="048a2-184">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="048a2-184">-InstanceId</span></span>

<span data-ttu-id="048a2-185">Anger en matris med instans-ID: n.</span><span class="sxs-lookup"><span data-stu-id="048a2-185">Specifies an array of instance IDs.</span></span>
<span data-ttu-id="048a2-186">Den här cmdleten hämtar resultatet av jobb med de angivna instans-ID: na.</span><span class="sxs-lookup"><span data-stu-id="048a2-186">This cmdlet gets the results of jobs with the specified instance IDs.</span></span>

<span data-ttu-id="048a2-187">Ett instans-ID är ett GUID som unikt identifierar jobbet på datorn.</span><span class="sxs-lookup"><span data-stu-id="048a2-187">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span>
<span data-ttu-id="048a2-188">Använd cmdleten för att hitta instans-ID för ett jobb `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="048a2-188">To find the instance ID of a job, use the `Get-Job` cmdlet.</span></span>

```yaml
Type: System.Guid[]
Parameter Sets: InstanceIdParameterSet
Aliases:

Required: True
Position: 0
Default value: All instances
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="048a2-189">– Jobb</span><span class="sxs-lookup"><span data-stu-id="048a2-189">-Job</span></span>

<span data-ttu-id="048a2-190">Anger det jobb för vilket resultat hämtas.</span><span class="sxs-lookup"><span data-stu-id="048a2-190">Specifies the job for which results are being retrieved.</span></span>

<span data-ttu-id="048a2-191">Ange en variabel som innehåller jobbet eller ett kommando som hämtar jobbet.</span><span class="sxs-lookup"><span data-stu-id="048a2-191">Enter a variable that contains the job or a command that gets the job.</span></span>
<span data-ttu-id="048a2-192">Du kan också skicka ett jobb objekt till `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="048a2-192">You can also pipe a job object to `Receive-Job`.</span></span>

```yaml
Type: System.Management.Automation.Job[]
Parameter Sets: Location, Session, ComputerName
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="048a2-193">-Behåll</span><span class="sxs-lookup"><span data-stu-id="048a2-193">-Keep</span></span>

<span data-ttu-id="048a2-194">Anger att denna cmdlet sparar de aggregerade data strömmarna i systemet, även efter att du har tagit emot dem.</span><span class="sxs-lookup"><span data-stu-id="048a2-194">Indicates that this cmdlet saves the aggregated stream data in the system, even after you have received them.</span></span> <span data-ttu-id="048a2-195">Som standard raderas aggregerade data ström data efter att de har visats med `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="048a2-195">By default, aggregated stream data is erased after viewed with `Receive-Job`.</span></span>

<span data-ttu-id="048a2-196">Om du stänger sessionen eller tar bort jobbet med `Remove-Job` cmdleten raderas även sammanställda data ström data.</span><span class="sxs-lookup"><span data-stu-id="048a2-196">Closing the session, or removing the job with the `Remove-Job` cmdlet also deletes aggregated stream data.</span></span>

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

### <span data-ttu-id="048a2-197">– Plats</span><span class="sxs-lookup"><span data-stu-id="048a2-197">-Location</span></span>

<span data-ttu-id="048a2-198">Anger en matris med platser.</span><span class="sxs-lookup"><span data-stu-id="048a2-198">Specifies an array of locations.</span></span>
<span data-ttu-id="048a2-199">Denna cmdlet hämtar bara resultatet av jobb på de angivna platserna.</span><span class="sxs-lookup"><span data-stu-id="048a2-199">This cmdlet gets only the results of jobs in the specified locations.</span></span>

```yaml
Type: System.String[]
Parameter Sets: Location
Aliases:

Required: False
Position: 1
Default value: All locations
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="048a2-200">-Name</span><span class="sxs-lookup"><span data-stu-id="048a2-200">-Name</span></span>

<span data-ttu-id="048a2-201">Anger en matris med användarvänliga namn.</span><span class="sxs-lookup"><span data-stu-id="048a2-201">Specifies an array of friendly names.</span></span>
<span data-ttu-id="048a2-202">Den här cmdleten hämtar resultatet av jobb som har de angivna namnen.</span><span class="sxs-lookup"><span data-stu-id="048a2-202">This cmdlet gets the results of jobs that have the specified names.</span></span>
<span data-ttu-id="048a2-203">Jokertecken stöds.</span><span class="sxs-lookup"><span data-stu-id="048a2-203">Wildcard characters are supported.</span></span>

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

### <span data-ttu-id="048a2-204">-Återkommer</span><span class="sxs-lookup"><span data-stu-id="048a2-204">-NoRecurse</span></span>

<span data-ttu-id="048a2-205">Anger att den här cmdleten endast får resultat från det angivna jobbet.</span><span class="sxs-lookup"><span data-stu-id="048a2-205">Indicates that this cmdlet gets results only from the specified job.</span></span>
<span data-ttu-id="048a2-206">Som standard `Receive-Job` hämtar också resultaten för alla underordnade jobb för det angivna jobbet.</span><span class="sxs-lookup"><span data-stu-id="048a2-206">By default, `Receive-Job` also gets the results of all child jobs of the specified job.</span></span>

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

### <span data-ttu-id="048a2-207">– Session</span><span class="sxs-lookup"><span data-stu-id="048a2-207">-Session</span></span>

<span data-ttu-id="048a2-208">Anger en matris med sessioner.</span><span class="sxs-lookup"><span data-stu-id="048a2-208">Specifies an array of sessions.</span></span>
<span data-ttu-id="048a2-209">Den här cmdleten hämtar resultatet av jobb som kördes i den angivna PowerShell-sessionen ( **PSSession** ).</span><span class="sxs-lookup"><span data-stu-id="048a2-209">This cmdlet gets the results of jobs that were run in the specified PowerShell session ( **PSSession** ).</span></span>
<span data-ttu-id="048a2-210">Ange en variabel som innehåller **PSSession** eller ett kommando som hämtar **PSSession** , till exempel ett `Get-PSSession` kommando.</span><span class="sxs-lookup"><span data-stu-id="048a2-210">Enter a variable that contains the **PSSession** or a command that gets the **PSSession** , such as a `Get-PSSession` command.</span></span>

```yaml
Type: System.Management.Automation.Runspaces.PSSession[]
Parameter Sets: Session
Aliases:

Required: False
Position: 1
Default value: All sessions
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="048a2-211">– Vänta</span><span class="sxs-lookup"><span data-stu-id="048a2-211">-Wait</span></span>

<span data-ttu-id="048a2-212">Anger att denna cmdlet undertrycker kommando tolken tills alla jobb resultat tas emot.</span><span class="sxs-lookup"><span data-stu-id="048a2-212">Indicates that this cmdlet suppresses the command prompt until all job results are received.</span></span>
<span data-ttu-id="048a2-213">Som standard `Receive-Job` returnerar omedelbart de tillgängliga resultaten.</span><span class="sxs-lookup"><span data-stu-id="048a2-213">By default, `Receive-Job` immediately returns the available results.</span></span>

<span data-ttu-id="048a2-214">Som standard väntar parametern **wait** tills jobbet är i något av följande tillstånd:</span><span class="sxs-lookup"><span data-stu-id="048a2-214">By default, the **Wait** parameter waits until the job is in one of the following states:</span></span>

- <span data-ttu-id="048a2-215">Slutförd</span><span class="sxs-lookup"><span data-stu-id="048a2-215">Completed</span></span>
- <span data-ttu-id="048a2-216">Misslyckad</span><span class="sxs-lookup"><span data-stu-id="048a2-216">Failed</span></span>
- <span data-ttu-id="048a2-217">Stoppad</span><span class="sxs-lookup"><span data-stu-id="048a2-217">Stopped</span></span>
- <span data-ttu-id="048a2-218">Inaktiverad</span><span class="sxs-lookup"><span data-stu-id="048a2-218">Suspended</span></span>
- <span data-ttu-id="048a2-219">Frånkopplad.</span><span class="sxs-lookup"><span data-stu-id="048a2-219">Disconnected.</span></span>

<span data-ttu-id="048a2-220">Om du vill att **wait** -parametern ska fortsätta vänta om jobb tillståndet är inaktiverat eller frånkopplat använder du parametern **Force** tillsammans med parametern **wait** .</span><span class="sxs-lookup"><span data-stu-id="048a2-220">To direct the **Wait** parameter to continue waiting if the job state is Suspended or Disconnected, use the **Force** parameter together with the **Wait** parameter.</span></span>

<span data-ttu-id="048a2-221">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="048a2-221">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="048a2-222">-WriteEvents</span><span class="sxs-lookup"><span data-stu-id="048a2-222">-WriteEvents</span></span>

<span data-ttu-id="048a2-223">Anger att denna cmdlet rapporterar ändringar i jobb tillstånd medan den väntar på att jobbet ska slutföras.</span><span class="sxs-lookup"><span data-stu-id="048a2-223">Indicates that this cmdlet reports changes in the job state while it waits for the job to finish.</span></span>

<span data-ttu-id="048a2-224">Den här parametern är endast giltig när parametern **wait** används i kommandot och parametern **Keep** utelämnas.</span><span class="sxs-lookup"><span data-stu-id="048a2-224">This parameter is valid only when the **Wait** parameter is used in the command and the **Keep** parameter is omitted.</span></span>

<span data-ttu-id="048a2-225">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="048a2-225">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="048a2-226">-WriteJobInResults</span><span class="sxs-lookup"><span data-stu-id="048a2-226">-WriteJobInResults</span></span>

<span data-ttu-id="048a2-227">Anger att den här cmdleten returnerar jobbobjektet följt av resultaten.</span><span class="sxs-lookup"><span data-stu-id="048a2-227">Indicates that this cmdlet returns the job object followed by the results.</span></span>

<span data-ttu-id="048a2-228">Den här parametern är endast giltig när parametern **wait** används i kommandot och parametern **Keep** utelämnas.</span><span class="sxs-lookup"><span data-stu-id="048a2-228">This parameter is valid only when the **Wait** parameter is used in the command and the **Keep** parameter is omitted.</span></span>

<span data-ttu-id="048a2-229">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="048a2-229">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="048a2-230">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="048a2-230">CommonParameters</span></span>

<span data-ttu-id="048a2-231">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="048a2-231">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="048a2-232">Mer information finns i [about_CommonParameters](./About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="048a2-232">For more information, see [about_CommonParameters](./About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="048a2-233">INDATA</span><span class="sxs-lookup"><span data-stu-id="048a2-233">INPUTS</span></span>

### <span data-ttu-id="048a2-234">System. Management. Automation. job</span><span class="sxs-lookup"><span data-stu-id="048a2-234">System.Management.Automation.Job</span></span>

<span data-ttu-id="048a2-235">Du kan skicka pipe-jobb objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="048a2-235">You can pipe job objects to this cmdlet.</span></span>

## <span data-ttu-id="048a2-236">UTDATA</span><span class="sxs-lookup"><span data-stu-id="048a2-236">OUTPUTS</span></span>

### <span data-ttu-id="048a2-237">PSObject</span><span class="sxs-lookup"><span data-stu-id="048a2-237">PSObject</span></span>

<span data-ttu-id="048a2-238">Den här cmdleten returnerar resultatet av kommandona i jobbet.</span><span class="sxs-lookup"><span data-stu-id="048a2-238">This cmdlet returns the results of the commands in the job.</span></span>

## <span data-ttu-id="048a2-239">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="048a2-239">NOTES</span></span>

## <span data-ttu-id="048a2-240">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="048a2-240">RELATED LINKS</span></span>

[<span data-ttu-id="048a2-241">Hämta jobb</span><span class="sxs-lookup"><span data-stu-id="048a2-241">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="048a2-242">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="048a2-242">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="048a2-243">Ta bort – jobb</span><span class="sxs-lookup"><span data-stu-id="048a2-243">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="048a2-244">Återuppta – jobb</span><span class="sxs-lookup"><span data-stu-id="048a2-244">Resume-Job</span></span>](Resume-Job.md)

[<span data-ttu-id="048a2-245">Start – jobb</span><span class="sxs-lookup"><span data-stu-id="048a2-245">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="048a2-246">Stoppa – jobb</span><span class="sxs-lookup"><span data-stu-id="048a2-246">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="048a2-247">Pausa – jobb</span><span class="sxs-lookup"><span data-stu-id="048a2-247">Suspend-Job</span></span>](Suspend-Job.md)

[<span data-ttu-id="048a2-248">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="048a2-248">Wait-Job</span></span>](Wait-Job.md)
