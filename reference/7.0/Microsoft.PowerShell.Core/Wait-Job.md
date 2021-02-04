---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 01/28/2021
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/wait-job?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Job
ms.openlocfilehash: 591d418c47cddc7dc1c9dd055d6bd0698a2245b0
ms.sourcegitcommit: 81558c2adb9d109946a027e5b96e4d24b3b13747
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/30/2021
ms.locfileid: "99098712"
---
# <span data-ttu-id="a17a9-103">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="a17a9-103">Wait-Job</span></span>

## <span data-ttu-id="a17a9-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="a17a9-104">SYNOPSIS</span></span>
<span data-ttu-id="a17a9-105">Väntar tills ett eller flera av de PowerShell-jobb som körs i sessionen är i ett avslutande tillstånd.</span><span class="sxs-lookup"><span data-stu-id="a17a9-105">Waits until one or all of the PowerShell jobs running in the session are in a terminating state.</span></span>

## <span data-ttu-id="a17a9-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="a17a9-106">SYNTAX</span></span>

### <span data-ttu-id="a17a9-107">SessionIdParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="a17a9-107">SessionIdParameterSet (Default)</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Id] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="a17a9-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="a17a9-108">JobParameterSet</span></span>

```
Wait-Job [-Job] <Job[]> [-Any] [-Timeout <Int32>] [-Force] [<CommonParameters>]
```

### <span data-ttu-id="a17a9-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="a17a9-109">NameParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="a17a9-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="a17a9-110">InstanceIdParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="a17a9-111">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="a17a9-111">StateParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-State] <JobState> [<CommonParameters>]
```

### <span data-ttu-id="a17a9-112">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="a17a9-112">FilterParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Filter] <Hashtable> [<CommonParameters>]
```

## <span data-ttu-id="a17a9-113">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="a17a9-113">DESCRIPTION</span></span>

<span data-ttu-id="a17a9-114">`Wait-Job`Cmdleten väntar på att ett jobb ska vara i ett avslutande tillstånd innan körningen fortsätter.</span><span class="sxs-lookup"><span data-stu-id="a17a9-114">The `Wait-Job` cmdlet waits for a job to be in a terminating state before continuing execution.</span></span>
<span data-ttu-id="a17a9-115">De avslutande tillstånden är:</span><span class="sxs-lookup"><span data-stu-id="a17a9-115">The terminating states are:</span></span>

- <span data-ttu-id="a17a9-116">Slutförd</span><span class="sxs-lookup"><span data-stu-id="a17a9-116">Completed</span></span>
- <span data-ttu-id="a17a9-117">Misslyckad</span><span class="sxs-lookup"><span data-stu-id="a17a9-117">Failed</span></span>
- <span data-ttu-id="a17a9-118">Stoppad</span><span class="sxs-lookup"><span data-stu-id="a17a9-118">Stopped</span></span>
- <span data-ttu-id="a17a9-119">Inaktiverad</span><span class="sxs-lookup"><span data-stu-id="a17a9-119">Suspended</span></span>
- <span data-ttu-id="a17a9-120">Frånkopplad</span><span class="sxs-lookup"><span data-stu-id="a17a9-120">Disconnected</span></span>

<span data-ttu-id="a17a9-121">Du kan vänta tills ett visst jobb eller att alla jobb är i ett avslutande tillstånd.</span><span class="sxs-lookup"><span data-stu-id="a17a9-121">You can wait until a specified job, or all jobs are in a terminating state.</span></span> <span data-ttu-id="a17a9-122">Du kan också ange en maximal vänte tid för jobbet med hjälp av parametern **timeout** , eller använda **Force** -parametern för att vänta på ett jobb i `Suspended` eller- `Disconnected` tillstånd.</span><span class="sxs-lookup"><span data-stu-id="a17a9-122">You can also set a maximum wait time for the job using the **Timeout** parameter, or use the **Force** parameter to wait for a job in the `Suspended` or `Disconnected` states.</span></span>

<span data-ttu-id="a17a9-123">När kommandona i jobbet har slutförts, `Wait-Job` returnerar ett jobb objekt och fortsätter körningen.</span><span class="sxs-lookup"><span data-stu-id="a17a9-123">When the commands in the job are complete, `Wait-Job` returns a job object and continues execution.</span></span>

<span data-ttu-id="a17a9-124">Du kan använda `Wait-Job` cmdleten för att vänta tills jobben har startats med hjälp av `Start-Job` cmdleten eller **AsJob** -parametern för `Invoke-Command` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a17a9-124">You can use the `Wait-Job` cmdlet to wait for jobs started by using the `Start-Job` cmdlet or the **AsJob** parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="a17a9-125">Mer information om jobb finns i [about_Jobs](./about/about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="a17a9-125">For more information about jobs, see [about_Jobs](./about/about_Jobs.md).</span></span>

