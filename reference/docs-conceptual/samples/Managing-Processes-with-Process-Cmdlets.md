---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Hantera processer med Process-cmdletar
ms.openlocfilehash: 0962290327a02141f582acdf168143dee14ac60a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030187"
---
# <a name="managing-processes-with-process-cmdlets"></a><span data-ttu-id="a6c5d-103">Hantera processer med Process-cmdletar</span><span class="sxs-lookup"><span data-stu-id="a6c5d-103">Managing Processes with Process Cmdlets</span></span>

<span data-ttu-id="a6c5d-104">Du kan använda process-cmdletar i Windows PowerShell för att hantera lokala och fjärranslutna processer i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a6c5d-104">You can use the Process cmdlets in Windows PowerShell to manage local and remote processes in Windows PowerShell.</span></span>

## <a name="getting-processes-get-process"></a><span data-ttu-id="a6c5d-105">Hämtar processer (Get-process)</span><span class="sxs-lookup"><span data-stu-id="a6c5d-105">Getting Processes (Get-Process)</span></span>

<span data-ttu-id="a6c5d-106">Kör en **Get-process** utan parametrar för att hämta processerna som körs på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="a6c5d-106">To get the processes running on the local computer, run a **Get-Process** with no parameters.</span></span>

<span data-ttu-id="a6c5d-107">Du kan hämta specifika processer genom att ange deras process namn eller process-ID.</span><span class="sxs-lookup"><span data-stu-id="a6c5d-107">You can get particular processes by specifying their process names or process IDs.</span></span> <span data-ttu-id="a6c5d-108">Följande kommando hämtar inaktiva processen:</span><span class="sxs-lookup"><span data-stu-id="a6c5d-108">The following command gets the Idle process:</span></span>

```
PS> Get-Process -id 0

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
      0       0        0         16     0               0 Idle
```

<span data-ttu-id="a6c5d-109">Även om det är normalt för cmdlets att returnera inga data i vissa situationer, genererar **Get-process** ett fel om den inte hittar några matchningar, eftersom den vanliga avsikten är att hämta en känd process som körs.</span><span class="sxs-lookup"><span data-stu-id="a6c5d-109">Although it is normal for cmdlets to return no data in some situations, when you specify a process by its ProcessId, **Get-Process** generates an error if it finds no matches, because the usual intent is to retrieve a known running process.</span></span> <span data-ttu-id="a6c5d-110">Om det inte finns någon process med detta ID är det troligt att ID: t är felaktigt eller att ränte processen redan har avslut ATS:</span><span class="sxs-lookup"><span data-stu-id="a6c5d-110">If there is no process with that Id, it is likely that the Id is incorrect or that the process of interest has already exited:</span></span>

```
PS> Get-Process -Id 99

Get-Process : No process with process ID 99 was found.
At line:1 char:12
+ Get-Process  <<<< -Id 99
```

<span data-ttu-id="a6c5d-111">Du kan använda name-parametern i cmdleten Get-process för att ange en delmängd av processerna baserat på processens namn.</span><span class="sxs-lookup"><span data-stu-id="a6c5d-111">You can use the Name parameter of the Get-Process cmdlet to specify a subset of processes based on the process name.</span></span> <span data-ttu-id="a6c5d-112">Parametern name kan ta flera namn i en kommaavgränsad lista och den stöder användning av jokertecken, så du kan skriva namn mönster.</span><span class="sxs-lookup"><span data-stu-id="a6c5d-112">The Name parameter can take multiple names in a comma-separated list and it supports the use of wildcards, so you can type name patterns.</span></span>

<span data-ttu-id="a6c5d-113">Följande kommando hämtar till exempel de namn som börjar med "ex".</span><span class="sxs-lookup"><span data-stu-id="a6c5d-113">For example, the following command gets process whose names begin with "ex."</span></span>

```
PS> Get-Process -Name ex*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    234       7     5572      12484   134     2.98   1684 EXCEL
    555      15    34500      12384   134   105.25    728 explorer
```

