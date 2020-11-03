---
description: Innehåller information om PowerShell Thread-baserade jobb. Ett tråd jobb är en typ av bakgrunds jobb som kör ett kommando eller uttryck i en separat tråd i den aktuella sessionen.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/16/2020
online version: 1.0.0
schema: 2.0.0
title: about_Thread_Jobs
ms.openlocfilehash: 4951ac2c14c0685fbf2ead16bc52c64096231260
ms.sourcegitcommit: 108686b166672cc08817c637dd93eb1ad830511d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/17/2020
ms.locfileid: "93272972"
---
# <a name="about-thread-jobs"></a>Om tråd jobb

## <a name="short-description"></a>Kort beskrivning

Innehåller information om PowerShell Thread-baserade jobb. Ett tråd jobb är en typ av bakgrunds jobb som kör ett kommando eller uttryck i en separat tråd i den aktuella sessionen.

## <a name="long-description"></a>Lång beskrivning

Den här artikeln beskriver hur du kör tråd jobb i PowerShell på en lokal dator.
Information om hur du kör bakgrunds jobb på en lokal dator finns [about_Jobs](about_Jobs.md).

Starta ett tråd jobb med hjälp av `Start-ThreadJob` cmdleten. Denna cmdlet är tillgänglig i **ThreadJob** -modulen som levereras med PowerShell.
`Start-ThreadJob` Returnerar ett enskilt jobb objekt som kapslar in kommandot eller skriptet som körs och kan användas med alla PowerShell-jobb som manipulerar-cmdletar.

## <a name="the-job-cmdlets"></a>Jobb-cmdletar

|Cmdlet           |Beskrivning                                            |
|-----------------|-------------------------------------------------------|
|`Start-ThreadJob`|Startar ett tråd jobb på en lokal dator.               |
|`Get-Job`        |Hämtar de jobb som startades i den aktuella sessionen.|
|`Receive-Job`    |Hämtar resultatet av jobb.                              |
|`Stop-Job`       |Stoppar ett pågående jobb.                                   |
|`Wait-Job`       |Ignorerar kommando tolken tills ett eller flera jobb|
|                 |full.                                              |
|`Remove-Job`     |Tar bort ett jobb.                                         |

## <a name="how-to-start-a-thread-job-on-the-local-computer"></a>Så här startar du ett tråd jobb på den lokala datorn

Om du vill starta ett tråd jobb på den lokala datorn använder du `Start-ThreadJob` cmdleten.

Om du vill skriva ett `Start-ThreadJob` kommando, omger du kommandot eller skriptet som jobbet körs inom klammerparenteser ( `{ }` ).

Följande kommando startar ett tråd jobb som kör ett `Get-Process` kommando på den lokala datorn.

```powershell
Start-ThreadJob -ScriptBlock { Get-Process }
```

`Start-ThreadJob`Kommandot returnerar ett `ThreadJob` objekt som representerar det jobb som körs. Jobbobjektet innehåller användbar information om jobbet, inklusive dess aktuella status för körning. Resultatet av jobbet samlas in när resultatet genereras.

## <a name="how-to-wait-for-a-job-to-complete-and-retrieve-job-results"></a>Vänta tills ett jobb har slutförts och hämta jobb resultat

Du kan använda PowerShell-jobbets cmdlets, till exempel `Wait-Job` och `Receive-Job` för att vänta tills ett jobb har slutförts och sedan returnera alla resultat som genereras av jobbet.

Följande kommando startar ett tråd jobb som kör ett `Get-Process` kommando och väntar sedan på att kommandot ska slutföras och returnerar slutligen alla data resultat som genereras av kommandot.

```powershell
Start-ThreadJob -ScriptBlock { Get-Process } | Wait-Job | Receive-Job
```

## <a name="powershell-concurrency-and-jobs"></a>PowerShell-samtidighet och jobb

PowerShell kör kommandon och skript via jobb samtidigt. Det finns tre jobbbaserade lösningar som tillhandahålls av PowerShell för att stödja samtidighet.

