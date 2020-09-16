---
title: Visa förloppet under multi-threading
description: Så här använder du Skriv förloppet över flera trådar med en förgrunds-objekt-parallell
ms.date: 08/02/2020
ms.openlocfilehash: 909fc1bbdeded8845b1955e3384fb55db7173030
ms.sourcegitcommit: 640646992955116def23d16dd12c221857d37b68
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/03/2020
ms.locfileid: "89410850"
---
# <a name="writing-progress-across-multiple-threads-with-foreach-parallel"></a><span data-ttu-id="95ca6-103">Skriv förlopp över flera trådar med förgrunds parallell</span><span class="sxs-lookup"><span data-stu-id="95ca6-103">Writing Progress across multiple threads with Foreach Parallel</span></span>

<span data-ttu-id="95ca6-104">Från och med PowerShell 7,0 är möjligheten att arbeta i flera trådar samtidigt möjlig med hjälp av **Parallel** -parametern i [-objekt-](/powershell/module/Microsoft.PowerShell.Core/Foreach-Object) cmdleten.</span><span class="sxs-lookup"><span data-stu-id="95ca6-104">Starting in PowerShell 7.0, the ability to work in multiple threads simultaneously is possible using the **Parallel** parameter in the [Foreach-Object](/powershell/module/Microsoft.PowerShell.Core/Foreach-Object) cmdlet.</span></span> <span data-ttu-id="95ca6-105">Det kan vara en utmaning att övervaka förloppet för dessa trådar.</span><span class="sxs-lookup"><span data-stu-id="95ca6-105">Monitoring the progress of these threads can be a challenge though.</span></span> <span data-ttu-id="95ca6-106">Normalt kan du övervaka förloppet för en process med hjälp av [Skriv förloppet](/powershell/module/Microsoft.PowerShell.Utility/Write-Progress).</span><span class="sxs-lookup"><span data-stu-id="95ca6-106">Normally, you can monitor the progress of a process using [Write-Progress](/powershell/module/Microsoft.PowerShell.Utility/Write-Progress).</span></span>
<span data-ttu-id="95ca6-107">Men eftersom PowerShell använder sig av en separat körnings utrymme för varje tråd när de använder **parallellt**, så rapporterar inte återställningen till värden lika enkelt som normal användning av `Write-Progress` .</span><span class="sxs-lookup"><span data-stu-id="95ca6-107">However, since PowerShell uses a separate runspace for each thread when using **Parallel**, reporting the progress back to the host isn't as straight forward as normal use of `Write-Progress`.</span></span>

## <a name="using-a-synced-hashtable-to-track-progress"></a><span data-ttu-id="95ca6-108">Använda en synkroniserad hash för att spåra förloppet</span><span class="sxs-lookup"><span data-stu-id="95ca6-108">Using a synced hashtable to track progress</span></span>

<span data-ttu-id="95ca6-109">När du skriver förloppet från flera trådar blir spårningen svår eftersom när parallella processer körs i PowerShell, och varje process har det egna körnings utrymme.</span><span class="sxs-lookup"><span data-stu-id="95ca6-109">When writing the progress from multiple threads, tracking becomes difficult because when running parallel processes in PowerShell, each process has it's own runspace.</span></span> <span data-ttu-id="95ca6-110">Du kan komma runt detta genom att använda en [synkroniserad hash](/dotnet/api/system.collections.hashtable.synchronized).</span><span class="sxs-lookup"><span data-stu-id="95ca6-110">To get around this, you can use a [synchronized hashtable](/dotnet/api/system.collections.hashtable.synchronized).</span></span> <span data-ttu-id="95ca6-111">En synkroniserad hash-post är en tråd säker data struktur som kan ändras av flera trådar samtidigt utan att ett fel utlöses.</span><span class="sxs-lookup"><span data-stu-id="95ca6-111">A synced hashtable is a thread safe data structure that can be modified by multiple threads simultaneously without throwing an error.</span></span>

### <a name="set-up"></a><span data-ttu-id="95ca6-112">Konfigurera</span><span class="sxs-lookup"><span data-stu-id="95ca6-112">Set up</span></span>

<span data-ttu-id="95ca6-113">En av nackerna med den här metoden är att det tar en, ganska komplicerad inställning att se till att allt körs utan fel.</span><span class="sxs-lookup"><span data-stu-id="95ca6-113">One of the downsides to this approach is it takes a, somewhat, complex set up to ensure everything runs without error.</span></span>

```powershell
$dataset = @(
    @{
        Id   = 1
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 2
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 3
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 4
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 5
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
)

# Create a hashtable for process.
# Keys should be ID's of the processes
$origin = @{}
$dataset | Foreach-Object {$origin.($_.id) = @{}}

# Create synced hashtable
$sync = [System.Collections.Hashtable]::Synchronized($origin)
```

