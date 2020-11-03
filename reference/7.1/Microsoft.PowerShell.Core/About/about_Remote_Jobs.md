---
description: Beskriver hur du kör bakgrunds jobb på fjärrdatorer.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 12/01/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_jobs?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote_Jobs
ms.openlocfilehash: fb2270ea5c0acdcf2c506e687787d22c73e2cb2c
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271689"
---
# <a name="about-remote-jobs"></a>Om Fjärrjobb

## <a name="short-description"></a>KORT BESKRIVNING
Beskriver hur du kör bakgrunds jobb på fjärrdatorer.

## <a name="detailed-description"></a>DETALJERAD BESKRIVNING

Ett bakgrunds jobb är ett kommando som körs asynkront utan att interagera med den aktuella sessionen. Kommando tolken returnerar omedelbart och du kan fortsätta att använda sessionen medan jobbet körs.

Som standard körs bakgrunds jobb på den lokala datorn. Du kan dock använda flera olika procedurer för att köra bakgrunds jobb på fjärrdatorer.

I det här avsnittet beskrivs hur du kör ett bakgrunds jobb på en fjärrdator. Information om hur du kör bakgrunds jobb på en lokal dator finns [about_Jobs](about_Jobs.md). Mer information om bakgrunds jobb finns [about_Job_Details](about_Job_Details.md).

## <a name="remote-background-jobs"></a>FJÄRRAN SLUTEN BAKGRUNDS JOBB

Du kan köra bakgrunds jobb på fjärrdatorer genom att använda tre olika metoder.

- Starta en interaktiv session med en fjärran sluten dator och starta ett jobb i den interaktiva sessionen. Procedurerna är desamma som att köra ett lokalt jobb, även om alla åtgärder utförs på fjärrdatorn.

- Kör ett bakgrunds jobb på en fjärrdator som returnerar sina resultat till den lokala datorn. Använd den här metoden när du vill samla in resultaten av bakgrunds jobb och underhålla dem på en central plats på den lokala datorn.

- Kör ett bakgrunds jobb på en fjärrdator som underhåller sina resultat på fjärrdatorn. Använd den här metoden när jobb data är säkrare att behållas på den ursprungliga datorn.

### <a name="start-a-background-job-in-an-interactive-session"></a>STARTA ETT BAKGRUNDS JOBB I EN INTERAKTIV SESSION

Du kan starta en interaktiv session med en fjärrdator och sedan starta ett bakgrunds jobb under den interaktiva sessionen. Mer information om interaktiva sessioner finns about_Remote och se Enter-PSSession.

Proceduren för att starta ett bakgrunds jobb i en interaktiv session är nästan identisk med proceduren för att starta ett bakgrunds jobb på den lokala datorn. Alla åtgärder sker dock på fjärrdatorn, inte på den lokala datorn.

#### <a name="step-1-enter-pssession"></a>STEG 1: ANGE-PSSESSION

Använd Enter-PSSession-cmdleten för att starta en interaktiv session med en fjärran sluten dator. Du kan använda parametern ComputerName i Enter-PSSession för att upprätta en tillfällig anslutning för den interaktiva sessionen. Du kan också använda parametern session för att köra den interaktiva sessionen i en PowerShell-session (PSSession).

Följande kommando startar en interaktiv session på Server01-datorn.

```powershell
C:\PS> Enter-PSSession -computername Server01
```

Kommando tolken ändras för att visa att du nu är ansluten till Server01-datorn.

```
Server01\C:>
```

#### <a name="step-2-start-job"></a>STEG 2: START-JOB

Om du vill starta ett bakgrunds jobb i sessionen använder du Start-Job cmdlet.

Följande kommando kör ett bakgrunds jobb som hämtar händelserna i händelse loggen för Windows PowerShell på Server01-datorn. Cmdleten Start-Job returnerar ett objekt som representerar jobbet.

Det här kommandot sparar jobbobjektet i jobb- \$ variabeln.

```powershell
Server01\C:> $job = start-job -scriptblock {
  get-eventlog "Windows PowerShell"
}
```