<span data-ttu-id="a17a9-126">Från och med Windows PowerShell 3,0 `Wait-Job` väntar cmdleten även på anpassade jobb typer, till exempel arbets flödes jobb och instanser av schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="a17a9-126">Starting in Windows PowerShell 3.0, the `Wait-Job` cmdlet also waits for custom job types, such as workflow jobs and instances of scheduled jobs.</span></span> <span data-ttu-id="a17a9-127">Om du vill kunna `Wait-Job` vänta på jobb av en viss typ importerar du modulen som stöder den anpassade jobb typen till sessionen innan du kör `Get-Job` cmdleten, antingen med hjälp av `Import-Module` cmdleten eller genom att använda eller hämta en cmdlet i modulen.</span><span class="sxs-lookup"><span data-stu-id="a17a9-127">To enable `Wait-Job` to wait for jobs of a particular type, import the module that supports the custom job type into the session before you run the `Get-Job` cmdlet, either by using the `Import-Module` cmdlet or by using or getting a cmdlet in the module.</span></span> <span data-ttu-id="a17a9-128">Information om en viss anpassad Jobbtyp finns i dokumentationen för den anpassade jobb typ funktionen.</span><span class="sxs-lookup"><span data-stu-id="a17a9-128">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="a17a9-129">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="a17a9-129">EXAMPLES</span></span>

### <span data-ttu-id="a17a9-130">Exempel 1: vänta på alla jobb</span><span class="sxs-lookup"><span data-stu-id="a17a9-130">Example 1: Wait for all jobs</span></span>

```powershell
Get-Job | Wait-Job
```

<span data-ttu-id="a17a9-131">Det här kommandot väntar på att alla jobb som körs i sessionen ska slutföras.</span><span class="sxs-lookup"><span data-stu-id="a17a9-131">This command waits for all of the jobs running in the session to finish.</span></span>

### <span data-ttu-id="a17a9-132">Exempel 2: vänta tills jobben har startats på fjärrdatorer med hjälp av Start-Job</span><span class="sxs-lookup"><span data-stu-id="a17a9-132">Example 2: Wait for jobs started on remote computers by using Start-Job</span></span>

```powershell
$s = New-PSSession Server01, Server02, Server03
Invoke-Command -Session $s -ScriptBlock {Start-Job -Name Date1 -ScriptBlock {Get-Date}}
$done = Invoke-Command -Session $s -Command {Wait-Job -Name Date1}
$done.Count
```

```Output
3
```

