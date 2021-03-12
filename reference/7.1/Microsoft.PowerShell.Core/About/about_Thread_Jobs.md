---
description: Innehåller information om PowerShell Thread-baserade jobb. Ett tråd jobb är en typ av bakgrunds jobb som kör ett kommando eller uttryck i en separat tråd i den aktuella sessionen.
Locale: en-US
ms.date: 11/11/2020
schema: 2.0.0
title: about_Thread_Jobs
ms.openlocfilehash: 67f3fc585a8c2d1c3ca98c7336a7e367ed6c66c7
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2021
ms.locfileid: "103194251"
---
# <a name="about-thread-jobs"></a>Om tråd jobb

## <a name="short-description"></a>Kort beskrivning

Innehåller information om PowerShell Thread-baserade jobb. Ett tråd jobb är en typ av bakgrunds jobb som kör ett kommando eller uttryck i en separat tråd i den aktuella sessionen.

## <a name="long-description"></a>Lång beskrivning

PowerShell kör kommandon och skript via jobb samtidigt. Det finns tre typer av jobb som tillhandahålls av PowerShell för att stödja samtidighet.

- `RemoteJob` -Kommandon och skript körs i en fjärran sluten session. Mer information finns i [about_Remote_Jobs](about_Remote_Jobs.md).
- `BackgroundJob` -Kommandon och skript körs i en separat process på den lokala datorn. Mer information finns i artikeln [om jobb](about_Jobs.md).
- `PSTaskJob` eller `ThreadJob` -kommandon och skript körs i en separat tråd i samma process på den lokala datorn.

Trådbaserade jobb är inte lika robusta som fjärr-och bakgrunds jobb eftersom de körs i samma process på olika trådar. Om ett jobb har ett kritiskt fel som låser processen avslutas alla andra jobb i processen.

Trådbaserade jobb kräver dock mindre kostnader. De använder inte Remoting-skiktet eller serialiseringen. Resultat objekt returneras som referenser till Live-objekt i den aktuella sessionen. Utan den här omkostnaderna körs trådbaserade jobb snabbare och använder färre resurser än andra jobb typer.

> [!IMPORTANT]
> Den överordnade sessionen som skapade jobbet övervakar också jobb statusen och samlar in pipeline-data. Det underordnade jobbets process avslutas av den överordnade processen när jobbet når ett slutfört tillstånd. Om den överordnade sessionen avbryts avbryts alla pågående underordnade jobb tillsammans med deras underordnade processer.

Det finns två sätt att komma runt den här situationen:

1. Används `Invoke-Command` för att skapa jobb som körs i frånkopplade sessioner. Mer information finns i [about_Remote_Jobs](about_Remote_Jobs.md).
1. Använd `Start-Process` för att skapa en ny process i stället för ett jobb. Mer information finns i [Start process](xref:Microsoft.PowerShell.Management.Start-Process).

## <a name="how-to-start-and-manage-thread-based-jobs"></a>Starta och hantera trådbaserade jobb

Det finns två sätt att starta trådbaserade jobb:

- `Start-ThreadJob` – från **ThreadJob** -modulen
- `ForEach-Object -Parallel -AsJob` -Parallel-funktionen har lagts till i PowerShell 7,0

Använd samma **jobb** -cmdlets som beskrivs i [about_Jobs](about_Jobs.md) för att hantera trådbaserade jobb.

### <a name="using-start-threadjob"></a>Använda `Start-ThreadJob`

**ThreadJob** -modulen levererades först med PowerShell 6. Den kan också installeras från PowerShell-galleriet för Windows PowerShell 5,1.

Om du vill starta ett tråd jobb på den lokala datorn använder du `Start-ThreadJob` cmdleten med ett kommando eller ett skript som omges av klammerparenteser ( `{ }` ).

I följande exempel startar ett tråd jobb som kör ett `Get-Process` kommando på den lokala datorn.

```powershell
Start-ThreadJob -ScriptBlock { Get-Process }
```

`Start-ThreadJob`Kommandot returnerar ett `ThreadJob` objekt som representerar det jobb som körs. Jobbobjektet innehåller användbar information om jobbet, inklusive dess aktuella status för körning. Resultatet av jobbet samlas in när resultatet genereras.

