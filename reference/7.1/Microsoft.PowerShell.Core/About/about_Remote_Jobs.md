---
description: Beskriver hur du kör jobb på fjärrdatorer.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 11/11/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_jobs?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Jobs
ms.openlocfilehash: 470fecd5d8eb0ef567d5d68d6a0fa940b6c819db
ms.sourcegitcommit: aac365f7813756e16b59322832a904e703e0465b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/12/2020
ms.locfileid: "94524764"
---
# <a name="about-remote-jobs"></a>Om Fjärrjobb

## <a name="short-description"></a>Kort beskrivning
Beskriver hur du kör bakgrunds jobb på fjärrdatorer.

## <a name="detailed-description"></a>Detaljerad beskrivning

PowerShell kör kommandon och skript via jobb samtidigt. Det finns tre typer av jobb som tillhandahålls av PowerShell för att stödja samtidighet.

- `RemoteJob` -Kommandon och skript körs i en fjärran sluten session.
- `BackgroundJob` -Kommandon och skript körs i en separat process på den lokala datorn. Mer information finns i artikeln [om jobb](about_Jobs.md).
- `PSTaskJob` eller `ThreadJob` -kommandon och skript körs i en separat tråd i samma process på den lokala datorn. Mer information finns i [about_Thread_Jobs](/powershell/module/ThreadJob/about_Thread_Jobs).

Att köra skript på distans, på en separat dator eller i en separat process, ger bra isolering. Eventuella fel som inträffar i fjärrjobbet påverkar inte andra jobb som körs eller den överordnade sessionen som startade jobbet. Dock lägger dataremoting till overhead, inklusive objekt serialisering. Alla objekt serialiseras och avserialiseras när de skickas mellan den överordnade sessionen och fjärrsessionen (Job). Serialisering av stora komplexa data objekt kan förbruka stora mängder beräknings-och minnes resurser och överföra stora mängder data i nätverket.

> [!IMPORTANT]
> Den överordnade sessionen som skapade jobbet övervakar också jobb statusen och samlar in pipeline-data. Det underordnade jobbets process avslutas av den överordnade processen när jobbet når ett slutfört tillstånd. Om den överordnade sessionen avbryts avbryts alla pågående underordnade jobb tillsammans med deras underordnade processer.

Det finns två sätt att komma runt den här situationen:

1. Används `Invoke-Command` för att skapa jobb som körs i frånkopplade sessioner. Se avsnittet [frånkopplade processer](#how-to-run-as-a-detached-process) i den här artikeln.
1. Använd `Start-Process` för att skapa en ny process i stället för ett jobb. Mer information finns i [Start process](xref:Microsoft.PowerShell.Management.Start-Process).

## <a name="remote-jobs"></a>Fjärrjobb

Du kan köra jobb på fjärrdatorer genom att använda tre olika metoder.

- Starta en interaktiv session på en fjärran sluten dator. Starta sedan ett jobb i den interaktiva sessionen. Procedurerna är desamma som att köra ett lokalt jobb, även om alla åtgärder utförs på fjärrdatorn.

- Kör ett jobb på en fjärrdator som returnerar sina resultat till den lokala datorn. Använd den här metoden om du vill samla in resultatet av jobb och underhålla dem på en central plats på den lokala datorn.

- Kör ett jobb på en fjärrdator som underhåller sina resultat på fjärrdatorn. Använd den här metoden när jobb data är säkrare att behållas på den ursprungliga datorn.

### <a name="start-a-job-in-an-interactive-session"></a>Starta ett jobb i en interaktiv session

Du kan starta en interaktiv session med en fjärrdator och sedan starta ett jobb under den interaktiva sessionen. Mer information om interaktiva sessioner finns about_Remote och se `Enter-PSSession` .

Proceduren för att starta ett jobb i en interaktiv session är nästan identisk med proceduren för att starta ett bakgrunds jobb på den lokala datorn. Alla åtgärder sker dock på fjärrdatorn, inte på den lokala datorn.

1. Använd `Enter-PSSession` cmdleten för att starta en interaktiv session med en fjärran sluten dator. Du kan använda parametern ComputerName för `Enter-PSSession` för att upprätta en tillfällig anslutning för den interaktiva sessionen. Du kan också använda parametern session för att köra den interaktiva sessionen i en PowerShell-session (PSSession).

   Följande kommando startar en interaktiv session på Server01-datorn.

   ```powershell
   C:\PS> Enter-PSSession -computername Server01
   ```

   Kommando tolken ändras för att visa att du nu är ansluten till Server01-datorn.

   ```
   Server01\C:>
   ```

1. Om du vill starta ett Fjärrjobb i sessionen använder du `Start-Job` cmdleten. Följande kommando kör ett Fjärrjobb som hämtar händelserna i händelse loggen för Windows PowerShell på Server01-datorn. `Start-Job`Cmdleten returnerar ett objekt som representerar jobbet.

   Det här kommandot sparar jobbobjektet i `$job` variabeln.

   ```powershell
   Server01\C:> $job = Start-Job -scriptblock {
     Get-Eventlog "Windows PowerShell"
   }
   ```

   När jobbet körs kan du använda den interaktiva sessionen för att köra andra kommandon, inklusive andra jobb. Du måste dock låta den interaktiva sessionen vara öppen tills jobbet har slutförts. Om du slutar sessionen avbryts jobbet och resultaten går förlorade.

1. Om du vill ta reda på om jobbet är klart kan du Visa värdet för `$job` variabeln eller använda `Get-Job` cmdleten för att hämta jobbet. Följande kommando använder `Get-Job` cmdleten för att Visa jobbet.

   ```powershell
   Server01\C:> Get-Job $job

   SessionId  Name  State      HasMoreData  Location   Command
   ---------  ----  -----      -----------  --------   -------
   1          Job1  Complete   True         localhost  Get-Eventlog "Windows...
   ```

   `Get-Job`Utdata visar att jobbet körs på "localhost"-datorn eftersom jobbet startade och körs på samma dator (i det här fallet Server01).

1. Använd cmdleten för att hämta resultatet av jobbet `Receive-Job` . Du kan visa resultaten i den interaktiva sessionen eller spara dem till en fil på fjärrdatorn. Följande kommando hämtar resultatet av jobbet i variabeln $job. Kommandot använder operatorn för omdirigering ( `>` ) för att spara resultatet av jobbet i PsLog.txt-filen på Server01-datorn.

   ```powershell
   Server01\C:> Receive-Job $job > c:\logs\PsLog.txt
   ```

1. Använd cmdleten för att avsluta den interaktiva sessionen `Exit-PSSession` . Kommando tolken ändras för att visa att du är tillbaka i den ursprungliga sessionen på den lokala datorn.

   ```powershell
   Server01\C:> Exit-PSSession
   C:\PS>
   ```

1. Du kan visa innehållet i `PsLog.txt` filen på Server01-datorn när som helst genom att starta en annan interaktiv session eller köra ett fjärrkommando. Den här typen av kommando körs bäst i en PSSession (en permanent anslutning) om du vill använda flera kommandon för att undersöka och hantera data i `PsLog.txt` filen. Mer information om PSSessions finns i [about_PSSessions](about_PSSessions.md).

   Följande kommandon använder `New-PSSession` cmdleten för att skapa en **PSSession** som är ansluten till Server01-datorn, och de använder `Invoke-Command` cmdleten för att köra `Get-Content` ett kommando i PSSession för att visa innehållet i filen.

   ```powershell
   $s = New-PSSession -computername Server01
   Invoke-Command -session $s -scriptblock {
     Get-Content c:\logs\pslog.txt}
   ```

### <a name="start-a-remote-job-that-returns-the-results-to-the-local-computer-asjob"></a>Starta ett Fjärrjobb som returnerar resultatet till den lokala datorn (AsJob)

Om du vill starta ett jobb på en fjärrdator som returnerar kommando resultatet till den lokala datorn använder du parametern **AsJob** för en cmdlet, till exempel `Invoke-Command` cmdleten.

När du använder **AsJob** -parametern skapas jobbobjektet faktiskt på den lokala datorn även om jobbet körs på fjärrdatorn. När jobbet har slutförts returneras resultatet till den lokala datorn.

Du kan använda de cmdlet: ar som innehåller jobbet Substantiv (jobb-cmdletar) för att hantera alla jobb som skapats av en valfri cmdlet. Många av cmdletarna som har **AsJob** -parametrar använder inte PowerShell-fjärrkommunikation, så du kan använda dem även på datorer som inte har kon figurer ATS för fjärr kommunikation och som inte uppfyller kraven för fjärr kommunikation.

1. Följande kommando använder **AsJob** -parametern för `Invoke-Command` för att starta ett jobb på Server01-datorn. Jobbet kör ett `Get-Eventlog` kommando som hämtar händelserna i system loggen. Du kan använda parametern JobName för att tilldela ett visnings namn till jobbet.

   ```powershell
   Invoke-Command -computername Server01 -scriptblock {
     Get-Eventlog system} -AsJob
   ```

   Resultatet av kommandot liknar följande exempel på utdata.

   ```Output
   SessionId   Name   State    HasMoreData   Location   Command
   ---------   ----   -----    -----------   --------   -------
   1           Job1   Running  True          Server01   Get-Eventlog system
   ```

   När parametern **AsJob** används `Invoke-Command` returnerar samma typ av jobb objekt som `Start-Job` returneras. Du kan spara jobbobjektet i en variabel, eller så kan du använda ett `Get-Job` kommando för att hämta jobbet.

   Observera att värdet för egenskapen location visar att jobbet kördes på Server01-datorn.

1. Använd jobb-cmdletarna om du vill hantera ett jobb som har startats med hjälp av **AsJob** -parametern för `Invoke-Command` cmdleten. Eftersom jobbobjektet som representerar fjärrjobbet finns på den lokala datorn behöver du inte köra fjärrkommandon för att hantera jobbet.

   Ta reda på om jobbet har slutförts genom att använda ett `Get-Job` kommando. Följande kommando hämtar alla jobb som startades i den aktuella sessionen.

   ```powershell
   Get-Job
   ```

   Eftersom fjärrjobbet startade i den aktuella sessionen hämtar ett lokalt `Get-Job` kommando jobbet. Egenskapen State för jobbobjektet visar att kommandot slutfördes korrekt.

   ```Output
   SessionId   Name   State      HasMoreData   Location   Command
   ---------   ----   -----      -----------   --------   -------
   1           Job1   Completed  True          Server01   Get-Eventlog system
   ```

1. Använd cmdleten för att hämta resultatet av jobbet `Receive-Job` . Eftersom jobb resultaten automatiskt returneras till datorn där jobbobjektet finns kan du få resultatet med ett lokalt `Receive-Job` kommando.

   Följande kommando använder `Receive-Job` cmdleten för att hämta resultatet av jobbet. Den använder sessions-ID: t för att identifiera jobbet. Det här kommandot sparar jobb resultaten i variabeln $results. Du kan också omdirigera resultaten till en fil.

   ```powershell
   $results = Receive-Job -id 1
   ```

### <a name="start-a-remote-job-that-keeps-the-results-on-the-remote-computer"></a>Starta ett Fjärrjobb som behåller resultatet på fjärrdatorn

Om du vill starta ett jobb på en fjärrdator som behåller kommando resultatet på fjärrdatorn använder du `Invoke-Command` cmdleten för att köra ett `Start-Job` kommando på en fjärrdator. Du kan använda den här metoden för att köra jobb på flera datorer.

När du kör ett `Start-Job` kommando via fjärr anslutning skapas jobbobjektet på fjärrdatorn och jobb resultaten bevaras på fjärrdatorn.
Alla åtgärder är lokala, från jobbets perspektiv. Du kör bara kommandon via fjärr anslutning för att hantera ett lokalt jobb på fjärrdatorn.

1. Använd `Invoke-Command` cmdleten för att köra ett `Start-Job` kommando på en fjärrdator.

   Det här kommandot kräver en PSSession (en permanent anslutning). Om du använder parametern ComputerName för `Invoke-Command` att upprätta en tillfällig anslutning `Invoke-Command` anses kommandot vara slutfört när jobbobjektet returneras. Därför stängs den tillfälliga anslutningen och jobbet avbryts.

   Följande kommando använder `New-PSSession` cmdleten för att skapa en PSSession som är ansluten till Server01-datorn. Kommandot sparar PSSession i `$s` variabeln.

   ```powershell
   $s = New-PSSession -computername Server01
   ```

   Nästa kommando använder `Invoke-Command` cmdleten för att köra ett `Start-Job` kommando i PSSession. `Start-Job`Kommandot och `Get-Eventlog` kommandot omges av klammerparenteser.

   ```powershell
   Invoke-Command -session $s -scriptblock {
     Start-Job -scriptblock {Get-Eventlog system}}
   ```

   Resultatet liknar följande exempel på utdata.

   ```Output
   Id       Name    State      HasMoreData     Location   Command
   --       ----    -----      -----------     --------   -------
   2        Job2    Running    True            Localhost  Get-Eventlog system
   ```

   När du kör ett `Start-Job` fjärrkommando, `Invoke-Command` returnerar samma typ av jobb objekt som `Start-Job` returneras. Du kan spara jobbobjektet i en variabel, eller så kan du använda ett `Get-Job` kommando för att hämta jobbet.

   Observera att värdet för egenskapen **location** visar att jobbet kördes på den lokala datorn, vilket kallas "localhost", även om jobbet kördes på Server01-datorn. Eftersom jobbobjektet skapas på den Server01 datorn och jobbet körs på samma dator betraktas det som ett lokalt bakgrunds jobb.

1. Om du vill hantera ett Fjärrjobb använder du **jobb** -cmdletarna. Eftersom jobbobjektet finns på fjärrdatorn måste du köra fjärrkommandon för att få, stoppa, vänta eller hämta jobb resultaten.

   Om du vill se om jobbet är klart använder du ett `Invoke-Command` kommando för att köra ett `Get-Job` kommando i PSSession som är anslutet till Server01-datorn.

   ```powershell
   Invoke-Command -session $s -scriptblock {Get-Job}
   ```

   Kommandot returnerar ett jobb objekt. Egenskapen **State** för jobbobjektet visar att kommandot slutfördes korrekt.

   ```Output
   SessionId   Name  State      HasMoreData   Location   Command
   ---------   ----  -----      -----------   --------   -------
   2           Job2  Completed  True          LocalHost   Get-Eventlog system
   ```

1. Om du vill hämta resultatet av jobbet använder du `Invoke-Command` cmdleten för att köra ett `Receive-Job` kommando i PSSession som är anslutet till Server01-datorn.

   Följande kommando använder `Receive-Job` cmdleten för att hämta resultatet av jobbet. Den använder sessions-ID: t för att identifiera jobbet. Det här kommandot sparar jobb resultatet i `$results` variabeln. Parametern Keep to används för `Receive-Job` att behålla resultatet i jobbets cacheminne på fjärrdatorn.

   ```powershell
   $results = Invoke-Command -session $s -scriptblock {
     Receive-Job -SessionId 2 -Keep
   }
   ```

   Du kan också omdirigera resultatet till en fil på den lokala datorn eller fjärrdatorn.
   Följande kommando använder en omdirigerings operator för att spara resultatet i en fil på Server01-datorn.

   ```powershell
   Invoke-Command -session $s -command {
     Receive-Job -SessionId 2 > c:\logs\pslog.txt
   }
   ```

## <a name="how-to-run-as-a-detached-process"></a>Köra som en frånkopplad process

Som tidigare nämnts avslutas alla pågående underordnade jobb tillsammans med sina underordnade processer när den överordnade sessionen avslutas. Du kan använda fjärr kommunikation på den lokala datorn för att köra jobb som inte är kopplade till den aktuella PowerShell-sessionen.

Skapa en ny PowerShell-session på den lokala datorn. Används `Invoke-Command` för att starta ett jobb i den här sessionen. `Invoke-Command` gör att du kan koppla från en fjärran sluten session och avsluta den överordnade sessionen. Senare kan du starta en ny PowerShell-session och ansluta till den tidigare frånkopplade sessionen för att återuppta övervakningen av jobbet. Alla data som returnerades till den ursprungliga PowerShell-sessionen försvinner dock när sessionen avslutas. Det är bara nya data objekt som genereras efter från kopplingen som returneras vid åter anslutning.

```powershell
# Create remote session on local machine
PS> $session = New-PSSession -cn localhost

# Start remote job
PS> $job = Invoke-Command -Session $session -ScriptBlock { 1..60 | % { sleep 1; "Output $_" } } -AsJob
PS> $job

Id     Name     PSJobTypeName   State         HasMoreData     Location      Command
--     ----     -------------   -----         -----------     --------      -------
1      Job1     RemoteJob       Running       True            localhost     1..60 | % { sleep 1; ...

# Disconnect the job session
PS> Disconnect-PSSession $session

Id Name         Transport ComputerName    ComputerType    State         ConfigurationName     Availability
-- ----         --------- ------------    ------------    -----         -----------------     ------------
1 Runspace1     WSMan     localhost       RemoteMachine   Disconnected  Microsoft.PowerShell          None

PS> $job

Id     Name     PSJobTypeName   State         HasMoreData     Location      Command
--     ----     -------------   -----         -----------     --------      -------
1      Job1     RemoteJob       Disconnected  True            localhost     1..60 | % { sleep 1;

# Reconnect the session to a new job object
PS> $jobNew = Receive-PSSession -Session $session -OutTarget Job
PS> $job | Wait-Job | Receive-Job
Output 9
Output 10
Output 11
...
```

I det här exemplet är jobben fortfarande kopplade till en överordnad PowerShell-session.
Den överordnade sessionen är dock inte den ursprungliga PowerShell-sessionen där `Invoke-Command` kördes.

## <a name="see-also"></a>Se även

- [about_Jobs](about_Jobs.md)
- [about_Job_Details](about_Job_Details.md)
- [about_Remote](about_Remote.md)
- [about_Remote_Variables](about_Remote_Variables.md)
- [Invoke-kommando](xref:Microsoft.PowerShell.Core.Invoke-Command)
- [Start – jobb](xref:Microsoft.PowerShell.Core.Start-Job)
- [Hämta jobb](xref:Microsoft.PowerShell.Core.Get-Job)
- [Wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job)
- [Stoppa – jobb](xref:Microsoft.PowerShell.Core.Stop-Job)
- [Ta bort – jobb](xref:Microsoft.PowerShell.Core.Remove-Job)
- [New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)
- [Retur-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)
- [Avsluta-PSSession](xref:Microsoft.PowerShell.Core.Exit-PSSession)