När jobbet körs kan du använda den interaktiva sessionen för att köra andra kommandon, inklusive andra bakgrunds jobb. Du måste dock låta den interaktiva sessionen vara öppen tills jobbet har slutförts. Om du slutar sessionen avbryts jobbet och resultaten går förlorade.

#### <a name="step-3-get-job"></a>STEG 3: HÄMTA JOBB

Om du vill ta reda på om jobbet har slutförts, visar du värdet för \$ jobb variabeln eller använder cmdleten Get-Job för att hämta jobbet. Följande kommando använder cmdleten Get-Job för att Visa jobbet.

```powershell
Server01\C:> get-job $job

SessionId  Name  State      HasMoreData  Location   Command
---------  ----  -----      -----------  --------   -------
1          Job1  Complete   True         localhost  get-eventlog "Windows...
```

Get-Job utdata visar att jobbet körs på "localhost"-datorn eftersom jobbet startade och körs på samma dator (i det här fallet Server01).

#### <a name="step-4-receive-job"></a>STEG 4: RECEIVE-JOB

Använd Receive-Job-cmdleten för att hämta resultatet av jobbet. Du kan visa resultaten i den interaktiva sessionen eller spara dem till en fil på fjärrdatorn. Följande kommando hämtar resultatet av jobbet i variabeln $job. Kommandot använder operatorn för omdirigering (>) för att spara resultatet av jobbet i PsLog.txt-filen på Server01-datorn.

```powershell
Server01\C:> receive-job $job > c:\logs\PsLog.txt
```

#### <a name="step-5-exit-pssession"></a>STEG 5: EXIT-PSSESSION

Använd Exit-PSSession-cmdleten om du vill avsluta den interaktiva sessionen. Kommando tolken ändras för att visa att du är tillbaka i den ursprungliga sessionen på den lokala datorn.

```powershell
Server01\C:> Exit-PSSession
C:\PS>
```

#### <a name="step-6-invoke-command-get-content"></a>STEG 6: INVOKE-COMMAND: GET-CONTENT

Om du vill visa innehållet i PsLog.txt-filen på Server01-datorn när som helst startar du en annan interaktiv session eller kör ett fjärrkommando. Den här typen av kommando körs bäst i en PSSession (en permanent anslutning) om du vill använda flera kommandon för att undersöka och hantera data i PsLog.txt-filen. Mer information om PSSessions finns i about_PSSessions.

Följande kommandon använder New-PSSession cmdlet för att skapa en PSSession som är ansluten till Server01-datorn, och de använder cmdleten Invoke-Command för att köra ett Get-Content kommando i PSSession för att visa innehållet i filen.

```powershell
$s = new-pssession -computername Server01
invoke-command -session $s -scriptblock {
  get-content c:\logs\pslog.txt}
```

### <a name="start-a-remote-job-that-returns-the-results-to-the-local-computer-asjob"></a>Starta ett Fjärrjobb som returnerar resultaten till den lokala datorn \( ASJOB\)

Om du vill starta ett bakgrunds jobb på en fjärrdator som returnerar kommando resultatet till den lokala datorn använder du parametern AsJob för en cmdlet som Invoke-Command-cmdlet.

När du använder AsJob-parametern skapas jobbobjektet faktiskt på den lokala datorn även om jobbet körs på fjärrdatorn. När jobbet har slutförts returneras resultatet till den lokala datorn.

Du kan använda de cmdlet: ar som innehåller jobbet Substantiv (jobb-cmdletar) för att hantera alla jobb som skapats av en valfri cmdlet. Många av cmdletarna som har AsJob-parametrar använder inte PowerShell-fjärrkommunikation, så du kan använda dem även på datorer som inte har kon figurer ATS för fjärr kommunikation och som inte uppfyller kraven för fjärr kommunikation.

#### <a name="step-1-invoke-command--asjob"></a>STEG 1: ANROPA-COMMAND-ASJOB