<span data-ttu-id="a6c5d-114">Eftersom .NET system. Diagnostics. process-klassen är grunden för Windows PowerShell-processer, följer några av de konventioner som används av system. Diagnostics. process.</span><span class="sxs-lookup"><span data-stu-id="a6c5d-114">Because the .NET System.Diagnostics.Process class is the foundation for Windows PowerShell processes, it follows some of the conventions used by System.Diagnostics.Process.</span></span> <span data-ttu-id="a6c5d-115">En av dessa konventioner är att process namnet för en körbar fil aldrig innehåller ". exe" i slutet av namnet på den körbara filen.</span><span class="sxs-lookup"><span data-stu-id="a6c5d-115">One of those conventions is that the process name for an executable never includes the ".exe" at the end of the executable name.</span></span>

<span data-ttu-id="a6c5d-116">**Get-process** accepterar också flera värden för parametern name.</span><span class="sxs-lookup"><span data-stu-id="a6c5d-116">**Get-Process** also accepts multiple values for the Name parameter.</span></span>

```
PS> Get-Process -Name exp*,power*

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    540      15    35172      48148   141    88.44    408 explorer
    605       9    30668      29800   155     7.11   3052 powershell
```

<span data-ttu-id="a6c5d-117">Du kan använda parametern ComputerName för Get-process för att få processer på fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="a6c5d-117">You can use the ComputerName parameter of Get-Process to get processes on remote computers.</span></span> <span data-ttu-id="a6c5d-118">Följande kommando hämtar till exempel PowerShell-processerna på den lokala datorn (representeras av "localhost") och på två fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="a6c5d-118">For example, the following command gets the PowerShell processes on the local computer (represented by "localhost") and on two remote computers.</span></span>

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server02

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    258       8    29772      38636   130            3700 powershell
    398      24    75988      76800   572            5816 powershell
    605       9    30668      29800   155     7.11   3052 powershell
```

<span data-ttu-id="a6c5d-119">Dator namnen är inte tydliga i den här vyn, men de lagras i egenskapen MachineName för de process objekt som Get-process returnerar.</span><span class="sxs-lookup"><span data-stu-id="a6c5d-119">The computer names are not evident in this display, but they are stored in the MachineName property of the process objects that Get-Process returns.</span></span> <span data-ttu-id="a6c5d-120">I följande kommando används format-Table-cmdleten för att Visa process-ID: t, ProcessName och MachineName-egenskaperna (ComputerName) för process objekt.</span><span class="sxs-lookup"><span data-stu-id="a6c5d-120">The following command uses the Format-Table cmdlet to display the process ID, ProcessName and MachineName (ComputerName) properties of the process objects.</span></span>

```
PS> Get-Process -Name PowerShell -ComputerName localhost, Server01, Server01 | Format-Table -Property ID, ProcessName, MachineName

  Id ProcessName MachineName
  -- ----------- -----------
3700 powershell  Server01
3052 powershell  Server02
5816 powershell  localhost
```

<span data-ttu-id="a6c5d-121">Detta mer komplexa kommando lägger till egenskapen MachineName till standard visningen av hämtnings processen.</span><span class="sxs-lookup"><span data-stu-id="a6c5d-121">This more complex command adds the MachineName property to the standard Get-Process display.</span></span>

```
PS> Get-Process powershell -ComputerName localhost, Server01, Server02 |
    Format-Table -Property Handles,
        @{Label="NPM(K)";Expression={[int]($_.NPM/1024)}},
        @{Label="PM(K)";Expression={[int]($_.PM/1024)}},
        @{Label="WS(K)";Expression={[int]($_.WS/1024)}},
        @{Label="VM(M)";Expression={[int]($_.VM/1MB)}},
        @{Label="CPU(s)";Expression={if ($_.CPU -ne $()){$_.CPU.ToString("N")}}},
        Id, ProcessName, MachineName -auto

