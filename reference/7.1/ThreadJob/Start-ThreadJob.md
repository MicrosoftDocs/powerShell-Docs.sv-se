---
external help file: Microsoft.PowerShell.ThreadJob.dll-Help.xml
Locale: en-US
Module Name: ThreadJob
ms.date: 12/05/2020
online version: https://docs.microsoft.com/powershell/module/threadjob/start-threadjob?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-ThreadJob
ms.openlocfilehash: bced2b87c3843833414ebfd189d003e83af9718f
ms.sourcegitcommit: f9d855dd73b916559a22e337672dea3fbb11c634
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/07/2020
ms.locfileid: "96777755"
---
# <span data-ttu-id="b138a-102">Start-ThreadJob</span><span class="sxs-lookup"><span data-stu-id="b138a-102">Start-ThreadJob</span></span>

## <span data-ttu-id="b138a-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="b138a-103">SYNOPSIS</span></span>
<span data-ttu-id="b138a-104">Skapar bakgrunds jobb som liknar- `Start-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b138a-104">Creates background jobs similar to the `Start-Job` cmdlet.</span></span>

## <span data-ttu-id="b138a-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b138a-105">SYNTAX</span></span>

### <span data-ttu-id="b138a-106">Script block</span><span class="sxs-lookup"><span data-stu-id="b138a-106">ScriptBlock</span></span>

```
Start-ThreadJob [-ScriptBlock] <ScriptBlock> [-Name <String>] [-InitializationScript <ScriptBlock>]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [-ThrottleLimit <Int32>]
 [-StreamingHost <PSHost>] [<CommonParameters>]
```

### <span data-ttu-id="b138a-107">FilePath</span><span class="sxs-lookup"><span data-stu-id="b138a-107">FilePath</span></span>

```
Start-ThreadJob [-FilePath] <String> [-Name <String>] [-InitializationScript <ScriptBlock>]
 [-InputObject <PSObject>] [-ArgumentList <Object[]>] [-ThrottleLimit <Int32>]
 [-StreamingHost <PSHost>] [<CommonParameters>]
```

## <span data-ttu-id="b138a-108">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b138a-108">DESCRIPTION</span></span>

<span data-ttu-id="b138a-109">`Start-ThreadJob` skapar bakgrunds jobb som liknar- `Start-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b138a-109">`Start-ThreadJob` creates background jobs similar to the `Start-Job` cmdlet.</span></span> <span data-ttu-id="b138a-110">Den största skillnaden är att jobben som skapas körs i separata trådar i den lokala processen.</span><span class="sxs-lookup"><span data-stu-id="b138a-110">The main difference is that the jobs which are created run in separate threads within the local process.</span></span> <span data-ttu-id="b138a-111">Som standard använder jobben den aktuella arbets katalogen för den anropare som startade jobbet.</span><span class="sxs-lookup"><span data-stu-id="b138a-111">By default, the jobs use the current working directory of the caller that started the job.</span></span>

<span data-ttu-id="b138a-112">Cmdleten stöder också en **ThrottleLimit** -parameter för att begränsa antalet jobb som körs samtidigt.</span><span class="sxs-lookup"><span data-stu-id="b138a-112">The cmdlet also supports a **ThrottleLimit** parameter to limit the number of jobs running at one time.</span></span> <span data-ttu-id="b138a-113">När fler jobb startas placeras de i kö och väntar tills det aktuella antalet jobb sjunker under begränsnings gränsen.</span><span class="sxs-lookup"><span data-stu-id="b138a-113">As more jobs are started, they are queued and wait until the current number of jobs drops below the throttle limit.</span></span>

## <span data-ttu-id="b138a-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="b138a-114">EXAMPLES</span></span>

### <span data-ttu-id="b138a-115">Exempel 1 – Skapa bakgrunds jobb med en tråd gräns på 2</span><span class="sxs-lookup"><span data-stu-id="b138a-115">Example 1 - Create background jobs with a thread limit of 2</span></span>

```powershell
Start-ThreadJob -ScriptBlock { 1..100 | % { sleep 1; "Output $_" } } -ThrottleLimit 2
Start-ThreadJob -ScriptBlock { 1..100 | % { sleep 1; "Output $_" } }
Start-ThreadJob -ScriptBlock { 1..100 | % { sleep 1; "Output $_" } }
Get-Job
```