<span data-ttu-id="a17a9-133">Det här exemplet visar hur du använder `Wait-Job` cmdleten med jobb som har startats på fjärrdatorer med hjälp av `Start-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a17a9-133">This example shows how to use the `Wait-Job` cmdlet with jobs started on remote computers by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="a17a9-134">Både- `Start-Job` och- `Wait-Job` kommandon skickas till fjärrdatorn med hjälp av `Invoke-Command` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a17a9-134">Both `Start-Job` and `Wait-Job` commands are submitted to the remote computer by using the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="a17a9-135">I det här exemplet används `Wait-Job` för att avgöra om ett `Get-Date` kommando som körs som ett jobb på tre olika datorer är klart.</span><span class="sxs-lookup"><span data-stu-id="a17a9-135">This example uses `Wait-Job` to determine whether a `Get-Date` command running as a job on three different computers is finished.</span></span>

<span data-ttu-id="a17a9-136">Det första kommandot skapar en Windows PowerShell-session (**PSSession**) på var och en av de tre fjärrdatorerna och lagrar dem i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="a17a9-136">The first command creates a Windows PowerShell session (**PSSession**) on each of the three remote computers and stores them in the `$s` variable.</span></span>

<span data-ttu-id="a17a9-137">Det andra kommandot använder `Invoke-Command` för att köra `Start-Job` i var och en av de tre sessionerna i `$s` .</span><span class="sxs-lookup"><span data-stu-id="a17a9-137">The second command uses `Invoke-Command` to run `Start-Job` in each of the three sessions in `$s`.</span></span>
<span data-ttu-id="a17a9-138">Alla jobb har namnet datum1.</span><span class="sxs-lookup"><span data-stu-id="a17a9-138">All of the jobs are named Date1.</span></span>

<span data-ttu-id="a17a9-139">Det tredje kommandot använder `Invoke-Command` för att köra `Wait-Job` .</span><span class="sxs-lookup"><span data-stu-id="a17a9-139">The third command uses `Invoke-Command` to run `Wait-Job`.</span></span> <span data-ttu-id="a17a9-140">Det här kommandot väntar på `Date1` att jobben på varje dator ska slutföras.</span><span class="sxs-lookup"><span data-stu-id="a17a9-140">This command waits for the `Date1` jobs on each computer to finish.</span></span> <span data-ttu-id="a17a9-141">Den innehåller den resulterande samlingen (**matris**) för **jobb** objekt i `$done` variabeln.</span><span class="sxs-lookup"><span data-stu-id="a17a9-141">It stores the resulting collection (**array**) of **job** objects in the `$done` variable.</span></span>

<span data-ttu-id="a17a9-142">Det fjärde kommandot använder egenskapen **Count** i matrisen med jobb objekt i `$done` variabeln för att fastställa hur många av jobben som är klara.</span><span class="sxs-lookup"><span data-stu-id="a17a9-142">The fourth command uses the **Count** property of the array of job objects in the `$done` variable to determine how many of the jobs are finished.</span></span>

### <span data-ttu-id="a17a9-143">Exempel 3: Bestäm när det första jobbet slutförs</span><span class="sxs-lookup"><span data-stu-id="a17a9-143">Example 3: Determine when the first job finishes</span></span>

```powershell
$s = New-PSSession (Get-Content Machines.txt)
$c = 'Get-EventLog -LogName System | where {$_.EntryType -eq "error" --and $_.Source -eq "LSASRV"} | Out-File Errors.txt'
Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {$Using:c}
Invoke-Command -Session $s -ScriptBlock {Wait-Job -Any}
```

<span data-ttu-id="a17a9-144">I det här exemplet används **valfri** parameter för `Wait-Job` för att fastställa när den första av många jobb som körs i den aktuella sessionen är i ett tillstånd där det avslutas.</span><span class="sxs-lookup"><span data-stu-id="a17a9-144">This example uses the **Any** parameter of `Wait-Job` to determine when the first of many jobs running in the current session are in a terminating state.</span></span> <span data-ttu-id="a17a9-145">Det visar också hur du använder `Wait-Job` cmdleten för att vänta på att fjärrjobben ska slutföras.</span><span class="sxs-lookup"><span data-stu-id="a17a9-145">It also shows how to use the `Wait-Job` cmdlet to wait for remote jobs to finish.</span></span>

<span data-ttu-id="a17a9-146">Det första kommandot skapar en **PSSession** på varje dator som anges i Machines.txt-filen och lagrar **PSSession** -objekt i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="a17a9-146">The first command creates a **PSSession** on each of the computers listed in the Machines.txt file and stores the **PSSession** objects in the `$s` variable.</span></span> <span data-ttu-id="a17a9-147">Kommandot använder `Get-Content` cmdleten för att hämta innehållet i filen.</span><span class="sxs-lookup"><span data-stu-id="a17a9-147">The command uses the `Get-Content` cmdlet to get the contents of the file.</span></span> <span data-ttu-id="a17a9-148">`Get-Content`Kommandot omges av parenteser för att kontrol lera att det körs före `New-PSSession` kommandot.</span><span class="sxs-lookup"><span data-stu-id="a17a9-148">The `Get-Content` command is enclosed in parentheses to make sure that it runs before the `New-PSSession` command.</span></span>

<span data-ttu-id="a17a9-149">Det andra kommandot lagrar en `Get-EventLog` kommando sträng, inom citat tecken, i `$c` variabeln.</span><span class="sxs-lookup"><span data-stu-id="a17a9-149">The second command stores a `Get-EventLog` command string, in quotation marks, in the `$c` variable.</span></span>

<span data-ttu-id="a17a9-150">Det tredje kommandot använder `Invoke-Command` cmdlet för att köras `Start-Job` i varje session i `$s` .</span><span class="sxs-lookup"><span data-stu-id="a17a9-150">The third command uses `Invoke-Command` cmdlet to run `Start-Job` in each of the sessions in `$s`.</span></span>
<span data-ttu-id="a17a9-151">`Start-Job`Kommandot startar ett jobb som kör `Get-EventLog` kommandot i `$c` variabeln.</span><span class="sxs-lookup"><span data-stu-id="a17a9-151">The `Start-Job` command starts a job that runs the `Get-EventLog` command in the `$c` variable.</span></span>

<span data-ttu-id="a17a9-152">Kommandot **använder omfångs** modifieraren för att indikera att `$c` variabeln har definierats på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="a17a9-152">The command uses the **Using** scope modifier to indicate that the `$c` variable was defined on the local computer.</span></span> <span data-ttu-id="a17a9-153">Omfångs modifieraren **använder** introduceras i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a17a9-153">The **Using** scope modifier is introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="a17a9-154">Mer information om hur du **använder** omfångs modifieraren finns [about_Remote_Variables](./about/about_Remote_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="a17a9-154">For more information about the **Using** scope modifier, see [about_Remote_Variables](./about/about_Remote_Variables.md).</span></span>

<span data-ttu-id="a17a9-155">Det fjärde kommandot använder `Invoke-Command` för att köra ett `Wait-Job` kommando i sessionerna.</span><span class="sxs-lookup"><span data-stu-id="a17a9-155">The fourth command uses `Invoke-Command` to run a `Wait-Job` command in the sessions.</span></span> <span data-ttu-id="a17a9-156">Den använder **valfri** parameter för att vänta tills det första jobbet på fjärrdatorerna avslutas.</span><span class="sxs-lookup"><span data-stu-id="a17a9-156">It uses the **Any** parameter to wait until the first job on the remote computers is terminating state.</span></span>

### <span data-ttu-id="a17a9-157">Exempel 4: Ange en vänte tid för jobb på fjärrdatorer</span><span class="sxs-lookup"><span data-stu-id="a17a9-157">Example 4: Set a wait time for jobs on remote computers</span></span>

```powershell
PS> $s = New-PSSession Server01, Server02, Server03
PS> $jobs = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {Get-Date}}
PS> $done = Invoke-Command -Session $s -ScriptBlock {Wait-Job -Timeout 30}
PS>
```

<span data-ttu-id="a17a9-158">Det här exemplet visar hur du använder **timeout** -parametern för `Wait-Job` för att ange en maximal vänte tid för de jobb som körs på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="a17a9-158">This example shows how to use the **Timeout** parameter of `Wait-Job` to set a maximum wait time for the jobs running on remote computers.</span></span>

<span data-ttu-id="a17a9-159">Det första kommandot skapar en **PSSession** på var och en av de tre fjärrdatorerna (Server01, Server02 och Server03) och lagrar sedan **PSSession** -objekten i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="a17a9-159">The first command creates a **PSSession** on each of three remote computers (Server01, Server02, and Server03), and then stores the **PSSession** objects in the `$s` variable.</span></span>

<span data-ttu-id="a17a9-160">Det andra kommandot använder `Invoke-Command` för att köras `Start-Job` i varje **PSSession** -objekt i `$s` .</span><span class="sxs-lookup"><span data-stu-id="a17a9-160">The second command uses `Invoke-Command` to run `Start-Job` in each of the **PSSession** objects in `$s`.</span></span> <span data-ttu-id="a17a9-161">Den lagrar de resulterande jobb objekten i `$jobs` variabeln.</span><span class="sxs-lookup"><span data-stu-id="a17a9-161">It stores the resulting job objects in the `$jobs` variable.</span></span>

<span data-ttu-id="a17a9-162">Det tredje kommandot använder `Invoke-Command` för att köras `Wait-Job` i varje session i `$s` .</span><span class="sxs-lookup"><span data-stu-id="a17a9-162">The third command uses `Invoke-Command` to run `Wait-Job` in each of the sessions in `$s`.</span></span> <span data-ttu-id="a17a9-163">`Wait-Job`Kommandot avgör om alla kommandon har slutförts inom 30 sekunder.</span><span class="sxs-lookup"><span data-stu-id="a17a9-163">The `Wait-Job` command determines whether all of the commands have completed within 30 seconds.</span></span> <span data-ttu-id="a17a9-164">Parametern **timeout** används med ett värde på 30 för att fastställa den maximala vänte tiden och lagrar sedan resultatet av kommandot i `$done` variabeln.</span><span class="sxs-lookup"><span data-stu-id="a17a9-164">It uses the **Timeout** parameter with a value of 30 to establish the maximum wait time, and then stores the results of the command in the `$done` variable.</span></span>

<span data-ttu-id="a17a9-165">I det här fallet är det bara kommandot på Server02-datorn som har slutförts efter 30 sekunder.</span><span class="sxs-lookup"><span data-stu-id="a17a9-165">In this case, after 30 seconds, only the command on the Server02 computer has completed.</span></span> <span data-ttu-id="a17a9-166">`Wait-Job` avslutar väntan, returnerar objektet som representerar jobbet som slutförts och visar kommando tolken.</span><span class="sxs-lookup"><span data-stu-id="a17a9-166">`Wait-Job` ends the wait, returns the object that represents the job that was completed, and displays the command prompt.</span></span>

<span data-ttu-id="a17a9-167">`$done`Variabeln innehåller ett jobb objekt som representerar jobbet som kördes på Server02.</span><span class="sxs-lookup"><span data-stu-id="a17a9-167">The `$done` variable contains a job object that represents the job that ran on Server02.</span></span>

### <span data-ttu-id="a17a9-168">Exempel 5: vänta tills ett av flera jobb har slutförts</span><span class="sxs-lookup"><span data-stu-id="a17a9-168">Example 5: Wait until one of several jobs finishes</span></span>

```powershell
Wait-Job -id 1,2,5 -Any
```

<span data-ttu-id="a17a9-169">Det här kommandot identifierar tre jobb efter deras ID och väntar tills någon av dem är i ett avslutande tillstånd.</span><span class="sxs-lookup"><span data-stu-id="a17a9-169">This command identifies three jobs by their IDs and waits until any one of them are in a terminating state.</span></span> <span data-ttu-id="a17a9-170">Körningen fortsätter när det första jobbet är klart.</span><span class="sxs-lookup"><span data-stu-id="a17a9-170">Execution continues when the first job finishes.</span></span>

### <span data-ttu-id="a17a9-171">Exempel 6: vänta i en period och Tillåt sedan att jobbet fortsätter i bakgrunden</span><span class="sxs-lookup"><span data-stu-id="a17a9-171">Example 6: Wait for a period, then allow job to continue in background</span></span>

```powershell
Wait-Job -Name "DailyLog" -Timeout 120
```

<span data-ttu-id="a17a9-172">Det här kommandot väntar 120 sekunder (två minuter) för att DailyLog-jobbet ska slutföras.</span><span class="sxs-lookup"><span data-stu-id="a17a9-172">This command waits 120 seconds (two minutes) for the DailyLog job to finish.</span></span> <span data-ttu-id="a17a9-173">Om jobbet inte slutförs under de kommande två minuterna fortsätter körningen och jobbet fortsätter att köras i bakgrunden.</span><span class="sxs-lookup"><span data-stu-id="a17a9-173">If the job does not finish in the next two minutes, execution continues, and the job continues to run in the background.</span></span>

### <span data-ttu-id="a17a9-174">Exempel 7: vänta på ett jobb efter namn</span><span class="sxs-lookup"><span data-stu-id="a17a9-174">Example 7: Wait for a job by name</span></span>

```powershell
Wait-Job -Name "Job3"
```

<span data-ttu-id="a17a9-175">Det här kommandot använder jobb namnet för att identifiera det jobb som ska vänta.</span><span class="sxs-lookup"><span data-stu-id="a17a9-175">This command uses the job name to identify the job for which to wait.</span></span>

### <span data-ttu-id="a17a9-176">Exempel 8: vänta tills jobb på den lokala datorn har startats med Start-Job</span><span class="sxs-lookup"><span data-stu-id="a17a9-176">Example 8: Wait for jobs on local computer started with Start-Job</span></span>

```powershell
$j = Start-Job -ScriptBlock {Get-ChildItem *.ps1| where {$_.lastwritetime -gt ((Get-Date) - (New-TimeSpan -Days 7))}}
$j | Wait-Job
```

<span data-ttu-id="a17a9-177">Det här exemplet visar hur du använder `Wait-Job` cmdleten med jobb som har startats på den lokala datorn med hjälp av `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="a17a9-177">This example shows how to use the `Wait-Job` cmdlet with jobs started on the local computer by using `Start-Job`.</span></span>

