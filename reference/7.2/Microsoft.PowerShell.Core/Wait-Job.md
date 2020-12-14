---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/wait-job?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Wait-Job
ms.openlocfilehash: 9517305860f0c9c38865885dc681aba82f843ed1
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708784"
---
# <span data-ttu-id="40888-102">Wait-Job</span><span class="sxs-lookup"><span data-stu-id="40888-102">Wait-Job</span></span>

## <span data-ttu-id="40888-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="40888-103">SYNOPSIS</span></span>
<span data-ttu-id="40888-104">Ignorerar kommando tolken tills en eller flera av PowerShell-bakgrunds jobben som körs i sessionen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="40888-104">Suppresses the command prompt until one or all of the PowerShell background jobs running in the session are completed.</span></span>

## <span data-ttu-id="40888-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="40888-105">SYNTAX</span></span>

### <span data-ttu-id="40888-106">SessionIdParameterSet (standard)</span><span class="sxs-lookup"><span data-stu-id="40888-106">SessionIdParameterSet (Default)</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Id] <Int32[]> [<CommonParameters>]
```

### <span data-ttu-id="40888-107">JobParameterSet</span><span class="sxs-lookup"><span data-stu-id="40888-107">JobParameterSet</span></span>

```
Wait-Job [-Job] <Job[]> [-Any] [-Timeout <Int32>] [-Force] [<CommonParameters>]
```

### <span data-ttu-id="40888-108">NameParameterSet</span><span class="sxs-lookup"><span data-stu-id="40888-108">NameParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Name] <String[]> [<CommonParameters>]
```

### <span data-ttu-id="40888-109">InstanceIdParameterSet</span><span class="sxs-lookup"><span data-stu-id="40888-109">InstanceIdParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-InstanceId] <Guid[]> [<CommonParameters>]
```

### <span data-ttu-id="40888-110">StateParameterSet</span><span class="sxs-lookup"><span data-stu-id="40888-110">StateParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-State] <JobState> [<CommonParameters>]
```

### <span data-ttu-id="40888-111">FilterParameterSet</span><span class="sxs-lookup"><span data-stu-id="40888-111">FilterParameterSet</span></span>

```
Wait-Job [-Any] [-Timeout <Int32>] [-Force] [-Filter] <Hashtable> [<CommonParameters>]
```

## <span data-ttu-id="40888-112">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="40888-112">DESCRIPTION</span></span>

<span data-ttu-id="40888-113">`Wait-Job`Cmdleten väntar på att PowerShell-arbetsjobben ska avslutas innan kommando tolken visas.</span><span class="sxs-lookup"><span data-stu-id="40888-113">The `Wait-Job` cmdlet waits for PowerShell background jobs to finish before it displays the command prompt.</span></span> <span data-ttu-id="40888-114">Du kan vänta tills ett bakgrunds jobb har slutförts, eller tills alla bakgrunds jobb är slutförda, och du kan ange en maximal vänte tid för jobbet.</span><span class="sxs-lookup"><span data-stu-id="40888-114">You can wait until any background job is complete, or until all background jobs are complete, and you can set a maximum wait time for the job.</span></span>

<span data-ttu-id="40888-115">När kommandona i jobbet har slutförts, `Wait-Job` visar kommando tolken och returnerar ett Job-objekt så att du kan skicka tillbaka det till ett annat kommando.</span><span class="sxs-lookup"><span data-stu-id="40888-115">When the commands in the job are complete, `Wait-Job` displays the command prompt and returns a job object so that you can pipe it to another command.</span></span>

<span data-ttu-id="40888-116">Du kan använda `Wait-Job` cmdleten för att vänta på bakgrunds jobb, till exempel de som startades med hjälp av `Start-Job` cmdleten eller parametern **AsJob** för `Invoke-Command` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="40888-116">You can use `Wait-Job` cmdlet to wait for background jobs, such as those that were started by using the `Start-Job` cmdlet or the **AsJob** parameter of the `Invoke-Command` cmdlet.</span></span> <span data-ttu-id="40888-117">Mer information om bakgrunds jobb i Windows PowerShell finns [about_Jobs](./about/about_Jobs.md).</span><span class="sxs-lookup"><span data-stu-id="40888-117">For more information about Windows PowerShell background jobs, see [about_Jobs](./about/about_Jobs.md).</span></span>

<span data-ttu-id="40888-118">Från och med Windows PowerShell 3,0 `Wait-Job` väntar cmdleten även på anpassade jobb typer, till exempel arbets flödes jobb och instanser av schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="40888-118">Starting in Windows PowerShell 3.0, the `Wait-Job` cmdlet also waits for custom job types, such as workflow jobs and instances of scheduled jobs.</span></span> <span data-ttu-id="40888-119">Om du vill kunna `Wait-Job` vänta på jobb av en viss typ importerar du modulen som stöder den anpassade jobb typen till sessionen innan du kör `Get-Job` cmdleten, antingen med hjälp av `Import-Module` cmdleten eller genom att använda eller hämta en cmdlet i modulen.</span><span class="sxs-lookup"><span data-stu-id="40888-119">To enable `Wait-Job` to wait for jobs of a particular type, import the module that supports the custom job type into the session before you run the `Get-Job` cmdlet, either by using the `Import-Module` cmdlet or by using or getting a cmdlet in the module.</span></span> <span data-ttu-id="40888-120">Information om en viss anpassad Jobbtyp finns i dokumentationen för den anpassade jobb typ funktionen.</span><span class="sxs-lookup"><span data-stu-id="40888-120">For information about a particular custom job type, see the documentation of the custom job type feature.</span></span>