```Output
Id   Name   PSJobTypeName   State        HasMoreData   Location     Command
--   ----   -------------   -----        -----------   --------     -------
1    Job1   ThreadJob       Running      True          PowerShell   1..100 | % { sleep 1;...
2    Job2   ThreadJob       Running      True          PowerShell   1..100 | % { sleep 1;...
3    Job3   ThreadJob       NotStarted   False         PowerShell   1..100 | % { sleep 1;...
```

### <span data-ttu-id="b138a-116">Exempel 2 – Jämför prestanda för Start-Job och Start-ThreadJob</span><span class="sxs-lookup"><span data-stu-id="b138a-116">Example 2 - Compare the performance of Start-Job and Start-ThreadJob</span></span>

<span data-ttu-id="b138a-117">I det här exemplet visas skillnaden mellan `Start-Job` och `Start-ThreadJob` .</span><span class="sxs-lookup"><span data-stu-id="b138a-117">This example shows the difference between `Start-Job` and `Start-ThreadJob`.</span></span> <span data-ttu-id="b138a-118">Jobben kör `Start-Sleep` cmdleten för 1 sekund.</span><span class="sxs-lookup"><span data-stu-id="b138a-118">The jobs run the `Start-Sleep` cmdlet for 1 second.</span></span> <span data-ttu-id="b138a-119">Eftersom jobben körs parallellt, är den totala körnings tiden ungefär 1 sekund, och varje gång som krävs för att skapa jobben.</span><span class="sxs-lookup"><span data-stu-id="b138a-119">Since the jobs run in parallel, the total execution time is about 1 second, plus any time required to create the jobs.</span></span>

```powershell
# start five background jobs each running 1 second
Measure-Command {1..5 | % {Start-Job {Start-Sleep 1}} | Wait-Job} | Select-Object TotalSeconds
Measure-Command {1..5 | % {Start-ThreadJob {Start-Sleep 1}} | Wait-Job} | Select-Object TotalSeconds
```

```Output
TotalSeconds
------------
   5.7665849
   1.5735008
```

<span data-ttu-id="b138a-120">När du har subtraherat 1 sekund för körnings tid kan du se att det `Start-Job` tar cirka 4,8 sekunder att skapa fem jobb.</span><span class="sxs-lookup"><span data-stu-id="b138a-120">After subtracting 1 second for execution time, you can see that `Start-Job` takes about 4.8 seconds to create five jobs.</span></span> <span data-ttu-id="b138a-121">`Start-ThreadJob` är 8 gånger snabbare, tar cirka 0,6 sekunder att skapa fem jobb.</span><span class="sxs-lookup"><span data-stu-id="b138a-121">`Start-ThreadJob` is 8 times faster, taking about 0.6 seconds to create five jobs.</span></span> <span data-ttu-id="b138a-122">Resultaten kan variera i din miljö, men den relativa förbättringen bör vara densamma.</span><span class="sxs-lookup"><span data-stu-id="b138a-122">The results may vary in your environment but the relative improvement should be the same.</span></span>

### <span data-ttu-id="b138a-123">Exempel 3 – skapa jobb med InputObject</span><span class="sxs-lookup"><span data-stu-id="b138a-123">Example 3 - Create jobs using InputObject</span></span>

<span data-ttu-id="b138a-124">I det här exemplet använder skript block `$input` variabeln för att ta emot ininformation från **InputObject** -parametern.</span><span class="sxs-lookup"><span data-stu-id="b138a-124">In this example, the script block uses the `$input` variable to receive input from the **InputObject** parameter.</span></span> <span data-ttu-id="b138a-125">Detta kan också göras av rör objekt till `Start-ThreadJob` .</span><span class="sxs-lookup"><span data-stu-id="b138a-125">This can also be done by piping objects to `Start-ThreadJob`.</span></span>

```powershell
$j = Start-ThreadJob -InputObject (Get-Process pwsh) -ScriptBlock { $input | Out-String }
$j | Wait-Job | Receive-Job
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     94   145.80     159.02      18.31   18276   1 pwsh
    101   163.30     222.05      29.00   35928   1 pwsh
```