|Jobb            |Beskrivning                                                  |
|---------------|-------------------------------------------------------------|
|`RemoteJob`    |Kommando och skript körs på en fjärrdator.                 |
|`BackgroundJob`|Kommando och skript körs i en separat process på den lokala    |
|               |datorspecifika.                                                     |
|`ThreadJob`    |Kommando och skript körs i en separat tråd inom samma  |
|               |processen på den lokala datorn.                                |

Varje typ av jobb har fördelar och nack delar. Att köra skript på en annan dator eller i en separat process har en bra isolering. Eventuella fel påverkar inte andra jobb som körs eller klienten som startade jobbet. Men Remoting-lagret lägger till overhead, inklusive objekt serialisering. Alla objekt som skickas till och från fjärrsessionen måste serialiseras och sedan avserialiseras i takt med att den passerar mellan klienten och mål sessionen. Serialiserings åtgärden kan använda många beräknings-och minnes resurser för stora komplexa data objekt.

## <a name="powershell-thread-based-jobs"></a>PowerShell Thread-baserade jobb

Trådbaserade jobb är inte lika robusta som fjärr-och bakgrunds jobb eftersom de körs i samma process på olika trådar. Om ett jobb har ett kritiskt fel som gör att processen kraschar, kommer alla andra jobb i processen också att Miss sen.

Trådbaserade jobb har dock mycket mindre kostnader. De behöver inte använda Remoting-lagret eller serialiseringen. Resultatet är att trådbaserade jobb ofta körs mycket snabbare och använder mycket mindre resurser än andra jobb typer.

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
10457.962


(Measure-Command {
    1..1000 | ForEach-Object { "Hello: $_" }
}).TotalMilliseconds
24.9277
```

I det första exemplet ovan visas en förgrunds slinga som skapar 1000 tråd jobb för att göra en enkel sträng skrivning. På grund av jobb omkostnader tar det över 33 sekunder att slutföra.

Det andra exemplet kör `ForEach` cmdleten för att utföra samma 1000-åtgärder och varje sträng skrivning körs sekventiellt utan någon jobb kostnad. Det slutförs med 25 millisekunder.

```powershell
$logNames.count
10

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

I exemplet ovan samlas upp till 5000 poster upp för 10 separata system loggar. Eftersom skriptet kräver läsning av ett antal loggar, är det klokt att utföra åtgärderna parallellt. Och jobbet slutförs över två gånger så snabbt som när skriptet körs sekventiellt.

```powershell
Measure-Command {
    $logs = $logNames | ForEach-Object {
        Get-WinEvent -LogName $_ -MaxEvents 5000 2>$null
    }
}

TotalMilliseconds : 252398.4321 (4 minutes 12 seconds)
$logs.Count
50000
```

## <a name="thread-jobs-and-variables"></a>Tråd jobb och variabler

Variabler överförs till tråd jobb på olika sätt.

`Start-ThreadJob` kan acceptera variabler som är skickas till cmdleten, skickas till-skript blocket via `$using` nyckelordet eller skickas via parametern **argument List** .

```powershell
$msg = "Hello"

$msg | Start-ThreadJob { $input | Write-Output } | Wait-Job | Receive-Job

Start-ThreadJob { Write-Output $using:msg } | Wait-Job | Receive-Job

Start-ThreadJob { param ([string] $message) Write-Output $message } -ArgumentList @($msg) |
  Wait-Job | Receive-Job
```

Eftersom tråd jobb körs i samma process, måste alla typer av variabel referenser som skickas till jobbet behandlas noggrant. Om det inte är ett tråd säkert objekt ska det aldrig tilldelas, och metod och egenskaper ska aldrig anropas på den.

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

Exemplet ovan skickar ett tråd säkert dotNet- `ConcurrentDictionary` objekt till alla underordnade jobb för att samla in unika namngivna process objekt. Eftersom det är ett tråd säkert objekt kan det användas på ett säkert sätt medan jobben körs samtidigt i processen.

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
