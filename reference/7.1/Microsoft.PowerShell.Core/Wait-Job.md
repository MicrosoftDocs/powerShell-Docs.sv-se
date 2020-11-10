---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/wait-job?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Job
ms.openlocfilehash: 560202531a992b9db8ba5d5ebc957f96750f1feb
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94389257"
---
# <span data-ttu-id="6a128-103">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="6a128-103">Wait-Job</span></span>

## <span data-ttu-id="6a128-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="6a128-104">SYNOPSIS</span></span>
<span data-ttu-id="6a128-105">Ignorerar kommando tolken tills en eller flera av PowerShell-bakgrunds jobben som körs i sessionen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="6a128-105">Suppresses the command prompt until one or all of the PowerShell background jobs running in the session are completed.</span></span>

## <span data-ttu-id="6a128-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="6a128-106">SYNTAX</span></span>

### <span data-ttu-id="6a128-107">SessionIdParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="6a128-107">SessionIdParameterSet (Default)</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Id] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="6a128-108">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="6a128-108">JobParameterSet</span></span>

```
Wait-Job [-Job] <Job[]> [-Any] [-Timeout <Int32>] [-Force] [<CommonParameters>]
```

### <span data-ttu-id="6a128-109">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="6a128-109">NameParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="6a128-110">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="6a128-110">InstanceIdParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="6a128-111">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="6a128-111">StateParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-State] <JobState> [<CommonParameters>]
```

### <span data-ttu-id="6a128-112">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="6a128-112">FilterParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Filter] <Hashtable> [<CommonParameters>]
```

## <span data-ttu-id="6a128-113">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="6a128-113">DESCRIPTION</span></span>

<span data-ttu-id="6a128-114">`Wait-Job`Cmdleten väntar på att PowerShell-arbetsjobben ska avslutas innan kommando tolken visas.</span><span class="sxs-lookup"><span data-stu-id="6a128-114">The `Wait-Job` cmdlet waits for PowerShell background jobs to finish before it displays the command prompt.</span></span> <span data-ttu-id="6a128-115">Du kan vänta tills ett bakgrunds jobb har slutförts, eller tills alla bakgrunds jobb är slutförda, och du kan ange en maximal vänte tid för jobbet.</span><span class="sxs-lookup"><span data-stu-id="6a128-115">You can wait until any background job is complete, or until all background jobs are complete, and you can set a maximum wait time for the job.</span></span>

<span data-ttu-id="6a128-116">När kommandona i jobbet har slutförts, `Wait-Job` visar kommando tolken och returnerar ett Job-objekt så att du kan skicka tillbaka det till ett annat kommando.</span><span class="sxs-lookup"><span data-stu-id="6a128-116">When the commands in the job are complete, `Wait-Job` displays the command prompt and returns a job object so that you can pipe it to another command.</span></span>

<span data-ttu-id="6a128-117">Du kan använda `Wait-Job` cmdleten för att vänta på bakgrunds jobb, till exempel de som startades med hjälp av `Start-Job` cmdleten eller parametern **AsJob** för `Invoke-Command` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6a128-117">You can use `Wait-Job` cmdlet to wait for background jobs, such as those that were started by using the `Start-Job` cmdlet or the **AsJob** parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="6a128-118">Mer information om bakgrunds jobb i Windows PowerShell finns [about_Jobs](./about/about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="6a128-118">For more information about Windows PowerShell background jobs, see [about_Jobs](./about/about_Jobs.md).</span></span>

<span data-ttu-id="6a128-119">Från och med Windows PowerShell 3,0 `Wait-Job` väntar cmdleten även på anpassade jobb typer, till exempel arbets flödes jobb och instanser av schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="6a128-119">Starting in Windows PowerShell 3.0, the `Wait-Job` cmdlet also waits for custom job types, such as workflow jobs and instances of scheduled jobs.</span></span> <span data-ttu-id="6a128-120">Om du vill kunna `Wait-Job` vänta på jobb av en viss typ importerar du modulen som stöder den anpassade jobb typen till sessionen innan du kör `Get-Job` cmdleten, antingen med hjälp av `Import-Module` cmdleten eller genom att använda eller hämta en cmdlet i modulen.</span><span class="sxs-lookup"><span data-stu-id="6a128-120">To enable `Wait-Job` to wait for jobs of a particular type, import the module that supports the custom job type into the session before you run the `Get-Job` cmdlet, either by using the `Import-Module` cmdlet or by using or getting a cmdlet in the module.</span></span> <span data-ttu-id="6a128-121">Information om en viss anpassad Jobbtyp finns i dokumentationen för den anpassade jobb typ funktionen.</span><span class="sxs-lookup"><span data-stu-id="6a128-121">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="6a128-122">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="6a128-122">EXAMPLES</span></span>

### <span data-ttu-id="6a128-123">Exempel 1: vänta på alla jobb</span><span class="sxs-lookup"><span data-stu-id="6a128-123">Example 1: Wait for all jobs</span></span>

```powershell
Get-Job | Wait-Job
```