## <span data-ttu-id="40888-121">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="40888-121">EXAMPLES</span></span>

### <span data-ttu-id="40888-122">Exempel 1: vänta på alla jobb</span><span class="sxs-lookup"><span data-stu-id="40888-122">Example 1: Wait for all jobs</span></span>

```powershell
Get-Job | Wait-Job
```

<span data-ttu-id="40888-123">Det här kommandot väntar på att alla bakgrunds jobb som körs i sessionen ska slutföras.</span><span class="sxs-lookup"><span data-stu-id="40888-123">This command waits for all of the background jobs running in the session to finish.</span></span>

### <span data-ttu-id="40888-124">Exempel 2: vänta tills jobben har startats på fjärrdatorer med hjälp av Start-Job</span><span class="sxs-lookup"><span data-stu-id="40888-124">Example 2: Wait for jobs started on remote computers by using Start-Job</span></span>

```powershell
$s = New-PSSession Server01, Server02, Server03
Invoke-Command -Session $s -ScriptBlock {Start-Job -Name Date1 -ScriptBlock {Get-Date}}
$done = Invoke-Command -Session $s -Command {Wait-Job -Name Date1}
$done.Count
```

```Output
3
```

<span data-ttu-id="40888-125">Det här exemplet visar hur du använder `Wait-Job` cmdleten med jobb som har startats på fjärrdatorer med hjälp av `Start-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="40888-125">This example shows how to use the `Wait-Job` cmdlet with jobs started on remote computers by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="40888-126">Både- `Start-Job` och- `Wait-Job` kommandon skickas till fjärrdatorn med hjälp av `Invoke-Command` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="40888-126">Both `Start-Job` and `Wait-Job` commands are submitted to the remote computer by using the `Invoke-Command` cmdlet.</span></span>

<span data-ttu-id="40888-127">I det här exemplet används `Wait-Job` för att avgöra om ett `Get-Date` kommando som körs som ett bakgrunds jobb på tre olika datorer är klart.</span><span class="sxs-lookup"><span data-stu-id="40888-127">This example uses `Wait-Job` to determine whether a `Get-Date` command running as a background job on three different computers is finished.</span></span>

<span data-ttu-id="40888-128">Det första kommandot skapar en Windows PowerShell-session (**PSSession**) på var och en av de tre fjärrdatorerna och lagrar dem i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="40888-128">The first command creates a Windows PowerShell session (**PSSession**) on each of the three remote computers and stores them in the `$s` variable.</span></span>

<span data-ttu-id="40888-129">Det andra kommandot använder `Invoke-Command` för att köra `Start-Job` i var och en av de tre sessionerna i `$s` .</span><span class="sxs-lookup"><span data-stu-id="40888-129">The second command uses `Invoke-Command` to run `Start-Job` in each of the three sessions in `$s`.</span></span>
<span data-ttu-id="40888-130">Alla jobb har namnet datum1.</span><span class="sxs-lookup"><span data-stu-id="40888-130">All of the jobs are named Date1.</span></span>

<span data-ttu-id="40888-131">Det tredje kommandot använder `Invoke-Command` för att köra `Wait-Job` .</span><span class="sxs-lookup"><span data-stu-id="40888-131">The third command uses `Invoke-Command` to run `Wait-Job`.</span></span> <span data-ttu-id="40888-132">Det här kommandot väntar på att datum1-jobben på varje dator ska slutföras.</span><span class="sxs-lookup"><span data-stu-id="40888-132">This command waits for the Date1 jobs on each computer to finish.</span></span> <span data-ttu-id="40888-133">Den innehåller den resulterande samlingen (matris) för jobb objekt i `$done` variabeln.</span><span class="sxs-lookup"><span data-stu-id="40888-133">It stores the resulting collection (array) of job objects in the `$done` variable.</span></span>

<span data-ttu-id="40888-134">Det fjärde kommandot använder egenskapen **Count** i matrisen med jobb objekt i `$done` variabeln för att fastställa hur många av jobben som är klara.</span><span class="sxs-lookup"><span data-stu-id="40888-134">The fourth command uses the **Count** property of the array of job objects in the `$done` variable to determine how many of the jobs are finished.</span></span>

### <span data-ttu-id="40888-135">Exempel 3: Bestäm när det första bakgrunds jobbet slutförs</span><span class="sxs-lookup"><span data-stu-id="40888-135">Example 3: Determine when the first background job finishes</span></span>

```powershell
$s = New-PSSession (Get-Content Machines.txt)
$c = 'Get-EventLog -LogName System | where {$_.EntryType -eq "error" --and $_.Source -eq "LSASRV"} | Out-File Errors.txt'
Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {$Using:c}
Invoke-Command -Session $s -ScriptBlock {Wait-Job -Any}
```

<span data-ttu-id="40888-136">I det här exemplet används **valfri** parameter för `Wait-Job` för att fastställa när den första av många bakgrunds jobb som körs i den aktuella sessionen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="40888-136">This example uses the **Any** parameter of `Wait-Job` to determine when the first of many background jobs running in the current session are completed.</span></span> <span data-ttu-id="40888-137">Det visar också hur du använder `Wait-Job` cmdleten för att vänta på att fjärrjobben ska slutföras.</span><span class="sxs-lookup"><span data-stu-id="40888-137">It also shows how to use the `Wait-Job` cmdlet to wait for remote jobs to finish.</span></span>

<span data-ttu-id="40888-138">Det första kommandot skapar en **PSSession** på varje dator som anges i Machines.txt-filen och lagrar **PSSession** -objekt i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="40888-138">The first command creates a **PSSession** on each of the computers listed in the Machines.txt file and stores the **PSSession** objects in the `$s` variable.</span></span> <span data-ttu-id="40888-139">Kommandot använder `Get-Content` cmdleten för att hämta innehållet i filen.</span><span class="sxs-lookup"><span data-stu-id="40888-139">The command uses the `Get-Content` cmdlet to get the contents of the file.</span></span> <span data-ttu-id="40888-140">`Get-Content`Kommandot omges av parenteser för att kontrol lera att det körs före `New-PSSession` kommandot.</span><span class="sxs-lookup"><span data-stu-id="40888-140">The `Get-Content` command is enclosed in parentheses to make sure that it runs before the `New-PSSession` command.</span></span>

<span data-ttu-id="40888-141">Det andra kommandot lagrar en `Get-EventLog` kommando sträng, inom citat tecken, i `$c` variabeln.</span><span class="sxs-lookup"><span data-stu-id="40888-141">The second command stores a `Get-EventLog` command string, in quotation marks, in the `$c` variable.</span></span>

<span data-ttu-id="40888-142">Det tredje kommandot använder `Invoke-Command` cmdlet för att köras `Start-Job` i varje session i `$s` .</span><span class="sxs-lookup"><span data-stu-id="40888-142">The third command uses `Invoke-Command` cmdlet to run `Start-Job` in each of the sessions in `$s`.</span></span>
<span data-ttu-id="40888-143">`Start-Job`Kommandot startar ett bakgrunds jobb som kör `Get-EventLog` kommandot i `$c` variabeln.</span><span class="sxs-lookup"><span data-stu-id="40888-143">The `Start-Job` command starts a background job that runs the `Get-EventLog` command in the `$c` variable.</span></span>

<span data-ttu-id="40888-144">Kommandot **använder omfångs** modifieraren för att indikera att `$c` variabeln har definierats på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="40888-144">The command uses the **Using** scope modifier to indicate that the `$c` variable was defined on the local computer.</span></span> <span data-ttu-id="40888-145">Omfångs modifieraren **använder** introduceras i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="40888-145">The **Using** scope modifier is introduced in Windows PowerShell 3.0.</span></span> <span data-ttu-id="40888-146">Mer information om hur du **använder** omfångs modifieraren finns [about_Remote_Variables](./about/about_Remote_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="40888-146">For more information about the **Using** scope modifier, see [about_Remote_Variables](./about/about_Remote_Variables.md).</span></span>

<span data-ttu-id="40888-147">Det fjärde kommandot använder `Invoke-Command` för att köra ett `Wait-Job` kommando i sessionerna.</span><span class="sxs-lookup"><span data-stu-id="40888-147">The fourth command uses `Invoke-Command` to run a `Wait-Job` command in the sessions.</span></span> <span data-ttu-id="40888-148">Den använder **valfri** parameter för att vänta tills det första jobbet på fjärrdatorerna har slutförts.</span><span class="sxs-lookup"><span data-stu-id="40888-148">It uses the **Any** parameter to wait until the first job on the remote computers is completed.</span></span>

### <span data-ttu-id="40888-149">Exempel 4: Ange en vänte tid för jobb på fjärrdatorer</span><span class="sxs-lookup"><span data-stu-id="40888-149">Example 4: Set a wait time for jobs on remote computers</span></span>

```powershell
$s = New-PSSession Server01, Server02, Server03
$jobs = Invoke-Command -Session $s -ScriptBlock {Start-Job -ScriptBlock {Get-Date}}
$done = Invoke-Command -Session $s -ScriptBlock {Wait-Job -Timeout 30}
```

<span data-ttu-id="40888-150">Det här exemplet visar hur du använder **timeout** -parametern för `Wait-Job` för att ange en maximal vänte tid för de jobb som körs på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="40888-150">This example shows how to use the **Timeout** parameter of `Wait-Job` to set a maximum wait time for the jobs running on remote computers.</span></span>

<span data-ttu-id="40888-151">Det första kommandot skapar en **PSSession** på var och en av de tre fjärrdatorerna (Server01, Server02 och Server03) och lagrar sedan **PSSession** -objekten i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="40888-151">The first command creates a **PSSession** on each of three remote computers (Server01, Server02, and Server03), and then stores the **PSSession** objects in the `$s` variable.</span></span>

<span data-ttu-id="40888-152">Det andra kommandot använder `Invoke-Command` för att köras `Start-Job` i varje **PSSession** -objekt i `$s` .</span><span class="sxs-lookup"><span data-stu-id="40888-152">The second command uses `Invoke-Command` to run `Start-Job` in each of the **PSSession** objects in `$s`.</span></span> <span data-ttu-id="40888-153">Den lagrar de resulterande jobb objekten i `$jobs` variabeln.</span><span class="sxs-lookup"><span data-stu-id="40888-153">It stores the resulting job objects in the `$jobs` variable.</span></span>

<span data-ttu-id="40888-154">Det tredje kommandot använder `Invoke-Command` för att köras `Wait-Job` i varje session i `$s` .</span><span class="sxs-lookup"><span data-stu-id="40888-154">The third command uses `Invoke-Command` to run `Wait-Job` in each of the sessions in `$s`.</span></span> <span data-ttu-id="40888-155">`Wait-Job`Kommandot avgör om alla kommandon har slutförts inom 30 sekunder.</span><span class="sxs-lookup"><span data-stu-id="40888-155">The `Wait-Job` command determines whether all of the commands have completed within 30 seconds.</span></span> <span data-ttu-id="40888-156">Parametern **timeout** används med ett värde på 30 för att fastställa den maximala vänte tiden och lagrar sedan resultatet av kommandot i `$done` variabeln.</span><span class="sxs-lookup"><span data-stu-id="40888-156">It uses the **Timeout** parameter with a value of 30 to establish the maximum wait time, and then stores the results of the command in the `$done` variable.</span></span>

<span data-ttu-id="40888-157">I det här fallet är det bara kommandot på Server02-datorn som har slutförts efter 30 sekunder.</span><span class="sxs-lookup"><span data-stu-id="40888-157">In this case, after 30 seconds, only the command on the Server02 computer has completed.</span></span> <span data-ttu-id="40888-158">`Wait-Job` avslutar väntan, visar kommando tolken och returnerar det objekt som representerar det jobb som har slutförts.</span><span class="sxs-lookup"><span data-stu-id="40888-158">`Wait-Job` ends the wait, displays the command prompt, and returns the object that represents the job that was completed.</span></span>

<span data-ttu-id="40888-159">`$done`Variabeln innehåller ett jobb objekt som representerar jobbet som kördes på Server02.</span><span class="sxs-lookup"><span data-stu-id="40888-159">The `$done` variable contains a job object that represents the job that ran on Server02.</span></span>

### <span data-ttu-id="40888-160">Exempel 5: vänta tills ett av flera jobb har slutförts</span><span class="sxs-lookup"><span data-stu-id="40888-160">Example 5: Wait until one of several jobs finishes</span></span>

```powershell
Wait-Job -id 1,2,5 -Any
```

<span data-ttu-id="40888-161">Detta kommando identifierar tre jobb efter deras ID och väntar tills någon av dem har slutförts.</span><span class="sxs-lookup"><span data-stu-id="40888-161">This command identifies three jobs by their IDs and waits until any one of them are completed.</span></span>
<span data-ttu-id="40888-162">Kommando tolken returnerar när det första jobbet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="40888-162">The command prompt returns when the first job finishes.</span></span>

### <span data-ttu-id="40888-163">Exempel 6: vänta i en period och Tillåt sedan att jobbet fortsätter i bakgrunden</span><span class="sxs-lookup"><span data-stu-id="40888-163">Example 6: Wait for a period, then allow job to continue in background</span></span>

```powershell
Wait-Job -Name "DailyLog" -Timeout 120
```

<span data-ttu-id="40888-164">Det här kommandot väntar 120 sekunder (två minuter) för att DailyLog-jobbet ska slutföras.</span><span class="sxs-lookup"><span data-stu-id="40888-164">This command waits 120 seconds (two minutes) for the DailyLog job to finish.</span></span> <span data-ttu-id="40888-165">Om jobbet inte slutförs inom de kommande två minuterna returnerar kommando tolken ändå och jobbet fortsätter att köras i bakgrunden.</span><span class="sxs-lookup"><span data-stu-id="40888-165">If the job does not finish in the next two minutes, the command prompt returns anyway, and the job continues to run in the background.</span></span>

### <span data-ttu-id="40888-166">Exempel 7: vänta på ett jobb efter namn</span><span class="sxs-lookup"><span data-stu-id="40888-166">Example 7: Wait for a job by name</span></span>

```powershell
Wait-Job -Name "Job3"
```

<span data-ttu-id="40888-167">Det här kommandot använder jobb namnet för att identifiera det jobb som ska vänta.</span><span class="sxs-lookup"><span data-stu-id="40888-167">This command uses the job name to identify the job for which to wait.</span></span>

### <span data-ttu-id="40888-168">Exempel 8: vänta tills jobb på den lokala datorn har startats med Start-Job</span><span class="sxs-lookup"><span data-stu-id="40888-168">Example 8: Wait for jobs on local computer started with Start-Job</span></span>

```powershell
$j = Start-Job -ScriptBlock {Get-ChildItem *.ps1| where {$_lastwritetime -gt ((Get-Date) - (New-TimeSpan -Days 7))}}
$j | Wait-Job
```

<span data-ttu-id="40888-169">Det här exemplet visar hur du använder `Wait-Job` cmdleten med jobb som har startats på den lokala datorn med hjälp av `Start-Job` .</span><span class="sxs-lookup"><span data-stu-id="40888-169">This example shows how to use the `Wait-Job` cmdlet with jobs started on the local computer by using `Start-Job`.</span></span>

<span data-ttu-id="40888-170">Kommandona startar ett jobb som hämtar Windows PowerShell-skriptfilerna som har lagts till eller uppdaterats under den senaste veckan.</span><span class="sxs-lookup"><span data-stu-id="40888-170">These commands start a job that gets the Windows PowerShell script files that were added or updated in the last week.</span></span>

<span data-ttu-id="40888-171">Det första kommandot använder `Start-Job` för att starta ett bakgrunds jobb på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="40888-171">The first command uses `Start-Job` to start a background job on the local computer.</span></span> <span data-ttu-id="40888-172">Jobbet kör ett `Get-ChildItem` kommando som hämtar alla filer som har fil namns tillägget. ps1 som har lagts till eller uppdaterats under den senaste veckan.</span><span class="sxs-lookup"><span data-stu-id="40888-172">The job runs a `Get-ChildItem` command that gets all of the files that have a .ps1 file name extension that were added or updated in the last week.</span></span>

<span data-ttu-id="40888-173">Det tredje kommandot använder `Wait-Job` för att vänta tills jobbet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="40888-173">The third command uses `Wait-Job` to wait until the job is completed.</span></span> <span data-ttu-id="40888-174">När jobbet har slutförts visar kommandot jobbobjektet som innehåller information om jobbet.</span><span class="sxs-lookup"><span data-stu-id="40888-174">When the job finishes, the command displays the job object, which contains information about the job.</span></span>

### <span data-ttu-id="40888-175">Exempel 9: vänta tills jobben har startats på fjärrdatorer genom att använda Invoke-Command</span><span class="sxs-lookup"><span data-stu-id="40888-175">Example 9: Wait for jobs started on remote computers by using Invoke-Command</span></span>

```powershell
$s = New-PSSession Server01, Server02, Server03
$j = Invoke-Command -Session $s -ScriptBlock {Get-Process} -AsJob
$j | Wait-Job
```

<span data-ttu-id="40888-176">Det här exemplet visar hur du använder `Wait-Job` med jobb som har startats på fjärrdatorer med hjälp av parametern **AsJob** i `Invoke-Command` .</span><span class="sxs-lookup"><span data-stu-id="40888-176">This example shows how to use `Wait-Job` with jobs started on remote computers by using the **AsJob** parameter of `Invoke-Command`.</span></span> <span data-ttu-id="40888-177">När du använder **AsJob** skapas jobbet på den lokala datorn och resultaten returneras automatiskt till den lokala datorn, även om jobbet körs på fjärrdatorerna.</span><span class="sxs-lookup"><span data-stu-id="40888-177">When using **AsJob**, the job is created on the local computer and the results are automatically returned to the local computer, even though the job runs on the remote computers.</span></span>

<span data-ttu-id="40888-178">I det här exemplet används `Wait-Job` för att avgöra om ett `Get-Process` kommando som körs i sessioner på tre fjärrdatorer har slutförts.</span><span class="sxs-lookup"><span data-stu-id="40888-178">This example uses `Wait-Job` to determine whether a `Get-Process` command running in the sessions on three remote computers is completed.</span></span>

<span data-ttu-id="40888-179">Det första kommandot skapar **PSSession** -objekt på tre datorer och lagrar dem i `$s` variabeln.</span><span class="sxs-lookup"><span data-stu-id="40888-179">The first command creates **PSSession** objects on three computers and stores them in the `$s` variable.</span></span>

<span data-ttu-id="40888-180">Det andra kommandot använder `Invoke-Command` för att köra `Get-Process` i var och en av de tre sessionerna i `$s` .</span><span class="sxs-lookup"><span data-stu-id="40888-180">The second command uses `Invoke-Command` to run `Get-Process` in each of the three sessions in `$s`.</span></span>
<span data-ttu-id="40888-181">Kommandot använder parametern **AsJob** för att köra kommandot asynkront som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="40888-181">The command uses the **AsJob** parameter to run the command asynchronously as a background job.</span></span> <span data-ttu-id="40888-182">Kommandot returnerar ett jobb objekt, precis som de jobb som har startats med hjälp av `Start-Job` , och jobbobjektet lagras i `$j` variabeln.</span><span class="sxs-lookup"><span data-stu-id="40888-182">The command returns a job object, just like the jobs started by using `Start-Job`, and the job object is stored in the `$j` variable.</span></span>

<span data-ttu-id="40888-183">Det tredje kommandot använder en pipeline-operator ( `|` ) för att skicka jobbobjektet till- `$j` `Wait-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="40888-183">The third command uses a pipeline operator (`|`) to send the job object in `$j` to the `Wait-Job` cmdlet.</span></span> <span data-ttu-id="40888-184">Ett `Invoke-Command` kommando krävs inte i det här fallet eftersom jobbet finns på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="40888-184">An `Invoke-Command` command is not required in this case, because the job resides on the local computer.</span></span>