Handles  NPM(K)  PM(K) WS(K) VM(M) CPU(s)  Id ProcessName  MachineName
-------  ------  ----- ----- ----- ------  -- -----------  -----------
    258       8  29772 38636   130         3700 powershell Server01
    398      24  75988 76800   572         5816 powershell localhost
    605       9  30668 29800   155 7.11    3052 powershell Server02
```

## <a name="stopping-processes-stop-process"></a><span data-ttu-id="a6c5d-122">Stoppa processer (Stop-process)</span><span class="sxs-lookup"><span data-stu-id="a6c5d-122">Stopping Processes (Stop-Process)</span></span>

<span data-ttu-id="a6c5d-123">Med Windows PowerShell får du flexibilitet för att visa processer, men vad händer om du stoppar en process?</span><span class="sxs-lookup"><span data-stu-id="a6c5d-123">Windows PowerShell gives you flexibility for listing processes, but what about stopping a process?</span></span>

<span data-ttu-id="a6c5d-124">Cmdleten **Stop process** tar ett namn eller ID för att ange en process som du vill stoppa.</span><span class="sxs-lookup"><span data-stu-id="a6c5d-124">The **Stop-Process** cmdlet takes a Name or Id to specify a process you want to stop.</span></span> <span data-ttu-id="a6c5d-125">Din möjlighet att stoppa processer beror på dina behörigheter.</span><span class="sxs-lookup"><span data-stu-id="a6c5d-125">Your ability to stop processes depends on your permissions.</span></span> <span data-ttu-id="a6c5d-126">Det går inte att stoppa vissa processer.</span><span class="sxs-lookup"><span data-stu-id="a6c5d-126">Some processes cannot be stopped.</span></span> <span data-ttu-id="a6c5d-127">Om du till exempel försöker stoppa inaktiva processer får du ett fel meddelande:</span><span class="sxs-lookup"><span data-stu-id="a6c5d-127">For example, if you try to stop the idle process, you get an error:</span></span>

```
PS> Stop-Process -Name Idle
Stop-Process : Process 'Idle (0)' cannot be stopped due to the following error:
 Access is denied