<span data-ttu-id="6a128-124">Det här kommandot väntar på att alla bakgrunds jobb som körs i sessionen ska slutföras.</span><span class="sxs-lookup"><span data-stu-id="6a128-124">This command waits for all of the background jobs running in the session to finish.</span></span>

### <span data-ttu-id="6a128-125">Exempel 2: vänta tills jobben har startats på fjärrdatorer med hjälp av Start-Job</span><span class="sxs-lookup"><span data-stu-id="6a128-125">Example 2: Wait for jobs started on remote computers by using Start-Job</span></span>

```powershell
$s = New-PSSession Server01, Server02, Server03
Invoke-Command -Session $s -ScriptBlock {Start-Job -Name Date1 -ScriptBlock {Get-Date}}
$done = Invoke-Command -Session $s -Command {Wait-Job -Name Date1}
$done.Count
```

```Output
3
```

<span data-ttu-id="6a128-126">Det här exemplet visar hur du använder `Wait-Job` cmdleten med jobb som har startats på fjärrdatorer med hjälp av `Start-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6a128-126">This example shows how to use the `Wait-Job` cmdlet with jobs started on remote computers by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="6a128-127">Både- `Start-Job` och- `Wait-Job` kommandon skickas till fjärrdatorn med hjälp av `Invoke-Command` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6a128-127">Both `Start-Job` and `Wait-Job` commands are submitted to the remote computer by using the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="6a128-128">I det här exemplet används `Wait-Job` för att avgöra om ett `Get-Date` kommando som körs som ett bakgrunds jobb på tre olika datorer är klart.</span><span class="sxs-lookup"><span data-stu-id="6a128-128">This example uses `Wait-Job` to determine whether a `Get-Date` command running as a background job on three different computers is finished.</span></span>

<span data-ttu-id="6a128-129">Det första kommandot skapar en Windows PowerShell-session ( **PSSession** ) på var och en av de tre fjärrdatorerna och lagrar dem i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="6a128-129">The first command creates a Windows PowerShell session ( **PSSession** ) on each of the three remote computers and stores them in the `$s` variable.</span></span>

<span data-ttu-id="6a128-130">Det andra kommandot använder `Invoke-Command` för att köra `Start-Job` i var och en av de tre sessionerna i `$s` .</span><span class="sxs-lookup"><span data-stu-id="6a128-130">The second command uses `Invoke-Command` to run `Start-Job` in each of the three sessions in `$s`.</span></span>
<span data-ttu-id="6a128-131">Alla jobb har namnet datum1.</span><span class="sxs-lookup"><span data-stu-id="6a128-131">All of the jobs are named Date1.</span></span>

<span data-ttu-id="6a128-132">Det tredje kommandot använder `Invoke-Command` för att köra `Wait-Job` .</span><span class="sxs-lookup"><span data-stu-id="6a128-132">The third command uses `Invoke-Command` to run `Wait-Job`.</span></span> <span data-ttu-id="6a128-133">Det här kommandot väntar på att datum1-jobben på varje dator ska slutföras.</span><span class="sxs-lookup"><span data-stu-id="6a128-133">This command waits for the Date1 jobs on each computer to finish.</span></span> <span data-ttu-id="6a128-134">Den innehåller den resulterande samlingen (matris) för jobb objekt i `$done` variabeln.</span><span class="sxs-lookup"><span data-stu-id="6a128-134">It stores the resulting collection (array) of job objects in the `$done` variable.</span></span>

<span data-ttu-id="6a128-135">Det fjärde kommandot använder egenskapen **Count** i matrisen med jobb objekt i `$done` variabeln för att fastställa hur många av jobben som är klara.</span><span class="sxs-lookup"><span data-stu-id="6a128-135">The fourth command uses the **Count** property of the array of job objects in the `$done` variable to determine how many of the jobs are finished.</span></span>

### <span data-ttu-id="6a128-136">Exempel 3: Bestäm när det första bakgrunds jobbet slutförs</span><span class="sxs-lookup"><span data-stu-id="6a128-136">Example 3: Determine when the first background job finishes</span></span>

```powershell
$s = New-PSSession (Get-Content Machines.txt)
$c = 'Get-EventLog -LogName System | where {$_.EntryType -eq "error" --and $_.Source -eq "LSASRV"} | Out-File Errors.txt'
Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {$Using:c}
Invoke-Command -Session $s -ScriptBlock {Wait-Job -Any}
```

<span data-ttu-id="6a128-137">I det här exemplet används **valfri** parameter för `Wait-Job` för att fastställa när den första av många bakgrunds jobb som körs i den aktuella sessionen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="6a128-137">This example uses the **Any** parameter of `Wait-Job` to determine when the first of many background jobs running in the current session are completed.</span></span> <span data-ttu-id="6a128-138">Det visar också hur du använder `Wait-Job` cmdleten för att vänta på att fjärrjobben ska slutföras.</span><span class="sxs-lookup"><span data-stu-id="6a128-138">It also shows how to use the `Wait-Job` cmdlet to wait for remote jobs to finish.</span></span>

<span data-ttu-id="6a128-139">Det första kommandot skapar en **PSSession** på varje dator som anges i Machines.txt-filen och lagrar **PSSession** -objekt i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="6a128-139">The first command creates a **PSSession** on each of the computers listed in the Machines.txt file and stores the **PSSession** objects in the `$s` variable.</span></span> <span data-ttu-id="6a128-140">Kommandot använder `Get-Content` cmdleten för att hämta innehållet i filen.</span><span class="sxs-lookup"><span data-stu-id="6a128-140">The command uses the `Get-Content` cmdlet to get the contents of the file.</span></span> <span data-ttu-id="6a128-141">`Get-Content`Kommandot omges av parenteser för att kontrol lera att det körs före `New-PSSession` kommandot.</span><span class="sxs-lookup"><span data-stu-id="6a128-141">The `Get-Content` command is enclosed in parentheses to make sure that it runs before the `New-PSSession` command.</span></span>

<span data-ttu-id="6a128-142">Det andra kommandot lagrar en `Get-EventLog` kommando sträng, inom citat tecken, i `$c` variabeln.</span><span class="sxs-lookup"><span data-stu-id="6a128-142">The second command stores a `Get-EventLog` command string, in quotation marks, in the `$c` variable.</span></span>

<span data-ttu-id="6a128-143">Det tredje kommandot använder `Invoke-Command` cmdlet för att köras `Start-Job` i varje session i `$s` .</span><span class="sxs-lookup"><span data-stu-id="6a128-143">The third command uses `Invoke-Command` cmdlet to run `Start-Job` in each of the sessions in `$s`.</span></span>
<span data-ttu-id="6a128-144">`Start-Job`Kommandot startar ett bakgrunds jobb som kör `Get-EventLog` kommandot i `$c` variabeln.</span><span class="sxs-lookup"><span data-stu-id="6a128-144">The `Start-Job` command starts a background job that runs the `Get-EventLog` command in the `$c` variable.</span></span>

<span data-ttu-id="6a128-145">Kommandot **använder omfångs** modifieraren för att indikera att `$c` variabeln har definierats på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="6a128-145">The command uses the **Using** scope modifier to indicate that the `$c` variable was defined on the local computer.</span></span> <span data-ttu-id="6a128-146">Omfångs modifieraren **använder** introduceras i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6a128-146">The **Using** scope modifier is introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="6a128-147">Mer information om hur du **använder** omfångs modifieraren finns [about_Remote_Variables](./about/about_Remote_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="6a128-147">For more information about the **Using** scope modifier, see [about_Remote_Variables](./about/about_Remote_Variables.md).</span></span>

<span data-ttu-id="6a128-148">Det fjärde kommandot använder `Invoke-Command` för att köra ett `Wait-Job` kommando i sessionerna.</span><span class="sxs-lookup"><span data-stu-id="6a128-148">The fourth command uses `Invoke-Command` to run a `Wait-Job` command in the sessions.</span></span> <span data-ttu-id="6a128-149">Den använder **valfri** parameter för att vänta tills det första jobbet på fjärrdatorerna har slutförts.</span><span class="sxs-lookup"><span data-stu-id="6a128-149">It uses the **Any** parameter to wait until the first job on the remote computers is completed.</span></span>

### <span data-ttu-id="6a128-150">Exempel 4: Ange en vänte tid för jobb på fjärrdatorer</span><span class="sxs-lookup"><span data-stu-id="6a128-150">Example 4: Set a wait time for jobs on remote computers</span></span>

```powershell
$s = New-PSSession Server01, Server02, Server03
$jobs = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {Get-Date}}
$done = Invoke-Command -Session $s -ScriptBlock {Wait-Job -Timeout 30}
```

<span data-ttu-id="6a128-151">Det här exemplet visar hur du använder **timeout** -parametern för `Wait-Job` för att ange en maximal vänte tid för de jobb som körs på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="6a128-151">This example shows how to use the **Timeout** parameter of `Wait-Job` to set a maximum wait time for the jobs running on remote computers.</span></span>

<span data-ttu-id="6a128-152">Det första kommandot skapar en **PSSession** på var och en av de tre fjärrdatorerna (Server01, Server02 och Server03) och lagrar sedan **PSSession** -objekten i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="6a128-152">The first command creates a **PSSession** on each of three remote computers (Server01, Server02, and Server03), and then stores the **PSSession** objects in the `$s` variable.</span></span>

<span data-ttu-id="6a128-153">Det andra kommandot använder `Invoke-Command` för att köras `Start-Job` i varje **PSSession** -objekt i `$s` .</span><span class="sxs-lookup"><span data-stu-id="6a128-153">The second command uses `Invoke-Command` to run `Start-Job` in each of the **PSSession** objects in `$s`.</span></span> <span data-ttu-id="6a128-154">Den lagrar de resulterande jobb objekten i `$jobs` variabeln.</span><span class="sxs-lookup"><span data-stu-id="6a128-154">It stores the resulting job objects in the `$jobs` variable.</span></span>

<span data-ttu-id="6a128-155">Det tredje kommandot använder `Invoke-Command` för att köras `Wait-Job` i varje session i `$s` .</span><span class="sxs-lookup"><span data-stu-id="6a128-155">The third command uses `Invoke-Command` to run `Wait-Job` in each of the sessions in `$s`.</span></span> <span data-ttu-id="6a128-156">`Wait-Job`Kommandot avgör om alla kommandon har slutförts inom 30 sekunder.</span><span class="sxs-lookup"><span data-stu-id="6a128-156">The `Wait-Job` command determines whether all of the commands have completed within 30 seconds.</span></span> <span data-ttu-id="6a128-157">Parametern **timeout** används med ett värde på 30 för att fastställa den maximala vänte tiden och lagrar sedan resultatet av kommandot i `$done` variabeln.</span><span class="sxs-lookup"><span data-stu-id="6a128-157">It uses the **Timeout** parameter with a value of 30 to establish the maximum wait time, and then stores the results of the command in the `$done` variable.</span></span>

<span data-ttu-id="6a128-158">I det här fallet är det bara kommandot på Server02-datorn som har slutförts efter 30 sekunder.</span><span class="sxs-lookup"><span data-stu-id="6a128-158">In this case, after 30 seconds, only the command on the Server02 computer has completed.</span></span> <span data-ttu-id="6a128-159">`Wait-Job` avslutar väntan, visar kommando tolken och returnerar det objekt som representerar det jobb som har slutförts.</span><span class="sxs-lookup"><span data-stu-id="6a128-159">`Wait-Job` ends the wait, displays the command prompt, and returns the object that represents the job that was completed.</span></span>

<span data-ttu-id="6a128-160">`$done`Variabeln innehåller ett jobb objekt som representerar jobbet som kördes på Server02.</span><span class="sxs-lookup"><span data-stu-id="6a128-160">The `$done` variable contains a job object that represents the job that ran on Server02.</span></span>

### <span data-ttu-id="6a128-161">Exempel 5: vänta tills ett av flera jobb har slutförts</span><span class="sxs-lookup"><span data-stu-id="6a128-161">Example 5: Wait until one of several jobs finishes</span></span>

```powershell
Wait-Job -id 1,2,5 -Any
```

<span data-ttu-id="6a128-162">Detta kommando identifierar tre jobb efter deras ID och väntar tills någon av dem har slutförts.</span><span class="sxs-lookup"><span data-stu-id="6a128-162">This command identifies three jobs by their IDs and waits until any one of them are completed.</span></span>
<span data-ttu-id="6a128-163">Kommando tolken returnerar när det första jobbet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="6a128-163">The command prompt returns when the first job finishes.</span></span>

### <span data-ttu-id="6a128-164">Exempel 6: vänta i en period och Tillåt sedan att jobbet fortsätter i bakgrunden</span><span class="sxs-lookup"><span data-stu-id="6a128-164">Example 6: Wait for a period, then allow job to continue in background</span></span>

```powershell
Wait-Job -Name "DailyLog" -Timeout 120
```

<span data-ttu-id="6a128-165">Det här kommandot väntar 120 sekunder (två minuter) för att DailyLog-jobbet ska slutföras.</span><span class="sxs-lookup"><span data-stu-id="6a128-165">This command waits 120 seconds (two minutes) for the DailyLog job to finish.</span></span> <span data-ttu-id="6a128-166">Om jobbet inte slutförs inom de kommande två minuterna returnerar kommando tolken ändå och jobbet fortsätter att köras i bakgrunden.</span><span class="sxs-lookup"><span data-stu-id="6a128-166">If the job does not finish in the next two minutes, the command prompt returns anyway, and the job continues to run in the background.</span></span>

### <span data-ttu-id="6a128-167">Exempel 7: vänta på ett jobb efter namn</span><span class="sxs-lookup"><span data-stu-id="6a128-167">Example 7: Wait for a job by name</span></span>

```powershell
Wait-Job -Name "Job3"
```

<span data-ttu-id="6a128-168">Det här kommandot använder jobb namnet för att identifiera det jobb som ska vänta.</span><span class="sxs-lookup"><span data-stu-id="6a128-168">This command uses the job name to identify the job for which to wait.</span></span>

### <span data-ttu-id="6a128-169">Exempel 8: vänta tills jobb på den lokala datorn har startats med Start-Job</span><span class="sxs-lookup"><span data-stu-id="6a128-169">Example 8: Wait for jobs on local computer started with Start-Job</span></span>

```powershell
$j = Start-Job -ScriptBlock {Get-ChildItem *.ps1| where {$_lastwritetime -gt ((Get-Date) - (New-TimeSpan -Days 7))}}
$j | Wait-Job
```

<span data-ttu-id="6a128-170">Det här exemplet visar hur du använder `Wait-Job` cmdleten med jobb som har startats på den lokala datorn med hjälp av `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="6a128-170">This example shows how to use the `Wait-Job` cmdlet with jobs started on the local computer by using `Start-Job`.</span></span>