<span data-ttu-id="a17a9-178">Kommandona startar ett jobb som hämtar Windows PowerShell-skriptfilerna som har lagts till eller uppdaterats under den senaste veckan.</span><span class="sxs-lookup"><span data-stu-id="a17a9-178">These commands start a job that gets the Windows PowerShell script files that were added or updated in the last week.</span></span>

<span data-ttu-id="a17a9-179">Det första kommandot använder `Start-Job` för att starta ett jobb på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="a17a9-179">The first command uses `Start-Job` to start a job on the local computer.</span></span> <span data-ttu-id="a17a9-180">Jobbet kör ett `Get-ChildItem` kommando som hämtar alla filer som har fil namns tillägget. ps1 som har lagts till eller uppdaterats under den senaste veckan.</span><span class="sxs-lookup"><span data-stu-id="a17a9-180">The job runs a `Get-ChildItem` command that gets all of the files that have a .ps1 file name extension that were added or updated in the last week.</span></span>

<span data-ttu-id="a17a9-181">Det tredje kommandot använder `Wait-Job` för att vänta tills jobbet är i ett avslutande tillstånd.</span><span class="sxs-lookup"><span data-stu-id="a17a9-181">The third command uses `Wait-Job` to wait until the job is in a terminating state.</span></span> <span data-ttu-id="a17a9-182">När jobbet har slutförts visar kommandot jobbobjektet som innehåller information om jobbet.</span><span class="sxs-lookup"><span data-stu-id="a17a9-182">When the job finishes, the command displays the job object, which contains information about the job.</span></span>