```powershell
$j = Get-Process pwsh | Start-ThreadJob -ScriptBlock { $input | Out-String }
$j | Wait-Job | Receive-Job
```

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     94   145.80     159.02      18.31   18276   1 pwsh
    101   163.30     222.05      29.00   35928   1 pwsh
```

### <span data-ttu-id="b138a-126">Exempel 4 – strömma jobbets utdata till den överordnade värden</span><span class="sxs-lookup"><span data-stu-id="b138a-126">Example 4 - Stream job output to parent host</span></span>

<span data-ttu-id="b138a-127">Med hjälp av parametern **StreamingHost** kan du ange att ett jobb dirigerar alla värden för utdata till en speciell värd.</span><span class="sxs-lookup"><span data-stu-id="b138a-127">Using the **StreamingHost** parameter you can tell a job to direct all host output to a specific host.</span></span> <span data-ttu-id="b138a-128">Utan den här parametern går utdata till jobb data ström samlingen och visas inte i en värd konsol förrän du får utdata från jobbet.</span><span class="sxs-lookup"><span data-stu-id="b138a-128">Without this parameter the output goes to the job data stream collection and doesn't appear in a host console until you receive the output from the job.</span></span>

<span data-ttu-id="b138a-129">I det här exemplet skickas den aktuella värden till `Start-ThreadJob` med hjälp av den `$Host` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="b138a-129">For this example, the current host is passed to `Start-ThreadJob` using the `$Host` automatic variable.</span></span>

```powershell
PS> Start-ThreadJob -ScriptBlock { Read-Host 'Say hello'; Write-Warning 'Warning output' } -StreamingHost $Host

Id   Name   PSJobTypeName   State         HasMoreData     Location      Command
--   ----   -------------   -----         -----------     --------      -------
7    Job7   ThreadJob       NotStarted    False           PowerShell    Read-Host 'Say hello'; �

PS> Say hello: Hello
WARNING: Warning output
PS> Receive-Job -Id 7
Hello
WARNING: Warning output
PS>
```

<span data-ttu-id="b138a-130">Observera att prompten från `Read-Host` visas och att du kan skriva in information.</span><span class="sxs-lookup"><span data-stu-id="b138a-130">Notice that the prompt from `Read-Host` is displayed and you are able to type input.</span></span> <span data-ttu-id="b138a-131">Sedan visas meddelandet från `Write-Warning` .</span><span class="sxs-lookup"><span data-stu-id="b138a-131">Then, the message from `Write-Warning` is displayed.</span></span> <span data-ttu-id="b138a-132">`Receive-Job`Cmdleten returnerar alla utdata från jobbet.</span><span class="sxs-lookup"><span data-stu-id="b138a-132">The `Receive-Job` cmdlet returns all the output from the job.</span></span>

## <span data-ttu-id="b138a-133">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="b138a-133">PARAMETERS</span></span>

### <span data-ttu-id="b138a-134">– Argument List</span><span class="sxs-lookup"><span data-stu-id="b138a-134">-ArgumentList</span></span>

<span data-ttu-id="b138a-135">Anger en matris med argument eller parameter värden för det skript som anges av **fil Sök vägen** eller **script block** -parametrarna.</span><span class="sxs-lookup"><span data-stu-id="b138a-135">Specifies an array of arguments, or parameter values, for the script that is specified by the **FilePath** or **ScriptBlock** parameters.</span></span>

<span data-ttu-id="b138a-136">**Argument List** måste vara den sista parametern på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="b138a-136">**ArgumentList** must be the last parameter on the command line.</span></span> <span data-ttu-id="b138a-137">Alla värden som följer efter parameter namnet tolkas som värden i argument listan.</span><span class="sxs-lookup"><span data-stu-id="b138a-137">All the values that follow the parameter name are interpreted values in the argument list.</span></span>

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b138a-138">-Sökväg</span><span class="sxs-lookup"><span data-stu-id="b138a-138">-FilePath</span></span>

<span data-ttu-id="b138a-139">Anger en skript fil som ska köras som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="b138a-139">Specifies a script file to run as a background job.</span></span> <span data-ttu-id="b138a-140">Ange sökvägen och fil namnet för skriptet.</span><span class="sxs-lookup"><span data-stu-id="b138a-140">Enter the path and filename of the script.</span></span> <span data-ttu-id="b138a-141">Skriptet måste finnas på den lokala datorn eller i en mapp som den lokala datorn kan komma åt.</span><span class="sxs-lookup"><span data-stu-id="b138a-141">The script must be on the local computer or in a folder that the local computer can access.</span></span>

<span data-ttu-id="b138a-142">När du använder den här parametern konverterar PowerShell innehållet i den angivna skript filen till ett-skript block och kör skript blocket som ett bakgrunds jobb.</span><span class="sxs-lookup"><span data-stu-id="b138a-142">When you use this parameter, PowerShell converts the contents of the specified script file to a script block and runs the script block as a background job.</span></span>

```yaml
Type: System.String
Parameter Sets: FilePath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b138a-143">-InitializationScript</span><span class="sxs-lookup"><span data-stu-id="b138a-143">-InitializationScript</span></span>