<span data-ttu-id="6a128-171">Kommandona startar ett jobb som hämtar Windows PowerShell-skriptfilerna som har lagts till eller uppdaterats under den senaste veckan.</span><span class="sxs-lookup"><span data-stu-id="6a128-171">These commands start a job that gets the Windows PowerShell script files that were added or updated in the last week.</span></span>

<span data-ttu-id="6a128-172">Det första kommandot använder `Start-Job` för att starta ett bakgrunds jobb på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="6a128-172">The first command uses `Start-Job` to start a background job on the local computer.</span></span> <span data-ttu-id="6a128-173">Jobbet kör ett `Get-ChildItem` kommando som hämtar alla filer som har fil namns tillägget. ps1 som har lagts till eller uppdaterats under den senaste veckan.</span><span class="sxs-lookup"><span data-stu-id="6a128-173">The job runs a `Get-ChildItem` command that gets all of the files that have a .ps1 file name extension that were added or updated in the last week.</span></span>

<span data-ttu-id="6a128-174">Det tredje kommandot använder `Wait-Job` för att vänta tills jobbet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="6a128-174">The third command uses `Wait-Job` to wait until the job is completed.</span></span> <span data-ttu-id="6a128-175">När jobbet har slutförts visar kommandot jobbobjektet som innehåller information om jobbet.</span><span class="sxs-lookup"><span data-stu-id="6a128-175">When the job finishes, the command displays the job object, which contains information about the job.</span></span>

