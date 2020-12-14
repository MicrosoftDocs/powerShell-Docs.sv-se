---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/receive-job?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Receive-Job
ms.openlocfilehash: 3a11bdb27f3fe16b7b66e82821a3ffe8fa5f6cfa
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710483"
---
# <span data-ttu-id="23816-102">Receive-Job</span><span class="sxs-lookup"><span data-stu-id="23816-102">Receive-Job</span></span>

## <span data-ttu-id="23816-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="23816-103">SYNOPSIS</span></span>
<span data-ttu-id="23816-104">Hämtar resultatet av PowerShell-bakgrunds jobben i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="23816-104">Gets the results of the PowerShell background jobs in the current session.</span></span>

## <span data-ttu-id="23816-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="23816-105">SYNTAX</span></span>

### <span data-ttu-id="23816-106">Plats (standard)</span><span class="sxs-lookup"><span data-stu-id="23816-106">Location (Default)</span></span>

```
Receive-Job [-Job] <Job[]> [[-Location] <String[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### <span data-ttu-id="23816-107">ComputerName</span><span class="sxs-lookup"><span data-stu-id="23816-107">ComputerName</span></span>

```
Receive-Job [-Job] <Job[]> [[-ComputerName] <String[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### <span data-ttu-id="23816-108">Session</span><span class="sxs-lookup"><span data-stu-id="23816-108">Session</span></span>

```
Receive-Job [-Job] <Job[]> [[-Session] <PSSession[]>] [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob]
 [-WriteEvents] [-WriteJobInResults] [<CommonParameters>]
```

### <span data-ttu-id="23816-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="23816-109">NameParameterSet</span></span>

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="23816-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="23816-110">InstanceIdParameterSet</span></span>

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-InstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="23816-111">SessionIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="23816-111">SessionIdParameterSet</span></span>

```
Receive-Job [-Keep] [-NoRecurse] [-Force] [-Wait] [-AutoRemoveJob] [-WriteEvents] [-WriteJobInResults]
 [-Id] <Int32[]> [<CommonParameters>]
```

## <span data-ttu-id="23816-112">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="23816-112">DESCRIPTION</span></span>

<span data-ttu-id="23816-113">`Receive-Job`Cmdlet: en hämtar resultatet av PowerShell bakgrunds jobb, t. ex. de som har startats med hjälp av `Start-Job` cmdleten eller parametern **AsJob** för valfri cmdlet.</span><span class="sxs-lookup"><span data-stu-id="23816-113">The `Receive-Job` cmdlet gets the results of PowerShell background jobs, such as those started by using the `Start-Job` cmdlet or the **AsJob** parameter of any cmdlet.</span></span>
<span data-ttu-id="23816-114">Du kan få resultaten av alla jobb eller identifiera jobb efter namn, ID, instans-ID, dator namn, plats eller session eller genom att skicka ett jobb objekt.</span><span class="sxs-lookup"><span data-stu-id="23816-114">You can get the results of all jobs or identify jobs by their name, ID, instance ID, computer name, location, or session, or by submitting a job object.</span></span>

<span data-ttu-id="23816-115">När du startar ett PowerShell-bakgrunds jobb startar jobbet, men resultaten visas inte direkt.</span><span class="sxs-lookup"><span data-stu-id="23816-115">When you start a PowerShell background job, the job starts, but the results do not appear immediately.</span></span> <span data-ttu-id="23816-116">I stället returnerar kommandot ett objekt som representerar bakgrunds jobbet.</span><span class="sxs-lookup"><span data-stu-id="23816-116">Instead, the command returns an object that represents the background job.</span></span>
<span data-ttu-id="23816-117">Jobbobjektet innehåller användbar information om jobbet, men det innehåller inte resultatet.</span><span class="sxs-lookup"><span data-stu-id="23816-117">The job object contains useful information about the job, but it does not contain the results.</span></span>
<span data-ttu-id="23816-118">Med den här metoden kan du fortsätta att arbeta i sessionen medan jobbet körs.</span><span class="sxs-lookup"><span data-stu-id="23816-118">This method lets you continue to work in the session while the job runs.</span></span>
<span data-ttu-id="23816-119">Mer information om bakgrunds jobb i PowerShell finns [about_Jobs](./About/about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="23816-119">For more information about background jobs in PowerShell, see [about_Jobs](./About/about_Jobs.md).</span></span>

<span data-ttu-id="23816-120">`Receive-Job`Cmdlet: en hämtar de resultat som har genererats vid den tidpunkt då `Receive-Job` kommandot skickas.</span><span class="sxs-lookup"><span data-stu-id="23816-120">The `Receive-Job` cmdlet gets the results that have been generated by the time that the `Receive-Job` command is submitted.</span></span>
<span data-ttu-id="23816-121">Om resultatet inte har slutförts ännu kan du köra ytterligare `Receive-Job` kommandon för att få återstående resultat.</span><span class="sxs-lookup"><span data-stu-id="23816-121">If the results are not yet complete, you can run additional `Receive-Job` commands to get the remaining results.</span></span>

<span data-ttu-id="23816-122">Som standard tas jobb resultaten bort från systemet när du tar emot dem, men du kan använda parametern **Keep** för att spara resultaten så att du kan ta emot dem igen.</span><span class="sxs-lookup"><span data-stu-id="23816-122">By default, job results are deleted from the system when you receive them, but you can use the **Keep** parameter to save the results so that you can receive them again.</span></span>
<span data-ttu-id="23816-123">Om du vill ta bort jobb resultaten kör du `Receive-Job` kommandot igen utan parametern **Keep** , stänger sessionen eller använder `Remove-Job` cmdleten för att ta bort jobbet från sessionen.</span><span class="sxs-lookup"><span data-stu-id="23816-123">To delete the job results, run the `Receive-Job` command again without the **Keep** parameter, close the session, or use the `Remove-Job` cmdlet to delete the job from the session.</span></span>

<span data-ttu-id="23816-124">Från och med Windows PowerShell 3,0 `Receive-Job` får även resultaten av anpassade jobb typer, till exempel arbets flödes jobb och instanser av schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="23816-124">Starting in Windows PowerShell 3.0, `Receive-Job` also gets the results of custom job types, such as workflow jobs and instances of scheduled jobs.</span></span>
<span data-ttu-id="23816-125">Om du vill göra `Receive-Job` det möjligt att hämta resultatet av en anpassad Jobbtyp importerar du modulen som stöder den anpassade jobb typen till sessionen innan den kör ett `Receive-Job` kommando, antingen med hjälp av `Import-Module` cmdleten eller genom att använda eller hämta en cmdlet i modulen.</span><span class="sxs-lookup"><span data-stu-id="23816-125">To enable `Receive-Job` to get the results a custom job type, import the module that supports the custom job type into the session before it runs a `Receive-Job` command, either by using the `Import-Module` cmdlet or by using or getting a cmdlet in the module.</span></span>
<span data-ttu-id="23816-126">Information om en viss anpassad Jobbtyp finns i dokumentationen för den anpassade jobb typ funktionen.</span><span class="sxs-lookup"><span data-stu-id="23816-126">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="23816-127">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="23816-127">EXAMPLES</span></span>

### <span data-ttu-id="23816-128">Exempel 1: få resultat för ett visst jobb</span><span class="sxs-lookup"><span data-stu-id="23816-128">Example 1: Get results for a particular job</span></span>

```powershell
$job = Start-Job -ScriptBlock {Get-Process}
Receive-Job -Job $job
```

<span data-ttu-id="23816-129">Dessa kommandon använder **jobb** parametern för `Receive-Job` för att hämta resultatet av ett visst jobb.</span><span class="sxs-lookup"><span data-stu-id="23816-129">These commands use the **Job** parameter of `Receive-Job` to get the results of a particular job.</span></span>

<span data-ttu-id="23816-130">Det första kommandot startar ett jobb med `Start-Job` och lagrar jobbobjektet i `$job` variabeln.</span><span class="sxs-lookup"><span data-stu-id="23816-130">The first command starts a job with `Start-Job` and stores the job object in the `$job` variable.</span></span>

<span data-ttu-id="23816-131">Det andra kommandot använder `Receive-Job` cmdleten för att hämta resultatet av jobbet.</span><span class="sxs-lookup"><span data-stu-id="23816-131">The second command uses the `Receive-Job` cmdlet to get the results of the job.</span></span>
<span data-ttu-id="23816-132">Den använder **jobb** parametern för att ange jobbet.</span><span class="sxs-lookup"><span data-stu-id="23816-132">It uses the **Job** parameter to specify the job.</span></span>

### <span data-ttu-id="23816-133">Exempel 2: Använd parametern Keep</span><span class="sxs-lookup"><span data-stu-id="23816-133">Example 2: Use the Keep parameter</span></span>

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

```Output
Cannot find any service with service name 'fakeservice'.
    + CategoryInfo          : ObjectNotFound: (fakeservice:String) [Get-Service], ServiceCommandException
    + FullyQualifiedErrorId : NoServiceFoundForGivenName,Microsoft.PowerShell.Commands.GetServiceCommand
    + PSComputerName        : localhost

Status   Name               DisplayName
------   ----               -----------
Running  dhcp               DHCP Client
```

<span data-ttu-id="23816-134">I det här exemplet lagras ett jobb i `$job` variabeln och det rör sig om jobbet till `Receive-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="23816-134">This example stores a job in the `$job` variable, and pipes the job to the `Receive-Job` cmdlet.</span></span> <span data-ttu-id="23816-135">`-Keep`Parametern används också för att tillåta att alla sammanställda data ström data hämtas igen efter den första vyn.</span><span class="sxs-lookup"><span data-stu-id="23816-135">The `-Keep` parameter is also used to allow all aggregated stream data to be retrieved again after first view.</span></span>

### <span data-ttu-id="23816-136">Exempel 3: få resultat från flera bakgrunds jobb</span><span class="sxs-lookup"><span data-stu-id="23816-136">Example 3: Get results of several background jobs</span></span>

<span data-ttu-id="23816-137">När du använder **AsJob** -parametern för `Invoke-Command` för att starta ett jobb skapas jobbobjektet på den lokala datorn, även om jobbet körs på fjärrdatorerna.</span><span class="sxs-lookup"><span data-stu-id="23816-137">When you use the **AsJob** parameter of `Invoke-Command` to start a job, the job object is created on the local computer, even though the job runs on the remote computers.</span></span>
<span data-ttu-id="23816-138">Därför använder du lokala kommandon för att hantera jobbet.</span><span class="sxs-lookup"><span data-stu-id="23816-138">As a result, you use local commands to manage the job.</span></span>

<span data-ttu-id="23816-139">När du använder **AsJob** returnerar PowerShell dessutom ett jobb objekt som innehåller ett underordnat jobb för varje jobb som startades.</span><span class="sxs-lookup"><span data-stu-id="23816-139">Also, when you use **AsJob**, PowerShell returns one job object that contains a child job for each job that was started.</span></span> <span data-ttu-id="23816-140">I det här fallet innehåller jobbobjektet tre underordnade jobb, ett för varje jobb på varje fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="23816-140">In this case, the job object contains three child jobs, one for each job on each remote computer.</span></span>

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

### <span data-ttu-id="23816-141">Exempel 4: få resultat från bakgrunds jobb på flera fjärrdatorer</span><span class="sxs-lookup"><span data-stu-id="23816-141">Example 4: Get results of background jobs on multiple remote computers</span></span>

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

<span data-ttu-id="23816-142">I det här exemplet visas hur du får resultaten av bakgrunds jobb som körs på tre fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="23816-142">This example shows how to get the results of background jobs run on three remote computers.</span></span>
<span data-ttu-id="23816-143">Till skillnad från föregående exempel, `Invoke-Command` som använder för att köra `Start-Job` kommandot, startade de tre oberoende jobben på var och en av de tre datorerna.</span><span class="sxs-lookup"><span data-stu-id="23816-143">Unlike the previous example, using `Invoke-Command` to run the `Start-Job` command actually started three independent jobs on each of the three computers.</span></span> <span data-ttu-id="23816-144">Därför returnerade kommandot tre jobb objekt som representerar tre jobb som körs lokalt på tre olika datorer.</span><span class="sxs-lookup"><span data-stu-id="23816-144">As a result, the command returned three job objects representing three jobs run locally on three different computers.</span></span>

> [!NOTE]
> <span data-ttu-id="23816-145">I det sista kommandot, eftersom `$j` är en lokal variabel, använder-skript blocket **using** scope modifierare för att identifiera `$j` variabeln.</span><span class="sxs-lookup"><span data-stu-id="23816-145">In the last command, because `$j` is a local variable, the script block uses the **Using** scope modifier to identify the `$j` variable.</span></span> <span data-ttu-id="23816-146">Mer information om hur du **använder** omfångs modifieraren finns [about_Remote_Variables](./About/about_Remote_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="23816-146">For more information about the **Using** scope modifier, see [about_Remote_Variables](./About/about_Remote_Variables.md).</span></span>

### <span data-ttu-id="23816-147">Exempel 5: åtkomst till underordnade jobb</span><span class="sxs-lookup"><span data-stu-id="23816-147">Example 5: Access child jobs</span></span>

<span data-ttu-id="23816-148">`-Keep`Parametern bevarar statusen för de aggregerade strömmarna för ett jobb så att det kan visas igen.</span><span class="sxs-lookup"><span data-stu-id="23816-148">The `-Keep` parameter preserves the state of the aggregated streams of a job so that it can be viewed again.</span></span> <span data-ttu-id="23816-149">Utan den här parametern raderas alla aggregerade data ström data när jobbet tas emot.</span><span class="sxs-lookup"><span data-stu-id="23816-149">Without this parameter all aggregated stream data is erased when the job is received.</span></span> <span data-ttu-id="23816-150">Mer information finns i [about_Job_Details](About/about_Job_Details.md#child-jobs)</span><span class="sxs-lookup"><span data-stu-id="23816-150">For more information, see [about_Job_Details](About/about_Job_Details.md#child-jobs)</span></span>

> [!NOTE]
> <span data-ttu-id="23816-151">De aggregerade strömmarna inkluderar strömmarna för alla underordnade jobb.</span><span class="sxs-lookup"><span data-stu-id="23816-151">The aggregated streams include the streams of all child jobs.</span></span> <span data-ttu-id="23816-152">Du kan fortfarande komma åt de enskilda data strömmarna via jobbobjektet och underordnade jobb objekt.</span><span class="sxs-lookup"><span data-stu-id="23816-152">You can still reach the individual streams of data through the job object and child job objects.</span></span>

```powershell
Start-Job -Name TestJob -ScriptBlock {dir C:\, Z:\}
# Without the Keep parameter, aggregated child job data is displayed once.
# Then destroyed.
Receive-Job -Name TestJob
```

```Output
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

```Output

```

```powershell
# Using the object model, you can still retrieve child job data and streams.
$job = Get-Job -Name TestJob
$job.ChildJobs[0].Error
```

```Output
Cannot find drive. A drive with the name 'Z' does not exist.
    + CategoryInfo          : ObjectNotFound: (Z:String) [Get-ChildItem], DriveNotFoundException
    + FullyQualifiedErrorId : DriveNotFound,Microsoft.PowerShell.Commands.GetChildItemCommand
    + PSComputerName        : localhost
```

## <span data-ttu-id="23816-153">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="23816-153">PARAMETERS</span></span>

### <span data-ttu-id="23816-154">-AutoRemoveJob</span><span class="sxs-lookup"><span data-stu-id="23816-154">-AutoRemoveJob</span></span>

<span data-ttu-id="23816-155">Anger att den här cmdleten tar bort jobbet när det har returnerat jobb resultatet.</span><span class="sxs-lookup"><span data-stu-id="23816-155">Indicates that this cmdlet deletes the job after it returns the job results.</span></span>
<span data-ttu-id="23816-156">Om jobbet har fler resultat tas jobbet fortfarande bort, men `Receive-Job` visar ett meddelande.</span><span class="sxs-lookup"><span data-stu-id="23816-156">If the job has more results, the job is still deleted, but `Receive-Job` displays a message.</span></span>

<span data-ttu-id="23816-157">Den här parametern fungerar bara på anpassade jobb typer.</span><span class="sxs-lookup"><span data-stu-id="23816-157">This parameter works only on custom job types.</span></span>
<span data-ttu-id="23816-158">Den är utformad för instanser av jobb typer som sparar jobbet eller typen utanför sessionen, till exempel instanser av schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="23816-158">It is designed for instances of job types that save the job or the type outside of the session, such as instances of scheduled jobs.</span></span>

<span data-ttu-id="23816-159">Den här parametern kan inte användas utan parametern **wait** .</span><span class="sxs-lookup"><span data-stu-id="23816-159">This parameter cannot be used without the **Wait** parameter.</span></span>

<span data-ttu-id="23816-160">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="23816-160">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="23816-161">-ComputerName</span><span class="sxs-lookup"><span data-stu-id="23816-161">-ComputerName</span></span>

<span data-ttu-id="23816-162">Anger en matris med namn på datorer.</span><span class="sxs-lookup"><span data-stu-id="23816-162">Specifies an array of names of computers.</span></span>

<span data-ttu-id="23816-163">Den här parametern väljs bland de jobb resultat som lagras på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="23816-163">This parameter selects from among the job results that are stored on the local computer.</span></span>
<span data-ttu-id="23816-164">Den hämtar inte data för jobb som körs på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="23816-164">It does not get data for jobs run on remote computers.</span></span>
<span data-ttu-id="23816-165">Om du vill hämta jobb resultat som lagras på fjärrdatorer använder du `Invoke-Command` cmdleten för att fjärrköra ett `Receive-Job` kommando.</span><span class="sxs-lookup"><span data-stu-id="23816-165">To get job results that are stored on remote computers, use the `Invoke-Command` cmdlet to run a `Receive-Job` command remotely.</span></span>

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

### <span data-ttu-id="23816-166">-Force</span><span class="sxs-lookup"><span data-stu-id="23816-166">-Force</span></span>

<span data-ttu-id="23816-167">Anger att denna cmdlet fortsätter att vänta om jobb är i tillståndet **Suspended** eller **disconnectd** .</span><span class="sxs-lookup"><span data-stu-id="23816-167">Indicates that this cmdlet continues waiting if jobs are in the **Suspended** or **Disconnected** state.</span></span> <span data-ttu-id="23816-168">Som standard returnerar **wait** -parametern i `Receive-Job` returnerar eller avbryter vänte tiden när jobben är i något av följande tillstånd:</span><span class="sxs-lookup"><span data-stu-id="23816-168">By default, the **Wait** parameter of `Receive-Job` returns, or terminates the wait, when jobs are in one of the following states:</span></span>

- <span data-ttu-id="23816-169">Slutförd</span><span class="sxs-lookup"><span data-stu-id="23816-169">Completed</span></span>
- <span data-ttu-id="23816-170">Misslyckad</span><span class="sxs-lookup"><span data-stu-id="23816-170">Failed</span></span>
- <span data-ttu-id="23816-171">Stoppad</span><span class="sxs-lookup"><span data-stu-id="23816-171">Stopped</span></span>
- <span data-ttu-id="23816-172">Inaktiverad</span><span class="sxs-lookup"><span data-stu-id="23816-172">Suspended</span></span>
- <span data-ttu-id="23816-173">Frånkopplad.</span><span class="sxs-lookup"><span data-stu-id="23816-173">Disconnected.</span></span>

<span data-ttu-id="23816-174">Parametern **Force** är giltig endast om parametern **wait** också används i kommandot.</span><span class="sxs-lookup"><span data-stu-id="23816-174">The **Force** parameter is valid only when the **Wait** parameter is also used in the command.</span></span>

<span data-ttu-id="23816-175">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="23816-175">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="23816-176">-ID</span><span class="sxs-lookup"><span data-stu-id="23816-176">-Id</span></span>

<span data-ttu-id="23816-177">Anger en matris med ID: n.</span><span class="sxs-lookup"><span data-stu-id="23816-177">Specifies an array of IDs.</span></span>
<span data-ttu-id="23816-178">Den här cmdleten hämtar resultatet av jobb med de angivna ID: na.</span><span class="sxs-lookup"><span data-stu-id="23816-178">This cmdlet gets the results of jobs with the specified IDs.</span></span>

<span data-ttu-id="23816-179">ID är ett heltal som unikt identifierar jobbet i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="23816-179">The ID is an integer that uniquely identifies the job in the current session.</span></span>
<span data-ttu-id="23816-180">Det är enklare att komma ihåg och skriva än instans-ID, men det är endast unikt i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="23816-180">It is easier to remember and type than the instance ID, but it is unique only in the current session.</span></span> <span data-ttu-id="23816-181">Du kan ange ett eller flera ID: n avgränsade med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="23816-181">You can type one or more IDs separated by commas.</span></span>
<span data-ttu-id="23816-182">Använd om du vill hitta ID: t för ett jobb `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="23816-182">To find the ID of a job, use `Get-Job`.</span></span>

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

### <span data-ttu-id="23816-183">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="23816-183">-InstanceId</span></span>

<span data-ttu-id="23816-184">Anger en matris med instans-ID: n.</span><span class="sxs-lookup"><span data-stu-id="23816-184">Specifies an array of instance IDs.</span></span>
<span data-ttu-id="23816-185">Den här cmdleten hämtar resultatet av jobb med de angivna instans-ID: na.</span><span class="sxs-lookup"><span data-stu-id="23816-185">This cmdlet gets the results of jobs with the specified instance IDs.</span></span>

<span data-ttu-id="23816-186">Ett instans-ID är ett GUID som unikt identifierar jobbet på datorn.</span><span class="sxs-lookup"><span data-stu-id="23816-186">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span>
<span data-ttu-id="23816-187">Använd cmdleten för att hitta instans-ID för ett jobb `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="23816-187">To find the instance ID of a job, use the `Get-Job` cmdlet.</span></span>

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

### <span data-ttu-id="23816-188">– Jobb</span><span class="sxs-lookup"><span data-stu-id="23816-188">-Job</span></span>

<span data-ttu-id="23816-189">Anger det jobb för vilket resultat hämtas.</span><span class="sxs-lookup"><span data-stu-id="23816-189">Specifies the job for which results are being retrieved.</span></span>

<span data-ttu-id="23816-190">Ange en variabel som innehåller jobbet eller ett kommando som hämtar jobbet.</span><span class="sxs-lookup"><span data-stu-id="23816-190">Enter a variable that contains the job or a command that gets the job.</span></span>
<span data-ttu-id="23816-191">Du kan också skicka ett jobb objekt till `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="23816-191">You can also pipe a job object to `Receive-Job`.</span></span>

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

### <span data-ttu-id="23816-192">-Behåll</span><span class="sxs-lookup"><span data-stu-id="23816-192">-Keep</span></span>

<span data-ttu-id="23816-193">Anger att denna cmdlet sparar de aggregerade data strömmarna i systemet, även efter att du har tagit emot dem.</span><span class="sxs-lookup"><span data-stu-id="23816-193">Indicates that this cmdlet saves the aggregated stream data in the system, even after you have received them.</span></span> <span data-ttu-id="23816-194">Som standard raderas aggregerade data ström data efter att de har visats med `Receive-Job` .</span><span class="sxs-lookup"><span data-stu-id="23816-194">By default, aggregated stream data is erased after viewed with `Receive-Job`.</span></span>

<span data-ttu-id="23816-195">Om du stänger sessionen eller tar bort jobbet med `Remove-Job` cmdleten raderas även sammanställda data ström data.</span><span class="sxs-lookup"><span data-stu-id="23816-195">Closing the session, or removing the job with the `Remove-Job` cmdlet also deletes aggregated stream data.</span></span>

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

### <span data-ttu-id="23816-196">– Plats</span><span class="sxs-lookup"><span data-stu-id="23816-196">-Location</span></span>

<span data-ttu-id="23816-197">Anger en matris med platser.</span><span class="sxs-lookup"><span data-stu-id="23816-197">Specifies an array of locations.</span></span>
<span data-ttu-id="23816-198">Denna cmdlet hämtar bara resultatet av jobb på de angivna platserna.</span><span class="sxs-lookup"><span data-stu-id="23816-198">This cmdlet gets only the results of jobs in the specified locations.</span></span>

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

### <span data-ttu-id="23816-199">-Name</span><span class="sxs-lookup"><span data-stu-id="23816-199">-Name</span></span>

<span data-ttu-id="23816-200">Anger en matris med användarvänliga namn.</span><span class="sxs-lookup"><span data-stu-id="23816-200">Specifies an array of friendly names.</span></span>
<span data-ttu-id="23816-201">Den här cmdleten hämtar resultatet av jobb som har de angivna namnen.</span><span class="sxs-lookup"><span data-stu-id="23816-201">This cmdlet gets the results of jobs that have the specified names.</span></span>
<span data-ttu-id="23816-202">Jokertecken stöds.</span><span class="sxs-lookup"><span data-stu-id="23816-202">Wildcard characters are supported.</span></span>

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

### <span data-ttu-id="23816-203">-Återkommer</span><span class="sxs-lookup"><span data-stu-id="23816-203">-NoRecurse</span></span>

<span data-ttu-id="23816-204">Anger att den här cmdleten endast får resultat från det angivna jobbet.</span><span class="sxs-lookup"><span data-stu-id="23816-204">Indicates that this cmdlet gets results only from the specified job.</span></span>
<span data-ttu-id="23816-205">Som standard `Receive-Job` hämtar också resultaten för alla underordnade jobb för det angivna jobbet.</span><span class="sxs-lookup"><span data-stu-id="23816-205">By default, `Receive-Job` also gets the results of all child jobs of the specified job.</span></span>

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

### <span data-ttu-id="23816-206">– Session</span><span class="sxs-lookup"><span data-stu-id="23816-206">-Session</span></span>

<span data-ttu-id="23816-207">Anger en matris med sessioner.</span><span class="sxs-lookup"><span data-stu-id="23816-207">Specifies an array of sessions.</span></span>
<span data-ttu-id="23816-208">Den här cmdleten hämtar resultatet av jobb som kördes i den angivna PowerShell-sessionen (**PSSession**).</span><span class="sxs-lookup"><span data-stu-id="23816-208">This cmdlet gets the results of jobs that were run in the specified PowerShell session (**PSSession**).</span></span>
<span data-ttu-id="23816-209">Ange en variabel som innehåller **PSSession** eller ett kommando som hämtar **PSSession**, till exempel ett `Get-PSSession` kommando.</span><span class="sxs-lookup"><span data-stu-id="23816-209">Enter a variable that contains the **PSSession** or a command that gets the **PSSession**, such as a `Get-PSSession` command.</span></span>

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

### <span data-ttu-id="23816-210">– Vänta</span><span class="sxs-lookup"><span data-stu-id="23816-210">-Wait</span></span>

<span data-ttu-id="23816-211">Anger att denna cmdlet undertrycker kommando tolken tills alla jobb resultat tas emot.</span><span class="sxs-lookup"><span data-stu-id="23816-211">Indicates that this cmdlet suppresses the command prompt until all job results are received.</span></span>
<span data-ttu-id="23816-212">Som standard `Receive-Job` returnerar omedelbart de tillgängliga resultaten.</span><span class="sxs-lookup"><span data-stu-id="23816-212">By default, `Receive-Job` immediately returns the available results.</span></span>

<span data-ttu-id="23816-213">Som standard väntar parametern **wait** tills jobbet är i något av följande tillstånd:</span><span class="sxs-lookup"><span data-stu-id="23816-213">By default, the **Wait** parameter waits until the job is in one of the following states:</span></span>

- <span data-ttu-id="23816-214">Slutförd</span><span class="sxs-lookup"><span data-stu-id="23816-214">Completed</span></span>
- <span data-ttu-id="23816-215">Misslyckad</span><span class="sxs-lookup"><span data-stu-id="23816-215">Failed</span></span>
- <span data-ttu-id="23816-216">Stoppad</span><span class="sxs-lookup"><span data-stu-id="23816-216">Stopped</span></span>
- <span data-ttu-id="23816-217">Inaktiverad</span><span class="sxs-lookup"><span data-stu-id="23816-217">Suspended</span></span>
- <span data-ttu-id="23816-218">Frånkopplad.</span><span class="sxs-lookup"><span data-stu-id="23816-218">Disconnected.</span></span>

<span data-ttu-id="23816-219">Om du vill att **wait** -parametern ska fortsätta vänta om jobb tillståndet är inaktiverat eller frånkopplat använder du parametern **Force** tillsammans med parametern **wait** .</span><span class="sxs-lookup"><span data-stu-id="23816-219">To direct the **Wait** parameter to continue waiting if the job state is Suspended or Disconnected, use the **Force** parameter together with the **Wait** parameter.</span></span>

<span data-ttu-id="23816-220">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="23816-220">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="23816-221">-WriteEvents</span><span class="sxs-lookup"><span data-stu-id="23816-221">-WriteEvents</span></span>

<span data-ttu-id="23816-222">Anger att denna cmdlet rapporterar ändringar i jobb tillstånd medan den väntar på att jobbet ska slutföras.</span><span class="sxs-lookup"><span data-stu-id="23816-222">Indicates that this cmdlet reports changes in the job state while it waits for the job to finish.</span></span>

<span data-ttu-id="23816-223">Den här parametern är endast giltig när parametern **wait** används i kommandot och parametern **Keep** utelämnas.</span><span class="sxs-lookup"><span data-stu-id="23816-223">This parameter is valid only when the **Wait** parameter is used in the command and the **Keep** parameter is omitted.</span></span>

<span data-ttu-id="23816-224">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="23816-224">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="23816-225">-WriteJobInResults</span><span class="sxs-lookup"><span data-stu-id="23816-225">-WriteJobInResults</span></span>

<span data-ttu-id="23816-226">Anger att den här cmdleten returnerar jobbobjektet följt av resultaten.</span><span class="sxs-lookup"><span data-stu-id="23816-226">Indicates that this cmdlet returns the job object followed by the results.</span></span>

<span data-ttu-id="23816-227">Den här parametern är endast giltig när parametern **wait** används i kommandot och parametern **Keep** utelämnas.</span><span class="sxs-lookup"><span data-stu-id="23816-227">This parameter is valid only when the **Wait** parameter is used in the command and the **Keep** parameter is omitted.</span></span>

<span data-ttu-id="23816-228">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="23816-228">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="23816-229">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="23816-229">CommonParameters</span></span>

<span data-ttu-id="23816-230">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="23816-230">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="23816-231">Mer information finns i [about_CommonParameters](./About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="23816-231">For more information, see [about_CommonParameters](./About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="23816-232">INDATA</span><span class="sxs-lookup"><span data-stu-id="23816-232">INPUTS</span></span>

### <span data-ttu-id="23816-233">System. Management. Automation. job</span><span class="sxs-lookup"><span data-stu-id="23816-233">System.Management.Automation.Job</span></span>

<span data-ttu-id="23816-234">Du kan skicka pipe-jobb objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="23816-234">You can pipe job objects to this cmdlet.</span></span>

## <span data-ttu-id="23816-235">UTDATA</span><span class="sxs-lookup"><span data-stu-id="23816-235">OUTPUTS</span></span>

### <span data-ttu-id="23816-236">PSObject</span><span class="sxs-lookup"><span data-stu-id="23816-236">PSObject</span></span>

<span data-ttu-id="23816-237">Den här cmdleten returnerar resultatet av kommandona i jobbet.</span><span class="sxs-lookup"><span data-stu-id="23816-237">This cmdlet returns the results of the commands in the job.</span></span>

## <span data-ttu-id="23816-238">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="23816-238">NOTES</span></span>

## <span data-ttu-id="23816-239">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="23816-239">RELATED LINKS</span></span>

[<span data-ttu-id="23816-240">Hämta jobb</span><span class="sxs-lookup"><span data-stu-id="23816-240">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="23816-241">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="23816-241">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="23816-242">Ta bort – jobb</span><span class="sxs-lookup"><span data-stu-id="23816-242">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="23816-243">Start – jobb</span><span class="sxs-lookup"><span data-stu-id="23816-243">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="23816-244">Stoppa – jobb</span><span class="sxs-lookup"><span data-stu-id="23816-244">Stop-Job</span></span>](Stop-Job.md)

[<span data-ttu-id="23816-245">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="23816-245">Wait-Job</span></span>](Wait-Job.md)