At line:1 char:13
+ Stop-Process  <<<< -Name Idle
```

<span data-ttu-id="a6c5d-128">Du kan också tvinga fram en fråga med **Confirm** -parametern.</span><span class="sxs-lookup"><span data-stu-id="a6c5d-128">You can also force prompting with the **Confirm** parameter.</span></span> <span data-ttu-id="a6c5d-129">Den här parametern är särskilt användbar om du använder ett jokertecken när du anger process namnet, eftersom det kan hända att du råkar matcha vissa processer som du inte vill stoppa:</span><span class="sxs-lookup"><span data-stu-id="a6c5d-129">This parameter is particularly useful if you use a wildcard when specifying the process name, because you may accidentally match some processes you do not want to stop:</span></span>

```
PS> Stop-Process -Name t*,e* -Confirm
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "explorer (408)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "taskmgr (4072)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):n
```

<span data-ttu-id="a6c5d-130">Det går att hantera komplexa processer med några av objekt filtrerings-cmdletarna.</span><span class="sxs-lookup"><span data-stu-id="a6c5d-130">Complex process manipulation is possible by using some of the object filtering cmdlets.</span></span> <span data-ttu-id="a6c5d-131">Eftersom ett process objekt har en svarande-egenskap som är sann när den inte längre svarar kan du stoppa alla program som inte svarar med följande kommando:</span><span class="sxs-lookup"><span data-stu-id="a6c5d-131">Because a Process object has a Responding property that is true when it is no longer responding, you can stop all nonresponsive applications with the following command:</span></span>

```powershell
Get-Process | Where-Object -FilterScript {$_.Responding -eq $false} | Stop-Process
```

<span data-ttu-id="a6c5d-132">Du kan använda samma metod i andra situationer.</span><span class="sxs-lookup"><span data-stu-id="a6c5d-132">You can use the same approach in other situations.</span></span> <span data-ttu-id="a6c5d-133">Anta till exempel att ett sekundärt meddelande fält program körs automatiskt när användare startar ett annat program.</span><span class="sxs-lookup"><span data-stu-id="a6c5d-133">For example, suppose a secondary notification area application automatically runs when users start another application.</span></span> <span data-ttu-id="a6c5d-134">Det kanske inte fungerar korrekt i Terminal Services-sessioner, men du vill fortfarande behålla det i sessioner som körs på den fysiska dator konsolen.</span><span class="sxs-lookup"><span data-stu-id="a6c5d-134">You may find that this does not work correctly in Terminal Services sessions, but you still want to keep it in sessions that run on the physical computer console.</span></span> <span data-ttu-id="a6c5d-135">Sessioner som är anslutna till den fysiska datorns dator har alltid sessions-ID 0, så du kan stoppa alla instanser av processen som finns i andra sessioner genom att använda **Where-Object** och processen, **SessionID**:</span><span class="sxs-lookup"><span data-stu-id="a6c5d-135">Sessions connected to the physical computer desktop always have a session ID of 0, so you can stop all instances of the process that are in other sessions by using **Where-Object** and the process, **SessionId**:</span></span>

```powershell
Get-Process -Name BadApp | Where-Object -FilterScript {$_.SessionId -neq 0} | Stop-Process
```

<span data-ttu-id="a6c5d-136">Cmdleten för att stoppa processen har ingen ComputerName-parameter.</span><span class="sxs-lookup"><span data-stu-id="a6c5d-136">The Stop-Process cmdlet does not have a ComputerName parameter.</span></span> <span data-ttu-id="a6c5d-137">Därför måste du använda cmdleten Invoke-Command för att köra kommandot Stop process på en fjärrdator.</span><span class="sxs-lookup"><span data-stu-id="a6c5d-137">Therefore, to run a stop process command on a remote computer, you need to use the Invoke-Command cmdlet.</span></span> <span data-ttu-id="a6c5d-138">Om du till exempel vill stoppa PowerShell-processen på fjärrdatorn Server01 skriver du:</span><span class="sxs-lookup"><span data-stu-id="a6c5d-138">For example, to stop the PowerShell process on the Server01 remote computer, type:</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Stop-Process Powershell}
```

## <a name="stopping-all-other-windows-powershell-sessions"></a><span data-ttu-id="a6c5d-139">Stoppa alla andra Windows PowerShell-sessioner</span><span class="sxs-lookup"><span data-stu-id="a6c5d-139">Stopping All Other Windows PowerShell Sessions</span></span>

<span data-ttu-id="a6c5d-140">Det kan ibland vara användbart att kunna stoppa alla andra Windows PowerShell-sessioner som körs, förutom den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="a6c5d-140">It may occasionally be useful to be able to stop all running Windows PowerShell sessions other than the current session.</span></span> <span data-ttu-id="a6c5d-141">Om en session använder för många resurser eller inte går att komma åt (den kan köras via fjärr anslutning eller i en annan fjärrskrivbordssession), kanske du inte kan stoppa den direkt.</span><span class="sxs-lookup"><span data-stu-id="a6c5d-141">If a session is using too many resources or is inaccessible (it may be running remotely or in another desktop session), you may not be able to directly stop it.</span></span> <span data-ttu-id="a6c5d-142">Om du försöker stoppa alla pågående sessioner kan den aktuella sessionen avslutas i stället.</span><span class="sxs-lookup"><span data-stu-id="a6c5d-142">If you try to stop all running sessions, however, the current session may be terminated instead.</span></span>

<span data-ttu-id="a6c5d-143">Varje Windows PowerShell-session har en miljö variabel i PID som innehåller ID: t för Windows PowerShell-processen.</span><span class="sxs-lookup"><span data-stu-id="a6c5d-143">Each Windows PowerShell session has an environment variable PID that contains the Id of the Windows PowerShell process.</span></span> <span data-ttu-id="a6c5d-144">Du kan kontrol lera $PID mot ID: t för varje session och endast Avsluta Windows PowerShell-sessioner som har ett annat ID. Följande pipeline-kommando gör detta och returnerar listan över avslutade sessioner (på grund av användningen av parametern **Passthru** ):</span><span class="sxs-lookup"><span data-stu-id="a6c5d-144">You can check the $PID against the Id of each session and terminate only Windows PowerShell sessions that have a different Id. The following pipeline command does this and returns the list of terminated sessions (because of the use of the **PassThru** parameter):</span></span>