### <a name="using-foreach-object--parallel--asjob"></a>Använda `ForEach-Object -Parallel -AsJob`

PowerShell 7,0 har lagt till en ny parameter uppsättning till `ForEach-Object` cmdleten. Med de nya parametrarna kan du köra skript block i parallella trådar som PowerShell-jobb.

Du kan skicka pipe-data till `ForEach-Object -Parallel` . Data skickas till skript blocket som körs parallellt. `-AsJob`Parametern skapar jobb objekt för var och en av de parallella trådarna.

Följande kommando startar ett jobb som innehåller underordnade jobb för varje indatavärde skickas till kommandot. Varje underordnat jobb kör `Write-Output` kommandot med ett skickas-indatavärde som argument.

```powershell
1..5 | ForEach-Object -Parallel { Write-Output $_ } -AsJob
```

`ForEach-Object -Parallel`Kommandot returnerar ett `PSTaskJob` objekt som innehåller underordnade jobb för varje skickas-indatavärde. Jobbobjektet innehåller användbar information om de underordnade jobb som kör status. Resultatet av de underordnade jobben samlas in när resultaten genereras.

## <a name="how-to-wait-for-a-job-to-complete-and-retrieve-job-results"></a>Vänta tills ett jobb har slutförts och hämta jobb resultat

Du kan använda PowerShell-jobbets cmdlets, till exempel `Wait-Job` och `Receive-Job` för att vänta tills ett jobb har slutförts och sedan returnera alla resultat som genereras av jobbet.

Följande kommando startar ett tråd jobb som kör ett `Get-Process` kommando och väntar sedan på att kommandot ska slutföras och returnerar slutligen alla data resultat som genereras av kommandot.

```powershell
Start-ThreadJob -ScriptBlock { Get-Process } | Wait-Job | Receive-Job
```

Följande kommando startar ett jobb som kör ett `Write-Output` kommando för varje skickas-indata och väntar sedan på att alla underordnade jobb ska slutföras och returnerar slutligen alla data resultat som har genererats av de underordnade jobben.

```powershell
1..5 | ForEach-Object -Parallel { Write-Output $_ } -AsJob | Wait-Job | Receive-Job
```

`Receive-Job`Cmdleten returnerar resultatet av de underordnade jobben.

```powershell
1
3
2
4
5
```

Eftersom varje underordnat jobb körs parallellt, garanteras inte ordningen på de genererade resultaten.

## <a name="thread-job-performance"></a>Prestanda för tråd jobb

Tråd jobb är snabbare och lättare att få högre vikt än andra typer av jobb. Men de har fortfarande överkapaciteter som kan vara stora jämfört med arbete som utförs av jobbet.

PowerShell kör kommandon och skript i en session. Endast ett kommando eller skript kan köras i taget i en session. När du kör flera jobb körs varje jobb i en separat session. Varje session bidrar till omkostnaderna.

Tråd jobb ger bästa möjliga prestanda när det arbete de utför är större än omkostnaderna för den session som används för att köra jobbet. Det finns två fall som uppfyller det här kriteriet.

- Arbetet är en beräknings intensiv körning av ett skript på flera tråd jobb kan dra nytta av flera processor kärnor och bli snabbare.

- Arbetet består av betydande vänte läge – ett skript som lägger tid på att vänta på I/O-eller fjärran rop-resultat. Att köra parallellt är vanligt vis snabbare än om de körs sekventiellt.

```powershell
(Measure-Command {
    1..1000 | ForEach { Start-ThreadJob { Write-Output "Hello $using:_" } } | Receive-Job -Wait
}).TotalMilliseconds
36860.8226

(Measure-Command {
    1..1000 | ForEach-Object { "Hello: $_" }
}).TotalMilliseconds
7.1975
```

I det första exemplet ovan visas en förgrunds slinga som skapar 1000 tråd jobb för att göra en enkel sträng skrivning. På grund av jobb omkostnader tar det över 36 sekunder att slutföra.

Det andra exemplet kör `ForEach` cmdleten för att utföra samma 1000-åtgärder.
Den här gången `ForEach-Object` körs i tur och ordning på en enda tråd, utan någon jobb kostnad. Den slutförs på bara 7 millisekunder.