<span data-ttu-id="b138a-144">Anger kommandon som körs innan jobbet startas.</span><span class="sxs-lookup"><span data-stu-id="b138a-144">Specifies commands that run before the job starts.</span></span> <span data-ttu-id="b138a-145">Omge kommandoen med klammerparenteser ( `{}` ) för att skapa ett skript block.</span><span class="sxs-lookup"><span data-stu-id="b138a-145">Enclose the commands in braces (`{}`) to create a script block.</span></span>

<span data-ttu-id="b138a-146">Använd den här parametern för att förbereda sessionen där jobbet körs.</span><span class="sxs-lookup"><span data-stu-id="b138a-146">Use this parameter to prepare the session in which the job runs.</span></span> <span data-ttu-id="b138a-147">Du kan till exempel använda den för att lägga till funktioner och moduler i sessionen.</span><span class="sxs-lookup"><span data-stu-id="b138a-147">For example, you can use it to add functions and modules to the session.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b138a-148">– InputObject</span><span class="sxs-lookup"><span data-stu-id="b138a-148">-InputObject</span></span>

<span data-ttu-id="b138a-149">Anger de objekt som ska användas som inmatade för skript blocket.</span><span class="sxs-lookup"><span data-stu-id="b138a-149">Specifies the objects used as input to the script block.</span></span> <span data-ttu-id="b138a-150">Du kan också använda pipeline-ingångar.</span><span class="sxs-lookup"><span data-stu-id="b138a-150">It also allows for pipeline input.</span></span> <span data-ttu-id="b138a-151">Använd den `$input` automatiska variabeln i-skript blocket för att komma åt objekten.</span><span class="sxs-lookup"><span data-stu-id="b138a-151">Use the `$input` automatic variable in the script block to access the input objects.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="b138a-152">-Name</span><span class="sxs-lookup"><span data-stu-id="b138a-152">-Name</span></span>

<span data-ttu-id="b138a-153">Anger ett eget namn för det nya jobbet.</span><span class="sxs-lookup"><span data-stu-id="b138a-153">Specifies a friendly name for the new job.</span></span> <span data-ttu-id="b138a-154">Du kan använda namnet för att identifiera jobbet till andra jobb-cmdlet: ar, till exempel `Stop-Job` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b138a-154">You can use the name to identify the job to other job cmdlets, such as the `Stop-Job` cmdlet.</span></span>

<span data-ttu-id="b138a-155">Det egna standardnamnet är "Job #", där "#" är ett ordnings tal som ökar för varje jobb.</span><span class="sxs-lookup"><span data-stu-id="b138a-155">The default friendly name is "Job#", where "#" is an ordinal number that is incremented for each job.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b138a-156">– Script block</span><span class="sxs-lookup"><span data-stu-id="b138a-156">-ScriptBlock</span></span>

<span data-ttu-id="b138a-157">Anger vilka kommandon som ska köras i bakgrunds jobbet.</span><span class="sxs-lookup"><span data-stu-id="b138a-157">Specifies the commands to run in the background job.</span></span> <span data-ttu-id="b138a-158">Omge kommandoen med klammerparenteser ( `{}` ) för att skapa ett skript block.</span><span class="sxs-lookup"><span data-stu-id="b138a-158">Enclose the commands in braces (`{}`) to create a script block.</span></span> <span data-ttu-id="b138a-159">Använd den `$Input` automatiska variabeln för att få åtkomst till värdet för parametern **InputObject** .</span><span class="sxs-lookup"><span data-stu-id="b138a-159">Use the `$Input` automatic variable to access the value of the **InputObject** parameter.</span></span> <span data-ttu-id="b138a-160">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="b138a-160">This parameter is required.</span></span>

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b138a-161">-StreamingHost</span><span class="sxs-lookup"><span data-stu-id="b138a-161">-StreamingHost</span></span>