### <span data-ttu-id="a17a9-183">Exempel 9: vänta tills jobben har startats på fjärrdatorer genom att använda Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="a17a9-183">Example 9: Wait for jobs started on remote computers by using Invoke-Command</span></span>

```powershell
$s = New-PSSession Server01, Server02, Server03
$j = Invoke-Command -Session $s -ScriptBlock {Get-Process} -AsJob
$j | Wait-Job
```

<span data-ttu-id="a17a9-184">Det här exemplet visar hur du använder `Wait-Job` med jobb som har startats på fjärrdatorer med hjälp av parametern **AsJob** i `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="a17a9-184">This example shows how to use `Wait-Job` with jobs started on remote computers by using the **AsJob** parameter of `Invoke-Command`.</span></span> <span data-ttu-id="a17a9-185">När du använder **AsJob** skapas jobbet på den lokala datorn och resultaten returneras automatiskt till den lokala datorn, även om jobbet körs på fjärrdatorerna.</span><span class="sxs-lookup"><span data-stu-id="a17a9-185">When using **AsJob**, the job is created on the local computer and the results are automatically returned to the local computer, even though the job runs on the remote computers.</span></span>

<span data-ttu-id="a17a9-186">I det här exemplet används `Wait-Job` för att avgöra om ett `Get-Process` kommando som körs i sessioner på tre fjärrdatorer är i ett avslutande tillstånd.</span><span class="sxs-lookup"><span data-stu-id="a17a9-186">This example uses `Wait-Job` to determine whether a `Get-Process` command running in the sessions on three remote computers is in a terminating state.</span></span>

<span data-ttu-id="a17a9-187">Det första kommandot skapar **PSSession** -objekt på tre datorer och lagrar dem i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="a17a9-187">The first command creates **PSSession** objects on three computers and stores them in the `$s` variable.</span></span>

<span data-ttu-id="a17a9-188">Det andra kommandot använder `Invoke-Command` för att köra `Get-Process` i var och en av de tre sessionerna i `$s` .</span><span class="sxs-lookup"><span data-stu-id="a17a9-188">The second command uses `Invoke-Command` to run `Get-Process` in each of the three sessions in `$s`.</span></span>
<span data-ttu-id="a17a9-189">Kommandot använder parametern **AsJob** för att köra kommandot asynkront som ett jobb.</span><span class="sxs-lookup"><span data-stu-id="a17a9-189">The command uses the **AsJob** parameter to run the command asynchronously as a job.</span></span> <span data-ttu-id="a17a9-190">Kommandot returnerar ett jobb objekt, precis som de jobb som har startats med hjälp av `Start-Job` , och jobbobjektet lagras i `$j` variabeln.</span><span class="sxs-lookup"><span data-stu-id="a17a9-190">The command returns a job object, just like the jobs started by using `Start-Job`, and the job object is stored in the `$j` variable.</span></span>

<span data-ttu-id="a17a9-191">Det tredje kommandot använder en pipeline-operator ( `|` ) för att skicka jobbobjektet till- `$j` `Wait-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a17a9-191">The third command uses a pipeline operator (`|`) to send the job object in `$j` to the `Wait-Job` cmdlet.</span></span> <span data-ttu-id="a17a9-192">Ett `Invoke-Command` kommando krävs inte i det här fallet eftersom jobbet finns på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="a17a9-192">An `Invoke-Command` command is not required in this case, because the job resides on the local computer.</span></span>

### <span data-ttu-id="a17a9-193">Exempel 10: vänta på ett jobb som har ett ID</span><span class="sxs-lookup"><span data-stu-id="a17a9-193">Example 10: Wait for a job that has an ID</span></span>