### <span data-ttu-id="6a128-176">Exempel 9: vänta tills jobben har startats på fjärrdatorer genom att använda Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="6a128-176">Example 9: Wait for jobs started on remote computers by using Invoke-Command</span></span>

```powershell
$s = New-PSSession Server01, Server02, Server03
$j = Invoke-Command -Session $s -ScriptBlock {Get-Process} -AsJob
$j | Wait-Job
```

<span data-ttu-id="6a128-177">Det här exemplet visar hur du använder `Wait-Job` med jobb som har startats på fjärrdatorer med hjälp av parametern **AsJob** i `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="6a128-177">This example shows how to use `Wait-Job` with jobs started on remote computers by using the **AsJob** parameter of `Invoke-Command`.</span></span> <span data-ttu-id="6a128-178">När du använder **AsJob** skapas jobbet på den lokala datorn och resultaten returneras automatiskt till den lokala datorn, även om jobbet körs på fjärrdatorerna.</span><span class="sxs-lookup"><span data-stu-id="6a128-178">When using **AsJob** , the job is created on the local computer and the results are automatically returned to the local computer, even though the job runs on the remote computers.</span></span>

<span data-ttu-id="6a128-179">I det här exemplet används `Wait-Job` för att avgöra om ett `Get-Process` kommando som körs i sessioner på tre fjärrdatorer har slutförts.</span><span class="sxs-lookup"><span data-stu-id="6a128-179">This example uses `Wait-Job` to determine whether a `Get-Process` command running in the sessions on three remote computers is completed.</span></span>

<span data-ttu-id="6a128-180">Det första kommandot skapar **PSSession** -objekt på tre datorer och lagrar dem i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="6a128-180">The first command creates **PSSession** objects on three computers and stores them in the `$s` variable.</span></span>

<span data-ttu-id="6a128-181">Det andra kommandot använder `Invoke-Command` för att köra `Get-Process` i var och en av de tre sessionerna i `$s` .</span><span class="sxs-lookup"><span data-stu-id="6a128-181">The second command uses `Invoke-Command` to run `Get-Process` in each of the three sessions in `$s`.</span></span>
<span data-ttu-id="6a128-182">Kommandot använder parametern **AsJob** för att köra kommandot asynkront som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="6a128-182">The command uses the **AsJob** parameter to run the command asynchronously as a background job.</span></span> <span data-ttu-id="6a128-183">Kommandot returnerar ett jobb objekt, precis som de jobb som har startats med hjälp av `Start-Job` , och jobbobjektet lagras i `$j` variabeln.</span><span class="sxs-lookup"><span data-stu-id="6a128-183">The command returns a job object, just like the jobs started by using `Start-Job`, and the job object is stored in the `$j` variable.</span></span>

<span data-ttu-id="6a128-184">Det tredje kommandot använder en pipeline-operator ( `|` ) för att skicka jobbobjektet till- `$j` `Wait-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6a128-184">The third command uses a pipeline operator (`|`) to send the job object in `$j` to the `Wait-Job` cmdlet.</span></span> <span data-ttu-id="6a128-185">Ett `Invoke-Command` kommando krävs inte i det här fallet eftersom jobbet finns på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="6a128-185">An `Invoke-Command` command is not required in this case, because the job resides on the local computer.</span></span>