<span data-ttu-id="b138a-162">Den här parametern ger ett tråd säkert sätt att låta `Write-Host` utdata gå direkt till det skickade **PSHost** -objektet.</span><span class="sxs-lookup"><span data-stu-id="b138a-162">This parameter provides a thread safe way to allow `Write-Host` output to go directly to the passed in **PSHost** object.</span></span> <span data-ttu-id="b138a-163">Utan det `Write-Host` går utdata till data ström samlingen för jobb information och visas inte i en värd konsol förrän jobben har körts.</span><span class="sxs-lookup"><span data-stu-id="b138a-163">Without it, `Write-Host` output goes to the job information data stream collection and doesn't appear in a host console until after the jobs finish running.</span></span>

```yaml
Type: System.Management.Automation.Host.PSHost
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b138a-164">-ThrottleLimit</span><span class="sxs-lookup"><span data-stu-id="b138a-164">-ThrottleLimit</span></span>

<span data-ttu-id="b138a-165">Den här parametern begränsar antalet jobb som körs samtidigt.</span><span class="sxs-lookup"><span data-stu-id="b138a-165">This parameter limits the number of jobs running at one time.</span></span> <span data-ttu-id="b138a-166">När jobben startas placeras de i kö och väntar tills en tråd är tillgänglig i trådpoolen för att köra jobbet.</span><span class="sxs-lookup"><span data-stu-id="b138a-166">As jobs are started, they are queued and wait until a thread is available in the thread pool to run the job.</span></span> <span data-ttu-id="b138a-167">Standard gränsen är 5 trådar.</span><span class="sxs-lookup"><span data-stu-id="b138a-167">The default limit is 5 threads.</span></span>

<span data-ttu-id="b138a-168">Storleken på trådpoolen är global till PowerShell-sessionen.</span><span class="sxs-lookup"><span data-stu-id="b138a-168">The thread pool size is global to the PowerShell session.</span></span> <span data-ttu-id="b138a-169">Om du anger en **ThrottleLimit** i ett anrop anges gränsen för efterföljande anrop i samma session.</span><span class="sxs-lookup"><span data-stu-id="b138a-169">Specifying a **ThrottleLimit** in one call sets the limit for subsequent calls in the same session.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: 5
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="b138a-170">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b138a-170">CommonParameters</span></span>

<span data-ttu-id="b138a-171">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b138a-171">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b138a-172">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b138a-172">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b138a-173">INDATA</span><span class="sxs-lookup"><span data-stu-id="b138a-173">INPUTS</span></span>

### <span data-ttu-id="b138a-174">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="b138a-174">System.Management.Automation.PSObject</span></span>

## <span data-ttu-id="b138a-175">UTDATA</span><span class="sxs-lookup"><span data-stu-id="b138a-175">OUTPUTS</span></span>

### <span data-ttu-id="b138a-176">ThreadJob.ThreadJob</span><span class="sxs-lookup"><span data-stu-id="b138a-176">ThreadJob.ThreadJob</span></span>

## <span data-ttu-id="b138a-177">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="b138a-177">NOTES</span></span>

## <span data-ttu-id="b138a-178">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="b138a-178">RELATED LINKS</span></span>

[<span data-ttu-id="b138a-179">Start – jobb</span><span class="sxs-lookup"><span data-stu-id="b138a-179">Start-Job</span></span>](../Microsoft.PowerShell.Core/Start-Job.md)

[<span data-ttu-id="b138a-180">Stoppa – jobb</span><span class="sxs-lookup"><span data-stu-id="b138a-180">Stop-Job</span></span>](../Microsoft.PowerShell.Core/Stop-Job.md)

[<span data-ttu-id="b138a-181">Mottagning – jobb</span><span class="sxs-lookup"><span data-stu-id="b138a-181">Receive-Job</span></span>](../Microsoft.PowerShell.Core/Receive-Job.md)