```powershell
Get-Job
```

```Output
Id   Name     State      HasMoreData     Location             Command
--   ----     -----      -----------     --------             -------
1    Job1     Completed  True            localhost,Server01.. get-service
4    Job4     Completed  True            localhost            dir | where
```

```powershell
Wait-Job -Id 1
```

<span data-ttu-id="a17a9-194">Det här kommandot väntar på jobbet med ID-värdet 1.</span><span class="sxs-lookup"><span data-stu-id="a17a9-194">This command waits for the job with an ID value of 1.</span></span>

## <span data-ttu-id="a17a9-195">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="a17a9-195">PARAMETERS</span></span>

### <span data-ttu-id="a17a9-196">– Alla</span><span class="sxs-lookup"><span data-stu-id="a17a9-196">-Any</span></span>

<span data-ttu-id="a17a9-197">Anger att denna cmdlet returnerar jobbobjektet och fortsätter körningen när ett jobb har slutförts.</span><span class="sxs-lookup"><span data-stu-id="a17a9-197">Indicates that this cmdlet returns the job object and continues execution when any job finishes.</span></span> <span data-ttu-id="a17a9-198">Som standard `Wait-Job` väntar det tills alla angivna jobb har slutförts innan meddelandet visas.</span><span class="sxs-lookup"><span data-stu-id="a17a9-198">By default, `Wait-Job` waits until all of the specified jobs are complete before it displays the prompt.</span></span>

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

### <span data-ttu-id="a17a9-199">-Filter</span><span class="sxs-lookup"><span data-stu-id="a17a9-199">-Filter</span></span>

<span data-ttu-id="a17a9-200">Anger en hash-tabell med villkor.</span><span class="sxs-lookup"><span data-stu-id="a17a9-200">Specifies a hash table of conditions.</span></span> <span data-ttu-id="a17a9-201">Denna cmdlet väntar på jobb som uppfyller alla villkor i hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="a17a9-201">This cmdlet waits for jobs that satisfy all of the conditions in the hash table.</span></span> <span data-ttu-id="a17a9-202">Ange en hash-tabell där nycklarna är jobb egenskaper och värdena är jobb egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="a17a9-202">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="a17a9-203">Den här parametern fungerar bara på anpassade jobb typer, till exempel arbets flödes jobb och schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="a17a9-203">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span> <span data-ttu-id="a17a9-204">Den fungerar inte på standard jobb, till exempel de som skapats med hjälp av `Start-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a17a9-204">It does not work on standard jobs, such as those created by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="a17a9-205">Information om stöd för den här parametern finns i hjälp avsnittet för jobb typen.</span><span class="sxs-lookup"><span data-stu-id="a17a9-205">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="a17a9-206">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a17a9-206">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="a17a9-207">-Force</span><span class="sxs-lookup"><span data-stu-id="a17a9-207">-Force</span></span>

<span data-ttu-id="a17a9-208">Anger att denna cmdlet fortsätter att vänta på jobb i tillståndet pausad eller frånkopplad.</span><span class="sxs-lookup"><span data-stu-id="a17a9-208">Indicates that this cmdlet continues to wait for jobs in the Suspended or Disconnected state.</span></span> <span data-ttu-id="a17a9-209">Som standard `Wait-Job` returnerar eller avslutar vänte läge när jobben är i något av följande tillstånd:</span><span class="sxs-lookup"><span data-stu-id="a17a9-209">By default, `Wait-Job` returns, or ends the wait, when jobs are in one of the following states:</span></span>

- <span data-ttu-id="a17a9-210">Slutförd</span><span class="sxs-lookup"><span data-stu-id="a17a9-210">Completed</span></span>
- <span data-ttu-id="a17a9-211">Misslyckad</span><span class="sxs-lookup"><span data-stu-id="a17a9-211">Failed</span></span>
- <span data-ttu-id="a17a9-212">Stoppad</span><span class="sxs-lookup"><span data-stu-id="a17a9-212">Stopped</span></span>
- <span data-ttu-id="a17a9-213">Inaktiverad</span><span class="sxs-lookup"><span data-stu-id="a17a9-213">Suspended</span></span>
- <span data-ttu-id="a17a9-214">Frånkopplad</span><span class="sxs-lookup"><span data-stu-id="a17a9-214">Disconnected</span></span>

<span data-ttu-id="a17a9-215">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="a17a9-215">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="a17a9-216">-ID</span><span class="sxs-lookup"><span data-stu-id="a17a9-216">-Id</span></span>

<span data-ttu-id="a17a9-217">Anger en matris med ID: n för jobb som denna cmdlet väntar på.</span><span class="sxs-lookup"><span data-stu-id="a17a9-217">Specifies an array of IDs of jobs for which this cmdlet waits.</span></span>

<span data-ttu-id="a17a9-218">ID är ett heltal som unikt identifierar jobbet i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="a17a9-218">The ID is an integer that uniquely identifies the job in the current session.</span></span> <span data-ttu-id="a17a9-219">Det är enklare att komma ihåg och skriva än instans-ID, men det är endast unikt i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="a17a9-219">It is easier to remember and type than the instance ID, but it is unique only in the current session.</span></span> <span data-ttu-id="a17a9-220">Du kan ange ett eller flera ID: n, avgränsade med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="a17a9-220">You can type one or more IDs, separated by commas.</span></span> <span data-ttu-id="a17a9-221">Om du vill hitta ID: t för ett jobb skriver du `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="a17a9-221">To find the ID of a job, type `Get-Job`.</span></span>

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