```
PS> Get-Process -Name powershell | Where-Object -FilterScript {$_.Id -ne $PID} | Stop-Process -PassThru

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    334       9    23348      29136   143     1.03    388 powershell
    304       9    23152      29040   143     1.03    632 powershell
    302       9    20916      26804   143     1.03   1116 powershell
    335       9    25656      31412   143     1.09   3452 powershell
    303       9    23156      29044   143     1.05   3608 powershell
    287       9    21044      26928   143     1.02   3672 powershell
```

## <a name="starting-debugging-and-waiting-for-processes"></a><span data-ttu-id="a6c5d-145">Starta, felsöka och vänta på processer</span><span class="sxs-lookup"><span data-stu-id="a6c5d-145">Starting, Debugging, and Waiting for Processes</span></span>

<span data-ttu-id="a6c5d-146">Windows PowerShell levereras också med cmdlets för att starta (eller starta om), felsöka en process och vänta tills processen har slutförts innan du kör ett kommando.</span><span class="sxs-lookup"><span data-stu-id="a6c5d-146">Windows PowerShell also comes with cmdlets to start (or restart), debug a process, and wait for a process to complete before running a command.</span></span> <span data-ttu-id="a6c5d-147">Information om dessa cmdlets finns i hjälp avsnittet om cmdleten för varje cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a6c5d-147">For information about these cmdlets, see the cmdlet help topic for each cmdlet.</span></span>

## <a name="see-also"></a><span data-ttu-id="a6c5d-148">Se även</span><span class="sxs-lookup"><span data-stu-id="a6c5d-148">See Also</span></span>

- <span data-ttu-id="a6c5d-149">[Hämta process [m2]](https://technet.microsoft.com/en-us/library/27a05dbd-4b69-48a3-8d55-b295f6225f15)</span><span class="sxs-lookup"><span data-stu-id="a6c5d-149">[Get-Process [m2]](https://technet.microsoft.com/en-us/library/27a05dbd-4b69-48a3-8d55-b295f6225f15)</span></span>
- <span data-ttu-id="a6c5d-150">[Stop-process [m2]](https://technet.microsoft.com/en-us/library/12454238-9881-457a-bde4-fb6cd124deec)</span><span class="sxs-lookup"><span data-stu-id="a6c5d-150">[Stop-Process [m2]](https://technet.microsoft.com/en-us/library/12454238-9881-457a-bde4-fb6cd124deec)</span></span>
- [<span data-ttu-id="a6c5d-151">Start process</span><span class="sxs-lookup"><span data-stu-id="a6c5d-151">Start-Process</span></span>](https://technet.microsoft.com/en-us/library/41a7e43c-9bb3-4dc2-8b0c-f6c32962e72c)
- [<span data-ttu-id="a6c5d-152">Vänta-process</span><span class="sxs-lookup"><span data-stu-id="a6c5d-152">Wait-Process</span></span>](https://technet.microsoft.com/en-us/library/9222af7a-789d-4a09-aa90-09d7c256c799)
- [<span data-ttu-id="a6c5d-153">Fel sökning – process</span><span class="sxs-lookup"><span data-stu-id="a6c5d-153">Debug-Process</span></span>](https://technet.microsoft.com/en-us/library/eea1dace-3913-4dbd-b659-5a94a610eee1)
- [<span data-ttu-id="a6c5d-154">Invoke-kommando</span><span class="sxs-lookup"><span data-stu-id="a6c5d-154">Invoke-Command</span></span>](https://technet.microsoft.com/en-us/library/22fd98ba-1874-492e-95a5-c069467b8462)