Följande kommando använder AsJob-parametern för Invoke-Command för att starta ett bakgrunds jobb på Server01-datorn. Jobbet kör ett Get-Eventlog-kommando som hämtar händelserna i system loggen. Du kan använda parametern JobName för att tilldela ett visnings namn till jobbet.

```powershell
invoke-command -computername Server01 -scriptblock {
  get-eventlog system} -asjob
```

Resultatet av kommandot liknar följande exempel på utdata.

```Output
SessionId   Name   State    HasMoreData   Location   Command
---------   ----   -----    -----------   --------   -------
1           Job1   Running  True          Server01   get-eventlog system
```

När parametern AsJob används returnerar Invoke-Command samma typ av jobb objekt som Start-Job returnerar. Du kan spara jobbobjektet i en variabel, eller så kan du använda ett Get-Job-kommando för att hämta jobbet.

Observera att värdet för egenskapen location visar att jobbet kördes på Server01-datorn.

#### <a name="step-2-get-job"></a>STEG 2: GET-JOB

Använd jobb-cmdletarna för att hantera ett jobb som har startats med hjälp av parametern AsJob i cmdleten Invoke-Command. Eftersom jobbobjektet som representerar fjärrjobbet finns på den lokala datorn behöver du inte köra fjärrkommandon för att hantera jobbet.

Använd ett Get-Job-kommando för att avgöra om jobbet har slutförts. Följande kommando hämtar alla jobb som startades i den aktuella sessionen.

```powershell
get-job
```

Eftersom fjärrjobbet startade i den aktuella sessionen hämtar ett lokalt Get-Job-kommando jobbet. Egenskapen State för jobbobjektet visar att kommandot slutfördes korrekt.

```Output
SessionId   Name   State      HasMoreData   Location   Command
---------   ----   -----      -----------   --------   -------
1           Job1   Completed  True          Server01   get-eventlog system
```

#### <a name="step-3-receive-job"></a>STEG 3: RECEIVE-JOB

Använd Receive-Job-cmdleten för att hämta resultatet av jobbet. Eftersom jobb resultaten automatiskt returneras till datorn där jobbobjektet finns kan du hämta resultatet med ett lokalt Receive-Job-kommando.

Följande kommando använder cmdleten Receive-Job för att hämta resultatet av jobbet. Den använder sessions-ID: t för att identifiera jobbet. Det här kommandot sparar jobb resultaten i variabeln $results. Du kan också omdirigera resultaten till en fil.

```powershell
$results = receive-job -id 1
```

### <a name="start-a-remote-job-that-keeps-the-results-on-the-remote-computer"></a>STARTA ETT FJÄRRJOBB SOM BEHÅLLER RESULTATET PÅ FJÄRRDATORN

Om du vill starta ett bakgrunds jobb på en fjärrdator som behåller kommando resultatet på fjärrdatorn, använder du Invoke-Command cmdlet för att köra ett Start-Job kommando på en fjärrdator. Du kan använda den här metoden för att köra bakgrunds jobb på flera datorer.

När du kör ett Start-Job-kommando via fjärr anslutning skapas jobbobjektet på fjärrdatorn och jobb resultaten bevaras på fjärrdatorn.
Alla åtgärder är lokala, från jobbets perspektiv. Du kör bara kommandon via fjärr anslutning för att hantera ett lokalt jobb på fjärrdatorn.

#### <a name="step-1-invoke-command-start-job"></a>STEG 1: INVOKE-KOMMANDOT START-JOB

Använd Invoke-Command cmdlet för att köra ett Start-Job kommando på en fjärrdator.

Det här kommandot kräver en PSSession (en permanent anslutning). Om du använder parametern ComputerName för Invoke-Command för att upprätta en tillfällig anslutning anses Invoke-Command-kommandot vara slutfört när jobbobjektet returneras. Därför stängs den tillfälliga anslutningen och jobbet avbryts.

Följande kommando använder cmdleten New-PSSession för att skapa en PSSession som är ansluten till Server01-datorn. Kommandot sparar PSSession i \$ s-variabeln.