### <span data-ttu-id="a17a9-222">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="a17a9-222">-InstanceId</span></span>

<span data-ttu-id="a17a9-223">Anger en matris med instans-ID: n för jobb som denna cmdlet väntar på.</span><span class="sxs-lookup"><span data-stu-id="a17a9-223">Specifies an array of instance IDs of jobs for which this cmdlet waits.</span></span> <span data-ttu-id="a17a9-224">Standardvärdet är alla jobb.</span><span class="sxs-lookup"><span data-stu-id="a17a9-224">The default is all jobs.</span></span>

<span data-ttu-id="a17a9-225">Ett instans-ID är ett GUID som unikt identifierar jobbet på datorn.</span><span class="sxs-lookup"><span data-stu-id="a17a9-225">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span> <span data-ttu-id="a17a9-226">Använd om du vill hitta instans-ID: t för ett jobb `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="a17a9-226">To find the instance ID of a job, use `Get-Job`.</span></span>

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

### <span data-ttu-id="a17a9-227">– Jobb</span><span class="sxs-lookup"><span data-stu-id="a17a9-227">-Job</span></span>

<span data-ttu-id="a17a9-228">Anger jobb för vilka denna cmdlet väntar.</span><span class="sxs-lookup"><span data-stu-id="a17a9-228">Specifies the jobs for which this cmdlet waits.</span></span> <span data-ttu-id="a17a9-229">Ange en variabel som innehåller jobb objekt eller ett kommando som hämtar jobb objekt.</span><span class="sxs-lookup"><span data-stu-id="a17a9-229">Enter a variable that contains the job objects or a command that gets the job objects.</span></span> <span data-ttu-id="a17a9-230">Du kan också använda en pipeline-operator för att skicka jobb objekt till- `Wait-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="a17a9-230">You can also use a pipeline operator to send job objects to the `Wait-Job` cmdlet.</span></span> <span data-ttu-id="a17a9-231">Som standard `Wait-Job` väntar alla jobb som skapats i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="a17a9-231">By default, `Wait-Job` waits for all jobs created in the current session.</span></span>

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

### <span data-ttu-id="a17a9-232">-Name</span><span class="sxs-lookup"><span data-stu-id="a17a9-232">-Name</span></span>

<span data-ttu-id="a17a9-233">Anger egna namn på jobb som denna cmdlet väntar på.</span><span class="sxs-lookup"><span data-stu-id="a17a9-233">Specifies friendly names of jobs for which this cmdlet waits.</span></span>

```yaml
Type: System.String[]
Parameter Sets: NameParameterSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a17a9-234">– Tillstånd</span><span class="sxs-lookup"><span data-stu-id="a17a9-234">-State</span></span>

<span data-ttu-id="a17a9-235">Anger ett jobb tillstånd.</span><span class="sxs-lookup"><span data-stu-id="a17a9-235">Specifies a job state.</span></span> <span data-ttu-id="a17a9-236">Denna cmdlet väntar bara på jobb i det angivna läget.</span><span class="sxs-lookup"><span data-stu-id="a17a9-236">This cmdlet waits only for jobs in the specified state.</span></span> <span data-ttu-id="a17a9-237">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="a17a9-237">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="a17a9-238">NotStarted</span><span class="sxs-lookup"><span data-stu-id="a17a9-238">NotStarted</span></span>
- <span data-ttu-id="a17a9-239">Körs</span><span class="sxs-lookup"><span data-stu-id="a17a9-239">Running</span></span>
- <span data-ttu-id="a17a9-240">Slutförd</span><span class="sxs-lookup"><span data-stu-id="a17a9-240">Completed</span></span>
- <span data-ttu-id="a17a9-241">Misslyckad</span><span class="sxs-lookup"><span data-stu-id="a17a9-241">Failed</span></span>
- <span data-ttu-id="a17a9-242">Stoppad</span><span class="sxs-lookup"><span data-stu-id="a17a9-242">Stopped</span></span>
- <span data-ttu-id="a17a9-243">Blockerad</span><span class="sxs-lookup"><span data-stu-id="a17a9-243">Blocked</span></span>
- <span data-ttu-id="a17a9-244">Inaktiverad</span><span class="sxs-lookup"><span data-stu-id="a17a9-244">Suspended</span></span>
- <span data-ttu-id="a17a9-245">Frånkopplad</span><span class="sxs-lookup"><span data-stu-id="a17a9-245">Disconnected</span></span>
- <span data-ttu-id="a17a9-246">Pausar</span><span class="sxs-lookup"><span data-stu-id="a17a9-246">Suspending</span></span>
- <span data-ttu-id="a17a9-247">Stoppas</span><span class="sxs-lookup"><span data-stu-id="a17a9-247">Stopping</span></span>

<span data-ttu-id="a17a9-248">Mer information om jobb tillstånd finns i [JobState-uppräkning](/dotnet/api/system.management.automation.jobstate).</span><span class="sxs-lookup"><span data-stu-id="a17a9-248">For more information about job states, see [JobState Enumeration](/dotnet/api/system.management.automation.jobstate).</span></span>

```yaml
Type: System.Management.Automation.JobState
Parameter Sets: StateParameterSet
Aliases:
Accepted values: NotStarted, Running, Completed, Failed, Stopped, Blocked, Suspended, Disconnected, Suspending, Stopping, AtBreakpoint

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### <span data-ttu-id="a17a9-249">-Timeout</span><span class="sxs-lookup"><span data-stu-id="a17a9-249">-Timeout</span></span>