<span data-ttu-id="95ca6-114">I det här avsnittet skapas tre olika data strukturer i tre olika syfte.</span><span class="sxs-lookup"><span data-stu-id="95ca6-114">This section creates three different data structures, for three different purposes.</span></span>

<span data-ttu-id="95ca6-115">`$dataSet`Variabeln lagrar en matris med hash som används för att koordinera nästa steg utan att risken ändras.</span><span class="sxs-lookup"><span data-stu-id="95ca6-115">The `$dataSet` variable stores an array of hashtables that is used to coordinate the next steps without the risk of being modified.</span></span> <span data-ttu-id="95ca6-116">Om en objekt samling ändras när du går igenom samlingen, genererar PowerShell ett fel.</span><span class="sxs-lookup"><span data-stu-id="95ca6-116">If an object collection is modified while iterating through the collection, PowerShell throws an error.</span></span> <span data-ttu-id="95ca6-117">Du måste behålla objekt samlingen i slingan separat från de objekt som ändras.</span><span class="sxs-lookup"><span data-stu-id="95ca6-117">You must keep the object collection in the loop separate from the objects being modified.</span></span> <span data-ttu-id="95ca6-118">`Id`Nyckeln i varje hash-tabellen är identifieraren för en modell process.</span><span class="sxs-lookup"><span data-stu-id="95ca6-118">The `Id` key in each hashtable is the identifier for a mock process.</span></span> <span data-ttu-id="95ca6-119">`Wait`Nyckeln simulerar arbets belastningen för varje modell process som spåras.</span><span class="sxs-lookup"><span data-stu-id="95ca6-119">The `Wait` key simulates the workload of each mock process being tracked.</span></span>

<span data-ttu-id="95ca6-120">`$origin`Variabeln lagrar en kapslad hash-tabell med varje nyckel som en av de blå process-ID: t.</span><span class="sxs-lookup"><span data-stu-id="95ca6-120">The `$origin` variable stores a nested hashtable with each key being one of the mock process id's.</span></span>
<span data-ttu-id="95ca6-121">Sedan används den för att torka den synkroniserade hash-filen som lagras i `$sync` variabeln.</span><span class="sxs-lookup"><span data-stu-id="95ca6-121">Then, it is used to hydrate the synchronized hashtable stored in the `$sync` variable.</span></span> <span data-ttu-id="95ca6-122">`$sync`Variabeln ansvarar för rapportering av förloppet till den överordnade körnings utrymme, som visar förloppet.</span><span class="sxs-lookup"><span data-stu-id="95ca6-122">The `$sync` variable is responsible for reporting the progress back to the parent runspace, which displays the progress.</span></span>

### <a name="running-the-processes"></a><span data-ttu-id="95ca6-123">Köra processerna</span><span class="sxs-lookup"><span data-stu-id="95ca6-123">Running the processes</span></span>

<span data-ttu-id="95ca6-124">I det här avsnittet körs multi-threaded-processer och skapar några av de utdata som används för att visa förloppet.</span><span class="sxs-lookup"><span data-stu-id="95ca6-124">This section runs the multi-threaded processes and creates some of the output used to display progress.</span></span>

```powershell
$job = $dataset | Foreach-Object -ThrottleLimit 3 -AsJob -Parallel {
    $syncCopy = $using:sync
    $process = $syncCopy.$($PSItem.Id)

    $process.Id = $PSItem.Id
    $process.Activity = "Id $($PSItem.Id) starting"
    $process.Status = "Processing"

    # Fake workload start up that takes x amount of time to complete
    start-sleep -Milliseconds ($PSItem.wait*5)

    # Process. update activity
    $process.Activity = "Id $($PSItem.id) processing"
    foreach ($percent in 1..100)
    {
        # Update process on status
        $process.Status = "Handling $percent/100"
        $process.PercentComplete = (($percent / 100) * 100)

        # Fake workload that takes x amount of time to complete
        Start-Sleep -Milliseconds $PSItem.Wait
    }

    # Mark process as completed
    $process.Completed = $true
}
```

<span data-ttu-id="95ca6-125">De blå processerna skickas till `Foreach-Object` och startas som jobb.</span><span class="sxs-lookup"><span data-stu-id="95ca6-125">The mock processes are sent to `Foreach-Object` and started as jobs.</span></span> <span data-ttu-id="95ca6-126">**ThrottleLimit** har angetts till **3** för att markera att köra flera processer i en kö.</span><span class="sxs-lookup"><span data-stu-id="95ca6-126">The **ThrottleLimit** is set to **3** to highlight running multiple processes in a queue.</span></span> <span data-ttu-id="95ca6-127">Jobben lagras i `$job` variabeln och gör det möjligt för oss att veta när alla processer har avslut ATS senare.</span><span class="sxs-lookup"><span data-stu-id="95ca6-127">The jobs are stored in the `$job` variable and allows us to know when all the processes have finished later on.</span></span>