I följande exempel samlas upp till 5000 poster upp för 10 separata system loggar. Eftersom skriptet kräver läsning av ett antal loggar, är det klokt att utföra åtgärderna parallellt.

```powershell
$logNames.count
10

Measure-Command {
    $logs = $logNames | ForEach-Object {
        Get-WinEvent -LogName $_ -MaxEvents 5000 2>$null
    }
}

TotalMilliseconds : 252398.4321 (4 minutes 12 seconds)
$logs.Count
50000
```

Skriptet slutförs på hälften av den tidpunkt då jobben körs parallellt.

```powershell
Measure-Command {
    $logs = $logNames | ForEach {
        Start-ThreadJob {
            Get-WinEvent -LogName $using:_ -MaxEvents 5000 2>$null
        } -ThrottleLimit 10
    } | Wait-Job | Receive-Job
}

TotalMilliseconds : 115994.3 (1 minute 56 seconds)
$logs.Count
50000
```

## <a name="thread-jobs-and-variables"></a>Tråd jobb och variabler

Det finns flera sätt att skicka värden till trådbaserade jobb.

`Start-ThreadJob` kan acceptera variabler som är skickas till cmdleten, skickas till-skript blocket via `$using` nyckelordet eller skickas via parametern **argument List** .

```powershell
$msg = "Hello"

$msg | Start-ThreadJob { $input | Write-Output } | Wait-Job | Receive-Job

Start-ThreadJob { Write-Output $using:msg } | Wait-Job | Receive-Job

Start-ThreadJob { param ([string] $message) Write-Output $message } -ArgumentList @($msg) |
  Wait-Job | Receive-Job
```

`ForEach-Object -Parallel` accepterar skickas i variabler och variabler som skickas direkt till-skript blocket via `$using` nyckelordet.

```powershell
$msg = "Hello"

$msg | ForEach-Object -Parallel { Write-Output $_ } -AsJob | Wait-Job | Receive-Job

1..1 | ForEach-Object -Parallel { Write-Output $using:msg } -AsJob | Wait-Job | Receive-Job
```

Eftersom tråd jobb körs i samma process, måste alla typer av variabel referenser som skickas till jobbet behandlas noggrant. Om det inte är ett tråd säkert objekt ska det aldrig tilldelas, och metod och egenskaper ska aldrig anropas på den.

I följande exempel skickas ett tråd säkert .NET- `ConcurrentDictionary` objekt till alla underordnade jobb för att samla in unika namngivna process objekt. Eftersom det är ett tråd säkert objekt kan det användas på ett säkert sätt medan jobben körs samtidigt i processen.

```powershell
$threadSafeDictionary = [System.Collections.Concurrent.ConcurrentDictionary[string,object]]::new()
$jobs = Get-Process | ForEach {
    Start-ThreadJob {
        $proc = $using:_
        $dict = $using:threadSafeDictionary
        $dict.TryAdd($proc.ProcessName, $proc)
    }
}
$jobs | Wait-Job | Receive-Job

$threadSafeDictionary.Count
96

$threadSafeDictionary["pwsh"]

NPM(K)  PM(M)   WS(M) CPU(s)    Id SI ProcessName
------  -----   ----- ------    -- -- -----------
  112  108.25  124.43  69.75 16272  1 pwsh
```

## <a name="see-also"></a>Se även

- [about_Remote_Jobs](about_Remote_Jobs.md)
- [about_Thread_Jobs](about_Thread_Jobs.md)
- [about_Job_Details](about_Job_Details.md)
- [about_Remote](about_Remote.md)
- [about_PSSessions](about_PSSessions.md)
- [Start – jobb](xref:Microsoft.PowerShell.Core.Start-Job)
- [Hämta jobb](xref:Microsoft.PowerShell.Core.Get-Job)
- [Mottagning – jobb](xref:Microsoft.PowerShell.Core.Receive-Job)
- [Stoppa – jobb](xref:Microsoft.PowerShell.Core.Stop-Job)
- [Wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job)
- [Ta bort – jobb](xref:Microsoft.PowerShell.Core.Remove-Job)