<span data-ttu-id="a17a9-250">Anger maximal vänte tid för varje jobb, i sekunder.</span><span class="sxs-lookup"><span data-stu-id="a17a9-250">Specifies the maximum wait time for each job, in seconds.</span></span> <span data-ttu-id="a17a9-251">Standardvärdet,-1, anger att cmdleten ska vänta tills jobbet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="a17a9-251">The default value, -1, indicates that the cmdlet waits until the job finishes.</span></span> <span data-ttu-id="a17a9-252">Tids inställningen startar när du skickar `Wait-Job` kommandot, inte `Start-Job` kommandot.</span><span class="sxs-lookup"><span data-stu-id="a17a9-252">The timing starts when you submit the `Wait-Job` command, not the `Start-Job` command.</span></span>

<span data-ttu-id="a17a9-253">Om den här tiden överskrids fortsätter vänte tiden och körningen även om jobbet fortfarande körs.</span><span class="sxs-lookup"><span data-stu-id="a17a9-253">If this time is exceeded, the wait ends and execution continues, even if the job is still running.</span></span>
<span data-ttu-id="a17a9-254">Kommandot visar inga fel meddelanden.</span><span class="sxs-lookup"><span data-stu-id="a17a9-254">The command does not display any error message.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutSec

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="a17a9-255">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="a17a9-255">CommonParameters</span></span>

<span data-ttu-id="a17a9-256">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="a17a9-256">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="a17a9-257">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="a17a9-257">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="a17a9-258">INDATA</span><span class="sxs-lookup"><span data-stu-id="a17a9-258">INPUTS</span></span>

### <span data-ttu-id="a17a9-259">System. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="a17a9-259">System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="a17a9-260">Du kan skicka vidare ett jobb objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a17a9-260">You can pipe a job object to this cmdlet.</span></span>

## <span data-ttu-id="a17a9-261">UTDATA</span><span class="sxs-lookup"><span data-stu-id="a17a9-261">OUTPUTS</span></span>

### <span data-ttu-id="a17a9-262">System. Management. Automation. PSRemotingJob</span><span class="sxs-lookup"><span data-stu-id="a17a9-262">System.Management.Automation.PSRemotingJob</span></span>

<span data-ttu-id="a17a9-263">Denna cmdlet returnerar jobb objekt som representerar jobben i ett avslutande tillstånd.</span><span class="sxs-lookup"><span data-stu-id="a17a9-263">This cmdlet returns job objects that represent the jobs in a terminating state.</span></span> <span data-ttu-id="a17a9-264">Om vänte tiden slutar eftersom värdet för parametern **timeout** överskrids, `Wait-Job` returnerar inga objekt.</span><span class="sxs-lookup"><span data-stu-id="a17a9-264">If the wait ends because the value of the **Timeout** parameter is exceeded, `Wait-Job` does not return any objects.</span></span>

## <span data-ttu-id="a17a9-265">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="a17a9-265">NOTES</span></span>

<span data-ttu-id="a17a9-266">Som standard `Wait-Job` returnerar eller avslutar vänte läge när jobben är i något av följande tillstånd:</span><span class="sxs-lookup"><span data-stu-id="a17a9-266">By default, `Wait-Job` returns, or ends the wait, when jobs are in one of the following states:</span></span>

- <span data-ttu-id="a17a9-267">Slutförd</span><span class="sxs-lookup"><span data-stu-id="a17a9-267">Completed</span></span>
- <span data-ttu-id="a17a9-268">Misslyckad</span><span class="sxs-lookup"><span data-stu-id="a17a9-268">Failed</span></span>
- <span data-ttu-id="a17a9-269">Stoppad</span><span class="sxs-lookup"><span data-stu-id="a17a9-269">Stopped</span></span>
- <span data-ttu-id="a17a9-270">Inaktiverad</span><span class="sxs-lookup"><span data-stu-id="a17a9-270">Suspended</span></span>
- <span data-ttu-id="a17a9-271">Frånkopplad till direkt om du vill `Wait-Job` fortsätta att vänta på pausade och frånkopplade jobb använder du parametern **Force** .</span><span class="sxs-lookup"><span data-stu-id="a17a9-271">Disconnected To direct `Wait-Job` to continue to wait for Suspended and Disconnected jobs, use the **Force** parameter.</span></span>

## <span data-ttu-id="a17a9-272">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="a17a9-272">RELATED LINKS</span></span>

[<span data-ttu-id="a17a9-273">Hämta jobb</span><span class="sxs-lookup"><span data-stu-id="a17a9-273">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="a17a9-274">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="a17a9-274">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="a17a9-275">Mottagning – jobb</span><span class="sxs-lookup"><span data-stu-id="a17a9-275">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="a17a9-276">Ta bort – jobb</span><span class="sxs-lookup"><span data-stu-id="a17a9-276">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="a17a9-277">Start – jobb</span><span class="sxs-lookup"><span data-stu-id="a17a9-277">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="a17a9-278">Stoppa – jobb</span><span class="sxs-lookup"><span data-stu-id="a17a9-278">Stop-Job</span></span>](Stop-Job.md)