### <span data-ttu-id="40888-185">Exempel 10: vänta på ett jobb som har ett ID</span><span class="sxs-lookup"><span data-stu-id="40888-185">Example 10: Wait for a job that has an ID</span></span>

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

<span data-ttu-id="40888-186">Det här kommandot väntar på jobbet med ID-värdet 1.</span><span class="sxs-lookup"><span data-stu-id="40888-186">This command waits for the job with an ID value of 1.</span></span>

## <span data-ttu-id="40888-187">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="40888-187">PARAMETERS</span></span>

### <span data-ttu-id="40888-188">– Alla</span><span class="sxs-lookup"><span data-stu-id="40888-188">-Any</span></span>

<span data-ttu-id="40888-189">Anger att denna cmdlet visar kommando tolken och returnerar jobbobjektet när ett jobb har slutförts.</span><span class="sxs-lookup"><span data-stu-id="40888-189">Indicates that this cmdlet displays the command prompt, and returns the job object, when any job finishes.</span></span> <span data-ttu-id="40888-190">Som standard `Wait-Job` väntar det tills alla angivna jobb har slutförts innan meddelandet visas.</span><span class="sxs-lookup"><span data-stu-id="40888-190">By default, `Wait-Job` waits until all of the specified jobs are complete before it displays the prompt.</span></span>

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