```powershell
$s = new-pssession -computername Server01
```

Nästa kommando använder cmdleten Invoke-Command för att köra ett Start-Job-kommando i PSSession. Kommandot Start-Job och kommandot Get-Eventlog omges av klammerparenteser.

```powershell
invoke-command -session $s -scriptblock {
  start-job -scriptblock {get-eventlog system}}
```

Resultatet liknar följande exempel på utdata.

```Output
Id       Name    State      HasMoreData     Location   Command
--       ----    -----      -----------     --------   -------
2        Job2    Running    True            Localhost  get-eventlog system
```

När du kör ett Start-Job kommando på distans, returnerar Invoke-Command samma typ av jobb objekt som Start-Job returnerar. Du kan spara jobbobjektet i en variabel, eller så kan du använda ett Get-Job-kommando för att hämta jobbet.

Observera att värdet för egenskapen location visar att jobbet kördes på den lokala datorn, vilket kallas "LocalHost", även om jobbet kördes på Server01-datorn. Eftersom jobbobjektet skapas på den Server01 datorn och jobbet körs på samma dator betraktas det som ett lokalt bakgrunds jobb.

#### <a name="step-2-invoke-command-get-job"></a>STEG 2: ANROPA-KOMMANDO GET-JOB

Använd jobb-cmdletarna om du vill hantera ett fjärran slutet bakgrunds jobb. Eftersom jobbobjektet finns på fjärrdatorn måste du köra fjärrkommandon för att få, stoppa, vänta eller hämta jobb resultaten.

Om du vill se om jobbet är klart använder du ett Invoke-Command kommando för att köra ett Get-Job kommando i PSSession som är anslutet till Server01-datorn.

```powershell
invoke-command -session $s -scriptblock {get-job}
```

Kommandot returnerar ett jobb objekt. Egenskapen State för jobbobjektet visar att kommandot slutfördes korrekt.

```Output
SessionId   Name  State      HasMoreData   Location   Command
---------   ----  -----      -----------   --------   -------
2           Job2  Completed  True          LocalHost   get-eventlog system
```

#### <a name="step-3-invoke-command-receive-job"></a>STEG 3: INVOKE-KOMMANDOT RECEIVE-JOB

Om du vill hämta resultatet av jobbet använder du cmdleten Invoke-Command för att köra ett Receive-Job kommando i PSSession som är anslutet till Server01-datorn.

Följande kommando använder cmdleten Receive-Job för att hämta resultatet av jobbet. Den använder sessions-ID: t för att identifiera jobbet. Det här kommandot sparar jobb resultaten i \$ variabeln Results. Parametern Behåll för Receive-Job används för att behålla resultatet i jobbets cacheminne på fjärrdatorn.

```powershell
$results = invoke-command -session $s -scriptblock {
  receive-job -sessionid 2 -keep}
```

Du kan också omdirigera resultatet till en fil på den lokala datorn eller fjärrdatorn.
Följande kommando använder en omdirigerings operator för att spara resultatet i en fil på Server01-datorn.

```powershell
invoke-command -session $s -command {
  receive-job -sessionid 2 > c:\logs\pslog.txt}
```

## <a name="see-also"></a>SE ÄVEN

[about_Jobs](about_Jobs.md)

[about_Job_Details](about_Job_Details.md)

[about_Remote](about_Remote.md)

[about_Remote_Variables](about_Remote_Variables.md)

[Invoke-kommando](xref:Microsoft.PowerShell.Core.Invoke-Command)

[Start – jobb](xref:Microsoft.PowerShell.Core.Start-Job)

[Hämta jobb](xref:Microsoft.PowerShell.Core.Get-Job)

[Wait-Job](xref:Microsoft.PowerShell.Core.Wait-Job)

[Stoppa – jobb](xref:Microsoft.PowerShell.Core.Stop-Job)

[Ta bort – jobb](xref:Microsoft.PowerShell.Core.Remove-Job)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)

[Retur-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[Avsluta-PSSession](xref:Microsoft.PowerShell.Core.Exit-PSSession)