### <span data-ttu-id="6a128-186">Exempel 10: vänta på ett jobb som har ett ID</span><span class="sxs-lookup"><span data-stu-id="6a128-186">Example 10: Wait for a job that has an ID</span></span>

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

<span data-ttu-id="6a128-187">Det här kommandot väntar på jobbet med ID-värdet 1.</span><span class="sxs-lookup"><span data-stu-id="6a128-187">This command waits for the job with an ID value of 1.</span></span>

## <span data-ttu-id="6a128-188">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="6a128-188">PARAMETERS</span></span>

### <span data-ttu-id="6a128-189">– Alla</span><span class="sxs-lookup"><span data-stu-id="6a128-189">-Any</span></span>

<span data-ttu-id="6a128-190">Anger att denna cmdlet visar kommando tolken och returnerar jobbobjektet när ett jobb har slutförts.</span><span class="sxs-lookup"><span data-stu-id="6a128-190">Indicates that this cmdlet displays the command prompt, and returns the job object, when any job finishes.</span></span> <span data-ttu-id="6a128-191">Som standard `Wait-Job` väntar det tills alla angivna jobb har slutförts innan meddelandet visas.</span><span class="sxs-lookup"><span data-stu-id="6a128-191">By default, `Wait-Job` waits until all of the specified jobs are complete before it displays the prompt.</span></span>

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