### <span data-ttu-id="40888-191">-Filter</span><span class="sxs-lookup"><span data-stu-id="40888-191">-Filter</span></span>

<span data-ttu-id="40888-192">Anger en hash-tabell med villkor.</span><span class="sxs-lookup"><span data-stu-id="40888-192">Specifies a hash table of conditions.</span></span> <span data-ttu-id="40888-193">Denna cmdlet väntar på jobb som uppfyller alla villkor i hash-tabellen.</span><span class="sxs-lookup"><span data-stu-id="40888-193">This cmdlet waits for jobs that satisfy all of the conditions in the hash table.</span></span> <span data-ttu-id="40888-194">Ange en hash-tabell där nycklarna är jobb egenskaper och värdena är jobb egenskaps värden.</span><span class="sxs-lookup"><span data-stu-id="40888-194">Enter a hash table where the keys are job properties and the values are job property values.</span></span>

<span data-ttu-id="40888-195">Den här parametern fungerar bara på anpassade jobb typer, till exempel arbets flödes jobb och schemalagda jobb.</span><span class="sxs-lookup"><span data-stu-id="40888-195">This parameter works only on custom job types, such as workflow jobs and scheduled jobs.</span></span> <span data-ttu-id="40888-196">Den fungerar inte på vanliga bakgrunds jobb, till exempel de som skapats med hjälp av `Start-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="40888-196">It does not work on standard background jobs, such as those created by using the `Start-Job` cmdlet.</span></span> <span data-ttu-id="40888-197">Information om stöd för den här parametern finns i hjälp avsnittet för jobb typen.</span><span class="sxs-lookup"><span data-stu-id="40888-197">For information about support for this parameter, see the help topic for the job type.</span></span>

<span data-ttu-id="40888-198">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="40888-198">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="40888-199">-Force</span><span class="sxs-lookup"><span data-stu-id="40888-199">-Force</span></span>

<span data-ttu-id="40888-200">Anger att denna cmdlet fortsätter att vänta på jobb i tillståndet pausad eller frånkopplad.</span><span class="sxs-lookup"><span data-stu-id="40888-200">Indicates that this cmdlet continues to wait for jobs in the Suspended or Disconnected state.</span></span> <span data-ttu-id="40888-201">Som standard `Wait-Job` returnerar eller avslutar vänte läge när jobben är i något av följande tillstånd:</span><span class="sxs-lookup"><span data-stu-id="40888-201">By default, `Wait-Job` returns, or ends the wait, when jobs are in one of the following states:</span></span>

- <span data-ttu-id="40888-202">Slutförd</span><span class="sxs-lookup"><span data-stu-id="40888-202">Completed</span></span>
- <span data-ttu-id="40888-203">Misslyckad</span><span class="sxs-lookup"><span data-stu-id="40888-203">Failed</span></span>
- <span data-ttu-id="40888-204">Stoppad</span><span class="sxs-lookup"><span data-stu-id="40888-204">Stopped</span></span>
- <span data-ttu-id="40888-205">Inaktiverad</span><span class="sxs-lookup"><span data-stu-id="40888-205">Suspended</span></span>
- <span data-ttu-id="40888-206">Frånkopplad</span><span class="sxs-lookup"><span data-stu-id="40888-206">Disconnected</span></span>

<span data-ttu-id="40888-207">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="40888-207">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="40888-208">-ID</span><span class="sxs-lookup"><span data-stu-id="40888-208">-Id</span></span>

<span data-ttu-id="40888-209">Anger en matris med ID: n för jobb som denna cmdlet väntar på.</span><span class="sxs-lookup"><span data-stu-id="40888-209">Specifies an array of IDs of jobs for which this cmdlet waits.</span></span>

<span data-ttu-id="40888-210">ID är ett heltal som unikt identifierar jobbet i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="40888-210">The ID is an integer that uniquely identifies the job in the current session.</span></span> <span data-ttu-id="40888-211">Det är enklare att komma ihåg och skriva än instans-ID, men det är endast unikt i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="40888-211">It is easier to remember and type than the instance ID, but it is unique only in the current session.</span></span> <span data-ttu-id="40888-212">Du kan ange ett eller flera ID: n, avgränsade med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="40888-212">You can type one or more IDs, separated by commas.</span></span> <span data-ttu-id="40888-213">Om du vill hitta ID: t för ett jobb skriver du `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="40888-213">To find the ID of a job, type `Get-Job`.</span></span>

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