<span data-ttu-id="95ca6-128">När du använder `using:` instruktionen för att referera till en överordnad omfångs variabel i PowerShell kan du inte använda uttryck för att göra den dynamisk.</span><span class="sxs-lookup"><span data-stu-id="95ca6-128">When using the `using:` statement to reference a parent scope variable in PowerShell, you can't use expressions to make it dynamic.</span></span> <span data-ttu-id="95ca6-129">Om du till exempel försökte skapa `$process` variabeln som detta, `$process = $using:sync.$($PSItem.id)` får du ett fel meddelande om att du inte kan använda uttryck där.</span><span class="sxs-lookup"><span data-stu-id="95ca6-129">For example, if you tried to create the `$process` variable like this, `$process = $using:sync.$($PSItem.id)`, you would get an error stating you can't use expressions there.</span></span> <span data-ttu-id="95ca6-130">Därför skapar vi `$syncCopy` variabeln för att kunna referera till och ändra `$sync` variabeln utan att risken för den fungerar.</span><span class="sxs-lookup"><span data-stu-id="95ca6-130">So, we create the `$syncCopy` variable to be able to reference and modify the `$sync` variable without the risk of it failing.</span></span>

<span data-ttu-id="95ca6-131">Därefter skapar vi en hash-hash som representerar förloppet för processen i slingan med `$process` variabeln genom att referera till synkroniserade hash-nycklar.</span><span class="sxs-lookup"><span data-stu-id="95ca6-131">Next, we build out a hashtable to represent the progress of the process currently in the loop using the `$process` variable by referencing the synchronized hashtable keys.</span></span> <span data-ttu-id="95ca6-132">**Aktivitet** och **status** nycklar används som parameter värden för `Write-Progress` för att visa statusen för en specifik skiss process i nästa avsnitt.</span><span class="sxs-lookup"><span data-stu-id="95ca6-132">The **Activity** and the **Status** keys are used as parameter values for `Write-Progress` to display the status of a given mock process in the next section.</span></span>

<span data-ttu-id="95ca6-133">`foreach`Slingan är bara ett sätt att simulera processen och är slumpmässig baserat på `$dataSet` attributet **wait** för att ställa in `Start-Sleep` i millisekunder.</span><span class="sxs-lookup"><span data-stu-id="95ca6-133">The `foreach` loop is just a way to simulate the process working and is randomized based on the `$dataSet` **Wait** attribute to set `Start-Sleep` using milliseconds.</span></span> <span data-ttu-id="95ca6-134">Hur du beräknar processens förlopp kan variera.</span><span class="sxs-lookup"><span data-stu-id="95ca6-134">How you calculate the progress of your process may vary.</span></span>

### <a name="displaying-the-progress-of-multiple-processes"></a><span data-ttu-id="95ca6-135">Visa förloppet för flera processer</span><span class="sxs-lookup"><span data-stu-id="95ca6-135">Displaying the progress of multiple processes</span></span>

<span data-ttu-id="95ca6-136">Nu när de blå processerna körs som jobb kan vi börja skriva process förloppet till PowerShell-fönstret.</span><span class="sxs-lookup"><span data-stu-id="95ca6-136">Now that the mock processes are running as jobs, we can start to write the processes progress to the PowerShell window.</span></span>

```powershell
while($job.State -eq 'Running')
{
    $sync.Keys | Foreach-Object {
        # If key is not defined, ignore
        if(![string]::IsNullOrEmpty($sync.$_.keys))
        {
            # Create parameter hashtable to splat
            $param = $sync.$_

            # Execute Write-Progress
            Write-Progress @param
        }
    }

    # Wait to refresh to not overload gui
    Start-Sleep -Seconds 0.1
}
```

<span data-ttu-id="95ca6-137">`$job`Variabeln innehåller det överordnade **jobbet** och har ett underordnat **jobb** för var och en av de blå processerna.</span><span class="sxs-lookup"><span data-stu-id="95ca6-137">The `$job` variable contains the parent **job** and has a child **job** for each of the mock processes.</span></span> <span data-ttu-id="95ca6-138">När något av de underordnade jobben fortfarande körs förblir det överordnade jobbets **tillstånd** "körs".</span><span class="sxs-lookup"><span data-stu-id="95ca6-138">While any of the child jobs are still running, the parent job **State** will remain "Running".</span></span> <span data-ttu-id="95ca6-139">Detta gör att vi kan använda `while` loopen för att kontinuerligt uppdatera förloppet för varje process tills alla processer har slutförts.</span><span class="sxs-lookup"><span data-stu-id="95ca6-139">This allows us to use the `while` loop to continually update the progress of every process until all processes are finished.</span></span>