### <span data-ttu-id="6a128-192">-Filter</span><span class="sxs-lookup"><span data-stu-id="6a128-192">-Filter</span></span>

<span data-ttu-id="6a128-193">Anger en hash-tabell med villkor.</span><span class="sxs-lookup"><span data-stu-id="6a128-193">Specifies a hash table of conditions.</span></span> <span data-ttu-id="6a128-194">Denna cmdlet väntar på jobb som uppfyller alla villkor i hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="6a128-194">This cmdlet waits for jobs that satisfy all of the conditions in the hash table.</span></span> <span data-ttu-id="6a128-195">Ange en hash-tabell där nycklarna är jobb egenskaper och värdena är jobb egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="6a128-195">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="6a128-196">Den här parametern fungerar bara på anpassade jobb typer, till exempel arbets flödes jobb och schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="6a128-196">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span> <span data-ttu-id="6a128-197">Den fungerar inte på vanliga bakgrunds jobb, till exempel de som skapats med hjälp av `Start-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6a128-197">It does not work on standard background jobs, such as those created by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="6a128-198">Information om stöd för den här parametern finns i hjälp avsnittet för jobb typen.</span><span class="sxs-lookup"><span data-stu-id="6a128-198">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="6a128-199">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6a128-199">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="6a128-200">-Force</span><span class="sxs-lookup"><span data-stu-id="6a128-200">-Force</span></span>

<span data-ttu-id="6a128-201">Anger att denna cmdlet fortsätter att vänta på jobb i tillståndet pausad eller frånkopplad.</span><span class="sxs-lookup"><span data-stu-id="6a128-201">Indicates that this cmdlet continues to wait for jobs in the Suspended or Disconnected state.</span></span> <span data-ttu-id="6a128-202">Som standard `Wait-Job` returnerar eller avslutar vänte läge när jobben är i något av följande tillstånd:</span><span class="sxs-lookup"><span data-stu-id="6a128-202">By default, `Wait-Job` returns, or ends the wait, when jobs are in one of the following states:</span></span>

- <span data-ttu-id="6a128-203">Slutförd</span><span class="sxs-lookup"><span data-stu-id="6a128-203">Completed</span></span>
- <span data-ttu-id="6a128-204">Misslyckad</span><span class="sxs-lookup"><span data-stu-id="6a128-204">Failed</span></span>
- <span data-ttu-id="6a128-205">Stoppad</span><span class="sxs-lookup"><span data-stu-id="6a128-205">Stopped</span></span>
- <span data-ttu-id="6a128-206">Inaktiverad</span><span class="sxs-lookup"><span data-stu-id="6a128-206">Suspended</span></span>
- <span data-ttu-id="6a128-207">Frånkopplad</span><span class="sxs-lookup"><span data-stu-id="6a128-207">Disconnected</span></span>

<span data-ttu-id="6a128-208">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="6a128-208">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="6a128-209">-ID</span><span class="sxs-lookup"><span data-stu-id="6a128-209">-Id</span></span>

<span data-ttu-id="6a128-210">Anger en matris med ID: n för jobb som denna cmdlet väntar på.</span><span class="sxs-lookup"><span data-stu-id="6a128-210">Specifies an array of IDs of jobs for which this cmdlet waits.</span></span>

<span data-ttu-id="6a128-211">ID är ett heltal som unikt identifierar jobbet i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="6a128-211">The ID is an integer that uniquely identifies the job in the current session.</span></span> <span data-ttu-id="6a128-212">Det är enklare att komma ihåg och skriva än instans-ID, men det är endast unikt i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="6a128-212">It is easier to remember and type than the instance ID, but it is unique only in the current session.</span></span> <span data-ttu-id="6a128-213">Du kan ange ett eller flera ID: n, avgränsade med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="6a128-213">You can type one or more IDs, separated by commas.</span></span> <span data-ttu-id="6a128-214">Om du vill hitta ID: t för ett jobb skriver du `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="6a128-214">To find the ID of a job, type `Get-Job`.</span></span>

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