### <span data-ttu-id="40888-214">-InstanceId</span><span class="sxs-lookup"><span data-stu-id="40888-214">-InstanceId</span></span>

<span data-ttu-id="40888-215">Anger en matris med instans-ID: n för jobb som denna cmdlet väntar på.</span><span class="sxs-lookup"><span data-stu-id="40888-215">Specifies an array of instance IDs of jobs for which this cmdlet waits.</span></span> <span data-ttu-id="40888-216">Standardvärdet är alla jobb.</span><span class="sxs-lookup"><span data-stu-id="40888-216">The default is all jobs.</span></span>

<span data-ttu-id="40888-217">Ett instans-ID är ett GUID som unikt identifierar jobbet på datorn.</span><span class="sxs-lookup"><span data-stu-id="40888-217">An instance ID is a GUID that uniquely identifies the job on the computer.</span></span> <span data-ttu-id="40888-218">Använd om du vill hitta instans-ID: t för ett jobb `Get-Job` .</span><span class="sxs-lookup"><span data-stu-id="40888-218">To find the instance ID of a job, use `Get-Job`.</span></span>

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

### <span data-ttu-id="40888-219">– Jobb</span><span class="sxs-lookup"><span data-stu-id="40888-219">-Job</span></span>

<span data-ttu-id="40888-220">Anger jobb för vilka denna cmdlet väntar.</span><span class="sxs-lookup"><span data-stu-id="40888-220">Specifies the jobs for which this cmdlet waits.</span></span> <span data-ttu-id="40888-221">Ange en variabel som innehåller jobb objekt eller ett kommando som hämtar jobb objekt.</span><span class="sxs-lookup"><span data-stu-id="40888-221">Enter a variable that contains the job objects or a command that gets the job objects.</span></span> <span data-ttu-id="40888-222">Du kan också använda en pipeline-operator för att skicka jobb objekt till- `Wait-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="40888-222">You can also use a pipeline operator to send job objects to the `Wait-Job` cmdlet.</span></span> <span data-ttu-id="40888-223">Som standard `Wait-Job` väntar alla jobb som skapats i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="40888-223">By default, `Wait-Job` waits for all jobs created in the current session.</span></span>

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

### <span data-ttu-id="40888-224">-Name</span><span class="sxs-lookup"><span data-stu-id="40888-224">-Name</span></span>

<span data-ttu-id="40888-225">Anger egna namn på jobb som denna cmdlet väntar på.</span><span class="sxs-lookup"><span data-stu-id="40888-225">Specifies friendly names of jobs for which this cmdlet waits.</span></span>

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

### <span data-ttu-id="40888-226">– Tillstånd</span><span class="sxs-lookup"><span data-stu-id="40888-226">-State</span></span>

<span data-ttu-id="40888-227">Anger ett jobb tillstånd.</span><span class="sxs-lookup"><span data-stu-id="40888-227">Specifies a job state.</span></span> <span data-ttu-id="40888-228">Denna cmdlet väntar bara på jobb i det angivna läget.</span><span class="sxs-lookup"><span data-stu-id="40888-228">This cmdlet waits only for jobs in the specified state.</span></span> <span data-ttu-id="40888-229">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="40888-229">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="40888-230">NotStarted</span><span class="sxs-lookup"><span data-stu-id="40888-230">NotStarted</span></span>
- <span data-ttu-id="40888-231">Körs</span><span class="sxs-lookup"><span data-stu-id="40888-231">Running</span></span>
- <span data-ttu-id="40888-232">Slutförd</span><span class="sxs-lookup"><span data-stu-id="40888-232">Completed</span></span>
- <span data-ttu-id="40888-233">Misslyckad</span><span class="sxs-lookup"><span data-stu-id="40888-233">Failed</span></span>
- <span data-ttu-id="40888-234">Stoppad</span><span class="sxs-lookup"><span data-stu-id="40888-234">Stopped</span></span>
- <span data-ttu-id="40888-235">Blockerad</span><span class="sxs-lookup"><span data-stu-id="40888-235">Blocked</span></span>
- <span data-ttu-id="40888-236">Inaktiverad</span><span class="sxs-lookup"><span data-stu-id="40888-236">Suspended</span></span>
- <span data-ttu-id="40888-237">Frånkopplad</span><span class="sxs-lookup"><span data-stu-id="40888-237">Disconnected</span></span>
- <span data-ttu-id="40888-238">Pausar</span><span class="sxs-lookup"><span data-stu-id="40888-238">Suspending</span></span>
- <span data-ttu-id="40888-239">Stoppas</span><span class="sxs-lookup"><span data-stu-id="40888-239">Stopping</span></span>

<span data-ttu-id="40888-240">Mer information om jobb tillstånd finns i [JobState-uppräkning](/dotnet/api/system.management.automation.jobstate).</span><span class="sxs-lookup"><span data-stu-id="40888-240">For more information about job states, see [JobState Enumeration](/dotnet/api/system.management.automation.jobstate).</span></span>

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

### <span data-ttu-id="40888-241">-Timeout</span><span class="sxs-lookup"><span data-stu-id="40888-241">-Timeout</span></span>

<span data-ttu-id="40888-242">Anger maximal vänte tid för varje bakgrunds jobb, i sekunder.</span><span class="sxs-lookup"><span data-stu-id="40888-242">Specifies the maximum wait time for each background job, in seconds.</span></span> <span data-ttu-id="40888-243">Standardvärdet,-1, anger att cmdleten ska vänta tills jobbet har slutförts.</span><span class="sxs-lookup"><span data-stu-id="40888-243">The default value, -1, indicates that the cmdlet waits until the job finishes.</span></span> <span data-ttu-id="40888-244">Tids inställningen startar när du skickar `Wait-Job` kommandot, inte `Start-Job` kommandot.</span><span class="sxs-lookup"><span data-stu-id="40888-244">The timing starts when you submit the `Wait-Job` command, not the `Start-Job` command.</span></span>

<span data-ttu-id="40888-245">Om den här tiden överskrids, avslutas vänte tiden och kommando tolken returnerar, även om jobbet fortfarande körs.</span><span class="sxs-lookup"><span data-stu-id="40888-245">If this time is exceeded, the wait ends and the command prompt returns, even if the job is still running.</span></span> <span data-ttu-id="40888-246">Kommandot visar inga fel meddelanden.</span><span class="sxs-lookup"><span data-stu-id="40888-246">The command does not display any error message.</span></span>

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

### <span data-ttu-id="40888-247">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="40888-247">CommonParameters</span></span>

<span data-ttu-id="40888-248">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="40888-248">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="40888-249">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="40888-249">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="40888-250">INDATA</span><span class="sxs-lookup"><span data-stu-id="40888-250">INPUTS</span></span>

### <span data-ttu-id="40888-251">System. Management. Automation. RemotingJob</span><span class="sxs-lookup"><span data-stu-id="40888-251">System.Management.Automation.RemotingJob</span></span>

<span data-ttu-id="40888-252">Du kan skicka vidare ett jobb objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="40888-252">You can pipe a job object to this cmdlet.</span></span>

## <span data-ttu-id="40888-253">UTDATA</span><span class="sxs-lookup"><span data-stu-id="40888-253">OUTPUTS</span></span>

### <span data-ttu-id="40888-254">System. Management. Automation. PSRemotingJob</span><span class="sxs-lookup"><span data-stu-id="40888-254">System.Management.Automation.PSRemotingJob</span></span>

<span data-ttu-id="40888-255">Denna cmdlet returnerar jobb objekt som representerar de slutförda jobben.</span><span class="sxs-lookup"><span data-stu-id="40888-255">This cmdlet returns job objects that represent the completed jobs.</span></span> <span data-ttu-id="40888-256">Om vänte tiden slutar eftersom värdet för parametern **timeout** överskrids, `Wait-Job` returnerar inga objekt.</span><span class="sxs-lookup"><span data-stu-id="40888-256">If the wait ends because the value of the **Timeout** parameter is exceeded, `Wait-Job` does not return any objects.</span></span>

## <span data-ttu-id="40888-257">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="40888-257">NOTES</span></span>

<span data-ttu-id="40888-258">Som standard `Wait-Job` returnerar eller avslutar vänte läge när jobben är i något av följande tillstånd:</span><span class="sxs-lookup"><span data-stu-id="40888-258">By default, `Wait-Job` returns, or ends the wait, when jobs are in one of the following states:</span></span>

- <span data-ttu-id="40888-259">Slutförd</span><span class="sxs-lookup"><span data-stu-id="40888-259">Completed</span></span>
- <span data-ttu-id="40888-260">Misslyckad</span><span class="sxs-lookup"><span data-stu-id="40888-260">Failed</span></span>
- <span data-ttu-id="40888-261">Stoppad</span><span class="sxs-lookup"><span data-stu-id="40888-261">Stopped</span></span>
- <span data-ttu-id="40888-262">Inaktiverad</span><span class="sxs-lookup"><span data-stu-id="40888-262">Suspended</span></span>
- <span data-ttu-id="40888-263">Frånkopplad till direkt om du vill `Wait-Job` fortsätta att vänta på pausade och frånkopplade jobb använder du parametern **Force** .</span><span class="sxs-lookup"><span data-stu-id="40888-263">Disconnected To direct `Wait-Job` to continue to wait for Suspended and Disconnected jobs, use the **Force** parameter.</span></span>

## <span data-ttu-id="40888-264">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="40888-264">RELATED LINKS</span></span>

[<span data-ttu-id="40888-265">Hämta jobb</span><span class="sxs-lookup"><span data-stu-id="40888-265">Get-Job</span></span>](Get-Job.md)

[<span data-ttu-id="40888-266">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="40888-266">Invoke-Command</span></span>](Invoke-Command.md)

[<span data-ttu-id="40888-267">Mottagning – jobb</span><span class="sxs-lookup"><span data-stu-id="40888-267">Receive-Job</span></span>](Receive-Job.md)

[<span data-ttu-id="40888-268">Ta bort – jobb</span><span class="sxs-lookup"><span data-stu-id="40888-268">Remove-Job</span></span>](Remove-Job.md)

[<span data-ttu-id="40888-269">Start – jobb</span><span class="sxs-lookup"><span data-stu-id="40888-269">Start-Job</span></span>](Start-Job.md)

[<span data-ttu-id="40888-270">Stoppa – jobb</span><span class="sxs-lookup"><span data-stu-id="40888-270">Stop-Job</span></span>](Stop-Job.md)