<span data-ttu-id="95ca6-140">I loopen loopar vi igenom var och en av nycklarna i `$sync` variabeln.</span><span class="sxs-lookup"><span data-stu-id="95ca6-140">Within the while loop, we loop through each of the keys in the `$sync` variable.</span></span> <span data-ttu-id="95ca6-141">Eftersom det här är en synkroniserad hash-uppdatering, uppdateras den ständigt men kan fortfarande användas utan att några fel utlöses.</span><span class="sxs-lookup"><span data-stu-id="95ca6-141">Since this is a synchronized hashtable, it is constantly updated but can still be accessed without throwing any errors.</span></span>

<span data-ttu-id="95ca6-142">Det finns en kontroll för att se till att den process som rapporteras verkligen körs med hjälp av `IsNullOrEmpty()` metoden.</span><span class="sxs-lookup"><span data-stu-id="95ca6-142">There is a check to ensure that the process being reported is actually running using the `IsNullOrEmpty()` method.</span></span> <span data-ttu-id="95ca6-143">Om processen inte har startats rapporterar inte loopen och går vidare till nästa tills den får en process som har startats.</span><span class="sxs-lookup"><span data-stu-id="95ca6-143">If the process hasn't been started, the loop won't report on it and move on to the next until it gets to a process that has been started.</span></span> <span data-ttu-id="95ca6-144">Om processen startas används hash-tabellen från den aktuella nyckeln för att splat parametrarna till `Write-Progress` .</span><span class="sxs-lookup"><span data-stu-id="95ca6-144">If the process is started, the hashtable from the current key is used to splat the parameters to `Write-Progress`.</span></span>

### <a name="full-example"></a><span data-ttu-id="95ca6-145">Fullständigt exempel</span><span class="sxs-lookup"><span data-stu-id="95ca6-145">Full example</span></span>

```powershell
# Example workload
$dataset = @(
    @{
        Id   = 1
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 2
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 3
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 4
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
    @{
        Id   = 5
        Wait = 3..10 | get-random | Foreach-Object {$_*100}
    }
)

# Create a hashtable for process.
# Keys should be ID's of the processes
$origin = @{}
$dataset | Foreach-Object {$origin.($_.id) = @{}}

# Create synced hashtable
$sync = [System.Collections.Hashtable]::Synchronized($origin)

$job = $dataset | Foreach-Object -ThrottleLimit 3 -AsJob -Parallel {
    $syncCopy = $using:sync
    $process = $syncCopy.$($PSItem.Id)

    $process.Id = $PSItem.Id
    $process.Activity = "Id $($PSItem.Id) starting"
    $process.Status = "Processing"

    # Fake workload start up that takes x amount of time to complete
    start-sleep -Milliseconds ($PSItem.wait*5)

    # Process. update activity
    $process.Activity = "Id $($PSItem.id) processing"
    foreach ($percent in 1..100)
    {
        # Update process on status
        $process.Status = "Handling $percent/100"
        $process.PercentComplete = (($percent / 100) * 100)

        # Fake workload that takes x amount of time to complete
        Start-Sleep -Milliseconds $PSItem.Wait
    }

    # Mark process as completed
    $process.Completed = $true
}

while($job.State -eq 'Running')
{
    $sync.Keys | Foreach-Object {
        # If key is not defined, ignore
        if(![string]::IsNullOrEmpty($sync.$_.keys))
        {
            # Create parameter hashtable to splat
            $param = $sync.$_

            # Execute Write-Progress
            Write-Progress @param
        }
    }

    # Wait to refresh to not overload gui
    Start-Sleep -Seconds 0.1
}
```

## <a name="related-links"></a><span data-ttu-id="95ca6-146">Relaterade länkar</span><span class="sxs-lookup"><span data-stu-id="95ca6-146">Related Links</span></span>

- [<span data-ttu-id="95ca6-147">about_Jobs</span><span class="sxs-lookup"><span data-stu-id="95ca6-147">about_Jobs</span></span>](/powershell/module/Microsoft.PowerShell.Core/About/about_Jobs)
- [<span data-ttu-id="95ca6-148">about_Scopes</span><span class="sxs-lookup"><span data-stu-id="95ca6-148">about_Scopes</span></span>](/powershell/module/Microsoft.PowerShell.Core/About/about_Scopes)
- [<span data-ttu-id="95ca6-149">about_Splatting</span><span class="sxs-lookup"><span data-stu-id="95ca6-149">about_Splatting</span></span>](/powershell/module/Microsoft.PowerShell.Core/About/about_Splatting)