### <span data-ttu-id="6a128-215">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="6a128-215">-InstanceId</span></span>

<span data-ttu-id="6a128-216">Anger en matris med instans-ID: n för jobb som denna cmdlet väntar på.</span><span class="sxs-lookup"><span data-stu-id="6a128-216">Specifies an array of instance IDs of jobs for which this cmdlet waits.</span></span> <span data-ttu-id="6a128-217">Standardvärdet är alla jobb.</span><span class="sxs-lookup"><span data-stu-id="6a128-217">The default is all jobs.</span></span>

<span data-ttu-id="6a128-218">Ett instans-ID är ett GUID som unikt identifierar jobbet på datorn.</span><span class="sxs-lookup"><span data-stu-id="6a128-218">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span> <span data-ttu-id="6a128-219">Använd om du vill hitta instans-ID: t för ett jobb `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="6a128-219">To find the instance ID of a job, use `Get-Job`.</span></span>

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

### <span data-ttu-id="6a128-220">– Jobb</span><span class="sxs-lookup"><span data-stu-id="6a128-220">-Job</span></span>

<span data-ttu-id="6a128-221">Anger jobb för vilka denna cmdlet väntar.</span><span class="sxs-lookup"><span data-stu-id="6a128-221">Specifies the jobs for which this cmdlet waits.</span></span> <span data-ttu-id="6a128-222">Ange en variabel som innehåller jobb objekt eller ett kommando som hämtar jobb objekt.</span><span class="sxs-lookup"><span data-stu-id="6a128-222">Enter a variable that contains the job objects or a command that gets the job objects.</span></span> <span data-ttu-id="6a128-223">Du kan också använda en pipeline-operator för att skicka jobb objekt till- `Wait-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="6a128-223">You can also use a pipeline operator to send job objects to the `Wait-Job` cmdlet.</span></span> <span data-ttu-id="6a128-224">Som standard `Wait-Job` väntar alla jobb som skapats i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="6a128-224">By default, `Wait-Job` waits for all jobs created in the current session.</span></span>

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

### <span data-ttu-id="6a128-225">-Name</span><span class="sxs-lookup"><span data-stu-id="6a128-225">-Name</span></span>

<span data-ttu-id="6a128-226">Anger egna namn på jobb som denna cmdlet väntar på.</span><span class="sxs-lookup"><span data-stu-id="6a128-226">Specifies friendly names of jobs for which this cmdlet waits.</span></span>

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

### <span data-ttu-id="6a128-227">– Tillstånd</span><span class="sxs-lookup"><span data-stu-id="6a128-227">-State</span></span>

<span data-ttu-id="6a128-228">Anger ett jobb tillstånd.</span><span class="sxs-lookup"><span data-stu-id="6a128-228">Specifies a job state.</span></span> <span data-ttu-id="6a128-229">Denna cmdlet väntar bara på jobb i det angivna läget.</span><span class="sxs-lookup"><span data-stu-id="6a128-229">This cmdlet waits only for jobs in the specified state.</span></span> <span data-ttu-id="6a128-230">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="6a128-230">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="6a128-231">NotStarted</span><span class="sxs-lookup"><span data-stu-id="6a128-231">NotStarted</span></span>
- <span data-ttu-id="6a128-232">Körs</span><span class="sxs-lookup"><span data-stu-id="6a128-232">Running</span></span>
- <span data-ttu-id="6a128-233">Slutförd</span><span class="sxs-lookup"><span data-stu-id="6a128-233">Completed</span></span>
- <span data-ttu-id="6a128-234">Misslyckad</span><span class="sxs-lookup"><span data-stu-id="6a128-234">Failed</span></span>
- <span data-ttu-id="6a128-235">Stoppad</span><span class="sxs-lookup"><span data-stu-id="6a128-235">Stopped</span></span>
- <span data-ttu-id="6a128-236">Blockerad</span><span class="sxs-lookup"><span data-stu-id="6a128-236">Blocked</span></span>
- <span data-ttu-id="6a128-237">Inaktiverad</span><span class="sxs-lookup"><span data-stu-id="6a128-237">Suspended</span></span>
- <span data-ttu-id="6a128-238">Frånkopplad</span><span class="sxs-lookup"><span data-stu-id="6a128-238">Disconnected</span></span>
- <span data-ttu-id="6a128-239">Pausar</span><span class="sxs-lookup"><span data-stu-id="6a128-239">Suspending</span></span>
- <span data-ttu-id="6a128-240">Stoppas</span><span class="sxs-lookup"><span data-stu-id="6a128-240">Stopping</span></span>

<span data-ttu-id="6a128-241">Mer information om jobb tillstånd finns i [JobState-uppräkning](/dotnet/api/system.management.automation.jobstate).</span><span class="sxs-lookup"><span data-stu-id="6a128-241">For more information about job states, see [JobState Enumeration](/dotnet/api/system.management.automation.jobstate).</span></span>

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

### <span data-ttu-id="6a128-242">-Timeout</span><span class="sxs-lookup"><span data-stu-id="6a128-242">-Timeout</span></span>

<span data-ttu-id="6a128-243">Anger maximal vänte tid för varje bakgrunds jobb, i sekunder.</span><span class="sxs-lookup"><span data-stu-id="6a128-243">Specifies the maximum wait time for each background job, in seconds.</span></span> <span data-ttu-id="6a128-244">Standardvärdet,-1, anger att cmdleten ska vänta tills jobbet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="6a128-244">The default value, -1, indicates that the cmdlet waits until the job finishes.</span></span> <span data-ttu-id="6a128-245">Tids inställningen startar när du skickar `Wait-Job` kommandot, inte `Start-Job` kommandot.</span><span class="sxs-lookup"><span data-stu-id="6a128-245">The timing starts when you submit the `Wait-Job` command, not the `Start-Job` command.</span></span>

<span data-ttu-id="6a128-246">Om den här tiden överskrids, avslutas vänte tiden och kommando tolken returnerar, även om jobbet fortfarande körs.</span><span class="sxs-lookup"><span data-stu-id="6a128-246">If this time is exceeded, the wait ends and the command prompt returns, even if the job is still running.</span></span> <span data-ttu-id="6a128-247">Kommandot visar inga fel meddelanden.</span><span class="sxs-lookup"><span data-stu-id="6a128-247">The command does not display any error message.</span></span>

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

### <span data-ttu-id="6a128-248">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="6a128-248">CommonParameters</span></span>

<span data-ttu-id="6a128-249">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="6a128-249">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="6a128-250">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="6a128-250">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="6a128-251">INDATA</span><span class="sxs-lookup"><span data-stu-id="6a128-251">INPUTS</span></span>

### <span data-ttu-id="6a128-252">System. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="6a128-252">System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="6a128-253">Du kan skicka vidare ett jobb objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6a128-253">You can pipe a job object to this cmdlet.</span></span>

## <span data-ttu-id="6a128-254">UTDATA</span><span class="sxs-lookup"><span data-stu-id="6a128-254">OUTPUTS</span></span>

### <span data-ttu-id="6a128-255">System. Management. Automation. PSRemotingJob</span><span class="sxs-lookup"><span data-stu-id="6a128-255">System.Management.Automation.PSRemotingJob</span></span>

<span data-ttu-id="6a128-256">Denna cmdlet returnerar jobb objekt som representerar de slutförda jobben.</span><span class="sxs-lookup"><span data-stu-id="6a128-256">This cmdlet returns job objects that represent the completed jobs.</span></span> <span data-ttu-id="6a128-257">Om vänte tiden slutar eftersom värdet för parametern **timeout** överskrids, `Wait-Job` returnerar inga objekt.</span><span class="sxs-lookup"><span data-stu-id="6a128-257">If the wait ends because the value of the **Timeout** parameter is exceeded, `Wait-Job` does not return any objects.</span></span>

## <span data-ttu-id="6a128-258">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="6a128-258">NOTES</span></span>

<span data-ttu-id="6a128-259">Som standard `Wait-Job` returnerar eller avslutar vänte läge när jobben är i något av följande tillstånd:</span><span class="sxs-lookup"><span data-stu-id="6a128-259">By default, `Wait-Job` returns, or ends the wait, when jobs are in one of the following states:</span></span>

- <span data-ttu-id="6a128-260">Slutförd</span><span class="sxs-lookup"><span data-stu-id="6a128-260">Completed</span></span>
- <span data-ttu-id="6a128-261">Misslyckad</span><span class="sxs-lookup"><span data-stu-id="6a128-261">Failed</span></span>
- <span data-ttu-id="6a128-262">Stoppad</span><span class="sxs-lookup"><span data-stu-id="6a128-262">Stopped</span></span>
- <span data-ttu-id="6a128-263">Inaktiverad</span><span class="sxs-lookup"><span data-stu-id="6a128-263">Suspended</span></span>
- <span data-ttu-id="6a128-264">Frånkopplad till direkt om du vill `Wait-Job` fortsätta att vänta på pausade och frånkopplade jobb använder du parametern **Force** .</span><span class="sxs-lookup"><span data-stu-id="6a128-264">Disconnected To direct `Wait-Job` to continue to wait for Suspended and Disconnected jobs, use the **Force** parameter.</span></span>

## <span data-ttu-id="6a128-265">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="6a128-265">RELATED LINKS</span></span>

[<span data-ttu-id="6a128-266">Hämta jobb</span><span class="sxs-lookup"><span data-stu-id="6a128-266">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="6a128-267">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="6a128-267">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="6a128-268">Mottagning – jobb</span><span class="sxs-lookup"><span data-stu-id="6a128-268">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="6a128-269">Ta bort – jobb</span><span class="sxs-lookup"><span data-stu-id="6a128-269">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="6a128-270">Start – jobb</span><span class="sxs-lookup"><span data-stu-id="6a128-270">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="6a128-271">Stoppa – jobb</span><span class="sxs-lookup"><span data-stu-id="6a128-271">Stop-Job</span></span>](Stop-Job.md)
